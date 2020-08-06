---
title: 刪除成員或集合 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], deleting
- leaf members [Master Data Services], deleting
- deleting members [Master Data Services]
- members [Master Data Services], deleting
- consolidated members [Master Data Services], deleting
ms.assetid: 519130a7-4226-4d71-9124-d2ee0ce7e5bd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9b248750c0e755c3fc9e32d45068c754e64957b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687016"
---
# <a name="delete-a-member-or-collection-master-data-services"></a><span data-ttu-id="d7cb4-102">刪除成員或集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d7cb4-102">Delete a Member or Collection (Master Data Services)</span></span>
  <span data-ttu-id="d7cb4-103">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，刪除您不再需要的成員或集合。</span><span class="sxs-lookup"><span data-stu-id="d7cb4-103">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], delete a member or collection when you no longer need it.</span></span> <span data-ttu-id="d7cb4-104">如果您要大量刪除成員，請改用暫存處理序。</span><span class="sxs-lookup"><span data-stu-id="d7cb4-104">If you want to delete members in bulk, use the staging process instead.</span></span> <span data-ttu-id="d7cb4-105">如需詳細資訊，請參閱[使用暫存進程停用或刪除成員 &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d7cb4-105">For more information, see [Deactivate or Delete Members by Using the Staging Process &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7cb4-106">如果某個成員是當做另一個成員的網域屬性值使用，您就無法刪除該成員。</span><span class="sxs-lookup"><span data-stu-id="d7cb4-106">You cannot delete a member if it is used as a domain-based attribute value for another member.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d7cb4-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="d7cb4-107">Prerequisites</span></span>  
 <span data-ttu-id="d7cb4-108">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="d7cb4-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d7cb4-109">您必須擁有存取 [ **Explorer** ] 功能區域的許可權。</span><span class="sxs-lookup"><span data-stu-id="d7cb4-109">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="d7cb4-110">針對成員，您至少必須擁有要從中刪除成員的分葉模型物件的 [**更新**] 許可權。</span><span class="sxs-lookup"><span data-stu-id="d7cb4-110">For members, you must have a minimum of **Update** permission to the leaf model object you are deleting a member from.</span></span>  
  
-   <span data-ttu-id="d7cb4-111">針對集合，您必須至少擁有分頁集合物件 **更新** 權限，才能將其刪除。</span><span class="sxs-lookup"><span data-stu-id="d7cb4-111">For collections, you must have a minimum of **Update** permission to the leaf collection object you are deleting.</span></span>  
  
### <a name="to-delete-a-member-or-collection"></a><span data-ttu-id="d7cb4-112">若要刪除成員或集合</span><span class="sxs-lookup"><span data-stu-id="d7cb4-112">To delete a member or collection</span></span>  
  
1.  <span data-ttu-id="d7cb4-113">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 首頁上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="d7cb4-113">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="d7cb4-114">從 **[版本]** 清單中選取版本。</span><span class="sxs-lookup"><span data-stu-id="d7cb4-114">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="d7cb4-115">按一下 **[總管]**。</span><span class="sxs-lookup"><span data-stu-id="d7cb4-115">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="d7cb4-116">若要刪除：</span><span class="sxs-lookup"><span data-stu-id="d7cb4-116">To delete:</span></span>  
  
    -   <span data-ttu-id="d7cb4-117">分葉成員，請從功能表列指向 [實體]\*\*\*\*，然後按一下包含該成員的實體名稱。</span><span class="sxs-lookup"><span data-stu-id="d7cb4-117">A leaf member, from the menu bar, point to **Entities** and click the name of the entity that contains the member.</span></span>  
  
    -   <span data-ttu-id="d7cb4-118">合併成員，請從功能表列指向 [階層]\*\*\*\*，然後按一下包含該成員的階層名稱。</span><span class="sxs-lookup"><span data-stu-id="d7cb4-118">A consolidated member, from the menu bar, point to **Hierarchies** and click the name of the hierarchy that contains the member.</span></span> <span data-ttu-id="d7cb4-119">然後按一下階層中包含此成員的節點。</span><span class="sxs-lookup"><span data-stu-id="d7cb4-119">Then click the node in the hierarchy that contains the member.</span></span>  
  
    -   <span data-ttu-id="d7cb4-120">集合，請從功能表列指向 [集合]\*\*\*\*，然後按一下包含該集合的實體名稱。</span><span class="sxs-lookup"><span data-stu-id="d7cb4-120">A collection, from the menu bar, point to **Collections** and click the name of the entity that contains the collection.</span></span>  
  
5.  <span data-ttu-id="d7cb4-121">在方格中，按一下要刪除之成員或集合的資料列。</span><span class="sxs-lookup"><span data-stu-id="d7cb4-121">In the grid, click the row of the member or collection you want to delete.</span></span>  
  
6.  <span data-ttu-id="d7cb4-122">按一下 [刪除成員]\*\*\*\*、[刪除]\*\*\*\* 或 [刪除集合]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d7cb4-122">Click **Delete Member**, **Delete**, or **Delete Collection**.</span></span>  
  
7.  <span data-ttu-id="d7cb4-123">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d7cb4-123">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7cb4-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7cb4-124">See Also</span></span>  
 <span data-ttu-id="d7cb4-125">[&#40;Master Data Services 重新啟用成員或集合&#41;](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d7cb4-125">[Reactivate a Member or Collection &#40;Master Data Services&#41;](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md) </span></span>  
 <span data-ttu-id="d7cb4-126">[成員 &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d7cb4-126">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 [<span data-ttu-id="d7cb4-127">集合 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d7cb4-127">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)  
  
  
