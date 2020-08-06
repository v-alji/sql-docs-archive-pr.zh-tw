---
title: 錯誤設定 ([)  (的 [採礦結構] 對話方塊中 Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.miningstructuredialog.general.f1
ms.assetid: d9aa028b-bad9-49c7-a81c-c2150e4dd481
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5eb41da36400271a9b058ecf275d26bd22d3ee53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607129"
---
# <a name="error-configuration-mining-structure-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="37e6c-102">錯誤組態 (採礦結構對話方塊) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="37e6c-102">Error Configuration (Mining Structure Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="37e6c-103">在 **SQL Server Management Studio** 中，使用 **[採礦結構屬性]** 對話方塊的 **[錯誤組態]** 頁面，即可設定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫中採礦結構的錯誤組態屬性。</span><span class="sxs-lookup"><span data-stu-id="37e6c-103">Use the **Error Configuration** page of the **Mining Structure Properties** dialog box in **SQL Server Management Studio** to set the error configuration properties of a mining structure in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
## <a name="options"></a><span data-ttu-id="37e6c-104">選項</span><span class="sxs-lookup"><span data-stu-id="37e6c-104">Options</span></span>  
 <span data-ttu-id="37e6c-105">**使用預設錯誤設定**</span><span class="sxs-lookup"><span data-stu-id="37e6c-105">**Use default error configuration**</span></span>  
 <span data-ttu-id="37e6c-106">選取即可針對處理作業中的物件使用預設錯誤組態。</span><span class="sxs-lookup"><span data-stu-id="37e6c-106">Select to use the default error configuration for objects in the processing operation.</span></span>  
  
 <span data-ttu-id="37e6c-107">**索引鍵錯誤動作**</span><span class="sxs-lookup"><span data-stu-id="37e6c-107">**Key error action**</span></span>  
 <span data-ttu-id="37e6c-108">在處理期間發現無法查閱的新索引鍵時，請選擇下列其中一個發生的動作：</span><span class="sxs-lookup"><span data-stu-id="37e6c-108">Choose one of the following actions that occur when a new key is encountered during processing that cannot be looked up:</span></span>  
  
-   <span data-ttu-id="37e6c-109">**[轉換為未知]** 會將該記錄的資訊彙總至未知成員。</span><span class="sxs-lookup"><span data-stu-id="37e6c-109">**Convert to unknown** aggregates the information for the record into the unknown member.</span></span>  
  
-   <span data-ttu-id="37e6c-110">**[捨棄記錄]** 會將該記錄的資訊排除在物件的處理範圍以外。</span><span class="sxs-lookup"><span data-stu-id="37e6c-110">**Discard record** excludes the information for the record from being processed with the object.</span></span>  
  
 <span data-ttu-id="37e6c-111">**忽略錯誤計數**</span><span class="sxs-lookup"><span data-stu-id="37e6c-111">**Ignore errors count**</span></span>  
 <span data-ttu-id="37e6c-112">按一下即可忽略處理時發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="37e6c-112">Click to ignore any errors that occur when processing.</span></span>  
  
 <span data-ttu-id="37e6c-113">**發生錯誤時停止**</span><span class="sxs-lookup"><span data-stu-id="37e6c-113">**Stop on error**</span></span>  
 <span data-ttu-id="37e6c-114">按一下即可在錯誤發生時停止處理。</span><span class="sxs-lookup"><span data-stu-id="37e6c-114">Click to stop processing when errors occur.</span></span> <span data-ttu-id="37e6c-115">此選項會啟用 **[錯誤數目]** 和 **[發生錯誤時的動作]** 選項。</span><span class="sxs-lookup"><span data-stu-id="37e6c-115">This option enables the **Number of errors** and the **On error action** options.</span></span>  
  
 <span data-ttu-id="37e6c-116">**錯誤數目**</span><span class="sxs-lookup"><span data-stu-id="37e6c-116">**Number of errors**</span></span>  
 <span data-ttu-id="37e6c-117">輸入處理停止之前所忽略的錯誤數目。</span><span class="sxs-lookup"><span data-stu-id="37e6c-117">Type the number of errors that are ignored before processing stops.</span></span>  
  
 <span data-ttu-id="37e6c-118">**發生錯誤時要執行的動作**</span><span class="sxs-lookup"><span data-stu-id="37e6c-118">**On error action**</span></span>  
 <span data-ttu-id="37e6c-119">當錯誤數目超出 [錯誤數目]\*\*\*\* 中的值時，請選擇採取下列動作之一：</span><span class="sxs-lookup"><span data-stu-id="37e6c-119">Choose one of the following actions to be taken when the number of errors exceeds the value in **Number of errors**:</span></span>  
  
-   <span data-ttu-id="37e6c-120">**[停止處理]** 會結束處理作業。</span><span class="sxs-lookup"><span data-stu-id="37e6c-120">**Stop processing** ends the processing operation.</span></span>  
  
-   <span data-ttu-id="37e6c-121">**[停止記錄]** 會停止記錄錯誤，但仍繼續處理作業。</span><span class="sxs-lookup"><span data-stu-id="37e6c-121">**Stop logging** stops logging errors, but continues the processing operation.</span></span>  
  
 <span data-ttu-id="37e6c-122">**找不到索引鍵**</span><span class="sxs-lookup"><span data-stu-id="37e6c-122">**Key not found**</span></span>  
 <span data-ttu-id="37e6c-123">當處理物件時找不到索引鍵時，請指定採取下列動作之一：</span><span class="sxs-lookup"><span data-stu-id="37e6c-123">Specify one of the following actions to be taken when a key is not found when an object is processed:</span></span>  
  
-   <span data-ttu-id="37e6c-124">**忽略錯誤**忽略錯誤</span><span class="sxs-lookup"><span data-stu-id="37e6c-124">**Ignore error** ignores the error</span></span>  
  
-   <span data-ttu-id="37e6c-125">[**報告並繼續**] 會報告錯誤，並繼續處理作業</span><span class="sxs-lookup"><span data-stu-id="37e6c-125">**Report and continue** reports the error and continues the processing operation</span></span>  
  
-   <span data-ttu-id="37e6c-126">**[報告並停止]** 會報告錯誤並停止處理作業。</span><span class="sxs-lookup"><span data-stu-id="37e6c-126">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="37e6c-127">**重複的索引鍵**</span><span class="sxs-lookup"><span data-stu-id="37e6c-127">**Duplicate key**</span></span>  
 <span data-ttu-id="37e6c-128">處理物件時如果找到重複索引鍵，請指定採取下列動作之一：</span><span class="sxs-lookup"><span data-stu-id="37e6c-128">Specify one of the following actions to be taken if a duplicate key is found when an object is processed:</span></span>  
  
-   <span data-ttu-id="37e6c-129">**忽略錯誤**忽略錯誤</span><span class="sxs-lookup"><span data-stu-id="37e6c-129">**Ignore error** ignores the error</span></span>  
  
-   <span data-ttu-id="37e6c-130">[**報告並繼續**] 會報告錯誤，並繼續處理作業</span><span class="sxs-lookup"><span data-stu-id="37e6c-130">**Report and continue** reports the error and continues the processing operation</span></span>  
  
-   <span data-ttu-id="37e6c-131">**[報告並停止]** 會報告錯誤並停止處理作業。</span><span class="sxs-lookup"><span data-stu-id="37e6c-131">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="37e6c-132">**Null 索引鍵已轉換為未知**</span><span class="sxs-lookup"><span data-stu-id="37e6c-132">**Null key converted to unknown**</span></span>  
 <span data-ttu-id="37e6c-133">指定處理物件時，若有 Null 成員索引鍵加入未知成員中，要採取下列其中一項動作。</span><span class="sxs-lookup"><span data-stu-id="37e6c-133">Specify one of the following actions to be taken when a null member key is added to the unknown member when an object is processed.</span></span>  
  
-   <span data-ttu-id="37e6c-134">**忽略錯誤**忽略錯誤</span><span class="sxs-lookup"><span data-stu-id="37e6c-134">**Ignore error** ignores the error</span></span>  
  
-   <span data-ttu-id="37e6c-135">[**報告並繼續**] 會報告錯誤，並繼續處理作業</span><span class="sxs-lookup"><span data-stu-id="37e6c-135">**Report and continue** reports the error and continues the processing operation</span></span>  
  
-   <span data-ttu-id="37e6c-136">**[報告並停止]** 會報告錯誤並停止處理作業。</span><span class="sxs-lookup"><span data-stu-id="37e6c-136">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="37e6c-137">**不允許 Null 索引鍵**</span><span class="sxs-lookup"><span data-stu-id="37e6c-137">**Null key not allowed**</span></span>  
 <span data-ttu-id="37e6c-138">指定處理物件時，若在不允許 Null 索引鍵的情況下找到 Null 索引鍵，要採取下列其中一項動作。</span><span class="sxs-lookup"><span data-stu-id="37e6c-138">Specify one of the following actions to be taken when a null key is found, but not allowed, when an object is processed.</span></span>  
  
-   <span data-ttu-id="37e6c-139">**忽略錯誤**忽略錯誤</span><span class="sxs-lookup"><span data-stu-id="37e6c-139">**Ignore error** ignores the error</span></span>  
  
-   <span data-ttu-id="37e6c-140">[**報告並繼續**] 會報告錯誤，並繼續處理作業</span><span class="sxs-lookup"><span data-stu-id="37e6c-140">**Report and continue** reports the error and continues the processing operation</span></span>  
  
-   <span data-ttu-id="37e6c-141">**[報告並停止]** 會報告錯誤並停止處理作業。</span><span class="sxs-lookup"><span data-stu-id="37e6c-141">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="37e6c-142">**錯誤記錄路徑**</span><span class="sxs-lookup"><span data-stu-id="37e6c-142">**Error log path**</span></span>  
 <span data-ttu-id="37e6c-143">輸入錯誤記錄檔的完整路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="37e6c-143">Type the full path and file name for the error log file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37e6c-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37e6c-144">See Also</span></span>  
 <span data-ttu-id="37e6c-145">[[採礦結構屬性] 對話方塊 &#40;Analysis Services-資料採礦&#41;](mining-structure-properties-dialog-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="37e6c-145">[Mining Structure Properties Dialog &#40;Analysis Services - Data Mining&#41;](mining-structure-properties-dialog-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="37e6c-146">[一般 &#40;[採礦結構] 對話方塊&#41; &#40;Analysis Services-資料採礦&#41;](general-mining-structure-dialog-box-analysis-services-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="37e6c-146">[General &#40;Mining Structure Dialog Box&#41; &#40;Analysis Services - Data Mining&#41;](general-mining-structure-dialog-box-analysis-services-data-mining.md)</span></span>  
  
  
