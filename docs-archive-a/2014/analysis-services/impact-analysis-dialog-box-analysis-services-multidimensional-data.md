---
title: 影響分析對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.impactanalysisdialog.f1
ms.assetid: 208268eb-4e14-44db-9c64-6f74b776adb6
author: minewiskan
ms.author: owend
ms.openlocfilehash: e47ab806b9bd10afc812113b69fe0849437068b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687330"
---
# <a name="impact-analysis-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="d5570-102">影響分析對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="d5570-102">Impact Analysis Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="d5570-103">如果 **[處理]** 對話方塊中所列出的物件已經處理，請使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 和 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的 **[影響分析]** 對話方塊來識別及選擇性地處理受影響的相依物件。</span><span class="sxs-lookup"><span data-stu-id="d5570-103">Use the **Impact Analysis** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to identify and optionally process dependent objects that are affected if the objects listed in the **Process** dialog box are processed.</span></span> <span data-ttu-id="d5570-104">在 **[處理]** 對話方塊中按一下 **[影響分析]** ，即可顯示 **[影響分析]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d5570-104">You can display the **Impact Analysis** dialog box by clicking **Impact Analysis** from the **Process** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d5570-105">如果物件受到一個以上的影響，物件就會出現一次以上。</span><span class="sxs-lookup"><span data-stu-id="d5570-105">An object appears more than once if it is affected in more than one way.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d5570-106">選項</span><span class="sxs-lookup"><span data-stu-id="d5570-106">Options</span></span>  
 <span data-ttu-id="d5570-107">**物件清單**</span><span class="sxs-lookup"><span data-stu-id="d5570-107">**Object list**</span></span>  
 <span data-ttu-id="d5570-108">在方格中顯示相依性物件的清單。</span><span class="sxs-lookup"><span data-stu-id="d5570-108">Displays a list of dependent objects in a grid.</span></span> <span data-ttu-id="d5570-109">方格包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="d5570-109">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="d5570-110">**Object Name**</span><span class="sxs-lookup"><span data-stu-id="d5570-110">**Object Name**</span></span>  
 <span data-ttu-id="d5570-111">顯示可能需要處理之相依性物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5570-111">Displays the name of the dependent object that may need to be processed.</span></span> <span data-ttu-id="d5570-112">名稱左邊的圖示會指出物件類型。</span><span class="sxs-lookup"><span data-stu-id="d5570-112">The icon to the left of the name indicates the object type.</span></span>  
  
 <span data-ttu-id="d5570-113">**型別**</span><span class="sxs-lookup"><span data-stu-id="d5570-113">**Type**</span></span>  
 <span data-ttu-id="d5570-114">顯示可能需要處理之相依性物件的類型。</span><span class="sxs-lookup"><span data-stu-id="d5570-114">Displays the type of dependent object that may need to be processed.</span></span>  
  
 <span data-ttu-id="d5570-115">**影響類型**</span><span class="sxs-lookup"><span data-stu-id="d5570-115">**Impact Type**</span></span>  
 <span data-ttu-id="d5570-116">顯示處理 [處理]\*\*\*\* 對話方塊中的物件時，會對相依物件造成的影響。</span><span class="sxs-lookup"><span data-stu-id="d5570-116">Displays the effect that processing the objects in the **Process** dialog box has on the dependent object.</span></span> <span data-ttu-id="d5570-117">下表列出可能的處理效果，並註解每一個處理的結果是會導致警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="d5570-117">The following table lists the possible effects of processing and notes whether each one results in a warning or an error.</span></span>  
  
|<span data-ttu-id="d5570-118">影響</span><span class="sxs-lookup"><span data-stu-id="d5570-118">Impact</span></span>|<span data-ttu-id="d5570-119">訊息</span><span class="sxs-lookup"><span data-stu-id="d5570-119">Message</span></span>|  
|------------|-------------|  
|<span data-ttu-id="d5570-120">將清除物件 (取消處理)</span><span class="sxs-lookup"><span data-stu-id="d5570-120">Object will be cleared (unprocessed)</span></span>|<span data-ttu-id="d5570-121">警告</span><span class="sxs-lookup"><span data-stu-id="d5570-121">Warning</span></span>|  
|<span data-ttu-id="d5570-122">物件將失效</span><span class="sxs-lookup"><span data-stu-id="d5570-122">Object would be invalid</span></span>|<span data-ttu-id="d5570-123">錯誤</span><span class="sxs-lookup"><span data-stu-id="d5570-123">Error</span></span>|  
|<span data-ttu-id="d5570-124">將捨棄彙總</span><span class="sxs-lookup"><span data-stu-id="d5570-124">Aggregation would be dropped</span></span>|<span data-ttu-id="d5570-125">警告</span><span class="sxs-lookup"><span data-stu-id="d5570-125">Warning</span></span>|  
|<span data-ttu-id="d5570-126">將捨棄彈性彙總</span><span class="sxs-lookup"><span data-stu-id="d5570-126">Flexible aggregation would be dropped</span></span>|<span data-ttu-id="d5570-127">警告</span><span class="sxs-lookup"><span data-stu-id="d5570-127">Warning</span></span>|  
|<span data-ttu-id="d5570-128">將捨棄索引</span><span class="sxs-lookup"><span data-stu-id="d5570-128">Indexes will be dropped</span></span>|<span data-ttu-id="d5570-129">警告</span><span class="sxs-lookup"><span data-stu-id="d5570-129">Warning</span></span>|  
|<span data-ttu-id="d5570-130">將處理非子物件</span><span class="sxs-lookup"><span data-stu-id="d5570-130">Non-child object will be processed</span></span>|<span data-ttu-id="d5570-131">警告</span><span class="sxs-lookup"><span data-stu-id="d5570-131">Warning</span></span>|  
  
 <span data-ttu-id="d5570-132">**處理物件**</span><span class="sxs-lookup"><span data-stu-id="d5570-132">**Process Object**</span></span>  
 <span data-ttu-id="d5570-133">選取您要進行處理作業的相依性物件。</span><span class="sxs-lookup"><span data-stu-id="d5570-133">Select the dependent objects that you want to process with the processing operation.</span></span> <span data-ttu-id="d5570-134">完成處理作業之後，必須處理未選取的相依性物件。</span><span class="sxs-lookup"><span data-stu-id="d5570-134">Dependent objects that are not selected must be processed after the processing operation is finished.</span></span> <span data-ttu-id="d5570-135">否則它們將無法使用。</span><span class="sxs-lookup"><span data-stu-id="d5570-135">Otherwise, they cannot be used.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5570-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5570-136">See Also</span></span>  
 <span data-ttu-id="d5570-137">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="d5570-137">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="d5570-138">進程對話方塊 &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="d5570-138">Process Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
