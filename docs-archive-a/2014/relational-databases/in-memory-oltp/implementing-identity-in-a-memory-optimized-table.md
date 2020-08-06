---
title: 在記憶體最佳化資料表中實作 IDENTITY | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
author: rothja
ms.author: jroth
ms.openlocfilehash: 955f9f1a905a9d0c71304320f60abe300e430e4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594562"
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a><span data-ttu-id="9b83e-102">在記憶體最佳化資料表中實作 IDENTITY</span><span class="sxs-lookup"><span data-stu-id="9b83e-102">Implementing IDENTITY in a Memory-Optimized Table</span></span>
  <span data-ttu-id="9b83e-103">記憶體最佳化資料表支援 IDENTITY(1, 1)。</span><span class="sxs-lookup"><span data-stu-id="9b83e-103">IDENTITY(1, 1) is supported on a memory-optimized table.</span></span> <span data-ttu-id="9b83e-104">但是，記憶體最佳化資料表不支援定義為 IDENTITY(x, y) (其中 x != 1 或 y != 1) 的識別欄位。</span><span class="sxs-lookup"><span data-stu-id="9b83e-104">However, identity columns with definition of IDENTITY(x, y) where x != 1 or y != 1 are not supported on memory-optimized tables.</span></span> <span data-ttu-id="9b83e-105">識別值的因應措施會使用順序物件 ([序號](../sequence-numbers/sequence-numbers.md)) 。</span><span class="sxs-lookup"><span data-stu-id="9b83e-105">The workaround for IDENTITY values uses the SEQUENCE object ([Sequence Numbers](../sequence-numbers/sequence-numbers.md)).</span></span>  
  
 <span data-ttu-id="9b83e-106">首先將 IDENTITY 屬性從您要轉換成 In-Memory OLTP 的資料表中移除。</span><span class="sxs-lookup"><span data-stu-id="9b83e-106">First remove the IDENTITY property from the table you are converting to In-Memory OLTP.</span></span> <span data-ttu-id="9b83e-107">接著在資料表中為資料行定義新的 SEQUENCE 物件。</span><span class="sxs-lookup"><span data-stu-id="9b83e-107">Then, define a new SEQUENCE object for the column in the table.</span></span> <span data-ttu-id="9b83e-108">做為識別資料行的 SEQUENCE 物件需倚賴使用 NEXT VALUE FOR 語法建立資料行之 DEFAULT 值的能力取得新的識別值。</span><span class="sxs-lookup"><span data-stu-id="9b83e-108">SEQUENCE objects as identity columns rely on the ability to create DEFAULT values for columns that use the NEXT VALUE FOR syntax to get a new identity value.</span></span> <span data-ttu-id="9b83e-109">由於 In-Memory OLTP 中不支援 DEFAULT，因此您必須將新產生的 SEQUENCE 值傳遞至 INSERT 陳述式或執行插入作業的原生編譯預存程序。</span><span class="sxs-lookup"><span data-stu-id="9b83e-109">Since DEFAULTs are not supported in In-Memory OLTP, you need to pass the newly-generated SEQUENCE value either to the INSERT statement or to a natively compiled stored procedure that does the insert.</span></span> <span data-ttu-id="9b83e-110">下列範例示範此模式。</span><span class="sxs-lookup"><span data-stu-id="9b83e-110">The following example demonstrates this pattern.</span></span>  
  
```sql  
-- Create a new In-Memory OLTP table to simulate IDENTITY insert  
-- Here the column C1 was the identity column in the original table  
--  
create table T1  
(  
  
[c1] integer not null primary key T1_c1 nonclustered,  
[c2] varchar(32) not null,  
[c3] datetime not null  
  
) with (memory_optimized = on)  
go  
  
-- This is a sequence provider that will give us values for column [c1]  
--  
create sequence usq_SequenceForT1 as integer start with 2 increment by 1  
go  
  
--   insert a sample row using the sequence  
--   note that a new value needs to be retrieved form   
--   the sequence object for every insert  
--  
declare @c1 integer = next value for [dbo].[usq_SequenceForT1]  
insert into T1 values (@c1, 'test', getdate())  
```  
  
 <span data-ttu-id="9b83e-111">執行插入作業數次之後，您會在資料行 [c1] 中看見有效的單純遞增值。</span><span class="sxs-lookup"><span data-stu-id="9b83e-111">After performing the insert several times, you see valid monotonically increasing values in column [c1].</span></span> <span data-ttu-id="9b83e-112">此結果集是使用資料表掃描和沒有 `ORDER BY` 的雜湊索引所產生，因此資料列並未排序。</span><span class="sxs-lookup"><span data-stu-id="9b83e-112">This result set is generated using table scan and hash index without `ORDER BY` so the rows are not ordered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b83e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b83e-113">See Also</span></span>  
 [<span data-ttu-id="9b83e-114">移轉至 In-Memory OLTP</span><span class="sxs-lookup"><span data-stu-id="9b83e-114">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
