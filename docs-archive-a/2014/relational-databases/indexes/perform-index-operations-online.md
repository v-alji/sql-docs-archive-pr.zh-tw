---
title: 線上執行索引作業 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index online operations [SQL Server]
- online index operations
- ONLINE option
ms.assetid: 1e43537c-bf67-4db3-9908-3cb45c6fdaa1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4d09bd99a0eaec5fdb433bd8c33351d7622957a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606292"
---
# <a name="perform-index-operations-online"></a><span data-ttu-id="82fb5-102">線上執行索引作業</span><span class="sxs-lookup"><span data-stu-id="82fb5-102">Perform Index Operations Online</span></span>
  <span data-ttu-id="82fb5-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中線上建立、重建或卸除索引。</span><span class="sxs-lookup"><span data-stu-id="82fb5-103">This topic describes how to create, rebuild, or drop indexes online in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="82fb5-104">在這些索引作業期間，ONLINE 選項可讓並行使用者存取基礎資料表或叢集索引資料，以及任何關聯的非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="82fb5-104">The ONLINE option allows concurrent user access to the underlying table or clustered index data and any associated nonclustered indexes during these index operations.</span></span> <span data-ttu-id="82fb5-105">例如，當某個使用者正在重建叢集索引時，此使用者和其他人可以繼續更新和查詢基礎資料。</span><span class="sxs-lookup"><span data-stu-id="82fb5-105">For example, while a clustered index is being rebuilt by one user, that user and others can continue to update and query the underlying data.</span></span> <span data-ttu-id="82fb5-106">當您離線執行資料定義語言 (DDL) 作業 (例如建立或重建叢集索引) 時，這些作業會保有基礎資料和關聯索引的獨佔鎖定。</span><span class="sxs-lookup"><span data-stu-id="82fb5-106">When you perform data definition language (DDL) operations offline, such as building or rebuilding a clustered index; these operations hold exclusive locks on the underlying data and associated indexes.</span></span> <span data-ttu-id="82fb5-107">這可避免在索引作業完成之前對基礎資料進行修改和查詢。</span><span class="sxs-lookup"><span data-stu-id="82fb5-107">This prevents modifications and queries to the underlying data until the index operation is complete.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82fb5-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的所有版本都無法使用線上索引作業。</span><span class="sxs-lookup"><span data-stu-id="82fb5-108">Online index operations are not available in every [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] edition.</span></span> <span data-ttu-id="82fb5-109">如需詳細資訊，請參閱＜ [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)＞。</span><span class="sxs-lookup"><span data-stu-id="82fb5-109">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="82fb5-110">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="82fb5-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="82fb5-111">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="82fb5-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="82fb5-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="82fb5-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="82fb5-113">安全性</span><span class="sxs-lookup"><span data-stu-id="82fb5-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="82fb5-114">**若要線上重建索引，使用：**</span><span class="sxs-lookup"><span data-stu-id="82fb5-114">**To rebuild an index online, using:**</span></span>  
  
     [<span data-ttu-id="82fb5-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="82fb5-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="82fb5-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="82fb5-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="82fb5-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="82fb5-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="82fb5-118">限制事項</span><span class="sxs-lookup"><span data-stu-id="82fb5-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="82fb5-119">建議您針對全年無休的商務環境執行線上索引作業，在索引作業期間，這類環境的並行使用者活動需求相當重要。</span><span class="sxs-lookup"><span data-stu-id="82fb5-119">We recommend performing online index operations for business environments that operate 24 hours a day, seven days a week, in which the need for concurrent user activity during index operations is vital.</span></span>  
  
-   <span data-ttu-id="82fb5-120">ONLINE 選項可用於下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="82fb5-120">The ONLINE option is available in the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
    -   [<span data-ttu-id="82fb5-121">CREATE INDEX</span><span class="sxs-lookup"><span data-stu-id="82fb5-121">CREATE INDEX</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
    -   [<span data-ttu-id="82fb5-122">ALTER INDEX</span><span class="sxs-lookup"><span data-stu-id="82fb5-122">ALTER INDEX</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
    -   [<span data-ttu-id="82fb5-123">DROP INDEX</span><span class="sxs-lookup"><span data-stu-id="82fb5-123">DROP INDEX</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
    -   <span data-ttu-id="82fb5-124">[ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) (搭配 CLUSTERED 索引選項時，用來加入或卸除 UNIQUE 或 PRIMARY KEY 條件約束)</span><span class="sxs-lookup"><span data-stu-id="82fb5-124">[ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) (To add or drop UNIQUE or PRIMARY KEY constraints with CLUSTERED index option)</span></span>  
  
-   <span data-ttu-id="82fb5-125">如需更多有關線上建立、重建或卸除索引的限制，請參閱 [線上索引作業的指導方針](guidelines-for-online-index-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="82fb5-125">For more limitations and restrictions concerning creating, rebuilding, or dropping indexes online, see [Guidelines for Online Index Operations](guidelines-for-online-index-operations.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="82fb5-126">Security</span><span class="sxs-lookup"><span data-stu-id="82fb5-126">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="82fb5-127">權限</span><span class="sxs-lookup"><span data-stu-id="82fb5-127">Permissions</span></span>  
 <span data-ttu-id="82fb5-128">需要資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="82fb5-128">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="82fb5-129">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="82fb5-129">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rebuild-an-index-online"></a><span data-ttu-id="82fb5-130">若要線上重建索引</span><span class="sxs-lookup"><span data-stu-id="82fb5-130">To rebuild an index online</span></span>  
  
1.  <span data-ttu-id="82fb5-131">在 [物件總管] 中，按一下加號展開包含您要線上重建索引之資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="82fb5-131">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to rebuild an index online.</span></span>  
  
2.  <span data-ttu-id="82fb5-132">展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="82fb5-132">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="82fb5-133">按一下加號展開要線上重建索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="82fb5-133">Click the plus sign to expand the table on which you want to rebuild an index online.</span></span>  
  
4.  <span data-ttu-id="82fb5-134">展開 **[索引]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="82fb5-134">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="82fb5-135">以滑鼠右鍵按一下要線上重建的索引，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="82fb5-135">Right-click the index that you want to rebuild online and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="82fb5-136">在 **[選取頁面]** 底下，選取 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="82fb5-136">Under **Select a page**, select **Options**.</span></span>  
  
7.  <span data-ttu-id="82fb5-137">選取 **[允許線上 DML 處理]** ，然後從清單中選取 **[True]** 。</span><span class="sxs-lookup"><span data-stu-id="82fb5-137">Select **Allow online DML processing**, and then select **True** from the list.</span></span>  
  
8.  <span data-ttu-id="82fb5-138">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="82fb5-138">Click **OK**.</span></span>  
  
9. <span data-ttu-id="82fb5-139">以滑鼠右鍵按一下要線上重建的索引，然後選取 [重建]。</span><span class="sxs-lookup"><span data-stu-id="82fb5-139">Right-click the index that you want to rebuild online and select **Rebuild**.</span></span>  
  
10. <span data-ttu-id="82fb5-140">在 **[重建索引]** 對話方塊中，確認 **[要重建的索引]** 方格中有正確索引，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="82fb5-140">In the **Rebuild Indexes** dialog box, verify that the correct index is in the **Indexes to rebuild** grid and click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="82fb5-141">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="82fb5-141">Using Transact-SQL</span></span>  
  
#### <a name="to-create-rebuild-or-drop-an-index-online"></a><span data-ttu-id="82fb5-142">若要線上建立、重建或卸除索引</span><span class="sxs-lookup"><span data-stu-id="82fb5-142">To create, rebuild, or drop an index online</span></span>  
  
1.  <span data-ttu-id="82fb5-143">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="82fb5-143">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="82fb5-144">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="82fb5-144">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="82fb5-145">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="82fb5-145">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="82fb5-146">這個範例會線上重建現有索引</span><span class="sxs-lookup"><span data-stu-id="82fb5-146">The example rebuilds an existing online</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER INDEX AK_Employee_NationalIDNumber ON HumanResources.Employee  
    REBUILD WITH (ONLINE = ON);  
    GO  
    ```  
  
     <span data-ttu-id="82fb5-147">下列範例會在線上刪除叢集索引，並利用 `NewGroup` 子句，將產生的資料表 (堆積) 移到 `MOVE TO` 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="82fb5-147">The following example deletes a clustered index online and moves the resulting table (heap) to the filegroup `NewGroup` by using the `MOVE TO` clause.</span></span> <span data-ttu-id="82fb5-148">它會查詢 `sys.indexes`、 `sys.tables`和 `sys.filegroups` 目錄檢視來確認在移動之前和之後，索引和資料表在檔案群組中的位置。</span><span class="sxs-lookup"><span data-stu-id="82fb5-148">The `sys.indexes`, `sys.tables`, and `sys.filegroups` catalog views are queried to verify the index and table placement in the filegroups before and after the move.</span></span>  
  
     [!code-sql[IndexDDL#DropIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/dropindex.sql#dropindex4)]  
  
 <span data-ttu-id="82fb5-149">如需詳細資訊，請參閱 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="82fb5-149">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
