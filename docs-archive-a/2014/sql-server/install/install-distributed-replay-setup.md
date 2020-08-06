---
title: 安裝 Distributed Replay (安裝程式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 64479cdc-661a-4e32-a381-8f8b5a238337
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 029737874fdab53669aab3be25b139d98d2907df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708093"
---
# <a name="install-distributed-replay-setup"></a><span data-ttu-id="63b67-102">安裝 Distributed Replay (安裝程式)</span><span class="sxs-lookup"><span data-stu-id="63b67-102">Install Distributed Replay (Setup)</span></span>
  <span data-ttu-id="63b67-103">您可以使用 [ [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝精靈] 安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Distributed Replay 功能。</span><span class="sxs-lookup"><span data-stu-id="63b67-103">Install the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay features with the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Installation Wizard.</span></span> <span data-ttu-id="63b67-104">規劃要安裝這些功能的位置時，請考慮下列事項：</span><span class="sxs-lookup"><span data-stu-id="63b67-104">When planning where to install the features, consider the following:</span></span>  
  
-   <span data-ttu-id="63b67-105">您可以選擇將管理工具與 Distributed Replay Controller 安裝在同一部電腦上，也可以選擇安裝在不同的電腦上。</span><span class="sxs-lookup"><span data-stu-id="63b67-105">You can install the administration tool on the same computer as the Distributed Replay controller, or on different computers.</span></span>  
  
-   <span data-ttu-id="63b67-106">每個 Distributed Replay 環境只可有一個控制器。</span><span class="sxs-lookup"><span data-stu-id="63b67-106">There can only be one controller in each Distributed Replay environment.</span></span>  
  
-   <span data-ttu-id="63b67-107">您最多可以在 16 部 (實體或虛擬) 電腦上安裝 Client 服務。</span><span class="sxs-lookup"><span data-stu-id="63b67-107">You can install the client service on up to 16 (physical or virtual) computers.</span></span>  
  
-   <span data-ttu-id="63b67-108">Distributed Replay Controller 電腦上只可安裝一個用戶端服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="63b67-108">Only one instance of the client service can be installed on the Distributed Replay controller computer.</span></span> <span data-ttu-id="63b67-109">您的 Distributed Replay 環境中如有多個用戶端，即不建議您將用戶端服務與控制器安裝在同一部電腦上。</span><span class="sxs-lookup"><span data-stu-id="63b67-109">If your Distributed Replay environment will have more than one client, we do not recommend installing the client service on the same computer as the controller.</span></span> <span data-ttu-id="63b67-110">這樣做可能會降低 Distributed Replay 的整體速度。</span><span class="sxs-lookup"><span data-stu-id="63b67-110">Doing so may decrease the overall speed of the distributed replay.</span></span>  
  
-   <span data-ttu-id="63b67-111">在效能測試案例中，我們不建議您在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的目標執行個體上安裝管理工具、Distributed Replay Controller 服務或 Client 服務。</span><span class="sxs-lookup"><span data-stu-id="63b67-111">For performance testing scenarios, we do not recommend installing the administration tool, Distributed Replay controller service, or client service on the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="63b67-112">在目標伺服器上安裝這些所有功能應限於應用程式相容性的功能測試。</span><span class="sxs-lookup"><span data-stu-id="63b67-112">Installing all of these features on the target server should be limited to functional testing for application compatibility.</span></span>  
  
-   <span data-ttu-id="63b67-113">安裝之後，必須先執行控制器服務 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller)，然後再啟動用戶端上的 Distributed Replay Client 服務。</span><span class="sxs-lookup"><span data-stu-id="63b67-113">After installation, the controller service, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay controller, must be running before you start the Distributed Replay client service on the clients.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63b67-114">如果要移除或變更 Distributed Replay 功能，請使用 Windows [控制台]  中的 [程式和功能]  視窗。</span><span class="sxs-lookup"><span data-stu-id="63b67-114">To remove or change the Distributed Replay features, use the Windows **Programs and Features** window in **Control Panel**.</span></span> <span data-ttu-id="63b67-115">在 [解除安裝或變更程式]  視窗中，選取 [[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]]，然後按一下 [移除]  開啟 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝精靈。</span><span class="sxs-lookup"><span data-stu-id="63b67-115">Select [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in the **Uninstall or change a program** window, and then click **Remove** to open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Installation Wizard.</span></span> <span data-ttu-id="63b67-116">在 [選取功能]  頁面上，核取您想要移除的 Distributed Replay 功能。</span><span class="sxs-lookup"><span data-stu-id="63b67-116">On the **Select Features** page, check the Distributed Replay features you want to remove.</span></span>  
  
 <span data-ttu-id="63b67-117">**必要條件：**</span><span class="sxs-lookup"><span data-stu-id="63b67-117">**Prerequisites:**</span></span>  
  
-   <span data-ttu-id="63b67-118">請確定您想要使用的電腦符合 [Distributed Replay 需求](../../tools/sql-server-profiler/replay-requirements.md)主題中所描述的需求。</span><span class="sxs-lookup"><span data-stu-id="63b67-118">Make sure that the computers that you want to use meet the requirements that are described in the topic [Distributed Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md).</span></span>  
  
-   <span data-ttu-id="63b67-119">開始進行此程序之前，請建立將用來執行 Controller 和 Client 服務的網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="63b67-119">Before you begin this procedure, you create the domain user accounts that the controller and client services will run under.</span></span> <span data-ttu-id="63b67-120">建議您不要將這些帳戶設定為 Windows Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="63b67-120">We recommend that these accounts are not members of the Windows Administrators group.</span></span> <span data-ttu-id="63b67-121">如需詳細資訊，請參閱 [Distributed Replay 安全性](../../tools/distributed-replay/distributed-replay-security.md) 主題中的＜使用者和服務帳戶＞一節。</span><span class="sxs-lookup"><span data-stu-id="63b67-121">For more information, see the User and Service Accounts section in the [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md) topic.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63b67-122">如果您要在同一部電腦上執行管理工具、Controller 服務和 Client 服務，可以使用本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="63b67-122">You can use local user accounts if you are running the administration tool, controller service, and client service on the same computer.</span></span>  
  
 <span data-ttu-id="63b67-123">**安裝位置：**</span><span class="sxs-lookup"><span data-stu-id="63b67-123">**Installation Locations:**</span></span>  
  
 <span data-ttu-id="63b67-124">假設您使用預設檔案位置和標準安裝，則基底目錄便位於 C:\Program Files\Microsoft SQL Server。</span><span class="sxs-lookup"><span data-stu-id="63b67-124">Assuming you use the default file locations and a standard installation, the base directory is found at C:\Program Files\Microsoft SQL Server.</span></span> <span data-ttu-id="63b67-125">在該目錄中，二進位編碼檔案與組件的安裝位置如下：</span><span class="sxs-lookup"><span data-stu-id="63b67-125">Within that, following are where the binaries and assemblies are installed to:</span></span>  
  
-   <span data-ttu-id="63b67-126">在 32 位元系統上：</span><span class="sxs-lookup"><span data-stu-id="63b67-126">On a 32-bit system:</span></span>  
  
     [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]<span data-ttu-id="63b67-127">工具</span><span class="sxs-lookup"><span data-stu-id="63b67-127">Tools</span></span>  
  
     <span data-ttu-id="63b67-128">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="63b67-128">\- OR -</span></span>  
  
     <span data-ttu-id="63b67-129">\<Share Feature Directory>\Tools \\ (使用者提供的替代共用功能目錄) </span><span class="sxs-lookup"><span data-stu-id="63b67-129">\<Share Feature Directory>\Tools\\(user-supplied alternative shared feature directory)</span></span>  
  
-   <span data-ttu-id="63b67-130">在 64 位元系統上：</span><span class="sxs-lookup"><span data-stu-id="63b67-130">On a 64-bit system:</span></span>  
  
     <span data-ttu-id="63b67-131">C:\Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (x86) \120\Tools</span><span class="sxs-lookup"><span data-stu-id="63b67-131">C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (x86) \120\Tools</span></span>  
  
     <span data-ttu-id="63b67-132">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="63b67-132">\- OR -</span></span>  
  
     <span data-ttu-id="63b67-133">\<Share Feature Directory (x86)>\Tools \\ (使用者提供的替代共用功能 (x86) 目錄) </span><span class="sxs-lookup"><span data-stu-id="63b67-133">\<Share Feature Directory (x86)>\Tools\\(user-supplied alternative shared feature (x86) directory)</span></span>  
  
### <a name="to-install-distributed-replay-features"></a><span data-ttu-id="63b67-134">安裝 Distributed Replay 功能</span><span class="sxs-lookup"><span data-stu-id="63b67-134">To install Distributed Replay features</span></span>  
  
1.  <span data-ttu-id="63b67-135">如果要開始安裝 Distributed Replay 功能，請啟動 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝精靈。</span><span class="sxs-lookup"><span data-stu-id="63b67-135">To start the installation of any of the Distributed Replay features, start the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Installation Wizard.</span></span>  
  
2.  <span data-ttu-id="63b67-136">[安裝程式支援規則]  頁面會識別安裝 SQL Server 安裝程式支援檔案時可能會發生的問題。</span><span class="sxs-lookup"><span data-stu-id="63b67-136">The **Setup Support Rules** page identifies issues that might occur when installing the SQL Server Setup support files.</span></span> <span data-ttu-id="63b67-137">您必須先更正任何安裝程式支援失敗，然後再繼續進行安裝。</span><span class="sxs-lookup"><span data-stu-id="63b67-137">You must correct any Setup support failures before continuing with Setup.</span></span>  
  
3.  <span data-ttu-id="63b67-138">在 **[產品金鑰]** 頁面上，選取選項按鈕，指出您要安裝免費的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本，或具有 PID 金鑰之產品的實際執行版本。</span><span class="sxs-lookup"><span data-stu-id="63b67-138">On the **Product Key** page, select an option button to indicate whether you are installing a free edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or a production version of the product that has a PID key.</span></span> <span data-ttu-id="63b67-139">如需詳細資訊，請參閱[SQL Server 2014 的版本和元件](../editions-and-components-of-sql-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="63b67-139">For more information, see [Editions and Components of SQL Server 2014](../editions-and-components-of-sql-server-2016.md).</span></span>  
  
4.  <span data-ttu-id="63b67-140">在 **[授權條款]** 頁面上，閱讀授權條款，然後選取要接受授權條款和條件的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="63b67-140">On the **License Terms** page, read the license agreement, and then select the check box to accept the license terms and conditions.</span></span> <span data-ttu-id="63b67-141">若要協助提升 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，您也可以啟用功能使用方式選項，並傳送報告給 [!INCLUDE[msCoName](../../includes/msconame-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="63b67-141">To help improve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can also enable the feature usage option and send reports to [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
5.  <span data-ttu-id="63b67-142">在 [安裝程式支援檔案]  頁面上，按一下 [安裝]  ，即可安裝或更新 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的安裝程式支援檔案。</span><span class="sxs-lookup"><span data-stu-id="63b67-142">On the **Setup Support Files** page, click **Install** to install or update the Setup Support files for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
6.  <span data-ttu-id="63b67-143">在 [安裝程式角色]  頁面上，選取 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能安裝]  ，然後按一下 [下一步]  繼續前往 [特徵選取]  頁面。</span><span class="sxs-lookup"><span data-stu-id="63b67-143">On the **Setup Role** page, select **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Feature Installation**, and then click **Next** to continue to the **Feature Selection** page.</span></span>  
  
7.  <span data-ttu-id="63b67-144">在 [特徵選取]  頁面上，設定您想要安裝的功能。</span><span class="sxs-lookup"><span data-stu-id="63b67-144">On the **Feature Selection** page, configure which features you want to install.</span></span>  
  
    -   <span data-ttu-id="63b67-145">若要安裝管理工具，請選取 [管理工具 - 基本]  。</span><span class="sxs-lookup"><span data-stu-id="63b67-145">To install the administration tool, select **Management Tools - Basic**.</span></span>  
  
    -   <span data-ttu-id="63b67-146">如果要安裝控制器服務，請選取 [Distributed Replay Controller]  。</span><span class="sxs-lookup"><span data-stu-id="63b67-146">To install the controller service, select **Distributed Replay Controller**.</span></span>  
  
    -   <span data-ttu-id="63b67-147">如果要安裝用戶端服務，請選取 [Distributed Replay Client]  。</span><span class="sxs-lookup"><span data-stu-id="63b67-147">To install the client service, select **Distributed Replay Client**.</span></span>  
  
     <span data-ttu-id="63b67-148">**重要**：當您設定 Distributed Replay Controller 時，可以指定將用來執行 Distributed Replay Client 服務的一或多個使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="63b67-148">**Important**: When you configure Distributed Replay controller, you can specify one or more user accounts that will be used to run the Distributed Replay client services.</span></span> <span data-ttu-id="63b67-149">下列是支援帳戶的清單：</span><span class="sxs-lookup"><span data-stu-id="63b67-149">The following is the list of supported accounts:</span></span>  
  
    -   <span data-ttu-id="63b67-150">網域使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="63b67-150">Domain user account</span></span>  
  
    -   <span data-ttu-id="63b67-151">使用者建立的本機使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="63b67-151">User created local user account</span></span>  
  
    -   <span data-ttu-id="63b67-152">系統管理員</span><span class="sxs-lookup"><span data-stu-id="63b67-152">Administrator</span></span>  
  
    -   <span data-ttu-id="63b67-153">虛擬帳戶和 MSA (受管理的服務帳戶)</span><span class="sxs-lookup"><span data-stu-id="63b67-153">Virtual account and MSA (Managed Service Account)</span></span>  
  
    -   <span data-ttu-id="63b67-154">網路服務、本機系統和系統</span><span class="sxs-lookup"><span data-stu-id="63b67-154">Network Services, Local Services, and System</span></span>  
  
     <span data-ttu-id="63b67-155">不接受群組帳戶 (本機或網域) 和其他內建帳戶 (例如 Everyone)。</span><span class="sxs-lookup"><span data-stu-id="63b67-155">Group accounts (local or domain) and other built-in accounts (like Everyone) are not accepted.</span></span>  
  
8.  <span data-ttu-id="63b67-156">(選擇性) 按一下省略符號 (...) 按鈕，即可變更共用功能目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="63b67-156">Optionally, click the ellipsis (...) button to change the shared feature directory path.</span></span>  
  
    1.  <span data-ttu-id="63b67-157">在 32 位元電腦上，預設安裝路徑為 **C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\**</span><span class="sxs-lookup"><span data-stu-id="63b67-157">On 32-bit computers, the default installation path is **C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\**</span></span>  
  
    2.  <span data-ttu-id="63b67-158">在 64 位元電腦上，預設安裝路徑為 **C:\Program Files (x86)\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\**</span><span class="sxs-lookup"><span data-stu-id="63b67-158">On 64-bit computers, the default installation path is **C:\Program Files (x86)\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\**</span></span>  
  
9. <span data-ttu-id="63b67-159">完成後，請按 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="63b67-159">When you are finished, click **Next**.</span></span>  
  
10. <span data-ttu-id="63b67-160">在 [安裝規則]  頁面上，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式會驗證您的電腦組態。</span><span class="sxs-lookup"><span data-stu-id="63b67-160">On the **Installation Rules** page, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup validates your computer configuration.</span></span> <span data-ttu-id="63b67-161">當驗證程序完成之後，請按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="63b67-161">Once the validation process is completed, click **Next**.</span></span>  
  
11. <span data-ttu-id="63b67-162">**[磁碟空間需求]** 頁面會計算您所指定之功能的所需磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="63b67-162">The **Disk Space Requirements** page calculates the required disk space for the features that you specify.</span></span> <span data-ttu-id="63b67-163">然後，它會比較所需的空間與可用的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="63b67-163">Then it compares the required space to the available disk space.</span></span>  
  
12. <span data-ttu-id="63b67-164">在 [錯誤報告]  頁面上，指定您想要傳送給 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 的資訊，以便協助改善 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="63b67-164">On the **Error Reporting** page, specify the information that you want to send to [!INCLUDE[msCoName](../../includes/msconame-md.md)] to help improve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="63b67-165">錯誤報告選項預設為啟用。</span><span class="sxs-lookup"><span data-stu-id="63b67-165">By default, option for error reporting is enabled.</span></span>  
  
13. <span data-ttu-id="63b67-166">系統組態檢查會在 [安裝組態規則]  頁面上另外執行一組規則，藉此向您所指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能驗證電腦組態。</span><span class="sxs-lookup"><span data-stu-id="63b67-166">On the **Installation Configuration Rules** page, the System Configuration Checker will run one more set of rules to validate your computer configuration with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features that you have specified.</span></span>  
  
14. <span data-ttu-id="63b67-167">在 [已完成安裝程式的準備工作]  頁面上，按一下 [安裝]  。</span><span class="sxs-lookup"><span data-stu-id="63b67-167">On the **Ready to Install the Program** page, click **Install**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="63b67-168">安裝 Distributed Replay 之後，您必須在控制器電腦與用戶端電腦上建立防火牆規則，並為目標伺服器上的每個用戶端電腦授與權限。</span><span class="sxs-lookup"><span data-stu-id="63b67-168">After you install Distributed Replay you must create firewall rules on the controller and client computers, and grant each client computer permissions on the target server.</span></span> <span data-ttu-id="63b67-169">如需詳細資訊，請參閱 [完成安裝後步驟](../../tools/distributed-replay/complete-the-post-installation-steps.md)。</span><span class="sxs-lookup"><span data-stu-id="63b67-169">For more information, see [Complete the Post-Installation Steps](../../tools/distributed-replay/complete-the-post-installation-steps.md).</span></span>  
  
 <span data-ttu-id="63b67-170">下列其他主題詳述了 Distributed Replay 的其他安裝方式：</span><span class="sxs-lookup"><span data-stu-id="63b67-170">These additional topics document other ways to install Distributed Replay:</span></span>  
  
-   [<span data-ttu-id="63b67-171">從命令提示字元安裝 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="63b67-171">Install Distributed Replay from the Command Prompt</span></span>](../../tools/distributed-replay/install-distributed-replay-overview.md)  
  
-   [<span data-ttu-id="63b67-172">使用設定檔安裝 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="63b67-172">Install Distributed Replay Using a Configuration File</span></span>](../../../2014/sql-server/install/install-distributed-replay-using-a-configuration-file.md)  
  
## <a name="net-framework-security"></a><span data-ttu-id="63b67-173">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="63b67-173">.NET Framework Security</span></span>  
 <span data-ttu-id="63b67-174">您必須具備管理權限，才可安裝各種 Distributed Replay 功能。</span><span class="sxs-lookup"><span data-stu-id="63b67-174">You must have administrative permissions in order to install any of the Distributed Replay features.</span></span> <span data-ttu-id="63b67-175">只有擁有系統管理員權限的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入能夠將用戶端服務帳戶加入測試伺服器的系統管理員伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="63b67-175">Only a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login having sysadmin permissions can add the client service accounts to the sysadmin server role of the test server.</span></span> <span data-ttu-id="63b67-176">如需 Distributed Replay 安全性考量的詳細資訊，請參閱 [Distributed Replay 安全性](../../tools/distributed-replay/distributed-replay-security.md)。</span><span class="sxs-lookup"><span data-stu-id="63b67-176">For more information about Distributed Replay security considerations, see [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63b67-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63b67-177">See Also</span></span>  
 <span data-ttu-id="63b67-178">[SQL Server 2014 版本所支援的功能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="63b67-178">[Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="63b67-179">[SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md) </span><span class="sxs-lookup"><span data-stu-id="63b67-179">[SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md) </span></span>  
 <span data-ttu-id="63b67-180">[Distributed Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md) </span><span class="sxs-lookup"><span data-stu-id="63b67-180">[Distributed Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md) </span></span>  
 <span data-ttu-id="63b67-181">[管理工具命令列選項 &#40;Distributed Replay Utility&#41;](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md) </span><span class="sxs-lookup"><span data-stu-id="63b67-181">[Administration Tool Command-line Options &#40;Distributed Replay Utility&#41;](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md) </span></span>  
 [<span data-ttu-id="63b67-182">設定 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="63b67-182">Configure Distributed Replay</span></span>](../../tools/distributed-replay/configure-distributed-replay.md)  
  
  
