---
title: 維度處理目的地編輯器 (Advanced Page) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimprocessingtransformation.advanced.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 2b30835a-2680-4d98-89a4-4f17e29e3818
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5be80cbbfb6871594d7481ccc0f9444d014885e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599603"
---
# <a name="dimension-processing-destination-editor-advanced-page"></a><span data-ttu-id="5e024-102">維度處理目的地編輯器 (進階頁面)</span><span class="sxs-lookup"><span data-stu-id="5e024-102">Dimension Processing Destination Editor (Advanced Page)</span></span>
  <span data-ttu-id="5e024-103">使用 **[維度處理目的地編輯器]** 對話方塊的 **[進階]** 頁面，來設定錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="5e024-103">Use the **Advanced** page of the **Dimension Processing Destination Editor** dialog box to configure error handling.</span></span>  
  
 <span data-ttu-id="5e024-104">若要深入了解維度處理目的地，請參閱＜ [Dimension Processing Destination](data-flow/dimension-processing-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5e024-104">To learn more about the Dimension Processing destination, see [Dimension Processing Destination](data-flow/dimension-processing-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5e024-105">選項</span><span class="sxs-lookup"><span data-stu-id="5e024-105">Options</span></span>  
 <span data-ttu-id="5e024-106">**使用預設錯誤組態。**</span><span class="sxs-lookup"><span data-stu-id="5e024-106">**Use default error configuration.**</span></span>  
 <span data-ttu-id="5e024-107">指定是否要使用預設的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="5e024-107">Specify whether to use the default [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] error handling.</span></span> <span data-ttu-id="5e024-108">根據預設，此值為 `True`。</span><span class="sxs-lookup"><span data-stu-id="5e024-108">By default, this value is `True`.</span></span>  
  
 <span data-ttu-id="5e024-109">**索引鍵錯誤動作**</span><span class="sxs-lookup"><span data-stu-id="5e024-109">**Key error action**</span></span>  
 <span data-ttu-id="5e024-110">指定如何處理具有無法接受之索引鍵值的記錄。</span><span class="sxs-lookup"><span data-stu-id="5e024-110">Specify how to handle records that have unacceptable key values.</span></span>  
  
|<span data-ttu-id="5e024-111">值</span><span class="sxs-lookup"><span data-stu-id="5e024-111">Value</span></span>|<span data-ttu-id="5e024-112">描述</span><span class="sxs-lookup"><span data-stu-id="5e024-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5e024-113">**ConvertToUnknown**</span><span class="sxs-lookup"><span data-stu-id="5e024-113">**ConvertToUnknown**</span></span>|<span data-ttu-id="5e024-114">將無法接受的索引鍵值轉換為 `UnknownMember` 值。</span><span class="sxs-lookup"><span data-stu-id="5e024-114">Convert the unacceptable key value to the `UnknownMember` value.</span></span>|  
|<span data-ttu-id="5e024-115">**DiscardRecord**</span><span class="sxs-lookup"><span data-stu-id="5e024-115">**DiscardRecord**</span></span>|<span data-ttu-id="5e024-116">捨棄記錄。</span><span class="sxs-lookup"><span data-stu-id="5e024-116">Discard the record.</span></span>|  
  
 <span data-ttu-id="5e024-117">**忽略錯誤**</span><span class="sxs-lookup"><span data-stu-id="5e024-117">**Ignore errors**</span></span>  
 <span data-ttu-id="5e024-118">指定應該忽略的錯誤。</span><span class="sxs-lookup"><span data-stu-id="5e024-118">Specify that errors should be ignored.</span></span>  
  
 <span data-ttu-id="5e024-119">**發生錯誤時停止**</span><span class="sxs-lookup"><span data-stu-id="5e024-119">**Stop on error**</span></span>  
 <span data-ttu-id="5e024-120">指定發生錯誤時，應該停止處理。</span><span class="sxs-lookup"><span data-stu-id="5e024-120">Specify that processing should stop when an error occurs.</span></span>  
  
 <span data-ttu-id="5e024-121">**錯誤數目**</span><span class="sxs-lookup"><span data-stu-id="5e024-121">**Number of errors**</span></span>  
 <span data-ttu-id="5e024-122">如果您已選取 [發生錯誤時停止]\*\*\*\*，則指定處理應該停止的錯誤臨界值。</span><span class="sxs-lookup"><span data-stu-id="5e024-122">Specify the error threshold at which processing should stop, if you have selected **Stop on errors**.</span></span>  
  
 <span data-ttu-id="5e024-123">**發生錯誤時要執行的動作**</span><span class="sxs-lookup"><span data-stu-id="5e024-123">**On error action**</span></span>  
 <span data-ttu-id="5e024-124">如果您已選取 [發生錯誤時停止]\*\*\*\*，則指定到達錯誤臨界值時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="5e024-124">Specify the action to take when the error threshold is reached, if you have selected **Stop on errors**.</span></span>  
  
|<span data-ttu-id="5e024-125">值</span><span class="sxs-lookup"><span data-stu-id="5e024-125">Value</span></span>|<span data-ttu-id="5e024-126">描述</span><span class="sxs-lookup"><span data-stu-id="5e024-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5e024-127">**StopProcessing**</span><span class="sxs-lookup"><span data-stu-id="5e024-127">**StopProcessing**</span></span>|<span data-ttu-id="5e024-128">停止處理。</span><span class="sxs-lookup"><span data-stu-id="5e024-128">Stop processing.</span></span>|  
|<span data-ttu-id="5e024-129">**StopLogging**</span><span class="sxs-lookup"><span data-stu-id="5e024-129">**StopLogging**</span></span>|<span data-ttu-id="5e024-130">停止記錄錯誤。</span><span class="sxs-lookup"><span data-stu-id="5e024-130">Stop logging errors.</span></span>|  
  
 <span data-ttu-id="5e024-131">**找不到索引鍵**</span><span class="sxs-lookup"><span data-stu-id="5e024-131">**Key not found**</span></span>  
 <span data-ttu-id="5e024-132">針對找不到索引鍵錯誤，指定要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="5e024-132">Specify the action to take for a key not found error.</span></span> <span data-ttu-id="5e024-133">依預設，此值為 **ReportAndContinue**。</span><span class="sxs-lookup"><span data-stu-id="5e024-133">By default, this value is **ReportAndContinue**.</span></span>  
  
|<span data-ttu-id="5e024-134">值</span><span class="sxs-lookup"><span data-stu-id="5e024-134">Value</span></span>|<span data-ttu-id="5e024-135">描述</span><span class="sxs-lookup"><span data-stu-id="5e024-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5e024-136">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="5e024-136">**IgnoreError**</span></span>|<span data-ttu-id="5e024-137">忽略錯誤並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="5e024-137">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="5e024-138">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="5e024-138">**ReportAndContinue**</span></span>|<span data-ttu-id="5e024-139">報告錯誤並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="5e024-139">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="5e024-140">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="5e024-140">**ReportAndStop**</span></span>|<span data-ttu-id="5e024-141">報告錯誤並停止處理。</span><span class="sxs-lookup"><span data-stu-id="5e024-141">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="5e024-142">**重複的索引鍵**</span><span class="sxs-lookup"><span data-stu-id="5e024-142">**Duplicate key**</span></span>  
 <span data-ttu-id="5e024-143">針對重複索引鍵錯誤，指定要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="5e024-143">Specify the action to take for a duplicate key error.</span></span> <span data-ttu-id="5e024-144">依預設，此值為 **IgnoreError**。</span><span class="sxs-lookup"><span data-stu-id="5e024-144">By default, this value is **IgnoreError**.</span></span>  
  
|<span data-ttu-id="5e024-145">值</span><span class="sxs-lookup"><span data-stu-id="5e024-145">Value</span></span>|<span data-ttu-id="5e024-146">描述</span><span class="sxs-lookup"><span data-stu-id="5e024-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5e024-147">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="5e024-147">**IgnoreError**</span></span>|<span data-ttu-id="5e024-148">忽略錯誤並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="5e024-148">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="5e024-149">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="5e024-149">**ReportAndContinue**</span></span>|<span data-ttu-id="5e024-150">報告錯誤並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="5e024-150">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="5e024-151">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="5e024-151">**ReportAndStop**</span></span>|<span data-ttu-id="5e024-152">報告錯誤並停止處理。</span><span class="sxs-lookup"><span data-stu-id="5e024-152">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="5e024-153">**Null 索引鍵已轉換為未知**</span><span class="sxs-lookup"><span data-stu-id="5e024-153">**Null key converted to unknown**</span></span>  
 <span data-ttu-id="5e024-154">指定當 Null 索引鍵轉換為 `UnknownMember` 值的時候應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="5e024-154">Specify the action to take when a null key has been converted to the `UnknownMember` value.</span></span> <span data-ttu-id="5e024-155">依預設，此值為 **IgnoreError**。</span><span class="sxs-lookup"><span data-stu-id="5e024-155">By default, this value is **IgnoreError**.</span></span>  
  
|<span data-ttu-id="5e024-156">值</span><span class="sxs-lookup"><span data-stu-id="5e024-156">Value</span></span>|<span data-ttu-id="5e024-157">描述</span><span class="sxs-lookup"><span data-stu-id="5e024-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5e024-158">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="5e024-158">**IgnoreError**</span></span>|<span data-ttu-id="5e024-159">忽略錯誤並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="5e024-159">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="5e024-160">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="5e024-160">**ReportAndContinue**</span></span>|<span data-ttu-id="5e024-161">報告錯誤並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="5e024-161">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="5e024-162">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="5e024-162">**ReportAndStop**</span></span>|<span data-ttu-id="5e024-163">報告錯誤並停止處理。</span><span class="sxs-lookup"><span data-stu-id="5e024-163">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="5e024-164">**不允許 Null 索引鍵**</span><span class="sxs-lookup"><span data-stu-id="5e024-164">**Null key not allowed**</span></span>  
 <span data-ttu-id="5e024-165">指定在不允許 Null 索引鍵的情況下如果發現 Null 索引鍵，所要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="5e024-165">Specify the action to take when null keys are not allowed and a null key is encountered.</span></span> <span data-ttu-id="5e024-166">依預設，此值為 **ReportAndContinue**。</span><span class="sxs-lookup"><span data-stu-id="5e024-166">By default, this value is **ReportAndContinue**.</span></span>  
  
|<span data-ttu-id="5e024-167">值</span><span class="sxs-lookup"><span data-stu-id="5e024-167">Value</span></span>|<span data-ttu-id="5e024-168">描述</span><span class="sxs-lookup"><span data-stu-id="5e024-168">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5e024-169">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="5e024-169">**IgnoreError**</span></span>|<span data-ttu-id="5e024-170">忽略錯誤並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="5e024-170">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="5e024-171">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="5e024-171">**ReportAndContinue**</span></span>|<span data-ttu-id="5e024-172">報告錯誤並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="5e024-172">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="5e024-173">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="5e024-173">**ReportAndStop**</span></span>|<span data-ttu-id="5e024-174">報告錯誤並停止處理。</span><span class="sxs-lookup"><span data-stu-id="5e024-174">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="5e024-175">**錯誤記錄路徑**</span><span class="sxs-lookup"><span data-stu-id="5e024-175">**Error log path**</span></span>  
 <span data-ttu-id="5e024-176">輸入錯誤記錄路徑，或者按一下 [瀏覽 (…)]\*\*\*\* 按鈕以選取目的地。</span><span class="sxs-lookup"><span data-stu-id="5e024-176">Type the path of the error log, or click the **browse(...)** button to select a destination.</span></span>  
  
 <span data-ttu-id="5e024-177">**瀏覽 (...)**</span><span class="sxs-lookup"><span data-stu-id="5e024-177">**Browse (...)**</span></span>  
 <span data-ttu-id="5e024-178">選取錯誤記錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="5e024-178">Select a path for the error log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e024-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e024-179">See Also</span></span>  
 <span data-ttu-id="5e024-180">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="5e024-180">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="5e024-181">[維度處理目的地編輯器 &#40;連線管理員頁面&#41;](../../2014/integration-services/dimension-processing-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="5e024-181">[Dimension Processing Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/dimension-processing-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="5e024-182">維度處理目的地編輯器 &#40;對應頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="5e024-182">Dimension Processing Destination Editor &#40;Mappings Page&#41;</span></span>](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md)  
  
  
