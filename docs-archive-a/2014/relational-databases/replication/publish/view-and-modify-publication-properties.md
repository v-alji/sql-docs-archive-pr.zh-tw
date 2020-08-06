---
title: 檢視及修改發行集屬性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- modifying replication properties, articles
- articles [SQL Server replication], modifying
- publications [SQL Server replication], properties
- articles [SQL Server replication], properties
- modifying replication properties, publications
- publications [SQL Server replication], modifying
ms.assetid: 27d72ea4-bcb6-48f2-b4aa-eb1410da7efc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 89b969bc3e285bbdc633a2b39d237968b216069a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585279"
---
# <a name="view-and-modify-publication-properties"></a><span data-ttu-id="f43d1-102">檢視及修改發行集屬性</span><span class="sxs-lookup"><span data-stu-id="f43d1-102">View and Modify Publication Properties</span></span>
  <span data-ttu-id="f43d1-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 Replication Management Objects (RMO)，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中檢視及修改發行集屬性。</span><span class="sxs-lookup"><span data-stu-id="f43d1-103">This topic describes how to view and modify publication properties in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="f43d1-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="f43d1-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f43d1-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="f43d1-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f43d1-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="f43d1-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f43d1-107">建議</span><span class="sxs-lookup"><span data-stu-id="f43d1-107">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="f43d1-108">**若要檢視及修改發行集屬性，請使用：**</span><span class="sxs-lookup"><span data-stu-id="f43d1-108">**To view and modify publication properties, using:**</span></span>  
  
     [<span data-ttu-id="f43d1-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f43d1-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f43d1-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f43d1-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="f43d1-111">Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="f43d1-111">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f43d1-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="f43d1-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f43d1-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="f43d1-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f43d1-114">有些屬性在建立了發行集後無法再修改，而另一些當存在發行集的訂閱時便無法修改。</span><span class="sxs-lookup"><span data-stu-id="f43d1-114">Some properties cannot be modified after a publication has been created, and others cannot be modified if there are subscriptions to the publication.</span></span> <span data-ttu-id="f43d1-115">無法修改的屬性以唯讀顯示。</span><span class="sxs-lookup"><span data-stu-id="f43d1-115">Properties that cannot be modified are displayed as read-only.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="f43d1-116">建議</span><span class="sxs-lookup"><span data-stu-id="f43d1-116">Recommendations</span></span>  
  
-   <span data-ttu-id="f43d1-117">建立發行集之後，某些屬性變更需要新的快照集。</span><span class="sxs-lookup"><span data-stu-id="f43d1-117">After a publication is created, some property changes require a new snapshot.</span></span> <span data-ttu-id="f43d1-118">如果發行集有訂閱，則某些變更還需要重新初始化所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="f43d1-118">If a publication has subscriptions, some changes also require all subscriptions to be reinitialized.</span></span> <span data-ttu-id="f43d1-119">如需詳細資訊，請參閱[變更發行集與發行項屬性](change-publication-and-article-properties.md)和[在現有發行集中新增和卸除發行項](add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="f43d1-119">For more information, see [Change Publication and Article Properties](change-publication-and-article-properties.md) and [Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f43d1-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f43d1-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f43d1-121">您可在位於 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 與複寫監視器的 [發行集屬性 - \<Publication>] 對話方塊中檢視及修改發行集屬性。</span><span class="sxs-lookup"><span data-stu-id="f43d1-121">View and modify publication properties in the **Publication Properties - \<Publication>** dialog box, which is available in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and Replication Monitor.</span></span> <span data-ttu-id="f43d1-122">如需啟動複寫監視器的詳細資訊，請參閱[啟動複寫監視器](../monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="f43d1-122">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="f43d1-123">[發行集屬性 - \<Publication>] 對話方塊包含下列頁面：</span><span class="sxs-lookup"><span data-stu-id="f43d1-123">The **Publication Properties - \<Publication>** dialog box includes the following pages:</span></span>  
  
-   <span data-ttu-id="f43d1-124">**[一般]** 頁面包含發行集名稱和描述、發行集類型以及訂閱過期設定。</span><span class="sxs-lookup"><span data-stu-id="f43d1-124">The **General** page includes the publication name and description, the database name, the type of publication, and the subscription expiration settings.</span></span>  
  
-   <span data-ttu-id="f43d1-125">**[發行項]** 頁面對應「新增發行集精靈」中的 **[發行項]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="f43d1-125">The **Articles** page corresponds to the **Articles** page in the New Publication Wizard.</span></span> <span data-ttu-id="f43d1-126">此頁面用於新增及刪除發行項，以及變更發行項的屬性與資料行篩選。</span><span class="sxs-lookup"><span data-stu-id="f43d1-126">Use this page to add and delete articles, and to change properties and column filtering for articles.</span></span>  
  
-   <span data-ttu-id="f43d1-127">**[篩選資料列]** 頁面對應「新增發行集精靈」中的 **[篩選資料表的資料列]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="f43d1-127">The **Filter Rows** page corresponds to the **Filter Table Rows** page in the New Publication Wizard.</span></span> <span data-ttu-id="f43d1-128">此頁面用於新增、編輯和刪除所有類型發行集的靜態資料列篩選，以及新增、編輯和刪除合併式發行集的參數化資料列篩選器和聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="f43d1-128">Use this page to add, edit, and delete static row filters for all types of publications, and to add, edit, and delete parameterized row filters and join filters for merge publications.</span></span>  
  
-   <span data-ttu-id="f43d1-129">**[快照集]** 頁面允許您指定快照集的格式和位置、是否應壓縮快照集，以及套用快照集前後要執行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="f43d1-129">The **Snapshot** page allows you to specify the format and location of the snapshot, whether the snapshot should be compressed, and scripts to run before and after the snapshot is applied.</span></span>  
  
-   <span data-ttu-id="f43d1-130">**[FTP 快照集]** 頁面 (針對快照式和交易式發行集，以及執行 SQL Server 2005 之前版本之「發行者」的合併式發行集) 允許您指定「訂閱者」是否可以透過「檔案傳輸通訊協定」(FTP) 下載快照集檔案。</span><span class="sxs-lookup"><span data-stu-id="f43d1-130">The **FTP Snapshot** page (for snapshot and transactional publications, and merge publications for Publishers running versions prior to SQL Server 2005) allows you to specify whether Subscribers can download snapshot files through File Transfer Protocol (FTP).</span></span>  
  
-   <span data-ttu-id="f43d1-131">**[FTP 快照集和網際網路]** 頁面 (針對執行 SQL Server 2005 或更新版本之「發行者」的合併式發行集) 允許您指定「訂閱者」是否可以透過 FTP 下載快照集檔案，以及「訂閱者」是否可以透過 HTTP 同步處理訂閱。</span><span class="sxs-lookup"><span data-stu-id="f43d1-131">The **FTP Snapshot and Internet** page (for merge publications from Publishers running SQL Server 2005 or later) allows you to specify whether Subscribers can download snapshot files through FTP, and whether Subscribers can synchronize subscriptions through HTTPS.</span></span>  
  
-   <span data-ttu-id="f43d1-132">**[訂閱選項]** 頁面允許您設定套用至所有訂閱的一些選項。</span><span class="sxs-lookup"><span data-stu-id="f43d1-132">The **Subscription Options** page allows you to set a number of options that apply to all subscriptions.</span></span> <span data-ttu-id="f43d1-133">選項視發行集類型的不同而不同。</span><span class="sxs-lookup"><span data-stu-id="f43d1-133">The options differ depending on the type of publication.</span></span>  
  
-   <span data-ttu-id="f43d1-134">**[發行集存取清單]** 頁面允許您指定可存取發行集的登入和群組。</span><span class="sxs-lookup"><span data-stu-id="f43d1-134">The **Publication Access List** page allows you to specify which logins and groups can access a publication.</span></span>  
  
-   <span data-ttu-id="f43d1-135">**[代理程式安全性]** 頁面允許您存取執行以下代理程式之帳戶的設定，並與複寫拓撲中的電腦建立連接：所有發行集的「快照集代理程式」；所有交易式發行集的「記錄讀取器代理程式」；及允許佇列更新訂閱之交易式發行集的「佇列讀取器代理程式」。</span><span class="sxs-lookup"><span data-stu-id="f43d1-135">The **Agent Security** page allows you to access settings for the accounts under which the following agents run and make connections to the computers in a replication topology: the Snapshot Agent for all publications; the Log Reader Agent for all transactional publications; and the Queue Reader Agent for transactional publications that allow queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="f43d1-136">**[資料分割]** 頁面 (針對執行 SQL Server 2005 或更新版本之「發行者」的合併式發行集) 允許您指定至含參數化篩選之發行集的「訂閱者」是否可以在一個快照集不可用時要求另一個快照集。</span><span class="sxs-lookup"><span data-stu-id="f43d1-136">The **Data Partitions** page (for merge publications from Publishers running SQL Server 2005 or later) allows you to specify whether Subscribers to publications with parameterized filters can request a snapshot if one is not available.</span></span> <span data-ttu-id="f43d1-137">它還允許您為一個或多個資料分割一次性或按循環排程產生快照集。</span><span class="sxs-lookup"><span data-stu-id="f43d1-137">It also allows you to generate snapshots for one or more partitions, either once or on a recurring schedule.</span></span>  
  
#### <a name="to-view-and-modify-publication-properties-in-management-studio"></a><span data-ttu-id="f43d1-138">若要在 Management Studio 中檢視和修改發行集屬性</span><span class="sxs-lookup"><span data-stu-id="f43d1-138">To view and modify publication properties in Management Studio</span></span>  
  
1.  <span data-ttu-id="f43d1-139">連接到 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中的發行者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="f43d1-139">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="f43d1-140">展開 **[複寫]** 資料夾，然後展開 **[本機發行集]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f43d1-140">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="f43d1-141">以滑鼠右鍵按一下發行集，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="f43d1-141">Right-click a publication, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="f43d1-142">必要時修改任何屬性，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="f43d1-142">Modify any properties if necessary, and then click **OK**.</span></span>  
  
#### <a name="to-view-and-modify-publication-properties-in-replication-monitor"></a><span data-ttu-id="f43d1-143">若要在複寫監視器中檢視和修改發行集屬性</span><span class="sxs-lookup"><span data-stu-id="f43d1-143">To view and modify publication properties in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="f43d1-144">展開「複寫監視器」左窗格中的「發行者」群組，然後展開一個「發行者」。</span><span class="sxs-lookup"><span data-stu-id="f43d1-144">Expand a Publisher group in the left pane of Replication Monitor, and then expand a Publisher.</span></span>  
  
2.  <span data-ttu-id="f43d1-145">以滑鼠右鍵按一下發行集，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="f43d1-145">Right-click a publication, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="f43d1-146">必要時修改任何屬性，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="f43d1-146">Modify any properties if necessary, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f43d1-147">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f43d1-147">Using Transact-SQL</span></span>  
 <span data-ttu-id="f43d1-148">您可以使用複寫預存程序來以程式設計的方式修改發行集及傳回其屬性。</span><span class="sxs-lookup"><span data-stu-id="f43d1-148">Publications can be modified and their properties returned programmatically using replication stored procedures.</span></span> <span data-ttu-id="f43d1-149">您使用的預存程序將根據發行集的類型而定。</span><span class="sxs-lookup"><span data-stu-id="f43d1-149">The stored procedures that you use will depend on the type of publication.</span></span>  
  
#### <a name="to-view-the-properties-of-a-snapshot-or-transactional-publication"></a><span data-ttu-id="f43d1-150">檢視快照式或交易式發行集的屬性</span><span class="sxs-lookup"><span data-stu-id="f43d1-150">To view the properties of a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="f43d1-151">執行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)，為 **\@publication** 參數指定發行集的名稱。</span><span class="sxs-lookup"><span data-stu-id="f43d1-151">Execute [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql), specifying the name of the publication for the **\@publication** parameter.</span></span> <span data-ttu-id="f43d1-152">如果您不指定這個參數，就會傳回發行者上與所有發行集有關的資訊。</span><span class="sxs-lookup"><span data-stu-id="f43d1-152">If you do not specify this parameter, information on all publications at the Publisher is returned.</span></span>  
  
#### <a name="to-change-the-properties-of-a-snapshot-or-transactional-publication"></a><span data-ttu-id="f43d1-153">變更快照式或交易式發行集的屬性</span><span class="sxs-lookup"><span data-stu-id="f43d1-153">To change the properties of a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="f43d1-154">執行 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)，在 **\@property** 參數中指定要變更的發行集屬性，並在 **\@value** 參數中指定這個屬性的新值。</span><span class="sxs-lookup"><span data-stu-id="f43d1-154">Execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying the publication property to change in the **\@property** parameter and the new value of this property in the **\@value** parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f43d1-155">如果此變更需要產生新的快照集，您也必須為 **\@force_invalidate_snapshot** 指定 **1** 值；如果此變更需要重新初始化訂閱者，則您必須為 **\@force_reinit_subscription** 指定 **1** 值。</span><span class="sxs-lookup"><span data-stu-id="f43d1-155">If the change will require the generation of a new snapshot, you must also specify a value of **1** for **\@force_invalidate_snapshot**, and if the change will require that Subscribers be reinitialized, you must specify a value of **1** for **\@force_reinit_subscription**.</span></span> <span data-ttu-id="f43d1-156">如需當變更時需要新的快照集或重新初始化之屬性的詳細資訊，請參閱[變更發行集與發行項屬性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f43d1-156">For more information on the properties that, when changed, require a new snapshot or reinitialization, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
#### <a name="to-view-the-properties-of-a-merge-publication"></a><span data-ttu-id="f43d1-157">檢視合併式發行集的屬性</span><span class="sxs-lookup"><span data-stu-id="f43d1-157">To view the properties of a merge publication</span></span>  
  
1.  <span data-ttu-id="f43d1-158">執行 [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)，為 **\@publication** 參數指定發行集的名稱。</span><span class="sxs-lookup"><span data-stu-id="f43d1-158">Execute [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specifying the name of the publication for the **\@publication** parameter.</span></span> <span data-ttu-id="f43d1-159">如果您不指定這個參數，就會傳回發行者上與所有發行集有關的資訊。</span><span class="sxs-lookup"><span data-stu-id="f43d1-159">If you do not specify this parameter, information on all publications at the Publisher is returned.</span></span>  
  
#### <a name="to-change-the-properties-of-a-merge-publication"></a><span data-ttu-id="f43d1-160">變更合併式發行集的屬性</span><span class="sxs-lookup"><span data-stu-id="f43d1-160">To change the properties of a merge publication</span></span>  
  
1.  <span data-ttu-id="f43d1-161">執行 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)，在 **\@property** 參數中指定要變更的發行集屬性，並在 **\@value** 參數中指定這個屬性的新值。</span><span class="sxs-lookup"><span data-stu-id="f43d1-161">Execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying the publication property being changed in the **\@property** parameter and the new value of this property in the **\@value** parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f43d1-162">如果此變更需要產生新的快照集，您也必須為 **\@force_invalidate_snapshot** 指定 **1** 值；如果此變更將需要重新初始化訂閱者，則您必須為 **\@force_reinit_subscription** 指定 **1** 值。如需變更時需要新快照集或重新初始化的屬性詳細資訊，請參閱[變更發行集與發行項屬性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f43d1-162">If the change will require the generation of a new snapshot, you must also specify a value of **1** for **\@force_invalidate_snapshot**, and if the change will require that Subscribers be reinitialized, you must specify a value of **1** for **\@force_reinit_subscription** For more information on the properties that, when changed, require a new snapshot or reinitialization, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
#### <a name="to-view-the-properties-of-a-snapshot"></a><span data-ttu-id="f43d1-163">檢視快照集的屬性</span><span class="sxs-lookup"><span data-stu-id="f43d1-163">To view the properties of a snapshot</span></span>  
  
1.  <span data-ttu-id="f43d1-164">執行 [sp_helppublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql)，為 **\@publication** 參數指定發行集的名稱。</span><span class="sxs-lookup"><span data-stu-id="f43d1-164">Execute [sp_helppublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql), specifying the name of the publication for the **\@publication** parameter.</span></span>  
  
#### <a name="to-change-the-properties-of-a-snapshot"></a><span data-ttu-id="f43d1-165">變更快照集的屬性</span><span class="sxs-lookup"><span data-stu-id="f43d1-165">To change the properties of a snapshot</span></span>  
  
1.  <span data-ttu-id="f43d1-166">執行 [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql)，針對適當的快照集參數指定一或多個新的快照集屬性。</span><span class="sxs-lookup"><span data-stu-id="f43d1-166">Execute [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql), specifying one or more of the new snapshot properties for the appropriate snapshot parameters.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="f43d1-167">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f43d1-167">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="f43d1-168">這個異動複寫範例會傳回發行集的屬性。</span><span class="sxs-lookup"><span data-stu-id="f43d1-168">This transactional replication example returns the properties of the publication.</span></span>  
  
 [!code-sql[HowTo#sp_helppublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranpub.sql#sp_helppublication)]  
  
 <span data-ttu-id="f43d1-169">這個異動複寫範例會停用發行集的結構描述複寫。</span><span class="sxs-lookup"><span data-stu-id="f43d1-169">This transactional replication example disables schema replication for the publication.</span></span>  
  
 [!code-sql[HowTo#sp_changepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranpub.sql#sp_changepublication)]  
  
 <span data-ttu-id="f43d1-170">這個合併式複寫範例會傳回發行集的屬性。</span><span class="sxs-lookup"><span data-stu-id="f43d1-170">This merge replication example returns the properties of the publication.</span></span>  
  
 [!code-sql[HowTo#sp_helpmergepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergepub.sql#sp_helpmergepublication)]  
  
 <span data-ttu-id="f43d1-171">這個合併式複寫範例會停用發行集的結構描述複寫。</span><span class="sxs-lookup"><span data-stu-id="f43d1-171">This merge replication example disables schema replication for the publication.</span></span>  
  
 [!code-sql[HowTo#sp_changemergepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergepub.sql#sp_changemergepublication)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="f43d1-172">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="f43d1-172">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="f43d1-173">您可以使用 Replication Management Objects (RMO) 以程式設計的方式修改發行集及存取其屬性。</span><span class="sxs-lookup"><span data-stu-id="f43d1-173">You can modify publications and access their properties programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="f43d1-174">用來檢視或修改發行集屬性的 RMO 類別，將取決於發行集的類型而定。</span><span class="sxs-lookup"><span data-stu-id="f43d1-174">The RMO classes that you use to view or modify publication properties depend on the type of publication.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-snapshot-or-transactional-publication"></a><span data-ttu-id="f43d1-175">檢視或修改快照式或交易式發行集的屬性</span><span class="sxs-lookup"><span data-stu-id="f43d1-175">To view or modify properties of a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="f43d1-176">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="f43d1-176">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="f43d1-177">建立 <xref:Microsoft.SqlServer.Replication.TransPublication> 類別的執行個體、為發行集設定 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 屬性，以及將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定為步驟 1 中所建立的連接。</span><span class="sxs-lookup"><span data-stu-id="f43d1-177">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPublication> class, set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
3.  <span data-ttu-id="f43d1-178">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="f43d1-178">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="f43d1-179">如果此方法傳回 `false`，則表示步驟 2 中的發行集屬性定義不正確，或者該發行集不存在。</span><span class="sxs-lookup"><span data-stu-id="f43d1-179">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="f43d1-180">(選擇性) 若要變更屬性，請針對一或多個可設定的屬性設定新的值。</span><span class="sxs-lookup"><span data-stu-id="f43d1-180">(Optional) To change properties, set a new value for one or more of the settable properties.</span></span> <span data-ttu-id="f43d1-181">使用邏輯 AND 運算子 (Microsoft Visual C# 中的 `&` 及 Microsoft Visual Basic 中的 `And`)，以判斷是否已針對 <xref:Microsoft.SqlServer.Replication.PublicationAttributes> 屬性設定給定的 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="f43d1-181">Use the logical AND operator (`&` in Microsoft Visual C# and `And` in Microsoft Visual Basic) to determine if a given <xref:Microsoft.SqlServer.Replication.PublicationAttributes> value is set for the <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> property.</span></span> <span data-ttu-id="f43d1-182">使用包含的邏輯 OR 運算子 (Visual C# 中的 `|` 和 Visual Basic 中的 `Or`)，並使用排除的邏輯 OR 運算子 (Visual C# 中的 `^` 和 Visual Basic 中的 `Xor`)，為 <xref:Microsoft.SqlServer.Replication.PublicationAttributes> 屬性變更 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="f43d1-182">Use the inclusive logical OR operator (`|` in Visual C# and `Or` in Visual Basic) and the exclusive logical OR operator (`^` in Visual C# and `Xor` in Visual Basic) to change the <xref:Microsoft.SqlServer.Replication.PublicationAttributes> values for the <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> property.</span></span>  
  
5.  <span data-ttu-id="f43d1-183">(選擇性) 如果您已針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 指定 `true` 的值，請呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法來認可伺服器上的變更。</span><span class="sxs-lookup"><span data-stu-id="f43d1-183">(Optional) If you specified a value of `true` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit changes on the server.</span></span> <span data-ttu-id="f43d1-184">如果您已針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 指定 `false` 的值 (預設值)，則會立即將變更傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="f43d1-184">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (the default), changes are sent to the server immediately.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-merge-publication"></a><span data-ttu-id="f43d1-185">檢視或修改合併式發行集的屬性</span><span class="sxs-lookup"><span data-stu-id="f43d1-185">To view or modify properties of a merge publication</span></span>  
  
1.  <span data-ttu-id="f43d1-186">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="f43d1-186">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="f43d1-187">建立 <xref:Microsoft.SqlServer.Replication.MergePublication> 類別的執行個體、為發行集設定 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 屬性，以及將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定為步驟 1 中所建立的連接。</span><span class="sxs-lookup"><span data-stu-id="f43d1-187">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class, set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
3.  <span data-ttu-id="f43d1-188">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="f43d1-188">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="f43d1-189">如果此方法傳回 `false`，則表示步驟 2 中的發行集屬性定義不正確，或者該發行集不存在。</span><span class="sxs-lookup"><span data-stu-id="f43d1-189">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="f43d1-190">(選擇性) 若要變更屬性，請針對一或多個可設定的屬性設定新的值。</span><span class="sxs-lookup"><span data-stu-id="f43d1-190">(Optional) To change properties, set a new value for one or more of the settable properties.</span></span> <span data-ttu-id="f43d1-191">使用邏輯 AND 運算子 (Visual C# 中的 `&` 及 Visual Basic 中的 `And`)，以判斷是否已針對 <xref:Microsoft.SqlServer.Replication.PublicationAttributes> 屬性設定給定的 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="f43d1-191">Use the logical AND operator (`&` in Visual C# and `And` in Visual Basic) to determine if a given <xref:Microsoft.SqlServer.Replication.PublicationAttributes> value is set for the <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> property.</span></span> <span data-ttu-id="f43d1-192">使用包含的邏輯 OR 運算子 (Visual C# 中的 `|` 和 Visual Basic 中的 `Or`)，並使用排除的邏輯 OR 運算子 (Visual C# 中的 `^` 和 Visual Basic 中的 `Xor`)，為 <xref:Microsoft.SqlServer.Replication.PublicationAttributes> 屬性變更 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="f43d1-192">Use the inclusive logical OR operator (`|` in Visual C# and `Or` in Visual Basic) and the exclusive logical OR operator (`^` in Visual C# and `Xor` in Visual Basic) to change the <xref:Microsoft.SqlServer.Replication.PublicationAttributes> values for the <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> property.</span></span>  
  
5.  <span data-ttu-id="f43d1-193">(選擇性) 如果您已針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 指定 `true` 的值，請呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法來認可伺服器上的變更。</span><span class="sxs-lookup"><span data-stu-id="f43d1-193">(Optional) If you specified a value of `true` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit changes on the server.</span></span> <span data-ttu-id="f43d1-194">如果您已針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 指定 `false` 的值 (預設值)，則會立即將變更傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="f43d1-194">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (the default), changes are sent to the server immediately.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="f43d1-195">範例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="f43d1-195">Examples (RMO)</span></span>  
 <span data-ttu-id="f43d1-196">此範例會設定交易式發行集的發行集屬性。</span><span class="sxs-lookup"><span data-stu-id="f43d1-196">This example sets publication attributes for a transactional publication.</span></span> <span data-ttu-id="f43d1-197">這些變更在明確傳送到伺服器之前，會先加以快取。</span><span class="sxs-lookup"><span data-stu-id="f43d1-197">The changes are cached until explicitly sent to the server.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeTranPub_cached](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changetranpub_cached)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeTranPub_cached](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changetranpub_cached)]  
  
 <span data-ttu-id="f43d1-198">此範例會停用合併式發行集的 DDL 複寫。</span><span class="sxs-lookup"><span data-stu-id="f43d1-198">This example disables DDL replication for a merge publication.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeMergePub_ddl](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changemergepub_ddl)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergePub_ddl](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changemergepub_ddl)]  
  
## <a name="see-also"></a><span data-ttu-id="f43d1-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f43d1-199">See Also</span></span>  
 <span data-ttu-id="f43d1-200">[發行資料和資料庫物件](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="f43d1-200">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="f43d1-201">[變更發行集與發行項屬性](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="f43d1-201">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="f43d1-202">[對發行集資料庫進行結構描述變更](make-schema-changes-on-publication-databases.md) </span><span class="sxs-lookup"><span data-stu-id="f43d1-202">[Make Schema Changes on Publication Databases](make-schema-changes-on-publication-databases.md) </span></span>  
 <span data-ttu-id="f43d1-203">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="f43d1-203">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 <span data-ttu-id="f43d1-204">[在發行集中加入和卸載文章](add-articles-to-and-drop-articles-from-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="f43d1-204">[Add Articles to and Drop Articles from a Publication](add-articles-to-and-drop-articles-from-a-publication.md) </span></span>  
 <span data-ttu-id="f43d1-205">[使用複寫監視器來檢視資訊及執行工作](../monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="f43d1-205">[View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="f43d1-206">檢視和修改發行項屬性</span><span class="sxs-lookup"><span data-stu-id="f43d1-206">View and Modify Article Properties</span></span>](view-and-modify-article-properties.md)  
  
  
