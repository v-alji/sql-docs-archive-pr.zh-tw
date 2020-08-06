---
title: 更新統計資料工作 (維護計畫) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.statistics.f1
helpviewer_keywords:
- Updates Statistics Task dialog box
ms.assetid: 22902fd0-eb39-4f18-af94-3fcb69d2a3a4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 486ef2da96785ed200900f497435117ef6437cb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606837"
---
# <a name="update-statistics-task-maintenance-plan"></a><span data-ttu-id="ccd04-102">更新統計資料工作 (維護計畫)</span><span class="sxs-lookup"><span data-stu-id="ccd04-102">Update Statistics Task (Maintenance Plan)</span></span>
  <span data-ttu-id="ccd04-103">使用 [更新統計資料工作] 對話方塊，更新資料表及索引中資料的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資訊。</span><span class="sxs-lookup"><span data-stu-id="ccd04-103">Use the **Update Statistics Task** dialog to update [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] information about the data in the tables and indexes.</span></span> <span data-ttu-id="ccd04-104">此工作針對資料庫中使用者資料表所建立的每個索引，重新取樣散發統計資料。</span><span class="sxs-lookup"><span data-stu-id="ccd04-104">This task resamples the distribution statistics of each index created on user tables in the database.</span></span> <span data-ttu-id="ccd04-105">在處理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 陳述式的期間， [!INCLUDE[tsql](../../includes/tsql-md.md)] 會使用散發統計資料來最佳化資料表的導覽。</span><span class="sxs-lookup"><span data-stu-id="ccd04-105">The distribution statistics are used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to optimize navigation through tables during the processing of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="ccd04-106">若要自動建立散發統計資料， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會在每個索引的對應資料表中，定期地取樣資料。</span><span class="sxs-lookup"><span data-stu-id="ccd04-106">To build the distribution statistics automatically, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodically samples the data in the corresponding table for each index.</span></span> <span data-ttu-id="ccd04-107">取樣大小會視資料表的資料列數與資料修改的頻率而定。</span><span class="sxs-lookup"><span data-stu-id="ccd04-107">This size of the sample is based on the number of rows in the table and the frequency of data modification.</span></span> <span data-ttu-id="ccd04-108">使用此選項即可使用資料表中指定的資料百分比執行其他取樣。</span><span class="sxs-lookup"><span data-stu-id="ccd04-108">Use this option to perform an additional sampling using the specified percentage of data in the tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ccd04-109">會使用此資訊來建立更好的查詢計畫。</span><span class="sxs-lookup"><span data-stu-id="ccd04-109">uses this information to create better query plans.</span></span>  
  
 <span data-ttu-id="ccd04-110">此工作會執行 UPDATE STATISTICS 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ccd04-110">This task executes the UPDATE STATISTICS statement.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ccd04-111">選項。</span><span class="sxs-lookup"><span data-stu-id="ccd04-111">Options</span></span>  
 <span data-ttu-id="ccd04-112">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="ccd04-112">**Connection**</span></span>  
 <span data-ttu-id="ccd04-113">選取執行此工作時要使用的伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="ccd04-113">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="ccd04-114">**新增**</span><span class="sxs-lookup"><span data-stu-id="ccd04-114">**New**</span></span>  
 <span data-ttu-id="ccd04-115">建立新的伺服器連接，以便執行此工作時使用。</span><span class="sxs-lookup"><span data-stu-id="ccd04-115">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="ccd04-116">下面會描述 **[新增連接]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ccd04-116">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="ccd04-117">**資料庫**</span><span class="sxs-lookup"><span data-stu-id="ccd04-117">**Databases**</span></span>  
 <span data-ttu-id="ccd04-118">指定受此工作影響的資料庫。</span><span class="sxs-lookup"><span data-stu-id="ccd04-118">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="ccd04-119">**所有資料庫**</span><span class="sxs-lookup"><span data-stu-id="ccd04-119">**All databases**</span></span>  
  
     <span data-ttu-id="ccd04-120">產生維護計畫，針對所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫執行維護工作，但 tempdb 除外。</span><span class="sxs-lookup"><span data-stu-id="ccd04-120">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, except tempdb.</span></span>  
  
-   <span data-ttu-id="ccd04-121">**所有系統資料庫**</span><span class="sxs-lookup"><span data-stu-id="ccd04-121">**All system databases**</span></span>  
  
     <span data-ttu-id="ccd04-122">產生維護計畫，針對每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料庫執行維護工作，但 tempdb 除外。</span><span class="sxs-lookup"><span data-stu-id="ccd04-122">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except tempdb.</span></span> <span data-ttu-id="ccd04-123">不會針對使用者建立的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="ccd04-123">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="ccd04-124">**所有使用者資料庫**</span><span class="sxs-lookup"><span data-stu-id="ccd04-124">**All user databases**</span></span>  
  
     <span data-ttu-id="ccd04-125">產生維護計畫，針對所有使用者建立的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="ccd04-125">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="ccd04-126">不會對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料庫執行任何維護工作。</span><span class="sxs-lookup"><span data-stu-id="ccd04-126">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="ccd04-127">**這些特定的資料庫**</span><span class="sxs-lookup"><span data-stu-id="ccd04-127">**These specific databases**</span></span>  
  
     <span data-ttu-id="ccd04-128">產生維護計畫，只針對選取的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="ccd04-128">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="ccd04-129">如果選擇此選項，則必須在清單中至少選取一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="ccd04-129">At least one database in the list must be selected if this option is chosen.</span></span>  
  
 <span data-ttu-id="ccd04-130">**附註** 維護計畫只針對相容性層級設為 80 (含) 以上的資料庫來執行。</span><span class="sxs-lookup"><span data-stu-id="ccd04-130">**Note** Maintenance plans only run against databases set to compatibility level 80 or higher.</span></span> <span data-ttu-id="ccd04-131">不會顯示相容性層級設為 70 或更低的資料庫。</span><span class="sxs-lookup"><span data-stu-id="ccd04-131">Databases set to compatibility level 70 or lower are not displayed.</span></span>  
  
 <span data-ttu-id="ccd04-132">**Object**</span><span class="sxs-lookup"><span data-stu-id="ccd04-132">**Object**</span></span>  
 <span data-ttu-id="ccd04-133">限制 [選取範圍] 格線僅顯示資料表、檢視或兩者。</span><span class="sxs-lookup"><span data-stu-id="ccd04-133">Limit the **Selection** grid to display tables, views, or both.</span></span>  
  
 <span data-ttu-id="ccd04-134">**選取範圍**</span><span class="sxs-lookup"><span data-stu-id="ccd04-134">**Selection**</span></span>  
 <span data-ttu-id="ccd04-135">指定受此工作影響的資料表或索引。</span><span class="sxs-lookup"><span data-stu-id="ccd04-135">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="ccd04-136">[物件] 方塊中的 **[資料表和檢視]** 為選取狀態時無法使用。</span><span class="sxs-lookup"><span data-stu-id="ccd04-136">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
 <span data-ttu-id="ccd04-137">**所有現有的統計資料**</span><span class="sxs-lookup"><span data-stu-id="ccd04-137">**All existing statistics**</span></span>  
 <span data-ttu-id="ccd04-138">同時更新資料行與索引的統計資料。</span><span class="sxs-lookup"><span data-stu-id="ccd04-138">Update statistics for both columns and indexes.</span></span>  
  
 <span data-ttu-id="ccd04-139">**僅限資料行統計資料**</span><span class="sxs-lookup"><span data-stu-id="ccd04-139">**Column statistics only**</span></span>  
 <span data-ttu-id="ccd04-140">僅更新資料行統計資料。</span><span class="sxs-lookup"><span data-stu-id="ccd04-140">Only update column statistics.</span></span>  
  
 <span data-ttu-id="ccd04-141">**僅限索引統計資料**</span><span class="sxs-lookup"><span data-stu-id="ccd04-141">**Index statistics only**</span></span>  
 <span data-ttu-id="ccd04-142">僅更新索引統計資料。</span><span class="sxs-lookup"><span data-stu-id="ccd04-142">Only update index statistics.</span></span>  
  
 <span data-ttu-id="ccd04-143">**掃描類型**</span><span class="sxs-lookup"><span data-stu-id="ccd04-143">**Scan type**</span></span>  
 <span data-ttu-id="ccd04-144">用來蒐集更新統計資料的掃描類型。</span><span class="sxs-lookup"><span data-stu-id="ccd04-144">Type of scan used to gather updated statistics.</span></span>  
  
 <span data-ttu-id="ccd04-145">**完整掃描**</span><span class="sxs-lookup"><span data-stu-id="ccd04-145">**Full scan**</span></span>  
 <span data-ttu-id="ccd04-146">讀取資料表或檢視中的所有資料列來蒐集統計資料。</span><span class="sxs-lookup"><span data-stu-id="ccd04-146">Read all rows in the table or view to gather the statistics.</span></span>  
  
 <span data-ttu-id="ccd04-147">**取樣者**</span><span class="sxs-lookup"><span data-stu-id="ccd04-147">**Sample by**</span></span>  
 <span data-ttu-id="ccd04-148">當收集較大資料表或檢視的統計資料時，指定要取樣的資料表或索引檢視百分比或資料列數。</span><span class="sxs-lookup"><span data-stu-id="ccd04-148">Specify the percentage of the table or indexed view, or the number of rows to sample when collecting statistics for larger tables or views.</span></span>  
  
 <span data-ttu-id="ccd04-149">**檢視 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="ccd04-149">**View T-SQL**</span></span>  
 <span data-ttu-id="ccd04-150">根據選取的選項，檢視此工作在伺服器上執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ccd04-150">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ccd04-151">受影響的物件數目較為大量時，會多花一些時間才會顯示。</span><span class="sxs-lookup"><span data-stu-id="ccd04-151">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="ccd04-152">新增連接對話方塊</span><span class="sxs-lookup"><span data-stu-id="ccd04-152">New Connection Dialog Box</span></span>  
 <span data-ttu-id="ccd04-153">**連線名稱**</span><span class="sxs-lookup"><span data-stu-id="ccd04-153">**Connection name**</span></span>  
 <span data-ttu-id="ccd04-154">輸入新連接的名稱。</span><span class="sxs-lookup"><span data-stu-id="ccd04-154">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="ccd04-155">**選取或輸入伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="ccd04-155">**Select or enter a server name**</span></span>  
 <span data-ttu-id="ccd04-156">選取執行此工作時要連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="ccd04-156">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="ccd04-157">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="ccd04-157">**Refresh**</span></span>  
 <span data-ttu-id="ccd04-158">重新整理可用的伺服器清單。</span><span class="sxs-lookup"><span data-stu-id="ccd04-158">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="ccd04-159">**輸入要登入到伺服器的資訊**</span><span class="sxs-lookup"><span data-stu-id="ccd04-159">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="ccd04-160">指定如何對伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="ccd04-160">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="ccd04-161">**使用 Windows 整合式安全性**</span><span class="sxs-lookup"><span data-stu-id="ccd04-161">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="ccd04-162">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 驗證連線到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ccd04-162">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="ccd04-163">**使用特定的使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="ccd04-163">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="ccd04-164">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連線到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ccd04-164">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="ccd04-165">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="ccd04-165">This option is not available.</span></span>  
  
 <span data-ttu-id="ccd04-166">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="ccd04-166">**User name**</span></span>  
 <span data-ttu-id="ccd04-167">提供驗證時要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="ccd04-167">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="ccd04-168">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="ccd04-168">This option is not available.</span></span>  
  
 <span data-ttu-id="ccd04-169">**密碼**</span><span class="sxs-lookup"><span data-stu-id="ccd04-169">**Password**</span></span>  
 <span data-ttu-id="ccd04-170">提供驗證時要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="ccd04-170">Provide a password to use when authenticating.</span></span> <span data-ttu-id="ccd04-171">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="ccd04-171">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccd04-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccd04-172">See Also</span></span>  
 [<span data-ttu-id="ccd04-173">UPDATE STATISTICS &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ccd04-173">UPDATE STATISTICS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/update-statistics-transact-sql)  
  
  
