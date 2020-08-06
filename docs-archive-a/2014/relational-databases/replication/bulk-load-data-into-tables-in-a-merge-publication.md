---
title: 將資料大量載入合併式發行集中的資料表 (複寫 Transact-sql 程式設計) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- bulk load [SQL Server replication]
- merge replication bulk loading [SQL Server replication]
- sp_addtabletocontents
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f669a1f7132aa0f588fd89fb9747a7dc9017fcf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709217"
---
# <a name="bulk-load-data-into-tables-in-a-merge-publication-replication-transact-sql-programming"></a><span data-ttu-id="696b3-102">將資料大量載入合併式發行集中的資料表 (複寫 Transact-SQL 程式設計)</span><span class="sxs-lookup"><span data-stu-id="696b3-102">Bulk-Load Data into Tables in a Merge Publication (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="696b3-103">使用 [bcp Utility](../../tools/bcp-utility.md) 或 [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) 命令將資料載入資料表時，根據預設不會引發在 [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql) 系統資料表中維護追蹤資料的合併式複寫觸發程序。</span><span class="sxs-lookup"><span data-stu-id="696b3-103">When data is loaded into tables using the [bcp Utility](../../tools/bcp-utility.md) or the [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) command, by default, the merge replication triggers that maintain tracking data in the [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql) system table are not fired.</span></span> <span data-ttu-id="696b3-104">您可以在資料載入時強制引發合併式複寫觸發程序，或者使用複寫預存程序，以程式設計的方式在大量複製作業之後插入產生的複寫中繼資料。</span><span class="sxs-lookup"><span data-stu-id="696b3-104">You can either force the merge replication triggers to fire as the data is loaded, or you can insert the generated replication metadata programmatically after the bulk copy operation using replication stored procedures.</span></span>  
  
### <a name="to-bulk-load-data-into-tables-published-by-merge-replication-using-the-bcp-utility"></a><span data-ttu-id="696b3-105">使用 bcp 公用程式將資料大量載入合併式發行集所發行的資料表</span><span class="sxs-lookup"><span data-stu-id="696b3-105">To bulk-load data into tables published by merge replication using the bcp utility</span></span>  
  
1.  <span data-ttu-id="696b3-106">在「發行者」或「訂閱者」端執行 [bcp Utility](../../tools/bcp-utility.md) 或 [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) ，將資料插入至使用合併式複寫所發行的資料表。</span><span class="sxs-lookup"><span data-stu-id="696b3-106">At either the Publisher or Subscriber, execute the [bcp Utility](../../tools/bcp-utility.md) or [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) to insert data into a table published using merge replication.</span></span>  
  
2.  <span data-ttu-id="696b3-107">使用下列其中一個方法，確保會針對插入的資料產生複寫中繼資料。</span><span class="sxs-lookup"><span data-stu-id="696b3-107">Use one of the following methods to ensure that replication metadata is generated for the inserted data.</span></span>  
  
    -   <span data-ttu-id="696b3-108">使用 FIRE_TRIGGERS 選項執行大量複製。</span><span class="sxs-lookup"><span data-stu-id="696b3-108">Execute the bulk copy using the FIRE_TRIGGERS option.</span></span>  
  
    -   <span data-ttu-id="696b3-109">在插入資料的資料庫上，執行 [sp_addtabletocontents &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="696b3-109">On the database into which data was inserted, execute [sp_addtabletocontents &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql).</span></span> <span data-ttu-id="696b3-110">指定要在其中插入資料的資料表名稱 **@table_name** 。</span><span class="sxs-lookup"><span data-stu-id="696b3-110">Specify the table name into which the data was inserted for **@table_name**.</span></span>  
  
  
