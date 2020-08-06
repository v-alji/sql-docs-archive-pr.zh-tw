---
title: 建立和管理 (SSAS 表格式) 的量值 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: edc1a4b2-96d3-4f34-bb70-6cacec79e819
author: minewiskan
ms.author: owend
ms.openlocfilehash: da507bf48b285a1414ffb85ba79da50508a2ae2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594211"
---
# <a name="create-and-manage-measures-ssas-tabular"></a><span data-ttu-id="4f74e-102">建立及管理量值 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="4f74e-102">Create and Manage Measures (SSAS Tabular)</span></span>
  <span data-ttu-id="4f74e-103">量值是為了在報表或 Excel 樞紐分析表 (或樞紐分析圖) 中使用而建立的公式。</span><span class="sxs-lookup"><span data-stu-id="4f74e-103">A measure is a formula that is created for use in a report or Excel PivotTable (or PivotChart).</span></span> <span data-ttu-id="4f74e-104">量值可以用標準彙總函式 (例如 COUNT 或 SUM) 做為基礎，或者，您也可以使用 DAX 自行定義公式。</span><span class="sxs-lookup"><span data-stu-id="4f74e-104">Measures can be based on standard aggregation functions, such as COUNT or SUM, or you can define your own formula by using DAX.</span></span> <span data-ttu-id="4f74e-105">本主題中的工作描述如何使用資料表的量值方格來建立和管理量值。</span><span class="sxs-lookup"><span data-stu-id="4f74e-105">The tasks in this topic describe how to create and manage measures by using a table's measure grid.</span></span>  
  
 <span data-ttu-id="4f74e-106">本主題也包括下列工作：</span><span class="sxs-lookup"><span data-stu-id="4f74e-106">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="4f74e-107">使用標準彙總公式建立量值</span><span class="sxs-lookup"><span data-stu-id="4f74e-107">To create a measure using a standard aggregation formula</span></span>](#bkmk_create_stand)  
  
-   [<span data-ttu-id="4f74e-108">使用自訂公式建立量值</span><span class="sxs-lookup"><span data-stu-id="4f74e-108">To create a measure using a custom formula</span></span>](#bkmk_create_custom)  
  
-   [<span data-ttu-id="4f74e-109">編輯量值屬性</span><span class="sxs-lookup"><span data-stu-id="4f74e-109">To edit measure properties</span></span>](#bkmk_edit)  
  
-   [<span data-ttu-id="4f74e-110">重新命名量值</span><span class="sxs-lookup"><span data-stu-id="4f74e-110">To rename a measure</span></span>](#bkmk_rename)  
  
-   [<span data-ttu-id="4f74e-111">刪除量值</span><span class="sxs-lookup"><span data-stu-id="4f74e-111">To delete a measure</span></span>](#bkmk_delete)  
  
## <a name="tasks"></a><span data-ttu-id="4f74e-112">工作</span><span class="sxs-lookup"><span data-stu-id="4f74e-112">Tasks</span></span>  
 <span data-ttu-id="4f74e-113">若要建立和管理量值，您將使用資料表的量值方格。</span><span class="sxs-lookup"><span data-stu-id="4f74e-113">To create and manage measures, you will use a table's measure grid.</span></span> <span data-ttu-id="4f74e-114">您只能在模型設計師的 [資料檢視] 中，檢視資料表的量值方格。</span><span class="sxs-lookup"><span data-stu-id="4f74e-114">You can view the measure grid for a table in the model designer in Data View only.</span></span> <span data-ttu-id="4f74e-115">您無法在 [圖表檢視] 中建立量值或檢視量值方格；但是，您可以在 [圖表檢視] 中檢視現有的量值。</span><span class="sxs-lookup"><span data-stu-id="4f74e-115">You cannot create measures or view the measure grid when in Diagram View; however, you can view existing measures in Diagram View.</span></span> <span data-ttu-id="4f74e-116">若要顯示資料表的量值方格，請按一下 **[資料表]** 功能表，然後按一下 **[顯示量值方格]**。</span><span class="sxs-lookup"><span data-stu-id="4f74e-116">To show the measure grid for a table, click the **Table** menu, and then click **Show Measure Grid**.</span></span>  
  
###  <a name="to-create-a-measure-using-a-standard-aggregation-formula"></a><a name="bkmk_create_stand"></a><span data-ttu-id="4f74e-117">若要使用標準匯總公式建立量值</span><span class="sxs-lookup"><span data-stu-id="4f74e-117">To create a measure using a standard aggregation formula</span></span>  
  
-   <span data-ttu-id="4f74e-118">依序按一下您要建立量值的資料行及 **[資料行]** 功能表，指向 **[自動加總]**，然後按一下彙總類型。</span><span class="sxs-lookup"><span data-stu-id="4f74e-118">Click on the column for which you want to create the measure, then click the **Column** menu, then point to **AutoSum**, and then click an aggregation type.</span></span>  
  
     <span data-ttu-id="4f74e-119">隨即會以預設名稱自動建立量值，後面接著量值方格中資料行正下方之第一個資料格的公式。</span><span class="sxs-lookup"><span data-stu-id="4f74e-119">The measure will be created automatically with a default name, followed by the formula in the first cell in the measure grid directly beneath the column.</span></span>  
  
###  <a name="to-create-a-measure-using-a-custom-formula"></a><a name="bkmk_create_custom"></a><span data-ttu-id="4f74e-120">若要使用自訂公式建立量值</span><span class="sxs-lookup"><span data-stu-id="4f74e-120">To create a measure using a custom formula</span></span>  
  
-   <span data-ttu-id="4f74e-121">在量值方格中，於您要建立量值的資料行下方，按一下資料格，然後在公式列中輸入名稱，後面依序接著冒號 (:)、等號 (=) 及公式。</span><span class="sxs-lookup"><span data-stu-id="4f74e-121">In the measure grid, beneath the column for which you want to create the measure, click a cell, then in the formula bar, type a name, followed by a colon (:), followed by an equals sign (=), followed by the formula.</span></span> <span data-ttu-id="4f74e-122">按下 ENTER 鍵接受公式。</span><span class="sxs-lookup"><span data-stu-id="4f74e-122">Press ENTER to accept the formula.</span></span>  
  
###  <a name="to-edit-measure-properties"></a><a name="bkmk_edit"></a><span data-ttu-id="4f74e-123">若要編輯量值屬性</span><span class="sxs-lookup"><span data-stu-id="4f74e-123">To edit measure properties</span></span>  
  
-   <span data-ttu-id="4f74e-124">在量值方格中，按一下量值，然後在 **[屬性]** 視窗中，輸入或選取不同的屬性值。</span><span class="sxs-lookup"><span data-stu-id="4f74e-124">In the measure grid, click a measure, and then In the **Properties** window, type or select a different property value.</span></span>  
  
###  <a name="to-rename-a-measure"></a><a name="bkmk_rename"></a><span data-ttu-id="4f74e-125">若要重新命名量值</span><span class="sxs-lookup"><span data-stu-id="4f74e-125">To rename a measure</span></span>  
  
-   <span data-ttu-id="4f74e-126">在量值方格中，按一下量值，然後在 **[屬性]** 視窗的 **[量值名稱]** 中輸入新名稱，再按一下 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="4f74e-126">In the measure grid, click on a measure, and then In the **Properties** window, in **Measure Name**, type a new name, and then click ENTER.</span></span>  
  
     <span data-ttu-id="4f74e-127">您也可以在公式列中重新命名量值。</span><span class="sxs-lookup"><span data-stu-id="4f74e-127">You can also rename a measure in the formula bar.</span></span> <span data-ttu-id="4f74e-128">量值名稱之前為公式，後面接著冒號。</span><span class="sxs-lookup"><span data-stu-id="4f74e-128">The measure name precedes the formula, followed by a colon.</span></span>  
  
###  <a name="to-delete-a-measure"></a><a name="bkmk_delete"></a><span data-ttu-id="4f74e-129">若要刪除量值</span><span class="sxs-lookup"><span data-stu-id="4f74e-129">To delete a measure</span></span>  
  
-   <span data-ttu-id="4f74e-130">在量值方格的量值上按一下滑鼠右鍵，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f74e-130">In the measure grid, right-click a measure, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f74e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f74e-131">See Also</span></span>  
 <span data-ttu-id="4f74e-132">[&#40;SSAS 表格式&#41;的量值](measures-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="4f74e-132">[Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md) </span></span>  
 <span data-ttu-id="4f74e-133">[&#40;SSAS 表格式&#41;的 Kpi](kpis-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="4f74e-133">[KPIs &#40;SSAS Tabular&#41;](kpis-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="4f74e-134">導出資料行 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="4f74e-134">Calculated Columns &#40;SSAS Tabular&#41;</span></span>](ssas-calculated-columns.md)  
  
  
