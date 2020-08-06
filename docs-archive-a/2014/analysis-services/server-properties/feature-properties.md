---
title: 功能屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQMSupportEnabled property
- ComUdfEnabled property
- LinkToOtherInstanceEnabled property
- ManagedCodeEnabled property
- ConnStringEncryptionEnabled property
- LinkFromOtherInstanceEnabled property
- LinkInsideInstanceEnabled property
- UseCachedPageAllocators property
ms.assetid: a34d046a-6562-4d98-b827-37cebc6d77b4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 08001a172c1b39fb912ef042ed85effd4f8ededa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710865"
---
# <a name="feature-properties"></a><span data-ttu-id="d12dd-102">功能屬性</span><span class="sxs-lookup"><span data-stu-id="d12dd-102">Feature Properties</span></span>
  <span data-ttu-id="d12dd-103">與產品功能有關的功能屬性，大部分是進階屬性，包含控制伺服器執行個體間之連結的屬性。</span><span class="sxs-lookup"><span data-stu-id="d12dd-103">Feature properties pertain to product features, most of them advanced, including properties that control links between server instances.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="d12dd-104">支援下表列出的伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="d12dd-104">supports the server properties listed in the following table.</span></span> <span data-ttu-id="d12dd-105">如需有關其他伺服器屬性及如何設定伺服器屬性的詳細資訊，請參閱＜ [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d12dd-105">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="d12dd-106">**適用物件：** 僅限多維度伺服器模式</span><span class="sxs-lookup"><span data-stu-id="d12dd-106">**Applies to:** Multidimensional server mode only</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d12dd-107">屬性</span><span class="sxs-lookup"><span data-stu-id="d12dd-107">Properties</span></span>  
  
|<span data-ttu-id="d12dd-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d12dd-108">Property</span></span>|<span data-ttu-id="d12dd-109">預設</span><span class="sxs-lookup"><span data-stu-id="d12dd-109">Default</span></span>|<span data-ttu-id="d12dd-110">描述</span><span class="sxs-lookup"><span data-stu-id="d12dd-110">Description</span></span>|  
|--------------|-------------|-----------------|  
|`ManagedCodeEnabled`|<span data-ttu-id="d12dd-111">1</span><span class="sxs-lookup"><span data-stu-id="d12dd-111">1</span></span>|<span data-ttu-id="d12dd-112">此為布林值屬性，指出是否啟用 CLR 儲存程序。</span><span class="sxs-lookup"><span data-stu-id="d12dd-112">A Boolean property that indicates whether CLR storage procedures are enabled.</span></span>|  
|`LinkInsideInstanceEnabled`|<span data-ttu-id="d12dd-113">1</span><span class="sxs-lookup"><span data-stu-id="d12dd-113">1</span></span>|<span data-ttu-id="d12dd-114">此為布林值屬性，指出是否可以在相同的伺服器執行個體內建立連結物件。</span><span class="sxs-lookup"><span data-stu-id="d12dd-114">A Boolean property that indicates whether a linked object can be created inside the same server instance.</span></span>|  
|`LinkToOtherInstanceEnabled`|<span data-ttu-id="d12dd-115">0</span><span class="sxs-lookup"><span data-stu-id="d12dd-115">0</span></span>|<span data-ttu-id="d12dd-116">此為布林值屬性，指出是否可以連結到遠端伺服器上的物件。</span><span class="sxs-lookup"><span data-stu-id="d12dd-116">A Boolean property that indicates whether objects on remote servers can be linked to.</span></span>|  
|`LinkFromOtherInstanceEnabled`|<span data-ttu-id="d12dd-117">0</span><span class="sxs-lookup"><span data-stu-id="d12dd-117">0</span></span>|<span data-ttu-id="d12dd-118">此為布林值屬性，指出是否可從其他伺服器執行個體連結到物件。</span><span class="sxs-lookup"><span data-stu-id="d12dd-118">A Boolean property that indicates whether objects can be linked to from other server instances.</span></span>|  
|`ConnStringEncryptionEnabled`|<span data-ttu-id="d12dd-119">1</span><span class="sxs-lookup"><span data-stu-id="d12dd-119">1</span></span>|<span data-ttu-id="d12dd-120">此為布林值屬性，指出在伺服器組態檔中的連接字串是否有加密。</span><span class="sxs-lookup"><span data-stu-id="d12dd-120">A Boolean property that indicates whether the connection string is encrypted in the server configuration file.</span></span>|  
|`UseCachedPageAllocators`|<span data-ttu-id="d12dd-121">0</span><span class="sxs-lookup"><span data-stu-id="d12dd-121">0</span></span>|<span data-ttu-id="d12dd-122">此為布林值屬性，指出是否啟用快取的頁面配置器。</span><span class="sxs-lookup"><span data-stu-id="d12dd-122">A Boolean property that indicates whether cached page allocators are enabled.</span></span>|  
|`ComUdfEnabled`|<span data-ttu-id="d12dd-123">0</span><span class="sxs-lookup"><span data-stu-id="d12dd-123">0</span></span>|<span data-ttu-id="d12dd-124">此為布林值屬性，指出是否啟用定義為 COM 物件的使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="d12dd-124">A Boolean property that indicates whether user-defined functions defined as COM objects are enabled.</span></span>|  
|`SQMSupportEnabled`|<span data-ttu-id="d12dd-125">1</span><span class="sxs-lookup"><span data-stu-id="d12dd-125">1</span></span>|<span data-ttu-id="d12dd-126">此為布林值屬性，指出錯誤和功能使用方式報表是否自動傳送至 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d12dd-126">A Boolean property that indicates whether error and feature usage reports are sent to [!INCLUDE[msCoName](../../includes/msconame-md.md)] automatically.</span></span>|  
|`ResourceMonitoringEnabled`|<span data-ttu-id="d12dd-127">1</span><span class="sxs-lookup"><span data-stu-id="d12dd-127">1</span></span>|<span data-ttu-id="d12dd-128">此為布林屬性，指出是否啟用內部資源監視計數器。</span><span class="sxs-lookup"><span data-stu-id="d12dd-128">A Boolean property that indicates whether internal resource monitoring counters are enabled.</span></span> <span data-ttu-id="d12dd-129">此屬性預設為啟用。</span><span class="sxs-lookup"><span data-stu-id="d12dd-129">This property is on by default.</span></span> <span data-ttu-id="d12dd-130">啟用時，此屬性可讓計數器收集有關 CPU、記憶體和 I/O 活動的使用量資料。</span><span class="sxs-lookup"><span data-stu-id="d12dd-130">When enabled, this property allows counters to collect usage data about CPU, memory, and I/O activity.</span></span><br /><br /> <span data-ttu-id="d12dd-131">報告有關資源使用量的動態管理檢視 (DMV) 會使用內部資源監視計數器。</span><span class="sxs-lookup"><span data-stu-id="d12dd-131">Internal resource monitoring counters are used by Dynamic Management Views (DMV) that report on resource utilization.</span></span> <span data-ttu-id="d12dd-132">如果您停用此屬性，DMV 查詢仍會執行，但結果集將會無效。</span><span class="sxs-lookup"><span data-stu-id="d12dd-132">If you disable this property, the DMV queries will still run, but the result set will be invalid.</span></span> <span data-ttu-id="d12dd-133">相依於此屬性的 DMV 如下：</span><span class="sxs-lookup"><span data-stu-id="d12dd-133">DMVs that depend on this property include the following:</span></span><br /><span data-ttu-id="d12dd-134">**DISCOVER_OBJECT_ACTIVITY**</span><span class="sxs-lookup"><span data-stu-id="d12dd-134">**DISCOVER_OBJECT_ACTIVITY**</span></span><br /><span data-ttu-id="d12dd-135">**DISCOVER_COMMAND_OBJECTS**</span><span class="sxs-lookup"><span data-stu-id="d12dd-135">**DISCOVER_COMMAND_OBJECTS**</span></span><br /><span data-ttu-id="d12dd-136">**DISCOVER_SESSIONS** (用於 SESSION_READS、SESSION_WRITES、SESSION_CPU_TIME_MS)</span><span class="sxs-lookup"><span data-stu-id="d12dd-136">**DISCOVER_SESSIONS** (for SESSION_READS, SESSION_WRITES, SESSION_CPU_TIME_MS)</span></span><br /><br /> <br /><br /> <span data-ttu-id="d12dd-137">在使用 NUMA 架構的多核心系統上，停用此屬性可以改善查詢效能，尤其是多使用者的高工作負載。</span><span class="sxs-lookup"><span data-stu-id="d12dd-137">On a multi-core system that uses NUMA architecture, disabling this property can improve query performance, particularly for high multi-user workloads.</span></span> <span data-ttu-id="d12dd-138">您將需要執行比較測試，判斷變更此屬性是否使查詢效能獲得改善。</span><span class="sxs-lookup"><span data-stu-id="d12dd-138">You will need to run comparison tests to determine whether query performance is improved as the result of changing this property.</span></span> <span data-ttu-id="d12dd-139">如需執行比較測試的最佳作法，包括清除快取和避免常見的錯誤，請參閱 [SQL Server 2008 R2 Analysis Services 作業指南](https://go.microsoft.com/fwlink/?LinkID=225539)。</span><span class="sxs-lookup"><span data-stu-id="d12dd-139">For best practices on running comparison tests, including clearing the cache and avoiding common mistakes, see the [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d12dd-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d12dd-140">See Also</span></span>  
 <span data-ttu-id="d12dd-141">[在 Analysis Services 中設定伺服器屬性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="d12dd-141">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 <span data-ttu-id="d12dd-142">[判斷 Analysis Services 實例的伺服器模式](../instances/determine-the-server-mode-of-an-analysis-services-instance.md) </span><span class="sxs-lookup"><span data-stu-id="d12dd-142">[Determine the Server Mode of an Analysis Services Instance](../instances/determine-the-server-mode-of-an-analysis-services-instance.md) </span></span>  
 [<span data-ttu-id="d12dd-143">使用動態管理檢視 &#40;DMV&#41; 監視 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="d12dd-143">Use Dynamic Management Views &#40;DMVs&#41; to Monitor Analysis Services</span></span>](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
