---
title: 開發特定類型的資料流程元件 | Microsoft Docs
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
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: 348e219a-b8ff-425e-b9c6-811880101c54
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3e168c866e03bfa5fd1f32127e4bfd6e58a2e8d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705310"
---
# <a name="developing-specific-types-of-data-flow-components"></a><span data-ttu-id="edb83-102">開發特定類型的資料流程元件</span><span class="sxs-lookup"><span data-stu-id="edb83-102">Developing Specific Types of Data Flow Components</span></span>
  <span data-ttu-id="edb83-103">本節涵蓋開發來源元件、具有同步輸出的轉換元件、具有非同步輸出的轉換元件以及目的地元件的細節。</span><span class="sxs-lookup"><span data-stu-id="edb83-103">This section covers the specifics of developing source components, transformation components with synchronous outputs, transformation components with asynchronous outputs, and destination components.</span></span>  
  
 <span data-ttu-id="edb83-104">如需元件開發的一般資訊，請參閱[開發自訂資料流程元件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="edb83-104">For information about component development in general, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="edb83-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="edb83-105">In This Section</span></span>  
 [<span data-ttu-id="edb83-106">開發自訂來源元件</span><span class="sxs-lookup"><span data-stu-id="edb83-106">Developing a Custom Source Component</span></span>](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)  
 <span data-ttu-id="edb83-107">包含有關開發可從外部資料來源存取資料之元件的資訊，並將它提供給資料流程中的下游元件。</span><span class="sxs-lookup"><span data-stu-id="edb83-107">Contains information on developing a component that accesses data from an external data source and supplies it to downstream components in the data flow.</span></span>  
  
 [<span data-ttu-id="edb83-108">開發具有同步輸出的自訂轉換元件</span><span class="sxs-lookup"><span data-stu-id="edb83-108">Developing a Custom Transformation Component with Synchronous Outputs</span></span>](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)  
 <span data-ttu-id="edb83-109">包含有關開發其輸出會同步到其輸入之轉換元件的資訊。</span><span class="sxs-lookup"><span data-stu-id="edb83-109">Contains information on developing a transformation component whose outputs are synchronous to its inputs.</span></span> <span data-ttu-id="edb83-110">這些元件不會將資料加入資料流程，但是會在資料通過時處理它。</span><span class="sxs-lookup"><span data-stu-id="edb83-110">These components do not add data to the data flow, but process data as it passes through.</span></span>  
  
 [<span data-ttu-id="edb83-111">開發具有非同步輸出的自訂轉換元件</span><span class="sxs-lookup"><span data-stu-id="edb83-111">Developing a Custom Transformation Component with Asynchronous Outputs</span></span>](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)  
 <span data-ttu-id="edb83-112">包含有關開發其輸出不會同步到其輸入之轉換元件的資訊。</span><span class="sxs-lookup"><span data-stu-id="edb83-112">Contains information on developing a transformation component whose outputs are not synchronous to its inputs.</span></span> <span data-ttu-id="edb83-113">這些元件會從上游元件收到資料，但是也會將資料加入資料流程。</span><span class="sxs-lookup"><span data-stu-id="edb83-113">These components receive data from upstream components, but also add data to the dataflow.</span></span>  
  
 [<span data-ttu-id="edb83-114">開發自訂目的地元件</span><span class="sxs-lookup"><span data-stu-id="edb83-114">Developing a Custom Destination Component</span></span>](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)  
 <span data-ttu-id="edb83-115">包含有關開發可從資料流程的上游元件收到資料列，並可將資料列寫入外部資料來源之元件的資訊。</span><span class="sxs-lookup"><span data-stu-id="edb83-115">Contains information on developing a component that receives rows from upstream components in the data flow and writes them to an external data source.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="edb83-116">參考</span><span class="sxs-lookup"><span data-stu-id="edb83-116">Reference</span></span>  
 <xref:Microsoft.SqlServer.Dts.Pipeline>  
 <span data-ttu-id="edb83-117">包含用以建立自訂資料流程元件的類別與介面。</span><span class="sxs-lookup"><span data-stu-id="edb83-117">Contains the classes and interfaces used to create custom data flow components.</span></span>  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>  
 <span data-ttu-id="edb83-118">包含資料流程工作的 Unmanaged 類別與介面。</span><span class="sxs-lookup"><span data-stu-id="edb83-118">Contains the unmanaged classes and interfaces of the data flow task.</span></span> <span data-ttu-id="edb83-119">開發人員在以程式設計方式建立資料流程或是建立自訂資料流程元件時，使用這些以及 Managed <xref:Microsoft.SqlServer.Dts.Pipeline> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="edb83-119">The developer uses these, and the managed <xref:Microsoft.SqlServer.Dts.Pipeline> namespace, when building a data flow programmatically or creating custom data flow components.</span></span>  
  
<span data-ttu-id="edb83-120">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="edb83-120">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="edb83-121">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="edb83-121">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="edb83-122">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="edb83-122">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="edb83-123">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="edb83-123">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edb83-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edb83-124">See Also</span></span>  
 <span data-ttu-id="edb83-125">[比較腳本解決方案和自訂物件](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span><span class="sxs-lookup"><span data-stu-id="edb83-125">[Comparing Scripting Solutions and Custom Objects](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span></span>  
 [<span data-ttu-id="edb83-126">開發特定類型的指令碼元件</span><span class="sxs-lookup"><span data-stu-id="edb83-126">Developing Specific Types of Script Components</span></span>](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
  
  
