---
title: MSSQLSERVER_2546 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5c1c5f64ca0daba413f2b71c05f5b8e57b2d55df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687914"
---
# <a name="mssqlserver_2546"></a><span data-ttu-id="20ba6-102">MSSQLSERVER_2546</span><span class="sxs-lookup"><span data-stu-id="20ba6-102">MSSQLSERVER_2546</span></span>
    
## <a name="details"></a><span data-ttu-id="20ba6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="20ba6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="20ba6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="20ba6-104">Product Name</span></span>|<span data-ttu-id="20ba6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="20ba6-105">SQL Server</span></span>|  
|<span data-ttu-id="20ba6-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="20ba6-106">Event ID</span></span>|<span data-ttu-id="20ba6-107">2546</span><span class="sxs-lookup"><span data-stu-id="20ba6-107">2546</span></span>|  
|<span data-ttu-id="20ba6-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="20ba6-108">Event Source</span></span>|<span data-ttu-id="20ba6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="20ba6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="20ba6-110">元件</span><span class="sxs-lookup"><span data-stu-id="20ba6-110">Component</span></span>|<span data-ttu-id="20ba6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="20ba6-111">SQLEngine</span></span>|  
|<span data-ttu-id="20ba6-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="20ba6-112">Symbolic Name</span></span>|<span data-ttu-id="20ba6-113">DBCC_INDEX_MARKED_DISABLED</span><span class="sxs-lookup"><span data-stu-id="20ba6-113">DBCC_INDEX_MARKED_DISABLED</span></span>|  
|<span data-ttu-id="20ba6-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="20ba6-114">Message Text</span></span>|<span data-ttu-id="20ba6-115">資料表 'OBJECT_NAME' 上的索引 'INDEX_NAME' 已標示為停用。</span><span class="sxs-lookup"><span data-stu-id="20ba6-115">Index 'INDEX_NAME' on table 'OBJECT_NAME' is marked as disabled.</span></span> <span data-ttu-id="20ba6-116">請重建索引使其上線。</span><span class="sxs-lookup"><span data-stu-id="20ba6-116">Rebuild the index to bring it online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="20ba6-117">說明</span><span class="sxs-lookup"><span data-stu-id="20ba6-117">Explanation</span></span>  
 <span data-ttu-id="20ba6-118">指定的索引已標示為離線或停用。</span><span class="sxs-lookup"><span data-stu-id="20ba6-118">The specified index is marked as offline or is disabled.</span></span> <span data-ttu-id="20ba6-119">因此，無法檢查此索引。</span><span class="sxs-lookup"><span data-stu-id="20ba6-119">Therefore, this index cannot be checked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="20ba6-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="20ba6-120">User Action</span></span>  
 <span data-ttu-id="20ba6-121">使用 ALTER INDEX 來重建索引。</span><span class="sxs-lookup"><span data-stu-id="20ba6-121">Rebuild the index by using ALTER INDEX.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ba6-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20ba6-122">See Also</span></span>  
 <span data-ttu-id="20ba6-123">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="20ba6-123">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 [<span data-ttu-id="20ba6-124">重新組織與重建索引</span><span class="sxs-lookup"><span data-stu-id="20ba6-124">Reorganize and Rebuild Indexes</span></span>](../indexes/indexes.md)  
  
  
