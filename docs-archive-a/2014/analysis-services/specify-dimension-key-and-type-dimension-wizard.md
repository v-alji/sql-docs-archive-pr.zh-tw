---
title: 指定維度索引鍵和類型 (維度 Wizard) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionkeyandtype.f1
ms.assetid: d7d5db55-36c3-45f6-ade3-29aa516589c1
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc08584ed12de8597b8289fd223cc47945d7d087
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598565"
---
# <a name="specify-dimension-key-and-type-dimension-wizard"></a><span data-ttu-id="e7fc1-102">指定維度索引鍵和類型 (維度精靈)</span><span class="sxs-lookup"><span data-stu-id="e7fc1-102">Specify Dimension Key and Type (Dimension Wizard)</span></span>
  <span data-ttu-id="e7fc1-103">使用 [指定維度索引鍵和類型]\*\*\*\* 頁面，即可定義維度的索引鍵屬性，並表示維度是否為緩時變維度 (SCD)。</span><span class="sxs-lookup"><span data-stu-id="e7fc1-103">Use the **Specify Dimension Key and Type** page to define the key attribute of the dimension and to indicate whether the dimension is a slowly changing dimension (SCD).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7fc1-104">唯有選取了 [選取建立方法]\*\*\*\* 頁面上的 [Build the dimension without using a data source (不使用資料來源而建立維度)]\*\*\*\*，以及選取了 [選取維度類型]\*\*\*\* 頁面上的 [標準維度]\*\*\*\* 之後，才會顯示此頁面。</span><span class="sxs-lookup"><span data-stu-id="e7fc1-104">This page is displayed only if you selected **Build the dimension without using a data source** on the **Select Build Method** page and if you selected **Standard dimension** on the **Select the Dimension Type** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e7fc1-105">選項</span><span class="sxs-lookup"><span data-stu-id="e7fc1-105">Options</span></span>  
 <span data-ttu-id="e7fc1-106">**索引鍵屬性**</span><span class="sxs-lookup"><span data-stu-id="e7fc1-106">**Key attribute**</span></span>  
 <span data-ttu-id="e7fc1-107">選取會成為維度之索引鍵屬性的屬性。</span><span class="sxs-lookup"><span data-stu-id="e7fc1-107">Select the attribute that will be the key attribute for the dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7fc1-108">如果未針對維度定義任何屬性，此選項唯一可用的值就是 [自動建立索引鍵屬性。]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e7fc1-108">If no attributes have been defined for the dimension, the only value available for this option is **Create key attribute automatically.**</span></span> <span data-ttu-id="e7fc1-109">如果針對維度定義了任何屬性，此值就不可以使用。</span><span class="sxs-lookup"><span data-stu-id="e7fc1-109">This value is not available if any attributes are defined for the dimension.</span></span>  
  
 <span data-ttu-id="e7fc1-110">**這是變更維度**</span><span class="sxs-lookup"><span data-stu-id="e7fc1-110">**This is a changing dimension**</span></span>  
 <span data-ttu-id="e7fc1-111">選取以表示維度是緩時變維度。</span><span class="sxs-lookup"><span data-stu-id="e7fc1-111">Select to indicate that the dimension is a slowly changing dimension.</span></span> <span data-ttu-id="e7fc1-112">選取此選項會建立其他的資料行和屬性，而這些資料行和屬性可用來長時間追蹤成員在維度階層內的移動。</span><span class="sxs-lookup"><span data-stu-id="e7fc1-112">Selecting this option will create additional columns and attributes that can be used to track the movement of members within the hierarchies of the dimension over time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7fc1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7fc1-113">See Also</span></span>  
 <span data-ttu-id="e7fc1-114">[維度嚮導 F1 說明](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="e7fc1-114">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="e7fc1-115">[維度 &#40;Analysis Services 多維資料&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="e7fc1-115">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="e7fc1-116">多維度模型中的維度</span><span class="sxs-lookup"><span data-stu-id="e7fc1-116">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
