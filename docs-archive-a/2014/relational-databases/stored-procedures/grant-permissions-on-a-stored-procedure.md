---
title: 授與預存程序的權限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], permissions
ms.assetid: a7d15816-a788-4099-ad91-dc4b26618299
author: stevestein
ms.author: sstein
ms.openlocfilehash: 23ea130b9d2033128adc99413c053d66936e3ccc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596570"
---
# <a name="grant-permissions-on-a-stored-procedure"></a><span data-ttu-id="e94c5-102">授與預存程序的權限</span><span class="sxs-lookup"><span data-stu-id="e94c5-102">Grant Permissions on a Stored Procedure</span></span>
  <span data-ttu-id="e94c5-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中授與預存程序的權限。</span><span class="sxs-lookup"><span data-stu-id="e94c5-103">This topic describes how to grant permissions on a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e94c5-104">權限可以授與資料庫中現有的使用者、資料庫角色或應用程式角色。</span><span class="sxs-lookup"><span data-stu-id="e94c5-104">Permissions can be granted to an existing user, database role, or application role in the database.</span></span>  
  
 <span data-ttu-id="e94c5-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="e94c5-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e94c5-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="e94c5-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e94c5-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="e94c5-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e94c5-108">安全性</span><span class="sxs-lookup"><span data-stu-id="e94c5-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e94c5-109">**使用下列方法授與預存程序的權限：**</span><span class="sxs-lookup"><span data-stu-id="e94c5-109">**To grant permissions on a stored procedure, using:**</span></span>  
  
     [<span data-ttu-id="e94c5-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e94c5-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e94c5-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e94c5-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e94c5-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="e94c5-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e94c5-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="e94c5-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e94c5-114">您無法使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 授與系統程序或系統函數的權限。</span><span class="sxs-lookup"><span data-stu-id="e94c5-114">You cannot use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to grant permissions on system procedures or system functions.</span></span> <span data-ttu-id="e94c5-115">請改用 [GRANT 物件權限](/sql/t-sql/statements/grant-object-permissions-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="e94c5-115">Use [GRANT Object Permissions](/sql/t-sql/statements/grant-object-permissions-transact-sql) instead.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e94c5-116">Security</span><span class="sxs-lookup"><span data-stu-id="e94c5-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e94c5-117">權限</span><span class="sxs-lookup"><span data-stu-id="e94c5-117">Permissions</span></span>  
 <span data-ttu-id="e94c5-118">同意授權者 (或是指定了 AS 選項的主體) 必須具有指定了 GRANT OPTION 的權限本身，或是具有隱含目前正在授與權限的更高權限。</span><span class="sxs-lookup"><span data-stu-id="e94c5-118">The grantor (or the principal specified with the AS option) must have either the permission itself with GRANT OPTION, or a higher permission that implies the permission being granted.</span></span> <span data-ttu-id="e94c5-119">需要程序所屬結構描述的 ALTER 權限，或程序的 CONTROL 權限。</span><span class="sxs-lookup"><span data-stu-id="e94c5-119">Requires ALTER permission on the schema to which the procedure belongs, or CONTROL permission on the procedure.</span></span> <span data-ttu-id="e94c5-120">如需詳細資訊，請參閱 [GRANT 物件權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql)中授與預存程序的權限。</span><span class="sxs-lookup"><span data-stu-id="e94c5-120">For more information, see [GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e94c5-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e94c5-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a><span data-ttu-id="e94c5-122">若要授與預存程序的權限</span><span class="sxs-lookup"><span data-stu-id="e94c5-122">To grant permissions on a stored procedure</span></span>  
  
1.  <span data-ttu-id="e94c5-123">在物件總管中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="e94c5-123">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="e94c5-124">依序展開 **[資料庫]** 、程序所屬的資料庫，以及 **[可程式性]** 。</span><span class="sxs-lookup"><span data-stu-id="e94c5-124">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="e94c5-125">展開 [預存程序]，以滑鼠右鍵按一下要授與權限的程序，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="e94c5-125">Expand **Stored Procedures**, right-click the procedure to grant permissions on, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="e94c5-126">在 **[預存程序屬性]** 上選取 **[權限]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="e94c5-126">From **Stored Procedure Properties**, select the **Permissions** page.</span></span>  
  
5.  <span data-ttu-id="e94c5-127">若要將權限授與使用者、資料庫角色或應用程式角色，請按一下 **[搜尋]** 。</span><span class="sxs-lookup"><span data-stu-id="e94c5-127">To grant permissions to a user, database role, or application role, click **Search**.</span></span>  
  
6.  <span data-ttu-id="e94c5-128">在 **[選取使用者或角色]** 中，按一下 **[物件類型]** ，以加入或清除想要的使用者和角色。</span><span class="sxs-lookup"><span data-stu-id="e94c5-128">In **Select Users or Roles**, click **Object Types** to add or clear the users and roles you want.</span></span>  
  
7.  <span data-ttu-id="e94c5-129">按一下 **[瀏覽]** 顯示使用者或角色的清單。</span><span class="sxs-lookup"><span data-stu-id="e94c5-129">Click **Browse** to display the list of users or roles.</span></span> <span data-ttu-id="e94c5-130">選取要獲得權限授與的使用者或角色。</span><span class="sxs-lookup"><span data-stu-id="e94c5-130">Select the users or roles to whom permissions should be granted.</span></span>  
  
8.  <span data-ttu-id="e94c5-131">在 **[明確權限]** 方格中，選取要授與指定使用者或角色的權限。</span><span class="sxs-lookup"><span data-stu-id="e94c5-131">In the **Explicit Permissions** grid, select the permissions to grant to the specified user or role.</span></span> <span data-ttu-id="e94c5-132">如需權限的說明，請參閱 [權限 &#40;Database Engine&#41;](../security/permissions-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="e94c5-132">For a description of the permissions, see [Permissions &#40;Database Engine&#41;](../security/permissions-database-engine.md).</span></span>  
  
 <span data-ttu-id="e94c5-133">選取 **[授與]** 表示要將指定的權限提供給被授與者。</span><span class="sxs-lookup"><span data-stu-id="e94c5-133">Selecting **Grant** indicates the grantee will be given the specified permission.</span></span> <span data-ttu-id="e94c5-134">選取 **[可授與]** 則表示授與者也能夠將指定的權限授與給其他主體。</span><span class="sxs-lookup"><span data-stu-id="e94c5-134">Selecting **Grant With** indicates that the grantee will also be able to grant the specified permission to other principals.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e94c5-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e94c5-135">Using Transact-SQL</span></span>  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a><span data-ttu-id="e94c5-136">若要授與預存程序的權限</span><span class="sxs-lookup"><span data-stu-id="e94c5-136">To grant permissions on a stored procedure</span></span>  
  
1.  <span data-ttu-id="e94c5-137">連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e94c5-137">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e94c5-138">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="e94c5-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e94c5-139">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="e94c5-139">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e94c5-140">此範例會將預存程序 `EXECUTE` 的 `HumanResources.uspUpdateEmployeeHireInfo` 權限授與名為 `Recruiting11`的應用程式角色。</span><span class="sxs-lookup"><span data-stu-id="e94c5-140">This example grants `EXECUTE` permission on the stored procedure `HumanResources.uspUpdateEmployeeHireInfo` to an application role named `Recruiting11`.</span></span>  
  
```sql  
USE AdventureWorks2012;   
GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    TO Recruiting11;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="e94c5-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e94c5-141">See Also</span></span>  
 <span data-ttu-id="e94c5-142">[sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e94c5-142">[sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql) </span></span>  
 <span data-ttu-id="e94c5-143">[GRANT 物件權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e94c5-143">[GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql) </span></span>  
 <span data-ttu-id="e94c5-144">[建立預存程序](../stored-procedures/create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="e94c5-144">[Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="e94c5-145">[修改預存程序](modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="e94c5-145">[Modify a Stored Procedure](modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="e94c5-146">[刪除預存程序](../stored-procedures/delete-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="e94c5-146">[Delete a Stored Procedure](../stored-procedures/delete-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="e94c5-147">重新命名預存程序</span><span class="sxs-lookup"><span data-stu-id="e94c5-147">Rename a Stored Procedure</span></span>](rename-a-stored-procedure.md)  
  
  
