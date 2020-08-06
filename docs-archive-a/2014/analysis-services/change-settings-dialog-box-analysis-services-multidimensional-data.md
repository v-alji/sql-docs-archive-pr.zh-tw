---
title: '[變更設定] 對話方塊 (Analysis Services-多維度資料) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.batchsettingsdialog.f1
ms.assetid: 0041e042-d7ce-48f9-a690-a6dc65471ff3
author: minewiskan
ms.author: owend
ms.openlocfilehash: e2649195e3aff4e17d378e54c4b1d656361dfe3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593708"
---
# <a name="change-settings-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="b6bd6-102">變更設定對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="b6bd6-102">Change Settings Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="b6bd6-103">使用 **和** 中的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [變更設定] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 對話方塊，即可變更 **[處理]** 對話方塊所列出之物件的處理設定。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-103">Use the **Change Settings** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to change the settings that govern the processing of objects listed in the **Process** dialog box.</span></span> <span data-ttu-id="b6bd6-104">您可以在 **[處理]** 對話方塊中按一下 **[變更設定]** ，以顯示 **[變更設定]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-104">You can display the **Change Settings** dialog box by clicking **Change Settings** on the **Process** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6bd6-105"> 對於 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [處理] **對話方塊中列出的物件，此對話方塊所指定的設定會覆寫從** 資料庫繼承的預設值。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-105">Settings specified in this dialog box override default settings inherited from the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database for the objects listed in the **Process** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b6bd6-106">選項</span><span class="sxs-lookup"><span data-stu-id="b6bd6-106">Options</span></span>  
 <span data-ttu-id="b6bd6-107">**處理選項**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-107">**Processing options**</span></span>  
 <span data-ttu-id="b6bd6-108">使用此索引標籤即可針對處理作業，修改處理順序、回寫資料表以及受影響的物件等相關設定。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-108">Use this tab to modify settings related to the processing order, writeback table, and affected objects for the processing operation.</span></span> <span data-ttu-id="b6bd6-109">索引標籤包含下列選項：</span><span class="sxs-lookup"><span data-stu-id="b6bd6-109">The tab contains the following options:</span></span>  
  
 <span data-ttu-id="b6bd6-110">**Parallel**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-110">**Parallel**</span></span>  
 <span data-ttu-id="b6bd6-111">按一下以平行處理物件。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-111">Click to process the objects in parallel.</span></span>  
  
 <span data-ttu-id="b6bd6-112">**平行工作數上限**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-112">**Maximum parallel tasks**</span></span>  
 <span data-ttu-id="b6bd6-113">選取處理作業平行執行的工作數上限，或選擇 [讓伺服器決定]\*\*\*\*，即可讓 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 選取最佳的平行工作數。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-113">Select the maximum number of tasks to execute in parallel by the processing operation, or choose **Let the server decide** to allow [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to select an optimal number of parallel tasks.</span></span>  
  
 <span data-ttu-id="b6bd6-114">**循序**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-114">**Sequential**</span></span>  
 <span data-ttu-id="b6bd6-115">按一下即可循序處理物件。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-115">Click to process the objects sequentially.</span></span>  
  
 <span data-ttu-id="b6bd6-116">**交易模式**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-116">**Transaction mode**</span></span>  
 <span data-ttu-id="b6bd6-117">選擇循序處理物件時使用的交易模式：</span><span class="sxs-lookup"><span data-stu-id="b6bd6-117">Choose the transaction mode that is used when objects are processed in sequential order:</span></span>  
  
-   <span data-ttu-id="b6bd6-118">**[一筆交易]** 會在相同交易中處理所有物件。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-118">**One Transaction** processes all objects in the same transaction.</span></span>  
  
-   <span data-ttu-id="b6bd6-119">**[個別交易]** 會在個別交易中處理所有物件，包括相依物件。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-119">**Separate Transactions** processes all objects, including dependent objects, in separate transactions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6bd6-120"> 只有選取 **[循序]** 時才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-120">This option is enabled only if **Sequential** is selected.</span></span>  
  
 <span data-ttu-id="b6bd6-121">**回寫資料表選項**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-121">**Writeback table option**</span></span>  
 <span data-ttu-id="b6bd6-122">選擇用來管理回寫資料表的選項：</span><span class="sxs-lookup"><span data-stu-id="b6bd6-122">Choose the option used to manage a writeback table:</span></span>  
  
-   <span data-ttu-id="b6bd6-123">**[建立]** 會建立回寫資料表 (如果不存在)。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-123">**Create** creates a writeback table if it does not exist.</span></span> <span data-ttu-id="b6bd6-124">如果回寫資料表已存在，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-124">An error occurs if a writeback table already exists.</span></span>  
  
-   <span data-ttu-id="b6bd6-125">**[永遠建立]** 會建立不存在的回寫資料表，如果已存在，則會覆寫現有的回寫資料表。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-125">**Create always** creates a writeback table if it does not exist, or overwrites the existing writeback table if it does exist.</span></span>  
  
-   <span data-ttu-id="b6bd6-126">**[使用現有的]** 會使用現有的回寫資料表 (如果存在)。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-126">**Use existing** uses the existing writeback table if it exists.</span></span> <span data-ttu-id="b6bd6-127">如果回寫資料表不存在，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-127">An error occurs if a writeback table does not exist.</span></span>  
  
 <span data-ttu-id="b6bd6-128">**處理受影響的物件**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-128">**Process affected objects**</span></span>  
 <span data-ttu-id="b6bd6-129">選取即可包含並處理相依於處理作業所包含物件的物件。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-129">Select to include and process objects that depend on objects included in the processing operation.</span></span>  
  
 <span data-ttu-id="b6bd6-130">**維度索引鍵錯誤**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-130">**Dimension key errors**</span></span>  
 <span data-ttu-id="b6bd6-131">使用此索引標籤即可修改處理作業錯誤組態的相關設定。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-131">Use this tab to modify settings related to the error configuration for the processing operation.</span></span> <span data-ttu-id="b6bd6-132">索引標籤包含下列選項：</span><span class="sxs-lookup"><span data-stu-id="b6bd6-132">The tab contains the following options:</span></span>  
  
 <span data-ttu-id="b6bd6-133">**使用預設錯誤設定**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-133">**Use default error configuration**</span></span>  
 <span data-ttu-id="b6bd6-134">選取即可針對處理作業中的物件使用預設錯誤組態。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-134">Select to use the default error configuration for objects in the processing operation.</span></span>  
  
 <span data-ttu-id="b6bd6-135">**使用自訂錯誤組態**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-135">**Use custom error configuration**</span></span>  
 <span data-ttu-id="b6bd6-136">選取即可為處理作業中的物件定義錯誤組態。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-136">Select to define the error configuration for objects in the processing operation.</span></span>  
  
 <span data-ttu-id="b6bd6-137">**索引鍵錯誤動作**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-137">**Key error action**</span></span>  
 <span data-ttu-id="b6bd6-138">在處理期間發現無法查閱的新索引鍵時，請選擇下列其中一個發生的動作：</span><span class="sxs-lookup"><span data-stu-id="b6bd6-138">Choose one of the following actions that occur when a new key is encountered during processing that cannot be looked up:</span></span>  
  
-   <span data-ttu-id="b6bd6-139">**[轉換為未知]** 會將該記錄的資訊彙總至未知成員。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-139">**Convert to unknown** aggregates the information for the record into the unknown member.</span></span>  
  
-   <span data-ttu-id="b6bd6-140">**[捨棄記錄]** 會將該記錄的資訊排除在物件的處理範圍以外。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-140">**Discard record** excludes the information for the record from being processed with the object.</span></span>  
  
 <span data-ttu-id="b6bd6-141">**忽略錯誤計數**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-141">**Ignore errors count**</span></span>  
 <span data-ttu-id="b6bd6-142">按一下即可忽略處理時發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-142">Click to ignore any errors that occur when processing.</span></span>  
  
 <span data-ttu-id="b6bd6-143">**發生錯誤時停止**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-143">**Stop on error**</span></span>  
 <span data-ttu-id="b6bd6-144">按一下即可在錯誤發生時停止處理。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-144">Click to stop processing when errors occur.</span></span> <span data-ttu-id="b6bd6-145">此選項會啟用 **[錯誤數目]** 和 **[發生錯誤時的動作]** 選項。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-145">This option enables the **Number of errors** and the **On error action** options.</span></span>  
  
 <span data-ttu-id="b6bd6-146">**錯誤數目**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-146">**Number of errors**</span></span>  
 <span data-ttu-id="b6bd6-147">輸入處理停止之前所忽略的錯誤數目。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-147">Type the number of errors that are ignored before processing stops.</span></span>  
  
 <span data-ttu-id="b6bd6-148">**發生錯誤時要執行的動作**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-148">**On error action**</span></span>  
 <span data-ttu-id="b6bd6-149">當錯誤數目超出 [錯誤數目]\*\*\*\* 中的值時，請選擇採取下列動作之一：</span><span class="sxs-lookup"><span data-stu-id="b6bd6-149">Choose one of the following actions to be taken when the number of errors exceeds the value in **Number of errors**:</span></span>  
  
-   <span data-ttu-id="b6bd6-150">**[停止處理]** 會結束處理作業。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-150">**Stop processing** ends the processing operation.</span></span>  
  
-   <span data-ttu-id="b6bd6-151">**[停止記錄]** 會停止記錄錯誤，但仍繼續處理作業。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-151">**Stop logging** stops logging errors, but continues the processing operation.</span></span>  
  
 <span data-ttu-id="b6bd6-152">**找不到索引鍵**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-152">**Key not found**</span></span>  
 <span data-ttu-id="b6bd6-153">當處理物件時找不到索引鍵時，請指定採取下列動作之一：</span><span class="sxs-lookup"><span data-stu-id="b6bd6-153">Specify one of the following actions to be taken when a key is not found when an object is processed:</span></span>  
  
-   <span data-ttu-id="b6bd6-154">**[忽略錯誤]** 會忽略錯誤。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-154">**Ignore error** ignores the error.</span></span>  
  
-   <span data-ttu-id="b6bd6-155">**[報告並繼續]** 會報告錯誤並繼續處理作業。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-155">**Report and continue** reports the error and continues the processing operation.</span></span>  
  
-   <span data-ttu-id="b6bd6-156">**[報告並停止]** 會報告錯誤並停止處理作業。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-156">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="b6bd6-157">**重複的索引鍵**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-157">**Duplicate key**</span></span>  
 <span data-ttu-id="b6bd6-158">處理物件時如果找到重複索引鍵，請指定採取下列動作之一：</span><span class="sxs-lookup"><span data-stu-id="b6bd6-158">Specify one of the following actions to be taken if a duplicate key is found when an object is processed:</span></span>  
  
-   <span data-ttu-id="b6bd6-159">**[忽略錯誤]** 會忽略錯誤。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-159">**Ignore error** ignores the error.</span></span>  
  
-   <span data-ttu-id="b6bd6-160">**[報告並繼續]** 會報告錯誤並繼續處理作業。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-160">**Report and continue** reports the error and continues the processing operation.</span></span>  
  
-   <span data-ttu-id="b6bd6-161">**[報告並停止]** 會報告錯誤並停止處理作業。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-161">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="b6bd6-162">**Null 索引鍵已轉換為未知**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-162">**Null key converted to unknown**</span></span>  
 <span data-ttu-id="b6bd6-163">指定處理物件時，若有 Null 成員索引鍵加入未知成員中，要採取下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="b6bd6-163">Specify one of the following actions to be taken when a null member key is added to the unknown member when an object is processed:</span></span>  
  
-   <span data-ttu-id="b6bd6-164">**[忽略錯誤]** 會忽略錯誤。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-164">**Ignore error** ignores the error.</span></span>  
  
-   <span data-ttu-id="b6bd6-165">**[報告並繼續]** 會報告錯誤並繼續處理作業。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-165">**Report and continue** reports the error and continues the processing operation.</span></span>  
  
-   <span data-ttu-id="b6bd6-166">**[報告並停止]** 會報告錯誤並停止處理作業。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-166">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="b6bd6-167">**不允許 Null 索引鍵**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-167">**Null key not allowed**</span></span>  
 <span data-ttu-id="b6bd6-168">指定處理物件時，若在不允許 Null 索引鍵的情況下找到 Null 索引鍵，要採取下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="b6bd6-168">Specify one of the following actions to be taken when a null key is found, but not allowed, when an object is processed:</span></span>  
  
-   <span data-ttu-id="b6bd6-169">**[忽略錯誤]** 會忽略錯誤。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-169">**Ignore error** ignores the error.</span></span>  
  
-   <span data-ttu-id="b6bd6-170">**[報告並繼續]** 會報告錯誤並繼續處理作業。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-170">**Report and continue** reports the error and continues the processing operation.</span></span>  
  
-   <span data-ttu-id="b6bd6-171">**[報告並停止]** 會報告錯誤並停止處理作業。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-171">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="b6bd6-172">**錯誤記錄路徑**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-172">**Error log path**</span></span>  
 <span data-ttu-id="b6bd6-173">輸入錯誤記錄檔的完整路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-173">Type the full path and file name for the error log file.</span></span>  
  
 <span data-ttu-id="b6bd6-174">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-174">**Browse**</span></span>  
 <span data-ttu-id="b6bd6-175">按一下即可開啟 [開啟]\*\*\*\* 對話方塊，並選取錯誤記錄檔的完整路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-175">Click to open the **Open** dialog box and select the full path and file name for the error log file.</span></span>  
  
 <span data-ttu-id="b6bd6-176">**處理受影響的物件**</span><span class="sxs-lookup"><span data-stu-id="b6bd6-176">**Process affected objects**</span></span>  
 <span data-ttu-id="b6bd6-177">按一下即可處理相依於 [處理]\*\*\*\* 對話方塊中所選取物件的物件。</span><span class="sxs-lookup"><span data-stu-id="b6bd6-177">Click to process the objects that have a dependency on the objects selected in the **Process** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6bd6-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6bd6-178">See Also</span></span>  
 <span data-ttu-id="b6bd6-179">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="b6bd6-179">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="b6bd6-180">進程對話方塊 &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="b6bd6-180">Process Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
