---
title: XMLA 概念 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, concepts
ms.assetid: 816183a7-d2f7-4e14-8e5b-2a4c1798fbc1
author: minewiskan
ms.author: owend
ms.openlocfilehash: b2e18917b56d40f8b813ba10083cc1b408e51a98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598023"
---
# <a name="xmla-concepts"></a><span data-ttu-id="af679-102">XMLA 概念</span><span class="sxs-lookup"><span data-stu-id="af679-102">XMLA Concepts</span></span>
  <span data-ttu-id="af679-103">XML for Analysis (XMLA) 開放標準支援對位於全球資訊網上的資料來源進行資料存取。</span><span class="sxs-lookup"><span data-stu-id="af679-103">The XML for Analysis (XMLA) open standard supports data access to data sources that reside on the World Wide Web.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="af679-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 根據 xmla 1.1 規格來執行 xmla。</span><span class="sxs-lookup"><span data-stu-id="af679-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] implements XMLA per the XMLA 1.1 specification.</span></span>  
  
 <span data-ttu-id="af679-105">XML for Analysis (XMLA) 是以簡易物件存取通訊協定 (SOAP) 為基礎的 XML 通訊協定，它是特別針對位在網路上的任何標準多維度資料來源進行通用資料存取而設計。</span><span class="sxs-lookup"><span data-stu-id="af679-105">XML for Analysis (XMLA) is a Simple Object Access Protocol (SOAP)-based XML protocol, designed specifically for universal data access to any standard multidimensional data source residing on the Web.</span></span> <span data-ttu-id="af679-106">XMLA 也不需要部署會公開元件物件模型 (COM) 或 .NET Framework 介面的用戶端元件 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="af679-106">XMLA also eliminates the need to deploy a client component that exposes Component Object Model (COM) or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework interfaces.</span></span> <span data-ttu-id="af679-107">XMLA 是針對網際網路最佳化，因為在這種環境下，往返伺服器的作業會耗用大量的時間和資源，而且資料來源的可設定狀態連接可能會限制伺服器上的使用者連接。</span><span class="sxs-lookup"><span data-stu-id="af679-107">XMLA is optimized for the Internet, when round trips to the server are expensive in terms of time and resources, and when stateful connections to a data source can limit user connections on the server.</span></span>  
  
 <span data-ttu-id="af679-108">XMLA 是的原生通訊協定 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ，用於用戶端應用程式和實例之間的所有互動 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="af679-108">XMLA is the native protocol for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], used for all interaction between a client application and an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="af679-109">完全支援 XML for Analysis 1.1，而且也提供延伸模組以支援中繼資料管理、工作階段管理以及鎖定功能。</span><span class="sxs-lookup"><span data-stu-id="af679-109">fully supports XML for Analysis 1.1, and also provides extensions to support metadata management, session management, and locking capabilities.</span></span> <span data-ttu-id="af679-110">分析管理物件 (AMO) 與 ADOMD.NET 在與 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 執行個體通訊時，會使用 XMLA 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="af679-110">Both Analysis Management Objects (AMO) and ADOMD.NET use the XMLA protocol when communicating with an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="handling-xmla-communications"></a><span data-ttu-id="af679-111">處理 XMLA 通訊</span><span class="sxs-lookup"><span data-stu-id="af679-111">Handling XMLA Communications</span></span>  
 <span data-ttu-id="af679-112">XMLA 開放標準描述兩種普遍可存取的方法：`Discover` 與 `Execute`。</span><span class="sxs-lookup"><span data-stu-id="af679-112">The XMLA open standard describes two generally accessible methods: `Discover` and `Execute`.</span></span> <span data-ttu-id="af679-113">這些方法使用 XML 支援的鬆散偶合的用戶端與伺服器架構，以處理 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 執行個體的傳入和傳出資訊。</span><span class="sxs-lookup"><span data-stu-id="af679-113">These methods use the loosely-coupled client and server architecture supported by XML to handle incoming and outgoing information on an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="af679-114">`Discover` 方法可從 Web 服務取得資訊與中繼資料。</span><span class="sxs-lookup"><span data-stu-id="af679-114">The `Discover` method obtains information and metadata from a Web service.</span></span> <span data-ttu-id="af679-115">這個資訊可包括可用資料來源的清單，以及有關任何資料來源提供者的資訊。</span><span class="sxs-lookup"><span data-stu-id="af679-115">This information can include a list of available data sources, as well as information about any of the data source providers.</span></span> <span data-ttu-id="af679-116">屬性會定義和塑造從資料來源取得的資料。</span><span class="sxs-lookup"><span data-stu-id="af679-116">Properties define and shape the data that is obtained from a data source.</span></span> <span data-ttu-id="af679-117">用戶端應用程式可能會需要來自 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 執行個體資料來源的許多資訊，`Discover` 方法正是定義這些資訊類型的常見方法。</span><span class="sxs-lookup"><span data-stu-id="af679-117">The `Discover` method is a common method for defining the many types of information a client application may require from data sources on [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instances.</span></span> <span data-ttu-id="af679-118">屬性與泛型介面提供的擴充性，讓您不需要在用戶端應用程式中重新撰寫已有的函數。</span><span class="sxs-lookup"><span data-stu-id="af679-118">The properties and the generic interface provide extensibility without requiring you to rewrite existing functions in a client application.</span></span>  
  
 <span data-ttu-id="af679-119">`Execute` 方法可讓應用程式針對 XMLA 資料來源執行提供者特定的命令。</span><span class="sxs-lookup"><span data-stu-id="af679-119">The `Execute` method allows applications to run provider-specific commands against XMLA data sources.</span></span>  
  
 <span data-ttu-id="af679-120">雖然 XMLA 通訊協定是針對 Web 應用程式最佳化，它也可以供 LAN 導向的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="af679-120">Although the XMLA protocol is optimized for Web applications, it can also be leveraged for LAN-oriented applications.</span></span> <span data-ttu-id="af679-121">下列應用程式可以從這個以 XML 為基礎的 API 獲益：</span><span class="sxs-lookup"><span data-stu-id="af679-121">The following applications can benefit from this XML-based API:</span></span>  
  
-   <span data-ttu-id="af679-122">在用戶端與伺服器之間需要彈性技術的用戶端/伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="af679-122">Client/server applications that require flexible technology between clients and the server</span></span>  
  
-   <span data-ttu-id="af679-123">以多個作業系統為目標的用戶端/伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="af679-123">Client/server applications that target multiple operating systems</span></span>  
  
-   <span data-ttu-id="af679-124">不需要重要狀態以增加伺服器容量的用戶端</span><span class="sxs-lookup"><span data-stu-id="af679-124">Clients that do not require significant state in order to increase server capacity</span></span>  
  
## <a name="xmla-and-the-unified-dimensional-model"></a><span data-ttu-id="af679-125">XMLA 與統一維度模型</span><span class="sxs-lookup"><span data-stu-id="af679-125">XMLA and the Unified Dimensional Model</span></span>  
 <span data-ttu-id="af679-126">XMLA 是運用統一維度模型 (UDM) 方法的商業智慧應用程式所使用的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="af679-126">XMLA is the protocol used by business intelligence applications that employ the Unified Dimensional Model (UDM) methodology</span></span>  
  
  
