---
title: 使用 XSD 架構中的批註 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, about annotated XSD schemas
- annotations [SQLXML]
- relationships [SQLXML]
- relationships [SQLXML], hierarchical relationships
- hierarchical relationships [SQLXML]
- mapping schema [SQLXML], scenarios for using
ms.assetid: 78f318a4-7a36-473b-9852-a4bae6940ce5
author: rothja
ms.author: jroth
ms.openlocfilehash: e2be94aa5815593d7a5a2e0c00bcd8849e81484e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595898"
---
# <a name="using-annotations-in-xsd-schemas-sqlxml-40"></a><span data-ttu-id="4da06-102">在 XSD 結構描述中使用註釋 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="4da06-102">Using Annotations in XSD Schemas (SQLXML 4.0)</span></span>
  <span data-ttu-id="4da06-103">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0 中，XSD 結構描述語言以類似 XML-Data Reduced (XDR) 結構描述語言所推出之註解的方式支援註解。</span><span class="sxs-lookup"><span data-stu-id="4da06-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0, the XSD schema language supports annotations in a manner similar to the annotations introduced in the XML-Data Reduced (XDR) schema language.</span></span> <span data-ttu-id="4da06-104">在 XSD 中有 XDR 不支援的其他註解。</span><span class="sxs-lookup"><span data-stu-id="4da06-104">There are additional annotations introduced in XSD that are not supported in XDR.</span></span>  
  
 <span data-ttu-id="4da06-105">這些註解可以在 XSD 結構描述內，用於指定 XML 到關聯式的對應。</span><span class="sxs-lookup"><span data-stu-id="4da06-105">These annotations can be used within the XSD schema to specify XML-to-relational mapping.</span></span> <span data-ttu-id="4da06-106">這包括 XSD 結構描述中的元素和屬性到資料庫中的資料表 (檢視) 和資料行之間的對應。</span><span class="sxs-lookup"><span data-stu-id="4da06-106">This includes mapping between elements and attributes in the XSD schema to tables (views) and columns in the databases.</span></span>  
  
 <span data-ttu-id="4da06-107">如果您沒有指定註解，就會使用預設對應。</span><span class="sxs-lookup"><span data-stu-id="4da06-107">If you do not specify the annotations, default mapping takes place.</span></span> <span data-ttu-id="4da06-108">根據預設，包含複雜類型的 XSD 元素會對應到指定之資料庫中的資料表 (檢視) 名稱，而包含簡單類型的元素或屬性會對應到具有相同名稱的資料行，做為元素或屬性。</span><span class="sxs-lookup"><span data-stu-id="4da06-108">By default, an XSD element with a complex type maps to a table (view) name in the specified database, and an element or attribute with a simple type maps to the column with the same name as the element or attribute.</span></span>  
  
 <span data-ttu-id="4da06-109">這些批註也可以用來指定 XML 中的階層式關聯性，因此代表資料庫中的關聯性，因為 XSD 架構只是關聯式資料的 XML 視圖。</span><span class="sxs-lookup"><span data-stu-id="4da06-109">These annotations can also be used to specify the hierarchical relationships in XML-thus representing the relationships in the database, because an XSD schema is simply an XML view of relational data.</span></span>  
  
 <span data-ttu-id="4da06-110">本節提供您可搭配 XSD 結構描述一起使用之註解的描述以及其使用方式的範例。</span><span class="sxs-lookup"><span data-stu-id="4da06-110">This section provides descriptions of the annotations you can use with XSD schemas and examples of their usage.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4da06-111">本節中的所有範例都會根據每個範例中所描述的註解式 XSD 結構描述，指定簡單的 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="4da06-111">All the examples in this section specify simple XPath queries against the annotated XSD schema described in each example.</span></span> <span data-ttu-id="4da06-112">同時會假設您熟悉 XPath 語言。</span><span class="sxs-lookup"><span data-stu-id="4da06-112">Familiarity with the XPath language is assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4da06-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="4da06-113">In This Section</span></span>  
 [<span data-ttu-id="4da06-114">&#40;SQLXML 4.0&#41;的 XSD 注釋</span><span class="sxs-lookup"><span data-stu-id="4da06-114">XSD Annotations &#40;SQLXML 4.0&#41;</span></span>](xsd-annotations-sqlxml-4-0.md)  
 <span data-ttu-id="4da06-115">列出您可以搭配 XSD 結構描述使用的註解、其描述，以及適用於 XDR 的相等註解。</span><span class="sxs-lookup"><span data-stu-id="4da06-115">Lists the annotations you can use with XSD schemas, their descriptions, and the equivalent annotations for XDR.</span></span>  
  
 [<span data-ttu-id="4da06-116">XSD 元素和屬性對資料表和資料行的預設對應 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4da06-116">Default Mapping of XSD Elements and Attributes to Tables and Columns &#40;SQLXML 4.0&#41;</span></span>](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
 <span data-ttu-id="4da06-117">說明預設對應，並提供與預設對應相關之工作的範例。</span><span class="sxs-lookup"><span data-stu-id="4da06-117">Explains default mapping and provides examples of tasks related to default mapping.</span></span>  
  
 [<span data-ttu-id="4da06-118">XSD 元素和屬性對資料表和資料行的明確對應 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4da06-118">Explicit Mapping of XSD Elements and Attributes to Tables and Columns &#40;SQLXML 4.0&#41;</span></span>](explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns.md)  
 <span data-ttu-id="4da06-119">說明與 `sql:relation` 和 `sql:field` 註解的明確對應，並提供範例。</span><span class="sxs-lookup"><span data-stu-id="4da06-119">Explains explicit mapping with the `sql:relation` and `sql:field` annotations, and provides examples.</span></span>  
  
 [<span data-ttu-id="4da06-120">使用 sql： relationship 指定關聯性 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4da06-120">Specifying Relationships Using sql:relationship &#40;SQLXML 4.0&#41;</span></span>](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
 <span data-ttu-id="4da06-121">描述及提供 `sql:relationship` 註解的範例。</span><span class="sxs-lookup"><span data-stu-id="4da06-121">Describes and provides examples of the `sql:relationship` annotation.</span></span>  
  
 [<span data-ttu-id="4da06-122">在 sql： relationship 上指定 sql：反向屬性 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4da06-122">Specifying the sql:inverse Attribute on sql:relationship &#40;SQLXML 4.0&#41;</span></span>](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)  
 <span data-ttu-id="4da06-123">描述 `sql:inverse` 註解。</span><span class="sxs-lookup"><span data-stu-id="4da06-123">Describes the `sql:inverse` annotation.</span></span>  
  
 [<span data-ttu-id="4da06-124">使用 sql： is-常數建立常數元素 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4da06-124">Creating Constant Elements Using sql:is-constant &#40;SQLXML 4.0&#41;</span></span>](creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)  
 <span data-ttu-id="4da06-125">描述及提供 `sql:is-constant` 註解的範例。</span><span class="sxs-lookup"><span data-stu-id="4da06-125">Describes and provides examples of the `sql:is-constant` annotation.</span></span>  
  
 [<span data-ttu-id="4da06-126">使用 sql：對應 &#40;SQLXML 4.0&#41;，從產生的 XML 檔排除架構元素</span><span class="sxs-lookup"><span data-stu-id="4da06-126">Excluding Schema Elements from the Resulting XML Document Using sql:mapped &#40;SQLXML 4.0&#41;</span></span>](excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)  
 <span data-ttu-id="4da06-127">描述及提供 `sql:mapped` 註解的範例。</span><span class="sxs-lookup"><span data-stu-id="4da06-127">Describes and provides examples of the `sql:mapped` annotation.</span></span>  
  
 [<span data-ttu-id="4da06-128">使用 sql： limit-field 和 sql： limit-value &#40;SQLXML 4.0&#41;篩選值</span><span class="sxs-lookup"><span data-stu-id="4da06-128">Filtering Values Using sql:limit-field and sql:limit-value &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 <span data-ttu-id="4da06-129">描述及提供 `sql:limit-field` 和 `sql:limit-value` 註解的範例。</span><span class="sxs-lookup"><span data-stu-id="4da06-129">Describes and provides examples of the `sql:limit-field` and `sql:limit-value` annotations.</span></span>  
  
 [<span data-ttu-id="4da06-130">使用 sql：索引鍵-欄位來識別索引鍵資料行 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4da06-130">Identifying Key Columns Using sql:key-fields &#40;SQLXML 4.0&#41;</span></span>](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)  
 <span data-ttu-id="4da06-131">描述及提供 `sql:key-fields` 註解的範例。</span><span class="sxs-lookup"><span data-stu-id="4da06-131">Describes and provides examples of the `sql:key-fields` annotation.</span></span>  
  
 [<span data-ttu-id="4da06-132">使用 targetNamespace 屬性來指定目標命名空間 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4da06-132">Specifying a Target Namespace Using the targetNamespace Attribute &#40;SQLXML 4.0&#41;</span></span>](specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
 <span data-ttu-id="4da06-133">描述並提供**targetNamespace**屬性的範例。</span><span class="sxs-lookup"><span data-stu-id="4da06-133">Describes and provides examples of the **targetNamespace** attribute.</span></span>  
  
 [<span data-ttu-id="4da06-134">使用 sql： prefix 建立有效的 ID、IDREF 和 IDREFS 類型屬性 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4da06-134">Creating Valid ID, IDREF, and IDREFS Type Attributes Using sql:prefix &#40;SQLXML 4.0&#41;</span></span>](creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)  
 <span data-ttu-id="4da06-135">描述及提供 `sql:prefix` 註解的範例。</span><span class="sxs-lookup"><span data-stu-id="4da06-135">Describes and provides examples of the `sql:prefix` annotation.</span></span>  
  
 [<span data-ttu-id="4da06-136">資料類型強制型轉和 sql： datatype 注釋 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4da06-136">Data Type Coercions and the sql:datatype Annotation &#40;SQLXML 4.0&#41;</span></span>](data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)  
 <span data-ttu-id="4da06-137">描述及提供 `sql:datatype` 註解的範例。</span><span class="sxs-lookup"><span data-stu-id="4da06-137">Describes and provides examples of the `sql:datatype` annotation.</span></span>  
  
 [<span data-ttu-id="4da06-138">將 XSD 資料類型對應到 XPath 資料類型 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4da06-138">Mapping XSD Data Types to XPath Data Types &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)  
 <span data-ttu-id="4da06-139">提供比較 XSD、XDR 與 XPath 資料類型的資料表，並列出相關的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 轉換。</span><span class="sxs-lookup"><span data-stu-id="4da06-139">Provides a table that compares XSD, XDR, and XPath datatypes and lists the relevant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conversions.</span></span>  
  
 [<span data-ttu-id="4da06-140">使用 sql： use-CDATA 建立 CDATA 區段 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4da06-140">Creating CDATA Sections Using sql:use-cdata &#40;SQLXML 4.0&#41;</span></span>](creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)  
 <span data-ttu-id="4da06-141">描述及提供 `sql:use-data` 註解的範例。</span><span class="sxs-lookup"><span data-stu-id="4da06-141">Describes and provides examples of the `sql:use-data` annotation.</span></span>  
  
 [<span data-ttu-id="4da06-142">使用 sql： &#40;SQLXML 4.0&#41;要求對 BLOB 資料的 URL 參考</span><span class="sxs-lookup"><span data-stu-id="4da06-142">Requesting URL References to BLOB Data Using sql:encode &#40;SQLXML 4.0&#41;</span></span>](requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)  
 <span data-ttu-id="4da06-143">描述及提供 `sql:encode` 註解的範例。</span><span class="sxs-lookup"><span data-stu-id="4da06-143">Describes and provides examples of the `sql:encode` annotation.</span></span>  
  
 [<span data-ttu-id="4da06-144">使用 sql：溢位欄位來抓取未使用的資料 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4da06-144">Retrieving Unconsumed Data Using the sql:overflow-field &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 <span data-ttu-id="4da06-145">描述及提供 `sql:overflow-field` 註解的範例。</span><span class="sxs-lookup"><span data-stu-id="4da06-145">Describes and provides examples of the `sql:overflow-field` annotation.</span></span>  
  
 [<span data-ttu-id="4da06-146">使用 sql:hide 來隱藏項目和屬性</span><span class="sxs-lookup"><span data-stu-id="4da06-146">Hiding Elements and Attributes by Using sql:hide</span></span>](hiding-elements-and-attributes-by-using-sql-hide.md)  
 <span data-ttu-id="4da06-147">描述及提供 `sql:hide` 註解的範例。</span><span class="sxs-lookup"><span data-stu-id="4da06-147">Describes and provides examples of the `sql:hide` annotation.</span></span>  
  
 [<span data-ttu-id="4da06-148">使用 sql:identity 和 sql:guid 註解</span><span class="sxs-lookup"><span data-stu-id="4da06-148">Using the sql:identity and sql:guid Annotations</span></span>](using-the-sql-identity-and-sql-guid-annotations.md)  
 <span data-ttu-id="4da06-149">描述及提供 `sql:identity` 和 `sql:guid` 註解的範例。</span><span class="sxs-lookup"><span data-stu-id="4da06-149">Describes and provides examples of the `sql:identity` and `sql:guid` annotations.</span></span>  
  
 [<span data-ttu-id="4da06-150">使用 sql:max-depth 來指定遞迴關聯性的深度</span><span class="sxs-lookup"><span data-stu-id="4da06-150">Specifying Depth in Recursive Relationships by Using sql:max-depth</span></span>](specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)  
 <span data-ttu-id="4da06-151">描述及提供 `sql:max-depth` 註解的範例。</span><span class="sxs-lookup"><span data-stu-id="4da06-151">Describes and provides examples of the `sql:max-depth` annotation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4da06-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4da06-152">See Also</span></span>  
 [<span data-ttu-id="4da06-153">&#40;SQLXML 4.0&#41;的批註式架構安全性考慮</span><span class="sxs-lookup"><span data-stu-id="4da06-153">Annotated Schema Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)  
  
  
