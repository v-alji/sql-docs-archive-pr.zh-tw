---
title: " (SSAS 表格式) 啟用 DirectQuery 設計模式 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8ccd2dc88f447e78f6558565a89accc341eac37c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596919"
---
# <a name="enable-directquery-design-mode-ssas-tabular"></a><span data-ttu-id="01b3e-102">啟用 DirectQuery 設計模式 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="01b3e-102">Enable DirectQuery Design Mode (SSAS Tabular)</span></span>
  <span data-ttu-id="01b3e-103">若要建立 DirectQuery 模式的模型，必須先將設計階段環境變更為支援使用 DirectQuery 模式。</span><span class="sxs-lookup"><span data-stu-id="01b3e-103">To create a model in DirectQuery mode, you must first change the design-time environment so that it supports the user of DirectQuery mode.</span></span> <span data-ttu-id="01b3e-104">當您這樣做時，設計工具還會執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="01b3e-104">When you do so, the designer will also do the following:</span></span>  
  
-   <span data-ttu-id="01b3e-105">啟用 DirectQuery 部署屬性。</span><span class="sxs-lookup"><span data-stu-id="01b3e-105">Enable the use of the DirectQuery deployment properties.</span></span>  
  
-   <span data-ttu-id="01b3e-106">將工作空間資料庫變更為以混合模式執行，以使用快取進行設計。</span><span class="sxs-lookup"><span data-stu-id="01b3e-106">Change the workspace database to run in a hybrid mode that uses the cache for designing.</span></span> <span data-ttu-id="01b3e-107">在您實際部署模型時，模式會變更回您在專案部署屬性中指定的任何值。</span><span class="sxs-lookup"><span data-stu-id="01b3e-107">When you actually deploy the model, the mode will be changed back to whatever value you specified in the project deployment properties.</span></span>  
  
-   <span data-ttu-id="01b3e-108">停用與 DirectQuery 模式不相容的設計功能。</span><span class="sxs-lookup"><span data-stu-id="01b3e-108">Disable design features that are incompatible with DirectQuery mode.</span></span>  
  
-   <span data-ttu-id="01b3e-109">驗證現有的模型。</span><span class="sxs-lookup"><span data-stu-id="01b3e-109">Validate the existing model.</span></span>  
  
 <span data-ttu-id="01b3e-110">此程序描述如何在設計工具中啟用 DirectQuery 模式。</span><span class="sxs-lookup"><span data-stu-id="01b3e-110">This procedure describes how to enable DirectQuery mode in the designer.</span></span>  
  
### <a name="to-enable-use-of-directquery-in-a-model"></a><span data-ttu-id="01b3e-111">若要在模型中啟用 DirectQuery</span><span class="sxs-lookup"><span data-stu-id="01b3e-111">To enable use of DirectQuery in a model</span></span>  
  
1.  <span data-ttu-id="01b3e-112">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，開啟方案檔。</span><span class="sxs-lookup"><span data-stu-id="01b3e-112">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the solution file.</span></span>  
  
2.  <span data-ttu-id="01b3e-113">在 [物件總管] 中，按兩下 Model.bim 檔案。</span><span class="sxs-lookup"><span data-stu-id="01b3e-113">In Object Explorer, double-click the Model.bim file.</span></span>  
  
3.  <span data-ttu-id="01b3e-114">在 [**屬性**] 窗格中，將屬性**DirectQueryMode**變更為**On**。</span><span class="sxs-lookup"><span data-stu-id="01b3e-114">In the **Properties** pane, change the property, **DirectQueryMode**, to **On**.</span></span>  
  
4.  <span data-ttu-id="01b3e-115">如果發生錯誤，請在 Visual Studio 中開啟**錯誤清單**，並解決會導致模型無法切換至 DirectQuery 模式的任何問題。</span><span class="sxs-lookup"><span data-stu-id="01b3e-115">If there are errors, in Visual Studio, open the **Error List** and resolve any problems that would prevent the model from being switched to DirectQuery mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01b3e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01b3e-116">See Also</span></span>  
 [<span data-ttu-id="01b3e-117">DirectQuery 模式 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="01b3e-117">DirectQuery Mode &#40;SSAS Tabular&#41;</span></span>](directquery-mode-ssas-tabular.md)  
  
  
