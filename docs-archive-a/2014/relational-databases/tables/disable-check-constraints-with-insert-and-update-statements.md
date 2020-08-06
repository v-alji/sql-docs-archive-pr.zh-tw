---
title: 停用 INSERT 與 UPDATE 陳述式的檢查條件約束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- CHECK constraints, disabling
- constraints [SQL Server], disabling
- disabling constraints
- constraints [SQL Server], check
ms.assetid: c7287ad1-50d2-4e80-bc0c-b5570f7e5f69
author: stevestein
ms.author: sstein
ms.openlocfilehash: 780a2c1bfd9f21c71367ad61f200ec19ab44a608
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595869"
---
# <a name="disable-check-constraints-with-insert-and-update-statements"></a><span data-ttu-id="c130e-102">使用 INSERT 與 UPDATE 陳述式停用檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="c130e-102">Disable Check Constraints with INSERT and UPDATE Statements</span></span>
  <span data-ttu-id="c130e-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中停用 INSERT 和 UPDATE 交易的檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="c130e-103">You can disable a check constraint for INSERT and UPDATE transactions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c130e-104">停用檢查條件約束之後，未來將不會根據條件約束的條件驗證資料行的插入或更新作業。</span><span class="sxs-lookup"><span data-stu-id="c130e-104">After you disable the check constraints, future inserts or updates to the column will not be validated against the constraint conditions.</span></span> <span data-ttu-id="c130e-105">如果您確知新資料將違反現有條件約束，或是條件約束只適用於已經在資料庫中的資料，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="c130e-105">Use this option if you know that new data will violate the existing constraint or if the constraint applies only to the data already in the database.</span></span>  
  
 <span data-ttu-id="c130e-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="c130e-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c130e-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="c130e-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c130e-108">安全性</span><span class="sxs-lookup"><span data-stu-id="c130e-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c130e-109">**若要使用下列項目來停用 INSERT 和 UPDATE 陳述式的檢查條件約束：**</span><span class="sxs-lookup"><span data-stu-id="c130e-109">**To disable a check constraint for INSERT and UPDATE statements, using:**</span></span>  
  
     [<span data-ttu-id="c130e-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c130e-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c130e-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c130e-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c130e-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="c130e-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c130e-113">Security</span><span class="sxs-lookup"><span data-stu-id="c130e-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c130e-114">權限</span><span class="sxs-lookup"><span data-stu-id="c130e-114">Permissions</span></span>  
 <span data-ttu-id="c130e-115">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="c130e-115">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c130e-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c130e-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-a-check-constraint-for-insert-and-update-statements"></a><span data-ttu-id="c130e-117">若要停用 INSERT 和 UPDATE 陳述式的檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="c130e-117">To disable a check constraint for INSERT and UPDATE statements</span></span>  
  
1.  <span data-ttu-id="c130e-118">在 **[物件總管]** 中，展開含有條件約束的資料表，然後展開 **[條件約束]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c130e-118">In **Object Explorer**, expand the table with the constraint and then expand the **Constraints** folder.</span></span>  
  
2.  <span data-ttu-id="c130e-119">以滑鼠右鍵按一下條件約束，然後選取 **[修改]** 。</span><span class="sxs-lookup"><span data-stu-id="c130e-119">Right-click the constraint and select **Modify**.</span></span>  
  
3.  <span data-ttu-id="c130e-120">在 **[資料表設計工具]** 底下的方格中，按一下 **[於 INSERT 及 UPDATE 時強制套用]** ，然後從下拉式功能表中選取 **[否]** 。</span><span class="sxs-lookup"><span data-stu-id="c130e-120">In the grid under **Table Designer**, click **Enforce For INSERTs And UPDATEs** and select **No** from the drop-down menu.</span></span>  
  
4.  <span data-ttu-id="c130e-121">按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="c130e-121">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c130e-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c130e-122">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-a-check-constraint-for-insert-and-update-statements"></a><span data-ttu-id="c130e-123">若要停用 INSERT 和 UPDATE 陳述式的檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="c130e-123">To disable a check constraint for INSERT and UPDATE statements</span></span>  
  
1.  <span data-ttu-id="c130e-124">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c130e-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c130e-125">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="c130e-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c130e-126">將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="c130e-126">Copy and paste the following examples into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT CK_PurchaseOrderHeader_Freight;   
    GO  
    ```  
  
 <span data-ttu-id="c130e-127">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c130e-127">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
