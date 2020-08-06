---
title: 觀點 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- ready-only cube view
- OLAP objects [Analysis Services], perspectives
- storing data [Analysis Services], perspectives
- perspectives [Analysis Services]
- cubes [Analysis Services], perspectives
- visibility [Analysis Services]
- storage [Analysis Services], perspectives
ms.assetid: b064171e-b1b4-4f32-95e5-59e1b831c4c9
author: minewiskan
ms.author: owend
ms.openlocfilehash: f385fd078500739d97394cd8856fc8bd6a3b87e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702034"
---
# <a name="perspectives"></a><span data-ttu-id="ece01-102">檢視方塊</span><span class="sxs-lookup"><span data-stu-id="ece01-102">Perspectives</span></span>
  <span data-ttu-id="ece01-103">檢視方塊是可讓使用者以更簡單的方式查看 Cube 的定義。</span><span class="sxs-lookup"><span data-stu-id="ece01-103">A perspective is a definition that allows users to see a cube in a simpler way.</span></span> <span data-ttu-id="ece01-104">檢視方塊是 Cube 功能的子集。</span><span class="sxs-lookup"><span data-stu-id="ece01-104">A perspective is a subset of the features of a cube.</span></span> <span data-ttu-id="ece01-105">檢視方塊可讓管理員建立 Cube 的檢視，幫助使用者將焦點放在最相關的資料上。</span><span class="sxs-lookup"><span data-stu-id="ece01-105">A perspective enables administrators to create views of a cube, helping users to focus on the most relevant data for them.</span></span> <span data-ttu-id="ece01-106">檢視方塊包含了 Cube 中所有物件的子集。</span><span class="sxs-lookup"><span data-stu-id="ece01-106">A perspective contains subsets of all objects from a cube.</span></span> <span data-ttu-id="ece01-107">檢視方塊不能包含父 Cube 中未定義的元素。</span><span class="sxs-lookup"><span data-stu-id="ece01-107">A perspective cannot include elements that are not defined in the parent cube.</span></span>  
  
 <span data-ttu-id="ece01-108">簡單的 <xref:Microsoft.AnalysisServices.Perspective> 物件是由以下項目所組成：基本資訊、維度、量值群組、計算、KPI 和動作。</span><span class="sxs-lookup"><span data-stu-id="ece01-108">A simple <xref:Microsoft.AnalysisServices.Perspective> object is composed of: basic information, dimensions, measure groups, calculations, KPIs, and actions.</span></span> <span data-ttu-id="ece01-109">基本資訊包括檢視方塊的名稱和預設量值。</span><span class="sxs-lookup"><span data-stu-id="ece01-109">Basic information includes the name and the default measure of the perspective.</span></span> <span data-ttu-id="ece01-110">維度是 Cube 維度的子集。</span><span class="sxs-lookup"><span data-stu-id="ece01-110">The dimensions are a subset of the cube dimensions.</span></span> <span data-ttu-id="ece01-111">量值群組是 Cube 量值群組的子集。</span><span class="sxs-lookup"><span data-stu-id="ece01-111">The measure groups are a subset of the cube measure groups.</span></span> <span data-ttu-id="ece01-112">計算是 Cube 計算的子集。</span><span class="sxs-lookup"><span data-stu-id="ece01-112">The calculations are a subset of the cube calculations.</span></span> <span data-ttu-id="ece01-113">KPI 是 Cube KPI 的子集。</span><span class="sxs-lookup"><span data-stu-id="ece01-113">The KPIs are a subset of the cube KPIs.</span></span> <span data-ttu-id="ece01-114">動作是 Cube 動作的子集。</span><span class="sxs-lookup"><span data-stu-id="ece01-114">The actions are a subset of the cube actions.</span></span>  
  
 <span data-ttu-id="ece01-115">Cube 必須要先更新及處理，然後才可以使用檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="ece01-115">A cube has to be updated and processed before the perspective can be used.</span></span>  
  
 <span data-ttu-id="ece01-116">Cube 可以是非常複雜的物件，供使用者在中進行探索 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ece01-116">Cubes can be very complex objects for users to explore in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="ece01-117">單一 Cube 可以代表整個資料倉儲的內容，且 Cube 中的多個量值群組代表多份事實資料表，而多個維度的基礎是多份維度資料表。</span><span class="sxs-lookup"><span data-stu-id="ece01-117">A single cube can represent the contents of a complete data warehouse, with multiple measure groups in a cube representing multiple fact tables, and multiple dimensions based on multiple dimension tables.</span></span> <span data-ttu-id="ece01-118">雖然這類 Cube 可以十分複雜且功能強大，但是對只需要與 Cube 的一小部份進行互動以滿足其商業智慧和報表需求的使用者而言，卻令人望而怯步。</span><span class="sxs-lookup"><span data-stu-id="ece01-118">Such a cube can be very complex and powerful, but daunting to users who may only need to interact with a small part of the cube in order to satisfy their business intelligence and reporting requirements.</span></span>  
  
 <span data-ttu-id="ece01-119">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，您可以使用觀點來降低中發現之 cube 的複雜度 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ece01-119">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use a perspective to reduce the perceived complexity of a cube in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="ece01-120">檢視方塊會定義可檢視之 Cube 子集，而這類子集會對 Cube 提供有焦點的商務特有或應用程式特有觀點；</span><span class="sxs-lookup"><span data-stu-id="ece01-120">A perspective defines a viewable subset of a cube that provides focused, business-specific or application-specific viewpoints on the cube.</span></span> <span data-ttu-id="ece01-121">檢視方塊會控制 Cube 所容納之物件的可見性。</span><span class="sxs-lookup"><span data-stu-id="ece01-121">The perspective controls the visibility of objects that are contained by a cube.</span></span> <span data-ttu-id="ece01-122">下列物件可以在檢視方塊中顯示或隱藏：</span><span class="sxs-lookup"><span data-stu-id="ece01-122">The following objects can be displayed or hidden in a perspective:</span></span>  
  
-   <span data-ttu-id="ece01-123">維度</span><span class="sxs-lookup"><span data-stu-id="ece01-123">Dimensions</span></span>  
  
-   <span data-ttu-id="ece01-124">屬性</span><span class="sxs-lookup"><span data-stu-id="ece01-124">Attributes</span></span>  
  
-   <span data-ttu-id="ece01-125">階層</span><span class="sxs-lookup"><span data-stu-id="ece01-125">Hierarchies</span></span>  
  
-   <span data-ttu-id="ece01-126">量值群組</span><span class="sxs-lookup"><span data-stu-id="ece01-126">Measure groups</span></span>  
  
-   <span data-ttu-id="ece01-127">量值</span><span class="sxs-lookup"><span data-stu-id="ece01-127">Measures</span></span>  
  
-   <span data-ttu-id="ece01-128">關鍵效能指標 (KPI)</span><span class="sxs-lookup"><span data-stu-id="ece01-128">Key Performance Indicators (KPIs)</span></span>  
  
-   <span data-ttu-id="ece01-129">計算 (導出成員、命名集和指令碼命令)</span><span class="sxs-lookup"><span data-stu-id="ece01-129">Calculations (calculated members, named sets, and script commands)</span></span>  
  
-   <span data-ttu-id="ece01-130">[動作]</span><span class="sxs-lookup"><span data-stu-id="ece01-130">Actions</span></span>  
  
 <span data-ttu-id="ece01-131">例如，範例資料庫中的「**艾德作品**」 cube [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 包含11個量值群組和二十個不同的 cube 維度，代表銷售、銷售預測和財務資料。</span><span class="sxs-lookup"><span data-stu-id="ece01-131">For example, the **Adventure Works** cube in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database contains eleven measure groups and twenty-one different cube dimensions, representing sales, sales forecasting, and financial data.</span></span> <span data-ttu-id="ece01-132">用戶端應用程式可以直接參考整個 Cube，但是這個觀點對於只想嘗試擷取基本銷售預測資訊的使用者而言可能不適合。</span><span class="sxs-lookup"><span data-stu-id="ece01-132">A client application can directly reference the complete cube, but this viewpoint may be overwhelming to a user trying to extract basic sales forecasting information.</span></span> <span data-ttu-id="ece01-133">相反地，相同的使用者可以使用「**銷售目標**」的觀點，將「**艾德作品**」 cube 的觀點限制為只有與銷售預測相關的物件。</span><span class="sxs-lookup"><span data-stu-id="ece01-133">Instead, the same user can use the **Sales Targets** perspective to limit the view of the **Adventure Works** cube to only those objects relevant to sales forecasting.</span></span>  
  
 <span data-ttu-id="ece01-134">在 Cube 中，使用者無法透過檢視方塊看到的物件，仍可以使用 XML for Analysis (XMLA)、多維度運算式 (MDX) 或資料採礦延伸模組 (DMX) 陳述式直接予以參考和擷取。</span><span class="sxs-lookup"><span data-stu-id="ece01-134">Objects in a cube that are not visible to the user through a perspective can still be directly referenced and retrieved using XML for Analysis (XMLA), Multidimensional Expressions (MDX), or Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="ece01-135">檢視方塊並不會限制 Cube 中物件的存取，而且也不應該這麼做；而檢視方塊是用來提供使用者較佳的 Cube 存取經驗。</span><span class="sxs-lookup"><span data-stu-id="ece01-135">Perspectives do not restrict access to objects in a cube and should not be used as such; instead, perspectives are used to provide a better user experience while accessing a cube.</span></span>  
  
 <span data-ttu-id="ece01-136">檢視方塊是 Cube 的唯讀檢視；使用檢視方塊並無法重新命名或變更 Cube 中的物件。</span><span class="sxs-lookup"><span data-stu-id="ece01-136">A perspective is a read-only view of the cube; objects in the cube cannot be renamed or changed by using a perspective.</span></span> <span data-ttu-id="ece01-137">同樣地，使用檢視方塊也無法變更 Cube 的行為或功能 (例如，使用視覺化總計)。</span><span class="sxs-lookup"><span data-stu-id="ece01-137">Similarly, the behavior or features of a cube, such as the use of visual totals, cannot be changed by using a perspective.</span></span>  
  
## <a name="security"></a><span data-ttu-id="ece01-138">安全性</span><span class="sxs-lookup"><span data-stu-id="ece01-138">Security</span></span>  
 <span data-ttu-id="ece01-139">檢視方塊並非用來作為安全性機制，而是在商業智慧應用程式中提供較佳使用者體驗的工具。</span><span class="sxs-lookup"><span data-stu-id="ece01-139">Perspectives are not meant to be used as a security mechanism, but as a tool for providing a better user experience in business intelligence applications.</span></span> <span data-ttu-id="ece01-140">特定檢視方塊的所有安全性，都是繼承自基礎 Cube。</span><span class="sxs-lookup"><span data-stu-id="ece01-140">All security for a particular perspective is inherited from the underlying cube.</span></span> <span data-ttu-id="ece01-141">例如，如果使用者沒有 Cube 中物件的存取權，則檢視方塊也無法提供該物件的存取權。</span><span class="sxs-lookup"><span data-stu-id="ece01-141">For example, perspectives cannot provide access to objects in a cube to which a user does not already have access.</span></span> <span data-ttu-id="ece01-142">必須先解決 Cube 的安全性，才能透過檢視方塊提供 Cube 中物件的存取權。</span><span class="sxs-lookup"><span data-stu-id="ece01-142">- Security for the cube must be resolved before access to objects in the cube can be provided through a perspective.</span></span>  
  
  
