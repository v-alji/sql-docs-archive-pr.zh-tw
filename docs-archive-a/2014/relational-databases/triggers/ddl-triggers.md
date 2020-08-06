---
title: DDL 觸發程序 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DDL triggers, about DDL triggers
ms.assetid: 1a4a6564-9820-4a14-9305-2c0e9ea37454
author: rothja
ms.author: jroth
ms.openlocfilehash: 6cbcc9f1efc477b8c54ad131f9efa9ff49cc5845
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606135"
---
# <a name="ddl-triggers"></a><span data-ttu-id="2e925-102">DDL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="2e925-102">DDL Triggers</span></span>
  <span data-ttu-id="2e925-103">DDL 觸發程序則是為了回應各種資料定義語言 (DDL) 事件而引發的。</span><span class="sxs-lookup"><span data-stu-id="2e925-103">DDL triggers fire in response to a variety of Data Definition Language (DDL) events.</span></span> <span data-ttu-id="2e925-104">這些事件主要對應至以 CREATE、ALTER、DROP、GRANT、DENY、REVOKE 或 UPDATE STATISTICS 關鍵字開頭的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2e925-104">These events primarily correspond to [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that start with the keywords CREATE, ALTER, DROP, GRANT, DENY, REVOKE or UPDATE STATISTICS.</span></span> <span data-ttu-id="2e925-105">執行類似 DDL 作業的某些系統預存程序也可能引發 DDL 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="2e925-105">Certain system stored procedures that perform DDL-like operations can also fire DDL triggers.</span></span>  
  
 <span data-ttu-id="2e925-106">當您要執行下列作業時，可使用 DDL 觸發程序：</span><span class="sxs-lookup"><span data-stu-id="2e925-106">Use DDL triggers when you want to do the following:</span></span>  
  
-   <span data-ttu-id="2e925-107">防止對資料庫結構描述進行特定變更。</span><span class="sxs-lookup"><span data-stu-id="2e925-107">Prevent certain changes to your database schema.</span></span>  
  
-   <span data-ttu-id="2e925-108">在資料庫中發生特定動作以回應資料庫結構描述的變更。</span><span class="sxs-lookup"><span data-stu-id="2e925-108">Have something occur in the database in response to a change in your database schema.</span></span>  
  
-   <span data-ttu-id="2e925-109">記錄資料庫結構描述的變更或事件。</span><span class="sxs-lookup"><span data-stu-id="2e925-109">Record changes or events in the database schema.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2e925-110">請測試 DDL 觸發程序，以判斷它們對執行之系統預存程序的回應。</span><span class="sxs-lookup"><span data-stu-id="2e925-110">Test your DDL triggers to determine their responses to system stored procedures that are run.</span></span> <span data-ttu-id="2e925-111">例如，CREATE TYPE 陳述式與 **sp_addtype** 預存程序，都會引發在 CREATE_TYPE 事件上建立的 DDL 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="2e925-111">For example, the CREATE TYPE statement and the **sp_addtype** stored procedure will both fire a DDL trigger that is created on a CREATE_TYPE event.</span></span>  
  
## <a name="types-of-ddl-triggers"></a><span data-ttu-id="2e925-112">DDL 觸發程序的類型</span><span class="sxs-lookup"><span data-stu-id="2e925-112">Types of DDL Triggers</span></span>  
 <span data-ttu-id="2e925-113">Transact-SQL DDL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="2e925-113">Transact-SQL DDL Trigger</span></span>  
 <span data-ttu-id="2e925-114">特殊類型的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序，可執行一或多個 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式以回應伺服器範圍或資料庫範圍事件。</span><span class="sxs-lookup"><span data-stu-id="2e925-114">A special type of [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure that executes one or more [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in response to a server-scoped or database-scoped event.</span></span> <span data-ttu-id="2e925-115">例如，如果執行陳述式 (例如 ALTER SERVER CONFIGURATION) 或使用 DROP TABLE 刪除資料表，則可能會引發 DDL 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="2e925-115">For example, a DDL Trigger may fire if a statement such as ALTER SERVER CONFIGURATION is executed or if a table is deleted by using DROP TABLE.</span></span>  
  
 <span data-ttu-id="2e925-116">CLR DDL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="2e925-116">CLR DDL Trigger</span></span>  
 <span data-ttu-id="2e925-117">CLR 觸發程序不執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序，而是執行以 Managed 程式碼撰寫的一個或多個方法，這些方法是在 .NET Framework 中建立並在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中上傳的組件成員。</span><span class="sxs-lookup"><span data-stu-id="2e925-117">Instead of executing a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, a CLR trigger executes one or more methods written in managed code that are members of an assembly created in the .NET Framework and uploaded in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2e925-118">在執行會觸發 DDL 觸發程序的 DDL 陳述式之後，才會引發 DDL 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="2e925-118">DDL triggers fire only after the DDL statements that trigger them are run.</span></span> <span data-ttu-id="2e925-119">DDL 觸發程序不能使用為 INSTEAD OF 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="2e925-119">DDL triggers cannot be used as INSTEAD OF triggers.</span></span> <span data-ttu-id="2e925-120">對於影響區域或全域暫存資料表與預存程序的事件，DDL 觸發程序不會為了回應它而引發。</span><span class="sxs-lookup"><span data-stu-id="2e925-120">DDL triggers do not fire in response to events that affect local or global temporary tables and stored procedures.</span></span>  
  
 <span data-ttu-id="2e925-121">DDL 觸發程序不會建立特殊 `inserted` 和 `deleted` 資料表。</span><span class="sxs-lookup"><span data-stu-id="2e925-121">DDL triggers do not create the special `inserted` and `deleted` tables.</span></span>  
  
 <span data-ttu-id="2e925-122">使用 EVENTDATA 函數將可擷取引發 DLL 觸發程序的事件資訊，以及觸發程序所造成的後續變更之資訊。</span><span class="sxs-lookup"><span data-stu-id="2e925-122">The information about an event that fires a DDL trigger, and the subsequent changes caused by the trigger, is captured by using the EVENTDATA function.</span></span>  
  
 <span data-ttu-id="2e925-123">要針對每個 DDL 事件建立的多個觸發程序。</span><span class="sxs-lookup"><span data-stu-id="2e925-123">Multiple triggers to be created for each DDL event.</span></span>  
  
 <span data-ttu-id="2e925-124">DDL 觸發程序不像 DML 觸發程序，並不以結構描述為範圍。</span><span class="sxs-lookup"><span data-stu-id="2e925-124">Unlike DML triggers, DDL triggers are not scoped to schemas.</span></span> <span data-ttu-id="2e925-125">因此，OBJECT_ID、OBJECT_NAME、OBJECTPROPERTY 和 OBJECTPROPERTYEX 等函數無法用來查詢有關 DDL 觸發程序的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2e925-125">Therefore, functions such as OBJECT_ID, OBJECT_NAME, OBJECTPROPERTY, and OBJECTPROPERTYEX cannot be used for querying metadata about DDL triggers.</span></span> <span data-ttu-id="2e925-126">請改用目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="2e925-126">Use the catalog views instead.</span></span>  
  
 <span data-ttu-id="2e925-127">伺服器範圍的 DDL 觸發程序會出現在 SQL Server Management Studio 物件總管的 [觸發程序]  資料夾中。</span><span class="sxs-lookup"><span data-stu-id="2e925-127">Server-scoped DDL triggers appear in the SQL Server Management Studio Object Explorer in the **Triggers** folder.</span></span> <span data-ttu-id="2e925-128">這個資料夾在 **[伺服器物件]** 資料夾之下。</span><span class="sxs-lookup"><span data-stu-id="2e925-128">This folder is located under the **Server Objects** folder.</span></span> <span data-ttu-id="2e925-129">資料庫範圍的 DDL 觸發程序則是出現在 [資料庫觸發程序]  資料夾。</span><span class="sxs-lookup"><span data-stu-id="2e925-129">Database-scoped DDL triggers appear in the **Database Triggers** folder.</span></span> <span data-ttu-id="2e925-130">這個資料夾在對應資料庫的 **[可程式性]** 資料夾之下。</span><span class="sxs-lookup"><span data-stu-id="2e925-130">This folder is located under the **Programmability** folder of the corresponding database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2e925-131">觸發程序內的惡意程式碼可能在擴大的權限下執行。</span><span class="sxs-lookup"><span data-stu-id="2e925-131">Malicious code inside triggers can run under escalated privileges.</span></span> <span data-ttu-id="2e925-132">如需如何協助降低此威脅的詳細資訊，請參閱 [管理觸發程序安全性](manage-trigger-security.md)。</span><span class="sxs-lookup"><span data-stu-id="2e925-132">For more information about how to help reduce this threat, see [Manage Trigger Security](manage-trigger-security.md).</span></span>  
  
## <a name="ddl-trigger-scope"></a><span data-ttu-id="2e925-133">DDL 觸發程序範圍</span><span class="sxs-lookup"><span data-stu-id="2e925-133">DDL Trigger Scope</span></span>  
 <span data-ttu-id="2e925-134">DDL 觸發程序可以引發以回應目前資料庫中 (或目前伺服器上) 處理的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 事件。</span><span class="sxs-lookup"><span data-stu-id="2e925-134">DDL triggers can fire in response to a [!INCLUDE[tsql](../../includes/tsql-md.md)] event processed in the current database, or on the current server.</span></span> <span data-ttu-id="2e925-135">觸發程序的範圍需視事件而定。</span><span class="sxs-lookup"><span data-stu-id="2e925-135">The scope of the trigger depends on the event.</span></span> <span data-ttu-id="2e925-136">例如，每當資料庫或伺服器執行個體上發生 CREATE_TABLE 事件時，為了回應 CREATE_TABLE 事件而建立來引發的 DDL 觸發程序可以進行此處理。</span><span class="sxs-lookup"><span data-stu-id="2e925-136">For example, a DDL trigger created to fire in response to a CREATE_TABLE event can do so whenever a CREATE_TABLE event occurs in the database, or on the server instance.</span></span> <span data-ttu-id="2e925-137">只有當伺服器執行個體上發生 CREATE_LOGIN 事件時，為了回應 CREATE_LOGIN 事件而建立來引發的 DDL 觸發程序才可以進行此處理。</span><span class="sxs-lookup"><span data-stu-id="2e925-137">A DDL trigger created to fire in response to a CREATE_LOGIN event can do so only when a CREATE_LOGIN event occurs in the server instance.</span></span>  
  
 <span data-ttu-id="2e925-138">在下列範例中，每當資料庫中發生 `safety` 或 `DROP_TABLE` 事件時，就會引發 DDL 觸發程序 `ALTER_TABLE` 。</span><span class="sxs-lookup"><span data-stu-id="2e925-138">In the following example, DDL trigger `safety` will fire whenever a `DROP_TABLE` or `ALTER_TABLE` event occurs in the database.</span></span>  
  
```  
CREATE TRIGGER safety   
ON DATABASE   
FOR DROP_TABLE, ALTER_TABLE   
AS   
   PRINT 'You must disable Trigger "safety" to drop or alter tables!'   
   ROLLBACK;  
```  
  
 <span data-ttu-id="2e925-139">在下列範例中，如果目前伺服器執行個體上發生了任何 `CREATE_DATABASE` 事件，DDL 觸發程序就會列印訊息。</span><span class="sxs-lookup"><span data-stu-id="2e925-139">In the following example, a DDL trigger prints a message if any `CREATE_DATABASE` event occurs on the current server instance.</span></span> <span data-ttu-id="2e925-140">這個範例使用 `EVENTDATA` 函數擷取對應 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的文字。</span><span class="sxs-lookup"><span data-stu-id="2e925-140">The example uses the `EVENTDATA` function to retrieve the text of the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="2e925-141">如需如何搭配 DDL 觸發程序使用 EVENTDATA 的詳細資訊，請參閱 [使用 EVENTDATA 函數](use-the-eventdata-function.md)。</span><span class="sxs-lookup"><span data-stu-id="2e925-141">For more information about how to use EVENTDATA with DDL triggers, see [Use the EVENTDATA Function](use-the-eventdata-function.md).</span></span>  
  
```  
IF EXISTS (SELECT * FROM sys.server_triggers  
    WHERE name = 'ddl_trig_database')  
DROP TRIGGER ddl_trig_database  
ON ALL SERVER;  
GO  
CREATE TRIGGER ddl_trig_database   
ON ALL SERVER   
FOR CREATE_DATABASE   
AS   
    PRINT 'Database Created.'  
    SELECT EVENTDATA().value('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]','nvarchar(max)')  
GO  
DROP TRIGGER ddl_trig_database  
ON ALL SERVER;  
GO  
  
```  
  
 <span data-ttu-id="2e925-142">您可以在本主題後面「選取特定的 DDL 陳述式以引發 DDL 觸發程序」一節所提供的連結中，找到 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式與其可指定之範圍的對應清單。</span><span class="sxs-lookup"><span data-stu-id="2e925-142">The lists that map the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to the scopes that can be specified for them are available through the links provided in the section "Selecting a Particular DDL Statement to Fire a DDL Trigger," later in this topic.</span></span>  
  
 <span data-ttu-id="2e925-143">以資料庫限定範圍的 DDL 觸發程序是以物件形式儲存在它們所建立的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="2e925-143">Database-scoped DDL triggers are stored as objects in the database in which they are created.</span></span> <span data-ttu-id="2e925-144">DDL 觸發程序可以在 **master** 資料庫中建立，其運作方式與使用者指定的資料庫中所建立者相似。</span><span class="sxs-lookup"><span data-stu-id="2e925-144">DDL triggers can be created in the **master** database and behave just like those created in user-designed databases.</span></span> <span data-ttu-id="2e925-145">您可以查詢 **sys.triggers** 目錄檢視，以取得有關 DDL 觸發程序的資訊。</span><span class="sxs-lookup"><span data-stu-id="2e925-145">You can obtain information about DDL triggers by querying the **sys.triggers** catalog view.</span></span> <span data-ttu-id="2e925-146">您可以在觸發程序建立所在的資料庫環境中查詢 **sys.triggers** ，或是藉由將資料庫名稱指定為識別碼，例如 **master.sys.triggers**。</span><span class="sxs-lookup"><span data-stu-id="2e925-146">You can query **sys.triggers** within the database context in which the triggers are created or by specifying the database name as an identifier, such as **master.sys.triggers**.</span></span>  
  
 <span data-ttu-id="2e925-147">伺服器範圍的 DDL 觸發程序是以物件的形式儲存在 **master** 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="2e925-147">Server-scoped DDL triggers are stored as objects in the **master** database.</span></span> <span data-ttu-id="2e925-148">然而，您可以藉由查詢任何資料庫環境中的 **sys.server_triggers** 目錄檢視，以取得有關伺服器範圍之 DDL 觸發程序的資訊。</span><span class="sxs-lookup"><span data-stu-id="2e925-148">However, you can obtain information about server-scoped DDL triggers by querying the **sys.server_triggers** catalog view in any database context.</span></span>  
  
## <a name="specifying-a-transact-sql-statement-or-group-of-statements"></a><span data-ttu-id="2e925-149">指定 Transact-SQL 陳述式或陳述式群組</span><span class="sxs-lookup"><span data-stu-id="2e925-149">Specifying a Transact-SQL Statement or Group of Statements</span></span>  
  
### <a name="selecting-a-particular-ddl-statement-to-fire-a-ddl-trigger"></a><span data-ttu-id="2e925-150">選取特定的 DDL 陳述式以引發 DDL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="2e925-150">Selecting a Particular DDL Statement to Fire a DDL Trigger</span></span>  
 <span data-ttu-id="2e925-151">DDL 觸發程序可以設計成在執行一個或多個特定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式之後才引發。</span><span class="sxs-lookup"><span data-stu-id="2e925-151">DDL triggers can be designed to fire after one or more particular [!INCLUDE[tsql](../../includes/tsql-md.md)] statements are run.</span></span> <span data-ttu-id="2e925-152">在前面的範例中，觸發程序 `safety` 會在任何 `DROP_TABLE` 或 `ALTER_TABLE` 事件之後引發。</span><span class="sxs-lookup"><span data-stu-id="2e925-152">In the previous example, trigger `safety` fires after any `DROP_TABLE` or `ALTER_TABLE` event.</span></span> <span data-ttu-id="2e925-153">如需可指定來引發 DDL 觸發程序的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式清單以及此觸發程序可以引發的範圍，請參閱 [DDL 事件](ddl-events.md)。</span><span class="sxs-lookup"><span data-stu-id="2e925-153">For lists of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that can be specified to fire a DDL trigger, and the scope at which the trigger can fire, see [DDL Events](ddl-events.md).</span></span>  
  
### <a name="selecting-a-predefined-group-of-ddl-statements-to-fire-a-ddl-trigger"></a><span data-ttu-id="2e925-154">選取預先定義的 DDL 陳述式群組以引發 DDL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="2e925-154">Selecting a Predefined Group of DDL Statements to Fire a DDL Trigger</span></span>  
 <span data-ttu-id="2e925-155">DDL 觸發程序可以在執行任何屬於預先定義之相似事件群組的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 事件之後引發。</span><span class="sxs-lookup"><span data-stu-id="2e925-155">A DDL trigger can fire after execution of any [!INCLUDE[tsql](../../includes/tsql-md.md)] event that belongs to a predefined grouping of similar events.</span></span> <span data-ttu-id="2e925-156">例如，如果您想要在執行 CREATE TABLE、ALTER TABLE 或 DROP TABLE 陳述式後引發 DDL 觸發程序，可以在 CREATE TRIGGER 陳述式中指定 FOR DDL_TABLE_EVENTS。</span><span class="sxs-lookup"><span data-stu-id="2e925-156">For example, if you want a DDL trigger to fire after any CREATE TABLE, ALTER TABLE, or DROP TABLE statement is run, you can specify FOR DDL_TABLE_EVENTS in the CREATE TRIGGER statement.</span></span> <span data-ttu-id="2e925-157">在執行 CREATE TRIGGER 後，事件群組所涵蓋的事件將加入 **sys.trigger_events** 目錄檢視中。</span><span class="sxs-lookup"><span data-stu-id="2e925-157">After CREATE TRIGGER is run, the events that are covered by an event group are added to the **sys.trigger_events** catalog view.</span></span>  
  
 <span data-ttu-id="2e925-158">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]中，如果在事件群組上建立觸發程序，則 **sys.trigger_events** 不會包含有關此事件群組的資訊，而 **sys.trigger_events** 則只會包含有關該群組涵蓋之個別事件的資訊。</span><span class="sxs-lookup"><span data-stu-id="2e925-158">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], if a trigger is created on an event group, **sys.trigger_events** does not include information about the event group, **sys.trigger_events** includes information only about the individual events covered by that group.</span></span> <span data-ttu-id="2e925-159">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 和更新版本中， **sys.trigger_events** 會保存有關觸發程序建立所在之事件群組的中繼資料，也會保存有關此事件群組涵蓋之個別事件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2e925-159">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and higher, **sys.trigger_events** persists metadata about the event group on which the triggers is created, and also about the individual events that the event group covers.</span></span> <span data-ttu-id="2e925-160">因此，對 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 和更新版本中事件群組所涵蓋之事件的變更，不會套用到 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]中的這些事件群組上所建立的 DDL 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="2e925-160">Therefore, changes to the events that are covered by event groups in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and higher do not apply to DDL triggers that are created on those event groups in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="2e925-161">如需可供 DDL 觸發程序使用之預先定義的 DDL 陳述式群組清單、事件群組所涵蓋的特定陳述式，以及可以為這些事件群組編寫程式的範圍，請參閱＜ [DDL Event Groups](ddl-event-groups.md)＞。</span><span class="sxs-lookup"><span data-stu-id="2e925-161">For a list of the predefined groups of DDL statements that are available for DDL triggers, the particular statements the event groups cover, and the scopes at which these event groups can be programmed, see [DDL Event Groups](ddl-event-groups.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="2e925-162">相關工作</span><span class="sxs-lookup"><span data-stu-id="2e925-162">Related Tasks</span></span>  
  
|<span data-ttu-id="2e925-163">Task</span><span class="sxs-lookup"><span data-stu-id="2e925-163">Task</span></span>|<span data-ttu-id="2e925-164">主題</span><span class="sxs-lookup"><span data-stu-id="2e925-164">Topic</span></span>|  
|----------|-----------|  
|<span data-ttu-id="2e925-165">描述如何建立、修改、刪除或停用 DDL 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="2e925-165">Describes how to create, modify, delete or disable DDL triggers.</span></span>|[<span data-ttu-id="2e925-166">實作 DDL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="2e925-166">Implement DDL Triggers</span></span>](implement-ddl-triggers.md)|  
|<span data-ttu-id="2e925-167">描述如何建立 CLR DDL 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="2e925-167">Describes how to create a CLR DDL trigger.</span></span>|[<span data-ttu-id="2e925-168">建立 CLR 觸發程序</span><span class="sxs-lookup"><span data-stu-id="2e925-168">Create CLR Triggers</span></span>](create-clr-triggers.md)|  
|<span data-ttu-id="2e925-169">描述如何傳回有關 DDL 觸發程序的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2e925-169">Describes how to return information about DDL triggers.</span></span>|[<span data-ttu-id="2e925-170">取得 DDL 觸發程序的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="2e925-170">Get Information About DDL Triggers</span></span>](get-information-about-ddl-triggers.md)|  
|<span data-ttu-id="2e925-171">描述如何傳回有關使用 EVENTDATA 函數引發 DDL 觸發程序之事件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2e925-171">Describes how to return information about an event that fires a DDL trigger by using the EVENTDATA function.</span></span>|[<span data-ttu-id="2e925-172">使用 EVENTDATA 函數</span><span class="sxs-lookup"><span data-stu-id="2e925-172">Use the EVENTDATA Function</span></span>](use-the-eventdata-function.md)|  
|<span data-ttu-id="2e925-173">描述如何管理觸發程序安全性。</span><span class="sxs-lookup"><span data-stu-id="2e925-173">Describes how to manage trigger security.</span></span>|[<span data-ttu-id="2e925-174">管理觸發程序安全性</span><span class="sxs-lookup"><span data-stu-id="2e925-174">Manage Trigger Security</span></span>](manage-trigger-security.md)|  
  
## <a name="see-also"></a><span data-ttu-id="2e925-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e925-175">See Also</span></span>  
 <span data-ttu-id="2e925-176">[DML 觸發程序](dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="2e925-176">[DML Triggers](dml-triggers.md) </span></span>  
 <span data-ttu-id="2e925-177">[登入觸發程序](logon-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="2e925-177">[Logon Triggers](logon-triggers.md) </span></span>  
 [<span data-ttu-id="2e925-178">CREATE TRIGGER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2e925-178">CREATE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-trigger-transact-sql)  
  
  
