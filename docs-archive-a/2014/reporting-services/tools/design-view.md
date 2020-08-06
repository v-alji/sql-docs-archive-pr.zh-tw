---
title: 設計檢視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.layoutview.f1
helpviewer_keywords:
- Layout View dialog box
ms.assetid: 6fa378aa-442f-4d2f-beab-02a0fb5cd3ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e4f8f3639318062bb36d650a57f63f9033a2ae73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700741"
---
# <a name="design-view"></a><span data-ttu-id="79750-102">設計檢視</span><span class="sxs-lookup"><span data-stu-id="79750-102">Design View</span></span>
  <span data-ttu-id="79750-103">使用 [設計] 檢視，即可排列報表中的報表項目。</span><span class="sxs-lookup"><span data-stu-id="79750-103">Use Design view to arrange report items in the report.</span></span> <span data-ttu-id="79750-104">[設計] 檢視有時稱為設計介面或配置檢視。</span><span class="sxs-lookup"><span data-stu-id="79750-104">Design view is sometimes called the design surface or layout view.</span></span>  
  
## <a name="report-design-surface"></a><span data-ttu-id="79750-105">報表設計介面</span><span class="sxs-lookup"><span data-stu-id="79750-105">Report Design Surface</span></span>  
 <span data-ttu-id="79750-106">設計介面由三個區段組成：報表本文、頁首和頁尾。</span><span class="sxs-lookup"><span data-stu-id="79750-106">The design surface consists of three sections: report body, page header, and page footer.</span></span> <span data-ttu-id="79750-107">使用 [工具箱]，即可選取要放入其中任一區段中的項目。</span><span class="sxs-lookup"><span data-stu-id="79750-107">Use the Toolbox to select items to place in any of these three sections.</span></span> <span data-ttu-id="79750-108">使用 [報表資料] 窗格可檢視影像、參數、資料來源和資料集，包括資料集查詢和欄位清單。</span><span class="sxs-lookup"><span data-stu-id="79750-108">Use the Report Data pane to view images, parameters, data sources, and datasets, including dataset queries and field lists.</span></span> <span data-ttu-id="79750-109">在您將報表項目加入到設計介面之後，請將資料集欄位從 **[報表資料]** 窗格拖曳到資料區，例如資料表、矩陣或清單。</span><span class="sxs-lookup"><span data-stu-id="79750-109">After you add report items to the design surface, drag dataset fields from the **Report Data** pane onto data regions such as table, matrix, or list.</span></span> <span data-ttu-id="79750-110">報表設計介面中的每個項目都包含可利用屬性對話方塊或 [屬性] 窗格來管理的屬性。</span><span class="sxs-lookup"><span data-stu-id="79750-110">Each item on the report design surface contains properties that can be managed using a properties dialog box or the Properties pane.</span></span>  
  
## <a name="toolbox"></a><span data-ttu-id="79750-111">工具箱</span><span class="sxs-lookup"><span data-stu-id="79750-111">Toolbox</span></span>  
 <span data-ttu-id="79750-112">[工具箱] 會列出適用於您報表的資料區域和其他報表項目。</span><span class="sxs-lookup"><span data-stu-id="79750-112">The Toolbox lists data regions and other report items that are available for your report.</span></span> <span data-ttu-id="79750-113">若要從 [工具箱] 加入報表項目，按兩下該項目，或將其拖曳到設計介面上。</span><span class="sxs-lookup"><span data-stu-id="79750-113">To add report items from the Toolbox, double-click the item or drag it to the design surface.</span></span> <span data-ttu-id="79750-114">接著，您可以使用物件控點來變更形狀和大小。</span><span class="sxs-lookup"><span data-stu-id="79750-114">You can then change the shape and size by using the object handles.</span></span>  
  
## <a name="report-data-pane"></a><span data-ttu-id="79750-115">報表資料窗格</span><span class="sxs-lookup"><span data-stu-id="79750-115">Report Data Pane</span></span>  
 <span data-ttu-id="79750-116">若要檢視 [報表資料] 窗格，請按一下 **[檢視]** 功能表上的 **[報表資料]**。</span><span class="sxs-lookup"><span data-stu-id="79750-116">To view the Report Data pane, on the **View** menu, click **Report Data**.</span></span> <span data-ttu-id="79750-117">使用此窗格可定義參數、影像、資料來源和資料集，也可參考內建欄位 (例如 ReportName)。</span><span class="sxs-lookup"><span data-stu-id="79750-117">Use this pane to define parameters, images, data sources, and datasets, and to reference built-in fields such as ReportName.</span></span> <span data-ttu-id="79750-118">若要加入新項目，按一下 **[新增]** 功能表，然後選取一個項目。</span><span class="sxs-lookup"><span data-stu-id="79750-118">To add a new item, click the **New** menu and select an item.</span></span> <span data-ttu-id="79750-119">若要將導出欄位加入到現有的資料集，按一下 **[資料集]**，然後在 **[資料集屬性]** 對話方塊中選取 **[欄位]**。</span><span class="sxs-lookup"><span data-stu-id="79750-119">To add calculated fields to an existing dataset, click **Dataset**, and in the **Dataset Properties** dialog box, select **Fields**.</span></span> <span data-ttu-id="79750-120">選取一個項目，然後按一下 **[編輯]** 來開啟 **[屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="79750-120">Select an item and click **Edit** to open the **Properties** dialog box.</span></span> <span data-ttu-id="79750-121">您也可以在 [報表資料] 窗格中，以滑鼠右鍵按一下項目來加入項目或更新其屬性。</span><span class="sxs-lookup"><span data-stu-id="79750-121">You can also right-click items in the Report Data pane to add items or update their properties.</span></span>  
  
 <span data-ttu-id="79750-122">將項目從 [報表資料] 窗格拖曳至設計介面上的資料區域和文字方塊，以便將資料和影像加入到報表中。</span><span class="sxs-lookup"><span data-stu-id="79750-122">Drag items from the Report Data pane to data regions and text boxes on the design surface to add data and images to a report.</span></span>  
  
 <span data-ttu-id="79750-123">如需詳細資訊，請參閱 [Report Data Pane](../report-data/report-data-pane.md)。</span><span class="sxs-lookup"><span data-stu-id="79750-123">For more information, see [Report Data Pane](../report-data/report-data-pane.md).</span></span>  
  
## <a name="grouping-pane"></a><span data-ttu-id="79750-124">群組窗格</span><span class="sxs-lookup"><span data-stu-id="79750-124">Grouping Pane</span></span>  
 <span data-ttu-id="79750-125">群組的用途在於將報表資料組織為視覺階層以及計算總計。</span><span class="sxs-lookup"><span data-stu-id="79750-125">Groups are used to organize your report data into a visual hierarchy and to calculate totals.</span></span> <span data-ttu-id="79750-126">使用 [群組] 窗格檢視針對資料表、矩陣或清單資料區域定義的群組。</span><span class="sxs-lookup"><span data-stu-id="79750-126">Use the Grouping pane to view the groups defined for a table, matrix, or list data region.</span></span> <span data-ttu-id="79750-127">根據預設，[群組] 窗格會將所選資料區域的所有群組顯示為扁平化清單。</span><span class="sxs-lookup"><span data-stu-id="79750-127">By default, the Grouping pane displays all the groups for the selected data region as a flattened list.</span></span> <span data-ttu-id="79750-128">[圖表] 和 [量測計] 資料區域會停用 [群組] 窗格。</span><span class="sxs-lookup"><span data-stu-id="79750-128">The Grouping pane is disabled for Chart and Gauge data regions.</span></span>  
  
 <span data-ttu-id="79750-129">若要查看群組之間的關聯性，請將 [群組] 窗格切換到 [進階] 模式。</span><span class="sxs-lookup"><span data-stu-id="79750-129">To see the groups in relationship to one another, toggle the Grouping pane to Advanced mode.</span></span> <span data-ttu-id="79750-130">這個模式會在對應於每個群組的資料區域中，顯示群組成員的階層、資料格的視覺顯示。</span><span class="sxs-lookup"><span data-stu-id="79750-130">This mode displays the hierarchy of group members, a visual display of cells in the data region that correspond to each group.</span></span>  
  
 <span data-ttu-id="79750-131">如需詳細資訊，請參閱＜ [Grouping Pane](grouping-pane.md)＞。</span><span class="sxs-lookup"><span data-stu-id="79750-131">For more information, see [Grouping Pane](grouping-pane.md).</span></span>  
  
## <a name="page-header-and-page-footer"></a><span data-ttu-id="79750-132">頁首和頁尾</span><span class="sxs-lookup"><span data-stu-id="79750-132">Page Header and Page Footer</span></span>  
 <span data-ttu-id="79750-133">頁首和頁尾可以分別沿著每個頁面的頂端和底部執行。</span><span class="sxs-lookup"><span data-stu-id="79750-133">A page header and page footer run along the top and bottom of each page, respectively.</span></span> <span data-ttu-id="79750-134">頁首和頁尾可以包含靜態文字、影像、線條、矩形、框線、背景色彩，以及背景影像。</span><span class="sxs-lookup"><span data-stu-id="79750-134">Headers and footers can contain static text, images, lines, rectangles, borders, background color, and background images.</span></span> <span data-ttu-id="79750-135">若要將報表項目加入到頁首或頁尾，以滑鼠右鍵按一下設計介面，然後選取 [頁首] 或 [頁尾]。</span><span class="sxs-lookup"><span data-stu-id="79750-135">To add report items to the header or footer, right-click the design surface and select Header or Footer.</span></span> <span data-ttu-id="79750-136">頁首和頁尾區段就會出現在設計介面上。</span><span class="sxs-lookup"><span data-stu-id="79750-136">Header and footer sections appear on the design surface.</span></span>  
  
## <a name="properties-pane"></a><span data-ttu-id="79750-137">屬性窗格</span><span class="sxs-lookup"><span data-stu-id="79750-137">Properties Pane</span></span>  
 <span data-ttu-id="79750-138">使用 [屬性] 窗格可檢視目前在設計介面上選取之報表項目的屬性，或是檢視目前在 [群組] 窗格中選取之群組的屬性。</span><span class="sxs-lookup"><span data-stu-id="79750-138">Use the Properties pane to view properties for the currently selected report item on the design surface or the currently selected group in the Grouping pane.</span></span> <span data-ttu-id="79750-139">或者，您也可以用滑鼠右鍵按一下選取的報表項目或群組，然後按一下 [屬性]\*\*\*\*，為此報表項目或群組開啟對應的 [屬性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="79750-139">Alternatively, you can right-click on a selected report item or group and then click **Properties** to open the corresponding **Properties** dialog box for the report item or group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79750-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79750-140">See Also</span></span>  
 <span data-ttu-id="79750-141">[頁首和頁尾 &#40;報表產生器和 SSRS&#41;](../report-design/page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="79750-141">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](../report-design/page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="79750-142">報表設計提示 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="79750-142">Report Design Tips &#40;Report Builder and SSRS&#41;</span></span>](../report-design/report-design-tips-report-builder-and-ssrs.md)  
  
  
