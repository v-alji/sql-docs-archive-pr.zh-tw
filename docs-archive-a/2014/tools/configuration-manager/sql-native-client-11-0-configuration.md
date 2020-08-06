---
title: SQL Native Client 11.0 設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- client configuration [SQL Server], SQL Server Native Client
ms.assetid: e73143e9-5e7b-4d0a-8827-ab900efdcb35
author: stevestein
ms.author: sstein
ms.openlocfilehash: 183dd2d161b1bf0b13140a607167b81dab086fdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592417"
---
# <a name="sql-native-client-110-configuration"></a><span data-ttu-id="150f6-102">SQL Native Client 11.0 組態</span><span class="sxs-lookup"><span data-stu-id="150f6-102">SQL Native Client 11.0 Configuration</span></span>
  <span data-ttu-id="150f6-103">本區段包含   組態管理員中 [!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server Native Client 組態[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]對話方塊的 F1 說明主題。</span><span class="sxs-lookup"><span data-stu-id="150f6-103">This section contains the F1 Help topics for the **SQL Server Native Client Configuration** dialogs in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="150f6-104">Native Client 為用戶端電腦用來與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連線的網路程式庫，從 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 開始。</span><span class="sxs-lookup"><span data-stu-id="150f6-104">Native Client is the network library that client computers use to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], starting with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="150f6-105">執行用戶端程式的電腦會使用「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 組態」中的設定。</span><span class="sxs-lookup"><span data-stu-id="150f6-105">The settings configured in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Configuration, are used on the computer running the client program.</span></span> <span data-ttu-id="150f6-106">在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的電腦上設定時，它們只會影響在伺服器執行的用戶端程式。</span><span class="sxs-lookup"><span data-stu-id="150f6-106">When configured on the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], they affect only those client programs running on the server.</span></span>  
  
 <span data-ttu-id="150f6-107">這些設定不會影響連接到先前版本 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的用戶端，除非它們使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]才提供的用戶端工具，例如： [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="150f6-107">These settings do not affect clients connecting to previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], unless they are using the client tools starting with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="150f6-108">本章節內容</span><span class="sxs-lookup"><span data-stu-id="150f6-108">In this Section</span></span>  
  
-   [<span data-ttu-id="150f6-109">SQL Server Native Client 組態屬性 &#40;旗標索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="150f6-109">SQL Server Native Client Configuration Properties &#40;Flags Tab&#41;</span></span>](../../../2014/tools/configuration-manager/sql-server-native-client-configuration-properties-flags-tab.md)  
  
-   [<span data-ttu-id="150f6-110">用戶端通訊協定 &#40;SQL Server 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="150f6-110">Client Protocols &#40;SQL Server Configuration Manager&#41;</span></span>](../../relational-databases/sql-server-configuration-manager.md)  
  
    -   [<span data-ttu-id="150f6-111">用戶端通訊協定屬性 &#40;順序索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="150f6-111">Client Protocols Properties &#40;Order Tab&#41;</span></span>](../../../2014/tools/configuration-manager/client-protocols-properties-order-tab.md)  
  
    -   [<span data-ttu-id="150f6-112">用戶端通訊協定 - 共用記憶體屬性 &#40;通訊協定索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="150f6-112">Client Protocols - Shared Memory Properties &#40;Protocol Tab&#41;</span></span>](../../../2014/tools/configuration-manager/client-protocols-shared-memory-properties-protocol-tab.md)  
  
    -   <span data-ttu-id="150f6-113">[用戶端通訊協定-&#40;通訊協定] 索引標籤的 TCP 和 IP 屬性&#41;](../../../2014/tools/configuration-manager/client-protocols-tcp-and-ip-properties-protocol-tab.md)</span><span class="sxs-lookup"><span data-stu-id="150f6-113">[Client Protocols - TCP and IP Properties &#40;Protocol Tab&#41;](../../../2014/tools/configuration-manager/client-protocols-tcp-and-ip-properties-protocol-tab.md)</span></span>  
  
    -   [<span data-ttu-id="150f6-114">用戶端通訊協定 - 具名管道內容 &#40;通訊協定索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="150f6-114">Client Protocols - Named Pipes Properties &#40;Protocol Tab&#41;</span></span>](../../../2014/tools/configuration-manager/client-protocols-named-pipes-properties-protocol-tab.md)  
  
-   [<span data-ttu-id="150f6-115">別名 &#40;SQL Server 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="150f6-115">Aliases &#40;SQL Server Configuration Manager&#41;</span></span>](../../../2014/tools/configuration-manager/aliases-sql-server-configuration-manager.md)  
  
    -   [<span data-ttu-id="150f6-116">新增別名 &#40;別名索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="150f6-116">New Alias &#40;Alias Tab&#41;</span></span>](../../../2014/tools/configuration-manager/new-alias-alias-tab.md)  
  
    -   [<span data-ttu-id="150f6-117">&#60;Alias&#62; 屬性 &#40;別名索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="150f6-117">&#60;Alias&#62; Properties &#40;Alias Tab&#41;</span></span>](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)  
  
    -   [<span data-ttu-id="150f6-118">使用共用記憶體通訊協定建立有效的連接字串</span><span class="sxs-lookup"><span data-stu-id="150f6-118">Creating a Valid Connection String Using Shared Memory Protocol</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
    -   [<span data-ttu-id="150f6-119">使用 TCP IP 建立有效的連接字串</span><span class="sxs-lookup"><span data-stu-id="150f6-119">Creating a Valid Connection String Using TCP IP</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
    -   [<span data-ttu-id="150f6-120">使用具名管道建立有效的連接字串</span><span class="sxs-lookup"><span data-stu-id="150f6-120">Creating a Valid Connection String Using Named Pipes</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)  
  
  
