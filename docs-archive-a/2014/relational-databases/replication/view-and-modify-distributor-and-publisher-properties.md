---
title: 檢視及修改散發者和發行者屬性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- Distributors [SQL Server replication], modifying
- modifying replication properties, Distributors
- Distributors [SQL Server replication], properties
ms.assetid: 5dae1d59-c377-4c6e-adc9-b68c5b328f79
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 571f6f3a0d44f0fc87c67885249fca441776946d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593921"
---
# <a name="view-and-modify-distributor-and-publisher-properties"></a><span data-ttu-id="6e2b7-102">檢視及修改散發者和發行者屬性</span><span class="sxs-lookup"><span data-stu-id="6e2b7-102">View and Modify Distributor and Publisher Properties</span></span>
  <span data-ttu-id="6e2b7-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 Replication Management Objects (RMO)，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視及修改「散發者」和「發行者」屬性。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-103">This topic describes how to view and modify Distributor and Publisher properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="6e2b7-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="6e2b7-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6e2b7-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="6e2b7-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6e2b7-106">建議</span><span class="sxs-lookup"><span data-stu-id="6e2b7-106">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="6e2b7-107">安全性</span><span class="sxs-lookup"><span data-stu-id="6e2b7-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6e2b7-108">**若要檢視及修改「散發者」和「發行者」屬性，請使用：**</span><span class="sxs-lookup"><span data-stu-id="6e2b7-108">**To view and modify Distributor and Publisher properties, using:**</span></span>  
  
     [<span data-ttu-id="6e2b7-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6e2b7-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6e2b7-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6e2b7-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="6e2b7-111">Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="6e2b7-111">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6e2b7-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="6e2b7-112">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="6e2b7-113">建議</span><span class="sxs-lookup"><span data-stu-id="6e2b7-113">Recommendations</span></span>  
  
-   <span data-ttu-id="6e2b7-114">對於執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 之前版本的「發行者」，**sysadmin** 固定伺服器角色中的使用者可在 [訂閱者] 頁面上註冊「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-114">For Publishers running versions prior to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], a user in the **sysadmin** fixed server role can register Subscribers on the **Subscribers** page.</span></span> <span data-ttu-id="6e2b7-115">從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]開始，它不再需要明確註冊複寫的「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-115">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], it is no longer necessary to explicitly register Subscribers for replication.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6e2b7-116">Security</span><span class="sxs-lookup"><span data-stu-id="6e2b7-116">Security</span></span>  
 <span data-ttu-id="6e2b7-117">可能的話，會在執行階段提示使用者輸入安全性認證。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-117">When possible, prompt users to enter security credentials at runtime.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6e2b7-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6e2b7-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-and-modify-distributor-properties"></a><span data-ttu-id="6e2b7-119">檢視和修改散發者屬性</span><span class="sxs-lookup"><span data-stu-id="6e2b7-119">To view and modify Distributor properties</span></span>  
  
1.  <span data-ttu-id="6e2b7-120">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的散發者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-120">Connect to the Distributor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="6e2b7-121">以滑鼠右鍵按一下 **[複寫]** 資料夾，然後按一下 **[散發者屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-121">Right-click the **Replication** folder, and then click **Distributor Properties**.</span></span>  
  
3.  <span data-ttu-id="6e2b7-122">檢視和修改 [散發者屬性 - \<Distributor>] 對話方塊中的屬性。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-122">View and modify properties in the **Distributor Properties - \<Distributor>** dialog box.</span></span>  
  
    -   <span data-ttu-id="6e2b7-123">若要檢視和修改散發資料庫的屬性，請按一下對話方塊中 [一般] 頁面上資料庫的屬性按鈕 ( **...** )。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-123">To view and modify properties for a distribution database, click the properties button (**...**) for the database on the **General** page of thedialog box.</span></span>  
  
    -   <span data-ttu-id="6e2b7-124">若要檢視和修改與「散發者」相關聯的「發行者」屬性，請按一下對話方塊中 **[發行者]** 頁面上「發行者」的屬性按鈕 ( **[...]** )。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-124">To view and modify Publisher properties associated with the Distributor, click the properties button (**...**) for the Publisher on the **Publishers** page of the dialog box.</span></span>  
  
    -   <span data-ttu-id="6e2b7-125">若要存取複寫代理程式的設定檔，請按一下對話方塊中 **[一般]** 頁面上的 **[設定檔預設值]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-125">To access profiles for replication agents, click the **Profile Defaults** button on the **General** page of the dialog box.</span></span> <span data-ttu-id="6e2b7-126">如需相關資訊，請參閱 [Replication Agent Profiles](agents/replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-126">For more information, see [Replication Agent Profiles](agents/replication-agent-profiles.md).</span></span>  
  
    -   <span data-ttu-id="6e2b7-127">若要變更在「發行者」端執行管理預存程序以及在「散發者」端更新資訊時所使用之帳戶的密碼，請在對話方塊中 **[發行者]** 頁面上的 **[密碼]** 和 **[確認密碼]** 方塊內輸入新的密碼。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-127">To change the password for the account used when administrative stored procedures execute at the Publisher and update information at the Distributor, enter a new password in the **Password** and **Confirm password** boxes on the **Publishers** page of the dialog box.</span></span> <span data-ttu-id="6e2b7-128">如需詳細資訊，請參閱[保護散發者](security/secure-the-distributor.md)。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-128">For more information, see [Secure the Distributor](security/secure-the-distributor.md).</span></span>  
  
4.  <span data-ttu-id="6e2b7-129">必要時修改任何屬性，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-129">Modify any properties if necessary, and then click **OK**.</span></span>  
  
#### <a name="to-view-and-modify-publisher-properties"></a><span data-ttu-id="6e2b7-130">檢視和修改發行者屬性</span><span class="sxs-lookup"><span data-stu-id="6e2b7-130">To view and modify Publisher properties</span></span>  
  
1.  <span data-ttu-id="6e2b7-131">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的發行者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-131">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="6e2b7-132">以滑鼠右鍵按一下 **[複寫]** 資料夾，然後按一下 **[發行者屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-132">Right-click the **Replication** folder, and then click **Publisher Properties**.</span></span>  
  
3.  <span data-ttu-id="6e2b7-133">在 [\*\*發行者屬性- \< Publisher > \*\* ] 對話方塊中，查看及修改屬性。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-133">View and modify properties in the **Publisher Properties - \< Publisher >** dialog box.</span></span>  
  
    -   <span data-ttu-id="6e2b7-134">**sysadmin** 固定伺服器角色中的使用者能啟用 **[發行集資料庫]** 頁面上複寫的資料庫。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-134">A user in the **sysadmin** fixed server role can enable databases for replication on the **Publication Databases** page.</span></span> <span data-ttu-id="6e2b7-135">啟用資料庫不會發行此資料庫；不過，它允許該資料庫之 **db_owner** 固定資料庫角色中的任何使用者在資料庫中建立一個或多個發行集。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-135">Enabling a database does not publish that database; rather, it allows any user in the **db_owner** fixed database role for that database to create one or more publications in the database.</span></span>  
  
4.  <span data-ttu-id="6e2b7-136">必要時修改任何屬性，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-136">Modify any properties if necessary, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6e2b7-137">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6e2b7-137">Using Transact-SQL</span></span>  
 <span data-ttu-id="6e2b7-138">您可以使用複寫預存程序來以程式設計的方式檢視發行者和散發者屬性。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-138">Publisher and Distributor properties can be viewed programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-view-distributor-and-distribution-database-properties"></a><span data-ttu-id="6e2b7-139">檢視散發者和散發資料庫屬性</span><span class="sxs-lookup"><span data-stu-id="6e2b7-139">To view Distributor and distribution database properties</span></span>  
  
1.  <span data-ttu-id="6e2b7-140">執行 [sp_helpdistributor](/sql/relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql) ，傳回有關散發者、散發資料庫和工作目錄的資訊。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-140">Execute [sp_helpdistributor](/sql/relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql) to return information about the Distributor, distribution database, and working directory.</span></span>  
  
2.  <span data-ttu-id="6e2b7-141">執行 [sp_helpdistributiondb](/sql/relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql) ，傳回指定之散發資料庫的屬性。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-141">Execute [sp_helpdistributiondb](/sql/relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql) to return properties of a specified distribution database.</span></span>  
  
#### <a name="to-change-distributor-and-distribution-database-properties"></a><span data-ttu-id="6e2b7-142">變更散發者和散發資料庫屬性</span><span class="sxs-lookup"><span data-stu-id="6e2b7-142">To change Distributor and distribution database properties</span></span>  
  
1.  <span data-ttu-id="6e2b7-143">在散發者上，執行 [sp_changedistributor_property](/sql/relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql) 來修改散發者屬性。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-143">At the Distributor, execute [sp_changedistributor_property](/sql/relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql) to modify Distributor properties.</span></span>  
  
2.  <span data-ttu-id="6e2b7-144">在散發者上，執行 [sp_changedistributiondb](/sql/relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql) 來修改散發資料庫屬性。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-144">At the Distributor, execute [sp_changedistributiondb](/sql/relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql) to modify distribution database properties.</span></span>  
  
3.  <span data-ttu-id="6e2b7-145">在散發者上，執行 [sp_changedistributor_password](/sql/relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql) 來變更散發者密碼。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-145">At the Distributor, execute [sp_changedistributor_password](/sql/relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql) to change the Distributor password.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6e2b7-146">可能的話，會在執行階段提示使用者輸入安全性認證。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-146">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="6e2b7-147">如果您將認證儲存在指令碼檔案中，必須保護該檔案免於未經授權的存取。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-147">If you must store credentials in a script file, secure the file to prevent unauthorized access.</span></span>  
  
4.  <span data-ttu-id="6e2b7-148">在散發者上，執行 [sp_changedistpublisher](/sql/relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql) 來變更使用此散發者之發行者的屬性。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-148">At the Distributor, execute [sp_changedistpublisher](/sql/relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql) to change the properties of a Publisher using the Distributor.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="6e2b7-149">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6e2b7-149">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="6e2b7-150">下列範例的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼會傳回有關散發者和散發資料庫的資訊。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-150">The following example [!INCLUDE[tsql](../../includes/tsql-md.md)] script returns information about the Distributor and distribution database.</span></span>  
  
 [!code-sql[HowTo#sp_helpdistributor](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_helpdistributor)]  
  
 [!code-sql[HowTo#sp_helpdistributiondb](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_helpdistributiondb)]  
  
 <span data-ttu-id="6e2b7-151">此範例會變更散發者的保留期限、連接散發者所使用的密碼，以及散發者檢查各種複寫代理程式之狀態的間隔 (也稱為活動訊號間隔)。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-151">This example changes retention periods for the Distributor, the password used when connecting to the Distributor, and the interval at which the Distributor checks the status of various replication agents (also known as the heartbeat interval).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6e2b7-152">可能的話，會在執行階段提示使用者輸入安全性認證。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-152">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="6e2b7-153">如果您將認證儲存在指令碼檔案中，必須保護該檔案免於未經授權的存取。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-153">If you must store credentials in a script file, secure the file to prevent unauthorized access.</span></span>  
  
 [!code-sql[HowTo#sp_changedistributor_property](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributor_property)]  
  
 [!code-sql[HowTo#sp_changedistributiondb](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributiondb)]  
  
 [!code-sql[HowTo#sp_changedistributor_password](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributor_password)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="6e2b7-154">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="6e2b7-154">Using Replication Management Objects (RMO)</span></span>  
  
#### <a name="to-view-and-modify-distributor-properties"></a><span data-ttu-id="6e2b7-155">檢視和修改散發者屬性</span><span class="sxs-lookup"><span data-stu-id="6e2b7-155">To view and modify Distributor properties</span></span>  
  
1.  <span data-ttu-id="6e2b7-156">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與散發者的連接。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-156">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="6e2b7-157">建立 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-157">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span> <span data-ttu-id="6e2b7-158">傳遞步驟 1 的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-158">Pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 1.</span></span>  
  
3.  <span data-ttu-id="6e2b7-159">(選擇性) 檢查 <xref:Microsoft.SqlServer.Replication.ReplicationServer.IsDistributor%2A> 屬性，確認目前連接的伺服器為散發者。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-159">(Optional) Check the <xref:Microsoft.SqlServer.Replication.ReplicationServer.IsDistributor%2A> property to verify that the currently connected server is a Distributor.</span></span>  
  
4.  <span data-ttu-id="6e2b7-160">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> 方法，從伺服器中取得屬性。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-160">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> method to get the properties from the server.</span></span>  
  
5.  <span data-ttu-id="6e2b7-161">(選擇性) 若要變更屬性，請針對 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 物件上可以設定的一或多個散發者屬性設定新的值。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-161">(Optional) To change properties, set a new value for one or more of the Distributor properties that can be set on the <xref:Microsoft.SqlServer.Replication.ReplicationServer> object.</span></span>  
  
6.  <span data-ttu-id="6e2b7-162">(選擇性) 如果 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 物件上的 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 屬性設定為 `true`，請呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法來認可伺服器的變更。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-162">(Optional) If the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> property on the <xref:Microsoft.SqlServer.Replication.ReplicationServer> object is set to `true`, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit the changes to the server.</span></span>  
  
#### <a name="to-view-and-modify-distribution-database-properties"></a><span data-ttu-id="6e2b7-163">檢視及修改散發資料庫屬性</span><span class="sxs-lookup"><span data-stu-id="6e2b7-163">To view and modify distribution database properties</span></span>  
  
1.  <span data-ttu-id="6e2b7-164">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與散發者的連接。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-164">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="6e2b7-165">建立 <xref:Microsoft.SqlServer.Replication.DistributionDatabase> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-165">Create an instance of the <xref:Microsoft.SqlServer.Replication.DistributionDatabase> class.</span></span> <span data-ttu-id="6e2b7-166">指定 name 屬性，並傳遞步驟 1 中的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-166">Specify the name property and pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 1.</span></span>  
  
3.  <span data-ttu-id="6e2b7-167">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法，從伺服器中取得屬性。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-167">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties from the server.</span></span> <span data-ttu-id="6e2b7-168">如果此方法傳回 `false`，則表示伺服器上沒有指定之名稱的資料庫存在。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-168">If this method returns `false`, the database with the specified name does not exist on the server.</span></span>  
  
4.  <span data-ttu-id="6e2b7-169">(選擇性) 若要變更屬性，請針對其中一個可設定的 <xref:Microsoft.SqlServer.Replication.DistributionDatabase> 屬性設定新的值。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-169">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.DistributionDatabase> properties that can be set.</span></span>  
  
5.  <span data-ttu-id="6e2b7-170">(選擇性) 如果 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 物件上的 <xref:Microsoft.SqlServer.Replication.DistributionDatabase> 屬性設定為 `true`，請呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法來認可伺服器的變更。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-170">(Optional) If the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> property on the <xref:Microsoft.SqlServer.Replication.DistributionDatabase> object is set to `true`, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit the changes to the server.</span></span>  
  
#### <a name="to-view-and-modify-publisher-properties"></a><span data-ttu-id="6e2b7-171">檢視和修改發行者屬性</span><span class="sxs-lookup"><span data-stu-id="6e2b7-171">To view and modify Publisher properties</span></span>  
  
1.  <span data-ttu-id="6e2b7-172">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-172">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="6e2b7-173">建立 <xref:Microsoft.SqlServer.Replication.DistributionPublisher> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-173">Create an instance of the <xref:Microsoft.SqlServer.Replication.DistributionPublisher> class.</span></span> <span data-ttu-id="6e2b7-174">指定 <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> 屬性，並傳遞步驟 1 中的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-174">Specify the <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> property and pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 1.</span></span>  
  
3.  <span data-ttu-id="6e2b7-175">(選擇性) 若要變更屬性，請針對其中一個可設定的 <xref:Microsoft.SqlServer.Replication.DistributionPublisher> 屬性設定新的值。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-175">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.DistributionPublisher> properties that can be set.</span></span>  
  
4.  <span data-ttu-id="6e2b7-176">(選擇性) 如果 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 物件上的 <xref:Microsoft.SqlServer.Replication.DistributionPublisher> 屬性設定為 `true`，請呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法來認可伺服器的變更。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-176">(Optional) If the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> property on the <xref:Microsoft.SqlServer.Replication.DistributionPublisher> object is set to `true`, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit the changes to the server.</span></span>  
  
#### <a name="to-change-the-password-for-the-administrative-connection-from-the-publisher-to-the-distributor"></a><span data-ttu-id="6e2b7-177">變更從發行者到散發者之管理連接的密碼</span><span class="sxs-lookup"><span data-stu-id="6e2b7-177">To change the password for the administrative connection from the Publisher to the Distributor</span></span>  
  
1.  <span data-ttu-id="6e2b7-178">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與散發者的連接。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-178">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="6e2b7-179">建立 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-179">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span>  
  
3.  <span data-ttu-id="6e2b7-180">將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定為在步驟 1 中建立的連接。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-180">Set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="6e2b7-181">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-181">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> method to get the properties of the object.</span></span>  
  
5.  <span data-ttu-id="6e2b7-182">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-182">Call the <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> method.</span></span> <span data-ttu-id="6e2b7-183">針對 *password* 參數傳遞新的密碼值。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-183">Pass the new password value for the *password* parameter.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6e2b7-184">可能的話，會在執行階段提示使用者輸入安全性認證。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-184">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="6e2b7-185">如果您必須儲存認證，請使用 [Windows .NET Framework 提供的](https://go.microsoft.com/fwlink/?LinkId=34733) 密碼編譯服務 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-185">If you must store credentials, use the [cryptographic services](https://go.microsoft.com/fwlink/?LinkId=34733) provided by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.</span></span>  
  
6.  <span data-ttu-id="6e2b7-186">(選擇性) 請執行以下步驟，在使用此散發者的每一個遠端發行者上變更密碼：</span><span class="sxs-lookup"><span data-stu-id="6e2b7-186">(Optional) Perform the following steps to change the password at each remote Publisher that uses this Distributor:</span></span>  
  
    1.  <span data-ttu-id="6e2b7-187">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-187">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
    2.  <span data-ttu-id="6e2b7-188">建立 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-188">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span>  
  
    3.  <span data-ttu-id="6e2b7-189">將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定為在步驟 6a 中建立的連接。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-189">Set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 6a.</span></span>  
  
    4.  <span data-ttu-id="6e2b7-190">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-190">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> method to get the properties of the object.</span></span>  
  
    5.  <span data-ttu-id="6e2b7-191">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-191">Call the <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> method.</span></span> <span data-ttu-id="6e2b7-192">針對 *password* 參數傳遞步驟 5 中的新密碼值。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-192">Pass the new password value from Step 5 for the *password* parameter.</span></span>  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="6e2b7-193">範例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="6e2b7-193">Example (RMO)</span></span>  
 <span data-ttu-id="6e2b7-194">這個範例會示範如何變更散發和散發資料庫的屬性。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-194">This example shows how to change Distribution and distribution database properties.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6e2b7-195">為了避免在程式碼中儲存認證，會在執行階段提供新的散發者密碼。</span><span class="sxs-lookup"><span data-stu-id="6e2b7-195">To avoid storing credentials in the code, the new Distributor password is supplied at runtime.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeDistPub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changedistpub)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeDistPub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changedistpub)]  
  
## <a name="see-also"></a><span data-ttu-id="6e2b7-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e2b7-196">See Also</span></span>  
 <span data-ttu-id="6e2b7-197">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="6e2b7-197">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 <span data-ttu-id="6e2b7-198">[停用發行和散發](disable-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="6e2b7-198">[Disable Publishing and Distribution](disable-publishing-and-distribution.md) </span></span>  
 <span data-ttu-id="6e2b7-199">[[設定散發]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="6e2b7-199">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="6e2b7-200">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="6e2b7-200">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 <span data-ttu-id="6e2b7-201">[散發者與發行者資訊指令碼](administration/distributor-and-publisher-information-script.md) </span><span class="sxs-lookup"><span data-stu-id="6e2b7-201">[Distributor and Publisher Information Script](administration/distributor-and-publisher-information-script.md) </span></span>  
 <span data-ttu-id="6e2b7-202">[Replication System Stored Procedures Concepts](concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="6e2b7-202">[Replication System Stored Procedures Concepts](concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="6e2b7-203">使用複寫監視器來檢視資訊及執行工作</span><span class="sxs-lookup"><span data-stu-id="6e2b7-203">View Information and Perform Tasks using Replication Monitor</span></span>](monitor/view-information-and-perform-tasks-replication-monitor.md)  
  
  
