---
title: XML 報表資料的 XML 查詢語法 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- namespaces [Reporting Services]
- data processing extensions [Reporting Services], data sources
- xmldp [Reporting Services]
- XML [Reporting Services], data retrieval
ms.assetid: d203886f-faa1-4a02-88f5-dd4c217181ef
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62dde2b3ab18b5edb5c3786d39173fea3a0854ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585051"
---
# <a name="xml-query-syntax-for-xml-report-data-ssrs"></a><span data-ttu-id="dadb9-102">XML 報表資料的 XML 查詢語法 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="dadb9-102">XML Query Syntax for XML Report Data (SSRS)</span></span>
  <span data-ttu-id="dadb9-103">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中，可以建立 XML 資料來源的資料集。</span><span class="sxs-lookup"><span data-stu-id="dadb9-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can create datasets for XML data sources.</span></span> <span data-ttu-id="dadb9-104">當您定義資料來源之後，要建立此資料集的查詢。</span><span class="sxs-lookup"><span data-stu-id="dadb9-104">After you define a data source, you create a query for the dataset.</span></span> <span data-ttu-id="dadb9-105">根據資料來源所指向的 XML 資料類型而定，您可藉由加入 XML `Query` 或元素路徑來建立資料集查詢。</span><span class="sxs-lookup"><span data-stu-id="dadb9-105">Depending on the type of XML data pointed to by the data source, you create the dataset query by including an XML `Query` or an element path.</span></span> <span data-ttu-id="dadb9-106">XML `Query` 會以標記開頭 **\<Query>** ，而且會包含因數據源而異的命名空間和 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="dadb9-106">An XML `Query` starts with a **\<Query>** tag and includes namespaces and XML elements that vary depending on the data source.</span></span> <span data-ttu-id="dadb9-107">元素路徑與命名空間無關，而且會指定當搭配類似 XPath 語法使用基礎 XML 資料時，要使用哪些節點和節點屬性。</span><span class="sxs-lookup"><span data-stu-id="dadb9-107">An element path is namespace-independent and specifies which nodes and node attributes to use from the underlying XML data with an XPath-like syntax.</span></span> <span data-ttu-id="dadb9-108">如需項目路徑的詳細資訊，請參閱 [XML 報表資料的項目路徑語法 &#40;SSRS&#41;](report-data-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="dadb9-108">For more information about element paths, see [Element Path Syntax for XML Report Data &#40;SSRS&#41;](report-data-ssrs.md).</span></span>  
  
 <span data-ttu-id="dadb9-109">您可以針對下列 XML 資料類型建立 XML 資料來源：</span><span class="sxs-lookup"><span data-stu-id="dadb9-109">You can create an XML data source for the following types of XML data:</span></span>  
  
-   <span data-ttu-id="dadb9-110">使用 http 通訊協定由 URL 所指向的 Xml 文件</span><span class="sxs-lookup"><span data-stu-id="dadb9-110">Xml documents pointed to by a URL using http protocol</span></span>  
  
-   <span data-ttu-id="dadb9-111">傳回 XML 資料的 Web 服務端點</span><span class="sxs-lookup"><span data-stu-id="dadb9-111">Web service endpoints that return XML data</span></span>  
  
-   <span data-ttu-id="dadb9-112">內嵌 XML 資料</span><span class="sxs-lookup"><span data-stu-id="dadb9-112">Embedded XML data</span></span>  
  
 <span data-ttu-id="dadb9-113">指定 XML `Query` 或元素路徑的方式會因 XML 資料類型而異。</span><span class="sxs-lookup"><span data-stu-id="dadb9-113">How you specify an XML `Query` or an element path depends on the type of XML data.</span></span>  
  
 <span data-ttu-id="dadb9-114">如果是 XML 文件，則 XML `Query` 是選擇性的；</span><span class="sxs-lookup"><span data-stu-id="dadb9-114">For an XML document, the XML `Query` is optional.</span></span> <span data-ttu-id="dadb9-115">如果它包含在內，它可以包含選擇性的 XML `ElementPath`，</span><span class="sxs-lookup"><span data-stu-id="dadb9-115">If it is included, it can contain an optional XML `ElementPath`.</span></span> <span data-ttu-id="dadb9-116">XML `ElementPath` 的值會使用元素路徑語法。</span><span class="sxs-lookup"><span data-stu-id="dadb9-116">The value of the XML `ElementPath` uses the element path syntax.</span></span> <span data-ttu-id="dadb9-117">當資料來源中的 XML 資料需要時，必須加入 XML `Query` 和 XML `ElementPath`，才能正確處理命名空間。</span><span class="sxs-lookup"><span data-stu-id="dadb9-117">You include the XML `Query` and XML `ElementPath` to process namespaces correctly when it is needed by the XML data from the data source.</span></span>  
  
 <span data-ttu-id="dadb9-118">如果是連接字串 URL 所指向的 Web 服務端點，XML `Query` 會定義此 Web 服務方法、SOAP 動作，或兩者皆定義。</span><span class="sxs-lookup"><span data-stu-id="dadb9-118">For a Web service endpoint pointed to by a connection string URL, the XML `Query` defines either the Web service method, the SOAP action, or both.</span></span> <span data-ttu-id="dadb9-119">XML 資料提供者會建立一個 Web 服務要求來擷取要用於報表的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="dadb9-119">The XML data provider creates a Web service request that retrieves XML data to use for the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dadb9-120">當 Web 服務命名空間包含斜線 (`/)` 字元時，請同時加入 Web 服務方法和 SOAP 動作，好讓 XML 資料處理延伸模組可以正確衍生此命名空間。</span><span class="sxs-lookup"><span data-stu-id="dadb9-120">When a Web service namespace includes a forward slash (`/)` character, include both the Web service method and the SOAP action so that the XML data processing extension can derive the namespace correctly.</span></span>  
  
 <span data-ttu-id="dadb9-121">如果是內嵌 XML 文件，XML `Query` 會定義要使用的內嵌 XML 資料，以及包含選擇性命名空間和選擇性 XML `ElementPath`。</span><span class="sxs-lookup"><span data-stu-id="dadb9-121">For an embedded XML document, the XML `Query` defines the embedded XML data to use, includes optional namespaces, and contains an optional XML `ElementPath`..</span></span>  
  
## <a name="specifying-query-parameters-for-xml-data"></a><span data-ttu-id="dadb9-122">指定 XML 資料的查詢參數</span><span class="sxs-lookup"><span data-stu-id="dadb9-122">Specifying Query Parameters for XML Data</span></span>  
 <span data-ttu-id="dadb9-123">您可以指定 XML 文件的查詢參數。</span><span class="sxs-lookup"><span data-stu-id="dadb9-123">You can specify query parameters for XML documents.</span></span>  
  
-   <span data-ttu-id="dadb9-124">針對 URL 要求，查詢參數會包含為標準 URL 參數。</span><span class="sxs-lookup"><span data-stu-id="dadb9-124">For URL requests, the query parameters are included as standard URL parameters.</span></span>  
  
-   <span data-ttu-id="dadb9-125">針對 Web 服務要求，查詢參數會傳遞至 Web 服務方法。</span><span class="sxs-lookup"><span data-stu-id="dadb9-125">For Web service requests, query parameters are passed to the Web service method.</span></span> <span data-ttu-id="dadb9-126">若要定義查詢參數，請使用 [資料集屬性] 對話方塊的 [參數] 頁面。</span><span class="sxs-lookup"><span data-stu-id="dadb9-126">To define a query parameter, use the **Parameters** page of the **Dataset Properties** dialog box.</span></span> <span data-ttu-id="dadb9-127">如需詳細資訊，請參閱 [資料集屬性對話方塊、參數](dataset-properties-dialog-box-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="dadb9-127">For more information, see [Dataset Properties Dialog Box, Parameters](dataset-properties-dialog-box-parameters.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="dadb9-128">範例</span><span class="sxs-lookup"><span data-stu-id="dadb9-128">Example</span></span>  
 <span data-ttu-id="dadb9-129">下表中的範例會說明如何從報表伺服器 Web 服務、XML 文件和內嵌 XML 資料中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="dadb9-129">The examples in the following table illustrate how to retrieve data from the Report Server Web service, an XML document, and embedded XML data.</span></span>  
  
|<span data-ttu-id="dadb9-130">XML 資料來源</span><span class="sxs-lookup"><span data-stu-id="dadb9-130">XML data source</span></span>|<span data-ttu-id="dadb9-131">查詢範例</span><span class="sxs-lookup"><span data-stu-id="dadb9-131">Query example</span></span>|  
|---------------------|-------------------|  
|<span data-ttu-id="dadb9-132">ListChildren 方法中的 Web 服務 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="dadb9-132">Web service XML data from ListChildren method.</span></span>|`<Query>`<br /><br /> `<Method Name="ListChildren" Namespace="https://schemas.microsoft.com/sqlserver/2005/06/30/reporting/reportingservices" />`<br /><br /> `</Query>`|  
|<span data-ttu-id="dadb9-133">SoapAction 中的 Web 服務 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="dadb9-133">Web service XML data from SoapAction.</span></span>|`<Query xmlns=namespace>`<br /><br /> `<SoapAction>http://schemas/microsoft.com/sqlserver/2005/03/23/reporting/reportingservices/ListChildren</SoapAction>`<br /><br /> `</Query>`|  
|<span data-ttu-id="dadb9-134">使用命名空間的 XML 文件或內嵌 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="dadb9-134">XML Document or embedded XML data that uses namespaces.</span></span><br /><br /> <span data-ttu-id="dadb9-135">指定元素路徑之命名空間的查詢元素。</span><span class="sxs-lookup"><span data-stu-id="dadb9-135">Query element specifying namespaces for an element path.</span></span>|`<Query xmlns:es="https://schemas.microsoft.com/StandardSchemas/ExtendedSales">`<br /><br /> `<ElementPath>/Customers/Customer/Orders/Order/es:LineItems/es:LineItem</ElementPath>`<br /><br /> `</Query>`|  
|<span data-ttu-id="dadb9-136">內嵌 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="dadb9-136">Embedded XML document.</span></span>|`<Query>`<br /><br /> `<XmlData>`<br /><br /> `<Customers>`<br /><br /> `<Customer ID="1">Bobby</Customer>`<br /><br /> `</Customers>`<br /><br /> `</XmlData>`<br /><br /> `<ElementPath>Customer {@}</ElementPath>`<br /><br /> `</Query>`|  
|<span data-ttu-id="dadb9-137">使用預設值的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="dadb9-137">XML document that uses default.</span></span>|<span data-ttu-id="dadb9-138">*沒有查詢*。</span><span class="sxs-lookup"><span data-stu-id="dadb9-138">*No query*.</span></span><br /><br /> <span data-ttu-id="dadb9-139">元素路徑衍生自 XML 文件本身，而且與命名空間無關。</span><span class="sxs-lookup"><span data-stu-id="dadb9-139">The element path is derived from the XML document itself and is namespace-independent.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="dadb9-140">第一個 Web 服務範例會使用 <xref:ReportService2006.ReportingService2006.ListChildren%2A> 方法中的 Web 服務 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="dadb9-140">The first Web service example lists the contents of the report server that uses the <xref:ReportService2006.ReportingService2006.ListChildren%2A> method.</span></span> <span data-ttu-id="dadb9-141">若要執行這個查詢，您必須建立新的資料來源，然後設定 http://localhost/reportserver/reportservice2006.asmx 的連接字串。</span><span class="sxs-lookup"><span data-stu-id="dadb9-141">To run this query, you must create a new data source and set the connection string to http://localhost/reportserver/reportservice2006.asmx.</span></span> <span data-ttu-id="dadb9-142"><xref:ReportService2006.ReportingService2006.ListChildren%2A> 方法接受兩個參數：`Item` 和 `Recursive`。</span><span class="sxs-lookup"><span data-stu-id="dadb9-142">The <xref:ReportService2006.ReportingService2006.ListChildren%2A> method takes two parameters: `Item` and `Recursive`.</span></span> <span data-ttu-id="dadb9-143">將 `Item` 的預設值設定為 `/`，並將 `Recursive` 的預設值設定為 `1`。</span><span class="sxs-lookup"><span data-stu-id="dadb9-143">Set the default value for `Item` to `/` and `Recursive` to `1`.</span></span>  
  
## <a name="specifying-namespaces"></a><span data-ttu-id="dadb9-144">指定命名空間</span><span class="sxs-lookup"><span data-stu-id="dadb9-144">Specifying Namespaces</span></span>  
 <span data-ttu-id="dadb9-145">使用 XML `Query` 元素可指定用於資料來源中 XML 資料的命名空間；</span><span class="sxs-lookup"><span data-stu-id="dadb9-145">Use the XML `Query` element to specify the namespaces that are used in the XML data from the data source.</span></span> <span data-ttu-id="dadb9-146">下列 XML 查詢會使用命名空間 `sales`。</span><span class="sxs-lookup"><span data-stu-id="dadb9-146">The following XML query uses the namespace `sales`.</span></span> <span data-ttu-id="dadb9-147">`sales:LineItems` 和 `sales:LineItem` 的 XML `ElementPath` 節點會使用命名空間 `sales`。</span><span class="sxs-lookup"><span data-stu-id="dadb9-147">The XML `ElementPath` nodes for `sales:LineItems` and `sales:LineItem` use the namespace `sales`.</span></span>  
  
```  
<Query xmlns:sales=  
"https://schemas.microsoft.com/StandardSchemas/ExtendedSales">  
   <SoapAction>  
      https://schemas.microsoft.com/SalesWebService/ListOrders   
   </SoapAction>  
   <ElementPath>  
      Customers/Customer/Orders/Order/sales:LineItems/sales:LineItem  
   </ElementPath>  
</Query>  
```  
  
 <span data-ttu-id="dadb9-148">若要指定資料提供者命名空間，好讓預設的命名空間留白，請使用 `xmldp`；</span><span class="sxs-lookup"><span data-stu-id="dadb9-148">To specify the data provider namespace so that the default namespace remains empty, use `xmldp`.</span></span> <span data-ttu-id="dadb9-149">下列範例會顯示這一點。</span><span class="sxs-lookup"><span data-stu-id="dadb9-149">This is shown in the following example.</span></span>  
  
### <a name="example"></a><span data-ttu-id="dadb9-150">範例</span><span class="sxs-lookup"><span data-stu-id="dadb9-150">Example</span></span>  
 <span data-ttu-id="dadb9-151">下列範例會使用 XML 文件 DPNamespace.xml，這個文件是當做表格之後的說明；</span><span class="sxs-lookup"><span data-stu-id="dadb9-151">The following examples use the XML document DPNamespace.xml, which is provided for illustration after the table.</span></span> <span data-ttu-id="dadb9-152">這個表格會顯示包含命名空間前置詞的兩個 XML ElementPath 語法範例。</span><span class="sxs-lookup"><span data-stu-id="dadb9-152">This table shows two examples of XML ElementPath syntax that includes namespace prefixes.</span></span>  
  
|<span data-ttu-id="dadb9-153">XML 查詢元素</span><span class="sxs-lookup"><span data-stu-id="dadb9-153">XML Query Element</span></span>|<span data-ttu-id="dadb9-154">在資料集中產生欄位</span><span class="sxs-lookup"><span data-stu-id="dadb9-154">Resulting fields in the dataset</span></span>|  
|-----------------------|-------------------------------------|  
|\<Query/>|<span data-ttu-id="dadb9-155">值 A： `https://schemas.microsoft.com/..` 。</span><span class="sxs-lookup"><span data-stu-id="dadb9-155">Value A: `https://schemas.microsoft.com/..`.</span></span><br /><br /> <span data-ttu-id="dadb9-156">值 B： `https://schemas.microsoft.com/..` 。</span><span class="sxs-lookup"><span data-stu-id="dadb9-156">Value B: `https://schemas.microsoft.com/..`.</span></span><br /><br /> <span data-ttu-id="dadb9-157">值 C： `https://schemas.microsoft.com/.` 。</span><span class="sxs-lookup"><span data-stu-id="dadb9-157">Value C: `https://schemas.microsoft.com/.`..</span></span>|  
|\<xmldp:Query xmlns:xmldp="https://schemas.microsoft.com/sqlserver/2005/02/reporting/XmlDPQuery" xmlns:ns="https://schemas.microsoft.com/..."><br /><br /> <span data-ttu-id="dadb9-158">\<xmldp:ElementPath>根 {} /ns： Element2/Node\</xmldp:ElementPath></span><span class="sxs-lookup"><span data-stu-id="dadb9-158">\<xmldp:ElementPath>Root {}/ns:Element2/Node\</xmldp:ElementPath></span></span><br /><br /> \</xmldp:Query>|<span data-ttu-id="dadb9-159">D 值</span><span class="sxs-lookup"><span data-stu-id="dadb9-159">Value D</span></span><br /><br /> <span data-ttu-id="dadb9-160">E 值</span><span class="sxs-lookup"><span data-stu-id="dadb9-160">Value E</span></span><br /><br /> <span data-ttu-id="dadb9-161">F 值</span><span class="sxs-lookup"><span data-stu-id="dadb9-161">Value F</span></span>|  
  
#### <a name="xml-document-dpnamespacexml"></a><span data-ttu-id="dadb9-162">XML 文件：DPNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="dadb9-162">XML document: DPNamespace.xml</span></span>  
 <span data-ttu-id="dadb9-163">您可以複製這段 XML，並將它儲存為報表設計師可以使用的 URL，以便當做 XML 資料來源使用；例如 http://localhost/DPNamespace.xml。</span><span class="sxs-lookup"><span data-stu-id="dadb9-163">You can copy this XML and save it to a URL available for Report Designer to use as an XML data source: for example, http://localhost/DPNamespace.xml.</span></span>  
  
```  
<Root xmlns:ns="https://schemas.microsoft.com/...">  
   <ns:Element1>  
      <Node>Value A</Node>  
      <Node>Value B</Node>  
      <Node>Value C</Node>  
   </ns:Element1>  
   <ns:Element2>  
      <Node>Value D</Node>  
      <Node>Value E</Node>  
      <Node>Value F</Node>  
   </ns:Element2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dadb9-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dadb9-164">See Also</span></span>  
 <span data-ttu-id="dadb9-165">[XML 連線類型 &#40;SSRS&#41;](xml-connection-type-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dadb9-165">[XML Connection Type &#40;SSRS&#41;](xml-connection-type-ssrs.md) </span></span>  
 [<span data-ttu-id="dadb9-166">Reporting Services 教學課程 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="dadb9-166">Reporting Services Tutorials &#40;SSRS&#41;</span></span>](../reporting-services-tutorials-ssrs.md)  
  
  
