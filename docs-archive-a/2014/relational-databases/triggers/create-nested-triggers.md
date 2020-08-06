---
title: 建立巢狀觸發程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- recursive DML triggers [SQL Server]
- DML triggers, nested
- triggers [SQL Server], nested
- direct recursion [SQL Server]
- triggers [SQL Server], recursive
- DML triggers, recursive
- RECURSIVE_TRIGGERS option
- indirect recursion [SQL Server]
- nested DML triggers
ms.assetid: cd522dda-b4ab-41b8-82b0-02445bdba7af
author: rothja
ms.author: jroth
ms.openlocfilehash: c0016fc3cdd93ea78ceed56efa076a01bd85be50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606141"
---
# <a name="create-nested-triggers"></a><span data-ttu-id="d52e9-102">建立巢狀觸發程序</span><span class="sxs-lookup"><span data-stu-id="d52e9-102">Create Nested Triggers</span></span>
  <span data-ttu-id="d52e9-103">觸發程序執行用來起始另一個觸發程序的動作時，DML 和 DDL 觸發程序就是巢狀觸發程序。</span><span class="sxs-lookup"><span data-stu-id="d52e9-103">Both DML and DDL triggers are nested when a trigger performs an action that initiates another trigger.</span></span> <span data-ttu-id="d52e9-104">這些動作可以起始化其他觸發程序等等。</span><span class="sxs-lookup"><span data-stu-id="d52e9-104">These actions can initiate other triggers, and so on.</span></span> <span data-ttu-id="d52e9-105">DML 與 DDL 觸發程序最多可以巢狀方式嵌套多達 32 層。</span><span class="sxs-lookup"><span data-stu-id="d52e9-105">DML and DDL triggers can be nested up to 32 levels.</span></span> <span data-ttu-id="d52e9-106">您可以透過 [巢狀觸發程序]  伺服器組態選項來控制 AFTER 觸發程序是否可為巢狀。</span><span class="sxs-lookup"><span data-stu-id="d52e9-106">You can control whether AFTER triggers can be nested through the **nested triggers** server configuration option.</span></span> <span data-ttu-id="d52e9-107">不論此設定為何，INSTEAD OF 觸發程序 (只有 DML 觸發程序可為 INSTEAD OF 觸發程序) 均可為巢狀。</span><span class="sxs-lookup"><span data-stu-id="d52e9-107">INSTEAD OF triggers (only DML triggers can be INSTEAD OF triggers) can be nested regardless of this setting.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d52e9-108">任何從 [!INCLUDE[tsql](../../includes/tsql-md.md)] 觸發程序對 Managed 程式碼的參考，都會算成 32 層巢狀限制中的一層。</span><span class="sxs-lookup"><span data-stu-id="d52e9-108">Any reference to managed code from a [!INCLUDE[tsql](../../includes/tsql-md.md)] trigger counts as one level against the 32-level nesting limit.</span></span> <span data-ttu-id="d52e9-109">從 Managed 程式碼內叫用的方法，不列入這項限制。</span><span class="sxs-lookup"><span data-stu-id="d52e9-109">Methods invoked from within managed code do not count against this limit.</span></span>  
  
 <span data-ttu-id="d52e9-110">如果允許巢狀觸發程序，但鏈結中的觸發程序形成一個無限迴圈時，則觸發程序會因為超過巢狀層級而終止執行。</span><span class="sxs-lookup"><span data-stu-id="d52e9-110">If nested triggers are allowed and a trigger in the chain starts an infinite loop, the nesting level is exceeded and the trigger terminates.</span></span>  
  
 <span data-ttu-id="d52e9-111">您可利用巢狀觸發程序來執行實用的內部管理功能，如儲存被前一個觸發程序所影響的資料列備份。</span><span class="sxs-lookup"><span data-stu-id="d52e9-111">You can use nested triggers to perform useful housekeeping functions such as storing a backup copy of rows affected by a previous trigger.</span></span> <span data-ttu-id="d52e9-112">例如，您可在 `PurchaseOrderDetail` 上建立觸發程序，其可儲存經 `PurchaseOrderDetail` 觸發程序所刪除的 `delcascadetrig` 資料列備份。</span><span class="sxs-lookup"><span data-stu-id="d52e9-112">For example, you can create a trigger on `PurchaseOrderDetail` that saves a backup copy of the `PurchaseOrderDetail` rows that the `delcascadetrig` trigger deleted.</span></span> <span data-ttu-id="d52e9-113">由於 `delcascadetrig` 觸發程序為作用中，刪除 `PurchaseOrderID` 的 `PurchaseOrderHeader` 1965，也會刪除 `PurchaseOrderDetail`對應的一或多個資料列。</span><span class="sxs-lookup"><span data-stu-id="d52e9-113">With the `delcascadetrig` trigger in effect, deleting `PurchaseOrderID` 1965 from `PurchaseOrderHeader` deletes the corresponding row or rows from `PurchaseOrderDetail`.</span></span> <span data-ttu-id="d52e9-114">若要儲存資料，您可在 `PurchaseOrderDetail` 上建立 DELETE 觸發程序，將刪除的資料儲存至另外建立的資料表 `del_save`。</span><span class="sxs-lookup"><span data-stu-id="d52e9-114">To save the data, you can create a DELETE trigger on `PurchaseOrderDetail` that saves the deleted data into another separately created table, `del_save`.</span></span> <span data-ttu-id="d52e9-115">例如：</span><span class="sxs-lookup"><span data-stu-id="d52e9-115">For example:</span></span>  
  
```  
CREATE TRIGGER Purchasing.savedel  
   ON Purchasing.PurchaseOrderDetail  
FOR DELETE  
AS  
   INSERT del_save;  
   SELECT * FROM deleted;  
```  
  
 <span data-ttu-id="d52e9-116">我們不建議您在與順序有關的序列中使用巢狀觸發程序。</span><span class="sxs-lookup"><span data-stu-id="d52e9-116">We do not recommend using nested triggers in an order-dependent sequence.</span></span> <span data-ttu-id="d52e9-117">請使用個別的觸發程序來串聯修改的資料。</span><span class="sxs-lookup"><span data-stu-id="d52e9-117">Use separate triggers to cascade data modifications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d52e9-118">因觸發程序是在交易內執行，所以在整組巢狀觸發程序中，只要有一層在執行時發生錯誤，即會取消整個交易，所有的修改資料均會回復原狀。</span><span class="sxs-lookup"><span data-stu-id="d52e9-118">Because triggers execute within a transaction, a failure at any level of a set of nested triggers cancels the entire transaction, and all data modifications are rolled back.</span></span> <span data-ttu-id="d52e9-119">您可在觸發程序中加入 PRINT 陳述式，這樣便可知道錯誤發生在那一層級。</span><span class="sxs-lookup"><span data-stu-id="d52e9-119">Include PRINT statements in your triggers so that you can determine where the failure has occurred.</span></span>  
  
## <a name="recursive-triggers"></a><span data-ttu-id="d52e9-120">遞迴觸發程序</span><span class="sxs-lookup"><span data-stu-id="d52e9-120">Recursive Triggers</span></span>  
 <span data-ttu-id="d52e9-121">除非設定 RECURSIVE_TRIGGERS 資料庫選項，否則 AFTER 觸發程序不會以遞迴方式自我呼叫。</span><span class="sxs-lookup"><span data-stu-id="d52e9-121">An AFTER trigger does not call itself recursively unless the RECURSIVE_TRIGGERS database option is set.</span></span>  
  
 <span data-ttu-id="d52e9-122">而遞迴有以下兩種不同類型：</span><span class="sxs-lookup"><span data-stu-id="d52e9-122">There are two types of recursion:</span></span>  
  
-   <span data-ttu-id="d52e9-123">直接遞迴</span><span class="sxs-lookup"><span data-stu-id="d52e9-123">Direct recursion</span></span>  
  
     <span data-ttu-id="d52e9-124">當觸發程序引發和執行使相同觸發程序再度引發的動作時，就會發生遞迴。</span><span class="sxs-lookup"><span data-stu-id="d52e9-124">This recursion occurs when a trigger fires and performs an action that causes the same trigger to fire again.</span></span> <span data-ttu-id="d52e9-125">例如，應用程式會更新資料表 **T3**；這將使觸發程序 **Trig3** 引發。</span><span class="sxs-lookup"><span data-stu-id="d52e9-125">For example, an application updates table **T3**; this causes trigger **Trig3** to fire.</span></span> <span data-ttu-id="d52e9-126">**Trig3** 會再次更新 **T3** ；這將使觸發程序 **Trig3** 再度引發。</span><span class="sxs-lookup"><span data-stu-id="d52e9-126">**Trig3** updates table **T3** again; this causes trigger **Trig3** to fire again.</span></span>  
  
     <span data-ttu-id="d52e9-127">在呼叫不同類型的觸發程序 (AFTER 或 INSTEAD OF) 之後，再次呼叫相同的觸發程序時，也會發生直接遞迴。</span><span class="sxs-lookup"><span data-stu-id="d52e9-127">Direct recursion can also occur when the same trigger is called again, but after a trigger of a different type (AFTER or INSTEAD OF) is called.</span></span> <span data-ttu-id="d52e9-128">換句話說，即使在第一次與第二次呼叫之間呼叫了一個或多個 AFTER 觸發程序，第二次呼叫相同 INSTEAD OF 觸發程序時，仍會發生 INSTEAD OF 觸發程序的直接遞迴。</span><span class="sxs-lookup"><span data-stu-id="d52e9-128">In other words, direct recursion of an INSTEAD OF trigger can occur when the same INSTEAD OF trigger is called for a second time, even if one or more AFTER triggers are called in between.</span></span> <span data-ttu-id="d52e9-129">同樣地，即使在第一次與第二次呼叫之間呼叫了一或多個 INSTEAD OF 觸發程序，第二次呼叫相同 AFTER 觸發程序時，仍會發生 AFTER 觸發程序的直接遞迴。</span><span class="sxs-lookup"><span data-stu-id="d52e9-129">Likewise, direct recursion of an AFTER trigger can occur when the same AFTER trigger is called for a second time, even if one or more INSTEAD OF triggers are called in between.</span></span> <span data-ttu-id="d52e9-130">例如，應用程式會更新資料表 **T4**。</span><span class="sxs-lookup"><span data-stu-id="d52e9-130">For example, an application updates table **T4**.</span></span> <span data-ttu-id="d52e9-131">這項更新會引發 INSTEAD OF 觸發程序 **Trig4** 。</span><span class="sxs-lookup"><span data-stu-id="d52e9-131">This update causes INSTEAD OF trigger **Trig4** to fire.</span></span> <span data-ttu-id="d52e9-132">**Trig4** 會更新資料表 **T5**。</span><span class="sxs-lookup"><span data-stu-id="d52e9-132">**Trig4** updates table **T5**.</span></span> <span data-ttu-id="d52e9-133">這項更新會引發 AFTER 觸發程序 **Trig5** 。</span><span class="sxs-lookup"><span data-stu-id="d52e9-133">This update causes AFTER trigger **Trig5** to fire.</span></span> <span data-ttu-id="d52e9-134">**Trig5** 會更新資料表 **T4**，而這項更新會再次引發 INSTEAD OF 觸發程序 **Trig4** 。</span><span class="sxs-lookup"><span data-stu-id="d52e9-134">**Trig5** updates table **T4**, and this update causes INSTEAD OF trigger **Trig4** to fire again.</span></span> <span data-ttu-id="d52e9-135">這個事件鏈結被視為 **Trig4**的直接遞迴。</span><span class="sxs-lookup"><span data-stu-id="d52e9-135">This chain of events is considered direct recursion for **Trig4**.</span></span>  
  
-   <span data-ttu-id="d52e9-136">間接遞迴</span><span class="sxs-lookup"><span data-stu-id="d52e9-136">Indirect recursion</span></span>  
  
     <span data-ttu-id="d52e9-137">觸發程序引發並執行會引發另一個相同類型之觸發程序 (AFTER 或 INSTEAD OF) 的動作時，會發生這類遞迴。</span><span class="sxs-lookup"><span data-stu-id="d52e9-137">This recursion occurs when a trigger fires and performs an action that causes another trigger of the same type (AFTER or INSTEAD OF) to fire.</span></span> <span data-ttu-id="d52e9-138">此第二個觸發程序執行使原始觸發程序再次引發的動作。</span><span class="sxs-lookup"><span data-stu-id="d52e9-138">This second trigger performs an action that causes the original trigger to fire again.</span></span> <span data-ttu-id="d52e9-139">換句話說，如果第二次呼叫 INSTEAD OF 觸發程序，則會在第一次與第二次呼叫之間呼叫另一個 INSTEAD OF 觸發程序時，發生間接遞迴。</span><span class="sxs-lookup"><span data-stu-id="d52e9-139">In other words, indirect recursion can occur when an INSTEAD OF trigger is called for a second time, but not until another INSTEAD OF trigger is called in between.</span></span> <span data-ttu-id="d52e9-140">同樣地，如果第二次呼叫 AFTER 觸發程序，則會在第一次與第二次呼叫之間呼叫另一個 AFTER 觸發程序時，發生間接遞迴。</span><span class="sxs-lookup"><span data-stu-id="d52e9-140">Likewise, indirect recursion can occur when an AFTER trigger is called for a second time, but not until another AFTER trigger is called in between.</span></span> <span data-ttu-id="d52e9-141">例如，應用程式會更新資料表 **T1**。</span><span class="sxs-lookup"><span data-stu-id="d52e9-141">For example, an application updates table **T1**.</span></span> <span data-ttu-id="d52e9-142">這項更新會引發 AFTER 觸發程序 **Trig1** 。</span><span class="sxs-lookup"><span data-stu-id="d52e9-142">This update causes AFTER trigger **Trig1** to fire.</span></span> <span data-ttu-id="d52e9-143">**Trig1** 會更新資料表 **T2**，而這項更新會引發 AFTER 觸發程序 **Trig2** 。</span><span class="sxs-lookup"><span data-stu-id="d52e9-143">**Trig1** updates table **T2**, and this update causes AFTER trigger **Trig2** to fire.</span></span> <span data-ttu-id="d52e9-144">接著，**Trig2** 會更新資料表 **T1** ，而這會再次引發 AFTER 觸發程序 **Trig1** 。</span><span class="sxs-lookup"><span data-stu-id="d52e9-144">**Trig2** in turn updates table **T1** that causes AFTER trigger **Trig1** to fire again.</span></span>  
  
 <span data-ttu-id="d52e9-145">RECURSIVE_TRIGGERS 資料庫選項設定為 OFF 時，只能防止 AFTER 觸發程序的直接遞迴。</span><span class="sxs-lookup"><span data-stu-id="d52e9-145">Only direct recursion of AFTER triggers is prevented when the RECURSIVE_TRIGGERS database option is set to OFF.</span></span> <span data-ttu-id="d52e9-146">若要停用 AFTER 觸發程序的間接遞迴，也請將 **巢狀觸發程序** 伺服器選項設定為 **0**。</span><span class="sxs-lookup"><span data-stu-id="d52e9-146">To disable indirect recursion of AFTER triggers, also set the **nested triggers** server option to **0**.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d52e9-147">範例</span><span class="sxs-lookup"><span data-stu-id="d52e9-147">Examples</span></span>  
 <span data-ttu-id="d52e9-148">下列範例顯示如何使用遞迴觸發程序來解決自我參考關聯 (又名為遞移封閉)。</span><span class="sxs-lookup"><span data-stu-id="d52e9-148">The following example shows using recursive triggers to solve a self-referencing relationship (also known as transitive closure).</span></span> <span data-ttu-id="d52e9-149">例如， `emp_mgr` 資料表定義下列項目：</span><span class="sxs-lookup"><span data-stu-id="d52e9-149">For example, the table `emp_mgr` defines the following:</span></span>  
  
-   <span data-ttu-id="d52e9-150">公司中的員工 (`emp`)。</span><span class="sxs-lookup"><span data-stu-id="d52e9-150">An employee (`emp`) in a company.</span></span>  
  
-   <span data-ttu-id="d52e9-151">每名員工的經理 (`mgr`)。</span><span class="sxs-lookup"><span data-stu-id="d52e9-151">The manager for each employee (`mgr`).</span></span>  
  
-   <span data-ttu-id="d52e9-152">在對每位員工報告的組織樹中員工的總數 (`NoOfReports`)。</span><span class="sxs-lookup"><span data-stu-id="d52e9-152">The total number of employees in the organizational tree reporting to each employee (`NoOfReports`).</span></span>  
  
 <span data-ttu-id="d52e9-153">當有新員工記錄插入時，遞迴 UPDATE 觸發程序可使 `NoOfReports` 資料行同時保持最新的資料。</span><span class="sxs-lookup"><span data-stu-id="d52e9-153">A recursive UPDATE trigger can be used to keep the `NoOfReports` column up-to-date as new employee records are inserted.</span></span> <span data-ttu-id="d52e9-154">INSERT 觸發程序則可在更新經理記錄的 `NoOfReports` 資料行時，遞迴更新在經理階層架構之上其他記錄的 `NoOfReports` 資料行。</span><span class="sxs-lookup"><span data-stu-id="d52e9-154">The INSERT trigger updates the `NoOfReports` column of the manager record, which recursively updates the `NoOfReports` column of other records up the management hierarchy.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
-- Turn recursive triggers ON in the database.  
ALTER DATABASE AdventureWorks2012  
   SET RECURSIVE_TRIGGERS ON;  
GO  
CREATE TABLE dbo.emp_mgr (  
   emp char(30) PRIMARY KEY,  
    mgr char(30) NULL FOREIGN KEY REFERENCES emp_mgr(emp),  
    NoOfReports int DEFAULT 0  
);  
GO  
CREATE TRIGGER dbo.emp_mgrins ON dbo.emp_mgr  
FOR INSERT  
AS  
DECLARE @e char(30), @m char(30);  
DECLARE c1 CURSOR FOR  
   SELECT emp_mgr.emp  
   FROM   emp_mgr, inserted  
   WHERE emp_mgr.emp = inserted.mgr;  
  
OPEN c1;  
FETCH NEXT FROM c1 INTO @e;  
WHILE @@fetch_status = 0  
BEGIN  
   UPDATE dbo.emp_mgr  
   SET emp_mgr.NoOfReports = emp_mgr.NoOfReports + 1 -- Add 1 for newly  
   WHERE emp_mgr.emp = @e ;                           -- added employee.  
  
   FETCH NEXT FROM c1 INTO @e;  
END  
CLOSE c1;  
DEALLOCATE c1;  
GO  
-- This recursive UPDATE trigger works assuming:  
--   1. Only singleton updates on emp_mgr.  
--   2. No inserts in the middle of the org tree.  
CREATE TRIGGER dbo.emp_mgrupd ON dbo.emp_mgr FOR UPDATE  
AS  
IF UPDATE (mgr)  
BEGIN  
   UPDATE dbo.emp_mgr  
   SET emp_mgr.NoOfReports = emp_mgr.NoOfReports + 1 -- Increment mgr's  
   FROM inserted                            -- (no. of reports) by  
   WHERE emp_mgr.emp = inserted.mgr;         -- 1 for the new report.  
  
   UPDATE dbo.emp_mgr  
   SET emp_mgr.NoOfReports = emp_mgr.NoOfReports - 1 -- Decrement mgr's  
   FROM deleted                             -- (no. of reports) by 1  
   WHERE emp_mgr.emp = deleted.mgr;          -- for the new report.  
END  
GO  
-- Insert some test data rows.  
INSERT dbo.emp_mgr(emp, mgr) VALUES  
    ('Harry', NULL)  
    ,('Alice', 'Harry')  
    ,('Paul', 'Alice')  
    ,('Joe', 'Alice')  
    ,('Dave', 'Joe');  
GO  
SELECT emp,mgr,NoOfReports  
FROM dbo.emp_mgr;  
GO  
-- Change Dave's manager from Joe to Harry  
UPDATE dbo.emp_mgr SET mgr = 'Harry'  
WHERE emp = 'Dave';  
GO  
SELECT emp,mgr,NoOfReports FROM emp_mgr;  
  
GO  
```  
  
 <span data-ttu-id="d52e9-155">更新前的結果如下。</span><span class="sxs-lookup"><span data-stu-id="d52e9-155">Here are the results before the update.</span></span>  
  
```  
emp                            mgr                           NoOfReports  
------------------------------ ----------------------------- -----------  
Alice                          Harry                          2  
Dave                           Joe                            0  
Harry                          NULL                           1  
Joe                            Alice                          1  
Paul                           Alice                          0  
```  
  
 <span data-ttu-id="d52e9-156">更新後的結果如下。</span><span class="sxs-lookup"><span data-stu-id="d52e9-156">Here are the results after the update.</span></span>  
  
```  
emp                            mgr                           NoOfReports  
------------------------------ ----------------------------- -----------  
Alice                          Harry                          2  
Dave                           Harry                          0  
Harry                          NULL                           2  
Joe                            Alice                          0  
Paul                           Alice                          0  
```  
  
 <span data-ttu-id="d52e9-157">**若要設定巢狀觸發程序選項**</span><span class="sxs-lookup"><span data-stu-id="d52e9-157">**To set the nested triggers option**</span></span>  
  
-   [<span data-ttu-id="d52e9-158">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d52e9-158">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
 <span data-ttu-id="d52e9-159">**若要設定 RECURSIVE_TRIGGERS 資料庫選項**</span><span class="sxs-lookup"><span data-stu-id="d52e9-159">**To set the RECURSIVE_TRIGGERS database option**</span></span>  
  
-   [<span data-ttu-id="d52e9-160">ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d52e9-160">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
## <a name="see-also"></a><span data-ttu-id="d52e9-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d52e9-161">See Also</span></span>  
 <span data-ttu-id="d52e9-162">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d52e9-162">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 [<span data-ttu-id="d52e9-163">設定 nested triggers 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="d52e9-163">Configure the nested triggers Server Configuration Option</span></span>](../../database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option.md)  
  
  
