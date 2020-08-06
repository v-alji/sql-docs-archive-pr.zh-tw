---
title: 使用非叢集資料行存放區索引 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 4c341fb8-7cb1-4cab-921b-e80b751d6c19
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c876eb6fdd466349ac369dcff8e292bc0839c669
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700192"
---
# <a name="using-nonclustered-columnstore-indexes"></a><span data-ttu-id="ccb2e-102">使用非叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="ccb2e-102">Using Nonclustered Columnstore Indexes</span></span>
  <span data-ttu-id="ccb2e-103">描述在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料表上使用非叢集資料行存放區索引的主要工作。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-103">Describes key tasks for using a nonclustered columnstore index on a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table.</span></span>

 <span data-ttu-id="ccb2e-104">如需資料行存放區索引的概觀，請參閱＜ [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-104">For an overview of columnstore indexes, see [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md).</span></span>

 <span data-ttu-id="ccb2e-105">如需有關叢集資料行存放區索引的詳細資訊，請參閱＜ [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-105">For information about clustered columnstore indexes, see [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).</span></span>

## <a name="contents"></a><span data-ttu-id="ccb2e-106">目錄</span><span class="sxs-lookup"><span data-stu-id="ccb2e-106">Contents</span></span>

-   [<span data-ttu-id="ccb2e-107">建立非叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="ccb2e-107">Create a Nonclustered Columnstore Index</span></span>](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#load)

-   [<span data-ttu-id="ccb2e-108">變更非叢集資料行存放區索引中的資料</span><span class="sxs-lookup"><span data-stu-id="ccb2e-108">Change the Data in a Nonclustered Columnstore Index</span></span>](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#change)

##  <a name="create-a-nonclustered-columnstore-index"></a><a name="load"></a><span data-ttu-id="ccb2e-109">建立非叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="ccb2e-109">Create a Nonclustered Columnstore Index</span></span>
 <span data-ttu-id="ccb2e-110">若要將資料載入非叢集資料行存放區索引，請先將資料載入至儲存為堆積或叢集索引的傳統 rowstore 資料表，然後使用 Create 資料行存放區[索引 &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)來建立資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-110">To load data into a nonclustered columnstore index, first load data into a traditional rowstore table stored as a heap or clustered index, and then use [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql) to create a columnstore index.</span></span>

 <span data-ttu-id="ccb2e-111">![將資料載入資料行存放區索引](../../2014/database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "將資料載入資料行存放區索引")</span><span class="sxs-lookup"><span data-stu-id="ccb2e-111">![Loading data into a columnstore index](../../2014/database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "Loading data into a columnstore index")</span></span>

##  <a name="change-the-data-in-a-nonclustered-columnstore-index"></a><a name="change"></a><span data-ttu-id="ccb2e-112">變更非叢集資料行存放區索引中的資料</span><span class="sxs-lookup"><span data-stu-id="ccb2e-112">Change the Data in a Nonclustered Columnstore Index</span></span>
 <span data-ttu-id="ccb2e-113">一旦您在資料表上建立非叢集資料行存放區索引，就無法直接修改該資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-113">Once you create a nonclustered columnstore index on a table, you cannot directly modify the data in that table.</span></span> <span data-ttu-id="ccb2e-114">使用 INSERT、UPDATE、DELETE 或 MERGE 的查詢將會失敗，並傳回錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-114">A query with INSERT, UPDATE, DELETE, or MERGE will fail and return an error message.</span></span> <span data-ttu-id="ccb2e-115">若要加入或修改資料表中的資料，您可以執行下列其中一項操作：</span><span class="sxs-lookup"><span data-stu-id="ccb2e-115">To add or modify the data in the table, you can do one of the following:</span></span>

-   <span data-ttu-id="ccb2e-116">停用資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-116">Disable the columnstore index.</span></span> <span data-ttu-id="ccb2e-117">然後您就可以更新資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-117">You can then update the data in the table.</span></span> <span data-ttu-id="ccb2e-118">如果您停用資料行存放區索引，您可以在完成更新資料時重建資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-118">If you disable the columnstore index, you can rebuild the columnstore index when you finish updating the data.</span></span> <span data-ttu-id="ccb2e-119">例如：</span><span class="sxs-lookup"><span data-stu-id="ccb2e-119">For example:</span></span>

    ```
    ALTER INDEX mycolumnstoreindex ON mytable DISABLE;
    -- update mytable --
    ALTER INDEX mycolumnstoreindex on mytable REBUILD
    ```

-   <span data-ttu-id="ccb2e-120">卸載資料行存放區索引、更新資料表，然後使用 CREATE 資料行存放區索引重新建立資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-120">Drop the columnstore index, update the table, and then re-create the columnstore index with CREATE COLUMNSTORE INDEX.</span></span> <span data-ttu-id="ccb2e-121">例如：</span><span class="sxs-lookup"><span data-stu-id="ccb2e-121">For example:</span></span>

    ```
    DROP INDEX mycolumnstoreindex ON mytable
    -- update mytable --
    CREATE NONCLUSTERED COLUMNSTORE INDEX mycolumnstoreindex ON mytable;

    ```

-   <span data-ttu-id="ccb2e-122">將資料載入未包含資料行存放區索引的暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-122">Load data into a staging table that does not have a columnstore index.</span></span> <span data-ttu-id="ccb2e-123">在暫存資料表上建立資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-123">Build a columnstore index on the staging table.</span></span> <span data-ttu-id="ccb2e-124">將暫存資料表切換至主資料表的空白分割區。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-124">Switch the staging table into an empty partition of the main table.</span></span>

-   <span data-ttu-id="ccb2e-125">從具有資料行存放區索引的資料表分割區切換至空白的暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-125">Switch a partition from the table with the columnstore index into an empty staging table.</span></span> <span data-ttu-id="ccb2e-126">如果暫存資料表上有資料行存放區索引，請停用資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-126">If there is a columnstore index on the staging table, disable the columnstore index.</span></span> <span data-ttu-id="ccb2e-127">執行所有更新。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-127">Perform any updates.</span></span> <span data-ttu-id="ccb2e-128">建立 (或重建) 資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-128">Build (or rebuild) the columnstore index.</span></span> <span data-ttu-id="ccb2e-129">將暫存資料表切換回 (現在為空白的) 主資料表分割區。</span><span class="sxs-lookup"><span data-stu-id="ccb2e-129">Switch the staging table back into the (now empty) partition of the main table.</span></span>




