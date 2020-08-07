---
title: 在資料警示設計工具中建立資料警示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8464ab9d-afe1-4490-955f-9f3319bcbf8d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 19c3001d4663848c009a353baa068f237d4a0b5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703954"
---
# <a name="create-a-data-alert-in-data-alert-designer"></a><span data-ttu-id="65de3-102">在資料警示設計工具中建立資料警示</span><span class="sxs-lookup"><span data-stu-id="65de3-102">Create a Data Alert in Data Alert Designer</span></span>
  <span data-ttu-id="65de3-103">您可在 [資料警示設計工具] 中建立資料警示定義。</span><span class="sxs-lookup"><span data-stu-id="65de3-103">You create data alert definitions in Data Alert Designer.</span></span> <span data-ttu-id="65de3-104">儲存警示定義之後，可以在 [資料警示設計工具] 中再次開啟、編輯，然後再次儲存警示定義。</span><span class="sxs-lookup"><span data-stu-id="65de3-104">After you save the alert definitions, you can reopen, edit, and then resave them in Data Alert Designer.</span></span> <span data-ttu-id="65de3-105">如需編輯警示定義的相關資訊，請參閱 [在資料警示管理員中管理我的資料警示](manage-my-data-alerts-in-data-alert-manager.md) 和 [在警示設計工具中編輯資料警示](edit-a-data-alert-in-alert-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="65de3-105">For information about editing alert definitions, see [Manage My Data Alerts in Data Alert Manager](manage-my-data-alerts-in-data-alert-manager.md) and [Edit a Data Alert in Alert Designer](edit-a-data-alert-in-alert-designer.md).</span></span>

### <a name="to-create-a-data-alert-definition"></a><span data-ttu-id="65de3-106">建立資料警示定義</span><span class="sxs-lookup"><span data-stu-id="65de3-106">To create a data alert definition</span></span>

1.  <span data-ttu-id="65de3-107">尋找包含要為其建立資料警示定義之報表的 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="65de3-107">Locate the SharePoint library that contains the report that you want to create a data alert definition for.</span></span>

2.  <span data-ttu-id="65de3-108">按一下報表。</span><span class="sxs-lookup"><span data-stu-id="65de3-108">Click the report.</span></span>

     <span data-ttu-id="65de3-109">報表就會執行。</span><span class="sxs-lookup"><span data-stu-id="65de3-109">The report runs.</span></span> <span data-ttu-id="65de3-110">如果報表參數化，請確認報表顯示的是您要接收其警示訊息的資料。</span><span class="sxs-lookup"><span data-stu-id="65de3-110">If the report is parameterized, verify that the report shows the data that you want to receive alert messages about.</span></span> <span data-ttu-id="65de3-111">如果沒有看見您需要的資料行或值，則可能需要使用不同的參數值重新執行報表。</span><span class="sxs-lookup"><span data-stu-id="65de3-111">If you do not see the columns or values you are interested in, you might want to rerun the report, using different parameter values.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="65de3-112">您選擇執行報表的參數值會儲存在警示定義中，並且在處理警示定義的過程中重新執行報表時使用。</span><span class="sxs-lookup"><span data-stu-id="65de3-112">The parameter values you chose to run the report are saved in the alert definition and will be used when report is rerun as a step in processing the alert definition.</span></span> <span data-ttu-id="65de3-113">若要使用不同的參數值，您必須建立新的警示定義。</span><span class="sxs-lookup"><span data-stu-id="65de3-113">To use different parameter values, you must create a new alert definition.</span></span>

3.  <span data-ttu-id="65de3-114">在 [動作]\*\*\*\* 功能表上，按一下 [新增資料警示]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65de3-114">On the **Actions** menu, click **New Data Alert**.</span></span>

     <span data-ttu-id="65de3-115">下圖顯示 [動作]\*\*\*\* 功能表。</span><span class="sxs-lookup"><span data-stu-id="65de3-115">The following picture shows the **Actions** menu.</span></span>

     <span data-ttu-id="65de3-116">![從 SharePoint 文件庫開啟警示設計工具](media/rs-openalertdesigneriw.gif "從 SharePoint 文件庫開啟警示設計工具")</span><span class="sxs-lookup"><span data-stu-id="65de3-116">![Open Alert Designer from SharePoint library](media/rs-openalertdesigneriw.gif "Open Alert Designer from SharePoint library")</span></span>

     <span data-ttu-id="65de3-117">[資料警示設計工具] 隨即開啟，並且在資料表中顯示報表所產生之第一個資料摘要的前 100 個資料列。</span><span class="sxs-lookup"><span data-stu-id="65de3-117">The Data Alert Designer opens, showing the first 100 rows of the first data feed that the report generates in a table.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="65de3-118">如果您未看見 [新資料警示]\*\*\*\* 選項，表示 SharePoint 網站上未設定警示服務，或是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本未包含資料警示。</span><span class="sxs-lookup"><span data-stu-id="65de3-118">If you do not see the **New Data Alert** option, the alerting service is not configured on the SharePoint site or the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] edition does not include data alerts.</span></span> <span data-ttu-id="65de3-119">如需詳細資訊，請參閱 [Reporting Services SharePoint 服務和服務應用程式](../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="65de3-119">For more information, see [Reporting Services SharePoint Service and Service Applications](../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md).</span></span>
    > 
    >  <span data-ttu-id="65de3-120">如果 [新資料警示]\*\*\*\* 選項呈現灰色，表示報表資料來源設定為使用整合式安全性認證或提示輸入認證。</span><span class="sxs-lookup"><span data-stu-id="65de3-120">If the **New Data Alert** option is grayed, the report data source is configured to use integrated security credentials or prompt for credentials.</span></span> <span data-ttu-id="65de3-121">若要使用 [新資料警示]\*\*\*\* 選項，則必須將資料來源更新為使用預存程序或不使用認證。</span><span class="sxs-lookup"><span data-stu-id="65de3-121">To make the **New Data Alert** option available, you must update the data source to use stored credentials or no credentials.</span></span>

     <span data-ttu-id="65de3-122">資料摘要的名稱會出現在 [報表資料名稱]\*\*\*\* 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="65de3-122">The name of the data feed appears in **Report data name** drop-down list.</span></span>

4.  <span data-ttu-id="65de3-123">您也可以選擇性地從 [報表資料名稱]\*\*\*\* 下拉式清單中選取不同的資料摘要。</span><span class="sxs-lookup"><span data-stu-id="65de3-123">Optionally, select a different data feed in the **Report data name** drop-down list.</span></span>

     <span data-ttu-id="65de3-124">如果未從報表產生任何資料摘要，則無法為該報表建立警示定義。</span><span class="sxs-lookup"><span data-stu-id="65de3-124">If no data feed is generated from the report, you cannot create an alert definition for the report.</span></span> <span data-ttu-id="65de3-125">報表的配置決定每一個資料摘要的內容。</span><span class="sxs-lookup"><span data-stu-id="65de3-125">The layout of the report determines the content of each data feed.</span></span> <span data-ttu-id="65de3-126">如需詳細資訊，請參閱[從報表產生資料摘要 &#40;報表產生器和 SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="65de3-126">For more information see, [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).</span></span>

5.  <span data-ttu-id="65de3-127">(選擇性) 在 [警示名稱]\*\*\*\* 文字方塊中，將預設名稱更新為更有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="65de3-127">Optionally, in the **Alert name** text box, update the default name to be more meaningful.</span></span>

     <span data-ttu-id="65de3-128">警示定義的預設名稱就是報表名稱。</span><span class="sxs-lookup"><span data-stu-id="65de3-128">The default name of the alert definition is the name of the report.</span></span> <span data-ttu-id="65de3-129">警示定義名稱不一定要是唯一的，不過這樣可能造成您之後在 [資料警示管理員] 中檢視警示清單時，難以區分各個警示的情況。</span><span class="sxs-lookup"><span data-stu-id="65de3-129">Alert definition names do not have to be unique, which can make it difficult to tell them apart when you later view the list of your alerts in Data Alert Manager.</span></span> <span data-ttu-id="65de3-130">建議您使用有意義且唯一的警示定義名稱。</span><span class="sxs-lookup"><span data-stu-id="65de3-130">It is recommended that you use meaningful and unique names for your alert definitions.</span></span>

6.  <span data-ttu-id="65de3-131">(選擇性) 將預設資料選項從 [資料摘要中的任何資料都有]\*\*\*\* 變更為 [資料摘要中的任何資料都沒有]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65de3-131">Optionally, change the default data option from **any data in the data feed has** to **no data in the data feed has**.</span></span>

7.  <span data-ttu-id="65de3-132">按一下 [新增規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65de3-132">Click **Add rule**.</span></span>

     <span data-ttu-id="65de3-133">資料摘要中的資料行清單隨即出現。</span><span class="sxs-lookup"><span data-stu-id="65de3-133">A list of the columns in the data feed appears.</span></span>

8.  <span data-ttu-id="65de3-134">在清單中，選取要在規則中使用的資料行，然後選取比較運算子並輸入臨界值。</span><span class="sxs-lookup"><span data-stu-id="65de3-134">In the list, select the column that you want to use in the rule, and then select a comparison operator and enter the threshold value.</span></span>

     <span data-ttu-id="65de3-135">根據所選取資料行的資料類型而定，會列出不同的比較運算子。</span><span class="sxs-lookup"><span data-stu-id="65de3-135">Depending on the data type of the selected column, different comparison operators are listed.</span></span> <span data-ttu-id="65de3-136">如果資料行的資料類型為日期，則規則的臨界值旁邊會顯示一個行事曆圖示。</span><span class="sxs-lookup"><span data-stu-id="65de3-136">If the column has a date data type, a calendar icon displays next to threshold value for the rule.</span></span> <span data-ttu-id="65de3-137">您可以藉由按一下行事曆中的日期或輸入日期的方式來輸入資料。</span><span class="sxs-lookup"><span data-stu-id="65de3-137">You can enter a data by clicking a date in the calendar or typing the date.</span></span>

     <span data-ttu-id="65de3-138">資料警示設計工具提供兩種比較模式：[值輸入模式]\*\*\*\* 和 [欄位選取模式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65de3-138">Data Alert Designer provides two comparison modes: **Value Entry Mode** and **Field Selection Mode**.</span></span> <span data-ttu-id="65de3-139">預設模式為 [值輸入模式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65de3-139">The default mode is **Value Entry Mode**.</span></span> <span data-ttu-id="65de3-140">只有在處於 [值輸入模式]\*\*\*\* 且使用 [is]\*\*\*\* 比較時，才可以新增 OR 子句。</span><span class="sxs-lookup"><span data-stu-id="65de3-140">You can add OR clauses only when you are in **Value Entry Mode** and are using the **is** comparison.</span></span>

9. <span data-ttu-id="65de3-141">若要新增 OR 子句，請按一下向下箭頭，然後按一下 [值輸入模式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65de3-141">To add an OR clause, click the down-arrow, and then click **Value Entry Mode**.</span></span>

10. <span data-ttu-id="65de3-142">輸入比較值。</span><span class="sxs-lookup"><span data-stu-id="65de3-142">Type the comparison value.</span></span>

11. <span data-ttu-id="65de3-143">（選擇性）按一下省略號\*\* ( ...] ) \*\* 。</span><span class="sxs-lookup"><span data-stu-id="65de3-143">Optionally, click the ellipsis **(...)** again.</span></span>

     <span data-ttu-id="65de3-144">省略號\*\* ( ... ) \*\*會出現在包含第一個子句的那一行。</span><span class="sxs-lookup"><span data-stu-id="65de3-144">The ellipsis **(...)** appears on the line that contains the first clause.</span></span>

     <span data-ttu-id="65de3-145">OR 子句將加入 AND 規則底下，且包含在規則內。</span><span class="sxs-lookup"><span data-stu-id="65de3-145">An OR clause is added below and within the AND rule.</span></span>

12. <span data-ttu-id="65de3-146">(選擇性) 按一下向下箭頭，選取 [欄位選取模式]\*\*\*\*，然後選取清單中的資料行。</span><span class="sxs-lookup"><span data-stu-id="65de3-146">Optionally, click the down-arrow, select **Field Selection Mode**, and then select a column in the list.</span></span>

     <span data-ttu-id="65de3-147">您會發現，您按一下以加入 OR 子句的省略號\*\* ( ... ) \*\*已消失。</span><span class="sxs-lookup"><span data-stu-id="65de3-147">You will notice that the ellipsis **(...)** that you click to add OR clauses has disappeared.</span></span>

13. <span data-ttu-id="65de3-148">(選擇性) 再按一次 [新增規則]\*\*\*\* 即可新增其他規則。</span><span class="sxs-lookup"><span data-stu-id="65de3-148">Optionally, click **Add rule** again to add additional rules.</span></span>

     <span data-ttu-id="65de3-149">規則是使用 AND 邏輯運算子結合。</span><span class="sxs-lookup"><span data-stu-id="65de3-149">The rules are combined by using the AND logical operator.</span></span>

14. <span data-ttu-id="65de3-150">在循環清單中選取一個選項。</span><span class="sxs-lookup"><span data-stu-id="65de3-150">Select an option in the recurrence list.</span></span> <span data-ttu-id="65de3-151">根據循環的類型輸入間隔。</span><span class="sxs-lookup"><span data-stu-id="65de3-151">Depending on the type of recurrence, enter an interval.</span></span>

15. <span data-ttu-id="65de3-152">(選擇性) 按一下 [進階]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65de3-152">Optionally, click **Advanced**.</span></span>

16. <span data-ttu-id="65de3-153">(選擇性) 輸入不同的日期，或開啟行事曆，然後按一下行事曆中的日期，藉此變更警示訊息開始的日期。</span><span class="sxs-lookup"><span data-stu-id="65de3-153">Optionally, change the date that the alert message starts on by typing a different date or opening the calendar, and then clicking a date in the calendar.</span></span>

     <span data-ttu-id="65de3-154">預設的開始日期為目前日期。</span><span class="sxs-lookup"><span data-stu-id="65de3-154">The default start date is the current date.</span></span>

17. <span data-ttu-id="65de3-155">(選擇性) 選取位於 [警示停止時間]\*\*\*\* 旁邊的核取方塊，然後選擇要停止警示訊息的日期。</span><span class="sxs-lookup"><span data-stu-id="65de3-155">Optionally, select the checkbox located next to **Stop alert on**, and then choose a date to stop the alert message.</span></span>

     <span data-ttu-id="65de3-156">根據預設，警示訊息沒有停止日期。</span><span class="sxs-lookup"><span data-stu-id="65de3-156">By default, an alert message has no stop date.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="65de3-157">停止警示訊息並不會刪除警示定義。</span><span class="sxs-lookup"><span data-stu-id="65de3-157">Stopping an alert message does not delete the alert definition.</span></span> <span data-ttu-id="65de3-158">停止警示訊息之後，可以藉由更新開始和停止日期將它重新啟動。</span><span class="sxs-lookup"><span data-stu-id="65de3-158">After you stop an alert message, you can restart it by updating the start and stop dates.</span></span> <span data-ttu-id="65de3-159">如需刪除警示定義的相關資訊，請參閱 [在資料警示管理員中管理我的資料警示](manage-my-data-alerts-in-data-alert-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="65de3-159">For information about deleting alert definitions, see [Manage My Data Alerts in Data Alert Manager](manage-my-data-alerts-in-data-alert-manager.md).</span></span>

18. <span data-ttu-id="65de3-160">(選擇性) 清除 [僅在結果變更時傳送訊息]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="65de3-160">Optionally, clear the **Send message only if results change** checkbox.</span></span>

     <span data-ttu-id="65de3-161">如果您經常傳送警示訊息，重複的資訊可能會造成困擾，因此您不應清除此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="65de3-161">If you send alert messages frequently, redundant information might not be welcome and you should not clear this checkbox.</span></span>

19. <span data-ttu-id="65de3-162">輸入警示訊息收件者的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="65de3-162">Enter the email addresses of alert message recipients.</span></span> <span data-ttu-id="65de3-163">以分號分隔地址。</span><span class="sxs-lookup"><span data-stu-id="65de3-163">Separate addresses with semicolons.</span></span>

     <span data-ttu-id="65de3-164">如果警示定義建立者的電子郵件地址可用，就會新增至 [收件者]\*\*\*\* 方塊中。</span><span class="sxs-lookup"><span data-stu-id="65de3-164">If the email address of the person who created the alert definition is available, it is added to the **Recipient(s)** box.</span></span>

20. <span data-ttu-id="65de3-165">(選擇性) 在 [主旨]\*\*\*\* 文字方塊中更新警示訊息的 [主旨]。</span><span class="sxs-lookup"><span data-stu-id="65de3-165">Optionally, in the **Subject** text box, update the Subject line of the alert message.</span></span>

     <span data-ttu-id="65de3-166">預設的主旨是**的 \<data alert name> 資料警示**。</span><span class="sxs-lookup"><span data-stu-id="65de3-166">The default Subject is **Data alert for \<data alert name>**.</span></span>

21. <span data-ttu-id="65de3-167">(選擇性) 在 [描述]\*\*\*\* 文字方塊中輸入警示訊息的描述。</span><span class="sxs-lookup"><span data-stu-id="65de3-167">Optionally, in the **Description** text box, type a description of the alert message.</span></span>

22. <span data-ttu-id="65de3-168">按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="65de3-168">Click **Save**.</span></span>

## <a name="see-also"></a><span data-ttu-id="65de3-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65de3-169">See Also</span></span>
 <span data-ttu-id="65de3-170">警示系統管理員的[資料警示設計](../../2014/reporting-services/data-alert-designer.md)工具[資料警示管理器](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) [Reporting Services 資料警示](../ssms/agent/alerts.md)</span><span class="sxs-lookup"><span data-stu-id="65de3-170">[Data Alert Designer](../../2014/reporting-services/data-alert-designer.md) [Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) [Reporting Services Data Alerts](../ssms/agent/alerts.md)</span></span>


