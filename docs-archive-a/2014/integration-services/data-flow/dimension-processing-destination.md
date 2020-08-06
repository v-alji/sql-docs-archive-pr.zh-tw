---
title: 維度處理目的地 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimensionprocessingdest.f1
helpviewer_keywords:
- Dimension Processing destination
- loading dimensions
- destinations [Integration Services], Dimension Processing
- dimensions [Analysis Services], processing
ms.assetid: 4c49bb95-7259-42f4-a785-bb6aaf5f8566
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 61cde87ac4fa5fcb1352491d787674447dd404b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593494"
---
# <a name="dimension-processing-destination"></a><span data-ttu-id="cc814-102">維度處理目的地</span><span class="sxs-lookup"><span data-stu-id="cc814-102">Dimension Processing Destination</span></span>
  <span data-ttu-id="cc814-103">「維度處理」目的地會載入及處理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 維度。</span><span class="sxs-lookup"><span data-stu-id="cc814-103">The Dimension Processing destination loads and processes an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dimension.</span></span> <span data-ttu-id="cc814-104">如需維度的詳細資訊，請參閱[維度 &#40;Analysis Services - 多維度資料&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data)。</span><span class="sxs-lookup"><span data-stu-id="cc814-104">For more information about dimensions, see [Dimensions &#40;Analysis Services - Multidimensional Data&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data).</span></span>  
  
 <span data-ttu-id="cc814-105">「維度處理」目的地包含下列功能：</span><span class="sxs-lookup"><span data-stu-id="cc814-105">The Dimension Processing destination includes the following features:</span></span>  
  
-   <span data-ttu-id="cc814-106">執行累加式、完整或更新處理的選項。</span><span class="sxs-lookup"><span data-stu-id="cc814-106">Options to perform incremental, full, or update processing.</span></span>  
  
-   <span data-ttu-id="cc814-107">錯誤組態，可以指定在發生指定數目的錯誤之後，維度處理是忽略錯誤還是停止。</span><span class="sxs-lookup"><span data-stu-id="cc814-107">Error configuration, to specify whether dimension processing ignores errors or stops after a specified number of errors.</span></span>  
  
-   <span data-ttu-id="cc814-108">將輸入資料行對應至維度資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="cc814-108">Mapping of input columns to columns in dimension tables.</span></span>  
  
 <span data-ttu-id="cc814-109">如需處理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件的詳細資訊，請參閱[處理選項和設定 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services)。</span><span class="sxs-lookup"><span data-stu-id="cc814-109">For more information about processing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects, see [Processing Options and Settings &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services).</span></span>  
  
## <a name="configuration-of-the-dimension-processing-destination"></a><span data-ttu-id="cc814-110">設定維度處理目的地</span><span class="sxs-lookup"><span data-stu-id="cc814-110">Configuration of the Dimension Processing Destination</span></span>  
 <span data-ttu-id="cc814-111">「維度處理」目的地會使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 連接管理員，以連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案或包含目的地所處理之維度的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="cc814-111">The Dimension Processing destination uses an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the dimensions the destination processes.</span></span> <span data-ttu-id="cc814-112">如需相關資訊，請參閱 [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="cc814-112">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 <span data-ttu-id="cc814-113">此目的地擁有一個輸入。</span><span class="sxs-lookup"><span data-stu-id="cc814-113">This destination has one input.</span></span> <span data-ttu-id="cc814-114">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="cc814-114">It does not support an error output.</span></span>  
  
 <span data-ttu-id="cc814-115">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="cc814-115">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="cc814-116">如需有關 **[維度處理目的地編輯器]** 對話方塊中可設定之屬性的詳細資訊，請按一下下列主題之一：</span><span class="sxs-lookup"><span data-stu-id="cc814-116">For more information about the properties that you can set in the **Dimension Processing Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="cc814-117">維度處理目的地編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="cc814-117">Dimension Processing Destination Editor &#40;Connection Manager Page&#41;</span></span>](../dimension-processing-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="cc814-118">維度處理目的地編輯器 &#40;對應頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="cc814-118">Dimension Processing Destination Editor &#40;Mappings Page&#41;</span></span>](../dimension-processing-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="cc814-119">維度處理目的地編輯器 &#40;進階頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="cc814-119">Dimension Processing Destination Editor &#40;Advanced Page&#41;</span></span>](../dimension-processing-destination-editor-advanced-page.md)  
  
 <span data-ttu-id="cc814-120">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="cc814-120">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="cc814-121">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按一下下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="cc814-121">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topic:</span></span>  
  
-   [<span data-ttu-id="cc814-122">Common Properties</span><span class="sxs-lookup"><span data-stu-id="cc814-122">Common Properties</span></span>](../common-properties.md)  
  
 <span data-ttu-id="cc814-123">如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="cc814-123">For more information about how to set the properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc814-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc814-124">See Also</span></span>  
 <span data-ttu-id="cc814-125">[資料流程](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="cc814-125">[Data Flow](data-flow.md) </span></span>  
 [<span data-ttu-id="cc814-126">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="cc814-126">Integration Services Transformations</span></span>](transformations/integration-services-transformations.md)  
  
  
