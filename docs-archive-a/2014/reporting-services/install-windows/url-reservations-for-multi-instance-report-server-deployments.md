---
title: 多重實例報表伺服器部署的 URL 保留專案 (SSRS Configuration Manager) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- URL reservations
ms.assetid: f67c83c0-1f74-42bb-bfc1-e50c38152d3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d2e51813ca2c85d089864dc5d2516e21ed975de4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585132"
---
# <a name="url-reservations-for-multi-instance-report-server-deployments--ssrs-configuration-manager"></a><span data-ttu-id="95b80-102">多重執行個體報表伺服器部署的 URL 保留項目 (SSRS 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="95b80-102">URL Reservations for Multi-Instance Report Server Deployments  (SSRS Configuration Manager)</span></span>
  <span data-ttu-id="95b80-103">如果您在相同電腦上安裝多個 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行個體，您就必須考慮要如何為每一個執行個體定義 URL 保留項目。</span><span class="sxs-lookup"><span data-stu-id="95b80-103">If you install multiple instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on the same computer, you must consider how you will define the URL reservations for each instance.</span></span> <span data-ttu-id="95b80-104">在每一個執行個體中，報表伺服器 Web 服務和報表管理員至少每一個都必須有一個 URL 保留項目。</span><span class="sxs-lookup"><span data-stu-id="95b80-104">Within each instance, the Report Server Web service and Report Manager must have at least one URL reservation each.</span></span> <span data-ttu-id="95b80-105">完整的保留項目集合在 HTTP.SYS 中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="95b80-105">The entire set of reservations must be unique in HTTP.SYS.</span></span>  
  
 <span data-ttu-id="95b80-106">在 URL 註冊期間偵測到重複的 URL，這是在此服務啟動時發生。</span><span class="sxs-lookup"><span data-stu-id="95b80-106">Duplicate URLs are detected during URL registration, which occurs when the service starts.</span></span> <span data-ttu-id="95b80-107">如果您建立非唯一的 URL 保留項目，則要等到您啟動此服務之後，才可偵測到名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="95b80-107">If you create URL reservations that are not unique, the name conflict might not be detected until you start the service.</span></span> <span data-ttu-id="95b80-108">因此，請務必遵循命名慣例或規則，以確保所有的值都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="95b80-108">For this reason, make sure that you follow naming conventions or rules to ensure all values are unique.</span></span>  
  
## <a name="default-naming-conventions"></a><span data-ttu-id="95b80-109">預設命名慣例</span><span class="sxs-lookup"><span data-stu-id="95b80-109">Default Naming Conventions</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="95b80-110">可安裝在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 具名執行個體內。</span><span class="sxs-lookup"><span data-stu-id="95b80-110">can be installed within a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] named instance.</span></span> <span data-ttu-id="95b80-111">當您在具名執行個體內安裝或設定報表伺服器時，執行個體名稱會自動包含在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 提供之預設 URL 保留項目的虛擬目錄中。</span><span class="sxs-lookup"><span data-stu-id="95b80-111">When you install or configure a report server within a named instance, the instance name is automatically included in the virtual directory in the default URL reservation that [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] provides.</span></span> <span data-ttu-id="95b80-112">下表將顯示預設執行個體和具名執行個體的 URL 保留項目。</span><span class="sxs-lookup"><span data-stu-id="95b80-112">The following table shows the URL reservations for a default instance and a named instance.</span></span>  
  
|<span data-ttu-id="95b80-113">SQL Server 執行個體</span><span class="sxs-lookup"><span data-stu-id="95b80-113">SQL Server Instance</span></span>|<span data-ttu-id="95b80-114">預設 URL 保留項目</span><span class="sxs-lookup"><span data-stu-id="95b80-114">Default URL Reservation</span></span>|  
|-------------------------|-----------------------------|  
|<span data-ttu-id="95b80-115">預設值 (MSSQLServer)</span><span class="sxs-lookup"><span data-stu-id="95b80-115">Default (MSSQLServer)</span></span>|http://+:80/reportserver|  
|<span data-ttu-id="95b80-116">已命名 (MynamedInstance)</span><span class="sxs-lookup"><span data-stu-id="95b80-116">Named (MynamedInstance)</span></span>|http://+:80/reportserver_MyNamedInstance|  
  
 <span data-ttu-id="95b80-117">如果是具名執行個體，虛擬目錄會包含此執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="95b80-117">For the named instance, the virtual directory includes the instance name.</span></span> <span data-ttu-id="95b80-118">預設執行個體和具名執行個體都會接聽相同的通訊埠，但是唯一的虛擬目錄名稱會決定哪一個報表伺服器取得要求。</span><span class="sxs-lookup"><span data-stu-id="95b80-118">Both the default instance and the named instance listen on the same port, but the unique virtual directory names determine which report server gets the request.</span></span>  
  
 <span data-ttu-id="95b80-119">最佳做法建議是使用虛擬目錄名稱來區分報表伺服器執行個體，</span><span class="sxs-lookup"><span data-stu-id="95b80-119">Best practice recommendations are to use the virtual directory name to distinguish among the report server instance.</span></span> <span data-ttu-id="95b80-120">這樣會清楚對應 URL 與目標執行個體，並確定應用程式名稱在整個系統中都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="95b80-120">It provides a clear correspondence between a URL and the target instance, and ensures that the application names are unique across the whole system.</span></span>  
  
## <a name="custom-naming-conventions"></a><span data-ttu-id="95b80-121">自訂命名慣例</span><span class="sxs-lookup"><span data-stu-id="95b80-121">Custom Naming Conventions</span></span>  
 <span data-ttu-id="95b80-122">雖然建議使用執行個體名稱，但是您可以使用 URL 語法和自己的命名慣例，以符合 URL 保留項目的唯一名稱條件約束。</span><span class="sxs-lookup"><span data-stu-id="95b80-122">Although using the instance name is recommended, you can use the URL syntax and your own naming conventions to meet the unique name constraints for URL reservations.</span></span> <span data-ttu-id="95b80-123">下列範例說明為每一個執行個體建立唯一 URL 的不同方式。</span><span class="sxs-lookup"><span data-stu-id="95b80-123">The following examples illustrate different approaches for creating unique URLs for each instance.</span></span>  
  
|<span data-ttu-id="95b80-124">報表伺服器預設執行個體 (MSSQLSERVER)</span><span class="sxs-lookup"><span data-stu-id="95b80-124">Report Server default instance (MSSQLSERVER)</span></span>|<span data-ttu-id="95b80-125">ReportServer_MyNamedInstance</span><span class="sxs-lookup"><span data-stu-id="95b80-125">ReportServer_MyNamedInstance</span></span>|<span data-ttu-id="95b80-126">唯一性</span><span class="sxs-lookup"><span data-stu-id="95b80-126">Uniqueness</span></span>|  
|----------------------------------------------------|-----------------------------------|----------------|  
|http://+:80/reportserver|http://+:8888/reportserver|<span data-ttu-id="95b80-127">每個執行個體會接聽不同的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="95b80-127">Each instance listens on a different port.</span></span>|  
|`http://www.contoso.com/reportserver`|`http://SRVR-46/reportserver`|<span data-ttu-id="95b80-128">每一個執行個體都會對應到不同的伺服器名稱 (完整網域名稱和電腦名稱)。</span><span class="sxs-lookup"><span data-stu-id="95b80-128">Each instance responds to different server names (fully qualified domain name, and machine name).</span></span>|  
  
## <a name="uniqueness-requirements"></a><span data-ttu-id="95b80-129">唯一性規定</span><span class="sxs-lookup"><span data-stu-id="95b80-129">Uniqueness Requirements</span></span>  
 <span data-ttu-id="95b80-130">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用的基礎技術對於唯一的名稱有一些規定。</span><span class="sxs-lookup"><span data-stu-id="95b80-130">The underlying technologies used by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] impose requirements around unique names.</span></span> <span data-ttu-id="95b80-131">HTTP.SYS 要求它的儲存機制內的所有 URL 都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="95b80-131">HTTP.SYS requires that all URLs within its repository be unique.</span></span> <span data-ttu-id="95b80-132">您可以讓通訊埠、主機名稱或虛擬目錄名稱不同，以建立唯一的 URL。</span><span class="sxs-lookup"><span data-stu-id="95b80-132">You can vary the port, host name, or virtual directory name to create a unique URL.</span></span> [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] <span data-ttu-id="95b80-133">要求相同處理序內的應用程式識別必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="95b80-133">requires that application identities be unique within the same process.</span></span> <span data-ttu-id="95b80-134">這項規定會影響虛擬目錄名稱，</span><span class="sxs-lookup"><span data-stu-id="95b80-134">This requirement affects the virtual directory names.</span></span> <span data-ttu-id="95b80-135">它指定您不能在相同的報表伺服器執行個體內重複虛擬目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="95b80-135">It specifies that you cannot duplicate a virtual directory name within the same report server instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95b80-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95b80-136">See Also</span></span>  
 <span data-ttu-id="95b80-137">[設定報表伺服器 URL &#40;SSRS 組態管理員&#41;](configure-report-server-urls-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="95b80-137">[Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="95b80-138">設定 URL &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="95b80-138">Configure a URL  &#40;SSRS Configuration Manager&#41;</span></span>](configure-a-url-ssrs-configuration-manager.md)  
  
  
