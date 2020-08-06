---
title: 從 Oracle 資料庫建立發行集 | Microsoft 文件
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], Oracle databases
- Oracle publishing [SQL Server replication], configuring
ms.assetid: b3812746-14b0-4b22-809e-b4a95e1c8083
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 29e299e6f2a3b271fe682b319a2f22a671cbd19d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709153"
---
# <a name="create-a-publication-from-an-oracle-database"></a><span data-ttu-id="22e03-102">從 Oracle 資料庫建立發行集</span><span class="sxs-lookup"><span data-stu-id="22e03-102">Create a Publication from an Oracle Database</span></span>
  <span data-ttu-id="22e03-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 或 Replication Management Objects (RMO)，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中從 Oracle 資料庫建立發行集。</span><span class="sxs-lookup"><span data-stu-id="22e03-103">This topic describes how to create a publication from an Oracle database in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="22e03-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="22e03-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="22e03-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="22e03-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="22e03-106">先決條件</span><span class="sxs-lookup"><span data-stu-id="22e03-106">Prerequisites</span></span>](#Prerequisites)  
  
-   <span data-ttu-id="22e03-107">**若要從 Oracle 資料庫建立發行集，請使用：**</span><span class="sxs-lookup"><span data-stu-id="22e03-107">**To create a publication from an Oracle database, using:**</span></span>  
  
     [<span data-ttu-id="22e03-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="22e03-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="22e03-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="22e03-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="22e03-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="22e03-110">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="22e03-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="22e03-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="22e03-112">建立發行集之前，您必須先在「[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者」上安裝 Oracle 軟體，也必須設定 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="22e03-112">Before creating a publication, you must install Oracle software on the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor, and you must configure the Oracle database.</span></span> <span data-ttu-id="22e03-113">如需詳細資訊，請參閱[設定 Oracle 發行者](../non-sql/configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="22e03-113">For more information, see [Configure an Oracle Publisher](../non-sql/configure-an-oracle-publisher.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="22e03-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="22e03-114">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="22e03-115">使用「新增發行集精靈」從「Oracle 資料庫」建立快照式或交易式發行集。</span><span class="sxs-lookup"><span data-stu-id="22e03-115">Create a snapshot or transactional publication from an Oracle Database with the New Publication Wizard.</span></span>  
  
 <span data-ttu-id="22e03-116">第一次從 Oracle 資料庫建立發行集時，必須在「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者」端識別「Oracle 發行者」(如果是同一資料庫的後續發行集，則不需要執行這個動作)。</span><span class="sxs-lookup"><span data-stu-id="22e03-116">The first time you create a publication from an Oracle database, you must identify the Oracle Publisher at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor (you do not need to do this for subsequent publications from the same database.).</span></span> <span data-ttu-id="22e03-117">可從 [新增發行集精靈] 或 [散發者屬性 - \<Distributor>] 對話方塊來完成 Oracle 發行者的識別；本主題會顯示 [散發者屬性 - \<Distributor>] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="22e03-117">Identifying the Oracle Publisher can be accomplished from the New Publication Wizard or the **Distributor Properties - \<Distributor>** dialog box; this topic shows the **Distributor Properties - \<Distributor>** dialog box.</span></span>  
  
#### <a name="to-identify-the-oracle-publisher-at-the-sql-server-distributor"></a><span data-ttu-id="22e03-118">若要在 SQL Server 散發者端識別 Oracle 發行者</span><span class="sxs-lookup"><span data-stu-id="22e03-118">To identify the Oracle Publisher at the SQL Server Distributor</span></span>  
  
1.  <span data-ttu-id="22e03-119">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中，連接到「Oracle 發行者」將其做為「散發者」使用的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="22e03-119">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance that the Oracle Publisher will use as a Distributor, and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="22e03-120">以滑鼠右鍵按一下 **[複寫]** 資料夾，然後按一下 **[散發者屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="22e03-120">Right-click the **Replication** folder, and then click **Distributor Properties**.</span></span>  
  
3.  <span data-ttu-id="22e03-121">在 [散發者屬性 - \<Distributor>] 對話方塊的 [發行者] 頁面上，按一下 [新增]，然後按一下 [新增 Oracle 發行者]。</span><span class="sxs-lookup"><span data-stu-id="22e03-121">On the **Publishers** page of the **Distributor Properties - \<Distributor>** dialog box, click **Add**, and then click **Add Oracle Publisher**.</span></span>  
  
4.  <span data-ttu-id="22e03-122">在 **[連接到伺服器]** 對話方塊上，按一下 **[選項]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="22e03-122">In the **Connect to Server** dialog box, click the **Options** button.</span></span>  
  
5.  <span data-ttu-id="22e03-123">在 **[登入]** 索引標籤上：</span><span class="sxs-lookup"><span data-stu-id="22e03-123">On the **Login** tab:</span></span>  
  
    1.  <span data-ttu-id="22e03-124">在 **[伺服器執行個體]** 下拉式方塊中輸入 Oracle 資料庫執行個體名稱或選取 **[瀏覽其他]** 。</span><span class="sxs-lookup"><span data-stu-id="22e03-124">Enter the Oracle database instance name or select **Browse for more** in the **Server instance** combo box.</span></span>  
  
    2.  <span data-ttu-id="22e03-125">選取 **[Oracle 標準驗證]** (建議選項) 或 **[Windows 驗證]** 。</span><span class="sxs-lookup"><span data-stu-id="22e03-125">Select **Oracle Standard Authentication** (recommended) or **Windows Authentication**.</span></span>  
  
         <span data-ttu-id="22e03-126">如果您選取 **[Windows 驗證]** ：必須使用 Windows 認證將 Oracle 伺服器設定為允許連接 (如需詳細資訊，請參閱 Oracle 文件集)；並且您的目前登入帳戶必須與您為複寫管理的使用者結構描述指定的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 帳戶相同。</span><span class="sxs-lookup"><span data-stu-id="22e03-126">If you select **Windows Authentication**: the Oracle server must be configured to allow connections using Windows credentials (for more information, see the Oracle documentation); and you must be currently logged in with the same [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows account you specified for the replication administrative user schema.</span></span>  
  
    3.  <span data-ttu-id="22e03-127">如果您選取 **[Oracle 標準驗證]** ，則於設定期間輸入您在「Oracle 發行者」上建立的複寫管理使用者結構描述之登入和密碼。</span><span class="sxs-lookup"><span data-stu-id="22e03-127">If you select **Oracle Standard Authentication**, enter the login and password of the replication administrative user schema you created on the Oracle Publisher during configuration.</span></span>  
  
6.  <span data-ttu-id="22e03-128">在 **[連接屬性]** 索引標籤上，選取 **[閘道]** 或 **[完整]** 的「發行者」類型。</span><span class="sxs-lookup"><span data-stu-id="22e03-128">On the **Connection Properties** tab, select a Publisher type of **Gateway** or **Complete**.</span></span>  
  
     <span data-ttu-id="22e03-129">**[完整]** 選項可以為 Oracle 發行提供具有完整支援功能的快照式和交易式發行集。</span><span class="sxs-lookup"><span data-stu-id="22e03-129">The **Complete** option is designed to provide snapshot and transactional publications with the complete set of supported features for Oracle publishing.</span></span> <span data-ttu-id="22e03-130">**[閘道]** 選項可以在複寫作為系統之間的閘道時，提供特定的設計最佳化以提升效能。</span><span class="sxs-lookup"><span data-stu-id="22e03-130">The **Gateway** option provides specific design optimizations to improve performance for cases where replication serves as a gateway between systems.</span></span> <span data-ttu-id="22e03-131">如果您計畫在多個交易式發行集內發行相同的資料表，就無法使用 **[閘道]** 選項。</span><span class="sxs-lookup"><span data-stu-id="22e03-131">The **Gateway** option cannot be used if you plan to publish the same table in multiple transactional publications.</span></span> <span data-ttu-id="22e03-132">如果您選取 **[閘道]** ，則資料表最多只能在一個交易式發行集裡出現，但可以在任意數目的快照式發行集裡出現。</span><span class="sxs-lookup"><span data-stu-id="22e03-132">A table can appear in at most one transactional publication and any number of snapshot publications if you select **Gateway**.</span></span>  
  
7.  <span data-ttu-id="22e03-133">按一下 **[連接]** ，建立與「Oracle 發行者」的連接，並為複寫設定該連接。</span><span class="sxs-lookup"><span data-stu-id="22e03-133">Click **Connect**, which creates a connection to the Oracle Publisher and configures it for replication.</span></span> <span data-ttu-id="22e03-134">[連線到伺服器] 對話方塊隨即關閉，並會將您返回至 [散發者屬性 - \<Distributor>] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="22e03-134">The **Connect to Server** dialog box closes and you are returned to the **Distributor Properties - \<Distributor>** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="22e03-135">如果網路組態有問題，此時您會收到一條錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="22e03-135">If there are any problems with the network configuration, you will receive an error at this point.</span></span> <span data-ttu-id="22e03-136">如果您遇到連接到 Oracle 資料庫的問題，請參閱在＜ [Troubleshooting Oracle Publishers](../non-sql/troubleshooting-oracle-publishers.md)＞中的「SQL Server 散發者無法連接到 Oracle 資料庫執行個體」一節。</span><span class="sxs-lookup"><span data-stu-id="22e03-136">If you experience problems connecting to the Oracle database, see the section "The SQL Server Distributor cannot connect to the Oracle database instance" in [Troubleshooting Oracle Publishers](../non-sql/troubleshooting-oracle-publishers.md).</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-create-a-publication-from-an-oracle-database"></a><span data-ttu-id="22e03-137">若要從 Oracle 資料庫建立發行集</span><span class="sxs-lookup"><span data-stu-id="22e03-137">To create a publication from an Oracle database</span></span>  
  
1.  <span data-ttu-id="22e03-138">連接到「Oracle 發行者」將其做為「散發者」使用的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="22e03-138">Connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance that the Oracle Publisher will use as a Distributor, and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="22e03-139">展開 **[複寫]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="22e03-139">Expand the **Replication** folder.</span></span>  
  
3.  <span data-ttu-id="22e03-140">以滑鼠右鍵按一下 **[本機發行集]** 資料夾，然後按一下 **[新增 Oracle 發行集]** 。</span><span class="sxs-lookup"><span data-stu-id="22e03-140">Right-click the **Local Publications** folder, and then click **New Oracle Publication**.</span></span>  
  
4.  <span data-ttu-id="22e03-141">在「新增發行集精靈」的 **[Oracle 發行者]** 頁面，選取「Oracle 發行者」。</span><span class="sxs-lookup"><span data-stu-id="22e03-141">On the **Oracle Publisher** page of the New Publication Wizard, select the Oracle Publisher.</span></span> <span data-ttu-id="22e03-142">如果「Oracle 發行者」未顯示，按一下 **[新增 Oracle 發行者]** ，這會引領您繼續先前程序之後的步驟。</span><span class="sxs-lookup"><span data-stu-id="22e03-142">If the Oracle Publisher is not displayed, click **Add Oracle Publisher**, which takes you through the steps from the previous procedure.</span></span>  
  
5.  <span data-ttu-id="22e03-143">在 **[發行集類型]** 頁面上，選取 **[快照集發行集]** 或 **[交易式發行集]** 。</span><span class="sxs-lookup"><span data-stu-id="22e03-143">On the **Publication Type** page, select **Snapshot publication** or **Transactional publication**.</span></span>  
  
6.  <span data-ttu-id="22e03-144">在 **[發行項]** 頁面上，選取您要發行的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="22e03-144">On the **Articles** page, select the database objects you want to publish.</span></span>  
  
     <span data-ttu-id="22e03-145">或者，透過展開資料表，然後清除一個或多個資料行之核取方塊的方式，篩選出資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="22e03-145">Optionally, filter out table columns by expanding a table and then clearing the checkbox for one or more columns.</span></span> <span data-ttu-id="22e03-146">如有必要，按一下 **[發行項屬性]** 以檢視和修改發行項屬性，並指定替代資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="22e03-146">Click **Article Properties** to view and modify article properties and to specify alternative data type mappings if necessary.</span></span> <span data-ttu-id="22e03-147">若要指定資料類型對應的詳細資訊，請參閱[指定 Oracle 發行者的資料類型對應](specify-data-type-mappings-for-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="22e03-147">For more information about data type mappings, see [Specify Data Type Mappings for an Oracle Publisher](specify-data-type-mappings-for-an-oracle-publisher.md).</span></span>  
  
7.  <span data-ttu-id="22e03-148">在 **[篩選資料表的資料列]** 頁面，選擇性地套用篩選以發行一個或多個資料表的資料子集。</span><span class="sxs-lookup"><span data-stu-id="22e03-148">On the **Filter Table Rows** page, optionally apply filters to publish a subset of data from one or more tables.</span></span>  
  
8.  <span data-ttu-id="22e03-149">僅當在訂閱資料庫中已建立了所有物件，且已加入了所有需要的資料時，才能在 **[快照集代理程式]** 頁面清除 **[立即建立快照集]** 。</span><span class="sxs-lookup"><span data-stu-id="22e03-149">On the **Snapshot Agent** page, clear **Create a snapshot immediately** only if you have created all objects and added all required data in the subscription database.</span></span>  
  
9. <span data-ttu-id="22e03-150">在 **[代理程式安全性]** 頁面，指定「快照集代理程式」的認證 (針對所有發行集) 和「記錄讀取器代理程式」的認證 (針對交易式發行集)。</span><span class="sxs-lookup"><span data-stu-id="22e03-150">On the **Agent Security** page, specify credentials for the Snapshot Agent (for all publications) and the Log Reader Agent (for transactional publications).</span></span> <span data-ttu-id="22e03-151">代理程式會使用您指定的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Windows 帳戶之內容，執行並與「 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 散發者」建立連接。</span><span class="sxs-lookup"><span data-stu-id="22e03-151">The agents run and make connections to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor using the context of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows account you specify.</span></span> <span data-ttu-id="22e03-152">代理程式會使用您指定為複寫管理使用者結構描述的帳戶內容，與 Oracle 資料庫建立連接。</span><span class="sxs-lookup"><span data-stu-id="22e03-152">The agents make connections to the Oracle database using the context of the account you specified as the replication administrative user schema.</span></span> <span data-ttu-id="22e03-153">如需詳細資訊，請參閱[設定 Oracle 發行者](../non-sql/configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="22e03-153">For more information, see [Configure an Oracle Publisher](../non-sql/configure-an-oracle-publisher.md).</span></span>  
  
     <span data-ttu-id="22e03-154">如需各代理程式所需權限的詳細資訊，請參閱＜ [Replication Agent Security Model](../security/replication-agent-security-model.md) ＞和＜ [Replication Security Best Practices](../security/replication-security-best-practices.md)＞。</span><span class="sxs-lookup"><span data-stu-id="22e03-154">For more information about the permissions required by each agent, see [Replication Agent Security Model](../security/replication-agent-security-model.md) and [Replication Security Best Practices](../security/replication-security-best-practices.md).</span></span>  
  
10. <span data-ttu-id="22e03-155">在 **[精靈動作]** 頁面上，選擇性地為發行集編寫指令碼。</span><span class="sxs-lookup"><span data-stu-id="22e03-155">On the **Wizard Actions** page, optionally script the publication.</span></span> <span data-ttu-id="22e03-156">如需詳細資訊，請參閱 [Scripting Replication](../scripting-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="22e03-156">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
11. <span data-ttu-id="22e03-157">在 **[完成精靈]** 頁面上，指定發行集的名稱。</span><span class="sxs-lookup"><span data-stu-id="22e03-157">On the **Complete the Wizard** page, specify a name for the publication.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="22e03-158">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="22e03-158">Using Transact-SQL</span></span>  
 <span data-ttu-id="22e03-159">當 Oracle 資料庫已經設定為發行者之後，您可以使用系統預存程序來建立交易式或快照式發行集，就像是從 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 發行者建立一樣。</span><span class="sxs-lookup"><span data-stu-id="22e03-159">After the Oracle database has been configured as a Publisher, you can create a transactional or snapshot publication the same way that you would from a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Publisher, by using system stored procedures.</span></span>  
  
#### <a name="to-create-an-oracle-publication"></a><span data-ttu-id="22e03-160">建立 Oracle 發行集</span><span class="sxs-lookup"><span data-stu-id="22e03-160">To create an Oracle Publication</span></span>  
  
1.  <span data-ttu-id="22e03-161">將 Oracle 資料庫設定為發行者。</span><span class="sxs-lookup"><span data-stu-id="22e03-161">Configure the Oracle database as a Publisher.</span></span> <span data-ttu-id="22e03-162">如需詳細資訊，請參閱[設定 Oracle 發行者](../non-sql/configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="22e03-162">For more information, see [Configure an Oracle Publisher](../non-sql/configure-an-oracle-publisher.md).</span></span>  
  
2.  <span data-ttu-id="22e03-163">如果遠端散發者不存在，請設定遠端散發者。</span><span class="sxs-lookup"><span data-stu-id="22e03-163">If a remote Distributor does not exist, configure the remote Distributor.</span></span> <span data-ttu-id="22e03-164">如需詳細資訊，請參閱 [Configure Publishing and Distribution](../configure-publishing-and-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="22e03-164">For more information, see [Configure Publishing and Distribution](../configure-publishing-and-distribution.md).</span></span>  
  
3.  <span data-ttu-id="22e03-165">在 Oracle 發行者將使用的遠端散發者端，執行 [sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="22e03-165">At the remote Distributor that the Oracle Publisher will use, execute [sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql).</span></span> <span data-ttu-id="22e03-166">指定 TNS 的 Oracle 資料庫實例) 名稱的透明網路基 (底 **@publisher** ，以及的值 `ORACLE` 或 `ORACLE GATEWAY` **@publisher_type** 。</span><span class="sxs-lookup"><span data-stu-id="22e03-166">Specify the Transparent Network Substrate (TNS) name of the Oracle database instance for **@publisher** and a value of `ORACLE` or `ORACLE GATEWAY` for **@publisher_type**.</span></span> <span data-ttu-id="22e03-167">`Specify` 指定當從 Oracle 發行者連接到遠端 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者時所使用的安全性模式，如下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="22e03-167">`Specify` the security mode used when connecting from the Oracle Publisher to the remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor as one of the following:</span></span>  
  
    -   <span data-ttu-id="22e03-168">若要使用預設值 Oracle 標準驗證，請將 **@security_mode** 指定 **@security_mode**的值、將 **@login**指定為組態設定期間在 Oracle 發行者上建立之複寫管理使用者結構描述的登入，並將 **@password**中從 Oracle 資料庫建立發行集。</span><span class="sxs-lookup"><span data-stu-id="22e03-168">To use Oracle Standard Authentication, the default, specify a value of **0** for **@security_mode**, the login of the replication administrative user schema you created on the Oracle Publisher during configuration for **@login**, and the password for **@password**.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="22e03-169">可能的話，會在執行階段提示使用者輸入安全性認證。</span><span class="sxs-lookup"><span data-stu-id="22e03-169">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="22e03-170">如果您將認證儲存在指令碼檔案中，必須保護該檔案免於未經授權的存取。</span><span class="sxs-lookup"><span data-stu-id="22e03-170">If you store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
    -   <span data-ttu-id="22e03-171">若要使用「Windows 驗證」，請將 **@security_mode** 指定 **@security_mode**中從 Oracle 資料庫建立發行集。</span><span class="sxs-lookup"><span data-stu-id="22e03-171">To use Windows Authentication, specify a value of **1** for **@security_mode**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="22e03-172">若要使用「Windows 驗證」，必須使用 Windows 認證將 Oracle 伺服器設定為允許連接 (如需詳細資訊，請參閱 Oracle 文件集)；並且您目前的登入帳戶必須與您為複寫管理使用者結構描述指定的 Microsoft Windows 帳戶相同。</span><span class="sxs-lookup"><span data-stu-id="22e03-172">To use Windows Authentication, the Oracle server must be configured to allow connections using Windows credentials (for more information, see the Oracle documentation); and you must be currently logged in with the same Microsoft Windows account you specified for the replication administrative user schema..</span></span>  
  
4.  <span data-ttu-id="22e03-173">針對發行集資料庫建立記錄讀取器代理程式作業。</span><span class="sxs-lookup"><span data-stu-id="22e03-173">Create a Log Reader Agent job for the publication database.</span></span>  
  
    -   <span data-ttu-id="22e03-174">如果您不確定發行的資料庫是否有記錄讀取器代理程式作業存在，請在散發資料庫上由 Oracle 發行者使用的散發者端執行 [sp_helplogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="22e03-174">If you are unsure whether a Log Reader Agent job exists for a published database, execute [sp_helplogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql) at the Distributor used by the Oracle Publisher on the distribution database.</span></span> <span data-ttu-id="22e03-175">針對指定 Oracle 發行者的名稱 **@publisher** 。</span><span class="sxs-lookup"><span data-stu-id="22e03-175">Specify the name of the Oracle Publisher for **@publisher**.</span></span> <span data-ttu-id="22e03-176">如果結果集是空的，就必須建立記錄讀取器代理程式作業。</span><span class="sxs-lookup"><span data-stu-id="22e03-176">If the result set is empty, then a Log Reader Agent job must be created.</span></span>  
  
    -   <span data-ttu-id="22e03-177">如果記錄讀取器代理程式作業已存在發行集資料庫中，請繼續進行步驟 5。</span><span class="sxs-lookup"><span data-stu-id="22e03-177">If a Log Reader Agent job already exists for the publication database, proceed to step 5.</span></span>  
  
    -   <span data-ttu-id="22e03-178">在散發資料庫上由 Oracle 發行者使用的散發者端，執行 [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="22e03-178">At the Distributor used by the Oracle Publisher on the distribution database, execute [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql).</span></span> <span data-ttu-id="22e03-179">針對和指定執行代理程式所用的 Windows **@job_login** 認證 **@job_password** 。</span><span class="sxs-lookup"><span data-stu-id="22e03-179">Specify the Windows credentials under which the agent runs for **@job_login** and **@job_password**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="22e03-180">**@job_login**參數必須符合步驟3中所提供的登入。</span><span class="sxs-lookup"><span data-stu-id="22e03-180">The **@job_login** parameter must match the login supplied in step 3.</span></span> <span data-ttu-id="22e03-181">請勿提供發行者安全性資訊。</span><span class="sxs-lookup"><span data-stu-id="22e03-181">Do not supply publisher security information.</span></span> <span data-ttu-id="22e03-182">記錄讀取器代理程式會使用步驟 3 中所提供的安全性資訊連接到發行者。</span><span class="sxs-lookup"><span data-stu-id="22e03-182">The Log Reader agent connects to the Publisher using the security information provided in step 3.</span></span>  
  
5.  <span data-ttu-id="22e03-183">在散發資料庫的散發者端，執行 [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) 來建立發行集。</span><span class="sxs-lookup"><span data-stu-id="22e03-183">At the Distributor on the distribution database, execute [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) to create the publication.</span></span> <span data-ttu-id="22e03-184">如需詳細資訊，請參閱[建立發行集](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="22e03-184">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
6.  <span data-ttu-id="22e03-185">在散發資料庫的散發者端，執行 [sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="22e03-185">At the Distributor on the distribution database, execute [sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql).</span></span> <span data-ttu-id="22e03-186">針對指定步驟4中所使用的發行集名稱 **@publication** ，以及針對和執行快照集代理程式的 Windows **@job_name** 認證 **@password** 。</span><span class="sxs-lookup"><span data-stu-id="22e03-186">Specify the publication name used in step 4 for **@publication** and the Windows credentials under which the Snapshot Agent runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="22e03-187">若要在連接到發行者時使用「Oracle 標準驗證」，您也必須針對 **@security_mode** 指定 **@publisher_security_mode** 的值，以及針對 **@publisher_login** ＞和＜ **@publisher_password**中從 Oracle 資料庫建立發行集。</span><span class="sxs-lookup"><span data-stu-id="22e03-187">To use Oracle Standard Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher_security_mode** and the Oracle login information for **@publisher_login** and **@publisher_password**.</span></span> <span data-ttu-id="22e03-188">這麼做會為發行集建立快照集代理程式作業。</span><span class="sxs-lookup"><span data-stu-id="22e03-188">This creates a Snapshot Agent job for the publication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22e03-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22e03-189">See Also</span></span>  
 <span data-ttu-id="22e03-190">[設定 Oracle 發行者](../non-sql/configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="22e03-190">[Configure an Oracle Publisher](../non-sql/configure-an-oracle-publisher.md) </span></span>  
 <span data-ttu-id="22e03-191">[發行資料和資料庫物件](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="22e03-191">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="22e03-192">[設定 Oracle 發行者的交易集作業 &#40;複寫 Transact-SQL 程式設計&#41;](../administration/configure-the-transaction-set-job-for-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="22e03-192">[Configure the Transaction Set Job for an Oracle Publisher &#40;Replication Transact-SQL Programming&#41;](../administration/configure-the-transaction-set-job-for-an-oracle-publisher.md) </span></span>  
 <span data-ttu-id="22e03-193">[Oracle 發行概觀](../non-sql/oracle-publishing-overview.md) </span><span class="sxs-lookup"><span data-stu-id="22e03-193">[Oracle Publishing Overview](../non-sql/oracle-publishing-overview.md) </span></span>  
 [<span data-ttu-id="22e03-194">授與 Oracle 權限的指令碼</span><span class="sxs-lookup"><span data-stu-id="22e03-194">Script to Grant Oracle Permissions</span></span>](../non-sql/script-to-grant-oracle-permissions.md)  
  
  
