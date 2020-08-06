---
title: 管理原則類別目錄 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.policycategories.f1
ms.assetid: d188a819-731f-4029-98aa-780d3299a0ce
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 168d05dd88286263da1dca5456a2c6072e946786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594005"
---
# <a name="manage-policy-categories"></a><span data-ttu-id="17167-102">管理原則類別目錄</span><span class="sxs-lookup"><span data-stu-id="17167-102">Manage Policy Categories</span></span>
  <span data-ttu-id="17167-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，將某個類別目錄中的任何或所有可用原則套用至 [!INCLUDE[tsql](../../includes/tsql-md.md)]的整個執行個體。</span><span class="sxs-lookup"><span data-stu-id="17167-103">This topic describes how to apply any or all available policies in a category to the whole instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="17167-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="17167-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="17167-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="17167-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="17167-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="17167-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="17167-107">安全性</span><span class="sxs-lookup"><span data-stu-id="17167-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="17167-108">**若要使用下列方法將類別目錄原則套用至 SQL Server 執行個體：**</span><span class="sxs-lookup"><span data-stu-id="17167-108">**To apply category policies to a SQL Server instance, using:**</span></span>  
  
     [<span data-ttu-id="17167-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="17167-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="17167-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="17167-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="17167-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="17167-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="17167-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="17167-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="17167-113">使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]時，如果未選取 **[託管資料庫訂閱]** 核取方塊，原則類別目錄必須個別套用到伺服器的每一個相關部分，例如一個或多個資料庫或資料表。</span><span class="sxs-lookup"><span data-stu-id="17167-113">When using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], if the **Mandate Database Subscriptions** check box is not selected, the policy category must be individually applied to each relevant portion of the server, such as one or more databases or tables.</span></span>  
  
-   <span data-ttu-id="17167-114">如果您指定不存在的原則類別目錄，就會建立新的原則類別目錄，而且當您執行此預存程序時，所有資料庫都會託管此訂閱。</span><span class="sxs-lookup"><span data-stu-id="17167-114">If you specify a policy category that does not exist, a new policy category is created and the subscription is mandated for all databases when you execute the stored procedure.</span></span> <span data-ttu-id="17167-115">如果您之後針對新的類別目錄清除託管的訂閱，只會針對您指定為 *target_object*的資料庫來套用此訂閱。</span><span class="sxs-lookup"><span data-stu-id="17167-115">If you then clear the mandated subscription for the new category, the subscription will only apply for the database that you specified as the *target_object*.</span></span> <span data-ttu-id="17167-116">如需如何變更授權之訂閱設定的詳細資訊，請參閱 [sp_syspolicy_update_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="17167-116">For more information about how to change a mandated subscription setting, see [sp_syspolicy_update_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="17167-117">Security</span><span class="sxs-lookup"><span data-stu-id="17167-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="17167-118">權限</span><span class="sxs-lookup"><span data-stu-id="17167-118">Permissions</span></span>  
 <span data-ttu-id="17167-119">此預存程序會在目前預存程序擁有者的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="17167-119">This stored procedure runs in the context of the current owner of the stored procedure.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="17167-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="17167-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-apply-category-policies-to-a-sql-server-instance"></a><span data-ttu-id="17167-121">若要將類別目錄原則套用至 SQL Server 執行個體</span><span class="sxs-lookup"><span data-stu-id="17167-121">To apply category policies to a SQL Server instance</span></span>  
  
1.  <span data-ttu-id="17167-122">在 **[物件總管]** 中，按一下加號展開要套用類別目錄原則的伺服器。</span><span class="sxs-lookup"><span data-stu-id="17167-122">In **Object Explorer**, click the plus sign to expand the server where you will apply category policies.</span></span>  
  
2.  <span data-ttu-id="17167-123">按一下加號展開 **[管理]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="17167-123">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="17167-124">以滑鼠右鍵按一下 [原則管理]  並選取 [管理類別目錄]  。</span><span class="sxs-lookup"><span data-stu-id="17167-124">Right-click **Policy Management** and select **Manage Categories**.</span></span>  
  
     <span data-ttu-id="17167-125">**[管理原則類別目錄]** 對話方塊中提供下列資訊：</span><span class="sxs-lookup"><span data-stu-id="17167-125">The following information is available in the **Manage Policy Categories** dialog box:</span></span>  
  
     <span data-ttu-id="17167-126">**名稱**</span><span class="sxs-lookup"><span data-stu-id="17167-126">**Name**</span></span>  
     <span data-ttu-id="17167-127">原則類別目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="17167-127">The name of the policy category.</span></span>  
  
     <span data-ttu-id="17167-128">**[託管資料庫訂閱]**</span><span class="sxs-lookup"><span data-stu-id="17167-128">**Mandate Database Subscriptions**</span></span>  
     <span data-ttu-id="17167-129">強制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上的所有資料庫強制施行原則類別目錄中的原則。</span><span class="sxs-lookup"><span data-stu-id="17167-129">Forces all databases on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to enforce policies in the policy category.</span></span>  
  
4.  <span data-ttu-id="17167-130">選取或清除 **[託管資料庫訂閱]** 下的任何或所有核取方塊，將該原則類別目錄套用至 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="17167-130">Select or clear any or all check boxes under **Mandate Database Subscriptions** to apply that policy category to the SQL Server instance.</span></span>  
  
5.  <span data-ttu-id="17167-131">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="17167-131">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="17167-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="17167-132">Using Transact-SQL</span></span>  
  
#### <a name="to-apply-category-policies-to-a-sql-server-instance"></a><span data-ttu-id="17167-133">若要將類別目錄原則套用至 SQL Server 執行個體</span><span class="sxs-lookup"><span data-stu-id="17167-133">To apply category policies to a SQL Server instance</span></span>  
  
1.  <span data-ttu-id="17167-134">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="17167-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="17167-135">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="17167-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="17167-136">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="17167-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb;  
    GO  
    -- configures the specified database to subscribe to a policy category that is named 'Table Naming Policies'.  
    EXEC dbo.sp_syspolicy_add_policy_category_subscription @target_type = N'DATABASE'  
    , @target_object = N'AdventureWorks2012'  
    , @policy_category = N'Table Naming Policies';  
    GO  
    ```  
  
 <span data-ttu-id="17167-137">如需詳細資訊，請參閱 [sp_syspolicy_add_policy_category_subscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-subscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="17167-137">For more information, see [sp_syspolicy_add_policy_category_subscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-subscription-transact-sql).</span></span>  
  
  
