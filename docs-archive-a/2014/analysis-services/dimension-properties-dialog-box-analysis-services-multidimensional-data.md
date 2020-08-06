---
title: 維度屬性對話方塊 (Analysis Services 多維資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.dimensionproperties.f1
helpviewer_keywords:
- Dimension Properties dialog box
ms.assetid: 7235d443-b2ce-4c53-b2eb-abceb28394bb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0523220c76c11280165bc825c5c00c5eb9e23be6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607141"
---
# <a name="dimension-properties-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="59c0c-102">維度屬性對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="59c0c-102">Dimension Properties Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="59c0c-103">使用 **中的** [維度屬性] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 對話方塊，即可設定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫中之維度的屬性。</span><span class="sxs-lookup"><span data-stu-id="59c0c-103">Use the **Dimension Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to set the properties of a dimension in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="59c0c-104">您可以在 [物件總管] 中以滑鼠右鍵按一下維度，然後選取 [屬性]\*\*\*\*，來顯示 [維度屬性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="59c0c-104">You can display the **Dimension Properties** dialog box by right-clicking a dimension in Object Explorer and selecting **Properties**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="59c0c-105">選項</span><span class="sxs-lookup"><span data-stu-id="59c0c-105">Options</span></span>  
  
|<span data-ttu-id="59c0c-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="59c0c-106">Term</span></span>|<span data-ttu-id="59c0c-107">定義</span><span class="sxs-lookup"><span data-stu-id="59c0c-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="59c0c-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="59c0c-108">**Name**</span></span>|<span data-ttu-id="59c0c-109">顯示維度的名稱。</span><span class="sxs-lookup"><span data-stu-id="59c0c-109">Displays the name of the dimension.</span></span>|  
|<span data-ttu-id="59c0c-110">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="59c0c-110">**ID**</span></span>|<span data-ttu-id="59c0c-111">顯示維度的識別碼。</span><span class="sxs-lookup"><span data-stu-id="59c0c-111">Displays the identifier of the dimension.</span></span>|  
|<span data-ttu-id="59c0c-112">**說明**</span><span class="sxs-lookup"><span data-stu-id="59c0c-112">**Description**</span></span>|<span data-ttu-id="59c0c-113">顯示維度的描述。</span><span class="sxs-lookup"><span data-stu-id="59c0c-113">Displays the description of the dimension.</span></span>|  
|<span data-ttu-id="59c0c-114">**建立時間戳記**</span><span class="sxs-lookup"><span data-stu-id="59c0c-114">**Create Timestamp**</span></span>|<span data-ttu-id="59c0c-115">顯示建立維度的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="59c0c-115">Displays the date and time the dimension was created.</span></span>|  
|<span data-ttu-id="59c0c-116">**上次結構描述更新**</span><span class="sxs-lookup"><span data-stu-id="59c0c-116">**Last Schema Update**</span></span>|<span data-ttu-id="59c0c-117">顯示上次更新維度的中繼資料的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="59c0c-117">Displays the date and time the metadata for the dimension was last updated.</span></span>|  
|<span data-ttu-id="59c0c-118">**處理模式**</span><span class="sxs-lookup"><span data-stu-id="59c0c-118">**Processing Mode**</span></span>|<span data-ttu-id="59c0c-119">選取用於維度的處理模式。</span><span class="sxs-lookup"><span data-stu-id="59c0c-119">Select the processing mode to use for the dimension.</span></span> <span data-ttu-id="59c0c-120">如需有關此屬性之值的詳細資訊，請參閱＜<xref:Microsoft.AnalysisServices.Dimension.ProcessingMode%2A>＞。</span><span class="sxs-lookup"><span data-stu-id="59c0c-120">For more information about the values for this property, see <xref:Microsoft.AnalysisServices.Dimension.ProcessingMode%2A>.</span></span>|  
|<span data-ttu-id="59c0c-121">**State**</span><span class="sxs-lookup"><span data-stu-id="59c0c-121">**State**</span></span>|<span data-ttu-id="59c0c-122">顯示維度的處理狀態。</span><span class="sxs-lookup"><span data-stu-id="59c0c-122">Displays the processing state of the dimension.</span></span> <span data-ttu-id="59c0c-123">如需有關此屬性之值的詳細資訊，請參閱＜<xref:Microsoft.AnalysisServices.ProcessableMajorObject.State%2A>＞。</span><span class="sxs-lookup"><span data-stu-id="59c0c-123">For more information about the values for this property, see <xref:Microsoft.AnalysisServices.ProcessableMajorObject.State%2A>.</span></span>|  
|<span data-ttu-id="59c0c-124">**上次處理**</span><span class="sxs-lookup"><span data-stu-id="59c0c-124">**Last Processed**</span></span>|<span data-ttu-id="59c0c-125">顯示上次處理維度的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="59c0c-125">Displays the date and time the dimension was last processed.</span></span>|  
|<span data-ttu-id="59c0c-126">**目前儲存模式**</span><span class="sxs-lookup"><span data-stu-id="59c0c-126">**Current Storage Mode**</span></span>|<span data-ttu-id="59c0c-127">顯示維度的目前儲存模式。</span><span class="sxs-lookup"><span data-stu-id="59c0c-127">Displays the current storage mode for the dimension.</span></span> <span data-ttu-id="59c0c-128">如需有關此屬性之值的詳細資訊，請參閱＜<xref:Microsoft.AnalysisServices.Dimension.CurrentStorageMode%2A>＞。</span><span class="sxs-lookup"><span data-stu-id="59c0c-128">For more information about the values for this property, see <xref:Microsoft.AnalysisServices.Dimension.CurrentStorageMode%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59c0c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59c0c-129">See Also</span></span>  
 <span data-ttu-id="59c0c-130">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="59c0c-130">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="59c0c-131">維度 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="59c0c-131">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
