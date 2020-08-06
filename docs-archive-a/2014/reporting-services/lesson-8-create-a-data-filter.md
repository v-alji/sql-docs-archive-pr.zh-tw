---
title: 第 8 課：建立資料篩選 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 19ccbdba-e3da-40a4-b652-32c628cf32e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9c11d4cf83619e53cd7e8f00091c66cc8e50ad76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592506"
---
# <a name="lesson-8-create-a-data-filter"></a><span data-ttu-id="61305-102">第 8 課：建立資料篩選</span><span class="sxs-lookup"><span data-stu-id="61305-102">Lesson 8: Create a Data Filter</span></span>
  <span data-ttu-id="61305-103">在父報表上加入鑽研動作後，下一步是要針對您為子報表定義的資料表建立資料篩選。</span><span class="sxs-lookup"><span data-stu-id="61305-103">After you add a drillthrough action on the parent report, your next step is to create a data filter for the data table that you defined for the child report.</span></span>  
  
 <span data-ttu-id="61305-104">您可以為鑽研報表建立以資料表為基礎的篩選， **或** 查詢篩選。</span><span class="sxs-lookup"><span data-stu-id="61305-104">You can create a table-based filter **or** a query filter for the drillthrough report.</span></span> <span data-ttu-id="61305-105">本課將提供這兩個選項的指示。</span><span class="sxs-lookup"><span data-stu-id="61305-105">This lesson provides instructions for both options.</span></span>  
  
## <a name="table-based-filter"></a><span data-ttu-id="61305-106">以資料表為基礎的篩選</span><span class="sxs-lookup"><span data-stu-id="61305-106">Table-Based Filter</span></span>  
 <span data-ttu-id="61305-107">您需要完成下列工作，才能實作以資料表為基礎的篩選。</span><span class="sxs-lookup"><span data-stu-id="61305-107">You need to complete the following tasks to implement a table-based filter.</span></span>  
  
-   <span data-ttu-id="61305-108">將篩選運算式加入至子報表中的 Tablix。</span><span class="sxs-lookup"><span data-stu-id="61305-108">Add a filter expression to the tablix in the child report.</span></span>  
  
-   <span data-ttu-id="61305-109">建立從 `PurchaseOrderDetail` 資料表選取未篩選資料的函數。</span><span class="sxs-lookup"><span data-stu-id="61305-109">Create a function that selects unfiltered data from the `PurchaseOrderDetail` table.</span></span>  
  
-   <span data-ttu-id="61305-110">加入將 `PurchaseOrderDetail` DataTable 繫結至子報表的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="61305-110">Add an event handler that binds the `PurchaseOrderDetail` DataTable to the child report.</span></span>  
  
#### <a name="to-add-a-filter-expression-to-the-tablix-in-the-child-report"></a><span data-ttu-id="61305-111">若要將篩選運算式加入至子報表中的 Tablix</span><span class="sxs-lookup"><span data-stu-id="61305-111">To add a filter expression to the tablix in the child report</span></span>  
  
1.  <span data-ttu-id="61305-112">開啟子報表。</span><span class="sxs-lookup"><span data-stu-id="61305-112">Open the child report.</span></span>  
  
2.  <span data-ttu-id="61305-113">選取 tablix 中的資料行標題，以滑鼠右鍵按一下資料行標題上方出現的灰色資料格，然後按一下 [ **Tablix 屬性**]。</span><span class="sxs-lookup"><span data-stu-id="61305-113">Select a column heading in the tablix, right-click the gray cell that appears above the column heading, and then click **Tablix Properties**.</span></span>  
  
3.  <span data-ttu-id="61305-114">按一下 [**篩選**] 頁面，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="61305-114">Click on the **Filters** page, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="61305-115">在 [**運算式**] 欄位 `ProductID` 的下拉式清單中，按一下。</span><span class="sxs-lookup"><span data-stu-id="61305-115">In the **Expression** filed, click `ProductID` from the drop-down list.</span></span> <span data-ttu-id="61305-116">這是要套用篩選的資料行。</span><span class="sxs-lookup"><span data-stu-id="61305-116">This is the column to which you apply the filter.</span></span>  
  
5.  <span data-ttu-id="61305-117">**=** 在 [**運算子**] 下拉式清單中，按一下等於 () ] 運算子。</span><span class="sxs-lookup"><span data-stu-id="61305-117">Click the equal (**=**) operator in the **Operator** drop-down list.</span></span>  
  
6.  <span data-ttu-id="61305-118">按一下 [**值**] 欄位旁的 [運算式] 按鈕，按一下 [**類別目錄**] 區域中的 [**參數**]，然後 `productid` 在 [**值**] 區域中按兩下。</span><span class="sxs-lookup"><span data-stu-id="61305-118">Click the expression button next to the **Value** field, click **Parameters** in the **Category** area, and then double-click `productid` in the **Values** area.</span></span> <span data-ttu-id="61305-119">[設定運算式對象: 值]  欄位現在應該包含類似 **=Parameters!productid.Value** 的運算式。</span><span class="sxs-lookup"><span data-stu-id="61305-119">The **Set expression for: Value** field should now contain expression similar to **=Parameters!productid.Value**.</span></span>  
  
7.  <span data-ttu-id="61305-120">按一下 [**確定]，** 然後在 [ **Tablix 屬性**] 對話方塊中再次 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="61305-120">Click **OK,** and **OK** again in the **Tablix Properties** dialog box.</span></span>  
  
8.  <span data-ttu-id="61305-121">儲存 .rdlc 檔。</span><span class="sxs-lookup"><span data-stu-id="61305-121">Save the .rdlc file.</span></span>  
  
#### <a name="to-create-a-function-that-selects-unfiltered-data-from-the-purchaseordedetail-table"></a><span data-ttu-id="61305-122">若要建立從 PurchaseOrdeDetail 資料表選取未篩選資料的函數</span><span class="sxs-lookup"><span data-stu-id="61305-122">To create a function that selects unfiltered data from the PurchaseOrdeDetail table</span></span>  
  
1.  <span data-ttu-id="61305-123">在 [方案總管] 中展開 [Default.aspx]，然後按兩下 [Default.aspx.cs]。</span><span class="sxs-lookup"><span data-stu-id="61305-123">In Solution Explorer, expand Default.aspx, and then double click Default.aspx.cs.</span></span>  
  
2.  <span data-ttu-id="61305-124">建立接受整數類型參數 `productid` 且傳回 `datatable` 物件的新函數，並執行下列操作。</span><span class="sxs-lookup"><span data-stu-id="61305-124">Create a new function that accepts a parameter, `productid`, of type Integer and returns a `datatable` object, and does the following.</span></span>  
  
    1.  <span data-ttu-id="61305-125">建立資料集的實例， `DataSet2` 這是在第[4 課：定義子報表的資料連線和資料表](lesson-4-define-a-data-connection-and-data-table-for-child-report.md)的步驟2中所建立。</span><span class="sxs-lookup"><span data-stu-id="61305-125">Creates an instance of the dataset, `DataSet2`, which was created in Step 2 of [Lesson 4: Define a Data Connection and Data Table for Child Report](lesson-4-define-a-data-connection-and-data-table-for-child-report.md).</span></span>  
  
    2.  <span data-ttu-id="61305-126">建立與 SqlServer 資料庫的連接，以執行 **第 4 課：定義子報表的資料連接和資料表**中定義的查詢。</span><span class="sxs-lookup"><span data-stu-id="61305-126">Create a connection to the SqlServer database to execute the query defined in **Lesson 4: Define a Data Connection and DataTable for Child Report**.</span></span>  
  
    3.  <span data-ttu-id="61305-127">查詢會傳回未篩選的資料。</span><span class="sxs-lookup"><span data-stu-id="61305-127">The query will return unfiltered data.</span></span>  
  
    4.  <span data-ttu-id="61305-128">執行查詢可在 DataSet 執行個體中填入未篩選資料。</span><span class="sxs-lookup"><span data-stu-id="61305-128">Fill the DataSet instance with the unfiltered data by executing the query.</span></span>  
  
    5.  <span data-ttu-id="61305-129">傳回 `PurchaseOrderDetail` DataTable。</span><span class="sxs-lookup"><span data-stu-id="61305-129">Return the `PurchaseOrderDetail` DataTable.</span></span>  
  
         <span data-ttu-id="61305-130">函數看起來類似下面所示 (僅供參考。</span><span class="sxs-lookup"><span data-stu-id="61305-130">The function will look similar to the one below, (This is just for your reference.</span></span> <span data-ttu-id="61305-131">您可以依照想要的任何模式提取必要的子報表資料)。</span><span class="sxs-lookup"><span data-stu-id="61305-131">You can follow any pattern that you want, to fetch the necessary data for child report).</span></span>  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table, fetch the  
            /// unfiltered data and bind it with the Child report  
            /// </summary>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail()  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlDataAdapter adap = new SqlDataAdapter("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail ", sqlconn);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
#### <a name="to-add-an-event-handler-that-binds-the-purchaseorderdetail-datatable-to-the-child-report"></a><span data-ttu-id="61305-132">若要加入將 PurchaseOrderDetail DataTable 繫結至子報表的事件處理常式</span><span class="sxs-lookup"><span data-stu-id="61305-132">To add an event handler that binds the PurchaseOrderDetail DataTable to the child report</span></span>  
  
1.  <span data-ttu-id="61305-133">開啟 [Default.aspx]。</span><span class="sxs-lookup"><span data-stu-id="61305-133">Open Default.aspx.</span></span>  
  
2.  <span data-ttu-id="61305-134">以滑鼠右鍵按一下 [ReportViewer] 控制項，然後按一下 [**屬性]。**</span><span class="sxs-lookup"><span data-stu-id="61305-134">Right click the ReportViewer control, and then click **Properties.**</span></span>  
  
3.  <span data-ttu-id="61305-135">在 [**屬性**] 頁面上，按一下 [**事件**] 圖示。</span><span class="sxs-lookup"><span data-stu-id="61305-135">On the **Properties** page, click the **Events** icon.</span></span>  
  
4.  <span data-ttu-id="61305-136">按兩下 [**鑽取**] 事件。</span><span class="sxs-lookup"><span data-stu-id="61305-136">Double click the **Drillthrough** event.</span></span>  
  
     <span data-ttu-id="61305-137">這樣會在程式碼中加入事件處理常式區段，看起來類似下面區塊。</span><span class="sxs-lookup"><span data-stu-id="61305-137">This will add an event handler section in the code, which will look similar to the below block.</span></span>  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  <span data-ttu-id="61305-138">完成事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="61305-138">Complete the event handler.</span></span> <span data-ttu-id="61305-139">它應該包含下列功能。</span><span class="sxs-lookup"><span data-stu-id="61305-139">It should include the following functionalty.</span></span>  
  
    1.  <span data-ttu-id="61305-140">從 *DrillthroughEventArgs* 參數提取子報表物件參考。</span><span class="sxs-lookup"><span data-stu-id="61305-140">Fetch the child report object reference from the *DrillthroughEventArgs* parameter.</span></span>  
  
    2.  <span data-ttu-id="61305-141">呼叫函數，`GetPurchaseOrderDetail`</span><span class="sxs-lookup"><span data-stu-id="61305-141">Call the function, `GetPurchaseOrderDetail`</span></span>  
  
    3.  <span data-ttu-id="61305-142">將 `PurchaseOrderDetail` DataTable 與報表的對應資料來源繫結。</span><span class="sxs-lookup"><span data-stu-id="61305-142">Bind the `PurchaseOrderDetail` DataTable with the report's corresponding data source.</span></span>  
  
         <span data-ttu-id="61305-143">完成的事件處理常式程式碼看起來如下所示。</span><span class="sxs-lookup"><span data-stu-id="61305-143">The completed event handler code will look similar to the following.</span></span>  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                     //Get the instance of the Target report, in our case the JumpReport.rdlc.  
                    LocalReport report = (LocalReport)e.Report;  
  
                     //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail()));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  <span data-ttu-id="61305-144">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="61305-144">Save the file.</span></span>  
  
## <a name="query-filter"></a><span data-ttu-id="61305-145">查詢篩選</span><span class="sxs-lookup"><span data-stu-id="61305-145">Query Filter</span></span>  
 <span data-ttu-id="61305-146">您需要完成下列工作，才能實作查詢篩選。</span><span class="sxs-lookup"><span data-stu-id="61305-146">You need to complete the following tasks to implement a query filter.</span></span>  
  
-   <span data-ttu-id="61305-147">建立從 `PurchaseOrderDetail` 資料表選取已篩選資料的函數。</span><span class="sxs-lookup"><span data-stu-id="61305-147">Create a function that selected filtered data from the `PurchaseOrderDetail` table.</span></span>  
  
-   <span data-ttu-id="61305-148">加入擷取參數值並將 `PurchaseOrdeDetail` DataTable 繫結至子報表的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="61305-148">Add an event handler that retrieves parameter values and binds the `PurchaseOrdeDetail` DataTable to the child report.</span></span>  
  
#### <a name="to-create-a-function-that-selects-filtered-data-from-the-purchaseorderdetail-table"></a><span data-ttu-id="61305-149">若要建立從 PurchaseOrderDetail 資料表選取已篩選資料的函數</span><span class="sxs-lookup"><span data-stu-id="61305-149">To create a function that selects filtered data from the PurchaseOrderDetail table</span></span>  
  
1.  <span data-ttu-id="61305-150">在 [方案總管] 中展開 [Default.aspx]，然後按兩下 [Default.aspx.cs]。</span><span class="sxs-lookup"><span data-stu-id="61305-150">In Solution Explorer, expand Default.aspx, and then double click Default.aspx.cs.</span></span>  
  
2.  <span data-ttu-id="61305-151">建立接受整數類型參數 `productid` 且傳回 `datatable` 物件的新函數，並執行下列操作。</span><span class="sxs-lookup"><span data-stu-id="61305-151">Create a new function that accepts a parameter, `productid`, of type Integer and returns a `datatable` object and does the following.</span></span>  
  
    1.  <span data-ttu-id="61305-152">建立資料集的實例， `DataSet2` 這是在第[4 課：定義子報表的資料連線和資料表](lesson-4-define-a-data-connection-and-data-table-for-child-report.md)的步驟2中所建立。</span><span class="sxs-lookup"><span data-stu-id="61305-152">Creates an instance of the dataset, `DataSet2`, which was created in Step 2 of [Lesson 4: Define a Data Connection and Data Table for Child Report](lesson-4-define-a-data-connection-and-data-table-for-child-report.md).</span></span>  
  
    2.  <span data-ttu-id="61305-153">建立與 SqlServer 資料庫的連接，以執行 **第 4 課：定義子報表的資料連接和資料表**中定義的查詢。</span><span class="sxs-lookup"><span data-stu-id="61305-153">Create a connection to the SqlServer database to execute the query defined **Lesson 4: Define a Data Connection and DataTable for Child Report**.</span></span>  
  
    3.  <span data-ttu-id="61305-154">查詢將包含參數 `productid`，確保傳回的資料是根據父報表中選取的 `ProductID` 篩選。</span><span class="sxs-lookup"><span data-stu-id="61305-154">The query will include a parameter, `productid`, to make sure the data returned is filtered based on the `ProductID` selected in the parent report.</span></span>  
  
    4.  <span data-ttu-id="61305-155">執行查詢可在 DataSet 執行個體中填入已篩選資料。</span><span class="sxs-lookup"><span data-stu-id="61305-155">Fill the DataSet instance with the filtered data by executing the query.</span></span>  
  
    5.  <span data-ttu-id="61305-156">傳回 `PurchaseOrderDetail` DataTable。</span><span class="sxs-lookup"><span data-stu-id="61305-156">Return the `PurchaseOrderDetail` DataTable.</span></span>  
  
         <span data-ttu-id="61305-157">函數看起來類似下面所示 (僅供參考。</span><span class="sxs-lookup"><span data-stu-id="61305-157">The function will look similar to the one below, (This is just for your reference.</span></span> <span data-ttu-id="61305-158">您可以依照想要的任何模式提取必要的子報表資料)。</span><span class="sxs-lookup"><span data-stu-id="61305-158">You can follow any pattern that you want, to fetch the necessary data for child report).</span></span>  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table and filter the  
            /// data for a specific ProductID selected in the Parent report.  
            /// </summary>  
            /// <param name="productid">Parameter passed from the Parent report to filter data.</param>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail(int productid)  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlDataAdapter adap = new SqlDataAdapter("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail where ProductID = " + productid, sqlconn);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
#### <a name="to-add-an-event-handler-that-retrieves-parameter-values-and-binds-the-purchaseordedetail-datatable-to-the-child-report"></a><span data-ttu-id="61305-159">若要加入擷取參數值並將 PurchaseOrdeDetail DataTable 繫結至子報表的事件處理常式</span><span class="sxs-lookup"><span data-stu-id="61305-159">To add an event handler that retrieves parameter values and binds the PurchaseOrdeDetail DataTable to the child report</span></span>  
  
1.  <span data-ttu-id="61305-160">開啟 [Default.aspx]。</span><span class="sxs-lookup"><span data-stu-id="61305-160">Open Default.aspx.</span></span>  
  
2.  <span data-ttu-id="61305-161">以滑鼠右鍵按一下 [ReportViewer] 控制項，然後按一下 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="61305-161">Right-click the ReportViewer control, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="61305-162">在 [**屬性**] 窗格上，按一下 [**事件**] 圖示。</span><span class="sxs-lookup"><span data-stu-id="61305-162">On the **Properties** pane, click the **Events** icon.</span></span>  
  
4.  <span data-ttu-id="61305-163">按兩下 [**鑽取**] 事件。</span><span class="sxs-lookup"><span data-stu-id="61305-163">Double click the **Drillthrough** event.</span></span>  
  
     <span data-ttu-id="61305-164">這樣會在程式碼中加入事件處理常式區段，看起來類似下面所示。</span><span class="sxs-lookup"><span data-stu-id="61305-164">This will add an event handler section in the code that will look similar to the following.</span></span>  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  <span data-ttu-id="61305-165">完成事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="61305-165">Complete the event handler.</span></span> <span data-ttu-id="61305-166">它應該包含下列功能。</span><span class="sxs-lookup"><span data-stu-id="61305-166">It should include the following functionality.</span></span>  
  
    1.  <span data-ttu-id="61305-167">從 *DrillthroughEventArgs* 參數提取子報表物件參考。</span><span class="sxs-lookup"><span data-stu-id="61305-167">Fetch the Child report object reference from the *DrillthroughEventArgs* parameter.</span></span>  
  
    2.  <span data-ttu-id="61305-168">從提取的子報表物件取得子報表參數清單。</span><span class="sxs-lookup"><span data-stu-id="61305-168">Get the child report parameter list from the child report object fetched.</span></span>  
  
    3.  <span data-ttu-id="61305-169">反覆運算參數集合，並擷取從父報表傳遞之參數 `ProductID` 的值。</span><span class="sxs-lookup"><span data-stu-id="61305-169">Iterate through the parameter's collection and retrieve the value for the parameter, `ProductID`, passed from the parent report.</span></span>  
  
    4.  <span data-ttu-id="61305-170">呼叫函數 `GetPurchaseOrderDetail`，並傳遞參數 `ProductID` 的值。</span><span class="sxs-lookup"><span data-stu-id="61305-170">Call the function, `GetPurchaseOrderDetail`, and pass the value for parameter `ProductID`.</span></span>  
  
    5.  <span data-ttu-id="61305-171">將 `PurchaseOrderDetail` DataTable 與報表的對應資料來源繫結。</span><span class="sxs-lookup"><span data-stu-id="61305-171">Bind the `PurchaseOrderDetail` DataTable with the Report's corresponding data source.</span></span>  
  
         <span data-ttu-id="61305-172">完成的事件處理常式程式碼看起來如下所示。</span><span class="sxs-lookup"><span data-stu-id="61305-172">The completed event handler code will look similar to the following.</span></span>  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                    //Variable to store the parameter value passed from the MainReport.  
                    int productid = 0;  
  
                    //Get the instance of the Target report, in our case the JumpReport.rdlc.  
                    LocalReport report = (LocalReport)e.Report;  
  
                    //Get all the parameters passed from the main report to the target report.  
                    //OriginalParametersToDrillthrough actually returns a Generic list of   
                    //type ReportParameter.  
                    IList<ReportParameter> list = report.OriginalParametersToDrillthrough;  
  
                    //Parse through each parameters to fetch the values passed along with them.  
                    foreach (ReportParameter param in list)  
                    {  
                        //Since we know the report has only one parameter and it is not a multivalued,   
                        //we can directly fetch the first value from the Values array.  
                        productid = Convert.ToInt32(param.Values[0].ToString());  
                    }  
  
                    //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail(productid)));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  <span data-ttu-id="61305-173">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="61305-173">Save the file.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="61305-174">下一項工作</span><span class="sxs-lookup"><span data-stu-id="61305-174">Next Task</span></span>  
 <span data-ttu-id="61305-175">您已成功針對您為子報表定義的資料表建立資料篩選。</span><span class="sxs-lookup"><span data-stu-id="61305-175">You have successfully created a data filter for the data table that you defined for the child report.</span></span> <span data-ttu-id="61305-176">接下來您將建立並執行網站應用程式。</span><span class="sxs-lookup"><span data-stu-id="61305-176">Next, you will build and run the website application.</span></span>  
  
  
