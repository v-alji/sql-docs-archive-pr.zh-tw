---
title: 維度 (Analysis Services 多維資料) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- OLAP objects [Analysis Services], dimensions
- dimensions [Analysis Services]
- Analysis Services objects, dimensions
ms.assetid: 2b114135-2572-4479-8c81-3ccf0cfeb9f7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e0e15d4f74c2c6cec06edaf692199e48534c7e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706877"
---
# <a name="dimensions-analysis-services---multidimensional-data"></a><span data-ttu-id="21b9b-102">維度 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="21b9b-102">Dimensions (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="21b9b-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，維度是 cube 的基礎元件。</span><span class="sxs-lookup"><span data-stu-id="21b9b-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], dimensions are a fundamental component of cubes.</span></span> <span data-ttu-id="21b9b-104">維度會以使用者希望了解的領域來組織資料，例如客戶、商店或員工。</span><span class="sxs-lookup"><span data-stu-id="21b9b-104">Dimensions organize data with relation to an area of interest, such as customers, stores, or employees, to users.</span></span> <span data-ttu-id="21b9b-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的維度包含對應到維度資料表中之資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="21b9b-105">Dimensions in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contain attributes that correspond to columns in dimension tables.</span></span> <span data-ttu-id="21b9b-106">這些屬性會顯示為屬性階層，並可以組成使用者自訂階層，也可以根據基礎維度資料表中的資料行定義為父子式階層。</span><span class="sxs-lookup"><span data-stu-id="21b9b-106">These attributes appear as attribute hierarchies and can be organized into user-defined hierarchies, or can be defined as parent-child hierarchies based on columns in the underlying dimension table.</span></span> <span data-ttu-id="21b9b-107">這些階層會用於組織包含在 Cube 中的量值。</span><span class="sxs-lookup"><span data-stu-id="21b9b-107">Hierarchies are used to organize measures that are contained in a cube.</span></span> <span data-ttu-id="21b9b-108">下列主題提供維度、屬性以及階層的概觀。</span><span class="sxs-lookup"><span data-stu-id="21b9b-108">The following topics provide an overview of dimensions, attributes, and hierarchies.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="21b9b-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="21b9b-109">In This Section</span></span>  
  
|<span data-ttu-id="21b9b-110">主題</span><span class="sxs-lookup"><span data-stu-id="21b9b-110">Topic</span></span>|<span data-ttu-id="21b9b-111">描述</span><span class="sxs-lookup"><span data-stu-id="21b9b-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="21b9b-112">維度簡介 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="21b9b-112">Introduction to Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimensions-analysis-services-multidimensional-data.md)|<span data-ttu-id="21b9b-113">提供維度概念的概觀。</span><span class="sxs-lookup"><span data-stu-id="21b9b-113">Provides an overview of dimension concepts.</span></span>|  
|[<span data-ttu-id="21b9b-114">屬性和屬性階層</span><span class="sxs-lookup"><span data-stu-id="21b9b-114">Attributes and Attribute Hierarchies</span></span>](attributes-and-attribute-hierarchies.md)|<span data-ttu-id="21b9b-115">描述屬性和屬性階層。</span><span class="sxs-lookup"><span data-stu-id="21b9b-115">Describes attributes and attribute hierarchies.</span></span>|  
|[<span data-ttu-id="21b9b-116">使用者階層</span><span class="sxs-lookup"><span data-stu-id="21b9b-116">User Hierarchies</span></span>](user-hierarchies.md)|<span data-ttu-id="21b9b-117">描述屬性的使用者自訂階層。</span><span class="sxs-lookup"><span data-stu-id="21b9b-117">Describes user-defined hierarchies of attributes.</span></span>|  
|[<span data-ttu-id="21b9b-118">可寫入維度</span><span class="sxs-lookup"><span data-stu-id="21b9b-118">Write-Enabled Dimensions</span></span>](write-enabled-dimensions.md)|<span data-ttu-id="21b9b-119">描述可寫入維度。</span><span class="sxs-lookup"><span data-stu-id="21b9b-119">Describes write-enabled dimensions.</span></span>|  
|[<span data-ttu-id="21b9b-120">維度翻譯</span><span class="sxs-lookup"><span data-stu-id="21b9b-120">Dimension Translations</span></span>](dimension-translations.md)|<span data-ttu-id="21b9b-121">描述維度中繼資料的翻譯。</span><span class="sxs-lookup"><span data-stu-id="21b9b-121">Describes translations of dimension meta data.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21b9b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21b9b-122">See Also</span></span>  
 <span data-ttu-id="21b9b-123">[多維度模型中的維度](../multidimensional-models/dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="21b9b-123">[Dimensions in Multidimensional Models](../multidimensional-models/dimensions-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="21b9b-124">Cube 物件 &#40;Analysis Services 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="21b9b-124">Cube Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
  
