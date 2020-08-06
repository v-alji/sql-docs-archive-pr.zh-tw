---
title: 資料集屬性對話方塊、參數 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10150"
- sql12.rtp.rptdesigner.datasetproperties.parameters.f1
ms.assetid: 43b00aab-e2c3-4e85-abe1-a2b5a21efeed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0073971de373321ce347f416657671e1f497dd1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710250"
---
# <a name="dataset-properties-dialog-box-parameters"></a><span data-ttu-id="10968-102">資料集屬性對話方塊、參數</span><span class="sxs-lookup"><span data-stu-id="10968-102">Dataset Properties Dialog Box, Parameters</span></span>
  <span data-ttu-id="10968-103">選取 **[資料集屬性]** 對話方塊上的 **[參數]** 來加入、變更與刪除查詢參數，包括連結到報表參數的查詢參數。</span><span class="sxs-lookup"><span data-stu-id="10968-103">Select **Parameters** on the **Dataset Properties** dialog box to add, change, and delete query parameters, including query parameters that link to report parameters.</span></span>  
  
 <span data-ttu-id="10968-104">每當在查詢索引標籤上變更查詢時，系統就會剖析查詢命令。</span><span class="sxs-lookup"><span data-stu-id="10968-104">Whenever the query is changed on the query tab, the query command is parsed.</span></span> <span data-ttu-id="10968-105">系統會針對已識別的每個查詢參數，建立含有相同之區分大小寫名稱的報表參數。</span><span class="sxs-lookup"><span data-stu-id="10968-105">For each query parameter that is identified, a report parameter with an identical case-sensitive name is created.</span></span> <span data-ttu-id="10968-106">根據預設，系統會將查詢參數自動加入到查詢參數清單中，並連結到對應的報表參數。</span><span class="sxs-lookup"><span data-stu-id="10968-106">By default, the query parameter is automatically added to the query parameter list and linked to the corresponding report parameter.</span></span>  
  
 <span data-ttu-id="10968-107">如果有一個報表參數的預設值相依於另一個連結到查詢參數的報表參數，報表參數的順序 (出現在 [報表參數屬性]  對話方塊中的順序) 很重要。</span><span class="sxs-lookup"><span data-stu-id="10968-107">If there are dependencies for the default values of one report parameter on another report parameter that is linked to a query parameter, the order of report parameters (as they appear in the **Report Parameters Properties** dialog box) is important.</span></span> <span data-ttu-id="10968-108">稍後在清單中的報表參數可以參照先前在清單中的報表參數。</span><span class="sxs-lookup"><span data-stu-id="10968-108">Report parameters later in the list can refer to report parameters earlier in the list.</span></span> <span data-ttu-id="10968-109">如需報表參數的詳細資訊，請參閱 [報表參數 &#40;報表產生器和報表設計師&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="10968-109">For more information about report parameters, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="10968-110">選項。</span><span class="sxs-lookup"><span data-stu-id="10968-110">Options</span></span>  
 <span data-ttu-id="10968-111">**加入**</span><span class="sxs-lookup"><span data-stu-id="10968-111">**Add**</span></span>  
 <span data-ttu-id="10968-112">將新的參數加入到清單中。</span><span class="sxs-lookup"><span data-stu-id="10968-112">Add a new parameter to the list.</span></span>  
  
 <span data-ttu-id="10968-113">**刪除**</span><span class="sxs-lookup"><span data-stu-id="10968-113">**Delete**</span></span>  
 <span data-ttu-id="10968-114">從清單中移除選取的參數。</span><span class="sxs-lookup"><span data-stu-id="10968-114">Remove the selected parameter from the list.</span></span>  
  
 <span data-ttu-id="10968-115">**參數名稱**</span><span class="sxs-lookup"><span data-stu-id="10968-115">**Parameter name**</span></span>  
 <span data-ttu-id="10968-116">在 [資料集屬性] 對話方塊的 [查詢] 索引標籤上，輸入您要加入到資料集之查詢參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="10968-116">Type the name of a query parameter that you added to the dataset on the **Query** tab of the **Dataset Properties** dialog box.</span></span>  
  
 <span data-ttu-id="10968-117">**參數值**</span><span class="sxs-lookup"><span data-stu-id="10968-117">**Parameter value**</span></span>  
 <span data-ttu-id="10968-118">輸入查詢參數的值。</span><span class="sxs-lookup"><span data-stu-id="10968-118">Enter a value for the query parameter.</span></span> <span data-ttu-id="10968-119">這可為靜態值或參考報表內之物件的運算式，但是它不可以參考任何報表項目或欄位。</span><span class="sxs-lookup"><span data-stu-id="10968-119">This can be a static value or an expression that refers to an object within the report, but it cannot refer to any report items or fields.</span></span> <span data-ttu-id="10968-120">根據預設， **[值]** 包含指向報表參數的運算式。</span><span class="sxs-lookup"><span data-stu-id="10968-120">By default, **Value** contains an expression that points to a report parameter.</span></span>  
  
 <span data-ttu-id="10968-121">**向上箭頭**</span><span class="sxs-lookup"><span data-stu-id="10968-121">**Up arrow**</span></span>  
 <span data-ttu-id="10968-122">將清單中所選取的參數向上移動。</span><span class="sxs-lookup"><span data-stu-id="10968-122">Move the selected parameter up in the list.</span></span>  
  
 <span data-ttu-id="10968-123">**向下箭頭**</span><span class="sxs-lookup"><span data-stu-id="10968-123">**Down arrow**</span></span>  
 <span data-ttu-id="10968-124">將清單中所選取的參數向下移動。</span><span class="sxs-lookup"><span data-stu-id="10968-124">Move the selected parameter down in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10968-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10968-125">See Also</span></span>  
 <span data-ttu-id="10968-126">[報表參數 &#40;報表產生器和報表設計師&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="10968-126">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="10968-127">[將資料加入報表 &#40;報表產生器和 SSRS&#41;](report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="10968-127">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) </span></span>  
 [<span data-ttu-id="10968-128">變更報表參數的順序 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="10968-128">Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;</span></span>](../report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)  
  
  
