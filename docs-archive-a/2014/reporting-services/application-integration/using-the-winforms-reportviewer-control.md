---
title: 使用 WinForms ReportViewer 控制項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- ReportViewer controls
ms.assetid: 29fb9f7d-ba65-49fd-9cbc-4c380869de96
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3e4eda5218a91b3c8286177607034da230ff7cc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595825"
---
# <a name="using-the-winforms-reportviewer-control"></a><span data-ttu-id="fd9e3-102">使用 WinForms ReportViewer 控制項</span><span class="sxs-lookup"><span data-stu-id="fd9e3-102">Using the WinForms ReportViewer Control</span></span>
  <span data-ttu-id="fd9e3-103">若要檢視已部署至報表伺服器或存在於本機檔案系統的報表，您可以使用 WinForms ReportViewer 控制項在 Windows 應用程式中加以轉譯。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-103">To view reports that have been deployed to a report server or reports that exist on the local file system, you can use the WinForms ReportViewer control to render them in a Windows application.</span></span>  
  
###### <a name="to-add-the-reportviewer-control-to-a-windows-application"></a><span data-ttu-id="fd9e3-104">將 ReportViewer 控制項加入至 Windows 應用程式</span><span class="sxs-lookup"><span data-stu-id="fd9e3-104">To add the ReportViewer Control to a Windows application</span></span>  
  
1.  <span data-ttu-id="fd9e3-105">使用或建立新的 Windows 應用程式 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-105">Create a new Windows application using either [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] or [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].</span></span>  
  
     <span data-ttu-id="fd9e3-106">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="fd9e3-106">\- Or -</span></span>  
  
     <span data-ttu-id="fd9e3-107">開啟現有的 Windows 應用程式專案並加入的新表單。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-107">Open an exiting Windows application project and add a new form.</span></span>  
  
2.  <span data-ttu-id="fd9e3-108">在 [工具箱]\*\*\*\* 中找出 ReportViewer 控制項。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-108">Locate the ReportViewer control in the **Toolbox**.</span></span> <span data-ttu-id="fd9e3-109">如果看不到 [工具箱]\*\*\*\*，可以從 [檢視]\*\*\*\* 功能表選取 [工具箱]\*\*\*\* 加以存取。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-109">If the **Toolbox** is not visible, you can access it from the **View** menu by selecting **Toolbox**.</span></span>  
  
     <span data-ttu-id="fd9e3-110">![選取 ReportViewer 控制項](../../../2014/reporting-services/media/windowsapp-toolboxreportviewer.png "選取 ReportViewer 控制項")</span><span class="sxs-lookup"><span data-stu-id="fd9e3-110">![Selecting ReportViewer control](../../../2014/reporting-services/media/windowsapp-toolboxreportviewer.png "Selecting ReportViewer control")</span></span>  
  
3.  <span data-ttu-id="fd9e3-111">拖曳 ReportViewer 控制項至 Windows Form 的設計介面。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-111">Drag the ReportViewer control onto the design surface of the Windows Form.</span></span>  
  
     <span data-ttu-id="fd9e3-112">名為 reportViewer1 的 ReportViewer 控制項會加入至表單。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-112">A ReportViewer control named reportViewer1 is added to the form.</span></span>  
  
 <span data-ttu-id="fd9e3-113">將控制項新增至表單後，[ReportViewer 工作]\*\*\*\* 智慧標籤會顯示，並提示您選取報表。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-113">After the control is added to the form, the **ReportViewer Tasks** smart tag appears and prompts you to select a report.</span></span>  
  
 <span data-ttu-id="fd9e3-114">如果您想要查看的報表已經部署到報表伺服器，請 **\<Server Report>** 從 [**選擇報表**] 下拉式清單中選取選項。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-114">If the report you wish to view has been deployed to a report server, select the **\<Server Report>** option from the **Choose Report** drop-down list.</span></span> <span data-ttu-id="fd9e3-115">選取此 **\<Server Report>** 選項之後，會出現兩個額外的屬性： [**報表伺服器 Url** ] 和 [**報表路徑**]。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-115">After the **\<Server Report>** option is selected, two additional properties appear: **Report Server Url** and **Report Path**.</span></span> <span data-ttu-id="fd9e3-116">[報表伺服器 URL]\*\*\*\* 是報表伺服器的位址，[報表路徑]\*\*\*\* 則是要轉譯之報表的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-116">The **Report Server Url** is the address to the report server and the **Report Path** is the full path to the report to render.</span></span>  
  
 <span data-ttu-id="fd9e3-117">![選取伺服器報表](../../../2014/reporting-services/media/windowsapp-serverreportsettings.png "選取伺服器報表")</span><span class="sxs-lookup"><span data-stu-id="fd9e3-117">![Select server report](../../../2014/reporting-services/media/windowsapp-serverreportsettings.png "Select server report")</span></span>  
  
 <span data-ttu-id="fd9e3-118">如果您要檢視的報表是本機模式報表，請選取 [設計新報表]\*\*\*\* 選項以啟動報表設計師，或選取已是現有專案一部分的報表。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-118">If the report you wish to view a report in local mode, select either the **Design a new report** option to launch the report designer or select a report that is already part of the existing project.</span></span>  
  
 <span data-ttu-id="fd9e3-119">![選取本機報表](../../../2014/reporting-services/media/windowsapp-localreportsettings.png "選取本機報表")</span><span class="sxs-lookup"><span data-stu-id="fd9e3-119">![Select local report](../../../2014/reporting-services/media/windowsapp-localreportsettings.png "Select local report")</span></span>  
  
## <a name="viewing-reports-in-remote-processing-mode"></a><span data-ttu-id="fd9e3-120">以遠端處理模式檢視報表</span><span class="sxs-lookup"><span data-stu-id="fd9e3-120">Viewing Reports in Remote Processing Mode</span></span>  
 <span data-ttu-id="fd9e3-121">下列範例示範如何使用 WinForms ReportViewer 控制項轉譯已部署到報表伺服器的報表。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-121">The following example demonstrates how to render a report that has been deployed to a report server using the WinForms ReportViewer control.</span></span> <span data-ttu-id="fd9e3-122">這個範例使用包含在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例報表專案中的 Sales Order Detail 報表。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-122">This example uses the Sales Order Detail report that is included with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample reports project.</span></span>  
  
```csharp  
public partial class Form1 : Form  
{  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        // Set the processing mode for the ReportViewer to Remote  
        reportViewer1.ProcessingMode = ProcessingMode.Remote;  
  
        ServerReport serverReport = reportViewer1.ServerReport;  
  
        // Get a reference to the default credentials  
        System.Net.ICredentials credentials =  
            System.Net.CredentialCache.DefaultCredentials;  
  
        // Get a reference to the report server credentials  
        ReportServerCredentials rsCredentials =  
            serverReport.ReportServerCredentials;  
  
        // Set the credentials for the server report  
        rsCredentials.NetworkCredentials = credentials;  
  
        // Set the report server URL and report path  
        serverReport.ReportServerUrl =   
            new Uri("http:// <Server Name>/reportserver");  
        serverReport.ReportPath =   
            "/AdventureWorks Sample Reports/Sales Order Detail";  
  
        // Create the sales order number report parameter  
        ReportParameter salesOrderNumber = new ReportParameter();  
        salesOrderNumber.Name = "SalesOrderNumber";  
        salesOrderNumber.Values.Add("SO43661");  
  
        // Set the report parameters for the report  
        reportViewer1.ServerReport.SetParameters(  
            new ReportParameter[] { salesOrderNumber });  
  
        // Refresh the report  
        reportViewer1.RefreshReport();  
    }  
}  
```  
  
```vb  
Imports Microsoft.Reporting.WinForms  
  
Public Class Form1  
  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
                           ByVal e As System.EventArgs) _  
                           Handles MyBase.Load  
  
        'Set the processing mode for the ReportViewer to Remote  
        reportViewer1.ProcessingMode = ProcessingMode.Remote  
  
        Dim serverReport As ServerReport  
        serverReport = reportViewer1.ServerReport  
  
        'Get a reference to the default credentials  
        Dim credentials As System.Net.ICredentials  
        credentials = System.Net.CredentialCache.DefaultCredentials  
  
        'Get a reference to the report server credentials  
        Dim rsCredentials As ReportServerCredentials  
        rsCredentials = serverReport.ReportServerCredentials  
  
        'Set the credentials for the server report  
        rsCredentials.NetworkCredentials = credentials  
  
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
  
        'Refresh the report  
        reportViewer1.RefreshReport()  
    End Sub  
  
End Class  
```  
  
## <a name="viewing-reports-in-local-processing-mode"></a><span data-ttu-id="fd9e3-123">以本機處理模式檢視報表</span><span class="sxs-lookup"><span data-stu-id="fd9e3-123">Viewing Reports in Local Processing Mode</span></span>  
 <span data-ttu-id="fd9e3-124">下列範例示範如何轉譯是 Windows 應用程式的一部分且尚未部署到報表伺服器的報表。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-124">The following example demonstrates how to render a report that is part of the Windows application and has not been deployed to a report server.</span></span>  
  
###### <a name="to-add-the-sales-order-detail-report-to-a-windows-application"></a><span data-ttu-id="fd9e3-125">將 Sales Order Detail 報表加入至 Windows 應用程式</span><span class="sxs-lookup"><span data-stu-id="fd9e3-125">To add the Sales Order Detail report to a Windows application</span></span>  
  
1.  <span data-ttu-id="fd9e3-126">開啟其中將加入此報表的 Windows 專案。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-126">Open the Windows project to which the report will be added.</span></span>  
  
2.  <span data-ttu-id="fd9e3-127">從 [專案]\*\*\*\* 功能表上，選取 [新增現有項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-127">From the **Project** menu, select **Add Existing Item**.</span></span>  
  
3.  <span data-ttu-id="fd9e3-128">瀏覽到安裝「[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 報表範例」專案的位置。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-128">Browse to the location where you installed the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] Report Samples project.</span></span>  
  
     <span data-ttu-id="fd9e3-129">如果要下載報表範例，請移至 [AdventureWorks 2012 報表範例](https://go.microsoft.com/fwlink/?LinkId=404153)</span><span class="sxs-lookup"><span data-stu-id="fd9e3-129">The download the report samples, go to [AdventureWorks 2012 Report Samples](https://go.microsoft.com/fwlink/?LinkId=404153)</span></span>  
  
4.  <span data-ttu-id="fd9e3-130">選取 Sales Order Detail.rdl 檔案，然後按一下 [新增]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-130">Select the Sales Order Detail.rdl file and click the **Add** button.</span></span>  
  
     <span data-ttu-id="fd9e3-131">Sales Order Detail.rdl 檔案現在應該是專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-131">The Sales Order Detail.rdl file should now be part of the project.</span></span>  
  
     <span data-ttu-id="fd9e3-132">![銷售訂單詳細資料報表](../../../2014/reporting-services/media/windowsapp-salesorderdetailreport.png "銷售訂單詳細資料報表")</span><span class="sxs-lookup"><span data-stu-id="fd9e3-132">![Sales Order Detail Report](../../../2014/reporting-services/media/windowsapp-salesorderdetailreport.png "Sales Order Detail Report")</span></span>  
  
5.  <span data-ttu-id="fd9e3-133">在方案總管中，以滑鼠右鍵按一下 Sales Order Detail.rdl 檔案，然後選擇 [重新命名]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-133">Right-click the Sales Order Detail.rdl file in Solution Explorer and select **Rename**.</span></span> <span data-ttu-id="fd9e3-134">將報表重新命名為 **Sales Order Detail.rdlc**，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-134">Rename the report to **Sales Order Detail.rdlc** and press ENTER.</span></span>  
  
     <span data-ttu-id="fd9e3-135">如果看不到方案總管，可以從 [檢視]\*\*\*\* 功能表選取方案總管\*\*\*\* 開啟。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-135">If Solution Explorer is not visible, you can open it from the **View** menu by selecting **Solution Explorer**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fd9e3-136">將副檔名從 rdl 重新命名為 rdlc 可以讓您使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] 的報表設計師編輯報表。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-136">Renaming the file extension from rdl to rdlc will allow you to edit the report using report designer for [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)].</span></span>  
  
6.  <span data-ttu-id="fd9e3-137">在報表重新命名後，選取檔案並找出 [屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-137">After the report has been renamed, select the file and locate the Properties window.</span></span> <span data-ttu-id="fd9e3-138">將 [複製到輸出目錄]\*\*\*\* 屬性變更為 [有更新時才複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-138">Change the **Copy to Output Directory** property to **Copy if Newer**.</span></span>  
  
     <span data-ttu-id="fd9e3-139">![設定 [複製到輸出] 設定](../../../2014/reporting-services/media/windowsapp-copytooutputsetting.png "設定 [複製到輸出] 設定")</span><span class="sxs-lookup"><span data-stu-id="fd9e3-139">![Configuring Copy To Output setting](../../../2014/reporting-services/media/windowsapp-copytooutputsetting.png "Configuring Copy To Output setting")</span></span>  
  
     <span data-ttu-id="fd9e3-140">如果看不到 [屬性]\*\*\*\* 視窗，可以從 [檢視]\*\*\*\* 功能表選取 [屬性視窗]\*\*\*\* 加以開啟。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-140">If the **Properties** window is not visible, you can open it from the **View** menu by selecting **Properties Window**.</span></span>  
  
 <span data-ttu-id="fd9e3-141">下列的程式碼範例會為銷售訂單資料建立資料集，然後以本機模式轉譯 Sales Order Detail 報表。</span><span class="sxs-lookup"><span data-stu-id="fd9e3-141">The following code example will create a dataset for the sales order data and then render the Sales Order Detail report in local mode.</span></span>  
  
```csharp  
public partial class Form1 : Form  
{  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        // Set the processing mode for the ReportViewer to Local  
        reportViewer1.ProcessingMode = ProcessingMode.Local;  
  
        LocalReport localReport = reportViewer1.LocalReport;  
  
        localReport.ReportPath = "Sales Order Detail.rdlc";  
  
        DataSet dataset = new DataSet("Sales Order Detail");  
  
        string salesOrderNumber = "SO43661";  
  
        // Get the sales order data  
        GetSalesOrderData(salesOrderNumber, ref dataset);  
  
        // Create a report data source for the sales order data  
        ReportDataSource dsSalesOrder = new ReportDataSource();  
        dsSalesOrder.Name = "SalesOrder";  
        dsSalesOrder.Value = dataset.Tables["SalesOrder"];  
  
        localReport.DataSources.Add(dsSalesOrder);  
  
        // Get the sales order detail data  
        GetSalesOrderDetailData(salesOrderNumber, ref dataset);  
  
        // Create a report data source for the sales order detail   
        // data  
        ReportDataSource dsSalesOrderDetail =  
            new ReportDataSource();  
        dsSalesOrderDetail.Name = "SalesOrderDetail";  
        dsSalesOrderDetail.Value =  
            dataset.Tables["SalesOrderDetail"];  
  
        localReport.DataSources.Add(dsSalesOrderDetail);  
  
        // Create a report parameter for the sales order number   
        ReportParameter rpSalesOrderNumber = new ReportParameter();  
        rpSalesOrderNumber.Name = "SalesOrderNumber";  
        rpSalesOrderNumber.Values.Add("SO43661");  
  
        // Set the report parameters for the report  
        localReport.SetParameters(  
            new ReportParameter[] { rpSalesOrderNumber });  
  
        // Refresh the report  
        reportViewer1.RefreshReport();  
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
}  
```  
  
```vb  
Imports System.Data.SqlClient  
Imports Microsoft.Reporting.WinForms  
  
Public Class Form1  
  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
                        ByVal e As System.EventArgs) _  
                        Handles MyBase.Load  
  
        'Set the processing mode for the ReportViewer to Local  
        reportViewer1.ProcessingMode = ProcessingMode.Local  
  
        Dim localReport As LocalReport  
        localReport = reportViewer1.LocalReport  
  
        localReport.ReportEmbeddedResource = _  
            "ReportViewerIntro.Sales Order Detail.rdlc"  
  
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
  
        'Refresh the report  
        reportViewer1.RefreshReport()  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fd9e3-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd9e3-142">See Also</span></span>  
 [<span data-ttu-id="fd9e3-143">使用 ReportViewer 控制項整合 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="fd9e3-143">Integrating Reporting Services Using the ReportViewer Controls</span></span>](../application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
  
  
