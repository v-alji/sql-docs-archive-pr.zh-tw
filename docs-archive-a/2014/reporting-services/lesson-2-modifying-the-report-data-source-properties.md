---
title: 第 2 課：修改報表資料來源屬性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c962b0ff-ce8a-4742-8262-dc730901afcf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05e56a58ce28ee1e1e450d3af012cbd1ffe668ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592527"
---
# <a name="lesson-2-modifying-the-report-data-source-properties"></a><span data-ttu-id="04435-102">Lesson 2: Modifying the Report Data Source Properties</span><span class="sxs-lookup"><span data-stu-id="04435-102">Lesson 2: Modifying the Report Data Source Properties</span></span>
  <span data-ttu-id="04435-103">在這一課，您將使用報表管理員來選取傳遞給收件者的報表。</span><span class="sxs-lookup"><span data-stu-id="04435-103">In this lesson, you will use Report Manager to select a report that will be delivered to recipients.</span></span> <span data-ttu-id="04435-104">您將定義的資料驅動訂閱將散發 **建立基本資料表報表 &amp;#40;SSRS 教學課程&amp;#41;** 教學課程中建立的 [建立基本資料表報表 &#40;SSRS 教學課程&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)報表。</span><span class="sxs-lookup"><span data-stu-id="04435-104">The data-driven subscription that you will define will distribute the **Sales Order** report created in the tutorial [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md).</span></span> <span data-ttu-id="04435-105">在下面的步驟中，您將修改報表用來取得資料的資料來源連接資訊。</span><span class="sxs-lookup"><span data-stu-id="04435-105">In the steps that follow, you will modify the data source connection information used by the report to get data.</span></span> <span data-ttu-id="04435-106">只有使用 **預存認證** 來存取報表資料來源的報表可以透過資料驅動訂閱散發。</span><span class="sxs-lookup"><span data-stu-id="04435-106">Only reports that use **stored credentials** to access a report data source can be distributed through a data-driven subscription.</span></span> <span data-ttu-id="04435-107">自動報表處理需要預存認證。</span><span class="sxs-lookup"><span data-stu-id="04435-107">Stored credentials are necessary for unattended report processing.</span></span>

 <span data-ttu-id="04435-108">您也會將資料集和報表修改成使用參數來依據 `[Order]` 篩選報表，讓訂閱能夠針對特定訂單和轉譯格式輸出不同的報表執行個體。</span><span class="sxs-lookup"><span data-stu-id="04435-108">You will also modify the dataset and report to use a parameter to filter the report on the `[Order]` so the subscription can output different instances of the report for specific orders and rendering formats.</span></span>

 <span data-ttu-id="04435-109">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="04435-109">**In this topic:**</span></span>

-   [<span data-ttu-id="04435-110">若要修改資料來源屬性</span><span class="sxs-lookup"><span data-stu-id="04435-110">To Modify the Data Source Properties</span></span>](#bkmk_modify_datasource)

-   [<span data-ttu-id="04435-111">若要修改 AdventureWorksDataset</span><span class="sxs-lookup"><span data-stu-id="04435-111">To Modify the AdventureWorksDataset</span></span>](#bkmk_modify_dataset)

-   [<span data-ttu-id="04435-112">若要加入報表參數並重新發行報表</span><span class="sxs-lookup"><span data-stu-id="04435-112">To Add a Report Parameter and Republish the Report</span></span>](#bkmk_add_reportparameter)

-   [<span data-ttu-id="04435-113">若要重新部署報表</span><span class="sxs-lookup"><span data-stu-id="04435-113">To Re-deploy the Report</span></span>](#bkmk_redeploy)

##  <a name="to-modify-the-data-source-properties"></a><a name="bkmk_modify_datasource"></a><span data-ttu-id="04435-114">若要修改資料來源屬性</span><span class="sxs-lookup"><span data-stu-id="04435-114">To Modify the Data Source Properties</span></span>

1.  <span data-ttu-id="04435-115">以系統管理員許可權啟動[報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) ，例如，以滑鼠右鍵按一下 Internet Explorer 的圖示，然後按一下 [以**系統管理員身分執行**]。</span><span class="sxs-lookup"><span data-stu-id="04435-115">Start [Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) with administrator privileges, for example, right-click the icon for Internet Explorer and click **Run as administrator**.</span></span>

2.  <span data-ttu-id="04435-116">瀏覽到包含 **Sales Orders** 報表的資料夾，然後在報表的內容功能表中，按一下 **[管理]**。</span><span class="sxs-lookup"><span data-stu-id="04435-116">Browse to the folder containing the **Sales Orders** report and in the context menu of the report, click **Manage**.</span></span>

     <span data-ttu-id="04435-117">![開啟報表內容功能表並選取管理](../../2014/tutorials/media/ssrs-tutorial-datadriven-manage-report.gif "開啟報表內容功能表並選取管理")</span><span class="sxs-lookup"><span data-stu-id="04435-117">![Open the report context menu and select manage](../../2014/tutorials/media/ssrs-tutorial-datadriven-manage-report.gif "Open the report context menu and select manage")</span></span>

3.  <span data-ttu-id="04435-118">按一下 [資料來源]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="04435-118">Click the **Data Sources** tab.</span></span>

4.  <span data-ttu-id="04435-119">針對 **[連接類型]**，選取 **[Microsoft SQL Server]**。</span><span class="sxs-lookup"><span data-stu-id="04435-119">For **Connection Type**, select **Microsoft SQL Server**.</span></span>

5.  <span data-ttu-id="04435-120">自訂資料來源連接字串將如下所示，而且它會假設範例資料庫位於本機資料庫伺服器上：</span><span class="sxs-lookup"><span data-stu-id="04435-120">The custom data source connection string will be the following and it assumes that the sample database is on a local database server:</span></span>

    ```
    Data source=localhost; initial catalog=AdventureWorks2012
    ```

6.  <span data-ttu-id="04435-121">按一下 **[安全地儲存在報表伺服器中的認證]**。</span><span class="sxs-lookup"><span data-stu-id="04435-121">Click **Credentials stored securely in the report server**.</span></span>

7.  <span data-ttu-id="04435-122">輸入您的使用者名稱 (使用 *domain\user*格式) 和密碼。</span><span class="sxs-lookup"><span data-stu-id="04435-122">Type your user name (use the format *domain\user*) and password.</span></span> <span data-ttu-id="04435-123">如果您沒有存取 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫的權限，請指定有這項權限的登入。</span><span class="sxs-lookup"><span data-stu-id="04435-123">If you do not have permission to access the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database, specify a login that does.</span></span>

8.  <span data-ttu-id="04435-124">按一下 **[連接到資料來源時做為 windows 認證**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="04435-124">Click **Use as windows credentials when connecting to the data source**, and then click **OK**.</span></span> <span data-ttu-id="04435-125">如果您並未使用網域帳戶 (例如，您是使用[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]登入)，請勿點選這個核取方塊。</span><span class="sxs-lookup"><span data-stu-id="04435-125">If you are not using a domain account (for example, if you are using a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login), do not click this checkbox.</span></span>

9. <span data-ttu-id="04435-126">按一下 [測試連接]\*\*\*\*，確認您能夠連線到資料來源。</span><span class="sxs-lookup"><span data-stu-id="04435-126">Click **Test Connection** to verify you can connect to the data source.</span></span>

10. <span data-ttu-id="04435-127">按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="04435-127">Click **Apply**.</span></span>

11. <span data-ttu-id="04435-128">檢視報表以確認報表是以您指定的認證來執行。</span><span class="sxs-lookup"><span data-stu-id="04435-128">View the report to verify that the report runs with the credentials you specified.</span></span> <span data-ttu-id="04435-129">若要查看報表，請按一下 [**視圖**] 索引標籤。請注意，一旦報表開啟之後，您必須選取員工名稱，然後按一下 [**查看報表**] 按鈕來查看報表。</span><span class="sxs-lookup"><span data-stu-id="04435-129">To view the report, click the **View** tab. Note that once the report is open, you must select an Employee name and then click the **View Report** button to view the report.</span></span>

##  <a name="to-modify-the-adventureworksdataset"></a><a name="bkmk_modify_dataset"></a><span data-ttu-id="04435-130">修改 AdventureWorksDataset</span><span class="sxs-lookup"><span data-stu-id="04435-130">To Modify the AdventureWorksDataset</span></span>

1.  <span data-ttu-id="04435-131">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中開啟 Sales Orders 報表。</span><span class="sxs-lookup"><span data-stu-id="04435-131">Open the Sales Orders report in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]</span></span>

2.  <span data-ttu-id="04435-132">以滑鼠右鍵按一下 `AdventureWorksDataset` 資料集，然後按一下 [資料集屬性]  。</span><span class="sxs-lookup"><span data-stu-id="04435-132">Right-click the dataset `AdventureWorksDataset` and click **Dataset Properties**.</span></span>

3.  <span data-ttu-id="04435-133">在 `WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)` 陳述式前面加入 `Group By` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="04435-133">Add the statement `WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)` before the `Group By` statement.</span></span> <span data-ttu-id="04435-134">完整的查詢語法如下：</span><span class="sxs-lookup"><span data-stu-id="04435-134">The full query syntax is the following:</span></span>

    ```
    SELECT soh.OrderDate AS Date, soh.SalesOrderNumber AS [Order], pps.Name AS Subcat, pp.Name AS Product, SUM(sd.OrderQty) AS Qty, SUM(sd.LineTotal)  AS LineTotal
    FROM Sales.SalesPerson AS sp INNER JOIN
      Sales.SalesOrderHeader AS soh ON sp.BusinessEntityID = soh.SalesPersonID INNER JOIN
       Sales.SalesOrderDetail AS sd ON sd.SalesOrderID = soh.SalesOrderID INNER JOIN
       Production.Product AS pp ON sd.ProductID = pp.ProductID
    INNER JOIN
       Production.ProductSubcategory AS pps ON pp.ProductSubcategoryID = pps.ProductSubcategoryID 
    INNER JOIN
        Production.ProductCategory AS ppc ON ppc.ProductCategoryID = pps.ProductCategoryID

    WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)

    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name, soh.SalesPersonID
    HAVING (ppc.Name = 'Clothing')
    ```

4.  <span data-ttu-id="04435-135">按一下 [檔案] &gt; [新增] &gt; [專案]</span><span class="sxs-lookup"><span data-stu-id="04435-135">Click **OK**</span></span>

##  <a name="to-add-a-report-parameter-and-republish-the-report"></a><a name="bkmk_add_reportparameter"></a><span data-ttu-id="04435-136">若要加入報表參數並重新發行報表</span><span class="sxs-lookup"><span data-stu-id="04435-136">To Add a Report Parameter and Republish the Report</span></span>

1.  <span data-ttu-id="04435-137">在 [**報表資料**] 窗格中，按一下 [**新增**]，然後按一下 [**參數 ...** ]</span><span class="sxs-lookup"><span data-stu-id="04435-137">In the **Report Data** pane click **New** and then click **Parameter...**</span></span>

2.  <span data-ttu-id="04435-138">在 **[名稱]** 中，輸入 `OrderNumber`。</span><span class="sxs-lookup"><span data-stu-id="04435-138">In **Name**, type `OrderNumber`.</span></span>

3.  <span data-ttu-id="04435-139">在 **[提示]** 中，輸入 `OrderNumber`。</span><span class="sxs-lookup"><span data-stu-id="04435-139">In **Prompt**, type `OrderNumber`.</span></span>

4.  <span data-ttu-id="04435-140">選取 [允許空白值 ("")]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="04435-140">Select **Allow blank value ("")**.</span></span>

5.  <span data-ttu-id="04435-141">選取 [允許 Null 值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="04435-141">Select **Allow null value**.</span></span>

6.  <span data-ttu-id="04435-142">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="04435-142">Click **OK**.</span></span> <span data-ttu-id="04435-143">參數將會加入至 [**報表資料] 窗格**，而且看起來會像下圖：</span><span class="sxs-lookup"><span data-stu-id="04435-143">The parameter will be added to the **Report Data pane** and it will look like the following image:</span></span>

     <span data-ttu-id="04435-144">![新的參數已加入至報表資料窗格](../../2014/tutorials/media/ssrs-tutorial-datadriven-parameter.gif "新的參數已加入至報表資料窗格")</span><span class="sxs-lookup"><span data-stu-id="04435-144">![The new parameter is added to the Report Data pane](../../2014/tutorials/media/ssrs-tutorial-datadriven-parameter.gif "The new parameter is added to the Report Data pane")</span></span>

7.  <span data-ttu-id="04435-145">按一下 [**預覽**] 索引標籤以執行報表。請注意位於報表頂端的參數輸入方塊。</span><span class="sxs-lookup"><span data-stu-id="04435-145">Click the **Preview** tab to run the report.Note the parameter input box at the top of the report.</span></span> <span data-ttu-id="04435-146">您可以：</span><span class="sxs-lookup"><span data-stu-id="04435-146">You can either:</span></span>

    -   <span data-ttu-id="04435-147">按一下 [檢視報表] 查看完整報表，而不使用參數。</span><span class="sxs-lookup"><span data-stu-id="04435-147">Click View Report to see the full report without using a parameter.</span></span>

    -   <span data-ttu-id="04435-148">取消選取 Null 選項並輸入訂單號碼 (例如 so71949)，即可單獨檢視報表中的單一訂單。</span><span class="sxs-lookup"><span data-stu-id="04435-148">Unselect the Null option and type an order number, for example so71949 to view only the one order in the report.</span></span>

         <span data-ttu-id="04435-149">![具有可見參數區域的報表檢視器](../../2014/tutorials/media/ssrs-tutorial-datadriven-reportviewer-parameter.gif "具有可見參數區域的報表檢視器")</span><span class="sxs-lookup"><span data-stu-id="04435-149">![Report viewer with parameter area visible](../../2014/tutorials/media/ssrs-tutorial-datadriven-reportviewer-parameter.gif "Report viewer with parameter area visible")</span></span>

8.  <span data-ttu-id="04435-150">請重新部署報表，讓下一課的訂閱組態能夠運用您在這一課所做的變更。</span><span class="sxs-lookup"><span data-stu-id="04435-150">Re-deploy the report so the subscription configuration in the next lesson can utilize the changes you made in this lesson.</span></span> <span data-ttu-id="04435-151">如需用於資料表教學課程的專案屬性詳細資訊，請參閱[第 6 課：新增群組和總計 &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md) 的＜將報表發行至報表伺服器 (選擇性)＞一節。</span><span class="sxs-lookup"><span data-stu-id="04435-151">For more information on the project properties used in the table tutorial, see section 'To Publish the Report to the Report Server (Optional)' of [Lesson 6: Adding Grouping and Totals &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).</span></span>

##  <a name="to-re-deploy-the-report"></a><a name="bkmk_redeploy"></a><span data-ttu-id="04435-152">重新部署報表</span><span class="sxs-lookup"><span data-stu-id="04435-152">To Re-deploy the Report</span></span>

1.  <span data-ttu-id="04435-153">請重新部署報表，讓下一課的訂閱組態能夠運用您在這一課所做的變更。</span><span class="sxs-lookup"><span data-stu-id="04435-153">Re-deploy the report so the subscription configuration in the next lesson can utilize the changes you made in this lesson.</span></span> <span data-ttu-id="04435-154">如需用於資料表教學課程的專案屬性詳細資訊，請參閱[第 6 課：新增群組和總計 &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md) 的＜將報表發行至報表伺服器 (選擇性)＞一節。</span><span class="sxs-lookup"><span data-stu-id="04435-154">For more information on the project properties used in the table tutorial, see section 'To Publish the Report to the Report Server (Optional)' of [Lesson 6: Adding Grouping and Totals &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).</span></span>

2.  <span data-ttu-id="04435-155">在工具列上，按一下 **[建置]** ，然後按一下 **[部署教學課程]**。</span><span class="sxs-lookup"><span data-stu-id="04435-155">On the toolbar click **Build** and then click **Deploy tutorial**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="04435-156">後續步驟</span><span class="sxs-lookup"><span data-stu-id="04435-156">Next Steps</span></span>
 <span data-ttu-id="04435-157">您已順利設定報表來利用預存認證取得資料。</span><span class="sxs-lookup"><span data-stu-id="04435-157">You successfully configured the report to get data using stored credentials.</span></span> <span data-ttu-id="04435-158">之後，您可以使用報表管理員中的 [資料驅動訂閱] 頁面來指定訂閱。</span><span class="sxs-lookup"><span data-stu-id="04435-158">Next, you specify the subscription using the Data-Driven Subscription pages in Report Manager.</span></span> <span data-ttu-id="04435-159">請參閱 [第 3 課：定義資料驅動訂閱](../reporting-services/lesson-3-defining-a-data-driven-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="04435-159">See [Lesson 3: Defining a Data-Driven Subscription](../reporting-services/lesson-3-defining-a-data-driven-subscription.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="04435-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04435-160">See Also</span></span>
 <span data-ttu-id="04435-161">[管理報表資料來源](report-data/manage-report-data-sources.md)[指定報表資料來源的認證和連接資訊](report-data/specify-credential-and-connection-information-for-report-data-sources.md)[建立資料驅動訂閱 &#40;Ssrs 教學課程&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md) [建立基本資料表報表 &#40;ssrs 教學課程&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)</span><span class="sxs-lookup"><span data-stu-id="04435-161">[Manage Report Data Sources](report-data/manage-report-data-sources.md) [Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md) [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md) [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)</span></span>


