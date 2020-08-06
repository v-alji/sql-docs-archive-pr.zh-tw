---
title: 檢視或變更收集組排程 (SQL Server Management Studio) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.collectionsetprop.uploads.f1
- sql12.swb.dc.collectionsetprop.general.f1
- sql12.swb.dc.collectionsetprop.description.f1
helpviewer_keywords:
- collection sets [SQL Server], changing schedules
- schedules [SQL Server], changing collection set
- collection sets [SQL Server], viewing schedules
- schedules [SQL Server], viewing collection set
ms.assetid: 26336c98-78c5-414f-8d6a-574fc3af60c4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2eb1acf0346b3e16bd1d54829abbc070e1d9d63b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599011"
---
# <a name="view-or-change-collection-set-schedules-sql-server-management-studio"></a><span data-ttu-id="a7b30-102">檢視或變更收集組排程 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="a7b30-102">View or Change Collection Set Schedules (SQL Server Management Studio)</span></span>
  <span data-ttu-id="a7b30-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]來檢視或變更收集組排程。</span><span class="sxs-lookup"><span data-stu-id="a7b30-103">You can view or change collection set schedules by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="a7b30-104">收集模式 (快取或非快取) 可決定您要如何對排程進行變更。</span><span class="sxs-lookup"><span data-stu-id="a7b30-104">The collection mode, cached or non-cached, determines how you can make changes to a schedule.</span></span> <span data-ttu-id="a7b30-105">快取模式會使用個別的排程來進行收集和上傳。</span><span class="sxs-lookup"><span data-stu-id="a7b30-105">Cached mode uses separate schedules for collection and upload.</span></span> <span data-ttu-id="a7b30-106">非快取模式會使用相同的排程來進行收集和上傳。</span><span class="sxs-lookup"><span data-stu-id="a7b30-106">Non-cached mode uses the same schedule for collection and upload.</span></span> <span data-ttu-id="a7b30-107">每一個系統資料收集組的收集模式類型如下：</span><span class="sxs-lookup"><span data-stu-id="a7b30-107">The type of collection mode for each of the System Datacollection sets is as follows:</span></span>  
  
-   <span data-ttu-id="a7b30-108">[磁碟使用量] 會使用非快取收集模式。</span><span class="sxs-lookup"><span data-stu-id="a7b30-108">**Disk Usage** uses non-cached collection mode.</span></span>  
  
-   <span data-ttu-id="a7b30-109">**[查詢統計資料]** 會使用快取收集模式。</span><span class="sxs-lookup"><span data-stu-id="a7b30-109">**Query Statistics** uses cached collection mode.</span></span>  
  
-   <span data-ttu-id="a7b30-110">**[伺服器活動]** 會使用快取收集模式。</span><span class="sxs-lookup"><span data-stu-id="a7b30-110">**Server Activity** uses cached collection mode.</span></span>  
  
### <a name="to-view-collection-set-schedules"></a><span data-ttu-id="a7b30-111">若要檢視收集組排程</span><span class="sxs-lookup"><span data-stu-id="a7b30-111">To view collection set schedules</span></span>  
  
1.  <span data-ttu-id="a7b30-112">在 [物件總管] 中，依序展開 **[管理]** 節點、 **[資料收集]** 和 **[系統資料收集組]** 。</span><span class="sxs-lookup"><span data-stu-id="a7b30-112">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="a7b30-113">以滑鼠右鍵按一下收集組名稱，然後按一下 [屬性] 開啟 [[資料收集組屬性]](#CollectionSet) 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a7b30-113">Right-click a collection set name, and then click **Properties** to open the [Data Collection Set Properties](#CollectionSet) dialog box.</span></span>  
  
### <a name="to-change-the-schedules-for-a-cached-mode-collection-set"></a><span data-ttu-id="a7b30-114">若要變更快取模式收集組的排程</span><span class="sxs-lookup"><span data-stu-id="a7b30-114">To change the schedules for a cached mode collection set</span></span>  
  
1.  <span data-ttu-id="a7b30-115">在 [物件總管] 中，依序展開 **[管理]** 節點、 **[資料收集]** 和 **[系統資料收集組]** 。</span><span class="sxs-lookup"><span data-stu-id="a7b30-115">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="a7b30-116">以滑鼠右鍵按一下使用快取模式的收集組，例如 [查詢統計資料]，然後按一下 [屬性] 開啟 [[資料收集組屬性]](#CollectionSet) 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a7b30-116">Right-click a collection set that uses cached mode, such as **Query Statistics**, and then click **Properties** to open the [Data Collection Set Properties](#CollectionSet) dialog box.</span></span>  
  
3.  <span data-ttu-id="a7b30-117">您可以在 **[一般]** 頁面上變更收集頻率。</span><span class="sxs-lookup"><span data-stu-id="a7b30-117">You can change the collection frequency on the **General** page.</span></span> <span data-ttu-id="a7b30-118">若要這樣做，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a7b30-118">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="a7b30-119">在詳細資料窗格中，按兩下針對 [收集項目] 資料表中 [收集頻率 (秒)] 資料行顯示的數字。</span><span class="sxs-lookup"><span data-stu-id="a7b30-119">In the details pane, double-click the number that is displayed for the **Collection Frequency (sec)** column in the **Collection items** table.</span></span>  
  
    2.  <span data-ttu-id="a7b30-120">若要增加或減少收集頻率，請輸入較低或較高的數字，然後按下 ENTER 儲存新的值。</span><span class="sxs-lookup"><span data-stu-id="a7b30-120">To increase or decrease the collection frequency, type a lower or higher number, and then press ENTER to store the new value.</span></span>  
  
4.  <span data-ttu-id="a7b30-121">若要變更收集組的現有上傳排程，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a7b30-121">To change the existing upload schedule for the collection set, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="a7b30-122">按一下 **[上傳]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="a7b30-122">Click the **Uploads** page.</span></span>  
  
    2.  <span data-ttu-id="a7b30-123">在詳細資料窗格中，按一下 **[挑選]** 。</span><span class="sxs-lookup"><span data-stu-id="a7b30-123">In the details pane, click **Pick**.</span></span>  
  
         <span data-ttu-id="a7b30-124">**[挑選作業流程]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="a7b30-124">The **Pick Schedule for Job** dialog box opens.</span></span> <span data-ttu-id="a7b30-125">可用的排程會顯示為資料表。</span><span class="sxs-lookup"><span data-stu-id="a7b30-125">The available schedules appear as a table.</span></span>  
  
    3.  <span data-ttu-id="a7b30-126">按一下含有所需排程的資料列。</span><span class="sxs-lookup"><span data-stu-id="a7b30-126">Click the row with the schedule that you want.</span></span> <span data-ttu-id="a7b30-127">例如，若要將排程變更為每 5 分鐘，請按一下排程名稱為 **CollectorSchedule_Every_5min**的資料列。</span><span class="sxs-lookup"><span data-stu-id="a7b30-127">For example, to change the schedule to every 5 minutes, click the row where the schedule name is **CollectorSchedule_Every_5min.**</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="a7b30-128">您可以按一下 **[屬性]** 開啟排程的 **[作業排程屬性]** 對話方塊，藉以檢視和編輯選取之排程的屬性。</span><span class="sxs-lookup"><span data-stu-id="a7b30-128">You can view and edit the properties for the selected schedule by clicking **Properties** to open the **Job Schedule Properties** dialog box for the schedule.</span></span> <span data-ttu-id="a7b30-129">您可以使用這對話方塊來變更排程資訊，例如頻率。</span><span class="sxs-lookup"><span data-stu-id="a7b30-129">You can use this dialog box to change schedule information, such as the frequency.</span></span>  
        >   
        >  <span data-ttu-id="a7b30-130">除了修改現有的排程以外，您也可以按一下 **[上傳]** 頁面上的 **[新增]** 來建立新的上傳排程。</span><span class="sxs-lookup"><span data-stu-id="a7b30-130">As an alternative to modifying an existing schedule, you can create a new upload schedule by clicking **New** on the **Uploads** page.</span></span> <span data-ttu-id="a7b30-131">這個動作會開啟 **[新增作業排程]** 對話方塊，讓您可以用來建立自訂排程。</span><span class="sxs-lookup"><span data-stu-id="a7b30-131">This action opens the **New Job Schedule** dialog box, which you can use to create a custom schedule.</span></span>  
  
    4.  <span data-ttu-id="a7b30-132">當您完成排程的設定之後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="a7b30-132">When you are finished configuring the schedule, click **OK**.</span></span>  
  
         <span data-ttu-id="a7b30-133">您所做的變更就會顯示在 **[上傳]** 頁面上。</span><span class="sxs-lookup"><span data-stu-id="a7b30-133">The changes that you made appear on the **Uploads** page.</span></span>  
  
5.  <span data-ttu-id="a7b30-134">按一下 **[確定]** 儲存對收集頻率和上傳排程所做的變更，並且關閉 **[資料收集組屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a7b30-134">Click **OK** to save the changes to the collection frequency and the upload schedule, and to close the **Data Collection Set Properties** dialog box.</span></span>  
  
### <a name="to-change-the-schedule-for-a-non-cached-mode-collection-set"></a><span data-ttu-id="a7b30-135">若要變更非快取模式收集組的排程</span><span class="sxs-lookup"><span data-stu-id="a7b30-135">To change the schedule for a non-cached mode collection set</span></span>  
  
1.  <span data-ttu-id="a7b30-136">在 [物件總管] 中，依序展開 **[管理]** 節點、 **[資料收集]** 和 **[系統資料收集組]** 。</span><span class="sxs-lookup"><span data-stu-id="a7b30-136">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="a7b30-137">以滑鼠右鍵按一下使用非快取模式的收集組 (例如 [磁碟使用量])，然後按一下 [屬性] 開啟 [[資料收集組屬性]](#CollectionSet) 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a7b30-137">Right-click a collection set that uses non-cached mode, such as **Disk Usage**, and then click **Properties** to open the [Data Collection Set Properties](#CollectionSet) dialog box.</span></span>  
  
     <span data-ttu-id="a7b30-138">**[資料收集組屬性]** 對話方塊隨即顯示收集組屬性的分頁檢視。</span><span class="sxs-lookup"><span data-stu-id="a7b30-138">The **Data Collection Set Properties** dialog box displays a paged view of the collection set properties.</span></span>  
  
3.  <span data-ttu-id="a7b30-139">若要變更收集組的排程，請按一下 **[挑選]** 。</span><span class="sxs-lookup"><span data-stu-id="a7b30-139">To change the schedule for the collection set, click **Pick**.</span></span>  
  
     <span data-ttu-id="a7b30-140">**[挑選作業流程]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="a7b30-140">The **Pick Schedule for Job** dialog box opens.</span></span> <span data-ttu-id="a7b30-141">可用的排程會顯示為資料表。</span><span class="sxs-lookup"><span data-stu-id="a7b30-141">The available schedules are displayed as a table.</span></span>  
  
4.  <span data-ttu-id="a7b30-142">按一下含有所需排程的資料列。</span><span class="sxs-lookup"><span data-stu-id="a7b30-142">Click the row with the schedule that you want.</span></span> <span data-ttu-id="a7b30-143">例如，若要將排程變更為每 5 分鐘，請按一下排程名稱為 **CollectorSchedule_Every_5min**的資料列。</span><span class="sxs-lookup"><span data-stu-id="a7b30-143">For example, to change the schedule to every 5 minutes, click the row where the schedule name is **CollectorSchedule_Every_5min**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a7b30-144">您可以按一下 **[屬性]** 開啟排程的 **[作業排程屬性]** 對話方塊，藉以檢視和編輯選取之排程的屬性。</span><span class="sxs-lookup"><span data-stu-id="a7b30-144">You can view and edit the properties for the selected schedule by clicking **Properties** to open the **Job Schedule Properties** dialog box for the schedule.</span></span> <span data-ttu-id="a7b30-145">您可以使用這對話方塊來變更排程資訊，例如頻率。</span><span class="sxs-lookup"><span data-stu-id="a7b30-145">You can use this dialog box to change schedule information, such as the frequency.</span></span>  
    >   
    >  <span data-ttu-id="a7b30-146">除了修改現有的排程以外，您也可以按一下 **[一般]** 頁面上的 **[新增]** 來建立新的收集和上傳排程。</span><span class="sxs-lookup"><span data-stu-id="a7b30-146">As an alternative to modifying an existing schedule, you can create a new collect and upload schedule by clicking **New** on the **General** page.</span></span> <span data-ttu-id="a7b30-147">這個動作會開啟 **[新增作業排程]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a7b30-147">This action opens the **New Job Schedule** dialog box.</span></span>  
  
5.  <span data-ttu-id="a7b30-148">當您完成排程的設定之後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="a7b30-148">When you are finished configuring the schedule, click **OK**.</span></span>  
  
6.  <span data-ttu-id="a7b30-149">按一下 **[確定]** 儲存這些變更並且關閉 **[資料收集組屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a7b30-149">Click **OK** to save the changes and to close the **Data Collection Set Properties** dialog box.</span></span>  
  
####  <a name="data-collection-set-properties-dialog-box"></a><a name="CollectionSet"></a> <span data-ttu-id="a7b30-150">資料收集組屬性對話方塊</span><span class="sxs-lookup"><span data-stu-id="a7b30-150">Data Collection Set Properties Dialog Box</span></span>  
 <span data-ttu-id="a7b30-151">**一般頁面**</span><span class="sxs-lookup"><span data-stu-id="a7b30-151">**General Page**</span></span>  
  
 <span data-ttu-id="a7b30-152">使用這個頁面可設定要如何收集及上傳資料、設定排程，以及設定管理資料倉儲中的資料保留期限。</span><span class="sxs-lookup"><span data-stu-id="a7b30-152">Use this page to configure how data is collected and uploaded, configure schedules, and configure data retention periods in the management data warehouse.</span></span> <span data-ttu-id="a7b30-153">這個頁面也會提供有關收集組的資訊，例如收集器類型和收集頻率，以及用於收集組的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="a7b30-153">This page also provides information about collection sets, such as collector types and collection frequencies, as well as the input parameters that are used for a collection set.</span></span>  
  
 <span data-ttu-id="a7b30-154">**名稱**</span><span class="sxs-lookup"><span data-stu-id="a7b30-154">**Name**</span></span>  
 <span data-ttu-id="a7b30-155">顯示此頁面參考的收集組名稱。</span><span class="sxs-lookup"><span data-stu-id="a7b30-155">Displays the name of the collection set that this page refers to.</span></span>  
  
 <span data-ttu-id="a7b30-156">**資料收集和上傳**</span><span class="sxs-lookup"><span data-stu-id="a7b30-156">**Data collection and upload**</span></span>  
 <span data-ttu-id="a7b30-157">指定要如何收集資料並將其上傳到管理資料倉儲。</span><span class="sxs-lookup"><span data-stu-id="a7b30-157">Specifies how data is collected and uploaded to the management data warehouse.</span></span> <span data-ttu-id="a7b30-158">請挑選下列其中一個選項。</span><span class="sxs-lookup"><span data-stu-id="a7b30-158">Pick one of the following options.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a7b30-159">**無快取 - 在相同排程時收集和上傳資料。**</span><span class="sxs-lookup"><span data-stu-id="a7b30-159">**Non-cached. Collection and data upload on the same schedule.**</span></span>|<span data-ttu-id="a7b30-160">當選取此選項時，請指定下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="a7b30-160">When selected, specify one of the following:</span></span><br /><br /> <span data-ttu-id="a7b30-161">**視需要**。</span><span class="sxs-lookup"><span data-stu-id="a7b30-161">**On-demand**.</span></span> <span data-ttu-id="a7b30-162">視需要收集及上傳資料。</span><span class="sxs-lookup"><span data-stu-id="a7b30-162">Data is collected and uploaded on demand.</span></span><br /><br /> <span data-ttu-id="a7b30-163">**排程**。</span><span class="sxs-lookup"><span data-stu-id="a7b30-163">**Schedule**.</span></span> <span data-ttu-id="a7b30-164">根據排程收集及上傳資料。</span><span class="sxs-lookup"><span data-stu-id="a7b30-164">Data is collected and uploaded according to a schedule.</span></span> <span data-ttu-id="a7b30-165">請按一下 **[挑選]** 從預先定義的排程清單中選取，或是按一下 **[新增]** 建立新的排程。</span><span class="sxs-lookup"><span data-stu-id="a7b30-165">Click **Pick** to select from a predefined list of schedules, or click **New** to create a new schedule.</span></span>|  
|<span data-ttu-id="a7b30-166">**快取 - 以一組收集頻率來收集和快取資料，並在個別排程時上傳快取的資料。**</span><span class="sxs-lookup"><span data-stu-id="a7b30-166">**Cached. Collect and cache data at a set of collection frequencies. Upload cached data on a separate schedule.**</span></span>|<span data-ttu-id="a7b30-167">以指定的收集頻率來收集和快取資料。</span><span class="sxs-lookup"><span data-stu-id="a7b30-167">Collect and cache data for a specified collection frequency.</span></span> <span data-ttu-id="a7b30-168">根據個別排程上傳收集的資料。</span><span class="sxs-lookup"><span data-stu-id="a7b30-168">Upload the collected data on a separate schedule.</span></span>|  
  
 <span data-ttu-id="a7b30-169">**收集項**</span><span class="sxs-lookup"><span data-stu-id="a7b30-169">**Collection items**</span></span>  
 <span data-ttu-id="a7b30-170">顯示收集組中的收集項。</span><span class="sxs-lookup"><span data-stu-id="a7b30-170">Displays the collection items in the collection set.</span></span> <span data-ttu-id="a7b30-171">下列資訊是針對每一個收集項所提供：</span><span class="sxs-lookup"><span data-stu-id="a7b30-171">The following information is provided for each collection item:</span></span>  
  
-   <span data-ttu-id="a7b30-172">**名稱**</span><span class="sxs-lookup"><span data-stu-id="a7b30-172">**Name**</span></span>  
  
-   <span data-ttu-id="a7b30-173">**收集器類型**</span><span class="sxs-lookup"><span data-stu-id="a7b30-173">**Collector Type**</span></span>  
  
-   <span data-ttu-id="a7b30-174">**收集頻率** (秒)。</span><span class="sxs-lookup"><span data-stu-id="a7b30-174">**Collection Frequency** (secs).</span></span> <span data-ttu-id="a7b30-175">如果 **[資料收集和上傳]** 設定為 [快取]，就可以編輯這個欄位。</span><span class="sxs-lookup"><span data-stu-id="a7b30-175">This field is editable if **Data collection and upload** is configured as cached.</span></span> <span data-ttu-id="a7b30-176">按兩下此資料格來設定收集頻率。</span><span class="sxs-lookup"><span data-stu-id="a7b30-176">Double-click this cell to set the collection frequency.</span></span>  
  
 <span data-ttu-id="a7b30-177">**輸入參數**</span><span class="sxs-lookup"><span data-stu-id="a7b30-177">**Input parameters**</span></span>  
 <span data-ttu-id="a7b30-178">顯示用於收集組的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="a7b30-178">Displays the input parameters used for the collection set.</span></span>  
  
 <span data-ttu-id="a7b30-179">**執行身分**</span><span class="sxs-lookup"><span data-stu-id="a7b30-179">**Run as**</span></span>  
 <span data-ttu-id="a7b30-180">指定用來執行收集組的帳戶。</span><span class="sxs-lookup"><span data-stu-id="a7b30-180">Specifies the account used to run the collection set.</span></span> <span data-ttu-id="a7b30-181">根據預設，這是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="a7b30-181">By default this is the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Service Account.</span></span> <span data-ttu-id="a7b30-182">如果定義了 Proxy 帳戶，這個清單就會包含可用 Proxy 帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="a7b30-182">If proxy accounts are defined, this list includes the names of the available proxy accounts.</span></span>  
  
 <span data-ttu-id="a7b30-183">**指定要將資料保留在管理資料倉儲中的天數。**</span><span class="sxs-lookup"><span data-stu-id="a7b30-183">**Set how long collected data will be retained in the management data warehouse.**</span></span>  
 <span data-ttu-id="a7b30-184">指定要將收集而來的資料保留多久。</span><span class="sxs-lookup"><span data-stu-id="a7b30-184">Specifies how long collected data is retained.</span></span> <span data-ttu-id="a7b30-185">請挑選下列其中一個選項。</span><span class="sxs-lookup"><span data-stu-id="a7b30-185">Pick one of the following options.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a7b30-186">**資料保留期限**</span><span class="sxs-lookup"><span data-stu-id="a7b30-186">**Retain data for**</span></span>|<span data-ttu-id="a7b30-187">預設會選取這個選項，而且預設的保留期限為 14 天。</span><span class="sxs-lookup"><span data-stu-id="a7b30-187">This option is selected by default, and the default retention period is 14 days.</span></span>|  
|<span data-ttu-id="a7b30-188">**永久保留資料**</span><span class="sxs-lookup"><span data-stu-id="a7b30-188">**Retain data indefinitely**</span></span>|<span data-ttu-id="a7b30-189">對於資料的保留時間長度沒有任何時間限制。</span><span class="sxs-lookup"><span data-stu-id="a7b30-189">There is no time limit on the length of time that data is retained.</span></span>|  
  
 <span data-ttu-id="a7b30-190">**上傳頁面**</span><span class="sxs-lookup"><span data-stu-id="a7b30-190">**Uploads Page**</span></span>  
  
 <span data-ttu-id="a7b30-191">使用這個頁面可針對此收集組所收集的資料來設定上傳排程。</span><span class="sxs-lookup"><span data-stu-id="a7b30-191">Use this page to configure the upload schedule for data that is collected by this collection set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7b30-192">只有當已針對 [資料收集和上傳] 設定 [已快取] 選項時，才會啟用這個索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a7b30-192">This tab is only enabled if the **Cached** option is configured for **Data collection and upload**.</span></span>  
  
 <span data-ttu-id="a7b30-193">**Server**</span><span class="sxs-lookup"><span data-stu-id="a7b30-193">**Server**</span></span>  
 <span data-ttu-id="a7b30-194">顯示將主控管理資料倉儲的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="a7b30-194">Displays the name of the server that hosts the management data warehouse.</span></span> <span data-ttu-id="a7b30-195">如需詳細資訊，請參閱[設定管理資料倉儲 &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="a7b30-195">For more information, see [Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md).</span></span>  
  
 <span data-ttu-id="a7b30-196">**管理資料倉儲**</span><span class="sxs-lookup"><span data-stu-id="a7b30-196">**Management data warehouse**</span></span>  
 <span data-ttu-id="a7b30-197">顯示管理資料倉儲的名稱。</span><span class="sxs-lookup"><span data-stu-id="a7b30-197">Displays the name of the management data warehouse.</span></span> <span data-ttu-id="a7b30-198">如需詳細資訊，請參閱[設定管理資料倉儲 &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="a7b30-198">For more information, see [Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md).</span></span>  
  
 <span data-ttu-id="a7b30-199">**上次上傳日期**</span><span class="sxs-lookup"><span data-stu-id="a7b30-199">**Last upload**</span></span>  
 <span data-ttu-id="a7b30-200">針對上次為此收集組完成的上傳顯示日期和時間資訊。</span><span class="sxs-lookup"><span data-stu-id="a7b30-200">Displays date and time information for the last upload done for the collection set.</span></span>  
  
 <span data-ttu-id="a7b30-201">**上傳排程**</span><span class="sxs-lookup"><span data-stu-id="a7b30-201">**Upload schedule**</span></span>  
 <span data-ttu-id="a7b30-202">指定收集組的上傳排程。</span><span class="sxs-lookup"><span data-stu-id="a7b30-202">Specifies the upload schedule for the collection set.</span></span> <span data-ttu-id="a7b30-203">當啟用這個選項時，請按一下 **[挑選]** 從預先定義的排程清單中選取，或是按一下 **[新增]** 建立新的排程。</span><span class="sxs-lookup"><span data-stu-id="a7b30-203">If enabled, Click **Pick** to select from a predefined list of schedules, or click **New** to create a new schedule.</span></span>  
  
 <span data-ttu-id="a7b30-204">**描述頁面**</span><span class="sxs-lookup"><span data-stu-id="a7b30-204">**Description Page**</span></span>  
  
 <span data-ttu-id="a7b30-205">使用此頁面可檢視此屬性頁面參考之收集組的描述。</span><span class="sxs-lookup"><span data-stu-id="a7b30-205">Use this page to view a description of the collection set that this properties page refers to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b30-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7b30-206">See Also</span></span>  
 <span data-ttu-id="a7b30-207">[管理資料收集](manage-data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="a7b30-207">[Manage Data Collection](manage-data-collection.md) </span></span>  
 <span data-ttu-id="a7b30-208">[[資料收集]](data-collection.md)</span><span class="sxs-lookup"><span data-stu-id="a7b30-208">[Data Collection](data-collection.md)</span></span>  
  
  
