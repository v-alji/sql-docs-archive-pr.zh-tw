---
title: 多維度模型中的計算 |Microsoft Docs
ms.custom: ''
ms.date: 12/10/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculations [Analysis Services], creating
- deleting calculations
- calculations [Analysis Services], scripts
- Cube Designer
- modifying scripts
- removing calculations
- calculations [Analysis Services], deleting
- scripts [Analysis Services], calculations
- cubes [Analysis Services], calculations
- solve orders [Analysis Services]
ms.assetid: c21b3459-9bef-45a2-aba5-c992eba5b66e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 64a9733c4fd198a9906e28c437f7ba4fb10dd39a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705681"
---
# <a name="calculations-in-multidimensional-models"></a><span data-ttu-id="2480d-102">多維度模型中的計算</span><span class="sxs-lookup"><span data-stu-id="2480d-102">Calculations in Multidimensional Models</span></span>
  <span data-ttu-id="2480d-103">使用 [Cube 設計師] 的 [計算]\*\*\*\* 索引標籤來建立導出成員、命名集，和其他多維度運算式 (MDX) 計算。</span><span class="sxs-lookup"><span data-stu-id="2480d-103">Use the **Calculations** tab of Cube Designer to create calculated members, named sets, and other Multidimensional Expressions (MDX) calculations.</span></span>  
  
 <span data-ttu-id="2480d-104">[計算]\*\*\*\* 索引標籤具有下列三個窗格：</span><span class="sxs-lookup"><span data-stu-id="2480d-104">The **Calculations** tab has the following three panes:</span></span>  
  
-   <span data-ttu-id="2480d-105">[指令碼組合管理]\*\*\*\* 窗格列出 Cube 中的計算。</span><span class="sxs-lookup"><span data-stu-id="2480d-105">The **Script Organizer** pane lists the calculations in a cube.</span></span> <span data-ttu-id="2480d-106">使用此窗格來建立、組織和選取計算以進行編輯。</span><span class="sxs-lookup"><span data-stu-id="2480d-106">Use this pane to create, organize, and select calculations for editing.</span></span>  
  
-   <span data-ttu-id="2480d-107">[計算工具]\*\*\*\* 窗格提供用來建立計算的中繼資料、函數和範本。</span><span class="sxs-lookup"><span data-stu-id="2480d-107">The **Calculation Tools** pane provides metadata, functions, and templates with which to create calculations.</span></span>  
  
-   <span data-ttu-id="2480d-108">[計算運算式] 窗格支援表單檢視與指令碼檢視。</span><span class="sxs-lookup"><span data-stu-id="2480d-108">The Calculation Expressions pane supports a form view and a script view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2480d-109">如需 MDX 腳本的詳細資訊，請參閱[Microsoft SQL Server 2005 中的 Mdx 腳本簡介](https://go.microsoft.com/fwlink/?LinkId=81892)，並參閱 Microsoft TechNet 網站上的[SQL Server 2005-Analysis Services](https://go.microsoft.com/fwlink/?LinkId=80853)頁面上的其他資源一節。</span><span class="sxs-lookup"><span data-stu-id="2480d-109">For more information about MDX scripting, see [Introduction to MDX Scripting in Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892), and see the Additional Resources section on the [SQL Server 2005 - Analysis Services](https://go.microsoft.com/fwlink/?LinkId=80853) page on the Microsoft TechNet Web site.</span></span> <span data-ttu-id="2480d-110">如需與 Cube 設計相關之效能問題的詳細資訊，請參閱 [SQL Server 2005 Analysis Services Performance Guide](https://download.microsoft.com/download/8/5/e/85eea4fa-b3bb-4426-97d0-7f7151b2011c/ssas2005perfguide.doc)(SQL Server 2005 Analysis Services 效能指南)。</span><span class="sxs-lookup"><span data-stu-id="2480d-110">For more information about performance issues related to cube design, see the [SQL Server 2005 Analysis Services Performance Guide](https://download.microsoft.com/download/8/5/e/85eea4fa-b3bb-4426-97d0-7f7151b2011c/ssas2005perfguide.doc).</span></span>  
  
## <a name="creating-a-new-calculation"></a><span data-ttu-id="2480d-111">建立新的計算</span><span class="sxs-lookup"><span data-stu-id="2480d-111">Creating a New Calculation</span></span>  
 <span data-ttu-id="2480d-112">若要建立新的計算，請在 [Cube 設計師] 之 [計算]\*\*\*\* 索引標籤的 [Cube]\*\*\*\* 功能表上，依照您要建立的計算類型，按一下 [新增導出成員]\*\*\*\*、[新增命名集]\*\*\*\* 或 [新增指令碼命令]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2480d-112">To create a new calculation, on the **Calculations** tab of Cube Designer, on the **Cube** menu, click either **New Calculated Member**, **New Named Set**, or **New Script Command**, depending on the type of calculation you want to create.</span></span> <span data-ttu-id="2480d-113">您也可以在工具列上按一下任何對應的按鈕，或以滑鼠右鍵按一下 [指令碼組合管理]\*\*\*\* 窗格中的任何位置，然後按一下快速鍵功能表上的其中一個命令。</span><span class="sxs-lookup"><span data-stu-id="2480d-113">You can also click any of the corresponding buttons on the toolbar, or right-click anywhere in the **Script Organizer** pane and then click one of the commands on the shortcut menu.</span></span> <span data-ttu-id="2480d-114">此動作會將新計算加入 [指令碼組合管理]\*\*\*\* 窗格，並在 [計算運算式] 窗格的計算表單中顯示其欄位。</span><span class="sxs-lookup"><span data-stu-id="2480d-114">This action adds a new calculation to the **Script Organizer** pane and displays fields for it in the calculations form in the Calculations Expressions pane.</span></span> <span data-ttu-id="2480d-115">如果您建立新的指令碼，此動作會在 [計算運算式] 窗格中開啟 [指令碼] 檢視。</span><span class="sxs-lookup"><span data-stu-id="2480d-115">If you create a new script, this action opens the Script view in the Calculation Expressions pane.</span></span> <span data-ttu-id="2480d-116">如需建立三種計算類型的詳細資訊，請參閱 [建立導出成員](create-calculated-members.md)、 [建立命名集](create-named-sets.md)和 [定義指派和其他指令碼命令](define-assignments-and-other-script-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="2480d-116">For more information about building the three types of calculations, see [Create Calculated Members](create-calculated-members.md), [Create Named Sets](create-named-sets.md), and [Define Assignments and Other Script Commands](define-assignments-and-other-script-commands.md).</span></span>  
  
## <a name="editing-scripts"></a><span data-ttu-id="2480d-117">編輯指令碼</span><span class="sxs-lookup"><span data-stu-id="2480d-117">Editing Scripts</span></span>  
 <span data-ttu-id="2480d-118">在 [**計算**] 索引標籤的 [計算運算式] 窗格中編輯腳本。[計算運算式] 窗格有兩個視圖： [腳本視圖] 和 [表單檢視]。</span><span class="sxs-lookup"><span data-stu-id="2480d-118">Edit scripts in the Calculation Expressions pane of the **Calculations** tab. The Calculation Expressions pane has two views, Script view and Form view.</span></span> <span data-ttu-id="2480d-119">[表單] 檢視會顯示單一命令的運算式與屬性。</span><span class="sxs-lookup"><span data-stu-id="2480d-119">The Form view shows the expressions and properties for a single command.</span></span> <span data-ttu-id="2480d-120">編輯 MDX 指令碼時，運算式方塊會填滿整個 [表單] 檢視。</span><span class="sxs-lookup"><span data-stu-id="2480d-120">When you edit an MDX script, an expression box fills the entire Form view.</span></span>  
  
 <span data-ttu-id="2480d-121">[指令碼] 檢視提供用來編輯指令碼的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="2480d-121">The Script view provides a code editor in which to edit the scripts.</span></span> <span data-ttu-id="2480d-122">當 [計算運算式] 窗格處於 [指令碼] 檢視時，會隱藏 [指令碼組合管理]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="2480d-122">While the Calculation Expressions pane is in Script view, the **Script Organizer** pane is hidden.</span></span> <span data-ttu-id="2480d-123">指令碼檢視會提供色彩編碼、尋找相符括號、自動完成以及 MDX 程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="2480d-123">The Script view provides color coding, parenthesis matching, auto-complete, and MDX code regions.</span></span> <span data-ttu-id="2480d-124">MDX 程式碼區域可以摺疊或展開，以利編輯。</span><span class="sxs-lookup"><span data-stu-id="2480d-124">The MDX code regions can be collapsed or expanded to facilitate editing.</span></span>  
  
 <span data-ttu-id="2480d-125">您可以按一下 [Cube]\*\*\*\* 功能表，指向 [顯示計算於]\*\*\*\*，然後按一下 [指令碼]\*\*\*\* 或 [表單]\*\*\*\*，即可在 [表單] 檢視與 [指令碼] 檢視間切換。</span><span class="sxs-lookup"><span data-stu-id="2480d-125">You can switch between the Form view and the Script view by clicking the **Cube** menu, pointing to **Show Calculations in**, and then clicking **Script** or **Form**.</span></span> <span data-ttu-id="2480d-126">您也可以在工具列上按一下 [表單檢視]\*\*\*\* 或 [指令碼檢視]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2480d-126">You can also click either **Form view** or **Script view** on the toolbar.</span></span>  
  
## <a name="changing-solve-order"></a><span data-ttu-id="2480d-127">變更求解順序</span><span class="sxs-lookup"><span data-stu-id="2480d-127">Changing Solve Order</span></span>  
 <span data-ttu-id="2480d-128">系統會以 [指令碼組合管理]\*\*\*\* 窗格中列出的順序來解決計算。</span><span class="sxs-lookup"><span data-stu-id="2480d-128">Calculations are solved in the order listed in the **Script Organizer** pane.</span></span> <span data-ttu-id="2480d-129">您可以滑鼠右鍵按一下任何計算，然後按一下快速鍵功能表上的 [上移]\*\*\*\* 或 [下移]\*\*\*\*，重新將計算排序。</span><span class="sxs-lookup"><span data-stu-id="2480d-129">You can reorder the calculations by right-clicking any calculation and then clicking **Move Up** or **Move Down** on the shortcut menu.</span></span> <span data-ttu-id="2480d-130">您也可以按一下計算，然後在工具列按一下 [上移]\*\*\*\* 或 [下移]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="2480d-130">You can also click a calculation and then click the **Move Up** or **Move Down** button on the toolbar.</span></span>  
  
 <span data-ttu-id="2480d-131">您可以針對導出資料格與導出成員，以手動方式覆寫此順序。</span><span class="sxs-lookup"><span data-stu-id="2480d-131">You can override this order manually for calculated cells and calculated members.</span></span> <span data-ttu-id="2480d-132">如需行程順序和求解順序的詳細資訊，請參閱[了解行程順序和求解順序 &#40;MDX&#41;](mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md)。</span><span class="sxs-lookup"><span data-stu-id="2480d-132">For more information about pass order and solve order, see [Understanding Pass Order and Solve Order &#40;MDX&#41;](mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md).</span></span>  
  
## <a name="deleting-a-calculation"></a><span data-ttu-id="2480d-133">刪除計算</span><span class="sxs-lookup"><span data-stu-id="2480d-133">Deleting a Calculation</span></span>  
 <span data-ttu-id="2480d-134">若要刪除現有的計算，請在 [計算]\*\*\*\* 索引標籤上，於 [指令碼組合管理]\*\*\*\* 窗格中，選取要刪除的計算，然後在 [編輯]\*\*\*\* 功能表上按一下 [刪除]\*\*\*\*，或在工具列上按一下**刪除**圖示。</span><span class="sxs-lookup"><span data-stu-id="2480d-134">To delete an existing calculation, on the **Calculations** tab, in the **Script Organizer** pane, select the calculation to be deleted, and then click **Delete** on the **Edit** menu or click the **Delete** icon on the toolbar.</span></span> <span data-ttu-id="2480d-135">您也可以在 [指令碼組合管理]\*\*\*\* 窗格中以滑鼠右鍵按一下計算，然後從快速鍵功能表中選取 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2480d-135">You can also right-click the calculation in the **Script Organizer** pane and select **Delete** from the short-cut menu.</span></span>  
  
  
