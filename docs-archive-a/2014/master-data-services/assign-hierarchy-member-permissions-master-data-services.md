---
title: 指派階層成員權限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], assigning member permissions
- members [Master Data Services], assigning permissions
ms.assetid: e1b8b46a-7cd1-4a7d-9345-dd7df081e145
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4a1602f9fe351f826b63d4447f90dcf02a10f49e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596781"
---
# <a name="assign-hierarchy-member-permissions-master-data-services"></a><span data-ttu-id="4480b-102">指派階層成員權限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="4480b-102">Assign Hierarchy Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="4480b-103">指派階層成員的權限，提供使用者或群組存取權，以便在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 的總管\*\*\*\* 功能區域中檢視資料。</span><span class="sxs-lookup"><span data-stu-id="4480b-103">Assign permissions to hierarchy members to give users or groups access to view data in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
 <span data-ttu-id="4480b-104">階層成員權限為選擇性。</span><span class="sxs-lookup"><span data-stu-id="4480b-104">Hierarchy member permissions are optional.</span></span> <span data-ttu-id="4480b-105">它們為必要的模型物件權限提供更細微的控制。</span><span class="sxs-lookup"><span data-stu-id="4480b-105">They provide added granularity to model object permissions, which are required.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4480b-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="4480b-106">Prerequisites</span></span>  
 <span data-ttu-id="4480b-107">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="4480b-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="4480b-108">您必須擁有存取 **[使用者及群組的權限]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="4480b-108">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="4480b-109">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="4480b-109">You must be a model administrator.</span></span> <span data-ttu-id="4480b-110">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="4480b-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-assign-hierarchy-member-permissions"></a><span data-ttu-id="4480b-111">若要指派階層成員權限</span><span class="sxs-lookup"><span data-stu-id="4480b-111">To assign hierarchy member permissions</span></span>  
  
1.  <span data-ttu-id="4480b-112">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[使用者及群組的權限]**。</span><span class="sxs-lookup"><span data-stu-id="4480b-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="4480b-113">在 **[使用者]** 或 **[群組]** 頁面上，選取要編輯之使用者或群組的資料列。</span><span class="sxs-lookup"><span data-stu-id="4480b-113">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="4480b-114">按一下 **[編輯選取的使用者]**。</span><span class="sxs-lookup"><span data-stu-id="4480b-114">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="4480b-115">按一下 [階層成員]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="4480b-115">Click the **Hierarchy Members** tab.</span></span>  
  
5.  <span data-ttu-id="4480b-116">從 **[模型]** 清單中選取模型。</span><span class="sxs-lookup"><span data-stu-id="4480b-116">From the **Model** list, select a model.</span></span>  
  
6.  <span data-ttu-id="4480b-117">從 **[版本]** 清單中選取版本。</span><span class="sxs-lookup"><span data-stu-id="4480b-117">From the **Version** list, select a version.</span></span>  
  
7.  <span data-ttu-id="4480b-118">從 [階層]\*\*\*\* 清單中選取階層。</span><span class="sxs-lookup"><span data-stu-id="4480b-118">From the **Hierarchy** list, select a hierarchy.</span></span>  
  
8.  <span data-ttu-id="4480b-119">按一下 **[編輯]** 。</span><span class="sxs-lookup"><span data-stu-id="4480b-119">Click **Edit**.</span></span>  
  
9. <span data-ttu-id="4480b-120">展開樹狀結構，然後按一下要指派權限的階層節點。</span><span class="sxs-lookup"><span data-stu-id="4480b-120">Expand the tree, and click the hierarchy node you want to assign permissions to.</span></span>  
  
10. <span data-ttu-id="4480b-121">從功能表中，選取 [**唯讀**]、[**更新**] 或 [**拒絕**]。</span><span class="sxs-lookup"><span data-stu-id="4480b-121">From the menu, select **Read-only**, **Update**, or **Deny**.</span></span>  
  
11. <span data-ttu-id="4480b-122">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="4480b-122">Click **Save**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4480b-123">階層成員權限不會立即生效。</span><span class="sxs-lookup"><span data-stu-id="4480b-123">Hierarchy member permissions do not take effect immediately.</span></span> <span data-ttu-id="4480b-124">如需詳細資訊，請參閱[立即套用成員權限 &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="4480b-124">See [Immediately Apply Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md) for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4480b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4480b-125">See Also</span></span>  
 <span data-ttu-id="4480b-126">[刪除階層成員許可權 &#40;Master Data Services&#41;](../../2014/master-data-services/delete-hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="4480b-126">[Delete Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/delete-hierarchy-member-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="4480b-127">[指派模型物件使用權限 &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="4480b-127">[Assign Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="4480b-128">階層成員權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4480b-128">Hierarchy Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
