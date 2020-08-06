---
title: " (匯總設計嚮導指定物件計數) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.calculatingobjectcounts.f1
ms.assetid: 305d9d79-d1ab-4704-a7b5-3283842b3996
author: minewiskan
ms.author: owend
ms.openlocfilehash: c66b972395f86746b2d08df234db8aa0c71d03fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597385"
---
# <a name="specify-object-counts-aggregation-design-wizard"></a><span data-ttu-id="66406-102">指定物件計數 (彙總設計精靈)</span><span class="sxs-lookup"><span data-stu-id="66406-102">Specify Object Counts (Aggregation Design Wizard)</span></span>
  <span data-ttu-id="66406-103">使用 **[指定物件計數]** 頁面，即可自動計算 Cube 中的物件計數，或者手動輸入估計的計數。</span><span class="sxs-lookup"><span data-stu-id="66406-103">Use the **Specify Object Counts** page to automatically calculate the count of objects in the cube or to manually enter estimated counts.</span></span> <span data-ttu-id="66406-104">「彙總設計精靈」會使用物件計數來估計儲存需求。</span><span class="sxs-lookup"><span data-stu-id="66406-104">The Aggregation Design Wizard uses the object counts to estimate storage requirements.</span></span>  
  
## <a name="options"></a><span data-ttu-id="66406-105">選項</span><span class="sxs-lookup"><span data-stu-id="66406-105">Options</span></span>  
 <span data-ttu-id="66406-106">**Cube 物件**</span><span class="sxs-lookup"><span data-stu-id="66406-106">**Cube Objects**</span></span>  
 <span data-ttu-id="66406-107">顯示 Cube 中的維度及屬性。</span><span class="sxs-lookup"><span data-stu-id="66406-107">Displays the dimensions and attributes in the cube.</span></span> <span data-ttu-id="66406-108">在 `AggregationUsage` `None` wizard 的 [**審核匯總使用**方式] 頁面中，只有未將其屬性設定為的屬性會顯示出來，因為這些屬性是唯一需要指定計數的屬性。</span><span class="sxs-lookup"><span data-stu-id="66406-108">Only the attributes that do not have their `AggregationUsage` property set to `None` in the **Review Aggregation Usage** page of the wizard are shown, because those are the only attributes that require the counts to be specified.</span></span>  
  
 <span data-ttu-id="66406-109">**估計計數**</span><span class="sxs-lookup"><span data-stu-id="66406-109">**Estimated count**</span></span>  
 <span data-ttu-id="66406-110">顯示量值群組中估計的資料列數目以及資料庫維度中估計的屬性成員計數。</span><span class="sxs-lookup"><span data-stu-id="66406-110">Displays the estimated number of rows in the measure group and the estimated attribute member counts in the database dimensions.</span></span> <span data-ttu-id="66406-111">您可以輸入要當做估計計數使用的值，也可以計算估計計數的值。</span><span class="sxs-lookup"><span data-stu-id="66406-111">You can type a value to use as the estimated count or you can calculate the estimated count values.</span></span> <span data-ttu-id="66406-112">若要計算計數值，請 `0` 在欄位中輸入，然後按一下 [**計數**]。</span><span class="sxs-lookup"><span data-stu-id="66406-112">To calculate the count values, type `0` in the field and then click **Count**.</span></span> <span data-ttu-id="66406-113">已經顯示計數的欄位不會更新。</span><span class="sxs-lookup"><span data-stu-id="66406-113">Fields that already display a count are not updated.</span></span>  
  
 <span data-ttu-id="66406-114">**分割計數**</span><span class="sxs-lookup"><span data-stu-id="66406-114">**Partition count**</span></span>  
 <span data-ttu-id="66406-115">(選擇性) 輸入量值群組中估計的資料列數目並輸入資料分割中估計的屬性成員計數。</span><span class="sxs-lookup"><span data-stu-id="66406-115">(Optional) Type the estimated number of rows in the measure group and type the estimated attribute member counts in the partitions.</span></span>  
  
 <span data-ttu-id="66406-116">**Count**</span><span class="sxs-lookup"><span data-stu-id="66406-116">**Count**</span></span>  
 <span data-ttu-id="66406-117">針對所有空白欄位，計算並重新填入 [估計計數]\*\*\*\* 資料行的值。</span><span class="sxs-lookup"><span data-stu-id="66406-117">Calculates and repopulates the values in the **Estimated count** column for all empty fields.</span></span> <span data-ttu-id="66406-118">已經顯示計數的欄位不會更新。</span><span class="sxs-lookup"><span data-stu-id="66406-118">Fields that already display a count are not updated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66406-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66406-119">See Also</span></span>  
 <span data-ttu-id="66406-120">[匯總設計嚮導 F1 說明](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="66406-120">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="66406-121">Analysis Services 的 &#40;多維度資料的嚮導&#41;</span><span class="sxs-lookup"><span data-stu-id="66406-121">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
