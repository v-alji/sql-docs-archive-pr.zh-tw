---
title: 建立衍生階層 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, creating
- creating derived hierarchies [Master Data Services]
ms.assetid: fec653c4-11cc-46a2-8dd8-b605341ebb40
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 20469ad30222e43a3104503cc32187c2e6512743
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701257"
---
# <a name="create-a-derived-hierarchy-master-data-services"></a><span data-ttu-id="04ed7-102">建立衍生階層 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="04ed7-102">Create a Derived Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="04ed7-103">當您需要以層級為基礎的階層，確保成員存在於正確層級時，可以在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中建立衍生階層。</span><span class="sxs-lookup"><span data-stu-id="04ed7-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a derived hierarchy when you want a level-based hierarchy that ensures that members exist at the correct level.</span></span> <span data-ttu-id="04ed7-104">衍生階層是以模型中存在的網域屬性關聯性為基礎。</span><span class="sxs-lookup"><span data-stu-id="04ed7-104">Derived hierarchies are based on the domain-based attribute relationships that exist in a model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="04ed7-105">如果成員沒有網域屬性值，衍生階層中不會包含此成員。</span><span class="sxs-lookup"><span data-stu-id="04ed7-105">If a domain-based attribute value doesn't exist for a member, the member is not included in the derived hierarchy.</span></span> <span data-ttu-id="04ed7-106">若需要求所有成員的網域屬性值，請參閱[要求屬性值 &#40;Master Data Services&#41;](require-attribute-values-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="04ed7-106">See [Require Attribute Values &#40;Master Data Services&#41;](require-attribute-values-master-data-services.md) to require a domain-based attribute value for all members.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="04ed7-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="04ed7-107">Prerequisites</span></span>  
 <span data-ttu-id="04ed7-108">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="04ed7-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="04ed7-109">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="04ed7-109">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="04ed7-110">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="04ed7-110">You must be a model administrator.</span></span> <span data-ttu-id="04ed7-111">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="04ed7-111">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-derived-hierarchy"></a><span data-ttu-id="04ed7-112">若要建立衍生階層</span><span class="sxs-lookup"><span data-stu-id="04ed7-112">To create a derived hierarchy</span></span>  
  
1.  <span data-ttu-id="04ed7-113">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="04ed7-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="04ed7-114">在 [**模型視圖**] 頁面上，從功能表列指向 [**管理**]，然後按一下 [**衍生**階層]。</span><span class="sxs-lookup"><span data-stu-id="04ed7-114">On the **Model View** page, from the menu bar, point to **Manage** and click **Derived Hierarchies**.</span></span>  
  
3.  <span data-ttu-id="04ed7-115">在 [衍生階層維護]\*\*\*\* 頁面上，選取 [模型]\*\*\*\* 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="04ed7-115">On the **Derived Hierarchy Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="04ed7-116">按一下 [**加入衍生**階層]。</span><span class="sxs-lookup"><span data-stu-id="04ed7-116">Click **Add derived hierarchy**.</span></span>  
  
5.  <span data-ttu-id="04ed7-117">在 [加入衍生階層]\*\*\*\* 頁面上的 [衍生階層名稱]\*\*\*\* 方塊中，輸入階層的名稱。</span><span class="sxs-lookup"><span data-stu-id="04ed7-117">On the **Add Derived Hierarchy** page, in the **Derived hierarchy name** box, type a name for the hierarchy.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="04ed7-118">請使用名稱來描述階層中的層級，例如 **產品到子類別目錄到類別目錄**。</span><span class="sxs-lookup"><span data-stu-id="04ed7-118">Use a name that describes the levels in the hierarchy, for example **Product to Subcategory to Category**.</span></span>  
  
6.  <span data-ttu-id="04ed7-119">按一下 [儲存衍生階層]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="04ed7-119">Click **Save derived hierarchy**.</span></span>  
  
7.  <span data-ttu-id="04ed7-120">在 [**編輯衍生**階層] 頁面的 [**可用的實體和**階層] 窗格中，按一下實體或階層，並將它拖曳至 [**目前層級**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="04ed7-120">On the **Edit Derived Hierarchy** page, in the **Available Entities and Hierarchies** pane, click an entity or hierarchy and drag it to the **Current Levels** pane.</span></span>  
  
8.  <span data-ttu-id="04ed7-121">繼續拖曳實體或階層，直到完成階層為止。</span><span class="sxs-lookup"><span data-stu-id="04ed7-121">Continue dragging entities or hierarchies until your hierarchy is complete.</span></span>  
  
9. <span data-ttu-id="04ed7-122">按一下 [上一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="04ed7-122">Click **Back**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04ed7-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04ed7-123">See Also</span></span>  
 <span data-ttu-id="04ed7-124">[衍生階層 &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="04ed7-124">[Derived Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span></span>  
 <span data-ttu-id="04ed7-125">[具有明確大寫的衍生階層 &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="04ed7-125">[Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md) </span></span>  
 [<span data-ttu-id="04ed7-126">網域屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="04ed7-126">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)  
  
  
