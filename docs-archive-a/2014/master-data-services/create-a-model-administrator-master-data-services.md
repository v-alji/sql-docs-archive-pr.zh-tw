---
title: 建立模型管理員 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], creating
ms.assetid: dae17afc-3b39-490e-b51f-2d8da26d429e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 24efc3961e6ed5b9f41b2321dfcc4fbf16632270
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606957"
---
# <a name="create-a-model-administrator-master-data-services"></a><span data-ttu-id="07cd1-102">建立模型管理員 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="07cd1-102">Create a Model Administrator (Master Data Services)</span></span>
  <span data-ttu-id="07cd1-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]當您希望群組或使用者擁有一或多個模型中所有物件的 [**更新**] 許可權時，可以在中建立模型管理員。</span><span class="sxs-lookup"><span data-stu-id="07cd1-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a model administrator when you want a group or user to have **Update** permission to all objects in one or more models.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="07cd1-104">若要簡化管理，請建立 Windows 或本機群組，並將它設定為模型管理員。</span><span class="sxs-lookup"><span data-stu-id="07cd1-104">To simplify administration, create a Windows or local group and configure it as a model administrator.</span></span> <span data-ttu-id="07cd1-105">然後不需存取 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]，您就可以在群組中加入及移除使用者。</span><span class="sxs-lookup"><span data-stu-id="07cd1-105">You can then add and remove users from the group without accessing [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="07cd1-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="07cd1-106">Prerequisites</span></span>  
 <span data-ttu-id="07cd1-107">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="07cd1-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="07cd1-108">您必須擁有存取 [使用者及群組的權限]\*\*\*\* 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="07cd1-108">You must have permission to access the **User and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="07cd1-109">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="07cd1-109">You must be a model administrator.</span></span> <span data-ttu-id="07cd1-110">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="07cd1-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-model-administrator"></a><span data-ttu-id="07cd1-111">若要建立模型管理員</span><span class="sxs-lookup"><span data-stu-id="07cd1-111">To create a model administrator</span></span>  
  
1.  <span data-ttu-id="07cd1-112">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[使用者及群組的權限]**。</span><span class="sxs-lookup"><span data-stu-id="07cd1-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="07cd1-113">在 **[使用者]** 或 **[群組]** 頁面上，選取要編輯之使用者或群組的資料列。</span><span class="sxs-lookup"><span data-stu-id="07cd1-113">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="07cd1-114">按一下 **[編輯選取的使用者]**。</span><span class="sxs-lookup"><span data-stu-id="07cd1-114">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="07cd1-115">按一下 **[模型]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="07cd1-115">Click the **Models** tab.</span></span>  
  
5.  <span data-ttu-id="07cd1-116">(選擇性) 從 **[模型]** 清單中選取模型。</span><span class="sxs-lookup"><span data-stu-id="07cd1-116">Optionally, select a model from the **Model** list.</span></span>  
  
6.  <span data-ttu-id="07cd1-117">按一下 **[編輯]** 。</span><span class="sxs-lookup"><span data-stu-id="07cd1-117">Click **Edit**.</span></span>  
  
7.  <span data-ttu-id="07cd1-118">按一下您要授與權限的模型。</span><span class="sxs-lookup"><span data-stu-id="07cd1-118">Click the model you want to grant permission to.</span></span>  
  
8.  <span data-ttu-id="07cd1-119">從功能表中，選取 [**更新**]。</span><span class="sxs-lookup"><span data-stu-id="07cd1-119">From the menu, select **Update**.</span></span>  
  
9. <span data-ttu-id="07cd1-120">針對您希望群組或使用者成為其管理員的每個模型，完成步驟 7 和 8。</span><span class="sxs-lookup"><span data-stu-id="07cd1-120">Complete steps 7 and 8 for each model you want the group or user to be an administrator for.</span></span>  
  
10. <span data-ttu-id="07cd1-121">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="07cd1-121">Click **Save**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07cd1-122">備註</span><span class="sxs-lookup"><span data-stu-id="07cd1-122">Remarks</span></span>  
 <span data-ttu-id="07cd1-123">請不要指派模型物件或階層成員的任何其他權限。</span><span class="sxs-lookup"><span data-stu-id="07cd1-123">Do not assign any other permissions to model objects or hierarchy members.</span></span> <span data-ttu-id="07cd1-124">如果您這樣做，使用者就不再是系統管理員，也無法在**Explorer**以外的任何功能區域中查看模型。</span><span class="sxs-lookup"><span data-stu-id="07cd1-124">If you do, the user is no longer an administrator and cannot view the model in any functional area other than **Explorer**.</span></span>  
  
 <span data-ttu-id="07cd1-125">有一個例外狀況：如果使用者在 [階層**成員**] 索引標籤上，將 [**更新**] 許可權指派給階層**根**，則使用者仍然會被視為模型管理員。</span><span class="sxs-lookup"><span data-stu-id="07cd1-125">There is one exception: if the user has **Update** permission assigned to a hierarchy **Root** on the **Hierarchy Members** tab, the user is still considered a model administrator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07cd1-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07cd1-126">See Also</span></span>  
 <span data-ttu-id="07cd1-127">[系統管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="07cd1-127">[Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md) </span></span>  
 <span data-ttu-id="07cd1-128">[指派模型物件使用權限 &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="07cd1-128">[Assign Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="07cd1-129">[指派階層成員許可權 &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="07cd1-129">[Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="07cd1-130">[模型物件使用權限 &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="07cd1-130">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="07cd1-131">階層成員權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="07cd1-131">Hierarchy Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
