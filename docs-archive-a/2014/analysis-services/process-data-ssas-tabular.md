---
title: " (SSAS 表格式) 處理資料 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d88f2dc9-2933-4be5-9bf3-48ffbc2d0a1a
author: minewiskan
ms.author: owend
ms.openlocfilehash: e2066cb6d871f43dda719cab3539253db97bfca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708718"
---
# <a name="process-data-ssas-tabular"></a><span data-ttu-id="3db3a-102">處理資料 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="3db3a-102">Process Data (SSAS Tabular)</span></span>
  <span data-ttu-id="3db3a-103">當您將資料匯入至快取模式的表格式模型時，您可以擷取該資料在匯入時的快照集。</span><span class="sxs-lookup"><span data-stu-id="3db3a-103">When you import data into a tabular model, in Cached mode, you are capturing a snapshot of that data at the time of import.</span></span> <span data-ttu-id="3db3a-104">在某些情況下，該資料可能永遠不會變更，因此不需要在模型中更新。</span><span class="sxs-lookup"><span data-stu-id="3db3a-104">In some cases, that data may never change and it does not need to be updated in the model.</span></span> <span data-ttu-id="3db3a-105">但是，您匯入的資料很有可能定期變更，因此為了讓模型可以反映資料來源的最新資料，您必須處理 (重新整理) 資料並重新計算導出資料。</span><span class="sxs-lookup"><span data-stu-id="3db3a-105">However, it is more likely that the data you are importing from changes regularly, and in order for your model to reflect the most recent data from the data sources, it is necessary to process (refresh) the data and re-calculate calculated data.</span></span> <span data-ttu-id="3db3a-106">若要更新模型中的資料，您可以在所有資料表上、在個別資料表上、透過資料分割或透過資料來源連接，來執行處理動作。</span><span class="sxs-lookup"><span data-stu-id="3db3a-106">To update the data in your model, you perform a process action on all tables, on an individual table, by a partition, or by a data source connection.</span></span>  
  
 <span data-ttu-id="3db3a-107">撰寫模型專案時，必須在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]手動起始處理動作。</span><span class="sxs-lookup"><span data-stu-id="3db3a-107">When authoring your model project, process actions must be initiated manually in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="3db3a-108">部署模型之後，即可使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 執行處理作業或使用指令碼排程處理作業。</span><span class="sxs-lookup"><span data-stu-id="3db3a-108">After a model has been deployed, process operations can be performed by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or scheduled by using a script.</span></span> <span data-ttu-id="3db3a-109">此處所述的工作都屬於您在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中製作模型期間可以執行的處理動作。</span><span class="sxs-lookup"><span data-stu-id="3db3a-109">Tasks described here all pertain to process actions that you can do during model authoring in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="3db3a-110">如需已部署模型之處理動作的詳細資訊，請參閱[處理資料庫、資料表或資料分割](tabular-models/process-database-table-or-partition-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3db3a-110">For more information about process actions for a deployed model, see [Process Database, Table, or Partition](tabular-models/process-database-table-or-partition-analysis-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="3db3a-111">相關工作</span><span class="sxs-lookup"><span data-stu-id="3db3a-111">Related Tasks</span></span>  
  
|<span data-ttu-id="3db3a-112">主題</span><span class="sxs-lookup"><span data-stu-id="3db3a-112">Topic</span></span>|<span data-ttu-id="3db3a-113">描述</span><span class="sxs-lookup"><span data-stu-id="3db3a-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3db3a-114">手動處理資料 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="3db3a-114">Manually Process Data &#40;SSAS Tabular&#41;</span></span>](manually-process-data-ssas-tabular.md)|<span data-ttu-id="3db3a-115">描述如何手動處理模型工作空間資料。</span><span class="sxs-lookup"><span data-stu-id="3db3a-115">Describes how to manually process model workspace data.</span></span>|  
|[<span data-ttu-id="3db3a-116">疑難排解處理資料 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="3db3a-116">Troubleshoot Process Data &#40;SSAS Tabular&#41;</span></span>](troubleshoot-process-data-ssas-tabular.md)|<span data-ttu-id="3db3a-117">描述如何疑難排解處理作業。</span><span class="sxs-lookup"><span data-stu-id="3db3a-117">Describes how to troubleshoot process operations.</span></span>|  
  
  
