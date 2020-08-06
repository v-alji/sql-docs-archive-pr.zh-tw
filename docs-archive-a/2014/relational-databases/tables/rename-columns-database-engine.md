---
title: 重新命名資料行 (Database Engine) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], names
- renaming columns
- column names [SQL Server]
ms.assetid: 7c71ec9f-0180-4398-b32a-4bfb7592e75d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6871ab82eaa17aa5e392e6b2bb3f5c60058f9af9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598762"
---
# <a name="rename-columns-database-engine"></a><span data-ttu-id="ed140-102">重新命名資料行 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="ed140-102">Rename Columns (Database Engine)</span></span>
  <span data-ttu-id="ed140-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中重新命名資料表資料行。</span><span class="sxs-lookup"><span data-stu-id="ed140-103">You can rename a table column in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ed140-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="ed140-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ed140-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="ed140-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ed140-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="ed140-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ed140-107">安全性</span><span class="sxs-lookup"><span data-stu-id="ed140-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ed140-108">**若要使用下列項目來重新命名資料行：**</span><span class="sxs-lookup"><span data-stu-id="ed140-108">**To rename columns, using:**</span></span>  
  
     [<span data-ttu-id="ed140-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ed140-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ed140-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ed140-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ed140-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="ed140-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ed140-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="ed140-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ed140-113">重新命名資料行不會自動重新命名該資料行的參考。</span><span class="sxs-lookup"><span data-stu-id="ed140-113">Renaming a column will not automatically rename references to that column.</span></span> <span data-ttu-id="ed140-114">您必須手動修改任何參考重新命名之資料行的物件。</span><span class="sxs-lookup"><span data-stu-id="ed140-114">You must modify any objects that reference the renamed column manually.</span></span> <span data-ttu-id="ed140-115">例如，如果您重新命名資料表資料行，且有觸發程序參考這個資料行，您必須修改觸發程序來反映新的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="ed140-115">For example, if you rename a table column and that column is referenced in a trigger, you must modify the trigger to reflect the new column name.</span></span> <span data-ttu-id="ed140-116">在重新命名物件之前，請利用 [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) 來列出其相依性。</span><span class="sxs-lookup"><span data-stu-id="ed140-116">Use [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) to list dependencies on the object before renaming it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ed140-117">Security</span><span class="sxs-lookup"><span data-stu-id="ed140-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ed140-118">權限</span><span class="sxs-lookup"><span data-stu-id="ed140-118">Permissions</span></span>  
 <span data-ttu-id="ed140-119">需要物件的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="ed140-119">Requires ALTER permission on the object.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ed140-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ed140-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-column-using-object-explorer"></a><span data-ttu-id="ed140-121">若要使用物件總管來重新命名資料行</span><span class="sxs-lookup"><span data-stu-id="ed140-121">To rename a column using Object Explorer</span></span>  
  
1.  <span data-ttu-id="ed140-122">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ed140-122">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ed140-123">在物件總管  中，以滑鼠右鍵按一下您想要重新命名資料行的資料表，然後選擇 [重新命名]  。</span><span class="sxs-lookup"><span data-stu-id="ed140-123">In **Object Explorer**, right-click the table in which you want to rename columns and choose **Rename**.</span></span>  
  
3.  <span data-ttu-id="ed140-124">輸入新的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="ed140-124">Type a new column name.</span></span>  
  
#### <a name="to-rename-a-column-using-table-designer"></a><span data-ttu-id="ed140-125">若要使用資料表設計工具來重新命名資料行</span><span class="sxs-lookup"><span data-stu-id="ed140-125">To rename a column using Table Designer</span></span>  
  
1.  <span data-ttu-id="ed140-126">在物件總管  中，以滑鼠右鍵按一下您想要重新命名資料行的資料表，然後選擇 [設計]  。</span><span class="sxs-lookup"><span data-stu-id="ed140-126">In **Object Explorer**, right-click the table to which you want to rename columns and choose **Design**.</span></span>  
  
2.  <span data-ttu-id="ed140-127">在 **[資料行名稱]** 下，選取您要變更的名稱，並輸入新名稱。</span><span class="sxs-lookup"><span data-stu-id="ed140-127">Under **Column Name**, select the name you want to change and type a new one.</span></span>  
  
3.  <span data-ttu-id="ed140-128">在 [檔案] \*\*\*\* 功能表上，按一下 [儲存「資料表名稱」__]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ed140-128">On the **File** menu, click **Save**_table name_.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ed140-129">您也可以在 **[資料行屬性]** 索引標籤中變更資料行的名稱。請選取您要變更名稱的資料行，並輸入新的 **[名稱]** 值。</span><span class="sxs-lookup"><span data-stu-id="ed140-129">You can also change the name of a column in the **Column Properties** tab. Select the column whose name you want to change and type a new value for **Name**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ed140-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ed140-130">Using Transact-SQL</span></span>  
 <span data-ttu-id="ed140-131">**若要重新命名資料行**</span><span class="sxs-lookup"><span data-stu-id="ed140-131">**To rename a column**</span></span>  
  
#### <a name="to-rename-a-column"></a><span data-ttu-id="ed140-132">重新命名資料行</span><span class="sxs-lookup"><span data-stu-id="ed140-132">To rename a column</span></span>  
  
1.  <span data-ttu-id="ed140-133">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ed140-133">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ed140-134">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="ed140-134">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ed140-135">下列範例會將 `TerritoryID` 資料表中的 `Sales.SalesTerritory` 資料行重新命名為 `TerrID`。</span><span class="sxs-lookup"><span data-stu-id="ed140-135">The following example renames the column `TerritoryID` in the table `Sales.SalesTerritory` to `TerrID`.</span></span> <span data-ttu-id="ed140-136">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="ed140-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_rename 'Sales.SalesTerritory.TerritoryID', 'TerrID', 'COLUMN';  
    GO  
    ```  
  
 <span data-ttu-id="ed140-137">如需詳細資訊，請參閱 [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ed140-137">For more information, see [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).</span></span>  
  
  
