---
title: 格式化文字方塊中的文字 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: df0794b5-96b0-4034-bd17-1be7f31e29db
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 522bc420f77b2e5e9d2163c28d3d688b7c47883c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594387"
---
# <a name="format-text-in-a-text-box-report-builder-and-ssrs"></a><span data-ttu-id="f96e6-102">格式化文字方塊中的文字 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f96e6-102">Format Text in a Text Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f96e6-103">您可以在文件方塊中，單獨地對文字任何一部分進行格式化，並且在同一個文字方塊中，混合使用預留文字與靜態文字。</span><span class="sxs-lookup"><span data-stu-id="f96e6-103">You can format any part of the text within a text box independently, and mix placeholder text and static text in one text box.</span></span> <span data-ttu-id="f96e6-104">混合格式與加入預留位置文字的功能可以讓您針對報表中的文字建立合併列印或範本。</span><span class="sxs-lookup"><span data-stu-id="f96e6-104">This ability to mix formats and add placeholder text enables you to create mail merges or templates for text in your report.</span></span> <span data-ttu-id="f96e6-105">您可以使用預留位置來個別定義和格式化任何運算式。</span><span class="sxs-lookup"><span data-stu-id="f96e6-105">Any expression can be defined and formatted separately using a placeholder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-combine-multiple-formats-in-a-text-box"></a><span data-ttu-id="f96e6-106">若要在文字方塊中結合多種格式</span><span class="sxs-lookup"><span data-stu-id="f96e6-106">To combine multiple formats in a text box</span></span>  
  
1.  <span data-ttu-id="f96e6-107">在 **[插入]** 索引標籤上，按一下 **[文字方塊]** 。</span><span class="sxs-lookup"><span data-stu-id="f96e6-107">On the **Insert** tab, click **Text Box**.</span></span> <span data-ttu-id="f96e6-108">按一下設計介面，然後拖曳滑鼠來建立一個所需大小的方塊。</span><span class="sxs-lookup"><span data-stu-id="f96e6-108">Click the design surface, and then drag to create a box that is the size you want.</span></span>  
  
2.  <span data-ttu-id="f96e6-109">在文字方塊內部，選取您想要格式化的文字。</span><span class="sxs-lookup"><span data-stu-id="f96e6-109">Inside the text box, select the text you want to format.</span></span>  
  
3.  <span data-ttu-id="f96e6-110">以滑鼠右鍵按一下選取的文字，然後按一下 [文字屬性]  。</span><span class="sxs-lookup"><span data-stu-id="f96e6-110">Right-click the selected text, and click **Text Properties**.</span></span>  
  
4.  <span data-ttu-id="f96e6-111">設定格式選項。</span><span class="sxs-lookup"><span data-stu-id="f96e6-111">Set formatting options.</span></span> <span data-ttu-id="f96e6-112">例如，在 [一般]  索引標籤上：</span><span class="sxs-lookup"><span data-stu-id="f96e6-112">For example, on the **General** tab:</span></span>  
  
    -   <span data-ttu-id="f96e6-113">**工具提示** ：輸入文字或評估為工具提示的運算式。</span><span class="sxs-lookup"><span data-stu-id="f96e6-113">**Tooltip** Type text or an expression that evaluates to a ToolTip.</span></span> <span data-ttu-id="f96e6-114">當使用者將滑鼠指標停留在報表的項目上方時，便會出現工具提示。</span><span class="sxs-lookup"><span data-stu-id="f96e6-114">The ToolTip appears when the user pauses the pointer over the item in a report</span></span>  
  
    -   <span data-ttu-id="f96e6-115">**標記類型** ：選取一個選項，指示要如何轉譯選取的文字：</span><span class="sxs-lookup"><span data-stu-id="f96e6-115">**Markup type** Select an option to indicate how the selected text will be rendered:</span></span>  
  
         <span data-ttu-id="f96e6-116">**純文字** ：將選取的文字顯示為簡單的文字。</span><span class="sxs-lookup"><span data-stu-id="f96e6-116">**Plain Text** Display the selected text as simple text.</span></span> <span data-ttu-id="f96e6-117">HTML 將視為常值文字。</span><span class="sxs-lookup"><span data-stu-id="f96e6-117">HTML will be treated as literal text.</span></span>  
  
         <span data-ttu-id="f96e6-118">**HTML**  將選取的文字顯示為 HTML。</span><span class="sxs-lookup"><span data-stu-id="f96e6-118">**HTML**  Display the selected text as HTML.</span></span> <span data-ttu-id="f96e6-119">如果預留位置的運算式值包含有效的 HTML 標記，這些標記將會轉譯為 HTML。</span><span class="sxs-lookup"><span data-stu-id="f96e6-119">If the expression value of the placeholder contains valid HTML tags, these tags will be rendered as HTML.</span></span> <span data-ttu-id="f96e6-120">如需詳細資訊，請參閱[將 HTML 匯入至報表 &#40;報表產生器及 SSRS&#41;](importing-html-into-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f96e6-120">For more information, see [Importing HTML into a Report &#40;Report Builder and SSRS&#41;](importing-html-into-a-report-report-builder-and-ssrs.md).</span></span>  
  
5.  <span data-ttu-id="f96e6-121">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="f96e6-121">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="f96e6-122">針對您想要格式化的其餘文字，重複步驟 2 至 5。</span><span class="sxs-lookup"><span data-stu-id="f96e6-122">Repeat steps 2 through 5 for the remaining text you want to format.</span></span>  
  
### <a name="to-format-text-and-placeholders-differently-in-the-same-text-box"></a><span data-ttu-id="f96e6-123">若要在相同的文字方塊中使用不同的方式格式化文字和預留位置</span><span class="sxs-lookup"><span data-stu-id="f96e6-123">To format text and placeholders differently in the same text box</span></span>  
  
1.  <span data-ttu-id="f96e6-124">在 **[插入]** 索引標籤上，按一下 **[清單]** 。</span><span class="sxs-lookup"><span data-stu-id="f96e6-124">On the **Insert** tab, click **List**.</span></span> <span data-ttu-id="f96e6-125">按一下設計介面，然後拖曳滑鼠來建立一個所需大小的方塊。</span><span class="sxs-lookup"><span data-stu-id="f96e6-125">Click the design surface, and then drag to create a box that is the size you want.</span></span> <span data-ttu-id="f96e6-126">**[資料集屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f96e6-126">The **Dataset Properties** dialog box opens.</span></span> <span data-ttu-id="f96e6-127">您可以使用共用資料集或在報表中內嵌資料集。</span><span class="sxs-lookup"><span data-stu-id="f96e6-127">You can use a shared dataset or a dataset embedded in your report.</span></span> <span data-ttu-id="f96e6-128">如需詳細資訊，請按一下[資料集屬性對話方塊、查詢 &#40;報表產生器&#41;](../report-data/dataset-properties-dialog-box-query-report-builder.md) 或[資料集屬性對話方塊、查詢](../dataset-properties-dialog-box-query.md)。</span><span class="sxs-lookup"><span data-stu-id="f96e6-128">For more information, click [Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](../report-data/dataset-properties-dialog-box-query-report-builder.md) or [Dataset Properties Dialog Box, Query](../dataset-properties-dialog-box-query.md).</span></span>  
  
2.  <span data-ttu-id="f96e6-129">在 **[插入]** 索引標籤上，按一下 **[文字方塊]** 。</span><span class="sxs-lookup"><span data-stu-id="f96e6-129">On the **Insert** tab, click **Text Box**.</span></span> <span data-ttu-id="f96e6-130">在清單中按一下，然後拖曳滑鼠來建立一個所需大小的方塊。</span><span class="sxs-lookup"><span data-stu-id="f96e6-130">Click in the list, and then drag to create a box that is the size you want.</span></span>  
  
3.  <span data-ttu-id="f96e6-131">在文字方塊中鍵入標籤，例如 **My Field**。</span><span class="sxs-lookup"><span data-stu-id="f96e6-131">Type a label in the text box - for example, **My Field**:.</span></span>  
  
4.  <span data-ttu-id="f96e6-132">將欄位從資料集拖曳至文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="f96e6-132">Drag a field from your dataset into the text box.</span></span> <span data-ttu-id="f96e6-133">如此就會針對您的欄位建立預留位置。</span><span class="sxs-lookup"><span data-stu-id="f96e6-133">A placeholder is created for your field.</span></span>  
  
5.  <span data-ttu-id="f96e6-134">從基本格式中選取預留位置文字，然後在 [主資料夾]  索引標籤的 [字型]  群組中按一下其中一個格式選項。例如，按一下 [粗體]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="f96e6-134">For basic formatting, select the placeholder text and then click one of the formatting options in the **Font** group on the **Home** tab. For example, click the **Bold** button.</span></span>  
  
     <span data-ttu-id="f96e6-135">如需其他格式選項，以滑鼠右鍵按一下預留位置文字，然後按一下 [預留位置屬性]  。</span><span class="sxs-lookup"><span data-stu-id="f96e6-135">For more formatting options, right-click the placeholder text, and then click **Placeholder Properties**.</span></span>  
  
6.  <span data-ttu-id="f96e6-136">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="f96e6-136">Click **OK**.</span></span> <span data-ttu-id="f96e6-137">在 [報表設計] 檢視中，文字方塊中應該包含 "**My Field**: [*FieldName*]"，其中 *FieldName* 是您欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="f96e6-137">In report design view, the text box should contain "**My Field**: [*FieldName*]", where *FieldName* is the name of your field.</span></span>  
  
7.  <span data-ttu-id="f96e6-138">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="f96e6-138">Click **Run**.</span></span>  
  
 <span data-ttu-id="f96e6-139">清單會針對欄位中每一個值重複一次，而且 *FieldName* 預留位置每次都會由資料集中該欄位的值取代。</span><span class="sxs-lookup"><span data-stu-id="f96e6-139">The list repeats one time for every value in the field, and the *FieldName* placeholder is replaced each time by the value of that field in the dataset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f96e6-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f96e6-140">See Also</span></span>  
 <span data-ttu-id="f96e6-141">[文字方塊 &#40;報表產生器及 SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f96e6-141">[Text Boxes &#40;Report Builder and SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f96e6-142">[格式化文字和預留位置 &#40;報表產生器及 SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f96e6-142">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f96e6-143">[報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f96e6-143">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f96e6-144">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f96e6-144">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f96e6-145">[將 HTML 新增至報表 &#40;報表產生器及 SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f96e6-145">[Add HTML into a Report &#40;Report Builder and SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f96e6-146">[列出 &#40;報表產生器和 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f96e6-146">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f96e6-147">[格式化數字和日期 &#40;報表產生器及 SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f96e6-147">[Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f96e6-148">預留位置屬性對話方塊、一般 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f96e6-148">Placeholder Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../placeholder-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
