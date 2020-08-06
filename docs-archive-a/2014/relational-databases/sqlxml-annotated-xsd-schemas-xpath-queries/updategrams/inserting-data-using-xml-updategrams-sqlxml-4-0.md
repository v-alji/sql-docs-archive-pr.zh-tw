---
title: 使用 XML Updategram 插入資料 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- xsi:nil attribute
- unique values
- <after> block
- id attribute
- data insertions [SQLXML]
- nil attribute
- <before> block
- updg:guid attribute
- multiple record insertions
- returnid attribute
- updategrams [SQLXML], inserting data
- updg:at-identity attribute
- invalid characters [SQLXML]
- updg:returnid attribute
- updg:id attribute
- namespaces [SQLXML], updategrams
- IDENTITY-type column
- guid attribute
- record insertion [SQLXML]
- null values [SQLXML]
- at-identity attribute
- xml data type [SQL Server], SQLXML
ms.assetid: 4dc48762-bc12-43fb-b356-ea1b9c1e287e
author: rothja
ms.author: jroth
ms.openlocfilehash: a80f2cb157e59f30ebcbff5c14abba1003de9e40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700861"
---
# <a name="inserting-data-using-xml-updategrams-sqlxml-40"></a><span data-ttu-id="7be02-102">使用 XML Updategram 插入資料 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="7be02-102">Inserting Data Using XML Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="7be02-103">當記錄實例出現在區塊中， **\<after>** 但不在對應的區塊中時，updategram 表示插入作業 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="7be02-103">An updategram indicates an insert operation when a record instance appears in the **\<after>** block but not in the corresponding **\<before>** block.</span></span> <span data-ttu-id="7be02-104">在此情況下，updategram 會將區塊中的記錄插入 **\<after>** 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="7be02-104">In this case, the updategram inserts the record in the **\<after>** block into the database.</span></span>  
  
 <span data-ttu-id="7be02-105">下列是插入作業的 Updategram 格式：</span><span class="sxs-lookup"><span data-stu-id="7be02-105">This is the updategram format for an insert operation:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   [<updg:before>  
   </updg:before>]  
    <updg:after [updg:returnid="x y ...] >  
       <ElementName [updg:id="value"]   
                   [updg:at-identity="x"]   
                   [updg:guid="y"]  
                   attribute="value"   
                   attribute="value"  
                   ...  
       />  
      [<ElementName .../>... ]  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
## <a name="before-block"></a><span data-ttu-id="7be02-106">\<before>總匯</span><span class="sxs-lookup"><span data-stu-id="7be02-106">\<before> Block</span></span>  
 <span data-ttu-id="7be02-107">**\<before>** 插入作業可以省略區塊。</span><span class="sxs-lookup"><span data-stu-id="7be02-107">The **\<before>** block can be omitted for an insert operation.</span></span> <span data-ttu-id="7be02-108">如果 `mapping-schema` 未指定選擇性屬性，在 **\<ElementName>** updategram 中指定的會對應至資料庫資料表，而子項目或屬性則會對應到資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="7be02-108">If the optional `mapping-schema` attribute is not specified, the **\<ElementName>** that is specified in the updategram maps to a database table and the child elements or attributes map to columns in the table.</span></span>  
  
## <a name="after-block"></a><span data-ttu-id="7be02-109">\<after>總匯</span><span class="sxs-lookup"><span data-stu-id="7be02-109">\<after> Block</span></span>  
 <span data-ttu-id="7be02-110">您可以在區塊中指定一或多個記錄 **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="7be02-110">You can specify one or more records in the **\<after>** block.</span></span>  
  
 <span data-ttu-id="7be02-111">如果 **\<after>** 區塊未提供特定資料行的值，則 updategram 會使用批註式架構中指定的預設值 (如果已) 指定架構。</span><span class="sxs-lookup"><span data-stu-id="7be02-111">If the **\<after>** block does not supply a value for a particular column, the updategram uses the default value that is specified in the annotated schema (if a schema has been specified).</span></span> <span data-ttu-id="7be02-112">如果架構未指定資料行的預設值，則 updategram 不會為此資料行指定任何明確的值，而是會將 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設值指派給這個資料行) 指定 (。</span><span class="sxs-lookup"><span data-stu-id="7be02-112">If the schema does not specify a default value for the column, the updategram does not specify any explicit value to this column and, instead, assigns the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] default value (if specified) to this column.</span></span> <span data-ttu-id="7be02-113">如果沒有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設值，而資料行接受 NULL 值，則 Updategram 會將資料行值設定為 NULL。</span><span class="sxs-lookup"><span data-stu-id="7be02-113">If there is no [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] default value and the column accepts a NULL value, the updategram sets the column value to NULL.</span></span> <span data-ttu-id="7be02-114">如果資料行沒有預設值，也不接受 NULL 值，則命令會失敗，而 Updategram 傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="7be02-114">If the column neither has a default value nor accepts a NULL value, the command fails and the updategram returns an error.</span></span> <span data-ttu-id="7be02-115">選擇性的 `updg:returnid` 屬性會用來傳回識別值，此值會在以 IDENTITY 類型的資料行將記錄加入至資料表時產生。</span><span class="sxs-lookup"><span data-stu-id="7be02-115">The optional `updg:returnid` attribute is used to return the identity value that is generated by the system when a record is added in a table with an IDENTITY-type column.</span></span>  
  
## <a name="updgid-attribute"></a><span data-ttu-id="7be02-116">updg:id 屬性</span><span class="sxs-lookup"><span data-stu-id="7be02-116">updg:id Attribute</span></span>  
 <span data-ttu-id="7be02-117">如果 Updategram 只插入記錄，就不需要 `updg:id` 屬性。</span><span class="sxs-lookup"><span data-stu-id="7be02-117">If the updategram is inserting only records, the updategram does not require the `updg:id` attribute.</span></span> <span data-ttu-id="7be02-118">如需的詳細資訊 `updg:id` ，請參閱[使用 XML Updategram 更新資料 &#40;SQLXML 4.0&#41;](updating-data-using-xml-updategrams-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="7be02-118">For more information about `updg:id`, see [Updating Data Using XML Updategrams &#40;SQLXML 4.0&#41;](updating-data-using-xml-updategrams-sqlxml-4-0.md).</span></span>  
  
## <a name="updgat-identity-attribute"></a><span data-ttu-id="7be02-119">updg:at-identity 屬性</span><span class="sxs-lookup"><span data-stu-id="7be02-119">updg:at-identity Attribute</span></span>  
 <span data-ttu-id="7be02-120">當 Updategram 在具有 IDENTITY 類型之資料行的資料表中插入記錄時，就可以使用選擇性的 `updg:at-identity` 屬性來擷取系統指派值。</span><span class="sxs-lookup"><span data-stu-id="7be02-120">When an updategram inserts a record in a table that has an IDENTITY-type column, the updategram can capture the system assigned value by using the optional `updg:at-identity` attribute.</span></span> <span data-ttu-id="7be02-121">Updategram 接著可以在後續作業中使用此值。</span><span class="sxs-lookup"><span data-stu-id="7be02-121">The updategram can then use this value in subsequent operations.</span></span> <span data-ttu-id="7be02-122">在執行 Updategram 時，您可以指定 `updg:returnid` 屬性以傳回產生的識別值。</span><span class="sxs-lookup"><span data-stu-id="7be02-122">Upon execution of the updategram, you can return the identity value that is generated by specifying the `updg:returnid` attribute.</span></span>  
  
## <a name="updgguid-attribute"></a><span data-ttu-id="7be02-123">updg:guid 屬性</span><span class="sxs-lookup"><span data-stu-id="7be02-123">updg:guid Attribute</span></span>  
 <span data-ttu-id="7be02-124">`updg:guid` 屬性是選擇性的屬性，會產生全域唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="7be02-124">The `updg:guid` attribute is an optional attribute that generates a globally unique identifier.</span></span> <span data-ttu-id="7be02-125">這個值會保留在所指定之整個區塊的範圍中 **\<sync>** 。</span><span class="sxs-lookup"><span data-stu-id="7be02-125">This value remains in scope for the entire **\<sync>** block in which it is specified.</span></span> <span data-ttu-id="7be02-126">您可以在區塊中的任何位置使用此值 **\<sync>** 。</span><span class="sxs-lookup"><span data-stu-id="7be02-126">You can use this value anywhere in the **\<sync>** block.</span></span> <span data-ttu-id="7be02-127">屬性會呼叫 `NEWGUID()` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 函數來產生唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="7be02-127">The attribute calls the `NEWGUID()`[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] function to generate the unique identifier.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7be02-128">範例</span><span class="sxs-lookup"><span data-stu-id="7be02-128">Examples</span></span>  
 <span data-ttu-id="7be02-129">若要使用下列範例建立工作範例，您必須符合[執行 SQLXML 範例的需求](../../sqlxml/requirements-for-running-sqlxml-examples.md)中所指定的需求。</span><span class="sxs-lookup"><span data-stu-id="7be02-129">To create working samples using the following examples, you must meet the requirements specified in [Requirements for Running SQLXML Examples](../../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
 <span data-ttu-id="7be02-130">使用 Updategram 範例之前，請注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="7be02-130">Before using the updategram examples, note the following:</span></span>  
  
-   <span data-ttu-id="7be02-131">大部分的範例都會使用預設對應 (也就是說，Updategram 中不會指定任何對應結構描述)。</span><span class="sxs-lookup"><span data-stu-id="7be02-131">Most of the examples use default mapping (that is, no mapping schema is specified in the updategram).</span></span> <span data-ttu-id="7be02-132">如需使用對應架構之 updategram 的更多範例，請參閱[在 Updategram 中指定批註式對應架構 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="7be02-132">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="7be02-133">大部分的範例都會使用 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="7be02-133">Most of the examples use the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="7be02-134">所有的更新都會套用到此資料庫內的資料表。</span><span class="sxs-lookup"><span data-stu-id="7be02-134">All the updates are applied to the tables in this database.</span></span>  
  
### <a name="a-inserting-a-record-by-using-an-updategram"></a><span data-ttu-id="7be02-135">A.</span><span class="sxs-lookup"><span data-stu-id="7be02-135">A.</span></span> <span data-ttu-id="7be02-136">使用 Updategram 插入記錄</span><span class="sxs-lookup"><span data-stu-id="7be02-136">Inserting a record by using an updategram</span></span>  
 <span data-ttu-id="7be02-137">這個屬性中心的 Updategram 會在 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 資料庫中的 HumanResources.Employee 資料表內插入記錄。</span><span class="sxs-lookup"><span data-stu-id="7be02-137">This attribute-centric updategram inserts a record in the HumanResources.Employee table in the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database.</span></span>  
  
 <span data-ttu-id="7be02-138">在此範例中，Updategram 不會指定對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="7be02-138">In this example, the updategram does not specify a mapping schema.</span></span> <span data-ttu-id="7be02-139">因此 Updategram 會使用預設對應，其中元素的名稱會對應到資料表名稱，而屬性或子元素則會對應到該資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="7be02-139">Therefore, the updategram uses default mapping, in which the element name maps to a table name and the attributes or child elements map to columns in that table.</span></span>  
  
 <span data-ttu-id="7be02-140">HumanResources.Department 資料表的 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 結構描述會對所有資料行賦予 'not null' 限制。</span><span class="sxs-lookup"><span data-stu-id="7be02-140">The [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] schema for the HumanResources.Department table imposes a 'not null' restriction on all columns.</span></span> <span data-ttu-id="7be02-141">因此 Updategram 必須包含針對所有資料行所指定的值。</span><span class="sxs-lookup"><span data-stu-id="7be02-141">Therefore, the updategram must include values specified for all columns.</span></span> <span data-ttu-id="7be02-142">DepartmentID 是 IDENTITY 類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="7be02-142">The DepartmentID is an IDENTITY-type column.</span></span> <span data-ttu-id="7be02-143">因此不會為它指定任何值。</span><span class="sxs-lookup"><span data-stu-id="7be02-143">Therefore, no values are specified for it.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department   
            Name="New Product Research"   
            GroupName="Research and Development"   
            ModifiedDate="2010-08-31"/>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="7be02-144">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="7be02-144">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="7be02-145">複製上述的 Updategram，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7be02-145">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="7be02-146">將檔案儲存為 MyUpdategram.xml。</span><span class="sxs-lookup"><span data-stu-id="7be02-146">Save the file as MyUpdategram.xml.</span></span>  
  
2.  <span data-ttu-id="7be02-147">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="7be02-147">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="7be02-148">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="7be02-148">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="7be02-149">在元素中心的對應中，Updategram 與下列類似：</span><span class="sxs-lookup"><span data-stu-id="7be02-149">In an element-centric mapping, the updategram looks like this:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department>  
            <Name> New Product Research </Name>  
            <GroupName> Research and Development </GroupName>  
            <ModifiedDate>2010-08-31</ModifiedDate>  
       </HumanResources.Department>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="7be02-150">在混合模式 (元素中心和屬性中心) 的 Updategram 中，元素可以同時具有屬性和子元素，如以下 Updategram 所示：</span><span class="sxs-lookup"><span data-stu-id="7be02-150">In a mixed-mode (element-centric and attribute-centric) updategram, an element can have both attributes and subelements, as shown in this updategram:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department   
            Name=" New Product Research "   
            <GroupName>Research and Development</GroupName>  
            <ModifiedDate>2010-08-31</ModifiedDate>  
       </HumanResources.Department>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
### <a name="b-inserting-multiple-records-by-using-an-updategram"></a><span data-ttu-id="7be02-151">B.</span><span class="sxs-lookup"><span data-stu-id="7be02-151">B.</span></span> <span data-ttu-id="7be02-152">使用 Updategram 插入多筆記錄</span><span class="sxs-lookup"><span data-stu-id="7be02-152">Inserting multiple records by using an updategram</span></span>  
 <span data-ttu-id="7be02-153">這個 Updategram 會將兩筆新的值班記錄加入至 HumanResources.Shift 資料表。</span><span class="sxs-lookup"><span data-stu-id="7be02-153">This updategram adds two new shift records to the HumanResources.Shift table.</span></span> <span data-ttu-id="7be02-154">Updategram 不會指定選擇性的 **\<before>** 區塊。</span><span class="sxs-lookup"><span data-stu-id="7be02-154">The updategram does not specify the optional **\<before>** block.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync>  
    <updg:after >  
       <HumanResources.Shift Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="7be02-155">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="7be02-155">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="7be02-156">複製上述的 Updategram，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7be02-156">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="7be02-157">將檔案儲存為 Updategram-AddShifts.xml。</span><span class="sxs-lookup"><span data-stu-id="7be02-157">Save the file as Updategram-AddShifts.xml.</span></span>  
  
2.  <span data-ttu-id="7be02-158">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="7be02-158">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="7be02-159">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="7be02-159">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="7be02-160">這個範例的另一個版本是使用兩個不同 **\<after>** 區塊（而不是一個區塊）來插入兩個員工的 updategram。</span><span class="sxs-lookup"><span data-stu-id="7be02-160">Another version of this example is an updategram that uses two separate **\<after>** blocks instead of one block to insert the two employees.</span></span> <span data-ttu-id="7be02-161">這是有效的方法，編碼方式如下：</span><span class="sxs-lookup"><span data-stu-id="7be02-161">This is valid and can be encoded as follows:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync>  
    <updg:after >  
       <HumanResources.Shift Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
    <updg:before>  
    </updg:before>  
    <updg:after >  
       <HumanResources.Shift Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
### <a name="c-working-with-valid-sql-server-characters-that-are-not-valid-in-xml"></a><span data-ttu-id="7be02-162">C.</span><span class="sxs-lookup"><span data-stu-id="7be02-162">C.</span></span> <span data-ttu-id="7be02-163">使用在 XML 中無效的有效 SQL Server 字元</span><span class="sxs-lookup"><span data-stu-id="7be02-163">Working with valid SQL Server characters that are not valid in XML</span></span>  
 <span data-ttu-id="7be02-164">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，資料表名稱可以包含空格，例如 Northwind 資料庫中的 Order Details 資料表。</span><span class="sxs-lookup"><span data-stu-id="7be02-164">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], table names can include a space, such as the Order Details table in the Northwind database.</span></span> <span data-ttu-id="7be02-165">不過，這在 XML 字元中無效，但不是有效的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 識別碼，但不能使用 ' __xHHHH \_ \_ ' 作為編碼值來編碼，其中 hhhh hhhh 會以最高有效位優先的順序，代表該字元的四位數十六進位 UCS-2 代碼。</span><span class="sxs-lookup"><span data-stu-id="7be02-165">However, this is not valid in XML characters that are valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identifiers but not valid XML identifiers can be encoded using '__xHHHH\_\_' as the encoding value, where HHHH stands for the four-digit hexadecimal UCS-2 code for the character in the most significant bit-first order.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7be02-166">此範例會使用 Northwind 資料庫。</span><span class="sxs-lookup"><span data-stu-id="7be02-166">This example uses the Northwind database.</span></span> <span data-ttu-id="7be02-167">您可以使用可從這個[Microsoft 網站](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)下載的 SQL 腳本來安裝 Northwind 資料庫。</span><span class="sxs-lookup"><span data-stu-id="7be02-167">You can install the Northwind database by using an SQL script available for download from this [Microsoft Web site](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>  
  
 <span data-ttu-id="7be02-168">此外，元素名稱也必須加上方括號 ([ ])。</span><span class="sxs-lookup"><span data-stu-id="7be02-168">Also, the element name must be enclosed within brackets ([ ]).</span></span> <span data-ttu-id="7be02-169">因為字元 [和] 在 XML 中無效，所以您必須分別將它們編碼為 _x005B \_ 和 _x005D \_ 。</span><span class="sxs-lookup"><span data-stu-id="7be02-169">Because the characters [and] are not valid in XML, you must encode them as _x005B\_ and _x005D\_, respectively.</span></span> <span data-ttu-id="7be02-170">(如果您使用對應結構描述，則可以提供不包含空格之類無效字元的元素。</span><span class="sxs-lookup"><span data-stu-id="7be02-170">(If you use a mapping schema, you can provide element names that do not contain characters that are not valid, such as white spaces.</span></span> <span data-ttu-id="7be02-171">對應結構描述會進行必要的對應，因此您就不必進行這些字元的編碼)。</span><span class="sxs-lookup"><span data-stu-id="7be02-171">The mapping schema does the necessary mapping; therefore, you do not need to encode for these characters).</span></span>  
  
 <span data-ttu-id="7be02-172">下列 Updategram 會在 Northwind 資料庫的 Order Details 資料表中加入記錄：</span><span class="sxs-lookup"><span data-stu-id="7be02-172">This updategram adds a record to the Order Details table in the Northwind database:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
      <_x005B_Order_x0020_Details_x005D_ OrderID="1"  
            ProductID="11"  
            UnitPrice="$1.0"  
            Quantity="1"  
            Discount="0.0" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="7be02-173">Order Details 資料表中的 UnitPrice 資料行是 `money` 類型。</span><span class="sxs-lookup"><span data-stu-id="7be02-173">The UnitPrice column in the Order Details table is of the `money` type.</span></span> <span data-ttu-id="7be02-174">若要套用適當的類型轉換 (從 `string` 類型轉換成 `money` 類型)，必須將錢幣符號字元 ($) 加入為值的一部分。</span><span class="sxs-lookup"><span data-stu-id="7be02-174">To apply the appropriate type conversion (from a `string` type to a `money` type), the dollar sign character ($) must be added as part of the value.</span></span> <span data-ttu-id="7be02-175">如果 Updategram 未指定對應結構描述，則會評估 `string` 值的第一個字元。</span><span class="sxs-lookup"><span data-stu-id="7be02-175">If the updategram does not specify a mapping schema, the first character of the `string` value is evaluated.</span></span> <span data-ttu-id="7be02-176">如果第一個字元為錢幣符號 ($)，則會套用適當的轉換。</span><span class="sxs-lookup"><span data-stu-id="7be02-176">If the first character is a dollar sign ($), the appropriate conversion is applied.</span></span>  
  
 <span data-ttu-id="7be02-177">如果 Updategram 是針對對應結構描述而指定，且其中的資料行適當地標示為 `dt:type="fixed.14.4"` 或 `sql:datatype="money"`，則不需要錢幣符號 ($)，轉換作業會由對應來處理。</span><span class="sxs-lookup"><span data-stu-id="7be02-177">If the updategram is specified against a mapping schema where the column is appropriately marked as either `dt:type="fixed.14.4"` or `sql:datatype="money"`, the dollar sign ($) is not required and the conversion is handled by the mapping.</span></span> <span data-ttu-id="7be02-178">這是建議的方式，可確保進行的是適當的類型轉換。</span><span class="sxs-lookup"><span data-stu-id="7be02-178">This is the recommended way to ensure that the appropriate type conversion occurs.</span></span>  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="7be02-179">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="7be02-179">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="7be02-180">複製上述的 Updategram，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7be02-180">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="7be02-181">將檔案儲存為 UpdategramSpacesInTableName.xml。</span><span class="sxs-lookup"><span data-stu-id="7be02-181">Save the file as UpdategramSpacesInTableName.xml.</span></span>  
  
2.  <span data-ttu-id="7be02-182">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="7be02-182">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="7be02-183">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="7be02-183">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="d-using-the-at-identity-attribute-to-retrieve-the-value-that-has-been-inserted-in-the-identity-type-column"></a><span data-ttu-id="7be02-184">D.</span><span class="sxs-lookup"><span data-stu-id="7be02-184">D.</span></span> <span data-ttu-id="7be02-185">使用 at-identity 屬性來擷取插入至 IDENTITY 類型之資料行的值</span><span class="sxs-lookup"><span data-stu-id="7be02-185">Using the at-identity attribute to retrieve the value that has been inserted in the IDENTITY-type column</span></span>  
 <span data-ttu-id="7be02-186">下列 Updategram 會插入兩筆記錄：在 Sales.SalesOrderHeader 資料表中插入一筆，而在 Sales.SalesOrderDetail 資料表中插入另一筆。</span><span class="sxs-lookup"><span data-stu-id="7be02-186">The following updategram inserts two records: one in the Sales.SalesOrderHeader table and another in the Sales.SalesOrderDetail table.</span></span>  
  
 <span data-ttu-id="7be02-187">首先，Updategram 會將記錄加入至 Sales.SalesOrderHeader 資料表。</span><span class="sxs-lookup"><span data-stu-id="7be02-187">First, the updategram adds a record to the Sales.SalesOrderHeader table.</span></span> <span data-ttu-id="7be02-188">在這個資料表中，SalesOrderID 資料行是 IDENTITY 類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="7be02-188">In this table, the SalesOrderID column is an IDENTITY-type column.</span></span> <span data-ttu-id="7be02-189">因此，當您將這筆記錄加入至該資料表時，Updategram 會使用 `at-identity` 屬性，將指派的 SalesOrderID 值擷取為 "x" (預留位置值)。</span><span class="sxs-lookup"><span data-stu-id="7be02-189">Therefore, when you add this record to the table, the updategram uses the `at-identity` attribute to capture the assigned SalesOrderID value as "x" (a placeholder value).</span></span> <span data-ttu-id="7be02-190">然後，updategram 會將此 `at-identity` 變數指定為元素中 SalesOrderID 屬性的值 \<Sales.SalesOrderDetail> 。</span><span class="sxs-lookup"><span data-stu-id="7be02-190">The updategam then specifies this `at-identity` variable as the value of SalesOrderID attribute in the \<Sales.SalesOrderDetail> element.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
 <updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
   <Sales.SalesOrderHeader updg:at-identity="x"   
             RevisionNumber="1"  
             OrderDate="2001-07-01 00:00:00.000"  
             DueDate="2001-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             CustomerID="676"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="00001111-2222-3333-4444-556677889900"  
             ModifiedDate="2001-07-08 00:00:00.000" />  
      <Sales.SalesOrderDetail SalesOrderID="x"  
                LineNumber="1"  
                OrderQty="1"  
                ProductID="776"  
                SpecialOfferID="1"  
                UnitPrice="2429.9928"  
                UnitPriceDiscount="0.00"  
                rowguid="aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee"  
                ModifiedDate="2001-07-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="7be02-191">如果想要傳回 `updg:at-identity` 屬性所產生的識別值，可以使用 `updg:returnid` 屬性。</span><span class="sxs-lookup"><span data-stu-id="7be02-191">If you want to return the identity value that is generated by the `updg:at-identity` attribute, you can use the `updg:returnid` attribute.</span></span> <span data-ttu-id="7be02-192">下列是經過修改的 Updategram，會傳回這個識別值 </span><span class="sxs-lookup"><span data-stu-id="7be02-192">The following is a revised updategram that returns this identity value.</span></span> <span data-ttu-id="7be02-193">(此 Updategram 會加入兩筆訂單記錄和兩筆訂單詳細資料的記錄，以稍微增加範例的複雜度)。</span><span class="sxs-lookup"><span data-stu-id="7be02-193">(This updategram adds two order records and two order detail records, just to make the example a little more complex.)</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
 <updg:sync>  
  <updg:before>  
  </updg:before>  
  <updg:after updg:returnid="x y" >  
       <HumanResources.Shift updg:at-identity="x" Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift updg:at-identity="y" Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:after>  
 </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="7be02-194">Updategram 在執行時會傳回類似下列的結果，其中包含所產生的識別值 (可用於資料表識別的 ShiftID 資料行產生值)：</span><span class="sxs-lookup"><span data-stu-id="7be02-194">When the updategram is executed, it returns results similar to the following, which includes the identity value (the generated value of the ShiftID column used for table identity) that was generated:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">   
  <returnid>   
    <x>4</x>   
    <y>5</y>   
  </returnid>   
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="7be02-195">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="7be02-195">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="7be02-196">複製上述的 Updategram，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7be02-196">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="7be02-197">將檔案儲存為 Updategram-returnId.xml。</span><span class="sxs-lookup"><span data-stu-id="7be02-197">Save the file as Updategram-returnId.xml.</span></span>  
  
2.  <span data-ttu-id="7be02-198">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="7be02-198">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="7be02-199">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="7be02-199">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="e-using-the-updgguid-attribute-to-generate-a-unique-value"></a><span data-ttu-id="7be02-200">E.</span><span class="sxs-lookup"><span data-stu-id="7be02-200">E.</span></span> <span data-ttu-id="7be02-201">使用 updg:guid 屬性來產生唯一值</span><span class="sxs-lookup"><span data-stu-id="7be02-201">Using the updg:guid attribute to generate a unique value</span></span>  
 <span data-ttu-id="7be02-202">在這個範例中，Updategram 會在 Cust 和 CustOrder 資料表中插入記錄，</span><span class="sxs-lookup"><span data-stu-id="7be02-202">In this example, the updategram inserts a record in the Cust and CustOrder tables.</span></span> <span data-ttu-id="7be02-203">此外，該 Updategram 也會使用 `updg:guid` 屬性來為 CustomerID 屬性產生唯一值。</span><span class="sxs-lookup"><span data-stu-id="7be02-203">Also, the updategram generates a unique value for the CustomerID attribute by using the `updg:guid` attribute.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after updg:returnid="x" >  
      <Cust updg:guid="x" >  
         <CustID>x</CustID>  
         <LastName>Fuller</LastName>  
      </Cust>  
      <CustOrder>  
         <CustID>x</CustID>  
         <OrderID>1</OrderID>  
      </CustOrder>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="7be02-204">Updategram 會指定 `returnid` 屬性。</span><span class="sxs-lookup"><span data-stu-id="7be02-204">The updategram specifies the `returnid` attribute.</span></span> <span data-ttu-id="7be02-205">因此會傳回所產生的 GUID：</span><span class="sxs-lookup"><span data-stu-id="7be02-205">As a result, the GUID that is generated is returned:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <returnid>  
    <x>7111BD1A-7F0B-4CEE-B411-260DADFEFA2A</x>   
  </returnid>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="7be02-206">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="7be02-206">To test the updategram</span></span>  
  
1.  <span data-ttu-id="7be02-207">複製上述的 Updategram，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7be02-207">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="7be02-208">將檔案儲存為 Updategram-GenerateGuid.xml。</span><span class="sxs-lookup"><span data-stu-id="7be02-208">Save the file as Updategram-GenerateGuid.xml.</span></span>  
  
2.  <span data-ttu-id="7be02-209">建立這些資料表：</span><span class="sxs-lookup"><span data-stu-id="7be02-209">Create these tables:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust (CustID uniqueidentifier, LastName varchar(20))  
    CREATE TABLE CustOrder (CustID uniqueidentifier, OrderID int)  
    ```  
  
3.  <span data-ttu-id="7be02-210">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="7be02-210">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="7be02-211">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="7be02-211">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="f-specifying-a-schema-in-an-updategram"></a><span data-ttu-id="7be02-212">F.</span><span class="sxs-lookup"><span data-stu-id="7be02-212">F.</span></span> <span data-ttu-id="7be02-213">在 Updategram 中指定結構描述</span><span class="sxs-lookup"><span data-stu-id="7be02-213">Specifying a schema in an updategram</span></span>  
 <span data-ttu-id="7be02-214">這個範例中的 Updategram 會在下列資料表中插入記錄：</span><span class="sxs-lookup"><span data-stu-id="7be02-214">The updategram in this example inserts a record into the following table:</span></span>  
  
```  
CustOrder(OrderID, EmployeeID, OrderType)  
```  
  
 <span data-ttu-id="7be02-215">這個 Updategram 中指定了 XSD 結構描述 (也就是說，沒有 Updategram 元素和屬性的預設對應)。</span><span class="sxs-lookup"><span data-stu-id="7be02-215">An XSD schema is specified in this updategram (that is, there is no default mapping of updategram elements and attributes).</span></span> <span data-ttu-id="7be02-216">該結構描述提供元素和屬性對資料庫資料表和資料行的必要對應。</span><span class="sxs-lookup"><span data-stu-id="7be02-216">The schema provides the necessary mapping of the elements and attributes to the database tables and columns.</span></span>  
  
 <span data-ttu-id="7be02-217">下列架構 ( # A0) 描述由「 **\<CustOrder>** **訂單**」和「**員工 id** 」屬性組成的元素。</span><span class="sxs-lookup"><span data-stu-id="7be02-217">The following schema (CustOrderSchema.xml) describes a **\<CustOrder>** element that consists of the **OrderID** and **EmployeeID** attributes.</span></span> <span data-ttu-id="7be02-218">為了讓架構更有趣，會將預設值指派給 [**員工**] 屬性。</span><span class="sxs-lookup"><span data-stu-id="7be02-218">To make the schema more interesting, a default value is assigned to the **EmployeeID** attribute.</span></span> <span data-ttu-id="7be02-219">Updategram 只會將屬性的預設值用於插入作業，而且只有在 Updategram 未指定該屬性時才會這麼做。</span><span class="sxs-lookup"><span data-stu-id="7be02-219">An updategram uses an attribute's default value only for insert operations, and then only if the updategram does not specify that attribute.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="CustOrder" >  
   <xsd:complexType>  
        <xsd:attribute name="OrderID"     type="xsd:integer" />   
        <xsd:attribute name="EmployeeID"  type="xsd:integer" />  
        <xsd:attribute name="OrderType  " type="xsd:integer" default="1"/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="7be02-220">這個 Updategram 會將記錄插入至 CustOrder 資料表。</span><span class="sxs-lookup"><span data-stu-id="7be02-220">This updategram inserts a record into the CustOrder table.</span></span> <span data-ttu-id="7be02-221">Updategram 只會指定 OrderID 和 EmployeeID 屬性值，</span><span class="sxs-lookup"><span data-stu-id="7be02-221">The updategram specifies only the OrderID and EmployeeID attribute values.</span></span> <span data-ttu-id="7be02-222">而不會指定 OrderType 屬性值。</span><span class="sxs-lookup"><span data-stu-id="7be02-222">It does not specify the OrderType attribute value.</span></span> <span data-ttu-id="7be02-223">因此，Updategram 會使用在前述結構描述中所指定之 EmployeeID 屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="7be02-223">Therefore, the updategram uses the default value of the EmployeeID attribute that is specified in the preceding schema.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"  
             xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync mapping-schema='CustOrderSchema.xml'>  
<updg:after>  
       <CustOrder OrderID="98000" EmployeeID="1" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="7be02-224">如需指定對應架構之 updategram 的更多範例，請參閱[在 Updategram 中指定批註式對應架構 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="7be02-224">For more examples of updategrams that specify a mapping schema, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="7be02-225">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="7be02-225">To test the updategram</span></span>  
  
1.  <span data-ttu-id="7be02-226">在**tempdb**資料庫中建立此資料表：</span><span class="sxs-lookup"><span data-stu-id="7be02-226">Create this table in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE CustOrder(  
                     OrderID int,   
                     EmployeeID int,   
                     OrderType int)  
    ```  
  
2.  <span data-ttu-id="7be02-227">複製上述的結構描述，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7be02-227">Copy the schema above and paste it into a text file.</span></span> <span data-ttu-id="7be02-228">然後將檔案儲存為 CustOrderSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="7be02-228">Save the file as CustOrderSchema.xml.</span></span>  
  
3.  <span data-ttu-id="7be02-229">複製上述的 Updategram，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7be02-229">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="7be02-230">然後將檔案在前述步驟所使用的相同資料夾中，儲存為 CustOrderUpdategram.xml。</span><span class="sxs-lookup"><span data-stu-id="7be02-230">Save the file as CustOrderUpdategram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="7be02-231">建立及使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行 Updategram。</span><span class="sxs-lookup"><span data-stu-id="7be02-231">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="7be02-232">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="7be02-232">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="7be02-233">這是相等的 XDR 結構描述：</span><span class="sxs-lookup"><span data-stu-id="7be02-233">This is the equivalent XDR schema:</span></span>  
  
```  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
 <ElementType name="CustOrder" >  
    <AttributeType name="OrderID" />  
    <AttributeType name="EmployeeID" />  
    <AttributeType name="OrderType" default="1" />  
    <attribute type="OrderID"  />  
    <attribute type="EmployeeID" />  
    <attribute type="OrderType" />  
  </ElementType>  
</Schema>  
```  
  
### <a name="g-using-the-xsinil-attribute-to-insert-null-values-in-a-column"></a><span data-ttu-id="7be02-234">G.</span><span class="sxs-lookup"><span data-stu-id="7be02-234">G.</span></span> <span data-ttu-id="7be02-235">使用 xsi:nil 屬性在資料行中插入 Null 值</span><span class="sxs-lookup"><span data-stu-id="7be02-235">Using the xsi:nil attribute to insert null values in a column</span></span>  
 <span data-ttu-id="7be02-236">如果想要在資料表中相對應的資料行中插入 Null 值，可以在 Updategram 中的元素上指定 `xsi:nil` 屬性。</span><span class="sxs-lookup"><span data-stu-id="7be02-236">If you want to insert a null value in the corresponding column in the table, you can specify the `xsi:nil` attribute on an element in an updategram.</span></span> <span data-ttu-id="7be02-237">在相對應的 XSD 結構描述中，也必須指定 XSD `nillable` 屬性。</span><span class="sxs-lookup"><span data-stu-id="7be02-237">In the corresponding XSD schema, the XSD `nillable` attribute also must be specified.</span></span>  
  
 <span data-ttu-id="7be02-238">例如，請考慮下列 XSD 結構描述：</span><span class="sxs-lookup"><span data-stu-id="7be02-238">For example, consider this XSD schema:</span></span>  
  
```  
<?xml version="1.0"?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="Student" sql:relation="Students">  
  <xsd:complexType>  
    <xsd:all>  
      <xsd:element name="fname" sql:field="first_name"   
                                type="xsd:string"   
                                 nillable="true"/>  
    </xsd:all>  
    <xsd:attribute name="SID"   
                        sql:field="StudentID"  
                        type="xsd:ID"/>      
    <xsd:attribute name="lname"       
                        sql:field="last_name"  
                        type="xsd:string"/>  
    <xsd:attribute name="minitial"    
                        sql:field="middle_initial"   
                        type="xsd:string"/>  
    <xsd:attribute name="years"       
                         sql:field="no_of_years"  
                         type="xsd:integer"/>  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="7be02-239">XSD 架構會為元素指定**nillable = "true"** **\<fname>** 。</span><span class="sxs-lookup"><span data-stu-id="7be02-239">The XSD schema specifies **nillable="true"** for the **\<fname>** element.</span></span> <span data-ttu-id="7be02-240">下列 Updategram 會使用這個結構描述：</span><span class="sxs-lookup"><span data-stu-id="7be02-240">The following updategram uses this schema:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"  
      xmlns:updg="urn:schemas-microsoft-com:xml-updategram"  
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  
<updg:sync mapping-schema='StudentSchema.xml'>  
  <updg:before/>  
  <updg:after>  
    <Student SID="S00004" lname="Elmaci" minitial="" years="2">  
      <fname xsi:nil="true">  
    </fname>  
    </Student>  
  </updg:after>  
</updg:sync>  
  
</ROOT>  
```  
  
 <span data-ttu-id="7be02-241">Updategram 會 `xsi:nil` 為 **\<fname>** 區塊中的元素指定 **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="7be02-241">The updategram specifies `xsi:nil` for the **\<fname>** element in the **\<after>** block.</span></span> <span data-ttu-id="7be02-242">因此，這個 Updategram 在執行時，會為資料表中的 first_name 資料行插入 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="7be02-242">Therefore, when this updategram is executed, a value of NULL is inserted for the first_name column in the table.</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="7be02-243">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="7be02-243">To test the updategram</span></span>  
  
1.  <span data-ttu-id="7be02-244">在**tempdb**資料庫中建立下列資料表：</span><span class="sxs-lookup"><span data-stu-id="7be02-244">Create the following table in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Students (  
       StudentID char(6)NOT NULL ,  
       first_name varchar(50),  
       last_name varchar(50),  
       middle_initial char(1),  
       no_of_years int NULL)  
    GO  
    ```  
  
2.  <span data-ttu-id="7be02-245">複製上述的結構描述，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7be02-245">Copy the schema above and paste it into a text file.</span></span> <span data-ttu-id="7be02-246">然後將檔案儲存為 StudentSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="7be02-246">Save the file as StudentSchema.xml.</span></span>  
  
3.  <span data-ttu-id="7be02-247">複製上述的 Updategram，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7be02-247">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="7be02-248">然後將檔案在前述步驟所使用的相同資料夾中，儲存為 StudentUpdategram.xml 以儲存 StudentSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="7be02-248">Save the file as StudentUpdategram.xml in the same folder used in previous step to save StudentSchema.xml.</span></span>  
  
4.  <span data-ttu-id="7be02-249">建立及使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行 Updategram。</span><span class="sxs-lookup"><span data-stu-id="7be02-249">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="7be02-250">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="7be02-250">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="h-specifying-namespaces-in-an-updategram"></a><span data-ttu-id="7be02-251">H.</span><span class="sxs-lookup"><span data-stu-id="7be02-251">H.</span></span> <span data-ttu-id="7be02-252">在 Updategram 中指定命名空間</span><span class="sxs-lookup"><span data-stu-id="7be02-252">Specifying namespaces in an updategram</span></span>  
 <span data-ttu-id="7be02-253">您在 Updategram 中所擁有的元素，可能會屬於在 Updategram 的相同元素中宣告的命名空間。</span><span class="sxs-lookup"><span data-stu-id="7be02-253">In an updategram you can have elements that belong to a namespace declared in the same element in the updategram.</span></span> <span data-ttu-id="7be02-254">在這種情況下，相對應的結構描述必須也要宣告相同的命名空間，且元素必須屬於該目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="7be02-254">In this case, the corresponding schema must also declare the same namespace and the element must belong to that target namespace.</span></span>  
  
 <span data-ttu-id="7be02-255">例如，在下列 updategram 中 ( # A0) ， **\<Order>** 元素屬於元素中宣告的命名空間。</span><span class="sxs-lookup"><span data-stu-id="7be02-255">For example, in the following updategram (UpdateGram-ElementHavingNamespace.xml), the **\<Order>** element belongs to a namespace declared in the element.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema='XSD-ElementHavingNameSpace.xml'>  
    <updg:after>  
       <x:Order  xmlns:x="http://server/xyz/schemas/"  
             updg:at-identity="SalesOrderID"   
             RevisionNumber="1"  
             OrderDate="2001-07-01 00:00:00.000"  
             DueDate="2001-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             CustomerID="676"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="00009999-8888-7777-6666-554433221100"  
             ModifiedDate="2001-07-08 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="7be02-256">在這種情況下，結構描述必須也要宣告命名空間，如下列結構描述所示：</span><span class="sxs-lookup"><span data-stu-id="7be02-256">In this case, the schema must also declare the namespace as shown in this schema:</span></span>  
  
 <span data-ttu-id="7be02-257">下列結構描述 (XSD-ElementHavingNamespace.xml) 顯示相對應元素和屬性的宣告方式。</span><span class="sxs-lookup"><span data-stu-id="7be02-257">The following schema (XSD-ElementHavingNamespace.xml) shows how the corresponding element and attributes must be declared.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
     xmlns:dt="urn:schemas-microsoft-com:datatypes"   
     xmlns:sql="urn:schemas-microsoft-com:mapping-schema"    
     xmlns:x="http://server/xyz/schemas/"   
     targetNamespace="http://server/xyz/schemas/" >  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" type="x:Order_type"/>  
  <xsd:complexType name="Order_type">  
    <xsd:attribute name="SalesOrderID"  type="xsd:ID"/>  
    <xsd:attribute name="RevisionNumber" type="xsd:unsignedByte"/>  
    <xsd:attribute name="OrderDate" type="xsd:dateTime"/>  
    <xsd:attribute name="DueDate" type="xsd:dateTime"/>  
    <xsd:attribute name="ShipDate" type="xsd:dateTime"/>  
    <xsd:attribute name="Status" type="xsd:unsignedByte"/>  
    <xsd:attribute name="OnlineOrderFlag" type="xsd:boolean"/>  
    <xsd:attribute name="SalesOrderNumber" type="xsd:string"/>  
    <xsd:attribute name="PurchaseOrderNumber" type="xsd:string"/>  
    <xsd:attribute name="AccountNumber" type="xsd:string"/>  
    <xsd:attribute name="CustomerID" type="xsd:int"/>  
    <xsd:attribute name="ContactID" type="xsd:int"/>  
    <xsd:attribute name="SalesPersonID" type="xsd:int"/>  
    <xsd:attribute name="TerritoryID" type="xsd:int"/>  
    <xsd:attribute name="BillToAddressID" type="xsd:int"/>  
    <xsd:attribute name="ShipToAddressID" type="xsd:int"/>  
    <xsd:attribute name="ShipMethodID" type="xsd:int"/>  
    <xsd:attribute name="CreditCardID" type="xsd:int"/>  
    <xsd:attribute name="CreditCardApprovalCode" type="xsd:string"/>  
    <xsd:attribute name="CurrencyRateID" type="xsd:int"/>  
    <xsd:attribute name="SubTotal" type="xsd:decimal"/>  
    <xsd:attribute name="TaxAmt" type="xsd:decimal"/>  
    <xsd:attribute name="Freight" type="xsd:decimal"/>  
    <xsd:attribute name="TotalDue" type="xsd:decimal"/>  
    <xsd:attribute name="Comment" type="xsd:string"/>  
    <xsd:attribute name="rowguid" type="xsd:string"/>  
    <xsd:attribute name="ModifiedDate" type="xsd:dateTime"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="7be02-258">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="7be02-258">To test the updategram</span></span>  
  
1.  <span data-ttu-id="7be02-259">複製上述的結構描述，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7be02-259">Copy the schema above and paste it into a text file.</span></span> <span data-ttu-id="7be02-260">將檔案儲存為 XSD-ElementHavingNamespace.xml。</span><span class="sxs-lookup"><span data-stu-id="7be02-260">Save the file as XSD-ElementHavingNamespace.xml.</span></span>  
  
2.  <span data-ttu-id="7be02-261">複製上述的 Updategram，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7be02-261">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="7be02-262">在用來儲存 XSD-ElementHavingnamespace.xml 的相同資料夾中，將檔案儲存為 Updategram-ElementHavingNamespace.xml。</span><span class="sxs-lookup"><span data-stu-id="7be02-262">Save the file as Updategram-ElementHavingNamespace.xml in the same folder used to save XSD-ElementHavingnamespace.xml.</span></span>  
  
3.  <span data-ttu-id="7be02-263">建立及使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行 Updategram。</span><span class="sxs-lookup"><span data-stu-id="7be02-263">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="7be02-264">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="7be02-264">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="i-inserting-data-into-an-xml-data-type-column"></a><span data-ttu-id="7be02-265">I.</span><span class="sxs-lookup"><span data-stu-id="7be02-265">I.</span></span> <span data-ttu-id="7be02-266">將資料插入至 XML 資料類型資料行</span><span class="sxs-lookup"><span data-stu-id="7be02-266">Inserting data into an XML data type column</span></span>  
 <span data-ttu-id="7be02-267">`xml` 資料類型是在 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中導入。</span><span class="sxs-lookup"><span data-stu-id="7be02-267">The `xml` data type was introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="7be02-268">您可以在下列前提下，使用 Updategram 來插入及更新以 `xml` 資料類型資料行所儲存的資料：</span><span class="sxs-lookup"><span data-stu-id="7be02-268">You can use updategrams to insert and update data stored in `xml` data type columns with the following provisions:</span></span>  
  
-   <span data-ttu-id="7be02-269">`xml` 資料行不可以用來識別現有的資料列，</span><span class="sxs-lookup"><span data-stu-id="7be02-269">The `xml` column cannot be used for identifying an existing row.</span></span> <span data-ttu-id="7be02-270">因此不能包含在 Updategram 的 `updg:before` 區段中。</span><span class="sxs-lookup"><span data-stu-id="7be02-270">Therefore, it cannot be included in the `updg:before` section of an updategram.</span></span>  
  
-   <span data-ttu-id="7be02-271">位於插入至 `xml` 資料行的 XML 片段範圍內的命名空間會受到保存，而其命名空間宣告則會加入至所插入片段的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="7be02-271">Namespaces that are in scope of the XML fragment inserted into the `xml` column will be preserved and their namespace declarations are added to the top element of the inserted fragment.</span></span>  
  
 <span data-ttu-id="7be02-272">例如，在下列 updategram 中 ( # A0) ，專案會 **\<Desc>** 更新範例資料庫之生產>productModel 資料表中的 ProductDescription 資料行 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7be02-272">For example, in the following updategram (SampleUpdateGram.xml), the **\<Desc>** element updates the ProductDescription column in the Production>productModel table in the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="7be02-273">這個 updategram 的結果是，ProductDescription 資料行的 XML 內容是以元素的 XML 內容進行更新 **\<Desc>** 。</span><span class="sxs-lookup"><span data-stu-id="7be02-273">The result of this updategram is that the XML contents of the ProductDescription column are update with the XML contents of the **\<Desc>** element.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync mapping-schema="SampleSchema.xml" >  
       <updg:before>  
<ProductModel ProductModelID="19">  
   <Name>Mountain-100</Name>  
</ProductModel>  
    </updg:before>  
    <updg:after>  
 <ProductModel>  
    <Name>Mountain-100</Name>  
    <Desc><?xml-stylesheet href="ProductDescription.xsl" type="text/xsl"?>  
        <p1:ProductDescription xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
              xmlns:wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"   
              xmlns:wf="http://www.adventure-works.com/schemas/OtherFeatures"   
              xmlns:html="http://www.w3.org/1999/xhtml"   
              xmlns="">  
  <p1:Summary>  
     <html:p>Insert Example</html:p>  
  </p1:Summary>  
  <p1:Manufacturer>  
    <p1:Name>AdventureWorks</p1:Name>  
    <p1:Copyright>2002</p1:Copyright>  
    <p1:ProductURL>HTTP://www.Adventure-works.com</p1:ProductURL>  
  </p1:Manufacturer>  
  <p1:Features>These are the product highlights.   
    <wm:Warranty>  
       <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
       <wm:Description>parts and labor</wm:Description>  
    </wm:Warranty>  
    <wm:Maintenance>  
       <wm:NoOfYears>10 years</wm:NoOfYears>  
       <wm:Description>maintenance contract available through your dealer or any AdventureWorks retail store.</wm:Description>  
    </wm:Maintenance>  
    <wf:wheel>High performance wheels.</wf:wheel>  
    <wf:saddle>  
      <html:i>Anatomic design</html:i> and made from durable leather for a full-day of riding in comfort.</wf:saddle>  
    <wf:pedal>  
       <html:b>Top-of-the-line</html:b> clipless pedals with adjustable tension.</wf:pedal>  
    <wf:BikeFrame>Each frame is hand-crafted in our Bothell facility to the optimum diameter and wall-thickness required of a premium mountain frame. The heat-treated welded aluminum frame has a larger diameter tube that absorbs the bumps.</wf:BikeFrame>  
    <wf:crankset> Triple crankset; alumunim crank arm; flawless shifting. </wf:crankset>  
   </p1:Features>  
   <p1:Picture>  
      <p1:Angle>front</p1:Angle>  
      <p1:Size>small</p1:Size>  
      <p1:ProductPhotoID>118</p1:ProductPhotoID>  
   </p1:Picture>  
   <p1:Specifications> These are the product specifications.  
     <Material>Almuminum Alloy</Material>  
     <Color>Available in most colors</Color>  
     <ProductLine>Mountain bike</ProductLine>  
     <Style>Unisex</Style>  
     <RiderExperience>Advanced to Professional riders</RiderExperience>  
   </p1:Specifications>  
  </p1:ProductDescription>  
 </Desc>  
      </ProductModel>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="7be02-274">Updategram 會參考下列的註解 XSD 結構描述 (SampleSchema.xml)。</span><span class="sxs-lookup"><span data-stu-id="7be02-274">The updategram refers to the following annotated XSD schema (SampleSchema.xml).</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
           xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
           xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">   
  <xsd:element name="ProductModel"  sql:relation="Production.ProductModel" >  
     <xsd:complexType>  
       <xsd:sequence>  
          <xsd:element name="Name" type="xsd:string"></xsd:element>  
          <xsd:element name="Desc" sql:field="CatalogDescription" sql:datatype="xml">  
           <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="ProductDescription">  
                 <xsd:complexType>  
                   <xsd:sequence>  
                     <xsd:element name="Summary" type="xsd:anyType">  
                     </xsd:element>  
                   </xsd:sequence>  
                 </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>   
       </xsd:sequence>  
       <xsd:attribute name="ProductModelID" sql:field="ProductModelID"/>  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="7be02-275">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="7be02-275">To test the updategram</span></span>  
  
1.  <span data-ttu-id="7be02-276">複製上述的結構描述，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7be02-276">Copy the schema above and paste it into a text file.</span></span> <span data-ttu-id="7be02-277">然後將檔案儲存為 XSD-SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="7be02-277">Save the file as XSD-SampleSchema.xml.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7be02-278">因為 Updategram 支援預設對應，所以沒辦法識別 `xml` 資料類型的開始和結尾。</span><span class="sxs-lookup"><span data-stu-id="7be02-278">Because updategrams support default mapping, there is no way to identify the beginning and ending of the `xml` data type.</span></span> <span data-ttu-id="7be02-279">這表示在插入或更新具有 `xml` 資料類型資料行的資料表時，需要使用對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="7be02-279">This effectively means that a mapping schema is required when inserting or updating tables with `xml` data type columns.</span></span> <span data-ttu-id="7be02-280">如果沒有提供結構描述，則 SQLXML 會傳回錯誤，指出資料表中遺失其中一個資料行。</span><span class="sxs-lookup"><span data-stu-id="7be02-280">When a schema is not provided, SQLXML returns an error indicating that one of the columns is missing from the table.</span></span>  
  
2.  <span data-ttu-id="7be02-281">複製上述的 Updategram，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7be02-281">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="7be02-282">然後將檔案在用來儲存 SampleSchema.xml 的相同資料夾中，儲存為 SampleUpdategram.xml。</span><span class="sxs-lookup"><span data-stu-id="7be02-282">Save the file as SampleUpdategram.xml in the same folder used to save SampleSchema.xml.</span></span>  
  
3.  <span data-ttu-id="7be02-283">建立及使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行 Updategram。</span><span class="sxs-lookup"><span data-stu-id="7be02-283">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="7be02-284">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="7be02-284">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7be02-285">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7be02-285">See Also</span></span>  
 [<span data-ttu-id="7be02-286">&#40;SQLXML 4.0&#41;的 Updategram 安全性考慮</span><span class="sxs-lookup"><span data-stu-id="7be02-286">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
