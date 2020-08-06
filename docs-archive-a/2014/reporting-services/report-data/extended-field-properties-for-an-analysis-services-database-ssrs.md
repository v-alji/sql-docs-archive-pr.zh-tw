---
title: Analysis Services 資料庫的擴充欄位屬性 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1d7d87e2-bf0d-4ebb-a287-80b5a967a3f2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f5c0a8ebcb739cdf6b3fa34acf467309e7854db1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710234"
---
# <a name="extended-field-properties-for-an-analysis-services-database-ssrs"></a><span data-ttu-id="720fd-102">Analysis Services 資料庫的擴充欄位屬性 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="720fd-102">Extended Field Properties for an Analysis Services Database (SSRS)</span></span>
  <span data-ttu-id="720fd-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料處理延伸模組支援擴充欄位屬性。</span><span class="sxs-lookup"><span data-stu-id="720fd-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data processing extension supports extended field properties.</span></span> <span data-ttu-id="720fd-104">擴充欄位屬性是除了欄位屬性 `Value` 和 `IsMissing` 之外，資料來源可用而且資料處理延伸模組支援的屬性。</span><span class="sxs-lookup"><span data-stu-id="720fd-104">Extended field properties are properties in addition to the field properties `Value` and `IsMissing` that are available on the data source and supported by the data processing extension.</span></span> <span data-ttu-id="720fd-105">在 [報表資料] 窗格中，報表資料集的欄位集合中不會顯示擴充屬性。</span><span class="sxs-lookup"><span data-stu-id="720fd-105">Extended properties do not appear in the Report Data pane as part of the field collection for a report dataset.</span></span> <span data-ttu-id="720fd-106">您可以在報表中包含擴充欄位屬性值，方法是撰寫使用內建集合依名稱指定的運算式 `Fields` 。</span><span class="sxs-lookup"><span data-stu-id="720fd-106">You can include extended field property values in your report by writing expressions that specify them by name using the built-in `Fields` collection.</span></span>  
  
 <span data-ttu-id="720fd-107">擴充屬性包括預先定義的屬性和自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="720fd-107">Extended properties include predefined properties and custom properties.</span></span> <span data-ttu-id="720fd-108">預先定義的屬性是多個資料來源共通的屬性，這類屬性會對應到特定欄位屬性名稱，而且可透過內建的 `Fields` 集合按照名稱存取。</span><span class="sxs-lookup"><span data-stu-id="720fd-108">Predefined properties are properties common to multiple data sources that are mapped to specific field property names and can be accessed through the built-in `Fields` collection by name.</span></span> <span data-ttu-id="720fd-109">自訂屬性則是各個資料提供者專有的屬性，這類屬性可透過內建的 `Fields` 集合存取，但只能透過使用擴充屬性名稱做為字串的語法。</span><span class="sxs-lookup"><span data-stu-id="720fd-109">Custom properties are specific to each data provider and can be accessed through the built-in `Fields` collection only through syntax using the extended property name as a string.</span></span>  
  
 <span data-ttu-id="720fd-110">當您使用圖形模式的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] MDX 查詢設計工具定義查詢時，預先定義的資料格屬性和維度屬性集合就會自動加入至 MDX 查詢中。</span><span class="sxs-lookup"><span data-stu-id="720fd-110">When you use the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] MDX query designer in graphical mode to define your query, a predefined set of cell properties and dimension properties are automatically added to the MDX query.</span></span> <span data-ttu-id="720fd-111">您只可以使用明確列在您報表的 MDX 查詢中的擴充屬性。</span><span class="sxs-lookup"><span data-stu-id="720fd-111">You can only use extended properties that are specifically listed in the MDX query in your report.</span></span> <span data-ttu-id="720fd-112">依報表的不同，您或許想修改預設的 MDX 命令文字，藉此包括 Cube 中定義的其他維度或自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="720fd-112">Depending on your report, you may want to modify the default MDX command text to include other dimension or custom properties defined in the cube.</span></span> <span data-ttu-id="720fd-113">如需 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料來源中可用之擴充欄位的詳細資訊，請參閱[建立和使用屬性值 &#40;MDX&#41;](../../analysis-services/creating-and-using-property-values-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="720fd-113">For more information about extended fields available in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data sources, see [Creating and Using Property Values &#40;MDX&#41;](../../analysis-services/creating-and-using-property-values-mdx.md).</span></span>  
  
## <a name="working-with-field-properties-in-a-report"></a><span data-ttu-id="720fd-114">使用報表中的欄位屬性</span><span class="sxs-lookup"><span data-stu-id="720fd-114">Working with Field Properties in a Report</span></span>  
 <span data-ttu-id="720fd-115">擴充欄位屬性包含預先定義的屬性和資料提供者特有的屬性。</span><span class="sxs-lookup"><span data-stu-id="720fd-115">Extended field properties include predefined properties and data provider-specific properties.</span></span> <span data-ttu-id="720fd-116">即使欄位屬性位於針對資料集所建立的查詢中，還是不會與欄位清單一起出現在 **[報表資料]** 窗格內，因此您無法將欄位屬性拖曳到報表設計介面上。</span><span class="sxs-lookup"><span data-stu-id="720fd-116">Field properties do not appear with the field list in the **Report Data** pane, even though they are in the query built for a dataset; therefore, you cannot drag field properties onto your report design surface.</span></span> <span data-ttu-id="720fd-117">不過，您必須將欄位拖曳到報表上，然後將該欄位的 `Value` 屬性變更為您要使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="720fd-117">Instead, you must drag the field onto the report and then change the `Value` property of the field to the property that you want to use.</span></span> <span data-ttu-id="720fd-118">例如，如果 Cube 中的資料格資料已經格式化，您可以利用以下運算式來使用 FormattedValue 欄位屬性： `=Fields!FieldName.FormattedValue`。</span><span class="sxs-lookup"><span data-stu-id="720fd-118">For example, if the cell data from a cube has already been formatted, you can use the FormattedValue field property by using the following expression: `=Fields!FieldName.FormattedValue`.</span></span>  
  
 <span data-ttu-id="720fd-119">若要參考未預先定義的擴充屬性，請在運算式中使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="720fd-119">To refer to an extended property that is not predefined, use the following syntax in an expression:</span></span>  
  
-   <span data-ttu-id="720fd-120">*Fields!FieldName("PropertyName")*</span><span class="sxs-lookup"><span data-stu-id="720fd-120">*Fields!FieldName("PropertyName")*</span></span>  
  
## <a name="predefined-field-properties"></a><span data-ttu-id="720fd-121">預先定義的欄位屬性</span><span class="sxs-lookup"><span data-stu-id="720fd-121">Predefined Field Properties</span></span>  
 <span data-ttu-id="720fd-122">在大多數情況下，預先定義的欄位屬性會套用至量值、層級或維度。</span><span class="sxs-lookup"><span data-stu-id="720fd-122">In most cases, predefined field properties apply to measures, levels, or dimensions.</span></span> <span data-ttu-id="720fd-123">預先定義的欄位屬性必須有儲存在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料來源中的對應值。</span><span class="sxs-lookup"><span data-stu-id="720fd-123">A predefined field property must have a corresponding value stored in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="720fd-124">如果值不存在，或者 (例如) 您在層級上指定了僅限量值的欄位屬性，則屬性會傳回 Null 值。</span><span class="sxs-lookup"><span data-stu-id="720fd-124">If a value does not exist, or if you specify a measure-only field property on a level (for example), the property returns a null value.</span></span>  
  
 <span data-ttu-id="720fd-125">您可以使用下列任一語法，從運算式參考預先定義的屬性：</span><span class="sxs-lookup"><span data-stu-id="720fd-125">You can use either of the following syntaxes to refer to a predefined property from an expression:</span></span>  
  
-   <span data-ttu-id="720fd-126">*Fields!FieldName.PropertyName*</span><span class="sxs-lookup"><span data-stu-id="720fd-126">*Fields!FieldName.PropertyName*</span></span>  
  
-   <span data-ttu-id="720fd-127">*Fields!FieldName("PropertyName")*</span><span class="sxs-lookup"><span data-stu-id="720fd-127">*Fields!FieldName("PropertyName")*</span></span>  
  
 <span data-ttu-id="720fd-128">下表提供您可以使用之預先定義的欄位屬性清單。</span><span class="sxs-lookup"><span data-stu-id="720fd-128">The following table provides a list of predefined field properties that you can use.</span></span>  
  
|<span data-ttu-id="720fd-129">**屬性**</span><span class="sxs-lookup"><span data-stu-id="720fd-129">**Property**</span></span>|<span data-ttu-id="720fd-130">**型別**</span><span class="sxs-lookup"><span data-stu-id="720fd-130">**Type**</span></span>|<span data-ttu-id="720fd-131">**描述或預期的值**</span><span class="sxs-lookup"><span data-stu-id="720fd-131">**Description or expected value**</span></span>|  
|------------------|--------------|---------------------------------------|  
|`Value`|`Object`|<span data-ttu-id="720fd-132">指定欄位的資料值。</span><span class="sxs-lookup"><span data-stu-id="720fd-132">Specifies the data value of the field.</span></span>|  
|`IsMissing`|`Boolean`|<span data-ttu-id="720fd-133">指出在產生的資料集裡是否有找到欄位。</span><span class="sxs-lookup"><span data-stu-id="720fd-133">Indicates whether the field was found in the resulting data set.</span></span>|  
|`UniqueName`|`String`|<span data-ttu-id="720fd-134">傳回層級的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="720fd-134">Returns the fully qualified name of a level.</span></span> <span data-ttu-id="720fd-135">例如，員工的 `UniqueName` 值可能是 *[employee]. [員工部門]。[部門]. & [Sales]. & [北美銷售經理]。 & [272]*。</span><span class="sxs-lookup"><span data-stu-id="720fd-135">For example, the `UniqueName` value for an employee might be *[Employee].[Employee Department].[Department].&[Sales].&[North American Sales Manager].&[272]*.</span></span>|  
|`BackgroundColor`|`String`|<span data-ttu-id="720fd-136">傳回資料庫中為欄位定義的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="720fd-136">Returns the background color defined in the database for the field.</span></span>|  
|`Color`|`String`|<span data-ttu-id="720fd-137">傳回資料庫中為項目定義的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="720fd-137">Returns the foreground color defined in the database for the item.</span></span>|  
|`FontFamily`|`String`|<span data-ttu-id="720fd-138">傳回資料庫中為項目定義之字型的名稱。</span><span class="sxs-lookup"><span data-stu-id="720fd-138">Returns the name of the font defined in the database for the item.</span></span>|  
|`FontSize`|`String`|<span data-ttu-id="720fd-139">傳回資料庫中為項目定義之字型的點數大小。</span><span class="sxs-lookup"><span data-stu-id="720fd-139">Returns the point size of the font defined in the database for the item.</span></span>|  
|`FontWeight`|`String`|<span data-ttu-id="720fd-140">傳回資料庫中為項目定義之字型的粗細。</span><span class="sxs-lookup"><span data-stu-id="720fd-140">Returns the weight of the font defined in the database for the item.</span></span>|  
|`FontStyle`|`String`|<span data-ttu-id="720fd-141">傳回資料庫中為項目定義之字型的樣式。</span><span class="sxs-lookup"><span data-stu-id="720fd-141">Returns the style of the font defined in the database for the item.</span></span>|  
|`TextDecoration`|`String`|<span data-ttu-id="720fd-142">傳回資料庫中為項目定義的特殊文字格式。</span><span class="sxs-lookup"><span data-stu-id="720fd-142">Returns special text formatting defined in the database for the item.</span></span>|  
|`FormattedValue`|`String`|<span data-ttu-id="720fd-143">傳回量值或關鍵數值的格式化值。</span><span class="sxs-lookup"><span data-stu-id="720fd-143">Returns a formatted value for a measure or key figure.</span></span> <span data-ttu-id="720fd-144">例如， `FormattedValue` **Sales 金額配額**的屬性會傳回貨幣格式，例如 $1124400.00。</span><span class="sxs-lookup"><span data-stu-id="720fd-144">For example, the `FormattedValue` property for **Sales Amount Quota** returns a currency format like $1,124,400.00.</span></span>|  
|`Key`|`Object`|<span data-ttu-id="720fd-145">傳回層級的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="720fd-145">Returns the key for a level.</span></span>|  
|`LevelNumber`|`Integer`|<span data-ttu-id="720fd-146">如果是父子式階層，則會傳回層級或維度編號。</span><span class="sxs-lookup"><span data-stu-id="720fd-146">For parent-child hierarchies, returns the level or dimension number.</span></span>|  
|`ParentUniqueName`|`String`|<span data-ttu-id="720fd-147">如果是父子式階層，會傳回父層級的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="720fd-147">For parent-child hierarchies, returns a fully qualified name of the parent level.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="720fd-148">當報表為其資料集執行及擷取資料時，只有在資料來源 (例如 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Cube) 提供這些值的情況下，這些擴充欄位屬性的值才會存在。</span><span class="sxs-lookup"><span data-stu-id="720fd-148">Values exist for these extended field properties only if the data source (for example, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cube) provides these values when your report runs and retrieves the data for its datasets.</span></span> <span data-ttu-id="720fd-149">這樣，您就可以利用以下章節所述的語法，從任何運算式參考那些欄位屬性值。</span><span class="sxs-lookup"><span data-stu-id="720fd-149">You can then refer to those field property values from any expression using the syntax described in the following section.</span></span> <span data-ttu-id="720fd-150">不過，由於這些欄位是此資料提供者的特定欄位，因此，您對這些值所作的變更不會隨同報表定義一併儲存。</span><span class="sxs-lookup"><span data-stu-id="720fd-150">However, because these fields are specific to this data provider, changes that you make to these values are not saved with the report definition.</span></span>  
  
### <a name="example-extended-properties"></a><span data-ttu-id="720fd-151">擴充屬性範例</span><span class="sxs-lookup"><span data-stu-id="720fd-151">Example Extended Properties</span></span>  
 <span data-ttu-id="720fd-152">為了示範說明擴充屬性，下列 MDX 查詢和結果集之中包含從為 Cube 定義的維度屬性中取得的數個成員屬性。</span><span class="sxs-lookup"><span data-stu-id="720fd-152">To illustrate extended properties, the following MDX query and result set include several member properties available from a dimension attribute defined for a cube.</span></span> <span data-ttu-id="720fd-153">這些成員屬性包括 MEMBER_CAPTION、UNIQUENAME、Properties("Day Name")、MEMBER_VALUE、PARENT_UNIQUE_NAME 和 MEMBER_KEY。</span><span class="sxs-lookup"><span data-stu-id="720fd-153">The member properties included are MEMBER_CAPTION, UNIQUENAME, Properties("Day Name"), MEMBER_VALUE, PARENT_UNIQUE_NAME, and MEMBER_KEY.</span></span>  
  
 <span data-ttu-id="720fd-154">這個 MDX 查詢會針對 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 範例資料庫中所包含之 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW 資料庫內的 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] Cube 來執行。</span><span class="sxs-lookup"><span data-stu-id="720fd-154">This MDX query runs against the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] cube in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW database, included with the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample databases.</span></span>  
  
```  
WITH MEMBER [Measures].[DateCaption]   
      AS '[Date].[Date].CURRENTMEMBER.MEMBER_CAPTION'   
   MEMBER [Measures].[DateUniqueName]   
      AS '[Date].[Date].CURRENTMEMBER.UNIQUENAME'   
   MEMBER [Measures].[DateDayName]   
      AS '[Date].[Date].Properties("Day Name")'   
   MEMBER [Measures].[DateValueinOriginalDatatype]   
      AS '[Date].[Date].CURRENTMEMBER.MEMBER_VALUE'   
   MEMBER [Measures].[DateParentUniqueName]   
      AS '[Date].[Date].CURRENTMEMBER.PARENT_UNIQUE_NAME'   
   MEMBER [Measures].[DateMemberKeyinOriginalDatatype]   
      AS '[Date].[Date].CURRENTMEMBER.MEMBER_KEY'   
SELECT {  
   [Measures].[DateCaption],   
   [Measures].[DateUniqueName],   
   [Measures].[DateDayName],   
   [Measures].[DateValueinOriginalDatatype],  
   [Measures].[DateParentUniqueName],  
   [Measures].[DateMemberKeyinOriginalDatatype]  
   } ON COLUMNS , [Date].[Date].ALLMEMBERS ON ROWS   
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="720fd-155">在 MDX 查詢窗格中執行這個查詢時，結果集會包含 1158 個資料列，</span><span class="sxs-lookup"><span data-stu-id="720fd-155">When you run this query in an MDX query pane, you get a result set with 1158 rows.</span></span> <span data-ttu-id="720fd-156">前四個資料列如下表所示。</span><span class="sxs-lookup"><span data-stu-id="720fd-156">The first four rows are shown in the following table.</span></span>  
  
|<span data-ttu-id="720fd-157">DateCaption</span><span class="sxs-lookup"><span data-stu-id="720fd-157">DateCaption</span></span>|<span data-ttu-id="720fd-158">DateUniqueName</span><span class="sxs-lookup"><span data-stu-id="720fd-158">DateUniqueName</span></span>|<span data-ttu-id="720fd-159">DateDayName</span><span class="sxs-lookup"><span data-stu-id="720fd-159">DateDayName</span></span>|<span data-ttu-id="720fd-160">DateValueinOriginalDatatype</span><span class="sxs-lookup"><span data-stu-id="720fd-160">DateValueinOriginalDatatype</span></span>|<span data-ttu-id="720fd-161">DateParentUniqueName</span><span class="sxs-lookup"><span data-stu-id="720fd-161">DateParentUniqueName</span></span>|<span data-ttu-id="720fd-162">DateMemberKeyinOriginalDatatype</span><span class="sxs-lookup"><span data-stu-id="720fd-162">DateMemberKeyinOriginalDatatype</span></span>|  
|-----------------|--------------------|-----------------|---------------------------------|--------------------------|-------------------------------------|  
|<span data-ttu-id="720fd-163">All Periods</span><span class="sxs-lookup"><span data-stu-id="720fd-163">All Periods</span></span>|<span data-ttu-id="720fd-164">[Date].[Date].[All Periods]</span><span class="sxs-lookup"><span data-stu-id="720fd-164">[Date].[Date].[All Periods]</span></span>|<span data-ttu-id="720fd-165">(Null)</span><span class="sxs-lookup"><span data-stu-id="720fd-165">(null)</span></span>|<span data-ttu-id="720fd-166">(Null)</span><span class="sxs-lookup"><span data-stu-id="720fd-166">(null)</span></span>|<span data-ttu-id="720fd-167">(Null)</span><span class="sxs-lookup"><span data-stu-id="720fd-167">(null)</span></span>|<span data-ttu-id="720fd-168">0</span><span class="sxs-lookup"><span data-stu-id="720fd-168">0</span></span>|  
|<span data-ttu-id="720fd-169">1-Jul-01</span><span class="sxs-lookup"><span data-stu-id="720fd-169">1-Jul-01</span></span>|<span data-ttu-id="720fd-170">[Date].[Date].&[1]</span><span class="sxs-lookup"><span data-stu-id="720fd-170">[Date].[Date].&[1]</span></span>|<span data-ttu-id="720fd-171">星期日</span><span class="sxs-lookup"><span data-stu-id="720fd-171">Sunday</span></span>|<span data-ttu-id="720fd-172">7/1/2001</span><span class="sxs-lookup"><span data-stu-id="720fd-172">7/1/2001</span></span>|<span data-ttu-id="720fd-173">[Date].[Date].[All Periods]</span><span class="sxs-lookup"><span data-stu-id="720fd-173">[Date].[Date].[All Periods]</span></span>|<span data-ttu-id="720fd-174">1</span><span class="sxs-lookup"><span data-stu-id="720fd-174">1</span></span>|  
|<span data-ttu-id="720fd-175">2-Jul-01</span><span class="sxs-lookup"><span data-stu-id="720fd-175">2-Jul-01</span></span>|<span data-ttu-id="720fd-176">[Date].[Date].&[2]</span><span class="sxs-lookup"><span data-stu-id="720fd-176">[Date].[Date].&[2]</span></span>|<span data-ttu-id="720fd-177">星期一</span><span class="sxs-lookup"><span data-stu-id="720fd-177">Monday</span></span>|<span data-ttu-id="720fd-178">7/2/2001</span><span class="sxs-lookup"><span data-stu-id="720fd-178">7/2/2001</span></span>|<span data-ttu-id="720fd-179">[Date].[Date].[All Periods]</span><span class="sxs-lookup"><span data-stu-id="720fd-179">[Date].[Date].[All Periods]</span></span>|<span data-ttu-id="720fd-180">2</span><span class="sxs-lookup"><span data-stu-id="720fd-180">2</span></span>|  
|<span data-ttu-id="720fd-181">3-Jul-01</span><span class="sxs-lookup"><span data-stu-id="720fd-181">3-Jul-01</span></span>|<span data-ttu-id="720fd-182">[Date].[Date].&[3]</span><span class="sxs-lookup"><span data-stu-id="720fd-182">[Date].[Date].&[3]</span></span>|<span data-ttu-id="720fd-183">星期二</span><span class="sxs-lookup"><span data-stu-id="720fd-183">Tuesday</span></span>|<span data-ttu-id="720fd-184">7/3/2001</span><span class="sxs-lookup"><span data-stu-id="720fd-184">7/3/2001</span></span>|<span data-ttu-id="720fd-185">[Date].[Date].[All Periods]</span><span class="sxs-lookup"><span data-stu-id="720fd-185">[Date].[Date].[All Periods]</span></span>|<span data-ttu-id="720fd-186">3</span><span class="sxs-lookup"><span data-stu-id="720fd-186">3</span></span>|  
  
 <span data-ttu-id="720fd-187">在圖形模式 MDX 查詢設計工具中所建置的預設 MDX 查詢只包含維度屬性的 MEMBER_CAPTION 和 UNIQUENAME。</span><span class="sxs-lookup"><span data-stu-id="720fd-187">Default MDX queries built using the MDX Query Designer in graphical mode only include MEMBER_CAPTION and UNIQUENAME for dimension properties.</span></span> <span data-ttu-id="720fd-188">依預設，這些值一定是 `String` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="720fd-188">By default, these values always are data type `String`.</span></span>  
  
 <span data-ttu-id="720fd-189">如果成員屬性必須保持原始資料類型，您可以在以文字為基礎的查詢設計工具中修改預設的 MDX 陳述式，以包含另一個屬性 MEMBER_VALUE。</span><span class="sxs-lookup"><span data-stu-id="720fd-189">If you need a member property in its original data type, you can include an additional property MEMBER_VALUE by modifying the default MDX statement in the text-based query designer.</span></span> <span data-ttu-id="720fd-190">在下列簡單的 MDX 陳述式中，已在要擷取的維度屬性清單中加入 MEMBER_VALUE。</span><span class="sxs-lookup"><span data-stu-id="720fd-190">In the following simple MDX statement, MEMBER_VALUE has been added to the list of dimension properties to retrieve.</span></span>  
  
```  
SELECT NON EMPTY {[Measures].[Order Count]} ON COLUMNS,   
NON EMPTY { ([Date].[Month of Year].[Month of Year] ) }   
DIMENSION PROPERTIES   
   MEMBER_CAPTION, MEMBER_UNIQUE_NAME, MEMBER_VALUE ON ROWS   
FROM [Adventure Works]  
CELL PROPERTIES   
   VALUE, BACK_COLOR, FORE_COLOR,   
   FORMATTED_VALUE, FORMAT_STRING,   
   FONT_NAME, FONT_SIZE, FONT_FLAGS  
```  
  
 <span data-ttu-id="720fd-191">MDX 結果窗格中前四個結果資料列顯示於下表中。</span><span class="sxs-lookup"><span data-stu-id="720fd-191">The first four rows of the result in the MDX Results pane appear in the following table.</span></span>  
  
|<span data-ttu-id="720fd-192">Month of Year</span><span class="sxs-lookup"><span data-stu-id="720fd-192">Month of Year</span></span>|<span data-ttu-id="720fd-193">Order Count</span><span class="sxs-lookup"><span data-stu-id="720fd-193">Order Count</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="720fd-194">一月</span><span class="sxs-lookup"><span data-stu-id="720fd-194">January</span></span>|<span data-ttu-id="720fd-195">2,481</span><span class="sxs-lookup"><span data-stu-id="720fd-195">2,481</span></span>|  
|<span data-ttu-id="720fd-196">二月</span><span class="sxs-lookup"><span data-stu-id="720fd-196">February</span></span>|<span data-ttu-id="720fd-197">2,684</span><span class="sxs-lookup"><span data-stu-id="720fd-197">2,684</span></span>|  
|<span data-ttu-id="720fd-198">3 月</span><span class="sxs-lookup"><span data-stu-id="720fd-198">March</span></span>|<span data-ttu-id="720fd-199">2,749</span><span class="sxs-lookup"><span data-stu-id="720fd-199">2,749</span></span>|  
|<span data-ttu-id="720fd-200">四月</span><span class="sxs-lookup"><span data-stu-id="720fd-200">April</span></span>|<span data-ttu-id="720fd-201">2,739</span><span class="sxs-lookup"><span data-stu-id="720fd-201">2,739</span></span>|  
  
 <span data-ttu-id="720fd-202">這些屬性雖然是 MDX 選取陳述式的一部分，但是卻不會出現在結果集資料行中，</span><span class="sxs-lookup"><span data-stu-id="720fd-202">Even though the properties are part of the MDX select statement, they do not appear in the result set columns.</span></span> <span data-ttu-id="720fd-203">然而，報表還是可以透過使用擴充屬性功能來使用這些資料。</span><span class="sxs-lookup"><span data-stu-id="720fd-203">Nevertheless, the data is available for a report by using the extended properties feature.</span></span> <span data-ttu-id="720fd-204">在的 [MDX 查詢結果] 窗格中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ，您可以按兩下資料格，並查看資料格屬性值（如果 cube 中已設定的話）。</span><span class="sxs-lookup"><span data-stu-id="720fd-204">In an MDX query result pane in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can double-click on the cell and see the cell property values if they are set in the cube.</span></span> <span data-ttu-id="720fd-205">如果按兩下包含 1,379 的第一個 [Order Count] 資料格，就會出現內含下列資料格屬性的快顯視窗：</span><span class="sxs-lookup"><span data-stu-id="720fd-205">If you double-click on the first Order Count cell that contains 1,379, you will see a pop-up window with the following cell properties:</span></span>  
  
|<span data-ttu-id="720fd-206">屬性</span><span class="sxs-lookup"><span data-stu-id="720fd-206">Property</span></span>|<span data-ttu-id="720fd-207">值</span><span class="sxs-lookup"><span data-stu-id="720fd-207">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="720fd-208">CellOrdinal</span><span class="sxs-lookup"><span data-stu-id="720fd-208">CellOrdinal</span></span>|<span data-ttu-id="720fd-209">0</span><span class="sxs-lookup"><span data-stu-id="720fd-209">0</span></span>|  
|<span data-ttu-id="720fd-210">值</span><span class="sxs-lookup"><span data-stu-id="720fd-210">VALUE</span></span>|<span data-ttu-id="720fd-211">2481</span><span class="sxs-lookup"><span data-stu-id="720fd-211">2481</span></span>|  
|<span data-ttu-id="720fd-212">BACK_COLOR</span><span class="sxs-lookup"><span data-stu-id="720fd-212">BACK_COLOR</span></span>|<span data-ttu-id="720fd-213">(Null)</span><span class="sxs-lookup"><span data-stu-id="720fd-213">(null)</span></span>|  
|<span data-ttu-id="720fd-214">FORE_COLOR</span><span class="sxs-lookup"><span data-stu-id="720fd-214">FORE_COLOR</span></span>|<span data-ttu-id="720fd-215">(Null)</span><span class="sxs-lookup"><span data-stu-id="720fd-215">(null)</span></span>|  
|<span data-ttu-id="720fd-216">FORMATTED_VALUE</span><span class="sxs-lookup"><span data-stu-id="720fd-216">FORMATTED_VALUE</span></span>|<span data-ttu-id="720fd-217">2,481</span><span class="sxs-lookup"><span data-stu-id="720fd-217">2,481</span></span>|  
|<span data-ttu-id="720fd-218">FORMAT_STRING</span><span class="sxs-lookup"><span data-stu-id="720fd-218">FORMAT_STRING</span></span>|<span data-ttu-id="720fd-219">#,#</span><span class="sxs-lookup"><span data-stu-id="720fd-219">#,#</span></span>|  
|<span data-ttu-id="720fd-220">FONT_NAME</span><span class="sxs-lookup"><span data-stu-id="720fd-220">FONT_NAME</span></span>|<span data-ttu-id="720fd-221">(Null)</span><span class="sxs-lookup"><span data-stu-id="720fd-221">(null)</span></span>|  
|<span data-ttu-id="720fd-222">FONT_SIZE</span><span class="sxs-lookup"><span data-stu-id="720fd-222">FONT_SIZE</span></span>|<span data-ttu-id="720fd-223">(Null)</span><span class="sxs-lookup"><span data-stu-id="720fd-223">(null)</span></span>|  
|<span data-ttu-id="720fd-224">FONT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="720fd-224">FONT_FLAGS</span></span>|<span data-ttu-id="720fd-225">(Null)</span><span class="sxs-lookup"><span data-stu-id="720fd-225">(null)</span></span>|  
  
 <span data-ttu-id="720fd-226">如果用這個查詢建立報表資料集，並將資料集繫結至資料表，就可以看到欄位的預設 VALUE 屬性，例如 `=Fields!Month_of_Year!Value`。</span><span class="sxs-lookup"><span data-stu-id="720fd-226">If you create a report dataset with this query and bind the dataset to a table, you can see the default VALUE property for a field, for example, `=Fields!Month_of_Year!Value`.</span></span> <span data-ttu-id="720fd-227">如果將這個運算式設定為資料表的排序運算式，結果資料表將會依月份的字母順序排序，因為 Value 欄位會使用 `String` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="720fd-227">If you set this expression as the sort expression for the table, your results will be to sort the table alphabetically by month because the Value field uses a `String` data type.</span></span> <span data-ttu-id="720fd-228">若要將資料表的排序順序設為依月份在當年出現的順序，一月最前，十二月最後，則請使用下列運算式：</span><span class="sxs-lookup"><span data-stu-id="720fd-228">To sort the table in so that the months are in the order they occur in the year with January first and December last, use the following expression:</span></span>  
  
```  
=Fields!Month_of_Year("MEMBER_VALUE")  
```  
  
 <span data-ttu-id="720fd-229">這會將欄位值依其在資料來源中的原始整數資料類型排序。</span><span class="sxs-lookup"><span data-stu-id="720fd-229">This sorts the value of the field in its original integer data type from the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="720fd-230">另請參閱</span><span class="sxs-lookup"><span data-stu-id="720fd-230">See Also</span></span>  
 <span data-ttu-id="720fd-231">[運算式 &#40;報表產生器及 SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="720fd-231">[Expressions &#40;Report Builder and SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="720fd-232">[運算式中的內建集合 &#40;報表產生器和 SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="720fd-232">[Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md) </span></span>  
 [<span data-ttu-id="720fd-233">資料集欄位集合 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="720fd-233">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
  
  
