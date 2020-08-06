---
title: 設定伺服器接聽替代管道 (SQL Server 組態管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Named Pipes [SQL Server], configuring
- listening [SQL Server], pipes
- pipes [SQL Server], alternate
- alternate pipes [SQL Server]
ms.assetid: 914f7491-e2be-4b0d-b3aa-fe5409cdbafa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 57d70cf4cd1d7474b895aeb8cb144c885e8a0f99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585592"
---
# <a name="configure-a-server-to-listen-on-an-alternate-pipe-sql-server-configuration-manager"></a><span data-ttu-id="12cff-102">設定接聽替代管道的伺服器 (SQL Server 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="12cff-102">Configure a Server to Listen on an Alternate Pipe (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="12cff-103">此主題描述如何使用 SQL Server 組態管理員，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定伺服器於替代管道接聽。</span><span class="sxs-lookup"><span data-stu-id="12cff-103">This topic describes how to configure a server to listen on an alternate pipe in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="12cff-104">根據預設， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的預設執行個體會接聽具名管道 \\\\.\pipe\sql\query。</span><span class="sxs-lookup"><span data-stu-id="12cff-104">By default, the default instance of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] listens on named pipe \\\\.\pipe\sql\query.</span></span> <span data-ttu-id="12cff-105">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 與 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 的具名執行個體會在其他管道上接聽。</span><span class="sxs-lookup"><span data-stu-id="12cff-105">Named instances of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and [!INCLUDE[ssEW](../../includes/ssew-md.md)] listen on other pipes.</span></span>  
  
 <span data-ttu-id="12cff-106">有三種方式可利用用戶端應用程式連接到特定的具名管道：</span><span class="sxs-lookup"><span data-stu-id="12cff-106">There are three ways to connect to a specific named pipe with a client application:</span></span>  
  
-   <span data-ttu-id="12cff-107">在伺服器上執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務。</span><span class="sxs-lookup"><span data-stu-id="12cff-107">Run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service on the server.</span></span>  
  
-   <span data-ttu-id="12cff-108">在用戶端上建立一個別名，指定具名管道。</span><span class="sxs-lookup"><span data-stu-id="12cff-108">Create an alias on the client, specifying the named pipe.</span></span>  
  
-   <span data-ttu-id="12cff-109">設定用戶端使用自訂連接字串進行連接。</span><span class="sxs-lookup"><span data-stu-id="12cff-109">Program the client to connect using a custom connection string.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="12cff-110">使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="12cff-110">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-configure-the-named-pipe-used-by-the-sql-server-database-engine"></a><span data-ttu-id="12cff-111">若要設定 SQL Server Database Engine 所使用的具名管道</span><span class="sxs-lookup"><span data-stu-id="12cff-111">To configure the named pipe used by the SQL Server Database Engine</span></span>  
  
1.  <span data-ttu-id="12cff-112">在 SQL Server 組態管理員的主控台窗格中，展開 [SQL Server 網路組態]，然後按一下以展開 *\<instance name>* 的 [通訊協定]。</span><span class="sxs-lookup"><span data-stu-id="12cff-112">In SQL Server Configuration Manager, in the console pane, expand **SQL Server Network Configuration**, and then click expand **Protocols for** *\<instance name>*.</span></span>  
  
2.  <span data-ttu-id="12cff-113">在詳細資料窗格中，以滑鼠右鍵按一下 [具名管道]，然後按一下 [內容]。</span><span class="sxs-lookup"><span data-stu-id="12cff-113">In the details pane, right-click **Named Pipes**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="12cff-114">在 **[通訊協定]** 索引標籤的 **[管道名稱]** 方塊中，輸入您要 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 接聽的管道，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="12cff-114">On the **Protocol** tab, in the **Pipe Name** box, type the pipe you want the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen on, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="12cff-115">在主控台窗格中，按一下 [SQL Server 服務]。</span><span class="sxs-lookup"><span data-stu-id="12cff-115">In the console pane, click **SQL Server Services**.</span></span>  
  
5.  <span data-ttu-id="12cff-116">在 [詳細資料窗格] 中，以滑鼠右鍵按一下 [SQL Server (\<instance name>)] ，然後按一下 [重新啟動]，先停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 後再重新啟動。</span><span class="sxs-lookup"><span data-stu-id="12cff-116">In the details pane, right-click **SQL Server (**\<instance name>**)** and then click **Restart**, to stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="12cff-117">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接聽替代管道時，有三種方式可利用用戶端應用程式連接到特定的具名管道：</span><span class="sxs-lookup"><span data-stu-id="12cff-117">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is listening on an alternate pipe, there are three ways to connect to a specific named pipe with a client application:</span></span>  
  
-   <span data-ttu-id="12cff-118">在伺服器上執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務。</span><span class="sxs-lookup"><span data-stu-id="12cff-118">Run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service on the server.</span></span>  
  
-   <span data-ttu-id="12cff-119">在用戶端上建立一個別名，指定具名管道。</span><span class="sxs-lookup"><span data-stu-id="12cff-119">Create an alias on the client, specifying the named pipe.</span></span>  
  
-   <span data-ttu-id="12cff-120">設定用戶端使用自訂連接字串進行連接。</span><span class="sxs-lookup"><span data-stu-id="12cff-120">Program the client to connect using a custom connection string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12cff-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12cff-121">See Also</span></span>  
 <span data-ttu-id="12cff-122">[建立或刪除用戶端使用的伺服器別名 &#40;SQL Server 組態管理員&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md) </span><span class="sxs-lookup"><span data-stu-id="12cff-122">[Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md) </span></span>  
 [<span data-ttu-id="12cff-123">伺服器網路組態</span><span class="sxs-lookup"><span data-stu-id="12cff-123">Server Network Configuration</span></span>](server-network-configuration.md)  
  
  
