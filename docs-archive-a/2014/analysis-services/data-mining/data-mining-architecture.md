---
title: 資料採礦架構 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 105f52e1-ad3b-4cd0-b67b-06dbb451c304
author: minewiskan
ms.author: owend
ms.openlocfilehash: a372972fd7fa39f7bcfd2e10abbc4fbf8f8c10aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599272"
---
# <a name="data-mining-architecture"></a><span data-ttu-id="f067d-102">資料採礦架構</span><span class="sxs-lookup"><span data-stu-id="f067d-102">Data Mining Architecture</span></span>
  <span data-ttu-id="f067d-103">本節描述在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的執行個體內裝載的資料採礦方案架構。</span><span class="sxs-lookup"><span data-stu-id="f067d-103">This section describes the architecture of data mining solutions that are hosted in an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="f067d-104">本節的主題描述可支援資料採礦之 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的邏輯和實體架構，也提供有關用戶端、提供者和通訊協定的資訊，該通訊協定可用來與資料採礦伺服器通訊以及在本機或遠端搭配資料採礦物件使用。</span><span class="sxs-lookup"><span data-stu-id="f067d-104">The topics in this section describe the logical and physical architecture of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that supports data mining, and also provide information about the clients, providers, and protocols that can be used to communicate with data mining servers, and to work with data mining objects either locally or remotely.</span></span>  
  
 <span data-ttu-id="f067d-105">一般來說，SQL Server 資料採礦會當做於多維度模式下執行之 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體一部分的服務來操作；因此，我們建議您也要檢閱以下線上叢書中描述 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 多維度方案操作、維護和組態的章節。</span><span class="sxs-lookup"><span data-stu-id="f067d-105">In general, SQL Server Data Mining operates as a service that is provided as part of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance running in multidimensional mode; therefore, we recommend that you also review the following sections of Books Online that describe the operation, maintenance, and configuration of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] multidimensional solutions.</span></span>  
  
 [<span data-ttu-id="f067d-106">多維度模型物件處理</span><span class="sxs-lookup"><span data-stu-id="f067d-106">Multidimensional Model Object Processing</span></span>](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)  
  
 [<span data-ttu-id="f067d-107">連接到 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="f067d-107">Connect to Analysis Services</span></span>](../instances/connect-to-analysis-services.md)  
  
 [<span data-ttu-id="f067d-108">資料庫儲存位置</span><span class="sxs-lookup"><span data-stu-id="f067d-108">Database Storage Location</span></span>](../multidimensional-models/database-storage-location.md)  
  
 [<span data-ttu-id="f067d-109">在 ReadOnly 和 ReadWrite 模式之間切換 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="f067d-109">Switch an Analysis Services database between ReadOnly and ReadWrite modes</span></span>](../multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
 <span data-ttu-id="f067d-110">如需有關如何在商務智慧方案中實作資料採礦的詳細資訊，請參閱 MSDN Library 的＜方案指南＞章節。</span><span class="sxs-lookup"><span data-stu-id="f067d-110">For more information about how you can implement data mining in your business intelligence solution, see the Solution Guides section of the MSDN Library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f067d-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="f067d-111">In This Section</span></span>  
 [<span data-ttu-id="f067d-112">邏輯架構 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="f067d-112">Logical Architecture &#40;Analysis Services - Data Mining&#41;</span></span>](logical-architecture-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="f067d-113">實體架構 &#40;Analysis Services – 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="f067d-113">Physical Architecture &#40;Analysis Services - Data Mining&#41;</span></span>](physical-architecture-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="f067d-114">資料採礦服務與資料來源</span><span class="sxs-lookup"><span data-stu-id="f067d-114">Data Mining Services and Data Sources</span></span>](data-mining-services-and-data-sources.md)  
  
 [<span data-ttu-id="f067d-115">資料採礦方案與物件的管理</span><span class="sxs-lookup"><span data-stu-id="f067d-115">Management of Data Mining Solutions and Objects</span></span>](management-of-data-mining-solutions-and-objects.md)  
  
 [<span data-ttu-id="f067d-116">安全性概觀 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="f067d-116">Security Overview &#40;Data Mining&#41;</span></span>](security-overview-data-mining.md)  
  
## <a name="see-also"></a><span data-ttu-id="f067d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f067d-117">See Also</span></span>  
 <span data-ttu-id="f067d-118">[多維度模型程式設計](../multidimensional-models/multidimensional-model-programming.md) </span><span class="sxs-lookup"><span data-stu-id="f067d-118">[Multidimensional Model Programming](../multidimensional-models/multidimensional-model-programming.md) </span></span>  
 [<span data-ttu-id="f067d-119">資料採礦程式設計</span><span class="sxs-lookup"><span data-stu-id="f067d-119">Data Mining Programming</span></span>](../dev-guide/data-mining-programming.md)  
  
  
