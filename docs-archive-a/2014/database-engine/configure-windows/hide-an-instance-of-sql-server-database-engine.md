---
title: 隱藏 SQL Server 資料庫引擎的執行個體 | Microsoft Docs
ms.custom: ''
ms.date: 08/19/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], hiding instances
- hiding instances of Database Engine
ms.assetid: 392de21a-57fa-4a69-8237-ced8ca86ed1d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d2b3287c5d4d747ccb3511461341d5aed8ff765d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688229"
---
# <a name="hide-an-instance-of-sql-server-database-engine"></a><span data-ttu-id="310c6-102">隱藏 SQL Server Database Engine 的執行個體</span><span class="sxs-lookup"><span data-stu-id="310c6-102">Hide an Instance of SQL Server Database Engine</span></span>
  <span data-ttu-id="310c6-103">此主題描述如何使用 SQL Server 組態管理員，在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中隱藏 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="310c6-103">This topic describes how to hide an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="310c6-104">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務來列舉電腦上安裝的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="310c6-104">uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service to enumerate instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] installed on the computer.</span></span> <span data-ttu-id="310c6-105">這可讓用戶端應用程式瀏覽伺服器，並可幫助用戶端區別同一部電腦上的多個 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="310c6-105">This enables client applications to browse for a server, and helps clients distinguish between multiple instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the same computer.</span></span> <span data-ttu-id="310c6-106">您可以使用下列程序防止 SQL Server Browser 服務向嘗試利用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [瀏覽] **按鈕尋找執行個體的用戶端電腦公開** 執行個體。</span><span class="sxs-lookup"><span data-stu-id="310c6-106">You can use the following procedure to prevent the SQL Server Browser service from exposing an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to client computers that try to locate the instance by using the **Browse** button.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="310c6-107">使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="310c6-107">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-hide-an-instance-of-the-sql-server-database-engine"></a><span data-ttu-id="310c6-108">若要隱藏 SQL Server Database Engine 的執行個體</span><span class="sxs-lookup"><span data-stu-id="310c6-108">To hide an instance of the SQL Server Database Engine</span></span>  
  
1.  <span data-ttu-id="310c6-109">在 [SQL Server 組態管理員] 中，展開 [SQL Server 網路組態]，然後以滑鼠右鍵按一下 [通訊協定] *\<server instance>* ，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="310c6-109">In **SQL Server Configuration Manager**, expand **SQL Server Network Configuration**, right-click **Protocols for** *\<server instance>*, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="310c6-110">在 **[旗標]** 索引標籤的 **[HideInstance]** 方塊中，選取 **[是]** ，然後按一下 **[確定]** 關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="310c6-110">On the **Flags** tab, in the **HideInstance** box, select **Yes**, and then click **OK** to close the dialog box.</span></span> <span data-ttu-id="310c6-111">此變更在新連接時會立即生效。</span><span class="sxs-lookup"><span data-stu-id="310c6-111">The change takes effect immediately for new connections.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="310c6-112">備註</span><span class="sxs-lookup"><span data-stu-id="310c6-112">Remarks</span></span>  
 <span data-ttu-id="310c6-113">如果隱藏具名執行個體，將必須於連接字串中提供連接埠號碼，才可連接到隱藏的執行個體 (即使瀏覽器服務正在執行中亦然)。</span><span class="sxs-lookup"><span data-stu-id="310c6-113">If you hide a named instance, you will need to provide the port number in the connection string to connect to the hidden instance, even if the browser service is running.</span></span> <span data-ttu-id="310c6-114">建議您使用靜態連接埠，而不要使用具名隱藏執行個體的動態連接埠。</span><span class="sxs-lookup"><span data-stu-id="310c6-114">We recommend that you use a static port instead of a dynamic port for the named hidden instance.</span></span>  
  <span data-ttu-id="310c6-115">如需詳細資訊，請參閱[設定伺服器接聽特定 TCP 通訊埠 &#40;SQL Server 組態管理員&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md)。</span><span class="sxs-lookup"><span data-stu-id="310c6-115">For more information, see [Configure a Server to Listen on a Specific TCP Port &#40;SQL Server Configuration Manager&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md).</span></span>  
  
### <a name="clustering"></a><span data-ttu-id="310c6-116">叢集</span><span class="sxs-lookup"><span data-stu-id="310c6-116">Clustering</span></span>  
 <span data-ttu-id="310c6-117">如果隱藏了叢集具名執行個體，叢集服務可能無法連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="310c6-117">If you hide a clustered named instance, cluster service may not be able to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="310c6-118">這會導致叢集實例的**IsAlive**檢查失敗，且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會離線。</span><span class="sxs-lookup"><span data-stu-id="310c6-118">This will cause the cluster instance's **IsAlive** check to fail and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will go offline.</span></span> <span data-ttu-id="310c6-119">建議您在叢集執行個體的所有節點中都建立別名，以反映為該執行個體所設定的靜態連接埠。</span><span class="sxs-lookup"><span data-stu-id="310c6-119">We recommend that you create an alias in all the nodes of the clustered instance to reflect the static port that you configured for the instance.</span></span>  
 <span data-ttu-id="310c6-120">如需詳細資訊，請參閱[建立或刪除用戶端使用的伺服器別名 &#40;SQL Server Configuration Manager&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md)。</span><span class="sxs-lookup"><span data-stu-id="310c6-120">For more information, see [Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md).</span></span>  
  
 <span data-ttu-id="310c6-121">如果隱藏了叢集具名執行個體，而當 **LastConnect** 登錄機碼 (**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI11.0\LastConnect**) 與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目前接聽的連接埠有不同的連接埠時，叢集服務可能無法連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="310c6-121">If you hide a clustered named instance, cluster service may not be able to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if the **LastConnect** registry key (**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI11.0\LastConnect**) has a different port than the port that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is listening on.</span></span> <span data-ttu-id="310c6-122">如果叢集服務將無法連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，可能會看到類似如下的錯誤：</span><span class="sxs-lookup"><span data-stu-id="310c6-122">If the cluster service is unable to make a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you might see an error similar to the following:</span></span>  
<span data-ttu-id="310c6-123">**事件識別碼：1001：事件名稱：容錯移轉叢集資源鎖死。**</span><span class="sxs-lookup"><span data-stu-id="310c6-123">**Event ID: 1001: Event Name: Failover clustering resource deadlock.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="310c6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="310c6-124">See Also</span></span>  
 <span data-ttu-id="310c6-125">[伺服器網路組態](server-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="310c6-125">[Server Network Configuration](server-network-configuration.md) </span></span>  
 <span data-ttu-id="310c6-126">[SQL 虛擬伺服器用戶端連接的描述](https://support.microsoft.com/kb/273673) </span><span class="sxs-lookup"><span data-stu-id="310c6-126">[Description of SQL Virtual Server client connections](https://support.microsoft.com/kb/273673) </span></span>  
 [<span data-ttu-id="310c6-127">如何將靜態連接埠指派給 SQL Server 具名執行個體，並避免常見陷阱</span><span class="sxs-lookup"><span data-stu-id="310c6-127">How to assign a static port to a SQL Server named instance - and avoid a common pitfall</span></span>](https://blogs.msdn.com/b/arvindsh/archive/2012/09/08/how-to-assign-a-static-port-to-a-sql-server-named-instance-and-avoid-a-common-pitfall.aspx)  
  
  
