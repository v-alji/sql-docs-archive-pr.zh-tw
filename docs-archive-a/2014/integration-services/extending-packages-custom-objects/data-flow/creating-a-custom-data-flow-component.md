---
title: 建立自訂資料流程元件 | Microsoft Docs
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
- design-time component interface [Integration Services]
- custom data flow components [Integration Services], about data flow components
- custom data flow components [Integration Services]
- data flow components [Integration Services]
- data flow components [Integration Services], developing
ms.assetid: 9d96bcf5-eba8-44bd-b113-ed51ad0d0521
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 110d07ff88707ad1a01f299b6f532df99ce58404
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597231"
---
# <a name="creating-a-custom-data-flow-component"></a><span data-ttu-id="16edb-102">建立自訂資料流程元件</span><span class="sxs-lookup"><span data-stu-id="16edb-102">Creating a Custom Data Flow Component</span></span>
  <span data-ttu-id="16edb-103">在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中，資料流程工作會公開物件模型，讓開發人員透過使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 與受控碼來建立自訂資料流程元件 (來源、轉換和目的地)。</span><span class="sxs-lookup"><span data-stu-id="16edb-103">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], the data flow task exposes an object model that lets developers create custom data flow components-sources, transformations, and destinations-by using the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] and managed code.</span></span>  
  
 <span data-ttu-id="16edb-104">資料流程工作是由兩個元件所組成：<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 介面以及定義元件之間資料移動的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> 物件之集合。</span><span class="sxs-lookup"><span data-stu-id="16edb-104">A data flow task consists of components that contain an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface and a collection of <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> objects that define the movement of data between components.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="16edb-105">建立自訂提供者時，您需要使用中繼資料資料行值更新 ProviderDescriptors.xml 檔。</span><span class="sxs-lookup"><span data-stu-id="16edb-105">When you create a custom provider, you need to update the ProviderDescriptors.xml file with the metadata column values.</span></span>  
  
## <a name="design-time-and-run-time"></a><span data-ttu-id="16edb-106">設計階段與執行階段</span><span class="sxs-lookup"><span data-stu-id="16edb-106">Design Time and Run Time</span></span>  
 <span data-ttu-id="16edb-107">據說在執行之前，資料流程工作會設計狀態階段進行累加變更。</span><span class="sxs-lookup"><span data-stu-id="16edb-107">Before execution, the data flow task is said to be in a design-time state, as it undergoes incremental changes.</span></span> <span data-ttu-id="16edb-108">變更可包括元件的加入或移除、連接元件的路徑物件之加入或移除，以及對於元件中繼資料的變更。</span><span class="sxs-lookup"><span data-stu-id="16edb-108">Changes may include the addition or removal of components, the addition or removal of the path objects that connect components, and changes to the metadata of the components.</span></span> <span data-ttu-id="16edb-109">當中繼資料變更發生時，元件可以監視變更並對其做出反應。</span><span class="sxs-lookup"><span data-stu-id="16edb-109">When metadata changes occur, the component can monitor and react to the changes.</span></span> <span data-ttu-id="16edb-110">例如，元件可以不允許某些變更，或是做其他變更以回應變更。</span><span class="sxs-lookup"><span data-stu-id="16edb-110">For example, a component can disallow certain changes or to make additional changes in response to a change.</span></span> <span data-ttu-id="16edb-111">在設計階段，設計工具會透過設計階段 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 介面與元件互動。</span><span class="sxs-lookup"><span data-stu-id="16edb-111">At design time, the designer interacts with a component through the design-time <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface.</span></span>  
  
 <span data-ttu-id="16edb-112">在執行時，資料流程工作會檢查元件的順序、準備執行計劃以及管理執行工作計劃的工作者執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="16edb-112">At execution time, the data flow task examines the sequence of components, prepares an execution plan, and manages a pool of worker threads that execute the work plan.</span></span> <span data-ttu-id="16edb-113">雖然每個工作者執行緒都會執行資料流程工作內部的某些工作，但是工作者執行緒的主要工作是透過執行階段 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> 介面來呼叫元件的方法。</span><span class="sxs-lookup"><span data-stu-id="16edb-113">Although each worker thread performs some work that is internal to the data flow task, the principal task of the worker thread is to call the methods of the component through the run-time <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> interface.</span></span>  
  
## <a name="creating-a-component"></a><span data-ttu-id="16edb-114">建立元件</span><span class="sxs-lookup"><span data-stu-id="16edb-114">Creating a Component</span></span>  
 <span data-ttu-id="16edb-115">若要建立資料流程元件，您可以從 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 基底類別衍生類別、套用 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> 類別，然後覆寫基底類別的適當方法。</span><span class="sxs-lookup"><span data-stu-id="16edb-115">To create a data flow component, you derive a class from the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class, apply the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> class, and then override the appropriate methods of the base class.</span></span> <span data-ttu-id="16edb-116"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 會實作 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 與 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> 介面，並為您公開其方法以便在元件中覆寫。</span><span class="sxs-lookup"><span data-stu-id="16edb-116">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> interfaces, and exposes their methods for you to override in your component.</span></span>  
  
 <span data-ttu-id="16edb-117">視您的元件使用的物件而定，專案將需要參考下列組件的某些或是全部：</span><span class="sxs-lookup"><span data-stu-id="16edb-117">Depending on the objects used by your component, your project will require references to some or all of the following assemblies:</span></span>  
  
|<span data-ttu-id="16edb-118">功能</span><span class="sxs-lookup"><span data-stu-id="16edb-118">Feature</span></span>|<span data-ttu-id="16edb-119">要參考的組件</span><span class="sxs-lookup"><span data-stu-id="16edb-119">Assembly to reference</span></span>|<span data-ttu-id="16edb-120">要匯入的命名空間</span><span class="sxs-lookup"><span data-stu-id="16edb-120">Namespace to import</span></span>|  
|-------------|---------------------------|-------------------------|  
|<span data-ttu-id="16edb-121">設計師中</span><span class="sxs-lookup"><span data-stu-id="16edb-121">Data flow</span></span>|<span data-ttu-id="16edb-122">Microsoft.SqlServer.PipelineHost</span><span class="sxs-lookup"><span data-stu-id="16edb-122">Microsoft.SqlServer.PipelineHost</span></span>|<xref:Microsoft.SqlServer.Dts.Pipeline>|  
|<span data-ttu-id="16edb-123">資料流程包裝函數</span><span class="sxs-lookup"><span data-stu-id="16edb-123">Data flow wrapper</span></span>|<span data-ttu-id="16edb-124">Microsoft.SqlServer.DTSPipelineWrap</span><span class="sxs-lookup"><span data-stu-id="16edb-124">Microsoft.SqlServer.DTSPipelineWrap</span></span>|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>|  
|<span data-ttu-id="16edb-125">執行階段</span><span class="sxs-lookup"><span data-stu-id="16edb-125">Runtime</span></span>|<span data-ttu-id="16edb-126">Microsoft.SQLServer.ManagedDTS</span><span class="sxs-lookup"><span data-stu-id="16edb-126">Microsoft.SQLServer.ManagedDTS</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime>|  
|<span data-ttu-id="16edb-127">執行階段包裝函數</span><span class="sxs-lookup"><span data-stu-id="16edb-127">Runtime wrapper</span></span>|<span data-ttu-id="16edb-128">Microsoft.SqlServer.DTSRuntimeWrap</span><span class="sxs-lookup"><span data-stu-id="16edb-128">Microsoft.SqlServer.DTSRuntimeWrap</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper>|  
  
 <span data-ttu-id="16edb-129">下列程式碼範例顯示從基底類別衍生的簡單元件，並套用 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>。</span><span class="sxs-lookup"><span data-stu-id="16edb-129">The following code example shows a simple component that derives from the base class, and applies the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>.</span></span> <span data-ttu-id="16edb-130">您需要加入 DTSPipelineWrap 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="16edb-130">You need to add a reference to the DTSPipelineWrap assembly.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsPipelineComponent(DisplayName = "SampleComponent", ComponentType = ComponentType.Transform )]  
    public class BasicComponent: PipelineComponent  
    {  
        // TODO: Override the base class methods.  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
<DtsPipelineComponent(DisplayName:="SampleComponent", ComponentType:=ComponentType.Transform)> _  
Public Class BasicComponent  
  
    Inherits PipelineComponent  
  
    ' TODO: Override the base class methods.  
  
End Class  
```  
  
<span data-ttu-id="16edb-131">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="16edb-131">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="16edb-132">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="16edb-132">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="16edb-133">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="16edb-133">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="16edb-134">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="16edb-134">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16edb-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16edb-135">See Also</span></span>  
 [<span data-ttu-id="16edb-136">開發資料流程元件的使用者介面</span><span class="sxs-lookup"><span data-stu-id="16edb-136">Developing a User Interface for a Data Flow Component</span></span>](developing-a-user-interface-for-a-data-flow-component.md)  
  
  
