---
title: 中繼資料 (Master Data Services) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- user-defined metadata [Master Data Services], about user-defined metadata
- metadata [Master Data Services], about metadata
- metadata [Master Data Services]
- user-defined metadata [Master Data Services]
ms.assetid: ac1aabe3-d8d4-4d7a-8954-50ee3c185d81
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 39ab95b7925306febb551962495da7ec9751589b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698404"
---
# <a name="metadata-master-data-services"></a><span data-ttu-id="d6b5f-102">中繼資料 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d6b5f-102">Metadata (Master Data Services)</span></span>
  <span data-ttu-id="d6b5f-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中，使用者定義的中繼資料是用來描述模型物件的資訊。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], user-defined metadata is information that you use to describe model objects.</span></span> <span data-ttu-id="d6b5f-104">例如，您可以追蹤特定模型或實體的擁有者，或追蹤提供資料給實體的來源系統。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-104">For example, you may want to track the owners of a particular model or entity, or track the source systems that supply data to an entity.</span></span>  
  
 <span data-ttu-id="d6b5f-105">使用者定義的中繼資料是由稱為「**中繼資料**」的模型所管理。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-105">User-defined metadata is managed by a model called **Metadata**.</span></span> <span data-ttu-id="d6b5f-106">當安裝時，會自動包含此模型 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ，而且它類似于其他所有 MDS 模型，但您無法建立其版本。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-106">This model is automatically included when [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] is installed, and it is similar to all other MDS models, except that you cannot create versions of it.</span></span>  
  
 <span data-ttu-id="d6b5f-107">當您使用使用者定義的中繼資料來擴展中繼資料模型時，可以將其包含在訂閱檢視中，以便透過訂閱系統來取用。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-107">After you populate the Metadata model with user-defined metadata, you can include it in subscription views, so it can be consumed by subscribing systems.</span></span>  
  
## <a name="metadata-entities"></a><span data-ttu-id="d6b5f-108">中繼資料實體</span><span class="sxs-lookup"><span data-stu-id="d6b5f-108">Metadata Entities</span></span>  
 <span data-ttu-id="d6b5f-109">中繼資料模型包含五個實體，每個實體代表一種支援使用者定義中繼資料的主要資料模型物件類型。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-109">The Metadata model includes five entities, each of which represents a type of master data model object that supports user-defined metadata.</span></span> <span data-ttu-id="d6b5f-110">例如，「**模型元資料定義**」實體包含代表模型的成員，而「**屬性元資料定義**」實體具有代表所有模型中所有屬性的成員。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-110">For example, the **Model Metadata Definition** entity contains members that represent models, and the **Attribute Metadata Definition** entity has members that represent all attributes in all models.</span></span>  
  
 <span data-ttu-id="d6b5f-111">若要定義模型物件的中繼資料，必須擴展其中一個成員的屬性。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-111">To define metadata for a model object, you populate one of these member's attributes.</span></span> <span data-ttu-id="d6b5f-112">例如，在**實體元資料定義**實體中，您可以在價格成員的 Description 屬性中填入下列文字：**銷售給客戶時的產品價格**。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-112">For example, in the **Entity Metadata Definition** entity, you can populate the Price member's Description attribute with the text: **The product price when sold to a customer**.</span></span>  
  
 <span data-ttu-id="d6b5f-113">每當加入或刪除支援使用者定義中繼資料的模型物件時，中繼資料模型中的成員會自動更新。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-113">The members in the Metadata model are automatically updated whenever model objects that support user-defined metadata are added or deleted.</span></span>  
  
 <span data-ttu-id="d6b5f-114">中繼資料模型無法建立版本、加入或變更版本旗標，或是另存為模型部署封裝。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-114">The Metadata model cannot be versioned, have version flags added or changed, or be saved as a model deployment package.</span></span> <span data-ttu-id="d6b5f-115">不過，它所提供的其他功能與其他主要資料模型都相同。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-115">However, it has all the same other functionality available to other master data models.</span></span> <span data-ttu-id="d6b5f-116">例如，您可以在中繼資料模型上實作一組商務規則來強制資料原則。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-116">For example, you might implement a set of business rules on the Metadata model to enforce data policies.</span></span>  
  
## <a name="customizing-your-metadata-model"></a><span data-ttu-id="d6b5f-117">自訂中繼資料模型</span><span class="sxs-lookup"><span data-stu-id="d6b5f-117">Customizing Your Metadata Model</span></span>  
 <span data-ttu-id="d6b5f-118">每個中繼資料定義實體都包含名稱、代碼和描述屬性。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-118">Each metadata definition entity includes Name, Code, and Description attributes.</span></span> <span data-ttu-id="d6b5f-119">您可以建立其他屬性，進一步描述模型物件。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-119">You may want to create additional attributes to further describe your model objects.</span></span>  
  
 <span data-ttu-id="d6b5f-120">例如，您可以建立：</span><span class="sxs-lookup"><span data-stu-id="d6b5f-120">For example, you might create:</span></span>  
  
-   <span data-ttu-id="d6b5f-121">名稱為 [擁有者] 的網域屬性，用來追蹤每個模型物件的擁有者。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-121">A domain-based attribute named Owner, which you use to track the owner of each model object.</span></span>  
  
-   <span data-ttu-id="d6b5f-122">名稱為 [上次檢閱日期] 的自由格式屬性，用來追蹤擁有者上次檢閱物件的日期。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-122">A free-form attribute named Last Review Date, which you use to track the date that an object was last reviewed by the owner.</span></span>  
  
-   <span data-ttu-id="d6b5f-123">名為 [來源] 的網域屬性，用來追蹤和管理與實例互動的來源系統 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-123">A domain-based attribute named Sources, which you use to track and manage the source systems that interact with the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] instance.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="d6b5f-124">相關工作</span><span class="sxs-lookup"><span data-stu-id="d6b5f-124">Related Tasks</span></span>  
  
|<span data-ttu-id="d6b5f-125">工作描述</span><span class="sxs-lookup"><span data-stu-id="d6b5f-125">Task Description</span></span>|<span data-ttu-id="d6b5f-126">主題</span><span class="sxs-lookup"><span data-stu-id="d6b5f-126">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="d6b5f-127">將中繼資料加入至模型物件。</span><span class="sxs-lookup"><span data-stu-id="d6b5f-127">Add metadata to a model object.</span></span>|[<span data-ttu-id="d6b5f-128">新增中繼資料 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d6b5f-128">Add Metadata &#40;Master Data Services&#41;</span></span>](add-metadata-master-data-services.md)
|&nbsp;|&nbsp;|
  
## <a name="related-content"></a><span data-ttu-id="d6b5f-129">相關內容</span><span class="sxs-lookup"><span data-stu-id="d6b5f-129">Related Content</span></span>  
  
-   [<span data-ttu-id="d6b5f-130">將資料匯出 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d6b5f-130">Exporting Data &#40;Master Data Services&#41;</span></span>](overview-exporting-data-master-data-services.md)  
  
  
