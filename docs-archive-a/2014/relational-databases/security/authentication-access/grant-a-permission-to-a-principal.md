---
title: 為主體授與權限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Grant permission to a principal
ms.assetid: 4107389d-05b6-4aa3-9fa8-95b40cdf05dc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4256d62bdeac2d79c51e5f3792c991e0e3b15096
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709094"
---
# <a name="grant-a-permission-to-a-principal"></a><span data-ttu-id="3e19f-102">為主體授與權限</span><span class="sxs-lookup"><span data-stu-id="3e19f-102">Grant a Permission to a Principal</span></span>
  <span data-ttu-id="3e19f-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中為主體授與權限。</span><span class="sxs-lookup"><span data-stu-id="3e19f-103">This topic describes how to grant permission to a principal in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="3e19f-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="3e19f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3e19f-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="3e19f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3e19f-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="3e19f-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3e19f-107">安全性</span><span class="sxs-lookup"><span data-stu-id="3e19f-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3e19f-108">**若要使用下列項目為主體授與權限：**</span><span class="sxs-lookup"><span data-stu-id="3e19f-108">**To grant permission to a principal, using:**</span></span>  
  
     [<span data-ttu-id="3e19f-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3e19f-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3e19f-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3e19f-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3e19f-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="3e19f-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3e19f-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="3e19f-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="3e19f-113">請考慮下列更輕鬆管理權限的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="3e19f-113">Consider the following best practices that can make managing permissions easier.</span></span>  
  
-   <span data-ttu-id="3e19f-114">將權限授與角色，而非個別登入或使用者。</span><span class="sxs-lookup"><span data-stu-id="3e19f-114">Grant permission to roles, instead of individual logins or users.</span></span> <span data-ttu-id="3e19f-115">當某位人員被另一位人員取代時，請從角色中移除離開的人員，並將新的人員加入至角色。</span><span class="sxs-lookup"><span data-stu-id="3e19f-115">When one individual is replaced by another, remove the departing individual from the role and add the new individual to the role.</span></span> <span data-ttu-id="3e19f-116">此時，許多可能與該角色相關聯的權限就會自動提供給新的人員使用。</span><span class="sxs-lookup"><span data-stu-id="3e19f-116">The many permissions that might be associated with the role will automatically be available to the new individual.</span></span> <span data-ttu-id="3e19f-117">如果組織中的許多人員需要相同的權限，只要將每位人員加入至角色，就會授與他們相同的權限。</span><span class="sxs-lookup"><span data-stu-id="3e19f-117">If several people in an organization require the same permissions, adding each of them to the role will grant them the same permissions.</span></span>  
  
-   <span data-ttu-id="3e19f-118">設定要由結構描述擁有的類似安全性實體 (資料表、檢視表和程序)，然後授與結構描述的權限。</span><span class="sxs-lookup"><span data-stu-id="3e19f-118">Configure similar securables (tables, views, and procedures) to be owned by a schema, then grant permissions to the schema.</span></span> <span data-ttu-id="3e19f-119">例如，薪資結構描述可能會擁有許多資料表、檢視表和預存程序。</span><span class="sxs-lookup"><span data-stu-id="3e19f-119">For example, the payroll schema might own several tables, views, and stored procedures.</span></span> <span data-ttu-id="3e19f-120">只要授與此結構描述的存取權，就可以同時授與執行薪資功能的所有必要權限。</span><span class="sxs-lookup"><span data-stu-id="3e19f-120">By granting access to the schema, all the necessary permissions to perform the payroll function can be granted at the same time.</span></span> <span data-ttu-id="3e19f-121">如需有關哪些安全性實體可以被授與權限的詳細資訊，請參閱＜ [Securables](../securables.md)＞。</span><span class="sxs-lookup"><span data-stu-id="3e19f-121">For more information about what securables can be granted permissions, see [Securables](../securables.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3e19f-122">Security</span><span class="sxs-lookup"><span data-stu-id="3e19f-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3e19f-123">權限</span><span class="sxs-lookup"><span data-stu-id="3e19f-123">Permissions</span></span>  
 <span data-ttu-id="3e19f-124">同意授權者 (或是指定了 AS 選項的主體) 必須具有指定了 GRANT OPTION 的權限本身，或是具有隱含目前正在授與權限的更高權限。</span><span class="sxs-lookup"><span data-stu-id="3e19f-124">The grantor (or the principal specified with the AS option) must have either the permission itself with GRANT OPTION or a higher permission that implies the permission being granted.</span></span> <span data-ttu-id="3e19f-125">**系統管理員 (sysadmin)** 固定伺服器角色的成員也能夠授與任何權限。</span><span class="sxs-lookup"><span data-stu-id="3e19f-125">Members of the **sysadmin** fixed server role can grant any permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3e19f-126">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3e19f-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-grant-permission-to-a-principal"></a><span data-ttu-id="3e19f-127">若要為主體授與權限</span><span class="sxs-lookup"><span data-stu-id="3e19f-127">To grant permission to a principal</span></span>  
  
1.  <span data-ttu-id="3e19f-128">在 [物件總管] 中，展開包含您要授與權限之物件的資料庫。</span><span class="sxs-lookup"><span data-stu-id="3e19f-128">In Object Explorer, expand the database that contains the object to which you want to grant permissions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3e19f-129">這些步驟特別處理授與預存程序的權限，但是您可以使用類似步驟加入資料表、檢視、函數、組件，以及其他安全性實體的權限。</span><span class="sxs-lookup"><span data-stu-id="3e19f-129">These steps deal specifically with granting permissions to a stored procedure, but you can use similar steps to add permissions to tables, views, functions, and assemblies, as well as other securables.</span></span> <span data-ttu-id="3e19f-130">如需詳細資訊，請參閱 [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="3e19f-130">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)</span></span>  
  
2.  <span data-ttu-id="3e19f-131">展開 **[可程式性]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3e19f-131">Expand the **Programmability** folder.</span></span>  
  
3.  <span data-ttu-id="3e19f-132">展開 **[預存程序]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3e19f-132">Expand the **Stored Procedures** folder.</span></span>  
  
4.  <span data-ttu-id="3e19f-133">以滑鼠右鍵按一下預存程序，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="3e19f-133">Right-click a stored procedure and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="3e19f-134">在 [**預存程式屬性-**_stored_procedure_name_ ] 對話方塊的 [選取頁面] 底下，選取 [**許可權**]。</span><span class="sxs-lookup"><span data-stu-id="3e19f-134">In the **Stored Procedure Properties -**_stored_procedure_name_ dialog box, under select a page, select **Permissions**.</span></span> <span data-ttu-id="3e19f-135">使用此頁面將使用者或角色加入至預存程序，並指定這些使用者或角色擁有的權限。</span><span class="sxs-lookup"><span data-stu-id="3e19f-135">Use this page to add users or roles to the stored procedure and specify the permissions those users or roles have.</span></span>  
  
6.  <span data-ttu-id="3e19f-136">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="3e19f-136">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3e19f-137">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3e19f-137">Using Transact-SQL</span></span>  
  
#### <a name="to-grant-permission-to-a-principal"></a><span data-ttu-id="3e19f-138">若要為主體授與權限</span><span class="sxs-lookup"><span data-stu-id="3e19f-138">To grant permission to a principal</span></span>  
  
1.  <span data-ttu-id="3e19f-139">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3e19f-139">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3e19f-140">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="3e19f-140">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3e19f-141">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="3e19f-141">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Grants EXECUTE permission on stored procedure HumanResources.uspUpdateEmployeeHireInfo to an application role called Recruiting11.   
    USE AdventureWorks2012;  
    GO  
    GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
        TO Recruiting11;  
    GO  
    ```  
  
 <span data-ttu-id="3e19f-142">如需詳細資訊，請參閱 [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) 和[授與物件權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3e19f-142">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) and [GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e19f-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e19f-143">See Also</span></span>  
 [<span data-ttu-id="3e19f-144">主體 &#40;Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="3e19f-144">Principals &#40;Database Engine&#41;</span></span>](principals-database-engine.md)  
  
  
