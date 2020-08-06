---
title: XML 報表資料的元素路徑語法 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ElementPath syntax
- XML [Reporting Services], data retrieval
ms.assetid: 07bd7a4e-fd7a-4a72-9344-3258f7c286d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b7d66b39761dc278abff25a3b22ccd18ca74272b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710241"
---
# <a name="element-path-syntax-for-xml-report-data-ssrs"></a><span data-ttu-id="f2c19-102">XML 報表資料的元素路徑語法 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="f2c19-102">Element Path Syntax for XML Report Data (SSRS)</span></span>
  <span data-ttu-id="f2c19-103">在「報表設計師」中，可藉由定義區分大小寫的元素路徑來指定要用於 XML 資料來源中之報表的資料。</span><span class="sxs-lookup"><span data-stu-id="f2c19-103">In Report Designer, you specify the data to use for a report from an XML data source by defining a case-sensitive element path.</span></span> <span data-ttu-id="f2c19-104">元素路徑會指出在 XML 資料來源中周遊 XML 階層式節點及其屬性的方法。</span><span class="sxs-lookup"><span data-stu-id="f2c19-104">An element path indicates how to traverse the XML hierarchical nodes and their attributes in the XML data source.</span></span> <span data-ttu-id="f2c19-105">若要使用預設的元素路徑，請將資料集查詢或 XML `ElementPath` (屬於 XML `Query`) 保留空白。</span><span class="sxs-lookup"><span data-stu-id="f2c19-105">To use the default element path, leave the dataset query or the XML `ElementPath` of the XML `Query` empty.</span></span> <span data-ttu-id="f2c19-106">由 XML 資料來源擷取資料時，具有文字值的元素節點以及元素節點屬性會變成結果集內的資料行。</span><span class="sxs-lookup"><span data-stu-id="f2c19-106">When data is retrieved from the XML data source, element nodes that have text values and element node attributes become columns in the result set.</span></span> <span data-ttu-id="f2c19-107">執行查詢時，節點及屬性的值會變成資料列資料。</span><span class="sxs-lookup"><span data-stu-id="f2c19-107">The values of the nodes and attributes become the row data when you run the query.</span></span> <span data-ttu-id="f2c19-108">這些資料行會以資料集欄位集合的方式顯示在 [報表資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="f2c19-108">The columns appear as the dataset field collection in the Report Data pane.</span></span> <span data-ttu-id="f2c19-109">此主題描述元素路徑語法。</span><span class="sxs-lookup"><span data-stu-id="f2c19-109">This topic describes the element path syntax.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2c19-110">元素路徑與命名空間無關。</span><span class="sxs-lookup"><span data-stu-id="f2c19-110">Element path syntax is namespace-independent.</span></span> <span data-ttu-id="f2c19-111">若要在專案路徑中使用命名空間，請使用 XML 查詢語法，其中包含 xml `ElementPath` [報表資料 &#40;SSRS&#41;的 Xml 查詢語法](report-data-ssrs.md)中所述的 xml 元素。</span><span class="sxs-lookup"><span data-stu-id="f2c19-111">To use namespaces in an element path, use the XML query syntax that includes an XML `ElementPath` element described in [XML Query Syntax for XML Report Data &#40;SSRS&#41;](report-data-ssrs.md).</span></span>  
  
 <span data-ttu-id="f2c19-112">下表描述定義元素路徑所使用的慣例。</span><span class="sxs-lookup"><span data-stu-id="f2c19-112">The following table describes conventions used to define an element path.</span></span>  
  
|<span data-ttu-id="f2c19-113">慣例</span><span class="sxs-lookup"><span data-stu-id="f2c19-113">Convention</span></span>|<span data-ttu-id="f2c19-114">用於</span><span class="sxs-lookup"><span data-stu-id="f2c19-114">Used for</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f2c19-115">**粗體字**</span><span class="sxs-lookup"><span data-stu-id="f2c19-115">**bold**</span></span>|<span data-ttu-id="f2c19-116">文字必須完全依照顯示的樣子輸入。</span><span class="sxs-lookup"><span data-stu-id="f2c19-116">Text that must be typed exactly as shown.</span></span>|  
|<span data-ttu-id="f2c19-117">&#124; (分隔號)</span><span class="sxs-lookup"><span data-stu-id="f2c19-117">&#124; (vertical bar)</span></span>|<span data-ttu-id="f2c19-118">會分隔語法項目，</span><span class="sxs-lookup"><span data-stu-id="f2c19-118">Separates syntax items.</span></span> <span data-ttu-id="f2c19-119">您只能選擇其中一個項目。</span><span class="sxs-lookup"><span data-stu-id="f2c19-119">You can choose only one of the items.</span></span>|  
|`[ ] (brackets)`|<span data-ttu-id="f2c19-120">選擇性的語法項目。</span><span class="sxs-lookup"><span data-stu-id="f2c19-120">Optional syntax items.</span></span> <span data-ttu-id="f2c19-121">不要輸入方括號。</span><span class="sxs-lookup"><span data-stu-id="f2c19-121">Do not type the brackets.</span></span>|  
|<span data-ttu-id="f2c19-122">**{}** (大括弧) </span><span class="sxs-lookup"><span data-stu-id="f2c19-122">**{ }** (braces)</span></span>|<span data-ttu-id="f2c19-123">會分隔語法項目的參數。</span><span class="sxs-lookup"><span data-stu-id="f2c19-123">Delimits parameters of syntax items.</span></span>|  
|<span data-ttu-id="f2c19-124">[ **,** ...*n*]</span><span class="sxs-lookup"><span data-stu-id="f2c19-124">[**,**...*n*]</span></span>|<span data-ttu-id="f2c19-125">指出先前項目可以重複 *n* 次。</span><span class="sxs-lookup"><span data-stu-id="f2c19-125">Indicates the preceding item can be repeated *n* number of times.</span></span> <span data-ttu-id="f2c19-126">以逗號分隔項目。</span><span class="sxs-lookup"><span data-stu-id="f2c19-126">The occurrences are separated by commas.</span></span>|  
  
## <a name="syntax"></a><span data-ttu-id="f2c19-127">語法</span><span class="sxs-lookup"><span data-stu-id="f2c19-127">Syntax</span></span>  
  
```  
  
Element path ::=  
    ElementNode[/Element path]  
ElementNode ::=  
    XMLName[(Encoding)][{[FieldList]}]  
XMLName ::=  
    [NamespacePrefix:]XMLLocalName  
Encoding ::=  
        HTMLEncoded | Base64Encoded  
FieldList ::=  
    Field[,FieldList]  
Field ::=  
    Attribute | Value | Element | ElementNode  
Attribute ::=  
        @XMLName[(Type)]  
Value ::=  
        @[(Type)]  
Element ::=  
    XMLName[(Type)]  
Type ::=  
        String | Integer | Boolean | Float | Decimal | Date | XML   
NamespacePrefix ::=  
    Identifier that specifies the namespace.  
XMLLocalName :: =  
    Identifier in the XML tag.   
```  
  
## <a name="remarks"></a><span data-ttu-id="f2c19-128">備註</span><span class="sxs-lookup"><span data-stu-id="f2c19-128">Remarks</span></span>  
 <span data-ttu-id="f2c19-129">下表摘要說明元素路徑的詞彙。</span><span class="sxs-lookup"><span data-stu-id="f2c19-129">The following table summarizes element path terms.</span></span> <span data-ttu-id="f2c19-130">表格中的範例會參考範例 XML 文件 Customers.xml (包含在本主題的「範例」一節中)。</span><span class="sxs-lookup"><span data-stu-id="f2c19-130">Examples in the table refer to the example XML document Customers.xml, which is included in the Examples section of this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2c19-131">XML 標記有區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f2c19-131">XML tags are case-sensitive.</span></span> <span data-ttu-id="f2c19-132">在元素路徑中指定 ElementNode 時，必須完全符合資料來源中的 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="f2c19-132">When you specify an ElementNode in the element path, you must exactly match the XML tags in the data source.</span></span>  
  
|<span data-ttu-id="f2c19-133">詞彙</span><span class="sxs-lookup"><span data-stu-id="f2c19-133">Term</span></span>|<span data-ttu-id="f2c19-134">定義</span><span class="sxs-lookup"><span data-stu-id="f2c19-134">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="f2c19-135">元素路徑</span><span class="sxs-lookup"><span data-stu-id="f2c19-135">Element path</span></span>|<span data-ttu-id="f2c19-136">定義 XML 文件中周遊節點的順序，以便使用 XML 資料來源擷取資料集的欄位資料。</span><span class="sxs-lookup"><span data-stu-id="f2c19-136">Defines the sequence of nodes to traverse within the XML document in order to retrieve field data for a dataset with an XML data source.</span></span>|  
|`ElementNode`|<span data-ttu-id="f2c19-137">XML 文件中的 XML 節點。</span><span class="sxs-lookup"><span data-stu-id="f2c19-137">The XML node in the XML document.</span></span> <span data-ttu-id="f2c19-138">節點是由標記指定，並存在於與其他節點構成的階層式關聯性中。</span><span class="sxs-lookup"><span data-stu-id="f2c19-138">Nodes are designated by tags and exist in a hierarchical relationship with other nodes.</span></span> <span data-ttu-id="f2c19-139">例如， \<Customers> 是根項目節點。</span><span class="sxs-lookup"><span data-stu-id="f2c19-139">For example, \<Customers> is the root element node.</span></span> <span data-ttu-id="f2c19-140">\<Customer>是的子項目 \<Customers> 。</span><span class="sxs-lookup"><span data-stu-id="f2c19-140">\<Customer> is a subelement of \<Customers>.</span></span>|  
|`XMLName`|<span data-ttu-id="f2c19-141">節點的名稱。</span><span class="sxs-lookup"><span data-stu-id="f2c19-141">The name of the node.</span></span> <span data-ttu-id="f2c19-142">例如，Customers 節點的名稱為 Customers。</span><span class="sxs-lookup"><span data-stu-id="f2c19-142">For example, the name of the Customers node is Customers.</span></span> <span data-ttu-id="f2c19-143">`XMLName` 可以使用命名空間識別碼做為前置詞，以確保所有節點的名稱都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="f2c19-143">An `XMLName` can be prefixed with a namespace identifier to uniquely name every node.</span></span>|  
|`Encoding`|<span data-ttu-id="f2c19-144">指出本元素的 `Value` 是已編碼的 XML，需要加以解碼並加入做為此元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="f2c19-144">Indicates that the `Value` for this element is encoded XML and needs to be decoded and included as a subelement of this element.</span></span>|  
|`FieldList`|<span data-ttu-id="f2c19-145">定義用來擷取資料的元素與屬性組合。</span><span class="sxs-lookup"><span data-stu-id="f2c19-145">Defines the set of elements and attributes to use to retrieve data.</span></span><br /><br /> <span data-ttu-id="f2c19-146">如果沒有指定，所有屬性和子元素都會做為欄位使用。</span><span class="sxs-lookup"><span data-stu-id="f2c19-146">If not specified, all attributes and subelements are used as fields.</span></span> <span data-ttu-id="f2c19-147">如果指定了空的欄位清單 (**{}**) ，就不會使用這個節點中的任何欄位。</span><span class="sxs-lookup"><span data-stu-id="f2c19-147">If the empty field list is specified (**{}**), no fields from this node are used.</span></span><br /><br /> <span data-ttu-id="f2c19-148">`FieldList` 可能不會同時包含 `Value` 及 `Element` 或 `ElementNode`。</span><span class="sxs-lookup"><span data-stu-id="f2c19-148">A `FieldList` may not contain both a `Value` and an `Element` or `ElementNode`.</span></span>|  
|`Field`|<span data-ttu-id="f2c19-149">指定擷取做為資料集欄位的資料。</span><span class="sxs-lookup"><span data-stu-id="f2c19-149">Specifies the data that is retrieved as a dataset field.</span></span>|  
|`Attribute`|<span data-ttu-id="f2c19-150">`ElementNode` 中名稱與值的配對。</span><span class="sxs-lookup"><span data-stu-id="f2c19-150">A name-value pair within the `ElementNode`.</span></span> <span data-ttu-id="f2c19-151">例如，在專案節點中 \<Customer ID="1"> ， `ID` 是屬性，並會 `@ID(Integer)` 在對應的資料欄位中傳回 "1" 做為整數類型 `ID` 。</span><span class="sxs-lookup"><span data-stu-id="f2c19-151">For example, in the element node \<Customer ID="1">, `ID` is an attribute and `@ID(Integer)` returns "1" as an integer type in the corresponding data field `ID`.</span></span>|  
|`Value`|<span data-ttu-id="f2c19-152">項目的值。</span><span class="sxs-lookup"><span data-stu-id="f2c19-152">The value of the element.</span></span> <span data-ttu-id="f2c19-153">`Value` 只能用於元素路徑中的最後一個 `ElementNode` 上。</span><span class="sxs-lookup"><span data-stu-id="f2c19-153">`Value` can only be used on the last `ElementNode` in the element path.</span></span> <span data-ttu-id="f2c19-154">例如，因為 \<Return> 是分葉節點，如果您將它包含在元素路徑的結尾，則的值 `Return {@}` 會是 `Chair` 。</span><span class="sxs-lookup"><span data-stu-id="f2c19-154">For example, because \<Return> is a leaf node, if you include it at the end of an element path, the value of `Return {@}` is `Chair`.</span></span>|  
|`Element`|<span data-ttu-id="f2c19-155">具名子元素的值。</span><span class="sxs-lookup"><span data-stu-id="f2c19-155">The value of the named subelement.</span></span> <span data-ttu-id="f2c19-156">例如，Customers {}/Customer {}/LastName 只會擷取 LastName 元素的值。</span><span class="sxs-lookup"><span data-stu-id="f2c19-156">For example, Customers {}/Customer {}/LastName retrieves values for only the LastName element.</span></span>|  
|`Type`|<span data-ttu-id="f2c19-157">此元素建立之欄位所使用的選擇性資料類型。</span><span class="sxs-lookup"><span data-stu-id="f2c19-157">The optional data type to use for the field created from this element.</span></span>|  
|`NamespacePrefix`|<span data-ttu-id="f2c19-158">`NamespacePrefix` 是在 XML 查詢元素中定義。</span><span class="sxs-lookup"><span data-stu-id="f2c19-158">`NamespacePrefix` is defined in the XML Query element.</span></span> <span data-ttu-id="f2c19-159">如果 XML 查詢元素不存在，則會省略 XML `ElementPath` 中的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f2c19-159">If no XML Query element exists, namespaces in the XML `ElementPath` are ignored.</span></span> <span data-ttu-id="f2c19-160">如果有 XML 查詢元素，XML `ElementPath` 則會有選擇性的 `IgnoreNamespaces` 屬性。</span><span class="sxs-lookup"><span data-stu-id="f2c19-160">If there is an XML Query element, the XML `ElementPath` has an optional attribute `IgnoreNamespaces`.</span></span> <span data-ttu-id="f2c19-161">如果 IgnoreNamespaces 為 `true` ，則 xml 和 xml 檔中的命名空間 `ElementPath` 會被忽略。</span><span class="sxs-lookup"><span data-stu-id="f2c19-161">If IgnoreNamespaces is `true`, namespaces in the XML `ElementPath` and the XML document are ignored.</span></span> <span data-ttu-id="f2c19-162">如需詳細資訊，請參閱 [XML 報表資料的 XML 查詢語法 &#40;SSRS&#41;](report-data-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f2c19-162">For more information, see [XML Query Syntax for XML Report Data &#40;SSRS&#41;](report-data-ssrs.md).</span></span>|  
  
## <a name="example---no-namespaces"></a><span data-ttu-id="f2c19-163">範例 - 沒有命名空間</span><span class="sxs-lookup"><span data-stu-id="f2c19-163">Example - No Namespaces</span></span>  
 <span data-ttu-id="f2c19-164">下列範例會使用 XML 文件 Customers.xml。</span><span class="sxs-lookup"><span data-stu-id="f2c19-164">The following examples use the XML document Customers.xml.</span></span> <span data-ttu-id="f2c19-165">這個表格會顯示元素路徑語法的範例，並且以 XML 文件為資料來源，顯示在定義資料集的查詢中使用元素路徑的結果。</span><span class="sxs-lookup"><span data-stu-id="f2c19-165">This table shows examples of element path syntax and the results of using the element path in a query that defines a dataset, based on the XML document as a data source.</span></span>  
  
 <span data-ttu-id="f2c19-166">請注意，當元素路徑是空的時，查詢會使用預設的元素路徑：第一個分葉節點集合的路徑。</span><span class="sxs-lookup"><span data-stu-id="f2c19-166">Note that when the element path is empty, the query uses the default element path: the first path to a leaf node collection.</span></span> <span data-ttu-id="f2c19-167">在第一個範例中，將元素路徑保留為空白相當於將元素路徑指定為 /Customers/Customer/Orders/Order。</span><span class="sxs-lookup"><span data-stu-id="f2c19-167">In the first example, leaving the element path empty is equivalent to specifying the element path /Customers/Customer/Orders/Order.</span></span> <span data-ttu-id="f2c19-168">路徑上的所有節點值和屬性都會傳回到結果集，而節點名稱和屬性會以資料集欄位的方式顯示。</span><span class="sxs-lookup"><span data-stu-id="f2c19-168">All node value and attributes along the path are returned in the result set, and the node names and attributes names appear as dataset fields.</span></span>  
  
-   <span data-ttu-id="f2c19-169">*空白*</span><span class="sxs-lookup"><span data-stu-id="f2c19-169">*Empty*</span></span>  
  
    |<span data-ttu-id="f2c19-170">單</span><span class="sxs-lookup"><span data-stu-id="f2c19-170">Order</span></span>|<span data-ttu-id="f2c19-171">數量</span><span class="sxs-lookup"><span data-stu-id="f2c19-171">Qty</span></span>|<span data-ttu-id="f2c19-172">識別碼</span><span class="sxs-lookup"><span data-stu-id="f2c19-172">ID</span></span>|<span data-ttu-id="f2c19-173">名字</span><span class="sxs-lookup"><span data-stu-id="f2c19-173">FirstName</span></span>|<span data-ttu-id="f2c19-174">姓氏</span><span class="sxs-lookup"><span data-stu-id="f2c19-174">LastName</span></span>|<span data-ttu-id="f2c19-175">Customer.ID</span><span class="sxs-lookup"><span data-stu-id="f2c19-175">Customer.ID</span></span>|<span data-ttu-id="f2c19-176">xmlns</span><span class="sxs-lookup"><span data-stu-id="f2c19-176">xmlns</span></span>|  
    |-----------|---------|--------|---------------|--------------|-----------------|-----------|  
    |<span data-ttu-id="f2c19-177">Chair</span><span class="sxs-lookup"><span data-stu-id="f2c19-177">Chair</span></span>|<span data-ttu-id="f2c19-178">6</span><span class="sxs-lookup"><span data-stu-id="f2c19-178">6</span></span>|<span data-ttu-id="f2c19-179">1</span><span class="sxs-lookup"><span data-stu-id="f2c19-179">1</span></span>|<span data-ttu-id="f2c19-180">Bobby</span><span class="sxs-lookup"><span data-stu-id="f2c19-180">Bobby</span></span>|<span data-ttu-id="f2c19-181">Moore</span><span class="sxs-lookup"><span data-stu-id="f2c19-181">Moore</span></span>|<span data-ttu-id="f2c19-182">11</span><span class="sxs-lookup"><span data-stu-id="f2c19-182">11</span></span>|http://www.adventure-works.com|  
    |<span data-ttu-id="f2c19-183">資料表</span><span class="sxs-lookup"><span data-stu-id="f2c19-183">Table</span></span>|<span data-ttu-id="f2c19-184">1</span><span class="sxs-lookup"><span data-stu-id="f2c19-184">1</span></span>|<span data-ttu-id="f2c19-185">2</span><span class="sxs-lookup"><span data-stu-id="f2c19-185">2</span></span>|<span data-ttu-id="f2c19-186">Bobby</span><span class="sxs-lookup"><span data-stu-id="f2c19-186">Bobby</span></span>|<span data-ttu-id="f2c19-187">Moore</span><span class="sxs-lookup"><span data-stu-id="f2c19-187">Moore</span></span>|<span data-ttu-id="f2c19-188">11</span><span class="sxs-lookup"><span data-stu-id="f2c19-188">11</span></span>|http://www.adventure-works.com|  
    |<span data-ttu-id="f2c19-189">Sofa</span><span class="sxs-lookup"><span data-stu-id="f2c19-189">Sofa</span></span>|<span data-ttu-id="f2c19-190">2</span><span class="sxs-lookup"><span data-stu-id="f2c19-190">2</span></span>|<span data-ttu-id="f2c19-191">8</span><span class="sxs-lookup"><span data-stu-id="f2c19-191">8</span></span>|<span data-ttu-id="f2c19-192">Crystal</span><span class="sxs-lookup"><span data-stu-id="f2c19-192">Crystal</span></span>|<span data-ttu-id="f2c19-193">Hu</span><span class="sxs-lookup"><span data-stu-id="f2c19-193">Hu</span></span>|<span data-ttu-id="f2c19-194">20</span><span class="sxs-lookup"><span data-stu-id="f2c19-194">20</span></span>|http://www.adventure-works.com|  
    |<span data-ttu-id="f2c19-195">EndTables</span><span class="sxs-lookup"><span data-stu-id="f2c19-195">EndTables</span></span>|<span data-ttu-id="f2c19-196">2</span><span class="sxs-lookup"><span data-stu-id="f2c19-196">2</span></span>|<span data-ttu-id="f2c19-197">15</span><span class="sxs-lookup"><span data-stu-id="f2c19-197">15</span></span>|<span data-ttu-id="f2c19-198">Wyatt</span><span class="sxs-lookup"><span data-stu-id="f2c19-198">Wyatt</span></span>|<span data-ttu-id="f2c19-199">Diaz</span><span class="sxs-lookup"><span data-stu-id="f2c19-199">Diaz</span></span>|<span data-ttu-id="f2c19-200">33</span><span class="sxs-lookup"><span data-stu-id="f2c19-200">33</span></span>|http://www.adventure-works.com|  
  
-   `Customers {}/Customer`  
  
    |<span data-ttu-id="f2c19-201">名字</span><span class="sxs-lookup"><span data-stu-id="f2c19-201">FirstName</span></span>|<span data-ttu-id="f2c19-202">姓氏</span><span class="sxs-lookup"><span data-stu-id="f2c19-202">LastName</span></span>|<span data-ttu-id="f2c19-203">識別碼</span><span class="sxs-lookup"><span data-stu-id="f2c19-203">ID</span></span>|  
    |---------------|--------------|--------|  
    |<span data-ttu-id="f2c19-204">Bobby</span><span class="sxs-lookup"><span data-stu-id="f2c19-204">Bobby</span></span>|<span data-ttu-id="f2c19-205">Moore</span><span class="sxs-lookup"><span data-stu-id="f2c19-205">Moore</span></span>|<span data-ttu-id="f2c19-206">11</span><span class="sxs-lookup"><span data-stu-id="f2c19-206">11</span></span>|  
    |<span data-ttu-id="f2c19-207">Crystal</span><span class="sxs-lookup"><span data-stu-id="f2c19-207">Crystal</span></span>|<span data-ttu-id="f2c19-208">Hu</span><span class="sxs-lookup"><span data-stu-id="f2c19-208">Hu</span></span>|<span data-ttu-id="f2c19-209">20</span><span class="sxs-lookup"><span data-stu-id="f2c19-209">20</span></span>|  
    |<span data-ttu-id="f2c19-210">Wyatt</span><span class="sxs-lookup"><span data-stu-id="f2c19-210">Wyatt</span></span>|<span data-ttu-id="f2c19-211">Diaz</span><span class="sxs-lookup"><span data-stu-id="f2c19-211">Diaz</span></span>|<span data-ttu-id="f2c19-212">33</span><span class="sxs-lookup"><span data-stu-id="f2c19-212">33</span></span>|  
  
-   `Customers {}/Customer {}/LastName`  
  
    |<span data-ttu-id="f2c19-213">姓氏</span><span class="sxs-lookup"><span data-stu-id="f2c19-213">LastName</span></span>|  
    |--------------|  
    |<span data-ttu-id="f2c19-214">Moore</span><span class="sxs-lookup"><span data-stu-id="f2c19-214">Moore</span></span>|  
    |<span data-ttu-id="f2c19-215">Hu</span><span class="sxs-lookup"><span data-stu-id="f2c19-215">Hu</span></span>|  
    |<span data-ttu-id="f2c19-216">Diaz</span><span class="sxs-lookup"><span data-stu-id="f2c19-216">Diaz</span></span>|  
  
-   `Customers {}/Customer {}/Orders/Order {@,@Qty}`  
  
    |<span data-ttu-id="f2c19-217">單</span><span class="sxs-lookup"><span data-stu-id="f2c19-217">Order</span></span>|<span data-ttu-id="f2c19-218">數量</span><span class="sxs-lookup"><span data-stu-id="f2c19-218">Qty</span></span>|  
    |-----------|---------|  
    |<span data-ttu-id="f2c19-219">Chair</span><span class="sxs-lookup"><span data-stu-id="f2c19-219">Chair</span></span>|<span data-ttu-id="f2c19-220">6</span><span class="sxs-lookup"><span data-stu-id="f2c19-220">6</span></span>|  
    |<span data-ttu-id="f2c19-221">資料表</span><span class="sxs-lookup"><span data-stu-id="f2c19-221">Table</span></span>|<span data-ttu-id="f2c19-222">1</span><span class="sxs-lookup"><span data-stu-id="f2c19-222">1</span></span>|  
    |<span data-ttu-id="f2c19-223">Sofa</span><span class="sxs-lookup"><span data-stu-id="f2c19-223">Sofa</span></span>|<span data-ttu-id="f2c19-224">2</span><span class="sxs-lookup"><span data-stu-id="f2c19-224">2</span></span>|  
    |<span data-ttu-id="f2c19-225">EndTables</span><span class="sxs-lookup"><span data-stu-id="f2c19-225">EndTables</span></span>|<span data-ttu-id="f2c19-226">2</span><span class="sxs-lookup"><span data-stu-id="f2c19-226">2</span></span>|  
  
-   `Customers {}/Customer/Orders/Order{ @ID(Integer)}`  
  
    |<span data-ttu-id="f2c19-227">Order.ID</span><span class="sxs-lookup"><span data-stu-id="f2c19-227">Order.ID</span></span>|<span data-ttu-id="f2c19-228">名字</span><span class="sxs-lookup"><span data-stu-id="f2c19-228">FirstName</span></span>|<span data-ttu-id="f2c19-229">姓氏</span><span class="sxs-lookup"><span data-stu-id="f2c19-229">LastName</span></span>|<span data-ttu-id="f2c19-230">識別碼</span><span class="sxs-lookup"><span data-stu-id="f2c19-230">ID</span></span>|  
    |--------------|---------------|--------------|--------|  
    |<span data-ttu-id="f2c19-231">1</span><span class="sxs-lookup"><span data-stu-id="f2c19-231">1</span></span>|<span data-ttu-id="f2c19-232">Bobby</span><span class="sxs-lookup"><span data-stu-id="f2c19-232">Bobby</span></span>|<span data-ttu-id="f2c19-233">Moore</span><span class="sxs-lookup"><span data-stu-id="f2c19-233">Moore</span></span>|<span data-ttu-id="f2c19-234">11</span><span class="sxs-lookup"><span data-stu-id="f2c19-234">11</span></span>|  
    |<span data-ttu-id="f2c19-235">2</span><span class="sxs-lookup"><span data-stu-id="f2c19-235">2</span></span>|<span data-ttu-id="f2c19-236">Bobby</span><span class="sxs-lookup"><span data-stu-id="f2c19-236">Bobby</span></span>|<span data-ttu-id="f2c19-237">Moore</span><span class="sxs-lookup"><span data-stu-id="f2c19-237">Moore</span></span>|<span data-ttu-id="f2c19-238">11</span><span class="sxs-lookup"><span data-stu-id="f2c19-238">11</span></span>|  
    |<span data-ttu-id="f2c19-239">8</span><span class="sxs-lookup"><span data-stu-id="f2c19-239">8</span></span>|<span data-ttu-id="f2c19-240">Crystal</span><span class="sxs-lookup"><span data-stu-id="f2c19-240">Crystal</span></span>|<span data-ttu-id="f2c19-241">Hu</span><span class="sxs-lookup"><span data-stu-id="f2c19-241">Hu</span></span>|<span data-ttu-id="f2c19-242">20</span><span class="sxs-lookup"><span data-stu-id="f2c19-242">20</span></span>|  
    |<span data-ttu-id="f2c19-243">15</span><span class="sxs-lookup"><span data-stu-id="f2c19-243">15</span></span>|<span data-ttu-id="f2c19-244">Wyatt</span><span class="sxs-lookup"><span data-stu-id="f2c19-244">Wyatt</span></span>|<span data-ttu-id="f2c19-245">Diaz</span><span class="sxs-lookup"><span data-stu-id="f2c19-245">Diaz</span></span>|<span data-ttu-id="f2c19-246">33</span><span class="sxs-lookup"><span data-stu-id="f2c19-246">33</span></span>|  
  
#### <a name="xml-document-customersxml"></a><span data-ttu-id="f2c19-247">XML 文件：Customers.xml</span><span class="sxs-lookup"><span data-stu-id="f2c19-247">XML document: Customers.xml</span></span>  
 <span data-ttu-id="f2c19-248">若要嘗試前一節中的元素路徑範例，可以複製這段 XML 並將它儲存為報表設計師可以存取的 URL，然後使用 XML 文件做為 XML 資料來源：例如 `http://localhost/Customers.xml`。</span><span class="sxs-lookup"><span data-stu-id="f2c19-248">To try out the element path examples in the previous section, you can copy this XML and save it to a URL that is accessible by Report Designer, and then use the XML document as an XML data source: for example, `http://localhost/Customers.xml`.</span></span>  
  
```  
<?xml version="1.0"?>  
<Customers xmlns="http://www.adventure-works.com">  
   <Customer ID="11">  
      <FirstName>Bobby</FirstName>  
      <LastName>Moore</LastName>  
      <Orders>  
         <Order ID="1" Qty="6">Chair</Order>  
         <Order ID="2" Qty="1">Table</Order>  
      </Orders>  
      <Returns>  
         <Return ID="1" Qty="2">Chair</Return>  
      </Returns>  
   </Customer>  
   <Customer ID="20">  
      <FirstName>Crystal</FirstName>  
      <LastName>Hu</LastName>  
      <Orders>  
         <Order ID="8" Qty="2">Sofa</Order>  
      </Orders>  
      <Returns/>  
   </Customer>  
   <Customer ID="33">  
      <FirstName>Wyatt</FirstName>  
      <LastName>Diaz</LastName>  
      <Orders>  
         <Order ID="15" Qty="2">EndTables</Order>  
      </Orders>  
      <Returns/>  
   </Customer>  
</Customers>  
```  
  
 <span data-ttu-id="f2c19-249">您也可以使用下列程序來建立 XML 資料來源，其中不包含連接字串，查詢中也不內嵌 Customers.XML。</span><span class="sxs-lookup"><span data-stu-id="f2c19-249">Alternatively, you can create an XML data source that has no connection string and embed Customers.XML in the query, using the following procedure:</span></span>  
  
###### <a name="to-embed-customersxml-in-a-query"></a><span data-ttu-id="f2c19-250">在查詢中內嵌 Customers.XML</span><span class="sxs-lookup"><span data-stu-id="f2c19-250">To embed Customers.XML in a query</span></span>  
  
1.  <span data-ttu-id="f2c19-251">使用空白連接字串建立 XML 資料來源。</span><span class="sxs-lookup"><span data-stu-id="f2c19-251">Create an XML data source with a blank connection string.</span></span>  
  
2.  <span data-ttu-id="f2c19-252">建立 XML 資料來源的新資料集。</span><span class="sxs-lookup"><span data-stu-id="f2c19-252">Create a new dataset for the XML data source.</span></span>  
  
3.  <span data-ttu-id="f2c19-253">在 **[資料集屬性]** 對話方塊中，按一下 **[查詢設計工具]**。</span><span class="sxs-lookup"><span data-stu-id="f2c19-253">In the **Dataset Properties** dialog box, click **Query Designer**.</span></span> <span data-ttu-id="f2c19-254">以文字為基礎的查詢設計工具對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f2c19-254">The text-based query designer dialog box opens.</span></span>  
  
4.  <span data-ttu-id="f2c19-255">在查詢窗格中，輸入下列兩行程式碼：</span><span class="sxs-lookup"><span data-stu-id="f2c19-255">In the query pane, enter the following two lines:</span></span>  
  
     `<Query>`  
  
     `<XmlData>`  
  
5.  <span data-ttu-id="f2c19-256">複製 Customers.XML，然後將這些文字貼在查詢窗格中的 `<XmlData>`之後。</span><span class="sxs-lookup"><span data-stu-id="f2c19-256">Copy Customers.XML and paste the text in the query pane after `<XmlData>`.</span></span>  
  
6.  <span data-ttu-id="f2c19-257">在查詢窗格中，刪除從 Customers.XML 複製的第一行程式碼： `<?xml version="1.0"?>`</span><span class="sxs-lookup"><span data-stu-id="f2c19-257">In the query pane, delete the first line that you copied from Customers.XML: `<?xml version="1.0"?>`</span></span>  
  
7.  <span data-ttu-id="f2c19-258">在查詢尾端，加入下列兩行程式碼：</span><span class="sxs-lookup"><span data-stu-id="f2c19-258">At the end of the query, add the following two lines:</span></span>  
  
     `<XmlData>`  
  
     `<Query>`  
  
8.  <span data-ttu-id="f2c19-259">按一下 [執行查詢]\*\*\*\* \(!)。</span><span class="sxs-lookup"><span data-stu-id="f2c19-259">Click **Run Query** (!).</span></span>  
  
     <span data-ttu-id="f2c19-260">結果集會顯示具有下列資料行的 4 行資料： `xmlns`、 `Customer.ID`、 `FirstName`、 `LastName`、 `ID`、 `Qty`、 `Order`。</span><span class="sxs-lookup"><span data-stu-id="f2c19-260">The result set displays 4 lines of data with the following columns: `xmlns`, `Customer.ID`, `FirstName`, `LastName`, `ID`, `Qty`, `Order`.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f2c19-261">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2c19-261">See Also</span></span>  
 <span data-ttu-id="f2c19-262">[XML 連線類型 &#40;SSRS&#41;](xml-connection-type-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f2c19-262">[XML Connection Type &#40;SSRS&#41;](xml-connection-type-ssrs.md) </span></span>  
 <span data-ttu-id="f2c19-263">[Reporting Services SSRS &#40;的教學課程&#41;](../reporting-services-tutorials-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f2c19-263">[Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md) </span></span>  
 [<span data-ttu-id="f2c19-264">加入、編輯、重新整理報表資料窗格中的欄位 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f2c19-264">Add, Edit, Refresh Fields in the Report Data Pane &#40;Report Builder and SSRS&#41;</span></span>](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md)  
  
  
