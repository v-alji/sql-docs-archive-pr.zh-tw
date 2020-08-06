---
title: 將報表匯出為另一種檔案類型 (報表產生器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b577568b-ecbd-44c3-be88-31dab6fc38a2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 240d3266b7b8c9a445658a9fd21fb9ea18a4c113
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686846"
---
# <a name="export-a-report-as-another-file-type-report-builder-and-ssrs"></a><span data-ttu-id="e16a8-102">將報表匯出為其他檔案類型 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="e16a8-102">Export a Report as Another File Type (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e16a8-103">當您在報表產生器或報表設計師中預覽報表時，可以將報表轉譯為其他檔案格式，例如 CSV、影像、PDF、 [!INCLUDE[ofprword](../includes/ofprword-md.md)]或 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]，或者，當您在報表伺服器上檢視報表時，也可以轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="e16a8-103">You can render a report to another file format, such as CSV, Image, PDF, [!INCLUDE[ofprword](../includes/ofprword-md.md)], or [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)], while previewing your report in Report Builder or Report Designer, or you can render the report while viewing the report on the report server.</span></span> <span data-ttu-id="e16a8-104">如果您想要將報表立即儲存為其他檔案類型，而不要將報表發行到報表伺服器，或者您想要查看以特定格式將報表設計傳遞給報表讀者時的外觀，使用特定格式來轉譯報表會相當有用。</span><span class="sxs-lookup"><span data-stu-id="e16a8-104">Rendering the report in a specific format in is helpful when you want to immediately save the report as another file type without publishing the report to the report server or when you want to see how your report design will appear when delivered to your report readers in a specific format.</span></span> <span data-ttu-id="e16a8-105">當您設定訂閱或透過電子郵件傳遞報表時，或者，如果您想要儲存報表伺服器上提供的報表時，在報表伺服器上轉譯報表很有用。</span><span class="sxs-lookup"><span data-stu-id="e16a8-105">Rendering the report on the report server is useful when you set up subscriptions or deliver your reports via e-mail, or if you want to save a report that is available on the report server.</span></span> <span data-ttu-id="e16a8-106">如需詳細資訊，請參閱[訂閱與傳遞 &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e16a8-106">For more information, see [Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-export-a-report-as-another-file-type-in-report-builder"></a><span data-ttu-id="e16a8-107">若要在報表產生器中將報表匯出為其他檔案類型</span><span class="sxs-lookup"><span data-stu-id="e16a8-107">To export a report as another file type in Report Builder</span></span>  
  
1.  <span data-ttu-id="e16a8-108">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="e16a8-108">Preview the report.</span></span>  
  
2.  <span data-ttu-id="e16a8-109">在功能區上按一下 **[匯出]**。</span><span class="sxs-lookup"><span data-stu-id="e16a8-109">On the ribbon, click **Export**.</span></span>  
  
3.  <span data-ttu-id="e16a8-110">選取要使用的格式。</span><span class="sxs-lookup"><span data-stu-id="e16a8-110">Select the format that you want to use.</span></span>  
  
     <span data-ttu-id="e16a8-111">[另存新檔]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="e16a8-111">The **Save As** dialog box opens.</span></span> <span data-ttu-id="e16a8-112">依預設，檔案名稱就是您匯出之報表的名稱。</span><span class="sxs-lookup"><span data-stu-id="e16a8-112">By default, the file name is that of the report that you exported.</span></span> <span data-ttu-id="e16a8-113">您可以選擇變更檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="e16a8-113">Optionally, you can change the file name.</span></span>  
  
4.  <span data-ttu-id="e16a8-114">導覽至您儲存匯出之報表的位置，然後將它開啟。</span><span class="sxs-lookup"><span data-stu-id="e16a8-114">Navigate to the location where you saved the exported report and open it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e16a8-115">如果因為您沒有與此檔案類型相關聯的程式而無法以您所選擇的格式開啟報表，系統將會提示您儲存匯出的報表，或在線上尋找一個程式來開啟該報表。</span><span class="sxs-lookup"><span data-stu-id="e16a8-115">If the program cannot open the report in the format that you chose because you do not have a program associated with this file type, you will be prompted to save the exported report or to find a program online to open the report.</span></span>  
  
### <a name="to-export-a-report-as-another-file-type-in-report-manager"></a><span data-ttu-id="e16a8-116">若要在報表管理員中將報表匯出為其他檔案類型</span><span class="sxs-lookup"><span data-stu-id="e16a8-116">To export a report as another file type in Report Manager</span></span>  
  
1.  <span data-ttu-id="e16a8-117">從「報表管理員」的 **[首頁]** 頁面上，導覽至您要匯出的報表。</span><span class="sxs-lookup"><span data-stu-id="e16a8-117">From the Report Manager **Home** page, navigate to the report that you want to export.</span></span>  
  
2.  <span data-ttu-id="e16a8-118">按一下報表。</span><span class="sxs-lookup"><span data-stu-id="e16a8-118">Click the report.</span></span>  
  
     <span data-ttu-id="e16a8-119">系統便會產生報表。</span><span class="sxs-lookup"><span data-stu-id="e16a8-119">The report is generated.</span></span>  
  
3.  <span data-ttu-id="e16a8-120">在 [報表檢視器] 工具列上，按一下 **[選取格式]** 下拉箭頭。</span><span class="sxs-lookup"><span data-stu-id="e16a8-120">On the Report Viewer toolbar, click the **Select a format** drop-down arrow.</span></span>  
  
4.  <span data-ttu-id="e16a8-121">選取要使用的格式。</span><span class="sxs-lookup"><span data-stu-id="e16a8-121">Select the format that you want to use.</span></span>  
  
5.  <span data-ttu-id="e16a8-122">按一下 [匯出]  。</span><span class="sxs-lookup"><span data-stu-id="e16a8-122">Click **Export**.</span></span>  
  
     <span data-ttu-id="e16a8-123">此時會出現一個訊息，詢問您要開啟還是儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="e16a8-123">A message appears asking you if you want to open or save the file.</span></span>  
  
6.  <span data-ttu-id="e16a8-124">若要以選取的匯出格式檢視報表，按一下 **[開啟]**。</span><span class="sxs-lookup"><span data-stu-id="e16a8-124">To view the report in the selected export format, click **Open**.</span></span>  
  
     <span data-ttu-id="e16a8-125">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="e16a8-125">\- or -</span></span>  
  
     <span data-ttu-id="e16a8-126">若要以選取的匯出格式立即儲存報表，按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="e16a8-126">To immediately save the report in the selected export format, click **Save**.</span></span>  
  
     <span data-ttu-id="e16a8-127">使用與您選擇之格式相關聯的應用程式，顯示或儲存報表。</span><span class="sxs-lookup"><span data-stu-id="e16a8-127">Using the application that is associated with the format that you chose, the report is either displayed or saved.</span></span> <span data-ttu-id="e16a8-128">如果您按一下 **[儲存]**，系統會提示您儲存報表的位置。</span><span class="sxs-lookup"><span data-stu-id="e16a8-128">If you click **Save**, you will be prompted for a location where you can save your report.</span></span>  
  
     <span data-ttu-id="e16a8-129">**注意** ：如果因為您沒有與此檔案類型相關聯的程式而無法以您所選擇的格式開啟報表，系統將會提示您儲存匯出的報表，或在線上尋找一個程式來開啟該報表。</span><span class="sxs-lookup"><span data-stu-id="e16a8-129">**Note** If the program cannot open the report in the format that you chose because you do not have a program associated with this file type, you will be prompted to save the exported report or to find a program online to open the report.</span></span>  
  
### <a name="to-export-a-report-as-another-file-type-in-a-sharepoint-library"></a><span data-ttu-id="e16a8-130">若要在 SharePoint 文件庫中將報表匯出為其他檔案類型</span><span class="sxs-lookup"><span data-stu-id="e16a8-130">To export a report as another file type in a SharePoint library</span></span>  
  
1.  <span data-ttu-id="e16a8-131">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="e16a8-131">Preview the report.</span></span>  
  
2.  <span data-ttu-id="e16a8-132">在工具列上，按一下 **[動作]**，指向 **[匯出]**，然後選取您要使用的格式。</span><span class="sxs-lookup"><span data-stu-id="e16a8-132">On the toolbar, click **Actions**, point to **Export**, and then select the format that you want to use.</span></span>  
  
     <span data-ttu-id="e16a8-133">隨即開啟 **[檔案下載]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e16a8-133">The **File Download** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="e16a8-134">若要以選取的匯出格式檢視報表，按一下 **[開啟]**。</span><span class="sxs-lookup"><span data-stu-id="e16a8-134">To view the report in the selected export format, click **Open**.</span></span>  
  
     <span data-ttu-id="e16a8-135">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="e16a8-135">\- or -</span></span>  
  
     <span data-ttu-id="e16a8-136">若要以選取的匯出格式立即儲存報表，按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="e16a8-136">To immediately save the report in the selected export format, click **Save**.</span></span>  
  
     <span data-ttu-id="e16a8-137">使用與您選擇之格式相關聯的應用程式，顯示或儲存報表。</span><span class="sxs-lookup"><span data-stu-id="e16a8-137">Using the application that is associated with the format that you chose, the report is either displayed or saved.</span></span> <span data-ttu-id="e16a8-138">如果您按一下 **[儲存]**，系統會提示您儲存報表的位置。</span><span class="sxs-lookup"><span data-stu-id="e16a8-138">If you click **Save**, you will be prompted for a location where you can save your report.</span></span>  
  
     <span data-ttu-id="e16a8-139">您可以選擇變更匯出之報表的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="e16a8-139">Optionally, change the file name of the exported report.</span></span>  
  
     <span data-ttu-id="e16a8-140">**注意** ：如果因為您沒有與此檔案類型相關聯的程式而無法以您所選擇的格式開啟報表，系統將會提示您儲存匯出的報表，或在線上尋找一個程式來開啟該報表。</span><span class="sxs-lookup"><span data-stu-id="e16a8-140">**Note** If the program cannot open the report in the format that you chose because you do not have a program associated with this file type, you will be prompted to save the exported report or to find a program online to open the report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e16a8-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e16a8-141">See Also</span></span>  
 <span data-ttu-id="e16a8-142">[匯出報表 &#40;報表產生器和 SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e16a8-142">[Exporting Reports &#40;Report Builder and SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e16a8-143">[Reporting Services &#40;報表產生器和 SSRS 中的分頁&#41;](report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e16a8-143">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e16a8-144">不同報表轉譯延伸模組的互動式功能 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e16a8-144">Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;</span></span>](report-builder/interactive-functionality-different-report-rendering-extensions.md)  
  
  
