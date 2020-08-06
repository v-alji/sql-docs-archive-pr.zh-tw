---
title: 非 SQL Server 訂閱者 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], non-SQL Server Subscribers
- heterogeneous data sources, non-SQL Server Subscribers
- heterogeneous data sources
- heterogeneous database replication, non-SQL Server Subscribers
- non-SQL Server Subscribers, about non-SQL Server Subscribers
- heterogeneous Subscribers
- heterogeneous Subscribers, about heterogeneous Subscribers
- Subscribers [SQL Server replication], non-SQL Server Subscribers
- non-SQL Server Subscribers
ms.assetid: 831e7586-2949-4b9b-a2f3-7b0b699b23ff
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a42ba5aedff4f23c6fb6be4155b1c6d4bf20471
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702753"
---
# <a name="non-sql-server-subscribers"></a><span data-ttu-id="01f12-102">非 SQL Server 訂閱者</span><span class="sxs-lookup"><span data-stu-id="01f12-102">Non-SQL Server Subscribers</span></span>
  <span data-ttu-id="01f12-103">下列非「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」可以使用發送訂閱來訂閱快照式和交易式發行集。</span><span class="sxs-lookup"><span data-stu-id="01f12-103">The following non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers can subscribe to snapshot and transactional publications using push subscriptions.</span></span> <span data-ttu-id="01f12-104">使用已列 OLE DB 提供者的最新版本，列出的每個資料庫之兩個最新版本可支援訂閱。</span><span class="sxs-lookup"><span data-stu-id="01f12-104">Subscriptions are supported for the two most recent versions of each database listed using the most recent version of the OLE DB provider listed.</span></span>  
  
 <span data-ttu-id="01f12-105">非 SQL Server 訂閱者的異質性複寫已被取代。</span><span class="sxs-lookup"><span data-stu-id="01f12-105">Heterogeneous replication to non-SQL Server subscribers is deprecated.</span></span> <span data-ttu-id="01f12-106">Oracle 發行已被取代。</span><span class="sxs-lookup"><span data-stu-id="01f12-106">Oracle Publishing is deprecated.</span></span> <span data-ttu-id="01f12-107">若要移動資料，請使用異動資料擷取和 [!INCLUDE[ssIS](../../../includes/ssis-md.md)]建立方案。</span><span class="sxs-lookup"><span data-stu-id="01f12-107">To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../../includes/ssis-md.md)].</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
|<span data-ttu-id="01f12-108">資料庫</span><span class="sxs-lookup"><span data-stu-id="01f12-108">Database</span></span>|<span data-ttu-id="01f12-109">作業系統</span><span class="sxs-lookup"><span data-stu-id="01f12-109">Operating System</span></span>|<span data-ttu-id="01f12-110">提供者</span><span class="sxs-lookup"><span data-stu-id="01f12-110">Provider</span></span>|  
|--------------|----------------------|--------------|  
|<span data-ttu-id="01f12-111">Oracle</span><span class="sxs-lookup"><span data-stu-id="01f12-111">Oracle</span></span>|<span data-ttu-id="01f12-112">Oracle 支援的所有平台</span><span class="sxs-lookup"><span data-stu-id="01f12-112">All platforms that Oracle supports</span></span>|<span data-ttu-id="01f12-113">Oracle OLE DB 提供者 (由 Oracle 提供)</span><span class="sxs-lookup"><span data-stu-id="01f12-113">Oracle OLE DB provider (supplied by Oracle)</span></span>|  
|<span data-ttu-id="01f12-114">IBM DB2</span><span class="sxs-lookup"><span data-stu-id="01f12-114">IBM DB2</span></span>|<span data-ttu-id="01f12-115">MVS、AS400、Unix、Linux 與 Windows (不包括 9.x)</span><span class="sxs-lookup"><span data-stu-id="01f12-115">MVS, AS400, Unix, Linux, Windows excluding 9.x</span></span>|<span data-ttu-id="01f12-116">Microsoft Host Integration Server (HIS) OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="01f12-116">Microsoft Host Integration Server (HIS) OLE DB provider</span></span>|  
  
 <span data-ttu-id="01f12-117">如需建立 Oracle 和 IBM DB2, 之訂閱的詳細資訊，請參閱＜ [Oracle 訂閱者](oracle-subscribers.md) ＞和＜ [IBM DB2 Subscribers](ibm-db2-subscribers.md)建立方案。</span><span class="sxs-lookup"><span data-stu-id="01f12-117">For information about creating subscriptions to Oracle and IBM DB2, see [Oracle Subscribers](oracle-subscribers.md) and [IBM DB2 Subscribers](ibm-db2-subscribers.md).</span></span>  
  
## <a name="considerations-for-non-sql-server-subscribers"></a><span data-ttu-id="01f12-118">非 SQL Server 訂閱者之考量</span><span class="sxs-lookup"><span data-stu-id="01f12-118">Considerations for Non-SQL Server Subscribers</span></span>  
 <span data-ttu-id="01f12-119">當複寫到非「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」時，請記住下列考量：</span><span class="sxs-lookup"><span data-stu-id="01f12-119">Keep the following considerations in mind when replicating to non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers:</span></span>  
  
### <a name="general-considerations"></a><span data-ttu-id="01f12-120">一般考量</span><span class="sxs-lookup"><span data-stu-id="01f12-120">General Considerations</span></span>  
  
-   <span data-ttu-id="01f12-121">複寫支援將資料表和索引檢視做為資料表發行至非「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」(索引檢視無法複寫為索引檢視)。</span><span class="sxs-lookup"><span data-stu-id="01f12-121">Replication supports publishing tables and indexed views as tables to non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers (indexed views cannot be replicated as indexed views).</span></span>  
  
-   <span data-ttu-id="01f12-122">在 [新增發行集] 中建立發行集，然後使用 [發行集屬性] 對話方塊為非 SQL Server 的訂閱者啟用時，不會為非「訂閱者」指定訂閱資料庫中所有物件的擁有者 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，而對於「 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」，則會設定為發行集資料庫中對應物件的擁有者。</span><span class="sxs-lookup"><span data-stu-id="01f12-122">When creating a publication in the New Publication Wizard and then enabling it for non-SQL Server Subscribers using the Publication Properties dialog box, the owner of all objects in the subscription database is not specified for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers, whereas for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers, it is set to the owner of the corresponding object in the publication database.</span></span>  
  
-   <span data-ttu-id="01f12-123">如果發行集要擁有「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」和非「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」，則在建立「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」的任何訂閱前，必須為非「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」啟用發行集。</span><span class="sxs-lookup"><span data-stu-id="01f12-123">If a publication will have [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers and non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers, the publication must be enabled for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers before any subscriptions to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers are created.</span></span>  
  
-   <span data-ttu-id="01f12-124">依預設，由「快照集代理程式」為非「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」產生的指令碼會在 CREATE TABLE 語法中使用未加引號的識別碼。</span><span class="sxs-lookup"><span data-stu-id="01f12-124">By default, scripts generated by the Snapshot Agent for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers use non-quoted identifiers in the CREATE TABLE syntax.</span></span> <span data-ttu-id="01f12-125">因此，名稱為 test 的已發行資料表會複寫為 TEST。</span><span class="sxs-lookup"><span data-stu-id="01f12-125">Therefore, a published table named 'test' is replicated as 'TEST'.</span></span> <span data-ttu-id="01f12-126">若要使用與發行集資料庫中資料表相同的大小寫，請使用「散發代理程式」的 **-QuotedIdentifier** 參數。</span><span class="sxs-lookup"><span data-stu-id="01f12-126">To use the same case as the table in the publication database, use the **-QuotedIdentifier** parameter for the Distribution Agent.</span></span> <span data-ttu-id="01f12-127">如果發行的物件名稱 (如資料表、資料行或條件約束) 包含空格或非「 **訂閱者」端之資料庫版本中的保留字，則還必須使用** -QuotedIdentifier[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 參數。</span><span class="sxs-lookup"><span data-stu-id="01f12-127">The **-QuotedIdentifier** parameter must also be used if published object names (such as tables, columns, and constraints) include spaces or words that are reserved words in the version of the database at the non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscriber.</span></span> <span data-ttu-id="01f12-128">如需有關此參數的詳細資訊，請參閱＜ [複寫散發代理程式](../agents/replication-distribution-agent.md)＞。</span><span class="sxs-lookup"><span data-stu-id="01f12-128">For more information about this parameter, see [Replication Distribution Agent](../agents/replication-distribution-agent.md).</span></span>  
  
-   <span data-ttu-id="01f12-129">「散發代理程式」執行時所用的帳戶必須具有 OLE DB 提供者安裝目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="01f12-129">The account under which the Distribution Agent runs must have read access to the install directory of the OLE DB provider.</span></span>  
  
-   <span data-ttu-id="01f12-130">依預設，對於非「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」，「散發代理程式」為訂閱資料庫 (「散發代理程式」的 **-SubscriberDB** 參數) 使用 [(預設目的地)] 的值：</span><span class="sxs-lookup"><span data-stu-id="01f12-130">By default for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers, the Distribution Agent uses a value of [(default destination)] for the subscription database (the **-SubscriberDB** parameter for the Distribution Agent):</span></span>  
  
    -   <span data-ttu-id="01f12-131">在 Oracle 中，伺服器最多只有一個資料庫，所以不需要指定資料庫。</span><span class="sxs-lookup"><span data-stu-id="01f12-131">For Oracle, a server has at most one database, so it is not necessary to specify the database.</span></span>  
  
    -   <span data-ttu-id="01f12-132">對於 IBM DB2，在 DB2 連接字串中指定資料庫。</span><span class="sxs-lookup"><span data-stu-id="01f12-132">For IBM DB2, the database is specified in the DB2 connection string.</span></span> <span data-ttu-id="01f12-133">如需相關資訊，請參閱 [為非 SQL Server 訂閱者建立訂閱](../create-a-subscription-for-a-non-sql-server-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="01f12-133">For more information, see [Create a Subscription for a Non-SQL Server Subscriber](../create-a-subscription-for-a-non-sql-server-subscriber.md).</span></span>  
  
-   <span data-ttu-id="01f12-134">如果「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者」在 64 位元平台上執行，則必須使用適當 OLE DB 提供者的 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="01f12-134">If the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor is running on a 64 bit platform, you must use the 64 bit version of the appropriate OLE DB provider.</span></span>  
  
-   <span data-ttu-id="01f12-135">複寫以 Unicode 格式移動資料，不論「發行者」與「訂閱者」上使用的定序/字碼頁為何。</span><span class="sxs-lookup"><span data-stu-id="01f12-135">Replication moves data in Unicode format regardless of the collation/code pages used on the Publisher and Subscriber.</span></span> <span data-ttu-id="01f12-136">在「發行者」和「訂閱者」之間複寫時，建議您選擇相容的定序/字碼頁。</span><span class="sxs-lookup"><span data-stu-id="01f12-136">It is recommended that you choose a compatible collation/code page when replicating between Publishers and Subscribers.</span></span>  
  
-   <span data-ttu-id="01f12-137">如果在發行集中新增或刪除發行項，則必須重新初始化非「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」的訂閱。</span><span class="sxs-lookup"><span data-stu-id="01f12-137">If an article is added to or deleted from a publication, subscriptions to non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers must be reinitialized.</span></span>  
  
-   <span data-ttu-id="01f12-138">所有非「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」支援之條件約束僅為：NULL 和 NOT NULL。</span><span class="sxs-lookup"><span data-stu-id="01f12-138">The only constraints supported for all non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers are: NULL, and NOT NULL.</span></span> <span data-ttu-id="01f12-139">主索引鍵條件約束複寫為唯一的索引。</span><span class="sxs-lookup"><span data-stu-id="01f12-139">Primary key constraints are replicated as unique indexes.</span></span>  
  
-   <span data-ttu-id="01f12-140">不同資料庫以不同方式處理值 NULL，這會影響空白值、空字串和 NULL 的表示方式。</span><span class="sxs-lookup"><span data-stu-id="01f12-140">The value NULL is treated differently by different databases, which affects how a blank value, an empty string, and a NULL are represented.</span></span> <span data-ttu-id="01f12-141">進而會影響插入到定義了唯一條件約束的資料行之值的行為。</span><span class="sxs-lookup"><span data-stu-id="01f12-141">This in turn affects the behavior of values inserted into columns with unique constraints defined.</span></span> <span data-ttu-id="01f12-142">例如，Oracle 在視為唯一的資料行中允許有多個 NULL 值，而 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 在唯一的資料行中只允許有一個 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="01f12-142">For example, Oracle allows multiple NULL values in a column that is considered unique, whereas [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] allows only a single NULL value in a unique column.</span></span>  
  
     <span data-ttu-id="01f12-143">另一個因素是，當資料行定義為 NOT NULL 時，如何處理 NULL 值、空字串和空白值。</span><span class="sxs-lookup"><span data-stu-id="01f12-143">An additional factor is how NULL values, empty strings, and blank values are treated when the column is defined as NOT NULL.</span></span> <span data-ttu-id="01f12-144">如需為「Oracle 訂閱者」解決此問題的詳細資訊，請參閱＜ [Oracle 訂閱者](oracle-subscribers.md)＞。</span><span class="sxs-lookup"><span data-stu-id="01f12-144">For information about addressing this issue for Oracle Subscribers, see [Oracle Subscribers](oracle-subscribers.md).</span></span>  
  
-   <span data-ttu-id="01f12-145">移除訂閱時，與複寫相關的中繼資料 (交易序號資料表) 不會從非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者刪除。</span><span class="sxs-lookup"><span data-stu-id="01f12-145">Replication-related metadata (transaction sequence table) is not deleted from non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] subscribers when the subscription is removed.</span></span>  
  
### <a name="conforming-to-the-requirements-of-the-subscriber-database"></a><span data-ttu-id="01f12-146">符合訂閱者資料庫之要求</span><span class="sxs-lookup"><span data-stu-id="01f12-146">Conforming to the Requirements of the Subscriber Database</span></span>  
  
-   <span data-ttu-id="01f12-147">發行的結構描述和資料必須符合「訂閱者」端資料庫的要求。</span><span class="sxs-lookup"><span data-stu-id="01f12-147">Published schema and data must conform to the requirements of the database at the Subscriber.</span></span> <span data-ttu-id="01f12-148">例如，如果非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫的最大資料列大小小於 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，則必須確定已發行的結構描述和資料不會超過此大小。</span><span class="sxs-lookup"><span data-stu-id="01f12-148">For example, if a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database has a smaller maximum row size than [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], you must ensure that the published schema and data do not exceed this size.</span></span>  
  
-   <span data-ttu-id="01f12-149">複寫到非「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」的資料表將採用「訂閱者」端資料庫的資料表命名慣例。</span><span class="sxs-lookup"><span data-stu-id="01f12-149">Tables replicated to non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers will adopt the table naming conventions of the database at the Subscriber.</span></span>  
  
-   <span data-ttu-id="01f12-150">非 SQL Server 訂閱者不支援 DDL。</span><span class="sxs-lookup"><span data-stu-id="01f12-150">DDL is not supported for non-SQL Server Subscribers.</span></span> <span data-ttu-id="01f12-151">如需結構描述變更的詳細資訊，請參閱[對發行集資料庫進行結構描述變更](../publish/make-schema-changes-on-publication-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="01f12-151">For more information about schema changes, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
### <a name="replication-feature-support"></a><span data-ttu-id="01f12-152">複寫功能支援</span><span class="sxs-lookup"><span data-stu-id="01f12-152">Replication Feature Support</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="01f12-153">提供兩種訂閱類型：發送訂閱和提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="01f12-153">offers two types of subscriptions: push and pull.</span></span> <span data-ttu-id="01f12-154">非「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」必須使用發送訂閱，該訂閱中「散發代理程式」在「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者」端執行。</span><span class="sxs-lookup"><span data-stu-id="01f12-154">Non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers must use push subscriptions, in which the Distribution Agent runs at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="01f12-155">提供兩種快照集格式：原生 bcp 模式以及字元模式。</span><span class="sxs-lookup"><span data-stu-id="01f12-155">offers two snapshot formats: native bcp-mode and character-mode.</span></span> <span data-ttu-id="01f12-156">非「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」需要字元模式快照集。</span><span class="sxs-lookup"><span data-stu-id="01f12-156">Non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers require character mode snapshots.</span></span>  
  
-   <span data-ttu-id="01f12-157">非「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」不能使用立即更新或佇列更新訂閱，或成為點對點拓撲中的節點。</span><span class="sxs-lookup"><span data-stu-id="01f12-157">Non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers cannot use immediate updating or queued updating subscriptions, or be nodes in a peer-to-peer topology.</span></span>  
  
-   <span data-ttu-id="01f12-158">非「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」不能從備份中自動初始化。</span><span class="sxs-lookup"><span data-stu-id="01f12-158">Non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers cannot be automatically initialized from a backup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f12-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01f12-159">See Also</span></span>  
 <span data-ttu-id="01f12-160">[異質資料庫複寫](heterogeneous-database-replication.md) </span><span class="sxs-lookup"><span data-stu-id="01f12-160">[Heterogeneous Database Replication](heterogeneous-database-replication.md) </span></span>  
 [<span data-ttu-id="01f12-161">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="01f12-161">Subscribe to Publications</span></span>](../subscribe-to-publications.md)  
  
  
