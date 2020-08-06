---
title: 資料庫物件安全性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], object security
- security [Master Data Services], database objects
ms.assetid: dd5ba503-7607-45d9-ad0d-909faaade179
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9713f615a190beee5054ee55471e0db387a8a9e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687018"
---
# <a name="database-object-security-master-data-services"></a><span data-ttu-id="b48f8-102">資料庫物件安全性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b48f8-102">Database Object Security (Master Data Services)</span></span>
  <span data-ttu-id="b48f8-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫中，資料儲存在多個資料庫資料表並且顯示在檢視表中。</span><span class="sxs-lookup"><span data-stu-id="b48f8-103">In the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database, data is stored in multiple database tables and is visible in views.</span></span> <span data-ttu-id="b48f8-104">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式中受到保護的資訊，對具有 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫存取權的使用者是可見的。</span><span class="sxs-lookup"><span data-stu-id="b48f8-104">Information that you might have secured in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web application is visible to users with access to the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
 <span data-ttu-id="b48f8-105">具體來說，員工薪資資訊可能包含在 Employee 模型中，公司財務資訊可能包含在 Account 模型中。</span><span class="sxs-lookup"><span data-stu-id="b48f8-105">Specifically, employee salary information might be contained in an Employee model, or company financial information might be in an Account model.</span></span> <span data-ttu-id="b48f8-106">您可以在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 使用者介面中拒絕使用者存取這些模型，但具有資料庫存取權的使用者可以檢視此資料。</span><span class="sxs-lookup"><span data-stu-id="b48f8-106">You can deny a user access to these models in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface, but users with access to the database can view this data.</span></span>  
  
 <span data-ttu-id="b48f8-107">您可以授與資料庫物件權限，讓特定資料供使用者使用。</span><span class="sxs-lookup"><span data-stu-id="b48f8-107">You can grant permissions to database objects to make specific data available to users.</span></span> <span data-ttu-id="b48f8-108">如需授與權限的詳細資訊，請參閱 [GRANT 物件權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b48f8-108">For more information on granting permissions, see [GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql).</span></span> <span data-ttu-id="b48f8-109">如需保護 SQL Server 安全的詳細資訊，請參閱 [保護 SQL Server 的安全](../relational-databases/security/securing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b48f8-109">For more information about securing SQL server, see [Securing SQL Server](../relational-databases/security/securing-sql-server.md).</span></span>  
  
 <span data-ttu-id="b48f8-110">下列工作需要存取 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫：</span><span class="sxs-lookup"><span data-stu-id="b48f8-110">The following tasks require access to the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database:</span></span>  
  
-   [<span data-ttu-id="b48f8-111">暫存資料</span><span class="sxs-lookup"><span data-stu-id="b48f8-111">Staging Data</span></span>](#Staging)  
  
-   [<span data-ttu-id="b48f8-112">依商務規則驗證資料</span><span class="sxs-lookup"><span data-stu-id="b48f8-112">Validating Data Against Business Rules</span></span>](#rules)  
  
-   [<span data-ttu-id="b48f8-113">刪除版本</span><span class="sxs-lookup"><span data-stu-id="b48f8-113">Deleting Versions</span></span>](#Versions)  
  
-   [<span data-ttu-id="b48f8-114">立即套用階層成員權限</span><span class="sxs-lookup"><span data-stu-id="b48f8-114">Immediately Applying Hierarchy Member Permissions</span></span>](#Hierarchy)  
  
-   [<span data-ttu-id="b48f8-115">變更系統管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="b48f8-115">Changing the System Administrator Account</span></span>](#SysAdmin)  
  
-   [<span data-ttu-id="b48f8-116">設定系統設定</span><span class="sxs-lookup"><span data-stu-id="b48f8-116">Configuring System Settings</span></span>](#SysSettings)  
  
##  <a name="staging-data"></a><a name="Staging"></a> <span data-ttu-id="b48f8-117">暫存資料</span><span class="sxs-lookup"><span data-stu-id="b48f8-117">Staging Data</span></span>  
 <span data-ttu-id="b48f8-118">在下表中，每個安全物件都會有 "name" 作為名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="b48f8-118">In the following table, each securable has "name" as part of the name.</span></span> <span data-ttu-id="b48f8-119">這表示建立實體時所指定的暫存資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="b48f8-119">This indicates the name of the staging table that is specified when an entity is created.</span></span> <span data-ttu-id="b48f8-120">如需詳細資訊，請參閱[資料匯入 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="b48f8-120">For more information, see [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)</span></span>  
  
|<span data-ttu-id="b48f8-121">動作</span><span class="sxs-lookup"><span data-stu-id="b48f8-121">Action</span></span>|<span data-ttu-id="b48f8-122">安全性實體</span><span class="sxs-lookup"><span data-stu-id="b48f8-122">Securables</span></span>|<span data-ttu-id="b48f8-123">權限</span><span class="sxs-lookup"><span data-stu-id="b48f8-123">Permissions</span></span>|  
|------------|----------------|-----------------|  
|<span data-ttu-id="b48f8-124">將分葉成員及其屬性載入至暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="b48f8-124">Load leaf members and their attributes into the staging table.</span></span>|<span data-ttu-id="b48f8-125">stg.name_Leaf</span><span class="sxs-lookup"><span data-stu-id="b48f8-125">stg.name_Leaf</span></span>|<span data-ttu-id="b48f8-126">必要：INSERT</span><span class="sxs-lookup"><span data-stu-id="b48f8-126">Required: INSERT</span></span><br /><br /> <span data-ttu-id="b48f8-127">選擇性：SELECT 和 UPDATE</span><span class="sxs-lookup"><span data-stu-id="b48f8-127">Optional: SELECT and UPDATE</span></span>|  
|<span data-ttu-id="b48f8-128">將資料從 [分葉] 暫存資料表載入至適當的 MDS 資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="b48f8-128">Load the data from the Leaf staging table into the appropriate MDS database tables.</span></span>|<span data-ttu-id="b48f8-129">stg.udp_name_Leaf</span><span class="sxs-lookup"><span data-stu-id="b48f8-129">stg.udp_name_Leaf</span></span>|<span data-ttu-id="b48f8-130">執行 CREATE 陳述式之前，請先執行</span><span class="sxs-lookup"><span data-stu-id="b48f8-130">EXECUTE</span></span>|  
|<span data-ttu-id="b48f8-131">將合併成員及其屬性載入至暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="b48f8-131">Load consolidated members and their attributes into the staging table.</span></span>|<span data-ttu-id="b48f8-132">stg.name_Consolidated</span><span class="sxs-lookup"><span data-stu-id="b48f8-132">stg.name_Consolidated</span></span>|<span data-ttu-id="b48f8-133">必要：INSERT</span><span class="sxs-lookup"><span data-stu-id="b48f8-133">Required: INSERT</span></span><br /><br /> <span data-ttu-id="b48f8-134">選擇性：SELECT 和 UPDATE</span><span class="sxs-lookup"><span data-stu-id="b48f8-134">Optional: SELECT and UPDATE</span></span>|  
|<span data-ttu-id="b48f8-135">將資料從 [合併] 暫存資料表載入至適當的 MDS 資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="b48f8-135">Load the data from the Consolidated staging table into the appropriate MDS database tables.</span></span>|<span data-ttu-id="b48f8-136">stg.udp_name_Consolidated</span><span class="sxs-lookup"><span data-stu-id="b48f8-136">stg.udp_name_Consolidated</span></span>|<span data-ttu-id="b48f8-137">執行 CREATE 陳述式之前，請先執行</span><span class="sxs-lookup"><span data-stu-id="b48f8-137">EXECUTE</span></span>|  
|<span data-ttu-id="b48f8-138">在明確階層中，將分葉和合併成員的關聯性載入至臨時表。</span><span class="sxs-lookup"><span data-stu-id="b48f8-138">Load leaf and consolidated members' relationships to each other in an explicit hierarchy into the staging table.</span></span>|<span data-ttu-id="b48f8-139">stg.name_Relationship</span><span class="sxs-lookup"><span data-stu-id="b48f8-139">stg.name_Relationship</span></span>|<span data-ttu-id="b48f8-140">必要：INSERT</span><span class="sxs-lookup"><span data-stu-id="b48f8-140">Required: INSERT</span></span><br /><br /> <span data-ttu-id="b48f8-141">選擇性：SELECT 和 UPDATE</span><span class="sxs-lookup"><span data-stu-id="b48f8-141">Optional: SELECT and UPDATE</span></span>|  
|<span data-ttu-id="b48f8-142">將資料從 [關聯性] 暫存資料表載入至適當的 MDS 資料表。</span><span class="sxs-lookup"><span data-stu-id="b48f8-142">Load the data from the Relationship staging table into the appropriate MDS tables.</span></span>|<span data-ttu-id="b48f8-143">stg.udp_name_Relationship</span><span class="sxs-lookup"><span data-stu-id="b48f8-143">stg.udp_name_Relationship</span></span>|<span data-ttu-id="b48f8-144">執行 CREATE 陳述式之前，請先執行</span><span class="sxs-lookup"><span data-stu-id="b48f8-144">EXECUTE</span></span>|  
|<span data-ttu-id="b48f8-145">檢視將資料從暫存資料表插入至 MDS 資料庫資料表時發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b48f8-145">View errors that occurred when data from the staging tables was being inserted into the MDS database tables.</span></span>|<span data-ttu-id="b48f8-146">stg.udp_name_Relationship</span><span class="sxs-lookup"><span data-stu-id="b48f8-146">stg.udp_name_Relationship</span></span>|<span data-ttu-id="b48f8-147">SELECT</span><span class="sxs-lookup"><span data-stu-id="b48f8-147">SELECT</span></span>|  
  
 <span data-ttu-id="b48f8-148">如需詳細資訊，請參閱[資料匯入 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b48f8-148">For more information, see [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).</span></span>  
  
##  <a name="validating-data-against-business-rules"></a><a name="rules"></a><span data-ttu-id="b48f8-149">根據商務規則驗證資料</span><span class="sxs-lookup"><span data-stu-id="b48f8-149">Validating Data Against Business Rules</span></span>  
  
|<span data-ttu-id="b48f8-150">動作</span><span class="sxs-lookup"><span data-stu-id="b48f8-150">Action</span></span>|<span data-ttu-id="b48f8-151">安全性實體</span><span class="sxs-lookup"><span data-stu-id="b48f8-151">Securable</span></span>|<span data-ttu-id="b48f8-152">權限</span><span class="sxs-lookup"><span data-stu-id="b48f8-152">Permissions</span></span>|  
|------------|---------------|-----------------|  
|<span data-ttu-id="b48f8-153">依商務規則驗證資料版本</span><span class="sxs-lookup"><span data-stu-id="b48f8-153">Validate a version of data against business rules</span></span>|<span data-ttu-id="b48f8-154">mdm.udpValidateModel</span><span class="sxs-lookup"><span data-stu-id="b48f8-154">mdm.udpValidateModel</span></span>|<span data-ttu-id="b48f8-155">執行 CREATE 陳述式之前，請先執行</span><span class="sxs-lookup"><span data-stu-id="b48f8-155">EXECUTE</span></span>|  
  
 <span data-ttu-id="b48f8-156">如需詳細資訊，請參閱 [驗證預存程序 &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b48f8-156">For more information, see [Validation Stored Procedure &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md).</span></span>  
  
##  <a name="deleting-versions"></a><a name="Versions"></a><span data-ttu-id="b48f8-157">刪除版本</span><span class="sxs-lookup"><span data-stu-id="b48f8-157">Deleting Versions</span></span>  
  
|<span data-ttu-id="b48f8-158">動作</span><span class="sxs-lookup"><span data-stu-id="b48f8-158">Action</span></span>|<span data-ttu-id="b48f8-159">安全性實體</span><span class="sxs-lookup"><span data-stu-id="b48f8-159">Securables</span></span>|<span data-ttu-id="b48f8-160">權限</span><span class="sxs-lookup"><span data-stu-id="b48f8-160">Permissions</span></span>|  
|------------|----------------|-----------------|  
|<span data-ttu-id="b48f8-161">決定要刪除之版本的識別碼</span><span class="sxs-lookup"><span data-stu-id="b48f8-161">Determine the ID of the version you want to delete</span></span>|<span data-ttu-id="b48f8-162">mdm.viw_SYSTEM_SCHEMA_VERSION</span><span class="sxs-lookup"><span data-stu-id="b48f8-162">mdm.viw_SYSTEM_SCHEMA_VERSION</span></span>|<span data-ttu-id="b48f8-163">SELECT</span><span class="sxs-lookup"><span data-stu-id="b48f8-163">SELECT</span></span>|  
|<span data-ttu-id="b48f8-164">刪除模型的版本</span><span class="sxs-lookup"><span data-stu-id="b48f8-164">Delete a version of a model</span></span>|<span data-ttu-id="b48f8-165">mdm.udpVersionDelete</span><span class="sxs-lookup"><span data-stu-id="b48f8-165">mdm.udpVersionDelete</span></span>|<span data-ttu-id="b48f8-166">執行 CREATE 陳述式之前，請先執行</span><span class="sxs-lookup"><span data-stu-id="b48f8-166">EXECUTE</span></span>|  
  
 <span data-ttu-id="b48f8-167">如需詳細資訊，請參閱[刪除版本 &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-version-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b48f8-167">For more information, see [Delete a Version &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-version-master-data-services.md).</span></span>  
  
##  <a name="immediately-applying-hierarchy-member-permissions"></a><a name="Hierarchy"></a><span data-ttu-id="b48f8-168">立即套用階層成員許可權</span><span class="sxs-lookup"><span data-stu-id="b48f8-168">Immediately Applying Hierarchy Member Permissions</span></span>  
  
|<span data-ttu-id="b48f8-169">動作</span><span class="sxs-lookup"><span data-stu-id="b48f8-169">Action</span></span>|<span data-ttu-id="b48f8-170">安全性實體</span><span class="sxs-lookup"><span data-stu-id="b48f8-170">Securables</span></span>|<span data-ttu-id="b48f8-171">權限</span><span class="sxs-lookup"><span data-stu-id="b48f8-171">Permissions</span></span>|  
|------------|----------------|-----------------|  
|<span data-ttu-id="b48f8-172">立即套用成員權限</span><span class="sxs-lookup"><span data-stu-id="b48f8-172">Immediately apply member permissions</span></span>|<span data-ttu-id="b48f8-173">mdm.udpSecurityMemberProcessRebuildModel</span><span class="sxs-lookup"><span data-stu-id="b48f8-173">mdm.udpSecurityMemberProcessRebuildModel</span></span>|<span data-ttu-id="b48f8-174">執行 CREATE 陳述式之前，請先執行</span><span class="sxs-lookup"><span data-stu-id="b48f8-174">EXECUTE</span></span>|  
  
 <span data-ttu-id="b48f8-175">如需詳細資訊，請參閱[立即套用成員權限 &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b48f8-175">For more information, see [Immediately Apply Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md).</span></span>  
  
##  <a name="changing-the-system-administrator-account"></a><a name="SysAdmin"></a><span data-ttu-id="b48f8-176">變更系統管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="b48f8-176">Changing the System Administrator Account</span></span>  
  
|<span data-ttu-id="b48f8-177">動作</span><span class="sxs-lookup"><span data-stu-id="b48f8-177">Action</span></span>|<span data-ttu-id="b48f8-178">安全性實體</span><span class="sxs-lookup"><span data-stu-id="b48f8-178">Securables</span></span>|<span data-ttu-id="b48f8-179">權限</span><span class="sxs-lookup"><span data-stu-id="b48f8-179">Permissions</span></span>|  
|------------|----------------|-----------------|  
|<span data-ttu-id="b48f8-180">決定新管理員的 SID</span><span class="sxs-lookup"><span data-stu-id="b48f8-180">Determine the SID of the new administrator</span></span>|<span data-ttu-id="b48f8-181">mdm.tblUser</span><span class="sxs-lookup"><span data-stu-id="b48f8-181">mdm.tblUser</span></span>|<span data-ttu-id="b48f8-182">SELECT</span><span class="sxs-lookup"><span data-stu-id="b48f8-182">SELECT</span></span>|  
|<span data-ttu-id="b48f8-183">變更系統管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="b48f8-183">Change the system administrator account</span></span>|<span data-ttu-id="b48f8-184">mdm.udpSecuritySetAdministrator</span><span class="sxs-lookup"><span data-stu-id="b48f8-184">mdm.udpSecuritySetAdministrator</span></span>|<span data-ttu-id="b48f8-185">執行 CREATE 陳述式之前，請先執行</span><span class="sxs-lookup"><span data-stu-id="b48f8-185">EXECUTE</span></span>|  
  
 <span data-ttu-id="b48f8-186">如需詳細資訊，請參閱[將系統管理員帳戶變更 &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b48f8-186">For more information, see [Change the System Administrator Account &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md).</span></span>  
  
##  <a name="configuring-system-settings"></a><a name="SysSettings"></a><span data-ttu-id="b48f8-187">正在進行系統設定</span><span class="sxs-lookup"><span data-stu-id="b48f8-187">Configuring System Settings</span></span>  
 <span data-ttu-id="b48f8-188">有些系統設定可設定控制 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]的行為。</span><span class="sxs-lookup"><span data-stu-id="b48f8-188">There are system settings that you can configure to control behavior in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="b48f8-189">您可以在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中調整這些設定；如果您有 UPDATE 存取權，也可以直接在 mdm.tblSystemSetting 資料庫資料表中調整這些設定。</span><span class="sxs-lookup"><span data-stu-id="b48f8-189">You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or if you have UPDATE access, you can adjust these settings directly in the mdm.tblSystemSetting database table.</span></span> <span data-ttu-id="b48f8-190">如需詳細資訊，請參閱 [系統設定 &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b48f8-190">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b48f8-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b48f8-191">See Also</span></span>  
 [<span data-ttu-id="b48f8-192">安全性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b48f8-192">Security &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/security-master-data-services.md)  
  
  
