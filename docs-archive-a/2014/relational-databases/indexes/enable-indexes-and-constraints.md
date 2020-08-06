---
title: 啟用索引和條件約束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], enabling
- nonclustered indexes [SQL Server], enabling a disabled index
- index enabling [SQL Server]
- disabled indexes [SQL Server], how to enable
- constraints [SQL Server], enabling
- clustered indexes, enabling disabled indexes
ms.assetid: c55c8865-322e-4ab0-ba04-ea1f56735353
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4d4e79689b80a40d00958fa557fe51df2adf9c14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606308"
---
# <a name="enable-indexes-and-constraints"></a><span data-ttu-id="e19bd-102">啟用索引與條件約束</span><span class="sxs-lookup"><span data-stu-id="e19bd-102">Enable Indexes and Constraints</span></span>
  <span data-ttu-id="e19bd-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中啟用已停用的索引。</span><span class="sxs-lookup"><span data-stu-id="e19bd-103">This topic describes how to enable a disabled index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e19bd-104">在停用索引後，在重建或卸除索引之前仍然是停用狀態。</span><span class="sxs-lookup"><span data-stu-id="e19bd-104">After an index is disabled, it remains in a disabled state until it is rebuilt or dropped</span></span>  
  
 <span data-ttu-id="e19bd-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="e19bd-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e19bd-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="e19bd-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e19bd-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="e19bd-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e19bd-108">安全性</span><span class="sxs-lookup"><span data-stu-id="e19bd-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e19bd-109">**使用下列方法啟用已停用的索引：**</span><span class="sxs-lookup"><span data-stu-id="e19bd-109">**To enable a disabled index, using:**</span></span>  
  
     [<span data-ttu-id="e19bd-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e19bd-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e19bd-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e19bd-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e19bd-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="e19bd-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e19bd-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="e19bd-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e19bd-114">在重建索引後，任何因為停用索引而停用的條件約束，都必須手動啟用。</span><span class="sxs-lookup"><span data-stu-id="e19bd-114">After rebuilding the index, any constraints that were disabled because of disabling the index must be manually enabled.</span></span> <span data-ttu-id="e19bd-115">重建關聯索引將可啟用 PRIMARY KEY 與 UNIQUE 條件約束。</span><span class="sxs-lookup"><span data-stu-id="e19bd-115">PRIMARY KEY and UNIQUE constraints are enabled by rebuilding the associated index.</span></span> <span data-ttu-id="e19bd-116">您必須先重建 (啟用) 索引，才可以啟用參考 PRIMARY KEY 或 UNIQUE 條件約束的 FOREIGN KEY 條件約束。</span><span class="sxs-lookup"><span data-stu-id="e19bd-116">This index must be rebuilt (enabled) before you can enable FOREIGN KEY constraints that reference the PRIMARY KEY or UNIQUE constraint.</span></span> <span data-ttu-id="e19bd-117">FOREIGN KEY 條件約束是使用 ALTER TABLE CHECK CONSTRAINT 陳述式來啟用。</span><span class="sxs-lookup"><span data-stu-id="e19bd-117">FOREIGN KEY constraints are enabled by using the ALTER TABLE CHECK CONSTRAINT statement.</span></span>  
  
-   <span data-ttu-id="e19bd-118">當 ONLINE 選項設定為 ON 時，將無法重建停用的叢集索引。</span><span class="sxs-lookup"><span data-stu-id="e19bd-118">Rebuilding a disabled clustered index cannot be performed when the ONLINE option is set to ON.</span></span>  
  
-   <span data-ttu-id="e19bd-119">當停用或啟用叢集索引，而非叢集索引是停用狀態時，叢集索引動作在停用的非叢集索引上具有下列結果。</span><span class="sxs-lookup"><span data-stu-id="e19bd-119">When the clustered index is disabled or enabled and the nonclustered index is disabled, the clustered index action has the following results on the disabled nonclustered index.</span></span>  
  
    |<span data-ttu-id="e19bd-120">叢集索引動作</span><span class="sxs-lookup"><span data-stu-id="e19bd-120">Clustered Index Action</span></span>|<span data-ttu-id="e19bd-121">停用的非叢集索引...</span><span class="sxs-lookup"><span data-stu-id="e19bd-121">Disabled Nonclustered Index ...</span></span>|  
    |----------------------------|-----------------------------------|  
    |<span data-ttu-id="e19bd-122">ALTER INDEX REBUILD</span><span class="sxs-lookup"><span data-stu-id="e19bd-122">ALTER INDEX REBUILD.</span></span>|<span data-ttu-id="e19bd-123">仍然停用。</span><span class="sxs-lookup"><span data-stu-id="e19bd-123">Remains disabled.</span></span>|  
    |<span data-ttu-id="e19bd-124">ALTER INDEX ALL REBUILD</span><span class="sxs-lookup"><span data-stu-id="e19bd-124">ALTER INDEX ALL REBUILD.</span></span>|<span data-ttu-id="e19bd-125">已重建和啟用。</span><span class="sxs-lookup"><span data-stu-id="e19bd-125">Is rebuilt and enabled.</span></span>|  
    |<span data-ttu-id="e19bd-126">DROP INDEX</span><span class="sxs-lookup"><span data-stu-id="e19bd-126">DROP INDEX.</span></span>|<span data-ttu-id="e19bd-127">仍然停用。</span><span class="sxs-lookup"><span data-stu-id="e19bd-127">Remains disabled.</span></span>|  
    |<span data-ttu-id="e19bd-128">CREATE INDEX WITH DROP_EXISTING</span><span class="sxs-lookup"><span data-stu-id="e19bd-128">CREATE INDEX WITH DROP_EXISTING.</span></span>|<span data-ttu-id="e19bd-129">仍然停用。</span><span class="sxs-lookup"><span data-stu-id="e19bd-129">Remains disabled.</span></span>|  
  
     <span data-ttu-id="e19bd-130">建立新叢集索引的行為會與 ALTER INDEX ALL REBUILD 相同。</span><span class="sxs-lookup"><span data-stu-id="e19bd-130">Creating a new clustered index, behaves the same as ALTER INDEX ALL REBUILD.</span></span>  
  
-   <span data-ttu-id="e19bd-131">在與叢集索引關聯的非叢集索引上所允許的動作，將視此兩種索引類型的停用或啟用狀態而定。</span><span class="sxs-lookup"><span data-stu-id="e19bd-131">Allowed actions on nonclustered indexes associated with a clustered index depend on the state, whether disabled or enabled, of both index types.</span></span> <span data-ttu-id="e19bd-132">下表摘要非叢集索引可允許的動作。</span><span class="sxs-lookup"><span data-stu-id="e19bd-132">The following table summarizes the allowed actions on nonclustered indexes.</span></span>  
  
    |<span data-ttu-id="e19bd-133">非叢集索引動作</span><span class="sxs-lookup"><span data-stu-id="e19bd-133">Nonclustered Index Action</span></span>|<span data-ttu-id="e19bd-134">當叢集和非叢集索引都已停用時。</span><span class="sxs-lookup"><span data-stu-id="e19bd-134">When both the clustered and nonclustered indexes are disabled.</span></span>|<span data-ttu-id="e19bd-135">當叢集索引已啟用，而非叢集索引處於停用或啟用狀態時。</span><span class="sxs-lookup"><span data-stu-id="e19bd-135">When the clustered index is enabled and the nonclustered index is in either state.</span></span>|  
    |-------------------------------|--------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
    |<span data-ttu-id="e19bd-136">ALTER INDEX REBUILD</span><span class="sxs-lookup"><span data-stu-id="e19bd-136">ALTER INDEX REBUILD.</span></span>|<span data-ttu-id="e19bd-137">此動作會失敗。</span><span class="sxs-lookup"><span data-stu-id="e19bd-137">The action fails.</span></span>|<span data-ttu-id="e19bd-138">此動作會成功。</span><span class="sxs-lookup"><span data-stu-id="e19bd-138">The action succeeds.</span></span>|  
    |<span data-ttu-id="e19bd-139">DROP INDEX</span><span class="sxs-lookup"><span data-stu-id="e19bd-139">DROP INDEX.</span></span>|<span data-ttu-id="e19bd-140">此動作會成功。</span><span class="sxs-lookup"><span data-stu-id="e19bd-140">The action succeeds.</span></span>|<span data-ttu-id="e19bd-141">此動作會成功。</span><span class="sxs-lookup"><span data-stu-id="e19bd-141">The action succeeds.</span></span>|  
    |<span data-ttu-id="e19bd-142">CREATE INDEX WITH DROP_EXISTING</span><span class="sxs-lookup"><span data-stu-id="e19bd-142">CREATE INDEX WITH DROP_EXISTING.</span></span>|<span data-ttu-id="e19bd-143">此動作會失敗。</span><span class="sxs-lookup"><span data-stu-id="e19bd-143">The action fails.</span></span>|<span data-ttu-id="e19bd-144">此動作會成功。</span><span class="sxs-lookup"><span data-stu-id="e19bd-144">The action succeeds.</span></span>|  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e19bd-145">Security</span><span class="sxs-lookup"><span data-stu-id="e19bd-145">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e19bd-146">權限</span><span class="sxs-lookup"><span data-stu-id="e19bd-146">Permissions</span></span>  
 <span data-ttu-id="e19bd-147">需要資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="e19bd-147">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="e19bd-148">如果使用 DBCC DBREINDEX，使用者必須擁有該資料表，或者是 **系統管理員** 固定伺服器角色或 **db_ddladmin** 和 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="e19bd-148">If using DBCC DBREINDEX, eser must either own the table or be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e19bd-149">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e19bd-149">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-enable-a-disabled-index"></a><span data-ttu-id="e19bd-150">啟用已停用的索引</span><span class="sxs-lookup"><span data-stu-id="e19bd-150">To enable a disabled index</span></span>  
  
1.  <span data-ttu-id="e19bd-151">在 [物件總管] 中，按一下加號展開資料庫，此資料庫包含您要啟用索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="e19bd-151">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to enable an index.</span></span>  
  
2.  <span data-ttu-id="e19bd-152">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e19bd-152">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="e19bd-153">按一下加號展開要啟用索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="e19bd-153">Click the plus sign to expand the table on which you want to enable an index.</span></span>  
  
4.  <span data-ttu-id="e19bd-154">按一下加號展開 **[索引]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e19bd-154">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="e19bd-155">以滑鼠右鍵按一下您要啟用的索引，然後選取 [重建]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e19bd-155">Right-click the index you want to enable and select **Rebuild**.</span></span>  
  
6.  <span data-ttu-id="e19bd-156">在 **[重建索引]** 對話方塊中，確認 **[要重建的索引]** 方格中有正確索引，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="e19bd-156">In the **Rebuild Indexes** dialog box, verify that the correct index is in the **Indexes to rebuild** grid and click **OK**.</span></span>  
  
#### <a name="to-enable-all-indexes-on-a-table"></a><span data-ttu-id="e19bd-157">啟用資料表上的所有索引</span><span class="sxs-lookup"><span data-stu-id="e19bd-157">To enable all indexes on a table</span></span>  
  
1.  <span data-ttu-id="e19bd-158">在 [物件總管] 中，按一下加號展開資料庫，此資料庫包含您要啟用索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="e19bd-158">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to enable the indexes.</span></span>  
  
2.  <span data-ttu-id="e19bd-159">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e19bd-159">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="e19bd-160">按一下加號展開要啟用索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="e19bd-160">Click the plus sign to expand the table on which you want to enable the indexes.</span></span>  
  
4.  <span data-ttu-id="e19bd-161">以滑鼠右鍵按一下 [索引]\*\*\*\* 資料夾，並選取 [全部重建]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e19bd-161">Right-click the **Indexes** folder and select **Rebuild All**.</span></span>  
  
5.  <span data-ttu-id="e19bd-162">在 **[重建索引]** 對話方塊中，確認 **[要重建的索引]** 方格中有正確索引，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e19bd-162">In the **Rebuild Indexes** dialog box, verify that the correct indexes are in the **Indexes to rebuild** grid and click **OK**.</span></span> <span data-ttu-id="e19bd-163">若要從 **[要重建的索引]** 方格中移除索引，請選取索引，然後按下 DELETE 鍵。</span><span class="sxs-lookup"><span data-stu-id="e19bd-163">To remove an index from the **Indexes to rebuild** grid, select the index and then press the Delete key.</span></span>  
  
 <span data-ttu-id="e19bd-164">**[重建索引]** 對話方塊中提供下列資訊：</span><span class="sxs-lookup"><span data-stu-id="e19bd-164">The following information is available in the **Rebuild Indexes** dialog box:</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e19bd-165">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e19bd-165">Using Transact-SQL</span></span>  
  
#### <a name="to-enable-a-disabled-index-using-alter-index"></a><span data-ttu-id="e19bd-166">使用 ALTER INDEX 啟用已停用的索引</span><span class="sxs-lookup"><span data-stu-id="e19bd-166">To enable a disabled index using ALTER INDEX</span></span>  
  
1.  <span data-ttu-id="e19bd-167">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e19bd-167">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e19bd-168">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="e19bd-168">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e19bd-169">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="e19bd-169">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Enables the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table.  
  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
    REBUILD;   
    GO  
    ```  
  
#### <a name="to-enable-a-disabled-index-using-create-index"></a><span data-ttu-id="e19bd-170">使用 CREATE INDEX 啟用已停用的索引</span><span class="sxs-lookup"><span data-stu-id="e19bd-170">To enable a disabled index using CREATE INDEX</span></span>  
  
1.  <span data-ttu-id="e19bd-171">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e19bd-171">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e19bd-172">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="e19bd-172">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e19bd-173">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="e19bd-173">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- re-creates the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table  
    -- using the OrganizationLevel and OrganizationNode columns  
    -- and then deletes the existing IX_Employee_OrganizationLevel_OrganizationNode index  
    CREATE INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
       (OrganizationLevel, OrganizationNode)  
    WITH (DROP_EXISTING = ON);  
    GO  
    ```  
  
#### <a name="to-enable-a-disabled-index-using-dbcc-dbreindex"></a><span data-ttu-id="e19bd-174">使用 DBCC DBREINDEX 啟用已停用的索引</span><span class="sxs-lookup"><span data-stu-id="e19bd-174">To enable a disabled index using DBCC DBREINDEX</span></span>  
  
1.  <span data-ttu-id="e19bd-175">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e19bd-175">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e19bd-176">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="e19bd-176">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e19bd-177">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="e19bd-177">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- enables the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table  
    DBCC DBREINDEX ("HumanResources.Employee", IX_Employee_OrganizationLevel_OrganizationNode);  
    GO  
    ```  
  
#### <a name="to-enable-all-indexes-on-a-table-using-alter-index"></a><span data-ttu-id="e19bd-178">使用 ALTER INDEX 啟用資料表上的所有索引</span><span class="sxs-lookup"><span data-stu-id="e19bd-178">To enable all indexes on a table using ALTER INDEX</span></span>  
  
1.  <span data-ttu-id="e19bd-179">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e19bd-179">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e19bd-180">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="e19bd-180">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e19bd-181">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="e19bd-181">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- enables all indexes  
    -- on the HumanResources.Employee table  
    ALTER INDEX ALL ON HumanResources.Employee  
    REBUILD;  
    GO  
    ```  
  
#### <a name="to-enable-all-indexes-on-a-table-using-dbcc-dbreindex"></a><span data-ttu-id="e19bd-182">使用 DBCC DBREINDEX 啟用資料表上的所有索引</span><span class="sxs-lookup"><span data-stu-id="e19bd-182">To enable all indexes on a table using DBCC DBREINDEX</span></span>  
  
1.  <span data-ttu-id="e19bd-183">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e19bd-183">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e19bd-184">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="e19bd-184">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e19bd-185">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="e19bd-185">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- enables all indexes  
    -- on the HumanResources.Employee table  
    DBCC DBREINDEX ("HumanResources.Employee", " ");  
    GO  
    ```  
  
 <span data-ttu-id="e19bd-186">如需詳細資訊，請參閱 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)、[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) 和 [DBCC DBREINDEX &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e19bd-186">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql), [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql), and [DBCC DBREINDEX &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql).</span></span>  
  
  
