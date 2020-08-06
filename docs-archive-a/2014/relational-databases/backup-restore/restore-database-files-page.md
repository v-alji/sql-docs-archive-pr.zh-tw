---
title: 還原資料庫 (檔案頁面) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoredb.files.f1 in the code
- sql12.swb.restoredb.files.f1
ms.assetid: 714c36ea-a9f9-43a4-99f9-a6f73d1baf8e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: edffd9454b51ea80a18311f735d29407f97f6eb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598462"
---
# <a name="restore-database-files-page"></a><span data-ttu-id="b4ea4-102">還原資料庫 (檔案頁面)</span><span class="sxs-lookup"><span data-stu-id="b4ea4-102">Restore Database (Files Page)</span></span>
  <span data-ttu-id="b4ea4-103">使用 **[還原資料庫]** 對話方塊的 **[檔案]** 頁面，管理資料庫中已選擇要還原的特定檔案。</span><span class="sxs-lookup"><span data-stu-id="b4ea4-103">Use the **Files** page of the **Restore Database** dialog box to manage the specific files you have chosen to restore within the database.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b4ea4-104">選項。</span><span class="sxs-lookup"><span data-stu-id="b4ea4-104">Options</span></span>  
  
### <a name="restore-database-files-as"></a><span data-ttu-id="b4ea4-105">將資料庫檔案還原為</span><span class="sxs-lookup"><span data-stu-id="b4ea4-105">Restore database files as</span></span>  
 <span data-ttu-id="b4ea4-106">用來指派和管理已還原之檔案的新檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="b4ea4-106">Use to assign and manage the new file path to the restored files.</span></span>  
  
 <span data-ttu-id="b4ea4-107">**將所有檔案重新放置到資料夾**</span><span class="sxs-lookup"><span data-stu-id="b4ea4-107">**Relocate all files to folder**</span></span>  
 <span data-ttu-id="b4ea4-108">重新放置還原的檔案。</span><span class="sxs-lookup"><span data-stu-id="b4ea4-108">Relocates restored files.</span></span>  
  
|<span data-ttu-id="b4ea4-109">選項</span><span class="sxs-lookup"><span data-stu-id="b4ea4-109">Option</span></span>|<span data-ttu-id="b4ea4-110">描述</span><span class="sxs-lookup"><span data-stu-id="b4ea4-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b4ea4-111">**資料檔資料夾**</span><span class="sxs-lookup"><span data-stu-id="b4ea4-111">**Data file folder**</span></span>|<span data-ttu-id="b4ea4-112">輸入或搜尋還原的資料檔應該重新放置到的目標資料檔資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="b4ea4-112">Enter or search for the data file folder name that the restored data file or files should be relocated to.</span></span>|  
|<span data-ttu-id="b4ea4-113">**記錄檔資料夾**</span><span class="sxs-lookup"><span data-stu-id="b4ea4-113">**Log file folder**</span></span>|<span data-ttu-id="b4ea4-114">輸入或搜尋還原的記錄檔應該重新放置到的目標記錄檔資料夾。</span><span class="sxs-lookup"><span data-stu-id="b4ea4-114">Enter or search for the log file or files folder that the restored log file should be relocated to.</span></span>|  
  
 <span data-ttu-id="b4ea4-115">**邏輯檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="b4ea4-115">**Logical File Name**</span></span>  
 <span data-ttu-id="b4ea4-116">為每個要還原的資料庫檔案顯示一個資料列。</span><span class="sxs-lookup"><span data-stu-id="b4ea4-116">Displays one row for each database file to be restored.</span></span>  
  
 <span data-ttu-id="b4ea4-117">**檔案類型**</span><span class="sxs-lookup"><span data-stu-id="b4ea4-117">**File Type**</span></span>  
 <span data-ttu-id="b4ea4-118">顯示檔案類型。</span><span class="sxs-lookup"><span data-stu-id="b4ea4-118">Displays the file type.</span></span>  
  
 <span data-ttu-id="b4ea4-119">**原始檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="b4ea4-119">**Original File Name**</span></span>  
 <span data-ttu-id="b4ea4-120">顯示已還原之檔案的原始檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="b4ea4-120">Displays the original file path for the restored file.</span></span>  
  
 <span data-ttu-id="b4ea4-121">**還原成**</span><span class="sxs-lookup"><span data-stu-id="b4ea4-121">**Restore As**</span></span>  
 <span data-ttu-id="b4ea4-122">列出已還原的檔案另存的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="b4ea4-122">Lists the file names that the restored files are to be saved as.</span></span> <span data-ttu-id="b4ea4-123">輸入或搜尋適當的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="b4ea4-123">Enter or search for the appropriate file name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4ea4-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4ea4-124">See Also</span></span>  
 <span data-ttu-id="b4ea4-125">[還原資料庫 &#40;一般頁面&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="b4ea4-125">[Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="b4ea4-126">[還原資料庫 &#40;選項頁面&#41;](restore-database-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="b4ea4-126">[Restore Database &#40;Options Page&#41;](restore-database-options-page.md) </span></span>  
 <span data-ttu-id="b4ea4-127">[RESTORE 引數 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b4ea4-127">[RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span></span>  
 <span data-ttu-id="b4ea4-128">[定義磁帶機的邏輯備份裝置 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b4ea4-128">[Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span></span>  
 [<span data-ttu-id="b4ea4-129">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b4ea4-129">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
