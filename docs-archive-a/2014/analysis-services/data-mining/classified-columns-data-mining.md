---
title: 已分類的資料行 (資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content types [data mining]
- STDEV column
- VARIANCE column
- PROBABLILITY column
- PROBABILITY_STDEV column
- columns [data mining], classified
- classified columns [data mining]
- PROBABILITY_VARIANCE column
- SUPPORT column
ms.assetid: 68bf3b78-dc12-497c-898f-b43a45646123
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c264dfb6a97b8b8f576966e8929f6b0dc51e4ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598680"
---
# <a name="classified-columns-data-mining"></a><span data-ttu-id="f6807-102">分類資料行 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="f6807-102">Classified Columns (Data Mining)</span></span>
  <span data-ttu-id="f6807-103">當您定義分類資料行時，您可以建立目前資料行與採礦結構中另一個資料行之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="f6807-103">When you define a classified column, you create a relationship between the current column and another column in the mining structure.</span></span> <span data-ttu-id="f6807-104">您指定為分類資料行之採礦結構資料行中的資料包含類別目錄的資訊，該資訊描述採礦結構中另一個資料行的值。</span><span class="sxs-lookup"><span data-stu-id="f6807-104">The data in the mining structure column that you designate as the classified column contains categorical information that describes the values in another column in the mining structure.</span></span>  
  
 <span data-ttu-id="f6807-105">例如，假設您有兩個具有數值資料的資料行：其中一個資料行為 [Yearly Purchases]，包含每個客戶在特定日曆年度的每年總購買量；另一個資料行為 [Standard Deviations]，包含這些值的標準差。</span><span class="sxs-lookup"><span data-stu-id="f6807-105">For example, suppose you have two columns with numerical data: one column, [Yearly Purchases], contains the total yearly purchases per customer for a specific calendar year, and the other column, [Standard Deviations], contains the standard deviations for those values.</span></span> <span data-ttu-id="f6807-106">在本例中，您可以將 [Yearly Purchases] 資料行指定為分類資料行，讓模型能夠在分析中使用此關聯性。</span><span class="sxs-lookup"><span data-stu-id="f6807-106">In this case you could designate the [Yearly Purchases] column as the classified column, and the model would be able to use this relationship in analysis.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f6807-107">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中提供的演算法不支援使用分類資料行；此功能是為了用來建立自訂演算法所提供。</span><span class="sxs-lookup"><span data-stu-id="f6807-107">The algorithms provided in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] do not support the use of classified columns; this feature is provided for use in creating custom algorithms.</span></span>  
  
## <a name="defining-a-classified-column"></a><span data-ttu-id="f6807-108">定義分類資料行</span><span class="sxs-lookup"><span data-stu-id="f6807-108">Defining a Classified Column</span></span>  
 <span data-ttu-id="f6807-109">分類資料行的資料類型必須為 `Long` 或 `Double`。</span><span class="sxs-lookup"><span data-stu-id="f6807-109">The data type of a classified column must be either `Long` or `Double`.</span></span>  
  
 <span data-ttu-id="f6807-110">下列清單描述 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 支援的分類資料行之內容類型。</span><span class="sxs-lookup"><span data-stu-id="f6807-110">The following list describes the content types that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supports for classified columns.</span></span>  
  
 <span data-ttu-id="f6807-111">**機率**</span><span class="sxs-lookup"><span data-stu-id="f6807-111">**PROBABILITY**</span></span>  
 <span data-ttu-id="f6807-112">資料行中的值是關聯值的機率，且是介於 0 和 1 之間的數字。</span><span class="sxs-lookup"><span data-stu-id="f6807-112">The value in the column is the probability of the associated value, and is a number between 0 and 1.</span></span>  
  
 <span data-ttu-id="f6807-113">**變化**</span><span class="sxs-lookup"><span data-stu-id="f6807-113">**VARIANCE**</span></span>  
 <span data-ttu-id="f6807-114">資料行中的值是關聯值的變異數。</span><span class="sxs-lookup"><span data-stu-id="f6807-114">The value in the column is the variance of the associated value.</span></span>  
  
 <span data-ttu-id="f6807-115">**STDEV**</span><span class="sxs-lookup"><span data-stu-id="f6807-115">**STDEV**</span></span>  
 <span data-ttu-id="f6807-116">資料行中的值是關聯值的標準差。</span><span class="sxs-lookup"><span data-stu-id="f6807-116">The value in the column is the standard deviation of the associated value.</span></span>  
  
 <span data-ttu-id="f6807-117">**PROBABILITY_VARIANCE**</span><span class="sxs-lookup"><span data-stu-id="f6807-117">**PROBABILITY_VARIANCE**</span></span>  
 <span data-ttu-id="f6807-118">資料行中的值是關聯值之機率的變異數。</span><span class="sxs-lookup"><span data-stu-id="f6807-118">The value in the column is the variance of the probability for the associated value.</span></span>  
  
 <span data-ttu-id="f6807-119">**PROBABILITY_STDEV**</span><span class="sxs-lookup"><span data-stu-id="f6807-119">**PROBABILITY_STDEV**</span></span>  
 <span data-ttu-id="f6807-120">資料行中的值是關聯值之機率的標準差。</span><span class="sxs-lookup"><span data-stu-id="f6807-120">The value in the column is the standard deviation of the probability for the associated value.</span></span>  
  
 <span data-ttu-id="f6807-121">**部門**</span><span class="sxs-lookup"><span data-stu-id="f6807-121">**SUPPORT**</span></span>  
 <span data-ttu-id="f6807-122">資料行中的值是關聯值的加權或案例複寫因數。</span><span class="sxs-lookup"><span data-stu-id="f6807-122">The value in the column is the weight, or case replication factor, of the associated value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6807-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6807-123">See Also</span></span>  
 <span data-ttu-id="f6807-124">[&#40;資料採礦&#41;的內容類型](content-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="f6807-124">[Content Types &#40;Data Mining&#41;](content-types-data-mining.md) </span></span>  
 <span data-ttu-id="f6807-125">[&#40;Analysis Services 的採礦結構-資料採礦&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="f6807-125">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="f6807-126">資料類型 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="f6807-126">Data Types &#40;Data Mining&#41;</span></span>](data-types-data-mining.md)  
  
  
