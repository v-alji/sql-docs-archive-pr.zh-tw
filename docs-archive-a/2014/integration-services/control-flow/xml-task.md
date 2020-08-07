---
title: XML 工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmltask.f1
helpviewer_keywords:
- XML [Integration Services]
- XML task [Integration Services]
ms.assetid: 9f761846-390e-46d5-9db7-858943d40849
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bd6c63a95f6972b53f88e4db1ab6f980971accac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596840"
---
# <a name="xml-task"></a><span data-ttu-id="114cb-102">XML 工作</span><span class="sxs-lookup"><span data-stu-id="114cb-102">XML Task</span></span>
  <span data-ttu-id="114cb-103">XML 工作用於處理 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="114cb-103">The XML task is used to work with XML data.</span></span> <span data-ttu-id="114cb-104">使用此工作，封裝可以擷取 XML 文件、使用「可延伸樣式表語言轉換」(XSLT) 樣式表和 XPath 運算式將作業套用到文件、合併多個文件，或者驗證、比較更新的文件，並將其儲存至檔案和變數。</span><span class="sxs-lookup"><span data-stu-id="114cb-104">Using this task, a package can retrieve XML documents, apply operations to the documents by using Extensible Stylesheet Language Transformations (XSLT) style sheets and XPath expressions, merge multiple documents, or validate, compare, and save the updated documents to files and variables.</span></span>  
  
 <span data-ttu-id="114cb-105">此工作可讓 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝在執行階段動態修改 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="114cb-105">This task enables an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package to dynamically modify XML documents at run time.</span></span> <span data-ttu-id="114cb-106">您可將 XML 工作用於下列用途：</span><span class="sxs-lookup"><span data-stu-id="114cb-106">You can use the XML task for the following purposes:</span></span>  
  
-   <span data-ttu-id="114cb-107">重新格式化 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="114cb-107">Reformat an XML document.</span></span> <span data-ttu-id="114cb-108">例如，此工作可以存取位於 XML 檔案的報表，然後動態套用 XSLT 樣式表以自訂文件的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="114cb-108">For example, the task can access a report that resides in an XML file and dynamically apply an XSLT style sheet to customize the document presentation.</span></span>  
  
-   <span data-ttu-id="114cb-109">選取 XML 文件的小節。</span><span class="sxs-lookup"><span data-stu-id="114cb-109">Select sections of an XML document.</span></span> <span data-ttu-id="114cb-110">例如，此工作可以存取位於 XML 檔案的報表，然後動態地套用 XPath 運算式來選取文件的小節。</span><span class="sxs-lookup"><span data-stu-id="114cb-110">For example, the task can access a report that resides in an XML file and dynamically apply an XPath expression to select a section of the document.</span></span> <span data-ttu-id="114cb-111">此作業也可以取得和處理文件中的值。</span><span class="sxs-lookup"><span data-stu-id="114cb-111">The operation can also get and process values in the document.</span></span>  
  
-   <span data-ttu-id="114cb-112">合併多個來源的文件。</span><span class="sxs-lookup"><span data-stu-id="114cb-112">Merge documents from many sources.</span></span> <span data-ttu-id="114cb-113">例如，此工作可以下載多個來源的報表，然後動態地將其合併到一個綜合的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="114cb-113">For example, the task can download reports from multiple sources and dynamically merge them into one comprehensive XML document.</span></span>  
  
-   <span data-ttu-id="114cb-114">驗證 XML 文件，並可選擇取得詳細的錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="114cb-114">Validate an XML document and optionally get detailed error output.</span></span> <span data-ttu-id="114cb-115">如需詳細資訊，請參閱＜ [Validate XML with the XML Task](xml-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="114cb-115">For more info, see [Validate XML with the XML Task](xml-task.md).</span></span>  
  
 <span data-ttu-id="114cb-116">您可以透過使用 XML 來源擷取 XML 文件的值，將 XML 資料包含到資料流程中。</span><span class="sxs-lookup"><span data-stu-id="114cb-116">You can include XML data in a data flow by using an XML source to extract values from an XML document.</span></span> <span data-ttu-id="114cb-117">如需詳細資訊，請參閱 [XML 來源](../data-flow/xml-source.md)。</span><span class="sxs-lookup"><span data-stu-id="114cb-117">For more information, see [XML Source](../data-flow/xml-source.md).</span></span>  
  
## <a name="xml-operations"></a><span data-ttu-id="114cb-118">XML 作業</span><span class="sxs-lookup"><span data-stu-id="114cb-118">XML Operations</span></span>  
 <span data-ttu-id="114cb-119">XML 工作執行的第一個動作是擷取特定的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="114cb-119">The first action the XML task performs is to retrieve a specific XML document.</span></span> <span data-ttu-id="114cb-120">此動作內建於 XML 工作中，並且可以自動發生。</span><span class="sxs-lookup"><span data-stu-id="114cb-120">This action is built into the XML task and occurs automatically.</span></span> <span data-ttu-id="114cb-121">擷取的 XML 文件用作 XML 工作執行之作業的資料來源。</span><span class="sxs-lookup"><span data-stu-id="114cb-121">The retrieved XML document is used as the source of data for the operation that the XML task performs.</span></span>  
  
 <span data-ttu-id="114cb-122">「差異」、「合併」和「修補」的 XML 作業需要兩個運算元。</span><span class="sxs-lookup"><span data-stu-id="114cb-122">The XML operations Diff, Merge, and Patch require two operands.</span></span> <span data-ttu-id="114cb-123">第一個運算元會指定來源 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="114cb-123">The first operand specifies the source XML document.</span></span> <span data-ttu-id="114cb-124">第二個運算元也會指定 XML 文件，其內容視作業的需求而定。</span><span class="sxs-lookup"><span data-stu-id="114cb-124">The second operand also specifies an XML document, the contents of which depend on the requirements of the operation.</span></span> <span data-ttu-id="114cb-125">例如，差異作業會比較兩個文件；因此，第二個運算元會指定與來源 XML 文件相比較的另一個類似 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="114cb-125">For example, the Diff operation compares two documents; therefore, the second operand specifies another, similar XML document to which the source XML document is compared.</span></span>  
  
 <span data-ttu-id="114cb-126">XML 工作可以將變數或「檔案」連接管理員用作其來源，或者在工作屬性中包含 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="114cb-126">The XML task can use a variable or a File connection manager as its source, or include the XML data in a task property.</span></span>  
  
 <span data-ttu-id="114cb-127">如果來源是變數，則指定的變數會包含 XML 文件的路徑。</span><span class="sxs-lookup"><span data-stu-id="114cb-127">If the source is a variable, the specified variable contains the path of the XML document.</span></span>  
  
 <span data-ttu-id="114cb-128">如果來源是「檔案」連接管理員，則指定的「檔案」連接管理員會提供來源資訊。</span><span class="sxs-lookup"><span data-stu-id="114cb-128">If the source is a File connection manager, the specified File connection manager provides the source information.</span></span> <span data-ttu-id="114cb-129">「檔案」連接管理員會在 XML 工作以外另行設定，並在 XML 工作中參考。</span><span class="sxs-lookup"><span data-stu-id="114cb-129">The File connection manager is configured separately from the XML task, and is referenced in the XML task.</span></span> <span data-ttu-id="114cb-130">「檔案」連接管理員的連接字串會指定 XML 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="114cb-130">The connection string of the File connection manager specifies the path of the XML file.</span></span> <span data-ttu-id="114cb-131">如需相關資訊，請參閱 [File Connection Manager](../connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="114cb-131">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="114cb-132">可以設定 XML 工作，以將作業結果儲存到變數或檔案。</span><span class="sxs-lookup"><span data-stu-id="114cb-132">The XML task can be configured to save the result of the operation to a variable or to a file.</span></span> <span data-ttu-id="114cb-133">如果儲存到檔案，XML 工作則使用「檔案」連接管理員來存取此檔案。</span><span class="sxs-lookup"><span data-stu-id="114cb-133">If saving to a file, the XML task uses a File connection manager to access the file.</span></span> <span data-ttu-id="114cb-134">您也可以將差異作業產生的 Diffgram 結果儲存到檔案和變數。</span><span class="sxs-lookup"><span data-stu-id="114cb-134">You can also save the results of the Diffgram generated by the Diff operation to files and variables.</span></span>  
  
## <a name="predefined-xml-operations"></a><span data-ttu-id="114cb-135">預先定義的 XML 作業</span><span class="sxs-lookup"><span data-stu-id="114cb-135">Predefined XML Operations</span></span>  
 <span data-ttu-id="114cb-136">XML 工作包括一組預先定義的作業，用於處理 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="114cb-136">The XML task includes a predefined set of operations for working with XML documents.</span></span> <span data-ttu-id="114cb-137">下表描述這些作業。</span><span class="sxs-lookup"><span data-stu-id="114cb-137">The following table describes these operations.</span></span>  
  
|<span data-ttu-id="114cb-138">作業</span><span class="sxs-lookup"><span data-stu-id="114cb-138">Operation</span></span>|<span data-ttu-id="114cb-139">描述</span><span class="sxs-lookup"><span data-stu-id="114cb-139">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="114cb-140">Diff</span><span class="sxs-lookup"><span data-stu-id="114cb-140">Diff</span></span>|<span data-ttu-id="114cb-141">比較兩份 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="114cb-141">Compares two XML documents.</span></span> <span data-ttu-id="114cb-142">差異作業使用來源 XML 文件做為基底文件，將其與第二個 XML 文件相比較，偵測兩者的差異，並將差異寫入 XML Diffgram 文件。</span><span class="sxs-lookup"><span data-stu-id="114cb-142">Using the source XML document as the base document, the Diff operation compares it to a second XML document, detects their differences, and writes the differences to an XML Diffgram document.</span></span> <span data-ttu-id="114cb-143">此作業包含用於自訂比較的屬性。</span><span class="sxs-lookup"><span data-stu-id="114cb-143">This operation includes properties for customizing the comparison.</span></span>|  
|<span data-ttu-id="114cb-144">合併</span><span class="sxs-lookup"><span data-stu-id="114cb-144">Merge</span></span>|<span data-ttu-id="114cb-145">合併兩份 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="114cb-145">Merges two XML documents.</span></span> <span data-ttu-id="114cb-146">「合併」作業使用來源 XML 文件做為基底文件，將第二個文件的內容加入此基底文件。</span><span class="sxs-lookup"><span data-stu-id="114cb-146">Using the source XML document as the base document, the Merge operation adds the content of a second document into the base document.</span></span> <span data-ttu-id="114cb-147">此作業可以指定基底文件中的合併位置。</span><span class="sxs-lookup"><span data-stu-id="114cb-147">The operation can specify a merge location within the base document.</span></span>|  
|<span data-ttu-id="114cb-148">Patch</span><span class="sxs-lookup"><span data-stu-id="114cb-148">Patch</span></span>|<span data-ttu-id="114cb-149">將差異作業的輸出 (稱為 Diffgram 文件) 套用到 XML 文件，以新建包含 Diffgram 文件內容的父文件。</span><span class="sxs-lookup"><span data-stu-id="114cb-149">Applies the output from the Diff operation, called a Diffgram document, to an XML document, to create a new parent document that includes content from the Diffgram document.</span></span>|  
|<span data-ttu-id="114cb-150">Validate</span><span class="sxs-lookup"><span data-stu-id="114cb-150">Validate</span></span>|<span data-ttu-id="114cb-151">針對「文件類型定義」(DTD) 或「XML 結構描述定義」(XSD) 結構描述來驗證 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="114cb-151">Validates the XML document against a Document Type Definition (DTD) or XML Schema definition (XSD) schema.</span></span>|  
|<span data-ttu-id="114cb-152">XPath</span><span class="sxs-lookup"><span data-stu-id="114cb-152">XPath</span></span>|<span data-ttu-id="114cb-153">執行 XPath 查詢和評估。</span><span class="sxs-lookup"><span data-stu-id="114cb-153">Performs XPath queries and evaluations.</span></span>|  
|<span data-ttu-id="114cb-154">XSLT</span><span class="sxs-lookup"><span data-stu-id="114cb-154">XSLT</span></span>|<span data-ttu-id="114cb-155">在 XML 文件上執行 XSL 轉換。</span><span class="sxs-lookup"><span data-stu-id="114cb-155">Performs XSL transformations on XML documents.</span></span>|  
  
### <a name="diff-operation"></a><span data-ttu-id="114cb-156">差異作業</span><span class="sxs-lookup"><span data-stu-id="114cb-156">Diff Operation</span></span>  
 <span data-ttu-id="114cb-157">視比較要求快還是精確而定，差異作業可設定為使用不同的比較演算法。</span><span class="sxs-lookup"><span data-stu-id="114cb-157">The Diff operation can be configured to use a different comparison algorithm depending on whether the comparison must be fast or precise.</span></span> <span data-ttu-id="114cb-158">作業也可以設定為根據比較文件的大小來自動選取快速或精確比較。</span><span class="sxs-lookup"><span data-stu-id="114cb-158">The operation can also be configured to automatically select a fast or precise comparison based on the size of the documents being compared.</span></span>  
  
 <span data-ttu-id="114cb-159">差異作業包含一組自訂 XML 比較的選項。</span><span class="sxs-lookup"><span data-stu-id="114cb-159">The Diff operation includes a set of options that customize the XML comparison.</span></span> <span data-ttu-id="114cb-160">下表描述這些選項。</span><span class="sxs-lookup"><span data-stu-id="114cb-160">The following table describes the options.</span></span>  
  
|<span data-ttu-id="114cb-161">選項</span><span class="sxs-lookup"><span data-stu-id="114cb-161">Option</span></span>|<span data-ttu-id="114cb-162">描述</span><span class="sxs-lookup"><span data-stu-id="114cb-162">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="114cb-163">**IgnoreComments**</span><span class="sxs-lookup"><span data-stu-id="114cb-163">**IgnoreComments**</span></span>|<span data-ttu-id="114cb-164">指定是否要比較註解節點的值。</span><span class="sxs-lookup"><span data-stu-id="114cb-164">A value that specifies whether comment nodes are compared.</span></span>|  
|<span data-ttu-id="114cb-165">**IgnoreNamespaces**</span><span class="sxs-lookup"><span data-stu-id="114cb-165">**IgnoreNamespaces**</span></span>|<span data-ttu-id="114cb-166">指定是否要比較元素的命名空間統一資源識別碼 (URI) 及其屬性名稱的值。</span><span class="sxs-lookup"><span data-stu-id="114cb-166">A value that specifies whether the namespace uniform resource identifier (URI) of an element and its attribute names are compared.</span></span> <span data-ttu-id="114cb-167">如果此選項設定為 `true`，則本機名稱相同但命名空間不同的兩個元素會被視為一樣。</span><span class="sxs-lookup"><span data-stu-id="114cb-167">If this option is set to `true`, two elements that have the same local name but a different namespace are considered to be identical.</span></span>|  
|<span data-ttu-id="114cb-168">**IgnorePrefixes**</span><span class="sxs-lookup"><span data-stu-id="114cb-168">**IgnorePrefixes**</span></span>|<span data-ttu-id="114cb-169">指定是否要比較元素前置詞和屬性名稱的值。</span><span class="sxs-lookup"><span data-stu-id="114cb-169">A value that specifies whether prefixes of element and attribute names are compared.</span></span> <span data-ttu-id="114cb-170">如果此選項設定為 `true,`，則本機名稱相同但命名空間 URI 和前置詞不同的兩個元素會被視為一樣。</span><span class="sxs-lookup"><span data-stu-id="114cb-170">If this option is set to `true,` two elements that have the same local name but a different namespace URI and prefix are considered identical.</span></span>|  
|<span data-ttu-id="114cb-171">**IgnoreXMLDeclaration**</span><span class="sxs-lookup"><span data-stu-id="114cb-171">**IgnoreXMLDeclaration**</span></span>|<span data-ttu-id="114cb-172">指定是否要比較 XML 宣告的值。</span><span class="sxs-lookup"><span data-stu-id="114cb-172">A value that specifies whether the XML declarations are compared.</span></span>|  
|<span data-ttu-id="114cb-173">**IgnoreOrderOfChildElements**</span><span class="sxs-lookup"><span data-stu-id="114cb-173">**IgnoreOrderOfChildElements**</span></span>|<span data-ttu-id="114cb-174">指定是否要比較子元素順序的值。</span><span class="sxs-lookup"><span data-stu-id="114cb-174">A value that specifies whether the order of child elements is compared.</span></span> <span data-ttu-id="114cb-175">如果此選項設定為 `true`，則同層級清單中只有位置不同的子元素會被視為一樣。</span><span class="sxs-lookup"><span data-stu-id="114cb-175">If this option is set to `true`, child elements that differ only in their position in a list of siblings are considered to be identical.</span></span>|  
|<span data-ttu-id="114cb-176">**IgnoreWhiteSpaces**</span><span class="sxs-lookup"><span data-stu-id="114cb-176">**IgnoreWhiteSpaces**</span></span>|<span data-ttu-id="114cb-177">指定是否要比較空白字元的值。</span><span class="sxs-lookup"><span data-stu-id="114cb-177">A value that specifies whether white spaces are compared.</span></span>|  
|<span data-ttu-id="114cb-178">**IgnoreProcessingInstructions**</span><span class="sxs-lookup"><span data-stu-id="114cb-178">**IgnoreProcessingInstructions**</span></span>|<span data-ttu-id="114cb-179">指定是否要比較處理指示的值。</span><span class="sxs-lookup"><span data-stu-id="114cb-179">A value that specifies whether processing instructions are compared.</span></span>|  
|<span data-ttu-id="114cb-180">**IgnoreDTD**</span><span class="sxs-lookup"><span data-stu-id="114cb-180">**IgnoreDTD**</span></span>|<span data-ttu-id="114cb-181">指定是否要忽略 DTD 的值。</span><span class="sxs-lookup"><span data-stu-id="114cb-181">A value that specifies whether the DTD is ignored.</span></span>|  
  
### <a name="merge-operation"></a><span data-ttu-id="114cb-182">合併作業</span><span class="sxs-lookup"><span data-stu-id="114cb-182">Merge Operation</span></span>  
 <span data-ttu-id="114cb-183">當您使用 XPath 陳述式識別來源文件中的合併位置時，此陳述式預期會傳回單一節點。</span><span class="sxs-lookup"><span data-stu-id="114cb-183">When you use an XPath statement to identify the merge location in the source document, this statement is expected to return a single node.</span></span> <span data-ttu-id="114cb-184">如果陳述式傳回多個節點，只會使用第一個節點。</span><span class="sxs-lookup"><span data-stu-id="114cb-184">If the statement returns multiple nodes, only the first node is used.</span></span> <span data-ttu-id="114cb-185">第二個文件的內容會合併到 XPath 查詢傳回的第一個節點之下。</span><span class="sxs-lookup"><span data-stu-id="114cb-185">The contents of the second document are merged under the first node that the XPath query returns.</span></span>  
  
### <a name="xpath-operation"></a><span data-ttu-id="114cb-186">XPath 作業</span><span class="sxs-lookup"><span data-stu-id="114cb-186">XPath Operation</span></span>  
 <span data-ttu-id="114cb-187">可以將 XPath 作業設定為使用不同類型的 XPath 功能。</span><span class="sxs-lookup"><span data-stu-id="114cb-187">The XPath operation can be configured to use different types of XPath functionality.</span></span>  
  
-   <span data-ttu-id="114cb-188">選取 [評估]  選項以實作 XPath 函數，例如 sum()。</span><span class="sxs-lookup"><span data-stu-id="114cb-188">Select the **Evaluation** option to implement XPath functions such as sum().</span></span>  
  
-   <span data-ttu-id="114cb-189">選取 **[節點清單]** 選項，將選取的節點當做 XML 片段傳回。</span><span class="sxs-lookup"><span data-stu-id="114cb-189">Select the **Node list** option to return the selected nodes as an XML fragment.</span></span>  
  
-   <span data-ttu-id="114cb-190">選取 **值** 選項以傳回所有選取節點的內部文字值 (串連成一個字串)。</span><span class="sxs-lookup"><span data-stu-id="114cb-190">Select the **Values** option to return the inner text value of all the selected nodes, concatenated into a string.</span></span>  
  
### <a name="validation-operation"></a><span data-ttu-id="114cb-191">驗證作業</span><span class="sxs-lookup"><span data-stu-id="114cb-191">Validation Operation</span></span>  
 <span data-ttu-id="114cb-192">可以將「驗證」作業設定為使用「文件類型定義」(DTD) 或「XML 結構描述定義」(XSD) 結構描述。</span><span class="sxs-lookup"><span data-stu-id="114cb-192">The Validation operation can be configured to use either a Document Type Definition (DTD) or XML Schema definition (XSD) schema.</span></span>  
  
 <span data-ttu-id="114cb-193">啟用 `ValidationDetails` 可取得詳細的錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="114cb-193">Enable `ValidationDetails` to get detailed error output.</span></span> <span data-ttu-id="114cb-194">如需詳細資訊，請參閱＜ [Validate XML with the XML Task](xml-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="114cb-194">For more info, see [Validate XML with the XML Task](xml-task.md).</span></span>  
  
## <a name="xml-document-encoding"></a><span data-ttu-id="114cb-195">XML 文件編碼</span><span class="sxs-lookup"><span data-stu-id="114cb-195">XML Document Encoding</span></span>  
 <span data-ttu-id="114cb-196">XML 工作只支援 Unicode 文件的合併。</span><span class="sxs-lookup"><span data-stu-id="114cb-196">The XML task supports merging of Unicode documents only.</span></span> <span data-ttu-id="114cb-197">這表示只能對具有 Unicode 編碼的文件套用「合併」作業。</span><span class="sxs-lookup"><span data-stu-id="114cb-197">This means the task can apply the Merge operation only to documents that have a Unicode encoding.</span></span> <span data-ttu-id="114cb-198">使用其他編碼將造成 XML 工作失敗。</span><span class="sxs-lookup"><span data-stu-id="114cb-198">Use of other encodings will cause the XML task to fail.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="114cb-199">「差異」和「修補」作業均包含一個選項，可用來忽略第二個運算元 XML 資料中的 XML 宣告，進而能夠在這些作業中使用具有其他編碼方式的文件。</span><span class="sxs-lookup"><span data-stu-id="114cb-199">The Diff and Patch operations include an option to ignore the XML declaration in the second-operand XML data, making it possible to use documents that have other encodings in these operations.</span></span>  
  
 <span data-ttu-id="114cb-200">若要確認 XML 文件是否可用，請檢視 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="114cb-200">To verify that the XML document can be used, review the XML declaration.</span></span> <span data-ttu-id="114cb-201">宣告必須明確指定 UTF-8 (表示 8 位元的 Unicode 編碼)。</span><span class="sxs-lookup"><span data-stu-id="114cb-201">The declaration must explicitly specify UTF-8, which indicates 8-bit Unicode encoding.</span></span>  
  
 <span data-ttu-id="114cb-202">下列標記顯示 Unicode 8 位元編碼。</span><span class="sxs-lookup"><span data-stu-id="114cb-202">The following tag shows the Unicode 8-bit encoding.</span></span>  
  
 `<?xml version="1.0" encoding="UTF-8"?>`  
  
## <a name="custom-logging-messages-available-on-the-xml-task"></a><span data-ttu-id="114cb-203">XML 工作上可用的自訂記錄訊息</span><span class="sxs-lookup"><span data-stu-id="114cb-203">Custom Logging Messages Available on the XML Task</span></span>  
 <span data-ttu-id="114cb-204">下表描述 XML 工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="114cb-204">The following table describes the custom log entry for the XML task.</span></span> <span data-ttu-id="114cb-205">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 記錄](../performance/integration-services-ssis-logging.md)和[自訂訊息以進行記錄](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="114cb-205">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="114cb-206">記錄項目</span><span class="sxs-lookup"><span data-stu-id="114cb-206">Log entry</span></span>|<span data-ttu-id="114cb-207">描述</span><span class="sxs-lookup"><span data-stu-id="114cb-207">Description</span></span>|  
|---------------|-----------------|  
|`XMLOperation`|<span data-ttu-id="114cb-208">提供有關工作執行之作業的資訊。</span><span class="sxs-lookup"><span data-stu-id="114cb-208">Provides information about the operation that the task performs</span></span>|  
  
## <a name="configuration-of-the-xml-task"></a><span data-ttu-id="114cb-209">XML 工作的組態</span><span class="sxs-lookup"><span data-stu-id="114cb-209">Configuration of the XML Task</span></span>  
 <span data-ttu-id="114cb-210">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="114cb-210">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="114cb-211">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="114cb-211">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="114cb-212">XML 工作編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="114cb-212">XML Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="114cb-213">以 XML 工作驗證 XML</span><span class="sxs-lookup"><span data-stu-id="114cb-213">Validate XML with the XML Task</span></span>](xml-task.md)  
  
-   [<span data-ttu-id="114cb-214">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="114cb-214">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="114cb-215">如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="114cb-215">For more information about how to set properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="114cb-216">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="114cb-216">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-xml-task"></a><span data-ttu-id="114cb-217">XML 工作的程式設計組態</span><span class="sxs-lookup"><span data-stu-id="114cb-217">Programmatic Configuration of the XML Task</span></span>  
 <span data-ttu-id="114cb-218">如需有關以程式設計方式設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="114cb-218">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.XMLTask.XMLTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="114cb-219">相關工作</span><span class="sxs-lookup"><span data-stu-id="114cb-219">Related Tasks</span></span>  
 [<span data-ttu-id="114cb-220">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="114cb-220">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-content"></a><span data-ttu-id="114cb-221">相關內容</span><span class="sxs-lookup"><span data-stu-id="114cb-221">Related Content</span></span>  
  
-   <span data-ttu-id="114cb-222">agilebi.com 上的部落格文章： [XML 目的地指令碼元件](http://agilebi.com/jwelch/2007/06/02/xml-destination-script-component/)</span><span class="sxs-lookup"><span data-stu-id="114cb-222">Blog entry, [XML Destination Script Component](http://agilebi.com/jwelch/2007/06/02/xml-destination-script-component/), on agilebi.com</span></span>  
  
-   <span data-ttu-id="114cb-223">www.codeplex.com 上的 CodePlex 範例： [處理 XML 資料封裝範例](https://msftisprodsamples.codeplex.com/wikipage?title=SS2008!Process%20XML%20Data%20Package%20Sample&version=10&ProjectName=msftisprodsamples)</span><span class="sxs-lookup"><span data-stu-id="114cb-223">CodePlex sample, [Process XML Data Package Sample](https://msftisprodsamples.codeplex.com/wikipage?title=SS2008!Process%20XML%20Data%20Package%20Sample&version=10&ProjectName=msftisprodsamples), on www.codeplex.com</span></span>  
  
