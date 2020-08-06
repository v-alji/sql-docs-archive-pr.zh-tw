---
title: 記憶體屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- LowMemoryLimit property
- MinimumAllocatedMemory property
- MidMemoryPrice property
- MemoryHeapType property
- memory [Analysis Services]
- DefaultPagesCountToReuse property
- TotalMemoryLimit property
- SessionMemoryLimit property
- VirtualMemoryLimit property
- WaitCountIfHighMemory property
- HighMemoryPrice property
- HeapTypeForObjects property
ms.assetid: 085f5195-7b2c-411a-9813-0ff5c6066d13
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f2d2e56c9a951cee27752bd57d55d185a9b6618
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710842"
---
# <a name="memory-properties"></a><span data-ttu-id="58be7-102">記憶體屬性</span><span class="sxs-lookup"><span data-stu-id="58be7-102">Memory Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="58be7-103">支援下表列出的伺服器記憶體屬性。</span><span class="sxs-lookup"><span data-stu-id="58be7-103">supports the server memory properties listed in the following table.</span></span> <span data-ttu-id="58be7-104">如需設定這些屬性的指引，請參閱《 [SQL Server 2008 R2 Analysis Services 操作指南](https://go.microsoft.com/fwlink/?LinkID=225539)》。</span><span class="sxs-lookup"><span data-stu-id="58be7-104">For guidance in setting these properties, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 <span data-ttu-id="58be7-105">1 - 100 之間的值代表 **實體記憶體總計** 或 **虛擬位址空間**的百分比，以較少者為準。</span><span class="sxs-lookup"><span data-stu-id="58be7-105">Values between 1 and 100 represent percentages of **Total Physical Memory** or **Virtual Address Space**, whichever is less.</span></span> <span data-ttu-id="58be7-106">超過 100 的值代表記憶體限制 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="58be7-106">Values over 100 represent memory limits in bytes.</span></span>  
  
 <span data-ttu-id="58be7-107">**適用物件：** 多維度和表格式伺服器模式（除非另有指示）。</span><span class="sxs-lookup"><span data-stu-id="58be7-107">**Applies to:** Multidimensional and Tabular server mode, unless noted otherwise.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="58be7-108">屬性</span><span class="sxs-lookup"><span data-stu-id="58be7-108">Properties</span></span>  
 `LowMemoryLimit`  
 <span data-ttu-id="58be7-109">帶正負號的 64 位元雙精確度浮點數屬性，此屬性定義一個臨界值，低於此值即表示伺服器記憶體不足 (以總實體記憶體的百分比表示)。</span><span class="sxs-lookup"><span data-stu-id="58be7-109">A signed 64-bit double-precision floating-point number property that defines the point at which the server is low on memory, expressed as percentage of total physical memory.</span></span> <span data-ttu-id="58be7-110">達到此限制時，執行個體將會開始關閉到期的工作階段並卸載未使用的計算，藉以緩慢地將記憶體清出快取。</span><span class="sxs-lookup"><span data-stu-id="58be7-110">When this limit is reached, the instance will start to slowly clear memory out of caches by closing expired sessions and unloading unused calculations.</span></span> <span data-ttu-id="58be7-111">伺服器不會在低於此限制時釋出記憶體。</span><span class="sxs-lookup"><span data-stu-id="58be7-111">The server will not release memory below this limit.</span></span> <span data-ttu-id="58be7-112">預設值 65，表示記憶體下限為實體記憶體或虛擬位址空間的 65%，以較少者為準。</span><span class="sxs-lookup"><span data-stu-id="58be7-112">The default value is 65; which indicates the low memory limit is 65% of physical memory or the virtual address space, whichever is less.</span></span>  
  
 `TotalMemoryLimit`  
 <span data-ttu-id="58be7-113">定義達到時的臨界值，讓伺服器更積極地取消配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="58be7-113">Defines a threshold that when reached, causes the server to deallocate memory more aggressively.</span></span> <span data-ttu-id="58be7-114">預設值 80% 的實體記憶體或虛擬位址空間的 65%，以較少者為準。</span><span class="sxs-lookup"><span data-stu-id="58be7-114">The default value 80% of physical memory or the virtual address space, whichever is less.</span></span>  
  
 <span data-ttu-id="58be7-115">請注意，`TotalMemoryLimit` 永遠必須小於 `HardMemoryLimit`</span><span class="sxs-lookup"><span data-stu-id="58be7-115">Note that `TotalMemoryLimit` must always be less than `HardMemoryLimit`</span></span>  
  
 `HardMemoryLimit`  
 <span data-ttu-id="58be7-116">指定記憶體閾值，超過此閥值後，執行個體會積極地終止使用中的使用者工作階段以減少記憶體的使用量。</span><span class="sxs-lookup"><span data-stu-id="58be7-116">Specifies a memory threshold after which the instance aggressively terminates active user sessions to reduce memory usage.</span></span> <span data-ttu-id="58be7-117">所有終止的工作階段都會收到一個因為記憶體不足的壓力而取消的錯誤。</span><span class="sxs-lookup"><span data-stu-id="58be7-117">All terminated sessions will receive an error about being cancelled by memory pressure.</span></span> <span data-ttu-id="58be7-118">預設值零 (0)，代表 `HardMemoryLimit` 會設定為 `TotalMemoryLimit` 和系統總實體記憶體之間的中間值；若系統的實體記憶體大於處理序的虛擬位址空間，則會改用虛擬位址空間來計算 `HardMemoryLimit`。</span><span class="sxs-lookup"><span data-stu-id="58be7-118">The default value, zero (0), means the `HardMemoryLimit` will be set to a midway value between `TotalMemoryLimit` and the total physical memory of the system; if the physical memory of the system is larger than the virtual address space of the process, then virtual address space will be used instead to calculate `HardMemoryLimit`.</span></span>  
  
 `VirtualMemoryLimit`  
 <span data-ttu-id="58be7-119">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="58be7-119">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `VertiPaqPagingPolicy`  
 <span data-ttu-id="58be7-120">指定伺服器記憶體不足時的分頁行為。</span><span class="sxs-lookup"><span data-stu-id="58be7-120">Specifies the paging behavior in the event the server runs low on memory.</span></span> <span data-ttu-id="58be7-121">下列是有效值：</span><span class="sxs-lookup"><span data-stu-id="58be7-121">Valid values are as follows:</span></span>  
  
 <span data-ttu-id="58be7-122">零 (**0**) 停用分頁。</span><span class="sxs-lookup"><span data-stu-id="58be7-122">Zero (**0**) disables paging.</span></span> <span data-ttu-id="58be7-123">如果記憶體不足，處理會失敗，且會出現記憶體不足的錯誤。</span><span class="sxs-lookup"><span data-stu-id="58be7-123">If memory is insufficient, processing fails with an out-of-memory error.</span></span> <span data-ttu-id="58be7-124">如果您停用分頁，就必須授與 Windows 權限給服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="58be7-124">If you disable paging, you must grant Windows privileges to the service account.</span></span> <span data-ttu-id="58be7-125">如需指示，請參閱[設定服務帳戶 &#40;Analysis Services&#41;](../instances/configure-service-accounts-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="58be7-125">See [Configure Service Accounts &#40;Analysis Services&#41;](../instances/configure-service-accounts-analysis-services.md) for instructions.</span></span>  
  
 <span data-ttu-id="58be7-126">**1** 是預設值。</span><span class="sxs-lookup"><span data-stu-id="58be7-126">**1** is the default.</span></span> <span data-ttu-id="58be7-127">此屬性允許使用作業系統分頁檔 (pagefile.sys)，在磁碟中分頁。</span><span class="sxs-lookup"><span data-stu-id="58be7-127">This property enables paging to disk using the operating system page file (pagefile.sys).</span></span>  
  
 <span data-ttu-id="58be7-128">當 `VertiPaqPagingPolicy` 設為 1 時，處理比較不可能因為記憶體限制而失敗，因為伺服器將會嘗試使用您指定的方法，在磁碟中分頁。</span><span class="sxs-lookup"><span data-stu-id="58be7-128">When `VertiPaqPagingPolicy` is set to 1, processing is less likely to fail due to memory constraints because the server will try to page to disk using the method that you specified.</span></span> <span data-ttu-id="58be7-129">設定 `VertiPaqPagingPolicy` 屬性並不能保證記憶體錯誤永遠不會發生。</span><span class="sxs-lookup"><span data-stu-id="58be7-129">Setting the `VertiPaqPagingPolicy` property does not guarantee that memory errors will never happen.</span></span> <span data-ttu-id="58be7-130">在下列狀況下，記憶體不足錯誤仍然可能發生：</span><span class="sxs-lookup"><span data-stu-id="58be7-130">Out of memory errors can still occur under the following conditions:</span></span>  
  
-   <span data-ttu-id="58be7-131">記憶體不足以供所有字典使用。</span><span class="sxs-lookup"><span data-stu-id="58be7-131">There is not enough memory for all dictionaries.</span></span> <span data-ttu-id="58be7-132">處理期間，Analysis Services 會針對記憶體中的每個資料行鎖定字典，所有這些字典不可大於 `VertiPaqMemoryLimit` 的指定值。</span><span class="sxs-lookup"><span data-stu-id="58be7-132">During processing, Analysis Services locks the dictionaries for each column in memory, and all of these together cannot be more than the value specified for `VertiPaqMemoryLimit`.</span></span>  
  
-   <span data-ttu-id="58be7-133">虛擬位址空間不足以容納處理序。</span><span class="sxs-lookup"><span data-stu-id="58be7-133">There is insufficient virtual address space to accommodate the process.</span></span>  
  
 <span data-ttu-id="58be7-134">若要解決持續發生的記憶體不足錯誤，您可以嘗試重新設計模型，減少需要處理的資料量，或在電腦上加入更多的實體記憶體。</span><span class="sxs-lookup"><span data-stu-id="58be7-134">To resolve persistent out of memory errors, you can either try to redesign the model to reduce the amount of data that needs processing, or you can add more physical memory to the computer.</span></span>  
  
 <span data-ttu-id="58be7-135">僅適用於表格式伺服器模式。</span><span class="sxs-lookup"><span data-stu-id="58be7-135">Applies to tabular server mode only.</span></span>  
  
 `VertiPaqMemoryLimit`  
 <span data-ttu-id="58be7-136">如果允許在磁碟中分頁，此使用會指定分頁開始的記憶體耗用量 (以總記憶體的百分比表示) 層級。</span><span class="sxs-lookup"><span data-stu-id="58be7-136">If paging to disk is allowed, this property specifies the level of memory consumption (as a percentage of total memory) at which paging starts.</span></span> <span data-ttu-id="58be7-137">預設值是 60。</span><span class="sxs-lookup"><span data-stu-id="58be7-137">The default is 60.</span></span> <span data-ttu-id="58be7-138">如果記憶體耗用量低於 60%，伺服器將不會磁碟中分頁。</span><span class="sxs-lookup"><span data-stu-id="58be7-138">If memory consumption is less than 60 percent, the server will not page to disk.</span></span>  
  
 <span data-ttu-id="58be7-139">此屬性相依於 `VertiPaqPagingPolicyProperty`，且必須設為 1，才會進行分頁。</span><span class="sxs-lookup"><span data-stu-id="58be7-139">This property depends on the `VertiPaqPagingPolicyProperty`, which must be set to 1 in order for paging to occur.</span></span>  
  
 <span data-ttu-id="58be7-140">僅適用於表格式伺服器模式。</span><span class="sxs-lookup"><span data-stu-id="58be7-140">Applies to tabular server mode only.</span></span>  
  
 `HighMemoryPrice`  
 <span data-ttu-id="58be7-141">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="58be7-141">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryHeapType`  
 <span data-ttu-id="58be7-142">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="58be7-142">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="58be7-143">僅適用於多維度伺服器模式。</span><span class="sxs-lookup"><span data-stu-id="58be7-143">Applies to multidimensional server mode only.</span></span>  
  
 `HeapTypeForObjects`  
 <span data-ttu-id="58be7-144">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="58be7-144">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="58be7-145">僅適用於多維度伺服器模式。</span><span class="sxs-lookup"><span data-stu-id="58be7-145">Applies to multidimensional server mode only.</span></span>  
  
 `DefaultPagesCountToReuse`  
 <span data-ttu-id="58be7-146">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="58be7-146">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `HandleIA64AlignmentFaults`  
 <span data-ttu-id="58be7-147">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="58be7-147">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MidMemoryPrice`  
 <span data-ttu-id="58be7-148">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="58be7-148">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MinimumAllocatedMemory`  
 <span data-ttu-id="58be7-149">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="58be7-149">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `PreAllocate`  
 <span data-ttu-id="58be7-150">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="58be7-150">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SessionMemoryLimit`  
 <span data-ttu-id="58be7-151">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="58be7-151">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `WaitCountIfHighMemory`  
 <span data-ttu-id="58be7-152">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="58be7-152">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58be7-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58be7-153">See Also</span></span>  
 <span data-ttu-id="58be7-154">[在 Analysis Services 中設定伺服器屬性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="58be7-154">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="58be7-155">判斷 Analysis Services 執行個體的伺服器模式</span><span class="sxs-lookup"><span data-stu-id="58be7-155">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
