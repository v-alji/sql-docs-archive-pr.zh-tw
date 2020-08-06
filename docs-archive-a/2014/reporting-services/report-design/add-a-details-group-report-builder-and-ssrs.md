---
title: 新增詳細資料群組 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ef8efba-6d48-4aeb-a3b9-a02ba5a44614
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 24b1f6af1aaf336a69a0068636ced60c364e556d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595773"
---
# <a name="add-a-details-group-report-builder-and-ssrs"></a><span data-ttu-id="fde84-102">加入詳細資料群組 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="fde84-102">Add a Details Group (Report Builder and SSRS)</span></span>
  <span data-ttu-id="fde84-103">系統會將報表資料集中的詳細資料指定為沒有群組運算式的群組。</span><span class="sxs-lookup"><span data-stu-id="fde84-103">The detail data from a report dataset is specified as a group with no group expression.</span></span> <span data-ttu-id="fde84-104">當您想要顯示矩陣的詳細資料、加回您已經從資料表或清單中刪除的詳細資料，或加入額外的詳細資料群組時，請將詳細資料群組加入至現有的 Tablix 資料區域。</span><span class="sxs-lookup"><span data-stu-id="fde84-104">Add a detail group to an existing tablix data region when you want to display the detail data for a matrix, add back detail data that you have deleted from a table or list, or to add additional detail groups.</span></span> <span data-ttu-id="fde84-105">如需群組的詳細資訊，請參閱 [了解群組 &#40;報表產生器及 SSRS&#41;](understanding-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="fde84-105">For more information about groups, see [Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-details-group-to-a-tablix-data-region"></a><span data-ttu-id="fde84-106">將詳細資料群組加入到 Tablix 資料區域</span><span class="sxs-lookup"><span data-stu-id="fde84-106">To add a details group to a tablix data region</span></span>  
  
1.  <span data-ttu-id="fde84-107">在設計介面上，按一下 Tablix 資料區域中的任意位置來選取它。</span><span class="sxs-lookup"><span data-stu-id="fde84-107">On the design surface, click anywhere in a tablix data region to select it.</span></span> <span data-ttu-id="fde84-108">[群組] 窗格會顯示選定資料區域的資料列和資料行群組。</span><span class="sxs-lookup"><span data-stu-id="fde84-108">The Grouping pane displays the row and column groups for the selected data region.</span></span>  
  
2.  <span data-ttu-id="fde84-109">在 [群組] 窗格中，以滑鼠右鍵按一下屬於最內部之子群組的群組。</span><span class="sxs-lookup"><span data-stu-id="fde84-109">In the Grouping pane, right-click a group that is an innermost child group.</span></span> <span data-ttu-id="fde84-110">按一下 **[加入群組]** ，然後按一下 **[子群組]** 。</span><span class="sxs-lookup"><span data-stu-id="fde84-110">Click **Add Group**, and then click **Child Group**.</span></span> <span data-ttu-id="fde84-111">**[Tablix 群組]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="fde84-111">The **Tablix Group** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="fde84-112">在 **[群組運算式]** 中，將運算式保留空白。</span><span class="sxs-lookup"><span data-stu-id="fde84-112">In **Group expression**, leave the expression blank.</span></span> <span data-ttu-id="fde84-113">詳細資料群組沒有運算式。</span><span class="sxs-lookup"><span data-stu-id="fde84-113">A details group has no expression.</span></span>  
  
4.  <span data-ttu-id="fde84-114">選取 **[顯示詳細資料]** 。</span><span class="sxs-lookup"><span data-stu-id="fde84-114">Select **Show detail data**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="fde84-115">此時新的詳細資料群組會當做子群組加入到 [群組] 窗格中，而且您在步驟 1 中選取之群組的資料列控制代碼會顯示詳細資料群組圖示。</span><span class="sxs-lookup"><span data-stu-id="fde84-115">A new details group is added as a child group in the Grouping pane, and the row handle for the group you selected in step 1 displays the details group icon.</span></span> <span data-ttu-id="fde84-116">如需控制代碼的詳細資訊，請參閱 [Tablix 資料區資料格、資料列及資料行 &#40;報表產生器及 SSRS&#41;](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="fde84-116">For more information about handles, see [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde84-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fde84-117">See Also</span></span>  
 <span data-ttu-id="fde84-118">[在資料區中加入或刪除群組 &#40;報表產生器及 SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fde84-118">[Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fde84-119">[了解群組 &#40;報表產生器及 SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fde84-119">[Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fde84-120">[Tablix 資料區 &#40;報表產生器及 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fde84-120">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fde84-121">[資料表 &#40;報表產生器和 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fde84-121">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fde84-122">[&#40;報表產生器和 SSRS&#41;的矩陣](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fde84-122">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fde84-123">[列出 &#40;報表產生器和 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fde84-123">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="fde84-124">資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="fde84-124">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
