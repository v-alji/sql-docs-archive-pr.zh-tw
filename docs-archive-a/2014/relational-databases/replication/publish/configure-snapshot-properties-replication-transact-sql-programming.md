---
title: 設定快照集屬性 (複寫 Transact-SQL 程式設計) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots [SQL Server replication], properties
ms.assetid: 978d150f-8971-458a-ab2b-3beba5937b46
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c7dd645fed073f73132c6993f12925a885a8e0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705005"
---
# <a name="configure-snapshot-properties-replication-transact-sql-programming"></a><span data-ttu-id="f3c43-102">設定快照集屬性 (複寫 Transact-SQL 程式設計)</span><span class="sxs-lookup"><span data-stu-id="f3c43-102">Configure Snapshot Properties (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="f3c43-103">可以使用複寫預存程序來以程式設計的方式定義及修改快照集屬性，使用的預存程序將取決於發行集的類型而定。</span><span class="sxs-lookup"><span data-stu-id="f3c43-103">Snapshot properties can be defined and modified programmatically using replication stored procedures, where the stored procedures used depend on the type of publication.</span></span>  
  
### <a name="to-configure-snapshot-properties-when-creating-a-snapshot-or-transactional-publication"></a><span data-ttu-id="f3c43-104">在建立快照式或交易式發行集時，設定快照集屬性</span><span class="sxs-lookup"><span data-stu-id="f3c43-104">To configure snapshot properties when creating a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="f3c43-105">在發行者上，執行 [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f3c43-105">At the Publisher, execute [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql).</span></span> <span data-ttu-id="f3c43-106">針對指定發行集名稱 **@publication** 、針對指定**快照**集或**連續**的值， **@repl_freq** 並針對下列其中一個或多個快照集相關的參數：</span><span class="sxs-lookup"><span data-stu-id="f3c43-106">Specify a publication name for **@publication**, a value of either **snapshot** or **continuous** for **@repl_freq**, and one or more of the following snapshot-related parameters:</span></span>  
  
    -   <span data-ttu-id="f3c43-107">**@alt_snapshot_folder**-如果從該位置（而不是快照集預設資料夾）存取這個發行集的快照集，則指定路徑。</span><span class="sxs-lookup"><span data-stu-id="f3c43-107">**@alt_snapshot_folder** - specify a path if the snapshot for this publication is accessed from that location instead of or in addition to the snapshot default folder.</span></span>  
  
    -   <span data-ttu-id="f3c43-108">**@compress_snapshot**-如果替代快照集資料夾中的快照集檔案壓縮成 CAB 檔案格式，則指定**true**的值 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f3c43-108">**@compress_snapshot** - specify a value of **true** if the snapshot files in the alternate snapshot folder are compressed in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] CAB file format.</span></span>  
  
    -   <span data-ttu-id="f3c43-109">**@pre_snapshot_script**-指定在套用初始快照集之前的初始化期間，將于訂閱者上執行之 **.sql**檔案的檔案名和完整路徑。</span><span class="sxs-lookup"><span data-stu-id="f3c43-109">**@pre_snapshot_script** - specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="f3c43-110">**@post_snapshot_script**-指定在套用初始快照集之後的初始化期間，將于訂閱者上執行之 **.sql**檔案的檔案名和完整路徑。</span><span class="sxs-lookup"><span data-stu-id="f3c43-110">**@post_snapshot_script** - specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="f3c43-111">**@snapshot_in_defaultfolder**-如果快照集只能在非預設位置中使用，請指定**false**的值。</span><span class="sxs-lookup"><span data-stu-id="f3c43-111">**@snapshot_in_defaultfolder** - specify a value of **false** if the snapshot is available only in a non-default location.</span></span>  
  
     <span data-ttu-id="f3c43-112">如需有關建立發行集的詳細資訊，請參閱＜ [Create a Publication](create-a-publication.md)＞。</span><span class="sxs-lookup"><span data-stu-id="f3c43-112">For more information about creating publications, see [Create a Publication](create-a-publication.md).</span></span>  
  
### <a name="to-configure-snapshot-properties-when-creating-a-merge-publication"></a><span data-ttu-id="f3c43-113">在建立合併式發行集時，設定快照集屬性</span><span class="sxs-lookup"><span data-stu-id="f3c43-113">To configure snapshot properties when creating a merge publication</span></span>  
  
1.  <span data-ttu-id="f3c43-114">在發行者端，執行 [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f3c43-114">At the Publisher, execute [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span> <span data-ttu-id="f3c43-115">針對指定發行集名稱 **@publication** 、針對指定**快照**集或**連續**的值， **@repl_freq** 並針對下列其中一個或多個快照集相關的參數：</span><span class="sxs-lookup"><span data-stu-id="f3c43-115">Specify a publication name for **@publication**, a value of either **snapshot** or **continuous** for **@repl_freq**, and one or more of the following snapshot-related parameters:</span></span>  
  
    -   <span data-ttu-id="f3c43-116">**@alt_snapshot_folder**-如果從該位置（而不是快照集預設資料夾）存取這個發行集的快照集，則指定路徑。</span><span class="sxs-lookup"><span data-stu-id="f3c43-116">**@alt_snapshot_folder** - specify a path if the snapshot for this publication is accessed from that location instead of or in addition to the snapshot default folder.</span></span>  
  
    -   <span data-ttu-id="f3c43-117">**@compress_snapshot**-如果替代快照集資料夾中的快照集檔案壓縮成 CAB 檔案格式，則指定**true**的值。</span><span class="sxs-lookup"><span data-stu-id="f3c43-117">**@compress_snapshot** - specify a value of **true** if the snapshot files in the alternate snapshot folder are compressed in the CAB file format.</span></span>  
  
    -   <span data-ttu-id="f3c43-118">**@pre_snapshot_script**-指定在套用初始快照集之前的初始化期間，將于訂閱者上執行之 **.sql**檔案的檔案名和完整路徑。</span><span class="sxs-lookup"><span data-stu-id="f3c43-118">**@pre_snapshot_script** - specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="f3c43-119">**@post_snapshot_script**-指定在套用初始快照集之後的初始化期間，將于訂閱者上執行之 **.sql**檔案的檔案名和完整路徑。</span><span class="sxs-lookup"><span data-stu-id="f3c43-119">**@post_snapshot_script** - specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="f3c43-120">**@snapshot_in_defaultfolder**-如果快照集只能在非預設位置中使用，請指定**false**的值。</span><span class="sxs-lookup"><span data-stu-id="f3c43-120">**@snapshot_in_defaultfolder** - specify a value of **false** if the snapshot is available only in a non-default location.</span></span>  
  
2.  <span data-ttu-id="f3c43-121">如需有關建立發行集的詳細資訊，請參閱＜ [Create a Publication](create-a-publication.md)＞。</span><span class="sxs-lookup"><span data-stu-id="f3c43-121">For more information about creating publications, see [Create a Publication](create-a-publication.md).</span></span>  
  
### <a name="to-modify-snapshot-properties-of-an-existing-snapshot-or-transactional-publication"></a><span data-ttu-id="f3c43-122">修改現有快照式或交易式發行集的快照集屬性</span><span class="sxs-lookup"><span data-stu-id="f3c43-122">To modify snapshot properties of an existing snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="f3c43-123">在發行集資料庫的發行者上，執行 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f3c43-123">At the Publisher on the publication database, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql).</span></span> <span data-ttu-id="f3c43-124">針對指定**1**的值 **@force_invalidate_snapshot** ，並針對下列其中一個值 **@property** ：</span><span class="sxs-lookup"><span data-stu-id="f3c43-124">Specify a value of **1** for **@force_invalidate_snapshot** and one of the following values for **@property**:</span></span>  
  
    -   <span data-ttu-id="f3c43-125">**alt_snapshot_folder** -也指定的替代快照集資料夾的新路徑 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="f3c43-125">**alt_snapshot_folder** -also specify a new path to the alternate snapshot folder for **@value**.</span></span>  
  
    -   <span data-ttu-id="f3c43-126">**compress_snapshot** -也針對指定**true**或**false**的值， **@value** 以指示替代快照集資料夾中的快照集檔案是否壓縮成 CAB 檔案格式。</span><span class="sxs-lookup"><span data-stu-id="f3c43-126">**compress_snapshot** - also specify a value of either **true** or **false** for **@value** to indicate whether the snapshot files in the alternate snapshot folder are compressed in the CAB file format.</span></span>  
  
    -   <span data-ttu-id="f3c43-127">**pre_snapshot_script** -也針對 **@value** 指定在套用初始快照集之前的初始化期間，將于訂閱者上執行之 **.sql**檔案的檔案名和完整路徑。</span><span class="sxs-lookup"><span data-stu-id="f3c43-127">**pre_snapshot_script** - also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="f3c43-128">**post_snapshot_script** -也針對 **@value** 指定在套用初始快照集之後的初始化期間，將于訂閱者上執行之 **.sql**檔案的檔案名和完整路徑。</span><span class="sxs-lookup"><span data-stu-id="f3c43-128">**post_snapshot_script** - also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="f3c43-129">**snapshot_in_defaultfolder** - 也指定 **true** 或 **false** 的值，以指示快照集是否可在非預設位置中使用。</span><span class="sxs-lookup"><span data-stu-id="f3c43-129">**snapshot_in_defaultfolder** - also specify a value of either **true** or **false** to indicate whether the snapshot is available only in a non-default location.</span></span>  
  
2.  <span data-ttu-id="f3c43-130">(選擇性) 在發行集資料庫的發行者上，執行 [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f3c43-130">(Optional) At the Publisher on the publication database, execute [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql).</span></span> <span data-ttu-id="f3c43-131">指定 **@publication** 和一或多個要變更的排程或安全性認證參數。</span><span class="sxs-lookup"><span data-stu-id="f3c43-131">Specify **@publication** and one or more of the scheduling or security credential parameters being changed.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f3c43-132">可能的話，會在執行階段提示使用者輸入安全性認證。</span><span class="sxs-lookup"><span data-stu-id="f3c43-132">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="f3c43-133">如果您必須將認證儲存在指令碼檔案中，則必須維護這個檔案的安全性，使他人無法在未獲授權的情況下擅自存取。</span><span class="sxs-lookup"><span data-stu-id="f3c43-133">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
3.  <span data-ttu-id="f3c43-134">從命令提示字元執行 [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) 或是啟動快照集代理程式作業來產生新的快照集。</span><span class="sxs-lookup"><span data-stu-id="f3c43-134">Run the [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) from the command prompt or start the Snapshot Agent job to generate a new snapshot.</span></span> <span data-ttu-id="f3c43-135">如需詳細資訊，請參閱 [建立和套用初始快照集](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="f3c43-135">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
### <a name="to-modify-snapshot-properties-of-an-existing-merge-publication"></a><span data-ttu-id="f3c43-136">修改現有合併式發行集的快照集屬性</span><span class="sxs-lookup"><span data-stu-id="f3c43-136">To modify snapshot properties of an existing merge publication</span></span>  
  
1.  <span data-ttu-id="f3c43-137">在發行集資料庫的發行者上，執行 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f3c43-137">At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="f3c43-138">針對指定**1**的值 **@force_invalidate_snapshot** ，並針對下列其中一個值 **@property** ：</span><span class="sxs-lookup"><span data-stu-id="f3c43-138">Specify a value of **1** for **@force_invalidate_snapshot** and one of the following values for **@property**:</span></span>  
  
    -   <span data-ttu-id="f3c43-139">**alt_snapshot_folder** -也指定的替代快照集資料夾的新路徑 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="f3c43-139">**alt_snapshot_folder** -also specify a new path to the alternate snapshot folder for **@value**.</span></span>  
  
    -   <span data-ttu-id="f3c43-140">**compress_snapshot** -也針對指定**true**或**false**的值， **@value** 以指示替代快照集資料夾中的快照集檔案是否壓縮成 CAB 檔案格式。</span><span class="sxs-lookup"><span data-stu-id="f3c43-140">**compress_snapshot** - also specify a value of either **true** or **false** for **@value** to indicate whether the snapshot files in the alternate snapshot folder are compressed in the CAB file format.</span></span>  
  
    -   <span data-ttu-id="f3c43-141">**pre_snapshot_script** -也針對 **@value** 指定在套用初始快照集之前的初始化期間，將于訂閱者上執行之 **.sql**檔案的檔案名和完整路徑。</span><span class="sxs-lookup"><span data-stu-id="f3c43-141">**pre_snapshot_script** - also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="f3c43-142">**post_snapshot_script** -也針對 **@value** 指定在套用初始快照集之後的初始化期間，將于訂閱者上執行之 **.sql**檔案的檔案名和完整路徑。</span><span class="sxs-lookup"><span data-stu-id="f3c43-142">**post_snapshot_script** - also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="f3c43-143">**snapshot_in_defaultfolder** - 也指定 **true** 或 **false** 的值，以指示快照集是否可在非預設位置中使用。</span><span class="sxs-lookup"><span data-stu-id="f3c43-143">**snapshot_in_defaultfolder** - also specify a value of either **true** or **false** to indicate whether the snapshot is available only in a non-default location.</span></span>  
  
2.  <span data-ttu-id="f3c43-144">從命令提示字元執行 [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) 或是啟動快照集代理程式作業來產生新的快照集。</span><span class="sxs-lookup"><span data-stu-id="f3c43-144">Run the [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) from the command prompt or start the Snapshot Agent job to generate a new snapshot.</span></span> <span data-ttu-id="f3c43-145">如需詳細資訊，請參閱 [建立和套用初始快照集](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="f3c43-145">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3c43-146">範例</span><span class="sxs-lookup"><span data-stu-id="f3c43-146">Example</span></span>  
 <span data-ttu-id="f3c43-147">這個範例會建立使用替代快照集資料夾和壓縮快照集的發行集。</span><span class="sxs-lookup"><span data-stu-id="f3c43-147">This example creates a publication that uses an alternate snapshot folder and a compressed snapshot.</span></span>  
  
 [!code-sql[HowTo#sp_mergealtsnapshot](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubaltsnapshot.sql#sp_mergealtsnapshot)]  
  
## <a name="see-also"></a><span data-ttu-id="f3c43-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3c43-148">See Also</span></span>  
 <span data-ttu-id="f3c43-149">[替代快照集資料夾位置](../alternate-snapshot-folder-locations.md) </span><span class="sxs-lookup"><span data-stu-id="f3c43-149">[Alternate Snapshot Folder Locations](../alternate-snapshot-folder-locations.md) </span></span>  
 <span data-ttu-id="f3c43-150">[壓縮的快照集](../compressed-snapshots.md) </span><span class="sxs-lookup"><span data-stu-id="f3c43-150">[Compressed Snapshots](../compressed-snapshots.md) </span></span>  
 <span data-ttu-id="f3c43-151">[在套用快照集之前及之後執行指令碼](../snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied) </span><span class="sxs-lookup"><span data-stu-id="f3c43-151">[Execute Scripts Before and After the Snapshot Is Applied](../snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied) </span></span>  
 <span data-ttu-id="f3c43-152">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="f3c43-152">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 <span data-ttu-id="f3c43-153">[透過 FTP 傳送快照集](../transfer-snapshots-through-ftp.md) </span><span class="sxs-lookup"><span data-stu-id="f3c43-153">[Transfer Snapshots Through FTP](../transfer-snapshots-through-ftp.md) </span></span>  
 [<span data-ttu-id="f3c43-154">變更發行集與發行項屬性</span><span class="sxs-lookup"><span data-stu-id="f3c43-154">Change Publication and Article Properties</span></span>](change-publication-and-article-properties.md)  
  
  
