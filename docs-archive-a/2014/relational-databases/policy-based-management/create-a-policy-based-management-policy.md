---
title: 建立原則式管理原則 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, creating policies
ms.assetid: b28bf963-89f9-4941-b6c1-6004fec347f1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e76b4dce17e00bae5e8ca4fcf071868c0641c786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596671"
---
# <a name="create-a-policy-based-management-policy"></a><span data-ttu-id="4a224-102">建立原則式管理原則</span><span class="sxs-lookup"><span data-stu-id="4a224-102">Create a Policy-Based Management Policy</span></span>
  <span data-ttu-id="4a224-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中建立原則式管理原則。</span><span class="sxs-lookup"><span data-stu-id="4a224-103">This topic describes how to create a Policy-Based Management policy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="4a224-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="4a224-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4a224-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="4a224-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4a224-106">安全性</span><span class="sxs-lookup"><span data-stu-id="4a224-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4a224-107">**若要使用下列項目來建立原則：**</span><span class="sxs-lookup"><span data-stu-id="4a224-107">**To create a policy, using:**</span></span>  
  
     [<span data-ttu-id="4a224-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4a224-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4a224-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="4a224-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4a224-110">Security</span><span class="sxs-lookup"><span data-stu-id="4a224-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4a224-111">權限</span><span class="sxs-lookup"><span data-stu-id="4a224-111">Permissions</span></span>  
 <span data-ttu-id="4a224-112">需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="4a224-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4a224-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4a224-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-policy"></a><span data-ttu-id="4a224-114">若要建立原則</span><span class="sxs-lookup"><span data-stu-id="4a224-114">To create a policy</span></span>  
  
1.  <span data-ttu-id="4a224-115">在物件總管  中，按一下加號，展開您想要建立新原則式管理原則的伺服器。</span><span class="sxs-lookup"><span data-stu-id="4a224-115">In **Object Explorer**, click the plus sign to expand the server where you want to create a new a Policy-Based Management policy.</span></span>  
  
2.  <span data-ttu-id="4a224-116">按一下加號展開 **[管理]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4a224-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="4a224-117">按一下加號展開 **[原則管理]** 。</span><span class="sxs-lookup"><span data-stu-id="4a224-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="4a224-118">以滑鼠右鍵按一下 [原則]  資料夾，然後選取 [新增原則]  。</span><span class="sxs-lookup"><span data-stu-id="4a224-118">Right-click the **Policies** folder and select **New Policy**.</span></span>  
  
5.  <span data-ttu-id="4a224-119">在 **[建立新原則]** 對話方塊的 **[名稱]** 方塊中，輸入新原則的名稱。</span><span class="sxs-lookup"><span data-stu-id="4a224-119">In the **Create New Policy** dialog box, in the **Name** box, type the name of the new policy.</span></span>  
  
6.  <span data-ttu-id="4a224-120">如果您想要在建立原則時立即啟用原則，請選取 **[已啟用]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="4a224-120">If you want the policy to be enabled as soon as it is created, select the **Enabled** check box.</span></span> <span data-ttu-id="4a224-121">如果評估模式為 **[視需要]** ，就無法使用 **[已啟用]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="4a224-121">If the evaluation mode is **On demand**, the **Enabled** check box is not available.</span></span>  
  
7.  <span data-ttu-id="4a224-122">在 **[檢查條件]** 清單中，選取其中一個現有的條件，或選取 **[新增條件]** 。</span><span class="sxs-lookup"><span data-stu-id="4a224-122">In the **Check condition** list, select one of the existing conditions, or select **New Condition**.</span></span> <span data-ttu-id="4a224-123">若要編輯條件，請選取該條件，然後按一下省略符號 (...)  。如需詳細資訊，請參閱[建立新的原則式管理條件](create-a-new-policy-based-management-condition.md)或[檢視或修改原則式管理條件的屬性](view-or-modify-the-properties-of-a-policy-based-management-condition.md)。</span><span class="sxs-lookup"><span data-stu-id="4a224-123">To edit a condition, select the condition and then click the ellipsis (**...**). For more information, see [Create a New Policy-Based Management Condition](create-a-new-policy-based-management-condition.md) or [View or Modify the Properties of a Policy-Based Management Condition](view-or-modify-the-properties-of-a-policy-based-management-condition.md).</span></span>  
  
8.  <span data-ttu-id="4a224-124">在 **[針對目標]** 方塊中，針對此原則選取一個或多個目標類型。</span><span class="sxs-lookup"><span data-stu-id="4a224-124">In the **Against targets** box, select one or more target types for this policy.</span></span> <span data-ttu-id="4a224-125">某些條件和 Facet 只能套用至特定目標類型。</span><span class="sxs-lookup"><span data-stu-id="4a224-125">Some conditions and facets can only be applied to certain types of targets.</span></span> <span data-ttu-id="4a224-126">可用的目標集會顯示在相關聯的方塊中。</span><span class="sxs-lookup"><span data-stu-id="4a224-126">The available target sets appear in the associated box.</span></span> <span data-ttu-id="4a224-127">展開 **[全部]** ，針對某些目標類型選取篩選條件。</span><span class="sxs-lookup"><span data-stu-id="4a224-127">Expand **Every** to select a filtering condition for some types of the targets.</span></span> <span data-ttu-id="4a224-128">如果此方塊中沒有出現任何目標，這表示檢查條件的範圍設定為伺服器層級。</span><span class="sxs-lookup"><span data-stu-id="4a224-128">If no targets appear in this box, the check condition is scoped at the server level.</span></span>  
  
9. <span data-ttu-id="4a224-129">在 **[評估模式]** 方塊中，選取這個原則的行為方式。</span><span class="sxs-lookup"><span data-stu-id="4a224-129">In the **Evaluation Mode** box, select how this policy will behave.</span></span> <span data-ttu-id="4a224-130">不同的條件可以有不同的有效評估模式。</span><span class="sxs-lookup"><span data-stu-id="4a224-130">Different conditions can have different valid evaluation modes.</span></span> <span data-ttu-id="4a224-131">如需哪些評估模式有效的詳細資訊，請參閱 [使用原則式管理來管理伺服器](administer-servers-by-using-policy-based-management.md)。</span><span class="sxs-lookup"><span data-stu-id="4a224-131">For more information about which evaluation modes are valid, see [Administer Servers by Using Policy-Based Management](administer-servers-by-using-policy-based-management.md).</span></span>  
  
10. <span data-ttu-id="4a224-132">如果此原則將依排程來評估，請將評估模式設定為 **[按排程時間]** ，然後按一下 **[挑選]** 選取排程，或是按一下 **[新增]** 建立新的排程。</span><span class="sxs-lookup"><span data-stu-id="4a224-132">If the policy will be evaluated on a schedule, set the evaluation mode to **On schedule**, and then click **Pick** to select a schedule, or click **New** to create a new schedule.</span></span>  
  
11. <span data-ttu-id="4a224-133">若要將此原則限制為目標類型的子集，請在 **[伺服器限制]** 方塊中，選取限制條件或建立新的條件。</span><span class="sxs-lookup"><span data-stu-id="4a224-133">To limit the policy to subset of the target types, in the **Server restriction** box, select from limiting conditions or create a new condition.</span></span>  
  
     <span data-ttu-id="4a224-134">如需有關 **[建立新原則]** 對話方塊可用之選項的詳細資訊，請參閱＜ [建立新原則或開啟原則對話方塊，一般頁面](../../integration-services/general-page-of-integration-services-designers-options.md) ＞或＜ [建立新原則或開啟原則對話方塊，描述頁面](create-new-policy-or-open-policy-dialog-box-description-page.md)＞。</span><span class="sxs-lookup"><span data-stu-id="4a224-134">For more information on the available options in the **Create New Policy** dialog box, see [Create New Policy or Open Policy Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md) or [Create New Policy or Open Policy Dialog Box, Description Page](create-new-policy-or-open-policy-dialog-box-description-page.md).</span></span>  
  
12. <span data-ttu-id="4a224-135">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4a224-135">When finished click **OK**.</span></span>  
  
  
