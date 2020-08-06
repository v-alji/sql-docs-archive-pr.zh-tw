---
title: MSSQLSERVER_1105 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1105 (Database Engine error)
ms.assetid: e7f4ad02-8c7f-4bb9-9781-2c86253f2138
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dea326fab7edd6a5c155c8f0182bffc044505eb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585487"
---
# <a name="mssqlserver_1105"></a><span data-ttu-id="0f4bb-102">MSSQLSERVER_1105</span><span class="sxs-lookup"><span data-stu-id="0f4bb-102">MSSQLSERVER_1105</span></span>
    
## <a name="details"></a><span data-ttu-id="0f4bb-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0f4bb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0f4bb-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0f4bb-104">Product Name</span></span>|<span data-ttu-id="0f4bb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0f4bb-105">SQL Server</span></span>|  
|<span data-ttu-id="0f4bb-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0f4bb-106">Event ID</span></span>|<span data-ttu-id="0f4bb-107">1105</span><span class="sxs-lookup"><span data-stu-id="0f4bb-107">1105</span></span>|  
|<span data-ttu-id="0f4bb-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="0f4bb-108">Event Source</span></span>|<span data-ttu-id="0f4bb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0f4bb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0f4bb-110">元件</span><span class="sxs-lookup"><span data-stu-id="0f4bb-110">Component</span></span>|<span data-ttu-id="0f4bb-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0f4bb-111">SQLEngine</span></span>|  
|<span data-ttu-id="0f4bb-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0f4bb-112">Symbolic Name</span></span>|<span data-ttu-id="0f4bb-113">NO_MORE_SPACE_IN_FG</span><span class="sxs-lookup"><span data-stu-id="0f4bb-113">NO_MORE_SPACE_IN_FG</span></span>|  
|<span data-ttu-id="0f4bb-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0f4bb-114">Message Text</span></span>|<span data-ttu-id="0f4bb-115">檔案群組已滿，無法在資料庫中為物件 '%.\*ls'%.\*ls 配置空間，檔案群組：'%.\*ls'，資料庫：'%.\*ls'。</span><span class="sxs-lookup"><span data-stu-id="0f4bb-115">Could not allocate space for object '%.\*ls'%.\*ls in database '%.\*ls' because the '%.\*ls' filegroup is full.</span></span> <span data-ttu-id="0f4bb-116">請刪除不必要的檔案、卸除檔案群組中的物件、將其他檔案加入檔案群組，或者將檔案群組中現有的檔案設定為自動成長，以產生磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="0f4bb-116">Create disk space by deleting unneeded files, dropping objects in the filegroup, adding additional files to the filegroup, or setting autogrowth on for existing files in the filegroup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0f4bb-117">說明</span><span class="sxs-lookup"><span data-stu-id="0f4bb-117">Explanation</span></span>  
 <span data-ttu-id="0f4bb-118">檔案群組中沒有可用的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="0f4bb-118">No disk space is available in a filegroup.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0f4bb-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0f4bb-119">User Action</span></span>  
 <span data-ttu-id="0f4bb-120">下列動作可以在檔案群組中提供可用的空間：</span><span class="sxs-lookup"><span data-stu-id="0f4bb-120">The following actions may make space available in the filegroup:</span></span>  
  
-   <span data-ttu-id="0f4bb-121">開啟自動成長功能。</span><span class="sxs-lookup"><span data-stu-id="0f4bb-121">Turn on autogrow.</span></span>  
  
-   <span data-ttu-id="0f4bb-122">加入更多檔案到檔案中。</span><span class="sxs-lookup"><span data-stu-id="0f4bb-122">Add more files to the file group.</span></span>  
  
-   <span data-ttu-id="0f4bb-123">卸除已經不需要的索引或資料表，以釋出磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="0f4bb-123">Free disk space by dropping index or tables that are no longer needed.</span></span>  
  
-   <span data-ttu-id="0f4bb-124">如需詳細資訊，請參閱《SQL Server 線上叢書》中的＜資料磁碟空間不足的疑難排解＞。</span><span class="sxs-lookup"><span data-stu-id="0f4bb-124">For more information, see "Troubleshooting Insufficient Data Disk Space" in SQL Server Books Online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f4bb-125">當索引位於數個檔案時，則當其中一個檔案已滿時，`ALTER INDEX REORGANIZE` 會傳回錯誤 1105。</span><span class="sxs-lookup"><span data-stu-id="0f4bb-125">When an index is located on several files, `ALTER INDEX REORGANIZE` can return error 1105 when one of the files is full.</span></span> <span data-ttu-id="0f4bb-126">當程序嘗試將列移至已滿的檔案時，會封鎖此重組的程序。</span><span class="sxs-lookup"><span data-stu-id="0f4bb-126">The reorganization process is blocked when the process tries to move rows to the full file.</span></span> <span data-ttu-id="0f4bb-127">若要解決此限制，請執行 `ALTER INDEX REBUILD` 而不是 `ALTER INDEX REORGANIZE`，或是為已滿的檔案增加檔案成長限制。</span><span class="sxs-lookup"><span data-stu-id="0f4bb-127">To work around this limitation perform an `ALTER INDEX REBUILD` instead of `ALTER INDEX REORGANIZE` or increase the file growth limit of any files that are full.</span></span>  
  
  
