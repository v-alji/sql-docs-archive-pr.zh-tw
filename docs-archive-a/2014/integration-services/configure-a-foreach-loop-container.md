---
title: 設定 Foreach 迴圈容器 |Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Foreach Loop containers
- containers [Integration Services], Foreach Loop
ms.assetid: 519c6f96-5e1f-47d2-b96a-d49946948c25
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 85fb399f51e22e091fac9b1d8d332b9a12e7d77e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592170"
---
# <a name="configure-a-foreach-loop-container"></a><span data-ttu-id="8ba96-102">設定 Foreach 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="8ba96-102">Configure a Foreach Loop Container</span></span>
  <span data-ttu-id="8ba96-103">此程序描述如何設定「Foreach 迴圈」容器，包括列舉值及容器層級的屬性運算式。</span><span class="sxs-lookup"><span data-stu-id="8ba96-103">This procedure describes how to configure a Foreach Loop container, including property expressions at the enumerator and container levels.</span></span>  
  
### <a name="to-configure-the-foreach-loop-container"></a><span data-ttu-id="8ba96-104">設定 Foreach 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="8ba96-104">To configure the Foreach Loop container</span></span>  
  
1.  <span data-ttu-id="8ba96-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="8ba96-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="8ba96-106">按一下 [控制流程]  索引標籤，然後按兩下 [Foreach 迴圈]。</span><span class="sxs-lookup"><span data-stu-id="8ba96-106">Click the **Control Flow** tab and double-click the Foreach Loop.</span></span>  
  
3.  <span data-ttu-id="8ba96-107">在 [Foreach 迴圈編輯器]  對話方塊中，按一下 [一般]  ，然後選擇性地修改 [Foreach 迴圈] 的名稱及描述。</span><span class="sxs-lookup"><span data-stu-id="8ba96-107">In the **Foreach Loop Editor** dialog box, click **General** and, optionally, modify the name and description of the Foreach Loop.</span></span>  
  
4.  <span data-ttu-id="8ba96-108">按一下 [集合]  從 [列舉值]  清單選取列舉值類型。</span><span class="sxs-lookup"><span data-stu-id="8ba96-108">Click **Collection** and select an enumerator type from the **Enumerator** list.</span></span>  
  
5.  <span data-ttu-id="8ba96-109">指定列舉值並設定列舉值選項如下：</span><span class="sxs-lookup"><span data-stu-id="8ba96-109">Specify an enumerator and set enumerator options as follows:</span></span>  
  
    -   <span data-ttu-id="8ba96-110">若要使用 Foreach 檔案列舉值，請提供包含要列舉之檔案的資料夾，指定檔案名稱及類型的篩選，並指定是否應該傳回完整的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="8ba96-110">To usethe Foreach File enumerator, provide the folder that contains the files to enumerate, specify a filter for the file name and type, and specify whether the fully qualified file name should be returned.</span></span> <span data-ttu-id="8ba96-111">同時，指示是否遞迴所有子資料夾，以取得更多檔案。</span><span class="sxs-lookup"><span data-stu-id="8ba96-111">Also, indicate whether to recurse through subfolders for more files.</span></span>  
  
    -   <span data-ttu-id="8ba96-112">若要使用 Foreach 項目列舉值，請按一下 [資料行]  ，然後在 [For Each 項目資料行]  對話方塊中，按一下 [加入]  以加入資料行。</span><span class="sxs-lookup"><span data-stu-id="8ba96-112">To use the Foreach Item enumerator, click **Columns**, and, in the **For Each Item Columns** dialog box, click **Add** to add columns.</span></span> <span data-ttu-id="8ba96-113">在 [資料類型]  清單中為每個資料行選取資料類型，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8ba96-113">Select a data type in the **Data Type** list for each column, and click **OK**.</span></span>  
  
         <span data-ttu-id="8ba96-114">在資料行中鍵入值，或從清單選取值。</span><span class="sxs-lookup"><span data-stu-id="8ba96-114">Type values in the columns or select values from lists.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="8ba96-115">若要加入新的資料列，請按一下您鍵入項目之資料格以外的任何位置。</span><span class="sxs-lookup"><span data-stu-id="8ba96-115">To add a new row, click anywhere outside the cell in which you typed.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="8ba96-116">如果值與資料行資料類型不相容，則文字會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="8ba96-116">If a value is not compatible with the column data type, the text is highlighted.</span></span>  
  
    -   <span data-ttu-id="8ba96-117">若要使用 Foreach ADO 列舉值，請選取現有的變數，或按一下 [ADO 物件來源變數]  清單中的 [新增變數]  ，以指定包含要列舉之 ADO 物件名稱的變數，然後選取列舉模式選項。</span><span class="sxs-lookup"><span data-stu-id="8ba96-117">To use the Foreach ADO enumerator, select an existing variable or click **New variable** in the **ADO object source variable** list to specify the variable that contains the name of the ADO object to enumerate, and select an enumeration mode option.</span></span>  
  
         <span data-ttu-id="8ba96-118">如果要建立新變數，請在 [加入變數]  對話方塊中設定變數屬性。</span><span class="sxs-lookup"><span data-stu-id="8ba96-118">If creating a new variable, set the variable properties in the **Add Variable** dialog box.</span></span>  
  
    -   <span data-ttu-id="8ba96-119">若要使用 Foreach ADO.NET 結構描述資料列集列舉值，請選取現有的 ADO.NET 連接，或按一下 [連接]  清單中的 [新增連接]  ，然後選取結構描述。</span><span class="sxs-lookup"><span data-stu-id="8ba96-119">To use the Foreach ADO.NET Schema Rowset enumerator, select an existing ADO.NET connection or click **New connection** in the **Connection** list, and then select a schema.</span></span>  
  
         <span data-ttu-id="8ba96-120">您可選擇按一下 [設定限制]  並選取結構描述限制，再選取包含限制值的變數或輸入限制值，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8ba96-120">Optionally, click **Set Restrictions** and select schema restrictions, select the variable that contains the restriction value or type the restriction value, and click **OK**.</span></span>  
  
    -   <span data-ttu-id="8ba96-121">若要使用 Foreach From Variable 列舉值，請在 [變數]  清單中選取變數。</span><span class="sxs-lookup"><span data-stu-id="8ba96-121">To use the Foreach From Variable enumerator, select a variable in the **Variable** list.</span></span>  
  
    -   <span data-ttu-id="8ba96-122">若要使用 Foreach NodeList 列舉值，請按一下 [DocumentSourceType] 並從清單中選取來源類型，然後按一下 [DocumentSource]。</span><span class="sxs-lookup"><span data-stu-id="8ba96-122">To use the Foreach NodeList enumerator, click DocumentSourceType and select the source type from the list, and then click DocumentSource.</span></span> <span data-ttu-id="8ba96-123">視 DocumentSourceType 所選的值而定，從清單中選取變數或檔案連接、建立新的變數或檔案連接，或在 [文件來源編輯器]  中輸入 XML 來源。</span><span class="sxs-lookup"><span data-stu-id="8ba96-123">Depending on the value selected for DocumentSourceType, select a variable or a file connection from the list, create a new variable or file connection, or type the XML source in the **Document Source Editor**.</span></span>  
  
         <span data-ttu-id="8ba96-124">接著，按一下 [EnumerationType] 並從清單中選取列舉類型。</span><span class="sxs-lookup"><span data-stu-id="8ba96-124">Next, click EnumerationType and select an enumeration type from the list.</span></span> <span data-ttu-id="8ba96-125">如果 EnumerationType 是 **Navigator、Node 或 NodeText**，請按一下 [OuterXPathStringSourceType] 並選取來源類型，然後按一下 [OuterXPathString]。</span><span class="sxs-lookup"><span data-stu-id="8ba96-125">If EnumerationType is **Navigator, Node, or NodeText**, click OuterXPathStringSourceType and select the source type, and then click OuterXPathString.</span></span> <span data-ttu-id="8ba96-126">視 OuterXPathStringSourceType 所設定的值而定，從清單中選取變數或檔案連接、建立新的變數或檔案連接，或為外部 XML 路徑語言 (XPath) 運算式輸入字串。</span><span class="sxs-lookup"><span data-stu-id="8ba96-126">Depending on the value set for OuterXPathStringSourceType, select a variable or a file connection from the list, create a new variable or file connection, or type the string for the outer XML Path Language (XPath) expression.</span></span>  
  
         <span data-ttu-id="8ba96-127">如果 EnumerationType 是 **ElementCollection**，請如上所述設定 OuterXPathStringSourceType 和 OuterXPathString。</span><span class="sxs-lookup"><span data-stu-id="8ba96-127">If EnumerationType is **ElementCollection**,set OuterXPathStringSourceType and OuterXPathString as described above.</span></span> <span data-ttu-id="8ba96-128">然後，按一下 [InnerElementType] 並為內部元素選取列舉類型，再按一下 [InnerXPathStringSourceType]。</span><span class="sxs-lookup"><span data-stu-id="8ba96-128">Then, click InnerElementType and select an enumeration type for the inner elements, and then click InnerXPathStringSourceType.</span></span> <span data-ttu-id="8ba96-129">視 InnerXPathStringSourceType 所設定的值而定，選取變數或檔案連接、建立新的變數或檔案連接，或為內部 XPath 運算式輸入字串。</span><span class="sxs-lookup"><span data-stu-id="8ba96-129">Depending on the value set for InnerXPathStringSourceType, select a variable or a file connection, create a new variable or file connection, or type the string for the inner XPath expression.</span></span>  
  
    -   <span data-ttu-id="8ba96-130">若要使用 Foreach SMO 列舉值，請選取現有的 ADO.NET 連接，或按一下 [連接]  清單中的 [新增連接]  ，然後輸入要使用的字串或按一下 [瀏覽]  。</span><span class="sxs-lookup"><span data-stu-id="8ba96-130">To use the Foreach SMO enumerator, select an existing ADO.NET connection or click **New connection** in the **Connection** list, and then either type the string to use or click **Browse**.</span></span> <span data-ttu-id="8ba96-131">如果按一下 [選取 SMO 列舉]  對話方塊中的 [瀏覽]  ，請選取要列舉的物件類型及列舉類型，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8ba96-131">If you click **Browse**, in the **Select SMO Enumeration** dialog box, select the object type to enumerate and the enumeration type, and click **OK**.</span></span>  
  
6.  <span data-ttu-id="8ba96-132">(選擇性) 按一下 [集合]  頁面上 [運算式]  文字方塊中的瀏覽按鈕 **(...)** ，以建立更新屬性值的運算式。</span><span class="sxs-lookup"><span data-stu-id="8ba96-132">Optionally, click the browse button **(...)** in the **Expressions** text box on the **Collection** page to create expressions that update property values.</span></span> <span data-ttu-id="8ba96-133">如需詳細資訊，請參閱[加入或變更屬性運算式](expressions/add-or-change-a-property-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="8ba96-133">For more information, see [Add or Change a Property Expression](expressions/add-or-change-a-property-expression.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8ba96-134">[屬性]\*\*\*\* 清單中列出的屬性會依列舉值而不同。</span><span class="sxs-lookup"><span data-stu-id="8ba96-134">The properties listed in the **Property** list varies by enumerator.</span></span>  
  
7.  <span data-ttu-id="8ba96-135">(選擇性) 按一下 [變數對應]\*\*\*\*，以將物件屬性對應至集合值，然後執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="8ba96-135">Optionally, click **Variable Mappings** to map object properties to the collection value, and then do the following:</span></span>  
  
    1.  <span data-ttu-id="8ba96-136">在 [變數] 清單中選取變數，或按一下 **\<New Variable>** ，以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="8ba96-136">In the **Variables** list, select a variable or click **\<New Variable>** to create a new variable.</span></span>  
  
    2.  <span data-ttu-id="8ba96-137">如果您加入新的變數，請在 [加入變數]  對話方塊中設定變數屬性，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8ba96-137">If you add a new variable, set the variable properties in the **Add Variable** dialog box and click **OK**.</span></span>  
  
    3.  <span data-ttu-id="8ba96-138">如果您使用 ForEach 項目列舉值，則可以在 [索引]  清單中更新索引值。</span><span class="sxs-lookup"><span data-stu-id="8ba96-138">If you use the For Each Item enumerator, you can update the index value in the **Index** list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="8ba96-139">索引值指示項目中要對應至變數的資料行。</span><span class="sxs-lookup"><span data-stu-id="8ba96-139">The index value indicates which column in the item to map to the variable.</span></span> <span data-ttu-id="8ba96-140">只有「For Each 項目」列舉值可以使用 0 之外的索引值。</span><span class="sxs-lookup"><span data-stu-id="8ba96-140">Only the For Each Item enumerator can use an index value other than 0.</span></span>  
  
8.  <span data-ttu-id="8ba96-141">(選擇性) 按一下 [運算式]  頁面上的 [運算式]  ，建立 Foreach 迴圈容器之屬性的屬性運算式。</span><span class="sxs-lookup"><span data-stu-id="8ba96-141">Optionally, click **Expressions** and, on the **Expressions** page, create property expressions for the properties of the Foreach Loop container.</span></span> <span data-ttu-id="8ba96-142">如需詳細資訊，請參閱[加入或變更屬性運算式](expressions/add-or-change-a-property-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="8ba96-142">For more information, see [Add or Change a Property Expression](expressions/add-or-change-a-property-expression.md).</span></span>  
  
9. <span data-ttu-id="8ba96-143">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8ba96-143">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ba96-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ba96-144">See Also</span></span>  
 [<span data-ttu-id="8ba96-145">Foreach 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="8ba96-145">Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
