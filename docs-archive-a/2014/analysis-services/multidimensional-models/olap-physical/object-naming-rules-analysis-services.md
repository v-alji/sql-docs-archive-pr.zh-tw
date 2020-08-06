---
title: 物件命名規則 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], naming
ms.assetid: b338a60d-4802-4b68-862a-6dc6a3f75e48
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6adfd4b23b6fe9129641271fc3c2381e161119ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598592"
---
# <a name="object-naming-rules-analysis-services"></a><span data-ttu-id="d6b7d-102">物件命名規則 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="d6b7d-102">Object Naming Rules (Analysis Services)</span></span>
  <span data-ttu-id="d6b7d-103">本主題將描述物件命名慣例以及任何物件名稱 (以 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 中的程式碼或指令碼形式) 中無法使用的保留字和字元。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-103">This topic describes object naming conventions, as well as the reserved words and characters that cannot be used in any object name, in code or script in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
##  <a name="naming-conventions"></a><a name="bkmk_Names"></a><span data-ttu-id="d6b7d-104">命名慣例</span><span class="sxs-lookup"><span data-stu-id="d6b7d-104">Naming Conventions</span></span>  
 <span data-ttu-id="d6b7d-105">每個物件都有在父集合的範圍內必須是唯一的 `Name` 和 `ID` 屬性。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-105">Every object has a `Name` and `ID` property that must be unique within the scope of the parent collection.</span></span> <span data-ttu-id="d6b7d-106">例如，兩個維度可以擁有相同的名稱，前提是每個維度都位在不同的資料庫內。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-106">For example, two dimensions can have same name as long as each one resides in a different database.</span></span>  
  
 <span data-ttu-id="d6b7d-107">雖然您可以手動指定它，但是在建立物件時通常會自動產生 `ID`。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-107">Although you can specify it manually, the `ID` is typically auto-generated when the object is created.</span></span> <span data-ttu-id="d6b7d-108">一旦您開始建立模型之後，絕對不要變更 `ID`。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-108">You should never change the `ID` once you have begun building a model.</span></span> <span data-ttu-id="d6b7d-109">整個模型中的所有物件參考都是根據 `ID`。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-109">All object references throughout a model are based on the `ID`.</span></span> <span data-ttu-id="d6b7d-110">因此，變更 `ID` 很容易導致模型損毀。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-110">Thus, changing an `ID` can easily result in model corruption.</span></span>  
  
 <span data-ttu-id="d6b7d-111">`DataSource` 和 `DataSourceView` 物件有顯著的命名慣例例外。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-111">`DataSource` and `DataSourceView` objects have notable exceptions to naming conventions.</span></span> <span data-ttu-id="d6b7d-112">`DataSource` 識別碼可以設定為一個非唯一的點 (.)，當做目前資料庫的參考。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-112">`DataSource` ID can be set to a single dot (.), which is not unique, as a reference to the current database.</span></span> <span data-ttu-id="d6b7d-113">第二個例外狀況為 `DataSourceView`，它會遵守針對 .NET Framework 中的 `DataSet` 物件所定義的命名慣例，其中會使用 `Name` 當做識別碼。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-113">A second exception is `DataSourceView`, which adheres to the naming conventions defined for `DataSet` objects in the .NET Framework, where the `Name` is used as the identifier.</span></span>  
  
 <span data-ttu-id="d6b7d-114">下列規則會套用到 `Name` 和 `ID` 屬性。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-114">The following rules apply to `Name` and `ID` properties.</span></span>  
  
-   <span data-ttu-id="d6b7d-115">名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-115">Names are case insensitive.</span></span> <span data-ttu-id="d6b7d-116">您不能在相同的資料庫中有名為 "sales" 的 cube，另一個名稱為 "Sales"。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-116">You cannot have a cube named "sales" and another named "Sales" in the same database.</span></span>  
  
-   <span data-ttu-id="d6b7d-117">物件名稱中不允許有任何開頭或尾端空白，但是您可以在名稱中內嵌空白。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-117">No leading or trailing spaces allowed in an object name, although you can embed spaces within a name.</span></span> <span data-ttu-id="d6b7d-118">開頭和尾端空白會以隱含方式加以修剪。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-118">Leading and trailing spaces are implicitly trimmed.</span></span> <span data-ttu-id="d6b7d-119">這同樣適用於物件的 `Name` 和 `ID`。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-119">This applies to both the `Name` and `ID` of an object.</span></span>  
  
-   <span data-ttu-id="d6b7d-120">最大字元數為 100。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-120">The maximum number of characters is 100.</span></span>  
  
-   <span data-ttu-id="d6b7d-121">識別項的第一個字元沒有特殊規定。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-121">There is no special requirement for the first character of an identifier.</span></span> <span data-ttu-id="d6b7d-122">第一個字元可能會是任何有效的字元。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-122">The first character may be any valid character.</span></span>  
  
##  <a name="reserved-words-and-characters"></a><a name="bkmk_reserved"></a><span data-ttu-id="d6b7d-123">保留字和字元</span><span class="sxs-lookup"><span data-stu-id="d6b7d-123">Reserved Words and Characters</span></span>  
 <span data-ttu-id="d6b7d-124">保留字為英文，而且會套用到物件名稱，而不是標題。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-124">Reserved words are in English, and apply to object names, not Captions.</span></span> <span data-ttu-id="d6b7d-125">如果您不小心在物件名稱中使用保留字，將會發生驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-125">If you inadvertently use a reserved word in an object name, a validation error will occur.</span></span> <span data-ttu-id="d6b7d-126">如果是多維度和資料採礦模型，底下所述的保留字在任何時候都無法在任何物件名稱中使用。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-126">For multidimensional and data mining models, the reserved words described below cannot be used in any object name, at any time.</span></span>  
  
 <span data-ttu-id="d6b7d-127">如果是資料庫相容性設定為 1103 的表格式模型，對於不符合擴充字元要求及某些用戶端應用程式命名慣例的特定物件而言，驗證規則已經鬆綁。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-127">For tabular models, where the database compatibility is set to 1103, validation rules have been relaxed for certain objects, out of compliance for the extended character requirements and naming conventions of certain client applications.</span></span> <span data-ttu-id="d6b7d-128">符合這些準則的資料庫受限於比較不嚴謹的驗證規則。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-128">Databases that meet these criteria are subject to less stringent validation rules.</span></span> <span data-ttu-id="d6b7d-129">在此情況下，有可能物件名稱包含受限的字元而且依然通過驗證。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-129">In this case, it's possible for an object name to include a restricted character and still pass validation.</span></span>  
  
 <span data-ttu-id="d6b7d-130">**保留字**</span><span class="sxs-lookup"><span data-stu-id="d6b7d-130">**Reserved Words**</span></span>  
  
-   <span data-ttu-id="d6b7d-131">AUX</span><span class="sxs-lookup"><span data-stu-id="d6b7d-131">AUX</span></span>  
  
-   <span data-ttu-id="d6b7d-132">CLOCK$</span><span class="sxs-lookup"><span data-stu-id="d6b7d-132">CLOCK$</span></span>  
  
-   <span data-ttu-id="d6b7d-133">COM1 到 COM9 (COM1、COM2、COM3 等等)</span><span class="sxs-lookup"><span data-stu-id="d6b7d-133">COM1 through COM9 (COM1, COM2, COM3, and so on)</span></span>  
  
-   <span data-ttu-id="d6b7d-134">CON</span><span class="sxs-lookup"><span data-stu-id="d6b7d-134">CON</span></span>  
  
-   <span data-ttu-id="d6b7d-135">LPT1 到 LPT9 (LPT1、LPT2、LPT3 等等)</span><span class="sxs-lookup"><span data-stu-id="d6b7d-135">LPT1 through LPT9 (LPT1, LPT2, LPT3, and so on)</span></span>  
  
-   <span data-ttu-id="d6b7d-136">NUL</span><span class="sxs-lookup"><span data-stu-id="d6b7d-136">NUL</span></span>  
  
-   <span data-ttu-id="d6b7d-137">PRN</span><span class="sxs-lookup"><span data-stu-id="d6b7d-137">PRN</span></span>  
  
-   <span data-ttu-id="d6b7d-138">在 XML 中，不允許使用 NULL 當做任何字串中的字元</span><span class="sxs-lookup"><span data-stu-id="d6b7d-138">NULL is not allowed as a character in any string within the XML</span></span>  
  
 <span data-ttu-id="d6b7d-139">**保留的字元**</span><span class="sxs-lookup"><span data-stu-id="d6b7d-139">**Reserved Characters**</span></span>  
  
 <span data-ttu-id="d6b7d-140">下表列出特定物件的無效字元。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-140">The following table lists invalid characters for specific objects.</span></span>  
  
|<span data-ttu-id="d6b7d-141">Object</span><span class="sxs-lookup"><span data-stu-id="d6b7d-141">Object</span></span>|<span data-ttu-id="d6b7d-142">無效字元</span><span class="sxs-lookup"><span data-stu-id="d6b7d-142">Invalid characters</span></span>|  
|------------|------------------------|  
|`Server`|<span data-ttu-id="d6b7d-143">在命名伺服器物件時要遵守 Windows 伺服器命名慣例。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-143">Follow Windows server naming conventions when naming a server object.</span></span> <span data-ttu-id="d6b7d-144">如需詳細資訊，請參閱[ (Windows) 的命名慣例](/windows/desktop/DNS/naming-conventions)。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-144">See [Naming Conventions (Windows)](/windows/desktop/DNS/naming-conventions) for details.</span></span>|  
|`DataSource`| `: / \ * \| ? " () [] {} <>` |  
|<span data-ttu-id="d6b7d-145">`Level` 或 `Attribute`</span><span class="sxs-lookup"><span data-stu-id="d6b7d-145">`Level` or `Attribute`</span></span>|````. , ; ' ` : / \ * & \| ? " & % $ ! + = [] {} < >````|  
|<span data-ttu-id="d6b7d-146">`Dimension` 或 `Hierarchy`</span><span class="sxs-lookup"><span data-stu-id="d6b7d-146">`Dimension` or `Hierarchy`</span></span>|````. , ; ' ` : / \ * \| ? " & % $ ! + = () [] {} <,>````|  
|<span data-ttu-id="d6b7d-147">所有其他物件</span><span class="sxs-lookup"><span data-stu-id="d6b7d-147">All other objects</span></span>|````. , ; ' ` : / \ * \| ? " & % $ ! + = () [] {} < >````|  
  
 <span data-ttu-id="d6b7d-148">**例外狀況：當允許保留的字元時**</span><span class="sxs-lookup"><span data-stu-id="d6b7d-148">**Exceptions: When Reserved Characters are Allowed**</span></span>  
  
 <span data-ttu-id="d6b7d-149">如前所述，具有特定模式和相容性層級的資料庫可以擁有包含保留字元的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-149">As noted, databases of a specific modality and compatibility level can have object names that include reserved characters.</span></span> <span data-ttu-id="d6b7d-150">如果是允許使用擴充字元的表格式資料庫 (1103 或更高層級)，維度屬性、階層、層級、量值和 KPI 物件名稱可以包含保留字元：</span><span class="sxs-lookup"><span data-stu-id="d6b7d-150">Dimension attribute, hierarchy, level, measure and KPI object names can include reserved characters, for tabular databases (1103 or higher) that allow the use of extended characters:</span></span>  
  
|<span data-ttu-id="d6b7d-151">伺服器模式和資料庫相容性層級</span><span class="sxs-lookup"><span data-stu-id="d6b7d-151">Server mode and database compatibility level</span></span>|<span data-ttu-id="d6b7d-152">允許保留的字元嗎？</span><span class="sxs-lookup"><span data-stu-id="d6b7d-152">Reserved characters allowed?</span></span>|  
|--------------------------------------------------|----------------------------------|  
|<span data-ttu-id="d6b7d-153">MOLAP (所有版本)</span><span class="sxs-lookup"><span data-stu-id="d6b7d-153">MOLAP (all versions)</span></span>|<span data-ttu-id="d6b7d-154">否</span><span class="sxs-lookup"><span data-stu-id="d6b7d-154">No</span></span>|  
|<span data-ttu-id="d6b7d-155">表格式 - 1050</span><span class="sxs-lookup"><span data-stu-id="d6b7d-155">Tabular - 1050</span></span>|<span data-ttu-id="d6b7d-156">否</span><span class="sxs-lookup"><span data-stu-id="d6b7d-156">No</span></span>|  
|<span data-ttu-id="d6b7d-157">表格式 - 1100</span><span class="sxs-lookup"><span data-stu-id="d6b7d-157">Tabular - 1100</span></span>|<span data-ttu-id="d6b7d-158">否</span><span class="sxs-lookup"><span data-stu-id="d6b7d-158">No</span></span>|  
|<span data-ttu-id="d6b7d-159">表格式-1130 和更高版本</span><span class="sxs-lookup"><span data-stu-id="d6b7d-159">Tabular - 1130 and higher</span></span>|<span data-ttu-id="d6b7d-160">是</span><span class="sxs-lookup"><span data-stu-id="d6b7d-160">Yes</span></span>|  
  
 <span data-ttu-id="d6b7d-161">資料庫可以有 ModelType 預設值。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-161">Databases can have a ModelType of default.</span></span> <span data-ttu-id="d6b7d-162">預設值相當於多維度，因此不支援在資料行名稱中使用保留的字元。</span><span class="sxs-lookup"><span data-stu-id="d6b7d-162">Default is equivalent to multidimensional, and thus does not support the use of reserved characters in column names.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6b7d-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6b7d-163">See Also</span></span>  
 <span data-ttu-id="d6b7d-164">[MDX 保留字](/sql/mdx/mdx-reserved-words) </span><span class="sxs-lookup"><span data-stu-id="d6b7d-164">[MDX Reserved Words](/sql/mdx/mdx-reserved-words) </span></span>  
 <span data-ttu-id="d6b7d-165">[翻譯 &#40;Analysis Services&#41;](/analysis-services/translation-support-in-analysis-services) </span><span class="sxs-lookup"><span data-stu-id="d6b7d-165">[Translations &#40;Analysis Services&#41;](/analysis-services/translation-support-in-analysis-services) </span></span>  
 [<span data-ttu-id="d6b7d-166">XML for Analysis 相容性 &#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="d6b7d-166">XML for Analysis Compliance &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-compliance-xmla)  
  
  
