---
title: 在 MDX 查詢設計工具中定義 Analysis Services (報表產生器和 SSRS) 的參數 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- parameters [Reporting Services], MDX
- Multidimensional Expressions [Reporting Services]
- Data Mining Prediction [Reporting Services]
- MDX [Reporting Services], defining parameters
- DMX [Reporting Services]
ms.assetid: 4ad1e5bc-f510-4752-b4f6-589e55317a90
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6b2b05fc0122eb25a7a0799f7b47b1b99486a28c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710249"
---
# <a name="define-parameters-in-the-mdx-query-designer-for-analysis-services-report-builder-and-ssrs"></a><span data-ttu-id="6dfd3-102">在 Analysis Services 的 MDX 查詢設計工具中定義參數 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6dfd3-102">Define Parameters in the MDX Query Designer for Analysis Services (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6dfd3-103">若要將 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 資料來源的 MDX 查詢參數化，您必須將查詢參數加入查詢中。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-103">To parameterize an MDX query for an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source, you must add a query parameter to the query.</span></span> <span data-ttu-id="6dfd3-104">在 MDX 查詢設計工具中，您可以透過指定篩選，在 [設計] 模式和 [查詢] 模式中加入查詢參數。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-104">In the MDX query designer, you can add a query parameter in both Design mode and Query mode by specifying a filter.</span></span> <span data-ttu-id="6dfd3-105">在您使用查詢參數來定義查詢之後，Reporting Services 會自動建立報表參數和資料集來提供有效值的清單。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-105">After you define the query with a query parameter, Reporting Services automatically creates a report parameter and a dataset to provide the list of valid values.</span></span> <span data-ttu-id="6dfd3-106">如此可讓使用者指定直接傳遞給查詢的值。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-106">This enables a user to specify a value that is passed directly to the query.</span></span>

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

### <a name="to-define-a-query-parameter-in-mdx-in-design-mode"></a><span data-ttu-id="6dfd3-107">在設計模式下定義 MDX 中的查詢參數</span><span class="sxs-lookup"><span data-stu-id="6dfd3-107">To define a query parameter in MDX in Design mode</span></span>

1.  <span data-ttu-id="6dfd3-108">在 [報表資料] 窗格中，以滑鼠右鍵按一下從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 資料來源類型建立的資料集，然後按一下 [查詢]  。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-108">In the Report Data pane, right-click on a dataset created from a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source type, and then click **Query**.</span></span> <span data-ttu-id="6dfd3-109">MDX 查詢設計工具會在 [設計] 模式中開啟。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-109">The MDX query designer opens in Design mode.</span></span>

2.  <span data-ttu-id="6dfd3-110">將維度拖曳到篩選區域，然後將它放在 **[維度]** 資料行的第一個資料格上。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-110">Drag a dimension to the filter area and drop it on the first cell in the **Dimension** column.</span></span>

3.  <span data-ttu-id="6dfd3-111">在 **[階層]** 資料行中，從下拉式清單選擇一個值。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-111">In the **Hierarchy** column, choose a value from the drop-down list.</span></span>

4.  <span data-ttu-id="6dfd3-112">在 **[運算子]** 資料行中，從下拉式清單選擇一個運算子。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-112">In the **Operator** column, choose an operator for the drop-down list.</span></span>

5.  <span data-ttu-id="6dfd3-113">在 **[篩選運算式]** 資料行中，從下拉式清單選取個別值，或是按一下 **[全部]** 成員來選擇所有的值。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-113">In the **Filter Expression** column, select individual values from the drop-down list, or click the **All** member to choose all values.</span></span>

6.  <span data-ttu-id="6dfd3-114">在 **[參數]** 資料行中，選取可建立報表參數的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-114">In the **Parameters** column, select the check box to create a report parameter.</span></span>

7.  <span data-ttu-id="6dfd3-115">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-115">Click **Run**.</span></span>

     <span data-ttu-id="6dfd3-116">在您執行查詢之後，按一下工具列上的 **[設計]** 可切換至 [查詢] 模式，以檢視已經建立的 MDX 查詢。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-116">After you run the query, click **Design** on the toolbar to toggle to Query mode to view the MDX query that was created.</span></span> <span data-ttu-id="6dfd3-117">如果您想要繼續使用 [設計] 模式來開發查詢，請不要在 [查詢] 模式中變更查詢文字。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-117">Do not change the query text in Query mode if you want to continue to use Design mode to develop the query.</span></span> <span data-ttu-id="6dfd3-118">按一下 **[設計]** 可切換回到 [設計] 模式。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-118">Click **Design** to toggle back to Design mode.</span></span>

8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]

     <span data-ttu-id="6dfd3-119">在 [報表資料] 窗格中，展開 [參數] 節點來顯示之前自動為篩選建立的報表參數。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-119">In the Report Data pane, expand the Parameters node to display the report parameter that was automatically created for the filter.</span></span>

     <span data-ttu-id="6dfd3-120">若要檢視可為報表參數提供可用值的資料集，請以滑鼠右鍵按一下 [報表資料] 窗格中的空白區，然後按一下 **[顯示隱藏的資料集]** 。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-120">To view the dataset that provides available values for the report parameter, right-click any blank area in the Report Data pane, and then click **Show Hidden Datasets**.</span></span> <span data-ttu-id="6dfd3-121">[報表資料] 窗格會顯示報表中的所有資料集。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-121">The Report Data pane displays all datasets in the report.</span></span>

### <a name="to-define-a-query-parameter-in-mdx-in-query-mode"></a><span data-ttu-id="6dfd3-122">在查詢模式下定義 MDX 中的查詢參數</span><span class="sxs-lookup"><span data-stu-id="6dfd3-122">To define a query parameter in MDX in Query mode</span></span>

1.  <span data-ttu-id="6dfd3-123">在 [報表資料] 窗格中，以滑鼠右鍵按一下從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 資料來源類型建立的資料集，然後按一下 [查詢]  。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-123">In the Report Data pane, right-click on a dataset created from a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source type, and then click **Query**.</span></span> <span data-ttu-id="6dfd3-124">MDX 查詢設計工具會在 [設計] 模式中開啟。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-124">The MDX query designer opens in Design mode.</span></span>

2.  <span data-ttu-id="6dfd3-125">在工具列上按一下 **[設計]** ，切換至 [查詢] 模式。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-125">On the toolbar, click **Design** to toggle to Query mode.</span></span>

3.  <span data-ttu-id="6dfd3-126">在 MDX 查詢設計工具的工具列上，按一下 [查詢參數]  (![[查詢參數] 對話方塊圖示](../../analysis-services/media/iconqueryparameter.gif "[查詢參數] 對話方塊圖示"))。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-126">On the MDX query designer toolbar, click **Query Parameters** (![Icon for the Query Parameters dialog box](../../analysis-services/media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")).</span></span> <span data-ttu-id="6dfd3-127">[查詢參數] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-127">The Query Parameters dialog box opens.</span></span>

4.  <span data-ttu-id="6dfd3-128">在 [**參數**] 資料行中，按一下 **\<Enter Parameter>** ，然後輸入參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-128">In the **Parameter** column, click **\<Enter Parameter>**, and then type the name of a parameter.</span></span>

5.  <span data-ttu-id="6dfd3-129">在 [維度]  資料行中，從下拉式清單選擇一個值。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-129">In the **Dimension** column, choose a value from the drop-down list.</span></span>

6.  <span data-ttu-id="6dfd3-130">在 **[階層]** 資料行中，從下拉式清單選擇一個值。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-130">In the **Hierarchy** column, choose a value from the drop-down list.</span></span>

7.  <span data-ttu-id="6dfd3-131">在 **[多個值]** 資料行中，選取可建立多值參數的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-131">In the **Multiple values** column, select the check box to create a multivalue parameter.</span></span>

8.  <span data-ttu-id="6dfd3-132">在 **[預設值]** 資料行中，從下拉式清單選取單一值或多個值 (視您在步驟 5 的選擇而定)。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-132">In the **Default** column, from the drop-down list, select a single value or multiple values depending on your choice in step 5.</span></span>

9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]

10. <span data-ttu-id="6dfd3-133">在查詢設計工具工具列上，按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-133">On the query designer toolbar, click **Run**.</span></span>

11. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]

     <span data-ttu-id="6dfd3-134">在 [報表資料] 窗格中，展開 [參數] 節點來顯示之前自動為篩選建立的報表參數。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-134">In the Report Data pane, expand the Parameters node to display the report parameter that was automatically created for the filter.</span></span>

     <span data-ttu-id="6dfd3-135">若要檢視可為報表參數提供可用值的資料集，請以滑鼠右鍵按一下 [報表資料] 窗格中的空白區，然後按一下 **[顯示隱藏的資料集]** 。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-135">To view the dataset that provides available values for the report parameter, right-click any blank area in the Report Data pane, and then click **Show Hidden Datasets**.</span></span> <span data-ttu-id="6dfd3-136">[報表資料] 窗格會顯示報表中的所有資料集。</span><span class="sxs-lookup"><span data-stu-id="6dfd3-136">The Report Data pane displays all datasets in the report.</span></span>

## <a name="see-also"></a><span data-ttu-id="6dfd3-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dfd3-137">See Also</span></span>
 <span data-ttu-id="6dfd3-138">[Mdx &#40;SSRS&#41;Analysis Services 連線類型](analysis-services-connection-type-for-mdx-ssrs.md) [Analysis Services mdx 查詢設計工具使用者介面](analysis-services-mdx-query-designer-user-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6dfd3-138">[Analysis Services Connection Type for MDX &#40;SSRS&#41;](analysis-services-connection-type-for-mdx-ssrs.md) [Analysis Services MDX Query Designer User Interface](analysis-services-mdx-query-designer-user-interface.md)</span></span>


