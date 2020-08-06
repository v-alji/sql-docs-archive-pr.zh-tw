---
title: " (XMLA) 插入、更新和卸載成員 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- inserting dimension members
- XML for Analysis, members
- removing dimension members
- dropping dimension members
- write-enabled dimensions [Analysis Services]
- XMLA, members
- deleting dimension members
- dimensions [Analysis Services], XML for Analysis
ms.assetid: bba922b5-8b88-4051-9506-ff055248182a
author: minewiskan
ms.author: owend
ms.openlocfilehash: aef124abc8398f1b314a391291b52340a90689ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599230"
---
# <a name="inserting-updating-and-dropping-members-xmla"></a><span data-ttu-id="58ee8-102">插入、更新和卸除成員 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="58ee8-102">Inserting, Updating, and Dropping Members (XMLA)</span></span>
  <span data-ttu-id="58ee8-103">您可以使用 XML for Analysis (XMLA) 中的[insert](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla)、 [update](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)和[Drop](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla)命令，分別插入、更新或刪除可寫入維度中的成員。</span><span class="sxs-lookup"><span data-stu-id="58ee8-103">You can use the [Insert](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla), [Update](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla), and [Drop](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla) commands in XML for Analysis (XMLA) to respectively insert, update, or delete members from a write-enabled dimension.</span></span> <span data-ttu-id="58ee8-104">如需已啟用寫入維度的詳細資訊，請參閱可[寫入維度](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)。</span><span class="sxs-lookup"><span data-stu-id="58ee8-104">For more information about write-enabled dimensions, see [Write-Enabled Dimensions](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).</span></span>  
  
## <a name="inserting-new-members"></a><span data-ttu-id="58ee8-105">插入新成員</span><span class="sxs-lookup"><span data-stu-id="58ee8-105">Inserting New Members</span></span>  
 <span data-ttu-id="58ee8-106">`Insert` 命令會將新的成員插入可寫入維度中的特定屬性。</span><span class="sxs-lookup"><span data-stu-id="58ee8-106">The `Insert` command inserts new members into specified attributes in a write-enabled dimension.</span></span>  
  
 <span data-ttu-id="58ee8-107">在建構 `Insert` 命令之前，您應該有下列可用於插入新成員的資訊：</span><span class="sxs-lookup"><span data-stu-id="58ee8-107">Before constructing the `Insert` command, you should have the following information available for the new members to be inserted:</span></span>  
  
-   <span data-ttu-id="58ee8-108">要在其中插入新成員的維度。</span><span class="sxs-lookup"><span data-stu-id="58ee8-108">The dimension in which to insert the new members.</span></span>  
  
-   <span data-ttu-id="58ee8-109">要在其中插入新成員的維度屬性。</span><span class="sxs-lookup"><span data-stu-id="58ee8-109">The dimension attribute in which to insert the new members.</span></span>  
  
-   <span data-ttu-id="58ee8-110">新成員的名稱，包括任何適用的名稱翻譯。</span><span class="sxs-lookup"><span data-stu-id="58ee8-110">The names of the new members, including any applicable translations for the name.</span></span>  
  
-   <span data-ttu-id="58ee8-111">新成員的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="58ee8-111">The keys of the new members.</span></span> <span data-ttu-id="58ee8-112">如果屬性使用複合索引鍵，索引鍵可能需要多個值。</span><span class="sxs-lookup"><span data-stu-id="58ee8-112">If an attribute uses a composite key, the key may require multiple values.</span></span>  
  
-   <span data-ttu-id="58ee8-113">並未像其他的屬性已實作在維度中，但適用的任何屬性值。</span><span class="sxs-lookup"><span data-stu-id="58ee8-113">Values for any applicable attribute properties that are not implemented as other attributes within the dimension.</span></span> <span data-ttu-id="58ee8-114">這樣的屬性包括一元運算、翻譯、自訂積存、自訂積存屬性以及略過的層級。</span><span class="sxs-lookup"><span data-stu-id="58ee8-114">Such attribute properties include unary operations, translations, custom rollups, custom rollup properties, and skipped levels.</span></span>  
  
 <span data-ttu-id="58ee8-115">`Insert` 命令只使用兩個屬性：</span><span class="sxs-lookup"><span data-stu-id="58ee8-115">The `Insert` command takes only two properties:</span></span>  
  
-   <span data-ttu-id="58ee8-116">[物件](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)屬性，包含要在其中插入成員之維度的物件參考。</span><span class="sxs-lookup"><span data-stu-id="58ee8-116">The [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property, which contains an object reference for the dimension in which the members are to be inserted.</span></span> <span data-ttu-id="58ee8-117">物件參考包含資料庫識別碼、Cube 識別碼以及維度的維度識別碼。</span><span class="sxs-lookup"><span data-stu-id="58ee8-117">The object reference contains the database identifier, cube identifier, and dimension identifier for the dimension.</span></span>  
  
-   <span data-ttu-id="58ee8-118">[Attributes](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/attributes-element-xmla)屬性，其中包含一或多個[屬性](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/attribute-element-xmla)專案，以識別要在其中插入成員的屬性。</span><span class="sxs-lookup"><span data-stu-id="58ee8-118">The [Attributes](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/attributes-element-xmla) property, which contains one or more [Attribute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/attribute-element-xmla) elements to identify the attributes in which members are to be inserted.</span></span> <span data-ttu-id="58ee8-119">每個 `Attribute` 元素可識別屬性，並為要加入識別屬性的單一成員提供名稱、值、翻譯、一元運算子、自訂積存、自訂積存屬性以及略過的層級。</span><span class="sxs-lookup"><span data-stu-id="58ee8-119">Each `Attribute` element identifies an attribute and provides the name, value, translations, unary operator, custom rollup, custom rollup properties, and skipped levels for a single member to be added to the identified attribute.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="58ee8-120">`Attribute` 元素的所有屬性都必須包含在內。</span><span class="sxs-lookup"><span data-stu-id="58ee8-120">All properties for the `Attribute` element must be included.</span></span> <span data-ttu-id="58ee8-121">否則，系統可能會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="58ee8-121">Otherwise, an error may occur.</span></span>  
  
## <a name="updating-existing-members"></a><span data-ttu-id="58ee8-122">更新現有的成員</span><span class="sxs-lookup"><span data-stu-id="58ee8-122">Updating Existing Members</span></span>  
 <span data-ttu-id="58ee8-123">`Update` 命令會根據與其他屬性中其他成員的關係，在可寫入的維度之指定屬性中更新現有的成員。</span><span class="sxs-lookup"><span data-stu-id="58ee8-123">The `Update` command updates existing members in specified attributes, based on relationships with other members in other attributes, in a write-enabled dimension.</span></span> <span data-ttu-id="58ee8-124">`Update` 命令可以將成員移到維度所含的階層中之其他層級，而且可用以重新設定父屬性所定義的父子式階層之結構。</span><span class="sxs-lookup"><span data-stu-id="58ee8-124">The `Update` command can move members to other levels in hierarchies contained by the dimension, and can be used to restructure parent-child hierarchies defined by parent attributes.</span></span>  
  
 <span data-ttu-id="58ee8-125">在建構 `Update` 命令之前，您應該有下列可用於更新成員的資訊：</span><span class="sxs-lookup"><span data-stu-id="58ee8-125">Before constructing the `Update` command, you should have the following information available for the members to be updated:</span></span>  
  
-   <span data-ttu-id="58ee8-126">要在其中更新現有成員的維度。</span><span class="sxs-lookup"><span data-stu-id="58ee8-126">The dimension in which to update existing members.</span></span>  
  
-   <span data-ttu-id="58ee8-127">要在其中更新現有成員的維度屬性。</span><span class="sxs-lookup"><span data-stu-id="58ee8-127">The dimension attributes in which to update existing members.</span></span>  
  
-   <span data-ttu-id="58ee8-128">現有成員的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="58ee8-128">The keys of the existing members.</span></span> <span data-ttu-id="58ee8-129">如果屬性使用複合索引鍵，索引鍵可能需要多個值。</span><span class="sxs-lookup"><span data-stu-id="58ee8-129">If an attribute uses a composite key, the key may require multiple values.</span></span>  
  
-   <span data-ttu-id="58ee8-130">並未像其他的屬性已實作在維度中，但適用的任何屬性值。</span><span class="sxs-lookup"><span data-stu-id="58ee8-130">Values for any applicable attribute properties that are not implemented as other attributes within the dimension.</span></span> <span data-ttu-id="58ee8-131">這樣的屬性包括一元運算、翻譯、自訂積存、自訂積存屬性以及略過的層級。</span><span class="sxs-lookup"><span data-stu-id="58ee8-131">Such attribute properties include unary operations, translations, custom rollups, custom rollup properties, and skipped levels.</span></span>  
  
 <span data-ttu-id="58ee8-132">`Update` 命令只使用三個必要的屬性：</span><span class="sxs-lookup"><span data-stu-id="58ee8-132">The `Update` command takes only three required properties:</span></span>  
  
-   <span data-ttu-id="58ee8-133">`Object` 屬性，包含要在其中更新成員之維度的物件參考。</span><span class="sxs-lookup"><span data-stu-id="58ee8-133">The `Object` property, which contains an object reference for the dimension in which the members are to be updated.</span></span> <span data-ttu-id="58ee8-134">物件參考包含資料庫識別碼、Cube 識別碼以及維度的維度識別碼。</span><span class="sxs-lookup"><span data-stu-id="58ee8-134">The object reference contains the database identifier, cube identifier, and dimension identifier for the dimension.</span></span>  
  
-   <span data-ttu-id="58ee8-135">`Attributes` 屬性，包含一或多個 `Attribute` 元素，以識別要在其中更新成員的屬性。</span><span class="sxs-lookup"><span data-stu-id="58ee8-135">The `Attributes` property, which contains one or more `Attribute` elements to identify the attributes in which members are to be updated.</span></span> <span data-ttu-id="58ee8-136">`Attribute` 元素可識別屬性，並為識別屬性要更新的單一成員提供名稱、值、翻譯、一元運算子、自訂積存、自訂積存屬性以及略過的層級。</span><span class="sxs-lookup"><span data-stu-id="58ee8-136">The `Attribute` element identifies an attribute and provides the name, value, translations, unary operator, custom rollup, custom rollup properties, and skipped levels for a single member updated for the identified attribute.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="58ee8-137">`Attribute` 元素的所有屬性都必須包含在內。</span><span class="sxs-lookup"><span data-stu-id="58ee8-137">All properties for the `Attribute` element must be included.</span></span> <span data-ttu-id="58ee8-138">否則，系統可能會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="58ee8-138">Otherwise, an error may occur.</span></span>  
  
-   <span data-ttu-id="58ee8-139">[Where](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/where-element-xmla)屬性，其中包含一或多個 `Attribute` 元素，這些專案會限制要在其中更新成員的屬性。</span><span class="sxs-lookup"><span data-stu-id="58ee8-139">The [Where](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/where-element-xmla) property, which contains one or more `Attribute` elements that constrain the attributes in which members are to be updated.</span></span> <span data-ttu-id="58ee8-140">`Where` 屬性對於將 `Update` 命令限制在成員的特定執行個體來說十分重要。</span><span class="sxs-lookup"><span data-stu-id="58ee8-140">The `Where` property is crucial to limiting an `Update` command to specific instances of a member.</span></span> <span data-ttu-id="58ee8-141">如果 `Where` 未指定屬性，則會更新指定成員的所有實例。</span><span class="sxs-lookup"><span data-stu-id="58ee8-141">If the `Where` property is not specified, all instances of a given member are updated.</span></span> <span data-ttu-id="58ee8-142">例如，您要將三個客戶的城市名稱從 Redmond 變更為 Bellevue。</span><span class="sxs-lookup"><span data-stu-id="58ee8-142">For example, there are three customers for whom you want to change the city name from Redmond to Bellevue.</span></span> <span data-ttu-id="58ee8-143">若要變更城市名稱，您必須提供 `Where` 屬性以識別 Customer 屬性中應該變更的三個 City 屬性成員。</span><span class="sxs-lookup"><span data-stu-id="58ee8-143">To change the city name, you must provide a `Where` property that identifies the three members in the Customer attribute for which the members in the City attribute should be changed.</span></span> <span data-ttu-id="58ee8-144">如果您沒有提供這個 `Where` 屬性，則城市名稱目前為 Redmond 的每個客戶，在執行 `Update` 命令之後，其城市名稱都將變成 Bellevue。</span><span class="sxs-lookup"><span data-stu-id="58ee8-144">If you do not provide this `Where` property, every customer whose city name is currently Redmond would have the city name of Bellevue after the `Update` command runs.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="58ee8-145">除了新成員之外，`Update` 命令只能為不包含在 `Where` 子句中的屬性更新屬性索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="58ee8-145">With the exception of new members, the `Update` command can only update attribute key values for attributes not included in the `Where` clause.</span></span> <span data-ttu-id="58ee8-146">例如，更新客戶時無法更新城市名稱，否則會為所有客戶變更城市名稱。</span><span class="sxs-lookup"><span data-stu-id="58ee8-146">For example, the city name cannot be updated when a customer is updated; otherwise, the city name is changed for all customers.</span></span>  
  
### <a name="updating-members-in-parent-attributes"></a><span data-ttu-id="58ee8-147">更新父屬性中的成員</span><span class="sxs-lookup"><span data-stu-id="58ee8-147">Updating Members in Parent Attributes</span></span>  
 <span data-ttu-id="58ee8-148">若要支援父屬性，請 `Update` 命令選擇性的[MoveWithDescendants](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/movewithdescendants-element-xmla)MovewithDescedants 屬性。</span><span class="sxs-lookup"><span data-stu-id="58ee8-148">To support parent attributes, the `Update` command the optional [MoveWithDescendants](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/movewithdescendants-element-xmla)MovewithDescedants properties.</span></span> <span data-ttu-id="58ee8-149">將 `MoveWithDescendants` 屬性設定為 true，以指定在該父成員識別碼變更時，父成員的下階也應該隨父成員一起移動。</span><span class="sxs-lookup"><span data-stu-id="58ee8-149">Setting the `MoveWithDescendants` property to true indicates that the descendants of the parent member should also be moved with the parent member when the identifier of that parent member changes.</span></span> <span data-ttu-id="58ee8-150">如果這個值是設定為 false，移動父成員會造成該父成員的直接下階升級為父成員先前所在的層級。</span><span class="sxs-lookup"><span data-stu-id="58ee8-150">If this value is set to false, moving a parent member causes the immediate descendants of that parent member to be promoted to the level in which the parent member formerly resided.</span></span>  
  
 <span data-ttu-id="58ee8-151">在父屬性中更新成員時，`Update` 命令無法更新其他屬性中的成員。</span><span class="sxs-lookup"><span data-stu-id="58ee8-151">When updating members in a parent attribute, the `Update` command cannot update members in other attributes.</span></span>  
  
## <a name="dropping-existing-members"></a><span data-ttu-id="58ee8-152">卸除現有的成員</span><span class="sxs-lookup"><span data-stu-id="58ee8-152">Dropping Existing Members</span></span>  
 <span data-ttu-id="58ee8-153">在建構 `Drop` 命令之前，您應該有下列可用於卸除成員的資訊：</span><span class="sxs-lookup"><span data-stu-id="58ee8-153">Before constructing the `Drop` command, you should have the following information available for the members to be dropped:</span></span>  
  
-   <span data-ttu-id="58ee8-154">要在其中卸除現有成員的維度。</span><span class="sxs-lookup"><span data-stu-id="58ee8-154">The dimension in which to drop existing members.</span></span>  
  
-   <span data-ttu-id="58ee8-155">要在其中卸除現有成員的維度屬性。</span><span class="sxs-lookup"><span data-stu-id="58ee8-155">The dimension attributes in which to drop existing members.</span></span>  
  
-   <span data-ttu-id="58ee8-156">要卸除之現有成員的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="58ee8-156">The keys of the existing members to be dropped.</span></span> <span data-ttu-id="58ee8-157">如果屬性使用複合索引鍵，索引鍵可能需要多個值。</span><span class="sxs-lookup"><span data-stu-id="58ee8-157">If an attribute uses a composite key, the key may require multiple values.</span></span>  
  
 <span data-ttu-id="58ee8-158">`Drop` 命令只使用兩個必要的屬性：</span><span class="sxs-lookup"><span data-stu-id="58ee8-158">The `Drop` command takes only two required properties:</span></span>  
  
-   <span data-ttu-id="58ee8-159">`Object` 屬性，包含要在其中卸除成員之維度的物件參考。</span><span class="sxs-lookup"><span data-stu-id="58ee8-159">The `Object` property, which contains an object reference for the dimension in which the members are to be dropped.</span></span> <span data-ttu-id="58ee8-160">物件參考包含資料庫識別碼、Cube 識別碼以及維度的維度識別碼。</span><span class="sxs-lookup"><span data-stu-id="58ee8-160">The object reference contains the database identifier, cube identifier, and dimension identifier for the dimension.</span></span>  
  
-   <span data-ttu-id="58ee8-161">`Where` 屬性包含一或多個 `Attribute` 元素，會限制要在其中刪除成員的屬性。</span><span class="sxs-lookup"><span data-stu-id="58ee8-161">The `Where` property, which contains one or more `Attribute` elements to constrain the attributes in which members are to be deleted.</span></span> <span data-ttu-id="58ee8-162">`Where` 屬性對於將 `Drop` 命令限制在成員的特定執行個體來說十分重要。</span><span class="sxs-lookup"><span data-stu-id="58ee8-162">The `Where` property is crucial to limiting a `Drop` command to specific instances of a member.</span></span> <span data-ttu-id="58ee8-163">如果未指定 `Where`命令，指定成員的所有執行個體都會卸除。</span><span class="sxs-lookup"><span data-stu-id="58ee8-163">If the `Where` command is not specified, all instances of a given member are dropped.</span></span> <span data-ttu-id="58ee8-164">例如，您要從 Redmond 卸除三個客戶。</span><span class="sxs-lookup"><span data-stu-id="58ee8-164">For example, there are three customers that you want to drop from Redmond.</span></span> <span data-ttu-id="58ee8-165">若要卸除這些客戶，您必須提供 `Where` 屬性以識別 Customer 屬性中要移除的三個成員，以及要從 City 屬性之 Redmond 成員中移除的三個客戶。</span><span class="sxs-lookup"><span data-stu-id="58ee8-165">To drop these customers, you must provide a `Where` property that identifies the three members in the Customer attribute to be removed and the Redmond member of the City attribute from which the three customers are to be removed.</span></span> <span data-ttu-id="58ee8-166">如果 `Where` 屬性只指定 City 屬性的 Redmond 成員，則 `Drop` 命令會卸除與 Redmond 關聯的每個客戶。</span><span class="sxs-lookup"><span data-stu-id="58ee8-166">If the `Where` property only specifies the Redmond member of the City attribute, every customer associated with Redmond would be dropped by the `Drop` command.</span></span> <span data-ttu-id="58ee8-167">如果 `Where` 屬性只在 Customer 屬性中指定三個成員，則 `Drop` 命令會完全刪除這三個客戶。</span><span class="sxs-lookup"><span data-stu-id="58ee8-167">If the `Where` property only specifies the three members in the Customer attribute, the three customers would be deleted entirely by the `Drop` command.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="58ee8-168">包括在 `Attribute` 命令中的 `Drop` 元素必須只包含 `AttributeName` 與 `Keys` 屬性。</span><span class="sxs-lookup"><span data-stu-id="58ee8-168">The `Attribute` elements included in a `Drop` command must contain only the `AttributeName` and `Keys` properties.</span></span> <span data-ttu-id="58ee8-169">否則，系統可能會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="58ee8-169">Otherwise, an error may occur.</span></span>  
  
### <a name="dropping-members-in-parent-attributes"></a><span data-ttu-id="58ee8-170">卸除父屬性中的成員</span><span class="sxs-lookup"><span data-stu-id="58ee8-170">Dropping Members in Parent Attributes</span></span>  
 <span data-ttu-id="58ee8-171">設定[DeleteWithDescendants](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/deletewithdescendants-element-xmla)屬性工作表示父成員的下階也應該與父成員一起刪除。</span><span class="sxs-lookup"><span data-stu-id="58ee8-171">Setting the [DeleteWithDescendants](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/deletewithdescendants-element-xmla) property indicates that the descendants of a parent member should also be deleted with the parent member.</span></span> <span data-ttu-id="58ee8-172">如果這個值是設定為 false，則會改將父成員的直接下階升級為父成員先前所在的層級。</span><span class="sxs-lookup"><span data-stu-id="58ee8-172">If this value is set to false, the immediate descendants of the parent member are instead promoted to the level in which the parent member formerly resided.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="58ee8-173">使用者只要擁有父成員的刪除權限，即可同時刪除父成員及其子階。</span><span class="sxs-lookup"><span data-stu-id="58ee8-173">A user needs only to have delete permissions for the parent member to delete both the parent member and its descendants.</span></span> <span data-ttu-id="58ee8-174">使用者不需要子階的刪除權限。</span><span class="sxs-lookup"><span data-stu-id="58ee8-174">A user does not need delete permissions on the descendants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ee8-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58ee8-175">See Also</span></span>  
 <span data-ttu-id="58ee8-176">[Drop 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="58ee8-176">[Drop Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla) </span></span>  
 <span data-ttu-id="58ee8-177">[&#40;XMLA&#41;插入元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="58ee8-177">[Insert Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla) </span></span>  
 <span data-ttu-id="58ee8-178">[Update 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="58ee8-178">[Update Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla) </span></span>  
 <span data-ttu-id="58ee8-179">[定義和識別 &#40;XMLA&#41;的物件](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects) </span><span class="sxs-lookup"><span data-stu-id="58ee8-179">[Defining and Identifying Objects &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects) </span></span>  
 [<span data-ttu-id="58ee8-180">在 Analysis Services 中使用 XMLA 進行開發</span><span class="sxs-lookup"><span data-stu-id="58ee8-180">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
