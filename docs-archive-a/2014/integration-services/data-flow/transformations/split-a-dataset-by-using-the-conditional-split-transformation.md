---
title: 使用條件式分割轉換來分割資料集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Conditional Split transformation
- splitting dataset
- datasets [Integration Services], splitting
ms.assetid: 23b3e84f-9296-4dc9-81c0-c7f06ae3f1ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2efbc3973db1ab1b6b61f6de879e451319b50e49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599091"
---
# <a name="split-a-dataset-by-using-the-conditional-split-transformation"></a><span data-ttu-id="4c9ea-102">使用條件式分割轉換來分割資料集</span><span class="sxs-lookup"><span data-stu-id="4c9ea-102">Split a Dataset by Using the Conditional Split Transformation</span></span>
  <span data-ttu-id="4c9ea-103">若要加入及設定「條件式分割」轉換，封裝中必須已包含至少一個「資料流程」工作和一個來源。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-103">To add and configure a Conditional Split transformation, the package must already include at least one Data Flow task and a source.</span></span>  
  
### <a name="to-conditionally-split-a-dataset"></a><span data-ttu-id="4c9ea-104">若要條件式分割資料集</span><span class="sxs-lookup"><span data-stu-id="4c9ea-104">To conditionally split a dataset</span></span>  
  
1.  <span data-ttu-id="4c9ea-105">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-105">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="4c9ea-106">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="4c9ea-107">按一下 **[資料流程]** 索引標籤，然後從 **[工具箱]** 拖曳「條件式分割」轉換至設計介面。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-107">Click the **Data Flow** tab, and, from the **Toolbox**, drag the Conditional Split transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="4c9ea-108">從來源或先前的轉換將連接子拖曳到「條件式分割」轉換，以便將「條件式分割」轉換連接到資料流程。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-108">Connect the Conditional Split transformation to the data flow by dragging the connector from the data source or the previous transformation to the Conditional Split transformation.</span></span>  
  
5.  <span data-ttu-id="4c9ea-109">按兩下「條件式分割」轉換。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-109">Double-click the Conditional Split transformation.</span></span>  
  
6.  <span data-ttu-id="4c9ea-110">在 **[條件式分割轉換編輯器]** 中，拖曳變數、資料行、函數和運算子到方格中的 **[條件]** 資料行，以建立要當作條件使用的運算式。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-110">In the **Conditional Split Transformation Editor**, build the expressions to use as conditions by dragging variables, columns, functions, and operators to the **Condition** column in the grid.</span></span> <span data-ttu-id="4c9ea-111">或者，您也可以在 **[條件]** 資料行中輸入運算式。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-111">Or, you can type the expression in the **Condition** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4c9ea-112">變數或資料行可以用在多個運算式中。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-112">A variable or column can be used in multiple expressions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4c9ea-113">如果運算式無效，則運算式文字會反白顯示，且資料行上的「工具提示」會描述錯誤。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-113">If the expression is not valid, the expression text is highlighted and a ToolTip on the column describes the errors.</span></span>  
  
7.  <span data-ttu-id="4c9ea-114">(選擇性) 修改 **[輸出名稱]** 資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-114">Optionally, modify the values in the **Output Name** column.</span></span> <span data-ttu-id="4c9ea-115">預設名稱為 Case 1、Case 2 等等。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-115">The default names are Case 1, Case 2, and so forth.</span></span>  
  
8.  <span data-ttu-id="4c9ea-116">若要修改評估條件的順序，請按一下向上鍵或向下鍵。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-116">To modify the sequence in which the conditions are evaluated, click the up arrow or down arrow.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4c9ea-117">將最可能遇到的條件放在清單的最上方。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-117">Place the conditions that are most likely to be encountered at the top of the list.</span></span>  
  
9. <span data-ttu-id="4c9ea-118">(選擇性) 修改不符合任何條件之資料列的預設輸出名稱。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-118">Optionally, modify the name of the default output for data rows that do not match any condition.</span></span>  
  
10. <span data-ttu-id="4c9ea-119">若要設定錯誤輸出，請按一下 **[設定錯誤輸出]** 。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-119">To configure an error output, click **Configure Error Output**.</span></span> <span data-ttu-id="4c9ea-120">如需詳細資訊，請參閱 [在資料流程元件中設定錯誤輸出](../../configure-an-error-output-in-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-120">For more information, see [Configure an Error Output in a Data Flow Component](../../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
11. <span data-ttu-id="4c9ea-121">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-121">Click **OK**.</span></span>  
  
12. <span data-ttu-id="4c9ea-122">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="4c9ea-122">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c9ea-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c9ea-123">See Also</span></span>  
 <span data-ttu-id="4c9ea-124">[Conditional Split Transformation](conditional-split-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="4c9ea-124">[Conditional Split Transformation](conditional-split-transformation.md) </span></span>  
 <span data-ttu-id="4c9ea-125">[Integration Services 轉換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="4c9ea-125">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="4c9ea-126">[Integration Services 路徑](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="4c9ea-126">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 <span data-ttu-id="4c9ea-127">[Integration Services 資料類型](../integration-services-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="4c9ea-127">[Integration Services Data Types](../integration-services-data-types.md) </span></span>  
 <span data-ttu-id="4c9ea-128">[資料流程工作](../../control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="4c9ea-128">[Data Flow Task](../../control-flow/data-flow-task.md) </span></span>  
 [<span data-ttu-id="4c9ea-129">Integration Services &#40;SSIS&#41; 運算式</span><span class="sxs-lookup"><span data-stu-id="4c9ea-129">Integration Services &#40;SSIS&#41; Expressions</span></span>](../../expressions/integration-services-ssis-expressions.md)  
  
  
