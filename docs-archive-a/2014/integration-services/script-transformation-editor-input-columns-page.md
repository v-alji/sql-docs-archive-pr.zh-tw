---
title: 腳本轉換編輯器 (輸入資料行頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.inputcolumn.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: d6e4ce84-3335-48e6-82d3-1c359ed87f63
author: chugugrace
ms.author: chugu
ms.openlocfilehash: daffb52b62ad59ae4fe574d7fa27d4820b9cb5a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687038"
---
# <a name="script-transformation-editor-input-columns-page"></a><span data-ttu-id="0f55a-102">指令碼轉換編輯器 (輸入資料行頁面)</span><span class="sxs-lookup"><span data-stu-id="0f55a-102">Script Transformation Editor (Input Columns Page)</span></span>
  <span data-ttu-id="0f55a-103">使用 [指令碼轉換編輯器] 對話方塊的 [輸入資料行] 頁面，對輸入資料行設定屬性。</span><span class="sxs-lookup"><span data-stu-id="0f55a-103">Use the **Input Columns** page of the **Script Transformation Editor** dialog box to set properties on input columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f55a-104">針對來源元件不會顯示 [輸入資料行]  頁面，因為來源元件只有輸出沒有輸入。</span><span class="sxs-lookup"><span data-stu-id="0f55a-104">The **Input Columns** page is not displayed for Source components, which have outputs but no inputs.</span></span>  
  
 <span data-ttu-id="0f55a-105">若要深入了解指令碼元件，請參閱＜ [Script Component](data-flow/transformations/script-component.md) ＞和＜ [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)＞。</span><span class="sxs-lookup"><span data-stu-id="0f55a-105">To learn more about the Script component, see [Script Component](data-flow/transformations/script-component.md) and [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span> <span data-ttu-id="0f55a-106">若要了解如何以程式設計方式編寫指令碼元件，請參閱＜ [以指令碼元件來擴充資料流程](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)＞。</span><span class="sxs-lookup"><span data-stu-id="0f55a-106">To learn about programming the Script component, see [Extending the Data Flow with the Script Component](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0f55a-107">選項。</span><span class="sxs-lookup"><span data-stu-id="0f55a-107">Options</span></span>  
 <span data-ttu-id="0f55a-108">**輸入名稱**</span><span class="sxs-lookup"><span data-stu-id="0f55a-108">**Input name**</span></span>  
 <span data-ttu-id="0f55a-109">從可用輸入的清單中選取。</span><span class="sxs-lookup"><span data-stu-id="0f55a-109">Select from the list of available inputs.</span></span>  
  
 <span data-ttu-id="0f55a-110">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="0f55a-110">**Available Input Columns**</span></span>  
 <span data-ttu-id="0f55a-111">利用核取方塊來指定指令碼轉換所使用的資料行。</span><span class="sxs-lookup"><span data-stu-id="0f55a-111">Using the check boxes, specify the columns that the script transformation will use.</span></span>  
  
 <span data-ttu-id="0f55a-112">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="0f55a-112">**Input Column**</span></span>  
 <span data-ttu-id="0f55a-113">從每個資料列的可用輸入資料行清單中選取。</span><span class="sxs-lookup"><span data-stu-id="0f55a-113">Select from the list of available input columns for each row.</span></span> <span data-ttu-id="0f55a-114">您的選擇會反映在 [可用的輸入資料行]  資料表的核取方塊選擇中。</span><span class="sxs-lookup"><span data-stu-id="0f55a-114">Your selections are reflected in the check box selections in the **Available Input Columns**table.</span></span>  
  
 <span data-ttu-id="0f55a-115">**輸出別名**</span><span class="sxs-lookup"><span data-stu-id="0f55a-115">**Output Alias**</span></span>  
 <span data-ttu-id="0f55a-116">輸入每一個輸出資料行的別名。</span><span class="sxs-lookup"><span data-stu-id="0f55a-116">Type an alias for each output column.</span></span> <span data-ttu-id="0f55a-117">預設是輸入資料行的名稱；但是，您可以選擇任何唯一的、描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="0f55a-117">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="0f55a-118">**使用類型**</span><span class="sxs-lookup"><span data-stu-id="0f55a-118">**Usage Type**</span></span>  
 <span data-ttu-id="0f55a-119">指定指令碼轉換是否要將每個資料行設定為 `ReadOnly` 或是 `ReadWrite`。</span><span class="sxs-lookup"><span data-stu-id="0f55a-119">Specify whether the Script Transformation will treat each column as `ReadOnly` or `ReadWrite`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f55a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f55a-120">See Also</span></span>  
 <span data-ttu-id="0f55a-121">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0f55a-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="0f55a-122">[選取腳本元件類型](../../2014/integration-services/select-script-component-type.md) </span><span class="sxs-lookup"><span data-stu-id="0f55a-122">[Select Script Component Type](../../2014/integration-services/select-script-component-type.md) </span></span>  
 <span data-ttu-id="0f55a-123">[[腳本轉換編輯器] &#40;[輸入和輸出] 頁面&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md) </span><span class="sxs-lookup"><span data-stu-id="0f55a-123">[Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md) </span></span>  
 <span data-ttu-id="0f55a-124">[腳本轉換編輯器 &#40;腳本頁面&#41;](../../2014/integration-services/script-transformation-editor-script-page.md) </span><span class="sxs-lookup"><span data-stu-id="0f55a-124">[Script Transformation Editor &#40;Script Page&#41;](../../2014/integration-services/script-transformation-editor-script-page.md) </span></span>  
 <span data-ttu-id="0f55a-125">[[腳本轉換編輯器] &#40;[連接管理員] 頁面&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span><span class="sxs-lookup"><span data-stu-id="0f55a-125">[Script Transformation Editor &#40;Connection Managers Page&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span></span>  
 [<span data-ttu-id="0f55a-126">額外的指令碼元件範例</span><span class="sxs-lookup"><span data-stu-id="0f55a-126">Additional Script Component Examples</span></span>](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
