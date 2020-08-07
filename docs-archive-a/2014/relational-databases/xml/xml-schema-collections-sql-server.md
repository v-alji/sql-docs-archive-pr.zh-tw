---
title: XML 結構描述集合 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XSD schemas [SQL Server]
- xml_schema_namespace function
- XML schema collections [SQL Server], about XML schema collections
- metadata [SQL Server], XML schema collections
- queries [XML in SQL Server], XML schema collections
- schema collections [SQL Server]
- schemas [SQL Server], XML
- XML [SQL Server], schema collections
- XML schema collections [SQL Server]
- schema collections [SQL Server], about XML schema collections
ms.assetid: 659d41aa-ccec-4554-804a-722a96ef25c2
author: rothja
ms.author: jroth
ms.openlocfilehash: 3ee4757f1353278447ee55e97c8d4ba23aa2d649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597676"
---
# <a name="xml-schema-collections-sql-server"></a><span data-ttu-id="e66b8-102">XML 結構描述集合 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e66b8-102">XML Schema Collections (SQL Server)</span></span>
  <span data-ttu-id="e66b8-103">如[xml &#40;transact-sql&#41;](/sql/t-sql/xml/xml-transact-sql)主題中所述，SQL Server 透過資料類型提供 xml 資料的原生儲存 `xml` 。</span><span class="sxs-lookup"><span data-stu-id="e66b8-103">As described in the topic, [xml &#40;Transact-SQL&#41;](/sql/t-sql/xml/xml-transact-sql), SQL Server provides native storage of XML data through the `xml` data type.</span></span> <span data-ttu-id="e66b8-104">您可以選擇透過 XML 架構集合，將 XSD 架構與變數或類型的資料行 `xml` 產生關聯。</span><span class="sxs-lookup"><span data-stu-id="e66b8-104">You can optionally associate XSD schemas with a variable or a column of `xml` type through an XML schema collection.</span></span> <span data-ttu-id="e66b8-105">XML 結構描述集合會儲存匯入的 XML 結構描述，然後用來執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e66b8-105">The XML schema collection stores the imported XML schemas and is then used to do the following:</span></span>  
  
-   <span data-ttu-id="e66b8-106">驗證 XML 執行個體</span><span class="sxs-lookup"><span data-stu-id="e66b8-106">Validate XML instances</span></span>  
  
-   <span data-ttu-id="e66b8-107">當 XML 資料儲存在資料庫中時，設定其類型</span><span class="sxs-lookup"><span data-stu-id="e66b8-107">Type the XML data as it is stored in the database</span></span>  
  
 <span data-ttu-id="e66b8-108">請注意，XML 結構描述集合是一個中繼資料實體，就像資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="e66b8-108">Note that the XML schema collection is a metadata entity like a table in the database.</span></span> <span data-ttu-id="e66b8-109">您可以加以建立、修改及卸除。</span><span class="sxs-lookup"><span data-stu-id="e66b8-109">You can create, modify, and drop them.</span></span> <span data-ttu-id="e66b8-110">系統會將 [CREATE XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) 陳述式中所指定的結構描述，自動匯入新建的 XML 結構描述集合物件中。</span><span class="sxs-lookup"><span data-stu-id="e66b8-110">Schemas specified in a [CREATE XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) statement are automatically imported into the newly created XML schema collection object.</span></span> <span data-ttu-id="e66b8-111">您可以使用 [ALTER XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) 陳述式，將其他的結構描述或結構描述元件匯入資料庫的現有集合物件中。</span><span class="sxs-lookup"><span data-stu-id="e66b8-111">You can import additional schemas or schema components into an existing collection object in the database by using the [ALTER XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="e66b8-112">如[比較具類型的 XML 與不具類型的 XML](../xml/compare-typed-xml-to-untyped-xml.md) 主題所述，如果 XML 是儲存在有關聯之結構描述的資料行或變數中，即為**具類型的** XML，因為結構描述會提供執行個體資料所需的資料類型資訊。</span><span class="sxs-lookup"><span data-stu-id="e66b8-112">As described in the topic, [Typed vs. Untyped XML](../xml/compare-typed-xml-to-untyped-xml.md), the XML stored in a column or variable that a schema is associated with is referred to as **typed** XML, because the schema provides the necessary data type information for the instance data.</span></span> <span data-ttu-id="e66b8-113">SQL Server 會使用此類型資訊來將資料儲存最佳化。</span><span class="sxs-lookup"><span data-stu-id="e66b8-113">SQL Server uses this type information to optimize data storage.</span></span>  
  
 <span data-ttu-id="e66b8-114">查詢處理引擎也會使用結構描述來檢查類型，以及將查詢和資料修改最佳化。</span><span class="sxs-lookup"><span data-stu-id="e66b8-114">The query-processing engine also uses the schema for type checking and to optimize queries and data modification.</span></span>  
  
 <span data-ttu-id="e66b8-115">此外，SQL Server 會使用相關聯的 XML 架構集合（在具類型的情況下） `xml` 來驗證 XML 實例。</span><span class="sxs-lookup"><span data-stu-id="e66b8-115">Also, SQL Server uses the associated XML schema collection, in the case of typed `xml`, to validate the XML instance.</span></span> <span data-ttu-id="e66b8-116">如果 XML 執行個體符合結構描述，資料庫就會允許執行個體以其類型資訊儲存在系統中。</span><span class="sxs-lookup"><span data-stu-id="e66b8-116">If the XML instance complies with the schema, the database allows the instance to be stored in the system with their type information.</span></span> <span data-ttu-id="e66b8-117">否則，資料庫會拒絕該執行個體。</span><span class="sxs-lookup"><span data-stu-id="e66b8-117">Otherwise, it rejects the instance.</span></span>  
  
 <span data-ttu-id="e66b8-118">您可以使用內建函數 XML_SCHEMA_NAMESPACE 來擷取儲存在資料庫中的結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="e66b8-118">You can use the intrinsic function XML_SCHEMA_NAMESPACE to retrieve the schema collection that is stored in the database.</span></span> <span data-ttu-id="e66b8-119">如需詳細資訊，請參閱 [檢視儲存的 XML 結構描述集合](../xml/view-a-stored-xml-schema-collection.md)。</span><span class="sxs-lookup"><span data-stu-id="e66b8-119">For more information, see [View a Stored XML Schema Collection](../xml/view-a-stored-xml-schema-collection.md).</span></span>  
  
 <span data-ttu-id="e66b8-120">您也可以使用 XML 結構描述集合來輸入 XML 變數、參數及資料行。</span><span class="sxs-lookup"><span data-stu-id="e66b8-120">You can also use the XML schema collection to type XML variables, parameters, and columns.</span></span>  
  
##  <a name="ddl-for-managing-schema-collections"></a><a name="ddl"></a> <span data-ttu-id="e66b8-121">管理結構描述集合的 DDL</span><span class="sxs-lookup"><span data-stu-id="e66b8-121">DDL for Managing Schema Collections</span></span>  
 <span data-ttu-id="e66b8-122">您可以在資料庫中建立 XML 結構描述集合，然後將它們與 `xml` 類型的變數和資料行產生關聯。</span><span class="sxs-lookup"><span data-stu-id="e66b8-122">You can create XML schema collections in the database and associate them with variables and columns of `xml` type.</span></span> <span data-ttu-id="e66b8-123">為了管理資料庫中的結構描述集合， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供了下列 DDL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="e66b8-123">To manage schema collections in the database, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides the following DDL statements:</span></span>  
  
-   <span data-ttu-id="e66b8-124">[CREATE XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) 將結構描述元件匯入資料庫中。</span><span class="sxs-lookup"><span data-stu-id="e66b8-124">[CREATE XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) Imports schema components into a database.</span></span>  
  
-   <span data-ttu-id="e66b8-125">[ALTER XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) 修改現有 XML 結構描述集合中的結構描述元件。</span><span class="sxs-lookup"><span data-stu-id="e66b8-125">[ALTER XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) Modifies the schema components in an existing XML schema collection.</span></span>  
  
-   <span data-ttu-id="e66b8-126">[DROP XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql) 刪除整個 XML 結構描述集合及其所有的元件。</span><span class="sxs-lookup"><span data-stu-id="e66b8-126">[DROP XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql) Deletes a complete XML schema collection and all its components.</span></span>  
  
 <span data-ttu-id="e66b8-127">若要使用 XML 結構描述集合及其包含的結構描述，您必須先使用 CREATE XML SCHEMA COLLECTION 陳述式來建立集合和結構描述。</span><span class="sxs-lookup"><span data-stu-id="e66b8-127">To use an XML schema collection and the schemas it contains, you must first create the collection and the schemas by using the CREATE XML SCHEMA COLLECTION statement.</span></span> <span data-ttu-id="e66b8-128">在建立結構描述集合之後，您就可以建立 `xml` 類型的變數和資料行，並將結構描述集合與它們產生關聯。</span><span class="sxs-lookup"><span data-stu-id="e66b8-128">After the schema collection is created, you can then create variables and columns of `xml` type and associate the schema collection with them.</span></span> <span data-ttu-id="e66b8-129">請注意，建立結構描述集合之後，各種結構描述元件會儲存在中繼資料內。</span><span class="sxs-lookup"><span data-stu-id="e66b8-129">Note that after a schema collection is created, various schema components are stored in the metadata.</span></span> <span data-ttu-id="e66b8-130">您也可以使用 ALTER XML SCHEMA COLLECTION 將更多元件加入現有的結構描述，或將新的結構描述加入現有的集合。</span><span class="sxs-lookup"><span data-stu-id="e66b8-130">You can also use the ALTER XML SCHEMA COLLECTION to add more components to the existing schemas or add new schemas to an existing collection.</span></span>  
  
 <span data-ttu-id="e66b8-131">若要卸除結構描述集合，請使用 DROP XML SCHEMA COLLECTION 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e66b8-131">To drop the schema collection, use the DROP XML SCHEMA COLLECTION statement.</span></span> <span data-ttu-id="e66b8-132">這會卸除集合中包含的所有結構描述，並移除集合物件。</span><span class="sxs-lookup"><span data-stu-id="e66b8-132">This drops all schemas that are contained in the collection and removes the collection object.</span></span> <span data-ttu-id="e66b8-133">請注意，必須符合 [DROP XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql) 中描述的條件，才能卸除結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="e66b8-133">Note that before you can drop a schema collection, the conditions described in [DROP XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql)must be met.</span></span>  
  
##  <a name="understanding-schema-components"></a><a name="components"></a> <span data-ttu-id="e66b8-134">了解結構描述元件</span><span class="sxs-lookup"><span data-stu-id="e66b8-134">Understanding Schema Components</span></span>  
 <span data-ttu-id="e66b8-135">當您使用 CREATE XML SCHEMA COLLECTION 陳述式時，會將各種結構描述元件匯入資料庫中。</span><span class="sxs-lookup"><span data-stu-id="e66b8-135">When you use the CREATE XML SCHEMA COLLECTION statement, various schema components are imported into the database.</span></span> <span data-ttu-id="e66b8-136">結構描述元件包括結構描述元素、屬性和類型定義。</span><span class="sxs-lookup"><span data-stu-id="e66b8-136">Schema components include schema elements, attributes, and type definitions.</span></span> <span data-ttu-id="e66b8-137">當您使用 DROP XML SCHEMA COLLECTION 陳述式時，整個集合都會移除。</span><span class="sxs-lookup"><span data-stu-id="e66b8-137">When you use the DROP XML SCHEMA COLLECTION statement, you remove the complete collection.</span></span>  
  
 <span data-ttu-id="e66b8-138">CREATE XML SCHEMA COLLECTION 會將結構描述元件儲存到各種系統資料表中。</span><span class="sxs-lookup"><span data-stu-id="e66b8-138">CREATE XML SCHEMA COLLECTION saves the schema components into various system tables.</span></span>  
  
 <span data-ttu-id="e66b8-139">例如，請考慮下列結構描述：</span><span class="sxs-lookup"><span data-stu-id="e66b8-139">For example, consider the following schema:</span></span>  
  
```  
<?xml version="1.0"?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            targetNamespace="uri:Cust_Orders2"  
            xmlns="uri:Cust_Orders2" >  
  <xsd:attribute name="SomeAttribute" type="xsd:int" />  
  <xsd:complexType name="SomeType" />  
  <xsd:complexType name="OrderType" >  
    <xsd:sequence>  
      <xsd:element name="OrderDate" type="xsd:date" />  
      <xsd:element name="RequiredDate" type="xsd:date" />  
      <xsd:element name="ShippedDate" type="xsd:date" />  
    </xsd:sequence>  
    <xsd:attribute name="OrderID" type="xsd:ID" />  
    <xsd:attribute name="CustomerID"  />  
    <xsd:attribute name="EmployeeID"  />  
  </xsd:complexType>  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order" type="OrderType"  
                     maxOccurs="unbounded" />  
       </xsd:sequence>  
      <xsd:attribute name="CustomerID" type="xsd:string" />  
      <xsd:attribute name="OrderIDList" type="xsd:IDREFS" />  
  </xsd:complexType>  
  <xsd:element name="Customer" type="CustomerType" />  
</xsd:schema>  
```  
  
 <span data-ttu-id="e66b8-140">以上的結構描述顯示可儲存於資料庫的不同類型元件，</span><span class="sxs-lookup"><span data-stu-id="e66b8-140">The previous schema shows the different types of components that can be stored in the database.</span></span> <span data-ttu-id="e66b8-141">這些元件包括 `SomeAttribute`、 `SomeType`、 `OrderType`、 `CustomerType`、 `Customer`、 `Order`、 `CustomerID`、 `OrderID`、 `OrderDate`、 `RequiredDate`及 `ShippedDate`。</span><span class="sxs-lookup"><span data-stu-id="e66b8-141">These include `SomeAttribute`, `SomeType`, `OrderType`, `CustomerType`, `Customer`, `Order`, `CustomerID`, `OrderID`, `OrderDate`, `RequiredDate`, and `ShippedDate`.</span></span>  
  
### <a name="component-categories"></a><span data-ttu-id="e66b8-142">元件類別</span><span class="sxs-lookup"><span data-stu-id="e66b8-142">Component Categories</span></span>  
 <span data-ttu-id="e66b8-143">儲存在資料庫中的「結構描述」元件可分成下列類別：</span><span class="sxs-lookup"><span data-stu-id="e66b8-143">The Schema components stored in the database fall into the following categories:</span></span>  
  
-   <span data-ttu-id="e66b8-144">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="e66b8-144">ELEMENT</span></span>  
  
-   <span data-ttu-id="e66b8-145">ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="e66b8-145">ATTRIBUTE</span></span>  
  
-   <span data-ttu-id="e66b8-146">TYPE (適用於簡單或複雜類型)</span><span class="sxs-lookup"><span data-stu-id="e66b8-146">TYPE (for simple or complex types)</span></span>  
  
-   <span data-ttu-id="e66b8-147">ATTRIBUTEGROUP</span><span class="sxs-lookup"><span data-stu-id="e66b8-147">ATTRIBUTEGROUP</span></span>  
  
-   <span data-ttu-id="e66b8-148">MODELGROUP</span><span class="sxs-lookup"><span data-stu-id="e66b8-148">MODELGROUP</span></span>  
  
 <span data-ttu-id="e66b8-149">例如：</span><span class="sxs-lookup"><span data-stu-id="e66b8-149">For example:</span></span>  
  
-   <span data-ttu-id="e66b8-150">**SomeAttribute** 是 ATTRIBUTE 元件。</span><span class="sxs-lookup"><span data-stu-id="e66b8-150">**SomeAttribute** is an ATTRIBUTE component.</span></span>  
  
-   <span data-ttu-id="e66b8-151">**SomeType**、 **OrderType**和 **CustomerType** 是 TYPE 元件。</span><span class="sxs-lookup"><span data-stu-id="e66b8-151">**SomeType**, **OrderType**, and **CustomerType** are TYPE components.</span></span>  
  
-   <span data-ttu-id="e66b8-152">**Customer** 是 ELEMENT 元件。</span><span class="sxs-lookup"><span data-stu-id="e66b8-152">**Customer** is an ELEMENT component.</span></span>  
  
 <span data-ttu-id="e66b8-153">當您將結構描述匯入資料庫後， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 並不會儲存結構描述本身。</span><span class="sxs-lookup"><span data-stu-id="e66b8-153">When you import a schema into the database, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not store the schema itself.</span></span> <span data-ttu-id="e66b8-154">不過， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會儲存各種個別的元件。</span><span class="sxs-lookup"><span data-stu-id="e66b8-154">Instead, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stores the various individual components.</span></span> <span data-ttu-id="e66b8-155">亦即，並未儲存 \<Schema> 標記，只是保留定義於其中的元件。</span><span class="sxs-lookup"><span data-stu-id="e66b8-155">That is, the \<Schema> tag is not stored, only the components that are defined within it are preserved.</span></span> <span data-ttu-id="e66b8-156">所有的結構描述元素都沒有保留。</span><span class="sxs-lookup"><span data-stu-id="e66b8-156">All schema elements are not preserved.</span></span> <span data-ttu-id="e66b8-157">若 \<Schema> 標記包含指定其元件預設行為的屬性，則這些屬性會在匯入程序期間移至標記內的結構描述元件，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="e66b8-157">If the \<Schema> tag contains attributes that specify default behavior of its components, these attributes are moved to the schema components within it during the import process, as shown in the following table.</span></span>  
  
|<span data-ttu-id="e66b8-158">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="e66b8-158">Attribute name</span></span>|<span data-ttu-id="e66b8-159">行為</span><span class="sxs-lookup"><span data-stu-id="e66b8-159">Behavior</span></span>|  
|--------------------|--------------|  
|<span data-ttu-id="e66b8-160">**attributeFormDefault**</span><span class="sxs-lookup"><span data-stu-id="e66b8-160">**attributeFormDefault**</span></span>|<span data-ttu-id="e66b8-161">**form** 屬性會套用到結構描述中尚未出現此屬性的所有屬性宣告上，而且其值會設定為 **attributeFormDefault** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="e66b8-161">The **form** attribute applied to all attribute declarations in the schema where it is not already present and the value is set to the value of the **attributeFormDefault** attribute.</span></span>|  
|<span data-ttu-id="e66b8-162">**elementFormDefault**</span><span class="sxs-lookup"><span data-stu-id="e66b8-162">**elementFormDefault**</span></span>|<span data-ttu-id="e66b8-163">**form** 屬性會套用到結構描述中尚未出現此屬性的所有元素宣告上，而且其值會設定為 **elementFormDefault** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="e66b8-163">The **form** attribute applied to all element declarations in the schema where it is not already present and the value is set to the value of the **elementFormDefault** attribute.</span></span>|  
|<span data-ttu-id="e66b8-164">**blockDefault**</span><span class="sxs-lookup"><span data-stu-id="e66b8-164">**blockDefault**</span></span>|<span data-ttu-id="e66b8-165">**block** 屬性會套用到尚未出現此屬性的所有元素宣告和類型定義上，而且其值會設定為 **blockDefault** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="e66b8-165">The **block** attribute applied to all element declarations and type definitions where it is not already present and the value is set to the value of the **blockDefault** attribute.</span></span>|  
|<span data-ttu-id="e66b8-166">**finalDefault**</span><span class="sxs-lookup"><span data-stu-id="e66b8-166">**finalDefault**</span></span>|<span data-ttu-id="e66b8-167">**final** 屬性會套用到尚未出現此屬性的所有元素宣告和類型定義上，而且其值會設定為 **finalDefault** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="e66b8-167">The **final** attribute applied to all element declarations and type definitions where it is not already present and the value is set to the value of the **finalDefault** attribute.</span></span>|  
|<span data-ttu-id="e66b8-168">**targetNamespace**</span><span class="sxs-lookup"><span data-stu-id="e66b8-168">**targetNamespace**</span></span>|<span data-ttu-id="e66b8-169">隸屬於目標命名空間之元件的詳細資訊會儲存在中繼資料內。</span><span class="sxs-lookup"><span data-stu-id="e66b8-169">Information about the components that belong to the target namespace is stored in the metadata.</span></span>|  
  
##  <a name="permissions-on-an-xml-schema-collection"></a><a name="perms"></a> <span data-ttu-id="e66b8-170">XML 結構描述集合上的權限</span><span class="sxs-lookup"><span data-stu-id="e66b8-170">Permissions on an XML Schema Collection</span></span>  
 <span data-ttu-id="e66b8-171">您必須有必要權限，才能執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e66b8-171">You must have the necessary permissions to do the following:</span></span>  
  
-   <span data-ttu-id="e66b8-172">建立/載入 XML 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="e66b8-172">Create/load the XML schema collection</span></span>  
  
-   <span data-ttu-id="e66b8-173">修改 XML 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="e66b8-173">Modify the XML schema collection</span></span>  
  
-   <span data-ttu-id="e66b8-174">卸除 XML 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="e66b8-174">Drop the XML schema collection</span></span>  
  
-   <span data-ttu-id="e66b8-175">使用 XML 架構集合來輸入 `xml` 類型資料行、變數和參數，或在資料表或資料行條件約束中使用它</span><span class="sxs-lookup"><span data-stu-id="e66b8-175">Use the XML schema collection to type `xml` type columns, variables, and parameters, or use it in table or column constraints</span></span>  
  
 <span data-ttu-id="e66b8-176">SQL Server 安全性模型允許在每個物件上都可以有 CONTROL 權限。</span><span class="sxs-lookup"><span data-stu-id="e66b8-176">The SQL Server security model allows CONTROL permission on every object.</span></span> <span data-ttu-id="e66b8-177">此權限的被授與者可取得物件上的所有其他權限。</span><span class="sxs-lookup"><span data-stu-id="e66b8-177">The grantee of this permission obtains all other permissions on the object.</span></span> <span data-ttu-id="e66b8-178">物件的擁有者也擁有該物件的所有權限。</span><span class="sxs-lookup"><span data-stu-id="e66b8-178">The owner of the object also has all the permissions on the object.</span></span>  
  
 <span data-ttu-id="e66b8-179">某物件上 CONTROL 權限的擁有者和被授與者，可以授與該物件上的任何權限。</span><span class="sxs-lookup"><span data-stu-id="e66b8-179">The owner and the grantee of the CONTROL permission on an object can grant any permission on the object.</span></span> <span data-ttu-id="e66b8-180">如果指定了 WITH GRANT OPTION，不是擁有者的使用者或沒有 CONTROL 權限的使用者仍可以授與物件上的權限。</span><span class="sxs-lookup"><span data-stu-id="e66b8-180">A user who is not the owner and does not have CONTROL permission can still grant permission on an object when WITH GRANT OPTION is specified.</span></span> <span data-ttu-id="e66b8-181">例如，假設「使用者 A」透過 WITH GRANT OPTION，對於 XML 結構描述集合 S 擁有 REFERENCES 權限，但沒有其他權限。「使用者 A」可以授與「使用者 B」對於結構描述集合 S 的 REFERENCES 權限。</span><span class="sxs-lookup"><span data-stu-id="e66b8-181">For example, assume User A has REFERENCES permission on XML schema collection S, through WITH GRANT OPTION, but no other permissions on S. User A could grant User B REFERENCES permission on schema collection S.</span></span>  
  
 <span data-ttu-id="e66b8-182">安全性模型也允許建立和使用 XML 結構描述集合的權限，或將所有權從某個使用者轉給另一個使用者的權限。</span><span class="sxs-lookup"><span data-stu-id="e66b8-182">The security model also allows permissions to create and use XML schema collections or transfer ownership from one user to another.</span></span> <span data-ttu-id="e66b8-183">下列主題描述 XML 結構描述集合權限。</span><span class="sxs-lookup"><span data-stu-id="e66b8-183">The following topics describe the XML schema collection permissions.</span></span>  
  
-   [<span data-ttu-id="e66b8-184">授與 XML 結構描述集合的權限</span><span class="sxs-lookup"><span data-stu-id="e66b8-184">Grant Permissions on an XML Schema Collection</span></span>](../xml/grant-permissions-on-an-xml-schema-collection.md)  
  
     <span data-ttu-id="e66b8-185">此主題討論如何授與權限以建立 XML 結構描述集合，以及如何授與 XML 結構描述集合物件上的權限。</span><span class="sxs-lookup"><span data-stu-id="e66b8-185">This topic discussess how to grant permissions to create an XML schema collection and how to grant permissions on an XML schema collection object.</span></span>  
  
-   [<span data-ttu-id="e66b8-186">撤銷 XML 結構描述集合的權限</span><span class="sxs-lookup"><span data-stu-id="e66b8-186">Revoke Permissions on an XML Schema Collection</span></span>](../xml/revoke-permissions-on-an-xml-schema-collection.md)  
  
     <span data-ttu-id="e66b8-187">此主題討論如何使用撤銷權限以防止建立 XML 結構描述集合，以及如何撤銷 XML 結構描述集合物件上的權限。</span><span class="sxs-lookup"><span data-stu-id="e66b8-187">This topic discusses how revoking permissions can be used to prevent the creation of an XML schema collection and how to revoke permissions on an XML schema collection object.</span></span>  
  
-   [<span data-ttu-id="e66b8-188">拒絕 XML 結構描述集合的權限</span><span class="sxs-lookup"><span data-stu-id="e66b8-188">Deny Permissions on an XML Schema Collection</span></span>](../xml/deny-permissions-on-an-xml-schema-collection.md)  
  
     <span data-ttu-id="e66b8-189">此主題討論如何拒絕建立 XML 結構描述集合的權限，以及拒絕 XML 結構描述集合物件的權限。</span><span class="sxs-lookup"><span data-stu-id="e66b8-189">This topic discusses how to deny permissions to create an XML schema collection and deny permission on an XML schema collection object.</span></span>  
  
##  <a name="getting-information-about-xml-schemas-and-schema-collections"></a><a name="info"></a> <span data-ttu-id="e66b8-190">取得有關 XML 結構描述和結構描述集合的資訊</span><span class="sxs-lookup"><span data-stu-id="e66b8-190">Getting Information about XML Schemas and Schema Collections</span></span>  
 <span data-ttu-id="e66b8-191">XML 結構描述集合會列舉在目錄檢視 sys.xml_schema_collections 中。</span><span class="sxs-lookup"><span data-stu-id="e66b8-191">XML schema collections are enumerated in the catalog view, sys.xml_schema_collections.</span></span> <span data-ttu-id="e66b8-192">XML 結構描述集合 "sys" 是由系統定義的。</span><span class="sxs-lookup"><span data-stu-id="e66b8-192">The XML schema collection "sys" is defined by the system.</span></span> <span data-ttu-id="e66b8-193">其包含預先定義的命名空間，您不需要明確地將其載入，即可用在所有使用者自訂的 XML 結構描述集合中。</span><span class="sxs-lookup"><span data-stu-id="e66b8-193">It contains the predefined namespaces that can be used in all user-defined XML schema collections without having to load them explicitly.</span></span> <span data-ttu-id="e66b8-194">此清單包含 xml、xs、xsi、fn 及 xdt 的命名空間。</span><span class="sxs-lookup"><span data-stu-id="e66b8-194">This list contains the namespaces for xml, xs, xsi, fn, and xdt.</span></span> <span data-ttu-id="e66b8-195">另外二個目錄檢視為 sys.xml_schema_namespaces：列舉出每個 XML 結構描述集合中的所有命名空間；以及 sys.xml_components：列舉出每個 XML 結構描述中的所有 XML 結構描述元件。</span><span class="sxs-lookup"><span data-stu-id="e66b8-195">Two other catalog views are sys.xml_schema_namespaces, which enumerates all namespaces within each XML schema collection, and sys.xml_components, which enumerates all XML schema components within each XML schema.</span></span>  
  
 <span data-ttu-id="e66b8-196">內建函數**XML_SCHEMA_NAMESPACE** *schemaName，xmlschemacollectionname namespace-uri，NAMESPACE-uri*會產生 `xml` 資料類型實例。。</span><span class="sxs-lookup"><span data-stu-id="e66b8-196">The built-in function **XML_SCHEMA_NAMESPACE**, *schemaName, XmlSchemacollectionName, namespace-uri*, yields an `xml` data type instance..</span></span> <span data-ttu-id="e66b8-197">此執行個體包含 XML 結構描述集合中所包含之結構描述的 XML 結構描述片段 (預先定義的 XML 結構描述除外)。</span><span class="sxs-lookup"><span data-stu-id="e66b8-197">This instance contains XML schema fragments for schemas that are contained in an XML schema collection, except the predefined XML schemas.</span></span>  
  
 <span data-ttu-id="e66b8-198">您可以用下列方法來列舉 XML 結構描述集合的內容：</span><span class="sxs-lookup"><span data-stu-id="e66b8-198">You can enumerate the contents of an XML schema collection in the following ways:</span></span>  
  
-   <span data-ttu-id="e66b8-199">在 XML 結構描述集合的適當目錄檢視上撰寫 Transact-SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="e66b8-199">Write Transact-SQL queries on the appropriate catalog views for XML schema collections.</span></span>  
  
-   <span data-ttu-id="e66b8-200">使用內建函數 **XML_SCHEMA_NAMESPACE()** 。</span><span class="sxs-lookup"><span data-stu-id="e66b8-200">Use the built-in function **XML_SCHEMA_NAMESPACE()**.</span></span> <span data-ttu-id="e66b8-201">您可以將 `xml` 資料類型方法套用在此函數的輸出上。</span><span class="sxs-lookup"><span data-stu-id="e66b8-201">You can apply `xml` data type methods on the output of this function.</span></span> <span data-ttu-id="e66b8-202">但是您不能修改基礎 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="e66b8-202">However, you cannot modify the underlying XML schemas.</span></span>  
  
 <span data-ttu-id="e66b8-203">如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e66b8-203">These are illustrated in the following examples.</span></span>  
  
### <a name="example-enumerate-the-xml-namespaces-in-an-xml-schema-collection"></a><span data-ttu-id="e66b8-204">範例：列舉 XML 結構描述集合中的 XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="e66b8-204">Example: Enumerate the XML Namespaces in an XML Schema Collection</span></span>  
 <span data-ttu-id="e66b8-205">針對 XML 結構描述集合 "myCollection" 來使用下列查詢：</span><span class="sxs-lookup"><span data-stu-id="e66b8-205">Use the following query for the XML schema collection "myCollection":</span></span>  
  
```  
SELECT XSN.name  
FROM    sys.xml_schema_collections XSC JOIN sys.xml_schema_namespaces XSN  
    ON (XSC.xml_collection_id = XSN.xml_collection_id)  
WHERE    XSC.name = 'myCollection'     
```  
  
### <a name="example-enumerate-the-contents-of-an-xml-schema-collection"></a><span data-ttu-id="e66b8-206">範例：列舉 XML 結構描述集合的內容</span><span class="sxs-lookup"><span data-stu-id="e66b8-206">Example: Enumerate the Contents of an XML Schema Collection</span></span>  
 <span data-ttu-id="e66b8-207">下列陳述式會列舉關聯式結構描述 dbo 中之 XML 結構描述集合 "myCollection" 的內容。</span><span class="sxs-lookup"><span data-stu-id="e66b8-207">The following statement enumerates the contents of the XML schema collection "myCollection" within the relational schema, dbo.</span></span>  
  
```  
SELECT XML_SCHEMA_NAMESPACE (N'dbo', N'myCollection')  
```  
  
 <span data-ttu-id="e66b8-208">藉 `xml` 由將目標命名空間指定為**XML_SCHEMA_NAMESPACE ( # B1**的第三個引數，可以將集合中的個別 XML 架構當做資料類型實例來取得。</span><span class="sxs-lookup"><span data-stu-id="e66b8-208">Individual XML schemas within the collection can be obtained as `xml` data type instances by specifying the target namespace as the third argument to **XML_SCHEMA_NAMESPACE()**.</span></span> <span data-ttu-id="e66b8-209">下列範例會顯示這一點。</span><span class="sxs-lookup"><span data-stu-id="e66b8-209">This is shown in the following example.</span></span>  
  
### <a name="example-output-a-specified-schema-from-an-xml-schema-collection"></a><span data-ttu-id="e66b8-210">範例：從 XML 結構描述集合輸出指定的結構描述</span><span class="sxs-lookup"><span data-stu-id="e66b8-210">Example: Output a Specified Schema from an XML Schema Collection</span></span>  
 <span data-ttu-id="e66b8-211">下列陳述式會從關聯式結構描述 dbo 中的 XML 結構描述集合 "myCollection"，輸出含有目標命名空間 "<https://www.microsoft.com/books>" 的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="e66b8-211">The following statement outputs the XML schema with the target namespace "<https://www.microsoft.com/books>" from the XML schema collection "myCollection" within the relational schema, dbo.</span></span>  
  
```  
SELECT XML_SCHEMA_NAMESPACE (N'dbo', N'myCollection',   
N'https://www.microsoft.com/books')  
```  
  
### <a name="querying-xml-schemas"></a><span data-ttu-id="e66b8-212">查詢 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="e66b8-212">Querying XML Schemas</span></span>  
 <span data-ttu-id="e66b8-213">您可以用下列方法來查詢您已載入至 XML 結構描述集合的 XML 結構描述：</span><span class="sxs-lookup"><span data-stu-id="e66b8-213">You can query XML schemas that you have loaded into XML schema collections in the following ways:</span></span>  
  
-   <span data-ttu-id="e66b8-214">在 XML 結構描述命名空間的目錄檢視上撰寫 Transact-SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="e66b8-214">Write Transact-SQL queries on catalog views for XML schema namespaces.</span></span>  
  
-   <span data-ttu-id="e66b8-215">建立一個包含 `xml` 資料類型資料行的資料表來儲存您的 XML 結構描述，並將其載入至 XML 類型系統。</span><span class="sxs-lookup"><span data-stu-id="e66b8-215">Create a table that contains an `xml` data type column to store your XML schemas and also load them into the XML type system.</span></span> <span data-ttu-id="e66b8-216">您可以使用 `xml` 資料類型方法來查詢 XML 資料行。</span><span class="sxs-lookup"><span data-stu-id="e66b8-216">You can query the XML column by using the `xml` data type methods.</span></span> <span data-ttu-id="e66b8-217">您也可以在此資料行上建立 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="e66b8-217">Also, you can build an XML index on this column.</span></span> <span data-ttu-id="e66b8-218">然而，使用這個方法時，應用程式必須維護儲存在 XML 資料行中之 XML 結構描述與 XML 類型系統之間的一致性。</span><span class="sxs-lookup"><span data-stu-id="e66b8-218">However, with this approach, the application must maintain consistency between the XML schemas stored in the XML column and the XML type system.</span></span> <span data-ttu-id="e66b8-219">例如，若您從 XML 類型系統中卸除 XML 結構描述命名空間，就必須也將它從資料表中卸除，以維持一致性。</span><span class="sxs-lookup"><span data-stu-id="e66b8-219">For example, if you drop the XML schema namespace from the XML type system, you also have to drop it from the table in order to preserve consistency.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e66b8-220">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e66b8-220">See Also</span></span>  
 <span data-ttu-id="e66b8-221">[檢視儲存的 XML 結構描述集合](../xml/view-a-stored-xml-schema-collection.md) </span><span class="sxs-lookup"><span data-stu-id="e66b8-221">[View a Stored XML Schema Collection](../xml/view-a-stored-xml-schema-collection.md) </span></span>  
 <span data-ttu-id="e66b8-222">[前置處理結構描述以合併包含的結構描述](../xml/preprocess-a-schema-to-merge-included-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="e66b8-222">[Preprocess a Schema to Merge Included Schemas](../xml/preprocess-a-schema-to-merge-included-schemas.md) </span></span>  
 [<span data-ttu-id="e66b8-223">伺服器上 XML 結構描述集合的需求與限制</span><span class="sxs-lookup"><span data-stu-id="e66b8-223">Requirements and Limitations for XML Schema Collections on the Server</span></span>](../xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
