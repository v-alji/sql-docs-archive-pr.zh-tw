---
title: 偵錯資料流程 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- progress reporting [Integration Services]
- data viewers [Integration Services]
- data flow [Integration Services], debugging
- debugging [Integration Services], data flow
- counting rows
ms.assetid: 1c574f1b-54f7-4c05-8e42-8620e2c1df0f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ed1d1b7ebb119d452ca3de92fdad47552d1cc36c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703102"
---
# <a name="debugging-data-flow"></a><span data-ttu-id="8e066-102">偵錯資料流程</span><span class="sxs-lookup"><span data-stu-id="8e066-102">Debugging Data Flow</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="8e066-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 和 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師包含許多功能和工具，可讓您用來對 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件中的資料流程進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="8e066-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] and the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer include features and tools that you can use to troubleshoot the data flows in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>  
  
-   [!INCLUDE[ssIS](../../includes/ssis-md.md)] <span data-ttu-id="8e066-104">設計師」會提供資料檢視器。</span><span class="sxs-lookup"><span data-stu-id="8e066-104">Designer provides data viewers.</span></span>  
  
-   [!INCLUDE[ssIS](../../includes/ssis-md.md)] <span data-ttu-id="8e066-105">設計師」和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 轉換會提供資料列計數。</span><span class="sxs-lookup"><span data-stu-id="8e066-105">Designer and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] transformations provide row counts.</span></span>  
  
-   [!INCLUDE[ssIS](../../includes/ssis-md.md)] <span data-ttu-id="8e066-106">設計師」提供執行階段的進度報表。</span><span class="sxs-lookup"><span data-stu-id="8e066-106">Designer provides progress reporting at run time.</span></span>  
  
## <a name="data-viewers"></a><span data-ttu-id="8e066-107">資料檢視器</span><span class="sxs-lookup"><span data-stu-id="8e066-107">Data Viewers</span></span>  
 <span data-ttu-id="8e066-108">資料檢視器可以顯示資料流程中兩個元件之間的資料。</span><span class="sxs-lookup"><span data-stu-id="8e066-108">Data viewers display data between two components in a data flow.</span></span> <span data-ttu-id="8e066-109">從資料來源擷取資料或資料第一次進入資料流程時、在轉換更新資料之前和之後，以及在資料載入其目的地之前，可以透過資料檢視器來顯示資料。</span><span class="sxs-lookup"><span data-stu-id="8e066-109">Data viewers can display data when the data is extracted from a data source and first enters a data flow, before and after a transformation updates the data, and before the data is loaded into its destination.</span></span>  
  
 <span data-ttu-id="8e066-110">若要檢視資料，請將資料檢視器附加至連接兩個資料流程元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="8e066-110">To view the data, you attach data viewers to the path that connects two data flow components.</span></span> <span data-ttu-id="8e066-111">具有在不同資料流程元件之間檢視資料的能力，可讓您更容易識別非預期的資料值、檢視轉換變更資料行值的方式，以及探索轉換失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="8e066-111">The ability to view data between data flow components makes it easier to identify unexpected data values, view the way a transformation changes column values, and discover the reason that a transformation fails.</span></span> <span data-ttu-id="8e066-112">例如，如果您發現參考資料表中的查閱失敗，為了修正此問題，您可能希望加入為空白資料行提供預設資料的轉換。</span><span class="sxs-lookup"><span data-stu-id="8e066-112">For example, you may find that a lookup in a reference table fails, and to correct this you may want to add a transformation that provides default data for blank columns.</span></span>  
  
 <span data-ttu-id="8e066-113">資料檢視器可以在方格中顯示資料。</span><span class="sxs-lookup"><span data-stu-id="8e066-113">A data viewer can display data in a grid.</span></span> <span data-ttu-id="8e066-114">使用方格時，您需要選取要顯示的資料行。</span><span class="sxs-lookup"><span data-stu-id="8e066-114">Using a grid, you select the columns to display.</span></span> <span data-ttu-id="8e066-115">選定資料行的值會以表格格式顯示。</span><span class="sxs-lookup"><span data-stu-id="8e066-115">The values for the selected columns display in a tabular format.</span></span>  
  
 <span data-ttu-id="8e066-116">您也可以在路徑上加入多個資料檢視器，</span><span class="sxs-lookup"><span data-stu-id="8e066-116">You can also include multiple data viewers on a path.</span></span> <span data-ttu-id="8e066-117">並以不同格式顯示相同資料，例如，建立資料的圖表檢視與方格檢視，或是為不同資料行建立不同的資料檢視器。</span><span class="sxs-lookup"><span data-stu-id="8e066-117">You can display the same data in different formats-for example, create a chart view and a grid view of the data-or create different data viewers for different columns of data.</span></span>  
  
 <span data-ttu-id="8e066-118">當您將資料檢視器加入至路徑時，「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」會在 **[資料流程]** 索引標籤之設計介面上的路徑旁邊，加入資料檢視器圖示。</span><span class="sxs-lookup"><span data-stu-id="8e066-118">When you add a data viewer to a path, [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer adds a data viewer icon to the design surface of the **Data Flow** tab, next to the path.</span></span> <span data-ttu-id="8e066-119">具備多個輸出的轉換 (例如「條件式分割」轉換) 可以在每個路徑上加入資料檢視器。</span><span class="sxs-lookup"><span data-stu-id="8e066-119">Transformations that can have multiple outputs, such as the Conditional Split transformation, can include a data viewer on each path.</span></span>  
  
 <span data-ttu-id="8e066-120">在執行階段， **[資料檢視器]** 視窗會開啟，並顯示以資料檢視器格式所指定的資訊。</span><span class="sxs-lookup"><span data-stu-id="8e066-120">At run time, a **Data Viewer** window opens and displays the information specified by the data viewer format.</span></span> <span data-ttu-id="8e066-121">例如，使用方格格式的資料檢視器會顯示選定資料行的資料、傳遞至資料流程元件的輸出資料列數目，以及顯示的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="8e066-121">For example, a data viewer that uses the grid format shows data for the selected columns, the number of output rows passed to the data flow component, and the number of rows displayed.</span></span> <span data-ttu-id="8e066-122">資訊會以逐一緩衝區的方式顯示，且根據資料流程中的資料列寬度而定，緩衝區可能包含一或多個資料列。</span><span class="sxs-lookup"><span data-stu-id="8e066-122">The information displays buffer by buffer and, depending on the width of the rows in the data flow, a buffer may contain more or fewer rows.</span></span>  
  
 <span data-ttu-id="8e066-123">在 **[資料檢視器]** 對話方塊中，您可以將資料複製到剪貼簿、從資料表清除所有資料、重新設定資料檢視器、繼續資料流程，以及卸離或附加資料檢視器。</span><span class="sxs-lookup"><span data-stu-id="8e066-123">In the **Data Viewer** dialog box, you can copy the data to the Clipboard, clear all data from the table, reconfigure the data viewer, resume the flow of data, and detach or attach the data viewer.</span></span>  
  
#### <a name="to-add-a-data-viewer"></a><span data-ttu-id="8e066-124">若要加入資料檢視器</span><span class="sxs-lookup"><span data-stu-id="8e066-124">To add a data viewer</span></span>  
  
-   [<span data-ttu-id="8e066-125">將資料檢視器新增到資料流程</span><span class="sxs-lookup"><span data-stu-id="8e066-125">Add a Data Viewer to a Data Flow</span></span>](../add-a-data-viewer-to-a-data-flow.md)  
  
## <a name="row-counts"></a><span data-ttu-id="8e066-126">資料列計數</span><span class="sxs-lookup"><span data-stu-id="8e066-126">Row Counts</span></span>  
 <span data-ttu-id="8e066-127">經過某個路徑傳送的資料列數目，會顯示在「 **設計師」中** [資料流程] [!INCLUDE[ssIS](../../includes/ssis-md.md)] 索引標籤之設計介面上的該路徑旁邊。</span><span class="sxs-lookup"><span data-stu-id="8e066-127">The number of rows that have passed through a path is displayed on the design surface of the **Data Flow** tab in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer next to the path.</span></span> <span data-ttu-id="8e066-128">隨著資料不斷經由路徑移動，該數目會定期更新。</span><span class="sxs-lookup"><span data-stu-id="8e066-128">The number is updated periodically while the data moves through the path.</span></span>  
  
 <span data-ttu-id="8e066-129">您也可以將「資料列計數」轉換加入資料流程，以擷取變數中的最後資料列計數。</span><span class="sxs-lookup"><span data-stu-id="8e066-129">You can also add a Row Count transformation to the data flow to capture the final row count in a variable.</span></span> <span data-ttu-id="8e066-130">如需詳細資訊，請參閱 [Row Count Transformation](../data-flow/transformations/row-count-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="8e066-130">For more information, see [Row Count Transformation](../data-flow/transformations/row-count-transformation.md).</span></span>  
  
## <a name="progress-reporting"></a><span data-ttu-id="8e066-131">進度報表</span><span class="sxs-lookup"><span data-stu-id="8e066-131">Progress Reporting</span></span>  
 <span data-ttu-id="8e066-132">當您執行封裝時，「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」會在 **[資料流程]** 索引標籤的設計介面上，使用指示狀態的色彩顯示每個資料流程元件，以描述進度。</span><span class="sxs-lookup"><span data-stu-id="8e066-132">When you run a package, [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer depicts progress on the design surface of the **Data Flow** tab by displaying each data flow component in a color that indicates status.</span></span> <span data-ttu-id="8e066-133">當每個元件開始執行其工作時，會從無色彩變更為黃色，並在成功完成時變更為綠色，</span><span class="sxs-lookup"><span data-stu-id="8e066-133">When each component starts to perform its work, it changes from no color to yellow, and when it finishes successfully, it changes to green.</span></span> <span data-ttu-id="8e066-134">紅色則表示該元件已失敗。</span><span class="sxs-lookup"><span data-stu-id="8e066-134">A red color indicates that the component failed.</span></span>  
  
 <span data-ttu-id="8e066-135">下表描述色彩編碼。</span><span class="sxs-lookup"><span data-stu-id="8e066-135">The following table describes the color-coding.</span></span>  
  
|<span data-ttu-id="8e066-136">Color</span><span class="sxs-lookup"><span data-stu-id="8e066-136">Color</span></span>|<span data-ttu-id="8e066-137">描述</span><span class="sxs-lookup"><span data-stu-id="8e066-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e066-138">無色彩</span><span class="sxs-lookup"><span data-stu-id="8e066-138">No color</span></span>|<span data-ttu-id="8e066-139">正在等候由資料流程引擎呼叫。</span><span class="sxs-lookup"><span data-stu-id="8e066-139">Waiting to be called by the data flow engine.</span></span>|  
|<span data-ttu-id="8e066-140">黃色</span><span class="sxs-lookup"><span data-stu-id="8e066-140">Yellow</span></span>|<span data-ttu-id="8e066-141">正在執行轉換、擷取資料或載入資料。</span><span class="sxs-lookup"><span data-stu-id="8e066-141">Performing a transformation, extracting data, or loading data.</span></span>|  
|<span data-ttu-id="8e066-142">綠色</span><span class="sxs-lookup"><span data-stu-id="8e066-142">Green</span></span>|<span data-ttu-id="8e066-143">已成功執行。</span><span class="sxs-lookup"><span data-stu-id="8e066-143">Ran successfully.</span></span>|  
|<span data-ttu-id="8e066-144">紅色</span><span class="sxs-lookup"><span data-stu-id="8e066-144">red</span></span>|<span data-ttu-id="8e066-145">已執行但發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="8e066-145">Ran with errors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e066-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e066-146">See Also</span></span>  
 [<span data-ttu-id="8e066-147">套件開發的疑難排解工具</span><span class="sxs-lookup"><span data-stu-id="8e066-147">Troubleshooting Tools for Package Development</span></span>](troubleshooting-tools-for-package-development.md)  
  
  
