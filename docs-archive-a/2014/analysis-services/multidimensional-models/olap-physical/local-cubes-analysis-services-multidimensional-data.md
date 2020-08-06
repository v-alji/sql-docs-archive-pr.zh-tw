---
title: 本機 Cube (Analysis Services 多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], local
ms.assetid: e52e1515-35a7-4dc3-9bbf-736d176ba0c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 75f02dd54992e9cc4f94d9845e0e25de5ed988f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598598"
---
# <a name="local-cubes-analysis-services---multidimensional-data"></a><span data-ttu-id="e6902-102">本機 Cube (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="e6902-102">Local Cubes (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="e6902-103">若要建立、更新或刪除本機 Cube，您必須撰寫及執行 ASSL 指令碼或 AMO 程式。</span><span class="sxs-lookup"><span data-stu-id="e6902-103">To create, update or delete local cubes, you must write and execute either an ASSL script or an AMO program.</span></span>  
  
 <span data-ttu-id="e6902-104">本機 Cube 和本機採礦模型可讓用戶端工作站與網路中斷連接時，仍能進行分析。</span><span class="sxs-lookup"><span data-stu-id="e6902-104">Local cubes and local mining models allow analysis on a client workstation while it is disconnected from the network.</span></span> <span data-ttu-id="e6902-105">例如，用戶端應用程式可能會呼叫 OLE DB for OLAP 9.0 Provider (MSOLAP.3)，以便載入本機 Cube 引擎來建立及查詢本機 Cube，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="e6902-105">For example, a client application might call the OLE DB for OLAP 9.0 Provider (MSOLAP.3), which loads the local cube engine to create and query local cubes, as shown in the following illustration:</span></span>  
  
 <span data-ttu-id="e6902-106">![本機 Cube 和模型的用戶端架構](../../../analysis-services/dev-guide/media/as-localcubearch9.gif "本機 Cube 和模型的用戶端架構")</span><span class="sxs-lookup"><span data-stu-id="e6902-106">![Client architecture for local cubes and models](../../../analysis-services/dev-guide/media/as-localcubearch9.gif "Client architecture for local cubes and models")</span></span>  
  
 <span data-ttu-id="e6902-107">與本機 Cube 進行互動時，ADMOD.NET 和分析管理物件 (AMO) 也會載入本機 Cube 引擎。</span><span class="sxs-lookup"><span data-stu-id="e6902-107">ADMOD.NET and Analysis Management Objects (AMO) also load the local cube engine when interacting with local cubes.</span></span> <span data-ttu-id="e6902-108">只有單一處理序可以存取本機 Cube 檔案，因為當本機 Cube 引擎建立本機 Cube 的連接時，它就會以獨佔方式鎖定本機 Cube 檔案。</span><span class="sxs-lookup"><span data-stu-id="e6902-108">Only a single process can access a local cube file, because the local cube engine exclusively locks a local cube file when it establishes a connection to the local cube.</span></span> <span data-ttu-id="e6902-109">透過處理序，最多允許五個同時連接。</span><span class="sxs-lookup"><span data-stu-id="e6902-109">With a process, up to five simultaneous connections are permitted.</span></span>  
  
 <span data-ttu-id="e6902-110">.cub 檔可能會包含一個以上的 Cube 或資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="e6902-110">A .cub file may contain more than one cube or data mining model.</span></span> <span data-ttu-id="e6902-111">本機 Cube 和資料採礦模型的查詢由本機 Cube 引擎處理，不需要連接到 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e6902-111">Queries to the local cubes and data mining models are handled by the local cube engine and do not require a connection to an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6902-112">目前不支援使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 來管理本機 Cube。</span><span class="sxs-lookup"><span data-stu-id="e6902-112">The use of [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] to manage local cubes is not supported.</span></span>  
  
## <a name="local-cubes"></a><span data-ttu-id="e6902-113">本機 Cube</span><span class="sxs-lookup"><span data-stu-id="e6902-113">Local Cubes</span></span>  
 <span data-ttu-id="e6902-114">本機 cube 可以從實例中的現有 cube [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 或關聯式資料來源建立及填入。</span><span class="sxs-lookup"><span data-stu-id="e6902-114">A local cube can be created and populated from either an existing cube in an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance or from a relational data source.</span></span>  
  
|<span data-ttu-id="e6902-115">本機 Cube 的資料來源</span><span class="sxs-lookup"><span data-stu-id="e6902-115">Source for data for local cube</span></span>|<span data-ttu-id="e6902-116">建立方法</span><span class="sxs-lookup"><span data-stu-id="e6902-116">Creation method</span></span>|  
|------------------------------------|---------------------|  
|<span data-ttu-id="e6902-117">以伺服器為基礎的 Cube</span><span class="sxs-lookup"><span data-stu-id="e6902-117">Server-based cube</span></span>|<span data-ttu-id="e6902-118">您可以使用 CREATE GLOBAL CUBE 語句或 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 指令碼語言 (ASSL) 腳本，從以伺服器為基礎的 cube 建立和填入 cube。</span><span class="sxs-lookup"><span data-stu-id="e6902-118">You can use either the CREATE GLOBAL CUBE statement or an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Scripting Language (ASSL) script to create and populate a cube from a server-based cube.</span></span> <span data-ttu-id="e6902-119">如需詳細資訊，請參閱[CREATE GLOBAL CUBE 語句 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube)或[Analysis Services 指令碼語言 &#40;ASSL&#41; 參考](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)。</span><span class="sxs-lookup"><span data-stu-id="e6902-119">For more information, see [CREATE GLOBAL CUBE Statement  &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube) or [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).</span></span>|  
|<span data-ttu-id="e6902-120">關聯式資料來源</span><span class="sxs-lookup"><span data-stu-id="e6902-120">Relational data source</span></span>|<span data-ttu-id="e6902-121">您可以使用 ASSL 指令碼，根據 OLE DB 關聯式資料庫建立和擴展 Cube。</span><span class="sxs-lookup"><span data-stu-id="e6902-121">You use an ASSL script to create and populate a cube from an OLE DB relational database.</span></span> <span data-ttu-id="e6902-122">若要使用 ASSL 來建立本機 Cube，您只要連接至本機 Cube 檔案 (\*.cub) 並以針對 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 執行個體執行 ASSL 指令碼來建立伺服器 Cube 的相同方式執行 ASSL 指令碼即可。</span><span class="sxs-lookup"><span data-stu-id="e6902-122">To create a local cube using ASSL, you simply connect to a local cube file (\*.cub) and execute the ASSL script in the same manner as executing an ASSL script against an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance to create a server cube.</span></span> <span data-ttu-id="e6902-123">如需詳細資訊，請參閱[Analysis Services 指令碼語言 &#40;ASSL&#41; 參考](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)。</span><span class="sxs-lookup"><span data-stu-id="e6902-123">For more information, see [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).</span></span>|  
  
 <span data-ttu-id="e6902-124">您可以使用 REFRESH CUBE 陳述式來重建本機 Cube 並更新其資料。</span><span class="sxs-lookup"><span data-stu-id="e6902-124">Use the REFRESH CUBE statement to rebuild a local cube and update its data.</span></span> <span data-ttu-id="e6902-125">如需詳細資訊，請參閱[&#40;MDX&#41;的 REFRESH CUBE 語句](/sql/mdx/mdx-data-definition-refresh-cube)。</span><span class="sxs-lookup"><span data-stu-id="e6902-125">For more information, see [REFRESH CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-refresh-cube).</span></span>  
  
### <a name="local-cubes-created-from-server-based-cubes"></a><span data-ttu-id="e6902-126">根據以伺服器為基礎的 Cube 建立本機 Cube</span><span class="sxs-lookup"><span data-stu-id="e6902-126">Local Cubes Created from Server-based Cubes</span></span>  
 <span data-ttu-id="e6902-127">根據以伺服器為基礎的 Cube 建立本機 Cube 時，請考量以下事項：</span><span class="sxs-lookup"><span data-stu-id="e6902-127">When creating local cubes created from server-based cubes, the following considerations apply:</span></span>  
  
-   <span data-ttu-id="e6902-128">不支援相異計數量值。</span><span class="sxs-lookup"><span data-stu-id="e6902-128">Distinct count measures are not supported.</span></span>  
  
-   <span data-ttu-id="e6902-129">當您加入量值時，至少必須同時加入一個與所加入之量值相關的維度。</span><span class="sxs-lookup"><span data-stu-id="e6902-129">When you add a measure, you must also include at least one dimension that is related to the measure being added.</span></span> <span data-ttu-id="e6902-130">如需維度關聯性到量值群組的詳細資訊，請參閱[維度關聯](../../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)性。</span><span class="sxs-lookup"><span data-stu-id="e6902-130">For more information about dimension relationships to measure groups, see [Dimension Relationships](../../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).</span></span>  
  
-   <span data-ttu-id="e6902-131">當您加入父子式階層時，就會忽略父子式階層上的層級和篩選，而加入整個父子式階層。</span><span class="sxs-lookup"><span data-stu-id="e6902-131">When you add a parent-child hierarchy, levels and filters on a parent-child hierarchy are ignored and the entire parent-child hierarchy is included.</span></span>  
  
-   <span data-ttu-id="e6902-132">不會建立成員屬性。</span><span class="sxs-lookup"><span data-stu-id="e6902-132">Member properties are not created.</span></span>  
  
-   <span data-ttu-id="e6902-133">當您加入局部加總量值時，「帳戶」或「時間」維度上不允許使用任何配量。</span><span class="sxs-lookup"><span data-stu-id="e6902-133">When you include a semi-additive measure, no slices are permitted on either the Account or the Time dimension.</span></span>  
  
-   <span data-ttu-id="e6902-134">參考維度一定會具體化。</span><span class="sxs-lookup"><span data-stu-id="e6902-134">Reference dimensions are always materialized.</span></span>  
  
-   <span data-ttu-id="e6902-135">包含多對多維度時，適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="e6902-135">When you include a many-to-many dimension, the following rules apply:</span></span>  
  
    -   <span data-ttu-id="e6902-136">您無法配量多對多維度。</span><span class="sxs-lookup"><span data-stu-id="e6902-136">You cannot slice the many-to-many dimension.</span></span>  
  
    -   <span data-ttu-id="e6902-137">您必須從中繼量值群組加入量值。</span><span class="sxs-lookup"><span data-stu-id="e6902-137">You must add a measure from the intermediary measure group.</span></span>  
  
    -   <span data-ttu-id="e6902-138">您無法配量多對多關聯性中所涉及之兩個量值群組所共用的任何維度。</span><span class="sxs-lookup"><span data-stu-id="e6902-138">You cannot slice any of the dimensions common to the two measure groups involved in the many-to-may relationship.</span></span>  
  
-   <span data-ttu-id="e6902-139">只有依賴加入至本機 Cube 之量值與維度的這些導出成員、命名集和指派會顯示在本機 Cube 中。</span><span class="sxs-lookup"><span data-stu-id="e6902-139">Only those calculated members, named sets, and assignments that rely upon measures and dimensions added to the local cube will appear in the local cube.</span></span> <span data-ttu-id="e6902-140">系統將自動排除無效的導出成員、命名集和指派。</span><span class="sxs-lookup"><span data-stu-id="e6902-140">Invalid calculated members, named sets, and assignments will be automatically excluded.</span></span>  
  
### <a name="security"></a><span data-ttu-id="e6902-141">安全性</span><span class="sxs-lookup"><span data-stu-id="e6902-141">Security</span></span>  
 <span data-ttu-id="e6902-142">為了讓使用者從伺服器 cube 建立本機 cube，使用者必須被授與伺服器 cube 的「**鑽取」和「本機 cube** 」許可權。</span><span class="sxs-lookup"><span data-stu-id="e6902-142">In order for a user to create a local cube from a server cube, the user must be granted **Drillthrough and Local Cube** permissions on the server cube.</span></span> <span data-ttu-id="e6902-143">如需詳細資訊，請參閱[Grant cube 或 model 許可權 &#40;Analysis Services&#41;](../../multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e6902-143">For more information, see [Grant cube or model permissions &#40;Analysis Services&#41;](../../multidimensional-models/grant-cube-or-model-permissions-analysis-services.md).</span></span>  
  
 <span data-ttu-id="e6902-144">使用伺服器 Cube 等角色時，本機 Cube 不會受到保護。</span><span class="sxs-lookup"><span data-stu-id="e6902-144">Local cubes are not secured using roles like server cubes.</span></span> <span data-ttu-id="e6902-145">擁有本機 Cube 檔案之檔案層級存取權的任何人都可以查詢其中的 Cube。</span><span class="sxs-lookup"><span data-stu-id="e6902-145">Anyone with file-level access to a local cube file can query cubes in it.</span></span> <span data-ttu-id="e6902-146">您可以使用本機 Cube 檔案的 `Encryption Password` 連接屬性來設定本機 Cube 檔案的密碼。</span><span class="sxs-lookup"><span data-stu-id="e6902-146">You can use the `Encryption Password` connection property on a local cube file to set a password on the local cube file.</span></span> <span data-ttu-id="e6902-147">如果設定本機 Cube 檔案的密碼，就會要求本機 Cube 檔案的所有未來連接都要使用此密碼，才能查詢檔案。</span><span class="sxs-lookup"><span data-stu-id="e6902-147">Setting a password on a local cube file requires all future connections to the local cube file to use this password in order to query the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6902-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6902-148">See Also</span></span>  
 <span data-ttu-id="e6902-149">[CREATE GLOBAL CUBE 語句 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube) </span><span class="sxs-lookup"><span data-stu-id="e6902-149">[CREATE GLOBAL CUBE Statement  &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube) </span></span>  
 <span data-ttu-id="e6902-150">[使用 Analysis Services 指令碼語言進行開發 &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span><span class="sxs-lookup"><span data-stu-id="e6902-150">[Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span></span>  
 [<span data-ttu-id="e6902-151">&#40;MDX&#41;的 REFRESH CUBE 語句</span><span class="sxs-lookup"><span data-stu-id="e6902-151">REFRESH CUBE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-refresh-cube)  
  
  
