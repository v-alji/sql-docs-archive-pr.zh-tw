---
title: 加入角色 | Microsoft Docs
ms.custom: ''
ms.date: 07/14/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASEUSER.MEMBERSHIP.F1
helpviewer_keywords:
- adding a member to a role
- join a role
ms.assetid: 05c8d10d-5823-46c6-8b1a-81722da6a42b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 58e8c071672c8c3afba8d6c424488899dcf76be7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592567"
---
# <a name="join-a-role"></a><span data-ttu-id="92117-102">加入角色</span><span class="sxs-lookup"><span data-stu-id="92117-102">Join a Role</span></span>
  <span data-ttu-id="92117-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中將角色指派給登入和資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="92117-103">This topic describes how to assign roles to logins and database users in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="92117-104">您可以在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中使用角色來有效率地管理權限。</span><span class="sxs-lookup"><span data-stu-id="92117-104">Use roles in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to efficiently manage permissions.</span></span> <span data-ttu-id="92117-105">您可以將權限指派給角色，然後在這些角色中加入和移除使用者與登入。</span><span class="sxs-lookup"><span data-stu-id="92117-105">Assign permissions to roles, and then add and remove users and logins to the roles.</span></span> <span data-ttu-id="92117-106">使用角色時，不需要針對每位使用者個別維護權限。</span><span class="sxs-lookup"><span data-stu-id="92117-106">By using roles, permissions do not have to be individually maintained for each user.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="92117-107">支援四種類型的角色。</span><span class="sxs-lookup"><span data-stu-id="92117-107">supports four types of roles.</span></span>  
  
-   <span data-ttu-id="92117-108">固定伺服器角色</span><span class="sxs-lookup"><span data-stu-id="92117-108">Fixed server roles</span></span>  
  
-   <span data-ttu-id="92117-109">使用者定義伺服器角色</span><span class="sxs-lookup"><span data-stu-id="92117-109">User-defined server roles</span></span>  
  
-   <span data-ttu-id="92117-110">固定資料庫角色</span><span class="sxs-lookup"><span data-stu-id="92117-110">Fixed database roles</span></span>  
  
-   <span data-ttu-id="92117-111">使用者定義資料庫角色</span><span class="sxs-lookup"><span data-stu-id="92117-111">User-defined database roles</span></span>  
  
 <span data-ttu-id="92117-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]會自動提供固定角色。</span><span class="sxs-lookup"><span data-stu-id="92117-112">The fixed roles are automatically available in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="92117-113">固定角色擁有完成一般工作的必要權限。</span><span class="sxs-lookup"><span data-stu-id="92117-113">Fixed roles have the necessary permissions to accomplish common tasks.</span></span> <span data-ttu-id="92117-114">如需有關固定角色的詳細資訊，請參閱下列連結。</span><span class="sxs-lookup"><span data-stu-id="92117-114">For more information about fixed roles, see the following links.</span></span> <span data-ttu-id="92117-115">使用者定義角色是由您所建立，而且可使用您所選取的權限來自訂。</span><span class="sxs-lookup"><span data-stu-id="92117-115">User-defined roles are created by you, and can be customized with the permissions that you select.</span></span> <span data-ttu-id="92117-116">如需有關使用者定義角色的詳細資訊，請參閱下列連結。</span><span class="sxs-lookup"><span data-stu-id="92117-116">For more information about user-defined roles, see the following links.</span></span>  
  
 <span data-ttu-id="92117-117">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="92117-117">**In This Topic**</span></span>  
  
-   <span data-ttu-id="92117-118">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="92117-118">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="92117-119">限制事項</span><span class="sxs-lookup"><span data-stu-id="92117-119">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="92117-120">安全性</span><span class="sxs-lookup"><span data-stu-id="92117-120">Security</span></span>](#Security)  
  
-   <span data-ttu-id="92117-121">**若要將角色指派給登入和資料庫使用，使用：**</span><span class="sxs-lookup"><span data-stu-id="92117-121">**To assign roles to logins and database users, using:**</span></span>  
  
     [<span data-ttu-id="92117-122">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="92117-122">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="92117-123">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="92117-123">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="92117-124">開始之前</span><span class="sxs-lookup"><span data-stu-id="92117-124">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="92117-125">限制事項</span><span class="sxs-lookup"><span data-stu-id="92117-125">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="92117-126">變更資料庫角色的名稱不會變更識別碼、擁有者或角色的權限。</span><span class="sxs-lookup"><span data-stu-id="92117-126">Changing the name of a database role does not change ID number, owner, or permissions of the role.</span></span>  
  
-   <span data-ttu-id="92117-127">您可以在 sys.database_role_members 和 sys.database_principals 目錄檢視中，看到資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="92117-127">Database roles are visible in the sys.database_role_members and sys.database_principals catalog views.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="92117-128">Security</span><span class="sxs-lookup"><span data-stu-id="92117-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="92117-129">權限</span><span class="sxs-lookup"><span data-stu-id="92117-129">Permissions</span></span>  
 <span data-ttu-id="92117-130">需要 `ALTER ANY ROLE` 資料庫的許可權、 `ALTER` 角色的許可權，或**db_securityadmin**的成員資格。</span><span class="sxs-lookup"><span data-stu-id="92117-130">Requires `ALTER ANY ROLE` permission on the database, `ALTER` permission on the role, or membership in **db_securityadmin**.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="92117-131">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="92117-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-add-a-member-to-a-fixed-server-role"></a><span data-ttu-id="92117-132">若要將成員加入至固定伺服器角色</span><span class="sxs-lookup"><span data-stu-id="92117-132">To add a member to a fixed server role</span></span>  
  
1.  <span data-ttu-id="92117-133">在 [物件總管] 中，展開要在其中編輯固定伺服器角色的伺服器。</span><span class="sxs-lookup"><span data-stu-id="92117-133">In Object Explorer, expand the server in which you want to edit a fixed server role.</span></span>  
  
2.  <span data-ttu-id="92117-134">展開 **[安全性]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="92117-134">Expand the **Security** folder.</span></span>  
  
3.  <span data-ttu-id="92117-135">展開 **[伺服器角色]** 資料夾</span><span class="sxs-lookup"><span data-stu-id="92117-135">Expand the **Server Roles** folder</span></span>  
  
4.  <span data-ttu-id="92117-136">以滑鼠右鍵按一下要編輯的角色，並且選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="92117-136">Right-click the role you want to edit and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="92117-137">在 [**伺服器角色屬性-**_server_role_name_ ] 對話方塊的 [**成員**] 頁面上，按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="92117-137">In the **Server Role Properties -**_server_role_name_ dialog box, on the **Members** page, click **Add**.</span></span>  
  
6.  <span data-ttu-id="92117-138">在 [選取伺服器登入或角色] 對話方塊中，於 [輸入要選取的物件名稱 (範例)] 底下輸入要加入至此伺服器角色的登入或伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="92117-138">In the **Select Server Login or Role** dialog box, under **Enter the object names to select (examples)**, enter the login or server role to add to this server role.</span></span> <span data-ttu-id="92117-139">或者，按一下 [瀏覽] 並選取 [瀏覽物件] 對話方塊中任何或所有可用的物件。</span><span class="sxs-lookup"><span data-stu-id="92117-139">Alternately, click **Browse...** and select any or all of the available objects in the **Browse for Objects** dialog box.</span></span> <span data-ttu-id="92117-140">按一下 **[確定**]，返回 [**伺服器角色屬性-**_server_role_name_ ] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="92117-140">Click **OK** to return to the **Server Role Properties -**_server_role_name_ dialog box.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-add-a-member-to-a-user-defined-database-role"></a><span data-ttu-id="92117-141">若要將成員加入至使用者定義資料庫角色</span><span class="sxs-lookup"><span data-stu-id="92117-141">To add a member to a user-defined database role</span></span>  
  
1.  <span data-ttu-id="92117-142">在 [物件總管] 中，展開要在其中編輯使用者定義資料庫角色的伺服器。</span><span class="sxs-lookup"><span data-stu-id="92117-142">In Object Explorer, expand the server in which you want to edit a user-defined database role.</span></span>  
  
2.  <span data-ttu-id="92117-143">展開 **[資料庫]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="92117-143">Expand the **Databases** folder.</span></span>  
  
3.  <span data-ttu-id="92117-144">展開您要編輯其中使用者定義資料庫角色的伺服器。</span><span class="sxs-lookup"><span data-stu-id="92117-144">Expand the database in which you want to edit a user-defined database role.</span></span>  
  
4.  <span data-ttu-id="92117-145">展開 **[安全性]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="92117-145">Expand the **Security** folder.</span></span>  
  
5.  <span data-ttu-id="92117-146">展開 **[角色]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="92117-146">Expand the **Roles** folder.</span></span>  
  
6.  <span data-ttu-id="92117-147">展開 **[伺服器角色]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="92117-147">Expand the **Server Roles** folder.</span></span>  
  
7.  <span data-ttu-id="92117-148">以滑鼠右鍵按一下要編輯的角色，並且選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="92117-148">Right-click the role you want to edit and select **Properties**.</span></span>  
  
8.  <span data-ttu-id="92117-149">在 [**資料庫角色屬性-**_database_role_name_ ] 對話方塊的 [**一般**] 頁面中，按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="92117-149">In the **Database Role Properties -**_database_role_name_ dialog box, in the **General** page, click **Add**.</span></span>  
  
9. <span data-ttu-id="92117-150">在 [選取資料庫使用者或角色] 對話方塊中，於 [輸入要選取的物件名稱 (範例)] 底下輸入要加入至此資料庫角色的登入或資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="92117-150">In the **Select Database User or Role** dialog box, under **Enter the object names to select (examples)**, enter the login or database role to add to this database role.</span></span> <span data-ttu-id="92117-151">或者，按一下 [瀏覽] 並選取 [瀏覽物件] 對話方塊中任何或所有可用的物件。</span><span class="sxs-lookup"><span data-stu-id="92117-151">Alternately, click **Browse...** and select any or all of the available objects in the **Browse for Objects** dialog box.</span></span> <span data-ttu-id="92117-152">按一下 **[確定**]，返回 [**資料庫角色屬性-**_database_role_name_ ] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="92117-152">Click **OK** to return to the **Database Role Properties -**_database_role_name_ dialog box.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="92117-153">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="92117-153">Using Transact-SQL</span></span>  
  
#### <a name="to-add-a-member-to-a-fixed-server-role"></a><span data-ttu-id="92117-154">若要將成員加入至固定伺服器角色</span><span class="sxs-lookup"><span data-stu-id="92117-154">To add a member to a fixed server role</span></span>  
  
1.  <span data-ttu-id="92117-155">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="92117-155">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="92117-156">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="92117-156">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="92117-157">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="92117-157">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    ALTER SERVER ROLE diskadmin ADD MEMBER [Domain\Juan] ;  
    GO  
    ```  
  
 <span data-ttu-id="92117-158">如需詳細資訊，請參閱 [ALTER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-role-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="92117-158">For more information, see [ALTER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-role-transact-sql).</span></span>  
  
#### <a name="to-add-a-member-to-a-user-defined-database-role"></a><span data-ttu-id="92117-159">若要將成員加入至使用者定義資料庫角色</span><span class="sxs-lookup"><span data-stu-id="92117-159">To add a member to a user-defined database role</span></span>  
  
1.  <span data-ttu-id="92117-160">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="92117-160">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="92117-161">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="92117-161">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="92117-162">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="92117-162">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    ALTER ROLE Marketing ADD MEMBER [Domain\Juan] ;  
    GO  
    ```  
  
 <span data-ttu-id="92117-163">如需詳細資訊，請參閱 [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="92117-163">For more information, see [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92117-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92117-164">See Also</span></span>  
 <span data-ttu-id="92117-165">[伺服器層級角色](server-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="92117-165">[Server-Level Roles](server-level-roles.md) </span></span>  
 <span data-ttu-id="92117-166">[資料庫層級角色](../authentication-access/database-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="92117-166">[Database-Level Roles](../authentication-access/database-level-roles.md) </span></span>  
 [<span data-ttu-id="92117-167">應用程式角色</span><span class="sxs-lookup"><span data-stu-id="92117-167">Application Roles</span></span>](../authentication-access/application-roles.md)  
  
  
