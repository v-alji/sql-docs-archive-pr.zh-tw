---
title: 開發特定類型的指令碼元件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: dfbbe959-6b4e-4b47-b9dd-bcc31929482d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 114c9ddca90ea02a8e1847444b28b9d5876650a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596777"
---
# <a name="developing-specific-types-of-script-components"></a><span data-ttu-id="33111-102">開發特定類型的指令碼元件</span><span class="sxs-lookup"><span data-stu-id="33111-102">Developing Specific Types of Script Components</span></span>
  <span data-ttu-id="33111-103">指令碼元件是您可以在封裝的資料流程中使用的可設定工具，幾乎可滿足 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 所含的來源、轉換和目的地未能達成的任何需求。</span><span class="sxs-lookup"><span data-stu-id="33111-103">The Script component is a configurable tool that you can use in the data flow of a package to fill almost any requirement that is not met by the sources, transformations, and destinations that are included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="33111-104">本章節包含指令碼元件程式碼範例，以示範設定指令碼元件的四種選項：</span><span class="sxs-lookup"><span data-stu-id="33111-104">This section contains Script component code samples that demonstrate the four options for configuring the Script component:</span></span>  
  
-   <span data-ttu-id="33111-105">做為來源。</span><span class="sxs-lookup"><span data-stu-id="33111-105">As a source.</span></span>  
  
-   <span data-ttu-id="33111-106">做為具有同步輸出的轉換。</span><span class="sxs-lookup"><span data-stu-id="33111-106">As a transformation with synchronous outputs.</span></span>  
  
-   <span data-ttu-id="33111-107">做為具有非同步輸出的轉換。</span><span class="sxs-lookup"><span data-stu-id="33111-107">As a transformation with asynchronous outputs.</span></span>  
  
-   <span data-ttu-id="33111-108">做為目的地。</span><span class="sxs-lookup"><span data-stu-id="33111-108">As a destination.</span></span>  
  
 <span data-ttu-id="33111-109">如需指令碼元件的其他範例，請參閱[其他指令碼元件範例](../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="33111-109">For additional examples of the Script component, see [Additional Script Component Examples](../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="33111-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="33111-110">In This Section</span></span>  
 [<span data-ttu-id="33111-111">以指令碼元件建立來源</span><span class="sxs-lookup"><span data-stu-id="33111-111">Creating a Source with the Script Component</span></span>](creating-a-source-with-the-script-component.md)  
 <span data-ttu-id="33111-112">說明和示範如何使用指令碼元件建立資料流程來源。</span><span class="sxs-lookup"><span data-stu-id="33111-112">Explains and demonstrates how to create a data flow source by using the Script component.</span></span>  
  
 [<span data-ttu-id="33111-113">使用指令碼元件建立同步轉換</span><span class="sxs-lookup"><span data-stu-id="33111-113">Creating a Synchronous Transformation with the Script Component</span></span>](creating-a-synchronous-transformation-with-the-script-component.md)  
 <span data-ttu-id="33111-114">說明和示範如何使用指令碼元件建立具有同步輸出的資料流程轉換。</span><span class="sxs-lookup"><span data-stu-id="33111-114">Explains and demonstrates how to create a data flow transformation with synchronous outputs by using the Script component.</span></span> <span data-ttu-id="33111-115">這種轉換會在資料列通過元件時就地修改資料列。</span><span class="sxs-lookup"><span data-stu-id="33111-115">This kind of transformation modifies rows of data in place as they pass through the component.</span></span>  
  
 [<span data-ttu-id="33111-116">使用指令碼元件建立非同步轉換</span><span class="sxs-lookup"><span data-stu-id="33111-116">Creating an Asynchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
 <span data-ttu-id="33111-117">說明和示範如何使用指令碼元件建立具有非同步輸出的資料流程轉換。</span><span class="sxs-lookup"><span data-stu-id="33111-117">Explains and demonstrates how to create a data flow transformation with asynchronous outputs by using the Script component.</span></span> <span data-ttu-id="33111-118">這種轉換必須先讀取所有的資料列，才可以將更多的資訊 (例如，計算的彙總) 加入通過元件的資料。</span><span class="sxs-lookup"><span data-stu-id="33111-118">This kind of transformation has to read all rows of data before it can add more information, such as calculated aggregates, to the data that passes through the component.</span></span>  
  
 [<span data-ttu-id="33111-119">使用指令碼元件建立目的地</span><span class="sxs-lookup"><span data-stu-id="33111-119">Creating a Destination with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
 <span data-ttu-id="33111-120">說明和示範如何使用指令碼元件建立資料流程目的地。</span><span class="sxs-lookup"><span data-stu-id="33111-120">Explains and demonstrates how to create a data flow destination by using the Script component.</span></span>  
  
<span data-ttu-id="33111-121">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="33111-121">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="33111-122">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="33111-122">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="33111-123">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="33111-123">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="33111-124">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="33111-124">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33111-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33111-125">See Also</span></span>  
 <span data-ttu-id="33111-126">[比較腳本解決方案和自訂物件](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span><span class="sxs-lookup"><span data-stu-id="33111-126">[Comparing Scripting Solutions and Custom Objects](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span></span>  
 [<span data-ttu-id="33111-127">開發特定類型的資料流程元件</span><span class="sxs-lookup"><span data-stu-id="33111-127">Developing Specific Types of Data Flow Components</span></span>](../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
  
  
