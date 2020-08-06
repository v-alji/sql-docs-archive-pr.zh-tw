---
title: 預覽檢視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.previewview.f1
helpviewer_keywords:
- Preview view [Reporting Services]
ms.assetid: 108255d1-5be8-47c1-80f3-1f2a055e4d02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1ff7c59c3ac5143d4f4103edea1a5ee309046547
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700699"
---
# <a name="preview-view"></a><span data-ttu-id="d1995-102">預覽檢視</span><span class="sxs-lookup"><span data-stu-id="d1995-102">Preview View</span></span>
  <span data-ttu-id="d1995-103">使用 **[預覽]** 檢視可顯示轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="d1995-103">Use **Preview** view to display the rendered report.</span></span> <span data-ttu-id="d1995-104">在預覽報表時，報表設計師會在本機執行報表，然後顯示在 [預覽] 檢視中。</span><span class="sxs-lookup"><span data-stu-id="d1995-104">When a report is previewed, Report Designer runs the report locally and displays it in the Preview view.</span></span> <span data-ttu-id="d1995-105">在預覽模式中，會完整處理報表。</span><span class="sxs-lookup"><span data-stu-id="d1995-105">In preview mode, the report is processed in full.</span></span> <span data-ttu-id="d1995-106">如果報表中有複雜的查詢或大量的資料，則在第一次進行檢視時，可能需要幾分鐘才能完成預覽。</span><span class="sxs-lookup"><span data-stu-id="d1995-106">If the report has a complex query or has a large amount of data, preview might take several minutes to complete the first time you view it.</span></span> <span data-ttu-id="d1995-107">若要查看只會影響報表格式的後續變更，則預覽會使用快取的資料。</span><span class="sxs-lookup"><span data-stu-id="d1995-107">For subsequent changes that affect only the format of the report, preview uses cached data.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d1995-108">當 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 以 RemoteApp 的形式執行時，報表無法顯示在 \*\*\*\* 的 [預覽] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]檢視中。</span><span class="sxs-lookup"><span data-stu-id="d1995-108">When [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] is run as a RemoteApp, reports cannot be displayed in **Preview** view in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="d1995-109">RemoteApp 程式是透過遠端桌面服務進行遠端存取的程式。</span><span class="sxs-lookup"><span data-stu-id="d1995-109">RemoteApp programs are programs that are accessed remotely through Remote Desktop Services.</span></span> <span data-ttu-id="d1995-110">如需詳細資訊，請參閱[TS RemoteApp 逐步指南](https://technet.microsoft.com/library/cc730673\(WS.10\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="d1995-110">For more information, see [TS RemoteApp Step-by-Step Guide](https://technet.microsoft.com/library/cc730673\(WS.10\).aspx).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d1995-111">選項</span><span class="sxs-lookup"><span data-stu-id="d1995-111">Options</span></span>  
 <span data-ttu-id="d1995-112">使用工具列即可管理預覽功能。</span><span class="sxs-lookup"><span data-stu-id="d1995-112">Use the toolbar to manage preview functions.</span></span>  
  
 <span data-ttu-id="d1995-113">**顯示或隱藏文件引導模式**</span><span class="sxs-lookup"><span data-stu-id="d1995-113">**Show or Hide Document Map**</span></span>  
 <span data-ttu-id="d1995-114">選擇此選項即可顯示或隱藏文字引導模式 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="d1995-114">Choose this option to show or hide the document map if one exists.</span></span>  
  
 <span data-ttu-id="d1995-115">**顯示或隱藏參數區域**</span><span class="sxs-lookup"><span data-stu-id="d1995-115">**Show or Hide Parameter Area**</span></span>  
 <span data-ttu-id="d1995-116">選擇此選項，即可為具有參數的報表顯示或隱藏參數方塊。</span><span class="sxs-lookup"><span data-stu-id="d1995-116">Choose this option to show or hide the parameters boxes for reports with parameters.</span></span>  
  
 <span data-ttu-id="d1995-117">**第一頁**</span><span class="sxs-lookup"><span data-stu-id="d1995-117">**First Page**</span></span>  
 <span data-ttu-id="d1995-118">選擇此選項即可移至報表的第一頁。</span><span class="sxs-lookup"><span data-stu-id="d1995-118">Choose this option to go to the first page of the report.</span></span>  
  
 <span data-ttu-id="d1995-119">**上一頁**</span><span class="sxs-lookup"><span data-stu-id="d1995-119">**Previous Page**</span></span>  
 <span data-ttu-id="d1995-120">選擇此選項即可移至報表的上一頁。</span><span class="sxs-lookup"><span data-stu-id="d1995-120">Choose this option to go to the previous page of the report.</span></span>  
  
 <span data-ttu-id="d1995-121">**目前的頁面**</span><span class="sxs-lookup"><span data-stu-id="d1995-121">**Current Page**</span></span>  
 <span data-ttu-id="d1995-122">顯示報表目前的頁面。</span><span class="sxs-lookup"><span data-stu-id="d1995-122">Displays the current page of the report.</span></span>  
  
 <span data-ttu-id="d1995-123">**總頁數**</span><span class="sxs-lookup"><span data-stu-id="d1995-123">**Total Pages**</span></span>  
 <span data-ttu-id="d1995-124">顯示報表的總頁數。</span><span class="sxs-lookup"><span data-stu-id="d1995-124">Displays the total number of pages in the report.</span></span>  
  
 <span data-ttu-id="d1995-125">**下一頁**</span><span class="sxs-lookup"><span data-stu-id="d1995-125">**Next Page**</span></span>  
 <span data-ttu-id="d1995-126">選擇此選項即可移至報表的下一頁。</span><span class="sxs-lookup"><span data-stu-id="d1995-126">Choose this option to go to the next page of the report.</span></span>  
  
 <span data-ttu-id="d1995-127">**最後一頁**</span><span class="sxs-lookup"><span data-stu-id="d1995-127">**Last Page**</span></span>  
 <span data-ttu-id="d1995-128">選擇此選項即可移至報表的最後一頁。</span><span class="sxs-lookup"><span data-stu-id="d1995-128">Choose this option to go to the last page of the report.</span></span>  
  
 <span data-ttu-id="d1995-129">**返回父報表**</span><span class="sxs-lookup"><span data-stu-id="d1995-129">**Back to Parent Report**</span></span>  
 <span data-ttu-id="d1995-130">選擇此選項即可移至父報表。</span><span class="sxs-lookup"><span data-stu-id="d1995-130">Choose this option to go to the parent report.</span></span> <span data-ttu-id="d1995-131">此選項用於導覽鑽研報表。</span><span class="sxs-lookup"><span data-stu-id="d1995-131">This option is used to navigate drillthrough reports.</span></span>  
  
 <span data-ttu-id="d1995-132">**停止轉譯**</span><span class="sxs-lookup"><span data-stu-id="d1995-132">**Stop Rendering**</span></span>  
 <span data-ttu-id="d1995-133">選擇此選項即可停止轉譯處理序。</span><span class="sxs-lookup"><span data-stu-id="d1995-133">Choose this option to stop the rendering process.</span></span>  
  
 <span data-ttu-id="d1995-134">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="d1995-134">**Refresh**</span></span>  
 <span data-ttu-id="d1995-135">選擇此選項可重新整理資料快取，然後再次執行報表。</span><span class="sxs-lookup"><span data-stu-id="d1995-135">Choose this option to refresh the data cache and run the report again.</span></span>  
  
 <span data-ttu-id="d1995-136">**Print**</span><span class="sxs-lookup"><span data-stu-id="d1995-136">**Print**</span></span>  
 <span data-ttu-id="d1995-137">選擇此選項即可列印報表。</span><span class="sxs-lookup"><span data-stu-id="d1995-137">Choose this option to print the report.</span></span>  
  
 <span data-ttu-id="d1995-138">**整頁模式**</span><span class="sxs-lookup"><span data-stu-id="d1995-138">**Print Layout**</span></span>  
 <span data-ttu-id="d1995-139">選擇這個選項即可切換預覽報表與報表出現在列印頁面上的檢視。</span><span class="sxs-lookup"><span data-stu-id="d1995-139">Choose this option to toggle between the preview report and the view of the report as it will appear on the printed page.</span></span>  
  
 <span data-ttu-id="d1995-140">**設定列印格式**</span><span class="sxs-lookup"><span data-stu-id="d1995-140">**Page Setup**</span></span>  
 <span data-ttu-id="d1995-141">選擇這個選項即可輕易變更頁面和列印屬性。</span><span class="sxs-lookup"><span data-stu-id="d1995-141">Choose this option to conveniently change page and print properties.</span></span> <span data-ttu-id="d1995-142">而使用 [整頁模式] 可在列印之前檢視變更。</span><span class="sxs-lookup"><span data-stu-id="d1995-142">Use Print Layout to view changes before printing.</span></span>  
  
 <span data-ttu-id="d1995-143">**匯出**</span><span class="sxs-lookup"><span data-stu-id="d1995-143">**Export**</span></span>  
 <span data-ttu-id="d1995-144">選擇此選項可使用特定的格式匯出轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="d1995-144">Choose this option to export the rendered report in a specific format.</span></span>  
  
 <span data-ttu-id="d1995-145">**縮放**</span><span class="sxs-lookup"><span data-stu-id="d1995-145">**Zoom**</span></span>  
 <span data-ttu-id="d1995-146">選取顯示比例來縮小或放大報表。</span><span class="sxs-lookup"><span data-stu-id="d1995-146">Select a zoom factor to zoom in or out on the report.</span></span>  
  
 <span data-ttu-id="d1995-147">**搜尋文字**</span><span class="sxs-lookup"><span data-stu-id="d1995-147">**Search Text**</span></span>  
 <span data-ttu-id="d1995-148">輸入文字，以在報表內搜尋相符的文字。</span><span class="sxs-lookup"><span data-stu-id="d1995-148">Type text to search for a match within the report.</span></span> <span data-ttu-id="d1995-149">您不可以使用搜尋運算子。</span><span class="sxs-lookup"><span data-stu-id="d1995-149">You cannot use search operators.</span></span> <span data-ttu-id="d1995-150">按一下 **[尋找]** 即可搜尋第一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="d1995-150">Click **Find** to search for the first instance.</span></span>  
  
 <span data-ttu-id="d1995-151">**尋找**</span><span class="sxs-lookup"><span data-stu-id="d1995-151">**Find**</span></span>  
 <span data-ttu-id="d1995-152">選擇這個選項即可開始搜尋報表，以找出搜尋文字。</span><span class="sxs-lookup"><span data-stu-id="d1995-152">Choose this option to begin searching the report for the search text.</span></span>  
  
 <span data-ttu-id="d1995-153">**找下一個**</span><span class="sxs-lookup"><span data-stu-id="d1995-153">**Find Next**</span></span>  
 <span data-ttu-id="d1995-154">選擇這個選項即可搜尋該搜尋文字的下一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="d1995-154">Choose this option to search for the next instance of the search text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1995-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1995-155">See Also</span></span>  
 <span data-ttu-id="d1995-156">[預覽報表](../reports/previewing-reports.md) </span><span class="sxs-lookup"><span data-stu-id="d1995-156">[Previewing Reports](../reports/previewing-reports.md) </span></span>  
 [<span data-ttu-id="d1995-157">報表設計師 F1 說明</span><span class="sxs-lookup"><span data-stu-id="d1995-157">Report Designer F1 Help</span></span>](report-designer-f1-help.md)  
  
  
