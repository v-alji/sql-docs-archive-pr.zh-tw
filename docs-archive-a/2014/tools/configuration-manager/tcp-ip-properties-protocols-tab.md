---
title: TCP/IP 屬性 (通訊協定] 索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1d5bc28faddae9a86a6636b56b907b57a2d8711a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585740"
---
# <a name="tcp---ip-properties-protocols-tab"></a><span data-ttu-id="6ca71-102">TCP/IP 屬性 (通訊協定] 索引標籤) </span><span class="sxs-lookup"><span data-stu-id="6ca71-102">TCP - IP Properties (Protocols Tab)</span></span>
  <span data-ttu-id="6ca71-103">使用 [TCP/IP 屬性]  對話方塊來設定 TCP/IP 通訊協定的選項。</span><span class="sxs-lookup"><span data-stu-id="6ca71-103">Use the **TCP/IP Properties** dialog box to configure the options for the TCP/IP protocol.</span></span> <span data-ttu-id="6ca71-104">按一下左窗格中的 [TCP/IP]  ，在詳細資料窗格中顯示個別的 IP 位址組態。</span><span class="sxs-lookup"><span data-stu-id="6ca71-104">Click **TCP/IP** in the left pane, to show individual IP address configurations in the details pane.</span></span>  
  
 <span data-ttu-id="6ca71-105">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 必須重新啟動之後，變更才能生效。</span><span class="sxs-lookup"><span data-stu-id="6ca71-105">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restarted before the changes take effect.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6ca71-106">選項。</span><span class="sxs-lookup"><span data-stu-id="6ca71-106">Options</span></span>  
 <span data-ttu-id="6ca71-107">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="6ca71-107">**Enabled**</span></span>  
 <span data-ttu-id="6ca71-108">可能的值為 [是]  和 [否]  。</span><span class="sxs-lookup"><span data-stu-id="6ca71-108">Possible values are **Yes** and **No**.</span></span>  
  
 <span data-ttu-id="6ca71-109">**Keep Alive**</span><span class="sxs-lookup"><span data-stu-id="6ca71-109">**Keep Alive**</span></span>  
 <span data-ttu-id="6ca71-110">指定傳送保持運作封包以確認連接遠端是否仍然可用的間隔 (毫秒)。</span><span class="sxs-lookup"><span data-stu-id="6ca71-110">Specify the interval (milliseconds) in which keep-alive packets are transmitted to verify that the computer at the remote end of a connection is still available.</span></span>  
  
 <span data-ttu-id="6ca71-111">**Listen All**</span><span class="sxs-lookup"><span data-stu-id="6ca71-111">**Listen All**</span></span>  
 <span data-ttu-id="6ca71-112">指定 SQL Server 是否將接聽電腦的網路卡所繫結的所有 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6ca71-112">Specify whether SQL Server will listen on all the IP addresses that are bound to network cards on the computer.</span></span> <span data-ttu-id="6ca71-113">如果設為 [否]  ，請使用每個 IP 位址的屬性對話方塊，分別設定每個 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6ca71-113">If set to **No**, configure each IP address separately using the properties dialog box for each IP address.</span></span> <span data-ttu-id="6ca71-114">如果設為 [是]  ，[IPAll]  屬性方塊的設定將套用到所有 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6ca71-114">If set to **Yes**, the settings of the **IPAll** properties box will apply to all IP addresses.</span></span> <span data-ttu-id="6ca71-115">預設值是 [是]  。</span><span class="sxs-lookup"><span data-stu-id="6ca71-115">Default value is **Yes**.</span></span>  
  
 <span data-ttu-id="6ca71-116">**No Delay**</span><span class="sxs-lookup"><span data-stu-id="6ca71-116">**No Delay**</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6ca71-117">未實作此屬性的變更。</span><span class="sxs-lookup"><span data-stu-id="6ca71-117">does not implement changes to this property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ca71-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ca71-118">See Also</span></span>  
 <span data-ttu-id="6ca71-119">[選擇網路通訊協定](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="6ca71-119">[Choosing a Network Protocol](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span></span>  
 [<span data-ttu-id="6ca71-120">使用 TCP IP 建立有效的連接字串</span><span class="sxs-lookup"><span data-stu-id="6ca71-120">Creating a Valid Connection String Using TCP IP</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
  
