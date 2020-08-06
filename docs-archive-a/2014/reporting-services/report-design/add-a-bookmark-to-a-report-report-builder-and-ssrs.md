---
title: 將書籤新增至報表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f130562e-5673-40e3-8e01-de7227a21d41
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fae543dd1b071ff38853637a3da57ffd2410c3a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707161"
---
# <a name="add-a-bookmark-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="dcce9-102">將書籤加入至報表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="dcce9-102">Add a Bookmark to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="dcce9-103">當您想要在報表中提供自訂內容資料表或是提供自訂內部導覽連結時，請將書籤或書籤連結加入到報表中。</span><span class="sxs-lookup"><span data-stu-id="dcce9-103">Add bookmarks and bookmark links to a report when you want to provide a customized table of contents or to provide customized internal navigation links in the report.</span></span> <span data-ttu-id="dcce9-104">一般來說，您會在報表中想要引導使用者的位置上加入書籤，例如每一個資料表或圖表的書籤，或是資料表或矩陣內顯示之唯一群組值的標籤。</span><span class="sxs-lookup"><span data-stu-id="dcce9-104">Typically, you add bookmarks to locations in the report to which you want to direct users, such as to each table or chart or to the unique group values displayed in a table or matrix.</span></span> <span data-ttu-id="dcce9-105">您可以建立自己的字串當做書籤使用，或是針對群組設定群組運算式的標籤。</span><span class="sxs-lookup"><span data-stu-id="dcce9-105">You can create your own strings to use as bookmarks, or, for groups, you can set the bookmark to the group expression.</span></span>  
  
 <span data-ttu-id="dcce9-106">當您建立書籤之後，可以加入使用者只需按一下就可移至每一個書籤的報表項目。</span><span class="sxs-lookup"><span data-stu-id="dcce9-106">After you create bookmarks, you can add report items that the user can click to go to each bookmark.</span></span> <span data-ttu-id="dcce9-107">這些項目通常是文字方塊或影像。</span><span class="sxs-lookup"><span data-stu-id="dcce9-107">These items are typically text boxes or images.</span></span>  
  
 <span data-ttu-id="dcce9-108">例如，如果您的報表顯示依色彩分組的資料表，您會將根據群組運算式的書籤加入到群組首。</span><span class="sxs-lookup"><span data-stu-id="dcce9-108">For example, if your report displays a table grouped by color, you would add a bookmark based on the group expression to the group header.</span></span> <span data-ttu-id="dcce9-109">然後您會加入一個具有單一文字方塊的資料表 (此文字方塊位於顯示色彩值的報表開頭)，然後您會在該文字方塊上設定書籤連結。</span><span class="sxs-lookup"><span data-stu-id="dcce9-109">Then you would add a table with a single text box at the beginning of the report that displayed the color values, and set the bookmark link on that text box.</span></span> <span data-ttu-id="dcce9-110">當您按一下色彩時，報表會跳到頁面，此頁面顯示該色彩的群組首資料列。</span><span class="sxs-lookup"><span data-stu-id="dcce9-110">When you click the color, the report jumps to the page that displays the group header row for that color.</span></span>  
  
 <span data-ttu-id="dcce9-111">您可以將書籤加入到任何報表項目，並將書籤連結加入到具有 **Action** 屬性的任何項目，例如文字方塊、影像或是圖表中的導出數列。</span><span class="sxs-lookup"><span data-stu-id="dcce9-111">You can add a bookmark to any report item and add a bookmark link to any item that has an **Action** property, for example, a text box, an image, or a calculated series in a chart.</span></span> <span data-ttu-id="dcce9-112">如需詳細資訊，請參閱[動作屬性對話方塊 &#40;報表產生器及 SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="dcce9-112">For more information, see the [Action Properties Dialog Box &#40;Report Builder and SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-bookmark"></a><span data-ttu-id="dcce9-113">加入書籤</span><span class="sxs-lookup"><span data-stu-id="dcce9-113">To add a bookmark</span></span>  
  
1.  <span data-ttu-id="dcce9-114">在 [報表設計] 檢視中，選取您想要加入書籤的文字方塊、影像、圖表或其他報表項目。</span><span class="sxs-lookup"><span data-stu-id="dcce9-114">In report design view, select the text box, image, chart, or other report item to which you want to add a bookmark.</span></span> <span data-ttu-id="dcce9-115">選定項目的屬性會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="dcce9-115">The properties for the selected item appear in the Properties pane.</span></span>  
  
2.  <span data-ttu-id="dcce9-116">在 **[書籤]** 旁邊的文字方塊內，輸入一個字串當做此書籤的標籤。</span><span class="sxs-lookup"><span data-stu-id="dcce9-116">In the text box next to **Bookmark**, type a string that is the label for this bookmark.</span></span> <span data-ttu-id="dcce9-117">例如，您可以輸入 **BikePhoto** 做為報表中影像的書籤。</span><span class="sxs-lookup"><span data-stu-id="dcce9-117">For example, you could type **BikePhoto** as the bookmark for an image in your report.</span></span> <span data-ttu-id="dcce9-118">另外，您也可以按一下運算式 (**fx**) 按鈕開啟 [運算式]  對話方塊，以指定評估為標籤的運算式。</span><span class="sxs-lookup"><span data-stu-id="dcce9-118">Alternatively, click the Expression (**fx**) button to open the **Expression** dialog box to specify an expression that evaluates to a label.</span></span> <span data-ttu-id="dcce9-119">如果是群組，您所輸入的運算式應該是群組運算式。</span><span class="sxs-lookup"><span data-stu-id="dcce9-119">For a group, the expression you type should be the group expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dcce9-120">書籤可以是任何字串，但它在報表內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="dcce9-120">The bookmark can be any string, but it must be unique in the report.</span></span> <span data-ttu-id="dcce9-121">如果此書籤不是唯一的，書籤的連結會尋找第一個相符的書籤。</span><span class="sxs-lookup"><span data-stu-id="dcce9-121">If the bookmark is not unique, a link to the bookmark finds the first matching bookmark.</span></span>  
  
### <a name="to-add-a-bookmark-link"></a><span data-ttu-id="dcce9-122">加入書籤連結</span><span class="sxs-lookup"><span data-stu-id="dcce9-122">To add a bookmark link</span></span>  
  
1.  <span data-ttu-id="dcce9-123">在 [設計] 檢視中，以滑鼠右鍵按一下要新增連結的文字方塊、影像或圖表，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="dcce9-123">In Design view, right-click the text box, image, chart, to which you want to add a link and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="dcce9-124">在該報表項目的 **[屬性]** 對話方塊中，按一下 **[動作]** 。</span><span class="sxs-lookup"><span data-stu-id="dcce9-124">In The **Properties** dialog box for that report item, click **Action**.</span></span>  
  
3.  <span data-ttu-id="dcce9-125">選取 **[移至書籤]** 。</span><span class="sxs-lookup"><span data-stu-id="dcce9-125">Select **Go to bookmark**.</span></span> <span data-ttu-id="dcce9-126">此對話方塊中會出現這個選項的其他區段。</span><span class="sxs-lookup"><span data-stu-id="dcce9-126">An additional section appears in the dialog box for this option.</span></span>  
  
4.  <span data-ttu-id="dcce9-127">在 **[選取書籤]** 方塊中，輸入或選取書籤或評估為書籤的運算式。</span><span class="sxs-lookup"><span data-stu-id="dcce9-127">In the **Select bookmark** box, type or select a bookmark or an expression that evaluates to a bookmark.</span></span> <span data-ttu-id="dcce9-128">使用先前的範例，輸入 **BikePhoto** 來建立報表中影像的連結。</span><span class="sxs-lookup"><span data-stu-id="dcce9-128">Using the previous example, type **BikePhoto** to create a link to the image in your report.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="dcce9-129">(選擇性) 文字不會自動格式化為連結的樣式。</span><span class="sxs-lookup"><span data-stu-id="dcce9-129">(Optional) The text is not automatically formatted like a link.</span></span> <span data-ttu-id="dcce9-130">如果是文字，則變更文字色彩及效果來指示該文字為連結，將會是很有協助的作法。</span><span class="sxs-lookup"><span data-stu-id="dcce9-130">For text, it is helpful to change the color and effect of the text to indicate that the text is a link.</span></span> <span data-ttu-id="dcce9-131">例如，在 [功能區] 的 [主資料夾] 索引標籤上設定 **[字型]** 區段，將色彩變更為藍色並加上底線效果。</span><span class="sxs-lookup"><span data-stu-id="dcce9-131">For example, change the color to blue and the effect to underline in the **Font** section in the Home tab of the Ribbon.</span></span>  
  
7.  <span data-ttu-id="dcce9-132">若要測試連結，請按一下 **[執行]** 預覽報表，然後按一下這個連結設定所在的報表項目。</span><span class="sxs-lookup"><span data-stu-id="dcce9-132">To test the link, click **Run** to preview the report, and then click the report item that you set this link on..</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcce9-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcce9-133">See Also</span></span>  
 <span data-ttu-id="dcce9-134">[互動式排序、文件引導模式及連結 &#40;報表產生器及 SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dcce9-134">[Interactive Sort, Document Maps, and Links &#40;Report Builder and SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="dcce9-135">[運算式 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dcce9-135">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="dcce9-136">篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="dcce9-136">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
