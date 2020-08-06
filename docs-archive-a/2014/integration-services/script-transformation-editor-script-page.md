---
title: 腳本轉換編輯器 (腳本頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.script.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: 4c6d1901-ef21-4aa7-9d0a-6bbeb7fadf1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df89bddd0a2f12e1d0efe0db74f4e10aadd772eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596083"
---
# <a name="script-transformation-editor-script-page"></a><span data-ttu-id="a182b-102">指令碼轉換編輯器 (指令碼頁面)</span><span class="sxs-lookup"><span data-stu-id="a182b-102">Script Transformation Editor (Script Page)</span></span>
  <span data-ttu-id="a182b-103">使用 **[指令碼轉換編輯器]** 對話方塊的 **[指令碼]** 索引標籤，來指定指令碼和相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="a182b-103">Use the **Script** tab of the **Script Transformation Editor** dialog box to specify a script and related properties.</span></span>  
  
 <span data-ttu-id="a182b-104">若要深入了解指令碼元件，請參閱＜ [Script Component](data-flow/transformations/script-component.md) ＞和＜ [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a182b-104">To learn more about the Script component, see [Script Component](data-flow/transformations/script-component.md) and [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span> <span data-ttu-id="a182b-105">若要了解如何以程式設計方式編寫指令碼元件，請參閱＜ [以指令碼元件來擴充資料流程](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a182b-105">To learn about programming the Script component, see [Extending the Data Flow with the Script Component](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a182b-106">選項。</span><span class="sxs-lookup"><span data-stu-id="a182b-106">Options</span></span>  
 <span data-ttu-id="a182b-107">**屬性**</span><span class="sxs-lookup"><span data-stu-id="a182b-107">**Properties**</span></span>  
 <span data-ttu-id="a182b-108">檢視和修改指令碼轉換的屬性。</span><span class="sxs-lookup"><span data-stu-id="a182b-108">View and modify the properties of the Script transformation.</span></span> <span data-ttu-id="a182b-109">顯示的許多屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="a182b-109">Many of the properties displayed are read-only.</span></span> <span data-ttu-id="a182b-110">您可以修改下列屬性：</span><span class="sxs-lookup"><span data-stu-id="a182b-110">You can modify the following properties:</span></span>  
  
|<span data-ttu-id="a182b-111">值</span><span class="sxs-lookup"><span data-stu-id="a182b-111">Value</span></span>|<span data-ttu-id="a182b-112">描述</span><span class="sxs-lookup"><span data-stu-id="a182b-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a182b-113">**說明**</span><span class="sxs-lookup"><span data-stu-id="a182b-113">**Description**</span></span>|<span data-ttu-id="a182b-114">以其用途來描述指令碼轉換。</span><span class="sxs-lookup"><span data-stu-id="a182b-114">Describe the script transformation in terms of its purpose.</span></span>|  
|<span data-ttu-id="a182b-115">**LocaleID**</span><span class="sxs-lookup"><span data-stu-id="a182b-115">**LocaleID**</span></span>|<span data-ttu-id="a182b-116">指定地區設定以提供排序和日期和時間轉換的特定區域資訊。</span><span class="sxs-lookup"><span data-stu-id="a182b-116">Specify the locale to provide region-specific information for ordering, and for date and time conversion.</span></span>|  
|<span data-ttu-id="a182b-117">**名稱**</span><span class="sxs-lookup"><span data-stu-id="a182b-117">**Name**</span></span>|<span data-ttu-id="a182b-118">輸入元件的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="a182b-118">Type a descriptive name for the component.</span></span>|  
|<span data-ttu-id="a182b-119">**ValidateExternalMetadata**</span><span class="sxs-lookup"><span data-stu-id="a182b-119">**ValidateExternalMetadata**</span></span>|<span data-ttu-id="a182b-120">指出指令碼轉換在設計階段是否對外部資料來源驗證資料行中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a182b-120">Indicate whether the Script transformation validates column metadata against external data sources at design time.</span></span> <span data-ttu-id="a182b-121">`false` 的值將會延遲到執行時間才驗證。</span><span class="sxs-lookup"><span data-stu-id="a182b-121">A value of `false` delays validation until the time of execution.</span></span>|  
|<span data-ttu-id="a182b-122">**ReadOnlyVariables**</span><span class="sxs-lookup"><span data-stu-id="a182b-122">**ReadOnlyVariables**</span></span>|<span data-ttu-id="a182b-123">輸入以逗號分隔的變數清單，以供指令碼轉換進行唯讀存取。</span><span class="sxs-lookup"><span data-stu-id="a182b-123">Type a comma-separated list of variables for read-only access by the Script transformation.</span></span><br /><br /> <span data-ttu-id="a182b-124">注意：變數名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="a182b-124">Note: Variable names are case-sensitive.</span></span>|  
|<span data-ttu-id="a182b-125">**ReadWriteVariables**</span><span class="sxs-lookup"><span data-stu-id="a182b-125">**ReadWriteVariables**</span></span>|<span data-ttu-id="a182b-126">輸入以逗號分隔的變數清單，以供指令碼轉換進行可讀寫存取。</span><span class="sxs-lookup"><span data-stu-id="a182b-126">Type a comma-separated list of variables for read/write access by the Script transformation.</span></span><br /><br /> <span data-ttu-id="a182b-127">注意：變數名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="a182b-127">Note: Variable names are case-sensitive.</span></span>|  
|<span data-ttu-id="a182b-128">**ScriptLanguage**</span><span class="sxs-lookup"><span data-stu-id="a182b-128">**ScriptLanguage**</span></span>|<span data-ttu-id="a182b-129">選取指令碼元件所要使用的指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="a182b-129">Select the script language to be used by the Script component.</span></span><br /><br /> <span data-ttu-id="a182b-130">若要為指令碼元件和指令碼工作設定預設指令碼語言，請使用 **[選項]** 對話方塊上 **[一般]** 頁面上的 **[指令碼語言]** 選項。</span><span class="sxs-lookup"><span data-stu-id="a182b-130">To set the default script language for Script components and Script tasks, use the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="a182b-131">如需相關資訊，請參閱 [General Page](general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="a182b-131">For more information, see [General Page](general-page-of-integration-services-designers-options.md).</span></span>|  
|<span data-ttu-id="a182b-132">**UserComponentTypeName**</span><span class="sxs-lookup"><span data-stu-id="a182b-132">**UserComponentTypeName**</span></span>|<span data-ttu-id="a182b-133">指定支援 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 基礎結構的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost> 類別和 `Microsoft.SqlServer.TxScript` 組件。</span><span class="sxs-lookup"><span data-stu-id="a182b-133">Specifies the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost> class and the `Microsoft.SqlServer.TxScript` assembly that support the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] infrastructure.</span></span>|  
  
 <span data-ttu-id="a182b-134">**編輯指令碼**</span><span class="sxs-lookup"><span data-stu-id="a182b-134">**Edit Script**</span></span>  
 <span data-ttu-id="a182b-135">使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) 來建立或修改指令碼。</span><span class="sxs-lookup"><span data-stu-id="a182b-135">Use [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) to create or modify a script.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a182b-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a182b-136">See Also</span></span>  
 <span data-ttu-id="a182b-137">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a182b-137">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="a182b-138">[選取腳本元件類型](../../2014/integration-services/select-script-component-type.md) </span><span class="sxs-lookup"><span data-stu-id="a182b-138">[Select Script Component Type](../../2014/integration-services/select-script-component-type.md) </span></span>  
 <span data-ttu-id="a182b-139">[腳本轉換編輯器 &#40;輸入資料行頁面&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="a182b-139">[Script Transformation Editor &#40;Input Columns Page&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md) </span></span>  
 <span data-ttu-id="a182b-140">[[腳本轉換編輯器] &#40;[輸入和輸出] 頁面&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md) </span><span class="sxs-lookup"><span data-stu-id="a182b-140">[Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md) </span></span>  
 <span data-ttu-id="a182b-141">[[腳本轉換編輯器] &#40;[連接管理員] 頁面&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span><span class="sxs-lookup"><span data-stu-id="a182b-141">[Script Transformation Editor &#40;Connection Managers Page&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span></span>  
 [<span data-ttu-id="a182b-142">額外的指令碼元件範例</span><span class="sxs-lookup"><span data-stu-id="a182b-142">Additional Script Component Examples</span></span>](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
