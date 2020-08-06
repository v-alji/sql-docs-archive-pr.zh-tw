---
title: 使用衍生的資料行轉換來衍生資料行值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- columns [Integration Services]
- derived columns
- columns [Integration Services], values
- Derived Column transformation
ms.assetid: 28b07746-fc6f-42b2-b741-9de6fac3f29c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 837ec552144697b40cf649bc0403edfe4dc57a57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585513"
---
# <a name="derive-column-values-by-using-the-derived-column-transformation"></a><span data-ttu-id="f4644-102">使用衍生的資料行轉換來衍生資料行值</span><span class="sxs-lookup"><span data-stu-id="f4644-102">Derive Column Values by Using the Derived Column Transformation</span></span>
  <span data-ttu-id="f4644-103">若要加入及設定「衍生的資料行」轉換，封裝中必須已包含至少一個「資料流程」工作和一個來源。</span><span class="sxs-lookup"><span data-stu-id="f4644-103">To add and configure a Derived Column transformation, the package must already include at least one Data Flow task and one source.</span></span>  
  
 <span data-ttu-id="f4644-104">「衍生的資料行」轉換使用運算式更新現有的值或將值加入至新的資料行。</span><span class="sxs-lookup"><span data-stu-id="f4644-104">The Derived Column transformation uses expressions to update the values of existing or to add values to new columns.</span></span> <span data-ttu-id="f4644-105">若您選擇將值加入至新的資料行， **[衍生的資料行轉換編輯器]** 對話方塊就會評估運算式並定義資料行的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f4644-105">When you choose to add values to new columns, the **Derived Column Transformation Editor** dialog box evaluates the expression and defines the metadata of the columns accordingly.</span></span> <span data-ttu-id="f4644-106">例如，如果運算式串連兩個資料行 (兩個資料行都使用 DT_WSTR 資料類型且長度為 50)，而且兩個資料行值之間會有空格，新的資料行會具有 DT_WSTR 資料類型且長度為 101。</span><span class="sxs-lookup"><span data-stu-id="f4644-106">For example, if an expression concatenates two columns-each with the DT_WSTR data type and a length of 50-with a space between the two column values, the new column has the DT_WSTR data type and a length of 101.</span></span> <span data-ttu-id="f4644-107">您可以更新新資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f4644-107">You can update the data type of new columns.</span></span> <span data-ttu-id="f4644-108">唯一的要求就是該資料類型必須與插入的資料相容。</span><span class="sxs-lookup"><span data-stu-id="f4644-108">The only requirement is that data type be compatible with the inserted data.</span></span> <span data-ttu-id="f4644-109">舉例來說，若您指派日期值到整數資料類型的資料行， **[衍生的資料行轉換編輯器]** 對話方塊就會產生驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="f4644-109">For example, the **Derived Column Transformation Editor** dialog box generates a validation error when you assign a date value to a column with an integer data type.</span></span> <span data-ttu-id="f4644-110">視您選擇的資料類型而定，您可指定資料行的長度、有效位數、小數位數和字碼頁。</span><span class="sxs-lookup"><span data-stu-id="f4644-110">Depending on the data type that you selected, you can specify the length, precision, scale, and code page of the column.</span></span>  
  
### <a name="to-derive-column-values"></a><span data-ttu-id="f4644-111">若要衍生資料行值</span><span class="sxs-lookup"><span data-stu-id="f4644-111">To derive column values</span></span>  
  
1.  <span data-ttu-id="f4644-112">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="f4644-112">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="f4644-113">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="f4644-113">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="f4644-114">按一下 **[資料流程]** 索引標籤，然後從 **[工具箱]** 拖曳「衍生的資料行」轉換至設計介面。</span><span class="sxs-lookup"><span data-stu-id="f4644-114">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Derived Column transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="f4644-115">從來源或先前的轉換將連接子拖曳到「衍生的資料行」轉換，以便將「衍生的資料行」轉換連接到資料流程。</span><span class="sxs-lookup"><span data-stu-id="f4644-115">Connect the Derived Column transformation to the data flow by dragging the connector from the source or the previous transformation to the Derived Column transformation.</span></span>  
  
5.  <span data-ttu-id="f4644-116">按兩下「衍生的資料行」轉換。</span><span class="sxs-lookup"><span data-stu-id="f4644-116">Double-click the Derived Column transformation.</span></span>  
  
6.  <span data-ttu-id="f4644-117">在 **[衍生的資料行轉換編輯器]** 對話方塊中，拖曳變數、資料行、函數和運算子到方格中的 **[運算式]** 資料行，以建立要當作條件使用的運算式。</span><span class="sxs-lookup"><span data-stu-id="f4644-117">In the **Derived Column Transformation Editor** dialog box, build the expressions to use as conditions by dragging variables, columns, functions, and operators to the **Expression** column in the grid.</span></span> <span data-ttu-id="f4644-118">或者，您也可以在 **[運算式]** 資料行中輸入運算式。</span><span class="sxs-lookup"><span data-stu-id="f4644-118">Alternatively, you can type the expression in the **Expression** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f4644-119">如果運算式無效，則運算式文字會反白顯示，且資料行上的「工具提示」會描述錯誤。</span><span class="sxs-lookup"><span data-stu-id="f4644-119">If the expression is not valid, the expression text is highlighted and a ToolTip on the column describes the errors.</span></span>  
  
7.  <span data-ttu-id="f4644-120">在 [衍生的資料行] 清單中，選取 **\<add as new column>** 以將運算式的評估結果寫入新資料行，或選取要以評估結果更新的現有資料行。</span><span class="sxs-lookup"><span data-stu-id="f4644-120">In the **Derived Column** list, select **\<add as new column>** to write the evaluation result of the expression to a new column, or select an existing column to update with the evaluation result.</span></span>  
  
     <span data-ttu-id="f4644-121">如果您選擇使用新資料行， **[衍生的資料行轉換編輯器]** 對話方塊就會依據資料類型、長度、有效位數、小數位數和字碼頁，評估運算式並指派資料類型到資料行。</span><span class="sxs-lookup"><span data-stu-id="f4644-121">If you chose to use a new column, the **Derived Column Transformation Editor** dialog box evaluates the expression and assigns a data type to the column, depending on the data type, length, precisions, scale, and code page.</span></span>  
  
8.  <span data-ttu-id="f4644-122">如果使用新的資料行，請在 **[資料類型]** 清單中選取資料類型。</span><span class="sxs-lookup"><span data-stu-id="f4644-122">If using a new column, select a data type in the **Data Type** list.</span></span> <span data-ttu-id="f4644-123">根據選取的資料類型而定，選擇性地更新 **[長度]** 、 **[有效位數]** 、 **[小數位數]** 和 **[字碼頁]** 資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="f4644-123">Depending on the selected data type, optionally update the values in the **Length**, **Precision**, **Scale**, and **Code Page** columns.</span></span> <span data-ttu-id="f4644-124">現有資料行的中繼資料無法變更。</span><span class="sxs-lookup"><span data-stu-id="f4644-124">Metadata of existing columns cannot be changed.</span></span>  
  
9. <span data-ttu-id="f4644-125">(選擇性) 修改 **[衍生的資料行名稱]** 資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="f4644-125">Optionally, modify the values in the **Derived Column Name** column.</span></span>  
  
10. <span data-ttu-id="f4644-126">若要設定錯誤輸出，請按一下 **[設定錯誤輸出]** 。</span><span class="sxs-lookup"><span data-stu-id="f4644-126">To configure the error output, click **Configure Error Output**.</span></span> <span data-ttu-id="f4644-127">如需詳細資訊，請參閱 [在資料流程元件中設定錯誤輸出](../../configure-an-error-output-in-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="f4644-127">For more information, see [Configure an Error Output in a Data Flow Component](../../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
11. <span data-ttu-id="f4644-128">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="f4644-128">Click **OK**.</span></span>  
  
12. <span data-ttu-id="f4644-129">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="f4644-129">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4644-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4644-130">See Also</span></span>  
 <span data-ttu-id="f4644-131">[Derived Column Transformation](derived-column-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="f4644-131">[Derived Column Transformation](derived-column-transformation.md) </span></span>  
 <span data-ttu-id="f4644-132">[Integration Services 資料類型](../integration-services-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="f4644-132">[Integration Services Data Types](../integration-services-data-types.md) </span></span>  
 <span data-ttu-id="f4644-133">[Integration Services 轉換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="f4644-133">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="f4644-134">[Integration Services 路徑](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="f4644-134">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 <span data-ttu-id="f4644-135">[資料流程工作](../../control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="f4644-135">[Data Flow Task](../../control-flow/data-flow-task.md) </span></span>  
 [<span data-ttu-id="f4644-136">Integration Services &#40;SSIS&#41; 運算式</span><span class="sxs-lookup"><span data-stu-id="f4644-136">Integration Services &#40;SSIS&#41; Expressions</span></span>](../../expressions/integration-services-ssis-expressions.md)  
  
  
