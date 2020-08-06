---
title: OLAP 引擎伺服器元件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- ports [Analysis Services]
- XML/A listener
- server architecture [Analysis Services]
ms.assetid: 5193c976-9dcd-459c-abba-8c3c44e7a7f2
author: minewiskan
ms.author: owend
ms.openlocfilehash: b60d721a69213ad52536830b49b40d6bb82a3811
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707938"
---
# <a name="olap-engine-server-components"></a><span data-ttu-id="590e2-102">OLAP 引擎伺服器元件</span><span class="sxs-lookup"><span data-stu-id="590e2-102">OLAP Engine Server Components</span></span>
  <span data-ttu-id="590e2-103">的伺服器元件 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 是**msmdsrv.exe**應用程式，它會以 Windows 服務的形式執行。</span><span class="sxs-lookup"><span data-stu-id="590e2-103">The server component of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] is the **msmdsrv.exe** application, which runs as a Windows service.</span></span> <span data-ttu-id="590e2-104">這個應用程式是由安全性元件、XML for Analysis (XMLA) 接聽程式元件、查詢處理器元件及執行下列功能的許多其他內部元件所組成：</span><span class="sxs-lookup"><span data-stu-id="590e2-104">This application consists of security components, an XML for Analysis (XMLA) listener component, a query processor component and numerous other internal components that perform the following functions:</span></span>

-   <span data-ttu-id="590e2-105">剖析從用戶端收到的陳述式</span><span class="sxs-lookup"><span data-stu-id="590e2-105">Parsing statements received from clients</span></span>

-   <span data-ttu-id="590e2-106">管理中繼資料</span><span class="sxs-lookup"><span data-stu-id="590e2-106">Managing metadata</span></span>

-   <span data-ttu-id="590e2-107">處理交易</span><span class="sxs-lookup"><span data-stu-id="590e2-107">Handling transactions</span></span>

-   <span data-ttu-id="590e2-108">處理計算</span><span class="sxs-lookup"><span data-stu-id="590e2-108">Processing calculations</span></span>

-   <span data-ttu-id="590e2-109">儲存維度和資料格資料</span><span class="sxs-lookup"><span data-stu-id="590e2-109">Storing dimension and cell data</span></span>

-   <span data-ttu-id="590e2-110">建立彙總</span><span class="sxs-lookup"><span data-stu-id="590e2-110">Creating aggregations</span></span>

-   <span data-ttu-id="590e2-111">排程查詢</span><span class="sxs-lookup"><span data-stu-id="590e2-111">Scheduling queries</span></span>

-   <span data-ttu-id="590e2-112">快取物件</span><span class="sxs-lookup"><span data-stu-id="590e2-112">Caching objects</span></span>

-   <span data-ttu-id="590e2-113">管理伺服器資源</span><span class="sxs-lookup"><span data-stu-id="590e2-113">Managing server resources</span></span>

## <a name="architectural-diagram"></a><span data-ttu-id="590e2-114">架構圖表</span><span class="sxs-lookup"><span data-stu-id="590e2-114">Architectural Diagram</span></span>
 <span data-ttu-id="590e2-115">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 執行個體會當做獨立服務來執行，並與透過 XML for Analysis (XMLA) 所進行的服務通訊 (使用 HTTP 或 TCP)。</span><span class="sxs-lookup"><span data-stu-id="590e2-115">An [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance runs as a stand-alone service and communication with the service occurs through XML for Analysis (XMLA), by using either HTTP or TCP.</span></span> <span data-ttu-id="590e2-116">AMO 是使用者應用程式與 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 執行個體之間的一層。</span><span class="sxs-lookup"><span data-stu-id="590e2-116">AMO is a layer between the user application and the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="590e2-117">這一層提供了對 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 管理物件的存取。</span><span class="sxs-lookup"><span data-stu-id="590e2-117">This layer provides access to [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] administrative objects.</span></span> <span data-ttu-id="590e2-118">AMO 是一個類別庫，它會接收來自用戶端應用程式的命令，並將這些命令轉換成 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 執行個體的 XMLA 訊息。</span><span class="sxs-lookup"><span data-stu-id="590e2-118">AMO is a class library that takes commands from a client application and converts those commands into XMLA messages for the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="590e2-119">AMO 會使用執行命令的方法成員以及為 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 物件保存資料的屬性成員，將 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 執行個體物件當做類別呈現給使用者應用程式。</span><span class="sxs-lookup"><span data-stu-id="590e2-119">AMO presents [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance objects as classes to the end user application, with method members that run commands and property members that hold the data for the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] objects.</span></span>

 <span data-ttu-id="590e2-120">下圖顯示 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 元件架構，其中包括在 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 執行個體內執行的所有主要元素以及與此執行個體互動的所有使用者元件。</span><span class="sxs-lookup"><span data-stu-id="590e2-120">The following illustration shows the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] components architecture, including all major elements running within the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance and all user components that interact with the instance.</span></span> <span data-ttu-id="590e2-121">下圖也會顯示存取此執行個體的唯一方法，就是使用 XML for Analysis (XMLA) 接聽程式 (利用 HTTP 或 TCP)。</span><span class="sxs-lookup"><span data-stu-id="590e2-121">The illustration also shows that the only way to access the instance is by using the XML for Analysis (XMLA) Listener, either by using HTTP or TCP.</span></span>

 <span data-ttu-id="590e2-122">![Analysis Services 系統架構圖表](../../../analysis-services/dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services 系統架構圖表")</span><span class="sxs-lookup"><span data-stu-id="590e2-122">![Analysis Services System Architecture Diagram](../../../analysis-services/dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services System Architecture Diagram")</span></span>

## <a name="xmla-listener"></a><span data-ttu-id="590e2-123">XMLA 接聽程式</span><span class="sxs-lookup"><span data-stu-id="590e2-123">XMLA Listener</span></span>
 <span data-ttu-id="590e2-124">XMLA 接聽程式元件會處理 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 及其用戶端之間的所有 XMLA 通訊。</span><span class="sxs-lookup"><span data-stu-id="590e2-124">The XMLA listener component handles all XMLA communications between [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] and its clients.</span></span> <span data-ttu-id="590e2-125">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] `Port` msmdsrv.ini 檔案中的設定可以用來指定實例接聽的通訊埠 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="590e2-125">The [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] `Port` configuration setting in the msmdsrv.ini file can be used to specify a port on which an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance listens.</span></span> <span data-ttu-id="590e2-126">這個檔案中 0 的值表示 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 會接聽預設通訊埠。</span><span class="sxs-lookup"><span data-stu-id="590e2-126">A value of 0 in this file indicates that [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] listen on the default port.</span></span> <span data-ttu-id="590e2-127">除非另有指定，否則 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 會使用下列預設 TCP 通訊埠：</span><span class="sxs-lookup"><span data-stu-id="590e2-127">Unless otherwise specified, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] uses the following default TCP ports:</span></span>

|<span data-ttu-id="590e2-128">連接埠</span><span class="sxs-lookup"><span data-stu-id="590e2-128">Port</span></span>|<span data-ttu-id="590e2-129">描述</span><span class="sxs-lookup"><span data-stu-id="590e2-129">Description</span></span>|
|----------|-----------------|
|<span data-ttu-id="590e2-130">2383</span><span class="sxs-lookup"><span data-stu-id="590e2-130">2383</span></span>|<span data-ttu-id="590e2-131">的預設實例 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="590e2-131">Default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|
|<span data-ttu-id="590e2-132">2382</span><span class="sxs-lookup"><span data-stu-id="590e2-132">2382</span></span>|<span data-ttu-id="590e2-133">其他實例的重新導向程式 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="590e2-133">Redirector for other instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|
|<span data-ttu-id="590e2-134">在伺服器啟動時動態指派</span><span class="sxs-lookup"><span data-stu-id="590e2-134">Dynamically assigned at server startup</span></span>|<span data-ttu-id="590e2-135">的命名實例 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="590e2-135">Named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|

 <span data-ttu-id="590e2-136">如需詳細資訊，請參閱[設定 Windows 防火牆以允許 Analysis Services 存取](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)。</span><span class="sxs-lookup"><span data-stu-id="590e2-136">See [Configure the Windows Firewall to Allow Analysis Services Access](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) for more details.</span></span>

## <a name="see-also"></a><span data-ttu-id="590e2-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="590e2-137">See Also</span></span>
 <span data-ttu-id="590e2-138">[物件命名規則 &#40;Analysis Services&#41;](object-naming-rules-analysis-services.md) [實體架構 &#40;Analysis Services-多維度資料](understanding-microsoft-olap-physical-architecture.md)&#41;[邏輯架構 &#40;Analysis Services 多維度資料&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)</span><span class="sxs-lookup"><span data-stu-id="590e2-138">[Object Naming Rules &#40;Analysis Services&#41;](object-naming-rules-analysis-services.md) [Physical Architecture &#40;Analysis Services - Multidimensional Data&#41;](understanding-microsoft-olap-physical-architecture.md) [Logical Architecture &#40;Analysis Services - Multidimensional Data&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)</span></span>


