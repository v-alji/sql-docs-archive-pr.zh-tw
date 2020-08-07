---
title: 設定多重主目錄電腦進行 SQL Server 存取 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- ports [SQL Server], multi-homed computer
- multi-homed computer [SQL Server] configuring ports
- firewall systems [Database Engine], multi-homed computer
ms.assetid: ba369e5b-7d1f-4544-b7f1-9b098a1e75bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b20fa552e57441ef211049f0e51b4f8d65e6f2e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597566"
---
# <a name="configure-a-multi-homed-computer-for-sql-server-access"></a><span data-ttu-id="82a8c-102">設定多重主目錄電腦進行 SQL Server 存取</span><span class="sxs-lookup"><span data-stu-id="82a8c-102">Configure a Multi-Homed Computer for SQL Server Access</span></span>
  <span data-ttu-id="82a8c-103">當伺服器必須提供兩個或多個網路或子網路的連接時，一般會使用多重主目錄電腦。</span><span class="sxs-lookup"><span data-stu-id="82a8c-103">When a server must provide a connection to two or more networks or network subnets, a typical scenario uses a multi-homed computer.</span></span> <span data-ttu-id="82a8c-104">這部電腦通常位於周邊網路 (也稱為 DMZ 或篩選的子網路) 中。</span><span class="sxs-lookup"><span data-stu-id="82a8c-104">Frequently this computer is located in a perimeter network (also known as DMZ, demilitarized zone, or screened subnet).</span></span> <span data-ttu-id="82a8c-105">此主題描述如何設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和具有進階安全性的 Windows 防火牆，以便在多重主目錄環境中提供給 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的網路連接。</span><span class="sxs-lookup"><span data-stu-id="82a8c-105">This topic describes how to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows Firewall with Advanced Security to provide for network connections to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a multi-homed environment.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82a8c-106">多重主目錄電腦具有多張網路介面卡，或者已經設定成針對單一網路介面卡使用多個 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="82a8c-106">A multi-homed computer has multiple network adapters or has been configured to use multiple IP addresses for a single network adapter.</span></span> <span data-ttu-id="82a8c-107">雙重主目錄電腦具有兩張網路介面卡，或者已經設定成針對單一網路介面卡使用兩個 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="82a8c-107">A dual-homed computer has two network adapters or has been configured to use two IP addresses for a single network adapter.</span></span>  
  
 <span data-ttu-id="82a8c-108">繼續進行本主題之前，您應該先熟悉 [設定 Windows 防火牆以允許 SQL Server 存取](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)主題中提供的資訊。</span><span class="sxs-lookup"><span data-stu-id="82a8c-108">Before you continue in this topic, you should be familiar with the information provided in the topic [Configure the Windows Firewall to Allow SQL Server Access](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span> <span data-ttu-id="82a8c-109">這個主題包含有關 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件如何使用防火牆的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="82a8c-109">This topic contains basic information about how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components work with the firewall.</span></span>  
  
 <span data-ttu-id="82a8c-110">**這個範例假設：**</span><span class="sxs-lookup"><span data-stu-id="82a8c-110">**Assumptions for this example:**</span></span>  
  
-   <span data-ttu-id="82a8c-111">電腦中安裝了兩張網路介面卡。</span><span class="sxs-lookup"><span data-stu-id="82a8c-111">There are two network adapters installed in the computer.</span></span> <span data-ttu-id="82a8c-112">其中一或多張網路介面卡可能是無線的。</span><span class="sxs-lookup"><span data-stu-id="82a8c-112">One or more of the network adapters can be wireless.</span></span> <span data-ttu-id="82a8c-113">您可以使用某張網路介面卡的 IP 位址，然後使用回送 IP 位址 (127.0.0.1) 當做第二張網路介面卡，藉以模擬擁有兩張網路介面卡。</span><span class="sxs-lookup"><span data-stu-id="82a8c-113">You can simulate having two network adapters by using the IP address of one network adapter, and using the loopback IP address (127.0.0.1) as the second network adapter.</span></span>  
  
-   <span data-ttu-id="82a8c-114">為了簡化，這個範例會使用 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="82a8c-114">For simplicity, this example uses IPv4 addresses.</span></span> <span data-ttu-id="82a8c-115">您可以使用 IPv6 位址來執行相同的程序。</span><span class="sxs-lookup"><span data-stu-id="82a8c-115">The same procedures can be performed by using IPv6 addresses.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="82a8c-116">IPv4 位址是一連串稱為八位元資料組的四個數字。</span><span class="sxs-lookup"><span data-stu-id="82a8c-116">IPv4 addresses are a series of four numbers known as octets.</span></span> <span data-ttu-id="82a8c-117">每個數字都小於 255，並以句號隔開，例如 127.0.0.1。</span><span class="sxs-lookup"><span data-stu-id="82a8c-117">Each number is less than 255, separated by periods, such as 127.0.0.1.</span></span> <span data-ttu-id="82a8c-118">IPv6 位址是一連串八個十六進位數字 (以冒號隔開)，例如 fe80:4898:23:3:49a6:f5c1:2452:b994。</span><span class="sxs-lookup"><span data-stu-id="82a8c-118">IPv6 addresses are a series of eight hexadecimal numbers separated by colons, such as fe80:4898:23:3:49a6:f5c1:2452:b994.</span></span>  
  
-   <span data-ttu-id="82a8c-119">防火牆規則可能會允許透過特定通訊埠存取，例如通訊埠 1433。</span><span class="sxs-lookup"><span data-stu-id="82a8c-119">Firewall rules could allow access through a specific port, such as port 1433.</span></span> <span data-ttu-id="82a8c-120">或者，防火牆規則可能會允許存取 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 程式 (sqlservr.exe)。</span><span class="sxs-lookup"><span data-stu-id="82a8c-120">Or firewall rules could allow access to the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] program (sqlservr.exe).</span></span> <span data-ttu-id="82a8c-121">這兩種方法各有優點。</span><span class="sxs-lookup"><span data-stu-id="82a8c-121">Neither method is better than the other.</span></span> <span data-ttu-id="82a8c-122">由於周邊網路中的伺服器會比內部網路上的伺服器更容易遭受攻擊，因此本主題會假設您想要擁有更精確的控制權，而且分別選取您所開啟的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="82a8c-122">Because a server in a perimeter network is more vulnerable to attack than servers on an intranet, this topic assumes that you want to have more precise control, and individually select the ports that you open.</span></span> <span data-ttu-id="82a8c-123">基於上述原因，本主題會假設您要將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定為接聽固定通訊埠。</span><span class="sxs-lookup"><span data-stu-id="82a8c-123">For that reason, this topic assumes that you will configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to listen on a fixed port.</span></span> <span data-ttu-id="82a8c-124">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所用連接埠的詳細資訊，請參閱 [設定 Windows 防火牆以允許 SQL Server 存取](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="82a8c-124">For more information about the ports that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses, see [Configure the Windows Firewall to Allow SQL Server Access](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
-   <span data-ttu-id="82a8c-125">這則範例會使用 TCP 通訊埠 1433 來設定 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的存取權。</span><span class="sxs-lookup"><span data-stu-id="82a8c-125">This example configures access to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by using TCP port 1433.</span></span> <span data-ttu-id="82a8c-126">您可以使用相同的一般步驟來設定不同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件所使用的其他通訊埠。</span><span class="sxs-lookup"><span data-stu-id="82a8c-126">The other ports that are the different [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components use can be configured by using the same general steps.</span></span>  
  
 <span data-ttu-id="82a8c-127">**這則範例中的一般步驟如下所示：**</span><span class="sxs-lookup"><span data-stu-id="82a8c-127">**The general steps in this example are as follows:**</span></span>  
  
-   <span data-ttu-id="82a8c-128">判斷電腦的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="82a8c-128">Determine the IP addresses on the computer.</span></span>  
  
-   <span data-ttu-id="82a8c-129">將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定為接聽特定的 TCP 通訊埠。</span><span class="sxs-lookup"><span data-stu-id="82a8c-129">Configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to listen on a specific TCP port.</span></span>  
  
-   <span data-ttu-id="82a8c-130">設定具有進階安全性的 Windows 防火牆。</span><span class="sxs-lookup"><span data-stu-id="82a8c-130">Configure Windows Firewall with Advanced Security.</span></span>  
  
## <a name="optional-procedures"></a><span data-ttu-id="82a8c-131">選擇性程序</span><span class="sxs-lookup"><span data-stu-id="82a8c-131">Optional Procedures</span></span>  
 <span data-ttu-id="82a8c-132">如果您已經知道電腦可用的 IP 位址，以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]所使用的 IP 位址，就可以略過下列程序。</span><span class="sxs-lookup"><span data-stu-id="82a8c-132">If you already know the IP addresses available to your computer and that are used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can skip these procedures.</span></span>  
  
#### <a name="to-determine-the-ip-addresses-available-on-the-computer"></a><span data-ttu-id="82a8c-133">若要判斷電腦可用的 IP 位址</span><span class="sxs-lookup"><span data-stu-id="82a8c-133">To determine the IP addresses available on the computer</span></span>  
  
1.  <span data-ttu-id="82a8c-134">在安裝的電腦上，依序按一下 [開始] 和 [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **執行**]，輸入， **Start** `cmd` 然後 [!INCLUDE[clickOK](../../includes/clickok-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="82a8c-134">On the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed, click **Start**, click **Run**, type `cmd` and then [!INCLUDE[clickOK](../../includes/clickok-md.md)].</span></span>  
  
2.  <span data-ttu-id="82a8c-135">在 [命令提示字元] 視窗中，輸入 `ipconfig,`，然後按下 ENTER，即可列出這部電腦可用的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="82a8c-135">In the Command Prompt window, type `ipconfig,` and then press ENTER to list the IP addresses available on this computer.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="82a8c-136">**ipconfig** 命令有時會列出許多可能的連結，包含已中斷連線的連結。</span><span class="sxs-lookup"><span data-stu-id="82a8c-136">The **ipconfig** command sometimes lists many possible connections, including connections that are disconnected.</span></span> <span data-ttu-id="82a8c-137">**ipconfig** 命令可以同時列出 IPv4 及 IPv6 的位址。</span><span class="sxs-lookup"><span data-stu-id="82a8c-137">The **ipconfig** command can list both IPv4 and IPv6 addresses.</span></span>  
  
3.  <span data-ttu-id="82a8c-138">請記下所使用的 IPv4 位址和 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="82a8c-138">Note the IPv4 addresses and IPv6 addresses that are being used.</span></span> <span data-ttu-id="82a8c-139">清單中的其他資訊 (例如暫時位址、子網路遮罩和預設閘道器) 都是設定 TCP/IP 網路的重要資訊。</span><span class="sxs-lookup"><span data-stu-id="82a8c-139">The other information in the list, such as temporary addresses, subnet masks, and default gateways is important information for configuring a TCP/IP network.</span></span> <span data-ttu-id="82a8c-140">不過，這則範例不會使用這項資訊。</span><span class="sxs-lookup"><span data-stu-id="82a8c-140">But this information is not used in this example.</span></span>  
  
#### <a name="to-determine-the-ip-addresses-and-ports-used-by-ssnoversion"></a><span data-ttu-id="82a8c-141">判斷使用的 IP 位址和連接埠 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82a8c-141">To determine the IP addresses and ports used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="82a8c-142">按一下 [開始] 並依序指向 [所有程式]、[[!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]] 和 [組態工具]，然後按一下 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員]。</span><span class="sxs-lookup"><span data-stu-id="82a8c-142">Click **Start**, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="82a8c-143">在\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager**的主控台窗格中，展開 [ \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 網路**設定]，展開 [\*\*通訊協定 \<instance name> \*\*]，然後按兩下 [ **tcp/ip**]。</span><span class="sxs-lookup"><span data-stu-id="82a8c-143">In **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager**, in the console pane, expand **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Network Configuration**, expand **Protocols for \<instance name>**, and then double-click **TCP/IP**.</span></span>  
  
3.  <span data-ttu-id="82a8c-144">在 [TCP/IP 內容]  對話方塊的 [IP 位址]  索引標籤上會出現數個 IP 位址，這些 IP 位址的格式是 **IP1**、**IP2** 到 **IPAll**。</span><span class="sxs-lookup"><span data-stu-id="82a8c-144">In the **TCP/IP Properties** dialog box, on the **IP Addresses** tab, several IP addresses appear in the format **IP1**, **IP2**, up to **IPAll**.</span></span> <span data-ttu-id="82a8c-145">其中一個是供回送介面卡的 IP 位址 127.0.0.1 使用。</span><span class="sxs-lookup"><span data-stu-id="82a8c-145">One of these is for the IP address of the loopback adapter, 127.0.0.1.</span></span> <span data-ttu-id="82a8c-146">此時會出現額外的 IP 位址，代表電腦上設定的每個 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="82a8c-146">Additional IP addresses appear for each IP Address configured on the computer.</span></span>  
  
4.  <span data-ttu-id="82a8c-147">對於任何 IP 位址而言，如果 [TCP 動態通訊埠]  對話方塊包含 **0**，這就表示 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 正在接聽動態連接埠。</span><span class="sxs-lookup"><span data-stu-id="82a8c-147">For any IP address if the **TCP Dynamic Ports** dialog box contains **0**, this indicates that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is listening on dynamic ports.</span></span> <span data-ttu-id="82a8c-148">這則範例會使用固定通訊埠來取代可能會在重新啟動時變更的動態通訊埠。</span><span class="sxs-lookup"><span data-stu-id="82a8c-148">This example uses fixed ports instead of dynamic ports which could change upon restart.</span></span> <span data-ttu-id="82a8c-149">因此，如果 [TCP 動態通訊埠]  對話方塊包含 **0**，請刪除 0。</span><span class="sxs-lookup"><span data-stu-id="82a8c-149">Therefore if the **TCP Dynamic Ports** dialog box contains **0**, delete the 0.</span></span>  
  
5.  <span data-ttu-id="82a8c-150">請記下針對您想要設定之每個 IP 位址所列出的 TCP 通訊埠。</span><span class="sxs-lookup"><span data-stu-id="82a8c-150">Note the TCP port that is listed for each IP address that you want to configure.</span></span> <span data-ttu-id="82a8c-151">在這則範例中，請假設兩個 IP 位址都在接聽預設通訊埠 1433。</span><span class="sxs-lookup"><span data-stu-id="82a8c-151">For this example, assume that both IP addresses are listening on the default port, 1433.</span></span>  
  
6.  <span data-ttu-id="82a8c-152">如果您不想要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用某些可用的連接埠，請在 [通訊協定]  索引標籤中，將 [全部接聽]  值變更為 [否]  。然後，在 [IP 位址]  索引標籤中，針對您不想要使用的 IP 位址，將 [使用中]  值變更為 [否]  。</span><span class="sxs-lookup"><span data-stu-id="82a8c-152">If you do not want [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use some of the available ports, on the **Protocol** tab, change the **Listen All** value to **No**; and on the **IP Addresses** tab, change the **Active** value to **No** for the IP addresses that you do not want to use.</span></span>  
  
## <a name="configuring-windows-firewall-with-advanced-security"></a><span data-ttu-id="82a8c-153">設定具有進階安全性的 Windows 防火牆</span><span class="sxs-lookup"><span data-stu-id="82a8c-153">Configuring Windows Firewall with Advanced Security</span></span>  
 <span data-ttu-id="82a8c-154">在您知道電腦所使用的 IP 位址以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所使用的通訊埠之後，就可以建立防火牆規則，然後針對特定的 IP 位址設定這些規則。</span><span class="sxs-lookup"><span data-stu-id="82a8c-154">After you know the IP addresses that the computer uses and the ports that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses, you can create firewall rules, and then configure those rules for specific IP addresses.</span></span>  
  
#### <a name="to-create-a-firewall-rule"></a><span data-ttu-id="82a8c-155">若要建立防火牆規則</span><span class="sxs-lookup"><span data-stu-id="82a8c-155">To create a firewall rule</span></span>  
  
1.  <span data-ttu-id="82a8c-156">在安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的電腦上，以管理員身分登入。</span><span class="sxs-lookup"><span data-stu-id="82a8c-156">On the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed, log on as an administrator..</span></span>  
  
2.  <span data-ttu-id="82a8c-157">依序按一下 [**開始**] 和 [**執行**]，輸入 `wf.msc` ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="82a8c-157">Click **Start**, click **Run**, type `wf.msc`, and click **OK**.</span></span>  
  
3.  <span data-ttu-id="82a8c-158">在 [使用者帳戶控制]  對話方塊中，按一下 [繼續]  ，即可使用管理員認證來開啟 [具有進階安全性的 Windows 防火牆] 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="82a8c-158">In the **User Account Control** dialog box, click **Continue** to use the Administrator credentials to open the Windows Firewall with Advanced Security snap-in.</span></span>  
  
4.  <span data-ttu-id="82a8c-159">在 [概觀]  頁面上，確認 Windows 防火牆已啟用。</span><span class="sxs-lookup"><span data-stu-id="82a8c-159">On the **Overview** page, confirm that the Windows Firewall is enabled.</span></span>  
  
5.  <span data-ttu-id="82a8c-160">在左窗格中，按一下 [輸入規則]  。</span><span class="sxs-lookup"><span data-stu-id="82a8c-160">In the left pane, click **Inbound Rules**.</span></span>  
  
6.  <span data-ttu-id="82a8c-161">以滑鼠右鍵按一下 [輸入規則]  ，然後按一下 [新增規則]  以開啟 [新增輸入規則精靈]  。</span><span class="sxs-lookup"><span data-stu-id="82a8c-161">Right-click **Inbound Rules**, and then click **New Rule** to open the **New Inbound Rule Wizard**.</span></span>  
  
7.  <span data-ttu-id="82a8c-162">您可以針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 程式建立規則。</span><span class="sxs-lookup"><span data-stu-id="82a8c-162">You could create a rule for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] program.</span></span> <span data-ttu-id="82a8c-163">不過，因為這則範例使用固定通訊埠，所以請選取 [連接埠]  ，然後按 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="82a8c-163">However, because this example uses a fixed port, select **Port**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="82a8c-164">在 [通訊協定及連接埠]  頁面上，選取 [TCP]  。</span><span class="sxs-lookup"><span data-stu-id="82a8c-164">On the **Protocols and Ports** page, select **TCP**.</span></span>  
  
9. <span data-ttu-id="82a8c-165">選取 [特定本機連接埠]  。</span><span class="sxs-lookup"><span data-stu-id="82a8c-165">Select **Specified local ports**.</span></span> <span data-ttu-id="82a8c-166">輸入以逗號隔開的通訊埠編號，然後按 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="82a8c-166">Type the port numbers separated by commas, and then click **Next**.</span></span> <span data-ttu-id="82a8c-167">在這則範例中，您將設定預設通訊埠。因此，請輸入 `1433`。</span><span class="sxs-lookup"><span data-stu-id="82a8c-167">In this example, you will configure the default port; therefore, enter `1433`.</span></span>  
  
10. <span data-ttu-id="82a8c-168">在 [動作]  頁面上，檢閱這些選項。</span><span class="sxs-lookup"><span data-stu-id="82a8c-168">On the **Action** page, review the options.</span></span> <span data-ttu-id="82a8c-169">在這則範例中，您不會使用防火牆來強制執行安全連接。</span><span class="sxs-lookup"><span data-stu-id="82a8c-169">In this example, you are not using the firewall to force secure connections.</span></span> <span data-ttu-id="82a8c-170">因此，請按一下 [允許該連線]  ，然後按 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="82a8c-170">Therefore, click **Allow the connection**, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="82a8c-171">您的環境可能需要使用安全連接。</span><span class="sxs-lookup"><span data-stu-id="82a8c-171">Your environment might require secure connections.</span></span> <span data-ttu-id="82a8c-172">如果您選取其中一個安全連接選項，可能必須設定憑證和 [強制加密]  選項。</span><span class="sxs-lookup"><span data-stu-id="82a8c-172">If you select one of the secure connections options, you might have to configure a certificate and the **Force Encryption** option.</span></span> <span data-ttu-id="82a8c-173">如需安全連線的詳細資訊，請參閱[啟用 Database Engine 的加密連接 &#40;SQL Server 組態管理員&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) 和[啟用 Database Engine 的加密連接 &#40;SQL Server 組態管理員&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="82a8c-173">For more information about secure connections, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) and [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span>  
  
11. <span data-ttu-id="82a8c-174">在 [設定檔]  頁面上，針對此規則選取一個或多個設定檔。</span><span class="sxs-lookup"><span data-stu-id="82a8c-174">On the **Profile** page, select one or more profiles for the rule.</span></span> <span data-ttu-id="82a8c-175">如果您不熟悉防火牆設定檔，請按一下防火牆程式中的 [深入了解設定檔]  連結。</span><span class="sxs-lookup"><span data-stu-id="82a8c-175">If you are unfamiliar with firewall profiles, click the **Learn more about profiles** link in the firewall program.</span></span>  
  
    -   <span data-ttu-id="82a8c-176">如果此電腦是伺服器，而且只有在連接至網域時才能使用，請選取 [網域]  ，然後按 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="82a8c-176">If the computer is a server and is available only when it is connected to a domain, select **Domain**, and then click **Next**.</span></span>  
  
    -   <span data-ttu-id="82a8c-177">如果此電腦是行動式電腦 (例如，筆記型電腦)，當它連接至不同的網路時，可能會使用多個設定檔。</span><span class="sxs-lookup"><span data-stu-id="82a8c-177">If the computer is a mobile computer (for example a laptop), it is likely to use multiple profiles when it connects to different networks.</span></span> <span data-ttu-id="82a8c-178">若為行動式電腦，您可以針對不同的設定檔設定不同的存取功能。</span><span class="sxs-lookup"><span data-stu-id="82a8c-178">For a mobile computer, you can configure different access capabilities for different profiles.</span></span> <span data-ttu-id="82a8c-179">例如，您可能會在電腦使用網域設定檔時允許存取，但在它使用公用設定檔時拒絕存取。</span><span class="sxs-lookup"><span data-stu-id="82a8c-179">For example, you might allow access when the computer uses the Domain profile but not allow access when it uses the Public profile.</span></span>  
  
12. <span data-ttu-id="82a8c-180">在 [名稱]  頁面上，針對此規則提供名稱和描述，然後按一下 [完成]  。</span><span class="sxs-lookup"><span data-stu-id="82a8c-180">On the **Name** page, provide a name and description for the rule, and then click **Finish**.</span></span>  
  
13. <span data-ttu-id="82a8c-181">重複這項程序，以便針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 即將使用的每個 IP 位址建立其他規則。</span><span class="sxs-lookup"><span data-stu-id="82a8c-181">Repeat this procedure to create another rule for each IP address that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will use.</span></span>  
  
 <span data-ttu-id="82a8c-182">在您已經建立一項或多項規則之後，請執行下列步驟，將電腦上的每個 IP 位址都設定成使用規則。</span><span class="sxs-lookup"><span data-stu-id="82a8c-182">After you have created one or more rules, perform the following steps to configure each IP address on the computer to use a rule.</span></span>  
  
#### <a name="to-configure-the-firewall-rule-for-a-specific-ip-addresses"></a><span data-ttu-id="82a8c-183">若要針對特定的 IP 位址設定防火牆規則</span><span class="sxs-lookup"><span data-stu-id="82a8c-183">To configure the firewall rule for a specific IP addresses</span></span>  
  
1.  <span data-ttu-id="82a8c-184">在 [具有進階安全性的 Windows 防火牆] 的 [輸入規則] 頁面上，以滑鼠右鍵按一下您剛建立的規則，然後按一下 [內容]。</span><span class="sxs-lookup"><span data-stu-id="82a8c-184">On the **Inbound Rules** page of the **Windows Firewall with Advanced Security**, right-click the rule that you just created, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="82a8c-185">在 [規則內容]  對話方塊中，選取 [範圍]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="82a8c-185">In the **Rule Properties** dialog box, select the **Scope** tab.</span></span>  
  
3.  <span data-ttu-id="82a8c-186">在 [本機 IP 位址]  區域中，選取 [這些 IP 位址]  ，然後按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="82a8c-186">In the **Local IP address** area, select **These IP addresses**, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="82a8c-187">在 [IP 位址]  對話方塊中，選取 [此 IP 位址或子網路]  ，然後輸入您想要設定的其中一個 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="82a8c-187">In the **IP Address** dialog box, select **This IP address or subnet**, and then type one of the IP addresses that you want to configure.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="82a8c-188">在 [遠端 IP 位址]  區域中，選取 [這些 IP 位址]  ，然後按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="82a8c-188">In the **Remote IP address** area, select **These IP addresses**, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="82a8c-189">您可以使用 [IP 位址]  對話方塊，針對電腦上選取的 IP 位址設定連接性。</span><span class="sxs-lookup"><span data-stu-id="82a8c-189">Use the **IP Address** dialog box to configure connectivity for the selected IP address on the computer.</span></span> <span data-ttu-id="82a8c-190">您可以啟用來自指定之 IP 位址、IP 位址範圍、整個子網路或特定電腦的連接。</span><span class="sxs-lookup"><span data-stu-id="82a8c-190">You can enable connections from specified IP addresses, ranges of IP addresses, whole subnets, or from certain computers.</span></span> <span data-ttu-id="82a8c-191">若要正確設定這個選項，您必須充分了解網路。</span><span class="sxs-lookup"><span data-stu-id="82a8c-191">To configure this option correctly, you must have a good understanding of the network.</span></span> <span data-ttu-id="82a8c-192">如需有關網路的詳細資訊，請洽詢網路管理員。</span><span class="sxs-lookup"><span data-stu-id="82a8c-192">For information about the network, see the network administrator.</span></span>  
  
8.  <span data-ttu-id="82a8c-193">若要關閉 [IP 位址]  對話方塊，請按一下 [確定]  。然後，按一下 [確定]  關閉 [規則內容]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="82a8c-193">To close the **IP Address** dialog box, click **OK**; and then click **OK** to close the **Rule Properties** dialog box.</span></span>  
  
9. <span data-ttu-id="82a8c-194">若要在多重主目錄電腦上設定其他 IP 位址，請使用其他 IP 位址和其他規則來重複這項程序。</span><span class="sxs-lookup"><span data-stu-id="82a8c-194">To configure the other IP addresses on a multi-homed computer, repeat this procedure by using another IP address and another rule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82a8c-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82a8c-195">See Also</span></span>  
 <span data-ttu-id="82a8c-196">[SQL Server Browser 服務 &#40;Database Engine 和 SSAS&#41;](../../database-engine/configure-windows/sql-server-browser-service-database-engine-and-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="82a8c-196">[SQL Server Browser Service &#40;Database Engine and SSAS&#41;](../../database-engine/configure-windows/sql-server-browser-service-database-engine-and-ssas.md) </span></span>  
 [<span data-ttu-id="82a8c-197">經由 Proxy 伺服器連接至 SQL Server &#40;SQL Server 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="82a8c-197">Connect to SQL Server Through a Proxy Server &#40;SQL Server Configuration Manager&#41;</span></span>](../../relational-databases/sql-server-configuration-manager.md)  
  
  
