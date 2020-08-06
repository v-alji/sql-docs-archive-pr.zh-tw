---
title: 壓縮資料庫工作 (維護計畫) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.shrink.f1
- Shrink Database Task
- Shrink Database(s) Task
helpviewer_keywords:
- Shrink Database Task dialog box
ms.assetid: a9874cac-cded-4145-9c38-8aafd267dbee
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b8ee6060a4ee6ca3272434cf3d9115638a675e62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699535"
---
# <a name="shrink-database-task-maintenance-plan"></a><span data-ttu-id="24e77-102">壓縮資料庫工作 (維護計畫)</span><span class="sxs-lookup"><span data-stu-id="24e77-102">Shrink Database Task (Maintenance Plan)</span></span>
  <span data-ttu-id="24e77-103">使用 [壓縮資料庫工作] 對話方塊來建立嘗試縮減選取之資料庫大小的工作。</span><span class="sxs-lookup"><span data-stu-id="24e77-103">Use the **Shrink Database Task** dialog to create a task that attempts to reduce the size of the selected databases.</span></span> <span data-ttu-id="24e77-104">使用下列選項以決定將資料庫縮小之後，要在資料庫中保留的未使用空間數量 (百分比愈大，資料庫可縮小的程度愈小)。</span><span class="sxs-lookup"><span data-stu-id="24e77-104">Use the options below to determine the amount of unused space to remain in the database after the database is shrunk (the larger the percentage, the less the database can shrink).</span></span> <span data-ttu-id="24e77-105">這個值是根據資料庫中實際資料的百分比而取得。</span><span class="sxs-lookup"><span data-stu-id="24e77-105">The value is based on the percentage of the actual data in the database.</span></span> <span data-ttu-id="24e77-106">例如：一個 100 MB 的資料庫，包含 60 MB 的資料及 40 MB 的可用空間，設定可用空間的百分比為 50 時，則結果為 60 MB 的資料及 30 MB 的可用空間 (因為 60 MB 的百分之 50 為 30 MB)。</span><span class="sxs-lookup"><span data-stu-id="24e77-106">For example, a 100-MB database containing 60 MB of data and 40 MB of free space, with a free space percentage of 50 percent, would result in 60 MB of data and 30 MB of free space (because 50 percent of 60 MB is 30 MB).</span></span> <span data-ttu-id="24e77-107">只有資料庫中超出的空間會被刪除。</span><span class="sxs-lookup"><span data-stu-id="24e77-107">Only excess space in the database is eliminated.</span></span> <span data-ttu-id="24e77-108">有效的數值範圍為 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="24e77-108">Valid values are from 0 through 100.</span></span>  
  
 <span data-ttu-id="24e77-109">將資料頁面從檔案結尾移到靠近檔案前端的未使用空間，以壓縮資料並復原儲存空間。</span><span class="sxs-lookup"><span data-stu-id="24e77-109">Shrinking data files recovers space by moving pages of data from the end of the file to unoccupied space closer to the front of the file.</span></span> <span data-ttu-id="24e77-110">當檔案結尾建立了足夠的可用空間後，檔案結尾的資料頁面便可取消配置並返回檔案系統。</span><span class="sxs-lookup"><span data-stu-id="24e77-110">When enough free space is created at the end of the file, data pages at end of the file can deallocated and returned to the file system.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="24e77-111">為壓縮檔案所移動的資料可散佈至檔案中的任何可用位置。</span><span class="sxs-lookup"><span data-stu-id="24e77-111">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="24e77-112">如此會造成索引片段，並可能導致大範圍之索引搜尋的查詢效能變慢。</span><span class="sxs-lookup"><span data-stu-id="24e77-112">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="24e77-113">若要消除資料片段，可考慮在壓縮之後重建該檔案的索引。</span><span class="sxs-lookup"><span data-stu-id="24e77-113">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
 <span data-ttu-id="24e77-114">此工作會執行 DBCC SHRINKDATABASE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="24e77-114">This task executes the DBCC SHRINKDATABASE statement.</span></span>  
  
## <a name="options"></a><span data-ttu-id="24e77-115">選項。</span><span class="sxs-lookup"><span data-stu-id="24e77-115">Options</span></span>  
 <span data-ttu-id="24e77-116">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="24e77-116">**Connection**</span></span>  
 <span data-ttu-id="24e77-117">選取執行此工作時要使用的伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="24e77-117">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="24e77-118">**新增**</span><span class="sxs-lookup"><span data-stu-id="24e77-118">**New**</span></span>  
 <span data-ttu-id="24e77-119">建立新的伺服器連接，以便執行此工作時使用。</span><span class="sxs-lookup"><span data-stu-id="24e77-119">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="24e77-120">下面會描述 **[新增連接]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="24e77-120">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="24e77-121">**資料庫**</span><span class="sxs-lookup"><span data-stu-id="24e77-121">**Databases**</span></span>  
 <span data-ttu-id="24e77-122">指定受此工作影響的資料庫。</span><span class="sxs-lookup"><span data-stu-id="24e77-122">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="24e77-123">**所有資料庫**</span><span class="sxs-lookup"><span data-stu-id="24e77-123">**All databases**</span></span>  
  
     <span data-ttu-id="24e77-124">產生維護計畫，針對所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫執行維護工作，但 tempdb 除外。</span><span class="sxs-lookup"><span data-stu-id="24e77-124">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except tempdb.</span></span>  
  
-   <span data-ttu-id="24e77-125">**所有系統資料庫**</span><span class="sxs-lookup"><span data-stu-id="24e77-125">**All system databases**</span></span>  
  
     <span data-ttu-id="24e77-126">產生維護計畫，針對每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料庫執行維護工作，但 tempdb 除外。</span><span class="sxs-lookup"><span data-stu-id="24e77-126">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except tempdb.</span></span> <span data-ttu-id="24e77-127">不會針對使用者建立的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="24e77-127">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="24e77-128">**所有使用者資料庫**</span><span class="sxs-lookup"><span data-stu-id="24e77-128">**All user databases**</span></span>  
  
     <span data-ttu-id="24e77-129">產生維護計畫，針對所有使用者建立的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="24e77-129">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="24e77-130">不會對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料庫執行任何維護工作。</span><span class="sxs-lookup"><span data-stu-id="24e77-130">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="24e77-131">**下列資料庫**</span><span class="sxs-lookup"><span data-stu-id="24e77-131">**These databases**</span></span>  
  
     <span data-ttu-id="24e77-132">產生維護計畫，只針對選取的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="24e77-132">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="24e77-133">如果選擇此選項，則必須在清單中至少選取一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="24e77-133">At least one database in the list must be selected if this option is chosen.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="24e77-134">維護計畫只針對相容性層級設為 80 (含) 以上的資料庫來執行。</span><span class="sxs-lookup"><span data-stu-id="24e77-134">Maintenance plans only run against databases set to compatibility level 80 or higher.</span></span> <span data-ttu-id="24e77-135">不會顯示相容性層級設為 70 或更低的資料庫。</span><span class="sxs-lookup"><span data-stu-id="24e77-135">Databases set to compatibility level 70 or lower are not displayed.</span></span>  
  
 <span data-ttu-id="24e77-136">**壓縮資料庫當它超過**</span><span class="sxs-lookup"><span data-stu-id="24e77-136">**Shrink database when it grows beyond**</span></span>  
 <span data-ttu-id="24e77-137">指定使工作執行的大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="24e77-137">Specify the size in megabytes that causes the task to execute.</span></span>  
  
 <span data-ttu-id="24e77-138">**壓縮後要保持的可用空間量**</span><span class="sxs-lookup"><span data-stu-id="24e77-138">**Amount of free space to remain after shrink**</span></span>  
 <span data-ttu-id="24e77-139">當資料庫檔案中的可用空間達到此大小時停止壓縮。</span><span class="sxs-lookup"><span data-stu-id="24e77-139">Stop shrinking when free space in database files reaches this size.</span></span>  
  
 <span data-ttu-id="24e77-140">**檢視 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="24e77-140">**View T-SQL**</span></span>  
 <span data-ttu-id="24e77-141">根據選取的選項，檢視此工作在伺服器上執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="24e77-141">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="24e77-142">受影響的物件數目較為大量時，會多花一些時間才會顯示。</span><span class="sxs-lookup"><span data-stu-id="24e77-142">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="24e77-143">新增連接對話方塊</span><span class="sxs-lookup"><span data-stu-id="24e77-143">New Connection Dialog Box</span></span>  
 <span data-ttu-id="24e77-144">**連線名稱**</span><span class="sxs-lookup"><span data-stu-id="24e77-144">**Connection name**</span></span>  
 <span data-ttu-id="24e77-145">輸入新連接的名稱。</span><span class="sxs-lookup"><span data-stu-id="24e77-145">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="24e77-146">**選取或輸入伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="24e77-146">**Select or enter a server name**</span></span>  
 <span data-ttu-id="24e77-147">選取執行此工作時要連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="24e77-147">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="24e77-148">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="24e77-148">**Refresh**</span></span>  
 <span data-ttu-id="24e77-149">重新整理可用的伺服器清單。</span><span class="sxs-lookup"><span data-stu-id="24e77-149">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="24e77-150">**輸入要登入到伺服器的資訊**</span><span class="sxs-lookup"><span data-stu-id="24e77-150">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="24e77-151">指定如何對伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="24e77-151">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="24e77-152">**使用 Windows NT 整合式安全性**</span><span class="sxs-lookup"><span data-stu-id="24e77-152">**Use Windows NT Integrated security**</span></span>  
 <span data-ttu-id="24e77-153">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 驗證連線到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="24e77-153">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="24e77-154">**使用特定的使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="24e77-154">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="24e77-155">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連線到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="24e77-155">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="24e77-156">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="24e77-156">This option is not available.</span></span>  
  
 <span data-ttu-id="24e77-157">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="24e77-157">**User name**</span></span>  
 <span data-ttu-id="24e77-158">提供驗證時要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="24e77-158">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="24e77-159">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="24e77-159">This option is not available.</span></span>  
  
 <span data-ttu-id="24e77-160">**密碼**</span><span class="sxs-lookup"><span data-stu-id="24e77-160">**Password**</span></span>  
 <span data-ttu-id="24e77-161">提供驗證時要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="24e77-161">Provide a password to use when authenticating.</span></span> <span data-ttu-id="24e77-162">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="24e77-162">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e77-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24e77-163">See Also</span></span>  
 [<span data-ttu-id="24e77-164">DBCC SHRINKDATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="24e77-164">DBCC SHRINKDATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql)  
  
  
