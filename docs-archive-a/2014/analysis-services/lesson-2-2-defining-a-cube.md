---
title: 定義 Cube |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8aa4ac2d-857f-4048-baa0-0f314e207cf6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 354a05840dd2e091f956454858edd5c75c8c4bdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584776"
---
# <a name="defining-a-cube"></a><span data-ttu-id="499d1-102">定義 Cube</span><span class="sxs-lookup"><span data-stu-id="499d1-102">Defining a Cube</span></span>
  <span data-ttu-id="499d1-103">「Cube 精靈」可協助您定義 Cube 的量值群組和維度。</span><span class="sxs-lookup"><span data-stu-id="499d1-103">The Cube Wizard helps you define the measure groups and dimensions for a cube.</span></span> <span data-ttu-id="499d1-104">在下列工作中，您將使用「Cube 精靈」來建立 Cube。</span><span class="sxs-lookup"><span data-stu-id="499d1-104">In the following task, you will use the Cube Wizard to build a cube.</span></span>  
  
### <a name="to-define-a-cube-and-its-properties"></a><span data-ttu-id="499d1-105">若要定義 Cube 及其屬性</span><span class="sxs-lookup"><span data-stu-id="499d1-105">To define a cube and its properties</span></span>  
  
1.  <span data-ttu-id="499d1-106">在方案總管中，以滑鼠右鍵按一下 [Cube]\*\*\*\*，然後按一下 [新增 Cube]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="499d1-106">In Solution Explorer, right-click **Cubes**, and then click **New Cube**.</span></span> <span data-ttu-id="499d1-107">[Cube 精靈] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="499d1-107">The Cube Wizard appears.</span></span>  
  
2.  <span data-ttu-id="499d1-108">在 [歡迎使用 Cube 精靈]\*\*\*\* 頁面上，按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="499d1-108">On the **Welcome to the Cube Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="499d1-109">在 [選取建立方法]\*\*\*\* 頁面上，確認已選取 [使用現有的資料表]\*\*\*\* 選項，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="499d1-109">On the **Select Creation Method** page, verify that the **Use existing tables** option is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="499d1-110">在 [選取量值群組資料表]\*\*\*\* 頁面上，確認已選取 [Adventure Works DW 2012]\*\*\*\* 資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="499d1-110">On the **Select Measure Group Tables** page, verify that the **Adventure Works DW 2012** data source view is selected.</span></span>  
  
5.  <span data-ttu-id="499d1-111">按一下 [建議]\*\*\*\*，讓 Cube 精靈建議用來建立量值群組的資料表。</span><span class="sxs-lookup"><span data-stu-id="499d1-111">Click **Suggest** to have the cube wizard suggest tables to use to create measure groups.</span></span>  
  
     <span data-ttu-id="499d1-112">此精靈會檢查這些資料表並建議使用 [InternetSales]\*\*\*\* 當作量值群組資料表。</span><span class="sxs-lookup"><span data-stu-id="499d1-112">The wizard examines the tables and suggests **InternetSales** as a measure group table.</span></span> <span data-ttu-id="499d1-113">量值群組資料表 (也稱為事實資料表) 包含您感興趣的量值，例如銷售的單位數。</span><span class="sxs-lookup"><span data-stu-id="499d1-113">Measure group tables, also called fact tables, contain the measures you are interested in, such as the number of units sold.</span></span>  
  
6.  <span data-ttu-id="499d1-114">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="499d1-114">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="499d1-115">在 [選取量值]\*\*\*\* 頁面上，檢閱 [網際網路銷售]\*\*\*\* 量值群組中的所選取量值，再清除下列量值的核取方塊：</span><span class="sxs-lookup"><span data-stu-id="499d1-115">On the **Select Measures** page, review the selected measures in the **Internet Sales** measure group, and then clear the check boxes for the following measures:</span></span>  
  
    -   <span data-ttu-id="499d1-116">**升級索引鍵**</span><span class="sxs-lookup"><span data-stu-id="499d1-116">**Promotion Key**</span></span>  
  
    -   <span data-ttu-id="499d1-117">**貨幣索引鍵**</span><span class="sxs-lookup"><span data-stu-id="499d1-117">**Currency Key**</span></span>  
  
    -   <span data-ttu-id="499d1-118">**銷售領域索引鍵**</span><span class="sxs-lookup"><span data-stu-id="499d1-118">**Sales Territory Key**</span></span>  
  
    -   <span data-ttu-id="499d1-119">**修訂號碼**</span><span class="sxs-lookup"><span data-stu-id="499d1-119">**Revision Number**</span></span>  
  
     <span data-ttu-id="499d1-120">根據預設，此精靈會選取事實資料表中所有未連結到維度的數值資料行當做量值。</span><span class="sxs-lookup"><span data-stu-id="499d1-120">By default, the wizard selects as measures all numeric columns in the fact table that are not linked to dimensions.</span></span> <span data-ttu-id="499d1-121">不過，這 4 個資料行不是實際量值。</span><span class="sxs-lookup"><span data-stu-id="499d1-121">However, these four columns are not actual measures.</span></span> <span data-ttu-id="499d1-122">前 3 個是連結事實資料表與維度資料表的索引鍵值，它們不使用於這個 Cube 的初始版本。</span><span class="sxs-lookup"><span data-stu-id="499d1-122">The first three are key values that link the fact table with dimension tables that are not used in the initial version of this cube.</span></span>  
  
8.  <span data-ttu-id="499d1-123">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="499d1-123">Click **Next**.</span></span>  
  
9. <span data-ttu-id="499d1-124">在 [選取現有維度]\*\*\*\* 頁面上，確定已選取您先前建立的 [Date]\*\*\*\* 維度，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="499d1-124">On the **Select Existing Dimensions** page, make sure the **Date** dimension that you created earlier is selected, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="499d1-125">在 [選取新維度]\*\*\*\* 頁面上，選取要建立的新維度。</span><span class="sxs-lookup"><span data-stu-id="499d1-125">On the **Select New Dimensions** page, select the new dimensions to be created.</span></span> <span data-ttu-id="499d1-126">若要執行這項操作，請確認已選取 [Customer]\*\*\*\*、[Geography]\*\*\*\* 和 [Product]\*\*\*\* 核取方塊，然後清除 [InternetSales]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="499d1-126">To do this, verify that the **Customer**, **Geography**, and **Product** check boxes are selected, and then clear the **InternetSales** check box.</span></span>  
  
11. <span data-ttu-id="499d1-127">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="499d1-127">Click **Next**.</span></span>  
  
12. <span data-ttu-id="499d1-128">在 [**正在完成嚮導]** 頁面上，將 cube 的名稱變更為 `Analysis Services Tutorial` 。</span><span class="sxs-lookup"><span data-stu-id="499d1-128">On the **Completing the Wizard** page, change the name of the cube to `Analysis Services Tutorial`.</span></span> <span data-ttu-id="499d1-129">在 [預覽] 窗格中，您可以看見 [InternetSales]\*\*\*\* 量值群組及其量值。</span><span class="sxs-lookup"><span data-stu-id="499d1-129">In the Preview pane, you can see the **InternetSales** measure group and its measures.</span></span> <span data-ttu-id="499d1-130">此外，您也可以看見 [Date]\*\*\*\*、[Customer]\*\*\*\* 和 [Product]\*\*\*\* 維度。</span><span class="sxs-lookup"><span data-stu-id="499d1-130">You can also see the **Date**, **Customer,** and **Product** dimensions.</span></span>  
  
13. <span data-ttu-id="499d1-131">按一下 [完成]\*\*\*\* 以完成程序。</span><span class="sxs-lookup"><span data-stu-id="499d1-131">Click **Finish** to complete the wizard.</span></span>  
  
     <span data-ttu-id="499d1-132">在方案總管的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程專案中，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 會出現在 [Cube]\*\*\*\* 資料夾內，而 [Customer] 和 [Product] 資料庫維度則出現在 [維度]\*\*\*\* 資料夾內。</span><span class="sxs-lookup"><span data-stu-id="499d1-132">In Solution Explorer, in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube appears in the **Cubes** folder, and the Customer and Product database dimensions appear in the **Dimensions** folder.</span></span> <span data-ttu-id="499d1-133">另外，在開發環境中心，[Cube 結構] 索引標籤會顯示 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube。</span><span class="sxs-lookup"><span data-stu-id="499d1-133">Additionally, in the center of the development environment, the Cube Structure tab displays the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>  
  
14. <span data-ttu-id="499d1-134">在 [Cube 結構] 索引標籤的工具列上，將 [顯示比例]\*\*\*\* 層級變更為 50%，這樣就可以更容易看到 Cube 中的維度資料表和事實資料表。</span><span class="sxs-lookup"><span data-stu-id="499d1-134">On the toolbar of the Cube Structure tab, change the **Zoom** level to 50 percent, so that you can more easily see the dimensions and fact tables in the cube.</span></span> <span data-ttu-id="499d1-135">請注意，事實資料表是黃色，維度資料表是藍色。</span><span class="sxs-lookup"><span data-stu-id="499d1-135">Notice that the fact table is yellow and the dimension tables are blue.</span></span>  
  
15. <span data-ttu-id="499d1-136">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="499d1-136">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="499d1-137">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="499d1-137">Next Task in Lesson</span></span>  
 [<span data-ttu-id="499d1-138">將屬性加入至維度</span><span class="sxs-lookup"><span data-stu-id="499d1-138">Adding Attributes to Dimensions</span></span>](lesson-2-3-adding-attributes-to-dimensions.md)  
  
## <a name="see-also"></a><span data-ttu-id="499d1-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="499d1-139">See Also</span></span>  
 <span data-ttu-id="499d1-140">[多維度模型中的 cube](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="499d1-140">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="499d1-141">多維度模型中的維度</span><span class="sxs-lookup"><span data-stu-id="499d1-141">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
