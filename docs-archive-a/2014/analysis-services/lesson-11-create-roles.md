---
title: 第12課：建立角色 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 984face4-00fc-46d3-8ae1-9755bf737bdf
author: minewiskan
ms.author: owend
ms.openlocfilehash: 962cd19726a5404de81e20a2209b25b9cc277e21
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584783"
---
# <a name="lesson-12-create-roles"></a><span data-ttu-id="d0a93-102">第 12 課：建立角色</span><span class="sxs-lookup"><span data-stu-id="d0a93-102">Lesson 12: Create Roles</span></span>
  <span data-ttu-id="d0a93-103">在這一課，您將建立角色。</span><span class="sxs-lookup"><span data-stu-id="d0a93-103">In this lesson, you will create roles.</span></span> <span data-ttu-id="d0a93-104">角色會藉由僅限身為角色成員的 Windows 使用者存取的方式，提供模型資料庫物件和資料安全性。</span><span class="sxs-lookup"><span data-stu-id="d0a93-104">Roles provide model database object and data security by limiting access to only those Windows users which are role members.</span></span> <span data-ttu-id="d0a93-105">每個角色都定義有單一權限︰「無」、「讀取」、「讀取和處理」、「處理」或「系統管理員」。</span><span class="sxs-lookup"><span data-stu-id="d0a93-105">Each role is defined with a single permission: None, Read, Read and Process, Process, or Administrator.</span></span> <span data-ttu-id="d0a93-106">您可以使用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中的 [角色管理員] 對話方塊，在模型撰寫期間定義角色。</span><span class="sxs-lookup"><span data-stu-id="d0a93-106">Roles can be defined during model authoring by using the Role Manager dialog box in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="d0a93-107">部署模型之後，您可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]管理角色。</span><span class="sxs-lookup"><span data-stu-id="d0a93-107">After a model has been deployed, you can manage roles by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="d0a93-108">如需詳細資訊，請參閱[角色 &#40;SSAS 表格式&#41;](tabular-models/roles-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="d0a93-108">To learn more, see [Roles &#40;SSAS Tabular&#41;](tabular-models/roles-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d0a93-109">建立角色不是完成本教學課程的必要工作。</span><span class="sxs-lookup"><span data-stu-id="d0a93-109">Creating roles is not necessary to complete this tutorial.</span></span> <span data-ttu-id="d0a93-110">根據預設，您目前登入的帳戶將擁有模型的「系統管理員」權限。</span><span class="sxs-lookup"><span data-stu-id="d0a93-110">By default, the account you are currently logged in with will have Administrator privileges on the model.</span></span> <span data-ttu-id="d0a93-111">不過，為了讓組織中的其他使用者能夠使用報表用戶端應用程式瀏覽模型，您必須至少建立一個具有「讀取」權限的角色，並將這些使用者加入為成員。</span><span class="sxs-lookup"><span data-stu-id="d0a93-111">However, to allow other users in your organization to browse the model by using a reporting client application, you must create at least one role with Read permissions and add those users as members.</span></span>  
  
 <span data-ttu-id="d0a93-112">您將建立三個角色︰</span><span class="sxs-lookup"><span data-stu-id="d0a93-112">You will create three roles:</span></span>  
  
-   <span data-ttu-id="d0a93-113">銷售經理-此角色可包含組織中您想要對所有模型物件和資料具有讀取權限的使用者。</span><span class="sxs-lookup"><span data-stu-id="d0a93-113">Sales Manager - This role can include users in your organization for which you want to have Read permission to all model objects and data.</span></span>  
  
-   <span data-ttu-id="d0a93-114">美國銷售分析師-此角色可包含組織中的使用者，您只希望能夠流覽美國 (美國) 的銷售相關資料。</span><span class="sxs-lookup"><span data-stu-id="d0a93-114">Sales Analyst US - This role can include users in your organization for which you want only to be able to browse data related to sales in the US (United States).</span></span> <span data-ttu-id="d0a93-115">對於此角色，您將使用 DAX 公式來定義「資料列篩選條件」\*\*，以限制成員只能瀏覽美國方面的資料。</span><span class="sxs-lookup"><span data-stu-id="d0a93-115">For this role, you will use a DAX formula to define a *Row Filter*, which restricts members to browse data only for the United States.</span></span>  
  
-   <span data-ttu-id="d0a93-116">系統管理員-此角色可包含您想要擁有系統管理員許可權的使用者，這允許無限制的存取權和許可權，在 model 資料庫上執行管理工作。</span><span class="sxs-lookup"><span data-stu-id="d0a93-116">Administrator - This role can include users for which you want to have Administrator permission, which allows unlimited access and permissions to perform administrative tasks on the model database.</span></span>  
  
 <span data-ttu-id="d0a93-117">因為組織中的 Windows 使用者和群組帳戶都是獨一無二，您可以將特定組織中的帳戶新增至成員。</span><span class="sxs-lookup"><span data-stu-id="d0a93-117">Because Windows user and group accounts in your organization are unique, you can add accounts from your particular organization to members.</span></span> <span data-ttu-id="d0a93-118">不過，針對此教學課程，您也可以將成員留空。</span><span class="sxs-lookup"><span data-stu-id="d0a93-118">However, for this tutorial, you can also leave the members blank.</span></span> <span data-ttu-id="d0a93-119">您稍後仍然能夠在第 12 課：「在 Excel 中進行分析」中測試每個角色的效用。</span><span class="sxs-lookup"><span data-stu-id="d0a93-119">You will still be able to test the effect of each role later in Lesson 12: Analyze in Excel.</span></span>  
  
 <span data-ttu-id="d0a93-120">完成本課程的估計時間： **15 分鐘**</span><span class="sxs-lookup"><span data-stu-id="d0a93-120">Estimated time to complete this lesson: **15 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d0a93-121">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="d0a93-121">Prerequisites</span></span>  
 <span data-ttu-id="d0a93-122">本主題是表格式模型教學課程的一部分，請依序完成。</span><span class="sxs-lookup"><span data-stu-id="d0a93-122">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="d0a93-123">在執行本課中的工作之前，您應已完成上一課： [第 11 課：建立資料分割](lesson-10-create-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="d0a93-123">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 11: Create Partitions](lesson-10-create-partitions.md).</span></span>  
  
## <a name="create-roles"></a><span data-ttu-id="d0a93-124">建立角色</span><span class="sxs-lookup"><span data-stu-id="d0a93-124">Create Roles</span></span>  
  
#### <a name="to-create-a-sales-manager-user-role"></a><span data-ttu-id="d0a93-125">建立「銷售經理」使用者角色</span><span class="sxs-lookup"><span data-stu-id="d0a93-125">To create a Sales Manager user role</span></span>  
  
1.  <span data-ttu-id="d0a93-126">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，按一下 [模型]\*\*\*\* 功能表，然後按一下 [角色]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0a93-126">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Roles**.</span></span>  
  
2.  <span data-ttu-id="d0a93-127">在 [角色管理員]\*\*\*\* 對話方塊中，按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0a93-127">In the **Role Manager** dialog box, click **New**.</span></span>  
  
     <span data-ttu-id="d0a93-128">清單中會新增 [無] 權限的新角色。</span><span class="sxs-lookup"><span data-stu-id="d0a93-128">A new role with the None permission is added to the list.</span></span>  
  
3.  <span data-ttu-id="d0a93-129">按一下 [新增] 角色，然後在 [**名稱**] 資料行中，將角色重新命名為 `Internet Sales Manager` 。</span><span class="sxs-lookup"><span data-stu-id="d0a93-129">Click on the new role, and then in the **Name** column, rename the role to `Internet Sales Manager`.</span></span>  
  
4.  <span data-ttu-id="d0a93-130">在 [權限]\*\*\*\* 資料行中，按一下下拉式清單，然後選取 [讀取]\*\*\*\* 權限。</span><span class="sxs-lookup"><span data-stu-id="d0a93-130">In the **Permissions** column, click the dropdown list, and then select the **Read** permission.</span></span>  
  
5.  <span data-ttu-id="d0a93-131">選擇性：按一下 [成員]\*\*\*\* 索引標籤，然後按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0a93-131">Optional: Click on the **Members** tab, and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="d0a93-132">在 [選取使用者或群組]\*\*\*\* 對話方塊中，輸入您想從組織中加入此角色的 Windows 使用者或群組。</span><span class="sxs-lookup"><span data-stu-id="d0a93-132">In the **Select Users or Groups** dialog box, enter the Windows users or groups from your organization you want to include in the role.</span></span>  
  
7.  <span data-ttu-id="d0a93-133">確認您的選擇，然後按一下 **[確定]**</span><span class="sxs-lookup"><span data-stu-id="d0a93-133">Verify your selections, and then click **OK**</span></span>  
  
#### <a name="to-create-a-sales-analyst-us-user-role"></a><span data-ttu-id="d0a93-134">建立「美國銷售分析師」使用者角色</span><span class="sxs-lookup"><span data-stu-id="d0a93-134">To create a Sales Analyst US user role</span></span>  
  
1.  <span data-ttu-id="d0a93-135">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，按一下 [模型]\*\*\*\* 功能表，然後按一下 [角色]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0a93-135">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Roles**.</span></span>  
  
2.  <span data-ttu-id="d0a93-136">在 [角色管理員]\*\*\*\* 對話方塊中，按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0a93-136">In the **Role Manager** dialog box, click **New**.</span></span>  
  
     <span data-ttu-id="d0a93-137">清單中會新增 [無] 權限的新角色。</span><span class="sxs-lookup"><span data-stu-id="d0a93-137">A new role with the None permission is added to the list.</span></span>  
  
3.  <span data-ttu-id="d0a93-138">按一下 [新增] 角色，然後在 [**名稱**] 資料行中，將角色重新命名為 `Internet Sales US` 。</span><span class="sxs-lookup"><span data-stu-id="d0a93-138">Click on the new role, and then in the **Name** column, rename the role to `Internet Sales US`.</span></span>  
  
4.  <span data-ttu-id="d0a93-139">在 [權限]\*\*\*\* 資料行中，按一下下拉式清單，然後選取 [讀取]\*\*\*\* 權限。</span><span class="sxs-lookup"><span data-stu-id="d0a93-139">In the **Permissions** column, click the dropdown list, and then select the **Read** permission.</span></span>  
  
5.  <span data-ttu-id="d0a93-140">按一下 [資料列篩選] 索引標籤，然後僅針對 [Geography]\*\*\*\* 資料表，在 [DAX 篩選] 資料行中輸入下列公式：</span><span class="sxs-lookup"><span data-stu-id="d0a93-140">Click on the Row Filters tab, and then for the **Geography** table only, in the DAX Filter column, type the following formula:</span></span>  
  
     `=Geography[Country Region Code] = "US"`  
  
     <span data-ttu-id="d0a93-141">「資料列篩選條件」公式必須解析成布林值 (TRUE/FALSE)。</span><span class="sxs-lookup"><span data-stu-id="d0a93-141">A Row Filter formula must resolve to a Boolean (TRUE/FALSE) value.</span></span> <span data-ttu-id="d0a93-142">在此公式中，您指定只有國家地區代碼值為 "US" 的資料列才會顯示給使用者。</span><span class="sxs-lookup"><span data-stu-id="d0a93-142">With this formula, you are specifying that only rows with the Country Region Code value of "US" be visible to the user.</span></span>  
  
     <span data-ttu-id="d0a93-143">完成建立公式時，按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="d0a93-143">When you have finished building the formula, press ENTER.</span></span>  
  
6.  <span data-ttu-id="d0a93-144">選擇性：按一下 [成員]\*\*\*\* 索引標籤，然後按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0a93-144">Optional: Click on the **Members** tab, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="d0a93-145">在 [選取使用者或群組]\*\*\*\* 對話方塊中，輸入您想從組織中加入此角色的 Windows 使用者或群組。</span><span class="sxs-lookup"><span data-stu-id="d0a93-145">In the **Select Users or Groups** dialog box, enter the Windows users or groups from your organization you want to include in the role.</span></span>  
  
8.  <span data-ttu-id="d0a93-146">確認您的選擇，然後按一下 **[確定]**</span><span class="sxs-lookup"><span data-stu-id="d0a93-146">Verify your selections, and then click **OK**</span></span>  
  
#### <a name="to-create-an-administrator-role"></a><span data-ttu-id="d0a93-147">若要建立 Administrator 角色</span><span class="sxs-lookup"><span data-stu-id="d0a93-147">To create an Administrator role</span></span>  
  
1.  <span data-ttu-id="d0a93-148">在 [角色管理員]\*\*\*\* 對話方塊中，按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0a93-148">In the **Role Manager** dialog box, click **New**.</span></span>  
  
2.  <span data-ttu-id="d0a93-149">按一下 [新增] 角色，然後在 [**名稱**] 資料行中，將角色重新命名為 `Internet Sales Administrator` 。</span><span class="sxs-lookup"><span data-stu-id="d0a93-149">Click on the new role, and then in the **Name** column, rename the role to `Internet Sales Administrator`.</span></span>  
  
3.  <span data-ttu-id="d0a93-150">按一下 [權限]\*\*\*\* 資料行中的下拉式清單，然後選取 [系統管理員]\*\*\*\* 權限。</span><span class="sxs-lookup"><span data-stu-id="d0a93-150">In the **Permissions** column, click the dropdown list, and then select the **Administrator** permission.</span></span>  
  
4.  <span data-ttu-id="d0a93-151">按一下 [成員]\*\*\*\* 索引標籤，然後按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0a93-151">Click on the **Members** tab, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="d0a93-152">選擇性：在 [選取使用者或群組]\*\*\*\* 對話方塊中，從組織輸入要包含在角色中的 Windows 使用者或群組。</span><span class="sxs-lookup"><span data-stu-id="d0a93-152">Optional: In the **Select Users or Groups** dialog box, enter the Windows users or groups from your organization you want to include in the role.</span></span>  
  
6.  <span data-ttu-id="d0a93-153">確認您的選擇，然後按一下 **[確定]**</span><span class="sxs-lookup"><span data-stu-id="d0a93-153">Verify your selections, and then click **OK**</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d0a93-154">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d0a93-154">Next Steps</span></span>  
 <span data-ttu-id="d0a93-155">若要繼續進行本教學課程，請前往下一課： [第 13 課：在 Excel 中進行分析](lesson-12-analyze-in-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="d0a93-155">To continue this tutorial, go to the next lesson: Lesson: [Lesson 13: Analyze in Excel](lesson-12-analyze-in-excel.md).</span></span>  
  
  
