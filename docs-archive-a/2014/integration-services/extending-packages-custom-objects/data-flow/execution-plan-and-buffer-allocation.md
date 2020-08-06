---
title: 執行計畫和緩衝配置 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom data flow components [Integration Services], buffer allocations
- custom data flow components [Integration Services], execution plans
- buffer allocations [Integration Services]
- data flow components [Integration Services], buffer allocations
- data flow components [Integration Services], execution plans
- execution plans [Integration Services]
ms.assetid: 679d9ff0-641e-47c3-abb8-d1a7dcb279dd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 03b8bb22988ccf77f8920252ac2d600478c92f3b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688069"
---
# <a name="execution-plan-and-buffer-allocation"></a><span data-ttu-id="ce504-102">執行計劃和緩衝區配置</span><span class="sxs-lookup"><span data-stu-id="ce504-102">Execution Plan and Buffer Allocation</span></span>
  <span data-ttu-id="ce504-103">在執行之前，資料流程工作會檢查其元件並為元件的每個順序產生執行計劃。</span><span class="sxs-lookup"><span data-stu-id="ce504-103">Before execution, the data flow task examines its components and generates an execution plan for each sequence of components.</span></span> <span data-ttu-id="ce504-104">本節提供有關執行計劃的詳細資料、如何檢視計劃以及輸入與輸出緩衝區如何根據執行計劃配置。</span><span class="sxs-lookup"><span data-stu-id="ce504-104">This section provides details about the execution plan, how to view the plan, and how input and output buffers are allocated based on the execution plan.</span></span>  
  
## <a name="understanding-the-execution-plan"></a><span data-ttu-id="ce504-105">了解執行計劃</span><span class="sxs-lookup"><span data-stu-id="ce504-105">Understanding the Execution Plan</span></span>  
 <span data-ttu-id="ce504-106">任何執行計劃都包含來源執行緒與工作執行緒，而且每個執行緒都包含工作清單，以指定來源執行緒的輸出工作清單，或是工作執行緒的輸入與輸出工作清單。</span><span class="sxs-lookup"><span data-stu-id="ce504-106">An execution plan contains source threads and work threads, and each thread contains work lists that specify output work lists for source threads or input and output work lists for work threads.</span></span> <span data-ttu-id="ce504-107">執行計畫中的來源執行緒代表資料流程中的來源元件，在執行計畫中以 *SourceThread\*\*n* 識別，其中 *n* 是來源執行緒從零開始的編號。</span><span class="sxs-lookup"><span data-stu-id="ce504-107">The source threads in an execution plan represent the source components in the data flow and are identified in the execution plan by *SourceThread\*\*n*, where *n* is the zero-based number of the source thread.</span></span>  
  
 <span data-ttu-id="ce504-108">每個來源執行緒會建立一個緩衝區、設定接聽程式，並且呼叫來源元件的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ce504-108">Each source thread creates a buffer, sets a listener, and calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method on the source component.</span></span> <span data-ttu-id="ce504-109">這是執行開始和資料起源的地方，即來源元件開始將資料列加入資料流程工作所提供的輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ce504-109">This is where execution starts and data originates, as the source component starts adding rows to the output buffers that are provided to it by the data flow task.</span></span> <span data-ttu-id="ce504-110">在來源執行緒執行之後，會將工作平衡地散佈在工作執行緒之間。</span><span class="sxs-lookup"><span data-stu-id="ce504-110">After the source threads are running, the balance of work is distributed among work threads.</span></span>  
  
 <span data-ttu-id="ce504-111">工作執行緒可能包含輸入和輸出工作清單，在執行計畫中識別為 *WorkThread\*\*n*，其中 *n* 是工作執行緒從零開始的編號。</span><span class="sxs-lookup"><span data-stu-id="ce504-111">A work thread may contain both input and output work lists and is identified in the execution plan as *WorkThread\*\*n*, where *n* is the zero-based number of the work thread.</span></span> <span data-ttu-id="ce504-112">當圖表包含具有非同步輸出的元件時，這些執行緒會包含輸出工作清單。</span><span class="sxs-lookup"><span data-stu-id="ce504-112">These threads contain output work lists when the graph contains a component with asynchronous outputs.</span></span>  
  
 <span data-ttu-id="ce504-113">下列範例執行計劃代表一個資料流程，其中包含連接到轉換的來源元件，而該轉換則帶有連接到目的地元件的非同步輸出。</span><span class="sxs-lookup"><span data-stu-id="ce504-113">The following sample execution plan represents a data flow that contains a source component connected to a transformation with an asynchronous output connected to a destination component.</span></span> <span data-ttu-id="ce504-114">在此範例中，WorkThread0 包含輸出工作清單，因為轉換元件具有非同步輸出。</span><span class="sxs-lookup"><span data-stu-id="ce504-114">In this example, WorkThread0 contains an output work list because the transformation component has an asynchronous output.</span></span>  
  
```  
SourceThread0   
    Influences: 72 158   
    Output Work List   
        CreatePrimeBuffer of type 1 for output id 10   
        SetBufferListener: "WorkThread0" for input ID 73   
        CallPrimeOutput on component "OLE DB Source" (1)   
    End Output Work List   
    This thread drives 0 distributors   
End SourceThread0   
WorkThread0   
    Influences: 72 158   
    Input Work list, input ID 73   
        CallProcessInput on input ID 73 on component "Sort" (72) for view type 2   
    End Input Work list for input 73   
    Output Work List   
        CreatePrimeBuffer of type 3 for output id 74   
        SetBufferListener: "WorkThread1" for input ID 171with internal handoff   
        CallPrimeOutput on component "Sort" (72)   
    End Output Work List   
    This thread drives 0 distributors   
End WorkThread0   
WorkThread1   
    Influences: 158   
    Input Work list, input ID 171  
        CallProcessInput on input ID 171 on component "OLE DB Destination" (158) for view type 4  
    End Input Work list for input 171   
    Output Work List   
    End Output Work List   
    This thread drives 0 distributors   
End WorkThread1  
```  
  
> [!NOTE]  
>  <span data-ttu-id="ce504-115">每次執行套件時，就會產生執行計畫，而且透過將記錄提供者新增至套件，就可以擷取該計畫，以允許記錄和選取 **PipelineExecutionPlan** 事件。</span><span class="sxs-lookup"><span data-stu-id="ce504-115">The execution plan is generated every time a package is executed, and can be captured by adding a log provider to the package, enabling logging, and selecting the **PipelineExecutionPlan** event.</span></span>  
  
## <a name="understanding-buffer-allocation"></a><span data-ttu-id="ce504-116">了解緩衝區配置</span><span class="sxs-lookup"><span data-stu-id="ce504-116">Understanding Buffer Allocation</span></span>  
 <span data-ttu-id="ce504-117">根據執行計劃，資料流程工作會建立緩衝區，以包含資料流程元件的輸出中所定義的資料行。</span><span class="sxs-lookup"><span data-stu-id="ce504-117">Based on the execution plan, the data flow task creates buffers that contain the columns defined in the outputs of the data flow components.</span></span> <span data-ttu-id="ce504-118">當資料流經元件的順序時，會重複使用緩衝區，直到遇到非同步輸出的元件為止。</span><span class="sxs-lookup"><span data-stu-id="ce504-118">The buffer is reused as the data flows through the sequence of components, until a component with asynchronous outputs is encountered.</span></span> <span data-ttu-id="ce504-119">接著會建立新緩衝區，它包含非同步輸出的輸出資料行，以及下游元件的輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="ce504-119">Then, a new buffer is created, which contains the output columns of the asynchronous output and the output columns of downstream components.</span></span>  
  
 <span data-ttu-id="ce504-120">在執行期間，元件可以存取目前來源或是工作執行緒中的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ce504-120">During execution, components have access to the buffer in the current source or work thread.</span></span> <span data-ttu-id="ce504-121">緩衝區可能是由 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法所提供的輸入緩衝區，或是由 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法所提供的輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ce504-121">The buffer is either an input buffer, provided by the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method, or an output buffer, provided by the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method.</span></span> <span data-ttu-id="ce504-122"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.Mode%2A> 的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 屬性也可將每個緩衝區識別為輸入或是輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ce504-122">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.Mode%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> also identifies each buffer as an input or output buffer.</span></span>  
  
 <span data-ttu-id="ce504-123">具有非同步輸出的轉換元件會從 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法接收現有輸入緩衝區，並從 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法接收新輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ce504-123">Transformation components with asynchronous outputs receive the existing input buffer from the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method, and receive the new output buffer from the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method.</span></span> <span data-ttu-id="ce504-124">具有非同步輸出的轉換元件是唯一會接收輸入和輸出緩衝區的資料流程元件類型。</span><span class="sxs-lookup"><span data-stu-id="ce504-124">A transformation component with asynchronous outputs is the only type of data flow component that receives both an input and an output buffer.</span></span>  
  
 <span data-ttu-id="ce504-125">因為提供給元件的緩衝區，有可能包含比該元件在其輸入或輸出資料行集合中所擁有的資料行還要多的資料行，所以元件開發人員可以呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> 方法，以指定其 `LineageID` 來找到緩衝區中的資料行。</span><span class="sxs-lookup"><span data-stu-id="ce504-125">Because the buffer provided to a component is likely to contain more columns than the component has in its input or output column collections, component developers can call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method to locate a column in the buffer by specifying its `LineageID`.</span></span>  
  
<span data-ttu-id="ce504-126">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="ce504-126">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ce504-127">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="ce504-127">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ce504-128">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="ce504-128">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ce504-129">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="ce504-129">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
