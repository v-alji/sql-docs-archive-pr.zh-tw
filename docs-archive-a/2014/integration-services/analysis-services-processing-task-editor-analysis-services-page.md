---
title: Analysis Services 處理工作編輯器 (Analysis Services 頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asprocessingtask.as.f1
helpviewer_keywords:
- Analysis Services Processing Task Editor
ms.assetid: 5612be78-57cf-4e4e-92cf-6bfa9f971040
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aabcfe286b40f58b429227654107d58e8a4ee837
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593525"
---
# <a name="analysis-services-processing-task-editor-analysis-services-page"></a><span data-ttu-id="92ab4-102">Analysis Services 處理工作編輯器 (Analysis Services 頁面)</span><span class="sxs-lookup"><span data-stu-id="92ab4-102">Analysis Services Processing Task Editor (Analysis Services Page)</span></span>
  <span data-ttu-id="92ab4-103">使用 [Analysis Services 處理工作編輯器]\*\*\*\* 對話方塊的 [Analysis Services]\*\*\*\* 頁面，即可指定 Analysis Services 連接管理員、選取要處理的分析物件，以及設定處理與錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="92ab4-103">Use the **Analysis Services** page of the **Analysis Services Processing Task Editor** dialog box to specify an Analysis Services connection manager, select the analytic objects to process, and set processing and error handling options.</span></span>  
  
 <span data-ttu-id="92ab4-104">處理表格式模型時，請牢記以下事項：</span><span class="sxs-lookup"><span data-stu-id="92ab4-104">When processing tabular models, keep the following in mind:</span></span>  
  
1.  <span data-ttu-id="92ab4-105">您無法在表格式模型上執行影響分析。</span><span class="sxs-lookup"><span data-stu-id="92ab4-105">You cannot perform impact analysis on tabular models.</span></span>  
  
2.  <span data-ttu-id="92ab4-106">系統不會公開表格式模型的部分處理選項，例如 [處理重組] 和 [處理重新計算]。</span><span class="sxs-lookup"><span data-stu-id="92ab4-106">Some processing options for tabular mode are not exposed, such as Process Defrag and Process Recalc.</span></span> <span data-ttu-id="92ab4-107">您可以使用「執行 DLL」工作，執行這些功能。</span><span class="sxs-lookup"><span data-stu-id="92ab4-107">You can perform these functions by using the Execute DDL task.</span></span>  
  
3.  <span data-ttu-id="92ab4-108">提供的部分處理選項 (例如處理索引) 不適合表格式模型，因此應該不會使用。</span><span class="sxs-lookup"><span data-stu-id="92ab4-108">Some processing options provided, such as process indexes, are not appropriate for tabular models and should not be used.</span></span>  
  
4.  <span data-ttu-id="92ab4-109">表格式模型會忽略批次處理設定。</span><span class="sxs-lookup"><span data-stu-id="92ab4-109">Batch settings are ignored for tabular models.</span></span>  
  
 <span data-ttu-id="92ab4-110">若要了解這個工作，請參閱 [Analysis Services 處理工作](control-flow/analysis-services-processing-task.md)。</span><span class="sxs-lookup"><span data-stu-id="92ab4-110">To learn about this task, see [Analysis Services Processing Task](control-flow/analysis-services-processing-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="92ab4-111">選項</span><span class="sxs-lookup"><span data-stu-id="92ab4-111">Options</span></span>  
 <span data-ttu-id="92ab4-112">**Analysis Services 連線管理員**</span><span class="sxs-lookup"><span data-stu-id="92ab4-112">**Analysis Services connection manager**</span></span>  
 <span data-ttu-id="92ab4-113">在清單中選取現有的 Analysis Services 連接管理員，或按一下 [新增]\*\*\*\* 以建立新的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="92ab4-113">Select an existing Analysis Services connection manager in the list or click **New** to create a new connection manager.</span></span>  
  
 <span data-ttu-id="92ab4-114">**新增**</span><span class="sxs-lookup"><span data-stu-id="92ab4-114">**New**</span></span>  
 <span data-ttu-id="92ab4-115">建立新的 Analysis Services 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="92ab4-115">Create a new Analysis Services connection manager.</span></span>  
  
 <span data-ttu-id="92ab4-116">**相關主題：** [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md)、 [加入 Analysis Services 連接管理員對話方塊 UI 參考](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)</span><span class="sxs-lookup"><span data-stu-id="92ab4-116">**Related Topics:** [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md), [Add Analysis Services Connection Manager Dialog Box UI Reference](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)</span></span>  
  
 <span data-ttu-id="92ab4-117">**物件清單**</span><span class="sxs-lookup"><span data-stu-id="92ab4-117">**Object list**</span></span>  
 |<span data-ttu-id="92ab4-118">屬性</span><span class="sxs-lookup"><span data-stu-id="92ab4-118">Property</span></span>|<span data-ttu-id="92ab4-119">描述</span><span class="sxs-lookup"><span data-stu-id="92ab4-119">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="92ab4-120">**Object Name**</span><span class="sxs-lookup"><span data-stu-id="92ab4-120">**Object Name**</span></span>|<span data-ttu-id="92ab4-121">列出指定的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="92ab4-121">Lists the specified object names.</span></span>|  
|<span data-ttu-id="92ab4-122">**型別**</span><span class="sxs-lookup"><span data-stu-id="92ab4-122">**Type**</span></span>|<span data-ttu-id="92ab4-123">列出指定的物件類型。</span><span class="sxs-lookup"><span data-stu-id="92ab4-123">Lists the types of the specified objects.</span></span>|  
|<span data-ttu-id="92ab4-124">**處理選項**</span><span class="sxs-lookup"><span data-stu-id="92ab4-124">**Process Options**</span></span>|<span data-ttu-id="92ab4-125">選取清單中的處理選項。</span><span class="sxs-lookup"><span data-stu-id="92ab4-125">Select a processing option in the list.</span></span><br /><br /> <span data-ttu-id="92ab4-126">**相關主題**：多[維度模型物件處理](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services)</span><span class="sxs-lookup"><span data-stu-id="92ab4-126">**Related Topics**: [Multidimensional Model Object Processing](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services)</span></span>|  
|<span data-ttu-id="92ab4-127">**設定**</span><span class="sxs-lookup"><span data-stu-id="92ab4-127">**Settings**</span></span>|<span data-ttu-id="92ab4-128">列出指定物件的處理設定。</span><span class="sxs-lookup"><span data-stu-id="92ab4-128">Lists processing settings for the specified objects.</span></span>|  
  
 <span data-ttu-id="92ab4-129">**加入**</span><span class="sxs-lookup"><span data-stu-id="92ab4-129">**Add**</span></span>  
 <span data-ttu-id="92ab4-130">將 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件加入清單中。</span><span class="sxs-lookup"><span data-stu-id="92ab4-130">Add an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object to the list.</span></span>  
  
 <span data-ttu-id="92ab4-131">**移除**</span><span class="sxs-lookup"><span data-stu-id="92ab4-131">**Remove**</span></span>  
 <span data-ttu-id="92ab4-132">選取物件，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="92ab4-132">Select an object, and then click **Delete**.</span></span>  
  
 <span data-ttu-id="92ab4-133">**影響分析**</span><span class="sxs-lookup"><span data-stu-id="92ab4-133">**Impact Analysis**</span></span>  
 <span data-ttu-id="92ab4-134">執行選取之物件的影響分析。</span><span class="sxs-lookup"><span data-stu-id="92ab4-134">Perform impact analysis on the selected object.</span></span>  
  
 <span data-ttu-id="92ab4-135">**相關主題：** [影響分析對話方塊 &#40;Analysis Services - 多維度資料&#41;](../../2014/analysis-services/impact-analysis-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="92ab4-135">**Related Topics:** [Impact Analysis Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../../2014/analysis-services/impact-analysis-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
 <span data-ttu-id="92ab4-136">**批次設定摘要**</span><span class="sxs-lookup"><span data-stu-id="92ab4-136">**Batch Settings Summary**</span></span>  
 |<span data-ttu-id="92ab4-137">屬性</span><span class="sxs-lookup"><span data-stu-id="92ab4-137">Property</span></span>|<span data-ttu-id="92ab4-138">描述</span><span class="sxs-lookup"><span data-stu-id="92ab4-138">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="92ab4-139">**處理順序**</span><span class="sxs-lookup"><span data-stu-id="92ab4-139">**Processing order**</span></span>|<span data-ttu-id="92ab4-140">指定循序地或在批次中處理物件；如果使用平行處理，請指定要並行處理的物件數目。</span><span class="sxs-lookup"><span data-stu-id="92ab4-140">Specifies whether objects are processed sequentially or in a batch; if parallel processing is used, specifies the number of objects to process concurrently.</span></span>|  
|<span data-ttu-id="92ab4-141">**交易模式**</span><span class="sxs-lookup"><span data-stu-id="92ab4-141">**Transaction mode**</span></span>|<span data-ttu-id="92ab4-142">指定循序處理的交易模式。</span><span class="sxs-lookup"><span data-stu-id="92ab4-142">Specifies the transaction mode for sequential processing.</span></span>|  
|<span data-ttu-id="92ab4-143">**維度錯誤**</span><span class="sxs-lookup"><span data-stu-id="92ab4-143">**Dimension errors**</span></span>|<span data-ttu-id="92ab4-144">指定發生錯誤時的工作行為。</span><span class="sxs-lookup"><span data-stu-id="92ab4-144">Specifies the task behavior when errors occur.</span></span>|  
|<span data-ttu-id="92ab4-145">**維度索引鍵錯誤記錄路徑**</span><span class="sxs-lookup"><span data-stu-id="92ab4-145">**Dimension key error log path**</span></span>|<span data-ttu-id="92ab4-146">指定記錄錯誤的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="92ab4-146">Specifies the path of the file to which errors are logged.</span></span>|  
|<span data-ttu-id="92ab4-147">**處理受影響的物件**</span><span class="sxs-lookup"><span data-stu-id="92ab4-147">**Process affected objects**</span></span>|<span data-ttu-id="92ab4-148">指出是否也處理相依物件或受影響的物件。</span><span class="sxs-lookup"><span data-stu-id="92ab4-148">Indicates whether dependent or affected objects are also processed.</span></span>|  
  
 <span data-ttu-id="92ab4-149">**變更設定**</span><span class="sxs-lookup"><span data-stu-id="92ab4-149">**Change Settings**</span></span>  
 <span data-ttu-id="92ab4-150">變更維度索引鍵中的處理選項和錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="92ab4-150">Change the processing options and the handling of errors in dimension keys.</span></span>  
  
 <span data-ttu-id="92ab4-151">**相關主題：** [變更設定對話方塊 &#40;Analysis Services - 多維度資料&#41;](../../2014/analysis-services/change-settings-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="92ab4-151">**Related Topics:** [Change Settings Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../../2014/analysis-services/change-settings-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92ab4-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92ab4-152">See Also</span></span>  
 <span data-ttu-id="92ab4-153">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="92ab4-153">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="92ab4-154">[Analysis Services 處理工作編輯器 &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="92ab4-154">[Analysis Services Processing Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="92ab4-155">Analysis Services 執行 DDL 工作</span><span class="sxs-lookup"><span data-stu-id="92ab4-155">Analysis Services Execute DDL Task</span></span>](control-flow/analysis-services-execute-ddl-task.md)  
  
  
