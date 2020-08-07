---
title: 建立伺服器角色 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverrole.members.f1
- SQL12.SWB.SERVERROLE.GENERAL.F1
- sql12.swb.serverrole.memberships.f1
helpviewer_keywords:
- SERVER ROLE, creating
ms.assetid: 74f19992-8082-4ed7-92a1-04fe676ee82d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 45c3d5bb9c9c7fdae9abe18ab3cb808cae4c1fa1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598786"
---
# <a name="create-a-server-role"></a><span data-ttu-id="3b4ec-102">建立伺服器角色</span><span class="sxs-lookup"><span data-stu-id="3b4ec-102">Create a Server Role</span></span>
  <span data-ttu-id="3b4ec-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中建立新的伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-103">This topic describes how to create a new server role in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="3b4ec-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="3b4ec-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3b4ec-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="3b4ec-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3b4ec-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="3b4ec-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3b4ec-107">安全性</span><span class="sxs-lookup"><span data-stu-id="3b4ec-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3b4ec-108">**若要建立新的伺服器角色，可使用下列項目：**</span><span class="sxs-lookup"><span data-stu-id="3b4ec-108">**To create a new server role, using:**</span></span>  
  
     [<span data-ttu-id="3b4ec-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3b4ec-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3b4ec-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3b4ec-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3b4ec-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="3b4ec-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3b4ec-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="3b4ec-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="3b4ec-113">不能將資料庫層級安全性實體授與伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-113">Server roles cannot be granted permission on database-level securables.</span></span> <span data-ttu-id="3b4ec-114">若要建立資料庫角色，請參閱 [CREATE ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-role-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-114">To create database roles, see [CREATE ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-role-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3b4ec-115">Security</span><span class="sxs-lookup"><span data-stu-id="3b4ec-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3b4ec-116">權限</span><span class="sxs-lookup"><span data-stu-id="3b4ec-116">Permissions</span></span>  
  
-   <span data-ttu-id="3b4ec-117">需要 CREATE SERVER ROLE 權限或系統管理員 (sysadmin) 固定伺服器角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-117">Requires CREATE SERVER ROLE permission or membership in the sysadmin fixed server role.</span></span>  
  
-   <span data-ttu-id="3b4ec-118">此外，也需要登入之 *server_principal* 的 IMPERSONATE、作為 *server_principal*之伺服器角色的 ALTER 權限，或作為 server_principal 之 Windows 群組中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-118">Also requires IMPERSONATE on the *server_principal* for logins, ALTER permission for server roles used as the *server_principal*, or membership in a Windows group that is used as the server_principal.</span></span>  
  
-   <span data-ttu-id="3b4ec-119">當您使用 AUTHORIZATION 選項指派伺服器角色擁有權時，也必須具備下列權限：</span><span class="sxs-lookup"><span data-stu-id="3b4ec-119">When you use the AUTHORIZATION option to assign server role ownership, the following permissions are also required:</span></span>  
  
    -   <span data-ttu-id="3b4ec-120">若要指派伺服器角色擁有權給另一個登入，則需要該登入的 IMPERSONATE 權限。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-120">To assign ownership of a server role to another login, requires IMPERSONATE permission on that login.</span></span>  
  
    -   <span data-ttu-id="3b4ec-121">若要指派伺服器角色擁有權給另一個伺服器角色，則需要收件者伺服器角色中的成員資格，或該伺服器角色的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-121">To assign ownership of a server role to another server role, requires membership in the recipient server role or ALTER permission on that server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3b4ec-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3b4ec-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-new-server-role"></a><span data-ttu-id="3b4ec-123">若要建立新的伺服器角色</span><span class="sxs-lookup"><span data-stu-id="3b4ec-123">To create a new server role</span></span>  
  
1.  <span data-ttu-id="3b4ec-124">在 [物件總管] 中，展開要建立新伺服器角色的伺服器。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-124">In Object Explorer, expand the server where you want to create the new server role.</span></span>  
  
2.  <span data-ttu-id="3b4ec-125">展開 **[安全性]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-125">Expand the **Security** folder.</span></span>  
  
3.  <span data-ttu-id="3b4ec-126">以滑鼠右鍵按一下 [伺服器角色] 資料夾，然後選取 [新增伺服器角色...]。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-126">Right-click the **Server Roles** folder and select **New Server Role...**.</span></span>  
  
4.  <span data-ttu-id="3b4ec-127">在 [**新增伺服器角色-**_server_role_name_ ] 對話方塊的 [**一般**] 頁面上，于 [**伺服器角色名稱**] 方塊中輸入新伺服器角色的名稱。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-127">In the **New Server Role -**_server_role_name_ dialog box, on the **General** page, enter a name for the new server role in the **Server role name** box.</span></span>  
  
5.  <span data-ttu-id="3b4ec-128">在 **[擁有者]** 方塊中，輸入將擁有新角色之伺服器主體的名稱。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-128">In the **Owner** box, enter the name of the server principal that will own the new role.</span></span> <span data-ttu-id="3b4ec-129">或者，按一下省略符號 **(...)** ，開啟 [選取伺服器登入或角色] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-129">Alternately, click the ellipsis **(...)** to open the **Select Server Login or Role** dialog box.</span></span>  
  
6.  <span data-ttu-id="3b4ec-130">在 [安全性實體] 底下，選取一或多個伺服器層級安全性實體。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-130">Under **Securables**, select one or more server-level securables.</span></span> <span data-ttu-id="3b4ec-131">已選取安全性實體時，您可以對這個伺服器角色授與或拒絕該安全性實體的權限。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-131">When a securable is selected, this server role can be granted or denied permissions on that securable.</span></span>  
  
7.  <span data-ttu-id="3b4ec-132">在 [權限；明確] 方塊中，選取核取方塊，對此伺服器角色授與、以授與選項授與 (grant with grant)，或拒絕所選取安全性實體的權限。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-132">In the **Permissions: Explicit** box, select the check box to grant, grant with grant, or deny permission to this server role for the selected securables.</span></span> <span data-ttu-id="3b4ec-133">如果不能授與或拒絕所有選取之安全性實體的權限，此權限表示為部分選取。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-133">If a permission cannot be granted or denied to all of the selected securables, the permission is represented as a partial select.</span></span>  
  
8.  <span data-ttu-id="3b4ec-134">在 **[成員]** 頁面上，使用 **[加入]** 按鈕，將代表個人或群組的登入加入至新的伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-134">On the **Members** page, use the **Add** button to add logins that represent individuals or groups to the new server role.</span></span>  
  
9. <span data-ttu-id="3b4ec-135">使用者定義的伺服器角色可以是另一個伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-135">A user-defined server role can be a member of another server role.</span></span> <span data-ttu-id="3b4ec-136">在 [成員資格] 頁面上，選取核取方塊，讓目前使用者定義的伺服器角色成為選取之伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-136">On the **Memberships** page, select a check box to make the current user-defined server role a member of a selected server role.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3b4ec-137">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3b4ec-137">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-new-server-role"></a><span data-ttu-id="3b4ec-138">若要建立新的伺服器角色</span><span class="sxs-lookup"><span data-stu-id="3b4ec-138">To create a new server role</span></span>  
  
1.  <span data-ttu-id="3b4ec-139">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-139">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3b4ec-140">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-140">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3b4ec-141">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-141">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    --Creates the server role auditors that is owned the securityadmin fixed server role.  
    USE master;  
    CREATE SERVER ROLE auditors AUTHORIZATION securityadmin;  
    GO  
    ```  
  
 <span data-ttu-id="3b4ec-142">如需詳細資訊，請參閱 [CREATE SERVER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-role-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3b4ec-142">For more information, see [CREATE SERVER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-role-transact-sql).</span></span>  
  
  
