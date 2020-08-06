---
title: 以程式設計方式新增資料流程工作 | Microsoft Docs
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
- adding Data Flow task
- SSIS data flow
- data flow task [Integration Services], adding
- MainPipe object
ms.assetid: 0ca03712-a82e-4aa7-949b-f869a8936ddf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f7e699cc8e88bafb2a4508fdac8560fa73befe1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594650"
---
# <a name="adding-the-data-flow-task-programmatically"></a><span data-ttu-id="33e76-102">以程式設計方式加入資料流程工作</span><span class="sxs-lookup"><span data-stu-id="33e76-102">Adding the Data Flow Task Programmatically</span></span>
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="33e76-103">包括稱為「資料流程」工作的一項工作，該工作是由物件模型中的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper> 命名空間所表示。</span><span class="sxs-lookup"><span data-stu-id="33e76-103">includes a task called the Data Flow task, which is represented by the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper> namespace in the object model.</span></span> <span data-ttu-id="33e76-104">「資料流程」工作是一項特殊且高效能的工作，專門用來在封裝執行期間轉換及移動資料。</span><span class="sxs-lookup"><span data-stu-id="33e76-104">The Data Flow task is a specialized, high-performance task, dedicated to transforming and moving data during package execution.</span></span> <span data-ttu-id="33e76-105">就像其他工作一樣，「資料流程」工作是由 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 物件所包裝，而且從執行階段引擎的觀點來看，這項工作只是封裝內的另一項工作。</span><span class="sxs-lookup"><span data-stu-id="33e76-105">Like other tasks, the Data Flow task is wrapped by the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object, and from the perspective of the run-time engine, this task is just another task in the package.</span></span> <span data-ttu-id="33e76-106">但是，此資料流程包含了其他稱為資料流程元件的物件。</span><span class="sxs-lookup"><span data-stu-id="33e76-106">However, the data flow contains additional objects called data flow components.</span></span> <span data-ttu-id="33e76-107">這些元件是讓資料從來源移到目的地的元件，有時是透過轉換。</span><span class="sxs-lookup"><span data-stu-id="33e76-107">These components are the components that make data move from a source to a destination, sometimes through a transformation.</span></span> <span data-ttu-id="33e76-108">這些元件會定義移動的方向及轉換資料的方式。</span><span class="sxs-lookup"><span data-stu-id="33e76-108">The components define both the direction of movement and how data is transformed.</span></span> <span data-ttu-id="33e76-109">設定「資料流程」工作牽涉到在此工作中加入元件，然後連接這些元件來建立資料流程，並達成所要的轉換。</span><span class="sxs-lookup"><span data-stu-id="33e76-109">Configuring the Data Flow task involves adding components to the task, and then connecting them to establish the flow of data and achieve the intended transformation.</span></span>  
  
 <span data-ttu-id="33e76-110">「資料流程」工作內有三種類型的元件：[資料流程來源]  、[資料流程轉換]  和 [資料流程目的地]  ，這些元件會依照這個順序顯示在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師工具箱內。</span><span class="sxs-lookup"><span data-stu-id="33e76-110">There are three types of components within a Data Flow task: **Data Flow Sources**, **Data Flow Transformations**, and **Data Flow Destinations**, shown in that order within the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer toolbox.</span></span> <span data-ttu-id="33e76-111">這些類型也可以更簡單地稱為來源、轉換或目的地。</span><span class="sxs-lookup"><span data-stu-id="33e76-111">These types are also referred to more simply as sources, transformations, or destinations.</span></span> <span data-ttu-id="33e76-112">如同名稱所指示，資料會從來源流向轉換，然後再流向目的地。</span><span class="sxs-lookup"><span data-stu-id="33e76-112">As implied by the names, data flows from a source to a transformation, and then to a destination.</span></span> <span data-ttu-id="33e76-113">這是過於簡單的資料流程描述，目的是要說明此概念，但是「資料流程」工作更具彈性而且功能非常強大，足以處理多個來源，並將傳送輸出給多個目的地的許多轉換連接在一起。</span><span class="sxs-lookup"><span data-stu-id="33e76-113">This is a simplistic description of the data flow to illustrate the concept, but the Data Flow task is flexible and powerful enough to handle multiple sources, and to connect together many transformations that send output to multiple destinations.</span></span>  
  
 <span data-ttu-id="33e76-114">「資料流程」工作會加入到封裝中，其方式就像是加入其他工作一樣。</span><span class="sxs-lookup"><span data-stu-id="33e76-114">The Data Flow task is added to a package the same way other tasks are added.</span></span> <span data-ttu-id="33e76-115">當加入此工作之後，會進行設定，其方式是將元件加入到資料流程工作中，然後在此工作中設定及連接元件。</span><span class="sxs-lookup"><span data-stu-id="33e76-115">After the task has been added, it is configured by adding components to the data flow task, and configuring and connecting components in the task.</span></span>  
  
## <a name="sample"></a><span data-ttu-id="33e76-116">範例</span><span class="sxs-lookup"><span data-stu-id="33e76-116">Sample</span></span>  
 <span data-ttu-id="33e76-117">下列程式碼範例示範如何將「資料流程」工作加入到封裝。</span><span class="sxs-lookup"><span data-stu-id="33e76-117">The following code sample shows how to add a Data Flow task to a package.</span></span> <span data-ttu-id="33e76-118">此範例需要參考 Microsoft.SqlServer.PipelineHost、Microsoft.SqlServer.DTSPipelineWrap 和 Microsoft.SqlServer.ManagedDTS 組件。</span><span class="sxs-lookup"><span data-stu-id="33e76-118">This example requires a reference to the assemblies Microsoft.SqlServer.PipelineHost, Microsoft.SqlServer.DTSPipelineWrap, and Microsoft.SqlServer.ManagedDTS.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      Executable e = p.Executables.Add("STOCK:PipelineTask");  
      TaskHost thMainPipe = e as TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;   
    }  
  }  
}  
```  
  
```vb  
Imports System.IO  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    Dim e As Executable = p.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As TaskHost = CType(e, TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="33e76-119">外部資源</span><span class="sxs-lookup"><span data-stu-id="33e76-119">External Resources</span></span>  
 <span data-ttu-id="33e76-120">blogs.msdn.com 上的部落格文章：[EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223) (EzAPI - 針對 SQL Server 2012 更新)。</span><span class="sxs-lookup"><span data-stu-id="33e76-120">Blog entry, [EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223), on blogs.msdn.com.</span></span>  
  
<span data-ttu-id="33e76-121">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="33e76-121">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="33e76-122">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="33e76-122">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="33e76-123">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="33e76-123">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="33e76-124">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="33e76-124">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e76-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33e76-125">See Also</span></span>  
 [<span data-ttu-id="33e76-126">以程式設計方式探索資料流程元件</span><span class="sxs-lookup"><span data-stu-id="33e76-126">Discovering Data Flow Components Programmatically</span></span>](../building-packages-programmatically/discovering-data-flow-components-programmatically.md)  
  
  
