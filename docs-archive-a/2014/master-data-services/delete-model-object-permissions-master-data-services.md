---
title: 刪除模型物件權限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting model object permissions [Master Data Services]
- permissions [Master Data Services], deleting model object permissions
- models [Master Data Services], deleting object permissions
ms.assetid: 859c5952-f600-4940-8064-1afd13f7f6dc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 98da869476e597d76a83b0b86cc9e6e4274a25e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699952"
---
# <a name="delete-model-object-permissions-master-data-services"></a><span data-ttu-id="33316-102">刪除模型物件權限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="33316-102">Delete Model Object Permissions (Master Data Services)</span></span>
  <span data-ttu-id="33316-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，刪除模型物件權限，移除所做的任何指派。</span><span class="sxs-lookup"><span data-stu-id="33316-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete model object permissions to remove any assignments that have been made.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="33316-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="33316-104">Prerequisites</span></span>  
 <span data-ttu-id="33316-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="33316-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="33316-106">您必須擁有存取 **[使用者及群組的權限]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="33316-106">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="33316-107">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="33316-107">You must be a model administrator.</span></span> <span data-ttu-id="33316-108">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="33316-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-model-object-permissions"></a><span data-ttu-id="33316-109">若要刪除模型物件權限</span><span class="sxs-lookup"><span data-stu-id="33316-109">To delete model object permissions</span></span>  
  
1.  <span data-ttu-id="33316-110">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[使用者及群組的權限]**。</span><span class="sxs-lookup"><span data-stu-id="33316-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="33316-111">在 **[使用者]** 或 **[群組]** 頁面上，選取要編輯之使用者或群組的資料列。</span><span class="sxs-lookup"><span data-stu-id="33316-111">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="33316-112">按一下 **[編輯選取的使用者]**。</span><span class="sxs-lookup"><span data-stu-id="33316-112">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="33316-113">按一下 **[模型]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="33316-113">Click the **Models** tab.</span></span>  
  
5.  <span data-ttu-id="33316-114">(選擇性) 從 **[模型]** 清單中選取模型。</span><span class="sxs-lookup"><span data-stu-id="33316-114">Optionally, select a model from the **Model** list.</span></span>  
  
6.  <span data-ttu-id="33316-115">在 [**模型許可權摘要**] 窗格中，選取您想要刪除之許可權的資料列。</span><span class="sxs-lookup"><span data-stu-id="33316-115">In the **Model Permission Summary** pane, select the row for the permission that you want to delete.</span></span>  
  
7.  <span data-ttu-id="33316-116">按一下 [**刪除選取的許可權**]。</span><span class="sxs-lookup"><span data-stu-id="33316-116">Click **Delete selected permission**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="33316-117">如果權限繼承自群組，則無法從使用者移除權限。</span><span class="sxs-lookup"><span data-stu-id="33316-117">You cannot remove a permission from a user if the permission is inherited from a group.</span></span> <span data-ttu-id="33316-118">您必須改為從群組移除權限。</span><span class="sxs-lookup"><span data-stu-id="33316-118">You must remove the permission from the group instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33316-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33316-119">See Also</span></span>  
 <span data-ttu-id="33316-120">[模型物件使用權限 &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="33316-120">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="33316-121">指派模型物件權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="33316-121">Assign Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)  
  
  
