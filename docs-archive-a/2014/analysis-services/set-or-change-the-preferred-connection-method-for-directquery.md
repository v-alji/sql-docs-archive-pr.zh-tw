---
title: 設定或變更 DirectQuery 的慣用連接方法 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f10d5678-d678-4251-8cce-4e30cfe15751
author: minewiskan
ms.author: owend
ms.openlocfilehash: 239c80ace0daa3498c8dafd8fea358ce540931d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705513"
---
# <a name="set-or-change-the-preferred-connection-method-for-directquery"></a><span data-ttu-id="ee912-102">設定或變更 DirectQuery 的慣用連接方法</span><span class="sxs-lookup"><span data-stu-id="ee912-102">Set or Change the Preferred Connection Method for DirectQuery</span></span>
  <span data-ttu-id="ee912-103">當您建立要用於 DirectQuery 模式的模型時，必須先將設計環境設定為支援使用 DirectQuery。</span><span class="sxs-lookup"><span data-stu-id="ee912-103">When you create a model for use in DirectQuery mode, you must first configure the design environment to support use of DirectQuery.</span></span> <span data-ttu-id="ee912-104">若要這樣做，請參閱[啟用 DirectQuery 設計模式 &#40;SSAS 表格式&#41;](tabular-models/enable-directquery-mode-in-ssdt.md)。</span><span class="sxs-lookup"><span data-stu-id="ee912-104">To do this, see [Enable DirectQuery Design Mode &#40;SSAS Tabular&#41;](tabular-models/enable-directquery-mode-in-ssdt.md).</span></span>  
  
 <span data-ttu-id="ee912-105">在您準備部署模型時，必須設定其他屬性，讓使用者能夠以其中一種 DirectQuery 模式來存取您的模型：</span><span class="sxs-lookup"><span data-stu-id="ee912-105">When you are ready to deploy the model, you must set some additional properties to enable users to access your model using one of the DirectQuery modes:</span></span>  
  
-   <span data-ttu-id="ee912-106">您必須指示對模型的查詢應該使用快取資料還是關聯式資料來源。</span><span class="sxs-lookup"><span data-stu-id="ee912-106">You must indicate whether queries against the model should use cached data or the relational data source.</span></span> <span data-ttu-id="ee912-107">您可以使用混合模式或僅限 DirectQuery 模式。</span><span class="sxs-lookup"><span data-stu-id="ee912-107">You can use a hybrid mode or DirectQuery only.</span></span>  
  
-   <span data-ttu-id="ee912-108">如果您使用資料分割，則必須指定哪個資料分割要做為 DirectQuery 資料來源。</span><span class="sxs-lookup"><span data-stu-id="ee912-108">If you are using partitions, you must indicate which partition to use as the DirectQuery data source.</span></span>  
  
-   <span data-ttu-id="ee912-109">您必須為將存取 SQL Server 資料來源的使用者設定模擬選項。</span><span class="sxs-lookup"><span data-stu-id="ee912-109">You must set impersonation options for users who will be accessing the SQL Server data source.</span></span>  
  
 <span data-ttu-id="ee912-110">此程序描述如何在設計工具中為 DirectQuery 模型設定慣用連接方法。</span><span class="sxs-lookup"><span data-stu-id="ee912-110">This procedure describes how to set the preferred connection method for a DirectQuery model in the designer.</span></span> <span data-ttu-id="ee912-111">此外也描述如何在部署模型後於 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 變更此屬性。</span><span class="sxs-lookup"><span data-stu-id="ee912-111">It also describes how you can change this property in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] after the model has been deployed.</span></span>  
  
### <a name="to-set-the-preferred-connection-method-for-a-directquery-model"></a><span data-ttu-id="ee912-112">若要為 DirectQuery 模型設定慣用連接方法</span><span class="sxs-lookup"><span data-stu-id="ee912-112">To set the preferred connection method for a DirectQuery model</span></span>  
  
1.  <span data-ttu-id="ee912-113">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟 DirectQuery 模型的方案檔。</span><span class="sxs-lookup"><span data-stu-id="ee912-113">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution file for the DirectQuery model.</span></span>  
  
2.  <span data-ttu-id="ee912-114">在 Visual Studio 中，選取 **[專案]** 功能表中的 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="ee912-114">In Visual Studio, from the **Project** menu, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="ee912-115">在 **[屬性]** 窗格中，將屬性 **DirectQueryMode**變更為支援 DirectQuery 使用的下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="ee912-115">In the **Properties** pane, change the property, **DirectQueryMode**, to one of the values that support DirectQuery usage:</span></span>  
  
    -   <span data-ttu-id="ee912-116">**InMemoryWithDirectQuery**：如果您使用此選項，則會部署模型，但是您必須先處理快取，然後才能對模型執行查詢。</span><span class="sxs-lookup"><span data-stu-id="ee912-116">**InMemory with DirectQuery**: If you use this option, the model is deployed but you must process the cache before you can run queries against the model.</span></span>  
  
    -   <span data-ttu-id="ee912-117">**DirectQueryWithInMemory**：如果您使用此選項，則快取在已處理時可供用戶端使用。</span><span class="sxs-lookup"><span data-stu-id="ee912-117">**DirectQuery with InMemory**: If you use this option, the cache will be available for use by clients if it has already been processed.</span></span> <span data-ttu-id="ee912-118">如果以此設定來部署模型但未處理快取，則某些用戶端在嘗試連接至模型時勢必會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="ee912-118">If you deploy the model with this setting and do not process the cache, some clients must get an error on trying to connect to the model.</span></span>  
  
    -   <span data-ttu-id="ee912-119">**DirectQueryOnly**：如果您使用此選項，則會部署中繼資料，但模型中沒有任何資料。</span><span class="sxs-lookup"><span data-stu-id="ee912-119">**DirectQuery only**: If you use this option, the metadata is deployed but the model has no data in it.</span></span> <span data-ttu-id="ee912-120">嘗試使用記憶體中模式進行連接的用戶端將會收到錯誤訊息，指出模型不存在或尚未處理。</span><span class="sxs-lookup"><span data-stu-id="ee912-120">Clients that attempt to connect using In-Memory mode will get an error, indicating that the model does not exist or has not been processed.</span></span>  
  
4.  <span data-ttu-id="ee912-121">如果發生錯誤，請在 Visual Studio 中開啟 **[錯誤清單]** ，並且解決阻礙模型以 DirectQuery 模式部署的任何問題。</span><span class="sxs-lookup"><span data-stu-id="ee912-121">If there are errors, in Visual Studio, open the **Error List** and resolve any problems that would prevent the model from being deployed in DirectQuery mode.</span></span>  
  
### <a name="to-verify-or-change-the-preferred-connection-method-for-a-directquery-model"></a><span data-ttu-id="ee912-122">若要為 DirectQuery 模型驗證或變更慣用連接方法</span><span class="sxs-lookup"><span data-stu-id="ee912-122">To verify or change the preferred connection method for a DirectQuery model</span></span>  
  
1.  <span data-ttu-id="ee912-123">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中，連接至部署了 DirectQuery 模型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ee912-123">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connect to the instance where you deployed the DirectQuery model.</span></span>  
  
2.  <span data-ttu-id="ee912-124">以滑鼠右鍵按一下模型資料庫，然後選取 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="ee912-124">Right-click the model database, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="ee912-125">在 **[屬性]** 窗格中，將屬性 **DirectQueryMode**變更為下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="ee912-125">In the **Properties** pane, change the property, **DirectQueryMode**, to one of these values:</span></span>  
  
    -   <span data-ttu-id="ee912-126">**僅限 DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="ee912-126">**DirectQuery Only**</span></span>  
  
    -   <span data-ttu-id="ee912-127">**InMemoryWithDirectQuery**</span><span class="sxs-lookup"><span data-stu-id="ee912-127">**InMemory with DirectQuery**</span></span>  
  
    -   <span data-ttu-id="ee912-128">**具有 InMemory 的 DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="ee912-128">**DirectQuery with InMemory**</span></span>  
  
 <span data-ttu-id="ee912-129">請注意，這些屬性與您在部署前於 Visual Studio 對專案設定的屬性相同。</span><span class="sxs-lookup"><span data-stu-id="ee912-129">Note that these properties are the same as the properties that you set on the project before deployment in Visual Studio.</span></span> <span data-ttu-id="ee912-130">只要您已將模型設定為支援使用 DirectQuery，隨時可以變更 DirectQuery 模式的慣用連接模式。</span><span class="sxs-lookup"><span data-stu-id="ee912-130">You can change the preferred connection mode for DirectQuery mode at any time, provided that you have configured the model to support DirectQuery usage.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee912-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee912-131">See Also</span></span>  
 <span data-ttu-id="ee912-132">[&#40;SSAS 表格式&#41;的 DirectQuery 模式](tabular-models/directquery-mode-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="ee912-132">[DirectQuery Mode &#40;SSAS Tabular&#41;](tabular-models/directquery-mode-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="ee912-133">&#40;SSAS 表格式&#41;啟用 DirectQuery 設計模式</span><span class="sxs-lookup"><span data-stu-id="ee912-133">Enable DirectQuery Design Mode &#40;SSAS Tabular&#41;</span></span>](tabular-models/enable-directquery-mode-in-ssdt.md)  
  
  
