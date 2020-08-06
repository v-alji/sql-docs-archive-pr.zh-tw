---
title: 用戶端 XML 格式 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- FOR XML clause, formatting
- middle tier XML formatting [SQLXML]
- client-side XML formatting
- client-side-xml attribute
ms.assetid: 9630a21d-a93b-4d3b-8a25-c4b32399f993
author: rothja
ms.author: jroth
ms.openlocfilehash: bf4a680d79a25d24ebdf779b41fd3be5a5d6a605
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597711"
---
# <a name="client-side-xml-formatting-sqlxml-40"></a><span data-ttu-id="7273c-102">用戶端 XML 格式 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="7273c-102">Client-side XML Formatting (SQLXML 4.0)</span></span>
  <span data-ttu-id="7273c-103">本主題提供有關用戶端 XML 格式的資訊。</span><span class="sxs-lookup"><span data-stu-id="7273c-103">This topic provides information about client-side XML formatting.</span></span> <span data-ttu-id="7273c-104">用戶端格式指的是 XML 在中間層的格式。</span><span class="sxs-lookup"><span data-stu-id="7273c-104">Client-side formatting refers to the formatting of XML on the middle tier.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7273c-105">本主題提供在用戶端上使用 FOR XML 子句的其他資訊，並假設您已經熟悉 FOR XML 子句。</span><span class="sxs-lookup"><span data-stu-id="7273c-105">This topic provides additional information about using the FOR XML clause on the client side, and assumes you are already familiar with the FOR XML clause.</span></span> <span data-ttu-id="7273c-106">如需 FOR XML 的詳細資訊，請參閱[使用 FOR xml 來建立 xml](../../xml/for-xml-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7273c-106">For more information about FOR XML, see [Constructing XML Using FOR XML](../../xml/for-xml-sql-server.md).</span></span>  
  
 <span data-ttu-id="7273c-107">**重要事項**若要以新的資料類型使用用戶端的 FOR XML 功能 `xml` ，用戶端應該一律使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT (SQLNCLI11) 資料提供者，而非 SQLOLEDB 提供者。</span><span class="sxs-lookup"><span data-stu-id="7273c-107">**Important** To use client-side FOR XML functionality with the new `xml` data type, clients should always use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) data provider instead of the SQLOLEDB provider.</span></span> <span data-ttu-id="7273c-108">SQLNCLI11 是最新版的 SQL Server 提供者，而且完全了解 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 推出的資料類型。</span><span class="sxs-lookup"><span data-stu-id="7273c-108">SQLNCLI11 is the latest version of the SQL Server provider and fully understands data types introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="7273c-109">包含 SQLOLEDB 提供者之用戶端 FOR XML 的行為會將 `xml` 資料類型視為字串。</span><span class="sxs-lookup"><span data-stu-id="7273c-109">The behavior for client side FOR XML with the SQLOLEDB provider will treat `xml` data types as strings.</span></span>  
  
## <a name="formatting-xml-documents-on-the-client-side"></a><span data-ttu-id="7273c-110">格式化用戶端上的 XML 文件</span><span class="sxs-lookup"><span data-stu-id="7273c-110">Formatting XML Documents on the Client Side</span></span>  
 <span data-ttu-id="7273c-111">當用戶端應用程式執行下列查詢時：</span><span class="sxs-lookup"><span data-stu-id="7273c-111">When a client application executes the following query:</span></span>  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
FOR XML RAW  
```  
  
 <span data-ttu-id="7273c-112">只有查詢的這個部分會傳送到伺服器：</span><span class="sxs-lookup"><span data-stu-id="7273c-112">...only this part of the query is sent to the server:</span></span>  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
```  
  
 <span data-ttu-id="7273c-113">伺服器會執行查詢，並將包含 FirstName 和 LastNamecolumns) 的資料列集 (傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="7273c-113">The server executes the query and returns a rowset (which contains FirstName and LastNamecolumns) to the client.</span></span> <span data-ttu-id="7273c-114">中間層接著會將 FOR XML 轉換套用至資料列集，並將 XML 格式傳回到用戶端。</span><span class="sxs-lookup"><span data-stu-id="7273c-114">The middle tier then applies the FOR XML transformation to the rowset and returns XML formatting to the client.</span></span>  
  
 <span data-ttu-id="7273c-115">同樣地，當您執行 XPath 查詢時，伺服器會將資料列集傳回到用戶端，並將 FOR XML EXPLICIT 轉換套用到用戶端上的資料列集，以產生所需的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="7273c-115">Similarly, when you execute an XPath query, the server returns the rowset to the client and the FOR XML EXPLICIT transformation is applied to the rowset on the client, generating the desired XML formatting.</span></span>  
  
 <span data-ttu-id="7273c-116">下表顯示您利用用戶端 FOR XML 指定的模式。</span><span class="sxs-lookup"><span data-stu-id="7273c-116">The following table shows the modes you can specify with client-side FOR XML.</span></span>  
  
|<span data-ttu-id="7273c-117">用戶端 FOR XML 模式</span><span class="sxs-lookup"><span data-stu-id="7273c-117">Client-side FOR XML mode</span></span>|<span data-ttu-id="7273c-118">註解</span><span class="sxs-lookup"><span data-stu-id="7273c-118">Comment</span></span>|  
|-------------------------------|-------------|  
|<span data-ttu-id="7273c-119">RAW</span><span class="sxs-lookup"><span data-stu-id="7273c-119">RAW</span></span>|<span data-ttu-id="7273c-120">在用戶端或伺服器端的 FOR XML 中指定時，會產生相同的結果。</span><span class="sxs-lookup"><span data-stu-id="7273c-120">Produces identical results when specified in client-side or server-side FOR XML.</span></span>|  
|<span data-ttu-id="7273c-121">NESTED</span><span class="sxs-lookup"><span data-stu-id="7273c-121">NESTED</span></span>|<span data-ttu-id="7273c-122">這類似於伺服器端上的 FOR XML AUTO 模式。</span><span class="sxs-lookup"><span data-stu-id="7273c-122">Is similar to FOR XML AUTO mode on the server-side.</span></span>|  
|<span data-ttu-id="7273c-123">EXPLICIT</span><span class="sxs-lookup"><span data-stu-id="7273c-123">EXPLICIT</span></span>|<span data-ttu-id="7273c-124">這類似於伺服器端的 FOR XML EXPLICIT 模式。</span><span class="sxs-lookup"><span data-stu-id="7273c-124">Is similar to server-side FOR XML EXPLICIT mode.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="7273c-125">如果您指定 AUTO 模式並要求用戶端 XML 格式，會將完整的查詢傳送到伺服器，也就是說，XML 格式會出現在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="7273c-125">If you specify AUTO mode and request client-side XML formatting, the entire query is sent to the server; that is, XML formatting occurs on the server.</span></span> <span data-ttu-id="7273c-126">這是為了方便而進行，但是請注意，NESTED 模式會傳回基礎資料表名稱，當做所產生之 XML 文件中的元素名稱。</span><span class="sxs-lookup"><span data-stu-id="7273c-126">This is done for convenience, but note that the NESTED mode returns base table names as element names in the XML document that is generated.</span></span> <span data-ttu-id="7273c-127">您撰寫的部分應用程式可能需要基礎資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="7273c-127">Some of the applications you write might require base table names.</span></span> <span data-ttu-id="7273c-128">例如，您可能會執行一個預存程序，並將所產生的資料載入到資料集 (在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 中)，接著在稍後產生 DiffGram 來更新資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="7273c-128">For example, you might execute a stored procedure and load the resulting data in a Dataset (in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework), and then later generate a DiffGram to update data in the tables.</span></span> <span data-ttu-id="7273c-129">在此種情況下，您需要基礎資料表資訊，而且您必須使用 NESTED 模式。</span><span class="sxs-lookup"><span data-stu-id="7273c-129">In such a case, you would need the base table information and you would have to use the NESTED mode.</span></span>  
  
## <a name="benefits-of-client-side-xml-formatting"></a><span data-ttu-id="7273c-130">用戶端 XML 格式的優點</span><span class="sxs-lookup"><span data-stu-id="7273c-130">Benefits of Client-side XML formatting</span></span>  
 <span data-ttu-id="7273c-131">以下為在用戶端上格式化 XML 的一些優點。</span><span class="sxs-lookup"><span data-stu-id="7273c-131">The following are some benefits of formatting XML on the client.</span></span>  
  
### <a name="if-you-have-stored-procedures-on-the-server-that-return-a-single-rowset-you-can-request-client-side-for-xml-transformation-to-generate-an-xml"></a><span data-ttu-id="7273c-132">如果您在伺服器上的預存程序傳回單一資料列集，您可以要求用戶端 FOR XML 轉換產生 XML。</span><span class="sxs-lookup"><span data-stu-id="7273c-132">If you have stored procedures on the server that return a single rowset, you can request client-side FOR XML transformation to generate an XML.</span></span>  
 <span data-ttu-id="7273c-133">例如，請考慮下列預存程序。</span><span class="sxs-lookup"><span data-stu-id="7273c-133">For example, consider the following stored procedure.</span></span> <span data-ttu-id="7273c-134">此預存程序會先從 AdventureWorks 資料庫的 Person.Contact 資料表中，傳回員工的名字和姓氏。</span><span class="sxs-lookup"><span data-stu-id="7273c-134">This procedure returns the first and last names of employees from the Person.Contact table in the AdventureWorks database:</span></span>  
  
```  
IF EXISTS (SELECT name FROM sysobjects  
   WHERE name = 'GetContacts' AND type = 'P')  
   DROP PROCEDURE GetContacts  
GO  
CREATE PROCEDURE GetContacts  
AS  
    SELECT   FirstName, LastName  
    FROM     Person.Contact  
```  
  
 <span data-ttu-id="7273c-135">下列範例 XML 範本會執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="7273c-135">The following sample XML template executes the stored procedure.</span></span> <span data-ttu-id="7273c-136">FOR XML 子句會在預存程序名稱後指定。</span><span class="sxs-lookup"><span data-stu-id="7273c-136">The FOR XML clause is specified after the stored procedure name.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    EXEC GetContacts FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="7273c-137">由於**用戶端-xml**屬性設定為 1 (true) 在範本中，因此預存程式會在伺服器上執行，而伺服器所傳回的兩個數據行資料列集會在仲介層轉換成 xml，並傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="7273c-137">Because the **client-side-xml** attribute is set to 1 (true) in the template, the stored procedure is executed on the server and the two-column rowset that is returned by the server is transformed into XML on the middle tier and returned to the client.</span></span> <span data-ttu-id="7273c-138">(此處僅顯示部分結果)。</span><span class="sxs-lookup"><span data-stu-id="7273c-138">(Only a partial result is shown here.)</span></span>  
  
```  
 <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact FirstName="Catherine" LastName="Abel" />  
</ROOT>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="7273c-139">當您使用的是 SQLXMLOLEDB 提供者或 SQLXML Managed 類別時，您可以使用 `ClientSideXml` 屬性來要求用戶端 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="7273c-139">When you are using the SQLXMLOLEDB Provider or SQLXML Managed Classes, you can use the `ClientSideXml` property to request client-side XML formatting.</span></span>  
  
### <a name="the-workload-is-more-balanced"></a><span data-ttu-id="7273c-140">工作負載較為對稱。</span><span class="sxs-lookup"><span data-stu-id="7273c-140">The workload is more balanced.</span></span>  
 <span data-ttu-id="7273c-141">由於用戶端會執行 XML 格式化，因此在伺服器和用戶端之間的工作負載較為對稱，讓伺服器可以做其他的事情。</span><span class="sxs-lookup"><span data-stu-id="7273c-141">Because the client does the XML formatting, the workload is balanced between the server and client, freeing the server to do other things.</span></span>  
  
## <a name="supporting-client-side-xml-formatting"></a><span data-ttu-id="7273c-142">支援用戶端 XML 格式</span><span class="sxs-lookup"><span data-stu-id="7273c-142">Supporting Client-side XML Formatting</span></span>  
 <span data-ttu-id="7273c-143">為支援用戶端 XML 格式功能，SQLXML 提供：</span><span class="sxs-lookup"><span data-stu-id="7273c-143">To support the client-side XML formatting functionality, SQLXML provides:</span></span>  
  
-   <span data-ttu-id="7273c-144">SQLXMLOLEDB 提供者</span><span class="sxs-lookup"><span data-stu-id="7273c-144">SQLXMLOLEDB Provider</span></span>  
  
-   <span data-ttu-id="7273c-145">SQLXML Managed 類別</span><span class="sxs-lookup"><span data-stu-id="7273c-145">SQLXML Managed Classes</span></span>  
  
-   <span data-ttu-id="7273c-146">增強的 XML 範本支援</span><span class="sxs-lookup"><span data-stu-id="7273c-146">Enhanced XML template support</span></span>  
  
-   <span data-ttu-id="7273c-147">SqlXmlCommand. ClientSideXml 屬性</span><span class="sxs-lookup"><span data-stu-id="7273c-147">SqlXmlCommand.ClientSideXml property</span></span>  
  
     <span data-ttu-id="7273c-148">您可以將 SQLXML Managed 類別的這個屬性設定為 true，藉以指定用戶端功能。</span><span class="sxs-lookup"><span data-stu-id="7273c-148">You can specify client-side formatting by setting this property of the SQLXML managed classes to true.</span></span>  
  
## <a name="enhanced-xml-template-support"></a><span data-ttu-id="7273c-149">增強的 XML 範本支援</span><span class="sxs-lookup"><span data-stu-id="7273c-149">Enhanced XML Template Support</span></span>  
 <span data-ttu-id="7273c-150">從開始 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ，中的 XML 範本已透過 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加入**用戶端-xml**屬性來增強。</span><span class="sxs-lookup"><span data-stu-id="7273c-150">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], the XML template in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] has been enhanced with the addition of the **client-side-xml** attribute.</span></span> <span data-ttu-id="7273c-151">如果此屬性設定為 true，XML 會在用戶端上格式化。</span><span class="sxs-lookup"><span data-stu-id="7273c-151">If this attribute is set to true, XML is formatted on the client.</span></span> <span data-ttu-id="7273c-152">請注意，此範本屬性的功能與 SQLXMLOLEDB 提供者特定的 ClientSideXML 屬性相同。</span><span class="sxs-lookup"><span data-stu-id="7273c-152">Note that this template attribute is identical in functionality to the SQLXMLOLEDB Provider-specific ClientSideXML property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7273c-153">如果您在使用 SQLXMLOLEDB 提供者的 ADO 應用程式中執行 XML 範本，並同時在範本和提供者 ClientSideXML 屬性中指定**用戶端 xml**屬性，則會優先使用範本中指定的值。</span><span class="sxs-lookup"><span data-stu-id="7273c-153">If you execute an XML template in an ADO application that is using the SQLXMLOLEDB Provider, and you specify both the **client-side-xml** attribute in the template and the provider ClientSideXML property, the value specified in the template takes precedence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7273c-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7273c-154">See Also</span></span>  
 <span data-ttu-id="7273c-155">[用戶端和伺服器端 XML 格式的架構 &#40;SQLXML 4.0&#41;](server-side-xml-formatting-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="7273c-155">[Architecture of Client-side and Server-side XML Formatting &#40;SQLXML 4.0&#41;](server-side-xml-formatting-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="7273c-156">[FOR XML &#40;SQL Server&#41;](../../xml/for-xml-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7273c-156">[FOR XML &#40;SQL Server&#41;](../../xml/for-xml-sql-server.md) </span></span>  
 <span data-ttu-id="7273c-157">[FOR XML 安全性考慮 &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="7273c-157">[FOR XML Security Considerations &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="7273c-158">[SQLXML 4.0 中的 xml 資料類型支援](../xml-data-type-support-in-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="7273c-158">[xml Data Type Support in SQLXML 4.0](../xml-data-type-support-in-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="7273c-159">[SQLXML Managed 類別](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md) </span><span class="sxs-lookup"><span data-stu-id="7273c-159">[SQLXML Managed Classes](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md) </span></span>  
 <span data-ttu-id="7273c-160">[用戶端與伺服器端 XML 格式設定 &#40;SQLXML 4.0&#41;](client-side-vs-server-side-xml-formatting-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="7273c-160">[Client-side vs. Server-side XML Formatting &#40;SQLXML 4.0&#41;](client-side-vs-server-side-xml-formatting-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="7273c-161">[SqlXmlCommand 物件 &#40;SQLXML Managed 類別&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlcommand-object.md) </span><span class="sxs-lookup"><span data-stu-id="7273c-161">[SqlXmlCommand Object &#40;SQLXML Managed Classes&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlcommand-object.md) </span></span>  
 [<span data-ttu-id="7273c-162">XML 資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7273c-162">XML Data &#40;SQL Server&#41;</span></span>](../../xml/xml-data-sql-server.md)  
  
  
