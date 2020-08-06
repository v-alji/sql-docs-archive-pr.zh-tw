---
title: 將次要資料庫聯結至可用性群組 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.joindbs.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- secondary databases [SQL Server]
- Availability Groups [SQL Server], joining
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: fd7efe79-c1f9-497d-bfe7-b2a2b2321cf5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b0d79325bcde33d13688003de079a42a9601cc41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595270"
---
# <a name="join-a-secondary-database-to-an-availability-group-sql-server"></a><span data-ttu-id="832e6-102">將次要資料庫聯結至可用性群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="832e6-102">Join a Secondary Database to an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="832e6-103">此主題說明如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]或 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中的 PowerShell，將次要資料庫聯結至 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="832e6-103">This topic explains how to join a secondary database to an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="832e6-104">當您準備次要複本的次要資料庫之後，您必須盡快將此資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="832e6-104">After you prepare a secondary database for a secondary replica, you need to join the database to the availability group as soon as possible.</span></span> <span data-ttu-id="832e6-105">這會從對應的主要資料庫開始將資料移動到次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="832e6-105">This will start data movement from the corresponding primary database to the secondary database.</span></span>  
  
-   <span data-ttu-id="832e6-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="832e6-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="832e6-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="832e6-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="832e6-108">安全性</span><span class="sxs-lookup"><span data-stu-id="832e6-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="832e6-109">**若要使用下列項目來準備次要資料庫：**</span><span class="sxs-lookup"><span data-stu-id="832e6-109">**To prepare a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="832e6-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="832e6-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="832e6-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="832e6-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="832e6-112">PowerShell</span><span class="sxs-lookup"><span data-stu-id="832e6-112">PowerShell</span></span>](#PowerShellProcedure)  
  
> [!NOTE]  
>  <span data-ttu-id="832e6-113">如需次要資料庫加入群組後會發生什麼情況的詳細資訊，請參閱[AlwaysOn 可用性群組 &#40;SQL Server&#41;的總覽](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="832e6-113">For information about what happens after a secondary database joins the group, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="832e6-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="832e6-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="832e6-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="832e6-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="832e6-116">您必須連接到裝載次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="832e6-116">You must be connected to the server instance that hosts the secondary replica.</span></span>  
  
-   <span data-ttu-id="832e6-117">次要複本必須已經加入可用性群組。</span><span class="sxs-lookup"><span data-stu-id="832e6-117">The secondary replica must already be joined to the availability group.</span></span> <span data-ttu-id="832e6-118">如需詳細資訊，請參閱 [將次要複本聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="832e6-118">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
-   <span data-ttu-id="832e6-119">最近必須已經準備次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="832e6-119">The secondary database must have been prepared recently.</span></span> <span data-ttu-id="832e6-120">如需詳細資訊，請參閱 [針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)中的 PowerShell，將次要資料庫聯結至 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="832e6-120">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="832e6-121">Security</span><span class="sxs-lookup"><span data-stu-id="832e6-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="832e6-122">權限</span><span class="sxs-lookup"><span data-stu-id="832e6-122">Permissions</span></span>  
 <span data-ttu-id="832e6-123">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="832e6-123">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="832e6-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="832e6-124">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="832e6-125">**若要將次要資料庫聯結至可用性群組**</span><span class="sxs-lookup"><span data-stu-id="832e6-125">**To join a secondary database to an availability group**</span></span>  
  
1.  <span data-ttu-id="832e6-126">在 [物件總管] 中，連接到裝載次要複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="832e6-126">In Object Explorer, connect to the server instance that hosts the secondary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="832e6-127">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="832e6-127">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="832e6-128">展開您要變更的可用性群組，然後擴展 **[可用性資料庫]** 節點。</span><span class="sxs-lookup"><span data-stu-id="832e6-128">Expand the availability group that you want to change, and expand the **Availability Databases** node.</span></span>  
  
4.  <span data-ttu-id="832e6-129">以滑鼠右鍵按一下資料庫，然後按一下 [加入可用性群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="832e6-129">Right-click the database, and click **Join to Availability Group**.</span></span>  
  
5.  <span data-ttu-id="832e6-130">這會開啟 **[將資料庫加入至可用性群組]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="832e6-130">This opens the **Join Databases to Availability Group** dialog box.</span></span> <span data-ttu-id="832e6-131">請確認顯示在標題列上的可用性群組名稱，以及顯示在方格中的資料庫名稱，然後按一下 **[確定]** 或按一下 **[取消]**。</span><span class="sxs-lookup"><span data-stu-id="832e6-131">Verify the availability group name, which is displayed on the title bar, and database name or names displayed in the grid, and click **OK**, or click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="832e6-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="832e6-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="832e6-133">**若要將次要資料庫聯結至可用性群組**</span><span class="sxs-lookup"><span data-stu-id="832e6-133">**To join a secondary database to an availability group**</span></span>  
  
1.  <span data-ttu-id="832e6-134">連接到裝載次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="832e6-134">Connect to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="832e6-135">使用 [ALTER DATABASE 陳述式的 SET HADR 子句](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="832e6-135">Use the [SET HADR clause of the ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) statement, as follows:</span></span>  
  
     <span data-ttu-id="832e6-136">ALTER DATABASE *database_name* SET HADR AVAILABILITY GROUP = *group_name*</span><span class="sxs-lookup"><span data-stu-id="832e6-136">ALTER DATABASE *database_name* SET HADR AVAILABILITY GROUP = *group_name*</span></span>  
  
     <span data-ttu-id="832e6-137">*database_name* 是要聯結的資料庫名稱，而 *group_name* 是可用性群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="832e6-137">where *database_name* is the name of a database to be joined and *group_name* is the name of the availability group.</span></span>  
  
     <span data-ttu-id="832e6-138">下列範例會將次要資料庫 `Db1` 聯結至 `MyAG` 可用性群組的本機次要複本。</span><span class="sxs-lookup"><span data-stu-id="832e6-138">The following example joins the secondary database, `Db1`, to the local secondary replica of the `MyAG` availability group.</span></span>  
  
    ```sql
    ALTER DATABASE Db1 SET HADR AVAILABILITY GROUP = MyAG;  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="832e6-139">若要查看內容中使用的這個 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式，請參閱 [建立可用性群組和 &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="832e6-139">To see this [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement used in context, see [Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="832e6-140">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="832e6-140">Using PowerShell</span></span>  
 <span data-ttu-id="832e6-141">**若要將次要資料庫聯結至可用性群組**</span><span class="sxs-lookup"><span data-stu-id="832e6-141">**To join a secondary database to an availability group**</span></span>  
  
1.  <span data-ttu-id="832e6-142">將目錄切換到 (`cd`) 裝載次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="832e6-142">Change directory (`cd`) to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="832e6-143">使用 `Add-SqlAvailabilityDatabase` 指令程式，將一個或多個次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="832e6-143">Use the `Add-SqlAvailabilityDatabase` cmdlet to join one or more secondary databases to the availability group.</span></span>  
  
     <span data-ttu-id="832e6-144">例如，下列命令會將次要資料庫 `Db1`聯結至裝載次要複本之其中一個伺服器執行個體上的可用性群組 `MyAG` 。</span><span class="sxs-lookup"><span data-stu-id="832e6-144">For example, the following command joins a secondary database, `Db1`, to the availability group `MyAG` on one of the server instances that hosts a secondary replica.</span></span>  
  
    ```powershell
    Add-SqlAvailabilityDatabase -Path SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAG -Database "Db1"  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="832e6-145">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="832e6-145">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="832e6-146">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="832e6-146">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="832e6-147">**若要設定和使用 SQL Server PowerShell 提供者**</span><span class="sxs-lookup"><span data-stu-id="832e6-147">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="832e6-148">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="832e6-148">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="832e6-149">相關工作</span><span class="sxs-lookup"><span data-stu-id="832e6-149">Related Tasks</span></span>  
  
-   [<span data-ttu-id="832e6-150">將次要複本聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="832e6-150">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="832e6-151">針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="832e6-151">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="832e6-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="832e6-152">See Also</span></span>  
 <span data-ttu-id="832e6-153">[ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="832e6-153">[ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) </span></span>  
 <span data-ttu-id="832e6-154">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="832e6-154">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="832e6-155">針對 AlwaysOn 可用性群組 Configuration &#40;SQL Server&#41;已刪除進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="832e6-155">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
