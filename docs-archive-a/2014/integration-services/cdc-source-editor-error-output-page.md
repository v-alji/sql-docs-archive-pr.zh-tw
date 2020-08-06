---
title: CDC 來源編輯器 (錯誤輸出頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.errorhandling.f1
ms.assetid: 8a4c2cb8-fd2f-4c45-824f-b93473a8981e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b39532304fddfa90fabe8cafe2a6caf5b1fb5c8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599629"
---
# <a name="cdc-source-editor-error-output-page"></a><span data-ttu-id="fd9ed-102">CDC 來源編輯器 (錯誤輸出頁面)</span><span class="sxs-lookup"><span data-stu-id="fd9ed-102">CDC Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="fd9ed-103">使用 [CDC 來源編輯器]  對話方塊的 [錯誤輸出]  頁面，即可選取錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-103">Use the **Error Output** page of the **CDC Source Editor** dialog box to select error handling options.</span></span>  
  
 <span data-ttu-id="fd9ed-104">若要了解有關 CDC 來源的詳細資訊，請參閱＜ [CDC Source](data-flow/cdc-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-104">To learn more about the CDC source, see [CDC Source](data-flow/cdc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="fd9ed-105">工作清單</span><span class="sxs-lookup"><span data-stu-id="fd9ed-105">Task List</span></span>  
 <span data-ttu-id="fd9ed-106">**若要開啟 CDC 來源編輯器的錯誤輸出頁面**</span><span class="sxs-lookup"><span data-stu-id="fd9ed-106">**To open the CDC Source Editor Error Output Page**</span></span>  
  
1.  <span data-ttu-id="fd9ed-107">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，開啟具有 CDC 來源的 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the CDC source.</span></span>  
  
2.  <span data-ttu-id="fd9ed-108">在 [資料流程]  索引標籤中，按兩下 CDC 來源。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-108">On the **Data Flow** tab, double-click the CDC source.</span></span>  
  
3.  <span data-ttu-id="fd9ed-109">在 [CDC 來源編輯器]  中，按一下 [錯誤輸出]  。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-109">In the **CDC Source Editor**, click **Error Output**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fd9ed-110">選項。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-110">Options</span></span>  
 <span data-ttu-id="fd9ed-111">**輸入/輸出**</span><span class="sxs-lookup"><span data-stu-id="fd9ed-111">**Input/Output**</span></span>  
 <span data-ttu-id="fd9ed-112">檢視資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-112">View the name of the data source.</span></span>  
  
 <span data-ttu-id="fd9ed-113">**資料行**</span><span class="sxs-lookup"><span data-stu-id="fd9ed-113">**Column**</span></span>  
 <span data-ttu-id="fd9ed-114">檢視您在 [CDC 來源編輯器]  對話方塊的 [連線管理員]  頁面上所選取的外部 (來源) 資料行。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-114">View the external (source) columns that you selected on the **Connection Manager** page of the **CDC Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="fd9ed-115">**錯誤**</span><span class="sxs-lookup"><span data-stu-id="fd9ed-115">**Error**</span></span>  
 <span data-ttu-id="fd9ed-116">選取 CDC 來源應該如何處理流程中的錯誤：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-116">Select how the CDC source should handle errors in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="fd9ed-117">**截斷**</span><span class="sxs-lookup"><span data-stu-id="fd9ed-117">**Truncation**</span></span>  
 <span data-ttu-id="fd9ed-118">選取 CDC 來源應該如何處理流程中的截斷：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-118">Select how the CDC source should handle truncation in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="fd9ed-119">**說明**</span><span class="sxs-lookup"><span data-stu-id="fd9ed-119">**Description**</span></span>  
 <span data-ttu-id="fd9ed-120">未使用。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-120">Not used.</span></span>  
  
 <span data-ttu-id="fd9ed-121">**將這個值設定到選取的資料格**</span><span class="sxs-lookup"><span data-stu-id="fd9ed-121">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="fd9ed-122">選取發生錯誤或截斷時 CDC 來源如何處理所有選取的資料格：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-122">Select how the CDC source handles all selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="fd9ed-123">**套用**</span><span class="sxs-lookup"><span data-stu-id="fd9ed-123">**Apply**</span></span>  
 <span data-ttu-id="fd9ed-124">將錯誤處理選項套用至選取的資料格。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-124">Apply the error handling options to the selected cells.</span></span>  
  
## <a name="error-handling-options"></a><span data-ttu-id="fd9ed-125">錯誤處理選項</span><span class="sxs-lookup"><span data-stu-id="fd9ed-125">Error Handling Options</span></span>  
 <span data-ttu-id="fd9ed-126">您可以使用下列選項來設定 CDC 來源處理錯誤和截斷的方式。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-126">You use the following options to configure how the CDC source handles errors and truncations.</span></span>  
  
 <span data-ttu-id="fd9ed-127">**失敗元件**</span><span class="sxs-lookup"><span data-stu-id="fd9ed-127">**Fail Component**</span></span>  
 <span data-ttu-id="fd9ed-128">當發生錯誤或截斷時，資料流程工作將失敗。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-128">The Data Flow task fails when an error or a truncation occurs.</span></span> <span data-ttu-id="fd9ed-129">此為預設行為。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-129">This is the default behavior.</span></span>  
  
 <span data-ttu-id="fd9ed-130">**忽略失敗**</span><span class="sxs-lookup"><span data-stu-id="fd9ed-130">**Ignore Failure**</span></span>  
 <span data-ttu-id="fd9ed-131">系統會忽略錯誤或截斷，並將資料列導向至 CDC 來源輸出。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-131">The error or the truncation is ignored and the data row is directed to the CDC source output.</span></span>  
  
 <span data-ttu-id="fd9ed-132">**重新導向流程**</span><span class="sxs-lookup"><span data-stu-id="fd9ed-132">**Redirect Flow**</span></span>  
 <span data-ttu-id="fd9ed-133">系統會將錯誤或截斷資料列導向至 CDC 來源的錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-133">The error or the truncation data row is directed to the error output of the CDC source.</span></span> <span data-ttu-id="fd9ed-134">在此情況中，就會使用 CDC 來源錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-134">In this case the CDC source error handling is used.</span></span> <span data-ttu-id="fd9ed-135">如需詳細資訊，請參閱 [CDC 來源](data-flow/cdc-source.md)。</span><span class="sxs-lookup"><span data-stu-id="fd9ed-135">For more information, see [CDC Source](data-flow/cdc-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd9ed-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd9ed-136">See Also</span></span>  
 <span data-ttu-id="fd9ed-137">[CDC 來源編輯器 &#40;連線管理員頁面&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="fd9ed-137">[CDC Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="fd9ed-138">CDC 來源編輯器 &#40;資料行頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="fd9ed-138">CDC Source Editor &#40;Columns Page&#41;</span></span>](../../2014/integration-services/cdc-source-editor-columns-page.md)  
  
  
