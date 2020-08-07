---
title: 外掛程式演算法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- third-party algorithms [Analysis Services]
- algorithms [data mining], creating
- plugin algorithms [Analysis Services]
ms.assetid: fe364ddc-576e-42fc-9ced-baa399992f92
author: minewiskan
ms.author: owend
ms.openlocfilehash: ebc5e007dcc6de7fb25d59547e21f1e892100570
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703457"
---
# <a name="plugin-algorithms"></a><span data-ttu-id="89034-102">外掛程式演算法</span><span class="sxs-lookup"><span data-stu-id="89034-102">Plugin Algorithms</span></span>
  <span data-ttu-id="89034-103">除了提供的演算法以外 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，還有其他許多演算法可供您用來進行資料採礦。</span><span class="sxs-lookup"><span data-stu-id="89034-103">In addition to the algorithms that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides, there are many other algorithms that you can use for data mining.</span></span> <span data-ttu-id="89034-104">因此， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會為協力廠商所建立的「外掛程式」演算法提供一項機制。</span><span class="sxs-lookup"><span data-stu-id="89034-104">Accordingly, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides a mechanism for "plugging in" algorithms that are created by third parties.</span></span> <span data-ttu-id="89034-105">只要演算法遵循特定的標準，就可以在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 內使用，就像使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法一樣。</span><span class="sxs-lookup"><span data-stu-id="89034-105">As long as the algorithms follow certain standards, you can use them within [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] just as you use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms.</span></span> <span data-ttu-id="89034-106">外掛程式演算法具有提供的所有演算法功能 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="89034-106">Plugin algorithms have all the capabilities of algorithms that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides.</span></span>  
  
 <span data-ttu-id="89034-107">如需 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 用於與外掛程式演算法通訊之介面的完整描述，請參閱建立自訂演算法和自訂模型檢視器的範例，這些範例會在 [CodePlex](https://go.microsoft.com/fwlink/?LinkID=87843) 網站上發佈。</span><span class="sxs-lookup"><span data-stu-id="89034-107">For a full description of the interfaces that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses to communicate with plugin algorithms, see the samples for creating a custom algorithm and custom model viewer that are published on [CodePlex](https://go.microsoft.com/fwlink/?LinkID=87843) Web site.</span></span>  
  
## <a name="algorithm-requirements"></a><span data-ttu-id="89034-108">演算法需求</span><span class="sxs-lookup"><span data-stu-id="89034-108">Algorithm Requirements</span></span>  
 <span data-ttu-id="89034-109">若要將演算法外掛至 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]，您必須實作下列 COM 介面：</span><span class="sxs-lookup"><span data-stu-id="89034-109">To plug an algorithm into [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you must implement the following COM interfaces:</span></span>  
  
 `IDMAlgorithm`  
 <span data-ttu-id="89034-110">實作會產生模型的演算法，並實作結果模型的預測作業。</span><span class="sxs-lookup"><span data-stu-id="89034-110">Implements an algorithm that produces models, and implements the prediction operations of the resulting models.</span></span>  
  
 `IDMAlgorithmNavigation`  
 <span data-ttu-id="89034-111">允許瀏覽器存取模型的內容。</span><span class="sxs-lookup"><span data-stu-id="89034-111">Enables browsers to access the content of the models.</span></span>  
  
 `IDMPersist`  
 <span data-ttu-id="89034-112">允許 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]儲存和載入演算法定型的模型。</span><span class="sxs-lookup"><span data-stu-id="89034-112">Enables the models that the algorithm trains to be saved and loaded by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 `IDMAlgorithmMetadata`  
 <span data-ttu-id="89034-113">描述演算法的功能和輸入參數。</span><span class="sxs-lookup"><span data-stu-id="89034-113">Describes the capabilities and input parameters of the algorithm.</span></span>  
  
 `IDMAlgorithmFactory`  
 <span data-ttu-id="89034-114">為實作演算法介面的物件建立執行個體，並允許 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 存取演算法中繼資料介面。</span><span class="sxs-lookup"><span data-stu-id="89034-114">Creates instances of the objects that implement the algorithm interface, and provides [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] with access to the algorithm-metadata interface.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="89034-115">會使用這些 COM 介面與外掛程式演算法通訊。</span><span class="sxs-lookup"><span data-stu-id="89034-115">uses these COM interfaces to communicate with plugin algorithms.</span></span> <span data-ttu-id="89034-116">雖然您使用的外掛程式演算法必須支援 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB for Data Mining 規格，但不必支援該規格中的所有資料採礦選項。</span><span class="sxs-lookup"><span data-stu-id="89034-116">Although plugin algorithms that you use must support the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB for Data Mining specification, they do not have to support all the data mining options in the specification.</span></span> <span data-ttu-id="89034-117">您可以使用 [MINING_SERVICES](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset) 結構描述資料列集，來決定演算法的功能。</span><span class="sxs-lookup"><span data-stu-id="89034-117">You can use the [MINING_SERVICES](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset) schema rowset to determine the capabilities of an algorithm.</span></span> <span data-ttu-id="89034-118">此結構描述資料列集，會列出每一個外掛程式演算法提供者的資料採礦支援選項。</span><span class="sxs-lookup"><span data-stu-id="89034-118">This schema rowset lists the data mining support options for each plugin algorithm provider.</span></span>  
  
 <span data-ttu-id="89034-119">您必須先註冊新的演算法，才能與 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]一起使用。</span><span class="sxs-lookup"><span data-stu-id="89034-119">You must register new algorithms before you use them with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="89034-120">若要註冊演算法，請在您要包含演算法之 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的 .ini 檔案中包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="89034-120">To register an algorithm, include the following information in the .ini file of the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] on which you want to include the algorithms:</span></span>  
  
-   <span data-ttu-id="89034-121">演算法名稱</span><span class="sxs-lookup"><span data-stu-id="89034-121">The algorithm name</span></span>  
  
-   <span data-ttu-id="89034-122">ProgID (這是選擇性，且只有外掛程式演算法才會包含)</span><span class="sxs-lookup"><span data-stu-id="89034-122">ProgID (this is optional and will only be included for plugin algorithms)</span></span>  
  
-   <span data-ttu-id="89034-123">指出是否啟用演算法的旗標</span><span class="sxs-lookup"><span data-stu-id="89034-123">A flag that indicates whether the algorithm is enabled or not</span></span>  
  
 <span data-ttu-id="89034-124">下列程式碼範例說明如何註冊新的演算法：</span><span class="sxs-lookup"><span data-stu-id="89034-124">The following code sample illustrates how to register a new algorithm:</span></span>  
  
 `<ConfigurationSettings>`  
  
 `...`  
  
 `<DataMining>`  
  
 `...`  
  
 `<Algorithms>`  
  
 `...`  
  
 `<Sample_Plugin_Algorithm>`  
  
 `<Enabled>1</Enabled>`  
  
 `<ProgID>Microsoft.DataMining.SamplePlugInAlgorithm.Factory</ProgID>`  
  
 `</Sample_PlugIn_Algorithm>`  
  
 `...`  
  
 `</Algorithms>`  
  
 `...`  
  
 `</DataMining>`  
  
 `...`  
  
 `</ConfigurationSettings>`  
  
## <a name="see-also"></a><span data-ttu-id="89034-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89034-125">See Also</span></span>  
 <span data-ttu-id="89034-126">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="89034-126">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="89034-127">DMSCHEMA_MINING_SERVICES 資料列集</span><span class="sxs-lookup"><span data-stu-id="89034-127">DMSCHEMA_MINING_SERVICES Rowset</span></span>](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset)  
  
  
