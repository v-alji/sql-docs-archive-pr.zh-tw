---
title: 保護透過網際網路的複寫 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server replication], Internet
- Internet [SQL Server replication], security
ms.assetid: 25b7af05-2721-4b24-9083-fb671e8bf4e0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 47408b2b9559d33da4563c6fc9560d20338ee01d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708166"
---
# <a name="securing-replication-over-the-internet"></a><span data-ttu-id="e5618-102">Securing Replication Over the Internet</span><span class="sxs-lookup"><span data-stu-id="e5618-102">Securing Replication Over the Internet</span></span>
  <span data-ttu-id="e5618-103">網際網路複寫可以提供彈性，特別是對於行動訂閱者，但是您必須正確設定網際網路複寫以保證充分的安全性。</span><span class="sxs-lookup"><span data-stu-id="e5618-103">Replication over the Internet can provide flexibility, particularly for mobile Subscribers, but you must configure Internet replication appropriately to ensure adequate security.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="e5618-104">建議使用下列兩個透過網際網路安全共用資訊的技術之一：</span><span class="sxs-lookup"><span data-stu-id="e5618-104">recommends using one of two techniques for securely sharing information over the Internet:</span></span>  
  
-   <span data-ttu-id="e5618-105">虛擬私人網路 (VPN)</span><span class="sxs-lookup"><span data-stu-id="e5618-105">Virtual private network (VPN)</span></span>  
  
-   <span data-ttu-id="e5618-106">合併式複寫的 Web 同步處理選項</span><span class="sxs-lookup"><span data-stu-id="e5618-106">The Web synchronization option for merge replication</span></span>  
  
## <a name="virtual-private-network"></a><span data-ttu-id="e5618-107">虛擬私人網路</span><span class="sxs-lookup"><span data-stu-id="e5618-107">Virtual Private Network</span></span>  
 <span data-ttu-id="e5618-108">虛擬私人網路會提供一個簡單又安全的分層方式，透過網際網路複寫 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料。</span><span class="sxs-lookup"><span data-stu-id="e5618-108">Virtual private networks provide a simple and secure layered approach to replicating [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data over the Internet.</span></span> <span data-ttu-id="e5618-109">透過網際網路的 VPN 連接在邏輯上的操作類似站台之間的「廣域網路」(WAN) 連結。</span><span class="sxs-lookup"><span data-stu-id="e5618-109">The VPN connection over the Internet logically operates as a Wide Area Network (WAN) link between the sites.</span></span>  
  
 <span data-ttu-id="e5618-110">藉由允許使用者穿過網際網路或其他公用網路 (使用如 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows NT 4.0 版本或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows2000 作業系統可用的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Point-to-Point Tunneling Protocol (PPTP) 之類的通訊協定，或 Windows 2000 作業系統可用的 Layer Two Tunneling Protocol (L2TP)) 的通道即可達成。</span><span class="sxs-lookup"><span data-stu-id="e5618-110">This is achieved by allowing the user to tunnel through the Internet or another public network using a protocol such as [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Point-to-Point Tunneling Protocol (PPTP) available with the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows NT version 4.0 or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2000 operating system, or Layer Two Tunneling Protocol (L2TP) available with the Windows 2000 operating system.</span></span> <span data-ttu-id="e5618-111">這個處理所提供的安全性和功能與私人網路中所提供的類似。</span><span class="sxs-lookup"><span data-stu-id="e5618-111">This process provides security and features similar to those available in a private network.</span></span>  
  
 <span data-ttu-id="e5618-112">如需有關設定 VPN 的詳細資訊，請參閱 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="e5618-112">For more information about setting up a VPN, see the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows documentation.</span></span>  
  
## <a name="web-synchronization-through-iis"></a><span data-ttu-id="e5618-113">透過 IIS 的 Web 同步處理</span><span class="sxs-lookup"><span data-stu-id="e5618-113">Web Synchronization Through IIS</span></span>  
 <span data-ttu-id="e5618-114">用於合併式複寫的 Web 同步處理選項提供了經由使用 HTTPS 通訊協定來複寫資料的功能，這是一個透過防火牆來複寫資料的便利方式。</span><span class="sxs-lookup"><span data-stu-id="e5618-114">The web synchronization option for merge replication provides the ability to replicate data using the HTTPS protocol, which can be a convenient approach to replicating data through a firewall.</span></span> <span data-ttu-id="e5618-115">如需詳細資訊，請參閱[設定 Web 同步處理](../configure-web-synchronization.md)和 [Web 同步處理的安全性架構](security-architecture-for-web-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="e5618-115">For more information, see [Configure Web Synchronization](../configure-web-synchronization.md) and [Security Architecture for Web Synchronization](security-architecture-for-web-synchronization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5618-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5618-116">See Also</span></span>  
 <span data-ttu-id="e5618-117">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="e5618-117">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="e5618-118">SQL Server 複寫安全性</span><span class="sxs-lookup"><span data-stu-id="e5618-118">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
