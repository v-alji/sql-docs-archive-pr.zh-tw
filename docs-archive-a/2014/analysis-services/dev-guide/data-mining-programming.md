---
title: 資料採礦程式設計 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- data mining [Analysis Services], developer's guide
ms.assetid: 9fd77b16-0b89-44ce-bcf1-7c04b62499da
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd4bd48b5914d5fda89f94c0a959e670ffec3321
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687333"
---
# <a name="data-mining-programming"></a><span data-ttu-id="8a199-102">資料採礦程式設計</span><span class="sxs-lookup"><span data-stu-id="8a199-102">Data Mining Programming</span></span>
  <span data-ttu-id="8a199-103">如果您發現 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的內建工具和檢視器不符合需求，就可以透過編碼自己的延伸模組，擴充 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的功能。</span><span class="sxs-lookup"><span data-stu-id="8a199-103">If you find that the built-in tools and viewers in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] do not meet your requirements, you can extend the power of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by coding your own extensions.</span></span> <span data-ttu-id="8a199-104">在這種方法中，您有兩種選擇：</span><span class="sxs-lookup"><span data-stu-id="8a199-104">In this approach, you have two options:</span></span>  
  
-   <span data-ttu-id="8a199-105">**XMLA**</span><span class="sxs-lookup"><span data-stu-id="8a199-105">**XMLA**</span></span>  
  
     [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="8a199-106">[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]支援 XML for Analysis (XMLA) 做為與用戶端應用程式通訊的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="8a199-106">[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] supports XML for Analysis (XMLA) as a protocol for communication with client applications.</span></span> <span data-ttu-id="8a199-107">擴充 XML for Analysis 規格的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 可支援其他命令。</span><span class="sxs-lookup"><span data-stu-id="8a199-107">Additional commands are supported by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that extend the XML for Analysis specification.</span></span>  
  
     <span data-ttu-id="8a199-108">因為 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會將 XMLA 用於資料定義、資料操作和資料控制支援，所以您可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 提供的視覺化工具來建立採礦結構和採礦模型，然後擴充您之前使用資料採礦延伸模組 (DMX) 和 Analysis Services 指令碼語言 (ASSL) 指令碼所建立的資料採礦物件。</span><span class="sxs-lookup"><span data-stu-id="8a199-108">Because [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses XMLA for data definition, data manipulation, and data control support, you can create mining structures and mining models by using the visual tools provided by [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and then extend the data mining objects that you have created by using Data Mining Extensions (DMX) and Analysis Services Scripting Language (ASSL) scripts.</span></span>  
  
     <span data-ttu-id="8a199-109">您可以完整地在 XMLA 指令碼中建立及修改資料採礦物件，並從您自己的應用程式以程式設計方式針對模型執行預測查詢。</span><span class="sxs-lookup"><span data-stu-id="8a199-109">You can create and modify data mining objects entirely in XMLA scripts, and run prediction queries against the models programmatically from your own applications.</span></span>  
  
-   <span data-ttu-id="8a199-110">**分析管理物件 (AMO)**</span><span class="sxs-lookup"><span data-stu-id="8a199-110">**Analysis Management Objects (AMO)**</span></span>  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="8a199-111">也提供了一個完整架構，可讓協力廠商資料採礦提供者將下列資料採礦物件整合至 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8a199-111">also provides a complete framework that enables third-party data mining providers to integrate the data mining objects into [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="8a199-112">您可以藉由使用 AMO 來建立採礦結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="8a199-112">You can create mining structures and mining models by using AMO.</span></span> <span data-ttu-id="8a199-113">請參閱 CodePlex 中的以下範例：</span><span class="sxs-lookup"><span data-stu-id="8a199-113">See the following samples in CodePlex:</span></span>  
  
    -   <span data-ttu-id="8a199-114">AMO 瀏覽器</span><span class="sxs-lookup"><span data-stu-id="8a199-114">AMO Browser</span></span>  
  
         <span data-ttu-id="8a199-115">連接到您所指定的 SSAS 執行個體，並列出所有伺服器物件及其屬性，包括採礦結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="8a199-115">Connects to the SSAS instance you specify and lists all server objects and their properties, including mining structure and mining models.</span></span>  
  
    -   <span data-ttu-id="8a199-116">AMO Simple 範例</span><span class="sxs-lookup"><span data-stu-id="8a199-116">AMO Simple Sample</span></span>  
  
         <span data-ttu-id="8a199-117">AS Simple 範例涵蓋了大部分主要物件的程式設計存取方式，而且會示範中繼資料瀏覽以及存取物件中的值。</span><span class="sxs-lookup"><span data-stu-id="8a199-117">The AS Simple Sample covers programmatic access to most major objects, and demonstrates metadata browsing, and access to the values in objects.</span></span>  
  
         <span data-ttu-id="8a199-118">此範例也會示範如何建立和處理資料採礦結構和模型，以及瀏覽現有的資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="8a199-118">The sample also demonstrates how to create and process a data mining structure and model, as well as browse an existing data mining model.</span></span>  
  
-   <span data-ttu-id="8a199-119">**DMX-3**</span><span class="sxs-lookup"><span data-stu-id="8a199-119">**DMX**</span></span>  
  
     <span data-ttu-id="8a199-120">您可以使用 DMX 來封裝命令陳述式、預測查詢和中繼資料查詢，並以表格格式傳回結果，前提是您已經建立與 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="8a199-120">You can use DMX to encapsulate command statements, prediction queries, and metadata queries and return results in a tabular format, assuming you have created a connection to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8a199-121">本節內容</span><span class="sxs-lookup"><span data-stu-id="8a199-121">In This Section</span></span>  
 [<span data-ttu-id="8a199-122">OLE DB for Data Mining</span><span class="sxs-lookup"><span data-stu-id="8a199-122">OLE DB for Data Mining</span></span>](../../../2014/analysis-services/dev-guide/ole-db-for-data-mining.md)  
 <span data-ttu-id="8a199-123">描述此規格的添加來支援資料採礦和多維度資料：新的結構描述資料列集和資料行、用來建立和管理採礦結構的資料採礦延伸模組 (DMX) 語言。</span><span class="sxs-lookup"><span data-stu-id="8a199-123">Describes additions to the specification to support data mining and multidimensional data: new schema rowsets and columns, Data Mining Extensions (DMX) language for creating and managing mining structures.</span></span>  
  
## <a name="related-reference"></a><span data-ttu-id="8a199-124">相關的參考資料</span><span class="sxs-lookup"><span data-stu-id="8a199-124">Related Reference</span></span>  
 [<span data-ttu-id="8a199-125">使用 ADOMD.NET 來開發</span><span class="sxs-lookup"><span data-stu-id="8a199-125">Developing with ADOMD.NET</span></span>](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net)  
 <span data-ttu-id="8a199-126">介紹 ADOMD.NET 用戶端和伺服器程式設計物件。</span><span class="sxs-lookup"><span data-stu-id="8a199-126">Introduces ADOMD.NET client and server programming objects.</span></span>  
  
 [<span data-ttu-id="8a199-127">使用分析管理物件 &#40;AMO&#41; 來開發</span><span class="sxs-lookup"><span data-stu-id="8a199-127">Developing with Analysis Management Objects &#40;AMO&#41;</span></span>](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)  
 <span data-ttu-id="8a199-128">介紹 AMO 程式設計程式庫。</span><span class="sxs-lookup"><span data-stu-id="8a199-128">Introduces the AMO programming library.</span></span>  
  
 [<span data-ttu-id="8a199-129">使用 Analysis Services 指令碼語言 &#40;ASSL&#41; 開發</span><span class="sxs-lookup"><span data-stu-id="8a199-129">Developing with Analysis Services Scripting Language &#40;ASSL&#41;</span></span>](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
 <span data-ttu-id="8a199-130">介紹 XML for Analysis (XMLA) 和它的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="8a199-130">Introduces XML for Analysis (XMLA) and its extensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a199-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a199-131">See Also</span></span>  
 <span data-ttu-id="8a199-132">[開發人員指南 &#40;Analysis Services&#41;](../analysis-services-developer-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="8a199-132">[Developer's Guide &#40;Analysis Services&#41;](../analysis-services-developer-documentation.md) </span></span>  
 [<span data-ttu-id="8a199-133">資料採礦延伸模組 &#40;DMX&#41; 參考</span><span class="sxs-lookup"><span data-stu-id="8a199-133">Data Mining Extensions &#40;DMX&#41; Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-reference)  
  
  
