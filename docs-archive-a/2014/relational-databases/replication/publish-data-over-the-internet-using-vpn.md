---
title: 使用 VPN 透過網際網路發行資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- VPNs [SQL Server replication]
- Web publishing [SQL Server replication], VPNs
- Internet [SQL Server replication], VPNs
ms.assetid: 9ffb6546-9973-4574-aaa0-8fe0017e3601
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7a477e70031053a9563c2f3ed3740091d632febe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606771"
---
# <a name="publish-data-over-the-internet-using-vpn"></a><span data-ttu-id="81744-102">使用 VPN 透過網際網路發行資料</span><span class="sxs-lookup"><span data-stu-id="81744-102">Publish Data over the Internet Using VPN</span></span>
  <span data-ttu-id="81744-103">虛擬私人網路 (Virtual Private Networking，VPN) 技術可以讓使用者在家裏、分公司辦公室、遠端用戶端以及其他公司透過網際網路連接到公司網路進行工作，同時保有安全的通訊。</span><span class="sxs-lookup"><span data-stu-id="81744-103">Virtual Private Networking (VPN) technology allows users working at home, branch offices, remote clients, and other companies to connect to a corporate network over the Internet, while maintaining secure communications.</span></span> <span data-ttu-id="81744-104">使用者可以使用「Windows 驗證」(Windows Authentication)，就好像他們是在區域網路 (Area Network，LAN) 一樣。</span><span class="sxs-lookup"><span data-stu-id="81744-104">Users can use Windows Authentication as though they were on a Local Area Network (LAN).</span></span> <span data-ttu-id="81744-105">所有類型的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複寫都可以透過 VPN 複寫資料，但如果您使用合併式複寫，請考慮使用 Web 同步處理，因為 Web 同步處理會省去使用 VPN 的需求。</span><span class="sxs-lookup"><span data-stu-id="81744-105">All types of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication can replicate data over a VPN, but consider using Web synchronization if you are using merge replication, because Web synchronization eliminates the need for a VPN.</span></span> <span data-ttu-id="81744-106">如需詳細資訊，請參閱＜ [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md)＞。</span><span class="sxs-lookup"><span data-stu-id="81744-106">For more information, see [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md).</span></span>  
  
 <span data-ttu-id="81744-107">VPN 包含用戶端軟體，因此電腦可以透過網際網路 (在某些特殊情況下，甚至是內部網路) 連接到專用電腦或伺服器中的軟體。</span><span class="sxs-lookup"><span data-stu-id="81744-107">A VPN includes client software so that computers connect over the Internet (or in special cases, even an intranet) to software in a dedicated computer or a server.</span></span> <span data-ttu-id="81744-108">也可以選擇對連線兩端加密及使用者驗證方法。</span><span class="sxs-lookup"><span data-stu-id="81744-108">Optionally, encryption at both ends, as well as user authentication methods, are used.</span></span> <span data-ttu-id="81744-109">透過網際網路的 VPN 連接在邏輯上的操作類似站台之間的「廣域網路」(WAN) 連結。</span><span class="sxs-lookup"><span data-stu-id="81744-109">The VPN connection over the Internet logically operates as a Wide Area Network (WAN) link between the sites.</span></span>  
  
 <span data-ttu-id="81744-110">VPN 透過另一個網路來連接其網路元件。</span><span class="sxs-lookup"><span data-stu-id="81744-110">A VPN connects the components of a network using another network.</span></span> <span data-ttu-id="81744-111">若要進行連接，使用者可使用如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Point-to-Point Tunneling Protocol (PPTP) 或 Layer Two Tunneling Protocol (L2TP) 之類的通訊協定穿過網際網路或其他共用網路。</span><span class="sxs-lookup"><span data-stu-id="81744-111">To connect, the user tunnels through the Internet or another public network using a protocol such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Point-to-Point Tunneling Protocol (PPTP) or Layer Two Tunneling Protocol (L2TP).</span></span> <span data-ttu-id="81744-112">這一程序提供的安全性和功能，與先前只能在私人網路使用的安全性和功能相同。</span><span class="sxs-lookup"><span data-stu-id="81744-112">This process provides the same security and features previously available only in a private network.</span></span> <span data-ttu-id="81744-113">PPTP 在 Microsoft Windows NT 4.0 版和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 (及更新版本) 作業系統中有提供；L2TP 在 Windows 2000 及更新版本中有提供。</span><span class="sxs-lookup"><span data-stu-id="81744-113">PPTP is available with the Microsoft Windows NT version 4.0 and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 (and later) operating systems; L2TP is available with Windows 2000 and later.</span></span>  
  
 <span data-ttu-id="81744-114">使用者看不到網際網路的中間路由基礎結構，資料像是透過專用私人連結來傳送一樣。</span><span class="sxs-lookup"><span data-stu-id="81744-114">For the user, the intermediate routing infrastructure of the Internet is not visible and it appears as though the data is being sent over a dedicated private link.</span></span> <span data-ttu-id="81744-115">就使用者而言，VPN 是使用者電腦和公司伺服器之間的點對點連線。</span><span class="sxs-lookup"><span data-stu-id="81744-115">As far as users are concerned, the VPN is a point-to-point connection between the user computer and a corporate server.</span></span>  
  
 <span data-ttu-id="81744-116">當您將遠端用戶端設定成使用 VPN 連接，而且用戶端可以存取 Internet 並已登入公司區域網路時，您可以設定複寫，就好像遠端用戶端是直接在 LAN (區域網路) 一樣。</span><span class="sxs-lookup"><span data-stu-id="81744-116">After you have your remote client configured to connect using a VPN, and the client has Internet access and is logged in to the corporate LAN, you can configure replication as though the remote client is connected directly on the LAN.</span></span> <span data-ttu-id="81744-117">基於安全因素，可以讓不同的網路資源供透過 VPN 連接的使用者，以及供直接連接到 LAN (區域網路) 的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="81744-117">For security reasons, it is possible to have different network resources available to users connected over VPN and to those connected directly on the LAN.</span></span>  
  
 <span data-ttu-id="81744-118">如需有關設定 VPN 的詳細資訊，請參閱 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="81744-118">For more information about setting up a VPN, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81744-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81744-119">See Also</span></span>  
 [<span data-ttu-id="81744-120">透過網際網路的複寫</span><span class="sxs-lookup"><span data-stu-id="81744-120">Replication over the Internet</span></span>](replication-over-the-internet.md)  
  
  
