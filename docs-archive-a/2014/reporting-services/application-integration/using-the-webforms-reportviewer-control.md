---
title: 使用 WebForms ReportViewer 控制項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- ReportViewer controls
ms.assetid: 4c200f36-4012-4108-8095-370b426ccf8d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 077dbbf0e59fc61d5a2dae5c3453e7a75542ecc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595836"
---
# <a name="using-the-webforms-reportviewer-control"></a><span data-ttu-id="cbf46-102">使用 WebForms ReportViewer 控制項</span><span class="sxs-lookup"><span data-stu-id="cbf46-102">Using the WebForms ReportViewer Control</span></span>
  <span data-ttu-id="cbf46-103">若要檢視已部署至報表伺服器或存在於本機檔案系統的報表，您可以使用 WebForms ReportViewer 控制項在 Web 應用程式中加以轉譯。</span><span class="sxs-lookup"><span data-stu-id="cbf46-103">To view reports deployed to a report server or reports that exist on the local file system, you can use the WebForms ReportViewer control to render them in a Web application.</span></span>  
  
###### <a name="to-use-the-reportviewer-control-in-a-web-application"></a><span data-ttu-id="cbf46-104">若要在 Web 應用程式中使用 ReportViewer 控制項</span><span class="sxs-lookup"><span data-stu-id="cbf46-104">To use the ReportViewer Control in a Web application</span></span>  
  
1.  <span data-ttu-id="cbf46-105">使用或建立新的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ASP.NET 網站 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cbf46-105">Create a new [!INCLUDE[msCoName](../../includes/msconame-md.md)] ASP.NET Web Site using either [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] or [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].</span></span>  
  
     <span data-ttu-id="cbf46-106">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="cbf46-106">\- Or -</span></span>  
  
     <span data-ttu-id="cbf46-107">開啟現有的 ASP.NET 網站並加入新的 Web Form。</span><span class="sxs-lookup"><span data-stu-id="cbf46-107">Open an exiting ASP.NET Web Site and add a new Web Form.</span></span>  
  
2.  <span data-ttu-id="cbf46-108">從 [工具箱]\*\*\*\* 視窗的 [AJAX 延伸模組]\*\*\*\* 群組中找出 **ScriptManager** 控制項，並將它拖曳到 Web 表單的設計介面。</span><span class="sxs-lookup"><span data-stu-id="cbf46-108">Locate the **ScriptManager** control in the **AJAX Extensions** group in the **Toolbox** window, and drag it to the design surface of the Web form.</span></span>  
  
     <span data-ttu-id="cbf46-109">如果看不到 [工具箱]\*\*\*\*，可以從 [檢視]\*\*\*\* 功能表選取 [工具箱]\*\*\*\* 加以存取。</span><span class="sxs-lookup"><span data-stu-id="cbf46-109">If the **Toolbox** is not visible, you can access it from the **View** menu by selecting **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="cbf46-110">在 [工具箱]\*\*\*\* 中找出 **ReportViewer** 控制項，並將它拖曳至設計介面上的 **ScriptManager** 控制項下方。</span><span class="sxs-lookup"><span data-stu-id="cbf46-110">Locate the **ReportViewer** control in the **Toolbox** and drag it to the design surface below the **ScriptManager** control.</span></span>  
  
     <span data-ttu-id="cbf46-111">名為 reportViewer1 的 **ReportViewer** 控制項會新增至表單。</span><span class="sxs-lookup"><span data-stu-id="cbf46-111">The **ReportViewer** control named reportViewer1 is added to the form.</span></span>  
  
 <span data-ttu-id="cbf46-112">將控制項新增至表單後，[ReportViewer 工作]\*\*\*\* 智慧標籤將會顯示以提示您選取報表。</span><span class="sxs-lookup"><span data-stu-id="cbf46-112">After the control is added to the form the **ReportViewer Tasks** smart tag will appear prompting you to select a report.</span></span> <span data-ttu-id="cbf46-113">如果您想要查看的報表已部署到報表伺服器，請 **\<Server Report>** 從 [**選擇報表**] 下拉式清單中選取選項。</span><span class="sxs-lookup"><span data-stu-id="cbf46-113">If the report you wish to view has been deployed to a report server select the **\<Server Report>** option from the **Choose Report** drop-down list.</span></span> <span data-ttu-id="cbf46-114">選取此 **\<Server Report>** 選項之後，將會顯示兩個額外的屬性： [**報表伺服器 Url** ] 和 [**報表路徑**]。</span><span class="sxs-lookup"><span data-stu-id="cbf46-114">Once the **\<Server Report>** option is selected two additional properties will appear, **Report Server Url** and **Report Path**.</span></span> <span data-ttu-id="cbf46-115">[報表伺服器 URL]\*\*\*\* 是到報表伺服器的位址，[報表路徑]\*\*\*\* 則是要轉譯之報表的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="cbf46-115">The **Report Server Url** is the address to the report server and the **Report Path** is the full path to the report you want to render.</span></span>  
  
 <span data-ttu-id="cbf46-116">如果您要以本機模式檢視報表，請選取 [設計新報表]\*\*\*\* 選項以啟動報表設計師，或選取已是現有專案一部分的報表。</span><span class="sxs-lookup"><span data-stu-id="cbf46-116">If you want to view a report in local mode select either the **Design a new report** option to launch the report designer or select a report that is already part of the existing project.</span></span> <span data-ttu-id="cbf46-117">在您選取報表之後，請務必在 ReportViewer 控制項的 **ReportPath** 屬性中輸入報表 RDLC 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="cbf46-117">After you have selected a report, be sure to enter the name of the report RDLC file in the **ReportPath** property of the ReportViewer control.</span></span> <span data-ttu-id="cbf46-118">這個屬性會出現在 [屬性]\*\*\*\* 窗格的 **LocalReport** 節點下方。</span><span class="sxs-lookup"><span data-stu-id="cbf46-118">This property appears under the **LocalReport** node in the **Properties** pane.</span></span>  
  
 <span data-ttu-id="cbf46-119">當轉譯報表時，您可以選擇隱藏 ReportViewer 工具列上的一個或多個項目。</span><span class="sxs-lookup"><span data-stu-id="cbf46-119">You have the option of hiding one or more of the items on the ReportViewer toolbar when the report is rendered.</span></span> <span data-ttu-id="cbf46-120">例如，您可以隱藏列印按鈕。</span><span class="sxs-lookup"><span data-stu-id="cbf46-120">For example, you can hide the print button.</span></span> <span data-ttu-id="cbf46-121">若要隱藏工具列專案，請 `False` 在 [**屬性**] 窗格中，將下列 ReportViewer 屬性設定為。</span><span class="sxs-lookup"><span data-stu-id="cbf46-121">To hide toolbar items, set the following ReportViewer properties to `False` in the **Properties** pane.</span></span>  
  
-   `ShowBackButton`  
  
-   `ShowExportControls`  
  
-   `ShowFindControls`  
  
-   `ShowPageNavigationControls`  
  
-   `ShowPrintButton`  
  
-   `ShowRefreshButton`  
  
-   `ShowZoomControl`  
  
## <a name="viewing-reports-in-remote-processing-mode"></a><span data-ttu-id="cbf46-122">以遠端處理模式檢視報表</span><span class="sxs-lookup"><span data-stu-id="cbf46-122">Viewing Reports in Remote Processing Mode</span></span>  
 <span data-ttu-id="cbf46-123">下列範例示範如何轉譯已部署到報表伺服器的報表。</span><span class="sxs-lookup"><span data-stu-id="cbf46-123">The following example demonstrates how to render a report that has been deployed to a report server.</span></span> <span data-ttu-id="cbf46-124">這個範例使用包含在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例報表專案中的 Sales Order Detail 報表。</span><span class="sxs-lookup"><span data-stu-id="cbf46-124">This example uses the Sales Order Detail report that is included with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample reports project.</span></span>  
  
 <span data-ttu-id="cbf46-125">此範例使用整合式 Windows 驗證，因此您必須啟用模擬。</span><span class="sxs-lookup"><span data-stu-id="cbf46-125">The example uses integrated Windows Authentication so you first must enable impersonation.</span></span> <span data-ttu-id="cbf46-126">若要這麼做，請將下列程式程式碼插入檔案中 `web.config` ：</span><span class="sxs-lookup"><span data-stu-id="cbf46-126">To do this insert the following line into the `web.config` file:</span></span>  
  
```  
<!-- Web.config file. -->  
<identity impersonate="true"/>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="cbf46-127">預設會啟用模擬。</span><span class="sxs-lookup"><span data-stu-id="cbf46-127">Impersonation is disabled by default.</span></span>  
  
```csharp  
protected void Page_Init(object sender, EventArgs e)  
{  
    if (!Page.IsPostBack)  
    {  
        // Set the processing mode for the ReportViewer to Remote  
        reportViewer.ProcessingMode = ProcessingMode.Remote;  
  
        ServerReport serverReport = reportViewer.ServerReport;  
  
        // Set the report server URL and report path  
        serverReport.ReportServerUrl =  
            new Uri("http://<Server Name>/reportserver");  
        serverReport.ReportPath =  
            "/AdventureWorks Sample Reports/Sales Order Detail";  
  
        // Create the sales order number report parameter  
        ReportParameter salesOrderNumber = new ReportParameter();  
        salesOrderNumber.Name = "SalesOrderNumber";  
        salesOrderNumber.Values.Add("SO43661");  
  
        // Set the report parameters for the report  
        reportViewer.ServerReport.SetParameters(  
            new ReportParameter[] { salesOrderNumber });  
    }  
}  
```  
  
```vb  
Imports Microsoft.Reporting.WebForms  
  
Partial Class _Default  
    Inherits System.Web.UI.Page  
  
    Protected Sub Page_Init(ByVal sender As Object, _  
            ByVal e As System.EventArgs) Handles Me.Init  
  
        If Not Page.IsPostBack Then  
  
            'Set the processing mode for the ReportViewer to Remote  
            reportViewer.ProcessingMode = ProcessingMode.Remote  
  
            Dim serverReport As ServerReport  
            serverReport = reportViewer.ServerReport  
  
            'Set the report server URL and report path  
            serverReport.ReportServerUrl = _  
                New Uri("http://<Server Name>/reportserver")  
            serverReport.ReportPath = _  
                "/AdventureWorks Sample Reports/Sales Order Detail"  
  
            'Create the sales order number report parameter  
            Dim salesOrderNumber As New ReportParameter()  
            salesOrderNumber.Name = "SalesOrderNumber"  
            salesOrderNumber.Values.Add("SO43661")  
  
            'Set the report parameters for the report  
            Dim parameters() As ReportParameter = {salesOrderNumber}  
            serverReport.SetParameters(parameters)  
  
        End If  
  
    End Sub  
  
End Class  
```  
  
## <a name="viewing-reports-in-local-processing-mode"></a><span data-ttu-id="cbf46-128">以本機處理模式檢視報表</span><span class="sxs-lookup"><span data-stu-id="cbf46-128">Viewing Reports in Local Processing Mode</span></span>  
 <span data-ttu-id="cbf46-129">下列範例示範如何轉譯是 Windows 應用程式的一部分且尚未部署到報表伺服器的報表。</span><span class="sxs-lookup"><span data-stu-id="cbf46-129">The following example demonstrates how to render a report that is part of the Windows application and has not been deployed to a report server.</span></span>  
  
###### <a name="to-add-the-sales-order-detail-report-to-a-web-site"></a><span data-ttu-id="cbf46-130">若要將 Sales Order Detail 報表加入網站</span><span class="sxs-lookup"><span data-stu-id="cbf46-130">To add the Sales Order Detail report to a Web Site</span></span>  
  
1.  <span data-ttu-id="cbf46-131">開啟將加入報表的網站。</span><span class="sxs-lookup"><span data-stu-id="cbf46-131">Open the Web Site that the report will be added to.</span></span>  
  
2.  <span data-ttu-id="cbf46-132">從 [網站]\*\*\*\* 功能表上，選取 [新增現有項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cbf46-132">From the **Website** menu, select **Add Existing Item**.</span></span>  
  
3.  <span data-ttu-id="cbf46-133">瀏覽至安裝 AdventureWorks 報表範例專案的位置。</span><span class="sxs-lookup"><span data-stu-id="cbf46-133">Browse to the location where the AdventureWorks Report Samples project is installed.</span></span>  
  
     <span data-ttu-id="cbf46-134">預設位置是 C:\Program Files\Microsoft SQL Server\100\Samples\Reporting Services\Report Samples\AdventureWorks Sample Reports。</span><span class="sxs-lookup"><span data-stu-id="cbf46-134">The default location is C:\Program Files\Microsoft SQL Server\100\Samples\Reporting Services\Report Samples\AdventureWorks Sample Reports.</span></span>  
  
4.  <span data-ttu-id="cbf46-135">選取 Sales Order Detail.rdl 檔案，然後按一下 [新增]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="cbf46-135">Select the Sales Order Detail.rdl file and click the **Add** button.</span></span>  
  
     <span data-ttu-id="cbf46-136">Sales Order Detail.rdl 檔案現在應該是專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="cbf46-136">The Sales Order Detail.rdl file should now be part of the project.</span></span>  
  
5.  <span data-ttu-id="cbf46-137">在方案總管中，以滑鼠右鍵按一下 Sales Order Detail.rdl 檔案，然後選擇 [重新命名]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cbf46-137">Right-click the Sales Order Detail.rdl file in Solution Explorer and select **Rename**.</span></span> <span data-ttu-id="cbf46-138">將報表重新命名為 **Sales Order Detail.rdlc**，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="cbf46-138">Rename the report to **Sales Order Detail.rdlc** and press ENTER.</span></span>  
  
     <span data-ttu-id="cbf46-139">如果看不到方案總管，您可以選取 [方案總管]，從 [ **View** ] 功能表中開啟它。</span><span class="sxs-lookup"><span data-stu-id="cbf46-139">If Solution Explorer is not visible, you can open it from the **View** menu by selecting Solution Explorer.</span></span>  
  
 <span data-ttu-id="cbf46-140">下列的程式碼範例會為銷售訂單資料建立資料集，然後以本機模式轉譯 Sales Order Detail 報表。</span><span class="sxs-lookup"><span data-stu-id="cbf46-140">The following code example will create a dataset for the sales order data and then render the Sales Order Detail report in local mode.</span></span>  
  
```csharp  
protected void Page_Init(object sender, EventArgs e)  
{  
    if (!Page.IsPostBack)  
    {  
        // Set the processing mode for the ReportViewer to Local  
        reportViewer.ProcessingMode = ProcessingMode.Local;  
  
        LocalReport localReport = reportViewer.LocalReport;  
  
        localReport.ReportPath = "Sales Order Detail.rdlc";  
  
        DataSet dataset = new DataSet("Sales Order Detail");  
  
        string salesOrderNumber = "SO43661";  
  
        GetSalesOrderData(salesOrderNumber, ref dataset);  
  
        ReportDataSource dsSalesOrder = new ReportDataSource();  
        dsSalesOrder.Name = "SalesOrder";  
        dsSalesOrder.Value = dataset.Tables["SalesOrder"];  
  
        localReport.DataSources.Add(dsSalesOrder);  
  
        GetSalesOrderDetailData(salesOrderNumber, ref dataset);  
  
        ReportDataSource dsSalesOrderDetail = new ReportDataSource();  
        dsSalesOrderDetail.Name = "SalesOrderDetail";  
        dsSalesOrderDetail.Value = dataset.Tables["SalesOrderDetail"];  
  
        localReport.DataSources.Add(dsSalesOrderDetail);  
  
        // Create the sales order number report parameter  
        ReportParameter rpSalesOrderNumber = new ReportParameter();  
        rpSalesOrderNumber.Name = "SalesOrderNumber";  
        rpSalesOrderNumber.Values.Add("SO43661");  
  
        // Set the report parameters for the report  
        localReport.SetParameters(  
            new ReportParameter[] { rpSalesOrderNumber });  
    }  
}  
  
private void GetSalesOrderData(string salesOrderNumber,  
                           ref DataSet dsSalesOrder)  
{  
    string sqlSalesOrder =  
        "SELECT SOH.SalesOrderNumber, S.Name AS Store, " +  
        "       SOH.OrderDate, C.FirstName AS SalesFirstName, " +  
        "       C.LastName AS SalesLastName, E.Title AS " +  
        "       SalesTitle, SOH.PurchaseOrderNumber, " +  
        "       SM.Name AS ShipMethod, BA.AddressLine1 " +  
        "       AS BillAddress1, BA.AddressLine2 AS " +  
        "       BillAddress2, BA.City AS BillCity, " +  
        "       BA.PostalCode AS BillPostalCode, BSP.Name " +  
        "       AS BillStateProvince, BCR.Name AS " +  
        "       BillCountryRegion, SA.AddressLine1 AS " +  
        "       ShipAddress1, SA.AddressLine2 AS " +  
        "       ShipAddress2, SA.City AS ShipCity, " +  
        "       SA.PostalCode AS ShipPostalCode, SSP.Name " +  
        "       AS ShipStateProvince, SCR.Name AS " +  
        "       ShipCountryRegion, CC.Phone AS CustPhone, " +  
        "       CC.FirstName AS CustFirstName, CC.LastName " +  
        "       AS CustLastName " +  
        "FROM   Person.Address SA INNER JOIN " +  
        "       Person.StateProvince SSP ON " +  
        "       SA.StateProvinceID = SSP.StateProvinceID " +  
        "       INNER JOIN Person.CountryRegion SCR ON " +  
        "       SSP.CountryRegionCode = SCR.CountryRegionCode " +  
        "       RIGHT OUTER JOIN Sales.SalesOrderHeader SOH " +  
        "       LEFT OUTER JOIN  Person.Contact CC ON " +  
        "       SOH.ContactID = CC.ContactID LEFT OUTER JOIN" +  
        "       Person.Address BA INNER JOIN " +  
        "       Person.StateProvince BSP ON " +  
        "       BA.StateProvinceID = BSP.StateProvinceID " +  
        "       INNER JOIN Person.CountryRegion BCR ON " +  
        "       BSP.CountryRegionCode = " +  
        "       BCR.CountryRegionCode ON SOH.BillToAddressID " +  
        "       = BA.AddressID ON  SA.AddressID = " +  
        "       SOH.ShipToAddressID LEFT OUTER JOIN " +  
        "       Person.Contact C RIGHT OUTER JOIN " +  
        "       HumanResources.Employee E ON C.ContactID = " +  
        "       E.ContactID ON SOH.SalesPersonID = " +  
        "       E.EmployeeID LEFT OUTER JOIN " +  
        "       Purchasing.ShipMethod SM ON SOH.ShipMethodID " +  
        "       = SM.ShipMethodID LEFT OUTER JOIN Sales.Store" +  
        "        S ON SOH.CustomerID = S.CustomerID " +  
        "WHERE  (SOH.SalesOrderNumber = @SalesOrderNumber)";  
  
    SqlConnection connection = new  
        SqlConnection("Data Source=(local); " +  
                      "Initial Catalog=AdventureWorks; " +  
                      "Integrated Security=SSPI");  
  
    SqlCommand command =  
        new SqlCommand(sqlSalesOrder, connection);  
  
    command.Parameters.Add(  
        new SqlParameter("SalesOrderNumber",  
        salesOrderNumber));  
  
    SqlDataAdapter salesOrderAdapter = new  
        SqlDataAdapter(command);  
  
    salesOrderAdapter.Fill(dsSalesOrder, "SalesOrder");  
}  
  
private void GetSalesOrderDetailData(string salesOrderNumber,  
                       ref DataSet dsSalesOrder)  
{  
    string sqlSalesOrderDetail =  
        "SELECT  SOD.SalesOrderDetailID, SOD.OrderQty, " +  
        "        SOD.UnitPrice, CASE WHEN " +  
        "        SOD.UnitPriceDiscount IS NULL THEN 0 " +  
        "        ELSE SOD.UnitPriceDiscount END AS " +  
        "        UnitPriceDiscount, SOD.LineTotal, " +  
        "        SOD.CarrierTrackingNumber, " +  
        "        SOD.SalesOrderID, P.Name, P.ProductNumber " +  
        "FROM    Sales.SalesOrderDetail SOD INNER JOIN " +  
        "        Production.Product P ON SOD.ProductID = " +  
        "        P.ProductID INNER JOIN " +  
        "        Sales.SalesOrderHeader SOH ON " +  
        "        SOD.SalesOrderID = SOH.SalesOrderID " +  
        "WHERE   (SOH.SalesOrderNumber = @SalesOrderNumber) " +  
        "ORDER BY SOD.SalesOrderDetailID";  
  
    using (SqlConnection connection = new  
        SqlConnection("Data Source=(local); " +  
                      "Initial Catalog=AdventureWorks; " +  
                      "Integrated Security=SSPI"))  
    {  
  
        SqlCommand command =  
            new SqlCommand(sqlSalesOrderDetail, connection);  
  
        command.Parameters.Add(  
            new SqlParameter("SalesOrderNumber",  
            salesOrderNumber));  
  
        SqlDataAdapter salesOrderDetailAdapter = new  
            SqlDataAdapter(command);  
  
        salesOrderDetailAdapter.Fill(dsSalesOrder,  
            "SalesOrderDetail");  
    }  
}  
```  
  
```vb  
Imports System.Data  
Imports System.Data.SqlClient  
Imports Microsoft.Reporting.WebForms  
  
Partial Class _Default  
    Inherits System.Web.UI.Page  
  
    Protected Sub Page_Init(ByVal sender As Object, _  
                ByVal e As System.EventArgs) Handles Me.Init  
  
        If Not Page.IsPostBack Then  
  
            'Set the processing mode for the ReportViewer to Local  
            reportViewer.ProcessingMode = ProcessingMode.Local  
  
            Dim localReport As LocalReport  
            localReport = reportViewer.LocalReport  
  
            localReport.ReportPath = "Sales Order Detail.rdlc"  
  
            Dim dataset As New DataSet("Sales Order Detail")  
  
            Dim salesOrderNumber As String = "SO43661"  
  
            'Get the sales order data  
            GetSalesOrderData(salesOrderNumber, dataset)  
  
            'Create a report data source for the sales order data  
            Dim dsSalesOrder As New ReportDataSource()  
            dsSalesOrder.Name = "SalesOrder"  
            dsSalesOrder.Value = dataset.Tables("SalesOrder")  
  
            localReport.DataSources.Add(dsSalesOrder)  
  
            'Get the sales order detail data  
            GetSalesOrderDetailData(salesOrderNumber, dataset)  
  
            'Create a report data source for the sales   
            'order detail data  
            Dim dsSalesOrderDetail As New ReportDataSource()  
            dsSalesOrderDetail.Name = "SalesOrderDetail"  
            dsSalesOrderDetail.Value = _  
                dataset.Tables("SalesOrderDetail")  
  
            localReport.DataSources.Add(dsSalesOrderDetail)  
  
            'Create a report parameter for the sales order number   
            Dim rpSalesOrderNumber As New ReportParameter()  
            rpSalesOrderNumber.Name = "SalesOrderNumber"  
            rpSalesOrderNumber.Values.Add("SO43661")  
  
            'Set the report parameters for the report  
            Dim parameters() As ReportParameter = {rpSalesOrderNumber}  
            localReport.SetParameters(parameters)  
  
        End If  
  
    End Sub  
  
    Private Sub GetSalesOrderData(ByVal salesOrderNumber As String, _  
                               ByRef dsSalesOrder As DataSet)  
  
        Dim sqlSalesOrder As String = _  
            "SELECT SOH.SalesOrderNumber, S.Name AS Store, " & _  
            "       SOH.OrderDate, C.FirstName AS SalesFirstName, " & _  
            "       C.LastName AS SalesLastName, E.Title AS " & _  
            "       SalesTitle, SOH.PurchaseOrderNumber, " & _  
            "       SM.Name AS ShipMethod, BA.AddressLine1 " & _  
            "       AS BillAddress1, BA.AddressLine2 AS " & _  
            "       BillAddress2, BA.City AS BillCity, " & _  
            "       BA.PostalCode AS BillPostalCode, BSP.Name " & _  
            "       AS BillStateProvince, BCR.Name AS " & _  
            "       BillCountryRegion, SA.AddressLine1 AS " & _  
            "       ShipAddress1, SA.AddressLine2 AS " & _  
            "       ShipAddress2, SA.City AS ShipCity, " & _  
            "       SA.PostalCode AS ShipPostalCode, SSP.Name " & _  
            "       AS ShipStateProvince, SCR.Name AS " & _  
            "       ShipCountryRegion, CC.Phone AS CustPhone, " & _  
            "       CC.FirstName AS CustFirstName, CC.LastName " & _  
            "       AS CustLastName " & _  
            "FROM   Person.Address SA INNER JOIN " & _  
            "       Person.StateProvince SSP ON " & _  
            "       SA.StateProvinceID = SSP.StateProvinceID " & _  
            "       INNER JOIN Person.CountryRegion SCR ON " & _  
            "       SSP.CountryRegionCode = SCR.CountryRegionCode " & _  
            "       RIGHT OUTER JOIN Sales.SalesOrderHeader SOH " & _  
            "       LEFT OUTER JOIN  Person.Contact CC ON " & _  
            "       SOH.ContactID = CC.ContactID LEFT OUTER JOIN" & _  
            "       Person.Address BA INNER JOIN " & _  
            "       Person.StateProvince BSP ON " & _  
            "       BA.StateProvinceID = BSP.StateProvinceID " & _  
            "       INNER JOIN Person.CountryRegion BCR ON " & _  
            "       BSP.CountryRegionCode = " & _  
            "       BCR.CountryRegionCode ON SOH.BillToAddressID " & _  
            "       = BA.AddressID ON  SA.AddressID = " & _  
            "       SOH.ShipToAddressID LEFT OUTER JOIN " & _  
            "       Person.Contact C RIGHT OUTER JOIN " & _  
            "       HumanResources.Employee E ON C.ContactID = " & _  
            "       E.ContactID ON SOH.SalesPersonID = " & _  
            "       E.EmployeeID LEFT OUTER JOIN " & _  
            "       Purchasing.ShipMethod SM ON SOH.ShipMethodID " & _  
            "       = SM.ShipMethodID LEFT OUTER JOIN Sales.Store" & _  
            "        S ON SOH.CustomerID = S.CustomerID " & _  
            "WHERE  (SOH.SalesOrderNumber = @SalesOrderNumber)"  
  
        Using connection As New SqlConnection( _  
                      "Data Source=(local); " & _  
                      "Initial Catalog=AdventureWorks; " & _  
                      "Integrated Security=SSPI")  
  
            Dim command As New SqlCommand(sqlSalesOrder, connection)  
  
            Dim parameter As New SqlParameter("SalesOrderNumber", _  
                salesOrderNumber)  
            command.Parameters.Add(parameter)  
  
            Dim salesOrderAdapter As New SqlDataAdapter(command)  
  
            salesOrderAdapter.Fill(dsSalesOrder, "SalesOrder")  
  
        End Using  
  
    End Sub  
  
    Private Sub GetSalesOrderDetailData( _  
                           ByVal salesOrderNumber As String, _  
                           ByRef dsSalesOrder As DataSet)  
  
        Dim sqlSalesOrderDetail As String = _  
            "SELECT  SOD.SalesOrderDetailID, SOD.OrderQty, " & _  
            "        SOD.UnitPrice, CASE WHEN " & _  
            "        SOD.UnitPriceDiscount IS NULL THEN 0 " & _  
            "        ELSE SOD.UnitPriceDiscount END AS " & _  
            "        UnitPriceDiscount, SOD.LineTotal, " & _  
            "        SOD.CarrierTrackingNumber, " & _  
            "        SOD.SalesOrderID, P.Name, P.ProductNumber " & _  
            "FROM    Sales.SalesOrderDetail SOD INNER JOIN " & _  
            "        Production.Product P ON SOD.ProductID = " & _  
            "        P.ProductID INNER JOIN " & _  
            "        Sales.SalesOrderHeader SOH ON " & _  
            "        SOD.SalesOrderID = SOH.SalesOrderID " & _  
            "WHERE   (SOH.SalesOrderNumber = @SalesOrderNumber) " & _  
            "ORDER BY SOD.SalesOrderDetailID"  
  
        Using connection As New SqlConnection( _  
                      "Data Source=(local); " & _  
                      "Initial Catalog=AdventureWorks; " & _  
                      "Integrated Security=SSPI")  
  
            Dim command As New SqlCommand(sqlSalesOrderDetail, _  
                                          connection)  
  
            Dim parameter As New SqlParameter("SalesOrderNumber", _  
                salesOrderNumber)  
            command.Parameters.Add(parameter)  
  
            Dim salesOrderDetailAdapter As New SqlDataAdapter(command)  
  
            salesOrderDetailAdapter.Fill(dsSalesOrder, _  
                "SalesOrderDetail")  
  
        End Using  
  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbf46-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbf46-141">See Also</span></span>  
 [<span data-ttu-id="cbf46-142">使用 ReportViewer 控制項整合 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="cbf46-142">Integrating Reporting Services Using the ReportViewer Controls</span></span>](integrating-reporting-services-using-reportviewer-controls.md)  
  
  
