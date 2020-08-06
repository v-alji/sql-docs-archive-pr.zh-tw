---
title: ASSL XML 慣例 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- whitespace [Analysis Services Scripting Language]
- trailing whitespace
- XSD data types [Analysis Services Scripting Language]
- inheritance [Analysis Services Scripting Language]
- cardinality [Analysis Services Scripting Language]
- white space [Analysis Services Scripting Language]
- ASSL, XML conventions
- defaults [Analysis Services Scripting Language]
- leading whitespace
- Analysis Services Scripting Language, XML conventions
- XML [Analysis Services Scripting Language]
- hierarchies [Analysis Services Scripting Language]
- inherited defaults [Analysis Services Scripting Language]
ms.assetid: bce4edad-4420-41ce-9672-8c00c5c0dec6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b70742b07fd6450b01cf205147a05f40c4b6121
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705557"
---
# <a name="assl-xml-conventions"></a><span data-ttu-id="3f8bc-102">ASSL XML 慣例</span><span class="sxs-lookup"><span data-stu-id="3f8bc-102">ASSL XML Conventions</span></span>
  <span data-ttu-id="3f8bc-103">Analysis Services 指令碼語言 (ASSL) 將物件階層以一組元素類型來表示，每個元素類型都定義了它們可以包含的子系元素。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-103">Analysis Services Scripting Language (ASSL) represents the hierarchy of objects as a set of element types, each of which defines the child elements they can contain.</span></span>  
  
 <span data-ttu-id="3f8bc-104">為了表示物件階層，ASSL 使用下列 XML 慣例：</span><span class="sxs-lookup"><span data-stu-id="3f8bc-104">To represent the object hierarchy, ASSL uses the following XML conventions:</span></span>  
  
-   <span data-ttu-id="3f8bc-105">所有物件和屬性都是以元素表示，但標準 XML 屬性（例如 ' XML： lang '）除外。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-105">All objects and properties are represented as elements, except for standard XML attributes such as 'xml:lang'.</span></span>  
  
-   <span data-ttu-id="3f8bc-106">元素名稱與列舉值都會遵循 Microsoft .NET Framework 所採用之 Pascal 大小寫 (不使用底線) 的命名慣例。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-106">Both element names and enumeration values follow the Microsoft .NET Framework naming convention of Pascal casing with no underscores.</span></span>  
  
-   <span data-ttu-id="3f8bc-107">所有值的大小寫都會保留。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-107">The case of all values is preserved.</span></span> <span data-ttu-id="3f8bc-108">列舉值也會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-108">Values for enumerations are also case-sensitive.</span></span>  
  
 <span data-ttu-id="3f8bc-109">除了這個慣例清單以外，Analysis Services 也會遵循有關基數、繼承、空白、資料類型以及預設值的某些慣例。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-109">In addition to this list of conventions, Analysis Services also follows certain conventions regarding cardinality, inheritance, whitespace, data types, and default values.</span></span>  
  
## <a name="cardinality"></a><span data-ttu-id="3f8bc-110">基數</span><span class="sxs-lookup"><span data-stu-id="3f8bc-110">Cardinality</span></span>  
 <span data-ttu-id="3f8bc-111">當元素具有大於 1 的基數時，就會有封裝此元素的 XML 元素集合。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-111">When an element has a cardinality that is greater than 1, there is an XML element collection that encapsulates this element.</span></span> <span data-ttu-id="3f8bc-112">集合名稱會使用包含在集合中的複數形式之元素。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-112">The name of collection uses the plural form of the elements contained in the collection.</span></span> <span data-ttu-id="3f8bc-113">例如，下列 XML 區段代表 `Dimensions` 元素中的 `Database` 集合：</span><span class="sxs-lookup"><span data-stu-id="3f8bc-113">For example, the following XML fragment represents the `Dimensions` collection within a `Database` element:</span></span>  
  
 `<Database>`  
  
 `...`  
  
 `<Dimensions>`  
  
 `<Dimension>`  
  
 `...`  
  
 `</Dimension>`  
  
 `<Dimension>`  
  
 `...`  
  
 `</Dimension>`  
  
 `</Dimensions>`  
  
 `</Database>`  
  
 ``  
  
 <span data-ttu-id="3f8bc-114">元素出現的順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-114">The order in which elements appear is unimportant.</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="3f8bc-115">繼承</span><span class="sxs-lookup"><span data-stu-id="3f8bc-115">Inheritance</span></span>  
 <span data-ttu-id="3f8bc-116">當有不同的物件具有重疊但非常不一樣的屬性集合時，就會使用繼承。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-116">Inheritance is used when there are distinct objects that have overlapping but significantly different sets of properties.</span></span> <span data-ttu-id="3f8bc-117">像這類重疊但是相異的物件為虛擬 Cube、連結 Cube 以及一般 Cube。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-117">Examples of such overlapping but distinct objects are virtual cubes, linked cubes, and regular cubes.</span></span> <span data-ttu-id="3f8bc-118">對於重疊但是相異的物件，Analysis Services 會使用 XML 執行個體命名空間的標準 `type` 屬性來指出繼承。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-118">For overlapping but distinct object, Analysis Services uses the standard `type` attribute from the XML Instance Namespace to indicate the inheritance.</span></span> <span data-ttu-id="3f8bc-119">例如，下列 XML 片段示範 `type` 屬性如何識別 `Cube` 元素是繼承自正規 Cube 或繼承自虛擬 Cube：</span><span class="sxs-lookup"><span data-stu-id="3f8bc-119">For example, the following XML fragment shows how the `type` attribute identifies whether a `Cube` element inherits from a regular cube or from a virtual cube:</span></span>  
  
 `<Cubes>`  
  
 `<Cube xsi:type="RegularCube">`  
  
 `<Name>Sales</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `<Cube xsi:type="VirtualCube">`  
  
 `<Name>SalesAndInventory</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `</Cubes>`  
  
 ``  
  
 <span data-ttu-id="3f8bc-120">當多個類型都具有相同名稱的屬性時，通常不會使用繼承。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-120">Inheritance is generally not used when multiple types have a property of the same name.</span></span> <span data-ttu-id="3f8bc-121">例如，`Name` 與 `ID` 屬性出現在許多元素上，但是這些屬性尚未升級到抽象類型。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-121">For example, the `Name` and `ID` properties appear on many elements, but these properties have not been promoted to an abstract type.</span></span>  
  
## <a name="whitespace"></a><span data-ttu-id="3f8bc-122">空白</span><span class="sxs-lookup"><span data-stu-id="3f8bc-122">Whitespace</span></span>  
 <span data-ttu-id="3f8bc-123">元素值中的空白會保留下來。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-123">Whitespace within an element value is preserved.</span></span> <span data-ttu-id="3f8bc-124">不過，開頭和尾端空白則一律都會修剪。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-124">However, leading and trailing whitespace is always trimmed.</span></span> <span data-ttu-id="3f8bc-125">例如，下列元素有相同的文字，但是在文字中有不同的空白數目，因此會將它們視為不同的值：</span><span class="sxs-lookup"><span data-stu-id="3f8bc-125">For example, the following elements have the same text but differing amounts of whitespace within that text, and are therefore treated as if they have different values:</span></span>  
  
 `<Description>My text<Description>`  
  
 `<Description>My  text<Description>`  
  
 ``  
  
 <span data-ttu-id="3f8bc-126">不過，下列元素只有開頭和尾端空白不同，因此會將它們視為具有相等的值：</span><span class="sxs-lookup"><span data-stu-id="3f8bc-126">However, the following elements vary only in leading and trailing whitespace, and are therefore treated as if they have equivalent values:</span></span>  
  
 `<Description>My text<Description>`  
  
 `<Description>  My text  <Description>`  
  
 ``  
  
## <a name="data-types"></a><span data-ttu-id="3f8bc-127">資料類型</span><span class="sxs-lookup"><span data-stu-id="3f8bc-127">Data Types</span></span>  
 <span data-ttu-id="3f8bc-128">Analysis Services 使用下列標準 XML 結構描述定義語言 (XSD) 資料類型：</span><span class="sxs-lookup"><span data-stu-id="3f8bc-128">Analysis Services uses the following standard XML Schema definition language (XSD) data types:</span></span>  
  
 `Int`  
 <span data-ttu-id="3f8bc-129">介於-231 到 231-1 範圍的整數值。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-129">An integer value in the range of -231 to 231 - 1.</span></span>  
  
 `Long`  
 <span data-ttu-id="3f8bc-130">介於-263 到 263-1 範圍的整數值。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-130">An integer value in range of -263 to 263 - 1.</span></span>  
  
 `String`  
 <span data-ttu-id="3f8bc-131">符合下列全域規則的字串值：</span><span class="sxs-lookup"><span data-stu-id="3f8bc-131">A string value that conforms to the following global rules:</span></span>  
  
-   <span data-ttu-id="3f8bc-132">移除控制字元。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-132">Control characters are stripped out.</span></span>  
  
-   <span data-ttu-id="3f8bc-133">修剪開頭和尾端空白。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-133">Leading and trailing white space is trimmed.</span></span>  
  
-   <span data-ttu-id="3f8bc-134">保留內部空白字元。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-134">Internal white space is preserved.</span></span>  
  
 <span data-ttu-id="3f8bc-135">`Name` 與 `ID` 屬性對於字串元素中的有效字元具有特殊限制。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-135">`Name` and `ID` properties have special limitations on valid characters in string elements.</span></span> <span data-ttu-id="3f8bc-136">如需和慣例的詳細資訊 `Name` `ID` ，請參閱[ASSL 物件和物件特性](assl-objects-and-object-characteristics.md)。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-136">For additional information about `Name` and `ID` conventions, see [ASSL Objects and Object Characteristics](assl-objects-and-object-characteristics.md).</span></span>  
  
 `DateTime`  
 <span data-ttu-id="3f8bc-137">`DateTime`.NET Framework 中的結構。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-137">A `DateTime` structure from the .NET Framework.</span></span> <span data-ttu-id="3f8bc-138"> 值不可以是 NULL。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-138">A `DateTime` value cannot be NULL.</span></span> <span data-ttu-id="3f8bc-139">`DataTime` 資料類型支援的最低日期是 1601 年 1 月 1 日，可供程式設計人員做為 `DateTime.MinValue` 來使用。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-139">The lowest date supported by the `DataTime` data type is January 1, 1601, which is available to programmers as `DateTime.MinValue`.</span></span> <span data-ttu-id="3f8bc-140">出現支援的最低日期即表示您遺漏了 `DateTime` 值。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-140">The lowest supported date indicates that a `DateTime` value is missing.</span></span>  
  
 `Boolean`  
 <span data-ttu-id="3f8bc-141">只有兩個值的列舉，例如 {true, false} 或是 {0, 1}。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-141">An enumeration with only two values, such as {true, false} or {0, 1}.</span></span>  
  
## <a name="default-values"></a><span data-ttu-id="3f8bc-142">預設值</span><span class="sxs-lookup"><span data-stu-id="3f8bc-142">Default Values</span></span>  
 <span data-ttu-id="3f8bc-143">Analysis Services 會使用下表所列的預設值。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-143">Analysis Services uses the defaults listed in the following table.</span></span>  
  
|<span data-ttu-id="3f8bc-144">XML 資料類型</span><span class="sxs-lookup"><span data-stu-id="3f8bc-144">XML data type</span></span>|<span data-ttu-id="3f8bc-145">預設值</span><span class="sxs-lookup"><span data-stu-id="3f8bc-145">Default value</span></span>|  
|-------------------|-------------------|  
|`Boolean`|<span data-ttu-id="3f8bc-146">否</span><span class="sxs-lookup"><span data-stu-id="3f8bc-146">False</span></span>|  
|`String`|<span data-ttu-id="3f8bc-147">"" (空字串)</span><span class="sxs-lookup"><span data-stu-id="3f8bc-147">"" (empty string)</span></span>|  
|<span data-ttu-id="3f8bc-148">`Integer` 或 `Long`</span><span class="sxs-lookup"><span data-stu-id="3f8bc-148">`Integer` or `Long`</span></span>|<span data-ttu-id="3f8bc-149">0 (零)</span><span class="sxs-lookup"><span data-stu-id="3f8bc-149">0 (zero)</span></span>|  
|`Timestamp`|<span data-ttu-id="3f8bc-150">12:00:00 AM、1/1/0001 (對應至 `System.DateTime` 具有0刻度的 .Net framework) </span><span class="sxs-lookup"><span data-stu-id="3f8bc-150">12:00:00 AM, 1/1/0001 (corresponding to a the .NET Frameworks `System.DateTime` with 0 ticks)</span></span>|  
  
 <span data-ttu-id="3f8bc-151">有顯示但為空的元素會解譯成具有 Null 字串值，而不是預設值。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-151">An element that is present but empty is interpreted as having a value of a null string, not the default value.</span></span>  
  
### <a name="inherited-defaults"></a><span data-ttu-id="3f8bc-152">繼承的預設值</span><span class="sxs-lookup"><span data-stu-id="3f8bc-152">Inherited Defaults</span></span>  
 <span data-ttu-id="3f8bc-153">物件上指定的某些屬性會針對子物件或下階物件上的相同屬性提供預設值。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-153">Some properties that are specified on an object provide default values for the same property on child or descendant objects.</span></span> <span data-ttu-id="3f8bc-154">例如，`Cube.StorageMode` 會針對 `Partition.StorageMode` 提供預設值。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-154">For example, `Cube.StorageMode` provides the default value for `Partition.StorageMode`.</span></span> <span data-ttu-id="3f8bc-155">Analysis Services 套用於繼承預設值的規則如下所示：</span><span class="sxs-lookup"><span data-stu-id="3f8bc-155">The rules that Analysis Services applies for inherited default values are as follows:</span></span>  
  
-   <span data-ttu-id="3f8bc-156">當子物件的屬性在 XML 中為 Null 時，其值就會預設為繼承的值。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-156">When the property for the child object is null in the XML, its value defaults to the inherited value.</span></span> <span data-ttu-id="3f8bc-157">但是，如果您從伺服器查詢此值，伺服器會傳回 XML 元素的 null 值。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-157">However, if you query the value from the server, the server returns the null value of the XML element.</span></span>  
  
-   <span data-ttu-id="3f8bc-158">您無法以程式設計方式判斷出子物件的屬性是直接在子物件上設定的，還是繼承而來。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-158">It is not possible to determine programmatically whether the property of a child object has been set directly on the child object or inherited.</span></span>  
  
 <span data-ttu-id="3f8bc-159">有些元素已定義遺漏元素時會套用的預設值。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-159">Some elements have defined defaults that apply when the element is missing.</span></span> <span data-ttu-id="3f8bc-160">例如，在下列 XML 片段中，即使當某個 `Dimension` 元素包含 `Dimension` 元素，但是另一個 `Visible` 元素不包含時，`Dimension` 元素也是相等的。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-160">For example, the `Dimension` elements in the following XML fragment are equivalent even though one `Dimension` element contains a `Visible` element, but the other `Dimension` element does not.</span></span>  
  
 `<Dimension>`  
  
 `<Name>Product</Name>`  
  
 `</Dimension>`  
  
 `<Dimension>`  
  
 `<Name>Product</ Name>`  
  
 `<Visible>true</Visible>`  
  
 `</Dimension>`  
  
 <span data-ttu-id="3f8bc-161">如需繼承預設值的詳細資訊，請參閱[ASSL 物件和物件特性](assl-objects-and-object-characteristics.md)。</span><span class="sxs-lookup"><span data-stu-id="3f8bc-161">For more information on inherited defaults, see [ASSL Objects and Object Characteristics](assl-objects-and-object-characteristics.md).</span></span>  
  
  
