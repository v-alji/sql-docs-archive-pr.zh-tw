---
title: 使用參數化篩選管理合併式發行集的資料分割 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- partitions [SQL Server replication]
- merge replication partitions [SQL Server replication], SQL Server Management Studio
- parameterized filters [SQL Server replication], partition management
ms.assetid: fb5566fe-58c5-48f7-8464-814ea78e6221
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 983b02865c0564919259f896bf09d8bdb0cd969f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585280"
---
# <a name="manage-partitions-for-a-merge-publication-with-parameterized-filters"></a><span data-ttu-id="6b640-102">使用參數化篩選管理合併式發行集的資料分割</span><span class="sxs-lookup"><span data-stu-id="6b640-102">Manage Partitions for a Merge Publication with Parameterized Filters</span></span>
  <span data-ttu-id="6b640-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 Replication Management Objects (RMO)，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中使用參數化篩選管理合併式發行集的資料分割。</span><span class="sxs-lookup"><span data-stu-id="6b640-103">This topic describes how to manage partitions for a merge publication with parameterized filters in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="6b640-104">參數化資料列篩選器可用來產生非重疊的資料分割。</span><span class="sxs-lookup"><span data-stu-id="6b640-104">Parameterized row filters can be used to generate nonoverlapping partitions.</span></span> <span data-ttu-id="6b640-105">這些資料分割可以限制為只有一個訂閱能收到給定資料分割。</span><span class="sxs-lookup"><span data-stu-id="6b640-105">These partitions can be restricted so that only one subscription receives a given partition.</span></span> <span data-ttu-id="6b640-106">在這種狀況中，大量的訂閱者會導致大量的資料分割，而這種情況則需要同等數量的資料分割快照集。</span><span class="sxs-lookup"><span data-stu-id="6b640-106">In these cases, a large number of subscribers will result in a large number of partitions, which in turn requires an equal number of partitioned snapshots.</span></span> <span data-ttu-id="6b640-107">如需詳細資訊，請參閱＜ [參數化資料列篩選器](../merge/parameterized-filters-parameterized-row-filters.md)＞。</span><span class="sxs-lookup"><span data-stu-id="6b640-107">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="6b640-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="6b640-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6b640-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="6b640-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6b640-110">建議</span><span class="sxs-lookup"><span data-stu-id="6b640-110">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="6b640-111">**若要使用參數化篩選管理合併式發行集的資料分割，請使用：**</span><span class="sxs-lookup"><span data-stu-id="6b640-111">**To manage partitions for a merge publication with parameterized filters, using:**</span></span>  
  
     [<span data-ttu-id="6b640-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6b640-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6b640-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6b640-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="6b640-114">Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="6b640-114">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6b640-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="6b640-115">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="6b640-116">建議</span><span class="sxs-lookup"><span data-stu-id="6b640-116">Recommendations</span></span>  
  
-   <span data-ttu-id="6b640-117">如果您為複寫拓撲編寫指令碼 (建議您如此做)，則發行集指令碼將包含呼叫建立資料分割的預存程序。</span><span class="sxs-lookup"><span data-stu-id="6b640-117">If you script a replication topology, which is recommended, publication scripts contain the stored procedure calls to create data partitions.</span></span> <span data-ttu-id="6b640-118">指令碼提供所建立資料分割的參考，並提供必要時重新建立一或多個資料分割的方式。</span><span class="sxs-lookup"><span data-stu-id="6b640-118">The script provides a reference for the partitions created and a way in which to re-create one or more partitions if necessary.</span></span> <span data-ttu-id="6b640-119">如需詳細資訊，請參閱 [Scripting Replication](../scripting-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="6b640-119">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
-   <span data-ttu-id="6b640-120">當發行集擁有會產生具有非重疊資料分割之訂閱的參數化篩選時，以及遺失了特定訂閱而需要重新建立時，您必須執行下列作業：移除先前訂閱的資料分割、重新建立訂閱，然後重新建立資料分割。</span><span class="sxs-lookup"><span data-stu-id="6b640-120">When a publication has parameterized filters that yield subscriptions with nonoverlapping partitions, and if a particular subscription is lost and needs to be re-created, you must do the following: remove the partition that was subscribed to, re-create the subscription, and then re-create the partition.</span></span> <span data-ttu-id="6b640-121">如需詳細資訊，請參閱＜ [參數化資料列篩選器](../merge/parameterized-filters-parameterized-row-filters.md)＞。</span><span class="sxs-lookup"><span data-stu-id="6b640-121">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span> <span data-ttu-id="6b640-122">複寫會在發行集建立指令碼產生時，針對現有的「訂閱者」資料分割產生建立指令碼。</span><span class="sxs-lookup"><span data-stu-id="6b640-122">Replication generates creation scripts for existing Subscriber partitions when a publication creation script is generated.</span></span> <span data-ttu-id="6b640-123">如需詳細資訊，請參閱 [Scripting Replication](../scripting-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="6b640-123">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6b640-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6b640-124">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="6b640-125">您可在 [發行集屬性 - \<Publication>] 對話方塊的 [資料分割] 頁面上管理資料分割。</span><span class="sxs-lookup"><span data-stu-id="6b640-125">Manage partitions on the **Data Partitions** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="6b640-126">如需有關存取這個對話方塊的詳細資訊，請參閱＜ [View and Modify Publication Properties](view-and-modify-publication-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="6b640-126">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span> <span data-ttu-id="6b640-127">您可以在此頁面中：建立和刪除資料分割；允許「訂閱者」初始化快照集產生和傳遞；為一個或多個資料分割產生快照集；清除快照集。</span><span class="sxs-lookup"><span data-stu-id="6b640-127">On this page you can: create and delete partitions; allow Subscribers to initiate snapshot generation and delivery; generate snapshots for one or more partitions; and clean up snapshots.</span></span>  
  
#### <a name="to-create-a-partition"></a><span data-ttu-id="6b640-128">若要建立資料分割</span><span class="sxs-lookup"><span data-stu-id="6b640-128">To create a partition</span></span>  
  
1.  <span data-ttu-id="6b640-129">在 [發行集屬性 - \<Publication>] 對話方塊的 [資料分割] 頁面上，按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="6b640-129">On the **Data Partitions** page of the **Publication Properties - \<Publication>** dialog box, click **Add**.</span></span>  
  
2.  <span data-ttu-id="6b640-130">在 **[加入資料分割]** 對話方塊中，輸入與您要建立之資料分割相關聯的 **[HOST_NAME()]** 和/或 **[SUSER_SNAME()]** 值。</span><span class="sxs-lookup"><span data-stu-id="6b640-130">In the **Add Data Partition** dialog box, enter a value for the **HOST_NAME()** and/or **SUSER_SNAME()** value associated with the partition you want to create.</span></span>  
  
3.  <span data-ttu-id="6b640-131">選擇性地指定重新整理快照集的排程：</span><span class="sxs-lookup"><span data-stu-id="6b640-131">Optionally specify a schedule for refreshing snapshots:</span></span>  
  
    1.  <span data-ttu-id="6b640-132">選取 **[排程這個資料分割的快照集代理程式在下列時間執行]**</span><span class="sxs-lookup"><span data-stu-id="6b640-132">Select **Schedule the Snapshot Agent for this partition to run at the following time(s)**</span></span>  
  
    2.  <span data-ttu-id="6b640-133">接受重新重理快照集的預設排程，或按一下 **[變更]** 以指定其他排程。</span><span class="sxs-lookup"><span data-stu-id="6b640-133">Accept the default schedule for refreshing snapshots, or click **Change** to specify a different schedule.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-partition"></a><span data-ttu-id="6b640-134">若要刪除資料分割</span><span class="sxs-lookup"><span data-stu-id="6b640-134">To delete a partition</span></span>  
  
1.  <span data-ttu-id="6b640-135">在 **[資料分割]** 頁面上，從方格中選取一個資料分割。</span><span class="sxs-lookup"><span data-stu-id="6b640-135">On the **Data Partitions** page, select a partition in the grid.</span></span>  
  
2.  <span data-ttu-id="6b640-136">按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="6b640-136">Click **Delete**.</span></span>  
  
#### <a name="to-allow-subscribers-to-initiate-snapshot-generation-and-delivery"></a><span data-ttu-id="6b640-137">若要允許訂閱者初始化快照集的產生與傳遞</span><span class="sxs-lookup"><span data-stu-id="6b640-137">To allow Subscribers to initiate snapshot generation and delivery</span></span>  
  
1.  <span data-ttu-id="6b640-138">在 **[資料分割]** 頁面上，選取 **[新的訂閱者嘗試進行同步處理時，自動定義資料分割並依需要產生快照]** 。</span><span class="sxs-lookup"><span data-stu-id="6b640-138">On the **Data Partitions** page, select **Automatically define a partition and generate a snapshot if needed when a new Subscriber tries to synchronize**.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-generate-a-snapshot-for-a-partition"></a><span data-ttu-id="6b640-139">若要產生資料分割的快照集</span><span class="sxs-lookup"><span data-stu-id="6b640-139">To generate a snapshot for a partition</span></span>  
  
1.  <span data-ttu-id="6b640-140">在 **[資料分割]** 頁面上，從方格中選取一個資料分割。</span><span class="sxs-lookup"><span data-stu-id="6b640-140">On the **Data Partitions** page, select a partition in the grid.</span></span>  
  
2.  <span data-ttu-id="6b640-141">按一下 **[立即產生選取的快照集]** 。</span><span class="sxs-lookup"><span data-stu-id="6b640-141">Click **Generate the selected snapshots now**.</span></span>  
  
#### <a name="to-clean-up-a-snapshot-for-a-partition"></a><span data-ttu-id="6b640-142">若要清除資料分割的快照集</span><span class="sxs-lookup"><span data-stu-id="6b640-142">To clean up a snapshot for a partition</span></span>  
  
1.  <span data-ttu-id="6b640-143">在 **[資料分割]** 頁面上，從方格中選取一個資料分割。</span><span class="sxs-lookup"><span data-stu-id="6b640-143">On the **Data Partitions** page, select a partition in the grid.</span></span>  
  
2.  <span data-ttu-id="6b640-144">按一下 **[清除現有快照集]** 。</span><span class="sxs-lookup"><span data-stu-id="6b640-144">Click **Clean up the existing snapshots**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6b640-145">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6b640-145">Using Transact-SQL</span></span>  
 <span data-ttu-id="6b640-146">若要使用參數化篩選以更好的方式管理發行集，可以使用複寫預存程序，以程式設計的方式列舉現有的資料分割。</span><span class="sxs-lookup"><span data-stu-id="6b640-146">To better manage a publication with parameterized filters, you can programmatically enumerate the existing partitions using replication stored procedures.</span></span> <span data-ttu-id="6b640-147">您也可以建立及刪除現有的資料分割。</span><span class="sxs-lookup"><span data-stu-id="6b640-147">You can also create and delete existing partitions.</span></span> <span data-ttu-id="6b640-148">您可取得下列有關現有資料分割的資訊：</span><span class="sxs-lookup"><span data-stu-id="6b640-148">The following information on existing partitions can be obtained:</span></span>  
  
-   <span data-ttu-id="6b640-149">資料分割的篩選方式 (使用 [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) 或 [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql))。</span><span class="sxs-lookup"><span data-stu-id="6b640-149">How a partition is filtered (using [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) or [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql)).</span></span>  
  
-   <span data-ttu-id="6b640-150">產生資料分割快照集的工作名稱。</span><span class="sxs-lookup"><span data-stu-id="6b640-150">The name of the job that generates a partitioned snapshot.</span></span>  
  
-   <span data-ttu-id="6b640-151">上次執行資料分割快照集作業的時間。</span><span class="sxs-lookup"><span data-stu-id="6b640-151">The last time that a partitioned snapshot job ran.</span></span>  
  
 <span data-ttu-id="6b640-152">雖然兩部分快照集的第二部份可以在初始化新訂閱時視需要而產生，但下列程序可用來控制產生此快照集的方式，並在最方便的時候預先產生此快照集。</span><span class="sxs-lookup"><span data-stu-id="6b640-152">While the second part of the two-part snapshot can be generated on-demand when a new subscription is initialized, the procedures below enable you to control how this snapshot is generated and to pre-generate this snapshot when it is most convenient.</span></span> <span data-ttu-id="6b640-153">如需詳細資訊，請參閱 [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="6b640-153">For more information, see [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md).</span></span>  
  
#### <a name="to-view-information-on-existing-partitions"></a><span data-ttu-id="6b640-154">若要在現有的資料分割上檢視資訊</span><span class="sxs-lookup"><span data-stu-id="6b640-154">To view information on existing partitions</span></span>  
  
1.  <span data-ttu-id="6b640-155">在發行集資料庫的發行者端，執行 [sp_helpmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6b640-155">At the Publisher on the publication database, execute [sp_helpmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql).</span></span> <span data-ttu-id="6b640-156">指定\*\* \@ 發行\*\*集的名稱。</span><span class="sxs-lookup"><span data-stu-id="6b640-156">Specify the name of the publication for **\@publication**.</span></span> <span data-ttu-id="6b640-157"> (選擇性) 指\定\** \@ suser_sname**或** \@ host_nam\e\** ，以根據單一篩選準則僅傳回信息。</span><span class="sxs-lookup"><span data-stu-id="6b640-157">(Optional) Specify **\@suser_sname** or **\@host_name** to return only information based on a single filtering criterion.</span></span>  
  
#### <a name="to-define-a-new-partition-and-generate-a-new-partitioned-snapshot"></a><span data-ttu-id="6b640-158">若要定義新的資料分割並產生新的資料分割快照集</span><span class="sxs-lookup"><span data-stu-id="6b640-158">To define a new partition and generate a new partitioned snapshot</span></span>  
  
1.  <span data-ttu-id="6b640-159">在發行集資料庫的發行者端，執行 [sp_addmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6b640-159">At the Publisher on the publication database, execute [sp_addmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql).</span></span> <span data-ttu-id="6b640-160">針對\*\* \@ 發行\*\*集指定發行集的名稱，並針對下列其中一項定義資料分割的參數化值：</span><span class="sxs-lookup"><span data-stu-id="6b640-160">Specify the name of the publication for **\@publication**, and the parameterized value that defines the partition for one of the following:</span></span>  
  
    -   <span data-ttu-id="6b640-161">\*\* \@ suser_sname\*\* -當參數化篩選是由[SUSER_SNAME &#40;transact-sql&#41;](/sql/t-sql/functions/suser-sname-transact-sql)所傳回的值所定義時。</span><span class="sxs-lookup"><span data-stu-id="6b640-161">**\@suser_sname** - when the parameterized filter is defined by the value returned by [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql).</span></span>  
  
    -   <span data-ttu-id="6b640-162">\*\* \@ host_name\*\* -當參數化篩選是由[HOST_NAME &#40;transact-sql&#41;](/sql/t-sql/functions/host-name-transact-sql)所傳回的值所定義時。</span><span class="sxs-lookup"><span data-stu-id="6b640-162">**\@host_name** - when the parameterized filter is defined by the value returned by [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql).</span></span>  
  
2.  <span data-ttu-id="6b640-163">建立並初始化這個新資料分割的參數化快照集。</span><span class="sxs-lookup"><span data-stu-id="6b640-163">Create and initialize the parameterized snapshot for this new partition.</span></span> <span data-ttu-id="6b640-164">如需詳細資訊，請參閱 [使用參數化篩選建立合併式發行集的快照集](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="6b640-164">For more information, see [Create a Snapshot for a Merge Publication with Parameterized Filters](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).</span></span>  
  
#### <a name="to-delete-a-partition"></a><span data-ttu-id="6b640-165">若要刪除資料分割</span><span class="sxs-lookup"><span data-stu-id="6b640-165">To delete a partition</span></span>  
  
1.  <span data-ttu-id="6b640-166">在發行集資料庫的發行者端，執行 [sp_dropmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6b640-166">At the Publisher on the publication database, execute [sp_dropmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql).</span></span> <span data-ttu-id="6b640-167">針對 [ \*\* \@ 發行\*\*集] 指定發行集的名稱，並針對下列其中一個定義資料分割的參數化值：</span><span class="sxs-lookup"><span data-stu-id="6b640-167">Specify the name of the publication for **\@publication** and the parameterized value that defines the partition for one of the following:</span></span>  
  
    -   <span data-ttu-id="6b640-168">\*\* \@ suser_sname\*\* -當參數化篩選是由[SUSER_SNAME &#40;transact-sql&#41;](/sql/t-sql/functions/suser-sname-transact-sql)所傳回的值所定義時。</span><span class="sxs-lookup"><span data-stu-id="6b640-168">**\@suser_sname** - when the parameterized filter is defined by the value returned by [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql).</span></span>  
  
    -   <span data-ttu-id="6b640-169">\*\* \@ host_name\*\* -當參數化篩選是由[HOST_NAME &#40;transact-sql&#41;](/sql/t-sql/functions/host-name-transact-sql)所傳回的值所定義時。</span><span class="sxs-lookup"><span data-stu-id="6b640-169">**\@host_name** - when the parameterized filter is defined by the value returned by [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql).</span></span>  
  
     <span data-ttu-id="6b640-170">這也會移除資料分割的快照集作業和快照集檔案。</span><span class="sxs-lookup"><span data-stu-id="6b640-170">This also removes the snapshot job and any snapshot files for the partition.</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="6b640-171">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="6b640-171">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="6b640-172">若要使用參數化篩選以更好的方式管理發行集，可以使用 Replication Management Objects (RMO)，以程式設計的方式建立新的「訂閱者」資料分割、列舉現有的「訂閱者」資料分割，以及刪除「訂閱者」資料分割。</span><span class="sxs-lookup"><span data-stu-id="6b640-172">To better manage a publication with parameterized filters, you can programmatically create new Subscriber partitions, enumerate the existing Subscriber partitions, and delete Subscriber partitions by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="6b640-173">如需有關如何建立「訂閱者」資料分割的詳細資訊，請參閱＜ [使用參數化篩選建立合併式發行集的快照集](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)＞。</span><span class="sxs-lookup"><span data-stu-id="6b640-173">For information about how to create Subscriber partitions, see [Create a Snapshot for a Merge Publication with Parameterized Filters](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).</span></span> <span data-ttu-id="6b640-174">您可取得下列有關現有資料分割的資訊：</span><span class="sxs-lookup"><span data-stu-id="6b640-174">The following information about existing partitions can be obtained:</span></span>  
  
-   <span data-ttu-id="6b640-175">資料分割所根據的值和篩選函數。</span><span class="sxs-lookup"><span data-stu-id="6b640-175">The value and filtering function upon which the partition is based.</span></span>  
  
-   <span data-ttu-id="6b640-176">為「訂閱者」產生參數化快照集的作業名稱。</span><span class="sxs-lookup"><span data-stu-id="6b640-176">The name of the job that generates a parameterized snapshot for the Subscriber.</span></span>  
  
-   <span data-ttu-id="6b640-177">上次執行參數化快照集作業的時間。</span><span class="sxs-lookup"><span data-stu-id="6b640-177">The last time that a parameterized snapshot job ran.</span></span>  
  
#### <a name="to-view-information-on-existing-partitions"></a><span data-ttu-id="6b640-178">若要在現有的資料分割上檢視資訊</span><span class="sxs-lookup"><span data-stu-id="6b640-178">To view information on existing partitions</span></span>  
  
1.  <span data-ttu-id="6b640-179">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="6b640-179">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="6b640-180">建立 <xref:Microsoft.SqlServer.Replication.MergePublication> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6b640-180">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class.</span></span> <span data-ttu-id="6b640-181">設定發行集的 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 屬性，並將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定為在步驟 1 中建立的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 。</span><span class="sxs-lookup"><span data-stu-id="6b640-181">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> created in step 1.</span></span>  
  
3.  <span data-ttu-id="6b640-182">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="6b640-182">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="6b640-183">如果此方法傳回 `false`，則表示步驟 2 中的發行集屬性定義不正確，或者該發行集不存在。</span><span class="sxs-lookup"><span data-stu-id="6b640-183">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="6b640-184">呼叫 <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> 方法，並將結果傳遞到 <xref:Microsoft.SqlServer.Replication.MergePartition> 物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="6b640-184">Call the <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> method, and pass the result to an array of <xref:Microsoft.SqlServer.Replication.MergePartition> objects.</span></span>  
  
5.  <span data-ttu-id="6b640-185">針對陣列中的每個 <xref:Microsoft.SqlServer.Replication.MergePartition> 物件，取得任何所要的屬性。</span><span class="sxs-lookup"><span data-stu-id="6b640-185">For each <xref:Microsoft.SqlServer.Replication.MergePartition> object in the array, get any properties of interest.</span></span>  
  
#### <a name="to-delete-existing-partitions"></a><span data-ttu-id="6b640-186">若要刪除現有的資料分割</span><span class="sxs-lookup"><span data-stu-id="6b640-186">To delete existing partitions</span></span>  
  
1.  <span data-ttu-id="6b640-187">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="6b640-187">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="6b640-188">建立 <xref:Microsoft.SqlServer.Replication.MergePublication> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6b640-188">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class.</span></span> <span data-ttu-id="6b640-189">設定發行集的 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 屬性，並將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定為在步驟 1 中建立的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 。</span><span class="sxs-lookup"><span data-stu-id="6b640-189">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> created in step 1.</span></span>  
  
3.  <span data-ttu-id="6b640-190">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="6b640-190">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="6b640-191">如果此方法傳回 `false`，則表示步驟 2 中的發行集屬性定義不正確，或者該發行集不存在。</span><span class="sxs-lookup"><span data-stu-id="6b640-191">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="6b640-192">呼叫 <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> 方法，並將結果傳遞到 <xref:Microsoft.SqlServer.Replication.MergePartition> 物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="6b640-192">Call the <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> method, and pass the result to an array of <xref:Microsoft.SqlServer.Replication.MergePartition> objects.</span></span>  
  
5.  <span data-ttu-id="6b640-193">對於陣列中的每個 <xref:Microsoft.SqlServer.Replication.MergePartition> 物件，決定是否應該刪除資料分割：</span><span class="sxs-lookup"><span data-stu-id="6b640-193">For each <xref:Microsoft.SqlServer.Replication.MergePartition> object in the array, determine whether the partition should be deleted.</span></span> <span data-ttu-id="6b640-194">這項決定通常是根據 <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A> 屬性或 <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A> 屬性的值而定。</span><span class="sxs-lookup"><span data-stu-id="6b640-194">This decision is usually based on the value of the <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A> property or the <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A> property.</span></span>  
  
6.  <span data-ttu-id="6b640-195">在步驟 2 的 <xref:Microsoft.SqlServer.Replication.MergePublication.RemoveMergePartition%2A> 物件上呼叫 <xref:Microsoft.SqlServer.Replication.MergePublication> 方法。</span><span class="sxs-lookup"><span data-stu-id="6b640-195">Call the <xref:Microsoft.SqlServer.Replication.MergePublication.RemoveMergePartition%2A> method on the <xref:Microsoft.SqlServer.Replication.MergePublication> object from step 2.</span></span> <span data-ttu-id="6b640-196">傳遞步驟 5 的 <xref:Microsoft.SqlServer.Replication.MergePartition> 物件。</span><span class="sxs-lookup"><span data-stu-id="6b640-196">Pass the <xref:Microsoft.SqlServer.Replication.MergePartition> object from step 5.</span></span>  
  
7.  <span data-ttu-id="6b640-197">針對每個刪除的資料分割重複步驟 6。</span><span class="sxs-lookup"><span data-stu-id="6b640-197">Repeat step 6 for each partition that is deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b640-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b640-198">See Also</span></span>  
 <span data-ttu-id="6b640-199">[Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="6b640-199">[Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="6b640-200">Snapshots for Merge Publications with Parameterized Filters</span><span class="sxs-lookup"><span data-stu-id="6b640-200">Snapshots for Merge Publications with Parameterized Filters</span></span>](../snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  
