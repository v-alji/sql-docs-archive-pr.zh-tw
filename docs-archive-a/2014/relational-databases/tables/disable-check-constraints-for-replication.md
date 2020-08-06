---
title: 停用複寫的檢查條件約束 | Microsoft Docs
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
ms.assetid: af98fc70-24dd-4bd3-a0a3-f701dfa67b2c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 98b6ca7c3525edeffdb47f294db568d3c115b2c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584352"
---
# <a name="disable-check-constraints-for-replication"></a><span data-ttu-id="e483e-102">停用複寫的檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="e483e-102">Disable Check Constraints for Replication</span></span>
  <span data-ttu-id="e483e-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中停用檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="e483e-103">You can disable check constraints in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e483e-104">您也可以明確停用複製的檢查條件約束，當您從舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]發行資料時，這會相當實用。</span><span class="sxs-lookup"><span data-stu-id="e483e-104">You can also explicitly disable check constraints for replication, which can be useful if you are publishing data from a previous version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e483e-105">如果使用複寫發行資料表，則會自動停用複製代理程式所執行作業的檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="e483e-105">If a table is published using replication, check constraints are automatically disabled for operations performed by replication agents.</span></span> <span data-ttu-id="e483e-106">當複寫代理程式在訂閱者端執行插入、更新或刪除時，不會檢查條件約束；如果使用者執行插入、更新或刪除，則會檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="e483e-106">When a replication agent performs an insert, update, or delete at a Subscriber, the constraint is not checked; if a user performs an insert, update, or delete, the constraint is checked.</span></span> <span data-ttu-id="e483e-107">停用複製代理程式的條件約束，是因為原本插入、更新或刪除資料時，就已在發行者端檢查過條件約束。</span><span class="sxs-lookup"><span data-stu-id="e483e-107">The constraint is disabled for the replication agent because the constraint was already checked at the Publisher when the data was originally inserted, updated, or deleted.</span></span> <span data-ttu-id="e483e-108">如需詳細資訊，請參閱 [指定結構描述選項](../replication/publish/specify-schema-options.md)。</span><span class="sxs-lookup"><span data-stu-id="e483e-108">For more information, see [Specify Schema Options](../replication/publish/specify-schema-options.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e483e-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="e483e-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e483e-110">Security</span><span class="sxs-lookup"><span data-stu-id="e483e-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e483e-111">權限</span><span class="sxs-lookup"><span data-stu-id="e483e-111">Permissions</span></span>  
 <span data-ttu-id="e483e-112">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="e483e-112">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e483e-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e483e-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-a-check-constraint-for-replication"></a><span data-ttu-id="e483e-114">若要停用複製的檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="e483e-114">To disable a check constraint for replication</span></span>  
  
1.  <span data-ttu-id="e483e-115">在 **[物件總管]** 中，展開包含您要修改之檢查條件約束的資料表，然後展開 **[條件約束]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e483e-115">In **Object Explorer**, expand the table with the check constraint you want to modify, and then expand the **Constraints** folder.</span></span>  
  
2.  <span data-ttu-id="e483e-116">以滑鼠右鍵按一下您要修改的檢查條件約束，然後按一下 **[修改]** 。</span><span class="sxs-lookup"><span data-stu-id="e483e-116">Right-click the check constraint you wish to modify and then click **Modify**.</span></span>  
  
3.  <span data-ttu-id="e483e-117">在 **[檢查條件約束]** 對話方塊中的 **[資料表設計工具]** 底下，針對 **[強制複寫]** 選取 **[否]** 值。</span><span class="sxs-lookup"><span data-stu-id="e483e-117">In the **Check Constraints** dialog box, under **Table Designer**, select a value of **No** for **Enforce For Replication**.</span></span>  
  
4.  <span data-ttu-id="e483e-118">按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="e483e-118">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e483e-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e483e-119">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-a-check-constraint-for-replication"></a><span data-ttu-id="e483e-120">若要停用複製的檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="e483e-120">To disable a check constraint for replication</span></span>  
  
1.  <span data-ttu-id="e483e-121">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e483e-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e483e-122">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="e483e-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e483e-123">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="e483e-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e483e-124">此範例會建立包含 IDENTITY 資料行及 CHECK 條件約束的資料表。</span><span class="sxs-lookup"><span data-stu-id="e483e-124">The example creates a table with an IDENTITY column and a CHECK constraint on the table.</span></span> <span data-ttu-id="e483e-125">接著範例會卸除條件約束再重新建立，並指定 NOT FOR REPLICATION 子句。</span><span class="sxs-lookup"><span data-stu-id="e483e-125">The example then drops the constraint and recreates it specifying the NOT FOR REPLICATION clause.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE dbo.doc_exd (column_a int IDENTITY (1,1)   
    CONSTRAINT exd_check CHECK (column_a > 1))   
  
    ALTER TABLE dbo.doc_exd   
    DROP CONSTRAINT exd_check;   
    GO  
    ALTER TABLE dbo.doc_exd    
    ADD CONSTRAINT exd_check CHECK NOT FOR REPLICATION (column_a > 1);  
    ```  
  
 <span data-ttu-id="e483e-126">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e483e-126">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>   
## <a name="see-also"></a><span data-ttu-id="e483e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e483e-127">See Also</span></span>  
 [<span data-ttu-id="e483e-128">指定結構描述選項</span><span class="sxs-lookup"><span data-stu-id="e483e-128">Specify Schema Options</span></span>](../replication/publish/specify-schema-options.md)  
  
  
