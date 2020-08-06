---
title: 執行合併功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: d4bcdc36-3302-4abc-9b35-64ec2b920986
author: rothja
ms.author: jroth
ms.openlocfilehash: 8c2e2d3f0796396c0f3f451215f1fd685979a842
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594561"
---
# <a name="implementing-merge-functionality"></a><span data-ttu-id="68b4a-102">實作 MERGE 功能</span><span class="sxs-lookup"><span data-stu-id="68b4a-102">Implementing MERGE Functionality</span></span>
  <span data-ttu-id="68b4a-103">根據資料庫中是否已有某個特殊資料列存在而定，資料庫可能需要執行插入或更新。</span><span class="sxs-lookup"><span data-stu-id="68b4a-103">A database may need to perform either an insert of an update, depending on whether a particular row already exists in the database.</span></span>  
  
 <span data-ttu-id="68b4a-104">在不使用 `MERGE` 陳述式的情況下，以下提供可在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中使用的一種方式：</span><span class="sxs-lookup"><span data-stu-id="68b4a-104">Without using the `MERGE` statement, the following is one approach you can use in [!INCLUDE[tsql](../../includes/tsql-md.md)]:</span></span>  
  
```sql  
UPDATE mytable SET col=@somevalue WHERE myPK = @parm  
IF @@ROWCOUNT = 0  
    INSERT mytable (columns) VALUES (@parm, @other values)  
```  
  
 <span data-ttu-id="68b4a-105">實作合併的另一種 [!INCLUDE[tsql](../../includes/tsql-md.md)] 方法：</span><span class="sxs-lookup"><span data-stu-id="68b4a-105">Another [!INCLUDE[tsql](../../includes/tsql-md.md)] method to implement a merge:</span></span>  
  
```sql  
IF EXISTS (SELECT 1 FROM mytable WHERE myPK = @parm)  
    UPDATE....  
ELSE  
    INSERT  
```  
  
 <span data-ttu-id="68b4a-106">針對原生編譯預存程序</span><span class="sxs-lookup"><span data-stu-id="68b4a-106">For a natively compiled stored procedure</span></span>  
  
```sql  
DECLARE @i  int  = 0  -- or whatever your PK data type is  
UPDATE mytable SET @i=myPK, othercolums = other values WHERE myPK = @parm  
IF @i = 0  
   INSERT....  
```  
  
## <a name="see-also"></a><span data-ttu-id="68b4a-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68b4a-107">See Also</span></span>  
 <span data-ttu-id="68b4a-108">[原生編譯預存程序的移轉問題](migration-issues-for-natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="68b4a-108">[Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md) </span></span>  
 [<span data-ttu-id="68b4a-109">記憶體中的 OLTP 不支援 Transact-SQL 建構</span><span class="sxs-lookup"><span data-stu-id="68b4a-109">Transact-SQL Constructs Not Supported by In-Memory OLTP</span></span>](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
