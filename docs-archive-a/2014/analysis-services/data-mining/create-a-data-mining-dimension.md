---
title: 建立資料採礦維度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], dimensions
ms.assetid: 9f0c39e5-3516-43ab-b203-f3f6dbcff89a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 265cf671bbc825258f0b2bd6627690e8c52f252b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686543"
---
# <a name="create-a-data-mining-dimension"></a><span data-ttu-id="ebdc9-102">建立資料採礦維度</span><span class="sxs-lookup"><span data-stu-id="ebdc9-102">Create a Data Mining Dimension</span></span>
  <span data-ttu-id="ebdc9-103">如果採礦結構是以 OLAP Cube 為基礎，您就可以建立一個包含採礦模型內容的維度。</span><span class="sxs-lookup"><span data-stu-id="ebdc9-103">If your mining structure is based on an OLAP cube, you can create a dimension that contains the content of the mining model.</span></span> <span data-ttu-id="ebdc9-104">然後您就可以將維度併入來源 Cube 中。</span><span class="sxs-lookup"><span data-stu-id="ebdc9-104">You can then incorporate the dimension back into the source cube.</span></span>  
  
 <span data-ttu-id="ebdc9-105">您也可以瀏覽維度、用它來瀏覽模型結果，或是使用 MDX 查詢維度。</span><span class="sxs-lookup"><span data-stu-id="ebdc9-105">You can also browse the dimension, use it to explore the model results, or query the dimension using MDX.</span></span>  
  
### <a name="to-create-a-data-mining-dimension"></a><span data-ttu-id="ebdc9-106">若要建立資料採礦維度</span><span class="sxs-lookup"><span data-stu-id="ebdc9-106">To create a data mining dimension</span></span>  
  
1.  <span data-ttu-id="ebdc9-107">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 的資料採礦設計師中，選取 [採礦結構]\*\*\*\* 索引標籤或 [採礦模型]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ebdc9-107">In Data Mining Designer in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], select either the **Mining Structure** tab or the **Mining Models** tab.</span></span>  
  
2.  <span data-ttu-id="ebdc9-108">從 [採礦模型]\*\*\*\* 功能表，選取 [建立資料採礦維度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ebdc9-108">From the **Mining Model** menu, select **Create a Data Mining Dimension**.</span></span>  
  
     <span data-ttu-id="ebdc9-109">[建立資料採礦維度]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="ebdc9-109">The **Create Data Mining Dimension** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="ebdc9-110">在 [建立資料採礦維度]\*\*\*\* 對話方塊的 [模型名稱]\*\*\*\* 清單中，選取 OLAP 採礦模型。</span><span class="sxs-lookup"><span data-stu-id="ebdc9-110">In the **Model name** list of the **Create Data Mining Dimension** dialog box, select an OLAP mining model.</span></span>  
  
4.  <span data-ttu-id="ebdc9-111">在 [維度名稱]\*\*\*\* 方塊中，輸入新資料採礦維度的名稱。</span><span class="sxs-lookup"><span data-stu-id="ebdc9-111">In the **Dimension name** box, enter a name for the new data mining dimension.</span></span>  
  
5.  <span data-ttu-id="ebdc9-112">如果您想要建立包含新資料採礦維度的 Cube，請選取 [建立 Cube]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ebdc9-112">If you want to create a cube that includes the new data mining dimension, select **Create cube**.</span></span> <span data-ttu-id="ebdc9-113">在選取 [建立 Cube]\*\*\*\* 之後，您就可以輸入 Cube 的新名稱。</span><span class="sxs-lookup"><span data-stu-id="ebdc9-113">After you select **Create cube**, you can enter a new name for the cube.</span></span>  
  
6.  <span data-ttu-id="ebdc9-114">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="ebdc9-114">Click **OK**.</span></span>  
  
     <span data-ttu-id="ebdc9-115">這時會建立資料採礦維度，並加入方案總管的 [維度]\*\*\*\* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ebdc9-115">The data mining dimension is created and is added to the **Dimensions** folder in Solution Explorer.</span></span> <span data-ttu-id="ebdc9-116">如果您選取 [建立 Cube]\*\*\*\*，則也會建立新的 Cube，並將其加入 [Cubes]\*\*\*\* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ebdc9-116">If you selected **Create cube**, a new cube is also created and is added to the **Cubes** folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebdc9-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebdc9-117">See Also</span></span>  
 [<span data-ttu-id="ebdc9-118">採礦結構工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="ebdc9-118">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
