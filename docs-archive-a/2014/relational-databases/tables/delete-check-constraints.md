---
title: 刪除檢查條件約束 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing constraints
- CHECK constraints, deleting
- constraints [SQL Server], deleting
- constraints [SQL Server], check
- deleting constraints
ms.assetid: 5f86c1a6-f5fa-4e77-a892-f6ae96fc0ab3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28a7f72993cbf2ed0a8cc76534380090ef0d0a55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595878"
---
# <a name="delete-check-constraints"></a><span data-ttu-id="982d0-102">刪除檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="982d0-102">Delete Check Constraints</span></span>
  <span data-ttu-id="982d0-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中刪除檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="982d0-103">You can delete a check constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="982d0-104">刪除檢查條件約束會從條件約束運算式中移除一個或多個資料行所接受資料值的限制。</span><span class="sxs-lookup"><span data-stu-id="982d0-104">Deleting check constraints removes the limitations on data values that are accepted in the column or columns included in the constraint expression.</span></span>  
  
 <span data-ttu-id="982d0-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="982d0-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="982d0-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="982d0-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="982d0-107">安全性</span><span class="sxs-lookup"><span data-stu-id="982d0-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="982d0-108">**若要使用下列項目來刪除檢查條件約束：**</span><span class="sxs-lookup"><span data-stu-id="982d0-108">**To delete a check constraint, using:**</span></span>  
  
     [<span data-ttu-id="982d0-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="982d0-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="982d0-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="982d0-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="982d0-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="982d0-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="982d0-112">Security</span><span class="sxs-lookup"><span data-stu-id="982d0-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="982d0-113">權限</span><span class="sxs-lookup"><span data-stu-id="982d0-113">Permissions</span></span>  
 <span data-ttu-id="982d0-114">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="982d0-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="982d0-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="982d0-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-check-constraint"></a><span data-ttu-id="982d0-116">若要刪除檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="982d0-116">To delete a check constraint</span></span>  
  
1.  <span data-ttu-id="982d0-117">在 **[物件總管]** 中，展開含有檢查條件約束的資料表。</span><span class="sxs-lookup"><span data-stu-id="982d0-117">In **Object Explorer**, expand the table with the check constraint.</span></span>  
  
2.  <span data-ttu-id="982d0-118">展開  **[條件約束]** 。</span><span class="sxs-lookup"><span data-stu-id="982d0-118">Expand  **Constraints**.</span></span>  
  
3.  <span data-ttu-id="982d0-119">以滑鼠右鍵按一下條件約束，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="982d0-119">Right-click the constraint and click **Delete**.</span></span>  
  
4.  <span data-ttu-id="982d0-120">在 **[刪除物件]** 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="982d0-120">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="982d0-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="982d0-121">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-check-constraint"></a><span data-ttu-id="982d0-122">若要刪除檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="982d0-122">To delete a check constraint</span></span>  
  
1.  <span data-ttu-id="982d0-123">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="982d0-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="982d0-124">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="982d0-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="982d0-125">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="982d0-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    ALTER TABLE dbo.DocExc   
    DROP CONSTRAINT CHK_ColumnD_DocExc;  
    GO  
    ```  
  
 <span data-ttu-id="982d0-126">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="982d0-126">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
  
