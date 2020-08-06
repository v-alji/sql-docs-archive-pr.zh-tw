---
title: 連接至遠端 Integration Services 伺服器 (SSIS 服務) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- service [Integration Services], remote instance
- Integration Services service, connecting
- Integration Services service, remote instance
- service [Integration Services], connecting
ms.assetid: 9487aff1-44d8-42c1-8176-bb9891d4632d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 03c9c4f1c94e4599c2c14f407996431dabd493dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706641"
---
# <a name="connect-to-a-remote-integration-services-server-ssis-service"></a><span data-ttu-id="91a1b-102">連接到遠端 Integration Services 伺服器 (SSIS 服務)</span><span class="sxs-lookup"><span data-stu-id="91a1b-102">Connect to a Remote Integration Services Server (SSIS Service)</span></span>
    
> [!IMPORTANT] 
> <span data-ttu-id="91a1b-103">本主題會討論 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務，即用於管理 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="91a1b-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="91a1b-104">支援此服務能與舊版 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]回溯相容。</span><span class="sxs-lookup"><span data-stu-id="91a1b-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="91a1b-105">從 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]開始，您可以管理 Integration Services 伺服器上的物件，例如封裝。</span><span class="sxs-lookup"><span data-stu-id="91a1b-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="91a1b-106">從 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 或其他管理應用程式連接到遠端伺服器上的 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 執行個體時，應用程式的使用者必須具備一組特定的伺服器權限。</span><span class="sxs-lookup"><span data-stu-id="91a1b-106">Connecting to an instance of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] on a remote server, from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or another management application, requires a specific set of rights on the server for the users of the application.</span></span>  
  
> [!IMPORTANT] 
> <span data-ttu-id="91a1b-107">若要管理儲存在遠端伺服器上的封裝，您不必連接到該遠端伺服器上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務執行個體，</span><span class="sxs-lookup"><span data-stu-id="91a1b-107">To manage packages that are stored on a remote server, you do not have to connect to the instance of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service on that remote server.</span></span> <span data-ttu-id="91a1b-108">而是要編輯 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務的組態檔，好讓 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 顯示儲存在遠端伺服器上的封裝。</span><span class="sxs-lookup"><span data-stu-id="91a1b-108">Instead, edit the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service so that [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] displays the packages that are stored on the remote server.</span></span> <span data-ttu-id="91a1b-109">如需詳細資訊，請參閱 [設定 Integration Services 服務 &#40;SSIS 服務&#41;](service/integration-services-service-ssis-service.md)回溯相容。</span><span class="sxs-lookup"><span data-stu-id="91a1b-109">For more information, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md).</span></span>  
  
## <a name="connecting-to-integration-services-on-a-remote-server"></a><span data-ttu-id="91a1b-110">連接到遠端伺服器上的 Integration Services</span><span class="sxs-lookup"><span data-stu-id="91a1b-110">Connecting to Integration Services on a Remote Server</span></span>  
  
#### <a name="to-connect-to-integration-services-on-a-remote-server"></a><span data-ttu-id="91a1b-111">連接到遠端伺服器上的 Integration Services</span><span class="sxs-lookup"><span data-stu-id="91a1b-111">To connect to Integration Services on a Remote Server</span></span>  
  
1.  <span data-ttu-id="91a1b-112">開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="91a1b-112">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="91a1b-113">依序選取 [檔案]\*\*\*\*、[連接物件總管]\*\*\*\*，以顯示 [連接到伺服器]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="91a1b-113">Select **File**, **Connect Object Explorer** to display the **Connect to Server** dialog box.</span></span>  
  
3.  <span data-ttu-id="91a1b-114">選取 [伺服器類型]\*\*\*\* 清單中的 [Integration Services]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="91a1b-114">Select **Integration Services** in the **Server type** list.</span></span>  
  
4.  <span data-ttu-id="91a1b-115">在 [伺服器名稱]\*\*\*\* 文字方塊中鍵入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="91a1b-115">Type the name of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server in the **Server name** text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="91a1b-116">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務不是執行個體特定的。</span><span class="sxs-lookup"><span data-stu-id="91a1b-116">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is not instance-specific.</span></span> <span data-ttu-id="91a1b-117">您可以使用 Integration Services 服務執行所在的電腦名稱來連接此服務。</span><span class="sxs-lookup"><span data-stu-id="91a1b-117">You connect to the service by using the name of the computer on which the Integration Services service is running.</span></span>  
  
5.  <span data-ttu-id="91a1b-118">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="91a1b-118">Click **Connect**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91a1b-119">[瀏覽伺服器]\*\*\*\* 對話方塊不會顯示 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的遠端執行個體。</span><span class="sxs-lookup"><span data-stu-id="91a1b-119">The **Browse for Servers** dialog box does not display remote instances of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="91a1b-120">此外，[連接到伺服器]\*\*\*\* 對話方塊的 [連接選項]\*\*\*\* 索引標籤 (按一下 [選項]\*\*\*\* 按鈕即可顯示) 上的可用選項不適用於 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 連接。</span><span class="sxs-lookup"><span data-stu-id="91a1b-120">In addition, the options available on the **Connection Options** tab of the **Connect to Server** dialog box, which is displayed by clicking the **Options** button, are not applicable to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] connections.</span></span>  
  
## <a name="eliminating-the-access-is-denied-error"></a><span data-ttu-id="91a1b-121">排除「存取遭到拒絕」的錯誤</span><span class="sxs-lookup"><span data-stu-id="91a1b-121">Eliminating the "Access Is Denied" Error</span></span>  
 <span data-ttu-id="91a1b-122">如果不具備足夠權限的使用者試圖連接到遠端伺服器上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 執行個體，伺服器便會回應「存取遭到拒絕」的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="91a1b-122">When a user without sufficient rights attempts to connect to an instance of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] on a remote server, the server responds with an "Access is denied" error message.</span></span> <span data-ttu-id="91a1b-123">只要確保使用者具有 DCOM 權限，就可以避免產生這個錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="91a1b-123">You can avoid this error message by ensuring that users have the required DCOM permissions.</span></span>  
  
#### <a name="to-configure-rights-for-remote-users-on-windows-server-2003-or-windows-xp"></a><span data-ttu-id="91a1b-124">設定 Windows Server 2003 或 Windows XP 遠端使用者的權限</span><span class="sxs-lookup"><span data-stu-id="91a1b-124">To configure rights for remote users on Windows Server 2003 or Windows XP</span></span>  
  
1.  <span data-ttu-id="91a1b-125">如果使用者不是本機 Administrators 群組的成員，請將使用者加入「分散式 COM 使用者」群組。</span><span class="sxs-lookup"><span data-stu-id="91a1b-125">If the user is not a member of the local Administrators group, add the user to the Distributed COM Users group.</span></span> <span data-ttu-id="91a1b-126">您可以從 [系統管理工具]\*\*\*\* 功能表中的 [電腦管理] MMC 嵌入式管理單元進行這項作業。</span><span class="sxs-lookup"><span data-stu-id="91a1b-126">You can do this in the Computer Management MMC snap-in accessed from the **Administrative Tools** menu.</span></span>  
  
2.  <span data-ttu-id="91a1b-127">開啟 [控制台]，依序按兩下 [系統管理工具]\*\*\*\*、[元件服務]\*\*\*\* 啟動 [元件服務] MMC 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="91a1b-127">Open Control Panel, double-click **Administrative Tools,** and then double-click **Component Services** to start the Component Services MMC snap-in.</span></span>  
  
3.  <span data-ttu-id="91a1b-128">展開控制台左邊窗格中的 [元件服務]\*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="91a1b-128">Expand the **Component Services** node in the left pane of the console.</span></span> <span data-ttu-id="91a1b-129">依序展開 [電腦]\*\*\*\* 節點和 [我的電腦]\*\*\*\*，然後按一下 [DCOM 設定]\*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="91a1b-129">Expand the **Computers** node, expand **My Computer**, and then click the **DCOM Config** node.</span></span>  
  
4.  <span data-ttu-id="91a1b-130">選取 [DCOM 設定]\*\*\*\* 節點，然後選取可以設定之應用程式清單中的 SQL Server Integration Services 11.0。</span><span class="sxs-lookup"><span data-stu-id="91a1b-130">Select the **DCOM Config** node, and then select SQL Server Integration Services 11.0 in the list of applications that can be configured.</span></span>  
  
5.  <span data-ttu-id="91a1b-131">以滑鼠右鍵按一下 SQL Server Integration Services 11.0，然後選取 [內容]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="91a1b-131">Right-click on SQL Server Integration Services 11.0 and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="91a1b-132">在 [SQL Server Integration Services 11.0 內容]\*\*\*\* 對話方塊中，選取 [安全性]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="91a1b-132">In the **SQL Server Integration Services 11.0 Properties** dialog box, select the **Security** tab.</span></span>  
  
7.  <span data-ttu-id="91a1b-133">選取 [啟動和啟用權限]\*\*\*\* 底下的 [自訂]\*\*\*\*，然後按一下 [編輯]\*\*\*\* 開啟 [啟動權限]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="91a1b-133">Under **Launch and Activation Permissions**, select **Customize**, then click **Edit** to open the **Launch Permission** dialog box.</span></span>  
  
8.  <span data-ttu-id="91a1b-134">在 [啟動權限]\*\*\*\* 對話方塊中，新增或刪除使用者，並指派適當權限給適當的使用者與群組。</span><span class="sxs-lookup"><span data-stu-id="91a1b-134">In the **Launch Permission** dialog box, add or delete users, and assign the appropriate permissions to the appropriate users and groups.</span></span> <span data-ttu-id="91a1b-135">可用的權限有本機啟動、遠端啟動、本機啟用以及遠端啟用。</span><span class="sxs-lookup"><span data-stu-id="91a1b-135">The available permissions are Local Launch, Remote Launch, Local Activation, and Remote Activation.</span></span> <span data-ttu-id="91a1b-136">啟動權限可授與或拒絕啟動及停止服務的權限；啟用權限則可以授與或拒絕連接到服務的權限。</span><span class="sxs-lookup"><span data-stu-id="91a1b-136">The Launch rights grant or deny permission to start and stop the service; the Activation rights grant or deny permission to connect to the service.</span></span>  
  
9. <span data-ttu-id="91a1b-137">按一下 [確定] 關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="91a1b-137">Click OK to close the dialog box.</span></span>  
  
10. <span data-ttu-id="91a1b-138">在 [存取權限]\*\*\*\* 底下，重複步驟 7 和 8，為適當的使用者和群組指派適當的權限。</span><span class="sxs-lookup"><span data-stu-id="91a1b-138">Under **Access Permissions**, repeat steps 7 and 8 to assign the appropriate permissions to the appropriate users and groups.</span></span>  
  
11. <span data-ttu-id="91a1b-139">關閉 MMC 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="91a1b-139">Close the MMC snap-in.</span></span>  
  
12. <span data-ttu-id="91a1b-140">重新啟動 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="91a1b-140">Restart the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
#### <a name="to-configure-rights-for-remote-users-on-windows-2000-with-the-latest-service-packs"></a><span data-ttu-id="91a1b-141">設定具有最新 Service Pack 版本的 Windows 2000 遠端使用者權限</span><span class="sxs-lookup"><span data-stu-id="91a1b-141">To configure rights for remote users on Windows 2000 with the latest service packs</span></span>  
  
1.  <span data-ttu-id="91a1b-142">在命令提示字元執行 **dcomcnfg.exe** 。</span><span class="sxs-lookup"><span data-stu-id="91a1b-142">Run **dcomcnfg.exe** at the command prompt.</span></span>  
  
2.  <span data-ttu-id="91a1b-143">在 [分散式 COM 組態內容]\*\*\*\* 對話方塊的 [應用程式]\*\*\*\* 頁面上，選取 SQL Server Integration Services 11.0，然後按一下 [內容]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="91a1b-143">On the **Applications** page of the **Distributed COM Configuration Properties** dialog box, select SQL Server Integration Services 11.0 and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="91a1b-144">選取 [安全性] 頁面 \*\*\*\* 。</span><span class="sxs-lookup"><span data-stu-id="91a1b-144">Select the **Security** page.</span></span>  
  
4.  <span data-ttu-id="91a1b-145">使用兩個分開的對話方塊設定 [存取權限]\*\*\*\* 與 [啟動權限]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="91a1b-145">Use the two separate dialog boxes to configure **Access Permissions** and **Launch Permissions**.</span></span> <span data-ttu-id="91a1b-146">您無法區分遠端與本機存取，存取權限包含了本機與遠端存取，而啟動權限則包含了本機與遠端啟動。</span><span class="sxs-lookup"><span data-stu-id="91a1b-146">You cannot distinguish between remote and local access - Access permissions include local and remote access, and Launch permissions include local and remote launch.</span></span>  
  
5.  <span data-ttu-id="91a1b-147">關閉對話方塊和 **dcomcnfg.exe**。</span><span class="sxs-lookup"><span data-stu-id="91a1b-147">Close the dialog boxes and **dcomcnfg.exe**.</span></span>  
  
6.  <span data-ttu-id="91a1b-148">重新啟動 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="91a1b-148">Restart the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
## <a name="connecting-by-using-a-local-account"></a><span data-ttu-id="91a1b-149">使用本機帳戶進行連接</span><span class="sxs-lookup"><span data-stu-id="91a1b-149">Connecting by using a Local Account</span></span>  
 <span data-ttu-id="91a1b-150">如果您是在用戶端電腦上使用本機 Windows 帳戶工作，那麼只有當遠端電腦上存在和本機帳戶相同名稱與密碼以及適當權限的帳戶，您才能連接到遠端電腦上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="91a1b-150">If you are working in a local Windows account on a client computer, you can connect to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service on a remote computer only if a local account that has the same name and password and the appropriate rights exists on the remote computer.</span></span>  
  
## <a name="by-default-the-ssis-service-does-not-support-delegation"></a><span data-ttu-id="91a1b-151">SSIS 服務預設不支援委派</span><span class="sxs-lookup"><span data-stu-id="91a1b-151">By default the SSIS service does not support delegation</span></span>  
<span data-ttu-id="91a1b-152">根據預設 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ，服務不支援認證的委派，或有時稱為雙躍點。</span><span class="sxs-lookup"><span data-stu-id="91a1b-152">By default the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service does not support the delegation of credentials, or what is sometimes referred to as a double hop.</span></span> <span data-ttu-id="91a1b-153">在這種情況中，您是在用戶端電腦上工作、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務是在第二部電腦上執行， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 則是在第三部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="91a1b-153">In this scenario, you are working on a client computer, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is running on a second computer, and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is running on a third computer.</span></span> <span data-ttu-id="91a1b-154">首先， [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 已順利將認證從用戶端電腦傳遞至正在其上執行 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務的第二部電腦。</span><span class="sxs-lookup"><span data-stu-id="91a1b-154">First, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] successfully passes your credentials from the client computer to the second computer on which the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is running.</span></span> <span data-ttu-id="91a1b-155">接著，不過， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務無法將認證從第二部電腦委派至正在其上執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的第三部電腦。</span><span class="sxs-lookup"><span data-stu-id="91a1b-155">Then, however, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service cannot delegate your credentials from the second computer to the third computer on which [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is running.</span></span>

<span data-ttu-id="91a1b-156">將 [信任這個使用者，可委派任何服務 (只限 Kerberos)]\*\*\*\* 權限授與 SQL Server 服務帳戶 (可將 Integration Services 服務 (ISServerExec.exe) 啟動為子處理序)，即可啟用認證委派。</span><span class="sxs-lookup"><span data-stu-id="91a1b-156">You can enable delegation of credentials by granting the **Trust this user for delegation to any service (Kerberos Only)** right to the SQL Server service account, which launches the Integration Services service (ISServerExec.exe) as a child process.</span></span> <span data-ttu-id="91a1b-157">在授與此權限之前，請考慮它是否符合您組織的安全性需求。</span><span class="sxs-lookup"><span data-stu-id="91a1b-157">Before you grant this right, consider whether it meets the security requirements of your organization.</span></span>

<span data-ttu-id="91a1b-158">如需詳細資訊，請參閱 [取得使用 SSIS 封裝的跨網域 Kerberos 和委派](https://blogs.msdn.microsoft.com/psssql/2014/06/26/getting-cross-domain-kerberos-and-delegation-working-with-ssis-package/)。</span><span class="sxs-lookup"><span data-stu-id="91a1b-158">For more info, see [Getting Cross Domain Kerberos and Delegation working with SSIS Package](https://blogs.msdn.microsoft.com/psssql/2014/06/26/getting-cross-domain-kerberos-and-delegation-working-with-ssis-package/).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="91a1b-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91a1b-159">See Also</span></span>  
 [<span data-ttu-id="91a1b-160">針對 SSIS 服務的存取設定 Windows 防火牆</span><span class="sxs-lookup"><span data-stu-id="91a1b-160">Configure a Windows Firewall for Access to the SSIS Service</span></span>](../../2014/integration-services/configure-a-windows-firewall-for-access-to-the-ssis-service.md)  
  
  
