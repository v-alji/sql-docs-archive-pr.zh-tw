---
title: 合併資料分割對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.mergepartition.f1
ms.assetid: 1c94e250-ee18-4f98-b112-985f6346102a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1978c187bfb5097d286f78650b5bda6645c7a054
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599242"
---
# <a name="merge-partition-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="b7798-102">合併資料分割對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="b7798-102">Merge Partition Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="b7798-103">在 **SQL Server Management Studio** 中，使用 **[合併資料分割]** 對話方塊，即可為 Cube 中的量值群組合併資料分割。</span><span class="sxs-lookup"><span data-stu-id="b7798-103">Use the **Merge Partition** dialog box in **SQL Server Management Studio** to merge partitions for a measure group in a cube.</span></span> <span data-ttu-id="b7798-104">在物件總管\*\*\*\* 中，以滑鼠右鍵按一下 [資料分割] 資料夾或資料分割，然後從操作功能表選取 [合併資料分割]\*\*\*\*，即可顯示 [合併資料分割]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b7798-104">You can display the **Merge Partition** dialog box by right-clicking the Partitions folder or a partition in **Object Explorer** and selecting **Merge Partitions** from the context menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b7798-105">選項</span><span class="sxs-lookup"><span data-stu-id="b7798-105">Options</span></span>  
 <span data-ttu-id="b7798-106">**Server**</span><span class="sxs-lookup"><span data-stu-id="b7798-106">**Server**</span></span>  
 <span data-ttu-id="b7798-107">選取包含目標資料分割之 Analysis Services 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="b7798-107">Select the name of the Analysis Services instance that contains the target partition.</span></span>  
  
 <span data-ttu-id="b7798-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b7798-108">**Name**</span></span>  
 <span data-ttu-id="b7798-109">選取現有資料分割的名稱作為目標資料分割。</span><span class="sxs-lookup"><span data-stu-id="b7798-109">Select the name of an existing partition to use as the target partition.</span></span>  
  
 <span data-ttu-id="b7798-110">**資料夾**</span><span class="sxs-lookup"><span data-stu-id="b7798-110">**Folder**</span></span>  
 <span data-ttu-id="b7798-111">如果 [名稱] 中選取的資料分割不使用 Analysis Services 執行個體的預設資料夾，則會顯示包含目標資料分割的資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="b7798-111">Displays the name of the folder that contains the target partition, if the partition selected in Name does not use the default folder for the Analysis Services instance.</span></span>  
  
 <span data-ttu-id="b7798-112">**來源資料分割**</span><span class="sxs-lookup"><span data-stu-id="b7798-112">**Source Partitions**</span></span>  
 <span data-ttu-id="b7798-113">顯示方格，其中包含可以合併至目標資料分割的來源資料分割。</span><span class="sxs-lookup"><span data-stu-id="b7798-113">Displays a grind containing the source partitions that can be merged into the target partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b7798-114">只有在相同量值群組中共用相同彙總設計的資料分割可以進行合併。</span><span class="sxs-lookup"><span data-stu-id="b7798-114">Only partitions in the same measure group that share the same aggregation design can be merged.</span></span>  
  
 <span data-ttu-id="b7798-115">方格包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="b7798-115">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="b7798-116">資料行</span><span class="sxs-lookup"><span data-stu-id="b7798-116">Column</span></span>|<span data-ttu-id="b7798-117">描述</span><span class="sxs-lookup"><span data-stu-id="b7798-117">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b7798-118">**合併式**</span><span class="sxs-lookup"><span data-stu-id="b7798-118">**Merge**</span></span>|<span data-ttu-id="b7798-119">選取即可將來源資料分割合併至目標資料分割。</span><span class="sxs-lookup"><span data-stu-id="b7798-119">Select to merge the source partition into the target partition.</span></span>|  
|<span data-ttu-id="b7798-120">**分割區名稱**</span><span class="sxs-lookup"><span data-stu-id="b7798-120">**Partition Name**</span></span>|<span data-ttu-id="b7798-121">顯示來源資料分割的名稱。</span><span class="sxs-lookup"><span data-stu-id="b7798-121">Displays the name of the source partition.</span></span>|  
|<span data-ttu-id="b7798-122">**上次處理**</span><span class="sxs-lookup"><span data-stu-id="b7798-122">**Last Processed**</span></span>|<span data-ttu-id="b7798-123">顯示上次處理來源資料分割的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="b7798-123">Displays the date and time at which the source partition was last processed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7798-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7798-124">See Also</span></span>  
 <span data-ttu-id="b7798-125">[分割區 &#40;Analysis Services 多維度資料&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="b7798-125">[Partitions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="b7798-126">在 Analysis Services 中合併分割區 &#40;SSAS - 多維度&#41;</span><span class="sxs-lookup"><span data-stu-id="b7798-126">Merge Partitions in Analysis Services &#40;SSAS - Multidimensional&#41;</span></span>](multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)  
  
  
