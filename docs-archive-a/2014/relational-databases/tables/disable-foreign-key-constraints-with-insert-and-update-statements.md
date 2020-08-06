---
title: 停用 INSERT 和 UPDATE 陳述式的外部索引鍵條件約束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- constraints [SQL Server], foreign keys
- foreign keys [SQL Server], disabling constraints
- disabling constraints
- UPDATE statement [SQL Server], foreign key constraints
- INSERT statement [SQL Server], foreign key constraints
ms.assetid: 029168d7-085e-4b13-9b86-5644b67c6e24
author: stevestein
ms.author: sstein
ms.openlocfilehash: e91328f4f12f2a0a27f397c7bd95390a505f3998
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594963"
---
# <a name="disable-foreign-key-constraints-with-insert-and-update-statements"></a><span data-ttu-id="60015-102">停用 INSERT 和 UPDATE 陳述式的外部索引鍵條件約束</span><span class="sxs-lookup"><span data-stu-id="60015-102">Disable Foreign Key Constraints with INSERT and UPDATE Statements</span></span>
  <span data-ttu-id="60015-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中停用 INSERT 和 UPDATE 交易期間的外部索引鍵條件約束。</span><span class="sxs-lookup"><span data-stu-id="60015-103">You can disable a foreign key constraint during INSERT and UPDATE transactions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="60015-104">如果您確知新資料將違反現有條件約束，或是條件約束只適用於已經在資料庫中的資料，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="60015-104">Use this option if you know that new data will violate the existing constraint or if the constraint applies only to the data already in the database.</span></span>  
  
 <span data-ttu-id="60015-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="60015-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="60015-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="60015-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="60015-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="60015-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="60015-108">安全性</span><span class="sxs-lookup"><span data-stu-id="60015-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="60015-109">**使用下列方法停用 INSERT 和 UPDATE 陳述式的外部索引鍵條件約束：**</span><span class="sxs-lookup"><span data-stu-id="60015-109">**To disable a foreign key constraint for INSERT and UPDATE statements, using:**</span></span>  
  
     [<span data-ttu-id="60015-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="60015-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="60015-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="60015-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="60015-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="60015-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="60015-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="60015-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="60015-114">停用這些條件約束之後，未來將不會根據條件約束的條件驗證資料行的插入或更新作業。</span><span class="sxs-lookup"><span data-stu-id="60015-114">After you disable these constraints, future inserts or updates to the column will not be validated against the constraint conditions.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="60015-115">Security</span><span class="sxs-lookup"><span data-stu-id="60015-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="60015-116">權限</span><span class="sxs-lookup"><span data-stu-id="60015-116">Permissions</span></span>  
 <span data-ttu-id="60015-117">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="60015-117">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="60015-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="60015-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-a-foreign-key-constraint-for-insert-and-update-statements"></a><span data-ttu-id="60015-119">若要停用 INSERT 和 UPDATE 陳述式的外部索引鍵條件約束</span><span class="sxs-lookup"><span data-stu-id="60015-119">To disable a foreign key constraint for INSERT and UPDATE statements</span></span>  
  
1.  <span data-ttu-id="60015-120">在 **[物件總管]** 中，展開含有條件約束的資料表，然後展開 **[索引鍵]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="60015-120">In **Object Explorer**, expand the table with the constraint and then expand the **Keys** folder.</span></span>  
  
2.  <span data-ttu-id="60015-121">以滑鼠右鍵按一下條件約束，然後選取 **[修改]** 。</span><span class="sxs-lookup"><span data-stu-id="60015-121">Right-click the constraint and select **Modify**.</span></span>  
  
3.  <span data-ttu-id="60015-122">在 **[資料表設計工具]** 底下的方格中，按一下 **[強制使用外部索引鍵條件約束]** ，然後從下拉式功能表中選取 **[否]** 。</span><span class="sxs-lookup"><span data-stu-id="60015-122">In the grid under **Table Designer**, click **Enforce Foreign Key Constraint** and select **No** from the drop-down menu.</span></span>  
  
4.  <span data-ttu-id="60015-123">按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="60015-123">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="60015-124">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="60015-124">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-a-foreign-key-constraint-for-insert-and-update-statements"></a><span data-ttu-id="60015-125">若要停用 INSERT 和 UPDATE 陳述式的外部索引鍵條件約束</span><span class="sxs-lookup"><span data-stu-id="60015-125">To disable a foreign key constraint for INSERT and UPDATE statements</span></span>  
  
1.  <span data-ttu-id="60015-126">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="60015-126">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="60015-127">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="60015-127">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="60015-128">將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="60015-128">Copy and paste the following examples into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT FK_PurchaseOrderHeader_Employee_EmployeeID;  
    GO  
    ```  
  
 <span data-ttu-id="60015-129">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="60015-129">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
