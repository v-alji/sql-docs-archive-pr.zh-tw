---
title: 建立 DML 觸發程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], DML triggers
- deferred name resolution, DML triggers
- WITH ENCRYPTION clause
- IF UPDATE
- SET statement, DML triggers
- DML triggers, programming
- testing column changes
- results [SQL Server], DML triggers
ms.assetid: b2b52258-642b-462e-8e0f-18c09d2eccf4
author: rothja
ms.author: jroth
ms.openlocfilehash: f843513ba634bcb3479e373eb9ac978ab584588d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606139"
---
# <a name="create-dml-triggers"></a><span data-ttu-id="aca57-102">建立 DML 觸發程序</span><span class="sxs-lookup"><span data-stu-id="aca57-102">Create DML Triggers</span></span>
  <span data-ttu-id="aca57-103">此主題描述如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 以及使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] CREATE TRIGGER 陳述式來建立 [!INCLUDE[tsql](../../includes/tsql-md.md)] DML 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="aca57-103">This topic describes how to create a [!INCLUDE[tsql](../../includes/tsql-md.md)] DML trigger by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TRIGGER statement.</span></span>  
  
##  <a name="before-you-begin"></a><a name="Top"></a> <span data-ttu-id="aca57-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="aca57-104">Before You Begin</span></span>  
  
### <a name="limitations-and-restrictions"></a><span data-ttu-id="aca57-105">限制事項</span><span class="sxs-lookup"><span data-stu-id="aca57-105">Limitations and Restrictions</span></span>  
 <span data-ttu-id="aca57-106">如需與建立 DML 觸發程序相關之限制事項的清單，請參閱 [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="aca57-106">For a list of limitations and restrictions related to creating DML triggers, see [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="aca57-107">權限</span><span class="sxs-lookup"><span data-stu-id="aca57-107">Permissions</span></span>  
 <span data-ttu-id="aca57-108">需要建立觸發程序之資料表或檢視的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="aca57-108">Requires ALTER permission on the table or view on which the trigger is being created.</span></span>  
  
##  <a name="how-to-create-a-dml-trigger"></a><a name="Procedures"></a> <span data-ttu-id="aca57-109">如何建立 DML 觸發程序</span><span class="sxs-lookup"><span data-stu-id="aca57-109">How to Create a DML Trigger</span></span>  
 <span data-ttu-id="aca57-110">您可以使用下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="aca57-110">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="aca57-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="aca57-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="aca57-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="aca57-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="aca57-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="aca57-113">Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="aca57-114">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="aca57-114">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="aca57-115">依序展開 [資料庫]  、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫、[資料表]  和 **Purchasing.PurchaseOrderHeader** 資料表。</span><span class="sxs-lookup"><span data-stu-id="aca57-115">Expand **Databases**, expand the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, expand **Tables** and then expand the table **Purchasing.PurchaseOrderHeader**.</span></span>  
  
3.  <span data-ttu-id="aca57-116">以滑鼠右鍵按一下 [觸發程序]  ，然後選取 [新增觸發程序]  。</span><span class="sxs-lookup"><span data-stu-id="aca57-116">Right-click **Triggers**, and then select **New Trigger**.</span></span>  
  
4.  <span data-ttu-id="aca57-117">在 **[查詢]** 功能表上，按一下 **[指定範本參數的值]** 。</span><span class="sxs-lookup"><span data-stu-id="aca57-117">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span> <span data-ttu-id="aca57-118">您也可以按 (Ctrl-Shift-M) 開啟 [指定範本參數的值]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="aca57-118">Alternatively, you can press (Ctrl-Shift-M) to open the **Specify Values for Template Parameters** dialog box.</span></span>  
  
5.  <span data-ttu-id="aca57-119">在 **[指定範本參數的值]** 對話方塊中，為顯示的參數輸入下列值。</span><span class="sxs-lookup"><span data-stu-id="aca57-119">In the **Specify Values for Template Parameters** dialog box, enter the following values for the parameters shown.</span></span>  
  
    |<span data-ttu-id="aca57-120">參數</span><span class="sxs-lookup"><span data-stu-id="aca57-120">Parameter</span></span>|<span data-ttu-id="aca57-121">值</span><span class="sxs-lookup"><span data-stu-id="aca57-121">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="aca57-122">作者</span><span class="sxs-lookup"><span data-stu-id="aca57-122">Author</span></span>|<span data-ttu-id="aca57-123">*您的名字*</span><span class="sxs-lookup"><span data-stu-id="aca57-123">*Your name*</span></span>|  
    |<span data-ttu-id="aca57-124">建立日期</span><span class="sxs-lookup"><span data-stu-id="aca57-124">Create Date</span></span>|<span data-ttu-id="aca57-125">*今天的日期*</span><span class="sxs-lookup"><span data-stu-id="aca57-125">*Today's date*</span></span>|  
    |<span data-ttu-id="aca57-126">描述</span><span class="sxs-lookup"><span data-stu-id="aca57-126">Description</span></span>|<span data-ttu-id="aca57-127">先檢查供應商信用評等，再允許插入含有該供應商的新採購單。</span><span class="sxs-lookup"><span data-stu-id="aca57-127">Checks the vendor credit rating before allowing a new purchase order with the vendor to be inserted.</span></span>|  
    |<span data-ttu-id="aca57-128">Schema_Name</span><span class="sxs-lookup"><span data-stu-id="aca57-128">Schema_Name</span></span>|<span data-ttu-id="aca57-129">購買</span><span class="sxs-lookup"><span data-stu-id="aca57-129">Purchasing</span></span>|  
    |<span data-ttu-id="aca57-130">Trigger_Name</span><span class="sxs-lookup"><span data-stu-id="aca57-130">Trigger_Name</span></span>|<span data-ttu-id="aca57-131">NewPODetail2</span><span class="sxs-lookup"><span data-stu-id="aca57-131">NewPODetail2</span></span>|  
    |<span data-ttu-id="aca57-132">Table_Name</span><span class="sxs-lookup"><span data-stu-id="aca57-132">Table_Name</span></span>|<span data-ttu-id="aca57-133">PurchaseOrderDetail</span><span class="sxs-lookup"><span data-stu-id="aca57-133">PurchaseOrderDetail</span></span>|  
    |<span data-ttu-id="aca57-134">Data_Modification_Statement</span><span class="sxs-lookup"><span data-stu-id="aca57-134">Data_Modification_Statement</span></span>|<span data-ttu-id="aca57-135">從清單中移除 UPDATE 和 DELETE。</span><span class="sxs-lookup"><span data-stu-id="aca57-135">Remove UPDATE and DELETE from the list.</span></span>|  
  
6.  <span data-ttu-id="aca57-136">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="aca57-136">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="aca57-137">在 [查詢編輯器]  中，將 `-- Insert statements for trigger here` 註解取代為下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="aca57-137">In the **Query Editor**, replace the comment `-- Insert statements for trigger here` with the following statement:</span></span>  
  
    ```sql  
    IF @@ROWCOUNT = 1  
    BEGIN  
       UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal + LineTotal  
       FROM inserted  
       WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
  
    END  
    ELSE  
    BEGIN  
          UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal +   
          (SELECT SUM(LineTotal)  
          FROM inserted  
          WHERE PurchaseOrderHeader.PurchaseOrderID  
           = inserted.PurchaseOrderID)  
       WHERE PurchaseOrderHeader.PurchaseOrderID IN  
          (SELECT PurchaseOrderID FROM inserted)  
    END;  
    ```  
  
8.  <span data-ttu-id="aca57-138">若要驗證語法是否有效，請在 [查詢]  功能表上按一下 [剖析]  。</span><span class="sxs-lookup"><span data-stu-id="aca57-138">To verify the syntax is valid, on the **Query** menu, click **Parse**.</span></span> <span data-ttu-id="aca57-139">如果傳回錯誤訊息，請比較陳述式與上列資訊，並視需要進行更正，然後重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="aca57-139">If an error message is returned, compare the statement with the information above and correct as needed and repeat this step.</span></span>  
  
9. <span data-ttu-id="aca57-140">若要建立 DML 觸發程序，請在 [查詢]  功能表中按一下 [執行]  。</span><span class="sxs-lookup"><span data-stu-id="aca57-140">To create the DML trigger, from the **Query** menu, click **Execute**.</span></span> <span data-ttu-id="aca57-141">DML 觸發程序會建立為資料庫中的物件。</span><span class="sxs-lookup"><span data-stu-id="aca57-141">The DML trigger is created as an object in the database.</span></span>  
  
10. <span data-ttu-id="aca57-142">若要查看物件總管中所列的 DML 觸發程序，請以滑鼠右鍵按一下 [觸發程序]  ，然後選取 [重新整理]  。</span><span class="sxs-lookup"><span data-stu-id="aca57-142">To see the DML trigger listed in Object Explorer, right-click **Triggers** and select **Refresh**.</span></span>  
  
 [<span data-ttu-id="aca57-143">開始之前</span><span class="sxs-lookup"><span data-stu-id="aca57-143">Before You Begin</span></span>](#Top)  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="aca57-144">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="aca57-144">Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="aca57-145">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="aca57-145">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="aca57-146">在 **[檔案]** 功能表中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="aca57-146">From the **File** menu, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="aca57-147">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="aca57-147">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="aca57-148">此範例會建立與上面相同的預存 DML 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="aca57-148">This example creates the same stored DML trigger as above.</span></span>  
  
    ```sql
    -- Trigger valid for multirow and single row inserts  
    -- and optimal for single row inserts.  
    USE AdventureWorks2012;  
    GO  
    CREATE TRIGGER NewPODetail3  
    ON Purchasing.PurchaseOrderDetail  
    FOR INSERT AS  
    IF @@ROWCOUNT = 1  
    BEGIN  
       UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal + LineTotal  
       FROM inserted  
       WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
  
    END  
    ELSE  
    BEGIN  
          UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal +   
          (SELECT SUM(LineTotal)  
          FROM inserted  
          WHERE PurchaseOrderHeader.PurchaseOrderID  
           = inserted.PurchaseOrderID)  
       WHERE PurchaseOrderHeader.PurchaseOrderID IN  
          (SELECT PurchaseOrderID FROM inserted)  
    END;  
    ```  
