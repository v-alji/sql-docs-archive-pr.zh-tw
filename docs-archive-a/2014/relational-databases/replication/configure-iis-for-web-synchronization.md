---
title: 針對 Web 同步處理設定 IIS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- IIS server configuration [SQL Server replication]
- websync.log
- Web synchronization, IIS servers
ms.assetid: d651186e-c9ca-4864-a444-2cd6943b8e35
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 523c4fc30151acd3ee4df21f2fdaa2187e702870
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593947"
---
# <a name="configure-iis-for-web-synchronization"></a><span data-ttu-id="b086b-102">針對 Web 同步處理設定 IIS</span><span class="sxs-lookup"><span data-stu-id="b086b-102">Configure IIS for Web Synchronization</span></span>
  <span data-ttu-id="b086b-103">本主題中的程序，會構成設定合併式複寫之 Web 同步處理時所採取的第二個步驟。</span><span class="sxs-lookup"><span data-stu-id="b086b-103">The procedures in this topic make up the second step in configuring Web synchronization for merge replication.</span></span> <span data-ttu-id="b086b-104">請在啟用 Web 同步處理的發行集之後執行這個步驟。</span><span class="sxs-lookup"><span data-stu-id="b086b-104">You perform this step after you enable a publication for Web synchronization.</span></span> <span data-ttu-id="b086b-105">如需組態處理序的概觀，請參閱＜ [[設定 Web 同步處理]](configure-web-synchronization.md)＞。</span><span class="sxs-lookup"><span data-stu-id="b086b-105">For an overview of the configuration process, see [Configure Web Synchronization](configure-web-synchronization.md).</span></span> <span data-ttu-id="b086b-106">完成本主題中的程序之後，請繼續執行第三個步驟，即設定訂閱來使用 Web 同步處理。</span><span class="sxs-lookup"><span data-stu-id="b086b-106">After you complete the procedures in this topic, continue to the third step, configuring a subscription to use Web synchronization.</span></span> <span data-ttu-id="b086b-107">第三個步驟在下列主題中描述：</span><span class="sxs-lookup"><span data-stu-id="b086b-107">This third step is described in the following topics:</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="b086b-108">：[如何：設定訂閱來使用 Web 同步處理\(SQL Server Management Studio\)](https://msdn.microsoft.com/library/ms345214.aspx)</span><span class="sxs-lookup"><span data-stu-id="b086b-108">: [How to: Configure a Subscription to Use Web Synchronization \(SQL Server Management Studio\)](https://msdn.microsoft.com/library/ms345214.aspx)</span></span>  
  
-   <span data-ttu-id="b086b-109">複寫 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式設計： [如何：將訂閱設定為使用 Web 同步處理 (複寫 Transact-SQL 程式設計)](https://msdn.microsoft.com/library/ms345206.aspx)</span><span class="sxs-lookup"><span data-stu-id="b086b-109">Replication [!INCLUDE[tsql](../../includes/tsql-md.md)] programming: [How to: Configure a Subscription to Use Web Synchronization (Replication Transact-SQL Programming)](https://msdn.microsoft.com/library/ms345206.aspx)</span></span>  
  
-   <span data-ttu-id="b086b-110">RMO： [如何：設定訂閱使用 Web 同步處理 (RMO 程式設計)](https://msdn.microsoft.com/library/ms345207.aspx)</span><span class="sxs-lookup"><span data-stu-id="b086b-110">RMO: [How to: Configure a Subscription to Use Web Synchronization (RMO Programming)](https://msdn.microsoft.com/library/ms345207.aspx)</span></span>  
  
 <span data-ttu-id="b086b-111">Web 同步處理利用執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) 的電腦，來同步處理合併式發行集的提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="b086b-111">Web synchronization uses a computer that is running [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) to synchronize pull subscriptions to merge publications.</span></span> <span data-ttu-id="b086b-112">支援 IIS 5.0 版、IIS 6.0 版和 IIS 7.0 版。</span><span class="sxs-lookup"><span data-stu-id="b086b-112">IIS version 5.0, IIS version 6.0, and IIS version 7.0 are supported.</span></span> <span data-ttu-id="b086b-113">但是，IIS 7.0 版不支援「設定 Web 同步處理精靈」。</span><span class="sxs-lookup"><span data-stu-id="b086b-113">The Configure Web Synchronization Wizard is not supported on IIS version 7.0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b086b-114">確定您的應用程式只使用 [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] 或更新版本，而且 IIS 伺服器上未安裝較早版本的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b086b-114">Make sure that your application uses only [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] or later versions, and that earlier versions of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] are not installed on the IIS server.</span></span> <span data-ttu-id="b086b-115">較早版本的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 可能導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="b086b-115">Earlier versions of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] can cause errors.</span></span> <span data-ttu-id="b086b-116">其中包括下列項目：「Web 同步處理期間，訊息的格式無效。</span><span class="sxs-lookup"><span data-stu-id="b086b-116">These include the following: "The format of a message during Web synchronization was invalid.</span></span> <span data-ttu-id="b086b-117">請確認已在 Web 伺服器正確地設定複寫元件」。</span><span class="sxs-lookup"><span data-stu-id="b086b-117">Ensure that replication components are properly configured at the Web server".</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="b086b-118">請勿同時使用 WebSync 和替代快照集資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="b086b-118">Do not use both WebSync and alternate snapshot folder locations at the same time.</span></span>  
  
 <span data-ttu-id="b086b-119">若要使用 Web 同步處理，您必須完成下列步驟來設定 IIS。</span><span class="sxs-lookup"><span data-stu-id="b086b-119">To use Web synchronization, you must configure IIS by completing the following steps.</span></span> <span data-ttu-id="b086b-120">本主題中有每個步驟的詳細描述。</span><span class="sxs-lookup"><span data-stu-id="b086b-120">Each step is described in detail in this topic.</span></span>  
  
1.  <span data-ttu-id="b086b-121">設定安全通訊端層 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="b086b-121">Configure Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="b086b-122">IIS 與所有訂閱者之間的通訊需要 SSL。</span><span class="sxs-lookup"><span data-stu-id="b086b-122">SSL is required for communication between IIS and all Subscribers.</span></span>  
  
2.  <span data-ttu-id="b086b-123">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用安裝精靈，在執行 IIS 的電腦上安裝連接元件 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b086b-123">Install [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connectivity components on the computer that is running IIS by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard.</span></span> <span data-ttu-id="b086b-124">如果您打算使用步驟 3 提到的「設定 Web 同步處理精靈」，您也必須將 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 安裝在執行 IIS 的電腦上。</span><span class="sxs-lookup"><span data-stu-id="b086b-124">If you plan to use the Configure Web Synchronization Wizard that is mentioned in step 3, you must also install [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] on the computer that is running IIS.</span></span>  
  
3.  <span data-ttu-id="b086b-125">設定執行 IIS 的電腦來進行 Web 同步處理。</span><span class="sxs-lookup"><span data-stu-id="b086b-125">Configure the computer that is running IIS for Web synchronization.</span></span> <span data-ttu-id="b086b-126">您可以手動設定電腦，或使用「設定 Web 同步處理精靈」。</span><span class="sxs-lookup"><span data-stu-id="b086b-126">You can configure the computer manually or use the Configure Web Synchronization Wizard.</span></span> <span data-ttu-id="b086b-127">我們建議您使用精靈。</span><span class="sxs-lookup"><span data-stu-id="b086b-127">We recommend that you use the wizard.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b086b-128">如果執行 IIS 的電腦在 Windows 的 64 位元版本上執行，您必須執行下列命令，確定該伺服器已正確設定，才可執行 Internet Server API (ISAPI) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b086b-128">If the computer that is running IIS is running on a 64-bit version of Windows, you must run following command to make sure that the server is properly configured to run Internet Server API (ISAPI) applications.</span></span> <span data-ttu-id="b086b-129">如需詳細資訊，請參閱 IIS 文件集。</span><span class="sxs-lookup"><span data-stu-id="b086b-129">For more information, see the IIS documentation.</span></span>  
  
    ```  
    cscript %SystemDrive%\inetpub\AdminScripts\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 1  
    ```  
  
4.  <span data-ttu-id="b086b-130">為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener 設定適當的權限。</span><span class="sxs-lookup"><span data-stu-id="b086b-130">Set the appropriate permissions for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener.</span></span>  
  
5.  <span data-ttu-id="b086b-131">在診斷模式下執行 Web 同步處理，以測試執行 IIS 的電腦連接，並確定 SSL 憑證已正確安裝。</span><span class="sxs-lookup"><span data-stu-id="b086b-131">Run Web synchronization in diagnostic mode to test the connection to the computer that is running IIS and to make sure that the SSL certificate is properly installed.</span></span>  
  
## <a name="configuring-secure-sockets-layer"></a><span data-ttu-id="b086b-132">設定安全通訊端層</span><span class="sxs-lookup"><span data-stu-id="b086b-132">Configuring Secure Sockets Layer</span></span>  
 <span data-ttu-id="b086b-133">若要設定 SSL，請為所要使用之執行 IIS 的電腦指定一個憑證。</span><span class="sxs-lookup"><span data-stu-id="b086b-133">To configure SSL, specify a certificate for the computer that is running IIS to use.</span></span> <span data-ttu-id="b086b-134">合併式複寫的 Web 同步處理支援使用伺服器憑證，但不支援用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="b086b-134">Web synchronization for merge replication supports using server certificates but not client certificates.</span></span> <span data-ttu-id="b086b-135">若要設定 IIS 以進行部署，必須先從憑證授權中心 (CA) 獲得憑證。</span><span class="sxs-lookup"><span data-stu-id="b086b-135">To configure IIS for deployment, you must first obtain a certificate from a certification authority (CA).</span></span> <span data-ttu-id="b086b-136">憑證授權單位是負責建立及保證屬於使用者、電腦或其他憑證授權中心之公開加密金鑰真實性的實體。</span><span class="sxs-lookup"><span data-stu-id="b086b-136">A certificate authority is an entity that is responsible for establishing and vouching for the authenticity of public encryption keys that belong to users, computers, or other certification authorities.</span></span> <span data-ttu-id="b086b-137">如需有關憑證的詳細資訊，請參閱 IIS 文件集。</span><span class="sxs-lookup"><span data-stu-id="b086b-137">For more information about certificates, see the IIS documentation.</span></span> <span data-ttu-id="b086b-138">在您安裝憑證之後，必須將憑證與 Web 同步處理所使用的網站相關聯。</span><span class="sxs-lookup"><span data-stu-id="b086b-138">After you install the certificate, you must associate the certificate with the Web site that is used by Web synchronization.</span></span>  
  
#### <a name="to-specify-a-certificate-for-deployment"></a><span data-ttu-id="b086b-139">若要指定部署憑證</span><span class="sxs-lookup"><span data-stu-id="b086b-139">To specify a certificate for deployment</span></span>  
  
1.  <span data-ttu-id="b086b-140">以管理員身分登入執行 IIS 的電腦。</span><span class="sxs-lookup"><span data-stu-id="b086b-140">Log on to the computer that is running IIS as an administrator.</span></span>  
  
2.  <span data-ttu-id="b086b-141">啟動 **[Internet Information Services (IIS) 管理員]**：</span><span class="sxs-lookup"><span data-stu-id="b086b-141">Start **Internet Information Services (IIS) Manager**:</span></span>  
  
    1.  <span data-ttu-id="b086b-142">按一下 **[開始]** ，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-142">Click **Start**, and then click **Run**.</span></span>  
  
    2.  <span data-ttu-id="b086b-143">在 [**開啟**] 方塊中，輸入 `inetmgr` ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-143">In the **Open** box, type `inetmgr`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="b086b-144">執行 IIS 憑證精靈：</span><span class="sxs-lookup"><span data-stu-id="b086b-144">Run the IIS Certificate Wizard:</span></span>  
  
    1.  <span data-ttu-id="b086b-145">在 **[Internet Information Services (IIS) 管理員]** 中，展開 **[本機電腦]** 節點，然後展開 **[網站]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b086b-145">In **Internet Information Services (IIS) Manager**, expand the **local computer** node, and then expand the **Web Sites** folder.</span></span>  
  
    2.  <span data-ttu-id="b086b-146">以滑鼠右鍵按一下 **[預設網站]**，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-146">Right-click **Default Web Site**, and then click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="b086b-147">在 **[預設網站屬性]** 對話方塊的 **[目錄安全性]** 索引標籤中，按一下 **[伺服器憑證]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-147">In the **Default Web Site Properties** dialog box, on the **Directory Security** tab, click **Server Certificate**.</span></span>  
  
    4.  <span data-ttu-id="b086b-148">完成「Web 伺服器憑證精靈」。</span><span class="sxs-lookup"><span data-stu-id="b086b-148">Complete the Web Server Certificate Wizard.</span></span>  
  
4.  <span data-ttu-id="b086b-149">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="b086b-149">Click **OK**.</span></span>  
  
 <span data-ttu-id="b086b-150">如果您無法從 CA 取得伺服器憑證，您可以指定憑證來進行測試。</span><span class="sxs-lookup"><span data-stu-id="b086b-150">If you cannot obtain a server certificate from a CA, you can specify a certificate for testing.</span></span> <span data-ttu-id="b086b-151">若要設定 IIS 6.0 來進行測試，請利用 SelfSSL 公用程式來安裝憑證。</span><span class="sxs-lookup"><span data-stu-id="b086b-151">To configure IIS 6.0 for testing, install a certificate by using the SelfSSL utility.</span></span> <span data-ttu-id="b086b-152">IIS 6.0 資源套件中有提供此公用程式。</span><span class="sxs-lookup"><span data-stu-id="b086b-152">This utility is available in the IIS 6.0 Resource Kit.</span></span> <span data-ttu-id="b086b-153">您可以從 [Microsoft 下載中心](https://www.microsoft.com/download/details.aspx?id=5135)下載這些工具。</span><span class="sxs-lookup"><span data-stu-id="b086b-153">You can download the tools from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=5135).</span></span> <span data-ttu-id="b086b-154">如需 IIS 5.0，請移至 [Microsoft 說明及支援](https://go.microsoft.com/fwlink/?LinkId=46229)。</span><span class="sxs-lookup"><span data-stu-id="b086b-154">For IIS 5.0, go to [Microsoft Help and Support](https://go.microsoft.com/fwlink/?LinkId=46229).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b086b-155">憑證必須先與網站相關聯，該網站才能夠使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="b086b-155">A certificate must be associated with a Web site before that Web site can use SSL.</span></span> <span data-ttu-id="b086b-156">SelfSSL 會自動將憑證與預設網站相關聯。</span><span class="sxs-lookup"><span data-stu-id="b086b-156">SelfSSL automatically associates the certificate with the default Web site.</span></span> <span data-ttu-id="b086b-157">如果您已擁有憑證或稍後從 CA 安裝憑證，則必須明確地將憑證與 Web 同步處理所使用的網站相關聯。</span><span class="sxs-lookup"><span data-stu-id="b086b-157">If you already have a certificate or later install a certificate from a CA, you must explicitly associate that certificate with the Web site that is used by Web synchronization.</span></span> <span data-ttu-id="b086b-158">請確定只有一個與用於同步處理訂閱之網站相關聯的憑證。</span><span class="sxs-lookup"><span data-stu-id="b086b-158">Make sure there is only one certificate associated with the Web site that is used to synchronize subscriptions.</span></span> <span data-ttu-id="b086b-159">如果有多個憑證，訂閱者將使用第一個可用的網站。</span><span class="sxs-lookup"><span data-stu-id="b086b-159">If there are multiple certificates, the Subscriber will use the first available Web site.</span></span>  
  
#### <a name="to-specify-a-certificate-for-testing-in-iis-60"></a><span data-ttu-id="b086b-160">若要指定憑證以在 IIS 6.0 中進行測試</span><span class="sxs-lookup"><span data-stu-id="b086b-160">To specify a certificate for testing in IIS 6.0</span></span>  
  
1.  <span data-ttu-id="b086b-161">以管理員身分登入執行 IIS 的電腦。</span><span class="sxs-lookup"><span data-stu-id="b086b-161">Log on to the computer that is running IIS as an administrator.</span></span>  
  
2.  <span data-ttu-id="b086b-162">下載並安裝 SelfSSL。</span><span class="sxs-lookup"><span data-stu-id="b086b-162">Download and install SelfSSL.</span></span> <span data-ttu-id="b086b-163">根據預設，應用程式會安裝到 \<*drive*> ： \Program Files\IIS resources\selfssl。</span><span class="sxs-lookup"><span data-stu-id="b086b-163">By default, the application is installed to \<*drive*>:\Program Files\IIS Resources\SelfSSL.</span></span> <span data-ttu-id="b086b-164">應用程式和檔快捷方式會複製到 \<*drive*> ： \Documents 和 Settings\All Settings\all users\start Menu\Programs\IIS resources\selfssl。</span><span class="sxs-lookup"><span data-stu-id="b086b-164">Application and documentation shortcuts are copied to \<*drive*>:\Documents and Settings\All Users\Start Menu\Programs\IIS Resources\SelfSSL.</span></span>  
  
3.  <span data-ttu-id="b086b-165">執行 SelfSSL：</span><span class="sxs-lookup"><span data-stu-id="b086b-165">Run SelfSSL:</span></span>  
  
    -   <span data-ttu-id="b086b-166">若要利用所有參數的預設值來執行 SelfSSL，請找出應用程式的安裝目錄，然後按兩下 SelfSSL.exe。</span><span class="sxs-lookup"><span data-stu-id="b086b-166">To run SelfSSL with default values for all parameters, locate the installation directory for the application, and then double-click SelfSSL.exe.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="b086b-167">依預設，SelfSSL 安裝的憑證在七天內有效。</span><span class="sxs-lookup"><span data-stu-id="b086b-167">By default, the certificate that is installed by SelfSSL is valid for seven days.</span></span>  
  
    -   <span data-ttu-id="b086b-168">若要指定一或多個參數值：請按一下 **[開始]**，然後按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-168">To specify values for one or more parameters: click **Start**, and then click **Run**.</span></span> <span data-ttu-id="b086b-169">在 [**開啟**] 方塊中，輸入 `cmd` ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-169">In the **Open** box, enter `cmd`, and then click **OK**.</span></span> <span data-ttu-id="b086b-170">找出 SelfSSL 安裝目錄，輸入 `SelfSSL`，然後指定一或多個參數的值。</span><span class="sxs-lookup"><span data-stu-id="b086b-170">Locate the SelfSSL installation directory, type `SelfSSL`, and then specify values for one or more parameters.</span></span> <span data-ttu-id="b086b-171">如需參數列表，請輸入 `SelfSSL -?`。</span><span class="sxs-lookup"><span data-stu-id="b086b-171">For a list of parameters, type `SelfSSL -?`.</span></span>  
  
## <a name="installing-connectivity-components-and-sql-server-management-studio"></a><span data-ttu-id="b086b-172">安裝連接元件和 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b086b-172">Installing Connectivity Components and SQL Server Management Studio</span></span>  
  
#### <a name="to-install-sql-server-connectivity-components-and-sql-server-management-studio"></a><span data-ttu-id="b086b-173">若要安裝 SQL Server 連接元件和 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b086b-173">To install SQL Server connectivity components and SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="b086b-174">以管理員身分登入執行 IIS 的電腦。</span><span class="sxs-lookup"><span data-stu-id="b086b-174">Log on as an administrator to the computer that is running IIS.</span></span>  
  
2.  <span data-ttu-id="b086b-175">從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 安裝磁碟，啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝精靈。</span><span class="sxs-lookup"><span data-stu-id="b086b-175">From the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] installation disk, start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard.</span></span> <span data-ttu-id="b086b-176">如需使用此 wizard 的詳細資訊，請參閱[Install SQL Server 2014 from The 安裝 wizard &#40;安裝程式&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="b086b-176">For more information about using this wizard, see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
3.  <span data-ttu-id="b086b-177">在 **[特徵選取]** 頁面中，選取 **[用戶端工具連接性]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-177">On the **Feature Selection** page, select **Client Tools Connectivity**.</span></span>  
  
4.  <span data-ttu-id="b086b-178">如果您打算使用 [設定 Web 同步處理精靈]，請選取 **[管理工具 - 基本]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-178">If you plan to use the Configure Web Synchronization Wizard, select **Management Tools - Basic**.</span></span>  
  
5.  <span data-ttu-id="b086b-179">完成精靈，然後重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="b086b-179">Complete the wizard, and then restart the computer.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b086b-180">您可以安裝其他元件，但 Web 同步處理只需要連接元件。</span><span class="sxs-lookup"><span data-stu-id="b086b-180">You can install additional components, but only the connectivity components are required for Web synchronization.</span></span>  
  
## <a name="configuring-the-computer-that-is-running-iis-by-using-the-configure-web-synchronization-wizard"></a><span data-ttu-id="b086b-181">利用「設定 Web 同步處理精靈」來設定執行 IIS 的電腦</span><span class="sxs-lookup"><span data-stu-id="b086b-181">Configuring the Computer That Is Running IIS by Using the Configure Web Synchronization Wizard</span></span>  
 <span data-ttu-id="b086b-182">利用「設定 Web 同步處理精靈」或以手動方式來設定 IIS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="b086b-182">Configure the IIS server by using the Configure Web Synchronization Wizard or manually.</span></span> <span data-ttu-id="b086b-183">我們建議您使用精靈，不過，在下一節中，我們也提供手動組態的步驟。</span><span class="sxs-lookup"><span data-stu-id="b086b-183">We recommend using the wizard, but we also provide steps for manual configuration in the next section.</span></span> <span data-ttu-id="b086b-184">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 所提供的「Web 同步處理精靈」只能用於在執行 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]之發行者或升級為 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]之發行者上建立的發行集。</span><span class="sxs-lookup"><span data-stu-id="b086b-184">The Web Synchronization Wizard that is available with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] can be used only for publications that were created on a Publisher that is running [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], or a Publisher that was upgraded to [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span> <span data-ttu-id="b086b-185">此精靈無法用於 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]的發行集。</span><span class="sxs-lookup"><span data-stu-id="b086b-185">The wizard cannot be used for publications on [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="b086b-186">此精靈可搭配 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本以及 [!INCLUDE[ssEWnoversion](../../includes/ssewnoversion-md.md)] 3.0 和更新版本的訂閱使用。</span><span class="sxs-lookup"><span data-stu-id="b086b-186">The wizard can be used with subscriptions on [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions, and [!INCLUDE[ssEWnoversion](../../includes/ssewnoversion-md.md)] 3.0 and later versions.</span></span>  
  
 <span data-ttu-id="b086b-187">這個組態具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="b086b-187">The configuration has the following characteristics:</span></span>  
  
-   <span data-ttu-id="b086b-188">在 IIS 中使用預設網站。</span><span class="sxs-lookup"><span data-stu-id="b086b-188">Uses the default Web site in IIS.</span></span> <span data-ttu-id="b086b-189">不過，您也可以使用其他網站。</span><span class="sxs-lookup"><span data-stu-id="b086b-189">However, you can use another Web site.</span></span> <span data-ttu-id="b086b-190">如需有關如何建立網站的詳細資訊，請參閱 IIS 文件集。</span><span class="sxs-lookup"><span data-stu-id="b086b-190">For more information about how to create Web sites, see the IIS documentation.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b086b-191">您指定的網站提供 Web 同步處理所使用之元件的存取權。</span><span class="sxs-lookup"><span data-stu-id="b086b-191">The Web site that you specify provides access to the components that are used by Web synchronization.</span></span> <span data-ttu-id="b086b-192">網站不提供其他資料或網頁的存取權，除非您將網站設定為必須提供。</span><span class="sxs-lookup"><span data-stu-id="b086b-192">The Web site does not provide access to other data or Web pages unless you configure the site to do so.</span></span>  
  
-   <span data-ttu-id="b086b-193">建立虛擬目錄及其相關聯的別名。</span><span class="sxs-lookup"><span data-stu-id="b086b-193">Creates a virtual directory and its associated alias.</span></span> <span data-ttu-id="b086b-194">別名在存取 Web 同步處理元件時使用。</span><span class="sxs-lookup"><span data-stu-id="b086b-194">The alias is used when accessing the Web synchronization components.</span></span> <span data-ttu-id="b086b-195">例如，若 IIS 位址為 `https://*server.domain.com*` 且您指定別名為 'websync1'，則存取 replisapi.dll 元件的位址為 `https://*server.domain.com*/websync1/replisapi.dll`。</span><span class="sxs-lookup"><span data-stu-id="b086b-195">For example, if the IIS address is `https://*server.domain.com*` and you specify an alias of 'websync1', the address to access the replisapi.dll component is `https://*server.domain.com*/websync1/replisapi.dll`.</span></span>  
  
-   <span data-ttu-id="b086b-196">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="b086b-196">Uses Basic Authentication.</span></span> <span data-ttu-id="b086b-197">我們建議您使用基本驗證，因為，基本驗證可讓您在不同的電腦上執行 IIS 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 發行者/散發者 (建議的組態)，而不需要 Kerberos 委派。</span><span class="sxs-lookup"><span data-stu-id="b086b-197">We recommend using Basic Authentication because Basic Authentication enables you to run IIS and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher/Distributor on separate computers (the recommended configuration) without requiring Kerberos delegation.</span></span> <span data-ttu-id="b086b-198">搭配基本驗證使用 SSL，可以確保登入、密碼及所有資料在傳輸中時都會加密。</span><span class="sxs-lookup"><span data-stu-id="b086b-198">Using SSL with Basic Authentication makes sure that logins, passwords, and all data are encrypted in transit.</span></span> <span data-ttu-id="b086b-199">無論使用哪一種驗證類型，都需要 (SSL。 ) 如需 Web 同步處理最佳作法的詳細資訊，請參閱[設定 Web 同步](configure-web-synchronization.md)處理中的「Web 同步處理的安全性最佳作法」一節。</span><span class="sxs-lookup"><span data-stu-id="b086b-199">(SSL is required, regardless of the type of authentication that is used.) For more information about best practices for Web synchronization, see the section "Security Best Practices for Web Synchronization" in [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
#### <a name="to-configure-the-computer-that-is-running-iis-by-using-the-configure-web-synchronization-wizard"></a><span data-ttu-id="b086b-200">若要利用「設定 Web 同步處理精靈」來設定執行 IIS 的電腦</span><span class="sxs-lookup"><span data-stu-id="b086b-200">To configure the computer that is running IIS by using the Configure Web Synchronization Wizard</span></span>  
  
1.  <span data-ttu-id="b086b-201">在執行 IIS 的電腦上啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b086b-201">On the computer that is running IIS, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="b086b-202">連接到發行者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="b086b-202">Connect to the Publisher, and then expand the server node.</span></span>  
  
3.  <span data-ttu-id="b086b-203">展開 **[本機發行集]** 資料夾，以滑鼠右鍵按一下發行集，然後按一下 **[設定 Web 同步處理]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-203">Expand the **Local Publications** folder, right-click the publication, and then click **Configure Web Synchronization**.</span></span>  
  
4.  <span data-ttu-id="b086b-204">在「設定 Web 同步處理精靈」的 **[訂閱者類型]** 頁面中，選取 **[SQL Server]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-204">In the Configure Web Synchronization Wizard, on the **Subscriber Type** page, select **SQL Server**.</span></span>  
  
5.  <span data-ttu-id="b086b-205">在 **[Web 伺服器]** 頁面中：</span><span class="sxs-lookup"><span data-stu-id="b086b-205">On the **Web Server** page:</span></span>  
  
    1.  <span data-ttu-id="b086b-206">選取將同步處理訂閱的 IIS 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b086b-206">Select the instance of IIS that will synchronize subscriptions.</span></span>  
  
    2.  <span data-ttu-id="b086b-207">選取 **[建立新的虛擬目錄]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-207">Select **Create a new virtual directory**.</span></span>  
  
    3.  <span data-ttu-id="b086b-208">在頁面的下方窗格中，依序展開 IIS 執行個體和 **[網站]**，然後按一下 **[預設網站]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-208">In the lower pane of the page, expand the instance of IIS, expand **Web Sites**, and then click **Default Web Site**.</span></span>  
  
6.  <span data-ttu-id="b086b-209">在 **[虛擬目錄資訊]** 頁面中：</span><span class="sxs-lookup"><span data-stu-id="b086b-209">On the **Virtual Directory Information** page:</span></span>  
  
    1.  <span data-ttu-id="b086b-210">在 **[別名]** 方塊中輸入虛擬目錄的別名。</span><span class="sxs-lookup"><span data-stu-id="b086b-210">In the **Alias** box, enter an alias for the virtual directory.</span></span>  
  
    2.  <span data-ttu-id="b086b-211">在 **[路徑]** 方塊中輸入虛擬目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="b086b-211">In the **Path** box, enter a path of the virtual directory.</span></span> <span data-ttu-id="b086b-212">例如，如果您 `websync1` 在 [**別名**] 方塊中輸入，請 `C:\Inetpub\wwwroot\websync1` 在 [**路徑**] 方塊中輸入。</span><span class="sxs-lookup"><span data-stu-id="b086b-212">For example, if you entered `websync1` in the **Alias** box, enter `C:\Inetpub\wwwroot\websync1` in the **Path** box.</span></span> <span data-ttu-id="b086b-213">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="b086b-213">Click **Next**.</span></span>  
  
    3.  <span data-ttu-id="b086b-214">在兩個對話方塊中，按一下 **[是]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-214">On both dialog boxes, click **Yes**.</span></span> <span data-ttu-id="b086b-215">這會指定您要建立新資料夾，並指定您要複製 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Internet Server API (ISAPI) DLL。</span><span class="sxs-lookup"><span data-stu-id="b086b-215">This specifies that you want to create a new folder and that you want to copy the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Internet Server API (ISAPI) DLL.</span></span> <span data-ttu-id="b086b-216">.</span><span class="sxs-lookup"><span data-stu-id="b086b-216">.</span></span>  
  
7.  <span data-ttu-id="b086b-217">在 **[驗證的存取]** 頁面中：</span><span class="sxs-lookup"><span data-stu-id="b086b-217">On the **Authenticated Access** page:</span></span>  
  
    1.  <span data-ttu-id="b086b-218">確定清除了 **[整合式 Windows 驗證]** 和 **[Windows 網域伺服器的摘要式驗證]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-218">Make sure that **Integrated Windows authentication** and **Digest authentication for Windows domain servers** are cleared.</span></span>  
  
    2.  <span data-ttu-id="b086b-219">選取 **[基本驗證]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-219">Select **Basic Authentication**.</span></span>  
  
    3.  <span data-ttu-id="b086b-220">在 **[預設網域]** 和 **[範圍]** 方塊中，輸入執行 IIS 之電腦的網域。</span><span class="sxs-lookup"><span data-stu-id="b086b-220">In the **Default Domain** and **Realm** boxes, enter the domain of the computer that is running IIS.</span></span>  
  
8.  <span data-ttu-id="b086b-221">在 **[目錄存取]** 頁面中：</span><span class="sxs-lookup"><span data-stu-id="b086b-221">On the **Directory Access** page:</span></span>  
  
    1.  <span data-ttu-id="b086b-222">按一下 **[加入]**，然後在 **[選取使用者或群組]** 對話方塊中，新增訂閱者將用於連接 IIS 的帳戶。</span><span class="sxs-lookup"><span data-stu-id="b086b-222">Click **Add**, and then in the **Select Users or Groups** dialog box, add the accounts under which Subscribers will make connections to IIS.</span></span> <span data-ttu-id="b086b-223">您可以在 [新增訂閱精靈] 的 [Web 伺服器資訊]\*\*\*\* 頁面中指定這些帳戶，或者將其指定為 [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)*@internet_login* 參數的值。</span><span class="sxs-lookup"><span data-stu-id="b086b-223">These are the accounts that you will specify on the **Web Server Information** page of the New Subscription Wizard or as the value for the [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)*@internet_login* parameter.</span></span>  
  
9. <span data-ttu-id="b086b-224">在 **[快照集共用存取]** 頁面中，輸入快照集共用。</span><span class="sxs-lookup"><span data-stu-id="b086b-224">On the **Snapshot Share Access** page, enter the snapshot share.</span></span> <span data-ttu-id="b086b-225">在此共用上設定適當的權限，以便訂閱者可以存取快照集檔案。</span><span class="sxs-lookup"><span data-stu-id="b086b-225">The appropriate permissions are set on this share so that Subscribers can access the snapshot files.</span></span> <span data-ttu-id="b086b-226">如需共用權限的詳細資訊，請參閱[保護快照集資料夾](security/secure-the-snapshot-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="b086b-226">For more information about permissions for the share, see [Secure the Snapshot Folder](security/secure-the-snapshot-folder.md).</span></span>  
  
10. <span data-ttu-id="b086b-227">在 **[正在完成精靈]** 頁面中，按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-227">On the **Completing the Wizard** page, click **Finish**.</span></span>  
  
     <span data-ttu-id="b086b-228">如果出現失敗，例如在嘗試設定執行 IIS 的遠端電腦時出現網路錯誤，則會回復所有完成的動作並取消所有剩餘動作。</span><span class="sxs-lookup"><span data-stu-id="b086b-228">If a failure occurs, such as a network error while trying to configure a remote computer that is running IIS, all completed actions are rolled back and all remaining actions are canceled.</span></span> <span data-ttu-id="b086b-229">如果已完成的動作無法回復，精靈最終頁面中的狀態將顯示 **[成功]** ，並仍然認可完成的動作。</span><span class="sxs-lookup"><span data-stu-id="b086b-229">If a completed action cannot be rolled back, the status in the final page of the wizard displays **Success** and the completed actions remain committed.</span></span>  
  
11. <span data-ttu-id="b086b-230">如果執行 IIS 的電腦執行於 64 位元版本的 Windows 上，則必須將 replisapi.dll 複製到適當的目錄：</span><span class="sxs-lookup"><span data-stu-id="b086b-230">If the computer that is running IIS is running on a 64-bit version of Windows, replisapi.dll must be copied to the appropriate directory:</span></span>  
  
    1.  <span data-ttu-id="b086b-231">按一下 **[開始]** ，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-231">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="b086b-232">在 [**開啟**] 方塊中，輸入 `iisreset` ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-232">In the **Open** box, enter `iisreset`, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="b086b-233">停止並重新啟動 IIS 之後，請將 replisapi.dll 從 [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]COM\replisapi 複製到步驟 6b 中指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="b086b-233">After IIS stops and restarts, copy replisapi.dll from [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]COM\replisapi to the directory that is specified in step 6b.</span></span>  
  
    3.  <span data-ttu-id="b086b-234">按一下 **[開始]** ，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-234">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="b086b-235">在 [**開啟**] 方塊中，輸入 `cmd` ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-235">In the **Open** box, enter `cmd`, and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="b086b-236">於您在步驟 6b 中指定的目錄中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="b086b-236">In the directory that you specified in step 6b, execute the following command:</span></span>  
  
         `regsvr32 replisapi.dll`  
  
## <a name="manually-configuring-the-computer-that-is-running-iis"></a><span data-ttu-id="b086b-237">手動設定執行 IIS 的電腦</span><span class="sxs-lookup"><span data-stu-id="b086b-237">Manually Configuring the Computer That Is Running IIS</span></span>  
 <span data-ttu-id="b086b-238">若要手動設定執行 IIS 的電腦，您必須安裝及設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener，然後為要連接 IIS 的訂閱者設定授權。</span><span class="sxs-lookup"><span data-stu-id="b086b-238">To configure the computer that is running IIS manually, you must install and configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener, and then configure authorization for Subscribers that will connect to IIS.</span></span>  
  
#### <a name="to-install-and-configure-the-sql-server-replication-listener"></a><span data-ttu-id="b086b-239">若要安裝和設定 SQL Server Replication Listener</span><span class="sxs-lookup"><span data-stu-id="b086b-239">To install and configure the SQL Server Replication Listener</span></span>  
  
1.  <span data-ttu-id="b086b-240">在執行 IIS 的電腦上建立檔案目錄來容納 replisapi.dll。</span><span class="sxs-lookup"><span data-stu-id="b086b-240">Create a file directory on the computer that is running IIS to contain replisapi.dll.</span></span> <span data-ttu-id="b086b-241">您可以在任何位置建立該目錄，但建議您在 \<*drive*>:\Inetpub 目錄下建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="b086b-241">You can create the directory wherever you want, but we recommend that you create the directory under the \<*drive*>:\Inetpub directory.</span></span> <span data-ttu-id="b086b-242">例如，您可以建立目錄 \<*drive*>:\Inetpub\SQLReplication\\。</span><span class="sxs-lookup"><span data-stu-id="b086b-242">For example, create the directory \<*drive*>:\Inetpub\SQLReplication\\.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="b086b-243">強烈建議您在 NTFS 檔案系統資料分割 (而非 FAT 檔案系統) 上建立此目錄。</span><span class="sxs-lookup"><span data-stu-id="b086b-243">We strongly recommend that you create this directory on an NTFS file system partition instead of a FAT file system.</span></span> <span data-ttu-id="b086b-244">使用 NTFS 檔案系統時，可使用 NTFS 檔案系統權限，來準確控制可存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複寫的使用者。</span><span class="sxs-lookup"><span data-stu-id="b086b-244">When you use the NTFS file system, you can use NTFS file system permissions to control precisely the users that can access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span>  
  
2.  <span data-ttu-id="b086b-245">將 replisapi.dll 從目錄 [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com\ 複製到步驟 1 中建立的檔案目錄。</span><span class="sxs-lookup"><span data-stu-id="b086b-245">Copy replisapi.dll from the directory [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com\ to the file directory that you created in step 1.</span></span>  
  
3.  <span data-ttu-id="b086b-246">註冊 replisapi.dll：</span><span class="sxs-lookup"><span data-stu-id="b086b-246">Register replisapi.dll:</span></span>  
  
    1.  <span data-ttu-id="b086b-247">按一下 **[開始]** ，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-247">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="b086b-248">在 [**開啟**] 方塊中，輸入 `cmd` ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-248">In the **Open** box, enter `cmd`, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="b086b-249">於您在步驟 1 中建立的目錄中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="b086b-249">In the directory that you created in step 1, execute the following command:</span></span>  
  
         `regsvr32 replisapi.dll`  
  
4.  <span data-ttu-id="b086b-250">為複寫建立新網站，或使用現有的站台。</span><span class="sxs-lookup"><span data-stu-id="b086b-250">Create a new Web site for replication, or use an existing site.</span></span> <span data-ttu-id="b086b-251">網站在同步處理期間可由複寫元件存取。</span><span class="sxs-lookup"><span data-stu-id="b086b-251">The Web site will be accessed by replication components during synchronization.</span></span> <span data-ttu-id="b086b-252">如需有關如何建立網站的詳細資訊，請參閱 IIS 文件集。</span><span class="sxs-lookup"><span data-stu-id="b086b-252">For more information about how to create Web sites, see the IIS documentation.</span></span>  
  
5.  <span data-ttu-id="b086b-253">在 IIS 中建立虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="b086b-253">Create a virtual directory in IIS.</span></span> <span data-ttu-id="b086b-254">虛擬目錄應該在步驟 4 所建立的網站之下建立，且應該對應至步驟 1 所建立的目錄。</span><span class="sxs-lookup"><span data-stu-id="b086b-254">The virtual directory should be created under the Web site that was created in step 4, and should be mapped to the directory that was created in step 1.</span></span> <span data-ttu-id="b086b-255">如需有關如何建立虛擬目錄的詳細資訊，請參閱 IIS 文件集。</span><span class="sxs-lookup"><span data-stu-id="b086b-255">For more information about how to create virtual directories, see the IIS documentation.</span></span> <span data-ttu-id="b086b-256">我們建議您在指派權限給此目錄時愈嚴格愈好。</span><span class="sxs-lookup"><span data-stu-id="b086b-256">We recommend that you be as restrictive as possible when you assign permissions to this directory.</span></span> <span data-ttu-id="b086b-257">您必須選取 **讀取** 和 **執行** 權限，但是可以清除 **執行指令碼**、 **寫入**和 **瀏覽** 權限。</span><span class="sxs-lookup"><span data-stu-id="b086b-257">You must select **Read** and **Execute** permissions, but you can clear **Run scripts**, **Write**, and **Browse** permissions.</span></span>  
  
6.  <span data-ttu-id="b086b-258">設定 IIS，使 replisapi.dll 能夠執行。</span><span class="sxs-lookup"><span data-stu-id="b086b-258">Configure IIS to enable replisapi.dll to execute.</span></span> <span data-ttu-id="b086b-259">步驟 4 中指派的權限對於舊版 IIS 而言已經足夠；不過，IIS 6.0 版要求啟用 Internet Server API (ISAPI) 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="b086b-259">The permissions that are assigned in step 4 are sufficient for earlier versions of IIS; however, IIS version 6.0 requires Internet Server API (ISAPI) extensions to be enabled.</span></span> <span data-ttu-id="b086b-260">如需詳細資訊，請參閱 IIS 6.0 文件集中的＜設定 ISAPI 延伸模組＞和＜啟用和停用動態內容＞。</span><span class="sxs-lookup"><span data-stu-id="b086b-260">For more information, see "Configuring ISAPI Extensions" and "Enabling and Disabling Dynamic Content" in the IIS 6.0 documentation.</span></span>  
  
#### <a name="to-configure-iis-authentication"></a><span data-ttu-id="b086b-261">若要設定 IIS 驗證</span><span class="sxs-lookup"><span data-stu-id="b086b-261">To configure IIS authentication</span></span>  
  
-   <span data-ttu-id="b086b-262">當訂閱者連接到 IIS 時，訂閱者必須經過 IIS 驗證才能存取資源和處理序。</span><span class="sxs-lookup"><span data-stu-id="b086b-262">When Subscribers connect to IIS, IIS must authenticate the Subscribers before they can access resources and processes.</span></span> <span data-ttu-id="b086b-263">IIS 提供三種類型的驗證：匿名、基本和整合式。</span><span class="sxs-lookup"><span data-stu-id="b086b-263">IIS offers three types of authentication: Anonymous, Basic, and Integrated.</span></span> <span data-ttu-id="b086b-264">驗證可套用至整個網站或您建立的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="b086b-264">Authentication can be applied to the whole Web site or to the virtual directory that you created.</span></span>  
  
     <span data-ttu-id="b086b-265">我們建議您搭配 SSL 使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="b086b-265">We recommend that you use Basic Authentication with SSL.</span></span> <span data-ttu-id="b086b-266">不論採用哪一種驗證類型，都需要 SSL。</span><span class="sxs-lookup"><span data-stu-id="b086b-266">SSL is required, regardless of the type of authentication that is used.</span></span> <span data-ttu-id="b086b-267">如需有關如何設定驗證的詳細資訊，請參閱 IIS 文件集。</span><span class="sxs-lookup"><span data-stu-id="b086b-267">For more information about how to configure authentication, see the IIS documentation.</span></span>  
  
## <a name="setting-permissions-for-the-sql-server-replication-listener"></a><span data-ttu-id="b086b-268">設定 SQL Server Replication Listener 的權限</span><span class="sxs-lookup"><span data-stu-id="b086b-268">Setting Permissions for the SQL Server Replication Listener</span></span>  
 <span data-ttu-id="b086b-269">當訂閱者連接到執行 IIS 的電腦時，系統會利用您先前設定 IIS 時所指定的驗證類型來驗證訂閱者。</span><span class="sxs-lookup"><span data-stu-id="b086b-269">When a Subscriber connects to the computer that is running IIS, the Subscriber is authenticated by using the type of authentication that was specified when you configured IIS.</span></span> <span data-ttu-id="b086b-270">IIS 驗證訂閱者之後，IIS 會檢查訂閱者是否獲授權叫用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複寫。</span><span class="sxs-lookup"><span data-stu-id="b086b-270">After IIS authenticates the Subscriber, IIS checks whether the Subscriber is authorized to invoke [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="b086b-271">您可藉由設定 replisapi.dll 的權限來控制可以叫用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複寫的使用者。</span><span class="sxs-lookup"><span data-stu-id="b086b-271">You control the users that can invoke [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication by setting permissions for replisapi.dll.</span></span> <span data-ttu-id="b086b-272">您必須適當地設定權限，才能避免未經授權的使用者存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複寫。</span><span class="sxs-lookup"><span data-stu-id="b086b-272">Properly configuring permissions is necessary to prevent unauthorized access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span>  
  
 <span data-ttu-id="b086b-273">若要設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener 執行時所用帳戶的最小權限，請完成下列程序。</span><span class="sxs-lookup"><span data-stu-id="b086b-273">To configure the minimum permissions for the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener runs, complete the following procedure.</span></span> <span data-ttu-id="b086b-274">此程式中的步驟適用于執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] IIS 6.0。</span><span class="sxs-lookup"><span data-stu-id="b086b-274">The steps in the procedure apply to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] running IIS 6.0.</span></span>  
  
 <span data-ttu-id="b086b-275">除了執行下列步驟之外，請確保所需的登入位於發行集存取清單 (PAL) 中。</span><span class="sxs-lookup"><span data-stu-id="b086b-275">In addition to performing the following steps, make sure that the required logins are in the publication access list (PAL).</span></span> <span data-ttu-id="b086b-276">如需 PAL 的詳細資訊，請參閱[保護發行者](security/secure-the-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="b086b-276">For more information about the PAL, see [Secure the Publisher](security/secure-the-publisher.md).</span></span>  
  
#### <a name="to-configure-the-account-and-permissions"></a><span data-ttu-id="b086b-277">若要設定帳戶和權限</span><span class="sxs-lookup"><span data-stu-id="b086b-277">To configure the account and permissions</span></span>  
  
1.  <span data-ttu-id="b086b-278">在執行 IIS 的電腦上建立本機帳戶：</span><span class="sxs-lookup"><span data-stu-id="b086b-278">Create a local account on the computer that is running IIS:</span></span>  
  
    1.  <span data-ttu-id="b086b-279">以滑鼠右鍵按一下 [**我的電腦**]，然後按一下 [**管理**]。</span><span class="sxs-lookup"><span data-stu-id="b086b-279">Right-click **My Computer**, and then click **Manage**.</span></span>  
  
    2.  <span data-ttu-id="b086b-280">在 **[電腦管理]** 中，展開 **[本機使用者和群組]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-280">In **Computer Management**, expand **Local Users and Groups**.</span></span>  
  
    3.  <span data-ttu-id="b086b-281">以滑鼠右鍵按一下 **[使用者]** ，然後按一下 **[新增使用者]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-281">Right-click **Users**, and then click **New User**.</span></span>  
  
    4.  <span data-ttu-id="b086b-282">輸入使用者名稱與增強式密碼。</span><span class="sxs-lookup"><span data-stu-id="b086b-282">Enter a user name and a strong password.</span></span>  
  
    5.  <span data-ttu-id="b086b-283">按一下 **[建立]** ，然後按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-283">Click **Create**, and then click **Close**.</span></span>  
  
2.  <span data-ttu-id="b086b-284">將帳戶加入 IIS_WPG 群組：</span><span class="sxs-lookup"><span data-stu-id="b086b-284">Add the account to the IIS_WPG group:</span></span>  
  
    1.  <span data-ttu-id="b086b-285">在 **[電腦管理]** 中展開 **[本機使用者和群組]**，然後按一下 **[群組]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-285">In **Computer Management**, expand **Local Users and Groups**, and then click **Groups**.</span></span>  
  
    2.  <span data-ttu-id="b086b-286">以滑鼠右鍵按一下 **[IIS_WPG]**，然後按一下 **[加入群組]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-286">Right-click **IIS_WPG**, and then click **Add to Group**.</span></span>  
  
    3.  <span data-ttu-id="b086b-287">在 **[IIS_WPG 屬性]** 對話方塊中，按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-287">In the **IIS_WPG Properties** dialog box, click **Add**.</span></span>  
  
    4.  <span data-ttu-id="b086b-288">在 **[選取使用者、電腦或群組]** 對話方塊中，加入在步驟 1 建立的帳戶。</span><span class="sxs-lookup"><span data-stu-id="b086b-288">In the **Select Users, Computers, or Groups** dialog box, add the account created in step 1.</span></span>  
  
    5.  <span data-ttu-id="b086b-289">確定 **[從這個位置]** 欄位中的名稱是本機電腦的名稱，而不是網域。</span><span class="sxs-lookup"><span data-stu-id="b086b-289">Make sure that the name in the **From this location** field is the name of the local computer instead of a domain.</span></span> <span data-ttu-id="b086b-290">如果該名稱不是本機電腦，請按一下 **[位置]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-290">If the name is not a local computer, click **Locations**.</span></span> <span data-ttu-id="b086b-291">在 **[位置]** 對話方塊中，選取本機電腦，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-291">In the **Locations** dialog box, elect the local computer, and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="b086b-292">在 **[選取使用者]** 對話方塊和 **[IIS_WPG 屬性]** 對話方塊中，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-292">In the **Select Users** dialog box and the **IIS_WPG Properties** dialog box, click **OK**.</span></span>  
  
3.  <span data-ttu-id="b086b-293">將包含 replisapi.dll 之資料夾的最小權限授與帳戶：</span><span class="sxs-lookup"><span data-stu-id="b086b-293">Grant the minimum permissions on the folder that contains replisapi.dll to the account :</span></span>  
  
    1.  <span data-ttu-id="b086b-294">找出您先前為 replisapi.dll 建立的資料夾，以滑鼠右鍵按一下該資料夾，然後按一下 **[共用和安全性]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-294">Locate the folder that you created for replisapi.dll, right-click the folder, and then click **Sharing and Security**.</span></span>  
  
    2.  <span data-ttu-id="b086b-295">在 [安全性]\*\*\*\* 索引標籤上，按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b086b-295">On the **Security** tab, click **Add**.</span></span>  
  
    3.  <span data-ttu-id="b086b-296">在 **[選取使用者、電腦或群組]** 對話方塊中，加入在步驟 1 建立的帳戶。</span><span class="sxs-lookup"><span data-stu-id="b086b-296">In the **Select Users, Computers, or Groups** dialog box, add the account that you created in step 1.</span></span>  
  
    4.  <span data-ttu-id="b086b-297">確定 **[從這個位置]** 欄位中的名稱是本機電腦的名稱，而不是網域。</span><span class="sxs-lookup"><span data-stu-id="b086b-297">Make sure that the name in the **From this location** field is the name of the local computer instead of a domain.</span></span> <span data-ttu-id="b086b-298">如果該名稱不是本機電腦，請按一下 **[位置]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-298">If the name is not a local computer, click **Locations**.</span></span> <span data-ttu-id="b086b-299">在 **[位置]** 對話方塊中，選取本機電腦，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-299">In the **Locations** dialog box, select the local computer, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="b086b-300">確認只將**讀取**、**讀取與執行**和**列出資料夾內容**權限授與這個帳戶。</span><span class="sxs-lookup"><span data-stu-id="b086b-300">Make sure that the account is granted only **Read**, **Read & Execute**, and **List Folder Contents** permissions.</span></span>  
  
    6.  <span data-ttu-id="b086b-301">選取不需要存取目錄的使用者或群組，然後按一下 **[移除]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-301">Select any users or groups that do not require access to the directory, and then click **Remove**.</span></span>  
  
    7.  <span data-ttu-id="b086b-302">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="b086b-302">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="b086b-303">在 **[Internet Information Services (IIS) 管理員]** 中建立應用程式集區：</span><span class="sxs-lookup"><span data-stu-id="b086b-303">Create an application pool in **Internet Information Services (IIS) Manager**:</span></span>  
  
    1.  <span data-ttu-id="b086b-304">按一下 **[開始]** ，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-304">Click **Start**, and then click **Run**.</span></span>  
  
    2.  <span data-ttu-id="b086b-305">在 [**開啟**] 方塊中，輸入 `inetmgr` ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-305">In the **Open** box, type `inetmgr`, and then click **OK**.</span></span>  
  
    3.  <span data-ttu-id="b086b-306">在 **[Internet Information Services (IIS) 管理員]** 中，展開 **[本機電腦]** 節點。</span><span class="sxs-lookup"><span data-stu-id="b086b-306">In **Internet Information Services (IIS) Manager**, expand the **local computer** node.</span></span>  
  
    4.  <span data-ttu-id="b086b-307">以滑鼠右鍵按一下 **[應用程式集區]**，指向 **[新增]** ，然後按一下 **[應用程式集區]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-307">Right-click **Application Pools**, point to **New** and then click **Application Pool**.</span></span>  
  
    5.  <span data-ttu-id="b086b-308">在 **[應用程式集區身分識別]** 欄位中輸入集區的名稱，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-308">Enter a name for the pool in the **Application pool ID** field, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="b086b-309">將帳戶與應用程式集區相關聯：</span><span class="sxs-lookup"><span data-stu-id="b086b-309">Associate the account with the application pool:</span></span>  
  
    1.  <span data-ttu-id="b086b-310">在 **[Internet Information Services (IIS) 管理員]** 中展開 **[本機電腦]** 節點，然後展開 **[應用程式集區]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-310">In **Internet Information Services (IIS) Manager**, expand the **local computer** node, and then expand **Application Pools**.</span></span>  
  
    2.  <span data-ttu-id="b086b-311">以滑鼠右鍵按一下您先前建立的應用程式集區，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-311">Right-click the application pool that you created, and then click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="b086b-312">在 [ \*\* \<ApplicationPoolName> 屬性**] 對話方塊的 [**識別**] 索引標籤上，按一下 [**可\*\*設定]。</span><span class="sxs-lookup"><span data-stu-id="b086b-312">In the **\<ApplicationPoolName> Properties** dialog box, on the **Identity** tab, click **Configurable**.</span></span>  
  
    4.  <span data-ttu-id="b086b-313">在 **[使用者名稱]** 和 **[密碼]** 欄位中，輸入步驟 1 中建立的帳戶和密碼。</span><span class="sxs-lookup"><span data-stu-id="b086b-313">In the **User name** and **password** fields, enter the account and password that were created in step 1.</span></span>  
  
    5.  <span data-ttu-id="b086b-314">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="b086b-314">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="b086b-315">將應用程式集區與 Web 同步處理所使用的虛擬目錄相關聯：</span><span class="sxs-lookup"><span data-stu-id="b086b-315">Associate the application pool with the virtual directory that is used for Web synchronization:</span></span>  
  
    1.  <span data-ttu-id="b086b-316">在 **[Internet Information Services (IIS) 管理員]** 中展開 **[本機電腦]** 節點，然後展開 **[網站]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-316">In **Internet Information Services (IIS) Manager**, expand the **local computer** node, and then expand **Web Sites**.</span></span>  
  
    2.  <span data-ttu-id="b086b-317">展開您用於 Web 同步處理的網站，以滑鼠右鍵按一下您為 Web 同步處理建立的虛擬目錄，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-317">Expand the Web site that you are using for Web synchronization, right-click the virtual directory that you created for Web synchronization, and then click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="b086b-318">在 [ \*\* \<VirtualDirectoryName> 屬性**] 對話方塊的 [**虛擬目錄**] 索引標籤上，從 [**應用程式集\*\*區] 下拉式清單中，選取在步驟5中建立的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="b086b-318">On the **Virtual Directory** tab of the **\<VirtualDirectoryName> Properties** dialog box, from the **Application pool** drop-down list, select the application pool that was created in step 5.</span></span>  
  
    4.  <span data-ttu-id="b086b-319">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="b086b-319">Click **OK**.</span></span>  
  
## <a name="testing-the-connection-to-replisapidll"></a><span data-ttu-id="b086b-320">測試與 replisapi.dll 的連接</span><span class="sxs-lookup"><span data-stu-id="b086b-320">Testing the Connection to replisapi.dll</span></span>  
 <span data-ttu-id="b086b-321">在診斷模式下執行 Web 同步處理，以測試執行 IIS 之電腦的連接，並確定安全通訊端層 (SSL) 憑證已正確安裝。</span><span class="sxs-lookup"><span data-stu-id="b086b-321">Run Web synchronization in diagnostic mode to test the connection to the computer that is running IIS and to make sure that the Secure Sockets Layer (SSL) certificate is properly installed.</span></span> <span data-ttu-id="b086b-322">若要在診斷模式下執行 Web 同步處理，您必須是執行 IIS 之電腦上的管理員。</span><span class="sxs-lookup"><span data-stu-id="b086b-322">To run Web synchronization in diagnostic mode, you must be an administrator on the computer running IIS.</span></span>  
  
#### <a name="to-test-the-connection-to-replisapidll"></a><span data-ttu-id="b086b-323">若要測試與 replisapi.dll 的連接</span><span class="sxs-lookup"><span data-stu-id="b086b-323">To test the connection to replisapi.dll</span></span>  
  
1.  <span data-ttu-id="b086b-324">確定訂閱者端的區域網路 (LAN) 設定正確：</span><span class="sxs-lookup"><span data-stu-id="b086b-324">Make sure that local area network (LAN) settings at the Subscriber are correct:</span></span>  
  
    1.  <span data-ttu-id="b086b-325">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer 的 **[工具]** 功能表中，按一下 **[網際網路選項]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-325">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer, on the **Tools** menu, click **Internet Options**.</span></span>  
  
    2.  <span data-ttu-id="b086b-326">在 **[連接]** 索引標籤中，按一下 **[LAN 設定]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-326">On the **Connections** tab, click **LAN Settings**.</span></span>  
  
    3.  <span data-ttu-id="b086b-327">如果 LAN 上未使用 Proxy 伺服器，請清除 **[自動偵測設定]** 與 **[在 LAN 中使用 Proxy 伺服器]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-327">If a proxy server is not used on the LAN, clear **Automatically Detect Settings** and **Use a proxy server for your LAN**.</span></span>  
  
    4.  <span data-ttu-id="b086b-328">如果使用 Proxy 伺服器，請選取 **[在 LAN 中使用 Proxy 伺服器]** 和 **[本機位址不使用 Proxy 伺服器]**。</span><span class="sxs-lookup"><span data-stu-id="b086b-328">If a proxy server is used, select **Use a proxy server for your LAN** and **Bypass proxy server for local addresses**.</span></span>  
  
    5.  <span data-ttu-id="b086b-329">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="b086b-329">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="b086b-330">在訂閱者端的 Internet Explorer 中，將 `?diag` 附加至 replisapi.dll 的位址，以便在診斷模式下連接伺服器。</span><span class="sxs-lookup"><span data-stu-id="b086b-330">At the Subscriber, in Internet Explorer, connect to the server in diagnostic mode by appending `?diag` to the address for the replisapi.dll.</span></span> <span data-ttu-id="b086b-331">例如： `https://server.domain.com/directory/replisapi.dll?diag` 。</span><span class="sxs-lookup"><span data-stu-id="b086b-331">For example: `https://server.domain.com/directory/replisapi.dll?diag`.</span></span>  
  
3.  <span data-ttu-id="b086b-332">如果 Windows 作業系統無法辨識您先前為 IIS 指定的憑證，則會出現 **[安全性警示]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b086b-332">If the certificate that you specified for IIS is not recognized by the Windows operating system, the **Security Alert** dialog box appears.</span></span> <span data-ttu-id="b086b-333">發生此警示的可能是因為該憑證是測試憑證，或者該憑證是由 Windows 無法辨識的憑證授權單位 (CA) 所發行。</span><span class="sxs-lookup"><span data-stu-id="b086b-333">This alert might occur because the certificate is a test certificate or the certificate was issued by a certification authority (CA) that Windows does not recognize.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b086b-334">如果未出現此對話方塊，請確定您要存取之伺服器的憑證已做為信任憑證加入訂閱者端的憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="b086b-334">If this dialog box does not appear, make sure that the certificate for the server that you are accessing has been added to the certificate store at the Subscriber as a trusted certificate.</span></span> <span data-ttu-id="b086b-335">如需有關匯入憑證的詳細資訊，請參閱 IIS 文件集。</span><span class="sxs-lookup"><span data-stu-id="b086b-335">For more information about exporting certificates, see the IIS documentation.</span></span>  
  
    1.  <span data-ttu-id="b086b-336">在 **[安全性警示]** 對話方塊中，按一下 **[檢視憑證]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-336">In the **Security Alert** dialog box, click **View Certificate**.</span></span>  
  
    2.  <span data-ttu-id="b086b-337">在 **[憑證]** 對話方塊的 **[一般]** 索引標籤上，按一下 **[安裝憑證]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-337">In the **Certificate** dialog box, on the **General** tab, click **Install Certificate**.</span></span>  
  
    3.  <span data-ttu-id="b086b-338">完成「憑證匯入精靈」，以接受預設值。</span><span class="sxs-lookup"><span data-stu-id="b086b-338">Complete the Certificate Import Wizard, accepting the defaults.</span></span>  
  
    4.  <span data-ttu-id="b086b-339">在 **[安全性警告]** 對話方塊中，按一下 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-339">In the **Security Warning** dialog box, click **Yes**.</span></span>  
  
    5.  <span data-ttu-id="b086b-340">在「憑證匯入精靈」確認對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-340">In the Certificate Import Wizard confirmation dialog box, click **OK**.</span></span>  
  
    6.  <span data-ttu-id="b086b-341">關閉 **[憑證]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b086b-341">Close the **Certificate** dialog box.</span></span>  
  
    7.  <span data-ttu-id="b086b-342">在 **[安全性警示]** 對話方塊中，按一下 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-342">In the **Security Alert** dialog box, click **Yes**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b086b-343">將為使用者安裝憑證。</span><span class="sxs-lookup"><span data-stu-id="b086b-343">Certificates are installed for users.</span></span> <span data-ttu-id="b086b-344">這項處理序必須針對將與 IIS 同步處理的每位使用者執行。</span><span class="sxs-lookup"><span data-stu-id="b086b-344">This process must be performed for each user that will synchronize with IIS.</span></span>  
  
4.  <span data-ttu-id="b086b-345">在 [連接到 \<ServerName>] 對話方塊中，指定合併代理程式要用來連線到 IIS 的登入和密碼。</span><span class="sxs-lookup"><span data-stu-id="b086b-345">In the **Connect to \<ServerName>** dialog box, specify the login and password that the Merge Agent will use to connect to IIS.</span></span> <span data-ttu-id="b086b-346">也可以在「新增訂閱精靈」中指定這些認證。</span><span class="sxs-lookup"><span data-stu-id="b086b-346">These credentials will also be specified in the New Subscription Wizard.</span></span>  
  
5.  <span data-ttu-id="b086b-347">在稱為 **[SQL Websync 診斷資訊]** 的 Internet Explorer 視窗中，確認頁面中每個 **[狀態]** 資料行中的值都是 **[SUCCESS]** 。</span><span class="sxs-lookup"><span data-stu-id="b086b-347">In the Internet Explorer window called **SQL Websync diagnostic information**, verify that the value in each **Status** column on the page is **SUCCESS**.</span></span>  
  
6.  <span data-ttu-id="b086b-348">確定憑證已正確安裝於訂閱者端：</span><span class="sxs-lookup"><span data-stu-id="b086b-348">Make sure that the certificate is installed correctly on the Subscriber:</span></span>  
  
    1.  <span data-ttu-id="b086b-349">關閉 Internet Explorer，然後再重新開啟。</span><span class="sxs-lookup"><span data-stu-id="b086b-349">Close and then reopen Internet Explorer.</span></span>  
  
    2.  <span data-ttu-id="b086b-350">在診斷模式下連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="b086b-350">Connect to the server in diagnostic mode.</span></span> <span data-ttu-id="b086b-351">如果憑證已正確安裝，就不會出現 **[安全性警示]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b086b-351">If the certificate is installed properly, the **Security Alert** dialog box will not appear.</span></span> <span data-ttu-id="b086b-352">如果出現此對話方塊，合併代理程式將在嘗試連接到執行 IIS 的電腦時失敗。</span><span class="sxs-lookup"><span data-stu-id="b086b-352">If the dialog box appears, the Merge Agent will fail when it tries to connect to the computer that is running IIS.</span></span> <span data-ttu-id="b086b-353">您必須確定要存取的伺服器憑證已做為信任憑證加入訂閱者端的憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="b086b-353">You must make sure that the certificate for the server that you are accessing has been added to the certificate store at the Subscriber as a trusted certificate.</span></span> <span data-ttu-id="b086b-354">如需有關匯入憑證的詳細資訊，請參閱 IIS 文件集。</span><span class="sxs-lookup"><span data-stu-id="b086b-354">For more information about exporting certificates, see the IIS documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b086b-355">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b086b-355">See Also</span></span>  
 [<span data-ttu-id="b086b-356">設定 Web 同步處理</span><span class="sxs-lookup"><span data-stu-id="b086b-356">Configure Web Synchronization</span></span>](configure-web-synchronization.md)  
  
  
