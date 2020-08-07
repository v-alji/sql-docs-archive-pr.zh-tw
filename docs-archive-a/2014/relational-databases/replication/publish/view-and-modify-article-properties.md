---
title: 檢視和修改發行項屬性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_changearticle
- sp_helparticle
- viewing replication properties
- sp_changemergearticle
- sp_helpmergearticle
- modifying replication properties, articles
- articles [SQL Server replication], modifying
- articles [SQL Server replication], properties
ms.assetid: e71831fa-3d39-4e4a-9706-4d3a497082cc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8194b5cc2d4c4a2f1f116ca5a99ea16e18156f13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704030"
---
# <a name="view-and-modify-article-properties"></a><span data-ttu-id="213ac-102">檢視和修改發行項屬性</span><span class="sxs-lookup"><span data-stu-id="213ac-102">View and Modify Article Properties</span></span>
  <span data-ttu-id="213ac-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 Replication Management Objects (RMO)，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中檢視及修改發行項屬性。</span><span class="sxs-lookup"><span data-stu-id="213ac-103">This topic describes how to view and modify article properties in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="213ac-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="213ac-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="213ac-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="213ac-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="213ac-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="213ac-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="213ac-107">建議</span><span class="sxs-lookup"><span data-stu-id="213ac-107">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="213ac-108">**若要檢視和修改發行項屬性，請使用：**</span><span class="sxs-lookup"><span data-stu-id="213ac-108">**To view and modify article properties, using:**</span></span>  
  
     [<span data-ttu-id="213ac-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="213ac-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="213ac-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="213ac-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="213ac-111">Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="213ac-111">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="213ac-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="213ac-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="213ac-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="213ac-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="213ac-114">有些屬性在建立了發行集後無法再修改，而另一些當存在發行集的訂閱時便無法修改。</span><span class="sxs-lookup"><span data-stu-id="213ac-114">Some properties cannot be modified after a publication has been created, and others cannot be modified if there are subscriptions to the publication.</span></span> <span data-ttu-id="213ac-115">無法修改的屬性以唯讀顯示。</span><span class="sxs-lookup"><span data-stu-id="213ac-115">Properties that cannot be modified are displayed as read-only.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="213ac-116">建議</span><span class="sxs-lookup"><span data-stu-id="213ac-116">Recommendations</span></span>  
  
-   <span data-ttu-id="213ac-117">建立發行集之後，某些屬性變更需要新的快照集。</span><span class="sxs-lookup"><span data-stu-id="213ac-117">After a publication is created, some property changes require a new snapshot.</span></span> <span data-ttu-id="213ac-118">如果發行集有訂閱，則某些變更還需要重新初始化所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="213ac-118">If a publication has subscriptions, some changes also require all subscriptions to be reinitialized.</span></span> <span data-ttu-id="213ac-119">如需詳細資訊，請參閱[變更發行集與發行項屬性](change-publication-and-article-properties.md)和[在現有發行集中新增和卸除發行項](add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="213ac-119">For more information, see [Change Publication and Article Properties](change-publication-and-article-properties.md) and [Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="213ac-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="213ac-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="213ac-121">您可在位於 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 和複寫監視器的 [發行集屬性 - \<Publication>] 對話方塊中檢視及修改發行項屬性。</span><span class="sxs-lookup"><span data-stu-id="213ac-121">View and modify article properties in the **Publication Properties - \<Publication>** dialog box, which is available in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and Replication Monitor.</span></span> <span data-ttu-id="213ac-122">如需啟動複寫監視器的詳細資訊，請參閱[啟動複寫監視器](../monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="213ac-122">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="213ac-123">**[一般]** 頁面包含發行集名稱和描述、發行集類型以及訂閱過期設定。</span><span class="sxs-lookup"><span data-stu-id="213ac-123">The **General** page includes the publication name and description, the database name, the type of publication, and the subscription expiration settings.</span></span>  
  
-   <span data-ttu-id="213ac-124">**[發行項]** 頁面對應「新增發行集精靈」中的 **[發行項]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="213ac-124">The **Articles** page corresponds to the **Articles** page in the New Publication Wizard.</span></span> <span data-ttu-id="213ac-125">此頁面用於新增及刪除發行項，以及變更發行項的屬性與資料行篩選。</span><span class="sxs-lookup"><span data-stu-id="213ac-125">Use this page to add and delete articles, and to change properties and column filtering for articles.</span></span>  
  
-   <span data-ttu-id="213ac-126">**[篩選資料列]** 頁面對應「新增發行集精靈」中的 **[篩選資料表的資料列]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="213ac-126">The **Filter Rows** page corresponds to the **Filter Table Rows** page in the New Publication Wizard.</span></span> <span data-ttu-id="213ac-127">此頁面用於新增、編輯和刪除所有類型發行集的靜態資料列篩選，以及新增、編輯和刪除合併式發行集的參數化資料列篩選器和聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="213ac-127">Use this page to add, edit, and delete static row filters for all types of publications, and to add, edit, and delete parameterized row filters and join filters for merge publications.</span></span>  
  
-   <span data-ttu-id="213ac-128">**[快照集]** 頁面允許您指定快照集的格式和位置、是否應壓縮快照集，以及套用快照集前後要執行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="213ac-128">The **Snapshot** page allows you to specify the format and location of the snapshot, whether the snapshot should be compressed, and scripts to run before and after the snapshot is applied.</span></span>  
  
-   <span data-ttu-id="213ac-129">**[FTP 快照集]** 頁面 (針對快照式和交易式發行集，以及執行 SQL Server 2005 之前版本之「發行者」的合併式發行集) 允許您指定「訂閱者」是否可以透過「檔案傳輸通訊協定」(FTP) 下載快照集檔案。</span><span class="sxs-lookup"><span data-stu-id="213ac-129">The **FTP Snapshot** page (for snapshot and transactional publications, and merge publications for Publishers running versions prior to SQL Server 2005) allows you to specify whether Subscribers can download snapshot files through File Transfer Protocol (FTP).</span></span>  
  
-   <span data-ttu-id="213ac-130">**[FTP 快照集和網際網路]** 頁面 (針對執行 SQL Server 2005 或更新版本之「發行者」的合併式發行集) 允許您指定「訂閱者」是否可以透過 FTP 下載快照集檔案，以及「訂閱者」是否可以透過 HTTP 同步處理訂閱。</span><span class="sxs-lookup"><span data-stu-id="213ac-130">The **FTP Snapshot and Internet** page (for merge publications from Publishers running SQL Server 2005 or later) allows you to specify whether Subscribers can download snapshot files through FTP, and whether Subscribers can synchronize subscriptions through HTTPS.</span></span>  
  
-   <span data-ttu-id="213ac-131">**[訂閱選項]** 頁面允許您設定套用至所有訂閱的一些選項。</span><span class="sxs-lookup"><span data-stu-id="213ac-131">The **Subscription Options** page allows you to set a number of options that apply to all subscriptions.</span></span> <span data-ttu-id="213ac-132">選項視發行集類型的不同而不同。</span><span class="sxs-lookup"><span data-stu-id="213ac-132">The options differ depending on the type of publication.</span></span>  
  
-   <span data-ttu-id="213ac-133">**[發行集存取清單]** 頁面允許您指定可存取發行集的登入和群組。</span><span class="sxs-lookup"><span data-stu-id="213ac-133">The **Publication Access List** page allows you to specify which logins and groups can access a publication.</span></span>  
  
-   <span data-ttu-id="213ac-134">**[代理程式安全性]** 頁面允許您存取執行以下代理程式之帳戶的設定，並與複寫拓撲中的電腦建立連接：所有發行集的「快照集代理程式」；所有交易式發行集的「記錄讀取器代理程式」；及允許佇列更新訂閱之交易式發行集的「佇列讀取器代理程式」。</span><span class="sxs-lookup"><span data-stu-id="213ac-134">The **Agent Security** page allows you to access settings for the accounts under which the following agents run and make connections to the computers in a replication topology: the Snapshot Agent for all publications; the Log Reader Agent for all transactional publications; and the Queue Reader Agent for transactional publications that allow queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="213ac-135">**[資料分割]** 頁面 (針對執行 SQL Server 2005 或更新版本之「發行者」的合併式發行集) 允許您指定至含參數化篩選之發行集的「訂閱者」是否可以在一個快照集不可用時要求另一個快照集。</span><span class="sxs-lookup"><span data-stu-id="213ac-135">The **Data Partitions** page (for merge publications from Publishers running SQL Server 2005 or later) allows you to specify whether Subscribers to publications with parameterized filters can request a snapshot if one is not available.</span></span> <span data-ttu-id="213ac-136">它還允許您為一個或多個資料分割一次性或按循環排程產生快照集。</span><span class="sxs-lookup"><span data-stu-id="213ac-136">It also allows you to generate snapshots for one or more partitions, either once or on a recurring schedule.</span></span>  
  
#### <a name="to-view-and-modify-article-properties"></a><span data-ttu-id="213ac-137">若要檢視和修改發行項屬性</span><span class="sxs-lookup"><span data-stu-id="213ac-137">To view and modify article properties</span></span>  
  
1.  <span data-ttu-id="213ac-138">在 [發行集屬性 - \<Publication>]  對話方塊的 [發行項] 頁面上，選取一個發行項，然後按一下 [發行項屬性]。</span><span class="sxs-lookup"><span data-stu-id="213ac-138">On the **Articles** Page of the **Publication Properties - \<Publication>** dialog box, select an article, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="213ac-139">選取應套用發行項屬性變更的物件︰</span><span class="sxs-lookup"><span data-stu-id="213ac-139">Select which articles property changes should apply to:</span></span>  
  
    -   <span data-ttu-id="213ac-140">按一下 [設定醒目提示 \<ObjectType> 發行項的屬性]，以啟動 [發行項屬性 - \<ObjectName>] 對話方塊；在這個對話方塊中所做屬性變更只會套用至 [發行項] 頁面上物件窗格中醒目提示的物件。</span><span class="sxs-lookup"><span data-stu-id="213ac-140">Click **Set Properties of Highlighted \<ObjectType> Article** to launch the **Article Properties - \<ObjectName>** dialog box; property changes made in this dialog box are applied only to the object that is highlighted in the object pane on the **Articles** page.</span></span>  
  
    -   <span data-ttu-id="213ac-141">按一下 [設定所有 \<ObjectType> 發行項的屬性]，以啟動 [所有 \<ObjectType> 發行項的屬性] 對話方塊；在這個對話方塊中所做的屬性變更會套用至 [發行項] 頁面上物件窗格中屬於該類型的所有物件，包含尚未選取發行的物件。</span><span class="sxs-lookup"><span data-stu-id="213ac-141">Click **Set Properties of All \<ObjectType> Articles**, to launch the **Properties for All \<ObjectType> Articles** dialog box; property changes made in this dialog box are applied to all objects of that type in the object pane on the **Articles** page, including ones not yet selected for publication.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="213ac-142">在 [所有 \<ObjectType> 發行項的屬性] 對話方塊中所做屬性變更，會覆寫先前在 [發行項屬性 - \<ObjectName>] 對話方塊中所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="213ac-142">Property changes made in the **Properties for All \<ObjectType> Articles** dialog box override any made previously in the **Article Properties - \<ObjectName>** dialog box.</span></span> <span data-ttu-id="213ac-143">例如，若要設定所有屬於某物件類型之發行項的一些預設值，但同時要設定個別物件的某些屬性，則請先設定所有發行項的預設值，</span><span class="sxs-lookup"><span data-stu-id="213ac-143">If, for example, you want to set a number of defaults for all articles of an object type, but also want to set some properties for individual objects, set the defaults for all articles first.</span></span> <span data-ttu-id="213ac-144">然後再設定個別物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="213ac-144">Then set the properties for the individual objects.</span></span>  
  
3.  <span data-ttu-id="213ac-145">必要時修改任何屬性，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="213ac-145">Modify any properties if necessary, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="213ac-146">在 [發行集屬性 - \<Publication>] 對話方塊上，按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="213ac-146">Click **OK** on the **Publication Properties - \<Publication>** dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="213ac-147">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="213ac-147">Using Transact-SQL</span></span>  
 <span data-ttu-id="213ac-148">您可以使用複寫預存程序來以程式設計的方式修改發行項及傳回其屬性。</span><span class="sxs-lookup"><span data-stu-id="213ac-148">Articles can be modified and their properties returned programmatically using replication stored procedures.</span></span> <span data-ttu-id="213ac-149">使用哪些預存程序要依發行項所屬的發行集類型而定。</span><span class="sxs-lookup"><span data-stu-id="213ac-149">The stored procedures that you use depend on the type of publication to which the article belongs.</span></span>  
  
#### <a name="to-view-the-properties-of-an-article-belonging-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="213ac-150">檢視屬於快照式或交易式發行集之發行項的屬性</span><span class="sxs-lookup"><span data-stu-id="213ac-150">To view the properties of an article belonging to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="213ac-151">執行[sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)，並針對發行集參數指定發行集的名稱，並針對\*\* \@ 發行\*\* \*\* \@ 項參數指定\*\*發行項的名稱。</span><span class="sxs-lookup"><span data-stu-id="213ac-151">Execute [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql), specifying the name of the publication for the **\@publication** parameter and the name of the article for the **\@article** parameter.</span></span> <span data-ttu-id="213ac-152">如果您未指定發行\*\* \@ \*\*項，則會針對發行集中的所有文章傳回信息。</span><span class="sxs-lookup"><span data-stu-id="213ac-152">If you do not specify **\@article**, information will be returned for all articles in the publication.</span></span>  
  
2.  <span data-ttu-id="213ac-153">針對資料表發行項執行 [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) ，以列出基底資料表中可用的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="213ac-153">Execute [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) for table articles to list all columns available in the base table.</span></span>  
  
#### <a name="to-modify-the-properties-of-an-article-belonging-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="213ac-154">修改屬於快照式或交易式發行集之發行項的屬性</span><span class="sxs-lookup"><span data-stu-id="213ac-154">To modify the properties of an article belonging to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="213ac-155">執行[sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)，在\*\* \@ property**參數中指定要變更的發行項屬性，並在** \@ value\*\*參數中指定這個屬性的新值。</span><span class="sxs-lookup"><span data-stu-id="213ac-155">Execute [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql), specifying the article property being changed in the **\@property** parameter and the new value of this property in the **\@value** parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="213ac-156">如果變更需要產生新的快照集，您也必須為\*\* \@ force_invalidate_snapshot**指定**1**的值，而且如果變更需要重新初始化訂閱者，您也必須為** \@ force_reinit_subscription**指定**1\*\*的值。</span><span class="sxs-lookup"><span data-stu-id="213ac-156">If the change requires the generation of a new snapshot, you must also specify a value of **1** for **\@force_invalidate_snapshot**, and if the change requires that Subscribers be reinitialized, you must also specify a value of **1** for **\@force_reinit_subscription**.</span></span> <span data-ttu-id="213ac-157">如需當變更時需要新的快照集或重新初始化之屬性的詳細資訊，請參閱[變更發行集與發行項屬性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="213ac-157">For more information on the properties that, when changed, require a new snapshot or reinitialization, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
#### <a name="to-view-the-properties-of-an-article-belonging-to-a-merge-publication"></a><span data-ttu-id="213ac-158">檢視屬於合併式發行集之發行項的屬性</span><span class="sxs-lookup"><span data-stu-id="213ac-158">To view the properties of an article belonging to a merge publication</span></span>  
  
1.  <span data-ttu-id="213ac-159">執行[sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)，並針對發行集參數指定發行集的名稱，並針對\*\* \@ 發行\*\* \*\* \@ 項參數指定\*\*發行項的名稱。</span><span class="sxs-lookup"><span data-stu-id="213ac-159">Execute [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql), specifying the name of the publication for the **\@publication** parameter and the name of the article for the **\@article** parameter.</span></span> <span data-ttu-id="213ac-160">如果您不指定這些參數，將會傳回發行集中或發行者上所有發行項的資訊。</span><span class="sxs-lookup"><span data-stu-id="213ac-160">If you do not specify these parameters, information will be returned for all articles in a publication or at the publisher.</span></span>  
  
2.  <span data-ttu-id="213ac-161">針對資料表發行項執行 [sp_helpmergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-helpmergearticlecolumn-transact-sql) ，以列出基底資料表中可用的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="213ac-161">Execute [sp_helpmergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-helpmergearticlecolumn-transact-sql) for table articles to list all columns available in the base table.</span></span>  
  
#### <a name="to-modify-the-properties-of-an-article-belonging-to-a-merge-publication"></a><span data-ttu-id="213ac-162">修改屬於合併式發行集之發行項的屬性</span><span class="sxs-lookup"><span data-stu-id="213ac-162">To modify the properties of an article belonging to a merge publication</span></span>  
  
1.  <span data-ttu-id="213ac-163">執行[sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)，在\*\* \@ property**參數中指定要變更的發行項屬性，並在** \@ value\*\*參數中指定這個屬性的新值。</span><span class="sxs-lookup"><span data-stu-id="213ac-163">Execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying the article property being changed in the **\@property** parameter and the new value of this property in the **\@value** parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="213ac-164">如果變更需要產生新的快照集，您也必須為\*\* \@ force_invalidate_snapshot**指定**1**的值，而且如果變更需要重新初始化訂閱者，您也必須為** \@ force_reinit_subscription**指定**1\*\*的值。</span><span class="sxs-lookup"><span data-stu-id="213ac-164">If the change requires the generation of a new snapshot, you must also specify a value of **1** for **\@force_invalidate_snapshot**, and if the change requires that Subscribers be reinitialized, you must also specify a value of **1** for **\@force_reinit_subscription**.</span></span> <span data-ttu-id="213ac-165">如需當變更時需要新的快照集或重新初始化之屬性的詳細資訊，請參閱[變更發行集與發行項屬性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="213ac-165">For more information on the properties that, when changed, require a new snapshot or reinitialization, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="213ac-166">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="213ac-166">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="213ac-167">這個異動複寫範例會傳回已發行之發行項的屬性。</span><span class="sxs-lookup"><span data-stu-id="213ac-167">This transactional replication example returns the properties of the published article.</span></span>  
  
 [!code-sql[HowTo#sp_helptranarticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranart.sql#sp_helptranarticle)]  
  
 <span data-ttu-id="213ac-168">這個異動複寫範例會變更已發行之發行項的結構描述選項。</span><span class="sxs-lookup"><span data-stu-id="213ac-168">This transactional replication example changes the schema options for the published article.</span></span>  
  
 [!code-sql[HowTo#sp_changetranarticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranart.sql#sp_changetranarticle)]  
  
 <span data-ttu-id="213ac-169">這個合併式複寫範例會傳回已發行之發行項的屬性。</span><span class="sxs-lookup"><span data-stu-id="213ac-169">This merge replication example returns the properties of the published article.</span></span>  
  
 [!code-sql[HowTo#sp_helpmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergeart.sql#sp_helpmergearticle)]  
  
 <span data-ttu-id="213ac-170">這個合併式複寫範例會變更已發行之發行項的衝突偵測設定。</span><span class="sxs-lookup"><span data-stu-id="213ac-170">This merge replication example changes the conflict detection settings for a published article.</span></span>  
  
 [!code-sql[HowTo#sp_changemergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergeart.sql#sp_changemergearticle)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="213ac-171">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="213ac-171">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="213ac-172">您可以使用 Replication Management Objects (RMO) 以程式設計的方式修改發行項及存取其屬性。</span><span class="sxs-lookup"><span data-stu-id="213ac-172">You can modify articles and access their properties programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="213ac-173">用來檢視或修改發行項屬性的 RMO 類別，將取決於發行項所屬的發行集類型而定。</span><span class="sxs-lookup"><span data-stu-id="213ac-173">The RMO classes you use to view or modify article properties depend on the type of publication to which the article belongs.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-an-article-that-belongs-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="213ac-174">檢視或修改屬於快照式或交易式發行集之發行項的屬性</span><span class="sxs-lookup"><span data-stu-id="213ac-174">To view or modify properties of an article that belongs to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="213ac-175">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="213ac-175">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="213ac-176">建立 <xref:Microsoft.SqlServer.Replication.TransArticle> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="213ac-176">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransArticle> class.</span></span>  
  
3.  <span data-ttu-id="213ac-177">設定 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>和 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="213ac-177">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="213ac-178">針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定步驟 1 中的連接。</span><span class="sxs-lookup"><span data-stu-id="213ac-178">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="213ac-179">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="213ac-179">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="213ac-180">如果此方法傳回 `false`，則表示步驟 3 中的發行項屬性定義不正確，或者該發行項不存在。</span><span class="sxs-lookup"><span data-stu-id="213ac-180">If this method returns `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span>  
  
6.  <span data-ttu-id="213ac-181">(選擇性) 若要變更屬性，請針對其中一個可設定的 <xref:Microsoft.SqlServer.Replication.TransArticle> 屬性設定新的值。</span><span class="sxs-lookup"><span data-stu-id="213ac-181">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.TransArticle> properties that can be set.</span></span>  
  
7.  <span data-ttu-id="213ac-182">(選擇性) 如果您已針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 指定 `true` 的值，請呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法來認可伺服器上的變更。</span><span class="sxs-lookup"><span data-stu-id="213ac-182">(Optional) If you specified a value of `true` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit changes on the server.</span></span> <span data-ttu-id="213ac-183">如果您已針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 指定 `false` 的值 (預設值)，則會立即將變更傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="213ac-183">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (the default), changes are sent to the server immediately.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-an-article-that-belongs-to-a-merge-publication"></a><span data-ttu-id="213ac-184">檢視或修改屬於合併式發行集之發行項的屬性</span><span class="sxs-lookup"><span data-stu-id="213ac-184">To view or modify properties of an article that belongs to a merge publication</span></span>  
  
1.  <span data-ttu-id="213ac-185">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="213ac-185">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="213ac-186">建立 <xref:Microsoft.SqlServer.Replication.MergeArticle> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="213ac-186">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class.</span></span>  
  
3.  <span data-ttu-id="213ac-187">設定 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>和 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="213ac-187">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="213ac-188">針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定步驟 1 中的連接。</span><span class="sxs-lookup"><span data-stu-id="213ac-188">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="213ac-189">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="213ac-189">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="213ac-190">如果此方法傳回 `false`，則表示步驟 3 中的發行項屬性定義不正確，或者該發行項不存在。</span><span class="sxs-lookup"><span data-stu-id="213ac-190">If this method returns `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span>  
  
6.  <span data-ttu-id="213ac-191">(選擇性) 若要變更屬性，請針對其中一個可設定的 <xref:Microsoft.SqlServer.Replication.MergeArticle> 屬性設定新的值。</span><span class="sxs-lookup"><span data-stu-id="213ac-191">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.MergeArticle> properties that can be set.</span></span>  
  
7.  <span data-ttu-id="213ac-192">(選擇性) 如果您已針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 指定 `true` 的值，請呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法來認可伺服器上的變更。</span><span class="sxs-lookup"><span data-stu-id="213ac-192">(Optional) If you specified a value of `true` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit changes on the server.</span></span> <span data-ttu-id="213ac-193">如果您已針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 指定 `false` 的值 (預設值)，則會立即將變更傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="213ac-193">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (the default), changes are sent to the server immediately.</span></span>  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="213ac-194">範例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="213ac-194">Example (RMO)</span></span>  
 <span data-ttu-id="213ac-195">此範例會變更合併發行項，以指定此發行項所使用的商務邏輯處理常式。</span><span class="sxs-lookup"><span data-stu-id="213ac-195">This example changes a merge article to specify the business logic handler used by the article.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## <a name="see-also"></a><span data-ttu-id="213ac-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="213ac-196">See Also</span></span>  
 <span data-ttu-id="213ac-197">[為合併發行項實作商務邏輯處理常式](../implement-a-business-logic-handler-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="213ac-197">[Implement a Business Logic Handler for a Merge Article](../implement-a-business-logic-handler-for-a-merge-article.md) </span></span>  
 <span data-ttu-id="213ac-198">[發行資料和資料庫物件](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="213ac-198">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="213ac-199">[變更發行集與發行項屬性](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="213ac-199">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="213ac-200">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="213ac-200">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="213ac-201">Advanced Merge Replication Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="213ac-201">Advanced Merge Replication Conflict Detection and Resolution</span></span>](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
