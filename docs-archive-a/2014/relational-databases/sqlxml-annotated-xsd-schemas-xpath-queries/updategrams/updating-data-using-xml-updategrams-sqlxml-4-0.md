---
title: 使用 XML Updategram 更新資料 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREF type attribute [SQLXML]
- before attribute
- <sync> block
- <after> block
- id attribute
- <before> block
- updg:after attribute
- mapping-schema attribute
- IDREFS type attribute [SQLXML]
- updg:id attribute
- multiple record updates
- after attribute
- updategrams [SQLXML], updating data
- updg:before attribute
- record updates [SQLXML]
ms.assetid: 90ef8a33-5ae3-4984-8259-608d2f1d727f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6b019478868b61f293eda824d9b302099728dec4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597739"
---
# <a name="updating-data-using-xml-updategrams-sqlxml-40"></a><span data-ttu-id="ade8a-102">使用 XML Updategram 更新資料 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="ade8a-102">Updating Data Using XML Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="ade8a-103">當您更新現有的資料時，您必須同時指定 **\<before>** 和 **\<after>** 區塊。</span><span class="sxs-lookup"><span data-stu-id="ade8a-103">When you update existing data, you must specify both the **\<before>** and **\<after>** blocks.</span></span> <span data-ttu-id="ade8a-104">和區塊中指定的元素會 **\<before>** **\<after>** 描述所需的變更。</span><span class="sxs-lookup"><span data-stu-id="ade8a-104">The elements specified in the **\<before>** and **\<after>** blocks describe the desired change.</span></span> <span data-ttu-id="ade8a-105">Updategram 會使用區塊中指定的 (s) 元素， **\<before>** 來識別資料庫中 (s) 的現有記錄。</span><span class="sxs-lookup"><span data-stu-id="ade8a-105">The updategram uses the element(s) that are specified in the **\<before>** block to identify the existing record(s) in the database.</span></span> <span data-ttu-id="ade8a-106">區塊中 (s) 的對應元素， **\<after>** 會指出記錄在執行更新作業之後的外觀。</span><span class="sxs-lookup"><span data-stu-id="ade8a-106">The corresponding element(s) in the **\<after>** block indicate how the records should look after executing the update operation.</span></span> <span data-ttu-id="ade8a-107">在此資訊中，updategram 會建立符合區塊的 SQL 語句 **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="ade8a-107">From this information, the updategram creates an SQL statement that matches the **\<after>** block.</span></span> <span data-ttu-id="ade8a-108">接著，Updategram 會使用此陳述式來更新資料庫。</span><span class="sxs-lookup"><span data-stu-id="ade8a-108">The updategram then uses this statement to update the database.</span></span>  
  
 <span data-ttu-id="ade8a-109">下列是更新作業的 Updategram 格式：</span><span class="sxs-lookup"><span data-stu-id="ade8a-109">This is the updategram format for an update operation:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync [mapping-schema="SampleSchema.xml"]  >  
   <updg:before>  
      <ElementName [updg:id="value"] .../>  
      [<ElementName [updg:id="value"] .../> ... ]  
   </updg:before>  
   <updg:after>  
      <ElementName [updg:id="value"] ... />  
      [<ElementName [updg:id="value"] .../> ...]  
   </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 `<updg:before>`  
 <span data-ttu-id="ade8a-110">區塊中的元素 **\<before>** 可識別資料庫資料表中的現有記錄。</span><span class="sxs-lookup"><span data-stu-id="ade8a-110">The elements in the **\<before>** block identify existing records in the database tables.</span></span>  
  
 `<updg:after>`  
 <span data-ttu-id="ade8a-111">區塊中的元素 **\<after>** 會描述在套用更新之後，區塊中指定的記錄 **\<before>** 應如何查看。</span><span class="sxs-lookup"><span data-stu-id="ade8a-111">The elements in the **\<after>** block describe how the records specified in the **\<before>** block should look after the updates are applied.</span></span>  
  
 <span data-ttu-id="ade8a-112">`mapping-schema` 屬性會識別 Updategram 所使用的對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="ade8a-112">The `mapping-schema` attribute identifies the mapping schema to be used by the updategram.</span></span> <span data-ttu-id="ade8a-113">如果 updategram 指定對應架構，則在和區塊中指定的元素和屬性 **\<before>** 名稱 **\<after>** 必須符合架構中的名稱。</span><span class="sxs-lookup"><span data-stu-id="ade8a-113">If the updategram specifies a mapping schema, the element and attribute names specified in the **\<before>** and **\<after>** blocks must match the names in the schema.</span></span> <span data-ttu-id="ade8a-114">對應的結構描述會將這些元素或屬性名稱對應到資料庫資料表和資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="ade8a-114">The mapping schema maps these element or attribute names to the database table and column names.</span></span>  
  
 <span data-ttu-id="ade8a-115">如果 Updategram 沒有指定結構描述，Updategram 會使用預設的對應。</span><span class="sxs-lookup"><span data-stu-id="ade8a-115">If an updategram does not specify a schema, the updategam uses default mapping.</span></span> <span data-ttu-id="ade8a-116">在預設的對應中， **\<ElementName>** updategram 中指定的會對應至資料庫資料表，而子項目或屬性則會對應至資料庫資料行。</span><span class="sxs-lookup"><span data-stu-id="ade8a-116">In default mapping, the **\<ElementName>** specified in the updategram maps to the database table and the child elements or attributes map to the database columns.</span></span>  
  
 <span data-ttu-id="ade8a-117">區塊中的元素 **\<before>** 必須與資料庫中只有一個資料表資料列相符。</span><span class="sxs-lookup"><span data-stu-id="ade8a-117">An element in the **\<before>** block must match with only one table row in the database.</span></span> <span data-ttu-id="ade8a-118">如果元素符合多個資料表資料列，或不符合任何資料表資料列，則 updategram 會傳回錯誤並取消整個 **\<sync>** 區塊。</span><span class="sxs-lookup"><span data-stu-id="ade8a-118">If the element either matches multiple table rows or does not match any table row, the updategram returns an error and cancels the entire **\<sync>** block.</span></span>  
  
 <span data-ttu-id="ade8a-119">Updategram 可以包含多個 **\<sync>** 區塊。</span><span class="sxs-lookup"><span data-stu-id="ade8a-119">An updategram can include multiple **\<sync>** blocks.</span></span> <span data-ttu-id="ade8a-120">**\<sync>** 會將每個區塊視為一筆交易。</span><span class="sxs-lookup"><span data-stu-id="ade8a-120">Each **\<sync>** block is treated as a transaction.</span></span> <span data-ttu-id="ade8a-121">每個 **\<sync>** 區塊可以有多個 **\<before>** 和 **\<after>** 區塊。</span><span class="sxs-lookup"><span data-stu-id="ade8a-121">Each **\<sync>** block can have multiple **\<before>** and **\<after>** blocks.</span></span> <span data-ttu-id="ade8a-122">例如，如果您要更新兩個現有的記錄，您可以指定兩個 **\<before>** 和 **\<after>** 配對，每個更新的記錄一個。</span><span class="sxs-lookup"><span data-stu-id="ade8a-122">For example, if you are updating two of the existing records, you could specify two **\<before>** and **\<after>** pairs, one for each record being updated.</span></span>  
  
## <a name="using-the-updgid-attribute"></a><span data-ttu-id="ade8a-123">使用 updg:id 屬性</span><span class="sxs-lookup"><span data-stu-id="ade8a-123">Using the updg:id Attribute</span></span>  
 <span data-ttu-id="ade8a-124">在和區塊中指定多個元素時 **\<before>** **\<after>** ，請使用 `updg:id` 屬性來標記 **\<before>** 和區塊中的 **\<after>** 資料列。</span><span class="sxs-lookup"><span data-stu-id="ade8a-124">When multiple elements are specified in the **\<before>** and **\<after>** blocks, use the `updg:id` attribute to mark rows in the **\<before>** and **\<after>** blocks.</span></span> <span data-ttu-id="ade8a-125">處理邏輯會使用這項資訊來判斷區塊中的哪個記錄 **\<before>** 與區塊中的哪一筆記錄 **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="ade8a-125">The processing logic uses this information to determine what record in the **\<before>** block pairs with what record in the **\<after>** block.</span></span>  
  
 <span data-ttu-id="ade8a-126">如果下列其中一個項目存在，就不需要 `updg:id` 屬性 (但建議存在)：</span><span class="sxs-lookup"><span data-stu-id="ade8a-126">The `updg:id` attribute is not necessary (although recommended) if either of the following exists:</span></span>  
  
-   <span data-ttu-id="ade8a-127">指定之對應結構描述中的元素已經定義 `sql:key-fields` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ade8a-127">The elements in the specified mapping schema have the `sql:key-fields` attribute defined on them.</span></span>  
  
-   <span data-ttu-id="ade8a-128">在 Updategram 中有一或多個針對索引鍵欄位提供的特定值。</span><span class="sxs-lookup"><span data-stu-id="ade8a-128">There is one or more specific value supplied for the key field(s) in the updategram.</span></span>  
  
 <span data-ttu-id="ade8a-129">如果是這種情況，updategram 會使用中指定的索引鍵資料行 `sql:key-fields` 來配對和區塊中的元素 **\<before>** **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="ade8a-129">If either is the case, the updategram uses the key columns that are specified in the `sql:key-fields` to pair the elements in the **\<before>** and **\<after>** blocks.</span></span>  
  
 <span data-ttu-id="ade8a-130">如果對應結構描述沒有識別索引鍵資料行 (透過使用 `sql:key-fields`)，或者如果 Updategram 要更新索引鍵資料行值，您必須指定 `updg:id`。</span><span class="sxs-lookup"><span data-stu-id="ade8a-130">If the mapping schema does not identify key columns (by using `sql:key-fields`) or if the updategram is updating a key column value, you must specify `updg:id`.</span></span>  
  
 <span data-ttu-id="ade8a-131">在和區塊中識別的記錄 **\<before>** **\<after>** 不一定要有相同的順序。</span><span class="sxs-lookup"><span data-stu-id="ade8a-131">The records that are identified in the **\<before>** and **\<after>** blocks do not have to be in the same order.</span></span> <span data-ttu-id="ade8a-132">`updg:id`屬性會強制在和區塊中指定的元素之間產生關聯 **\<before>** **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="ade8a-132">The `updg:id` attribute forces the association between the elements that are specified in the **\<before>** and **\<after>** blocks.</span></span>  
  
 <span data-ttu-id="ade8a-133">如果您在區塊中指定一個元素， **\<before>** 而且在區塊中只有一個對應的元素 **\<after>** ， `updg:id` 則不需要使用。</span><span class="sxs-lookup"><span data-stu-id="ade8a-133">If you specify one element in the **\<before>** block and only one corresponding element in the **\<after>** block, using `updg:id` is not necessary.</span></span> <span data-ttu-id="ade8a-134">不過，建議您無論如何還是指定 `updg:id` 來避免模稜兩可的情況。</span><span class="sxs-lookup"><span data-stu-id="ade8a-134">However, it is recommended that you specify `updg:id` anyway to avoid ambiguity.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ade8a-135">範例</span><span class="sxs-lookup"><span data-stu-id="ade8a-135">Examples</span></span>  
 <span data-ttu-id="ade8a-136">使用 Updategram 範例之前，請注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="ade8a-136">Before you use the updategram examples, note the following:</span></span>  
  
-   <span data-ttu-id="ade8a-137">大部分的範例都會使用預設對應 (也就是說，Updategram 中不會指定任何對應結構描述)。</span><span class="sxs-lookup"><span data-stu-id="ade8a-137">Most of the examples use default mapping (that is, no mapping schema is specified in the updategram).</span></span> <span data-ttu-id="ade8a-138">如需使用對應架構之 updategram 的更多範例，請參閱[在 Updategram 中指定批註式對應架構 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="ade8a-138">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="ade8a-139">大部分的範例會使用 AdventureWorks 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="ade8a-139">Most of the examples use the AdventureWorks sample database.</span></span> <span data-ttu-id="ade8a-140">所有的更新都會套用到此資料庫內的資料表。</span><span class="sxs-lookup"><span data-stu-id="ade8a-140">All the updates are applied to the tables in this database.</span></span> <span data-ttu-id="ade8a-141">您可以還原 AdventureWorks 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ade8a-141">You can restore the AdventureWorks database.</span></span>  
  
### <a name="a-updating-a-record"></a><span data-ttu-id="ade8a-142">A.</span><span class="sxs-lookup"><span data-stu-id="ade8a-142">A.</span></span> <span data-ttu-id="ade8a-143">更新記錄</span><span class="sxs-lookup"><span data-stu-id="ade8a-143">Updating a record</span></span>  
 <span data-ttu-id="ade8a-144">下列 Updategram 會在 AdventureWorks 資料庫的 Person.Contact 資料表中，將員工姓氏更新為 Fuller。</span><span class="sxs-lookup"><span data-stu-id="ade8a-144">The following updategram updates the employee last name to Fuller in the Person.Contact table in the AdventureWorks database.</span></span> <span data-ttu-id="ade8a-145">Updategram 沒有指定任何對應結構描述，因此，Updategam 會使用預設的對應。</span><span class="sxs-lookup"><span data-stu-id="ade8a-145">The updategram does not specify any mapping schema; therefore, the updategram uses default mapping.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" />  
</updg:before>  
<updg:after>  
   <Person.Contact LastName="Abel-Achong" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="ade8a-146">區塊中所述的記錄 **\<before>** 代表資料庫中的目前記錄。</span><span class="sxs-lookup"><span data-stu-id="ade8a-146">The record described in the **\<before>** block represents the current record in the database.</span></span> <span data-ttu-id="ade8a-147">Updategram 會使用區塊中指定的所有資料行值 **\<before>** 來搜尋記錄。</span><span class="sxs-lookup"><span data-stu-id="ade8a-147">The updategram uses all of the column values specified in the **\<before>** block to search for the record.</span></span> <span data-ttu-id="ade8a-148">在此 updategram 中， **\<before>** 區塊僅提供 ContactID 資料行，因此，updategram 只會使用值來搜尋記錄。</span><span class="sxs-lookup"><span data-stu-id="ade8a-148">In this updategram, the **\<before>** block provides only the ContactID column; therefore, the updategram uses only the value to search for the record.</span></span> <span data-ttu-id="ade8a-149">如果您要將 LastName 值加入到此區塊中，Updategram 會同時使用 ContactID 和 LastName 值進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="ade8a-149">If you were to add the LastName value to this block, the updategram would use both the ContactID and LastName values to search.</span></span>  
  
 <span data-ttu-id="ade8a-150">在此 updategram 中， **\<after>** 區塊只會提供 LastName 資料行值，因為這是唯一變更的值。</span><span class="sxs-lookup"><span data-stu-id="ade8a-150">In this updategram, the **\<after>** block provides only the LastName column value because this is the only value that is being changed.</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="ade8a-151">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="ade8a-151">To test the updategram</span></span>  
  
1.  <span data-ttu-id="ade8a-152">複製上述的 updategram 範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="ade8a-152">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="ade8a-153">將檔案儲存為 UpdateLastName.xml。</span><span class="sxs-lookup"><span data-stu-id="ade8a-153">Save the file as UpdateLastName.xml.</span></span>  
  
2.  <span data-ttu-id="ade8a-154">建立及使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行 Updategram。</span><span class="sxs-lookup"><span data-stu-id="ade8a-154">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="ade8a-155">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="ade8a-155">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="b-updating-multiple-records-by-using-the-updgid-attribute"></a><span data-ttu-id="ade8a-156">B.</span><span class="sxs-lookup"><span data-stu-id="ade8a-156">B.</span></span> <span data-ttu-id="ade8a-157">使用 updg:id 屬性更新多筆記錄</span><span class="sxs-lookup"><span data-stu-id="ade8a-157">Updating multiple records by using the updg:id attribute</span></span>  
 <span data-ttu-id="ade8a-158">在此範例中，updategram 會在 AdventureWorks 資料庫的 HumanResources.Shift 資料表上執行兩個變更：</span><span class="sxs-lookup"><span data-stu-id="ade8a-158">In this example, the updategram performs two updates on the HumanResources.Shift table in the AdventureWorks database:</span></span>  
  
-   <span data-ttu-id="ade8a-159">它會將早上七點起的原始日班名稱從 "Day" 變更為 "Early Morning"。</span><span class="sxs-lookup"><span data-stu-id="ade8a-159">It changes the name of the original day shift that starts at 7:00AM from "Day" to "Early Morning".</span></span>  
  
-   <span data-ttu-id="ade8a-160">它會插入名稱為 "Late Morning" 的新輪班，從早上十點開始。</span><span class="sxs-lookup"><span data-stu-id="ade8a-160">It inserts a new shift named "Late Morning" that starts at 10:00AM.</span></span>  
  
 <span data-ttu-id="ade8a-161">在 updategram 中，屬性會在 `updg:id` 和區塊中的元素之間建立關聯 **\<before>** **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="ade8a-161">In the updategram, the `updg:id` attribute creates associations between elements in the **\<before>** and **\<after>** blocks.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift updg:id="x" Name="Day" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift updg:id="y" Name="Late Morning"   
                            StartTime="1900-01-01 10:00:00.000"  
                            EndTime="1900-01-01 18:00:00.000"  
                            ModifiedDate="2004-06-01 00:00:00.000"/>  
      <HumanResources.Shift updg:id="x" Name="Early Morning" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="ade8a-162">請注意， `updg:id` 屬性如何將區塊中元素的第一個實例 \<HumanResources.Shift> **\<before>** 與區塊中專案的第二個實例配對 \<HumanResources.Shift> **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="ade8a-162">Notice how the `updg:id` attribute pairs the first instance of the \<HumanResources.Shift> element in the **\<before>** block with the second instance of the \<HumanResources.Shift> element in the **\<after>** block.</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="ade8a-163">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="ade8a-163">To test the updategram</span></span>  
  
1.  <span data-ttu-id="ade8a-164">複製上述的 updategram 範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="ade8a-164">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="ade8a-165">將檔案儲存為 UpdateMultipleRecords.xml。</span><span class="sxs-lookup"><span data-stu-id="ade8a-165">Save the file as UpdateMultipleRecords.xml.</span></span>  
  
2.  <span data-ttu-id="ade8a-166">建立及使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行 Updategram。</span><span class="sxs-lookup"><span data-stu-id="ade8a-166">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="ade8a-167">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="ade8a-167">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="c-specifying-multiple-before-and-after-blocks"></a><span data-ttu-id="ade8a-168">C.</span><span class="sxs-lookup"><span data-stu-id="ade8a-168">C.</span></span> <span data-ttu-id="ade8a-169">指定多個 \<before> 和 \<after> 區塊</span><span class="sxs-lookup"><span data-stu-id="ade8a-169">Specifying multiple \<before> and \<after> blocks</span></span>  
 <span data-ttu-id="ade8a-170">若要避免不明確，您可以使用多個 **\<before>** 和區塊配對，在範例 B 中撰寫 updategram **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="ade8a-170">To avoid ambiguity, you can write the updategram in Example B by using multiple **\<before>** and **\<after>** block pairs.</span></span> <span data-ttu-id="ade8a-171">指定 **\<before>** 和 **\<after>** 配對是一種指定多個更新的方式，最小的混淆。</span><span class="sxs-lookup"><span data-stu-id="ade8a-171">Specifying **\<before>** and **\<after>** pairs is one way of specifying multiple updates with a minimum of confusion.</span></span> <span data-ttu-id="ade8a-172">此外，如果 **\<before>** 和 **\<after>** 區塊最多指定一個元素，您就不需要使用 `updg:id` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ade8a-172">Also, if each of the **\<before>** and **\<after>** blocks specify at most one element, you do not have to use the `updg:id` attribute.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ade8a-173">若要形成一組配對， **\<after>** 標記必須緊接在其對應的 **\<before>** 標記之後。</span><span class="sxs-lookup"><span data-stu-id="ade8a-173">To form a pair, the **\<after>** tag must immediately follow its corresponding **\<before>** tag.</span></span>  
  
 <span data-ttu-id="ade8a-174">在下列 updategram 中，第一個 **\<before>** 和 **\<after>** 配對會更新 day shift 的 shift 名稱。</span><span class="sxs-lookup"><span data-stu-id="ade8a-174">In the following updategram, the first **\<before>** and **\<after>** pair updates the shift name for the day shift.</span></span> <span data-ttu-id="ade8a-175">第二個配對會插入新的輪班記錄。</span><span class="sxs-lookup"><span data-stu-id="ade8a-175">The second pair inserts a new shift record.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="1" Name="Day" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="Early Morning" />  
    </updg:after>  
    <updg:before>  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="Late Morning"   
                            StartTime="1900-01-01 10:00:00.000"  
                            EndTime="1900-01-01 18:00:00.000"  
                            ModifiedDate="2004-06-01 00:00:00.000"/>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="ade8a-176">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="ade8a-176">To test the updategram</span></span>  
  
1.  <span data-ttu-id="ade8a-177">複製上述的 updategram 範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="ade8a-177">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="ade8a-178">將檔案儲存為 UpdateMultipleBeforeAfter.xml。</span><span class="sxs-lookup"><span data-stu-id="ade8a-178">Save the file as UpdateMultipleBeforeAfter.xml.</span></span>  
  
2.  <span data-ttu-id="ade8a-179">建立及使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行 Updategram。</span><span class="sxs-lookup"><span data-stu-id="ade8a-179">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="ade8a-180">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="ade8a-180">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="d-specifying-multiple-sync-blocks"></a><span data-ttu-id="ade8a-181">D.</span><span class="sxs-lookup"><span data-stu-id="ade8a-181">D.</span></span> <span data-ttu-id="ade8a-182">指定多個 \<sync> 區塊</span><span class="sxs-lookup"><span data-stu-id="ade8a-182">Specifying multiple \<sync> blocks</span></span>  
 <span data-ttu-id="ade8a-183">您可以 **\<sync>** 在 updategram 中指定多個區塊。</span><span class="sxs-lookup"><span data-stu-id="ade8a-183">You can specify multiple **\<sync>** blocks in an updategram.</span></span> <span data-ttu-id="ade8a-184">所指定的每個 **\<sync>** 區塊都是獨立的交易。</span><span class="sxs-lookup"><span data-stu-id="ade8a-184">Each **\<sync>** block that is specified is an independent transaction.</span></span>  
  
 <span data-ttu-id="ade8a-185">在下列 updategram 中，第一個 **\<sync>** 區塊會更新 Sales. Customer 資料表中的記錄。</span><span class="sxs-lookup"><span data-stu-id="ade8a-185">In the following updategram, the first **\<sync>** block updates a record in the Sales.Customer table.</span></span> <span data-ttu-id="ade8a-186">為了簡單起見，Updategram 僅會指定所需的資料行值；識別值 (CustomerID) 以及要更新的值 (SalesPersonID)。</span><span class="sxs-lookup"><span data-stu-id="ade8a-186">For the sake of simplicity, the updategram specifies only the required column values; the identity value (CustomerID) and the value being updated (SalesPersonID).</span></span>  
  
 <span data-ttu-id="ade8a-187">第二個 **\<sync>** 區塊會將兩筆記錄加入 SalesOrderHeader 資料表。</span><span class="sxs-lookup"><span data-stu-id="ade8a-187">The second **\<sync>** block adds two records to the Sales.SalesOrderHeader table.</span></span> <span data-ttu-id="ade8a-188">針對這個資料表，SalesOrderID 是 IDENTITY 類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="ade8a-188">For this table, SalesOrderID is an IDENTITY-type column.</span></span> <span data-ttu-id="ade8a-189">因此，updategram 不會在每個元素中指定 SalesOrderID 的值 \<Sales.SalesOrderHeader> 。</span><span class="sxs-lookup"><span data-stu-id="ade8a-189">Therefore, the updategram does not specify the value of SalesOrderID in each of the \<Sales.SalesOrderHeader> elements.</span></span>  
  
 <span data-ttu-id="ade8a-190">指定多個 **\<sync>** 區塊很有用，因為如果第二個 **\<sync>** 區塊 (交易) 無法將記錄加入 SalesOrderHeader 資料表中，則第 **\<sync>** 一個區塊仍然可以更新 sales. customer 資料表中的客戶記錄。</span><span class="sxs-lookup"><span data-stu-id="ade8a-190">Specifying multiple **\<sync>** blocks is useful because if the second **\<sync>** block (a transaction) fails to add records to Sales.SalesOrderHeader table, the first **\<sync>** block can still update the customer record in the Sales.Customer table.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
      <Sales.Customer CustomerID="1" SalesPersonID="280" />  
    </updg:before>  
    <updg:after>  
      <Sales.Customer CustomerID="1" SalesPersonID="283" />  
    </updg:after>  
  </updg:sync>  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
   <Sales.SalesOrderHeader   
             CustomerID="1"  
             RevisionNumber="1"  
             OrderDate="2004-07-01 00:00:00.000"  
             DueDate="2004-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="01010101-2222-3333-4444-556677889900"  
             ModifiedDate="2004-07-08 00:00:00.000" />  
   <Sales.SalesOrderHeader  
             CustomerID="1"  
             RevisionNumber="1"  
             OrderDate="2004-07-01 00:00:00.000"  
             DueDate="2004-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="1000.0000"  
             TaxAmt="0.0000"  
             Freight="0.0000"  
             rowguid="10101010-2222-3333-4444-556677889900"  
             ModifiedDate="2004-07-09 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="ade8a-191">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="ade8a-191">To test the updategram</span></span>  
  
1.  <span data-ttu-id="ade8a-192">複製上述的 updategram 範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="ade8a-192">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="ade8a-193">將檔案儲存為 UpdateMultipleSyncs.xml。</span><span class="sxs-lookup"><span data-stu-id="ade8a-193">Save the file as UpdateMultipleSyncs.xml.</span></span>  
  
2.  <span data-ttu-id="ade8a-194">建立及使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行 Updategram。</span><span class="sxs-lookup"><span data-stu-id="ade8a-194">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="ade8a-195">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="ade8a-195">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="e-using-a-mapping-schema"></a><span data-ttu-id="ade8a-196">E.</span><span class="sxs-lookup"><span data-stu-id="ade8a-196">E.</span></span> <span data-ttu-id="ade8a-197">使用對應的結構描述</span><span class="sxs-lookup"><span data-stu-id="ade8a-197">Using a mapping schema</span></span>  
 <span data-ttu-id="ade8a-198">在此範例中，Updategram 會使用 `mapping-schema` 屬性指定對應的結構描述 </span><span class="sxs-lookup"><span data-stu-id="ade8a-198">In this example, the updategram specifies a mapping schema by using the `mapping-schema` attribute.</span></span> <span data-ttu-id="ade8a-199">(沒有預設的對應，也就是說，對應結構描述會在 Updategram 中提供所需的元素和屬性對應給資料庫資料表與資料行)。</span><span class="sxs-lookup"><span data-stu-id="ade8a-199">(There is no default mapping; that is, the mapping schema provides the necessary mapping of elements and attributes in the updategram to the database tables and columns.)</span></span>  
  
 <span data-ttu-id="ade8a-200">在 Updategram 中指定的元素和屬性指的是對應結構描述中的元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="ade8a-200">The elements and attributes specified in the updategram refer to the elements and attributes in the mapping schema.</span></span>  
  
 <span data-ttu-id="ade8a-201">下列 XSD 對應架構具有 **\<Customer>** 、和專案， **\<Order>** 這些專案 **\<OD>** 會對應至資料庫中的 Customer、SalesOrderHeader 和 sales. SalesOrderDetail 資料表。</span><span class="sxs-lookup"><span data-stu-id="ade8a-201">The following XSD mapping schema has **\<Customer>**, **\<Order>**, and **\<OD>** elements that map to the Sales.Customer, Sales.SalesOrderHeader, and Sales.SalesOrderDetail tables in the database.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustomerOrder"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  
    <sql:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustomerOrder" >  
           <xsd:complexType>  
              <xsd:sequence>  
                <xsd:element name="OD"   
                             sql:relation="Sales.SalesOrderDetail"  
                             sql:relationship="OrderOD" >  
                 <xsd:complexType>  
                  <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                  <xsd:attribute name="ProductID" type="xsd:integer" />  
                  <xsd:attribute name="UnitPrice" type="xsd:decimal" />  
                  <xsd:attribute name="OrderQty" type="xsd:integer" />  
                  <xsd:attribute name="UnitPriceDiscount" type="xsd:decimal" />   
                 </xsd:complexType>  
                </xsd:element>  
              </xsd:sequence>  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="OrderDate" type="xsd:date" />  
           </xsd:complexType>  
        </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="ade8a-202">此對應結構描述 (UpdategramMappingSchema.xml) 會在下列的 Updategram 中指定。</span><span class="sxs-lookup"><span data-stu-id="ade8a-202">This mapping schema (UpdategramMappingSchema.xml) is specified in the following updategram.</span></span> <span data-ttu-id="ade8a-203">Updategram 會針對特定的訂單，在 Sales.SalesOrderDetail 資料表中加入訂單詳細資料項目。</span><span class="sxs-lookup"><span data-stu-id="ade8a-203">The updategram adds an order detail item in the Sales.SalesOrderDetail table for a specific order.</span></span> <span data-ttu-id="ade8a-204">Updategram 包含 nested 元素：在專案 **\<OD>** 內嵌套的元素 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="ade8a-204">The updategram includes nested elements: an **\<OD>** element nested inside an **\<Order>** element.</span></span> <span data-ttu-id="ade8a-205">在這兩個元素之間的主索引鍵/外部索引鍵關聯性會在對應的結構描述中指定。</span><span class="sxs-lookup"><span data-stu-id="ade8a-205">The primary key/foreign key relationship between these two elements is specified in the mapping schema.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="UpdategramMappingSchema.xml" >  
    <updg:before>  
       <Order SalesOrderID="43659" />  
    </updg:before>  
    <updg:after>  
      <Order SalesOrderID="43659" >  
          <OD ProductID="776" UnitPrice="2329.0000"  
              OrderQty="2" UnitPriceDiscount="0.0" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="ade8a-206">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="ade8a-206">To test the updategram</span></span>  
  
1.  <span data-ttu-id="ade8a-207">複製上述的對應結構描述，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="ade8a-207">Copy the mapping schema above and paste it into a text file.</span></span> <span data-ttu-id="ade8a-208">將檔案儲存為 UpdategramMappingSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="ade8a-208">Save the file as UpdategramMappingSchema.xml.</span></span>  
  
2.  <span data-ttu-id="ade8a-209">複製上述的 updategram 範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="ade8a-209">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="ade8a-210">然後將檔案在先前用於儲存對應結構描述 (UpdategramMappingSchema.xml) 的相同資料夾中，儲存為 UpdateWithMappingSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="ade8a-210">Save the file as UpdateWithMappingSchema.xml in the same folder as was used to save the mapping schema (UpdategramMappingSchema.xml).</span></span>  
  
3.  <span data-ttu-id="ade8a-211">建立及使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行 Updategram。</span><span class="sxs-lookup"><span data-stu-id="ade8a-211">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="ade8a-212">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="ade8a-212">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="ade8a-213">如需使用對應架構之 updategram 的更多範例，請參閱[在 Updategram 中指定批註式對應架構 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="ade8a-213">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
### <a name="f-using-a-mapping-schema-with-idrefs-attributes"></a><span data-ttu-id="ade8a-214">F.</span><span class="sxs-lookup"><span data-stu-id="ade8a-214">F.</span></span> <span data-ttu-id="ade8a-215">搭配 IDREFS 屬性使用對應的結構描述</span><span class="sxs-lookup"><span data-stu-id="ade8a-215">Using a mapping schema with IDREFS attributes</span></span>  
 <span data-ttu-id="ade8a-216">此範例說明 Updategrams 如何使用對應結構描述中的 IDREFS 屬性更新多個資料表中的記錄。</span><span class="sxs-lookup"><span data-stu-id="ade8a-216">This example illustrates how updategrams use the IDREFS attributes in the mapping schema to update records in multiple tables.</span></span> <span data-ttu-id="ade8a-217">此範例假設資料庫由下列資料表組成：</span><span class="sxs-lookup"><span data-stu-id="ade8a-217">For this example, assume that the database consists of the following tables:</span></span>  
  
-   <span data-ttu-id="ade8a-218">Student(StudentID, LastName)</span><span class="sxs-lookup"><span data-stu-id="ade8a-218">Student(StudentID, LastName)</span></span>  
  
-   <span data-ttu-id="ade8a-219">Course(CourseID, CourseName)</span><span class="sxs-lookup"><span data-stu-id="ade8a-219">Course(CourseID, CourseName)</span></span>  
  
-   <span data-ttu-id="ade8a-220">Enrollment(StudentID, CourseID)</span><span class="sxs-lookup"><span data-stu-id="ade8a-220">Enrollment(StudentID, CourseID)</span></span>  
  
 <span data-ttu-id="ade8a-221">因為一位學生可以註冊許多課程，而且一個課程可以有許多學生，因此需要第三個資料表，也就是 Enrollment 資料表，來代表這個 M:N 關聯性。</span><span class="sxs-lookup"><span data-stu-id="ade8a-221">Because a student can enroll in many courses and a course can have many students, the third table, the Enrollment table, is required to represent this M:N relationship.</span></span>  
  
 <span data-ttu-id="ade8a-222">下列 XSD 對應架構會使用 **\<Student>** 、和元素來提供資料表的 XML 視圖 **\<Course>** **\<Enrollment>** 。</span><span class="sxs-lookup"><span data-stu-id="ade8a-222">The following XSD mapping schema provides an XML view of the tables by using the **\<Student>**, **\<Course>**, and **\<Enrollment>** elements.</span></span> <span data-ttu-id="ade8a-223">對應架構中的**IDREFS**屬性會指定這些元素之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="ade8a-223">The **IDREFS** attributes in the mapping schema specify the relationship between these elements.</span></span> <span data-ttu-id="ade8a-224">元素上的**StudentIDList**屬性 **\<Course>** 是一個**IDREFS**類型屬性，它會參考註冊資料表中的 StudentID 資料行。</span><span class="sxs-lookup"><span data-stu-id="ade8a-224">The **StudentIDList** attribute on the **\<Course>** element is an **IDREFS** type attribute that refers to the StudentID column in the Enrollment table.</span></span> <span data-ttu-id="ade8a-225">同樣地，元素上的**EnrolledIn**屬性 **\<Student>** 是一個**IDREFS**類型屬性，它會參考註冊資料表中的 CourseID 資料行。</span><span class="sxs-lookup"><span data-stu-id="ade8a-225">Likewise, the **EnrolledIn** attribute on the **\<Student>** element is an **IDREFS** type attribute that refers to the CourseID column in the Enrollment table.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="StudentEnrollment"  
          parent="Student"  
          parent-key="StudentID"  
          child="Enrollment"  
          child-key="StudentID" />  
  
    <sql:relationship name="CourseEnrollment"  
          parent="Course"  
          parent-key="CourseID"  
          child="Enrollment"  
          child-key="CourseID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Course" sql:relation="Course"   
                             sql:key-fields="CourseID" >  
    <xsd:complexType>  
    <xsd:attribute name="CourseID"  type="xsd:string" />   
    <xsd:attribute name="CourseName"   type="xsd:string" />   
    <xsd:attribute name="StudentIDList" sql:relation="Enrollment"  
                 sql:field="StudentID"  
                 sql:relationship="CourseEnrollment"   
                                     type="xsd:IDREFS" />  
  
    </xsd:complexType>  
  </xsd:element>  
  <xsd:element name="Student" sql:relation="Student" >  
    <xsd:complexType>  
    <xsd:attribute name="StudentID"  type="xsd:string" />   
    <xsd:attribute name="LastName"   type="xsd:string" />   
    <xsd:attribute name="EnrolledIn" sql:relation="Enrollment"  
                 sql:field="CourseID"  
                 sql:relationship="StudentEnrollment"   
                                     type="xsd:IDREFS" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="ade8a-226">每當您在 Updategram 中指定此結構描述，並在 Course 資料表中插入記錄時，Updategram 會在 Course 資料表中插入一個新的課程記錄。</span><span class="sxs-lookup"><span data-stu-id="ade8a-226">Whenever you specify this schema in an updategram and insert a record in the Course table, the updategram inserts a new course record in the Course table.</span></span> <span data-ttu-id="ade8a-227">如果您為 the StudentIDList 屬性指定一或多個新的學生識別碼，Updategram 也會為每個新的學生，在 Enrollment 資料表中插入一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="ade8a-227">If you specify one or more new student IDs for the StudentIDList attribute, the updategram also inserts a record in the Enrollment table for the each new student.</span></span> <span data-ttu-id="ade8a-228">Updategram 可確保沒有將重複項目加入到 Enrollment 資料表中。</span><span class="sxs-lookup"><span data-stu-id="ade8a-228">The updategram ensures that no duplicates are added to the Enrollment table.</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="ade8a-229">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="ade8a-229">To test the updategram</span></span>  
  
1.  <span data-ttu-id="ade8a-230">在資料庫中建立虛擬根目錄中指定的這些資料表：</span><span class="sxs-lookup"><span data-stu-id="ade8a-230">Create these tables in the database that is specified in the virtual root:</span></span>  
  
    ```  
    CREATE TABLE Student(StudentID varchar(10) primary key,   
                         LastName varchar(25))  
    CREATE TABLE Course(CourseID varchar(10) primary key,   
                        CourseName varchar(25))  
    CREATE TABLE Enrollment(StudentID varchar(10)   
                                      references Student(StudentID),  
                           CourseID varchar(10)   
                                      references Course(CourseID))  
    ```  
  
2.  <span data-ttu-id="ade8a-231">加入這個範例資料：</span><span class="sxs-lookup"><span data-stu-id="ade8a-231">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Student VALUES ('S1','Davoli')  
    INSERT INTO Student VALUES ('S2','Fuller')  
  
    INSERT INTO Course VALUES  ('CS101', 'C Programming')  
    INSERT INTO Course VALUES  ('CS102', 'Understanding XML')  
  
    INSERT INTO Enrollment VALUES ('S1', 'CS101')  
    INSERT INTO Enrollment VALUES ('S1', 'CS102')  
    ```  
  
3.  <span data-ttu-id="ade8a-232">複製上述的對應結構描述，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="ade8a-232">Copy the mapping schema above and paste it into a text file.</span></span> <span data-ttu-id="ade8a-233">將檔案儲存為 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="ade8a-233">Save the file as SampleSchema.xml.</span></span>  
  
4.  <span data-ttu-id="ade8a-234">將 Updategram (SampleUpdategram) 儲存在前述步驟用於儲存對應結構描述的相同資料夾中 </span><span class="sxs-lookup"><span data-stu-id="ade8a-234">Save the updategram (SampleUpdategram) in the same folder used to save the mapping schema in the previous step.</span></span> <span data-ttu-id="ade8a-235">(這個 Updategram 會從 CS102 課程中卸除 StudentID="1" 的學生)。</span><span class="sxs-lookup"><span data-stu-id="ade8a-235">(This updategram drops a student with StudentID="1" from the CS102 course.)</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101 CS102" />  
        </updg:before>  
        <updg:after >  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
5.  <span data-ttu-id="ade8a-236">建立及使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行 Updategram。</span><span class="sxs-lookup"><span data-stu-id="ade8a-236">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="ade8a-237">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="ade8a-237">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
6.  <span data-ttu-id="ade8a-238">儲存並執行下列 Updategram，如前述步驟所述。</span><span class="sxs-lookup"><span data-stu-id="ade8a-238">Save and execute the following updategram as described in the previous steps.</span></span> <span data-ttu-id="ade8a-239">Updategram 會在 Enrollment 資料表中加入一筆記錄，藉以將 StudentID="1" 的學生加回 CS102 課程。</span><span class="sxs-lookup"><span data-stu-id="ade8a-239">The updategram adds the student with StudentID="1" back into the CS102 course by adding a record in the Enrollment table.</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101" />  
        </updg:before>  
        <updg:after >  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101 CS102" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
7.  <span data-ttu-id="ade8a-240">儲存並執行這個接下來的 Updategram，如前述步驟所述。</span><span class="sxs-lookup"><span data-stu-id="ade8a-240">Save and execute this next updategram as described in the previous steps.</span></span> <span data-ttu-id="ade8a-241">這個 Updategram 會插入三個新的學生，並為他們註冊 CS101 課程。</span><span class="sxs-lookup"><span data-stu-id="ade8a-241">This updategram inserts three new students and enrolls them in the CS101 course.</span></span> <span data-ttu-id="ade8a-242">IDREFS 關聯性會將資料表再次插入 Enrollment 資料表中。</span><span class="sxs-lookup"><span data-stu-id="ade8a-242">Again, the IDREFS relationship inserts records in the Enrollment table.</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
           <Course updg:id="y" CourseID="CS101"   
                               CourseName="C Programming" />  
        </updg:before>  
        <updg:after >  
           <Student updg:id="x1" StudentID="S3" LastName="Leverling" />  
           <Student updg:id="x2" StudentID="S4" LastName="Pecock" />  
           <Student updg:id="x3" StudentID="S5" LastName="Buchanan" />  
           <Course updg:id="y" CourseID="CS101"  
                               CourseName="C Programming"  
                               StudentIDList="S3 S4 S5" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
 <span data-ttu-id="ade8a-243">這是相等的 XDR 結構描述：</span><span class="sxs-lookup"><span data-stu-id="ade8a-243">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <ElementType name="Enrollment" sql:relation="Enrollment" sql:key-fields="StudentID CourseID">  
    <AttributeType name="StudentID" dt:type="id" />  
    <AttributeType name="CourseID" dt:type="id" />  
  
    <attribute type="StudentID" />  
    <attribute type="CourseID" />  
  </ElementType>  
  <ElementType name="Course" sql:relation="Course" sql:key-fields="CourseID">  
    <AttributeType name="CourseID" dt:type="id" />  
    <AttributeType name="CourseName" />  
  
    <attribute type="CourseID" />  
    <attribute type="CourseName" />  
  
    <AttributeType name="StudentIDList" dt:type="idrefs" />  
    <attribute type="StudentIDList" sql:relation="Enrollment" sql:field="StudentID" >  
        <sql:relationship  
                key-relation="Course"  
                key="CourseID"  
                foreign-relation="Enrollment"  
                foreign-key="CourseID" />  
    </attribute>  
  
  </ElementType>  
  <ElementType name="Student" sql:relation="Student">  
    <AttributeType name="StudentID" dt:type="id" />  
     <AttributeType name="LastName" />  
  
    <attribute type="StudentID" />  
    <attribute type="LastName" />  
  
    <AttributeType name="EnrolledIn" dt:type="idrefs" />  
    <attribute type="EnrolledIn" sql:relation="Enrollment" sql:field="CourseID" >  
        <sql:relationship  
                key-relation="Student"  
                key="StudentID"  
                foreign-relation="Enrollment"  
                foreign-key="StudentID" />  
    </attribute>  
  
    <element type="Enrollment" sql:relation="Enrollment" >  
        <sql:relationship key-relation="Student"  
                          key="StudentID"  
                          foreign-relation="Enrollment"  
                          foreign-key="StudentID" />  
    </element>  
  </ElementType>  
  
</Schema>  
```  
  
 <span data-ttu-id="ade8a-244">如需使用對應架構之 updategram 的更多範例，請參閱[在 Updategram 中指定批註式對應架構 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="ade8a-244">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade8a-245">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ade8a-245">See Also</span></span>  
 [<span data-ttu-id="ade8a-246">&#40;SQLXML 4.0&#41;的 Updategram 安全性考慮</span><span class="sxs-lookup"><span data-stu-id="ade8a-246">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
