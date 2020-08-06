---
title: 設定用戶端通訊協定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default protocols
- network protocols [SQL Server], client configuration
- TCP/IP [SQL Server], client protocols
- disabling client protocols
- ordering protocols [SQL Server]
- protocols [SQL Server], order for client computers
- configure client protocols
- client protocols [SQL Server]
- protocols [SQL Server], client configuration
ms.assetid: 3dfa2702-ba65-43b4-a777-6727846e133a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2eb223815c3e3af50813e02d3ded60573c327155
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607098"
---
# <a name="configure-client-protocols"></a><span data-ttu-id="97f5d-102">設定用戶端通訊協定</span><span class="sxs-lookup"><span data-stu-id="97f5d-102">Configure Client Protocols</span></span>
  <span data-ttu-id="97f5d-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 組態管理員，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中設定用戶端應用程式所使用的用戶端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="97f5d-103">This topic describes how to configure client protocols used by client applications in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="97f5d-104">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援使用 TCP/IP 網路通訊協定和具名管道通訊協定來進行用戶端通訊。</span><span class="sxs-lookup"><span data-stu-id="97f5d-104">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports client communication with the TCP/IP network protocol and the named pipes protocol.</span></span> <span data-ttu-id="97f5d-105">如果用戶端是連接到同一部電腦上的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體，也可以使用共用記憶體通訊協定。</span><span class="sxs-lookup"><span data-stu-id="97f5d-105">The shared memory protocol is also available if the client is connecting to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the same computer.</span></span> <span data-ttu-id="97f5d-106">選取通訊協定有三種常見的方法。</span><span class="sxs-lookup"><span data-stu-id="97f5d-106">There are three common methods of selecting the protocol.</span></span>  
  
-   <span data-ttu-id="97f5d-107">您可以在「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」中設定通訊協定順序，來設定所有用戶端應用程式使用相同的網路通訊協定。</span><span class="sxs-lookup"><span data-stu-id="97f5d-107">Configure all client applications to use the same network protocol by setting the protocol order in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
-   <span data-ttu-id="97f5d-108">藉由建立別名，您可以設定單一用戶端應用程式使用不同的網路通訊協定。</span><span class="sxs-lookup"><span data-stu-id="97f5d-108">Configure a single client application to use a different network protocol by creating an alias.</span></span> <span data-ttu-id="97f5d-109">如需詳細資訊，請參閱[建立或刪除用戶端使用的伺服器別名 &#40;SQL Server Configuration Manager&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md)。</span><span class="sxs-lookup"><span data-stu-id="97f5d-109">For more information, see [Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md).</span></span>  
  
-   <span data-ttu-id="97f5d-110">有些用戶端應用程式 (如 sqlcmd.exe) 可以指定通訊協定做為連接字串的一部分。</span><span class="sxs-lookup"><span data-stu-id="97f5d-110">Some client applications, such as sqlcmd.exe, can specify the protocol as part of the connection string.</span></span> <span data-ttu-id="97f5d-111">如需詳細資訊，請參閱[使用 sqlcmd 連接至 Database Engine](../../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="97f5d-111">For more information, see [Connect to the Database Engine With sqlcmd](../../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md).</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="97f5d-112">使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="97f5d-112">Using SQL Server Configuration Manager</span></span>  
  
###  <a name="to-enable-or-disable-a-client-protocol"></a><a name="EnableDisable"></a> <span data-ttu-id="97f5d-113">啟用或停用用戶端通訊協定</span><span class="sxs-lookup"><span data-stu-id="97f5d-113">To enable or disable a client protocol</span></span>  
  
1.  <span data-ttu-id="97f5d-114">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員中，展開 [SQL Server Native Client Configuration (SQL Server Native Client 組態)]，並以滑鼠右鍵按一下 [用戶端通訊協定]，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="97f5d-114">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Native Client Configuration**, right-click **Client Protocols**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="97f5d-115">在 **[停用的通訊協定]** 方塊中按一下某通訊協定，再按一下 **[啟用]** ，即可啟用通訊協定。</span><span class="sxs-lookup"><span data-stu-id="97f5d-115">Click a protocol in the **Disabled Protocols** box, and then click **Enable**, to enable a protocol.</span></span>  
  
3.  <span data-ttu-id="97f5d-116">在 **[啟用的通訊協定]** 方塊中按一下某通訊協定，再按一下 **[停用]** ，即可停用通訊協定。</span><span class="sxs-lookup"><span data-stu-id="97f5d-116">Click a protocol in the **Enabled Protocols** box, and then click **Disable**, to disable a protocol.</span></span>  
  
###  <a name="to-change-the-default-protocol-or-the-protocol-order-for-client-computers"></a><a name="ChangeDefault"></a> <span data-ttu-id="97f5d-117">變更用戶端電腦的預設通訊協定或通訊協定順序</span><span class="sxs-lookup"><span data-stu-id="97f5d-117">To change the default protocol or the protocol order for client computers</span></span>  
  
1.  <span data-ttu-id="97f5d-118">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員中，展開 [SQL Server Native Client Configuration (SQL Server Native Client 組態)]，並以滑鼠右鍵按一下 [用戶端通訊協定]，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="97f5d-118">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Native Client Configuration**, right-click **Client Protocols**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="97f5d-119">在 **[啟用的通訊協定]** 方塊中，按一下 **[上移]** 或 **[下移]** ，來變更要連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]時使用通訊協定的順序。</span><span class="sxs-lookup"><span data-stu-id="97f5d-119">In the **Enabled Protocols** box, click **Move Up** or **Move Down**, to change the order in which protocols are tried, when attempting to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="97f5d-120">**[啟用的通訊協定]** 方塊裡最上方的通訊協定，是預設通訊協定。</span><span class="sxs-lookup"><span data-stu-id="97f5d-120">The top protocol in the **Enabled Protocols** box is the default protocol.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="97f5d-121">「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」會為伺服器別名組態與預設用戶端網路程式庫建立登錄項目。</span><span class="sxs-lookup"><span data-stu-id="97f5d-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager creates registry entries for the server alias configurations and default client network library.</span></span> <span data-ttu-id="97f5d-122">然而，應用程式並不會安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端網路程式庫或網路通訊協定。</span><span class="sxs-lookup"><span data-stu-id="97f5d-122">However, the application does not install either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client network libraries or the network protocols.</span></span> <span data-ttu-id="97f5d-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端網路程式庫是在安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時安裝；網路通訊協定是在安裝 Microsoft Windows 時安裝 (或透過 [控制台] 中的 [網路] 安裝)。</span><span class="sxs-lookup"><span data-stu-id="97f5d-123">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client network libraries are installed during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup; the network protocols are installed as part of Microsoft Windows Setup (or through **Networks** in **Control Panel**).</span></span> <span data-ttu-id="97f5d-124">某些特定網路通訊協定可能不會隨 Windows 安裝。</span><span class="sxs-lookup"><span data-stu-id="97f5d-124">A particular network protocol may not be available as part of Windows Setup.</span></span> <span data-ttu-id="97f5d-125">如需有關安裝這些網路通訊協定的詳細資訊，請參閱供應商說明文件。</span><span class="sxs-lookup"><span data-stu-id="97f5d-125">For more information about installing these network protocols, see the vendor documentation.</span></span>  
  
###  <a name="to-configure-a-client-to-use-tcpip"></a><a name="Configure"></a> <span data-ttu-id="97f5d-126">設定用戶端使用 TCP/IP</span><span class="sxs-lookup"><span data-stu-id="97f5d-126">To configure a client to use TCP/IP</span></span>  
  
1.  <span data-ttu-id="97f5d-127">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員中，展開 [SQL Server Native Client Configuration (SQL Server Native Client 組態)]，並以滑鼠右鍵按一下 [用戶端通訊協定]，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="97f5d-127">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Native Client Configuration**, right-click **Client Protocols**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="97f5d-128">請在 **[啟用的通訊協定]** 方塊中，按一下向上箭號與向下箭號，以便在嘗試連接 SQL Server 時變更通訊協定的順序。</span><span class="sxs-lookup"><span data-stu-id="97f5d-128">In the **Enabled Protocols** box, click the up and down arrows to change the order in which protocols are tried, when attempting to connect to SQL Server.</span></span> <span data-ttu-id="97f5d-129">**[啟用的通訊協定]** 方塊裡最上方的通訊協定，是預設通訊協定。</span><span class="sxs-lookup"><span data-stu-id="97f5d-129">The top protocol in the **Enabled Protocols** box is the default protocol.</span></span>  
  
 <span data-ttu-id="97f5d-130">您可以勾選 **[啟用共用記憶體通訊協定]** 方塊來個別啟用共用記憶體通訊協定。</span><span class="sxs-lookup"><span data-stu-id="97f5d-130">The shared memory protocol is enabled separately by checking the **Enabled Shared Memory Protocol** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97f5d-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97f5d-131">See Also</span></span>  
 [<span data-ttu-id="97f5d-132">設定遠端登入逾時伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="97f5d-132">Configure the remote login timeout Server Configuration Option</span></span>](configure-the-remote-login-timeout-server-configuration-option.md)  
  
  
