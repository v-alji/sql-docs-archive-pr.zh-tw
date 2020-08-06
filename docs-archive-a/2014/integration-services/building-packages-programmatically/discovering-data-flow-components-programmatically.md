---
title: 以程式設計方式探索資料流程元件 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PipelineComponentInfos collection
- data flow task [Integration Services], components
- discovering data flow components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: ff92a96a-8af6-4532-82cc-c0bbff92401b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a18102f38f1ad06e918efe2ca529185d40deef9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700147"
---
# <a name="discovering-data-flow-components-programmatically"></a><span data-ttu-id="b918c-102">以程式設計方式探索資料流程元件</span><span class="sxs-lookup"><span data-stu-id="b918c-102">Discovering Data Flow Components Programmatically</span></span>
  <span data-ttu-id="b918c-103">在將資料流程工作加入封裝之後，下一步可能就是要判斷有哪些資料流程元件可供您使用。</span><span class="sxs-lookup"><span data-stu-id="b918c-103">After you have added a data flow task to a package, your next step may be to determine what data flow components are available for your use.</span></span> <span data-ttu-id="b918c-104">您可以使用程式設計方式探索安裝在本機電腦上可供使用的資料流程來源、轉換和目的地。</span><span class="sxs-lookup"><span data-stu-id="b918c-104">You can programmatically discover the data flow sources, transformations, and destinations that are installed and available on the local computer.</span></span> <span data-ttu-id="b918c-105">如需將資料流程工作新增套件的資訊，請參閱[以程式設計方式新增資料流程工作](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="b918c-105">For information about adding a data flow task to the package, see [Adding the Data Flow Task Programmatically](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md).</span></span>  
  
## <a name="discovering-components"></a><span data-ttu-id="b918c-106">探索元件</span><span class="sxs-lookup"><span data-stu-id="b918c-106">Discovering Components</span></span>  
 <span data-ttu-id="b918c-107"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 類別提供 <xref:Microsoft.SqlServer.Dts.Runtime.Application.PipelineComponentInfos%2A> 集合，其中包含每個正確安裝在本機電腦之元件的 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> 物件。</span><span class="sxs-lookup"><span data-stu-id="b918c-107">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class provides the <xref:Microsoft.SqlServer.Dts.Runtime.Application.PipelineComponentInfos%2A> collection, which contains a <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> object for each component correctly installed on the local computer.</span></span> <span data-ttu-id="b918c-108">每個 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> 都包含元件的相關資訊，例如其名稱、描述和建立名稱。</span><span class="sxs-lookup"><span data-stu-id="b918c-108">Each <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> contains information about a component such as its name, description, and creation name.</span></span> <span data-ttu-id="b918c-109">當您將元件加入封裝時，可以使用在 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> 屬性中傳回的值，以設定 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> 的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 屬性。</span><span class="sxs-lookup"><span data-stu-id="b918c-109">You can use the value returned in the <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> property to set the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> when you add a component to a package.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="b918c-110">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b918c-110">Next Step</span></span>  
 <span data-ttu-id="b918c-111">在探索可用的元件之後，下一個步驟是新增和設定元件，這將在下一主題中討論：[以程式設計方式新增資料流程元件](../building-packages-programmatically/adding-data-flow-components-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="b918c-111">After discovering available components, the next step is to add and configure the components, which is discussed in the next topic, [Adding Data Flow Components Programmatically](../building-packages-programmatically/adding-data-flow-components-programmatically.md).</span></span>  
  
## <a name="sample"></a><span data-ttu-id="b918c-112">範例</span><span class="sxs-lookup"><span data-stu-id="b918c-112">Sample</span></span>  
 <span data-ttu-id="b918c-113">下列程式碼範例會示範如何列舉 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfos> 物件的 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 集合，以程式設計方式探索在本機電腦上可用的資料流程元件。</span><span class="sxs-lookup"><span data-stu-id="b918c-113">The following code sample shows how to enumerate the <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfos> collection of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> object to programmatically discover the data flow components available on the local computer.</span></span> <span data-ttu-id="b918c-114">這個範例需要 Microsoft.SqlServer.ManagedDTS 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="b918c-114">This sample requires a reference to the Microsoft.SqlServer.ManagedDTS assembly.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Application application = new Application();  
      PipelineComponentInfos componentInfos = application.PipelineComponentInfos;  
  
      foreach (PipelineComponentInfo componentInfo in componentInfos)  
      {  
        Console.WriteLine("Name: " + componentInfo.Name + "\n" +  
          " CreationName: " + componentInfo.CreationName + "\n");  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim application As Application = New Application()  
  
    Dim componentInfos As PipelineComponentInfos = application.PipelineComponentInfos  
  
    For Each componentInfo As PipelineComponentInfo In componentInfos  
      Console.WriteLine("Name: " & componentInfo.Name & vbCrLf & _  
        " CreationName: " & componentInfo.CreationName & vbCrLf)  
    Next  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
<span data-ttu-id="b918c-115">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="b918c-115">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="b918c-116">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="b918c-116">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="b918c-117">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="b918c-117">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="b918c-118">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="b918c-118">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b918c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b918c-119">See Also</span></span>  
 [<span data-ttu-id="b918c-120">以程式設計方式加入資料流程元件</span><span class="sxs-lookup"><span data-stu-id="b918c-120">Adding Data Flow Components Programmatically</span></span>](../building-packages-programmatically/adding-data-flow-components-programmatically.md)  
  
  
