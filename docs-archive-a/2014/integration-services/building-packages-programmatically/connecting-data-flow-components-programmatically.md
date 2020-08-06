---
title: 以程式設計的方式連線資料流程元件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], components
- paths [Integration Services], components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: 404ecab7-7698-447b-93d6-dd256beb11ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 39494fee5314f309b79abfd30303fdd607fd3c50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594646"
---
# <a name="connecting-data-flow-components-programmatically"></a><span data-ttu-id="2e17e-102">以程式設計的方式連接資料流程元件</span><span class="sxs-lookup"><span data-stu-id="2e17e-102">Connecting Data Flow Components Programmatically</span></span>
  <span data-ttu-id="2e17e-103">在將元件加入資料流程工作後，就可以連接元件以建立執行樹狀目錄，以代表從來源經過轉換到目的地的資料流程。</span><span class="sxs-lookup"><span data-stu-id="2e17e-103">After you have added components to the data flow task, you connect them to create an execution tree that represents the flow of data from sources through transformations to destinations.</span></span> <span data-ttu-id="2e17e-104">您使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> 物件以連接資料流程中的元件。</span><span class="sxs-lookup"><span data-stu-id="2e17e-104">You use <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> objects to connect the components in the data flow.</span></span>  
  
## <a name="creating-a-path"></a><span data-ttu-id="2e17e-105">建立路徑</span><span class="sxs-lookup"><span data-stu-id="2e17e-105">Creating a Path</span></span>  
 <span data-ttu-id="2e17e-106">呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipe> 介面中 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.PathCollection%2A> 屬性的 New 方法，以建立新路徑並將它新增資料流程工作中的路徑集合。</span><span class="sxs-lookup"><span data-stu-id="2e17e-106">Call the New method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.PathCollection%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipe> interface to create a new path and add it to the collection of paths in the data flow task.</span></span> <span data-ttu-id="2e17e-107">此方法會傳回中斷連接的新 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> 物件，您可用以連接兩個元件。</span><span class="sxs-lookup"><span data-stu-id="2e17e-107">This method returns a new, disconnected <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> object, which you then use to connect two components.</span></span>  
  
 <span data-ttu-id="2e17e-108">呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100.AttachPathAndPropagateNotifications%2A> 方法以連接路徑並通知元件參與已連接它們的路徑。</span><span class="sxs-lookup"><span data-stu-id="2e17e-108">Call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100.AttachPathAndPropagateNotifications%2A> method to connect the path and to notify the components participating in the path that they have been connected.</span></span> <span data-ttu-id="2e17e-109">這個方法會以參數的方式接受上游元件的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>以及下游元件的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>。</span><span class="sxs-lookup"><span data-stu-id="2e17e-109">This method accepts an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> of the upstream component and an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> of the downstream component as parameters.</span></span> <span data-ttu-id="2e17e-110">依預設，呼叫元件的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 方法會為具有輸入的元件建立單一輸入，並為具有輸出的元件建立單一輸出。</span><span class="sxs-lookup"><span data-stu-id="2e17e-110">By default, the call to the component's <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method creates a single input for components that have inputs, and a single output for components that have outputs.</span></span> <span data-ttu-id="2e17e-111">下列範例使用目的地之來源與輸入的這個預設輸出。</span><span class="sxs-lookup"><span data-stu-id="2e17e-111">The following example uses this default output of the source and input of the destination.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="2e17e-112">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2e17e-112">Next Step</span></span>  
 <span data-ttu-id="2e17e-113">在您建立兩個元件之間的路徑之後，下一個步驟就是要對應下游元件中的輸入資料行，這將在下一主題中討論：[以程式設計方式選取輸入資料行](../building-packages-programmatically/selecting-input-columns-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="2e17e-113">After you establish a path between two components, the next step is to map input columns in the downstream component, which is discussed in the next topic, [Selecting Input Columns Programmatically](../building-packages-programmatically/selecting-input-columns-programmatically.md).</span></span>  
  
## <a name="sample"></a><span data-ttu-id="2e17e-114">範例</span><span class="sxs-lookup"><span data-stu-id="2e17e-114">Sample</span></span>  
 <span data-ttu-id="2e17e-115">下列程式碼範例示範如何在兩個元件之間建立路徑。</span><span class="sxs-lookup"><span data-stu-id="2e17e-115">The following code sample shows how to establish a path between two components.</span></span>  
  
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
      Package package = new Package();  
      Executable e = package.Executables.Add("STOCK:PipelineTask");  
      TaskHost thMainPipe = e as TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;  
  
      // Create the source component.    
      IDTSComponentMetaData100 source =  
        dataFlowTask.ComponentMetaDataCollection.New();  
      source.ComponentClassID = "DTSAdapter.OleDbSource";  
      CManagedComponentWrapper srcDesignTime = source.Instantiate();  
      srcDesignTime.ProvideComponentProperties();  
  
      // Create the destination component.  
      IDTSComponentMetaData100 destination =  
        dataFlowTask.ComponentMetaDataCollection.New();  
      destination.ComponentClassID = "DTSAdapter.OleDbDestination";  
      CManagedComponentWrapper destDesignTime = destination.Instantiate();  
      destDesignTime.ProvideComponentProperties();  
  
      // Create the path.  
      IDTSPath100 path = dataFlowTask.PathCollection.New();  
      path.AttachPathAndPropagateNotifications(source.OutputCollection[0],  
        destination.InputCollection[0]);  
    }  
  }  
```  
  
 <span data-ttu-id="2e17e-116">}</span><span class="sxs-lookup"><span data-stu-id="2e17e-116">}</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Microsoft.SqlServer.Dts.Runtime.Package = _  
      New Microsoft.SqlServer.Dts.Runtime.Package()  
    Dim e As Executable = package.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As Microsoft.SqlServer.Dts.Runtime.TaskHost = _  
      CType(e, Microsoft.SqlServer.Dts.Runtime.TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
    ' Create the source component.    
    Dim source As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    source.ComponentClassID = "DTSAdapter.OleDbSource"  
    Dim srcDesignTime As CManagedComponentWrapper = source.Instantiate()  
    srcDesignTime.ProvideComponentProperties()  
  
    ' Create the destination component.  
    Dim destination As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    destination.ComponentClassID = "DTSAdapter.OleDbDestination"  
    Dim destDesignTime As CManagedComponentWrapper = destination.Instantiate()  
    destDesignTime.ProvideComponentProperties()  
  
    ' Create the path.  
    Dim path As IDTSPath100 = dataFlowTask.PathCollection.New()  
    path.AttachPathAndPropagateNotifications(source.OutputCollection(0), _  
      destination.InputCollection(0))  
  
  End Sub  
  
End Module  
```  
  
<span data-ttu-id="2e17e-117">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="2e17e-117">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="2e17e-118">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="2e17e-118">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="2e17e-119">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="2e17e-119">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="2e17e-120">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="2e17e-120">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e17e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e17e-121">See Also</span></span>  
 [<span data-ttu-id="2e17e-122">以程式設計方式選取輸入資料行</span><span class="sxs-lookup"><span data-stu-id="2e17e-122">Selecting Input Columns Programmatically</span></span>](../building-packages-programmatically/selecting-input-columns-programmatically.md)  
  
  
