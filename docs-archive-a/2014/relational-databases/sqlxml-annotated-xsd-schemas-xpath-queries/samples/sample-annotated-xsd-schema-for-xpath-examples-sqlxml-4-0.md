---
title: XPath 範例的批註式 XSD 架構範例 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], annotated XSD schemas in queries
- annotated XSD schemas, samples
- annotated XSD schemas, queries
ms.assetid: fefa2cc8-2d3c-4336-aeae-ce063a3a8df2
author: rothja
ms.author: jroth
ms.openlocfilehash: 7c7065bed89d867dda3ecffc7d80f2f729832e2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585239"
---
# <a name="sample-annotated-xsd-schema-for-xpath-examples-sqlxml-40"></a><span data-ttu-id="4b9df-102">XPath 範例的範例註解式 XSD 結構描述 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="4b9df-102">Sample Annotated XSD Schema for XPath Examples (SQLXML 4.0)</span></span>
  <span data-ttu-id="4b9df-103">本章節的範例 XPath 查詢會參考對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="4b9df-103">The sample XPath queries in this section refer to a mapping schema.</span></span> <span data-ttu-id="4b9df-104">此對應結構描述是註解式 XML 結構描述 (XSD) 檔案。</span><span class="sxs-lookup"><span data-stu-id="4b9df-104">The mapping schema is an annotated XML Schema (XSD) file.</span></span> <span data-ttu-id="4b9df-105">如需對應架構的詳細資訊，請參閱[批註式 XSD 架構簡介 &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="4b9df-105">For more information about mapping schemas, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="4b9df-106">以下是針對註解式 XSD 結構描述執行 XPath 查詢所需的處理：</span><span class="sxs-lookup"><span data-stu-id="4b9df-106">The following are needed to execute XPath queries against an annotated XSD schema:</span></span>  
  
-   <span data-ttu-id="4b9df-107">建立包含 XPath 查詢的範本。</span><span class="sxs-lookup"><span data-stu-id="4b9df-107">Create a template with an XPath query in it.</span></span> <span data-ttu-id="4b9df-108">在此範本中，您會指定 XPath 查詢執行時所要針對的對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="4b9df-108">In the template, you specify the mapping schema against which the XPath query is to be executed.</span></span> <span data-ttu-id="4b9df-109">在此案例中，對應結構描述必須儲存在與範本檔案相關的目錄中 (或是它的一個子目錄，其中會將相對路徑指定為範本中的 `mapping-schema` 屬性值)。</span><span class="sxs-lookup"><span data-stu-id="4b9df-109">In this case, the mapping schema must be stored in the directory (or one of its subdirectories, in which case a relative path is specified as the value of the `mapping-schema` attribute in the template) associated with template file.</span></span>  
  
-   <span data-ttu-id="4b9df-110">建立一個將 SQLXML 延伸模組用於 ADO 來執行查詢的測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b9df-110">Create a test application that uses SQLXML extensions for ADO to execute queries.</span></span> <span data-ttu-id="4b9df-111">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="4b9df-111">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="4b9df-112">在本章節的所有範例中，為了加以說明，將會在範本中指定 XPath 查詢，而且會使用 ADO 來執行此範本。</span><span class="sxs-lookup"><span data-stu-id="4b9df-112">In all the examples in this section, for illustration purposes, the XPath queries are specified in a template and the template is executed using ADO.</span></span> <span data-ttu-id="4b9df-113">因此，您必須使用下列的對應結構描述檔案 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="4b9df-113">Therefore, you must use the following mapping schema file, SampleSchema1.xml.</span></span> <span data-ttu-id="4b9df-114">將這個檔案儲存在您存放範本的目錄中。</span><span class="sxs-lookup"><span data-stu-id="4b9df-114">Save this file in the directory where your templates are stored.</span></span>  
  
## <a name="sample-annotated-xsd-schema-sampleschema1xml"></a><span data-ttu-id="4b9df-115">範例註解式 XSD 結構描述 (SampleSchema1.xml)</span><span class="sxs-lookup"><span data-stu-id="4b9df-115">Sample Annotated XSD Schema (SampleSchema1.xml)</span></span>  
  
```  
<?xml version="1.0"?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="CustOrders"  
                        parent="Sales.Customer"  
                        parent-key="CustomerID"  
                        child="Sales.SalesOrderHeader"  
                        child-key="CustomerID" />  
      <sql:relationship name="OrderOrderDetail"  
                        parent="Sales.SalesOrderHeader"  
                        parent-key="SalesOrderID"  
                        child="Sales.SalesOrderDetail"  
                        child-key="SalesOrderID" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustOrders" />  
     </xsd:sequence>  
     <xsd:attribute name="CustomerID" type="xsd:ID"/>  
     <xsd:attribute name="TerritoryID"/>  
     <xsd:attribute name="AccountNumber"/>  
     <xsd:attribute name="CustomerType"/>  
     <xsd:attribute name="Orders" type="xsd:IDREFS" sql:prefix="Ord-"/>  
  </xsd:complexType>  
  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" type="OrderType"/>  
  
  <xsd:complexType name="OrderType">  
     <xsd:sequence>  
        <xsd:element name="OrderDetail"   
                     sql:relation="Sales.SalesOrderDetail"  
                     sql:relationship="OrderOrderDetail" />  
     </xsd:sequence>  
     <xsd:attribute name="SalesOrderID" type="xsd:ID" sql:prefix="Ord-"/>  
     <xsd:attribute name="SalesPersonID"/>  
     <xsd:attribute name="OrderDate"/>  
     <xsd:attribute name="DueDate"/>  
     <xsd:attribute name="ShipDate"/>  
  </xsd:complexType>  
  
  <xsd:element name="OrderDetail" sql:relation="Sales.SalesOrderDetail" type="OrderDetailType"/>  
  
  <xsd:complexType name="OrderDetailType">  
    <xsd:attribute name="ProductID" type="xsd:IDREF"/>  
    <xsd:attribute name="UnitPrice"/>  
    <xsd:attribute name="OrderQty"/>  
    <xsd:attribute name="UnitPriceDiscount"/>  
  </xsd:complexType>  
  
  <xsd:element name="UnitPriceDiscount" sql:relation="Sales.SalesOrderDetail" type="DiscountType"/>  
  
  <xsd:complexType name="DiscountType">  
    <xsd:simpleContent>  
       <xsd:extension base="xsd:string">  
          <xsd:anyAttribute namespace="##other" processContents="lax"/>  
       </xsd:extension>  
    </xsd:simpleContent>  
  </xsd:complexType>  
  
  <xsd:element name="Contact" sql:relation="Person.Contact" type="ContactType"/>  
  
  <xsd:complexType name="ContactType">  
    <xsd:attribute name="ContactID"/>  
    <xsd:attribute name="LastName"/>  
    <xsd:attribute name="FirstName"/>  
    <xsd:attribute name="Title"/>  
  </xsd:complexType>  
  
</xsd:schema>  
```  
  
  
