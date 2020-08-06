---
title: 匯出資料 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- exporting data [Master Data Services]
- subscription views [Master Data Services]
- subscription views [Master Data Services], about subscription views
ms.assetid: 8b74409a-ea70-45f8-84c7-da6905e4901a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: edae5b996c25a1b6053231ed2f69ef511b9fbfa6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596078"
---
# <a name="exporting-data-master-data-services"></a><span data-ttu-id="0dc80-102">匯出資料 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0dc80-102">Exporting Data (Master Data Services)</span></span>
  <span data-ttu-id="0dc80-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 您可以建立訂閱檢視，將  資料匯出至訂閱系統。</span><span class="sxs-lookup"><span data-stu-id="0dc80-103">You can export [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] data to subscribing systems by creating subscriptions views.</span></span> <span data-ttu-id="0dc80-104">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 然後，任何訂閱系統可以檢視  資料庫中的已發行資料。</span><span class="sxs-lookup"><span data-stu-id="0dc80-104">Any subscribing system can then view the published data in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="0dc80-105">如需檢視的更多資訊，請參閱[檢視](../relational-databases/views/views.md)。</span><span class="sxs-lookup"><span data-stu-id="0dc80-105">For more information about views, see [Views](../relational-databases/views/views.md).</span></span>  
  
## <a name="subscription-view-formats"></a><span data-ttu-id="0dc80-106">訂閱檢視格式</span><span class="sxs-lookup"><span data-stu-id="0dc80-106">Subscription View Formats</span></span>  
 <span data-ttu-id="0dc80-107">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]當您在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中建立檢視時，可以從  提供的一組標準檢視格式中選擇。</span><span class="sxs-lookup"><span data-stu-id="0dc80-107">When you create a view in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], you choose from a set of standard view formats that [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] provides.</span></span> <span data-ttu-id="0dc80-108">您可以使用這些格式來建立顯示下列項目的檢視表：</span><span class="sxs-lookup"><span data-stu-id="0dc80-108">You can use these formats to create views that show:</span></span>  
  
-   <span data-ttu-id="0dc80-109">所有分葉成員及其屬性。</span><span class="sxs-lookup"><span data-stu-id="0dc80-109">All leaf members and their attributes.</span></span>  
  
-   <span data-ttu-id="0dc80-110">所有合併成員及其屬性。</span><span class="sxs-lookup"><span data-stu-id="0dc80-110">All consolidated members and their attributes.</span></span>  
  
-   <span data-ttu-id="0dc80-111">所有集合及其屬性。</span><span class="sxs-lookup"><span data-stu-id="0dc80-111">All collections and their attributes.</span></span>  
  
-   <span data-ttu-id="0dc80-112">明確加入至集合的成員。</span><span class="sxs-lookup"><span data-stu-id="0dc80-112">The members explicitly added to a collection.</span></span>  
  
-   <span data-ttu-id="0dc80-113">在衍生階層中的父子式或層級格式成員。</span><span class="sxs-lookup"><span data-stu-id="0dc80-113">The members in a derived hierarchy, in either a parent child or level format.</span></span>  
  
-   <span data-ttu-id="0dc80-114">在所有明確階層中，實體的父子式或層級格式成員。</span><span class="sxs-lookup"><span data-stu-id="0dc80-114">The members in all explicit hierarchies for an entity, in either a parent child or level format.</span></span>  
  
## <a name="subscription-views-can-become-out-of-date"></a><span data-ttu-id="0dc80-115">訂閱檢視可能過期</span><span class="sxs-lookup"><span data-stu-id="0dc80-115">Subscription Views Can Become Out-of-Date</span></span>  
 <span data-ttu-id="0dc80-116">在建立實體或階層的訂閱檢視之後，檢視中未自動反映相關聯的模型物件變更。</span><span class="sxs-lookup"><span data-stu-id="0dc80-116">After you create a subscription view for an entity or hierarchy, changes to the associated model objects are not automatically reflected in the view.</span></span> <span data-ttu-id="0dc80-117">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 您可能需要在 中重新產生訂閱檢視，以反映模型物件變更。</span><span class="sxs-lookup"><span data-stu-id="0dc80-117">You might need to regenerate a subscription view in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to reflect changes to model objects.</span></span> <span data-ttu-id="0dc80-118">當模型物件變更時， **[匯出]** 頁面上的 **[已變更]** 欄會更新為 **True** 。</span><span class="sxs-lookup"><span data-stu-id="0dc80-118">The **Changed** column on the **Export** page is updated to **True** when model objects change.</span></span> <span data-ttu-id="0dc80-119">**True** 表示您應該編輯並儲存訂閱檢視，藉以重新產生訂閱檢視。</span><span class="sxs-lookup"><span data-stu-id="0dc80-119">**True** indicates that you should edit the subscription view and save it, which regenerates the view.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0dc80-120">相關工作</span><span class="sxs-lookup"><span data-stu-id="0dc80-120">Related Tasks</span></span>  
  
|<span data-ttu-id="0dc80-121">工作描述</span><span class="sxs-lookup"><span data-stu-id="0dc80-121">Task Description</span></span>|<span data-ttu-id="0dc80-122">主題</span><span class="sxs-lookup"><span data-stu-id="0dc80-122">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="0dc80-123">建立主要資料的訂閱檢視。</span><span class="sxs-lookup"><span data-stu-id="0dc80-123">Create a subscription view of your master data.</span></span>|[<span data-ttu-id="0dc80-124">建立訂閱視圖 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0dc80-124">Create a Subscription View &#40;Master Data Services&#41;</span></span>](create-a-subscription-view-to-export-data-master-data-services.md)|  
|<span data-ttu-id="0dc80-125">刪除現有的訂閱檢視。</span><span class="sxs-lookup"><span data-stu-id="0dc80-125">Delete an existing subscription view.</span></span>|[<span data-ttu-id="0dc80-126">刪除訂閱檢視 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0dc80-126">Delete a Subscription View &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-subscription-view-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="0dc80-127">相關內容</span><span class="sxs-lookup"><span data-stu-id="0dc80-127">Related Content</span></span>  
  
-   [<span data-ttu-id="0dc80-128">訂閱檢視格式 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0dc80-128">Subscription View Formats &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/subscription-view-formats-master-data-services.md)  
  
-   [<span data-ttu-id="0dc80-129">檢視</span><span class="sxs-lookup"><span data-stu-id="0dc80-129">Views</span></span>](../relational-databases/views/views.md)  
  
  
