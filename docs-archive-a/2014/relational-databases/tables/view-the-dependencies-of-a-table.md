---
title: 檢視資料表的相依性 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table dependencies [SQL Server]
- dependencies [SQL Server], tables
- displaying dependences
- viewing dependencies
ms.assetid: c4351ef5-e7d0-46e7-8367-88695e9974f8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 20f54b913124cdaa8a7dfeebac01ba070cc37d88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607326"
---
# <a name="view-the-dependencies-of-a-table"></a><span data-ttu-id="f03e8-102">檢視資料表的相依性</span><span class="sxs-lookup"><span data-stu-id="f03e8-102">View the Dependencies of a Table</span></span>
  <span data-ttu-id="f03e8-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中檢視資料表的相依性。</span><span class="sxs-lookup"><span data-stu-id="f03e8-103">You can view a table's dependencies in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f03e8-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="f03e8-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f03e8-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="f03e8-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f03e8-106">安全性</span><span class="sxs-lookup"><span data-stu-id="f03e8-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f03e8-107">**使用下列項目來檢視資料表的相依性：**</span><span class="sxs-lookup"><span data-stu-id="f03e8-107">**To view a table's dependencies, using:**</span></span>  
  
     [<span data-ttu-id="f03e8-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f03e8-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f03e8-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f03e8-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f03e8-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="f03e8-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f03e8-111">Security</span><span class="sxs-lookup"><span data-stu-id="f03e8-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f03e8-112">權限</span><span class="sxs-lookup"><span data-stu-id="f03e8-112">Permissions</span></span>  
 <span data-ttu-id="f03e8-113">需要資料庫的 VIEW DEFINITION 權限和資料庫之 sys.sql_expression_dependencies 的 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="f03e8-113">Requires VIEW DEFINITION permission on the database and SELECT permission on sys.sql_expression_dependencies for the database.</span></span> <span data-ttu-id="f03e8-114">根據預設，SELECT 權限只授與 db_owner 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="f03e8-114">By default, SELECT permission is granted only to members of the db_owner fixed database role.</span></span> <span data-ttu-id="f03e8-115">當 SELECT 和 VIEW DEFINITION 權限授與其他使用者時，被授與者就可以檢視資料庫中的所有相依性。</span><span class="sxs-lookup"><span data-stu-id="f03e8-115">When SELECT and VIEW DEFINITION permissions are granted to another user, the grantee can view all dependencies in the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f03e8-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f03e8-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-dependencies-of-a-table"></a><span data-ttu-id="f03e8-117">若要檢視資料表的相依性</span><span class="sxs-lookup"><span data-stu-id="f03e8-117">To view the dependencies of a table</span></span>  
  
1.  <span data-ttu-id="f03e8-118">在 **[物件總管]** 中，展開 **[資料庫]** 、展開其中一個資料庫，再展開 **[資料表]** 。</span><span class="sxs-lookup"><span data-stu-id="f03e8-118">In **Object Explorer**, expand **Databases**, expand a database, and then expand **Tables**.</span></span>  
  
2.  <span data-ttu-id="f03e8-119">以滑鼠右鍵按一下資料表，然後按一下 [檢視相依性]。</span><span class="sxs-lookup"><span data-stu-id="f03e8-119">Right-click a table, and then click **View Dependencies**.</span></span>  
  
3.  <span data-ttu-id="f03e8-120">在 [物件相依性] _\<object name>_ 對話方塊中，選取 [相依於] _\<object name>_ ，或 [所相依的物件] _\<object name>_ 。</span><span class="sxs-lookup"><span data-stu-id="f03e8-120">In the **Object Dependencies**_\<object name>_ dialog box, select either **Objects that depend on** _\<object name>_, or **Objects on which**_\<object name>_**depends**.</span></span>  
  
4.  <span data-ttu-id="f03e8-121">選取 **[相依性]** 方格中的物件。</span><span class="sxs-lookup"><span data-stu-id="f03e8-121">Select an object in the **Dependencies** grid.</span></span> <span data-ttu-id="f03e8-122">物件類型 (如「觸發程序」或「預存程序」) 會出現在 [類型] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="f03e8-122">The type of object (such as "Trigger" or "Stored Procedure"), appears in the **Type** box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f03e8-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f03e8-123">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-objects-that-depend-on-a-table"></a><span data-ttu-id="f03e8-124">若要檢視相依於資料表的物件</span><span class="sxs-lookup"><span data-stu-id="f03e8-124">To view the objects that depend on a table</span></span>  
  
1.  <span data-ttu-id="f03e8-125">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f03e8-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f03e8-126">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="f03e8-126">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f03e8-127">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="f03e8-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referencing_id = OBJECT_ID(N'Production.vProductAndDescription');   
    GO  
  
    ```  
  
#### <a name="to-view-the-objects-on-which-a-table-depends"></a><span data-ttu-id="f03e8-128">若要檢視資料表所相依的物件</span><span class="sxs-lookup"><span data-stu-id="f03e8-128">To view the objects on which a table depends</span></span>  
  
1.  <span data-ttu-id="f03e8-129">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f03e8-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f03e8-130">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="f03e8-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f03e8-131">下列範例會傳回相依於 `Production.Product`資料表的物件。</span><span class="sxs-lookup"><span data-stu-id="f03e8-131">The following example returns the objects that depend on the table `Production.Product`.</span></span> <span data-ttu-id="f03e8-132">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="f03e8-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referenced_id = OBJECT_ID(N'Production.Product');   
    GO  
  
    ```  
  
 <span data-ttu-id="f03e8-133">如需詳細資訊，請參閱 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="f03e8-133">For additional information, see [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)</span></span>  
  
  
