---
title: 查看 Cube 架構 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 82fc715c-e08e-447d-8fc8-9c9005f145f0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e7d324db1e0c41588694031d3c121fdb47233f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707921"
---
# <a name="view-the-cube-schema"></a><span data-ttu-id="33544-102">檢視 Cube 結構描述</span><span class="sxs-lookup"><span data-stu-id="33544-102">View the Cube Schema</span></span>
  <span data-ttu-id="33544-103">**[Cube 設計師]** 之 **[Cube 結構]** 索引標籤的 **[資料來源檢視]** 窗格顯示 Cube 結構描述。</span><span class="sxs-lookup"><span data-stu-id="33544-103">The **Data Source View** pane of the **Cube Structure** tab in **Cube Designer** displays the cube schema.</span></span> <span data-ttu-id="33544-104">結構描述是一組衍生 Cube 量值和維度的來源資料表。</span><span class="sxs-lookup"><span data-stu-id="33544-104">The schema is the set of tables from which the measures and dimensions for a cube are derived.</span></span> <span data-ttu-id="33544-105">每一個 Cube 結構描述是由一個或多個事實資料表及一個或多個維度資料表所組成，Cube 中的量值和維度會以這些資料表為基礎。</span><span class="sxs-lookup"><span data-stu-id="33544-105">Every cube schema consists of one or more fact tables and one or more dimension tables on which the measures and dimensions in the cube are based.</span></span>  
  
 <span data-ttu-id="33544-106">**[Cube 結構]** 索引標籤的 **[資料來源檢視]** 窗格顯示做為 Cube 基礎之資料來源檢視的圖表。</span><span class="sxs-lookup"><span data-stu-id="33544-106">The **Data Source View** pane of the **Cube Structure** tab displays a diagram of the data source view on which the cube is based.</span></span> <span data-ttu-id="33544-107">此圖表是資料來源檢視主要圖表的子集。</span><span class="sxs-lookup"><span data-stu-id="33544-107">This diagram is a subset of the main diagram of the data source view.</span></span> <span data-ttu-id="33544-108">您可以隱藏及顯示 **[資料來源檢視]** 窗格中的資料表，以及檢視任何現有的圖表。</span><span class="sxs-lookup"><span data-stu-id="33544-108">You can hide and show tables in the **Data Source View** pane and view any existing diagrams.</span></span> <span data-ttu-id="33544-109">但是，您無法變更基礎結構描述 (例如將新關聯性或具名查詢加入基礎結構描述)。</span><span class="sxs-lookup"><span data-stu-id="33544-109">However, you cannot make changes (such as adding new relationships or named queries) to the underlying schema.</span></span> <span data-ttu-id="33544-110">若要變更結構描述，請使用資料來源檢視設計工具。</span><span class="sxs-lookup"><span data-stu-id="33544-110">To make changes to the schema, use Data Source View Designer.</span></span>  
  
 <span data-ttu-id="33544-111">當您建立 Cube 時，顯示在 **[Cube 結構]** 索引標籤之 **[資料來源檢視]** 窗格中的圖表，一開始會與專案或資料庫之資料來源檢視中的 **[顯示所有資料表]** 圖表相同。</span><span class="sxs-lookup"><span data-stu-id="33544-111">When you create a cube, the diagram displayed in the **Data Source View** pane of the **Cube Structure** tab is initially the same as the **Show All Tables** diagram in the data source view for the project or database.</span></span> <span data-ttu-id="33544-112">您可以使用資料來源檢視中的任何現有圖表來取代此圖表，並在 **[資料來源檢視]** 窗格中進行調整。</span><span class="sxs-lookup"><span data-stu-id="33544-112">You can replace this diagram with any existing diagram in the data source view and make adjustments in the **Data Source View** pane.</span></span>  
  
 <span data-ttu-id="33544-113">當您在 **[Cube 設計師]** 中使用圖表時， **[資料來源檢視]** 功能表會提供作用於索引標籤或索引標籤中任何所選物件的命令。</span><span class="sxs-lookup"><span data-stu-id="33544-113">While you work with the diagram in **Cube Designer**, commands that act on the tab or on any selected object in the tab are available on the **Data Source View** menu.</span></span> <span data-ttu-id="33544-114">您也可以在圖表背景或圖表中的任何物件上按一下滑鼠右鍵，以使用作用於圖表或所選物件的命令。</span><span class="sxs-lookup"><span data-stu-id="33544-114">You can also right-click the background of the diagram or any object in the diagram to use commands that act on the diagram or selected object.</span></span> <span data-ttu-id="33544-115">您可以：</span><span class="sxs-lookup"><span data-stu-id="33544-115">You can:</span></span>  
  
-   <span data-ttu-id="33544-116">在圖表和樹狀格式之間進行切換。</span><span class="sxs-lookup"><span data-stu-id="33544-116">Switch between diagram and tree formats.</span></span>  
  
-   <span data-ttu-id="33544-117">排列、尋找、顯示及隱藏資料表。</span><span class="sxs-lookup"><span data-stu-id="33544-117">Arrange, find, show, and hide tables.</span></span>  
  
-   <span data-ttu-id="33544-118">顯示易記名稱。</span><span class="sxs-lookup"><span data-stu-id="33544-118">Show friendly names.</span></span>  
  
-   <span data-ttu-id="33544-119">切換配置。</span><span class="sxs-lookup"><span data-stu-id="33544-119">Switch layouts.</span></span>  
  
-   <span data-ttu-id="33544-120">變更縮放比例。</span><span class="sxs-lookup"><span data-stu-id="33544-120">Change the magnification.</span></span>  
  
-   <span data-ttu-id="33544-121">檢視屬性。</span><span class="sxs-lookup"><span data-stu-id="33544-121">View properties.</span></span>  
  
 <span data-ttu-id="33544-122">此外，您可以執行下表中所列的動作：</span><span class="sxs-lookup"><span data-stu-id="33544-122">Additionally, you can perform the actions listed in the following table:</span></span>  
  
|<span data-ttu-id="33544-123">收件者</span><span class="sxs-lookup"><span data-stu-id="33544-123">To</span></span>|<span data-ttu-id="33544-124">執行方式</span><span class="sxs-lookup"><span data-stu-id="33544-124">Do this</span></span>|  
|--------|-------------|  
|<span data-ttu-id="33544-125">使用 Cube 之資料來源檢視中的圖表</span><span class="sxs-lookup"><span data-stu-id="33544-125">Use a diagram from the data source view of the cube</span></span>|<span data-ttu-id="33544-126">在 **[資料來源檢視]** 功能表上，指向 **[複製圖表來源]**，然後按一下您要使用的資料來源檢視圖表。</span><span class="sxs-lookup"><span data-stu-id="33544-126">On the **Data Source View** menu, point to **Copy Diagram from**, and then click the data source view diagram you want to use.</span></span><br /><br /> <span data-ttu-id="33544-127">- 或 -</span><span class="sxs-lookup"><span data-stu-id="33544-127">- or -</span></span><br /><br /> <span data-ttu-id="33544-128">以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\* 窗格的背景，然後指向 [複製圖表來源]\*\*\*\*，再按一下資料來源檢視中您想要的圖表。</span><span class="sxs-lookup"><span data-stu-id="33544-128">Right-click the background of the **Data Source View** pane, point to **Copy Diagram from**, and then click the diagram in the data source view that you want.</span></span> <span data-ttu-id="33544-129">此方法會建立單獨的圖表複本，讓您在 **[Cube 產生器]** 索引標籤上所做的任何變更不會出現在原始圖表中。</span><span class="sxs-lookup"><span data-stu-id="33544-129">This method creates an independent copy of the diagram, so any changes you make on the **Cube Builder** tab do not appear in the original diagram.</span></span>|  
|<span data-ttu-id="33544-130">僅顯示 Cube 所使用的資料表</span><span class="sxs-lookup"><span data-stu-id="33544-130">Show only the tables that are used in the cube</span></span>|<span data-ttu-id="33544-131">在 **[資料來源檢視]** 功能表上，按一下 **[僅顯示使用過的資料表]**。</span><span class="sxs-lookup"><span data-stu-id="33544-131">On the **Data Source View** menu, click **Show Only Used Tables**.</span></span><br /><br /> <span data-ttu-id="33544-132">- 或 -</span><span class="sxs-lookup"><span data-stu-id="33544-132">- or -</span></span><br /><br /> <span data-ttu-id="33544-133">以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\* 窗格的背景，然後按一下 [僅顯示使用過的資料表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33544-133">Right-click the background of the **Data Source View** pane, and then click **Show Only Used Tables**.</span></span>|  
|<span data-ttu-id="33544-134">編輯資料來源檢視結構描述</span><span class="sxs-lookup"><span data-stu-id="33544-134">Edit the data source view schema</span></span>|<span data-ttu-id="33544-135">在 **[資料來源檢視]** 功能表上，按一下 **[編輯資料來源檢視]**。</span><span class="sxs-lookup"><span data-stu-id="33544-135">On the **Data Source View** menu, click **Edit Data Source View**.</span></span><br /><br /> <span data-ttu-id="33544-136">- 或 -</span><span class="sxs-lookup"><span data-stu-id="33544-136">- or -</span></span><br /><br /> <span data-ttu-id="33544-137">以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\* 窗格的背景，然後按一下 [編輯資料來源檢視]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33544-137">Right-click the background of the **Data Source View** pane, and then click **Edit Data Source View**.</span></span>|  
  
  
