---
title: 資料採礦查詢轉換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquerytrans.f1
helpviewer_keywords:
- Data Mining Query transformation
- prediction queries [Integration Services]
ms.assetid: 7960133b-a3e1-48af-ba43-55ed78c38e71
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 278fdc3b1abd38b63f01e967e28d11983a09e682
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585516"
---
# <a name="data-mining-query-transformation"></a><span data-ttu-id="da285-102">資料採礦查詢轉換</span><span class="sxs-lookup"><span data-stu-id="da285-102">Data Mining Query Transformation</span></span>
  <span data-ttu-id="da285-103">「資料採礦查詢」轉換會對資料採礦模型執行預測查詢。</span><span class="sxs-lookup"><span data-stu-id="da285-103">The Data Mining Query transformation performs prediction queries against data mining models.</span></span> <span data-ttu-id="da285-104">這項轉換包含用來建立「資料採礦延伸模組」(DMX) 查詢的查詢產生器。</span><span class="sxs-lookup"><span data-stu-id="da285-104">This transformation contains a query builder for creating Data Mining Extensions (DMX) queries.</span></span> <span data-ttu-id="da285-105">查詢產生器可讓您建立自訂陳述式，以便使用 DMX 語言對照現有採礦模型評估轉換輸入資料。</span><span class="sxs-lookup"><span data-stu-id="da285-105">The query builder lets you create custom statements for evaluating the transformation input data against an existing mining model using the DMX language.</span></span> <span data-ttu-id="da285-106">如需詳細資訊，請參閱[資料採礦延伸模組 &#40;DMX&#41; 參考](/sql/dmx/data-mining-extensions-dmx-reference)。</span><span class="sxs-lookup"><span data-stu-id="da285-106">For more information, see [Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference).</span></span>  
  
 <span data-ttu-id="da285-107">如果模型是在相同的資料採礦結構上建立，則一項轉換可執行多項預測查詢。</span><span class="sxs-lookup"><span data-stu-id="da285-107">One transformation can execute multiple prediction queries if the models are built on the same data mining structure.</span></span> <span data-ttu-id="da285-108">如需詳細資訊，請參閱[資料採礦查詢介面](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools)。</span><span class="sxs-lookup"><span data-stu-id="da285-108">For more information, see [Data Mining Query Interfaces](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools).</span></span>  
  
## <a name="configuration-of-the-data-mining-query-transformation"></a><span data-ttu-id="da285-109">設定資料採礦查詢轉換</span><span class="sxs-lookup"><span data-stu-id="da285-109">Configuration of the Data Mining Query Transformation</span></span>  
 <span data-ttu-id="da285-110">「資料採礦查詢」轉換會使用 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 連接管理員連接到包含採礦結構和採礦模型的 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 專案或 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="da285-110">The Data Mining Query transformation uses an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] that contains the mining structure and mining models.</span></span> <span data-ttu-id="da285-111">如需相關資訊，請參閱 [Analysis Services Connection Manager](../../connection-manager/analysis-services-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="da285-111">For more information, see [Analysis Services Connection Manager](../../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 <span data-ttu-id="da285-112">此轉換有一個輸入和一個輸出。</span><span class="sxs-lookup"><span data-stu-id="da285-112">This transformation has one input and one output.</span></span> <span data-ttu-id="da285-113">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="da285-113">It does not support an error output.</span></span>  
  
 <span data-ttu-id="da285-114">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="da285-114">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="da285-115">如需可在 **[資料採礦查詢轉換編輯器]** 對話方塊中設定之屬性的詳細資訊，請按一下下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="da285-115">For more information about the properties that you can set in the **Data Mining Query Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="da285-116">資料採礦查詢轉換編輯器 &#40;採礦模型索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="da285-116">Data Mining Query Transformation Editor &#40;Mining Model Tab&#41;</span></span>](../../data-mining-query-transformation-editor-mining-model-tab.md)  
  
-   [<span data-ttu-id="da285-117">資料採礦查詢轉換編輯器 &#40;採礦模型索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="da285-117">Data Mining Query Transformation Editor &#40;Mining Model Tab&#41;</span></span>](../../data-mining-query-transformation-editor-mining-model-tab.md)  
  
 <span data-ttu-id="da285-118">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="da285-118">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="da285-119">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="da285-119">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="da285-120">Common Properties</span><span class="sxs-lookup"><span data-stu-id="da285-120">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="da285-121">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="da285-121">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="da285-122">如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="da285-122">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
