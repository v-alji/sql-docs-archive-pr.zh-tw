---
title: 重新命名資料表 (Database Engine) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table renaming [SQL Server]
- table names [SQL Server]
- tables [SQL Server], Visual Database Tools
- renaming tables
ms.assetid: 2f5c922d-4d71-4694-9fca-28dd99375799
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6e73bbb92d8fd3fdcaa7756ce1dcb74d8cd598b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598759"
---
# <a name="rename-tables-database-engine"></a><span data-ttu-id="42672-102">重新命名資料表 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="42672-102">Rename Tables (Database Engine)</span></span>
  <span data-ttu-id="42672-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中重新命名資料表。</span><span class="sxs-lookup"><span data-stu-id="42672-103">You can rename a table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="42672-104">在重新命名資料表之前請仔細考慮。</span><span class="sxs-lookup"><span data-stu-id="42672-104">Think carefully before you rename a table.</span></span> <span data-ttu-id="42672-105">如果現有的查詢、檢視表、使用者定義函數、預存程序或程式參考此資料表，則名稱修改將會使這些物件失效。</span><span class="sxs-lookup"><span data-stu-id="42672-105">If existing queries, views, user-defined functions, stored procedures, or programs refer to that table, the name modification will make these objects invalid.</span></span>  
  
 <span data-ttu-id="42672-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="42672-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="42672-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="42672-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="42672-108">限制事項</span><span class="sxs-lookup"><span data-stu-id="42672-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="42672-109">安全性</span><span class="sxs-lookup"><span data-stu-id="42672-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="42672-110">**若要使用下列項目來重新命名資料表：**</span><span class="sxs-lookup"><span data-stu-id="42672-110">**To rename a table, using:**</span></span>  
  
     [<span data-ttu-id="42672-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="42672-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="42672-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="42672-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="42672-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="42672-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="42672-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="42672-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="42672-115">重新命名資料表不會自動重新命名該資料表的參考。</span><span class="sxs-lookup"><span data-stu-id="42672-115">Renaming a table will not automatically rename references to that table.</span></span> <span data-ttu-id="42672-116">您必須手動修改任何參考重新命名之資料表的物件。</span><span class="sxs-lookup"><span data-stu-id="42672-116">You must manually modify any objects that reference the renamed table.</span></span> <span data-ttu-id="42672-117">例如，如果您重新命名了資料表，而且觸發程序參考該資料表，您就必須修改觸發程序來反映新的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="42672-117">For example, if you rename a table and that table is referenced in a trigger, you must modify the trigger to reflect the new table name.</span></span> <span data-ttu-id="42672-118">在重新命名資料表之前，請使用 [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) 列出其相依性。</span><span class="sxs-lookup"><span data-stu-id="42672-118">Use [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) to list dependencies on the table before renaming it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="42672-119">Security</span><span class="sxs-lookup"><span data-stu-id="42672-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="42672-120">權限</span><span class="sxs-lookup"><span data-stu-id="42672-120">Permissions</span></span>  
 <span data-ttu-id="42672-121">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="42672-121">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="42672-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="42672-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-table"></a><span data-ttu-id="42672-123">重新命名資料表</span><span class="sxs-lookup"><span data-stu-id="42672-123">To rename a table</span></span>  
  
1.  <span data-ttu-id="42672-124">在物件總管中，以滑鼠右鍵按一下想要重新命名的資料表，然後從快速鍵功能表選擇 [設計]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="42672-124">In Object Explorer, right-click the table you want to rename and choose **Design** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="42672-125">從 **[檢視]** 功能表中選擇 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="42672-125">From the **View** menu, choose **Properties**.</span></span>  
  
3.  <span data-ttu-id="42672-126">在 **[屬性]** 視窗中的 **[名稱]** 值欄位中，輸入資料表的新名稱。</span><span class="sxs-lookup"><span data-stu-id="42672-126">In the field for the **Name** value in the **Properties** window, type a new name for the table.</span></span>  
  
4.  <span data-ttu-id="42672-127">若要取消這個動作，請在離開這個欄位之前按 ESC 鍵。</span><span class="sxs-lookup"><span data-stu-id="42672-127">To cancel this action, press the ESC key before leaving this field.</span></span>  
  
5.  <span data-ttu-id="42672-128">從 [檔案 **] 功能表中，選擇 [** **儲存**_資料表名稱_]。</span><span class="sxs-lookup"><span data-stu-id="42672-128">From the **File** menu choose **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="42672-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="42672-129">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-a-table"></a><span data-ttu-id="42672-130">重新命名資料表</span><span class="sxs-lookup"><span data-stu-id="42672-130">To rename a table</span></span>  
  
1.  <span data-ttu-id="42672-131">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="42672-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="42672-132">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="42672-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="42672-133">下列範例會將 `SalesTerritory` 資料表重新命名為 `SalesTerr` 結構描述中的 `Sales` 。</span><span class="sxs-lookup"><span data-stu-id="42672-133">The following example renames the `SalesTerritory` table to `SalesTerr` in the `Sales` schema.</span></span> <span data-ttu-id="42672-134">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="42672-134">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    EXEC sp_rename 'Sales.SalesTerritory', 'SalesTerr';  
    ```  
  
 <span data-ttu-id="42672-135">如需其他範例，請參閱 [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="42672-135">For additional examples, see [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).</span></span>  
  
  
