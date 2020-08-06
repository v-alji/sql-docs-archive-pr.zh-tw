---
title: 修改量值 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7bd48810-15ce-45ff-862b-372d08606995
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd352cbca1d21f5842e075d9cb8e5e766aa369b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598637"
---
# <a name="modifying-measures"></a><span data-ttu-id="29528-102">修改量值</span><span class="sxs-lookup"><span data-stu-id="29528-102">Modifying Measures</span></span>
  <span data-ttu-id="29528-103">您可以使用 [FormatString]\*\*\*\* 屬性來定義格式設定，以便控制向使用者顯示量值的方式。</span><span class="sxs-lookup"><span data-stu-id="29528-103">You can use the **FormatString** property to define formatting settings that control how measures are displayed to users.</span></span> <span data-ttu-id="29528-104">在這項工作中，您在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 中指定貨幣和百分比量值的格式化屬性。</span><span class="sxs-lookup"><span data-stu-id="29528-104">In this task, you specify formatting properties for the currency and percentage measures in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>  
  
### <a name="to-modify-the-measures-of-the-cube"></a><span data-ttu-id="29528-105">若要修改 Cube 的量值</span><span class="sxs-lookup"><span data-stu-id="29528-105">To modify the measures of the cube</span></span>  
  
1.  <span data-ttu-id="29528-106">針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube，切換到 [Cube 設計師] 的 [Cube 結構]\*\*\*\* 索引標籤，並展開 [量值]\*\*\*\* 窗格中的 [網際網路銷售]\*\*\*\* 量值群組，然後以滑鼠右鍵按一下 [訂購數量]\*\*\*\*，再按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="29528-106">Switch to the **Cube Structure** tab of Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, expand the **Internet Sales** measure group in the **Measures** pane, right-click **Order Quantity**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="29528-107">在 [屬性] 視窗中，按一下 [自動隱藏]\*\*\*\* 圖釘圖示來固定開啟 [屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="29528-107">In the Properties window, click the **Auto Hide** pushpin icon to pin the Properties window open.</span></span>  
  
     <span data-ttu-id="29528-108">當 [屬性] 視窗保持開啟時，要在 Cube 中變更數個項目的屬性會更加容易。</span><span class="sxs-lookup"><span data-stu-id="29528-108">It is easier to change properties for several items in the cube when the Properties window remains open.</span></span>  
  
3.  <span data-ttu-id="29528-109">在 [屬性] 視窗中，按一下 [FormatString]\*\*\*\* 清單，然後輸入 **#,#**。</span><span class="sxs-lookup"><span data-stu-id="29528-109">In the Properties window, click the **FormatString** list, and then type **#,#**.</span></span>  
  
4.  <span data-ttu-id="29528-110">在 [Cube 結構]\*\*\*\* 索引標籤的工具列上，按一下左側的 [顯示量值方格]\*\*\*\* 圖示。</span><span class="sxs-lookup"><span data-stu-id="29528-110">On the toolbar of the **Cube Structure** tab, click the **Show Measures Grid** icon on the left.</span></span>  
  
     <span data-ttu-id="29528-111">方格檢視可讓您同時選取多個量值。</span><span class="sxs-lookup"><span data-stu-id="29528-111">The grid view lets you select multiple measures at the same time.</span></span>  
  
5.  <span data-ttu-id="29528-112">選取下列量值。</span><span class="sxs-lookup"><span data-stu-id="29528-112">Select the following measures.</span></span> <span data-ttu-id="29528-113">您可以在按住 CTRL 鍵的同時，按一下每個量值，藉以選取多個量值：</span><span class="sxs-lookup"><span data-stu-id="29528-113">You can select multiple measures by clicking each while holding down the CTRL key:</span></span>  
  
    -   <span data-ttu-id="29528-114">**Unit Price**</span><span class="sxs-lookup"><span data-stu-id="29528-114">**Unit Price**</span></span>  
  
    -   <span data-ttu-id="29528-115">**擴充量**</span><span class="sxs-lookup"><span data-stu-id="29528-115">**Extended Amount**</span></span>  
  
    -   <span data-ttu-id="29528-116">**折扣量**</span><span class="sxs-lookup"><span data-stu-id="29528-116">**Discount Amount**</span></span>  
  
    -   <span data-ttu-id="29528-117">**產品標準成本**</span><span class="sxs-lookup"><span data-stu-id="29528-117">**Product Standard Cost**</span></span>  
  
    -   <span data-ttu-id="29528-118">**產品總成本**</span><span class="sxs-lookup"><span data-stu-id="29528-118">**Total Product Cost**</span></span>  
  
    -   <span data-ttu-id="29528-119">**銷售量**</span><span class="sxs-lookup"><span data-stu-id="29528-119">**Sales Amount**</span></span>  
  
    -   <span data-ttu-id="29528-120">**稅額**</span><span class="sxs-lookup"><span data-stu-id="29528-120">**Tax Amt**</span></span>  
  
    -   <span data-ttu-id="29528-121">**Freight**</span><span class="sxs-lookup"><span data-stu-id="29528-121">**Freight**</span></span>  
  
6.  <span data-ttu-id="29528-122">在 [屬性] 視窗的 [FormatString]\*\*\*\* 清單中，選取 [貨幣]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="29528-122">In the Properties window, in the **FormatString** list, select **Currency**.</span></span>  
  
7.  <span data-ttu-id="29528-123">在 [屬性] 視窗 (標題列正下方) 頂端的下拉式清單中，選取 [單價折扣百分比]\*\*\*\* 量值，然後選取 [FormatString]\*\*\*\* 清單中的 [百分比]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="29528-123">In the drop-down list at the top of the Properties window (right below the title bar), select the measure **Unit Price Discount Pct**, and then select **Percent** in the **FormatString** list.</span></span>  
  
8.  <span data-ttu-id="29528-124">在 [屬性視窗中，將 [**單價折扣百分比**] 量值的 [**名稱**] 屬性變更為 `Unit Price Discount Percentage` 。</span><span class="sxs-lookup"><span data-stu-id="29528-124">In the Properties window, change the **Name** property for the **Unit Price Discount Pct** measure to `Unit Price Discount Percentage`.</span></span>  
  
9. <span data-ttu-id="29528-125">在 [**量值**] 窗格中，按一下 [**稅金 Amt** ]，並將此量值的名稱變更為 `Tax Amount` 。</span><span class="sxs-lookup"><span data-stu-id="29528-125">In the **Measures** pane, click **Tax Amt** and change the name of this measure to `Tax Amount`.</span></span>  
  
10. <span data-ttu-id="29528-126">在 [屬性] 視窗中，按一下 [自動隱藏]\*\*\*\* 圖示隱藏 [屬性] 視窗，然後按一下 [Cube 結構]\*\*\*\* 索引標籤的工具列上的 [顯示量值樹狀目錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="29528-126">In the Properties window, click the **Auto Hide** icon to hide the Properties window, and then click **Show Measures Tree** on the toolbar of the **Cube Structure** tab.</span></span>  
  
11. <span data-ttu-id="29528-127">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="29528-127">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="29528-128">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="29528-128">Next Task in Lesson</span></span>  
 [<span data-ttu-id="29528-129">修改客戶維度</span><span class="sxs-lookup"><span data-stu-id="29528-129">Modifying the Customer Dimension</span></span>](lesson-3-2-modifying-the-customer-dimension.md)  
  
## <a name="see-also"></a><span data-ttu-id="29528-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29528-130">See Also</span></span>  
 <span data-ttu-id="29528-131">[定義資料庫維度](multidimensional-models/define-database-dimensions.md) </span><span class="sxs-lookup"><span data-stu-id="29528-131">[Define Database Dimensions](multidimensional-models/define-database-dimensions.md) </span></span>  
 [<span data-ttu-id="29528-132">設定量值屬性</span><span class="sxs-lookup"><span data-stu-id="29528-132">Configure Measure Properties</span></span>](multidimensional-models/configure-measure-properties.md)  
  
  
