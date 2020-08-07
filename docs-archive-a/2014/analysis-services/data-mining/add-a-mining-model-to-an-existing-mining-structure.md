---
title: 將採礦模型加入至現有的採礦結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], adding
- mining structures [Analysis Services], mining models
- adding mining models
ms.assetid: fcf72300-0674-4e73-a826-9b8eeffefbb5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0afdf5f795303eaa8bb672aa80e68e0f1f891607
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598068"
---
# <a name="add-a-mining-model-to-an-existing-mining-structure"></a><span data-ttu-id="ab063-102">將採礦模型加入至現有的採礦結構</span><span class="sxs-lookup"><span data-stu-id="ab063-102">Add a Mining Model to an Existing Mining Structure</span></span>
  <span data-ttu-id="ab063-103">在加入初始模型之後，您就可以將更多採礦模型加入至採礦結構中。</span><span class="sxs-lookup"><span data-stu-id="ab063-103">You can add more mining models to a mining structure, after you add the initial model.</span></span> <span data-ttu-id="ab063-104">每一個模型必須包含存在於結構中的資料行，但您可以為每一個採礦模型定義不同的資料行使用方式。</span><span class="sxs-lookup"><span data-stu-id="ab063-104">Each model must contain columns that exist in the structure, but you can define the usage of the columns differently for each mining model.</span></span> <span data-ttu-id="ab063-105">如需如何定義採礦模型資料行的詳細資訊，請參閱 [採礦模型資料行](mining-model-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="ab063-105">For more information about how to define mining models columns, see [Mining Model Columns](mining-model-columns.md).</span></span>  
  
### <a name="to-add-a-mining-model-to-the-structure"></a><span data-ttu-id="ab063-106">若要將採礦模型加入至結構</span><span class="sxs-lookup"><span data-stu-id="ab063-106">To add a mining model to the structure</span></span>  
  
1.  <span data-ttu-id="ab063-107">從 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的 [採礦模型]\*\*\*\* 功能表項目中，選取 [新增採礦模型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ab063-107">From the **Mining Model** menu item in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select **New Mining Model**.</span></span>  
  
     <span data-ttu-id="ab063-108">就會開啟 [新增採礦模型]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ab063-108">The **New Mining Model** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="ab063-109">在 [模型名稱]\*\*\*\* 之下，輸入新採礦模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="ab063-109">Under **Model name**, enter a name for the new mining model.</span></span>  
  
3.  <span data-ttu-id="ab063-110">在 [演算法名稱]\*\*\*\* 之下，選取用來建立採礦模型的演算法。</span><span class="sxs-lookup"><span data-stu-id="ab063-110">Under **Algorithm name**, select the algorithm that the mining model will be built from.</span></span>  
  
4.  <span data-ttu-id="ab063-111">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="ab063-111">Click **OK**.</span></span>  
  
 <span data-ttu-id="ab063-112">新的 [採礦模型] 會出現在 [**採礦模型**] 索引標籤中。此模型會使用存在於結構中的預設資料行。</span><span class="sxs-lookup"><span data-stu-id="ab063-112">A new mining model appears in the **Mining Models** tab. The model uses the default columns that exist in the structure.</span></span> <span data-ttu-id="ab063-113">如需如何修改資料行的相關資訊，請參閱 [變更採礦模型的屬性](change-the-properties-of-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="ab063-113">For information about how to modify the columns, see [Change the Properties of a Mining Model](change-the-properties-of-a-mining-model.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab063-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab063-114">See Also</span></span>  
 [<span data-ttu-id="ab063-115">採礦模型工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="ab063-115">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
