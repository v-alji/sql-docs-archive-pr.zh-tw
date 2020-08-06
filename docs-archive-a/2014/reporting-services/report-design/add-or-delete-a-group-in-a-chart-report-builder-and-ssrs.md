---
title: 在圖表中新增或刪除群組 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0445b0ac-acae-4462-80fb-fe9735ac66db
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2ac558ccbd8855018877228b2b38debf769f1573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707138"
---
# <a name="add-or-delete-a-group-in-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="0ff58-102">在圖表中加入或刪除群組 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="0ff58-102">Add or Delete a Group in a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="0ff58-103">在圖表資料區域中按一下，以顯示 **[圖表資料]** 窗格。</span><span class="sxs-lookup"><span data-stu-id="0ff58-103">Click in the chart data region to display the **Chart Data** pane.</span></span> <span data-ttu-id="0ff58-104">將資料集欄位拖曳到 **[類別目錄群組]** 和 **[數列群組]** 區域來建立群組。</span><span class="sxs-lookup"><span data-stu-id="0ff58-104">Create groups by dragging dataset fields to the **Category Groups** and **Series Groups** areas.</span></span> <span data-ttu-id="0ff58-105">若要加入巢狀群組，請將多個欄位加入至該區域。</span><span class="sxs-lookup"><span data-stu-id="0ff58-105">To add nested groups, add multiple fields to the area.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-parent-or-child-group-to-a-chart"></a><span data-ttu-id="0ff58-106">將父群組或子群組加入至圖表中</span><span class="sxs-lookup"><span data-stu-id="0ff58-106">To add a parent or child group to a chart</span></span>  
  
1.  <span data-ttu-id="0ff58-107">在報表設計介面上，按一下圖表中的任意位置來選取它。</span><span class="sxs-lookup"><span data-stu-id="0ff58-107">On the report design surface, click anywhere in the chart to select it.</span></span> <span data-ttu-id="0ff58-108">隨即出現 [圖表資料]  窗格。</span><span class="sxs-lookup"><span data-stu-id="0ff58-108">The **Chart Data** pane appears.</span></span>  
  
2.  <span data-ttu-id="0ff58-109">從 **[報表資料]** 視窗將欄位拖曳到 **[類別目錄群組]** 和 **[數列群組]** 區域。</span><span class="sxs-lookup"><span data-stu-id="0ff58-109">Drag a field from the **Report Data** window to the **Category Groups** or **Series Groups** area.</span></span> <span data-ttu-id="0ff58-110">若要加入父群組，請將游標放在現有群組的前方。</span><span class="sxs-lookup"><span data-stu-id="0ff58-110">To add a parent group, position the cursor in front of an existing group.</span></span> <span data-ttu-id="0ff58-111">若要加入子群組，則將游標放在現有群組的後方。</span><span class="sxs-lookup"><span data-stu-id="0ff58-111">To add a child group, position the cursor after an existing group.</span></span>  
  
### <a name="to-edit-a-category-group-on-a-chart"></a><span data-ttu-id="0ff58-112">編輯圖表上的類別目錄群組</span><span class="sxs-lookup"><span data-stu-id="0ff58-112">To edit a category group on a chart</span></span>  
  
1.  <span data-ttu-id="0ff58-113">在報表設計介面上，按一下圖表中的任意位置來選取它。</span><span class="sxs-lookup"><span data-stu-id="0ff58-113">On the report design surface, click anywhere in the chart to select it.</span></span> <span data-ttu-id="0ff58-114">隨即出現 [圖表資料]  窗格。</span><span class="sxs-lookup"><span data-stu-id="0ff58-114">The **Chart Data** pane appears.</span></span>  
  
2.  <span data-ttu-id="0ff58-115">以滑鼠右鍵按一下 [類別目錄群組]  區域中的群組，然後按一下 [類別目錄群組屬性]  。</span><span class="sxs-lookup"><span data-stu-id="0ff58-115">Right-click the group in the **Category Groups** area, and then click **Category Group Properties**.</span></span>  
  
3.  <span data-ttu-id="0ff58-116">加入或移除群組運算式、篩選、排序運算式和群組變數。</span><span class="sxs-lookup"><span data-stu-id="0ff58-116">Add or remove group expressions, filters, sort expressions, and group variables.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-a-series-group-on-a-chart"></a><span data-ttu-id="0ff58-117">編輯圖表上的數列群組</span><span class="sxs-lookup"><span data-stu-id="0ff58-117">To edit a series group on a chart</span></span>  
  
1.  <span data-ttu-id="0ff58-118">在報表設計介面上，按一下圖表中的任意位置來選取它。</span><span class="sxs-lookup"><span data-stu-id="0ff58-118">On the report design surface, click anywhere in the chart to select it.</span></span> <span data-ttu-id="0ff58-119">隨即出現 [圖表資料]  窗格。</span><span class="sxs-lookup"><span data-stu-id="0ff58-119">The **Chart Data** pane appears.</span></span>  
  
2.  <span data-ttu-id="0ff58-120">以滑鼠右鍵按一下 [數列群組]  區域中的群組，然後按一下 [數列群組屬性]  。</span><span class="sxs-lookup"><span data-stu-id="0ff58-120">Right-click the group in the **Series Groups** area, and then click **Series Group Properties**.</span></span>  
  
3.  <span data-ttu-id="0ff58-121">加入或移除群組運算式、篩選、排序運算式和群組變數。</span><span class="sxs-lookup"><span data-stu-id="0ff58-121">Add or remove group expressions, filters, sort expressions, and group variables.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-group-from-a-chart"></a><span data-ttu-id="0ff58-122">從圖表刪除群組</span><span class="sxs-lookup"><span data-stu-id="0ff58-122">To delete a group from a chart</span></span>  
  
1.  <span data-ttu-id="0ff58-123">在報表設計介面上，按一下圖表中的任意位置來選取它。</span><span class="sxs-lookup"><span data-stu-id="0ff58-123">On the report design surface, click anywhere in the chart to select it.</span></span> <span data-ttu-id="0ff58-124">隨即出現 [圖表資料]  窗格。</span><span class="sxs-lookup"><span data-stu-id="0ff58-124">The **Chart Data** pane appears.</span></span>  
  
2.  <span data-ttu-id="0ff58-125">以滑鼠右鍵按一下 [類別目錄群組]  或 [數列群組]  區域中的群組，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="0ff58-125">Right-click the group in the **Category Groups** or **Series Groups** area, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ff58-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ff58-126">See Also</span></span>  
 [<span data-ttu-id="0ff58-127">圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0ff58-127">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
