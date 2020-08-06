---
title: 報表、報表組件和報表定義 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report definitions
- reports
ms.assetid: 2d746550-f8cc-4e97-8a06-d0f03cffc18d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0926de326d0b5859e895d69da4dd2ad7863ccd2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599351"
---
# <a name="reports-report-parts-and-report-definitions-report-builder-and-ssrs"></a><span data-ttu-id="ae866-102">報表、報表組件和報表定義 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="ae866-102">Reports, Report Parts, and Report Definitions (Report Builder and SSRS)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="ae866-103">會使用各種詞彙來描述不同狀態的報表，這些狀態包括初始定義、已發行的報表以及使用者檢視的報表。</span><span class="sxs-lookup"><span data-stu-id="ae866-103">uses a variety of terms to describe a report in different states, including the initial definition, the published report, and the viewed report as it appears to the user.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-definition-rdl-files"></a><span data-ttu-id="ae866-104">報表定義 (.rdl) 檔案</span><span class="sxs-lookup"><span data-stu-id="ae866-104">Report Definition (.rdl) Files</span></span>  
 <span data-ttu-id="ae866-105">報表定義是您在報表產生器或報表設計師中建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="ae866-105">A report definition is a file that you create in Report Builder or Report Designer.</span></span> <span data-ttu-id="ae866-106">它提供資料來源連接、用於擷取資料之查詢、運算式、參數、影像、文字方塊、資料表，以及您可能包含在報表中之其他任何設計階段元素的完整描述。</span><span class="sxs-lookup"><span data-stu-id="ae866-106">It provides a complete description of data source connections, queries used to retrieve data, expressions, parameters, images, text boxes, tables, and any other design-time elements that you might include in a report.</span></span> <span data-ttu-id="ae866-107">雖然報表定義可以很複雜，不過它至少會指定查詢和其他報表內容、報表屬性，以及報表配置。</span><span class="sxs-lookup"><span data-stu-id="ae866-107">Although report definitions can be complex, at a minimum they specify a query and other report content, report properties, and a report layout.</span></span>  
  
 <span data-ttu-id="ae866-108">報表定義會在執行階段轉譯成已處理的報表。</span><span class="sxs-lookup"><span data-stu-id="ae866-108">Report definitions are rendered at run time as a processed report.</span></span> <span data-ttu-id="ae866-109">這時候，系統會從資料來源中擷取資料，並且根據報表定義中的指示格式化這項資料。</span><span class="sxs-lookup"><span data-stu-id="ae866-109">At that time, the data is retrieved from the data source and formatted according to the instructions in the report definition.</span></span> <span data-ttu-id="ae866-110">您可以直接從電腦執行報表定義並儲存在本機，也可以將它發行到報表伺服器，讓其他人執行。</span><span class="sxs-lookup"><span data-stu-id="ae866-110">A report definition can be run directly from your computer and saved locally, or it can be published to a report server for others to run as well.</span></span>  
  
 <span data-ttu-id="ae866-111">報表定義是以符合 XML 文法 (稱為報表定義語言 (RDL)) 的 XML 所撰寫。</span><span class="sxs-lookup"><span data-stu-id="ae866-111">Report definitions are written in XML that conforms to an XML grammar called Report Definition Language (RDL).</span></span> <span data-ttu-id="ae866-112">RDL 描述 XML 元素，包含報表可能出現的所有可能變化。</span><span class="sxs-lookup"><span data-stu-id="ae866-112">RDL describes the XML elements, encompassing all possible variations that a report can assume.</span></span>  
  
## <a name="client-report-definition-rdlc-files"></a><span data-ttu-id="ae866-113">用戶端報表定義 (.rdlc) 檔案</span><span class="sxs-lookup"><span data-stu-id="ae866-113">Client Report Definition (.rdlc) Files</span></span>  
 <span data-ttu-id="ae866-114">Visual Studio 報表設計師會產生可搭配 ReportViewer 控制項使用的用戶端報表定義 (.rdlc) 檔案。</span><span class="sxs-lookup"><span data-stu-id="ae866-114">The Visual Studio Report Designer produces client report definition (.rdlc) files for use with the ReportViewer control.</span></span> <span data-ttu-id="ae866-115">這些 .rdlc 檔案可轉換成 .rdl 檔案，以搭配 Reporting Services 報表設計師使用。</span><span class="sxs-lookup"><span data-stu-id="ae866-115">The .rdlc files can be converted to .rdl files for use with Reporting Services Report Designer.</span></span>  
  
## <a name="report-part-rsc-files"></a><span data-ttu-id="ae866-116">報表組件檔 (.rsc)</span><span class="sxs-lookup"><span data-stu-id="ae866-116">Report Part (.rsc) Files</span></span>  
 <span data-ttu-id="ae866-117">報表組件定義是報表定義檔的 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="ae866-117">A report part definition is an XML fragment of a report definition file.</span></span> <span data-ttu-id="ae866-118">您可藉由建立報表定義，然後選取報表中的報表項目個別發行為報表組件，藉此建立報表組件。</span><span class="sxs-lookup"><span data-stu-id="ae866-118">You create report parts by creating a report definition, and then selecting report items in the report to publish separately as report parts.</span></span> <span data-ttu-id="ae866-119">報表組件包括資料區、矩形與其包含的項目，以及影像。</span><span class="sxs-lookup"><span data-stu-id="ae866-119">Report parts include data regions, rectangles and their contained items, and images.</span></span> <span data-ttu-id="ae866-120">您可以將報表組件與其相依的資料集和共用資料來源參考一併儲存，以便於其他報表中重複使用。</span><span class="sxs-lookup"><span data-stu-id="ae866-120">You can save a report part with its dependent datasets and shared data source references so it can be reused in other reports.</span></span>  
  
 [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
## <a name="published-reports"></a><span data-ttu-id="ae866-121">已發行的報表</span><span class="sxs-lookup"><span data-stu-id="ae866-121">Published Reports</span></span>  
 <span data-ttu-id="ae866-122">建立 .rdl 檔案之後，您就可以將它儲存在本機，也可以將它儲存至報表伺服器上的個人資料夾 (例如 [我的報表] 資料夾)。</span><span class="sxs-lookup"><span data-stu-id="ae866-122">After you create an .rdl file, you can save it locally, or save it to a personal folder (such as the My Reports folder) on the report server.</span></span> <span data-ttu-id="ae866-123">報表可供其他人查看時，可以將它從報表產生器儲存到報表伺服器上的公用資料夾，然後透過報表管理員上載或是從報表設計師部署報表專案方案的方式來發行該報表。</span><span class="sxs-lookup"><span data-stu-id="ae866-123">When the report is ready for others to see, you publish it by saving it from Report Builder to a public folder on the report server, uploading it through Report Manager, or deploying a report project solution from Report Designer.</span></span> <span data-ttu-id="ae866-124">已發行的報表是儲存在報表伺服器資料庫中，並在報表伺服器或 SharePoint 網站上管理的項目。</span><span class="sxs-lookup"><span data-stu-id="ae866-124">A published report is an item that is stored in a report server database and managed on a report server or SharePoint site.</span></span>  
  
 <span data-ttu-id="ae866-125">已發行的報表會透過使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 以角色為基礎之安全性模型的角色指派來維護其安全。</span><span class="sxs-lookup"><span data-stu-id="ae866-125">A published report is secured through role assignments using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] role-based security model.</span></span> <span data-ttu-id="ae866-126">您可以透過 URL、SharePoint Web 組件或報表管理員存取已發行的報表，也可以在報表產生器中導覽並開啟它們。</span><span class="sxs-lookup"><span data-stu-id="ae866-126">Published reports are accessed through URLs, SharePoint Web parts, or Report Manager, or you can navigate to and open them in Report Builder.</span></span>  
  
### <a name="report-snapshots"></a><span data-ttu-id="ae866-127">報表快照集</span><span class="sxs-lookup"><span data-stu-id="ae866-127">Report Snapshots</span></span>  
 <span data-ttu-id="ae866-128">您也可以將報表當做快照集來發行 (其中包含報表一開始執行時的配置資訊和資料)。</span><span class="sxs-lookup"><span data-stu-id="ae866-128">A report can also be published as a snapshot that contains both layout information and data as of the time the report was initially run.</span></span> <span data-ttu-id="ae866-129">報表快照集不會以特定轉譯格式儲存。</span><span class="sxs-lookup"><span data-stu-id="ae866-129">Report snapshots are not saved in a particular rendering format.</span></span> <span data-ttu-id="ae866-130">而是只有在使用者或應用程式要求它時，報表快照集才以最後的檢視格式轉譯 (例如 HTML)。</span><span class="sxs-lookup"><span data-stu-id="ae866-130">Instead, report snapshots are rendered in a final viewing format (such as HTML) only when a user or an application requests it.</span></span> <span data-ttu-id="ae866-131">如需詳細資訊，請參閱[在報表管理員中尋找及檢視報表 &#40;報表產生器及 SSRS&#41;](../report-builder/finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ae866-131">For more information, see [Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;](../report-builder/finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md).</span></span>  
  
## <a name="rendered-reports"></a><span data-ttu-id="ae866-132">已轉譯的報表</span><span class="sxs-lookup"><span data-stu-id="ae866-132">Rendered Reports</span></span>  
 <span data-ttu-id="ae866-133">已轉譯的報表是一種完全處理的報表，其中包含採用適合檢視之格式 (例如 HTML) 的資料與配置資訊。</span><span class="sxs-lookup"><span data-stu-id="ae866-133">A rendered report is a fully processed report that contains both data and layout information in a format suitable for viewing (such as HTML).</span></span> <span data-ttu-id="ae866-134">報表要等到轉譯成輸出格式後，才能夠檢視。</span><span class="sxs-lookup"><span data-stu-id="ae866-134">Until a report is rendered into an output format, it cannot be viewed.</span></span> <span data-ttu-id="ae866-135">您可以執行下列任一種動作來轉譯報表：</span><span class="sxs-lookup"><span data-stu-id="ae866-135">You can render a report by doing one of the following:</span></span>  
  
-   <span data-ttu-id="ae866-136">在報表產生器或報表設計師中建立或開啟報表並且執行它。</span><span class="sxs-lookup"><span data-stu-id="ae866-136">Create or open a report in Report Builder or Report Designer and run it.</span></span>  
  
-   <span data-ttu-id="ae866-137">在報表管理員中尋找並執行報表。</span><span class="sxs-lookup"><span data-stu-id="ae866-137">Find and run a report in Report Manager.</span></span>  
  
-   <span data-ttu-id="ae866-138">在與 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表伺服器整合的 SharePoint 網站上尋找並執行報表。</span><span class="sxs-lookup"><span data-stu-id="ae866-138">Find and run a report on a SharePoint site that is integrated with a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server.</span></span>  
  
-   <span data-ttu-id="ae866-139">訂閱報表，訂閱的報表會以您指定的輸出格式傳遞到電子郵件收件匣或檔案共用。</span><span class="sxs-lookup"><span data-stu-id="ae866-139">Subscribe to a report, which is delivered to an e-mail inbox or a file share in an output format that you specify.</span></span>  
  
 <span data-ttu-id="ae866-140">訂閱報表，訂閱的報表會以您指定的輸出格式傳遞到電子郵件收件匣或檔案共用。報表的預設轉譯格式為 HTML 4.0。</span><span class="sxs-lookup"><span data-stu-id="ae866-140">Subscribe to a report, which is delivered to an e-mail inbox or a file share in an output format that you specify.The default rendering format for a report is HTML 4.0.</span></span> <span data-ttu-id="ae866-141">除了 HTML 以外，報表還可以使用許多輸出格式轉譯，包括 Excel、Word、XML、PDF、TIFF 與 CSV。</span><span class="sxs-lookup"><span data-stu-id="ae866-141">In addition to HTML, reports can be rendered in a variety of output formats, including Excel, Word, XML, PDF, TIFF, and CSV.</span></span> <span data-ttu-id="ae866-142">如同已發行的報表一樣，已轉譯的報表也無法編輯或回存到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ae866-142">As with published reports, rendered reports cannot be edited or saved back to a report server.</span></span> <span data-ttu-id="ae866-143">如需詳細資訊，請參閱[匯出報表 &#40;報表產生器和 SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ae866-143">For more information, see [Exporting Reports &#40;Report Builder and SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae866-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae866-144">See Also</span></span>  
 <span data-ttu-id="ae866-145">[報表撰寫概念 &#40;報表產生器和 SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ae866-145">[Report Authoring Concepts &#40;Report Builder and SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ae866-146">[SQL Server 2014 中的報表產生器](../report-builder/report-builder-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="ae866-146">[Report Builder in SQL Server 2014](../report-builder/report-builder-in-sql-server-2016.md) </span></span>  
 <span data-ttu-id="ae866-147">[安裝、卸載和報表產生器支援](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="ae866-147">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 <span data-ttu-id="ae866-148">[尋找、查看和管理報表 &#40;報表產生器和 SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ae866-148">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ae866-149">匯出報表 &#40;報表產生器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ae866-149">Exporting Reports &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
