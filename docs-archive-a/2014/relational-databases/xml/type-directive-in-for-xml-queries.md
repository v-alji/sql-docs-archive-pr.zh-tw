---
title: FOR XML 查詢中的 TYPE 指示詞 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, TYPE directive
- TYPE directive
ms.assetid: a3df6c30-1f25-45dc-b5a9-bd0e41921293
author: rothja
ms.author: jroth
ms.openlocfilehash: cddce90718ef5edfcf161ddc6cc52b617825a2e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606653"
---
# <a name="type-directive-in-for-xml-queries"></a><span data-ttu-id="0532f-102">在 FOR XML 查詢中的 TYPE 指示詞</span><span class="sxs-lookup"><span data-stu-id="0532f-102">TYPE Directive in FOR XML Queries</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="0532f-103">支援[xml &#40;transact-sql&#41;](/sql/t-sql/xml/xml-transact-sql)可讓您藉由指定 type 指示詞，選擇性地要求以資料類型的形式傳回 for xml 查詢的結果 `xml` 。</span><span class="sxs-lookup"><span data-stu-id="0532f-103">support for the [xml &#40;Transact-SQL&#41;](/sql/t-sql/xml/xml-transact-sql) enables you to optionally request that the result of a FOR XML query be returned as `xml` data type by specifying the TYPE directive.</span></span> <span data-ttu-id="0532f-104">這將允許您處理伺服器上 FOR XML 查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="0532f-104">This allows you to process the result of a FOR XML query on the server.</span></span> <span data-ttu-id="0532f-105">例如，您可以針對它指定 XQuery、將結果指派給 `xml` 類型變數，或撰寫[NESTED FOR XML 查詢](use-nested-for-xml-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="0532f-105">For example, you can specify an XQuery against it, assign the result to an `xml` type variable, or write [Nested FOR XML queries](use-nested-for-xml-queries.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0532f-106">會傳回 XML 資料類型的執行個體資料至用戶端，做為不同伺服器建構的結果，例如使用 TYPE 指示詞的 FOR XML 查詢，或使用 `xml` 資料類型從 SQL 資料表資料行和輸出參數傳回 XML 執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="0532f-106">returns XML data type instance data to the client as a result of different server-constructs such as FOR XML queries that use the TYPE directive, or where the `xml` data type is used to return XML instance data values from SQL table columns and output parameters.</span></span> <span data-ttu-id="0532f-107">在用戶端應用程式中，ADO.NET 提供者要求以二進位編碼從伺服器傳送此 XML 資料類型資訊。</span><span class="sxs-lookup"><span data-stu-id="0532f-107">In client application code, the ADO.NET provider requests this XML data type information to be sent in a binary encoding from the server.</span></span> <span data-ttu-id="0532f-108">然而，如果您使用沒有 TYPE 指示詞的 FOR XML，XML 資料會以字串類型傳回。</span><span class="sxs-lookup"><span data-stu-id="0532f-108">However, if you are using FOR XML without the TYPE directive, the XML data comes back as a string type.</span></span> <span data-ttu-id="0532f-109">在任一情況下，用戶端提供者將永遠可以處理任一 XML 形式。</span><span class="sxs-lookup"><span data-stu-id="0532f-109">In any case, the client provider will always be able to handle either form of XML.</span></span> <span data-ttu-id="0532f-110">請注意，不含 TYPE 指示詞的最上層 FOR XML 無法與資料指標一起使用。</span><span class="sxs-lookup"><span data-stu-id="0532f-110">Note that top-level FOR XML without the TYPE directive cannot be used with cursors.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0532f-111">範例</span><span class="sxs-lookup"><span data-stu-id="0532f-111">Examples</span></span>  
 <span data-ttu-id="0532f-112">下列範例說明搭配 FOR XML 查詢使用 TYPE 指示詞。</span><span class="sxs-lookup"><span data-stu-id="0532f-112">The following examples illustrate the use of the TYPE directive with FOR XML queries.</span></span>  
  
### <a name="retrieving-for-xml-query-results-as-xml-type"></a><span data-ttu-id="0532f-113">以 xml 類型擷取 FOR XML 查詢結果</span><span class="sxs-lookup"><span data-stu-id="0532f-113">Retrieving FOR XML query results as xml type</span></span>  
 <span data-ttu-id="0532f-114">下列查詢將擷取 `Contacts` 資料表中客戶的連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="0532f-114">The following query retrieves customer contact information from the `Contacts` table.</span></span> <span data-ttu-id="0532f-115">由於 `TYPE` 指示詞是在 `FOR XML` 中指定，因此結果會以 `xml` 類型傳回。</span><span class="sxs-lookup"><span data-stu-id="0532f-115">Because the `TYPE` directive is specified in `FOR XML`, the result is returned as `xml` type.</span></span>  
  
```  
USE AdventureWorks2012;  
Go  
SELECT BusinessEntityID, FirstName, LastName  
FROM Person.Person  
ORDER BY BusinessEntityID  
FOR XML AUTO, TYPE;  
```  
  
 <span data-ttu-id="0532f-116">以下是部份結果：</span><span class="sxs-lookup"><span data-stu-id="0532f-116">This is the partial result:</span></span>  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="S??nchez"/>`  
  
 `<Person.Person BusinessEntityID="2" FirstName="Terri" LastName="Duffy"/>`  
  
 `...`  
  
### <a name="assigning-for-xml-query-results-to-an-xml-type-variable"></a><span data-ttu-id="0532f-117">將 FOR XML 查詢結果指派給 xml 類型變數</span><span class="sxs-lookup"><span data-stu-id="0532f-117">Assigning FOR XML query results to an xml type variable</span></span>  
 <span data-ttu-id="0532f-118">在以下範例中，FOR XML 結果會指派給一個 `xml` 類型變數 `@x`。</span><span class="sxs-lookup"><span data-stu-id="0532f-118">In the following example, a FOR XML result is assigned to an `xml` type variable, `@x`.</span></span> <span data-ttu-id="0532f-119">查詢會從的資料行抓取連絡人資訊，例如 `BusinessEntityID` 、 `FirstName` 、 `LastName` 和其他電話號碼 `AdditionalContactInfo` `xml``TYPE` 。</span><span class="sxs-lookup"><span data-stu-id="0532f-119">The query retrieves contact information, such as the `BusinessEntityID`, `FirstName`, `LastName`, and additional telephone numbers, from the `AdditionalContactInfo` column of `xml``TYPE`.</span></span> <span data-ttu-id="0532f-120">由於 `FOR XML` 子句會指定 `TYPE` 指示詞，因此 XML 將以 `xml` 類型傳回並將其指派給變數。</span><span class="sxs-lookup"><span data-stu-id="0532f-120">Because the `FOR XML` clause specifies `TYPE` directive, the XML is returned as `xml` type and is assigned to a variable.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @x xml;  
SET @x = (  
   SELECT BusinessEntityID,   
          FirstName,   
          LastName,   
          AdditionalContactInfo.query('  
declare namespace aci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
              //act:telephoneNumber/act:number') as MorePhoneNumbers  
   FROM Person.Person  
   FOR XML AUTO, TYPE);  
SELECT @x;  
GO  
```  
  
### <a name="querying-results-of-a-for-xml-query"></a><span data-ttu-id="0532f-121">查詢 FOR XML 查詢的結果</span><span class="sxs-lookup"><span data-stu-id="0532f-121">Querying results of a FOR XML query</span></span>  
 <span data-ttu-id="0532f-122">FOR XML 查詢會傳回 XML。</span><span class="sxs-lookup"><span data-stu-id="0532f-122">The FOR XML queries return XML.</span></span> <span data-ttu-id="0532f-123">因此，您可以將 `xml` 類型方法 (例如 `query()` 與 `value()`) 套用至 FOR XML 查詢所傳回的 XML 結果。</span><span class="sxs-lookup"><span data-stu-id="0532f-123">Therefore, you can apply `xml` type methods, such as `query()` and `value()`, to the XML result returned by FOR XML queries.</span></span>  
  
 <span data-ttu-id="0532f-124">在下列查詢中，`xml` 資料類型的 `query()` 方法是用以查詢 `FOR XML` 查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="0532f-124">In the following query, the `query()` method of the `xml` data type is used to query the result of the `FOR XML` query.</span></span> <span data-ttu-id="0532f-125">如需詳細資訊，請參閱 [query&#40;&#41; 方法 &#40;xml 資料類型&#41;](/sql/t-sql/xml/query-method-xml-data-type)。</span><span class="sxs-lookup"><span data-stu-id="0532f-125">For more information, see [query&#40;&#41; Method &#40;xml Data Type&#41;](/sql/t-sql/xml/query-method-xml-data-type).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT (SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
DECLARE namespace aci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
DECLARE namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumbers  
FROM Person.Person  
FOR XML AUTO, TYPE).query('/Person.Person[1]');  
```  
  
 <span data-ttu-id="0532f-126">內部 `SELECT ... FOR XML` 查詢會傳回 `xml` 類型結果，以利外部 `SELECT` 將 `query()` 方法套用至 `xml` 類型。</span><span class="sxs-lookup"><span data-stu-id="0532f-126">The inner `SELECT ... FOR XML` query returns an `xml` type result to which the outer `SELECT` applies the `query()` method to the `xml` type.</span></span> <span data-ttu-id="0532f-127">請注意已指定 `TYPE` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="0532f-127">Note the `TYPE` directive specified.</span></span>  
  
 <span data-ttu-id="0532f-128">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="0532f-128">This is the result:</span></span>  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="S??nchez">`  
  
 `<PhoneNumbers>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">111-111-1111</act:number>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">112-111-1111</act:number>`  
  
 `</PhoneNumbers>`  
  
 `</Person.Person>`  
  
 <span data-ttu-id="0532f-129">在下列查詢中，`xml` 資料類型的 `value()` 方法是用以擷取 `SELECT...FOR XML` 查詢所傳回的 XML 結果。</span><span class="sxs-lookup"><span data-stu-id="0532f-129">In the following query, the `value()` method of the `xml` data type is used to retrieve a value from the XML result returned by the `SELECT...FOR XML` query.</span></span> <span data-ttu-id="0532f-130">如需詳細資訊，請參閱 [value&#40;&#41; 方法 &#40;xml 資料類型&#41;](/sql/t-sql/xml/value-method-xml-data-type)。</span><span class="sxs-lookup"><span data-stu-id="0532f-130">For more information, see [value&#40;&#41; Method &#40;xml Data Type&#41;](/sql/t-sql/xml/value-method-xml-data-type).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @FirstPhoneFromAdditionalContactInfo varchar(40);  
SELECT @FirstPhoneFromAdditionalContactInfo =   
 ( SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace aci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
   //act:telephoneNumber/act:number  
   ') AS PhoneNumbers  
   FROM Person.Person Contact  
   FOR XML AUTO, TYPE).value('  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
  /Contact[@BusinessEntityID="1"][1]/PhoneNumbers[1]/act:number[1]', 'varchar(40)'  
 )  
SELECT @FirstPhoneFromAdditionalContactInfo;  
```  
  
 <span data-ttu-id="0532f-131">在 `value()` 方法中的 XQuery 路徑運算式會擷取客戶連絡人之 `BusinessEntityID` 為 `1`的第一個客戶電話號碼。</span><span class="sxs-lookup"><span data-stu-id="0532f-131">The XQuery path expression in the `value()` method retrieves the first telephone number of a customer contact whose `BusinessEntityID` is `1`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0532f-132">如果未指定 TYPE 指示詞，FOR XML 查詢結果會以 `nvarchar(max)` 類型傳回。</span><span class="sxs-lookup"><span data-stu-id="0532f-132">If the TYPE directive is not specified, the FOR XML query result is returned as type `nvarchar(max)`.</span></span>  
  
### <a name="using-for-xml-query-results-in-insert-update-and-delete-transact-sql-dml"></a><span data-ttu-id="0532f-133">使用 INSERT、UPDATE 及 DELETE 中的 FOR XML 查詢結果 (Transact-SQL DML)</span><span class="sxs-lookup"><span data-stu-id="0532f-133">Using FOR XML query results in INSERT, UPDATE, and DELETE (Transact-SQL DML)</span></span>  
 <span data-ttu-id="0532f-134">下列範例示範如何在「資料管理語言」(DML) 陳述式中使用 FOR XML 查詢。</span><span class="sxs-lookup"><span data-stu-id="0532f-134">The following example demonstrates how FOR XML queries can be used in Data Manipulation Language (DML) statements.</span></span> <span data-ttu-id="0532f-135">在下列範例中，`FOR XML` 會傳回 `xml` 類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0532f-135">In the example, the `FOR XML` returns an instance of `xml` type.</span></span> <span data-ttu-id="0532f-136">`INSERT` 陳述式會將此 XML 插入資料表中。</span><span class="sxs-lookup"><span data-stu-id="0532f-136">The `INSERT` statement inserts this XML into a table.</span></span>  
  
```  
CREATE TABLE T1(intCol int, XmlCol xml);  
GO  
INSERT INTO T1   
VALUES(1, '<Root><ProductDescription ProductModelID="1" /></Root>');  
GO  
  
CREATE TABLE T2(XmlCol xml)  
GO  
INSERT INTO T2(XmlCol)   
SELECT (SELECT XmlCol.query('/Root')   
        FROM T1   
        FOR XML AUTO,TYPE);   
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="0532f-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0532f-137">See Also</span></span>  
 [<span data-ttu-id="0532f-138">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0532f-138">FOR XML &#40;SQL Server&#41;</span></span>](../xml/for-xml-sql-server.md)  
  
  
