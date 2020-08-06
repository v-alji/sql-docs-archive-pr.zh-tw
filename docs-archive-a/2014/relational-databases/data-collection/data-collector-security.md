---
title: 資料收集器安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
- security [data collector]
- data collector [SQL Server], security
ms.assetid: e75d6975-641e-440a-a642-cb39a583359a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c89f1658f6ae1b5bd79de96f20222b0b19529df2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592710"
---
# <a name="data-collector-security"></a><span data-ttu-id="311e1-102">資料收集器安全性</span><span class="sxs-lookup"><span data-stu-id="311e1-102">Data Collector Security</span></span>
  <span data-ttu-id="311e1-103">資料收集器會使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式所實作之以角色為基礎的安全性模型。</span><span class="sxs-lookup"><span data-stu-id="311e1-103">The data collector uses the role-based security model implemented by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="311e1-104">這個模型可讓資料庫管理員在只具有執行該工作所需權限的安全性內容中執行各種資料收集器工作。</span><span class="sxs-lookup"><span data-stu-id="311e1-104">This model lets the database administrator run the various data collector tasks in a security context that has only the permissions required to perform that task.</span></span> <span data-ttu-id="311e1-105">這個方法也可用於牽涉到內部資料表的作業，這些資料表只能使用預存程序或檢視來存取。</span><span class="sxs-lookup"><span data-stu-id="311e1-105">This approach is also used for operations involving internal tables, which can only be accessed by using a stored procedure or view.</span></span> <span data-ttu-id="311e1-106">系統不會授與任何權限給內部資料表。</span><span class="sxs-lookup"><span data-stu-id="311e1-106">No permissions are granted to internal tables.</span></span> <span data-ttu-id="311e1-107">不過，系統會針對用來存取資料表之預存程序或檢視表的使用者檢查權限。</span><span class="sxs-lookup"><span data-stu-id="311e1-107">Instead, permissions are checked on the user of the stored procedure or view that is used to access a table.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="311e1-108">此安全性模型的另一個重要層面為同心權限。</span><span class="sxs-lookup"><span data-stu-id="311e1-108">Another key aspect of this security model is concentric permissions.</span></span> <span data-ttu-id="311e1-109">在同心權限之下，較高權限的角色會繼承較低權限的角色在物件上的權限 (包括警示、操作員、作業、排程和 Proxy)。</span><span class="sxs-lookup"><span data-stu-id="311e1-109">Under concentric permissions, more privileged roles inherit the permissions of less privileged roles on objects (including alerts, operators, jobs, schedules, and proxies).</span></span> <span data-ttu-id="311e1-110">如需詳細資訊，請參閱 [SQL Server Agent Fixed Database Roles](../../ssms/agent/sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="311e1-110">For more information, see [SQL Server Agent Fixed Database Roles](../../ssms/agent/sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="311e1-111">下列章節將大略描述資料收集安全性，以及您必須授與給使用者的角色，好讓您可以設定及使用資料收集器，並執行與管理資料倉儲有關的工作。</span><span class="sxs-lookup"><span data-stu-id="311e1-111">The following sections describe data collection security in general, as well as the roles you must grant to users so they can configure and use the data collector, and carry out tasks associated with the management data warehouse.</span></span>  
  
## <a name="general-security"></a><span data-ttu-id="311e1-112">一般安全性</span><span class="sxs-lookup"><span data-stu-id="311e1-112">General Security</span></span>  
 <span data-ttu-id="311e1-113">資料收集器的安裝是根據針對 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]所指定的記載標準。</span><span class="sxs-lookup"><span data-stu-id="311e1-113">The data collector is installed according to the documented standards specified for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
### <a name="network-security"></a><span data-ttu-id="311e1-114">網路安全性</span><span class="sxs-lookup"><span data-stu-id="311e1-114">Network Security</span></span>  
 <span data-ttu-id="311e1-115">機密資訊可以在目標執行個體、與組態伺服器有關的關聯式執行個體、執行中的收集組，以及主控管理資料倉儲的伺服器之間傳遞。</span><span class="sxs-lookup"><span data-stu-id="311e1-115">Sensitive information can be passed between target instances, the relational instance associated with the configuration server, the collection sets that are running, and the server that hosts the management data warehouse.</span></span>  
  
 <span data-ttu-id="311e1-116">為了保護透過網路傳輸的任何資料，會實作標準安全性機制，例如 [!INCLUDE[tsql](../../includes/tsql-md.md)]的通訊協定加密。</span><span class="sxs-lookup"><span data-stu-id="311e1-116">To protect any data that is transferred over a network, the standard security mechanisms are implemented, such as protocol encryption for [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
## <a name="permissions-for-configuring-and-using-the-data-collector"></a><span data-ttu-id="311e1-117">設定及使用資料收集器的權限</span><span class="sxs-lookup"><span data-stu-id="311e1-117">Permissions for Configuring and Using the Data Collector</span></span>  
 <span data-ttu-id="311e1-118">根據工作而定，使用者必須是針對資料收集器提供之一個或多個固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="311e1-118">Depending on the task, users must be members of one or more of the fixed database roles provided for the data collector.</span></span> <span data-ttu-id="311e1-119">下面依照最高存取權限到最低存取權限的順序列出這些角色：</span><span class="sxs-lookup"><span data-stu-id="311e1-119">In order of most-privileged to least-privileged access, the roles are as follows:</span></span>  
  
-   `dc_admin`  
  
-   <span data-ttu-id="311e1-120">**dc_operator**</span><span class="sxs-lookup"><span data-stu-id="311e1-120">**dc_operator**</span></span>  
  
-   <span data-ttu-id="311e1-121">**dc_proxy**</span><span class="sxs-lookup"><span data-stu-id="311e1-121">**dc_proxy**</span></span>  
  
 <span data-ttu-id="311e1-122">這些角色儲存在 msdb 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="311e1-122">These roles are stored in the msdb database.</span></span> <span data-ttu-id="311e1-123">根據預設，沒有任何使用者隸屬於這些資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="311e1-123">By default, no user is a member of these database roles.</span></span> <span data-ttu-id="311e1-124">您必須明確授與這些角色的使用者成員資格。</span><span class="sxs-lookup"><span data-stu-id="311e1-124">User membership in these roles must be granted explicitly.</span></span>  
  
 <span data-ttu-id="311e1-125">身為系統管理員（ `sysadmin` ）固定伺服器角色成員的使用者，擁有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 物件和資料收集器視圖的完整存取權。</span><span class="sxs-lookup"><span data-stu-id="311e1-125">Users who are members of the `sysadmin` fixed server role have full access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent objects and data collector views.</span></span> <span data-ttu-id="311e1-126">不過，您必須將他們明確加入至資料收集器角色。</span><span class="sxs-lookup"><span data-stu-id="311e1-126">However, they need to be explicitly added to data collector roles.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="311e1-127">db_ssisadmin 角色和 dc_admin 角色的成員可以將其權限提高為系統管理員 (sysadmin)。</span><span class="sxs-lookup"><span data-stu-id="311e1-127">Members of the db_ssisadmin role and the dc_admin role may be able to elevate their privileges to sysadmin.</span></span> <span data-ttu-id="311e1-128">之所以能夠進行此權限提高，是因為這些角色可以修改 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝，而且 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 可藉由使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的 sysadmin 安全性內容由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行。</span><span class="sxs-lookup"><span data-stu-id="311e1-128">This elevation of privilege can occur because these roles can modify [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages can be executed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the sysadmin security context of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="311e1-129">若要在執行維護計畫、資料收集組和其他 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝時預防此權限提高，請將執行封裝的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業設為使用有限權限的 Proxy 帳戶，或是只將系統管理員 (sysadmin) 成員加入 db_ssisadmin 和 dc_admin 角色。</span><span class="sxs-lookup"><span data-stu-id="311e1-129">To guard against this elevation of privilege when running maintenance plans, data collection sets, and other [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs that run packages to use a proxy account with limited privileges or only add sysadmin members to the db_ssisadmin and dc_admin roles.</span></span>  
  
### <a name="dc_admin-role"></a><span data-ttu-id="311e1-130">dc_admin 角色</span><span class="sxs-lookup"><span data-stu-id="311e1-130">dc_admin Role</span></span>  
 <span data-ttu-id="311e1-131">指派給角色的使用者 `dc_admin` 具有完整的系統管理員存取權 (建立、讀取、更新和刪除伺服器實例上的資料收集器設定) 。</span><span class="sxs-lookup"><span data-stu-id="311e1-131">Users assigned to the `dc_admin` role have full administrator access (Create, Read, Update, and Delete) to the data collector configuration on a server instance.</span></span> <span data-ttu-id="311e1-132">這個角色的成員可以執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="311e1-132">Members of this role can perform the following operations:</span></span>  
  
-   <span data-ttu-id="311e1-133">設定收集器層級的屬性。</span><span class="sxs-lookup"><span data-stu-id="311e1-133">Set collector-level properties.</span></span>  
  
-   <span data-ttu-id="311e1-134">加入新的收集組。</span><span class="sxs-lookup"><span data-stu-id="311e1-134">Add new collection sets.</span></span>  
  
-   <span data-ttu-id="311e1-135">安裝新的集合類型。</span><span class="sxs-lookup"><span data-stu-id="311e1-135">Install new collection types.</span></span>  
  
-   <span data-ttu-id="311e1-136">執行 **dc_operator** 角色允許的所有作業。</span><span class="sxs-lookup"><span data-stu-id="311e1-136">Perform all the operations permitted to the **dc_operator** role.</span></span>  
  
 <span data-ttu-id="311e1-137">`dc_admin`角色是下列角色的成員：</span><span class="sxs-lookup"><span data-stu-id="311e1-137">The `dc_admin` role is a member of the following roles:</span></span>  
  
-   <span data-ttu-id="311e1-138">**SQLAgentUserRole**。</span><span class="sxs-lookup"><span data-stu-id="311e1-138">**SQLAgentUserRole**.</span></span> <span data-ttu-id="311e1-139">這個角色是建立排程及執行作業所需的角色。</span><span class="sxs-lookup"><span data-stu-id="311e1-139">This role is required to create schedules and run jobs.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="311e1-140">針對資料收集器所建立的 proxy 必須授與的存取權， `dc_admin` 才能建立它們，並在任何需要 proxy 的作業步驟中使用它們。</span><span class="sxs-lookup"><span data-stu-id="311e1-140">Proxies created for the data collector must grant access to `dc_admin` to create them and use them in any job steps that require a proxy.</span></span>  
  
-   <span data-ttu-id="311e1-141">**dc_operator**。</span><span class="sxs-lookup"><span data-stu-id="311e1-141">**dc_operator**.</span></span> <span data-ttu-id="311e1-142">的成員會 `dc_admin` 繼承指定給**dc_operator**的許可權。</span><span class="sxs-lookup"><span data-stu-id="311e1-142">Members of `dc_admin` inherit the permissions given to **dc_operator**.</span></span>  
  
### <a name="dc_operator-role"></a><span data-ttu-id="311e1-143">dc_operator 角色</span><span class="sxs-lookup"><span data-stu-id="311e1-143">dc_operator Role</span></span>  
 <span data-ttu-id="311e1-144">**dc_operator** 角色的成員具有讀取和更新的存取權。</span><span class="sxs-lookup"><span data-stu-id="311e1-144">Members of the **dc_operator** role have Read and Update access.</span></span> <span data-ttu-id="311e1-145">這個角色支援與執行和設定收集組有關的作業工作。</span><span class="sxs-lookup"><span data-stu-id="311e1-145">This role supports operations tasks related to running and configuring collection sets.</span></span> <span data-ttu-id="311e1-146">這個角色的成員可以執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="311e1-146">Members of this role can perform the following operations:</span></span>  
  
-   <span data-ttu-id="311e1-147">啟動或停止收集組。</span><span class="sxs-lookup"><span data-stu-id="311e1-147">Start or stop a collection set.</span></span>  
  
-   <span data-ttu-id="311e1-148">列舉現有的收集組。</span><span class="sxs-lookup"><span data-stu-id="311e1-148">Enumerate existing collection sets.</span></span>  
  
-   <span data-ttu-id="311e1-149">檢視與收集組有關的詳細資訊 (例如集合項目和收集頻率)。</span><span class="sxs-lookup"><span data-stu-id="311e1-149">View the detailed information (for example, collection items, and collection frequency) associated with a collection set.</span></span>  
  
-   <span data-ttu-id="311e1-150">變更現有收集組的上傳頻率。</span><span class="sxs-lookup"><span data-stu-id="311e1-150">Change the upload frequency for existing collection sets.</span></span>  
  
-   <span data-ttu-id="311e1-151">針對屬於現有收集組之一部分的集合項目變更其收集頻率。</span><span class="sxs-lookup"><span data-stu-id="311e1-151">Change the collection frequency for collection items that are part of an existing collection set.</span></span>  
  
 <span data-ttu-id="311e1-152">**dc_operator** 角色是列舉及檢視資料收集器封裝時所需下列角色的成員：</span><span class="sxs-lookup"><span data-stu-id="311e1-152">The **dc_operator** role is a member of the following roles that are required for enumerating and viewing data collector packages:</span></span>  
  
-   <span data-ttu-id="311e1-153">**db_ssisltduser**</span><span class="sxs-lookup"><span data-stu-id="311e1-153">**db_ssisltduser**</span></span>  
  
-   <span data-ttu-id="311e1-154">**db_ssisoperator**</span><span class="sxs-lookup"><span data-stu-id="311e1-154">**db_ssisoperator**</span></span>  
  
 <span data-ttu-id="311e1-155">如需詳細資訊，請參閱 [Integration Services 角色 &#40;SSIS 服務&#41;](../../integration-services/security/integration-services-roles-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="311e1-155">For more information, see [Integration Services Roles &#40;SSIS Service&#41;](../../integration-services/security/integration-services-roles-ssis-service.md).</span></span>  
  
### <a name="dc_proxy-role"></a><span data-ttu-id="311e1-156">dc_proxy 角色</span><span class="sxs-lookup"><span data-stu-id="311e1-156">dc_proxy Role</span></span>  
 <span data-ttu-id="311e1-157">**dc_proxy** 角色的成員對於資料收集器收集組和收集器層級的屬性具有讀取存取權。</span><span class="sxs-lookup"><span data-stu-id="311e1-157">Members of the **dc_proxy** role have Read access to data collector collection sets and collector-level properties.</span></span> <span data-ttu-id="311e1-158">這個角色的成員也可以執行自己所擁有的作業，並建立以現有 Proxy 帳戶身分執行的作業步驟。</span><span class="sxs-lookup"><span data-stu-id="311e1-158">Members of this role can also execute jobs that they own and create job steps that run as an existing proxy account.</span></span>  
  
 <span data-ttu-id="311e1-159">這個角色的成員可以執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="311e1-159">Members of this role can perform the following operations:</span></span>  
  
-   <span data-ttu-id="311e1-160">檢視收集組組態資訊 (例如集合項目的輸入參數及這些項目的收集頻率)。</span><span class="sxs-lookup"><span data-stu-id="311e1-160">View collection set configuration information (for example, input parameters for collection items, and the collection frequency for these items).</span></span>  
  
-   <span data-ttu-id="311e1-161">取得只能由單一預存程序存取的內部加密資訊 (例如，用於資料上傳的資料倉儲連接資訊)。</span><span class="sxs-lookup"><span data-stu-id="311e1-161">Obtain internal encrypted information that can only be accessed by a signed stored procedure (for example, data warehouse connection information used for data uploads).</span></span>  
  
-   <span data-ttu-id="311e1-162">記錄收集組執行階段事件。</span><span class="sxs-lookup"><span data-stu-id="311e1-162">Log collection-set run-time events.</span></span>  
  
 <span data-ttu-id="311e1-163">**dc_proxy** 角色是列舉及檢視資料收集器封裝時所需下列角色的成員：</span><span class="sxs-lookup"><span data-stu-id="311e1-163">The **dc_proxy** role is a member of the following roles that are required for enumerating and viewing data collector packages:</span></span>  
  
-   <span data-ttu-id="311e1-164">**db_ssisltduser**。</span><span class="sxs-lookup"><span data-stu-id="311e1-164">**db_ssisltduser**.</span></span>  
  
-   <span data-ttu-id="311e1-165">**db_ssisoperator**</span><span class="sxs-lookup"><span data-stu-id="311e1-165">**db_ssisoperator**</span></span>  
  
 <span data-ttu-id="311e1-166">如需詳細資訊，請參閱 [Integration Services 角色 &#40;SSIS 服務&#41;](../../integration-services/security/integration-services-roles-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="311e1-166">For more information, see [Integration Services Roles &#40;SSIS Service&#41;](../../integration-services/security/integration-services-roles-ssis-service.md).</span></span>  
  
## <a name="permissions-for-configuring-and-using-the-management-data-warehouse"></a><span data-ttu-id="311e1-167">設定及使用管理資料倉儲的權限</span><span class="sxs-lookup"><span data-stu-id="311e1-167">Permissions for Configuring and Using the Management Data Warehouse</span></span>  
 <span data-ttu-id="311e1-168">根據工作而定，使用者必須是針對存取管理資料倉儲所提供之一個或多個固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="311e1-168">Depending on the task, users must be members of one or more of the fixed database roles provided for accessing the management data warehouse.</span></span> <span data-ttu-id="311e1-169">下面依照最高存取權限到最低存取權限的順序列出這些角色：</span><span class="sxs-lookup"><span data-stu-id="311e1-169">In order of most-privileged to least-privileged access, the roles are as follows:</span></span>  
  
-   <span data-ttu-id="311e1-170">**mdw_admin**</span><span class="sxs-lookup"><span data-stu-id="311e1-170">**mdw_admin**</span></span>  
  
-   <span data-ttu-id="311e1-171">**mdw_writer**</span><span class="sxs-lookup"><span data-stu-id="311e1-171">**mdw_writer**</span></span>  
  
-   <span data-ttu-id="311e1-172">**mdw_reader**</span><span class="sxs-lookup"><span data-stu-id="311e1-172">**mdw_reader**</span></span>  
  
 <span data-ttu-id="311e1-173">這些角色儲存在 msdb 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="311e1-173">These roles are stored in the msdb database.</span></span> <span data-ttu-id="311e1-174">根據預設，沒有任何使用者隸屬於這些資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="311e1-174">By default, no user is a member of these database roles.</span></span> <span data-ttu-id="311e1-175">您必須明確授與這些角色的使用者成員資格。</span><span class="sxs-lookup"><span data-stu-id="311e1-175">User membership in these roles must be granted explicitly.</span></span>  
  
 <span data-ttu-id="311e1-176">身為系統管理員（ `sysadmin` ）固定伺服器角色成員的使用者具有資料收集器視圖的完整存取權。</span><span class="sxs-lookup"><span data-stu-id="311e1-176">Users who are members of the `sysadmin` fixed server role have full access to data collector views.</span></span> <span data-ttu-id="311e1-177">不過，您必須將他們明確加入至資料庫角色，才能執行其他作業。</span><span class="sxs-lookup"><span data-stu-id="311e1-177">However, they need to be explicitly added to database roles to perform other operations.</span></span>  
  
### <a name="mdw_admin-role"></a><span data-ttu-id="311e1-178">mdw_admin 角色</span><span class="sxs-lookup"><span data-stu-id="311e1-178">mdw_admin Role</span></span>  
 <span data-ttu-id="311e1-179">**mdw_admin** 角色的成員對於管理資料倉儲具有讀取、寫入、更新和刪除的存取權。</span><span class="sxs-lookup"><span data-stu-id="311e1-179">Members of the **mdw_admin** role have Read, Write, Update, and Delete access to the management data warehouse.</span></span>  
  
 <span data-ttu-id="311e1-180">這個角色的成員可以執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="311e1-180">Members of this role can perform the following operations:</span></span>  
  
-   <span data-ttu-id="311e1-181">在需要時變更管理資料倉儲結構描述 (例如，在安裝新的集合類型時加入新的資料表)。</span><span class="sxs-lookup"><span data-stu-id="311e1-181">Change the management data warehouse schema when required (for example, adding a new table when a new collection type is installed).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="311e1-182">當架構變更時，使用者也必須是角色的成員， `dc_admin` 才能安裝新的收集器型別，因為這個動作需要在 msdb 中更新資料收集器設定的許可權。</span><span class="sxs-lookup"><span data-stu-id="311e1-182">Where there is a schema change, the user must also be a member of the `dc_admin` role to install a new collector type, since this action requires permission to update the data collector configuration in msdb.</span></span>  
  
-   <span data-ttu-id="311e1-183">在管理資料倉儲上執行維護作業，例如封存或清除。</span><span class="sxs-lookup"><span data-stu-id="311e1-183">Run maintenance jobs on the management data warehouse, such as archive or cleanup.</span></span>  
  
### <a name="mdw_writer-role"></a><span data-ttu-id="311e1-184">mdw_writer 角色</span><span class="sxs-lookup"><span data-stu-id="311e1-184">mdw_writer Role</span></span>  
 <span data-ttu-id="311e1-185">**mdw_writer** 角色的成員可以將資料上傳及寫入管理資料倉儲。</span><span class="sxs-lookup"><span data-stu-id="311e1-185">Members of the **mdw_writer** role can upload and write data to the management data warehouse.</span></span> <span data-ttu-id="311e1-186">在管理資料倉儲內儲存資料的任何資料收集器都必須是這個角色的成員。</span><span class="sxs-lookup"><span data-stu-id="311e1-186">Any data collector that stores data in the management data warehouse has to be a member of this role.</span></span>  
  
### <a name="mdw_reader-role"></a><span data-ttu-id="311e1-187">mdw_reader 角色</span><span class="sxs-lookup"><span data-stu-id="311e1-187">mdw_reader Role</span></span>  
 <span data-ttu-id="311e1-188">**mdw_reader** 角色的成員對於管理資料倉儲具有讀取存取權。</span><span class="sxs-lookup"><span data-stu-id="311e1-188">Members of the **mdw_reader** role have Read access to the management data warehouse.</span></span> <span data-ttu-id="311e1-189">由於這個角色的目的是要藉由提供歷程記錄資料的存取來支援疑難排解，所以這個角色的成員無法檢視管理資料倉儲結構描述的其他元素。</span><span class="sxs-lookup"><span data-stu-id="311e1-189">Because the purpose of this role is to support troubleshooting by providing access to historical data, members of this role cannot view other elements of the management data warehouse schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="311e1-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="311e1-190">See Also</span></span>  
 [<span data-ttu-id="311e1-191">實作 SQL Server Agent 安全性</span><span class="sxs-lookup"><span data-stu-id="311e1-191">Implement SQL Server Agent Security</span></span>](../../ssms/agent/implement-sql-server-agent-security.md)  
  
  
