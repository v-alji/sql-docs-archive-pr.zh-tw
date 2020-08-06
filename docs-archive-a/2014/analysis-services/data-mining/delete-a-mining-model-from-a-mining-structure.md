---
title: 從採礦結構中刪除採礦模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], mining models
- deleting mining models
- removing mining models
- mining models [Analysis Services], deleting
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 72c79dcdccf6225b8e75144f8b090dcab7506c10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599270"
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a><span data-ttu-id="bb519-102">從採礦結構刪除採礦模型</span><span class="sxs-lookup"><span data-stu-id="bb519-102">Delete a Mining Model from a Mining Structure</span></span>
  <span data-ttu-id="bb519-103">您可以使用資料採礦設計師、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 DMX 陳述式來刪除採礦模型。</span><span class="sxs-lookup"><span data-stu-id="bb519-103">You can delete mining models by using Data Mining Designer, by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or by using DMX statements.</span></span>  
  
### <a name="delete-a-mining-model-using-sql-server-data-tools"></a><span data-ttu-id="bb519-104">使用 SQL Server 資料工具刪除採礦模型</span><span class="sxs-lookup"><span data-stu-id="bb519-104">Delete a mining model using SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="bb519-105">選取 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的 [採礦模型]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bb519-105">Select the **Mining Models** tab in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="bb519-106">以滑鼠右鍵按一下您想刪除的模型，然後選取 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb519-106">Right-click the model that you want to delete, and select **Delete**.</span></span>  
  
     <span data-ttu-id="bb519-107">[刪除物件]\*\*\*\* 對話方塊就會開啟。</span><span class="sxs-lookup"><span data-stu-id="bb519-107">The **Delete Objects** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="bb519-108">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="bb519-108">Click **OK**.</span></span>  
  
### <a name="delete-a-mining-model-using-sql-server-management-studio"></a><span data-ttu-id="bb519-109">使用 SQL Server Management Studio 刪除採礦模型</span><span class="sxs-lookup"><span data-stu-id="bb519-109">Delete a mining model using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="bb519-110">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，開啟包含模型的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bb519-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that contains the model.</span></span>  
  
2.  <span data-ttu-id="bb519-111">展開 [採礦結構]\*\*\*\*，然後展開 [採礦模型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb519-111">Expand **Mining Structures**, and then expand **Mining Models**.</span></span>  
  
3.  <span data-ttu-id="bb519-112">以滑鼠右鍵按一下您想刪除的模型，然後選取 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb519-112">Right-click the model you want to delete, and select **Delete**.</span></span>  
  
     <span data-ttu-id="bb519-113">刪除模型並不會刪除定型資料，只刪除定型模型時建立的中繼資料和所有模式。</span><span class="sxs-lookup"><span data-stu-id="bb519-113">Deleting the model does not delete the training data, only the metadata and any patterns created when you trained the model.</span></span>  
  
### <a name="delete-a-mining-model-using-dmx"></a><span data-ttu-id="bb519-114">使用 DMX 刪除採礦模型</span><span class="sxs-lookup"><span data-stu-id="bb519-114">Delete a mining model using DMX</span></span>  
  
-   [<span data-ttu-id="bb519-115">DROP MINING MODEL &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="bb519-115">DROP MINING MODEL &#40;DMX&#41;</span></span>](/sql/dmx/drop-mining-model-dmx)  
  
## <a name="see-also"></a><span data-ttu-id="bb519-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb519-116">See Also</span></span>  
 [<span data-ttu-id="bb519-117">採礦模型工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="bb519-117">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
