---
title: 查看匯總使用方式 (以使用量為基礎的基於優化 Wizard) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.reviewaggregationusage.f1
ms.assetid: 49ce2094-c4dc-4e46-8cef-c17c5db084ca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5ef9f900e64858515db226d1f9b864874a4ba827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592931"
---
# <a name="review-aggregation-usage-usage-based-optimiation-wizard"></a><span data-ttu-id="ba46c-102">檢閱彙總使用方式 (基於使用方式的最佳化精靈)</span><span class="sxs-lookup"><span data-stu-id="ba46c-102">Review Aggregation Usage (Usage-Based Optimiation Wizard)</span></span>
  <span data-ttu-id="ba46c-103">使用 **[檢閱彙總使用方式]** 頁面，即可設定彙總使用方式設定。</span><span class="sxs-lookup"><span data-stu-id="ba46c-103">Use the **Review Aggregation Usage** page to configure aggregation usage settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ba46c-104">選項</span><span class="sxs-lookup"><span data-stu-id="ba46c-104">Options</span></span>  
 <span data-ttu-id="ba46c-105">**預設值**</span><span class="sxs-lookup"><span data-stu-id="ba46c-105">**Default**</span></span>  
 <span data-ttu-id="ba46c-106">選取此選項，即可將屬性的彙總使用方式設定設為 Default。</span><span class="sxs-lookup"><span data-stu-id="ba46c-106">Select to set the aggregation usage setting for the attribute to Default.</span></span> <span data-ttu-id="ba46c-107">透過使用這項設定，設計工具會根據屬性和維度的類型來套用預設規則。</span><span class="sxs-lookup"><span data-stu-id="ba46c-107">By using this setting, the designer applies a default rule based on the type of attribute and dimension.</span></span>  
  
 <span data-ttu-id="ba46c-108">**完整**</span><span class="sxs-lookup"><span data-stu-id="ba46c-108">**Full**</span></span>  
 <span data-ttu-id="ba46c-109">選取此選項，即可將屬性的彙總使用方式設定設為 Full。</span><span class="sxs-lookup"><span data-stu-id="ba46c-109">Select to set the aggregation usage setting for the attribute to Full.</span></span> <span data-ttu-id="ba46c-110">透過使用這項設定，Cube 的每個彙總都必須包含這個屬性或在屬性鏈結中較低的相關屬性。</span><span class="sxs-lookup"><span data-stu-id="ba46c-110">By using this setting, every aggregation for the cube must include this attribute or a related attribute that is lower in the attribute chain.</span></span> <span data-ttu-id="ba46c-111">當某個屬性包含許多成員時，您就應該避免使用 Full 彙總使用方式設定。</span><span class="sxs-lookup"><span data-stu-id="ba46c-111">The Full aggregation usage setting should be avoided when an attribute contains many members.</span></span> <span data-ttu-id="ba46c-112">如果針對多個屬性或具有許多成員的屬性指定，這項設定可能會讓彙總無法設計，因為大小過大。</span><span class="sxs-lookup"><span data-stu-id="ba46c-112">If specified for multiple attributes or attributes that have many members, this setting might prevent aggregations from being designed because of excessive size.</span></span>  
  
 <span data-ttu-id="ba46c-113">**None**</span><span class="sxs-lookup"><span data-stu-id="ba46c-113">**None**</span></span>  
 <span data-ttu-id="ba46c-114">選取此選項，即可將屬性的彙總使用方式設定設為 None。</span><span class="sxs-lookup"><span data-stu-id="ba46c-114">Select to set the aggregation usage setting for the attribute to None.</span></span> <span data-ttu-id="ba46c-115">透過使用這項設定，Cube 的任何彙總都無法包含這個屬性。</span><span class="sxs-lookup"><span data-stu-id="ba46c-115">By using this setting, no aggregation for the cube can include this attribute.</span></span>  
  
 <span data-ttu-id="ba46c-116">**L**</span><span class="sxs-lookup"><span data-stu-id="ba46c-116">**Unrestricted**</span></span>  
 <span data-ttu-id="ba46c-117">選取此選項，即可將屬性的彙總使用方式設定設為 Unrestricted。</span><span class="sxs-lookup"><span data-stu-id="ba46c-117">Select to set the aggregation usage setting for the attribute to Unrestricted.</span></span> <span data-ttu-id="ba46c-118">透過使用這項設定，系統將不會對彙總設計師設定任何限制。</span><span class="sxs-lookup"><span data-stu-id="ba46c-118">By using this setting, no restrictions are put on the aggregation designer.</span></span> <span data-ttu-id="ba46c-119">不過，此屬性仍然必須經過評估，以便判斷它是否為重要的彙總候選。</span><span class="sxs-lookup"><span data-stu-id="ba46c-119">However, the attribute must still be evaluated to determine whether it is a valuable aggregation candidate.</span></span>  
  
 <span data-ttu-id="ba46c-120">**全部設定為預設值**</span><span class="sxs-lookup"><span data-stu-id="ba46c-120">**Set All to Default**</span></span>  
 <span data-ttu-id="ba46c-121">選取此選項，即可將所有屬性的彙總使用方式設定都設為 Default。</span><span class="sxs-lookup"><span data-stu-id="ba46c-121">Select to set the aggregation usage settings for all attributes to Default.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba46c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba46c-122">See Also</span></span>  
 <span data-ttu-id="ba46c-123">[匯總設計嚮導 F1 說明](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="ba46c-123">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="ba46c-124">Analysis Services 的 &#40;多維度資料的嚮導&#41;</span><span class="sxs-lookup"><span data-stu-id="ba46c-124">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
