---
title: 修復 SQL Server 2014 安裝 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 90c11b28-892b-44d6-978e-0eee48c75b7d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f3e382137a971b3f8b23cf1d814bff9908f04150
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701542"
---
# <a name="drop-a-sql-server-2014-installation"></a><span data-ttu-id="b08dc-102">卸除 SQL Server 2014 安裝</span><span class="sxs-lookup"><span data-stu-id="b08dc-102">Drop a SQL Server 2014 Installation</span></span>
  <span data-ttu-id="b08dc-103">下列情況下可以使用修復作業：</span><span class="sxs-lookup"><span data-stu-id="b08dc-103">Repair operation can be used in the following scenarios:</span></span>  
  
-   <span data-ttu-id="b08dc-104">修復成功安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之後卻又損毀的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b08dc-104">Repair an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is corrupted after it was successfully installed.</span></span>  
  
-   <span data-ttu-id="b08dc-105">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱對應到新升級的執行個體之後，升級作業遭到取消或失敗，請修復這個執行個體。</span><span class="sxs-lookup"><span data-stu-id="b08dc-105">Repair an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if the upgrade operation is cancelled or fails after the instance name is mapped to the newly-upgraded instance.</span></span>  
  
    -   <span data-ttu-id="b08dc-106">如果您在摘要記錄檔中看到以下訊息，您可以修復失敗的升級執行個體：</span><span class="sxs-lookup"><span data-stu-id="b08dc-106">If you see the following message in the summary log, you can repair the failed upgrade instance:</span></span>  
  
         <span data-ttu-id="b08dc-107">「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升級失敗。</span><span class="sxs-lookup"><span data-stu-id="b08dc-107">"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] upgrade failed.</span></span> <span data-ttu-id="b08dc-108">若要繼續，請調查失敗的原因、更正問題，然後修復安裝。」</span><span class="sxs-lookup"><span data-stu-id="b08dc-108">To continue, investigate the reason for the failure, correct the problem, and then repair your installation."</span></span>  
  
    -   <span data-ttu-id="b08dc-109">如果您在摘要記錄檔中看到以下訊息，您需要解除安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]然後再重新安裝。</span><span class="sxs-lookup"><span data-stu-id="b08dc-109">If you see the following message in the summary log, you need to uninstall and reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b08dc-110">您無法修復 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b08dc-110">You cannot repair the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
         <span data-ttu-id="b08dc-111">「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升級失敗。</span><span class="sxs-lookup"><span data-stu-id="b08dc-111">"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] upgrade failed.</span></span> <span data-ttu-id="b08dc-112">若要繼續，請調查失敗的原因並更正問題。」</span><span class="sxs-lookup"><span data-stu-id="b08dc-112">To continue, investigate the reason for the failure, correct the problem."</span></span>  
  
 <span data-ttu-id="b08dc-113">當您修復 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體時：</span><span class="sxs-lookup"><span data-stu-id="b08dc-113">When you repair an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="b08dc-114">所有遺失或損毀的檔案都會被取代</span><span class="sxs-lookup"><span data-stu-id="b08dc-114">All missing or corrupt files are replaced.</span></span>  
  
-   <span data-ttu-id="b08dc-115">所有遺失或損毀的登錄機碼都會被取代</span><span class="sxs-lookup"><span data-stu-id="b08dc-115">All missing or corrupt registry keys are replaced.</span></span>  
  
-   <span data-ttu-id="b08dc-116">所有遺失或無效的組態值都會設為預設值。</span><span class="sxs-lookup"><span data-stu-id="b08dc-116">All missing or invalid configuration values are set to default values.</span></span>  
  
 <span data-ttu-id="b08dc-117">繼續進行之前，請針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集，檢閱下列重要資訊：</span><span class="sxs-lookup"><span data-stu-id="b08dc-117">Before you continue, for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover clusters, review the following important information:</span></span>  
  
-   <span data-ttu-id="b08dc-118">您必須在個別的叢集節點上執行修復。</span><span class="sxs-lookup"><span data-stu-id="b08dc-118">Repair must be run on individual cluster nodes.</span></span>  
  
-   <span data-ttu-id="b08dc-119">若要在失敗的「準備」作業之後修復容錯移轉叢集節點，請使用 [移除節點]  ，然後再次執行「準備」步驟。</span><span class="sxs-lookup"><span data-stu-id="b08dc-119">To repair a failover cluster node after a failed Prepare operation, use **Remove node** and then perform the Prepare step again.</span></span> <span data-ttu-id="b08dc-120">如需詳細資訊，請參閱[在 SQL Server 容錯移轉叢集中新增或移除節點 &#40;安裝程式&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="b08dc-120">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).</span></span>  
  
### <a name="to-repair-a-failed-installation-of-ssnoversion-from-the-installation-center"></a><span data-ttu-id="b08dc-121">若要從安裝中心修復失敗的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝</span><span class="sxs-lookup"><span data-stu-id="b08dc-121">To repair a failed installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the Installation Center</span></span>  
  
1.  <span data-ttu-id="b08dc-122">從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝媒體啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式 (setup.exe)。</span><span class="sxs-lookup"><span data-stu-id="b08dc-122">Launch the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup program (setup.exe) from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation media.</span></span>  
  
2.  <span data-ttu-id="b08dc-123">驗證必要元件和系統之後，安裝程式將會顯示 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝中心] 頁面。</span><span class="sxs-lookup"><span data-stu-id="b08dc-123">After prerequisites and system verification, the Setup program will display the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Center page.</span></span>  
  
3.  <span data-ttu-id="b08dc-124">按一下左側導覽區域中的 [維護]  ，然後按一下 [修復]  啟動修復作業。</span><span class="sxs-lookup"><span data-stu-id="b08dc-124">Click **Maintenance** in the left-hand navigation area, and then click **Repair** to start the repair operation.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="b08dc-125">如果使用 [開始] 功能表啟動安裝中心，您將需要在這個階段提供安裝媒體的位置。</span><span class="sxs-lookup"><span data-stu-id="b08dc-125">If the Installation Center was launched using the start menu, you will need to provide the location of the installation media at this time.</span></span>  
  
4.  <span data-ttu-id="b08dc-126">安裝程式支援規則和檔案常式將會執行，以便確保您的系統已安裝必要元件而且電腦通過安裝程式驗證規則。</span><span class="sxs-lookup"><span data-stu-id="b08dc-126">Setup support rule and file routines will run to ensure that your system has prerequisites installed and that the computer passes Setup validation rules.</span></span> <span data-ttu-id="b08dc-127">按一下 **[確定]** 或 **[安裝]** 繼續進行。</span><span class="sxs-lookup"><span data-stu-id="b08dc-127">Click **OK** or **Install** to continue.</span></span>  
  
5.  <span data-ttu-id="b08dc-128">在 [選取執行個體] 頁面上，選取要修復的執行個體，然後按一下 [下一步]  繼續進行。</span><span class="sxs-lookup"><span data-stu-id="b08dc-128">On the Select Instance page, select the instance to repair, and then click **Next** to continue.</span></span>  
  
6.  <span data-ttu-id="b08dc-129">修復規則將會執行，以便驗證作業。</span><span class="sxs-lookup"><span data-stu-id="b08dc-129">The repair rules will run to validate the operation.</span></span> <span data-ttu-id="b08dc-130">若要繼續進行，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="b08dc-130">To continue, click **Next**.</span></span>  
  
7.  <span data-ttu-id="b08dc-131">[已完成修復準備工作] 頁面會指出作業準備繼續進行。</span><span class="sxs-lookup"><span data-stu-id="b08dc-131">The Ready to Repair page indicates that the operation is ready to proceed.</span></span> <span data-ttu-id="b08dc-132">若要繼續，請按一下 [修復]  。</span><span class="sxs-lookup"><span data-stu-id="b08dc-132">To continue, click **Repair**.</span></span>  
  
8.  <span data-ttu-id="b08dc-133">[修復進度] 頁面會顯示修復作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="b08dc-133">The Repair Progress page shows the status of the repair operation.</span></span> <span data-ttu-id="b08dc-134">[完成] 頁面會指出作業已完成。</span><span class="sxs-lookup"><span data-stu-id="b08dc-134">The Complete page indicates that the operation is finished.</span></span>  
  
### <a name="to-repair-a-failed-installation-of-ssnoversion-using-command-prompt"></a><span data-ttu-id="b08dc-135">若要使用命令提示字元修復失敗的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝</span><span class="sxs-lookup"><span data-stu-id="b08dc-135">To repair a failed installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Command Prompt</span></span>  
  
1.  <span data-ttu-id="b08dc-136">在命令提示字元執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="b08dc-136">Run the following command at a command prompt:</span></span>  
  
    ```  
    Setup.exe /q /ACTION=Repair /INSTANCENAME=instancename  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b08dc-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b08dc-137">See Also</span></span>  
 <span data-ttu-id="b08dc-138">[檢視與讀取 SQL Server 安裝程式記錄檔](view-and-read-sql-server-setup-log-files.md) </span><span class="sxs-lookup"><span data-stu-id="b08dc-138">[View and Read SQL Server Setup Log Files](view-and-read-sql-server-setup-log-files.md) </span></span>  
 [<span data-ttu-id="b08dc-139">安裝的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="b08dc-139">Installation How-to Topics</span></span>](../../sql-server/install/installation-how-to-topics.md)  
  
  
