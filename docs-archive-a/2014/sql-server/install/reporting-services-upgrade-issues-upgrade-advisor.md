---
title: 升級建議程式 (Reporting Services 升級問題) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], upgrade issues
- Reporting Services, upgrades
- upgrading Reporting Services
- report servers [Reporting Services], upgrade issues
ms.assetid: d9663f25-98d7-4508-ae3c-55a7277211bd
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 569afe735d68a724c0b4cc61ad2b7767088c2b30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606595"
---
# <a name="reporting-services-upgrade-issues-upgrade-advisor"></a><span data-ttu-id="bc27d-102">Reporting Services 升級問題 (Upgrade Advisor)</span><span class="sxs-lookup"><span data-stu-id="bc27d-102">Reporting Services Upgrade Issues (Upgrade Advisor)</span></span>
  <span data-ttu-id="bc27d-103">下列主題將描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 可能會影響升級至的問題 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bc27d-103">The following topics describe the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] issues that might affect your upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="bc27d-104">這些主題會描述一些可讓您採取的動作，以便減輕這些變更對環境的影響。</span><span class="sxs-lookup"><span data-stu-id="bc27d-104">The topics describe actions that you can take to mitigate the effect of these changes on your environment.</span></span>  
  
 <span data-ttu-id="bc27d-105">Upgrade Advisor 會分析報表伺服器安裝。</span><span class="sxs-lookup"><span data-stu-id="bc27d-105">Upgrade Advisor analyzes a report server installation.</span></span> <span data-ttu-id="bc27d-106">如果只安裝用戶端元件 (例如，如果「報表設計師」是安裝在電腦上的唯一 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 元件)，則不會報告任何問題。</span><span class="sxs-lookup"><span data-stu-id="bc27d-106">If only client components are installed (for example, if Report Designer is the only [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] component installed on the computer), no issues will be reported.</span></span>  
  
 <span data-ttu-id="bc27d-107">根據設定安裝的方式而定，您可能會遇到 Upgrade Advisor 未報告的其他問題。</span><span class="sxs-lookup"><span data-stu-id="bc27d-107">Depending on how you configured your installation, you may encounter additional issues that are not reported by Upgrade Advisor.</span></span> <span data-ttu-id="bc27d-108">雖然這些問題不會導致 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 升級失敗，但它們可能會影響報表和應用程式在升級完成後的執行方式。</span><span class="sxs-lookup"><span data-stu-id="bc27d-108">These issues do not prevent a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] upgrade from succeeding, but they may affect how reports and applications run after an upgrade is finished.</span></span> <span data-ttu-id="bc27d-109">若要進一步了解這些問題，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜Reporting Services 回溯相容性＞。</span><span class="sxs-lookup"><span data-stu-id="bc27d-109">To learn about these issues, see "Reporting Services Backward Compatibility" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="bc27d-110">如果您無法使用安裝程式來升級 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝，可以安裝新的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行個體，然後將現有的安裝移轉至新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc27d-110">If you cannot use Setup to upgrade a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation, you can install a new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance and migrate your existing installation to the new instance.</span></span> <span data-ttu-id="bc27d-111">如需詳細資訊，請參閱《線上叢書》中的「升級和遷移 Reporting Services」 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ， [升級和遷移 Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="bc27d-111">For more information, see "Upgrade and Migrate Reporting Services" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online, [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).</span></span>  
  
 <span data-ttu-id="bc27d-112">下列主題將描述 Upgrade Advisor 所報告的已知問題，以及說明如何修改現有的安裝，以便允許進行升級。</span><span class="sxs-lookup"><span data-stu-id="bc27d-112">The following topics describe known issues that are reported by Upgrade Advisor, and explain how you can modify your existing installation to allow an upgrade to occur.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bc27d-113">Upgrade Advisor 必須安裝在報表伺服器上，才能分析 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc27d-113">Upgrade Advisor must be installed on the report server to analyze an instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="bc27d-114">不支援遠端分析。</span><span class="sxs-lookup"><span data-stu-id="bc27d-114">does not support remote analysis.</span></span>  
>   
>  <span data-ttu-id="bc27d-115">如需詳細資訊，請參閱 [安裝 Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="bc27d-115">For more information, see [Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bc27d-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="bc27d-116">In This Section</span></span>  
  
-   [<span data-ttu-id="bc27d-117">&#40;Upgrade Advisor 的報表伺服器網站上的用戶端憑證&#41;</span><span class="sxs-lookup"><span data-stu-id="bc27d-117">Client certificates on the report server web site &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/client-certificates-on-the-report-server-web-site-upgrade-advisor.md)  
  
-   [<span data-ttu-id="bc27d-118">在報表伺服器上偵測到自訂延伸模組 &#40;Upgrade Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="bc27d-118">Custom extensions were detected on the report server &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/custom-extensions-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [<span data-ttu-id="bc27d-119">在報表伺服器上偵測到自訂報表專案 &#40;Upgrade Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="bc27d-119">Custom report items were detected on the report server &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/custom-report-items-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [<span data-ttu-id="bc27d-120">&#40;Upgrade Advisor 未偵測到 IIS 回溯相容性元件&#41;</span><span class="sxs-lookup"><span data-stu-id="bc27d-120">IIS backward compatibility components were not detected &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/iis-backward-compatibility-components-were-not-detected-upgrade-advisor.md)  
  
-   [<span data-ttu-id="bc27d-121">偵測到 &#40;Upgrade Advisor&#41;的 IP 位址限制 </span><span class="sxs-lookup"><span data-stu-id="bc27d-121">IP address restriction detected &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/ip-address-restriction-detected-upgrade-advisor.md)  
  
-   [<span data-ttu-id="bc27d-122">在報表伺服器網站上偵測到 ISAPI 篩選器 &#40;Upgrade Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="bc27d-122">ISAPI filters detected on the report server site &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/isapi-filters-detected-on-the-report-server-site-upgrade-advisor.md)  
  
-   [<span data-ttu-id="bc27d-123">在報表伺服器電腦上偵測到過時的延伸模組 &#40;Upgrade Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="bc27d-123">Obsolete extensions were detected on the report server computer &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor.md)  
  
-   [<span data-ttu-id="bc27d-124">&#40;Upgrade Advisor&#41;未設定報表伺服器資料庫 </span><span class="sxs-lookup"><span data-stu-id="bc27d-124">Report server database is not configured &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/report-server-database-is-not-configured-upgrade-advisor.md)  
  
-   [<span data-ttu-id="bc27d-125">SQL Server 2005 &#40;Upgrade Advisor 偵測到的報表伺服器 Web 服務群組&#41;</span><span class="sxs-lookup"><span data-stu-id="bc27d-125">SQL Server 2005 Report Server Web Service group detected &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/sql-server-2005-report-server-web-service-group-detected-upgrade-advisor.md)  
  
-   [<span data-ttu-id="bc27d-126">&#40;Upgrade Advisor 未指定虛擬目錄&#41;</span><span class="sxs-lookup"><span data-stu-id="bc27d-126">Virtual directories are unspecified &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/virtual-directories-are-unspecified-upgrade-advisor.md)  
  
-   [<span data-ttu-id="bc27d-127">虛擬目錄具有不支援的驗證方法 &#40;Upgrade Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="bc27d-127">Virtual directory has unsupported authentication method &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/virtual-directory-has-unsupported-authentication-method-upgrade-advisor.md)  
  
-   [<span data-ttu-id="bc27d-128">SQL Server Standard 和 Enterprise &#40;Upgrade Advisor&#41;的 CPU 與記憶體限制的變更 </span><span class="sxs-lookup"><span data-stu-id="bc27d-128">Changes to CPU and memory limits for SQL Server Standard and Enterprise &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/cpu-memory-limits-changes-sql-server-standard-enterprise-upgrade-advisor.md)  
  
-   [<span data-ttu-id="bc27d-129">SharePoint 伺服器陣列所需的網域帳戶 &#40;Upgrade Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="bc27d-129">Domain accounts required for SharePoint farm &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/domain-accounts-required-for-sharepoint-farm-upgrade-advisor.md)  
  
-   [<span data-ttu-id="bc27d-130">直接流覽至報表伺服器 &#40;Upgrade Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="bc27d-130">Direct Browsing to Report Server &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/direct-browsing-to-report-server-upgrade-advisor.md)  
  
-   [<span data-ttu-id="bc27d-131">&#40;Upgrade Advisor 已安裝 Microsoft SharePoint 2007&#41;</span><span class="sxs-lookup"><span data-stu-id="bc27d-131">Microsoft SharePoint 2007 is Installed &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/microsoft-sharepoint-2007-is-installed-upgrade-advisor.md)  
  
-   [<span data-ttu-id="bc27d-132">Microsoft SQL Server Reporting Services SharePoint 共用服務會並存安裝 &#40;Upgrade Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="bc27d-132">Microsoft SQL Server Reporting Services SharePoint Shared Service is Installed Side by Side &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/sql-server-reporting-services-sharepoint-shared-service-side-by-side-upgrade-advisor.md)  
  
-   [<span data-ttu-id="bc27d-133">資料庫引擎伺服器定序不相容 &#40;Upgrade Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="bc27d-133">Incompatible Database Engine Server Collation &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/incompatible-database-engine-server-collation-upgrade-advisor.md)  
  
-   [<span data-ttu-id="bc27d-134">其他 Reporting Services 升級問題</span><span class="sxs-lookup"><span data-stu-id="bc27d-134">Other Reporting Services Upgrade Issues</span></span>](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md)  
  
  
