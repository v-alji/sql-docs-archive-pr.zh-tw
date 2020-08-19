---
title: 更新統計資料 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- updating statistics
- statistics [SQL Server], updating
ms.assetid: 4b97c0b4-03ff-4cfb-9c3f-3b33290b7a2c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 28491dda23c2ba9402e91dc051249f5bdcdf28d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599408"
---
# <a name="update-statistics"></a><span data-ttu-id="42802-102">更新統計資料</span><span class="sxs-lookup"><span data-stu-id="42802-102">Update Statistics</span></span>
  <span data-ttu-id="42802-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中針對資料表或索引檢視表更新查詢最佳化統計資料。</span><span class="sxs-lookup"><span data-stu-id="42802-103">You can update query optimization statistics on a table or indexed view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="42802-104">根據預設，查詢最佳化工具已經視需要更新統計資料，以便改善查詢計畫。不過，在某些情況下，您可以使用 UPDATE STATISTICS 或 `sp_updatestats` 預存程序，讓統計資料的更新頻率高於預設更新頻率，藉以改善查詢效能。</span><span class="sxs-lookup"><span data-stu-id="42802-104">By default, the query optimizer already updates statistics as necessary to improve the query plan; in some cases you can improve query performance by using UPDATE STATISTICS or the stored procedure `sp_updatestats` to update statistics more frequently than the default updates.</span></span>  
  
 <span data-ttu-id="42802-105">更新統計資料可確保查詢使用最新的統計資料進行編譯。</span><span class="sxs-lookup"><span data-stu-id="42802-105">Updating statistics ensures that queries compile with up-to-date statistics.</span></span> <span data-ttu-id="42802-106">不過，更新統計資料會導致查詢重新編譯。</span><span class="sxs-lookup"><span data-stu-id="42802-106">However, updating statistics causes queries to recompile.</span></span> <span data-ttu-id="42802-107">我們建議您不要太頻繁地更新統計資料，因為改善查詢計劃與重新編譯查詢所花費的時間之間具有效能權衡取捨。</span><span class="sxs-lookup"><span data-stu-id="42802-107">We recommend not updating statistics too frequently because there is a performance tradeoff between improving query plans and the time it takes to recompile queries.</span></span> <span data-ttu-id="42802-108">特定的權衡取捨完全取決於您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="42802-108">The specific tradeoffs depend on your application.</span></span> <span data-ttu-id="42802-109">UPDATE STATISTICS 可以使用 tempdb 來排序資料列的範例，以便建立統計資料。</span><span class="sxs-lookup"><span data-stu-id="42802-109">UPDATE STATISTICS can use tempdb to sort the sample of rows for building statistics.</span></span>  
  
 <span data-ttu-id="42802-110">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="42802-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="42802-111">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="42802-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="42802-112">安全性</span><span class="sxs-lookup"><span data-stu-id="42802-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="42802-113">**若要使用下列項目更新統計資料物件：**</span><span class="sxs-lookup"><span data-stu-id="42802-113">**To update a statistics object, using:**</span></span>  
  
     [<span data-ttu-id="42802-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="42802-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="42802-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="42802-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="42802-116">開始之前</span><span class="sxs-lookup"><span data-stu-id="42802-116">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="42802-117">Security</span><span class="sxs-lookup"><span data-stu-id="42802-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="42802-118">權限</span><span class="sxs-lookup"><span data-stu-id="42802-118">Permissions</span></span>  
 <span data-ttu-id="42802-119">如果使用 UPDATE STATISTICS 或透過 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]進行變更，需要資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="42802-119">If using UPDATE STATISTICS or making changes through [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], requires ALTER permission on the table or view.</span></span> <span data-ttu-id="42802-120">如果使用 `sp_updatestats`，需要 **系統管理員** 固定伺服器角色的成員資格或資料庫 (**dbo**) 的擁有權。</span><span class="sxs-lookup"><span data-stu-id="42802-120">If using `sp_updatestats`, requires membership in the **sysadmin** fixed server role, or ownership of the database (**dbo**).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="42802-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="42802-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-update-a-statistics-object"></a><span data-ttu-id="42802-122">若要更新統計資料物件</span><span class="sxs-lookup"><span data-stu-id="42802-122">To update a statistics object</span></span>  
  
1.  <span data-ttu-id="42802-123">在 **[物件總管]** 中，按一下加號展開要在其中更新統計資料的資料庫。</span><span class="sxs-lookup"><span data-stu-id="42802-123">In **Object Explorer**, click the plus sign to expand the database in which you want to update the statistic.</span></span>  
  
2.  <span data-ttu-id="42802-124">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="42802-124">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="42802-125">按一下加號展開要在其中更新統計資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="42802-125">Click the plus sign to expand the table in which you want to update the statistic.</span></span>  
  
4.  <span data-ttu-id="42802-126">按一下加號展開 **[統計資料]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="42802-126">Click the plus sign to expand the **Statistics** folder.</span></span>  
  
5.  <span data-ttu-id="42802-127">以滑鼠右鍵按一下要更新的統計資料物件，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="42802-127">Right-click the statistics object you wish to update and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="42802-128">在 [ **統計資料屬性-**_statistics_name_ ] 對話方塊中，選取 [ **更新這些資料行的統計資料** ] 核取方塊，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="42802-128">In the **Statistics Properties -**_statistics_name_ dialog box, select the **Update statistics for these columns** check box and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="42802-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="42802-129">Using Transact-SQL</span></span>  
  
#### <a name="to-update-a-specific-statistics-object"></a><span data-ttu-id="42802-130">若要更新特定的統計資料物件</span><span class="sxs-lookup"><span data-stu-id="42802-130">To update a specific statistics object</span></span>  
  
1.  <span data-ttu-id="42802-131">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="42802-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="42802-132">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="42802-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="42802-133">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="42802-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- The following example updates the statistics for the AK_SalesOrderDetail_rowguid index of the SalesOrderDetail table.   
    UPDATE STATISTICS Sales.SalesOrderDetail AK_SalesOrderDetail_rowguid;   
    GO  
    ```  
  
#### <a name="to-update-all-statistics-in-a-table"></a><span data-ttu-id="42802-134">若要更新資料表中的所有統計資料</span><span class="sxs-lookup"><span data-stu-id="42802-134">To update all statistics in a table</span></span>  
  
1.  <span data-ttu-id="42802-135">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="42802-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="42802-136">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="42802-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="42802-137">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="42802-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- The following example updates the statistics for all indexes on the SalesOrderDetail table.   
    UPDATE STATISTICS Sales.SalesOrderDetail;   
    GO  
    ```  
  
 <span data-ttu-id="42802-138">如需詳細資訊，請參閱 [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql)所建立的資料庫維護計畫。</span><span class="sxs-lookup"><span data-stu-id="42802-138">For more information, see [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql).</span></span>  
  
#### <a name="to-update-all-statistics-in-a-database"></a><span data-ttu-id="42802-139">若要更新資料庫中的所有統計資料</span><span class="sxs-lookup"><span data-stu-id="42802-139">To update all statistics in a database</span></span>  
  
1.  <span data-ttu-id="42802-140">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="42802-140">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="42802-141">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="42802-141">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="42802-142">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="42802-142">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- The following example updates the statistics for all tables in the database.   
    EXEC sp_updatestats;  
    ```  
  
 <span data-ttu-id="42802-143">如需詳細資訊，請參閱 [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="42802-143">For more information, see [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql).</span></span>  
  
  
