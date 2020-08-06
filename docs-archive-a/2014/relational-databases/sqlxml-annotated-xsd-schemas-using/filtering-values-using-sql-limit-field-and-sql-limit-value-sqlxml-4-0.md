---
title: 使用 sql： limit-field 和 sql： limit-value (SQLXML 4.0) 來篩選值 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, filtering values
- limiting values [SQLXML]
- limit-value annotation
- limit-field annotation
- sql:limit-field
- sql:limit-value
- filtering [SQLXML]
ms.assetid: c0f7ae92-eeec-430e-a66a-f22c3ae64a5e
author: rothja
ms.author: jroth
ms.openlocfilehash: 7886a9a6f51c76ed693576ca6f4659f4051d1f20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709034"
---
# <a name="filtering-values-using-sqllimit-field-and-sqllimit-value-sqlxml-40"></a><span data-ttu-id="642fa-102">使用 sql:limit-field 和 sql:limit-value 篩選值 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="642fa-102">Filtering Values Using sql:limit-field and sql:limit-value (SQLXML 4.0)</span></span>
  <span data-ttu-id="642fa-103">您可以根據特定的限制值來限制從資料庫查詢傳回的資料列。</span><span class="sxs-lookup"><span data-stu-id="642fa-103">You can limit rows that are returned from a database query on the basis of some limiting value.</span></span> <span data-ttu-id="642fa-104">`sql:limit-field` 和 `sql:limit-value` 註解用於識別包含限制值的資料庫資料行，以及指定篩選所傳回之資料所使用的特定限制值。</span><span class="sxs-lookup"><span data-stu-id="642fa-104">The `sql:limit-field` and `sql:limit-value` annotations are used to identify the database column that contains limiting values and to specify a specific limiting value to be used to filter the data returned.</span></span>  
  
 <span data-ttu-id="642fa-105">`sql:limit-field` 註解用於識別包含限制值的資料行；該註解可在每個對應的元素或屬性上使用。</span><span class="sxs-lookup"><span data-stu-id="642fa-105">The `sql:limit-field` annotation is used to identify a column that contains a limiting value; it is allowed on each mapped element or attribute.</span></span>  
  
 <span data-ttu-id="642fa-106">`sql:limit-value` 註解用於指定 `sql:limit-field` 註解中所指定之資料行中的限制值。</span><span class="sxs-lookup"><span data-stu-id="642fa-106">The `sql:limit-value` annotation is used to specify the limited value in the column that is specified in the `sql:limit-field` annotation.</span></span> <span data-ttu-id="642fa-107">`sql:limit-value` 註解是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="642fa-107">The `sql:limit-value` annotation is optional.</span></span> <span data-ttu-id="642fa-108">如果未指定 `sql:limit-value`，則會假設 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="642fa-108">If `sql:limit-value` is not specified, a NULL value is assumed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="642fa-109">使用 `sql:limit-field` (其中對應的 SQL 資料行屬於 `real` 類型) 時，SQLXML 4.0 會針對 XML 結構描述中指定的 `sql:limit-value` 執行轉換，做為 `nvarchar` 指定的值。</span><span class="sxs-lookup"><span data-stu-id="642fa-109">When working with a `sql:limit-field` where the mapped SQL column is of type `real`, SQLXML 4.0 performs conversion on the `sql:limit-value` as specified in XML schemas as an `nvarchar` specified value.</span></span> <span data-ttu-id="642fa-110">這需要使用完整的科學記號標記法指定十進位限制值。</span><span class="sxs-lookup"><span data-stu-id="642fa-110">This requires that decimal limit values be specified using full scientific notation.</span></span> <span data-ttu-id="642fa-111">如需詳細資訊，請參閱下列範例 B。</span><span class="sxs-lookup"><span data-stu-id="642fa-111">For more information, see Example B below.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="642fa-112">範例</span><span class="sxs-lookup"><span data-stu-id="642fa-112">Examples</span></span>  
 <span data-ttu-id="642fa-113">若要使用這些範例建立工作範例，您必須已經安裝下列項目：</span><span class="sxs-lookup"><span data-stu-id="642fa-113">To create working samples using these examples, you need to have the following installed:</span></span>  
  
-   <span data-ttu-id="642fa-114">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span><span class="sxs-lookup"><span data-stu-id="642fa-114">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span></span>  
  
-   <span data-ttu-id="642fa-115">MDAC 2.6 或更新版本</span><span class="sxs-lookup"><span data-stu-id="642fa-115">MDAC 2.6 or later</span></span>  
  
 <span data-ttu-id="642fa-116">在這些範例中，這些範本用於針對對應 XSD 結構描述指定 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="642fa-116">In these examples, templates are used to specify XPath queries against the mapping XSD schema.</span></span>  
  
### <a name="a-limiting-the-customer-addresses-returned-to-a-specific-address-type"></a><span data-ttu-id="642fa-117">A.</span><span class="sxs-lookup"><span data-stu-id="642fa-117">A.</span></span> <span data-ttu-id="642fa-118">將傳回的客戶地址限制為特定的地址類型</span><span class="sxs-lookup"><span data-stu-id="642fa-118">Limiting the customer addresses returned to a specific address type</span></span>  
 <span data-ttu-id="642fa-119">在這個範例中，資料庫包含兩個資料表：</span><span class="sxs-lookup"><span data-stu-id="642fa-119">In this example, a database contains two tables:</span></span>  
  
-   <span data-ttu-id="642fa-120">Customer (CustomerID, CompanyName)</span><span class="sxs-lookup"><span data-stu-id="642fa-120">Customer (CustomerID, CompanyName)</span></span>  
  
-   <span data-ttu-id="642fa-121">Addresses (CustomerID, AddressType, StreetAddress)</span><span class="sxs-lookup"><span data-stu-id="642fa-121">Addresses (CustomerID, AddressType, StreetAddress)</span></span>  
  
 <span data-ttu-id="642fa-122">一個客戶可以有一個送貨地址和/或一個帳單地址。</span><span class="sxs-lookup"><span data-stu-id="642fa-122">A customer can have a shipping address and/or a billing address.</span></span> <span data-ttu-id="642fa-123">AddressType 資料行值為 Shipping 和 Billing。</span><span class="sxs-lookup"><span data-stu-id="642fa-123">The AddressType column values are Shipping and Billing.</span></span>  
  
 <span data-ttu-id="642fa-124">這是對應的架構，其中**ShipTo**架構屬性會對應至位址關聯中的 StreetAddress 資料行。</span><span class="sxs-lookup"><span data-stu-id="642fa-124">This is the mapping schema in which the **ShipTo** schema attribute maps to the StreetAddress column in the Addresses relation.</span></span> <span data-ttu-id="642fa-125">針對此屬性傳回的值會透過指定 `sql:limit-field` 和 `sql:limit-value` 註解，僅限於送貨地址。</span><span class="sxs-lookup"><span data-stu-id="642fa-125">The values that are returned for this attribute are limited to only shipping addresses by specifying the `sql:limit-field` and `sql:limit-value` annotations.</span></span> <span data-ttu-id="642fa-126">同樣地， **BillTo**架構屬性只會傳回客戶的帳單位址。</span><span class="sxs-lookup"><span data-stu-id="642fa-126">Similarly, the **BillTo** schema attribute returns only the billing address of a customer.</span></span>  
  
 <span data-ttu-id="642fa-127">這是結構描述：</span><span class="sxs-lookup"><span data-stu-id="642fa-127">This is the schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustAddr"  
        parent="Customer"  
        parent-key="CustomerID"  
        child="Addresses"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Customer" >  
   <xsd:complexType>  
        <xsd:sequence>  
        <xsd:element name="BillTo"   
                       type="xsd:string"   
                       sql:relation="Addresses"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="billing"  
                       sql:relationship="CustAddr" >  
        </xsd:element>  
        <xsd:element name="ShipTo"   
                       type="xsd:string"   
                       sql:relation="Addresses"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="shipping"  
                       sql:relationship="CustAddr" >  
        </xsd:element>  
        </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:int" />   
        <xsd:attribute name="CompanyName"  type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="642fa-128">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="642fa-128">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="642fa-129">在**tempdb**資料庫中建立兩個數據表：</span><span class="sxs-lookup"><span data-stu-id="642fa-129">Create two tables in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Customer (CustomerID int primary key,   
                           CompanyName varchar(30))  
    CREATE TABLE Addresses(CustomerID int,   
                           StreetAddress varchar(50),  
                           AddressType varchar(10))  
    ```  
  
2.  <span data-ttu-id="642fa-130">加入範例資料：</span><span class="sxs-lookup"><span data-stu-id="642fa-130">Add the sample data:</span></span>  
  
    ```  
    INSERT INTO Customer values (1, 'Company A')  
    INSERT INTO Customer values (2, 'Company B')  
  
    INSERT INTO Addresses values  
               (1, 'Obere Str. 57 Berlin', 'billing')  
    INSERT INTO Addresses values  
               (1, 'Avda. de la Constituci??n 2222 M??xico D.F.', 'shipping')  
    INSERT INTO Addresses values  
               (2, '120 Hanover Sq., London', 'billing')  
    INSERT INTO Addresses values  
               (2, 'Forsterstr. 57, Mannheim', 'shipping')  
    ```  
  
3.  <span data-ttu-id="642fa-131">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="642fa-131">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="642fa-132">將此檔案儲存為 LimitFieldValue.xml。</span><span class="sxs-lookup"><span data-stu-id="642fa-132">Save the file as LimitFieldValue.xml.</span></span>  
  
4.  <span data-ttu-id="642fa-133">建立下列範本 (LimitFieldValueT.xml)，並將其儲存在先前步驟中儲存結構描述 (LimitFieldValue.xml) 的相同位置：</span><span class="sxs-lookup"><span data-stu-id="642fa-133">Create the following template (LimitFieldValueT.xml), and save it in the same where you saved the schema (LimitFieldValue.xml) in the previous step:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="LimitFieldValue.xml">  
            /Customer  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="642fa-134">為對應結構描述 (LimitFieldValue.xml) 指定的目錄路徑，是儲存範本之目錄的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="642fa-134">The directory path specified for the mapping schema (LimitFieldValue.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="642fa-135">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="642fa-135">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\LimitFieldValue.xml"  
    ```  
  
5.  <span data-ttu-id="642fa-136">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="642fa-136">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="642fa-137">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="642fa-137">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="642fa-138">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="642fa-138">This is the result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer CustomerID="1" CompanyName="Company A">   
     <BillTo>Obere Str. 57 Berlin</BillTo>   
     <ShipTo>Avda. de la Constituci??n 2222 M??xico D.F.</ShipTo>   
  </Customer>   
  <Customer CustomerID="2" CompanyName="Company B">   
     <BillTo>120 Hanover Sq., London</BillTo>   
     <ShipTo>Forsterstr. 57, Mannheim</ShipTo>   
   </Customer>   
</ROOT>  
```  
  
### <a name="b-limiting-results-based-on-a-discount-value-of-type-real-data"></a><span data-ttu-id="642fa-139">B.</span><span class="sxs-lookup"><span data-stu-id="642fa-139">B.</span></span> <span data-ttu-id="642fa-140">根據實數資料類型的折扣值限制結果</span><span class="sxs-lookup"><span data-stu-id="642fa-140">Limiting results based on a discount value of type real data</span></span>  
 <span data-ttu-id="642fa-141">在這個範例中，資料庫包含兩個資料表：</span><span class="sxs-lookup"><span data-stu-id="642fa-141">In this example, a database contains two tables:</span></span>  
  
-   <span data-ttu-id="642fa-142">Orders (OrderID)</span><span class="sxs-lookup"><span data-stu-id="642fa-142">Orders (OrderID)</span></span>  
  
-   <span data-ttu-id="642fa-143">OrderDetails (OrderID, ProductID, UnitPrice, Quantity, Price, Discount)</span><span class="sxs-lookup"><span data-stu-id="642fa-143">OrderDetails (OrderID, ProductID, UnitPrice, Quantity, Price, Discount)</span></span>  
  
 <span data-ttu-id="642fa-144">這是對應的架構，其中訂單詳細資料上的 **「訂單」屬性會**對應到 orders 關聯中的「訂單」資料行。</span><span class="sxs-lookup"><span data-stu-id="642fa-144">This is the mapping schema in which the **OrderID** attribute on the order details maps to the OrderID column in the orders relation.</span></span> <span data-ttu-id="642fa-145">針對此屬性傳回的值僅限於值為 2.0000000 e-001 (0.2) 使用和注釋所指定的**折扣**屬性 `sql:limit-field` `sql:limit-value` 。</span><span class="sxs-lookup"><span data-stu-id="642fa-145">The values that are returned for this attribute are limited to only those that have a value of 2.0000000e-001 (0.2) as specified for the **Discount** attribute using the `sql:limit-field` and `sql:limit-value` annotations.</span></span>  
  
 <span data-ttu-id="642fa-146">這是結構描述：</span><span class="sxs-lookup"><span data-stu-id="642fa-146">This is the schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
   <xsd:appinfo>  
    <sql:relationship name="OrderOrderDetails"  
        parent="Orders"  
        parent-key="OrderID"  
        child="OrderDetails"  
        child-key="OrderID" />  
   </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="root" sql:is-constant="1">  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="Order" sql:relation="Orders" >  
          <xsd:complexType>  
             <xsd:sequence>  
                <xsd:element name="orderDetail"   
                       sql:relation="OrderDetails"   
                       sql:limit-field="Discount"                       sql:limit-value="2.0000000e-001"  
                       sql:relationship="OrderOrderDetails">  
                   <xsd:complexType>  
                     <xsd:attribute name="OrderID"   />   
                     <xsd:attribute name="ProductID" />   
                     <xsd:attribute name="Discount"  />   
                     <xsd:attribute name="Quantity"  />   
                     <xsd:attribute name="UnitPrice" />   
                   </xsd:complexType>  
                </xsd:element>  
            </xsd:sequence>  
           <xsd:attribute name="OrderID"/>   
          </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
   </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="642fa-147">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="642fa-147">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="642fa-148">在**tempdb**資料庫中建立兩個數據表：</span><span class="sxs-lookup"><span data-stu-id="642fa-148">Create two tables in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Orders ([OrderID] int NOT NULL ) ON [PRIMARY]  
    ALTER TABLE Orders WITH NOCHECK ADD   
    CONSTRAINT [PK_Orders] PRIMARY KEY  CLUSTERED (  
       [OrderID]  
     )  ON [PRIMARY]   
    CREATE TABLE [OrderDetails] (  
       [OrderID] int NOT NULL ,  
       [ProductID] int NOT NULL ,  
       [UnitPrice] money NULL ,  
       [Quantity] smallint NOT NULL ,  
       [Discount] real NOT NULL   
    ) ON [PRIMARY]  
    ```  
  
2.  <span data-ttu-id="642fa-149">加入範例資料：</span><span class="sxs-lookup"><span data-stu-id="642fa-149">Add the sample data:</span></span>  
  
    ```  
    INSERT INTO Orders ([OrderID]) values (10248)  
    INSERT INTO Orders ([OrderID]) values (10250)  
    INSERT INTO Orders ([OrderID]) values (10251)  
    INSERT INTO Orders ([OrderID]) values (10257)  
    INSERT INTO Orders ([OrderID]) values (10258)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10248,11,14,12,0)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10250,51,42.4,35,0.15)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10251,22,16.8,6,0.05)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10257,77,10.4,15,0)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10258,2,15.2,50,0.2)  
    ```  
  
3.  <span data-ttu-id="642fa-150">將結構描述 (LimitFieldValue.xml) 儲存在目錄中。</span><span class="sxs-lookup"><span data-stu-id="642fa-150">Save the schema (LimitFieldValue.xml) in a directory.</span></span>  
  
4.  <span data-ttu-id="642fa-151">複製下列測試指令碼 (TestQuery.vbs)、將 MyServer 修改為您 SQL Server 電腦的名稱，然後將其儲存在先前步驟中儲存結構描述所使用的相同目錄中：</span><span class="sxs-lookup"><span data-stu-id="642fa-151">Create the following test script (TestQuery.vbs), modify MyServer to the name of your SQL Server computer and save it in the same directory as you used in the previous step to save the schema:</span></span>  
  
    ```  
    Set conn = CreateObject("ADODB.Connection")  
    conn.Open "Provider=SQLOLEDB;Data Source=MyServer;Database=tempdb;Integrated Security=SSPI"  
    conn.Properties("SQLXML Version") = "sqlxml.4.0"   
    Set cmd = CreateObject("ADODB.Command")  
    Set stm = CreateObject("ADODB.Stream")  
    Set cmd.ActiveConnection = conn  
    stm.open  
    result ="none"  
    strXPathQuery="/root"  
    DBGUID_XPATH = "{EC2A4293-E898-11D2-B1B7-00C04F680C56}"  
    cmd.Dialect = DBGUID_XPATH  
    cmd.CommandText = strXPathQuery  
    cmd.Properties("Mapping schema") = "LimitFieldReal.xml"  
    cmd.Properties("Output Stream").Value = stm  
    cmd.Properties("Output Encoding") = "utf-8"  
    WScript.Echo "executing for xml query"  
    On Error Resume Next  
    cmd.Execute , ,1024  
    if err then  
    Wscript.Echo err.description  
    Wscript.Echo err.Number  
    Wscript.Echo err.source  
    On Error GoTo 0  
    else  
    stm.Position = 0  
    result  = stm.ReadText  
    end if  
    WScript.Echo result  
    Wscript.Echo "done"  
    ```  
  
5.  <span data-ttu-id="642fa-152">在 [Windows 檔案總管] 中按一下 TestQuery.vbs 檔案來執行它。</span><span class="sxs-lookup"><span data-stu-id="642fa-152">Execute the TestQuery.vbs file by clicking on it in Windows Explorer.</span></span>  
  
     <span data-ttu-id="642fa-153">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="642fa-153">This is the result:</span></span>  
  
    ```  
    <root>  
      <Order OrderID="10248"/>  
      <Order OrderID="10250"/>  
      <Order OrderID="10251"/>  
      <Order OrderID="10257"/>  
      <Order OrderID="10258">  
        <orderDetail OrderID="10258"   
                     ProductID="2"   
                     Discount="0.2"   
                     Quantity="50"/>  
      </Order>  
    </root>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="642fa-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="642fa-154">See Also</span></span>  
 <span data-ttu-id="642fa-155">[float 和 real &#40;Transact-sql&#41;](/sql/t-sql/data-types/float-and-real-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="642fa-155">[float and real &#40;Transact-SQL&#41;](/sql/t-sql/data-types/float-and-real-transact-sql) </span></span>  
 <span data-ttu-id="642fa-156">[Nchar 和 Nvarchar &#40;Transact-sql&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="642fa-156">[nchar and nvarchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql) </span></span>  
 <span data-ttu-id="642fa-157">[安裝 SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md) </span><span class="sxs-lookup"><span data-stu-id="642fa-157">[Installing SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md) </span></span>  
 [<span data-ttu-id="642fa-158">在查詢中使用批註式 XSD 架構 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="642fa-158">Using Annotated XSD Schemas in Queries &#40;SQLXML 4.0&#41;</span></span>](../../relational-databases/sqlxml/annotated-xsd-schemas/using-annotated-xsd-schemas-in-queries-sqlxml-4-0.md)  
  
  
