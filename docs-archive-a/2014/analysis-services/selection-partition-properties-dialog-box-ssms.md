---
title: '[選取 (資料分割屬性] 對話方塊)  (SSMS) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.partitionproperties.selection.f1
ms.assetid: 29a7b556-2484-4f66-b74c-1c061b3ce25c
author: minewiskan
ms.author: owend
ms.openlocfilehash: c88ebf6beb5e548fc91155bad6ca6d818ce99463
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592890"
---
# <a name="selection-partition-properties-dialog-box-ssms"></a><span data-ttu-id="c8ba6-102">選取範圍 (資料分割屬性對話方塊) (SSMS)</span><span class="sxs-lookup"><span data-stu-id="c8ba6-102">Selection (Partition Properties Dialog Box) (SSMS)</span></span>
  <span data-ttu-id="c8ba6-103">在 SQL Server Management Studio 中，使用 **[資料分割屬性]** 對話方塊的 **[選取範圍]** 頁面，即可從量值群組中選取資料分割，然後在 **[一般]**、 **[主動式快取]** 或 **[錯誤組態]** 窗格中檢視或修改屬性。</span><span class="sxs-lookup"><span data-stu-id="c8ba6-103">Use the **Selection** page of the **Partition Properties** dialog box in SQL Server Management Studio to select a partition from a measure group for which to view or modify properties in the **General**, **Proactive Caching**, or **Error Configuration** pane.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c8ba6-104">選項</span><span class="sxs-lookup"><span data-stu-id="c8ba6-104">Options</span></span>  
 <span data-ttu-id="c8ba6-105">**Grid**</span><span class="sxs-lookup"><span data-stu-id="c8ba6-105">**Grid**</span></span>  
 <span data-ttu-id="c8ba6-106">顯示包含所選取資料分割之量值群組的資料分割。</span><span class="sxs-lookup"><span data-stu-id="c8ba6-106">Displays the partitions of the measure group that contain the selected partition.</span></span>  
  
 <span data-ttu-id="c8ba6-107">選取要在 **[一般]**、 **[主動式快取]** 或 **[錯誤組態]** 頁面中檢視其屬性的資料分割。</span><span class="sxs-lookup"><span data-stu-id="c8ba6-107">Select the partition for which to view the properties in the **General**, **Proactive Caching**, or **Error Configuration** page.</span></span>  
  
 <span data-ttu-id="c8ba6-108">方格包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="c8ba6-108">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="c8ba6-109">資料行</span><span class="sxs-lookup"><span data-stu-id="c8ba6-109">Column</span></span>|<span data-ttu-id="c8ba6-110">描述</span><span class="sxs-lookup"><span data-stu-id="c8ba6-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c8ba6-111">**名稱**</span><span class="sxs-lookup"><span data-stu-id="c8ba6-111">**Name**</span></span>|<span data-ttu-id="c8ba6-112">顯示分割區的名稱。</span><span class="sxs-lookup"><span data-stu-id="c8ba6-112">Displays the name of the partition.</span></span>|  
|<span data-ttu-id="c8ba6-113">**Source**</span><span class="sxs-lookup"><span data-stu-id="c8ba6-113">**Source**</span></span>|<span data-ttu-id="c8ba6-114">顯示用來提供資料分割之來源資料的資料表或查詢。</span><span class="sxs-lookup"><span data-stu-id="c8ba6-114">Displays the table or query used to provide source data for the partition.</span></span>|  
|<span data-ttu-id="c8ba6-115">**彙總**</span><span class="sxs-lookup"><span data-stu-id="c8ba6-115">**Aggregations**</span></span>|<span data-ttu-id="c8ba6-116">顯示描述資料分割所使用之彙總設計的字串。</span><span class="sxs-lookup"><span data-stu-id="c8ba6-116">Displays a string describing the aggregation design used by the partition.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8ba6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8ba6-117">See Also</span></span>  
 <span data-ttu-id="c8ba6-118">[&#40;SSMS&#41;的 [資料分割屬性] 對話方塊](partition-properties-dialog-box-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="c8ba6-118">[Partition Properties Dialog Box &#40;SSMS&#41;](partition-properties-dialog-box-ssms.md) </span></span>  
 <span data-ttu-id="c8ba6-119">[[一般 &#40;資料分割屬性] 對話方塊&#41; &#40;SSMS&#41;](general-partition-properties-dialog-box-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="c8ba6-119">[General &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](general-partition-properties-dialog-box-ssms.md) </span></span>  
 <span data-ttu-id="c8ba6-120">[主動式快取 &#40;資料分割屬性] 對話方塊&#41; &#40;SSMS&#41;](proactive-caching-partition-properties-dialog-box-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="c8ba6-120">[Proactive Caching &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](proactive-caching-partition-properties-dialog-box-ssms.md) </span></span>  
 [<span data-ttu-id="c8ba6-121">&#40;SSAS 的 Cube、資料分割和維度處理的錯誤設定&#41;</span><span class="sxs-lookup"><span data-stu-id="c8ba6-121">Error Configuration for Cube, Partition, and Dimension Processing &#40;SSAS - Multidimensional&#41;</span></span>](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)  
  
  
