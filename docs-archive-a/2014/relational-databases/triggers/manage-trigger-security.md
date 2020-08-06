---
title: 管理觸發程序安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], security
ms.assetid: e94720a8-a3a2-4364-b0a3-bbe86e3ce4d5
author: rothja
ms.author: jroth
ms.openlocfilehash: fdc176dcad50c3bf28f058c3724a01267975bfc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606120"
---
# <a name="manage-trigger-security"></a><span data-ttu-id="e8217-102">管理觸發程序安全性</span><span class="sxs-lookup"><span data-stu-id="e8217-102">Manage Trigger Security</span></span>
  <span data-ttu-id="e8217-103">依預設，DML 與 DDL 觸發程序會在呼叫觸發程序的該使用者之環境下執行。</span><span class="sxs-lookup"><span data-stu-id="e8217-103">By default, both DML and DDL triggers execute under the context of the user that calls the trigger.</span></span> <span data-ttu-id="e8217-104">觸發程序的呼叫者是執行陳述式而引發觸發程序執行的使用者。</span><span class="sxs-lookup"><span data-stu-id="e8217-104">The caller of a trigger is the user that executes the statement that causes the trigger to run.</span></span> <span data-ttu-id="e8217-105">例如，如果使用者 **Mary** 執行 DELETE 陳述式而引發 DML 觸發程序 **DML_trigMary** 執行，就會在 **Mary** 使用者權限的環境下執行 **DML_trigMary**內的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e8217-105">For example, if user **Mary** executes a DELETE statement that causes DML trigger **DML_trigMary** to run, the code inside **DML_trigMary** executes in the context of the user privileges for **Mary**.</span></span> <span data-ttu-id="e8217-106">此預設行為有可能遭到居心不良的使用者加以利用，成為在資料庫或伺服器執行個體中導入惡意程式碼的漏洞。</span><span class="sxs-lookup"><span data-stu-id="e8217-106">This default behavior can be exploited by users who want to introduce malicious code in the database or server instance.</span></span> <span data-ttu-id="e8217-107">例如，下列 DDL 觸發程序是由使用者 `JohnDoe`建立的：</span><span class="sxs-lookup"><span data-stu-id="e8217-107">For example, the following DDL trigger is created by user `JohnDoe`:</span></span>  
  
 `CREATE TRIGGER DDL_trigJohnDoe`  
  
 `ON DATABASE`  
  
 `FOR ALTER_TABLE`  
  
 `AS`  
  
 `GRANT CONTROL SERVER TO JohnDoe ;`  
  
 `GO`  
  
 <span data-ttu-id="e8217-108">這個觸發程序所代表的意義是，只要有權執行 `GRANT CONTROL SERVER` 陳述式的使用者 (例如 **sysadmin** 固定伺服器角色的成員) 執行 `ALTER TABLE` 陳述式，就會授與 `JohnDoe``CONTROL SERVER` 權限。</span><span class="sxs-lookup"><span data-stu-id="e8217-108">What this trigger means is that as soon as a user that has permission to execute a `GRANT CONTROL SERVER` statement, such as a member of the **sysadmin** fixed server role, executes an `ALTER TABLE` statement, `JohnDoe` is granted `CONTROL SERVER` permission.</span></span> <span data-ttu-id="e8217-109">換句話說，雖然 `JohnDoe` 無法授與 `CONTROL SERVER` 權限給自己，不過他可以啟用觸發程序程式碼，以便授與自己在提升權限的情況下執行的權限。</span><span class="sxs-lookup"><span data-stu-id="e8217-109">In other words, although `JohnDoe` cannot grant `CONTROL SERVER` permission to himself, he enabled the trigger code that grants him this permission to execute under escalated privileges.</span></span> <span data-ttu-id="e8217-110">DML 與 DDL 觸發程序都曝露於此種安全性威脅下。</span><span class="sxs-lookup"><span data-stu-id="e8217-110">Both DML and DDL triggers are open to this kind of security threat.</span></span>  
  
## <a name="trigger-security-best-practices"></a><span data-ttu-id="e8217-111">觸發程序安全性最佳作法</span><span class="sxs-lookup"><span data-stu-id="e8217-111">Trigger Security Best Practices</span></span>  
 <span data-ttu-id="e8217-112">您可以採用下列措施來防止觸發程序的程式碼在提升權限的情況下執行：</span><span class="sxs-lookup"><span data-stu-id="e8217-112">You can take the following measures to prevent trigger code from executing under escalated privileges:</span></span>  
  
-   <span data-ttu-id="e8217-113">請透過查詢 [sys.triggers](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) 與 [sys.server_triggers](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) 目錄檢視來了解資料庫與伺服器執行個體上所存在的 DML 與 DDL 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="e8217-113">Be aware of the DML and DDL triggers that exist in the database and on the server instance by querying the [sys.triggers](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) and [sys.server_triggers](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) catalog views.</span></span> <span data-ttu-id="e8217-114">下列查詢會傳回目前資料庫中所有的 DML 與資料庫層級的 DDL 觸發程序，以及在伺服器執行個體上的所有伺服器層級的 DDL 觸發程序：</span><span class="sxs-lookup"><span data-stu-id="e8217-114">The following query returns all DML and database-level DDL triggers in the current database, and all server-level DDL triggers on the server instance:</span></span>  
  
    ```  
    SELECT type, name, parent_class_desc FROM sys.triggers  
    UNION  
    SELECT type, name, parent_class_desc FROM sys.server_triggers ;  
    ```  
  
-   <span data-ttu-id="e8217-115">如果觸發程序是在提升權限的情況下執行，使用 [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) 停用觸發程序有可能會傷害資料庫或伺服器的完整性。</span><span class="sxs-lookup"><span data-stu-id="e8217-115">Use [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) to disable triggers that can harm the integrity of the database or server if the triggers execute under escalated privileges.</span></span> <span data-ttu-id="e8217-116">下列陳述式會停用目前資料庫中所有資料庫層級的 DDL 觸發程序：</span><span class="sxs-lookup"><span data-stu-id="e8217-116">The following statement disables all database-level DDL triggers in the current database:</span></span>  
  
    ```  
    DISABLE TRIGGER ALL ON DATABASE  
    ```  
  
     <span data-ttu-id="e8217-117">下列陳述式會停用在伺服器執行個體上所有伺服器層級的 DDL 觸發程序：</span><span class="sxs-lookup"><span data-stu-id="e8217-117">This statement disables all server-level DDL triggers on the server instance:</span></span>  
  
    ```  
    DISABLE TRIGGER ALL ON ALL SERVER  
    ```  
  
     <span data-ttu-id="e8217-118">此陳述式停用了目前資料庫中所有的 DML 觸發程序：</span><span class="sxs-lookup"><span data-stu-id="e8217-118">This statement disables all DML triggers in the current database:</span></span>  
  
    ```  
    DECLARE @schema_name sysname, @trigger_name sysname, @object_name sysname ;  
    DECLARE @sql nvarchar(max) ;  
    DECLARE trig_cur CURSOR FORWARD_ONLY READ_ONLY FOR  
        SELECT SCHEMA_NAME(schema_id) AS schema_name,  
            name AS trigger_name,  
            OBJECT_NAME(parent_object_id) as object_name  
        FROM sys.objects WHERE type in ('TR', 'TA') ;  
  
    OPEN trig_cur ;  
    FETCH NEXT FROM trig_cur INTO @schema_name, @trigger_name, @object_name ;  
  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
        SELECT @sql = 'DISABLE TRIGGER ' + QUOTENAME(@schema_name) + '.'  
            + QUOTENAME(@trigger_name) +  
            ' ON ' + QUOTENAME(@schema_name) + '.'   
            + QUOTENAME(@object_name) + ' ; ' ;  
        EXEC (@sql) ;  
        FETCH NEXT FROM trig_cur INTO @schema_name, @trigger_name, @object_name ;  
    END  
    GO  
  
    -- Verify triggers are disabled. Should return an empty result set.  
    SELECT * FROM sys.triggers WHERE is_disabled = 0 ;  
    GO  
  
    CLOSE trig_cur ;  
    DEALLOCATE trig_cur;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e8217-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8217-119">See Also</span></span>  
 <span data-ttu-id="e8217-120">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8217-120">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="e8217-121">[DML 觸發程序](../triggers/dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="e8217-121">[DML Triggers](../triggers/dml-triggers.md) </span></span>  
 [<span data-ttu-id="e8217-122">DDL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="e8217-122">DDL Triggers</span></span>](../triggers/ddl-triggers.md)  
  
  
