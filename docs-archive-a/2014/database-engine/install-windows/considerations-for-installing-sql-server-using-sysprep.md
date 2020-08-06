---
title: 使用 SysPrep 安裝 SQL Server 的考量 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: e1792eeb-2874-4653-b20e-3063f4eb4e5d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 537bb3c55990a68f17697789953c4f15fe023434
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701557"
---
# <a name="considerations-for-installing-sql-server-using-sysprep"></a><span data-ttu-id="f27fb-102">使用 SysPrep 安裝 SQL Server 的考量</span><span class="sxs-lookup"><span data-stu-id="f27fb-102">Considerations for Installing SQL Server Using SysPrep</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f27fb-103">SysPrep 可讓您在電腦上準備 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的獨立執行個體，並於稍後完成設定。</span><span class="sxs-lookup"><span data-stu-id="f27fb-103">SysPrep allows you to prepare a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a computer and to complete the configuration at a later time.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f27fb-104">SysPrep 需要使用包含兩個步驟的程序來取得已設定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]獨立執行個體。</span><span class="sxs-lookup"><span data-stu-id="f27fb-104">SysPrep involves a two-step process to get to a configured stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f27fb-105">這些步驟包含以下內容：</span><span class="sxs-lookup"><span data-stu-id="f27fb-105">The steps include the following:</span></span>  
  
-   [<span data-ttu-id="f27fb-106">準備映像</span><span class="sxs-lookup"><span data-stu-id="f27fb-106">Prepare Image</span></span>](#BKMK_PrepareImage)  
  
     <span data-ttu-id="f27fb-107">這個步驟會在安裝產品二進位編碼檔案之後停止安裝程序，而不會針對正在準備的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體設定電腦、網路或帳戶特有的資訊。</span><span class="sxs-lookup"><span data-stu-id="f27fb-107">This step stops the installation process after the product binaries are installed, without configuring the computer, network, or account-specific information for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is being prepared.</span></span>  
  
-   [<span data-ttu-id="f27fb-108">完成映像</span><span class="sxs-lookup"><span data-stu-id="f27fb-108">Complete Image</span></span>](#BKMK_CompleteImage)  
  
     <span data-ttu-id="f27fb-109">這個步驟可讓您完成已備妥之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的組態。</span><span class="sxs-lookup"><span data-stu-id="f27fb-109">This step enables you to complete the configuration of a prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f27fb-110">在此步驟中，您可以提供電腦、網路和帳戶特有的資訊。</span><span class="sxs-lookup"><span data-stu-id="f27fb-110">During this step, you can provide the computer, network, and account-specific information.</span></span>  
  
 <span data-ttu-id="f27fb-111">如需如何使用 SysPrep 安裝的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[使用 sysprep 安裝 SQL Server 2014](install-sql-server-using-sysprep.md)。</span><span class="sxs-lookup"><span data-stu-id="f27fb-111">For more information about how to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using SysPrep, see [Install SQL Server 2014 Using SysPrep](install-sql-server-using-sysprep.md).</span></span>  
  
## <a name="common-uses-for-ssnoversion-sysprep"></a><span data-ttu-id="f27fb-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep 的常見用法</span><span class="sxs-lookup"><span data-stu-id="f27fb-112">Common Uses for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep</span></span>  
 <span data-ttu-id="f27fb-113">您可依照下列任何方法使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep 功能：</span><span class="sxs-lookup"><span data-stu-id="f27fb-113">You can use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep capability in any of the following ways:</span></span>  
  
-   <span data-ttu-id="f27fb-114">您可以使用「準備映像」步驟，在同一部電腦上準備一個或多個未設定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="f27fb-114">By using the Prepare Image step, you can prepare one or more unconfigured instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the same computer.</span></span> <span data-ttu-id="f27fb-115">您可以在同一部電腦上使用完整的映像步驟來設定這些備妥的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f27fb-115">You can configure these prepared instances by using the Complete Image step on the same computer.</span></span>  
  
-   <span data-ttu-id="f27fb-116">您可以擷取備妥之執行個體的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式組態檔，並將它用於準備多部電腦上的其他未設定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，以供日後組態設定使用。</span><span class="sxs-lookup"><span data-stu-id="f27fb-116">You can capture the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup configuration file of the prepared instance and use it to prepare additional unconfigured [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances on multiple computers for later configuration.</span></span>  
  
-   <span data-ttu-id="f27fb-117">當結合 Windows 系統準備工具 (也稱為 Windows SysPrep) 時，您可以建立作業系統的映像，包括來源電腦上未設定的已備妥 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="f27fb-117">In combination with the Windows System Preparation tool (also known as Windows SysPrep); you can create an image of the operating system including the unconfigured prepared instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the source computer.</span></span> <span data-ttu-id="f27fb-118">然後，您可以將作業系統映像部署到多部電腦上。</span><span class="sxs-lookup"><span data-stu-id="f27fb-118">You can then deploy the operating system image to multiple computers.</span></span> <span data-ttu-id="f27fb-119">當您完成作業系統的組態之後，可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式的「完成映像」步驟來設定備妥的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f27fb-119">After you complete the configuration of the operating system, you can configure the prepared instances by using the Complete Image step of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
     <span data-ttu-id="f27fb-120">Windows SysPrep 工具可用來準備 Windows 作業系統映像，</span><span class="sxs-lookup"><span data-stu-id="f27fb-120">The Windows SysPrep tool is used to prepare Windows operating system images.</span></span> <span data-ttu-id="f27fb-121">其目的是為了擷取作業系統的自訂映像，以供整個組織部署。</span><span class="sxs-lookup"><span data-stu-id="f27fb-121">It is used to capture a customized image of the operating system for deployment throughout an organization.</span></span> <span data-ttu-id="f27fb-122">如需有關 SysPrep 及其用途的詳細資訊，請參閱＜ [什麼是 Sysprep？](https://go.microsoft.com/fwlink/?LinkId=143546)＞。</span><span class="sxs-lookup"><span data-stu-id="f27fb-122">For more information about SysPrep and its uses, see [What is SysPrep](https://go.microsoft.com/fwlink/?LinkId=143546).</span></span>  
  
## <a name="installation-media-considerations"></a><span data-ttu-id="f27fb-123">安裝媒體考量</span><span class="sxs-lookup"><span data-stu-id="f27fb-123">Installation Media Considerations</span></span>  
 <span data-ttu-id="f27fb-124">如果您使用完整版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，請考量以下事項：</span><span class="sxs-lookup"><span data-stu-id="f27fb-124">If you are using a full version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consider the following:</span></span>  
  
-   <span data-ttu-id="f27fb-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的非 Express 版：</span><span class="sxs-lookup"><span data-stu-id="f27fb-125">Non-Express editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
    -   <span data-ttu-id="f27fb-126">「準備映像」步驟會使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Evaluation Edition 來安裝產品二進位編碼檔案。</span><span class="sxs-lookup"><span data-stu-id="f27fb-126">The Prepare Image step uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Evaluation edition to install the product binaries.</span></span> <span data-ttu-id="f27fb-127">當此執行個體完成時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的版本取決於「完成映像」步驟中所提供的產品識別碼。</span><span class="sxs-lookup"><span data-stu-id="f27fb-127">When the instance is completed, the edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] depends on the product ID provided during the complete image step.</span></span>  
  
    -   <span data-ttu-id="f27fb-128">如果您提供 Evaluation Edition 產品識別碼，評估期間將會在備妥的執行個體完成後的 180 天到期。</span><span class="sxs-lookup"><span data-stu-id="f27fb-128">If you provide an Evaluation edition product ID, the evaluation period is set to expire 180 days after the prepared instance is completed.</span></span>  
  
-   <span data-ttu-id="f27fb-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Express 版：</span><span class="sxs-lookup"><span data-stu-id="f27fb-129">Express editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
    -   <span data-ttu-id="f27fb-130">若要準備 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 版本的執行個體，請使用 Express 安裝媒體。</span><span class="sxs-lookup"><span data-stu-id="f27fb-130">To prepare an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express editions, use the Express installation media.</span></span>  
  
    -   <span data-ttu-id="f27fb-131">您不能指定備妥之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 版本執行個體的產品識別碼。</span><span class="sxs-lookup"><span data-stu-id="f27fb-131">You cannot specify Product IDs for a prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express editions.</span></span>  
  
## <a name="supported-ssnoversion-installations"></a><span data-ttu-id="f27fb-132">支援的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝</span><span class="sxs-lookup"><span data-stu-id="f27fb-132">Supported [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installations</span></span>  
 <span data-ttu-id="f27fb-133">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的 SysPrep 支援所有功能，包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的工具。</span><span class="sxs-lookup"><span data-stu-id="f27fb-133">SysPrep in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] supports all features, including tools, of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f27fb-134">您可以針對 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或之前版本的並存安裝準備多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="f27fb-134">You can prepare multiple instances for side-by-side installations of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] or earlier versions.</span></span> <span data-ttu-id="f27fb-135">這些執行個體的功能必須支援 SysPrep。</span><span class="sxs-lookup"><span data-stu-id="f27fb-135">The features of these instances must support SysPrep.</span></span>  
  
 <span data-ttu-id="f27fb-136">當準備映像步驟結束時，將會自動安裝及完成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="f27fb-136">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is automatically installed and completed at the end of the prepare image step.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f27fb-137">當您準備 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體時，也會自動準備瀏覽器與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]寫入器。</span><span class="sxs-lookup"><span data-stu-id="f27fb-137">Browser and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Writer are automatically prepared when you prepare an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f27fb-138">當您在完成映像步驟中完成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時，便會完成這兩個項目。</span><span class="sxs-lookup"><span data-stu-id="f27fb-138">They are completed when you complete the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance by using the Complete Image step.</span></span>  
  
 <span data-ttu-id="f27fb-139">如需支援之版本的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="f27fb-139">For information about supported editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="f27fb-140">您可以執行版本升級，同時設定備妥的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="f27fb-140">You can perform an edition upgrade while configuring a prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f27fb-141">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 版本不支援這個選項。</span><span class="sxs-lookup"><span data-stu-id="f27fb-141">This option is not supported for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express editions.</span></span>  
  
 <span data-ttu-id="f27fb-142">從 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]開始， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep 支援從命令列進行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集安裝。</span><span class="sxs-lookup"><span data-stu-id="f27fb-142">Beginning in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep supports [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster installations from the command line.</span></span>  
  
## <a name="ssnoversion-sysprep-limitations"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f27fb-143">SysPrep 限制</span><span class="sxs-lookup"><span data-stu-id="f27fb-143">SysPrep Limitations</span></span>  
 <span data-ttu-id="f27fb-144">不支援修復備妥的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f27fb-144">Repairing a prepared instance is not supported.</span></span> <span data-ttu-id="f27fb-145">如果安裝程式在準備映像或完成映像步驟期間失敗，您必須執行解除安裝。</span><span class="sxs-lookup"><span data-stu-id="f27fb-145">If Setup fails during the Prepare Image or Complete Image step, you must run uninstall.</span></span>  
  
##  <a name="prepare-image"></a><a name="BKMK_PrepareImage"></a> <span data-ttu-id="f27fb-146">準備映像</span><span class="sxs-lookup"><span data-stu-id="f27fb-146">Prepare Image</span></span>  
 <span data-ttu-id="f27fb-147">準備映像步驟會安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 產品和功能，但不會設定安裝。</span><span class="sxs-lookup"><span data-stu-id="f27fb-147">The Prepare Image step installs the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] product and features but does not configure the installation.</span></span>  
  
 <span data-ttu-id="f27fb-148">您可以在這個步驟中，指定要安裝的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 產品安裝檔的安裝位置。</span><span class="sxs-lookup"><span data-stu-id="f27fb-148">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features to be installed and the installation location for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] product installation files can be specified during this step.</span></span> <span data-ttu-id="f27fb-149">若要準備 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，可以在 [安裝中心] 的 [進階] 頁面上透過 [Image Preparation of a stand-alone instance for SysPrep deployment (準備 SysPrep 部署獨立執行個體的映像)] 或是從命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="f27fb-149">You can prepare an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] either through the **Image Preparation of a stand-alone instance for SysPrep deployment** on the **Advanced** page of the **Installation Center** or from the command prompt.</span></span>  
  
-   <span data-ttu-id="f27fb-150">您可以在同一部電腦上準備多個可於稍後完成的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="f27fb-150">You can prepare multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the same computer that can be completed later.</span></span>  
  
-   <span data-ttu-id="f27fb-151">您可以從現有的已備妥 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體中，新增或移除 SysPrep 安裝所支援的功能。</span><span class="sxs-lookup"><span data-stu-id="f27fb-151">You can add or remove features that are supported for SysPrep installations from the existing prepared instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f27fb-152">當準備好執行個體之後，就可以使用 **[開始]** 功能表上的捷徑，讓您完成已備妥之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的組態。</span><span class="sxs-lookup"><span data-stu-id="f27fb-152">After the instance is prepared, a shortcut on the **Start** menu becomes available to complete the configuration of the prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="complete-image"></a><a name="BKMK_CompleteImage"></a> <span data-ttu-id="f27fb-153">完成映像</span><span class="sxs-lookup"><span data-stu-id="f27fb-153">Complete Image</span></span>  
 <span data-ttu-id="f27fb-154">您可以使用下列其中一個方法，完成已備妥的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體：</span><span class="sxs-lookup"><span data-stu-id="f27fb-154">You can complete the prepared instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using either of the following methods:</span></span>  
  
-   <span data-ttu-id="f27fb-155">使用 [開始] 功能表上的捷徑。</span><span class="sxs-lookup"><span data-stu-id="f27fb-155">Use the shortcut on the Start menu.</span></span>  
  
-   <span data-ttu-id="f27fb-156">在 [安裝中心] 的 [進階] 頁面上存取 [Image completion of a prepared stand-alone instance (完成備妥之獨立執行個體的映像)] 步驟。</span><span class="sxs-lookup"><span data-stu-id="f27fb-156">Access the **Image completion of a prepared stand-alone instance** step on the **Advanced** page of the **Installation Center**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f27fb-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f27fb-157">See Also</span></span>  
 [<span data-ttu-id="f27fb-158">規劃 SQL Server 安裝</span><span class="sxs-lookup"><span data-stu-id="f27fb-158">Planning a SQL Server Installation</span></span>](../../sql-server/install/planning-a-sql-server-installation.md)  
  
  
