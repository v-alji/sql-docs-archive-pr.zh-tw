---
title: 其他指令碼元件範例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: 849dd38a-abb5-4702-a413-882aae3980a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 897ca075674f5c3dbaf355390fe8346580bf638a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597224"
---
# <a name="additional-script-component-examples"></a><span data-ttu-id="00d3b-102">額外的指令碼元件範例</span><span class="sxs-lookup"><span data-stu-id="00d3b-102">Additional Script Component Examples</span></span>
  <span data-ttu-id="00d3b-103">指令碼元件是您可以在封裝的資料流程中使用的可設定工具，幾乎可滿足 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 所含的來源、轉換和目的地未能達成的任何需求。</span><span class="sxs-lookup"><span data-stu-id="00d3b-103">The Script component is a configurable tool that you can use in the data flow of a package to fill almost any requirement that is not met by the sources, transformations, and destinations that are included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="00d3b-104">本節包含指令碼元件程式碼範例，以示範各種類型的可用功能。</span><span class="sxs-lookup"><span data-stu-id="00d3b-104">This section contains Script component code samples that demonstrate the various types of functionality that are available.</span></span>  
  
 <span data-ttu-id="00d3b-105">如需示範如何將指令碼元件設定為來源、轉換或目的地的範例，請參閱[開發特定類型的指令碼元件](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)。</span><span class="sxs-lookup"><span data-stu-id="00d3b-105">For samples that demonstrate how to configure the Script component as a basic source, transformation, or destination, see [Developing Specific Types of Script Components](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="00d3b-106">如果您要建立可以更輕鬆地在多個資料流程工作與多個封裝之間重複使用的元件，請考慮使用這些指令碼元件範例中的程式碼，做為自訂資料流程元件的起點。</span><span class="sxs-lookup"><span data-stu-id="00d3b-106">If you want to create components that you can more easily reuse across multiple Data Flow tasks and multiple packages, consider using the code in these Script component samples as the starting point for custom data flow components.</span></span> <span data-ttu-id="00d3b-107">如需詳細資訊，請參閱 [開發自訂資料流程元件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="00d3b-107">For more information, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00d3b-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="00d3b-108">In This Section</span></span>  
 [<span data-ttu-id="00d3b-109">模擬指令碼元件的錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="00d3b-109">Simulating an Error Output for the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)  
 <span data-ttu-id="00d3b-110">指令碼元件不支援標準錯誤輸出，但是只要經過少量的設定和程式碼撰寫，即可模擬標準錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="00d3b-110">The Script component does not support a standard error output, but you can simulate a standard error output with very little additional configuration and coding.</span></span>  
  
 [<span data-ttu-id="00d3b-111">使用指令碼元件增強錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="00d3b-111">Enhancing an Error Output with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-examples/enhancing-an-error-output-with-the-script-component.md)  
 <span data-ttu-id="00d3b-112">說明和示範如何使用指令碼元件，將其他資訊加入標準錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="00d3b-112">Explains and demonstrates how to add additional information to a standard error output by using the Script component.</span></span>  
  
 [<span data-ttu-id="00d3b-113">使用指令碼元件建立 ODBC 目的地</span><span class="sxs-lookup"><span data-stu-id="00d3b-113">Creating an ODBC Destination with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-examples/creating-an-odbc-destination-with-the-script-component.md)  
 <span data-ttu-id="00d3b-114">說明和示範如何使用指令碼元件，建立 ODBC 資料流程目的地。</span><span class="sxs-lookup"><span data-stu-id="00d3b-114">Explains and demonstrates how to create an ODBC data flow destination by using the Script component.</span></span>  
  
 [<span data-ttu-id="00d3b-115">使用指令碼元件剖析非標準文字檔案格式</span><span class="sxs-lookup"><span data-stu-id="00d3b-115">Parsing Non-Standard Text File Formats with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-examples/parsing-non-standard-text-file-formats-with-the-script-component.md)  
 <span data-ttu-id="00d3b-116">說明和示範如何將兩個不同的非標準文字檔案格式剖析成目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="00d3b-116">Explains and demonstrates how to parse two different non-standard text file formats into destination tables.</span></span>  
  
<span data-ttu-id="00d3b-117">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="00d3b-117">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="00d3b-118">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="00d3b-118">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="00d3b-119">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="00d3b-119">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="00d3b-120">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="00d3b-120">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
