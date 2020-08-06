---
title: 啟用資料庫引擎 (SQL Server 組態管理員) 的加密連接 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], encrypted
- SSL [SQL Server]
- Secure Sockets Layer (SSL)
- encryption [SQL Server], connections
- cryptography [SQL Server], connections
- certificates [SQL Server], installing
- requesting encrypted connections
- installing certificates
- security [SQL Server], encryption
ms.assetid: e1e55519-97ec-4404-81ef-881da3b42006
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e1653df929e3f8bc67158a0685ce07b8ba65de6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708602"
---
# <a name="enable-encrypted-connections-to-the-database-engine-sql-server-configuration-manager"></a><span data-ttu-id="22a7a-102">啟用 Database Engine 的加密連接 (SQL Server 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="22a7a-102">Enable Encrypted Connections to the Database Engine (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="22a7a-103">此主題描述如何使用 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 組態管理員指定 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的憑證，以啟用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的加密連接。</span><span class="sxs-lookup"><span data-stu-id="22a7a-103">This topic describes how to enable encrypted connections for an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] by specifying a certificate for the [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="22a7a-104">伺服器電腦必須提供憑證，且用戶端機器必須設定為信任該憑證的根授權單位。</span><span class="sxs-lookup"><span data-stu-id="22a7a-104">The server computer must have a certificate provisioned, and the client machine must be set up to trust the certificate's root authority.</span></span> <span data-ttu-id="22a7a-105">提供是安裝憑證的處理序，方法是將它匯入 Windows。</span><span class="sxs-lookup"><span data-stu-id="22a7a-105">Provisioning is the process of installing a certificate by importing it into Windows.</span></span>  
  
 <span data-ttu-id="22a7a-106">您必須針對 **伺服器驗證**發出此憑證。</span><span class="sxs-lookup"><span data-stu-id="22a7a-106">The certificate must be issued for **Server Authentication**.</span></span> <span data-ttu-id="22a7a-107">憑證的名稱必須是電腦的完整網域名稱 (FQDN)。</span><span class="sxs-lookup"><span data-stu-id="22a7a-107">The name of the certificate must be the fully qualified domain name (FQDN) of the computer.</span></span>  
  
 <span data-ttu-id="22a7a-108">電腦上之使用者的憑證會儲存在本機中。</span><span class="sxs-lookup"><span data-stu-id="22a7a-108">Certificates are stored locally for the users on the computer.</span></span> <span data-ttu-id="22a7a-109">若要安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]所使用的憑證，則除非服務是以 LocalSystem、NetworkService 或 LocalService 執行，否則您必須使用與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務相同的使用者帳戶來執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員，而在此情況下，您可以使用管理帳戶。</span><span class="sxs-lookup"><span data-stu-id="22a7a-109">To install a certificate for use by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must be running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager under the same user account as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service unless the service is running as LocalSystem, NetworkService, or LocalService, in which case you may use an administrative account.</span></span>  
  
 <span data-ttu-id="22a7a-110">用戶端必須可確認伺服器所使用之憑證的擁有權。</span><span class="sxs-lookup"><span data-stu-id="22a7a-110">The client must be able to verify the ownership of the certificate used by the server.</span></span> <span data-ttu-id="22a7a-111">如果用戶端具有已簽署伺服器憑證之憑證授權單位的公開金鑰憑證，則不需要進一步進行組態設定。</span><span class="sxs-lookup"><span data-stu-id="22a7a-111">If the client has the public key certificate of the certification authority that signed the server certificate, no further configuration is necessary.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="22a7a-112">Windows 包含許多憑證授權單位的公開金鑰憑證。</span><span class="sxs-lookup"><span data-stu-id="22a7a-112">Windows includes the public key certificates of many certification authorities.</span></span> <span data-ttu-id="22a7a-113">如果伺服器憑證是由用戶端沒有公開金鑰憑證的公開或私人憑證授權單位所簽署，則您必須安裝已簽署伺服器憑證之憑證授權單位的公開金鑰憑證。</span><span class="sxs-lookup"><span data-stu-id="22a7a-113">If the server certificate was signed by a public or private certification authority for which the client does not have the public key certificate, you must install the public key certificate of the certification authority that signed the server certificate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22a7a-114">若要在容錯移轉叢集中使用加密功能，請務必在容錯移轉叢集中的所有節點上，對於虛擬伺服器使用完整的 DNS 名稱來安裝伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="22a7a-114">To use encryption with a failover cluster, you must install the server certificate with the fully qualified DNS name of the virtual server on all nodes in the failover cluster.</span></span> <span data-ttu-id="22a7a-115">例如，如果您有兩個節點的叢集，且節點名為 test1. *\<your company>* 。com 和 *\<your company>* test2。com，而且您有一個名為 virtsql 的虛擬伺服器，您必須安裝 virtsql 的 *\<your company>* 憑證。這兩個節點上的 com。</span><span class="sxs-lookup"><span data-stu-id="22a7a-115">For example, if you have a two-node cluster, with nodes named test1.*\<your company>*.com and test2.*\<your company>*.com, and you have a virtual server named virtsql, you need to install a certificate for virtsql.*\<your company>*.com on both nodes.</span></span> <span data-ttu-id="22a7a-116">您可以將 [[ForceEncryption]] **[ForceEncryption]** 選項的值設為 [是] **[是]**。</span><span class="sxs-lookup"><span data-stu-id="22a7a-116">You can set the value of the **ForceEncryption**option to **Yes**.</span></span>  
  
 <span data-ttu-id="22a7a-117">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="22a7a-117">**In This Topic**</span></span>  
  
-   <span data-ttu-id="22a7a-118">**若要啟用加密連接：**</span><span class="sxs-lookup"><span data-stu-id="22a7a-118">**To enable encrypted connections:**</span></span>  
  
     [<span data-ttu-id="22a7a-119">在伺服器上提供 (安裝) 憑證</span><span class="sxs-lookup"><span data-stu-id="22a7a-119">Provision (install) a certificate on the server</span></span>](#Provision)  
  
     [<span data-ttu-id="22a7a-120">匯出伺服器憑證</span><span class="sxs-lookup"><span data-stu-id="22a7a-120">Export the server certificate</span></span>](#Export)  
  
     [<span data-ttu-id="22a7a-121">設定伺服器接受加密連接</span><span class="sxs-lookup"><span data-stu-id="22a7a-121">Configure the server to accept encrypted connections</span></span>](#ConfigureServerConnections)  
  
     [<span data-ttu-id="22a7a-122">設定用戶端要求加密的連接</span><span class="sxs-lookup"><span data-stu-id="22a7a-122">Configure the client to request encrypted connections</span></span>](#ConfigureClientConnections)  
  
     [<span data-ttu-id="22a7a-123">從 SQL Server Management Studio 加密連接</span><span class="sxs-lookup"><span data-stu-id="22a7a-123">Encrypt a connection from SQL Server Management Studio</span></span>](#EncryptConnection)  
  
##  <a name="SSMSProcedure"></a>  
  
###  <a name="to-provision-install-a-certificate-on-the-server"></a><a name="Provision"></a> <span data-ttu-id="22a7a-124">若要在伺服器上提供 (安裝) 憑證</span><span class="sxs-lookup"><span data-stu-id="22a7a-124">To provision (install) a certificate on the server</span></span>  
  
1.  <span data-ttu-id="22a7a-125">在 [**開始**] 功能表上，按一下 [**執行**]，然後在 [**開啟**] 方塊中輸入， `MMC` 然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="22a7a-125">On the **Start** menu, click **Run**, and in the **Open** box, type `MMC` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="22a7a-126">在 MMC 主控台的 [檔案] 功能表上，按一下 [新增/移除嵌入式管理單元]。</span><span class="sxs-lookup"><span data-stu-id="22a7a-126">In the MMC console, on the **File** menu, click **Add/Remove Snap-in**.</span></span>  
  
3.  <span data-ttu-id="22a7a-127">在 [新增/移除嵌入式管理單元] 對話方塊中，按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="22a7a-127">In the **Add/Remove Snap-in** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="22a7a-128">在 [新增獨立嵌入式管理單元] 對話方塊中，按一下 [憑證]，然後按 [新增]。</span><span class="sxs-lookup"><span data-stu-id="22a7a-128">In the **Add Standalone Snap-in** dialog box, click **Certificates**, click **Add**.</span></span>  
  
5.  <span data-ttu-id="22a7a-129">在 [憑證嵌入式管理單元] 對話方塊中，按一下 [電腦帳戶]，然後按 [完成]。</span><span class="sxs-lookup"><span data-stu-id="22a7a-129">In the **Certificates snap-in** dialog box, click **Computer account**, and then click **Finish**.</span></span>  
  
6.  <span data-ttu-id="22a7a-130">在 [新增獨立嵌入式管理單元] 對話方塊中，按一下 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="22a7a-130">In the **Add Standalone Snap-in** dialog box, click **Close.**</span></span>  
  
7.  <span data-ttu-id="22a7a-131">在 [新增/移除嵌入式管理單元] 對話方塊中，按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="22a7a-131">In the **Add/Remove Snap-in** dialog box, click **OK**.</span></span>  
  
8.  <span data-ttu-id="22a7a-132">在 [憑證] 嵌入式管理單元中，展開 [憑證] 後再展開 [個人]，然後以滑鼠右鍵按一下 [憑證]，接著指向 [所有工作]，再按 [匯入]。</span><span class="sxs-lookup"><span data-stu-id="22a7a-132">In the **Certificates** snap-in, expand **Certificates**, expand **Personal**, and then right-click **Certificates**, point to **All Tasks**, and then click **Import**.</span></span>  
  
9. <span data-ttu-id="22a7a-133">完成 **[憑證匯入精靈]** 以加入憑證至電腦中，然後關閉 MMC 主控台。</span><span class="sxs-lookup"><span data-stu-id="22a7a-133">Complete the **Certificate Import Wizard**, to add a certificate to the computer, and close the MMC console.</span></span> <span data-ttu-id="22a7a-134">如需新增憑證至電腦的詳細資訊，請參閱 Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="22a7a-134">For more information about adding a certificate to a computer, see your Windows documentation.</span></span>  
  
###  <a name="to-export-the-server-certificate"></a><a name="Export"></a><span data-ttu-id="22a7a-135">若要匯出伺服器憑證</span><span class="sxs-lookup"><span data-stu-id="22a7a-135">To export the server certificate</span></span>  
  
1.  <span data-ttu-id="22a7a-136">從 [憑證] 嵌入式管理單元的 [憑證] / [個人] 資料夾中找到憑證，以滑鼠右鍵按一下 [憑證]，並指向 [所有工作]，然後按一下 [匯出]。</span><span class="sxs-lookup"><span data-stu-id="22a7a-136">From the **Certificates** snap-in, locate the certificate in the **Certificates** / **Personal** folder, right-click the **Certificate**, point to **All Tasks**, and then click **Export**.</span></span>  
  
2.  <span data-ttu-id="22a7a-137">完成 **[憑證匯出精靈]** ，並將憑證檔儲存在方便取得的位置。</span><span class="sxs-lookup"><span data-stu-id="22a7a-137">Complete the **Certificate Export Wizard**, storing the certificate file in a convenient location.</span></span>  
  
###  <a name="to-configure-the-server-to-accept-encrypted-connections"></a><a name="ConfigureServerConnections"></a> <span data-ttu-id="22a7a-138">若要設定伺服器接受加密的連接</span><span class="sxs-lookup"><span data-stu-id="22a7a-138">To configure the server to accept encrypted connections</span></span>  
  
1.  <span data-ttu-id="22a7a-139">在 [SQL Server 組態管理員] 中，展開 [SQL Server 網路組態]，並以滑鼠右鍵按一下 [ _\<server instance>_ 的通訊協定]，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="22a7a-139">In **SQL Server Configuration Manager**, expand **SQL Server Network Configuration**, right-click **Protocols for** _\<server instance>_, and then select**Properties**.</span></span>  
  
2.  <span data-ttu-id="22a7a-140">在 [屬性的**通訊協定** _\<instance name>_ **Properties** ] 對話方塊的 [**憑證**] 索引標籤上，從 [**憑證**] 方塊的下拉式方塊中選取所需的憑證，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="22a7a-140">In the **Protocols for**_\<instance name>_ **Properties** dialog box, on the **Certificate** tab, select the desired certificate from the drop down for the **Certificate** box, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="22a7a-141">在 **[旗標]** 索引標籤的 **[ForceEncryption]** 方塊中選取 **[是]** ，然後按一下 **[確定]** 以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="22a7a-141">On the **Flags** tab, in the **ForceEncryption** box, select **Yes**, and then click **OK** to close the dialog box.</span></span>  
  
4.  <span data-ttu-id="22a7a-142">重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="22a7a-142">Restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
###  <a name="to-configure-the-client-to-request-encrypted-connections"></a><a name="ConfigureClientConnections"></a><span data-ttu-id="22a7a-143">設定用戶端要求加密的連接</span><span class="sxs-lookup"><span data-stu-id="22a7a-143">To configure the client to request encrypted connections</span></span>  
  
1.  <span data-ttu-id="22a7a-144">將原始憑證或匯出的憑證檔複製到用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="22a7a-144">Copy either the original certificate or the exported certificate file to the client computer.</span></span>  
  
2.  <span data-ttu-id="22a7a-145">在用戶端電腦上，使用 [憑證] 嵌入式管理單元安裝根憑證或匯出的憑證檔。</span><span class="sxs-lookup"><span data-stu-id="22a7a-145">On the client computer, use the **Certificates** snap-in to install either the root certificate or the exported certificate file.</span></span>  
  
3.  <span data-ttu-id="22a7a-146">在主控台窗格中，以滑鼠右鍵按一下 [SQL Server Native Client 組態]\*\*\*\*，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22a7a-146">In the console pane, right-click **SQL Server Native Client Configuration**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="22a7a-147">在 **[旗標]** 頁面的 **[強制通訊協定加密]** 方塊中，按一下 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="22a7a-147">On the **Flags** page, in the **Force protocol encryption** box, click **Yes**.</span></span>  
  
###  <a name="to-encrypt-a-connection-from-sql-server-management-studio"></a><a name="EncryptConnection"></a><span data-ttu-id="22a7a-148">若要從 SQL Server Management Studio 加密連接</span><span class="sxs-lookup"><span data-stu-id="22a7a-148">To encrypt a connection from SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="22a7a-149">在 [物件總管] 工具列上，按一下 **[連接]** ，再按一下 **[Database Engine]** 。</span><span class="sxs-lookup"><span data-stu-id="22a7a-149">On the Object Explorer toolbar, click **Connect**, and then click **Database Engine**.</span></span>  
  
2.  <span data-ttu-id="22a7a-150">在 **[連接到伺服器]** 對話方塊中，完成連接資訊，然後按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="22a7a-150">In the **Connect to Server** dialog box, complete the connection information, and then click **Options**.</span></span>  
  
3.  <span data-ttu-id="22a7a-151">在 **[連接屬性]** 索引標籤上，按一下 **[加密連接]** 。</span><span class="sxs-lookup"><span data-stu-id="22a7a-151">On the **Connection Properties** tab, click **Encrypt connection**.</span></span>  
  
  
