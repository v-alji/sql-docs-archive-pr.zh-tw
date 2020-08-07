---
title: ODBC 來源編輯器 (錯誤輸出頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.errorhandling.f1
ms.assetid: b2f6866c-db07-4cb3-9f38-889f8d2b03e6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a8e169875a26efbe0a7f1ac3d06856b393266eb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703182"
---
# <a name="odbc-source-editor-error-output-page"></a><span data-ttu-id="98b46-102">ODBC 來源編輯器 (錯誤輸出頁面)</span><span class="sxs-lookup"><span data-stu-id="98b46-102">ODBC Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="98b46-103">使用 **[ODBC 來源編輯器]** 對話方塊的 **[錯誤輸出]** 頁面，即可選取錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="98b46-103">Use the **Error Output** page of the **ODBC Source Editor** dialog box to select error handling options.</span></span>  
  
 <span data-ttu-id="98b46-104">若要了解有關 ODBC 來源的詳細資訊，請參閱＜ [CDC Source](data-flow/cdc-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="98b46-104">To learn more about the ODBC source, see [CDC Source](data-flow/cdc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="98b46-105">工作清單</span><span class="sxs-lookup"><span data-stu-id="98b46-105">Task List</span></span>  
 <span data-ttu-id="98b46-106">**若要開啟 ODBC 來源編輯器的錯誤輸出頁面**</span><span class="sxs-lookup"><span data-stu-id="98b46-106">**To open the ODBC Source Editor Error Output Page**</span></span>  
  
-   <span data-ttu-id="98b46-107">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，開啟具有 ODBC 來源的 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="98b46-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the ODBC source.</span></span>  
  
-   <span data-ttu-id="98b46-108">在 [資料流程]\*\*\*\* 索引標籤上，按兩下 ODBC 來源。</span><span class="sxs-lookup"><span data-stu-id="98b46-108">On the **Data Flow** tab, double-click the ODBC source.</span></span>  
  
-   <span data-ttu-id="98b46-109">在 **[ODBC 來源編輯器]** 中，按一下 **[錯誤輸出]**。</span><span class="sxs-lookup"><span data-stu-id="98b46-109">In the **ODBC Source Editor**, click **Error Output**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="98b46-110">選項。</span><span class="sxs-lookup"><span data-stu-id="98b46-110">Options</span></span>  
  
### <a name="inputoutput"></a><span data-ttu-id="98b46-111">輸入/輸出</span><span class="sxs-lookup"><span data-stu-id="98b46-111">Input/Output</span></span>  
 <span data-ttu-id="98b46-112">檢視資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="98b46-112">View the name of the data source.</span></span>  
  
### <a name="column"></a><span data-ttu-id="98b46-113">資料行</span><span class="sxs-lookup"><span data-stu-id="98b46-113">Column</span></span>  
 <span data-ttu-id="98b46-114">未使用。</span><span class="sxs-lookup"><span data-stu-id="98b46-114">Not used.</span></span>  
  
### <a name="error"></a><span data-ttu-id="98b46-115">錯誤</span><span class="sxs-lookup"><span data-stu-id="98b46-115">Error</span></span>  
 <span data-ttu-id="98b46-116">選取 ODBC 來源應該如何處理流程中的錯誤：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="98b46-116">Select how the ODBC source should handle errors in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
### <a name="truncation"></a><span data-ttu-id="98b46-117">截斷</span><span class="sxs-lookup"><span data-stu-id="98b46-117">Truncation</span></span>  
 <span data-ttu-id="98b46-118">選取 ODBC 來源應該如何處理流程中的截斷：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="98b46-118">Select how the ODBC source should handle truncation in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
### <a name="description"></a><span data-ttu-id="98b46-119">說明</span><span class="sxs-lookup"><span data-stu-id="98b46-119">Description</span></span>  
 <span data-ttu-id="98b46-120">未使用。</span><span class="sxs-lookup"><span data-stu-id="98b46-120">Not used.</span></span>  
  
### <a name="set-this-value-to-selected-cells"></a><span data-ttu-id="98b46-121">將這個值設定到選取的資料格</span><span class="sxs-lookup"><span data-stu-id="98b46-121">Set this value to selected cells</span></span>  
 <span data-ttu-id="98b46-122">選取發生錯誤或截斷時 ODBC 來源如何處理所有選取的資料格：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="98b46-122">Select how the ODBC source handles all selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
### <a name="apply"></a><span data-ttu-id="98b46-123">套用</span><span class="sxs-lookup"><span data-stu-id="98b46-123">Apply</span></span>  
 <span data-ttu-id="98b46-124">將錯誤處理選項套用至選取的資料格。</span><span class="sxs-lookup"><span data-stu-id="98b46-124">Apply the error handling options to the selected cells.</span></span>  
  
## <a name="error-handling-options"></a><span data-ttu-id="98b46-125">錯誤處理選項</span><span class="sxs-lookup"><span data-stu-id="98b46-125">Error Handling Options</span></span>  
 <span data-ttu-id="98b46-126">您可以使用下列選項來設定 ODBC 來源處理錯誤和截斷的方式。</span><span class="sxs-lookup"><span data-stu-id="98b46-126">You use the following options to configure how the ODBC source handles errors and truncations.</span></span>  
  
### <a name="fail-component"></a><span data-ttu-id="98b46-127">失敗元件</span><span class="sxs-lookup"><span data-stu-id="98b46-127">Fail Component</span></span>  
 <span data-ttu-id="98b46-128">當發生錯誤或截斷時，資料流程工作將失敗。</span><span class="sxs-lookup"><span data-stu-id="98b46-128">The Data Flow task fails when an error or a truncation occurs.</span></span> <span data-ttu-id="98b46-129">此為預設行為。</span><span class="sxs-lookup"><span data-stu-id="98b46-129">This is the default behavior.</span></span>  
  
### <a name="ignore-failure"></a><span data-ttu-id="98b46-130">忽略失敗</span><span class="sxs-lookup"><span data-stu-id="98b46-130">Ignore Failure</span></span>  
 <span data-ttu-id="98b46-131">忽略錯誤或截斷。</span><span class="sxs-lookup"><span data-stu-id="98b46-131">The error or the truncation is ignored.</span></span>  
  
### <a name="redirect-flow"></a><span data-ttu-id="98b46-132">重新導向流程</span><span class="sxs-lookup"><span data-stu-id="98b46-132">Redirect Flow</span></span>  
 <span data-ttu-id="98b46-133">導致錯誤或截斷的資料列會導向至 ODBC 來源的錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="98b46-133">The row that is causing the error or the truncation is directed to the error output of the ODBC source.</span></span> <span data-ttu-id="98b46-134">如需相關資訊，請參閱 [ODBC Source](data-flow/odbc-source.md)。</span><span class="sxs-lookup"><span data-stu-id="98b46-134">For more information, see [ODBC Source](data-flow/odbc-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98b46-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98b46-135">See Also</span></span>  
 <span data-ttu-id="98b46-136">[ODBC 來源編輯器 &#40;連線管理員頁面&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="98b46-136">[ODBC Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="98b46-137">ODBC 來源編輯器 &#40;資料行頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="98b46-137">ODBC Source Editor &#40;Columns Page&#41;</span></span>](../../2014/integration-services/odbc-source-editor-columns-page.md)  
  
  
