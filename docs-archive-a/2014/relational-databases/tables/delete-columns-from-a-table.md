---
title: 從資料表中刪除資料行 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], deleting
- removing columns
- deleting columns
- dropping columns
ms.assetid: 0d8f6e4f-bc71-4fa3-8615-74249c8e072d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 62f9bca8ee53ae97bb1ac7f37e597b7814a0c370
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597034"
---
# <a name="delete-columns-from-a-table"></a><span data-ttu-id="8dfa2-102">從資料表中刪除資料行</span><span class="sxs-lookup"><span data-stu-id="8dfa2-102">Delete Columns from a Table</span></span>
  <span data-ttu-id="8dfa2-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中刪除資料表資料行。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-103">This topic describes how to delete table columns in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="8dfa2-104">當您從資料表中刪除資料行時，就會從資料庫中刪除該資料行以及它所包含的所有資料。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-104">When you delete a column from a table, it and all the data it contains are deleted from the database.</span></span> <span data-ttu-id="8dfa2-105">此動作無法復原。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-105">This action cannot be undone.</span></span>  
  
 <span data-ttu-id="8dfa2-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="8dfa2-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8dfa2-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="8dfa2-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8dfa2-108">限制事項</span><span class="sxs-lookup"><span data-stu-id="8dfa2-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="8dfa2-109">安全性</span><span class="sxs-lookup"><span data-stu-id="8dfa2-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8dfa2-110">**若要使用下列項目從資料表中刪除資料行：**</span><span class="sxs-lookup"><span data-stu-id="8dfa2-110">**To delete a column from a table, using:**</span></span>  
  
     [<span data-ttu-id="8dfa2-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8dfa2-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8dfa2-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8dfa2-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8dfa2-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="8dfa2-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8dfa2-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="8dfa2-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="8dfa2-115">您無法刪除具有 CHECK 條件約束的資料行。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-115">You cannot delete a column that has a CHECK constraint.</span></span> <span data-ttu-id="8dfa2-116">您必須先刪除條件約束。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-116">You must first delete the constraint.</span></span>  
  
 <span data-ttu-id="8dfa2-117">除非使用資料表設計工具，否則您無法刪除具有 PRIMARY KEY 或 FOREIGN KEY 條件約束或其他相依性的資料行。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-117">You cannot delete a column that has PRIMARY KEY or FOREIGN KEY constraints or other dependencies except when using the Table Designer.</span></span> <span data-ttu-id="8dfa2-118">使用 [物件總管] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]時，您必須先移除資料行的所有相依性。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-118">When using Object Explorer or [!INCLUDE[tsql](../../includes/tsql-md.md)], you must first remove all dependencies on the column.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8dfa2-119">Security</span><span class="sxs-lookup"><span data-stu-id="8dfa2-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8dfa2-120">權限</span><span class="sxs-lookup"><span data-stu-id="8dfa2-120">Permissions</span></span>  
 <span data-ttu-id="8dfa2-121">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-121">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8dfa2-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8dfa2-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-columns-by-using-object-explorer"></a><span data-ttu-id="8dfa2-123">若要使用物件總管來刪除資料行</span><span class="sxs-lookup"><span data-stu-id="8dfa2-123">To delete columns by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="8dfa2-124">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8dfa2-125">在**物件總管**中，以滑鼠右鍵按一下您想要從中刪除資料行的資料表，然後選擇 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-125">In **Object Explorer**, right-click the table from which you want to delete columns and choose **Delete**.</span></span>  
  
3.  <span data-ttu-id="8dfa2-126">在 **[刪除物件]** 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-126">In **Delete Object** dialog box, click **OK**.</span></span>  
  
 <span data-ttu-id="8dfa2-127">如果資料行包含條件約束或其他相依性， **[刪除物件]** 對話方塊將會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-127">If the column contains constraints or other dependencies, an error message will display in the **Delete Object** dialog box.</span></span> <span data-ttu-id="8dfa2-128">請刪除參考的條件約束，藉以解決此錯誤。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-128">Resolve the error by deleting the referenced constraints.</span></span>  
  
#### <a name="to-delete-columns-by-using-table-designer"></a><span data-ttu-id="8dfa2-129">若要使用資料表設計工具來刪除資料行</span><span class="sxs-lookup"><span data-stu-id="8dfa2-129">To delete columns by using Table Designer</span></span>  
  
1.  <span data-ttu-id="8dfa2-130">在**物件總管**中，以滑鼠右鍵按一下您想要從中刪除資料行的資料表，然後選擇 [設計]  。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-130">In **Object Explorer**, right-click the table from which you want to delete columns and choose **Design**.</span></span>  
  
2.  <span data-ttu-id="8dfa2-131">以滑鼠右鍵按一下您想要刪除的資料行，然後從捷徑功能表中選擇 [刪除資料行]  。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-131">Right-click the column you want to delete and choose **Delete Column** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="8dfa2-132">如果資料行參與關聯性 (FOREIGN KEY 或 PRIMARY KEY)，則會有訊息提示您確認是否要刪除選取的資料行及其關聯性。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-132">If the column participates in a relationship (FOREIGN KEY or PRIMARY KEY), a message prompts you to confirm the deletion of the selected columns and their relationships.</span></span> <span data-ttu-id="8dfa2-133">選擇 [是]  。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-133">Choose **Yes**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8dfa2-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8dfa2-134">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-columns"></a><span data-ttu-id="8dfa2-135">若要刪除資料行</span><span class="sxs-lookup"><span data-stu-id="8dfa2-135">To delete columns</span></span>  
  
1.  <span data-ttu-id="8dfa2-136">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8dfa2-137">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8dfa2-138">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-138">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE dbo.doc_exb DROP COLUMN column_b ;  
    ```  
  
 <span data-ttu-id="8dfa2-139">如果資料行包含條件約束或其他相依性，將會傳回錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-139">If the column contains constraints or other dependencies, an error message will be returned.</span></span> <span data-ttu-id="8dfa2-140">請刪除參考的條件約束，藉以解決此錯誤。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-140">Resolve the error by deleting the referenced constraints.</span></span>  
  
 <span data-ttu-id="8dfa2-141">如需其他範例，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8dfa2-141">For additional examples, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
##  <a name="FollowUp"></a>  
