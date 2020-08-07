---
title: 實體架構 (Analysis Services-資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- server architecture [Analysis Services]
- architecture [Analysis Services]
ms.assetid: 25eeecf0-6e85-4527-b94d-5503d27edaed
author: minewiskan
ms.author: owend
ms.openlocfilehash: 787ca28c08dc41a6b9561251077716a406358c6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703465"
---
# <a name="physical-architecture-analysis-services---data-mining"></a><span data-ttu-id="ab3ab-102">實體架構 (Analysis Services – 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="ab3ab-102">Physical Architecture (Analysis Services - Data Mining)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="ab3ab-103">會 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 使用伺服器和用戶端元件，為商業智慧應用程式提供資料採礦功能：</span><span class="sxs-lookup"><span data-stu-id="ab3ab-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses both server and client components to supply data mining functionality for business intelligence applications:</span></span>

-   <span data-ttu-id="ab3ab-104">伺服器元件是以 Microsoft Windows 服務的形式實作。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-104">The server component is implemented as a Microsoft Windows service.</span></span> <span data-ttu-id="ab3ab-105">同一部電腦上可以有多個執行個體，每個 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體都實作為個別的 Windows 服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-105">You can have multiple instances on the same computer, with each instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implemented as a separate instance of the Windows service.</span></span>

-   <span data-ttu-id="ab3ab-106">用戶端使用公用標準 XML for Analysis (XMLA) 與 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 通訊；而 XMLA 是一種用於發出命令和接收回應的 SOAP 型通訊協定，並以 Web 服務的形式公開。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-106">Clients communicate with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using the public standard XML for Analysis (XMLA), a SOAP-based protocol for issuing commands and receiving responses, exposed as a Web service.</span></span> <span data-ttu-id="ab3ab-107">用戶端物件模型也可透過 XMLA 予以提供，且可使用 Managed 提供者 (例如 ADOMD.Net) 或原生 OLE DB 提供者進行存取。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-107">Client object models are also provided over XMLA, and can be accessed either by using a managed provider, such as ADOMD.NET, or a native OLE DB provider.</span></span>

-   <span data-ttu-id="ab3ab-108">可以使用資料採礦延伸模組 (DMX，一種資料採礦導向的業界標準查詢語言) 發出查詢命令。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-108">Query commands can be issued using Data Mining Extensions (DMX), an industry standard query language oriented toward data mining.</span></span> <span data-ttu-id="ab3ab-109">也可以使用 Analysis Services 指令碼語言 (ASSL) 來管理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-109">Analysis Services Scripting Language (ASSL) can also be used to manage [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database objects.</span></span>

## <a name="architectural-diagram"></a><span data-ttu-id="ab3ab-110">架構圖表</span><span class="sxs-lookup"><span data-stu-id="ab3ab-110">Architectural Diagram</span></span>
 <span data-ttu-id="ab3ab-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體會當做獨立服務來執行，並與透過 XML for Analysis (XMLA) 所進行的服務通訊 (使用 HTTP 或 TCP)。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-111">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance runs as a stand-alone service and communication with the service occurs through XML for Analysis (XMLA), by using either HTTP or TCP.</span></span>

 <span data-ttu-id="ab3ab-112">AMO 是介於使用者應用程式與 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體之間的一層，該執行個體會提供對 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理物件的存取權。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-112">AMO is a layer between the user application and the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that provides access to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrative objects.</span></span> <span data-ttu-id="ab3ab-113">AMO 是一個類別庫，它會接收來自用戶端應用程式的命令，並將這些命令轉換成 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的 XMLA 訊息。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-113">AMO is a class library that takes commands from a client application and converts those commands into XMLA messages for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="ab3ab-114">AMO 會使用執行命令的方法成員以及為 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件保存資料的屬性成員，將 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體物件當做類別呈現給使用者應用程式。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-114">AMO presents [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance objects as classes to the end user application, with method members that run commands and property members that hold the data for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects.</span></span>

 <span data-ttu-id="ab3ab-115">下圖顯示 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 元件架構，其中包括 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體內的服務以及與此執行個體互動的使用者元件。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-115">The following illustration shows the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] components architecture, including services within the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and user components that interact with the instance.</span></span>

 <span data-ttu-id="ab3ab-116">下圖顯示存取此執行個體的唯一方法就是使用 XML for Analysis (XMLA) 接聽程式 (利用 HTTP 或 TCP)。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-116">The illustration shows that the only way to access the instance is by using the XML for Analysis (XMLA) Listener, either by using HTTP or TCP.</span></span>

> [!WARNING]
>  <span data-ttu-id="ab3ab-117">DSO 已被取代。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-117">DSO has been deprecated.</span></span> <span data-ttu-id="ab3ab-118">您不應該使用 DSO 來開發方案。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-118">You should not use DSO to develop solutions.</span></span>

 <span data-ttu-id="ab3ab-119">![Analysis Services 系統架構圖表](../dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services 系統架構圖表")</span><span class="sxs-lookup"><span data-stu-id="ab3ab-119">![Analysis Services System Architecture Diagram](../dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services System Architecture Diagram")</span></span>

## <a name="server-configuration"></a><span data-ttu-id="ab3ab-120">伺服器組態</span><span class="sxs-lookup"><span data-stu-id="ab3ab-120">Server Configuration</span></span>
 <span data-ttu-id="ab3ab-121">一個伺服器執行個體可以支援多個 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫，而且每個資料庫都有自己的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服務執行個體，可回應用戶端要求並處理物件。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-121">One server instance can support multiple [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases, each with its own instance of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] service that responds to client requests and processes objects.</span></span>

 <span data-ttu-id="ab3ab-122">如果您想要處理表格式模型和資料採礦及/或多維度模型，則必須安裝個別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-122">Separate instances must be installed if you want to work with both tabular models and data mining and/or multidimensional models.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="ab3ab-123">支援並存安裝表格式模式下所執行的執行個體 (該執行個體會使用 xVelocity 記憶體內部分析引擎 (VertiPaq) 儲存引擎) 以及使用其中一個傳統 OLAP、MOLAP 或 ROLAP 組態所執行的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-123">supports side-by-side installation of instances running in tabular mode (which uses the xVelocity in-memory analytics engine (VertiPaq) storage engine) and instances running in one of the conventional OLAP, MOLAP, or ROLAP configurations.</span></span> <span data-ttu-id="ab3ab-124">如需詳細資訊，請參閱 [判斷 Analysis Services 執行個體的伺服器模式](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-124">For more information, see [Determine the Server Mode of an Analysis Services Instance](../instances/determine-the-server-mode-of-an-analysis-services-instance.md).</span></span>

 <span data-ttu-id="ab3ab-125">用戶端與 Analysis Services 伺服器之間的所有通訊都會使用 XMLA，這是一種與平台和語言無關的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-125">All communications between a client and the Analysis Services server use XMLA, which is a platform-independent and language-independent protocol.</span></span> <span data-ttu-id="ab3ab-126">從用戶端收到要求時，Analysis Services 就會判斷此要求是否與 OLAP 或資料採礦有關，然後適當地路由傳送此要求。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-126">When a request is received from a client, Analysis Services determines whether the request relates to OLAP or data mining, and routes the request appropriately.</span></span> <span data-ttu-id="ab3ab-127">如需詳細資訊，請參閱 [OLAP 引擎伺服器元件](../multidimensional-models/olap-physical/olap-engine-server-components.md)。</span><span class="sxs-lookup"><span data-stu-id="ab3ab-127">For more information, see [OLAP Engine Server Components](../multidimensional-models/olap-physical/olap-engine-server-components.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ab3ab-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab3ab-128">See Also</span></span>
 [<span data-ttu-id="ab3ab-129">邏輯架構 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="ab3ab-129">Logical Architecture &#40;Analysis Services - Data Mining&#41;</span></span>](logical-architecture-analysis-services-data-mining.md)


