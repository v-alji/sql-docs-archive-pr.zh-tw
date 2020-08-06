---
title: " (SSMS) 的 [資料分割屬性] 對話方塊 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionpropertiesdialog.f1
ms.assetid: dfb5b7a0-7543-4e5e-8a30-4b734606e157
author: minewiskan
ms.author: owend
ms.openlocfilehash: b606a39ef99e5313b526ab0210448e295c5f04cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686502"
---
# <a name="partition-properties-dialog-box-ssms"></a><span data-ttu-id="662f9-102">資料分割屬性對話方塊 (SSMS)</span><span class="sxs-lookup"><span data-stu-id="662f9-102">Partition Properties Dialog Box (SSMS)</span></span>
  <span data-ttu-id="662f9-103">使用 SQL Server Management Studio 中的 [資料分割屬性]\*\*\*\* 對話方塊，即可針對 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫中的 Cube 來設定資料分割的屬性。</span><span class="sxs-lookup"><span data-stu-id="662f9-103">Use the **Partition Properties** dialog box in SQL Server Management Studio to set the properties of a partition for a cube in an [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="662f9-104">若要開啟 [資料分割屬性]\*\*\*\* 對話方塊，請在物件總管\*\*\*\* 中以滑鼠右鍵按一下資料分割，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="662f9-104">To open the **Partition Properties** dialog box, in **Object Explorer**, right-click a partition, and then click **Properties**.</span></span>  
  
 <span data-ttu-id="662f9-105">[資料分割屬性]\*\*\*\* 對話方塊會包含下列頁面：</span><span class="sxs-lookup"><span data-stu-id="662f9-105">The **Partition Properties** dialog box contains the following pages:</span></span>  
  
## <a name="pages"></a><span data-ttu-id="662f9-106">頁面</span><span class="sxs-lookup"><span data-stu-id="662f9-106">Pages</span></span>  
  
|<span data-ttu-id="662f9-107">頁面</span><span class="sxs-lookup"><span data-stu-id="662f9-107">Page</span></span>|<span data-ttu-id="662f9-108">描述</span><span class="sxs-lookup"><span data-stu-id="662f9-108">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="662f9-109">**選取範圍**</span><span class="sxs-lookup"><span data-stu-id="662f9-109">**Selection**</span></span>|<span data-ttu-id="662f9-110">使用 [選取範圍]\*\*\*\* 頁面，即可選取量值群組中的資料分割，以顯示或修改其屬性。</span><span class="sxs-lookup"><span data-stu-id="662f9-110">Use the **Selection** page to select the partition in the measure group for which you want to display or modify properties.</span></span> <span data-ttu-id="662f9-111">如需此頁面的詳細資訊，請參閱[選取範圍 &#40;資料分割屬性對話方塊&#41; &#40;SSMS&#41;](selection-partition-properties-dialog-box-ssms.md)。</span><span class="sxs-lookup"><span data-stu-id="662f9-111">For more information about this page, see [Selection &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](selection-partition-properties-dialog-box-ssms.md).</span></span>|  
|<span data-ttu-id="662f9-112">**一般**</span><span class="sxs-lookup"><span data-stu-id="662f9-112">**General**</span></span>|<span data-ttu-id="662f9-113">使用 [一般]\*\*\*\* 頁面，即可顯示及修改 [選取範圍]\*\*\*\* 頁面中所選取之資料分割的一般屬性。</span><span class="sxs-lookup"><span data-stu-id="662f9-113">Use the **General** page to display and modify the general properties of the partition selected in the **Selection** page.</span></span> <span data-ttu-id="662f9-114">如需此頁面的詳細資訊，請參閱[一般 &#40;資料分割屬性對話方塊&#41; &#40;SSMS&#41;](general-partition-properties-dialog-box-ssms.md)。</span><span class="sxs-lookup"><span data-stu-id="662f9-114">For more information about this page, see [General &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](general-partition-properties-dialog-box-ssms.md).</span></span>|  
|<span data-ttu-id="662f9-115">**主動式快取**</span><span class="sxs-lookup"><span data-stu-id="662f9-115">**Proactive Caching**</span></span>|<span data-ttu-id="662f9-116">使用 [主動式快取]\*\*\*\* 頁面，即可顯示及修改 [選取範圍]\*\*\*\* 頁面中所選取之資料分割的儲存體與主動式快取設定。</span><span class="sxs-lookup"><span data-stu-id="662f9-116">Use the **Proactive Caching** page to display and modify the storage and proactive caching settings of the partition selected in the **Selection** page.</span></span> <span data-ttu-id="662f9-117">如需此頁面的詳細資訊，請參閱[主動式快取 &#40;資料分割屬性對話方塊&#41; &#40;SSMS&#41;](proactive-caching-partition-properties-dialog-box-ssms.md)。</span><span class="sxs-lookup"><span data-stu-id="662f9-117">For more information about this page, see [Proactive Caching &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](proactive-caching-partition-properties-dialog-box-ssms.md).</span></span>|  
|<span data-ttu-id="662f9-118">**錯誤組態**</span><span class="sxs-lookup"><span data-stu-id="662f9-118">**Error Configuration**</span></span>|<span data-ttu-id="662f9-119">使用 [錯誤組態]\*\*\*\* 頁面，即可顯示及修改用於處理 [選取範圍]\*\*\*\* 頁面中所選取資料分割的錯誤組態設定。</span><span class="sxs-lookup"><span data-stu-id="662f9-119">Use the **Error Configuration** page to display and modify the error configuration settings for processing the partition selected in the **Selection** page.</span></span> <span data-ttu-id="662f9-120">如需此頁面的詳細資訊，請參閱[設定 Cube、分割區和維度處理 &#40;SSAS - 多維度&#41; 時發生錯誤](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)。</span><span class="sxs-lookup"><span data-stu-id="662f9-120">For more information about this page, see [Error Configuration for Cube, Partition, and Dimension Processing &#40;SSAS - Multidimensional&#41;](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="662f9-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="662f9-121">See Also</span></span>  
 <span data-ttu-id="662f9-122">[分割區 &#40;Analysis Services 多維度資料&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="662f9-122">[Partitions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="662f9-123">[遠端資料分割](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md) </span><span class="sxs-lookup"><span data-stu-id="662f9-123">[Remote Partitions](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md) </span></span>  
 [<span data-ttu-id="662f9-124">Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="662f9-124">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
