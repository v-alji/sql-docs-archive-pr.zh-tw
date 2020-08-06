---
title: 刪除主索引鍵 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing primary keys
- deleting primary keys
- primary keys [SQL Server], deleting
ms.assetid: c472e465-7bdd-4d74-8fc9-e47fca007ccb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 44fa1271143f813364bfd2109f8147f1d04294a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607332"
---
# <a name="delete-primary-keys"></a><span data-ttu-id="e6e09-102">刪除主索引鍵</span><span class="sxs-lookup"><span data-stu-id="e6e09-102">Delete Primary Keys</span></span>
  <span data-ttu-id="e6e09-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中刪除 (卸除) 主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="e6e09-103">You can delete (drop) a primary key in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e6e09-104">刪除主索引鍵時，系統會刪除對應的索引。</span><span class="sxs-lookup"><span data-stu-id="e6e09-104">When the primary key is deleted, the corresponding index is deleted.</span></span>  
  
 <span data-ttu-id="e6e09-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="e6e09-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e6e09-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="e6e09-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e6e09-107">安全性</span><span class="sxs-lookup"><span data-stu-id="e6e09-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e6e09-108">**若要使用下列項目來刪除主索引鍵：**</span><span class="sxs-lookup"><span data-stu-id="e6e09-108">**To delete a primary key using:**</span></span>  
  
     [<span data-ttu-id="e6e09-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e6e09-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e6e09-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e6e09-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e6e09-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="e6e09-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e6e09-112">Security</span><span class="sxs-lookup"><span data-stu-id="e6e09-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e6e09-113">權限</span><span class="sxs-lookup"><span data-stu-id="e6e09-113">Permissions</span></span>  
 <span data-ttu-id="e6e09-114">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="e6e09-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e6e09-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e6e09-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-primary-key-constraint-using-object-explorer"></a><span data-ttu-id="e6e09-116">若要使用物件總管來刪除主索引鍵條件約束</span><span class="sxs-lookup"><span data-stu-id="e6e09-116">To delete a primary key constraint using Object Explorer</span></span>  
  
1.  <span data-ttu-id="e6e09-117">在 [物件總管] 中，展開包含主索引鍵的資料表，然後展開 **[索引鍵]** 。</span><span class="sxs-lookup"><span data-stu-id="e6e09-117">In Object Explorer, expand the table that contains the primary key and then expand **Keys**.</span></span>  
  
2.  <span data-ttu-id="e6e09-118">以滑鼠右鍵按一下索引鍵，然後選取 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="e6e09-118">Right-click the key and select **Delete**.</span></span>  
  
3.  <span data-ttu-id="e6e09-119">在 **[刪除物件]** 對話方塊中，確認指定了正確的索引鍵，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="e6e09-119">In the **Delete Object** dialog box, verify the correct key is specified and click **OK**.</span></span>  
  
#### <a name="to-delete-a-primary-key-constraint-using-table-designer"></a><span data-ttu-id="e6e09-120">若要使用資料表設計工具來刪除主索引鍵條件約束</span><span class="sxs-lookup"><span data-stu-id="e6e09-120">To delete a primary key constraint using Table Designer</span></span>  
  
1.  <span data-ttu-id="e6e09-121">在物件總管中，以滑鼠右鍵按一下含有主索引鍵的資料表，然後按一下 [設計]  。</span><span class="sxs-lookup"><span data-stu-id="e6e09-121">In Object Explorer, right-click the table with the primary key, and click **Design**.</span></span>  
  
2.  <span data-ttu-id="e6e09-122">在資料表方格中，以滑鼠右鍵按一下包含主索引鍵的資料列，然後選擇 [移除主索引鍵]  關閉設定。</span><span class="sxs-lookup"><span data-stu-id="e6e09-122">In the table grid, right-click the row with the primary key and choose **Remove Primary Key** to toggle the setting from on to off.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e6e09-123">若要恢復此一動作，可將資料表關閉而不儲存變更。</span><span class="sxs-lookup"><span data-stu-id="e6e09-123">To undo this action, close the table without saving the changes.</span></span> <span data-ttu-id="e6e09-124">如果恢復刪除主索引鍵的動作，將會遺失所有對資料表進行的其他變更。</span><span class="sxs-lookup"><span data-stu-id="e6e09-124">Deleting a primary key cannot be undone without losing all other changes made to the table.</span></span>  
  
3.  <span data-ttu-id="e6e09-125">在 [檔案]  功能表上，按一下 [儲存「資料表名稱」]。</span><span class="sxs-lookup"><span data-stu-id="e6e09-125">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e6e09-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e6e09-126">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-primary-key-constraint"></a><span data-ttu-id="e6e09-127">若要刪除主索引鍵條件約束</span><span class="sxs-lookup"><span data-stu-id="e6e09-127">To delete a primary key constraint</span></span>  
  
1.  <span data-ttu-id="e6e09-128">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e6e09-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e6e09-129">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="e6e09-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e6e09-130">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="e6e09-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e6e09-131">此範例會先識別主索引鍵條件約束的名稱，然後再刪除條件約束。</span><span class="sxs-lookup"><span data-stu-id="e6e09-131">The example first identifies the name of the primary key constraint and then deletes the constraint.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Return the name of primary key.  
    SELECT name  
    FROM sys.key_constraints  
    WHERE type = 'PK' AND OBJECT_NAME(parent_object_id) = N'TransactionHistoryArchive';  
    GO  
    -- Delete the primary key constraint.  
    ALTER TABLE Production.TransactionHistoryArchive  
    DROP CONSTRAINT PK_TransactionHistoryArchive_TransactionID;   
    GO  
    ```  
  
 <span data-ttu-id="e6e09-132">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) 和 [sys.key_constraints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-constraints-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="e6e09-132">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) and [sys.key_constraints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-constraints-transact-sql)</span></span>  
  
###  <a name="TsqlExample"></a>  
