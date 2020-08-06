---
title: XML 來源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmlsource.f1
helpviewer_keywords:
- sources [Integration Services], XML
- XML source [Integration Services]
- XML Source Editor
ms.assetid: 68c27ea5-e93d-4e26-bfb2-d967ca0a5282
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d13a1bf01729932eaa6b232ac7839d2e3001f5fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599072"
---
# <a name="xml-source"></a><span data-ttu-id="5cc94-102">XML 來源</span><span class="sxs-lookup"><span data-stu-id="5cc94-102">XML Source</span></span>
  <span data-ttu-id="5cc94-103">XML 來源會讀取 XML 資料檔案，並將資料填入來源輸出中的資料行。</span><span class="sxs-lookup"><span data-stu-id="5cc94-103">The XML source reads an XML data file and populates the columns in the source output with the data.</span></span>  
  
 <span data-ttu-id="5cc94-104">XML 檔案中的資料經常會包括階層式關聯性。</span><span class="sxs-lookup"><span data-stu-id="5cc94-104">The data in XML files frequently includes hierarchical relationships.</span></span> <span data-ttu-id="5cc94-105">例如，XML 資料檔案可代表目錄以及目錄中的項目。</span><span class="sxs-lookup"><span data-stu-id="5cc94-105">For example, an XML data file can represent catalogs and items in catalogs.</span></span> <span data-ttu-id="5cc94-106">在資料能夠進入資料程序之前，必須先決定 XML 資料檔案中各元素之間的關聯性，並且為檔案中各元素產生輸出。</span><span class="sxs-lookup"><span data-stu-id="5cc94-106">Before the data can enter the data flow, the relationship of the elements in XML data file must be determined, and an output must be generated for each element in the file.</span></span>  
  
## <a name="schemas"></a><span data-ttu-id="5cc94-107">結構描述</span><span class="sxs-lookup"><span data-stu-id="5cc94-107">Schemas</span></span>  
 <span data-ttu-id="5cc94-108">XML 來源使用結構描述解譯 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="5cc94-108">The XML source uses a schema to interpret the XML data.</span></span> <span data-ttu-id="5cc94-109">XML 來源支援使用 XML 結構描述定義 (XSD) 檔或內嵌結構描述，將 XML 資料翻譯成表格格式。</span><span class="sxs-lookup"><span data-stu-id="5cc94-109">The XML source supports use of a XML Schema Definition (XSD) file or inline schemas to translate the XML data into a tabular format.</span></span> <span data-ttu-id="5cc94-110">如果您使用 [XML 來源編輯器]  對話方塊設定 XML 來源，則使用者介面可從指定的 XML 資料檔案產生 XSD。</span><span class="sxs-lookup"><span data-stu-id="5cc94-110">If you configure the XML source by using the **XML Source Editor** dialog box, the user interface can generate an XSD from the specified XML data file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5cc94-111">不支援 DTD。</span><span class="sxs-lookup"><span data-stu-id="5cc94-111">DTDs are not supported.</span></span>  
  
 <span data-ttu-id="5cc94-112">結構描述僅可支援單一命名空間，而不支援結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="5cc94-112">The schemas can support a single namespace only; they do not support schema collections.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5cc94-113">XML 來源不會根據 XSD 驗證 XML 檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="5cc94-113">The XML source does not validate the data in the XML file against the XSD.</span></span>  
  
## <a name="xml-source-editor"></a><span data-ttu-id="5cc94-114">XML 來源編輯器</span><span class="sxs-lookup"><span data-stu-id="5cc94-114">XML Source Editor</span></span>  
 <span data-ttu-id="5cc94-115">XML 檔案中的資料經常會包括階層式關聯性。</span><span class="sxs-lookup"><span data-stu-id="5cc94-115">The data in the XML files frequently includes hierarchical relationships.</span></span> <span data-ttu-id="5cc94-116">[XML 來源編輯器]  對話方塊會使用指定的結構描述產生 XML 來源輸出。</span><span class="sxs-lookup"><span data-stu-id="5cc94-116">The **XML Source Editor** dialog box uses the specified schema to generate the XML source outputs.</span></span> <span data-ttu-id="5cc94-117">您可以指定 XSD 檔、使用內嵌結構描述，或從指定的 XML 資料檔案產生 XSD。</span><span class="sxs-lookup"><span data-stu-id="5cc94-117">You can specify an XSD file, use an inline schema, or generate an XSD from the specified XML data file.</span></span> <span data-ttu-id="5cc94-118">結構描述必須於設計階段提供。</span><span class="sxs-lookup"><span data-stu-id="5cc94-118">The schema must be available at design time.</span></span>  
  
 <span data-ttu-id="5cc94-119">XML 來源會藉由為包含 XML 檔案中其他元素的每項元素建立輸出的方式，從 XML 資料產生表格式結構。</span><span class="sxs-lookup"><span data-stu-id="5cc94-119">The XML source generates tabular structures from the XML data by creating an output for every element that contains other elements in the XML files.</span></span> <span data-ttu-id="5cc94-120">例如，如果 XML 資料代表目錄以及目錄中的項目，則 XML 來源會為目錄以及目錄所包含的每一種項目建立輸出。</span><span class="sxs-lookup"><span data-stu-id="5cc94-120">For example, if the XML data represents catalogs and items in catalogs, the XML source creates an output for catalogs and an output for each type of item that the catalogs contain.</span></span> <span data-ttu-id="5cc94-121">每一個項目的輸出將包含該項目屬性的輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="5cc94-121">The output of each item will contain output columns for the attributes of that item.</span></span>  
  
 <span data-ttu-id="5cc94-122">為了提供有關輸出中資料的階層式關聯性的資訊，XML 來源會在輸出中加入識別每一個子元素所屬父元素的資料行。</span><span class="sxs-lookup"><span data-stu-id="5cc94-122">To provide information about the hierarchical relationship of the data in the outputs, the XML source adds a column in the outputs that identifies the parent element for each child element.</span></span> <span data-ttu-id="5cc94-123">若使用含有不同項目類型的目錄範例，則各項目可能會有識別其所屬目錄的資料行值。</span><span class="sxs-lookup"><span data-stu-id="5cc94-123">Using the example of catalogs with different types of items, each item would have a column value that identifies the catalog to which it belongs.</span></span>  
  
 <span data-ttu-id="5cc94-124">XML 來源會為每一個元素建立輸出，但您不需使用所有輸出。</span><span class="sxs-lookup"><span data-stu-id="5cc94-124">The XML source creates an output for every element, but it is not required that you use all the outputs.</span></span> <span data-ttu-id="5cc94-125">您可以刪除任何不要使用的輸出，或不要將它連接到下游元件。</span><span class="sxs-lookup"><span data-stu-id="5cc94-125">You can delete any output that you do not want to use, or just not connect it to a downstream component.</span></span>  
  
 <span data-ttu-id="5cc94-126">XML 來源還會產生輸出名稱，以確保名稱不會模糊不清。</span><span class="sxs-lookup"><span data-stu-id="5cc94-126">The XML source also generates the output names, to ensure that the names are unambiguous.</span></span> <span data-ttu-id="5cc94-127">這些名稱可能很長，且可能不會以對您來說實用的方式識別輸出。</span><span class="sxs-lookup"><span data-stu-id="5cc94-127">These names may be long and may not identify the outputs in a way that is useful to you.</span></span> <span data-ttu-id="5cc94-128">您可以重新命名輸出，只要其名稱保持唯一即可。</span><span class="sxs-lookup"><span data-stu-id="5cc94-128">You can rename the outputs, as long as their names remain unique.</span></span> <span data-ttu-id="5cc94-129">您也可以修改資料類型和輸出資料行的長度。</span><span class="sxs-lookup"><span data-stu-id="5cc94-129">You can also modify the data type and the length of output columns.</span></span>  
  
 <span data-ttu-id="5cc94-130">XML 來源會針對每一項輸出加入錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="5cc94-130">For every output, the XML source adds an error output.</span></span> <span data-ttu-id="5cc94-131">依預設，錯誤輸出中的資料行的資料類型為 Unicode 字串 (DT_WSTR)，且其長度為 255，不過您可以藉由修改資料類型和長度的方式設定錯誤輸出中的資料行。</span><span class="sxs-lookup"><span data-stu-id="5cc94-131">By default the columns in error outputs have Unicode string data type (DT_WSTR) with a length of 255, but you can configure the columns in the error outputs by modifying their data type and length.</span></span>  
  
 <span data-ttu-id="5cc94-132">如果 XML 資料檔案包含 XSD 中沒有的元素，則會略過這些元素且不會產生其輸出。</span><span class="sxs-lookup"><span data-stu-id="5cc94-132">If the XML data file contains elements that are not in the XSD, these elements are ignored and no output is generated for them.</span></span> <span data-ttu-id="5cc94-133">換言之，如果 XML 資料檔案遺漏了 XSD 中出現的元素，則輸出會包含擁有 Null 值的資料行。</span><span class="sxs-lookup"><span data-stu-id="5cc94-133">On the other hand, if the XML data file is missing elements that are represented in the XSD, the output will contain columns with null values.</span></span>  
  
 <span data-ttu-id="5cc94-134">從 XML 資料檔案擷取資料時，該資料會轉換為 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="5cc94-134">When the data is extracted from the XML data file, it is converted to an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type.</span></span> <span data-ttu-id="5cc94-135">但是，XML 來源無法將 XML 資料轉換成 DT_TIME2 或 DT_DBTIMESTAMP2 資料類型，因為此來源不支援這些資料類型。</span><span class="sxs-lookup"><span data-stu-id="5cc94-135">However, the XML source cannot convert the XML data to the DT_TIME2 or DT_DBTIMESTAMP2 data types because the source does not support these data types.</span></span> <span data-ttu-id="5cc94-136">如需詳細資訊，請參閱 [Integration Services 資料類型](integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5cc94-136">For more information, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="5cc94-137">XSD 或內嵌結構描述可能會指定元素的資料類型；如果未指定，則 [XML 來源編輯器]  對話方塊會指派 Unicode 字串資料類型 (DT_WSTR) 給包含該元素的輸出中的資料行，並將資料行長度設定為 255 個字元。</span><span class="sxs-lookup"><span data-stu-id="5cc94-137">The XSD or inline schema may specify the data type for elements, but if it does not, the **XML Source Editor** dialog box assigns the Unicode string data type (DT_WSTR) to the column in the output that contains the element, and sets the column length to 255 characters.</span></span>  
  
 <span data-ttu-id="5cc94-138">如果結構描述指定元素的最大長度，輸出資料行的長度會設為此值。</span><span class="sxs-lookup"><span data-stu-id="5cc94-138">If the schema specifies the maximum length of an element, the length of output column is set to this value.</span></span> <span data-ttu-id="5cc94-139">如果最大長度大於元素轉換成的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料類型支援的長度，則資料會截斷成該資料類型的最大長度。</span><span class="sxs-lookup"><span data-stu-id="5cc94-139">If the maximum length is greater than the length supported by the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type to which the element is converted, then the data is truncated to the maximum length of the data type.</span></span> <span data-ttu-id="5cc94-140">例如，如果字串長度為 5000，因為 DT_WSTR 資料類型的最大長度是 4000 個字元，則字串會截斷成 4000 個字元；同樣地，位元組資料會截斷成 DT_BYTES 資料類型的最大長度 8000 個字元。</span><span class="sxs-lookup"><span data-stu-id="5cc94-140">For example, if a string has a length of 5000, it is truncated to 4000 characters because the maximum length of the DT_WSTR data type is 4000 characters; likewise, byte data is truncated to 8000 characters, the maximum length of the DT_BYTES data type.</span></span> <span data-ttu-id="5cc94-141">如果結構描述指定無最大長度，則具有其中一種資料類型的預設資料行長度會設為 255。</span><span class="sxs-lookup"><span data-stu-id="5cc94-141">If the schema specifies no maximum length, the default length of columns with either data type is set to 255.</span></span> <span data-ttu-id="5cc94-142">XML 來源中的資料截斷會使用與其他資料流程元件中的截斷相同的方式來處理。</span><span class="sxs-lookup"><span data-stu-id="5cc94-142">Data truncation in the XML source is handled the same way as truncation in other data flow components.</span></span> <span data-ttu-id="5cc94-143">如需詳細資訊，請參閱 [處理資料中的錯誤](error-handling-in-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5cc94-143">For more information, see [Error Handling in Data](error-handling-in-data.md).</span></span>  
  
 <span data-ttu-id="5cc94-144">您可以修改資料類型和資料行長度。</span><span class="sxs-lookup"><span data-stu-id="5cc94-144">You can modify the data type and the column length.</span></span> <span data-ttu-id="5cc94-145">如需詳細資訊，請參閱 [Integration Services 資料類型](integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5cc94-145">For more information, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
## <a name="configuration-of-the-xml-source"></a><span data-ttu-id="5cc94-146">設定 XML 來源</span><span class="sxs-lookup"><span data-stu-id="5cc94-146">Configuration of the XML Source</span></span>  
 <span data-ttu-id="5cc94-147">XML 來源支援三種不同的資料存取模式。</span><span class="sxs-lookup"><span data-stu-id="5cc94-147">The XML source supports three different data access modes.</span></span> <span data-ttu-id="5cc94-148">您可以指定 XML 資料檔案的檔案位置、包含檔案位置的變數，或包含 XML 資料的變數。</span><span class="sxs-lookup"><span data-stu-id="5cc94-148">You can specify the file location of the XML data file, the variable that contains the file location, or the variable that contains the XML data.</span></span>  
  
 <span data-ttu-id="5cc94-149">XML 來源包括 `XMLData` 和 `XMLSchemaDefinition` 自訂屬性；屬性運算式可以在載入封裝時更新這些屬性。</span><span class="sxs-lookup"><span data-stu-id="5cc94-149">The XML source includes the `XMLData` and `XMLSchemaDefinition` custom properties that can be updated by property expressions when the package is loaded.</span></span> <span data-ttu-id="5cc94-150">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 運算式](../expressions/integration-services-ssis-expressions.md)、[在封裝中使用屬性運算式](../expressions/use-property-expressions-in-packages.md)和 [XML 來源自訂屬性](xml-source-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="5cc94-150">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md), and [XML Source Custom Properties](xml-source-custom-properties.md).</span></span>  
  
 <span data-ttu-id="5cc94-151">XML 來源支援多項規則輸出和多項錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="5cc94-151">The XML source supports multiple regular outputs and multiple error outputs.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5cc94-152">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含用來設定 XML 來源的 [XML 來源編輯器]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5cc94-152">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes the **XML Source Edito**r dialog box for configuring the XML source.</span></span> <span data-ttu-id="5cc94-153">[ [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師] 中即提供此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5cc94-153">This dialog box is available in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="5cc94-154">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="5cc94-154">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="5cc94-155">如需 [XML 來源編輯器] \*\*\*\* 對話方塊中可設定屬性的詳細資訊，請按一下下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="5cc94-155">For more information about the properties that you can set in the **XML Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="5cc94-156">[XML 來源編輯器 &#40;[連線管理員] 頁面&#41;](../xml-source-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="5cc94-156">[XML Source Editor &#40;Connection Manager Page&#41;](../xml-source-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="5cc94-157">[XML 來源編輯器 &#40;[資料行] 頁面&#41;](../xml-source-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="5cc94-157">[XML Source Editor &#40;Columns Page&#41;](../xml-source-editor-columns-page.md)</span></span>  
  
-   <span data-ttu-id="5cc94-158">[XML 來源編輯器 &#40;[錯誤輸出] 頁面&#41;](../xml-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="5cc94-158">[XML Source Editor &#40;Error Output Page&#41;](../xml-source-editor-error-output-page.md)</span></span>  
  
 <span data-ttu-id="5cc94-159">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="5cc94-159">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="5cc94-160">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="5cc94-160">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="5cc94-161">Common Properties</span><span class="sxs-lookup"><span data-stu-id="5cc94-161">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="5cc94-162">XML 來源自訂屬性</span><span class="sxs-lookup"><span data-stu-id="5cc94-162">XML Source Custom Properties</span></span>](xml-source-custom-properties.md)  
  
 <span data-ttu-id="5cc94-163">如需有關如何設定屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="5cc94-163">For more information about how to set the properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="5cc94-164">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="5cc94-164">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="5cc94-165">相關工作</span><span class="sxs-lookup"><span data-stu-id="5cc94-165">Related Tasks</span></span>  
 [<span data-ttu-id="5cc94-166">使用 XML 來源來擷取資料</span><span class="sxs-lookup"><span data-stu-id="5cc94-166">Extract Data by Using the XML Source</span></span>](xml-source.md)  
  
## <a name="related-content"></a><span data-ttu-id="5cc94-167">相關內容</span><span class="sxs-lookup"><span data-stu-id="5cc94-167">Related Content</span></span>  
 <span data-ttu-id="5cc94-168">[使用 XML 檔案設定 SSIS 封裝](https://www.sqlshack.com/using-xml-file-configure-ssis-package/)的技術文章。</span><span class="sxs-lookup"><span data-stu-id="5cc94-168">Technical article, [Using an XML file to configure an SSIS package](https://www.sqlshack.com/using-xml-file-configure-ssis-package/).</span></span>  
  
  
