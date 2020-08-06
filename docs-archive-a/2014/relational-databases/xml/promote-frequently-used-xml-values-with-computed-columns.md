---
title: 使用計算資料行升級常用的 XML 值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- promoting properties [XML in SQL Server]
- property promotion [XML in SQL Server]
ms.assetid: f5111896-c2fd-4209-b500-f2baa45489ad
author: rothja
ms.author: jroth
ms.openlocfilehash: bfb83b7772ffd92eab7087db11e4c3ffd96afa47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702502"
---
# <a name="promote-frequently-used-xml-values-with-computed-columns"></a><span data-ttu-id="ea7e0-102">使用計算資料行升級常用的 XML 值</span><span class="sxs-lookup"><span data-stu-id="ea7e0-102">Promote Frequently Used XML Values with Computed Columns</span></span>
  <span data-ttu-id="ea7e0-103">如果查詢主要只是針對少數的元素和屬性值來執行，您可能會想要將那些量升級至關聯式資料行。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-103">If queries are made principally on a small number of element and attribute values, you may want to promote those quantities into relational columns.</span></span> <span data-ttu-id="ea7e0-104">若已擷取整個 XML 執行個體，但您只是要針對小部分的 XML 資料來發出查詢要求時，這是很有幫助的。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-104">This is helpful when queries are issued on a small part of the XML data while the whole XML instance is retrieved.</span></span> <span data-ttu-id="ea7e0-105">您不需要在 XML 資料行上建立 XML 索引，</span><span class="sxs-lookup"><span data-stu-id="ea7e0-105">Creating an XML index on the XML column is not required.</span></span> <span data-ttu-id="ea7e0-106">即可為升級的資料行建立索引。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-106">Instead, the promoted column can be indexed.</span></span> <span data-ttu-id="ea7e0-107">您必須撰寫查詢來使用升級的資料行。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-107">Queries must be written to use the promoted column.</span></span> <span data-ttu-id="ea7e0-108">意即，查詢最佳化工具不再將 XML 資料行查詢的目標放在升級的資料行。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-108">That is, the query optimizer does not target again the queries on the XML column to the promoted column.</span></span>  
  
 <span data-ttu-id="ea7e0-109">升級的資料行可以是同一資料表中的已計算資料行，也可以是資料表中由使用者維護的另一個資料行。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-109">The promoted column can be a computed column in the same table or it can be a separate, user-maintained column in a table.</span></span> <span data-ttu-id="ea7e0-110">當單一值從每個 XML 執行個體升級起來時，這就足夠了。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-110">This is sufficient when singleton values are promoted from each XML instance.</span></span> <span data-ttu-id="ea7e0-111">然而，若為多重值的屬性，您就必須為屬性建立個別的資料表，請見下節說明。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-111">However, for multi-valued properties, you have to create a separate table for the property, as described in the following section.</span></span>  
  
## <a name="computed-column-based-on-the-xml-data-type"></a><span data-ttu-id="ea7e0-112">以 xml 資料類型為基礎的計算的資料行</span><span class="sxs-lookup"><span data-stu-id="ea7e0-112">Computed Column Based on the xml Data Type</span></span>  
 <span data-ttu-id="ea7e0-113">您可以使用叫用資料類型方法的使用者自訂函數來建立計算資料行 `xml` 。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-113">A computed column can be created by using a user-defined function that invokes `xml` data type methods.</span></span> <span data-ttu-id="ea7e0-114">計算資料行的類型可以是任何 SQL 類型，包括 XML。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-114">The type of the computed column can be any SQL type, including XML.</span></span> <span data-ttu-id="ea7e0-115">下列範例會加以說明。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-115">This is illustrated in the following example.</span></span>  
  
### <a name="example-computed-column-based-on-the-xml-data-type-method"></a><span data-ttu-id="ea7e0-116">範例：以 xml 資料類型方法為基礎的計算資料行</span><span class="sxs-lookup"><span data-stu-id="ea7e0-116">Example: Computed Column Based on the xml Data Type Method</span></span>  
 <span data-ttu-id="ea7e0-117">針對書籍的 ISBN 號碼來建立使用者自訂函數：</span><span class="sxs-lookup"><span data-stu-id="ea7e0-117">Create the user-defined function for a book ISBN number:</span></span>  
  
```  
CREATE FUNCTION udf_get_book_ISBN (@xData xml)  
RETURNS varchar(20)  
BEGIN  
   DECLARE @ISBN   varchar(20)  
   SELECT @ISBN = @xData.value('/book[1]/@ISBN', 'varchar(20)')  
   RETURN @ISBN   
END  
```  
  
 <span data-ttu-id="ea7e0-118">將計算的資料行加入 ISBN 的資料表中：</span><span class="sxs-lookup"><span data-stu-id="ea7e0-118">Add a computed column to the table for the ISBN:</span></span>  
  
```  
ALTER TABLE      T  
ADD   ISBN AS dbo.udf_get_book_ISBN(xCol)  
```  
  
 <span data-ttu-id="ea7e0-119">可以用一般的方式來檢索計算的資料行。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-119">The computed column can be indexed in the usual way.</span></span>  
  
### <a name="example-queries-on-a-computed-column-based-on-xml-data-type-methods"></a><span data-ttu-id="ea7e0-120">範例：查詢以 xml 資料類型方法為基礎的計算資料行</span><span class="sxs-lookup"><span data-stu-id="ea7e0-120">Example: Queries on a Computed Column Based on xml Data Type Methods</span></span>  
 <span data-ttu-id="ea7e0-121">若要取得 ISBN 為 0-7356-1588-2 的 <`book`>，請：</span><span class="sxs-lookup"><span data-stu-id="ea7e0-121">To obtain the <`book`> whose ISBN is 0-7356-1588-2:</span></span>  
  
```  
SELECT xCol  
FROM   T  
WHERE  xCol.exist('/book/@ISBN[. = "0-7356-1588-2"]') = 1  
```  
  
 <span data-ttu-id="ea7e0-122">您可以改寫對 XML 資料行的查詢，以使用計算的資料行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ea7e0-122">The query on the XML column can be rewritten to use the computed column as follows:</span></span>  
  
```  
SELECT xCol  
FROM   T  
WHERE  ISBN = '0-7356-1588-2'  
```  
  
 <span data-ttu-id="ea7e0-123">您可以使用使用者定義函數來建立使用者定義函數，以傳回 `xml` 資料類型和計算資料行。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-123">You can create a user-defined function to return the `xml` data type and a computed column by using the user-defined function.</span></span> <span data-ttu-id="ea7e0-124">然而，您不能在計算的 XML 資料行上建立 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-124">However, you cannot create an XML index on the computed, XML column.</span></span>  
  
## <a name="creating-property-tables"></a><span data-ttu-id="ea7e0-125">建立屬性資料表</span><span class="sxs-lookup"><span data-stu-id="ea7e0-125">Creating Property Tables</span></span>  
 <span data-ttu-id="ea7e0-126">您可能會想要將某些多重值的屬性從 XML 資料升級至一或多個資料表中、在那些資料表上建立索引，然後再讓您的查詢目標使用那些資料表。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-126">You may want to promote some of the multivalued properties from your XML data into one or more tables, create indexes on those tables, and target again your queries to use them.</span></span> <span data-ttu-id="ea7e0-127">一般案例中都是由少數的屬性來涵蓋大部份的查詢工作負載。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-127">A typical scenario is one in which a small number of properties covers most of your query workload.</span></span> <span data-ttu-id="ea7e0-128">您可以執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="ea7e0-128">You can do the following:</span></span>  
  
-   <span data-ttu-id="ea7e0-129">建立一或多個資料表來保存多重值的屬性。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-129">Create one or more tables to hold the multivalued properties.</span></span> <span data-ttu-id="ea7e0-130">您會發現，每個資料表各儲存一個屬性，並且在屬性資料表中複製基底資料表的主索引鍵，再向後聯結基底資料表，這麼做是很方便的。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-130">You may find it convenient to store one property per table and duplicate the primary key of the base table in the property tables for back joining with the base table.</span></span>  
  
-   <span data-ttu-id="ea7e0-131">如果您要維持屬性的相對順序，就必須為相對順序導入另一個資料行。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-131">If you want to maintain the relative order of the properties, you have to introduce a separate column for the relative order.</span></span>  
  
-   <span data-ttu-id="ea7e0-132">在 XML 資料行上建立觸發程序，以維護屬性資料表。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-132">Create triggers on the XML column to maintain the property tables.</span></span> <span data-ttu-id="ea7e0-133">在觸發程序中執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="ea7e0-133">Within the triggers, do one of the following:</span></span>  
  
    -   <span data-ttu-id="ea7e0-134">使用 `xml` 資料類型方法（例如\*\* ( # B1 的節點**和**值 ( # B3 \*\*）來插入和刪除屬性資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-134">Use `xml` data type methods, such as **nodes()** and **value()**, to insert and delete rows of the property tables.</span></span>  
  
    -   <span data-ttu-id="ea7e0-135">在 Common Language Runtime (CLR) 中建立資料流資料表值函式，以插入及刪除屬性資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-135">Create streaming table-valued functions in the common language runtime (CLR) to insert and delete rows of the property tables.</span></span>  
  
    -   <span data-ttu-id="ea7e0-136">撰寫查詢來讓 SQL 存取屬性資料表，並讓 XML 存取基底資料表中的 XML 資料表，再使用其主索引鍵來聯結這二個資料表。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-136">Write queries for SQL access to the property tables and for XML access to the XML column in the base table, with joins between the tables by using their primary key.</span></span>  
  
### <a name="example-create-a-property-table"></a><span data-ttu-id="ea7e0-137">範例：建立屬性資料表</span><span class="sxs-lookup"><span data-stu-id="ea7e0-137">Example: Create a Property Table</span></span>  
 <span data-ttu-id="ea7e0-138">舉例來說，假設您要升級作者的名字。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-138">For illustration, assume that you want to promote the first name of the authors.</span></span> <span data-ttu-id="ea7e0-139">書籍的作者可能不只一個，所以名字是多重值的屬性。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-139">Books have one or more authors, so that first name is a multivalued property.</span></span> <span data-ttu-id="ea7e0-140">每個名字都是儲存在屬性資料表的不同資料列中。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-140">Each first name is stored in a separate row of a property table.</span></span> <span data-ttu-id="ea7e0-141">在屬性資料表中會複製基底資料表的主索引鍵，以供向後聯結。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-141">The primary key of the base table is duplicated in the property table for back join.</span></span>  
  
```  
create table tblPropAuthor (propPK int, propAuthor varchar(max))  
```  
  
### <a name="example-create-a-user-defined-function-to-generate-a-rowset-from-an-xml-instance"></a><span data-ttu-id="ea7e0-142">範例：建立使用者自訂函數，以從 XML 執行個體產生資料列集</span><span class="sxs-lookup"><span data-stu-id="ea7e0-142">Example: Create a User-defined Function to Generate a Rowset from an XML Instance</span></span>  
 <span data-ttu-id="ea7e0-143">下列資料表值函式 udf_XML2Table 可接受主索引鍵值和 XML 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-143">The following table-valued function, udf_XML2Table, accepts a primary key value and an XML instance.</span></span> <span data-ttu-id="ea7e0-144">它會擷取 <`book`> 元素中所有作者的名字，並傳回主索引鍵的資料列集 (名字配對)。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-144">It retrieves the first name of all authors of the <`book`> elements and returns a rowset of primary key, first name pairs.</span></span>  
  
```  
create function udf_XML2Table (@pk int, @xCol xml)  
returns @ret_Table table (propPK int, propAuthor varchar(max))  
with schemabinding  
as  
begin  
      insert into @ret_Table   
      select @pk, nref.value('.', 'varchar(max)')  
      from   @xCol.nodes('/book/author/first-name') R(nref)  
      return  
end  
```  
  
### <a name="example-create-triggers-to-populate-a-property-table"></a><span data-ttu-id="ea7e0-145">範例：建立觸發程序以填入屬性資料表</span><span class="sxs-lookup"><span data-stu-id="ea7e0-145">Example: Create Triggers to Populate a Property Table</span></span>  
 <span data-ttu-id="ea7e0-146">插入觸發程序會在屬性資料表中插入資料列：</span><span class="sxs-lookup"><span data-stu-id="ea7e0-146">The insert trigger inserts rows into the property table:</span></span>  
  
```  
create trigger trg_docs_INS on T for insert  
as  
      declare @wantedXML xml  
      declare @FK int  
      select @wantedXML = xCol from inserted  
      select @FK = PK from inserted  
  
   insert into tblPropAuthor  
   select * from dbo.udf_XML2Table(@FK, @wantedXML)  
```  
  
 <span data-ttu-id="ea7e0-147">刪除觸發程序會依據已刪除之資料列的主索引鍵值，從屬性資料表中刪除資料列：</span><span class="sxs-lookup"><span data-stu-id="ea7e0-147">The delete trigger deletes the rows from the property table based on the primary key value of the deleted rows:</span></span>  
  
```  
create trigger trg_docs_DEL on T for delete  
as  
   declare @FK int  
   select @FK = PK from deleted  
   delete tblPropAuthor where propPK = @FK  
```  
  
 <span data-ttu-id="ea7e0-148">更新觸發程序會在對應至已更新之 XML 執行個體的屬性資料表中，刪除現有的資料列，並且在屬性資料表中插入新的資料列：</span><span class="sxs-lookup"><span data-stu-id="ea7e0-148">The update trigger deletes the existing rows in the property table corresponding to the updated XML instance and inserts new rows into the property table:</span></span>  
  
```  
create trigger trg_docs_UPD  
on T  
for update  
as  
if update(xCol) or update(pk)  
begin  
      declare @FK int  
      declare @wantedXML xml  
      select @FK = PK from deleted  
      delete tblPropAuthor where propPK = @FK  
  
   select @wantedXML = xCol from inserted  
   select @FK = pk from inserted  
  
   insert into tblPropAuthor   
      select * from dbo.udf_XML2Table(@FK, @wantedXML)  
end  
```  
  
### <a name="example-find-xml-instances-whose-authors-have-the-same-first-name"></a><span data-ttu-id="ea7e0-149">範例：尋找作者名字相同的 XML 執行個體</span><span class="sxs-lookup"><span data-stu-id="ea7e0-149">Example: Find XML Instances Whose Authors Have the Same First Name</span></span>  
 <span data-ttu-id="ea7e0-150">查詢可以在 XML 資料行上形成。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-150">The query can be formed on the XML column.</span></span> <span data-ttu-id="ea7e0-151">或者，可以在屬性資料表中搜尋 "David" 這個名字，然後執行向後聯結基底資料表，以傳回 XML 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-151">Alternatively, it can search the property table for first name "David" and perform a back join with the base table to return the XML instance.</span></span> <span data-ttu-id="ea7e0-152">例如：</span><span class="sxs-lookup"><span data-stu-id="ea7e0-152">For example:</span></span>  
  
```  
SELECT xCol   
FROM     T JOIN tblPropAuthor ON T.pk = tblPropAuthor.propPK  
WHERE    tblPropAuthor.propAuthor = 'David'  
```  
  
### <a name="example-solution-using-the-clr-streaming-table-valued-function"></a><span data-ttu-id="ea7e0-153">範例：使用 CLR 資料流資料表值函式的解決方案</span><span class="sxs-lookup"><span data-stu-id="ea7e0-153">Example: Solution Using the CLR Streaming Table-valued Function</span></span>  
 <span data-ttu-id="ea7e0-154">這個解決方案包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="ea7e0-154">This solution is made up of the following steps:</span></span>  
  
1.  <span data-ttu-id="ea7e0-155">定義 CLR 類別 SqlReaderBase，在 XML 執行個體上套用路徑運算式，以實作 ISqlReader 並產生資料流資料表值的輸出。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-155">Define a CLR class, SqlReaderBase, that implements ISqlReader and generates a streaming, table-valued output by applying a path expression on an XML instance.</span></span>  
  
2.  <span data-ttu-id="ea7e0-156">建立組件及 Transact-SQL 使用者自訂函數，以啟動 CLR 類別。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-156">Create an assembly and a Transact-SQL user-defined function to start the CLR class.</span></span>  
  
3.  <span data-ttu-id="ea7e0-157">使用使用者自訂函數來定義插入、更新及刪除觸發程序，以維護屬性資料表。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-157">Define the insert, update, and delete triggers by using the user-defined function to maintain a property tables.</span></span>  
  
 <span data-ttu-id="ea7e0-158">若要執行此作業，您要先建立資料流 CLR 函數。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-158">To do this, you first create the streaming CLR function.</span></span> <span data-ttu-id="ea7e0-159">`xml`資料類型會在 ADO.NET 中公開為 managed 類別 SqlXml，並支援傳回 XmlReader 的**CreateReader ( # B1**方法。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-159">The `xml` data type is exposed as a managed class SqlXml in ADO.NET and supports the **CreateReader()** method that returns an XmlReader.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ea7e0-160">本節中的範例程式碼使用 XPathDocument 及 XPathNavigator。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-160">The example code in this section uses XPathDocument and XPathNavigator.</span></span> <span data-ttu-id="ea7e0-161">它們會強制您將所有 XML 文件載入記憶體。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-161">These force you to load all the XML documents into memory.</span></span> <span data-ttu-id="ea7e0-162">如果您在應用程式中使用類似的程式碼來處理好幾個大型 XML 文件，此程式碼是無法調整的。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-162">If you are using similar code in your application to process several large XML documents, this code is not scalable.</span></span> <span data-ttu-id="ea7e0-163">反之，您要讓記憶體配置維持少量，並且盡可能使用資料流介面。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-163">Instead, keep memory allocations small and use streaming interfaces whenever possible.</span></span> <span data-ttu-id="ea7e0-164">如需有關效能的詳細資訊，請參閱 [CLR 整合的架構](../../database-engine/dev-guide/architecture-of-clr-integration.md)。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-164">For more information about performance, see [Architecture of CLR Integration](../../database-engine/dev-guide/architecture-of-clr-integration.md).</span></span>  
  
```  
public class c_streaming_xml_tvf {  
   public static ISqlReader streaming_xml_tvf   
(SqlXml xmlDoc, string pathExpression) {  
      return (new TestSqlReaderBase (xmlDoc, pathExpression));  
   }  
}  
  
// Class that implements ISqlReader  
public class TestSqlReaderBase : ISqlReader {  
XPathNodeIterator m_iterator;           
   public SqlChars FirstName;  
// Metadata for current resultset  
private SqlMetaData[] m_rgSqlMetaData;        
  
   public TestSqlReaderBase (SqlXml xmlDoc, string pathExpression) {     
      // Variables for XPath navigation  
      XPathDocument xDoc;  
      XPathNavigator xNav;  
      XPathExpression xPath;  
  
      // Set sql metadata  
      m_rgSqlMetaData = new SqlMetaData[1];  
      m_rgSqlMetaData[0] = new SqlMetaData ("FirstName",    
SqlDbType.NVarChar,50);     
  
      //Set up the Navigator  
      if (!xmlDoc.IsNull)  
          xDoc = new XPathDocument (xmlDoc.CreateReader());  
      else  
          xDoc = new XPathDocument ();  
      xNav = xDoc.CreateNavigator();  
      xPath = xNav.Compile (pathExpression);  
      m_iterator = xNav.Select(xPath);  
   }  
   public bool Read() {  
      bool moreRows = true;  
      if (moreRows = m_iterator.MoveNext())  
         FirstName = new SqlChars (m_iterator.Current.Value);  
      return moreRows;  
   }  
}  
```  
  
 <span data-ttu-id="ea7e0-165">接著，請建立組件以及對應於 CLR 函數 streaming_xml_tvf 的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 使用者自訂函數 SQL_streaming_xml_tvf (未顯示)。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-165">Next, create an assembly and a [!INCLUDE[tsql](../../includes/tsql-md.md)] user-defined function, SQL_streaming_xml_tvf (not shown), that corresponds to the CLR function, streaming_xml_tvf.</span></span> <span data-ttu-id="ea7e0-166">使用者自訂函數可用來定義資料表值函式 CLR_udf_XML2Table，以產生資料列集：</span><span class="sxs-lookup"><span data-stu-id="ea7e0-166">The user-defined function is used to define the table-valued function, CLR_udf_XML2Table, for rowset generation:</span></span>  
  
```  
create function CLR_udf_XML2Table (@pk int, @xCol xml)  
returns @ret_Table table (FK int, FirstName varchar(max))  
with schemabinding  
as  
begin  
      insert into @ret_Table   
   select @pk, FirstName   
   FROM   SQL_streaming_xml_tvf (@xCol, '/book/author/first-name')  
      return  
end  
```  
  
 <span data-ttu-id="ea7e0-167">最後，請依照範例「建立觸發程序來擴展屬性資料表」的說明來定義觸發程序，但請將 udf_XML2Table 置換成 CLR_udf_XML2Table 函數。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-167">Finally, define triggers as shown in the example, "Create triggers to populate a property table", but replace udf_XML2Table with the CLR_udf_XML2Table function.</span></span> <span data-ttu-id="ea7e0-168">插入觸發程序如下列範例中所示：</span><span class="sxs-lookup"><span data-stu-id="ea7e0-168">The insert trigger is shown in the following example:</span></span>  
  
```  
create trigger CLR_trg_docs_INS on T for insert  
as  
   declare @wantedXML xml  
   declare @FK int  
   select @wantedXML = xCol from inserted  
   select @FK = PK from inserted  
  
   insert into tblPropAuthor  
      select *  
   from    dbo.CLR_udf_XML2Table(@FK, @wantedXML)  
```  
  
 <span data-ttu-id="ea7e0-169">刪除觸發程序與非 CLR 版本相同。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-169">The delete trigger is identical to the non-CLR version.</span></span> <span data-ttu-id="ea7e0-170">然而，更新觸發程序只會將函數 udf_XML2Table() 置換成 CLR_udf_XML2Table()。</span><span class="sxs-lookup"><span data-stu-id="ea7e0-170">However, the update trigger just replaces the function udf_XML2Table() with CLR_udf_XML2Table().</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea7e0-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea7e0-171">See Also</span></span>  
 [<span data-ttu-id="ea7e0-172">使用計算資料行中的 XML</span><span class="sxs-lookup"><span data-stu-id="ea7e0-172">Use XML in Computed Columns</span></span>](use-xml-in-computed-columns.md)  
  
  
