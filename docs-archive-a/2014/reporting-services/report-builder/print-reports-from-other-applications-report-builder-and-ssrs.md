---
title: 從其他應用程式列印報表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a5560581-fd57-4a45-b7ea-43b21a8a7419
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 58fee2cf31601dc638eebd69a13727a805408ac0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702490"
---
# <a name="print-reports-from-other-applications-report-builder-and-ssrs"></a><span data-ttu-id="6a4ca-102">從其他應用程式列印報表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6a4ca-102">Print Reports from Other Applications (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6a4ca-103">報表產生器提供匯出選項，可以讓您輕鬆地在其他應用程式中檢視報表。</span><span class="sxs-lookup"><span data-stu-id="6a4ca-103">Report Builder provides an export option that allows you to easily view a report in other applications.</span></span> <span data-ttu-id="6a4ca-104">`Export` 命令提供於報表工具列上，當您在瀏覽器或網路架構應用程式中開啟報表時，此工具列會出現在報表頂端。</span><span class="sxs-lookup"><span data-stu-id="6a4ca-104">The `Export` command is available on the report toolbar that appears at the top of a report when you open it in a browser or Web-based application.</span></span> <span data-ttu-id="6a4ca-105">匯出報表會將報表顯示在不同的應用程式中 (例如，如果將報表匯出至 Excel，就會在 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]中開啟報表)。</span><span class="sxs-lookup"><span data-stu-id="6a4ca-105">Exporting a report displays it in a different application (for example, exporting a report to Excel opens the report in [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]).</span></span> <span data-ttu-id="6a4ca-106">若要列印，則建議只有當應用程式有您要使用的特定列印功能時，您才匯出報表。</span><span class="sxs-lookup"><span data-stu-id="6a4ca-106">For printing purposes, exporting a report is recommended only if the application has specific printing features that you want to use.</span></span>  
  
 <span data-ttu-id="6a4ca-107">若要將報表匯出至另一個應用程式，您必須已安裝該應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a4ca-107">To export a report to another application, you must have that application installed.</span></span> <span data-ttu-id="6a4ca-108">例如，在匯出為 Acrobat (PDF) 格式之前，您必須在電腦中安裝 Adobe Acrobat Reader。</span><span class="sxs-lookup"><span data-stu-id="6a4ca-108">For example, you must have Adobe Acrobat Reader installed on your computer before you can export to the Acrobat (PDF) format.</span></span> <span data-ttu-id="6a4ca-109">如果選擇將報表匯出成 TIFF 格式，報表伺服器就會將報表放入與 TIFF 檔案類型關聯的檢視應用程式中。</span><span class="sxs-lookup"><span data-stu-id="6a4ca-109">If you choose to export a report to TIFF format, the report server places the report in a viewing application that is associated with the TIFF file type.</span></span> <span data-ttu-id="6a4ca-110">雖然使用的應用程式會視您的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 版本而定，但通常此工具為 Windows 圖片和傳真檢視器。</span><span class="sxs-lookup"><span data-stu-id="6a4ca-110">Although the application used depends on which version of [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows you have, typically this tool is Windows Picture and Fax Viewer.</span></span> <span data-ttu-id="6a4ca-111">預設的解析度對應於螢幕解析度 96 DPI。</span><span class="sxs-lookup"><span data-stu-id="6a4ca-111">The default resolution corresponds to a screen resolution of 96 dots per inch (DPI).</span></span> <span data-ttu-id="6a4ca-112">您可以將 Windows 圖片和傳真檢視器的解析度增加至 300 DPI 或 600 DPI，以符合印表機的功能。</span><span class="sxs-lookup"><span data-stu-id="6a4ca-112">You can increase the resolution in Windows Picture and Fax Viewer to 300 DPI or 600 DPI to match the capabilities of your printer.</span></span> <span data-ttu-id="6a4ca-113">如需有關調整解析度的詳細資訊，請參閱 Windows 產品文件集。</span><span class="sxs-lookup"><span data-stu-id="6a4ca-113">For more information about adjusting the resolution, see the Windows product documentation.</span></span>  
  
 <span data-ttu-id="6a4ca-114">如果您選擇網頁封存 (亦稱為 MHTML)，則報表將匯出至預設的瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="6a4ca-114">If you choose Web archive (also known as MHTML), the report is exported to your default browser.</span></span> <span data-ttu-id="6a4ca-115">從瀏覽器列印會造成在每一頁的底端加入報表路徑資訊。</span><span class="sxs-lookup"><span data-stu-id="6a4ca-115">Printing from the browser may result in report path information being added at the bottom of every page.</span></span> <span data-ttu-id="6a4ca-116">在大部份的情況下，您可以設定瀏覽器選項，使其省略列印頁面上的路徑資訊。</span><span class="sxs-lookup"><span data-stu-id="6a4ca-116">In most cases, you can set browser options to omit path information on a printed page.</span></span> <span data-ttu-id="6a4ca-117">如需詳細資訊，請參閱您使用之瀏覽器的產品文件集。</span><span class="sxs-lookup"><span data-stu-id="6a4ca-117">For more information, see the product documentation for the browser you are using.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6a4ca-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a4ca-118">See Also</span></span>  
 <span data-ttu-id="6a4ca-119">[列印報表 &#40;報表產生器及 SSRS&#41;](print-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6a4ca-119">[Print a Report &#40;Report Builder and SSRS&#41;](print-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6a4ca-120">[使用列印控制項從瀏覽器列印報表 &#40;報表產生器和 SSRS&#41;](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6a4ca-120">[Print Reports from a Browser with the Print Control &#40;Report Builder and SSRS&#41;](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6a4ca-121">[匯出報表 &#40;報表產生器和 SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6a4ca-121">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6a4ca-122">[將報表匯出為另一種檔案類型 &#40;報表產生器和 SSRS&#41;](../export-a-report-as-another-file-type-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6a4ca-122">[Export a Report as Another File Type &#40;Report Builder and SSRS&#41;](../export-a-report-as-another-file-type-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6a4ca-123">尋找、檢視和管理報表 &#40;報表產生器及 SSRS &#41;</span><span class="sxs-lookup"><span data-stu-id="6a4ca-123">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
