---
title: 建立遞迴階層群組 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8b830ba5-4d64-4348-a2b1-76b9338a1462
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bf86c3989170ed8cd452168a558ead348258331e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594433"
---
# <a name="create-a-recursive-hierarchy-group-report-builder-and-ssrs"></a><span data-ttu-id="d52fb-102">建立遞迴階層群組 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="d52fb-102">Create a Recursive Hierarchy Group (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d52fb-103">遞迴階層群組會組織包含多個階層層級之單一報表資料集內的資料，例如組織階層內經理-員工關聯性的報告結構。</span><span class="sxs-lookup"><span data-stu-id="d52fb-103">A recursive hierarchy group organizes data from a single report dataset that includes multiple hierarchical levels, such as the report-to structure for manager-employee relationships in an organizational hierarchy.</span></span>  
  
 <span data-ttu-id="d52fb-104">您必須有單一資料集可容納所有階層式資料，而且必須有個別欄位可包含要分組的項目以及做為分組依據的項目，才能將資料表內的資料組織成遞迴階層群組。</span><span class="sxs-lookup"><span data-stu-id="d52fb-104">Before you can organize data in a table as a recursive hierarchy group, you must have a single dataset that contains all the hierarchical data, You must have separate fields for the item to group and for the item to group by.</span></span> <span data-ttu-id="d52fb-105">例如，在您希望以遞迴方式將員工分組在其經理底下的資料集中，可能包含名稱、員工名稱、員工識別碼和經理識別碼。</span><span class="sxs-lookup"><span data-stu-id="d52fb-105">For example, a dataset where you want to group employees recursively under their manager might contain a name, an employee name, an employee ID, and a manager ID.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-create-a-recursive-hierarchy-group"></a><span data-ttu-id="d52fb-106">建立遞迴階層群組</span><span class="sxs-lookup"><span data-stu-id="d52fb-106">To create a recursive hierarchy group</span></span>  
  
1.  <span data-ttu-id="d52fb-107">在 [設計] 檢視中加入資料表，並將資料集欄位拖曳至顯示。</span><span class="sxs-lookup"><span data-stu-id="d52fb-107">In Design view, add a table, and drag the dataset fields to display.</span></span> <span data-ttu-id="d52fb-108">一般來說，您想要顯示為階層的欄位會位於第一個資料行中。</span><span class="sxs-lookup"><span data-stu-id="d52fb-108">Typically, the field that you want to show as a hierarchy is in the first column.</span></span>  
  
2.  <span data-ttu-id="d52fb-109">以滑鼠右鍵按一下資料表中的任何地方，即可選取它。</span><span class="sxs-lookup"><span data-stu-id="d52fb-109">Right-click anywhere in the table to select it.</span></span> <span data-ttu-id="d52fb-110">[群組] 窗格會顯示選定資料表的詳細資料群組。</span><span class="sxs-lookup"><span data-stu-id="d52fb-110">The Grouping pane displays the details group for the selected table.</span></span> <span data-ttu-id="d52fb-111">在 [資料列群組] 窗格中，以滑鼠右鍵按一下 [詳細資料]  ，然後按一下 [編輯群組]  。</span><span class="sxs-lookup"><span data-stu-id="d52fb-111">In the Row Groups pane, right-click **Details**, and then click **Edit Group**.</span></span> <span data-ttu-id="d52fb-112">**[群組屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d52fb-112">The **Group Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="d52fb-113">在 **[群組運算式]** 中，按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="d52fb-113">In **Group expressions**, click **Add**.</span></span> <span data-ttu-id="d52fb-114">新的資料列會出現在方格中。</span><span class="sxs-lookup"><span data-stu-id="d52fb-114">A new row appears in the grid.</span></span>  
  
4.  <span data-ttu-id="d52fb-115">在 [群組對象]  清單中，鍵入或選取要分組的欄位。</span><span class="sxs-lookup"><span data-stu-id="d52fb-115">In the **Group on** list, type or select the field to group.</span></span>  
  
5.  <span data-ttu-id="d52fb-116">按一下 **[進階]** 。</span><span class="sxs-lookup"><span data-stu-id="d52fb-116">Click **Advanced**.</span></span>  
  
6.  <span data-ttu-id="d52fb-117">在 [遞迴父系]  清單中，輸入或選取要作為分組對象的欄位。</span><span class="sxs-lookup"><span data-stu-id="d52fb-117">In the **Recursive Parent** list, enter or select the field to group on.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="d52fb-118">執行報表。</span><span class="sxs-lookup"><span data-stu-id="d52fb-118">Run the report.</span></span> <span data-ttu-id="d52fb-119">報表會顯示遞迴階層群組，但是不會有任何顯示階層的縮排</span><span class="sxs-lookup"><span data-stu-id="d52fb-119">The report displays the recursive hierarchy group, although there is no indent to show the hierarchy</span></span>  
  
### <a name="to-format-a-recursive-hierarchy-group-with-indent-levels"></a><span data-ttu-id="d52fb-120">以縮排層次格式化遞迴階層群組</span><span class="sxs-lookup"><span data-stu-id="d52fb-120">To format a recursive hierarchy group with indent levels</span></span>  
  
1.  <span data-ttu-id="d52fb-121">按一下文字方塊，其中包含您想要將縮排層次加入其中以顯示階層格式的欄位。</span><span class="sxs-lookup"><span data-stu-id="d52fb-121">Click the text box that contains the field to which you want to add indent levels to display a hierarchy format.</span></span> <span data-ttu-id="d52fb-122">文字方塊的屬性會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="d52fb-122">The properties for the text box appear in the Properties pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d52fb-123">如果看不到 [屬性] 窗格，請按一下 [檢視] 索引標籤上的 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="d52fb-123">If you do not see the Properties pane, click **Properties** on the **View** tab.</span></span>  
  
2.  <span data-ttu-id="d52fb-124">在 [屬性] 窗格中，展開 `Padding` 節點、按一下 [**左**]，然後從下拉式清單中選取 [] **\<Expression...>** 。</span><span class="sxs-lookup"><span data-stu-id="d52fb-124">In the Properties pane, expand the `Padding` node, click **Left**, and from the drop-down list, select **\<Expression...>**.</span></span>  
  
3.  <span data-ttu-id="d52fb-125">在 [運算式] 窗格中，輸入下列運算式：</span><span class="sxs-lookup"><span data-stu-id="d52fb-125">In the Expression pane, type the following expression:</span></span>  
  
     `=CStr(2 + (Level()*10)) + "pt"`  
  
     <span data-ttu-id="d52fb-126">Padding 屬性全都需要 *nnyy*格式的字串，其中 *nn* 是數字，而 *yy* 是測量單位。</span><span class="sxs-lookup"><span data-stu-id="d52fb-126">The Padding properties all require a string in the format *nnyy*, where *nn* is a number and *yy* is the unit of measure.</span></span> <span data-ttu-id="d52fb-127">此範例運算式會建立一個利用 `Level` 函數的字串，以便根據遞迴層級來增加填補大小。</span><span class="sxs-lookup"><span data-stu-id="d52fb-127">The example expression builds a string that uses the `Level` function to increase the size of the padding based on recursion level.</span></span> <span data-ttu-id="d52fb-128">例如，層級 1 的資料列會產生 (2 + (1\*10))=12pt 的填補，層級 3 的資料列會產生 (2 + (3\*10))=32pt 的填補。</span><span class="sxs-lookup"><span data-stu-id="d52fb-128">For example, a row that has a level of 1 would result in a padding of (2 + (1\*10))=12pt, and a row that has a level of 3 would result in a padding of (2 + (3\*10))=32pt.</span></span> <span data-ttu-id="d52fb-129">如需函式的詳細資訊 `Level` ，請參閱[Level](report-builder-functions-level-function.md)。</span><span class="sxs-lookup"><span data-stu-id="d52fb-129">For information about the `Level` function, see [Level](report-builder-functions-level-function.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="d52fb-130">執行報表。</span><span class="sxs-lookup"><span data-stu-id="d52fb-130">Run the report.</span></span> <span data-ttu-id="d52fb-131">報表會以階層檢視來顯示分組的資料。</span><span class="sxs-lookup"><span data-stu-id="d52fb-131">The report displays a hierarchical view of the grouped data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d52fb-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d52fb-132">See Also</span></span>  
 <span data-ttu-id="d52fb-133">[建立遞迴階層群組 &#40;報表產生器及 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d52fb-133">[Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d52fb-134">[篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d52fb-134">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d52fb-135">[彙總函式參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d52fb-135">[Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span></span>  
 <span data-ttu-id="d52fb-136">[資料表 &#40;報表產生器及 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d52fb-136">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d52fb-137">[矩陣 &#40;報表產生器及 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d52fb-137">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d52fb-138">[清單 &#40;報表產生器及 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d52fb-138">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d52fb-139">資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d52fb-139">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
