---
title: 建立和管理 (SSAS 表格式) 的角色 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.rolemanager.f1
- sql12.asvs.bidtoolset.roledb.f1
ms.assetid: e23d27a8-e968-4082-9dbe-963fc724b5d9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 335e0e311d97ea452449cd0c5d6550f6dbcca4f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592297"
---
# <a name="create-and-manage-roles-ssas-tabular"></a><span data-ttu-id="89040-102">建立及管理角色 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="89040-102">Create and Manage Roles (SSAS Tabular)</span></span>
  <span data-ttu-id="89040-103">表格式模型中的角色定義模型的成員權限。</span><span class="sxs-lookup"><span data-stu-id="89040-103">Roles, in tabular models, define member permissions for a model.</span></span> <span data-ttu-id="89040-104">您可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的 [角色管理員] 對話方塊來定義模型專案的角色。</span><span class="sxs-lookup"><span data-stu-id="89040-104">Roles are defined for a model project by using the Role Manager dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="89040-105">部署模型之後，資料庫管理員即可使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]管理角色。</span><span class="sxs-lookup"><span data-stu-id="89040-105">When a model is deployed, database administrators can manage roles by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="89040-106">此主題中的工作描述如何使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的 [角色管理員] 對話方塊，在模型撰寫期間建立及管理角色。</span><span class="sxs-lookup"><span data-stu-id="89040-106">The tasks in this topic describe how to create and manage roles during model authoring by using the Role Manager dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="89040-107">如需在已部署的模型資料庫中管理角色的相關資訊，請參閱[表格式模型角色 &#40;SSAS 表格式&#41;](roles-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="89040-107">For information about managing roles in a deployed model database, see [Tabular Model Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="89040-108">工作</span><span class="sxs-lookup"><span data-stu-id="89040-108">Tasks</span></span>  
 <span data-ttu-id="89040-109">若要建立、編輯、複製及刪除角色，您要使用 [角色管理員]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="89040-109">To create, edit, copy, and delete roles, you will use the **Role Manager** dialog box.</span></span> <span data-ttu-id="89040-110">若要檢視 [角色管理員]\*\*\*\* 對話方塊，請在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 中按一下 [模型]\*\*\*\* 功能表，然後按一下 [角色管理員]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="89040-110">To view the **Role Manager** dialog box, in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Role Manager**.</span></span>  
  
###  <a name="to-create-a-new-role"></a><a name="bkmk_new_role"></a><span data-ttu-id="89040-111">若要建立新的角色</span><span class="sxs-lookup"><span data-stu-id="89040-111">To create a new role</span></span>  
  
1.  <span data-ttu-id="89040-112">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 中，按一下 [模型]\*\*\*\* 功能表，然後按一下 [角色管理員]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="89040-112">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Role Manager**.</span></span>  
  
2.  <span data-ttu-id="89040-113">在 [角色管理員]\*\*\*\* 對話方塊中，按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="89040-113">In the **Role Manager** dialog box, click **New**.</span></span>  
  
     <span data-ttu-id="89040-114">反白顯示的新角色即會加入至 [角色] 清單中。</span><span class="sxs-lookup"><span data-stu-id="89040-114">A new highlighted role is added to the Roles list.</span></span>  
  
3.  <span data-ttu-id="89040-115">在 [角色]\*\*\*\* 清單的 [名稱]\*\*\*\* 欄位中，輸入角色的名稱。</span><span class="sxs-lookup"><span data-stu-id="89040-115">In the **Roles** list, in the **Name** field, type a name for the role.</span></span>  
  
     <span data-ttu-id="89040-116">依預設，每個新角色的預設角色名稱是以累加的方式進行編號。</span><span class="sxs-lookup"><span data-stu-id="89040-116">By default, the name of the default role will be incrementally numbered for each new role.</span></span> <span data-ttu-id="89040-117">建議您輸入清楚識別成員類型的名稱，例如「財務經理」或「人力資源專員」。</span><span class="sxs-lookup"><span data-stu-id="89040-117">It is recommended you type a name that clearly identifies the member type, for example, Finance Managers or Human Resources Specialists.</span></span>  
  
4.  <span data-ttu-id="89040-118">在 [權限]\*\*\*\* 欄位中，按一下向下箭頭，然後選取下列其中一個權限類型：</span><span class="sxs-lookup"><span data-stu-id="89040-118">In the **Permissions** field, click the down arrow and then select one of the following permission types:</span></span>  
  
    |<span data-ttu-id="89040-119">權限</span><span class="sxs-lookup"><span data-stu-id="89040-119">Permission</span></span>|<span data-ttu-id="89040-120">描述</span><span class="sxs-lookup"><span data-stu-id="89040-120">Description</span></span>|  
    |----------------|-----------------|  
    |<span data-ttu-id="89040-121">**None**</span><span class="sxs-lookup"><span data-stu-id="89040-121">**None**</span></span>|<span data-ttu-id="89040-122">成員無法對模型結構描述進行任何修改，也無法查詢資料。</span><span class="sxs-lookup"><span data-stu-id="89040-122">Members cannot make any modifications to the model schema and cannot query data.</span></span>|  
    |<span data-ttu-id="89040-123">**讀取**</span><span class="sxs-lookup"><span data-stu-id="89040-123">**Read**</span></span>|<span data-ttu-id="89040-124">成員可以查詢資料 (根據資料列篩選)，但無法對模型結構描述進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="89040-124">Members are allowed to query data (based on row filters) but cannot make any changes to the model schema.</span></span>|  
    |<span data-ttu-id="89040-125">**讀取和處理**</span><span class="sxs-lookup"><span data-stu-id="89040-125">**Read and Process**</span></span>|<span data-ttu-id="89040-126">成員可以查詢資料 (根據資料列層級篩選) 並執行「處理」和「全部處理」作業，但無法對模型結構描述進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="89040-126">Members are allowed to query data (based on row-level filters) and run Process and Process All operations, but cannot make any changes to the model schema.</span></span>|  
    |<span data-ttu-id="89040-127">**處理程序**</span><span class="sxs-lookup"><span data-stu-id="89040-127">**Process**</span></span>|<span data-ttu-id="89040-128">成員可以執行「處理」和「全部處理」作業。</span><span class="sxs-lookup"><span data-stu-id="89040-128">Members can run Process and Process All operations.</span></span> <span data-ttu-id="89040-129">無法修改模型結構描述，也無法查詢資料。</span><span class="sxs-lookup"><span data-stu-id="89040-129">Cannot modify the model schema and cannot query data.</span></span>|  
    |<span data-ttu-id="89040-130">**系統管理員**</span><span class="sxs-lookup"><span data-stu-id="89040-130">**Administrator**</span></span>|<span data-ttu-id="89040-131">成員可以對模型結構描述進行修改，也可以查詢所有資料。</span><span class="sxs-lookup"><span data-stu-id="89040-131">Members can make modifications to the model schema and can query all data.</span></span>|  
  
5.  <span data-ttu-id="89040-132">若要輸入角色的描述，請按一下 [描述]\*\*\*\* 欄位，然後輸入描述。</span><span class="sxs-lookup"><span data-stu-id="89040-132">To enter a description for the role, click the **Description** field, and then type a description.</span></span>  
  
6.  <span data-ttu-id="89040-133">如果您建立的角色具有「讀取」或「讀取和處理」權限，您可以使用 DAX 公式加入資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="89040-133">If the role you are creating has Read or Read and Process permission, you can add row filters using a DAX formula.</span></span> <span data-ttu-id="89040-134">若要加入資料列篩選，請按一下 [資料列篩選]\*\*\*\* 索引標籤，選取資料表，然後按一下 [DAX 篩選]\*\*\*\* 欄位並輸入 DAX 公式。</span><span class="sxs-lookup"><span data-stu-id="89040-134">To add row filters, click the **Row Filters** tab, then select a table, then click the **DAX Filter** field, and then type a DAX formula.</span></span>  
  
7.  <span data-ttu-id="89040-135">若要將成員加入至角色，請按一下 [成員]\*\*\*\* 索引標籤，然後按一下 [加入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="89040-135">To add members to the role, click the **Members** tab, and then click **Add**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="89040-136">您也可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，將角色成員加入至已部署的模型。</span><span class="sxs-lookup"><span data-stu-id="89040-136">Role members can also be added to a deployed model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="89040-137">如需詳細資訊，請參閱[使用 SSMS 管理角色 &#40;SSAS 表格式&#41;](manage-roles-by-using-ssms-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="89040-137">For more information, see [Manage Roles by using SSMS &#40;SSAS Tabular&#41;](manage-roles-by-using-ssms-ssas-tabular.md).</span></span>  
  
8.  <span data-ttu-id="89040-138">在 [選取使用者或群組]\*\*\*\* 對話方塊中，輸入 Windows 使用者或 Windows 群組物件做為成員。</span><span class="sxs-lookup"><span data-stu-id="89040-138">In the **Select Users or Groups** dialog box, enter Windows user or Windows group objects as members.</span></span>  
  
9. <span data-ttu-id="89040-139">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="89040-139">Click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89040-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89040-140">See Also</span></span>  
 <span data-ttu-id="89040-141">[&#40;SSAS 表格式&#41;的角色](roles-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="89040-141">[Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md) </span></span>  
 <span data-ttu-id="89040-142">[SSAS 表格式 &#40;的觀點&#41;](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="89040-142">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 <span data-ttu-id="89040-143">[在 Excel 中分析 &#40;SSAS 表格式&#41;](analyze-in-excel-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="89040-143">[Analyze in Excel &#40;SSAS Tabular&#41;](analyze-in-excel-ssas-tabular.md) </span></span>  
 <span data-ttu-id="89040-144">[USERNAME 函數 &#40;DAX&#41;](/dax/username-function-dax) </span><span class="sxs-lookup"><span data-stu-id="89040-144">[USERNAME Function &#40;DAX&#41;](/dax/username-function-dax) </span></span>  
 [<span data-ttu-id="89040-145">&#40;DAX&#41;的 CUSTOMDATA 函數</span><span class="sxs-lookup"><span data-stu-id="89040-145">CUSTOMDATA Function &#40;DAX&#41;</span></span>](/dax/customdata-function-dax)  
  
  
