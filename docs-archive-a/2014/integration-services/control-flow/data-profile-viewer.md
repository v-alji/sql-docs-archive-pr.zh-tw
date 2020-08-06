---
title: 資料設定檔檢視器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profile Viewer [Integration Services]
- Data Profiling task [Integration Services], output viewer
ms.assetid: b9043428-ce26-45bb-910c-588d07579565
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e82aae19525625d966bdd01334eca07a1c4c68f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596853"
---
# <a name="data-profile-viewer"></a><span data-ttu-id="4b61b-102">資料設定檔檢視器</span><span class="sxs-lookup"><span data-stu-id="4b61b-102">Data Profile Viewer</span></span>
  <span data-ttu-id="4b61b-103">檢視和分析資料設定檔是資料分析程序中的下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="4b61b-103">Viewing and analyzing the data profiles is the next step in the data profiling process.</span></span> <span data-ttu-id="4b61b-104">您可以在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝內部執行「資料分析」工作並計算資料設定檔後，檢視這些設定檔。</span><span class="sxs-lookup"><span data-stu-id="4b61b-104">You can view these profiles after you have run the Data Profiling task inside an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package and computed the data profiles.</span></span> <span data-ttu-id="4b61b-105">如需如何設定和執行「資料分析」工作的詳細資訊，請參閱 [資料分析工作的設定](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="4b61b-105">For more information about how to set up and run the Data Profiling tasks, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4b61b-106">輸出檔可能包含您資料庫的相關敏感性資料，以及資料庫所包含的資料。</span><span class="sxs-lookup"><span data-stu-id="4b61b-106">The output file might contain sensitive data about your database and the data that database contains.</span></span> <span data-ttu-id="4b61b-107">如需如何讓這個檔案更安全的相關建議，請參閱 [對封裝使用之檔案的存取權](../access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="4b61b-107">For suggestions on how to make this file more secure, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
## <a name="data-profiles"></a><span data-ttu-id="4b61b-108">資料設定檔</span><span class="sxs-lookup"><span data-stu-id="4b61b-108">Data Profiles</span></span>  
 <span data-ttu-id="4b61b-109">若要檢視資料設定檔，您可以設定「資料分析」工作，將其輸出傳送到檔案，然後使用獨立的「資料設定檔檢視器」即可。</span><span class="sxs-lookup"><span data-stu-id="4b61b-109">To view the data profiles, you configure the Data Profiling task to send its output to a file, and then you use the stand-alone Data Profile Viewer.</span></span> <span data-ttu-id="4b61b-110">若要開啟資料設定檔檢視器，請執行下列其中一項操作。</span><span class="sxs-lookup"><span data-stu-id="4b61b-110">To open the Data Profile Viewer, do one of the following.</span></span>  
  
-   <span data-ttu-id="4b61b-111">以滑鼠右鍵按一下 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中的 [資料分析] 工作，然後按一下 [編輯]。</span><span class="sxs-lookup"><span data-stu-id="4b61b-111">Right-click the **Data Profiling** task in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, and then click **Edit**.</span></span> <span data-ttu-id="4b61b-112">在 [資料分析工作編輯器] 的 [一般] 頁面上按一下 [開啟設定檔檢視器]。</span><span class="sxs-lookup"><span data-stu-id="4b61b-112">Click **Open Profile Viewer** on the **General** page of the **Data Profiling Task Editor**.</span></span>  
  
-   <span data-ttu-id="4b61b-113">在 *\<drive>* :\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn 資料夾中，執行 DataProfileViewer.exe。</span><span class="sxs-lookup"><span data-stu-id="4b61b-113">In the folder, *\<drive>*:\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn, run DataProfileViewer.exe.</span></span>  
  
 <span data-ttu-id="4b61b-114">此檢視器可使用多個窗格，顯示您所要求與計算之結果的設定檔以及選擇性的詳細資料與向下鑽研能力：</span><span class="sxs-lookup"><span data-stu-id="4b61b-114">The viewer uses multiple panes to display the profiles that you requested and the computed results, with optional details and drilldown capability:</span></span>  
  
 <span data-ttu-id="4b61b-115">**設定檔** 窗格</span><span class="sxs-lookup"><span data-stu-id="4b61b-115">**Profiles** pane</span></span>  
 <span data-ttu-id="4b61b-116">[設定檔]  窗格會顯示「資料設定檔」工作所要求的設定檔。</span><span class="sxs-lookup"><span data-stu-id="4b61b-116">The **Profiles** pane displays the profiles that were requested in the Data Profile task.</span></span> <span data-ttu-id="4b61b-117">若要檢視設定檔的計算結果，請在 [設定檔]  窗格中選取設定檔，結果就會顯示在檢視器的其他窗格中。</span><span class="sxs-lookup"><span data-stu-id="4b61b-117">To view the computed results for the profile, select the profile in the **Profiles** pane and the results will appear in the other panes of the viewer.</span></span>  
  
 <span data-ttu-id="4b61b-118">**結果** 窗格</span><span class="sxs-lookup"><span data-stu-id="4b61b-118">**Results** pane</span></span>  
 <span data-ttu-id="4b61b-119">[結果]  窗格會使用單一資料列來摘要說明設定檔的計算結果。</span><span class="sxs-lookup"><span data-stu-id="4b61b-119">The **Results** pane uses a single row to summarize the computed results of the profile.</span></span> <span data-ttu-id="4b61b-120">例如，如果您要求 [資料行長度散發設定檔]  ，這個資料列會包含最小和最大長度，以及資料列計數。</span><span class="sxs-lookup"><span data-stu-id="4b61b-120">For example, if you request a **Column Length Distribution Profile**, this row includes the minimum and maximum length, and the row count.</span></span> <span data-ttu-id="4b61b-121">對於大部分的設定檔，您可以在 [結果]  窗格中選取這個資料列，以便在選用的 [詳細資料]  窗格中查看其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4b61b-121">For most profiles, you can select this row in the **Results** pane to see additional detail in the optional **Details** pane.</span></span>  
  
 <span data-ttu-id="4b61b-122">**詳細資料** 窗格</span><span class="sxs-lookup"><span data-stu-id="4b61b-122">**Details** pane</span></span>  
 <span data-ttu-id="4b61b-123">對於大部分的設定檔類型，[詳細資料]  窗格會顯示在 [結果]  窗格中選取之設定檔結果的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4b61b-123">For most profile types, the **Details** pane displays additional information about the profile results selected in the **Results** pane.</span></span> <span data-ttu-id="4b61b-124">例如，如果您要求 [資料行長度散發設定檔]  ，[詳細資料]  窗格會顯示所找到的每個資料行長度。</span><span class="sxs-lookup"><span data-stu-id="4b61b-124">For example, if you request a **Column Length Distribution Profile**, the **Details** pane displays each column length that was found.</span></span> <span data-ttu-id="4b61b-125">此窗格也會顯示資料行值中，具有該資料行長度之資料列的數目與百分比。</span><span class="sxs-lookup"><span data-stu-id="4b61b-125">The pane also displays the number and percentage of rows in which the column value has that column length.</span></span>  
  
 <span data-ttu-id="4b61b-126">對於根據一個以上的資料行所計算的三種設定檔類型 ([候選索引鍵]、[功能相依性] 與 [值包含])，[詳細資料]  窗格會顯示預期關聯性的違規。</span><span class="sxs-lookup"><span data-stu-id="4b61b-126">For the three profile types that are computed against more than one column (Candidate Key, Functional Dependency, and Value Inclusion), the **Details** pane displays violations of the expected relationship.</span></span> <span data-ttu-id="4b61b-127">例如，如果您要求 [候選索引鍵設定檔]，[詳細資料] 窗格會顯示違反候選索引鍵唯一性的重複值。</span><span class="sxs-lookup"><span data-stu-id="4b61b-127">For example, if you request a Candidate Key Profile, the Details pane displays duplicate values that violate the uniqueness of the candidate key.</span></span>  
  
 <span data-ttu-id="4b61b-128">如果可以使用計算設定檔所使用的資料來源，您可以在 [詳細資料]  窗格中按兩下資料列，以便在 [向下鑽研]  窗格中查看相符的資料列。</span><span class="sxs-lookup"><span data-stu-id="4b61b-128">If the data source that is used to compute the profile is available, you can double-click a row in the **Details** pane to see the matching rows of data in the **Drilldown** pane.</span></span>  
  
 <span data-ttu-id="4b61b-129">**向下鑽研** 窗格</span><span class="sxs-lookup"><span data-stu-id="4b61b-129">**Drilldown** pane</span></span>  
 <span data-ttu-id="4b61b-130">當以下條件成立時，您可以在 [詳細資料]  窗格中按兩下資料列，在 [向下鑽研]  窗格中查看相符的資料列：</span><span class="sxs-lookup"><span data-stu-id="4b61b-130">You can double-click a row in the **Details** pane to see the matching rows of data in the **Drilldown** pane when the following conditions are true:</span></span>  
  
-   <span data-ttu-id="4b61b-131">可以使用用來計算設定檔的資料來源。</span><span class="sxs-lookup"><span data-stu-id="4b61b-131">The data source that is used to compute the profile is available.</span></span>  
  
-   <span data-ttu-id="4b61b-132">您具有檢視資料的權限。</span><span class="sxs-lookup"><span data-stu-id="4b61b-132">You have permission to view the data.</span></span>  
  
 <span data-ttu-id="4b61b-133">為了連接到來源資料庫完成向下鑽研要求，資料設定檔檢視器會使用 Windows 驗證及目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="4b61b-133">To connect to the source database for a drilldown request, the Data Profile Viewer uses Windows Authentication and the credentials of the current user.</span></span> <span data-ttu-id="4b61b-134">資料設定檔檢視器不會使用儲存在執行「資料分析」工作之封裝內的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="4b61b-134">The Data Profile Viewer does not use the connection information that is stored in the package that ran the Data Profiling task.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4b61b-135">資料設定檔檢視器所提供的向下鑽研功能會傳送即時查詢給原始資料來源。</span><span class="sxs-lookup"><span data-stu-id="4b61b-135">The drilldown capability that is available in the Data Profile Viewer sends live queries to the original data source.</span></span> <span data-ttu-id="4b61b-136">這些查詢對於伺服器的效能可能會有負面影響。</span><span class="sxs-lookup"><span data-stu-id="4b61b-136">These queries may have a negative impact on the performance of the server.</span></span>  
>   
>  <span data-ttu-id="4b61b-137">如果您從不是最近建立的輸出檔向下切入，則向下鑽研查詢傳回的資料列集可能與計算原始輸出的資料列集不同。</span><span class="sxs-lookup"><span data-stu-id="4b61b-137">If you drill down from an output file that was not created recently, the drilldown queries might return a different set of rows than those on which the original output was calculated.</span></span>  
  
 <span data-ttu-id="4b61b-138">如需資料設定檔檢視器之使用者介面的詳細資訊，請參閱 [資料設定檔檢視器 F1 說明](../data-profile-viewer-f1-help.md)。</span><span class="sxs-lookup"><span data-stu-id="4b61b-138">For more information about the user interface of the Data Profile Viewer, see [Data Profile Viewer F1 Help](../data-profile-viewer-f1-help.md).</span></span>  
  
  
