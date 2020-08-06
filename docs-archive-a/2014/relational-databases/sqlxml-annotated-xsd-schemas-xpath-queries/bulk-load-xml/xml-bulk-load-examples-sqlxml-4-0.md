---
title: XML 大量載入範例 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- overflow-field annotation
- ConnectionCommand property
- XMLFragment property
- relationship chains [SQLXML]
- multiple table bulk loading
- examples [SQLXML], XML Bulk Load
- overflow data [SQLXML]
- sql:datatype
- transaction mode [SQLXML]
- CheckConstraints property
- sql:overflow-field
- XML Bulk Load [SQLXML], examples
- TempFilePath property
- datatype annotation
- Transaction property
- KeepIdentity property
- Execute method
- streaming XML data
- xml data type [SQL Server], SQLXML
- bulk load [SQLXML], examples
ms.assetid: 970e4553-b41d-4a12-ad50-0ee65d1f305d
author: rothja
ms.author: jroth
ms.openlocfilehash: c7eaec77ef068efd28c4da65833afa5047b222f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686870"
---
# <a name="xml-bulk-load-examples-sqlxml-40"></a><span data-ttu-id="675d3-102">XML 大量載入範例 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="675d3-102">XML Bulk Load Examples (SQLXML 4.0)</span></span>
  <span data-ttu-id="675d3-103">下列範例說明 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的 XML 大量載入功能。</span><span class="sxs-lookup"><span data-stu-id="675d3-103">The following examples illustrate the XML Bulk Load functionality in Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="675d3-104">每個範例都會提供一個 XSD 結構描述及其等同的 XDR 結構描述。</span><span class="sxs-lookup"><span data-stu-id="675d3-104">Each example provides an XSD schema and its equivalent XDR schema.</span></span>  
  
## <a name="bulk-loader-script-validateandbulkloadvbs"></a><span data-ttu-id="675d3-105">大量載入程式指令碼 (ValidateAndBulkload.vbs)</span><span class="sxs-lookup"><span data-stu-id="675d3-105">Bulk Loader Script (ValidateAndBulkload.vbs)</span></span>  
 <span data-ttu-id="675d3-106">下列在 Visual Basic Scripting Edition 中撰寫的腳本 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] (VBScript) ，會將 xml 檔載入到 XML DOM; 針對架構進行驗證; 而且，如果檔是有效的，則會執行 xml 大量載入，以將 xml 載入 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="675d3-106">The following script, written in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript), loads an XML document into the XML DOM; validates it against a schema; and, if the document is valid, executes an XML bulk load to load the XML into a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="675d3-107">此指令碼可以搭配本主題稍後所參考的每個個別範例使用。</span><span class="sxs-lookup"><span data-stu-id="675d3-107">This script can be used with each of the individual examples that refer to it later in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="675d3-108">如果沒有從資料檔上傳任何內容，XML 大量載入不會擲回警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="675d3-108">XML Bulk Load does not throw a warning or an error if no content is uploaded from the data file.</span></span> <span data-ttu-id="675d3-109">因此，最好在執行大量載入作業之前，先驗證您的 XML 資料檔。</span><span class="sxs-lookup"><span data-stu-id="675d3-109">Therefore, it is a good practice to validate your XML data file prior to executing a bulk load operation.</span></span>  
  
```  
Dim FileValid  
  
set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
objBL.ConnectionString = "provider=SQLOLEDB;data source=MyServer;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile = "c:\error.log"  
  
'Validate the data file prior to bulkload  
Dim sOutput   
sOutput = ValidateFile("SampleXMLData.xml", "", "SampleSchema.xml")  
WScript.Echo sOutput  
  
If FileValid Then  
   ' Check constraints and initiate transaction (if needed)  
   ' objBL.CheckConstraints = True  
   ' objBL.Transaction=True  
  'Execute XML bulkload using file.  
  objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
  set objBL=Nothing  
End If  
  
Function ValidateFile(strXmlFile,strUrn,strXsdFile)  
  
   ' Create a schema cache and add SampleSchema.xml to it.  
   Dim xs, fso, sAppPath  
   Set fso = CreateObject("Scripting.FileSystemObject")   
   Set xs = CreateObject("MSXML2.XMLSchemaCache.6.0")  
   sAppPath = fso.GetFolder(".")   
   xs.Add strUrn, sAppPath & "\" & strXsdFile  
  
   ' Create an XML DOMDocument object.  
   Dim xd   
   Set xd = CreateObject("MSXML2.DOMDocument.6.0")  
  
   ' Assign the schema cache to the DOM document.  
   ' schemas collection.  
   Set xd.schemas = xs  
  
   ' Load XML document as DOM document.  
   xd.async = False  
   xd.Load sAppPath & "\" & strXmlFile  
  
   ' Return validation results in message to the user.  
   If xd.parseError.errorCode <> 0 Then  
        ValidateFile = "Validation failed on " & _  
             strXmlFile & vbCrLf & _  
             "=======" & vbCrLf & _  
             "Reason: " & xd.parseError.reason & _  
             vbCrLf & "Source: " & _  
             xd.parseError.srcText & _  
             vbCrLf & "Line: " & _  
             xd.parseError.Line & vbCrLf  
             FileValid = False  
    Else  
        ValidateFile = "Validation succeeded for " & _  
             strXmlFile & vbCrLf & _  
             "========" & _  
             vbCrLf & "Contents to be bulkloaded" & vbCrLf  
             FileValid = True  
    End If  
End Function  
```  
  
## <a name="a-bulk-loading-xml-in-a-table"></a><span data-ttu-id="675d3-110">A.</span><span class="sxs-lookup"><span data-stu-id="675d3-110">A.</span></span> <span data-ttu-id="675d3-111">將 XML 大量載入到資料表中</span><span class="sxs-lookup"><span data-stu-id="675d3-111">Bulk loading XML in a table</span></span>  
 <span data-ttu-id="675d3-112">這個範例會建立在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ConnectionString 屬性中指定之實例的連接， (MyServer) 。</span><span class="sxs-lookup"><span data-stu-id="675d3-112">This example establishes a connection to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is specified in the ConnectionString property (MyServer).</span></span> <span data-ttu-id="675d3-113">此範例也會指定 ErrorLogFile 屬性。</span><span class="sxs-lookup"><span data-stu-id="675d3-113">The example also specifies the ErrorLogFile property.</span></span> <span data-ttu-id="675d3-114">因此，錯誤輸出會儲存在指定的檔案 ("C:\error.log") 中，您也可以決定變更到不同的位置。</span><span class="sxs-lookup"><span data-stu-id="675d3-114">Therefore, the error output is saved in the specified file ("C:\error.log"), which you might also decide to change to a different location.</span></span> <span data-ttu-id="675d3-115">同時也請注意，Execute 方法的參數都是對應架構檔案 ( # A0) 和 XML 資料檔案 ( # A1) 。</span><span class="sxs-lookup"><span data-stu-id="675d3-115">Notice also that the Execute method has as its parameters both the mapping schema file (SampleSchema.xml) and the XML data file (SampleXMLData.xml).</span></span> <span data-ttu-id="675d3-116">當大量載入執行時，您在**tempdb**資料庫中建立的「使用者」資料表會根據 XML 資料檔案的內容包含新的記錄。</span><span class="sxs-lookup"><span data-stu-id="675d3-116">When the bulk load executes, the Cust table you have created in **tempdb** database will contain new records based upon the contents of the XML data file.</span></span>  
  
#### <a name="to-test-a-sample-bulk-load"></a><span data-ttu-id="675d3-117">測試大量載入範例</span><span class="sxs-lookup"><span data-stu-id="675d3-117">To test a sample bulk load</span></span>  
  
1.  <span data-ttu-id="675d3-118">建立下述資料表：</span><span class="sxs-lookup"><span data-stu-id="675d3-118">Create this table:</span></span>  
  
    ```  
    CREATE TABLE Cust(CustomerID  int PRIMARY KEY,  
                      CompanyName varchar(20),  
                      City        varchar(20));  
    GO  
    ```  
  
2.  <span data-ttu-id="675d3-119">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="675d3-119">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="675d3-120">將下列 XSD 結構描述加入到此檔案中：</span><span class="sxs-lookup"><span data-stu-id="675d3-120">To this file, add the following XSD schema:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
       <xsd:element name="ROOT" sql:is-constant="1" >  
         <xsd:complexType>  
           <xsd:sequence>  
             <xsd:element name="Customers" sql:relation="Cust" maxOccurs="unbounded">  
               <xsd:complexType>  
                 <xsd:sequence>  
                   <xsd:element name="CustomerID"  type="xsd:integer" />  
                   <xsd:element name="CompanyName" type="xsd:string" />  
                   <xsd:element name="City"        type="xsd:string" />  
                 </xsd:sequence>  
               </xsd:complexType>  
             </xsd:element>  
           </xsd:sequence>  
          </xsd:complexType>  
         </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="675d3-121">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 SampleXMLData.xml。</span><span class="sxs-lookup"><span data-stu-id="675d3-121">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="675d3-122">將下列 XML 文件加入到此檔案中：</span><span class="sxs-lookup"><span data-stu-id="675d3-122">To this file, add the following XML document:</span></span>  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Sean Chai</CompanyName>  
        <City>New York</City>  
      </Customers>  
      <Customers>  
        <CustomerID>1112</CustomerID>  
        <CompanyName>Tom Johnston</CompanyName>  
         <City>Los Angeles</City>  
      </Customers>  
      <Customers>  
        <CustomerID>1113</CustomerID>  
        <CompanyName>Institute of Art</CompanyName>  
        <City>Chicago</City>  
      </Customers>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="675d3-123">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 ValidateAndBulkload.vbs。</span><span class="sxs-lookup"><span data-stu-id="675d3-123">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="675d3-124">將本主題開頭提供的 VBScript 程式碼加入到此檔案中。</span><span class="sxs-lookup"><span data-stu-id="675d3-124">To this file, add the VBScript code that is provided above at the beginning of this topic.</span></span> <span data-ttu-id="675d3-125">修改連接字串以提供適當的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="675d3-125">Modify the connection string to provide the appropriate server name.</span></span> <span data-ttu-id="675d3-126">針對指定為 Execute 方法參數的檔案指定適當的路徑。</span><span class="sxs-lookup"><span data-stu-id="675d3-126">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span>  
  
5.  <span data-ttu-id="675d3-127">執行 VBScript 程式碼。</span><span class="sxs-lookup"><span data-stu-id="675d3-127">Execute the VBScript code.</span></span> <span data-ttu-id="675d3-128">XML 大量載入會將 XML 載入到 Cust 資料表中。</span><span class="sxs-lookup"><span data-stu-id="675d3-128">XML Bulk Load loads the XML into the Cust table.</span></span>  
  
 <span data-ttu-id="675d3-129">這是相等的 XDR 結構描述：</span><span class="sxs-lookup"><span data-stu-id="675d3-129">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers"  sql:relation="Cust" >  
      <element type="CustomerID"  sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City"        sql:field="City" />  
  
   </ElementType>  
</Schema>  
```  
  
## <a name="b-bulk-loading-xml-data-in-multiple-tables"></a><span data-ttu-id="675d3-130">B.</span><span class="sxs-lookup"><span data-stu-id="675d3-130">B.</span></span> <span data-ttu-id="675d3-131">將 XML 資料大量載入到多個資料表中</span><span class="sxs-lookup"><span data-stu-id="675d3-131">Bulk loading XML data in multiple tables</span></span>  
 <span data-ttu-id="675d3-132">在此範例中，XML 檔是由 **\<Customer>** 和元素所組成 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="675d3-132">In this example, the XML document consists of the **\<Customer>** and **\<Order>** elements.</span></span>  
  
```  
<ROOT>  
  <Customers>  
    <CustomerID>1111</CustomerID>  
    <CompanyName>Sean Chai</CompanyName>  
    <City>NY</City>  
    <Order OrderID="1" />  
    <Order OrderID="2" />  
  </Customers>  
  <Customers>  
    <CustomerID>1112</CustomerID>  
    <CompanyName>Tom Johnston</CompanyName>  
     <City>LA</City>    
    <Order OrderID="3" />  
  </Customers>  
  <Customers>  
    <CustomerID>1113</CustomerID>  
    <CompanyName>Institute of Art</CompanyName>  
    <Order OrderID="4" />  
  </Customers>  
</ROOT>  
```  
  
 <span data-ttu-id="675d3-133">這個範例會將 XML 資料大量載入到兩個**Cust** **資料表：**</span><span class="sxs-lookup"><span data-stu-id="675d3-133">This example bulk loads the XML data into two tables, **Cust** and **CustOrder**:</span></span>  
  
```  
Cust(CustomerID, CompanyName, City)  
CustOrder(OrderID, CustomerID)  
```  
  
 <span data-ttu-id="675d3-134">下列 XSD 結構描述會定義這些資料表的 XML 檢視。</span><span class="sxs-lookup"><span data-stu-id="675d3-134">The following XSD schema defines the XML view of these tables.</span></span> <span data-ttu-id="675d3-135">架構會指定和元素之間的父子式關聯 **\<Customer>** 性 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="675d3-135">The schema specifies the parent-child relationship between the **\<Customer>** and **\<Order>** elements.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="CustCustOrder"  
          parent="Cust"  
          parent-key="CustomerID"  
          child="CustOrder"  
          child-key="CustomerID" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="ROOT" sql:is-constant="1" >  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Customers" sql:relation="Cust" >  
          <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="CustomerID"  type="xsd:integer" />  
              <xsd:element name="CompanyName" type="xsd:string" />  
              <xsd:element name="City"        type="xsd:string" />  
              <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
                <xsd:complexType>  
                  <xsd:attribute name="OrderID" type="xsd:integer" />  
                </xsd:complexType>  
              </xsd:element>  
             </xsd:sequence>  
          </xsd:complexType>  
        </xsd:element>  
      </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="675d3-136">XML 大量載入會使用上述和專案之間指定的主鍵/外鍵關聯性， **\<Cust>** **\<CustOrder>** 將資料大量載入到這兩個數據表。</span><span class="sxs-lookup"><span data-stu-id="675d3-136">XML Bulk Load uses the primary key/foreign key relationship specified above between the **\<Cust>** and **\<CustOrder>** elements to bulk load the data into both tables.</span></span>  
  
#### <a name="to-test-a-sample-bulk-load"></a><span data-ttu-id="675d3-137">測試大量載入範例</span><span class="sxs-lookup"><span data-stu-id="675d3-137">To test a sample bulk load</span></span>  
  
1.  <span data-ttu-id="675d3-138">在**tempdb**資料庫中建立兩個數據表：</span><span class="sxs-lookup"><span data-stu-id="675d3-138">Create two tables in **tempdb** database:</span></span>  
  
    ```  
    USE tempdb;  
    CREATE TABLE Cust(  
           CustomerID  int PRIMARY KEY,  
           CompanyName varchar(20),  
           City        varchar(20));  
    CREATE TABLE CustOrder(        OrderID     int PRIMARY KEY,   
            CustomerID int FOREIGN KEY REFERENCES Cust(CustomerID));  
    ```  
  
2.  <span data-ttu-id="675d3-139">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="675d3-139">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="675d3-140">將這個範例所提供的 XSD 結構描述加入到此檔案中。</span><span class="sxs-lookup"><span data-stu-id="675d3-140">Add the XSD schema that is provided in this example to the file.</span></span>  
  
3.  <span data-ttu-id="675d3-141">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 SampleData.xml。</span><span class="sxs-lookup"><span data-stu-id="675d3-141">Create a file in your preferred text or XML editor, and save it as SampleData.xml.</span></span> <span data-ttu-id="675d3-142">將這個範例先前所提供的 XML 文件加入到此檔案中。</span><span class="sxs-lookup"><span data-stu-id="675d3-142">Add the XML document that was provided earlier in this example to the file.</span></span>  
  
4.  <span data-ttu-id="675d3-143">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 ValidateAndBulkload.vbs。</span><span class="sxs-lookup"><span data-stu-id="675d3-143">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="675d3-144">將本主題開頭提供的 VBScript 程式碼加入到此檔案中。</span><span class="sxs-lookup"><span data-stu-id="675d3-144">To this file, add the VBScript code that is provided above at the beginning of this topic.</span></span> <span data-ttu-id="675d3-145">修改連接字串以提供適當的伺服器和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="675d3-145">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="675d3-146">針對指定為 Execute 方法參數的檔案指定適當的路徑。</span><span class="sxs-lookup"><span data-stu-id="675d3-146">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span>  
  
5.  <span data-ttu-id="675d3-147">執行上述的 VBScript 程式碼。</span><span class="sxs-lookup"><span data-stu-id="675d3-147">Execute the VBScript code above.</span></span> <span data-ttu-id="675d3-148">XML 大量載入會將 XML 文件載入到 Cust 和 CustOrder 資料表中。</span><span class="sxs-lookup"><span data-stu-id="675d3-148">XML Bulk Load loads the XML document into the Cust and CustOrder tables.</span></span>  
  
 <span data-ttu-id="675d3-149">這是相等的 XDR 結構描述：</span><span class="sxs-lookup"><span data-stu-id="675d3-149">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust" >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
<sql:relationship  
                key-relation="Cust"  
                key="CustomerID"  
                foreign-key="CustomerID"  
                foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
</Schema>  
```  
  
## <a name="c-using-chain-relationships-in-the-schema-to-bulk-load-xml"></a><span data-ttu-id="675d3-150">C.</span><span class="sxs-lookup"><span data-stu-id="675d3-150">C.</span></span> <span data-ttu-id="675d3-151">使用結構描述中的鏈結關聯性大量載入 XML</span><span class="sxs-lookup"><span data-stu-id="675d3-151">Using chain relationships in the schema to bulk load XML</span></span>  
 <span data-ttu-id="675d3-152">此範例說明 XML 大量載入如何使用在對應結構描述中指定的 M:N 關聯性，將代表 M:N 關聯性的資料載入到資料表中。</span><span class="sxs-lookup"><span data-stu-id="675d3-152">This example illustrates how the M:N relationship that is specified in the mapping schema is used by XML Bulk Load to load data in a table that represents an M:N relationship.</span></span>  
  
 <span data-ttu-id="675d3-153">例如，請考慮下列 XSD 結構描述：</span><span class="sxs-lookup"><span data-stu-id="675d3-153">For example, consider this XSD schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrderOD"  
          parent="Ord"  
          parent-key="OrderID"  
          child="OrderDetail"  
          child-key="OrderID" />  
  
    <sql:relationship name="ODProduct"  
          parent="OrderDetail"  
          parent-key="ProductID"  
          child="Product"  
          child-key="ProductID"   
          inverse="true"/>  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="ROOT" sql:is-constant="1" >  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Ord"   
                     sql:key-fields="OrderID" >  
          <xsd:complexType>  
            <xsd:sequence>  
             <xsd:element name="Product"  
                          sql:relation="Product"   
                          sql:key-fields="ProductID"  
                          sql:relationship="OrderOD ODProduct">  
               <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
               </xsd:complexType>  
             </xsd:element>  
           </xsd:sequence>  
           <xsd:attribute name="OrderID"   type="xsd:integer" />   
           <xsd:attribute name="CustomerID"   type="xsd:string" />  
         </xsd:complexType>  
       </xsd:element>  
      </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="675d3-154">架構會指定 **\<Order>** 具有子專案的元素 **\<Product>** 。</span><span class="sxs-lookup"><span data-stu-id="675d3-154">The schema specifies an **\<Order>** element with a **\<Product>** child element.</span></span> <span data-ttu-id="675d3-155">**\<Order>** 元素會對應至 Ord 資料表，而 **\<Product>** 元素會對應至資料庫中的 Product 資料表。</span><span class="sxs-lookup"><span data-stu-id="675d3-155">The **\<Order>** element maps to Ord table and the **\<Product>** element maps to the Product table in the database.</span></span> <span data-ttu-id="675d3-156">在元素上指定的鏈關聯性會 **\<Product>** 識別 OrderDetail 資料表所代表的 M:N 關聯性。</span><span class="sxs-lookup"><span data-stu-id="675d3-156">The chain relationship specified on the **\<Product>** element identifies a M:N relationship represented by the OrderDetail table.</span></span> <span data-ttu-id="675d3-157">(一個訂單可以包含許多產品，而一個產品可以包含在許多訂單中)。</span><span class="sxs-lookup"><span data-stu-id="675d3-157">(An order can include many products, and a product can be included in many orders.)</span></span>  
  
 <span data-ttu-id="675d3-158">當您要使用此結構描述大量載入 XML 文件時，會將記錄加入到 Ord、Product 和 OrderDetail 資料表中。</span><span class="sxs-lookup"><span data-stu-id="675d3-158">When you are bulk loading an XML document with this schema, records are added to the Ord, Product, and OrderDetail tables.</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="675d3-159">測試工作範例</span><span class="sxs-lookup"><span data-stu-id="675d3-159">To test a working sample</span></span>  
  
1.  <span data-ttu-id="675d3-160">建立三個資料表：</span><span class="sxs-lookup"><span data-stu-id="675d3-160">Create three tables:</span></span>  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int  PRIMARY KEY,  
             CustomerID  varchar(5));  
    GO  
    CREATE TABLE Product (  
             ProductID   int PRIMARY KEY,  
             ProductName varchar(20));  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID));  
    GO  
    ```  
  
2.  <span data-ttu-id="675d3-161">將這個範例在上方所提供的結構描述儲存為 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="675d3-161">Save the schema that is provided above in this example as SampleSchema.xml.</span></span>  
  
3.  <span data-ttu-id="675d3-162">將下列 XML 資料範例儲存為 SampleXMLData.xml：</span><span class="sxs-lookup"><span data-stu-id="675d3-162">Save the following sample XML data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>    
      <Order OrderID="1" CustomerID="ALFKI">  
        <Product ProductID="1" ProductName="Chai" />  
        <Product ProductID="2" ProductName="Chang" />  
      </Order>  
      <Order OrderID="2" CustomerID="ANATR">  
        <Product ProductID="3" ProductName="Aniseed Syrup" />  
        <Product ProductID="4" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="675d3-163">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 ValidateAndBulkload.vbs。</span><span class="sxs-lookup"><span data-stu-id="675d3-163">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="675d3-164">將本主題開頭提供的 VBScript 程式碼加入到此檔案中。</span><span class="sxs-lookup"><span data-stu-id="675d3-164">To this file, add the VBScript code that is provided above at the beginning of this topic.</span></span> <span data-ttu-id="675d3-165">修改連接字串以提供適當的伺服器和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="675d3-165">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="675d3-166">從此範例的原始程式碼取消註解下列幾行。</span><span class="sxs-lookup"><span data-stu-id="675d3-166">Uncomment the following lines from the source code for this example.</span></span>  
  
    ```  
    objBL.CheckConstraints = True  
    objBL.Transaction=True  
    ```  
  
5.  <span data-ttu-id="675d3-167">執行 VBScript 程式碼。</span><span class="sxs-lookup"><span data-stu-id="675d3-167">Execute the VBScript code.</span></span> <span data-ttu-id="675d3-168">XML 大量載入會將 XML 文件載入到 Ord 和 Product 資料表中。</span><span class="sxs-lookup"><span data-stu-id="675d3-168">XML Bulk Load loads the XML document into the Ord and Product tables.</span></span>  
  
## <a name="d-bulk-loading-in-identity-type-columns"></a><span data-ttu-id="675d3-169">D.</span><span class="sxs-lookup"><span data-stu-id="675d3-169">D.</span></span> <span data-ttu-id="675d3-170">大量載入識別類型資料行</span><span class="sxs-lookup"><span data-stu-id="675d3-170">Bulk loading in identity type columns</span></span>  
 <span data-ttu-id="675d3-171">此範例說明大量載入如何處理識別類型資料行。</span><span class="sxs-lookup"><span data-stu-id="675d3-171">This example illustrates how bulk load handles identity type columns.</span></span> <span data-ttu-id="675d3-172">在此範例中，資料會大量載入到三個資料表 (Ord、Product 和 OrderDetail) 中。</span><span class="sxs-lookup"><span data-stu-id="675d3-172">In the example, data is bulk loaded into three tables (Ord, Product, and OrderDetail).</span></span>  
  
 <span data-ttu-id="675d3-173">在這些資料表中：</span><span class="sxs-lookup"><span data-stu-id="675d3-173">In these tables:</span></span>  
  
-   <span data-ttu-id="675d3-174">Ord 資料表中的 OrderID 是識別類型資料行</span><span class="sxs-lookup"><span data-stu-id="675d3-174">OrderID in the Ord table is an identity type column</span></span>  
  
-   <span data-ttu-id="675d3-175">Product 資料表中的 ProductID 是識別類型資料行。</span><span class="sxs-lookup"><span data-stu-id="675d3-175">ProductID in the Product table is an identity type column.</span></span>  
  
-   <span data-ttu-id="675d3-176">OrderDetail 中的 OrderID 和 ProductID 資料行是參考 Ord 和 Product 資料表中對應主索引鍵資料行的外部索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="675d3-176">OrderID and ProductID columns in the OrderDetail are foreign key columns referring to corresponding primary key columns in the Ord and Product tables.</span></span>  
  
 <span data-ttu-id="675d3-177">下列是此範例的資料表結構描述：</span><span class="sxs-lookup"><span data-stu-id="675d3-177">The following are the table schemas for this example:</span></span>  
  
```  
Ord (OrderID, CustomerID)  
Product (ProductID, ProductName)  
OrderDetail (OrderID, ProductID)  
```  
  
 <span data-ttu-id="675d3-178">在此 XML 大量載入範例中，BulkLoad 物件模型的 KeepIdentity 屬性會設定為 false。</span><span class="sxs-lookup"><span data-stu-id="675d3-178">In this example of XML Bulk Load, the KeepIdentity property of the BulkLoad object model is set to false.</span></span> <span data-ttu-id="675d3-179">因此，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會分別在 Product 和 Ord 資料表中，為 ProductID 和 OrderID 資料行產生識別值 (系統會忽略要大量載入之文件所提供的任何值)。</span><span class="sxs-lookup"><span data-stu-id="675d3-179">Therefore, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] generates identity values for the ProductID and OrderID columns in the Product and Ord tables, respectively (any values provided in the documents to be bulk loaded are ignored).</span></span>  
  
 <span data-ttu-id="675d3-180">在此情況下，XML 大量載入會在資料表之間識別主索引鍵/外部索引鍵關聯性。</span><span class="sxs-lookup"><span data-stu-id="675d3-180">In this case, XML Bulk Load identifies the primary key/foreign key relationship among tables.</span></span> <span data-ttu-id="675d3-181">大量載入會先將記錄插入具有主索引鍵的資料表，然後再將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 所產生的識別值傳播到具有外部索引鍵資料行的資料表中。</span><span class="sxs-lookup"><span data-stu-id="675d3-181">Bulk Load first inserts records in the tables with the primary key, then propagates the identity value generated by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to the tables with foreign key columns.</span></span> <span data-ttu-id="675d3-182">在下列範例中，XML 大量載入會以下列順序，將資料插入資料表中。</span><span class="sxs-lookup"><span data-stu-id="675d3-182">In the following example, XML Bulk Load inserts data in tables in this order:</span></span>  
  
1.  <span data-ttu-id="675d3-183">產品</span><span class="sxs-lookup"><span data-stu-id="675d3-183">Product</span></span>  
  
2.  <span data-ttu-id="675d3-184">Ord</span><span class="sxs-lookup"><span data-stu-id="675d3-184">Ord</span></span>  
  
3.  <span data-ttu-id="675d3-185">OrderDetail</span><span class="sxs-lookup"><span data-stu-id="675d3-185">OrderDetail</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="675d3-186">若要傳播在 Products 和 Orders 資料表中產生的識別值，處理邏輯需要 XML 大量載入追蹤這些值，以便稍後插入 OrderDetails 資料表中。</span><span class="sxs-lookup"><span data-stu-id="675d3-186">In order to propagate identity values generated in the Products and Orders tables, the processing logic requires XML Bulk Load to keep track of these values for later insertion into the OrderDetails table.</span></span> <span data-ttu-id="675d3-187">方法是，XML 大量載入建立中繼資料表、在這些資料表中擴展資料，並在稍後移除它們。</span><span class="sxs-lookup"><span data-stu-id="675d3-187">To do that, XML Bulk Load creates intermediate tables, populates the data in these tables, and later removes them.</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="675d3-188">測試工作範例</span><span class="sxs-lookup"><span data-stu-id="675d3-188">To test a working sample</span></span>  
  
1.  <span data-ttu-id="675d3-189">建立這些資料表：</span><span class="sxs-lookup"><span data-stu-id="675d3-189">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int identity(1,1)  PRIMARY KEY,  
             CustomerID  varchar(5));  
    GO  
    CREATE TABLE Product (  
             ProductID   int identity(1,1) PRIMARY KEY,  
             ProductName varchar(20));  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID));  
    GO  
    ```  
  
2.  <span data-ttu-id="675d3-190">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="675d3-190">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="675d3-191">將這個 XSD 結構描述加入到此檔案中。</span><span class="sxs-lookup"><span data-stu-id="675d3-191">Add this XSD schema to this file.</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
     <xsd:annotation>  
       <xsd:appinfo>  
        <sql:relationship name="OrderOD"  
              parent="Ord"  
              parent-key="OrderID"  
              child="OrderDetail"  
              child-key="OrderID" />  
        <sql:relationship name="ODProduct"  
              parent="OrderDetail"  
              parent-key="ProductID"  
              child="Product"  
              child-key="ProductID"   
              inverse="true"/>  
       </xsd:appinfo>  
     </xsd:annotation>  
  
      <xsd:element name="Order" sql:relation="Ord"   
                                sql:key-fields="OrderID" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="Product" sql:relation="Product"   
                         sql:key-fields="ProductID"  
                         sql:relationship="OrderOD ODProduct">  
              <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
              </xsd:complexType>  
            </xsd:element>  
         </xsd:sequence>  
            <xsd:attribute name="OrderID"   type="xsd:integer" />   
            <xsd:attribute name="CustomerID"   type="xsd:string" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="675d3-192">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 SampleXMLData.xml。</span><span class="sxs-lookup"><span data-stu-id="675d3-192">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="675d3-193">加入下列 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="675d3-193">Add the following XML document.</span></span>  
  
    ```  
    <ROOT>    
      <Order OrderID="11" CustomerID="ALFKI">  
        <Product ProductID="11" ProductName="Chai" />  
        <Product ProductID="22" ProductName="Chang" />  
      </Order>  
      <Order OrderID="22" CustomerID="ANATR">  
         <Product ProductID="33" ProductName="Aniseed Syrup" />  
        <Product ProductID="44" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="675d3-194">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 ValidateAndBulkload.vbs。</span><span class="sxs-lookup"><span data-stu-id="675d3-194">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="675d3-195">將下列 VBScript 程式碼加入到此檔案中。</span><span class="sxs-lookup"><span data-stu-id="675d3-195">To this file, add the following VBScript code.</span></span> <span data-ttu-id="675d3-196">修改連接字串以提供適當的伺服器和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="675d3-196">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="675d3-197">針對做為方法之參數的檔案指定適當的路徑 `Execute` 。</span><span class="sxs-lookup"><span data-stu-id="675d3-197">Specify the appropriate path for the files that serve as parameters to the `Execute` method.</span></span>  
  
    ```  
    Set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "C:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Transaction = False  
    objBL.KeepIdentity = False  
    objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
    Set objBL = Nothing  
    MsgBox "Done."  
    ```  
  
5.  <span data-ttu-id="675d3-198">執行 VBScript 程式碼。</span><span class="sxs-lookup"><span data-stu-id="675d3-198">Execute the VBScript code.</span></span> <span data-ttu-id="675d3-199">XML 大量載入會將資料載入到適當的資料表中。</span><span class="sxs-lookup"><span data-stu-id="675d3-199">The XML Bulk Load will load the data into the appropriate tables.</span></span>  
  
## <a name="e-generating-table-schemas-before-bulk-loading"></a><span data-ttu-id="675d3-200">E.</span><span class="sxs-lookup"><span data-stu-id="675d3-200">E.</span></span> <span data-ttu-id="675d3-201">大量載入前產生資料表結構描述</span><span class="sxs-lookup"><span data-stu-id="675d3-201">Generating table schemas before bulk loading</span></span>  
 <span data-ttu-id="675d3-202">如果大量載入前資料表不存在，XML 大量載入可以選擇性地產生資料表。</span><span class="sxs-lookup"><span data-stu-id="675d3-202">XML Bulk Load can optionally generate the tables if they do not exist before bulk loading.</span></span> <span data-ttu-id="675d3-203">將 Sqlxmlbulkload.sqlxmlbulkload.4.0 物件的 SchemaGen 屬性設定為 TRUE 會執行此工作。</span><span class="sxs-lookup"><span data-stu-id="675d3-203">Setting the SchemaGen property of the SQLXMLBulkLoad object to TRUE does this.</span></span> <span data-ttu-id="675d3-204">您也可以選擇性地要求 XML 大量載入來卸載任何現有的資料表，並藉由將 SGDropTables 屬性設定為 TRUE 來重新建立它們。</span><span class="sxs-lookup"><span data-stu-id="675d3-204">You can also optionally request XML Bulk Load to drop any existing tables and re-create them by setting the SGDropTables property to TRUE.</span></span> <span data-ttu-id="675d3-205">下列 VBScript 範例說明這些屬性的用法。</span><span class="sxs-lookup"><span data-stu-id="675d3-205">The following VBScript example illustrates the use of these properties.</span></span>  
  
 <span data-ttu-id="675d3-206">同時，此範例會將兩個額外的屬性設定為 TRUE：</span><span class="sxs-lookup"><span data-stu-id="675d3-206">Also, this example sets two additional properties to TRUE:</span></span>  
  
-   <span data-ttu-id="675d3-207">CheckConstraints.</span><span class="sxs-lookup"><span data-stu-id="675d3-207">CheckConstraints.</span></span> <span data-ttu-id="675d3-208">將此屬性設定為 TRUE 可確保要插入資料表的資料沒有違反已經在資料表上指定的任何條件約束 (在此情況下為 Cust 和 CustOrder 資料表之間指定的 PRIMARY KEY/FOREIGN KEY 條件約束)。</span><span class="sxs-lookup"><span data-stu-id="675d3-208">Setting this property to TRUE ensures that the data being inserted into the tables does not violate any constraints that have been specified on the tables (in this case the PRIMARY KEY/FOREIGN KEY constraints specified between the Cust and CustOrder tables).</span></span> <span data-ttu-id="675d3-209">如果有條件約束違規，大量載入便會失敗。</span><span class="sxs-lookup"><span data-stu-id="675d3-209">If there is a constraint violation, the bulk load fails.</span></span>  
  
-   <span data-ttu-id="675d3-210">XMLFragment.</span><span class="sxs-lookup"><span data-stu-id="675d3-210">XMLFragment.</span></span> <span data-ttu-id="675d3-211">此屬性必須設定為 TRUE，因為 XML 文件 (資料來源) 範例不包含單一的最上層元素 (因此為片段)。</span><span class="sxs-lookup"><span data-stu-id="675d3-211">This property must be set to TRUE because the sample XML document (data source) contains no single, top-level element (and is thus a fragment).</span></span>  
  
 <span data-ttu-id="675d3-212">這是 VBScript 程式碼：</span><span class="sxs-lookup"><span data-stu-id="675d3-212">This is the VBScript code:</span></span>  
  
```  
Dim objBL   
Set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile = "c:\error.log"  
  
objBL.CheckConstraints=true  
objBL.XMLFragment = True  
objBL.SchemaGen = True  
objBL.SGDropTables = True  
  
objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
Set objBL = Nothing  
```  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="675d3-213">測試工作範例</span><span class="sxs-lookup"><span data-stu-id="675d3-213">To test a working sample</span></span>  
  
1.  <span data-ttu-id="675d3-214">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="675d3-214">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="675d3-215">將稍早範例「使用結構描述中的鏈結關聯性大量載入 XML」中提供的 XSD 結構描述加入到檔案中。</span><span class="sxs-lookup"><span data-stu-id="675d3-215">Add the XSD schema that is provided in the earlier example, "Using chain relationships in the schema to bulk load XML", to the file.</span></span>  
  
2.  <span data-ttu-id="675d3-216">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 SampleXMLData.xml。</span><span class="sxs-lookup"><span data-stu-id="675d3-216">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="675d3-217">將稍早範例「使用結構描述中的鏈結關聯性大量載入 XML」中提供的 XML 文件加入到檔案中。</span><span class="sxs-lookup"><span data-stu-id="675d3-217">Add the XML document that is provided in the earlier example, "Using chain relationships in the schema to bulk load XML", to the file.</span></span> <span data-ttu-id="675d3-218">\<ROOT>從檔 (中移除元素，使其成為) 的片段。</span><span class="sxs-lookup"><span data-stu-id="675d3-218">Remove the \<ROOT> element from the document (to make it a fragment).</span></span>  
  
3.  <span data-ttu-id="675d3-219">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 ValidateAndBulkload.vbs。</span><span class="sxs-lookup"><span data-stu-id="675d3-219">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="675d3-220">將此範例中的 VBScript 程式碼加入到此檔案中。</span><span class="sxs-lookup"><span data-stu-id="675d3-220">To this file, add the VBScript code in this example.</span></span> <span data-ttu-id="675d3-221">修改連接字串以提供適當的伺服器和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="675d3-221">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="675d3-222">針對指定為 Execute 方法參數的檔案指定適當的路徑。</span><span class="sxs-lookup"><span data-stu-id="675d3-222">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span>  
  
4.  <span data-ttu-id="675d3-223">執行 VBScript 程式碼。</span><span class="sxs-lookup"><span data-stu-id="675d3-223">Execute the VBScript code.</span></span> <span data-ttu-id="675d3-224">XML 大量載入會根據所提供的對應結構描述建立所需的資料表，並在其中大量載入資料。</span><span class="sxs-lookup"><span data-stu-id="675d3-224">The XML Bulk Load creates the necessary tables on the basis of the mapping schema that is provided and bulk loads the data in it.</span></span>  
  
## <a name="f-bulk-loading-from-a-stream"></a><span data-ttu-id="675d3-225">F.</span><span class="sxs-lookup"><span data-stu-id="675d3-225">F.</span></span> <span data-ttu-id="675d3-226">從資料流大量載入</span><span class="sxs-lookup"><span data-stu-id="675d3-226">Bulk loading from a stream</span></span>  
 <span data-ttu-id="675d3-227">XML 大量載入物件模型的 Execute 方法會接受兩個參數。</span><span class="sxs-lookup"><span data-stu-id="675d3-227">The Execute method of the XML Bulk Load object model takes two parameters.</span></span> <span data-ttu-id="675d3-228">第一個參數是對應的結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="675d3-228">The first parameter is the mapping schema file.</span></span> <span data-ttu-id="675d3-229">第二個參數會提供要載入到資料庫中的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="675d3-229">The second parameter provides the XML data that is to be loaded in the database.</span></span> <span data-ttu-id="675d3-230">有兩種方式可將 XML 資料傳遞給 XML 大量載入的 Execute 方法：</span><span class="sxs-lookup"><span data-stu-id="675d3-230">There are two ways to pass the XML data to the Execute method of XML Bulk Load:</span></span>  
  
-   <span data-ttu-id="675d3-231">將檔案名稱指定為參數。</span><span class="sxs-lookup"><span data-stu-id="675d3-231">Specify the file name as the parameter.</span></span>  
  
-   <span data-ttu-id="675d3-232">傳遞包含 XML 資料的資料流。</span><span class="sxs-lookup"><span data-stu-id="675d3-232">Pass a stream that contains the XML data.</span></span>  
  
 <span data-ttu-id="675d3-233">此範例說明如何從資料流大量載入。</span><span class="sxs-lookup"><span data-stu-id="675d3-233">This example illustrates how to bulk load from a stream.</span></span>  
  
 <span data-ttu-id="675d3-234">VBScript 會先執行 SELECT 陳述式，從 Northwind 資料庫的 Customers 資料表中擷取客戶資訊。</span><span class="sxs-lookup"><span data-stu-id="675d3-234">VBScript first executes a SELECT statement to retrieve customer information from the Customers table in the Northwind database.</span></span> <span data-ttu-id="675d3-235">由於 FOR XML 子句是在 SELECT 陳述式中指定的 (利用 ELEMENTS 選項)，因此查詢會傳回此形式的元素中心 XML 文件：</span><span class="sxs-lookup"><span data-stu-id="675d3-235">Because the FOR XML clause is specified (with the ELEMENTS option) in the SELECT statement, the query returns an element-centric XML document of this form:</span></span>  
  
```  
<Customer>  
  <CustomerID>..</CustomerID>  
  <CompanyName>..</CompanyName>  
  <City>..</City>  
</Customer>  
...  
```  
  
 <span data-ttu-id="675d3-236">接著，腳本會將 XML 當做資料流程傳遞至 Execute 方法，做為它的第二個參數。</span><span class="sxs-lookup"><span data-stu-id="675d3-236">The script then passes the XML as a stream to the Execute method as its second parameter.</span></span> <span data-ttu-id="675d3-237">Execute 方法會將資料大量載入至 [加入] 資料表。</span><span class="sxs-lookup"><span data-stu-id="675d3-237">The Execute method bulk loads the data into the Cust table.</span></span>  
  
 <span data-ttu-id="675d3-238">因為此腳本會將 SchemaGen 屬性設為 TRUE，並將 SGDropTables 屬性設定為 TRUE，所以 XML 大量載入會在指定的資料庫中建立 [加入] 資料表。</span><span class="sxs-lookup"><span data-stu-id="675d3-238">Because this script sets the SchemaGen property to TRUE and SGDropTables property to TRUE, XML Bulk Load creates the Cust table in the specified database.</span></span> <span data-ttu-id="675d3-239">(如果此資料表已存在，它會先卸除資料表，然後再重新建立它)。</span><span class="sxs-lookup"><span data-stu-id="675d3-239">(If the table already exists, it first drops the table and then re-creates it.)</span></span>  
  
 <span data-ttu-id="675d3-240">這是 VBScript 範例：</span><span class="sxs-lookup"><span data-stu-id="675d3-240">This is the VBScript example:</span></span>  
  
```  
Set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
Set objCmd = CreateObject("ADODB.Command")  
Set objConn = CreateObject("ADODB.Connection")  
Set objStrmOut = CreateObject ("ADODB.Stream")  
  
objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile     = "c:\error.log"  
objBL.CheckConstraints = True  
objBL.SchemaGen        = True  
objBL.SGDropTables     = True  
objBL.XMLFragment      = True  
' Open a connection to the instance of SQL Server to get the source data.  
  
objConn.Open "provider=SQLOLEDB;server=(local);database=tempdb;integrated security=SSPI"  
Set objCmd.ActiveConnection = objConn  
objCmd.CommandText = "SELECT CustomerID, CompanyName, City FROM Customers FOR XML AUTO, ELEMENTS"  
  
' Open the return stream and execute the command.  
Const adCRLF = -1  
Const adExecuteStream = 1024  
objStrmOut.Open  
objStrmOut.LineSeparator = adCRLF  
objCmd.Properties("Output Stream").Value = objStrmOut  
objCmd.Execute , , adExecuteStream  
objStrmOut.Position = 0  
  
' Execute bulk load. Read source XML data from the stream.  
objBL.Execute "SampleSchema.xml", objStrmOut  
  
Set objBL = Nothing  
```  
  
 <span data-ttu-id="675d3-241">下列 XSD 對應結構描述會提供必要的資訊來建立資料表：</span><span class="sxs-lookup"><span data-stu-id="675d3-241">The following XSD mapping schema provides the necessary information to create the table:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="ROOT" sql:is-constant="true" >  
  <xsd:complexType>  
    <xsd:sequence>  
      <xsd:element ref="Customers"/>  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
<xsd:element name="Customers" sql:relation="Cust" >  
  <xsd:complexType>  
    <xsd:sequence>  
      <xsd:element name="CustomerID"  
                   type="xsd:string"  
                   sql:datatype="nvarchar(5)"/>  
      <xsd:element name="CompanyName"  
                   type="xsd:string"  
                   sql:datatype="nvarchar(40)"/>  
      <xsd:element name="City"  
                   type="xsd:string"  
                   sql:datatype="nvarchar(40)"/>  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="675d3-242">這是相等的 XDR 結構描述：</span><span class="sxs-lookup"><span data-stu-id="675d3-242">This is equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust"  >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
    </ElementType>  
</Schema>  
```  
  
### <a name="opening-a-stream-on-an-existing-file"></a><span data-ttu-id="675d3-243">開啟現有檔案上的資料流</span><span class="sxs-lookup"><span data-stu-id="675d3-243">Opening a Stream on an Existing File</span></span>  
 <span data-ttu-id="675d3-244">您也可以在現有的 XML 資料檔案上開啟資料流程，並以參數的形式將資料流程傳遞至 Execute 方法 (，而不是以參數) 傳遞檔案名。</span><span class="sxs-lookup"><span data-stu-id="675d3-244">You can also open a stream on an existing XML data file and pass the stream as a parameter to the Execute method (instead of passing the file name as the parameter).</span></span>  
  
 <span data-ttu-id="675d3-245">這是將資料流當做參數傳遞的 Visual Basic 範例：</span><span class="sxs-lookup"><span data-stu-id="675d3-245">This is a Visual Basic example of passing a stream as the parameter:</span></span>  
  
```  
Private Sub Form_Load()  
Dim objBL As New SQLXMLBulkLoad  
Dim objStrm As New ADODB.Stream  
Dim objFileSystem As New Scripting.FileSystemObject  
Dim objFile As Scripting.TextStream  
  
MsgBox "Begin BulkLoad..."  
objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile = "c:\error.log"  
objBL.CheckConstraints = True  
objBL.SchemaGen = True  
objBL.SGDropTables = True  
' Here again a stream is specified that contains the source data   
' (instead of the file name). But this is just an illustration.  
' Usually this is useful if you have an XML data   
' stream that is created by some other means that you want to bulk   
' load. This example starts with an XML text file, so it may not be the   
' best to use a stream (you can specify the file name directly).  
' Here you could have specified the file name itself.   
Set objFile = objFileSystem.OpenTextFile("c:\SampleData.xml")  
objStrm.Open  
objStrm.WriteText objFile.ReadAll  
objStrm.Position = 0  
objBL.Execute "c:\SampleSchema.xml", objStrm  
  
Set objBL = Nothing  
MsgBox "Done."  
End Sub  
```  
  
 <span data-ttu-id="675d3-246">若要測試應用程式，請在此範例中提供的檔案 (SampleData.xml) 和 XSD 結構描述中使用下列 XML 文件：</span><span class="sxs-lookup"><span data-stu-id="675d3-246">To test the application, use the following XML document in a file (SampleData.xml) and the XSD schema that is provided in this example:</span></span>  
  
 <span data-ttu-id="675d3-247">這是 XML 來源資料 (SampleData.xml)：</span><span class="sxs-lookup"><span data-stu-id="675d3-247">This is the XML source data (SampleData.xml):</span></span>  
  
```  
<ROOT>  
  <Customers>  
    <CustomerID>1111</CustomerID>  
    <CompanyName>Hanari Carnes</CompanyName>  
    <City>NY</City>  
    <Order OrderID="1" />  
    <Order OrderID="2" />  
  </Customers>  
  
  <Customers>  
    <CustomerID>1112</CustomerID>  
    <CompanyName>Toms Spezialitten</CompanyName>  
     <City>LA</City>  
    <Order OrderID="3" />  
  </Customers>  
  <Customers>  
    <CustomerID>1113</CustomerID>  
    <CompanyName>Victuailles en stock</CompanyName>  
    <Order CustomerID= "4444" OrderID="4" />  
</Customers>  
</ROOT>  
```  
  
 <span data-ttu-id="675d3-248">這是相等的 XDR 結構描述：</span><span class="sxs-lookup"><span data-stu-id="675d3-248">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust"  >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
             <sql:relationship  
                key-relation="Cust"  
                key="CustomerID"  
                foreign-key="CustomerID"  
                foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
</Schema>  
```  
  
## <a name="g-bulk-loading-in-overflow-columns"></a><span data-ttu-id="675d3-249">G.</span><span class="sxs-lookup"><span data-stu-id="675d3-249">G.</span></span> <span data-ttu-id="675d3-250">大量載入溢位資料行</span><span class="sxs-lookup"><span data-stu-id="675d3-250">Bulk loading in overflow columns</span></span>  
 <span data-ttu-id="675d3-251">如果對應結構描述使用 `sql:overflow-field` 註解指定溢位資料行，XML 大量載入會在所有未耗用的資料從來源文件複製到此資料行中。</span><span class="sxs-lookup"><span data-stu-id="675d3-251">If the mapping schema specifies an overflow column by using the `sql:overflow-field` annotation, XML Bulk Load copies all unconsumed data from the source document into this column.</span></span>  
  
 <span data-ttu-id="675d3-252">請考慮使用這個 XSD 結構描述：</span><span class="sxs-lookup"><span data-stu-id="675d3-252">Consider this XSD schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
          parent="Cust"  
          parent-key="CustomerID"  
          child="CustOrder"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  <xsd:element name="Customers" sql:relation="Cust"  
                                sql:overflow-field="OverflowColumn" >  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="CustomerID"  type="xsd:integer" />  
       <xsd:element name="CompanyName" type="xsd:string" />  
       <xsd:element name="City"        type="xsd:string" />  
       <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
         <xsd:complexType>  
          <xsd:attribute name="OrderID" type="xsd:integer" />  
          <xsd:attribute name="CustomerID" type="xsd:integer" />  
         </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="675d3-253">此結構描述會識別 Cust 資料表的溢位資料行 (OverflowColumn)。</span><span class="sxs-lookup"><span data-stu-id="675d3-253">The schema identifies an overflow column (OverflowColumn) for the Cust table.</span></span> <span data-ttu-id="675d3-254">如此一來，每個元素所有未耗用的 XML 資料 **\<Customer>** 就會加入至此資料行。</span><span class="sxs-lookup"><span data-stu-id="675d3-254">As a result, all unconsumed XML data for each **\<Customer>** element is added to this column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="675d3-255">) 指定**abstract = "true"** 的所有抽象元素 (專案，而且指定了**禁止 = "true"** 的所有禁止屬性 (屬性) 會被 XML 大量載入視為溢位，並加入至溢位資料行（如果有指定的話）。</span><span class="sxs-lookup"><span data-stu-id="675d3-255">All abstract elements (elements for which **abstract="true"** is specified) and all prohibited attributes (attributes for which **prohibited="true"** is specified) are considered overflow by XML Bulk Load and are added to the overflow column, if specified.</span></span> <span data-ttu-id="675d3-256">(否則便會予以忽略)。</span><span class="sxs-lookup"><span data-stu-id="675d3-256">(Otherwise, they are ignored.)</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="675d3-257">測試工作範例</span><span class="sxs-lookup"><span data-stu-id="675d3-257">To test a working sample</span></span>  
  
1.  <span data-ttu-id="675d3-258">在**tempdb**資料庫中建立兩個數據表：</span><span class="sxs-lookup"><span data-stu-id="675d3-258">Create two tables in **tempdb** database:</span></span>  
  
    ```  
    USE tempdb;  
    CREATE TABLE Cust (  
                  CustomerID     int         PRIMARY KEY,  
                  CompanyName    varchar(20) NOT NULL,  
                  City           varchar(20) DEFAULT 'Seattle',  
                  OverflowColumn nvarchar(200));  
    GO  
    CREATE TABLE CustOrder (  
                  OrderID    int PRIMARY KEY,  
                  CustomerID int FOREIGN KEY   
                                 REFERENCES Cust(CustomerID));  
    GO  
    ```  
  
2.  <span data-ttu-id="675d3-259">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="675d3-259">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="675d3-260">將這個範例所提供的 XSD 結構描述加入到此檔案中。</span><span class="sxs-lookup"><span data-stu-id="675d3-260">Add the XSD schema that is provided in this example to the file.</span></span>  
  
3.  <span data-ttu-id="675d3-261">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 SampleXMLData.xml。</span><span class="sxs-lookup"><span data-stu-id="675d3-261">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="675d3-262">將下列 XML 文件加入到此檔案中：</span><span class="sxs-lookup"><span data-stu-id="675d3-262">Add the following XML document to the file:</span></span>  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City><![CDATA[NY]]> </City>  
        <Junk>garbage in overflow</Junk>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
      </Customers>  
  
      <Customers>  
        <CustomerID>1112</CustomerID>  
        <CompanyName>Toms Spezialitten</CompanyName>  
         <![CDATA[LA]]>   
        <!-- <xyz><address>111 Maple, Seattle</address></xyz>   -->  
        <Order OrderID="3" />  
      </Customers>  
      <Customers>  
        <CustomerID>1113</CustomerID>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
    </Customers>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="675d3-263">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 ValidateAndBulkload.vbs。</span><span class="sxs-lookup"><span data-stu-id="675d3-263">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="675d3-264">將下列 Microsoft Visual Basic Scripting Edition (VBScript) 程式碼加入到此檔案中。</span><span class="sxs-lookup"><span data-stu-id="675d3-264">To this file, add the following Microsoft Visual Basic Scripting Edition (VBScript) code.</span></span> <span data-ttu-id="675d3-265">修改連接字串以提供適當的伺服器和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="675d3-265">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="675d3-266">針對指定為 Execute 方法參數的檔案指定適當的路徑。</span><span class="sxs-lookup"><span data-stu-id="675d3-266">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
5.  <span data-ttu-id="675d3-267">執行 VBScript 程式碼。</span><span class="sxs-lookup"><span data-stu-id="675d3-267">Execute the VBScript code.</span></span>  
  
 <span data-ttu-id="675d3-268">這是相等的 XDR 結構描述：</span><span class="sxs-lookup"><span data-stu-id="675d3-268">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust"   
                       sql:overflow-field="OverflowColumn"  >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
             <sql:relationship  
                key-relation="Cust"  
                key="CustomerID"  
                foreign-key="CustomerID"  
                foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
</Schema>  
```  
  
## <a name="h-specifying-the-file-path-for-temp-files-in-transaction-mode"></a><span data-ttu-id="675d3-269">H.</span><span class="sxs-lookup"><span data-stu-id="675d3-269">H.</span></span> <span data-ttu-id="675d3-270">在交易模式下指定暫存檔案的檔案路徑</span><span class="sxs-lookup"><span data-stu-id="675d3-270">Specifying the file path for temp files in transaction mode</span></span>  
 <span data-ttu-id="675d3-271">當您以交易模式大量載入 (也就是，當 Transaction 屬性設定為 TRUE) 時，您也必須在下列任一條件成立時，設定 TempFilePath 屬性：</span><span class="sxs-lookup"><span data-stu-id="675d3-271">When you are bulk loading in transaction mode (that is, when the Transaction property is set to TRUE), you also must set the TempFilePath property when either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="675d3-272">您要大量載入到遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="675d3-272">You are bulk loading to a remote server.</span></span>  
  
-   <span data-ttu-id="675d3-273">您想要使用替代的本機磁碟或資料夾 (非 TEMP環境變數所指定的路徑) 來儲存交易模式下所建立的暫存檔案。</span><span class="sxs-lookup"><span data-stu-id="675d3-273">You want to use an alternate local drive or folder (one other than the path that is specified by the TEMP environment variable) to store the temporary files that are created in the transaction mode.</span></span>  
  
 <span data-ttu-id="675d3-274">例如，下列 VBScript 程式碼會在交易模式下，將資料從 SampleXMLData.xml 檔大量載入到資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="675d3-274">For example, the following VBScript code bulk loads data from the SampleXMLData.xml file into the database tables in transaction mode.</span></span> <span data-ttu-id="675d3-275">已指定 TempFilePath 屬性，以設定在交易模式中產生之暫存檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="675d3-275">The TempFilePath property is specified to set the path for the temporary files that are generated in transaction mode.</span></span>  
  
```  
set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile = "c:\error.log"  
objBL.CheckConstraints = True  
objBL.Transaction=True  
objBL.TempFilePath="\\Server\MyDir"  
objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
set objBL=Nothing  
```  
  
> [!NOTE]  
>  <span data-ttu-id="675d3-276">暫存檔案路徑必須是一個共用位置，可存取 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 目標執行個體之服務帳戶以及執行大量載入應用程式的帳戶。</span><span class="sxs-lookup"><span data-stu-id="675d3-276">The temporary file path must be a shared location that is accessible to the service account of the target instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and to the account that is running the bulk load application.</span></span> <span data-ttu-id="675d3-277">除非您是在本機伺服器上大量載入，否則暫存檔案路徑必須是 UNC 路徑 (例如 \\ \servername\sharename ....) 。</span><span class="sxs-lookup"><span data-stu-id="675d3-277">Unless you are bulk loading on a local server, the temporary file path must be a UNC path (such as \\\servername\sharename).</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="675d3-278">測試工作範例</span><span class="sxs-lookup"><span data-stu-id="675d3-278">To test a working sample</span></span>  
  
1.  <span data-ttu-id="675d3-279">在**tempdb**資料庫中建立此資料表：</span><span class="sxs-lookup"><span data-stu-id="675d3-279">Create this table in **tempdb** database:</span></span>  
  
    ```  
    USE tempdb;  
    CREATE TABLE Cust (     CustomerID uniqueidentifier,   
          LastName  varchar(20));  
    GO  
    ```  
  
2.  <span data-ttu-id="675d3-280">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="675d3-280">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="675d3-281">將下列 XSD 結構描述加入到此檔案中：</span><span class="sxs-lookup"><span data-stu-id="675d3-281">Add the following XSD schema to the file:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="ROOT" sql:is-constant="true" >  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element ref="Customers" />  
          </xsd:sequence>  
        </xsd:complexType>  
      </xsd:element>  
  
      <xsd:element name="Customers" sql:relation="Cust" >  
       <xsd:complexType>  
         <xsd:attribute name="CustomerID"  type="xsd:string" />  
         <xsd:attribute name="LastName" type="xsd:string" />  
       </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="675d3-282">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 SampleXMLData.xml。</span><span class="sxs-lookup"><span data-stu-id="675d3-282">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="675d3-283">將下列 XML 文件加入到此檔案中：</span><span class="sxs-lookup"><span data-stu-id="675d3-283">Add the following XML document to the file:</span></span>  
  
    ```  
    <ROOT>  
    <Customers CustomerID="6F9619FF-8B86-D011-B42D-00C04FC964FF"   
               LastName="Smith" />  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="675d3-284">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 ValidateAndBulkload.vbs。</span><span class="sxs-lookup"><span data-stu-id="675d3-284">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="675d3-285">將下列 VBScript 程式碼加入到此檔案中。</span><span class="sxs-lookup"><span data-stu-id="675d3-285">To this file, add the following VBScript code.</span></span> <span data-ttu-id="675d3-286">修改連接字串以提供適當的伺服器和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="675d3-286">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="675d3-287">針對指定為 Execute 方法參數的檔案指定適當的路徑。</span><span class="sxs-lookup"><span data-stu-id="675d3-287">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span> <span data-ttu-id="675d3-288">也請為 TempFilePath 屬性指定適當的路徑。</span><span class="sxs-lookup"><span data-stu-id="675d3-288">Also specify the appropriate path for the TempFilePath property.</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Transaction=True  
    objBL.TempFilePath="\\server\folder"  
    objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
5.  <span data-ttu-id="675d3-289">執行 VBScript 程式碼。</span><span class="sxs-lookup"><span data-stu-id="675d3-289">Execute the VBScript code.</span></span>  
  
     <span data-ttu-id="675d3-290">`sql:datatype`當**customerid**的值指定為包含大括弧 ( {和} ) 的 GUID （例如）時，架構必須指定**customerid**屬性的對應。</span><span class="sxs-lookup"><span data-stu-id="675d3-290">The schema must specify the corresponding `sql:datatype` for the **CustomerID** attribute when the value for **CustomerID** is specified as a GUID that includes braces ({ and }), such as:</span></span>  
  
    ```  
    <ROOT>  
    <Customers CustomerID="{6F9619FF-8B86-D011-B42D-00C04FC964FF}"   
               LastName="Smith" />  
    </ROOT>  
    ```  
  
     <span data-ttu-id="675d3-291">這是更新的結構描述：</span><span class="sxs-lookup"><span data-stu-id="675d3-291">This is the updated schema:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="ROOT" sql:is-constant="true" >  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element ref="Customers" />  
          </xsd:sequence>  
        </xsd:complexType>  
      </xsd:element>  
  
      <xsd:element name="Customers" sql:relation="Cust" >  
       <xsd:complexType>  
         <xsd:attribute name="CustomerID"  type="xsd:string"   
                        sql:datatype="uniqueidentifier" />  
         <xsd:attribute name="LastName" type="xsd:string" />  
       </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
     <span data-ttu-id="675d3-292">當 `sql:datatype` 指定將資料行類型識別為時 `uniqueidentifier` ，大量載入作業會從**CustomerID**值中移除 ( {和} ) 的大括弧，然後再將它插入資料行中。</span><span class="sxs-lookup"><span data-stu-id="675d3-292">When `sql:datatype` is specified identifying the column type as `uniqueidentifier`, the bulk load operation removes the braces ({ and }) from the **CustomerID** value before inserting it in the column.</span></span>  
  
 <span data-ttu-id="675d3-293">這是相等的 XDR 結構描述：</span><span class="sxs-lookup"><span data-stu-id="675d3-293">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
<ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
</ElementType>  
<ElementType name="Customers" sql:relation="Cust" >  
  <AttributeType name="CustomerID"  sql:datatype="uniqueidentifier" />  
  <AttributeType name="LastName"   />  
  
  <attribute type="CustomerID" />  
  <attribute type="LastName"   />  
</ElementType>  
</Schema>  
```  
  
## <a name="i-using-an-existing-database-connection-with-the-connectioncommand-property"></a><span data-ttu-id="675d3-294">I.</span><span class="sxs-lookup"><span data-stu-id="675d3-294">I.</span></span> <span data-ttu-id="675d3-295">搭配 ConnectionCommand 屬性使用現有的資料庫連接</span><span class="sxs-lookup"><span data-stu-id="675d3-295">Using an existing database connection with the ConnectionCommand property</span></span>  
 <span data-ttu-id="675d3-296">您可以使用現有的 ADO 連接來大量載入 XML。</span><span class="sxs-lookup"><span data-stu-id="675d3-296">You can use an existing ADO connection to bulk load XML.</span></span> <span data-ttu-id="675d3-297">這在 XML 大量載入只是將在資料來源上執行之許多作業中的一個時相當實用。</span><span class="sxs-lookup"><span data-stu-id="675d3-297">This is useful if XML Bulk Load is just one of many operations that will be performed on a data source.</span></span>  
  
 <span data-ttu-id="675d3-298">ConnectionCommand 屬性可讓您藉由使用 ADO command 物件，來使用現有的 ADO 連接。</span><span class="sxs-lookup"><span data-stu-id="675d3-298">The ConnectionCommand property enables you to use an existing ADO connection by using an ADO command object.</span></span> <span data-ttu-id="675d3-299">這會在下列 Visual Basic 範例中加以說明：</span><span class="sxs-lookup"><span data-stu-id="675d3-299">This is illustrated in the following Visual Basic example:</span></span>  
  
```  
Private Sub Form_Load()  
Dim objBL As New SQLXMLBulkLoad4  
Dim objCmd As New ADODB.Command  
Dim objConn As New ADODB.Connection  
  
'Open a connection to an instance of SQL Server.  
objConn.Open "provider=SQLOLEDB;data source=(local);database=tempdb;integrated security=SSPI"  
'Ask the Command object to use the connection just established.  
Set objCmd.ActiveConnection = objConn  
  
'Tell Bulk Load to use the active command object that is using the Connection obj.  
objBL.ConnectionCommand = objCmd  
objBL.ErrorLogFile = "c:\error.log"  
objBL.CheckConstraints = True  
'The Transaction property must be set to True if you use ConnectionCommand.  
objBL.Transaction = True  
objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
Set objBL = Nothing  
End Sub  
```  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="675d3-300">測試工作範例</span><span class="sxs-lookup"><span data-stu-id="675d3-300">To test a working sample</span></span>  
  
1.  <span data-ttu-id="675d3-301">在**tempdb**資料庫中建立兩個數據表：</span><span class="sxs-lookup"><span data-stu-id="675d3-301">Create two tables in **tempdb** database:</span></span>  
  
    ```  
    USE tempdb;  
    CREATE TABLE Cust(  
                   CustomerID   varchar(5) PRIMARY KEY,  
                   CompanyName  varchar(30),  
                   City         varchar(20));  
    GO  
    CREATE TABLE CustOrder(  
                   CustomerID  varchar(5) references Cust (CustomerID),  
                   OrderID     varchar(5) PRIMARY KEY);  
    GO  
    ```  
  
2.  <span data-ttu-id="675d3-302">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="675d3-302">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="675d3-303">將下列 XSD 結構描述加入到此檔案中：</span><span class="sxs-lookup"><span data-stu-id="675d3-303">Add the following XSD schema to the file:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
    <xsd:annotation>  
      <xsd:appinfo>  
        <sql:relationship name="CustCustOrder"  
              parent="Cust"  
              parent-key="CustomerID"  
              child="CustOrder"  
              child-key="CustomerID" />  
      </xsd:appinfo>  
    </xsd:annotation>  
      <xsd:element name="ROOT" sql:is-constant="true" >  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element ref="Customers" />  
          </xsd:sequence>  
        </xsd:complexType>  
      </xsd:element>  
      <xsd:element name="Customers" sql:relation="Cust" >  
       <xsd:complexType>  
         <xsd:sequence>  
           <xsd:element name="CustomerID"  type="xsd:integer" />  
           <xsd:element name="CompanyName" type="xsd:string" />  
           <xsd:element name="City"        type="xsd:string" />  
           <xsd:element name="Order"   
                              sql:relation="CustOrder"  
                              sql:relationship="CustCustOrder" >  
             <xsd:complexType>  
              <xsd:attribute name="OrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:integer" />  
             </xsd:complexType>  
           </xsd:element>  
         </xsd:sequence>  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="675d3-304">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 SampleXMLData.xml。</span><span class="sxs-lookup"><span data-stu-id="675d3-304">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="675d3-305">將下列 XML 文件加入到此檔案中：</span><span class="sxs-lookup"><span data-stu-id="675d3-305">Add the following XML document to the file:</span></span>  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City>NY</City>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
      </Customers>  
  
      <Customers>  
        <CustomerID>1112</CustomerID>  
        <CompanyName>Toms Spezialitten</CompanyName>  
         <City>LA</City>  
        <Order OrderID="3" />  
      </Customers>  
      <Customers>  
        <CustomerID>1113</CustomerID>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
    </Customers>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="675d3-306">建立 Visual Basic (標準 EXE) 應用程式與之前的程式碼。</span><span class="sxs-lookup"><span data-stu-id="675d3-306">Create a Visual Basic (Standard EXE) application and the preceding code.</span></span> <span data-ttu-id="675d3-307">將這些參考加入到專案中：</span><span class="sxs-lookup"><span data-stu-id="675d3-307">Add these references to the project:</span></span>  
  
    ```  
    Microsoft XML BulkLoad for SQL Server 4.0 Type Library  
    Microsoft ActiveX Data objects 2.6 Library  
    ```  
  
5.  <span data-ttu-id="675d3-308">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="675d3-308">Execute the application.</span></span>  
  
 <span data-ttu-id="675d3-309">這是相等的 XDR 結構描述：</span><span class="sxs-lookup"><span data-stu-id="675d3-309">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust"  >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
         <sql:relationship  
                key-relation="Cust"  
                key="CustomerID"  
                foreign-key="CustomerID"  
                foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
</Schema>  
```  
  
## <a name="j-bulk-loading-in-xml-data-type-columns"></a><span data-ttu-id="675d3-310">J.</span><span class="sxs-lookup"><span data-stu-id="675d3-310">J.</span></span> <span data-ttu-id="675d3-311">大量載入到 xml 資料類型資料行</span><span class="sxs-lookup"><span data-stu-id="675d3-311">Bulk loading in xml Data Type columns</span></span>  
 <span data-ttu-id="675d3-312">如果對應架構使用批註來指定[xml 資料類型資料](/sql/t-sql/xml/xml-transact-sql)行 `sql:datatype="xml"` ，xml 大量載入可以將來源文件中的對應欄位之 xml 子專案複製到這個資料行。</span><span class="sxs-lookup"><span data-stu-id="675d3-312">If the mapping schema specifies a [xml data type](/sql/t-sql/xml/xml-transact-sql) column by using the `sql:datatype="xml"` annotation, XML Bulk Load can copy XML child elements for the mapped field from the source document into this column.</span></span>  
  
 <span data-ttu-id="675d3-313">請考慮使用下列 XSD 結構描述，該結構描述會對應 AdventureWorks 範本資料庫中的 Production.ProductModel 資料表檢視。</span><span class="sxs-lookup"><span data-stu-id="675d3-313">Consider the following XSD schema, which maps a view of the Production.ProductModel table in the AdventureWorks sample database.</span></span> <span data-ttu-id="675d3-314">在此資料表中，資料類型的 CatalogDescription 欄位 `xml` 會 **\<Desc>** 使用和注釋對應到元素 `sql:field` `sql:datatype="xml"` 。</span><span class="sxs-lookup"><span data-stu-id="675d3-314">In this table, the CatalogDescription field of `xml` data type is mapped to a **\<Desc>** element using the `sql:field` and `sql:datatype="xml"` annotations.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
           xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
           xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">   
  <xsd:element name="ProductModel"  sql:relation="Production.ProductModel" >  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Name" type="xs:string"></xsd:element>  
        <xsd:element name="Desc" sql:field="CatalogDescription" sql:datatype="xml">  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element name="ProductDescription">  
              <xsd:complexType>  
                <xsd:sequence>  
                  <xsd:element name="Summary" type="xs:anyType"/>  
                </xsd:sequence>  
              </xsd:complexType>  
            </xsd:element>  
          </xsd:sequence>  
        </xsd:complexType>  
        </xsd:element>   
     </xsd:sequence>  
     <xsd:attribute name="ProductModelID" sql:field="ProductModelID" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="675d3-315">測試工作範例</span><span class="sxs-lookup"><span data-stu-id="675d3-315">To test a working sample</span></span>  
  
1.  <span data-ttu-id="675d3-316">確認已安裝 AdventureWorks 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="675d3-316">Verify that the AdventureWorks sample database is installed.</span></span>  
  
2.  <span data-ttu-id="675d3-317">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="675d3-317">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="675d3-318">複製以上的 XSD 結構描述，並將其貼入檔案並加以儲存。</span><span class="sxs-lookup"><span data-stu-id="675d3-318">Copy the XSD schema above and paste it into the file and save it.</span></span>  
  
3.  <span data-ttu-id="675d3-319">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 SampleXMLData.xml。</span><span class="sxs-lookup"><span data-stu-id="675d3-319">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="675d3-320">複製下列 XML 文件，然後將其貼入檔案並儲存在先前步驟所使用的相同資料夾中。</span><span class="sxs-lookup"><span data-stu-id="675d3-320">Copy the following XML document below and paste it into the file and save it in the same folder as was used for the previous step.</span></span>  
  
    ```  
    <ProductModel ProductModelID="2005">  
        <Name>Mountain-100 (2005 model)</Name>  
        <Desc><?xml-stylesheet href="ProductDescription.xsl" type="text/xsl"?>  
            <p1:ProductDescription xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
                  xmlns:wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"   
                  xmlns:wf="http://www.adventure-works.com/schemas/OtherFeatures"   
                  xmlns:html="http://www.w3.org/1999/xhtml"   
                  xmlns="">  
                <p1:Summary>  
                    <html:p>Our top-of-the-line competition mountain bike.   
          Performance-enhancing options include the innovative HL Frame,   
          super-smooth front suspension, and traction for all terrain.  
                            </html:p>  
                </p1:Summary>  
                <p1:Manufacturer>  
                    <p1:Name>AdventureWorks</p1:Name>  
                    <p1:Copyright>2002-2005</p1:Copyright>  
                    <p1:ProductURL>HTTP://www.Adventure-works.com</p1:ProductURL>  
                </p1:Manufacturer>  
                <p1:Features>These are the product highlights.   
                     <wm:Warranty>  
                        <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
                        <wm:Description>parts and labor</wm:Description>  
                    </wm:Warranty><wm:Maintenance>  
                        <wm:NoOfYears>10 years</wm:NoOfYears>  
                        <wm:Description>maintenance contract available through your dealer or any AdventureWorks retail store.</wm:Description>  
                    </wm:Maintenance><wf:wheel>High performance wheels.</wf:wheel><wf:saddle>  
                        <html:i>Anatomic design</html:i> and made from durable leather for a full-day of riding in comfort.</wf:saddle><wf:pedal>  
                        <html:b>Top-of-the-line</html:b> clipless pedals with adjustable tension.</wf:pedal><wf:BikeFrame>Each frame is hand-crafted in our Bothell facility to the optimum diameter   
          and wall-thickness required of a premium mountain frame.   
          The heat-treated welded aluminum frame has a larger diameter tube that absorbs the bumps.</wf:BikeFrame><wf:crankset> Triple crankset; alumunim crank arm; flawless shifting. </wf:crankset></p1:Features>  
                <!-- add one or more of these elements... one for each specific product in this product model -->  
                <p1:Picture>  
                    <p1:Angle>front</p1:Angle>  
                    <p1:Size>small</p1:Size>  
                    <p1:ProductPhotoID>118</p1:ProductPhotoID>  
                </p1:Picture>  
                <!-- add any tags in <specifications> -->  
                <p1:Specifications> These are the product specifications.  
                       <Material>Almuminum Alloy</Material><Color>Available in most colors</Color><ProductLine>Mountain bike</ProductLine><Style>Unisex</Style><RiderExperience>Advanced to Professional riders</RiderExperience></p1:Specifications>  
            </p1:ProductDescription>  
        </Desc>  
    </ProductModel>  
    ```  
  
4.  <span data-ttu-id="675d3-321">以慣用的文字編輯器或 XML 編輯器建立一個檔案，然後將其儲存為 BulkloadXml.vbs。</span><span class="sxs-lookup"><span data-stu-id="675d3-321">Create a file in your preferred text or XML editor, and save it as BulkloadXml.vbs.</span></span> <span data-ttu-id="675d3-322">複製下列 VBScript 程式碼，並將其貼入檔案。</span><span class="sxs-lookup"><span data-stu-id="675d3-322">Copy the following VBScript code and paste it into the file.</span></span> <span data-ttu-id="675d3-323">將其儲存在先前 XML 資料和結構描述檔案所使用的相同資料夾中。</span><span class="sxs-lookup"><span data-stu-id="675d3-323">Save it in the same folder as was used for the previous XML data and schema files.</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=MyServer;database=AdventureWorks;integrated security=SSPI"  
  
    Dim fso, sAppPath  
    Set fso = CreateObject("Scripting.FileSystemObject")   
    sAppPath = fso.GetFolder(".")   
  
    objBL.ErrorLogFile = sAppPath & "\error.log"  
  
    'Execute XML bulkload using file.  
    objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
5.  <span data-ttu-id="675d3-324">執行 BulkloadXml.vbs 指令碼。</span><span class="sxs-lookup"><span data-stu-id="675d3-324">Execute the BulkloadXml.vbs script.</span></span>  
  
  
