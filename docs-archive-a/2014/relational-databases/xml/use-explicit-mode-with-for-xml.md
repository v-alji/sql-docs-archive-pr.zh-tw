---
title: 搭配 FOR XML 使用 EXPLICIT 模式 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- EXPLICIT FOR XML mode
- FOR XML clause, EXPLICIT mode
- FOR XML EXPLICIT mode
ms.assetid: 8b26e8ce-5465-4e7a-b237-98d0f4578ab1
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e3db80333c74166301fcff7bb25edea4aca38a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594960"
---
# <a name="use-explicit-mode-with-for-xml"></a><span data-ttu-id="07dfc-102">搭配 FOR XML 使用 EXPLICIT 模式</span><span class="sxs-lookup"><span data-stu-id="07dfc-102">Use EXPLICIT Mode with FOR XML</span></span>
  <span data-ttu-id="07dfc-103">如 [使用 FOR XML 建構 XML](../xml/for-xml-sql-server.md)主題中所述，RAW 和 AUTO 模式對從查詢結果產生之 XML 形式的控制不大。</span><span class="sxs-lookup"><span data-stu-id="07dfc-103">As described in the topic, [Constructing XML Using FOR XML](../xml/for-xml-sql-server.md), RAW and AUTO mode do not provide much control over the shape of the XML generated from a query result.</span></span> <span data-ttu-id="07dfc-104">但是，EXPLICIT 模式在由查詢結果產生想要的 XML 方面，可提供的彈性最大。</span><span class="sxs-lookup"><span data-stu-id="07dfc-104">However, EXPLICIT mode provides the most flexibility in generating the XML you want from a query result.</span></span>  
  
 <span data-ttu-id="07dfc-105">EXPLICIT 模式詢必須以特定方式寫入，如此一來有關所需 XML 的額外資訊 (例如 XML 中將會構成的巢狀結構 )，就可以明確指定在查詢內。</span><span class="sxs-lookup"><span data-stu-id="07dfc-105">The EXPLICIT mode query must be written in a specific way so that the additional information about the required XML, such as expected nesting in the XML, is explicitly specified as part of the query.</span></span> <span data-ttu-id="07dfc-106">根據您要求使用的 XML，撰寫 EXPLICIT 模式查詢會相當繁雜。</span><span class="sxs-lookup"><span data-stu-id="07dfc-106">Depending on the XML you request, writing EXPLICIT mode queries can be cumbersome.</span></span> <span data-ttu-id="07dfc-107">您可能會發現對撰寫 EXPLICIT 模式查詢而言， [使用 PATH 模式](../xml/use-path-mode-with-for-xml.md) 搭配巢狀結構是較為簡單的替代方法。</span><span class="sxs-lookup"><span data-stu-id="07dfc-107">You may find that [Using PATH Mode](../xml/use-path-mode-with-for-xml.md) with nesting is a simpler alternative to writing EXPLICIT mode queries.</span></span>  
  
 <span data-ttu-id="07dfc-108">因為您會將想要的 XML 描述為 EXPLICIT 模式中查詢的一部份，所以您必須確定產生的 XML 有效而且格式正確。</span><span class="sxs-lookup"><span data-stu-id="07dfc-108">Because you describe the XML you want as part of the query in EXPLICIT mode, you must ensure that the generated XML is well formed and valid.</span></span>  
  
## <a name="rowset-processing-in-explicit-mode"></a><span data-ttu-id="07dfc-109">EXPLICIT 模式中的資料列集處理</span><span class="sxs-lookup"><span data-stu-id="07dfc-109">Rowset Processing in EXPLICIT Mode</span></span>  
 <span data-ttu-id="07dfc-110">EXPLICIT 模式會將執行查詢所產生的資料列集轉換為 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="07dfc-110">The EXPLICIT mode transforms the rowset that results from the query execution into an XML document.</span></span> <span data-ttu-id="07dfc-111">資料列集必須具有特定格式，EXPLICIT 模式才能產生 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="07dfc-111">In order for EXPLICIT mode to produce the XML document, the rowset must have a specific format.</span></span> <span data-ttu-id="07dfc-112">您必須撰寫 SELECT 查詢，以特定格式產生資料列集 ( **通用資料表**)，如此處理邏輯之後才能產生您想要的 XML。</span><span class="sxs-lookup"><span data-stu-id="07dfc-112">This requires that you write the SELECT query to produce the rowset, the **universal table**, with a specific format so the processing logic can then produce the XML you want.</span></span>  
  
 <span data-ttu-id="07dfc-113">首先，查詢必須產生以下兩個中繼資料資料行：</span><span class="sxs-lookup"><span data-stu-id="07dfc-113">First, the query must produce the following two metadata columns:</span></span>  
  
-   <span data-ttu-id="07dfc-114">第一個資料行必須提供目前元素的標記編號、整數類型，而且該資料行名稱必須為 **Tag**。</span><span class="sxs-lookup"><span data-stu-id="07dfc-114">The first column must provide the tag number, integer type, of the current element, and the column name must be **Tag**.</span></span> <span data-ttu-id="07dfc-115">您的查詢必須要為資料列集將要建構的每個元素，提供唯一的標記編號。</span><span class="sxs-lookup"><span data-stu-id="07dfc-115">Your query must provide a unique tag number for each element that will be constructed from the rowset.</span></span>  
  
-   <span data-ttu-id="07dfc-116">第二個資料行必須提供父元素的標記編號，而且此資料行名稱必須為 **Parent**。</span><span class="sxs-lookup"><span data-stu-id="07dfc-116">The second column must provide a tag number of the parent element, and this column name must be **Parent**.</span></span> <span data-ttu-id="07dfc-117">如此一來，「標記」與「父系」資料行就可以提供階層資訊。</span><span class="sxs-lookup"><span data-stu-id="07dfc-117">In this way, the Tag and the Parent column provide hierarchy information.</span></span>  
  
 <span data-ttu-id="07dfc-118">這些中繼資料資料行值連同資料行名稱中的資訊，都會用來產生您想要的 XML。</span><span class="sxs-lookup"><span data-stu-id="07dfc-118">These metadata column values, together with the information in the column names, are used to produce the XML you want.</span></span> <span data-ttu-id="07dfc-119">請注意，您的查詢必須以特定的方式提供資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="07dfc-119">Note that your query must provide column names in a specific way.</span></span> <span data-ttu-id="07dfc-120">此外，也請注意， **Parent** 資料行中的 0 或 NULL 表示該對應元素沒有父系。</span><span class="sxs-lookup"><span data-stu-id="07dfc-120">Also note that a 0 or NULL in the **Parent** column indicates that the corresponding element has no parent.</span></span> <span data-ttu-id="07dfc-121">該元素會作為最上層元素增加到 XML。</span><span class="sxs-lookup"><span data-stu-id="07dfc-121">The element is added to the XML as a top-level element.</span></span>  
  
 <span data-ttu-id="07dfc-122">若要了解查詢產生的通用資料表是如何處理以產生 XML 結果，假設您已經撰寫可以處理此通用資料表的查詢：</span><span class="sxs-lookup"><span data-stu-id="07dfc-122">To understand how the universal table generated by a query is processed into generating XML result, assume that you have written a query that produces this universal table:</span></span>  
  
 <span data-ttu-id="07dfc-123">![範例通用資料表](../../database-engine/media/xmlutable.gif "範例通用資料表")</span><span class="sxs-lookup"><span data-stu-id="07dfc-123">![Sample universal table](../../database-engine/media/xmlutable.gif "Sample universal table")</span></span>  
  
 <span data-ttu-id="07dfc-124">記下有關此通用資料表的下列各項：</span><span class="sxs-lookup"><span data-stu-id="07dfc-124">Note the following about this universal table:</span></span>  
  
-   <span data-ttu-id="07dfc-125">前兩個資料行是 **Tag** 和 **Parent** ，而且都是中繼資料行。</span><span class="sxs-lookup"><span data-stu-id="07dfc-125">The first two columns are **Tag** and **Parent** and are meta columns.</span></span> <span data-ttu-id="07dfc-126">這些值可以決定階層。</span><span class="sxs-lookup"><span data-stu-id="07dfc-126">These values determine the hierarchy.</span></span>  
  
-   <span data-ttu-id="07dfc-127">資料行名稱是以特定方式指定，如本主題稍後所述。</span><span class="sxs-lookup"><span data-stu-id="07dfc-127">The column names are specified in a certain way, as described later in this topic.</span></span>  
  
-   <span data-ttu-id="07dfc-128">在由此通用資料表產生 XML 時，此資料表中的資料會垂直分割成資料行群組。</span><span class="sxs-lookup"><span data-stu-id="07dfc-128">In generating the XML from this universal table, the data in this table is partitioned vertically into column groups.</span></span> <span data-ttu-id="07dfc-129">分組是根據 **Tag** 值及資料行名稱來決定。</span><span class="sxs-lookup"><span data-stu-id="07dfc-129">The grouping is determined based on the **Tag** value and the column names.</span></span> <span data-ttu-id="07dfc-130">建構 XML 時，處理邏輯會為每個資料列選取一個資料行群組並建構一個元素。</span><span class="sxs-lookup"><span data-stu-id="07dfc-130">In constructing XML, the processing logic selects one group of columns for each row and constructs an element.</span></span> <span data-ttu-id="07dfc-131">以下適用於此範例：</span><span class="sxs-lookup"><span data-stu-id="07dfc-131">The following applies in this example:</span></span>  
  
    -   <span data-ttu-id="07dfc-132">對於第一個資料列中的 **Tag** 資料行值 1，其名稱包含相同標記編號的資料行 **Customer!1!cid** 及 **Customer!1!name**會形成一個群組。</span><span class="sxs-lookup"><span data-stu-id="07dfc-132">For **Tag** column value 1 in the first row, the columns whose names include the same tag number, **Customer!1!cid** and **Customer!1!name**, form a group.</span></span> <span data-ttu-id="07dfc-133">這些資料行是用來處理資料列，而且您可能已注意到產生的元素是 <`Customer id=... name=...`>。</span><span class="sxs-lookup"><span data-stu-id="07dfc-133">These columns are used in processing the row, and you may have noticed that the shape of the generated element is <`Customer id=... name=...`>.</span></span> <span data-ttu-id="07dfc-134">資料行名稱格式會在本主題稍後描述。</span><span class="sxs-lookup"><span data-stu-id="07dfc-134">Column name format is described later in this topic.</span></span>  
  
    -   <span data-ttu-id="07dfc-135">對於 **Tag** 資料行值 2 的資料列，資料行 **Order!2!id** 及 **Order!2!date** 會形成一個群組，之後會用來建構元素 <`Order id=... date=... /`>。</span><span class="sxs-lookup"><span data-stu-id="07dfc-135">For rows with **Tag** column value 2, columns **Order!2!id** and **Order!2!date** form a group that is then used in constructing elements, <`Order id=... date=... /`>.</span></span>  
  
    -   <span data-ttu-id="07dfc-136">對於 **Tag** 資料行值 3 的資料列，資料行 **OrderDetail!3!id!id** 及 **OrderDetail!3!pid!idref** 會形成一個群組。</span><span class="sxs-lookup"><span data-stu-id="07dfc-136">For rows with **Tag** column value 3, columns **OrderDetail!3!id!id** and **OrderDetail!3!pid!idref** form a group.</span></span> <span data-ttu-id="07dfc-137">每一個資料列都會由這些資料行產生一個元素 <`OrderDetail id=... pid=...`>。</span><span class="sxs-lookup"><span data-stu-id="07dfc-137">Each of these rows generates an element, <`OrderDetail id=... pid=...`>, from these columns.</span></span>  
  
-   <span data-ttu-id="07dfc-138">請注意，在產生 XML 階層時，會依序處理資料列。</span><span class="sxs-lookup"><span data-stu-id="07dfc-138">Note that in generating XML hierarchy, the rows are processed in order.</span></span> <span data-ttu-id="07dfc-139">決定 XML 階層的方式如下所示：</span><span class="sxs-lookup"><span data-stu-id="07dfc-139">The XML hierarchy is determined as shown in the following:</span></span>  
  
    -   <span data-ttu-id="07dfc-140">第一個資料列指定 **Tag** 值 1 及 **Parent** 值 NULL。</span><span class="sxs-lookup"><span data-stu-id="07dfc-140">The first row specifies **Tag** value 1 and **Parent** value NULL.</span></span> <span data-ttu-id="07dfc-141">因此，對應的元素 (<`Customer`> 元素) 是新增為 XML 中的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="07dfc-141">Therefore, the corresponding element, <`Customer`> element, is added as a top-level element in the XML.</span></span>  
  
        ```  
        <Customer cid="C1" name="Janine">  
        ```  
  
    -   <span data-ttu-id="07dfc-142">第二個資料列指定 **Tag** 值 2 及 **Parent** 值 1。</span><span class="sxs-lookup"><span data-stu-id="07dfc-142">The second row identifies **Tag** value 2 and **Parent** value 1.</span></span> <span data-ttu-id="07dfc-143">因此，<`Order`> 元素會加入為 <`Customer`> 元素的子系。</span><span class="sxs-lookup"><span data-stu-id="07dfc-143">Therefore, the element, <`Order`> element, is added as a child of the <`Customer`> element.</span></span>  
  
        ```  
        <Customer cid="C1" name="Janine">  
           <Order id="O1" date="1/20/1996">  
        ```  
  
    -   <span data-ttu-id="07dfc-144">後面兩個資料列指定 **Tag** 值 3 及 **Parent** 值 2。</span><span class="sxs-lookup"><span data-stu-id="07dfc-144">The next two rows identify **Tag** value 3 and **Parent** value 2.</span></span> <span data-ttu-id="07dfc-145">因此，<`OrderDetail`> 這兩個元素會加入為 <`Order`> 元素的子系。</span><span class="sxs-lookup"><span data-stu-id="07dfc-145">Therefore, the two elements, <`OrderDetail`> elements, are added as children of the <`Order`> element.</span></span>  
  
        ```  
        <Customer cid="C1" name="Janine">  
           <Order id="O1" date="1/20/1996">  
              <OrderDetail id="OD1" pid="P1"/>  
              <OrderDetail id="OD2" pid="P2"/>  
        ```  
  
    -   <span data-ttu-id="07dfc-146">最後一個資料列將 2 指定為 **Tag** 編號，並將 1 指定為 **Parent** 標記編號。</span><span class="sxs-lookup"><span data-stu-id="07dfc-146">The last row identifies 2 as the **Tag** number and 1 as the **Parent** tag number.</span></span> <span data-ttu-id="07dfc-147">因此，會將另一個 <`Order`> 元素子系新增到 <`Customer`> 父元素。</span><span class="sxs-lookup"><span data-stu-id="07dfc-147">Therefore, another <`Order`> element child is added to the <`Customer`> parent element.</span></span>  
  
        ```  
        <Customer cid="C1" name="Janine">  
           <Order id="O1" date="1/20/1996">  
              <OrderDetail id="OD1" pid="P1"/>  
              <OrderDetail id="OD2" pid="P2"/>  
           </Order>  
           <Order id="O2" date="3/29/1997">  
        </Customer>  
        ```  
  
 <span data-ttu-id="07dfc-148">簡言之， **Tag** 及 **Parent** 中繼資料行中的值、資料行名稱提供的相關資訊，以及資料列的正確順序都可以在您使用 EXPLICIT 模式時，產生您想要的 XML。</span><span class="sxs-lookup"><span data-stu-id="07dfc-148">To summarize, the values in the **Tag** and **Parent** meta columns, the information provided in the column names, and the correct ordering of the rows produce the XML you want when you use EXPLICIT mode.</span></span>  
  
### <a name="universal-table-row-ordering"></a><span data-ttu-id="07dfc-149">通用資料表資料列順序</span><span class="sxs-lookup"><span data-stu-id="07dfc-149">Universal Table Row Ordering</span></span>  
 <span data-ttu-id="07dfc-150">在建構 XML 時，會按照順序處理通用資料表中的資料列集。</span><span class="sxs-lookup"><span data-stu-id="07dfc-150">In constructing the XML, the rows in the universal table are processed in order.</span></span> <span data-ttu-id="07dfc-151">因此，若要擷取與父系相關的正確子執行個體，就必須要將資料列集中的資料列排序，如此每個父節點後面就會緊跟著其所屬子系。</span><span class="sxs-lookup"><span data-stu-id="07dfc-151">Therefore, to retrieve the correct children instances associated with their parent, the rows in the rowset must be ordered so that each parent node is immediately followed by its children.</span></span>  
  
## <a name="specifying-column-names-in-a-universal-table"></a><span data-ttu-id="07dfc-152">指定通用資料表的資料行名稱</span><span class="sxs-lookup"><span data-stu-id="07dfc-152">Specifying Column Names in a Universal Table</span></span>  
 <span data-ttu-id="07dfc-153">撰寫 EXPLICIT 模式查詢時，必須使用此格式指定所產生資料列集中的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="07dfc-153">When writing EXPLICIT mode queries, column names in the resulting rowset must be specified by using this format.</span></span> <span data-ttu-id="07dfc-154">它們可提供轉換資訊，包括使用指示詞指定的元素集屬性名稱和其他資訊在內。</span><span class="sxs-lookup"><span data-stu-id="07dfc-154">They provide transformation information including element and attribute names and other additional information, specified by using directives.</span></span>  
  
 <span data-ttu-id="07dfc-155">此為一般格式：</span><span class="sxs-lookup"><span data-stu-id="07dfc-155">This is the general format:</span></span>  
  
```  
  
ElementName!TagNumber!AttributeName!Directive  
```  
  
 <span data-ttu-id="07dfc-156">以下是格式的部份描述。</span><span class="sxs-lookup"><span data-stu-id="07dfc-156">Following is the description of the parts of the format.</span></span>  
  
 <span data-ttu-id="07dfc-157">*ElementName*</span><span class="sxs-lookup"><span data-stu-id="07dfc-157">*ElementName*</span></span>  
 <span data-ttu-id="07dfc-158">是產生的元素一般識別碼。</span><span class="sxs-lookup"><span data-stu-id="07dfc-158">Is the resulting generic identifier of the element.</span></span> <span data-ttu-id="07dfc-159">例如，若將 **Customers** 指定為 *ElementName*，就會產生 \<Customers> 元素。</span><span class="sxs-lookup"><span data-stu-id="07dfc-159">For example, if **Customers** is specified as *ElementName*, the \<Customers> element is generated.</span></span>  
  
 <span data-ttu-id="07dfc-160">*TagNumber*</span><span class="sxs-lookup"><span data-stu-id="07dfc-160">*TagNumber*</span></span>  
 <span data-ttu-id="07dfc-161">是指派給元素的唯一標記值。</span><span class="sxs-lookup"><span data-stu-id="07dfc-161">Is a unique tag value assigned to an element.</span></span> <span data-ttu-id="07dfc-162">此值搭配兩個中繼資料資料行 **Tag** 及 **Parent**，就可以決定結果 XML 中元素的巢狀結構。</span><span class="sxs-lookup"><span data-stu-id="07dfc-162">This value, with the help of the two metadata columns, **Tag** and **Parent**, determines the nesting of the elements in the resulting XML.</span></span>  
  
 <span data-ttu-id="07dfc-163">*AttributeName*</span><span class="sxs-lookup"><span data-stu-id="07dfc-163">*AttributeName*</span></span>  
 <span data-ttu-id="07dfc-164">提供要在指定的 *ElementName*中建構的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="07dfc-164">Provides the name of the attribute to construct in the specified *ElementName*.</span></span> <span data-ttu-id="07dfc-165">如果未指定「指示詞」，就會使用這個行為。</span><span class="sxs-lookup"><span data-stu-id="07dfc-165">This is the behavior if *Directive* is not specified.</span></span>  
  
 <span data-ttu-id="07dfc-166">如果指定「指示詞」而且它是 **xml**、**cdata** 或 **element**，就會使用此值建構 *ElementName* 的元素子系，而且會加入資料行值。</span><span class="sxs-lookup"><span data-stu-id="07dfc-166">If *Directive* is specified and it is **xml**, **cdata**, or **element**, this value is used to construct an element child of *ElementName*, and the column value is added to it.</span></span>  
  
 <span data-ttu-id="07dfc-167">如果指定「指示詞」，*AttributeName* 可以為空白。</span><span class="sxs-lookup"><span data-stu-id="07dfc-167">If you specify the *Directive*, the *AttributeName* can be empty.</span></span> <span data-ttu-id="07dfc-168">例如，ElementName!TagNumber!!Directive。</span><span class="sxs-lookup"><span data-stu-id="07dfc-168">For example, ElementName!TagNumber!!Directive.</span></span> <span data-ttu-id="07dfc-169">在此情況下， *ElementName*會直接包含資料行值。</span><span class="sxs-lookup"><span data-stu-id="07dfc-169">In this case, the column value is directly contained by the *ElementName*.</span></span>  
  
 <span data-ttu-id="07dfc-170">*Directive*</span><span class="sxs-lookup"><span data-stu-id="07dfc-170">*Directive*</span></span>  
 <span data-ttu-id="07dfc-171">「指示詞」是選擇性的，而且您可以用以提供建構 XML 的額外資訊。 </span><span class="sxs-lookup"><span data-stu-id="07dfc-171">*Directive* is optional and you can use it to provide additional information for construction of the XML.</span></span> <span data-ttu-id="07dfc-172">「指示詞」有兩種用途。</span><span class="sxs-lookup"><span data-stu-id="07dfc-172">*Directive* has two purposes.</span></span>  
  
 <span data-ttu-id="07dfc-173">其中一項用途是將值編碼為 ID、IDREF 及 IDREFS。</span><span class="sxs-lookup"><span data-stu-id="07dfc-173">One of the purposes is to encode values as ID, IDREF, and IDREFS.</span></span> <span data-ttu-id="07dfc-174">您可以指定 **ID**、**IDREF** 及 **IDREFS** 關鍵字作為「指示詞」。</span><span class="sxs-lookup"><span data-stu-id="07dfc-174">You can specify **ID**, **IDREF**, and **IDREFS** keywords as *Directives*.</span></span> <span data-ttu-id="07dfc-175">這些指示詞會覆寫屬性類型。</span><span class="sxs-lookup"><span data-stu-id="07dfc-175">These directives overwrite the attribute types.</span></span> <span data-ttu-id="07dfc-176">您可以藉此建立內部文件連結。</span><span class="sxs-lookup"><span data-stu-id="07dfc-176">This allows you to create intra-document links.</span></span>  
  
 <span data-ttu-id="07dfc-177">此外，您可以使用「指示詞」指出要如何將字串資料對應到 XML。</span><span class="sxs-lookup"><span data-stu-id="07dfc-177">Also, you can use *Directive* to indicate how to map the string data to XML.</span></span> <span data-ttu-id="07dfc-178">**hide**、**element、elementxsinil**、**xml**、**xmltext** 及 **cdata** 關鍵字可以作為「指示詞」。</span><span class="sxs-lookup"><span data-stu-id="07dfc-178">The **hide**, **element, elementxsinil**, **xml**, **xmltext**, and **cdata** keywords can be used as the *Directive*.</span></span> <span data-ttu-id="07dfc-179">**hide** 指示詞會隱藏節點。</span><span class="sxs-lookup"><span data-stu-id="07dfc-179">The **hide** directive hides the node.</span></span> <span data-ttu-id="07dfc-180">只是為了進行排序而擷取值，但不希望產生 XML 時，這就很有用。</span><span class="sxs-lookup"><span data-stu-id="07dfc-180">This is useful when you retrieve values only for sorting purposes, but you do not want them in the resulting XML.</span></span>  
  
 <span data-ttu-id="07dfc-181">**element** 指示詞會產生內含元素而不是屬性。</span><span class="sxs-lookup"><span data-stu-id="07dfc-181">The **element** directive generates a contained element instead of an attribute.</span></span> <span data-ttu-id="07dfc-182">內含的資料會被編碼為實體。</span><span class="sxs-lookup"><span data-stu-id="07dfc-182">The contained data is encoded as an entity.</span></span> <span data-ttu-id="07dfc-183">例如， **<** 字元會變成 &lt;。</span><span class="sxs-lookup"><span data-stu-id="07dfc-183">For example, the **<** character becomes &lt;.</span></span> <span data-ttu-id="07dfc-184">對於 NULL 資料行值，不會產生任何元素。</span><span class="sxs-lookup"><span data-stu-id="07dfc-184">For NULL column values, no element is generated.</span></span> <span data-ttu-id="07dfc-185">如果希望 Null 資料行值會產生一個元素，您可以指定 **elementxsinil** 指示詞。</span><span class="sxs-lookup"><span data-stu-id="07dfc-185">If you want an element generated for null column values, you can specify the **elementxsinil** directive.</span></span> <span data-ttu-id="07dfc-186">這將會產生具有屬性 xsi:nil=TRUE 的元素。</span><span class="sxs-lookup"><span data-stu-id="07dfc-186">This will generate an element that has the attribute xsi:nil=TRUE.</span></span>  
  
 <span data-ttu-id="07dfc-187">除了不會進行實體編碼之外， **xml** 指示詞和 **element** 指示詞一樣。</span><span class="sxs-lookup"><span data-stu-id="07dfc-187">The **xml** directive is the same as an **element** directive, except that no entity encoding occurs.</span></span> <span data-ttu-id="07dfc-188">請注意， **element** 指示詞可以與 **ID**、 **IDREF**或 **IDREFS**合併，而 **xml** 指示詞不能與任何其他指示詞一起使用，除了 **hide**之外。</span><span class="sxs-lookup"><span data-stu-id="07dfc-188">Note that the **element** directive can be combined with **ID**, **IDREF**, or **IDREFS**, whereas the **xml** directive is not allowed with any other directive, except **hide**.</span></span>  
  
 <span data-ttu-id="07dfc-189">**cdata** 指示詞包含利用 CDATA 區段包裝的資料。</span><span class="sxs-lookup"><span data-stu-id="07dfc-189">The **cdata** directive contains the data by wrapping it with a CDATA section.</span></span> <span data-ttu-id="07dfc-190">內容並未進行實體編碼。</span><span class="sxs-lookup"><span data-stu-id="07dfc-190">The content is not entity encoded.</span></span> <span data-ttu-id="07dfc-191">原始資料類型必須是文字類型，例如 **varchar**、 **nvarchar**、 **text**或 **ntext**。</span><span class="sxs-lookup"><span data-stu-id="07dfc-191">The original data type must be a text type such as **varchar**, **nvarchar**, **text**, or **ntext**.</span></span> <span data-ttu-id="07dfc-192">此指示詞只適用於 **hide**。</span><span class="sxs-lookup"><span data-stu-id="07dfc-192">This directive can be used only with **hide**.</span></span> <span data-ttu-id="07dfc-193">使用此指示詞時，絕不能指定 *AttributeName* 。</span><span class="sxs-lookup"><span data-stu-id="07dfc-193">When this directive is used, *AttributeName* must not be specified.</span></span>  
  
 <span data-ttu-id="07dfc-194">在大部份情況下，您可以合併這兩個群組織間的指示詞，但不可以合併指示詞本身。</span><span class="sxs-lookup"><span data-stu-id="07dfc-194">Combining directives between these two groups is allowed in most cases, but combining them among themselves is not allowed.</span></span>  
  
 <span data-ttu-id="07dfc-195">如果未指定「指示詞」及 *AttributeName* (例如 **Customer!1**)，就會隱含 **element** 指示詞 (例如 **Customer!1!!element**)，而 *ElementName* 中會包含資料行資料。</span><span class="sxs-lookup"><span data-stu-id="07dfc-195">If the *Directive* and the *AttributeName* is not specified, for example, **Customer!1**, an **element** directive is implied, such as **Customer!1!!element**, and column data is contained in the *ElementName*.</span></span>  
  
 <span data-ttu-id="07dfc-196">如果指定 **xmltext** 指示詞，資料行內容會包裝在單一標記中，與文件的其他部分整合。</span><span class="sxs-lookup"><span data-stu-id="07dfc-196">If the **xmltext** directive is specified, the column content is wrapped in a single tag that is integrated with the rest of the document.</span></span> <span data-ttu-id="07dfc-197">此指示詞用來取得 OPENXML 儲存在資料行的溢位 (未消耗) XML 資料很有用。</span><span class="sxs-lookup"><span data-stu-id="07dfc-197">This directive is useful in fetching overflow, unconsumed, XML data stored in a column by OPENXML.</span></span> <span data-ttu-id="07dfc-198">如需詳細資訊，請參閱 [OPENXML &#40;SQL Server&#41;](../xml/openxml-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="07dfc-198">For more information, see [OPENXML &#40;SQL Server&#41;](../xml/openxml-sql-server.md).</span></span>  
  
 <span data-ttu-id="07dfc-199">如果指定 *AttributeName* ，就會以指定的名稱取代標記名稱。</span><span class="sxs-lookup"><span data-stu-id="07dfc-199">If *AttributeName* is specified, the tag name is replaced by the specified name.</span></span> <span data-ttu-id="07dfc-200">否則，將內容放在不進行實體編碼的內含項目開頭，就會在內含元素目前的屬性清單後面附加上該屬性。</span><span class="sxs-lookup"><span data-stu-id="07dfc-200">Otherwise, the attribute is appended to the current list of attributes of the enclosing elements by putting the content at the beginning of the containment without entity encoding.</span></span> <span data-ttu-id="07dfc-201">具有此指示詞的資料行必須屬於文字類型，例如 **varchar**、 **nvarchar**、 **char**、 **nchar**、 **text**或 **ntext**。</span><span class="sxs-lookup"><span data-stu-id="07dfc-201">The column with this directive must be a text type, such as **varchar**, **nvarchar**, **char**, **nchar**, **text**, or **ntext**.</span></span> <span data-ttu-id="07dfc-202">此指示詞只適用於 **hide**。</span><span class="sxs-lookup"><span data-stu-id="07dfc-202">This directive can be used only with **hide**.</span></span> <span data-ttu-id="07dfc-203">此指示詞可用來取得儲存在資料行的溢位資料。</span><span class="sxs-lookup"><span data-stu-id="07dfc-203">This directive is useful in fetching overflow data stored in a column.</span></span> <span data-ttu-id="07dfc-204">若內容不是完整形成的 XML，則行為是未定義的。</span><span class="sxs-lookup"><span data-stu-id="07dfc-204">If the content is not a well-formed XML, the behavior is undefined.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="07dfc-205">本節內容</span><span class="sxs-lookup"><span data-stu-id="07dfc-205">In This Section</span></span>  
 <span data-ttu-id="07dfc-206">下列範例說明 EXPLICIT 模式的用法。</span><span class="sxs-lookup"><span data-stu-id="07dfc-206">The following examples illustrate the use of EXPLICIT mode.</span></span>  
  
-   [<span data-ttu-id="07dfc-207">範例：擷取員工資訊</span><span class="sxs-lookup"><span data-stu-id="07dfc-207">Example: Retrieving Employee Information</span></span>](../xml/example-retrieving-employee-information.md)  
  
-   [<span data-ttu-id="07dfc-208">範例：指定 ELEMENT 指示詞</span><span class="sxs-lookup"><span data-stu-id="07dfc-208">Example: Specifying the ELEMENT Directive</span></span>](../xml/example-specifying-the-element-directive.md)  
  
-   [<span data-ttu-id="07dfc-209">範例：指定 ELEMENTXSINIL 指示詞</span><span class="sxs-lookup"><span data-stu-id="07dfc-209">Example: Specifying the ELEMENTXSINIL Directive</span></span>](../xml/example-specifying-the-elementxsinil-directive.md)  
  
-   [<span data-ttu-id="07dfc-210">範例：使用 EXPLICIT 模式建構同層級</span><span class="sxs-lookup"><span data-stu-id="07dfc-210">Example: Constructing Siblings with EXPLICIT Mode</span></span>](../xml/example-constructing-siblings-with-explicit-mode.md)  
  
-   [<span data-ttu-id="07dfc-211">範例：指定識別碼和 IDREF 指示詞</span><span class="sxs-lookup"><span data-stu-id="07dfc-211">Example: Specifying the ID and IDREF Directives</span></span>](../xml/example-specifying-the-id-and-idref-directives.md)  
  
-   [<span data-ttu-id="07dfc-212">範例：指定識別碼和 IDREFS 指示詞</span><span class="sxs-lookup"><span data-stu-id="07dfc-212">Example: Specifying the ID and IDREFS Directives</span></span>](../xml/example-specifying-the-id-and-idrefs-directives.md)  
  
-   [<span data-ttu-id="07dfc-213">範例：指定 HIDE 指示詞</span><span class="sxs-lookup"><span data-stu-id="07dfc-213">Example: Specifying the HIDE Directive</span></span>](../xml/example-specifying-the-hide-directive.md)  
  
-   [<span data-ttu-id="07dfc-214">範例：指定 ELEMENT 指示詞及實體編碼</span><span class="sxs-lookup"><span data-stu-id="07dfc-214">Example: Specifying the ELEMENT Directive and Entity Encoding</span></span>](../xml/example-specifying-the-element-directive-and-entity-encoding.md)  
  
-   [<span data-ttu-id="07dfc-215">範例：指定 CDATA 指示詞</span><span class="sxs-lookup"><span data-stu-id="07dfc-215">Example: Specifying the CDATA Directive</span></span>](../xml/example-specifying-the-cdata-directive.md)  
  
-   [<span data-ttu-id="07dfc-216">範例：指定 XMLTEXT 指示詞</span><span class="sxs-lookup"><span data-stu-id="07dfc-216">Example: Specifying the XMLTEXT Directive</span></span>](../xml/example-specifying-the-xmltext-directive.md)  
  
## <a name="see-also"></a><span data-ttu-id="07dfc-217">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07dfc-217">See Also</span></span>  
 <span data-ttu-id="07dfc-218">[使用 FOR XML 的 RAW 模式](../xml/use-raw-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="07dfc-218">[Use RAW Mode with FOR XML](../xml/use-raw-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="07dfc-219">[搭配 FOR XML 使用 AUTO 模式](../xml/use-auto-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="07dfc-219">[Use AUTO Mode with FOR XML](../xml/use-auto-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="07dfc-220">[搭配 FOR XML 使用 PATH 模式](../xml/use-path-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="07dfc-220">[Use PATH Mode with FOR XML](../xml/use-path-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="07dfc-221">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07dfc-221">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="07dfc-222">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="07dfc-222">FOR XML &#40;SQL Server&#41;</span></span>](../xml/for-xml-sql-server.md)  
  
  
