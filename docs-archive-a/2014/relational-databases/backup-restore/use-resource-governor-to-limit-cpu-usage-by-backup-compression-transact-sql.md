---
title: 使用資源管理員進行備份壓縮，以限制 CPU 使用率 (Transact-SQL) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup compression [SQL Server], Resource Governor
- backup compression [SQL Server], CPU usage
- compression [SQL Server], backup compression
- backups [SQL Server], compression
- Resource Governor, backup compression
ms.assetid: 01796551-578d-4425-9b9e-d87210f7ba72
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19a95cfa5c6780fbdf71ae58bd141aa9aa351efa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709673"
---
# <a name="use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql"></a><span data-ttu-id="3b669-102">使用資源管理員進行備份壓縮，以限制 CPU 使用率 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3b669-102">Use Resource Governor to Limit CPU Usage by Backup Compression (Transact-SQL)</span></span>
  <span data-ttu-id="3b669-103">根據預設，使用壓縮來備份會大幅增加 CPU 使用量，而且壓縮程序所耗用的額外 CPU 可能會對並行作業造成不良的影響。</span><span class="sxs-lookup"><span data-stu-id="3b669-103">By default, backing up using compression significantly increases CPU usage, and the additional CPU consumed by the compression process can adversely impact concurrent operations.</span></span> <span data-ttu-id="3b669-104">因此，如果發生 CPU 爭用的情況，您可能會想要在[資源管理員](../resource-governor/resource-governor.md) 限制 CPU 使用量的工作階段中，建立低優先權的壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="3b669-104">Therefore, you might want to create a low-priority compressed backup in a session whose CPU usage is limited by[Resource Governor](../resource-governor/resource-governor.md) when CPU contention occurs.</span></span> <span data-ttu-id="3b669-105">這個主題所展示的狀況會將特定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者的工作階段對應至在這類情況中限制 CPU 使用量的資源管理員工作負載群組，藉以分類這些工作階段。</span><span class="sxs-lookup"><span data-stu-id="3b669-105">This topic presents a scenario that classifies the sessions of a particular [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user by mapping them to a Resource Governor workload group that limits CPU usage in such cases.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3b669-106">在給定的資源管理員狀況中，工作階段分類可能會以使用者名稱、應用程式名稱，或可區分連接的其他任何項目為基礎。</span><span class="sxs-lookup"><span data-stu-id="3b669-106">In a given Resource Governor scenario, session classification might be based on a user name, an application name, or anything else that can differentiate a connection.</span></span> <span data-ttu-id="3b669-107">如需相關資訊，請參閱 [Resource Governor Classifier Function](../resource-governor/resource-governor-classifier-function.md) 以及 [Resource Governor Workload Group](../resource-governor/resource-governor-workload-group.md)。</span><span class="sxs-lookup"><span data-stu-id="3b669-107">For more information, see [Resource Governor Classifier Function](../resource-governor/resource-governor-classifier-function.md) and [Resource Governor Workload Group](../resource-governor/resource-governor-workload-group.md).</span></span>  
  
##  <a name="this-topic-contains-the-following-set-of-scenarios-which-are-presented-in-sequence"></a><a name="Top"></a> <span data-ttu-id="3b669-108">這個主題包含下列狀況集，並依序展示：</span><span class="sxs-lookup"><span data-stu-id="3b669-108">This topic contains the following set of scenarios, which are presented in sequence:</span></span>  
  
1.  [<span data-ttu-id="3b669-109">針對低優先權作業設定登入和使用者</span><span class="sxs-lookup"><span data-stu-id="3b669-109">Setting Up a Login and User for Low-Priority Operations</span></span>](#setup_login_and_user)  
  
2.  [<span data-ttu-id="3b669-110">設定資源管理員來限制 CPU 使用量</span><span class="sxs-lookup"><span data-stu-id="3b669-110">Configuring Resource Governor to Limit CPU Usage</span></span>](#configure_RG)  
  
3.  [<span data-ttu-id="3b669-111">確認目前工作階段的分類 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3b669-111">Verifying the Classification of the Current Session (Transact-SQL)</span></span>](#verifying)  
  
4.  [<span data-ttu-id="3b669-112">使用含有限制 CPU 的工作階段來壓縮備份</span><span class="sxs-lookup"><span data-stu-id="3b669-112">Compressing Backups Using a Session with Limited CPU</span></span>](#creating_compressed_backup)  
  
##  <a name="setting-up-a-login-and-user-for-low-priority-operations"></a><a name="setup_login_and_user"></a> <span data-ttu-id="3b669-113">針對低優先權作業設定登入和使用者</span><span class="sxs-lookup"><span data-stu-id="3b669-113">Setting Up a Login and User for Low-Priority Operations</span></span>  
 <span data-ttu-id="3b669-114">這個主題中的狀況需要使用低優先權 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入和使用者。</span><span class="sxs-lookup"><span data-stu-id="3b669-114">The scenario in this topic requires a low-priority [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and user.</span></span> <span data-ttu-id="3b669-115">使用者名稱將用來分類在登入中執行的工作階段，並且將它們路由傳送至限制 CPU 使用量的資源管理員工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="3b669-115">The user name will be used to classify sessions running in the login and route them to a Resource Governor workload group that limits CPU usage.</span></span>  
  
 <span data-ttu-id="3b669-116">下列程序描述針對此目的設定登入和使用者的步驟，後面接著 [!INCLUDE[tsql](../../includes/tsql-md.md)] 範例：「範例 A：設定登入和使用者 (Transact-SQL)」。</span><span class="sxs-lookup"><span data-stu-id="3b669-116">The following procedure describes the steps for setting up a login and user for this purpose, followed by a [!INCLUDE[tsql](../../includes/tsql-md.md)] example, "Example A: Setting Up a Login and User (Transact-SQL)."</span></span>  
  
### <a name="to-set-up-a-login-and-database-user-for-classifying-sessions"></a><span data-ttu-id="3b669-117">設定登入和資料庫使用者以便分類工作階段</span><span class="sxs-lookup"><span data-stu-id="3b669-117">To set up a login and database user for classifying sessions</span></span>  
  
1.  <span data-ttu-id="3b669-118">針對建立低優先權壓縮備份，建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="3b669-118">Create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login for creating low-priority compressed backups.</span></span>  
  
     <span data-ttu-id="3b669-119">**若要建立登入**</span><span class="sxs-lookup"><span data-stu-id="3b669-119">**To create a login**</span></span>  
  
    -   [<span data-ttu-id="3b669-120">建立登入</span><span class="sxs-lookup"><span data-stu-id="3b669-120">Create a Login</span></span>](../security/authentication-access/create-a-login.md)  
  
    -   [<span data-ttu-id="3b669-121">CREATE LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3b669-121">CREATE LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-login-transact-sql)  
  
2.  <span data-ttu-id="3b669-122">(選擇性) 將 VIEW SERVER STATE 授與這個登入。</span><span class="sxs-lookup"><span data-stu-id="3b669-122">Optionally, grant VIEW SERVER STATE to this login.</span></span>  
  
    -   [<span data-ttu-id="3b669-123">GRANT 系統物件權限 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3b669-123">GRANT System Object Permissions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/grant-system-object-permissions-transact-sql)  
  
     <span data-ttu-id="3b669-124">如需詳細資訊，請參閱 [GRANT 資料庫主體權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3b669-124">For more information, see [GRANT Database Principal Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql).</span></span>  
  
3.  <span data-ttu-id="3b669-125">針對這個登入建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者。</span><span class="sxs-lookup"><span data-stu-id="3b669-125">Create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user for this login.</span></span>  
  
     <span data-ttu-id="3b669-126">**建立使用者**</span><span class="sxs-lookup"><span data-stu-id="3b669-126">**To create a user**</span></span>  
  
    -   [<span data-ttu-id="3b669-127">建立資料庫使用者</span><span class="sxs-lookup"><span data-stu-id="3b669-127">Create a Database User</span></span>](../security/authentication-access/create-a-database-user.md)  
  
    -   [<span data-ttu-id="3b669-128">CREATE USER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3b669-128">CREATE USER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-user-transact-sql)  
  
4.  <span data-ttu-id="3b669-129">若要讓這個登入和使用者的工作階段備份給定的資料庫，請將使用者加入至該資料庫的 db_backupoperator 資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="3b669-129">To enable sessions of this login and user to back up a given database, add the user to the db_backupoperator database role of that database.</span></span> <span data-ttu-id="3b669-130">請針對這位使用者將備份的每個資料庫執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="3b669-130">Do this for each database that this user will back up.</span></span> <span data-ttu-id="3b669-131">(選擇性) 將使用者加入至其他固定資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="3b669-131">Optionally, add the user to other fixed database roles.</span></span>  
  
     <span data-ttu-id="3b669-132">**將使用者加入至固定資料庫角色**</span><span class="sxs-lookup"><span data-stu-id="3b669-132">**To add a user to a fixed database role**</span></span>  
  
    -   [<span data-ttu-id="3b669-133">sp_addrolemember &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3b669-133">sp_addrolemember &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql)  
  
     <span data-ttu-id="3b669-134">如需詳細資訊，請參閱 [GRANT 資料庫主體權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3b669-134">For more information, see [GRANT Database Principal Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql).</span></span>  
  
### <a name="example-a-setting-up-a-login-and-user-transact-sql"></a><span data-ttu-id="3b669-135">範例 A：設定登入和使用者 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3b669-135">Example A: Setting Up a Login and User (Transact-SQL)</span></span>  
 <span data-ttu-id="3b669-136">只有當您選擇針對低優先權備份建立新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入和使用者時，下列範例才會相關。</span><span class="sxs-lookup"><span data-stu-id="3b669-136">The following example is relevant only if you choose to create a new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and user for low-priority backups.</span></span> <span data-ttu-id="3b669-137">或者，您也可以使用現有的登入和使用者 (如果適當項目存在的話)。</span><span class="sxs-lookup"><span data-stu-id="3b669-137">Alternatively, you can use an existing login and user, if an appropriate one exists.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3b669-138">下列範例會使用範例登入和使用者名稱 *domain_name*`\MAX_CPU`。</span><span class="sxs-lookup"><span data-stu-id="3b669-138">The following example uses a sample login and user name, *domain_name*`\MAX_CPU`.</span></span> <span data-ttu-id="3b669-139">請將這些名稱取代成您打算在建立低優先順序壓縮備份時使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入和使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="3b669-139">Replace these with the names of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and user that you plan to use when creating your low-priority compressed backups.</span></span>  
  
 <span data-ttu-id="3b669-140">這個範例會針對 *domain_name*`\MAX_CPU` Windows 帳戶建立登入，然後將 VIEW SERVER STATE 權限授與此登入。</span><span class="sxs-lookup"><span data-stu-id="3b669-140">This example creates a login for the *domain_name*`\MAX_CPU` Windows account and then grants VIEW SERVER STATE permission to the login.</span></span> <span data-ttu-id="3b669-141">這個權限可讓您確認登入工作階段的資源管理員分類。</span><span class="sxs-lookup"><span data-stu-id="3b669-141">This permission enables you to verify the Resource Governor classification of sessions of the login.</span></span> <span data-ttu-id="3b669-142">然後，此範例會針對 *domain_name*`\MAX_CPU` 建立使用者並將它加入至 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 範例資料庫的 db_backupoperator 固定資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="3b669-142">The example then creates a user for *domain_name*`\MAX_CPU` and adds it to the db_backupoperator fixed database role for the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="3b669-143">資源管理員分類函數將會使用這個使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="3b669-143">This user name will be used by the Resource Governor classifier function.</span></span>  
  
```sql  
-- Create a SQL Server login for low-priority operations  
USE master;  
CREATE LOGIN [domain_name\MAX_CPU] FROM WINDOWS;  
GRANT VIEW SERVER STATE TO [domain_name\MAX_CPU];  
GO  
-- Create a SQL Server user in AdventureWorks2012 for this login  
USE AdventureWorks2012;  
CREATE USER [domain_name\MAX_CPU] FOR LOGIN [domain_name\MAX_CPU];  
EXEC sp_addrolemember 'db_backupoperator', 'domain_name\MAX_CPU';  
GO  
  
```  
  
 <span data-ttu-id="3b669-144">[[頁首]](#Top)</span><span class="sxs-lookup"><span data-stu-id="3b669-144">[&#91;Top&#93;](#Top)</span></span>  
  
##  <a name="configuring-resource-governor-to-limit-cpu-usage"></a><a name="configure_RG"></a> <span data-ttu-id="3b669-145">設定資源管理員來限制 CPU 使用量</span><span class="sxs-lookup"><span data-stu-id="3b669-145">Configuring Resource Governor to Limit CPU Usage</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b669-146">請確定資源管理員已啟用。</span><span class="sxs-lookup"><span data-stu-id="3b669-146">Ensure that Resource Governor is enabled.</span></span> <span data-ttu-id="3b669-147">如需詳細資訊，請參閱 [啟用資源管理員](../resource-governor/enable-resource-governor.md)。</span><span class="sxs-lookup"><span data-stu-id="3b669-147">For more information, see [Enable Resource Governor](../resource-governor/enable-resource-governor.md).</span></span>  
  
 <span data-ttu-id="3b669-148">在這個資源管理員狀況中，組態設定包含下列基本步驟：</span><span class="sxs-lookup"><span data-stu-id="3b669-148">In this Resource Governor scenario, configuration comprises the following basic steps:</span></span>  
  
1.  <span data-ttu-id="3b669-149">建立和設定資源管理員資源集區，以便在發生 CPU 競爭時，限制提供給資源集區中要求的最大平均 CPU 頻寬。</span><span class="sxs-lookup"><span data-stu-id="3b669-149">Create and configure a Resource Governor resource pool that limits the maximum average CPU bandwidth that will be given to requests in the resource pool when CPU contention occurs.</span></span>  
  
2.  <span data-ttu-id="3b669-150">建立和設定使用這個集區的資源管理員工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="3b669-150">Create and configure a Resource Governor workload group that uses this pool.</span></span>  
  
3.  <span data-ttu-id="3b669-151">建立 *「分類函數」* (Classifier Function)，它是使用者定義的函數 (UDF)，而且資源管理員會使用其傳回值來分類工作階段，以便將它們路由傳送至適當的工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="3b669-151">Create a *classifier function*, which is a user-defined function (UDF) whose return values are used by Resource Governor for classifying sessions so that they are routed to the appropriate workload group.</span></span>  
  
4.  <span data-ttu-id="3b669-152">向資源管理員註冊此分類函數。</span><span class="sxs-lookup"><span data-stu-id="3b669-152">Register the classifier function with Resource Governor.</span></span>  
  
5.  <span data-ttu-id="3b669-153">將這些變更套用至資源管理員的記憶體中組態。</span><span class="sxs-lookup"><span data-stu-id="3b669-153">Apply the changes to the Resource Governor in-memory configuration.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b669-154">如需有關資源管理員資源集區、工作負載群組和分類的相關資訊，請參閱 [資源管理員](../resource-governor/resource-governor.md)。</span><span class="sxs-lookup"><span data-stu-id="3b669-154">For information about Resource Governor resource pools, workload groups, and classification, see [Resource Governor](../resource-governor/resource-governor.md).</span></span>  
  
 <span data-ttu-id="3b669-155">這些步驟的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式將在「設定資源管理員來限制 CPU 使用量」程序中說明，而且後面接著該程序的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="3b669-155">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statements for these steps are described in the procedure, "To configure Resource Governor for limiting CPU usage," which is followed by a [!INCLUDE[tsql](../../includes/tsql-md.md)] example of the procedure.</span></span>  
  
 <span data-ttu-id="3b669-156">**設定資源管理員 (SQL Server Management Studio)**</span><span class="sxs-lookup"><span data-stu-id="3b669-156">**To configure Resource Governor (SQL Server Management Studio)**</span></span>  
  
-   [<span data-ttu-id="3b669-157">使用範本設定資源管理員</span><span class="sxs-lookup"><span data-stu-id="3b669-157">Configure Resource Governor Using a Template</span></span>](../resource-governor/configure-resource-governor-using-a-template.md)  
  
-   [<span data-ttu-id="3b669-158">建立資源集區</span><span class="sxs-lookup"><span data-stu-id="3b669-158">Create a Resource Pool</span></span>](../resource-governor/create-a-resource-pool.md)  
  
-   [<span data-ttu-id="3b669-159">建立工作負載群組</span><span class="sxs-lookup"><span data-stu-id="3b669-159">Create a Workload Group</span></span>](../resource-governor/create-a-workload-group.md)  
  
### <a name="to-configure-resource-governor-for-limiting-cpu-usage-transact-sql"></a><span data-ttu-id="3b669-160">設定資源管理員來限制 CPU 使用量 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3b669-160">To configure Resource Governor for limiting CPU usage (Transact-SQL)</span></span>  
  
1.  <span data-ttu-id="3b669-161">發出 [CREATE RESOURCE POOL](/sql/t-sql/statements/create-resource-pool-transact-sql) 陳述式來建立資源集區。</span><span class="sxs-lookup"><span data-stu-id="3b669-161">Issue a [CREATE RESOURCE POOL](/sql/t-sql/statements/create-resource-pool-transact-sql) statement to create a resource pool.</span></span> <span data-ttu-id="3b669-162">這個程序的範例會使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="3b669-162">The example for this procedure uses the following syntax:</span></span>  
  
     <span data-ttu-id="3b669-163">*CREATE RESOURCE POOL pool_name* WITH ( MAX_CPU_PERCENT = *value* );</span><span class="sxs-lookup"><span data-stu-id="3b669-163">*CREATE RESOURCE POOL pool_name* WITH ( MAX_CPU_PERCENT = *value* );</span></span>  
  
     <span data-ttu-id="3b669-164">*Value* 是介於 1 和 100 之間的整數，表示最大平均 CPU 頻寬的百分比。</span><span class="sxs-lookup"><span data-stu-id="3b669-164">*Value* is an integer from 1 to 100 that indicates the percentage of maximum average CPU bandwidth.</span></span> <span data-ttu-id="3b669-165">適當的值會因您的環境而不同。</span><span class="sxs-lookup"><span data-stu-id="3b669-165">The appropriate value depends on your environment.</span></span> <span data-ttu-id="3b669-166">為了方便說明，這個主題中的範例會使用 20% percent (MAX_CPU_PERCENT = 20)。</span><span class="sxs-lookup"><span data-stu-id="3b669-166">For the purpose of illustration, the example in this topic uses 20%  percent (MAX_CPU_PERCENT = 20.)</span></span>  
  
2.  <span data-ttu-id="3b669-167">發出 [CREATE WORKLOAD GROUP](/sql/t-sql/statements/create-workload-group-transact-sql) 陳述式，針對您想要管理其 CPU 使用量的低優先權作業建立工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="3b669-167">Issue a [CREATE WORKLOAD GROUP](/sql/t-sql/statements/create-workload-group-transact-sql) statement to create a workload group for low-priority operations whose CPU usage you want to govern.</span></span> <span data-ttu-id="3b669-168">這個程序的範例會使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="3b669-168">The example for this procedure uses the following syntax:</span></span>  
  
     <span data-ttu-id="3b669-169">CREATE WORKLOAD GROUP *group_name* USING *pool_name*;</span><span class="sxs-lookup"><span data-stu-id="3b669-169">CREATE WORKLOAD GROUP *group_name* USING *pool_name*;</span></span>  
  
3.  <span data-ttu-id="3b669-170">發出 [CREATE FUNCTION](/sql/t-sql/statements/create-function-transact-sql) 陳述式來建立分類函數，以便將上述步驟中建立工作負載群組對應至低優先權登入的使用者。</span><span class="sxs-lookup"><span data-stu-id="3b669-170">Issue a [CREATE FUNCTION](/sql/t-sql/statements/create-function-transact-sql) statement to create a classifier function that maps the workload group created in the preceding step to the user of the low-priority login.</span></span> <span data-ttu-id="3b669-171">這個程序的範例會使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="3b669-171">The example for this procedure uses the following syntax:</span></span>  
  
     <span data-ttu-id="3b669-172">CREATE FUNCTION [*schema_name*.]*function_name*() RETURNS sysname</span><span class="sxs-lookup"><span data-stu-id="3b669-172">CREATE FUNCTION [*schema_name*.]*function_name*() RETURNS sysname</span></span>  
  
     <span data-ttu-id="3b669-173">WITH SCHEMABINDING</span><span class="sxs-lookup"><span data-stu-id="3b669-173">WITH SCHEMABINDING</span></span>  
  
     <span data-ttu-id="3b669-174">AS</span><span class="sxs-lookup"><span data-stu-id="3b669-174">AS</span></span>  
  
     <span data-ttu-id="3b669-175">BEGIN</span><span class="sxs-lookup"><span data-stu-id="3b669-175">BEGIN</span></span>  
  
     <span data-ttu-id="3b669-176">DECLARE @workload_group_name AS *sysname*</span><span class="sxs-lookup"><span data-stu-id="3b669-176">DECLARE @workload_group_name AS *sysname*</span></span>  
  
     <span data-ttu-id="3b669-177">IF (SUSER_NAME() = '*user_of_low_priority_login*')</span><span class="sxs-lookup"><span data-stu-id="3b669-177">IF (SUSER_NAME() = '*user_of_low_priority_login*')</span></span>  
  
     <span data-ttu-id="3b669-178">SET @workload_group_name = '*workload_group_name*'</span><span class="sxs-lookup"><span data-stu-id="3b669-178">SET @workload_group_name = '*workload_group_name*'</span></span>  
  
     <span data-ttu-id="3b669-179">RETURN @workload_group_name</span><span class="sxs-lookup"><span data-stu-id="3b669-179">RETURN @workload_group_name</span></span>  
  
     <span data-ttu-id="3b669-180">END</span><span class="sxs-lookup"><span data-stu-id="3b669-180">END</span></span>  
  
     <span data-ttu-id="3b669-181">如需有關這個 CREATE FUNCTION 陳述式之元件的詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="3b669-181">For information about the components of this CREATE FUNCTION statement, see:</span></span>  
  
    -   [<span data-ttu-id="3b669-182">DECLARE @local_variable &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3b669-182">DECLARE @local_variable &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/declare-local-variable-transact-sql)  
  
    -   [<span data-ttu-id="3b669-183">SUSER_SNAME &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3b669-183">SUSER_SNAME &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/suser-sname-transact-sql)  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="3b669-184">SUSER_NAME 只是可用於分類函數的其中一個系統函數。</span><span class="sxs-lookup"><span data-stu-id="3b669-184">SUSER_NAME is just one of several system functions that can be used in a classifier function.</span></span> <span data-ttu-id="3b669-185">如需詳細資訊，請參閱 [建立和測試分類使用者定義函數](../resource-governor/create-and-test-a-classifier-user-defined-function.md)。</span><span class="sxs-lookup"><span data-stu-id="3b669-185">For more information, see [Create and Test a Classifier User-Defined Function](../resource-governor/create-and-test-a-classifier-user-defined-function.md).</span></span>  
  
    -   <span data-ttu-id="3b669-186">[SET @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-local-variable-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3b669-186">[SET @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-local-variable-transact-sql).</span></span>  
  
4.  <span data-ttu-id="3b669-187">發出 [ALTER RESOURCE GOVERNOR](/sql/t-sql/statements/alter-resource-governor-transact-sql) 陳述式，向資源管理員註冊此分類函數。</span><span class="sxs-lookup"><span data-stu-id="3b669-187">Issue an [ALTER RESOURCE GOVERNOR](/sql/t-sql/statements/alter-resource-governor-transact-sql) statement to register the classifier function with Resource Governor.</span></span> <span data-ttu-id="3b669-188">這個程序的範例會使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="3b669-188">The example for this procedure uses the following syntax:</span></span>  
  
     <span data-ttu-id="3b669-189">ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION = *schema_name*.*function_name*);</span><span class="sxs-lookup"><span data-stu-id="3b669-189">ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION = *schema_name*.*function_name*);</span></span>  
  
5.  <span data-ttu-id="3b669-190">發出第二個 ALTER RESOURCE GOVERNOR 陳述式，將這些變更套用至資源管理員的記憶體中組態，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3b669-190">Issue a second ALTER RESOURCE GOVERNOR statement to apply the changes to the Resource Governor in-memory configuration, as follows:</span></span>  
  
    ```  
    ALTER RESOURCE GOVERNOR RECONFIGURE;  
    ```  
  
### <a name="example-b-configuring-resource-governor-transact-sql"></a><span data-ttu-id="3b669-191">範例 B：設定 Resource Governor (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3b669-191">Example B: Configuring Resource Governor (Transact-SQL)</span></span>  
 <span data-ttu-id="3b669-192">下列範例會在單一交易中執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="3b669-192">The following example performs the following steps within a single transaction:</span></span>  
  
1.  <span data-ttu-id="3b669-193">建立 `pMAX_CPU_PERCENT_20` 資源集區。</span><span class="sxs-lookup"><span data-stu-id="3b669-193">Creates the `pMAX_CPU_PERCENT_20` resource pool.</span></span>  
  
2.  <span data-ttu-id="3b669-194">建立 `gMAX_CPU_PERCENT_20` 工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="3b669-194">Creates the `gMAX_CPU_PERCENT_20` workload group.</span></span>  
  
3.  <span data-ttu-id="3b669-195">建立 `rgclassifier_MAX_CPU()` 分類函數，而且它會使用在上述範例中建立的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="3b669-195">Creates the `rgclassifier_MAX_CPU()` classifier function, which uses the user name created in the preceding example.</span></span>  
  
4.  <span data-ttu-id="3b669-196">向資源管理員註冊此分類函數。</span><span class="sxs-lookup"><span data-stu-id="3b669-196">Registers the classifier function with Resource Governor.</span></span>  
  
 <span data-ttu-id="3b669-197">認可交易之後，此範例就會套用在 ALTER WORKLOAD GROUP 或 ALTER RESOURCE POOL 陳述式中要求的組態變更。</span><span class="sxs-lookup"><span data-stu-id="3b669-197">After committing the transaction, the example applies the configuration changes requested in the ALTER WORKLOAD GROUP or ALTER RESOURCE POOL statements.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3b669-198">下列範例會使用在「範例 A：設定登入和使用者 (Transact-SQL)」中所建立範例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者的使用者名稱：網域名稱  `\MAX_CPU`。</span><span class="sxs-lookup"><span data-stu-id="3b669-198">The following example uses the user name of the sample [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user created in "Example A: Setting Up a Login and User (Transact-SQL)," *domain_name*`\MAX_CPU`.</span></span> <span data-ttu-id="3b669-199">請將這個名稱取代成您打算在建立低優先順序壓縮備份時使用的登入使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="3b669-199">Replace this with the name of the user of the login that you plan to use for creating low-priority compressed backups.</span></span>  
  
```sql  
-- Configure Resource Governor.  
BEGIN TRAN  
USE master;  
-- Create a resource pool that sets the MAX_CPU_PERCENT to 20%.   
CREATE RESOURCE POOL pMAX_CPU_PERCENT_20  
   WITH  
      (MAX_CPU_PERCENT = 20);  
GO  
-- Create a workload group to use this pool.   
CREATE WORKLOAD GROUP gMAX_CPU_PERCENT_20  
USING pMAX_CPU_PERCENT_20;  
GO  
-- Create a classification function.  
-- Note that any request that does not get classified goes into   
-- the 'Default' group.  
CREATE FUNCTION dbo.rgclassifier_MAX_CPU() RETURNS sysname   
WITH SCHEMABINDING  
AS  
BEGIN  
    DECLARE @workload_group_name AS sysname  
      IF (SUSER_NAME() = 'domain_name\MAX_CPU')  
          SET @workload_group_name = 'gMAX_CPU_PERCENT_20'  
    RETURN @workload_group_name  
END;  
GO  
  
-- Register the classifier function with Resource Governor.  
ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION= dbo.rgclassifier_MAX_CPU);  
COMMIT TRAN;  
GO  
-- Start Resource Governor  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="3b669-200">[[頁首]](#Top)</span><span class="sxs-lookup"><span data-stu-id="3b669-200">[&#91;Top&#93;](#Top)</span></span>  
  
##  <a name="verifying-the-classification-of-the-current-session-transact-sql"></a><a name="verifying"></a> <span data-ttu-id="3b669-201">確認目前工作階段的分類 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3b669-201">Verifying the Classification of the Current Session (Transact-SQL)</span></span>  
 <span data-ttu-id="3b669-202">(選擇性) 以您在分類函數中指定之使用者的身分登入，然後在 [物件總管] 中發出下列 [SELECT](/sql/t-sql/queries/select-transact-sql) 陳述式，藉以確認工作階段分類：</span><span class="sxs-lookup"><span data-stu-id="3b669-202">Optionally, log in as the user that you specified in your classifier function, and verify the session classification by issuing the following [SELECT](/sql/t-sql/queries/select-transact-sql) statement in Object Explorer:</span></span>  
  
```sql  
USE master;  
SELECT sess.session_id, sess.login_name, sess.group_id, grps.name   
FROM sys.dm_exec_sessions AS sess   
JOIN sys.dm_resource_governor_workload_groups AS grps   
    ON sess.group_id = grps.group_id  
WHERE session_id > 50;  
GO  
```  
  
 <span data-ttu-id="3b669-203">在結果窗格中，**名稱**資料行應該會針對您在分類函數中指定的工作負載群組名稱，列出一或多個工作階段。</span><span class="sxs-lookup"><span data-stu-id="3b669-203">In the results pane, the **name** column should list one or more sessions for the workload-group name that you specified in your classifier function.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b669-204">如需此 SELECT 陳述式呼叫的動態管理檢視相關資訊，請參閱 [sys.dm_exec_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) 和 [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3b669-204">For information about the dynamic management views called by this SELECT statement, see [sys.dm_exec_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) and [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql).</span></span>  
  
 <span data-ttu-id="3b669-205">[[頁首]](#Top)</span><span class="sxs-lookup"><span data-stu-id="3b669-205">[&#91;Top&#93;](#Top)</span></span>  
  
##  <a name="compressing-backups-using-a-session-with-limited-cpu"></a><a name="creating_compressed_backup"></a> <span data-ttu-id="3b669-206">使用含有限制 CPU 的工作階段來壓縮備份</span><span class="sxs-lookup"><span data-stu-id="3b669-206">Compressing Backups Using a Session with Limited CPU</span></span>  
 <span data-ttu-id="3b669-207">若要在含有限制最大 CPU 的工作階段中建立壓縮備份，請以您在分類函數中指定之使用者的身分登入。</span><span class="sxs-lookup"><span data-stu-id="3b669-207">To create a compressed backup in a session with a limited maximum CPU, log in as the user specified in your classifier function.</span></span> <span data-ttu-id="3b669-208">在備份命令中， () 指定 WITH 壓縮， [!INCLUDE[tsql](../../includes/tsql-md.md)] 或選取 [**壓縮備份** ([!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) ]。</span><span class="sxs-lookup"><span data-stu-id="3b669-208">In your backup command, either specify WITH COMPRESSION ([!INCLUDE[tsql](../../includes/tsql-md.md)]) or select **Compress backup** ([!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]).</span></span> <span data-ttu-id="3b669-209">若要建立壓縮的資料庫備份，請參閱[建立完整資料庫備份 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3b669-209">To create a compressed database backup, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
### <a name="example-c-creating-a-compressed-backup-transact-sql"></a><span data-ttu-id="3b669-210">範例 C：建立壓縮備份 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3b669-210">Example C: Creating a Compressed Backup (Transact-SQL)</span></span>  
 <span data-ttu-id="3b669-211">下列 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 範例會在最近格式化的備份檔案 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 中建立 `Z:\SQLServerBackups\AdvWorksData.bak`資料庫的完整壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="3b669-211">The following [BACKUP](/sql/t-sql/statements/backup-transact-sql) example creates a compressed full backup of the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database in a newly formatted backup file, `Z:\SQLServerBackups\AdvWorksData.bak`.</span></span>  
  
```sql  
--Run backup statement in the gBackup session.  
BACKUP DATABASE AdventureWorks2012 TO DISK='Z:\SQLServerBackups\AdvWorksData.bak'   
WITH   
   FORMAT,   
   MEDIADESCRIPTION='AdventureWorks2012 Compressed Data Backups'  
   DESCRIPTION='First database backup on AdventureWorks2012 Compressed Data Backups media set'  
   COMPRESSION;  
GO  
```  
  
 <span data-ttu-id="3b669-212">[[頁首]](#Top)</span><span class="sxs-lookup"><span data-stu-id="3b669-212">[&#91;Top&#93;](#Top)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b669-213">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b669-213">See Also</span></span>  
 <span data-ttu-id="3b669-214">[建立和測試分類使用者定義函數](../resource-governor/create-and-test-a-classifier-user-defined-function.md) </span><span class="sxs-lookup"><span data-stu-id="3b669-214">[Create and Test a Classifier User-Defined Function](../resource-governor/create-and-test-a-classifier-user-defined-function.md) </span></span>  
 [<span data-ttu-id="3b669-215">資源管理員</span><span class="sxs-lookup"><span data-stu-id="3b669-215">Resource Governor</span></span>](../resource-governor/resource-governor.md)  
  
  
