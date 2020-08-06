---
title: 平衡型資料分配器轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.balanceddatadistributor.f1
ms.assetid: ae0b33dd-f44b-42df-b6f6-69861770ce10
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 09591013bc1f21659720fa9fec2e94167be93a1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595220"
---
# <a name="balanced-data-distributor-transformation"></a><span data-ttu-id="59dfd-102">平衡資料分佈器轉換</span><span class="sxs-lookup"><span data-stu-id="59dfd-102">Balanced Data Distributor Transformation</span></span>
  <span data-ttu-id="59dfd-103">平衡資料分佈器 (BDD) 轉換利用新型 CPU 的並行處理能力。</span><span class="sxs-lookup"><span data-stu-id="59dfd-103">The Balanced Data Distributor (BDD) transformation takes advantage of concurrent processing capability of modern CPUs.</span></span> <span data-ttu-id="59dfd-104">它會將傳入資料列的緩衝區一致地分佈到個別執行緒上的輸出。</span><span class="sxs-lookup"><span data-stu-id="59dfd-104">It distributes buffers of incoming rows uniformly across outputs on separate threads.</span></span> <span data-ttu-id="59dfd-105">透過針對每個輸出路徑使用個別執行緒，BDD 元件可提升 SSIS 封裝在多核心或多處理器機器上的效能。</span><span class="sxs-lookup"><span data-stu-id="59dfd-105">By using separate threads for each output path, the BDD component improves the performance of an SSIS package on multi-core or multi-processor machines.</span></span> <span data-ttu-id="59dfd-106">BDD 元件是 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 功能套件的一部分。</span><span class="sxs-lookup"><span data-stu-id="59dfd-106">The BDD component is part of the Feature Pack for [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="59dfd-107">請從[這裡](https://go.microsoft.com/fwlink/p/?LinkId=391999)下載並安裝。</span><span class="sxs-lookup"><span data-stu-id="59dfd-107">Download and install it from [here](https://go.microsoft.com/fwlink/p/?LinkId=391999).</span></span>  
  
 <span data-ttu-id="59dfd-108">下列圖表顯示使用 BDD 轉換的簡單範例。</span><span class="sxs-lookup"><span data-stu-id="59dfd-108">The following diagram shows a simple example of using the BDD transformation.</span></span> <span data-ttu-id="59dfd-109">在此範例中，BDD 轉換會在從一般檔案來源輸入資料時，挑選一個管線緩衝區，然後以循環配置資源的方式向下傳送至三個輸出路徑的其中一個路徑。</span><span class="sxs-lookup"><span data-stu-id="59dfd-109">In this example, the BDD transformation picks one pipeline buffer at a time from the input data from a flat file source and sends it down one of the three output paths in a round robin fashion.</span></span> <span data-ttu-id="59dfd-110">在 SQL Server Data Tools 中，您可以在顯示資料流程工作屬性的 [屬性]\*\*\*\* 視窗中，查看 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.DefaultBufferSize%2A> (預設管線緩衝區大小) 和 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.DefaultBufferMaxRows%2A> (管線緩衝區中的預設最大資料列數) 的值。</span><span class="sxs-lookup"><span data-stu-id="59dfd-110">In SQL Server Data Tools, you can check the values of a <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.DefaultBufferSize%2A>(default size of the pipeline buffer) and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.DefaultBufferMaxRows%2A>(default maximum number of rows in a pipeline buffer) in the **Properties** window displaying properties of a data flow task.</span></span>  
  
 <span data-ttu-id="59dfd-111">![平衡型資料分配器](../../media/balanceddatadistributor.JPG "平衡型資料散發者")</span><span class="sxs-lookup"><span data-stu-id="59dfd-111">![Balanced Data Distributor](../../media/balanceddatadistributor.JPG "Balanced Data Distributor")</span></span>  
  
 <span data-ttu-id="59dfd-112">在符合下列條件的狀況下，平衡資料分佈器轉換將有助於提升封裝的效能：</span><span class="sxs-lookup"><span data-stu-id="59dfd-112">The Balanced Data Distributor transformation helps improve performance of a package in a scenario that satisfies the following conditions:</span></span>  
  
1.  <span data-ttu-id="59dfd-113">大量資料傳入 BDD 轉換。</span><span class="sxs-lookup"><span data-stu-id="59dfd-113">There is large amount of data coming into the BDD transformation.</span></span> <span data-ttu-id="59dfd-114">如果資料大小很小，而且只要一個緩衝區即可保存資料，則不需要使用 BDD 轉換。</span><span class="sxs-lookup"><span data-stu-id="59dfd-114">If the data size is small and only one buffer can hold the data, there is no point in using the BDD transformation.</span></span> <span data-ttu-id="59dfd-115">如果資料大小很大，而且需要多個緩衝區來保存資料，BDD 可透過個別執行緒有效率地並行處理資料緩衝區。</span><span class="sxs-lookup"><span data-stu-id="59dfd-115">If the data size is large and several buffers are required to hold the data, BDD can efficiently process buffers of data in parallel by using separate threads.</span></span>  
  
2.  <span data-ttu-id="59dfd-116">資料的讀取速度比資料流程其餘部分的處理速度更快。</span><span class="sxs-lookup"><span data-stu-id="59dfd-116">The data can be read faster than the rest of the data flow can process it.</span></span> <span data-ttu-id="59dfd-117">在此狀況下，資料轉換的執行速度會比資料傳入的速度更慢。</span><span class="sxs-lookup"><span data-stu-id="59dfd-117">In this scenario, the transformations that are performed on the data run slowly compared to the rate at which data is coming.</span></span> <span data-ttu-id="59dfd-118">如果瓶頸在目的地，目的地必須可以並行處理。</span><span class="sxs-lookup"><span data-stu-id="59dfd-118">If the bottleneck is at the destination, the destination must be parallelizable though.</span></span>  
  
3.  <span data-ttu-id="59dfd-119">資料不需要經過排序。</span><span class="sxs-lookup"><span data-stu-id="59dfd-119">The data does not need to be ordered.</span></span> <span data-ttu-id="59dfd-120">例如，如果資料需要保持固定順序，則不應該使用 BDD 轉換分割資料。</span><span class="sxs-lookup"><span data-stu-id="59dfd-120">For example, if the data needs to stay sorted, you should not split the data using the BDD transformation.</span></span>  
  
 <span data-ttu-id="59dfd-121">請注意，如果 SSIS 封裝的瓶頸是由於資料可從來源讀取的速度，則 BDD 元件對於提升效能並沒有幫助。</span><span class="sxs-lookup"><span data-stu-id="59dfd-121">Note that if the bottleneck in an SSIS package is due to the rate at which data can be read from the source, the BDD component does not help improve the performance.</span></span> <span data-ttu-id="59dfd-122">如果 SSIS 封裝的瓶頸是因為目的地不支援平行處理原則，則 BDD 沒有用；不過，您可以平行執行所有轉換，並使用聯集全部轉換結合 BDD 轉換之不同輸出路徑傳出的輸出資料，再將資料傳送至目的地。</span><span class="sxs-lookup"><span data-stu-id="59dfd-122">If the bottleneck in an SSIS package is because the destination does not support parallelism, the BDD does not help; however, you can perform all the transformations in parallel and use the Union All transformation to combine the output data coming out of different output paths of the BDD transformation before sending the data to the destination.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="59dfd-123">如需使用轉換的示範簡報，請參閱 TechNet Library 上的 [平衡型資料分配器影片](https://go.microsoft.com/fwlink/?LinkID=226278) 。</span><span class="sxs-lookup"><span data-stu-id="59dfd-123">See the [Balanced Data Distributor video](https://go.microsoft.com/fwlink/?LinkID=226278) on the TechNet Library for a presentation with a demo on using the transformation.</span></span>  
  
  
