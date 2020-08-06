---
title: 資料分割處理目的地編輯器 (Advanced Page) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.advanced.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: 2039ee0f-069d-479d-90b2-2a12481b1162
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 12845ecd644eabd949ea37fbb18ba6cc9cf342f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592099"
---
# <a name="partition-processing-destination-editor-advanced-page"></a><span data-ttu-id="b0f8c-102">資料分割處理目的地編輯器 (進階頁面)</span><span class="sxs-lookup"><span data-stu-id="b0f8c-102">Partition Processing Destination Editor (Advanced Page)</span></span>
  <span data-ttu-id="b0f8c-103">使用 **[資料分割處理目的地編輯器]** 對話方塊的 **[進階]** 頁面，來設定錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-103">Use the **Advanced** page of the **Partition Processing Destination Editor** dialog box to configure error handling.</span></span>  
  
 <span data-ttu-id="b0f8c-104">若要深入了解資料分割處理目的地，請參閱＜ [Partition Processing Destination](data-flow/partition-processing-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-104">To learn more about the Partition Processing destination, see [Partition Processing Destination](data-flow/partition-processing-destination.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b0f8c-105">此處描述的工作不適用於 Analysis Services 表格式模型。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-105">Tasks described here do not apply to Analysis Services tabular models.</span></span>  <span data-ttu-id="b0f8c-106">您無法針對表格式模型，將輸入資料行對應至資料分割資料行。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-106">You cannot map input columns to partition columns for tabular models.</span></span> <span data-ttu-id="b0f8c-107">您可以改用 Analysis Services 執行 DDL 工作 ( [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) ) 來處理資料分割。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-107">You can instead use the Analysis Services Execute DDL task [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) to process the partition.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b0f8c-108">選項</span><span class="sxs-lookup"><span data-stu-id="b0f8c-108">Options</span></span>  
 <span data-ttu-id="b0f8c-109">**使用預設錯誤組態。**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-109">**Use default error configuration.**</span></span>  
 <span data-ttu-id="b0f8c-110">指定是否要使用預設的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-110">Specify whether to use the default [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] error handling.</span></span> <span data-ttu-id="b0f8c-111">根據預設，此值為 `True`。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-111">By default, this value is `True`.</span></span>  
  
 <span data-ttu-id="b0f8c-112">**索引鍵錯誤動作**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-112">**Key error action**</span></span>  
 <span data-ttu-id="b0f8c-113">指定如何處理具有無法接受之索引鍵值的記錄。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-113">Specify how to handle records that have unacceptable key values.</span></span>  
  
|<span data-ttu-id="b0f8c-114">值</span><span class="sxs-lookup"><span data-stu-id="b0f8c-114">Value</span></span>|<span data-ttu-id="b0f8c-115">描述</span><span class="sxs-lookup"><span data-stu-id="b0f8c-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b0f8c-116">**ConvertToUnknown**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-116">**ConvertToUnknown**</span></span>|<span data-ttu-id="b0f8c-117">將無法接受的索引鍵值轉換為未知值。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-117">Convert the unacceptable key value to the Unknown value.</span></span>|  
|<span data-ttu-id="b0f8c-118">**DiscardRecord**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-118">**DiscardRecord**</span></span>|<span data-ttu-id="b0f8c-119">捨棄記錄。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-119">Discard the record.</span></span>|  
  
 <span data-ttu-id="b0f8c-120">**忽略錯誤**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-120">**Ignore errors**</span></span>  
 <span data-ttu-id="b0f8c-121">指定應該忽略的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-121">Specify that errors should be ignored.</span></span>  
  
 <span data-ttu-id="b0f8c-122">**發生錯誤時停止**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-122">**Stop on error**</span></span>  
 <span data-ttu-id="b0f8c-123">指定發生錯誤時，應該停止處理。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-123">Specify that processing should stop when an error occurs.</span></span>  
  
 <span data-ttu-id="b0f8c-124">**錯誤數目**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-124">**Number of errors**</span></span>  
 <span data-ttu-id="b0f8c-125">如果您已選取 [發生錯誤時停止]\*\*\*\*，請指定處理應該停止的錯誤臨界值。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-125">Specify the error threshold at which processing should stop, if you have selected **Stop on error**.</span></span>  
  
 <span data-ttu-id="b0f8c-126">**發生錯誤時要執行的動作**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-126">**On error action**</span></span>  
 <span data-ttu-id="b0f8c-127">如果您已選取 [發生錯誤時停止]\*\*\*\*，請指定到達錯誤臨界值時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-127">Specify the action to take when the error threshold is reached, if you have selected **Stop on error**.</span></span>  
  
|<span data-ttu-id="b0f8c-128">值</span><span class="sxs-lookup"><span data-stu-id="b0f8c-128">Value</span></span>|<span data-ttu-id="b0f8c-129">描述</span><span class="sxs-lookup"><span data-stu-id="b0f8c-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b0f8c-130">**StopProcessing**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-130">**StopProcessing**</span></span>|<span data-ttu-id="b0f8c-131">停止處理。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-131">Stop processing.</span></span>|  
|<span data-ttu-id="b0f8c-132">**StopLogging**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-132">**StopLogging**</span></span>|<span data-ttu-id="b0f8c-133">停止記錄錯誤。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-133">Stop logging errors.</span></span>|  
  
 <span data-ttu-id="b0f8c-134">**找不到索引鍵**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-134">**Key not found**</span></span>  
 <span data-ttu-id="b0f8c-135">針對找不到索引鍵錯誤，指定要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-135">Specify the action to take for a key not found error.</span></span> <span data-ttu-id="b0f8c-136">依預設，此值為 **ReportAndContinue**。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-136">By default, this value is **ReportAndContinue**.</span></span>  
  
|<span data-ttu-id="b0f8c-137">值</span><span class="sxs-lookup"><span data-stu-id="b0f8c-137">Value</span></span>|<span data-ttu-id="b0f8c-138">描述</span><span class="sxs-lookup"><span data-stu-id="b0f8c-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b0f8c-139">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-139">**IgnoreError**</span></span>|<span data-ttu-id="b0f8c-140">忽略錯誤並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-140">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="b0f8c-141">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-141">**ReportAndContinue**</span></span>|<span data-ttu-id="b0f8c-142">報告錯誤並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-142">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="b0f8c-143">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-143">**ReportAndStop**</span></span>|<span data-ttu-id="b0f8c-144">報告錯誤並停止處理。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-144">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="b0f8c-145">**重複的索引鍵**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-145">**Duplicate key**</span></span>  
 <span data-ttu-id="b0f8c-146">針對重複索引鍵錯誤，指定要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-146">Specify the action to take for a duplicate key error.</span></span> <span data-ttu-id="b0f8c-147">依預設，此值為 **IgnoreError**。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-147">By default, this value is **IgnoreError**.</span></span>  
  
|<span data-ttu-id="b0f8c-148">值</span><span class="sxs-lookup"><span data-stu-id="b0f8c-148">Value</span></span>|<span data-ttu-id="b0f8c-149">描述</span><span class="sxs-lookup"><span data-stu-id="b0f8c-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b0f8c-150">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-150">**IgnoreError**</span></span>|<span data-ttu-id="b0f8c-151">忽略錯誤並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-151">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="b0f8c-152">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-152">**ReportAndContinue**</span></span>|<span data-ttu-id="b0f8c-153">報告錯誤並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-153">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="b0f8c-154">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-154">**ReportAndStop**</span></span>|<span data-ttu-id="b0f8c-155">報告錯誤並停止處理。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-155">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="b0f8c-156">**Null 索引鍵已轉換為未知**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-156">**Null key converted to unknown**</span></span>  
 <span data-ttu-id="b0f8c-157">指定當 Null 索引鍵轉換為未知值的時候應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-157">Specify the action to take when a null key has been converted to the Unknown value.</span></span> <span data-ttu-id="b0f8c-158">依預設，此值為 **IgnoreError**。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-158">By default, this value is **IgnoreError**.</span></span>  
  
|<span data-ttu-id="b0f8c-159">值</span><span class="sxs-lookup"><span data-stu-id="b0f8c-159">Value</span></span>|<span data-ttu-id="b0f8c-160">描述</span><span class="sxs-lookup"><span data-stu-id="b0f8c-160">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b0f8c-161">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-161">**IgnoreError**</span></span>|<span data-ttu-id="b0f8c-162">忽略錯誤並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-162">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="b0f8c-163">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-163">**ReportAndContinue**</span></span>|<span data-ttu-id="b0f8c-164">報告錯誤並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-164">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="b0f8c-165">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-165">**ReportAndStop**</span></span>|<span data-ttu-id="b0f8c-166">報告錯誤並停止處理。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-166">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="b0f8c-167">**不允許 Null 索引鍵**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-167">**Null key not allowed**</span></span>  
 <span data-ttu-id="b0f8c-168">指定在不允許 Null 索引鍵的情況下如果發現 Null 索引鍵，所要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-168">Specify the action to take when null keys are not allowed and a null key is encountered.</span></span> <span data-ttu-id="b0f8c-169">依預設，此值為 **ReportAndContinue**。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-169">By default, this value is **ReportAndContinue**.</span></span>  
  
|<span data-ttu-id="b0f8c-170">值</span><span class="sxs-lookup"><span data-stu-id="b0f8c-170">Value</span></span>|<span data-ttu-id="b0f8c-171">描述</span><span class="sxs-lookup"><span data-stu-id="b0f8c-171">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b0f8c-172">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-172">**IgnoreError**</span></span>|<span data-ttu-id="b0f8c-173">忽略錯誤並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-173">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="b0f8c-174">**ReportAndContinue**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-174">**ReportAndContinue**</span></span>|<span data-ttu-id="b0f8c-175">報告錯誤並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-175">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="b0f8c-176">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-176">**ReportAndStop**</span></span>|<span data-ttu-id="b0f8c-177">報告錯誤並停止處理。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-177">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="b0f8c-178">**錯誤記錄路徑**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-178">**Error log path**</span></span>  
 <span data-ttu-id="b0f8c-179">輸入錯誤記錄檔的路徑，或者使用瀏覽 **(...)** 按鈕來選取目的地。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-179">Type the path for the error log, or select a destination by using the browse **(...)** button.</span></span>  
  
 <span data-ttu-id="b0f8c-180">**瀏覽 (...)**</span><span class="sxs-lookup"><span data-stu-id="b0f8c-180">**Browse (...)**</span></span>  
 <span data-ttu-id="b0f8c-181">選取錯誤記錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="b0f8c-181">Select a path for the error log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0f8c-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0f8c-182">See Also</span></span>  
 <span data-ttu-id="b0f8c-183">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b0f8c-183">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="b0f8c-184">資料分割處理目的地編輯器 &#40;對應頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="b0f8c-184">Partition Processing Destination Editor &#40;Mappings Page&#41;</span></span>](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md)  
  
  
