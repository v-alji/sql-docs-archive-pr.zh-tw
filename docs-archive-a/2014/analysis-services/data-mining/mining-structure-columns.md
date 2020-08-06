---
title: 採礦結構資料行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], structure
- mining structures [Analysis Services], columns
- data sources [Analysis Services], mining structure columns
- columns [data mining], mining structure columns
ms.assetid: 20cbf433-70d1-4b61-a462-41a8435b27b4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0caebfaef9b80be2d8fb5586a061dcccd31981f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598646"
---
# <a name="mining-structure-columns"></a><span data-ttu-id="d4428-102">採礦結構資料行</span><span class="sxs-lookup"><span data-stu-id="d4428-102">Mining Structure Columns</span></span>
  <span data-ttu-id="d4428-103">當您建立採礦結構時會定義採礦結構中的資料行，其方法是選擇外部資料的資料行，然後指定資料如何用於模型化。</span><span class="sxs-lookup"><span data-stu-id="d4428-103">You define the columns in a mining structure when you create the mining structure, by choosing columns of external data and then specifying how the data is to be used for modeling.</span></span> <span data-ttu-id="d4428-104">因此，採礦結構資料行不只是資料來源中的資料複本：這些資料行會定義採礦模型如何使用來源中的資料。</span><span class="sxs-lookup"><span data-stu-id="d4428-104">Therefore, mining structure columns are more than copies of data from a data source: they define how the data from the source is to be used by the mining model.</span></span> <span data-ttu-id="d4428-105">您可以指派可判斷如何將資料離散化的屬性以及可描述如何分佈資料值的屬性。</span><span class="sxs-lookup"><span data-stu-id="d4428-105">You can assign properties that determine how the data is discretized, properties that describe how the data values are distributed</span></span>  
  
 <span data-ttu-id="d4428-106">採礦結構資料行的設計就是要提供彈性和擴充性，因為您用於建立採礦模型的每一個演算法，都可能使用結構中的不同資料行來解譯資料。</span><span class="sxs-lookup"><span data-stu-id="d4428-106">Mining structure columns are designed to be flexible and extensible, because each algorithm that you use to build a mining model may use different columns from the structure to interpret the data.</span></span> <span data-ttu-id="d4428-107">您可以使用單一採礦結構並使用其中的資料行來自訂每一個模型的資料，而不必在每一個模型中都有一組資料。</span><span class="sxs-lookup"><span data-stu-id="d4428-107">Rather than have one set of data for each model, you can use a single mining structure and use the columns in it to customize the data for each model.</span></span>  
  
## <a name="defining-mining-structure-columns"></a><span data-ttu-id="d4428-108">定義採礦結構資料行</span><span class="sxs-lookup"><span data-stu-id="d4428-108">Defining Mining Structure Columns</span></span>  
 <span data-ttu-id="d4428-109">定義結構資料行的基本資料類型和內容類型是衍生自您用於建立結構的資料來源。</span><span class="sxs-lookup"><span data-stu-id="d4428-109">The basic data types and content types that define structure columns are derived from the data source that you use to create the structure.</span></span> <span data-ttu-id="d4428-110">您可以在採礦結構內變更這些設定，也可以設定模型旗標和設定連續資料行的分佈。</span><span class="sxs-lookup"><span data-stu-id="d4428-110">You can change these settings within the mining structure, and you can also set modeling flags and set the distribution for continuous columns.</span></span>  
  
 <span data-ttu-id="d4428-111">採礦結構資料行的定義必須包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="d4428-111">The definition of a mining structure column must contain the following information:</span></span>  
  
-   <span data-ttu-id="d4428-112">**識別碼**：資料行的唯一名稱，通常與名稱相同。</span><span class="sxs-lookup"><span data-stu-id="d4428-112">**ID**: The unique name of the column, often the same as the name.</span></span> <span data-ttu-id="d4428-113">在您建立採礦結構之後無法變更識別碼，但是可以變更名稱。</span><span class="sxs-lookup"><span data-stu-id="d4428-113">This cannot be changed after you create the mining structure, whereas the name can be changed.</span></span>  
  
-   <span data-ttu-id="d4428-114">**名稱**：資料行的名稱或別名。</span><span class="sxs-lookup"><span data-stu-id="d4428-114">**Name**: A name or alias for the column.</span></span>  
  
-   <span data-ttu-id="d4428-115">**內容**：描述資料為離散或連續的列舉。</span><span class="sxs-lookup"><span data-stu-id="d4428-115">**Content**: An enumeration that describes whether the data is discrete or continuous.</span></span>  
  
-   <span data-ttu-id="d4428-116">**類型**：表示一般資料類型的列舉。</span><span class="sxs-lookup"><span data-stu-id="d4428-116">**Type**: An enumeration that indicates the general data type.</span></span>  
  
-   <span data-ttu-id="d4428-117">**分佈**：描述預期之值分佈的列舉。</span><span class="sxs-lookup"><span data-stu-id="d4428-117">**Distribution**: An enumeration that describes the expected distribution of values.</span></span> <span data-ttu-id="d4428-118">如果資料行是連續的，便包括分佈。</span><span class="sxs-lookup"><span data-stu-id="d4428-118">A distribution is included if the column is continuous.</span></span>  
  
-   <span data-ttu-id="d4428-119">**模型旗標**：表示如何處理遺失值等項目的列舉。</span><span class="sxs-lookup"><span data-stu-id="d4428-119">**Modeling flags**: An enumeration that indicates how to handle missing values and so forth.</span></span> <span data-ttu-id="d4428-120">也可以在採礦模型上定義模型旗標，但是這些模型旗標與結構資料行上使用的旗標不一樣。</span><span class="sxs-lookup"><span data-stu-id="d4428-120">Modeling flags can also be defined on the mining model, but the model flags are different than the flags used on structure columns.</span></span>  
  
-   <span data-ttu-id="d4428-121">**繫結**：指定來源資料的屬性。</span><span class="sxs-lookup"><span data-stu-id="d4428-121">**Bindings**: Properties that specify the source data.</span></span>  
  
 <span data-ttu-id="d4428-122">協力廠商演算法也可以包括可在採礦結構資料行上定義的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="d4428-122">Third-party algorithms may also include custom properties that can be defined on the mining structure column.</span></span>  
  
 <span data-ttu-id="d4428-123">如需資料採礦結構和資料採礦模型的詳細資訊，請參閱 [採礦結構 &#40;Analysis Services - 資料採礦&#41;](mining-structures-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="d4428-123">For more information about the data mining structure and the data mining model, see [Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="d4428-124">相關內容</span><span class="sxs-lookup"><span data-stu-id="d4428-124">Related Content</span></span>  
 <span data-ttu-id="d4428-125">如需有關如何定義及使用採礦結構資料行的詳細資訊，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="d4428-125">See the following topics for more information about how to define and use mining structure columns.</span></span>  
  
|<span data-ttu-id="d4428-126">主題</span><span class="sxs-lookup"><span data-stu-id="d4428-126">Topic</span></span>|<span data-ttu-id="d4428-127">連結</span><span class="sxs-lookup"><span data-stu-id="d4428-127">Links</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="d4428-128">描述您可以用於定義採礦結構資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d4428-128">Describes the data types that you can use to define a mining structure column.</span></span>|[<span data-ttu-id="d4428-129">資料類型 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="d4428-129">Data Types &#40;Data Mining&#41;</span></span>](data-types-data-mining.md)|  
|<span data-ttu-id="d4428-130">描述可供採礦結構資料行內包含之每一個資料類型使用的內容類型。</span><span class="sxs-lookup"><span data-stu-id="d4428-130">Describes the content types that are available for each type of data that is contained in a mining structure column.</span></span> <span data-ttu-id="d4428-131">內容類型相依於資料類型。</span><span class="sxs-lookup"><span data-stu-id="d4428-131">Content types are dependent on data type.</span></span> <span data-ttu-id="d4428-132">內容類型會在模型層級指派，而且會決定模型使用資料行資料的方式。</span><span class="sxs-lookup"><span data-stu-id="d4428-132">The content type is assigned at the model level, and determines how the column data is used by the model.</span></span>|[<span data-ttu-id="d4428-133">內容類型 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="d4428-133">Content Types &#40;Data Mining&#41;</span></span>](content-types-data-mining.md)|  
|<span data-ttu-id="d4428-134">介紹巢狀資料表的概念，並說明如何將巢狀資料表當做採礦結構資料行加入至資料來源。</span><span class="sxs-lookup"><span data-stu-id="d4428-134">Introduces the concept of nested tables, and explains how nested tables can be added to the data source as mining structure columns.</span></span>|[<span data-ttu-id="d4428-135">分類資料行 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="d4428-135">Classified Columns &#40;Data Mining&#41;</span></span>](classified-columns-data-mining.md)|  
|<span data-ttu-id="d4428-136">列出並說明您可以在採礦結構資料行上設定的分佈屬性，以便指定資料行中預期的值分佈。</span><span class="sxs-lookup"><span data-stu-id="d4428-136">Lists and explains the distribution properties that you can set on a mining structure column to specify the expected distribution of values in the column.</span></span>|[<span data-ttu-id="d4428-137">資料行分佈 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="d4428-137">Column Distributions &#40;Data Mining&#41;</span></span>](column-distributions-data-mining.md)|  
|<span data-ttu-id="d4428-138">說明分隔 (有時稱為「資料收納」\*\*) 的概念，並描述 Analysis Services 為分隔連續數值資料所提供的方法。</span><span class="sxs-lookup"><span data-stu-id="d4428-138">Explains the concept of discretization (sometimes referred to as *binning*) and describes the methods that Analysis Services provides for discretizing continuous numeric data.</span></span>|[<span data-ttu-id="d4428-139">分隔方法 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="d4428-139">Discretization Methods &#40;Data Mining&#41;</span></span>](discretization-methods-data-mining.md)|  
|<span data-ttu-id="d4428-140">描述您可以在採礦結構資料行上設定的模型旗標。</span><span class="sxs-lookup"><span data-stu-id="d4428-140">Describes the modeling flags that you can set on a mining structure column.</span></span>|[<span data-ttu-id="d4428-141">模型旗標 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="d4428-141">Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)|  
|<span data-ttu-id="d4428-142">描述分類資料行，這是一種特殊類型的資料行，可用來讓採礦結構資料行之間產生關聯。</span><span class="sxs-lookup"><span data-stu-id="d4428-142">Describes classified columns, which are a special type of column that you can use to relate one mining structure column to another.</span></span>|[<span data-ttu-id="d4428-143">分類資料行 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="d4428-143">Classified Columns &#40;Data Mining&#41;</span></span>](classified-columns-data-mining.md)|  
|<span data-ttu-id="d4428-144">學習加入及修改採礦結構資料行。</span><span class="sxs-lookup"><span data-stu-id="d4428-144">Learn to add and modify mining structure columns.</span></span>|[<span data-ttu-id="d4428-145">採礦結構工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="d4428-145">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)|  
  
## <a name="see-also"></a><span data-ttu-id="d4428-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4428-146">See Also</span></span>  
 <span data-ttu-id="d4428-147">[&#40;Analysis Services 的採礦結構-資料採礦&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="d4428-147">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="d4428-148">採礦模型資料行</span><span class="sxs-lookup"><span data-stu-id="d4428-148">Mining Model Columns</span></span>](mining-model-columns.md)  
  
  
