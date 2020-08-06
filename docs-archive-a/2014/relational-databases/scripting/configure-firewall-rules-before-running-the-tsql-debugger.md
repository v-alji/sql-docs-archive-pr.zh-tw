---
title: 設定 Transact-SQL 偵錯工具
ms.custom: seo-lt-2019
ms.date: 10/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vs.debug.error.sqlde_register_failed
- vs.debug.error.sqlde_accessdenied
- vs.debug.error.sqlde_firewall.remotemachines
helpviewer_keywords:
- Transact-SQL debugger, remote connections
- Windows Firewall [Database Engine], Transact-SQL debugger
- Transact-SQL debugger, Windows Firewall
- Transact-SQL debugger, configuring
- ports [SQL Server], Transact-SQL debugger
- TCP/IP [SQL Server], port numbers
ms.assetid: f50e0b0d-eaf0-4f4a-be83-96f5be63e7ea
author: rothja
ms.author: jroth
ms.openlocfilehash: a320e77e86c933a33d96d708580d5050b0c06de2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598813"
---
# <a name="configure-the-transact-sql-debugger"></a><span data-ttu-id="02384-102">設定 Transact-SQL 偵錯工具</span><span class="sxs-lookup"><span data-stu-id="02384-102">Configure the Transact-SQL Debugger</span></span>
  <span data-ttu-id="02384-103">當連接的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 執行個體與 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器在不同的電腦上執行時，就必須設定 Windows 防火牆規則才能啟用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 偵錯。</span><span class="sxs-lookup"><span data-stu-id="02384-103">Windows Firewall rules must be configured to enable [!INCLUDE[tsql](../../includes/tsql-md.md)] debugging when connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that is running on a different computer than the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
## <a name="configuring-the-transact-sql-debugger"></a><span data-ttu-id="02384-104">設定 Transact-SQL 偵錯工具</span><span class="sxs-lookup"><span data-stu-id="02384-104">Configuring the Transact-SQL Debugger</span></span>  
 <span data-ttu-id="02384-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具同時包含伺服器端和用戶端元件。</span><span class="sxs-lookup"><span data-stu-id="02384-105">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger includes both server-side and client-side components.</span></span> <span data-ttu-id="02384-106">伺服器端的偵錯工具元件會隨著 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 (SP2) 或更新版本中的每個 Database Engine 執行個體一起安裝。</span><span class="sxs-lookup"><span data-stu-id="02384-106">The server-side debugger components are installed with each instance of the Database Engine from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 (SP2) or later.</span></span> <span data-ttu-id="02384-107">包括用戶端偵錯工具元件的情況：</span><span class="sxs-lookup"><span data-stu-id="02384-107">The client-side debugger components are included:</span></span>  
  
-   <span data-ttu-id="02384-108">當您從 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或更新版本安裝用戶端工具時。</span><span class="sxs-lookup"><span data-stu-id="02384-108">When you install the client-side tools from [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later.</span></span>  
  
-   <span data-ttu-id="02384-109">當您安裝 Microsoft Visual Studio 2010 或更新版本時。</span><span class="sxs-lookup"><span data-stu-id="02384-109">When you install Microsoft Visual Studio 2010 or later.</span></span>  
  
-   <span data-ttu-id="02384-110">當您從 Web 下載安裝 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 時。</span><span class="sxs-lookup"><span data-stu-id="02384-110">When you install [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] from the web download.</span></span>  
  
 <span data-ttu-id="02384-111">當 [!INCLUDE[tsql](../../includes/tsql-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 與 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 執行個體在同一部電腦上執行時，沒有任何執行 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]偵錯工具的組態需求。</span><span class="sxs-lookup"><span data-stu-id="02384-111">There are no configuration requirements to run the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger when [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] is running on the same computer as the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="02384-112">不過，當連接至遠端 [!INCLUDE[tsql](../../includes/tsql-md.md)] 執行個體時，若要執行 [!INCLUDE[ssDE](../../includes/ssde-md.md)]偵錯工具，就必須在這兩部電腦上啟用 Windows 防火牆中的程式和通訊埠規則。</span><span class="sxs-lookup"><span data-stu-id="02384-112">However, to run the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger when connected to a remote instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], program and port rules in the Windows Firewall must be enabled on both computers.</span></span> <span data-ttu-id="02384-113">這些規則可以由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式建立。</span><span class="sxs-lookup"><span data-stu-id="02384-113">These rules may be created by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup.</span></span> <span data-ttu-id="02384-114">如果您嘗試開啟遠端偵錯工作階段時發生錯誤，請確定您的電腦上已定義下列防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="02384-114">If you get errors attempting to open a remote debugging session, ensure the following firewall rules are defined on your computer.</span></span>  
  
 <span data-ttu-id="02384-115">使用 [具有進階安全性的 Windows 防火牆]\*\*\*\* 應用程式來管理防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="02384-115">Use the **Windows Firewall with Advanced Security** application to manage the firewall rules.</span></span> <span data-ttu-id="02384-116">在 [!INCLUDE[win7](../../includes/win7-md.md)] 和 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 中，開啟 [控制台]\*\*\*\*，開啟 [Windows 防火牆]\*\*\*\*，然後選取 [進階設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-116">In both [!INCLUDE[win7](../../includes/win7-md.md)] and [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)], open **Control Panel**, open **Windows Firewall**, and select **Advanced settings**.</span></span> <span data-ttu-id="02384-117">在 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 中，您也可以開啟 [服務管理員]\*\*\*\*，然後展開左窗格中的 [組態]\*\*\*\*，再展開 [具有進階安全性的 Windows 防火牆]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-117">In [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] you can also open **Service Manager**, expand **Configuration** in the left pane, and expand **Windows Firewall with Advanced Security**.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="02384-118">在 [Windows 防火牆] 中啟用規則可能會讓您的電腦暴露在防火牆設計可封鎖的安全性威脅下。</span><span class="sxs-lookup"><span data-stu-id="02384-118">Enabling rules in the Windows Firewall may expose your computer to security threats that the firewall is designed to block.</span></span> <span data-ttu-id="02384-119">啟用遠端偵錯規則會解除封鎖本主題中列出的通訊埠和程式。</span><span class="sxs-lookup"><span data-stu-id="02384-119">Enabling rules for remote debugging unblocks the ports and programs listed in this topic.</span></span>  
  
## <a name="firewall-rules-on-the-server"></a><span data-ttu-id="02384-120">伺服器上的防火牆規則</span><span class="sxs-lookup"><span data-stu-id="02384-120">Firewall Rules on the Server</span></span>  
 <span data-ttu-id="02384-121">在執行 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體的電腦上，使用 [具有進階安全性的 Windows 防火牆]\*\*\*\* 指定下列資訊：</span><span class="sxs-lookup"><span data-stu-id="02384-121">On the computer that is running the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], use **Windows Firewall with Advanced Security** to specify the following information:</span></span>  
  
-   <span data-ttu-id="02384-122">加入 sqlservr.exe 的輸入程式規則。</span><span class="sxs-lookup"><span data-stu-id="02384-122">Add an inbound program rule for sqlservr.exe.</span></span> <span data-ttu-id="02384-123">每一個需要支援遠端偵錯工作階段的執行個體都必須有一項規則。</span><span class="sxs-lookup"><span data-stu-id="02384-123">You must have a rule for each instance that needs to support remote debugging sessions.</span></span>  
  
    1.  <span data-ttu-id="02384-124">在 [具有進階安全性的 Windows 防火牆]\*\*\*\* 的左窗格中，以滑鼠右鍵按一下 [輸入規則]\*\*\*\*，再從動作窗格選取 [新增規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-124">In **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then select **New Rule** in the action pane.</span></span>  
  
    2.  <span data-ttu-id="02384-125">在 [規則類型]\*\*\*\* 對話方塊中，選取 [程式]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-125">In the **Rule Type** dialog, select **Program**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="02384-126">在 [程式]\*\*\*\* 對話方塊中，選取 [這個程式路徑]\*\*\*\*，然後輸入此執行個體的 sqlservr.exe 完整路徑。</span><span class="sxs-lookup"><span data-stu-id="02384-126">In the **Program** dialog, select **This program path:** and enter the full path to sqlservr.exe for this instance.</span></span> <span data-ttu-id="02384-127">根據預設，sqlservr.exe 會安裝在 C:\Program Files\Microsoft SQL Server\MSSQL12. 中。*Instancename*\MSSQL\Binn，其中*instancename*是預設實例的 MSSQLSERVER，以及任何已命名實例的實例名稱。</span><span class="sxs-lookup"><span data-stu-id="02384-127">By default, sqlservr.exe is installed in C:\Program Files\Microsoft SQL Server\MSSQL12.*InstanceName*\MSSQL\Binn, where *InstanceName* is MSSQLSERVER for the default instance, and the instance name for any named instance.</span></span>  
  
    4.  <span data-ttu-id="02384-128">在 [動作]\*\*\*\* 對話方塊中，選取 [允許連線]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-128">In the **Action** dialog, select **Allow the connection**, and click **Next**.</span></span>  
  
    5.  <span data-ttu-id="02384-129">在 [設定檔]\*\*\*\* 對話方塊中，選取描述您想要開啟執行個體之偵錯工作階段時電腦連線環境的任何設定檔，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-129">In the **Profile** dialog, select any profiles that describe the computer connection environment when you want to open a debugging session with the instance, and click **Next**.</span></span>  
  
    6.  <span data-ttu-id="02384-130">在 [名稱]\*\*\*\* 對話方塊中，輸入此規則的名稱和描述，然後按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-130">In the **Name** dialog, type a name and description for this rule and click **Finish**.</span></span>  
  
    7.  <span data-ttu-id="02384-131">在 [輸入規則]\*\*\*\* 清單中，以滑鼠右鍵按一下您建立的規則，然後選取動作窗格中的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-131">In the **Inbound Rules** list, right click the rule you created, and then select **Properties** in the action pane.</span></span>  
  
    8.  <span data-ttu-id="02384-132">選取 [通訊協定及連接埠]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="02384-132">Select the **Protocols and Ports** tab.</span></span>  
  
    9. <span data-ttu-id="02384-133">在 [通訊協定類型:]\*\*\*\* 方塊中選取 [TCP]\*\*\*\*，在 [本機通訊埠:]\*\*\*\* 方塊中選取 [RPC 動態通訊埠]\*\*\*\*，按一下 [套用]\*\*\*\*，再按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-133">Select **TCP** in the **Protocol type:** box, select **RPC Dynamic Ports** in the **Local port:** box, click **Apply**, and then click **OK**.</span></span>  
  
-   <span data-ttu-id="02384-134">加入 svchost.exe 的輸入程式規則可啟用來自遠端偵錯工具工作階段的 DCOM 通訊。</span><span class="sxs-lookup"><span data-stu-id="02384-134">Add an inbound program rule for svchost.exe to enable DCOM communications from remote debugger sessions.</span></span>  
  
    1.  <span data-ttu-id="02384-135">在 [具有進階安全性的 Windows 防火牆]\*\*\*\* 的左窗格中，以滑鼠右鍵按一下 [輸入規則]\*\*\*\*，再從動作窗格選取 [新增規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-135">In **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then select **New Rule** in the action pane.</span></span>  
  
    2.  <span data-ttu-id="02384-136">在 [規則類型]\*\*\*\* 對話方塊中，選取 [程式]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-136">In the **Rule Type** dialog, select **Program**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="02384-137">在 [程式]\*\*\*\* 對話方塊中，選取 [這個程式路徑:]\*\*\*\*，然後輸入 svchost.exe 的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="02384-137">In the **Program** dialog, select **This program path:** and enter the full path to svchost.exe.</span></span> <span data-ttu-id="02384-138">根據預設，svchost.exe 安裝於 %systemroot%\System32\svchost.exe。</span><span class="sxs-lookup"><span data-stu-id="02384-138">By default, svchost.exe is installed in %systemroot%\System32\svchost.exe.</span></span>  
  
    4.  <span data-ttu-id="02384-139">在 [動作]\*\*\*\* 對話方塊中，選取 [允許連線]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-139">In the **Action** dialog, select **Allow the connection**, and click **Next**.</span></span>  
  
    5.  <span data-ttu-id="02384-140">在 [設定檔]\*\*\*\* 對話方塊中，選取描述您想要開啟執行個體之偵錯工作階段時電腦連線環境的任何設定檔，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-140">In the **Profile** dialog, select any profiles that describe the computer connection environment when you want to open a debugging session with the instance, and click **Next**.</span></span>  
  
    6.  <span data-ttu-id="02384-141">在 [名稱]\*\*\*\* 對話方塊中，輸入此規則的名稱和描述，然後按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-141">In the **Name** dialog, type a name and description for this rule and click **Finish**.</span></span>  
  
    7.  <span data-ttu-id="02384-142">在 [輸入規則]\*\*\*\* 清單中，以滑鼠右鍵按一下您建立的規則，然後選取動作窗格中的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-142">In the **Inbound Rules** list, right click the rule you created, and then select **Properties** in the action pane.</span></span>  
  
    8.  <span data-ttu-id="02384-143">選取 [通訊協定及連接埠]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="02384-143">Select the **Protocols and Ports** tab.</span></span>  
  
    9. <span data-ttu-id="02384-144">在 [通訊協定類型:]\*\*\*\* 方塊中選取 [TCP]\*\*\*\*，在 [本機通訊埠:]\*\*\*\* 方塊中選取 [RPC 端點對應程式]\*\*\*\*，按一下 [套用]\*\*\*\*，再按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-144">Select **TCP** in the **Protocol type:** box, select **RPC Endpoint Mapper** in the **Local port:** box, click **Apply**, and then click **OK**.</span></span>  
  
-   <span data-ttu-id="02384-145">如果網域原則要求透過 IPsec 完成網路通訊，您也必須加入開啟 UDP 通訊埠 4500 和 UDP 通訊埠 500 的輸入規則。</span><span class="sxs-lookup"><span data-stu-id="02384-145">If the domain policy requires network communications to be done through IPsec, you must also add inbound rules opening UDP port 4500 and UDP port 500.</span></span>  
  
## <a name="firewall-rules-on-the-client"></a><span data-ttu-id="02384-146">用戶端上的防火牆規則</span><span class="sxs-lookup"><span data-stu-id="02384-146">Firewall Rules on the Client</span></span>  
 <span data-ttu-id="02384-147">在執行 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器的電腦上，SQL Server 安裝程式或 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 安裝程式可能已將 Windows 防火牆設定為允許遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="02384-147">On the computer that is running the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor, the SQL Server setup or [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] setup may have configured the Windows Firewall to allow remote debugging.</span></span>  
  
 <span data-ttu-id="02384-148">如果您嘗試開啟遠端偵錯工作階段時發生錯誤，可以使用 [具有進階安全性的 Windows 防火牆]\*\*\*\* 設定防火牆規則，手動設定程式和通訊埠例外狀況：</span><span class="sxs-lookup"><span data-stu-id="02384-148">If you get errors attempting to open a remote debugging session, you can manually configure the program and port exceptions by using **Windows Firewall with Advanced Security** to configure firewall rules:</span></span>  
  
-   <span data-ttu-id="02384-149">加入 svchost 的程式項目：</span><span class="sxs-lookup"><span data-stu-id="02384-149">Add a program entry for svchost:</span></span>  
  
    1.  <span data-ttu-id="02384-150">在 [具有進階安全性的 Windows 防火牆]\*\*\*\* 的左窗格中，以滑鼠右鍵按一下 [輸入規則]\*\*\*\*，再從動作窗格選取 [新增規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-150">In **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then select **New Rule** in the action pane.</span></span>  
  
    2.  <span data-ttu-id="02384-151">在 [規則類型]\*\*\*\* 對話方塊中，選取 [程式]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-151">In the **Rule Type** dialog, select **Program**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="02384-152">在 [程式]\*\*\*\* 對話方塊中，選取 [這個程式路徑:]\*\*\*\*，然後輸入 svchost.exe 的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="02384-152">In the **Program** dialog, select **This program path:** and enter the full path to svchost.exe.</span></span> <span data-ttu-id="02384-153">根據預設，svchost.exe 安裝於 %systemroot%\System32\svchost.exe。</span><span class="sxs-lookup"><span data-stu-id="02384-153">By default, svchost.exe is installed in %systemroot%\System32\svchost.exe.</span></span>  
  
    4.  <span data-ttu-id="02384-154">在 [動作]\*\*\*\* 對話方塊中，選取 [允許連線]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-154">In the **Action** dialog, select **Allow the connection**, and click **Next**.</span></span>  
  
    5.  <span data-ttu-id="02384-155">在 [設定檔]\*\*\*\* 對話方塊中，選取描述您想要開啟執行個體之偵錯工作階段時電腦連線環境的任何設定檔，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-155">In the **Profile** dialog, select any profiles that describe the computer connection environment when you want to open a debugging session with the instance, and click **Next**.</span></span>  
  
    6.  <span data-ttu-id="02384-156">在 [名稱]\*\*\*\* 對話方塊中，輸入此規則的名稱和描述，然後按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-156">In the **Name** dialog, type a name and description for this rule and click **Finish**.</span></span>  
  
    7.  <span data-ttu-id="02384-157">在 [輸入規則]\*\*\*\* 清單中，以滑鼠右鍵按一下您建立的規則，然後選取動作窗格中的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-157">In the **Inbound Rules** list, right click the rule you created, and then select **Properties** in the action pane.</span></span>  
  
    8.  <span data-ttu-id="02384-158">選取 [通訊協定及連接埠]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="02384-158">Select the **Protocols and Ports** tab.</span></span>  
  
    9. <span data-ttu-id="02384-159">在 [通訊協定類型:]\*\*\*\* 方塊中選取 [TCP]\*\*\*\*，在 [本機通訊埠:]\*\*\*\* 方塊中選取 [RPC 端點對應程式]\*\*\*\*，按一下 [套用]\*\*\*\*，再按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-159">Select **TCP** in the **Protocol type:** box, select **RPC Endpoint Mapper** in the **Local port:** box, click **Apply**, and then click **OK**.</span></span>  
  
-   <span data-ttu-id="02384-160">針對裝載 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器的應用程式加入程式項目。</span><span class="sxs-lookup"><span data-stu-id="02384-160">Add a program entry for the application hosting the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="02384-161">如果您需要在同一部電腦上同時從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 開啟遠端偵錯工作階段，則必須針對兩者加入程式規則：</span><span class="sxs-lookup"><span data-stu-id="02384-161">If you need to open remote debugging sessions from both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] on the same computer, you must add a program rule for both:</span></span>  
  
    1.  <span data-ttu-id="02384-162">在 [具有進階安全性的 Windows 防火牆]\*\*\*\* 的左窗格中，以滑鼠右鍵按一下 [輸入規則]\*\*\*\*，再從動作窗格選取 [新增規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-162">In **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then select **New Rule** in the action pane.</span></span>  
  
    2.  <span data-ttu-id="02384-163">在 [規則類型]\*\*\*\* 對話方塊中，選取 [程式]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-163">In the **Rule Type** dialog, select **Program**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="02384-164">在 [程式]\*\*\*\* 對話方塊中，選取 [這個程式路徑:]\*\*\*\*，然後輸入下列三個值的其中一個。</span><span class="sxs-lookup"><span data-stu-id="02384-164">In the **Program** dialog, select **This program path:** and enter one of these three values.</span></span>  
  
        -   <span data-ttu-id="02384-165">針對 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]輸入 ssms.exe 的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="02384-165">For [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], enter the full path to ssms.exe.</span></span> <span data-ttu-id="02384-166">根據預設，ssms.exe 安裝於 C:\Program Files (x86)\Microsoft SQL Server\120\Tools\Binn\Management Studio。</span><span class="sxs-lookup"><span data-stu-id="02384-166">By default, ssms.exe is installed in C:\Program Files (x86)\Microsoft SQL Server\120\Tools\Binn\Management Studio.</span></span>  
  
        -   <span data-ttu-id="02384-167">針對 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 輸入 devenv.exe 的完整路徑：</span><span class="sxs-lookup"><span data-stu-id="02384-167">For [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] enter the full path to devenv.exe:</span></span>  
  
            1.  <span data-ttu-id="02384-168">根據預設，Visual Studio 2010 的 devenv.exe 位於 C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE。</span><span class="sxs-lookup"><span data-stu-id="02384-168">By default, the devenv.exe for Visual Studio 2010 is in C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE.</span></span>  
  
            2.  <span data-ttu-id="02384-169">根據預設，Visual Studio 2012 的 devenv.exe 位於 C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE</span><span class="sxs-lookup"><span data-stu-id="02384-169">By default, the devenv.exe for Visual Studio 2012 is in C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE</span></span>  
  
            3.  <span data-ttu-id="02384-170">您可以從用來啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的捷徑找到 ssms.exe 的路徑。</span><span class="sxs-lookup"><span data-stu-id="02384-170">You can find the path to ssms.exe from the shortcut you use to launch [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="02384-171">您可以從用來啟動 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]的捷徑找到 devenv.exe 的路徑。</span><span class="sxs-lookup"><span data-stu-id="02384-171">You can find the path to devenv.exe from the shortcut you use to launch [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="02384-172">以滑鼠右鍵按一下捷徑，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-172">Right click the shortcut and select **Properties**.</span></span> <span data-ttu-id="02384-173">可執行檔和路徑會在 [目標]\*\*\*\* 方塊中列出。</span><span class="sxs-lookup"><span data-stu-id="02384-173">The executable and path are listed in the **Target** box.</span></span>  
  
    4.  <span data-ttu-id="02384-174">在 [動作]\*\*\*\* 對話方塊中，選取 [允許連線]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-174">In the **Action** dialog, select **Allow the connection**, and click **Next**.</span></span>  
  
    5.  <span data-ttu-id="02384-175">在 [設定檔]\*\*\*\* 對話方塊中，選取描述您想要開啟執行個體之偵錯工作階段時電腦連線環境的任何設定檔，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-175">In the **Profile** dialog, select any profiles that describe the computer connection environment when you want to open a debugging session with the instance, and click **Next**.</span></span>  
  
    6.  <span data-ttu-id="02384-176">在 [名稱]\*\*\*\* 對話方塊中，輸入此規則的名稱和描述，然後按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-176">In the **Name** dialog, type a name and description for this rule and click **Finish**.</span></span>  
  
    7.  <span data-ttu-id="02384-177">在 [輸入規則]\*\*\*\* 清單中，以滑鼠右鍵按一下您建立的規則，然後選取動作窗格中的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-177">In the **Inbound Rules** list, right click the rule you created, and then select **Properties** in the action pane.</span></span>  
  
    8.  <span data-ttu-id="02384-178">選取 [通訊協定及連接埠]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="02384-178">Select the **Protocols and Ports** tab.</span></span>  
  
    9. <span data-ttu-id="02384-179">在 [通訊協定類型:]\*\*\*\* 方塊中選取 [TCP]\*\*\*\*，在 [本機通訊埠:]\*\*\*\* 方塊中選取 [RPC 動態通訊埠]\*\*\*\*，按一下 [套用]\*\*\*\*，再按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02384-179">Select **TCP** in the **Protocol type:** box, select **RPC Dynamic Ports** in the **Local port:** box, click **Apply**, and then click **OK**.</span></span>  
  
## <a name="requirements-for-starting-the-debugger"></a><span data-ttu-id="02384-180">啟動偵錯工具的需求</span><span class="sxs-lookup"><span data-stu-id="02384-180">Requirements for Starting the Debugger</span></span>  
 <span data-ttu-id="02384-181">啟動 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具的所有嘗試也必須符合下列需求：</span><span class="sxs-lookup"><span data-stu-id="02384-181">All attempts to start the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger must also meet the following requirements:</span></span>  
  
* [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="02384-182">或 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 必須在屬於系統管理員固定伺服器角色成員的 Windows 帳戶底下執行。</span><span class="sxs-lookup"><span data-stu-id="02384-182">or [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] must be running under a Windows account that is a member of the sysadmin fixed server roll.</span></span>  
  
* <span data-ttu-id="02384-183">您必須使用屬於系統管理員 (sysadmin) 固定伺服器角色成員的 Windows 驗證或 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 驗證登入來連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 查詢編輯器視窗。</span><span class="sxs-lookup"><span data-stu-id="02384-183">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window must be connected by using either a Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication login that is a member of the sysadmin fixed server role.</span></span>  
  
* <span data-ttu-id="02384-184">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器視窗必須連接至 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Service Pack 2 (SP2) 或更新版本中的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="02384-184">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window must be connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 (SP2) or later.</span></span> <span data-ttu-id="02384-185">當 [查詢編輯器] 視窗連接至處於單一使用者模式下的執行個體時，您就無法執行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="02384-185">You cannot run the debugger when the Query Editor window is connected to an instance that is in single-user mode.</span></span>

* <span data-ttu-id="02384-186">伺服器必須透過 RPC 回應用戶端。</span><span class="sxs-lookup"><span data-stu-id="02384-186">The server needs to communicate back to the client via RPC.</span></span> <span data-ttu-id="02384-187">執行 SQL Server 服務的帳戶應該要有用戶端的驗證許可權。</span><span class="sxs-lookup"><span data-stu-id="02384-187">The account under which SQL Server service is running should have authenticate permissions to the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02384-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02384-188">See Also</span></span>  
 <span data-ttu-id="02384-189">[Transact-sql 偵錯工具](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="02384-189">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="02384-190">[執行 Transact-sql 偵錯工具](run-the-transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="02384-190">[Run the Transact-SQL Debugger](run-the-transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="02384-191">[逐步執行 Transact-sql 程式碼](step-through-transact-sql-code.md) </span><span class="sxs-lookup"><span data-stu-id="02384-191">[Step Through Transact-SQL Code](step-through-transact-sql-code.md) </span></span>  
 <span data-ttu-id="02384-192">[Transact-sql 偵錯工具資訊](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="02384-192">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 [<span data-ttu-id="02384-193">Database Engine 查詢編輯器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="02384-193">Database Engine Query Editor &#40;SQL Server Management Studio&#41;</span></span>](database-engine-query-editor-sql-server-management-studio.md)  
  
  
