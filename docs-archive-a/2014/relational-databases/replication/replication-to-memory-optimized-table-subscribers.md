---
title: 複寫至記憶體最佳化資料表訂閱者 | Microsoft 文件
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
ms.assetid: 1a8e6bc7-433e-471d-b646-092dc80a2d1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: df61b83d2f6d07cbbd21773b8940dd4e5341f76b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585268"
---
# <a name="replication-to-memory-optimized-table-subscribers"></a><span data-ttu-id="b2b76-102">複寫至記憶體最佳化資料表訂閱者</span><span class="sxs-lookup"><span data-stu-id="b2b76-102">Replication to Memory-Optimized Table Subscribers</span></span>
  <span data-ttu-id="b2b76-103">做為異動複寫訂閱者的資料表 (不包括點對點異動複寫) 可以設定為記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="b2b76-103">Tables acting as transactional replication subscribers, excluding Peer-to-peer transactional replication, can be configured as memory-optimized tables.</span></span> <span data-ttu-id="b2b76-104">其他複寫組態與記憶體最佳化資料表不相容。</span><span class="sxs-lookup"><span data-stu-id="b2b76-104">Other replication configurations are not compatible with memory-optimized tables.</span></span>  
  
## <a name="configuring-a-memory-optimized-table-as-a-subscriber"></a><span data-ttu-id="b2b76-105">將記憶體最佳化資料表設定為訂閱者</span><span class="sxs-lookup"><span data-stu-id="b2b76-105">Configuring a memory-optimized table as a subscriber</span></span>  
 <span data-ttu-id="b2b76-106">若要設定記憶體最佳化資料表做為訂閱者，請執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="b2b76-106">To configure a memory-optimized table as a subscriber, perform the following steps.</span></span>  
  
 <span data-ttu-id="b2b76-107">**建立和啟用發行集**</span><span class="sxs-lookup"><span data-stu-id="b2b76-107">**Create and Enable Publication**</span></span>  
  
1.  <span data-ttu-id="b2b76-108">建立發行集。</span><span class="sxs-lookup"><span data-stu-id="b2b76-108">Create a publication.</span></span>  
  
2.  <span data-ttu-id="b2b76-109">將發行項加入至發行集。</span><span class="sxs-lookup"><span data-stu-id="b2b76-109">Add articles to the publication.</span></span> <span data-ttu-id="b2b76-110">針對 `@upd_cmd` 參數，請使用 SCALL 或 SQL 慣例。</span><span class="sxs-lookup"><span data-stu-id="b2b76-110">For the `@upd_cmd` parameter, use the SCALL or SQL convention.</span></span>  
  
    ```  
    EXEC sp_addarticle  
        @publication = N'Publication1',  
        @article = N'Mem_Table',  
        @source_owner = N'dbo',  
        @source_object = N'Mem_Table',  
        @type = N'logbased',  
        @description = null,  
        @creation_script = null,  
        @pre_creation_cmd = N'none',  
        @schema_option = 0x00000000080050DF,  
        @identityrangemanagementoption = N'manual',  
        @destination_table = N'Mem_Table',  
        @destination_owner = N'dbo',  
        @vertical_partition = N'false',  
        @ins_cmd = N'CALL sp_MSins_Mem_Table',  
        @del_cmd = N'CALL sp_MSdel_Mem_Table',  
        @upd_cmd = N'SCALL sp_MSupd_Mem_Table';  
    GO  
    ```  
  
 <span data-ttu-id="b2b76-111">**產生快照集和調整結構描述**</span><span class="sxs-lookup"><span data-stu-id="b2b76-111">**Generate a Snapshot and Adjust the Schema**</span></span>  
  
1.  <span data-ttu-id="b2b76-112">建立快照集工作，並產生快照集。</span><span class="sxs-lookup"><span data-stu-id="b2b76-112">Create a snapshot job and generate a snapshot.</span></span>  
  
    ```  
    EXEC sp_addpublication_snapshot @publication = N'Publication1', @frequency_type = 1;  
    EXEC sp_startpublication_snapshot @publication = N'Publication1';  
    ```  
  
2.  <span data-ttu-id="b2b76-113">導覽到快照集資料夾。</span><span class="sxs-lookup"><span data-stu-id="b2b76-113">Navigate to the snapshot folder.</span></span> <span data-ttu-id="b2b76-114">預設位置為 "C:\Program Files\Microsoft SQL Server\MSSQL12. \<INSTANCE>\MSSQL\repldata\unc\XXX\YYYYMMDDHHMMSS \\ "。</span><span class="sxs-lookup"><span data-stu-id="b2b76-114">The default location is "C:\Program Files\Microsoft SQL Server\MSSQL12.\<INSTANCE>\MSSQL\repldata\unc\XXX\YYYYMMDDHHMMSS\\".</span></span>  
  
3.  <span data-ttu-id="b2b76-115">找出 **。.SCH**您資料表的檔案，並在 Management Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="b2b76-115">Locate the **.SCH** file for your table and open it in Management Studio.</span></span> <span data-ttu-id="b2b76-116">變更資料表結構描述並更新預存程序，如下所述。</span><span class="sxs-lookup"><span data-stu-id="b2b76-116">Change the table schema and update the stored procedure as described below.</span></span>  
  
     <span data-ttu-id="b2b76-117">評估 IDX 檔案中定義的索引。</span><span class="sxs-lookup"><span data-stu-id="b2b76-117">Evaluate the indexes defined in the IDX file.</span></span> <span data-ttu-id="b2b76-118">修改 `CREATE TABLE`，以指定必要的索引、條件約束、主索引鍵和記憶體最佳化語法。</span><span class="sxs-lookup"><span data-stu-id="b2b76-118">Modify `CREATE TABLE` to specify the required indexes, constraints, primary key, and memory-optimized syntax.</span></span> <span data-ttu-id="b2b76-119">對於記憶體最佳化資料表，索引資料行應該是 NOT NULL，而字元類型的索引資料行必須是 Unicode 並且使用 BIN2 定序。</span><span class="sxs-lookup"><span data-stu-id="b2b76-119">For memory-optimized tables, index columns should be NOT NULL and index columns of character types must be Unicode and use BIN2 collation.</span></span> <span data-ttu-id="b2b76-120">請參閱以下範例：</span><span class="sxs-lookup"><span data-stu-id="b2b76-120">See example below:</span></span>  
  
    ```  
    SET ANSI_PADDING ON;  
    GO  
  
    SET ANSI_NULLS ON;  
    GO  
  
    SET QUOTED_IDENTIFIER ON;  
    GO  
  
    CREATE TABLE [dbo].[Mem_Table]([c1] [int] NOT NULL,  
        [c2] [float] NOT NULL,  
        [c3] [decimal](10, 2) NOT NULL,  
        [c4] [nvarchar](5) COLLATE SQL_Latin1_General_CP850_BIN2 NOT NULL,  
        INDEX [hash_index_sample_memoryoptimizedtable_c2] HASH (c2) WITH (BUCKET_COUNT = 1024),  
        INDEX [index_sample_memoryoptimizedtable_c3] NONCLUSTERED ([c3]),  
        INDEX [nvarchar_index_sample_memoryoptimizedtable_c4] ([c4]),  
        CONSTRAINT [PK_sample_memoryoptimizedtable] PRIMARY KEY NONCLUSTERED ([c1])) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA);  
    GO  
    ```  
  
4.  <span data-ttu-id="b2b76-121">使用 SCALL 慣例做為 `@upd_cmd` 參數時，請移至結構描述 (.SCH) 檔案並變更 `create procedure [sp_MSupd_<SCHEMA><TABLE_NAME>]` 中的資料表更新陳述式，以移除主索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="b2b76-121">When using SCALL convention for the `@upd_cmd` parameter, go to the schema (.SCH) file and change the table update statement in `create procedure [sp_MSupd_<SCHEMA><TABLE_NAME>]` to remove primary key columns.</span></span>  
  
     <span data-ttu-id="b2b76-122">若要支援主索引鍵更新，請使用自訂更新預存程序取代主索引鍵更新陳述式，如下所述：</span><span class="sxs-lookup"><span data-stu-id="b2b76-122">To support primary key updates, use a custom update stored procedure to replace the primary key update statement, as follows:</span></span>  
  
    1.  <span data-ttu-id="b2b76-123">選取遺漏的資料行值 (SCALL 僅對更新作業提供包含的資料行)。</span><span class="sxs-lookup"><span data-stu-id="b2b76-123">Select missing column values (SCALL only provides the column involved into the update operation).</span></span>  
  
    2.  <span data-ttu-id="b2b76-124">刪除現有記錄。</span><span class="sxs-lookup"><span data-stu-id="b2b76-124">Delete the existing record.</span></span>  
  
    3.  <span data-ttu-id="b2b76-125">插入新記錄並提供新值，包括新的主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b2b76-125">Insert a new record with new values provided including the new primary key.</span></span>  
  
     <span data-ttu-id="b2b76-126">原始更新程序如下所示：</span><span class="sxs-lookup"><span data-stu-id="b2b76-126">The original update procedure looks like this:</span></span>  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                   @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    update [dbo].[Mem_Table] set  
                   [c1] = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
     <span data-ttu-id="b2b76-127">如果發行者的主索引鍵應永遠不更新，</span><span class="sxs-lookup"><span data-stu-id="b2b76-127">If the primary key should never be updated on a publisher.</span></span> <span data-ttu-id="b2b76-128">請在更新程序中，將對這類資料行的更新設為註解，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b2b76-128">Comment out the update to such columns in the update procedure as follows:</span></span>  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                   @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    update [dbo].[Mem_Table] set  
    --             [c1] = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
     <span data-ttu-id="b2b76-129">若要允許支援更新主索引鍵，請修改更新程序，如下所示</span><span class="sxs-lookup"><span data-stu-id="b2b76-129">To allow the support of updates to the primary key, modify the update procedure to read as follows</span></span>  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                    @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    select  
                   @c1 = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   @c2 = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   @c3 = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   @c4 = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    from [dbo].[Mem_Table] where [c1] = @pkc1  
    if @@rowcount <> 0 begin  
            delete [dbo].[Mem_Table] where [c1] = @pkc1  
            if @@rowcount <> 0  
                   insert into [dbo].[Mem_Table]([c1],  
                           [c2],  
                           [c3],  
                           [c4]) values (  
                           @c1,  
                           @c2,  
                           @c3,  
                           @c4  
                   )   
    end  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
5.  <span data-ttu-id="b2b76-130">使用 [**提升為快照隔離**] 選項建立訂閱者資料庫，並在使用非 Unicode 字元資料類型時，將預設定序設定為 Latin1_General_CS_AS_KS_WS。</span><span class="sxs-lookup"><span data-stu-id="b2b76-130">Create subscriber database using the **elevate to snapshot isolation** option and set the default collation to Latin1_General_CS_AS_KS_WS in case of using non Unicode character data types.</span></span>  
  
    ```  
    CREATE DATABASE [Sub]   
    CONTAINMENT = NONE   
    ON PRIMARY ( NAME = [Sub], FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub.mdf]),   
    FILEGROUP [mem] CONTAINS MEMORY_OPTIMIZED_DATA ( NAME = [mem],   
    FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub])  
    LOG ON ( NAME = [Sub_log], FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub.ldf])  
    COLLATE Latin1_General_CS_AS_KS_WS;  
  
    ALTER DATABASE [Sub] SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT = ON;  
    GO  
    ```  
  
6.  <span data-ttu-id="b2b76-131">將架構套用至訂閱者的資料庫，並儲存架構以供未來使用。</span><span class="sxs-lookup"><span data-stu-id="b2b76-131">Apply the schema to a subscriber's database and save the schema for future use.</span></span>  
  
7.  <span data-ttu-id="b2b76-132">將發行者 (來源) 資料載入至訂閱者。</span><span class="sxs-lookup"><span data-stu-id="b2b76-132">Load the publisher (source) data to the subscriber.</span></span> <span data-ttu-id="b2b76-133">資料在發行者端應該不會變更，除非您加入訂閱。</span><span class="sxs-lookup"><span data-stu-id="b2b76-133">Data should not change at the publisher until you add a subscription.</span></span>  <span data-ttu-id="b2b76-134">您可以使用 BCP，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b2b76-134">You can use BCP as shown below:</span></span>  
  
    ```  
    bcp Pub.dbo.Mem_Table out Mem_Table.bcp -S. -T -C1252 -n  
    bcp Sub.dbo.Mem_Table in Mem_Table.bcp -S. -T -C1252 -n  
    ```  
  
8.  <span data-ttu-id="b2b76-135">將發行項重新設定為停用訂閱者端的結構描述變更：</span><span class="sxs-lookup"><span data-stu-id="b2b76-135">Reconfigure the article to disable schema changes on the subscriber:</span></span>  
  
    ```  
    EXEC sp_changearticle  
        @publication = N'Publication1',  
        @article = N'Mem_Table',  
        @property = N'schema_option',  
        @value = 0,  
        @force_invalidate_snapshot = 1,  
        @force_reinit_subscription = 1;  
    GO  
    ```  
  
 <span data-ttu-id="b2b76-136">**加入非同步訂閱**</span><span class="sxs-lookup"><span data-stu-id="b2b76-136">**Add no sync Subscription**</span></span>  
  
 <span data-ttu-id="b2b76-137">加入 nosync 訂閱。</span><span class="sxs-lookup"><span data-stu-id="b2b76-137">Add a nosync subscription.</span></span>  
  
```  
EXEC sp_addsubscription  
    @publication = N' Publication1',  
    @subscriber = @@ServerName,  
    @destination_db = N'Sub',  
    @subscription_type = N'Push',  
    @sync_type = N'replication support only',  
    @article = N'all',  
    @update_mode = N'read only',  
    @subscriber_type = 0;  
GO  
```  
  
 <span data-ttu-id="b2b76-138">記憶體最佳化資料表現在應該會開始接收來自發行者的更新。</span><span class="sxs-lookup"><span data-stu-id="b2b76-138">Memory-optimized tables should now start receiving updates from the publisher.</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="b2b76-139">限制</span><span class="sxs-lookup"><span data-stu-id="b2b76-139">Restrictions</span></span>  
 <span data-ttu-id="b2b76-140">僅支援單向異動複寫。</span><span class="sxs-lookup"><span data-stu-id="b2b76-140">Only one-way transactional replication is supported.</span></span> <span data-ttu-id="b2b76-141">不支援點對點異動複寫。</span><span class="sxs-lookup"><span data-stu-id="b2b76-141">Peer-to-peer transactional replication is not supported.</span></span>  
  
 <span data-ttu-id="b2b76-142">無法發行記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="b2b76-142">Memory-optimized tables cannot be published.</span></span>  
  
 <span data-ttu-id="b2b76-143">散發者端的複寫資料表無法設定為記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="b2b76-143">Replication tables on the distributor cannot be configured as memory-optimized tables.</span></span>  
  
 <span data-ttu-id="b2b76-144">合併式複寫無法包含記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="b2b76-144">Merge replication cannot include memory-optimized tables.</span></span>  
  
 <span data-ttu-id="b2b76-145">在訂閱者端，異動複寫中包含的資料表可以設定為記憶體最佳化資料表，但是訂閱者資料表必須符合記憶體最佳化資料表的需求。</span><span class="sxs-lookup"><span data-stu-id="b2b76-145">At the subscriber, tables involved in transactional replication can be configured as memory optimized tables, but the subscriber tables must meet the requirements of memory-optimized tables.</span></span> <span data-ttu-id="b2b76-146">需求的限制如下。</span><span class="sxs-lookup"><span data-stu-id="b2b76-146">This requires the following restrictions.</span></span>  
  
-   <span data-ttu-id="b2b76-147">若要在異動複寫訂閱者上建立記憶體最佳化資料表，必須手動修改用來建立記憶體最佳化資料表的快照集結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="b2b76-147">To create a memory-optimized table on a transactional replication subscriber, the snapshot schema files used to create the memory-optimized tables must be manually modified.</span></span> <span data-ttu-id="b2b76-148">如需詳細資訊，請參閱[修改架構](#Schema)檔案。</span><span class="sxs-lookup"><span data-stu-id="b2b76-148">For more information, see [Modifying a schema file](#Schema).</span></span>  
  
-   <span data-ttu-id="b2b76-149">複寫至訂閱者端記憶體最佳化資料表的資料表限制，會是記憶體最佳化資料表每一個資料列限制的 8060 個位元組。</span><span class="sxs-lookup"><span data-stu-id="b2b76-149">Tables replicated to memory-optimized tables on a subscriber are limited to the 8060 bytes per row limit of memory-optimized tables.</span></span>  
  
-   <span data-ttu-id="b2b76-150">複寫至訂閱者端記憶體最佳化資料表的資料表限制，則為記憶體最佳化資料表中允許的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b2b76-150">Tables replicated to memory-optimized tables on a subscriber are limited to the data types permitted in memory-optimized tables.</span></span> <span data-ttu-id="b2b76-151">如需詳細資訊，請參閱[支援的資料類型](../in-memory-oltp/supported-data-types-for-in-memory-oltp.md)。</span><span class="sxs-lookup"><span data-stu-id="b2b76-151">For more information, see [Supported Data Types](../in-memory-oltp/supported-data-types-for-in-memory-oltp.md).</span></span>  
  
-   <span data-ttu-id="b2b76-152">對於更新複寫至訂閱者端之記憶體最佳化資料表的資料表主索引鍵也有些限制。</span><span class="sxs-lookup"><span data-stu-id="b2b76-152">There are restrictions on updating the primary key of tables being replicated to a memory-optimized table on a subscriber.</span></span> <span data-ttu-id="b2b76-153">如需詳細資訊，請參閱[將變更複寫至主要金鑰](#PrimaryKey)。</span><span class="sxs-lookup"><span data-stu-id="b2b76-153">For more information, see [Replicating changes to a primary key](#PrimaryKey).</span></span>  
  
-   <span data-ttu-id="b2b76-154">記憶體最佳化資料表中不支援外部索引鍵、唯一條件約束、觸發程序、結構描述修改、ROWGUIDCOL、計算資料行、資料壓縮、別名資料類型、版本設定及鎖定。</span><span class="sxs-lookup"><span data-stu-id="b2b76-154">Foreign key, unique constraint, triggers, schema modifications, ROWGUIDCOL, computed columns, data compression, alias data types, versioning, and locks are not supported in memory-optimized tables.</span></span> <span data-ttu-id="b2b76-155">如需詳細資訊，請參閱＜ [Transact-SQL Constructs Not Supported by In-Memory OLTP](../in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md) ＞。</span><span class="sxs-lookup"><span data-stu-id="b2b76-155">See [Transact-SQL Constructs Not Supported by In-Memory OLTP](../in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md) for information.</span></span>  
  
##  <a name="modifying-a-schema-file"></a><a name="Schema"></a><span data-ttu-id="b2b76-156">修改架構檔案</span><span class="sxs-lookup"><span data-stu-id="b2b76-156">Modifying a schema file</span></span>  
  
-   <span data-ttu-id="b2b76-157">不支援叢集索引。</span><span class="sxs-lookup"><span data-stu-id="b2b76-157">Clustered indexes are not supported.</span></span> <span data-ttu-id="b2b76-158">將任何叢集索引變更為非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="b2b76-158">Change any clustered indexes to nonclustered indexes.</span></span>  
  
-   <span data-ttu-id="b2b76-159">索引之索引鍵中的所有資料行都必須指定為 `NOT NULL`。</span><span class="sxs-lookup"><span data-stu-id="b2b76-159">All columns in the key of an index must be specified as `NOT NULL`.</span></span>  
  
-   <span data-ttu-id="b2b76-160">如果使用記憶體最佳化資料表選項 `DURABILITY = SCHEMA_AND_DATA` ，則資料表必須具有非叢集主索引鍵索引。</span><span class="sxs-lookup"><span data-stu-id="b2b76-160">If using the memory-optimized table option `DURABILITY = SCHEMA_AND_DATA` the table must have a nonclustered primary key index.</span></span>  
  
-   <span data-ttu-id="b2b76-161">ANSI_PADDING 必須為 ON。</span><span class="sxs-lookup"><span data-stu-id="b2b76-161">ANSI_PADDING must be ON.</span></span>  
  
##  <a name="replicating-changes-to-a-primary-key"></a><a name="PrimaryKey"></a><span data-ttu-id="b2b76-162">將變更複寫至主要金鑰</span><span class="sxs-lookup"><span data-stu-id="b2b76-162">Replicating changes to a primary key</span></span>  
 <span data-ttu-id="b2b76-163">記憶體最佳化資料表的主索引鍵無法更新。</span><span class="sxs-lookup"><span data-stu-id="b2b76-163">The primary key of a memory-optimized table cannot be updated.</span></span> <span data-ttu-id="b2b76-164">若要複寫訂閱者端的主索引鍵更新，請修改更新預存程序，將更新做為刪除和插入組傳遞。</span><span class="sxs-lookup"><span data-stu-id="b2b76-164">To replicate a primary key update on a subscriber, modify the update stored procedure to deliver the update as a delete and insert pair.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b76-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2b76-165">See Also</span></span>  
 [<span data-ttu-id="b2b76-166">SQL Server 複寫</span><span class="sxs-lookup"><span data-stu-id="b2b76-166">SQL Server Replication</span></span>](sql-server-replication.md)  
  
  
