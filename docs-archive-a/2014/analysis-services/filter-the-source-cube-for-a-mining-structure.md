---
title: 篩選採礦結構的來源 Cube |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slice cubes [Analysis Services]
- mining structures [Analysis Services], filtering source cube
- cubes [Analysis Services], slicing
- filtering data [Analysis Services]
ms.assetid: 05dce7e1-2fe5-4500-bacf-c1a8a76e1424
author: minewiskan
ms.author: owend
ms.openlocfilehash: 61409b4803f43d3ff2634daaba65a92bc343db36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592988"
---
# <a name="filter-the-source-cube-for-a-mining-structure"></a><span data-ttu-id="0078d-102">篩選採礦結構的來源 Cube</span><span class="sxs-lookup"><span data-stu-id="0078d-102">Filter the Source Cube for a Mining Structure</span></span>
  <span data-ttu-id="0078d-103">當您建立以多維度模型中的資料為基礎的採礦結構 (OLAP Cube) 時，您可以配量此挖掘*結構所依據*的 cube。</span><span class="sxs-lookup"><span data-stu-id="0078d-103">When you create a mining structure that is based on data in a multidimensional model (an OLAP cube), you can *slice* the cube that the mining structure is based on.</span></span> <span data-ttu-id="0078d-104">配量處理可讓您建立資料子集，當做用來定型採礦模型的一種資料篩選。</span><span class="sxs-lookup"><span data-stu-id="0078d-104">Slicing lets you create subsets of data, as a kind of filter on the data that is used to train the mining model.</span></span>  
  
### <a name="to-slice-a-cube"></a><span data-ttu-id="0078d-105">若要對 Cube 進行配量處理</span><span class="sxs-lookup"><span data-stu-id="0078d-105">To slice a cube</span></span>  
  
1.  <span data-ttu-id="0078d-106">在的 [資料採礦設計師] 中 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] ，選取 [**採礦結構**] 索引標籤或 [**採礦模型**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0078d-106">In Data Mining Designer in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], select the **Mining Structure** tab or the **Mining Models** tab.</span></span>  
  
2.  <span data-ttu-id="0078d-107">在 [**採礦模型**] 功能表上，選取 [**定義採礦結構 Cube**配量]。</span><span class="sxs-lookup"><span data-stu-id="0078d-107">On the **Mining Model** menu, select **Define Mining Structure Cube Slice**.</span></span>  
  
     <span data-ttu-id="0078d-108">[配量**Cube** ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="0078d-108">The **Slice Cube** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="0078d-109">在 [配量 Cube] 對話方塊的 [**維度**]**資料**行中，選取您要篩選的維度。</span><span class="sxs-lookup"><span data-stu-id="0078d-109">In the **Dimension** column of the **Slice Cube** dialog box, select the dimension that you want to filter.</span></span>  
  
4.  <span data-ttu-id="0078d-110">使用 [階層]**資料行中的清單**選取階層的層級。</span><span class="sxs-lookup"><span data-stu-id="0078d-110">Select a level of a hierarchy, using the list in the **Hierarchy** column.</span></span>  
  
5.  <span data-ttu-id="0078d-111">從 [**運算子**] 資料行的清單中選取運算子，以用於建立篩選準則。</span><span class="sxs-lookup"><span data-stu-id="0078d-111">Select an operator from the list in the **Operator** column, to use in building the filter condition.</span></span>  
  
6.  <span data-ttu-id="0078d-112">按一下 [**篩選**] 資料行中的方塊。</span><span class="sxs-lookup"><span data-stu-id="0078d-112">Click the box in the **Filter** column.</span></span>  
  
     <span data-ttu-id="0078d-113">隨即開啟一個對話方塊，其中包含指定之階層層級的所有成員。</span><span class="sxs-lookup"><span data-stu-id="0078d-113">A dialog box opens that contains all the members at the specified level of the hierarchy.</span></span>  
  
7.  <span data-ttu-id="0078d-114">選取您要篩選的成員。</span><span class="sxs-lookup"><span data-stu-id="0078d-114">Select the member or members on which you want to filter.</span></span>  
  
8.  <span data-ttu-id="0078d-115">在 [成員] 對話方塊中按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="0078d-115">Click **OK** in the member dialog box.</span></span>  
  
9. <span data-ttu-id="0078d-116">在 [配量**Cube** ] 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="0078d-116">Click **OK** in the **Slice Cube** dialog box.</span></span>  
  
     <span data-ttu-id="0078d-117">來源 Cube 現在會依 Cube 配量定義來篩選。</span><span class="sxs-lookup"><span data-stu-id="0078d-117">The source cube is now filtered as defined by the cube slice.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0078d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0078d-118">See Also</span></span>  
 <span data-ttu-id="0078d-119">[採礦結構工作和操作說明](data-mining/mining-structure-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="0078d-119">[Mining Structure Tasks and How-tos](data-mining/mining-structure-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="0078d-120">建立新的 OLAP 採礦結構</span><span class="sxs-lookup"><span data-stu-id="0078d-120">Create a New OLAP Mining Structure</span></span>](data-mining/create-a-new-olap-mining-structure.md)  
  
  
