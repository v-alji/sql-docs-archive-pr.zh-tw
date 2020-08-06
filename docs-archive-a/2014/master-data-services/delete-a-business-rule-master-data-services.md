---
title: 刪除商務規則 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting business rules [Master Data Services]
- business rules [Master Data Services], deleting
ms.assetid: b97aa4f9-569f-451d-ad62-65b81f980299
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8e6db486f71634cf025c57eabbedeeb9efdbc437
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687013"
---
# <a name="delete-a-business-rule-master-data-services"></a><span data-ttu-id="aa076-102">刪除商務規則 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="aa076-102">Delete a Business Rule (Master Data Services)</span></span>
  <span data-ttu-id="aa076-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，刪除不再需要的商務規則。</span><span class="sxs-lookup"><span data-stu-id="aa076-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete a business rule when it is no longer needed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa076-104">您可以避免資料使用商務規則來加以驗證，其方式是排除該商務規則，而不是將它刪除。</span><span class="sxs-lookup"><span data-stu-id="aa076-104">You can prevent data from being validated against a business rule by excluding it, rather than deleting it.</span></span> <span data-ttu-id="aa076-105">如需詳細資訊，請參閱 [排除商務規則 &#40;Master Data Services&#41;](exclude-a-business-rule-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="aa076-105">For more information, see [Exclude a Business Rule &#40;Master Data Services&#41;](exclude-a-business-rule-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="aa076-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="aa076-106">Prerequisites</span></span>  
 <span data-ttu-id="aa076-107">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="aa076-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="aa076-108">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="aa076-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="aa076-109">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="aa076-109">You must be a model administrator.</span></span> <span data-ttu-id="aa076-110">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="aa076-110">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-a-business-rule"></a><span data-ttu-id="aa076-111">若要刪除商務規則</span><span class="sxs-lookup"><span data-stu-id="aa076-111">To delete a business rule</span></span>  
  
1.  <span data-ttu-id="aa076-112">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="aa076-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="aa076-113">從功能表列，指向 **[管理]** ，然後按一下 **[商務規則]**。</span><span class="sxs-lookup"><span data-stu-id="aa076-113">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="aa076-114">在 [商務規則維護]\*\*\*\* 頁面上，選取 [模型]\*\*\*\* 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="aa076-114">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="aa076-115">從 [實體]\*\*\*\* 清單中選取實體。</span><span class="sxs-lookup"><span data-stu-id="aa076-115">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="aa076-116">從 [成員類型]\*\*\*\* 清單中，選取要套用商務規則的成員類型。</span><span class="sxs-lookup"><span data-stu-id="aa076-116">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="aa076-117">從 [屬性]\*\*\*\* 清單中，選取屬性或保留預設值 [全部]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aa076-117">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="aa076-118">在方格中，按一下您想要刪除之商務規則的資料列。</span><span class="sxs-lookup"><span data-stu-id="aa076-118">In the grid, click the row for the business rule you want to delete.</span></span>  
  
8.  <span data-ttu-id="aa076-119">按一下 [**刪除選取的商務規則**]。</span><span class="sxs-lookup"><span data-stu-id="aa076-119">Click **Delete selected business rule**.</span></span>  
  
9. <span data-ttu-id="aa076-120">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="aa076-120">In the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="aa076-121">[**狀態**] 資料行中的值是 [**刪除暫**止]。</span><span class="sxs-lookup"><span data-stu-id="aa076-121">The value in the **Status** column is **Deletion pending**.</span></span>  
  
10. <span data-ttu-id="aa076-122">按一下 [發行商務規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aa076-122">Click **Publish business rules**.</span></span>  
  
11. <span data-ttu-id="aa076-123">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="aa076-123">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa076-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa076-124">See Also</span></span>  
 <span data-ttu-id="aa076-125">[排除商務規則 &#40;Master Data Services&#41;](exclude-a-business-rule-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="aa076-125">[Exclude a Business Rule &#40;Master Data Services&#41;](exclude-a-business-rule-master-data-services.md) </span></span>  
 <span data-ttu-id="aa076-126">[建立和發佈商務規則 &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="aa076-126">[Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md) </span></span>  
 [<span data-ttu-id="aa076-127">商務規則 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="aa076-127">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
