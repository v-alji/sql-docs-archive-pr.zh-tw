---
title: 資料處理延伸模組概觀 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], about extensions
ms.assetid: 1d652605-9313-4c75-98b4-ba4dcbbb222d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5e589d3a4e090aee52d2590c0b2ccff435c2321a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594944"
---
# <a name="data-processing-extensions-overview"></a><span data-ttu-id="4ff8d-102">資料處理延伸模組概觀</span><span class="sxs-lookup"><span data-stu-id="4ff8d-102">Data Processing Extensions Overview</span></span>
  <span data-ttu-id="4ff8d-103">在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的資料處理延伸模組，可讓您連接到資料來源並擷取資料。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-103">Data processing extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enable you to connect to a data source and retrieve data.</span></span> <span data-ttu-id="4ff8d-104">它們也可當做資料來源與資料集之間的橋樑。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-104">They also serve as a bridge between a data source and a dataset.</span></span> <span data-ttu-id="4ff8d-105">因為 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組是依照 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 資料提供者介面子集建立的。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-105">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extensions are modeled after a subset of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data provider interfaces.</span></span>

 <span data-ttu-id="4ff8d-106">下表列出 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 隨附的資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-106">The following table lists the data processing extensions included with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>

|<span data-ttu-id="4ff8d-107">資料處理延伸模組</span><span class="sxs-lookup"><span data-stu-id="4ff8d-107">Data processing extension</span></span>|<span data-ttu-id="4ff8d-108">描述</span><span class="sxs-lookup"><span data-stu-id="4ff8d-108">Description</span></span>|
|-------------------------------|-----------------|
|<span data-ttu-id="4ff8d-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的資料處理延伸模組</span><span class="sxs-lookup"><span data-stu-id="4ff8d-109">Data processing extension for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span></span>|<span data-ttu-id="4ff8d-110">使用 .NET Framework Data Provider for SQL Server 來連線和擷取 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 的資料。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-110">Uses the .NET Framework Data Provider for SQL Server to connect to and retrieve data from the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span>|
|<span data-ttu-id="4ff8d-111">OLE DB 的資料處理延伸模組</span><span class="sxs-lookup"><span data-stu-id="4ff8d-111">Data processing extension for OLE DB</span></span>|<span data-ttu-id="4ff8d-112">使用 .NET Framework Data Provider for OLE DB。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-112">Uses the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="4ff8d-113">透過這個延伸模組，報表伺服器可以查詢具有 OLE DB 提供者的資料來源。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-113">With this extension, the report server can query any data source that has an OLE DB provider.</span></span>|
|<span data-ttu-id="4ff8d-114">Oracle 的資料處理延伸模組</span><span class="sxs-lookup"><span data-stu-id="4ff8d-114">Data processing extension for Oracle</span></span>|<span data-ttu-id="4ff8d-115">使用 .NET Framework Data Provider for Oracle。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-115">Uses the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="4ff8d-116">透過這個延伸模組，報表伺服器可以藉由 Oracle 用戶端連接軟體存取 Oracle 資料來源。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-116">With this extension, the report server can access Oracle data sources through Oracle client connectivity software.</span></span>|
|<span data-ttu-id="4ff8d-117">ODBC 的資料處理延伸模組</span><span class="sxs-lookup"><span data-stu-id="4ff8d-117">Data processing extension for ODBC</span></span>|<span data-ttu-id="4ff8d-118">使用 .NET Framework Data Provider for ODBC。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-118">Uses the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="4ff8d-119">透過這個延伸模組，報表伺服器可以存取具有 ODBC 驅動程式之資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-119">With this extension, the report server can access data in any database for which there is an ODBC driver.</span></span>|

 <span data-ttu-id="4ff8d-120">您可以使用 [!INCLUDE[ssRS](../../../includes/ssrs.md)] 資料處理 API 將自訂資料處理加入報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-120">You can use the [!INCLUDE[ssRS](../../../includes/ssrs.md)] data processing API to add custom data processing to your report server.</span></span>

> [!NOTE]
>  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="4ff8d-121">為 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中的資料提供者提供了內建支援。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-121">has built-in support for data providers in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="4ff8d-122">如果您已實作完整的資料提供者，就不需要實作 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-122">If you have already implemented a full data provider, you do not need to implement a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension.</span></span> <span data-ttu-id="4ff8d-123">不過，您應該考慮擴充資料提供者，使其得以涵蓋 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 2005 的特定功能，例如安全的連接認證與伺服器端的彙總。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-123">However, you should consider extending your data provider to include functionality specific to [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 2005, which includes secure connection credentials and server-side aggregates.</span></span>

 <span data-ttu-id="4ff8d-124">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 隨附的每個資料處理延伸模組會使用一組共用的介面。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-124">Each of the data processing extensions included with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] uses a common set of interfaces.</span></span> <span data-ttu-id="4ff8d-125">這可確保每個延伸模組都會實作可比較的功能。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-125">This ensures that each extension implements comparable functionality.</span></span>

 <span data-ttu-id="4ff8d-126">您可以為自己的資料來源開發資料處理延伸模組，或使用介面來將其他資料處理層加入共同的資料庫基礎結構。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-126">You can develop data processing extensions for your own data sources, or you can use the interfaces to add an additional layer of data processing to common database infrastructures.</span></span> <span data-ttu-id="4ff8d-127">您可以部署自訂資料處理延伸模組，以將資料緊密整合到組織中的現有報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-127">You can deploy your custom data processing extensions to enable seamless integration of data into the existing report servers in your organization.</span></span> <span data-ttu-id="4ff8d-128">這些自訂資料處理延伸模組也可以做為提供給客戶之自訂報表套件的一部分。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-128">You can also use them as part of a custom reporting suite that you provide to your consumers.</span></span>

 <span data-ttu-id="4ff8d-129">![資料處理延伸模組架構](../../media/bk-dataprocess-extensions.gif "資料處理延伸模組架構")Reporting Services 資料處理延伸模組架構</span><span class="sxs-lookup"><span data-stu-id="4ff8d-129">![Data processing extension architecture](../../media/bk-dataprocess-extensions.gif "Data processing extension architecture") Reporting Services data processing extension architecture</span></span>

 <span data-ttu-id="4ff8d-130">實作自訂 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組有下列幾項優點：</span><span class="sxs-lookup"><span data-stu-id="4ff8d-130">The advantages to implementing a custom [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension include:</span></span>

-   <span data-ttu-id="4ff8d-131">簡化資料存取架構，通常可提供較佳的可維護性與更高的效能。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-131">A simplified data access architecture, often with better maintainability and improved performance.</span></span>

-   <span data-ttu-id="4ff8d-132">直接向取用者公開延伸模組特定功能。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-132">The ability to directly expose extension-specific functionality to consumers.</span></span>

-   <span data-ttu-id="4ff8d-133">提供取用者特定介面，供其存取 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的資料來源。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-133">A specific interface for your consumers to access your data source within [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>

## <a name="data-extension-process-flow"></a><span data-ttu-id="4ff8d-134">資料延伸模組處理流量</span><span class="sxs-lookup"><span data-stu-id="4ff8d-134">Data Extension Process Flow</span></span>
 <span data-ttu-id="4ff8d-135">開發自訂資料延伸模組之前，應該先了解報表伺服器如何使用資料延伸模組處理資料，</span><span class="sxs-lookup"><span data-stu-id="4ff8d-135">Before developing your custom data extension, you should understand how the report server uses data extensions to process data.</span></span> <span data-ttu-id="4ff8d-136">並熟悉報表伺服器呼叫的建構函式與方法。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-136">You should also understand the constructors and methods that are called by the report server.</span></span>

 <span data-ttu-id="4ff8d-137">![資料處理延伸模組的處理](../../media/bk-ext-01.gif "資料處理延伸模組的處理流程")流程報表伺服器所呼叫之資料延伸模組的逐步程式流程</span><span class="sxs-lookup"><span data-stu-id="4ff8d-137">![Process flow for data processing extension](../../media/bk-ext-01.gif "Process flow for data processing extension") The step-by-step process flow of a data extension that is called by the report server</span></span>

 <span data-ttu-id="4ff8d-138">圖例中顯示了下列事件的順序：</span><span class="sxs-lookup"><span data-stu-id="4ff8d-138">The illustration shows the following sequence of events:</span></span>

1.  <span data-ttu-id="4ff8d-139">報表伺服器會建立連接物件，並傳遞與報表關聯的連接字串與認證。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-139">The report server creates a connection object and passes in the connection string and credentials associated with the report.</span></span>

2.  <span data-ttu-id="4ff8d-140">報表的命令文字會用以建立命令物件。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-140">The command text of the report is used to create a command object.</span></span> <span data-ttu-id="4ff8d-141">在程序中，資料處理延伸模組可能包含剖析命令文字以及為命令建立任何參數的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-141">In the process, the data processing extension may include code that parses the command text and creates any parameters for the command.</span></span>

3.  <span data-ttu-id="4ff8d-142">處理命令物件與任何參數之後，就會產生資料讀取器，以傳回結果集並允許報表伺服器將報表資料與報表配置相關聯。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-142">Once the command object and any parameters are processed, a data reader is generated that returns a result set and enables the report server to associate the report data with the report layout.</span></span>

## <a name="developer-requirements"></a><span data-ttu-id="4ff8d-143">開發人員需求</span><span class="sxs-lookup"><span data-stu-id="4ff8d-143">Developer Requirements</span></span>
 <span data-ttu-id="4ff8d-144">若要開發 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組，您需要：</span><span class="sxs-lookup"><span data-stu-id="4ff8d-144">Developing a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension requires you to have:</span></span>

-   <span data-ttu-id="4ff8d-145">已安裝報表設計師或報表伺服器的部署電腦。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-145">A deployment computer with Report Designer or a report server installed.</span></span>

-   <span data-ttu-id="4ff8d-146">[!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)]已安裝或更新版本或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 軟體發展工具組 (SDK) 的開發電腦。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-146">A development computer with [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] or above, or the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Software Development Kit (SDK) installed.</span></span>

-   <span data-ttu-id="4ff8d-147">對 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的特性與功能有深入的了解。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-147">An in-depth understanding of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] features and capabilities.</span></span>

-   <span data-ttu-id="4ff8d-148">深入瞭解 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 架構、 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 資料提供者、ADO.NET 資料集物件和通用 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 介面。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-148">An in-depth understanding of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] architecture, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data providers, ADO.NET DataSet objects, and the common [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] interfaces.</span></span>

-   <span data-ttu-id="4ff8d-149">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual c # 或 .net 等語言的開發經驗 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4ff8d-149">Development experience in a [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] language such as [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ff8d-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ff8d-150">See Also</span></span>
 <span data-ttu-id="4ff8d-151">延伸模組連結[庫 Reporting Services](../reporting-services-extension-library.md) [Reporting Services](../reporting-services-extensions.md)延伸模組</span><span class="sxs-lookup"><span data-stu-id="4ff8d-151">[Reporting Services Extensions](../reporting-services-extensions.md) [Reporting Services Extension Library](../reporting-services-extension-library.md)</span></span>


