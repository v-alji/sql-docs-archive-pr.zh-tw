---
title: 在應用程式的程式碼中使用 FOR XML 結果 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, application code usage
- XML [SQL Server], FOR XML clause
- ASP.NET [SQL Server]
- .NET Framework [SQL Server], FOR XML data
- ADO [SQL Server]
- XML data islands [SQL Server]
- data islands [SQL Server]
ms.assetid: 41ae67bd-ece9-49ea-8062-c8d658ab4154
author: rothja
ms.author: jroth
ms.openlocfilehash: 3cabe7e65cb53a28a370615ed84e38ba2b8db44c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599387"
---
# <a name="use-for-xml-results-in-application-code"></a><span data-ttu-id="3e574-102">在應用程式的程式碼中使用 FOR XML 結果</span><span class="sxs-lookup"><span data-stu-id="3e574-102">Use FOR XML Results in Application Code</span></span>
  <span data-ttu-id="3e574-103">藉由在 SQL 查詢中使用 FOR XML 子句，您就可以將查詢結果擷取為 XML 資料，以及將其轉換為 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="3e574-103">By using FOR XML clauses with SQL queries, you can retrieve and even cast query results as XML data.</span></span> <span data-ttu-id="3e574-104">如果可以在 XML 應用程式的程式碼中使用 FOR XML 查詢結果，此功能便能讓您執行下列功能：</span><span class="sxs-lookup"><span data-stu-id="3e574-104">This functionality allows you to do the following when FOR XML query results can be used in XML application code:</span></span>  
  
-   <span data-ttu-id="3e574-105">針對 [XML 資料 &#40;SQL Server&#41;](xml-data-sql-server.md) 值的執行個體，查詢 SQL 資料表</span><span class="sxs-lookup"><span data-stu-id="3e574-105">Query SQL tables for instances of [XML Data &#40;SQL Server&#41;](xml-data-sql-server.md) values</span></span>  
  
-   <span data-ttu-id="3e574-106">套用 [TYPE Directive in FOR XML Queries](type-directive-in-for-xml-queries.md) ，以 XML 格式傳回包含文字或影像類型資料的查詢結果</span><span class="sxs-lookup"><span data-stu-id="3e574-106">Apply the [TYPE Directive in FOR XML Queries](type-directive-in-for-xml-queries.md) to return the result of queries that contain text or image typed data as XML</span></span>  
  
 <span data-ttu-id="3e574-107">此主題提供範例來示範這些方式。</span><span class="sxs-lookup"><span data-stu-id="3e574-107">This topic provides examples that demonstrate these approaches.</span></span>  
  
## <a name="retrieving-for-xml-data-with-ado-and-xml-data-islands"></a><span data-ttu-id="3e574-108">以 ADO 和 XML 資料島擷取 FOR XML 資料</span><span class="sxs-lookup"><span data-stu-id="3e574-108">Retrieving FOR XML Data with ADO and XML Data Islands</span></span>  
 <span data-ttu-id="3e574-109">當您使用 FOR XML 查詢時，支援 COM `Stream` 介面的 ADO `IStream` 物件或其他物件，例如 Active Server Pages (ASP) `Request` 和 `Response` 物件，可用來包含結果。</span><span class="sxs-lookup"><span data-stu-id="3e574-109">The ADO `Stream` object or other objects that support the COM `IStream` interface, such as the Active Server Pages (ASP) `Request` and `Response` objects, can be used to contain the results when you are working with FOR XML queries.</span></span>  
  
 <span data-ttu-id="3e574-110">例如，下列 ASP 程式碼顯示在 AdventureWorks 範例資料庫的 Sales.Store 資料表中查詢 `xml` 資料類型資料行 Demographics 的結果。</span><span class="sxs-lookup"><span data-stu-id="3e574-110">For example, the following ASP code shows the results of querying an `xml` data type column, Demographics, in the Sales.Store table of the AdventureWorks sample database.</span></span> <span data-ttu-id="3e574-111">該查詢尤其會在此資料行的執行個體值中尋找 CustomerID 等於 3 的資料列。</span><span class="sxs-lookup"><span data-stu-id="3e574-111">Specifically, the query looks for the instance value of this column for the row where the CustomerID is equal to 3.</span></span>  
  
```  
<!-- BeginRecordAndStreamVBS -->  
<%@ LANGUAGE = VBScript %>  
<!-- %  Option Explicit      % -->  
<!-- 'Request.ServerVariables("SERVER_NAME") & ";" & _ -->  
<HTML>  
<HEAD>  
<META NAME="GENERATOR" Content="Microsoft Developer Studio"/>  
<META HTTP-EQUIV="Content-Type" content="text/html"; charset="iso-8859-1">  
<TITLE>FOR XML Query Example</TITLE>  
<STYLE>  
   BODY  
   {  
      FONT-FAMILY: Tahoma;  
      FONT-SIZE: 8pt;  
      OVERFLOW: auto  
   }  
   H3  
   {  
      FONT-FAMILY: Tahoma;  
      FONT-SIZE: 8pt;  
      OVERFLOW: auto  
   }  
</STYLE>  
  
<!-- #include file="adovbs.inc" -->  
<%  
   Response.Write "<H3>Server-side processing</H3>"  
   Response.Write "Page Generated @ " & Now() & "<BR/>"  
   Dim adoConn  
   Set adoConn = Server.CreateObject("ADODB.Connection")  
   Dim sConn  
   sConn = "Provider=SQLOLEDB;Data Source=(local);" & _  
            "Initial Catalog=AdventureWorks;Integrated Security=SSPI;"  
   Response.write "Connect String = " & sConn & "<BR/>"  
   adoConn.ConnectionString = sConn  
   adoConn.CursorLocation = adUseClient  
   adoConn.Open  
   Response.write "ADO Version = " & adoConn.Version & "<BR/>"  
   Response.write "adoConn.State = " & adoConn.State & "<BR/>"  
   Dim adoCmd  
   Set adoCmd = Server.CreateObject("ADODB.Command")  
   Set adoCmd.ActiveConnection = adoConn  
   Dim sQuery  
   sQuery = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'><sql:query>SELECT Demographics from Sales.Store WHERE CustomerID = 3 FOR XML AUTO</sql:query></ROOT>"  
   Response.write "Query String = " & sQuery & "<BR/>"  
   Dim adoStreamQuery  
   Set adoStreamQuery = Server.CreateObject("ADODB.Stream")  
   adoStreamQuery.Open  
   adoStreamQuery.WriteText sQuery, adWriteChar  
   adoStreamQuery.Position = 0  
   adoCmd.CommandStream = adoStreamQuery  
   adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"  
   Response.write "Pushing XML to client for processing "  & "<BR/>"  
   adoCmd.Properties("Output Stream") = Response  
   Response.write "<XML ID='MyDataIsle'>"  
   adoCmd.Execute , , 1024  
   Response.write "</XML>"  
%>  
<SCRIPT language="VBScript" For="window" Event="onload">  
   Dim xmlDoc  
   Set xmlDoc = MyDataIsle.XMLDocument  
   Dim root  
   Set root = xmlDoc.documentElement.childNodes.Item(0).childNodes.Item(0).childNodes.Item(0)  
   For each child in root.childNodes  
      dim OutputXML  
      OutputXML = document.all("log").innerHTML  
      document.all("log").innerHTML = OutputXML & "<LI><B>" & child.nodeName &  ":</B>  " & child.Text  & "</LI>"  
   Next  
   MsgBox xmlDoc.xml  
</SCRIPT>  
</HEAD>  
<BODY>  
   <H3>Client-side processing of XML Document MyDataIsle</H3>  
   <UL id=log>  
   </UL>  
</BODY>  
</HTML>  
<!-- EndRecordAndStreamVBS -->  
```  
  
 <span data-ttu-id="3e574-112">此範例 ASP 頁面包含伺服器端 VBScript，它使用 ADO 來執行 FOR XML 查詢，並在 XML 資料島 MyDataIsle 內傳回 XML 結果。</span><span class="sxs-lookup"><span data-stu-id="3e574-112">This example ASP page contains server-side VBScript that uses ADO to execute the FOR XML query and return the XML results in an XML data island, MyDataIsle.</span></span> <span data-ttu-id="3e574-113">然後此 XML 資料島會傳回瀏覽器中，以進行其他用戶端處理。</span><span class="sxs-lookup"><span data-stu-id="3e574-113">This XML data island is then returned in the browser for additional client-side processing.</span></span> <span data-ttu-id="3e574-114">接著，會使用其他用戶端 VBScript 程式碼來處理 XML 資料島的內容。</span><span class="sxs-lookup"><span data-stu-id="3e574-114">Additional client-side VBScript code is then used to process the contents of the XML data island.</span></span> <span data-ttu-id="3e574-115">執行此程序之後，才會將內容顯示為結果 DHTML 的一部份，並開啟訊息方塊來顯示 XML 資料島之預先處理過的內容。</span><span class="sxs-lookup"><span data-stu-id="3e574-115">This process is performed before displaying the contents as part of the resultant DHTML and opening a message box to show the preprocessed contents of the XML data island.</span></span>  
  
#### <a name="to-test-this-example"></a><span data-ttu-id="3e574-116">若要測試此範例</span><span class="sxs-lookup"><span data-stu-id="3e574-116">To test this example</span></span>  
  
1.  <span data-ttu-id="3e574-117">確認已安裝 IIS，而且也為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝了 AdventureWorks 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="3e574-117">Verify that IIS is installed and that the AdventureWorks sample database for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been installed.</span></span>  
  
     <span data-ttu-id="3e574-118">此範例需要安裝 Internet Information Services (IIS) 5.0 版或更新版本，並已啟用 ASP 支援。</span><span class="sxs-lookup"><span data-stu-id="3e574-118">This example requires that Internet Information Services (IIS) version 5.0, or later versions, are installed with ASP support enabled.</span></span> <span data-ttu-id="3e574-119">同時，也必須安裝 AdventureWorks 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="3e574-119">Also, the AdventureWorks sample database has to be installed.</span></span>  
  
2.  <span data-ttu-id="3e574-120">複製先前提供的程式碼範例，並將它貼到 XML 或您使用的文字編輯器中。</span><span class="sxs-lookup"><span data-stu-id="3e574-120">Copy the code example that was previously provided and paste it into the XML or text editor that you use.</span></span> <span data-ttu-id="3e574-121">以 RetrieveResults.asp 的名稱，將檔案另存於 IIS 使用的根目錄中。</span><span class="sxs-lookup"><span data-stu-id="3e574-121">Save the file as RetrieveResults.asp in the root directory that is used for IIS.</span></span> <span data-ttu-id="3e574-122">此目錄通常是 C:Inetpub\wwwroot。</span><span class="sxs-lookup"><span data-stu-id="3e574-122">Typically, this is C:Inetpub\wwwroot.</span></span>  
  
3.  <span data-ttu-id="3e574-123">使用下列 URL，在瀏覽器視窗中開啟 ASP 頁面。</span><span class="sxs-lookup"><span data-stu-id="3e574-123">Open the ASP page in a browser window by using the following URL.</span></span> <span data-ttu-id="3e574-124">首先，將 'MyServer' 取代成 "localhost" 或安裝了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 IIS 之伺服器的實際名稱。</span><span class="sxs-lookup"><span data-stu-id="3e574-124">First, replace 'MyServer' with either "localhost" or the actual name of the server where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and IIS are installed.</span></span>  
  
    ```  
    http://MyServer/RetrieveResults.asp  
    ```  
  
 <span data-ttu-id="3e574-125">產生的 HTML 頁面結果類似下列範例輸出：</span><span class="sxs-lookup"><span data-stu-id="3e574-125">The generated HTML page results that appear will be similar to the following sample output:</span></span>  
  
##### <a name="server-side-processing"></a><span data-ttu-id="3e574-126">伺服器端處理</span><span class="sxs-lookup"><span data-stu-id="3e574-126">Server-side processing</span></span>  
 <span data-ttu-id="3e574-127">Page Generated \@ 3/11/2006 3:36:02 PM</span><span class="sxs-lookup"><span data-stu-id="3e574-127">Page Generated \@ 3/11/2006 3:36:02 PM</span></span>  
  
 <span data-ttu-id="3e574-128">Connect String = Provider=SQLOLEDB;Data Source=MyServer;Initial Catalog=AdventureWorks;Integrated Security=SSPI;</span><span class="sxs-lookup"><span data-stu-id="3e574-128">Connect String = Provider=SQLOLEDB;Data Source=MyServer;Initial Catalog=AdventureWorks;Integrated Security=SSPI;</span></span>  
  
 <span data-ttu-id="3e574-129">ADO Version = 2.8</span><span class="sxs-lookup"><span data-stu-id="3e574-129">ADO Version = 2.8</span></span>  
  
 <span data-ttu-id="3e574-130">adoConn.State = 1</span><span class="sxs-lookup"><span data-stu-id="3e574-130">adoConn.State = 1</span></span>  
  
 <span data-ttu-id="3e574-131">Query String = SELECT Demographics from Sales.Store WHERE CustomerID = 3 FOR XML AUTO</span><span class="sxs-lookup"><span data-stu-id="3e574-131">Query String = SELECT Demographics from Sales.Store WHERE CustomerID = 3 FOR XML AUTO</span></span>  
  
 <span data-ttu-id="3e574-132">將 XML 發送至用戶端進行處理</span><span class="sxs-lookup"><span data-stu-id="3e574-132">Pushing XML to client for processing</span></span>  
  
##### <a name="client-side-processing-of-xml-document-mydataisle"></a><span data-ttu-id="3e574-133">XML 文件 MyDataIsle 的用戶端處理</span><span class="sxs-lookup"><span data-stu-id="3e574-133">Client-side processing of XML Document MyDataIsle</span></span>  
  
-   <span data-ttu-id="3e574-134">**AnnualSales：** 1500000</span><span class="sxs-lookup"><span data-stu-id="3e574-134">**AnnualSales:** 1500000</span></span>  
  
-   <span data-ttu-id="3e574-135">**AnnualRevenue：** 150000</span><span class="sxs-lookup"><span data-stu-id="3e574-135">**AnnualRevenue:** 150000</span></span>  
  
-   <span data-ttu-id="3e574-136">**BankName：** Primary International</span><span class="sxs-lookup"><span data-stu-id="3e574-136">**BankName:** Primary International</span></span>  
  
-   <span data-ttu-id="3e574-137">**BusinessType：** OS</span><span class="sxs-lookup"><span data-stu-id="3e574-137">**BusinessType:** OS</span></span>  
  
-   <span data-ttu-id="3e574-138">**YearOpened：** 1974</span><span class="sxs-lookup"><span data-stu-id="3e574-138">**YearOpened:** 1974</span></span>  
  
-   <span data-ttu-id="3e574-139">**Specialty：** 路段</span><span class="sxs-lookup"><span data-stu-id="3e574-139">**Specialty:** Road</span></span>  
  
-   <span data-ttu-id="3e574-140">**SquareFeet：** 38000</span><span class="sxs-lookup"><span data-stu-id="3e574-140">**SquareFeet:** 38000</span></span>  
  
-   <span data-ttu-id="3e574-141">**Brands：** 3</span><span class="sxs-lookup"><span data-stu-id="3e574-141">**Brands:** 3</span></span>  
  
-   <span data-ttu-id="3e574-142">**Internet：** DSL</span><span class="sxs-lookup"><span data-stu-id="3e574-142">**Internet:** DSL</span></span>  
  
-   <span data-ttu-id="3e574-143">**NumberEmployees：** 40</span><span class="sxs-lookup"><span data-stu-id="3e574-143">**NumberEmployees:** 40</span></span>  
  
 <span data-ttu-id="3e574-144">VBScript 訊息方塊會顯示下列由 FOR XML 查詢結果所傳回之原始而未篩選過的 XML 資料島內容。</span><span class="sxs-lookup"><span data-stu-id="3e574-144">The VBScript message box will then show the following original, unfiltered XML data island contents that were returned by the FOR XML query results.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Sales.Store>  
    <Demographics>  
      <StoreSurvey xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
        <AnnualSales>1500000</AnnualSales>  
        <AnnualRevenue>150000</AnnualRevenue>  
        <BankName>Primary International</BankName>  
        <BusinessType>OS</BusinessType>  
        <YearOpened>1974</YearOpened>  
        <Specialty>Road</Specialty>  
        <SquareFeet>38000</SquareFeet>  
        <Brands>3</Brands>  
        <Internet>DSL</Internet>  
        <NumberEmployees>40</NumberEmployees>  
      </StoreSurvey>  
    </Demographics>  
  </Sales.Store>  
</ROOT>  
```  
  
## <a name="retrieving-for-xml-data-with-aspnet-and-the-net-framework"></a><span data-ttu-id="3e574-145">使用 ASP.NET 和 .NET Framework 來擷取 FOR XML 資料</span><span class="sxs-lookup"><span data-stu-id="3e574-145">Retrieving FOR XML Data with ASP.NET and the .NET Framework</span></span>  
 <span data-ttu-id="3e574-146">如前一範例所示，下列 ASP.NET 程式碼顯示在 AdventureWorks 範例資料庫的 Sales.Store 資料表中查詢 `xml` 資料類型資料行 Demographics 的結果。</span><span class="sxs-lookup"><span data-stu-id="3e574-146">As in the previous example, the following ASP.NET code shows the results of querying an `xml` data type column, Demographics, in the Sales.Store table of the AdventureWorks sample database.</span></span> <span data-ttu-id="3e574-147">如前一範例所示，此查詢會在此資料行的執行個體值中尋找 CustomerID 等於 3 的資料列。</span><span class="sxs-lookup"><span data-stu-id="3e574-147">As in the previous example, the query looks for the instance value of this column for the row where the CustomerID is equal to 3.</span></span>  
  
 <span data-ttu-id="3e574-148">在此範例中，使用了下列 Microsoft .NET Framework 管理的 API 來完成 FOR XML 查詢結果的傳回和轉譯作業：</span><span class="sxs-lookup"><span data-stu-id="3e574-148">In this example, the following Microsoft .NET Framework managed APIs are used to accomplish the return and rendering of the FOR XML query results:</span></span>  
  
1.  <span data-ttu-id="3e574-149">`SqlConnection` 用來開啟 SQL Server 的連接，並以指定之連接字串變數 strConn 的內容為基礎。</span><span class="sxs-lookup"><span data-stu-id="3e574-149">`SqlConnection` is used to open a connection to SQL Server, based on the contents of a specified connection string variable, strConn.</span></span>  
  
2.  <span data-ttu-id="3e574-150">`SqlDataAdapter` 則做為資料配接器使用，它使用 SQL 連接和指定的 SQL 查詢字串來執行 FOR XML 查詢。</span><span class="sxs-lookup"><span data-stu-id="3e574-150">`SqlDataAdapter` is then used as the data adapter and it uses the SQL connection and a specified SQL query string to execute the FOR XML query.</span></span>  
  
3.  <span data-ttu-id="3e574-151">執行查詢之後，會呼叫 `SqlDataAdapter.Fill` 方法，並傳遞 `DataSet,` 的執行個體 (MyDataSet)，以便在資料集內填入 FOR XML 查詢的輸出。</span><span class="sxs-lookup"><span data-stu-id="3e574-151">After the query has executed, the `SqlDataAdapter.Fill` method is then called and passed an instance of a `DataSet,` MyDataSet, in order to fill the data set with the output of the FOR XML query.</span></span>  
  
4.  <span data-ttu-id="3e574-152">接著會呼叫 `DataSet.GetXml` 方法，將查詢結果當作可在伺服器所產生 HTML 頁面中顯示的字串，予以傳回。</span><span class="sxs-lookup"><span data-stu-id="3e574-152">The `DataSet.GetXml` method is then called to return the query results as a string that can be displayed in the server-generated HTML page.</span></span>  
  
    ```  
    <%@ Page Language="VB" %>  
    <HTML>  
    <HEAD>  
    <TITLE>FOR XML Query Example</TITLE>  
    <STYLE>  
       BODY  
       {  
          FONT-FAMILY: Tahoma;  
          FONT-SIZE: 8pt;  
          OVERFLOW: auto  
       }  
       H3  
       {  
          FONT-FAMILY: Tahoma;  
          FONT-SIZE: 8pt;  
          OVERFLOW: auto  
       }  
    </STYLE>  
    </HEAD>  
    <BODY>  
    <%  
    Dim s as String  
    s = "<H3>Server-side processing</H3>" & _  
        "Page Generated @ " & Now() & "<BR/>"  
  
    Dim SQL As String   
    SQL = "SELECT Demographics from Sales.Store WHERE CustomerID = 3 FOR XML AUTO"  
  
    Dim strConn As String   
    strConn = "Server=(local);Database=AdventureWorks;Integrated Security=SSPI;"  
  
    Dim MySqlConn As New System.Data.SqlClient.SqlConnection(strConn)  
    Dim MySqlAdapter As New System.Data.SqlClient.SqlDataAdapter(SQL,MySqlConn)  
    Dim MyDataSet As New System.Data.DataSet  
  
    MySqlConn.Open()  
    s = s & "<P>SqlConnection opened.</P>"   
  
    MySqlAdapter.Fill(MyDataSet)  
    s = s & "<P>" & MyDataSet.GetXml  & "</P>"  
  
    MySqlConn.Close()  
    s = s & "<P>SqlConnection closed.</P>"   
  
    Message.InnerHtml=s  
    %>  
    <SPAN id="Message" runat=server />  
    </BODY>  
    </HTML>  
    ```  
  
#### <a name="to-test-this-example"></a><span data-ttu-id="3e574-153">若要測試此範例</span><span class="sxs-lookup"><span data-stu-id="3e574-153">To test this example</span></span>  
  
1.  <span data-ttu-id="3e574-154">確認已安裝 IIS，而且也為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝了 AdventureWorks 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="3e574-154">Verify that IIS is installed and that the AdventureWorks sample database for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been installed.</span></span>  
  
     <span data-ttu-id="3e574-155">此範例需要安裝 Internet Information Services (IIS) 5.0 版或更新版本，並已啟用 ASP.NET 支援。</span><span class="sxs-lookup"><span data-stu-id="3e574-155">This example requires that Internet Information Services (IIS) version 5.0, or later versions, are installed with ASP.NET support enabled.</span></span> <span data-ttu-id="3e574-156">同時，也必須安裝 AdventureWorks 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="3e574-156">Also, the AdventureWorks sample database has to be installed.</span></span>  
  
2.  <span data-ttu-id="3e574-157">複製先前提供的程式碼，並將它貼到 XML 或您使用的文字編輯器中。</span><span class="sxs-lookup"><span data-stu-id="3e574-157">Copy the code that was previously provided and paste it into the XML or text editor that you use.</span></span> <span data-ttu-id="3e574-158">以 RetrieveResults.asp 的名稱，將檔案另存於 IIS 使用的根目錄中。</span><span class="sxs-lookup"><span data-stu-id="3e574-158">Save the file as RetrieveResults.aspx in the root directory used for IIS.</span></span> <span data-ttu-id="3e574-159">此目錄通常是 C:Inetpub\wwwroot。</span><span class="sxs-lookup"><span data-stu-id="3e574-159">Typically, this is C:Inetpub\wwwroot.</span></span>  
  
3.  <span data-ttu-id="3e574-160">使用下列 URL，在瀏覽器視窗中開啟 ASP.NET 頁面。</span><span class="sxs-lookup"><span data-stu-id="3e574-160">Open the ASP.NET page in a browser window using the following URL.</span></span> <span data-ttu-id="3e574-161">首先，將 'MyServer' 取代成 "localhost" 或安裝了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 IIS 之伺服器的實際名稱。</span><span class="sxs-lookup"><span data-stu-id="3e574-161">First, replace 'MyServer' with either "localhost" or the actual name of the server where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and IIS are installed.</span></span>  
  
    ```  
    http://MyServer/RetrieveResults.aspx  
    ```  
  
 <span data-ttu-id="3e574-162">產生的 HTML 頁面結果類似下列範例輸出：</span><span class="sxs-lookup"><span data-stu-id="3e574-162">The generated HTML page results that appear will be similar to the following sample output:</span></span>  
  
##### <a name="server-side-processing"></a><span data-ttu-id="3e574-163">伺服器端處理</span><span class="sxs-lookup"><span data-stu-id="3e574-163">Server-side processing</span></span>  
  
```  
Page Generated @ 3/11/2006 3:36:02 PM  
  
SqlConnection opened.  
  
<Sales.Store><Demographics><StoreSurvey xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey"><AnnualSales>1500000</AnnualSales><AnnualRevenue>150000</AnnualRevenue><BankName>Primary International</BankName><BusinessType>OS</BusinessType><YearOpened>1974</YearOpened><Specialty>Road</Specialty><SquareFeet>38000</SquareFeet><Brands>3</Brands><Internet>DSL</Internet><NumberEmployees>40</NumberEmployees></StoreSurvey></Demographics></Sales.Store>  
  
SqlConnection closed.  
```  
  
> [!NOTE]  
>  <span data-ttu-id="3e574-164">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `xml` 資料類型支援可讓您藉由指定 type 指示詞，要求以資料類型傳回 FOR XML 查詢的結果 `xml` ，而不是字串或影像類型資料。 [TYPE directive](type-directive-in-for-xml-queries.md)</span><span class="sxs-lookup"><span data-stu-id="3e574-164">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`xml` data type support lets you request that the result of a FOR XML query be returned as `xml` data type, instead of as string or image typed data, by specifying the [TYPE directive](type-directive-in-for-xml-queries.md).</span></span> <span data-ttu-id="3e574-165">如果在 FOR XML 查詢中使用了 TYPE 指示詞時，它會提供以程式方式存取 FOR XML 結果 (類似 [在應用程式中使用 XML 資料](use-xml-data-in-applications.md)中所顯示)。</span><span class="sxs-lookup"><span data-stu-id="3e574-165">When the TYPE directive is used in FOR XML queries, it provides programmatic access to the FOR XML results similar to that shown in [Use XML Data in Applications](use-xml-data-in-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e574-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e574-166">See Also</span></span>  
 [<span data-ttu-id="3e574-167">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3e574-167">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
