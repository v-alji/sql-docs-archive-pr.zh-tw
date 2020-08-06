---
title: 新增或刪除指標 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a8b1aac1-53ef-47a4-afc0-8fa866c6c480
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 186ed4f5b6cf7cb239dc7c33a11089c11bccae14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703874"
---
# <a name="add-or-delete-an-indicator-report-builder-and-ssrs"></a><span data-ttu-id="d9034-102">加入或刪除指標 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="d9034-102">Add or Delete an Indicator (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d9034-103">指標是最小的量測計，看一眼就可傳達單一資料值的狀態。</span><span class="sxs-lookup"><span data-stu-id="d9034-103">Indicators are minimal gauges that convey the state of a single data value at a glance.</span></span> <span data-ttu-id="d9034-104">如需指標的詳細資訊，請參閱 [指標 &#40;報表產生器及 SSRS&#41;](indicators-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d9034-104">For more information about them, see [Indicators &#40;Report Builder and SSRS&#41;](indicators-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="d9034-105">指標通常會放在資料表或矩陣的資料格中，但是您也可以單獨使用指標、與量測計並存使用，或是內嵌在量測計中。</span><span class="sxs-lookup"><span data-stu-id="d9034-105">Indicators are commonly placed in cells in a table or matrix, but you can also use indicators by themselves, side-by-side with gauges, or embedded in gauges.</span></span>  
  
 <span data-ttu-id="d9034-106">當您初次加入指標時，預設會將它設定為使用百分比做為度量單位。</span><span class="sxs-lookup"><span data-stu-id="d9034-106">When you first add an indicator, it is by default configured to use percentages as measurement units.</span></span> <span data-ttu-id="d9034-107">百分比範圍會平均分佈在指標集合的成員當中，而且指標顯示的值範圍為指標的父項，例如資料表或矩陣。</span><span class="sxs-lookup"><span data-stu-id="d9034-107">The percentage ranges are evenly distributed across members of the indicator set, and the scope of values shown by the indicator is the parent of the indicator such as a table or matrix.</span></span>  
  
 <span data-ttu-id="d9034-108">您可以更新指標的值和狀態。</span><span class="sxs-lookup"><span data-stu-id="d9034-108">You can update the values and states of indicators.</span></span> <span data-ttu-id="d9034-109">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="d9034-109">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="d9034-110">變更指標圖示和指標集合 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d9034-110">Change Indicator Icons and Indicator Sets &#40;Report Builder and SSRS&#41;</span></span>](change-indicator-icons-and-indicator-sets-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="d9034-111">設定度量單位 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d9034-111">Set and Configure Measurement Units &#40;Report Builder and SSRS&#41;</span></span>](set-and-configure-measurement-units-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="d9034-112">設定同步處理範圍 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d9034-112">Set Synchronization Scope &#40;Report Builder and SSRS&#41;</span></span>](set-synchronization-scope-report-builder-and-ssrs.md)  
  
 <span data-ttu-id="d9034-113">因為指標位於量測計面板的內部，所以當您想要使用 [指標屬性]  對話方塊或 [屬性]  窗格來設定指標時，您需要選取指標，而不是此面板。</span><span class="sxs-lookup"><span data-stu-id="d9034-113">Because an indicator is positioned inside the gauge panel, you need to select the indicator instead of the panel when you want to configure the indicator by using the **Indicators Properties** dialog box or the **Properties** pane.</span></span> <span data-ttu-id="d9034-114">下圖顯示選取的指標如何出現在它的量測計面板中。</span><span class="sxs-lookup"><span data-stu-id="d9034-114">The following picture shows a selected indicator in its gauge panel.</span></span>  
  
 <span data-ttu-id="d9034-115">![rs_GaugePanelWithIndicator](../media/rs-gaugepanelwithindicator.gif "rs_GaugePanelWithIndicator")</span><span class="sxs-lookup"><span data-stu-id="d9034-115">![rs_GaugePanelWithIndicator](../media/rs-gaugepanelwithindicator.gif "rs_GaugePanelWithIndicator")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d9034-116">根據資料值的資料行寬度和長度，資料表或矩陣資料格中的文字可能會換行，並將文字顯示在多行上。</span><span class="sxs-lookup"><span data-stu-id="d9034-116">Depending on column width and the length of data values, the text in table or matrix cells might wrap and display text on multiple lines.</span></span> <span data-ttu-id="d9034-117">發生這個情況時，指標圖示可能會伸展並變更形狀。</span><span class="sxs-lookup"><span data-stu-id="d9034-117">When this occurs, the indicator icon might be stretched and change shape.</span></span> <span data-ttu-id="d9034-118">這可能會使指標圖示較不容易讀取。</span><span class="sxs-lookup"><span data-stu-id="d9034-118">This can make the indicator icon less readable.</span></span> <span data-ttu-id="d9034-119">將指標放在矩形內部以確認圖示絕不會伸展。</span><span class="sxs-lookup"><span data-stu-id="d9034-119">Place the indicator inside a rectangle to ensure that the icon is never stretched.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-indicator-to-a-table-or-matrix"></a><span data-ttu-id="d9034-120">若要將指標加入至資料表或矩陣</span><span class="sxs-lookup"><span data-stu-id="d9034-120">To add an indicator to a table or matrix</span></span>  
  
1.  <span data-ttu-id="d9034-121">開啟現有的報表，或建立新的報表，其中包含的資料表和矩陣含有您想要顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="d9034-121">Open an existing report or create a new report that contains a table and matrix with the data you want to display.</span></span> <span data-ttu-id="d9034-122">如需詳細資訊，請參閱[資料表 &#40;報表產生器及 SSRS&#41;](tables-report-builder-and-ssrs.md) 和[矩陣 &#40;報表產生器及 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d9034-122">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) or [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="d9034-123">將資料行插入資料表或矩陣中。</span><span class="sxs-lookup"><span data-stu-id="d9034-123">Insert a column in your table or matrix.</span></span> <span data-ttu-id="d9034-124">如需詳細資訊，請參閱[插入或刪除資料行 &#40;報表產生器及 SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d9034-124">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="d9034-125">選擇性地在 [插入]  索引標籤上，按一下 [矩形]  ，然後在新的資料行中按一下資料格。</span><span class="sxs-lookup"><span data-stu-id="d9034-125">Optionally, on the **Insert** tab, click **Rectangle**, and then click a cell in the new column.</span></span>  
  
4.  <span data-ttu-id="d9034-126">在 [插入]  索引標籤上，按一下 [指標]  ，然後在新的資料行中按一下資料格。</span><span class="sxs-lookup"><span data-stu-id="d9034-126">On the **Insert** tab, click **Indicator**, and then click a cell in the new column.</span></span>  
  
     <span data-ttu-id="d9034-127">如果您已經將矩形加入至資料格，按一下該資料格。</span><span class="sxs-lookup"><span data-stu-id="d9034-127">If you added a rectangle to a cell, click that cell.</span></span>  
  
5.  <span data-ttu-id="d9034-128">在左窗格的 [Select Indicator Style] (選取指標樣式)  對話方塊中，按一下您想要的指標類型，然後按一下指標集合。</span><span class="sxs-lookup"><span data-stu-id="d9034-128">In the **Select Indicator Style** dialog box, in the left pane, click the indicator type you want, and then click the indicator set.</span></span>  
  
6.  <span data-ttu-id="d9034-129">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d9034-129">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="d9034-130">按一下指標。</span><span class="sxs-lookup"><span data-stu-id="d9034-130">Click the indicator.</span></span> <span data-ttu-id="d9034-131">[量測計資料]  窗格隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d9034-131">The **Gauge Data** pane opens.</span></span>  
  
8.  <span data-ttu-id="d9034-132">在 [值]  區域的 [(未指定)]  下拉式清單中，按一下您希望其值顯示為指標的欄位。</span><span class="sxs-lookup"><span data-stu-id="d9034-132">In the **Values** area, in the **(Unspecified)** drop-down list, click the field whose values you want to display as an indicator.</span></span>  
  
     <span data-ttu-id="d9034-133">指標會設定為使用預設值。</span><span class="sxs-lookup"><span data-stu-id="d9034-133">The indicator is configured to use default values.</span></span> <span data-ttu-id="d9034-134">根據預設，指標會設定為使用百分比當做度量單位，而且百分比範圍會平均分佈在指標的成員當中，而指標傳達的值會使用最近的群組範圍。</span><span class="sxs-lookup"><span data-stu-id="d9034-134">By default, indicators are configured use percentages as measurement units and the percentage ranges are evenly distributed across the members of the indicator and the value that the indicator conveys uses the scope of the nearest group.</span></span>  
  
### <a name="to-delete-an-indicator-to-a-table-or-matrix"></a><span data-ttu-id="d9034-135">若要刪除資料表或矩陣中的指標</span><span class="sxs-lookup"><span data-stu-id="d9034-135">To delete an indicator to a table or matrix</span></span>  
  
1.  <span data-ttu-id="d9034-136">以滑鼠右鍵按一下要刪除的指標，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="d9034-136">Right-click the indicator to delete and click **Delete**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d9034-137">指標可能會位於包含其他指標或量測計的量測計面板內部。</span><span class="sxs-lookup"><span data-stu-id="d9034-137">An indicator might be positioned inside a gauge panel that contains other indicators or gauges.</span></span> <span data-ttu-id="d9034-138">如果量測計面板包含多個項目，請務必按一下指標來將它刪除，而不是按一下量測計面板。</span><span class="sxs-lookup"><span data-stu-id="d9034-138">If the gauge panels contain multiple items, be sure to click the indicator to delete it, not the gauge panel.</span></span> <span data-ttu-id="d9034-139">如果您按一下並刪除量測計面板，量測計面板以及其中的所有項目都會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="d9034-139">If you click and then delete the gauge panel, the gauge panels and all the items in it are deleted.</span></span>  
  
2.  <span data-ttu-id="d9034-140">按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="d9034-140">Click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9034-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9034-141">See Also</span></span>  
 [<span data-ttu-id="d9034-142">指標 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d9034-142">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
