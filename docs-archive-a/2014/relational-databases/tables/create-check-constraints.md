---
title: 建立檢查條件約束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table constraints [SQL Server]
- attaching check constraints
- columns [SQL Server], constraints
- constraints [SQL Server], check
- CHECK constraints, attaching
ms.assetid: b8756304-9454-4d39-996a-64516831b7df
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7795ee6eca85a22bdd4e84c90ce49a9449ddff28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607344"
---
# <a name="create-check-constraints"></a><span data-ttu-id="f6c32-102">建立檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="f6c32-102">Create Check Constraints</span></span>
  <span data-ttu-id="f6c32-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立資料表的檢查條件約束，以便指定一個或多個資料行可接受的資料值。</span><span class="sxs-lookup"><span data-stu-id="f6c32-103">You can create a check constraint in a table to specify the data values that are acceptable in one or more columns in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f6c32-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="f6c32-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f6c32-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="f6c32-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f6c32-106">安全性</span><span class="sxs-lookup"><span data-stu-id="f6c32-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f6c32-107">**若要使用下列項目來建立新的檢查條件約束：**</span><span class="sxs-lookup"><span data-stu-id="f6c32-107">**To create a new check constraint using:**</span></span>  
  
     [<span data-ttu-id="f6c32-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f6c32-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f6c32-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f6c32-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f6c32-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="f6c32-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f6c32-111">Security</span><span class="sxs-lookup"><span data-stu-id="f6c32-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f6c32-112">權限</span><span class="sxs-lookup"><span data-stu-id="f6c32-112">Permissions</span></span>  
 <span data-ttu-id="f6c32-113">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="f6c32-113">Requires ALTER permissions on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f6c32-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f6c32-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-new-check-constraint"></a><span data-ttu-id="f6c32-115">若要建立新的檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="f6c32-115">To create a new check constraint</span></span>  
  
1.  <span data-ttu-id="f6c32-116">在 [物件總管]  中，展開您想要加入檢查條件約束的資料表、以滑鼠右鍵按一下 [條件約束]  ，然後按一下 [新增條件約束]  。</span><span class="sxs-lookup"><span data-stu-id="f6c32-116">In **Object Explorer**, expand the table to which you want to add a check constraint, right-click **Constraints** and click **New Constraint**.</span></span>  
  
2.  <span data-ttu-id="f6c32-117">在 [檢查條件約束]  對話方塊中，按一下 [運算式]  欄位，然後按一下省略符號 **(...)** 。</span><span class="sxs-lookup"><span data-stu-id="f6c32-117">In the **Check Constraints** dialog box, click in the **Expression** field and then click the ellipses **(...)**.</span></span>  
  
3.  <span data-ttu-id="f6c32-118">在 **[檢查條件約束運算式]** 對話方塊中，輸入檢查條件約束的 SQL 運算式。</span><span class="sxs-lookup"><span data-stu-id="f6c32-118">In the **Check Constraint Expression** dialog box, type the SQL expressions for the check constraint.</span></span> <span data-ttu-id="f6c32-119">例如，若要將 `SellEndDate` 資料表之 `Product` 資料行中的項目限制為大於或等於 `SellStartDate` 資料行中日期的值或是 NULL 值，請輸入：</span><span class="sxs-lookup"><span data-stu-id="f6c32-119">For example, to limit the entries in the `SellEndDate` column of the `Product` table to a value that is either greater than or equal to the date in the `SellStartDate` column or is a NULL value, type:</span></span>  
  
    ```  
    SellEndDate >= SellStartDate OR SellEndDate IS NULL  
    ```  
  
     <span data-ttu-id="f6c32-120">或者，若要要求 `zip` 資料行中的項目必須是 5 位數，請輸入：</span><span class="sxs-lookup"><span data-stu-id="f6c32-120">Or, to require entries in the `zip` column to be 5 digits, type:</span></span>  
  
    ```  
    zip LIKE '[0-9][0-9][0-9][0-9][0-9]'  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="f6c32-121">請務必將任何非數字條件約束值放在單引號 (') 中。</span><span class="sxs-lookup"><span data-stu-id="f6c32-121">Make sure to enclose any non-numeric constraint values in single quotation marks (').</span></span>  
  
4.  <span data-ttu-id="f6c32-122">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="f6c32-122">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="f6c32-123">在 [識別]  類別目錄中，您可以變更檢查條件約束的名稱，並且加入條件約束的描述 (擴充屬性)。</span><span class="sxs-lookup"><span data-stu-id="f6c32-123">In the **Identity** category, you can change the name of the check constraint and add a description (extended property) for the constraint.</span></span>  
  
6.  <span data-ttu-id="f6c32-124">在 **[資料表設計工具]** 類別目錄中，您可以設定強制執行條件約束的時間。</span><span class="sxs-lookup"><span data-stu-id="f6c32-124">In the **Table Designer** category, you can set when the constraint is enforced.</span></span>  
  
    |<span data-ttu-id="f6c32-125">**收件人：**</span><span class="sxs-lookup"><span data-stu-id="f6c32-125">**To:**</span></span>|<span data-ttu-id="f6c32-126">**請在下列欄位中選取 [是]：**</span><span class="sxs-lookup"><span data-stu-id="f6c32-126">**Select Yes in the Following Fields:**</span></span>|  
    |-------------|---------------------------------------------|  
    |<span data-ttu-id="f6c32-127">針對建立條件約束之前存在的資料測試條件約束</span><span class="sxs-lookup"><span data-stu-id="f6c32-127">Test the constraint on data that existed before you created the constraint</span></span>|<span data-ttu-id="f6c32-128">**檢查建立或重新啟用時的現有資料**</span><span class="sxs-lookup"><span data-stu-id="f6c32-128">**Check Existing Data On Creation Or Enabling**</span></span>|  
    |<span data-ttu-id="f6c32-129">每次在此資料表上進行複寫作業時都強制執行條件約束</span><span class="sxs-lookup"><span data-stu-id="f6c32-129">Enforce the constraint whenever a replication operation occurs on this table</span></span>|<span data-ttu-id="f6c32-130">**強制複寫**</span><span class="sxs-lookup"><span data-stu-id="f6c32-130">**Enforce For Replication**</span></span>|  
    |<span data-ttu-id="f6c32-131">每次插入或更新此資料表的資料列時都強制執行條件約束</span><span class="sxs-lookup"><span data-stu-id="f6c32-131">Enforce the constraint whenever a row of this table is inserted or updated</span></span>|<span data-ttu-id="f6c32-132">**於 INSERT 及 UPDATE 時強制套用**</span><span class="sxs-lookup"><span data-stu-id="f6c32-132">**Enforce For INSERTs And UPDATEs**</span></span>|  
  
7.  <span data-ttu-id="f6c32-133">按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="f6c32-133">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f6c32-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f6c32-134">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-new-check-constraint"></a><span data-ttu-id="f6c32-135">若要建立新的檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="f6c32-135">To create a new check constraint</span></span>  
  
1.  <span data-ttu-id="f6c32-136">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f6c32-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f6c32-137">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="f6c32-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f6c32-138">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="f6c32-138">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    ALTER TABLE dbo.DocExc   
       ADD ColumnD int NULL   
       CONSTRAINT CHK_ColumnD_DocExc   
       CHECK (ColumnD > 10 AND ColumnD < 50);  
    GO  
    -- Adding values that will pass the check constraint  
    INSERT INTO dbo.DocExc (ColumnD) VALUES (49);  
    GO  
    -- Adding values that will fail the check constraint  
    INSERT INTO dbo.DocExc (ColumnD) VALUES (55);  
    GO  
  
    ```  
  
 <span data-ttu-id="f6c32-139">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f6c32-139">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
