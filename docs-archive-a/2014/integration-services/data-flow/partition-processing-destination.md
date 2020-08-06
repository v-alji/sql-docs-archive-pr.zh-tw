---
title: 資料分割處理目的地 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partitionprocessingdest.f1
helpviewer_keywords:
- partitions [Analysis Services], processing
- Partition Processing destination [Integration Services]
- destinations [Integration Services], Partition Processing
ms.assetid: 36c592ff-3f78-4a58-b496-31c1c8eee131
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d32306328f7a0575e55397d5209b4767d0cf1bd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593474"
---
# <a name="partition-processing-destination"></a><span data-ttu-id="52883-102">資料分割處理目的地</span><span class="sxs-lookup"><span data-stu-id="52883-102">Partition Processing Destination</span></span>
  <span data-ttu-id="52883-103">「資料分割處理」目的地會載入及處理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料分割。</span><span class="sxs-lookup"><span data-stu-id="52883-103">The Partition Processing destination loads and processes an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] partition.</span></span> <span data-ttu-id="52883-104">如需資料分割的詳細資訊，請參閱[資料分割 &#40;Analysis Services - 多維度資料&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data)。</span><span class="sxs-lookup"><span data-stu-id="52883-104">For more information about partitions, see [Partitions &#40;Analysis Services - Multidimensional Data&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data).</span></span>  
  
 <span data-ttu-id="52883-105">「資料分割處理」目的地包含下列功能：</span><span class="sxs-lookup"><span data-stu-id="52883-105">The Partition Processing destination includes the following features:</span></span>  
  
-   <span data-ttu-id="52883-106">執行累加式、完整或更新處理的選項。</span><span class="sxs-lookup"><span data-stu-id="52883-106">Options to perform incremental, full, or update processing.</span></span>  
  
-   <span data-ttu-id="52883-107">指定在發生指定數目的錯誤之後，處理會忽略錯誤還是停止的錯誤組態。</span><span class="sxs-lookup"><span data-stu-id="52883-107">Error configuration, to specify whether processing ignores errors or stops after a specified number of errors.</span></span>  
  
-   <span data-ttu-id="52883-108">將輸入資料行對應至資料分割資料行。</span><span class="sxs-lookup"><span data-stu-id="52883-108">Mapping of input columns to partition columns.</span></span>  
  
 <span data-ttu-id="52883-109">如需處理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件的詳細資訊，請參閱[處理選項和設定 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services)。</span><span class="sxs-lookup"><span data-stu-id="52883-109">For more information about processing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects, see [Processing Options and Settings &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="52883-110">此處描述的工作不適用於 Analysis Services 表格式模型。</span><span class="sxs-lookup"><span data-stu-id="52883-110">Tasks described here do not apply to Analysis Services tabular models.</span></span>  <span data-ttu-id="52883-111">您無法針對表格式模型，將輸入資料行對應至資料分割資料行。</span><span class="sxs-lookup"><span data-stu-id="52883-111">You cannot map input columns to partition columns for tabular models.</span></span> <span data-ttu-id="52883-112">您可以改用 Analysis Services 執行 DDL 工作 ( [Analysis Services Execute DDL Task](../control-flow/analysis-services-execute-ddl-task.md) ) 來處理資料分割。</span><span class="sxs-lookup"><span data-stu-id="52883-112">You can instead use the Analysis Services Execute DDL task [Analysis Services Execute DDL Task](../control-flow/analysis-services-execute-ddl-task.md) to process the partition.</span></span>  
  
## <a name="configuration-of-the-partition-processing-destination"></a><span data-ttu-id="52883-113">設定資料分割處理目的地</span><span class="sxs-lookup"><span data-stu-id="52883-113">Configuration of the Partition Processing Destination</span></span>  
 <span data-ttu-id="52883-114">資料分割處理目的地會使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 連接管理員，以連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案或包含目的地所處理之 Cube 及資料分割的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="52883-114">The Partition Processing destination uses an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the cubes and partitions the destination processes.</span></span> <span data-ttu-id="52883-115">如需相關資訊，請參閱 [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="52883-115">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 <span data-ttu-id="52883-116">此目的地擁有一個輸入。</span><span class="sxs-lookup"><span data-stu-id="52883-116">This destination has one input.</span></span> <span data-ttu-id="52883-117">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="52883-117">It does not support an error output.</span></span>  
  
 <span data-ttu-id="52883-118">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="52883-118">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="52883-119">如需有關 **[資料分割處理目的地編輯器]** 對話方塊中可設定之屬性的詳細資訊，請按一下下列主題之一：</span><span class="sxs-lookup"><span data-stu-id="52883-119">For more information about the properties that you can set in the Partition Processing **Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="52883-120">資料分割處理目的地編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="52883-120">Partition Processing Destination Editor &#40;Connection Manager Page&#41;</span></span>](../partition-processing-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="52883-121">資料分割處理目的地編輯器 &#40;對應頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="52883-121">Partition Processing Destination Editor &#40;Mappings Page&#41;</span></span>](../partition-processing-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="52883-122">資料分割處理目的地編輯器 &#40;進階頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="52883-122">Partition Processing Destination Editor &#40;Advanced Page&#41;</span></span>](../partition-processing-destination-editor-advanced-page.md)  
  
 <span data-ttu-id="52883-123">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="52883-123">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="52883-124">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="52883-124">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="52883-125">Common Properties</span><span class="sxs-lookup"><span data-stu-id="52883-125">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="52883-126">資料分割處理目的地自訂屬性</span><span class="sxs-lookup"><span data-stu-id="52883-126">Partition Processing Destination Custom Properties</span></span>](partition-processing-destination-custom-properties.md)  
  
 <span data-ttu-id="52883-127">如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="52883-127">For more information about how to set the properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
