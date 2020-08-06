---
title: MSSQLSERVER_3156 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3156 (Database Engine error)
ms.assetid: 345d8ed4-177e-4ec3-bab3-25d30000e323
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 25b5a037012a6d6b47b91e763a49cfb67b89f43c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596026"
---
# <a name="mssqlserver_3156"></a><span data-ttu-id="66d26-102">MSSQLSERVER_3156</span><span class="sxs-lookup"><span data-stu-id="66d26-102">MSSQLSERVER_3156</span></span>
    
## <a name="details"></a><span data-ttu-id="66d26-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="66d26-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="66d26-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="66d26-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="66d26-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="66d26-105">Event ID</span></span>|<span data-ttu-id="66d26-106">3156</span><span class="sxs-lookup"><span data-stu-id="66d26-106">3156</span></span>|  
|<span data-ttu-id="66d26-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="66d26-107">Event Source</span></span>|<span data-ttu-id="66d26-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="66d26-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="66d26-109">元件</span><span class="sxs-lookup"><span data-stu-id="66d26-109">Component</span></span>|<span data-ttu-id="66d26-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="66d26-110">SQLEngine</span></span>|  
|<span data-ttu-id="66d26-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="66d26-111">Symbolic Name</span></span>|<span data-ttu-id="66d26-112">LDDB_CANT_WRITE</span><span class="sxs-lookup"><span data-stu-id="66d26-112">LDDB_CANT_WRITE</span></span>|  
|<span data-ttu-id="66d26-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="66d26-113">Message Text</span></span>|<span data-ttu-id="66d26-114">檔案 '%ls' 無法還原到 '%ls'。</span><span class="sxs-lookup"><span data-stu-id="66d26-114">File '%ls' cannot be restored to '%ls'.</span></span> <span data-ttu-id="66d26-115">請使用 WITH MOVE 來識別該檔案的有效位置。</span><span class="sxs-lookup"><span data-stu-id="66d26-115">Use WITH MOVE to identify a valid location for the file.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="66d26-116">說明</span><span class="sxs-lookup"><span data-stu-id="66d26-116">Explanation</span></span>  
 <span data-ttu-id="66d26-117">這個一般訊息表示由於指定的位置有問題，以致檔案無法還原邏輯檔案名稱或實體檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="66d26-117">This general message identifies the logical or physical file names of files that could not be restored because of a problem with the specified location.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="66d26-118">可能的原因</span><span class="sxs-lookup"><span data-stu-id="66d26-118">Possible Causes</span></span>  
 <span data-ttu-id="66d26-119">可能的原因包括：</span><span class="sxs-lookup"><span data-stu-id="66d26-119">The possible causes include the following:</span></span>  
  
-   <span data-ttu-id="66d26-120">您可能必須對指定的 Windows 目錄有存取權。</span><span class="sxs-lookup"><span data-stu-id="66d26-120">You might need access to the specified Windows directory.</span></span>  
  
-   <span data-ttu-id="66d26-121">您所輸入的路徑可能有誤，或是指定的路徑不存在。</span><span class="sxs-lookup"><span data-stu-id="66d26-121">You might have mistyped the path or specified a path that does not exist.</span></span>  
  
-   <span data-ttu-id="66d26-122">檔案名稱可能正由另一檔案使用中，因而無法覆寫。</span><span class="sxs-lookup"><span data-stu-id="66d26-122">The file name might be being used by a file that cannot be overwritten.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="66d26-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="66d26-123">User Action</span></span>  
 <span data-ttu-id="66d26-124">請查閱錯誤記錄檔中的其他訊息，以取得更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="66d26-124">Look at the error logs for other messages that provide more details.</span></span>  
  
 <span data-ttu-id="66d26-125">從指定的位置著手修正問題，例如授與存取權，或在 RESTORE 陳述式中使用 WITH MOVE 選項來重新放置檔案。</span><span class="sxs-lookup"><span data-stu-id="66d26-125">Correct the problem with the specified location, for example, by granting access, or use the WITH MOVE option in your RESTORE statement to relocate the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66d26-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66d26-126">See Also</span></span>  
 <span data-ttu-id="66d26-127">[將資料庫還原到新位置 &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="66d26-127">[Restore a Database to a New Location &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="66d26-128">[將檔案還原到新的位置 &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="66d26-128">[Restore Files to a New Location &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span></span>  
 [<span data-ttu-id="66d26-129">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="66d26-129">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
