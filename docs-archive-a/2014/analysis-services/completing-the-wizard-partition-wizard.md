---
title: 正在完成 Wizard (Partition Wizard) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.finish.f1
ms.assetid: 68a4dd5d-94d9-4a02-be31-949a6da0ef51
author: minewiskan
ms.author: owend
ms.openlocfilehash: d60be28170e8f8ec156d1c37149ddbc04b64bf8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593048"
---
# <a name="completing-the-wizard-partition-wizard"></a><span data-ttu-id="235b3-102">正在完成精靈 (資料分割精靈)</span><span class="sxs-lookup"><span data-stu-id="235b3-102">Completing the Wizard (Partition Wizard)</span></span>
  <span data-ttu-id="235b3-103">使用 [正在完成精靈]\*\*\*\* 頁面，即可命名資料分割、定義資料分割的彙總設計，以及在完成資料分割精靈之後選擇性地部署和處理資料分割。</span><span class="sxs-lookup"><span data-stu-id="235b3-103">Use the **Completing the Wizard** page to name the partition, define the aggregation design for your partition, and optionally deploy and process the partition after completing the Partition Wizard.</span></span>  
  
## <a name="options"></a><span data-ttu-id="235b3-104">選項。</span><span class="sxs-lookup"><span data-stu-id="235b3-104">Options</span></span>  
 <span data-ttu-id="235b3-105">**名稱**</span><span class="sxs-lookup"><span data-stu-id="235b3-105">**Name**</span></span>  
 <span data-ttu-id="235b3-106">輸入新資料分割的名稱。</span><span class="sxs-lookup"><span data-stu-id="235b3-106">Type the name for the new partition.</span></span> <span data-ttu-id="235b3-107">如果您使用多個資料表，請輸入要和資料表名稱結合的前置詞，以建立每個資料分割名稱。</span><span class="sxs-lookup"><span data-stu-id="235b3-107">If you are working with multiple tables, enter the prefix that will be combined with the table name to create each partition name.</span></span>  
  
 <span data-ttu-id="235b3-108">**彙總選項**</span><span class="sxs-lookup"><span data-stu-id="235b3-108">**Aggregation options**</span></span>  
 <span data-ttu-id="235b3-109">指定資料分割的彙總選項。</span><span class="sxs-lookup"><span data-stu-id="235b3-109">Specifies the aggregation option for the partition.</span></span>  
  
 <span data-ttu-id="235b3-110">下表列出可用的彙總選項。</span><span class="sxs-lookup"><span data-stu-id="235b3-110">The following table lists the aggregation options that are available.</span></span>  
  
|<span data-ttu-id="235b3-111">選項</span><span class="sxs-lookup"><span data-stu-id="235b3-111">Option</span></span>|<span data-ttu-id="235b3-112">描述</span><span class="sxs-lookup"><span data-stu-id="235b3-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="235b3-113">**立即設計資料分割的彙總**</span><span class="sxs-lookup"><span data-stu-id="235b3-113">**Design aggregations for the partition now**</span></span>|<span data-ttu-id="235b3-114">在資料分割精靈建立新的資料分割之後，請設計新資料分割的彙總。</span><span class="sxs-lookup"><span data-stu-id="235b3-114">Designs aggregations for the new partition after the Partition Wizard creates the new partition.</span></span> <span data-ttu-id="235b3-115">在資料分割精靈中按一下 [完成]\*\*\*\* 之後，請選取此選項來啟動彙總設計精靈。</span><span class="sxs-lookup"><span data-stu-id="235b3-115">Selecting this option starts the Aggregation Design Wizard after you click **Finish** in the Partition Wizard.</span></span> <span data-ttu-id="235b3-116">如需 [彙總設計精靈] 的詳細資訊，請參閱 [彙總設計精靈 F1 說明](aggregation-design-wizard-f1-help.md)。</span><span class="sxs-lookup"><span data-stu-id="235b3-116">For more information about the Aggregation Design Wizard, see [Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md).</span></span>|  
|<span data-ttu-id="235b3-117">**稍後再設計彙總**</span><span class="sxs-lookup"><span data-stu-id="235b3-117">**Design the aggregations later**</span></span>|<span data-ttu-id="235b3-118">建立資料分割，且不在此時設計彙總。</span><span class="sxs-lookup"><span data-stu-id="235b3-118">Creates the partition without designing aggregations at this time.</span></span>|  
|<span data-ttu-id="235b3-119">**從現有的資料分割複製彙總設計**</span><span class="sxs-lookup"><span data-stu-id="235b3-119">**Copy the aggregation design from an existing partition**</span></span>|<span data-ttu-id="235b3-120">從量值群組的現有資料分割中，將彙總設計複製到新的資料分割。</span><span class="sxs-lookup"><span data-stu-id="235b3-120">Copies the aggregation design from an existing partition in the measure group to the new partition.</span></span> <span data-ttu-id="235b3-121">按一下此選項，讓 [複製來源]\*\*\*\* 選項可以使用。</span><span class="sxs-lookup"><span data-stu-id="235b3-121">Clicking this option makes the **Copy from** option available.</span></span> <span data-ttu-id="235b3-122">使用 [複製來源]\*\*\*\* 選項，即可選取要複製彙總設計的資料分割。</span><span class="sxs-lookup"><span data-stu-id="235b3-122">Use the **Copy from** option to select the partition from which to copy the aggregation design.</span></span><br /><br /> <span data-ttu-id="235b3-123">請注意，未來可能會合並的資料分割必須具有相同的資料表結構和匯總設計。</span><span class="sxs-lookup"><span data-stu-id="235b3-123">Note that partitions that may be merged in the future must have the same table structure and aggregation design.</span></span> <span data-ttu-id="235b3-124">如果您可能在量值群組中將新的資料分割與現有的資料分割進行合併，則應將現有之資料分割的彙總設計複製到新的資料分割中。</span><span class="sxs-lookup"><span data-stu-id="235b3-124">If you might merge the new partition with an existing partition in the measure group, you should copy the aggregation design of the existing partition into the new partition.</span></span>|  
  
 <span data-ttu-id="235b3-125">**立即部署及處理**</span><span class="sxs-lookup"><span data-stu-id="235b3-125">**Deploy and Process Now**</span></span>  
 <span data-ttu-id="235b3-126">針對 [處理與儲存位置]\*\*\*\* 頁面上指定的 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體，部署及處理資料分割。</span><span class="sxs-lookup"><span data-stu-id="235b3-126">Deploys and processes the partition to the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance specified on the **Processing and Storage Locations** page.</span></span> <span data-ttu-id="235b3-127">在此頁面上按一下 [完成]\*\*\*\* 之後，精靈就會部署及處理資料分割。</span><span class="sxs-lookup"><span data-stu-id="235b3-127">The wizard deploys and processes the partition after you click **Finish** on this page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="235b3-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="235b3-128">See Also</span></span>  
 [<span data-ttu-id="235b3-129">資料分割 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="235b3-129">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
