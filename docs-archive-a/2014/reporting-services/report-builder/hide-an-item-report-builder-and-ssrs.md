---
title: 隱藏項目 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.visibility.f1
- "10503"
ms.assetid: 9d78f8de-959b-456f-8947-687fa6e2ba91
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 56e834204698369687528c622cf6167a492766f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593838"
---
# <a name="hide-an-item-report-builder-and-ssrs"></a><span data-ttu-id="9548f-102">隱藏項目 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="9548f-102">Hide an Item (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9548f-103">當您想要有條件地根據報表參數或是您所指定的某些其他運算式來隱藏項目時，請設定報表項目的可見性。</span><span class="sxs-lookup"><span data-stu-id="9548f-103">Set the visibility of a report item when you want to conditionally hide an item based on a report parameter or some other expression that you specify.</span></span>

 <span data-ttu-id="9548f-104">您也可以設計報表來允許使用者根據按一下報表中文字方塊的動作來切換報表項目的可見性，例如針對鑽研報表。</span><span class="sxs-lookup"><span data-stu-id="9548f-104">You can also design a report to allow the user to toggle the visibility of report items based on clicking text boxes in the report, for example, for a drilldown report.</span></span> <span data-ttu-id="9548f-105">如需詳細資訊，請參閱 [將展開或摺疊動作加入項目中 &#40;報表產生器及 SSRS&#41;](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9548f-105">For more information, see [Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md).</span></span>

 <span data-ttu-id="9548f-106">下列程序描述如何根據常數或運算式，顯示或隱藏轉譯報表中的報表項目。</span><span class="sxs-lookup"><span data-stu-id="9548f-106">The following procedures describe how to show or hide a report item in a rendered report based on a constant or an expression.</span></span>

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

### <a name="to-hide-a-report-item"></a><span data-ttu-id="9548f-107">隱藏報表項目</span><span class="sxs-lookup"><span data-stu-id="9548f-107">To hide a report item</span></span>

1.  <span data-ttu-id="9548f-108">在報表設計檢視中，以滑鼠右鍵按一下報表項目，然後開啟其 [屬性]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="9548f-108">In report design view, right-click the report item and open its **Properties** page.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="9548f-109">若要選取整個資料表或矩陣資料區，請在資料區中按一下來選取它，以滑鼠右鍵按一下資料列、資料行或角控點，然後按一下 [Tablix 屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9548f-109">To select an entire table or matrix data region, click in the data region to select it, right-click a row, column, or corner handle, and then click **Tablix Properties**.</span></span>

2.  <span data-ttu-id="9548f-110">按一下 [**可見度]。**</span><span class="sxs-lookup"><span data-stu-id="9548f-110">Click **Visibility.**</span></span>

3.  <span data-ttu-id="9548f-111">在 **[一開始執行報表時]** 中，指定當您一開始檢視報表時，是否要隱藏此項目：</span><span class="sxs-lookup"><span data-stu-id="9548f-111">In **When the report is initially run**, specify whether to hide the item when you first view the report:</span></span>

    -   <span data-ttu-id="9548f-112">若要顯示此項目，請按一下 **[顯示]**。</span><span class="sxs-lookup"><span data-stu-id="9548f-112">To display the item, click **Show**.</span></span>

    -   <span data-ttu-id="9548f-113">若要隱藏此項目，請按一下 **[隱藏]**。</span><span class="sxs-lookup"><span data-stu-id="9548f-113">To hide the item, click **Hide**.</span></span>

    -   <span data-ttu-id="9548f-114">若要指定在執行階段評估的運算式，請按一下 [依據運算式顯示或隱藏]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9548f-114">To specify an expression that is evaluated at run-time, click **Show or hide based on an expression**.</span></span> <span data-ttu-id="9548f-115">鍵入運算式或按一下運算式 (**fx**) 按鈕，在 [運算式]\*\*\*\* 對話方塊中建立運算式。</span><span class="sxs-lookup"><span data-stu-id="9548f-115">Type the expression or click the expression (**fx**) button to create the expression in the **Expression** dialog box.</span></span>

        > [!NOTE]
        >  <span data-ttu-id="9548f-116">當您指定可見性的運算式時，會設定報表項目的 Hidden 屬性，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="9548f-116">When you specify an expression for visibility, you are setting the Hidden property of the report item, as shown in the following image.</span></span> <span data-ttu-id="9548f-117">評估之後的運算式會在值為 False 時顯示此報表項目，並在值為 True 時隱藏此報表項目。</span><span class="sxs-lookup"><span data-stu-id="9548f-117">The evaluated expression shows the report item when the value is False, and hides the report item when the value is True.</span></span> 
        > <span data-ttu-id="9548f-118">![Properties_Visibility 對話方塊與隱藏的屬性](../media/hiddenproperty-propertiesvisibility.png "Properties_Visibility 對話方塊與隱藏的屬性")</span><span class="sxs-lookup"><span data-stu-id="9548f-118">![Properties_Visibility dialog and Hidden property](../media/hiddenproperty-propertiesvisibility.png "Properties_Visibility dialog and Hidden property")</span></span>

4.  <span data-ttu-id="9548f-119">按兩次 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="9548f-119">Click **OK** twice.</span></span>

### <a name="to-hide-static-rows-in-a-table-matrix-or-list"></a><span data-ttu-id="9548f-120">隱藏資料表、矩陣或清單中的靜態資料列</span><span class="sxs-lookup"><span data-stu-id="9548f-120">To hide static rows in a table, matrix, or list</span></span>

1.  <span data-ttu-id="9548f-121">在報表設計檢視中，按一下資料表、矩陣或清單來顯示資料列和資料行控點。</span><span class="sxs-lookup"><span data-stu-id="9548f-121">In report design view, click the table, matrix, or list to display the row and column handles.</span></span>

2.  <span data-ttu-id="9548f-122">以滑鼠右鍵按一下資料列控點，然後按一下 [資料列可見性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9548f-122">Right-click the row handle, and then click **Row Visibility**.</span></span> <span data-ttu-id="9548f-123">**[資料列可見性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="9548f-123">The **Row Visibility** dialog box opens.</span></span>

3.  <span data-ttu-id="9548f-124">若要設定可見性，請遵循第一個程序中的步驟 3 和 4。</span><span class="sxs-lookup"><span data-stu-id="9548f-124">To set the visibility, follow steps 3 and 4 in the first procedure.</span></span>

### <a name="to-hide-static-columns-in-a-table-matrix-or-list"></a><span data-ttu-id="9548f-125">若要隱藏資料表、矩陣或清單中的靜態資料行</span><span class="sxs-lookup"><span data-stu-id="9548f-125">To hide static columns in a table, matrix, or list</span></span>

1.  <span data-ttu-id="9548f-126">在 [設計] 檢視中，選取資料表、矩陣或清單來顯示資料列和資料行控點。</span><span class="sxs-lookup"><span data-stu-id="9548f-126">In Design view, select the table, matrix, or list to display the row and column handles.</span></span>

2.  <span data-ttu-id="9548f-127">以滑鼠右鍵按一下資料行控點，然後按一下 [資料行可見性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9548f-127">Right-click the column handle, and then click **Column Visibility**.</span></span>

3.  <span data-ttu-id="9548f-128">在 **[資料行可見性]** 對話方塊中，遵循第一個程序中的步驟 3 和 4。</span><span class="sxs-lookup"><span data-stu-id="9548f-128">In the **Column Visibility** dialog box, follow steps 3 and 4 in the first procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="9548f-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9548f-129">See Also</span></span>
 <span data-ttu-id="9548f-130">[深入分析動作 &#40;報表產生器和 ssrs&#41;](../report-design/drilldown-action-report-builder-and-ssrs.md) [將展開或折迭動作新增至 &#40;報表產生器和](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)ssrs&#41;[運算式範例 &#40;報表產生器和 ssrs](../report-design/expression-examples-report-builder-and-ssrs.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="9548f-130">[Drilldown Action &#40;Report Builder and SSRS&#41;](../report-design/drilldown-action-report-builder-and-ssrs.md) [Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) [Expression Examples &#40;Report Builder and SSRS&#41;](../report-design/expression-examples-report-builder-and-ssrs.md)</span></span>


