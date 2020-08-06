---
title: 資料警示設計工具 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- editing, data alerts
- updating, data alerts
- editing, alerts
- updating, alerts
- creating, data alerts
- creating, alerts
ms.assetid: b2018116-cf1a-4e54-b29c-39e0ca2bda77
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 47640a086ab85d0cb150bef66881684e2a9a774a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597657"
---
# <a name="data-alert-designer"></a><span data-ttu-id="0efed-102">資料警示設計工具</span><span class="sxs-lookup"><span data-stu-id="0efed-102">Data Alert Designer</span></span>
  <span data-ttu-id="0efed-103">您可在 [資料警示設計工具] 中建立和編輯資料警示定義。</span><span class="sxs-lookup"><span data-stu-id="0efed-103">You create and edit data alert definitions in Data Alert Designer.</span></span> <span data-ttu-id="0efed-104">警示定義是中繼資料的集合，包括您感興趣的報表資料、報表資料必須符合才能建立資料警示執行個體和傳送資料警示訊息的規則、警示訊息的收件者等。</span><span class="sxs-lookup"><span data-stu-id="0efed-104">An alert definition is a collection of metadata, including the report data that you are interested in, the rules that report data must satisfy to create data alert instances and send data alert messages, the recipients of the alert message, and so forth.</span></span>

 <span data-ttu-id="0efed-105">若要建立警示定義，您需要執行一些相關工作：</span><span class="sxs-lookup"><span data-stu-id="0efed-105">To create an alert definition you do a number of related tasks:</span></span>

-   <span data-ttu-id="0efed-106">選取包括您要使用之資料的報表和報表資料摘要。</span><span class="sxs-lookup"><span data-stu-id="0efed-106">Select the report and the report data feed that includes data that you want to use.</span></span>

-   <span data-ttu-id="0efed-107">定義導致傳送警示的規則和子句。</span><span class="sxs-lookup"><span data-stu-id="0efed-107">Define the rules and clauses that cause an alert to be sent.</span></span> <span data-ttu-id="0efed-108">使用藉由 AND 運算子組合的多個子句時，規則可簡單也可複雜。</span><span class="sxs-lookup"><span data-stu-id="0efed-108">The rules can be simple or complex, using multiple clauses combined by AND operators.</span></span>

-   <span data-ttu-id="0efed-109">定義警示訊息傳送的頻率，以及警示開始和停止的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="0efed-109">Define the frequency that the alert message is sent and the date and time the alert starts and stops.</span></span> <span data-ttu-id="0efed-110">警示訊息可以只在結果變更時傳送。</span><span class="sxs-lookup"><span data-stu-id="0efed-110">Alert messages can be sent only when results change.</span></span>

-   <span data-ttu-id="0efed-111">指定警示訊息收件者的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="0efed-111">Specify the email addresses of alert message recipients.</span></span>

-   <span data-ttu-id="0efed-112">自訂警示訊息的 [主旨]\*\*\*\* 行。</span><span class="sxs-lookup"><span data-stu-id="0efed-112">Customize the **Subject** line of the alert message.</span></span>

-   <span data-ttu-id="0efed-113">提供要包含在警示訊息中的警示描述。</span><span class="sxs-lookup"><span data-stu-id="0efed-113">Provide a description of alert to include in alert message.</span></span>

> [!NOTE]
>  <span data-ttu-id="0efed-114">由於 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 資料警示功能只有在您安裝 SharePoint 模式的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 時才可使用，因此要建立其警示的報表必須儲存、部署或上傳到 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="0efed-114">Because the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] data alerts feature is available only when you install [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in SharePoint mode, the report on which you want to create an alert must be saved, deployed, or uploaded to a SharePoint document library.</span></span>
> 
>  <span data-ttu-id="0efed-115">資料警示不能在使用 Windows 整合式驗證或提示輸入認證的報表上建立。</span><span class="sxs-lookup"><span data-stu-id="0efed-115">Data alerts cannot be created on reports that use Windows Integrated authentication or prompts for credentials.</span></span> <span data-ttu-id="0efed-116">報表必須使用預存認證。</span><span class="sxs-lookup"><span data-stu-id="0efed-116">The reports must use stored credentials.</span></span> <span data-ttu-id="0efed-117">如需詳細資訊，請參閱 [指定報表資料來源的認證及連接資訊](report-data/specify-credential-and-connection-information-for-report-data-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="0efed-117">For more information, see [Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span>

 <span data-ttu-id="0efed-118">若要開啟 [資料警示設計工具]，請在報表工具列上按一下 [動作]\*\*\*\* 功能表上的 [新資料警示]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="0efed-118">To open Data Alert Designer, you click the **New Data Alert** option on the **Actions** menu on the report toolbar.</span></span> <span data-ttu-id="0efed-119">如果您看不見 [新資料警示]\*\*\*\* 選項，表示報表未設定為使用預存認證。</span><span class="sxs-lookup"><span data-stu-id="0efed-119">If you do not see the **New Data Alert** option, the report is not configured to use stored credentials.</span></span> <span data-ttu-id="0efed-120">您可以藉由從 SharePoint 文件庫更新報表資料來源的方式更新認證類型。</span><span class="sxs-lookup"><span data-stu-id="0efed-120">You can update the credential type by updating the report data source from the SharePoint library.</span></span>

##  <a name="data-alert-designer-user-interface"></a><a name="AlertDesigner"></a> <span data-ttu-id="0efed-121">資料警示設計工具使用者介面</span><span class="sxs-lookup"><span data-stu-id="0efed-121">Data Alert Designer User Interface</span></span>
 <span data-ttu-id="0efed-122">[資料警示設計工具] 分成下列幾個區域。</span><span class="sxs-lookup"><span data-stu-id="0efed-122">The Data Alert Designer is divided into areas.</span></span> <span data-ttu-id="0efed-123">選取報表資料摘要的區域、將規則加入條件中以建立簡單或複雜條件的區域等。</span><span class="sxs-lookup"><span data-stu-id="0efed-123">The area where you select the report data feed, the area where you create simple or complex conditions by adding rules to conditions, and so on.</span></span> <span data-ttu-id="0efed-124">下圖顯示 [資料警示設計工具] 中的區域。</span><span class="sxs-lookup"><span data-stu-id="0efed-124">The following picture shows the areas in Data Alert Designer.</span></span>

 <span data-ttu-id="0efed-125">![警示設計工具使用者介面中的區域](media/rs-alertdesigner.gif "警示設計工具使用者介面中的區域")</span><span class="sxs-lookup"><span data-stu-id="0efed-125">![Areas within the Alert Designer user interface](media/rs-alertdesigner.gif "Areas within the Alert Designer user interface")</span></span>
 

### <a name="alert-data"></a><span data-ttu-id="0efed-126">警示資料</span><span class="sxs-lookup"><span data-stu-id="0efed-126">Alert Data</span></span>
 <span data-ttu-id="0efed-127">當您開啟 [資料警示設計工具] 時，該工具會從報表產生並提供所有資料摘要，而 [報表資料名稱]\*\*\*\* 下拉式清單中會包含摘要的名稱。</span><span class="sxs-lookup"><span data-stu-id="0efed-127">When you open Data Alert Designer, it generates and makes available all the data feeds from the report and the **Report data name** drop-down list contains the names of the feeds.</span></span> <span data-ttu-id="0efed-128">資料摘要是在您建立警示定義時於記憶體中快取，而顯示資料摘要資料的資料表會在您於資料摘要之間切換以探索報表資料時迅速填入。</span><span class="sxs-lookup"><span data-stu-id="0efed-128">The data feeds are cached in memory while you are creating the alert definition and the table that display the data feed data is populated quickly when you switch between data feeds to explore the report data.</span></span>

 <span data-ttu-id="0efed-129">建立資料警示定義的第一個步驟，就是選取包含您要讓警示監視之資料的報表資料摘要。</span><span class="sxs-lookup"><span data-stu-id="0efed-129">The first step in creating a data alert definition is to select the report data feed that contains the data that you want the alert to monitor.</span></span> <span data-ttu-id="0efed-130">報表可以不包含任何資料摘要，或是包含多個資料摘要。</span><span class="sxs-lookup"><span data-stu-id="0efed-130">Reports can have zero or multiple data feeds.</span></span> <span data-ttu-id="0efed-131">如果報表沒有任何資料摘要，則無法為其建立警示。</span><span class="sxs-lookup"><span data-stu-id="0efed-131">If a report has no data feeds, you cannot create alerts on it.</span></span> <span data-ttu-id="0efed-132">資料摘要可以由任何資料區產生，包括所有類型的圖表、量測計、指標，以及資料表、矩陣和清單。</span><span class="sxs-lookup"><span data-stu-id="0efed-132">A data feed can be generated by any data region, including all types of charts, gauges, indicators as well as tables, matrices, and lists.</span></span>

 <span data-ttu-id="0efed-133">如果報表已參數化，而您未在報表資料摘要中看見預期的資料和資料行，請使用適當的參數值重新執行報表。</span><span class="sxs-lookup"><span data-stu-id="0efed-133">If the report is parameterized and you do not see the data and columns that you expect in the report data feed, rerun the report using the appropriate parameter values.</span></span> <span data-ttu-id="0efed-134">資料行和值必須出現在報表內，才會包含在資料摘要中。</span><span class="sxs-lookup"><span data-stu-id="0efed-134">The columns and values must be present in the report to be included in the data feed.</span></span>

 <span data-ttu-id="0efed-135">根據報表的配置而定，可能不容易了解報表擁有的資料摘要數目，或者哪一個資料摘要中包括哪些資料。</span><span class="sxs-lookup"><span data-stu-id="0efed-135">Depending on the layout of the report, it might not be intuitive how many data feeds a report has, nor what data is included in which data feed.</span></span> <span data-ttu-id="0efed-136">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]Atom 轉譯延伸模組會產生您搭配警示使用的資料摘要。</span><span class="sxs-lookup"><span data-stu-id="0efed-136">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]Atom rendering extension generates the data feeds that you use with alerts.</span></span> <span data-ttu-id="0efed-137">Atom 轉譯延伸模組會將報表資料提供為扁平化資料列集，也就是採用所有資料行擁有相同資料列數的表格格式提供。</span><span class="sxs-lookup"><span data-stu-id="0efed-137">The Atom rendering extension provides report data as flattened rowsets, a tabular format in which all columns have the same number of rows.</span></span> <span data-ttu-id="0efed-138">這些資料列集就是資料摘要的內容。</span><span class="sxs-lookup"><span data-stu-id="0efed-138">These rowsets are the contents of the data feeds.</span></span> <span data-ttu-id="0efed-139">由於報表配置時常相當複雜，且包含多個對等或巢狀資料區，因此需要多個資料摘要才能提供所有報表資料。</span><span class="sxs-lookup"><span data-stu-id="0efed-139">Because report layout is often complex and contains multiple peer or nested data regions, multiple data feeds are needed to make available all the report data..</span></span> <span data-ttu-id="0efed-140">如需如何從報表產生資料摘要的詳細資訊，請參閱[從多個報表產生資料摘要 &#40;報表產生器及 SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md)，並參閱[從報表產生資料摘要 &#40;報表產生器及 SSRS&#41;](report-builder/generate-data-feeds-from-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="0efed-140">For more information about how data feeds are generated from reports, see [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md) and see [Generate Data Feeds from a Report &#40;Report Builder and SSRS&#41;](report-builder/generate-data-feeds-from-a-report-report-builder-and-ssrs.md).</span></span>

 <span data-ttu-id="0efed-141">當您選擇資料摘要時，摘要中的資料會在 [資料警示設計工具] 的 [警示資料] 窗格中，顯示為具有資料列和資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="0efed-141">When you choose a data feed, the data from the feed displays in a table with rows and columns in the alert data pane of Data Alert Designer.</span></span> <span data-ttu-id="0efed-142">來自報表所使用資料來源或報表本身所指定資料行名稱和資料摘要的中繼資料，會填入您在資料條件中用來定義規則的欄位清單。</span><span class="sxs-lookup"><span data-stu-id="0efed-142">The metadata from the data source that the report uses or the report itself specifies the column names and the data feed populates the field list that you use to define rules in the data condition.</span></span> <span data-ttu-id="0efed-143">資料摘要還會提供中繼資料，像是限制值的資料表資料行之資料類型，以及您建立規則時在欄位中使用的比較運算子。</span><span class="sxs-lookup"><span data-stu-id="0efed-143">The data feed also provides metadata such as the data types of table columns that restrict the values and comparison operators that you can use with fields when you create the rules.</span></span>

 <span data-ttu-id="0efed-144">某些報表會有數百萬個資料列的資料。</span><span class="sxs-lookup"><span data-stu-id="0efed-144">Some reports have millions of rows of data.</span></span> <span data-ttu-id="0efed-145">資料表只會顯示摘要中前 100 個資料列的資料。</span><span class="sxs-lookup"><span data-stu-id="0efed-145">The table shows only the first 100 rows of data in the feed.</span></span>

### <a name="alert-name"></a><span data-ttu-id="0efed-146">警示名稱</span><span class="sxs-lookup"><span data-stu-id="0efed-146">Alert Name</span></span>
 <span data-ttu-id="0efed-147">根據預設，警示定義與報表的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="0efed-147">By default, the alert definition has the same name as the report.</span></span> <span data-ttu-id="0efed-148">您可以將警示名稱變更為更有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="0efed-148">You can change the alert name to be more meaningful.</span></span> <span data-ttu-id="0efed-149">這樣更方便您管理警示，判斷哪些警示需要更新、刪除等。</span><span class="sxs-lookup"><span data-stu-id="0efed-149">This makes it easier for you to manage your alerts, determining which alerts to update, delete and so on.</span></span>

 <span data-ttu-id="0efed-150">您可以在報表上建立多個警示。</span><span class="sxs-lookup"><span data-stu-id="0efed-150">You can create multiple alerts on a report.</span></span> <span data-ttu-id="0efed-151">雖然您可以擁有多個相同名稱的警示定義，不過建議您使用唯一的警示名稱。</span><span class="sxs-lookup"><span data-stu-id="0efed-151">It is possible to have multiple alert definitions with the same name, but it is recommended that you make alert names unique.</span></span> <span data-ttu-id="0efed-152">這樣更方便您區分及管理警示定義。</span><span class="sxs-lookup"><span data-stu-id="0efed-152">It makes it easier to differentiate and manage alert definitions.</span></span> <span data-ttu-id="0efed-153">您可以在 [資料警示管理員] 中檢視您建立之所有警示的清單。</span><span class="sxs-lookup"><span data-stu-id="0efed-153">You can view a list of all the alerts you created in Data Alert Manager.</span></span> <span data-ttu-id="0efed-154">如需詳細資訊，請參閱 [警示系統管理員的資料警示管理員](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) 和 [在資料警示管理員中管理我的資料警示](manage-my-data-alerts-in-data-alert-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="0efed-154">For more information, see [Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) and [Manage My Data Alerts in Data Alert Manager](manage-my-data-alerts-in-data-alert-manager.md).</span></span>

### <a name="rules-and-clauses"></a><span data-ttu-id="0efed-155">規則和子句</span><span class="sxs-lookup"><span data-stu-id="0efed-155">Rules and Clauses</span></span>
 <span data-ttu-id="0efed-156">資料變更的範圍和警示規則會定義觸發警示的資料變更。</span><span class="sxs-lookup"><span data-stu-id="0efed-156">The scope of data changes and the in the alert rules define the data changes that trigger the alert.</span></span> <span data-ttu-id="0efed-157">資料變更的範圍如下：</span><span class="sxs-lookup"><span data-stu-id="0efed-157">The scope of the data changes are as follow:</span></span>

-   <span data-ttu-id="0efed-158">資料中至少**有**一個值符合條件所指定的規則。</span><span class="sxs-lookup"><span data-stu-id="0efed-158">**Any data has**-at least one value in the data satisfies the rules that the condition specifies.</span></span>

-   <span data-ttu-id="0efed-159">**沒有資料**-資料中沒有任何值符合條件所指定的規則。</span><span class="sxs-lookup"><span data-stu-id="0efed-159">**No data has**-no value in the data satisfied the rules that the condition specifies.</span></span>

 <span data-ttu-id="0efed-160">規則可包含零個、一個或多個子句。</span><span class="sxs-lookup"><span data-stu-id="0efed-160">A rule contains zero, one, or many clauses.</span></span> <span data-ttu-id="0efed-161">多項規則會藉由 AND 邏輯運算子結合。</span><span class="sxs-lookup"><span data-stu-id="0efed-161">Multiple rules are combined by the AND logical operator.</span></span> <span data-ttu-id="0efed-162">如果資料行為字串資料類型，則規則可以包含藉由 OR 運算子組合的多個子句。</span><span class="sxs-lookup"><span data-stu-id="0efed-162">A rule can include multiple clause combined by the OR operator if the column has the string data type.</span></span> <span data-ttu-id="0efed-163">以下說明僅使用一個子句的基本規則，使用 AND 運算子組合的多項規則，以及擁有一個或多個 OR 子句的多項規則。</span><span class="sxs-lookup"><span data-stu-id="0efed-163">The following shows basic rules that use only one clause, multiple rules combined by using the AND operator, multiple rules that with one or more OR clauses.</span></span>

 <span data-ttu-id="0efed-164">**簡單的規則**</span><span class="sxs-lookup"><span data-stu-id="0efed-164">**Simple rules**</span></span>

-   <span data-ttu-id="0efed-165">Net sales **大於** 100000</span><span class="sxs-lookup"><span data-stu-id="0efed-165">Net sales **is greater than** 100000</span></span>

-   <span data-ttu-id="0efed-166">Sales date **晚於** 6/1/2010</span><span class="sxs-lookup"><span data-stu-id="0efed-166">Sales date **is after** 6/1/2010</span></span>

-   <span data-ttu-id="0efed-167">Company Name **不是** Contoso</span><span class="sxs-lookup"><span data-stu-id="0efed-167">Company Name **is not** Contoso</span></span>

 <span data-ttu-id="0efed-168">**藉由 AND 運算子組合的規則**</span><span class="sxs-lookup"><span data-stu-id="0efed-168">**Rules combined by AND operator**</span></span>

-   <span data-ttu-id="0efed-169">Sales **大於** 1500.00</span><span class="sxs-lookup"><span data-stu-id="0efed-169">Sales **is greater than** 1500.00</span></span>

     <span data-ttu-id="0efed-170">**且** Units Sold **小於** 500</span><span class="sxs-lookup"><span data-stu-id="0efed-170">**and** Units Sold **is less than** 500</span></span>

     <span data-ttu-id="0efed-171">Return date **早於** 1/1/2010</span><span class="sxs-lookup"><span data-stu-id="0efed-171">Return date **is before** 1/1/2010</span></span>

-   <span data-ttu-id="0efed-172">Sales **大於或等於** 1500.00</span><span class="sxs-lookup"><span data-stu-id="0efed-172">Sales **is greater than or equal to** 1500.00</span></span>

     <span data-ttu-id="0efed-173">**且** Return date **晚於** 1/1/2010</span><span class="sxs-lookup"><span data-stu-id="0efed-173">**and** Return date **is after** 1/1/2010</span></span>

     <span data-ttu-id="0efed-174">**且** Units Sold **大於** 500</span><span class="sxs-lookup"><span data-stu-id="0efed-174">**and** Units Sold **is greater than** 500</span></span>

-   <span data-ttu-id="0efed-175">Promotion name **包含** Spring</span><span class="sxs-lookup"><span data-stu-id="0efed-175">Promotion name **contains** Spring</span></span>

     <span data-ttu-id="0efed-176">**且** Units Sold **大於** 500</span><span class="sxs-lookup"><span data-stu-id="0efed-176">**and** Units Sold **is greater than** 500</span></span>

     <span data-ttu-id="0efed-177">**且** Returns **是**  0</span><span class="sxs-lookup"><span data-stu-id="0efed-177">**and** Returns **is**  0</span></span>

 <span data-ttu-id="0efed-178">**使用 OR 子句的規則**</span><span class="sxs-lookup"><span data-stu-id="0efed-178">**Rules with OR clauses**</span></span>

-   <span data-ttu-id="0efed-179">Last Name **是** Blythe</span><span class="sxs-lookup"><span data-stu-id="0efed-179">Last Name **is** Blythe</span></span>

     <span data-ttu-id="0efed-180">**或**  Petulescu</span><span class="sxs-lookup"><span data-stu-id="0efed-180">**Or**  Petulescu</span></span>

     <span data-ttu-id="0efed-181">**或**  Martin</span><span class="sxs-lookup"><span data-stu-id="0efed-181">**Or**  Martin</span></span>

-   <span data-ttu-id="0efed-182">Return date **晚於** 1/1/2010</span><span class="sxs-lookup"><span data-stu-id="0efed-182">Return date **is after** 1/1/2010</span></span>

     <span data-ttu-id="0efed-183">**且** Sales Territory **是**  Central</span><span class="sxs-lookup"><span data-stu-id="0efed-183">**and** Sales Territory **is**  Central</span></span>

     <span data-ttu-id="0efed-184">**或**  South</span><span class="sxs-lookup"><span data-stu-id="0efed-184">**Or**  South</span></span>

     <span data-ttu-id="0efed-185">**或**  North</span><span class="sxs-lookup"><span data-stu-id="0efed-185">**Or**  North</span></span>

 <span data-ttu-id="0efed-186">根據欄位的資料類型而定，[資料警示設計工具] 會提供不同的比較。</span><span class="sxs-lookup"><span data-stu-id="0efed-186">Depending on the data type of the field, Data Alert Designer provides different comparisons.</span></span> <span data-ttu-id="0efed-187">[資料警示設計工具] 會為要比較其值之欄位的資料類型提供專屬的比較。</span><span class="sxs-lookup"><span data-stu-id="0efed-187">Data Alert Designer provides comparisons that are tailored to the data type of the field to which values are compared.</span></span> <span data-ttu-id="0efed-188">以下列出不同的資料類型可使用的比較。</span><span class="sxs-lookup"><span data-stu-id="0efed-188">The following lists comparisons available for different data types.</span></span> <span data-ttu-id="0efed-189">規則中不支援 `Boolean` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="0efed-189">The `Boolean` data type is not supported in rules.</span></span>

-   <span data-ttu-id="0efed-190">日期時間資料類型比較包括： **是**、 **不是**、 **早於**和 **晚於**</span><span class="sxs-lookup"><span data-stu-id="0efed-190">Date time data type comparisons are: **is**, **is not**, **is before**, and **is after**</span></span>

-   <span data-ttu-id="0efed-191">數值資料類型的比較包括： **是**、 **不是**、 **小於**、 **小於或等於**、 **大於**以及 **大於或等於**</span><span class="sxs-lookup"><span data-stu-id="0efed-191">Numeric data type comparisons are: **is**, **is not**, **is less than**, **is less than or equal to**, and **is greater than**, and **is greater than or equal to**</span></span>

-   <span data-ttu-id="0efed-192">字串資料類型的比較包括： **是**、 **不是**及 **包含**</span><span class="sxs-lookup"><span data-stu-id="0efed-192">String data type comparisons are: **is**, **is not**, and **contains**</span></span>

 <span data-ttu-id="0efed-193">在建立規則時，您會透過選擇 [值輸入模式]\*\*\*\* 或 [欄位選取模式]\*\*\*\* 的方式指定要在比較中使用值或欄位。</span><span class="sxs-lookup"><span data-stu-id="0efed-193">When you create a rule, you specify whether to use to use a value or field in the comparison by choosing **Value Entry Mode** or **Field Selection Mode**.</span></span> <span data-ttu-id="0efed-194">如果您選擇 [值輸入模式]\*\*\*\*，則提供要比較的值清單。</span><span class="sxs-lookup"><span data-stu-id="0efed-194">If you choose **Value Entry Mode**, you provide a list of values to compare to.</span></span> <span data-ttu-id="0efed-195">包含多個 OR 子句的比較與 [!INCLUDE[tsql](../includes/tsql-md.md)]中的 IN 邏輯比較十分相似，後者是用來測試是否有相符項目的值清單。</span><span class="sxs-lookup"><span data-stu-id="0efed-195">A comparison that includes multiple OR clauses is very similar to the IN logical comparison in [!INCLUDE[tsql](../includes/tsql-md.md)], which is a list of values to test for a match.</span></span> <span data-ttu-id="0efed-196">如需詳細資訊，請參閱 [IN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/in-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0efed-196">For more information, see [IN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/in-transact-sql).</span></span>

 <span data-ttu-id="0efed-197">如果您選擇 [欄位選取模式]\*\*\*\*，則會在兩個欄位之間逐一比較資料列。</span><span class="sxs-lookup"><span data-stu-id="0efed-197">If you choose **Field Selection Mode**, the comparison is between two fields, row by row.</span></span> <span data-ttu-id="0efed-198">這兩個欄位必須擁有相容的資料類型 (例如，兩個數值欄位)，否則比較無效。</span><span class="sxs-lookup"><span data-stu-id="0efed-198">The two fields must have compatible data types (for example, two numeric fields) or the comparison is not valid.</span></span> <span data-ttu-id="0efed-199">當您選擇 [欄位選取模式]\*\*\*\* 時，欄位清單會自動顯示。</span><span class="sxs-lookup"><span data-stu-id="0efed-199">A list of fields displays automatically when you choose **Field Selection Mode**.</span></span>

 <span data-ttu-id="0efed-200">沒有規則的資料警示也是有效的。</span><span class="sxs-lookup"><span data-stu-id="0efed-200">Data alerts without rules are also valid.</span></span> <span data-ttu-id="0efed-201">這類警示可能很實用。</span><span class="sxs-lookup"><span data-stu-id="0efed-201">This type of alert can be very useful.</span></span> <span data-ttu-id="0efed-202">假設您只想要在報表資料摘要中有資料時收到通知。</span><span class="sxs-lookup"><span data-stu-id="0efed-202">Imagine a scenario in which you want only to be notified when the report data feed has data.</span></span> <span data-ttu-id="0efed-203">資料摘要包含出席者資訊，且摘要是空的，直到出席者取消為止。</span><span class="sxs-lookup"><span data-stu-id="0efed-203">The data feed contains attendee information and the feed is empty until an attendee cancels.</span></span> <span data-ttu-id="0efed-204">在此案例中，您會從出現第一個取消開始收到警示。</span><span class="sxs-lookup"><span data-stu-id="0efed-204">In this scenario, you would receive an alert, starting with the first cancellation.</span></span>

 <span data-ttu-id="0efed-205">您可以刪除個別規則和子句。</span><span class="sxs-lookup"><span data-stu-id="0efed-205">You can delete individual rules and clauses.</span></span>

 <span data-ttu-id="0efed-206">規則和子句包含在資料警示訊息中。</span><span class="sxs-lookup"><span data-stu-id="0efed-206">Rules and clauses are included in the data alert message.</span></span>

### <a name="schedule-settings"></a><span data-ttu-id="0efed-207">排程設定</span><span class="sxs-lookup"><span data-stu-id="0efed-207">Schedule Settings</span></span>
 <span data-ttu-id="0efed-208">您為資料警示定義的排程會定義傳送資料警示訊息的循環模式，以及何時開始和停止傳送警示訊息。</span><span class="sxs-lookup"><span data-stu-id="0efed-208">The schedule that you define for the data alert defines the recurrence pattern for sending the data alert message and when to start and stop sending the alert messages.</span></span> <span data-ttu-id="0efed-209">模式包括：一次、分鐘、每天和每週。</span><span class="sxs-lookup"><span data-stu-id="0efed-209">The patterns are: once, minute, daily, and weekly.</span></span> <span data-ttu-id="0efed-210">雖然警示只有一項排程，但是您可以使用這些間隔建立符合大部分商務需要的複雜循環模式。</span><span class="sxs-lookup"><span data-stu-id="0efed-210">Although an alert has only one schedule you can create complex recurrence patterns that meet most business needs by using these intervals.</span></span> <span data-ttu-id="0efed-211">以下範例為排程中常用的循環模式：</span><span class="sxs-lookup"><span data-stu-id="0efed-211">The following are examples of common recurrence patterns to use in schedules:</span></span>

-   <span data-ttu-id="0efed-212">每\*\*隔10天 (s) \*\* -每隔10天傳送警示一次。</span><span class="sxs-lookup"><span data-stu-id="0efed-212">**Daily every 10 day(s)** - sends alerts once a day, every 10 days.</span></span>

-   <span data-ttu-id="0efed-213">每**周每2周 (s) 星期一**-只在每隔兩周的星期一傳送警示。</span><span class="sxs-lookup"><span data-stu-id="0efed-213">**Weekly every 2 week(s) on Monday** - sends alerts every two weeks on Mondays only.</span></span>

-   <span data-ttu-id="0efed-214">\*\*每小時每12小時 (s) \*\* -每12小時傳送警示一次。</span><span class="sxs-lookup"><span data-stu-id="0efed-214">**Hourly every 12 hour(s)** - sends alerts every 12 hours.</span></span>

-   <span data-ttu-id="0efed-215">\*\*每隔30分鐘 (s) \*\* -每隔30分鐘傳送警示一次。</span><span class="sxs-lookup"><span data-stu-id="0efed-215">**Minute every 30 minute(s)** - sends alerts every 30 minutes.</span></span>

 <span data-ttu-id="0efed-216">循環模式會指定警示傳送的時間。</span><span class="sxs-lookup"><span data-stu-id="0efed-216">The recurrence pattern specifies when the alert is sent.</span></span> <span data-ttu-id="0efed-217">如果在模式指定的間隔期間符合規則，警示在間隔結束之前並不會傳送。</span><span class="sxs-lookup"><span data-stu-id="0efed-217">If the rules are met during the interval that the pattern specifies, the alert is not sent until the end of the interval.</span></span>

 <span data-ttu-id="0efed-218">如果您要在報表資料符合指定的規則時，盡快收到資料警示訊息，可以排程讓警示經常執行。</span><span class="sxs-lookup"><span data-stu-id="0efed-218">If you want to receive a data alert message as soon as possible when report data follow the specified rules, you can schedule the alert to run often.</span></span> <span data-ttu-id="0efed-219">如果報表資料並未變更，您和其他收件者可能收到許多重複的訊息。</span><span class="sxs-lookup"><span data-stu-id="0efed-219">When the report data does not change, you and other recipients might receive many redundant messages.</span></span> <span data-ttu-id="0efed-220">如果您只想要在套用規則後的結果變更時收到訊息，請選取 [只在結果變更時傳送訊息]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="0efed-220">If you want to receive messages only, when the results from applying the rules change, select the **Send message only if results change** option.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="0efed-221">除非業務上有重要的理由，否則建議您不要使用頻率高於每天一次的循環模式。</span><span class="sxs-lookup"><span data-stu-id="0efed-221">It is recommended that you do not use a recurrence pattern that is more frequent than daily unless you have an important business reason to do so.</span></span> <span data-ttu-id="0efed-222">不支援即時處理資料警示定義。</span><span class="sxs-lookup"><span data-stu-id="0efed-222">Processing data alert definition in real time is not a supported scenario.</span></span> <span data-ttu-id="0efed-223">處理資料警示定義的頻率過高，會影響報表伺服器和整體 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 部署的效能。</span><span class="sxs-lookup"><span data-stu-id="0efed-223">Processing data alert definitions too frequently impacts the performance of the report server and the overall [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] deployment.</span></span>

### <a name="email-settings"></a><span data-ttu-id="0efed-224">電子郵件設定</span><span class="sxs-lookup"><span data-stu-id="0efed-224">Email Settings</span></span>
 <span data-ttu-id="0efed-225">您可在 [收件者]\*\*\*\* 選項中指定要接收資料警示訊息電子郵件之收件者的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="0efed-225">You specify the email addresses of recipients to receive data alert messages by email in the **Recipient(s)** option.</span></span> <span data-ttu-id="0efed-226">多個電子郵件是以分號分隔，與 Microsoft Office Outlook 電子郵件中的方式相同。</span><span class="sxs-lookup"><span data-stu-id="0efed-226">Multiple email addresses are separated by semicolons, the same way that you do in Microsoft Office Outlook email messages.</span></span> <span data-ttu-id="0efed-227">您也可以指定通訊群組做為收件者，如此可讓管理收件者清單的工作更容易且更有效率。</span><span class="sxs-lookup"><span data-stu-id="0efed-227">You can also specify distribution groups as recipients, which makes it easier and more efficient to manage the recipient list.</span></span> <span data-ttu-id="0efed-228">如果建立警示定義時，SharePoint 可以判斷您的電子郵件地址，則您的電子郵件地址會自動加入收件者清單，否則您就必須明確將自己加入為收件者。</span><span class="sxs-lookup"><span data-stu-id="0efed-228">If SharePoint can determine your email address when you are creating an alert definition, your email address is automatically added to the recipients list; otherwise, you need to explicitly add yourself as a recipient.</span></span>

 <span data-ttu-id="0efed-229">電子郵件的預設主旨是\*\* \<alert name> 的資料警示\*\*。</span><span class="sxs-lookup"><span data-stu-id="0efed-229">The default subject of the email is **Data alert for \<alert name>**.</span></span> <span data-ttu-id="0efed-230">您可以依需要變更主旨。</span><span class="sxs-lookup"><span data-stu-id="0efed-230">You can change the subject to fit your needs.</span></span>

 <span data-ttu-id="0efed-231">您也可以在 [描述]\*\*\*\* 選項中提供要包含在資料警示訊息中的描述。</span><span class="sxs-lookup"><span data-stu-id="0efed-231">You can also provide a description to include in the data alert message in the **Description** option.</span></span> <span data-ttu-id="0efed-232">包含描述 (尤其是擁有類似的資料警示時) 有助於迅速區分和了解警示訊息。</span><span class="sxs-lookup"><span data-stu-id="0efed-232">Including a description, especially if you have data alerts that are similar, will help you quickly differentiate and understand your alert messages.</span></span> <span data-ttu-id="0efed-233">除了在報表資料滿足指定的規則時傳送的警示訊息之外，警示訊息還會在發生錯誤時傳送至所有收件者。</span><span class="sxs-lookup"><span data-stu-id="0efed-233">In addition to the alert message that is sent when report data satisfied the specified rules, an alert message is sent to all recipients when an error occurs.</span></span> <span data-ttu-id="0efed-234">如需相關資訊，請參閱 [Data Alert Messages](../../2014/reporting-services/data-alert-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="0efed-234">For more information, see [Data Alert Messages](../../2014/reporting-services/data-alert-messages.md).</span></span>

 <span data-ttu-id="0efed-235">如需如何產生電子郵件的詳細資訊，請參閱 [Reporting Services 資料警示](../ssms/agent/alerts.md)。</span><span class="sxs-lookup"><span data-stu-id="0efed-235">For more information about how the email is generated, see [Reporting Services Data Alerts](../ssms/agent/alerts.md).</span></span>

##  <a name="create-a-data-alert-definition"></a><a name="CreateAlert"></a> <span data-ttu-id="0efed-236">建立資料警示定義</span><span class="sxs-lookup"><span data-stu-id="0efed-236">Create a Data Alert Definition</span></span>
 <span data-ttu-id="0efed-237">如果您擁有「SharePoint 檢視項目」和「建立提醒」權限，只要報表使用預存認證或不使用認證，您就可以為任何可以檢視的報表建立資料警示定義。</span><span class="sxs-lookup"><span data-stu-id="0efed-237">If you are granted the SharePoint View Items and Create Alerts permissions you can create a data alert definition for any report that you have permission to view as long as the report uses stored credentials or no credentials.</span></span> <span data-ttu-id="0efed-238">您會從 SharePoint 文件庫執行報表。</span><span class="sxs-lookup"><span data-stu-id="0efed-238">You run the report from a SharePoint library.</span></span> <span data-ttu-id="0efed-239">您可在 [資料警示設計工具] 中使用的資料是來自該報表。</span><span class="sxs-lookup"><span data-stu-id="0efed-239">The data that is available for you to use in Data Alert Designer comes from the report.</span></span> <span data-ttu-id="0efed-240">如果報表已參數化，您可能需要使用不同的參數值來執行報表，以確保您想要的資料會出現在報表中。</span><span class="sxs-lookup"><span data-stu-id="0efed-240">If the report is parameterized, you might need to run the report using different parameter values to ensure the data that you are interested in appears in the report.</span></span> <span data-ttu-id="0efed-241">報表開啟之後，在報表工具列上按一下 [動作]\*\*\*\* 功能表上的 [新資料警示]\*\*\*\* 選項，開啟 [資料警示設計工具]。</span><span class="sxs-lookup"><span data-stu-id="0efed-241">After the report is open, you click the **New Data Alert** option on the **Actions** menu on the report toolbar to open Data Alert Designer.</span></span> <span data-ttu-id="0efed-242">下圖說明如何開啟 [資料警示設計工具]。</span><span class="sxs-lookup"><span data-stu-id="0efed-242">The following picture shows you how to open Data Alert Designer.</span></span>

 <span data-ttu-id="0efed-243">![從 SharePoint 文件庫開啟警示設計工具](media/rs-openalertdesigneriw.gif "從 SharePoint 文件庫開啟警示設計工具")</span><span class="sxs-lookup"><span data-stu-id="0efed-243">![Open Alert Designer from SharePoint library](media/rs-openalertdesigneriw.gif "Open Alert Designer from SharePoint library")</span></span>

 <span data-ttu-id="0efed-244">如需詳細資訊，請參閱 [在資料警示設計工具中建立資料警示](create-a-data-alert-in-data-alert-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="0efed-244">For more information, see [Create a Data Alert in Data Alert Designer](create-a-data-alert-in-data-alert-designer.md).</span></span>


##  <a name="save-a-data-alert-definition"></a><a name="SaveAlert"></a> <span data-ttu-id="0efed-245">儲存資料警示定義</span><span class="sxs-lookup"><span data-stu-id="0efed-245">Save a Data Alert Definition</span></span>
 <span data-ttu-id="0efed-246">[資料警示設計工具] 會顯示將儲存資料警示定義的目標網站 URL。</span><span class="sxs-lookup"><span data-stu-id="0efed-246">Data Alert Designer displays the URL of the site where the data alert definition will be saved.</span></span> <span data-ttu-id="0efed-247">資料警示定義會固定儲存到報表所在的網站。</span><span class="sxs-lookup"><span data-stu-id="0efed-247">Data alert definitions are always saved to the same site as the reports.</span></span>

> [!NOTE]
>  <span data-ttu-id="0efed-248">您選擇執行報表的參數值會儲存在警示定義中，並且在處理警示定義的過程中重新執行報表時使用。</span><span class="sxs-lookup"><span data-stu-id="0efed-248">The parameter values you chose to run the report are saved in the alert definition and will be used when report is rerun as a step in processing the alert definition.</span></span> <span data-ttu-id="0efed-249">若要使用不同的參數值，您必須建立新的警示定義。</span><span class="sxs-lookup"><span data-stu-id="0efed-249">To use different parameter values, you must create a new alert definition.</span></span>

 <span data-ttu-id="0efed-250">警示定義儲存之前，會先進行驗證。</span><span class="sxs-lookup"><span data-stu-id="0efed-250">Before the alert definition is saved, it is validated.</span></span> <span data-ttu-id="0efed-251">您必須先更正所有錯誤，才能成功儲存警示定義。</span><span class="sxs-lookup"><span data-stu-id="0efed-251">You must correct any errors before the alert definition can be saved successfully.</span></span> <span data-ttu-id="0efed-252">如需詳細資訊，請參閱 [在資料警示設計工具中建立資料警示](create-a-data-alert-in-data-alert-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="0efed-252">For more information, see [Create a Data Alert in Data Alert Designer](create-a-data-alert-in-data-alert-designer.md).</span></span>


##  <a name="edit-a-data-alert-definition"></a><a name="EditAlert"></a> <span data-ttu-id="0efed-253">編輯資料警示定義</span><span class="sxs-lookup"><span data-stu-id="0efed-253">Edit a Data Alert Definition</span></span>
 <span data-ttu-id="0efed-254">儲存資料警示定義之後，您就可以在 [資料警示設計工具] 中再次開啟該警示定義並進行編輯。</span><span class="sxs-lookup"><span data-stu-id="0efed-254">After you save your data alert definition, you can reopen and then edit it in Data Alert Designer.</span></span> <span data-ttu-id="0efed-255">您可以加入、變更或刪除規則和子句，以及變更排程和電子郵件設定。</span><span class="sxs-lookup"><span data-stu-id="0efed-255">You can add, change, or delete rules and clauses and change the schedule and email settings.</span></span> <span data-ttu-id="0efed-256">如果警示使用的報表資料摘要已變更，而且不再提供警示規則參考的欄位，或是欄位的資料類型或其他中繼資料已變更，則警示定義就不再有效，您必須修正它，才能再次儲存。</span><span class="sxs-lookup"><span data-stu-id="0efed-256">If the report data feed that the alert uses has changed and no longer provides the fields that the alert rules reference or the data types or other metadata of the fields have changed, the alert definition is no longer valid, and you must correct it before you can resave it.</span></span> <span data-ttu-id="0efed-257">如果您想要使用不同的資料摘要，則必須建立新的警示定義。</span><span class="sxs-lookup"><span data-stu-id="0efed-257">If you want to use a different data feed, you must create a new alert definition.</span></span>

 <span data-ttu-id="0efed-258">若要編輯資料警示定義，請在 [資料警示管理員] 中以滑鼠右鍵按一下該資料警示定義，然後按一下 [編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0efed-258">To edit a data alert definition, you right click it in Data Alert Manager and click **Edit**.</span></span> <span data-ttu-id="0efed-259">下圖說明 [資料警示管理員] 中資料警示的內容功能表。</span><span class="sxs-lookup"><span data-stu-id="0efed-259">The following picture shows you the context menu on a data alert in Data Alert Manager.</span></span>

 <span data-ttu-id="0efed-260">![按一下 [編輯] 來開啟資料警示設計工具](media/rs-alertmanageriwopendesigner.gif "按一下 [編輯] 來開啟資料警示設計工具")</span><span class="sxs-lookup"><span data-stu-id="0efed-260">![Open Data Alert Designer by clicking Edit](media/rs-alertmanageriwopendesigner.gif "Open Data Alert Designer by clicking Edit")</span></span>

 <span data-ttu-id="0efed-261">如需詳細資訊，請參閱 [在警示設計工具中編輯資料警示](edit-a-data-alert-in-alert-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="0efed-261">For more information, see [Edit a Data Alert in Alert Designer](edit-a-data-alert-in-alert-designer.md).</span></span>


##  <a name="related-tasks"></a><a name="HowTo"></a> <span data-ttu-id="0efed-262">相關工作</span><span class="sxs-lookup"><span data-stu-id="0efed-262">Related Tasks</span></span>
 <span data-ttu-id="0efed-263">本節列出如何建立和編輯警示的程序。</span><span class="sxs-lookup"><span data-stu-id="0efed-263">This section lists procedures that show you how to create and edit alerts.</span></span>

-   [<span data-ttu-id="0efed-264">在警示設計工具中編輯資料警示</span><span class="sxs-lookup"><span data-stu-id="0efed-264">Edit a Data Alert in Alert Designer</span></span>](edit-a-data-alert-in-alert-designer.md)

-   [<span data-ttu-id="0efed-265">在資料警示設計工具中建立資料警示</span><span class="sxs-lookup"><span data-stu-id="0efed-265">Create a Data Alert in Data Alert Designer</span></span>](create-a-data-alert-in-data-alert-designer.md)


## <a name="see-also"></a><span data-ttu-id="0efed-266">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0efed-266">See Also</span></span>
 <span data-ttu-id="0efed-267">警示系統管理員的[Reporting Services 資料警示](../ssms/agent/alerts.md)[資料警示管理員](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md)</span><span class="sxs-lookup"><span data-stu-id="0efed-267">[Reporting Services Data Alerts](../ssms/agent/alerts.md) [Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md)</span></span>


