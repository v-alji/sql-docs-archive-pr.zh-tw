---
title: MSSQLSERVER_2530 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 5d4be07a-38a5-4b25-819c-4dcb4636cc15
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 30b57aae907d6f0acc4d1c0e6021bf936621c69e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585474"
---
# <a name="mssqlserver_2530"></a><span data-ttu-id="546c1-102">MSSQLSERVER_2530</span><span class="sxs-lookup"><span data-stu-id="546c1-102">MSSQLSERVER_2530</span></span>
    
## <a name="details"></a><span data-ttu-id="546c1-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="546c1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="546c1-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="546c1-104">Product Name</span></span>|<span data-ttu-id="546c1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="546c1-105">SQL Server</span></span>|  
|<span data-ttu-id="546c1-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="546c1-106">Event ID</span></span>|<span data-ttu-id="546c1-107">2530</span><span class="sxs-lookup"><span data-stu-id="546c1-107">2530</span></span>|  
|<span data-ttu-id="546c1-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="546c1-108">Event Source</span></span>|<span data-ttu-id="546c1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="546c1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="546c1-110">元件</span><span class="sxs-lookup"><span data-stu-id="546c1-110">Component</span></span>|<span data-ttu-id="546c1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="546c1-111">SQLEngine</span></span>|  
|<span data-ttu-id="546c1-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="546c1-112">Symbolic Name</span></span>|<span data-ttu-id="546c1-113">DBCC_INDEX_IS_OFFLINE</span><span class="sxs-lookup"><span data-stu-id="546c1-113">DBCC_INDEX_IS_OFFLINE</span></span>|  
|<span data-ttu-id="546c1-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="546c1-114">Message Text</span></span>|<span data-ttu-id="546c1-115">資料表 "%.\*ls" 上的索引 "%.\*ls" 已停用。</span><span class="sxs-lookup"><span data-stu-id="546c1-115">The index "%.\*ls" on table "%.\*ls" is disabled.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="546c1-116">說明</span><span class="sxs-lookup"><span data-stu-id="546c1-116">Explanation</span></span>  
 <span data-ttu-id="546c1-117">指定的索引已停用，因此無法進行 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="546c1-117">The DBCC statement cannot proceed because the specified index is disabled.</span></span> <span data-ttu-id="546c1-118">索引停用後，在重建或卸除並重新建立之前，索引會一直維持在停用狀態。</span><span class="sxs-lookup"><span data-stu-id="546c1-118">After an index is disabled, it remains in a disabled state until it is rebuilt or dropped and re-created.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="546c1-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="546c1-119">User Action</span></span>  
  
1.  <span data-ttu-id="546c1-120">使用以下其中一個方法來啟用已停用的索引：</span><span class="sxs-lookup"><span data-stu-id="546c1-120">Enable the disabled index by using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="546c1-121">ALTER INDEX 陳述式加上 REBUILD 子句</span><span class="sxs-lookup"><span data-stu-id="546c1-121">ALTER INDEX statement with the REBUILD clause</span></span>  
  
    -   <span data-ttu-id="546c1-122">CREATE INDEX 加上 DROP_EXISTING 子句</span><span class="sxs-lookup"><span data-stu-id="546c1-122">CREATE INDEX with the DROP_EXISTING clause</span></span>  
  
    -   <span data-ttu-id="546c1-123">DBCC DBREINDEX</span><span class="sxs-lookup"><span data-stu-id="546c1-123">DBCC DBREINDEX</span></span>  
  
2.  <span data-ttu-id="546c1-124">請重新執行 DBCC 陳述式。</span><span class="sxs-lookup"><span data-stu-id="546c1-124">Rerun the DBCC statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="546c1-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="546c1-125">See Also</span></span>  
 <span data-ttu-id="546c1-126">[啟用索引和條件約束](../indexes/enable-indexes-and-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="546c1-126">[Enable Indexes and Constraints](../indexes/enable-indexes-and-constraints.md) </span></span>  
 <span data-ttu-id="546c1-127">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="546c1-127">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="546c1-128">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="546c1-128">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 [<span data-ttu-id="546c1-129">DBCC DBREINDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="546c1-129">DBCC DBREINDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql)  
  
  
