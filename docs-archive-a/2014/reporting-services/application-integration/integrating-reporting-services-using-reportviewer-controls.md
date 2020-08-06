---
title: 使用 ReportViewer 控制項整合 Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- ReportViewer controls
- integrating reports [Reporting Services]
ms.assetid: 3ba47fb4-73a9-4059-89fd-329adebe94a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 18e28dbf1557bf36106b454738d0c0bfc037f2a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585160"
---
# <a name="integrating-reporting-services-using-the-reportviewer-controls"></a><span data-ttu-id="e7a51-102">使用 ReportViewer 控制項整合 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="e7a51-102">Integrating Reporting Services Using the ReportViewer Controls</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="e7a51-103">[!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)]提供兩個 ReportViewer 控制項，可將報表檢視功能整合到您的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="e7a51-103">[!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] provides two ReportViewer controls for integrating report viewing functionality into your applications.</span></span> <span data-ttu-id="e7a51-104">一個版本是用於 Windows Form 應用程式，另一個版本則是用於 Web Form 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e7a51-104">There is a version for Windows Forms-based applications and one for Web Forms applications.</span></span> <span data-ttu-id="e7a51-105">每個控制項都提供類似的功能，但是每個功能都是針對其個別的環境所設計的。</span><span class="sxs-lookup"><span data-stu-id="e7a51-105">Each control provides similar functionality but each is designed to target their individual environments.</span></span> <span data-ttu-id="e7a51-106">這兩個控制項都可以處理已部署至報表伺服器的報表 (遠端處理模式) 或已複製到尚未 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝 (本機處理模式) 的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e7a51-106">Both controls can process reports that have been deployed to a report server (remote processing mode) or have been copied to a computer where [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] has not been installed (local processing mode).</span></span>  
  
 <span data-ttu-id="e7a51-107">ReportViewer 控制項並未內建支援動態適應具備不同螢幕解析度之不同裝置的功能。</span><span class="sxs-lookup"><span data-stu-id="e7a51-107">The ReportViewer control does not include built-in support for dynamically adapting to different devices with different screen resolutions.</span></span>  
  
## <a name="remote-processing-mode"></a><span data-ttu-id="e7a51-108">遠端處理模式</span><span class="sxs-lookup"><span data-stu-id="e7a51-108">Remote Processing Mode</span></span>  
 <span data-ttu-id="e7a51-109">遠端處理模式是檢視已經部署到報表伺服器之報表的建議使用方法。</span><span class="sxs-lookup"><span data-stu-id="e7a51-109">Remote processing mode is the preferred method for viewing reports that have been deployed to a report server.</span></span> <span data-ttu-id="e7a51-110">遠端處理模式提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="e7a51-110">Remote processing mode provides the following advantages:</span></span>  
  
-   <span data-ttu-id="e7a51-111">遠端處理可提供執行報表最佳化的方案，因為報表伺服器會處理報表。</span><span class="sxs-lookup"><span data-stu-id="e7a51-111">Remote processing provides an optimized solution for running reports because the report is processed by the report server.</span></span>  
  
-   <span data-ttu-id="e7a51-112">因為報表伺服器會處理所有的程序，所以報表要求可在向外延展部署中由多部報表伺服器處理，或在單一向上延展案例中由具備多個處理器的伺服器處理。</span><span class="sxs-lookup"><span data-stu-id="e7a51-112">Because all processing is handled by the report server, a report request can be processed by multiple report servers in a scale-out deployment or a server that has multiple processors in a scale-up scenario.</span></span>  
  
 <span data-ttu-id="e7a51-113">此外，在遠端模式中執行的報表可以利用報表伺服器的完整功能，包括所有的轉譯與資料延伸模組。</span><span class="sxs-lookup"><span data-stu-id="e7a51-113">In addition, reports run in remote mode can utilize the full functionality of the report server including all rendering and data extensions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7a51-114">當 ReportViewer 控制項在遠端處理模式下執行時，其可用的延伸模組清單須視安裝在報表伺服器上的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 版本而定。</span><span class="sxs-lookup"><span data-stu-id="e7a51-114">The list of extensions available to the ReportViewer control when it is running in remote processing mode depends on the edition of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] that is installed on the report server.</span></span>  
  
## <a name="local-processing-mode"></a><span data-ttu-id="e7a51-115">本機處理模式</span><span class="sxs-lookup"><span data-stu-id="e7a51-115">Local Processing Mode</span></span>  
 <span data-ttu-id="e7a51-116">本機處理模式提供替代的方法，可在未安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的情況下檢視和轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="e7a51-116">Local processing mode provides an alternative method for viewing and rendering reports when [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is not installed.</span></span> <span data-ttu-id="e7a51-117">與遠端處理不同的是，只有報表伺服器提供的功能子集可在控制項中使用。</span><span class="sxs-lookup"><span data-stu-id="e7a51-117">Unlike remote processing only a subset of the functionality provided by the report server is available in the control.</span></span> <span data-ttu-id="e7a51-118">在本機處理模式中，資料處理不是由控制項來進行，而是由主機應用程式所實作。</span><span class="sxs-lookup"><span data-stu-id="e7a51-118">In local processing mode, data processing is not handled by the control but rather implemented by the hosting application.</span></span> <span data-ttu-id="e7a51-119">但是，報表處理是由控制項本身所處理。</span><span class="sxs-lookup"><span data-stu-id="e7a51-119">However report processing is handled by the control itself.</span></span> <span data-ttu-id="e7a51-120">在本機處理模式中，只能使用 PDF、Excel、Word 和 Image 轉譯延伸模組。</span><span class="sxs-lookup"><span data-stu-id="e7a51-120">In local processing mode, only the PDF, Excel, Word, and Image rendering extensions are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a51-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7a51-121">See Also</span></span>  
 <span data-ttu-id="e7a51-122">[將 Reporting Services 整合至應用程式](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="e7a51-122">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 [<span data-ttu-id="e7a51-123">使用 Visual Studio (Blog) 建立 SSRS 報表</span><span class="sxs-lookup"><span data-stu-id="e7a51-123">Create SSRS Reports Using Visual Studio (Blog)</span></span>](https://jwcooney.com/2015/01/07/ssrs-basics-set-up-visual-studio-to-write-a-new-ssrs-report/)  
  
  
