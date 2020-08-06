---
title: 用戶端通訊協定屬性 (順序] 索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- client protocols [SQL Server]
ms.assetid: 64fd7135-1756-4885-bed9-9ab8997ecc6c
author: stevestein
ms.author: sstein
ms.openlocfilehash: a367cff3495389d1a707ed108ba75e1e736538b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688370"
---
# <a name="client-protocols-properties-order-tab"></a><span data-ttu-id="2e37f-102">用戶端通訊協定屬性 (順序索引標籤)</span><span class="sxs-lookup"><span data-stu-id="2e37f-102">Client Protocols Properties (Order Tab)</span></span>
  <span data-ttu-id="2e37f-103">您可以使用 [用戶端通訊協定內容]\*\*\*\* 對話方塊上的 [順序]\*\*\*\* 頁面來檢視與啟用用戶端通訊協定。</span><span class="sxs-lookup"><span data-stu-id="2e37f-103">Use the **Order**page on the **Client Protocols Properties** dialog box to view and enable the client protocols.</span></span>  
  
 <span data-ttu-id="2e37f-104">按一下通訊協定，然後按一下 [啟用]  或 [停用]  ，將選取的通訊協定移到 [停用通訊協定]  或 [啟用通訊協定]  清單中。</span><span class="sxs-lookup"><span data-stu-id="2e37f-104">Click a protocol, and then click **Enable** or **Disable** to move the selected protocol to the **Disabled Protocols** or **Enabled Protocols** list.</span></span>  
  
 <span data-ttu-id="2e37f-105">系統會以所列的順序嘗試通訊協定，亦即先嘗試使用第一順位的通訊協定，然後再嘗試使用第二順位的通訊協定，依此類推。若要上移或下移 [啟用的通訊協定]  清單中的通訊協定，請按一下向上箭頭或向下箭頭按鈕。</span><span class="sxs-lookup"><span data-stu-id="2e37f-105">Protocols are tried in the order listed, attempting to connect using the top protocol first, and then the second listed protocol, etc. Move protocols up or down the **Enabled Protocols** list, by clicking the up arrow and down arrow buttons.</span></span> <span data-ttu-id="2e37f-106">當您從該電腦上的用戶端連接到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，一律會先嘗試使用**共用記憶體**通訊協定 (若已啟用)。</span><span class="sxs-lookup"><span data-stu-id="2e37f-106">When connecting to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a client on that computer, the **Shared Memory** protocol will always be tried first, if enabled.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2e37f-107">[!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET SqlClient 不會使用這些設定。</span><span class="sxs-lookup"><span data-stu-id="2e37f-107">These settings are not used by [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET SqlClient.</span></span> <span data-ttu-id="2e37f-108">.NET SqlClient 的通訊協定順序最先是 TCP，接著是具名管道，您無法變更此順序。</span><span class="sxs-lookup"><span data-stu-id="2e37f-108">The protocol order for .NET SqlClient is first TCP, and then named pipes, which cannot be changed.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2e37f-109">選項。</span><span class="sxs-lookup"><span data-stu-id="2e37f-109">Options</span></span>  
 <span data-ttu-id="2e37f-110">**停用的通訊協定**</span><span class="sxs-lookup"><span data-stu-id="2e37f-110">**Disabled Protocols**</span></span>  
 <span data-ttu-id="2e37f-111">列出已安裝但目前未使用的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="2e37f-111">Lists protocols which are installed but are not currently used.</span></span>  
  
 <span data-ttu-id="2e37f-112">**啟用的通訊協定**</span><span class="sxs-lookup"><span data-stu-id="2e37f-112">**Enabled Protocols**</span></span>  
 <span data-ttu-id="2e37f-113">列出 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 此電腦上用戶端可用的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="2e37f-113">Lists protocols which are available for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clients on this computer.</span></span>  
  
 **>**  
 <span data-ttu-id="2e37f-114">啟用目前 [停用的通訊協定]  方塊中反白顯示的通訊協定，並將它移到 [啟用的通訊協定]  方塊。</span><span class="sxs-lookup"><span data-stu-id="2e37f-114">Enables the currently highlighted protocol in the **Disabled Protocols** box, moving it to the **Enabled Protocols** box.</span></span>  
  
 **\<**  
 <span data-ttu-id="2e37f-115">停用目前 [啟用的通訊協定]  方塊中反白顯示的通訊協定，並將它移到 [停用的通訊協定]  方塊。</span><span class="sxs-lookup"><span data-stu-id="2e37f-115">Disables the currently highlighted protocol in the **Enabled Protocols** box, moving it to the **Disabled Protocols** box.</span></span>  
  
 <span data-ttu-id="2e37f-116">向上箭頭</span><span class="sxs-lookup"><span data-stu-id="2e37f-116">Up arrow</span></span>  
 <span data-ttu-id="2e37f-117">在清單中將反白顯示的通訊協定向上移動。</span><span class="sxs-lookup"><span data-stu-id="2e37f-117">Moves the highlighted protocol up in the list.</span></span> <span data-ttu-id="2e37f-118">這樣可以提高所選取通訊協定的優先順序，網路程式庫會優先使用選取的通訊協定來進行連接。</span><span class="sxs-lookup"><span data-stu-id="2e37f-118">This allows you to increase the priority in which the Net-Library will attempt to use the selected protocol for connections.</span></span>  
  
 <span data-ttu-id="2e37f-119">向下箭頭</span><span class="sxs-lookup"><span data-stu-id="2e37f-119">Down arrow</span></span>  
 <span data-ttu-id="2e37f-120">在清單中將反白顯示的通訊協定向下移動。</span><span class="sxs-lookup"><span data-stu-id="2e37f-120">Moves the highlighted protocol down in the list.</span></span> <span data-ttu-id="2e37f-121">這樣可以降低所選取通訊協定的優先順序，網路程式庫會優先使用順序較高的其他通訊協定來進行連接。</span><span class="sxs-lookup"><span data-stu-id="2e37f-121">This allows you to decrease the priority in which the Net-Library will attempt to use the selected protocol for connections.</span></span>  
  
 <span data-ttu-id="2e37f-122">**啟用共用記憶體通訊協定**</span><span class="sxs-lookup"><span data-stu-id="2e37f-122">**Enable Shared Memory Protocol**</span></span>  
 <span data-ttu-id="2e37f-123">當您從該電腦的用戶端連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，系統會啟用總是優先嘗試的共用記憶體通訊協定 (若已啟用該協定)。</span><span class="sxs-lookup"><span data-stu-id="2e37f-123">Enables the shared memory protocol which is always tried first (if enabled), when connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a client on that computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2e37f-124">若通訊協定是以前置詞或連接字串的一部份來指定，則只會嘗試使用指定的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="2e37f-124">If the protocol is specified through a prefix or as part of the connection string, only the specified protocol is attempted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e37f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e37f-125">See Also</span></span>  
 [<span data-ttu-id="2e37f-126">選擇網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="2e37f-126">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
