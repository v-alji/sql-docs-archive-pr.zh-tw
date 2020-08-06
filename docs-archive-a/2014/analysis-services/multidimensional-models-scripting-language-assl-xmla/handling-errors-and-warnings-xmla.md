---
title: 處理 (XMLA) 的錯誤和警告 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- errors [XML for Analysis]
- inline errors [XMLA]
- SOAP faults [XML for Analysis]
- XML for Analysis, errors
- faults [XML for Analysis]
- messages [XML for Analysis]
- XMLA, errors
- warnings [XML for Analysis]
- inline warnings [XMLA]
ms.assetid: ab895282-098d-468e-9460-032598961f45
author: minewiskan
ms.author: owend
ms.openlocfilehash: 07b88d800237e5b4b06af0c1ff11cbd0af846600
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594776"
---
# <a name="handling-errors-and-warnings-xmla"></a><span data-ttu-id="68dd5-102">處理錯誤和警告 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="68dd5-102">Handling Errors and Warnings (XMLA)</span></span>
  <span data-ttu-id="68dd5-103">當 XML for Analysis (XMLA) [探索](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)或[執行](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)方法呼叫未執行、成功執行但產生錯誤或警告，或成功執行但傳回包含錯誤的結果時，就需要錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="68dd5-103">Error handling is required when an XML for Analysis (XMLA) [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) or [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method call does not run, runs successfully but generates errors or warnings, or runs successfully but returns results that contain errors.</span></span>  
  
|<span data-ttu-id="68dd5-104">錯誤</span><span class="sxs-lookup"><span data-stu-id="68dd5-104">Error</span></span>|<span data-ttu-id="68dd5-105">報告</span><span class="sxs-lookup"><span data-stu-id="68dd5-105">Reporting</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="68dd5-106">XMLA 方法呼叫未執行</span><span class="sxs-lookup"><span data-stu-id="68dd5-106">The XMLA method call does not run</span></span>|[!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="68dd5-107">傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] SOAP 錯誤訊息，其中包含失敗的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="68dd5-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns a SOAP fault message that contains the details of the failure.</span></span><br /><br /> <span data-ttu-id="68dd5-108">如需詳細資訊，請參閱[處理 SOAP 錯誤](#handling_soap_faults)一節。</span><span class="sxs-lookup"><span data-stu-id="68dd5-108">For more information, see the section, [Handling SOAP Faults](#handling_soap_faults).</span></span>|  
|<span data-ttu-id="68dd5-109">方法呼叫成功時的錯誤或警告</span><span class="sxs-lookup"><span data-stu-id="68dd5-109">Errors or warnings on a successful method call</span></span>|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="68dd5-110">在包含方法呼叫結果之[根](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla)元素的[Messages](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla)屬性中，分別包含每個錯誤或警告的[error](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla)或[warning](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/warning-element-xmla)元素。</span><span class="sxs-lookup"><span data-stu-id="68dd5-110">includes an [error](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) or [warning](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/warning-element-xmla) element for each error or warning, respectively, in the [Messages](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla) property of the [root](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) element that contains the results of the method call.</span></span><br /><br /> <span data-ttu-id="68dd5-111">如需詳細資訊，請參閱[處理錯誤和警告](#handling_errors_and_warnings)一節。</span><span class="sxs-lookup"><span data-stu-id="68dd5-111">For more information, see the section, [Handling Errors and Warnings](#handling_errors_and_warnings).</span></span>|  
|<span data-ttu-id="68dd5-112">方法呼叫成功時結果中的錯誤</span><span class="sxs-lookup"><span data-stu-id="68dd5-112">Errors in the result for a successful method call</span></span>|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="68dd5-113">在 `error` `warning` 方法呼叫結果的適當資料[格或](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla)資料[列](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/row-element-xmla)元素內，分別包含錯誤或警告的內嵌或元素。</span><span class="sxs-lookup"><span data-stu-id="68dd5-113">includes an inline `error` or `warning` element for the error or warning, respectively, within the appropriate [Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) or [row](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/row-element-xmla) element of the results of the method call.</span></span><br /><br /> <span data-ttu-id="68dd5-114">如需詳細資訊，請參閱[處理內嵌錯誤和警告](#handling_inline_errors_and_warnings)一節。</span><span class="sxs-lookup"><span data-stu-id="68dd5-114">For more information, see the section, [Handling Inline Errors and Warnings](#handling_inline_errors_and_warnings).</span></span>|  
  
##  <a name="handling-soap-faults"></a><a name="handling_soap_faults"></a><span data-ttu-id="68dd5-115">處理 SOAP 錯誤</span><span class="sxs-lookup"><span data-stu-id="68dd5-115">Handling SOAP Faults</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="68dd5-116">在發生下列情況時會傳回 SOAP 錯誤：</span><span class="sxs-lookup"><span data-stu-id="68dd5-116">returns a SOAP fault when the following situations occur:</span></span>  
  
-   <span data-ttu-id="68dd5-117">包含 XMLA 方法的 SOAP 訊息，其格式不正確或是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體無法驗證它。</span><span class="sxs-lookup"><span data-stu-id="68dd5-117">The SOAP message that contains the XMLA method was not well-formed or could not be validated by the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="68dd5-118">發生通訊錯誤或是其他有關包含 XMLA 方法之 SOAP 訊息的錯誤。</span><span class="sxs-lookup"><span data-stu-id="68dd5-118">A communications or other error occurred involving the SOAP message that contains the XMLA method.</span></span>  
  
-   <span data-ttu-id="68dd5-119">XMLA 方法並未在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="68dd5-119">The XMLA method did not run on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="68dd5-120">以 "XMLForAnalysis" 開頭的 XMLstartA 之 SOAP 錯誤碼，後面會接著句號和十六進位的 HRESULT 結果碼。</span><span class="sxs-lookup"><span data-stu-id="68dd5-120">The SOAP fault codes for XMLstartA start with "XMLForAnalysis", followed by a period and the hexadecimal HRESULT result code.</span></span> <span data-ttu-id="68dd5-121">例如，`0x80000005` 的錯誤碼會格式化為 "`XMLForAnalysis.0x80000005`"。</span><span class="sxs-lookup"><span data-stu-id="68dd5-121">For example, an error code of "`0x80000005`" is formatted as "`XMLForAnalysis.0x80000005`".</span></span> <span data-ttu-id="68dd5-122">如需有關 SOAP 錯誤格式的詳細資訊，請參閱 W3C 簡易物件存取通訊協定 (SOAP) 1.1 中的 Soap 錯誤。</span><span class="sxs-lookup"><span data-stu-id="68dd5-122">For more information about the SOAP fault format, see Soap Fault in the W3C Simple Object Access Protocol (SOAP) 1.1.</span></span>  
  
### <a name="fault-code-information"></a><span data-ttu-id="68dd5-123">錯誤碼資訊</span><span class="sxs-lookup"><span data-stu-id="68dd5-123">Fault Code Information</span></span>  
 <span data-ttu-id="68dd5-124">下表將顯示包含在 SOAP 回應之詳細資料區段中的 XMLA 錯誤碼資訊。</span><span class="sxs-lookup"><span data-stu-id="68dd5-124">The following table shows the XMLA fault code information that is contained in the detail section of the SOAP response.</span></span> <span data-ttu-id="68dd5-125">資料行是在 SOAP 錯誤的詳細資料區段中某個錯誤的屬性。</span><span class="sxs-lookup"><span data-stu-id="68dd5-125">The columns are the attributes of an error in the detail section of a SOAP fault.</span></span>  
  
|<span data-ttu-id="68dd5-126">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="68dd5-126">Column name</span></span>|<span data-ttu-id="68dd5-127">類型</span><span class="sxs-lookup"><span data-stu-id="68dd5-127">Type</span></span>|<span data-ttu-id="68dd5-128">描述</span><span class="sxs-lookup"><span data-stu-id="68dd5-128">Description</span></span>|<span data-ttu-id="68dd5-129">允許 Null<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="68dd5-129">Null allowed<sup>1</sup></span></span>|  
|-----------------|----------|-----------------|------------------------------|  
|`ErrorCode`|`UnsignedInt`|<span data-ttu-id="68dd5-130">傳回指出方法成功或失敗的代碼。</span><span class="sxs-lookup"><span data-stu-id="68dd5-130">Return code that indicates the success or failure of the method.</span></span> <span data-ttu-id="68dd5-131">必須將十六進位值轉換成 `UnsignedInt` 值。</span><span class="sxs-lookup"><span data-stu-id="68dd5-131">The hexadecimal value must be converted to an `UnsignedInt` value.</span></span>|<span data-ttu-id="68dd5-132">否</span><span class="sxs-lookup"><span data-stu-id="68dd5-132">No</span></span>|  
|`WarningCode`|`UnsignedInt`|<span data-ttu-id="68dd5-133">傳回指出警告狀況的代碼。</span><span class="sxs-lookup"><span data-stu-id="68dd5-133">Return code that indicates a warning condition.</span></span> <span data-ttu-id="68dd5-134">必須將十六進位值轉換成 `UnsignedInt` 值。</span><span class="sxs-lookup"><span data-stu-id="68dd5-134">The hexadecimal value must be converted to an `UnsignedInt` value.</span></span>|<span data-ttu-id="68dd5-135">是</span><span class="sxs-lookup"><span data-stu-id="68dd5-135">Yes</span></span>|  
|`Description`|`String`|<span data-ttu-id="68dd5-136">產生錯誤的元件所傳回的警告文字與描述。</span><span class="sxs-lookup"><span data-stu-id="68dd5-136">Error or warning text and description returned by the component that generated the error.</span></span>|<span data-ttu-id="68dd5-137">是</span><span class="sxs-lookup"><span data-stu-id="68dd5-137">Yes</span></span>|  
|`Source`|`String`|<span data-ttu-id="68dd5-138">產生錯誤或警告之元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="68dd5-138">Name of the component that generated the error or warning.</span></span>|<span data-ttu-id="68dd5-139">是</span><span class="sxs-lookup"><span data-stu-id="68dd5-139">Yes</span></span>|  
|`HelpFile`|`String`|<span data-ttu-id="68dd5-140">描述錯誤或警告之說明檔或主題的路徑或 URL。</span><span class="sxs-lookup"><span data-stu-id="68dd5-140">Path or URL to the Help file or topic that describes the error or warning.</span></span>|<span data-ttu-id="68dd5-141">是</span><span class="sxs-lookup"><span data-stu-id="68dd5-141">Yes</span></span>|  
  
 <span data-ttu-id="68dd5-142"><sup>1</sup>表示資料是否為必要且必須傳回，或資料是否為選擇性，如果不適用，則允許 null 字串。</span><span class="sxs-lookup"><span data-stu-id="68dd5-142"><sup>1</sup> Indicates whether the data is required and must be returned, or whether the data is optional and a null string is allowed if the column does not apply.</span></span>  
  
 <span data-ttu-id="68dd5-143">下列是方法呼叫失敗時所發生的 SOAP 錯誤之範例：</span><span class="sxs-lookup"><span data-stu-id="68dd5-143">The following is an example of a SOAP fault that occurred when a method call failed:</span></span>  
  
```  
<?xml version="1.0"?>  
   <SOAP-ENV:Envelope  
   xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
   SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
      <SOAP-ENV:Fault>  
         <faultcode>XMLAnalysisError.0x80000005</faultcode>  
         <faultstring>The XML for Analysis provider encountered an error.</faultstring>  
         <faultactor>XML for Analysis Provider</faultactor>  
         <detail>  
<Error  
ErrorCode="2147483653"  
Description="An unexpected error has occurred."  
Source="XML for Analysis Provider"  
HelpFile="" />  
         </detail>  
      </SOAP-ENV:Fault>  
</SOAP-ENV:Envelope>  
```  
  
##  <a name="handling-errors-and-warnings"></a><a name="handling_errors_and_warnings"></a><span data-ttu-id="68dd5-144">處理錯誤和警告</span><span class="sxs-lookup"><span data-stu-id="68dd5-144">Handling Errors and Warnings</span></span>  
 <span data-ttu-id="68dd5-145">如果下列情況在該命令執行之後發生，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會傳回 `Messages` 元素中的 `root` 屬性：</span><span class="sxs-lookup"><span data-stu-id="68dd5-145">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns the `Messages` property in the `root` element for a command if the following situations occur after that command runs:</span></span>  
  
-   <span data-ttu-id="68dd5-146">方法本身並未失敗，但是方法呼叫成功之後，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上發生失敗。</span><span class="sxs-lookup"><span data-stu-id="68dd5-146">The method itself did not fail, but a failure occurred on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance after the method call succeeded.</span></span>  
  
-   <span data-ttu-id="68dd5-147">當命令成功時，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體會傳回警告。</span><span class="sxs-lookup"><span data-stu-id="68dd5-147">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance returns a warning when the command is successful.</span></span>  
  
 <span data-ttu-id="68dd5-148"> 屬性會遵循  元素所包含的所有其他屬性，而且可以包含一或多個  元素。</span><span class="sxs-lookup"><span data-stu-id="68dd5-148">The `Messages` property follows all other properties that are contained by the `root` element, and can contain one or more `Message` elements.</span></span> <span data-ttu-id="68dd5-149">因此，每個 `Message` 元素可包含單一 `error` 或 `warning` 元素，以分別描述指定命令所發生的任何錯誤或是警告。</span><span class="sxs-lookup"><span data-stu-id="68dd5-149">In turn, each `Message` element can contain either a single `error` or `warning` element describing any errors or warnings, respectively, that occurred for the specified command.</span></span>  
  
 <span data-ttu-id="68dd5-150">如需屬性中所含錯誤和警告的詳細資訊 `Messages` ，請參閱[Messages 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla)。</span><span class="sxs-lookup"><span data-stu-id="68dd5-150">For more information about errors and warnings that are contained in the `Messages` property, see [Messages Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla).</span></span>  
  
### <a name="handling-errors-during-serialization"></a><span data-ttu-id="68dd5-151">處理序列化期間的錯誤。</span><span class="sxs-lookup"><span data-stu-id="68dd5-151">Handling Errors During Serialization</span></span>  
 <span data-ttu-id="68dd5-152">如果在實例已經開始序列化 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 成功執行命令的輸出之後發生錯誤，則會在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 發生錯誤時傳回不同命名空間中的[Exception](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/exception-element-xmla)元素。</span><span class="sxs-lookup"><span data-stu-id="68dd5-152">If an error occurs after the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance has already begun serializing the output of a successfully run command, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns an [Exception](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/exception-element-xmla) element in a different namespace at the point of the error.</span></span> <span data-ttu-id="68dd5-153">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體接著會關閉所有開啟的元素，這樣傳送到用戶端的 XML 文件就會是有效的文件。</span><span class="sxs-lookup"><span data-stu-id="68dd5-153">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance then closes all open elements so that the XML document sent to the client is a valid document.</span></span> <span data-ttu-id="68dd5-154">執行個體也會傳回 `Messages` 元素，以包含錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="68dd5-154">The instance also returns a `Messages` element that contains the description of the error.</span></span>  
  
##  <a name="handling-inline-errors-and-warnings"></a><a name="handling_inline_errors_and_warnings"></a><span data-ttu-id="68dd5-155">處理內嵌錯誤和警告</span><span class="sxs-lookup"><span data-stu-id="68dd5-155">Handling Inline Errors and Warnings</span></span>  
 <span data-ttu-id="68dd5-156">如果 XMLA 方法本身並未失敗，但是在 XMLA 方法呼叫成功之後，在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上發生該方法傳回的結果中資料元素的特定錯誤，則 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會為命令傳回內嵌 `error` 或 `warning`。</span><span class="sxs-lookup"><span data-stu-id="68dd5-156">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns an inline `error` or `warning` for a command if the XMLA method itself did not fail, but an error specific to a data element in the results returned by the method occurred on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance after the XMLA method call succeeded.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="68dd5-157">`error` `warning` 如果發生資料格特定的問題，或在使用 MDDataSet 資料類型的元素中包含的其他資料，則提供內嵌和元素 `root` ，例如，儲存格的安全性錯誤或格式錯誤。 [MDDataSet](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/mddataset-data-type-xmla)</span><span class="sxs-lookup"><span data-stu-id="68dd5-157">supplies inline `error` and `warning` elements if issues specific to a cell or to other data that are contained within a `root` element using the [MDDataSet](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/mddataset-data-type-xmla) data type occur, such as a security error or formatting error for a cell.</span></span> <span data-ttu-id="68dd5-158">在這些情況下，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會傳回 `error` 或 `warning` 元素中，分別包含錯誤或警告的 `Cell` 或 `row` 元素。</span><span class="sxs-lookup"><span data-stu-id="68dd5-158">In these cases, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns an `error` or `warning` element in the `Cell` or `row` element that contains the error or warning, respectively.</span></span>  
  
 <span data-ttu-id="68dd5-159">下列範例說明 `Execute` 使用[語句](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla)命令從方法傳回的資料列集中包含錯誤的結果集。</span><span class="sxs-lookup"><span data-stu-id="68dd5-159">The following example illustrates a result set that contains an error in the rowset returned from an `Execute` method using the [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) command.</span></span>  
  
```  
<return>  
   ...  
   <root>  
      ...  
      <CellData>  
      ...  
         <Cell CellOrdinal="10">  
            <Value>  
               <Error>  
                  <ErrorCode>2148497527</ErrorCode>   
                  <Description>Security Error.</Description>   
               </Error>  
            </Value>  
         </Cell>  
      </CellData>  
      ...  
   </root>  
   ...  
</return>  
```  
  
## <a name="see-also"></a><span data-ttu-id="68dd5-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68dd5-160">See Also</span></span>  
 [<span data-ttu-id="68dd5-161">在 Analysis Services 中使用 XMLA 進行開發</span><span class="sxs-lookup"><span data-stu-id="68dd5-161">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
