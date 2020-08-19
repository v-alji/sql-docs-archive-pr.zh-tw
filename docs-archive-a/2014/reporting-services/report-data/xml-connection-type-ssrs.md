---
title: XML 連線類型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5b55fff2-1b15-4156-83ef-15ad9cf9f509
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 141f6449e0493ba7a12e9270bedab967b7795ee0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707174"
---
# <a name="xml-connection-type-ssrs"></a><span data-ttu-id="66fb0-102">XML 連接類型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="66fb0-102">XML Connection Type (SSRS)</span></span>
  <span data-ttu-id="66fb0-103">若要在報表中包含來自 XML 資料來源的資料，您必須具有以 XML 類型之報表資料來源為基礎的資料集。</span><span class="sxs-lookup"><span data-stu-id="66fb0-103">To include data from an XML data source in your report, you must have a dataset that is based on a report data source of type XML.</span></span> <span data-ttu-id="66fb0-104">此內建資料來源類型是以 XML 資料延伸模組為基礎。</span><span class="sxs-lookup"><span data-stu-id="66fb0-104">This built-in data source type is based on the XML data extension.</span></span> <span data-ttu-id="66fb0-105">請使用此資料來源類型連接至 XML 文件、Web 服務或內嵌在查詢中的 XML，並從中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="66fb0-105">Use this data source type to connect to and retrieve data from XML documents, Web services, or XML that is embedded in the query.</span></span>  
  
 <span data-ttu-id="66fb0-106">此資料延伸模組支援與連接字串分開管理的參數和認證。</span><span class="sxs-lookup"><span data-stu-id="66fb0-106">This data extension supports parameters and credentials managed separately from the connection string.</span></span>  
  
 <span data-ttu-id="66fb0-107">您可以使用本主題中的資訊來建置資料來源。</span><span class="sxs-lookup"><span data-stu-id="66fb0-107">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="66fb0-108">如需逐步指示，請參閱 [加入及驗證資料連線或資料來源 &#40;Report Builder 和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="66fb0-108">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="66fb0-109">連接字串</span><span class="sxs-lookup"><span data-stu-id="66fb0-109">Connection String</span></span>  
 <span data-ttu-id="66fb0-110">連接字串必須是指向 Web 服務、網路架構應用程式或可透過 HTTP 使用之 XML 文件的 URL；</span><span class="sxs-lookup"><span data-stu-id="66fb0-110">The connection string must be a URL that points to the Web service, Web-based application, or XML document available through HTTP.</span></span> <span data-ttu-id="66fb0-111">XML 文件的副檔名必須是 XML。</span><span class="sxs-lookup"><span data-stu-id="66fb0-111">XML documents must have the XML extension.</span></span> <span data-ttu-id="66fb0-112">您也可以針對內嵌在資料集查詢中的 XML 資料使用空的連接字串。</span><span class="sxs-lookup"><span data-stu-id="66fb0-112">You can also use an empty connection string for XML data embedded in the dataset query.</span></span>  
  
 <span data-ttu-id="66fb0-113">下列範例分別說明 Web 服務和 XML 文件的連接字串語法。</span><span class="sxs-lookup"><span data-stu-id="66fb0-113">The following examples illustrate the connection string syntax for a Web service and XML document, respectively.</span></span> <span data-ttu-id="66fb0-114">不支援 `file://` 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="66fb0-114">The `file://` protocol is not supported.</span></span>  
  
|<span data-ttu-id="66fb0-115">XML 文件類型</span><span class="sxs-lookup"><span data-stu-id="66fb0-115">XML document type</span></span>|<span data-ttu-id="66fb0-116">連接字串範例</span><span class="sxs-lookup"><span data-stu-id="66fb0-116">Connection String Example</span></span>|  
|-----------------------|-------------------------------|  
|<span data-ttu-id="66fb0-117">Web 服務</span><span class="sxs-lookup"><span data-stu-id="66fb0-117">Web service</span></span>|`http://adventure-works.com/results.aspx`|  
|<span data-ttu-id="66fb0-118">XML 文件</span><span class="sxs-lookup"><span data-stu-id="66fb0-118">XML document</span></span>|`http://localhost/XML/Customers.xml`|  
|<span data-ttu-id="66fb0-119">內嵌 XML 文件</span><span class="sxs-lookup"><span data-stu-id="66fb0-119">Embedded XML document</span></span>|<span data-ttu-id="66fb0-120">*Empty*</span><span class="sxs-lookup"><span data-stu-id="66fb0-120">*Empty*</span></span>|  
  
 <span data-ttu-id="66fb0-121">如需更多連接字串範例，請參閱 [報表產生器中的資料連接、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="66fb0-121">For more connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="66fb0-122">認證</span><span class="sxs-lookup"><span data-stu-id="66fb0-122">Credentials</span></span>  
 <span data-ttu-id="66fb0-123">需要有認證才能夠執行報表、於本機預覽報表並且從報表伺服器預覽報表。</span><span class="sxs-lookup"><span data-stu-id="66fb0-123">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="66fb0-124">發行報表之後，您可能需要變更資料來源的認證，如此當報表在報表伺服器上執行時，擷取資料的權限就會是有效的。</span><span class="sxs-lookup"><span data-stu-id="66fb0-124">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="66fb0-125">報表撰寫用戶端提供下列可用來指定認證的選項：</span><span class="sxs-lookup"><span data-stu-id="66fb0-125">From a report authoring client, the following options are available to specify credentials:</span></span>  
  
-   <span data-ttu-id="66fb0-126">目前的 Windows 使用者 (也稱為整合式安全性)。</span><span class="sxs-lookup"><span data-stu-id="66fb0-126">Current Windows user (also known as integrated security).</span></span>  
  
-   <span data-ttu-id="66fb0-127">不需要認證。</span><span class="sxs-lookup"><span data-stu-id="66fb0-127">No credentials are required.</span></span> <span data-ttu-id="66fb0-128">如果您未選取認證，則會使用匿名存取。</span><span class="sxs-lookup"><span data-stu-id="66fb0-128">If you select no credentials, Anonymous access is used.</span></span> <span data-ttu-id="66fb0-129">請確定您已為報表伺服器定義自動執行帳戶，以連接到外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="66fb0-129">Make sure that you have defined the unattended execution account for the report server to connect to an external data source.</span></span> <span data-ttu-id="66fb0-130">XML 資料處理延伸模組不會將認證傳遞到目標 URL 或 Web 服務。除非您已定義自動執行帳戶，否則連接不會成功。</span><span class="sxs-lookup"><span data-stu-id="66fb0-130">The XML data processing extension does not pass credentials to the target URL or the Web service; the connection will be unsuccessful unless you have defined the unattended execution account.</span></span> <span data-ttu-id="66fb0-131">如需詳細資訊，請參閱 msdn.microsoft.com 上《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [線上叢書](https://go.microsoft.com/fwlink/?linkid=121312)》中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文件的[設定自動執行帳戶 &#40;SSRS 設定管理員&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="66fb0-131">For more information, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="66fb0-132">不支援預存認證和提示認證。</span><span class="sxs-lookup"><span data-stu-id="66fb0-132">Stored and prompted credentials are not supported.</span></span> <span data-ttu-id="66fb0-133">請記住，如果您停用 Windows 整合式安全性，您就無法利用它擷取資料。</span><span class="sxs-lookup"><span data-stu-id="66fb0-133">Remember that if you disable Windows integrated security, you cannot use it to retrieve data.</span></span> <span data-ttu-id="66fb0-134">如果您指定預存認證或提示認證，執行階段中將會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="66fb0-134">If you specify stored or prompted credentials, an error will occur at run time.</span></span>  
  
 <span data-ttu-id="66fb0-135">如需詳細資訊，請參閱 [Reporting Services 中的資料連線、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) ，或 [在 Report Builder 中指定認證](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="66fb0-135">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
##  <a name="queries"></a><a name="Query"></a> <span data-ttu-id="66fb0-136">查詢</span><span class="sxs-lookup"><span data-stu-id="66fb0-136">Queries</span></span>  
 <span data-ttu-id="66fb0-137">查詢會指定要為報表資料集擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="66fb0-137">A query specifies which data to retrieve for a report dataset.</span></span> <span data-ttu-id="66fb0-138">查詢結果集中的資料行會填入資料集的欄位集合。</span><span class="sxs-lookup"><span data-stu-id="66fb0-138">The columns in the result set for a query populate the field collection for a dataset.</span></span> <span data-ttu-id="66fb0-139">報表只會處理查詢所擷取的第一個結果集。</span><span class="sxs-lookup"><span data-stu-id="66fb0-139">A report processes only the first result set retrieved by a query.</span></span>  
  
 <span data-ttu-id="66fb0-140">您必須使用以文字為基礎的查詢設計工具來建立查詢；</span><span class="sxs-lookup"><span data-stu-id="66fb0-140">You must use the text-based query designer to create the query.</span></span> <span data-ttu-id="66fb0-141">查詢必須傳回 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="66fb0-141">The query must return XML data.</span></span>  
  
 <span data-ttu-id="66fb0-142">如需以文字為基礎之查詢設計工具的詳細資訊，請參閱[以文字為基礎的查詢設計工具使用者介面 &#40;報表產生器&#41;](text-based-query-designer-user-interface-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="66fb0-142">For more information about the text-based query designer, see [Text-based Query Designer User Interface &#40;Report Builder&#41;](text-based-query-designer-user-interface-report-builder.md).</span></span>  
  
 <span data-ttu-id="66fb0-143">以下為資料來源為 XML 類型時，資料集查詢的可能值。</span><span class="sxs-lookup"><span data-stu-id="66fb0-143">The possible values for a dataset query for a data source that is type XML are shown below.</span></span>  
  
-   <span data-ttu-id="66fb0-144">*空白*：使用空白查詢來建立預設結果集。</span><span class="sxs-lookup"><span data-stu-id="66fb0-144">*Empty*: Use an empty query to create a default result set.</span></span> <span data-ttu-id="66fb0-145">預設查詢的建立方式，是藉由讀取資料來源，並周遊到 XML 節點階層中的第一個分葉集合。</span><span class="sxs-lookup"><span data-stu-id="66fb0-145">The default query is created by reading the data source and traversing the XML node hierarchy to the first leaf collection.</span></span> <span data-ttu-id="66fb0-146">結果集會包含所有節點，連同該路徑上的文字值和所有節點屬性；</span><span class="sxs-lookup"><span data-stu-id="66fb0-146">The result set includes all nodes with text values and all node attributes along that path.</span></span> <span data-ttu-id="66fb0-147">結果集內的資料行會對應到資料集的欄位。</span><span class="sxs-lookup"><span data-stu-id="66fb0-147">Columns in the result set are mapped to fields for the dataset.</span></span>  
  
-   <span data-ttu-id="66fb0-148">專案路徑：指定從資料來源抓取 XML 資料時，要使用的節點順序。</span><span class="sxs-lookup"><span data-stu-id="66fb0-148">An element path: Specifies the sequence of nodes to use when retrieving XML data from the data source.</span></span>  
  
-   <span data-ttu-id="66fb0-149">XML 查詢元素：具有下列選擇性元素的 XML 查詢規格：</span><span class="sxs-lookup"><span data-stu-id="66fb0-149">An XML Query element: An XML query specification with the following optional elements:</span></span>  
  
    -   <span data-ttu-id="66fb0-150">**針對 Web 服務：**</span><span class="sxs-lookup"><span data-stu-id="66fb0-150">**For a Web service:**</span></span>  
  
         <span data-ttu-id="66fb0-151">必要的 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="66fb0-151">Required XML Elements:</span></span>  
  
         <span data-ttu-id="66fb0-152">`<Method Namespace=` "命名空間" `Name="MethodName" />`</span><span class="sxs-lookup"><span data-stu-id="66fb0-152">`<Method Namespace=` *"namespace"*  `Name="MethodName" />`</span></span>  
  
         `-- or --`  
  
         <span data-ttu-id="66fb0-153">`<SoapAction>` soap 動作 `</SoapAction>`</span><span class="sxs-lookup"><span data-stu-id="66fb0-153">`<SoapAction>` *soap action* `</SoapAction>`</span></span>  
  
         <span data-ttu-id="66fb0-154">選擇性 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="66fb0-154">Optional XML Elements:</span></span>  
  
         <span data-ttu-id="66fb0-155">`<ElementPath>` 元素路徑 `</ElementPath>`</span><span class="sxs-lookup"><span data-stu-id="66fb0-155">`<ElementPath>`  *element path*  `</ElementPath>`</span></span>  
  
         <span data-ttu-id="66fb0-156">`<Method Namespace=` "命名空間" `Name="MethodName" />`</span><span class="sxs-lookup"><span data-stu-id="66fb0-156">`<Method Namespace=` *"namespace"*  `Name="MethodName" />`</span></span>  
  
         `-- or --`  
  
         <span data-ttu-id="66fb0-157">`<SoapAction>` soap 動作 `</SoapAction>`</span><span class="sxs-lookup"><span data-stu-id="66fb0-157">`<SoapAction>` *soap action* `</SoapAction>`</span></span>  
  
    -   <span data-ttu-id="66fb0-158">**若為 XML 檔：**</span><span class="sxs-lookup"><span data-stu-id="66fb0-158">**For an XML document:**</span></span>  
  
         <span data-ttu-id="66fb0-159">選擇性 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="66fb0-159">Optional XML Elements:</span></span>  
  
         <span data-ttu-id="66fb0-160">`<ElementPath>` 元素路徑 `</ElementPath>`</span><span class="sxs-lookup"><span data-stu-id="66fb0-160">`<ElementPath>`  *element path*  `</ElementPath>`</span></span>  
  
    -   <span data-ttu-id="66fb0-161">**針對內嵌的 XML 檔：**</span><span class="sxs-lookup"><span data-stu-id="66fb0-161">**For an embedded XML document:**</span></span>  
  
         <span data-ttu-id="66fb0-162">必要的 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="66fb0-162">Required XML Elements:</span></span>  
  
         <span data-ttu-id="66fb0-163">`<XmlData>` 內部 XML `</XmlData>`</span><span class="sxs-lookup"><span data-stu-id="66fb0-163">`<XmlData>` inner XML `</XmlData>`</span></span>  
  
         <span data-ttu-id="66fb0-164">選擇性 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="66fb0-164">Optional XML Elements:</span></span>  
  
         <span data-ttu-id="66fb0-165">`<ElementPath>` 元素路徑 `</ElementPath>`</span><span class="sxs-lookup"><span data-stu-id="66fb0-165">`<ElementPath>`  *element path*  `</ElementPath>`</span></span>  
  
         `-- or --`  
  
         <span data-ttu-id="66fb0-166">`<ElementPath IgnoreNamespaces="true">` 元素路徑 `</ElementPath>`</span><span class="sxs-lookup"><span data-stu-id="66fb0-166">`<ElementPath IgnoreNamespaces="true">`  *element path*  `</ElementPath>`</span></span>  
  
 <span data-ttu-id="66fb0-167">如需查詢語法的詳細資訊，請參閱 msdn.microsoft.com 上《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [線上叢書](https://go.microsoft.com/fwlink/?linkid=121312)》中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文件的 [XML 報表資料的 XML 查詢語法 &#40;SSRS&#41;](report-data-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="66fb0-167">For more information about query syntax, see [XML Query Syntax for XML Report Data &#40;SSRS&#41;](report-data-ssrs.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="66fb0-168">如需範例，請參閱 [Reporting Services:Using XML and Web Service Data Sources](https://go.microsoft.com/fwlink/?LinkId=81654) (Reporting Services：使用 XML 與 Web 服務資料來源)。</span><span class="sxs-lookup"><span data-stu-id="66fb0-168">For examples, see [Reporting Services: Using XML and Web Service Data Sources](https://go.microsoft.com/fwlink/?LinkId=81654).</span></span>  
  
### <a name="requirements-for-retrieving-xml-web-service-data"></a><span data-ttu-id="66fb0-169">擷取 XML Web 服務資料的需求</span><span class="sxs-lookup"><span data-stu-id="66fb0-169">Requirements for Retrieving XML Web Service Data</span></span>  
 <span data-ttu-id="66fb0-170">XML 資料處理延伸模組不會為您偵測結構描述。</span><span class="sxs-lookup"><span data-stu-id="66fb0-170">The XML data processing extension does not detect the schema for you.</span></span> <span data-ttu-id="66fb0-171">因此，您必須有某個方式可以探索哪些 SOAP 方法將擷取您想要的資料，</span><span class="sxs-lookup"><span data-stu-id="66fb0-171">Therefore, you must have some way of discovering which SOAP methods will retrieve the data that you want.</span></span> <span data-ttu-id="66fb0-172">您也必須了解 Web 服務用於其資料的定址配置或命名空間。</span><span class="sxs-lookup"><span data-stu-id="66fb0-172">You must also understand the addressing scheme or namespace that the Web service uses for its data.</span></span>  
  
 <span data-ttu-id="66fb0-173">若為 Web 服務，您可以提供 `Query` 指定要呼叫之方法或 SOAP 動作的 <> 元素。</span><span class="sxs-lookup"><span data-stu-id="66fb0-173">For a Web service, you can provide a <`Query`> element that specifies a method to call or SOAP action.</span></span> <span data-ttu-id="66fb0-174">如果 XML 資料來源有一個階層式結構會產生您想用於報表中的資料，可以將此查詢保留空白，並使用預設查詢。</span><span class="sxs-lookup"><span data-stu-id="66fb0-174">You can leave the query empty and use the default query if the XML data source has a hierarchical structure that produces the data that you want to use for your report.</span></span> <span data-ttu-id="66fb0-175">此查詢執行時所擷取的 XML 元素節點值和屬性會對應到您用於報表中的資料集欄位。</span><span class="sxs-lookup"><span data-stu-id="66fb0-175">XML element node values and attributes retrieved when the query runs map to the dataset fields you use in your report.</span></span>  
  
### <a name="requirements-for-retrieving-xml-document-data"></a><span data-ttu-id="66fb0-176">擷取 XML 文件資料的需求</span><span class="sxs-lookup"><span data-stu-id="66fb0-176">Requirements for Retrieving XML Document Data</span></span>  
 <span data-ttu-id="66fb0-177">使用 http 通訊協定時，伺服器必須傳回 XML 資料，或是必須將 XML 資料內嵌在 XML `Query` 元素中。</span><span class="sxs-lookup"><span data-stu-id="66fb0-177">Using the http protocol, the server must return XML data or the XML data must be embedded in the XML `Query` element.</span></span> <span data-ttu-id="66fb0-178">如果您使用 http 通訊協定直接參考 XML 文件，其副檔名必須是 .xml。</span><span class="sxs-lookup"><span data-stu-id="66fb0-178">If you refer to an XML document directly using the http protocol, the extension must be .xml.</span></span>  
  
 <span data-ttu-id="66fb0-179">您必須知道如何建立 XML 查詢來擷取所有需要的資料。</span><span class="sxs-lookup"><span data-stu-id="66fb0-179">You must know how to create an XML query that retrieves all the data you need.</span></span> <span data-ttu-id="66fb0-180">如果您未指定元素路徑，剖析 XML 文件的預設行為是選取到 XML 文件中分葉節點集合的第一個可用路徑。</span><span class="sxs-lookup"><span data-stu-id="66fb0-180">If you do not specify an element path, the default behavior for parsing an XML document is to select the first available path to a leaf-node collection in the XML document.</span></span> <span data-ttu-id="66fb0-181">如果此 XML 文件包含其他同層級分葉節點集合的其他路徑，除非您在查詢中指定路徑，否則會忽略這些節點。</span><span class="sxs-lookup"><span data-stu-id="66fb0-181">If the XML document includes additional paths to other sibling leaf-node collections, those nodes will be ignored unless you specify a path in your query.</span></span>  
  
 <span data-ttu-id="66fb0-182">您可以使用類似於 XQuery 的 XML 語法提供元素路徑。</span><span class="sxs-lookup"><span data-stu-id="66fb0-182">You can provide an element path using XML syntax similar to XQuery.</span></span>  
  
 <span data-ttu-id="66fb0-183">如需詳細資訊，請參閱 msdn.microsoft.com 上《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [線上叢書](https://go.microsoft.com/fwlink/?linkid=121312)》中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文件的 [XML 報表資料的元素路徑語法 &#40;SSRS&#41;](element-path-syntax-for-xml-report-data-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="66fb0-183">For more information, see [Element Path Syntax for XML Report Data &#40;SSRS&#41;](element-path-syntax-for-xml-report-data-ssrs.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312) on msdn.microsoft.com.</span></span>  
  
##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="66fb0-184">參數</span><span class="sxs-lookup"><span data-stu-id="66fb0-184">Parameters</span></span>  
 <span data-ttu-id="66fb0-185">系統不會分析查詢來識別參數。</span><span class="sxs-lookup"><span data-stu-id="66fb0-185">The query is not analyzed to identify parameters.</span></span>  
  
 <span data-ttu-id="66fb0-186">若要加入參數，您必須透過 [[資料集屬性](../dataset-properties-dialog-box-parameters-report-builder.md)] 對話方塊上的 [參數] 頁面手動建立參數。</span><span class="sxs-lookup"><span data-stu-id="66fb0-186">To add parameters, you must create them manually through the **Parameter** page on the [Dataset Properties](../dataset-properties-dialog-box-parameters-report-builder.md) dialog box.</span></span>  
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="66fb0-187">備註</span><span class="sxs-lookup"><span data-stu-id="66fb0-187">Remarks</span></span>  
 <span data-ttu-id="66fb0-188">XML 資料延伸模組支援從表格式而非階層式 XML 資料進行報告的功能。</span><span class="sxs-lookup"><span data-stu-id="66fb0-188">The XML data extension supports reporting from XML data that is tabular and not hierarchical.</span></span> <span data-ttu-id="66fb0-189">如需詳細資訊，請參閱[從外部資料來源新增資料 &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="66fb0-189">For more information, see [Add Data from External Data Sources &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md).</span></span>  
  
 <span data-ttu-id="66fb0-190">沒有提供從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫擷取 XML 文件的內建支援。</span><span class="sxs-lookup"><span data-stu-id="66fb0-190">There is no built-in support for retrieving XML documents from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a> <span data-ttu-id="66fb0-191">如何主題</span><span class="sxs-lookup"><span data-stu-id="66fb0-191">How-To Topics</span></span>  
 <span data-ttu-id="66fb0-192">本節包含使用資料連接、資料來源與資料集的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="66fb0-192">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="66fb0-193">新增及驗證資料連線或資料來源 &#40;Report Builder 和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="66fb0-193">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="66fb0-194">建立共用資料集或內嵌資料集 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="66fb0-194">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="66fb0-195">將篩選加入資料集中 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="66fb0-195">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="66fb0-196">相關章節</span><span class="sxs-lookup"><span data-stu-id="66fb0-196">Related Sections</span></span>  
 <span data-ttu-id="66fb0-197">本文件集的這些章節會提供報表資料的深入概念性資訊，以及如何定義、自訂和使用與報表資料相關組件的程序資訊。</span><span class="sxs-lookup"><span data-stu-id="66fb0-197">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="66fb0-198">將資料加入至報表 &#40;Report Builder 和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="66fb0-198">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="66fb0-199">提供存取報表資料的概觀。</span><span class="sxs-lookup"><span data-stu-id="66fb0-199">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="66fb0-200">報表產生器中的資料連接、資料來源及連接字串</span><span class="sxs-lookup"><span data-stu-id="66fb0-200">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="66fb0-201">提供資料連接與資料來源的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="66fb0-201">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="66fb0-202">報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="66fb0-202">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="66fb0-203">提供內嵌與共用資料集的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="66fb0-203">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="66fb0-204">資料集欄位集合 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="66fb0-204">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="66fb0-205">提供查詢所產生之資料集欄位集合的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="66fb0-205">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="66fb0-206">《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [線上叢書》](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文件的 [Reporting Services 支援的資料來源 &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="66fb0-206">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="66fb0-207">提供支援每一個資料延伸模組之平台與版本的深入資訊。</span><span class="sxs-lookup"><span data-stu-id="66fb0-207">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66fb0-208">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66fb0-208">See Also</span></span>  
 <span data-ttu-id="66fb0-209">[報表參數 &#40;報表產生器和報表設計師&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="66fb0-209">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="66fb0-210">[篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="66fb0-210">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="66fb0-211">運算式 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="66fb0-211">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
