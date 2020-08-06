---
title: sql：關聯性和索引鍵排序規則 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- key ordering rules [SQLXML]
- relationship annotation
ms.assetid: 914cb152-09f5-4b08-b35d-71940e4e9986
author: rothja
ms.author: jroth
ms.openlocfilehash: 716e911676dc81539fc641bee139d92e29dc49db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597757"
---
# <a name="sqlrelationship-and-the-key-ordering-rule-sqlxml-40"></a><span data-ttu-id="e1589-102">sql:relationship 和關鍵識別碼順序規則 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="e1589-102">sql:relationship and the Key Ordering Rule (SQLXML 4.0)</span></span>
  <span data-ttu-id="e1589-103">由於 XML 大量載入會產生記錄做為其節點進入範圍，並將這些記錄傳送到 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 做為其節點離開範圍，因此用於記錄的資料必須存在於節點的範圍內。</span><span class="sxs-lookup"><span data-stu-id="e1589-103">Because XML Bulk Load generates records as their nodes enter into scope and sends those records to Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as their nodes exit scope, the data for the record must be present within the scope of the node.</span></span>  
  
 <span data-ttu-id="e1589-104">請考慮下列 XSD 架構，其中和元素之間的一對多關聯性 **\<Customer>** **\<Order>** (一個客戶可以使用專案指定) 的多個訂單 `<sql:relationship>` ：</span><span class="sxs-lookup"><span data-stu-id="e1589-104">Consider the following XSD schema, in which the one-to-many relationship between **\<Customer>** and **\<Order>** elements (one customer can place many orders) is specified by using the `<sql:relationship>` element:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"<>   
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
</xsd:schema>  
```  
  
 <span data-ttu-id="e1589-105">當 **\<Customer>** 元素節點進入範圍內時，XML 大量載入會產生客戶記錄。</span><span class="sxs-lookup"><span data-stu-id="e1589-105">As the **\<Customer>** element node enters into scope, XML Bulk Load generates a customer record.</span></span> <span data-ttu-id="e1589-106">此記錄會持續到 XML 大量載入讀取為止 **\</Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="e1589-106">This record stays until XML Bulk Load reads **\</Customer>**.</span></span> <span data-ttu-id="e1589-107">在處理專案 **\<Order>** 節點時，XML 大量載入 `<sql:relationship>` 會使用從父元素取得 CustOrder 資料表之 CustomerID 外鍵資料行的值 **\<Customer>** ，因為此元素不 **\<Order>** 會指定**customerid**屬性。</span><span class="sxs-lookup"><span data-stu-id="e1589-107">In processing the **\<Order>** element node, XML Bulk Load uses `<sql:relationship>` to obtain the value of the CustomerID foreign key column of the CustOrder table from the **\<Customer>** parent element, because the **\<Order>** element does not specify the **CustomerID** attribute.</span></span> <span data-ttu-id="e1589-108">這表示在定義 **\<Customer>** 元素時，您必須先在架構中指定**CustomerID**屬性，然後再指定 `<sql:relationship>` 。</span><span class="sxs-lookup"><span data-stu-id="e1589-108">This means that in defining the **\<Customer>** element, you must specify the **CustomerID** attribute in the schema before you specify `<sql:relationship>`.</span></span> <span data-ttu-id="e1589-109">否則，當 **\<Order>** 元素進入範圍內時，Xml 大量載入會產生 CustOrder 資料表的記錄，而當 XML 大量載入到達 **\</Order>** 結束標記時，它會將記錄傳送至， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 而不含 CustomerID 外鍵資料行值。</span><span class="sxs-lookup"><span data-stu-id="e1589-109">Otherwise, when an **\<Order>** element enters into scope, XML Bulk Load generates a record for the CustOrder table, and when the XML Bulk Load reaches the **\</Order>** end tag, it sends the record to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] without the CustomerID foreign key column value.</span></span>  
  
 <span data-ttu-id="e1589-110">將這個範例所提供的結構描述儲存為 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="e1589-110">Save the schema that is provided in this example as SampleSchema.xml.</span></span>  
  
### <a name="to-test-a-working-sample"></a><span data-ttu-id="e1589-111">測試工作範例</span><span class="sxs-lookup"><span data-stu-id="e1589-111">To test a working sample</span></span>  
  
1.  <span data-ttu-id="e1589-112">建立這些資料表：</span><span class="sxs-lookup"><span data-stu-id="e1589-112">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int          PRIMARY KEY,  
               CompanyName    varchar(20)  NOT NULL,  
                  City           varchar(20)  DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                  OrderID        varchar(10) PRIMARY KEY,  
               CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="e1589-113">儲存下列範例資料為 SampleXMLData.xml：</span><span class="sxs-lookup"><span data-stu-id="e1589-113">Save the following sample data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>    
      <Customers>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City>NY</City>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
        <CustomerID>1111</CustomerID>  
      </Customers>  
      <Customers>  
        <CompanyName>Toms Spezialitten</CompanyName>  
         <City>LA</City>    
        <Order OrderID="3" />  
        <CustomerID>1112</CustomerID>  
      </Customers>  
      <Customers>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
        <CustomerID>1113</CustomerID>  
      </Customers>  
    </ROOT>  
    ```  
  
3.  <span data-ttu-id="e1589-114">若要執行 XML 大量載入，請儲存和執行下列 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) 範例為 MySample.vbs：</span><span class="sxs-lookup"><span data-stu-id="e1589-114">To execute XML Bulk Load, save and execute the following [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) example as MySample.vbs:</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Transaction=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
     <span data-ttu-id="e1589-115">結果是，XML 大量載入將 NULL 值插入到 CustOrder 資料表的 CustomerID 外部索引鍵資料行中。</span><span class="sxs-lookup"><span data-stu-id="e1589-115">The result is that XML Bulk Load inserts a NULL value in the CustomerID foreign key column of the CustOrder table.</span></span> <span data-ttu-id="e1589-116">如果您修改 XML 範例資料 **\<CustomerID>** ，使子項目出現在子專案之前 **\<Order>** ，您會得到預期的結果： XML 大量載入會將指定的外鍵值插入資料行。</span><span class="sxs-lookup"><span data-stu-id="e1589-116">If you revise the XML sample data so that the **\<CustomerID>** child element appears before the **\<Order>** child element, you get the expected result: XML Bulk Load inserts the specified foreign key value into the column.</span></span>  
  
 <span data-ttu-id="e1589-117">這是相等的 XDR 結構描述：</span><span class="sxs-lookup"><span data-stu-id="e1589-117">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="CustomerID"  />  
   <ElementType name="CompanyName" />  
   <ElementType name="City"        />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust" >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
                 <sql:relationship  
                        key-relation    ="Cust"  
                        key             ="CustomerID"  
                        foreign-key     ="CustomerID"  
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
  
  
