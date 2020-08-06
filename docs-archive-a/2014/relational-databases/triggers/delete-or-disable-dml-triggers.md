---
title: 刪除或停用 DML 觸發程序 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DML triggers, disabling
- removing DML triggers
- disabling DML triggers
- dropping DML triggers
- deleting DML triggers
- DML triggers, removing
ms.assetid: 0f97f953-33c5-4b26-afeb-db2a26ce38b4
author: rothja
ms.author: jroth
ms.openlocfilehash: 39b345ade1258987df06938791ac0024e8612365
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606136"
---
# <a name="delete-or-disable-dml-triggers"></a><span data-ttu-id="b10a1-102">刪除或停用 DML 觸發程序</span><span class="sxs-lookup"><span data-stu-id="b10a1-102">Delete or Disable DML Triggers</span></span>
  <span data-ttu-id="b10a1-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 刪除或停用 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的 DML 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b10a1-103">This topic describes how to delete or disable a DML trigger in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="b10a1-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="b10a1-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b10a1-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="b10a1-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b10a1-106">建議</span><span class="sxs-lookup"><span data-stu-id="b10a1-106">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="b10a1-107">安全性</span><span class="sxs-lookup"><span data-stu-id="b10a1-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b10a1-108">**若要刪除或停用 DML 觸發程序，使用：**</span><span class="sxs-lookup"><span data-stu-id="b10a1-108">**To delete or disable a DML trigger, using:**</span></span>  
  
     [<span data-ttu-id="b10a1-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b10a1-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b10a1-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b10a1-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b10a1-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="b10a1-111">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="b10a1-112">建議</span><span class="sxs-lookup"><span data-stu-id="b10a1-112">Recommendations</span></span>  
  
-   <span data-ttu-id="b10a1-113">刪除觸發程序時，會從目前的資料庫卸除它。</span><span class="sxs-lookup"><span data-stu-id="b10a1-113">When a trigger is deleted, it is dropped from the current database.</span></span> <span data-ttu-id="b10a1-114">其所依據的資料表和資料不受影響。</span><span class="sxs-lookup"><span data-stu-id="b10a1-114">The table and the data upon which it is based are not affected.</span></span> <span data-ttu-id="b10a1-115">刪除資料表時會自動刪除資料表上的所有觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b10a1-115">Deleting a table automatically deletes any triggers on the table.</span></span>  
  
-   <span data-ttu-id="b10a1-116">觸發程序預設為在建立時啟用。</span><span class="sxs-lookup"><span data-stu-id="b10a1-116">A trigger is enabled by default when it is created.</span></span>  
  
-   <span data-ttu-id="b10a1-117">即使停用觸發程序，也不會卸除它。</span><span class="sxs-lookup"><span data-stu-id="b10a1-117">Disabling a trigger does not drop it.</span></span> <span data-ttu-id="b10a1-118">該觸發程序仍然會以物件形式存在於目前的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="b10a1-118">The trigger still exists as an object in the current database.</span></span> <span data-ttu-id="b10a1-119">不過，當設計此觸發程序的 INSERT、UPDATE 或 DELETE 陳述式執行時，不會引發觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b10a1-119">However, the trigger will not fire when any INSERT, UPDATE, or DELETE statement on which it was programmed is executed.</span></span> <span data-ttu-id="b10a1-120">已停用的觸發程序可重新啟用。</span><span class="sxs-lookup"><span data-stu-id="b10a1-120">Triggers that are disabled can be reenabled.</span></span> <span data-ttu-id="b10a1-121">啟用觸發程序並不會重新建立它。</span><span class="sxs-lookup"><span data-stu-id="b10a1-121">Enabling a trigger does not re-create it.</span></span> <span data-ttu-id="b10a1-122">觸發程序會以當初建立的相同方式引發。</span><span class="sxs-lookup"><span data-stu-id="b10a1-122">The trigger fires in the same manner as when it was originally created.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b10a1-123">Security</span><span class="sxs-lookup"><span data-stu-id="b10a1-123">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b10a1-124">權限</span><span class="sxs-lookup"><span data-stu-id="b10a1-124">Permissions</span></span>  
 <span data-ttu-id="b10a1-125">刪除 DML 觸發程序需要定義觸發程序所在資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="b10a1-125">To delete a DML trigger requires ALTER permission on the table or view on which the trigger is defined.</span></span>  
  
 <span data-ttu-id="b10a1-126">若要停用或啟用 DML 觸發程序，使用者至少要對建立該觸發程序的資料表或檢視，具備 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="b10a1-126">To disable or enable a DML trigger, at a minimum, a user must have ALTER permission on the table or view on which the trigger was created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b10a1-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b10a1-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-dml-trigger"></a><span data-ttu-id="b10a1-128">刪除 DML 觸發程序</span><span class="sxs-lookup"><span data-stu-id="b10a1-128">To delete a DML trigger</span></span>  
  
1.  <span data-ttu-id="b10a1-129">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="b10a1-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="b10a1-130">展開您要的資料庫，展開 **[資料表]** ，然後展開包含您要刪除之觸發程序的資料表。</span><span class="sxs-lookup"><span data-stu-id="b10a1-130">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger that you want to delete.</span></span>  
  
3.  <span data-ttu-id="b10a1-131">展開 **[觸發程序]** ，以滑鼠右鍵按一下要刪除的觸發程序，然後按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="b10a1-131">Expand **Triggers**, right-click the trigger to delete, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="b10a1-132">在 **[刪除物件]** 對話方塊中，確認要刪除的觸發程序，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="b10a1-132">In the **Delete Object** dialog box, verify the trigger to delete, and then click **OK**.</span></span>  
  
#### <a name="to-disable-and-enable-a-dml-trigger"></a><span data-ttu-id="b10a1-133">若要停用和啟用 DML 觸發程序</span><span class="sxs-lookup"><span data-stu-id="b10a1-133">To disable and enable a DML trigger</span></span>  
  
1.  <span data-ttu-id="b10a1-134">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="b10a1-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="b10a1-135">展開您要的資料庫，展開 **[資料表]** ，然後展開包含您要停用之觸發程序的資料表。</span><span class="sxs-lookup"><span data-stu-id="b10a1-135">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger that you want to disable.</span></span>  
  
3.  <span data-ttu-id="b10a1-136">展開 **[觸發程序]** ，以滑鼠右鍵按一下要停用的觸發程序，然後按一下 **[停用]** 。</span><span class="sxs-lookup"><span data-stu-id="b10a1-136">Expand **Triggers**, right-click the trigger to disable, and then click **Disable**.</span></span>  
  
4.  <span data-ttu-id="b10a1-137">若要啟用觸發程序，請按一下 **[啟用]** 。</span><span class="sxs-lookup"><span data-stu-id="b10a1-137">To enable the trigger, click **Enable**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b10a1-138">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b10a1-138">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-dml-trigger"></a><span data-ttu-id="b10a1-139">刪除 DML 觸發程序</span><span class="sxs-lookup"><span data-stu-id="b10a1-139">To delete a DML trigger</span></span>  
  
1.  <span data-ttu-id="b10a1-140">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b10a1-140">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b10a1-141">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="b10a1-141">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b10a1-142">將下列範例複製並貼入查詢視窗中。</span><span class="sxs-lookup"><span data-stu-id="b10a1-142">Copy and paste the following examples into the query window.</span></span> <span data-ttu-id="b10a1-143">執行 [CREATE TRIGGER](/sql/t-sql/statements/create-trigger-transact-sql) 陳述式即可建立 `Sales.bonus_reminder` 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b10a1-143">Execute the [CREATE TRIGGER](/sql/t-sql/statements/create-trigger-transact-sql) statement to create the `Sales.bonus_reminder` trigger.</span></span> <span data-ttu-id="b10a1-144">若要刪除觸發程序，請執行 [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b10a1-144">To delete the trigger, execute the [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) statement.</span></span>  
  
```sql  
--Create the trigger.  
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
--Delete the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ('Sales.bonus_reminder', 'TR') IS NOT NULL  
   DROP TRIGGER Sales.bonus_reminder;  
GO  
  
```  
  
#### <a name="to-disable-and-enable-a-dml-trigger"></a><span data-ttu-id="b10a1-145">若要停用和啟用 DML 觸發程序</span><span class="sxs-lookup"><span data-stu-id="b10a1-145">To disable and enable a DML trigger</span></span>  
  
1.  <span data-ttu-id="b10a1-146">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b10a1-146">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b10a1-147">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="b10a1-147">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b10a1-148">將下列範例複製並貼入查詢視窗中。</span><span class="sxs-lookup"><span data-stu-id="b10a1-148">Copy and paste the following examples into the query window.</span></span> <span data-ttu-id="b10a1-149">執行 [CREATE TRIGGER](/sql/t-sql/statements/create-trigger-transact-sql) 陳述式即可建立 `Sales.bonus_reminder` 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b10a1-149">Execute the [CREATE TRIGGER](/sql/t-sql/statements/create-trigger-transact-sql) statement to create the `Sales.bonus_reminder` trigger.</span></span> <span data-ttu-id="b10a1-150">若要停用和啟用觸發程序，請分別執行 [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) 和 [ENABLE TRIGGER](/sql/t-sql/statements/enable-trigger-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b10a1-150">To disable and enable the trigger, execute the [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) and [ENABLE TRIGGER](/sql/t-sql/statements/enable-trigger-transact-sql) statements, respectively.</span></span>  
  
```sql  
--Create the trigger.  
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
--Disable the trigger.  
USE AdventureWorks2012;  
GO  
DISABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
  
```  
  
```sql  
--Enable the trigger.  
USE AdventureWorks2012;  
GO  
ENABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="b10a1-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b10a1-151">See Also</span></span>  
 <span data-ttu-id="b10a1-152">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b10a1-152">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span></span>  
 <span data-ttu-id="b10a1-153">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b10a1-153">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="b10a1-154">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b10a1-154">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span></span>  
 <span data-ttu-id="b10a1-155">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b10a1-155">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="b10a1-156">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b10a1-156">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="b10a1-157">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b10a1-157">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span></span>  
 <span data-ttu-id="b10a1-158">[取得關於 DML 觸發程序的詳細資訊](dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="b10a1-158">[Get Information About DML Triggers](dml-triggers.md) </span></span>  
 <span data-ttu-id="b10a1-159">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b10a1-159">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span></span>  
 <span data-ttu-id="b10a1-160">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b10a1-160">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span></span>  
 <span data-ttu-id="b10a1-161">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b10a1-161">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span></span>  
 <span data-ttu-id="b10a1-162">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b10a1-162">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="b10a1-163">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b10a1-163">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="b10a1-164">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b10a1-164">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span></span>  
 <span data-ttu-id="b10a1-165">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b10a1-165">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span></span>  
 <span data-ttu-id="b10a1-166">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b10a1-166">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="b10a1-167">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b10a1-167">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span></span>  
 [<span data-ttu-id="b10a1-168">sys.server_assembly_modules &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b10a1-168">sys.server_assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
  
