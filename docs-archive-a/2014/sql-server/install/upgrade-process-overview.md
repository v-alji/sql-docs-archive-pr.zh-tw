---
title: 升級程式總覽 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server
- Upgrade Advisor [SQL Server], process description
- SQL Server Upgrade Advisor, process description
- upgrade process [Upgrade Advisor]
ms.assetid: f77ffbab-a195-4124-acce-9c538f7ca9ce
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5da6dc3b3e6d6c7058193801100bf2552bfde7cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710134"
---
# <a name="upgrade-process-overview"></a><span data-ttu-id="1cbd6-102">升級程序概觀</span><span class="sxs-lookup"><span data-stu-id="1cbd6-102">Upgrade Process Overview</span></span>
  <span data-ttu-id="1cbd6-103">本主題會提供 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor 的最佳作法資訊，以及升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 之建議程序的摘要。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-103">This topic provides best practice information for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor and a summary of the recommended process for upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="upgrade-process"></a><span data-ttu-id="1cbd6-104">升級程序</span><span class="sxs-lookup"><span data-stu-id="1cbd6-104">Upgrade Process</span></span>  
 <span data-ttu-id="1cbd6-105">執行 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 的伺服器可以升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-105">Servers that are running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] can be upgraded to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="1cbd6-106">有些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件可以就地升級、有些元件必須移轉，而其他元件則已由新元件取代。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-106">Whereas some [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components can be upgraded in place, others must be migrated, and still others have been superseded by new components.</span></span> <span data-ttu-id="1cbd6-107">例如，從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 開始，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) 便取代了 Data Transformation Services (DTS)，而且 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 不再支援 DTS。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-107">For example, starting with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) supersedes Data Transformation Services (DTS), and DTS is no longer supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="1cbd6-108">當設計升級計畫時，您可能需要規劃將目前 DTS 封裝升級為 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-108">When you formulate your upgrade plan, you might need to plan for updating your current DTS packages to [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages.</span></span>  
  
 <span data-ttu-id="1cbd6-109">Upgrade Advisor 可讓您評估目前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝、元件和相關檔案，以便識別在升級或移轉至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 期間或之後將導致問題發生的已知問題。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-109">Upgrade Advisor enables you to evaluate current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations, components, and related files to identify known issues that will cause problems both during and after you upgrade or migrate to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="1cbd6-110">其中少數已知問題會封鎖 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 升級。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-110">A few of these known issues block the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] upgrade.</span></span> <span data-ttu-id="1cbd6-111">在 Upgrade Advisor 報表中，這些問題會識別為「升級封鎖程式」。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-111">In the Upgrade Advisor report, these issues are identified as Upgrade Blockers.</span></span> <span data-ttu-id="1cbd6-112">如果您在執行安裝程式之前沒有處理這些「升級封鎖程式」，[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝程式會結束，並建議您執行 Upgrade Advisor 來識別封鎖升級的特定問題。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-112">If you have not addressed the Upgrade Blockers before you run Setup, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup exits and recommends that you run Upgrade Advisor to identify the specific issues that are blocking the upgrade.</span></span>  
  
 <span data-ttu-id="1cbd6-113">建議的最佳作法是，在升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 之前，備份資料和系統設定，然後採取針對組織所定義之作業指導方針所述的策略性步驟。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-113">As a best practice before upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that you back up your data and system settings, and take strategic steps as outlined in the operational guidelines defined for your organization.</span></span> <span data-ttu-id="1cbd6-114">請使用下列步驟來完成升級：</span><span class="sxs-lookup"><span data-stu-id="1cbd6-114">Use the following steps to complete the upgrade:</span></span>  
  
1.  <span data-ttu-id="1cbd6-115">檢閱 [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-115">Review [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="1cbd6-116">備份資料和系統設定。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-116">Back up data and system settings.</span></span>  
  
3.  <span data-ttu-id="1cbd6-117">執行 Upgrade Advisor。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-117">Run Upgrade Advisor.</span></span>  
  
     <span data-ttu-id="1cbd6-118">Upgrade Advisor 不會修改資料或變更電腦的設定。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-118">Upgrade Advisor does not modify your data or change settings on your computer.</span></span>  
  
4.  <span data-ttu-id="1cbd6-119">檢閱 Upgrade Advisor 報表中識別的問題。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-119">Review the issues identified in the Upgrade Advisor report.</span></span>  
  
5.  <span data-ttu-id="1cbd6-120">解決讓您無法升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的任何封鎖問題。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-120">Resolve any blocking issues that would prevent you from upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
6.  <span data-ttu-id="1cbd6-121">解決任何其他升級前問題。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-121">Resolve any other pre-upgrade issues.</span></span>  
  
7.  <span data-ttu-id="1cbd6-122">執行 Upgrade Advisor 來確認所有已知問題都已經解決。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-122">Run Upgrade Advisor to verify that all known issues have been addressed.</span></span>  
  
8.  <span data-ttu-id="1cbd6-123">執行 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-123">Run [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup.</span></span>  
  
9. <span data-ttu-id="1cbd6-124">解決任何升級後和移轉問題。</span><span class="sxs-lookup"><span data-stu-id="1cbd6-124">Resolve any post-upgrade and migration issues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cbd6-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cbd6-125">See Also</span></span>  
 <span data-ttu-id="1cbd6-126">[正在執行 Upgrade Advisor &#40;使用者介面&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md) </span><span class="sxs-lookup"><span data-stu-id="1cbd6-126">[Running Upgrade Advisor &#40;User Interface&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md) </span></span>  
 <span data-ttu-id="1cbd6-127">[使用報表](../../../2014/sql-server/install/using-reports.md) </span><span class="sxs-lookup"><span data-stu-id="1cbd6-127">[Using Reports](../../../2014/sql-server/install/using-reports.md) </span></span>  
 [<span data-ttu-id="1cbd6-128">使用升級建議程式</span><span class="sxs-lookup"><span data-stu-id="1cbd6-128">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
