---
title: 維護清除工作 (維護計畫) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.cleanup.f1
helpviewer_keywords:
- Maintenance Cleanup Task dialog box
ms.assetid: 022b679c-6799-4c13-9185-814224a20412
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9023881ff5cf5ba5ddd8c61aa179c5881162bf44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596678"
---
# <a name="maintenance-cleanup-task-maintenance-plan"></a><span data-ttu-id="d875e-102">維護清除工作 (維護計畫)</span><span class="sxs-lookup"><span data-stu-id="d875e-102">Maintenance Cleanup Task (Maintenance Plan)</span></span>
  <span data-ttu-id="d875e-103">使用 **[維護清除工作]** ，即可移除與維護計畫相關的舊檔案 (包括維護計畫和資料庫備份檔案所建立的文字報表)。</span><span class="sxs-lookup"><span data-stu-id="d875e-103">Use the **Maintenance Cleanup Task** to remove old files related to maintenance plans, including text reports created by maintenance plans and database backup files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d875e-104">維護清除工作不會自動刪除所指定目錄之子資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="d875e-104">The Maintenance Cleanup task does not automatically delete files in the subfolders of the specified directory.</span></span> <span data-ttu-id="d875e-105">這項功能可降低利用「維護清除」工作刪除檔案這類惡意攻擊的可能性。</span><span class="sxs-lookup"><span data-stu-id="d875e-105">This feature reduces the possibility of a malicious attack that uses the Maintenance Cleanup task to delete files.</span></span> <span data-ttu-id="d875e-106">如果您要刪除第一層子資料夾中的檔案，必須選取 [包含第一層的子資料夾]。</span><span class="sxs-lookup"><span data-stu-id="d875e-106">If you want to delete files in first-level subfolders, you must select **Include first-level subfolders**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d875e-107">選項。</span><span class="sxs-lookup"><span data-stu-id="d875e-107">Options</span></span>  
 <span data-ttu-id="d875e-108">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="d875e-108">**Connection**</span></span>  
 <span data-ttu-id="d875e-109">顯示目前的連接。</span><span class="sxs-lookup"><span data-stu-id="d875e-109">Displays the current connection.</span></span>  
  
 <span data-ttu-id="d875e-110">**新增**</span><span class="sxs-lookup"><span data-stu-id="d875e-110">**New**</span></span>  
 <span data-ttu-id="d875e-111">建立新的伺服器連接，以便執行此工作時使用。</span><span class="sxs-lookup"><span data-stu-id="d875e-111">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="d875e-112">下面會描述 **[新增連接]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d875e-112">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="d875e-113">**備份檔案**</span><span class="sxs-lookup"><span data-stu-id="d875e-113">**Backup files**</span></span>  
 <span data-ttu-id="d875e-114">刪除備份檔案。</span><span class="sxs-lookup"><span data-stu-id="d875e-114">Delete backup files.</span></span>  
  
 <span data-ttu-id="d875e-115">**維護計畫文字報表**</span><span class="sxs-lookup"><span data-stu-id="d875e-115">**Maintenance Plan text reports**</span></span>  
 <span data-ttu-id="d875e-116">刪除先前執行之維護計畫的文字報表。</span><span class="sxs-lookup"><span data-stu-id="d875e-116">Delete text reports of previously run maintenance plans.</span></span>  
  
 <span data-ttu-id="d875e-117">**刪除特定檔案**</span><span class="sxs-lookup"><span data-stu-id="d875e-117">**Delete specific file**</span></span>  
 <span data-ttu-id="d875e-118">刪除 [檔案名稱] 方塊中提供的特定檔案。</span><span class="sxs-lookup"><span data-stu-id="d875e-118">Delete the specific file provided in the **File name** box.</span></span>  
  
 <span data-ttu-id="d875e-119">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="d875e-119">**File name**</span></span>  
 <span data-ttu-id="d875e-120">要刪除的檔案路徑與名稱。</span><span class="sxs-lookup"><span data-stu-id="d875e-120">Path and name of the file to be deleted.</span></span>  
  
 <span data-ttu-id="d875e-121">**根據副檔名搜尋資料夾並刪除檔案**</span><span class="sxs-lookup"><span data-stu-id="d875e-121">**Search folder and delete files based on an extension**</span></span>  
 <span data-ttu-id="d875e-122">刪除指定之資料夾中具有指定之副檔名的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="d875e-122">Delete all files with the specified extension in the specified folder.</span></span> <span data-ttu-id="d875e-123">使用此方法即可同時刪除多個檔案，例如 Tuesday 資料夾中副檔名為 .bak 的所有備份檔案。</span><span class="sxs-lookup"><span data-stu-id="d875e-123">Use this to delete multiple files at once, such as all backup files with the .bak extension, in the Tuesday folder.</span></span>  
  
 <span data-ttu-id="d875e-124">**資料夾**</span><span class="sxs-lookup"><span data-stu-id="d875e-124">**Folder**</span></span>  
 <span data-ttu-id="d875e-125">包含要刪除檔案的資料夾路徑與名稱。</span><span class="sxs-lookup"><span data-stu-id="d875e-125">Path and name of the folder containing the files to be deleted.</span></span>  
  
 <span data-ttu-id="d875e-126">**副檔名**</span><span class="sxs-lookup"><span data-stu-id="d875e-126">**File extension**</span></span>  
 <span data-ttu-id="d875e-127">提供要刪除的檔案副檔名。</span><span class="sxs-lookup"><span data-stu-id="d875e-127">Provide the file extension of the files to be deleted.</span></span>  
  
 <span data-ttu-id="d875e-128">**包含第一層的子資料夾**</span><span class="sxs-lookup"><span data-stu-id="d875e-128">**Include first-level subfolders**</span></span>  
 <span data-ttu-id="d875e-129">從 [資料夾] 底下的第一層子資料夾中，刪除具有 [副檔名] 中所指定之副檔名的檔案。</span><span class="sxs-lookup"><span data-stu-id="d875e-129">Delete files with the extension specified for **File extension** from first-level subfolders under **Folder**.</span></span>  
  
 <span data-ttu-id="d875e-130">**在工作執行階段依據檔案存在時間刪除檔案**</span><span class="sxs-lookup"><span data-stu-id="d875e-130">**Delete files based on the age of the file at task run time**</span></span>  
 <span data-ttu-id="d875e-131">在 [刪除早於下列時限的檔案] 方塊中提供數字以及時間單位，以指定您要刪除之檔案的最低存在時間。</span><span class="sxs-lookup"><span data-stu-id="d875e-131">Specify the minimum age of the files that you want to delete by providing a number, and unit of time in the **Delete files older than the following** box.</span></span>  
  
 <span data-ttu-id="d875e-132">**刪除早於下列時限的檔案**</span><span class="sxs-lookup"><span data-stu-id="d875e-132">**Delete files older than the following**</span></span>  
 <span data-ttu-id="d875e-133">提供數字以及時間單位 (日、週、月或年)，以指定您要刪除之檔案的最低存在時間。</span><span class="sxs-lookup"><span data-stu-id="d875e-133">Specify the minimum age of the files that you want to delete by providing a number, and unit of time (Day, Week, Month, or Year).</span></span> <span data-ttu-id="d875e-134">存在時間超過指定時間的檔案會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="d875e-134">Files older than the time frame specified will be deleted.</span></span>  
  
 <span data-ttu-id="d875e-135">**檢視 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="d875e-135">**View T-SQL**</span></span>  
 <span data-ttu-id="d875e-136">根據選取的選項，檢視此工作在伺服器上執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d875e-136">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d875e-137">受影響的物件數目較為大量時，會多花一些時間才會顯示。</span><span class="sxs-lookup"><span data-stu-id="d875e-137">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="d875e-138">新增連接對話方塊</span><span class="sxs-lookup"><span data-stu-id="d875e-138">New Connection Dialog Box</span></span>  
 <span data-ttu-id="d875e-139">**連線名稱**</span><span class="sxs-lookup"><span data-stu-id="d875e-139">**Connection name**</span></span>  
 <span data-ttu-id="d875e-140">輸入新連接的名稱。</span><span class="sxs-lookup"><span data-stu-id="d875e-140">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="d875e-141">**選取或輸入伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="d875e-141">**Select or enter a server name**</span></span>  
 <span data-ttu-id="d875e-142">選取執行此工作時要連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="d875e-142">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="d875e-143">**...**</span><span class="sxs-lookup"><span data-stu-id="d875e-143">**...**</span></span>  
 <span data-ttu-id="d875e-144">選取此項以檢視可用伺服器的清單。</span><span class="sxs-lookup"><span data-stu-id="d875e-144">Select to view the list of available servers.</span></span>  
  
 <span data-ttu-id="d875e-145">**輸入要登入到伺服器的資訊**</span><span class="sxs-lookup"><span data-stu-id="d875e-145">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="d875e-146">指定如何對伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="d875e-146">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="d875e-147">**使用 Windows 整合式安全性**</span><span class="sxs-lookup"><span data-stu-id="d875e-147">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="d875e-148">使用 Microsoft Windows 驗證來連接 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d875e-148">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with Microsoft Windows Authentication.</span></span>  
  
 <span data-ttu-id="d875e-149">**使用特定的使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="d875e-149">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="d875e-150">使用 SQL Server 驗證來連接 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d875e-150">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] using SQL Server Authentication.</span></span> <span data-ttu-id="d875e-151">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="d875e-151">This option is not available.</span></span>  
  
 <span data-ttu-id="d875e-152">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="d875e-152">**User name**</span></span>  
 <span data-ttu-id="d875e-153">提供驗證時要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="d875e-153">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="d875e-154">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="d875e-154">This option is not available.</span></span>  
  
 <span data-ttu-id="d875e-155">**密碼**</span><span class="sxs-lookup"><span data-stu-id="d875e-155">**Password**</span></span>  
 <span data-ttu-id="d875e-156">提供驗證時要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="d875e-156">Provide a password to use when authenticating.</span></span> <span data-ttu-id="d875e-157">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="d875e-157">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d875e-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d875e-158">See Also</span></span>  
 [<span data-ttu-id="d875e-159">維護計畫</span><span class="sxs-lookup"><span data-stu-id="d875e-159">Maintenance Plans</span></span>](maintenance-plans.md)  
  
  
