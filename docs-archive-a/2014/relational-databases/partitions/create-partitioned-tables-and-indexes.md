---
title: 建立資料分割資料表及索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.createpartition.partitionscheme.f1
- sql12.swb.createpartition.selectoutput.f1
- sql12.swb.createpartition.finish.f1
- sql12.swb.createpartition.summary.f1
- sql12.swb.createpartition.mappartition.f1
- sql12.swb.createpartition.partitioncolumn.f1
- sql12.swb.createpartition.progress.f1
- sql12.swb.createpartition.createjob.f1
- sql12.swb.createpartition.getstart.f1
- sql12.swb.createpartition.partitionfunction.f1
helpviewer_keywords:
- partitioned indexes [SQL Server], creating
- partition schemes [SQL Server], creating
- partition functions [SQL Server], creating
- partitioned tables [SQL Server], creating
- partition functions [SQL Server]
- partition schemes [SQL Server]
ms.assetid: 7641df10-1921-42a7-ba6e-4cb03b3ba9c8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 76ccd8b784902f8542f06f3823e5f8dcb78e9201
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594509"
---
# <a name="create-partitioned-tables-and-indexes"></a><span data-ttu-id="795b6-102">建立分割區資料表及索引</span><span class="sxs-lookup"><span data-stu-id="795b6-102">Create Partitioned Tables and Indexes</span></span>
  <span data-ttu-id="795b6-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立分割區資料表或索引。</span><span class="sxs-lookup"><span data-stu-id="795b6-103">You can create a partitioned table or index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="795b6-104">分割區資料表及索引中的資料會被水平分割成單元，可散佈在資料庫中的多個檔案群組中。</span><span class="sxs-lookup"><span data-stu-id="795b6-104">The data in partitioned tables and indexes is horizontally divided into units that can be spread across more than one filegroup in a database.</span></span> <span data-ttu-id="795b6-105">分割作業可讓大型資料表和索引更容易管理及擴充。</span><span class="sxs-lookup"><span data-stu-id="795b6-105">Partitioning can make large tables and indexes more manageable and scalable.</span></span>  
  
 <span data-ttu-id="795b6-106">分割區資料表或索引的建立過程通常分為四個部分：</span><span class="sxs-lookup"><span data-stu-id="795b6-106">Creating a partitioned table or index typically happens in four parts:</span></span>  
  
1.  <span data-ttu-id="795b6-107">建立一個或多個檔案群組和對應的檔案，它們將存放分割區配置所指定的分割區。</span><span class="sxs-lookup"><span data-stu-id="795b6-107">Create a filegroup or filegroups and corresponding files that will hold the partitions specified by the partition scheme.</span></span>  
  
2.  <span data-ttu-id="795b6-108">建立分割區函數，此函數根據指定之資料行的各個值，將資料表或索引的資料列對應到分割區中。</span><span class="sxs-lookup"><span data-stu-id="795b6-108">Create a partition function that maps the rows of a table or index into partitions based on the values of a specified column.</span></span>  
  
3.  <span data-ttu-id="795b6-109">建立分割區配置，將分割區資料表或索引的分割區，對應至新的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="795b6-109">Create a partition scheme that maps the partitions of a partitioned table or index to the new filegroups.</span></span>  
  
4.  <span data-ttu-id="795b6-110">建立或修改資料表或索引，以及指定分割區配置做為儲存位置。</span><span class="sxs-lookup"><span data-stu-id="795b6-110">Create or modify a table or index and specify the partition scheme as the storage location.</span></span>  
  
 <span data-ttu-id="795b6-111">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="795b6-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="795b6-112">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="795b6-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="795b6-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="795b6-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="795b6-114">安全性</span><span class="sxs-lookup"><span data-stu-id="795b6-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="795b6-115">**使用下列方法建立分割區資料表或索引：**</span><span class="sxs-lookup"><span data-stu-id="795b6-115">**To create a partitioned table or index, using:**</span></span>  
  
     [<span data-ttu-id="795b6-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="795b6-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="795b6-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="795b6-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="795b6-118">開始之前</span><span class="sxs-lookup"><span data-stu-id="795b6-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="795b6-119">限制事項</span><span class="sxs-lookup"><span data-stu-id="795b6-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="795b6-120">分割區函數和配置的範圍只限於它們建立所在的資料庫。</span><span class="sxs-lookup"><span data-stu-id="795b6-120">The scope of a partition function and scheme is limited to the database in which they have been created.</span></span> <span data-ttu-id="795b6-121">在這個資料庫內，分割區函數是在不同於其他函數的個別命名空間中。</span><span class="sxs-lookup"><span data-stu-id="795b6-121">Within the database, partition functions reside in a separate namespace from other functions.</span></span>  
  
-   <span data-ttu-id="795b6-122">如果分割區函數內的任何資料列含有 Null 值的分割資料行，這些資料列都會配置到最左邊的分割區。</span><span class="sxs-lookup"><span data-stu-id="795b6-122">If any rows within a partition function have partitioning columns with null values, these rows are allocated to the left-most partition.</span></span> <span data-ttu-id="795b6-123">不過，如果將 NULL 指定為界限值且指示 RIGHT，最左邊的分割區會保持空白，而且 NULL 值會放在第二個分割區。</span><span class="sxs-lookup"><span data-stu-id="795b6-123">However, if NULL is specified as a boundary value and RIGHT is indicated, the left-most partition remains empty and NULL values are placed in the second partition.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="795b6-124">Security</span><span class="sxs-lookup"><span data-stu-id="795b6-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="795b6-125">權限</span><span class="sxs-lookup"><span data-stu-id="795b6-125">Permissions</span></span>  
 <span data-ttu-id="795b6-126">建立分割區資料表，需要資料庫中的 CREATE TABLE 權限及建立資料表的結構描述之 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="795b6-126">Creating a partitioned table requires CREATE TABLE permission in the database and ALTER permission on the schema in which the table is being created.</span></span> <span data-ttu-id="795b6-127">建立分割區索引，需要建立索引的資料表或檢視的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="795b6-127">Creating a partitioned index requires ALTER permission on the table or view where the index is being created.</span></span> <span data-ttu-id="795b6-128">建立分割區資料表或索引，還需要下列任何一個附加權限：</span><span class="sxs-lookup"><span data-stu-id="795b6-128">Creating either a partitioned table or index requires any one of the following additional permissions:</span></span>  
  
-   <span data-ttu-id="795b6-129">ALTER ANY DATASPACE 權限。</span><span class="sxs-lookup"><span data-stu-id="795b6-129">ALTER ANY DATASPACE permission.</span></span> <span data-ttu-id="795b6-130">這個權限預設會授與 **sysadmin** 固定伺服器角色以及 **db_owner** 和 **db_ddladmin** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="795b6-130">This permission defaults to members of the **sysadmin** fixed server role and the **db_owner** and **db_ddladmin** fixed database roles.</span></span>  
  
-   <span data-ttu-id="795b6-131">建立分割區函數和分割區配置之資料庫的 CONTROL 或 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="795b6-131">CONTROL or ALTER permission on the database in which the partition function and partition scheme are being created.</span></span>  
  
-   <span data-ttu-id="795b6-132">建立分割區函數和分割區配置之資料庫伺服器的 CONTROL SERVER 或 ALTER ANY DATABASE 權限。</span><span class="sxs-lookup"><span data-stu-id="795b6-132">CONTROL SERVER or ALTER ANY DATABASE permission on the server of the database in which the partition function and partition scheme are being created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="795b6-133">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="795b6-133">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="795b6-134">請遵循此程序中的步驟，建立一個或多個檔案群組、對應檔案和資料表。</span><span class="sxs-lookup"><span data-stu-id="795b6-134">Follow the steps in this procedure to create one or more filegroups, corresponding files, and a table.</span></span> <span data-ttu-id="795b6-135">在下一個程序中建立分割區資料表時，您將會參考這些物件。</span><span class="sxs-lookup"><span data-stu-id="795b6-135">You will reference these objects in the next procedure when you create the partitioned table.</span></span>  
  
#### <a name="to-create-new-filegroups-for-a-partitioned-table"></a><span data-ttu-id="795b6-136">為分割區資料表建立新的檔案群組</span><span class="sxs-lookup"><span data-stu-id="795b6-136">To create new filegroups for a partitioned table</span></span>  
  
1.  <span data-ttu-id="795b6-137">在物件總管中，以滑鼠右鍵按一下要建立分割區資料表的資料庫，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="795b6-137">In Object Explorer, right-click the database in which you want to create a partitioned table and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="795b6-138">在 [資料庫屬性 - **database_name**]  對話方塊的 [選取頁面]  底下，選取 [檔案群組]  。</span><span class="sxs-lookup"><span data-stu-id="795b6-138">In the **Database Properties -** *database_name* dialog box, under **Select a page**, select **Filegroups**.</span></span>  
  
3.  <span data-ttu-id="795b6-139">按一下 **[資料列]** 底下的 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-139">Under **Rows**, click **Add**.</span></span> <span data-ttu-id="795b6-140">在新資料列中，輸入檔案群組名稱。</span><span class="sxs-lookup"><span data-stu-id="795b6-140">In the new row, enter the filegroup name.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="795b6-141">建立分割區時，除了針對界限值指定的檔案群組數目以外，一定要有一個額外的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="795b6-141">You must always have one extra filegroup in addition to the number of filegroups specified for the boundary values when you are creating partitions.</span></span>  
  
4.  <span data-ttu-id="795b6-142">繼續加入資料列，直到為分割區資料表建立所有的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="795b6-142">Continue adding rows until you have created all of the filegroups for the partitioned table.</span></span>  
  
5.  <span data-ttu-id="795b6-143">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="795b6-143">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="795b6-144">在 **[選取頁面]** 底下，選取 **[檔案]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-144">Under **Select a page**, select **Files**.</span></span>  
  
7.  <span data-ttu-id="795b6-145">按一下 **[資料列]** 底下的 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-145">Under **Rows**, click **Add**.</span></span> <span data-ttu-id="795b6-146">在新資料列中，輸入檔案名稱並選取檔案群組。</span><span class="sxs-lookup"><span data-stu-id="795b6-146">In the new row, enter a filename and select a filegroup.</span></span>  
  
8.  <span data-ttu-id="795b6-147">繼續加入資料列，直到為每個檔案群組建立至少一個檔案。</span><span class="sxs-lookup"><span data-stu-id="795b6-147">Continue adding rows until you have created at least one file for each filegroup.</span></span>  
  
9. <span data-ttu-id="795b6-148">展開 **[資料表]** 資料夾，像平常一樣地建立資料表。</span><span class="sxs-lookup"><span data-stu-id="795b6-148">Expand the **Tables** folder and create a table as you normally would.</span></span> <span data-ttu-id="795b6-149">如需詳細資訊，請參閱[建立資料表 &#40;Database Engine&#41;](../tables/create-tables-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="795b6-149">For more information, see [Create Tables &#40;Database Engine&#41;](../tables/create-tables-database-engine.md).</span></span> <span data-ttu-id="795b6-150">或者，您可以在下個程序中指定現有的資料表。</span><span class="sxs-lookup"><span data-stu-id="795b6-150">Alternatively, you can specify an existing table in the next procedure.</span></span>  
  
#### <a name="to-create-a-partitioned-table"></a><span data-ttu-id="795b6-151">建立分割區資料表</span><span class="sxs-lookup"><span data-stu-id="795b6-151">To create a partitioned table</span></span>  
  
1.  <span data-ttu-id="795b6-152">以滑鼠右鍵按一下要分割的資料表，指向 [儲存體]  ，然後按一下 [建立分割區...]  。</span><span class="sxs-lookup"><span data-stu-id="795b6-152">Right-click the table that you wish to partition, point to **Storage**, and then click **Create Partition...**.</span></span>  
  
2.  <span data-ttu-id="795b6-153">在 **[建立分割區精靈]** 的 **[歡迎使用建立分割區精靈]** 頁面上，按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-153">In the **Create Partition Wizard**, on the **Welcome to the Create Partition Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="795b6-154">在 **[選取分割資料行]** 頁面的 **[可用的分割資料行]** 方格中，選取要用來分割資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="795b6-154">On the **Select a Partitioning Column** page, in the **Available partitioning columns** grid, select the column on which you want to partition your table.</span></span> <span data-ttu-id="795b6-155">只有包含可用來分割資料之資料類型的資料行才會顯示在 **[可用的分割資料行]** 方格中。</span><span class="sxs-lookup"><span data-stu-id="795b6-155">Only columns with data types that can be used to partition data will be displayed in the **Available partitioning columns** grid.</span></span> <span data-ttu-id="795b6-156">如果您選取了某個計算資料行當做分割資料行，就必須將此資料行指定為保存的資料行。</span><span class="sxs-lookup"><span data-stu-id="795b6-156">If you select a computed column as the partitioning column, the column must be designated as a persisted column.</span></span>  
  
     <span data-ttu-id="795b6-157">您對分割資料行和值範圍擁有的選擇主要是由資料可以按邏輯方式分組到什麼程度所決定。</span><span class="sxs-lookup"><span data-stu-id="795b6-157">The choices you have for the partitioning column and the values range are determined primarily by the extent to which your data can be grouped in a logical way.</span></span> <span data-ttu-id="795b6-158">例如，您可能會選擇依據每年的月份或季度，將資料分成邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="795b6-158">For example, you may choose to divide your data into logical groupings by months or quarters of a year.</span></span> <span data-ttu-id="795b6-159">您打算針對資料進行的查詢將會決定這個邏輯群組是否足夠用於管理資料表分割區。</span><span class="sxs-lookup"><span data-stu-id="795b6-159">The queries you plan to make against your data will determine whether this logical grouping is adequate for managing your table partitions.</span></span> <span data-ttu-id="795b6-160">除了 `text`、`ntext`、`image`、`xml`、`timestamp`、`varchar(max)`、`nvarchar(max)`、`varbinary(max)`、別名資料類型或 CLR 使用者自訂資料類型，所有資料類型都能有效用在資料分割資料行上。</span><span class="sxs-lookup"><span data-stu-id="795b6-160">All data types are valid for use as partitioning columns, except `text`, `ntext`, `image`, `xml`, `timestamp`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, alias data types, or CLR user-defined data types.</span></span>  
  
     <span data-ttu-id="795b6-161">在此頁面上可以使用下列其他選項：</span><span class="sxs-lookup"><span data-stu-id="795b6-161">The following additional options are available on this page:</span></span>  
  
     <span data-ttu-id="795b6-162">**共置此資料表至選取的分割區資料表**</span><span class="sxs-lookup"><span data-stu-id="795b6-162">**Collocate this table to the selected partitioned table**</span></span>  
     <span data-ttu-id="795b6-163">可讓您選取分割區資料表，其中包含要在此分割資料行上與這個資料表聯結的相關資料。</span><span class="sxs-lookup"><span data-stu-id="795b6-163">Allows you to select a partitioned table that contains related data to join with this table on the partitioning column.</span></span> <span data-ttu-id="795b6-164">在分割資料行上聯結分割區的資料表通常會讓查詢更有效率。</span><span class="sxs-lookup"><span data-stu-id="795b6-164">Tables with partitions joined on the partitioning columns are typically queried more efficiently.</span></span>  
  
     <span data-ttu-id="795b6-165">**使用索引的分割區資料行讓非唯一索引和唯一索引進行儲存體對齊**</span><span class="sxs-lookup"><span data-stu-id="795b6-165">**Storage-align non-unique indexes and unique indexes with an indexed partition column**</span></span>  
     <span data-ttu-id="795b6-166">讓使用相同分割區配置進行分割區的所有資料表索引對齊。</span><span class="sxs-lookup"><span data-stu-id="795b6-166">Aligns all indexes of the table that are partitioned with the same partition scheme.</span></span> <span data-ttu-id="795b6-167">當資料表及其索引對齊時，您就可以更有效率地將分割區移入和移出分割區資料表，因為資料是使用相同的演算法進行分割區。</span><span class="sxs-lookup"><span data-stu-id="795b6-167">When a table and its indexes are aligned, you can move partitions in and out of partitioned tables more effectively, because your data is partitioned with the same algorithm.</span></span>  
  
     <span data-ttu-id="795b6-168">選取分割資料行和任何其他選項之後，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-168">After selecting the partitioning column and any other options, click **Next**.</span></span>  
  
4.  <span data-ttu-id="795b6-169">在 **[選取分割區函數]** 頁面，按一下 **[選取分割區函數]** 底下的 **[新的分割區函數]** 或 **[現有的分割區函數]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-169">On the **Select a Partition Function** page, under **Select partition function**, click either **New partition function** or **Existing partition function**.</span></span> <span data-ttu-id="795b6-170">如果您選擇 **[新的分割區函數]** ，請輸入函數的名稱。</span><span class="sxs-lookup"><span data-stu-id="795b6-170">If you choose **New partition function**, enter the name of the function.</span></span> <span data-ttu-id="795b6-171">如果您選擇 [現有的分割區函數]  ，請從清單中選取要使用的函數名稱。</span><span class="sxs-lookup"><span data-stu-id="795b6-171">If you choose **Existing partition function**, select the name of the function you'd like to use from the list.</span></span> <span data-ttu-id="795b6-172">如果資料庫上沒有其他分割區函數， **[現有的分割區函數]** 選項就無法使用。</span><span class="sxs-lookup"><span data-stu-id="795b6-172">The **Existing partition function** option will not be available if there are no other partition functions on the database.</span></span>  
  
     <span data-ttu-id="795b6-173">完成這個頁面之後，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-173">After completing this page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="795b6-174">在 **[選取分割區配置]** 頁面，按一下 **[選取分割區配置]** 底下的 **[新的分割區配置]** 或 **[現有的分割區配置]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-174">On the **Select a Partition Scheme** page, under **Select partition scheme**, click either **New partition scheme** or **Existing partition scheme**.</span></span> <span data-ttu-id="795b6-175">如果您選擇 **[新的分割區配置]** ，請輸入配置的名稱。</span><span class="sxs-lookup"><span data-stu-id="795b6-175">If you choose **New partition scheme**, enter the name of the scheme.</span></span> <span data-ttu-id="795b6-176">如果您選擇 [現有的分割區配置]  ，請從清單中選取要使用的配置名稱。</span><span class="sxs-lookup"><span data-stu-id="795b6-176">If you choose **Existing partition scheme**, select the name of the scheme you'd like to use from the list.</span></span> <span data-ttu-id="795b6-177">如果資料庫上沒有其他分割區配置， **[現有的分割區配置]** 選項就無法使用。</span><span class="sxs-lookup"><span data-stu-id="795b6-177">The **Existing partition scheme** option will not be available if there are no other partition schemes on the database.</span></span>  
  
     <span data-ttu-id="795b6-178">完成這個頁面之後，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-178">After completing this page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="795b6-179">在 **[對應分割區]** 頁面上，選取 **[範圍]** 底下的 **[左界限]** 或 **[右界限]** ，指定要在建立的每個檔案群組中包含最高或最低的界限值。</span><span class="sxs-lookup"><span data-stu-id="795b6-179">On the **Map Partitions** page, under **Range**, select either **Left boundary** or **Right boundary** to specify whether to include the highest or lowest bounding value within each filegroup you create.</span></span> <span data-ttu-id="795b6-180">建立分割區時，除了針對界限值指定的檔案群組數目以外，您一定要輸入一個額外的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="795b6-180">You must always enter one extra filegroup in addition to the number of filegroups specified for the boundary values when you are creating partitions.</span></span>  
  
     <span data-ttu-id="795b6-181">在 **[選取檔案群組並指定界限值]** 方格中的 **[檔案群組]** 底下，選取要用於分割資料的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="795b6-181">In the **Select filegroups and specify boundary values** grid, under **Filegroup**, select the filegroup into which you want to partition your data.</span></span> <span data-ttu-id="795b6-182">在 **[界限]** 下方，輸入每個檔案群組的界限值。</span><span class="sxs-lookup"><span data-stu-id="795b6-182">Under **Boundary**, enter the boundary value for each filegroup.</span></span> <span data-ttu-id="795b6-183">如果界限值保持空白，分割區函數會使用分割區函數名稱，將整份資料表或索引對應到單一分割區。</span><span class="sxs-lookup"><span data-stu-id="795b6-183">If boundary value is left empty, the partition function maps the whole table or index into a single partition using the partition function name.</span></span>  
  
     <span data-ttu-id="795b6-184">在此頁面上可以使用下列其他選項：</span><span class="sxs-lookup"><span data-stu-id="795b6-184">The following additional options are available on this page:</span></span>  
  
     <span data-ttu-id="795b6-185">**設定界限…**</span><span class="sxs-lookup"><span data-stu-id="795b6-185">**Set Boundaries...**</span></span>  
     <span data-ttu-id="795b6-186">開啟 **[設定界限值]** 對話方塊，即可選取您想要用於分割區的界限值和日期範圍。</span><span class="sxs-lookup"><span data-stu-id="795b6-186">Opens the **Set Boundary Values** dialog box to select the boundary values and date ranges you want for your partitions.</span></span> <span data-ttu-id="795b6-187">只有當您選取了包含下列其中一個資料類型的分割資料行時，才能使用這個選項：`date`、`datetime`、`smalldatetime`、`datetime2` 或 `datetimeoffset`。</span><span class="sxs-lookup"><span data-stu-id="795b6-187">This option is only available when you have selected a partitioning column that contains one of the following data types: `date`, `datetime`, `smalldatetime`, `datetime2`, or `datetimeoffset`.</span></span>  
  
     <span data-ttu-id="795b6-188">**估計儲存體**</span><span class="sxs-lookup"><span data-stu-id="795b6-188">**Estimate storage**</span></span>  
     <span data-ttu-id="795b6-189">針對指定給分割區的每個檔案群組估計儲存體的列數、需要空間和可用空間。</span><span class="sxs-lookup"><span data-stu-id="795b6-189">Estimates rowcount, required space, and available space for storage for each filegroup specified for the partitions.</span></span> <span data-ttu-id="795b6-190">這些值都會在方格中顯示成唯讀值。</span><span class="sxs-lookup"><span data-stu-id="795b6-190">These values are displayed in the grid as read-only values.</span></span>  
  
     <span data-ttu-id="795b6-191">**[設定界限值]** 對話方塊允許下列其他選項：</span><span class="sxs-lookup"><span data-stu-id="795b6-191">The **Set Boundary Values** dialog box allows for the following additional options:</span></span>  
  
     <span data-ttu-id="795b6-192">**開始日期**</span><span class="sxs-lookup"><span data-stu-id="795b6-192">**Start date**</span></span>  
     <span data-ttu-id="795b6-193">針對分割區的範圍值選取開始日期。</span><span class="sxs-lookup"><span data-stu-id="795b6-193">Selects the starting date for the range values of your partitions.</span></span>  
  
     <span data-ttu-id="795b6-194">**結束日期**</span><span class="sxs-lookup"><span data-stu-id="795b6-194">**End date**</span></span>  
     <span data-ttu-id="795b6-195">針對分割區的範圍值選取結束日期。</span><span class="sxs-lookup"><span data-stu-id="795b6-195">Selects the ending date for the range values of your partitions.</span></span> <span data-ttu-id="795b6-196">如果您在 [對應分割區]  頁面上選取 [左界限]  ，這個日期就會成為每個檔案群組/分割區的最後一個值。</span><span class="sxs-lookup"><span data-stu-id="795b6-196">If you selected **Left boundary** on the **Map Partitions** page, this date will be the last value for each filegroup/partition.</span></span> <span data-ttu-id="795b6-197">如果您在 [對應分割區]  頁面上選取 [右界限]  ，這個日期就會成為倒數第二個檔案群組的第一個值。</span><span class="sxs-lookup"><span data-stu-id="795b6-197">If you selected **Right boundary** on the **Map Partitions** page, this date will be the first value in the next-to-last filegroup.</span></span>  
  
     <span data-ttu-id="795b6-198">**日期範圍**</span><span class="sxs-lookup"><span data-stu-id="795b6-198">**Date range**</span></span>  
     <span data-ttu-id="795b6-199">針對每個分割區選取您想要的日期資料粒度或範圍值遞增。</span><span class="sxs-lookup"><span data-stu-id="795b6-199">Selects the date granularity or range value increment you want for each partition.</span></span>  
  
     <span data-ttu-id="795b6-200">完成這個頁面之後，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-200">After completing this page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="795b6-201">在 **[選取輸出選項]** 頁面上，指定要如何完成分割區資料表。</span><span class="sxs-lookup"><span data-stu-id="795b6-201">In the **Select an Output Option** page, specify how you want to complete your partitioned table.</span></span> <span data-ttu-id="795b6-202">選取 **[建立指令碼]** ，根據精靈中先前的步驟建立 SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="795b6-202">Select **Create Script** to create a SQL script based the previous pages in the wizard.</span></span> <span data-ttu-id="795b6-203">選取 **[立即執行]** ，在完成精靈中的其餘所有頁面後建立新的分割區資料表。</span><span class="sxs-lookup"><span data-stu-id="795b6-203">Select **Run immediately** to create the new partitioned table after completing all remaining pages in the wizard.</span></span> <span data-ttu-id="795b6-204">選取 **[排程]** ，在預先定義的未來日期建立新的分割區資料表。</span><span class="sxs-lookup"><span data-stu-id="795b6-204">Select **Schedule** to create the new partitioned table at a predetermined time in the future.</span></span>  
  
     <span data-ttu-id="795b6-205">如果您選取 **[建立指令碼]** ，在 **[指令碼選項]** 底下可以使用下列選項：</span><span class="sxs-lookup"><span data-stu-id="795b6-205">If you select **Create script**, the following options are available under **Script options**:</span></span>  
  
     <span data-ttu-id="795b6-206">**編寫指令碼至檔案**</span><span class="sxs-lookup"><span data-stu-id="795b6-206">**Script to file**</span></span>  
     <span data-ttu-id="795b6-207">產生指令碼做為 .sql 檔案。</span><span class="sxs-lookup"><span data-stu-id="795b6-207">Generates the script as a .sql file.</span></span> <span data-ttu-id="795b6-208">在 **[檔案名稱]** 方塊中輸入檔案名稱和位置，或按一下 **[瀏覽]** 開啟 **[指令碼檔案位置]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="795b6-208">Enter a file name and location in the **File name** box or click **Browse** to open the **Script File Location** dialog box.</span></span> <span data-ttu-id="795b6-209">從 **[另存新檔]** ，選取 **[Unicode 文字]** 或 **[ANSI 文字]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-209">From **Save As**, select **Unicode text** or **ANSI text**.</span></span>  
  
     <span data-ttu-id="795b6-210">**編寫指令碼至剪貼簿**</span><span class="sxs-lookup"><span data-stu-id="795b6-210">**Script to Clipboard**</span></span>  
     <span data-ttu-id="795b6-211">將指令碼儲存至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="795b6-211">Saves the script to the Clipboard.</span></span>  
  
     <span data-ttu-id="795b6-212">**編寫指令碼至新增查詢視窗**</span><span class="sxs-lookup"><span data-stu-id="795b6-212">**Script to New Query Window**</span></span>  
     <span data-ttu-id="795b6-213">產生指令碼至新的 [查詢編輯器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="795b6-213">Generates the script to a new Query Editor window.</span></span> <span data-ttu-id="795b6-214">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="795b6-214">This is the default selection.</span></span>  
  
     <span data-ttu-id="795b6-215">如果您選取 **[排程]** ，請按一下 **[變更排程]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-215">If you select **Schedule**, click **Change schedule**.</span></span>  
  
    1.  <span data-ttu-id="795b6-216">在 [新增作業排程]  對話方塊的 [名稱]  方塊中，輸入作業排程的名稱。</span><span class="sxs-lookup"><span data-stu-id="795b6-216">In the **New Job Schedule** dialog box, in the **Name** box, enter the job schedule's name.</span></span>  
  
    2.  <span data-ttu-id="795b6-217">在 **[排程類型]** 清單，選取排程類型：</span><span class="sxs-lookup"><span data-stu-id="795b6-217">On the **Schedule type** list, select the type of schedule:</span></span>  
  
        -   <span data-ttu-id="795b6-218">**當 SQL Server Agent 啟動時自動啟動**</span><span class="sxs-lookup"><span data-stu-id="795b6-218">**Start automatically when SQL Server Agent starts**</span></span>  
  
        -   <span data-ttu-id="795b6-219">**只要 CPU 閒置就啟動**</span><span class="sxs-lookup"><span data-stu-id="795b6-219">**Start whenever the CPUs become idle**</span></span>  
  
        -   <span data-ttu-id="795b6-220">**重複執行**：</span><span class="sxs-lookup"><span data-stu-id="795b6-220">**Recurring**.</span></span> <span data-ttu-id="795b6-221">如果您的新分割區資料表會使用新資訊定期更新，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="795b6-221">Select this option if your new partitioned table updates with new information on a regular basis.</span></span>  
  
        -   <span data-ttu-id="795b6-222">**執行一次**：</span><span class="sxs-lookup"><span data-stu-id="795b6-222">**One time**.</span></span> <span data-ttu-id="795b6-223">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="795b6-223">This is the default selection.</span></span>  
  
    3.  <span data-ttu-id="795b6-224">選取或清除 **[已停用]** 核取方塊，以啟用或停用排程。</span><span class="sxs-lookup"><span data-stu-id="795b6-224">Select or clear the **Enabled** check box to enable or disable the schedule.</span></span>  
  
    4.  <span data-ttu-id="795b6-225">如果您選取 **[重複執行]** ：</span><span class="sxs-lookup"><span data-stu-id="795b6-225">If you select **Recurring**:</span></span>  
  
        1.  <span data-ttu-id="795b6-226">在 **[頻率]** 底下的 **[發生於]** 清單中，指定發生頻率：</span><span class="sxs-lookup"><span data-stu-id="795b6-226">Under **Frequency**, on the **Occurs** list, specify the frequency of occurrence:</span></span>  
  
            -   <span data-ttu-id="795b6-227">如果您選取 **[每天]** ，在 **[重複頻率]** 方塊中，輸入幾天重複一次作業排程的頻率。</span><span class="sxs-lookup"><span data-stu-id="795b6-227">If you select **Daily**, in the **Recurs every** box, enter how often the job schedule repeats in days.</span></span>  
  
            -   <span data-ttu-id="795b6-228">如果您選取 **[每週]** ，在 **[重複頻率]** 方塊中，輸入幾週重複一次作業排程的頻率。</span><span class="sxs-lookup"><span data-stu-id="795b6-228">If you select **Weekly**, in the **Recurs every** box, enter how often the job schedule repeats in weeks.</span></span> <span data-ttu-id="795b6-229">選取一週中執行作業排程是在星期幾。</span><span class="sxs-lookup"><span data-stu-id="795b6-229">Select the day or days of the week on which the job schedule is run.</span></span>  
  
            -   <span data-ttu-id="795b6-230">如果您選取 **[每月]** ，可以選取 **[天]** 或 **[於]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-230">If you select **Monthly**, select either **Day** or **The**.</span></span>  
  
                -   <span data-ttu-id="795b6-231">如果您選取 **[天]** ，請輸入執行作業排程的當月日期以及幾個月重複一次作業排程的頻率。</span><span class="sxs-lookup"><span data-stu-id="795b6-231">If you select **Day**, enter both the date of the month you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="795b6-232">例如，若要在每兩個月的 15 日執行一次作業排程，請選取 [日]  ，然後在第一個方塊中輸入 "15"，並在第二個方塊中輸入 "2"。</span><span class="sxs-lookup"><span data-stu-id="795b6-232">For example, if you want the job schedule to run on the 15th day of the month every other month, select **Day** and enter "15" in the first box and "2" in the second box.</span></span> <span data-ttu-id="795b6-233">請注意，在第二個方塊中允許的最大數目是 "99"。</span><span class="sxs-lookup"><span data-stu-id="795b6-233">Please note that the largest number allowed in the second box is "99".</span></span>  
  
                -   <span data-ttu-id="795b6-234">如果您選取 **[於]** ，請選取執行作業排程的當月一週中特定的星期幾，以及幾個月重複一次作業排程的頻率。</span><span class="sxs-lookup"><span data-stu-id="795b6-234">If you select **The**, select the specific day of the week within the month that you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="795b6-235">例如，若要在每兩個月的最後一個工作日執行一次作業排程，請選取 [日]  ，然後從第一個清單中選取 [最後一個]  ，並從第二個清單中選取 [工作日]  ，然後在最後一個方塊中輸入 "2"。</span><span class="sxs-lookup"><span data-stu-id="795b6-235">For example, if you want the job schedule to run on the last weekday of the month every other month, select **Day**, select **last** from the first list and **weekday** from the second list, and then enter "2" in the last box.</span></span> <span data-ttu-id="795b6-236">您也可以在前兩個清單中選取 [第一個]  、[第二個]  、[第三個]  或 [第四個]  ，以及特定工作日 (例如星期日或星期三)。</span><span class="sxs-lookup"><span data-stu-id="795b6-236">You can also select **first**, **second**, **third**, or **fourth**, as well as specific weekdays (for example: Sunday or Wednesday) from the first two lists.</span></span> <span data-ttu-id="795b6-237">請注意，在最後一個方塊中允許的最大數目是 "99"。</span><span class="sxs-lookup"><span data-stu-id="795b6-237">Please note that the largest number allowed in the last box is "99".</span></span>  
  
        2.  <span data-ttu-id="795b6-238">在 **[每日頻率]** 底下，指定在執行作業排程當天重複作業排程的頻率：</span><span class="sxs-lookup"><span data-stu-id="795b6-238">Under **Daily frequency**, specify how often the job schedule repeats on the day the job schedule runs:</span></span>  
  
            -   <span data-ttu-id="795b6-239">如果您選取 **[執行一次於]** ，請在 **[執行一次於]** 方塊中輸入執行作業排程的當天特定時間。</span><span class="sxs-lookup"><span data-stu-id="795b6-239">If you select **Occurs once at**, enter the specific time of day when the job schedule should run in the **Occurs once at** box.</span></span> <span data-ttu-id="795b6-240">輸入時、分鐘和秒的時間，以及上午或下午。</span><span class="sxs-lookup"><span data-stu-id="795b6-240">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
            -   <span data-ttu-id="795b6-241">如果您選取 **[重複執行於每]** ，請在 **[頻率]** 底下指定在所選當天執行作業排程的頻率。</span><span class="sxs-lookup"><span data-stu-id="795b6-241">If you select **Occurs every**, specify how often the job schedule runs during the day chosen under **Frequency**.</span></span> <span data-ttu-id="795b6-242">例如，若要在執行作業排程的當天每 2 個小時重複一次作業排程，請選取 [發生間隔]  ，在第一個方塊中輸入 "2"，然後從清單中選取 [小時]  。</span><span class="sxs-lookup"><span data-stu-id="795b6-242">For example, if you want the job schedule to repeat every 2 hours during the day that the job schedule is run, select **Occurs every**, enter "2" in the first box, and then select **hour(s)** from the list.</span></span> <span data-ttu-id="795b6-243">您也可以從這個清單中選取 [分鐘]  和 [秒]  。</span><span class="sxs-lookup"><span data-stu-id="795b6-243">From this list you can also select **minute(s)** and **second(s)**.</span></span> <span data-ttu-id="795b6-244">請注意，在第一個方塊中允許的最大數目是 "100"。</span><span class="sxs-lookup"><span data-stu-id="795b6-244">Please note that the largest number allowed in the first box is "100".</span></span>  
  
                 <span data-ttu-id="795b6-245">在 **[開始時間]** 方塊中，輸入作業排程應該開始執行的時間。</span><span class="sxs-lookup"><span data-stu-id="795b6-245">In the **Starting at** box, enter the time that the job schedule should start running.</span></span> <span data-ttu-id="795b6-246">在 **[結束時間]** 方塊中，輸入作業排程應該停止重複的時間。</span><span class="sxs-lookup"><span data-stu-id="795b6-246">In the **Ending at** box, enter the time that the job schedule should stop repeating.</span></span> <span data-ttu-id="795b6-247">輸入時、分鐘和秒的時間，以及上午或下午。</span><span class="sxs-lookup"><span data-stu-id="795b6-247">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
        3.  <span data-ttu-id="795b6-248">在 **[持續時間]** 底下的 **[開始日期]** ，輸入您希望作業排程開始執行的日期。</span><span class="sxs-lookup"><span data-stu-id="795b6-248">Under **Duration**, in **Start date**, enter the date that you want the job schedule to start running.</span></span> <span data-ttu-id="795b6-249">選取 **[結束日期]** 或 **[沒有結束日期]** ，以指示作業排程應該停止執行的日期。</span><span class="sxs-lookup"><span data-stu-id="795b6-249">Select **End date** or **No end date** to indicate when the job schedule should stop running.</span></span> <span data-ttu-id="795b6-250">如果您選取 **[結束日期]** ，請輸入您希望作業排程停止執行的日期。</span><span class="sxs-lookup"><span data-stu-id="795b6-250">If you select **End date**, enter the date that you want to job schedule to stop running.</span></span>  
  
    5.  <span data-ttu-id="795b6-251">如果您選取 [執行一次]  ，請在 [僅執行一次於]  底下的 [日期]  方塊中，輸入將要執行作業排程的日期。</span><span class="sxs-lookup"><span data-stu-id="795b6-251">If you select **One Time**, under **One-time occurrence**, in the **Date** box, enter the date that the job schedule will be run.</span></span> <span data-ttu-id="795b6-252">在 **[時間]** 方塊中，輸入將要執行作業排程的時間。</span><span class="sxs-lookup"><span data-stu-id="795b6-252">In the **Time** box, enter the time that the job schedule will be run.</span></span> <span data-ttu-id="795b6-253">輸入時、分鐘和秒的時間，以及上午或下午。</span><span class="sxs-lookup"><span data-stu-id="795b6-253">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
    6.  <span data-ttu-id="795b6-254">在 **[摘要]** 底下的 **[描述]** ，確認所有作業排程設定是否都正確。</span><span class="sxs-lookup"><span data-stu-id="795b6-254">Under **Summary**, in **Description**, verify that all job schedule settings are correct.</span></span>  
  
    7.  <span data-ttu-id="795b6-255">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="795b6-255">Click **OK**.</span></span>  
  
     <span data-ttu-id="795b6-256">完成這個頁面之後，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-256">After completing this page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="795b6-257">在 **[檢閱摘要]** 頁面上，展開 **[檢閱您的選擇]** 底下的所有可用選項，確認所有分割區設定是否都正確。</span><span class="sxs-lookup"><span data-stu-id="795b6-257">On the **Review Summary** page, under **Review your selections**, expand all available options to verify that all partition settings are correct.</span></span> <span data-ttu-id="795b6-258">如果一切如預期，請按一下 **[完成]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-258">If everything is as expected, click **Finish**.</span></span>  
  
9. <span data-ttu-id="795b6-259">在 **[建立分割區精靈進度]** 頁面上，監視 [建立分割區精靈] 動作的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="795b6-259">On the **Create Partition Wizard Progress** page, monitor status information about the actions of the Create Partition Wizard.</span></span> <span data-ttu-id="795b6-260">根據您在精靈中選取的選項，[進度] 頁面可能會包含一個或多個動作。</span><span class="sxs-lookup"><span data-stu-id="795b6-260">Depending on the options that you selected in the wizard, the progress page might contain one or more actions.</span></span> <span data-ttu-id="795b6-261">頂端的方塊會顯示精靈的整體狀態以及精靈已接收的狀態、錯誤和警告訊息數。</span><span class="sxs-lookup"><span data-stu-id="795b6-261">The top box displays the overall status of the wizard and the number of status, error, and warning messages that the wizard has received.</span></span>  
  
     <span data-ttu-id="795b6-262">在 **[建立分割區精靈進度]** 頁面上可以使用下列選項：</span><span class="sxs-lookup"><span data-stu-id="795b6-262">The following options are available on the **Create Partition Wizard Progress** page:</span></span>  
  
     <span data-ttu-id="795b6-263">**詳細資料**</span><span class="sxs-lookup"><span data-stu-id="795b6-263">**Details**</span></span>  
     <span data-ttu-id="795b6-264">提供從精靈所採取的動作傳回的動作、狀態和任何訊息。</span><span class="sxs-lookup"><span data-stu-id="795b6-264">Provides the action, status, and any messages that are returned from action taken by the wizard.</span></span>  
  
     <span data-ttu-id="795b6-265">**動作**</span><span class="sxs-lookup"><span data-stu-id="795b6-265">**Action**</span></span>  
     <span data-ttu-id="795b6-266">指定每個動作的類型和名稱。</span><span class="sxs-lookup"><span data-stu-id="795b6-266">Specifies the type and name of each action.</span></span>  
  
     <span data-ttu-id="795b6-267">**狀態**</span><span class="sxs-lookup"><span data-stu-id="795b6-267">**Status**</span></span>  
     <span data-ttu-id="795b6-268">指出整個精靈動作傳回 [成功]  或 [失敗]  的值。</span><span class="sxs-lookup"><span data-stu-id="795b6-268">Indicates whether the wizard action as a whole returned the value of **Success** or **Failure**.</span></span>  
  
     <span data-ttu-id="795b6-269">**訊息**</span><span class="sxs-lookup"><span data-stu-id="795b6-269">**Message**</span></span>  
     <span data-ttu-id="795b6-270">提供從程序所傳回的任何錯誤或警告訊息。</span><span class="sxs-lookup"><span data-stu-id="795b6-270">Provides any error or warning messages that are returned from the process.</span></span>  
  
     <span data-ttu-id="795b6-271">**Report**</span><span class="sxs-lookup"><span data-stu-id="795b6-271">**Report**</span></span>  
     <span data-ttu-id="795b6-272">建立包含 [建立分割區精靈] 結果的報表。</span><span class="sxs-lookup"><span data-stu-id="795b6-272">Creates a report that contains the results of the Create Partition Wizard.</span></span> <span data-ttu-id="795b6-273">選項為 **[檢視報表]** 、 **[將報表儲存到檔案]** 、 **[複製報表到剪貼簿]** 和 **[以電子郵件傳送報表]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-273">The options are **View Report**, **Save Report to File**, **Copy Report to Clipboard**, and **Send Report as Email**.</span></span>  
  
     <span data-ttu-id="795b6-274">**檢視報表**</span><span class="sxs-lookup"><span data-stu-id="795b6-274">**View Report**</span></span>  
     <span data-ttu-id="795b6-275">開啟 [檢視報表]  對話方塊，其中包含 [建立分割區精靈] 進度的文字報表。</span><span class="sxs-lookup"><span data-stu-id="795b6-275">Opens the **View Report** dialog box, which contains a text report of the progress of the Create Partition Wizard.</span></span>  
  
     <span data-ttu-id="795b6-276">**將報表儲存到檔案**</span><span class="sxs-lookup"><span data-stu-id="795b6-276">**Save Report to File**</span></span>  
     <span data-ttu-id="795b6-277">開啟 [另存報表]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="795b6-277">Opens the **Save Report As** dialog box.</span></span>  
  
     <span data-ttu-id="795b6-278">**複製報表到剪貼簿**</span><span class="sxs-lookup"><span data-stu-id="795b6-278">**Copy Report to Clipboard**</span></span>  
     <span data-ttu-id="795b6-279">將精靈進度報表的結果複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="795b6-279">Copies the results of the wizard's progress report to the Clipboard.</span></span>  
  
     <span data-ttu-id="795b6-280">**[以電子郵件傳送報表]**</span><span class="sxs-lookup"><span data-stu-id="795b6-280">**Send Report as Email**</span></span>  
     <span data-ttu-id="795b6-281">將精靈進度報表的結果複製到電子郵件。</span><span class="sxs-lookup"><span data-stu-id="795b6-281">Copies the results of the wizard's progress report into an email message.</span></span>  
  
     <span data-ttu-id="795b6-282">完成後，請按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-282">When complete, click **Close**.</span></span>  
  
 <span data-ttu-id="795b6-283">建立分割區精靈會建立分割區函數和配置，然後將此分割區套用至指定資料表。</span><span class="sxs-lookup"><span data-stu-id="795b6-283">The Create Partition Wizard creates the partition function and scheme and then applies the partitioning to the specified table.</span></span> <span data-ttu-id="795b6-284">若要驗證資料表分割區，在物件總管中以滑鼠右鍵按一下資料表，並選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="795b6-284">To verify the table partitioning, in Object Explorer, right-click the table and select **Properties**.</span></span> <span data-ttu-id="795b6-285">按一下 **[儲存體]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="795b6-285">Click the **Storage** page.</span></span> <span data-ttu-id="795b6-286">此頁面會顯示諸如分割區函數和配置名稱以及分割區數目等資訊。</span><span class="sxs-lookup"><span data-stu-id="795b6-286">The page displays information such as the name of the partition function and scheme and the number of partitions.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="795b6-287">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="795b6-287">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-partitioned-table"></a><span data-ttu-id="795b6-288">建立分割區資料表</span><span class="sxs-lookup"><span data-stu-id="795b6-288">To create a partitioned table</span></span>  
  
1.  <span data-ttu-id="795b6-289">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="795b6-289">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="795b6-290">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-290">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="795b6-291">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="795b6-291">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="795b6-292">範例會建立新的檔案群組、分割區函數和分割區配置。</span><span class="sxs-lookup"><span data-stu-id="795b6-292">The example creates new filegroups, a partition function, and a partition scheme.</span></span> <span data-ttu-id="795b6-293">新資料表是以指定為儲存位置的分割區配置建立的。</span><span class="sxs-lookup"><span data-stu-id="795b6-293">A new table is created with the partition scheme specified as the storage location.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Adds four new filegroups to the AdventureWorks2012 database  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test1fg;  
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test2fg;  
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test3fg;  
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test4fg;   
  
    -- Adds one file for each filegroup.  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = test1dat1,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\t1dat1.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP test1fg;  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = test2dat2,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\t2dat2.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP test2fg;  
    GO  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = test3dat3,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\t3dat3.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP test3fg;  
    GO  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = test4dat4,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\t4dat4.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP test4fg;  
    GO  
    -- Creates a partition function called myRangePF1 that will partition a table into four partitions  
    CREATE PARTITION FUNCTION myRangePF1 (int)  
        AS RANGE LEFT FOR VALUES (1, 100, 1000) ;  
    GO  
    -- Creates a partition scheme called myRangePS1 that applies myRangePF1 to the four filegroups created above  
    CREATE PARTITION SCHEME myRangePS1  
        AS PARTITION myRangePF1  
        TO (test1fg, test2fg, test3fg, test4fg) ;  
    GO  
    -- Creates a partitioned table called PartitionTable that uses myRangePS1 to partition col1  
    CREATE TABLE PartitionTable (col1 int PRIMARY KEY, col2 char(10))  
        ON myRangePS1 (col1) ;  
    GO  
    ```  
  
#### <a name="to-determine-if-a-table-is-partitioned"></a><span data-ttu-id="795b6-294">若要判斷資料表是否已分割</span><span class="sxs-lookup"><span data-stu-id="795b6-294">To determine if a table is partitioned</span></span>  
  
1.  <span data-ttu-id="795b6-295">下列查詢會在資料表 `PartitionTable` 已分割時，傳回一個或多個資料列。</span><span class="sxs-lookup"><span data-stu-id="795b6-295">The following query returns one or more rows if the table `PartitionTable` is partitioned.</span></span> <span data-ttu-id="795b6-296">如果資料表未分割，則不會傳回任何資料列。</span><span class="sxs-lookup"><span data-stu-id="795b6-296">If the table is not partitioned, no rows are returned.</span></span>  
  
    ```  
    SELECT *   
    FROM sys.tables AS t   
    JOIN sys.indexes AS i   
        ON t.[object_id] = i.[object_id]   
        AND i.[type] IN (0,1)   
    JOIN sys.partition_schemes ps   
        ON i.data_space_id = ps.data_space_id   
    WHERE t.name = 'PartitionTable';   
    GO  
    ```  
  
#### <a name="to-determine-the-boundary-values-for-a-partitioned-table"></a><span data-ttu-id="795b6-297">若要判斷分割資料表的界限值</span><span class="sxs-lookup"><span data-stu-id="795b6-297">To determine the boundary values for a partitioned table</span></span>  
  
1.  <span data-ttu-id="795b6-298">下列查詢會針對 `PartitionTable` 資料表中的每一個分割區傳回界限值。</span><span class="sxs-lookup"><span data-stu-id="795b6-298">The following query returns the boundary values for each partition in the `PartitionTable` table.</span></span>  
  
    ```  
    SELECT t.name AS TableName, i.name AS IndexName, p.partition_number, p.partition_id, i.data_space_id, f.function_id, f.type_desc, r.boundary_id, r.value AS BoundaryValue   
    FROM sys.tables AS t  
    JOIN sys.indexes AS i  
        ON t.object_id = i.object_id  
    JOIN sys.partitions AS p  
        ON i.object_id = p.object_id AND i.index_id = p.index_id   
    JOIN  sys.partition_schemes AS s   
        ON i.data_space_id = s.data_space_id  
    JOIN sys.partition_functions AS f   
        ON s.function_id = f.function_id  
    LEFT JOIN sys.partition_range_values AS r   
        ON f.function_id = r.function_id and r.boundary_id = p.partition_number  
    WHERE t.name = 'PartitionTable' AND i.type <= 1  
    ORDER BY p.partition_number;  
    ```  
  
#### <a name="to-determine-the-partition-column-for-a-partitioned-table"></a><span data-ttu-id="795b6-299">若要判斷分割資料表的分割區資料行</span><span class="sxs-lookup"><span data-stu-id="795b6-299">To determine the partition column for a partitioned table</span></span>  
  
1.  <span data-ttu-id="795b6-300">下列查詢會傳回資料表之分割區資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="795b6-300">The following query returns the name of the partitioning column for table.</span></span> <span data-ttu-id="795b6-301">`PartitionTable`第 1 課：建立 Windows Azure 儲存體物件`PartitionTable`。</span><span class="sxs-lookup"><span data-stu-id="795b6-301">`PartitionTable`.</span></span>  
  
    ```  
    SELECT   
        t.[object_id] AS ObjectID   
        , t.name AS TableName   
        , ic.column_id AS PartitioningColumnID   
        , c.name AS PartitioningColumnName   
    FROM sys.tables AS t   
    JOIN sys.indexes AS i   
        ON t.[object_id] = i.[object_id]   
        AND i.[type] <= 1 -- clustered index or a heap   
    JOIN sys.partition_schemes AS ps   
        ON ps.data_space_id = i.data_space_id   
    JOIN sys.index_columns AS ic   
        ON ic.[object_id] = i.[object_id]   
        AND ic.index_id = i.index_id   
        AND ic.partition_ordinal >= 1 -- because 0 = non-partitioning column   
    JOIN sys.columns AS c   
        ON t.[object_id] = c.[object_id]   
        AND ic.column_id = c.column_id   
    WHERE t.name = 'PartitionTable' ;   
    GO  
    ```  
  
 <span data-ttu-id="795b6-302">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="795b6-302">For more information, see:</span></span>  
  
-   [<span data-ttu-id="795b6-303">ALTER DATABASE 檔案及檔案群組選項 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="795b6-303">ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
-   [<span data-ttu-id="795b6-304">CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="795b6-304">CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-partition-function-transact-sql)  
  
-   [<span data-ttu-id="795b6-305">CREATE PARTITION SCHEME &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="795b6-305">CREATE PARTITION SCHEME &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-partition-scheme-transact-sql)  
  
-   [<span data-ttu-id="795b6-306">CREATE TABLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="795b6-306">CREATE TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-table-transact-sql)  
  
  
