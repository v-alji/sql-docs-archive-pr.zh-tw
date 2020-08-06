---
title: 使用 SSMS (SSAS 表格式) 管理角色 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 652faac0-1cfc-438b-8119-2f4b090a2381
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4ee34d5e75d5d4ce3679d46d29af3215852d2bbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687208"
---
# <a name="manage-roles-by-using-ssms-ssas-tabular"></a><span data-ttu-id="807bc-102">使用 SSMS 管理角色 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="807bc-102">Manage Roles by using SSMS (SSAS Tabular)</span></span>
  <span data-ttu-id="807bc-103">對於部署的表格式模型，可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]建立、編輯和管理角色。</span><span class="sxs-lookup"><span data-stu-id="807bc-103">You can create, edit, and manage roles for a deployed tabular model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="807bc-104">本主題的工作：</span><span class="sxs-lookup"><span data-stu-id="807bc-104">Tasks in this topic:</span></span>  
  
-   [<span data-ttu-id="807bc-105">若要建立新角色</span><span class="sxs-lookup"><span data-stu-id="807bc-105">To create a new role</span></span>](#bkmk_new_role)  
  
-   [<span data-ttu-id="807bc-106">若要複製角色</span><span class="sxs-lookup"><span data-stu-id="807bc-106">To copy a role</span></span>](#bkmk_copy_role)  
  
-   [<span data-ttu-id="807bc-107">若要編輯角色</span><span class="sxs-lookup"><span data-stu-id="807bc-107">To edit a role</span></span>](#bkmk_edit_role)  
  
-   [<span data-ttu-id="807bc-108">若要刪除角色</span><span class="sxs-lookup"><span data-stu-id="807bc-108">To delete a role</span></span>](#bkmk_deletet_role)  
  
> [!CAUTION]  
>  <span data-ttu-id="807bc-109">透過在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 中使用 [角色管理員] 定義的角色重新部署表格式模型專案，將會覆寫已部署表格式模型中定義的角色。</span><span class="sxs-lookup"><span data-stu-id="807bc-109">Re-deploying a tabular model project with roles defined by using Role Manager in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] will overwrite roles defined in a deployed tabular model.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="807bc-110">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中開啟模型專案時使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 管理表格式模型工作空間資料庫可能會造成 Model.bim 檔案損毀。</span><span class="sxs-lookup"><span data-stu-id="807bc-110">Using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to manage a tabular model workspace database while the model project is open in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] may cause the Model.bim file to become corrupted.</span></span> <span data-ttu-id="807bc-111">當您針對表格式模型工作空間資料庫建立及管理角色時，請在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中使用 [角色管理員]。</span><span class="sxs-lookup"><span data-stu-id="807bc-111">When creating and managing roles for a tabular model workspace database, use Role Manager in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
###  <a name="to-create-a-new-role"></a><a name="bkmk_new_role"></a><span data-ttu-id="807bc-112">若要建立新的角色</span><span class="sxs-lookup"><span data-stu-id="807bc-112">To create a new role</span></span>  
  
1.  <span data-ttu-id="807bc-113">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，展開您要建立新角色的表格式模型資料庫，然後以滑鼠右鍵按一下 [角色]\*\*\*\*，再按一下 [新增角色]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="807bc-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the tabular model database for which you want to create a new role, then right click on **Roles**, and then click **New Role**.</span></span>  
  
2.  <span data-ttu-id="807bc-114">在 [建立角色]\*\*\*\* 對話方塊的 [選取頁面] 視窗中，按一下 [一般]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="807bc-114">In the **Create Role** dialog box, in the Select a page window, click **General**.</span></span>  
  
3.  <span data-ttu-id="807bc-115">在 [一般設定] 視窗中，於 [名稱]\*\*\*\* 欄位內輸入角色的名稱。</span><span class="sxs-lookup"><span data-stu-id="807bc-115">In the general settings window, in the **Name** field, type a name for the role.</span></span>  
  
     <span data-ttu-id="807bc-116">依預設，每個新角色的預設角色名稱是以累加的方式進行編號。</span><span class="sxs-lookup"><span data-stu-id="807bc-116">By default, the name of the default role will be incrementally numbered for each new role.</span></span> <span data-ttu-id="807bc-117">建議您輸入清楚識別成員類型的名稱，例如「財務經理」或「人力資源專員」。</span><span class="sxs-lookup"><span data-stu-id="807bc-117">It is recommended you type a name that clearly identifies the member type, for example, Finance Managers or Human Resources Specialists.</span></span>  
  
4.  <span data-ttu-id="807bc-118">在 [為這個角色設定資料庫權限]\*\*\*\* 中，選取下列其中一個權限選項：</span><span class="sxs-lookup"><span data-stu-id="807bc-118">In **Set the database permissions for this role**, select one of the following permissions options:</span></span>  
  
    |<span data-ttu-id="807bc-119">權限</span><span class="sxs-lookup"><span data-stu-id="807bc-119">Permission</span></span>|<span data-ttu-id="807bc-120">描述</span><span class="sxs-lookup"><span data-stu-id="807bc-120">Description</span></span>|  
    |----------------|-----------------|  
    |<span data-ttu-id="807bc-121">**完整控制權 (管理員)**</span><span class="sxs-lookup"><span data-stu-id="807bc-121">**Full control (Administrator)**</span></span>|<span data-ttu-id="807bc-122">成員可以對模型結構描述進行修改，也可以檢視所有資料。</span><span class="sxs-lookup"><span data-stu-id="807bc-122">Members can make modifications to the model schema and can view all data.</span></span>|  
    |<span data-ttu-id="807bc-123">**處理資料庫**</span><span class="sxs-lookup"><span data-stu-id="807bc-123">**Process database**</span></span>|<span data-ttu-id="807bc-124">成員可以執行「處理」和「全部處理」作業。</span><span class="sxs-lookup"><span data-stu-id="807bc-124">Members can run Process and Process All operations.</span></span> <span data-ttu-id="807bc-125">無法修改模型結構描述，也無法檢視資料。</span><span class="sxs-lookup"><span data-stu-id="807bc-125">Cannot modify the model schema and cannot view data.</span></span>|  
    |<span data-ttu-id="807bc-126">**讀取**</span><span class="sxs-lookup"><span data-stu-id="807bc-126">**Read**</span></span>|<span data-ttu-id="807bc-127">成員可以檢視資料 (根據資料列篩選)，但無法對模型結構描述進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="807bc-127">Members are allowed to view data (based on row filters) but cannot make any changes to the model schema.</span></span>|  
  
5.  <span data-ttu-id="807bc-128">在 [建立角色]\*\*\*\* 對話方塊的 [選取頁面] 視窗中，按一下 [成員資格]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="807bc-128">In the **Create Role** dialog box, in the Select a page window, click **Membership**.</span></span>  
  
6.  <span data-ttu-id="807bc-129">在成員資格設定視窗中，按一下 [加入]\*\*\*\*，然後在 [選取使用者或群組]\*\*\*\* 對話方塊中，加入您要當做成員加入的 Windows 使用者或群組。</span><span class="sxs-lookup"><span data-stu-id="807bc-129">In the membership settings window, click **Add**, and then in the **Select Users or Groups** dialog box, add the Windows users or groups you want to add as members.</span></span>  
  
7.  <span data-ttu-id="807bc-130">如果您建立的角色具有「讀取」權限，您可以使用 DAX 公式加入任何資料表的資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="807bc-130">If the role you are creating has Read permissions, you can add row filters for any table using a DAX formula.</span></span> <span data-ttu-id="807bc-131">若要加入資料列篩選，請在 [**角色屬性- \<rolename> \*\* ] 對話方塊的 [**選取頁面**] 中，按一下 [資料**列篩選\*\*]。</span><span class="sxs-lookup"><span data-stu-id="807bc-131">To add row filters, in the **Role Properties - \<rolename>** dialog box, in **Select a page**, click on **Row Filters**.</span></span>  
  
8.  <span data-ttu-id="807bc-132">在 [資料列篩選] 視窗中，選取資料表，然後按一下 [ **Dax 篩選**] 欄位，然後在 [ **dax 篩選 \<tablename> 條件-** ] 欄位中輸入 DAX 公式。</span><span class="sxs-lookup"><span data-stu-id="807bc-132">In the row filters window, select a table, then click on the **DAX Filter** field, and then in the **DAX Filter - \<tablename>** field, type a DAX formula.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="807bc-133">[DAX 篩選準則] \<tablename> 欄位不包含 [自動完成查詢編輯器] 或 [插入函數] 功能。</span><span class="sxs-lookup"><span data-stu-id="807bc-133">The DAX Filter - \<tablename> field does not contain an AutoComplete query editor or insert function feature.</span></span> <span data-ttu-id="807bc-134">若要在撰寫 DAX 公式時使用自動完成功能，您必須在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中使用 DAX 公式編輯器。</span><span class="sxs-lookup"><span data-stu-id="807bc-134">To use AutoComplete when writing a DAX formula, you must use a DAX formula editor in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
9. <span data-ttu-id="807bc-135">按一下 [確定]\*\*\*\*，儲存角色。</span><span class="sxs-lookup"><span data-stu-id="807bc-135">Click **Ok** to save the role.</span></span>  
  
###  <a name="to-copy-a-role"></a><a name="bkmk_copy_role"></a> <span data-ttu-id="807bc-136">若要複製角色</span><span class="sxs-lookup"><span data-stu-id="807bc-136">To copy a role</span></span>  
  
1.  <span data-ttu-id="807bc-137">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，展開包含您要複製之角色的表格式模型資料庫，然後展開 [角色]\*\*\*\*，再以滑鼠右鍵按一下此角色，然後按一下 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="807bc-137">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the tabular model database that contains the role you want to copy, then expand **Roles**, then right click on the role, and then click **Duplicate**.</span></span>  
  
###  <a name="to-edit-a-role"></a><a name="bkmk_edit_role"></a><span data-ttu-id="807bc-138">編輯角色</span><span class="sxs-lookup"><span data-stu-id="807bc-138">To edit a role</span></span>  
  
-   <span data-ttu-id="807bc-139">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，展開包含您要編輯之角色的表格式模型資料庫，然後展開 [角色]\*\*\*\*，再以滑鼠右鍵按一下此角色，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="807bc-139">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the tabular model database that contains the role you want to edit, then expand **Roles**, then right click on the role, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="807bc-140">在 [**角色屬性** \<rolename> ] 對話方塊中，您可以變更許可權、加入或移除成員，以及加入/編輯資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="807bc-140">In the **Role Properties** \<rolename> dialog box, you can change permissions, add or remove members, and add/edit row filters.</span></span>  
  
###  <a name="to-delete-a-role"></a><a name="bkmk_deletet_role"></a><span data-ttu-id="807bc-141">若要刪除角色</span><span class="sxs-lookup"><span data-stu-id="807bc-141">To delete a role</span></span>  
  
-   <span data-ttu-id="807bc-142">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，展開包含您要刪除之角色的表格式模型資料庫，然後展開 [角色]\*\*\*\*，再以滑鼠右鍵按一下此角色，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="807bc-142">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the tabular model database that contains the role you want to delete, then expand **Roles**, then right click on the role, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="807bc-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="807bc-143">See Also</span></span>  
 [<span data-ttu-id="807bc-144">角色 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="807bc-144">Roles &#40;SSAS Tabular&#41;</span></span>](roles-ssas-tabular.md)  
  
  
