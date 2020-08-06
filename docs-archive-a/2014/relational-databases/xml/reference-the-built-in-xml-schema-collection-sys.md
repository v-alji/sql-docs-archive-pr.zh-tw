---
title: 參考內建 XML 結構描述集合 (sys) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- sys XML schema collections [SQL Server]
- schema collections [SQL Server], predefined
- predefined XML schema collections [SQL Server]
- XML schema collections [SQL Server], predefined
- built-in XML schema collections [SQL Server]
ms.assetid: 1e118303-5df0-4ee4-bd8d-14ced7544144
author: rothja
ms.author: jroth
ms.openlocfilehash: 7fa30107e1746b33e3f9b8eb1cfa53d1f4d25fb8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688645"
---
# <a name="reference-the-built-in-xml-schema-collection-sys"></a><span data-ttu-id="40c6d-102">參考內建 XML 結構描述集合 (sys)</span><span class="sxs-lookup"><span data-stu-id="40c6d-102">Reference the Built-in XML Schema Collection (sys)</span></span>
  <span data-ttu-id="40c6d-103">您建立的每一個資料庫，在 **sys** 關聯式結構描述中，都有一個預先定義的 **sys** XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="40c6d-103">Every database you create has a predefined **sys** XML schema collection in the **sys** relational schema.</span></span> <span data-ttu-id="40c6d-104">此集合會保留這些預先定義的結構描述，所以從其他使用者建立的任何 XML 結構描述集合都能存取這些結構描述。</span><span class="sxs-lookup"><span data-stu-id="40c6d-104">It reserves these predefined schemas, and they can be accessed from any other user-created XML schema collection.</span></span> <span data-ttu-id="40c6d-105">這些預先定義的結構描述中使用的前置詞在 XQuery 中是有意義的。</span><span class="sxs-lookup"><span data-stu-id="40c6d-105">The prefixes used in these predefined schemas are meaningful in XQuery.</span></span> <span data-ttu-id="40c6d-106">只有 **xml** 是保留的前置詞。</span><span class="sxs-lookup"><span data-stu-id="40c6d-106">Only **xml** is a reserved prefix.</span></span>  
  
```  
xml = http://www.w3.org/XML/1998/namespace  
xs = http://www.w3.org/2001/XMLSchema  
xsi = http://www.w3.org/2001/XMLSchema-instance  
fn = http://www.w3.org/2004/07/xpath-functions  
sqltypes = https://schemas.microsoft.com/sqlserver/2004/sqltypes  
xdt = http://www.w3.org/2004/07/xpath-datatypes  
(no prefix) = urn:schemas-microsoft-com:xml-sql  
(no prefix) = https://schemas.microsoft.com/sqlserver/2004/SOAP  
```  
  
 <span data-ttu-id="40c6d-107">請注意， **sqltypes** 命名空間包含的元件可以從任何使用者建立的 XML 結構描述集合參考。</span><span class="sxs-lookup"><span data-stu-id="40c6d-107">Note that the **sqltypes** namespace contains components that can be referenced from any user-created XML schema collection.</span></span> <span data-ttu-id="40c6d-108">您可以從 **Microsoft 網站** 下載 [sqltypes](https://go.microsoft.com/fwlink/?linkid=31850)結構描述。</span><span class="sxs-lookup"><span data-stu-id="40c6d-108">You can download the **sqltypes** schema from this [Microsoft Web site](https://go.microsoft.com/fwlink/?linkid=31850).</span></span> <span data-ttu-id="40c6d-109">內建的元件包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="40c6d-109">The built-in components include the following:</span></span>  
  
-   <span data-ttu-id="40c6d-110">XSD 類型</span><span class="sxs-lookup"><span data-stu-id="40c6d-110">XSD types</span></span>  
  
-   <span data-ttu-id="40c6d-111">XML 屬性 **lang**, **base**及 **space**</span><span class="sxs-lookup"><span data-stu-id="40c6d-111">XML attributes **lang**, **base**, and **space**</span></span>  
  
-   <span data-ttu-id="40c6d-112">**sqltypes** 命名空間的元件</span><span class="sxs-lookup"><span data-stu-id="40c6d-112">Components of the **sqltypes** namespace</span></span>  
  
 <span data-ttu-id="40c6d-113">下列查詢會傳回可以從使用者建立之 XML 結構描述集合參考的內建元件：</span><span class="sxs-lookup"><span data-stu-id="40c6d-113">The following query returns built-in components that can be referenced from a user-created XML schema collection:</span></span>  
  
```  
SELECT C.name, N.name, C.symbol_space_desc from sys.xml_schema_components C join sys.xml_schema_namespaces N  
on ((C.xml_namespace_id = N.xml_namespace_id) AND (C.xml_collection_id = N.xml_collection_id))  
join sys.xml_schema_collections SC  
on SC.xml_collection_id = C.xml_collection_id  
where ((C.xml_collection_id = 1) AND (C.name is not null) AND (C.scoping_xml_component_id is null)   
AND (SC.schema_id = 4))  
GO  
```  
  
 <span data-ttu-id="40c6d-114">下列範例顯示這些元件在使用者結構描述中的參考方式。</span><span class="sxs-lookup"><span data-stu-id="40c6d-114">The following example shows how these components are referenced in a user schema.</span></span> <span data-ttu-id="40c6d-115">`CREATE XML SCHEMA COLLECTION` 建立 XML 結構描述集合，其參考 `varchar` 命名空間中所定義的 `sqltypes` 類型。</span><span class="sxs-lookup"><span data-stu-id="40c6d-115">`CREATE XML SCHEMA COLLECTION` creates an XML schema collection that references the `varchar` type defined in the `sqltypes` namespace.</span></span> <span data-ttu-id="40c6d-116">此範例也會參考 `lang` 命名空間中定義的 `xml` 屬性。</span><span class="sxs-lookup"><span data-stu-id="40c6d-116">The example also references the `lang` attribute that is defined in the `xml` namespace.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema   
   xmlns="http://www.w3.org/2001/XMLSchema"   
   targetNamespace="myNS"  
   xmlns:ns="myNS"  
   xmlns:s="https://schemas.microsoft.com/sqlserver/2004/sqltypes" >   
   <import namespace="http://www.w3.org/XML/1998/namespace"/>  
   <import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes"/>  
   <element name="root">  
      <complexType>  
          <sequence>  
             <element name="a" type="string"/>  
             <element name="b" type="string"/>  
             <!-- varchar type is defined in the sys.sys collection and   
                  can be referenced in any user-defined schema -->  
             <element name="c" type="s:varchar"/>  
          </sequence>  
          <attribute name="att" type="int"/>  
          <!-- xml:lang attribute is defined in the sys.sys collection   
               and can be referenced in any user-defined schema -->  
          <attribute ref="xml:lang"/>  
      </complexType>  
    </element>  
 </schema>'  
GO  
 -- Cleanup  
DROP xml schema collection SC   
GO  
```  
  
 <span data-ttu-id="40c6d-117">您應該注意下列各項：</span><span class="sxs-lookup"><span data-stu-id="40c6d-117">You should note the following:</span></span>  
  
-   <span data-ttu-id="40c6d-118">您不能在任何使用者自訂 XML 結構描述集合中，使用這些命名空間來修改 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="40c6d-118">You cannot modify XML schemas with these namespaces in any user-defined XML schema collection.</span></span> <span data-ttu-id="40c6d-119">例如，下列的 XML 結構描述集合會失敗，因為它把元件加入到 `sqltypes` 保護的命名空間：</span><span class="sxs-lookup"><span data-stu-id="40c6d-119">For example, the following XML schema collection fails, because it is adding a component to the `sqltypes` protected namespace:</span></span>  
  
    ```  
    CREATE XML SCHEMA COLLECTION SC AS '  
    <schema xmlns="http://www.w3.org/2001/XMLSchema"   
    targetNamespace    
        ="https://schemas.microsoft.com/sqlserver/2004/sqltypes" >   
          <element name="root" type="string"/>  
    </schema>'  
    GO  
    ```  
  
-   <span data-ttu-id="40c6d-120">您不能使用 `sys` XML 結構描述集合來鍵入 `xml` 資料行、變數或參數。</span><span class="sxs-lookup"><span data-stu-id="40c6d-120">You cannot use the `sys` XML schema collection to type `xml` columns, variables, or parameters.</span></span> <span data-ttu-id="40c6d-121">例如，下列程式碼會傳回錯誤：</span><span class="sxs-lookup"><span data-stu-id="40c6d-121">For example, the following code returns an error:</span></span>  
  
    ```  
    DECLARE @x xml (sys.sys)  
    ```  
  
-   <span data-ttu-id="40c6d-122">不支援這些內建結構描述的序列化。</span><span class="sxs-lookup"><span data-stu-id="40c6d-122">Serialization of these built-in schemas is not supported.</span></span> <span data-ttu-id="40c6d-123">例如，下列程式碼會傳回錯誤：</span><span class="sxs-lookup"><span data-stu-id="40c6d-123">For example, the following code returns an error:</span></span>  
  
    ```  
    SELECT XML_SCHEMA_NAMESPACE(N'sys',N'sys')  
    GO  
    ```  
  
 <span data-ttu-id="40c6d-124">下列程式碼是另一個範例，在此您將建立一個 XML 結構描述集合，此結構描述集合會使用 `varchar` 命名空間中定義的 `sqltypes` 類型：</span><span class="sxs-lookup"><span data-stu-id="40c6d-124">The following code is another example in which you create an XML schema collection that uses the `varchar` type defined in the `sqltypes` namespace:</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"   
        targetNamespace="myNS" xmlns:ns="myNS"  
        xmlns:s="https://schemas.microsoft.com/sqlserver/2004/sqltypes">  
   <import     
     namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes"/>  
      <simpleType name="myType">  
            <restriction base="s:varchar">  
                  <maxLength value="20"/>  
            </restriction>  
      </simpleType>  
      <element name="root" type="ns:myType"/>  
</schema>'  
go  
```  
  
 <span data-ttu-id="40c6d-125">如下所示，您可以建立 `XML` 類型的變數，將 XML 執行個體指派給這個變數，並確認 <`root`> 元素類型的值是 `varchar` 類型。</span><span class="sxs-lookup"><span data-stu-id="40c6d-125">As shown in the following, you can create a typed `XML` variable, assign an XML instance to it, and verify that the value of the <`root`> element type is a `varchar` type.</span></span>  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root xmlns="myNS">My data</root>'  
SELECT @var.query('declare namespace sqltypes = "https://schemas.microsoft.com/sqlserver/2004/sqltypes";  
declare namespace ns="myNS";   
data(/ns:root[1]) instance of sqltypes:varchar?')  
GO  
```  
  
 <span data-ttu-id="40c6d-126">`instance of sqltypes:varchar?` 運算式會傳回 TRUE，因為 <`root`> 元素值的類型是由 **varchar** 衍生而來 (根據與 `@var` 變數相關的結構描述而衍生)。</span><span class="sxs-lookup"><span data-stu-id="40c6d-126">The `instance of sqltypes:varchar?` expression returns TRUE, because the <`root`> element value is of a type derived from **varchar** according to the schema that is associated with the `@var` variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c6d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40c6d-127">See Also</span></span>  
 [<span data-ttu-id="40c6d-128">XML 結構描述集合 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40c6d-128">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
  
  
