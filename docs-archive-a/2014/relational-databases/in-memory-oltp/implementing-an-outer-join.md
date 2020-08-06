---
title: 實作外部聯結 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 67084043-6b23-4975-b9db-6e49923d4bab
author: rothja
ms.author: jroth
ms.openlocfilehash: 73017541a8fc7b933c4ace1ef6539d53047ea5df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585395"
---
# <a name="implementing-an-outer-join"></a><span data-ttu-id="6c873-102">實作外部聯結</span><span class="sxs-lookup"><span data-stu-id="6c873-102">Implementing an Outer Join</span></span>
  <span data-ttu-id="6c873-103">原生編譯的預存程序不支援外部聯結。</span><span class="sxs-lookup"><span data-stu-id="6c873-103">Outer join is not supported in natively compiled stored procedures.</span></span> <span data-ttu-id="6c873-104">下列範例示範如何在原生編譯的預存程序中實作左方外部聯結功能。</span><span class="sxs-lookup"><span data-stu-id="6c873-104">The following sample shows a way to implement the functionality of a left outer join in a natively compiled stored procedure.</span></span>  
  
 <span data-ttu-id="6c873-105">此範例使用一個資料表變數來模擬聯結左側的資料指標，並使用另一個資料表變數來建構單一結果集，由於需要建立額外的資料列複本，因此僅適用於處理有限數目的資料列。</span><span class="sxs-lookup"><span data-stu-id="6c873-105">The samples uses a table variable to simulate a cursor on the left side of the join, and a table variable to construct a single result set, which is only suitable when processing a limited number of rows as it involves creating an additional copy of the data rows.</span></span>  
  
 <span data-ttu-id="6c873-106">T1_type 類型的變數 (@outer) 會用來逐一查看 t1 的資料列，並使用 while 迴圈來模擬資料指標。</span><span class="sxs-lookup"><span data-stu-id="6c873-106">A variable (@outer) of type t1_type is used to iterate over the rows from t1, using a while loop to simulate a cursor.</span></span> <span data-ttu-id="6c873-107">@result然後會使用 t1t2_join_type 類型的變數來建立結果集。</span><span class="sxs-lookup"><span data-stu-id="6c873-107">The variable @result of type t1t2_join_type is then used to construct the result set.</span></span>  
  
 <span data-ttu-id="6c873-108">您應該測試這個因應措施的執行效果，以確定其在您的應用程式中如預期般執行。</span><span class="sxs-lookup"><span data-stu-id="6c873-108">You should test the performance of this workaround, to be sure that it performs as expected in your application.</span></span>  
  
```  
-- original query:  
select   
   t1.c1 as t1c1,  
   t1.c2 as t1c2,  
   t2.c2 as t2c2,  
   t2.c3 as t2c3  
   from t1 left join t2 on t1.c2=t2.c3  
GO  
  
create table dbo.t1  
(c1 int not null primary key nonclustered,  
c2 int not null) with (memory_optimized=on)  
  
create table dbo.t2  
(c2 int not null primary key nonclustered,  
c3 int not null) with (memory_optimized=on)  
  
INSERT t1 VALUES (1,2)  
INSERT t1 VALUES (2,3)  
INSERT t1 VALUES (3,2)  
INSERT t2 VALUES (2,3)  
INSERT t2 VALUES (4,3)  
GO  
  
create type dbo.t1_type as table  
(  
   id int identity not null primary key nonclustered hash with (bucket_count=1024),  
   c1 int,  
   c2 int  
) with (memory_optimized=on)  
GO  
  
create type dbo.t1t2_join_type as table  
(  
   t1c1 int not null index ix_t1c1,  
   t1c2 int not null,  
   t2c2 int,  
   t2c3 int  
) with (memory_optimized=on)  
GO  
  
-- ====== scenario: generic left join  
  
-- stored procedure including the workaround  
create procedure dbo.usp_left_join  
with native_compilation, execute as owner, schemabinding  
as  
begin atomic with (transaction isolation level = snapshot, language = N'us_english')  
  
   DECLARE @outer dbo.t1_type  
   DECLARE @result dbo.t1t2_join_type  
  
   -- populate the variable used for iterating over the outer rows  
   INSERT @outer(c1, c2) select c1,c2 from dbo.t1  
  
   DECLARE @i int = 1  
   DECLARE @max int = scope_identity()  
  
   DECLARE @t1c1 int  
   DECLARE @t1c2 int  
  
   while @i <= @max  
   begin     
      select @t1c1 = c1, @t1c2 = c2 from @outer where id = @i  
  
      INSERT @result select @t1c1, @t1c2, c2, c3 from dbo.t2 where c3 = @t1c2  
  
      if @@rowcount = 0   
         INSERT @result (t1c1, t1c2) VALUES (@t1c1, @t1c2)  
  
      set @i += 1  
   end  
  
   select   
      t1c1,  
      t1c2,  
      t2c2,  
      t2c3  
   from @result  
end  
GO  
  
exec dbo.usp_left_join  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c873-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c873-109">See Also</span></span>  
 <span data-ttu-id="6c873-110">[原生編譯預存程序的移轉問題](migration-issues-for-natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="6c873-110">[Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md) </span></span>  
 [<span data-ttu-id="6c873-111">記憶體中的 OLTP 不支援 Transact-SQL 建構</span><span class="sxs-lookup"><span data-stu-id="6c873-111">Transact-SQL Constructs Not Supported by In-Memory OLTP</span></span>](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
