---
title: XML 編輯器
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.editorxml.f1
- sql12.swb.xmleditor.f1
- vs.xmleditor
- sql12.swb.editor.xml.f1
helpviewer_keywords:
- XML Designer [SQL Server Management Studio]
ms.assetid: 0824a5ce-e67b-4b53-98d9-d371faf2d23c
author: rothja
ms.author: jroth
ms.openlocfilehash: b7c3bbbda4f5a31c4d83b559c1aa623ca2aff89f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599452"
---
# <a name="xml-editor-sql-server-management-studio"></a><span data-ttu-id="057a6-102">XML 編輯器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="057a6-102">XML Editor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="057a6-103">提供一組視覺化工具，以搭配 XML 結構描述、ADO.NET 資料集以及 XML 文件使用。</span><span class="sxs-lookup"><span data-stu-id="057a6-103">Provides a set of visual tools for working with XML Schemas, ADO.NET datasets, and XML documents.</span></span> <span data-ttu-id="057a6-104">XML 設計工具支援全球資訊網協會 (WC3) 定義的 XML 結構描述定義 (XSD) 語言。</span><span class="sxs-lookup"><span data-stu-id="057a6-104">The XML Designer supports the XML Schema Definition (XSD) language defined by the World Wide Web Consortium (WC3).</span></span> <span data-ttu-id="057a6-105">設計師不支援 DTD (文件類型定義) 或其他 XML 結構描述語言，例如 XDR (XML-Data Reduced)。</span><span class="sxs-lookup"><span data-stu-id="057a6-105">The designer does not support DTDs (document type definitions) or other XML schema languages, such as XDR (XML-Data Reduced).</span></span>  
  
 <span data-ttu-id="057a6-106">若要顯示設計師，請在專案中加入資料集、XML 結構描述或 XML 檔案，或開啟下面資料表中所列出的任何檔案類型。</span><span class="sxs-lookup"><span data-stu-id="057a6-106">To display the designer, add a dataset, XML Schema, or XML file to your project or open any of the file types listed in the table below.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="057a6-107">在結構描述檢視中作業時，沒有 **[恢復]** 命令可用。</span><span class="sxs-lookup"><span data-stu-id="057a6-107">There is no **Undo** command when working in Schema view.</span></span> <span data-ttu-id="057a6-108">請仔細規劃您的工作，並經常儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="057a6-108">Plan your work carefully and save your files often.</span></span>  
  
 <span data-ttu-id="057a6-109">設計師提供下列三種檢視 (或模式) 來處理 XML 檔案、XML 結構描述和資料集：</span><span class="sxs-lookup"><span data-stu-id="057a6-109">The designer provides the following three views (or modes) to work on XML files, XML Schemas, and datasets:</span></span>  
  
|<span data-ttu-id="057a6-110">檢視</span><span class="sxs-lookup"><span data-stu-id="057a6-110">View</span></span>|<span data-ttu-id="057a6-111">描述</span><span class="sxs-lookup"><span data-stu-id="057a6-111">Description</span></span>|<span data-ttu-id="057a6-112">支援的檔案類型</span><span class="sxs-lookup"><span data-stu-id="057a6-112">File types supported</span></span>|  
|----------|-----------------|--------------------------|  
|<span data-ttu-id="057a6-113">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="057a6-113">**Schema**</span></span>|<span data-ttu-id="057a6-114">以視覺化的方式建立和修改 XML 結構描述與 ADO.NET 資料集。</span><span class="sxs-lookup"><span data-stu-id="057a6-114">For visually creating and modifying XML Schemas and ADO.NET datasets.</span></span>|<span data-ttu-id="057a6-115">.xsd</span><span class="sxs-lookup"><span data-stu-id="057a6-115">.xsd</span></span>|  
|<span data-ttu-id="057a6-116">**Data**</span><span class="sxs-lookup"><span data-stu-id="057a6-116">**Data**</span></span>|<span data-ttu-id="057a6-117">在結構化資料方格中，以視覺化的方式修改 XML 資料檔案。</span><span class="sxs-lookup"><span data-stu-id="057a6-117">For visually modifying XML data files in a structured data grid.</span></span>|<span data-ttu-id="057a6-118">.xml</span><span class="sxs-lookup"><span data-stu-id="057a6-118">.xml</span></span>|  
|<span data-ttu-id="057a6-119">**XML**</span><span class="sxs-lookup"><span data-stu-id="057a6-119">**XML**</span></span>|<span data-ttu-id="057a6-120">用於編輯 XML；來源編輯器提供色彩編碼和 IntelliSense，其中包括自動完成和列出成員。</span><span class="sxs-lookup"><span data-stu-id="057a6-120">For editing XML; the source editor provides color-coding and IntelliSense, including Complete Word and List Members.</span></span>|<span data-ttu-id="057a6-121">.xml .xsd .xslt .wsdl.web.resx.tdl.wsf.hta.disco.vsdisco.config</span><span class="sxs-lookup"><span data-stu-id="057a6-121">.xml .xsd .xslt .wsdl.web.resx.tdl.wsf.hta.disco.vsdisco.config</span></span>|  
|<span data-ttu-id="057a6-122">**執行程序表**</span><span class="sxs-lookup"><span data-stu-id="057a6-122">**ShowPlan**</span></span>|<span data-ttu-id="057a6-123">顯示使用 SET SHOWPLAN_XML ON 選項建立的 xml 查詢計畫。</span><span class="sxs-lookup"><span data-stu-id="057a6-123">Displays xml query plans created using the SET SHOWPLAN_XML ON option.</span></span>|<span data-ttu-id="057a6-124">.showplan</span><span class="sxs-lookup"><span data-stu-id="057a6-124">.showplan</span></span>|  
  
## <a name="schema-view"></a><span data-ttu-id="057a6-125">結構描述檢視</span><span class="sxs-lookup"><span data-stu-id="057a6-125">Schema View</span></span>  
 <span data-ttu-id="057a6-126">結構描述檢視提供元素、屬性、類型等等可組成 XML 結構描述和 ADO.NET 資料集的視覺表示法。</span><span class="sxs-lookup"><span data-stu-id="057a6-126">Schema view provides a visual representation of the elements, attributes, types, and so on, that make up XML Schemas and ADO.NET datasets.</span></span>  
  
 <span data-ttu-id="057a6-127">在結構描述檢視中，您可以從工具箱的 XML 結構描述索引標籤，或從伺服器總管，在設計介面上卸除元素，以建構結構描述和資料集。</span><span class="sxs-lookup"><span data-stu-id="057a6-127">In Schema view you can construct schemas and datasets by dropping elements on the design surface from either the XML Schema tab of the Toolbox or from Server Explorer.</span></span> <span data-ttu-id="057a6-128">此外，您可以用滑鼠右鍵按一下設計介面，或者從快速鍵功能表中選取 [加入]，以將元素加入設計師中。</span><span class="sxs-lookup"><span data-stu-id="057a6-128">Additionally, you can add elements to the designer by right-clicking the design surface and selecting Add from the shortcut menu.</span></span>  
  
 <span data-ttu-id="057a6-129">在結構描述檢視中，您可以：</span><span class="sxs-lookup"><span data-stu-id="057a6-129">In Schema view you can:</span></span>  
  
-   <span data-ttu-id="057a6-130">建構並修改現有的 XML 結構描述和 ADO.NET 資料集</span><span class="sxs-lookup"><span data-stu-id="057a6-130">Construct and modify existing XML Schemas and ADO.NET datasets</span></span>  
  
-   <span data-ttu-id="057a6-131">建立與編輯資料表之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="057a6-131">Create and edit relationships between tables</span></span>  
  
-   <span data-ttu-id="057a6-132">建立與編輯索引鍵</span><span class="sxs-lookup"><span data-stu-id="057a6-132">Create and edit keys</span></span>  
  
-   <span data-ttu-id="057a6-133">從 XML 結構描述產生 ADO.NET 資料集</span><span class="sxs-lookup"><span data-stu-id="057a6-133">Generate ADO.NET datasets from XML Schemas</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="057a6-134">結構描述檢視中的元素配置儲存在 .xsx 檔案中，只要按一下方案總管工具列的 **[顯示所有檔案]** ，然後展開 .xsd 檔案就能看到。</span><span class="sxs-lookup"><span data-stu-id="057a6-134">The layout of elements in Schema view is stored in the .xsx file, which can be seen by clicking **Show All Files** in the Solution Explorer toolbar, and then expanding the .xsd file.</span></span> <span data-ttu-id="057a6-135">如果沒有 .xsx 檔案，則表示從未於 XML 設計工具中開啟 .xsd 檔案。</span><span class="sxs-lookup"><span data-stu-id="057a6-135">If there is no .xsx file present, it means the .xsd file has never been opened in the XML Designer.</span></span>  
  
### <a name="customizing-schema-view"></a><span data-ttu-id="057a6-136">自訂結構描述檢視</span><span class="sxs-lookup"><span data-stu-id="057a6-136">Customizing Schema View</span></span>  
 <span data-ttu-id="057a6-137">下列功能可以在結構描述檢視中修改元素的視覺化配置：</span><span class="sxs-lookup"><span data-stu-id="057a6-137">The following features modify the visual layout of elements in Schema view:</span></span>  
  
-   <span data-ttu-id="057a6-138">顯示比例</span><span class="sxs-lookup"><span data-stu-id="057a6-138">Zooming</span></span>  
  
-   <span data-ttu-id="057a6-139">展開或摺疊巢狀元素</span><span class="sxs-lookup"><span data-stu-id="057a6-139">Expanding or collapsing of nested elements</span></span>  
  
-   <span data-ttu-id="057a6-140">自動排列元素配置</span><span class="sxs-lookup"><span data-stu-id="057a6-140">Automatically arranging layout of elements</span></span>  
  
-   <span data-ttu-id="057a6-141">重新設定摺疊元素的預設狀態</span><span class="sxs-lookup"><span data-stu-id="057a6-141">Resetting default state of collapsed elements</span></span>  
  
##### <a name="to-expand-hidden-nested-elements"></a><span data-ttu-id="057a6-142">若要展開隱藏的巢狀元素</span><span class="sxs-lookup"><span data-stu-id="057a6-142">To expand hidden nested elements</span></span>  
  
-   <span data-ttu-id="057a6-143">按一下元素底部的加號圖示。</span><span class="sxs-lookup"><span data-stu-id="057a6-143">Click the plus icon on the bottom of the element.</span></span>  
  
##### <a name="to-collapse-nested-elements"></a><span data-ttu-id="057a6-144">若要摺疊巢狀元素</span><span class="sxs-lookup"><span data-stu-id="057a6-144">To collapse nested elements</span></span>  
  
-   <span data-ttu-id="057a6-145">在您要顯示於設計師的最底部元素上，按一下減號圖示。</span><span class="sxs-lookup"><span data-stu-id="057a6-145">Click the minus icon on the bottom-most element that you want to appear on the designer.</span></span>  
  
## <a name="data-view"></a><span data-ttu-id="057a6-146">資料檢視</span><span class="sxs-lookup"><span data-stu-id="057a6-146">Data View</span></span>  
 <span data-ttu-id="057a6-147">資料檢視提供資料方格，可以用來修改 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="057a6-147">Data view provides a data grid that can be used to modify .xml files.</span></span> <span data-ttu-id="057a6-148">只有 XML 檔案中的內容 (但不包含標記和結構) 可以在資料檢視中編輯。</span><span class="sxs-lookup"><span data-stu-id="057a6-148">Only the content (but not the tags and structure) in an XML file can be edited in Data view.</span></span>  
  
 <span data-ttu-id="057a6-149">資料檢視中有兩個不同的區域： **[資料表]** 與 **[資料]** 。</span><span class="sxs-lookup"><span data-stu-id="057a6-149">There are two separate areas in Data view: **Data Tables** and **Data**.</span></span> <span data-ttu-id="057a6-150">[資料表]  區域是 XML 檔案中定義的關聯清單，以巢狀結構為順序 (從最外層到最內層)。</span><span class="sxs-lookup"><span data-stu-id="057a6-150">The **Data Tables** area is a list of relations defined in the XML file, in the order of its nesting (from the outermost to the innermost).</span></span> <span data-ttu-id="057a6-151">**[資料]** 區域是資料方格，會根據資料表區域的選擇顯示資料。</span><span class="sxs-lookup"><span data-stu-id="057a6-151">The **Data** area is a data grid that displays data based on the selection in the Data Tables area.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="057a6-152">新建立的 XML 檔案中不包含資料，因此無法在資料檢視中顯示。</span><span class="sxs-lookup"><span data-stu-id="057a6-152">Newly created XML files contain no data and therefore cannot be displayed in Data view.</span></span> <span data-ttu-id="057a6-153">此外還有部份 XML文件的執行個體，其資料檢視完全無法叫用。</span><span class="sxs-lookup"><span data-stu-id="057a6-153">There are also some instances of XML documents where data view cannot be invoked at all.</span></span> <span data-ttu-id="057a6-154">即使 XML 格式正確，但如果不是結構化資料卻嘗試切換到資料檢視，則會產生下列訊息：「雖然這份文件格式正確，但其中包含資料檢視無法顯示的結構。」</span><span class="sxs-lookup"><span data-stu-id="057a6-154">Although the XML would be considered well formed, if it is not structured data trying to switch to Data view will generate the following message: "Although this document is well formed, it contains structure that Data View cannot display."</span></span>  
  
 <span data-ttu-id="057a6-155">在資料檢視中，您可以：</span><span class="sxs-lookup"><span data-stu-id="057a6-155">In Data view you can:</span></span>  
  
-   <span data-ttu-id="057a6-156">手動擴展資料表</span><span class="sxs-lookup"><span data-stu-id="057a6-156">Manually populate data tables</span></span>  
  
-   <span data-ttu-id="057a6-157">編輯現有的資料表</span><span class="sxs-lookup"><span data-stu-id="057a6-157">Edit existing data tables</span></span>  
  
-   <span data-ttu-id="057a6-158">自 XML 文件產生 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="057a6-158">Generate an XML Schema from an XML document</span></span>  
  
## <a name="xml-view"></a><span data-ttu-id="057a6-159">XML 檢視</span><span class="sxs-lookup"><span data-stu-id="057a6-159">XML View</span></span>  
 <span data-ttu-id="057a6-160">XML 檢視提供編輯器來編輯原始 XML，並提供 IntelliSense 和色彩編碼。</span><span class="sxs-lookup"><span data-stu-id="057a6-160">XML view provides an editor for editing raw XML and provides IntelliSense and color coding.</span></span> <span data-ttu-id="057a6-161">在處理具有相關聯之結構描述的 .xsd 檔案與 .xml 檔案時，可以使用陳述式完成。</span><span class="sxs-lookup"><span data-stu-id="057a6-161">Statement completion is available when working on .xsd files and .xml files that have an associated schema.</span></span> <span data-ttu-id="057a6-162">輸入 \< 以起始標記，您會看到在該位置有效的元素清單。</span><span class="sxs-lookup"><span data-stu-id="057a6-162">Type \< to initiate a tag and you will be presented with a list of elements that are valid at that location.</span></span> <span data-ttu-id="057a6-163">鍵入元素名稱並按下空格鍵之後，將會出現該元素所支援的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="057a6-163">After you type the element name and press the SPACEBAR, you will be presented with a list of attributes that the element supports.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="057a6-164">IntelliSense 選項。</span><span class="sxs-lookup"><span data-stu-id="057a6-164">IntelliSense options are not available on the toolbar.</span></span> <span data-ttu-id="057a6-165">在 XML 編輯器中，若要存取選項，請在 **[編輯]** 功能表上，按一下 **[IntelliSense]** 。</span><span class="sxs-lookup"><span data-stu-id="057a6-165">When in the XML Editor, to access the options, on the **Edit** menu, click **IntelliSense**.</span></span>  
  
## <a name="showplan-view"></a><span data-ttu-id="057a6-166">SHOWPLAN 檢視</span><span class="sxs-lookup"><span data-stu-id="057a6-166">SHOWPLAN view</span></span>  
 <span data-ttu-id="057a6-167">查詢計畫使用 SET SHOWPLAN_XML ON 選項建立時，就可以將查詢計畫以 XML 格式儲存。</span><span class="sxs-lookup"><span data-stu-id="057a6-167">Query plans can be saved in XML format when created using SET SHOWPLAN_XML ON option.</span></span> <span data-ttu-id="057a6-168">在副檔名為 .showplan 的檔案上按兩下，即可開啟查詢計畫。</span><span class="sxs-lookup"><span data-stu-id="057a6-168">Double-click a file with the .showplan extension to open the query plan.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="057a6-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="057a6-169">See Also</span></span>  
 [<span data-ttu-id="057a6-170">以 XML 格式儲存執行計畫</span><span class="sxs-lookup"><span data-stu-id="057a6-170">Save an Execution Plan in XML Format</span></span>](../performance/save-an-execution-plan-in-xml-format.md)  
  
  
