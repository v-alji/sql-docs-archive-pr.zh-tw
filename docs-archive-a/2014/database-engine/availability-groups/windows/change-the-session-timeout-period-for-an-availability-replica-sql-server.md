---
title: 變更可用性複本的工作階段逾時期限 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], session timeout
- session timeout [SQL Server]
ms.assetid: e23c6e06-1cd1-4d4a-9bc2-e3e06ab2933d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 302ba4a2b0b72a70b05e563eb4085913074469eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708673"
---
# <a name="change-the-session-timeout-period-for-an-availability-replica-sql-server"></a><span data-ttu-id="c195e-102">變更可用性複本的工作階段逾時期限 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c195e-102">Change the Session-Timeout Period for an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="c195e-103">本主題描述如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中的 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]或 PowerShell 來設定 AlwaysOn 可用性複本的工作階段逾時期限。</span><span class="sxs-lookup"><span data-stu-id="c195e-103">This topic describes how to configure the session-timeout period of an AlwaysOn availability replica by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="c195e-104">工作階段逾時期限是複本屬性，它會控制可用性複本將連接視為失敗之前等候連接複本發出 Ping 回應的秒數 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="c195e-104">The session-timeout period is a replica property that controls how many seconds (in seconds) that an availability replica waits for a ping response from a connected replica before considering the connection to have failed.</span></span> <span data-ttu-id="c195e-105">根據預設，複本會等候 Ping 回應的時間為 10 秒。</span><span class="sxs-lookup"><span data-stu-id="c195e-105">By default, a replica waits 10 seconds for a ping response.</span></span> <span data-ttu-id="c195e-106">這個複本屬性只適用於可用性群組之給定次要複本與主要複本之間的連接。</span><span class="sxs-lookup"><span data-stu-id="c195e-106">This replica property applies only the connection between a given secondary replica and the primary replica of the availability group.</span></span> <span data-ttu-id="c195e-107">如需工作階段逾時期間的詳細資訊，請參閱 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="c195e-107">For more information about the session-timeout period, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="c195e-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="c195e-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c195e-109">先決條件</span><span class="sxs-lookup"><span data-stu-id="c195e-109">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="c195e-110">建議</span><span class="sxs-lookup"><span data-stu-id="c195e-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="c195e-111">安全性</span><span class="sxs-lookup"><span data-stu-id="c195e-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c195e-112">**若要使用下列項目變更工作階段逾時期限：**</span><span class="sxs-lookup"><span data-stu-id="c195e-112">**To change the session-timeout period, using:**</span></span>  
  
     [<span data-ttu-id="c195e-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c195e-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c195e-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c195e-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="c195e-115">PowerShell</span><span class="sxs-lookup"><span data-stu-id="c195e-115">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c195e-116">開始之前</span><span class="sxs-lookup"><span data-stu-id="c195e-116">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="c195e-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="c195e-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="c195e-118">您必須連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="c195e-118">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="c195e-119">建議</span><span class="sxs-lookup"><span data-stu-id="c195e-119">Recommendations</span></span>  
 <span data-ttu-id="c195e-120">我們建議您讓逾時期限保持在 10 秒或更久。</span><span class="sxs-lookup"><span data-stu-id="c195e-120">We recommend that you keep the time-out period at 10 seconds or greater.</span></span> <span data-ttu-id="c195e-121">將這個值設定為小於 10 秒，可能會使負荷重的系統遺漏 PING 以及宣告假失敗。</span><span class="sxs-lookup"><span data-stu-id="c195e-121">Setting the value to less than 10 seconds creates the possibility of a heavily loaded system missing PINGs and declaring a false failure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c195e-122">Security</span><span class="sxs-lookup"><span data-stu-id="c195e-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c195e-123">權限</span><span class="sxs-lookup"><span data-stu-id="c195e-123">Permissions</span></span>  
 <span data-ttu-id="c195e-124">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="c195e-124">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c195e-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c195e-125">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="c195e-126">**若要變更可用性複本的工作階段逾時期限**</span><span class="sxs-lookup"><span data-stu-id="c195e-126">**To change the session-timeout period for an availability replica**</span></span>  
  
1.  <span data-ttu-id="c195e-127">在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="c195e-127">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="c195e-128">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="c195e-128">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="c195e-129">按一下您想要設定其可用性複本的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="c195e-129">Click the availability group whose availability replica you want to configure.</span></span>  
  
4.  <span data-ttu-id="c195e-130">以滑鼠右鍵按一下要設定的複本，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="c195e-130">Right-click the replica to be configured, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="c195e-131">在 **[可用性複本屬性]** 對話方塊中，使用 **[工作階段逾時 (秒)]** 欄位來變更此複本之工作階段逾時期限的秒數。</span><span class="sxs-lookup"><span data-stu-id="c195e-131">In the **Availability Replica Properties** dialog box, use the **Session timeout (seconds)** field to change the number of seconds for the session-timeout period on this replica.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c195e-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c195e-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="c195e-133">**若要變更可用性複本的工作階段逾時期限**</span><span class="sxs-lookup"><span data-stu-id="c195e-133">**To change the session-timeout period for an availability replica**</span></span>  
  
1.  <span data-ttu-id="c195e-134">連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="c195e-134">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="c195e-135">使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 陳述式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c195e-135">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="c195e-136">ALTER AVAILABILITY GROUP *group_name*</span><span class="sxs-lookup"><span data-stu-id="c195e-136">ALTER AVAILABILITY GROUP *group_name*</span></span>  
  
     <span data-ttu-id="c195e-137">MODIFY REPLICA ON '*instance_name*' WITH ( SESSION_TIMEOUT =*seconds* )</span><span class="sxs-lookup"><span data-stu-id="c195e-137">MODIFY REPLICA ON '*instance_name*' WITH ( SESSION_TIMEOUT =*seconds* )</span></span>  
  
     <span data-ttu-id="c195e-138">其中 *group_name* 是可用性群組的名稱、 *instance_name* 是裝載要修改之可用性複本的伺服器執行個體名稱，而 *seconds* 會指定複本將記錄套用至資料庫 (做為次要複本) 之前必須等候的最小秒數。</span><span class="sxs-lookup"><span data-stu-id="c195e-138">where *group_name* is the name of the availability group, *instance_name* is the name of the server instance that hosts the availability replica to be modified, and *seconds* specifies the minimum number of seconds that the replica must wait before applying log to databases when acting as a secondary replica.</span></span> <span data-ttu-id="c195e-139">預設值為 0 秒，表示沒有套用延遲。</span><span class="sxs-lookup"><span data-stu-id="c195e-139">The default is 0 seconds, which indicates that there is no apply delay.</span></span>  
  
     <span data-ttu-id="c195e-140">下列範例 (在 `AccountsAG` 可用性群組的主要複本上輸入) 會針對位於 `15` 伺服器執行個體上的複本，將工作階段逾時值變更為 `INSTANCE09` 秒。</span><span class="sxs-lookup"><span data-stu-id="c195e-140">The following example, entered on the primary replica of the `AccountsAG` availability group, changes the session-timeout value to `15` seconds for the replica located on the `INSTANCE09` server instance.</span></span>  
  
    ```  
    ALTER AVAILABILITY GROUP AccountsAG   
       MODIFY REPLICA ON 'INSTANCE09' WITH (SESSION_TIMEOUT = 15);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="c195e-141">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c195e-141">Using PowerShell</span></span>  

### <a name="to-change-the-session-timeout-period-for-an-availability-replica"></a><span data-ttu-id="c195e-142">若要變更可用性複本的工作階段逾時期限</span><span class="sxs-lookup"><span data-stu-id="c195e-142">To change the session-timeout period for an availability replica</span></span>
  
1.  <span data-ttu-id="c195e-143">變更目錄 (`cd`) 為裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="c195e-143">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="c195e-144">使用 `Set-SqlAvailabilityReplica` 指令程式搭配 `SessionTimeout` 參數來變更指定可用性複本之工作階段逾時期限的秒數。</span><span class="sxs-lookup"><span data-stu-id="c195e-144">Use the `Set-SqlAvailabilityReplica` cmdlet with the `SessionTimeout` parameter to change the number of seconds for the session-timeout period on a specified availability replica.</span></span>  
  
     <span data-ttu-id="c195e-145">例如，下列命令會將工作階段逾時期限設定為 15 秒。</span><span class="sxs-lookup"><span data-stu-id="c195e-145">For example, the following command sets the session-timeout period to 15 seconds.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityReplica -SessionTimeout 15 -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="c195e-146">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="c195e-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="c195e-147">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="c195e-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="c195e-148">若要設定及使用 SQL Server PowerShell 提供者，請參閱[SQL Server PowerShell 提供者](../../../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="c195e-148">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c195e-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c195e-149">See Also</span></span>  
 [<span data-ttu-id="c195e-150">AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;</span><span class="sxs-lookup"><span data-stu-id="c195e-150">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
