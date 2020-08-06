---
title: 針對 Web 同步處理設定 IIS 7 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- IIS 7 server configuration [SQL Server replication]
- Web synchronization, IIS 7 servers
ms.assetid: c201fe2c-0a76-44e5-a233-05e14cd224a6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 65b5aa1ea0d314a9675b1c1b90b688d2990e6d24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607377"
---
# <a name="configure-iis-7-for-web-synchronization"></a><span data-ttu-id="4b196-102">針對 Web 同步處理設定 IIS 7</span><span class="sxs-lookup"><span data-stu-id="4b196-102">Configure IIS 7 for Web Synchronization</span></span>
  <span data-ttu-id="4b196-103">本主題中的程序將逐步引導您完成手動設定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) 7 及更新版本的程序，以搭配使用 Web 同步處理，並進行合併式複寫。</span><span class="sxs-lookup"><span data-stu-id="4b196-103">The procedures in this topic will guide you through the process of manually configuring [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) version 7 and higher for use with Web synchronization for merge replication.</span></span> 
  
 <span data-ttu-id="4b196-104">設定 IIS 7 是啟用 Web 同步處理所需之三個步驟的第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="4b196-104">Configuring IIS 7 is the first of three steps needed to enable Web synchronization.</span></span>  
  
 <span data-ttu-id="4b196-105">如需完整組態處理序的概觀，請參閱[設定 Web 同步處理](configure-web-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="4b196-105">For an overview of the entire configuration process, see [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4b196-106">確定您的應用程式只使用 [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] 或更新版本，而且 IIS 伺服器上未安裝較早版本的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4b196-106">Make sure that your application uses only [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] or later versions, and that earlier versions of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] are not installed on the IIS server.</span></span> <span data-ttu-id="4b196-107">較早版本的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 可能導致錯誤，例如：「Web 同步處理期間的訊息格式無效。</span><span class="sxs-lookup"><span data-stu-id="4b196-107">Earlier versions of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] can cause errors, such as: "The format of a message during Web synchronization was invalid.</span></span> <span data-ttu-id="4b196-108">請確認已在 Web 伺服器正確地設定複寫元件」。</span><span class="sxs-lookup"><span data-stu-id="4b196-108">Ensure that replication components are properly configured at the Web server."</span></span>  
  
 <span data-ttu-id="4b196-109">若要使用 Web 同步處理，您必須完成下列步驟來設定 IIS 7。</span><span class="sxs-lookup"><span data-stu-id="4b196-109">To use Web synchronization, you must configure IIS 7 by completing the following steps.</span></span> <span data-ttu-id="4b196-110">本主題中有每個步驟的詳細描述。</span><span class="sxs-lookup"><span data-stu-id="4b196-110">Each step is described in detail in this topic.</span></span>  
  
1.  <span data-ttu-id="4b196-111">在執行 IIS 的電腦上安裝並設定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener。</span><span class="sxs-lookup"><span data-stu-id="4b196-111">Install and configure the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener on the computer that is running IIS.</span></span>  
  
2.  <span data-ttu-id="4b196-112">設定安全通訊端層 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="4b196-112">Configure Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="4b196-113">IIS 與所有訂閱者之間的通訊都需要 SSL。</span><span class="sxs-lookup"><span data-stu-id="4b196-113">SSL is required for communication between IIS and all subscribers.</span></span>  
  
3.  <span data-ttu-id="4b196-114">設定 IIS 驗證。</span><span class="sxs-lookup"><span data-stu-id="4b196-114">Configure IIS authentication.</span></span>  
  
4.  <span data-ttu-id="4b196-115">設定帳戶並設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener 的權限。</span><span class="sxs-lookup"><span data-stu-id="4b196-115">Configure an account and set permissions for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener.</span></span>  
  
## <a name="installing-the-sql-server-replication-listener"></a><span data-ttu-id="4b196-116">安裝 SQL Server Replication Listener</span><span class="sxs-lookup"><span data-stu-id="4b196-116">Installing the SQL Server Replication Listener</span></span>  

<span data-ttu-id="4b196-117">IIS 5.0 版開始支援 Web 同步處理。</span><span class="sxs-lookup"><span data-stu-id="4b196-117">Web synchronization is supported on IIS, beginning with version 5.0.</span></span> <span data-ttu-id="4b196-118">IIS 7.0 版或更新版本不提供 IIS 5 和 IIS 6 版的 [設定 Web 同步處理精靈]。</span><span class="sxs-lookup"><span data-stu-id="4b196-118">The Configure Web Synchronization Wizard of IIS version 5 and 6, is not available with IIS version 7.0 and higher.</span></span> <span data-ttu-id="4b196-119">**從 SQL Server 2012 開始，若要在 IIS 伺服器上使用 Web 同步處理元件，您應該安裝具有複寫功能的 SQL Server。例如，免費的 SQL Server Express Edition。**</span><span class="sxs-lookup"><span data-stu-id="4b196-119">**Beginning with SQL Server 2012, to use the web sync component on IIS server, you should install SQL Server with replication. This can be the free SQL Server Express edition.**</span></span>
  
#### <a name="to-install-and-configure-the-sql-server-replication-listener"></a><span data-ttu-id="4b196-120">若要安裝和設定 SQL Server Replication Listener</span><span class="sxs-lookup"><span data-stu-id="4b196-120">To install and configure the SQL Server Replication Listener</span></span>  
  
1. <span data-ttu-id="4b196-121">在 IIS 電腦上安裝 SQL Server 複寫。</span><span class="sxs-lookup"><span data-stu-id="4b196-121">Install SQL Server replication on the IIS computer.</span></span>

2.  <span data-ttu-id="4b196-122">在執行 IIS 的電腦上，針對 replisapi.dll 建立新的檔案目錄。</span><span class="sxs-lookup"><span data-stu-id="4b196-122">Create a new file directory for replisapi.dll on the computer that is running IIS.</span></span> <span data-ttu-id="4b196-123">您可以在任何位置建立該目錄，但建議您在 \<*drive*>:\Inetpub 目錄下建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="4b196-123">You can create the directory wherever you want, but we recommend that you create the directory under the \<*drive*>:\Inetpub directory.</span></span> <span data-ttu-id="4b196-124">例如，您可以建立目錄 \<*drive*>:\Inetpub\SQLReplication\\。</span><span class="sxs-lookup"><span data-stu-id="4b196-124">For example, create the directory \<*drive*>:\Inetpub\SQLReplication\\.</span></span>  
  
3.  <span data-ttu-id="4b196-125">將 replisapi.dll 從目錄 [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com\ 複製到步驟 1 中建立的檔案目錄。</span><span class="sxs-lookup"><span data-stu-id="4b196-125">Copy replisapi.dll from the directory [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com\ to the file directory that you created in step 1.</span></span>  
  
4.  <span data-ttu-id="4b196-126">註冊 replisapi.dll：</span><span class="sxs-lookup"><span data-stu-id="4b196-126">Register replisapi.dll:</span></span>  
  
    1.  <span data-ttu-id="4b196-127">按一下 **[開始]** ，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-127">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="4b196-128">在 [**開啟**] 方塊中，輸入 `cmd` ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="4b196-128">In the **Open** box, enter `cmd`, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="4b196-129">在步驟 1 中建立的目錄中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="4b196-129">In the directory created in step 1, execute the following command:</span></span>  
  
         `regsvr32 replisapi.dll`  
  
5.  <span data-ttu-id="4b196-130">為複寫建立新網站，或使用現有的網站。</span><span class="sxs-lookup"><span data-stu-id="4b196-130">Create a new Web site for replication or use an existing site.</span></span> <span data-ttu-id="4b196-131">這個網站將在同步處理期間由複寫元件存取。</span><span class="sxs-lookup"><span data-stu-id="4b196-131">This Web site will be accessed by replication components during synchronization.</span></span> <span data-ttu-id="4b196-132">本主題中的程序將採用預設的網站。</span><span class="sxs-lookup"><span data-stu-id="4b196-132">Procedures in this topic will assume the Default Web Site.</span></span> <span data-ttu-id="4b196-133">如需有關如何建立網站的詳細資訊，請參閱 IIS 文件集。</span><span class="sxs-lookup"><span data-stu-id="4b196-133">For more information about how to create Web sites, see the IIS documentation</span></span>  
  
6.  <span data-ttu-id="4b196-134">在 IIS 中建立虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="4b196-134">Create a virtual directory in IIS.</span></span> <span data-ttu-id="4b196-135">虛擬目錄應該在步驟 4 所建立的網站之下建立，而且應該對應至步驟 1 所建立的目錄。</span><span class="sxs-lookup"><span data-stu-id="4b196-135">The virtual directory should be created under the Web site that you created in step 4 and map it to the directory created in step 1.</span></span> <span data-ttu-id="4b196-136">在指派此目錄的權限時愈嚴格愈好。</span><span class="sxs-lookup"><span data-stu-id="4b196-136">Be as restrictive as possible when you assign permissions to this directory.</span></span> <span data-ttu-id="4b196-137">您至少必須選取 **[讀取]** 和 **[執行]** 權限。</span><span class="sxs-lookup"><span data-stu-id="4b196-137">You must select at least **Read** and **Execute** permissions.</span></span>  
  
    1.  <span data-ttu-id="4b196-138">在 **[Internet Information Services (IIS) 管理員]** 的 **[連線]** 窗格中，以滑鼠右鍵按一下 **[預設的網站]** ，然後選取 **[新增虛擬目錄]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-138">In **Internet Information Services (IIS) Manager**, in the **Connections** pane, right-click **Default Web Site**, and then select **Add Virtual Directory**.</span></span>  
  
    2.  <span data-ttu-id="4b196-139">針對 [**別名**]，輸入 `SQLReplication` 。</span><span class="sxs-lookup"><span data-stu-id="4b196-139">For **Alias**, enter `SQLReplication`.</span></span>  
  
    3.  <span data-ttu-id="4b196-140">針對 [實體路徑]，輸入 **\<drive>:\Inetpub\SQLReplication\\** ，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="4b196-140">For **Physical Path**, enter **\<drive>:\Inetpub\SQLReplication\\**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="4b196-141">設定 IIS，使 replisapi.dll 能夠執行。</span><span class="sxs-lookup"><span data-stu-id="4b196-141">Configure IIS to enable replisapi.dll to execute.</span></span>  
  
    1.  <span data-ttu-id="4b196-142">在 **[Internet Information Services (IIS) 管理員]** 中，按一下 **[預設的網站]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-142">In **Internet Information Services (IIS) Manager**, click **Default Web Site**.</span></span>  
  
    2.  <span data-ttu-id="4b196-143">在中央窗格中，按一下 **[處理常式對應]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-143">In the center pane, click **Handler Mappings**.</span></span>  
  
    3.  <span data-ttu-id="4b196-144">在 **[動作]** 窗格中，按一下 **[新增模組對應]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-144">In the **Actions** pane, click **Add Module Mapping**.</span></span>  
  
    4.  <span data-ttu-id="4b196-145">針對 [**要求**路徑]，輸入 `replisapi.dll` 。</span><span class="sxs-lookup"><span data-stu-id="4b196-145">For **Request** Path, enter `replisapi.dll`.</span></span>  
  
    5.  <span data-ttu-id="4b196-146">從 **[模組]** 下拉式清單中選取 **[IsapiModule]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-146">From the **Module** drop-down list, select **IsapiModule**.</span></span>  
  
    6.  <span data-ttu-id="4b196-147">針對 [可執行檔]，輸入 **\<drive>:\Inetpub\SQLReplication\replisapi.dll**。</span><span class="sxs-lookup"><span data-stu-id="4b196-147">For **Executable**, enter **\<drive>:\Inetpub\SQLReplication\replisapi.dll**.</span></span>  
  
    7.  <span data-ttu-id="4b196-148">針對 [名稱] 輸入 `Replisapi`。</span><span class="sxs-lookup"><span data-stu-id="4b196-148">For **Name**, enter `Replisapi`.</span></span>  
  
    8.  <span data-ttu-id="4b196-149">按一下 **[要求限制]** 按鈕、按一下 **[存取]** 索引標籤，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-149">Click the **Request Restrictions** button, click the **Access** tab, and then click **Execute**.</span></span>  
  
    9. <span data-ttu-id="4b196-150">按一下 **[確定]** 關閉 **[要求限制]** 對話方塊，然後再次按一下 **[確定]** 關閉 **[新增模組對應]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4b196-150">Click **OK** to close the **Request Restrictions** dialog box, and then click **OK** again to close the **Add Module Mapping** dialog box.</span></span> <span data-ttu-id="4b196-151">當系統提示您允許 ISAPI 延伸模組時，請按一下 **[是]** 加入此延伸模組。</span><span class="sxs-lookup"><span data-stu-id="4b196-151">When you are prompted to allow the ISAPI extension, click **Yes** to add the extension.</span></span>  
  
    10. <span data-ttu-id="4b196-152">確認 Replisapi.dll 是否列於 **[已啟用]** 處理常式對應底下。</span><span class="sxs-lookup"><span data-stu-id="4b196-152">Verify that Replisapi.dll is listed under the **Enabled** handler mappings.</span></span> <span data-ttu-id="4b196-153">如果它位於 **[已停用]** 清單中，請以滑鼠右鍵按一下 Replisapi 項目，然後按一下 **[編輯功能權限]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-153">If it is in the **Disabled** list, right-click the Replisapi entry and then click **Edit Feature Permissions**.</span></span> <span data-ttu-id="4b196-154">核取 **[執行]** 方塊，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-154">Check the **Execute** box, and then click **OK**.</span></span>  
  
## <a name="configuring-iis-authentication"></a><span data-ttu-id="4b196-155">設定 IIS 驗證</span><span class="sxs-lookup"><span data-stu-id="4b196-155">Configuring IIS Authentication</span></span>  
 <span data-ttu-id="4b196-156">當訂閱者電腦連接到 IIS 時，訂閱者必須經過 IIS 驗證才能存取資源和處理序。</span><span class="sxs-lookup"><span data-stu-id="4b196-156">When subscriber computers connect to IIS, IIS must authenticate the subscribers before they can access resources and processes.</span></span> <span data-ttu-id="4b196-157">驗證可套用至整個網站或您建立的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="4b196-157">Authentication can be applied to the whole Web site or to the virtual directory that you created.</span></span>  
  
 <span data-ttu-id="4b196-158">我們建議您搭配 SSL 使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="4b196-158">We recommend that you use Basic Authentication with SSL.</span></span> <span data-ttu-id="4b196-159">不論採用哪一種驗證類型，都需要 SSL。</span><span class="sxs-lookup"><span data-stu-id="4b196-159">SSL is required, regardless of the type of authentication that is used.</span></span>  
  
 <span data-ttu-id="4b196-160">我們建議您搭配 SSL 使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="4b196-160">We recommend that you use Basic Authentication with SSL.</span></span> <span data-ttu-id="4b196-161">不論採用哪一種驗證類型，都需要 SSL。</span><span class="sxs-lookup"><span data-stu-id="4b196-161">SSL is required, regardless of the type of authentication that is used.</span></span>  
  
#### <a name="to-configure-iis-authentication"></a><span data-ttu-id="4b196-162">若要設定 IIS 驗證</span><span class="sxs-lookup"><span data-stu-id="4b196-162">To Configure IIS Authentication</span></span>  
  
1.  <span data-ttu-id="4b196-163">在 **[Internet Information Services (IIS) 管理員]** 中，按一下 **[預設的網站]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-163">In **Internet Information Services (IIS) Manager**, click **Default Web Site**.</span></span>  
  
2.  <span data-ttu-id="4b196-164">在中間窗格中，按兩下 **[驗證]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-164">In the middle pane, double-click **Authentication**.</span></span>  
  
3.  <span data-ttu-id="4b196-165">以滑鼠右鍵按一下 [匿名驗證]，然後選擇 [停用]。</span><span class="sxs-lookup"><span data-stu-id="4b196-165">Right-click Anonymous Authentication, and then choose Disable.</span></span>  
  
4.  <span data-ttu-id="4b196-166">以滑鼠右鍵按一下 [基本驗證]，然後選擇 [啟用]。</span><span class="sxs-lookup"><span data-stu-id="4b196-166">Right-click Basic Authentication, and then choose Enable.</span></span>  
  
## <a name="configuring-secure-sockets-layer"></a><span data-ttu-id="4b196-167">設定安全通訊端層</span><span class="sxs-lookup"><span data-stu-id="4b196-167">Configuring Secure Sockets Layer</span></span>  
 <span data-ttu-id="4b196-168">若要設定 SSL，請指定要由執行 IIS 之電腦使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="4b196-168">To configure SSL, specify a certificate to be used by the computer running IIS.</span></span> <span data-ttu-id="4b196-169">合併式複寫的 Web 同步處理支援使用伺服器憑證，但不支援用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="4b196-169">Web synchronization for merge replication supports using server certificates, but not client certificates.</span></span> <span data-ttu-id="4b196-170">若要設定 IIS 以進行部署，必須先從憑證授權中心 (CA) 獲得憑證。</span><span class="sxs-lookup"><span data-stu-id="4b196-170">To configure IIS for deployment, you must first obtain a certificate from a certification authority (CA).</span></span> <span data-ttu-id="4b196-171">如需有關憑證的詳細資訊，請參閱 IIS 文件集。</span><span class="sxs-lookup"><span data-stu-id="4b196-171">For more information about certificates, see the IIS documentation.</span></span>  
  
 <span data-ttu-id="4b196-172">在您安裝憑證之後，必須將憑證與 Web 同步處理所使用的網站相關聯。</span><span class="sxs-lookup"><span data-stu-id="4b196-172">After you install the certificate, you must associate the certificate with the Web site that is used by Web synchronization.</span></span> <span data-ttu-id="4b196-173">如果是為了開發和測試，您可以指定自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="4b196-173">For development and testing, you can specify a self-signed certificate.</span></span> <span data-ttu-id="4b196-174">IIS 7 可以為您建立憑證並在電腦上註冊此憑證。</span><span class="sxs-lookup"><span data-stu-id="4b196-174">IIS 7 can create a certificate for you and register it on your computer.</span></span>  
  
 <span data-ttu-id="4b196-175">針對實際執行部署與此處所提供程序之間的差異在於，進行實際執行和實際執行前測試時，您會使用 CA 所核發的憑證而非自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="4b196-175">The difference between deploying for production and the procedures given here is that in production and pre-production testing, you would use a certificate issued by a CA instead of a self-signed certificate.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4b196-176">若為實際執行安裝，則不建議使用自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="4b196-176">A self-signed certificate is not recommended for a production installation.</span></span> <span data-ttu-id="4b196-177">自我簽署憑證並不安全。</span><span class="sxs-lookup"><span data-stu-id="4b196-177">Self-signed certificates are not secure.</span></span> <span data-ttu-id="4b196-178">如果只是為了開發和測試，請使用自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="4b196-178">Use self-signed certificates for development and testing only.</span></span>  
  
 <span data-ttu-id="4b196-179">若要設定 SSL，您將執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="4b196-179">To configure SSL, you will perform the following steps:</span></span>  
  
1.  <span data-ttu-id="4b196-180">將網站設定為要求 SSL 並忽略用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="4b196-180">Configure the Web site to require SSL and ignore client certificates.</span></span>  
  
2.  <span data-ttu-id="4b196-181">從 CA 取得憑證，或建立自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="4b196-181">Obtain a certificate from a CA or create a self-signed certificate.</span></span>  
  
3.  <span data-ttu-id="4b196-182">將憑證繫結至複寫網站。</span><span class="sxs-lookup"><span data-stu-id="4b196-182">Bind the certificate to the replication Web site.</span></span>  
  
#### <a name="to-require-ssl-security-for-a-web-site"></a><span data-ttu-id="4b196-183">若要要求網站的 SSL 安全性</span><span class="sxs-lookup"><span data-stu-id="4b196-183">To require SSL security for a Web site</span></span>  
  
1.  <span data-ttu-id="4b196-184">在 **[Internet Information Services (IIS) 管理員]** 中，展開本機伺服器節點，然後按一下 **[預設的網站]** (或是您的 Web 同步處理網站，如果它與預設的網站不同的話)。</span><span class="sxs-lookup"><span data-stu-id="4b196-184">In **Internet Information Services (IIS) Manager**, expand the local server node, and then click the **Default Web Site** (or your Web synchronization site if it is different from the default Web site).</span></span>  
  
2.  <span data-ttu-id="4b196-185">在中間窗格中，按兩下 **[SSL 設定]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-185">In the middle pane, double-click **SSL Settings**.</span></span>  
  
3.  <span data-ttu-id="4b196-186">核取 **[必須使用 SSL]** 選項。</span><span class="sxs-lookup"><span data-stu-id="4b196-186">Check the **Require SSL** option.</span></span> <span data-ttu-id="4b196-187">在 **[用戶端憑證]** 底下，確認已選取 **[略過]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4b196-187">Under **Client certificates**, verify that the **Ignore** button is selected.</span></span>  
  
#### <a name="to-create-a-self-signed-certificate-for-testing"></a><span data-ttu-id="4b196-188">若要針對測試建立自我簽署憑證</span><span class="sxs-lookup"><span data-stu-id="4b196-188">To create a self-signed certificate for testing</span></span>  
  
1.  <span data-ttu-id="4b196-189">在 **[Internet Information Services (IIS) 管理員]** 中，按一下本機伺服器節點，然後在中央窗格中，按兩下 **[伺服器憑證]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-189">In **Internet Information Services (IIS) Manager**, click the local server node, and then in the center pane, double-click on **Server Certificates**.</span></span>  
  
2.  <span data-ttu-id="4b196-190">在 **[動作]** 窗格中，按一下 **[建立自我簽署憑證]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-190">In the **Actions** pane, click **Create Self-Signed Certificate**.</span></span>  
  
3.  <span data-ttu-id="4b196-191">在 **[建立自我簽署憑證]** 對話方塊中，輸入憑證的名稱，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-191">In the **Create Self-Signed Certificate** dialog box, enter a name for the certificate, and then click **OK**.</span></span>  
  
###### <a name="to-bind-a-certificate-to-a-web-site"></a><span data-ttu-id="4b196-192">若要將憑證繫結至網站</span><span class="sxs-lookup"><span data-stu-id="4b196-192">To bind a certificate to a Web site</span></span>  
  
1.  <span data-ttu-id="4b196-193">在 **[連線]** 窗格中，按一下 **[預設的網站]** (或是您的 Web 同步處理網站，如果它與預設的網站不同的話)。</span><span class="sxs-lookup"><span data-stu-id="4b196-193">In the **Connections** pane, click the **Default Web Site** (or your Web synchronization site, if it is different from the default Web site).</span></span>  
  
2.  <span data-ttu-id="4b196-194">在 **[動作]** 窗格中，按一下 **[繫結]** ，然後按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-194">In the **Actions** pane, click **Bindings**, and then click **Add**.</span></span> <span data-ttu-id="4b196-195">**[新增站台繫結]** 對話方塊將會出現。</span><span class="sxs-lookup"><span data-stu-id="4b196-195">The **Add Site Binding** dialog box will appear.</span></span>  
  
3.  <span data-ttu-id="4b196-196">從 **[類型]** 下拉式清單中選取 **[https]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-196">From the **Type** drop-down list, select **https**.</span></span> <span data-ttu-id="4b196-197">保留 **[IP 位址]** 和 **[連接埠]** 的預設設定。</span><span class="sxs-lookup"><span data-stu-id="4b196-197">Leave the default settings for **IP address** and **Port**.</span></span>  
  
4.  <span data-ttu-id="4b196-198">從 **[SSL 憑證]** 下拉式清單中，選取您在＜若要針對測試建立自我簽署憑證＞中建立的憑證、按一下 **[確定]** ，然後按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-198">From the **SSL certificate** drop-down list, select the certificate created in "To create a self-signed certificate for testing," click **OK**, and then click **Close**.</span></span>  
  
###### <a name="to-test-the-certificate"></a><span data-ttu-id="4b196-199">若要測試憑證</span><span class="sxs-lookup"><span data-stu-id="4b196-199">To test the certificate</span></span>  
  
1.  <span data-ttu-id="4b196-200">在 **在ternet 在formation Services (IIS) Manager**中，按一下 **[預設的網站].**</span><span class="sxs-lookup"><span data-stu-id="4b196-200">In **Internet Information Services (IIS) Manager**, click **Default Web Site.**</span></span>  
  
2.  <span data-ttu-id="4b196-201">在 [動作] 窗格中，按一下 [瀏覽 \*:443(https)]。</span><span class="sxs-lookup"><span data-stu-id="4b196-201">From the **Actions** pane, click **Browse \*:443(https)**.</span></span>  
  
3.  <span data-ttu-id="4b196-202">Internet Explorer 將開啟並顯示一則訊息：「此網站的安全性憑證有問題」。</span><span class="sxs-lookup"><span data-stu-id="4b196-202">Internet Explorer will open and display a message that "There is a problem with this website's security certificate."</span></span> <span data-ttu-id="4b196-203">這則警告是要告知您，相關聯的憑證是由無法辨識的 CA 所核發，而且可能不值得信任。</span><span class="sxs-lookup"><span data-stu-id="4b196-203">This warning tells you that the associated certificate was not issued by a recognized CA and might not be trustworthy.</span></span> <span data-ttu-id="4b196-204">這是預期的警告，因此請按一下 **[繼續瀏覽此網站 (不建議)]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-204">This is an expected warning, so click **Continue to this website (not recommended)**.</span></span>  
  
4.  <span data-ttu-id="4b196-205">如果系統提示您 **[連線到 localhost]** ，請輸入使用者名稱和密碼以繼續。</span><span class="sxs-lookup"><span data-stu-id="4b196-205">If you are prompted to **Connect to localhost**, enter a user name and password to proceed.</span></span> <span data-ttu-id="4b196-206">此時，您應該會看到網站的預設頁面。</span><span class="sxs-lookup"><span data-stu-id="4b196-206">You should see the default page for the Web site.</span></span>  
  
## <a name="setting-permissions-for-the-sql-server-replication-listener"></a><span data-ttu-id="4b196-207">設定 SQL Server Replication Listener 的權限</span><span class="sxs-lookup"><span data-stu-id="4b196-207">Setting Permissions for the SQL Server Replication Listener</span></span>  
 <span data-ttu-id="4b196-208">當訂閱者電腦連接到執行 IIS 的電腦時，系統會利用您先前設定 IIS 時所指定的驗證類型來驗證訂閱者。</span><span class="sxs-lookup"><span data-stu-id="4b196-208">When a subscriber computer connects to the computer running IIS, the subscriber is authenticated by using the type of authentication specified when you configured IIS.</span></span> <span data-ttu-id="4b196-209">IIS 驗證訂閱者之後，IIS 會檢查訂閱者是否獲授權叫用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複寫。</span><span class="sxs-lookup"><span data-stu-id="4b196-209">After IIS authenticates the subscriber, IIS checks whether the subscriber is authorized to invoke [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="4b196-210">您可藉由設定 replisapi.dll 的權限來控制可以叫用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複寫的使用者。</span><span class="sxs-lookup"><span data-stu-id="4b196-210">You control the users that can invoke [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication by setting permissions for replisapi.dll.</span></span> <span data-ttu-id="4b196-211">您必須適當地設定權限，才能避免未經授權的使用者存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複寫。</span><span class="sxs-lookup"><span data-stu-id="4b196-211">Properly configuring permissions is necessary to prevent unauthorized access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span>  
  
 <span data-ttu-id="4b196-212">若要設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener 執行時所用帳戶的最小權限，請完成下列程序。</span><span class="sxs-lookup"><span data-stu-id="4b196-212">To configure the minimum permissions for the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener runs, complete the following procedure.</span></span> <span data-ttu-id="4b196-213">下列程序中的步驟適用於執行 IIS 7.0 的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Server 2008。</span><span class="sxs-lookup"><span data-stu-id="4b196-213">The steps in the following procedure apply to [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Server 2008 running IIS 7.0.</span></span>  
  
 <span data-ttu-id="4b196-214">除了執行下列步驟之外，請確保所需的登入位於發行集存取清單 (PAL) 中。</span><span class="sxs-lookup"><span data-stu-id="4b196-214">In addition to performing the following steps, make sure that the required logins are in the publication access list (PAL).</span></span> <span data-ttu-id="4b196-215">如需 PAL 的詳細資訊，請參閱[保護發行者](security/secure-the-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="4b196-215">For more information about the PAL, see [Secure the Publisher](security/secure-the-publisher.md).</span></span>  
  
 <span data-ttu-id="4b196-216">**重要事項** ：在本節中建立的帳戶就是在同步處理期間連接至發行者和散發者的帳戶。</span><span class="sxs-lookup"><span data-stu-id="4b196-216">**Important** The account created in this section is the account that will connect to the Publisher and Distributor during synchronization.</span></span> <span data-ttu-id="4b196-217">這個帳戶必須新增為散發和發行集伺服器的 SQL 登入帳戶。</span><span class="sxs-lookup"><span data-stu-id="4b196-217">This account must be added as a SQL Login account on the distribution and publication server.</span></span>  
  
 <span data-ttu-id="4b196-218">用於 SQL Server Replication Listener 的帳戶必須擁有如＜合併代理程式安全性＞主題中＜連接到發行者或散發者＞一節底下所描述的權限。</span><span class="sxs-lookup"><span data-stu-id="4b196-218">The account used for the SQL Server Replication Listener must have permissions as described in the Merge Agent Security topic, in the "Connect to the Publisher or Distributor" section.</span></span>  
  
 <span data-ttu-id="4b196-219">總而言之，此帳戶必須：</span><span class="sxs-lookup"><span data-stu-id="4b196-219">In summary, the account must:</span></span>  
  
-   <span data-ttu-id="4b196-220">是發行集存取清單 (PAL) 的成員。</span><span class="sxs-lookup"><span data-stu-id="4b196-220">Be a member of the Publication Access List (PAL).</span></span>  
  
-   <span data-ttu-id="4b196-221">對應至與發行集資料庫中之使用者相關聯的登入。</span><span class="sxs-lookup"><span data-stu-id="4b196-221">Be mapped to a login associated with a user in the publication database.</span></span>  
  
-   <span data-ttu-id="4b196-222">對應至與散發資料庫中之使用者相關聯的登入。</span><span class="sxs-lookup"><span data-stu-id="4b196-222">Be mapped to a login associated with a user in the distribution database.</span></span>  
  
-   <span data-ttu-id="4b196-223">擁有快照集共用的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="4b196-223">Have Read permissions on the snapshot share.</span></span>  
  
#### <a name="to-configure-the-account-and-permissions"></a><span data-ttu-id="4b196-224">若要設定帳戶和權限</span><span class="sxs-lookup"><span data-stu-id="4b196-224">To configure the account and permissions</span></span>  
  
1.  <span data-ttu-id="4b196-225">在執行 IIS 的電腦上建立本機帳戶：</span><span class="sxs-lookup"><span data-stu-id="4b196-225">Create a local account on the computer running IIS:</span></span>  
  
    1.  <span data-ttu-id="4b196-226">開啟 **[伺服器管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-226">Open **Server Manager**.</span></span> <span data-ttu-id="4b196-227">在 [開始] 功能表中，以滑鼠右鍵按一下 **[電腦]** ，然後按一下 **[管理]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-227">From the Start menu, right-click **Computer**, and then click **Manage**.</span></span>  
  
    2.  <span data-ttu-id="4b196-228">在 **[伺服器管理員]** 中，展開 **[設定]** ，然後展開 **[本機使用者和群組]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-228">In **Server Manager**, expand **Configuration**, and then expand **Local Users and Groups**.</span></span>  
  
    3.  <span data-ttu-id="4b196-229">以滑鼠右鍵按一下 **[使用者]** ，然後按一下 **[新增使用者]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-229">Right-click **Users**, and then click **New User**.</span></span>  
  
    4.  <span data-ttu-id="4b196-230">輸入使用者名稱與增強式密碼。</span><span class="sxs-lookup"><span data-stu-id="4b196-230">Enter a user name and a strong password.</span></span> <span data-ttu-id="4b196-231">清除 **[使用者必須在下次登入時變更密碼]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-231">Clear **User must change password at next logon**.</span></span>  
  
    5.  <span data-ttu-id="4b196-232">按一下 **[建立]** ，然後按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-232">Click **Create**, and then click **Close**.</span></span>  
  
2.  <span data-ttu-id="4b196-233">將此帳戶加入至 IIS_IUSRS 群組：</span><span class="sxs-lookup"><span data-stu-id="4b196-233">Add the account to the IIS_IUSRS group:</span></span>  
  
    1.  <span data-ttu-id="4b196-234">在 **[伺服器管理員]** 中，展開 **[設定]** 、展開 **[本機使用者和群組]** ，然後按一下 **[群組]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-234">In **Server Manager**, expand **Configuration**, expand **Local Users and Groups**, and then click **Groups**.</span></span>  
  
    2.  <span data-ttu-id="4b196-235">以滑鼠右鍵按一下 **[IIS_IUSRS]** ，然後按一下 **[加入群組]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-235">Right-click **IIS_IUSRS**, and then click **Add to Group**.</span></span>  
  
    3.  <span data-ttu-id="4b196-236">在 **[IIS_IUSRS 內容]** 對話方塊中，按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-236">In the **IIS_IUSRS Properties** dialog box, click **Add**.</span></span>  
  
    4.  <span data-ttu-id="4b196-237">在 **[選取使用者、電腦或群組]** 對話方塊中，加入在步驟 1 建立的帳戶。</span><span class="sxs-lookup"><span data-stu-id="4b196-237">In the **Select Users, Computers, or Groups** dialog box, add the account created in step 1.</span></span>  
  
    5.  <span data-ttu-id="4b196-238">確認 **[從這個位置]** 顯示本機電腦的名稱 (而非網域)。</span><span class="sxs-lookup"><span data-stu-id="4b196-238">Verify that **From this location** displays the name of the local computer (not a domain).</span></span> <span data-ttu-id="4b196-239">如果此欄位沒有顯示本機電腦名稱，請按一下 **[位置]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-239">If this field does not display the local computer name, click **Locations**.</span></span> <span data-ttu-id="4b196-240">在 **[位置]** 對話方塊中，選取本機電腦，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-240">In the **Locations** dialog box, select the local computer, and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="4b196-241">在 [選取使用者]  對話方塊和 [IIS_IUSRS Properties] (IIS_IUSRS 屬性)  對話方塊中，按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="4b196-241">In the **Select Users** dialog box and the **IIS_IUSRS Properties** dialog box, click**OK**.</span></span>  
  
3.  <span data-ttu-id="4b196-242">將包含 replisapi.dll 之資料夾的最小權限授與帳戶：</span><span class="sxs-lookup"><span data-stu-id="4b196-242">Grant minimum account permissions on the folder that contains replisapi.dll:</span></span>  
  
    1.  <span data-ttu-id="4b196-243">在 [Windows 檔案總管] 中，以滑鼠右鍵按一下您針對 replisapi.dll 所建立的資料夾，然後按一下 **[內容]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-243">In Windows Explorer, right-click the folder that you created for replisapi.dll, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="4b196-244">在 **[安全性]** 索引標籤上，按一下 **[編輯]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-244">On the **Security** tab, click **Edit**.</span></span>  
  
    3.  <span data-ttu-id="4b196-245">在 [\<foldername> 的權限] 對話方塊中，按一下 [新增] 以新增您在步驟 1 中建立的帳戶。</span><span class="sxs-lookup"><span data-stu-id="4b196-245">In the **Permissions for \<foldername>** dialog box, click **Add** to add the account that you created in step 1.</span></span>  
  
    4.  <span data-ttu-id="4b196-246">確認 **[從這個位置]** 顯示本機電腦的名稱 (而非網域)。</span><span class="sxs-lookup"><span data-stu-id="4b196-246">Verify that **From this location** displays the name of the local computer (not a domain).</span></span> <span data-ttu-id="4b196-247">如果此欄位沒有顯示本機電腦名稱，請按一下 **[位置]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-247">If this field does not display the local computer name, click **Locations**.</span></span> <span data-ttu-id="4b196-248">在 **[位置]** 對話方塊中，選取本機電腦，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-248">In the **Locations** dialog box, select the local computer, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="4b196-249">確認只將**讀取**、**讀取與執行**和**列出資料夾內容**權限授與這個帳戶。</span><span class="sxs-lookup"><span data-stu-id="4b196-249">Verify that the account is granted only **Read**, **Read & Execute**, and **List Folder Contents** permissions.</span></span>  
  
    6.  <span data-ttu-id="4b196-250">選取任何不需要存取目錄的使用者或群組、按一下 **[移除]** ，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-250">Select any users or groups that do not require access to the directory, click **Remove**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="4b196-251">在 **[Internet Information Services (IIS) 管理員]** 中建立應用程式集區：</span><span class="sxs-lookup"><span data-stu-id="4b196-251">Create an application pool in **Internet Information Services (IIS) Manager**:</span></span>  
  
    1.  <span data-ttu-id="4b196-252">在 **[Internet Information Services (IIS) 管理員]** 的 **[連線]** 窗格中，展開本機伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="4b196-252">In **Internet Information Services (IIS) Manager**, in the **Connections** pane, expand the local server node.</span></span>  
  
    2.  <span data-ttu-id="4b196-253">以滑鼠右鍵按一下 **[應用程式集區]** ，然後按一下 **[新增應用程式集區]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-253">Right-click **Application Pools**, and then click **Add Application Pool**.</span></span>  
  
    3.  <span data-ttu-id="4b196-254">輸入應用程式集區的名稱、保留其餘欄位的預設值，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-254">Enter a name for the application pool, leave the default values for the remaining fields, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b196-255">如果您預期有兩個以上的並行同步處理用戶端，可能會想要建立 Web 處理序區。</span><span class="sxs-lookup"><span data-stu-id="4b196-255">If you anticipate having more than two concurrent synchronization clients, you might want to create a web garden.</span></span> <span data-ttu-id="4b196-256">如需詳細資訊，請參閱[建立 Web 處理序區](configure-web-synchronization.md)中的＜建立 Web 處理序區＞。</span><span class="sxs-lookup"><span data-stu-id="4b196-256">For more information, see "Creating a Web Garden" in [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
5.  <span data-ttu-id="4b196-257">將帳戶與應用程式集區相關聯：</span><span class="sxs-lookup"><span data-stu-id="4b196-257">Associate the account with the application pool:</span></span>  
  
    1.  <span data-ttu-id="4b196-258">在 **[Internet Information Services (IIS) 管理員]** 中，展開本機伺服器節點，然後按一下 **[應用程式集區]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-258">In **Internet Information Services (IIS) Manager**, expand the local server node, and then click on **Application Pools**.</span></span>  
  
    2.  <span data-ttu-id="4b196-259">以滑鼠右鍵按一下您先前建立的應用程式集區，然後按一下 **[設定應用程式集區預設值]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-259">Right-click the application pool that you created, and then click **Set Application Pool Defaults**.</span></span>  
  
    3.  <span data-ttu-id="4b196-260">在 **[應用程式集區預設值]** 對話方塊中，向下捲動至 **[處理序模型]** 區段，然後按一下 **[識別]** 欄位。</span><span class="sxs-lookup"><span data-stu-id="4b196-260">In the **Application Pool Defaults** dialog box, scroll down to the **Process Model** section, and then click the **Identity** field.</span></span>  
  
    4.  <span data-ttu-id="4b196-261">按一下位於 **[識別]** 列右側的省略符號按鈕。</span><span class="sxs-lookup"><span data-stu-id="4b196-261">Click the ellipsis button on the right side of the **Identity** row.</span></span>  
  
    5.  <span data-ttu-id="4b196-262">按一下 **[自訂帳戶]** 選項按鈕，然後按一下 **[設定]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-262">Click the **Custom Account** radio button, and then click **Set**.</span></span>  
  
    6.  <span data-ttu-id="4b196-263">在 **[使用者名稱]** 和 **[密碼]** 欄位中，輸入步驟 1 中建立的帳戶和密碼，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-263">In the **User name** and **Password** fields, enter the account and password that were created in step 1, and then click **OK**.</span></span>  
  
    7.  <span data-ttu-id="4b196-264">按一下 [確定]  關閉 [應用程式集區識別]  對話方塊，然後再按一下 [確定]  關閉 [應用程式集區預設值] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4b196-264">Click **OK** to close the **Application Pool Identity** dialog box, and then click **OK** again to close the **Application Pool Defaults**dialog box.</span></span>  
  
6.  <span data-ttu-id="4b196-265">讓應用程式集區與複寫網站產生關聯：</span><span class="sxs-lookup"><span data-stu-id="4b196-265">Associate the application pool with the replication Web site:</span></span>  
  
    1.  <span data-ttu-id="4b196-266">在 **[Internet Information Services (IIS) 管理員]** 中，展開本機伺服器節點，然後按一下 **[預設的網站]** (或是您的 Web 同步處理網站，如果它與預設的網站不同的話)。</span><span class="sxs-lookup"><span data-stu-id="4b196-266">In **Internet Information Services (IIS) Manager**, expand the local server node, and then click on the **Default Web Site** (or your Web synchronization site if it is different from the default Web site).</span></span>  
  
    2.  <span data-ttu-id="4b196-267">在 **[動作]** 窗格的 **[管理網站]** 底下，按一下 **[進階設定]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-267">In the **Actions** pane, under **Manage Web Site**, click **Advanced Settings**.</span></span>  
  
    3.  <span data-ttu-id="4b196-268">在 **[進階設定]** 對話方塊中，按一下 **[應用程式集區]** 右側的省略符號按鈕。</span><span class="sxs-lookup"><span data-stu-id="4b196-268">In the **Advanced Settings** dialog box, click on the ellipsis button to the right of **Application Pool**.</span></span>  
  
    4.  <span data-ttu-id="4b196-269">從 **[應用程式集區]** 下拉式清單中，選取您在步驟 4 中建立的應用程式集區，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-269">From the **Application pool** drop-down list, select the application pool you created in step 4, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="4b196-270">再次按一下 **[確定]** 關閉 [進階設定]。</span><span class="sxs-lookup"><span data-stu-id="4b196-270">Click **OK** again to close Advanced Settings.</span></span>  
  
## <a name="testing-the-connection-to-replisapidll"></a><span data-ttu-id="4b196-271">測試與 replisapi.dll 的連接</span><span class="sxs-lookup"><span data-stu-id="4b196-271">Testing the Connection to replisapi.dll</span></span>  
 <span data-ttu-id="4b196-272">在診斷模式下執行 Web 同步處理，以測試執行 IIS 之電腦的連接，並確定安全通訊端層 (SSL) 憑證已正確安裝。</span><span class="sxs-lookup"><span data-stu-id="4b196-272">Run Web synchronization in diagnostic mode to test the connection to the computer running IIS and to make sure that the Secure Sockets Layer (SSL) certificate is properly installed.</span></span> <span data-ttu-id="4b196-273">若要在診斷模式下執行 Web 同步處理，您必須是執行 IIS 之電腦上的管理員。</span><span class="sxs-lookup"><span data-stu-id="4b196-273">To run Web synchronization in diagnostic mode, you must be an administrator on the computer running IIS.</span></span>  
  
#### <a name="to-test-the-connection-to-replisapidll"></a><span data-ttu-id="4b196-274">若要測試與 replisapi.dll 的連接</span><span class="sxs-lookup"><span data-stu-id="4b196-274">To test the connection to replisapi.dll</span></span>  
  
1.  <span data-ttu-id="4b196-275">確定訂閱者端的區域網路 (LAN) 設定正確：</span><span class="sxs-lookup"><span data-stu-id="4b196-275">Make sure that local area network (LAN) settings at the Subscriber are correct:</span></span>  
  
    1.  <span data-ttu-id="4b196-276">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer 的 **[工具]** 功能表中，按一下 **[網際網路選項]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-276">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer, on the **Tools** menu, click **Internet Options**.</span></span>  
  
    2.  <span data-ttu-id="4b196-277">在 **[連接]** 索引標籤中，按一下 **[LAN 設定]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-277">On the **Connections** tab, click **LAN Settings**.</span></span>  
  
    3.  <span data-ttu-id="4b196-278">如果 LAN 上未使用 Proxy 伺服器，請清除 **[自動偵測設定]** 與 **[在 LAN 中使用 Proxy 伺服器]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-278">If a proxy server is not used on the LAN, clear **Automatically Detect Settings** and **Use a proxy server for your LAN**.</span></span>  
  
    4.  <span data-ttu-id="4b196-279">如果使用 Proxy 伺服器，請按一下 **[在您的區域網路使用 Proxy 伺服器]** 和 **[近端網址不使用 Proxy]** ，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-279">If a proxy server is used, click **Use a proxy server for your LAN** and **Bypass proxy server for local addresses**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="4b196-280">在訂閱者端的 Internet Explorer 中，將 `?diag` 附加至 replisapi.dll 的位址，以便在診斷模式下連接伺服器。</span><span class="sxs-lookup"><span data-stu-id="4b196-280">At the Subscriber, in Internet Explorer, connect to the server in diagnostic mode by appending `?diag` to the address for the replisapi.dll.</span></span> <span data-ttu-id="4b196-281">例如： `https://server.domain.com/directory/replisapi.dll?diag` 。</span><span class="sxs-lookup"><span data-stu-id="4b196-281">For example: `https://server.domain.com/directory/replisapi.dll?diag`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b196-282">在上述範例中，您應該將 **server.domain.com** 取代成 IIS 管理員中 **[伺服器憑證]** 區段底下所列的確切 **[發行給]** 名稱。</span><span class="sxs-lookup"><span data-stu-id="4b196-282">In the example above, **server.domain.com** should be replaced with the exact **Issued To** name listed under the **Server Certificates** section in IIS Manager.</span></span>  
  
3.  <span data-ttu-id="4b196-283">如果 Windows 作業系統無法辨識您先前為 IIS 指定的憑證，則會出現 **[安全性警示]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4b196-283">If the certificate that you specified for IIS is not recognized by the Windows operating system, the **Security Alert** dialog box appears.</span></span> <span data-ttu-id="4b196-284">發生此警示的可能是因為該憑證是測試憑證，或者該憑證是由 Windows 無法辨識的憑證授權單位 (CA) 所發行。</span><span class="sxs-lookup"><span data-stu-id="4b196-284">This alert might occur because the certificate is a test certificate or the certificate was issued by a certification authority (CA) that Windows does not recognize.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b196-285">如果未出現此對話方塊，請確定您要存取之伺服器的憑證已做為信任憑證加入訂閱者端的憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="4b196-285">If this dialog box does not appear, make sure that the certificate for the server that you are accessing has been added to the certificate store at the Subscriber as a trusted certificate.</span></span> <span data-ttu-id="4b196-286">如需有關匯入憑證的詳細資訊，請參閱 IIS 文件集。</span><span class="sxs-lookup"><span data-stu-id="4b196-286">For more information about exporting certificates, see the IIS documentation.</span></span>  
  
    1.  <span data-ttu-id="4b196-287">在 **[安全性警示]** 對話方塊中，按一下 **[檢視憑證]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-287">In the **Security Alert** dialog box, click **View Certificate**.</span></span>  
  
    2.  <span data-ttu-id="4b196-288">在 **[憑證]** 對話方塊的 **[一般]** 索引標籤上，按一下 **[安裝憑證]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-288">In the **Certificate** dialog box, on the **General** tab, click **Install Certificate**.</span></span>  
  
    3.  <span data-ttu-id="4b196-289">完成「憑證匯入精靈」，以接受預設值。</span><span class="sxs-lookup"><span data-stu-id="4b196-289">Complete the Certificate Import Wizard, accepting the defaults.</span></span>  
  
    4.  <span data-ttu-id="4b196-290">在 **[安全性警告]** 對話方塊中，按一下 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-290">In the **Security Warning** dialog box, click **Yes**.</span></span>  
  
    5.  <span data-ttu-id="4b196-291">在「憑證匯入精靈」確認對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-291">In the Certificate Import Wizard confirmation dialog box, click **OK**.</span></span>  
  
    6.  <span data-ttu-id="4b196-292">關閉 **[憑證]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4b196-292">Close the **Certificate** dialog box.</span></span>  
  
    7.  <span data-ttu-id="4b196-293">在 **[安全性警示]** 對話方塊中，按一下 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-293">In the **Security Alert** dialog box, click **Yes**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b196-294">將為使用者安裝憑證。</span><span class="sxs-lookup"><span data-stu-id="4b196-294">Certificates are installed for users.</span></span> <span data-ttu-id="4b196-295">這項處理序必須針對將與 IIS 同步處理的每位使用者執行。</span><span class="sxs-lookup"><span data-stu-id="4b196-295">This process must be performed for each user that will synchronize with IIS.</span></span>  
  
4.  <span data-ttu-id="4b196-296">在 [連接到 \<ServerName>] 對話方塊中，指定合併代理程式要用來連線到 IIS 的登入和密碼。</span><span class="sxs-lookup"><span data-stu-id="4b196-296">In the **Connect to \<ServerName>** dialog box, specify the login and password that the Merge Agent will use to connect to IIS.</span></span> <span data-ttu-id="4b196-297">也可以在「新增訂閱精靈」中指定這些認證。</span><span class="sxs-lookup"><span data-stu-id="4b196-297">These credentials will also be specified in the New Subscription Wizard.</span></span>  
  
5.  <span data-ttu-id="4b196-298">在稱為 **[SQL Websync 診斷資訊]** 的 Internet Explorer 視窗中，確認頁面中每個 **[狀態]** 資料行中的值都是 **[SUCCESS]** 。</span><span class="sxs-lookup"><span data-stu-id="4b196-298">In the Internet Explorer window called **SQL Websync diagnostic information**, verify that the value in each **Status** column on the page is **SUCCESS**.</span></span>  
  
6.  <span data-ttu-id="4b196-299">確定憑證已正確安裝於訂閱者端：</span><span class="sxs-lookup"><span data-stu-id="4b196-299">Make sure that the certificate is installed correctly on the Subscriber:</span></span>  
  
    1.  <span data-ttu-id="4b196-300">關閉 Internet Explorer，然後再重新開啟。</span><span class="sxs-lookup"><span data-stu-id="4b196-300">Close and then reopen Internet Explorer.</span></span>  
  
    2.  <span data-ttu-id="4b196-301">在診斷模式下連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="4b196-301">Connect to the server in diagnostic mode.</span></span> <span data-ttu-id="4b196-302">如果憑證已正確安裝，就不會出現 **[安全性警示]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4b196-302">If the certificate is installed properly, the **Security Alert** dialog box will not appear.</span></span> <span data-ttu-id="4b196-303">如果出現此對話方塊，合併代理程式將在嘗試連接到執行 IIS 的電腦時失敗。</span><span class="sxs-lookup"><span data-stu-id="4b196-303">If the dialog box appears, the Merge Agent will fail when it tries to connect to the computer that is running IIS.</span></span> <span data-ttu-id="4b196-304">您必須確定要存取的伺服器憑證已做為信任憑證加入訂閱者端的憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="4b196-304">You must make sure that the certificate for the server that you are accessing has been added to the certificate store at the Subscriber as a trusted certificate.</span></span> <span data-ttu-id="4b196-305">如需有關匯入憑證的詳細資訊，請參閱 IIS 文件集。</span><span class="sxs-lookup"><span data-stu-id="4b196-305">For more information about exporting certificates, see the IIS documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b196-306">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b196-306">See Also</span></span>  
 <span data-ttu-id="4b196-307">[合併式複寫的 Web 同步處理](web-synchronization-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="4b196-307">[Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md) </span></span>  
 [<span data-ttu-id="4b196-308">設定 Web 同步處理</span><span class="sxs-lookup"><span data-stu-id="4b196-308">Configure Web Synchronization</span></span>](configure-web-synchronization.md)  
  
  
