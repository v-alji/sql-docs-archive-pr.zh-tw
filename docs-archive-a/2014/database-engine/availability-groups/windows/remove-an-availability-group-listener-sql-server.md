---
title: 移除可用性群組接聽程式 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.removeaglistener.default.f1
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
ms.assetid: fd9bba9a-d29f-4c23-8ecd-aaa049ed5f1b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 057b9c137cb4d8bbbdd03be61df600f7e59b264c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593606"
---
# <a name="remove-an-availability-group-listener-sql-server"></a><span data-ttu-id="68cf3-102">移除可用性群組接聽程式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="68cf3-102">Remove an Availability Group Listener (SQL Server)</span></span>
  <span data-ttu-id="68cf3-103">本主題描述如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中的 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]或 PowerShell，從 AlwaysOn 可用性群組中移除可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="68cf3-103">This topic describes how to remove an availability group listener from an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="68cf3-104">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="68cf3-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="68cf3-105">先決條件</span><span class="sxs-lookup"><span data-stu-id="68cf3-105">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="68cf3-106">建議</span><span class="sxs-lookup"><span data-stu-id="68cf3-106">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="68cf3-107">安全性</span><span class="sxs-lookup"><span data-stu-id="68cf3-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="68cf3-108">**若要使用下列方法移除接聽程式：**</span><span class="sxs-lookup"><span data-stu-id="68cf3-108">**To remove a listener, using:**</span></span>  
  
     [<span data-ttu-id="68cf3-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="68cf3-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="68cf3-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="68cf3-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="68cf3-111">PowerShell</span><span class="sxs-lookup"><span data-stu-id="68cf3-111">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="68cf3-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="68cf3-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="68cf3-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="68cf3-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="68cf3-114">您必須連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="68cf3-114">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="68cf3-115">建議</span><span class="sxs-lookup"><span data-stu-id="68cf3-115">Recommendations</span></span>  
 <span data-ttu-id="68cf3-116">刪除可用性群組接聽程式之前，我們建議您先確定沒有應用程式正在使用接聽程式。</span><span class="sxs-lookup"><span data-stu-id="68cf3-116">Before you delete an availability group listener, we recommend that you ensure that no applications are using it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="68cf3-117">Security</span><span class="sxs-lookup"><span data-stu-id="68cf3-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="68cf3-118">權限</span><span class="sxs-lookup"><span data-stu-id="68cf3-118">Permissions</span></span>  
 <span data-ttu-id="68cf3-119">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="68cf3-119">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="68cf3-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="68cf3-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="68cf3-121">**若要移除可用性群組接聽程式**</span><span class="sxs-lookup"><span data-stu-id="68cf3-121">**To remove an availability group listener**</span></span>  
  
1.  <span data-ttu-id="68cf3-122">在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體，然後按一下伺服器名稱以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="68cf3-122">In Object Explorer, connect to the server instance that hosts the primary replica, and click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="68cf3-123">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="68cf3-123">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="68cf3-124">展開可用性群組的節點，然後展開 **[可用性群組接聽程式]** 節點。</span><span class="sxs-lookup"><span data-stu-id="68cf3-124">Expand the node of the availability group, and expand the **Availability Groups Listeners** node.</span></span>  
  
4.  <span data-ttu-id="68cf3-125">以滑鼠右鍵按一下要移除的接聽程式，然後選取 **[刪除]** 命令。</span><span class="sxs-lookup"><span data-stu-id="68cf3-125">Right-click the listener to be removed, and select the **Delete** command.</span></span>  
  
5.  <span data-ttu-id="68cf3-126">這樣就會開啟 **[從可用性群組移除接聽程式]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="68cf3-126">This opens the **Remove Listener from Availability Group** dialog box.</span></span> <span data-ttu-id="68cf3-127">如需詳細資訊，請參閱本主題稍後的＜ [從可用性群組移除接聽程式](#AgListenerPropertiesDialog)＞。</span><span class="sxs-lookup"><span data-stu-id="68cf3-127">For more information, see [Remove Listener from Availability Group](#AgListenerPropertiesDialog), later in this topic.</span></span>  
  
###  <a name="remove-listener-from-availability-group-dialog-box"></a><a name="AgListenerPropertiesDialog"></a><span data-ttu-id="68cf3-128">從 [可用性群組 (] 對話方塊中移除接聽程式) </span><span class="sxs-lookup"><span data-stu-id="68cf3-128">Remove Listener from Availability Group (Dialog Box)</span></span>  
 <span data-ttu-id="68cf3-129">**名稱**</span><span class="sxs-lookup"><span data-stu-id="68cf3-129">**Name**</span></span>  
 <span data-ttu-id="68cf3-130">要移除的接聽程式名稱。</span><span class="sxs-lookup"><span data-stu-id="68cf3-130">The name of the listener to be removed.</span></span>  
  
 <span data-ttu-id="68cf3-131">**結果**</span><span class="sxs-lookup"><span data-stu-id="68cf3-131">**Result**</span></span>  
 <span data-ttu-id="68cf3-132">顯示連結 ( **[成功]** 或 **[錯誤]**)，而且按一下即可取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="68cf3-132">Displays a link, either **Success** or **Error**, which you can click for more information.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="68cf3-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="68cf3-133">Using Transact-SQL</span></span>  
 <span data-ttu-id="68cf3-134">**若要移除可用性群組接聽程式**</span><span class="sxs-lookup"><span data-stu-id="68cf3-134">**To remove an availability group listener**</span></span>  
  
1.  <span data-ttu-id="68cf3-135">連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="68cf3-135">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="68cf3-136">使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 陳述式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="68cf3-136">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="68cf3-137">改變可用性群組*group_name*移除接聽程式 **' *`dns_name`* '**</span><span class="sxs-lookup"><span data-stu-id="68cf3-137">ALTER AVAILABILITY GROUP *group_name* REMOVE LISTENER **'*`dns_name`*'**</span></span>  
  
     <span data-ttu-id="68cf3-138">*group_name* 是可用性群組的名稱， *dns_name* 是可用性群組接聽程式的 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="68cf3-138">where *group_name* is the name of the availability group and *dns_name* is the DNS name of the availability group listener.</span></span>  
  
     <span data-ttu-id="68cf3-139">下列範例會刪除 `AccountsAG` 可用性群組的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="68cf3-139">The following example deletes the listener of the `AccountsAG` availability group.</span></span> <span data-ttu-id="68cf3-140">DNS 名稱是 AccountsAG_Listener。</span><span class="sxs-lookup"><span data-stu-id="68cf3-140">The DNS name is AccountsAG_Listener.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP AccountsAG REMOVE LISTENER 'AccountsAG_Listener';  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="68cf3-141">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="68cf3-141">Using PowerShell</span></span>  
 <span data-ttu-id="68cf3-142">**若要移除可用性群組接聽程式**</span><span class="sxs-lookup"><span data-stu-id="68cf3-142">**To remove an availability group listener**</span></span>  
  
1.  <span data-ttu-id="68cf3-143">將預設值 (`cd`) 設定為裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="68cf3-143">Set default (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="68cf3-144">使用內建的 `Remove-Item` 指令程式移除接聽程式。</span><span class="sxs-lookup"><span data-stu-id="68cf3-144">Use the built in `Remove-Item` cmdlet to remove a listener.</span></span> <span data-ttu-id="68cf3-145">例如，下列命令會從名為 `MyListener` 的可用性群組中移除名為 `MyAg`的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="68cf3-145">For example, the following command removes a listener named `MyListener` from an availability group named `MyAg`.</span></span>  
  
    ```powershell
    Remove-Item SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\MyListener  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="68cf3-146">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="68cf3-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="68cf3-147">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="68cf3-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="68cf3-148">相關工作</span><span class="sxs-lookup"><span data-stu-id="68cf3-148">Related Tasks</span></span>  
  
-   [<span data-ttu-id="68cf3-149">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="68cf3-149">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="68cf3-150">檢視可用性群組接聽程式屬性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="68cf3-150">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="68cf3-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68cf3-151">See Also</span></span>  
 <span data-ttu-id="68cf3-152">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="68cf3-152">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="68cf3-153">可用性群組接聽程式、用戶端連線及應用程式容錯移轉 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="68cf3-153">Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;</span></span>](../../listeners-client-connectivity-application-failover.md)  
