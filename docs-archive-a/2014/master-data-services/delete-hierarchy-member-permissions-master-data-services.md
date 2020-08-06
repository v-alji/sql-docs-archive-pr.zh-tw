---
title: 刪除階層成員權限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting member permissions [Master Data Services]
- members [Master Data Services], deleting permissions
- permissions [Master Data Services], deleting member permissions
ms.assetid: 7f22d5e2-70c1-422c-99c2-e995a47d812a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8b6e7fbfc4379733d5cb809ce4d46d2c12d05a48
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699955"
---
# <a name="delete-hierarchy-member-permissions-master-data-services"></a><span data-ttu-id="cc762-102">刪除階層成員權限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cc762-102">Delete Hierarchy Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="cc762-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，刪除模型物件權限，移除所做的任何指派。</span><span class="sxs-lookup"><span data-stu-id="cc762-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete model object permissions to remove any assignments that have been made.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cc762-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="cc762-104">Prerequisites</span></span>  
 <span data-ttu-id="cc762-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="cc762-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="cc762-106">您必須擁有存取 **[使用者及群組的權限]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="cc762-106">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="cc762-107">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="cc762-107">You must be a model administrator.</span></span> <span data-ttu-id="cc762-108">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="cc762-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-hierarchy-member-permissions"></a><span data-ttu-id="cc762-109">若要刪除階層成員權限</span><span class="sxs-lookup"><span data-stu-id="cc762-109">To delete hierarchy member permissions</span></span>  
  
1.  <span data-ttu-id="cc762-110">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[使用者及群組的權限]**。</span><span class="sxs-lookup"><span data-stu-id="cc762-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="cc762-111">在 **[使用者]** 或 **[群組]** 頁面上，選取要編輯之使用者或群組的資料列。</span><span class="sxs-lookup"><span data-stu-id="cc762-111">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="cc762-112">按一下 **[編輯選取的使用者]**。</span><span class="sxs-lookup"><span data-stu-id="cc762-112">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="cc762-113">按一下 [階層成員]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cc762-113">Click the **Hierarchy Members** tab.</span></span>  
  
5.  <span data-ttu-id="cc762-114">從 **[模型]** 清單中選取模型。</span><span class="sxs-lookup"><span data-stu-id="cc762-114">From the **Model** list, select a model.</span></span>  
  
6.  <span data-ttu-id="cc762-115">從 **[版本]** 清單中選取版本。</span><span class="sxs-lookup"><span data-stu-id="cc762-115">From the **Version** list, select a version.</span></span>  
  
7.  <span data-ttu-id="cc762-116">在 [階層**成員許可權摘要**] 窗格中，選取您想要刪除之許可權的資料列。</span><span class="sxs-lookup"><span data-stu-id="cc762-116">In the **Hierarchy Member Permission Summary** pane, select the row for the permission that you want to delete.</span></span>  
  
8.  <span data-ttu-id="cc762-117">按一下 [**刪除選取的許可權**]。</span><span class="sxs-lookup"><span data-stu-id="cc762-117">Click **Delete selected permission**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cc762-118">如果權限繼承自群組，則無法從使用者移除權限。</span><span class="sxs-lookup"><span data-stu-id="cc762-118">You cannot remove a permission from a user if the permission is inherited from a group.</span></span> <span data-ttu-id="cc762-119">您必須改為從群組移除權限。</span><span class="sxs-lookup"><span data-stu-id="cc762-119">You must remove the permission from the group instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc762-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc762-120">See Also</span></span>  
 <span data-ttu-id="cc762-121">[階層成員許可權 &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cc762-121">[Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="cc762-122">指派階層成員權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cc762-122">Assign Hierarchy Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
  
