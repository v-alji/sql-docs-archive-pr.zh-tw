---
title: 建立、修改和刪除共用排程 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report-specific schedules [Reporting Services]
- shared schedules [Reporting Services]
- modifying schedules
- removing schedules
- shared schedules [Reporting Services], creating
- shared schedules [Reporting Services], modifying
- schedules [Reporting Services], deleting
- deleting schedules
- schedules [Reporting Services], creating
- schedules [Reporting Services], modifying
- shared schedules [Reporting Services], deleting
ms.assetid: 05da5f3d-9222-43a9-893b-aa10f0f690f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ec235126caee5acd0d5c79958528565d917bf522
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598730"
---
# <a name="create-modify-and-delete-schedules"></a><span data-ttu-id="5dee4-102">Create, Modify, and Delete Schedules</span><span class="sxs-lookup"><span data-stu-id="5dee4-102">Create, Modify, and Delete Schedules</span></span>
  <span data-ttu-id="5dee4-103">使用本主題可讓您了解如何建立、修改和刪除排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-103">Use this topic to learn about how to create, modify, and delete schedules.</span></span>  
  
 <span data-ttu-id="5dee4-104">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="5dee4-104">In this topic:</span></span>  
  
-   [<span data-ttu-id="5dee4-105">管理共用排程的概觀</span><span class="sxs-lookup"><span data-stu-id="5dee4-105">Overview of Managing Shared Schedules</span></span>](#bkmk_overview)  
  
-   [<span data-ttu-id="5dee4-106"> (SharePoint 模式建立和管理共用排程) </span><span class="sxs-lookup"><span data-stu-id="5dee4-106">Create and Manage Shared Schedules (SharePoint Mode)</span></span>](#bkmk_sharepoint)  
  
-   [<span data-ttu-id="5dee4-107">建立及管理共用排程 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="5dee4-107">Create and Manage Shared Schedules (Native Mode)</span></span>](#bkmk_native)  
  
##  <a name="overview-of-managing-shared-schedules"></a><a name="bkmk_overview"></a><span data-ttu-id="5dee4-108">管理共用排程的總覽</span><span class="sxs-lookup"><span data-stu-id="5dee4-108">Overview of Managing Shared Schedules</span></span>  
 <span data-ttu-id="5dee4-109">若要管理原生模式的共用排程，請使用報表管理員中的 [排程] 頁面或 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的 [共用排程] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5dee4-109">To manage shared schedules for native mode, use the Schedules page in Report Manager or the Shared Schedules folder in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="5dee4-110">如果是 SharePoint 模式，請使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式的管理頁面。</span><span class="sxs-lookup"><span data-stu-id="5dee4-110">For SharePoint mode use, the management pages for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
 <span data-ttu-id="5dee4-111">您可以檢視所有為報表伺服器定義的共用排程、暫停與繼續排程 (只能在報表管理員上進行)，以及選取要修改或刪除的排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-111">You can view all the shared schedules that are defined for the report server, pause and resume schedules (on Report Manager only), and select schedules to modify or delete.</span></span> <span data-ttu-id="5dee4-112">[共用排程] 頁面中會有每一個排程狀態的下列摘要資訊：頻率、擁有者、到期日與狀態。</span><span class="sxs-lookup"><span data-stu-id="5dee4-112">The Shared Schedules page summarizes the following information about the state of each schedule: frequency, owner, expiration date, and status.</span></span>  
  
 <span data-ttu-id="5dee4-113">您可以透過下列方式來區別某個共用排程是否使用中：</span><span class="sxs-lookup"><span data-stu-id="5dee4-113">You can tell whether a shared schedule is actively used by:</span></span>  
  
-   <span data-ttu-id="5dee4-114">在 [共用排程] 頁面上檢查 [上次執行] 日期、[下次執行] 日期以及 [狀態] 欄位中的值。</span><span class="sxs-lookup"><span data-stu-id="5dee4-114">Inspecting the values in the Last Run date, Next Run date, and Status fields on the Shared Schedules page.</span></span> <span data-ttu-id="5dee4-115">若因為排程已過期而不再執行，到期日就會顯示在 [狀態] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="5dee4-115">If a schedule no longer runs because it has expired, the expiration date appears in the Status field.</span></span>  
  
-   <span data-ttu-id="5dee4-116">檢視給定之共用排程的 [報表] 頁面。</span><span class="sxs-lookup"><span data-stu-id="5dee4-116">Viewing the Reports page of a given Shared Schedule.</span></span> <span data-ttu-id="5dee4-117">此頁面會列出使用共用排程的所有報表和共用資料集。</span><span class="sxs-lookup"><span data-stu-id="5dee4-117">This page lists all reports and shared datasets that use the shared schedule.</span></span>  
  
-   <span data-ttu-id="5dee4-118">檢視報表執行記錄檔或追蹤記錄，以便判斷報表是否已在排程指定的時間執行。</span><span class="sxs-lookup"><span data-stu-id="5dee4-118">Viewing the report execution log files or trace logs to determine whether reports have been run at the times specified by the schedule.</span></span> <span data-ttu-id="5dee4-119">如需詳細資訊，請參閱 [Reporting Services 記錄檔和來源](../report-server/reporting-services-log-files-and-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="5dee4-119">For more information, see [Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md).</span></span>  
  
##  <a name="create-and-manage-shared-schedules-sharepoint-mode"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="5dee4-120">(SharePoint 模式建立和管理共用排程) </span><span class="sxs-lookup"><span data-stu-id="5dee4-120">Create and Manage Shared Schedules (SharePoint Mode)</span></span>  
 <span data-ttu-id="5dee4-121">共用排程是一種多用途排程，可提供現成的排程資訊給任何數目的報表或訂閱。</span><span class="sxs-lookup"><span data-stu-id="5dee4-121">A shared schedule is a multipurpose schedule that provides ready-to-use schedule information to any number of reports or subscriptions.</span></span> <span data-ttu-id="5dee4-122">您可以只建立共用排程一次，然後等到需要排程資訊時，在訂閱或屬性頁面中參考它。</span><span class="sxs-lookup"><span data-stu-id="5dee4-122">You create a shared schedule once, and then reference it in a subscription or property page when you need schedule information.</span></span> <span data-ttu-id="5dee4-123">共用排程可以集中管理、暫停和繼續。</span><span class="sxs-lookup"><span data-stu-id="5dee4-123">Shared schedules can be centrally managed, paused, and resumed.</span></span> <span data-ttu-id="5dee4-124">相對地，您必須手動編輯自訂排程，才能避免執行報表或訂閱。</span><span class="sxs-lookup"><span data-stu-id="5dee4-124">In contrast, you must edit a custom schedule manually to prevent a report or subscription from running.</span></span>  
  
 <span data-ttu-id="5dee4-125">您必須具有網站管理員的身分，才能在 SharePoint 網站上建立、修改或刪除共用排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-125">You must be a site administrator to create, modify, or delete shared schedules on a SharePoint site.</span></span>  
  
 <span data-ttu-id="5dee4-126">您可以依排程的描述性名稱來識別特定的排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-126">You can identify a specific schedule by its descriptive name.</span></span> <span data-ttu-id="5dee4-127">如果沒有指定名稱，便會根據排程的相關事實 (例如排程的循環模式或執行日期和時間) 來建立預設名稱。</span><span class="sxs-lookup"><span data-stu-id="5dee4-127">If a name is not specified, a default name is created based on facts about the schedule, such as its recurrence pattern or dates and times when it runs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5dee4-128">建立共用排程需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="5dee4-128">Creating shared schedules requires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
### <a name="create-shared-schedules-sharepoint"></a><span data-ttu-id="5dee4-129">建立共用排程 (SharePoint)</span><span class="sxs-lookup"><span data-stu-id="5dee4-129">Create Shared Schedules (SharePoint)</span></span>  
  
##### <a name="to-create-shared-schedules"></a><span data-ttu-id="5dee4-130">若要建立共用排程</span><span class="sxs-lookup"><span data-stu-id="5dee4-130">To create shared schedules</span></span>  
  
1.  <span data-ttu-id="5dee4-131">按一下 **[網站動作]** 。</span><span class="sxs-lookup"><span data-stu-id="5dee4-131">Click **Site Actions**.</span></span>  
  
2.  <span data-ttu-id="5dee4-132">按一下 **[站台設定]** 。</span><span class="sxs-lookup"><span data-stu-id="5dee4-132">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="5dee4-133">在 [Reporting Services] 區段中，按一下 **[管理共用排程]** 。</span><span class="sxs-lookup"><span data-stu-id="5dee4-133">In the Reporting Services section, click **Manage Shared Schedules**.</span></span>  
  
4.  <span data-ttu-id="5dee4-134">按一下 **[加入排程]** ，開啟 [排程屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="5dee4-134">Click **Add Schedule** to open the Schedule Properties page.</span></span>  
  
5.  <span data-ttu-id="5dee4-135">輸入排程的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="5dee4-135">Enter a descriptive name for the schedule.</span></span> <span data-ttu-id="5dee4-136">在用來處理 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表的應用程式頁面上，這個名稱會出現在整個網站中排程定義頁面的下拉清單方塊中。</span><span class="sxs-lookup"><span data-stu-id="5dee4-136">On the application pages used to work with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] reports, this name will appear in drop-down lists in schedule definition pages throughout the site.</span></span> <span data-ttu-id="5dee4-137">避免使用難讀的冗長名稱。</span><span class="sxs-lookup"><span data-stu-id="5dee4-137">Avoid long names that are hard to read.</span></span> <span data-ttu-id="5dee4-138">務必按照命名慣例，在名稱開頭放入最多描述資訊。</span><span class="sxs-lookup"><span data-stu-id="5dee4-138">Do follow a naming convention that puts the most description information at the beginning of the name.</span></span>  
  
6.  <span data-ttu-id="5dee4-139">選擇頻率。</span><span class="sxs-lookup"><span data-stu-id="5dee4-139">Choose a frequency.</span></span> <span data-ttu-id="5dee4-140">依據您所選擇的頻率而定，出現在頁面上的排程選項可能會改變以支援該頻率 (例如，如果您選擇 [月]  ，各月份的名稱將會出現在頁面上)。</span><span class="sxs-lookup"><span data-stu-id="5dee4-140">Depending on the frequency you choose, the schedule options that appear on the page might change to support that frequency (for example, if you choose **Month**, the name of each month will appear on the page).</span></span>  
  
7.  <span data-ttu-id="5dee4-141">定義排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-141">Define the schedule.</span></span> <span data-ttu-id="5dee4-142">單一排程無法支援所有的排程組合。</span><span class="sxs-lookup"><span data-stu-id="5dee4-142">Not all schedule combinations can be supported in a single schedule.</span></span>  
  
8.  <span data-ttu-id="5dee4-143">設定開始和結束日期。</span><span class="sxs-lookup"><span data-stu-id="5dee4-143">Set a start and end date.</span></span>  
  
9. <span data-ttu-id="5dee4-144">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="5dee4-144">Click **OK**.</span></span>  
  
### <a name="delete-shared-schedules-sharepoint"></a><span data-ttu-id="5dee4-145">刪除共用排程 (SharePoint)</span><span class="sxs-lookup"><span data-stu-id="5dee4-145">Delete Shared Schedules (SharePoint)</span></span>  
 <span data-ttu-id="5dee4-146">無論是共用或報表特定排程，所有排程都必須手動刪除。</span><span class="sxs-lookup"><span data-stu-id="5dee4-146">All schedules, whether shared or report specific, must be deleted manually.</span></span> <span data-ttu-id="5dee4-147">如果您刪除使用中的共用排程，該排程的所有參考都會取代成非特定的自訂排程 (亦即沒有日期或時間資訊的自訂排程)。</span><span class="sxs-lookup"><span data-stu-id="5dee4-147">If you delete a shared schedule that is in use, all references to it are replaced with unspecified custom schedules (that is, a custom schedule that does not have date or time information).</span></span>  
  
 <span data-ttu-id="5dee4-148">刪除排程與造成它過期是不相同的。</span><span class="sxs-lookup"><span data-stu-id="5dee4-148">Deleting a schedule and causing it to expire are different.</span></span> <span data-ttu-id="5dee4-149">到期日是用來停止排程，但不會刪除它。</span><span class="sxs-lookup"><span data-stu-id="5dee4-149">An expiration date is used to stop a schedule but does not delete it.</span></span> <span data-ttu-id="5dee4-150">因為排程是用來自動化報表伺服器作業，所以永遠不會自動刪除。</span><span class="sxs-lookup"><span data-stu-id="5dee4-150">Because schedules are used to automate report server operations, they are never deleted automatically.</span></span> <span data-ttu-id="5dee4-151">過期的排程會提供證據給報表伺服器管理員，以說明自動化處理序突然停止的原因。</span><span class="sxs-lookup"><span data-stu-id="5dee4-151">Expired schedules provide evidence to report server administrators as to why an automated process has suddenly stopped.</span></span> <span data-ttu-id="5dee4-152">如果沒有顯示過期排程，報表伺服器管理員可能會誤判問題，或浪費不必要的時間嘗試解決功能正常的處理序。</span><span class="sxs-lookup"><span data-stu-id="5dee4-152">Without the presence of the expired schedule, a report server administrator might misdiagnose the problem or spend unnecessary time trying to troubleshoot a fully functional process.</span></span>  
  
 <span data-ttu-id="5dee4-153">已經過期的自訂排程會繼續附加至報表。</span><span class="sxs-lookup"><span data-stu-id="5dee4-153">A custom schedule that has expired remains attached to the report.</span></span> <span data-ttu-id="5dee4-154">您可以檢查排程的結束日期，判斷它是否過期。</span><span class="sxs-lookup"><span data-stu-id="5dee4-154">You can determine if a schedule has expired by checking its end date.</span></span> <span data-ttu-id="5dee4-155">過期的共用排程會保留在 [共用排程] 清單中。</span><span class="sxs-lookup"><span data-stu-id="5dee4-155">An expired shared schedule remains in the Shared Schedules list.</span></span> <span data-ttu-id="5dee4-156">[狀態] 欄位會指示排程是否已過期。</span><span class="sxs-lookup"><span data-stu-id="5dee4-156">The Status field indicates whether the schedule has expired.</span></span> <span data-ttu-id="5dee4-157">您可以延長結束日期來恢復排程，或者，若您不再需要排程參考時，可以移除它。</span><span class="sxs-lookup"><span data-stu-id="5dee4-157">You can reinstate the schedule by extending the end date, or you can remove the schedule reference if you no longer need it.</span></span>  
  
##### <a name="to-delete-a-shared-schedule"></a><span data-ttu-id="5dee4-158">若要刪除共用排程</span><span class="sxs-lookup"><span data-stu-id="5dee4-158">To delete a shared schedule</span></span>  
  
1.  <span data-ttu-id="5dee4-159">按一下 **[網站動作]** 。</span><span class="sxs-lookup"><span data-stu-id="5dee4-159">Click **Site Actions**.</span></span>  
  
2.  <span data-ttu-id="5dee4-160">按一下 **[站台設定]** 。</span><span class="sxs-lookup"><span data-stu-id="5dee4-160">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="5dee4-161">在 [Reporting Services] 區段中，按一下 **[管理共用排程]** 。</span><span class="sxs-lookup"><span data-stu-id="5dee4-161">In the Reporting Services section, click **Manage Shared Schedules**.</span></span>  
  
4.  <span data-ttu-id="5dee4-162">選取排程，然後按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="5dee4-162">Select the schedule, and click **Delete**.</span></span>  
  
##  <a name="create-and-manage-shared-schedules-native-mode"></a><a name="bkmk_native"></a> <span data-ttu-id="5dee4-163">(原生模式建立和管理共用排程) </span><span class="sxs-lookup"><span data-stu-id="5dee4-163">Create and Manage Shared Schedules (Native Mode)</span></span>  
 <span data-ttu-id="5dee4-164">您必須使用報表管理員中的 [排程] 頁面或 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的 [共用排程] 資料夾，手動刪除共用排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-164">Shared schedules must be deleted manually using the Schedules page in Report Manager or the Shared Schedules folder in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="5dee4-165">如果您刪除使用中的共用排程，所有的參考都會以報表特定排程取代。</span><span class="sxs-lookup"><span data-stu-id="5dee4-165">If you delete a shared schedule that is in use, all references to it are replaced with report-specific schedules.</span></span>  
  
 <span data-ttu-id="5dee4-166">當您刪除報表或訂閱，或者選擇不同的方法來執行報表或訂閱時，系統就會刪除報表和訂閱特有的排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-166">Report and subscription-specific schedules are deleted when you delete the report or subscription, or when you choose a different approach to run the report or subscription.</span></span> <span data-ttu-id="5dee4-167">例如，選擇 [永遠以最新的資料執行此報表]  將會刪除您建立為以報表執行快照集的方式執行報表的報表特有排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-167">For example, choosing **Always run this report with the most recent data** will delete a report-specific schedule that you created to run a report as a report execution snapshot.</span></span>  
  
 <span data-ttu-id="5dee4-168">刪除排程與造成它過期是不相同的。</span><span class="sxs-lookup"><span data-stu-id="5dee4-168">Deleting a schedule and causing it to expire are different.</span></span> <span data-ttu-id="5dee4-169">到期日是用來停止排程，但不會刪除它。</span><span class="sxs-lookup"><span data-stu-id="5dee4-169">An expiration date is used to stop a schedule but does not delete it.</span></span> <span data-ttu-id="5dee4-170">因為排程是用來自動化大量功能，所以永遠不會自動刪除。</span><span class="sxs-lookup"><span data-stu-id="5dee4-170">Because schedules are used to automate so many features, they are never deleted automatically.</span></span> <span data-ttu-id="5dee4-171">過期的排程會提供證據給報表伺服器管理員，以說明自動化處理序突然停止的原因。</span><span class="sxs-lookup"><span data-stu-id="5dee4-171">Expired schedules provide evidence to report server administrators as to why an automated process has suddenly stopped.</span></span> <span data-ttu-id="5dee4-172">如果沒有顯示過期排程，報表伺服器管理員就會誤判問題，或花不必要的時間嘗試解決功能正常的處理序。</span><span class="sxs-lookup"><span data-stu-id="5dee4-172">Without the presence of the expired schedule, a report server administrator can misdiagnose the problem or spend unnecessary time trying to troubleshoot a fully functional process.</span></span>  
  
 <span data-ttu-id="5dee4-173">已經過期的報表特定排程會繼續附加至報表。</span><span class="sxs-lookup"><span data-stu-id="5dee4-173">A report-specific schedule that has expired remains attached to the report.</span></span> <span data-ttu-id="5dee4-174">您可以檢查排程的結束日期，判斷它是否過期。</span><span class="sxs-lookup"><span data-stu-id="5dee4-174">You can determine if a schedule has expired by checking its end date.</span></span> <span data-ttu-id="5dee4-175">過期的共用排程會保留在 [共用排程] 清單中。</span><span class="sxs-lookup"><span data-stu-id="5dee4-175">An expired shared schedules remains in the Shared Schedules list.</span></span> <span data-ttu-id="5dee4-176">[狀態] 欄位會指示排程是否已過期。</span><span class="sxs-lookup"><span data-stu-id="5dee4-176">The Status field indicates whether the schedule has expired.</span></span> <span data-ttu-id="5dee4-177">您可以延長結束日期來恢復排程，或者，若您不再需要排程參考時，可以移除它。</span><span class="sxs-lookup"><span data-stu-id="5dee4-177">You can reinstate the schedule by extending the end date, or you can remove the schedule reference if you no longer need it.</span></span>  
  
### <a name="create-delete-or-modify-a-shared-schedule-report-manager"></a><span data-ttu-id="5dee4-178">建立、刪除或修改共用排程 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="5dee4-178">Create, Delete, or Modify a Shared Schedule (Report Manager)</span></span>  
 <span data-ttu-id="5dee4-179">建立與修改排程，包含決定排程何時執行的設定頻率選項。</span><span class="sxs-lookup"><span data-stu-id="5dee4-179">Creating and modifying a schedule consists of setting frequency options that determine when the schedule runs.</span></span>  
  
-   <span data-ttu-id="5dee4-180">共用排程會建立為個別項目。</span><span class="sxs-lookup"><span data-stu-id="5dee4-180">Shared schedules are created as separate items.</span></span> <span data-ttu-id="5dee4-181">建立之後，您可以在定義訂閱或其他已排程的作業時參考它們。</span><span class="sxs-lookup"><span data-stu-id="5dee4-181">After they are created, you reference them when defining a subscription or some other scheduled operation.</span></span>  
  
-   <span data-ttu-id="5dee4-182">報表特定排程是當您定義訂閱或設定報表執行屬性時建立的；填寫排程資訊是定義訂閱或設定屬性的一部分。</span><span class="sxs-lookup"><span data-stu-id="5dee4-182">Report-specific schedules are created when you define a subscription or set report execution properties; filling out schedule information is part of defining a subscription or setting properties.</span></span> <span data-ttu-id="5dee4-183">若要定義報表特定排程，請您開啟使用它的報表或訂閱。</span><span class="sxs-lookup"><span data-stu-id="5dee4-183">To define a report-specific schedule, you open the report or subscription that uses it.</span></span>  
  
 <span data-ttu-id="5dee4-184">共用排程包含在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表伺服器上執行之任何已發行報表和訂閱數目可用的排程與循環資訊。</span><span class="sxs-lookup"><span data-stu-id="5dee4-184">A shared schedule contains schedule and recurrence information that can be used by any number of published reports and subscriptions that run on a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="5dee4-185">如果您擁有許多同時執行的報表和訂閱，就可以針對這些作業建立共用排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-185">If you have many reports and subscriptions that run at the same time, you can create a shared schedule for those jobs.</span></span> <span data-ttu-id="5dee4-186">如果您之後想要變更循環模式或結束日期，可以在單一位置進行變更。</span><span class="sxs-lookup"><span data-stu-id="5dee4-186">If you want to subsequently change the recurrence pattern or the end date, you can make the change in one place.</span></span>  
  
 <span data-ttu-id="5dee4-187">共用排程的維護方式比較簡單，而且在管理排程作業方面提供更大的彈性。</span><span class="sxs-lookup"><span data-stu-id="5dee4-187">Shared schedules are easier to maintain and give you more flexibility in managing scheduled operations.</span></span> <span data-ttu-id="5dee4-188">例如，您可以暫停並繼續共用排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-188">For example, you can pause and resume shared schedules.</span></span> <span data-ttu-id="5dee4-189">此外，如果您發現同時執行的排程作業過多，就可以建立在不同時間執行的多個共用排程，然後調整排程資訊，直到處理負載平均分散到報表伺服器為止。</span><span class="sxs-lookup"><span data-stu-id="5dee4-189">Also, if you find that too many scheduled operations are running at the same time, you can create multiple shared schedules that run at different times and then adjust the schedule information until the processing load evens out across the report server.</span></span>  
  
 <span data-ttu-id="5dee4-190">您可以在任何時候建立或修改排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-190">You can create or modify a schedule at any time.</span></span> <span data-ttu-id="5dee4-191">不過，如果排程在您修改完成之前便開始執行，則會使用舊版排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-191">However, if a schedule starts to run before you have completed your modifications, the earlier version of the schedule is used.</span></span> <span data-ttu-id="5dee4-192">修訂的排程在您儲存之前不會生效。</span><span class="sxs-lookup"><span data-stu-id="5dee4-192">The revised schedule does not take effect until you save it.</span></span>  
  
 <span data-ttu-id="5dee4-193">如果您修改共用排程，就可以在進行變更之前暫停它。</span><span class="sxs-lookup"><span data-stu-id="5dee4-193">If you are modifying a shared schedule, you can pause it before you make changes.</span></span> <span data-ttu-id="5dee4-194">當您繼續排程時，變更便會生效。</span><span class="sxs-lookup"><span data-stu-id="5dee4-194">The changes take effect when you resume the schedule.</span></span>  
  
##### <a name="to-create-or-modify-a-shared-schedule-report-manager"></a><span data-ttu-id="5dee4-195">若要建立或修改共用排程 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="5dee4-195">To create or modify a shared schedule (Report Manager)</span></span>  
  
1.  <span data-ttu-id="5dee4-196">啟動 [報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="5dee4-196">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="5dee4-197">在報表管理員中，按一下全域工具列上的 [網站設定] **[站台設定]**。</span><span class="sxs-lookup"><span data-stu-id="5dee4-197">In Report Manager, click **Site Settings**on the global toolbar.</span></span>  
  
3.  <span data-ttu-id="5dee4-198">按一下 **[** 排程]。</span><span class="sxs-lookup"><span data-stu-id="5dee4-198">Click **schedules**.</span></span>  
  
4.  <span data-ttu-id="5dee4-199">按一下 **[新增排程]**。</span><span class="sxs-lookup"><span data-stu-id="5dee4-199">Click **New Schedule**.</span></span> <span data-ttu-id="5dee4-200">若要修改現有的排程，請按一下排程的名稱。</span><span class="sxs-lookup"><span data-stu-id="5dee4-200">To modify an existing schedule, click the name of the schedule.</span></span>  
  
5.  <span data-ttu-id="5dee4-201">輸入排程的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="5dee4-201">Type a descriptive name for the schedule.</span></span>  
  
6.  <span data-ttu-id="5dee4-202">選取 **[小時]** 、 **[天]** 、 **[週]** 或 **[月]** 。</span><span class="sxs-lookup"><span data-stu-id="5dee4-202">Select **Hour**, **Day**, **Week**, or **Month**.</span></span> <span data-ttu-id="5dee4-203">按 **[一次]** ，即可建立只執行一次的排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-203">Click **Once** to create a schedule that runs one time only.</span></span> <span data-ttu-id="5dee4-204">當您指定排程的基礎時，其他選項會出現。</span><span class="sxs-lookup"><span data-stu-id="5dee4-204">Additional options appear when you specify the basis of your schedule.</span></span>  
  
7.  <span data-ttu-id="5dee4-205">選擇性地選取排程的開始日期。</span><span class="sxs-lookup"><span data-stu-id="5dee4-205">Optionally select a date to start the schedule.</span></span> <span data-ttu-id="5dee4-206">預設值是目前的日期。</span><span class="sxs-lookup"><span data-stu-id="5dee4-206">The default is the current day.</span></span> <span data-ttu-id="5dee4-207">您也可以選擇較晚的日期，來延後排程的開始時間。</span><span class="sxs-lookup"><span data-stu-id="5dee4-207">You can postpone the schedule start time by choosing a later date.</span></span>  
  
8.  <span data-ttu-id="5dee4-208">選擇性地選取結束排程的日期。</span><span class="sxs-lookup"><span data-stu-id="5dee4-208">Optionally, select a date to end the schedule.</span></span> <span data-ttu-id="5dee4-209">排程會在此日期停止執行，但不會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="5dee4-209">The schedule stops running on this date, but is not deleted.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##### <a name="to-delete-a-shared-schedule-report-manager"></a><span data-ttu-id="5dee4-210">若要刪除共用排程 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="5dee4-210">To delete a shared schedule (Report Manager)</span></span>  
  
1.  <span data-ttu-id="5dee4-211">在報表管理員中，按一下全域工具列上的 [網站設定] **[站台設定]**。</span><span class="sxs-lookup"><span data-stu-id="5dee4-211">In Report Manager, click **Site Settings**on the global toolbar.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5dee4-212"> 如果無法使用 **[站台設定]** ，您就沒有存取站台設定的權限。</span><span class="sxs-lookup"><span data-stu-id="5dee4-212">If **Site Settings** is not available, you do not have permission to access site settings.</span></span>  
  
2.  <span data-ttu-id="5dee4-213">在頁面上的 **[其他]** 區段中，按一下 **[管理共用排程]**。</span><span class="sxs-lookup"><span data-stu-id="5dee4-213">In the **Other** section on the page, click **Manage shared schedules**.</span></span>  
  
3.  <span data-ttu-id="5dee4-214">選取要刪除之排程旁邊的核取方塊，然後按一下 **[刪除]**。</span><span class="sxs-lookup"><span data-stu-id="5dee4-214">Select the check box next to the schedule you want to delete, and then click **Delete**.</span></span>  
  
 <span data-ttu-id="5dee4-215">如果您刪除了多個報表和訂閱所使用的共用排程，報表伺服器將會針對先前使用此共用排程的每個報表和訂閱建立個別的排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-215">If you delete a shared schedule that is used by multiple reports and subscriptions, the report server will create individual schedules for each report and subscription that previously used the shared schedule.</span></span> <span data-ttu-id="5dee4-216">每個新的個別排程將包含共用排程中原本指定的日期、時間和循環模式。</span><span class="sxs-lookup"><span data-stu-id="5dee4-216">Each new individual schedule will contain the date, time, and recurrence pattern that was specified in the shared schedule.</span></span> <span data-ttu-id="5dee4-217">請注意， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 不會提供個別排程的集中管理功能。</span><span class="sxs-lookup"><span data-stu-id="5dee4-217">Note that [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not provide central management of individual schedules.</span></span> <span data-ttu-id="5dee4-218">如果您刪除了共用排程，現在就必須針對每個個別項目維護排程資訊。</span><span class="sxs-lookup"><span data-stu-id="5dee4-218">If you delete a shared schedule, you will now have to maintain the schedule information for each individual item.</span></span>  
  
 <span data-ttu-id="5dee4-219">如果您不確定是否使用了共用排程，請考慮改在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中刪除它。</span><span class="sxs-lookup"><span data-stu-id="5dee4-219">If you are not sure whether a shared schedule is used, consider deleting it in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] instead.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="5dee4-220">提供的共用排程管理功能與報表管理員相同，但是它會提供額外的 [報表] 頁面，其中顯示每個使用此排程之報表的名稱。</span><span class="sxs-lookup"><span data-stu-id="5dee4-220">provides the same shared schedule management features as Report Manager, but it provides an additional Reports page that shows you the name of each report that uses the schedule.</span></span>  
  
### <a name="create-delete-or-modify-a-shared-schedule-management-studio"></a><span data-ttu-id="5dee4-221">建立、刪除或修改共用排程 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5dee4-221">Create, Delete, or Modify a Shared Schedule (Management Studio)</span></span>  
 <span data-ttu-id="5dee4-222">共用排程包含在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表伺服器上執行之任何已發行報表和訂閱數目可用的排程與循環資訊。</span><span class="sxs-lookup"><span data-stu-id="5dee4-222">A shared schedule contains schedule and recurrence information that can be used by any number of published reports and subscriptions that run on a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="5dee4-223">如果您擁有許多同時執行的報表和訂閱，就可以針對這些作業建立共用排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-223">If you have many reports and subscriptions that run at the same time, you can create a shared schedule for those jobs.</span></span> <span data-ttu-id="5dee4-224">如果您之後想要變更循環模式或結束日期，可以在單一位置進行變更。</span><span class="sxs-lookup"><span data-stu-id="5dee4-224">If you want to subsequently change the recurrence pattern or the end date, you can make the change in one place.</span></span>  
  
 <span data-ttu-id="5dee4-225">共用排程的維護方式比較簡單，而且在管理排程作業方面提供更大的彈性。</span><span class="sxs-lookup"><span data-stu-id="5dee4-225">Shared schedules are easier to maintain and give you more flexibility in managing scheduled operations.</span></span> <span data-ttu-id="5dee4-226">例如，您可以暫停並繼續共用排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-226">For example, you can pause and resume shared schedules.</span></span> <span data-ttu-id="5dee4-227">此外，如果您發現同時執行的排程作業過多，就可以建立在不同時間執行的多個共用排程，然後調整排程資訊，直到處理負載平均分散到報表伺服器為止。</span><span class="sxs-lookup"><span data-stu-id="5dee4-227">Also, if you find that too many scheduled operations are running at the same time, you can create multiple shared schedules that run at different times and then adjust the schedule information until the processing load evens out across the report server.</span></span>  
  
##### <a name="to-create-or-modify-a-shared-schedule-management-studio"></a><span data-ttu-id="5dee4-228">若要建立或修改共用排程 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5dee4-228">To create or modify a shared schedule (Management Studio)</span></span>  
  
1.  <span data-ttu-id="5dee4-229">啟動 SQL Server Management Studio 並連接至報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="5dee4-229">Start SQL Server Management Studio and connect to a report server instance.</span></span>  
  
2.  <span data-ttu-id="5dee4-230">在 [物件總管] 中，展開報表伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="5dee4-230">In Object Explorer, expand a report server node.</span></span>  
  
3.  <span data-ttu-id="5dee4-231">在 [共用排程] 資料夾上按一下滑鼠右鍵，然後按一下 [**新增排程**]。</span><span class="sxs-lookup"><span data-stu-id="5dee4-231">Right-click the Shared Schedules folder, and then click **New Schedule**.</span></span> <span data-ttu-id="5dee4-232">就會顯示 **[新增共用排程]** 對話方塊的 [一般] 頁面。</span><span class="sxs-lookup"><span data-stu-id="5dee4-232">The General page of the **New Shared Schedule** dialog box is displayed.</span></span>  
  
     <span data-ttu-id="5dee4-233">若要修改現有的共用排程，請展開 [共用排程] 資料夾、以滑鼠右鍵按一下您要修改的排程，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="5dee4-233">To modify an existing shared schedule, expand the Shared Schedules folder, right-click the schedule you want to modify, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="5dee4-234">輸入排程的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="5dee4-234">Type a descriptive name for the schedule.</span></span>  
  
5.  <span data-ttu-id="5dee4-235">選擇性地選取排程的開始日期。</span><span class="sxs-lookup"><span data-stu-id="5dee4-235">Optionally select a date to start the schedule.</span></span> <span data-ttu-id="5dee4-236">預設值是目前的日期。</span><span class="sxs-lookup"><span data-stu-id="5dee4-236">The default is the current day.</span></span>  
  
6.  <span data-ttu-id="5dee4-237">選擇性地選取排程的結束日期。</span><span class="sxs-lookup"><span data-stu-id="5dee4-237">Optionally select a date to end the schedule.</span></span> <span data-ttu-id="5dee4-238">排程會在此日期停止執行，但不會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="5dee4-238">The schedule stops running on this date, but is not deleted.</span></span>  
  
7.  <span data-ttu-id="5dee4-239">若要設定重複執行排程，請選取 **[小時]** 、 **[天]** 、 **[週]** 或 **[月]** 。</span><span class="sxs-lookup"><span data-stu-id="5dee4-239">To configure a recurring schedule, select **Hour**, **Day**, **Week**, or **Month**.</span></span> <span data-ttu-id="5dee4-240">就會顯示其他選項。</span><span class="sxs-lookup"><span data-stu-id="5dee4-240">Additional options are displayed.</span></span> <span data-ttu-id="5dee4-241">請根據您偏好的小時、天、週或月，使用這些選項來設定排程頻率。</span><span class="sxs-lookup"><span data-stu-id="5dee4-241">Use these additional options to configure schedule frequency, based on your preferred hour, day, week, or month.</span></span>  
  
     <span data-ttu-id="5dee4-242">若要指定單次 (非重複執行) 排程，請選取 [一次]  ，然後指定 [開始時間]  。</span><span class="sxs-lookup"><span data-stu-id="5dee4-242">Or, to specify a one-time (non-recurring) schedule, select **Once**, and then specify a **Start time**.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##### <a name="to-delete-a-shared-schedule-management-studio"></a><span data-ttu-id="5dee4-243">若要刪除共用排程 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5dee4-243">To delete a shared schedule (Management Studio)</span></span>  
  
1.  <span data-ttu-id="5dee4-244">在 [物件總管] 中，展開報表伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="5dee4-244">In Object Explorer, expand a report server node.</span></span>  
  
2.  <span data-ttu-id="5dee4-245">展開 [共用排程] 資料夾，以滑鼠右鍵按一下您要刪除的排程，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="5dee4-245">Expand the Shared Schedules folder, right-click the schedule you want to delete, and then click **Delete**.</span></span> <span data-ttu-id="5dee4-246">**[刪除目錄項目]** 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="5dee4-246">The **Delete Catalog Items** dialog box appears.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="5dee4-247">如果您刪除了多個報表和訂閱所使用的共用排程，報表伺服器將會針對先前使用此共用排程的每個報表和訂閱建立個別的排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-247">If you delete a shared schedule that is used by multiple reports and subscriptions, the report server will create individual schedules for each report and subscription that previously used the shared schedule.</span></span> <span data-ttu-id="5dee4-248">每個新的個別排程將包含共用排程中原本指定的日期、時間和循環模式。</span><span class="sxs-lookup"><span data-stu-id="5dee4-248">Each new individual schedule will contain the date, time, and recurrence pattern that was specified in the shared schedule.</span></span> <span data-ttu-id="5dee4-249">請注意， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 不會提供個別排程的集中管理功能。</span><span class="sxs-lookup"><span data-stu-id="5dee4-249">Note that [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not provide central management of individual schedules.</span></span> <span data-ttu-id="5dee4-250">如果您刪除了共用排程，現在就必須針對每個個別項目維護排程資訊。</span><span class="sxs-lookup"><span data-stu-id="5dee4-250">If you delete a shared schedule, you will now have to maintain the schedule information for each individual item.</span></span> <span data-ttu-id="5dee4-251">刪除共用排程之前，請使用 [[報表] 頁面](../tools/schedule-properties-reports-page.md)來判斷哪些報表目前正在使用共用排程。</span><span class="sxs-lookup"><span data-stu-id="5dee4-251">Before deleting a shared schedule, use the [Reports Page](../tools/schedule-properties-reports-page.md) to determine which reports are currently using the shared schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dee4-252">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5dee4-252">See Also</span></span>  
 <span data-ttu-id="5dee4-253">[[排程]](schedules.md) </span><span class="sxs-lookup"><span data-stu-id="5dee4-253">[Schedules](schedules.md) </span></span>  
 <span data-ttu-id="5dee4-254">[暫停和繼續共用排程](pause-and-resume-shared-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="5dee4-254">[Pause and Resume Shared Schedules](pause-and-resume-shared-schedules.md) </span></span>  
 <span data-ttu-id="5dee4-255">[將報表快取 &#40;報表管理員&#41;](../report-server/cache-a-report-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="5dee4-255">[Cache a Report &#40;Report Manager&#41;](../report-server/cache-a-report-report-manager.md) </span></span>  
 [<span data-ttu-id="5dee4-256">將快照集加入報表記錄 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="5dee4-256">Add a Snapshot to Report History &#40;Report Manager&#41;</span></span>](../report-server/add-a-snapshot-to-report-history-report-manager.md)  
  
  
