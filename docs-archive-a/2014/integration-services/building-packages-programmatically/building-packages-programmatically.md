---
title: 以程式設計方式建立封裝 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 7474b1f4-7607-4f28-a6fd-67f7db1dd3f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8ef8fd0b6b5bdeead718f204a0933771fe58924a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594648"
---
# <a name="building-packages-programmatically"></a><span data-ttu-id="6f6d3-102">以程式設計方式建立封裝</span><span class="sxs-lookup"><span data-stu-id="6f6d3-102">Building Packages Programmatically</span></span>
  <span data-ttu-id="6f6d3-103">如果您需要動態建立封裝，或要在開發環境以外的地方管理和執行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝，可以使用程式設計方式操作封裝。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-103">If you need to create packages dynamically, or to manage and execute [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages outside the development environment, you can manipulate packages programmatically.</span></span> <span data-ttu-id="6f6d3-104">在這種方法中，您有連續範圍的選項：</span><span class="sxs-lookup"><span data-stu-id="6f6d3-104">In this approach, you have a continuous range of options:</span></span>

-   <span data-ttu-id="6f6d3-105">在不須修改的情況下載入並執行現有的封裝。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-105">Load and execute an existing package without modification.</span></span>

-   <span data-ttu-id="6f6d3-106">載入現有的封裝、重新加以設定 (例如，針對不同的資料來源)，然後執行。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-106">Load an existing package, reconfigure it (for example, for a different data source), and execute it.</span></span>

-   <span data-ttu-id="6f6d3-107">建立新封裝、逐物件和逐屬性地加入與設定元件、儲存，然後加以執行。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-107">Create a new package, add and configure components object by object and property by property, save it, and execute it.</span></span>

 <span data-ttu-id="6f6d3-108">您可以透過任何 Managed 程式語言，使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 物件模型撰寫用來建立、設定和執行封裝的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-108">You can use the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model to write code that creates, configures, and executes packages in any managed programming language.</span></span> <span data-ttu-id="6f6d3-109">例如，您可能會想要建立中繼資料驅動的封裝，以根據選取的資料來源及其資料表與資料行，設定其連接或是其資料來源、轉換與目的地。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-109">For example, you may want to create metadata-driven packages that configure their connections or their data sources, transformations, and destinations based on the selected data source and its tables and columns.</span></span>

 <span data-ttu-id="6f6d3-110">本節會描述和示範如何以程式設計方式逐行建立和設定封裝。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-110">This section describes and demonstrates how to create and configure a package programmatically line by line.</span></span> <span data-ttu-id="6f6d3-111">在封裝程式設計選項範圍中較不複雜的一端，您無須修改即可直接載入和執行現有的封裝，如[以程式設計方式執行及管理封裝](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-111">At the less complex end of the range of package programming options, you can simply load and run an existing package without modification as described in [Running and Managing Packages Programmatically](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md).</span></span>

 <span data-ttu-id="6f6d3-112">並未在此說明的中間選項是以範本形式載入現有的封裝、重新加以設定 (例如，針對不同的資料來源)，然後執行。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-112">An intermediate option not described here is that of loading an existing package as a template, reconfiguring it (for example, for a different data source), and executing it.</span></span> <span data-ttu-id="6f6d3-113">您也可以使用本節中的資訊，修改封裝中的現有物件。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-113">You can also use the information in this section to modify the existing objects in a package.</span></span>

> [!NOTE]
>  <span data-ttu-id="6f6d3-114">當您使用現有封裝做為範本，並修改資料流程中的現有資料行時，可能必須移除現有的資料行，並呼叫受影響元件的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-114">When you use an existing package as a template and modify existing columns in the data flow, you may have to remove existing columns and call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> method of affected components.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6f6d3-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="6f6d3-115">In This Section</span></span>
 <span data-ttu-id="6f6d3-116">[以程式設計方式建立封裝](../building-packages-programmatically/creating-a-package-programmatically.md)描述如何以程式設計方式建立封裝。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-116">[Creating a Package Programmatically](../building-packages-programmatically/creating-a-package-programmatically.md) Describes how to create a package programmatically.</span></span>

 <span data-ttu-id="6f6d3-117">[以程式設計方式加入](../building-packages-programmatically/adding-tasks-programmatically.md)工作描述如何將工作加入至封裝。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-117">[Adding Tasks Programmatically](../building-packages-programmatically/adding-tasks-programmatically.md) Describes how to add tasks to the package.</span></span>

 <span data-ttu-id="6f6d3-118">[以程式設計方式連接](../building-packages-programmatically/connecting-tasks-programmatically.md)工作描述如何根據上一個工作或容器的執行結果，控制封裝中容器和工作的執行。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-118">[Connecting Tasks Programmatically](../building-packages-programmatically/connecting-tasks-programmatically.md) Describes how to control execution of the containers and tasks in a package based on the result of the execution of a previous task or container.</span></span>

 <span data-ttu-id="6f6d3-119">[以程式設計方式新增連接](../building-packages-programmatically/adding-connections-programmatically.md)描述如何將連線管理員加入封裝。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-119">[Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md) Describes how to add connection managers to a package.</span></span>

 <span data-ttu-id="6f6d3-120">[以程式設計方式使用變數](../building-packages-programmatically/working-with-variables-programmatically.md)描述如何在封裝執行期間加入和使用變數。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-120">[Working with Variables Programmatically](../building-packages-programmatically/working-with-variables-programmatically.md) Describes how to add and use variables during package execution.</span></span>

 <span data-ttu-id="6f6d3-121">[以程式設計方式處理事件](../building-packages-programmatically/handling-events-programmatically.md)描述如何處理封裝和工作事件。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-121">[Handling Events Programmatically](../building-packages-programmatically/handling-events-programmatically.md) Describes how to handle package and task events.</span></span>

 <span data-ttu-id="6f6d3-122">[以程式設計方式啟用記錄](../building-packages-programmatically/enabling-logging-programmatically.md)描述如何啟用封裝或工作的記錄，以及如何將自訂篩選套用至記錄事件。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-122">[Enabling Logging Programmatically](../building-packages-programmatically/enabling-logging-programmatically.md) Describes how to enable logging for a package or task, and how to apply custom filters to log events.</span></span>

 <span data-ttu-id="6f6d3-123">[以程式設計方式加入資料流程工作](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md)描述如何加入和設定資料流程工作及其元件。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-123">[Adding the Data Flow Task Programmatically](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md) Describes how to add and configure the Data Flow task and its components.</span></span>

 <span data-ttu-id="6f6d3-124">[以程式設計方式探索資料流程元件](../building-packages-programmatically/discovering-data-flow-components-programmatically.md)描述如何偵測本機電腦上所安裝的元件。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-124">[Discovering Data Flow Components Programmatically](../building-packages-programmatically/discovering-data-flow-components-programmatically.md) Describes how to detect the components that are installed on the local computer.</span></span>

 <span data-ttu-id="6f6d3-125">[以程式設計方式加入資料流程元件](../building-packages-programmatically/adding-data-flow-components-programmatically.md)描述如何將元件加入至資料流程工作。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-125">[Adding Data Flow Components Programmatically](../building-packages-programmatically/adding-data-flow-components-programmatically.md) Describes how to add a component to a data flow task.</span></span>

 <span data-ttu-id="6f6d3-126">[以程式設計方式連接資料流程元件](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)描述如何連接兩個數據流元件。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-126">[Connecting Data Flow Components Programmatically](../building-packages-programmatically/connecting-data-flow-components-programmatically.md) Describes how to connect two data flow components.</span></span>

 <span data-ttu-id="6f6d3-127">[以程式設計方式選取輸入資料行](../building-packages-programmatically/selecting-input-columns-programmatically.md)描述如何從資料流程中的上游元件提供給元件的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-127">[Selecting Input Columns Programmatically](../building-packages-programmatically/selecting-input-columns-programmatically.md) Describes how to select input columns from those that are provided to a component by upstream components in the data flow.</span></span>

 <span data-ttu-id="6f6d3-128">[以程式設計方式儲存封裝](../building-packages-programmatically/saving-a-package-programmatically.md)描述如何以程式設計方式儲存封裝。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-128">[Saving a Package Programmatically](../building-packages-programmatically/saving-a-package-programmatically.md) Describes how to save a package programmatically.</span></span>

## <a name="reference"></a><span data-ttu-id="6f6d3-129">參考</span><span class="sxs-lookup"><span data-stu-id="6f6d3-129">Reference</span></span>
 <span data-ttu-id="6f6d3-130">[Integration Services 錯誤和訊息參考](../integration-services-error-and-message-reference.md)列出預先定義的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 錯誤碼及其符號名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-130">[Integration Services Error and Message Reference](../integration-services-error-and-message-reference.md) Lists the predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error codes with their symbolic names and descriptions.</span></span>

## <a name="related-sections"></a><span data-ttu-id="6f6d3-131">相關章節</span><span class="sxs-lookup"><span data-stu-id="6f6d3-131">Related Sections</span></span>
 <span data-ttu-id="6f6d3-132">[使用腳本擴充封裝](../extending-packages-scripting/extending-packages-with-scripting.md)討論如何使用腳本工作來擴充控制流程，以及如何使用腳本元件來擴充資料流程。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-132">[Extending Packages with Scripting](../extending-packages-scripting/extending-packages-with-scripting.md) Discusses how to extend the control flow by using the Script task, and how to extend the data flow by using the Script component.</span></span>

 <span data-ttu-id="6f6d3-133">[使用自訂物件擴充封裝](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)討論如何建立程式自訂工作、資料流程元件以及其他封裝物件，以便在多個封裝中使用。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-133">[Extending Packages with Custom Objects](../extending-packages-custom-objects/extending-packages-with-custom-objects.md) Discusses how to create program custom tasks, data flow components, and other package objects for use in multiple packages.</span></span>

 <span data-ttu-id="6f6d3-134">[以程式設計方式執行和管理封裝](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)討論如何列舉、執行和管理封裝及其儲存所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-134">[Running and Managing Packages Programmatically](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md) Discusses how to enumerate, run, and manage packages and the folders in which they are stored.</span></span>

## <a name="external-resources"></a><span data-ttu-id="6f6d3-135">外部資源</span><span class="sxs-lookup"><span data-stu-id="6f6d3-135">External Resources</span></span>

-   <span data-ttu-id="6f6d3-136">位於 www.codeplex.com/MSFTISProdSamples 的 CodePlex 範例：[Integration Services 產品範例](https://go.microsoft.com/fwlink/?LinkID=131204)</span><span class="sxs-lookup"><span data-stu-id="6f6d3-136">CodePlex samples, [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkID=131204), on www.codeplex.com/MSFTISProdSamples</span></span>

-   <span data-ttu-id="6f6d3-137">blogs.msdn.com 上的部落格文章：[Performance profiling your custom extensions](https://go.microsoft.com/fwlink/?LinkId=238831) (對自訂延伸模組進行效能分析)。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-137">Blog entry, [Performance profiling your custom extensions](https://go.microsoft.com/fwlink/?LinkId=238831), on blogs.msdn.com.</span></span>

<span data-ttu-id="6f6d3-138">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="6f6d3-138">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6f6d3-139">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="6f6d3-139">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6f6d3-140">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="6f6d3-140">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6f6d3-141">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="6f6d3-141">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f6d3-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f6d3-142">See Also</span></span>
 [<span data-ttu-id="6f6d3-143">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="6f6d3-143">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)


