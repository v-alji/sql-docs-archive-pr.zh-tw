---
title: 設計匯總 (Analysis Services-多維度) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- aggregations [Analysis Services], partitions
- partitions [Analysis Services], aggregations
ms.assetid: 3072b7e0-6961-42ad-a287-16f391f2cec4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 18d8ea1adb645868a11b70966ba3be2ed1764fbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606452"
---
# <a name="designing-aggregations-analysis-services---multidimensional"></a><span data-ttu-id="c093d-102">設計彙總 (Analysis Services - 多維度)</span><span class="sxs-lookup"><span data-stu-id="c093d-102">Designing Aggregations (Analysis Services - Multidimensional)</span></span>
  <span data-ttu-id="c093d-103">彙總是 Cube 資料的預先計算摘要，可幫助啟用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 以提供快速查詢回應。</span><span class="sxs-lookup"><span data-stu-id="c093d-103">Aggregations are precalculated summaries of cube data that help enable [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to provide rapid query responses.</span></span>  
  
 <span data-ttu-id="c093d-104">若要設定分割區的儲存選項和設計彙總，請使用彙總設計精靈。</span><span class="sxs-lookup"><span data-stu-id="c093d-104">To set storage options and design aggregations for a partition, use the Aggregation Design Wizard.</span></span> <span data-ttu-id="c093d-105">此精靈一次操作一個量值群組的單一分割區，因此您可以為每一個分割區選取不同的選項和設計。</span><span class="sxs-lookup"><span data-stu-id="c093d-105">The wizard operates on a single partition of a measure group at a time so that you can select different options and designs for each partition.</span></span> <span data-ttu-id="c093d-106">此精靈會逐步引導您設定分割區的儲存和設計彙總。</span><span class="sxs-lookup"><span data-stu-id="c093d-106">The wizard takes you through steps to configure storage and design aggregation for a partition.</span></span> <span data-ttu-id="c093d-107">如需設定儲存的詳細資訊，請參閱。</span><span class="sxs-lookup"><span data-stu-id="c093d-107">For more information about configuring storage, see.</span></span>  
  
 <span data-ttu-id="c093d-108">選取方法來控制精靈要設計的彙總數目，然後讓精靈設計彙總。</span><span class="sxs-lookup"><span data-stu-id="c093d-108">Select a method for controlling the number of aggregations the wizard will design, and then let the wizard design the aggregations.</span></span>  
  
 <span data-ttu-id="c093d-109">其目標是要設定最佳的彙總數目。</span><span class="sxs-lookup"><span data-stu-id="c093d-109">The goal is to design the optimal number of aggregations.</span></span> <span data-ttu-id="c093d-110">此數目不只要最佳化回應時間，還要防止分割區的大小過大。</span><span class="sxs-lookup"><span data-stu-id="c093d-110">This number should not only provide satisfactory response time, but also prevent excessive partition size.</span></span> <span data-ttu-id="c093d-111">彙總數目越大產生的回應時間越快，但也需要更多的儲存空間，而且可能要花更久的時間來計算。</span><span class="sxs-lookup"><span data-stu-id="c093d-111">A greater number of aggregations produces faster response times but it also requires more storage space and may take longer to compute.</span></span> <span data-ttu-id="c093d-112">不僅如此，當精靈設計越來越多的彙總時，較早的彙總會比較晚的彙總產生更大的效能改善。</span><span class="sxs-lookup"><span data-stu-id="c093d-112">Moreover, as the wizard designs more and more aggregations, earlier aggregations produce considerably larger performance gains than later aggregations.</span></span> <span data-ttu-id="c093d-113">減少較沒有用的彙總也可增加效能。</span><span class="sxs-lookup"><span data-stu-id="c093d-113">Reduction in less useful aggregations increases performance as well.</span></span> <span data-ttu-id="c093d-114">您可以藉由精靈中可用的下列其中一個方法，來控制精靈設計的彙總數目：</span><span class="sxs-lookup"><span data-stu-id="c093d-114">You can control the number of aggregations the wizard designs by one of the following methods available in the wizard:</span></span>  
  
-   <span data-ttu-id="c093d-115">指定彙總的儲存空間限制。</span><span class="sxs-lookup"><span data-stu-id="c093d-115">Specify a storage space limit for the aggregations.</span></span>  
  
-   <span data-ttu-id="c093d-116">指定效能改善限制。</span><span class="sxs-lookup"><span data-stu-id="c093d-116">Specify a performance gain limit.</span></span>  
  
-   <span data-ttu-id="c093d-117">當顯示的效能對大小曲線開始拉平且是在可接受的效能改善範圍內，請手動停止精靈。</span><span class="sxs-lookup"><span data-stu-id="c093d-117">Stop the wizard manually when the displayed performance versus size curve starts to level off at an acceptable performance gain.</span></span>  
  
-   <span data-ttu-id="c093d-118">選擇不要設計彙總。</span><span class="sxs-lookup"><span data-stu-id="c093d-118">Choose not to design aggregations.</span></span>  
  
 <span data-ttu-id="c093d-119">若要設計儲存，精靈必須能夠連接到目標伺服器上的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c093d-119">To design storage, the wizard must be able to connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] on the target server.</span></span> <span data-ttu-id="c093d-120">如果 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 未執行於目標伺服器上，或儲存體設計處理序無法連接到目標伺服器，則精靈會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c093d-120">The wizard will display an error message if [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is not running on the target server or if the storage design process is otherwise unable to connect to the target server.</span></span>  
  
 <span data-ttu-id="c093d-121">精靈的最後步驟可讓您處理或延遲處理。</span><span class="sxs-lookup"><span data-stu-id="c093d-121">The final step of the wizard allows you to process or defer processing.</span></span> <span data-ttu-id="c093d-122">處理會建立您以精靈設計的彙總，而延遲處理則會儲存所設計的彙總供未來處理，如此可讓設計活動繼續而不進行處理。</span><span class="sxs-lookup"><span data-stu-id="c093d-122">Processing creates the aggregations you design with the wizard, while deferring processing saves the designed aggregations for future processing, thus allowing design activities to continue without processing.</span></span> <span data-ttu-id="c093d-123">視分割區的大小而定，處理可能需要花費很多時間。</span><span class="sxs-lookup"><span data-stu-id="c093d-123">Depending on the size of the partition, processing may take considerable time.</span></span> <span data-ttu-id="c093d-124">您可以選擇中斷處理分割區。</span><span class="sxs-lookup"><span data-stu-id="c093d-124">If you choose, you can interrupt processing a partition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c093d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c093d-125">See Also</span></span>  
 [<span data-ttu-id="c093d-126">彙總和彙總設計</span><span class="sxs-lookup"><span data-stu-id="c093d-126">Aggregations and Aggregation Designs</span></span>](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
