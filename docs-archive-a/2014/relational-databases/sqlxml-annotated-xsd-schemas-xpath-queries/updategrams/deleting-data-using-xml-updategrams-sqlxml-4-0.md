---
title: 使用 XML Updategram 刪除資料 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- <after> block
- updategrams [SQLXML], deleting data
- <before> block
- mapping-schema attribute
- record deletions [SQLXML]
ms.assetid: 4fb116d7-7652-474a-a567-cb475a20765c
author: rothja
ms.author: jroth
ms.openlocfilehash: d941005c71dc33dd8c4f5c5cc15f645cd0e68177
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598772"
---
# <a name="deleting-data-using-xml-updategrams-sqlxml-40"></a><span data-ttu-id="e5cec-102">使用 XML Updategram 刪除資料 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="e5cec-102">Deleting Data Using XML Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="e5cec-103">當記錄實例出現在區塊中 **\<before>** ，但在區塊中沒有對應的記錄時，updategram 表示刪除作業 **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="e5cec-103">An updategram indicates a delete operation when a record instance appears in the **\<before>** block with no corresponding records in the **\<after>** block.</span></span> <span data-ttu-id="e5cec-104">在此情況下，updategram 會從資料庫中刪除區塊中的記錄 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="e5cec-104">In this case, the updategram deletes the record in the **\<before>** block from the database.</span></span>  
  
 <span data-ttu-id="e5cec-105">下列是刪除作業的 Updategram 格式：</span><span class="sxs-lookup"><span data-stu-id="e5cec-105">This is the updategram format for a delete operation:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   <updg:before>  
       <ElementName />  
      [<ElementName .../>... ]  
   </updg:before>  
    [<updg:after>  
    </updg:after>]  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="e5cec-106">**\<after>** 如果 updategram 只執行刪除作業，您可以省略標記。</span><span class="sxs-lookup"><span data-stu-id="e5cec-106">You can omit the **\<after>** tag if the updategram is performing only a delete operation.</span></span> <span data-ttu-id="e5cec-107">如果您沒有指定選擇性的 `mapping-schema` 屬性， **\<ElementName>** updategram 中指定的會對應至資料庫資料表，而子項目或屬性則會對應到資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="e5cec-107">If you do not specify the optional `mapping-schema` attribute, the **\<ElementName>** specified in the updategram maps to a database table and the child elements or attributes map to columns in the table.</span></span>  
  
 <span data-ttu-id="e5cec-108">如果在 updategram 中指定的元素符合資料表中的多個資料列，或不符合任何資料列，則 updategram 會傳回錯誤並取消整個 **\<sync>** 區塊。</span><span class="sxs-lookup"><span data-stu-id="e5cec-108">If an element specified in the updategram either matches more than one row in the table or does not match any row, the updategram returns an error and cancels the entire **\<sync>** block.</span></span> <span data-ttu-id="e5cec-109">Updategram 中的元素一次只能刪除一個記錄。</span><span class="sxs-lookup"><span data-stu-id="e5cec-109">Only one record at a time can be deleted by an element in the updategram.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e5cec-110">範例</span><span class="sxs-lookup"><span data-stu-id="e5cec-110">Examples</span></span>  
 <span data-ttu-id="e5cec-111">本章節中的範例會使用預設對應 (也就是說，Updategram 中不會指定任何對應結構描述)。</span><span class="sxs-lookup"><span data-stu-id="e5cec-111">Examples in this section use default mapping (that is, no mapping schema is specified in the updategram).</span></span> <span data-ttu-id="e5cec-112">如需使用對應架構之 updategram 的更多範例，請參閱[在 Updategram 中指定批註式對應架構 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="e5cec-112">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="e5cec-113">若要使用下列範例建立工作範例，您必須符合[執行 SQLXML 範例的需求](../../sqlxml/requirements-for-running-sqlxml-examples.md)中所指定的需求。</span><span class="sxs-lookup"><span data-stu-id="e5cec-113">To create working samples using the following examples, you must meet the requirements specified in [Requirements for Running SQLXML Examples](../../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-deleting-a-record-by-using-an-updategram"></a><span data-ttu-id="e5cec-114">A.</span><span class="sxs-lookup"><span data-stu-id="e5cec-114">A.</span></span> <span data-ttu-id="e5cec-115">使用 Updategram 刪除記錄</span><span class="sxs-lookup"><span data-stu-id="e5cec-115">Deleting a record by using an updategram</span></span>  
 <span data-ttu-id="e5cec-116">下列 Updategram 會從 HumanResources.Shift 資料表刪除兩筆記錄。</span><span class="sxs-lookup"><span data-stu-id="e5cec-116">The following updategrams deletes two records from the HumanResources.Shift table.</span></span>  
  
 <span data-ttu-id="e5cec-117">在這些範例中，Updategram 不會指定對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="e5cec-117">In these examples, the updategram does not specify a mapping schema.</span></span> <span data-ttu-id="e5cec-118">因此 Updategram 會使用預設對應，其中元素的名稱會對應到資料表名稱，而屬性或子元素則會對應到資料行。</span><span class="sxs-lookup"><span data-stu-id="e5cec-118">Therefore, the updategram uses default mapping, in which the element name maps to table name and the attributes or subelements map to columns.</span></span>  
  
 <span data-ttu-id="e5cec-119">第一個 updategram 是以屬性為中心，而且會) 區塊中的兩個晚上和晚上晚上，識別兩個 (移位 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="e5cec-119">This first updategram is attribute-centric and identifies two shifts (Day-Evening and Evening-Night) in the **\<before>** block.</span></span> <span data-ttu-id="e5cec-120">因為區塊中沒有對應的記錄 **\<after>** ，所以這是刪除作業。</span><span class="sxs-lookup"><span data-stu-id="e5cec-120">Because there is no corresponding record in the **\<after>** block, this is a delete operation.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
       <HumanResources.Shift ShiftID="4"  
                        Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift ShiftID="5"  
                        Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:before>  
  <updg:after>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="e5cec-121">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="e5cec-121">To test the updategram</span></span>  
  
1.  <span data-ttu-id="e5cec-122">完成範例 B ( 「使用 updategram 插入多筆記錄」 ) [使用 XML updategram &#40;SQLXML 4.0&#41;插入資料](inserting-data-using-xml-updategrams-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="e5cec-122">Complete example B ("Inserting multiple records by using an updategram") in [Inserting Data Using XML Updategrams &#40;SQLXML 4.0&#41;](inserting-data-using-xml-updategrams-sqlxml-4-0.md).</span></span>  
  
2.  <span data-ttu-id="e5cec-123">將上述 updategram 複製到 [記事本]，並將它儲存為與用來完成 ( 「使用 updategram 插入多筆記錄」 ) 在使用[XML updategram &#40;SQLXML 4.0&#41;插入資料](inserting-data-using-xml-updategrams-sqlxml-4-0.md)中所用的相同資料夾中的 Updategram-RemoveShifts.xml。</span><span class="sxs-lookup"><span data-stu-id="e5cec-123">Copy the updategram above to Notepad and save it as Updategram-RemoveShifts.xml in the same folder as was used to complete ("Inserting multiple records by using an updategram") in [Inserting Data Using XML Updategrams &#40;SQLXML 4.0&#41;](inserting-data-using-xml-updategrams-sqlxml-4-0.md).</span></span>  
  
3.  <span data-ttu-id="e5cec-124">建立及使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行 Updategram。</span><span class="sxs-lookup"><span data-stu-id="e5cec-124">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="e5cec-125">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="e5cec-125">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5cec-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5cec-126">See Also</span></span>  
 [<span data-ttu-id="e5cec-127">&#40;SQLXML 4.0&#41;的 Updategram 安全性考慮</span><span class="sxs-lookup"><span data-stu-id="e5cec-127">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
