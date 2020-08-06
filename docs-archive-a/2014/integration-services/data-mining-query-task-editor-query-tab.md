---
title: '[資料採礦查詢工作編輯器] (查詢索引標籤) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dmquerytask.query.f1
helpviewer_keywords:
- Data Mining Query Task Editor
ms.assetid: 72b1755d-d226-46c5-b862-0c9333196a10
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6005c92d0d48850461c01353ddf94c61140d0f2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706589"
---
# <a name="data-mining-query-task-editor-query-tab"></a><span data-ttu-id="e5db0-102">資料採礦查詢工作編輯器 (查詢索引標籤)</span><span class="sxs-lookup"><span data-stu-id="e5db0-102">Data Mining Query Task Editor (Query Tab)</span></span>
  <span data-ttu-id="e5db0-103">使用 [資料採礦查詢工作]\*\*\*\* 對話方塊的 [查詢]\*\*\*\* 索引標籤，即可依據採礦模型建立預測查詢。</span><span class="sxs-lookup"><span data-stu-id="e5db0-103">Use the **Query** tab of the **Data Mining Query Task** dialog box to create prediction queries based on a mining model.</span></span> <span data-ttu-id="e5db0-104">在此對話方塊中，您也可以將參數和結果集繫結到變數。</span><span class="sxs-lookup"><span data-stu-id="e5db0-104">In this dialog box you can also bind parameters and result sets to variables.</span></span>  
  
 <span data-ttu-id="e5db0-105">若要深入了解在封裝中實作資料採礦，請參閱 [Data Mining Query Task](control-flow/data-mining-query-task.md) (資料採礦查詢工作) 和 [Data Mining Solutions](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions)(資料採礦方案)。</span><span class="sxs-lookup"><span data-stu-id="e5db0-105">To learn about implementing data mining in packages, see [Data Mining Query Task](control-flow/data-mining-query-task.md) and [Data Mining Solutions](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions).</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="e5db0-106">一般選項</span><span class="sxs-lookup"><span data-stu-id="e5db0-106">General Options</span></span>  
 <span data-ttu-id="e5db0-107">**名稱**</span><span class="sxs-lookup"><span data-stu-id="e5db0-107">**Name**</span></span>  
 <span data-ttu-id="e5db0-108">為資料採礦查詢工作提供唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="e5db0-108">Provide a unique name for the Data Mining Query task.</span></span> <span data-ttu-id="e5db0-109">這個名稱是作為工作圖示中的標籤使用。</span><span class="sxs-lookup"><span data-stu-id="e5db0-109">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e5db0-110">工作名稱在封裝內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="e5db0-110">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="e5db0-111">**說明**</span><span class="sxs-lookup"><span data-stu-id="e5db0-111">**Description**</span></span>  
 <span data-ttu-id="e5db0-112">輸入資料採礦查詢工作的描述。</span><span class="sxs-lookup"><span data-stu-id="e5db0-112">Type a description of the Data Mining Query task.</span></span>  
  
## <a name="build-query-tab-options"></a><span data-ttu-id="e5db0-113">建立查詢索引標籤選項</span><span class="sxs-lookup"><span data-stu-id="e5db0-113">Build Query Tab Options</span></span>  
 <span data-ttu-id="e5db0-114">**資料採礦查詢**</span><span class="sxs-lookup"><span data-stu-id="e5db0-114">**Data mining query**</span></span>  
 <span data-ttu-id="e5db0-115">輸入資料採礦查詢。</span><span class="sxs-lookup"><span data-stu-id="e5db0-115">Type a data mining query.</span></span>  
  
 <span data-ttu-id="e5db0-116">**相關主題：**  [資料採礦延伸模組 &#40;DMX&#41; 參考](/sql/dmx/data-mining-extensions-dmx-reference)</span><span class="sxs-lookup"><span data-stu-id="e5db0-116">**Related Topics:**  [Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference)</span></span>  
  
 <span data-ttu-id="e5db0-117">**建立新查詢**</span><span class="sxs-lookup"><span data-stu-id="e5db0-117">**Build New Query**</span></span>  
 <span data-ttu-id="e5db0-118">使用圖形工具來建立資料採礦查詢。</span><span class="sxs-lookup"><span data-stu-id="e5db0-118">Create the data mining query using a graphical tool.</span></span>  
  
 <span data-ttu-id="e5db0-119">**相關主題：** [資料採礦查詢](control-flow/data-mining-query.md)</span><span class="sxs-lookup"><span data-stu-id="e5db0-119">**Related Topics:** [Data Mining Query](control-flow/data-mining-query.md)</span></span>  
  
## <a name="parameter-mapping-tab-options"></a><span data-ttu-id="e5db0-120">參數對應索引標籤選項</span><span class="sxs-lookup"><span data-stu-id="e5db0-120">Parameter Mapping Tab Options</span></span>  
 <span data-ttu-id="e5db0-121">**參數名稱**</span><span class="sxs-lookup"><span data-stu-id="e5db0-121">**Parameter Name**</span></span>  
 <span data-ttu-id="e5db0-122">選擇性地更新參數名稱。</span><span class="sxs-lookup"><span data-stu-id="e5db0-122">Optionally, update the parameter name.</span></span> <span data-ttu-id="e5db0-123">在 [變數名稱]\*\*\*\* 清單中選取變數，即可將參數對應至變數。</span><span class="sxs-lookup"><span data-stu-id="e5db0-123">Map the parameter to a variable by selecting a variable in the **Variable Name** list.</span></span>  
  
 <span data-ttu-id="e5db0-124">**變數名稱**</span><span class="sxs-lookup"><span data-stu-id="e5db0-124">**Variable Name**</span></span>  
 <span data-ttu-id="e5db0-125">在清單中選取變數，以將其對應至參數。</span><span class="sxs-lookup"><span data-stu-id="e5db0-125">Select a variable in the list to map it to the parameter.</span></span>  
  
 <span data-ttu-id="e5db0-126">**加入**</span><span class="sxs-lookup"><span data-stu-id="e5db0-126">**Add**</span></span>  
 <span data-ttu-id="e5db0-127">將參數加入清單中。</span><span class="sxs-lookup"><span data-stu-id="e5db0-127">Add to a parameter to the list.</span></span>  
  
 <span data-ttu-id="e5db0-128">**移除**</span><span class="sxs-lookup"><span data-stu-id="e5db0-128">**Remove**</span></span>  
 <span data-ttu-id="e5db0-129">選取參數，然後按一下 [移除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e5db0-129">Select a parameter, and then click **Remove**.</span></span>  
  
## <a name="result-set-tab-options"></a><span data-ttu-id="e5db0-130">結果集索引標籤選項</span><span class="sxs-lookup"><span data-stu-id="e5db0-130">Result Set Tab Options</span></span>  
 <span data-ttu-id="e5db0-131">**結果名稱**</span><span class="sxs-lookup"><span data-stu-id="e5db0-131">**Result Name**</span></span>  
 <span data-ttu-id="e5db0-132">選擇性地更新結果集名稱。</span><span class="sxs-lookup"><span data-stu-id="e5db0-132">Optionally, update the result set name.</span></span> <span data-ttu-id="e5db0-133">在 [變數名稱]\*\*\*\* 清單中選取變數，即可將結果對應至變數。</span><span class="sxs-lookup"><span data-stu-id="e5db0-133">Map the result to a variable by selecting a variable in the **Variable Name** list.</span></span>  
  
 <span data-ttu-id="e5db0-134">按一下 [加入]\*\*\*\* 來加入結果之後，請為該結果提供唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="e5db0-134">After you have added a result by clicking **Add**, provide a unique name for the result.</span></span>  
  
 <span data-ttu-id="e5db0-135">**變數名稱**</span><span class="sxs-lookup"><span data-stu-id="e5db0-135">**Variable Name**</span></span>  
 <span data-ttu-id="e5db0-136">在清單中選取變數，以將其對應至結果集。</span><span class="sxs-lookup"><span data-stu-id="e5db0-136">Select a variable in the list to map it to the result set.</span></span>  
  
 <span data-ttu-id="e5db0-137">**結果類型**</span><span class="sxs-lookup"><span data-stu-id="e5db0-137">**Result Type**</span></span>  
 <span data-ttu-id="e5db0-138">指出傳回單一資料列或完整結果集。</span><span class="sxs-lookup"><span data-stu-id="e5db0-138">Indicate whether to return a single row or a full result set.</span></span>  
  
 <span data-ttu-id="e5db0-139">**加入**</span><span class="sxs-lookup"><span data-stu-id="e5db0-139">**Add**</span></span>  
 <span data-ttu-id="e5db0-140">將結果集加入清單中。</span><span class="sxs-lookup"><span data-stu-id="e5db0-140">Add a result set to the list.</span></span>  
  
 <span data-ttu-id="e5db0-141">**移除**</span><span class="sxs-lookup"><span data-stu-id="e5db0-141">**Remove**</span></span>  
 <span data-ttu-id="e5db0-142">選取結果，然後按一下 [移除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e5db0-142">Select a result, and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5db0-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5db0-143">See Also</span></span>  
 <span data-ttu-id="e5db0-144">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e5db0-144">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="e5db0-145">[資料採礦查詢工作編輯器 &#40;[模型] 索引標籤&#41;](../../2014/integration-services/data-mining-query-task-editor-mining-model-tab.md) </span><span class="sxs-lookup"><span data-stu-id="e5db0-145">[Data Mining Query Task Editor &#40;Mining Model Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-mining-model-tab.md) </span></span>  
 <span data-ttu-id="e5db0-146">[資料採礦查詢工作編輯器 &#40;輸出] 索引標籤&#41;](../../2014/integration-services/data-mining-query-task-editor-output-tab.md) </span><span class="sxs-lookup"><span data-stu-id="e5db0-146">[Data Mining Query Task Editor &#40;Output Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-output-tab.md) </span></span>  
 [<span data-ttu-id="e5db0-147">資料採礦設計師</span><span class="sxs-lookup"><span data-stu-id="e5db0-147">Data Mining Designer</span></span>](https://docs.microsoft.com/analysis-services/data-mining/data-mining-designer)  
  
  
