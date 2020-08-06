---
title: 報表產生器 SQL Server 2014 的新功能&#39;|Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8223c19b-4b0d-4b1d-a042-9a726c18e708
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ce72af225130bc3f081a53008a303c5213db636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597010"
---
# <a name="what39s-new-in-report-builder-for-sql-server-2014"></a><span data-ttu-id="60a7c-102">SQL Server 2014 報表產生器的新功能&#39;</span><span class="sxs-lookup"><span data-stu-id="60a7c-102">What&#39;s New in Report Builder for SQL Server 2014</span></span>
  <span data-ttu-id="60a7c-103">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 導入了許多 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="60a7c-103">The [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] introduces a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features.</span></span>  
  
 <span data-ttu-id="60a7c-104">如需此版本中其他產品和技術之功能的相關資訊 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] ，請參閱[SQL Server 2014 中的新](../sql-server/what-s-new-in-sql-server-2016.md)功能。</span><span class="sxs-lookup"><span data-stu-id="60a7c-104">For information about features in this release for other [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] products and technologies, see [What's New in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="60a7c-105">如需有關此版本中新功能的最新資訊和資源，請參閱[SQL Server Reporting Services (SSRS) 的新功能的其他資訊](https://go.microsoft.com/fwlink/?LinkId=207147)。</span><span class="sxs-lookup"><span data-stu-id="60a7c-105">For the most recent information and resources regarding new features in this release, see [Additional information on what is new in SQL Server Reporting Services (SSRS)](https://go.microsoft.com/fwlink/?LinkId=207147).</span></span>  
  
##  <a name="excel-renderer-for-microsoft-excel-2007-2010-and-microsoft-excel-2003"></a><a name="ExcelRenderer"></a><span data-ttu-id="60a7c-106">適用于 Microsoft Excel 2007-2010 和 Microsoft Excel 2003 的 excel 轉譯器</span><span class="sxs-lookup"><span data-stu-id="60a7c-106">Excel Renderer for Microsoft Excel 2007-2010 and Microsoft Excel 2003</span></span>  
 <span data-ttu-id="60a7c-107">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Excel 轉譯延伸模組是 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 新功能，它會將報表轉譯為相容於 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2007-2010 以及已安裝 Microsoft Office Word、Excel 和 PowerPoint 相容性套件的 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2003 的 Excel 文件。</span><span class="sxs-lookup"><span data-stu-id="60a7c-107">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Excel rendering extension, new in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], renders a report as an Excel document that is compatible with [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2007-2010 as well as [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint installed.</span></span> <span data-ttu-id="60a7c-108">此格式為 Office Open XML，其副檔名為 .xlsx。</span><span class="sxs-lookup"><span data-stu-id="60a7c-108">The format is Office Open XML and the file extension of files is .xlsx.</span></span>  
  
 <span data-ttu-id="60a7c-109">此 Excel 轉譯延伸模組移除了舊版的限制，可與 Excel 2003 相容。</span><span class="sxs-lookup"><span data-stu-id="60a7c-109">This Excel-rendering extension removes limitations of the earlier version, compatible with Excel 2003.</span></span> <span data-ttu-id="60a7c-110">以下列出轉譯延伸模組中的改進功能：</span><span class="sxs-lookup"><span data-stu-id="60a7c-110">The following lists the improvement in the rendering extension:</span></span>  
  
-   <span data-ttu-id="60a7c-111">每個工作表的資料列上限為 1,048,576。</span><span class="sxs-lookup"><span data-stu-id="60a7c-111">Maximum rows per worksheet is 1,048,576.</span></span>  
  
-   <span data-ttu-id="60a7c-112">每個工作表的資料行上限為 16,384。</span><span class="sxs-lookup"><span data-stu-id="60a7c-112">Maximum columns per worksheet is 16,384.</span></span>  
  
-   <span data-ttu-id="60a7c-113">工作表中允許的色彩數目約為 1600 萬 (24 位元色彩)。</span><span class="sxs-lookup"><span data-stu-id="60a7c-113">Number of colors allowed in a worksheet is approximately 16 million (24-bit color).</span></span>  
  
-   <span data-ttu-id="60a7c-114">ZIP 壓縮提供較小的檔案大小。</span><span class="sxs-lookup"><span data-stu-id="60a7c-114">ZIP compression provides smaller files sizes.</span></span>  
  
 <span data-ttu-id="60a7c-115">如需詳細資訊，請參閱 [匯出至 Microsoft Excel &#40;報表產生器及 SSRS&#41;](report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)中使用這項資料。</span><span class="sxs-lookup"><span data-stu-id="60a7c-115">For more information, see [Exporting to Microsoft Excel &#40;Report Builder and SSRS&#41;](report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="word-renderer-for-microsoft-word-2007-2010-and-microsoft-word-2003"></a><a name="WordRenderer"></a><span data-ttu-id="60a7c-116">適用于 Microsoft Word 2007-2010 和 Microsoft Word 2003 的 word 轉譯器</span><span class="sxs-lookup"><span data-stu-id="60a7c-116">Word Renderer for Microsoft Word 2007-2010 and Microsoft Word 2003</span></span>  
 <span data-ttu-id="60a7c-117">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Word 轉譯延伸模組是 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 的新功能，它會將報表轉譯為相容於 [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2007-2010 以及已安裝 [!INCLUDE[ofprword](../includes/ofprword-md.md)] Office Word、Excel 和 PowerPoint 相容性套件的 [!INCLUDE[msCoName](../includes/msconame-md.md)] 2003 的 Word 文件。</span><span class="sxs-lookup"><span data-stu-id="60a7c-117">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Word rendering extension, new in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], renders a report as a Word document that is compatible with [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2007-2010 as well as [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2003 with the [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Compatibility Pack for Word, Excel, and PowerPoint installed.</span></span> <span data-ttu-id="60a7c-118">此格式為 Office Open XML，其副檔名為 docx。</span><span class="sxs-lookup"><span data-stu-id="60a7c-118">The format is Office Open XML and the file extension of files is docx.</span></span>  
  
 <span data-ttu-id="60a7c-119">除了讓 Word 2007-2010 新功能用於匯出的報表之外，匯出的報表 \*.docx 檔案通常較小。</span><span class="sxs-lookup"><span data-stu-id="60a7c-119">In addition to making the features that are new in Word 2007-2010 available to exported reports, \*.docx files of exported reports tend to be smaller.</span></span> <span data-ttu-id="60a7c-120">使用 Word 轉譯器所匯出的報表通常比使用 Word 2003 轉譯器所匯出的相同報表小得多。</span><span class="sxs-lookup"><span data-stu-id="60a7c-120">Reports exported by using the Word renderer are typically significantly smaller than the same reports exported by using the Word 2003 renderer.</span></span>  
  
 <span data-ttu-id="60a7c-121">如需詳細資訊，請參閱 [匯出至 Microsoft Word &#40;報表產生器及 SSRS&#41;](report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md)中使用這項資料。</span><span class="sxs-lookup"><span data-stu-id="60a7c-121">For more information, see [Exporting to Microsoft Word &#40;Report Builder and SSRS&#41;](report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60a7c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60a7c-122">See Also</span></span>  
 [<span data-ttu-id="60a7c-123">SQL Server 2014 中的報表產生器</span><span class="sxs-lookup"><span data-stu-id="60a7c-123">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
