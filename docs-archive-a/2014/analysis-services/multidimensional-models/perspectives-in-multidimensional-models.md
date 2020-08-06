---
title: 多維度模型中的觀點 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- default members
- hiding objects from perspective
- renaming perspectives
- attributes [Analysis Services], default members
- removing perspectives
- perspectives [Analysis Services]
- names [Analysis Services], perspectives
- cubes [Analysis Services], perspectives
- deleting perspectives
ms.assetid: 5a3d6577-6833-4c24-820c-b65bb856157b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2d4be87ddbd691710b361d8b07d225bce37659fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593652"
---
# <a name="perspectives-in-multidimensional-models"></a><span data-ttu-id="4c57f-102">多維度模型中的檢視方塊</span><span class="sxs-lookup"><span data-stu-id="4c57f-102">Perspectives in Multidimensional Models</span></span>
  <span data-ttu-id="4c57f-103">檢視方塊是針對特定應用程式或使用者的群組所建立之 Cube 的子集。</span><span class="sxs-lookup"><span data-stu-id="4c57f-103">A perspective is a subset of a cube created for a particular application or group of users.</span></span> <span data-ttu-id="4c57f-104">Cube 本身是預設檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="4c57f-104">The cube itself is the default perspective.</span></span> <span data-ttu-id="4c57f-105">檢視方塊會以 Cube 的形式向用戶端公開。</span><span class="sxs-lookup"><span data-stu-id="4c57f-105">A perspective is exposed to a client as a cube.</span></span> <span data-ttu-id="4c57f-106">檢視方塊在使用者檢視時，會顯示成另一個 Cube 的樣子。</span><span class="sxs-lookup"><span data-stu-id="4c57f-106">When a user views a perspective, it appears like another cube.</span></span> <span data-ttu-id="4c57f-107">透過在檢視方塊中回寫，對 Cube 資料所做的任何變更，都是對原始 Cube 的變更。</span><span class="sxs-lookup"><span data-stu-id="4c57f-107">Any changes made to cube data through writeback in the perspective are to the original cube.</span></span> <span data-ttu-id="4c57f-108">如需 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中之檢視的詳細資訊，請參閱 [檢視方塊](../multidimensional-models-olap-logical-cube-objects/perspectives.md)。</span><span class="sxs-lookup"><span data-stu-id="4c57f-108">For more information about the views in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], see [Perspectives](../multidimensional-models-olap-logical-cube-objects/perspectives.md).</span></span>  
  
 <span data-ttu-id="4c57f-109">使用 Cube 設計師中的 [檢視方塊]\*\*\*\* 索引標籤，即可建立或修改 Cube 中的檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="4c57f-109">Use the **Perspectives** tab in Cube Designer to create or modify perspectives in a cube.</span></span> <span data-ttu-id="4c57f-110">[檢視方塊]\*\*\*\* 索引標籤的第一個資料行是 [Cube 物件]\*\*\*\* 資料行，會列出 Cube 中的所有物件。</span><span class="sxs-lookup"><span data-stu-id="4c57f-110">The first column of the **Perspectives** tab is the **Cube Objects** column, which lists all the objects in the cube.</span></span> <span data-ttu-id="4c57f-111">這會對應到 Cube 的預設檢視方塊，也就是 Cube 本身。</span><span class="sxs-lookup"><span data-stu-id="4c57f-111">This corresponds to the default perspective for the cube, which is the cube itself.</span></span>  
  
## <a name="creating-or-deleting-perspectives"></a><span data-ttu-id="4c57f-112">建立或刪除檢視方塊</span><span class="sxs-lookup"><span data-stu-id="4c57f-112">Creating or Deleting Perspectives</span></span>  
 <span data-ttu-id="4c57f-113">您可以按一下 [Cube]\*\*\*\* 功能表上的 [新增檢視方塊]\*\*\*\*，將檢視方塊加入 [檢視方塊]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="4c57f-113">You can add a perspective to the **Perspectives** tab by clicking **New Perspective** on the **Cube** menu.</span></span> <span data-ttu-id="4c57f-114">您也可以按一下工具列上的 [新增檢視方塊]\*\*\*\* 按鈕，或者以滑鼠右鍵按一下窗格中的任何位置，然後按一下捷徑功能表上的 [新增檢視方塊]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c57f-114">You can also click the **New Perspective** button on the toolbar, or right-click anywhere in the pane and click **New Perspective** on the shortcut menu.</span></span> <span data-ttu-id="4c57f-115">您可以將任意數量的檢視方塊加入至 Cube。</span><span class="sxs-lookup"><span data-stu-id="4c57f-115">You can add any number of perspectives to a cube.</span></span>  
  
 <span data-ttu-id="4c57f-116">若要移除檢視方塊，請先按一下要刪除之檢視方塊的資料行裡任一個資料格。</span><span class="sxs-lookup"><span data-stu-id="4c57f-116">To remove a perspective, first click any cell in the column for the perspective that you want to delete.</span></span> <span data-ttu-id="4c57f-117">然後，在 [Cube]\*\*\*\* 功能表上，按一下 [刪除檢視方塊]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c57f-117">Then, on the **Cube** menu, click **Delete Perspective**.</span></span> <span data-ttu-id="4c57f-118">您也可以按一下工具列上的 [刪除檢視方塊]\*\*\*\* 按鈕，或者以滑鼠右鍵按一下要刪除之檢視方塊中的任一個資料格，然後按一下捷徑功能表上的 [刪除檢視方塊]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c57f-118">You can also click the **Delete Perspective** button on the toolbar, or right-click any cell in the perspective you want to delete, and then click **Delete Perspective** on the shortcut menu.</span></span>  
  
## <a name="renaming-perspectives"></a><span data-ttu-id="4c57f-119">重新命名檢視方塊</span><span class="sxs-lookup"><span data-stu-id="4c57f-119">Renaming Perspectives</span></span>  
 <span data-ttu-id="4c57f-120">每個檢視方塊的第一個資料列會顯示它的名稱。</span><span class="sxs-lookup"><span data-stu-id="4c57f-120">The first row of each perspective shows its name.</span></span> <span data-ttu-id="4c57f-121">您建立檢視方塊時，初始的名稱為 Perspective (如果已經有名為 Perspective 的檢視方塊，則會在後面加上序號，從 1 開始)。</span><span class="sxs-lookup"><span data-stu-id="4c57f-121">When you create a perspective, the name is initially Perspective (followed by an ordinal number, starting with 1, if there is already a perspective called Perspective).</span></span> <span data-ttu-id="4c57f-122">您可以按一下名稱，來編輯檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="4c57f-122">You can click the name to edit it.</span></span>  
  
## <a name="hiding-objects-from-a-perspective"></a><span data-ttu-id="4c57f-123">隱藏檢視方塊中的物件</span><span class="sxs-lookup"><span data-stu-id="4c57f-123">Hiding Objects from a Perspective</span></span>  
 <span data-ttu-id="4c57f-124">若要隱藏檢視方塊中的物件，請清除資料列中的核取方塊，該資料列會對應到檢視方塊之資料行中的物件。</span><span class="sxs-lookup"><span data-stu-id="4c57f-124">To hide an object from a perspective, clear the check box in the row that corresponds to the object in the column for the perspective.</span></span> <span data-ttu-id="4c57f-125">可以在檢視方塊中隱藏的 Cube 物件如下：</span><span class="sxs-lookup"><span data-stu-id="4c57f-125">The cube objects that can be hidden from a perspective are:</span></span>  
  
-   <span data-ttu-id="4c57f-126">量值群組</span><span class="sxs-lookup"><span data-stu-id="4c57f-126">Measure groups</span></span>  
  
-   <span data-ttu-id="4c57f-127">量值</span><span class="sxs-lookup"><span data-stu-id="4c57f-127">Measures</span></span>  
  
-   <span data-ttu-id="4c57f-128">維度</span><span class="sxs-lookup"><span data-stu-id="4c57f-128">Dimensions</span></span>  
  
-   <span data-ttu-id="4c57f-129">階層</span><span class="sxs-lookup"><span data-stu-id="4c57f-129">Hierarchies</span></span>  
  
-   <span data-ttu-id="4c57f-130">命名集</span><span class="sxs-lookup"><span data-stu-id="4c57f-130">Named sets</span></span>  
  
-   <span data-ttu-id="4c57f-131">KPI</span><span class="sxs-lookup"><span data-stu-id="4c57f-131">KPIs</span></span>  
  
-   <span data-ttu-id="4c57f-132">動作</span><span class="sxs-lookup"><span data-stu-id="4c57f-132">Actions</span></span>  
  
-   <span data-ttu-id="4c57f-133">導出成員</span><span class="sxs-lookup"><span data-stu-id="4c57f-133">Calculated members</span></span>  
  
 <span data-ttu-id="4c57f-134">若要檢視任何物件，請展開 [Cube 物件]\*\*\*\* 之下，任何物件類型的類別目錄 ([量值群組]\*\*\*\*、[維度]\*\*\*\*、[KPI]\*\*\*\*、[計算]\*\*\*\* 或 [動作]\*\*\*\*)。</span><span class="sxs-lookup"><span data-stu-id="4c57f-134">To view any object, expand the category (**Measure Groups**, **Dimensions**, **KPIs**, **Calculations**, or **Actions**) for any object type under **Cube Objects**.</span></span> <span data-ttu-id="4c57f-135">若要檢視維度中的階層或屬性，請先展開維度，然後展開 [階層]\*\*\*\* 或 [屬性]\*\*\*\* 資料列。</span><span class="sxs-lookup"><span data-stu-id="4c57f-135">To view hierarchies or attributes in a dimension, first expand a dimension, and then expand the **Hierarchies** or **Attributes** row.</span></span> <span data-ttu-id="4c57f-136">若要檢視量值群組中的量值，請展開量值群組。</span><span class="sxs-lookup"><span data-stu-id="4c57f-136">To view measures in a measure group, expand the measure group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c57f-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c57f-137">See Also</span></span>  
 [<span data-ttu-id="4c57f-138">多維度模型中的 Cube</span><span class="sxs-lookup"><span data-stu-id="4c57f-138">Cubes in Multidimensional Models</span></span>](cubes-in-multidimensional-models.md)  
  
  
