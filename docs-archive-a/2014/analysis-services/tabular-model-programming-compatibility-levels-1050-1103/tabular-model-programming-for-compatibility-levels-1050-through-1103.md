---
title: 表格式模型程式設計 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 0ceb461e-12c1-44ea-97ac-b99bf308676b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2565ed28a882750ab9b37beadbce698d3a0abb19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710838"
---
# <a name="tabular-model-programming"></a><span data-ttu-id="77f8e-102">表格式模型程式設計</span><span class="sxs-lookup"><span data-stu-id="77f8e-102">Tabular Model Programming</span></span>
  <span data-ttu-id="77f8e-103">表格式模型使用關聯式建構，將分析和報表應用程式所使用的 Analysis Services 資料模型化。</span><span class="sxs-lookup"><span data-stu-id="77f8e-103">Tabular models use relational constructs to model the Analysis Services data used by analytical and reporting applications.</span></span> <span data-ttu-id="77f8e-104">這些模型在設定為表格式模式的 Analysis Service 執行個體上執行，對儲存體使用記憶體中分析引擎，以及在要求資料時執行彙總和計算資料的快速資料表掃描。</span><span class="sxs-lookup"><span data-stu-id="77f8e-104">These models run on an Analysis Service instance that is configured for tabular mode, using an in-memory analytics engine for storage and fast table scans that aggregate and calculate data as it is requested.</span></span>  
  
 <span data-ttu-id="77f8e-105">在程式設計方面，您在 AMO、ADOMD.NET、XMLA 或 OLE DB 中使用的物件對表格式和多維度方案來說基本上都是相同。</span><span class="sxs-lookup"><span data-stu-id="77f8e-105">Programmatically, the objects you work with in AMO, ADOMD.NET, XMLA, or OLE DB are fundamentally the same for both tabular and multidimensional solutions.</span></span> <span data-ttu-id="77f8e-106">如果表格式模型資料庫最能符合您的自訂 BI 方案需求，您可以使用任何 Analysis Services 用戶端程式庫和程式設計介面，將您的應用程式與 Analysis Services 執行個體上的表格式模型整合。</span><span class="sxs-lookup"><span data-stu-id="77f8e-106">If the requirements of your custom BI solution are best met by a tabular model database, you can use any of the Analysis Services client libraries and programming interfaces to integrate your application with tabular models on an Analysis Services instance.</span></span> <span data-ttu-id="77f8e-107">若要查詢和計算表格式模型資料，您可以在程式碼中使用內嵌 MDX 或 DAX。</span><span class="sxs-lookup"><span data-stu-id="77f8e-107">To query and calculate tabular model data, you can use either embedded MDX or DAX in your code.</span></span>  
  
 <span data-ttu-id="77f8e-108">本節提供有關如何以程式設計方式使用表格式模型實體及其屬性的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="77f8e-108">This section provides more information about how you can programmatically work with tabular model entities and their properties.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="77f8e-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="77f8e-109">In This Section</span></span>  
 [<span data-ttu-id="77f8e-110">商業智慧的 CSDL 註解 &#40;CSDLBI&#41;</span><span class="sxs-lookup"><span data-stu-id="77f8e-110">CSDL Annotations for Business Intelligence &#40;CSDLBI&#41;</span></span>](/analysis-services/csdlbi/csdl-annotations-for-business-intelligence-csdlbi)  
  
 [<span data-ttu-id="77f8e-111">了解表格式物件模型</span><span class="sxs-lookup"><span data-stu-id="77f8e-111">Understanding the Tabular Object Model</span></span>](representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
 [<span data-ttu-id="77f8e-112">CSDL 之 BI 註解的技術參考</span><span class="sxs-lookup"><span data-stu-id="77f8e-112">Technical Reference for BI Annotations to CSDL</span></span>](/analysis-services/csdlbi/technical-reference-for-bi-annotations-to-csdl)  
  
 [<span data-ttu-id="77f8e-113">IMDEmbedded 介面</span><span class="sxs-lookup"><span data-stu-id="77f8e-113">IMDEmbedded Interface</span></span>](imdembeddeddata-interface.md)  
  
## <a name="see-also"></a><span data-ttu-id="77f8e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77f8e-114">See Also</span></span>  
 <span data-ttu-id="77f8e-115">[&#40;SSAS 表格式&#41;的表格式模型](../tabular-models/tabular-models-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="77f8e-115">[Tabular Modeling &#40;SSAS Tabular&#41;](../tabular-models/tabular-models-ssas.md) </span></span>  
 [<span data-ttu-id="77f8e-116">表格式模型設計師 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="77f8e-116">Tabular Model Designer &#40;SSAS Tabular&#41;</span></span>](../tabular-model-designer-ssas-tabular.md)  
  
  
