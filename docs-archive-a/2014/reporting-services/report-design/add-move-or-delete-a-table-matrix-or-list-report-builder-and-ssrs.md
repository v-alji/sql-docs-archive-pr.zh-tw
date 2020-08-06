---
title: 新增、移動或刪除資料表、矩陣或清單 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b97c470-cde0-4bb1-a46e-5f5f5553feaa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 43941639a41c897a49cd34662b74de26a27e3f07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707145"
---
# <a name="add-move-or-delete-a-table-matrix-or-list-report-builder-and-ssrs"></a><span data-ttu-id="32485-102">加入、移動或刪除資料表、矩陣或清單 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="32485-102">Add, Move, or Delete a Table, Matrix, or List (Report Builder and SSRS)</span></span>
  <span data-ttu-id="32485-103">資料區會顯示報表資料集中的資料。</span><span class="sxs-lookup"><span data-stu-id="32485-103">A data region displays data from a report dataset.</span></span> <span data-ttu-id="32485-104">資料區包括資料表、矩陣、清單、圖表和量測計。</span><span class="sxs-lookup"><span data-stu-id="32485-104">Data regions include table, matrix, list, chart, and gauge.</span></span> <span data-ttu-id="32485-105">若要讓某個資料區以巢狀結構的方式置於另一個資料區內，請個別加入每一個資料區，然後將子資料區拖曳到父資料區。</span><span class="sxs-lookup"><span data-stu-id="32485-105">To nest one data region inside another, add each data region separately, and then drag the child data region onto the parent data region.</span></span>  
  
 <span data-ttu-id="32485-106">將資料表或矩陣資料區加入至報表最簡單的方式就是執行新增資料表或新增矩陣精靈。</span><span class="sxs-lookup"><span data-stu-id="32485-106">The simplest way to add a table or matrix data region to your report is to run the New Table or New Matrix Wizard.</span></span> <span data-ttu-id="32485-107">這些精靈會引導您完成選擇資料來源的連接、排列欄位，以及選擇配置和樣式的程序。</span><span class="sxs-lookup"><span data-stu-id="32485-107">These wizards will guide you through the process of choosing a connection to a data source, arranging fields, and choosing the layout and style.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32485-108">您只能在報表產生器中使用此精靈。</span><span class="sxs-lookup"><span data-stu-id="32485-108">The wizard is available only in Report Builder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-table-or-matrix-to-a-report-by-using-the-new-table-or-new-matrix-wizard"></a><span data-ttu-id="32485-109">若要使用新增資料表或新增矩陣精靈，將資料表或矩陣加入至報表</span><span class="sxs-lookup"><span data-stu-id="32485-109">To add a table or matrix to a report by using the New Table or New Matrix Wizard</span></span>  
  
1.  <span data-ttu-id="32485-110">在 **[插入]** 索引標籤上，按一下 **[資料表]** 或 **[矩陣]** ，然後按一下 **[資料表精靈]** 或 **[矩陣精靈]** 。</span><span class="sxs-lookup"><span data-stu-id="32485-110">On the **Insert** tab, click **Table** or **Matrix**, and then click **Table Wizard** or **Matrix Wizard**.</span></span>  
  
2.  <span data-ttu-id="32485-111">依照 [ **NewTable** ] 或 [**新增矩陣**] 嚮導中的步驟進行。</span><span class="sxs-lookup"><span data-stu-id="32485-111">Follow the steps in the **NewTable** or **New Matrix** wizard.</span></span>  
  
3.  <span data-ttu-id="32485-112">在 **[主資料夾]** 索引標籤上，按一下 **[執行]** 查看轉譯的報表。</span><span class="sxs-lookup"><span data-stu-id="32485-112">On the **Home** tab, click **Run** to see the rendered report.</span></span>  
  
4.  <span data-ttu-id="32485-113">在 **[執行]** 索引標籤上，按一下 **[設計]** 繼續處理報表。</span><span class="sxs-lookup"><span data-stu-id="32485-113">On the **Run** tab, click **Design** to continue working on the report.</span></span>  
  
### <a name="to-add-a-data-region"></a><span data-ttu-id="32485-114">若要加入資料區</span><span class="sxs-lookup"><span data-stu-id="32485-114">To add a data region</span></span>  
  
1.  <span data-ttu-id="32485-115">在 **[功能區]** 的 **[資料區域]** 群組中，按一下要加入的資料區。</span><span class="sxs-lookup"><span data-stu-id="32485-115">On the **Ribbon**, in the **Data Regions** group, click the data region to add.</span></span>  
  
2.  <span data-ttu-id="32485-116">按一下設計介面，然後拖曳滑鼠來建立一個方塊，這就是您想要的資料區大小。</span><span class="sxs-lookup"><span data-stu-id="32485-116">Click the design surface, and then drag to create a box that is the desired size of the data region.</span></span>  
  
3.  <span data-ttu-id="32485-117">將報表資料集欄位從 [報表資料] 窗格拖曳到資料區資料格上。</span><span class="sxs-lookup"><span data-stu-id="32485-117">Drag a report dataset field from the Report Data pane onto a data region cell.</span></span> <span data-ttu-id="32485-118">資料區現在會繫結至報表資料集中的資料。</span><span class="sxs-lookup"><span data-stu-id="32485-118">The data region is now bound to data from the report dataset.</span></span>  
  
### <a name="to-select-a-data-region"></a><span data-ttu-id="32485-119">若要選取資料區</span><span class="sxs-lookup"><span data-stu-id="32485-119">To select a data region</span></span>  
  
-   <span data-ttu-id="32485-120">若為 Tablix 資料區，請以滑鼠右鍵按一下角控點。</span><span class="sxs-lookup"><span data-stu-id="32485-120">For a tablix data region, right-click the corner handle.</span></span> <span data-ttu-id="32485-121">若為圖表或量測計資料區，請在資料區中按一下。</span><span class="sxs-lookup"><span data-stu-id="32485-121">For a chart or gauge data region, click in the data region.</span></span>  
  
     <span data-ttu-id="32485-122">隨即出現選取控點和八個調整大小的控點。</span><span class="sxs-lookup"><span data-stu-id="32485-122">A selection handle and eight resizing handles appear.</span></span>  
  
     <span data-ttu-id="32485-123">若為巢狀資料區，請在巢狀資料區中按一下滑鼠右鍵、按一下 [選取]  ，然後選取您想要的報表項目。</span><span class="sxs-lookup"><span data-stu-id="32485-123">For nested data regions, right-click in the nested data region, click **Select**, and then select the report item you want.</span></span> <span data-ttu-id="32485-124">若要確認哪一個報表項目已選取，請使用 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="32485-124">To verify which report item is selected, use the Properties pane.</span></span> <span data-ttu-id="32485-125">設計介面上選取的項目名稱會出現在 [屬性] 窗格的工具列中。</span><span class="sxs-lookup"><span data-stu-id="32485-125">The name of the selected item on the design surface appears in the toolbar of the Properties pane.</span></span>  
  
### <a name="to-move-a-data-region"></a><span data-ttu-id="32485-126">若要移動資料區</span><span class="sxs-lookup"><span data-stu-id="32485-126">To move a data region</span></span>  
  
-   <span data-ttu-id="32485-127">若要移動資料區，請按一下資料區的選取控點，然後拖曳它。</span><span class="sxs-lookup"><span data-stu-id="32485-127">To move a data region, click the selection handle of the data region and drag it.</span></span> <span data-ttu-id="32485-128">使用貼齊格線，將它與現有的報表項目對齊。</span><span class="sxs-lookup"><span data-stu-id="32485-128">Use snaplines to align it to existing report items.</span></span>  
  
     <span data-ttu-id="32485-129">如果看不到尺規，請按一下 [檢視] 索引標籤，並選取 **[尺規]** 選項。</span><span class="sxs-lookup"><span data-stu-id="32485-129">If the ruler is not visible, click the View tab and select the **Ruler** option.</span></span>  
  
     <span data-ttu-id="32485-130">另外，您也可以使用方向鍵，將選取的資料區移到設計介面上。</span><span class="sxs-lookup"><span data-stu-id="32485-130">Alternatively, use the arrow keys to move the selected data region on the design surface.</span></span>  
  
### <a name="to-delete-a-data-region"></a><span data-ttu-id="32485-131">若要刪除資料區</span><span class="sxs-lookup"><span data-stu-id="32485-131">To delete a data region</span></span>  
  
-   <span data-ttu-id="32485-132">選取資料區，在資料區中按一下滑鼠右鍵，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="32485-132">Select the data region, right-click in the data region, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32485-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32485-133">See Also</span></span>  
 <span data-ttu-id="32485-134">[Tablix 資料區 &#40;報表產生器及 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="32485-134">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="32485-135">[資料表 &#40;報表產生器和 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="32485-135">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="32485-136">[&#40;報表產生器和 SSRS&#41;的矩陣](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="32485-136">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="32485-137">[列出 &#40;報表產生器和 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="32485-137">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="32485-138">資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="32485-138">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
