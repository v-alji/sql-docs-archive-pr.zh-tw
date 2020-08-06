---
title: 檢視或修改原則式管理原則的屬性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, modify policies
- Policy-Based Management, view policies
ms.assetid: ba805504-5db5-4731-a8da-a0e89cb20c37
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: da2226d3049a84098eb8e561635161f73b71ab10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593984"
---
# <a name="view-or-modify-the-properties-of-a-policy-based-management-policy"></a><span data-ttu-id="6e29b-102">檢視或修改原則式管理原則的屬性</span><span class="sxs-lookup"><span data-stu-id="6e29b-102">View or Modify the Properties of a Policy-Based Management Policy</span></span>
  <span data-ttu-id="6e29b-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視或修改原則式管理原則的屬性。</span><span class="sxs-lookup"><span data-stu-id="6e29b-103">This topic describes how to view or modify a Policy-Based Management policy's properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="6e29b-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="6e29b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6e29b-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="6e29b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6e29b-106">安全性</span><span class="sxs-lookup"><span data-stu-id="6e29b-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6e29b-107">**若要使用下列項目來檢視或修改原則的屬性：**</span><span class="sxs-lookup"><span data-stu-id="6e29b-107">**To view or modify a policy's properties, using:**</span></span>  
  
     [<span data-ttu-id="6e29b-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6e29b-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6e29b-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6e29b-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6e29b-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="6e29b-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6e29b-111">Security</span><span class="sxs-lookup"><span data-stu-id="6e29b-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6e29b-112">權限</span><span class="sxs-lookup"><span data-stu-id="6e29b-112">Permissions</span></span>  
 <span data-ttu-id="6e29b-113">需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="6e29b-113">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6e29b-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6e29b-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-properties-of-all-policies-on-an-object"></a><span data-ttu-id="6e29b-115">若要檢視物件之所有原則的屬性</span><span class="sxs-lookup"><span data-stu-id="6e29b-115">To view the properties of all policies on an object</span></span>  
  
1.  <span data-ttu-id="6e29b-116">在物件總管中，以滑鼠右鍵按一下伺服器、伺服器物件、資料庫或資料庫物件，指向 [原則]\*\*\*\*，然後選取 [檢視]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6e29b-116">In Object Explorer, right-click a server, server object, database, or database object, point to **Policies** and select **View**.</span></span> <span data-ttu-id="6e29b-117">如需有關 [檢視原則 - _物件名稱_]\*\*\*\* 對話方塊中可用選項的詳細資訊，請參閱[檢視原則對話方塊](view-policies-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="6e29b-117">For more information on the available options in the **View Policies -**_object_name_ dialog box, see [View Policies Dialog Box](view-policies-dialog-box.md).</span></span>  
  
2.  <span data-ttu-id="6e29b-118">完成後，請按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="6e29b-118">When finished, click **Close**.</span></span>  
  
#### <a name="to-view-or-modify-a-specific-policys-properties"></a><span data-ttu-id="6e29b-119">若要檢視或修改特定原則的屬性</span><span class="sxs-lookup"><span data-stu-id="6e29b-119">To view or modify a specific policy's properties</span></span>  
  
1.  <span data-ttu-id="6e29b-120">在 **物件總管**中，按一下加號，展開包含您想要檢視或修改之原則式管理原則的伺服器。</span><span class="sxs-lookup"><span data-stu-id="6e29b-120">In **Object Explorer**, click the plus sign to expand the server that contains the Policy-Based Management policy that you want to view or modify.</span></span>  
  
2.  <span data-ttu-id="6e29b-121">按一下加號展開 **[管理]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6e29b-121">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="6e29b-122">按一下加號展開 **[原則管理]**。</span><span class="sxs-lookup"><span data-stu-id="6e29b-122">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="6e29b-123">按一下加號展開 **[原則]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6e29b-123">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="6e29b-124">以滑鼠右鍵按一下您想要檢視或修改的原則，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6e29b-124">Right-click the policy that you want to view or modify and select **Properties**.</span></span> <span data-ttu-id="6e29b-125">如需有關 [開啟原則 - _原則名稱_]\*\*\*\* 對話方塊中可用選項的詳細資訊，請參閱[建立新原則或開啟原則對話方塊，一般頁面](../../integration-services/general-page-of-integration-services-designers-options.md)和[建立新原則或開啟原則對話方塊，描述頁面](create-new-policy-or-open-policy-dialog-box-description-page.md)。</span><span class="sxs-lookup"><span data-stu-id="6e29b-125">For more information on the available options in the **Open Policy -**_policy_name_ dialog box, see [Create New Policy or Open Policy Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md) and [Create New Policy or Open Policy Dialog Box, Description Page](create-new-policy-or-open-policy-dialog-box-description-page.md).</span></span>  
  
6.  <span data-ttu-id="6e29b-126">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="6e29b-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6e29b-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6e29b-127">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-policys-properties"></a><span data-ttu-id="6e29b-128">若要檢視原則的屬性</span><span class="sxs-lookup"><span data-stu-id="6e29b-128">To view a policy's properties</span></span>  
  
1.  <span data-ttu-id="6e29b-129">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6e29b-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6e29b-130">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="6e29b-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6e29b-131">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="6e29b-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       execution_mode,  
       description,  
       is_enabled,  
       job_id  
    FROM syspolicy_policies;  
    GO  
    ```  
  
 <span data-ttu-id="6e29b-132">如需詳細資訊，請參閱 [syspolicy_policies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syspolicy-policies-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6e29b-132">For more information, see [syspolicy_policies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syspolicy-policies-transact-sql).</span></span>  
  
  
