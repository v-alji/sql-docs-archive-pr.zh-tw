---
title: MSSQLSERVER_3176 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3176 (Database Engine error)
ms.assetid: 4be24c64-2d52-4cb4-b4d7-36efbe4555b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 64e1a836995fe8738bb5c2ff0cb4de10d84d1f29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596022"
---
# <a name="mssqlserver_3176"></a><span data-ttu-id="17af5-102">MSSQLSERVER_3176</span><span class="sxs-lookup"><span data-stu-id="17af5-102">MSSQLSERVER_3176</span></span>
    
## <a name="details"></a><span data-ttu-id="17af5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="17af5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="17af5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="17af5-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="17af5-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="17af5-105">Event ID</span></span>|<span data-ttu-id="17af5-106">3176</span><span class="sxs-lookup"><span data-stu-id="17af5-106">3176</span></span>|  
|<span data-ttu-id="17af5-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="17af5-107">Event Source</span></span>|<span data-ttu-id="17af5-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="17af5-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="17af5-109">元件</span><span class="sxs-lookup"><span data-stu-id="17af5-109">Component</span></span>|<span data-ttu-id="17af5-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="17af5-110">SQLEngine</span></span>|  
|<span data-ttu-id="17af5-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="17af5-111">Symbolic Name</span></span>|<span data-ttu-id="17af5-112">LDDB_FILE_CLAIM</span><span class="sxs-lookup"><span data-stu-id="17af5-112">LDDB_FILE_CLAIM</span></span>|  
|<span data-ttu-id="17af5-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="17af5-113">Message Text</span></span>|<span data-ttu-id="17af5-114">檔案 '%ls' 已被 '%ls'(%d) 和 '%ls'(%d) 所要求。</span><span class="sxs-lookup"><span data-stu-id="17af5-114">File '%ls' is claimed by '%ls'(%d) and '%ls'(%d).</span></span> <span data-ttu-id="17af5-115">WITH MOVE 子句可以用來重新放置一個或多個檔案。</span><span class="sxs-lookup"><span data-stu-id="17af5-115">The WITH MOVE clause can be used to relocate one or more files.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="17af5-116">說明</span><span class="sxs-lookup"><span data-stu-id="17af5-116">Explanation</span></span>  
 <span data-ttu-id="17af5-117">試圖使用單一檔案從事多種用途。</span><span class="sxs-lookup"><span data-stu-id="17af5-117">Attempting to use a file for more than one purpose.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="17af5-118">可能的原因</span><span class="sxs-lookup"><span data-stu-id="17af5-118">Possible Causes</span></span>  
 <span data-ttu-id="17af5-119">檔案名稱正由另一資料庫使用中。</span><span class="sxs-lookup"><span data-stu-id="17af5-119">Another database is already using the file name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="17af5-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="17af5-120">User Action</span></span>  
 <span data-ttu-id="17af5-121">請將資料庫檔案還原到其他位置。</span><span class="sxs-lookup"><span data-stu-id="17af5-121">Restore the database files to a different location.</span></span> <span data-ttu-id="17af5-122">在 RESTORE 陳述式中，使用 WITH MOVE 子句搬移每個檔案。</span><span class="sxs-lookup"><span data-stu-id="17af5-122">In a RESTORE statement, use a WITH MOVE clause to move each file.</span></span> <span data-ttu-id="17af5-123">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 開啟 [還原資料庫] 對話方塊，在 [選項] 頁面的 [將資料庫檔案還原為] 方格中變更檔案位置。</span><span class="sxs-lookup"><span data-stu-id="17af5-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], change the file locations in the **Restore the database files as** grid of the **Restore Database Options** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17af5-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17af5-124">See Also</span></span>  
 <span data-ttu-id="17af5-125">[將資料庫還原到新位置 &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="17af5-125">[Restore a Database to a New Location &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="17af5-126">[將檔案還原到新的位置 &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="17af5-126">[Restore Files to a New Location &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span></span>  
 [<span data-ttu-id="17af5-127">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="17af5-127">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
