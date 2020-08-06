---
title: 修改或重新命名 DML 觸發程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- renaming triggers
- modifying triggers
- DML triggers, modifying
ms.assetid: c7317eec-c0e9-479e-a4a7-83b6b6c58d59
author: rothja
ms.author: jroth
ms.openlocfilehash: 65bb13552b552d54b5547eadedc412977e423a57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606119"
---
# <a name="modify-or-rename-dml-triggers"></a><span data-ttu-id="ccb3d-102">修改或重新命名 DML 觸發程序</span><span class="sxs-lookup"><span data-stu-id="ccb3d-102">Modify or Rename DML Triggers</span></span>
  <span data-ttu-id="ccb3d-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 修改或重新命名 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的 DML 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-103">This topic describes how to modify or rename a DML trigger in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ccb3d-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="ccb3d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ccb3d-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="ccb3d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ccb3d-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="ccb3d-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ccb3d-107">建議</span><span class="sxs-lookup"><span data-stu-id="ccb3d-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="ccb3d-108">安全性</span><span class="sxs-lookup"><span data-stu-id="ccb3d-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ccb3d-109">**使用下列方法修改或重新命名 DML 觸發程序：**</span><span class="sxs-lookup"><span data-stu-id="ccb3d-109">**To modify or rename a DML trigger, using:**</span></span>  
  
     [<span data-ttu-id="ccb3d-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ccb3d-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ccb3d-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ccb3d-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ccb3d-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="ccb3d-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ccb3d-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="ccb3d-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ccb3d-114">當您重新命名觸發程序時，觸發程序必須位於目前資料庫中，而且新名稱必須遵照 [識別碼](../databases/database-identifiers.md)的規則。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-114">When you rename a trigger, the trigger must be in the current database, and the new name must follow the rules for [identifiers](../databases/database-identifiers.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="ccb3d-115">建議</span><span class="sxs-lookup"><span data-stu-id="ccb3d-115">Recommendations</span></span>  
  
-   <span data-ttu-id="ccb3d-116">我們建議您不要使用 [sp_rename](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) 預存程序重新命名觸發程序。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-116">We recommend you do not use the [sp_rename](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) stored procedure to rename a trigger.</span></span> <span data-ttu-id="ccb3d-117">變更物件名稱的任何部分，可能破壞指令碼和預存程序。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-117">Changing any part of an object name can break scripts and stored procedures.</span></span> <span data-ttu-id="ccb3d-118">重新命名觸發程序並不會變更 [sys.sql_modules](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) 目錄檢視 definition 資料行中對應的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-118">Renaming a trigger does not change the name of the corresponding object name in the definition column of the [sys.sql_modules](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) catalog view.</span></span> <span data-ttu-id="ccb3d-119">我們建議您先卸除，再重新建立觸發程序。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-119">We recommend that you drop and re-create the trigger instead.</span></span>  
  
-   <span data-ttu-id="ccb3d-120">如果您變更 DML 觸發程序所參考的物件名稱，就必須修改觸發程序以反映新的名稱。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-120">If you change the name of an object referenced by a DML trigger, you must modify the trigger so that its text reflects the new name.</span></span> <span data-ttu-id="ccb3d-121">因此，在您重新命名物件之前，請先顯示此物件的相依性，以判斷是否有任何觸發程序受到相關變更的影響。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-121">Therefore, before you rename an object, display the dependencies of the object first to determine whether any triggers are affected by the proposed change.</span></span>  
  
-   <span data-ttu-id="ccb3d-122">亦可將 DML 觸發程序的定義修改為加密的形態</span><span class="sxs-lookup"><span data-stu-id="ccb3d-122">A DML trigger can also be modified to encrypt its definition.</span></span>  
  
-   <span data-ttu-id="ccb3d-123">若要檢視觸發程序的相依性，您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或下列函數和目錄檢視：</span><span class="sxs-lookup"><span data-stu-id="ccb3d-123">To view the dependencies of a trigger, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or the following function and catalog views:</span></span>  
  
    -   [<span data-ttu-id="ccb3d-124">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ccb3d-124">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
    -   [<span data-ttu-id="ccb3d-125">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ccb3d-125">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
    -   [<span data-ttu-id="ccb3d-126">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ccb3d-126">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ccb3d-127">Security</span><span class="sxs-lookup"><span data-stu-id="ccb3d-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ccb3d-128">權限</span><span class="sxs-lookup"><span data-stu-id="ccb3d-128">Permissions</span></span>  
 <span data-ttu-id="ccb3d-129">變更 DML 觸發程序需要定義觸發程序的資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-129">To alter a DML trigger requires ALTER permission on the table or view on which the trigger is defined.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ccb3d-130">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ccb3d-130">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-dml-trigger"></a><span data-ttu-id="ccb3d-131">若要修改 DML 觸發程序</span><span class="sxs-lookup"><span data-stu-id="ccb3d-131">To modify a DML trigger</span></span>  
  
1.  <span data-ttu-id="ccb3d-132">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ccb3d-133">展開您要的資料庫，展開 **[資料表]** ，然後展開包含您要修改之觸發程序的資料表。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-133">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger that you want to modify.</span></span>  
  
3.  <span data-ttu-id="ccb3d-134">展開 **[觸發程序]** ，以滑鼠右鍵按一下要修改的觸發程序，再按一下 **[修改]** 。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-134">Expand **Triggers**, right-click the trigger to modify, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="ccb3d-135">修改觸發程序，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-135">Modify the trigger, and then click **Execute**.</span></span>  
  
#### <a name="to-rename-a-dml-trigger"></a><span data-ttu-id="ccb3d-136">若要重新命名 DML 觸發程序</span><span class="sxs-lookup"><span data-stu-id="ccb3d-136">To rename a DML trigger</span></span>  
  
1.  <span data-ttu-id="ccb3d-137">[刪除觸發程序](../triggers/dml-triggers.md) ，也就是要重新命名的觸發程序。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-137">[Delete the trigger](../triggers/dml-triggers.md) that you want to rename.</span></span>  
  
2.  <span data-ttu-id="ccb3d-138">[重新建立觸發程序](../triggers/create-dml-triggers.md)，並指定新名稱。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-138">[Re-create the trigger](../triggers/create-dml-triggers.md), specifying the new name.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ccb3d-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ccb3d-139">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-trigger-using-alter-trigger"></a><span data-ttu-id="ccb3d-140">若要使用 ALTER TRIGGER 修改觸發程序</span><span class="sxs-lookup"><span data-stu-id="ccb3d-140">To modify a trigger using ALTER TRIGGER</span></span>  
  
1.  <span data-ttu-id="ccb3d-141">連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-141">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ccb3d-142">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ccb3d-143">複製下列範例並貼入查詢中。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-143">Copy and paste the following examples into the query.</span></span> <span data-ttu-id="ccb3d-144">執行第一個範例，建立當使用者嘗試在 `SalesPersonQuotaHistory` 資料表中加入或變更資料時，將使用者定義訊息列印到用戶端的 DML 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-144">Execute the first example to create a DML trigger that prints a user-defined message to the client when a user tries to add or change data in the `SalesPersonQuotaHistory` table.</span></span> <span data-ttu-id="ccb3d-145">執行 [ALTER TRIGGER](/sql/t-sql/statements/alter-trigger-transact-sql) 陳述式修改觸發程式，使它只在 `INSERT` 活動上引發。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-145">Execute the [ALTER TRIGGER](/sql/t-sql/statements/alter-trigger-transact-sql) statement to modify the trigger to fire only on `INSERT` activities.</span></span> <span data-ttu-id="ccb3d-146">這個觸發程序很有用，因為它會提醒使用者在這份資料表中更新或插入資料列，以便同時通知 `Compensation` 部門。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-146">This trigger is helpful because it reminds the user that updates or inserts rows into this table to also notify the `Compensation` department.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```sql  
USE AdventureWorks2012;  
GO  
ALTER TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
AFTER INSERT  
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
#### <a name="to-rename-a-trigger-using-drop-trigger-and-alter-trigger"></a><span data-ttu-id="ccb3d-147">若要使用 DROP TRIGGER 和 ALTER TRIGGER 重新命名觸發程序</span><span class="sxs-lookup"><span data-stu-id="ccb3d-147">To rename a trigger using DROP TRIGGER and ALTER TRIGGER</span></span>  
  
1.  <span data-ttu-id="ccb3d-148">連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-148">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ccb3d-149">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ccb3d-150">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-150">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ccb3d-151">此範例會使用 [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) 和 [ALTER TRIGGER](/sql/t-sql/statements/alter-trigger-transact-sql) 陳述式將 `Sales.bonus_reminder` 觸發程序重新命名為 `Sales.bonus_reminder_2`。</span><span class="sxs-lookup"><span data-stu-id="ccb3d-151">This example use the [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) and [ALTER TRIGGER](/sql/t-sql/statements/alter-trigger-transact-sql) statements to rename the `Sales.bonus_reminder` trigger to `Sales.bonus_reminder_2`.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder_2  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="ccb3d-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccb3d-152">See Also</span></span>  
 <span data-ttu-id="ccb3d-153">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccb3d-153">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="ccb3d-154">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccb3d-154">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span></span>  
 <span data-ttu-id="ccb3d-155">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccb3d-155">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="ccb3d-156">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccb3d-156">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="ccb3d-157">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccb3d-157">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span></span>  
 <span data-ttu-id="ccb3d-158">[sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccb3d-158">[sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) </span></span>  
 <span data-ttu-id="ccb3d-159">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccb3d-159">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span></span>  
 <span data-ttu-id="ccb3d-160">[取得關於 DML 觸發程序的詳細資訊](../triggers/get-information-about-dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="ccb3d-160">[Get Information About DML Triggers](../triggers/get-information-about-dml-triggers.md) </span></span>  
 <span data-ttu-id="ccb3d-161">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccb3d-161">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span></span>  
 <span data-ttu-id="ccb3d-162">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccb3d-162">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span></span>  
 <span data-ttu-id="ccb3d-163">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccb3d-163">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span></span>  
 <span data-ttu-id="ccb3d-164">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccb3d-164">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="ccb3d-165">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccb3d-165">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="ccb3d-166">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccb3d-166">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span></span>  
 <span data-ttu-id="ccb3d-167">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccb3d-167">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span></span>  
 <span data-ttu-id="ccb3d-168">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccb3d-168">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="ccb3d-169">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccb3d-169">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span></span>  
 [<span data-ttu-id="ccb3d-170">sys.server_assembly_modules &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ccb3d-170">sys.server_assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
  
