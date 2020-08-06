---
title: 用戶端通訊協定- (通訊協定] 索引標籤) 的 TCP 和 IP 屬性 |Microsoft Docs
description: 瞭解如何在 Microsoft SQL Server Configuration Manager 中指定 TCP/IP 選項，例如 [keep-alive] 參數和預設埠號碼。
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], client protocols
- client protocols [SQL Server]
ms.assetid: d04f1bce-069c-4a02-b561-c87c3282be36
author: rothja
ms.author: jroth
ms.openlocfilehash: dfcf0348dc863970384a40cc9e773481adeedb35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705814"
---
# <a name="client-protocols---tcp-and-ip-properties-protocol-tab"></a><span data-ttu-id="ade81-103">用戶端通訊協定 - TCP 和 IP 屬性 (通訊協定索引標籤)</span><span class="sxs-lookup"><span data-stu-id="ade81-103">Client Protocols - TCP and IP Properties (Protocol Tab)</span></span>
  <span data-ttu-id="ade81-104">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員中，您可以使用 [TCP/IP 內容]\*\*\*\* 對話方塊的 [通訊協定]\*\*\*\* 索引標籤來檢視或指定下列選項。</span><span class="sxs-lookup"><span data-stu-id="ade81-104">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, use the **Protocol** tab on the **TCP/IP Properties** dialog box to view or specify the following options.</span></span> <span data-ttu-id="ade81-105">若要連接到其他通訊埠，請在 **[預設通訊埠]** 方塊內輸入通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="ade81-105">To connect to a different port, type the port number in the **Default Port** box.</span></span> <span data-ttu-id="ade81-106">如需連接字串的詳細資訊，請參閱 [使用 TCP/IP 建立有效的連接字串](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)。</span><span class="sxs-lookup"><span data-stu-id="ade81-106">For more information about connection strings, see [Creating a Valid Connection String Using TCP IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ade81-107">選項</span><span class="sxs-lookup"><span data-stu-id="ade81-107">Options</span></span>  
 <span data-ttu-id="ade81-108">**[預設通訊埠]**</span><span class="sxs-lookup"><span data-stu-id="ade81-108">**Default Port**</span></span>  
 <span data-ttu-id="ade81-109">指定 TCP/IP 網路程式庫嘗試連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的目標執行個體時，要使用的預設通訊埠。</span><span class="sxs-lookup"><span data-stu-id="ade81-109">Specifies the port that the TCP/IP Net-library will use to attempt to connect to the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ade81-110">預設的通訊埠值為 1433。</span><span class="sxs-lookup"><span data-stu-id="ade81-110">The default value port is 1433.</span></span>  
  
 <span data-ttu-id="ade81-111">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的預設執行個體時，用戶端會使用這個值。</span><span class="sxs-lookup"><span data-stu-id="ade81-111">When connecting to a default instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)], the client uses this value.</span></span> <span data-ttu-id="ade81-112">如果預設執行個體已設為接聽不同的通訊埠，請將此值變更為該通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="ade81-112">If a default instance has been configured to listen on a different port, change this value to that port number.</span></span>  
  
 <span data-ttu-id="ade81-113">連接到具名的 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體時，用戶端會嘗試從在伺服器電腦執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Service 取得通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="ade81-113">When connecting to a named instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)], the client will attempt to obtain the port number from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Service running on the server computer.</span></span> <span data-ttu-id="ade81-114">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Service 未執行，就必須透過這項設定提供通訊埠編號，或者以連接字串方式提供。</span><span class="sxs-lookup"><span data-stu-id="ade81-114">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Service is not running, the port number must be provided through this setting, or as part of the connection string.</span></span>  
  
 <span data-ttu-id="ade81-115">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="ade81-115">**Enabled**</span></span>  
 <span data-ttu-id="ade81-116">可能的值為 **[是] 和 [** **否**]。</span><span class="sxs-lookup"><span data-stu-id="ade81-116">Possible values are **Yes** and **No**.</span></span>  
  
 <span data-ttu-id="ade81-117">**保持運作**</span><span class="sxs-lookup"><span data-stu-id="ade81-117">**Keep Alive**</span></span>  
 <span data-ttu-id="ade81-118">此參數 (以毫秒為單位) 藉由傳送 **KEEPALIVE** 封包，來控制 TCP 嘗試驗證閒置連線是否仍完整無缺的頻率。</span><span class="sxs-lookup"><span data-stu-id="ade81-118">This parameter (in milliseconds) controls how often TCP attempts to verify that an idle connection is still intact by sending a **KEEPALIVE** packet.</span></span> <span data-ttu-id="ade81-119">預設為 30000 毫秒。</span><span class="sxs-lookup"><span data-stu-id="ade81-119">The default is 30000 milliseconds.</span></span>  
  
 <span data-ttu-id="ade81-120">**保持運作的間隔**</span><span class="sxs-lookup"><span data-stu-id="ade81-120">**Keep Alive Interval**</span></span>  
 <span data-ttu-id="ade81-121">此參數 (以毫秒為單位) 可決定在收到回應之前，用以分隔 **KEEPALIVE** 重新傳輸的間隔。</span><span class="sxs-lookup"><span data-stu-id="ade81-121">This parameter (in milliseconds) determines the interval separating **KEEPALIVE** retransmissions until a response is received.</span></span> <span data-ttu-id="ade81-122">預設為 1000 毫秒。</span><span class="sxs-lookup"><span data-stu-id="ade81-122">The default is 1000 milliseconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade81-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ade81-123">See Also</span></span>  
 <span data-ttu-id="ade81-124">[選擇網路通訊協定](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="ade81-124">[Choosing a Network Protocol](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span></span>  
 <span data-ttu-id="ade81-125">[新別名 &#40;別名] 索引標籤&#41;](../../../2014/tools/configuration-manager/new-alias-alias-tab.md) </span><span class="sxs-lookup"><span data-stu-id="ade81-125">[New Alias &#40;Alias Tab&#41;](../../../2014/tools/configuration-manager/new-alias-alias-tab.md) </span></span>  
 [<span data-ttu-id="ade81-126">&#60;Alias&#62; 屬性 &#40;別名索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="ade81-126">&#60;Alias&#62; Properties &#40;Alias Tab&#41;</span></span>](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)  
  
  
