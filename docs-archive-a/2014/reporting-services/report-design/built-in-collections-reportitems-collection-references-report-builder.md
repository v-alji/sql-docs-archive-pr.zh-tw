---
title: ReportItems 集合參考 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: edc0c75f-0530-4e6d-85aa-3385301bfd00
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 61c89002adafb030288535debfe72de061945640
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686830"
---
# <a name="reportitems-collection-references-report-builder-and-ssrs"></a><span data-ttu-id="522f0-102">ReportItems 集合參考 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="522f0-102">ReportItems Collection References (Report Builder and SSRS)</span></span>
  <span data-ttu-id="522f0-103">`ReportItems` 內建集合是報表項目的文字方塊集合，例如，報表設計介面上的資料區或文字方塊列。</span><span class="sxs-lookup"><span data-stu-id="522f0-103">The `ReportItems` built-in collection is the set of text boxes from report items such as rows of a data region or text boxes on the report design surface.</span></span> <span data-ttu-id="522f0-104">`ReportItems` 集合包含在頁首、頁尾或報表主體目前範圍中的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="522f0-104">The `ReportItems` collection includes text boxes that are in the current scope of a page header, page footer, or report body.</span></span> <span data-ttu-id="522f0-105">這個集合是在執行階段由報表處理器和報表轉譯器而決定。</span><span class="sxs-lookup"><span data-stu-id="522f0-105">This collection is determined at run time by the report processor and the report renderer.</span></span> <span data-ttu-id="522f0-106">隨著報表處理器連續地將報表資料和報表項目配置元素結合為報表的使用者檢視頁面，目前的範圍也會變更。</span><span class="sxs-lookup"><span data-stu-id="522f0-106">The current scope changes as the report processor successively combines report data and the report item layout elements as the user views pages of a report.</span></span> <span data-ttu-id="522f0-107">您可以使用 `ReportItems` 內建集合來產生字典樣式的頁首，以在每個頁面上顯示第一個及最後一個項目。</span><span class="sxs-lookup"><span data-stu-id="522f0-107">You can use the `ReportItems` built-in collection to produce dictionary-style page headers that show the first and last items on each page.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-the-reportitems-value-property"></a><span data-ttu-id="522f0-108">使用 ReportItems 值屬性</span><span class="sxs-lookup"><span data-stu-id="522f0-108">Using the ReportItems Value Property</span></span>  
 <span data-ttu-id="522f0-109">`ReportItems` 集合內的項目只有一個屬性：Value。</span><span class="sxs-lookup"><span data-stu-id="522f0-109">Items within the `ReportItems` collection have only one property: Value.</span></span> <span data-ttu-id="522f0-110">`ReportItems` 項目的值可用來顯示或計算報表中其他欄位的資料。</span><span class="sxs-lookup"><span data-stu-id="522f0-110">The value for a `ReportItems` item can be used to display or calculate data from another field in the report.</span></span> <span data-ttu-id="522f0-111">若要存取目前文字方塊的值，您可以使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 內建全域 Me.Value，或是只使用 Value。</span><span class="sxs-lookup"><span data-stu-id="522f0-111">To access the value of the current text box, you can use the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] built-in global Me.Value or simply Value.</span></span> <span data-ttu-id="522f0-112">在報表函數 (例如，First 和彙總函式) 中，請使用完整的語法。</span><span class="sxs-lookup"><span data-stu-id="522f0-112">In report functions such as First and aggregate functions, use the fully qualified syntax.</span></span>  
  
 <span data-ttu-id="522f0-113">例如：</span><span class="sxs-lookup"><span data-stu-id="522f0-113">For example:</span></span>  
  
-   <span data-ttu-id="522f0-114">這個置於文字方塊中的運算式會顯示名為 `Textbox1` 的 `ReportItem` 文字方塊的值：</span><span class="sxs-lookup"><span data-stu-id="522f0-114">This expression, placed in a text box, displays the value of a `ReportItem` text box named `Textbox1`:</span></span>  
  
     `=ReportItems!Textbox1.Value`  
  
-   <span data-ttu-id="522f0-115">這個運算式會放在 `ReportItem` [文字方塊色彩] 屬性中，當值是 > 0 時，會以黑色顯示文字; 否則，此值會以紅色顯示：</span><span class="sxs-lookup"><span data-stu-id="522f0-115">This expression, placed in a `ReportItem` text box Color property, displays the text in black when the value is > 0; otherwise, the value is displayed in red:</span></span>  
  
     `=IIF(Me.Value > 0,"Black","Red")`  
  
-   <span data-ttu-id="522f0-116">這個放在頁首或頁尾之文字方塊中的運算式，會為名為 `LastName`的文字方塊顯示已轉譯報表之每一頁的第一個值：</span><span class="sxs-lookup"><span data-stu-id="522f0-116">This expression, placed in a text box in the page header or page footer, displays the first value per page of the rendered report, for a text box named `LastName`:</span></span>  
  
     `=First(ReportItems("LastName").Value)`  
  
## <a name="dictionary-style-page-header-expressions"></a><span data-ttu-id="522f0-117">字典樣式頁首運算式</span><span class="sxs-lookup"><span data-stu-id="522f0-117">Dictionary-Style Page Header Expressions</span></span>  
 <span data-ttu-id="522f0-118">您可以建立頁首來顯示頁面上的第一個客戶，以及頁面上的最後一個客戶。</span><span class="sxs-lookup"><span data-stu-id="522f0-118">You can create a page header to display the first customer on the page and the last customer on the page.</span></span> <span data-ttu-id="522f0-119">因為頁首中的文字方塊在運算式中只能參考 `ReportItems` 內建集合一次，所以您需要將兩個文字方塊加入到頁首：一個是第一個客戶的名稱 (`=First(ReportItems!textboxLastName.Value`)，另一個則是最後一個客戶的名稱 (`=Last(ReportItems!textboxLastName.Value`)。</span><span class="sxs-lookup"><span data-stu-id="522f0-119">Because a text box in the page header can only refer to the `ReportItems` built-in collection once in an expression, you need to add two text boxes to the page header: one for the first customer name (`=First(ReportItems!textboxLastName.Value`) and one for the last customer name (`=Last(ReportItems!textboxLastName.Value`).</span></span>  
  
 <span data-ttu-id="522f0-120">在頁首或頁尾區段中，只有目前頁面上的文字方塊才能做為 `ReportItems` 集合的成員。</span><span class="sxs-lookup"><span data-stu-id="522f0-120">In a page header or page footer section, only text boxes on the current page are available as a member of the `ReportItems` collection.</span></span> <span data-ttu-id="522f0-121">例如，如果 `ReportItems!textboxLastName.Value` 參考的文字方塊只會顯示在多頁面資料區域的第一個頁面上，則您會看到第一頁的值，但所有其他的頁面都會顯示 **#Error** ，表示運算式無法評估為已寫入。</span><span class="sxs-lookup"><span data-stu-id="522f0-121">For example, if `ReportItems!textboxLastName.Value` refers to a text box that only appears on the first page for a multipage data region, you see a value for the first page, but all other pages display **#Error** to show the expression could not be evaluated as written.</span></span>  
  
## <a name="scope-for-the-reportitems-collection"></a><span data-ttu-id="522f0-122">ReportItems 集合的範圍</span><span class="sxs-lookup"><span data-stu-id="522f0-122">Scope for the ReportItems Collection</span></span>  
 <span data-ttu-id="522f0-123">在系統處理報表時，每個報表主體或資料區域中的文字方塊都會在其資料集、資料區域和群組關聯的內容中進行評估。</span><span class="sxs-lookup"><span data-stu-id="522f0-123">As the report is processed, each text box in the report body or in a data region is evaluated in the context of its dataset, data region, and group associations.</span></span> <span data-ttu-id="522f0-124">`ReportItems` 集合參考的範圍是目前的範圍或高於目前範圍的任何點。</span><span class="sxs-lookup"><span data-stu-id="522f0-124">The scope for a reference to the `ReportItems` collection is the current scope or any point higher than the current scope.</span></span>  
  
 <span data-ttu-id="522f0-125">例如，在父群組的資料列內的文字方塊所包含的運算式，不得參考子群組資料列中的文字方塊的名稱。</span><span class="sxs-lookup"><span data-stu-id="522f0-125">For example, a text box in a row that is in a parent group must not contain an expression that refers to the name of a text box in a child group row.</span></span> <span data-ttu-id="522f0-126">此類運算式不會解析為報表中的值，因為子資料列文字方塊超出範圍。</span><span class="sxs-lookup"><span data-stu-id="522f0-126">Such an expression does not resolve to a value in the report because the child row text box is out of scope.</span></span> <span data-ttu-id="522f0-127">如需詳細資訊，請參閱 [彙總函式參考 &#40;報表產生器和 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="522f0-127">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="522f0-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="522f0-128">See Also</span></span>  
 <span data-ttu-id="522f0-129">[運算式中的內建集合 &#40;報表產生器及 SSRS&#41;](built-in-collections-in-expressions-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="522f0-129">[Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](built-in-collections-in-expressions-report-builder.md) </span></span>  
 <span data-ttu-id="522f0-130">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="522f0-130">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="522f0-131">[Reporting Services 中的分頁 &#40;報表產生器及 SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="522f0-131">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="522f0-132">篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="522f0-132">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
