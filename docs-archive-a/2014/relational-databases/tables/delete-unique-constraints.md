---
title: 刪除唯一的條件約束 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing constraints
- UNIQUE constraints [SQL Server], deleting
- constraints [SQL Server], deleting
- deleting constraints
- constraints [SQL Server], unique
ms.assetid: 71e563fc-f5d7-4c2e-a42f-f0695a831f32
author: stevestein
ms.author: sstein
ms.openlocfilehash: f2fe2264aed4eb2f292a6bd1e4e565cebe2a833f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597702"
---
# <a name="delete-unique-constraints"></a><span data-ttu-id="34397-102">刪除唯一的條件約束</span><span class="sxs-lookup"><span data-stu-id="34397-102">Delete Unique Constraints</span></span>
  <span data-ttu-id="34397-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中刪除唯一條件約束。</span><span class="sxs-lookup"><span data-stu-id="34397-103">You can delete a unique constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="34397-104">刪除唯一條件約束會移除條件約束運算式所包含之資料行或資料行組合中輸入值的唯一性要求，並且刪除對應的唯一索引。</span><span class="sxs-lookup"><span data-stu-id="34397-104">Deleting a unique constraint removes the requirement for uniqueness for values entered in the column or combination of columns included in the constraint expression and deletes the corresponding unique index.</span></span>  
  
 <span data-ttu-id="34397-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="34397-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="34397-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="34397-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="34397-107">安全性</span><span class="sxs-lookup"><span data-stu-id="34397-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="34397-108">**若要使用下列項目來刪除唯一條件約束：**</span><span class="sxs-lookup"><span data-stu-id="34397-108">**To delete a unique constraint, using:**</span></span>  
  
     [<span data-ttu-id="34397-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="34397-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="34397-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="34397-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="34397-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="34397-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="34397-112">Security</span><span class="sxs-lookup"><span data-stu-id="34397-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="34397-113">權限</span><span class="sxs-lookup"><span data-stu-id="34397-113">Permissions</span></span>  
 <span data-ttu-id="34397-114">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="34397-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="34397-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="34397-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-unique-constraint-using-object-explorer"></a><span data-ttu-id="34397-116">若要使用物件總管來刪除唯一條件約束</span><span class="sxs-lookup"><span data-stu-id="34397-116">To delete a unique constraint using Object Explorer</span></span>  
  
1.  <span data-ttu-id="34397-117">在 [物件總管] 中，展開包含唯一條件約束的資料表，然後展開 **[條件約束]** 。</span><span class="sxs-lookup"><span data-stu-id="34397-117">In Object Explorer, expand the table that contains the unique constraint and then expand **Constraints**.</span></span>  
  
2.  <span data-ttu-id="34397-118">以滑鼠右鍵按一下索引鍵，然後選取 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="34397-118">Right-click the key and select **Delete**.</span></span>  
  
3.  <span data-ttu-id="34397-119">在 **[刪除物件]** 對話方塊中，確認指定了正確的索引鍵，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="34397-119">In the **Delete Object** dialog box, verify the correct key is specified and click **OK**.</span></span>  
  
#### <a name="to-delete-a-unique-constraint-using-table-designer"></a><span data-ttu-id="34397-120">若要使用資料表設計工具來刪除唯一條件約束</span><span class="sxs-lookup"><span data-stu-id="34397-120">To delete a unique constraint using Table Designer</span></span>  
  
1.  <span data-ttu-id="34397-121">在物件總管  中，以滑鼠右鍵按一下含有唯一條件約束的資料表，然後按一下 [設計]  。</span><span class="sxs-lookup"><span data-stu-id="34397-121">In **Object Explorer**, right-click the table with the unique constraint, and click **Design**.</span></span>  
  
2.  <span data-ttu-id="34397-122">在 [資料表設計工具]  功能表上，按一下 [索引/索引鍵]  。</span><span class="sxs-lookup"><span data-stu-id="34397-122">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
3.  <span data-ttu-id="34397-123">在 [索引/索引鍵]  對話方塊中，從 [選取的主/唯一索引鍵和索引]  清單中選取唯一索引鍵。</span><span class="sxs-lookup"><span data-stu-id="34397-123">In the **Indexes/Keys** dialog box, select the unique key in the **Selected Primary/Unique Key and Index** list.</span></span>  
  
4.  <span data-ttu-id="34397-124">按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="34397-124">Click **Delete**.</span></span>  
  
5.  <span data-ttu-id="34397-125">在 [檔案]  功能表上，按一下 [儲存「資料表名稱」  ]  。</span><span class="sxs-lookup"><span data-stu-id="34397-125">On the **File** menu, click **Save** _table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="34397-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="34397-126">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-unique-constraint"></a><span data-ttu-id="34397-127">若要刪除唯一條件約束</span><span class="sxs-lookup"><span data-stu-id="34397-127">To delete a unique constraint</span></span>  
  
1.  <span data-ttu-id="34397-128">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="34397-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="34397-129">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="34397-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="34397-130">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="34397-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Return the name of unique constraint.  
    SELECT name  
    FROM sys.objects  
    WHERE type = 'UQ' AND OBJECT_NAME(parent_object_id) = N' DocExc';  
    GO  
    -- Delete the unique constraint.  
    ALTER TABLE dbo.DocExc   
    DROP CONSTRAINT UNQ_ColumnB_DocExc;  
    GO  
    ```  
  
 <span data-ttu-id="34397-131">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) 和 [sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="34397-131">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) and [sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
