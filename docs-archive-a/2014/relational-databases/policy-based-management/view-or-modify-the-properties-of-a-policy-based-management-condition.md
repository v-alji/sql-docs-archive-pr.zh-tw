---
title: 檢視或修改原則式管理條件的屬性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view policy conditions
- Policy-Based Management, modify policy conditions
ms.assetid: 890d7384-8444-4767-bb6f-f5debb155747
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 08baec48bd13445ef56ea6a29520d23ebaf683b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593983"
---
# <a name="view-or-modify-the-properties-of-a-policy-based-management-condition"></a><span data-ttu-id="9bfc5-102">檢視或修改原則式管理條件的屬性</span><span class="sxs-lookup"><span data-stu-id="9bfc5-102">View or Modify the Properties of a Policy-Based Management Condition</span></span>
  <span data-ttu-id="9bfc5-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視或修改原則式管理條件的屬性。</span><span class="sxs-lookup"><span data-stu-id="9bfc5-103">This topic describes how to view or modify the properties of a Policy-Based Management condition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="9bfc5-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="9bfc5-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9bfc5-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="9bfc5-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9bfc5-106">安全性</span><span class="sxs-lookup"><span data-stu-id="9bfc5-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9bfc5-107">**若要使用下列項目來檢視或修改條件的屬性：**</span><span class="sxs-lookup"><span data-stu-id="9bfc5-107">**To view or modify a condition's properties, using:**</span></span>  
  
     [<span data-ttu-id="9bfc5-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9bfc5-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9bfc5-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9bfc5-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9bfc5-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="9bfc5-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9bfc5-111">Security</span><span class="sxs-lookup"><span data-stu-id="9bfc5-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9bfc5-112">權限</span><span class="sxs-lookup"><span data-stu-id="9bfc5-112">Permissions</span></span>  
 <span data-ttu-id="9bfc5-113">需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="9bfc5-113">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9bfc5-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9bfc5-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-modify-a-conditions-properties"></a><span data-ttu-id="9bfc5-115">若要檢視或修改條件的屬性</span><span class="sxs-lookup"><span data-stu-id="9bfc5-115">To view or modify a condition's properties</span></span>  
  
1.  <span data-ttu-id="9bfc5-116">在 **[物件總管]** 中，按一下加號，展開包含您想要檢視或修改之條件的伺服器。</span><span class="sxs-lookup"><span data-stu-id="9bfc5-116">In **Object Explorer**, click the plus sign to expand the server that contains the condition that you want to view or modify.</span></span>  
  
2.  <span data-ttu-id="9bfc5-117">按一下加號展開 **[管理]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9bfc5-117">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="9bfc5-118">按一下加號展開 **[原則管理]**。</span><span class="sxs-lookup"><span data-stu-id="9bfc5-118">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="9bfc5-119">按一下加號展開 **[條件]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9bfc5-119">Click the plus sign to expand the **Conditions** folder.</span></span>  
  
5.  <span data-ttu-id="9bfc5-120">以滑鼠右鍵按一下您想要檢視或編輯的條件，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9bfc5-120">Right-click the condition that you want to view or edit and select **Properties**.</span></span> <span data-ttu-id="9bfc5-121">如需有關 [開啟條件 - _條件名稱_]\*\*\*\* 對話方塊中可用選項的詳細資訊，請參閱[建立新條件或開啟條件對話方塊，一般頁面](../../integration-services/general-page-of-integration-services-designers-options.md)、[開啟條件對話方塊，相依原則頁面](open-condition-dialog-box-dependent-policies-page.md)、[建立新條件或開啟條件對話方塊，描述頁面](create-new-condition-or-open-condition-dialog-box-description-page.md)，以及[進階編輯 &#40;條件&#41; 對話方塊](advanced-edit-condition-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="9bfc5-121">For more information on the available options in the **Open Condition -**_condition_name_ dialog box, see [Create New Condition or Open Condition Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md), [Open Condition Dialog Box, Dependent Policies Page](open-condition-dialog-box-dependent-policies-page.md), [Create New Condition or Open Condition Dialog Box, Description Page](create-new-condition-or-open-condition-dialog-box-description-page.md), and [Advanced Edit &#40;Condition&#41; Dialog Box](advanced-edit-condition-dialog-box.md).</span></span>  
  
6.  <span data-ttu-id="9bfc5-122">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="9bfc5-122">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9bfc5-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9bfc5-123">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-conditions-properties"></a><span data-ttu-id="9bfc5-124">若要檢視條件的屬性</span><span class="sxs-lookup"><span data-stu-id="9bfc5-124">To view a condition's properties</span></span>  
  
1.  <span data-ttu-id="9bfc5-125">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9bfc5-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9bfc5-126">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="9bfc5-126">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9bfc5-127">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="9bfc5-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       description,  
       facet,  
       expression,  
       is_name_condition,  
       obj_name  
    FROM syspolicy_conditions;  
    GO  
  
    ```  
  
 <span data-ttu-id="9bfc5-128">如需詳細資訊，請參閱 [syspolicy_conditions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syspolicy-conditions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9bfc5-128">For more information, see [syspolicy_conditions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syspolicy-conditions-transact-sql).</span></span>  
  
  
