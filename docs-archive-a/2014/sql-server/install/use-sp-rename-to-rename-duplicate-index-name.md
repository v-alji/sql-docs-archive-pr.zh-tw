---
title: 使用 sp_rename 重新命名重複的索引名稱 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- table names [SQL Server]
- duplicate table names
- index names [SQL Server]
- sp_rename
- duplicate index names
ms.assetid: ee66c7a5-eb6d-4fcf-970c-ab099d78c8d9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b8ffe3b9befd0c7239d32094e5738e0fb2947c5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710122"
---
# <a name="use-sp_rename-to-rename-duplicate-index-name"></a><span data-ttu-id="dca45-102">使用 sp_rename 重新命名重複的索引名稱</span><span class="sxs-lookup"><span data-stu-id="dca45-102">Use sp_rename to rename duplicate index name</span></span>
  <span data-ttu-id="dca45-103">Upgrade Advisor 偵測到重複的資料表或檢視表索引名稱。</span><span class="sxs-lookup"><span data-stu-id="dca45-103">Upgrade Advisor has detected duplicate table or view index names.</span></span> <span data-ttu-id="dca45-104">升級之前，請先重新命名索引以移除重複項目。</span><span class="sxs-lookup"><span data-stu-id="dca45-104">Rename the indexes to remove duplicates before upgrading.</span></span>  
  
## <a name="component"></a><span data-ttu-id="dca45-105">元件</span><span class="sxs-lookup"><span data-stu-id="dca45-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="dca45-106">更正動作</span><span class="sxs-lookup"><span data-stu-id="dca45-106">Corrective Action</span></span>  
  
1.  <span data-ttu-id="dca45-107">請執行下列查詢來尋找重複的索引。</span><span class="sxs-lookup"><span data-stu-id="dca45-107">Locate the duplicate indexes by executing the following query.</span></span>  
  
    ```  
    SELECT DISTINCT OBJECT_NAME(o.id), name  
    FROM sysindexes as o  
    WHERE EXISTS   
        (SELECT name FROM sysindexes  as i  
          WHERE i.id = o.id  
          AND i.name = o.name and i.indid < o.indid);  
    ```  
  
2.  <span data-ttu-id="dca45-108">使用**sp_rename**來變更其中一個索引名稱。</span><span class="sxs-lookup"><span data-stu-id="dca45-108">Use **sp_rename** to change one of the index names.</span></span> <span data-ttu-id="dca45-109">因為索引名稱相同，所以您無法判斷要重新命名的索引。</span><span class="sxs-lookup"><span data-stu-id="dca45-109">Because the index names are the same, you cannot determine which index will be renamed.</span></span> <span data-ttu-id="dca45-110">這個步驟可讓您區分索引。</span><span class="sxs-lookup"><span data-stu-id="dca45-110">This step allows you to differentiate the indexes.</span></span>  
  
    ```  
    EXEC sp_rename N'table_name.index_name', N'new_index_name', N'INDEX'  
    ```  
  
3.  <span data-ttu-id="dca45-111">請執行下列查詢來確認重新命名的索引。</span><span class="sxs-lookup"><span data-stu-id="dca45-111">Verify which index was renamed by executing the following query.</span></span> <span data-ttu-id="dca45-112">此查詢會傳回指定資料表或檢視上的所有索引 (包括索引鍵資料行名稱)。</span><span class="sxs-lookup"><span data-stu-id="dca45-112">This query returns all indexes (including key column names) on the specified table or view.</span></span>  
  
    ```  
    SELECT i.name AS IndexName, c.name AS ColumnName, ik.colid, ik.keyno  
    FROM sysindexes i  
    JOIN sysindexkeys ik ON i.id = ik.id and i.indid = ik.indid   
    JOIN syscolumns c ON c.id = ik.id and ik.colid = c.colid  
    WHERE i.id = OBJECT_ID('table_or_view_name')  
    ```  
  
4.  <span data-ttu-id="dca45-113">如有必要，請再次使用**sp_rename**來更正索引名稱。</span><span class="sxs-lookup"><span data-stu-id="dca45-113">If necessary, use **sp_rename** again to correct the index names.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca45-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dca45-114">See Also</span></span>  
 <span data-ttu-id="dca45-115">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="dca45-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="dca45-116">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="dca45-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
