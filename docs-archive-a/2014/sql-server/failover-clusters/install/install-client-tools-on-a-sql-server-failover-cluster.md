---
title: 在 SQL Server 容錯移轉叢集上安裝用戶端工具 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 3c82d510-9798-46be-bebb-cac9bef56936
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b9cd0b426c01ebdb6f61d164302963ac3c7ff8aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595594"
---
# <a name="install-client-tools-on-a-sql-server-failover-cluster"></a><span data-ttu-id="c359c-102">在 SQL Server 容錯移轉叢集上安裝用戶端工具</span><span class="sxs-lookup"><span data-stu-id="c359c-102">Install Client Tools on a SQL Server Failover Cluster</span></span>
  <span data-ttu-id="c359c-103">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 之類的用戶端工具是在相同機器上所有執行個體通用的共用功能。</span><span class="sxs-lookup"><span data-stu-id="c359c-103">Client tools such as [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] are shared features common across all instances on the same machine.</span></span> <span data-ttu-id="c359c-104">這些功能與可以並排安裝的支援 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本回溯相容。</span><span class="sxs-lookup"><span data-stu-id="c359c-104">They are backward compatible, with supported [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] versions that can be installed side by side.</span></span> <span data-ttu-id="c359c-105">在一個節點上一次只能存在一個版本的用戶端工具。</span><span class="sxs-lookup"><span data-stu-id="c359c-105">Only one version of the client tool exists on a node at a time.</span></span>  
  
 <span data-ttu-id="c359c-106">如果在安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 叢集的第一個節點期間安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用戶端工具，則會使用 [加入節點]，將這些用戶端工具自動加入至稍後可能會加入至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的所有節點。</span><span class="sxs-lookup"><span data-stu-id="c359c-106">If the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client tools are installed during setup on first node of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cluster, they are automatically added to any nodes that may be added later to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] using Add Node.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="c359c-107">線上叢書》自動加入至要加入至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 叢集的其他節點。</span><span class="sxs-lookup"><span data-stu-id="c359c-107">Books Online is not automatically added to the additional nodes added to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cluster using Add Node.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="c359c-108">線上叢書》手動安裝在您想要擁有《 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 線上叢書》本機副本的節點上。</span><span class="sxs-lookup"><span data-stu-id="c359c-108">Books Online can be installed manually on the nodes that you wish to have a local copy of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="c359c-109">如果您沒有在一開始安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 叢集期間安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用戶端工具，您可以稍後再進行安裝，如以下程序所述。</span><span class="sxs-lookup"><span data-stu-id="c359c-109">If you do not install the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client tools during the initial installation of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cluster, you can install it later as described in the procedures below.</span></span>  
  
## <a name="installation-procedures"></a><span data-ttu-id="c359c-110">安裝程序</span><span class="sxs-lookup"><span data-stu-id="c359c-110">Installation procedures</span></span>  
  
#### <a name="installing-ssnoversion-client-tools-using-the-setup-user-interface"></a><span data-ttu-id="c359c-111">使用安裝程式使用者介面安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用戶端工具</span><span class="sxs-lookup"><span data-stu-id="c359c-111">Installing [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client Tools Using the Setup User Interface</span></span>  
  
1.  <span data-ttu-id="c359c-112">插入 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝媒體。</span><span class="sxs-lookup"><span data-stu-id="c359c-112">Insert the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation media.</span></span> <span data-ttu-id="c359c-113">在根安裝資料夾中，按兩下 Setup.exe。</span><span class="sxs-lookup"><span data-stu-id="c359c-113">From the root installation folder, double click Setup.exe.</span></span> <span data-ttu-id="c359c-114">若要從網路共用進行安裝，請找出共用上的根資料夾，然後按兩下 Setup.exe。</span><span class="sxs-lookup"><span data-stu-id="c359c-114">To install from the network share, locate the root folder on the share, and then double-click Setup.exe.</span></span>  
  
2.  <span data-ttu-id="c359c-115">在 [安裝]  頁面上，按一下 [新的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 獨立安裝或將功能加入到現有安裝]  。</span><span class="sxs-lookup"><span data-stu-id="c359c-115">On the **Installation** page, click **New [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stand-alone installation or add Features to an existing installation**.</span></span> <span data-ttu-id="c359c-116">請不要按 [新的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集安裝]  。</span><span class="sxs-lookup"><span data-stu-id="c359c-116">Do not click **New [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster installation**.</span></span>  
  
3.  <span data-ttu-id="c359c-117">系統組態檢查將會先確認電腦的系統狀態，然後安裝程式才會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="c359c-117">The system configuration checker verifies the system state of your computer before Setup will continue.</span></span>  
  
4.  <span data-ttu-id="c359c-118">在 [安裝類型]  頁面上，按一下 [執行 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 的新安裝]  。</span><span class="sxs-lookup"><span data-stu-id="c359c-118">On the **Installation Type** page, click **Perform a new installation of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]**.</span></span>  
  
5.  <span data-ttu-id="c359c-119">在 **[特徵選取]** 頁面上，選取您要安裝的工具，然後遵循安裝程序的其餘步驟進行。</span><span class="sxs-lookup"><span data-stu-id="c359c-119">On the **Feature Selection** page, select the tools that you want to install and follow through the rest of the steps of the Setup process.</span></span>  
  
#### <a name="installing-ssnoversion-client-tools-at-the-command-prompt"></a><span data-ttu-id="c359c-120">在命令提示字元安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用戶端工具</span><span class="sxs-lookup"><span data-stu-id="c359c-120">Installing [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client tools at the command prompt</span></span>  
  
1.  <span data-ttu-id="c359c-121">若要安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用戶端工具與《[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 線上叢書》，請執行下列命令：Setup.exe/q/Action=Install /Features=Tools</span><span class="sxs-lookup"><span data-stu-id="c359c-121">To install [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client tools and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online, run the following command: Setup.exe/q/Action=Install /Features=Tools</span></span>  
  
2.  <span data-ttu-id="c359c-122">如果只要安裝基本 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理工具，請執行下列命令：Setup.exe/q/Action=Install Features=SSMS。</span><span class="sxs-lookup"><span data-stu-id="c359c-122">To install only the basic [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management tools run the following command: Setup.exe/q/Action=Install Features=SSMS.</span></span> <span data-ttu-id="c359c-123">這會針對 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 、 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]、sqlcmd 公用程式，以及 [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)]Powershell 提供者，安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 支援。</span><span class="sxs-lookup"><span data-stu-id="c359c-123">This will install [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] support for [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)], [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)], sqlcmd utility, and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Powershell provider.</span></span>  
  
3.  <span data-ttu-id="c359c-124">如果要安裝完整的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理工具，請執行下列命令：Setup.exe/q/Action=Install /Features=ADV_SSMS。</span><span class="sxs-lookup"><span data-stu-id="c359c-124">To install the complete [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management tools, run the following command: Setup.exe/q/Action=Install /Features=ADV_SSMS.</span></span> <span data-ttu-id="c359c-125">如需功能參數值的詳細資訊，請參閱[從命令提示字元安裝 SQL Server 2014](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="c359c-125">For more information about parameter values for the features, see [Install SQL Server 2014 from the Command Prompt](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
### <a name="uninstalling-ssnoversion-client-tools"></a><span data-ttu-id="c359c-126">解除安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用戶端工具</span><span class="sxs-lookup"><span data-stu-id="c359c-126">Uninstalling [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client Tools</span></span>  
 <span data-ttu-id="c359c-127">這些用戶端工具在 [控制台] 的 [新增或移除程式] 中顯示為 **[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]** ，而且可以從該處移除。</span><span class="sxs-lookup"><span data-stu-id="c359c-127">They appear in Add or Remove programs in Control Panel as **[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]**, and can be removed from there.</span></span> <span data-ttu-id="c359c-128">當您使用 [移除節點] 從容錯移轉叢集解除安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體時，不會同時解除安裝用戶端元件。</span><span class="sxs-lookup"><span data-stu-id="c359c-128">When you use Remove Node to uninstall an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from the failover cluster, the client components are not uninstalled at the same time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c359c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c359c-129">See Also</span></span>  
 [<span data-ttu-id="c359c-130">檢視與讀取 SQL Server 安裝程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="c359c-130">View and Read SQL Server Setup Log Files</span></span>](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
