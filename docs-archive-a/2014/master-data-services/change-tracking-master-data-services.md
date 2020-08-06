---
title: 變更追蹤 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2d3b69057b02884f41a43aa9a009ab3db937ed25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701281"
---
# <a name="change-tracking-master-data-services"></a><span data-ttu-id="0781f-102">變更追蹤 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0781f-102">Change Tracking (Master Data Services)</span></span>
  <span data-ttu-id="0781f-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以使用變更追蹤群組在屬性值變更時採取動作。</span><span class="sxs-lookup"><span data-stu-id="0781f-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can use change tracking groups to take action when an attribute value changes.</span></span> <span data-ttu-id="0781f-104">當您不知道新值，但想要知道是否發生任何變更時，請使用變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="0781f-104">Use change tracking when you don't know what the new value will be, but instead want to know if any change occurred.</span></span>  
  
## <a name="configuring-change-tracking"></a><span data-ttu-id="0781f-105">設定變更追蹤</span><span class="sxs-lookup"><span data-stu-id="0781f-105">Configuring Change Tracking</span></span>  
 <span data-ttu-id="0781f-106">若要設定變更追蹤，您要將屬性加入至變更追蹤群組。</span><span class="sxs-lookup"><span data-stu-id="0781f-106">To configure change tracking, you add an attribute to a change tracking group.</span></span> <span data-ttu-id="0781f-107">此群組可以包含一個或多個屬性。</span><span class="sxs-lookup"><span data-stu-id="0781f-107">The group can contain one or many attributes.</span></span> <span data-ttu-id="0781f-108">接著，您要建立商務規則來定義群組中的任何屬性變更時所要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="0781f-108">Then, you create a business rule to define the action that is taken when any of the attributes in the group change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0781f-109">變更追蹤商務規則會將暫存 (匯入的) 資料視為變更。</span><span class="sxs-lookup"><span data-stu-id="0781f-109">Change tracking business rules consider staged (imported) data to be changed.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0781f-110">相關工作</span><span class="sxs-lookup"><span data-stu-id="0781f-110">Related Tasks</span></span>  
  
|<span data-ttu-id="0781f-111">工作描述</span><span class="sxs-lookup"><span data-stu-id="0781f-111">Task Description</span></span>|<span data-ttu-id="0781f-112">主題</span><span class="sxs-lookup"><span data-stu-id="0781f-112">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="0781f-113">將屬性加入至變更追蹤群組。</span><span class="sxs-lookup"><span data-stu-id="0781f-113">Add attributes to a change tracking group.</span></span>|[<span data-ttu-id="0781f-114">將屬性加入至變更追蹤群組 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0781f-114">Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;</span></span>](add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|<span data-ttu-id="0781f-115">建立根據屬性變更來起始動作的商務規則。</span><span class="sxs-lookup"><span data-stu-id="0781f-115">Create a business rule that initiates actions based on attribute changes.</span></span>|[<span data-ttu-id="0781f-116">根據屬性值變更來起始動作 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0781f-116">Initiate Actions Based on Attribute Value Changes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="0781f-117">相關內容</span><span class="sxs-lookup"><span data-stu-id="0781f-117">Related Content</span></span>  
  
-   [<span data-ttu-id="0781f-118">驗證 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0781f-118">Validation &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-master-data-services.md)  
  
-   [<span data-ttu-id="0781f-119">商務規則 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0781f-119">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="0781f-120">屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0781f-120">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
