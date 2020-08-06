---
title: 使用 IPv6 連接 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Internet Protocol
- IPv4
- IPv6
ms.assetid: 2669098c-f5f1-43da-aec6-e91003ac89f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0f2ecd605f67446fade262cfe795f344dfb165c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704586"
---
# <a name="connecting-using-ipv6"></a><span data-ttu-id="69b3c-102">使用 IPv6 連接</span><span class="sxs-lookup"><span data-stu-id="69b3c-102">Connecting Using IPv6</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="69b3c-103">和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 完整支援網際網路通訊協定第 4 版 (IPv4) 與網際網路通訊協定第 6 版 (IPv6)。</span><span class="sxs-lookup"><span data-stu-id="69b3c-103">and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client fully support both Internet Protocol version 4 (IPv4) and Internet Protocol version 6 (IPv6).</span></span> <span data-ttu-id="69b3c-104">當 Windows 是設定為 IPv6 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]時，元件會自動辨識 IPv6 的存在性。</span><span class="sxs-lookup"><span data-stu-id="69b3c-104">When Windows is configured with IPv6 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], components automatically recognize the existence of IPv6.</span></span> <span data-ttu-id="69b3c-105">不需要特殊的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態。</span><span class="sxs-lookup"><span data-stu-id="69b3c-105">No special [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configuration is necessary.</span></span>  
  
 <span data-ttu-id="69b3c-106">支援包括但不限於下列各項：</span><span class="sxs-lookup"><span data-stu-id="69b3c-106">Support includes but is not limited to the following:</span></span>  
  
-   <span data-ttu-id="69b3c-107">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 和其他伺服器元件可同時接聽 IPv4 和 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="69b3c-107">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and the other server components can listen on both IPv4 and IPv6 addresses at the same time.</span></span> <span data-ttu-id="69b3c-108">當 IPv4 和 IPv6 都出現時，您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員，來設定 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 只接聽 IPv4 位址或 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="69b3c-108">When both IPv4 and IPv6 are present, you can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to configure the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen only on IPv4 addresses or only on IPv6 addresses.</span></span>  
  
-   <span data-ttu-id="69b3c-109">當支援 IPv4 和 IPv6 的電腦上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務是在 IPv4 位址上接受查詢時，它的回應是將 IPv4 位址及第一個 IPv4 TCP 通訊埠列在其清單中。</span><span class="sxs-lookup"><span data-stu-id="69b3c-109">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service running on a machine that supports both IPv4 and IPv6 is queried on an IPv4 address, it responds with an IPv4 address and the first IPv4 TCP port in its list.</span></span> <span data-ttu-id="69b3c-110">在 IPv6 位址上接受查詢時，它的回應是將 IPv6 位址及第一個 IPv6 TCP 通訊埠列在其清單中。</span><span class="sxs-lookup"><span data-stu-id="69b3c-110">When queried on an IPv6 address, it responds with an IPv6 address and the first IPv6 TCP port in its list.</span></span> <span data-ttu-id="69b3c-111">若要避免不一致，我們建議 IPv4 和 IPv6 接聽程式設定為接聽相同通訊埠。</span><span class="sxs-lookup"><span data-stu-id="69b3c-111">To avoid inconsistency, we recommend that the IPv4 and IPv6 listeners be configured to listen to the same port.</span></span>  
  
-   <span data-ttu-id="69b3c-112">像 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員之類的工具接受 IPv4 和 IPv6 格式的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="69b3c-112">Tools such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager accept both IPv4 and IPv6 formats for IP addresses.</span></span> <span data-ttu-id="69b3c-113">在大多數情況下，如果 \<*computer_name*> \\ < 使用伺服器主機名稱或完整功能變數名稱 (FQDN) 來指定*instance_name*>，則不需要修改連接字串。</span><span class="sxs-lookup"><span data-stu-id="69b3c-113">In most cases, the connection string does not need to be modified if the \<*computer_name*>\\<*instance_name*> is specified using server hostname or fully qualified domain name (FQDN).</span></span> <span data-ttu-id="69b3c-114">如果伺服器電腦有 IPv4 和 IPv6，其主機名稱或 FQDN 將解析成多個 IP 位址，包括至少一個 IPv4 位址及多個 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="69b3c-114">If the server computer has both IPv4 and IPv6, its hostname or FQDN will be resolved into multiple IP addresses, including at least one IPv4 address and multiple IPv6 addresses.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="69b3c-115">Native Client 嘗試依照從 TCP/IP 接收的順序來使用這些 IP 位址建立連線，以及使用第一個成功的連線。</span><span class="sxs-lookup"><span data-stu-id="69b3c-115">Native Client attempts to establish connections using these IP addresses in the order received from TCP/IP and uses the first connection that succeeds.</span></span> <span data-ttu-id="69b3c-116">由於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 無法預測順序，因此，這應該被視為隨機順序。</span><span class="sxs-lookup"><span data-stu-id="69b3c-116">Because the order cannot be predicted by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, this should be regarded as random order.</span></span> <span data-ttu-id="69b3c-117">如果 IPv4 和 IPv6 位址都出現，則先嘗試使用 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="69b3c-117">IPv4 addresses are attempted first if both IPv4 and IPv6 addresses are present.</span></span> <span data-ttu-id="69b3c-118">此邏輯對 ODBC、OLE DB 或 ADO.NET 的使用者是透明化的。</span><span class="sxs-lookup"><span data-stu-id="69b3c-118">This logic is transparent to the users of ODBC, OLE DB, or ADO.NET.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="69b3c-119">如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 未接聽 IPv4，在嘗試使用 IPv6 位址之前，嘗試建立的 IPv4 連接必須等到逾時。</span><span class="sxs-lookup"><span data-stu-id="69b3c-119">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is not listening on IPv4, the attempted IPv4 connection must wait for the time-out period before the IPv6 address is attempted.</span></span> <span data-ttu-id="69b3c-120">若要避免發生此情形，請直接連接到 IPv6 IP 位址，或在具有 IPv6 位址的用戶端上設定別名。</span><span class="sxs-lookup"><span data-stu-id="69b3c-120">To avoid this, connect directly to the IPv6 IP address or configure an alias on the client with the IPv6 address.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b3c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69b3c-121">See Also</span></span>  
 [<span data-ttu-id="69b3c-122">SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="69b3c-122">SQL Server Configuration Manager</span></span>](../../relational-databases/sql-server-configuration-manager.md)  
  
  
