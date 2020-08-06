---
title: 使用設定檔安裝 SQL Server 2014 |Microsoft Docs
ms.custom: ''
ms.date: 01/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: a832153a-6775-4bed-83f0-55790766d885
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a2f09ad6253762fe5b525f6c918931f4806c84c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688158"
---
# <a name="install-sql-server-2014-using-a-configuration-file"></a><span data-ttu-id="d0bd5-102">使用組態檔安裝 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="d0bd5-102">Install SQL Server 2014 Using a Configuration File</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d0bd5-103">安裝程式可供您根據系統預設值與執行階段輸入，產生組態檔。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-103">Setup provides the ability to generate a configuration file based upon the system default and run-time inputs.</span></span> <span data-ttu-id="d0bd5-104">您可以使用相同的設定，於整個企業中利用組態檔部署 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-104">You can use the configuration file to deploy [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] throughout the enterprise with the same configuration.</span></span> <span data-ttu-id="d0bd5-105">您也可以透過建立啟動 Setup.exe 的批次檔，在企業中將手動安裝標準化。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-105">You can also standardize manual installations throughout the enterprise, by creating a batch file that launches Setup.exe.</span></span>  
  
 <span data-ttu-id="d0bd5-106">安裝程式僅支援透過命令提示字元使用組態檔。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-106">Setup supports the use of the configuration file only through the command prompt.</span></span> <span data-ttu-id="d0bd5-107">使用組態檔時，參數的處理順序如下所述：</span><span class="sxs-lookup"><span data-stu-id="d0bd5-107">The processing order of the parameters while using the configuration file is outlined below:</span></span>  
  
-   <span data-ttu-id="d0bd5-108">組態檔會覆寫封裝中的預設值</span><span class="sxs-lookup"><span data-stu-id="d0bd5-108">The configuration file overwrites the defaults in a package</span></span>  
  
-   <span data-ttu-id="d0bd5-109">命令列的值會覆寫組態檔中的值</span><span class="sxs-lookup"><span data-stu-id="d0bd5-109">Command-line values overwrite the values in the configuration file</span></span>  
  
 <span data-ttu-id="d0bd5-110">組態檔可用來追蹤每個安裝的參數和值。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-110">The configuration file can be used to track the parameters and values for each installation.</span></span> <span data-ttu-id="d0bd5-111">這點會讓組態檔適用於驗證和稽核安裝。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-111">This makes the configuration file useful for verifying and auditing the installations.</span></span>  
  
## <a name="configuration-file-structure"></a><span data-ttu-id="d0bd5-112">組態檔結構</span><span class="sxs-lookup"><span data-stu-id="d0bd5-112">Configuration File Structure</span></span>  
 <span data-ttu-id="d0bd5-113">ConfigurationFile.ini 檔案是包含參數 (名稱/值組) 和描述性註解的文字檔。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-113">The ConfigurationFile.ini file is a text file with parameters (name/value pair) and descriptive comments.</span></span>  
  
 <span data-ttu-id="d0bd5-114">下面是 ConfigurationFile.ini 檔案的範例：</span><span class="sxs-lookup"><span data-stu-id="d0bd5-114">The following is an example of a ConfigurationFile.ini file:</span></span>  
  
```  
; Microsoft SQL Server Configuration file  
[OPTIONS]  
; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE.   
; This is a required parameter.   
ACTION="Install"  
; Specifies features to install, uninstall, or upgrade.   
; The list of top-level features include SQL, AS, RS, IS, and Tools.   
; The SQL feature will install the database engine, replication, and full-text.   
; The Tools feature will install Management Tools, Books online,   
; SQL Server Data Tools, and other shared components.   
FEATURES=SQL,Tools  
```  
  
#### <a name="how-to-generate-a-configuration-file"></a><span data-ttu-id="d0bd5-115">如何產生組態檔</span><span class="sxs-lookup"><span data-stu-id="d0bd5-115">How to generate a configuration file</span></span>  
  
1.  <span data-ttu-id="d0bd5-116">插入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝媒體。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-116">Insert the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation media.</span></span> <span data-ttu-id="d0bd5-117">在根資料夾中，按兩下 Setup.exe。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-117">From the root folder, double-click Setup.exe.</span></span> <span data-ttu-id="d0bd5-118">若要從網路共用進行安裝，請找出共用上的根資料夾，然後按兩下 Setup.exe。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-118">To install from a network share, locate the root folder on the share, and then double-click Setup.exe.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d0bd5-119">Express Edition 安裝程式不會自動建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-119">Express Edition setup does not create a configuration file automatically.</span></span> <span data-ttu-id="d0bd5-120">下列命令將會啟動安裝程式並建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-120">The following command will start  setup and create a configuration file.</span></span>  
    >   
    >  <span data-ttu-id="d0bd5-121">SETUP.exe /UIMODE=Normal /ACTION=INSTALL</span><span class="sxs-lookup"><span data-stu-id="d0bd5-121">SETUP.exe /UIMODE=Normal /ACTION=INSTALL</span></span>  
  
2.  <span data-ttu-id="d0bd5-122">遵循精靈的指示，直到 **[準備安裝]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-122">Follow the wizard through to the **Ready to Install** page.</span></span> <span data-ttu-id="d0bd5-123">組態檔的路徑已指定於 **[準備安裝]** 頁面的 [組態檔路徑] 區段中。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-123">The path to the configuration file is specified in the **Ready to Install** page in the configuration file path section.</span></span> <span data-ttu-id="d0bd5-124">如需有關如何安裝的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[install SQL Server 2014 From The 安裝 Wizard &#40;安裝程式&#41;](install-sql-server-from-the-installation-wizard-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-124">For more information about how to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
3.  <span data-ttu-id="d0bd5-125">取消安裝程式而不實際完成安裝，即可產生 INI 檔案。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-125">Cancel the setup without actually completing the installation, to generate the INI file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d0bd5-126">安裝程式基礎結構會針對已執行的動作寫出所有適當的參數，但密碼等機密資訊除外。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-126">The setup infrastructure writes out all the appropriate parameters for the actions that were run, with the exception of sensitive information such as passwords.</span></span> <span data-ttu-id="d0bd5-127">/IAcceptSQLServerLicenseTerms 參數也不會寫出至組態檔，而且需要修改組態檔或在命令提示字元中提供某個值。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-127">The /IAcceptSQLServerLicenseTerms parameter is also not written out to the configuration file and requires either a modification of the configuration file or a value to be supplied at the command prompt.</span></span> <span data-ttu-id="d0bd5-128">如需詳細資訊，請參閱[從命令提示字元安裝 SQL Server 2014](install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-128">For more information, see [Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md).</span></span> <span data-ttu-id="d0bd5-129">此外，若為通常不會透過命令提示字元提供值的布林值參數，系統就會包含一個值。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-129">In addition, a value is included for Boolean parameters where a value is usually not supplied through the command prompt.</span></span>  
  
## <a name="using-the-configuration-file-to-install-ssnoversion"></a><span data-ttu-id="d0bd5-130">使用組態檔安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0bd5-130">Using the Configuration File to Install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="d0bd5-131">您只能針對命令列安裝使用組態檔。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-131">You can only use the configuration file on command-line installations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d0bd5-132">如果您需要對組態檔進行變更，我們建議您製作副本並使用此副本進行變更。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-132">If you need to make changes to the configuration file, we recommend that you make a copy and work with the copy.</span></span>  
  
#### <a name="how-to-use-a-configuration-file-to-install-a-stand-alone-ssnoversion-instance"></a><span data-ttu-id="d0bd5-133">如何使用組態檔安裝獨立式 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-133">How to use a configuration file to install a stand-alone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance</span></span>  
  
-   <span data-ttu-id="d0bd5-134">透過命令提示字元執行安裝，並且使用 *ConfigurationFile* 參數來提供 ConfigurationFile.ini。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-134">Run the installation through the command prompt and supply the ConfigurationFile.ini using the *ConfigurationFile* parameter.</span></span>  
  
#### <a name="how-to-use-a-configuration-file-to-prepare-and-complete-an-image-of-a-stand-alone-ssnoversion-instance-sysprep"></a><span data-ttu-id="d0bd5-135">如何使用組態檔準備及完成獨立式 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體 (SysPrep) 的映像</span><span class="sxs-lookup"><span data-stu-id="d0bd5-135">How to use a configuration file to prepare and complete an image of a stand-alone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (SysPrep)</span></span>  
  
1.  <span data-ttu-id="d0bd5-136">若要在同一部電腦上準備一個或多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體並進行設定。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-136">To prepare one or more instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and configure them on the same machine.</span></span>  
  
    -   <span data-ttu-id="d0bd5-137">從安裝中心的 [進階] 頁面執行 [準備 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 獨立執行個體的映像]，並擷取備妥的映像組態檔。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-137">Run **Image preparation of a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** from the **Advanced** page of the Installation Center and capture the prepare image configuration file.</span></span>  
  
    -   <span data-ttu-id="d0bd5-138">使用相同的準備映像組態檔當做範本，以便準備其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-138">Use the same prepare image configuration file as a template to prepare more instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="d0bd5-139">從 [安裝中心] 的 [進階] 頁面執行 [完成備妥的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 獨立執行個體的映像]，在電腦上設定備妥的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-139">Run **Image completion of a prepared stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** from the **Advanced** page of the Installation Center to configure a prepared instances on the machine.</span></span>  
  
2.  <span data-ttu-id="d0bd5-140">若要使用 Windows SysPrep 工具來準備作業系統的映像，包括未設定的已備妥 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-140">To prepare an image of the operating system including an unconfigured prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], using Windows SysPrep tool.</span></span>  
  
    -   <span data-ttu-id="d0bd5-141">從 [安裝中心] 的 [進階] 頁面執行 [準備 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 獨立執行個體的映像]，並擷取備妥的映像組態檔。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-141">Run the **Image preparation of a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** from the Advanced page of the Installation Center and capture the prepare image configuration file.</span></span>  
  
    -   <span data-ttu-id="d0bd5-142">從 [安裝中心] 的 [進階] 頁面執行 [完成備妥的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 獨立執行個體的映像]，但在擷取完成的組態檔之後，在 [準備開始完成] 頁面上取消它。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-142">Run the **Image completion of a prepared stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** from the **Advanced** page of the Installation Center, but cancel it on the **Ready to Complete** page after capturing the complete configuration file.</span></span>  
  
    -   <span data-ttu-id="d0bd5-143">完成映像組態檔可以與 Windows 映像儲存在一起，以便自動化已備妥執行個體的組態設定作業。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-143">The complete image configuration file can be stored with the Windows image for automating the configuration of the prepared instances.</span></span>  
  
#### <a name="how-to-install-a-ssnoversion-failover-cluster-using-the-configuration-file"></a><span data-ttu-id="d0bd5-144">如何使用組態檔安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集</span><span class="sxs-lookup"><span data-stu-id="d0bd5-144">How to install a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster using the configuration file</span></span>  
  
1.  <span data-ttu-id="d0bd5-145">整合式安裝選項 (在節點上建立單一節點容錯移轉叢集並且在其他節點上執行 AddNode)：</span><span class="sxs-lookup"><span data-stu-id="d0bd5-145">Integrated Install option (create a single node failover cluster on a node and for additional nodes, run AddNode on them):</span></span>  
  
    -   <span data-ttu-id="d0bd5-146">執行「安裝容錯移轉叢集」選項並且擷取列出所有安裝設定的組態檔。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-146">Run the "Install a Failover Cluster" option and capture the configuration file that lists all the installation settings.</span></span>  
  
    -   <span data-ttu-id="d0bd5-147">透過提供 *ConfigurationFile* 參數，執行命令列容錯移轉叢集安裝。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-147">Run the command-line failover cluster install by supplying the *ConfigurationFile* parameter.</span></span>  
  
    -   <span data-ttu-id="d0bd5-148">在要加入的其他節點上，執行 AddNode 來擷取適用於現有容錯移轉叢集的 ConfigurationFile.ini 檔案。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-148">On an additional node to be added, run AddNode to capture the ConfigurationFile.ini file applicable to the existing failover cluster.</span></span>  
  
    -   <span data-ttu-id="d0bd5-149">透過使用 ConfigurationFile 參數來提供相同的組態檔，在即將聯結容錯移轉叢集的所有其他節點上執行命令列 AddNode。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-149">Run the command-line AddNode on all the additional nodes that will join the failover cluster, by supplying the same configuration file using the ConfigurationFile parameter.</span></span>  
  
2.  <span data-ttu-id="d0bd5-150">進階安裝選項 (在所有容錯移轉叢集節點上準備容錯移轉叢集。然後，準備所有節點之後，在擁有共用磁碟的節點上執行「完成」)：</span><span class="sxs-lookup"><span data-stu-id="d0bd5-150">Advanced install option (prepare failover cluster on all failover cluster nodes, then, after preparing all the nodes, run complete on the node that owns the shared disk):</span></span>  
  
    -   <span data-ttu-id="d0bd5-151">在其中一個節點上執行 **[準備]** ，然後擷取 ConfigurationFile.ini 檔案。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-151">Run **Prepare** on one of the nodes, and capture the ConfigurationFile.ini file.</span></span>  
  
    -   <span data-ttu-id="d0bd5-152">在即將針對容錯移轉叢集準備的所有節點上，提供相同的 ConfigurationFile.ini 檔案給安裝程式。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-152">Supply the same ConfigurationFile.ini file to Setup on all the nodes that will be prepared for the failover cluster.</span></span>  
  
    -   <span data-ttu-id="d0bd5-153">備妥所有節點之後，請在擁有共用磁碟的節點上執行「完成容錯移轉叢集」作業，並且擷取 ConfigurationFile.ini 檔案。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-153">After all the nodes have been prepared, run a complete failover cluster operation on the node that owns the shared disk and capture the ConfigurationFile.ini file.</span></span>  
  
    -   <span data-ttu-id="d0bd5-154">然後，您就可以提供這個 ConfigurationFile.ini 檔案來完成容錯移轉叢集。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-154">You can then supply this ConfigurationFile.ini file to complete the failover cluster.</span></span>  
  
#### <a name="how-to-add-or-remove-a-node-to-a-ssnoversion-failover-cluster-using-the-configuration-file"></a><span data-ttu-id="d0bd5-155">如何使用組態檔為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集加入或移除一個節點</span><span class="sxs-lookup"><span data-stu-id="d0bd5-155">How to add or remove a node to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster using the configuration file</span></span>  
  
-   <span data-ttu-id="d0bd5-156">如果您擁有先前用來在容錯移轉叢集中加入節點或移除節點的組態檔，就可以重複使用相同的檔案來加入或移除其他節點。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-156">If you have a configuration file that was previously used to add a node to or remove a node from a failover cluster, you can reuse that same file to add or remove additional nodes.</span></span>  
  
#### <a name="how-to-upgrade-a-ssnoversion-failover-cluster-using-the-configuration-file"></a><span data-ttu-id="d0bd5-157">如何使用組態檔升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集</span><span class="sxs-lookup"><span data-stu-id="d0bd5-157">How to upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster using the configuration file</span></span>  
  
1.  <span data-ttu-id="d0bd5-158">在被動節點上執行「升級」，然後擷取 ConfigurationFile.ini 檔案。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-158">Run upgrade on the passive node and capture the ConfigurationFile.ini file.</span></span> <span data-ttu-id="d0bd5-159">您可以透過執行實際升級或在結束時退出而不進行實際升級，完成此作業。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-159">You can do this either by performing the actual upgrade, or exiting at the end without doing the actual upgrade.</span></span>  
  
2.  <span data-ttu-id="d0bd5-160">在要升級的所有其他節點上，提供 ConfigurationFile.ini 檔案來完成此程序。</span><span class="sxs-lookup"><span data-stu-id="d0bd5-160">On all the additional nodes to be upgraded, supply the ConfigurationFile.ini file to complete the process.</span></span>  
  
## <a name="sample-syntax"></a><span data-ttu-id="d0bd5-161">範例語法</span><span class="sxs-lookup"><span data-stu-id="d0bd5-161">Sample Syntax</span></span>  
 <span data-ttu-id="d0bd5-162">下面是有關如何使用組態檔的部分範例：</span><span class="sxs-lookup"><span data-stu-id="d0bd5-162">Following are some examples on how to use the configuration file:</span></span>  
  
-   <span data-ttu-id="d0bd5-163">若要在命令提示字元中指定組態檔：</span><span class="sxs-lookup"><span data-stu-id="d0bd5-163">To specify the configuration file at the command prompt:</span></span>  
  
```  
Setup.exe /ConfigurationFile=MyConfigurationFile.INI  
```  
  
-   <span data-ttu-id="d0bd5-164">若要在命令提示字元而非組態檔中指定密碼：</span><span class="sxs-lookup"><span data-stu-id="d0bd5-164">To specify passwords at the command prompt instead of in the configuration file:</span></span>  
  
```  
Setup.exe /SQLSVCPASSWORD="************" /AGTSVCPASSWORD="************" /ASSVCPASSWORD="************" /ISSVCPASSWORD="************" /RSSVCPASSWORD="************" /ConfigurationFile=MyConfigurationFile.INI  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0bd5-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0bd5-165">See Also</span></span>  
 <span data-ttu-id="d0bd5-166">[從命令提示字元安裝 SQL Server 2014](install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="d0bd5-166">[Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md) </span></span>  
 <span data-ttu-id="d0bd5-167">[SQL Server 容錯移轉叢集安裝](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md) </span><span class="sxs-lookup"><span data-stu-id="d0bd5-167">[SQL Server Failover Cluster Installation](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md) </span></span>  
 [<span data-ttu-id="d0bd5-168">升級 SQL Server 容錯移轉叢集</span><span class="sxs-lookup"><span data-stu-id="d0bd5-168">Upgrade a SQL Server Failover Cluster</span></span>](../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md)  
  
  
