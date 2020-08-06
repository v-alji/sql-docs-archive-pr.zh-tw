---
title: 升級至不同版本的 SQL Server 2014 (安裝) |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 31d16820-d126-4c57-82cc-27701e4091bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ebb461118ace46000288ee800f30cf90726c465f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698521"
---
# <a name="upgrade-to-a-different-edition-of-sql-server-2014-setup"></a><span data-ttu-id="c78d5-102">升級為不同的 SQL Server 2014 版本 (安裝程式)</span><span class="sxs-lookup"><span data-stu-id="c78d5-102">Upgrade to a Different Edition of SQL Server 2014 (Setup)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c78d5-103">安裝程式支援各種不同 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本之間的版本升級。</span><span class="sxs-lookup"><span data-stu-id="c78d5-103">Setup supports edition upgrade among various editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="c78d5-104">如需支援版本升級方式的詳細資訊，請參閱 [支援的版本與版本升級](supported-version-and-edition-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="c78d5-104">For information about supported edition upgrade paths, see [Supported Version and Edition Upgrades](supported-version-and-edition-upgrades.md).</span></span> <span data-ttu-id="c78d5-105">在您起始 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]執行個體的版本升級之前，請檢閱以下主題：</span><span class="sxs-lookup"><span data-stu-id="c78d5-105">Before you initiate the edition upgrade of an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], review the following topics:</span></span>  
  
-   [<span data-ttu-id="c78d5-106">SQL Server 2014 各版本所支援的功能</span><span class="sxs-lookup"><span data-stu-id="c78d5-106">Features Supported by the Editions of SQL Server 2014</span></span>](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
-   [<span data-ttu-id="c78d5-107">SQL Server 2014 的版本和元件</span><span class="sxs-lookup"><span data-stu-id="c78d5-107">Editions and Components of SQL Server 2014</span></span>](../../sql-server/editions-and-components-of-sql-server-2016.md)  
  
-   [<span data-ttu-id="c78d5-108">SQL Server 版本的計算容量限制</span><span class="sxs-lookup"><span data-stu-id="c78d5-108">Compute Capacity Limits by Edition of SQL Server</span></span>](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)  
  
-   [<span data-ttu-id="c78d5-109">安裝 SQL Server 2014 的硬體與軟體需求</span><span class="sxs-lookup"><span data-stu-id="c78d5-109">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
> [!NOTE]  
>  <span data-ttu-id="c78d5-110">\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在叢集環境中：\*\* 在叢集的其中一個節點上執行版本升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 就已足夠。</span><span class="sxs-lookup"><span data-stu-id="c78d5-110">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a clustered environment:** Running edition upgrade on one of the nodes of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cluster is sufficient.</span></span> <span data-ttu-id="c78d5-111">這個節點可以是主動或被動節點，而且引擎不會在版本升級期間讓資源離線。</span><span class="sxs-lookup"><span data-stu-id="c78d5-111">This node can be either active or passive, and the engine does not bring the resources offline during the Edition Upgrade.</span></span> <span data-ttu-id="c78d5-112">版本升級之後，您必須重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體或容錯移轉至不同的節點。</span><span class="sxs-lookup"><span data-stu-id="c78d5-112">After the edition upgrade it is required to either restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance or failover to a different node.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c78d5-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="c78d5-113">Prerequisites</span></span>  
 <span data-ttu-id="c78d5-114">如果是本機安裝，您必須以管理員身分執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="c78d5-114">For local installations, you must run Setup as an administrator.</span></span> <span data-ttu-id="c78d5-115">如果您是從遠端共用位置安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，則必須使用對遠端共用位置具有讀取權限的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="c78d5-115">If you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a remote share, you must use a domain account that has read permissions on the remote share.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c78d5-116">若要啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本變更，您必須重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="c78d5-116">For the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] edition change to be activated, you must restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.</span></span> <span data-ttu-id="c78d5-117">這樣會導致應用程式關閉，同時服務會離線。</span><span class="sxs-lookup"><span data-stu-id="c78d5-117">This will result in application down time while services are offline.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="c78d5-118">程序</span><span class="sxs-lookup"><span data-stu-id="c78d5-118">Procedure</span></span>  
  
#### <a name="to-upgrade-to-a-different-edition-of-sscurrent"></a><span data-ttu-id="c78d5-119">若要升級至不同的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本</span><span class="sxs-lookup"><span data-stu-id="c78d5-119">To upgrade to a different edition of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]</span></span>  
  
1.  <span data-ttu-id="c78d5-120">插入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝媒體。</span><span class="sxs-lookup"><span data-stu-id="c78d5-120">Insert the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation media.</span></span> <span data-ttu-id="c78d5-121">在根資料夾中按兩下 setup.exe，或從 [組態工具] 啟動 [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝中心]。</span><span class="sxs-lookup"><span data-stu-id="c78d5-121">From the root folder, double-click setup.exe or launch the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Center from Configuration Tools.</span></span> <span data-ttu-id="c78d5-122">若要從網路共用進行安裝，請找出共用上的根資料夾，然後按兩下 Setup.exe。</span><span class="sxs-lookup"><span data-stu-id="c78d5-122">To install from a network share, locate the root folder on the share, and then double-click Setup.exe.</span></span>  
  
2.  <span data-ttu-id="c78d5-123">若要將現有的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 執行個體升級至不同的版本，請在 [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝中心] 中，按一下 **[維護]** ，然後選取 **[版本升級]** 。</span><span class="sxs-lookup"><span data-stu-id="c78d5-123">To upgrade an existing instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to a different edition, from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Center click **Maintenance**, and then select **Edition Upgrade**.</span></span>  
  
3.  <span data-ttu-id="c78d5-124">如果需要安裝程式支援檔案， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式就會安裝這些檔案。</span><span class="sxs-lookup"><span data-stu-id="c78d5-124">If Setup support files are required, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup installs them.</span></span> <span data-ttu-id="c78d5-125">如果系統指示您重新啟動電腦，請先重新啟動，然後再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="c78d5-125">If you are instructed to restart your computer, restart before you continue.</span></span>  
  
4.  <span data-ttu-id="c78d5-126">系統組態檢查會在電腦上執行探索作業。</span><span class="sxs-lookup"><span data-stu-id="c78d5-126">The System Configuration Checker runs a discovery operation on your computer.</span></span> <span data-ttu-id="c78d5-127">若要繼續進行，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="c78d5-127">To continue, click **OK**.</span></span>  
  
5.  <span data-ttu-id="c78d5-128">在 [產品金鑰] 頁面上，選取選項按鈕，指出您要升級至免費的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本，還是您擁有產品之實際執行版本的 PID 金鑰。</span><span class="sxs-lookup"><span data-stu-id="c78d5-128">On the Product Key page, select a radio button to indicate whether you are upgrading to a free edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or whether you have a PID key for a production version of the product.</span></span> <span data-ttu-id="c78d5-129">如需詳細資訊，請參閱[SQL Server 2014 的版本和元件](../../sql-server/editions-and-components-of-sql-server-2016.md)和[支援的版本與版本升級](supported-version-and-edition-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="c78d5-129">For more information, see [Editions and Components of SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) and [Supported Version and Edition Upgrades](supported-version-and-edition-upgrades.md).</span></span>  
  
6.  <span data-ttu-id="c78d5-130">在 [授權條款] 頁面上，閱讀授權合約，然後選取要接受授權條款和條件的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c78d5-130">On the License Terms page, read the license agreement, and then select the check box to accept the licensing terms and conditions.</span></span> <span data-ttu-id="c78d5-131">若要繼續進行，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="c78d5-131">To continue, click **Next**.</span></span> <span data-ttu-id="c78d5-132">若要結束安裝程式，請按一下 **[取消]** 。</span><span class="sxs-lookup"><span data-stu-id="c78d5-132">To end Setup, click **Cancel**.</span></span>  
  
7.  <span data-ttu-id="c78d5-133">在 [選取執行個體] 頁面中，指定要升級的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="c78d5-133">On the Select Instance page, specify the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to upgrade.</span></span>  
  
8.  <span data-ttu-id="c78d5-134">[版本升級規則] 頁面會驗證您的電腦組態，然後版本升級作業才會開始。</span><span class="sxs-lookup"><span data-stu-id="c78d5-134">The Edition Upgrade Rules page validates your computer configuration before the edition upgrade operation begins.</span></span>  
  
9. <span data-ttu-id="c78d5-135">[已完成升級版本的準備工作] 頁面會顯示在安裝期間指定之安裝選項的樹狀檢視。</span><span class="sxs-lookup"><span data-stu-id="c78d5-135">The Ready to Upgrade Edition page shows a tree view of installation options that were specified during Setup.</span></span> <span data-ttu-id="c78d5-136">若要繼續，請按一下 **[升級]** 。</span><span class="sxs-lookup"><span data-stu-id="c78d5-136">To continue, click **Upgrade**.</span></span>  
  
10. <span data-ttu-id="c78d5-137">在版本升級程序期間，您必須重新啟動這些服務，才能挑選新的設定。</span><span class="sxs-lookup"><span data-stu-id="c78d5-137">During the edition upgrade process, the services need to be restarted to pick up the new setting.</span></span> <span data-ttu-id="c78d5-138">版本升級之後，[完成] 頁面會提供版本升級之摘要記錄檔的連結。</span><span class="sxs-lookup"><span data-stu-id="c78d5-138">After edition upgrade, the Complete page provides a link to the summary log file for the edition upgrade.</span></span> <span data-ttu-id="c78d5-139">若要關閉精靈，請按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="c78d5-139">To close the wizard, click **Close**.</span></span>  
  
11. <span data-ttu-id="c78d5-140">[完成] 頁面會提供安裝和其他重要注意事項之摘要記錄檔的連結。</span><span class="sxs-lookup"><span data-stu-id="c78d5-140">The Complete page provides a link to the summary log file for the installation and other important notes.</span></span>  
  
12. <span data-ttu-id="c78d5-141">如果指示您重新啟動電腦，請立刻執行。</span><span class="sxs-lookup"><span data-stu-id="c78d5-141">If you are instructed to restart the computer, do so now.</span></span> <span data-ttu-id="c78d5-142">當您完成安裝時，請務必閱讀安裝精靈所提供的訊息。</span><span class="sxs-lookup"><span data-stu-id="c78d5-142">It is important to read the message from the Installation Wizard when you are done with Setup.</span></span> <span data-ttu-id="c78d5-143">如需安裝程式記錄檔的資訊，請參閱 [檢視與讀取 SQL Server 安裝程式記錄檔](view-and-read-sql-server-setup-log-files.md)。</span><span class="sxs-lookup"><span data-stu-id="c78d5-143">For information about Setup log files, see [View and Read SQL Server Setup Log Files](view-and-read-sql-server-setup-log-files.md).</span></span>  
  
13. <span data-ttu-id="c78d5-144">如果您是從 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]升級，就必須執行一些額外的步驟，然後才能使用升級的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體：</span><span class="sxs-lookup"><span data-stu-id="c78d5-144">If you upgraded from [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], you must perform additional steps before you can use your upgraded instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
    -   <span data-ttu-id="c78d5-145">在 Windows SCM 中啟用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="c78d5-145">Enable the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service in Windows SCM.</span></span>  
  
    -   <span data-ttu-id="c78d5-146">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員來提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="c78d5-146">Provision the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
 <span data-ttu-id="c78d5-147">除了上述步驟以外，如果您是從 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]升級，可能必須進行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c78d5-147">In addition to the steps above, you may need to do the following if you upgraded from [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]:</span></span>  
  
-   <span data-ttu-id="c78d5-148">在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 中提供的使用者會在升級之後維持已提供的狀態。</span><span class="sxs-lookup"><span data-stu-id="c78d5-148">Users that were provisioned in [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] remain provisioned after the upgrade.</span></span> <span data-ttu-id="c78d5-149">更明確地說，BUILTIN\Users 群組會維持已提供的狀態。</span><span class="sxs-lookup"><span data-stu-id="c78d5-149">Specifically, the BUILTIN\Users group remains provisioned.</span></span> <span data-ttu-id="c78d5-150">您可以視需要停用、移除或重新提供這些帳戶。</span><span class="sxs-lookup"><span data-stu-id="c78d5-150">Disable, remove, or reprovision these accounts as needed.</span></span> <span data-ttu-id="c78d5-151">如需詳細資訊，請參閱 [設定 Windows 服務帳戶與權限](../configure-windows/configure-windows-service-accounts-and-permissions.md)預覽版本升級問題的解答。</span><span class="sxs-lookup"><span data-stu-id="c78d5-151">For more information, see [Configure Windows Service Accounts and Permissions](../configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
-   <span data-ttu-id="c78d5-152">tempdb 和 model 系統資料庫的大小和復原模式在升級之後會維持不變。</span><span class="sxs-lookup"><span data-stu-id="c78d5-152">Sizes and recovery mode for the tempdb and model system databases remain unchanged after the upgrade.</span></span> <span data-ttu-id="c78d5-153">您可以視需要重新設定這些設定。</span><span class="sxs-lookup"><span data-stu-id="c78d5-153">Reconfigure these settings as needed.</span></span> <span data-ttu-id="c78d5-154">如需詳細資訊，請參閱[系統資料庫的備份與還原 &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c78d5-154">For more information, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md).</span></span>  
  
-   <span data-ttu-id="c78d5-155">範本資料庫在升級之後會保留在電腦上。</span><span class="sxs-lookup"><span data-stu-id="c78d5-155">Template databases remain on the computer after the upgrade.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c78d5-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c78d5-156">See Also</span></span>  
 <span data-ttu-id="c78d5-157">[升級至 SQL Server 2014](upgrade-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c78d5-157">[Upgrade to SQL Server 2014](upgrade-sql-server.md) </span></span>  
 [<span data-ttu-id="c78d5-158">回溯相容性</span><span class="sxs-lookup"><span data-stu-id="c78d5-158">Backward Compatibility</span></span>](../../getting-started/backward-compatibility.md)  
  
  
