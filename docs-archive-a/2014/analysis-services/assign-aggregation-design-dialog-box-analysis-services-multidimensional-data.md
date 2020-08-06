---
title: 指派匯總設計對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.copyaggregationdesign.f1
ms.assetid: 50c26cb1-c294-4f17-8b9e-435fdbd4806d
author: minewiskan
ms.author: owend
ms.openlocfilehash: dfc4f7a0847373360a79ddda366ad7aa3f02c5de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593220"
---
# <a name="assign-aggregation-design-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="0ead6-102">指派彙總設計對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="0ead6-102">Assign Aggregation Design Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="0ead6-103">使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的 [指派彙總設計]\*\*\*\* 對話方塊，即可將彙總設計指派給一個或多個目的地資料分割。</span><span class="sxs-lookup"><span data-stu-id="0ead6-103">Use the **Assign Aggregation Design** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to assign aggregation designs to one or more destination partitions.</span></span> <span data-ttu-id="0ead6-104">您可以在**物件總管**中以滑鼠右鍵按一下資料分割或彙總設計，然後選取 [指派彙總設計]\*\*\*\*，藉以顯示 [指派彙總設計]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0ead6-104">You can display the **Assign Aggregation Design** dialog box by right-clicking a partition or aggregation design in **Object Explorer** and selecting **Assign Aggregation Design**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0ead6-105">選項</span><span class="sxs-lookup"><span data-stu-id="0ead6-105">Options</span></span>  
  
|<span data-ttu-id="0ead6-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="0ead6-106">Term</span></span>|<span data-ttu-id="0ead6-107">定義</span><span class="sxs-lookup"><span data-stu-id="0ead6-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="0ead6-108">**彙總設計**</span><span class="sxs-lookup"><span data-stu-id="0ead6-108">**Aggregation designs**</span></span>|<span data-ttu-id="0ead6-109">選取要指派給一個或多個目的地資料分割的彙總設計。</span><span class="sxs-lookup"><span data-stu-id="0ead6-109">Select an aggregation design to assign to one or more destination partitions.</span></span>|  
|<span data-ttu-id="0ead6-110">**目的地資料分割**</span><span class="sxs-lookup"><span data-stu-id="0ead6-110">**Destination partitions**</span></span>|<span data-ttu-id="0ead6-111">選取要指派彙總設計的目的地資料分割。</span><span class="sxs-lookup"><span data-stu-id="0ead6-111">Select the partitions to which to assign the aggregation design.</span></span> <span data-ttu-id="0ead6-112">下列方格用來指定目的地資料分割：</span><span class="sxs-lookup"><span data-stu-id="0ead6-112">The following grid is used to specify destination partitions:</span></span><br /><br /> <span data-ttu-id="0ead6-113">\<check box>：選取或清除資料行標頭中的核取方塊，以包含或排除所有列出的資料分割作為目的地資料分割。</span><span class="sxs-lookup"><span data-stu-id="0ead6-113">\<check box>: Select or clear the check box in the column header to include or exclude all listed partitions as destination partitions.</span></span> <span data-ttu-id="0ead6-114">選取或清除資料分割旁的核取方塊，即可包含或排除該資料分割當做目的地資料分割。</span><span class="sxs-lookup"><span data-stu-id="0ead6-114">Select or clear a check box next to a partition to include or exclude that partition as a destination partition.</span></span><br /><br /> <span data-ttu-id="0ead6-115">**分割**區：顯示資料分割的名稱。</span><span class="sxs-lookup"><span data-stu-id="0ead6-115">**Partition**: Displays the name of the partition.</span></span><br /><br /> <span data-ttu-id="0ead6-116">**來源**：顯示資料分割的來源資料表或查詢。</span><span class="sxs-lookup"><span data-stu-id="0ead6-116">**Source**: Displays the source table or query for the partition.</span></span><br /><br /> <span data-ttu-id="0ead6-117">**匯總設計**：顯示資料分割之現有匯總設計的名稱。</span><span class="sxs-lookup"><span data-stu-id="0ead6-117">**Aggregation Design**: Displays the name of the existing aggregation design for the partition.</span></span>|  
|<span data-ttu-id="0ead6-118">**隱藏具有彙總設計的資料分割**</span><span class="sxs-lookup"><span data-stu-id="0ead6-118">**Hide partitions with aggregation designs**</span></span>|<span data-ttu-id="0ead6-119">選取此選項，即可單獨顯示沒有被指派彙總設計的資料分割。</span><span class="sxs-lookup"><span data-stu-id="0ead6-119">Select to show only the partitions that do not have aggregation designs assigned to them.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ead6-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ead6-120">See Also</span></span>  
 [<span data-ttu-id="0ead6-121">彙總和彙總設計</span><span class="sxs-lookup"><span data-stu-id="0ead6-121">Aggregations and Aggregation Designs</span></span>](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
