---
title: sql： limit-field 和 sql： limit-value (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- limiting values [SQLXML]
- limit-value annotation
- limit-field annotation
- sql:limit-field
- sql:limit-value
- filtering [SQLXML]
ms.assetid: 402c21cf-9566-463f-a928-f94270c11db3
author: rothja
ms.author: jroth
ms.openlocfilehash: a6d0383aece7a2bafa5d21b76d0c4da9cb057984
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595886"
---
# <a name="sqllimit-field-and-sqllimit-value-sqlxml-40"></a><span data-ttu-id="891d1-102">sql:limit-field 和 sql:limit-value (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="891d1-102">sql:limit-field and sql:limit-value (SQLXML 4.0)</span></span>
  <span data-ttu-id="891d1-103">XML 大量載入會根據 `sql:limit-field` 和 `sql:limit-value` 註解的定義來處理這些註解。</span><span class="sxs-lookup"><span data-stu-id="891d1-103">XML Bulk Load processes the `sql:limit-field` and `sql:limit-value` annotations per their definition.</span></span> <span data-ttu-id="891d1-104">如需詳細資訊，請參閱[使用 sql： limit-field 和 sql： limit-value 來篩選值 &#40;SQLXML 4.0&#41;](annotation-interpretation-sql-limit-field-and-sql-limit-value.md)。</span><span class="sxs-lookup"><span data-stu-id="891d1-104">For more information, see [Filtering Values Using sql:limit-field and sql:limit-value &#40;SQLXML 4.0&#41;](annotation-interpretation-sql-limit-field-and-sql-limit-value.md).</span></span>  
  
 <span data-ttu-id="891d1-105">例如，假設資料庫包含下列資料表：</span><span class="sxs-lookup"><span data-stu-id="891d1-105">For example, suppose a database contains the following tables:</span></span>  
  
-   <span data-ttu-id="891d1-106">Customer (CustomerID, CompanyName)</span><span class="sxs-lookup"><span data-stu-id="891d1-106">Customer (CustomerID, CompanyName)</span></span>  
  
-   <span data-ttu-id="891d1-107">Addresses (CustomerID, StreetAddress, AddressType)</span><span class="sxs-lookup"><span data-stu-id="891d1-107">Addresses (CustomerID, StreetAddress, AddressType)</span></span>  
  
 <span data-ttu-id="891d1-108">客戶可能有許多地址，而每個地址都具有相關聯的地址類型 (例如，送貨地址或帳單地址)。</span><span class="sxs-lookup"><span data-stu-id="891d1-108">A customer can have many addresses, and each address has an address type associated with it (for example, a shipping address or a billing address).</span></span>  
  
 <span data-ttu-id="891d1-109">現在，請考慮這些資料表的這個 XML 檢視 (指定在下列註解 XSD 結構描述中)：</span><span class="sxs-lookup"><span data-stu-id="891d1-109">Now consider this XML view of these tables as specified in the following annotated XSD schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustAddr"  
        parent="Customer"  
        parent-key="CustomerID"  
        child="Address"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Customer" >  
   <xsd:complexType>  
        <xsd:attribute name="CustomerID"   type="xsd:int" />   
        <xsd:attribute name="CompanyName"  type="xsd:string" />  
        <xsd:attribute name="BillTo"   
                       type="xsd:string"   
                       sql:relation="Address"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="billing"  
                       sql:relationship="CustAddr" >  
        </xsd:attribute>  
        <xsd:attribute name="ShipTo"   
                       type="xsd:string"   
                       sql:relation="Address"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="shipping"  
                       sql:relationship="CustAddr" >  
        </xsd:attribute>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="891d1-110">在接到這個結構描述和 XML 資料時，XML 大量載入會將針對 BillTo 屬性所指定的值以及 AddressType 資料行的 "billing" 值插入至 CustAddress 資料表的 StreetAddress 資料行。</span><span class="sxs-lookup"><span data-stu-id="891d1-110">Upon receiving this schema and XML data, XML Bulk Load inserts the value that is specified for the BillTo attribute into the StreetAddress column of the CustAddress table along with the "billing" value for the AddressType column.</span></span>  
  
 <span data-ttu-id="891d1-111">同樣地，XML 大量載入會將針對 ShipTo 屬性所指定的值以及 AddressType 資料行中的 "shipping" 值插入至 StreetAddress 資料行。</span><span class="sxs-lookup"><span data-stu-id="891d1-111">Similarly, XML Bulk Load inserts the value that is specified for the ShipTo attribute into the StreetAddress column along with the "shipping" value in the AddressType column.</span></span>  
  
### <a name="to-test-a-working-sample"></a><span data-ttu-id="891d1-112">測試工作範例</span><span class="sxs-lookup"><span data-stu-id="891d1-112">To test a working sample</span></span>  
  
1.  <span data-ttu-id="891d1-113">將這個範例所提供的結構描述儲存為 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="891d1-113">Save the schema that is provided in this example as SampleSchema.xml.</span></span>  
  
2.  <span data-ttu-id="891d1-114">建立這些資料表：</span><span class="sxs-lookup"><span data-stu-id="891d1-114">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Customer(  
                     CustomerID     int         PRIMARY KEY,  
                     CompanyName    varchar(20) NOT NULL)  
    GO  
    CREATE TABLE Address(  
                      CustomerID     int        FOREIGN KEY REFERENCES   
                                                 Customer(CustomerID),   
                      StreetAddress  varchar(50),  
                      AddressType    varchar(10))  
    GO  
    ```  
  
3.  <span data-ttu-id="891d1-115">儲存下列範例資料為 SampleXMLData.xml：</span><span class="sxs-lookup"><span data-stu-id="891d1-115">Save the following sample data as SampleXMLData.xml:</span></span>  
  
    ```  
    <Customer CustomerID="1111" CompanyName="Sean Chai" City="NY"   
                 BillTo="111 Maple (Billing) "   
                 ShipTo="111 Maple (Shipping)" />  
    <Customer CustomerID="1112" CompanyName="Dont Know" City="LA"   
                 BillTo="222 Spruce (Billing)"   
                 ShipTo="222 Spruce (Shipping)" />  
    ```  
  
4.  <span data-ttu-id="891d1-116">若要執行 XML 大量載入，請將這個 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) 範例儲存為 Sample.vbs 並執行它：</span><span class="sxs-lookup"><span data-stu-id="891d1-116">To execute XML Bulk Load, save and execute this [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) example as Sample.vbs:</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.XMLFragment = True  
    objBL.CheckConstraints=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
 <span data-ttu-id="891d1-117">這是相等的 XDR 結構描述：</span><span class="sxs-lookup"><span data-stu-id="891d1-117">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="Customer" sql:relation="Customer" >  
    <AttributeType name="CustomerID" />  
    <AttributeType name="CompanyName" />  
    <AttributeType name="BillTo" />  
    <AttributeType name="ShipTo" />  
  
    <attribute type="CustomerID" />  
    <attribute type="CompanyName" />  
    <attribute type="BillTo"   
                sql:limit-field="AddressType"  
                sql:limit-value="billing"  
                sql:field="StreetAddress"  
                sql:relation="Address" >  
                <sql:relationship   
                        key="CustomerID"  
                        key-relation="Customer"  
                        foreign-relation="Address"  
                        foreign-key="CustomerID" />  
    </attribute>  
    <attribute type="ShipTo"   
                sql:limit-field="AddressType"  
                sql:limit-value="shipping"  
                sql:field="StreetAddress"  
                sql:relation="Address" >  
                <sql:relationship   
                     key="CustomerID"  
                     key-relation="Customer"  
                     foreign-relation="Address"  
                     foreign-key="CustomerID" />  
    </attribute>  
</ElementType>  
</Schema>  
```  
  
  
