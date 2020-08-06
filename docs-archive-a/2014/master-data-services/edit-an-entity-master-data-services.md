---
title: 變更機構名稱 (Master Data Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], changing name
ms.assetid: 6a5b9f14-6dfc-49d7-a771-e96461d4feae
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9690fde44b0d56d790f4340779167fb55b400223
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687007"
---
# <a name="change-an-entity-name-master-data-services"></a><span data-ttu-id="48d0b-102">變更實體名稱 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="48d0b-102">Change an Entity Name (Master Data Services)</span></span>
  <span data-ttu-id="48d0b-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中，您可以變更實體的名稱。</span><span class="sxs-lookup"><span data-stu-id="48d0b-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can change the name of an entity.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="48d0b-104">系統將不會更新相關聯之暫存資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="48d0b-104">The names of the associated staging tables will not be updated.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="48d0b-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="48d0b-105">Prerequisites</span></span>  
 <span data-ttu-id="48d0b-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="48d0b-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="48d0b-107">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="48d0b-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="48d0b-108">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="48d0b-108">You must be a model administrator.</span></span> <span data-ttu-id="48d0b-109">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="48d0b-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-change-an-entity-name"></a><span data-ttu-id="48d0b-110">若要變更實體名稱</span><span class="sxs-lookup"><span data-stu-id="48d0b-110">To change an entity name</span></span>  
  
1.  <span data-ttu-id="48d0b-111">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="48d0b-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="48d0b-112">在 **[模型檢視]** 頁面上，從功能表列指向 **[管理]** ，然後按一下 **[實體]**。</span><span class="sxs-lookup"><span data-stu-id="48d0b-112">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="48d0b-113">在 **[實體維護]** 頁面上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="48d0b-113">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="48d0b-114">按一下您想要變更名稱之實體的資料列。</span><span class="sxs-lookup"><span data-stu-id="48d0b-114">Click the row for the entity with the name you want to change.</span></span>  
  
5.  <span data-ttu-id="48d0b-115">按一下 **[編輯選取的實體]**。</span><span class="sxs-lookup"><span data-stu-id="48d0b-115">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="48d0b-116">在 [**機構名稱**] 方塊中，輸入實體的更新名稱。</span><span class="sxs-lookup"><span data-stu-id="48d0b-116">In the **Entity name** box, type the updated name of the entity.</span></span>  
  
7.  <span data-ttu-id="48d0b-117">按一下 [**儲存實體**]。</span><span class="sxs-lookup"><span data-stu-id="48d0b-117">Click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48d0b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48d0b-118">See Also</span></span>  
 <span data-ttu-id="48d0b-119">[建立實體 &#40;Master Data Services&#41;](create-an-entity-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="48d0b-119">[Create an Entity &#40;Master Data Services&#41;](create-an-entity-master-data-services.md) </span></span>  
 <span data-ttu-id="48d0b-120">[刪除實體 &#40;Master Data Services&#41;](delete-an-entity-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="48d0b-120">[Delete an Entity &#40;Master Data Services&#41;](delete-an-entity-master-data-services.md) </span></span>  
 [<span data-ttu-id="48d0b-121">實體 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="48d0b-121">Entities &#40;Master Data Services&#41;</span></span>](entities-master-data-services.md)  
  
  
