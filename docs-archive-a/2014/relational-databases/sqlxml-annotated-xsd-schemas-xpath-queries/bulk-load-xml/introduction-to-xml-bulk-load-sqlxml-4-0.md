---
title: XML 大量載入簡介 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nontransacted XML Bulk Load operations
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
- transacted XML Bulk Load operations
- streaming XML data
ms.assetid: 38bd3cbd-65ef-4c23-9ef3-e70ecf6bb88a
author: rothja
ms.author: jroth
ms.openlocfilehash: 4f3e0e78edd967e5fcb7377312c1811d34cb1ef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686876"
---
# <a name="introduction-to-xml-bulk-load-sqlxml-40"></a><span data-ttu-id="928bf-102">XML 大量載入簡介 (SQLXML 4.0) </span><span class="sxs-lookup"><span data-stu-id="928bf-102">Introduction to XML Bulk Load (SQLXML 4.0)</span></span>
  <span data-ttu-id="928bf-103">XML 大量載入是獨立的 COM 物件，可讓您將半結構化的 XML 資料載入至 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="928bf-103">XML Bulk Load is a stand-alone COM object that allows you to load semistructured XML data into Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables.</span></span>  
  
 <span data-ttu-id="928bf-104">您可以使用 INSERT 陳述式和 OPENXML 函數將 XML 資料插入至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫，不過當您需要插入大量的 XML 資料時，大量載入公用程式可以提供較佳的效能。</span><span class="sxs-lookup"><span data-stu-id="928bf-104">You can insert XML data into a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database by using an INSERT statement and the OPENXML function; however, the Bulk Load utility provides better performance when you need to insert large amounts of XML data.</span></span>  
  
 <span data-ttu-id="928bf-105">XML 大量載入物件模型的 Execute 方法會採用兩個參數：</span><span class="sxs-lookup"><span data-stu-id="928bf-105">The Execute method of the XML Bulk Load object model takes two parameters:</span></span>  
  
-   <span data-ttu-id="928bf-106">註解 XML 結構描述定義 (XSD) 或 XML 資料精簡 (XDR) 結構描述。</span><span class="sxs-lookup"><span data-stu-id="928bf-106">An annotated XML Schema Definition (XSD) or XML-Data Reduced (XDR) schema.</span></span> <span data-ttu-id="928bf-107">XML 大量載入公用程式在識別其中將插入 XML 資料的 SQL Server 資料表時，會解譯此對應結構描述以及結構描述中所指定的註解。</span><span class="sxs-lookup"><span data-stu-id="928bf-107">The XML Bulk Load utility interprets this mapping schema and the annotations that are specified in the schema in identifying the SQL Server tables into which the XML data is to be inserted.</span></span>  
  
-   <span data-ttu-id="928bf-108">XML 文件或文件片段 (文件片段是沒有單一最上層元素的文件)。</span><span class="sxs-lookup"><span data-stu-id="928bf-108">An XML document or document fragment (a document fragment is a document without a single top-level element).</span></span> <span data-ttu-id="928bf-109">可以指定 XML 大量載入能從中讀取的檔案名稱或資料流。</span><span class="sxs-lookup"><span data-stu-id="928bf-109">A file name or a stream from which XML Bulk Load can read can be specified.</span></span>  
  
 <span data-ttu-id="928bf-110">XML 大量載入會解譯對應結構描述並識別其中將插入 XML 資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="928bf-110">XML Bulk Load interprets the mapping schema and identifies the table(s) into which the XML data is to be inserted.</span></span>  
  
 <span data-ttu-id="928bf-111">這裡假設您熟悉下列的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能：</span><span class="sxs-lookup"><span data-stu-id="928bf-111">It is assumed that you are familiar with the following [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features:</span></span>  
  
-   <span data-ttu-id="928bf-112">註解 XSD 和 XDR 結構描述。</span><span class="sxs-lookup"><span data-stu-id="928bf-112">Annotated XSD and XDR schemas.</span></span> <span data-ttu-id="928bf-113">如需批註式 XSD 架構的詳細資訊，請參閱[批註式 Xsd 架構簡介 &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="928bf-113">For more information about annotated XSD schemas, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="928bf-114">如需批註式 XDR 架構的詳細資訊，請參閱[SQLXML 4.0&#41;中 &#40;已被取代的批註式 Xdr 架構](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="928bf-114">For information about annotated XDR schemas, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="928bf-115">大量插入機制，例如 [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT 陳述式和 bcp 公用程式。</span><span class="sxs-lookup"><span data-stu-id="928bf-115">bulk insert mechanisms, such as the [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT statement and the bcp utility.</span></span> <span data-ttu-id="928bf-116">如需詳細資訊，請參閱[BULK INSERT &#40;transact-sql&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)和[bcp 公用程式](../../../tools/bcp-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="928bf-116">For more information, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) and [bcp Utility](../../../tools/bcp-utility.md).</span></span>  
  
## <a name="streaming-of-xml-data"></a><span data-ttu-id="928bf-117">XML 資料的資料流</span><span class="sxs-lookup"><span data-stu-id="928bf-117">Streaming of XML Data</span></span>  
 <span data-ttu-id="928bf-118">因為來源 XML 文件可能很大，所以不會將整個文件讀入記憶體來進行大量載入處理，</span><span class="sxs-lookup"><span data-stu-id="928bf-118">Because the source XML document can be large, the entire document is not read into memory for bulk load processing.</span></span> <span data-ttu-id="928bf-119">而是由 XML 大量載入以資料流的方式解譯 XML 資料，再加以讀取。</span><span class="sxs-lookup"><span data-stu-id="928bf-119">Instead, XML Bulk Load interprets the XML data as a stream and reads it.</span></span> <span data-ttu-id="928bf-120">此公用程式讀取資料時會識別資料庫資料表，從 XML 資料來源產生適當的記錄，然後再將記錄傳送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 進行插入。</span><span class="sxs-lookup"><span data-stu-id="928bf-120">As the utility reads the data, it identifies the database table(s), generates the appropriate record(s) from the XML data source, and then sends the record(s) to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for insertion.</span></span>  
  
 <span data-ttu-id="928bf-121">例如，下列來源 XML 檔是由 **\<Customer>** 元素和 **\<Order>** 子項目所組成：</span><span class="sxs-lookup"><span data-stu-id="928bf-121">For example, the following source XML document consists of **\<Customer>** elements and **\<Order>** child elements:</span></span>  
  
```  
<Customer ...>  
    <Order.../>  
    <Order .../>  
     ...  
</Customer>  
...  
```  
  
 <span data-ttu-id="928bf-122">當 XML 大量載入讀取 **\<Customer>** 元素時，它會產生 Customertable 的記錄。</span><span class="sxs-lookup"><span data-stu-id="928bf-122">As XML Bulk Load reads the **\<Customer>** element, it generates a record for the Customertable.</span></span> <span data-ttu-id="928bf-123">當它讀取 **\</Customer>** 結束標記時，XML 大量載入會將該記錄插入中的資料表 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="928bf-123">When it reads the **\</Customer>** end tag, XML Bulk Load inserts that record into the table in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="928bf-124">同樣地，當它讀取 **\<Order>** 元素時，XML 大量載入會產生 Ordertable 的記錄，然後在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 讀取結束標記時將該記錄插入資料表中 **\</Order>** 。</span><span class="sxs-lookup"><span data-stu-id="928bf-124">In the same way, when it reads the **\<Order>** element, XML Bulk Load generates a record for the Ordertable, and then inserts that record into the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table upon reading the **\</Order>** end tag.</span></span>  
  
## <a name="transacted-and-nontransacted-xml-bulk-load-operations"></a><span data-ttu-id="928bf-125">交易和非交易 XML 大量載入作業</span><span class="sxs-lookup"><span data-stu-id="928bf-125">Transacted and Nontransacted XML Bulk Load Operations</span></span>  
 <span data-ttu-id="928bf-126">XML 大量載入可以在交易或非交易模式中操作。</span><span class="sxs-lookup"><span data-stu-id="928bf-126">XML Bulk Load can operate in either a transacted or a nontransacted mode.</span></span> <span data-ttu-id="928bf-127">如果您是在非交易模式中大量載入，效能通常是最佳的：也就是說，Transaction 屬性會設定為 FALSE) 而且下列其中一個條件為 true：</span><span class="sxs-lookup"><span data-stu-id="928bf-127">Performance is usually optimal if you are bulk loading in a nontransacted mode: that is, the Transaction property is set to FALSE) and either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="928bf-128">其中要大量載入資料的資料表是空的，且沒有任何索引。</span><span class="sxs-lookup"><span data-stu-id="928bf-128">The tables into which the data is bulk loaded are empty with no indexes.</span></span>  
  
-   <span data-ttu-id="928bf-129">資料表具有資料和唯一的索引。</span><span class="sxs-lookup"><span data-stu-id="928bf-129">The tables have data and unique indexes.</span></span>  
  
 <span data-ttu-id="928bf-130">非交易的方法並不保證能在大量載入程序發生問題時進行回復 (雖然可能可以進行部分回復)。</span><span class="sxs-lookup"><span data-stu-id="928bf-130">The nontransacted approach does not guarantee a rollback if something goes wrong in the bulk load process (although partial rollbacks can happen).</span></span> <span data-ttu-id="928bf-131">當資料表是空白時，適用非交易的大量載入。</span><span class="sxs-lookup"><span data-stu-id="928bf-131">The nontransacted bulk load is appropriate when the database is empty.</span></span> <span data-ttu-id="928bf-132">因此在發生問題時，您可以清除資料庫，然後再次啟動 XML 大量載入。</span><span class="sxs-lookup"><span data-stu-id="928bf-132">Therefore, if something does go wrong, you can clean the database and start XML Bulk Load again.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="928bf-133">在非交易模式中，XML 大量載入會使用預設的內部交易並加以認可。</span><span class="sxs-lookup"><span data-stu-id="928bf-133">In nontransacted mode, XML Bulk Load uses a default internal transaction and commits it.</span></span> <span data-ttu-id="928bf-134">當 Transaction 屬性設定為 TRUE 時，XML 大量載入不會在此交易上呼叫 commit。</span><span class="sxs-lookup"><span data-stu-id="928bf-134">When the Transaction property is set to TRUE, XML Bulk Load does not call commit on this transaction.</span></span>  
  
 <span data-ttu-id="928bf-135">如果 Transaction 屬性設定為 TRUE，XML 大量載入會建立暫存檔案，這是對應架構中所識別的每個資料表各一個檔案。</span><span class="sxs-lookup"><span data-stu-id="928bf-135">If the Transaction property is set to TRUE, XML Bulk Load creates temporary files, one for each table that is identified in the mapping schema.</span></span> <span data-ttu-id="928bf-136">XML 大量載入會先把來自來源 XML 文件的記錄儲存在這些暫存檔中。</span><span class="sxs-lookup"><span data-stu-id="928bf-136">XML Bulk Load first stores the records from the source XML document in these temporary files.</span></span> <span data-ttu-id="928bf-137">接著 [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT 陳述式會從檔案擷取這些記錄，然後將它們儲存在對應的資料表中。</span><span class="sxs-lookup"><span data-stu-id="928bf-137">Then, a [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT statement retrieves these records from the files and stores them in the corresponding tables.</span></span> <span data-ttu-id="928bf-138">您可以使用 TempFilePath 屬性來指定這些暫存檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="928bf-138">You can specify the location for these temporary files by using the TempFilePath property.</span></span> <span data-ttu-id="928bf-139">您必須確定用於 XML 大量載入的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 帳戶具有這個路徑的存取權。</span><span class="sxs-lookup"><span data-stu-id="928bf-139">You must ensure that the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account used with XML Bulk Load has access to this path.</span></span> <span data-ttu-id="928bf-140">如果未指定 TempFilePath 屬性，則會使用 TEMP 環境變數中指定的預設檔案路徑來建立暫存檔案。</span><span class="sxs-lookup"><span data-stu-id="928bf-140">If the TempFilePath property is not specified, the default file path that is specified in the TEMP environment variable is used to create the temporary files.</span></span>  
  
 <span data-ttu-id="928bf-141">如果 Transaction 屬性設定為 FALSE (預設設定) ，則 XML 大量載入會使用 OLE DB 介面 IRowsetFastLoad 來大量載入資料。</span><span class="sxs-lookup"><span data-stu-id="928bf-141">If the Transaction property is set to FALSE (the default setting), XML Bulk Load uses the OLE DB interface IRowsetFastLoad to bulk load the data.</span></span>  
  
 <span data-ttu-id="928bf-142">如果 ConnectionString 屬性設定連接字串，且 Transaction 屬性設定為 TRUE，則 XML 大量載入會在自己的交易內容中運作。</span><span class="sxs-lookup"><span data-stu-id="928bf-142">If the ConnectionString property sets the connection string, and the Transaction property is set to TRUE, XML Bulk Load operates in its own transaction context.</span></span> <span data-ttu-id="928bf-143">(例如，XML 大量載入會啟動本身的交易，然後依需要進行認可或回復)。</span><span class="sxs-lookup"><span data-stu-id="928bf-143">(For example, XML Bulk Load starts its own transaction, and commits or rolls back as appropriate.)</span></span>  
  
 <span data-ttu-id="928bf-144">如果 ConnectionCommand 屬性設定與現有連線物件的連接，且 Transaction 屬性設定為 TRUE，則 XML 大量載入不會在成功或失敗的情況下，分別發出 COMMIT 或 ROLLBACK 語句。</span><span class="sxs-lookup"><span data-stu-id="928bf-144">If the ConnectionCommand property sets the connection with an existing connection object and the Transaction property is set to TRUE, XML Bulk Load does not issue a COMMIT or ROLLBACK statement in the case of a success or a failure, respectively.</span></span> <span data-ttu-id="928bf-145">如果發生錯誤，XML 大量載入會傳回適當的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="928bf-145">If there is an error, XML Bulk Load returns the appropriate error message.</span></span> <span data-ttu-id="928bf-146">至於是否要發出 COMMIT 或 ROLLBACK 陳述式，則會留給起始大量載入的用戶端決定。</span><span class="sxs-lookup"><span data-stu-id="928bf-146">The decision to issue a COMMIT or ROLLBACK statement is left to the client that initiated the bulk load.</span></span> <span data-ttu-id="928bf-147">用於 XML 大量載入的連線物件應為 ICommand 類型，或為 ADO 命令物件。</span><span class="sxs-lookup"><span data-stu-id="928bf-147">The connection object that is used for XML Bulk Load should be of type ICommand or be an ADO command object.</span></span>  
  
 <span data-ttu-id="928bf-148">在 SQLXML 4.0 中，ConnectionObject 不能用於將 Transaction 屬性設為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="928bf-148">In SQLXML 4.0, a ConnectionObject cannot be used with the Transaction property set to FALSE.</span></span> <span data-ttu-id="928bf-149">ConnectionObject 不支援非交易模式，因為無法在傳入的會話上開啟一個以上的 IRowsetFastLoad 介面。</span><span class="sxs-lookup"><span data-stu-id="928bf-149">The nontransacted mode is not supported with a ConnectionObject because it is impossible to open more than one IRowsetFastLoad interface on a passed-in session.</span></span>  
  
  
