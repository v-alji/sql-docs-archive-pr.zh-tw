---
title: 新增、移動或刪除文字方塊 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f042cf81-d933-4ac7-9287-c074a46bde98
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cd85415fd2f0bac2a37b3fbda06795e10f351b19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707142"
---
# <a name="add-move-or-delete-a-text-box-report-builder-and-ssrs"></a><span data-ttu-id="2e4fa-102">加入、移動或刪除文字方塊 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="2e4fa-102">Add, Move, or Delete a Text Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2e4fa-103">文字方塊是報表中最常使用的報表項目。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-103">Text boxes are the most commonly used report item in reports.</span></span> <span data-ttu-id="2e4fa-104">您可以將文字方塊加入至報表主體，以便顯示標題、參數選擇、內建欄位和日期等資訊。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-104">You can add a text box to the report body to display information such as titles, parameter choices, built-in fields, and dates.</span></span>  
  
 <span data-ttu-id="2e4fa-105">資料表或矩陣中的每個資料格實際上都是文字方塊。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-105">Every cell in a table or matrix is really a text box.</span></span> <span data-ttu-id="2e4fa-106">幾乎所有顯示在報表中的報表資料 (包含資料表和矩陣) 都是報表處理器評估報表中每一個文字方塊內容的結果。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-106">Almost all report data displayed in a report with tables and matrices is the result of the report processor evaluating the contents of each text box in the report.</span></span> <span data-ttu-id="2e4fa-107">因此，您可以利用在資料區外部格式化其他文字方塊的相同方式，格式化資料格。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-107">As such, you can format cells in the same way you would format other text boxes outside the data region.</span></span>  
  
 <span data-ttu-id="2e4fa-108">若要將文字方塊加入至清單資料區，您必須先加入此文字方塊，然後將它拖曳到清單中。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-108">To add a text box to a list data region, you must first add the text box and then drag it into the list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2e4fa-109">當您按一下文字方塊時，就可以立即編輯文字方塊中的文字。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-109">When you click a text box, you're immediately editing the text in the text box.</span></span> <span data-ttu-id="2e4fa-110">若要選取文字方塊本身，而非其中的文字，請按下 ESC。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-110">To select the text box itself, not the text in it, press ESC.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-text-box"></a><span data-ttu-id="2e4fa-111">若要加入文字方塊</span><span class="sxs-lookup"><span data-stu-id="2e4fa-111">To add a text box</span></span>  
  
1.  <span data-ttu-id="2e4fa-112">在 [設計] 檢視的 **[插入]** 索引標籤上，按一下 **[文字方塊]** 。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-112">On the **Insert** tab in Design view, click **Text Box**.</span></span>  
  
2.  <span data-ttu-id="2e4fa-113">在設計介面中，按一下然後將方塊拖曳至所需的文字方塊大小。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-113">On the design surface, click and then drag a box to the desired size of the text box.</span></span> <span data-ttu-id="2e4fa-114">另外，您也可以按一下設計介面來建立預設大小的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-114">Alternatively, click the design surface to create a text box of default size.</span></span>  
  
### <a name="to-add-a-text-box-in-a-list"></a><span data-ttu-id="2e4fa-115">若要在清單中加入文字方塊</span><span class="sxs-lookup"><span data-stu-id="2e4fa-115">To add a text box in a list</span></span>  
  
1.  <span data-ttu-id="2e4fa-116">在 [報表設計] 檢視的 **[插入]** 索引標籤上，按一下 **[清單]**。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-116">On the **Insert** tab in report design view, click **List**.</span></span>  
  
2.  <span data-ttu-id="2e4fa-117">在設計介面中，按一下然後將方塊拖曳至所需的清單大小。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-117">On the design surface, click and then drag a box to the desired size of the list.</span></span> <span data-ttu-id="2e4fa-118">另外，您也可以按一下設計介面來建立預設大小的清單。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-118">Alternatively, click the design surface to create a list of default size.</span></span>  
  
3.  <span data-ttu-id="2e4fa-119">在 **[插入]** 索引標籤上，按一下 **[文字方塊]**。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-119">On the **Insert** tab, click **Text Box**.</span></span>  
  
4.  <span data-ttu-id="2e4fa-120">在設計介面中，於步驟 1 加入的清單內部，按一下然後將方塊拖曳至所需的文字方塊大小。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-120">On the design surface, click and then drag a box to the desired size of the text box inside the list you added in step 1.</span></span> <span data-ttu-id="2e4fa-121">或者，按一下在清單內部的設計介面，即可建立預設大小的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-121">Alternatively, click the design surface inside the list to create a text box of default size.</span></span>  
  
5.  <span data-ttu-id="2e4fa-122">若要確認文字方塊以巢狀結構的方式正確置於清單內，請選取此文字方塊。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-122">To confirm the text box is correctly nested inside the list, select the text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2e4fa-123">如果您在文字方塊中按一下並且處於編輯模式，請按下 ESC 來選取文字方塊。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-123">If you click in the text box and are in edit mode, press ESC to select the text box.</span></span>  
  
6.  <span data-ttu-id="2e4fa-124">在 [屬性] 窗格內，確認 **[Parent]** 屬性是自動加入至清單資料區的矩形。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-124">In the Properties pane, verify that the **Parent** property is the rectangle that was automatically added to the list data region.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2e4fa-125">如果看不到 [屬性] 窗格，請核取 [檢視]\*\*\*\* 索引標籤上的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-125">If the Properties pane is not visible, check **Properties** on the **View** tab.</span></span>  
  
### <a name="to-move-a-text-box"></a><span data-ttu-id="2e4fa-126">若要移動文字方塊</span><span class="sxs-lookup"><span data-stu-id="2e4fa-126">To move a text box</span></span>  
  
1.  <span data-ttu-id="2e4fa-127">在 [報表設計] 檢視中，按一下文字方塊內的任何空白處，即可選取該文字方塊。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-127">In report design view, click any empty space within the text box to select the text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2e4fa-128">如果您在文字方塊中按一下並且處於編輯模式，請按下 ESC 來選取文字方塊。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-128">If you click in the text box and are in edit mode, press ESC to select the text box.</span></span>  
  
2.  <span data-ttu-id="2e4fa-129">按一下文字方塊控點，並將文字方塊拖曳到新的位置。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-129">Click the text box handle and drag the text box to the new location.</span></span> <span data-ttu-id="2e4fa-130">另外，您也可以使用方向鍵，水平或垂直移動選取的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-130">Alternatively, you can use the arrow keys to move a selected text box horizontally or vertically.</span></span> <span data-ttu-id="2e4fa-131">若要在設計介面上以較小的增量來移動文字方塊，請按住 CTRL 鍵的同時再按方向鍵。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-131">To move the text box in smaller increments on the design surface, hold down CTRL plus the arrow keys.</span></span>  
  
### <a name="to-delete-a-text-box"></a><span data-ttu-id="2e4fa-132">若要刪除文字方塊</span><span class="sxs-lookup"><span data-stu-id="2e4fa-132">To delete a text box</span></span>  
  
1.  <span data-ttu-id="2e4fa-133">在 [報表設計] 檢視中，以滑鼠右鍵按一下文字方塊內的任何空白處來選取它，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-133">In report design view, right-click any empty space within the text box to select it, and then click **Delete**.</span></span> <span data-ttu-id="2e4fa-134">或者，按一下文字方塊內的任何空白處，然後按 DELETE 鍵。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-134">Alternatively, click any empty space within the text box, and then press DELETE.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2e4fa-135">如果您在文字方塊中按一下並且處於編輯模式，請按下 ESC 來選取文字方塊。</span><span class="sxs-lookup"><span data-stu-id="2e4fa-135">If you click in the text box and are in edit mode, press ESC to select the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e4fa-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e4fa-136">See Also</span></span>  
 <span data-ttu-id="2e4fa-137">[文字方塊 &#40;報表產生器和 SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2e4fa-137">[Text Boxes &#40;Report Builder and SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2e4fa-138">[運算式 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2e4fa-138">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2e4fa-139">鍵盤快速鍵 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="2e4fa-139">Keyboard Shortcuts &#40;Report Builder&#41;</span></span>](../report-builder/keyboard-shortcuts-report-builder.md)  
  
  
