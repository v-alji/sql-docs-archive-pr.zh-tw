---
title: MSSQLSERVER_1904 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1904 (Database Engine error)
ms.assetid: 2a35d57d-74e2-45a2-8f67-3f2e51d69712
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 568cfe7499c041c2ee6a8ac3698b31698171bece
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595078"
---
# <a name="mssqlserver_1904"></a><span data-ttu-id="334b2-102">MSSQLSERVER_1904</span><span class="sxs-lookup"><span data-stu-id="334b2-102">MSSQLSERVER_1904</span></span>
    
## <a name="details"></a><span data-ttu-id="334b2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="334b2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="334b2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="334b2-104">Product Name</span></span>|<span data-ttu-id="334b2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="334b2-105">SQL Server</span></span>|  
|<span data-ttu-id="334b2-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="334b2-106">Event ID</span></span>|<span data-ttu-id="334b2-107">1904</span><span class="sxs-lookup"><span data-stu-id="334b2-107">1904</span></span>|  
|<span data-ttu-id="334b2-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="334b2-108">Event Source</span></span>|<span data-ttu-id="334b2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="334b2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="334b2-110">元件</span><span class="sxs-lookup"><span data-stu-id="334b2-110">Component</span></span>|<span data-ttu-id="334b2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="334b2-111">SQLEngine</span></span>|  
|<span data-ttu-id="334b2-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="334b2-112">Symbolic Name</span></span>|<span data-ttu-id="334b2-113">KEYCOUNT</span><span class="sxs-lookup"><span data-stu-id="334b2-113">KEYCOUNT</span></span>|  
|<span data-ttu-id="334b2-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="334b2-114">Message Text</span></span>|<span data-ttu-id="334b2-115">資料表 '%.\*ls' 上的 %S_MSG '%.\*ls'，其在 %S_MSG 索引鍵清單中有 %d 個資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="334b2-115">The %S_MSG '%.\*ls' on table '%.\*ls' has %d column names in %S_MSG key list.</span></span> <span data-ttu-id="334b2-116">索引或統計資料索引鍵資料行清單的上限為 %d。</span><span class="sxs-lookup"><span data-stu-id="334b2-116">The maximum limit for index or statistics key column list is %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="334b2-117">說明</span><span class="sxs-lookup"><span data-stu-id="334b2-117">Explanation</span></span>  
 <span data-ttu-id="334b2-118">指定之索引或統計資料的索引鍵資料行清單超過允許的資料行數目上限。</span><span class="sxs-lookup"><span data-stu-id="334b2-118">The key column list for the specified index or statistics exceeds the maximum number of columns allowed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="334b2-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="334b2-119">User Action</span></span>  
 <span data-ttu-id="334b2-120">將索引鍵資料行清單修改成包含不超過指定的資料行數目上限。</span><span class="sxs-lookup"><span data-stu-id="334b2-120">Modify the key column list to include no more than the specified maximum number of columns.</span></span>  
  
 <span data-ttu-id="334b2-121">若為非叢集索引，請考慮在 CREATE INDEX 陳述式中使用 INCLUDE 子句，以便將資料行加入至索引，當做非索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="334b2-121">For nonclustered indexes, consider using the INCLUDE clause in the CREATE INDEX statement to add columns to the index as nonkey columns.</span></span> <span data-ttu-id="334b2-122">這個方法可避免超過目前索引大小限制：16 個索引鍵資料行的上限。</span><span class="sxs-lookup"><span data-stu-id="334b2-122">This method avoids exceeding the current index size limitation of a maximum of 16 key columns.</span></span> <span data-ttu-id="334b2-123">如需詳細資訊，請參閱 [建立內含資料行的索引](../indexes/create-indexes-with-included-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="334b2-123">For more information, see [Create Indexes with Included Columns](../indexes/create-indexes-with-included-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="334b2-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="334b2-124">See Also</span></span>  
 <span data-ttu-id="334b2-125">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="334b2-125">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 [<span data-ttu-id="334b2-126">CREATE STATISTICS &#40;TRANSACT-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="334b2-126">CREATE STATISTICS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-statistics-transact-sql)  
  
  
