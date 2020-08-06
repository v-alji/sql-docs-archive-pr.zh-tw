---
title: 訂閱或取消訂閱原則類別目錄資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.groupsubscription.f1
ms.assetid: d2c31769-7098-428e-ad9c-ef56541b7c52
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2b4ca6f804352b57b30b42012da93e0d031be8d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699454"
---
# <a name="subscribe-or-unsubscribe-a-database--to-a-policy-category"></a><span data-ttu-id="88172-102">讓資料庫訂閱或取消訂閱原則類別目錄</span><span class="sxs-lookup"><span data-stu-id="88172-102">Subscribe or Unsubscribe a Database  to a Policy Category</span></span>
  <span data-ttu-id="88172-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中讓資料庫訂閱或取消訂閱原則類別目錄。</span><span class="sxs-lookup"><span data-stu-id="88172-103">This topic describes how to subscribe or unsubscribe a database to a policy category.in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="88172-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="88172-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="88172-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="88172-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="88172-106">安全性</span><span class="sxs-lookup"><span data-stu-id="88172-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="88172-107">**若要使用下列方法讓資料庫訂閱或取消訂閱原則類別目錄：**</span><span class="sxs-lookup"><span data-stu-id="88172-107">**To subscribe or unsubscribe a database to a policy category., using:**</span></span>  
  
     [<span data-ttu-id="88172-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="88172-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="88172-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="88172-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="88172-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="88172-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="88172-111">Security</span><span class="sxs-lookup"><span data-stu-id="88172-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="88172-112">權限</span><span class="sxs-lookup"><span data-stu-id="88172-112">Permissions</span></span>  
 <span data-ttu-id="88172-113">需要 db_owner 固定資料庫角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="88172-113">Requires membership in the db_owner fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="88172-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="88172-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-subscribe-or-unsubscribe-a-database-to-a-policy-category"></a><span data-ttu-id="88172-115">若要讓資料庫訂閱或取消訂閱原則類別目錄</span><span class="sxs-lookup"><span data-stu-id="88172-115">To subscribe or unsubscribe a database to a policy category</span></span>  
  
1.  <span data-ttu-id="88172-116">在 **[物件總管]** 中，按一下加號展開伺服器，此伺服器包含要管理其中類別目錄訂閱的資料庫。</span><span class="sxs-lookup"><span data-stu-id="88172-116">In **Object Explorer**, click the plus sign to expand the server that contains the database wherein you want to manage category subscriptions.</span></span>  
  
2.  <span data-ttu-id="88172-117">按一下加號展開 **[資料庫]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="88172-117">Click the plus sign to expand the **Databases** folder.</span></span>  
  
3.  <span data-ttu-id="88172-118">以滑鼠右鍵按一下要管理其中類別目錄訂閱的資料庫，指向 [原則]\*\*\*\* 並選取 [類別目錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="88172-118">Right-click the database wherein you want to manage category subscriptions, point to **Policies**, and select **Categories**</span></span>  
  
     <span data-ttu-id="88172-119">**[類別目錄]** 對話方塊有下列選項：</span><span class="sxs-lookup"><span data-stu-id="88172-119">The following options are available in the **Categories** dialog box:</span></span>  
  
     <span data-ttu-id="88172-120">展開資料行</span><span class="sxs-lookup"><span data-stu-id="88172-120">Expand column</span></span>  
     <span data-ttu-id="88172-121">按一下此選項可展開原則類別目錄。</span><span class="sxs-lookup"><span data-stu-id="88172-121">Click to expand a policy category.</span></span> <span data-ttu-id="88172-122">這個清單會列出此類別目錄中所包含的所有原則。</span><span class="sxs-lookup"><span data-stu-id="88172-122">This lists all the policies that are included in the category.</span></span>  
  
     <span data-ttu-id="88172-123">**名稱**</span><span class="sxs-lookup"><span data-stu-id="88172-123">**Name**</span></span>  
     <span data-ttu-id="88172-124">原則類別目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="88172-124">The name of the policy category.</span></span>  
  
     <span data-ttu-id="88172-125">**訂閱**</span><span class="sxs-lookup"><span data-stu-id="88172-125">**Subscribed**</span></span>  
     <span data-ttu-id="88172-126">指出目標是否已訂閱原則類別目錄。</span><span class="sxs-lookup"><span data-stu-id="88172-126">Indicates whether the target has subscribed to the policy category.</span></span> <span data-ttu-id="88172-127">如果已停用此核取方塊，會針對 **[託管資料庫訂閱]** 設定原則類別目錄。</span><span class="sxs-lookup"><span data-stu-id="88172-127">If this check box is disabled, the policy category is set for **Mandate Database Subscriptions**.</span></span> <span data-ttu-id="88172-128">這表示，原則類別目錄會套用到伺服器上的所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="88172-128">This means that the policy category applies to all databases on the server.</span></span>  
  
     <span data-ttu-id="88172-129">**原則**</span><span class="sxs-lookup"><span data-stu-id="88172-129">**Policy**</span></span>  
     <span data-ttu-id="88172-130">當原則群組展開時，會顯示原則類別目錄中的原則。</span><span class="sxs-lookup"><span data-stu-id="88172-130">When policy groups are expanded, displays the policies in the policy category.</span></span>  
  
     <span data-ttu-id="88172-131">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="88172-131">**Enabled**</span></span>  
     <span data-ttu-id="88172-132">指出原則已啟用或停用。</span><span class="sxs-lookup"><span data-stu-id="88172-132">Indicates whether the policies are enabled or disabled.</span></span>  
  
     <span data-ttu-id="88172-133">**執行模式**</span><span class="sxs-lookup"><span data-stu-id="88172-133">**Execution Mode**</span></span>  
     <span data-ttu-id="88172-134">顯示原則的執行模式。</span><span class="sxs-lookup"><span data-stu-id="88172-134">Displays the execution mode of the policy.</span></span>  
  
     <span data-ttu-id="88172-135">**History**</span><span class="sxs-lookup"><span data-stu-id="88172-135">**History**</span></span>  
     <span data-ttu-id="88172-136">按一下 [檢視記錄] 超連結可開啟記錄檔檢視器，以查看原則記錄。</span><span class="sxs-lookup"><span data-stu-id="88172-136">Click the View History hyperlink to open the Log File Viewer to see the policy history.</span></span>  
  
4.  <span data-ttu-id="88172-137">若要訂閱原則式管理類別目錄，請選取 [已訂閱]\*\*\*\* 資料行下類別目錄的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="88172-137">To subscribe to a Policy-Based Management category, select the category's check box under the **Subscribed** column.</span></span> <span data-ttu-id="88172-138">若要取消訂閱類別目錄，請清除核取方塊。</span><span class="sxs-lookup"><span data-stu-id="88172-138">To unsubscribe from a category, clear the check box.</span></span>  
  
5.  <span data-ttu-id="88172-139">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="88172-139">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="88172-140">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="88172-140">Using Transact-SQL</span></span>  
  
#### <a name="to-subscribe-a-database-to-a-policy-category"></a><span data-ttu-id="88172-141">若要讓資料庫訂閱原則類別目錄</span><span class="sxs-lookup"><span data-stu-id="88172-141">To subscribe a database to a policy category</span></span>  
  
1.  <span data-ttu-id="88172-142">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="88172-142">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="88172-143">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="88172-143">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="88172-144">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="88172-144">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    -- Adds a subscription to the 'Finance' policy category for the AdventureWorks2012 database.  
    EXEC sys.sp_syspolicy_subscribe_to_policy_category @policy_category = N'Finance';  
    GO  
    ```  
  
 <span data-ttu-id="88172-145">如需詳細資訊，請參閱 [sp_syspolicy_subscribe_to_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-subscribe-to-policy-category-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="88172-145">For more information, see [sp_syspolicy_subscribe_to_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-subscribe-to-policy-category-transact-sql).</span></span>  
  
#### <a name="to-unsubscribe-a-database-to-a-policy-category"></a><span data-ttu-id="88172-146">若要讓資料庫取消訂閱原則類別目錄</span><span class="sxs-lookup"><span data-stu-id="88172-146">To unsubscribe a database to a policy category</span></span>  
  
1.  <span data-ttu-id="88172-147">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="88172-147">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="88172-148">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="88172-148">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="88172-149">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="88172-149">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    -- Deletes a subscription to the 'Finance' policy category for the AdventureWorks2012 database.  
    EXEC sys.sp_syspolicy_unsubscribe_from_policy_category @policy_category = N'Finance';  
    GO  
    ```  
  
 <span data-ttu-id="88172-150">如需詳細資訊，請參閱 [sp_syspolicy_unsubscribe_from_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="88172-150">For more information, see [sp_syspolicy_unsubscribe_from_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql).</span></span>  
  
  
