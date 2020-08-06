---
title: '[內容] 屬性 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Income property
- InitialBonus property
- PercentScanPerPrice property
- FileStore properties
- BackgroundTrimCost property
- Tax property
- PerformanceTrace property
- MinimumBalance property
- UnbufferedThreshold property
- BackgroundTrimAmount property
- MaximumBalance property
- MemoryLimitMin property
- MemoryLimit property
ms.assetid: 580cf0aa-7425-4d48-aa8d-128f5b488fcd
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc81273b55dea5820ef80f34c22d293492eb8055
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710861"
---
# <a name="filestore-properties"></a><span data-ttu-id="f15ec-102">FileStore 屬性</span><span class="sxs-lookup"><span data-stu-id="f15ec-102">Filestore Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="f15ec-103">支援下表列出的 Filestore 伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="f15ec-103">supports the filestore server properties listed in the following tables.</span></span> <span data-ttu-id="f15ec-104">這些全部都是進階屬性，除非是在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援人員的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="f15ec-104">These are all advanced properties that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span> <span data-ttu-id="f15ec-105">如需有關其他伺服器屬性及如何設定伺服器屬性的詳細資訊，請參閱＜ [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)＞。</span><span class="sxs-lookup"><span data-stu-id="f15ec-105">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="f15ec-106">**適用於：** 多維度與表格式伺服器模式</span><span class="sxs-lookup"><span data-stu-id="f15ec-106">**Applies to:** Multidimensional and Tabular server mode</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f15ec-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f15ec-107">Properties</span></span>  
 `MemoryLimit`  
 <span data-ttu-id="f15ec-108">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="f15ec-108">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryLimitMin`  
 <span data-ttu-id="f15ec-109">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="f15ec-109">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `PercentScanPerPrice`  
 <span data-ttu-id="f15ec-110">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="f15ec-110">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `PerformanceTrace`  
 <span data-ttu-id="f15ec-111">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="f15ec-111">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `RandomFileAccessMode`  
 <span data-ttu-id="f15ec-112">此為布林屬性，指出是否在隨機檔案存取模式下存取資料庫檔案和快取檔案。</span><span class="sxs-lookup"><span data-stu-id="f15ec-112">A Boolean property that indicates whether database files and cached files are accessed in random file access mode.</span></span> <span data-ttu-id="f15ec-113">此屬性預設為關閉。</span><span class="sxs-lookup"><span data-stu-id="f15ec-113">This property is off by default.</span></span> <span data-ttu-id="f15ec-114">Analysis Services 在開啟分割資料檔進行讀取時，預設不會設定隨機檔案存取旗標。</span><span class="sxs-lookup"><span data-stu-id="f15ec-114">By default, Analysis Services does not set the random file access flag when opening partition data files for read access.</span></span>  
  
 <span data-ttu-id="f15ec-115">在高階系統上，尤其是具有大型記憶體資源和多個 NUMA 節點的系統，使用隨機檔案存取會很有幫助。</span><span class="sxs-lookup"><span data-stu-id="f15ec-115">On high-end systems, particularly those with large memory resources and multiple NUMA nodes, it can be advantageous to use random file access.</span></span> <span data-ttu-id="f15ec-116">在隨機存取模式下，Windows 會略過將資料從磁碟讀入系統檔案快取的頁面對應作業，藉此降低快取的競爭情況。</span><span class="sxs-lookup"><span data-stu-id="f15ec-116">In random access mode, Windows bypasses page mapping operations that read data from disk into the system file cache, thereby lowering contention on the cache.</span></span>  
  
 <span data-ttu-id="f15ec-117">您將需要執行比較測試，判斷變更此屬性是否使查詢效能獲得改善。</span><span class="sxs-lookup"><span data-stu-id="f15ec-117">You will need to run comparison tests to determine whether query performance is improved as the result of changing this property.</span></span> <span data-ttu-id="f15ec-118">如需執行比較測試的最佳作法，包括清除快取和避免常見的錯誤，請參閱 [SQL Server 2008 R2 Analysis Services 作業指南](https://go.microsoft.com/fwlink/?LinkID=225539)。</span><span class="sxs-lookup"><span data-stu-id="f15ec-118">For best practices on running comparison tests, including clearing the cache and avoiding common mistakes, see the [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span> <span data-ttu-id="f15ec-119">如需使用此屬性之取捨的詳細資訊，請參閱 [https://support.microsoft.com/kb/2549369](https://support.microsoft.com/kb/2549369) 。</span><span class="sxs-lookup"><span data-stu-id="f15ec-119">For additional information on the tradeoffs of using this property, see [https://support.microsoft.com/kb/2549369](https://support.microsoft.com/kb/2549369).</span></span>  
  
 <span data-ttu-id="f15ec-120">若要在 Management Studio 中檢視或修改這個屬性，請在伺服器屬性頁面中啟用進階屬性清單。</span><span class="sxs-lookup"><span data-stu-id="f15ec-120">To view or modify this property in Management Studio, enable the advanced properties list in the server properties page.</span></span> <span data-ttu-id="f15ec-121">您也可以變更 msmdsrv.ini 檔案中的屬性。</span><span class="sxs-lookup"><span data-stu-id="f15ec-121">You can also change the property in the msmdsrv.ini file.</span></span> <span data-ttu-id="f15ec-122">設定這個屬性之後，建議重新啟動伺服器，否則會繼續在之前的模式下存取已開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="f15ec-122">Restarting the server is recommended after setting this property; otherwise files that are already open will continue to be accessed in the previous mode.</span></span>  
  
 `UnbufferedThreshold`  
 <span data-ttu-id="f15ec-123">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="f15ec-123">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="memory-model-category"></a><span data-ttu-id="f15ec-124">記憶體模型類別目錄</span><span class="sxs-lookup"><span data-stu-id="f15ec-124">Memory Model Category</span></span>  
 `MemoryModel\Tax`  
 <span data-ttu-id="f15ec-125">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="f15ec-125">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryModel\Income`  
 <span data-ttu-id="f15ec-126">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="f15ec-126">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryModel\MaximumBalance`  
 <span data-ttu-id="f15ec-127">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="f15ec-127">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryModel\MinimumBalance`  
 <span data-ttu-id="f15ec-128">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="f15ec-128">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryModel\InitialBonus`  
 <span data-ttu-id="f15ec-129">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="f15ec-129">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15ec-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f15ec-130">See Also</span></span>  
 <span data-ttu-id="f15ec-131">[在 Analysis Services 中設定伺服器屬性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="f15ec-131">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="f15ec-132">判斷 Analysis Services 執行個體的伺服器模式</span><span class="sxs-lookup"><span data-stu-id="f15ec-132">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
