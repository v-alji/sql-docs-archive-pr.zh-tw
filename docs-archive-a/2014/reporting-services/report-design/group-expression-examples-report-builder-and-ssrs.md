---
title: 群組運算式範例 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data [Reporting Services], grouping
- grouping data
- expressions [Reporting Services], adding
- groups [Reporting Services], expressions
ms.assetid: 34cd0249-fc74-4cf2-ba11-7b072992bfd2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 128e3fa7aed189fd00072c2c3e961b80f8137c99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686794"
---
# <a name="group-expression-examples-report-builder-and-ssrs"></a><span data-ttu-id="8d613-102">群組運算式範例 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="8d613-102">Group Expression Examples (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8d613-103">在資料區域中，您可以依據單一欄位來分組資料，或是建立較為複雜的運算式來識別分組的資料。</span><span class="sxs-lookup"><span data-stu-id="8d613-103">In a data region, you can group data by a single field, or create more complex expressions that identify the data on which to group.</span></span> <span data-ttu-id="8d613-104">複雜運算式包含了多個欄位或參數、條件陳述式或自訂程式碼的參考。</span><span class="sxs-lookup"><span data-stu-id="8d613-104">Complex expressions include references to multiple fields or parameters, conditional statements, or custom code.</span></span> <span data-ttu-id="8d613-105">當您為資料區定義群組時，您會將這些運算式加入到 **[群組]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="8d613-105">When you define a group for a data region, you add these expressions to the **Group** properties.</span></span> <span data-ttu-id="8d613-106">如需詳細資訊，請參閱 [在資料區中加入或刪除群組 &#40;報表產生器及 SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="8d613-106">For more information, see [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="8d613-107">若要合併根據簡單欄位運算式的兩個或多個群組，請將每一個欄位加入到群組定義中的群組運算式清單。</span><span class="sxs-lookup"><span data-stu-id="8d613-107">To merge two or more groups that are based on simple field expressions, add each field to the group expressions list in the group definition.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="examples-of-group-expressions"></a><span data-ttu-id="8d613-108">群組運算式的範例</span><span class="sxs-lookup"><span data-stu-id="8d613-108">Examples of Group Expressions</span></span>  
 <span data-ttu-id="8d613-109">下表提供您可用來定義群組的群組運算式範例。</span><span class="sxs-lookup"><span data-stu-id="8d613-109">The following table provides examples of group expressions that you can use to define a group.</span></span>  
  
|<span data-ttu-id="8d613-110">描述</span><span class="sxs-lookup"><span data-stu-id="8d613-110">Description</span></span>|<span data-ttu-id="8d613-111">運算是</span><span class="sxs-lookup"><span data-stu-id="8d613-111">Expression</span></span>|  
|-----------------|----------------|  
|<span data-ttu-id="8d613-112">依 `Region` 欄位分組。</span><span class="sxs-lookup"><span data-stu-id="8d613-112">Group by the `Region` field.</span></span>|`=Fields!Region.Value`|  
|<span data-ttu-id="8d613-113">依姓名分組。</span><span class="sxs-lookup"><span data-stu-id="8d613-113">Group by last name and first name.</span></span>|`=Fields!LastName.Value`<br /><br /> `=Fields!FirstName.Value`|  
|<span data-ttu-id="8d613-114">依姓氏的第一個字母分組。</span><span class="sxs-lookup"><span data-stu-id="8d613-114">Group by the first letter of the last name.</span></span>|`=Fields!LastName.Value.Substring(0,1)`|  
|<span data-ttu-id="8d613-115">依使用者選取的參數分組。</span><span class="sxs-lookup"><span data-stu-id="8d613-115">Group by parameter, based on user selection.</span></span><br /><br /> <span data-ttu-id="8d613-116">在此範例中， `GroupBy` 參數必須根據提供有效分組選擇的可用值清單。</span><span class="sxs-lookup"><span data-stu-id="8d613-116">In this example, the parameter `GroupBy` must be based on an available values list that provides a valid choice to group on.</span></span>|`=Fields(Parameters!GroupBy.Value).Value`|  
|<span data-ttu-id="8d613-117">依三個不同的年齡範圍分組：</span><span class="sxs-lookup"><span data-stu-id="8d613-117">Group by three separate age ranges:</span></span><br /><br /> <span data-ttu-id="8d613-118">「21 歲以下」、「21 歲到 50 歲之間」及「超過 50 歲」</span><span class="sxs-lookup"><span data-stu-id="8d613-118">"Under 21", "Between 21 and 50", and "Over 50".</span></span>|`=IIF(First(Fields!Age.Value)<21,"Under 21",(IIF(First(Fields!Age.Value)>=21 AND First(Fields!Age.Value)<=50,"Between 21 and 50","Over 50")))`|  
|<span data-ttu-id="8d613-119">依多個年齡範圍分組。</span><span class="sxs-lookup"><span data-stu-id="8d613-119">Group by many age ranges.</span></span> <span data-ttu-id="8d613-120">此範例會示範可針對下列範圍傳回字串的自訂程式碼 (以 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET 所撰寫)：</span><span class="sxs-lookup"><span data-stu-id="8d613-120">This example shows custom code, written in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET, that returns a string for the following ranges:</span></span><br /><br /> <span data-ttu-id="8d613-121">25 歲或 25 歲以下</span><span class="sxs-lookup"><span data-stu-id="8d613-121">25 or Under</span></span><br /><br /> <span data-ttu-id="8d613-122">26 歲到 50 歲</span><span class="sxs-lookup"><span data-stu-id="8d613-122">26 to 50</span></span><br /><br /> <span data-ttu-id="8d613-123">51 歲到 75 歲</span><span class="sxs-lookup"><span data-stu-id="8d613-123">51 to 75</span></span><br /><br /> <span data-ttu-id="8d613-124">超過 75 歲</span><span class="sxs-lookup"><span data-stu-id="8d613-124">Over 75</span></span>|`=Code.GetRangeValueByAge(Fields!Age.Value)`<br /><br /> <span data-ttu-id="8d613-125">自訂程式碼：</span><span class="sxs-lookup"><span data-stu-id="8d613-125">Custom code:</span></span><br /><br /> `Function GetRangeValueByAge(ByVal age As Integer) As String`<br /><br /> `Select Case age`<br /><br /> `Case 0 To 25`<br /><br /> `GetRangeValueByByAge = "25 or Under"`<br /><br /> `Case 26 To 50`<br /><br /> `GetRangeValueByByAge = "26 to 50"`<br /><br /> `Case 51 to 75`<br /><br /> `GetRangeValueByByAge = "51 to 75"`<br /><br /> `Case Else`<br /><br /> `GetRangeValueByByAge = "Over 75"`<br /><br /> `End Select`<br /><br /> `Return GetRangeValueByByAge`<br /><br /> `End Function`|  
  
## <a name="see-also"></a><span data-ttu-id="8d613-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d613-126">See Also</span></span>  
 <span data-ttu-id="8d613-127">[篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8d613-127">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8d613-128">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8d613-128">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8d613-129">報表設計師中運算式的自訂程式碼及組件參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8d613-129">Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;</span></span>](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)  
  
  
