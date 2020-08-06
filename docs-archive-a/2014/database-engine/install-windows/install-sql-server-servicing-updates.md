---
title: 安裝 SQL Server 2014 服務更新 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 7d6c962b-c8d0-49f7-a2ac-00ad8dca930a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ace0fd187386d9a9d96e82f61d1efaa254f08c6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688157"
---
# <a name="install-sql-server-2014-servicing-updates"></a><span data-ttu-id="25c7b-102">安裝 SQL Server 2014 服務更新</span><span class="sxs-lookup"><span data-stu-id="25c7b-102">Install SQL Server 2014 Servicing Updates</span></span>
  <span data-ttu-id="25c7b-103">本主題提供有關安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]更新的資訊。</span><span class="sxs-lookup"><span data-stu-id="25c7b-103">This topic provides information about installing updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="25c7b-104">本節提供下列作業的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="25c7b-104">This section provides information about the following:</span></span>  
  
-   <span data-ttu-id="25c7b-105">在進行新安裝期間安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的更新。</span><span class="sxs-lookup"><span data-stu-id="25c7b-105">Installing updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] during a new installation</span></span>  
  
-   <span data-ttu-id="25c7b-106">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝完成之後安裝更新。</span><span class="sxs-lookup"><span data-stu-id="25c7b-106">Installing updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] after it has already been installed.</span></span>  
  
 <span data-ttu-id="25c7b-107">我們建議客戶及時評估並安裝最新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新，以便確保系統保持在最新狀態而且具有最新的安全性更新。</span><span class="sxs-lookup"><span data-stu-id="25c7b-107">We recommend that customers evaluate and install latest [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] updates in a timely manner to make sure that systems are up-to-date with the most recent security updates.</span></span>  
  
## <a name="installing-updates-for-sscurrent-during-a-new-installation"></a><span data-ttu-id="25c7b-108">在進行新安裝期間安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的更新。</span><span class="sxs-lookup"><span data-stu-id="25c7b-108">Installing Updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] During a New Installation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="25c7b-109">安裝程式會整合最新產品更新與主要產品安裝，因此主要產品及其適用的更新可同時安裝。</span><span class="sxs-lookup"><span data-stu-id="25c7b-109">setup integrates the latest product updates with the main product installation so that the main product and its applicable updates are installed at the same time.</span></span> <span data-ttu-id="25c7b-110">產品更新可以從下列位置搜尋適用的更新：</span><span class="sxs-lookup"><span data-stu-id="25c7b-110">Product Update can search for the applicable updates from:</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="25c7b-111">Update</span><span class="sxs-lookup"><span data-stu-id="25c7b-111">Update</span></span>  
  
-   <span data-ttu-id="25c7b-112">Windows Server Update Services (WSUS)</span><span class="sxs-lookup"><span data-stu-id="25c7b-112">Windows Server Update Services (WSUS)</span></span>  
  
-   <span data-ttu-id="25c7b-113">本機資料夾</span><span class="sxs-lookup"><span data-stu-id="25c7b-113">A local folder</span></span>  
  
-   <span data-ttu-id="25c7b-114">網路共用</span><span class="sxs-lookup"><span data-stu-id="25c7b-114">A network share</span></span>  
  
 <span data-ttu-id="25c7b-115">安裝程式找到最新版本的可用更新後，會使用目前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程序進行下載與整合。</span><span class="sxs-lookup"><span data-stu-id="25c7b-115">After Setup finds the latest versions of the applicable updates, it downloads and integrates them with the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup process.</span></span> <span data-ttu-id="25c7b-116">產品更新可能包括累計更新、Service Pack，或 Service Pack 加上累計更新。</span><span class="sxs-lookup"><span data-stu-id="25c7b-116">Product Update can include a cumulative update, service pack, or service pack plus cumulative update.</span></span> <span data-ttu-id="25c7b-117">產品更新功能是 PCU1 中提供之彙集[功能](https://go.microsoft.com/fwlink/?LinkId=219945)的延伸模組 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="25c7b-117">Product Update functionality is an extension of the [Slipstream Functionality](https://go.microsoft.com/fwlink/?LinkId=219945) that was available in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] PCU1.</span></span>  
  
## <a name="installing-updates-for-sscurrent-after-it-has-already-been-installed"></a><span data-ttu-id="25c7b-118">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝完成之後安裝更新</span><span class="sxs-lookup"><span data-stu-id="25c7b-118">Installing Updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] after it has already been installed</span></span>  
 <span data-ttu-id="25c7b-119">在已安裝的實例上 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，建議您套用所有可用的更新：一般發佈版本 (GDR-安全性/重大更新) 、Service pack (SP) ，以及最新可用的累計更新 (CU) 。</span><span class="sxs-lookup"><span data-stu-id="25c7b-119">On an installed instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that you apply all available updates: General Distribution Releases (GDR - security/critical updates), Service Packs (SP), as well as the latest available Cumulative Update (CU).</span></span>  
  
 <span data-ttu-id="25c7b-120">根據服務版本的類型，SQL Server 可透過 Microsoft Update (MU) 、Microsoft 下載中心和（或）客戶支援服務的修補伺服器取得更新。</span><span class="sxs-lookup"><span data-stu-id="25c7b-120">Depending on the type of servicing release, SQL Server updates are available via Microsoft Update (MU), the Microsoft Download Center, and/or the Customer Support Services hotfix Server.</span></span> <span data-ttu-id="25c7b-121">SQL Server 的安全性和重大更新是由 Microsoft Update (自動提供，若要查看這些更新，您必須透過 [控制台]) 中的 Windows Update 加入宣告 MU。</span><span class="sxs-lookup"><span data-stu-id="25c7b-121">Security and Critical updates for SQL Server are automatically provided by Microsoft Update (to be able to see these updates you need to opt-in to MU through Windows Update in Control panel).</span></span> <span data-ttu-id="25c7b-122">在 MU 上提供 Service Pack 做為選擇性/重要下載，以及下載中心。</span><span class="sxs-lookup"><span data-stu-id="25c7b-122">Service Packs are available on MU as Optional/Important downloads as well as the Download Center.</span></span> <span data-ttu-id="25c7b-123">在 CU 知識庫文章中提供的 Microsoft 修復程式下載伺服器上提供累計更新。</span><span class="sxs-lookup"><span data-stu-id="25c7b-123">Cumulative updates are available on the Microsoft hotfix download server provided in CU Knowledge Base articles.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25c7b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25c7b-124">See Also</span></span>  
 <span data-ttu-id="25c7b-125">[從安裝精靈安裝 SQL Server 2014 &#40;安裝程式&#41;](install-sql-server-from-the-installation-wizard-setup.md) </span><span class="sxs-lookup"><span data-stu-id="25c7b-125">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](install-sql-server-from-the-installation-wizard-setup.md) </span></span>  
 <span data-ttu-id="25c7b-126">[從命令提示字元安裝更新](installing-updates-from-the-command-prompt.md)[將功能新增至 SQL Server 2014 &#40;安裝程式的實例&#41;](add-features-to-an-instance-of-sql-server-setup.md) </span><span class="sxs-lookup"><span data-stu-id="25c7b-126">[Installing updates from the command prompt](installing-updates-from-the-command-prompt.md) [Add Features to an Instance of SQL Server 2014 &#40;Setup&#41;](add-features-to-an-instance-of-sql-server-setup.md) </span></span>  
 [<span data-ttu-id="25c7b-127">卸除 SQL Server 2014 安裝</span><span class="sxs-lookup"><span data-stu-id="25c7b-127">Drop a SQL Server 2014 Installation</span></span>](repair-a-failed-sql-server-installation.md)  
  
  
