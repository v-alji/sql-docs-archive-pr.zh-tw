---
title: 資料庫屬性 (檔案群組頁面) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.filegroups.f1
ms.assetid: 8d06e859-73dd-4019-b6e8-99c5c5297697
author: stevestein
ms.author: sstein
ms.openlocfilehash: d0546a17491ed5d3b36890a605c5faa922c24fe6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595102"
---
# <a name="database-properties-filegroups-page"></a><span data-ttu-id="043bf-102">資料庫屬性 (檔案群組頁面)</span><span class="sxs-lookup"><span data-stu-id="043bf-102">Database Properties (Filegroups Page)</span></span>
  <span data-ttu-id="043bf-103">使用此頁面來檢視檔案群組或將新的檔案群組加入選取的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="043bf-103">Use this page to view the filegroups or add a new filegroup to the selected database.</span></span> <span data-ttu-id="043bf-104">檔案群組類型分成「資料列」檔案群組、FILESTREAM 資料和記憶體最佳化檔案群組。</span><span class="sxs-lookup"><span data-stu-id="043bf-104">Filegroup types are separated into *row* filegroups, FILESTREAM data, and memory-optimized filegroups.</span></span>  
  
 <span data-ttu-id="043bf-105">資料列檔案群組包含一般的資料和記錄檔。</span><span class="sxs-lookup"><span data-stu-id="043bf-105">Row filegroups contain regular data and log files.</span></span> <span data-ttu-id="043bf-106">FILESTREAM 資料檔案群組包含 FILESTREAM 資料檔案。</span><span class="sxs-lookup"><span data-stu-id="043bf-106">FILESTREAM data filegroups contain FILESTREAM data files.</span></span> <span data-ttu-id="043bf-107">當您使用 FILESTREAM 儲存體時，這些資料檔案會儲存有關二進位大型物件 (BLOB) 資料如何儲存在檔案系統上的資訊。</span><span class="sxs-lookup"><span data-stu-id="043bf-107">These data files store information about how binary large object (BLOB) data is stored on the file system when you are using FILESTREAM storage.</span></span> <span data-ttu-id="043bf-108">對於這兩種類型的檔案群組而言，選項都是相同的。</span><span class="sxs-lookup"><span data-stu-id="043bf-108">The options are the same for both types of filegroups.</span></span>  
  
 <span data-ttu-id="043bf-109">如果未啟用 FILESTREAM，將無法使用 [Filestream] 區段。</span><span class="sxs-lookup"><span data-stu-id="043bf-109">If FILESTREAM is not enabled, the **Filestream** section will not be available.</span></span> <span data-ttu-id="043bf-110">您可以使用 [伺服器屬性 (進階頁面)](../../database-engine/configure-windows/server-properties-advanced-page.md)來啟用 FILESTREAM 儲存體。</span><span class="sxs-lookup"><span data-stu-id="043bf-110">You can enable FILESTREAM storage by using [Server Properties (Advanced Page)](../../database-engine/configure-windows/server-properties-advanced-page.md).</span></span>  
  
 <span data-ttu-id="043bf-111">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如何使用資料列檔案群組的相關資訊，請參閱 [資料庫檔案與檔案群組](database-files-and-filegroups.md)。</span><span class="sxs-lookup"><span data-stu-id="043bf-111">For information about how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses row filegroups, see [Database Files and Filegroups](database-files-and-filegroups.md).</span></span> <span data-ttu-id="043bf-112">如需 FILESTREAM 資料和檔案群組的詳細資訊，請參閱 [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="043bf-112">For more information about FILESTREAM data and filegroups, see [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md).</span></span>  
  
 <span data-ttu-id="043bf-113">記憶體最佳化檔案群組是讓資料庫包含一個或多個記憶體最佳化資料表的必要條件。</span><span class="sxs-lookup"><span data-stu-id="043bf-113">Memory-optimized file groups are required for a database to contain one or more memory-optimized tables.</span></span>  
  
## <a name="row-and-filestream-data-filegroup-options"></a><span data-ttu-id="043bf-114">資料列和 FILESTREAM 資料檔案群組選項</span><span class="sxs-lookup"><span data-stu-id="043bf-114">Row and FILESTREAM Data Filegroup Options</span></span>  
 <span data-ttu-id="043bf-115">**名稱**</span><span class="sxs-lookup"><span data-stu-id="043bf-115">**Name**</span></span>  
 <span data-ttu-id="043bf-116">輸入檔案群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="043bf-116">Enter the name of the filegroup.</span></span>  
  
 <span data-ttu-id="043bf-117">**檔案**</span><span class="sxs-lookup"><span data-stu-id="043bf-117">**Files**</span></span>  
 <span data-ttu-id="043bf-118">顯示檔案群組中的檔案計數。</span><span class="sxs-lookup"><span data-stu-id="043bf-118">Displays the count of files in the filegroup.</span></span>  
  
 <span data-ttu-id="043bf-119">**唯讀**</span><span class="sxs-lookup"><span data-stu-id="043bf-119">**Read-only**</span></span>  
 <span data-ttu-id="043bf-120">選取即可將檔案群組設定為唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="043bf-120">Select to set the filegroup to a read-only status.</span></span>  
  
 <span data-ttu-id="043bf-121">**預設值**</span><span class="sxs-lookup"><span data-stu-id="043bf-121">**Default**</span></span>  
 <span data-ttu-id="043bf-122">選取即可讓這個檔案群組成為預設的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="043bf-122">Select to make this filegroup the default filegroup.</span></span> <span data-ttu-id="043bf-123">您可以有一個預設的資料列檔案群組，以及一個預設的 FILESTREAM 資料檔案群組。</span><span class="sxs-lookup"><span data-stu-id="043bf-123">You can have one default filegroup for rows and one default filegroup for FILESTREAM data.</span></span>  
  
 <span data-ttu-id="043bf-124">**加入**</span><span class="sxs-lookup"><span data-stu-id="043bf-124">**Add**</span></span>  
 <span data-ttu-id="043bf-125">將新的空白資料列加入列出資料庫之檔案群組的方格中。</span><span class="sxs-lookup"><span data-stu-id="043bf-125">Adds a new blank row to the grid listing filegroups for the database.</span></span>  
  
 <span data-ttu-id="043bf-126">**移除**</span><span class="sxs-lookup"><span data-stu-id="043bf-126">**Remove**</span></span>  
 <span data-ttu-id="043bf-127">從方格中移除選取的檔案群組資料列。</span><span class="sxs-lookup"><span data-stu-id="043bf-127">Removes the selected filegroup row from the grid.</span></span>  
  
## <a name="memory-optimized-data-filegroup-options"></a><span data-ttu-id="043bf-128">記憶體最佳化資料檔案群組選項</span><span class="sxs-lookup"><span data-stu-id="043bf-128">Memory-Optimized Data Filegroup Options</span></span>  
 <span data-ttu-id="043bf-129">**名稱**</span><span class="sxs-lookup"><span data-stu-id="043bf-129">**Name**</span></span>  
 <span data-ttu-id="043bf-130">輸入記憶體最佳化檔案群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="043bf-130">Enter the name of the memory-optimized filegroup.</span></span>  
  
 <span data-ttu-id="043bf-131">**Filestream 檔案**</span><span class="sxs-lookup"><span data-stu-id="043bf-131">**Filestream Files**</span></span>  
 <span data-ttu-id="043bf-132">顯示記憶體最佳化資料檔案群組中的檔案 (容器) 數目。</span><span class="sxs-lookup"><span data-stu-id="043bf-132">Displays the number of files (containers) in the memory-optimized data filegroup.</span></span> <span data-ttu-id="043bf-133">您可以在 [檔案] 頁面中加入容器。</span><span class="sxs-lookup"><span data-stu-id="043bf-133">You can add containers in the **Files** page.</span></span>  
  
 <span data-ttu-id="043bf-134">**加入**</span><span class="sxs-lookup"><span data-stu-id="043bf-134">**Add**</span></span>  
 <span data-ttu-id="043bf-135">將新的空白資料列加入列出資料庫之檔案群組的方格中。</span><span class="sxs-lookup"><span data-stu-id="043bf-135">Adds a new blank row to the grid listing filegroups for the database.</span></span>  
  
 <span data-ttu-id="043bf-136">**移除**</span><span class="sxs-lookup"><span data-stu-id="043bf-136">**Remove**</span></span>  
 <span data-ttu-id="043bf-137">從方格中移除選取的檔案群組資料列。</span><span class="sxs-lookup"><span data-stu-id="043bf-137">Removes the selected filegroup row from the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="043bf-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="043bf-138">See Also</span></span>  
 <span data-ttu-id="043bf-139">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="043bf-139">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="043bf-140">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="043bf-140">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
