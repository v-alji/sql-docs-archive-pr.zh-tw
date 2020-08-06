---
title: 取得 DML 觸發程序的資訊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- metadata [SQL Server], triggers
- viewing DML triggers
- DML triggers, metadata
- displaying DML triggers
- status information [SQL Server], triggers
- DML triggers, viewing
ms.assetid: 37574aac-181d-4aca-a2cc-8abff64237dc
author: rothja
ms.author: jroth
ms.openlocfilehash: 2f65976d2f517137e23bd9e5e1c98cc76324bc49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606132"
---
# <a name="get-information-about-dml-triggers"></a><span data-ttu-id="5f221-102">取得關於 DML 觸發程序的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="5f221-102">Get Information About DML Triggers</span></span>
  <span data-ttu-id="5f221-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 取得有關 [!INCLUDE[tsql](../../includes/tsql-md.md)]中 DML 觸發程序的資訊。</span><span class="sxs-lookup"><span data-stu-id="5f221-103">This topic describes how to get information about DML triggers in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="5f221-104">這項資訊可能包括資料表上觸發程序的類型、觸發程序的名稱、其擁有者，以及建立或修改的日期。</span><span class="sxs-lookup"><span data-stu-id="5f221-104">This information can include the types of triggers on a table, the name of a trigger, its owner and the date it was created or modified.</span></span> <span data-ttu-id="5f221-105">如果觸發程序建立時並未加密，則您會取得觸發程序的定義。</span><span class="sxs-lookup"><span data-stu-id="5f221-105">If the trigger was not encrypted when it was created, you obtain the definition of the trigger.</span></span> <span data-ttu-id="5f221-106">定義可幫助您了解觸發程序如何影響本身定義所在的資料表。</span><span class="sxs-lookup"><span data-stu-id="5f221-106">You can use the definition to help you understand how a trigger affects the table up on which it is defined.</span></span> <span data-ttu-id="5f221-107">另外，您可以找出特定觸發程序所使用的物件。</span><span class="sxs-lookup"><span data-stu-id="5f221-107">Also, you can find out the objects that a specific trigger uses.</span></span> <span data-ttu-id="5f221-108">有了這項資訊，您就可以識別影響觸發程序的物件 (如果已在資料庫中變更或刪除這些物件)。</span><span class="sxs-lookup"><span data-stu-id="5f221-108">With this information, you can identify the objects that affect the trigger if they are changed or deleted in the database.</span></span>  
  
 <span data-ttu-id="5f221-109">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="5f221-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5f221-110">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="5f221-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5f221-111">安全性</span><span class="sxs-lookup"><span data-stu-id="5f221-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5f221-112">**若要取得 DML 觸發程序的相關資訊，使用：**</span><span class="sxs-lookup"><span data-stu-id="5f221-112">**To get information about DML triggers, using:**</span></span>  
  
     [<span data-ttu-id="5f221-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5f221-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5f221-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5f221-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5f221-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="5f221-115">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5f221-116">Security</span><span class="sxs-lookup"><span data-stu-id="5f221-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5f221-117">權限</span><span class="sxs-lookup"><span data-stu-id="5f221-117">Permissions</span></span>  
 <span data-ttu-id="5f221-118">**sys.sql.modules**、 **sys.object**、 **sys.triggers**、 **sys.events**、 **sys.trigger_events**</span><span class="sxs-lookup"><span data-stu-id="5f221-118">**sys.sql.modules**, **sys.object**, **sys.triggers**, **sys.events**, **sys.trigger_events**</span></span>  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] <span data-ttu-id="5f221-119">如需相關資訊，請參閱 [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="5f221-119">For more information, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
 <span data-ttu-id="5f221-120">OBJECT_DEFINITION、OBJECTPROPERTY、 **sp_helptext**</span><span class="sxs-lookup"><span data-stu-id="5f221-120">OBJECT_DEFINITION, OBJECTPROPERTY, **sp_helptext**</span></span>  
 <span data-ttu-id="5f221-121">需要 **public** 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="5f221-121">Requires membership in the **public** role.</span></span> <span data-ttu-id="5f221-122">凡具有下列任一權限的物件擁有者或承授者，都看得到使用者物件的定義：ALTER、CONTROL、TAKE OWNERSHIP 或 VIEW DEFINITION。</span><span class="sxs-lookup"><span data-stu-id="5f221-122">The definition of user objects is visible to the object owner or grantees that have any one of the following permissions: ALTER, CONTROL, TAKE OWNERSHIP, or VIEW DEFINITION.</span></span> <span data-ttu-id="5f221-123">**db_owner**、 **db_ddladmin**和 **db_securityadmin** 固定資料庫角色的成員隱含地擁有這些權限。</span><span class="sxs-lookup"><span data-stu-id="5f221-123">These permissions are implicitly held by members of the **db_owner**, **db_ddladmin**, and **db_securityadmin** fixed database roles.</span></span>  
  
 <span data-ttu-id="5f221-124">**sys.sql_expression_dependencies**</span><span class="sxs-lookup"><span data-stu-id="5f221-124">**sys.sql_expression_dependencies**</span></span>  
 <span data-ttu-id="5f221-125">需要資料庫的 VIEW DEFINITION 權限和資料庫之 **sys.sql_expression_dependencies** 的 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="5f221-125">Requires VIEW DEFINITION permission on the database and SELECT permission on **sys.sql_expression_dependencies** for the database.</span></span> <span data-ttu-id="5f221-126">依預設，SELECT 權限只授與 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="5f221-126">By default, SELECT permission is granted only to members of the **db_owner** fixed database role.</span></span> <span data-ttu-id="5f221-127">當 SELECT 和 VIEW DEFINITION 權限授與其他使用者時，被授與者就可以檢視資料庫中的所有相依性。</span><span class="sxs-lookup"><span data-stu-id="5f221-127">When SELECT and VIEW DEFINITION permissions are granted to another user, the grantee can view all dependencies in the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5f221-128">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5f221-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-definition-of-a-dml-trigger"></a><span data-ttu-id="5f221-129">若要檢視 DML 觸發程序的定義</span><span class="sxs-lookup"><span data-stu-id="5f221-129">To view the definition of a DML trigger</span></span>  
  
1.  <span data-ttu-id="5f221-130">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="5f221-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="5f221-131">展開您要的資料庫，展開 **[資料表]** ，然後展開包含您要檢視其定義之觸發程序的資料表。</span><span class="sxs-lookup"><span data-stu-id="5f221-131">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger for which you want to view the definition.</span></span>  
  
3.  <span data-ttu-id="5f221-132">展開 [觸發程序]，以滑鼠右鍵按一下您要的觸發程序，然後按一下 [修改]。</span><span class="sxs-lookup"><span data-stu-id="5f221-132">Expand **Triggers**, right-click the trigger you want, and then click **Modify**.</span></span> <span data-ttu-id="5f221-133">DML 觸發程序的定義會出現在查詢視窗中。</span><span class="sxs-lookup"><span data-stu-id="5f221-133">The definition of the DML trigger appears in the query window.</span></span>  
  
#### <a name="to-view-the-dependencies-of-a-dml-trigger"></a><span data-ttu-id="5f221-134">若要檢視 DML 觸發程序的相依性</span><span class="sxs-lookup"><span data-stu-id="5f221-134">To view the dependencies of a DML trigger</span></span>  
  
1.  <span data-ttu-id="5f221-135">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="5f221-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="5f221-136">展開您要的資料庫，展開 **[資料表]** ，然後展開包含您要檢視的觸發程序及其相依性的資料表。</span><span class="sxs-lookup"><span data-stu-id="5f221-136">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger and its dependencies that you want to view.</span></span>  
  
3.  <span data-ttu-id="5f221-137">展開 [觸發程序]，以滑鼠右鍵按一下您要的觸發程序，然後按一下 [檢視相依性]。</span><span class="sxs-lookup"><span data-stu-id="5f221-137">Expand **Triggers**, right-click the trigger you want, and then click **View Dependencies**.</span></span>  
  
4.  <span data-ttu-id="5f221-138">在 [物件相依性] 視窗中，若要檢視相依於 DML 觸發程序的物件，請選取 [相依於 \<DML trigger name> 的物件]。</span><span class="sxs-lookup"><span data-stu-id="5f221-138">In the **Object Dependencies** window, to view the objects that depend on the DML trigger, select **Objects that depend on \<DML trigger name>**.</span></span> <span data-ttu-id="5f221-139">物件會出現在 **[相依性]** 區域中。</span><span class="sxs-lookup"><span data-stu-id="5f221-139">The objects appear in the **Dependencies** area.</span></span>  
  
     <span data-ttu-id="5f221-140">若要檢視 DML 所相依的物件，請選取 [\<DML trigger name> 所相依的物件]。</span><span class="sxs-lookup"><span data-stu-id="5f221-140">To view the objects on which the DML depends, select **Objects on which \<DML trigger name> depends**.</span></span> <span data-ttu-id="5f221-141">物件會出現在 **[相依性]** 區域中。</span><span class="sxs-lookup"><span data-stu-id="5f221-141">The objects appear in the **Dependencies** area.</span></span> <span data-ttu-id="5f221-142">展開每個節點，查看所有物件。</span><span class="sxs-lookup"><span data-stu-id="5f221-142">Expand each node to see all the objects.</span></span>  
  
5.  <span data-ttu-id="5f221-143">若要取得出現在 **[相依性]** 區域中之物件的相關資訊，請按一下該物件。</span><span class="sxs-lookup"><span data-stu-id="5f221-143">To obtain information about an object that appears in the **Dependencies** area, click the object.</span></span> <span data-ttu-id="5f221-144">**[選取的物件]** 欄位的 **[名稱]** 、 **[類型]** 和 **[相依性類型]** 方塊中會提供資訊。</span><span class="sxs-lookup"><span data-stu-id="5f221-144">In the **Selected object** field, information is provided in the **Name**, **Type**, and **Dependency type** boxes.</span></span>  
  
6.  <span data-ttu-id="5f221-145">若要關閉 **[物件相依性]** 視窗，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="5f221-145">To close the **Object Dependencies** window, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5f221-146">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5f221-146">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-definition-of-a-dml-trigger"></a><span data-ttu-id="5f221-147">若要檢視 DML 觸發程序的定義</span><span class="sxs-lookup"><span data-stu-id="5f221-147">To view the definition of a DML trigger</span></span>  
  
1.  <span data-ttu-id="5f221-148">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5f221-148">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5f221-149">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="5f221-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5f221-150">將下列其中一個範例複製並貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="5f221-150">Copy and paste one of the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="5f221-151">每個範例都會說明如何檢視 `iuPerson` 觸發程序的定義。</span><span class="sxs-lookup"><span data-stu-id="5f221-151">Each example shows how you can view the definition of the `iuPerson` trigger.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT definition   
FROM sys.sql_modules  
WHERE object_id = OBJECT_ID(N'Person.iuPerson');   
GO  
```  
  
```sql  
USE AdventureWorks2012;   
GO  
SELECT OBJECT_DEFINITION (OBJECT_ID(N'Person.iuPerson')) AS ObjectDefinition;   
GO  
  
```  
  
```sql  
USE AdventureWorks2012;   
GO  
EXEC sp_helptext 'Person.iuPerson'  
GO  
  
```  
  
#### <a name="to-view-the-dependencies-of-a-dml-trigger"></a><span data-ttu-id="5f221-152">若要檢視 DML 觸發程序的相依性</span><span class="sxs-lookup"><span data-stu-id="5f221-152">To view the dependencies of a DML trigger</span></span>  
  
1.  <span data-ttu-id="5f221-153">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5f221-153">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5f221-154">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="5f221-154">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5f221-155">將下列其中一個範例複製並貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="5f221-155">Copy and paste one of the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="5f221-156">每個範例都會說明如何檢視 `iuPerson` 觸發程序的相依性。</span><span class="sxs-lookup"><span data-stu-id="5f221-156">Each example shows how you can view the dependencies of `iuPerson` trigger.</span></span>  
  
```  
USE AdventureWorks2012;   
GO  
SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
    o.type_desc AS referencing_desciption,   
    COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
    referencing_class_desc, referenced_class_desc,   
    referenced_server_name, referenced_database_name, referenced_schema_name,   
    referenced_entity_name,   
    COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,   
    is_caller_dependent, is_ambiguous  
FROM sys.sql_expression_dependencies AS sed  
INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
WHERE referencing_id = OBJECT_ID(N'Person.iuPerson');   
GO  
  
```  
  
#### <a name="to-view-information-about-dml-triggers-in-the-database"></a><span data-ttu-id="5f221-157">若要檢視有關資料庫中 DML 觸發程序的資訊</span><span class="sxs-lookup"><span data-stu-id="5f221-157">To view information about DML triggers in the database</span></span>  
  
1.  <span data-ttu-id="5f221-158">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5f221-158">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5f221-159">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="5f221-159">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5f221-160">將下列其中一個範例複製並貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="5f221-160">Copy and paste one of the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="5f221-161">每個範例都會說明如何檢視資料庫中有關 DML 觸發程序 (`TR`) 的資訊。</span><span class="sxs-lookup"><span data-stu-id="5f221-161">Each example shows how you can view information about DML triggers (`TR`) in the database.</span></span>  
  
```  
USE AdventureWorks2012;   
GO  
SELECT  name, parent_id, create_date, modify_date, is_instead_of_trigger  
FROM sys.triggers  
WHERE type = 'TR';   
GO  
  
```  
  
```sql  
USE AdventureWorks2012;   
GO  
SELECT  name, object_id, schema_id, parent_object_id, type_desc, create_date, modify_date, is_published  
FROM sys.objects  
WHERE type = 'TR';   
GO  
  
```  
  
```sql  
USE AdventureWorks2012;   
GO  
SELECT OBJECTPROPERTY(OBJECT_ID(N'Person.iuPerson'), 'ExecIsInsteadOfTrigger');   
GO  
  
```  
  
#### <a name="to-view-information-about-events-that-fire-a-dml-trigger"></a><span data-ttu-id="5f221-162">若要檢視有關引發 DML 觸發程序之事件的資訊</span><span class="sxs-lookup"><span data-stu-id="5f221-162">To view information about events that fire a DML trigger</span></span>  
  
1.  <span data-ttu-id="5f221-163">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5f221-163">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5f221-164">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="5f221-164">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5f221-165">將下列其中一個範例複製並貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="5f221-165">Copy and paste one of the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="5f221-166">每個範例都會說明如何檢視引發 `iuPerson` 觸發程序的事件。</span><span class="sxs-lookup"><span data-stu-id="5f221-166">Each example shows how you can view the events that fire the `iuPerson` trigger.</span></span>  
  
```sql  
USE AdventureWorks2012;   
GO  
SELECT object_id, type, type_desc, is_trigger_event, event_group_type, event_group_type_desc   
FROM sys.events  
WHERE object_id = OBJECT_ID('Person.iuPerson');   
GO  
```  
  
```sql  
USE AdventureWorks2012;   
GO   
SELECT object_id, type,is_first, is_last  
FROM sys.trigger_events  
WHERE object_id = OBJECT_ID('Person.iuPerson');   
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f221-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f221-167">See Also</span></span>  
 <span data-ttu-id="5f221-168">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-168">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="5f221-169">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-169">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span></span>  
 <span data-ttu-id="5f221-170">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-170">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="5f221-171">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-171">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="5f221-172">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-172">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span></span>  
 <span data-ttu-id="5f221-173">[sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-173">[sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) </span></span>  
 <span data-ttu-id="5f221-174">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-174">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span></span>  
 <span data-ttu-id="5f221-175">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-175">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span></span>  
 <span data-ttu-id="5f221-176">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-176">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span></span>  
 <span data-ttu-id="5f221-177">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-177">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span></span>  
 <span data-ttu-id="5f221-178">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-178">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="5f221-179">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-179">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="5f221-180">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-180">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span></span>  
 <span data-ttu-id="5f221-181">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-181">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span></span>  
 <span data-ttu-id="5f221-182">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-182">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="5f221-183">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-183">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="5f221-184">[sys.server_assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-184">[sys.server_assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql) </span></span>  
 <span data-ttu-id="5f221-185">[OBJECTPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectpropertyex-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f221-185">[OBJECTPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectpropertyex-transact-sql) </span></span>  
 [<span data-ttu-id="5f221-186">OBJECT_DEFINITION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5f221-186">OBJECT_DEFINITION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/object-definition-transact-sql)  
  
  
