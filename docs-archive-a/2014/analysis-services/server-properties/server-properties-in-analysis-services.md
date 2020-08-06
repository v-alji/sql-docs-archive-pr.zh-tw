---
title: 在 Analysis Services 中設定伺服器屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SSAS, configuration properties
- Analysis Services, configuration properties
- SQL Server Analysis Services, configuration properties
- configuration options [Analysis Services]
- server properties [Analysis Services]
- properties [Analysis Services], configuration
- properties [Analysis Services]
ms.assetid: 274b89cd-14ed-4666-bc13-eedf1de51e18
author: minewiskan
ms.author: owend
ms.openlocfilehash: 087154756960c6d53fbd66ca4c111ac157503a53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595303"
---
# <a name="configure-server-properties-in-analysis-services"></a><span data-ttu-id="f9dc6-102">在 Analysis Services 中設定伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="f9dc6-102">Configure Server Properties in Analysis Services</span></span>
  <span data-ttu-id="f9dc6-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理員可以修改 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的預設伺服器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-103">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrator can modify default server configuration properties for an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="f9dc6-104">每一個執行個體都有自己的組態屬性，可以在同一部伺服器上與其他執行個體分開設定。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-104">Each instance has its own configuration properties that can be set independently of other instances on the same server.</span></span>  
  
 <span data-ttu-id="f9dc6-105">若要設定伺服器屬性，請使用 SQL Server Management Studio，或是編輯特定執行個體的 msmdsrv.ini 檔。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-105">To set server properties, use SQL Server Management Studio or edit the msmdsrv.ini file of a specific instance.</span></span>  
  
 <span data-ttu-id="f9dc6-106">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="f9dc6-106">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="f9dc6-107">設定伺服器 (執行個體) 屬性</span><span class="sxs-lookup"><span data-stu-id="f9dc6-107">Configure Server (Instance) Properties</span></span>](#bkmk_config)  
  
 [<span data-ttu-id="f9dc6-108">伺服器屬性參考</span><span class="sxs-lookup"><span data-stu-id="f9dc6-108">Server Property Reference</span></span>](#bkmk_ref)  
  
##  <a name="configure-server-instance-properties"></a><a name="bkmk_config"></a><span data-ttu-id="f9dc6-109">設定伺服器 (實例) 屬性</span><span class="sxs-lookup"><span data-stu-id="f9dc6-109">Configure Server (Instance) Properties</span></span>  
 <span data-ttu-id="f9dc6-110">SQL Server Management Studio 中的屬性頁包含可用屬性的子集，其中只會顯示較可能修改的屬性。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-110">The property pages in SQL Server Management Studio contain a subset of the available properties, showing only those properties that are more likely to be modified.</span></span> <span data-ttu-id="f9dc6-111">完整的屬性集可以在 msmdsrv.ini 檔中找到。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-111">The full set of properties can be found in the msmdsrv.ini file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9dc6-112">本主題沒有在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中記載部署組態屬性。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-112">This topic does not document the deployment configuration properties in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="f9dc6-113">如需部署設定的詳細資訊，請參閱[指定解決方案部署的設定](../multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-113">For more information about deployment configuration, see [Specifying Configuration Settings for Solution Deployment](../multidimensional-models/deployment-script-files-solution-deployment-config-settings.md).</span></span>  
  
#### <a name="view-or-set-configuration-properties-in-management-studio"></a><span data-ttu-id="f9dc6-114">在 Management Studio 中檢視或設定組態屬性</span><span class="sxs-lookup"><span data-stu-id="f9dc6-114">View or set configuration properties in Management Studio</span></span>  
  
1.  <span data-ttu-id="f9dc6-115">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
     <span data-ttu-id="f9dc6-116">在物件總管中，以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-116">In Object Explorer, right-click the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, and then click **Properties**.</span></span> <span data-ttu-id="f9dc6-117">[一般] 頁面隨即顯示，其中顯示最常使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-117">The General page appears, displaying the more commonly used properties.</span></span>  
  
2.  <span data-ttu-id="f9dc6-118">若要檢視其他屬性，請按一下頁面底部的 [顯示進階 (全部) 屬性]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-118">To view additional properties, click the **Show Advanced (All) Properties** checkbox at the bottom of the page.</span></span>  
  
     <span data-ttu-id="f9dc6-119">只有表格式模式和多維度模式伺服器支援修改伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-119">Modifying server properties is supported only for tabular mode and multidimensional mode servers.</span></span> <span data-ttu-id="f9dc6-120">如果您已安裝 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]，除非 Microsoft 產品支援工程師另有指示，否則請務必使用預設值。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-120">If you installed [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], always use the default values unless you are directed otherwise by a Microsoft product support engineer.</span></span>  
  
     <span data-ttu-id="f9dc6-121">如需如何透過伺服器屬性處理操作或效能問題的指示，請參閱＜ [SQL Server 2008 R2 Analysis Services 作業指南](https://go.microsoft.com/fwlink/?LinkID=225539)＞。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-121">For guidance on how to address operational or performance issues through server properties, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
     <span data-ttu-id="f9dc6-122">您也可以在此 Microsoft 技術白皮書 [SQL Server 2005 Analysis Services (SSAS) 伺服器屬性](https://go.microsoft.com/fwlink/?LinkID=199102)中閱讀有關伺服器屬性 (在最後幾個版本中大部分未變更) 的資訊。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-122">You can also read about server properties (many of which are unchanged over the last several releases) in this Microsoft white paper, [SQL Server 2005 Analysis Services (SSAS) Server Properties](https://go.microsoft.com/fwlink/?LinkID=199102).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f9dc6-123">部分屬性只能在 msmdrsrv.ini 檔中設定。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-123">Some properties can only be set in the msmdrsrv.ini file.</span></span> <span data-ttu-id="f9dc6-124">如果即使在顯示進階屬性之後仍看不到您要設定的屬性，可能需要直接編輯 msmdsrv.ini 檔。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-124">If the property you want to set is not visible even after you show advanced properties, you might need to edit the msmdsrv.ini file directly.</span></span>  
  
#### <a name="view-or-edit-configuration-properties-in-the-msmdsrvini-file"></a><span data-ttu-id="f9dc6-125">在 msmdsrv.ini 檔中檢視或編輯組態屬性</span><span class="sxs-lookup"><span data-stu-id="f9dc6-125">View or edit configuration properties in the msmdsrv.ini file</span></span>  
  
1.  <span data-ttu-id="f9dc6-126">在開始進行之前，請先檢查 Management Studio 中 [一般] 屬性頁的 **[DataDir]** 屬性，以確認 Analysis Services 程式檔的位置，包括 msmdsrv.ini 檔。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-126">Before you begin, check the **DataDir** property in the General property page in Management Studio to verify the location of the Analysis Services program files, including the msmdsrv.ini file.</span></span> <span data-ttu-id="f9dc6-127">確認程式檔的位置將可確保您修改的檔案是正確的。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-127">Verifying the location of the program files will ensure that you are modifying the correct file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f9dc6-128">在預設安裝中，檔案位於 \Program Files\Microsoft SQL Server\MSAS12.MSSQLSERVER\OLAP\Config 資料夾中</span><span class="sxs-lookup"><span data-stu-id="f9dc6-128">In a default installation, the file can be found in the \Program Files\Microsoft SQL Server\MSAS12.MSSQLSERVER\OLAP\Config folder</span></span>  
  
2.  <span data-ttu-id="f9dc6-129">建立檔案的備份，以免需要還原原始檔案。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-129">Create a backup of the file in case you need to revert to the original file.</span></span>  
  
3.  <span data-ttu-id="f9dc6-130">使用文字編輯器檢視或編輯 msmdsrv.ini 檔。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-130">Use a text editor to view or edit the msmdsrv.ini file.</span></span>  
  
4.  <span data-ttu-id="f9dc6-131">在您儲存檔案之後，必須重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-131">After you save the file, you must restart the service.</span></span>  
  
##  <a name="server-property-reference"></a><a name="bkmk_ref"></a> <span data-ttu-id="f9dc6-132">伺服器屬性參考</span><span class="sxs-lookup"><span data-stu-id="f9dc6-132">Server Property Reference</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="f9dc6-133">組態屬性對於微調您的系統而言很重要。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-133">configuration properties are important for fine tuning your system.</span></span> <span data-ttu-id="f9dc6-134">例如，若要使查詢記錄行為與您的需求一致，您可以設定相關屬性。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-134">For example, to make query log behavior consistent with your requirements, you can set the relevant properties.</span></span>  
  
 <span data-ttu-id="f9dc6-135">下列主題說明各種 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 組態屬性：</span><span class="sxs-lookup"><span data-stu-id="f9dc6-135">The following topics explain the various [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] configuration properties:</span></span>  
  
|<span data-ttu-id="f9dc6-136">主題</span><span class="sxs-lookup"><span data-stu-id="f9dc6-136">Topic</span></span>|<span data-ttu-id="f9dc6-137">描述</span><span class="sxs-lookup"><span data-stu-id="f9dc6-137">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f9dc6-138">一般屬性</span><span class="sxs-lookup"><span data-stu-id="f9dc6-138">General Properties</span></span>](general-properties.md)|<span data-ttu-id="f9dc6-139">一般屬性是基本和進階屬性，並且包含定義資料目錄、備份目錄和其他伺服器行為的屬性。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-139">The general properties are both basic and advanced properties, and include properties that define the data directory, backup directory, and other server behaviors.</span></span>|  
|[<span data-ttu-id="f9dc6-140">資料採礦屬性</span><span class="sxs-lookup"><span data-stu-id="f9dc6-140">Data Mining Properties</span></span>](data-mining-properties.md)|<span data-ttu-id="f9dc6-141">資料採礦屬性控制要啟用和停用哪些資料採礦演算法。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-141">The data mining properties control which data mining algorithms are enabled and which are disabled.</span></span> <span data-ttu-id="f9dc6-142">依預設，會啟用所有的演算法。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-142">By default, all of the algorithms are enabled.</span></span>|  
|<span data-ttu-id="f9dc6-143">DSO</span><span class="sxs-lookup"><span data-stu-id="f9dc6-143">DSO</span></span>|<span data-ttu-id="f9dc6-144">不再支援 DSO。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-144">DSO is no longer supported.</span></span> <span data-ttu-id="f9dc6-145">DSO 屬性會遭到忽略。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-145">DSO properties are ignored.</span></span>|  
|[<span data-ttu-id="f9dc6-146">Feature 屬性</span><span class="sxs-lookup"><span data-stu-id="f9dc6-146">Feature Properties</span></span>](feature-properties.md)|<span data-ttu-id="f9dc6-147">與產品功能有關的功能屬性，大部分是進階屬性，包含控制伺服器執行個體間之連結的屬性。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-147">The feature properties pertain to product features, most of them advanced, including properties that control links between server instances.</span></span>|  
|<span data-ttu-id="f9dc6-148">[[內容] 屬性](filestore-properties.md)</span><span class="sxs-lookup"><span data-stu-id="f9dc6-148">[Filestore Properties](filestore-properties.md)</span></span>|<span data-ttu-id="f9dc6-149">檔案存放區屬性僅供進階使用。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-149">The file store properties are for advanced use only.</span></span> <span data-ttu-id="f9dc6-150">其中包含進階記憶體管理設定。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-150">They include advanced memory management settings.</span></span>|  
|[<span data-ttu-id="f9dc6-151">鎖定管理員屬性</span><span class="sxs-lookup"><span data-stu-id="f9dc6-151">Lock Manager Properties</span></span>](lock-manager-properties.md)|<span data-ttu-id="f9dc6-152">鎖定管理員屬性定義與鎖定和逾時有關的伺服器行為。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-152">The lock manager properties define server behaviors pertaining to locking and timeouts.</span></span> <span data-ttu-id="f9dc6-153">這些屬性大部分僅供進階使用。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-153">Most of these properties are for advanced use only.</span></span>|  
|[<span data-ttu-id="f9dc6-154">記錄檔屬性</span><span class="sxs-lookup"><span data-stu-id="f9dc6-154">Log Properties</span></span>](log-properties.md)|<span data-ttu-id="f9dc6-155">記錄屬性控制在伺服器上是否記錄事件、記錄於何處以及如何記錄。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-155">The log properties controls if, where, and how events are logged on the server.</span></span> <span data-ttu-id="f9dc6-156">這包含錯誤記錄、例外狀況記錄、飛行記錄器、查詢記錄和追蹤。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-156">This includes error logging, exception logging, flight recorder, query logging, and traces.</span></span>|  
|[<span data-ttu-id="f9dc6-157">記憶體屬性</span><span class="sxs-lookup"><span data-stu-id="f9dc6-157">Memory Properties</span></span>](memory-properties.md)|<span data-ttu-id="f9dc6-158">記憶體屬性控制伺服器如何使用記憶體。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-158">The memory properties control how the server uses memory.</span></span> <span data-ttu-id="f9dc6-159">這些屬性主要是供進階使用。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-159">They are primarily for advanced use.</span></span>|  
|[<span data-ttu-id="f9dc6-160">網路屬性</span><span class="sxs-lookup"><span data-stu-id="f9dc6-160">Network Properties</span></span>](network-properties.md)|<span data-ttu-id="f9dc6-161">網路屬性控制與網路有關的伺服器行為，包含控制壓縮和二進位 XML 的屬性。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-161">The network properties control server behavior pertaining to networking, including properties that control compression and binary XML.</span></span> <span data-ttu-id="f9dc6-162">這些屬性大部分僅供進階使用。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-162">Most of these properties are for advanced use only.</span></span>|  
|[<span data-ttu-id="f9dc6-163">OLAP 屬性</span><span class="sxs-lookup"><span data-stu-id="f9dc6-163">OLAP Properties</span></span>](olap-properties.md)|<span data-ttu-id="f9dc6-164">OLAP 屬性控制 Cube 和維度處理、延遲處理、資料快取，以及查詢行為。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-164">The OLAP properties control cube and dimension processing, lazy processing, data caching, and query behavior.</span></span> <span data-ttu-id="f9dc6-165">這些包含基本和進階屬性。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-165">These include both basic and advanced properties.</span></span>|  
|[<span data-ttu-id="f9dc6-166">安全性屬性</span><span class="sxs-lookup"><span data-stu-id="f9dc6-166">Security Properties</span></span>](security-properties.md)|<span data-ttu-id="f9dc6-167">安全性區段包含定義存取權限的基本和進階屬性。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-167">The security section contains both basic and advanced properties that define access permissions.</span></span> <span data-ttu-id="f9dc6-168">這包含與管理員和使用者有關的設定。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-168">This includes settings pertaining to administrators and users.</span></span>|  
|[<span data-ttu-id="f9dc6-169">執行緒集區屬性</span><span class="sxs-lookup"><span data-stu-id="f9dc6-169">Thread Pool Properties</span></span>](thread-pool-properties.md)|<span data-ttu-id="f9dc6-170">執行緒集區屬性控制伺服器會建立多少執行緒。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-170">The thread pool properties control how many threads the server creates.</span></span> <span data-ttu-id="f9dc6-171">這些屬性主要是進階屬性。</span><span class="sxs-lookup"><span data-stu-id="f9dc6-171">These are primarily advanced properties.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9dc6-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9dc6-172">See Also</span></span>  
 <span data-ttu-id="f9dc6-173">[Analysis Services 實例管理](../instances/analysis-services-instance-management.md) </span><span class="sxs-lookup"><span data-stu-id="f9dc6-173">[Analysis Services Instance Management](../instances/analysis-services-instance-management.md) </span></span>  
 [<span data-ttu-id="f9dc6-174">指定方案部署的組態設定</span><span class="sxs-lookup"><span data-stu-id="f9dc6-174">Specifying Configuration Settings for Solution Deployment</span></span>](../multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
  
