---
title: 模型 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], about models
- models [Master Data Services]
ms.assetid: 9f862a3d-25ab-41e9-b833-1db99959e825
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1d5a4a431d3ca7b6fa499de68a2bc4c5033cd086
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606377"
---
# <a name="models-master-data-services"></a><span data-ttu-id="1d085-102">模型 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1d085-102">Models (Master Data Services)</span></span>
  <span data-ttu-id="1d085-103">模型是 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中最高層級的資料組織。</span><span class="sxs-lookup"><span data-stu-id="1d085-103">Models are the highest level of data organization in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="1d085-104">模型定義主要資料管理方案中的資料結構。</span><span class="sxs-lookup"><span data-stu-id="1d085-104">A model defines the structure of data in your master data management solution.</span></span> <span data-ttu-id="1d085-105">模型包含下列物件：</span><span class="sxs-lookup"><span data-stu-id="1d085-105">A model contains the following objects:</span></span>  
  
-   <span data-ttu-id="1d085-106">實體</span><span class="sxs-lookup"><span data-stu-id="1d085-106">Entities</span></span>  
  
-   <span data-ttu-id="1d085-107">屬性和屬性群組</span><span class="sxs-lookup"><span data-stu-id="1d085-107">Attributes and attribute groups</span></span>  
  
-   <span data-ttu-id="1d085-108">明確和衍生階層</span><span class="sxs-lookup"><span data-stu-id="1d085-108">Explicit and derived hierarchies</span></span>  
  
-   <span data-ttu-id="1d085-109">集合</span><span class="sxs-lookup"><span data-stu-id="1d085-109">Collections</span></span>  
  
 <span data-ttu-id="1d085-110">模型組織主要資料的結構。</span><span class="sxs-lookup"><span data-stu-id="1d085-110">Models organize the structure of your master data.</span></span> <span data-ttu-id="1d085-111">您的 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 實作可以有一個或多個模型，其中每個模型都會將類似資料分組在一起。</span><span class="sxs-lookup"><span data-stu-id="1d085-111">Your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] implementation can have one or many models that each group similar kinds of data.</span></span> <span data-ttu-id="1d085-112">主要資料通常以四種方式分類：人員、位置、東西或概念。</span><span class="sxs-lookup"><span data-stu-id="1d085-112">In general, master data can be categorized in one of four ways: people, places, things, or concepts.</span></span> <span data-ttu-id="1d085-113">例如，您可以建立一個 Product 模型來容納產品相關的資料，或是建立一個 Customer 模型來容納客戶相關的資料。</span><span class="sxs-lookup"><span data-stu-id="1d085-113">For example, you can create a Product model to contain product-related data or a Customer model to contain customer-related data.</span></span>  
  
 <span data-ttu-id="1d085-114">您可以指派使用者和群組權限來檢視及更新模型內的物件。</span><span class="sxs-lookup"><span data-stu-id="1d085-114">You can assign users and groups permission to view and update objects within the model.</span></span> <span data-ttu-id="1d085-115">如果您未提供模型的權限，就不會顯示權限。</span><span class="sxs-lookup"><span data-stu-id="1d085-115">If you do not give permission to the model, it is not displayed.</span></span>  
  
 <span data-ttu-id="1d085-116">您可以在任何給定的時刻，於模型內建立主資料的複本。</span><span class="sxs-lookup"><span data-stu-id="1d085-116">At any given time, you can create copies of the master data within a model.</span></span> <span data-ttu-id="1d085-117">這些複本稱為版本。</span><span class="sxs-lookup"><span data-stu-id="1d085-117">These copies are called versions.</span></span>  
  
 <span data-ttu-id="1d085-118">當您在測試環境中定義模型時，不論有沒有對應的資料，您都可以從測試環境到實際執行環境來部署此模型。</span><span class="sxs-lookup"><span data-stu-id="1d085-118">When you have defined a model in a test environment, you can deploy it, with or without the corresponding data, from the test environment to a production environment.</span></span> <span data-ttu-id="1d085-119">這樣就不需要在實際執行環境內重建模型。</span><span class="sxs-lookup"><span data-stu-id="1d085-119">This eliminates the need to recreate your models in your production environment.</span></span>  
  
## <a name="how-models-relate-to-other-objects"></a><span data-ttu-id="1d085-120">模型如何與其他物件相關聯</span><span class="sxs-lookup"><span data-stu-id="1d085-120">How Models Relate to Other Objects</span></span>  
 <span data-ttu-id="1d085-121">模型包含實體。</span><span class="sxs-lookup"><span data-stu-id="1d085-121">A model contains entities.</span></span> <span data-ttu-id="1d085-122">實體包含屬性、明確階層和集合。</span><span class="sxs-lookup"><span data-stu-id="1d085-122">Entities contain attributes, explicit hierarchies, and collections.</span></span> <span data-ttu-id="1d085-123">屬性可以包含在屬性群組中。</span><span class="sxs-lookup"><span data-stu-id="1d085-123">Attributes can be contained in attribute groups.</span></span> <span data-ttu-id="1d085-124">當實體做為另一個實體的屬性時，就會有網域屬性。</span><span class="sxs-lookup"><span data-stu-id="1d085-124">Domain-based attributes exist when an entity is used as an attribute for another entity.</span></span>  
  
 <span data-ttu-id="1d085-125">下圖顯示模型中物件之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="1d085-125">This image shows the relationships among the objects in a model.</span></span>  
  
 <span data-ttu-id="1d085-126">![Master Data Services 模型中的物件](../../2014/master-data-services/media/mds-conc-model-circles.gif "Master Data Services 模型中的物件")</span><span class="sxs-lookup"><span data-stu-id="1d085-126">![Objects in a Master Data Services Model](../../2014/master-data-services/media/mds-conc-model-circles.gif "Objects in a Master Data Services Model")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1d085-127">衍生階層也是模型物件，但在上圖中未顯示。</span><span class="sxs-lookup"><span data-stu-id="1d085-127">Derived hierarchies are also model objects, but they are not shown in the image.</span></span> <span data-ttu-id="1d085-128">衍生階層衍生自實體之間存在的網域屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="1d085-128">Derived hierarchies are derived from the domain-based attribute relationships that exist between entities.</span></span> <span data-ttu-id="1d085-129">如需詳細資訊，請參閱[衍生階層 &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1d085-129">See [Derived Hierarchies &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md) for more information.</span></span>  
  
 <span data-ttu-id="1d085-130">主要資料是模型物件中包含的資料。</span><span class="sxs-lookup"><span data-stu-id="1d085-130">Master data is the data that is contained in the model objects.</span></span> <span data-ttu-id="1d085-131">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，主要資料是儲存為實體中的成員。</span><span class="sxs-lookup"><span data-stu-id="1d085-131">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], master data is stored as members in an entity.</span></span>  
  
 <span data-ttu-id="1d085-132">模型物件是在 **使用者介面的** [系統管理] [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 功能區域中進行維護。</span><span class="sxs-lookup"><span data-stu-id="1d085-132">Model objects are maintained in the **System Administration** functional area of the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface.</span></span>  
  
## <a name="model-example"></a><span data-ttu-id="1d085-133">模型範例</span><span class="sxs-lookup"><span data-stu-id="1d085-133">Model Example</span></span>  
 <span data-ttu-id="1d085-134">在下列範例中，Product 模型中的物件以邏輯方式分組產品相關資料。</span><span class="sxs-lookup"><span data-stu-id="1d085-134">In the following example, the objects in the Product model logically group product-related data.</span></span>  
  
 <span data-ttu-id="1d085-135">![產品模型主要資料範例](../../2014/master-data-services/media/mds-conc-model.gif "產品模型主要資料範例")</span><span class="sxs-lookup"><span data-stu-id="1d085-135">![Product Model Master Data Example](../../2014/master-data-services/media/mds-conc-model.gif "Product Model Master Data Example")</span></span>  
  
 <span data-ttu-id="1d085-136">其他常見的模型如下：</span><span class="sxs-lookup"><span data-stu-id="1d085-136">Other common models are:</span></span>  
  
-   <span data-ttu-id="1d085-137">帳戶，可能包括類似資產負債表帳戶、損益表帳戶、統計資料及帳戶類型等實體。</span><span class="sxs-lookup"><span data-stu-id="1d085-137">Accounts, which could include entities such as balance sheet accounts, income statement accounts, statistics, and account type.</span></span>  
  
-   <span data-ttu-id="1d085-138">客戶，可能包括類似性別、教育、職業及婚姻狀態等實體。</span><span class="sxs-lookup"><span data-stu-id="1d085-138">Customer, which could include entities such as gender, education, occupation, and marital status.</span></span>  
  
-   <span data-ttu-id="1d085-139">地理位置，可能包括類似郵遞區號、城市、縣市、州、省、區域、領域、國家/地區及大陸等實體。</span><span class="sxs-lookup"><span data-stu-id="1d085-139">Geography, which could include entities such as postal codes, cities, counties, states, provinces, regions, territories, countries, and continents.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="1d085-140">相關工作</span><span class="sxs-lookup"><span data-stu-id="1d085-140">Related Tasks</span></span>  
  
|<span data-ttu-id="1d085-141">工作描述</span><span class="sxs-lookup"><span data-stu-id="1d085-141">Task Description</span></span>|<span data-ttu-id="1d085-142">主題</span><span class="sxs-lookup"><span data-stu-id="1d085-142">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="1d085-143">建立模型來組織您的主要資料。</span><span class="sxs-lookup"><span data-stu-id="1d085-143">Create a model to organize your master data.</span></span>|[<span data-ttu-id="1d085-144">建立模型 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1d085-144">Create a Model &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-model-master-data-services.md)|  
|<span data-ttu-id="1d085-145">變更現有模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="1d085-145">Change the name of an existing model.</span></span>|[<span data-ttu-id="1d085-146">變更模型名稱 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1d085-146">Change a Model Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-model-name-master-data-services.md)|  
|<span data-ttu-id="1d085-147">刪除現有模型。</span><span class="sxs-lookup"><span data-stu-id="1d085-147">Delete an existing model.</span></span>|[<span data-ttu-id="1d085-148">刪除模型 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1d085-148">Delete a Model &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-model-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="1d085-149">相關內容</span><span class="sxs-lookup"><span data-stu-id="1d085-149">Related Content</span></span>  
  
-   [<span data-ttu-id="1d085-150">Master Data Services 概觀</span><span class="sxs-lookup"><span data-stu-id="1d085-150">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)  
  
-   [<span data-ttu-id="1d085-151">實體 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1d085-151">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)  
  
-   [<span data-ttu-id="1d085-152">屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1d085-152">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
-   [<span data-ttu-id="1d085-153">部署模型 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1d085-153">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
-   [<span data-ttu-id="1d085-154">模型物件權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1d085-154">Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/model-object-permissions-master-data-services.md)  
  
  
