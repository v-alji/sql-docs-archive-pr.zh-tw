---
title: 資料分析工作編輯器 (一般頁面) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataprofilingtask.general.f1
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: eec15906-d757-4079-b2f6-aca4e52b3b4c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4cfcdf472f817d3dd688a5f867ac74d46835ab91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597266"
---
# <a name="data-profiling-task-editor-general-page"></a><span data-ttu-id="80e0c-102">資料分析工作編輯器 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="80e0c-102">Data Profiling Task Editor (General Page)</span></span>
  <span data-ttu-id="80e0c-103">您可以使用 [資料分析工作編輯器] 的 [一般] 頁面來設定下列選項：</span><span class="sxs-lookup"><span data-stu-id="80e0c-103">Use the **General** page of the **Data Profiling Task Editor** to configure the following options:</span></span>  
  
-   <span data-ttu-id="80e0c-104">指定設定檔輸出的目的地。</span><span class="sxs-lookup"><span data-stu-id="80e0c-104">Specify the destination for the profile output.</span></span>  
  
-   <span data-ttu-id="80e0c-105">使用預設設定來簡化分析單一資料表或檢視表的工作。</span><span class="sxs-lookup"><span data-stu-id="80e0c-105">Use the default settings to simplify the task of profiling a single table or view.</span></span>  
  
 <span data-ttu-id="80e0c-106">如需如何使用資料分析工作的詳細資訊，請參閱 [資料分析工作的設定](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="80e0c-106">For more information about how to use the Data Profiling task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="80e0c-107">如需如何使用資料設定檔檢視器來分析資料分析工作輸出的詳細資訊，請參閱 [資料設定檔檢視器](data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="80e0c-107">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
 <span data-ttu-id="80e0c-108">**開啟資料分析工作編輯器的一般頁面**</span><span class="sxs-lookup"><span data-stu-id="80e0c-108">**To open the General page of the Data Profiling Task Editor**</span></span>  
  
1.  <span data-ttu-id="80e0c-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟具有資料分析工作的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="80e0c-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that has the Data Profiling task.</span></span>  
  
2.  <span data-ttu-id="80e0c-110">在 [控制流程]  索引標籤中，按兩下資料分析工作。</span><span class="sxs-lookup"><span data-stu-id="80e0c-110">On the **Control Flow** tab, double-click the Data Profiling task.</span></span>  
  
3.  <span data-ttu-id="80e0c-111">在 [資料分析工作編輯器]  中，按一下 [一般]  。</span><span class="sxs-lookup"><span data-stu-id="80e0c-111">In the **Data Profiling Task Editor**, click **General**.</span></span>  
  
## <a name="data-profiling-options"></a><span data-ttu-id="80e0c-112">資料分析選項</span><span class="sxs-lookup"><span data-stu-id="80e0c-112">Data Profiling Options</span></span>  
 <span data-ttu-id="80e0c-113">**逾時**</span><span class="sxs-lookup"><span data-stu-id="80e0c-113">**Timeout**</span></span>  
 <span data-ttu-id="80e0c-114">指定資料分析工作應該逾時並停止執行之前經過的秒數。</span><span class="sxs-lookup"><span data-stu-id="80e0c-114">Specify the number of seconds after which the Data Profiling task should timeout and stop running.</span></span> <span data-ttu-id="80e0c-115">預設值為 0，表示沒有逾時。</span><span class="sxs-lookup"><span data-stu-id="80e0c-115">The default value is 0, which indicates no timeout.</span></span>  
  
## <a name="destination-options"></a><span data-ttu-id="80e0c-116">目的地選項</span><span class="sxs-lookup"><span data-stu-id="80e0c-116">Destination Options</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="80e0c-117">輸出檔可能包含您資料庫的相關敏感性資料，以及資料庫所包含的資料。</span><span class="sxs-lookup"><span data-stu-id="80e0c-117">The output file might contain sensitive data about your database and the data that database contains.</span></span> <span data-ttu-id="80e0c-118">如需如何讓這個檔案更安全的相關建議，請參閱 [對封裝使用之檔案的存取權](../access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="80e0c-118">For suggestions about how to make this file more secure, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
 <span data-ttu-id="80e0c-119">**DestinationType**</span><span class="sxs-lookup"><span data-stu-id="80e0c-119">**DestinationType**</span></span>  
 <span data-ttu-id="80e0c-120">指定要將資料設定檔輸出儲存至檔案或變數：</span><span class="sxs-lookup"><span data-stu-id="80e0c-120">Specify whether to save the data profile output to a file or a variable:</span></span>  
  
|<span data-ttu-id="80e0c-121">值</span><span class="sxs-lookup"><span data-stu-id="80e0c-121">Value</span></span>|<span data-ttu-id="80e0c-122">描述</span><span class="sxs-lookup"><span data-stu-id="80e0c-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="80e0c-123">**FileConnection**</span><span class="sxs-lookup"><span data-stu-id="80e0c-123">**FileConnection**</span></span>|<span data-ttu-id="80e0c-124">將設定檔輸出儲存至檔案連線管理員中指定之位置的檔案。</span><span class="sxs-lookup"><span data-stu-id="80e0c-124">Save the profile output to a file in the location that is specified in a File connection manager.</span></span><br /><br /> <span data-ttu-id="80e0c-125">注意：您可以在 [目的地]  選項中指定要使用的檔案連線管理員。</span><span class="sxs-lookup"><span data-stu-id="80e0c-125">Note: You specify which File connection manager to use in the **Destination** option.</span></span>|  
|<span data-ttu-id="80e0c-126">**變數**</span><span class="sxs-lookup"><span data-stu-id="80e0c-126">**Variable**</span></span>|<span data-ttu-id="80e0c-127">將設定檔輸出儲存至封裝變數。</span><span class="sxs-lookup"><span data-stu-id="80e0c-127">Save the profile output to a package variable.</span></span><br /><br /> <span data-ttu-id="80e0c-128">注意：您可以在 [目的地]  選項中指定要使用的封裝變數。</span><span class="sxs-lookup"><span data-stu-id="80e0c-128">Note: You specify which package variable to use in the **Destination** option.</span></span>|  
  
 <span data-ttu-id="80e0c-129">**目的地**</span><span class="sxs-lookup"><span data-stu-id="80e0c-129">**Destination**</span></span>  
 <span data-ttu-id="80e0c-130">指定哪一個檔案連線管理員或封裝變數包含資料設定檔輸出：</span><span class="sxs-lookup"><span data-stu-id="80e0c-130">Specify which File connection manager or package variable contains the data profile output:</span></span>  
  
-   <span data-ttu-id="80e0c-131">如果 [DestinationType]  選項設定為 [FileConnection]  ，[目的地]  選項就會顯示可用的檔案連線管理員。</span><span class="sxs-lookup"><span data-stu-id="80e0c-131">If the **DestinationType** option is set to **FileConnection**, the **Destination** option displays the available File connection managers.</span></span> <span data-ttu-id="80e0c-132">您可選取其中一個連線管理員，或選取 \<New File connection> 來建立新的檔案連線管理員。</span><span class="sxs-lookup"><span data-stu-id="80e0c-132">Select one of these connection managers, or select \<New File connection> to create a new File connection manager.</span></span>  
  
-   <span data-ttu-id="80e0c-133">如果 [DestinationType]  選項設定為 [變數]  ，[目的地]  選項就會在 [目的地]  清單中顯示可用的封裝變數。</span><span class="sxs-lookup"><span data-stu-id="80e0c-133">If the **DestinationType** option is set to **Variable**, the **Destination** option displays the available package variables in the **Destination** list.</span></span> <span data-ttu-id="80e0c-134">您可選取其中一個變數，或選取 \<New Variable> 來建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="80e0c-134">Select one of these variables, or select \<New Variable> to create a new variable.</span></span>  
  
 <span data-ttu-id="80e0c-135">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="80e0c-135">**OverwriteDestination**</span></span>  
 <span data-ttu-id="80e0c-136">指定是否要覆寫輸出檔 (如果它已經存在的話)。</span><span class="sxs-lookup"><span data-stu-id="80e0c-136">Specify whether to overwrite the output file if it already exists.</span></span> <span data-ttu-id="80e0c-137">預設值為 **[False]** 。</span><span class="sxs-lookup"><span data-stu-id="80e0c-137">The default value is **False**.</span></span> <span data-ttu-id="80e0c-138">只有當 [DestinationType] 選項設定為 [FileConnection] 時，系統才會使用這個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="80e0c-138">The value of this property is used only when the DestinationType option is set to FileConnection.</span></span> <span data-ttu-id="80e0c-139">當 [DestinationType] 選項設定為 [變數] 時，此工作永遠會覆寫變數的上一個值。</span><span class="sxs-lookup"><span data-stu-id="80e0c-139">When the DestinationType option is set to Variable, the task always overwrites the previous value of the variable.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="80e0c-140">如果您嘗試執行資料分析工作一次以上，但不變更輸出檔名稱或將 **OverwriteDestination** 屬性的值變更為 **True**，此工作便會失敗，並顯示輸出檔已經存在的訊息。</span><span class="sxs-lookup"><span data-stu-id="80e0c-140">If you try to run the Data Profiling task more than once without changing the output file name or changing the value of the **OverwriteDestination** property to **True**, the task fails with the message that the output file already exists.</span></span>  
  
## <a name="other-options"></a><span data-ttu-id="80e0c-141">其他選項</span><span class="sxs-lookup"><span data-stu-id="80e0c-141">Other Options</span></span>  
 <span data-ttu-id="80e0c-142">**快速分析**</span><span class="sxs-lookup"><span data-stu-id="80e0c-142">**Quick Profile**</span></span>  
 <span data-ttu-id="80e0c-143">顯示 [單一資料表快速分析表單]  。</span><span class="sxs-lookup"><span data-stu-id="80e0c-143">Display the **Single Table Quick Profile Form**.</span></span> <span data-ttu-id="80e0c-144">這個表單會簡化使用預設設定來分析單一資料表或檢視表的工作。</span><span class="sxs-lookup"><span data-stu-id="80e0c-144">This form simplifies the task of profiling a single table or view by using default settings.</span></span> <span data-ttu-id="80e0c-145">如需詳細資訊，請參閱 [單一資料表快速分析表單 &#40;資料分析工作&#41;](single-table-quick-profile-form-data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="80e0c-145">For more information, see [Single Table Quick Profile Form &#40;Data Profiling Task&#41;](single-table-quick-profile-form-data-profiling-task.md).</span></span>  
  
 <span data-ttu-id="80e0c-146">**開啟設定檔檢視器**</span><span class="sxs-lookup"><span data-stu-id="80e0c-146">**Open Profile Viewer**</span></span>  
 <span data-ttu-id="80e0c-147">開啟資料設定檔檢視器。</span><span class="sxs-lookup"><span data-stu-id="80e0c-147">Opens the Data Profile Viewer.</span></span> <span data-ttu-id="80e0c-148">獨立資料設定檔檢視器會顯示資料分析工作的資料設定檔輸出。</span><span class="sxs-lookup"><span data-stu-id="80e0c-148">The stand-alone Data Profile Viewer displays data profile output from the Data Profiling task.</span></span> <span data-ttu-id="80e0c-149">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝內部執行資料分析工作並計算資料設定檔後，您可以檢視資料設定檔輸出。</span><span class="sxs-lookup"><span data-stu-id="80e0c-149">You can view the data profile output after you have run the Data Profiling task inside the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package and computed the data profiles.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="80e0c-150">您也可以藉由在 *\<drive>* :\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn 資料夾中執行 DataProfileViewer.exe 的方式來開啟資料設定檔檢視器。</span><span class="sxs-lookup"><span data-stu-id="80e0c-150">You can also open the Data Profile Viewer by running the DataProfileViewer.exe in the folder, *\<drive>*:\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e0c-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80e0c-151">See Also</span></span>  
 <span data-ttu-id="80e0c-152">[單一資料表快速分析表單 &#40;資料分析工作&#41;](single-table-quick-profile-form-data-profiling-task.md) </span><span class="sxs-lookup"><span data-stu-id="80e0c-152">[Single Table Quick Profile Form &#40;Data Profiling Task&#41;](single-table-quick-profile-form-data-profiling-task.md) </span></span>  
 [<span data-ttu-id="80e0c-153">資料分析工作編輯器 &#40;設定檔要求頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="80e0c-153">Data Profiling Task Editor &#40;Profile Requests Page&#41;</span></span>](data-profiling-task-editor-profile-requests-page.md)  
  
  
