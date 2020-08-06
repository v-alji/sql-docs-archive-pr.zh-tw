---
title: Updategram (SQLXML 4.0) 簡介 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- explicit schema mapping [SQLXML]
- updategrams [SQLXML], mapping schema specifying
- namespaces [SQLXML]
- updategrams [SQLXML], about updategrams
- attribute-centric mapping
- invalid characters [SQLXML]
- element-centric mapping [SQLXML]
- mapping schema [SQLXML], updategrams
- namespaces [SQLXML], updategrams
- executing updategrams [SQLXML]
- implicit schema mapping
ms.assetid: cfe24e82-a645-4f93-ab16-39c21f90cce6
author: rothja
ms.author: jroth
ms.openlocfilehash: eb2f29d7f5d86d28254dacb9c55cceb9b4c72d8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700858"
---
# <a name="introduction-to-updategrams-sqlxml-40"></a><span data-ttu-id="91287-102">Updategram 簡介 (SQLXML 4.0) </span><span class="sxs-lookup"><span data-stu-id="91287-102">Introduction to Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="91287-103">您可以 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用 UPDATEGRAM 或 OPENXML 函數，從現有的 XML 檔修改中的資料庫)  (插入、更新或刪除 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="91287-103">You can modify (insert, update, or delete) a database in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from an existing XML document by using an updategram or the OPENXML [!INCLUDE[tsql](../../../includes/tsql-md.md)] function.</span></span>  
  
 <span data-ttu-id="91287-104">OPENXML 函數可透過切割現有的 XML 文件，並提供可以傳遞到 INSERT、UPDATE 或 DELETE 陳述式之資料列集來修改資料庫。</span><span class="sxs-lookup"><span data-stu-id="91287-104">The OPENXML function modifies a database by shredding the existing XML document and providing a rowset that can be passed to an INSERT, UPDATE, or DELETE statement.</span></span> <span data-ttu-id="91287-105">利用 OPENXML，可以針對資料庫資料表直接執行作業。</span><span class="sxs-lookup"><span data-stu-id="91287-105">With OPENXML, operations are performed directly against the database tables.</span></span> <span data-ttu-id="91287-106">因此，每當資料列集提供者 (例如資料表) 可以當做來源顯示時，OPENXML 最適合。</span><span class="sxs-lookup"><span data-stu-id="91287-106">Therefore, OPENXML is most appropriate wherever rowset providers, such as a table, can appear as a source.</span></span>  
  
 <span data-ttu-id="91287-107">Updategram 跟 OPENXML 一樣，可讓您在資料庫中插入、更新或刪除資料，不過，Updategram 會根據註解式 XSD (或 XDR) 結構描述提供的 XML 檢視運作，例如，更新會套用到對應結構描述提供的 XML 檢視。</span><span class="sxs-lookup"><span data-stu-id="91287-107">Like OPENXML, an updategram allows you to insert, update, or delete data in the database; however, an updategram works against the XML views provided by the annotated XSD (or an XDR) schema; for example, the updates are applied to the XML view provided by the mapping schema.</span></span> <span data-ttu-id="91287-108">對應結構描述會依序擁有將 XML 元素和屬性對應到對應的資料庫資料表和資料行的必要資訊。</span><span class="sxs-lookup"><span data-stu-id="91287-108">The mapping schema, in turn, has the necessary information to map XML elements and attributes to the corresponding database tables and columns.</span></span> <span data-ttu-id="91287-109">Updategram 會使用此對應資訊來更新資料庫資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="91287-109">The updategram uses this mapping information to update the database tables and columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91287-110">本文件集假設您非常熟悉 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的範本和對應結構描述支援。</span><span class="sxs-lookup"><span data-stu-id="91287-110">This documentation assumes that you are familiar with templates and mapping schema support in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="91287-111">如需詳細資訊，請參閱[批註式 XSD 架構簡介 &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="91287-111">For more information, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="91287-112">如需使用 XDR 的繼承應用程式，請參閱[SQLXML 4.0&#41;中 &#40;已被取代的批註式 XDR 架構](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="91287-112">For legacy applications that use XDR, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
## <a name="required-namespaces-in-the-updategram"></a><span data-ttu-id="91287-113">Updategram 中的必要命名空間</span><span class="sxs-lookup"><span data-stu-id="91287-113">Required Namespaces in the Updategram</span></span>  
 <span data-ttu-id="91287-114">Updategram 中的關鍵字（例如 **\<sync>** 、 **\<before>** 和 **\<after>** ）存在於 `urn:schemas-microsoft-com:xml-updategram` 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="91287-114">The keywords in an updategram, such as **\<sync>**, **\<before>**, and **\<after>**, exist in the `urn:schemas-microsoft-com:xml-updategram` namespace.</span></span> <span data-ttu-id="91287-115">您使用的命名空間前置詞是任意的。</span><span class="sxs-lookup"><span data-stu-id="91287-115">The namespace prefix that you use is arbitrary.</span></span> <span data-ttu-id="91287-116">在此文件集中，`updg` 前置詞代表 `updategram` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="91287-116">In this documentation, the `updg` prefix denotes the `updategram` namespace.</span></span>  
  
## <a name="reviewing-syntax"></a><span data-ttu-id="91287-117">檢閱語法</span><span class="sxs-lookup"><span data-stu-id="91287-117">Reviewing Syntax</span></span>  
 <span data-ttu-id="91287-118">Updategram 是具有 **\<sync>** 、 **\<before>** 和區塊的範本， **\<after>** 可形成 updategram 的語法。</span><span class="sxs-lookup"><span data-stu-id="91287-118">An updategram is a template with **\<sync>**, **\<before>**, and **\<after>** blocks that form the syntax of the updategram.</span></span> <span data-ttu-id="91287-119">下列程式碼以其簡單的形式顯示此語法：</span><span class="sxs-lookup"><span data-stu-id="91287-119">The following code shows this syntax in its simplest form:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema= "AnnotatedSchemaFile.xml"] >  
    <updg:before>  
        ...  
    </updg:before>  
    <updg:after>  
        ...  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="91287-120">下列定義描述每個區塊的角色：</span><span class="sxs-lookup"><span data-stu-id="91287-120">The following definitions describe the role of each of these blocks:</span></span>  
  
 **\<before>**  
 <span data-ttu-id="91287-121">識別記錄執行個體的目前狀態 (也稱為「之前的狀態」)。</span><span class="sxs-lookup"><span data-stu-id="91287-121">Identifies the existing state (also called "the before state") of the record instance.</span></span>  
  
 **\<after>**  
 <span data-ttu-id="91287-122">識別所要變更資料的新狀態。</span><span class="sxs-lookup"><span data-stu-id="91287-122">Identifies the new state to which data is to be changed.</span></span>  
  
 **\<sync>**  
 <span data-ttu-id="91287-123">包含 **\<before>** 和 **\<after>** 區塊。</span><span class="sxs-lookup"><span data-stu-id="91287-123">Contains the **\<before>** and **\<after>** blocks.</span></span> <span data-ttu-id="91287-124">**\<sync>** 區塊可以包含一組以上的 **\<before>** 和 **\<after>** 區塊。</span><span class="sxs-lookup"><span data-stu-id="91287-124">A **\<sync>** block can contain more than one set of **\<before>** and **\<after>** blocks.</span></span> <span data-ttu-id="91287-125">如果有一組以上的 **\<before>** 和 **\<after>** 區塊，即使它們是空的，這些區塊也會 () 必須指定為配對。</span><span class="sxs-lookup"><span data-stu-id="91287-125">If there is more than one set of **\<before>** and **\<after>** blocks, these blocks (even if they are empty) must be specified as pairs.</span></span> <span data-ttu-id="91287-126">此外，updategram 可以有一個以上的 **\<sync>** 區塊。</span><span class="sxs-lookup"><span data-stu-id="91287-126">Furthermore, an updategram can have more than one **\<sync>** block.</span></span> <span data-ttu-id="91287-127">每個 **\<sync>** 區塊都是交易的一個單位 (這表示區塊中的所有專案 **\<sync>** 都已完成，或未完成任何動作) 。</span><span class="sxs-lookup"><span data-stu-id="91287-127">Each **\<sync>** block is one unit of transaction (which means that either everything in the **\<sync>** block is done or nothing is done).</span></span> <span data-ttu-id="91287-128">如果您 **\<sync>** 在 updategram 中指定多個區塊，則一個區塊的失敗不 **\<sync>** 會影響其他 **\<sync>** 區塊。</span><span class="sxs-lookup"><span data-stu-id="91287-128">If you specify multiple **\<sync>** blocks in an updategram, the failure of one **\<sync>** block does not affect the other **\<sync>** blocks.</span></span>  
  
 <span data-ttu-id="91287-129">Updategram 是否刪除、插入或更新記錄實例，取決於 **\<before>** 和區塊的內容 **\<after>** ：</span><span class="sxs-lookup"><span data-stu-id="91287-129">Whether an updategram deletes, inserts, or updates a record instance depends on the contents of the **\<before>** and **\<after>** blocks:</span></span>  
  
-   <span data-ttu-id="91287-130">如果記錄實例只顯示在區塊中 **\<before>** 沒有對應實例的區塊中 **\<after>** ，則 updategram 會執行刪除作業。</span><span class="sxs-lookup"><span data-stu-id="91287-130">If a record instance appears only in the **\<before>** block with no corresponding instance in the **\<after>** block, the updategram performs a delete operation.</span></span>  
  
-   <span data-ttu-id="91287-131">如果記錄實例只顯示在區塊中 **\<after>** 沒有對應實例的區塊中 **\<before>** ，則為插入作業。</span><span class="sxs-lookup"><span data-stu-id="91287-131">If a record instance appears only in the **\<after>** block with no corresponding instance in the **\<before>** block, it is an insert operation.</span></span>  
  
-   <span data-ttu-id="91287-132">如果記錄實例出現在區塊中， **\<before>** 而且在區塊中有對應的實例 **\<after>** ，則它是更新作業。</span><span class="sxs-lookup"><span data-stu-id="91287-132">If a record instance appears in the **\<before>** block and has a corresponding instance in the **\<after>** block, it is an update operation.</span></span> <span data-ttu-id="91287-133">在此情況下，updategram 會將記錄實例更新為區塊中指定的值 **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="91287-133">In this case, the updategram updates the record instance to the values that are specified in the **\<after>** block.</span></span>  
  
## <a name="specifying-a-mapping-schema-in-the-updategram"></a><span data-ttu-id="91287-134">指定 Updategram 中的對應結構描述</span><span class="sxs-lookup"><span data-stu-id="91287-134">Specifying a Mapping Schema in the Updategram</span></span>  
 <span data-ttu-id="91287-135">在 Updategram 中，對應結構描述 (同時支援 XSD 和 XDR 結構描述) 提供的 XML 摘要可以是隱含的或明確的 (也就是說，Updategram 可以選擇是否搭配指定的對應結構描述使用)。</span><span class="sxs-lookup"><span data-stu-id="91287-135">In an updategram, the XML abstraction that is provided by a mapping schema (both XSD and XDR schemas are supported) can be implicit or explicit (that is, an updategram can work with or without a specified mapping schema).</span></span> <span data-ttu-id="91287-136">如果您未指定對應架構，則 updategram 會假設 (預設對應) 的隱含對應，其中區塊或區塊中的每個專案都會 **\<before>** **\<after>** 對應到資料表，而每個元素的子專案或屬性會對應至資料庫中的資料行。</span><span class="sxs-lookup"><span data-stu-id="91287-136">If you do not specify a mapping schema, the updategram assumes an implicit mapping (the default mapping), where each element in the **\<before>** block or **\<after>** block maps to a table and each element's child element or attribute maps to a column in the database.</span></span> <span data-ttu-id="91287-137">如果您明確地指定對應結構描述，Updategram 中的元素和屬性必須符合對應結構描述中的元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="91287-137">If you explicitly specify a mapping schema, the elements and attributes in the updategram must match the elements and attributes in the mapping schema.</span></span>  
  
### <a name="implicit-default-mapping"></a><span data-ttu-id="91287-138">隱含的 (預設) 對應</span><span class="sxs-lookup"><span data-stu-id="91287-138">Implicit (default) Mapping</span></span>  
 <span data-ttu-id="91287-139">在多數情況下，執行簡單更新的 Updategram 可能不需要對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="91287-139">In most cases, an updategram that performs simple updates might not require a mapping schema.</span></span> <span data-ttu-id="91287-140">在此情況下，Updategram 會依賴預設對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="91287-140">In this case, the updategram relies on the default mapping schema.</span></span>  
  
 <span data-ttu-id="91287-141">下列 Updategram 示範隱含的對應。</span><span class="sxs-lookup"><span data-stu-id="91287-141">The following updategram demonstrates implicit mapping.</span></span> <span data-ttu-id="91287-142">在這個範例中，Updategram 會在 Sales.Customer 資料表中插入新客戶。</span><span class="sxs-lookup"><span data-stu-id="91287-142">In this example, the updategram inserts a new customer in the Sales.Customer table.</span></span> <span data-ttu-id="91287-143">由於此 updategram 使用隱含對應，因此專案會 \<Sales.Customer> 對應至 customer 資料表，而 CustomerID 和 SalesPersonID 屬性會對應至 sales. customer 資料表中的對應資料行。</span><span class="sxs-lookup"><span data-stu-id="91287-143">Because this updategram uses implicit mapping, the \<Sales.Customer> element maps to the Sales.Customer table, and the CustomerID and SalesPersonID attributes map to the corresponding columns in the Sales.Customer table.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
</updg:before>  
<updg:after>  
    <Sales.Customer CustomerID="1" SalesPersonID="277" />  
    </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="explicit-mapping"></a><span data-ttu-id="91287-144">明確的對應</span><span class="sxs-lookup"><span data-stu-id="91287-144">Explicit Mapping</span></span>  
 <span data-ttu-id="91287-145">如果您指定對應結構描述 (XSD 或 XDR)，Updategram 會使用結構描述來判斷要更新的資料庫資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="91287-145">If you specify a mapping schema (either XSD or XDR), the updategram uses the schema to determine the database tables and columns that are to be updated.</span></span>  
  
 <span data-ttu-id="91287-146">如果 Updategram 執行複雜的更新 (例如，根據在對應結構描述中指定的父子式關聯性，將記錄插入多個資料表)，您必須使用 Updategram 執行所依據的 `mapping-schema` 屬性，明確地提供對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="91287-146">If the updategram performs a complex update (for example, inserting records in multiple tables on the basis of the parent-child relationship that is specified in the mapping schema), you must explicitly provide the mapping schema by using the `mapping-schema` attribute against which the updategram executes.</span></span>  
  
 <span data-ttu-id="91287-147">由於 Updategram 是一個範本，因此，在 Updategram 中針對對應結構描述所指定的路徑是範本檔位置的相對路徑 (相對於儲存 Updategram 的位置)。</span><span class="sxs-lookup"><span data-stu-id="91287-147">Because an updategram is a template, the path specified for the mapping schema in the updategram is relative to the location of the template file (relative to where the updategram is stored).</span></span> <span data-ttu-id="91287-148">如需詳細資訊，請參閱[在 Updategram 中指定批註式對應架構 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="91287-148">For more information, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
## <a name="element-centric-and-attribute-centric-mapping-in-updategrams"></a><span data-ttu-id="91287-149">Updategram 中的元素中心及屬性中心對應</span><span class="sxs-lookup"><span data-stu-id="91287-149">Element-centric and Attribute-centric Mapping in Updategrams</span></span>  
 <span data-ttu-id="91287-150">利用預設對應 (在 Updategram 中未指定對應結構描述時)，Updategram 元素會對應到資料表，而子元素 (如果是元素中心對應) 和屬性 (如果是屬性中心對應) 則會對應到資料行。</span><span class="sxs-lookup"><span data-stu-id="91287-150">With default mapping (when the mapping schema is not specified in the updategram), the updategram elements map to tables and the  child elements (in the case of element-centric mapping) and the attributes (in the case of attribute-centric mapping) map to columns.</span></span>  
  
### <a name="element-centric-mapping"></a><span data-ttu-id="91287-151">元素中心的對應</span><span class="sxs-lookup"><span data-stu-id="91287-151">Element-centric Mapping</span></span>  
 <span data-ttu-id="91287-152">在元素中心的 Updategram 中，一個元素包含表示元素屬性的多個子元素。</span><span class="sxs-lookup"><span data-stu-id="91287-152">In an element-centric updategram, an element contains child elements that denote the properties of the element.</span></span> <span data-ttu-id="91287-153">例如，請參閱下列 Updategram。</span><span class="sxs-lookup"><span data-stu-id="91287-153">As an example, refer to the following updategram.</span></span> <span data-ttu-id="91287-154">**\<Person.Contact>** 元素包含 **\<FirstName>** 和 **\<LastName>** 子項目。</span><span class="sxs-lookup"><span data-stu-id="91287-154">The **\<Person.Contact>** element contains the **\<FirstName>** and **\<LastName>** child elements.</span></span> <span data-ttu-id="91287-155">這些子項目是元素的屬性 **\<Person.Contact>** 。</span><span class="sxs-lookup"><span data-stu-id="91287-155">These child elements are properties of the **\<Person.Contact>** element.</span></span>  
  
 <span data-ttu-id="91287-156">由於此 updategram 不會指定對應架構，因此 updategram 會使用隱含對應，其中 **\<Person.Contact>** 元素會對應到 Person. Contact 資料表，而其子項目則對應至 FirstName 和 LastName 資料行。</span><span class="sxs-lookup"><span data-stu-id="91287-156">Because this updategram does not specify a mapping schema, the updategram uses implicit mapping, where the **\<Person.Contact>** element maps to the Person.Contact table and its child elements map to the FirstName and LastName columns.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:after>  
    <Person.Contact>  
       <FirstName>Catherine</FirstName>  
       <LastName>Abel</LastName>  
    </Person.Contact>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="attribute-centric-mapping"></a><span data-ttu-id="91287-157">以屬性為主的對應</span><span class="sxs-lookup"><span data-stu-id="91287-157">Attribute-centric Mapping</span></span>  
 <span data-ttu-id="91287-158">在屬性中心的對應中，元素擁有屬性。</span><span class="sxs-lookup"><span data-stu-id="91287-158">In an attribute-centric mapping, the elements have attributes.</span></span> <span data-ttu-id="91287-159">下列 Updategram 使用屬性中心的對應。</span><span class="sxs-lookup"><span data-stu-id="91287-159">The following updategram uses attribute-centric mapping.</span></span> <span data-ttu-id="91287-160">在此範例中， **\<Person.Contact>** 元素是由**FirstName**和**LastName**屬性所組成。</span><span class="sxs-lookup"><span data-stu-id="91287-160">In this example, the **\<Person.Contact>** element consists of the **FirstName** and **LastName** attributes.</span></span> <span data-ttu-id="91287-161">這些屬性是元素的屬性 **\<Person.Contact>** 。</span><span class="sxs-lookup"><span data-stu-id="91287-161">These attributes are the properties of the **\<Person.Contact>** element.</span></span> <span data-ttu-id="91287-162">如先前範例所示，此 updategram 不會指定對應架構，因此它會依賴隱含對應，將 **\<Person.Contact>** 元素對應至 Person 資料表，並將元素的屬性對應到資料表中的個別資料行。</span><span class="sxs-lookup"><span data-stu-id="91287-162">As in the previous example, this updategram specifies no mapping schema, so it relies on implicit mapping to map the **\<Person.Contact>** element to the Person.Contact table and the element's attributes to the respective columns in the table.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
    <Person.Contact FirstName="Catherine" LastName="Abel" />  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="using-both-element-centric-and-attribute-centric-mapping"></a><span data-ttu-id="91287-163">同時使用元素中心和屬性中心的對應</span><span class="sxs-lookup"><span data-stu-id="91287-163">Using Both Element-centric and Attribute-centric Mapping</span></span>  
 <span data-ttu-id="91287-164">您可以指定混用的元素中心與屬性中心對應，如下列 Updategram 所示。</span><span class="sxs-lookup"><span data-stu-id="91287-164">You can specify a mix of element-centric and attribute-centric mapping, as shown in the following updategram.</span></span> <span data-ttu-id="91287-165">請注意， **\<Person.Contact>** 元素同時包含屬性和子項目。</span><span class="sxs-lookup"><span data-stu-id="91287-165">Notice that the **\<Person.Contact>** element contains both an attribute and a child element.</span></span> <span data-ttu-id="91287-166">同時，這個 Updategram 依賴隱含的對應。</span><span class="sxs-lookup"><span data-stu-id="91287-166">Also, this updategram relies on implicit mapping.</span></span> <span data-ttu-id="91287-167">因此， **FirstName**屬性和 **\<LastName>** 子項目會對應至 Person 資料表中的對應資料行。</span><span class="sxs-lookup"><span data-stu-id="91287-167">Thus, the **FirstName** attribute and the **\<LastName>** child element map to corresponding columns in the Person.Contact table.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
    <Person.Contact FirstName="Catherine" >  
       <LastName>Abel</LastName>  
    </Person.Contact>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="working-with-characters-valid-in-sql-server-but-not-valid-in-xml"></a><span data-ttu-id="91287-168">使用在 SQL Server 有效，但在 XML 無效的字元</span><span class="sxs-lookup"><span data-stu-id="91287-168">Working with Characters Valid in SQL Server but Not Valid in XML</span></span>  
 <span data-ttu-id="91287-169">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，資料表名稱可以包含一個空格。</span><span class="sxs-lookup"><span data-stu-id="91287-169">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], table names can include a space.</span></span> <span data-ttu-id="91287-170">不過，此種類型的資料表名稱在 XML 中無效。</span><span class="sxs-lookup"><span data-stu-id="91287-170">However, this type of table name is not valid in XML.</span></span>  
  
 <span data-ttu-id="91287-171">若要編碼的字元是有效的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 識別碼，但不是有效的 XML 識別碼，請使用 ' __xHHHH \_ \_ ' 作為編碼值，其中 hhhh hhhh 會以最高有效位優先的順序，代表該字元的四位數十六進位 UCS-2 代碼。</span><span class="sxs-lookup"><span data-stu-id="91287-171">To encode characters that are valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identifiers but are not valid XML identifiers, use '__xHHHH\_\_' as the encoding value, where HHHH stands for the four-digit hexadecimal UCS-2 code for the character in the most significant bit-first order.</span></span> <span data-ttu-id="91287-172">使用此編碼配置時，空白字元會取代為 x0020 (四位數的十六進位碼，用於空白字元) ;因此，中的資料表名稱 [Order Details] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會變成 \_ XML _x005B_Order_x0020_Details_x005D。</span><span class="sxs-lookup"><span data-stu-id="91287-172">Using this encoding scheme, a space character gets replaced with x0020 (the four-digit hexadecimal code for a space character); thus, the table name [Order Details] in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] becomes _x005B_Order_x0020_Details_x005D\_ in XML.</span></span>  
  
 <span data-ttu-id="91287-173">同樣地，您可能需要指定三部分的元素名稱，例如 \<[database].[owner].[table]> 。</span><span class="sxs-lookup"><span data-stu-id="91287-173">Similarly, you might need to specify three-part element names, such as \<[database].[owner].[table]>.</span></span> <span data-ttu-id="91287-174">因為括弧字元 ( [和] ) 在 XML 中無效，所以您必須將此指定為 \<_x005B_database_x005D\_._x005B_owner_x005D\_._x005B_table_x005D\_> ，其中 _x005B \_ 是左括弧 ( 的編碼方式 [) ，而 _x005D \_ 是右方括弧 (] ) 的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="91287-174">Because the bracket characters ([ and ]) are not valid in XML, you must specify this as \<_x005B_database_x005D\_._x005B_owner_x005D\_._x005B_table_x005D\_>, where _x005B\_ is the encoding for the left bracket ([) and _x005D\_ is the encoding for the right bracket (]).</span></span>  
  
## <a name="executing-updategrams"></a><span data-ttu-id="91287-175">執行 Updategram</span><span class="sxs-lookup"><span data-stu-id="91287-175">Executing Updategrams</span></span>  
 <span data-ttu-id="91287-176">Updategram 是一個範本，因此，範本的所有處理機制都會套用到 Updategram。</span><span class="sxs-lookup"><span data-stu-id="91287-176">Because an updategram is a template, all the processing mechanisms of a template apply to the updategram.</span></span> <span data-ttu-id="91287-177">對於 SQLXML 4.0，您可以利用下列任一種方式執行 Updategram：</span><span class="sxs-lookup"><span data-stu-id="91287-177">For SQLXML 4.0, you can execute an updategram in either of the following ways:</span></span>  
  
-   <span data-ttu-id="91287-178">在 ADO 命令中提交它。</span><span class="sxs-lookup"><span data-stu-id="91287-178">By submitting it in an ADO command.</span></span>  
  
-   <span data-ttu-id="91287-179">當做 OLE DB 命令提交它。</span><span class="sxs-lookup"><span data-stu-id="91287-179">By submitting it as an OLE DB command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91287-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91287-180">See Also</span></span>  
 [<span data-ttu-id="91287-181">&#40;SQLXML 4.0&#41;的 Updategram 安全性考慮</span><span class="sxs-lookup"><span data-stu-id="91287-181">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
