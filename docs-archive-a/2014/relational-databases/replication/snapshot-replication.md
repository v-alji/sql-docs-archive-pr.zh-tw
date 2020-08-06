---
title: 快照式複寫 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], about snapshot replication
- snapshot replication [SQL Server]
ms.assetid: 5d745f22-9c6b-4e11-8c62-bc50e9a8bf38
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6192c196e31c4c5772099074c79b3c6c4ca7aeed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710585"
---
# <a name="snapshot-replication"></a><span data-ttu-id="1a789-102">快照式複寫</span><span class="sxs-lookup"><span data-stu-id="1a789-102">Snapshot Replication</span></span>
  <span data-ttu-id="1a789-103">快照式複寫可以精確地將資料以其特定時點的樣子散發出去，且不監視此資料的更新。</span><span class="sxs-lookup"><span data-stu-id="1a789-103">Snapshot replication distributes data exactly as it appears at a specific moment in time and does not monitor for updates to the data.</span></span> <span data-ttu-id="1a789-104">在進行同步處理的時候，會產生整個快照集並傳送至「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="1a789-104">When synchronization occurs, the entire snapshot is generated and sent to Subscribers.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1a789-105">快照集複寫可以自行使用，但一般同時使用快照集處理 (它可建立所有發行集指定的物件和資料的副本) 以提供用於交易式發行集和合併式發行集的初始資料與資料庫物件集合。</span><span class="sxs-lookup"><span data-stu-id="1a789-105">Snapshot replication can be used by itself, but the snapshot process (which creates a copy of all of the objects and data specified by a publication) is also commonly used to provide the initial set of data and database objects for transactional and merge publications.</span></span>  
  
 <span data-ttu-id="1a789-106">若下列一或多項敘述為真，則最適合單獨使用快照式複寫：</span><span class="sxs-lookup"><span data-stu-id="1a789-106">Using snapshot replication by itself is most appropriate when one or more of the following is true:</span></span>  
  
-   <span data-ttu-id="1a789-107">較少變更資料。</span><span class="sxs-lookup"><span data-stu-id="1a789-107">Data changes infrequently.</span></span>  
  
-   <span data-ttu-id="1a789-108">可接受已過時的發行者相關資料副本放置一段時間。</span><span class="sxs-lookup"><span data-stu-id="1a789-108">It is acceptable to have copies of data that are out of date with respect to the Publisher for a period of time.</span></span>  
  
-   <span data-ttu-id="1a789-109">複寫小量資料時。</span><span class="sxs-lookup"><span data-stu-id="1a789-109">Replicating small volumes of data.</span></span>  
  
-   <span data-ttu-id="1a789-110">在短時間內發生大量變更。</span><span class="sxs-lookup"><span data-stu-id="1a789-110">A large volume of changes occurs over a short period of time.</span></span>  
  
 <span data-ttu-id="1a789-111">資料變更數量可觀但次數不頻繁時，最適合快照式複寫。</span><span class="sxs-lookup"><span data-stu-id="1a789-111">Snapshot replication is most appropriate when data changes are substantial but infrequent.</span></span> <span data-ttu-id="1a789-112">例如，某個銷售單位維護一個產品價格表，其中所有價格在一年當中會同時更新一至二次，建議您在變更後複寫整個資料的快照集。</span><span class="sxs-lookup"><span data-stu-id="1a789-112">For example, if a sales organization maintains a product price list and the prices are all updated at the same time once or twice each year, replicating the entire snapshot of data after it has changed is recommended.</span></span> <span data-ttu-id="1a789-113">指定類型的資料，也可能適合更頻繁的快照集。</span><span class="sxs-lookup"><span data-stu-id="1a789-113">Given certain types of data, more frequent snapshots may also be appropriate.</span></span> <span data-ttu-id="1a789-114">例如，如果在白天更新「發行者」端的相對較小的資料表，但有一些延遲可以接受，則變更可以作為快照集每夜傳遞。</span><span class="sxs-lookup"><span data-stu-id="1a789-114">For example, if a relatively small table is updated at the Publisher during the day, but some latency is acceptable, changes can be delivered nightly as a snapshot.</span></span>  
  
 <span data-ttu-id="1a789-115">快照式複寫相對於異動複寫，其在「發行者」上的連續性負擔更低，因為它不追蹤累加的變更。</span><span class="sxs-lookup"><span data-stu-id="1a789-115">Snapshot replication has a lower continuous overhead on the Publisher than transactional replication, because incremental changes are not tracked.</span></span> <span data-ttu-id="1a789-116">但是，如果複寫的資料集變得很大，它將需要大量資源來產生和套用快照集。</span><span class="sxs-lookup"><span data-stu-id="1a789-116">However, if the dataset set being replicated is very large, it will require substantial resources to generate and apply the snapshot.</span></span> <span data-ttu-id="1a789-117">在評估是否使用快照式複寫時，請考慮整個資料集的大小和對資料進行變更的頻率。</span><span class="sxs-lookup"><span data-stu-id="1a789-117">Consider the size of the entire data set and the frequency of changes to the data when evaluating whether to utilize snapshot replication.</span></span>  
  
 <span data-ttu-id="1a789-118">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="1a789-118">**In this topic**</span></span>  
  
 [<span data-ttu-id="1a789-119">快照式複寫如何運作</span><span class="sxs-lookup"><span data-stu-id="1a789-119">How Snapshot Replication Works</span></span>](#HowWorks)  
  
 [<span data-ttu-id="1a789-120">快照集代理程式</span><span class="sxs-lookup"><span data-stu-id="1a789-120">Snapshot Agent</span></span>](#SnapshotAgent)  
  
 [<span data-ttu-id="1a789-121">散發與合併代理程式</span><span class="sxs-lookup"><span data-stu-id="1a789-121">Distribution and Merge Agents</span></span>](#DistAgent)  
  
##  <a name="how-snapshot-replication-works"></a><a name="HowWorks"></a> <span data-ttu-id="1a789-122">快照式複寫如何運作</span><span class="sxs-lookup"><span data-stu-id="1a789-122">How Snapshot Replication Works</span></span>  
 <span data-ttu-id="1a789-123">依預設，三種類型的複寫均使用快照集來初始化「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="1a789-123">By default, all three types of replication use a snapshot to initialize Subscribers.</span></span> <span data-ttu-id="1a789-124">「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 快照集代理程式」總是會產生快照集檔案，但是根據所使用的複寫類型，傳遞檔案的代理程式有所不同。</span><span class="sxs-lookup"><span data-stu-id="1a789-124">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Snapshot Agent always generates the snapshot files, but the agent that delivers the files differs depending on the type of replication being used.</span></span> <span data-ttu-id="1a789-125">快照式複寫和異動複寫使用「散發代理程式」傳遞檔案，而合併式複寫則使用「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 合併代理程式」。</span><span class="sxs-lookup"><span data-stu-id="1a789-125">Snapshot replication and transactional replication use the Distribution Agent to deliver the files, whereas merge replication uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Merge Agent.</span></span> <span data-ttu-id="1a789-126">快照集代理程式於發行者端執行。</span><span class="sxs-lookup"><span data-stu-id="1a789-126">The Snapshot Agent runs at the Distributor.</span></span> <span data-ttu-id="1a789-127">「散發代理程式」和「合併代理程式」則在發送訂閱的「散發者」端或提取訂閱的「訂閱者」端執行。</span><span class="sxs-lookup"><span data-stu-id="1a789-127">The Distribution Agent and Merge Agent run at the Distributor for push subscriptions, or at Subscribers for pull subscriptions.</span></span>  
  
 <span data-ttu-id="1a789-128">快照集的產生和套用可以在訂閱建立後立即進行，也可以在發行集建立時所排定的時間進行。</span><span class="sxs-lookup"><span data-stu-id="1a789-128">Snapshots can be generated and applied either immediately after the subscription is created or according to a schedule set at the time the publication is created.</span></span> <span data-ttu-id="1a789-129">「快照集代理程式」會準備包含已發行資料表與資料庫物件之結構描述及資料的快照集檔案，將檔案儲存在「發行者」的快照集資料夾內，然後追蹤「散發者」散發資料庫中的資訊。</span><span class="sxs-lookup"><span data-stu-id="1a789-129">The Snapshot Agent prepares snapshot files containing the schema and data of published tables and database objects, stores the files in the snapshot folder for the Publisher, and records tracking information in the distribution database on the Distributor.</span></span> <span data-ttu-id="1a789-130">在設定「散發者」時指定預設快照集資料夾，但也可以為發行集指定預設位置以外的替代位置，或兩個位置均指定。</span><span class="sxs-lookup"><span data-stu-id="1a789-130">You specify a default snapshot folder when you configure a Distributor, but you can specify an alternate location for a publication instead of or in addition to the default.</span></span>  
  
 <span data-ttu-id="1a789-131">除了本主題中描述的標準快照集處理之外，兩段式快照集處理還可以用於含參數化篩選的合併式發行集。</span><span class="sxs-lookup"><span data-stu-id="1a789-131">In addition to the standard snapshot process described in this topic, a two-part snapshot process is used for merge publications with parameterized filters.</span></span>  
  
 <span data-ttu-id="1a789-132">下圖顯示快照式複寫的主體元件。</span><span class="sxs-lookup"><span data-stu-id="1a789-132">The following illustration shows the principal components of snapshot replication.</span></span>  
  
 <span data-ttu-id="1a789-133">![快照式複寫元件和資料流程](media/snapshot.gif "快照式複寫元件和資料流程")</span><span class="sxs-lookup"><span data-stu-id="1a789-133">![Snapshot replication components and data flow](media/snapshot.gif "Snapshot replication components and data flow")</span></span>  
  
##  <a name="snapshot-agent"></a><a name="SnapshotAgent"></a> <span data-ttu-id="1a789-134">快照集代理程式</span><span class="sxs-lookup"><span data-stu-id="1a789-134">Snapshot Agent</span></span>  
 <span data-ttu-id="1a789-135">針對合併式複寫，每次執行快照集代理程式都會產生快照集。</span><span class="sxs-lookup"><span data-stu-id="1a789-135">For merge replication, a snapshot is generated every time the Snapshot Agent runs.</span></span> <span data-ttu-id="1a789-136">針對異動複寫，是否產生快照集是依照發行集屬性 **immediate_sync**的設定而定。</span><span class="sxs-lookup"><span data-stu-id="1a789-136">For transactional replication, snapshot generation depends on the setting of the publication property **immediate_sync**.</span></span> <span data-ttu-id="1a789-137">若屬性設定為 TRUE (使用新增發行集精靈的預設)，每次執行快照集代理程式都會產生快照集，同時隨時可套用至訂閱者。</span><span class="sxs-lookup"><span data-stu-id="1a789-137">If the property is set to TRUE (the default when using the New Publication Wizard), a snapshot is generated every time the Snapshot Agent runs, and it can be applied to a Subscriber at any time.</span></span> <span data-ttu-id="1a789-138">若屬性設定為 FALSE (使用 **sp_addpublication**時的預設)，則只有在上次執行快照集代理程式後有加入新訂閱的情況下，才會產生快照集。訂閱者必須等待快照集代理程式完成，才能同步處理。</span><span class="sxs-lookup"><span data-stu-id="1a789-138">If the property is set to FALSE (the default when using **sp_addpublication**), the snapshot is generated only if a new subscription has been added since the last Snapshot Agent run; Subscribers must wait for the Snapshot Agent to complete before they can synchronize.</span></span>  
  
 <span data-ttu-id="1a789-139">「快照集代理程式」會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="1a789-139">The Snapshot Agent performs the following steps:</span></span>  
  
1.  <span data-ttu-id="1a789-140">建立從「散發者」到「發行者」的連接，然後在必要時鎖定已發行的資料表：</span><span class="sxs-lookup"><span data-stu-id="1a789-140">Establishes a connection from the Distributor to the Publisher, and then takes locks on published tables if necessary:</span></span>  
  
    -   <span data-ttu-id="1a789-141">針對合併式發行集，快照集代理程式未使用任何鎖定。</span><span class="sxs-lookup"><span data-stu-id="1a789-141">For merge publications, the Snapshot Agent does not take any locks.</span></span>  
  
    -   <span data-ttu-id="1a789-142">對於交易式發行集，「快照集代理程式」依預設僅在快照集產生的初始階段進行鎖定。</span><span class="sxs-lookup"><span data-stu-id="1a789-142">For transactional publications, by default the Snapshot Agent take locks only during the initial phase of snapshot generation.</span></span>  
  
    -   <span data-ttu-id="1a789-143">對於快照式發行集，在整個快照集產生處理過程中均保持鎖定。</span><span class="sxs-lookup"><span data-stu-id="1a789-143">For snapshot publications, locks are held during the entire snapshot generation process.</span></span>  
  
2.  <span data-ttu-id="1a789-144">將每個發行項的資料表結構描述副本寫入 .sch 檔案。</span><span class="sxs-lookup"><span data-stu-id="1a789-144">Writes a copy of the table schema for each article to a .sch file.</span></span> <span data-ttu-id="1a789-145">如果已發行其他資料庫物件 (例如索引、條件約束、預存程序、檢視、使用者自訂函數等)，則會產生其他指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="1a789-145">If other database objects are published, such as indexes, constraints, stored procedures, views, user-defined functions, and so on, additional script files are generated.</span></span>  
  
3.  <span data-ttu-id="1a789-146">從「發行者」端的已發行資料表複製資料，並將其寫入快照集資料夾。</span><span class="sxs-lookup"><span data-stu-id="1a789-146">Copies the data from the published table at the Publisher and writes the data to the snapshot folder.</span></span> <span data-ttu-id="1a789-147">快照集以一組大量複製程式 (BCP) 檔案的形式產生。</span><span class="sxs-lookup"><span data-stu-id="1a789-147">The snapshot is generated as a set of bulk copy program (BCP) files.</span></span>  
  
4.  <span data-ttu-id="1a789-148">對於快照式和交易式發行集，「快照集代理程式」會附加資料列至散發資料庫中的 **MSrepl_commands** 和 **MSrepl_transactions** 資料表。</span><span class="sxs-lookup"><span data-stu-id="1a789-148">For snapshot and transactional publications, the Snapshot Agent appends rows to the **MSrepl_commands** and **MSrepl_transactions** tables in the distribution database.</span></span> <span data-ttu-id="1a789-149">**MSrepl_commands** 資料表中的項目為命令，表示 .sch 和 .bcp 檔案的位置、其他快照集檔案，以及對前快照集 (pre-snapshot) 或後快照集 (post-snapshot) 指令碼的參考。</span><span class="sxs-lookup"><span data-stu-id="1a789-149">The entries in the **MSrepl_commands** table are commands indicating the location of .sch and .bcp files, any other snapshot files, and references to any pre- or post-snapshot scripts.</span></span> <span data-ttu-id="1a789-150">**MSrepl_transactions** 資料表中的項目是與同步處理「訂閱者」相關的命令。</span><span class="sxs-lookup"><span data-stu-id="1a789-150">The entries in the **MSrepl_transactions** table are commands relevant to synchronizing the Subscriber.</span></span>  
  
     <span data-ttu-id="1a789-151">對於合併式發行集，「快照集代理程式」還執行其他步驟。</span><span class="sxs-lookup"><span data-stu-id="1a789-151">For merge publications, the Snapshot Agent performs additional steps.</span></span>  
  
5.  <span data-ttu-id="1a789-152">釋放對已發行資料表的鎖定。</span><span class="sxs-lookup"><span data-stu-id="1a789-152">Releases any locks on published tables.</span></span>  
  
 <span data-ttu-id="1a789-153">在快照集產生期間，無法對已發行的資料進行結構描述變更。</span><span class="sxs-lookup"><span data-stu-id="1a789-153">During snapshot generation, you cannot make schema changes on published tables.</span></span> <span data-ttu-id="1a789-154">快照集檔案產生之後，您可以使用 Windows Explorer 在快照集資料夾中檢視這些檔案。</span><span class="sxs-lookup"><span data-stu-id="1a789-154">After the snapshot files are generated, you can view them in the snapshot folder using Windows Explorer.</span></span>  
  
##  <a name="distribution-agent-and-merge-agent"></a><a name="DistAgent"></a> <span data-ttu-id="1a789-155">散發代理程式與合併代理程式</span><span class="sxs-lookup"><span data-stu-id="1a789-155">Distribution Agent and Merge Agent</span></span>  
 <span data-ttu-id="1a789-156">對於快照式發行集，每次為發行集執行「散發代理程式」時，它都會將新快照集移至每個尚未同步處理但已標示要進行重新初始化的「訂閱者」，或包含新發行項。</span><span class="sxs-lookup"><span data-stu-id="1a789-156">For snapshot publications, each time the Distribution Agent runs for the publication, it moves a new snapshot to each Subscriber that has not yet been synchronized, has been marked for reinitialization, or includes new articles.</span></span>  
  
 <span data-ttu-id="1a789-157">對於快照式和異動複寫，「散發代理程式」執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="1a789-157">For snapshot and transactional replication, the Distribution Agent performs the following steps:</span></span>  
  
1.  <span data-ttu-id="1a789-158">建立與「散發者」的連接。</span><span class="sxs-lookup"><span data-stu-id="1a789-158">Establishes a connection to the Distributor.</span></span>  
  
2.  <span data-ttu-id="1a789-159">檢查「散發者」上散發資料庫中的 **MSrepl_commands** 與 **MSrepl_transactions** 資料表。</span><span class="sxs-lookup"><span data-stu-id="1a789-159">Examines the **MSrepl_commands** and **MSrepl_transactions** tables in the distribution database on the Distributor.</span></span> <span data-ttu-id="1a789-160">代理程式會從第一個資料表中讀取快照集檔案的位置，並從兩個資料表中讀取「訂閱者」同步處理命令。</span><span class="sxs-lookup"><span data-stu-id="1a789-160">The agent reads the location of the snapshot files from the first table and Subscriber synchronization commands from both tables.</span></span>  
  
3.  <span data-ttu-id="1a789-161">將結構描述與命令套用至訂閱資料庫上。</span><span class="sxs-lookup"><span data-stu-id="1a789-161">Applies the schema and commands to the subscription database.</span></span>  
  
 <span data-ttu-id="1a789-162">對於未篩選的合併式複寫資料集，「合併代理程式」執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="1a789-162">For an unfiltered merge replication publication, the Merge Agent performs the following steps:</span></span>  
  
1.  <span data-ttu-id="1a789-163">建立與「發行者」的連接。</span><span class="sxs-lookup"><span data-stu-id="1a789-163">Establishes a connection to the Publisher.</span></span>  
  
2.  <span data-ttu-id="1a789-164">檢查「散發者」上的 **sysmergeschemachange** 資料表，並判斷是否存在應在「訂閱者」端套用的新快照集。</span><span class="sxs-lookup"><span data-stu-id="1a789-164">Examines the **sysmergeschemachange** table on the Publisher and determines whether there is a new snapshot that should be applied at the Subscriber.</span></span>  
  
3.  <span data-ttu-id="1a789-165">如果存在新快照集，「合併代理程式」會從 **sysmergeschemachange**中指定的位置將快照集檔案套用至訂閱資料庫。</span><span class="sxs-lookup"><span data-stu-id="1a789-165">If a new snapshot is available, the Merge Agent applies to the subscription database the snapshot files from the location specified in **sysmergeschemachange**.</span></span>  
  
  
