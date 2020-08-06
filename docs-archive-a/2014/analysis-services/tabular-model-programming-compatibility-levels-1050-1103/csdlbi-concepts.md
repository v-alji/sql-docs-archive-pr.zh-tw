---
title: CSDLBI 概念 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 2fbdf621-a94d-4a55-a088-3d56d65016ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 16c6597171eef10da67ad497e4303b3716298e6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594237"
---
# <a name="csdlbi-concepts"></a><span data-ttu-id="b18f0-102">CSDLBI 概念</span><span class="sxs-lookup"><span data-stu-id="b18f0-102">CSDLBI Concepts</span></span>
  <span data-ttu-id="b18f0-103">具有 BI 註解的概念結構定義語言 (CSDLBI) 是以實體資料架構為基礎，這是一種用於表示資料摘要，以便用程式設計方式存取、查詢或匯出不同的資料集。</span><span class="sxs-lookup"><span data-stu-id="b18f0-103">Conceptual Schema Definition Language with BI annotations (CSDLBI) is based on the Entity Data Framework, which is an abstraction for representing data in a way that enables disparate data sets to be programmatically accessed, queried, or exported.</span></span> <span data-ttu-id="b18f0-104">CSDLBI 可用來表示使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 建立的資料模型，因為它支援豐富的資料驅動報表和應用程式。</span><span class="sxs-lookup"><span data-stu-id="b18f0-104">CSDLBI is used to represent data models created using [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] because it supports rich, data-driven reporting and applications.</span></span>  
  
 <span data-ttu-id="b18f0-105">本節將說明 CSDLBI 表示法如何對應 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料模型 (包含表格式與多維度)，以及每個模型類型的範例。</span><span class="sxs-lookup"><span data-stu-id="b18f0-105">This section explains how the CSDLBI representation maps to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data models (both tabular and multidimensional), along with examples of each model type.</span></span>  
  
 <span data-ttu-id="b18f0-106">用來說明這些概念的範例都取自 AdventureWorks 範例資料庫 (可在 Codeplex 上取得)。</span><span class="sxs-lookup"><span data-stu-id="b18f0-106">Examples used to illustrate these concepts are taken from the AdventureWorks sample database, available on Codeplex.</span></span> <span data-ttu-id="b18f0-107">如需範例的詳細資訊，請參閱 SQL Server 的「[艾德作品」範例](https://go.microsoft.com/fwlink/?linkID=220093)。</span><span class="sxs-lookup"><span data-stu-id="b18f0-107">For more information about the samples, see [Adventure Works Samples for SQL Server](https://go.microsoft.com/fwlink/?linkID=220093).</span></span>  
  
## <a name="structure-of-a-tabular-model-in-csdlbi"></a><span data-ttu-id="b18f0-108">CSDLBI 中表格式模型的結構</span><span class="sxs-lookup"><span data-stu-id="b18f0-108">Structure of a Tabular Model in CSDLBI</span></span>  
 <span data-ttu-id="b18f0-109">描述報表模型及其資料的 CSDLBI 文件會以 xsd 陳述式為開頭，後面接著模型的定義。</span><span class="sxs-lookup"><span data-stu-id="b18f0-109">A CSDLBI document that describes a report model and its data begins with the xsd statement, followed by the definition of a model.</span></span>  
  
 <span data-ttu-id="b18f0-110">模型是一種命名空間，其中包含下列主要實體、關聯和屬性：</span><span class="sxs-lookup"><span data-stu-id="b18f0-110">The model is a namespace, which contains the following major entities, associations, and properties:</span></span>  
  
-   <span data-ttu-id="b18f0-111">`EntityContainer` 會列出模型中的資料表。</span><span class="sxs-lookup"><span data-stu-id="b18f0-111">The `EntityContainer` lists the tables in the model.</span></span>  
  
-   <span data-ttu-id="b18f0-112">每個列出的資料表都會將 `EntityContainer` 設為 `EntitySet`。</span><span class="sxs-lookup"><span data-stu-id="b18f0-112">Each table is listed with the `EntityContainer` as an `EntitySet`.</span></span>  
  
-   <span data-ttu-id="b18f0-113">兩個資料表之間的每個關聯性都會描述成 `AssociationSet`，其中定義關聯性端點和關聯性角色。</span><span class="sxs-lookup"><span data-stu-id="b18f0-113">Each relationship between two tables is described as an `AssociationSet` that defines the relationship end points and the relationship roles.</span></span>  
  
-   <span data-ttu-id="b18f0-114">`EntityType` 元素會針對 BISM 擴充，以便提供有關資料表以及內含資料行的其他詳細資料，包括用於排序和顯示用途的屬性。</span><span class="sxs-lookup"><span data-stu-id="b18f0-114">The `EntityType` element is extended for BISM to provide additional detail about the tables and the columns in them, including properties for sorting and display purposes.</span></span>  
  
-   <span data-ttu-id="b18f0-115">`Measure` 元素會定義可用於模型的計算。</span><span class="sxs-lookup"><span data-stu-id="b18f0-115">The `Measure` element defines calculations that can be used in the model.</span></span> <span data-ttu-id="b18f0-116">您可以使用新的 `KPI` 元素來加入一組特殊顯示屬性，藉以將量值轉換成 KPI。</span><span class="sxs-lookup"><span data-stu-id="b18f0-116">A measure can be turned into a KPI by adding a set of special display attributes, using the new `KPI` Element.</span></span>  
  
-   <span data-ttu-id="b18f0-117">檢視方塊沒有個別表示法。</span><span class="sxs-lookup"><span data-stu-id="b18f0-117">There is no separate representation of perspectives.</span></span> <span data-ttu-id="b18f0-118">不包含在檢視方塊中的資料行和資料表會以 CSDL 呈現，但是使用 `Hidden` 屬性來標幟。</span><span class="sxs-lookup"><span data-stu-id="b18f0-118">Columns and tables that are not included in a perspective are present in the CSDL but flagged with the `Hidden` attribute.</span></span>  
  
### <a name="entities-entitysets-and-entitytypes"></a><span data-ttu-id="b18f0-119">實體、EntitySet 和 EntityType</span><span class="sxs-lookup"><span data-stu-id="b18f0-119">Entities, EntitySets, and EntityTypes</span></span>  
 <span data-ttu-id="b18f0-120">實體資料架構中實體的概念已擴充，可表示資料模型中的資料行和資料表。</span><span class="sxs-lookup"><span data-stu-id="b18f0-120">The notion of an entity in the Entity Data Framework is extended to represent columns and tables from the data model.</span></span> <span data-ttu-id="b18f0-121">下列摘錄顯示僅包含三個資料表之簡單模型中的 `EntitySet` 元素清單。</span><span class="sxs-lookup"><span data-stu-id="b18f0-121">The following excerpt shows the list of `EntitySet` elements in a simple model containing only three tables.</span></span>  
  
```  
<EntityContainer Name="SimpleModel">  
<EntitySet Name="DimCustomer"EntityType="SimpleModel.DimCustomer">  
     <bi:EntitySet />  
   </EntitySet>  
<EntitySet Name="DimDate" EntityType="SimpleModel.DimDate">  
     <bi:EntitySet />  
   </EntitySet>  
<EntitySet Name="DimGeography" EntityType="SimpleModel.DimGeography">  
     <bi:EntitySet />  
   </EntitySet> />  
  
```  
  
 <span data-ttu-id="b18f0-122">`EntitySet` 不包含資料表中資料行或資料的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b18f0-122">The `EntitySet` does not contain information about columns or data in the table.</span></span> <span data-ttu-id="b18f0-123">資料行及其屬性的詳細描述是在 EntityType 元素中提供。</span><span class="sxs-lookup"><span data-stu-id="b18f0-123">The detailed description of the columns and their properties is provided in the EntityType element.</span></span>  
  
 <span data-ttu-id="b18f0-124">每個實體 (資料表) 的 `EntitySet` 元素都包含一些屬性的集合，這些屬性會定義索引鍵資料行、資料行的資料類型和長度、Null 屬性、排序行為等等。</span><span class="sxs-lookup"><span data-stu-id="b18f0-124">The `EntitySet` element for each entity (table) includes a collection of properties that define the key column, the data type and length of the column, nullability, sorting behavior, and so forth.</span></span> <span data-ttu-id="b18f0-125">例如，下列 CSDL 摘錄描述的是 Customer 資料表中的三個資料行。</span><span class="sxs-lookup"><span data-stu-id="b18f0-125">For example, the following CSDL excerpt describes three columns in the Customer table.</span></span> <span data-ttu-id="b18f0-126">第一個資料行是模型在內部使用的特殊隱藏資料行。</span><span class="sxs-lookup"><span data-stu-id="b18f0-126">The first column is a special hidden column used internally by the model.</span></span>  
  
```  
<EntityType Name="Customer">  
  <Key>  
     <PropertyRef Name="RowNumber" />  
  </Key>  
    <Property Name="RowNumber" Type="Int64" Nullable="false">  
     <bi:Property Hidden="true" Contents="RowNumber"  
       Stability="RowNumber" />  
    </Property>  
    <Property Name="CustomerKey" Type="Int64" Nullable="false">  
      <bi:Property />  
    </Property>  
     <Property Name="FirstName" Type="String" MaxLength="Max" FixedLength="false">  
       <bi:Property />  
      </Property>  
  
```  
  
 <span data-ttu-id="b18f0-127">為了限制產生的 CSDLBI 文件大小，在實體中出現一次以上的屬性會由現有屬性的參考指定，因此只需要針對 `EntityType` 列出該屬性一次即可。</span><span class="sxs-lookup"><span data-stu-id="b18f0-127">To limit the size of the CSDLBI document that is generated, properties that appear more than once in an entity are specified by a reference to an existing property, so that the property need be listed only once for the `EntityType`.</span></span> <span data-ttu-id="b18f0-128">用戶端應用程式可以尋找符合 `EntityType` 的 `OriginEntityType`，藉以取得屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b18f0-128">The client application can get the value of the property by finding the `EntityType` that matches the `OriginEntityType`.</span></span>  
  
### <a name="relationships"></a><span data-ttu-id="b18f0-129">關聯性</span><span class="sxs-lookup"><span data-stu-id="b18f0-129">Relationships</span></span>  
 <span data-ttu-id="b18f0-130">在 Entity Data Framework 中，關係會定義為實體之間的*關聯*。</span><span class="sxs-lookup"><span data-stu-id="b18f0-130">In the Entity Data Framework, relationships are defined as *associations* between entities.</span></span>  
  
 <span data-ttu-id="b18f0-131">關聯永遠只有兩端，每一端都指向資料表中的欄位或資料行。</span><span class="sxs-lookup"><span data-stu-id="b18f0-131">Associations always have exactly two ends, each pointing to a field or column in a table.</span></span> <span data-ttu-id="b18f0-132">因此，如果關聯性具有不同的端點，兩個資料表之間就可能會存在多個關聯性。</span><span class="sxs-lookup"><span data-stu-id="b18f0-132">Therefore, multiple relationships are possible between two tables, if the relationships have different end points.</span></span> <span data-ttu-id="b18f0-133">角色名稱會指派給關聯的端點，表示關聯如何用於資料模型的內容。</span><span class="sxs-lookup"><span data-stu-id="b18f0-133">A role name is assigned to the end points of the association, and indicates how the association is used in the context of the data model.</span></span> <span data-ttu-id="b18f0-134">角色名稱的範例可能是**ShipTo**，適用于與 Orders 資料表中的客戶識別碼相關的客戶識別碼。</span><span class="sxs-lookup"><span data-stu-id="b18f0-134">An example of a role name might be **ShipTo**, when applied to a customer ID that is related to the customer ID in an Orders table.</span></span>  
  
 <span data-ttu-id="b18f0-135">模型的 CSDLBI 標記法也會包含關聯上的屬性，以決定如何在關聯的*多重性*方面對應實體。</span><span class="sxs-lookup"><span data-stu-id="b18f0-135">The CSDLBI representation of the model also contains attributes on the association that determine how the entities are mapped to each other in terms of the *multiplicity* of the association.</span></span> <span data-ttu-id="b18f0-136">多重性會指出位於資料表之間關聯性端點的屬性或資料行是位於關聯性的一端，還是多端。</span><span class="sxs-lookup"><span data-stu-id="b18f0-136">Multiplicity indicates whether the attribute or column at the end point of a relationship between tables is on the one side of a relationship, or on the many side.</span></span> <span data-ttu-id="b18f0-137">一對一關聯性沒有個別的值。</span><span class="sxs-lookup"><span data-stu-id="b18f0-137">There is no separate value for one-to-one relationships.</span></span> <span data-ttu-id="b18f0-138">CSDLBI 註解支援多重性 0 (表示實體並未與任何項目產生關聯) 或 0..1 (表示一對一關聯性或一對多關聯性)。</span><span class="sxs-lookup"><span data-stu-id="b18f0-138">CSDLBI annotations support multiplicity of 0 (meaning the entity is not associated with anything) or 0..1, which means either a one-one relationship or a one-to-many relationship.</span></span>  
  
 <span data-ttu-id="b18f0-139">下列範例表示 Date 與 ProductInventory 資料表之間關聯性的 CSDLBI 輸出，其中這兩個資料表都在 DateAlternateKey 資料行上聯結。</span><span class="sxs-lookup"><span data-stu-id="b18f0-139">The following sample represents the CSDLBI output for a relationship between the tables, Date and ProductInventory, where the two tables are joined on the column DateAlternateKey.</span></span> <span data-ttu-id="b18f0-140">請注意，根據預設，`AssociationSet` 的名稱是關聯性中相關資料行的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="b18f0-140">Notice that, by default, the name of the `AssociationSet` is the fully qualified name of the columns that are involved in the relationship.</span></span> <span data-ttu-id="b18f0-141">不過，當您設計模型時，可以將此行為變更成使用不同的命名格式。</span><span class="sxs-lookup"><span data-stu-id="b18f0-141">However, you can change this behavior when you design the model, to use a different naming format.</span></span>  
  
```  
<AssociationSet Name="ProductInventory_Date_DateKey" Association="Model.ProductInventory_Date_DateKey">  
              <End EntitySet="ProductInventory" />  
              <End EntitySet="Date" />  
              <bi:AssociationSet />  
            </AssociationSet>  
  
```  
  
### <a name="visualization-and-navigation-properties"></a><span data-ttu-id="b18f0-142">視覺效果和導覽屬性</span><span class="sxs-lookup"><span data-stu-id="b18f0-142">Visualization and Navigation Properties</span></span>  
 <span data-ttu-id="b18f0-143">CSDLBI 註解最重要的部分就是在報表層中定義呈現方式的屬性，以及在實體之間導覽關聯性的屬性。</span><span class="sxs-lookup"><span data-stu-id="b18f0-143">An important part of the CSDLBI annotations are the properties for defining presentation in the reporting layer, and for navigating the relationships among entities.</span></span> <span data-ttu-id="b18f0-144">一般而言，當您建立資料模型時，如果用戶端應用程式會指定呈現方式的排序和其他詳細資料，您就會認為控制資料的排序或分組方式或是控制可能的預設值不重要。</span><span class="sxs-lookup"><span data-stu-id="b18f0-144">Typically, when you are creating a data model, you do not consider it important to control how the data is ordered or grouped, or what the default value might be, on the assumption that the client application will specify ordering and other details of presentation.</span></span> <span data-ttu-id="b18f0-145">不過，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 表格式模型是針對與 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 報表用戶端整合所設計，而且包含支援在報表設計介面中呈現資料模型內之實體的屬性 (Property) 與屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="b18f0-145">However, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tabular models are designed for integration with the [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reporting client, and includes properties and attributes that support presentation of entities from the data model in the report design surface.</span></span>  
  
 <span data-ttu-id="b18f0-146">視覺效果的延伸模組包含了一些屬性，可用於指定要搭配數值資料使用的預設彙總、指出文字欄位會指向影像的 URL，或是指定用來排序目前欄位的欄位。</span><span class="sxs-lookup"><span data-stu-id="b18f0-146">Extensions for visualization include attributes for specifying the default aggregation to use with numerical data, for indicating that a text field points to a URL of an image, or specifying the field used to sort the current field.</span></span>  
  
### <a name="name-properties-and-naming-conventions"></a><span data-ttu-id="b18f0-147">名稱屬性和命名慣例</span><span class="sxs-lookup"><span data-stu-id="b18f0-147">Name Properties and Naming Conventions</span></span>  
 <span data-ttu-id="b18f0-148">CSDLBI 結構描述規定每個實體都必須具有唯一名稱以及可當做索引鍵使用的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b18f0-148">The CSDLBI schema provides that each entity has a unique name and an identifier that can be used as a key.</span></span> <span data-ttu-id="b18f0-149">此外，某些實體可以具有用於顯示用途的標題，以及根據實體使用位置而變更的內容名稱。</span><span class="sxs-lookup"><span data-stu-id="b18f0-149">In addition, some entities can have captions used for display purposes, and contextual names that change depending on where the entity is used.</span></span>  
  
 <span data-ttu-id="b18f0-150">`Documentation` 元素讓報表設計師有機會提供實體的描述，以便協助商務使用者了解資料的意義。</span><span class="sxs-lookup"><span data-stu-id="b18f0-150">The `Documentation` element provides the opportunity for report designers to furnish a description of the entity, to help business users understand the meaning of the data.</span></span> <span data-ttu-id="b18f0-151">某些實體也允許使用一個或多個 `Annotation` 屬性，這些屬性會提供額外的中繼資料，以供應用程式或用戶端取用。</span><span class="sxs-lookup"><span data-stu-id="b18f0-151">Some entities also allow one or more `Annotation` attributes, which provide extra metadata for consumption by the application or by clients.</span></span>  
  
 <span data-ttu-id="b18f0-152">當您在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 工具中產生模型時，針對物件所建立的名稱就會遵循 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的物件命名和名稱唯一性慣例。</span><span class="sxs-lookup"><span data-stu-id="b18f0-152">When you generate a model the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tools, the names that are created for objects follow the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] conventions for object naming and name uniqueness.</span></span> <span data-ttu-id="b18f0-153">不過，因為 CSDLBI 是以實體資料架構 (EDF) 為基礎 (要求名稱遵守 C# 識別碼的慣例)，所以當伺服器建立模型的 CSDLBI 輸出時，伺服器會接受用於 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 結構描述內部的名稱，並且自動建立符合 EDF 需求的新物件名稱。</span><span class="sxs-lookup"><span data-stu-id="b18f0-153">However, because CSDLBI is based on the Entity Data Framework (EDF), which requires that names adhere to conventions for C# identifiers, when the server creates the CSDLBI output for a model, the server takes the names used within the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] schema and automatically creates new object names that comply with EDF requirements.</span></span> <span data-ttu-id="b18f0-154">下表描述的是用以產生新名稱的作業。</span><span class="sxs-lookup"><span data-stu-id="b18f0-154">The following table describes the operations by which the new names are generated.</span></span>  
  
|<span data-ttu-id="b18f0-155">規則</span><span class="sxs-lookup"><span data-stu-id="b18f0-155">Rule</span></span>|<span data-ttu-id="b18f0-156">動作</span><span class="sxs-lookup"><span data-stu-id="b18f0-156">Action</span></span>|  
|----------|------------|  
|<span data-ttu-id="b18f0-157">沒有禁止的字元</span><span class="sxs-lookup"><span data-stu-id="b18f0-157">No forbidden characters</span></span>|<span data-ttu-id="b18f0-158">由底線取代禁止的字元。</span><span class="sxs-lookup"><span data-stu-id="b18f0-158">Forbidden characters are replaced by underscore.</span></span>|  
|<span data-ttu-id="b18f0-159">名稱必須是唯一的</span><span class="sxs-lookup"><span data-stu-id="b18f0-159">Names must be unique</span></span>|<span data-ttu-id="b18f0-160">如果兩個字串完全相同，就會附加底線及數字，讓其中一個字串成為唯一的字串</span><span class="sxs-lookup"><span data-stu-id="b18f0-160">If two strings are the same, one is made unique by appending underscore plus a number</span></span>|  
  
> [!WARNING]  
>  <span data-ttu-id="b18f0-161">標題和限定詞都具有翻譯，而且對於給定的語言而言，可能會存在其中一個。</span><span class="sxs-lookup"><span data-stu-id="b18f0-161">Captions and qualifiers both have translations, and for a given language, one or the other might be present.</span></span> <span data-ttu-id="b18f0-162">這表示，如果限定詞與名稱或限定詞與標題已串連，則字串可能使用兩種不同的語言。</span><span class="sxs-lookup"><span data-stu-id="b18f0-162">This means that in cases where a qualifier and name or qualifier and caption are concatenated, the strings could be in two different languages.</span></span>  
  
## <a name="additions-to-support-multidimensional-models"></a><span data-ttu-id="b18f0-163">支援多維度模型的新增功能</span><span class="sxs-lookup"><span data-stu-id="b18f0-163">Additions to Support Multidimensional Models</span></span>  
 <span data-ttu-id="b18f0-164">CSDLBI 1.0 版註解僅支援表格式模型。</span><span class="sxs-lookup"><span data-stu-id="b18f0-164">Version 1.0 of the CSDLBI annotations supported only tabular models.</span></span> <span data-ttu-id="b18f0-165">1.1 版中已加入使用傳統 BI 開發工具所建立之多維度模型 (OLAP Cube) 的支援。</span><span class="sxs-lookup"><span data-stu-id="b18f0-165">In version 1.1, support was added for multidimensional models (OLAP cubes) created using traditional BI development tools.</span></span> <span data-ttu-id="b18f0-166">因此，現在您可以對多維度模型發出 XML 要求，並且接收模型的 CSDLBI 定義，以便於報表中使用。</span><span class="sxs-lookup"><span data-stu-id="b18f0-166">Therefore, you can now issue an XML request to a multidimensional model and receive a CSDLBI definition of the model, for use in reporting.</span></span>  
  
 <span data-ttu-id="b18f0-167">**Cube：** SQL Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 表格式資料庫只能包含一個模式。</span><span class="sxs-lookup"><span data-stu-id="b18f0-167">**Cubes:** A SQL Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tabular database can contain only one mode.</span></span> <span data-ttu-id="b18f0-168">相反地，每個多維度資料庫都可包含多個 Cube，且每個資料庫會與預設 Cube 產生關聯。</span><span class="sxs-lookup"><span data-stu-id="b18f0-168">In contrast, each multidimensional database can contain multiple cubes, each database being associated with a default cube.</span></span> <span data-ttu-id="b18f0-169">因此，對多維度伺服器發出 XML 要求時，必須指定 Cube，否則將會傳回預設 Cube 的 XML。</span><span class="sxs-lookup"><span data-stu-id="b18f0-169">Therefore, when issuing an XML request against a multidimensional server, it is necessary to specify the cube; otherwise, the XML for the default cube will be returned.</span></span>  
  
 <span data-ttu-id="b18f0-170">另外，Cube 的表示法非常類似表格式模型資料庫的表示法。</span><span class="sxs-lookup"><span data-stu-id="b18f0-170">The representation of a cube is otherwise very much like that of a tabular model database.</span></span> <span data-ttu-id="b18f0-171">Cube 名稱和 Cube 會對應表格式資料庫名稱和資料庫識別碼。</span><span class="sxs-lookup"><span data-stu-id="b18f0-171">The cube name and cube correspond to the tabular database name and database identifier.</span></span>  
  
 <span data-ttu-id="b18f0-172">**維度：** 維度會在 CSDLBI 中表示為實體 (資料表) 具有資料行和屬性。</span><span class="sxs-lookup"><span data-stu-id="b18f0-172">**Dimensions:** A dimension is represented in CSDLBI as an entity (table) with columns and properties.</span></span> <span data-ttu-id="b18f0-173">請注意，即使未包含在檢視方塊內，包含在模型中的維度仍將以 CSDL 輸出表示，並標示為 `Hidden`。</span><span class="sxs-lookup"><span data-stu-id="b18f0-173">Note that even if not included in a perspective, a dimension that is included in the model will be represented in the CSDL output, marked as `Hidden`.</span></span>  
  
 <span data-ttu-id="b18f0-174">**觀點：** 用戶端可以針對個別的觀點要求 CSDL。</span><span class="sxs-lookup"><span data-stu-id="b18f0-174">**Perspectives:** A client can request CSDL for individual perspectives.</span></span> <span data-ttu-id="b18f0-175">如需詳細資訊，請參閱 DISCOVER_CSDL_METADATA 資料列[集](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset)。</span><span class="sxs-lookup"><span data-stu-id="b18f0-175">For more information, see [DISCOVER_CSDL_METADATA Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset).</span></span>  
  
 <span data-ttu-id="b18f0-176">階層 **：** 階層在 CSDLBI 中受到支援，並以一組層級表示。</span><span class="sxs-lookup"><span data-stu-id="b18f0-176">**Hierarchies:** Hierarchies are supported and represented in CSDLBI as a set of levels.</span></span>  
  
 <span data-ttu-id="b18f0-177">**成員：** 已新增對預設成員的支援，且預設值會自動加入至 CSDLBI 輸出。</span><span class="sxs-lookup"><span data-stu-id="b18f0-177">**Members:** Support for the default member has been added and default values are automatically added to the CSDLBI output.</span></span>  
  
 <span data-ttu-id="b18f0-178">匯出**成員：** 多維度模型支援**所有**具有單一真實成員之子系的匯出成員。</span><span class="sxs-lookup"><span data-stu-id="b18f0-178">**Calculated Members:** Multidimensional models support calculated members for child of **All** with a single real member.</span></span>  
  
 <span data-ttu-id="b18f0-179">**維度屬性：** 在 CSDLBI 輸出中，維度屬性會受到支援，而且會自動標示為非匯總。</span><span class="sxs-lookup"><span data-stu-id="b18f0-179">**Dimension attributes:** In CSDLBI output, dimension attributes are supported and automatically marked as non-aggregatable.</span></span>  
  
 <span data-ttu-id="b18f0-180">**Kpi：** CSDLBI 版本1.1 支援 Kpi，但標記法已變更。</span><span class="sxs-lookup"><span data-stu-id="b18f0-180">**KPIs:** KPIs were supported in CSDLBI version 1.1, but the representation has changed.</span></span> <span data-ttu-id="b18f0-181">KPI 之前是量值的屬性。</span><span class="sxs-lookup"><span data-stu-id="b18f0-181">Before, a KPI was a property of a measure.</span></span> <span data-ttu-id="b18f0-182">在 1.1 版中，KPI 元素可以加入至量值</span><span class="sxs-lookup"><span data-stu-id="b18f0-182">In version 1.1, the KPI element can be added to a measure</span></span>  
  
 <span data-ttu-id="b18f0-183">**新屬性：** 已加入其他屬性來支援 DirectQuery 模型。</span><span class="sxs-lookup"><span data-stu-id="b18f0-183">**New properties:** Additional attributes were added to support DirectQuery models.</span></span>  
  
 <span data-ttu-id="b18f0-184">**限制：** 不支援資料格安全性。</span><span class="sxs-lookup"><span data-stu-id="b18f0-184">**Limitations:** Cell security is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b18f0-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b18f0-185">See Also</span></span>  
 [<span data-ttu-id="b18f0-186">商業智慧的 CSDL 註解 &#40;CSDLBI&#41;</span><span class="sxs-lookup"><span data-stu-id="b18f0-186">CSDL Annotations for Business Intelligence &#40;CSDLBI&#41;</span></span>](/analysis-services/csdlbi/csdl-annotations-for-business-intelligence-csdlbi)  
  
  
