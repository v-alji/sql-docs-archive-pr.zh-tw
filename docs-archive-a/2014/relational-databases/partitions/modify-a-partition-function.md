---
title: 修改資料分割函式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: ae5bfc09-f27a-4ea9-9518-485278b11674
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: bf14e633e62839b1abca7f38f833efab933c18f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687822"
---
# <a name="modify-a-partition-function"></a><span data-ttu-id="4fa49-102">修改資料分割函數</span><span class="sxs-lookup"><span data-stu-id="4fa49-102">Modify a Partition Function</span></span>
  <span data-ttu-id="4fa49-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在資料分割資料表或索引的資料分割函數中，加上或減去指定的資料分割數 (遞增為 1)，藉以變更 [!INCLUDE[tsql](../../includes/tsql-md.md)]中資料表或索引的資料分割方式。</span><span class="sxs-lookup"><span data-stu-id="4fa49-103">You can change the way a table or index is partitioned in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by adding or subtracting the number of partitions specified, in increments of 1, in the partition function of the partitioned table or index by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="4fa49-104">若要加入資料分割，可以將現有資料分割「拆解」為兩個資料分割，並重新定義新資料分割的界限。</span><span class="sxs-lookup"><span data-stu-id="4fa49-104">When you add a partition, you do so by "splitting" an existing partition into two partitions and redefining the boundaries of the new partitions.</span></span> <span data-ttu-id="4fa49-105">若要卸除資料分割，可以將兩個資料分割的界限「合併」成為一個。</span><span class="sxs-lookup"><span data-stu-id="4fa49-105">When you drop a partition, you do so by "merging" the boundaries of two partitions into one.</span></span> <span data-ttu-id="4fa49-106">最後這個動作會重新擴展一個資料分割，並使另一個資料分割成為未指派。</span><span class="sxs-lookup"><span data-stu-id="4fa49-106">This last action repopulates one partition and leaves the other partition unassigned.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="4fa49-107">多份資料表或索引可以使用相同的資料分割函數。</span><span class="sxs-lookup"><span data-stu-id="4fa49-107">More than one table or index can use the same partition function.</span></span> <span data-ttu-id="4fa49-108">當您修改資料分割函數時，將會在單一交易中影響所有資料表或索引。</span><span class="sxs-lookup"><span data-stu-id="4fa49-108">When you modify a partition function, you affect all of them in a single transaction.</span></span> <span data-ttu-id="4fa49-109">修改之前，請先檢查資料分割函式的相依性。</span><span class="sxs-lookup"><span data-stu-id="4fa49-109">Check the partition function's dependencies before modifying it.</span></span>  
  
 <span data-ttu-id="4fa49-110">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="4fa49-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4fa49-111">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="4fa49-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4fa49-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="4fa49-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4fa49-113">安全性</span><span class="sxs-lookup"><span data-stu-id="4fa49-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4fa49-114">**若要使用下列項目來修改資料分割函數：**</span><span class="sxs-lookup"><span data-stu-id="4fa49-114">**To modify a partition function, using:**</span></span>  
  
     [<span data-ttu-id="4fa49-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4fa49-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4fa49-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4fa49-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4fa49-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="4fa49-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4fa49-118">限制事項</span><span class="sxs-lookup"><span data-stu-id="4fa49-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="4fa49-119">ALTER PARTITION FUNCTION 只能用來將一個資料分割拆解成兩個，或將兩個資料分割合併為一個。</span><span class="sxs-lookup"><span data-stu-id="4fa49-119">ALTER PARTITION FUNCTION can only be used for splitting one partition into two, or for merging two partitions into one.</span></span> <span data-ttu-id="4fa49-120">若要變更資料表或索引的資料分割方式 (例如，從 10 個資料分割變更成 5 個)，您可以使用下列任何一個選項：</span><span class="sxs-lookup"><span data-stu-id="4fa49-120">To change the way a table or index is partitioned (from 10 partitions to 5, for example), you can use any one of the following options:</span></span>  
  
    -   <span data-ttu-id="4fa49-121">使用所需的資料分割函數來建立新的資料分割資料表，然後再使用 INSERT INTO ...SELECT FROM [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式或 **中的** [管理資料分割精靈] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，將舊資料表中的資料插入新資料表中。</span><span class="sxs-lookup"><span data-stu-id="4fa49-121">Create a new partitioned table with the desired partition function, and then insert the data from the old table into the new table by using either an INSERT INTO ... SELECT FROM [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or the **Manage Partition Wizard** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
    -   <span data-ttu-id="4fa49-122">建立堆積的資料分割叢集索引。</span><span class="sxs-lookup"><span data-stu-id="4fa49-122">Create a partitioned clustered index on a heap.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="4fa49-123">卸除資料分割叢集索引會產生資料分割堆積。</span><span class="sxs-lookup"><span data-stu-id="4fa49-123">Dropping a partitioned clustered index results in a partitioned heap.</span></span>  
  
    -   <span data-ttu-id="4fa49-124">利用設定了 DROP EXISTING = ON 子句的 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX 陳述式來卸除和重建現有的資料分割索引。</span><span class="sxs-lookup"><span data-stu-id="4fa49-124">Drop and rebuild an existing partitioned index by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX statement with the DROP EXISTING = ON clause.</span></span>  
  
    -   <span data-ttu-id="4fa49-125">執行 ALTER PARTITION FUNCTION 陳述式的序列。</span><span class="sxs-lookup"><span data-stu-id="4fa49-125">Perform a sequence of ALTER PARTITION FUNCTION statements.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4fa49-126">不提供修改資料分割函數的複寫支援。</span><span class="sxs-lookup"><span data-stu-id="4fa49-126">does not provide replication support for modifying a partition function.</span></span> <span data-ttu-id="4fa49-127">如果您要變更發行集資料庫中的資料分割函數，必須在訂閱資料庫中手動執行此作業。</span><span class="sxs-lookup"><span data-stu-id="4fa49-127">If you want to make changes to a partition function in the publication database, you must do this manually in the subscription database.</span></span>  
  
-   <span data-ttu-id="4fa49-128">ALTER PARTITION FUNCTION 所影響的所有檔案群組都必須在線上。</span><span class="sxs-lookup"><span data-stu-id="4fa49-128">All filegroups that are affected by ALTER PARTITION FUNCTION must be online.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4fa49-129">Security</span><span class="sxs-lookup"><span data-stu-id="4fa49-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4fa49-130">權限</span><span class="sxs-lookup"><span data-stu-id="4fa49-130">Permissions</span></span>  
 <span data-ttu-id="4fa49-131">下列中的任何權限都可用來執行 ALTER PARTITION FUNCTION：</span><span class="sxs-lookup"><span data-stu-id="4fa49-131">Any one of the following permissions can be used to execute ALTER PARTITION FUNCTION:</span></span>  
  
-   <span data-ttu-id="4fa49-132">ALTER ANY DATASPACE 權限。</span><span class="sxs-lookup"><span data-stu-id="4fa49-132">ALTER ANY DATASPACE permission.</span></span> <span data-ttu-id="4fa49-133">這個權限預設會授與 **sysadmin** 固定伺服器角色以及 **db_owner** 和 **db_ddladmin** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="4fa49-133">This permission defaults to members of the **sysadmin** fixed server role and the **db_owner** and **db_ddladmin** fixed database roles.</span></span>  
  
-   <span data-ttu-id="4fa49-134">對於建立資料分割函數之資料庫的 CONTROL 或 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="4fa49-134">CONTROL or ALTER permission on the database in which the partition function was created.</span></span>  
  
-   <span data-ttu-id="4fa49-135">對於建立資料分割函數之資料庫伺服器的 CONTROL SERVER 或 ALTER ANY DATABASE 權限。</span><span class="sxs-lookup"><span data-stu-id="4fa49-135">CONTROL SERVER or ALTER ANY DATABASE permission on the server of the database in which the partition function was created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4fa49-136">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4fa49-136">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="4fa49-137">**若要修改資料分割函數：**</span><span class="sxs-lookup"><span data-stu-id="4fa49-137">**To modify a partition function:**</span></span>  
  
 <span data-ttu-id="4fa49-138">您無法使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]來執行這項特定動作。</span><span class="sxs-lookup"><span data-stu-id="4fa49-138">This specific action cannot be performed using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="4fa49-139">若要修改資料分割函數，您必須先刪除此函數，然後再使用 [建立資料分割精靈] 來建立具有所需屬性的新函數。</span><span class="sxs-lookup"><span data-stu-id="4fa49-139">In order to modify a partition function, you must first delete the function and then create a new one with the desired properties using the Create Partition Wizard.</span></span> <span data-ttu-id="4fa49-140">如需相關資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="4fa49-140">For more information, see</span></span>  
  
#### <a name="to-delete-a-partition-function"></a><span data-ttu-id="4fa49-141">若要刪除資料分割函數</span><span class="sxs-lookup"><span data-stu-id="4fa49-141">To delete a partition function</span></span>  
  
1.  <span data-ttu-id="4fa49-142">展開您想要刪除資料分割函數的資料庫，然後展開 **[儲存體]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4fa49-142">Expand the database where you want to delete the partition function and then expand the **Storage** folder.</span></span>  
  
2.  <span data-ttu-id="4fa49-143">展開 **[資料分割函數]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4fa49-143">Expand the **Partition Functions** folder.</span></span>  
  
3.  <span data-ttu-id="4fa49-144">以滑鼠右鍵按一下您想要刪除的資料分割函數，然後選取 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="4fa49-144">Right-click the partition function you want to delete and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="4fa49-145">在 **[刪除物件]** 對話方塊中，確定已選取正確的資料分割函數，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4fa49-145">In the **Delete Object** dialog box, ensure that the correct partition function is selected, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4fa49-146">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4fa49-146">Using Transact-SQL</span></span>  
  
#### <a name="to-split-a-single-partition-into-two-partitions"></a><span data-ttu-id="4fa49-147">若要將單一資料分割拆解成兩個資料分割</span><span class="sxs-lookup"><span data-stu-id="4fa49-147">To split a single partition into two partitions</span></span>  
  
1.  <span data-ttu-id="4fa49-148">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4fa49-148">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4fa49-149">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="4fa49-149">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4fa49-150">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4fa49-150">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Look for a previous version of the partition function "myRangePF1" and deletes it if it is found.  
    IF EXISTS (SELECT * FROM sys.partition_functions  
        WHERE name = 'myRangePF1')  
        DROP PARTITION FUNCTION myRangePF1;  
    GO  
    -- Create a new partition function called "myRangePF1" that partitions a table into four partitions.  
    CREATE PARTITION FUNCTION myRangePF1 (int)  
    AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
    GO  
    --Split the partition between boundary_values 100 and 1000  
    --to create two partitions between boundary_values 100 and 500  
    --and between boundary_values 500 and 1000.  
    ALTER PARTITION FUNCTION myRangePF1 ()  
    SPLIT RANGE (500);  
    ```  
  
#### <a name="to-merge-two-partitions-into-one-partition"></a><span data-ttu-id="4fa49-151">若要將兩個資料分割合併成一個資料分割</span><span class="sxs-lookup"><span data-stu-id="4fa49-151">To merge two partitions into one partition</span></span>  
  
1.  <span data-ttu-id="4fa49-152">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4fa49-152">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4fa49-153">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="4fa49-153">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4fa49-154">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4fa49-154">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Look for a previous version of the partition function "myRangePF1" and deletes it if it is found.  
    IF EXISTS (SELECT * FROM sys.partition_functions  
        WHERE name = 'myRangePF1')  
        DROP PARTITION FUNCTION myRangePF1;  
    GO  
    -- Create a new partition function called "myRangePF1" that partitions a table into four partitions.  
    CREATE PARTITION FUNCTION myRangePF1 (int)  
    AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
    GO  
    --Merge the partitions between boundary_values 1 and 100  
    --and between boundary_values 100 and 1000 to create one partition  
    --between boundary_values 1 and 1000.  
    ALTER PARTITION FUNCTION myRangePF1 ()  
    MERGE RANGE (100);  
    ```  
  
 <span data-ttu-id="4fa49-155">如需詳細資訊，請參閱 [ALTER PARTITION FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-partition-function-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4fa49-155">For more information, see [ALTER PARTITION FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-partition-function-transact-sql).</span></span>  
  
  
