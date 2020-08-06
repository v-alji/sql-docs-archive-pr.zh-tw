---
title: 合併式複寫的 Web 同步處理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication synchronization [SQL Server replication]
- Internet [SQL Server replication], synchronization
- synchronization [SQL Server replication], Web Synchronization
- Web publishing [SQL Server replication], synchronization
- Web synchronization, about
- Web synchronization
ms.assetid: 84785aba-b2c1-4821-9e9d-a363c73dcb37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef7bf5a6f77d593a90508a0b69d02f8c0db04407
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599473"
---
# <a name="web-synchronization-for-merge-replication"></a><span data-ttu-id="27595-102">合併式複寫的 Web 同步處理</span><span class="sxs-lookup"><span data-stu-id="27595-102">Web Synchronization for Merge Replication</span></span>
  <span data-ttu-id="27595-103">合併式複寫的 Web 同步處理可讓您利用 HTTPS 通訊協定來複寫資料，而且對下列案例很有用：</span><span class="sxs-lookup"><span data-stu-id="27595-103">Web synchronization for merge replication lets you replicate data by using the HTTPS protocol, and is useful for the following scenarios:</span></span>

-   <span data-ttu-id="27595-104">透過網際網路同步處理來自行動使用者的資料。</span><span class="sxs-lookup"><span data-stu-id="27595-104">Synchronizing data from mobile users over the Internet.</span></span>

-   <span data-ttu-id="27595-105">跨越公司防火牆在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫之間同步處理資料。</span><span class="sxs-lookup"><span data-stu-id="27595-105">Synchronizing data between [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases across a corporate firewall.</span></span>

 <span data-ttu-id="27595-106">例如，旅行途中的銷售代表可以使用 Web 同步處理。</span><span class="sxs-lookup"><span data-stu-id="27595-106">For example, a traveling sales representative can use Web synchronization.</span></span> <span data-ttu-id="27595-107">[!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]公司有許多銷售代表需要訪問他們所在地區的各店鋪及供應商。</span><span class="sxs-lookup"><span data-stu-id="27595-107">The company, [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)], has sales representatives that travel to various stores and suppliers throughout their regions.</span></span> <span data-ttu-id="27595-108">長途旅行時，這些銷售代表會在旅館中停宿，他們需要一個便利的方式可以讓他們在每日結束時上傳銷售資料並下載產品更新。</span><span class="sxs-lookup"><span data-stu-id="27595-108">On longer trips the representatives stay in hotels and need a convenient way to upload sales data and download any product updates at the end of each day.</span></span>

 <span data-ttu-id="27595-109">[!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] 的 IT 部門用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 對每台可攜式電腦進行了設定，可以讓合併式複寫使用 Web 同步處理。</span><span class="sxs-lookup"><span data-stu-id="27595-109">The [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] IT department has configured each portable computer with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and has enabled merge replication to use Web synchronization.</span></span> <span data-ttu-id="27595-110">每台可攜式電腦上的合併代理程式都有一個指向複寫元件的網際網路 URL，這些複寫元件安裝在執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) 的電腦上。</span><span class="sxs-lookup"><span data-stu-id="27595-110">The Merge Agent on each portable computer has an Internet URL that points to the replication components that are installed on a computer that is running [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS).</span></span> <span data-ttu-id="27595-111">這些元件會利用發行者來同步處理訂閱者。</span><span class="sxs-lookup"><span data-stu-id="27595-111">These components synchronize the Subscriber with the Publisher.</span></span> <span data-ttu-id="27595-112">現在每個銷售代表都可以透過任何可用的網際網路連接進行連線，而不需要使用遠端撥號連接，並能夠上傳及下載適當的資料。</span><span class="sxs-lookup"><span data-stu-id="27595-112">Each representative can now connect through any available Internet connection without using a remote dial-up connection, and can upload and download the appropriate data.</span></span> <span data-ttu-id="27595-113">網際網路連接使用了「安全通訊端層」(SSL)，因此不需要使用虛擬私人網路 (VPN)。</span><span class="sxs-lookup"><span data-stu-id="27595-113">The Internet connection uses Secure Sockets Layer (SSL); therefore, a virtual private network (VPN) is not required.</span></span>

 <span data-ttu-id="27595-114">如需設定 Web 同步處理所需元件的資訊，請參閱[設定 Web 同步處理](configure-web-synchronization.md)、[針對 Web 同步處理設定 IIS](configure-iis-for-web-synchronization.md) 和[針對 Web 同步處理設定 IIS 7](configure-iis-7-for-web-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="27595-114">For information about how to configure the components that are required for Web synchronization, see [Configure Web Synchronization](configure-web-synchronization.md), [Configure IIS for Web Synchronization](configure-iis-for-web-synchronization.md), and [Configure IIS 7 for Web Synchronization](configure-iis-7-for-web-synchronization.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="27595-115">Web 同步處理專為同步處理可攜式電腦、手持式裝置及其他用戶端的資料而設計。</span><span class="sxs-lookup"><span data-stu-id="27595-115">Web synchronization is designed for synchronizing data with portable computers, handheld devices, and other clients.</span></span> <span data-ttu-id="27595-116">Web 同步處理並非用於高容量伺服器至伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="27595-116">Web synchronization is not intended for high-volume server-to-server applications.</span></span>

## <a name="overview-of-how-web-synchronization-works"></a><span data-ttu-id="27595-117">Web 同步處理運作方式概觀</span><span class="sxs-lookup"><span data-stu-id="27595-117">Overview of How Web Synchronization Works</span></span>
 <span data-ttu-id="27595-118">當使用 Web 同步處理時，訂閱者端的更新會封裝並當作 XML 訊息用 HTTPS 通訊協定傳送到執行 IIS 的電腦。</span><span class="sxs-lookup"><span data-stu-id="27595-118">When Web synchronization is used, updates at the Subscriber are packaged and sent as an XML message to the computer that is running IIS by using the HTTPS protocol.</span></span> <span data-ttu-id="27595-119">然後執行 IIS 的電腦會以二進位格式 (通常使用 TCP/IP) 將命令傳送到發行者。</span><span class="sxs-lookup"><span data-stu-id="27595-119">The computer that is running IIS then sends the commands to the Publisher in a binary format, typically by using TCP/IP.</span></span> <span data-ttu-id="27595-120">發行者端的更新會傳送到執行 IIS 的電腦，然後封裝為 XML 訊息傳遞到訂閱者。</span><span class="sxs-lookup"><span data-stu-id="27595-120">Updates at the Publisher are sent to the computer that is running IIS and then packaged as an XML message for delivery to the Subscriber.</span></span>

 <span data-ttu-id="27595-121">下圖顯示了合併式複寫之 Web 同步處理所涉及的部分元件。</span><span class="sxs-lookup"><span data-stu-id="27595-121">The following illustration shows some of the components that are involved in Web synchronization for merge replication.</span></span>

 <span data-ttu-id="27595-122">![Web 同步處理元件和資料流程](media/web-sync01.gif "Web 同步處理元件和資料流程")</span><span class="sxs-lookup"><span data-stu-id="27595-122">![Web synchronization components and data flow](media/web-sync01.gif "Web synchronization components and data flow")</span></span>

 <span data-ttu-id="27595-123">Web 同步處理是僅用於提取訂閱的選項；因此「合併代理程式」永遠是在訂閱者端執行。</span><span class="sxs-lookup"><span data-stu-id="27595-123">Web synchronization is an option only for pull subscriptions; therefore, a Merge Agent will always run on the Subscriber.</span></span> <span data-ttu-id="27595-124">此合併代理程式可以是標準合併代理程式、合併代理程式 ActiveX 控制項，或透過 Replication Management Objects (RMO) 提供同步處理的應用程式。</span><span class="sxs-lookup"><span data-stu-id="27595-124">This Merge Agent can be the standard Merge Agent, the Merge Agent ActiveX control, or an application that provides synchronization through Replication Management Objects (RMO).</span></span> <span data-ttu-id="27595-125">若要指定執行 IIS 之電腦的位置，請使用合併代理程式的 **-InternetUrl**參數。</span><span class="sxs-lookup"><span data-stu-id="27595-125">To specify the location of the computer that is running IIS, use the **-InternetUrl** parameter for the Merge Agent.</span></span>

 <span data-ttu-id="27595-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener (Replisapi.dll) 在執行 IIS 的電腦上設定，負責處理從發行者和訂閱者傳送到伺服器的訊息。</span><span class="sxs-lookup"><span data-stu-id="27595-126">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener (Replisapi.dll) is configured on the computer that is running IIS and is responsible for handling messages that are sent to the server from the Publisher and Subscribers.</span></span> <span data-ttu-id="27595-127">拓撲中的每個節點都利用「合併式複寫重新調整器」(Replrec.dll) 來處理 XML 資料流。</span><span class="sxs-lookup"><span data-stu-id="27595-127">Each node in the topology handles the XML data stream by using the Merge Replication Reconciler (Replrec.dll).</span></span>

 <span data-ttu-id="27595-128">參與 Web 同步處理的所有電腦都需要[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="27595-128">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or a later version is required for all computers that participate in Web synchronization.</span></span>

### <a name="synchronization-process"></a><span data-ttu-id="27595-129">同步處理程序</span><span class="sxs-lookup"><span data-stu-id="27595-129">Synchronization Process</span></span>
 <span data-ttu-id="27595-130">同步處理期間會發生下列步驟：</span><span class="sxs-lookup"><span data-stu-id="27595-130">The following steps occur during synchronization:</span></span>

1.  <span data-ttu-id="27595-131">合併代理程式會在訂閱者端啟動。</span><span class="sxs-lookup"><span data-stu-id="27595-131">The Merge Agent is started at the Subscriber.</span></span> <span data-ttu-id="27595-132">此代理程式會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="27595-132">The agent does the following:</span></span>

    1.  <span data-ttu-id="27595-133">建立到訂閱資料庫的 SQL 連接。</span><span class="sxs-lookup"><span data-stu-id="27595-133">Makes an SQL connection to the subscription database.</span></span>

    2.  <span data-ttu-id="27595-134">從資料庫擷取任何變更。</span><span class="sxs-lookup"><span data-stu-id="27595-134">Extracts any changes from the database.</span></span>

    3.  <span data-ttu-id="27595-135">對執行 IIS 的電腦進行 HTTPS 要求。</span><span class="sxs-lookup"><span data-stu-id="27595-135">Makes an HTTPS request to the computer that is running IIS.</span></span>

    4.  <span data-ttu-id="27595-136">上傳資料變更來做為 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="27595-136">Uploads data changes as an XML message.</span></span>

2.  <span data-ttu-id="27595-137">執行 IIS 的電腦上主控的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener 和合併式複寫重新調整器會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="27595-137">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener and Merge Replication Reconciler that are hosted on the computer that is running IIS do the following:</span></span>

    1.  <span data-ttu-id="27595-138">回應 HTTPS 要求。</span><span class="sxs-lookup"><span data-stu-id="27595-138">Respond to the HTTPS request.</span></span>

    2.  <span data-ttu-id="27595-139">建立到發行集資料庫的 SQL 連接。</span><span class="sxs-lookup"><span data-stu-id="27595-139">Make an SQL connection to the publication database.</span></span>

    3.  <span data-ttu-id="27595-140">將上傳變更套用到發行集資料庫。</span><span class="sxs-lookup"><span data-stu-id="27595-140">Apply the upload changes to the publication database.</span></span>

    4.  <span data-ttu-id="27595-141">擷取訂閱者的下載變更。</span><span class="sxs-lookup"><span data-stu-id="27595-141">Extract the download changes for the Subscriber.</span></span>

    5.  <span data-ttu-id="27595-142">將 HTTPS 回應傳回合併代理程式。</span><span class="sxs-lookup"><span data-stu-id="27595-142">Send an HTTPS response back to the Merge Agent.</span></span>

3.  <span data-ttu-id="27595-143">接著，訂閱者端的合併代理程式會接受 HTTPS 回應，並將下載變更套用到訂閱資料庫。</span><span class="sxs-lookup"><span data-stu-id="27595-143">The Merge Agent at the Subscriber then accepts the HTTPS response and applies the download changes to the subscription database.</span></span>

## <a name="see-also"></a><span data-ttu-id="27595-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27595-144">See Also</span></span>
 <span data-ttu-id="27595-145">設定 web[同步處理的](topologies-for-web-synchronization.md) [web 同步](configure-web-synchronization.md)處理拓撲</span><span class="sxs-lookup"><span data-stu-id="27595-145">[Configure Web Synchronization](configure-web-synchronization.md) [Topologies for Web Synchronization](topologies-for-web-synchronization.md)</span></span>


