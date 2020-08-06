---
title: '[XML 工作編輯器] (一般頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmltask.general.f1
helpviewer_keywords:
- XML Task Editor
ms.assetid: b9622c48-3243-4408-a1de-9ba20e32ff70
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f73681a818d80c4e8b2755086e653e5c7e682f01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705238"
---
# <a name="xml-task-editor-general-page"></a><span data-ttu-id="1cb6c-102">XML Task Editor (General Page)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-102">XML Task Editor (General Page)</span></span>
  <span data-ttu-id="1cb6c-103">使用 **[XML 工作編輯器]** 對話方塊的 **[一般節點]** ，即可指定作業類型和設定作業。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-103">Use the **General Node** of the **XML Task Editor** dialog box to specify the operation type and configure the operation.</span></span>  
  
 <span data-ttu-id="1cb6c-104">若要了解這個工作，請參閱＜ [XML Task](control-flow/xml-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-104">To learn about this task, see [XML Task](control-flow/xml-task.md).</span></span> <span data-ttu-id="1cb6c-105">如需有關使用 XML 文件和資料的詳細資訊，請參閱 MSDN Library 中的 "[Employing XML in the .NET Framework](https://go.microsoft.com/fwlink/?LinkId=56214)"。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-105">For information about working with XML documents and data, see "[Employing XML in the .NET Framework](https://go.microsoft.com/fwlink/?LinkId=56214)" in the MSDN Library.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="1cb6c-106">靜態選項</span><span class="sxs-lookup"><span data-stu-id="1cb6c-106">Static Options</span></span>  
 <span data-ttu-id="1cb6c-107">**OperationType**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-107">**OperationType**</span></span>  
 <span data-ttu-id="1cb6c-108">從清單中選取作業類型。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-108">Select the operation type from the list.</span></span> <span data-ttu-id="1cb6c-109">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-109">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-110">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-110">Value</span></span>|<span data-ttu-id="1cb6c-111">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-111">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-112">**驗證**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-112">**Validate**</span></span>|<span data-ttu-id="1cb6c-113">針對「文件類型定義」(DTD) 或「XML 結構描述定義」(XSD) 結構描述來驗證 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-113">Validates the XML document against a Document Type Definition (DTD) or XML Schema definition (XSD) schema.</span></span> <span data-ttu-id="1cb6c-114">選取此選項會在 **[驗證]** 區段中顯示動態選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-114">Selecting this option displays the dynamic options in section, **Validate**.</span></span>|  
|<span data-ttu-id="1cb6c-115">**XSLT**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-115">**XSLT**</span></span>|<span data-ttu-id="1cb6c-116">在 XML 文件上執行 XSL 轉換。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-116">Performs XSL transformations on XML documents.</span></span> <span data-ttu-id="1cb6c-117">選取此選項會在 **[XSLT]** 區段中顯示動態選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-117">Selecting this option displays the dynamic options in section, **XSLT**.</span></span>|  
|<span data-ttu-id="1cb6c-118">**XPATH**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-118">**XPATH**</span></span>|<span data-ttu-id="1cb6c-119">執行 XPath 查詢和評估。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-119">Performs XPath queries and evaluations.</span></span> <span data-ttu-id="1cb6c-120">選取此選項會在 **[XPATH]** 區段中顯示動態選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-120">Selecting this option displays the dynamic options in section, **XPATH**.</span></span>|  
|<span data-ttu-id="1cb6c-121">**合併式**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-121">**Merge**</span></span>|<span data-ttu-id="1cb6c-122">合併兩份 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-122">Merges two XML documents.</span></span> <span data-ttu-id="1cb6c-123">選取此選項會在 **[合併]** 區段中顯示動態選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-123">Selecting this option displays the dynamic options in section, **Merge**.</span></span>|  
|<span data-ttu-id="1cb6c-124">**Diff**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-124">**Diff**</span></span>|<span data-ttu-id="1cb6c-125">比較兩份 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-125">Compares two XML documents.</span></span> <span data-ttu-id="1cb6c-126">選取此選項會在 **[Diff]** 區段中顯示動態選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-126">Selecting this option displays the dynamic options in section, **Diff**.</span></span>|  
|<span data-ttu-id="1cb6c-127">**修補**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-127">**Patch**</span></span>|<span data-ttu-id="1cb6c-128">套用 Diff 作業的輸出，以建立新文件。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-128">Applies the output from the Diff operation to create a new document.</span></span> <span data-ttu-id="1cb6c-129">選取此選項會在 **[修補]** 區段中顯示動態選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-129">Selecting this option displays the dynamic options in section, **Patch**.</span></span>|  
  
 <span data-ttu-id="1cb6c-130">**SourceType**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-130">**SourceType**</span></span>  
 <span data-ttu-id="1cb6c-131">選取 XML 文件的來源類型。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-131">Select the source type of the XML document.</span></span> <span data-ttu-id="1cb6c-132">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-132">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-133">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-133">Value</span></span>|<span data-ttu-id="1cb6c-134">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-135">**直接輸入**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-135">**Direct input**</span></span>|<span data-ttu-id="1cb6c-136">設定 XML 文件的來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-136">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="1cb6c-137">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-137">**File connection**</span></span>|<span data-ttu-id="1cb6c-138">選取包含 XML 文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-138">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="1cb6c-139">**變數**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-139">**Variable**</span></span>|<span data-ttu-id="1cb6c-140">設定包含 XML 文件的變數來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-140">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="1cb6c-141">**Source**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-141">**Source**</span></span>  
 <span data-ttu-id="1cb6c-142">如果 [Source]  設定為 [直接輸入]  ，請提供 XML 程式碼，或按一下省略符號按鈕 ([...])  ，然後使用 [文件來源編輯器]  對話方塊來提供 XML。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-142">If **Source** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="1cb6c-143">如果 [Source] 設定為 [檔案連線]，請選取檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-143">If **Source** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="1cb6c-144">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-144">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="1cb6c-145">如果 [Source] 設定為 [變數]，請選取現有的變數，或按一下 [\<New variable...>] 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-145">If **Source** is set to **Variable**, select an existing variable, or click **\<New variable...>** to create a new variable.</span></span>  
  
 <span data-ttu-id="1cb6c-146">**相關主題**：[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-146">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
## <a name="operationtype-dynamic-options"></a><span data-ttu-id="1cb6c-147">OperationType 動態選項</span><span class="sxs-lookup"><span data-stu-id="1cb6c-147">OperationType Dynamic Options</span></span>  
  
### <a name="operationtype--validate"></a><span data-ttu-id="1cb6c-148">OperationType = 驗證</span><span class="sxs-lookup"><span data-stu-id="1cb6c-148">OperationType = Validate</span></span>  
 <span data-ttu-id="1cb6c-149">指定驗證作業的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-149">Specify options for the Validate operation.</span></span>  
  
 <span data-ttu-id="1cb6c-150">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-150">**SaveOperationResult**</span></span>  
 <span data-ttu-id="1cb6c-151">指定 XML 工作是否儲存驗證作業的輸出。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-151">Specify whether the XML task saves the output of the Validate operation.</span></span>  
  
 <span data-ttu-id="1cb6c-152">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-152">**OverwriteDestination**</span></span>  
 <span data-ttu-id="1cb6c-153">指定是否要覆寫目的地檔案或變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-153">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="1cb6c-154">**目的地**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-154">**Destination**</span></span>  
 <span data-ttu-id="1cb6c-155">選取現有的檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-155">Select an existing File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="1cb6c-156">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-156">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="1cb6c-157">**DestinationType**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-157">**DestinationType**</span></span>  
 <span data-ttu-id="1cb6c-158">選取 XML 文件的目的地類型。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-158">Select the destination type of the XML document.</span></span> <span data-ttu-id="1cb6c-159">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-159">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-160">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-160">Value</span></span>|<span data-ttu-id="1cb6c-161">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-161">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-162">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-162">**File connection**</span></span>|<span data-ttu-id="1cb6c-163">選取包含 XML 文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-163">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="1cb6c-164">**變數**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-164">**Variable**</span></span>|<span data-ttu-id="1cb6c-165">設定包含 XML 文件的變數來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-165">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="1cb6c-166">**ValidationType**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-166">**ValidationType**</span></span>  
 <span data-ttu-id="1cb6c-167">選取驗證類型。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-167">Select the validation type.</span></span> <span data-ttu-id="1cb6c-168">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-168">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-169">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-169">Value</span></span>|<span data-ttu-id="1cb6c-170">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-170">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-171">**DTD**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-171">**DTD**</span></span>|<span data-ttu-id="1cb6c-172">使用文件類型定義 (DTD)。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-172">Use a Document Type Definition (DTD).</span></span>|  
|<span data-ttu-id="1cb6c-173">**XSD**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-173">**XSD**</span></span>|<span data-ttu-id="1cb6c-174">使用 XML 結構描述定義 (XSD) 結構描述。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-174">Use an XML Schema definition (XSD) schema.</span></span> <span data-ttu-id="1cb6c-175">選取此選項會在 **[ValidationType]** 區段中顯示動態選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-175">Selecting this option displays the dynamic options in section, **ValidationType**.</span></span>|  
  
 <span data-ttu-id="1cb6c-176">**FailOnValidationFail**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-176">**FailOnValidationFail**</span></span>  
 <span data-ttu-id="1cb6c-177">指定無法驗證文件時作業是否失敗。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-177">Specify whether the operation fails if the document fails to validate.</span></span>  
  
 <span data-ttu-id="1cb6c-178">**ValidationDetails**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-178">**ValidationDetails**</span></span>  
 <span data-ttu-id="1cb6c-179">當此屬性的值為 True 時，會提供詳細的錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-179">Provides rich error output when the value of this property is true.</span></span> <span data-ttu-id="1cb6c-180">如需詳細資訊，請參閱＜ [Validate XML with the XML Task](control-flow/validate-xml-with-the-xml-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-180">For more info, see [Validate XML with the XML Task](control-flow/validate-xml-with-the-xml-task.md).</span></span>  
  
### <a name="validationtype-dynamic-options"></a><span data-ttu-id="1cb6c-181">ValidationType 動態選項</span><span class="sxs-lookup"><span data-stu-id="1cb6c-181">ValidationType Dynamic Options</span></span>  
  
#### <a name="validationtype--xsd"></a><span data-ttu-id="1cb6c-182">ValidationType = XSD</span><span class="sxs-lookup"><span data-stu-id="1cb6c-182">ValidationType = XSD</span></span>  
 <span data-ttu-id="1cb6c-183">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-183">**SecondOperandType**</span></span>  
 <span data-ttu-id="1cb6c-184">選取第二個 XML 文件的來源類型。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-184">Select the source type of the second XML document.</span></span> <span data-ttu-id="1cb6c-185">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-185">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-186">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-186">Value</span></span>|<span data-ttu-id="1cb6c-187">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-187">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-188">**直接輸入**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-188">**Direct input**</span></span>|<span data-ttu-id="1cb6c-189">設定 XML 文件的來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-189">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="1cb6c-190">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-190">**File connection**</span></span>|<span data-ttu-id="1cb6c-191">選取包含 XML 文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-191">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="1cb6c-192">**變數**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-192">**Variable**</span></span>|<span data-ttu-id="1cb6c-193">設定包含 XML 文件的變數來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-193">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="1cb6c-194">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-194">**SecondOperand**</span></span>  
 <span data-ttu-id="1cb6c-195">如果 [SecondOperandType]  設定為 [直接輸入]  ，請提供 XML 程式碼，或按一下省略符號按鈕 ([...])  ，然後使用 [來源編輯器]  對話方塊來提供 XML。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-195">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="1cb6c-196">如果 [SecondOperandType] 設定為 [檔案連線]，請選取檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-196">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="1cb6c-197">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-197">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="1cb6c-198">如果 [XPathStringSourceType] 設定為 [變數]，請選取現有的變數，或按一下 [\<**New variable...**>] 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-198">If **XPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="1cb6c-199">**相關主題**：[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-199">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
### <a name="operationtype--xslt"></a><span data-ttu-id="1cb6c-200">OperationType = XSLT</span><span class="sxs-lookup"><span data-stu-id="1cb6c-200">OperationType = XSLT</span></span>  
 <span data-ttu-id="1cb6c-201">指定 XSLT 作業的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-201">Specify options for the XSLT operation.</span></span>  
  
 <span data-ttu-id="1cb6c-202">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-202">**SaveOperationResult**</span></span>  
 <span data-ttu-id="1cb6c-203">指定 XML 工作是否儲存 XSLT 作業的輸出。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-203">Specify whether the XML task saves the output of the XSLT operation.</span></span>  
  
 <span data-ttu-id="1cb6c-204">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-204">**OverwriteDestination**</span></span>  
 <span data-ttu-id="1cb6c-205">指定是否要覆寫目的地檔案或變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-205">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="1cb6c-206">**目的地**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-206">**Destination**</span></span>  
 <span data-ttu-id="1cb6c-207">如果 [DestinationType] 設定為 [檔案連線]，請選取檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-207">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="1cb6c-208">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-208">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="1cb6c-209">如果 [DestinationType] 設定為 [變數]，請選取現有的變數，或按一下 [\<**New variable...**>] 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-209">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="1cb6c-210">**相關主題**：[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-210">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="1cb6c-211">**DestinationType**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-211">**DestinationType**</span></span>  
 <span data-ttu-id="1cb6c-212">選取 XML 文件的目的地類型。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-212">Select the destination type of the XML document.</span></span> <span data-ttu-id="1cb6c-213">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-213">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-214">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-214">Value</span></span>|<span data-ttu-id="1cb6c-215">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-215">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-216">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-216">**File connection**</span></span>|<span data-ttu-id="1cb6c-217">選取包含 XML 文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-217">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="1cb6c-218">**變數**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-218">**Variable**</span></span>|<span data-ttu-id="1cb6c-219">設定包含 XML 文件的變數來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-219">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="1cb6c-220">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-220">**SecondOperandType**</span></span>  
 <span data-ttu-id="1cb6c-221">選取第二個 XML 文件的來源類型。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-221">Select the source type of the second XML document.</span></span> <span data-ttu-id="1cb6c-222">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-222">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-223">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-223">Value</span></span>|<span data-ttu-id="1cb6c-224">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-224">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-225">**直接輸入**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-225">**Direct input**</span></span>|<span data-ttu-id="1cb6c-226">設定 XML 文件的來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-226">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="1cb6c-227">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-227">**File connection**</span></span>|<span data-ttu-id="1cb6c-228">選取包含 XML 文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-228">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="1cb6c-229">**變數**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-229">**Variable**</span></span>|<span data-ttu-id="1cb6c-230">設定包含 XML 文件的變數來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-230">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="1cb6c-231">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-231">**SecondOperand**</span></span>  
 <span data-ttu-id="1cb6c-232">如果 [SecondOperandType]  設定為 [直接輸入]  ，請提供 XML 程式碼，或按一下省略符號按鈕 ([...])  ，然後使用 [來源編輯器]  對話方塊來提供 XML。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-232">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="1cb6c-233">如果 [SecondOperandType] 設定為 [檔案連線]，請選取檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-233">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="1cb6c-234">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-234">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="1cb6c-235">如果 [XPathStringSourceType] 設定為 [變數]，請選取現有的變數，或按一下 [\<**New variable...**>] 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-235">If **XPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="1cb6c-236">**相關主題**：[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-236">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
### <a name="operationtype--xpath"></a><span data-ttu-id="1cb6c-237">OperationType = XPATH</span><span class="sxs-lookup"><span data-stu-id="1cb6c-237">OperationType = XPATH</span></span>  
 <span data-ttu-id="1cb6c-238">指定 XPath 作業的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-238">Specify options for the XPath operation.</span></span>  
  
 <span data-ttu-id="1cb6c-239">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-239">**SaveOperationResult**</span></span>  
 <span data-ttu-id="1cb6c-240">指定 XML 工作是否儲存 XPath 作業的輸出。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-240">Specify whether the XML task saves the output of the XPath operation.</span></span>  
  
 <span data-ttu-id="1cb6c-241">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-241">**OverwriteDestination**</span></span>  
 <span data-ttu-id="1cb6c-242">指定是否要覆寫目的地檔案或變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-242">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="1cb6c-243">**目的地**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-243">**Destination**</span></span>  
 <span data-ttu-id="1cb6c-244">如果 [DestinationType] 設定為 [檔案連線]，請選取檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-244">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="1cb6c-245">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-245">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="1cb6c-246">如果 [DestinationType] 設定為 [變數]，請選取現有的變數，或按一下 [\<**New variable...**>] 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-246">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="1cb6c-247">**相關主題**：[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-247">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="1cb6c-248">**DestinationType**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-248">**DestinationType**</span></span>  
 <span data-ttu-id="1cb6c-249">選取 XML 文件的目的地類型。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-249">Select the destination type of the XML document.</span></span> <span data-ttu-id="1cb6c-250">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-250">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-251">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-251">Value</span></span>|<span data-ttu-id="1cb6c-252">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-252">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-253">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-253">**File connection**</span></span>|<span data-ttu-id="1cb6c-254">選取包含 XML 文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-254">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="1cb6c-255">**變數**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-255">**Variable**</span></span>|<span data-ttu-id="1cb6c-256">設定包含 XML 文件的變數來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-256">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="1cb6c-257">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-257">**SecondOperandType**</span></span>  
 <span data-ttu-id="1cb6c-258">選取第二個 XML 文件的來源類型。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-258">Select the source type of the second XML document.</span></span> <span data-ttu-id="1cb6c-259">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-259">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-260">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-260">Value</span></span>|<span data-ttu-id="1cb6c-261">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-261">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-262">**直接輸入**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-262">**Direct input**</span></span>|<span data-ttu-id="1cb6c-263">設定 XML 文件的來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-263">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="1cb6c-264">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-264">**File connection**</span></span>|<span data-ttu-id="1cb6c-265">選取包含 XML 文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-265">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="1cb6c-266">**變數**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-266">**Variable**</span></span>|<span data-ttu-id="1cb6c-267">設定包含 XML 文件的變數來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-267">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="1cb6c-268">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-268">**SecondOperand**</span></span>  
 <span data-ttu-id="1cb6c-269">如果 [SecondOperandType]  設定為 [直接輸入]  ，請提供 XML 程式碼，或按一下省略符號按鈕 ([...])  ，然後使用 [來源編輯器]  對話方塊來提供 XML。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-269">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="1cb6c-270">如果 [SecondOperandType] 設定為 [檔案連線]，請選取檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-270">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="1cb6c-271">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-271">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="1cb6c-272">如果 [XPathStringSourceType] 設定為 [變數]，請選取現有的變數，或按一下 [\<**New variable...**>] 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-272">If **XPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="1cb6c-273">**相關主題**：[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-273">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="1cb6c-274">**PutResultInOneNode**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-274">**PutResultInOneNode**</span></span>  
 <span data-ttu-id="1cb6c-275">指定是否將結果寫入單一節點。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-275">Specify whether the result is written to a single node.</span></span>  
  
 <span data-ttu-id="1cb6c-276">**XPathOperation**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-276">**XPathOperation**</span></span>  
 <span data-ttu-id="1cb6c-277">選取 XPath 結果類型。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-277">Select the XPath result type.</span></span> <span data-ttu-id="1cb6c-278">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-278">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-279">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-279">Value</span></span>|<span data-ttu-id="1cb6c-280">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-280">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-281">**評估**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-281">**Evaluation**</span></span>|<span data-ttu-id="1cb6c-282">傳回 XPath 函數的結果。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-282">Returns the results of an XPath function.</span></span>|  
|<span data-ttu-id="1cb6c-283">**節點清單**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-283">**Node list**</span></span>|<span data-ttu-id="1cb6c-284">將選取的節點當做 XML 片段傳回。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-284">Return the selected nodes as an XML fragment.</span></span>|  
|<span data-ttu-id="1cb6c-285">**值**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-285">**Values**</span></span>|<span data-ttu-id="1cb6c-286">傳回所有選取之節點的內部文字值，串連成字串。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-286">Return the inner text value of all selected nodes, concatenated into a string.</span></span>|  
  
### <a name="operationtype--merge"></a><span data-ttu-id="1cb6c-287">OperationType = 合併</span><span class="sxs-lookup"><span data-stu-id="1cb6c-287">OperationType = Merge</span></span>  
 <span data-ttu-id="1cb6c-288">指定合併作業的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-288">Specify options for the Merge operation.</span></span>  
  
 <span data-ttu-id="1cb6c-289">**XPathStringSourceType**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-289">**XPathStringSourceType**</span></span>  
 <span data-ttu-id="1cb6c-290">選取 XML 文件的來源類型。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-290">Select the source type of the XML document.</span></span> <span data-ttu-id="1cb6c-291">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-291">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-292">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-292">Value</span></span>|<span data-ttu-id="1cb6c-293">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-293">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-294">**直接輸入**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-294">**Direct input**</span></span>|<span data-ttu-id="1cb6c-295">設定 XML 文件的來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-295">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="1cb6c-296">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-296">**File connection**</span></span>|<span data-ttu-id="1cb6c-297">選取包含 XML 文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-297">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="1cb6c-298">**變數**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-298">**Variable**</span></span>|<span data-ttu-id="1cb6c-299">設定包含 XML 文件的變數來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-299">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="1cb6c-300">**XPathStringSource**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-300">**XPathStringSource**</span></span>  
 <span data-ttu-id="1cb6c-301">如果 [XPathStringSourceType]  設定為 [直接輸入]  ，請提供 XML 程式碼，或按一下省略符號按鈕 ([...])  ，然後使用 [文件來源編輯器]  對話方塊來提供 XML。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-301">If **XPathStringSourceType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="1cb6c-302">如果 [XPathStringSourceType] 設定為 [檔案連線]，請選取檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-302">If **XPathStringSourceType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="1cb6c-303">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-303">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="1cb6c-304">如果 [XPathStringSourceType] 設定為 [變數]，請選取現有的變數，或按一下 [\<**New variable...**>] 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-304">If **XPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="1cb6c-305">**相關主題**：[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-305">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
 <span data-ttu-id="1cb6c-306">當您使用 XPath 陳述式識別來源文件中的合併位置時，此陳述式預期會傳回單一節點。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-306">When you use an XPath statement to identify the merge location in the source document, this statement is expected to return a single node.</span></span> <span data-ttu-id="1cb6c-307">如果陳述式傳回多個節點，只會使用第一個節點。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-307">If the statement returns multiple nodes, only the first node is used.</span></span> <span data-ttu-id="1cb6c-308">第二個文件的內容會合併到 XPath 查詢傳回的第一個節點之下。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-308">The contents of the second document are merged under the first node that the XPath query returns.</span></span>  
  
 <span data-ttu-id="1cb6c-309">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-309">**SaveOperationResult**</span></span>  
 <span data-ttu-id="1cb6c-310">指定 XML 工作是否儲存合併作業的輸出。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-310">Specify whether the XML task saves the output of the Merge operation.</span></span>  
  
 <span data-ttu-id="1cb6c-311">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-311">**OverwriteDestination**</span></span>  
 <span data-ttu-id="1cb6c-312">指定是否要覆寫目的地檔案或變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-312">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="1cb6c-313">**目的地**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-313">**Destination**</span></span>  
 <span data-ttu-id="1cb6c-314">如果 [DestinationType] 設定為 [檔案連線]，請選取檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-314">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="1cb6c-315">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-315">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="1cb6c-316">如果 [DestinationType] 設定為 [變數]，請選取現有的變數，或按一下 [\<**New variable...**>] 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-316">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="1cb6c-317">**相關主題**：[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-317">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="1cb6c-318">**DestinationType**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-318">**DestinationType**</span></span>  
 <span data-ttu-id="1cb6c-319">選取 XML 文件的目的地類型。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-319">Select the destination type of the XML document.</span></span> <span data-ttu-id="1cb6c-320">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-320">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-321">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-321">Value</span></span>|<span data-ttu-id="1cb6c-322">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-322">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-323">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-323">**File connection**</span></span>|<span data-ttu-id="1cb6c-324">選取包含 XML 文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-324">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="1cb6c-325">**變數**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-325">**Variable**</span></span>|<span data-ttu-id="1cb6c-326">設定包含 XML 文件的變數來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-326">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="1cb6c-327">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-327">**SecondOperandType**</span></span>  
 <span data-ttu-id="1cb6c-328">選取第二份 XML 文件的目的地類型。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-328">Select the destination type of the second XML document.</span></span> <span data-ttu-id="1cb6c-329">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-329">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-330">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-330">Value</span></span>|<span data-ttu-id="1cb6c-331">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-331">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-332">**直接輸入**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-332">**Direct input**</span></span>|<span data-ttu-id="1cb6c-333">設定 XML 文件的來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-333">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="1cb6c-334">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-334">**File connection**</span></span>|<span data-ttu-id="1cb6c-335">選取包含 XML 文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-335">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="1cb6c-336">**變數**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-336">**Variable**</span></span>|<span data-ttu-id="1cb6c-337">設定包含 XML 文件的變數來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-337">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="1cb6c-338">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-338">**SecondOperand**</span></span>  
 <span data-ttu-id="1cb6c-339">如果 [SecondOperandType]  設定為 [直接輸入]  ，請提供 XML 程式碼，或按一下省略符號按鈕 ([...])  ，然後使用 [文件來源編輯器]  對話方塊來提供 XML。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-339">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="1cb6c-340">如果 [SecondOperandType] 設定為 [檔案連線]，請選取檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-340">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="1cb6c-341">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-341">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="1cb6c-342">如果 [SecondOperandType] 設定為 [變數]，請選取現有的變數，或按一下 [\<**New variable...**>] 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-342">If **SecondOperandType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="1cb6c-343">**相關主題**：[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-343">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="operationtype--diff"></a><span data-ttu-id="1cb6c-344">OperationType = Diff</span><span class="sxs-lookup"><span data-stu-id="1cb6c-344">OperationType = Diff</span></span>  
 <span data-ttu-id="1cb6c-345">指定 Diff 作業的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-345">Specify options for the Diff operation.</span></span>  
  
 <span data-ttu-id="1cb6c-346">**DiffAlgorithm**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-346">**DiffAlgorithm**</span></span>  
 <span data-ttu-id="1cb6c-347">選取比較文件時要使用的 Diff 演算法。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-347">Select the Diff algorithm to use when comparing documents.</span></span> <span data-ttu-id="1cb6c-348">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-348">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-349">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-349">Value</span></span>|<span data-ttu-id="1cb6c-350">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-350">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-351">**Auto**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-351">**Auto**</span></span>|<span data-ttu-id="1cb6c-352">讓 XML 工作決定使用快速或精確演算法。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-352">Let the XML task determine whether to use the fast or precise algorithm.</span></span>|  
|<span data-ttu-id="1cb6c-353">**快速**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-353">**Fast**</span></span>|<span data-ttu-id="1cb6c-354">使用快速但比較不精確的 Diff 演算法。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-354">Use a fast, but less precise Diff algorithm.</span></span>|  
|<span data-ttu-id="1cb6c-355">**精確**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-355">**Precise**</span></span>|<span data-ttu-id="1cb6c-356">使用精確 Diff 演算法。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-356">Use a precise Diff algorithm.</span></span>|  
  
 <span data-ttu-id="1cb6c-357">**Diff 選項**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-357">**Diff Options**</span></span>  
 <span data-ttu-id="1cb6c-358">設定要套用至 Diff 作業的 Diff 選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-358">Set the Diff options to apply to the Diff operation.</span></span> <span data-ttu-id="1cb6c-359">選項會在下表中列出。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-359">The options are listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-360">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-360">Value</span></span>|<span data-ttu-id="1cb6c-361">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-361">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-362">**IgnoreXMLDeclaration**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-362">**IgnoreXMLDeclaration**</span></span>|<span data-ttu-id="1cb6c-363">指定是否比較 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-363">Specify whether to compare the XML declaration.</span></span>|  
|<span data-ttu-id="1cb6c-364">**IgnoreDTD**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-364">**IgnoreDTD**</span></span>|<span data-ttu-id="1cb6c-365">指定是否忽略文件類型定義 (DTD)。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-365">Specify whether to ignore the document type definition (DTD).</span></span>|  
|<span data-ttu-id="1cb6c-366">**IgnoreWhite Spaces**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-366">**IgnoreWhite Spaces**</span></span>|<span data-ttu-id="1cb6c-367">指定在比較文件時是否忽略空白數量的差異。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-367">Specify whether to ignore differences in the amount of white space when comparing documents.</span></span>|  
|<span data-ttu-id="1cb6c-368">**IgnoreNamespaces**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-368">**IgnoreNamespaces**</span></span>|<span data-ttu-id="1cb6c-369">指定是否比較元素的命名空間統一資源識別碼 (URI) 及其屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-369">Specify whether to compare the namespace uniform resource identifier (URI) of an element and its attribute names.</span></span><br /><br /> <span data-ttu-id="1cb6c-370">注意：如果此選項設定為 `True`，則會將擁有相同本機名稱但命名空間不同的兩個元素視為相同。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-370">Note: If this option is set to `True`, two elements that have the same local name but different namespaces are considered identical.</span></span>|  
|<span data-ttu-id="1cb6c-371">**IgnoreProcessingInstructions**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-371">**IgnoreProcessingInstructions**</span></span>|<span data-ttu-id="1cb6c-372">指定是否比較處理指示。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-372">Specify whether to compare processing instructions.</span></span>|  
|<span data-ttu-id="1cb6c-373">**IgnoreOrderOf ChildElements**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-373">**IgnoreOrderOf ChildElements**</span></span>|<span data-ttu-id="1cb6c-374">指定是否比較子元素的順序。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-374">Specify whether to compare the order of child elements.</span></span><br /><br /> <span data-ttu-id="1cb6c-375">注意：如果此選項設定為 `True`，則會將只是在同層級清單中位置不同的子元素視為相同。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-375">Note: If this option is set to `True`, child elements that differ only in their position in a list of siblings are considered identical.</span></span>|  
|<span data-ttu-id="1cb6c-376">**IgnoreComments**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-376">**IgnoreComments**</span></span>|<span data-ttu-id="1cb6c-377">指定是否比較註解節點。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-377">Specify whether to compare comment nodes.</span></span>|  
|<span data-ttu-id="1cb6c-378">**IgnorePrefixes**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-378">**IgnorePrefixes**</span></span>|<span data-ttu-id="1cb6c-379">指定是否比較元素與屬性名稱的前置詞。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-379">Specify whether to compare prefixes of element and attribute names.</span></span><br /><br /> <span data-ttu-id="1cb6c-380">注意：如果此選項設定為 `True`，則會將擁有相同本機名稱但命名空間 URI 與前置詞不同的兩個元素視為相同。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-380">Note: If you set this option to `True`, two elements that have the same local name, but different namespace URIs and prefixes, are considered identical.</span></span>|  
  
 <span data-ttu-id="1cb6c-381">**FailOnDifference**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-381">**FailOnDifference**</span></span>  
 <span data-ttu-id="1cb6c-382">指定 Diff 作業失敗時工作是否失敗。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-382">Specify whether the task fails if the Diff operation fails.</span></span>  
  
 <span data-ttu-id="1cb6c-383">**SaveDiffGram**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-383">**SaveDiffGram**</span></span>  
 <span data-ttu-id="1cb6c-384">指定是否儲存比較結果 DiffGram 文件。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-384">Specify whether to save the comparison result, a DiffGram document.</span></span>  
  
 <span data-ttu-id="1cb6c-385">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-385">**SaveOperationResult**</span></span>  
 <span data-ttu-id="1cb6c-386">指定 XML 工作是否儲存 Diff 作業的輸出。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-386">Specify whether the XML task saves the output of the Diff operation.</span></span>  
  
 <span data-ttu-id="1cb6c-387">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-387">**OverwriteDestination**</span></span>  
 <span data-ttu-id="1cb6c-388">指定是否要覆寫目的地檔案或變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-388">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="1cb6c-389">**目的地**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-389">**Destination**</span></span>  
 <span data-ttu-id="1cb6c-390">如果 [DestinationType] 設定為 [檔案連線]，請選取檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-390">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="1cb6c-391">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-391">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="1cb6c-392">如果 [DestinationType] 設定為 [變數]，請選取現有的變數，或按一下 [\<**New variable...**>] 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-392">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="1cb6c-393">**相關主題**：[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-393">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="1cb6c-394">**DestinationType**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-394">**DestinationType**</span></span>  
 <span data-ttu-id="1cb6c-395">選取 XML 文件的目的地類型。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-395">Select the destination type of the XML document.</span></span> <span data-ttu-id="1cb6c-396">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-396">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-397">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-397">Value</span></span>|<span data-ttu-id="1cb6c-398">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-398">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-399">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-399">**File connection**</span></span>|<span data-ttu-id="1cb6c-400">選取包含 XML 文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-400">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="1cb6c-401">**變數**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-401">**Variable**</span></span>|<span data-ttu-id="1cb6c-402">設定包含 XML 文件的變數來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-402">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="1cb6c-403">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-403">**SecondOperandType**</span></span>  
 <span data-ttu-id="1cb6c-404">選取 XML 文件的目的地類型。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-404">Select the destination type of the XML document.</span></span> <span data-ttu-id="1cb6c-405">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-405">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-406">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-406">Value</span></span>|<span data-ttu-id="1cb6c-407">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-407">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-408">**直接輸入**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-408">**Direct input**</span></span>|<span data-ttu-id="1cb6c-409">設定 XML 文件的來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-409">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="1cb6c-410">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-410">**File connection**</span></span>|<span data-ttu-id="1cb6c-411">選取包含 XML 文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-411">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="1cb6c-412">**變數**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-412">**Variable**</span></span>|<span data-ttu-id="1cb6c-413">設定包含 XML 文件的變數來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-413">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="1cb6c-414">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-414">**SecondOperand**</span></span>  
 <span data-ttu-id="1cb6c-415">如果 [SecondOperandType]  設定為 [直接輸入]  ，請提供 XML 程式碼，或按一下省略符號按鈕 ([...])  ，然後使用 [文件來源編輯器]  對話方塊來提供 XML。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-415">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="1cb6c-416">如果 [SecondOperandType] 設定為 [檔案連線]，請選取檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-416">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="1cb6c-417">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-417">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="1cb6c-418">如果 [SecondOperandType] 設定為 [變數]，請選取現有的變數，或按一下 [\<**New variable...**>] 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-418">If **SecondOperandType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="1cb6c-419">**相關主題**：[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-419">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="operationtype--patch"></a><span data-ttu-id="1cb6c-420">OperationType = 修補</span><span class="sxs-lookup"><span data-stu-id="1cb6c-420">OperationType = Patch</span></span>  
 <span data-ttu-id="1cb6c-421">指定修補作業的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-421">Specify options for the Patch operation.</span></span>  
  
 <span data-ttu-id="1cb6c-422">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-422">**SaveOperationResult**</span></span>  
 <span data-ttu-id="1cb6c-423">指定 XML 工作是否儲存修補作業的輸出。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-423">Specify whether the XML task saves the output of the Patch operation.</span></span>  
  
 <span data-ttu-id="1cb6c-424">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-424">**OverwriteDestination**</span></span>  
 <span data-ttu-id="1cb6c-425">指定是否要覆寫目的地檔案或變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-425">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="1cb6c-426">**目的地**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-426">**Destination**</span></span>  
 <span data-ttu-id="1cb6c-427">如果 [DestinationType] 設定為 [檔案連線]，請選取檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-427">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="1cb6c-428">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-428">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="1cb6c-429">如果 [DestinationType] 設定為 [變數]，請選取現有的變數，或按一下 [\<**New variable...**>] 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-429">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="1cb6c-430">**相關主題**：[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-430">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="1cb6c-431">**DestinationType**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-431">**DestinationType**</span></span>  
 <span data-ttu-id="1cb6c-432">選取 XML 文件的目的地類型。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-432">Select the destination type of the XML document.</span></span> <span data-ttu-id="1cb6c-433">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-433">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-434">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-434">Value</span></span>|<span data-ttu-id="1cb6c-435">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-435">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-436">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-436">**File connection**</span></span>|<span data-ttu-id="1cb6c-437">選取包含 XML 文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-437">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="1cb6c-438">**變數**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-438">**Variable**</span></span>|<span data-ttu-id="1cb6c-439">設定包含 XML 文件的變數來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-439">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="1cb6c-440">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-440">**SecondOperandType**</span></span>  
 <span data-ttu-id="1cb6c-441">選取 XML 文件的目的地類型。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-441">Select the destination type of the XML document.</span></span> <span data-ttu-id="1cb6c-442">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-442">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1cb6c-443">值</span><span class="sxs-lookup"><span data-stu-id="1cb6c-443">Value</span></span>|<span data-ttu-id="1cb6c-444">描述</span><span class="sxs-lookup"><span data-stu-id="1cb6c-444">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cb6c-445">**直接輸入**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-445">**Direct input**</span></span>|<span data-ttu-id="1cb6c-446">設定 XML 文件的來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-446">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="1cb6c-447">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-447">**File connection**</span></span>|<span data-ttu-id="1cb6c-448">選取包含 XML 文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-448">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="1cb6c-449">**變數**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-449">**Variable**</span></span>|<span data-ttu-id="1cb6c-450">設定包含 XML 文件的變數來源。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-450">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="1cb6c-451">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="1cb6c-451">**SecondOperand**</span></span>  
 <span data-ttu-id="1cb6c-452">如果 [SecondOperandType]  設定為 [直接輸入]  ，請提供 XML 程式碼，或按一下省略符號按鈕 ([...])  ，然後使用 [文件來源編輯器]  對話方塊來提供 XML。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-452">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="1cb6c-453">如果 [SecondOperandType] 設定為 [檔案連線]，請選取檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-453">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="1cb6c-454">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-454">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="1cb6c-455">如果 [SecondOperandType] 設定為 [變數]，請選取現有的變數，或按一下 [\<**New variable...**>] 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="1cb6c-455">If **SecondOperandType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="1cb6c-456">**相關主題**：[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="1cb6c-456">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cb6c-457">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cb6c-457">See Also</span></span>  
 <span data-ttu-id="1cb6c-458">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1cb6c-458">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="1cb6c-459">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="1cb6c-459">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
