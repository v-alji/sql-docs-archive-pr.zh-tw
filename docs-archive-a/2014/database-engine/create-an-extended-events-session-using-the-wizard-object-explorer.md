---
title: 使用 Wizard (物件總管) 建立擴充事件會話 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- Sql12.ssms.XeWizard.Summary.f1
- Sql12.ssms.XeWizard.SetSessionProperties.f1
- Sql12.ssms.XeWizard.CaptureAddFields.f1
- Sql12.ssms.XeWizard.SelectEvents.f1
- Sql12.ssms.XeWizard.SpecifySessionTargets.f1
- Sql12.ssms.XeWizard.Welcome.f1
- sql12.ssms.XeWizard.Welcome.f1
- Sql12.ssms.XeWizard.ChooseTemplate.f1
- Sql12.ssms.XeWizard.SetSessionEventFilters.f1
- Sql12.ssms.XeWizard.Results.f1
helpviewer_keywords:
- Sql11.ssms.XeWizard.CaptureAddFields.f1
- Sql11.ssms.XeWizard.SetSessionEventFilters.f1
- Sql11.ssms.XeWizard.SpecifySessionTargets.f1
- Sql11.ssms.XeWizard.Results.f1
- Sql11.ssms.XeWizard.ChooseTemplate.f1
- Sql11.ssms.XeWizard.SetSessionProperties.f1
- Sql11.ssms.XeWizard.Welcome.f1
- Sql11.ssms.XeWizard.Summary.f1
- Sql11.ssms.XeWizard.SelectEvents.f1
ms.assetid: 80c0456f-17c0-41d8-b2aa-502a2f3bb6de
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cdfc9141b0b99d5b06fc73044b8f4fae623922b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596256"
---
# <a name="create-an-extended-events-session-using-the-wizard-object-explorer"></a><span data-ttu-id="9d4bb-102">使用精靈建立擴充事件工作階段 (物件總管)</span><span class="sxs-lookup"><span data-stu-id="9d4bb-102">Create an Extended Events Session Using the Wizard (Object Explorer)</span></span>
  <span data-ttu-id="9d4bb-103">為了幫助您選取及擷取伺服器上的事件，「擴充事件」包含了 [新增工作階段精靈]，可引導您建立「擴充事件」工作階段的步驟。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-103">To help you select and capture events on your server, Extended Events includes a New Session Wizard that guides you through the steps to create an Extended Events session.</span></span> <span data-ttu-id="9d4bb-104">[新增工作階段精靈] 會公開大部分的擴充事件功能。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-104">The New Session Wizard exposes most of the Extended Events functionality.</span></span> <span data-ttu-id="9d4bb-105">[新增工作階段對話方塊](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md)也讓您定義擷取、顯示及分析資料的擴充事件工作階段。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-105">The [New Session dialog](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md) also lets you define an Extended Events session that captures, displays, and analyzes your data.</span></span> <span data-ttu-id="9d4bb-106">[新增工作階段] 對話方塊會公開所有擴充事件功能。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-106">The New Session dialog exposes all Extended Events functionality.</span></span>  
  
### <a name="to-open-the-new-session-wizard"></a><span data-ttu-id="9d4bb-107">若要開啟新增工作階段精靈</span><span class="sxs-lookup"><span data-stu-id="9d4bb-107">To open the New Session Wizard</span></span>  
  
1.  <span data-ttu-id="9d4bb-108">在 [物件總管] 中，依序展開 **[管理]** 節點和 **[擴充事件]**。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-108">In Object Explorer, expand the **Management** node, and then expand **Extended Events**.</span></span>  
  
2.  <span data-ttu-id="9d4bb-109">以滑鼠右鍵按一下 [工作階段]\*\*\*\*，然後按一下 [新增工作階段精靈]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-109">Right-click **Sessions**, and then click **New Session Wizard**.</span></span>  
  
### <a name="use-the-following-new-session-wizard-pages-to-create-an-event-session"></a><span data-ttu-id="9d4bb-110">使用下列新增工作階段精靈頁面來建立事件工作階段</span><span class="sxs-lookup"><span data-stu-id="9d4bb-110">Use the following New Session Wizard pages to create an event session</span></span>  
  
-   [<span data-ttu-id="9d4bb-111">簡介</span><span class="sxs-lookup"><span data-stu-id="9d4bb-111">Introduction</span></span>](#BKMK_Welcome)  
  
-   [<span data-ttu-id="9d4bb-112">設定工作階段屬性</span><span class="sxs-lookup"><span data-stu-id="9d4bb-112">Set Session Properties</span></span>](#BKMK_SetSessionProperties)  
  
-   [<span data-ttu-id="9d4bb-113">選擇範本</span><span class="sxs-lookup"><span data-stu-id="9d4bb-113">Choose Template</span></span>](#BKMK_ChooseTemplate)  
  
-   [<span data-ttu-id="9d4bb-114">選取要擷取的事件</span><span class="sxs-lookup"><span data-stu-id="9d4bb-114">Select Events to Capture</span></span>](#BKMK_SelectEventsToCapture)  
  
-   [<span data-ttu-id="9d4bb-115">擷取全域欄位</span><span class="sxs-lookup"><span data-stu-id="9d4bb-115">Capture Global Fields</span></span>](#BKMK_CaptureGlobalFields)  
  
-   [<span data-ttu-id="9d4bb-116">設定工作階段事件篩選</span><span class="sxs-lookup"><span data-stu-id="9d4bb-116">Set Session Event Filters</span></span>](#BKMK_SetSessionEventFilters)  
  
-   [<span data-ttu-id="9d4bb-117">指定工作階段資料存放區</span><span class="sxs-lookup"><span data-stu-id="9d4bb-117">Specify Session Data Storage</span></span>](#BKMK_SpecifySessionDataOutput)  
  
-   [<span data-ttu-id="9d4bb-118">總結</span><span class="sxs-lookup"><span data-stu-id="9d4bb-118">Summary</span></span>](#BKMK_Summary)  
  
-   [<span data-ttu-id="9d4bb-119">建立事件會話</span><span class="sxs-lookup"><span data-stu-id="9d4bb-119">Create Event Session</span></span>](#BKMK_CreateEventSession)  
  
##  <a name="introduction"></a><a name="BKMK_Welcome"></a><span data-ttu-id="9d4bb-120">問世</span><span class="sxs-lookup"><span data-stu-id="9d4bb-120">Introduction</span></span>  
 <span data-ttu-id="9d4bb-121">在 [簡介]\*\*\*\* 頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9d4bb-121">On the **Introduction** page, do the following:</span></span>  
  
-   <span data-ttu-id="9d4bb-122">在 [新增工作階段精靈] 的 [簡介]\*\*\*\* 頁面上，按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-122">On the **Introduction** page of the New Session Wizard, click **Next**.</span></span>  
  
     <span data-ttu-id="9d4bb-123">如果您將使用精靈一次以上，而且不想在每次啟動精靈時閱讀簡介，請選取 [不要再顯示此頁面]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-123">Select the **Do not show this page again** check box if you will be using the wizard more than once and do not want to read the introduction each time the wizard is launched.</span></span>  
  
##  <a name="set-session-properties"></a><a name="BKMK_SetSessionProperties"></a><span data-ttu-id="9d4bb-124">設定會話屬性</span><span class="sxs-lookup"><span data-stu-id="9d4bb-124">Set Session Properties</span></span>  
 <span data-ttu-id="9d4bb-125">在 [設定工作階段屬性]\*\*\*\* 頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9d4bb-125">On the **Set Session Properties** page, do the following:</span></span>  
  
-   <span data-ttu-id="9d4bb-126">在 [工作階段名稱]\*\*\*\* 方塊中，為事件工作階段輸入有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-126">In the **Session name** box, type a meaningful name for the event session.</span></span>  
  
     <span data-ttu-id="9d4bb-127">如果當您啟動伺服器時想要啟動工作階段，請選取 [在伺服器啟動時啟動事件工作階段]\*\*\*\* 核取方塊，然後按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-127">If you want to start the session when you start the server, select the **Start the event session at server startup** check box, and then click **Next**.</span></span>  
  
##  <a name="choose-template"></a><a name="BKMK_ChooseTemplate"></a><span data-ttu-id="9d4bb-128">選擇範本</span><span class="sxs-lookup"><span data-stu-id="9d4bb-128">Choose Template</span></span>  
 <span data-ttu-id="9d4bb-129">在 [選擇範本]\*\*\*\* 頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9d4bb-129">On the **Choose Template** page, do the following:</span></span>  
  
-   <span data-ttu-id="9d4bb-130">選取 [使用此事件工作階段範本]\*\*\*\* 選項，從針對常見問題所設計的一組預先設定的範本中選取。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-130">Select the **Use this event session template** option to select from a set of pre-configured templates designed for common problems.</span></span> <span data-ttu-id="9d4bb-131">從下拉式清單中選取您想要使用的範本，然後按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-131">Select the template you want to use from the drop-down list, and then click **Next**.</span></span>  
  
     <span data-ttu-id="9d4bb-132">-或-</span><span class="sxs-lookup"><span data-stu-id="9d4bb-132">-OR-</span></span>  
  
-   <span data-ttu-id="9d4bb-133">如果您不想要使用任何預先設定的範本，請選取 [不使用範本]\*\*\*\* 選項，然後按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-133">Select the **Do not use a template** option if you do not want to use any pre-configured template, and then click **Next**.</span></span>  
  
##  <a name="select-events-to-capture"></a><a name="BKMK_SelectEventsToCapture"></a><span data-ttu-id="9d4bb-134">選取要捕獲的事件</span><span class="sxs-lookup"><span data-stu-id="9d4bb-134">Select Events to Capture</span></span>  
 <span data-ttu-id="9d4bb-135">在 [選取要擷取的事件]\*\*\*\* 頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9d4bb-135">On the **Select Events to Capture** page, do the following:</span></span>  
  
1.  <span data-ttu-id="9d4bb-136">從 [事件程式庫]\*\*\*\* 選取您想要擷取的事件，然後按一下向右箭號。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-136">Select the events you want to capture from the **Event library**, and then click the right arrow.</span></span> <span data-ttu-id="9d4bb-137">您可以使用 Shift+按一下滑鼠左鍵或 Ctrl+按一下滑鼠左鍵，在 [事件程式庫] 中選取多個事件。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-137">You can select multiple events in the Event Library by using either Shift+Click or Ctrl+Click.</span></span>  
  
     <span data-ttu-id="9d4bb-138">您可以從下拉式清單方塊中選取您想要搜尋事件的方式。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-138">You can select how you want to search for the events you want to capture from the drop-down list box.</span></span> <span data-ttu-id="9d4bb-139">例如，您可以搜尋事件名稱或是事件名稱及其說明。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-139">For example, you can search for event names or event names and their descriptions.</span></span> <span data-ttu-id="9d4bb-140">您可以在 [事件程式庫]\*\*\*\* 方塊中輸入您想要搜尋的文字，以搜尋資料表中的任何文字。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-140">You can search for any word in the table by entering the text you want to search for in the **Event library** box.</span></span> <span data-ttu-id="9d4bb-141">例如，如果您想要尋找**lock_acquired**事件，您可以輸入**lock**或**lock 取得**。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-141">For example, if you want to find the **lock_acquired** event, you can enter **lock**, or **lock acquire**.</span></span>  
  
     <span data-ttu-id="9d4bb-142">您所選取的事件會出現在 [選取的事件]\*\*\*\* 方塊中。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-142">The events you select appear in the **Selected events** box.</span></span> <span data-ttu-id="9d4bb-143">若要從 [選取的事件]\*\*\*\* 方塊中移除事件，請按一下向左箭號。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-143">To remove events from the **Selected events** box, click the left arrow.</span></span>  
  
2.  <span data-ttu-id="9d4bb-144">選取您想要擷取的事件之後，請按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-144">After you select the events you want to capture, click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9d4bb-145">依預設，[偵錯]\*\*\*\* 通道的事件是隱藏的。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-145">Events from the **Debug** channel are hidden by default.</span></span> <span data-ttu-id="9d4bb-146">若要顯示偵錯事件，請從 [通道]\*\*\*\* 下拉式清單中選取 [偵錯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-146">To display debug events, select **Debug** from the **Channel** drop-down list.</span></span>  
  
##  <a name="capture-global-fields"></a><a name="BKMK_CaptureGlobalFields"></a><span data-ttu-id="9d4bb-147">捕捉全域欄位</span><span class="sxs-lookup"><span data-stu-id="9d4bb-147">Capture Global Fields</span></span>  
 <span data-ttu-id="9d4bb-148">您可以使用全域欄位 (也稱為動作)，將選定事件的單一個或多個動作產生關聯。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-148">You use global fields (also referred to as actions) to associate single or multiple actions for your selected events.</span></span> <span data-ttu-id="9d4bb-149">如果您在 [選擇範本]\*\*\*\* 頁面上選取範本，此範本中定義的所有全域欄位都會顯示在這個頁面上。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-149">If you selected a template on the **Choose Template** page, all of the global fields that are defined in the template are displayed on this page.</span></span>  
  
 <span data-ttu-id="9d4bb-150">在 [擷取全域欄位]\*\*\*\* 頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9d4bb-150">On the **Capture Global Fields** page, do the following:</span></span>  
  
-   <span data-ttu-id="9d4bb-151">選取您想要針對事件工作階段擷取的全域欄位，然後按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-151">Select the global fields that you want to capture for the event session, and then click **Next**.</span></span>  
  
     <span data-ttu-id="9d4bb-152">您可以選取或取消選取全域欄位旁邊的核取方塊，以移除或加入全域欄位。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-152">You can remove or add global fields by selecting or clearing the check box next to the global field.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9d4bb-153">選取的動作會依 [名稱]\*\*\*\* 排序，好讓您依字母順序檢視關聯的動作。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-153">The selected actions are sorted by **Name** enabling you to view the associated actions in alphabetical order.</span></span> <span data-ttu-id="9d4bb-154">您可以按一下欄位名稱旁邊的欄位標題，依說明或啟用/停用狀態來排序。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-154">You can sort by description or by the enable/disable status by clicking the column heading next to the field name.</span></span>  
  
##  <a name="set-session-event-filters"></a><a name="BKMK_SetSessionEventFilters"></a><span data-ttu-id="9d4bb-155">設定會話事件篩選器</span><span class="sxs-lookup"><span data-stu-id="9d4bb-155">Set Session Event Filters</span></span>  
 <span data-ttu-id="9d4bb-156">您可以套用篩選 (也稱為述詞) 來限制您想要擷取的事件。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-156">You can apply filters (also called predicates) to limit the events that you want to capture.</span></span> <span data-ttu-id="9d4bb-157">在 [設定工作階段事件篩選]\*\*\*\* 頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9d4bb-157">On the **Set Session Event Filters** page, do the following:</span></span>  
  
1.  <span data-ttu-id="9d4bb-158">如果您不使用預先設定的範本，請建立您的篩選準則，然後按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-158">If you are not using a pre-configured template, create your filter criteria, and then click **Next**.</span></span>  
  
     <span data-ttu-id="9d4bb-159">如果您使用預先設定的範本，則在 [範本中的篩選 (唯讀)]\*\*\*\* 區段中，[新增工作階段精靈] 會列出已從範本建立的篩選。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-159">If you are using a pre-configured template, in the **Filters from template (read-only)** section, the New Session Wizard lists filters already created from the template.</span></span>  
  
2.  <span data-ttu-id="9d4bb-160">在 [其他篩選]\*\*\*\* 區段中，您可以為事件工作階段設定其他篩選。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-160">In the **Additional filters** section, you can configure additional filters for the event session.</span></span>  
  
     <span data-ttu-id="9d4bb-161">您所設定的篩選會套用到所有選取的事件。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-161">The filters you configure apply to all selected events.</span></span> <span data-ttu-id="9d4bb-162">[新增工作階段精靈] 不支援為每個事件設定篩選。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-162">The New Session Wizard does not support configuring filters for each event.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9d4bb-163">當您為篩選設定群組子句時，儲存結果之後會從篩選中移除多餘的括號。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-163">When you configure a group clause for your filter, redundant parentheses are removed from the filter after the result is saved.</span></span> <span data-ttu-id="9d4bb-164">例如，如果您建立篩選群組 **Clause 1** 和 **Clause 2**，括弧將會出現在子句的周圍。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-164">For example, if you create a filter grouping **Clause 1** and **Clause 2**, parentheses will appear around the clauses.</span></span> <span data-ttu-id="9d4bb-165">當您儲存篩選之後，將會移除多餘的括號。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-165">After you save the filter, the redundant parentheses are removed.</span></span> <span data-ttu-id="9d4bb-166">移除括號並不會影響篩選邏輯。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-166">The removal of the parentheses does not affect the filter logic.</span></span>  
  
##  <a name="specify-session-data-storage"></a><a name="BKMK_SpecifySessionDataOutput"></a><span data-ttu-id="9d4bb-167">指定會話資料存放區</span><span class="sxs-lookup"><span data-stu-id="9d4bb-167">Specify Session Data Storage</span></span>  
 <span data-ttu-id="9d4bb-168">您可使用 [指定工作階段資料存放區]\*\*\*\* 頁面，指定您要如何收集資料進行分析。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-168">You use the **Specify Session Data Storage** page to specify how you want to collect your data for analysis.</span></span> <span data-ttu-id="9d4bb-169">SQL Server 擴充事件會使用資料輸出的目標。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-169">SQL Server Extended Events uses targets for data output.</span></span> <span data-ttu-id="9d4bb-170">目標會儲存事件資料，而且可以執行動作，例如寫入檔案及彙總事件資料。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-170">Targets store event data and can perform actions such as writing to a file and aggregating event data.</span></span> <span data-ttu-id="9d4bb-171">在 [指定工作階段資料存放區]\*\*\*\* 頁面上，決定您要如何收集資料進行分析，然後執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9d4bb-171">Decide how you want to collect your data for analysis, and on the **Specify Session Data Storage** page, do the following:</span></span>  
  
1.  <span data-ttu-id="9d4bb-172">如果是大型資料集而且要建立歷程記錄，請選取 [將資料儲存至檔案以供日後分析]\*\*\*\* 核取方塊，然後執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9d4bb-172">For large data sets and creating historical records, select the **Save data to a file for later analysis** check box, and then do the following:</span></span>  
  
    1.  <span data-ttu-id="9d4bb-173">在 [伺服器上的檔案名稱]\*\*\*\* 方塊中，輸入路徑和檔案名稱，或是按一下 [瀏覽]\*\*\*\* 指定伺服器上想要用來儲存資料的檔案目錄。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-173">In the **File name on server** box, enter the path and file name, or click **Browse** to specify the file directory on the server where you want to save the data.</span></span>  
  
    2.  <span data-ttu-id="9d4bb-174">在 [檔案大小上限]\*\*\*\* 方塊中，指定用於檔案目標的檔案大小上限。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-174">In the **Maximum file size** box, specify the maximum file size to be used for the file target.</span></span> <span data-ttu-id="9d4bb-175">如果未指定檔案大小上限，檔案可以成長到磁碟已滿。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-175">If you do not specify the maximum file size, the file will grow until the disk is full.</span></span> <span data-ttu-id="9d4bb-176">預設檔案大小為 1 GB。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-176">The default file size is 1 gigabyte (GB).</span></span>  
  
    3.  <span data-ttu-id="9d4bb-177">選取 [啟用檔案換用]\*\*\*\* 核取方塊來啟用檔案目標的檔案換用。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-177">Select the **Enable file rollover** check box to enable file rollover for the file target.</span></span>  
  
    4.  <span data-ttu-id="9d4bb-178">在 [檔案數量上限]\*\*\*\* 方塊中，指定您想要在檔案系統中保留的檔案數目上限。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-178">In the **Maximum number of files** box, specify the maximum number of files you want to retain in the file system.</span></span>  
  
2.  <span data-ttu-id="9d4bb-179">如果要收集最近的資料，請選取 [只使用最新資料 (ring_buffer 目標)]\*\*\*\* 核取方塊，然後執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9d4bb-179">For collecting recent data, select the **Work with only the most recent data (ring buffer target)** check box, and then do the following:</span></span>  
  
    1.  <span data-ttu-id="9d4bb-180">在 [要保留的事件數目]\*\*\*\* 方塊中，使用向上和向下箭號來輸入或選取您想要保留的事件數目。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-180">In the **Number of events to keep** box, enter or select the number of events you want to keep by using the up and down arrows.</span></span>  
  
    2.  <span data-ttu-id="9d4bb-181">在 [緩衝區記憶體大小上限]\*\*\*\* 方塊中，指定要使用的緩衝區記憶體最大數量。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-181">In the **Maximum buffer memory size** box, specify the maximum amount of buffer memory to use.</span></span> <span data-ttu-id="9d4bb-182">當到達這個值時，將會捨棄現有的事件。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-182">The existing events are dropped when this value is reached.</span></span>  
  
    3.  <span data-ttu-id="9d4bb-183">如果您想要保留緩衝區中每一個類型的特定事件數目，請選取 [在緩衝區已滿時保留指定的事件數目 (每一類型)]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-183">If you want to keep a specific number of events of each type in the buffer, select the **Keep a specified number of events (per type) when the buffer is full** check box.</span></span>  
  
    4.  <span data-ttu-id="9d4bb-184">在 [要保留的事件數目 (每一類型)]\*\*\*\* 方塊中，使用向上和向下箭號來輸入或選取您想要保留的事件數目 (每一類型)。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-184">In the **Number of events to keep (per type)** box, enter or select the number of events (per type) that you want to keep by using the up and down arrows.</span></span>  
  
##  <a name="summary"></a><a name="BKMK_Summary"></a> <span data-ttu-id="9d4bb-185">摘要</span><span class="sxs-lookup"><span data-stu-id="9d4bb-185">Summary</span></span>  
 <span data-ttu-id="9d4bb-186">在 [摘要]\*\*\*\* 頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9d4bb-186">On the **Summary** page, do the following:</span></span>  
  
1.  <span data-ttu-id="9d4bb-187">請確定您的選擇正確無誤。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-187">Make sure that your selections are correct.</span></span> <span data-ttu-id="9d4bb-188">展開事件工作階段節點，以確認您的所有選擇都將包含在事件工作階段中。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-188">Expand the event session nodes to verify that all of your selections will be included in the event session.</span></span>  
  
2.  <span data-ttu-id="9d4bb-189">按一下 [指令碼]\*\*\*\*，將工作階段建立指令碼匯出到新的查詢編輯器視窗。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-189">Click **Script** to export the session creation script to a new Query Editor window.</span></span>  
  
3.  <span data-ttu-id="9d4bb-190">按一下 [完成]\*\*\*\* 建立事件工作階段。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-190">Click **Finish** to create the event session.</span></span>  
  
##  <a name="create-event-session"></a><a name="BKMK_CreateEventSession"></a><span data-ttu-id="9d4bb-191">建立事件會話</span><span class="sxs-lookup"><span data-stu-id="9d4bb-191">Create Event Session</span></span>  
 <span data-ttu-id="9d4bb-192">在 [建立事件工作階段]\*\*\*\* 頁面上，於成功建立您的事件工作階段之後執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9d4bb-192">On the **Create Event Session** page, after your event session has been successfully created, do the following:</span></span>  
  
1.  <span data-ttu-id="9d4bb-193">按一下 [在工作階段建立後立即啟動事件工作階段]\*\*\*\* 即可在關閉精靈之後啟動工作階段。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-193">Click **Start the event session immediately after session creation** to start the session after you close the wizard.</span></span> <span data-ttu-id="9d4bb-194">在您建立事件工作階段之後必須立即啟動此工作階段，才能監看即時資料。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-194">You must start the event session immediately after you create the session to be able to watch live data.</span></span>  
  
2.  <span data-ttu-id="9d4bb-195">按一下 [擷取同時監看畫面上的即時資料]\*\*\*\*，檢視事件工作階段的即時資料。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-195">Click **Watch live data on screen as it is captured** to view live data for your event session.</span></span> <span data-ttu-id="9d4bb-196">建立工作階段之後，即時資料將會立即開始顯示追蹤。</span><span class="sxs-lookup"><span data-stu-id="9d4bb-196">The live data will start displaying tracing immediately after the session is created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d4bb-197">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d4bb-197">See Also</span></span>  
 [<span data-ttu-id="9d4bb-198">使用新增工作階段對話方塊建立擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="9d4bb-198">Create an Extended Events Session Using the New Session Dialog</span></span>](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md)  
  
  
