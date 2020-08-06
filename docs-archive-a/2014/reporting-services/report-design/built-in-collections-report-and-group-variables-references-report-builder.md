---
title: 報表和群組變數集合參考 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10404"
- sql12.rtp.rptdesigner.categorygroupproperties.variables.f1
- "10083"
- sql12.rtp.rptdesigner.seriesgroupproperties.variables.f1
- sql12.rtp.rptdesigner.reportproperties.variables.f1
- sql12.rtp.rptdesigner.groupproperties.variables.f1
- "10292"
- "10412"
ms.assetid: 4be5b463-3ce2-483d-a3c6-dae752cb543e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 41dd652bf39721b13801131a5ec268495edf9d29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686831"
---
# <a name="report-and-group-variables-collections-references-report-builder-and-ssrs"></a><span data-ttu-id="5e9d3-102">報表和群組變數集合參考 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="5e9d3-102">Report and Group Variables Collections References (Report Builder and SSRS)</span></span>
  <span data-ttu-id="5e9d3-103">當您要進行的複雜計算是在報表的運算式中使用一次以上時，建議您建立一個變數。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-103">When you have a complex calculation that is used more than once in expressions in a report, you might want to create a variable.</span></span> <span data-ttu-id="5e9d3-104">您可以建立報表變數或群組變數。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-104">You can create a report variable or a group variable.</span></span> <span data-ttu-id="5e9d3-105">變數名稱在報表中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-105">Variable names must be unique in a report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-variables"></a><span data-ttu-id="5e9d3-106">報表變數</span><span class="sxs-lookup"><span data-stu-id="5e9d3-106">Report Variables</span></span>  
 <span data-ttu-id="5e9d3-107">報表變數可用來保存與時間相依之計算的值，例如貨幣匯率或時間戳記，或多次參考之複雜計算的值。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-107">Use a report variable to hold a value for time-dependent calculations, such as currency rates or time stamps, or for a complex calculation that is referenced multiple times.</span></span> <span data-ttu-id="5e9d3-108">根據預設，報表變數只要計算一次，就可以供整份報表的運算式使用。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-108">By default, a report variable is calculated once and can be used in expressions throughout a report.</span></span> <span data-ttu-id="5e9d3-109">報表變數預設是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-109">Report variables are read-only by default.</span></span> <span data-ttu-id="5e9d3-110">您可以變更預設值，將報表變數啟用為讀寫。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-110">You can change the default to enable a report variable as read-write.</span></span> <span data-ttu-id="5e9d3-111">報表變數中的值會在整個工作階段中保留，直到再次處理報表。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-111">The value in a report variable is preserved throughout a session, until the report is processed again.</span></span>  
  
 <span data-ttu-id="5e9d3-112">若要新增報表變數，請開啟 [報表屬性]  對話方塊、按一下 [變數]  ，然後提供名稱及值。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-112">To add a report variable, open the **ReportProperties** dialog box, click **Variables**, and provide a name and a value.</span></span> <span data-ttu-id="5e9d3-113">名稱是區分大小寫、以字母為開頭而且沒有任何空格的字串。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-113">Names are case-sensitive strings that begin with a letter and have no spaces.</span></span> <span data-ttu-id="5e9d3-114">名稱可以包含字母、數字或底線 (_)。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-114">A name can include letters, numbers, or underscores (_).</span></span>  
  
 <span data-ttu-id="5e9d3-115">若要參考運算式中的變數，請使用全域集合語法，例如 `=Variables!CustomTimeStamp.Value`。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-115">To refer to the variable in an expression, use the global collection syntax, for example, `=Variables!CustomTimeStamp.Value`.</span></span> <span data-ttu-id="5e9d3-116">此值會在設計介面的文字方塊中顯示為 `<<Expr>>`。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-116">On the design surface, the value appears in a text box as `<<Expr>>`.</span></span>  
  
 <span data-ttu-id="5e9d3-117">您可以透過以下方式來使用報表變數：</span><span class="sxs-lookup"><span data-stu-id="5e9d3-117">You can use report variables in the following ways:</span></span>  
  
-   <span data-ttu-id="5e9d3-118">**唯讀使用** ：設定一次某個值，以建立報表工作階段的常數，例如，用來建立時間戳記。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-118">**Read-only use** Set a value once to create a constant for the report session, for example, to create a time stamp.</span></span>  
  
     <span data-ttu-id="5e9d3-119">文字方塊中的運算式會在使用者逐頁檢視報表時視需要進行評估；因此，動態值 (例如，包含 `Now()` 函式的運算式，此函式會傳回當日時間) 可能會在您向後一頁之後，使用 [上一頁]  按鈕返回時傳回不同的值。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-119">Because expressions in text boxes are evaluated on-demand as a user pages through a report, dynamic values (for example, an expression that includes the `Now()` function, which returns the time of day) can return different values if you page forward and backward by using the **Back** button.</span></span> <span data-ttu-id="5e9d3-120">您可藉由將報表變數的值設定為運算式 `=Now()`，然後將該變數加入至您的運算式，來確保在整個報表處理時都會使用相同的值。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-120">By setting a the value of a report variable to the expression `=Now()`, and then adding the variable to your expression, you ensure the same value is used throughout report processing.</span></span>  
  
-   <span data-ttu-id="5e9d3-121">**讀寫使用** ：設定一次某個值，然後在報表工作階段中序列化該值。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-121">**Read-write use** Set a value once and serialize the value within a report session.</span></span> <span data-ttu-id="5e9d3-122">變數的讀寫選項會比在報表定義的程式碼區塊中使用靜態變數提供更好的替代方案。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-122">The read-write option for variables provides a better alternative than using a static variable in the Code block in the report definition.</span></span>  
  
     <span data-ttu-id="5e9d3-123">當您清除變數的**唯讀**選項時，變數的可寫入屬性會設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-123">When you clear the **Read-Only** option for a variable, the Writable property for the variable is set to `true`.</span></span> <span data-ttu-id="5e9d3-124">若要更新運算式的值，請使用 SetValue 方法，例如， `=Variables!MyVariable.SetValue("123")`。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-124">To update the value from an expression, use the SetValue method, for example, `=Variables!MyVariable.SetValue("123")`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5e9d3-125">您無法控制報表處理器初始化變數，或評估更新變數之運算式的時間。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-125">You cannot control when the report processor initializes a variable or evaluates an expression that updates a variable.</span></span> <span data-ttu-id="5e9d3-126">系統未定義變數初始化的執行順序。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-126">The order of execution for variable initialization is undefined.</span></span>  
  
 <span data-ttu-id="5e9d3-127">如需有關工作階段的詳細資訊，請參閱＜ [Previewing Reports in Report Builder](../report-builder/previewing-reports-in-report-builder.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-127">For more information about sessions, see [Previewing Reports in Report Builder](../report-builder/previewing-reports-in-report-builder.md).</span></span>  
  
## <a name="group-variables"></a><span data-ttu-id="5e9d3-128">群組變數</span><span class="sxs-lookup"><span data-stu-id="5e9d3-128">Group Variables</span></span>  
 <span data-ttu-id="5e9d3-129">群組變數可用來計算一次群組範圍內的複雜運算式。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-129">Use a group variable to calculate a complex expression once in the scope of a group.</span></span> <span data-ttu-id="5e9d3-130">群組變數只有在群組及其子群組的範圍內有效。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-130">A group variable is valid only in the scope of the group and its child groups.</span></span>  
  
 <span data-ttu-id="5e9d3-131">例如，假設資料區域針對不同稅率類別目錄的貨品顯示存貨資料，而您想要為每個類別目錄套用不同的稅率。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-131">For example, suppose a data region displays inventory data for items that are in different tax categories and you want to apply different tax rates for each category.</span></span> <span data-ttu-id="5e9d3-132">您會根據類別目錄將資料分組，並在父群組上定義 *Tax* 變數。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-132">You would group the data on Category and define a *Tax* variable on the parent group.</span></span> <span data-ttu-id="5e9d3-133">然後針對每個稅率類別目錄定義 *ItemTax* 的群組變數，並將每個不同的類別目錄子群組指派給正確的群組變數。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-133">Then you would define a group variable for *ItemTax* for each tax category and assign each of the different Category subgroups to the correct group variable.</span></span> <span data-ttu-id="5e9d3-134">例如：</span><span class="sxs-lookup"><span data-stu-id="5e9d3-134">For example:</span></span>  
  
-   <span data-ttu-id="5e9d3-135">對於以 `[Category]`為基礎的父群組，定義具有 *值的* Tax `[Tax]`變數。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-135">For the parent group based on `[Category]`, define the variable *Tax* with a value `[Tax]`.</span></span> <span data-ttu-id="5e9d3-136">假設類別目錄值為 Food 和 Clothing。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-136">Assume the category values are Food and Clothing.</span></span>  
  
-   <span data-ttu-id="5e9d3-137">對於以 `[Subcategory]`為基礎的子群組，則將 *ItemsTax* 變數定義為 `=Variables!Tax.Value * Sum(Fields!Price.Value)`。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-137">For the child group based on `[Subcategory]`, define the variable *ItemsTax* as `=Variables!Tax.Value * Sum(Fields!Price.Value)`.</span></span> <span data-ttu-id="5e9d3-138">假設 Food 類別目錄的子類別目錄值為 Beverages 和 Bread。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-138">Assume the subcategory values for the category Food are Beverages and Bread.</span></span> <span data-ttu-id="5e9d3-139">假設 Clothing 的子類別目錄值為 Shirts 和 Hats。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-139">Assume the subcategory values for Clothing are Shirts and Hats.</span></span>  
  
-   <span data-ttu-id="5e9d3-140">針對子群組中資料列的文字方塊，加入 `=Variables!ItemsTax.Value`運算式。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-140">For a text box in a row in the child group, add the expression `=Variables!ItemsTax.Value`.</span></span>  
  
     <span data-ttu-id="5e9d3-141">該文字方塊會使用 Food 稅率顯示 Beverages 和 Bread 的總稅額，而使用 Clothing 稅率顯示 Shirts 和 Hats 的總稅額。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-141">The text box displays the total tax for Beverages and Bread using the Food tax and for Shirts and Hats using the Clothing tax.</span></span>  
  
 <span data-ttu-id="5e9d3-142">若要加入群組變數，請開啟 **[Tablix 群組屬性]** 對話方塊，按一下 **[變數]** ，然後提供名稱及值。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-142">To add a group variable, open the **Tablix Group Properties** dialog box, click **Variables**, and provide a name and a value.</span></span> <span data-ttu-id="5e9d3-143">群組變數會針對每個唯一的群組值計算一次。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-143">The group variable is calculated once per unique group value.</span></span>  
  
 <span data-ttu-id="5e9d3-144">若要參考運算式中的變數，請使用全域集合語法，例如 `=Variables!GroupDescription.Value`。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-144">To refer to the variable in an expression, use the global collection syntax, for example, `=Variables!GroupDescription.Value`.</span></span> <span data-ttu-id="5e9d3-145">此值會在設計介面的文字方塊中顯示為 `<<Expr>>`。</span><span class="sxs-lookup"><span data-stu-id="5e9d3-145">On the design surface, the value appears in a text box as `<<Expr>>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e9d3-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e9d3-146">See Also</span></span>  
 <span data-ttu-id="5e9d3-147">[篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5e9d3-147">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5e9d3-148">[運算式中的內建集合 &#40;報表產生器及 SSRS&#41;](built-in-collections-in-expressions-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="5e9d3-148">[Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](built-in-collections-in-expressions-report-builder.md) </span></span>  
 [<span data-ttu-id="5e9d3-149">運算式範例 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5e9d3-149">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
