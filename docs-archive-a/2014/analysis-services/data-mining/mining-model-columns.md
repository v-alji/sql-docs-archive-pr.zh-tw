---
title: 採礦模型資料行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], mining model columns
- columns [data mining]
- REGRESSOR column
- columns [data mining], modeling flags
- modeling flags [data mining]
- MODEL_EXISTENCE_ONLY column
- usage property [data mining]
ms.assetid: fab47643-5bfd-424e-a0f7-69e665db6bab
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f936f3f4e0b8f65326e9a6e84f75e6f4e82657f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700498"
---
# <a name="mining-model-columns"></a><span data-ttu-id="ceff6-102">採礦模型資料行</span><span class="sxs-lookup"><span data-stu-id="ceff6-102">Mining Model Columns</span></span>
  <span data-ttu-id="ceff6-103">資料採礦模型會將採礦模型演算法套用至以採礦結構表示的資料。</span><span class="sxs-lookup"><span data-stu-id="ceff6-103">A data mining model applies a mining model algorithm to the data that is represented by a mining structure.</span></span> <span data-ttu-id="ceff6-104">與採礦結構相同，採礦模型也會包含資料行。</span><span class="sxs-lookup"><span data-stu-id="ceff6-104">Like the mining structure, the mining model contains columns.</span></span> <span data-ttu-id="ceff6-105">採礦模型包含在採礦結構內，且繼承採礦結構所定義的所有屬性值。</span><span class="sxs-lookup"><span data-stu-id="ceff6-105">A mining model is contained within the mining structure, and inherits all the values of the properties that are defined by the mining structure.</span></span> <span data-ttu-id="ceff6-106">此模型可以使用採礦結構包含的所有資料行或資料行子集。</span><span class="sxs-lookup"><span data-stu-id="ceff6-106">The model can use all the columns that the mining structure contains or a subset of the columns.</span></span>  
  
 <span data-ttu-id="ceff6-107">您可以在採礦模型資料行上定義兩項額外資訊：使用方式和模型旗標。</span><span class="sxs-lookup"><span data-stu-id="ceff6-107">You can define two additional pieces of information on a mining model column: usage, and modeling flags.</span></span>  
  
-   <span data-ttu-id="ceff6-108">**使用方式** 是定義模型如何使用資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="ceff6-108">**Usage** is a property that defines how the model uses the column.</span></span> <span data-ttu-id="ceff6-109">資料行可以做為輸入資料行、索引鍵資料行或可預測資料行使用。</span><span class="sxs-lookup"><span data-stu-id="ceff6-109">Columns can be used as input columns, key columns, or predictable columns.</span></span>  
  
-   <span data-ttu-id="ceff6-110">**模型旗標** 為演算法提供額外的資訊，說明案例資料表中所定義的資料，使演算法可以建立更精確的模型。</span><span class="sxs-lookup"><span data-stu-id="ceff6-110">**Modeling flags** provide the algorithm with additional information about the data that is defined in the case table, so that the algorithm can build a more accurate model.</span></span> <span data-ttu-id="ceff6-111">您可以使用資料採礦延伸模組 (DMX) 語言以程式設計方式定義模型旗標，或在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的 [資料採礦設計師]\*\*\*\* 中定義。</span><span class="sxs-lookup"><span data-stu-id="ceff6-111">You can define modeling flags programmatically by using the Data Mining Extensions (DMX) language, or in **Data Mining Designer** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="ceff6-112">下列清單描述您在採礦模型資料行上可以定義的模型旗標。</span><span class="sxs-lookup"><span data-stu-id="ceff6-112">The following list describes the modeling flags that you can define on a mining model column.</span></span>  
  
 `MODEL_EXISTENCE_ONLY`  
 <span data-ttu-id="ceff6-113">指出屬性是否出現比屬性資料行中的值更重要。</span><span class="sxs-lookup"><span data-stu-id="ceff6-113">Indicates that the presence of the attribute is more important than the values that are in the attribute column.</span></span> <span data-ttu-id="ceff6-114">例如，假設案例資料表包含與特定客戶相關聯的訂購項目清單。</span><span class="sxs-lookup"><span data-stu-id="ceff6-114">For example, consider a case table that contains a list of order items that are associated with a particular customer.</span></span> <span data-ttu-id="ceff6-115">資料表資料包含每一個項目的產品類型、識別碼以及成本。</span><span class="sxs-lookup"><span data-stu-id="ceff6-115">The table data includes the product type, ID, and cost of each item.</span></span> <span data-ttu-id="ceff6-116">針對模型的用途而言，客戶購買特定訂購項目的事實可能比訂購項目本身的成本更重要。</span><span class="sxs-lookup"><span data-stu-id="ceff6-116">For modeling purposes, the fact that the customer purchased a particular order item may be more important than the cost of the order item itself.</span></span> <span data-ttu-id="ceff6-117">在此情況下，成本資料行應該標示為 `MODEL_EXISTENCE_ONLY`。</span><span class="sxs-lookup"><span data-stu-id="ceff6-117">In this case, the cost column should be marked as `MODEL_EXISTENCE_ONLY`.</span></span>  
  
 `REGRESSOR`  
 <span data-ttu-id="ceff6-118">指示演算法可以在迴歸演算法的迴歸公式中使用指定的資料行。</span><span class="sxs-lookup"><span data-stu-id="ceff6-118">Indicates that the algorithm can use the specified column in the regression formula of regression algorithms.</span></span> <span data-ttu-id="ceff6-119">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 決策樹和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時間序列演算法支援此旗標。</span><span class="sxs-lookup"><span data-stu-id="ceff6-119">This flag is supported by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithms.</span></span>  
  
 <span data-ttu-id="ceff6-120">如需使用 DMX 以程式設計方式設定 Usage 屬性以及定義模型旗標的詳細資訊，請參閱 [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx)。</span><span class="sxs-lookup"><span data-stu-id="ceff6-120">For more information about setting the usage property and defining modeling flags programmatically with DMX, see [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).</span></span> <span data-ttu-id="ceff6-121">如需在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中設定 Usage 屬性以及定義模型旗標的詳細資訊，請參閱 [移動資料採礦物件](moving-data-mining-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="ceff6-121">For more information about setting the usage property and defining modeling flags in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], see [Moving Data Mining Objects](moving-data-mining-objects.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceff6-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ceff6-122">See Also</span></span>  
 <span data-ttu-id="ceff6-123">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="ceff6-123">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="ceff6-124">[&#40;Analysis Services 的採礦結構-資料採礦&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="ceff6-124">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="ceff6-125">[變更採礦模型的屬性](change-the-properties-of-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="ceff6-125">[Change the Properties of a Mining Model](change-the-properties-of-a-mining-model.md) </span></span>  
 <span data-ttu-id="ceff6-126">[從採礦模型中排除資料行](exclude-a-column-from-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="ceff6-126">[Exclude a Column from a Mining Model](exclude-a-column-from-a-mining-model.md) </span></span>  
 [<span data-ttu-id="ceff6-127">採礦結構資料行</span><span class="sxs-lookup"><span data-stu-id="ceff6-127">Mining Structure Columns</span></span>](mining-structure-columns.md)  
  
  
