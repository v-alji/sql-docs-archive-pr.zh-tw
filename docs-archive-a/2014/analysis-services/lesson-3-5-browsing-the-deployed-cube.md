---
title: 流覽已部署的 Cube |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 849c6109-1453-4fe4-a892-c49a982cfadb
author: minewiskan
ms.author: owend
ms.openlocfilehash: b876c8b2876aaf4ad28b0f4ea3fb8bab32cd787b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597432"
---
# <a name="browsing-the-deployed-cube"></a><span data-ttu-id="ba350-102">瀏覽已部署的 Cube</span><span class="sxs-lookup"><span data-stu-id="ba350-102">Browsing the Deployed Cube</span></span>
  <span data-ttu-id="ba350-103">在下列工作中，您將瀏覽 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube。</span><span class="sxs-lookup"><span data-stu-id="ba350-103">In the following task, you browse the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="ba350-104">我們的分析會跨多個維度比較量值，因此您將使用 Excel 樞紐分析表瀏覽資料。</span><span class="sxs-lookup"><span data-stu-id="ba350-104">Because our analysis compares measure across multiple dimensions, you will use an Excel PivotTable to browse your data.</span></span> <span data-ttu-id="ba350-105">使用樞紐分析表可讓您將客戶、日期和產品資訊放在不同的軸上，讓您可以看到跨特定時間週期、客戶人口統計資料和產品線檢視時，[網際網路銷售] 如何變更。</span><span class="sxs-lookup"><span data-stu-id="ba350-105">Using a PivotTable lets you place customer, date, and product information on different axes so that you can see how Internet Sales change when viewed across specific time periods, customer demographics, and product lines.</span></span>  
  
### <a name="to-browse-the-deployed-cube"></a><span data-ttu-id="ba350-106">瀏覽已部署的 Cube</span><span class="sxs-lookup"><span data-stu-id="ba350-106">To browse the deployed cube</span></span>  
  
1.  <span data-ttu-id="ba350-107">若要切換至中的 [Cube 設計師] [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] ，請在 [方案總管的 [ **cube]** 資料夾中，按兩下 [ \*\* [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學\*\*課程] Cube。</span><span class="sxs-lookup"><span data-stu-id="ba350-107">To switch to Cube Designer in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], double-click the **[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial** cube in the **Cubes** folder of the Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="ba350-108">開啟 [瀏覽器]\*\*\*\* 索引標籤，然後按一下設計師工具列上的 [重新連接]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ba350-108">Open the **Browser** tab, and then click the **Reconnect** button on the toolbar of the designer.</span></span>  
  
3.  <span data-ttu-id="ba350-109">按一下 Excel 圖示，啟動 Excel，並使用工作空間資料庫做為資料來源。</span><span class="sxs-lookup"><span data-stu-id="ba350-109">Click the Excel icon to launch Excel using the workspace database as the data source.</span></span> <span data-ttu-id="ba350-110">出現啟用連接的提示時，按一下 [啟用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba350-110">When prompted to enable connections, click **Enable**.</span></span>  
  
4.  <span data-ttu-id="ba350-111">在樞紐分析表欄位清單中，展開 [網際網路銷售]\*\*\*\*，然後將 [銷售量]\*\*\*\* 量值拖曳至 [值]\*\*\*\* 區域中。</span><span class="sxs-lookup"><span data-stu-id="ba350-111">In the PivotTable Field List, expand **Internet Sales**, and then drag the **Sales Amount** measure to the **Values** area.</span></span>  
  
5.  <span data-ttu-id="ba350-112">在樞紐分析表欄位清單中，展開 [產品]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba350-112">In the PivotTable Field List, expand **Product**.</span></span>  
  
6.  <span data-ttu-id="ba350-113">將 [產品型號線]\*\*\*\* 使用者階層拖曳至 [資料行]\*\*\*\* 區域。</span><span class="sxs-lookup"><span data-stu-id="ba350-113">Drag the **Product Model Lines** user hierarchy to the **Columns** area.</span></span>  
  
7.  <span data-ttu-id="ba350-114">在樞紐分析表欄位清單中，依序展開 [客戶]\*\*\*\* 和 [位置]\*\*\*\*，然後從 [客戶] 維度的 [位置] 顯示資料夾，將 [客戶地理位置]\*\*\*\* 階層拖曳到 [資料列]\*\*\*\* 區域。</span><span class="sxs-lookup"><span data-stu-id="ba350-114">In the PivotTable Field List, expand **Customer**, expand **Location**, and then drag the **Customer Geography** hierarchy from the Location display folder in the Customer dimension to the **Rows** area.</span></span>  
  
8.  <span data-ttu-id="ba350-115">在樞紐分析表欄位清單中，展開 [訂購日期]\*\*\*\*，然後將 [Order Date.Calendar Date]\*\*\*\* 階層拖曳到 [報表篩選]\*\*\*\* 區域。</span><span class="sxs-lookup"><span data-stu-id="ba350-115">In the PivotTable Field List, expand **Order Date**, and then drag the **Order Date.Calendar Date** hierarchy to the **Report Filter** area.</span></span>  
  
9. <span data-ttu-id="ba350-116">按一下資料窗格中 [Order Date.Calendar Date]\*\*\*\* 篩選右邊的箭頭、清除 [(全部)]\*\*\*\* 層級的核取方塊、依序展開 [2006]\*\*\*\*、[H1 CY 2006]\*\*\*\* 和 [Q1 CY 2006]\*\*\*\*、選取 [February 2006]\*\*\*\* 的核取方塊，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba350-116">Click the arrow to the right of the **Order Date.Calendar Date** filter in the data pane, clear the check box for the **(All)** level, expand **2006**, expand **H1 CY 2006**, expand **Q1 CY 2006**, select the check box for **February 2006**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ba350-117">此時會出現按區域的網際網路銷售量和 2006 年 2 月的當月產品線，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ba350-117">Internet sales by region and product line for the month of February, 2006 appear as shown in the following image.</span></span>  
  
     <span data-ttu-id="ba350-118">![依區域和產品線區分的網際網路銷售額](../../2014/tutorials/media/l3-cube-browser-finish.gif "依區域和產品線區分的網際網路銷售額")</span><span class="sxs-lookup"><span data-stu-id="ba350-118">![Internet sales by region and product line](../../2014/tutorials/media/l3-cube-browser-finish.gif "Internet sales by region and product line")</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="ba350-119">下一課</span><span class="sxs-lookup"><span data-stu-id="ba350-119">Next Lesson</span></span>  
 [<span data-ttu-id="ba350-120">第4課：定義 Advanced 屬性和維度屬性</span><span class="sxs-lookup"><span data-stu-id="ba350-120">Lesson 4: Defining Advanced Attribute and Dimension Properties</span></span>](lesson-4-defining-advanced-attribute-and-dimension-properties.md)  
  
  
