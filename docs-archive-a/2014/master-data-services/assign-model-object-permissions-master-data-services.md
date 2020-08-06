---
title: 指派模型物件權限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], assigning object permissions
- permissions [Master Data Services], assigning model object permissions
ms.assetid: 4b80148d-2318-415c-9479-28c240e48bcd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 92ac8ef3ac63b7128c4cbb7e9305ee6bd56ca010
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596765"
---
# <a name="assign-model-object-permissions-master-data-services"></a><span data-ttu-id="3a137-102">指派模型物件權限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3a137-102">Assign Model Object Permissions (Master Data Services)</span></span>
  <span data-ttu-id="3a137-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，當您需要提供使用者或群組對於 **之** [總管] [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]功能區域中資料的存取權時，或當您需要將使用者或群組設為管理員時，請指派模型物件的權限。</span><span class="sxs-lookup"><span data-stu-id="3a137-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], assign permissions to model objects when you need to give a user or group access to data in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], or when you need to make a user or group an administrator.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a137-104">當您指派某個模型的權限時，會明確拒絕所有其他模型的權限。</span><span class="sxs-lookup"><span data-stu-id="3a137-104">When you assign permission to a model, permission to all other models is implicitly denied.</span></span> <span data-ttu-id="3a137-105">如果未指派模型物件權限，使用者或群組就無法存取 **[總管]** 中的資料。</span><span class="sxs-lookup"><span data-stu-id="3a137-105">If you do not assign model object permissions, the user or group cannot access any data in **Explorer**.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3a137-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="3a137-106">Prerequisites</span></span>  
 <span data-ttu-id="3a137-107">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="3a137-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="3a137-108">您必須擁有存取 **[使用者及群組的權限]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="3a137-108">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="3a137-109">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="3a137-109">You must be a model administrator.</span></span> <span data-ttu-id="3a137-110">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3a137-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-assign-model-object-permissions"></a><span data-ttu-id="3a137-111">若要指派模型物件權限</span><span class="sxs-lookup"><span data-stu-id="3a137-111">To assign model object permissions</span></span>  
  
1.  <span data-ttu-id="3a137-112">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[使用者及群組的權限]**。</span><span class="sxs-lookup"><span data-stu-id="3a137-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="3a137-113">在 **[使用者]** 或 **[群組]** 頁面上，選取要編輯之使用者或群組的資料列。</span><span class="sxs-lookup"><span data-stu-id="3a137-113">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="3a137-114">按一下 **[編輯選取的使用者]**。</span><span class="sxs-lookup"><span data-stu-id="3a137-114">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="3a137-115">按一下 **[模型]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3a137-115">Click the **Models** tab.</span></span>  
  
5.  <span data-ttu-id="3a137-116">(選擇性) 從 **[模型]** 清單中選取模型。</span><span class="sxs-lookup"><span data-stu-id="3a137-116">Optionally, select a model from the **Model** list.</span></span>  
  
6.  <span data-ttu-id="3a137-117">按一下 **[編輯]** 。</span><span class="sxs-lookup"><span data-stu-id="3a137-117">Click **Edit**.</span></span>  
  
7.  <span data-ttu-id="3a137-118">展開樹狀結構，然後按一下要指派權限的模型物件。</span><span class="sxs-lookup"><span data-stu-id="3a137-118">Expand the tree, and click the model object you want to assign permissions to.</span></span>  
  
8.  <span data-ttu-id="3a137-119">從功能表中，選取 [**唯讀**]、[**更新**] 或 [**拒絕**]。</span><span class="sxs-lookup"><span data-stu-id="3a137-119">From the menu, select **Read-only**, **Update**, or **Deny**.</span></span>  
  
9. <span data-ttu-id="3a137-120">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="3a137-120">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3a137-121">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3a137-121">Next Steps</span></span>  
  
-   <span data-ttu-id="3a137-122">(選擇性) [指派階層成員權限 &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="3a137-122">(Optional) [Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a137-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a137-123">See Also</span></span>  
 <span data-ttu-id="3a137-124">[刪除模型物件使用權限 &#40;Master Data Services&#41;](../../2014/master-data-services/delete-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3a137-124">[Delete Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/delete-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="3a137-125">[模型物件使用權限 &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3a137-125">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="3a137-126">建立模型管理員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3a137-126">Create a Model Administrator &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-model-administrator-master-data-services.md)  
  
  
