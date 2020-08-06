---
title: 第6課：定義計算 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e0a1e354-e879-4eb8-bb2b-6c3809e32cb6
author: minewiskan
ms.author: owend
ms.openlocfilehash: e0b3f7e925a11146204dc6c55e9ddd6820ecb802
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594780"
---
# <a name="lesson-6-defining-calculations"></a><span data-ttu-id="adeff-102">第 6 課：定義計算</span><span class="sxs-lookup"><span data-stu-id="adeff-102">Lesson 6: Defining Calculations</span></span>
  <span data-ttu-id="adeff-103">在這一課中，您要學習定義計算，它們是多維度運算式 (MDX) 運算式或指令碼。</span><span class="sxs-lookup"><span data-stu-id="adeff-103">In this lesson, you learn to define calculations, which are Multidimensional Expressions (MDX) expressions or scripts.</span></span> <span data-ttu-id="adeff-104">計算可讓您定義導出成員、命名集，以及執行其他指令碼命令，以便擴充 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Cube 的功能。</span><span class="sxs-lookup"><span data-stu-id="adeff-104">Calculations enable you to define calculated members, named sets, and execute other script commands to extend the capabilities of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube.</span></span> <span data-ttu-id="adeff-105">例如，您可以執行指令碼命令，先定義 Subcube，然後再將計算指派給 Subcube 中的資料格。</span><span class="sxs-lookup"><span data-stu-id="adeff-105">For example, you can run a script command to define a subcube and then assign a calculation to the cells in the subcube.</span></span>  
  
 <span data-ttu-id="adeff-106">當您在 Cube 設計師定義新的計算時，這些計算會加入至 Cube 設計師之 [計算]\*\*\*\* 索引標籤的 [指令碼組合管理]\*\*\*\* 窗格，而特定計算類型的欄位則是顯示在 [計算運算式]\*\*\*\* 窗格的計算表單中。</span><span class="sxs-lookup"><span data-stu-id="adeff-106">When you define a new calculation in Cube Designer, the calculation is added to the **Script Organizer** pane of the **Calculations** tab of Cube Designer, and the fields for the particular calculation type are displayed in a calculations form in the **Calculation Expressions** pane.</span></span> <span data-ttu-id="adeff-107">計算是以它們列示在 [指令碼組合管理]\*\*\*\* 窗格的順序來執行的。</span><span class="sxs-lookup"><span data-stu-id="adeff-107">Calculations are executed in the order in which they are listed in the **Script Organizer** pane.</span></span> <span data-ttu-id="adeff-108">您可以用滑鼠右鍵按一下特定的計算，然後選取 [上移]\*\*\*\* 或 [下移]\*\*\*\*；或者按一下特定的計算，然後在 [計算]\*\*\*\* 索引標籤的工具列上，按一下 [上移]\*\*\*\* 或 [下移]\*\*\*\* 圖示，重新排列計算。</span><span class="sxs-lookup"><span data-stu-id="adeff-108">You can reorder the calculations by right-clicking on a particular calculation and then selecting **Move Up** or **Move Down**, or by clicking a particular calculation and then using the **Move Up** or **Move Down** icons on the toolbar of the **Calculations** tab.</span></span>  
  
 <span data-ttu-id="adeff-109">您可以在 [計算]\*\*\*\* 索引標籤上，加入新的計算，以及在 [計算運算式]\*\*\*\* 窗格的下列檢視中，檢視或編輯現有的計算：</span><span class="sxs-lookup"><span data-stu-id="adeff-109">On the **Calculations** tab, you can add new calculations and view or edit existing calculations in the following views in the **Calculation Expressions** pane:</span></span>  
  
-   <span data-ttu-id="adeff-110">表單檢視。</span><span class="sxs-lookup"><span data-stu-id="adeff-110">Form view.</span></span> <span data-ttu-id="adeff-111">這份檢視所顯示的，是單一命令的運算式和屬性，以圖形格式表示。</span><span class="sxs-lookup"><span data-stu-id="adeff-111">This view shows the expressions and properties for a single command in a graphical format.</span></span> <span data-ttu-id="adeff-112">當您編輯 MDX 指令碼時，運算式方塊會幫您填寫表單檢視。</span><span class="sxs-lookup"><span data-stu-id="adeff-112">When you edit an MDX script, an expression box fills the Form view.</span></span>  
  
-   <span data-ttu-id="adeff-113">指令碼檢視。</span><span class="sxs-lookup"><span data-stu-id="adeff-113">Script view.</span></span> <span data-ttu-id="adeff-114">這份檢視會以程式碼編輯器顯示所有的計算指令碼，讓您輕鬆變更計算指令碼。</span><span class="sxs-lookup"><span data-stu-id="adeff-114">This view displays all calculation scripts in a code editor, which lets you easily change the calculation scripts.</span></span> <span data-ttu-id="adeff-115">如果 [計算運算式]\*\*\*\* 窗格是在指令碼檢視中，[指令碼組合管理]\*\*\*\* 就會隱藏起來。</span><span class="sxs-lookup"><span data-stu-id="adeff-115">When the **Calculation Expressions** pane is in Script view, the **Script Organizer** is hidden.</span></span> <span data-ttu-id="adeff-116">指令碼檢視會提供色彩編碼、尋找相符括號、自動完成以及 MDX 程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="adeff-116">The Script view provides color coding, parenthesis matching, auto-complete, and MDX code regions.</span></span> <span data-ttu-id="adeff-117">您可以展開或收合 MDX 程式碼區域，讓編輯作業更加容易。</span><span class="sxs-lookup"><span data-stu-id="adeff-117">You can expand or collapse the MDX code regions to make editing easier.</span></span>  
  
 <span data-ttu-id="adeff-118">若要在 [計算運算式]\*\*\*\* 窗格中的這兩份檢視之間切換，請在 [計算]\*\*\*\* 索引標籤的工具列上，按一下 [表單檢視]\*\*\*\* 或 [指令碼檢視]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="adeff-118">To switch between these views in the **Calculation Expressions** pane, click **Form View** or **Script View** on the toolbar of the **Calculations** tab.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="adeff-119">如果 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 在任何計算中發現語法錯誤，就不會顯示表單檢視，除非指令碼檢視將錯誤更正。</span><span class="sxs-lookup"><span data-stu-id="adeff-119">If [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] detects a syntax error in any calculation, the Form view will not display until the error is corrected in the Script view.</span></span>  
  
 <span data-ttu-id="adeff-120">您也可以利用商業智慧精靈，在 Cube 加入特定的計算。</span><span class="sxs-lookup"><span data-stu-id="adeff-120">You can also use the Business Intelligence Wizard to add certain calculations to a cube.</span></span> <span data-ttu-id="adeff-121">例如，您可以利用這個精靈，將時間智慧加入 Cube 中，也就是說，針對與時間有關的計算 (例如，某週期至今、移動平均或循環週期成長率) 來定義導出成員。</span><span class="sxs-lookup"><span data-stu-id="adeff-121">For example, you can use this wizard to add time intelligence to a cube, which means defining calculated members for time-related calculations such as period-to-date, moving averages, or period over period growth.</span></span> <span data-ttu-id="adeff-122">如需詳細資訊，請參閱 [使用商業智慧精靈定義時間智慧計算](multidimensional-models/define-time-intelligence-calculations-using-the-business-intelligence-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="adeff-122">For more information, see [Define Time Intelligence Calculations using the Business Intelligence Wizard](multidimensional-models/define-time-intelligence-calculations-using-the-business-intelligence-wizard.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="adeff-123">在 [計算]\*\*\*\* 索引標籤上，計算指令碼是以 CALCULATE 命令開頭。</span><span class="sxs-lookup"><span data-stu-id="adeff-123">On the **Calculations** tab, the calculation script starts with the CALCULATE command.</span></span> <span data-ttu-id="adeff-124">CALCULATE 命令會控制 Cube 中的資料格彙總，不過，只有在您想要手動指定 Cube 資料格的彙總方式時，才編輯這個命令。</span><span class="sxs-lookup"><span data-stu-id="adeff-124">The CALCULATE command controls the aggregation of the cells in the cube and you should edit this command only if you intend to manually specify how the cube cells should be aggregated.</span></span>  
  
 <span data-ttu-id="adeff-125">如需詳細資訊，請參閱 [計算](multidimensional-models-olap-logical-cube-objects/calculations.md)和 [多維度模型中的計算](multidimensional-models/calculations-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="adeff-125">For more information, see [Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md), and [Calculations in Multidimensional Models](multidimensional-models/calculations-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="adeff-126">此教學課程中，所有課程已完成的專案都可在線上取得。</span><span class="sxs-lookup"><span data-stu-id="adeff-126">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="adeff-127">您可以從先前的課程中使用已完成的專案做為起點，向前跳到任何課程。</span><span class="sxs-lookup"><span data-stu-id="adeff-127">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="adeff-128">[按一下這裡](https://go.microsoft.com/fwlink/?LinkID=221866) ，下載此教學課程隨附的範例專案。</span><span class="sxs-lookup"><span data-stu-id="adeff-128">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="adeff-129">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="adeff-129">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="adeff-130">定義導出成員</span><span class="sxs-lookup"><span data-stu-id="adeff-130">Defining Calculated Members</span></span>](lesson-6-1-defining-calculated-members.md)  
 <span data-ttu-id="adeff-131">在這項工作中，您要學習定義導出成員。</span><span class="sxs-lookup"><span data-stu-id="adeff-131">In this task, you learn to define calculated members.</span></span>  
  
 [<span data-ttu-id="adeff-132">定義命名集</span><span class="sxs-lookup"><span data-stu-id="adeff-132">Defining Named Sets</span></span>](lesson-6-2-defining-named-sets.md)  
 <span data-ttu-id="adeff-133">在這項工作中，您要學習定義命名集。</span><span class="sxs-lookup"><span data-stu-id="adeff-133">In this task, you learn to define named sets.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="adeff-134">下一課</span><span class="sxs-lookup"><span data-stu-id="adeff-134">Next Lesson</span></span>  
 [<span data-ttu-id="adeff-135">第 7 課：定義關鍵效能指標 &#40;KPI&#41;</span><span class="sxs-lookup"><span data-stu-id="adeff-135">Lesson 7: Defining Key Performance Indicators &#40;KPIs&#41;</span></span>](lesson-7-defining-key-performance-indicators-kpis.md)  
  
## <a name="see-also"></a><span data-ttu-id="adeff-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adeff-136">See Also</span></span>  
 <span data-ttu-id="adeff-137">[Analysis Services 教學課程案例](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="adeff-137">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="adeff-138">[多維度模型化 &#40;的艾德作品教學課程&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="adeff-138">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 <span data-ttu-id="adeff-139">[建立命名集](multidimensional-models/create-named-sets.md) </span><span class="sxs-lookup"><span data-stu-id="adeff-139">[Create Named Sets](multidimensional-models/create-named-sets.md) </span></span>  
 [<span data-ttu-id="adeff-140">建立導出成員</span><span class="sxs-lookup"><span data-stu-id="adeff-140">Create Calculated Members</span></span>](multidimensional-models/create-calculated-members.md)  
  
  
