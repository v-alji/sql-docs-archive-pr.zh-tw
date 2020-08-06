---
title: 將現有的索引移至不同的檔案群組 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- moving tables
- switching filegroups for index
- moving indexes
- indexes [SQL Server], moving
- filegroups [SQL Server], switching
ms.assetid: 167ebe77-487d-4ca8-9452-4b2c7d5cb96e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c99847dcb8d4d65272dd3660c7fd60d3efb8d951
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606295"
---
# <a name="move-an-existing-index-to-a-different-filegroup"></a><span data-ttu-id="38a09-102">將現有的索引移至不同的檔案群組</span><span class="sxs-lookup"><span data-stu-id="38a09-102">Move an Existing Index to a Different Filegroup</span></span>
  <span data-ttu-id="38a09-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中將目前檔案群組的現有索引移到不同的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="38a09-103">This topic describes how to move an existing index from its current filegroup to a different filegroup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="38a09-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="38a09-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="38a09-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="38a09-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="38a09-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="38a09-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="38a09-107">安全性</span><span class="sxs-lookup"><span data-stu-id="38a09-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="38a09-108">**若要將現有的索引移至不同的檔案群組，使用：**</span><span class="sxs-lookup"><span data-stu-id="38a09-108">**To move an existing index to a different filegroup, using:**</span></span>  
  
     [<span data-ttu-id="38a09-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="38a09-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="38a09-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="38a09-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="38a09-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="38a09-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="38a09-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="38a09-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="38a09-113">如果資料表含有叢集索引，則將叢集索引移到新的檔案群組也會使資料表移到該檔案群組中。</span><span class="sxs-lookup"><span data-stu-id="38a09-113">If a table has a clustered index, moving the clustered index to a new filegroup moves the table to that filegroup.</span></span>  
  
-   <span data-ttu-id="38a09-114">您無法使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]移動使用 UNIQUE 或 PRIMARY KEY 條件約束建立的索引。</span><span class="sxs-lookup"><span data-stu-id="38a09-114">You cannot move indexes created using a UNIQUE or PRIMARY KEY constraint using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="38a09-115">若要移動這些索引，請使用 [中的](/sql/t-sql/statements/create-index-transact-sql) CREATE INDEX [!INCLUDE[tsql](../../includes/tsql-md.md)]陳述式搭配 (DROP_EXISTING=ON) 選項。</span><span class="sxs-lookup"><span data-stu-id="38a09-115">To move these indexes use the [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) statement with the (DROP_EXISTING=ON) option in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="38a09-116">Security</span><span class="sxs-lookup"><span data-stu-id="38a09-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="38a09-117">權限</span><span class="sxs-lookup"><span data-stu-id="38a09-117">Permissions</span></span>  
 <span data-ttu-id="38a09-118">需要資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="38a09-118">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="38a09-119">使用者必須是 **系統管理員** 固定伺服器角色的成員，或是 **db_ddladmin** 和 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="38a09-119">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="38a09-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="38a09-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-move-an-existing-index-to-a-different-filegroup-using-table-designer"></a><span data-ttu-id="38a09-121">若要使用資料表設計工具將現有的索引移至不同的檔案群組</span><span class="sxs-lookup"><span data-stu-id="38a09-121">To move an existing index to a different filegroup using Table Designer</span></span>  
  
1.  <span data-ttu-id="38a09-122">在 [物件總管] 中，按一下加號展開資料庫，此資料庫包含的資料表中有您要移動的索引。</span><span class="sxs-lookup"><span data-stu-id="38a09-122">In Object Explorer, click the plus sign to expand the database that contains the table containing the index that you want to move.</span></span>  
  
2.  <span data-ttu-id="38a09-123">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="38a09-123">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="38a09-124">以滑鼠右鍵按一下包含您要移動之索引的資料表，然後選取 [設計]  。</span><span class="sxs-lookup"><span data-stu-id="38a09-124">Right-click the table containing the index that you want to move and select **Design**.</span></span>  
  
4.  <span data-ttu-id="38a09-125">在 [資料表設計工具]  功能表上，按一下 [索引/索引鍵]  。</span><span class="sxs-lookup"><span data-stu-id="38a09-125">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="38a09-126">選取您要移動的索引。</span><span class="sxs-lookup"><span data-stu-id="38a09-126">Select the index that you want to move.</span></span>  
  
6.  <span data-ttu-id="38a09-127">在主要方格中，展開 **[資料空間規格]** 。</span><span class="sxs-lookup"><span data-stu-id="38a09-127">In the main grid, expand **Data Space Specification**.</span></span>  
  
7.  <span data-ttu-id="38a09-128">選取 **[檔案群組或分割區配置名稱]** ，然後從清單中選取要將索引移至其中的檔案群組或分割區配置。</span><span class="sxs-lookup"><span data-stu-id="38a09-128">Select **Filegroup or Partition Scheme Name** and select from the list the filegroup or partition scheme to where you want to move the index.</span></span>  
  
8.  <span data-ttu-id="38a09-129">按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="38a09-129">Click **Close**.</span></span>  
  
9. <span data-ttu-id="38a09-130">在 [檔案] 功能表上，選取 [儲存 _table_name_]。</span><span class="sxs-lookup"><span data-stu-id="38a09-130">On the **File** menu, select **Save**_table_name_.</span></span>  
  
#### <a name="to-move-an-existing-index-to-a-different-filegroup-in-object-explorer"></a><span data-ttu-id="38a09-131">若要在物件總管中將現有的索引移到不同的檔案群組</span><span class="sxs-lookup"><span data-stu-id="38a09-131">To move an existing index to a different filegroup in Object Explorer</span></span>  
  
1.  <span data-ttu-id="38a09-132">在 [物件總管] 中，按一下加號展開資料庫，此資料庫包含的資料表中有您要移動的索引。</span><span class="sxs-lookup"><span data-stu-id="38a09-132">In Object Explorer, click the plus sign to expand the database that contains the table containing the index that you want to move.</span></span>  
  
2.  <span data-ttu-id="38a09-133">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="38a09-133">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="38a09-134">按一下加號，展開包含您要移動之索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="38a09-134">Click the plus sign to expand the table containing the index that you want to move.</span></span>  
  
4.  <span data-ttu-id="38a09-135">按一下加號展開 **[索引]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="38a09-135">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="38a09-136">以滑鼠右鍵按一下您要移動的索引，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="38a09-136">Right-click the index that you want to move and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="38a09-137">在 **[選取頁面]** 底下，選取 **[儲存體]** 。</span><span class="sxs-lookup"><span data-stu-id="38a09-137">Under **Select a page**, select **Storage**.</span></span>  
  
7.  <span data-ttu-id="38a09-138">選取要移動索引的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="38a09-138">Select the filegroup in which to move the index.</span></span>  
  
     <span data-ttu-id="38a09-139">如果資料表或索引已分割，請選取移動索引所使用的分割區配置。</span><span class="sxs-lookup"><span data-stu-id="38a09-139">If the table or index is partitioned, select the partition scheme in which to move the index.</span></span> <span data-ttu-id="38a09-140">如需有關分割區索引的詳細資訊，請參閱＜ [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="38a09-140">For more information about partitioned indexes, see [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).</span></span>  
  
     <span data-ttu-id="38a09-141">如果您要移動叢集索引，可使用線上處理。</span><span class="sxs-lookup"><span data-stu-id="38a09-141">If you are moving a clustered index, you can use online processing.</span></span> <span data-ttu-id="38a09-142">線上處理允許並行使用者在索引作業期間，存取基礎資料和非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="38a09-142">Online processing allows concurrent user access to the underlying data and to nonclustered indexes during the index operation.</span></span> <span data-ttu-id="38a09-143">如需詳細資訊，請參閱 [Perform Index Operations Online](perform-index-operations-online.md)。</span><span class="sxs-lookup"><span data-stu-id="38a09-143">For more information, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
     <span data-ttu-id="38a09-144">在使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的多處理器電腦上，您可以指定平行處理原則的最大程度值，藉以設定用來執行索引陳述式的處理器數目。</span><span class="sxs-lookup"><span data-stu-id="38a09-144">On multiprocessor computers using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can configure the number of processors used to execute the index statement by specifying a maximum degree of parallelism value.</span></span> <span data-ttu-id="38a09-145">並非每個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]版本都可使用平行索引作業功能。</span><span class="sxs-lookup"><span data-stu-id="38a09-145">The Parallel indexed operations feature is not available in every edition of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="38a09-146">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="38a09-146">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="38a09-147">如需平行索引作業的詳細資訊，請參閱 [設定平行索引作業](configure-parallel-index-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="38a09-147">For more information about Parallel indexed operations, see [Configure Parallel Index Operations](configure-parallel-index-operations.md).</span></span>  
  
8.  <span data-ttu-id="38a09-148">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="38a09-148">Click **OK**.</span></span>  
  
 <span data-ttu-id="38a09-149">下列資訊可從 [索引屬性 - **index_name**]  對話方塊的 [儲存體]  頁面取得：</span><span class="sxs-lookup"><span data-stu-id="38a09-149">The following information is available on the **Storage** page of the **Index Properties -** _index_name_ dialog box:</span></span>  
  
 <span data-ttu-id="38a09-150">**檔案群組**</span><span class="sxs-lookup"><span data-stu-id="38a09-150">**Filegroup**</span></span>  
 <span data-ttu-id="38a09-151">在指定的檔案群組中儲存索引。</span><span class="sxs-lookup"><span data-stu-id="38a09-151">Stores the index in the specified filegroup.</span></span> <span data-ttu-id="38a09-152">清單僅顯示標準 (資料列) 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="38a09-152">The list only displays standard (row) filegroups.</span></span> <span data-ttu-id="38a09-153">預設清單選取項目為資料庫的 PRIMARY 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="38a09-153">The default list selection is the PRIMARY filegroup of the database.</span></span>  
  
 <span data-ttu-id="38a09-154">**檔案資料流檔案群組**</span><span class="sxs-lookup"><span data-stu-id="38a09-154">**Filestream filegroup**</span></span>  
 <span data-ttu-id="38a09-155">為 FILESTREAM 資料指定檔案群組。</span><span class="sxs-lookup"><span data-stu-id="38a09-155">Specifies the filegroup for FILESTREAM data.</span></span> <span data-ttu-id="38a09-156">此清單只會顯示 FILESTREAM 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="38a09-156">This list displays only FILESTREAM filegroups.</span></span> <span data-ttu-id="38a09-157">預設清單選取項目為資料庫的 PRIMARY FILESTREAM 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="38a09-157">The default list selection is the PRIMARY FILESTREAM filegroup.</span></span>  
  
 <span data-ttu-id="38a09-158">**分割區配置**</span><span class="sxs-lookup"><span data-stu-id="38a09-158">**Partition scheme**</span></span>  
 <span data-ttu-id="38a09-159">在資料分割結構描述中儲存索引。</span><span class="sxs-lookup"><span data-stu-id="38a09-159">Stores the index in a partition scheme.</span></span> <span data-ttu-id="38a09-160">按一下 **[資料分割配置]** 以啟用下列方格。</span><span class="sxs-lookup"><span data-stu-id="38a09-160">Clicking **Partition Scheme** enables the grid below.</span></span> <span data-ttu-id="38a09-161">預設清單選取項目是用來儲存資料表資料的資料分割配置。</span><span class="sxs-lookup"><span data-stu-id="38a09-161">The default list selection is the partition scheme that is used for storing the table data.</span></span> <span data-ttu-id="38a09-162">當您在清單中選取不同的資料分割配置時，會更新方格中的資訊。</span><span class="sxs-lookup"><span data-stu-id="38a09-162">When you select a different partition scheme in the list, the information in the grid is updated.</span></span>  
  
 <span data-ttu-id="38a09-163">如果資料庫中沒有資料分割結構描述，則無法使用資料分割結構描述選項。</span><span class="sxs-lookup"><span data-stu-id="38a09-163">The partition scheme option is unavailable if there are no partition schemes in the database.</span></span>  
  
 <span data-ttu-id="38a09-164">**檔案資料流資料分割配置**</span><span class="sxs-lookup"><span data-stu-id="38a09-164">**Filestream partition scheme**</span></span>  
 <span data-ttu-id="38a09-165">指定資料分割配置的 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="38a09-165">Specifies the partition scheme for FILESTREAM data.</span></span> <span data-ttu-id="38a09-166">資料分割配置必須對稱於在 **[資料分割配置]** 選項中所指定的配置。</span><span class="sxs-lookup"><span data-stu-id="38a09-166">The partition scheme must be symmetric with the scheme that is specified in the **Partition scheme** option.</span></span>  
  
 <span data-ttu-id="38a09-167">如果資料表不是資料分割，則此欄位空白。</span><span class="sxs-lookup"><span data-stu-id="38a09-167">If the table is not partitioned, the field is blank.</span></span>  
  
 <span data-ttu-id="38a09-168">**資料分割結構描述參數**</span><span class="sxs-lookup"><span data-stu-id="38a09-168">**Partition Scheme Parameter**</span></span>  
 <span data-ttu-id="38a09-169">顯示參與資料分割結構描述的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="38a09-169">Displays the name of the column that participates in the partition scheme.</span></span>  
  
 <span data-ttu-id="38a09-170">**資料表資料行**</span><span class="sxs-lookup"><span data-stu-id="38a09-170">**Table Column**</span></span>  
 <span data-ttu-id="38a09-171">選取資料表或檢視以對應至資料分割結構描述。</span><span class="sxs-lookup"><span data-stu-id="38a09-171">Select the table or view to map to the partition scheme.</span></span>  
  
 <span data-ttu-id="38a09-172">**資料行資料類型**</span><span class="sxs-lookup"><span data-stu-id="38a09-172">**Column Data Type**</span></span>  
 <span data-ttu-id="38a09-173">顯示有關資料行的資料類型資訊。</span><span class="sxs-lookup"><span data-stu-id="38a09-173">Displays data type information about the column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38a09-174">如果資料表資料行是計算資料行， **[資料行資料類型]** 就會顯示「計算資料行」。</span><span class="sxs-lookup"><span data-stu-id="38a09-174">If the table column is a computed column, **Column Data Type** displays "computed column."</span></span>  
  
 <span data-ttu-id="38a09-175">**移動索引時，允許線上處理 DML 陳述式**</span><span class="sxs-lookup"><span data-stu-id="38a09-175">**Allow online processing of DML statements while moving the index**</span></span>  
 <span data-ttu-id="38a09-176">允許使用者在索引作業期間存取基礎資料表或叢集索引資料，以及與非叢集索引相關聯的任何項目。</span><span class="sxs-lookup"><span data-stu-id="38a09-176">Allows users to access the underlying table or clustered index data and any associated nonclustered indexes during the index operation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38a09-177">此選項不適用於 XML 索引，或索引為已停用的叢集索引時亦不適用。</span><span class="sxs-lookup"><span data-stu-id="38a09-177">This option is not available for XML indexes, or if the index is a disabled clustered index.</span></span>  
  
 <span data-ttu-id="38a09-178">**設定最大平行程度**</span><span class="sxs-lookup"><span data-stu-id="38a09-178">**Set maximum degree of parallelism**</span></span>  
 <span data-ttu-id="38a09-179">限制平行計畫執行期間要使用的處理器數目。</span><span class="sxs-lookup"><span data-stu-id="38a09-179">Limits the number of processors to use during parallel plan execution.</span></span> <span data-ttu-id="38a09-180">預設值 (0) 會使用實際可用的 CPU 數目。</span><span class="sxs-lookup"><span data-stu-id="38a09-180">The default value, 0, uses the actual number of available CPUs.</span></span> <span data-ttu-id="38a09-181">將值設定為 1 會抑制平行計畫的產生；將值設定為大於 1 的數字則會限制單一查詢執行所使用的處理器最大數目。</span><span class="sxs-lookup"><span data-stu-id="38a09-181">Setting the value to 1 suppresses parallel plan generation; setting the value to a number greater than 1 restricts the maximum number of processors used by a single query execution.</span></span> <span data-ttu-id="38a09-182">此選項僅會在對話方塊處於 **[重建]** 或 **[重新建立]** 狀態時可用。</span><span class="sxs-lookup"><span data-stu-id="38a09-182">This option only becomes available if the dialog box is in the **Rebuild** or **Recreate** state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38a09-183">如果指定的數值大於可用的 CPU 數目，就會使用可用 CPU 的實際數目。</span><span class="sxs-lookup"><span data-stu-id="38a09-183">If a value greater than the number of available CPUs is specified, the actual number of available CPUs is used.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="38a09-184">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="38a09-184">Using Transact-SQL</span></span>  
  
#### <a name="to-move-an-existing-index-to-a-different-filegroup"></a><span data-ttu-id="38a09-185">若要將現有的索引移至不同的檔案群組</span><span class="sxs-lookup"><span data-stu-id="38a09-185">To move an existing index to a different filegroup</span></span>  
  
1.  <span data-ttu-id="38a09-186">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="38a09-186">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="38a09-187">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="38a09-187">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="38a09-188">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="38a09-188">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Creates the TransactionsFG1 filegroup on the AdventureWorks2012 database  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP TransactionsFG1;  
    GO  
    /* Adds the TransactionsFG1dat3 file to the TransactionsFG1 filegroup. Please note that you will have to change the filename parameter in this statement to execute it without errors.  
    */  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = TransactionsFG1dat3,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\TransactionsFG1dat3.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP TransactionsFG1;  
    GO  
    /*Creates the IX_Employee_OrganizationLevel_OrganizationNode index  
      on the TransactionsPS1 filegroup and drops the original IX_Employee_OrganizationLevel_OrganizationNode index.  
    */  
    CREATE NONCLUSTERED INDEX IX_Employee_OrganizationLevel_OrganizationNode  
        ON HumanResources.Employee (OrganizationLevel, OrganizationNode)  
        WITH (DROP_EXISTING = ON)  
        ON TransactionsFG1;  
    GO  
    ```  
  
 <span data-ttu-id="38a09-189">如需詳細資訊，請參閱 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="38a09-189">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
