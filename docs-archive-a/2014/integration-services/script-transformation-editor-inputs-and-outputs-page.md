---
title: 腳本轉換編輯器 (輸入和輸出頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.columnproperties.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: 9659d2d2-5d73-4470-9768-e07b77142fc9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 16adf74a1cd8f0c778bc18eaff84437b8fc13603
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687036"
---
# <a name="script-transformation-editor-inputs-and-outputs-page"></a><span data-ttu-id="ea540-102">指令碼轉換編輯器 (輸入及輸出頁面)</span><span class="sxs-lookup"><span data-stu-id="ea540-102">Script Transformation Editor (Inputs and Outputs Page)</span></span>
  <span data-ttu-id="ea540-103">使用 **[指令碼轉換編輯器]** 對話方塊的 **[輸入及輸出]** 頁面，即可加入、移除和設定指令碼轉換的輸入及輸出。</span><span class="sxs-lookup"><span data-stu-id="ea540-103">Use the **Inputs and Outputs** page of the **Script Transformation Editor** dialog box to add, remove, and configure inputs and outputs for the Script Transformation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ea540-104">來源元件會有輸出但沒有輸入，而目的地元件會有輸入但沒有輸出。</span><span class="sxs-lookup"><span data-stu-id="ea540-104">Source components have outputs and no inputs, while destination components have inputs but no outputs.</span></span> <span data-ttu-id="ea540-105">轉換則同時具有輸入和輸出。</span><span class="sxs-lookup"><span data-stu-id="ea540-105">Transformations have both inputs and outputs.</span></span>  
  
 <span data-ttu-id="ea540-106">若要深入了解指令碼元件，請參閱＜ [Script Component](data-flow/transformations/script-component.md) ＞和＜ [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ea540-106">To learn more about the Script component, see [Script Component](data-flow/transformations/script-component.md) and [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span> <span data-ttu-id="ea540-107">若要了解如何以程式設計方式編寫指令碼元件，請參閱＜ [以指令碼元件來擴充資料流程](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ea540-107">To learn about programming the Script component, see [Extending the Data Flow with the Script Component](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ea540-108">選項。</span><span class="sxs-lookup"><span data-stu-id="ea540-108">Options</span></span>  
 <span data-ttu-id="ea540-109">**Inputs and outputs**</span><span class="sxs-lookup"><span data-stu-id="ea540-109">**Inputs and outputs**</span></span>  
 <span data-ttu-id="ea540-110">在左方選取輸入及輸出，即可在右方檢視其在資料表中的屬性。</span><span class="sxs-lookup"><span data-stu-id="ea540-110">Select an input or output on the left to view its properties in the table on the right.</span></span> <span data-ttu-id="ea540-111">可用於編輯的屬性會根據選取範圍而有所不同。</span><span class="sxs-lookup"><span data-stu-id="ea540-111">Properties available for editing vary according to the selection.</span></span> <span data-ttu-id="ea540-112">顯示的許多屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="ea540-112">Many of the properties displayed are read-only.</span></span> <span data-ttu-id="ea540-113">如需個別屬性的詳細資訊，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="ea540-113">For more information on the individual properties, see the following topics.</span></span>  
  
 [<span data-ttu-id="ea540-114">Common Properties</span><span class="sxs-lookup"><span data-stu-id="ea540-114">Common Properties</span></span>](../../2014/integration-services/common-properties.md)  
  
 [<span data-ttu-id="ea540-115">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="ea540-115">Transformation Custom Properties</span></span>](data-flow/transformations/transformation-custom-properties.md)  
  
 <span data-ttu-id="ea540-116">**加入輸出**</span><span class="sxs-lookup"><span data-stu-id="ea540-116">**Add Output**</span></span>  
 <span data-ttu-id="ea540-117">將其他輸出加入到清單中。</span><span class="sxs-lookup"><span data-stu-id="ea540-117">Add an additional output to the list.</span></span>  
  
 <span data-ttu-id="ea540-118">**加入資料行**</span><span class="sxs-lookup"><span data-stu-id="ea540-118">**Add Column**</span></span>  
 <span data-ttu-id="ea540-119">選取要放置新輸出資料行的資料夾，再按一下 [加入資料行]  將其加入。</span><span class="sxs-lookup"><span data-stu-id="ea540-119">Select a folder in which to place the new output column, and then add the column by clicking **Add Column**.</span></span>  
  
 <span data-ttu-id="ea540-120">**移除輸出**</span><span class="sxs-lookup"><span data-stu-id="ea540-120">**Remove Output**</span></span>  
 <span data-ttu-id="ea540-121">選取輸出，然後按一下 [移除輸出]  將它移除。</span><span class="sxs-lookup"><span data-stu-id="ea540-121">Select an output, and then remove it by clicking **Remove Output**.</span></span>  
  
 <span data-ttu-id="ea540-122">**移除資料行**</span><span class="sxs-lookup"><span data-stu-id="ea540-122">**Remove Column**</span></span>  
 <span data-ttu-id="ea540-123">選取資料行，然後按一下 [移除資料行]  將它移除。</span><span class="sxs-lookup"><span data-stu-id="ea540-123">Select a column, and then remove it by clicking **Remove Column**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea540-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea540-124">See Also</span></span>  
 <span data-ttu-id="ea540-125">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ea540-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="ea540-126">[選取腳本元件類型](../../2014/integration-services/select-script-component-type.md) </span><span class="sxs-lookup"><span data-stu-id="ea540-126">[Select Script Component Type](../../2014/integration-services/select-script-component-type.md) </span></span>  
 <span data-ttu-id="ea540-127">[腳本轉換編輯器 &#40;輸入資料行頁面&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="ea540-127">[Script Transformation Editor &#40;Input Columns Page&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md) </span></span>  
 <span data-ttu-id="ea540-128">[腳本轉換編輯器 &#40;腳本頁面&#41;](../../2014/integration-services/script-transformation-editor-script-page.md) </span><span class="sxs-lookup"><span data-stu-id="ea540-128">[Script Transformation Editor &#40;Script Page&#41;](../../2014/integration-services/script-transformation-editor-script-page.md) </span></span>  
 <span data-ttu-id="ea540-129">[[腳本轉換編輯器] &#40;[連接管理員] 頁面&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span><span class="sxs-lookup"><span data-stu-id="ea540-129">[Script Transformation Editor &#40;Connection Managers Page&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span></span>  
 [<span data-ttu-id="ea540-130">額外的指令碼元件範例</span><span class="sxs-lookup"><span data-stu-id="ea540-130">Additional Script Component Examples</span></span>](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
