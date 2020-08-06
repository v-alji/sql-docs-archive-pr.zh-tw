---
title: 瞭解資料庫架構 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Schema Generation Wizard, database schema
- database schema [Analysis Services]
- relational schema [Analysis Services], database schema
- subject area schema options [Analysis Services]
- staging area schema options [Analysis Services]
- denormalized schemas
ms.assetid: 51e411f9-ee3f-4b92-9833-c2bce8c6b752
author: minewiskan
ms.author: owend
ms.openlocfilehash: 84f44db1b7abca1b8cad45cf5f46fcc0006bd92a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700327"
---
# <a name="understanding-the-database-schemas"></a><span data-ttu-id="c2629-102">了解資料庫結構描述</span><span class="sxs-lookup"><span data-stu-id="c2629-102">Understanding the Database Schemas</span></span>
  <span data-ttu-id="c2629-103">結構描述產生精靈會根據 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]裡的維度和量值群組，產生主題領域資料庫反正規化關聯式結構描述。</span><span class="sxs-lookup"><span data-stu-id="c2629-103">The Schema Generation Wizard generates a denormalized relational schema for the subject area database based on the dimensions and measure groups in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="c2629-104">此精靈會針對每一個維度產生關聯式資料表 (稱為維度資料表)，以便儲存維度資料，也會針對每一個量值群組產生關聯式資料表 (稱為事實資料表)，以便儲存事實資料。</span><span class="sxs-lookup"><span data-stu-id="c2629-104">The wizard generates a relational table for each dimension to store dimension data, which is called a dimension table, and a relational table for each measure group to store fact data, which is called a fact table.</span></span> <span data-ttu-id="c2629-105">精靈產生這些關聯式資料表時，會忽略連結維度、連結量值群組和伺服器時間維度。</span><span class="sxs-lookup"><span data-stu-id="c2629-105">The wizard ignores linked dimensions, linked measure groups, and server time dimensions when it generates these relational tables.</span></span>  
  
## <a name="validation"></a><span data-ttu-id="c2629-106">驗證</span><span class="sxs-lookup"><span data-stu-id="c2629-106">Validation</span></span>  
 <span data-ttu-id="c2629-107">[結構描述產生精靈] 在開始產生基礎關聯式結構描述之前，會先驗證 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Cube 和維度。</span><span class="sxs-lookup"><span data-stu-id="c2629-107">Before it begins to generate the underlying relational schema, the Schema Generation Wizard validates the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cubes and dimensions.</span></span> <span data-ttu-id="c2629-108">如果精靈偵測到錯誤會停止，並會在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的 [工作清單] 視窗報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="c2629-108">If the wizard detects errors, it stops and reports the errors to the Task List window in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="c2629-109">導致無法產生之錯誤的範例包括：</span><span class="sxs-lookup"><span data-stu-id="c2629-109">Examples of errors that prevent generation include the following:</span></span>  
  
-   <span data-ttu-id="c2629-110">擁有一個以上之索引鍵屬性的維度。</span><span class="sxs-lookup"><span data-stu-id="c2629-110">Dimensions that have more than one key attribute.</span></span>  
  
-   <span data-ttu-id="c2629-111">擁有與索引鍵屬性不同之資料類型的父屬性。</span><span class="sxs-lookup"><span data-stu-id="c2629-111">Parent attributes that have different data types than the key attributes.</span></span>  
  
-   <span data-ttu-id="c2629-112">沒有量值的量值群組。</span><span class="sxs-lookup"><span data-stu-id="c2629-112">Measure groups that do not have measures.</span></span>  
  
-   <span data-ttu-id="c2629-113">未正確設定的變質維度或量值。</span><span class="sxs-lookup"><span data-stu-id="c2629-113">Degenerate dimensions or measures that are improperly configured.</span></span>  
  
-   <span data-ttu-id="c2629-114">未正確設定的 Surrogate 索引鍵，例如使用 `ScdOriginalID` 屬性類型的多個屬性，或使用 `ScdOriginalID` (未繫結到使用整數資料類型的資料行) 的屬性。</span><span class="sxs-lookup"><span data-stu-id="c2629-114">Surrogate keys that are improperly configured, such as multiple attributes using the `ScdOriginalID` attribute type or an attribute using the `ScdOriginalID` that is not bound to a column using the integer data type.</span></span>  
  
## <a name="dimension-tables"></a><span data-ttu-id="c2629-115">維度資料表</span><span class="sxs-lookup"><span data-stu-id="c2629-115">Dimension Tables</span></span>  
 <span data-ttu-id="c2629-116">針對每個維度，結構描述產生精靈會產生要包含在主題領域資料庫裡的維度資料表。</span><span class="sxs-lookup"><span data-stu-id="c2629-116">For each dimension, the Schema Generation Wizard generates a dimension table to be included in the subject area database.</span></span> <span data-ttu-id="c2629-117">維度資料表的結構，取決於設計資料表所依據之維度時的選擇。</span><span class="sxs-lookup"><span data-stu-id="c2629-117">The structure of the dimension table depends on the choices made while designing the dimension on which it is based.</span></span>  
  
 <span data-ttu-id="c2629-118">資料行</span><span class="sxs-lookup"><span data-stu-id="c2629-118">Columns</span></span>  
 <span data-ttu-id="c2629-119">針對做為維度資料表基礎之維度中每個屬性的相關聯繫結 (例如每個屬性 (Attribute) 之 `KeyColumns`、`NameColumn`、`ValueColumn`、`CustomRollupColumn`、`CustomRollupPropertiesColumn` 和 `UnaryOperatorColumn` 屬性 (Property) 的繫結)，精靈會產生一個資料行。</span><span class="sxs-lookup"><span data-stu-id="c2629-119">The wizard generates one column for the bindings associated to each attribute in the dimension on which the dimension table is based, such as the bindings for the `KeyColumns`, `NameColumn`, `ValueColumn`, `CustomRollupColumn`, `CustomRollupPropertiesColumn`, and `UnaryOperatorColumn` properties of each attribute.</span></span>  
  
 <span data-ttu-id="c2629-120">關聯性</span><span class="sxs-lookup"><span data-stu-id="c2629-120">Relationships</span></span>  
 <span data-ttu-id="c2629-121">針對每個父屬性的資料行和維度資料表的主索引鍵，精靈會產生兩者之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="c2629-121">The wizard generates a relationship between the column for each parent attribute and the primary key of the dimension table.</span></span>  
  
 <span data-ttu-id="c2629-122">針對定義為 Cube 中之參考維度的其他每個維度資料表，精靈也會產生與主索引鍵的關聯性 (如果適用的話)。</span><span class="sxs-lookup"><span data-stu-id="c2629-122">The wizard also generates a relationship to the primary key in each additional dimension table defined as a referenced dimension in the cube, if applicable.</span></span>  
  
 <span data-ttu-id="c2629-123">條件約束</span><span class="sxs-lookup"><span data-stu-id="c2629-123">Constraints</span></span>  
 <span data-ttu-id="c2629-124">依預設，精靈會根據維度的索引鍵屬性，為每個維度資料表產生一個主索引鍵條件約束。</span><span class="sxs-lookup"><span data-stu-id="c2629-124">The wizard generates a primary key constraint, by default, for each dimension table based on the key attribute of the dimension.</span></span> <span data-ttu-id="c2629-125">如果產生主索引鍵條件約束，依預設會產生另一個名稱資料行。</span><span class="sxs-lookup"><span data-stu-id="c2629-125">If the primary key constraint is generated, a separate name column is generated by default.</span></span> <span data-ttu-id="c2629-126">即使您決定不在資料庫中建立主索引鍵，仍會在資料來源檢視中建立一個邏輯主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c2629-126">A logical primary key is created in the data source view even if you decide not to create the primary key in the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2629-127">如果做為維度資料表之基礎的維度中，指定了一個以上的索引鍵屬性，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c2629-127">An error occurs if more than one key attribute is specified in the dimension on which the dimension table is based.</span></span>  
  
 <span data-ttu-id="c2629-128">翻譯</span><span class="sxs-lookup"><span data-stu-id="c2629-128">Translations</span></span>  
 <span data-ttu-id="c2629-129">精靈會另外產生一個資料表，以保存需要翻譯資料行之任何屬性的已翻譯值。</span><span class="sxs-lookup"><span data-stu-id="c2629-129">The wizard generates a separate table to hold the translated values for any attribute that requires a translation column.</span></span> <span data-ttu-id="c2629-130">精靈也會為每一種必要的語言，建立個別資料行。</span><span class="sxs-lookup"><span data-stu-id="c2629-130">The wizard also creates a separate column for each of the required languages.</span></span>  
  
## <a name="fact-tables"></a><span data-ttu-id="c2629-131">事實資料表</span><span class="sxs-lookup"><span data-stu-id="c2629-131">Fact Tables</span></span>  
 <span data-ttu-id="c2629-132">針對 Cube 中的每個量值群組，結構描述產生精靈會產生要包含在主題領域資料庫裡的一個事實資料表。</span><span class="sxs-lookup"><span data-stu-id="c2629-132">For each measure group in a cube, the Schema Generation Wizard generates a fact table to be included in the subject area database.</span></span> <span data-ttu-id="c2629-133">事實資料表的結構，取決於設計資料表所依據之量值群組時的選擇，以及在量值群組與任何內含維度之間建立的關聯性。</span><span class="sxs-lookup"><span data-stu-id="c2629-133">The structure of the fact table depends on the choices made while designing the measure group on which it is based, and the relationships established between the measure group and any included dimensions.</span></span>  
  
 <span data-ttu-id="c2629-134">資料行</span><span class="sxs-lookup"><span data-stu-id="c2629-134">Columns</span></span>  
 <span data-ttu-id="c2629-135">精靈會為每個量值產生一個資料行，不過使用 `Count` 彙總函式的量值除外。</span><span class="sxs-lookup"><span data-stu-id="c2629-135">The wizard generates one column for each measure, except for measures that use the `Count` aggregation function.</span></span> <span data-ttu-id="c2629-136">這些量值在事實資料表中不需要有對應的資料行。</span><span class="sxs-lookup"><span data-stu-id="c2629-136">Such measures do not require a corresponding column in the fact table.</span></span>  
  
 <span data-ttu-id="c2629-137">精靈也會在量值群組上，針對每個一般維度關聯性的每個資料粒度屬性資料行，產生一個資料行；也會針對與此資料表做為基礎的量值群組，有事實維度關聯性的維度之每個屬性的相關聯繫結，產生一或多個資料行 (如果適用的話)。</span><span class="sxs-lookup"><span data-stu-id="c2629-137">The wizard also generates one column for each granularity attribute column of each regular dimension relationship on the measure group, and one or more columns for the bindings associated to each attribute of a dimension that has a fact dimension relationship to the measure group on which this table is based, if applicable.</span></span>  
  
 <span data-ttu-id="c2629-138">關聯性</span><span class="sxs-lookup"><span data-stu-id="c2629-138">Relationships</span></span>  
 <span data-ttu-id="c2629-139">精靈會為每個一般維度關聯性，產生從事實資料表到維度資料表之資料粒度屬性的一個關聯性。</span><span class="sxs-lookup"><span data-stu-id="c2629-139">The wizard generates one relationship for each regular dimension relationship from the fact table to the dimension table's granularity attribute.</span></span> <span data-ttu-id="c2629-140">如果資料粒度是以維度資料表的索引鍵屬性為基礎，會在資料庫和資料來源檢視中建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="c2629-140">If the granularity is based on the key attribute of the dimension table, the relationship is created in the database and in the data source view.</span></span> <span data-ttu-id="c2629-141">如果資料粒度是以另一個屬性為基礎，則只會在資料來源檢視中建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="c2629-141">If the granularity is based on another attribute, the relationship is created only in the data source view.</span></span>  
  
 <span data-ttu-id="c2629-142">如果您選擇在嚮導中產生索引，則會為每個關聯性資料行產生非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="c2629-142">If you chose to generate indexes in the wizard, a nonclustered index is generated for each of these relationship columns.</span></span>  
  
 <span data-ttu-id="c2629-143">條件約束</span><span class="sxs-lookup"><span data-stu-id="c2629-143">Constraints</span></span>  
 <span data-ttu-id="c2629-144">不會在事實資料表上產生主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c2629-144">Primary keys are not generated on fact tables.</span></span>  
  
 <span data-ttu-id="c2629-145">如果您選擇強制執行參考完整性，適用的話，則會在維度資料表和事實資料表之間產生參考完整性條件約束。</span><span class="sxs-lookup"><span data-stu-id="c2629-145">If you chose to enforce referential integrity, referential integrity constraints are generated between dimension tables and fact tables where applicable.</span></span>  
  
 <span data-ttu-id="c2629-146">翻譯</span><span class="sxs-lookup"><span data-stu-id="c2629-146">Translations</span></span>  
 <span data-ttu-id="c2629-147">針對量值群組中需要翻譯資料行的任何屬性，精靈會產生另一個資料表來保存已翻譯值。</span><span class="sxs-lookup"><span data-stu-id="c2629-147">The wizard generates a separate table to hold the translated values for any property in the measure group that requires a translation column.</span></span> <span data-ttu-id="c2629-148">精靈也會為每一種必要的語言，建立個別資料行。</span><span class="sxs-lookup"><span data-stu-id="c2629-148">The wizard also creates a separate column for each of the required languages.</span></span>  
  
## <a name="data-type-conversion-and-default-lengths"></a><span data-ttu-id="c2629-149">資料類型轉換和預設長度</span><span class="sxs-lookup"><span data-stu-id="c2629-149">Data Type Conversion and Default Lengths</span></span>  
 <span data-ttu-id="c2629-150">在所有情況下，架構產生嚮導都會忽略資料類型，但使用資料類型的資料行除外 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `wchar` 。</span><span class="sxs-lookup"><span data-stu-id="c2629-150">Schema Generation Wizard ignores data types in all cases except for columns that use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `wchar` data type.</span></span> <span data-ttu-id="c2629-151">`wchar` 資料大小會直接翻譯成 `nvarchar` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="c2629-151">The `wchar` data size translates directly to the `nvarchar` data type.</span></span> <span data-ttu-id="c2629-152">但是，如果使用 `wchar` 大小指定的資料行長度大於 4000 個位元組，結構描述產生精靈就會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c2629-152">However, if the specified length of a column using the `wchar` size is larger than 4000 bytes, the Schema Generation Wizard generates an error.</span></span>  
  
 <span data-ttu-id="c2629-153">如果資料項目 (例如屬性的繫結) 沒有指定的長度，則會針對資料行使用下表中所列的預設長度。</span><span class="sxs-lookup"><span data-stu-id="c2629-153">If a data item, such as the binding for an attribute, has no specified length, the default length listed in the following table is used for the column.</span></span>  
  
|<span data-ttu-id="c2629-154">資料項目</span><span class="sxs-lookup"><span data-stu-id="c2629-154">Data item</span></span>|<span data-ttu-id="c2629-155">預設長度 (位元組)</span><span class="sxs-lookup"><span data-stu-id="c2629-155">Default length (bytes)</span></span>|  
|---------------|------------------------------|  
|<span data-ttu-id="c2629-156">KeyColumn</span><span class="sxs-lookup"><span data-stu-id="c2629-156">KeyColumn</span></span>|<span data-ttu-id="c2629-157">50</span><span class="sxs-lookup"><span data-stu-id="c2629-157">50</span></span>|  
|<span data-ttu-id="c2629-158">NameColumn</span><span class="sxs-lookup"><span data-stu-id="c2629-158">NameColumn</span></span>|<span data-ttu-id="c2629-159">50</span><span class="sxs-lookup"><span data-stu-id="c2629-159">50</span></span>|  
|<span data-ttu-id="c2629-160">CustomRollupColumn</span><span class="sxs-lookup"><span data-stu-id="c2629-160">CustomRollupColumn</span></span>|<span data-ttu-id="c2629-161">3000</span><span class="sxs-lookup"><span data-stu-id="c2629-161">3000</span></span>|  
|<span data-ttu-id="c2629-162">CustomRollupPropertiesColumn</span><span class="sxs-lookup"><span data-stu-id="c2629-162">CustomRollupPropertiesColumn</span></span>|<span data-ttu-id="c2629-163">500</span><span class="sxs-lookup"><span data-stu-id="c2629-163">500</span></span>|  
|<span data-ttu-id="c2629-164">UnaryOperatorColumn</span><span class="sxs-lookup"><span data-stu-id="c2629-164">UnaryOperatorColumn</span></span>|<span data-ttu-id="c2629-165">1</span><span class="sxs-lookup"><span data-stu-id="c2629-165">1</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2629-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2629-166">See Also</span></span>  
 <span data-ttu-id="c2629-167">[瞭解累加式產生](understanding-incremental-generation.md) </span><span class="sxs-lookup"><span data-stu-id="c2629-167">[Understanding Incremental Generation](understanding-incremental-generation.md) </span></span>  
 [<span data-ttu-id="c2629-168">管理對資料來源檢視及資料來源所做的變更</span><span class="sxs-lookup"><span data-stu-id="c2629-168">Manage Changes to Data Source Views and Data Sources</span></span>](manage-changes-to-data-source-views-and-data-sources.md)  
  
  
