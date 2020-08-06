---
title: 瀏覽伺服器 (網路伺服器) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.browseservers.network.f1
ms.assetid: a59ffcd6-4b69-4c5c-9740-699ccb2183fb
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0ba5e4e5dd6d9a6541a98e0cb30229d7335bac24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597374"
---
# <a name="browse-for-servers-network-servers"></a><span data-ttu-id="008f9-102">瀏覽伺服器 (網路伺服器)</span><span class="sxs-lookup"><span data-stu-id="008f9-102">Browse for Servers (Network Servers)</span></span>
  <span data-ttu-id="008f9-103">如果連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 元件，但不知道 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的確實名稱，請在 [伺服器名稱]\*\*\*\* 方塊中按一下 [瀏覽其他]\*\*\*\*，以開啟 [瀏覽伺服器]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="008f9-103">If you are connecting to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] component and you do not know the exact name of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance, click **Browse for more** in the **Server name** box to open the **Browse for Servers** dialog box.</span></span>  
  
 <span data-ttu-id="008f9-104">伺服器電腦上的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser 服務會擴展這個對話方塊。</span><span class="sxs-lookup"><span data-stu-id="008f9-104">This dialog is populated by the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser service on the server computers.</span></span> <span data-ttu-id="008f9-105">執行個體名稱未出現在清單中的原因很多：</span><span class="sxs-lookup"><span data-stu-id="008f9-105">There are several reasons why the name of an instance might not appear in the list:</span></span>  
  
-   <span data-ttu-id="008f9-106">在執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的電腦上可能未執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Browser 服務。</span><span class="sxs-lookup"><span data-stu-id="008f9-106">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser service might not be running on the computer running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="008f9-107">防火牆可能封鎖了 UDP 通訊埠 1434。</span><span class="sxs-lookup"><span data-stu-id="008f9-107">UDP port 1434 might be blocked by a firewall.</span></span>  
  
-   <span data-ttu-id="008f9-108">可能設定了 **HideInstance** 旗標。</span><span class="sxs-lookup"><span data-stu-id="008f9-108">The **HideInstance** flag might be set.</span></span>  
  
 <span data-ttu-id="008f9-109">若要連接至未出現在清單中的執行個體，請輸入執行個體的完整連接字串 (包括 TCP/IP 通訊埠編號或具名管道的管道名稱)。</span><span class="sxs-lookup"><span data-stu-id="008f9-109">To connect to an instance that does not appear in the list, type a full connection string for the instance, including the TCP/IP port number or the named pipes pipe name.</span></span>  
  
## <a name="options"></a><span data-ttu-id="008f9-110">選項</span><span class="sxs-lookup"><span data-stu-id="008f9-110">Options</span></span>  
 <span data-ttu-id="008f9-111">**從網路中選取一個連接的 SQL Server 執行個體**</span><span class="sxs-lookup"><span data-stu-id="008f9-111">**Select a SQL Server instance in the network for your connection**</span></span>  
 <span data-ttu-id="008f9-112">按一下樹狀結構中所顯示的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體，以指定您想要連接到的伺服器。</span><span class="sxs-lookup"><span data-stu-id="008f9-112">Designate the server you want to connect to by clicking on the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance displayed in the tree.</span></span> <span data-ttu-id="008f9-113">您可以按一下以或符號標示的節點，以顯示或隱藏部分樹狀檢視 **+** **-** 。</span><span class="sxs-lookup"><span data-stu-id="008f9-113">You can show or hide portions of the tree view by clicking on the nodes marked with a **+** or **-** symbol.</span></span>  
  
  
