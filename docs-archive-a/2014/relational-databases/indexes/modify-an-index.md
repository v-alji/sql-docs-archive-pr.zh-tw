---
title: 修改索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], modifying
- modifying indexes
- index changes [SQL Server]
ms.assetid: 97e3110d-fde7-4f5d-9309-dc1697960aeb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2af9293966afce8372f5b83a579418c546c82816
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707554"
---
# <a name="modify-an-index"></a><span data-ttu-id="c5fbc-102">修改索引</span><span class="sxs-lookup"><span data-stu-id="c5fbc-102">Modify an Index</span></span>
  <span data-ttu-id="c5fbc-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，修改 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的索引。</span><span class="sxs-lookup"><span data-stu-id="c5fbc-103">This topic describes how to modify an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c5fbc-104">因 PRIMARY KEY 或 UNIQUE 條件約束而建立的索引將無法使用此方法來修改。</span><span class="sxs-lookup"><span data-stu-id="c5fbc-104">Indexes created as the result of a PRIMARY KEY or UNIQUE constraint cannot be modified by using this method.</span></span> <span data-ttu-id="c5fbc-105">必須修改條件約束。</span><span class="sxs-lookup"><span data-stu-id="c5fbc-105">Instead, the constraint must be modified.</span></span>  
  
 <span data-ttu-id="c5fbc-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="c5fbc-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c5fbc-107">**若要修改索引，使用：**</span><span class="sxs-lookup"><span data-stu-id="c5fbc-107">**To modify an index, using:**</span></span>  
  
     [<span data-ttu-id="c5fbc-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c5fbc-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c5fbc-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c5fbc-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c5fbc-110">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c5fbc-110">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-an-index"></a><span data-ttu-id="c5fbc-111">若要修改索引</span><span class="sxs-lookup"><span data-stu-id="c5fbc-111">To modify an index</span></span>  
  
1.  <span data-ttu-id="c5fbc-112">在 [物件總管] 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="c5fbc-112">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="c5fbc-113">展開 **[資料庫]** ，展開資料表所在的資料庫，然後展開 **[資料表]** 。</span><span class="sxs-lookup"><span data-stu-id="c5fbc-113">Expand **Databases**, expand the database in which the table belongs, and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="c5fbc-114">展開索引所在的資料表，然後展開 **[索引]** 。</span><span class="sxs-lookup"><span data-stu-id="c5fbc-114">Expand the table in which the index belongs and then expand **Indexes**.</span></span>  
  
4.  <span data-ttu-id="c5fbc-115">以滑鼠右鍵按一下您要修改的索引，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="c5fbc-115">Right-click the index that you want to modify and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="c5fbc-116">在 **[索引屬性]** 對話方塊中，進行所需的變更。</span><span class="sxs-lookup"><span data-stu-id="c5fbc-116">In the **Index Properties** dialog box, make the desired changes.</span></span> <span data-ttu-id="c5fbc-117">例如，您可以在索引鍵中加入或移除資料行，或是變更索引選項的設定。</span><span class="sxs-lookup"><span data-stu-id="c5fbc-117">For example, you can add or remove a column from the index key, or change the setting of an index option.</span></span>  
  
#### <a name="to-modify-index-columns"></a><span data-ttu-id="c5fbc-118">若要修改索引資料行</span><span class="sxs-lookup"><span data-stu-id="c5fbc-118">To modify index columns</span></span>  
  
1.  <span data-ttu-id="c5fbc-119">若要加入、移除或變更索引資料行的位置，請選取 **[索引屬性]** 對話方塊中的 **[一般]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="c5fbc-119">To add, remove, or change the position of an index column, select the **General** page from the **Index Properties** dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c5fbc-120">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c5fbc-120">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-an-index"></a><span data-ttu-id="c5fbc-121">若要修改索引</span><span class="sxs-lookup"><span data-stu-id="c5fbc-121">To modify an index</span></span>  
  
1.  <span data-ttu-id="c5fbc-122">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c5fbc-122">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c5fbc-123">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="c5fbc-123">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c5fbc-124">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="c5fbc-124">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="c5fbc-125">此範例會利用 `ProductID` 選項，在 `Production.WorkOrder` 資料表的 `DROP_EXISTING` 資料行上卸除及重新建立現有的索引。</span><span class="sxs-lookup"><span data-stu-id="c5fbc-125">This example drops and re-creates an existing index on the `ProductID` column of the `Production.WorkOrder` table by using the `DROP_EXISTING` option.</span></span> <span data-ttu-id="c5fbc-126">也會設定 `FILLFACTOR` 和 `PAD_INDEX` 選項。</span><span class="sxs-lookup"><span data-stu-id="c5fbc-126">The options `FILLFACTOR` and `PAD_INDEX` are also set.</span></span>  
  
     [!code-sql[IndexDDL#CreateIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/createindex.sql#createindex4)]  
  
     <span data-ttu-id="c5fbc-127">下列範例會使用 ALTER INDEX 設定 `AK_SalesOrderHeader_SalesOrderNumber`索引的幾個選項。</span><span class="sxs-lookup"><span data-stu-id="c5fbc-127">The following example uses ALTER INDEX to set several options on the index `AK_SalesOrderHeader_SalesOrderNumber`.</span></span>  
  
     [!code-sql[IndexDDL#AlterIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex4)]  
  
#### <a name="to-modify-index-columns"></a><span data-ttu-id="c5fbc-128">若要修改索引資料行</span><span class="sxs-lookup"><span data-stu-id="c5fbc-128">To modify index columns</span></span>  
  
1.  <span data-ttu-id="c5fbc-129">若要加入、移除或變更索引資料行的位置，您必須卸除索引，再重新建立該索引。</span><span class="sxs-lookup"><span data-stu-id="c5fbc-129">To add, remove, or change the position of an index column, you must drop and recreate the index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5fbc-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5fbc-130">See Also</span></span>  
 <span data-ttu-id="c5fbc-131">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c5fbc-131">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="c5fbc-132">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c5fbc-132">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="c5fbc-133">[INDEXPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/indexproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c5fbc-133">[INDEXPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/indexproperty-transact-sql) </span></span>  
 <span data-ttu-id="c5fbc-134">[sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c5fbc-134">[sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) </span></span>  
 <span data-ttu-id="c5fbc-135">[sys.index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c5fbc-135">[sys.index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql) </span></span>  
 <span data-ttu-id="c5fbc-136">[設定索引選項](set-index-options.md) </span><span class="sxs-lookup"><span data-stu-id="c5fbc-136">[Set Index Options](set-index-options.md) </span></span>  
 [<span data-ttu-id="c5fbc-137">重新命名索引</span><span class="sxs-lookup"><span data-stu-id="c5fbc-137">Rename Indexes</span></span>](indexes.md)  
  
  
