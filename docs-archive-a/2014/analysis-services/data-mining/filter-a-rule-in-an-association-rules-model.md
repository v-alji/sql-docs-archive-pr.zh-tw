---
title: 篩選關聯規則模型中的規則 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- filtering rules [Analysis Services]
- Mining Model Viewer [Analysis Services], rules
- Rules Viewer
ms.assetid: 26cdba5b-5bf1-439e-80a3-8759774e918b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c904713acc6eaf132e7cb1195186165f21d971a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597453"
---
# <a name="filter-a-rule-in-an-association-rules-model"></a><span data-ttu-id="e01d5-102">篩選關聯規則模型中的規則</span><span class="sxs-lookup"><span data-stu-id="e01d5-102">Filter a Rule in an Association Rules Model</span></span>
  <span data-ttu-id="e01d5-103">您可以在關聯模型中使用篩選，將結果限制為您所感興趣的關聯。</span><span class="sxs-lookup"><span data-stu-id="e01d5-103">You can use filtering with association models to restrict the results to just the associations that interest you.</span></span> <span data-ttu-id="e01d5-104">例如，您可以篩選規則，只顯示包含特定產品的規則。</span><span class="sxs-lookup"><span data-stu-id="e01d5-104">For example, you might filter the rules to show only those that include a specific product.</span></span>  
  
 <span data-ttu-id="e01d5-105">在資料採礦設計師中，您可以使用 **關聯規則檢視器 [規則]**[!INCLUDE[msCoName](../../includes/msconame-md.md)] 索引標籤上的控制項來篩選顯示的規則。</span><span class="sxs-lookup"><span data-stu-id="e01d5-105">In Data Mining Designer, you use the controls on the **Rules** tab of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer to filter the rules that are displayed.</span></span>  <span data-ttu-id="e01d5-106">您還可以對模型建立查詢，只查看包含特定值的項目集。</span><span class="sxs-lookup"><span data-stu-id="e01d5-106">You can also create a query on the model to see only itemset that contains a particular value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e01d5-107">這個選項僅適用於使用 Microsoft 關聯分析演算法所建立的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="e01d5-107">This option is available only for mining models that have been created by using the Microsoft Association Algorithm.</span></span>  
  
### <a name="filter-a-rule-in-an-association-model"></a><span data-ttu-id="e01d5-108">篩選關聯模型中的規則</span><span class="sxs-lookup"><span data-stu-id="e01d5-108">Filter a rule in an association model</span></span>  
  
1.  <span data-ttu-id="e01d5-109">使用 **[關聯規則檢視器]** 開啟此採礦模型。</span><span class="sxs-lookup"><span data-stu-id="e01d5-109">Open the mining model by using the **Association Rules Viewer**.</span></span> <span data-ttu-id="e01d5-110">若要在 SQL Server Management Studio 中進行這項處理，請以滑鼠右鍵按一下模型名稱，然後選取 **[瀏覽]**。</span><span class="sxs-lookup"><span data-stu-id="e01d5-110">To do this in SQL Server Management Studio, right click the model name and select **Browse**.</span></span> <span data-ttu-id="e01d5-111">若要在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中進行這項處理，請按兩下包含此模型的採礦結構，然後按一下 [資料採礦設計師]\*\*\*\* 的 [採礦模型檢視器]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e01d5-111">To do this in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], double-click the mining structure that contains the model, and then click the **Mining Model Viewer** tab of **Data Mining Designer**.</span></span>  
  
2.  <span data-ttu-id="e01d5-112">按一下 **[關聯規則檢視器]** 的 **[規則]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e01d5-112">Click the **Rules** tab of the **Association Rules Viewer**.</span></span>  
  
3.  <span data-ttu-id="e01d5-113">在 **[篩選規則]** 方塊中輸入規則條件。</span><span class="sxs-lookup"><span data-stu-id="e01d5-113">Type a rule condition into the **Filter Rule** box.</span></span> <span data-ttu-id="e01d5-114">例如，規則條件可能是 "Bike Stand"，這也會傳回 "Bike Stands"。</span><span class="sxs-lookup"><span data-stu-id="e01d5-114">For example, a rule condition might be "Bike Stand", which also returns "Bike Stands".</span></span>  
  
     <span data-ttu-id="e01d5-115">**[篩選規則]** 文字方塊會支援 .NET 語言所定義的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="e01d5-115">The **Filter Rule** text box supports regular expressions as defined by the .NET language.</span></span> <span data-ttu-id="e01d5-116">因此，您可以使用類似以下的運算式： `((.Helmets.*Fenders.*)|(.*Fenders.*Helmets.*))`。</span><span class="sxs-lookup"><span data-stu-id="e01d5-116">Therefore, you can use expressions such as the following: `((.Helmets.*Fenders.*)|(.*Fenders.*Helmets.*))`.</span></span> <span data-ttu-id="e01d5-117">此運算式會傳回包含 Helmets 和 Fenders 字 (順序不限) 之屬性的任何項目集。</span><span class="sxs-lookup"><span data-stu-id="e01d5-117">This expression would return any itemsets that include attributes with the words Helmets and Fenders, in any order.</span></span>  
  
4.  <span data-ttu-id="e01d5-118">在 **[最小機率]** 中，增加機率的值來查看更少的規則，或是降低此值來查看更多的規則。</span><span class="sxs-lookup"><span data-stu-id="e01d5-118">For **Minimum probability**, increase the value of probability to see fewer rules, or decrease the value to see more rules.</span></span>  
  
5.  <span data-ttu-id="e01d5-119">在 **[最低重要性]** 中，增加重要性的值來查看更少的規則，或是降低此值來查看更多的規則。</span><span class="sxs-lookup"><span data-stu-id="e01d5-119">For **Minimum importance**, increase the value of importance to see fewer rules, or decrease the value to see more rules.</span></span>  
  
6.  <span data-ttu-id="e01d5-120">在 **[顯示]** 中，選取下列其中一個選項： **[顯示屬性名稱和值]**、 **[只顯示屬性名稱]** 或 **[只顯示屬性值]**。</span><span class="sxs-lookup"><span data-stu-id="e01d5-120">For **Show**, select one of the following options: **Show attribute name and value**, **Show attribute name only**, or **Show attribute value only**.</span></span>  
  
7.  <span data-ttu-id="e01d5-121">在 **[最大資料列數]** 中，增加這個值來提高符合指定之條件的總規則數，或是降低這個值來限制傳回的規則數。</span><span class="sxs-lookup"><span data-stu-id="e01d5-121">For **Maximum rows**, increase the value to increase the total number of rules that meet the specified conditions, or decrease the value to limit the number of rules returned.</span></span> <span data-ttu-id="e01d5-122">規則會依據機率來排序，所以您可能會為了機率或重要性而移除符合指定之條件的其他規則。</span><span class="sxs-lookup"><span data-stu-id="e01d5-122">Rules are ordered by probability, so you might eliminate additional rules that meet the specified conditions for probability or importance.</span></span>  
  
8.  <span data-ttu-id="e01d5-123">選取或取消選取 **[顯示完整名稱]** 核取方塊，以切換規則名稱顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="e01d5-123">Select or deselect the **Show long name** check box to toggle the way that the rules names are displayed.</span></span>  
  
     <span data-ttu-id="e01d5-124">現在規則經過篩選後，只會顯示包含指示之項目的規則。</span><span class="sxs-lookup"><span data-stu-id="e01d5-124">The rules are now filtered to only display rules that contain the indicated item.</span></span> <span data-ttu-id="e01d5-125">篩選條件會套用到屬性值，不論是在規則分隔符號 "->" 之前或之後。</span><span class="sxs-lookup"><span data-stu-id="e01d5-125">The filter condition applies to attribute values either before or after the rule delimiter, "->".</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e01d5-126">此檢視器會根據採礦模型的查詢來快取最初的規則清單，而且除非您設定最大資料列數、機率、重要性或完整名稱的顯示來變更此查詢的條件，否則此檢視器不會重新整理規則的清單。</span><span class="sxs-lookup"><span data-stu-id="e01d5-126">The viewer caches the initial list of rules, based on a query to the mining model, and does not refresh the list of rules unless you change the conditions of the query by setting the maximum rows, the probability, importance, or the display of long names.</span></span> <span data-ttu-id="e01d5-127">因此，如果您輸入一個條件，而顯示畫面並未立即重新整理，您可以選取 **[顯示完整名稱]** 核取方塊然後再將它取消選取，以強制檢視器重新整理資料。</span><span class="sxs-lookup"><span data-stu-id="e01d5-127">Therefore, if you type a condition and the display does not immediately refresh, you can force the viewer to refresh the data by selecting and then deselecting the **Show long names** check box.</span></span>  
  
### <a name="create-a-query-on-the-itemsets-in-an-association-model"></a><span data-ttu-id="e01d5-128">對關聯模型中的項目集建立查詢</span><span class="sxs-lookup"><span data-stu-id="e01d5-128">Create a query on the itemsets in an association model</span></span>  
  
-   [<span data-ttu-id="e01d5-129">關聯模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="e01d5-129">Association Model Query Examples</span></span>](association-model-query-examples.md)  
  
## <a name="see-also"></a><span data-ttu-id="e01d5-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e01d5-130">See Also</span></span>  
 <span data-ttu-id="e01d5-131">[採礦模型檢視器工作和操作說明](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="e01d5-131">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="e01d5-132">[使用 Microsoft 關聯規則檢視器流覽模型](browse-a-model-using-the-microsoft-association-rules-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="e01d5-132">[Browse a Model Using the Microsoft Association Rules Viewer](browse-a-model-using-the-microsoft-association-rules-viewer.md) </span></span>  
 [<span data-ttu-id="e01d5-133">第 3 課：建立購物籃狀況 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="e01d5-133">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
  
