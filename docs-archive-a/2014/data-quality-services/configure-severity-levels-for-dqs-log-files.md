---
title: 設定 DQS 記錄檔的嚴重性層級 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.log.f1
helpviewer_keywords:
- severity levels
- log files,severity levels
- dqs log files,severity levels
- logging,severity levels
- configure severity levels
ms.assetid: 66ffcdec-4bf7-4dd5-a221-fd9baefeeef4
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 46fb9de1fbe1e3e59b20bb2ac7afeebe19ba2da5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687171"
---
# <a name="configure-severity-levels-for-dqs-log-files"></a><span data-ttu-id="47b70-102">為 DQS 記錄檔設定嚴重性層級</span><span class="sxs-lookup"><span data-stu-id="47b70-102">Configure Severity Levels for DQS Log Files</span></span>
  <span data-ttu-id="47b70-103">此主題描述如何使用 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] 來針對 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)](DQS) 中的各種不同活動和模組設定嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="47b70-103">This topic describes how to configure severity levels for various activities and modules in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) by using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="47b70-104">嚴重性層級會定義 DQS 中發生之事件的強度。</span><span class="sxs-lookup"><span data-stu-id="47b70-104">Severity levels define the intensity of events that occur in DQS.</span></span> <span data-ttu-id="47b70-105">DQS 事件具有以下的嚴重性層級 (依照嚴重性的遞減順序排列)：</span><span class="sxs-lookup"><span data-stu-id="47b70-105">DQS events have the following severity levels, in the decreasing order of severity:</span></span>  
  
-   <span data-ttu-id="47b70-106">**嚴重錯誤**：可能會造成嚴重/非預期結果的嚴重執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="47b70-106">**Fatal**: Critical runtime errors that might cause severe/unexpected results.</span></span>  
  
-   <span data-ttu-id="47b70-107">**錯誤**：其他執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="47b70-107">**Error**: Other runtime errors.</span></span>  
  
-   <span data-ttu-id="47b70-108">**警告**：可能會造成錯誤之事件的警告。</span><span class="sxs-lookup"><span data-stu-id="47b70-108">**Warn**: Warning about events that might result in an error.</span></span>  
  
-   <span data-ttu-id="47b70-109">**資訊**：非錯誤或警告之一般事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="47b70-109">**Info**: Information about general events that is not an error or a warning.</span></span> <span data-ttu-id="47b70-110">例如，DQS 處理序已啟動。</span><span class="sxs-lookup"><span data-stu-id="47b70-110">For example, a DQS process has started.</span></span>  
  
-   <span data-ttu-id="47b70-111">**偵錯**：有關事件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="47b70-111">**Debug**: Detailed (verbose) information about the event.</span></span>  
  
 <span data-ttu-id="47b70-112">藉由設定各種 DQS 活動和模組的嚴重性層級，您會針對各自 DQS 活動或模組來篩選想要記錄的資訊以及寫入 DQS 記錄檔的資訊。</span><span class="sxs-lookup"><span data-stu-id="47b70-112">By configuring severity levels for various DQS activities and modules, you are filtering the information that you want to be logged, and written to the DQS log file for the respective DQS activity or module.</span></span> <span data-ttu-id="47b70-113">例如，如果您將 DQS 活動的嚴重性層級設定為 **[警告]**，只會記錄與 DQS 活動相關之警告和更高嚴重性層級的訊息 (錯誤和嚴重錯誤)。</span><span class="sxs-lookup"><span data-stu-id="47b70-113">For example, if you set the severity level of a DQS activity to **Warn**, only warning and higher severity messages (Error and Fatal) associated with the DQS activity will be logged.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="47b70-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="47b70-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="47b70-115">Security</span><span class="sxs-lookup"><span data-stu-id="47b70-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="47b70-116">權限</span><span class="sxs-lookup"><span data-stu-id="47b70-116">Permissions</span></span>  
 <span data-ttu-id="47b70-117">您必須擁有 DQS_MAIN 資料庫的 dqs_administrator 角色，才能設定記錄嚴重性設定。</span><span class="sxs-lookup"><span data-stu-id="47b70-117">You must have the dqs_administrator role on the DQS_MAIN database to configure log severity settings.</span></span>  
  
##  <a name="configure-severity-levels-at-activity-level"></a><a name="ConfigureActivity"></a><span data-ttu-id="47b70-118">在活動層級設定嚴重性層級</span><span class="sxs-lookup"><span data-stu-id="47b70-118">Configure Severity Levels at Activity Level</span></span>  
 <span data-ttu-id="47b70-119">您可以在 DQS 中設定以下活動的記錄嚴重性設定：定義域管理、知識探索、比對原則、資料清理、資料比對和參考資料服務。</span><span class="sxs-lookup"><span data-stu-id="47b70-119">You can configure log severity settings for the following activities in DQS: domain management, knowledge discovery, matching policy, data cleansing, data matching, and reference data services.</span></span> <span data-ttu-id="47b70-120">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="47b70-120">To do so:</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="47b70-121">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="47b70-121">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="47b70-122">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，按一下 **[組態]**。</span><span class="sxs-lookup"><span data-stu-id="47b70-122">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="47b70-123">接下來，按一下 [**記錄檔設定**] 索引標籤。以下列出您可以選取嚴重性層級的 DQS 活動： [**定義域管理**]、[**知識探索**]、[**清理專案] (例如 [rds) **]、[比對**原則] 和**[比對專案] 和 [ **rds**]。</span><span class="sxs-lookup"><span data-stu-id="47b70-123">Next, click the **Log Settings** tab. The following DQS activities are listed for which you can select a severity level: **Domain Management**, **Knowledge Discovery**, **Cleansing Project (Ex. RDS)**, **Matching Policy and Matching Project**, and **RDS**.</span></span>  
  
4.  <span data-ttu-id="47b70-124">如果是 DQS 活動，請選取您想要記錄的嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="47b70-124">For a DQS activity, select the severity level that you want to be logged.</span></span> <span data-ttu-id="47b70-125">您可以選取下列其中一項： **[嚴重錯誤]**、 **[錯誤]**、 **[警告]**、 **[資訊]** 和 **[偵錯]**。</span><span class="sxs-lookup"><span data-stu-id="47b70-125">You can select one among the following: **Fatal**, **Error**, **Warn**, **Info**, and **Debug**.</span></span> <span data-ttu-id="47b70-126">例如，如果您希望在知識探索活動中，只將嚴重訊息寫入 DQS 記錄檔，請針對 **[知識探索]** 活動於下拉式清單中選取 **[嚴重錯誤]** 。</span><span class="sxs-lookup"><span data-stu-id="47b70-126">For example, if you want only fatal messages to be written to the DQS log files for the knowledge discovery activity, select **Fatal** in the drop-down list against the **Knowledge Discovery** activity.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="47b70-127">預設會針對每一個活動選取 **[錯誤]** 。</span><span class="sxs-lookup"><span data-stu-id="47b70-127">By default, **Error** is selected for each of the activities.</span></span> <span data-ttu-id="47b70-128">這表示，預設會針對每一個活動將錯誤和嚴重訊息寫入 DQS 記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="47b70-128">This implies that error and fatal messages will be written to the DQS log files for each activity, by default.</span></span>  
  
5.  <span data-ttu-id="47b70-129">按一下 **關閉**。</span><span class="sxs-lookup"><span data-stu-id="47b70-129">Click **Close**.</span></span>  
  
##  <a name="configure-severity-levels-at-module-level-advanced"></a><a name="ConfigureModule"></a><span data-ttu-id="47b70-130">設定模組層級 (Advanced) 的嚴重性等級</span><span class="sxs-lookup"><span data-stu-id="47b70-130">Configure Severity Levels at Module Level (Advanced)</span></span>  
 <span data-ttu-id="47b70-131">**[記錄檔設定]** 索引標籤中的 **[進階]** 區段可讓您在模組層級設定記錄嚴重性設定。</span><span class="sxs-lookup"><span data-stu-id="47b70-131">The **Advanced** section in the **Log Settings** tab enables you to configure log severity settings at a module level.</span></span> <span data-ttu-id="47b70-132">模組是 DQS 系統組件，可在 DQS 中實作某項功能內的各種不同功能。</span><span class="sxs-lookup"><span data-stu-id="47b70-132">Modules are DQS system assemblies that implement various functionalities within a feature in DQS.</span></span> <span data-ttu-id="47b70-133">例如，定義域管理活動包含類似以下的各種功能：定義定義域規則、定義規則條件、定義複合定義域的跨定義域規則等。</span><span class="sxs-lookup"><span data-stu-id="47b70-133">For example, the domain management activity contains various functionalities such as defining domain rules, defining rule conditions, defining cross-domain rules for composite domains, and so on.</span></span>  
  
 <span data-ttu-id="47b70-134">有時活動層級的資料粒度層級並不夠。</span><span class="sxs-lookup"><span data-stu-id="47b70-134">At times, the granularity level at the activity level is not sufficient.</span></span> <span data-ttu-id="47b70-135">您可能會想要調查活動內的特定模組中是否發生問題。</span><span class="sxs-lookup"><span data-stu-id="47b70-135">You might want to investigate an issue that is occurring in a particular module within an activity.</span></span> <span data-ttu-id="47b70-136">它可幫助您選擇在模組層級設定記錄嚴重性，以便更精確地隔離和追蹤問題。</span><span class="sxs-lookup"><span data-stu-id="47b70-136">It helps to have an option to configure log severities at the module level to isolate and track the issue more precisely.</span></span>  
  
 <span data-ttu-id="47b70-137">在活動層級指定的記錄嚴重性設定會決定組成活動之所有模組的記錄嚴重性設定。</span><span class="sxs-lookup"><span data-stu-id="47b70-137">The log severity setting specified at the activity level determines the log severity setting of all the modules that constitute the activity.</span></span> <span data-ttu-id="47b70-138">但是，如果活動層級和模組層級的記錄嚴重性設定之間有任何衝突，則會考量模組層級的嚴重性設定。</span><span class="sxs-lookup"><span data-stu-id="47b70-138">However, if there is any conflict between the log severity settings at the activity and module levels, the severity settings at the module level are considered.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="47b70-139">根據預設， **Microsoft.Ssdqs.Core.Startup** 模組會在 **[進階]** 區段中預先設定，且嚴重性層級設定為 **[資訊]**。</span><span class="sxs-lookup"><span data-stu-id="47b70-139">By default, the **Microsoft.Ssdqs.Core.Startup** module is preconfigured in the **Advanced** section with the severity level set as **Info**.</span></span> <span data-ttu-id="47b70-140">這樣做是為了記錄嚴重性為資訊或更高層級 (警告、錯誤和嚴重錯誤) 的事件，這些事件與啟動和停止 DQS 服務有關。</span><span class="sxs-lookup"><span data-stu-id="47b70-140">This is done to enable logging of events of severity Info and higher (Warn, Error, and Fatal) that are related to starting and stopping of DQS services.</span></span>  
> -   <span data-ttu-id="47b70-141">只有當您是熟悉 DQS 系統組件的資深 DQS 使用者時，才能在模組層級設定記錄嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="47b70-141">You should configure log severity levels at the module level only if you are an advanced DQS user who is familiar with the DQS system assemblies.</span></span>  
  
 <span data-ttu-id="47b70-142">若要在模組層級設定記錄嚴重性層級：</span><span class="sxs-lookup"><span data-stu-id="47b70-142">To configure log severity levels at the module level:</span></span>  
  
1.  <span data-ttu-id="47b70-143">在 **[記錄檔設定]** 索引標籤中，針對 **[進階]** 按一下向下箭號，以顯示區域。</span><span class="sxs-lookup"><span data-stu-id="47b70-143">In the **Log Settings** tab, click the down arrow against **Advanced** to display the area.</span></span>  
  
2.  <span data-ttu-id="47b70-144">在出現的方格中，從 **[模組]** 資料行的下拉式清單中選取模組名稱。</span><span class="sxs-lookup"><span data-stu-id="47b70-144">In the grid that appears, select a module name from the drop-down list in the **Module** column.</span></span>  
  
3.  <span data-ttu-id="47b70-145">接下來，從 **[嚴重性]** 資料行的下拉式清單中選取模組的嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="47b70-145">Next, select a severity level for the module from the drop-down list in the **Severity** column.</span></span> <span data-ttu-id="47b70-146">您可以選取下列其中一項： **[嚴重錯誤]**、 **[錯誤]**、 **[警告]**、 **[資訊]** 和 **[偵錯]**。</span><span class="sxs-lookup"><span data-stu-id="47b70-146">You can select one among the following: **Fatal**, **Error**, **Warn**, **Info**, and **Debug**.</span></span>  
  
     <span data-ttu-id="47b70-147">例如在定義域管理活動中，您可以為定義域規則定義功能設定與定義域管理活動不同的資料粒度層級，方法是選取 **Microsoft.Ssdqs.DomainRules.Define** 模組，並選取不同的記錄嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="47b70-147">For example, within the domain management activity, you can set a different granularity level for the domain rule definition functionality than the domain management activity by selecting the **Microsoft.Ssdqs.DomainRules.Define** module, and selecting a different log severity level.</span></span> <span data-ttu-id="47b70-148">同樣地，您可以針對跨定義域規則功能設定不同的資料粒度層級，方法是選取 **Microsoft.Ssdqs.DomainRules.Condition.CrossDomain** 模組，並選取不同的記錄嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="47b70-148">Similarly, you can set a different granularity level for the cross-domain rule functionality by selecting the **Microsoft.Ssdqs.DomainRules.Condition.CrossDomain** module, and selecting a different log severity level.</span></span>  
  
4.  <span data-ttu-id="47b70-149">必要時針對其他模組重複步驟 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="47b70-149">Repeat steps 2 and 3 for other modules, if required.</span></span> <span data-ttu-id="47b70-150">您也可以在方格中加入或刪除資料列，方法是按一下 **[加入模組]** 和 **[移除模組]** 圖示。</span><span class="sxs-lookup"><span data-stu-id="47b70-150">You can also add or delete rows to the grid by clicking the **Add Module** and **Remove Module** icons.</span></span>  
  
5.  <span data-ttu-id="47b70-151">按一下 [關閉] 。</span><span class="sxs-lookup"><span data-stu-id="47b70-151">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b70-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47b70-152">See Also</span></span>  
 [<span data-ttu-id="47b70-153">設定 DQS 記錄檔的進階設定</span><span class="sxs-lookup"><span data-stu-id="47b70-153">Configure Advanced Settings for DQS Log Files</span></span>](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)  
  
  
