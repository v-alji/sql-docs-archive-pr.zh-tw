---
title: 指定物件計數 (基於使用方式的優化 Wizard) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.calculatingobjectcounts.f1
ms.assetid: 306c7c25-ae24-4852-ab8c-c82f68a4bc1f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 862be19f12308def815a280dba04f42f0cbe6878
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598552"
---
# <a name="specify-object-counts-usage-based-optimization-wizard"></a><span data-ttu-id="0c7c3-102">指定物件計數 (基於使用方式的最佳化精靈)</span><span class="sxs-lookup"><span data-stu-id="0c7c3-102">Specify Object Counts (Usage-Based Optimization Wizard)</span></span>
  <span data-ttu-id="0c7c3-103">使用 **[指定物件計數]** 頁面，即可自動計算 Cube 中的物件計數，或者手動輸入估計的計數。</span><span class="sxs-lookup"><span data-stu-id="0c7c3-103">Use the **Specify Object Counts** page to automatically calculate the count of objects in the cube or to manually enter estimated counts.</span></span> <span data-ttu-id="0c7c3-104">「基於使用方式的最佳化精靈」會使用物件計數來估計儲存需求。</span><span class="sxs-lookup"><span data-stu-id="0c7c3-104">The Usage-Based Optimization Wizard uses the object counts to estimate storage requirements.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0c7c3-105">選項</span><span class="sxs-lookup"><span data-stu-id="0c7c3-105">Options</span></span>  
 <span data-ttu-id="0c7c3-106">**Cube 物件**</span><span class="sxs-lookup"><span data-stu-id="0c7c3-106">**Cube Objects**</span></span>  
 <span data-ttu-id="0c7c3-107">顯示 Cube 中的維度及屬性。</span><span class="sxs-lookup"><span data-stu-id="0c7c3-107">Displays the dimensions and attributes in the cube.</span></span> <span data-ttu-id="0c7c3-108">在 `AggregationUsage` wizard 的 [**審核匯總使用**方式] 頁面中，只有未將其屬性設為 [無] 的屬性會顯示出來，因為這是唯一需要指定計數的屬性。</span><span class="sxs-lookup"><span data-stu-id="0c7c3-108">Only the attributes that do not have their `AggregationUsage` property set to None in the **Review Aggregation Usage** page of the wizard are shown because those are the only attributes that need counts specified.</span></span>  
  
 <span data-ttu-id="0c7c3-109">**估計計數**</span><span class="sxs-lookup"><span data-stu-id="0c7c3-109">**Estimated count**</span></span>  
 <span data-ttu-id="0c7c3-110">顯示量值群組中估計的資料列數目以及資料庫維度中估計的屬性成員計數。</span><span class="sxs-lookup"><span data-stu-id="0c7c3-110">Displays the estimated number of rows in the measure group and the estimated attribute member counts in the database dimensions.</span></span> <span data-ttu-id="0c7c3-111">您可以輸入要當做估計計數使用的值，也可以計算估計計數的值。</span><span class="sxs-lookup"><span data-stu-id="0c7c3-111">You can type a value to use as the estimated count or you can calculate the estimated count values.</span></span> <span data-ttu-id="0c7c3-112">若要計算計數值，請在欄位中輸入 0 ，然後按一下 [計數] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0c7c3-112">To calculate the count values, type 0 in the field and then click **Count**.</span></span> <span data-ttu-id="0c7c3-113">已經顯示計數的欄位不會更新。</span><span class="sxs-lookup"><span data-stu-id="0c7c3-113">Fields that already display a count are not updated.</span></span>  
  
 <span data-ttu-id="0c7c3-114">**分割計數**</span><span class="sxs-lookup"><span data-stu-id="0c7c3-114">**Partition count**</span></span>  
 <span data-ttu-id="0c7c3-115">(選擇性) 輸入量值群組中估計的資料列數目以及資料分割中估計的屬性成員計數。</span><span class="sxs-lookup"><span data-stu-id="0c7c3-115">(Optional) Type the estimated number of rows in the measure group and the estimated attribute member counts in the partitions.</span></span>  
  
 <span data-ttu-id="0c7c3-116">**Count**</span><span class="sxs-lookup"><span data-stu-id="0c7c3-116">**Count**</span></span>  
 <span data-ttu-id="0c7c3-117">針對所有空白欄位，計算並重新填入 [估計計數]\*\*\*\* 資料行的值。</span><span class="sxs-lookup"><span data-stu-id="0c7c3-117">Calculates and repopulates the values in the **Estimated count** column for all empty fields.</span></span> <span data-ttu-id="0c7c3-118">已經顯示計數的欄位不會更新。</span><span class="sxs-lookup"><span data-stu-id="0c7c3-118">Fields that already display a count are not updated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c7c3-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c7c3-119">See Also</span></span>  
 <span data-ttu-id="0c7c3-120">[匯總設計嚮導 F1 說明](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="0c7c3-120">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="0c7c3-121">Analysis Services 的 &#40;多維度資料的嚮導&#41;</span><span class="sxs-lookup"><span data-stu-id="0c7c3-121">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
