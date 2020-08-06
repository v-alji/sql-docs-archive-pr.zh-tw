---
title: 檢視定序資訊 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- collations [SQL Server], view
ms.assetid: 1338b4ea-7142-44bc-a3b9-44e54431405f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 995e559cfd7ca871f5abd90751f2f79167bdf76f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606892"
---
# <a name="view-collation-information"></a><span data-ttu-id="267fb-102">檢視定序資訊</span><span class="sxs-lookup"><span data-stu-id="267fb-102">View Collation Information</span></span>
    
##  <a name="you-can-view-the-collation-of-a-server-database-or-column-in-ssmanstudiofull-using-object-explorer-menu-options-or-by-using-tsql"></a><a name="Top"></a> <span data-ttu-id="267fb-103">您可以使用 [物件總管] 功能表選項或使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視伺服器、資料庫或資料行的定序。</span><span class="sxs-lookup"><span data-stu-id="267fb-103">You can view the collation of a server, database, or column in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] using Object Explorer menu options or by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
##  <a name="how-to-view-a-collation-setting"></a><a name="Procedures"></a> <span data-ttu-id="267fb-104">如何檢視定序設定</span><span class="sxs-lookup"><span data-stu-id="267fb-104">How to View a Collation Setting</span></span>  
 <span data-ttu-id="267fb-105">您可以使用下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="267fb-105">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="267fb-106">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="267fb-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="267fb-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="267fb-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="267fb-108">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="267fb-108">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="267fb-109">**在 [物件總管] 中檢視伺服器 (SQL Server 執行個體) 的定序設定**</span><span class="sxs-lookup"><span data-stu-id="267fb-109">**To view a collation setting for a server (instance of SQL Server) in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="267fb-110">在 [物件總管] 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="267fb-110">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="267fb-111">在執行個體上按一下滑鼠右鍵，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="267fb-111">Right-click the instance and select **Properties**.</span></span>  
  
 <span data-ttu-id="267fb-112">**在 [物件總管] 中檢視資料庫的定序設定**</span><span class="sxs-lookup"><span data-stu-id="267fb-112">**To view a collation setting for a database in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="267fb-113">在物件總管中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="267fb-113">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="267fb-114">展開 [資料庫]  ，然後在資料庫上按一下滑鼠右鍵，再選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="267fb-114">Expand **Databases**, right-click the database and select **Properties**.</span></span>  
  
 <span data-ttu-id="267fb-115">**在 [物件總管] 中檢視資料行的定序設定**</span><span class="sxs-lookup"><span data-stu-id="267fb-115">**To view a collation setting for a column in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="267fb-116">在物件總管中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="267fb-116">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="267fb-117">依序展開 **[資料庫]** 、特定資料庫及 **[資料表]** 。</span><span class="sxs-lookup"><span data-stu-id="267fb-117">Expand **Databases**, expand the database and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="267fb-118">展開包含資料行的資料表，然後展開 **[資料行]** 。</span><span class="sxs-lookup"><span data-stu-id="267fb-118">Expand the table that contains the column and then expand **Columns**.</span></span>  
  
4.  <span data-ttu-id="267fb-119">在資料行上按一下滑鼠右鍵，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="267fb-119">Right-click the column and select **Properties**.</span></span> <span data-ttu-id="267fb-120">如果定序屬性為空白，則資料行不是字元資料類型。</span><span class="sxs-lookup"><span data-stu-id="267fb-120">If the collation property is empty, the column is not a character data type.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="267fb-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="267fb-121">Using Transact-SQL</span></span>  
 <span data-ttu-id="267fb-122">**檢視伺服器的定序設定**</span><span class="sxs-lookup"><span data-stu-id="267fb-122">**To view the collation setting of a server**</span></span>  
  
1.  <span data-ttu-id="267fb-123">在 [物件總管] 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後在工具列上按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="267fb-123">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and on the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="267fb-124">在查詢視窗中，輸入下列使用 SERVERPROPERTY 系統函數的陳述式。</span><span class="sxs-lookup"><span data-stu-id="267fb-124">In the query window, enter the following statement that uses the SERVERPROPERTY system function.</span></span>  
  
    ```  
    SELECT CONVERT (varchar, SERVERPROPERTY('collation'));  
    ```  
  
3.  <span data-ttu-id="267fb-125">或者，您可以使用 sp_helpsort 系統預存程序。</span><span class="sxs-lookup"><span data-stu-id="267fb-125">Alternatively, you can use the sp_helpsort system stored procedure.</span></span>  
  
    ```  
    EXECUTE sp_helpsort;  
    ```  
  
 <span data-ttu-id="267fb-126">**檢視 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="267fb-126">**To view all collations supported by [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**</span></span>  
  
1.  <span data-ttu-id="267fb-127">在 [物件總管] 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後在工具列上按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="267fb-127">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and on the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="267fb-128">在查詢視窗中，輸入下列使用 SERVERPROPERTY 系統函數的陳述式。</span><span class="sxs-lookup"><span data-stu-id="267fb-128">In the query window, enter the following statement that uses the SERVERPROPERTY system function.</span></span>  
  
    ```  
    SELECT name, description FROM sys.fn_helpcollations();  
    ```  
  
 <span data-ttu-id="267fb-129">**檢視資料庫的定序設定**</span><span class="sxs-lookup"><span data-stu-id="267fb-129">**To view the collation setting of a database**</span></span>  
  
1.  <span data-ttu-id="267fb-130">在 [物件總管] 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後在工具列上按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="267fb-130">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and on the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="267fb-131">在查詢視窗中，輸入下列使用 sys.databases 系統目錄檢視的陳述式。</span><span class="sxs-lookup"><span data-stu-id="267fb-131">In the query window, enter the following statement that uses the sys.databases system catalog view.</span></span>  
  
    ```  
    SELECT name, collation_name FROM sys.databases;  
    ```  
  
3.  <span data-ttu-id="267fb-132">或者，您可以使用 DATABASEPROPERTYEX 系統函數。</span><span class="sxs-lookup"><span data-stu-id="267fb-132">Alternatively, you can use the DATABASEPROPERTYEX system function.</span></span>  
  
    ```  
    SELECT CONVERT (varchar, DATABASEPROPERTYEX('database_name','collation'));  
    ```  
  
 <span data-ttu-id="267fb-133">**檢視資料行的定序設定**</span><span class="sxs-lookup"><span data-stu-id="267fb-133">**To view the collation setting of a column**</span></span>  
  
1.  <span data-ttu-id="267fb-134">在 [物件總管] 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後在工具列上按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="267fb-134">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and on the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="267fb-135">在查詢視窗中，輸入下列使用 sys.columns 系統目錄檢視的陳述式。</span><span class="sxs-lookup"><span data-stu-id="267fb-135">In the query window, enter the following statement that uses the sys.columns system catalog view.</span></span>  
  
    ```  
    SELECT name, collation_name FROM sys.columns WHERE name = N'<insert character data type column name>';  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="267fb-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="267fb-136">See Also</span></span>  
 <span data-ttu-id="267fb-137">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="267fb-137">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span></span>  
 <span data-ttu-id="267fb-138">[sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="267fb-138">[sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) </span></span>  
 <span data-ttu-id="267fb-139">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="267fb-139">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="267fb-140">[sys.columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="267fb-140">[sys.columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql) </span></span>  
 <span data-ttu-id="267fb-141">[定序優先順序 &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="267fb-141">[Collation Precedence &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql) </span></span>  
 [<span data-ttu-id="267fb-142">sp_helpsort &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="267fb-142">sp_helpsort &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-helpsort-transact-sql)  
  
  
