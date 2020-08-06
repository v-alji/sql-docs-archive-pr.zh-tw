---
title: Analysis Services OLE DB Provider (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services OLE DB Provider
ms.assetid: cdeecd50-1d91-4162-a4a2-01c7799b02a8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8c0348a23a6def4c3cdbd083354083947ce1390b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607148"
---
# <a name="analysis-services-ole-db-provider-analysis-services---multidimensional-data"></a><span data-ttu-id="8ac46-102">Analysis Services OLE DB 提供者 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="8ac46-102">Analysis Services OLE DB Provider (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="8ac46-103">Analysis Services OLE DB Provider 是與互動之應用程式的介面 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8ac46-103">The Analysis Services OLE DB Provider is an interface for applications interacting with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="8ac46-104">此介面會用於建立與多維度資料互動的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="8ac46-104">It is used to build client applications that interact with multidimensional data.</span></span> <span data-ttu-id="8ac46-105">這個提供者也提供方法，可針對多維度資料和關聯式資料進行線上和離線的資料採礦分析，而且會包含為 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的一部分，</span><span class="sxs-lookup"><span data-stu-id="8ac46-105">This provider also provides methods for online and offline data mining analysis of multidimensional data and relational data, and is included as part of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="8ac46-106">並且可由協力廠商用戶端應用程式轉散發。</span><span class="sxs-lookup"><span data-stu-id="8ac46-106">It can be redistributed by third-party client applications.</span></span>  
  
 <span data-ttu-id="8ac46-107">Analysis Services OLE DB 提供者是與 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 互動的主要方法，可用於完成與 Cube 或資料採礦模型連接、查詢 Cube 或資料採礦模型，以及擷取結構描述資訊等類工作。</span><span class="sxs-lookup"><span data-stu-id="8ac46-107">The Analysis Services OLE DB Provider is the primary method for interacting with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in order to accomplish such tasks as connecting to a cube or data mining model, querying a cube or data mining model, and retrieving schema information.</span></span>  
  
 <span data-ttu-id="8ac46-108">做為獨立的提供者，Analysis Services OLE DB 提供者可為用戶端應用程式提供從關聯式和多維度來源建立本機 Cube 檔案和採礦模型的能力。</span><span class="sxs-lookup"><span data-stu-id="8ac46-108">As a stand-alone provider, the Analysis Services OLE DB Provider provides client applications with the ability to create local cube files and mining models from relational and multidimensional sources.</span></span> <span data-ttu-id="8ac46-109">用戶端應用程式可以使用多維度運算式 (MDX) 來連接到本機 Cube 並執行查詢，而不必與執行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的完整伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="8ac46-109">Client applications can connect to a local cube and execute queries using Multidimensional Expressions (MDX) without interacting with the full-scale server running the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac46-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ac46-110">See Also</span></span>  
 [<span data-ttu-id="8ac46-111">多維度模型資料存取 &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="8ac46-111">Multidimensional Model Data Access &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)  
  
  
