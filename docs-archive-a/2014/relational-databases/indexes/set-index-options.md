---
title: 設定索引選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- ALLOW_ROW_LOCKS option
- SORT_IN_TEMPDB option
- DROP_EXISTING clause
- large data, indexes
- PAD_INDEX
- STATISTICS_NORECOMPUTE
- MAXDOP index option, setting
- index options [SQL Server]
- MAXDOP index option
- IGNORE_DUP_KEY option
- ALLOW_PAGE_LOCKS option
- ONLINE
ms.assetid: 7969af33-e94c-41f7-ab89-9d9a2747cd5c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9f2d7f0bbbf0d152d3f510ae9ddbe3168634ef96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707550"
---
# <a name="set-index-options"></a><span data-ttu-id="417a0-102">設定索引選項</span><span class="sxs-lookup"><span data-stu-id="417a0-102">Set Index Options</span></span>
  <span data-ttu-id="417a0-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改索引的屬性。</span><span class="sxs-lookup"><span data-stu-id="417a0-103">This topic describes how to modify the properties of an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="417a0-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="417a0-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="417a0-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="417a0-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="417a0-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="417a0-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="417a0-107">安全性</span><span class="sxs-lookup"><span data-stu-id="417a0-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="417a0-108">**使用下列方法修改索引的屬性：**</span><span class="sxs-lookup"><span data-stu-id="417a0-108">**To modify the properties of an index, using:**</span></span>  
  
     [<span data-ttu-id="417a0-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="417a0-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="417a0-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="417a0-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="417a0-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="417a0-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="417a0-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="417a0-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="417a0-113">透過使用 ALTER INDEX 陳述式的 SET 子句，會在索引立即套用下列選項：ALLOW_PAGE_LOCKS、ALLOW_ROW_LOCKS、IGNORE_DUP_KEY 和 STATISTICS_NORECOMPUTE。</span><span class="sxs-lookup"><span data-stu-id="417a0-113">The following options are immediately applied to the index by using the SET clause in the ALTER INDEX statement: ALLOW_PAGE_LOCKS, ALLOW_ROW_LOCKS, IGNORE_DUP_KEY, and STATISTICS_NORECOMPUTE.</span></span>  
  
-   <span data-ttu-id="417a0-114">當您使用 ALTER INDEX REBUILD 或 CREATE INDEX WITH DROP_EXISTING 重建索引時，可以設定下列選項：PAD_INDEX、FILLFACTOR、SORT_IN_TEMPDB、IGNORE_DUP_KEY、STATISTICS_NORECOMPUTE、ONLINE、ALLOW_ROW_LOCKS、ALLOW_PAGE_LOCKS、MAXDOP 和 DROP_EXISTING (僅限 CREATE INDEX)。</span><span class="sxs-lookup"><span data-stu-id="417a0-114">The following options can be set when you rebuild an index by using either ALTER INDEX REBUILD or CREATE INDEX WITH DROP_EXISTING: PAD_INDEX, FILLFACTOR, SORT_IN_TEMPDB, IGNORE_DUP_KEY, STATISTICS_NORECOMPUTE, ONLINE, ALLOW_ROW_LOCKS, ALLOW_PAGE_LOCKS, MAXDOP, and DROP_EXISTING (CREATE INDEX only).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="417a0-115">Security</span><span class="sxs-lookup"><span data-stu-id="417a0-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="417a0-116">權限</span><span class="sxs-lookup"><span data-stu-id="417a0-116">Permissions</span></span>  
 <span data-ttu-id="417a0-117">需要資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="417a0-117">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="417a0-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="417a0-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-the-properties-of-an-index-in-table-designer"></a><span data-ttu-id="417a0-119">在資料表設計工具中修改索引的屬性</span><span class="sxs-lookup"><span data-stu-id="417a0-119">To modify the properties of an index in Table Designer</span></span>  
  
1.  <span data-ttu-id="417a0-120">在 [物件總管] 中，按一下加號展開資料庫，此資料庫包含您要修改索引屬性的資料表。</span><span class="sxs-lookup"><span data-stu-id="417a0-120">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to modify an index's properties.</span></span>  
  
2.  <span data-ttu-id="417a0-121">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="417a0-121">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="417a0-122">以滑鼠右鍵按一下要修改索引屬性的資料表，然後選取 [設計]  。</span><span class="sxs-lookup"><span data-stu-id="417a0-122">Right-click the table on which you want to modify an index's properties and select **Design**.</span></span>  
  
4.  <span data-ttu-id="417a0-123">在 [資料表設計工具]  功能表上，按一下 [索引/索引鍵]  。</span><span class="sxs-lookup"><span data-stu-id="417a0-123">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="417a0-124">選取您要修改的索引。</span><span class="sxs-lookup"><span data-stu-id="417a0-124">Select the index that you want to modify.</span></span> <span data-ttu-id="417a0-125">其屬性會在主要方格中顯示。</span><span class="sxs-lookup"><span data-stu-id="417a0-125">Its properties will show up in the main grid.</span></span>  
  
6.  <span data-ttu-id="417a0-126">變更任何和所有屬性的設定，以自訂索引。</span><span class="sxs-lookup"><span data-stu-id="417a0-126">Change the settings of any and all properties to customize the index.</span></span>  
  
7.  <span data-ttu-id="417a0-127">按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="417a0-127">Click **Close**.</span></span>  
  
8.  <span data-ttu-id="417a0-128">在 [檔案]  功能表上，選取 [儲存 _table_name_]  。</span><span class="sxs-lookup"><span data-stu-id="417a0-128">On the **File** menu, select **Save**_table_name_.</span></span>  
  
#### <a name="to-modify-the-properties-of-an-index-in-object-explorer"></a><span data-ttu-id="417a0-129">在物件總管中修改索引的屬性</span><span class="sxs-lookup"><span data-stu-id="417a0-129">To modify the properties of an index in Object Explorer</span></span>  
  
1.  <span data-ttu-id="417a0-130">在 [物件總管] 中，按一下加號展開資料庫，此資料庫包含您要修改索引屬性的資料表。</span><span class="sxs-lookup"><span data-stu-id="417a0-130">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to modify an index's properties.</span></span>  
  
2.  <span data-ttu-id="417a0-131">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="417a0-131">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="417a0-132">按一下加號展開要修改索引屬性的資料表。</span><span class="sxs-lookup"><span data-stu-id="417a0-132">Click the plus sign to expand the table on which you want to modify an index's properties.</span></span>  
  
4.  <span data-ttu-id="417a0-133">按一下加號展開 **[索引]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="417a0-133">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="417a0-134">以滑鼠右鍵按一下要修改其屬性的索引，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="417a0-134">Right-click the index of which you want to modify the properties and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="417a0-135">在 **[選取頁面]** 底下，選取 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="417a0-135">Under **Select a page**, select **Options**.</span></span>  
  
7.  <span data-ttu-id="417a0-136">變更任何和所有屬性的設定，以自訂索引。</span><span class="sxs-lookup"><span data-stu-id="417a0-136">Change the settings of any and all properties to customize the index.</span></span>  
  
8.  <span data-ttu-id="417a0-137">若要新增、移除或變更索引資料行的位置，請選取 [索引屬性 - _index_name_]  對話方塊中的 [一般]  頁面。</span><span class="sxs-lookup"><span data-stu-id="417a0-137">To add, remove, or change the position of an index column, select the **General** page from the **Index Properties -** _index_name_ dialog box.</span></span> <span data-ttu-id="417a0-138">如需相關資訊，請參閱 [Index Properties F1 Help](index-properties-f1-help.md)</span><span class="sxs-lookup"><span data-stu-id="417a0-138">For more information, see [Index Properties F1 Help](index-properties-f1-help.md)</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="417a0-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="417a0-139">Using Transact-SQL</span></span>  
  
#### <a name="to-see-the-properties-of-all-the-indexes-in-a-table"></a><span data-ttu-id="417a0-140">查看資料表中所有索引的屬性</span><span class="sxs-lookup"><span data-stu-id="417a0-140">To see the properties of all the indexes in a table</span></span>  
  
1.  <span data-ttu-id="417a0-141">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="417a0-141">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="417a0-142">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="417a0-142">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="417a0-143">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="417a0-143">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT i.name AS index_name,   
        i.type_desc,   
        i.is_unique,   
        ds.type_desc AS filegroup_or_partition_scheme,   
        ds.name AS filegroup_or_partition_scheme_name,   
        i.ignore_dup_key,   
        i.is_primary_key,   
        i.is_unique_constraint,   
        i.fill_factor,   
        i.is_padded,   
        i.is_disabled,   
        i.allow_row_locks,   
        i.allow_page_locks,   
        i.has_filter,   
        i.filter_definition  
    FROM sys.indexes AS i  
       INNER JOIN sys.data_spaces AS ds ON i.data_space_id = ds.data_space_id  
    WHERE is_hypothetical = 0 AND i.index_id <> 0   
       AND i.object_id = OBJECT_ID('HumanResources.Employee');   
    GO  
  
    ```  
  
#### <a name="to-set-the-properties-of-an-index"></a><span data-ttu-id="417a0-144">設定索引的屬性</span><span class="sxs-lookup"><span data-stu-id="417a0-144">To set the properties of an index</span></span>  
  
1.  <span data-ttu-id="417a0-145">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="417a0-145">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="417a0-146">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="417a0-146">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="417a0-147">將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="417a0-147">Copy and paste the following examples into the query window and click **Execute**.</span></span>  
  
     [!code-sql[IndexDDL#AlterIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex4)]  
  
     [!code-sql[IndexDDL#AlterIndex2](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex2)]  
  
 <span data-ttu-id="417a0-148">如需詳細資訊，請參閱 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="417a0-148">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
