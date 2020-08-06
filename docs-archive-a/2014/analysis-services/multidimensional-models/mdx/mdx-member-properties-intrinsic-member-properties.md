---
title: " (MDX) 的內建成員屬性 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- intrinsic member properties [MDX]
ms.assetid: 84e6fe64-9b37-4e79-bedf-ae02e80bfce8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 268203d044734bb4e6a1d2acf6311ee7ef828a53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698632"
---
# <a name="intrinsic-member-properties-mdx"></a><span data-ttu-id="8262f-102">內建成員屬性 (MDX)</span><span class="sxs-lookup"><span data-stu-id="8262f-102">Intrinsic Member Properties (MDX)</span></span>
  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="8262f-103">會公開維度成員的內建屬性，您可以將它們納入查詢中，以便傳回用於自訂應用程式的其他資料或中繼資料，或協助模型調查或建構。</span><span class="sxs-lookup"><span data-stu-id="8262f-103">exposes intrinsic properties on dimension members that you can include in a query to return additional data or metadata for use in a custom application, or to assist in model investigation or construction.</span></span> <span data-ttu-id="8262f-104">如果您使用 SQL Server 用戶端工具，您可以在 SQL Server Management Studio (SSMS) 中檢視內建屬性。</span><span class="sxs-lookup"><span data-stu-id="8262f-104">If you are using the SQL Server client tools, you can view intrinsic properties in SQL Server Management Studio (SSMS).</span></span>  
  
 <span data-ttu-id="8262f-105">內建屬性包括 `ID`、`KEY`、`KEYx` 和 `NAME`，這些屬性可在任何層級公開給每位成員。</span><span class="sxs-lookup"><span data-stu-id="8262f-105">Intrinsic properties include `ID`, `KEY`, `KEYx`, and `NAME`, which are properties exposed by every member, at any level.</span></span> <span data-ttu-id="8262f-106">您也可以傳回位置資訊，例如 `LEVEL_NUMBER` 或 `PARENT_UNIQUE_NAME`，以及其他資訊。</span><span class="sxs-lookup"><span data-stu-id="8262f-106">You can also return positional information, such as `LEVEL_NUMBER` or `PARENT_UNIQUE_NAME`, among others.</span></span>  
  
 <span data-ttu-id="8262f-107">取決於您如何建立查詢以及用來執行查詢的用戶端應用程式，成員屬性不一定會顯示在結果集中。</span><span class="sxs-lookup"><span data-stu-id="8262f-107">Depending on how you construct the query, and on the client application you are using to execute queries, member properties may or may not be visible in the result set.</span></span> <span data-ttu-id="8262f-108">如果您使用 SQL Server Management Studio 測試或執行查詢，您可以按兩下結果集中的成員，即可開啟 [成員屬性] 對話方塊，顯示每個內建成員屬性的值。</span><span class="sxs-lookup"><span data-stu-id="8262f-108">If you are using SQL Server Management Studio to test or run queries, you can double-click a member in the result set to open the Member Properties dialog box, showing the values for each intrinsic member property.</span></span>  
  
 <span data-ttu-id="8262f-109">如需有關使用及檢視維度成員屬性的簡介，請參閱 [在 SSMS 的 MDX 查詢視窗中檢視 SSAS 成員屬性](https://go.microsoft.com/fwlink/?LinkId=317362)。</span><span class="sxs-lookup"><span data-stu-id="8262f-109">For an introduction to using and viewing dimension member properties, see [Viewing SSAS Member Properties within an MDX Query Window in SSMS](https://go.microsoft.com/fwlink/?LinkId=317362).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8262f-110">作為提供者，符合 OLE DB 規格的 OLAP 區段（日期為1999年3月 (2.6) ）， [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 支援本主題中列出的內建成員屬性。</span><span class="sxs-lookup"><span data-stu-id="8262f-110">As a provider that is compliant with the OLAP section of the OLE DB specification dated March 1999 (2.6), [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supports the intrinsic member properties listed in this topic.</span></span>  
>   
>  <span data-ttu-id="8262f-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 以外的提供者可支援其他內建成員屬性。</span><span class="sxs-lookup"><span data-stu-id="8262f-111">Providers other than [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] may support additional intrinsic member properties.</span></span> <span data-ttu-id="8262f-112">如需其他提供者支援之內建成員屬性的詳細資訊，請參閱這些提供者提供的文件。</span><span class="sxs-lookup"><span data-stu-id="8262f-112">For more information about the intrinsic member properties supported by other providers, refer to the documentation that comes with those providers.</span></span>  
  
## <a name="types-of-member-properties"></a><span data-ttu-id="8262f-113">成員屬性類型</span><span class="sxs-lookup"><span data-stu-id="8262f-113">Types of Member Properties</span></span>  
 <span data-ttu-id="8262f-114">支援的內建成員屬性 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 有兩種類型：</span><span class="sxs-lookup"><span data-stu-id="8262f-114">The intrinsic member properties supported by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] are of two types:</span></span>  
  
 <span data-ttu-id="8262f-115">區分內容的成員屬性</span><span class="sxs-lookup"><span data-stu-id="8262f-115">Context sensitive member properties</span></span>  
 <span data-ttu-id="8262f-116">這些成員屬性必須用於特定階層或層級的內容，而且要將值提供給指定維度或層級的每個成員。</span><span class="sxs-lookup"><span data-stu-id="8262f-116">These member properties must be used in the context of a specific hierarchy or level, and supply values for each member of the specified dimension or level.</span></span>  
  
 <span data-ttu-id="8262f-117">請注意下列範例如何加入 `KEY` 屬性的路徑：`MEMBER [Measures].[Parent Member Key] AS [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")`。</span><span class="sxs-lookup"><span data-stu-id="8262f-117">Notice how the following example includes the path for the `KEY` property: `MEMBER [Measures].[Parent Member Key] AS [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")`.</span></span>  
  
 <span data-ttu-id="8262f-118">不區分內容的成員屬性</span><span class="sxs-lookup"><span data-stu-id="8262f-118">Non-context sensitive member properties</span></span>  
 <span data-ttu-id="8262f-119">這些成員屬性無法用於特定維度或層級的內容，並且會傳回座標軸上所有成員的值。</span><span class="sxs-lookup"><span data-stu-id="8262f-119">These member properties cannot be used in the context of a specific dimension or level, and return values for all members on an axis.</span></span>  
  
 <span data-ttu-id="8262f-120">不易受內容影響的屬性是獨立的，而且不包含路徑資訊。</span><span class="sxs-lookup"><span data-stu-id="8262f-120">Context-insensitive properties standalone and do not include path information.</span></span> <span data-ttu-id="8262f-121">請注意，在下列範例中，沒有為 `PARENT_UNIQUE_NAME` 指定維度或層級：`DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS`</span><span class="sxs-lookup"><span data-stu-id="8262f-121">Notice how there is no dimension or level specified for `PARENT_UNIQUE_NAME` in the following example: `DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS`</span></span>  
  
 <span data-ttu-id="8262f-122">不管內建成員屬性是否會區分內容，都適用以下使用方式規則：</span><span class="sxs-lookup"><span data-stu-id="8262f-122">Regardless of whether the intrinsic member property is context sensitive or not, the following usage rules apply:</span></span>  
  
-   <span data-ttu-id="8262f-123">您只能指定座標軸上預計之維度成員相關的內建成員屬性。</span><span class="sxs-lookup"><span data-stu-id="8262f-123">You can specify only those intrinsic member properties that relate to dimension members that are projected on the axis.</span></span>  
  
-   <span data-ttu-id="8262f-124">您可以利用不區分內容的內建成員屬性，在同一個查詢中混合區分內容的成員屬性要求。</span><span class="sxs-lookup"><span data-stu-id="8262f-124">You can mix requests for context sensitive member properties in the same query with non-context sensitive intrinsic member properties.</span></span>  
  
-   <span data-ttu-id="8262f-125">您可以使用 `PROPERTIES` 關鍵字以查詢屬性。</span><span class="sxs-lookup"><span data-stu-id="8262f-125">You use the `PROPERTIES` keyword to query for the properties.</span></span>  
  
 <span data-ttu-id="8262f-126">下列各節將描述中可用的各種內容相關和不區分內容的內建成員屬性 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ，以及如何搭配 `PROPERTIES` 每個屬性類型使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="8262f-126">The following sections describe both the various context sensitive and non-context sensitive intrinsic member properties available in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], and how to use the `PROPERTIES` keyword with each type of property.</span></span>  
  
## <a name="context-sensitive-member-properties"></a><span data-ttu-id="8262f-127">區分內容的成員屬性</span><span class="sxs-lookup"><span data-stu-id="8262f-127">Context Sensitive Member Properties</span></span>  
 <span data-ttu-id="8262f-128">所有維度成員及層級成員支援區分內容的內建成員屬性清單。</span><span class="sxs-lookup"><span data-stu-id="8262f-128">All dimension members and level members support a list of intrinsic member properties that are context sensitive.</span></span> <span data-ttu-id="8262f-129">下表列出這些區分內容的屬性。</span><span class="sxs-lookup"><span data-stu-id="8262f-129">The following table lists these context-sensitive properties.</span></span>  
  
|<span data-ttu-id="8262f-130">屬性</span><span class="sxs-lookup"><span data-stu-id="8262f-130">Property</span></span>|<span data-ttu-id="8262f-131">描述</span><span class="sxs-lookup"><span data-stu-id="8262f-131">Description</span></span>|  
|--------------|-----------------|  
|`ID`|<span data-ttu-id="8262f-132">內部維護用的成員識別碼。</span><span class="sxs-lookup"><span data-stu-id="8262f-132">The internally maintained ID for the member.</span></span>|  
|`Key`|<span data-ttu-id="8262f-133">原始資料類型的成員索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="8262f-133">The value of the member key in the original data type.</span></span> <span data-ttu-id="8262f-134">MEMBER_KEY 是為回溯相容性而提供。</span><span class="sxs-lookup"><span data-stu-id="8262f-134">MEMBER_KEY is for backward-compatibility.</span></span>  <span data-ttu-id="8262f-135">對於非複合索引鍵，MEMBER_KEY 的值與 KEY0 相同，對於複合索引鍵，MEMBER_KEY 屬性為 Null。</span><span class="sxs-lookup"><span data-stu-id="8262f-135">MEMBER_KEY has the same value as KEY0 for non-composite keys, and MEMBER_KEY property is null for composite keys.</span></span>|  
|`KEYx`|<span data-ttu-id="8262f-136">成員的索引鍵，其中 x 是索引鍵以零為基底的序數。</span><span class="sxs-lookup"><span data-stu-id="8262f-136">The key for the member, where x is the zero-based ordinal of the key.</span></span> <span data-ttu-id="8262f-137">KEY0 可用於複合和非複合索引鍵，但主要是用於複合索引鍵。</span><span class="sxs-lookup"><span data-stu-id="8262f-137">KEY0 is available for composite and non-composite keys, but primarily used for composite keys.</span></span><br /><br /> <span data-ttu-id="8262f-138">關於複合索引鍵，KEY0、KEY1、KEY2 等等，共同形成複合索引鍵。</span><span class="sxs-lookup"><span data-stu-id="8262f-138">For composite keys, KEY0, KEY1, KEY2, and so on, collectively form the composite key.</span></span> <span data-ttu-id="8262f-139">您可以在查詢中單獨使用每一項，藉以傳回複合索引鍵的該部分。</span><span class="sxs-lookup"><span data-stu-id="8262f-139">You can use each one independently in a query to return that portion of the composite key.</span></span> <span data-ttu-id="8262f-140">例如，指定 KEY0 可傳回複合索引鍵的第一個部分，指定 KEY1 傳回複合索引鍵的下一部分，依此類推。</span><span class="sxs-lookup"><span data-stu-id="8262f-140">For example, specifying KEY0 returns the first part of the composite key, specifying KEY1 returns the next part of the composite key, and so on.</span></span><br /><br /> <span data-ttu-id="8262f-141">如果索引鍵為非複合鍵，則 KEY0 相當於 `Key`。</span><span class="sxs-lookup"><span data-stu-id="8262f-141">If the key is non-composite, then KEY0 is equivalent to `Key`.</span></span><br /><br /> <span data-ttu-id="8262f-142">請注意，`KEYx` 可用於內容中，也可以在沒有內容的情況下使用。</span><span class="sxs-lookup"><span data-stu-id="8262f-142">Note that `KEYx` can be used in context as well as without context.</span></span> <span data-ttu-id="8262f-143">因此，兩個清單上都有它。</span><span class="sxs-lookup"><span data-stu-id="8262f-143">For this reason, it appears in both lists.</span></span><br /><br /> <span data-ttu-id="8262f-144">如需如何使用此成員屬性的範例，請參閱 [簡單的 MDX 小知識：Key0、Key1、Key2](https://go.microsoft.com/fwlink/?LinkId=317364)。</span><span class="sxs-lookup"><span data-stu-id="8262f-144">For an example of how to use this member property, see [A Simple MDX Tidbit: Key0, Key1, Key2](https://go.microsoft.com/fwlink/?LinkId=317364).</span></span>|  
|`Name`|<span data-ttu-id="8262f-145">成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="8262f-145">The name of the member.</span></span>|  
  
### <a name="properties-syntax-for-context-sensitive-properties"></a><span data-ttu-id="8262f-146">區分內容屬性的 PROPERTIES 語法</span><span class="sxs-lookup"><span data-stu-id="8262f-146">PROPERTIES Syntax for Context Sensitive Properties</span></span>  
 <span data-ttu-id="8262f-147">您可以在特定維度或層級的內容中使用這些成員屬性，而且要將值提供給指定維度或階層的每個成員。</span><span class="sxs-lookup"><span data-stu-id="8262f-147">You use these member properties in the context of a specific dimension or level, and supply values for each member of the specified dimension or level.</span></span>  
  
 <span data-ttu-id="8262f-148">對於維度成員屬性，您可以在屬性名稱前面加上套用該屬性的維度名稱。</span><span class="sxs-lookup"><span data-stu-id="8262f-148">For dimension member properties, you precede the name of the property with the name of the dimension to which the property applies.</span></span> <span data-ttu-id="8262f-149">下列範例會顯示適當語法：</span><span class="sxs-lookup"><span data-stu-id="8262f-149">The following example shows the appropriate syntax:</span></span>  
  
 `DIMENSION PROPERTIES Dimension.Property_name`  
  
 <span data-ttu-id="8262f-150">對於層級成員屬性，您可以在屬性名稱前面，只加上層級名稱，或者對於其他規格，則可加上維度及層級名稱。</span><span class="sxs-lookup"><span data-stu-id="8262f-150">For a level member property, you can precede the name of the property with just the level name or, for additional specification, both the dimension and level name.</span></span> <span data-ttu-id="8262f-151">下列範例會顯示適當語法：</span><span class="sxs-lookup"><span data-stu-id="8262f-151">The following example shows the appropriate syntax:</span></span>  
  
 `DIMENSION PROPERTIES [Dimension.]Level.Property_name`  
  
 <span data-ttu-id="8262f-152">為了方便說明，您要傳回 `[Sales]` 維度中每個參考成員的所有名稱。</span><span class="sxs-lookup"><span data-stu-id="8262f-152">To illustrate, you would like to return all the names of each referenced member in the `[Sales]` dimension.</span></span> <span data-ttu-id="8262f-153">若要傳回這些名稱，您要在多維度運算式 (MDX) 查詢中使用以下陳述式：</span><span class="sxs-lookup"><span data-stu-id="8262f-153">To return these names, you would use the following statement in a Multidimensional Expressions (MDX) query:</span></span>  
  
 `DIMENSION PROPERTIES [Sales].Name`  
  
## <a name="non-context-sensitive-member-properties"></a><span data-ttu-id="8262f-154">不區分內容的成員屬性</span><span class="sxs-lookup"><span data-stu-id="8262f-154">Non-Context Sensitive Member Properties</span></span>  
 <span data-ttu-id="8262f-155">所有成員支援同樣不顧內容的內建成員屬性清單。</span><span class="sxs-lookup"><span data-stu-id="8262f-155">All members support a list of intrinsic member properties that are the same regardless of context.</span></span> <span data-ttu-id="8262f-156">這些屬性能提供應用程式可用以加強使用者經驗的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="8262f-156">These properties provide additional information that can be used by applications to enhance the user's experience.</span></span>  
  
 <span data-ttu-id="8262f-157">下表列出支援的不區分內容內建屬性 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8262f-157">The following table lists the non-context sensitive intrinsic properties supported by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8262f-158">MEMBERS 結構描述資料列集中的資料行支援下表列出的內建成員屬性。</span><span class="sxs-lookup"><span data-stu-id="8262f-158">Columns in the MEMBERS schema rowset support the intrinsic member properties listed in the following table.</span></span> <span data-ttu-id="8262f-159">如需架構資料列集的詳細資訊 `MEMBERS` ，請參閱 MDSCHEMA_MEMBERS 資料列[集](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-members-rowset)。</span><span class="sxs-lookup"><span data-stu-id="8262f-159">For more information about the `MEMBERS` schema rowset, see [MDSCHEMA_MEMBERS Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-members-rowset).</span></span>  
  
|<span data-ttu-id="8262f-160">屬性</span><span class="sxs-lookup"><span data-stu-id="8262f-160">Property</span></span>|<span data-ttu-id="8262f-161">描述</span><span class="sxs-lookup"><span data-stu-id="8262f-161">Description</span></span>|  
|--------------|-----------------|  
|`CATALOG_NAME`|<span data-ttu-id="8262f-162">此一成員所屬 Cube 的名稱。</span><span class="sxs-lookup"><span data-stu-id="8262f-162">The name of the cube to which this member belongs.</span></span>|  
|`CHILDREN_CARDINALITY`|<span data-ttu-id="8262f-163">成員擁有的子系數目。</span><span class="sxs-lookup"><span data-stu-id="8262f-163">The number of children that the member has.</span></span> <span data-ttu-id="8262f-164">這可為一個估計值，因此您不應該依賴此值做為確實計數。</span><span class="sxs-lookup"><span data-stu-id="8262f-164">This can be an estimate, so you should not rely on this to be the exact count.</span></span> <span data-ttu-id="8262f-165">提供者應會傳回最佳的可能估計值。</span><span class="sxs-lookup"><span data-stu-id="8262f-165">Providers should return the best estimate possible.</span></span>|  
|`CUSTOM_ROLLUP`|<span data-ttu-id="8262f-166">自訂成員運算式。</span><span class="sxs-lookup"><span data-stu-id="8262f-166">The custom member expression.</span></span>|  
|`CUSTOM_ROLLUP_PROPERTIES`|<span data-ttu-id="8262f-167">自訂成員屬性。</span><span class="sxs-lookup"><span data-stu-id="8262f-167">The custom member properties.</span></span>|  
|`DESCRIPTION`|<span data-ttu-id="8262f-168">成員的可讀取描述。</span><span class="sxs-lookup"><span data-stu-id="8262f-168">A human-readable description of the member.</span></span>|  
|`DIMENSION_UNIQUE_NAME`|<span data-ttu-id="8262f-169">此一成員所屬維度的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="8262f-169">The unique name of the dimension to which this member belongs.</span></span> <span data-ttu-id="8262f-170">對於會依識別資格產生唯一名稱的提供者，此名稱的每個元件會使用分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8262f-170">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`HIERARCHY_UNIQUE_NAME`|<span data-ttu-id="8262f-171">階層架構的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="8262f-171">The unique name of the hierarchy.</span></span> <span data-ttu-id="8262f-172">如果該成員屬於多個階層，該成員所屬的每個階層都會有一個資料列。</span><span class="sxs-lookup"><span data-stu-id="8262f-172">If the member belongs to more than one hierarchy, there is one row for each hierarchy to which the member belongs.</span></span> <span data-ttu-id="8262f-173">對於會依識別資格產生唯一名稱的提供者，此名稱的每個元件會使用分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8262f-173">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`IS_DATAMEMBER`|<span data-ttu-id="8262f-174">指出成員是否為資料成員的布林值。</span><span class="sxs-lookup"><span data-stu-id="8262f-174">A Boolean that indicates whether the member is a data member.</span></span>|  
|`IS_PLACEHOLDERMEMBER`|<span data-ttu-id="8262f-175">表示成員是否為預留位置的布林值。</span><span class="sxs-lookup"><span data-stu-id="8262f-175">A Boolean that indicates whether the member is a placeholder.</span></span>|  
|`KEYx`|<span data-ttu-id="8262f-176">成員的索引鍵，其中 x 是索引鍵以零為基底的序數。</span><span class="sxs-lookup"><span data-stu-id="8262f-176">The key for the member, where x is the zero-based ordinal of the key.</span></span> <span data-ttu-id="8262f-177">KEY0 可用於複合和非複合索引鍵。</span><span class="sxs-lookup"><span data-stu-id="8262f-177">KEY0 is available for composite and non-composite keys.</span></span><br /><br /> <span data-ttu-id="8262f-178">如果索引鍵為非複合鍵，則 KEY0 相當於 `Key`。</span><span class="sxs-lookup"><span data-stu-id="8262f-178">If the key is non-composite, then KEY0 is equivalent to `Key`.</span></span><br /><br /> <span data-ttu-id="8262f-179">關於複合索引鍵，KEY0、KEY1、KEY2 等等，共同形成複合索引鍵。</span><span class="sxs-lookup"><span data-stu-id="8262f-179">For composite keys, KEY0, KEY1, KEY2, and so on, collectively form the composite key.</span></span> <span data-ttu-id="8262f-180">您可以在查詢中單獨參考每一項，藉以傳回複合索引鍵的該部分。</span><span class="sxs-lookup"><span data-stu-id="8262f-180">You can reference each one independently in a query to return that portion of the composite key.</span></span> <span data-ttu-id="8262f-181">例如，指定 KEY0 可傳回複合索引鍵的第一個部分，指定 KEY1 傳回複合索引鍵的下一部分，依此類推。</span><span class="sxs-lookup"><span data-stu-id="8262f-181">For example, specifying KEY0 returns the first part of the composite key, specifying KEY1 returns the next part of the composite key, and so on.</span></span><br /><br /> <span data-ttu-id="8262f-182">請注意，`KEYx` 可用於內容中，也可以在沒有內容的情況下使用。</span><span class="sxs-lookup"><span data-stu-id="8262f-182">Note that `KEYx` can be used in context as well as without context.</span></span> <span data-ttu-id="8262f-183">因此，兩個清單上都有它。</span><span class="sxs-lookup"><span data-stu-id="8262f-183">For this reason, it appears in both lists.</span></span><br /><br /> <span data-ttu-id="8262f-184">如需如何使用此成員屬性的範例，請參閱 [簡單的 MDX 小知識：Key0、Key1、Key2](https://go.microsoft.com/fwlink/?LinkId=317364)。</span><span class="sxs-lookup"><span data-stu-id="8262f-184">For an example of how to use this member property, see [A Simple MDX Tidbit: Key0, Key1, Key2](https://go.microsoft.com/fwlink/?LinkId=317364).</span></span>|  
|<span data-ttu-id="8262f-185">`LCID` *x*</span><span class="sxs-lookup"><span data-stu-id="8262f-185">`LCID` *x*</span></span>|<span data-ttu-id="8262f-186">以地區設定識別碼十六進位值翻譯的成員標題，其中 *x* 是地區設定識別碼十進位值 (例如，代表加拿大英文的 LCID1009)。</span><span class="sxs-lookup"><span data-stu-id="8262f-186">The translation of the member caption in the locale ID hexadecimal value, where *x* is the locale ID decimal value (for example, LCID1009 as English-Canada).</span></span> <span data-ttu-id="8262f-187">只有當翻譯的標題資料行繫結至資料來源時，才適用此功能。</span><span class="sxs-lookup"><span data-stu-id="8262f-187">This is only available if the translation has the caption column bound to the data source.</span></span>|  
|`LEVEL_NUMBER`|<span data-ttu-id="8262f-188">成員距根階層的距離。</span><span class="sxs-lookup"><span data-stu-id="8262f-188">The distance of the member from the root of the hierarchy.</span></span> <span data-ttu-id="8262f-189">根層級為零。</span><span class="sxs-lookup"><span data-stu-id="8262f-189">The root level is zero.</span></span>|  
|`LEVEL_UNIQUE_NAME`|<span data-ttu-id="8262f-190">成員所屬層級的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="8262f-190">The unique name of the level to which the member belongs.</span></span> <span data-ttu-id="8262f-191">對於會依識別資格產生唯一名稱的提供者，此名稱的每個元件會使用分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8262f-191">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`MEMBER_CAPTION`|<span data-ttu-id="8262f-192">與該成員關聯的標籤或標題。</span><span class="sxs-lookup"><span data-stu-id="8262f-192">A label or caption associated with the member.</span></span> <span data-ttu-id="8262f-193">標題主要是供顯示之用。</span><span class="sxs-lookup"><span data-stu-id="8262f-193">The caption is primarily for display purposes.</span></span> <span data-ttu-id="8262f-194">如果標題不存在，查詢就會傳回 `MEMBER_NAME`。</span><span class="sxs-lookup"><span data-stu-id="8262f-194">If a caption does not exist, the query returns `MEMBER_NAME`.</span></span>|  
|`MEMBER_KEY`|<span data-ttu-id="8262f-195">原始資料類型的成員索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="8262f-195">The value of the member key in the original data type.</span></span> <span data-ttu-id="8262f-196">MEMBER_KEY 是為回溯相容性而提供。</span><span class="sxs-lookup"><span data-stu-id="8262f-196">MEMBER_KEY is for backward-compatibility.</span></span>  <span data-ttu-id="8262f-197">對於非複合索引鍵，MEMBER_KEY 的值與 KEY0 相同，對於複合索引鍵，MEMBER_KEY 屬性為 Null。</span><span class="sxs-lookup"><span data-stu-id="8262f-197">MEMBER_KEY has the same value as KEY0 for non-composite keys, and MEMBER_KEY property is null for composite keys.</span></span>|  
|`MEMBER_NAME`|<span data-ttu-id="8262f-198">成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="8262f-198">The name of the member.</span></span>|  
|`MEMBER_TYPE`|<span data-ttu-id="8262f-199">成員的類型。</span><span class="sxs-lookup"><span data-stu-id="8262f-199">The type of the member.</span></span> <span data-ttu-id="8262f-200">此屬性可以有下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="8262f-200">This property can have one of the following values:</span></span> <br /><span data-ttu-id="8262f-201">**MDMEMBER_TYPE_REGULAR**</span><span class="sxs-lookup"><span data-stu-id="8262f-201">**MDMEMBER_TYPE_REGULAR**</span></span><br /><span data-ttu-id="8262f-202">**MDMEMBER_TYPE_ALL**</span><span class="sxs-lookup"><span data-stu-id="8262f-202">**MDMEMBER_TYPE_ALL**</span></span><br /><span data-ttu-id="8262f-203">**MDMEMBER_TYPE_FORMULA**</span><span class="sxs-lookup"><span data-stu-id="8262f-203">**MDMEMBER_TYPE_FORMULA**</span></span><br /><span data-ttu-id="8262f-204">**MDMEMBER_TYPE_MEASURE**</span><span class="sxs-lookup"><span data-stu-id="8262f-204">**MDMEMBER_TYPE_MEASURE**</span></span><br /><span data-ttu-id="8262f-205">**MDMEMBER_TYPE_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="8262f-205">**MDMEMBER_TYPE_UNKNOWN**</span></span><br /><br /> <br /><br /> <span data-ttu-id="8262f-206">MDMEMBER_TYPE_FORMULA 優先於 MDMEMBER_TYPE_MEASURE。</span><span class="sxs-lookup"><span data-stu-id="8262f-206">MDMEMBER_TYPE_FORMULA takes precedence over MDMEMBER_TYPE_MEASURE.</span></span> <span data-ttu-id="8262f-207">因此，如果 Measures 維度有一個公式 (導出) 成員，導出成員的 `MEMBER_TYPE` 屬性為 MDMEMBER_TYPE_FORMULA。</span><span class="sxs-lookup"><span data-stu-id="8262f-207">Therefore, if there is a formula (calculated) member on the Measures dimension, the `MEMBER_TYPE` property for the calculated member is MDMEMBER_TYPE_FORMULA.</span></span>|  
|`MEMBER_UNIQUE_NAME`|<span data-ttu-id="8262f-208">成員的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="8262f-208">The unique name of the member.</span></span> <span data-ttu-id="8262f-209">對於會依識別資格產生唯一名稱的提供者，此名稱的每個元件會使用分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8262f-209">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`MEMBER_VALUE`|<span data-ttu-id="8262f-210">原始類型的成員值。</span><span class="sxs-lookup"><span data-stu-id="8262f-210">The value of the member in the original type.</span></span>|  
|`PARENT_COUNT`|<span data-ttu-id="8262f-211">此成員擁有的父系數目。</span><span class="sxs-lookup"><span data-stu-id="8262f-211">The number of parents that this member has.</span></span>|  
|`PARENT_LEVEL`|<span data-ttu-id="8262f-212">成員的父系距階層之根層級的距離。</span><span class="sxs-lookup"><span data-stu-id="8262f-212">The distance of the member's parent from the root level of the hierarchy.</span></span> <span data-ttu-id="8262f-213">根層級為零。</span><span class="sxs-lookup"><span data-stu-id="8262f-213">The root level is zero.</span></span>|  
|`PARENT_UNIQUE_NAME`|<span data-ttu-id="8262f-214">成員之父系的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="8262f-214">The unique name of the member's parent.</span></span> <span data-ttu-id="8262f-215">如果是根層級的任何成員，則會傳回 `NULL`。</span><span class="sxs-lookup"><span data-stu-id="8262f-215">`NULL` is returned for any members at the root level.</span></span> <span data-ttu-id="8262f-216">對於會依識別資格產生唯一名稱的提供者，此名稱的每個元件會使用分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8262f-216">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`SKIPPED_LEVELS`|<span data-ttu-id="8262f-217">略過的成員層級數目。</span><span class="sxs-lookup"><span data-stu-id="8262f-217">The number of skipped levels for the member.</span></span>|  
|`UNARY_OPERATOR`|<span data-ttu-id="8262f-218">成員的一元運算子。</span><span class="sxs-lookup"><span data-stu-id="8262f-218">The unary operator for the member.</span></span>|  
|`UNIQUE_NAME`|<span data-ttu-id="8262f-219">成員的完整名稱以此格式表示：[維度]、[層級]、[key6]。</span><span class="sxs-lookup"><span data-stu-id="8262f-219">The fully-qualified name of the member, in this format: [dimension].[level].[key6.]</span></span>|  
  
### <a name="properties-syntax-for-non-context-sensitive-properties"></a><span data-ttu-id="8262f-220">不區分內容屬性的 PROPERTIES 語法</span><span class="sxs-lookup"><span data-stu-id="8262f-220">PROPERTIES Syntax for Non-Context Sensitive Properties</span></span>  
 <span data-ttu-id="8262f-221">使用以下語法指定會使用 `PROPERTIES` 關鍵字的內建、不區分內容的成員屬性：</span><span class="sxs-lookup"><span data-stu-id="8262f-221">Use the following syntax to specify an intrinsic, non-context sensitive member property using the `PROPERTIES` keyword:</span></span>  
  
 `DIMENSION PROPERTIES Property`  
  
 <span data-ttu-id="8262f-222">請注意，此語法不允許依維度或層級限定屬性。</span><span class="sxs-lookup"><span data-stu-id="8262f-222">Notice that this syntax does not allow the property to be qualified by a dimension or level.</span></span> <span data-ttu-id="8262f-223">因為座標軸的所有成員套用了不區分內容的內建成員屬性，所以無法限定屬性。</span><span class="sxs-lookup"><span data-stu-id="8262f-223">The property cannot be qualified because an intrinsic member property that is not context sensitive applies to all members of an axis.</span></span>  
  
 <span data-ttu-id="8262f-224">例如，指定 `DESCRIPTION` 內建成員屬性的 MDX 陳述式會有以下語法：</span><span class="sxs-lookup"><span data-stu-id="8262f-224">For example, an MDX statement that specifies the `DESCRIPTION` intrinsic member property would have the following syntax:</span></span>  
  
 `DIMENSION PROPERTIES DESCRIPTION`  
  
 <span data-ttu-id="8262f-225">此陳述式會傳回座標軸維度中每個成員的描述。</span><span class="sxs-lookup"><span data-stu-id="8262f-225">This statement returns the description of each member in the axis dimension.</span></span> <span data-ttu-id="8262f-226">如果您嘗試使用維度或層級（如*維度* `.DESCRIPTION` 或*層級*）來限定屬性， `.DESCRIPTION` 則語句不會進行驗證。</span><span class="sxs-lookup"><span data-stu-id="8262f-226">If you tried to qualify the property with a dimension or level, as in *Dimension*`.DESCRIPTION` or *Level*`.DESCRIPTION`, the statement would not validate.</span></span>  
  
### <a name="example"></a><span data-ttu-id="8262f-227">範例</span><span class="sxs-lookup"><span data-stu-id="8262f-227">Example</span></span>  
 <span data-ttu-id="8262f-228">下列範例顯示傳回內建屬性的 MDX 查詢。</span><span class="sxs-lookup"><span data-stu-id="8262f-228">The following examples show MDX queries that return intrinsic properties.</span></span>  
  
 <span data-ttu-id="8262f-229">**範例 1：在查詢中使用會受內容影響的內建屬性**</span><span class="sxs-lookup"><span data-stu-id="8262f-229">**Example 1: Use context-sensitive intrinsic properties in query**</span></span>  
  
 <span data-ttu-id="8262f-230">下列範例會傳回父系識別碼、索引鍵和每項產品類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="8262f-230">The following example returns parent ID, key, and name for each product category.</span></span> <span data-ttu-id="8262f-231">請注意屬性如何公開為量值。</span><span class="sxs-lookup"><span data-stu-id="8262f-231">Notice how the properties are exposed as measures.</span></span> <span data-ttu-id="8262f-232">在您執行查詢時，這可讓您在資料格集中檢視屬性，而非 SSMS 的 [成員屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8262f-232">This lets you view the properties in a cellset when you run the query, rather than the Member Properties dialog in SSMS.</span></span> <span data-ttu-id="8262f-233">您可以執行類似此項目的查詢，以便從已部署的 Cube 擷取成員中繼資料。</span><span class="sxs-lookup"><span data-stu-id="8262f-233">You might run a query like this to retrieve member metadata from a cube that is already deployed.</span></span>  
  
```  
WITH  
MEMBER [Measures].[Parent Member ID] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("ID")  
MEMBER [Measures].[Parent Member Key] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")  
MEMBER [Measures].[Parent Member Name] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("Name")  
SELECT  
 {[Measures].[Parent Member ID], [Measures].[Parent Member Key], [Measures].[Parent Member Name] } on COLUMNS,   
 [Product].[Product Categories].AllMembers on ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="8262f-234">**範例 2：不受內容影響的內建屬性**</span><span class="sxs-lookup"><span data-stu-id="8262f-234">**Example 2: Non-context-sensitive intrinsic properties**</span></span>  
  
 <span data-ttu-id="8262f-235">下列範例是不受內容影響的內建屬性完整清單。</span><span class="sxs-lookup"><span data-stu-id="8262f-235">The following example is the full list of non-context-sensitive intrinsic properties.</span></span> <span data-ttu-id="8262f-236">在 SSMS 執行查詢後，請按一下個別成員，檢視 [成員屬性] 對話方塊中的屬性。</span><span class="sxs-lookup"><span data-stu-id="8262f-236">After running the query in SSMS, click individual members to view properties in the Member Properties dialog box.</span></span>  
  
```  
SELECT [Measures].[Sales Amount Quota] on COLUMNS,  
[Employee].[Employees].members  
DIMENSION PROPERTIES  
 CATALOG_NAME ,   
 CHILDREN_CARDINALITY ,  
 CUSTOM_ROLLUP ,   
 CUSTOM_ROLLUP_PROPERTIES ,   
 DESCRIPTION ,   
 DIMENSION_UNIQUE_NAME ,   
 HIERARCHY_UNIQUE_NAME ,  
 IS_DATAMEMBER ,   
 IS_PLACEHOLDERMEMBER ,   
 KEY0 ,  
 LCID ,  
 LEVEL_NUMBER ,  
 LEVEL_UNIQUE_NAME ,  
 MEMBER_CAPTION ,   
 MEMBER_KEY ,   
 MEMBER_NAME ,   
 MEMBER_TYPE ,  
 MEMBER_UNIQUE_NAME ,   
 MEMBER_VALUE ,   
 PARENT_COUNT ,   
 PARENT_LEVEL ,   
 PARENT_UNIQUE_NAME ,  
 SKIPPED_LEVELS ,   
 UNARY_OPERATOR ,   
 UNIQUE_NAME    
 ON ROWS  
FROM [Adventure Works]  
WHERE [Employee].[Employee Department].[Department].&[Sales]  
```  
  
 <span data-ttu-id="8262f-237">**範例 3：傳回做為結果集資料的成員屬性**</span><span class="sxs-lookup"><span data-stu-id="8262f-237">**Example 3: Return member properties as data in a result set**</span></span>  
  
 <span data-ttu-id="8262f-238">下列範例會針對指定的地區設定，傳回 Adventure Works Cube 中 Product 維度的產品類別目錄成員的已翻譯標題。</span><span class="sxs-lookup"><span data-stu-id="8262f-238">The following example returns the translated caption for the product category member in the Product dimension in the Adventure Works cube for specified locales.</span></span>  
  
```  
WITH   
MEMBER Measures.CategoryCaption AS Product.Category.CurrentMember.MEMBER_CAPTION  
MEMBER Measures.SpanishCategoryCaption AS Product.Category.CurrentMember.Properties("LCID3082")  
MEMBER Measures.FrenchCategoryCaption AS Product.Category.CurrentMember.Properties("LCID1036")  
SELECT   
{ Measures.CategoryCaption, Measures.SpanishCategoryCaption, Measures.FrenchCategoryCaption } ON 0  
,[Product].[Category].MEMBERS ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="8262f-239">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8262f-239">See Also</span></span>  
 <span data-ttu-id="8262f-240">[PeriodsToDate &#40;MDX&#41;](/sql/mdx/periodstodate-mdx) </span><span class="sxs-lookup"><span data-stu-id="8262f-240">[PeriodsToDate &#40;MDX&#41;](/sql/mdx/periodstodate-mdx) </span></span>  
 <span data-ttu-id="8262f-241">[&#40;MDX&#41;的子系](/sql/mdx/children-mdx) </span><span class="sxs-lookup"><span data-stu-id="8262f-241">[Children &#40;MDX&#41;](/sql/mdx/children-mdx) </span></span>  
 <span data-ttu-id="8262f-242">[Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) </span><span class="sxs-lookup"><span data-stu-id="8262f-242">[Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) </span></span>  
 <span data-ttu-id="8262f-243">[&#40;&#41; &#40;MDX&#41;設定計數](/sql/mdx/count-set-mdx) </span><span class="sxs-lookup"><span data-stu-id="8262f-243">[Count &#40;Set&#41; &#40;MDX&#41;](/sql/mdx/count-set-mdx) </span></span>  
 <span data-ttu-id="8262f-244">[篩選 &#40;MDX&#41;](/sql/mdx/filter-mdx) </span><span class="sxs-lookup"><span data-stu-id="8262f-244">[Filter &#40;MDX&#41;](/sql/mdx/filter-mdx) </span></span>  
 <span data-ttu-id="8262f-245">[AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx) </span><span class="sxs-lookup"><span data-stu-id="8262f-245">[AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx) </span></span>  
 <span data-ttu-id="8262f-246">[DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx) </span><span class="sxs-lookup"><span data-stu-id="8262f-246">[DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx) </span></span>  
 <span data-ttu-id="8262f-247">[MDX&#41;的屬性 &#40;](/sql/mdx/properties-mdx) </span><span class="sxs-lookup"><span data-stu-id="8262f-247">[Properties &#40;MDX&#41;](/sql/mdx/properties-mdx) </span></span>  
 <span data-ttu-id="8262f-248">[PrevMember &#40;MDX&#41;](/sql/mdx/prevmember-mdx) </span><span class="sxs-lookup"><span data-stu-id="8262f-248">[PrevMember &#40;MDX&#41;](/sql/mdx/prevmember-mdx) </span></span>  
 <span data-ttu-id="8262f-249">[使用成員屬性 &#40;MDX&#41;](mdx-member-properties.md) </span><span class="sxs-lookup"><span data-stu-id="8262f-249">[Using Member Properties &#40;MDX&#41;](mdx-member-properties.md) </span></span>  
 [<span data-ttu-id="8262f-250">MDX 函數參考 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="8262f-250">MDX Function Reference &#40;MDX&#41;</span></span>](/sql/mdx/mdx-function-reference-mdx)  
  
  
