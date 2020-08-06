---
title: 查看匯總使用 (匯總設計嚮導) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.aggregationdesignwizard.reviewusage.f1
ms.assetid: 107ee872-3df2-4931-b56c-af11e38f6745
author: minewiskan
ms.author: owend
ms.openlocfilehash: afbb02dae64f3f7ebd57065c3ff8a7d1e202dcf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592932"
---
# <a name="review-aggregation-usage-aggregation-design-wizard"></a><span data-ttu-id="a4a3c-102">檢閱彙總使用方式 (彙總設計精靈)</span><span class="sxs-lookup"><span data-stu-id="a4a3c-102">Review Aggregation Usage (Aggregation Design Wizard)</span></span>
  <span data-ttu-id="a4a3c-103">使用 **[檢閱彙總使用方式]** 頁面，即可設定彙總使用方式設定。</span><span class="sxs-lookup"><span data-stu-id="a4a3c-103">Use the **Review Aggregation Usage** page to configure aggregation usage settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a4a3c-104">選項</span><span class="sxs-lookup"><span data-stu-id="a4a3c-104">Options</span></span>  
 <span data-ttu-id="a4a3c-105">**預設值**</span><span class="sxs-lookup"><span data-stu-id="a4a3c-105">**Default**</span></span>  
 <span data-ttu-id="a4a3c-106">選取此選項，即可將屬性的彙總使用方式設定設為 Default。</span><span class="sxs-lookup"><span data-stu-id="a4a3c-106">Select to set the aggregation usage setting for the attribute to Default.</span></span> <span data-ttu-id="a4a3c-107">透過使用這項設定，設計工具會根據屬性和維度的類型來套用預設規則。</span><span class="sxs-lookup"><span data-stu-id="a4a3c-107">By using this setting, the designer applies a default rule based on the type of attribute and dimension.</span></span>  
  
 `Full`  
 <span data-ttu-id="a4a3c-108">選取此選項，即可將屬性的彙總使用方式設定設為 `Full`。</span><span class="sxs-lookup"><span data-stu-id="a4a3c-108">Select to set the aggregation usage setting for the attribute to `Full`.</span></span> <span data-ttu-id="a4a3c-109">透過使用這項設定，Cube 的每個彙總都必須包含這個屬性或在屬性鏈結中較低的相關屬性。</span><span class="sxs-lookup"><span data-stu-id="a4a3c-109">By using this setting, every aggregation for the cube must include this attribute or a related attribute that is lower in the attribute chain.</span></span> <span data-ttu-id="a4a3c-110">當某個屬性包含許多成員時，您就應該避免使用 `Full` 彙總使用方式設定。</span><span class="sxs-lookup"><span data-stu-id="a4a3c-110">The `Full` aggregation usage setting should be avoided when an attribute contains many members.</span></span> <span data-ttu-id="a4a3c-111">如果針對多個屬性或具有許多成員的屬性指定，這項設定可能會讓彙總無法設計，因為大小過大。</span><span class="sxs-lookup"><span data-stu-id="a4a3c-111">If specified for multiple attributes or attributes that have many members, this setting might prevent aggregations from being designed because of excessive size.</span></span>  
  
 <span data-ttu-id="a4a3c-112">**None**</span><span class="sxs-lookup"><span data-stu-id="a4a3c-112">**None**</span></span>  
 <span data-ttu-id="a4a3c-113">選取此選項，即可將屬性的彙總使用方式設定設為 None。</span><span class="sxs-lookup"><span data-stu-id="a4a3c-113">Select to set the aggregation usage setting for the attribute to None.</span></span> <span data-ttu-id="a4a3c-114">透過使用這項設定，Cube 的任何彙總都無法包含這個屬性。</span><span class="sxs-lookup"><span data-stu-id="a4a3c-114">By using this setting, no aggregation for the cube can include this attribute.</span></span>  
  
 `Unrestricted`  
 <span data-ttu-id="a4a3c-115">選取此選項，即可將屬性的彙總使用方式設定設為 `Unrestricted`。</span><span class="sxs-lookup"><span data-stu-id="a4a3c-115">Select to set the aggregation usage setting for the attribute to `Unrestricted`.</span></span> <span data-ttu-id="a4a3c-116">透過使用這項設定，系統將不會對彙總設計師設定任何限制。不過，此屬性仍然必須經過評估，以便判斷它是否為重要的彙總候選。</span><span class="sxs-lookup"><span data-stu-id="a4a3c-116">By using this setting, no restrictions are put on the aggregation designer; however, the attribute must still be evaluated to determine whether it is a valuable aggregation candidate.</span></span>  
  
 <span data-ttu-id="a4a3c-117">**全部設定為預設值**</span><span class="sxs-lookup"><span data-stu-id="a4a3c-117">**Set All to Default**</span></span>  
 <span data-ttu-id="a4a3c-118">選取此選項，即可將所有屬性的彙總使用方式設定都設為 Default。</span><span class="sxs-lookup"><span data-stu-id="a4a3c-118">Select to set the aggregation usage settings for all attributes to Default.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a3c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4a3c-119">See Also</span></span>  
 <span data-ttu-id="a4a3c-120">[匯總設計嚮導 F1 說明](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="a4a3c-120">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="a4a3c-121">Analysis Services 的 &#40;多維度資料的嚮導&#41;</span><span class="sxs-lookup"><span data-stu-id="a4a3c-121">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
