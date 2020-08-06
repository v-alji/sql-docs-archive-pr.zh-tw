---
title: 允許非管理員使用複寫監視器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, non-administrators access
ms.assetid: 1cf21d9e-831d-41a1-a5a0-83ff6d22fa86
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f4a7699c555086d627e4c3a52ea70acf931ea1af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593942"
---
# <a name="allow-non-administrators-to-use-replication-monitor"></a><span data-ttu-id="282c1-102">允許非管理員使用複寫監視器</span><span class="sxs-lookup"><span data-stu-id="282c1-102">Allow Non-Administrators to Use Replication Monitor</span></span>
  <span data-ttu-id="282c1-103">本主題描述如何允許非管理員藉由使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中使用複寫監視器。</span><span class="sxs-lookup"><span data-stu-id="282c1-103">This topic describes how to allow non-administrators to use Replication Monitor in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="282c1-104">「複寫監視器」可供身為下列角色成員的使用者使用：</span><span class="sxs-lookup"><span data-stu-id="282c1-104">Replication Monitor can be used by users who are members of the following roles:</span></span>  
  
-   <span data-ttu-id="282c1-105">**系統管理員 (sysadmin)** 固定伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="282c1-105">The **sysadmin** fixed server role.</span></span>  
  
     <span data-ttu-id="282c1-106">這些使用者可監視複寫，並且擁有變更複寫屬性的完全控制，例如，代理程式排程、代理程式設定檔等。</span><span class="sxs-lookup"><span data-stu-id="282c1-106">These users can monitor replication and have full control over changing replication properties such as agent schedules, agent profiles, and so on.</span></span>  
  
-   <span data-ttu-id="282c1-107">`replmonitor`散發資料庫中的資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="282c1-107">The `replmonitor` database role in the distribution database.</span></span>  
  
     <span data-ttu-id="282c1-108">這些使用者可監視複寫，但無法變更任何複寫屬性。</span><span class="sxs-lookup"><span data-stu-id="282c1-108">These users can monitor replication, but cannot change any replication properties.</span></span>  
  
 <span data-ttu-id="282c1-109">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="282c1-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="282c1-110">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="282c1-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="282c1-111">安全性</span><span class="sxs-lookup"><span data-stu-id="282c1-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="282c1-112">**若要允許非管理員使用複寫監視器，請使用：**</span><span class="sxs-lookup"><span data-stu-id="282c1-112">**To allow non-administrators to use Replication Monitor, using:**</span></span>  
  
     [<span data-ttu-id="282c1-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="282c1-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="282c1-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="282c1-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="282c1-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="282c1-115">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="282c1-116">Security</span><span class="sxs-lookup"><span data-stu-id="282c1-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="282c1-117">權限</span><span class="sxs-lookup"><span data-stu-id="282c1-117">Permissions</span></span>  
 <span data-ttu-id="282c1-118">若要允許非管理員使用「複寫監視器」，系統管理員（ **sysadmin** ）固定伺服器角色的成員必須將使用者加入至散發資料庫，並將該使用者指派給該 `replmonitor` 角色。</span><span class="sxs-lookup"><span data-stu-id="282c1-118">To allow non-administrators to use Replication Monitor, a member of the **sysadmin** fixed server role must add the user to the distribution database and assign that user to the `replmonitor` role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="282c1-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="282c1-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-allow-non-administrators-to-use-replication-monitor"></a><span data-ttu-id="282c1-120">允許非管理員使用複寫監視器</span><span class="sxs-lookup"><span data-stu-id="282c1-120">To allow non-administrators to use Replication Monitor</span></span>  
  
1.  <span data-ttu-id="282c1-121">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中連接到散發者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="282c1-121">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connect to the Distributor, and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="282c1-122">展開 **[資料庫]**，展開 **[系統資料庫]**，並且展開散發資料庫 (預設名稱為 **distribution** )。</span><span class="sxs-lookup"><span data-stu-id="282c1-122">Expand **Databases**, expand **System Databases**, and then expand the distribution database (named **distribution** by default).</span></span>  
  
3.  <span data-ttu-id="282c1-123">展開 **[安全性]**，以滑鼠右鍵按一下 **[使用者]**，再按一下 **[新增使用者]**。</span><span class="sxs-lookup"><span data-stu-id="282c1-123">Expand **Security**, right-click **Users**, and then click **New User**.</span></span>  
  
4.  <span data-ttu-id="282c1-124">輸入使用者名稱及使用者的登入。</span><span class="sxs-lookup"><span data-stu-id="282c1-124">Enter a user name and login for the user.</span></span>  
  
5.  <span data-ttu-id="282c1-125">選取的預設架構 `replmonitor` 。</span><span class="sxs-lookup"><span data-stu-id="282c1-125">Select a default schema of `replmonitor`.</span></span>  
  
6.  <span data-ttu-id="282c1-126">選取 `replmonitor` [**資料庫角色成員資格**] 方格中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="282c1-126">Select the `replmonitor` check box in the **Database role membership** grid.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="282c1-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="282c1-127">Using Transact-SQL</span></span>  
  
#### <a name="to-add-a-user-to-the-replmonitor-fixed-database-role"></a><span data-ttu-id="282c1-128">若要將使用者加入至 replmonitor 固定資料庫角色</span><span class="sxs-lookup"><span data-stu-id="282c1-128">To add a user to the replmonitor fixed database role</span></span>  
  
1.  <span data-ttu-id="282c1-129">在散發資料庫的「散發者」端，執行 [sp_helpuser &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpuser-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="282c1-129">At the Distributor on the distribution database, execute [sp_helpuser &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpuser-transact-sql).</span></span> <span data-ttu-id="282c1-130">如果使用者未列于 `UserName` 結果集中的，則必須使用[CREATE User &#40;transact-sql&#41;](/sql/t-sql/statements/create-user-transact-sql)語句，將使用者授與散發資料庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="282c1-130">If the user is not listed in `UserName` in the result set, the user must be granted access to the distribution database using the [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) statement.</span></span>  
  
2.  <span data-ttu-id="282c1-131">在散發資料庫的「散發者」端，執行[sp_helprolemember &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql)，針對參數指定的值 `replmonitor` **@rolename** 。</span><span class="sxs-lookup"><span data-stu-id="282c1-131">At the Distributor on the distribution database, execute [sp_helprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql), specifying a value of `replmonitor` for the **@rolename** parameter.</span></span> <span data-ttu-id="282c1-132">如果使用者列于 `MemberName` 結果集中的，則該使用者已屬於此角色。</span><span class="sxs-lookup"><span data-stu-id="282c1-132">If the user is listed in `MemberName` in the result set, the user already belongs to this role.</span></span>  
  
3.  <span data-ttu-id="282c1-133">如果使用者不屬於該 `replmonitor` 角色，請在散發資料庫的「散發者」[端執行 Sp_addrolemember &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="282c1-133">If the user does not belong to the `replmonitor` role, execute [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) at the Distributor on the distribution database.</span></span> <span data-ttu-id="282c1-134">針對指定的值 `replmonitor` **@rolename** ，並針對新增資料庫使用者或 Windows 登入的名稱 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] **@membername** 。</span><span class="sxs-lookup"><span data-stu-id="282c1-134">Specify a value of `replmonitor` for **@rolename** and the name of the database user or the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows login being added for **@membername**.</span></span>  
  
#### <a name="to-remove-a-user-from-the-replmonitor-fixed-database-role"></a><span data-ttu-id="282c1-135">若要從 replmonitor 固定資料庫角色移除使用者</span><span class="sxs-lookup"><span data-stu-id="282c1-135">To remove a user from the replmonitor fixed database role</span></span>  
  
1.  <span data-ttu-id="282c1-136">若要確認使用者屬於 `replmonitor` 角色，請在散發資料庫的「散發者」[端執行 Sp_helprolemember &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql) ，並為指定的值 `replmonitor` **@rolename** 。</span><span class="sxs-lookup"><span data-stu-id="282c1-136">To verify that the user belongs to the `replmonitor` role, execute [sp_helprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql) at the Distributor on the distribution database, and specify a value of `replmonitor` for **@rolename**.</span></span> <span data-ttu-id="282c1-137">如果使用者未列於結果集中的 `MemberName`，則該使用者目前不屬於此角色。</span><span class="sxs-lookup"><span data-stu-id="282c1-137">If the user is not listed in `MemberName` in the result set, the user does not currently belong to this role.</span></span>  
  
2.  <span data-ttu-id="282c1-138">如果使用者隸屬于 `replmonitor` 角色，請在散發資料庫的「散發者」[端執行 Sp_droprolemember &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="282c1-138">If the user does belong to the `replmonitor` role, execute [sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) at the Distributor on the distribution database.</span></span> <span data-ttu-id="282c1-139">針對指定的值 `replmonitor` **@rolename** ，並針對要移除的資料庫使用者或 Windows 登入指定名稱 **@membername** 。</span><span class="sxs-lookup"><span data-stu-id="282c1-139">Specify a value of `replmonitor` for **@rolename** and the name of the database user or the Windows login being removed for **@membername**.</span></span>  
  
  
