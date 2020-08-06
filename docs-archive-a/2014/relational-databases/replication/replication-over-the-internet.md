---
title: 透過網際網路的複寫 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Web publishing [SQL Server replication], about Web publishing
- Web publishing [SQL Server replication]
- Internet [SQL Server replication]
- Internet [SQL Server replication], publishing
ms.assetid: 04e7f4ed-e244-4bbe-ba12-09c33abea09e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 46c61f8a5383c87d46fa0dbda18876b43ffb7739
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585271"
---
# <a name="replication-over-the-internet"></a><span data-ttu-id="d71d8-102">透過網際網路的複寫</span><span class="sxs-lookup"><span data-stu-id="d71d8-102">Replication over the Internet</span></span>
  <span data-ttu-id="d71d8-103">透過網際網路複寫資料，可讓遠端、離線使用者在需要時使用網際網路連線存取資料。</span><span class="sxs-lookup"><span data-stu-id="d71d8-103">Replicating data over the Internet allows remote, disconnected users to access data when they need it using a connection to the Internet.</span></span> <span data-ttu-id="d71d8-104">使用下列方式，透過網際網路複寫資料：</span><span class="sxs-lookup"><span data-stu-id="d71d8-104">Replicate data over the Internet using:</span></span>  
  
-   <span data-ttu-id="d71d8-105">虛擬私人網路 (VPN)。</span><span class="sxs-lookup"><span data-stu-id="d71d8-105">A Virtual Private Network (VPN).</span></span> <span data-ttu-id="d71d8-106">如需詳細資訊，請參閱[使用 VPN 透過網際網路發行資料](publish-data-over-the-internet-using-vpn.md)。</span><span class="sxs-lookup"><span data-stu-id="d71d8-106">For more information, see [Publish Data over the Internet Using VPN](publish-data-over-the-internet-using-vpn.md).</span></span>  
  
-   <span data-ttu-id="d71d8-107">合併式複寫的 Web 同步處理選項。</span><span class="sxs-lookup"><span data-stu-id="d71d8-107">The Web synchronization option for merge replication.</span></span> <span data-ttu-id="d71d8-108">如需詳細資訊，請參閱＜ [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d71d8-108">For more information, see [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md).</span></span>  
  
 <span data-ttu-id="d71d8-109">所有類型的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複寫都可以透過 VPN 複寫資料，但是您若是使用合併式複寫，則應考慮 Web 同步處理。</span><span class="sxs-lookup"><span data-stu-id="d71d8-109">All types of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication can replicate data over a VPN, but you should consider Web synchronization if you are using merge replication.</span></span>  
  
  
