---
title: 在報表伺服器網站上偵測到 (Upgrade Advisor) 的 ISAPI 篩選器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- ISAPI filters
- report servers [Reporting Services], upgrade issues
ms.assetid: dd30560d-9e16-47c7-ba68-a9743a657e4e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bff1834ddf1b8f90787a47a8fd58a240d2b715d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708077"
---
# <a name="isapi-filters-detected-on-the-report-server-site-upgrade-advisor"></a><span data-ttu-id="8cba4-102">在報表伺服器站台上偵測到 ISAPI 篩選器 (Upgrade Advisor)</span><span class="sxs-lookup"><span data-stu-id="8cba4-102">ISAPI filters detected on the report server site (Upgrade Advisor)</span></span>
  <span data-ttu-id="8cba4-103">Upgrade Advisor 在主控報表伺服器和報表管理員虛擬目錄的網站上偵測到一個或多個 ISAPI 篩選器。</span><span class="sxs-lookup"><span data-stu-id="8cba4-103">Upgrade Advisor detected one or more ISAPI filters on the Web site that hosts the report server and Report Manager virtual directories.</span></span> <span data-ttu-id="8cba4-104">中不支援 ISAPI 篩選器 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8cba4-104">ISAPI filters are not supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
||  
|-|  
|<span data-ttu-id="8cba4-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]自有.</span><span class="sxs-lookup"><span data-stu-id="8cba4-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native .</span></span>|  
  
## <a name="component"></a><span data-ttu-id="8cba4-106">元件</span><span class="sxs-lookup"><span data-stu-id="8cba4-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="8cba4-107">描述</span><span class="sxs-lookup"><span data-stu-id="8cba4-107">Description</span></span>  
 <span data-ttu-id="8cba4-108">升級之前，請確認網站上的 ISAPI 篩選器是否由 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 應用程式所使用。</span><span class="sxs-lookup"><span data-stu-id="8cba4-108">Before upgrading, verify whether the ISAPI filters on the Web site are used by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applications.</span></span> <span data-ttu-id="8cba4-109">如果您不需要 ISAPI 篩選器，就可以升級報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="8cba4-109">If you do not require the ISAPI filter, you can upgrade the report server.</span></span> <span data-ttu-id="8cba4-110">安裝程式將建立預設 URL，但不支援在 IIS 中執行的 ISAPI 篩選器。</span><span class="sxs-lookup"><span data-stu-id="8cba4-110">Setup will create the default URLs, without support for the ISAPI filter that runs in IIS.</span></span> <span data-ttu-id="8cba4-111">如果您需要 ISAPI 篩選器，在您找到主控 ISAPI 篩選器的替代方式 (例如，使用 ISA Server 或繼續在 IIS 中主控 ISAPI 篩選器) 以前，請勿進行升級。</span><span class="sxs-lookup"><span data-stu-id="8cba4-111">If you require the ISAPI filter, do not upgrade until you find an alternative way of hosting the ISAPI filter (for example, using ISA Server or continuing to host the ISAPI filter in IIS).</span></span> <span data-ttu-id="8cba4-112">在特定狀況中，報表伺服器支援 ASP.NET HTTPModules 當做 ISAPI 篩選器的取代項目。</span><span class="sxs-lookup"><span data-stu-id="8cba4-112">The report server supports ASP.NET HTTPModules as a replacement for ISAPI filters in certain scenarios.</span></span> <span data-ttu-id="8cba4-113">如需詳細資訊，請參閱 MSDN 上的 ASP.NET 文件集。</span><span class="sxs-lookup"><span data-stu-id="8cba4-113">For more information, see the ASP.NET documentation on MSDN.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="8cba4-114">更正動作</span><span class="sxs-lookup"><span data-stu-id="8cba4-114">Corrective Action</span></span>  
 <span data-ttu-id="8cba4-115">請評估並使用不同的解決方案來主控部署所需要的 ISAPI 篩選器。</span><span class="sxs-lookup"><span data-stu-id="8cba4-115">Evaluate and use a separate solution for hosting ISAPI filters required by your deployment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cba4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cba4-116">See Also</span></span>  
 [<span data-ttu-id="8cba4-117">&#40;Upgrade Advisor Reporting Services 升級問題&#41;</span><span class="sxs-lookup"><span data-stu-id="8cba4-117">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
