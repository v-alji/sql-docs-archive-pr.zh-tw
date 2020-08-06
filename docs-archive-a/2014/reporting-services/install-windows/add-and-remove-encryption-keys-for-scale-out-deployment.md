---
title: 新增和移除向外延展部署的加密金鑰 (SSRS Configuration Manager) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- encryption keys [Reporting Services]
- deleting encryption keys
- removing encryption keys
- adding encryption keys
- rskeymgmt utility
- scale-out deployments [Reporting Services]
ms.assetid: 2da86fb3-4b4d-407f-9825-74dcc42486f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3926e57c1ad3bb884af8debf7f831092b223a3cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710330"
---
# <a name="add-and-remove-encryption-keys-for-scale-out-deployment-ssrs-configuration-manager"></a><span data-ttu-id="fa5a4-102">加入和移除向外延展部署的加密金鑰 (SSRS 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="fa5a4-102">Add and Remove Encryption Keys for Scale-Out Deployment (SSRS Configuration Manager)</span></span>
  <span data-ttu-id="fa5a4-103">您可以設定多部報表伺服器來使用共用報表伺服器資料庫，以便在向外延展部署模型中執行 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-103">You can run [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in a scale-out deployment model by configuring multiple report servers to use a shared report server database.</span></span> <span data-ttu-id="fa5a4-104">向外延展部署的成員資格，會依報表伺服器是否在報表伺服器資料庫中儲存加密金鑰而定。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-104">Membership in a scale-out deployment is based on whether the report server stores an encryption key in the report server database.</span></span> <span data-ttu-id="fa5a4-105">您可以加入和移除特定報表伺服器執行個體的加密金鑰，來控制向外延展部署成員資格。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-105">You can control scale-out deployment membership by adding and removing encryption keys for specific report server instances.</span></span> <span data-ttu-id="fa5a4-106">如果您要從部署中移除節點，您可以依照任何順序來移除它們。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-106">If you are removing nodes from the deployment, you can remove them in any order.</span></span> <span data-ttu-id="fa5a4-107">如果您要將節點加入部署中，您必須從已屬於部署的報表伺服器聯結任何新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-107">If you are adding nodes to a deployment, you must join any new instances from a report server that is already part of the deployment.</span></span>  
  
## <a name="using-the-reporting-services-configuration-tool-to-configure-scale-out-deployment"></a><span data-ttu-id="fa5a4-108">使用 Reporting Services 組態工具設定向外延展部署</span><span class="sxs-lookup"><span data-stu-id="fa5a4-108">Using the Reporting Services Configuration Tool to Configure Scale-Out Deployment</span></span>  
 <span data-ttu-id="fa5a4-109">設定向外延展部署的最容易的方式，是使用 Reporting Services 組態工具。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-109">The easiest way to configure a scale-out deployment is to use the Reporting Services Configuration tool.</span></span> <span data-ttu-id="fa5a4-110">如需詳細資訊和逐步指示，請參閱[設定原生模式報表伺服器向外延展部署 &#40;SSRS 設定管理員&#41;](configure-a-native-mode-report-server-scale-out-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-110">For more information and step-by-step instructions, see [Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](configure-a-native-mode-report-server-scale-out-deployment.md).</span></span>  
  
## <a name="using-rskeymgmt-to-configure-scale-out-deployment"></a><span data-ttu-id="fa5a4-111">使用 Rskeymgmt 設定向外延展部署</span><span class="sxs-lookup"><span data-stu-id="fa5a4-111">Using Rskeymgmt to Configure Scale-Out Deployment</span></span>  
 <span data-ttu-id="fa5a4-112">使用 **rskeymgmt** 公用程式初始化報表伺服器執行個體，以使用共用報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-112">Use the **rskeymgmt** utility to initialize a report server instance to use a shared report server database.</span></span> <span data-ttu-id="fa5a4-113">將報表伺服器加入向外延展部署，需要將報表伺服器初始化。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-113">Adding a report server to a scale-out deployment requires that you initialize the report server.</span></span> <span data-ttu-id="fa5a4-114">初始化需要管理員權限。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-114">Initialization requires administrator permissions.</span></span> <span data-ttu-id="fa5a4-115">您必須擁有遠端電腦的管理員認證，且該電腦主控您要聯結至部署的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-115">You must have administrator credentials for the remote computer that hosts the report server you are joining to the deployment.</span></span>  
  
#### <a name="how-to-join-a-report-server-to-a-scale-out-deployment-rskeymgmt"></a><span data-ttu-id="fa5a4-116">如何將報表伺服器聯結至向外延展部署 (rskeymgmt)</span><span class="sxs-lookup"><span data-stu-id="fa5a4-116">How to join a report server to a scale-out deployment (rskeymgmt)</span></span>  
  
1.  <span data-ttu-id="fa5a4-117">在主控已經是報表伺服器向外延展部署成員之報表伺服器的電腦上，於本機執行 **rskeymgmt.exe** 。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-117">Run **rskeymgmt.exe** locally on the computer that hosts a report server that is already a member of the report server scale-out deployment.</span></span>  
  
2.  <span data-ttu-id="fa5a4-118">使用 `-j` 引數，即可將報表伺服器聯結至報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-118">Use the `-j` argument to join a report server to the report server database.</span></span> <span data-ttu-id="fa5a4-119">使用 `-m` 和 `-n` 引數，即可指定您要加入部署中的遠端報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-119">Use the `-m` and `-n` arguments to specify the remote report server instance you want to add to the deployment.</span></span> <span data-ttu-id="fa5a4-120">使用 `-u` 和 `-v` 引數，即可指定遠端電腦上的管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-120">Use the `-u` and `-v` arguments to specify an administrator account on the remote computer.</span></span> <span data-ttu-id="fa5a4-121">如果您要利用相同電腦上的多個報表伺服器執行個體來建立向外延展部署，所用的語法稍有不同。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-121">If you are creating a scale-out deployment using multiple report server instances on the same computer, the syntax to use is slightly different.</span></span> <span data-ttu-id="fa5a4-122">如需您應使用之語法的詳細資訊，請參閱 [rskeymgmt 公用程式 &#40;SSRS&#41;](../tools/rskeymgmt-utility-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-122">For more information about the syntax you should use, see [rskeymgmt Utility &#40;SSRS&#41;](../tools/rskeymgmt-utility-ssrs.md).</span></span>  
  
     <span data-ttu-id="fa5a4-123">下列範例說明，當您要將遠端報表伺服器聯結至向外延展部署 (如果您有遠端電腦的管理員權限，您可以省略認證) 時，您必須指定哪些引數：</span><span class="sxs-lookup"><span data-stu-id="fa5a4-123">The following example illustrates the arguments you must specify if you are joining a remote report server to a scale-out deployment (you can omit credentials if you have administrator permissions on the remote computer):</span></span>  
  
    ```  
    rskeymgmt -j -m <remotecomputer> -n <namedreportserverinstance> -u <administratoraccount> -v <administratorpassword>  
    ```  
  
#### <a name="how-to-remove-a-report-server-from-a-scale-out-deployment-rskeymgmt"></a><span data-ttu-id="fa5a4-124">如何從向外延展部署移除報表伺服器 (rskeymgmt)</span><span class="sxs-lookup"><span data-stu-id="fa5a4-124">How to remove a report server from a scale-out deployment (rskeymgmt)</span></span>  
  
1.  <span data-ttu-id="fa5a4-125">開啟您想要移除之報表伺服器的 rsreportserver.config 檔案，然後尋找安裝識別碼。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-125">Open the rsreportserver.config file of the report server you want to remove and find the installation ID.</span></span> <span data-ttu-id="fa5a4-126">根據預設，這個檔案位於 Program Files\Microsoft SQL Server\MSSQL.*n*\Reporting Services\ReportServer)。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-126">By default, this file is located at Program Files\Microsoft SQL Server\MSSQL.*n*\Reporting Services\ReportServer).</span></span>  
  
     <span data-ttu-id="fa5a4-127">如果您已安裝單一執行個體，電腦上將只有一個 rsreportserver.config 檔。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-127">If you installed a single instance, there will only be one rsreportserver.config file on the computer.</span></span> <span data-ttu-id="fa5a4-128">如果您安裝多個 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行個體，請利用 Reporting Services 組態工具中的 [伺服器狀態] 頁面，尋找您要移除之報表伺服器的執行個體識別碼 (例如，MSSQL.2)。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-128">If multiple instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] are installed, use the Server Status page in the Reporting Services Configuration tool to find the instance identifier (for example, MSSQL.2) for the report server that you want to remove.</span></span> <span data-ttu-id="fa5a4-129">儲存報表伺服器執行個體之程式檔案的資料夾名稱將以執行個體識別碼為基礎 (例如，Program Files\Microsoft SQL Server\MSSQL.2)。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-129">The name of the folder that stores the program files for the report server instance will be based on the instance identifier (for example, Program Files\Microsoft SQL Server\MSSQL.2).</span></span>  
  
2.  <span data-ttu-id="fa5a4-130">執行 **rskeymgmt.exe**。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-130">Run **rskeymgmt.exe**.</span></span> <span data-ttu-id="fa5a4-131">您可以在屬於報表伺服器向外延展部署的任何報表伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-131">You can run it on any report server that is part of the report server scale-out deployment.</span></span>  
  
3.  <span data-ttu-id="fa5a4-132">使用 `-r` 引數，即可將報表伺服器執行個體從向外延展部署釋放。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-132">Use the `-r` argument to release the report server instance from the scale-out deployment.</span></span> <span data-ttu-id="fa5a4-133">下列範例說明您必須指定的引數：</span><span class="sxs-lookup"><span data-stu-id="fa5a4-133">The following example illustrates the arguments you must specify:</span></span>  
  
    ```  
    rskeymgmt -r <installation ID>  
    ```  
  
 <span data-ttu-id="fa5a4-134">雖然這些步驟會從向外延展部署中移除報表伺服器，但是它們不會解除安裝報表伺服器上的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-134">These steps remove the report server from a scale-out deployment, but they do not uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance on the report server.</span></span> <span data-ttu-id="fa5a4-135">在您從向外延展部署中移除報表伺服器之後，如果不再需要該伺服器上的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，可以解除安裝該伺服器的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-135">After you remove the report server from the scale-out deployment, you can uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] from the server if you no longer need [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on that server.</span></span> <span data-ttu-id="fa5a4-136">如需相關資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》的[解除安裝現有的 SQL Server 執行個體 &#40;安裝程式&#41;](../../sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="fa5a4-136">For information, see [Uninstall an Existing Instance of SQL Server &#40;Setup&#41;](../../sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa5a4-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa5a4-137">See Also</span></span>  
 <span data-ttu-id="fa5a4-138">[設定和管理 &#40;SSRS Configuration Manager 的加密金鑰&#41;](ssrs-encryption-keys-manage-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="fa5a4-138">[Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-manage-encryption-keys.md) </span></span>  
 [<span data-ttu-id="fa5a4-139">將報表伺服器初始化 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="fa5a4-139">Initialize a Report Server &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-initialize-a-report-server.md)  
  
  
