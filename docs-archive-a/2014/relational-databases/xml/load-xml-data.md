---
title: 載入 XML 資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML data [SQL Server], loading
- loading XML data
ms.assetid: d1741e8d-f44e-49ec-9f14-10208b5468a7
author: rothja
ms.author: jroth
ms.openlocfilehash: c48d1d6feccb7df9fec9801ee56abcab99884754
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702505"
---
# <a name="load-xml-data"></a><span data-ttu-id="34b57-102">載入 XML 資料</span><span class="sxs-lookup"><span data-stu-id="34b57-102">Load XML Data</span></span>
  <span data-ttu-id="34b57-103">您可以透過幾種方式將 XML 資料傳送到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="34b57-103">You can transfer XML data into [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in several ways.</span></span> <span data-ttu-id="34b57-104">例如：</span><span class="sxs-lookup"><span data-stu-id="34b57-104">For example:</span></span>  
  
-   <span data-ttu-id="34b57-105">如果您將資料放在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的 [n]text 或 image 資料行中，則可使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]將資料表匯入更新的版本。</span><span class="sxs-lookup"><span data-stu-id="34b57-105">If you have your data in an [n]text or image column in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, you can import the table by using [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="34b57-106">使用 ALTER TABLE 陳述式將資料行類型變更為 XML。</span><span class="sxs-lookup"><span data-stu-id="34b57-106">Change the column type to XML by using the ALTER TABLE statement.</span></span>  
  
-   <span data-ttu-id="34b57-107">您可以使用 bcp out 從其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫大量複製資料，然後再使用 bcp in 將資料大量插入更新版本的資料庫。</span><span class="sxs-lookup"><span data-stu-id="34b57-107">You can bulk copy your data from another [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database by using bcp out, and then bulk insert the data into the later version database by using bcp in.</span></span>  
  
-   <span data-ttu-id="34b57-108">如果您將資料放在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的關聯式資料行中，請建立一個含有 [n]text 資料行的新資料表，並可選擇加入主索引鍵資料行來放置資料列識別碼。</span><span class="sxs-lookup"><span data-stu-id="34b57-108">If you have data in relational columns in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, create a new table with an [n]text column and, optionally, a primary key column for a row identifier.</span></span> <span data-ttu-id="34b57-109">使用用戶端程式設計來擷取在伺服器上以 FOR XML 產生的 XML，並將它寫入 `[n]text` 資料行。</span><span class="sxs-lookup"><span data-stu-id="34b57-109">Use client-side programming to retrieve the XML that is generated at the server with FOR XML and write it into the `[n]text` column.</span></span> <span data-ttu-id="34b57-110">然後使用先前提到的技巧，將資料傳送至更新版本的資料庫。</span><span class="sxs-lookup"><span data-stu-id="34b57-110">Then, use the previously mentioned techniques to transfer data to a later version database.</span></span> <span data-ttu-id="34b57-111">您可以選擇直接將 XML 寫入更新版本資料庫中的 XML 資料行。</span><span class="sxs-lookup"><span data-stu-id="34b57-111">You can choose to write the XML into an XML column in the later version database directly.</span></span>  
  
## <a name="bulk-loading-xml-data"></a><span data-ttu-id="34b57-112">大量載入 XML 資料</span><span class="sxs-lookup"><span data-stu-id="34b57-112">Bulk loading XML data</span></span>  
 <span data-ttu-id="34b57-113">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的大量載入功能 (例如 bcp) 來將 XML 資料大量載入伺服器中。</span><span class="sxs-lookup"><span data-stu-id="34b57-113">You can bulk load XML data into the server by using the bulk loading capabilities of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as bcp.</span></span> <span data-ttu-id="34b57-114">OPENROWSET 可讓您將資料從檔案載入至 XML 資料行中。</span><span class="sxs-lookup"><span data-stu-id="34b57-114">OPENROWSET allows you to load data into an XML column from files.</span></span> <span data-ttu-id="34b57-115">下列範例將說明這一點。</span><span class="sxs-lookup"><span data-stu-id="34b57-115">The following example illustrates this point.</span></span>  
  
##### <a name="example-loading-xml-from-files"></a><span data-ttu-id="34b57-116">範例：從檔案載入 XML</span><span class="sxs-lookup"><span data-stu-id="34b57-116">Example: Loading XML from Files</span></span>  
 <span data-ttu-id="34b57-117">此範例顯示如何在資料表 T 中插入資料列。XML 資料行的值從檔案 C:\MyFile\xmlfile.xml 載入成 CLOB，並且在整數資料行中提供值 10。</span><span class="sxs-lookup"><span data-stu-id="34b57-117">This example shows how to insert a row in table T. The value of the XML column is loaded from file C:\MyFile\xmlfile.xml as CLOB, and the integer column is supplied the value 10.</span></span>  
  
```  
INSERT INTO T  
SELECT 10, xCol  
FROM    (SELECT *      
    FROM OPENROWSET (BULK 'C:\MyFile\xmlfile.xml', SINGLE_CLOB)   
 AS xCol) AS R(xCol)  
```  
  
## <a name="text-encoding"></a><span data-ttu-id="34b57-118">文字編碼方式</span><span class="sxs-lookup"><span data-stu-id="34b57-118">Text Encoding</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="34b57-119">以 Unicode (UTF-16) 來儲存 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="34b57-119">stores XML data in Unicode (UTF-16).</span></span> <span data-ttu-id="34b57-120">從伺服器擷取出來的 XML 資料會成為 UTF-16 編碼。</span><span class="sxs-lookup"><span data-stu-id="34b57-120">XML data retrieved from the server comes out in UTF-16 encoding.</span></span> <span data-ttu-id="34b57-121">如果您要使用不同的編碼，則必須對所擷取的資料執行必要的轉碼作業。</span><span class="sxs-lookup"><span data-stu-id="34b57-121">If you want a different encoding, you have to perform the required conversion on the retrieved data.</span></span> <span data-ttu-id="34b57-122">有時 XML 資料可能會使用不同的編碼。</span><span class="sxs-lookup"><span data-stu-id="34b57-122">Sometimes, the XML data may be in a different encoding.</span></span> <span data-ttu-id="34b57-123">若有這種情形，您在載入資料時要特別小心。</span><span class="sxs-lookup"><span data-stu-id="34b57-123">If it is, you have to use care during data loading.</span></span> <span data-ttu-id="34b57-124">例如：</span><span class="sxs-lookup"><span data-stu-id="34b57-124">For example:</span></span>  
  
-   <span data-ttu-id="34b57-125">如果您的文字 XML 是 Unicode (UCS-2、UTF-16) 編碼，則可將它指派至 XML 資料行、變數或參數，都不會有任何問題。</span><span class="sxs-lookup"><span data-stu-id="34b57-125">If your text XML is in Unicode (UCS-2, UTF-16), you can assign it to an XML column, variable, or parameter  without any problems.</span></span>  
  
-   <span data-ttu-id="34b57-126">如果因為來源字碼頁的關係，編碼不是 Unicode 而且是隱含的，則資料庫中的字串字碼頁應與您要載入的字碼指標相同或相容。</span><span class="sxs-lookup"><span data-stu-id="34b57-126">If the encoding is not Unicode and is implicit, because of the source code page, the string code page in the database should be the same as or compatible with the code points that you want to load.</span></span> <span data-ttu-id="34b57-127">若有必要，請使用 COLLATE。</span><span class="sxs-lookup"><span data-stu-id="34b57-127">If required, use COLLATE.</span></span> <span data-ttu-id="34b57-128">如果沒有這類的伺服器字碼頁存在，則必須加入含有正確編碼的明確 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="34b57-128">If no such server code page exists, you have to add an explicit XML declaration with the correct encoding.</span></span>  
  
-   <span data-ttu-id="34b57-129">若要使用明確的編碼，請使用 `varbinary()` 類型 (與字碼頁沒有互動) 或使用適當字碼頁的字串類型。</span><span class="sxs-lookup"><span data-stu-id="34b57-129">To use an explicit encoding, use either the `varbinary()` type, which has no interaction with code pages, or use a string type of the appropriate code page.</span></span> <span data-ttu-id="34b57-130">然後再將資料指派給 XML 資料行、變數或參數。</span><span class="sxs-lookup"><span data-stu-id="34b57-130">Then, assign the data to an XML column, variable, or parameter.</span></span>  
  
### <a name="example-explicitly-specifying-an-encoding"></a><span data-ttu-id="34b57-131">範例：明確地指定編碼方式</span><span class="sxs-lookup"><span data-stu-id="34b57-131">Example: Explicitly Specifying an Encoding</span></span>  
 <span data-ttu-id="34b57-132">假設您將 XML 文件 vcdoc 儲存成沒有明確 XML 宣告的 `varchar(max)`。</span><span class="sxs-lookup"><span data-stu-id="34b57-132">Assume that you have an XML document, vcdoc, stored as `varchar(max)` that does not have an explicit XML declaration.</span></span> <span data-ttu-id="34b57-133">下列陳述式會加入具有編碼 "iso8859-1" 的 XML 宣告、串連 XML 文件、將結果轉換成 `varbinary(max)`，位元組表示法因而保存下來，最後再轉換成 XML。</span><span class="sxs-lookup"><span data-stu-id="34b57-133">The following statement adds an XML declaration with the encoding "iso8859-1", concatenates the XML document, casts the result to `varbinary(max)` so that the byte representation is preserved, and then finally casts it to XML.</span></span> <span data-ttu-id="34b57-134">這樣可以讓 XML 處理器依據所指定的編碼 "iso8859-1" 來剖析資料，並針對字串值來產生對應的 UTF-16 表示法。</span><span class="sxs-lookup"><span data-stu-id="34b57-134">This enables the XML processor to parse the data according to the specified encoding "iso8859-1" and generate the corresponding UTF-16 representation for string values.</span></span>  
  
```  
SELECT CAST(   
CAST (('<?xml version="1.0" encoding="iso8859-1"?>'+ vcdoc) AS VARBINARY (MAX))   
 AS XML)  
```  
  
### <a name="string-encoding-incompatibilities"></a><span data-ttu-id="34b57-135">字串編碼不相容</span><span class="sxs-lookup"><span data-stu-id="34b57-135">String Encoding Incompatibilities</span></span>  
 <span data-ttu-id="34b57-136">若您將 XML 複製並以字串常值形式貼到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)][查詢編輯器] 視窗中，就可能會造成 [N]VARCHAR 字串編碼不相容。</span><span class="sxs-lookup"><span data-stu-id="34b57-136">If you copy and paste XML as a string literal into the Query Editor window in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you might experience [N]VARCHAR string encoding incompatibilities.</span></span> <span data-ttu-id="34b57-137">這取決於 XML 執行個體的編碼而定。</span><span class="sxs-lookup"><span data-stu-id="34b57-137">This will depend on the encoding of your XML instance.</span></span> <span data-ttu-id="34b57-138">在許多情況下，您可能會想要移除 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="34b57-138">In many cases, you may want to remove the XML declaration.</span></span> <span data-ttu-id="34b57-139">例如：</span><span class="sxs-lookup"><span data-stu-id="34b57-139">For example:</span></span>  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
  <xsd:schema ...  
```  
  
 <span data-ttu-id="34b57-140">接著您應該加入 N，使 XML 執行個體成為 Unicode 執行個體。</span><span class="sxs-lookup"><span data-stu-id="34b57-140">You should then include an N to make the XML instance an instance of Unicode.</span></span> <span data-ttu-id="34b57-141">例如：</span><span class="sxs-lookup"><span data-stu-id="34b57-141">For example:</span></span>  
  
```  
-- Assign XML instance to a variable.  
DECLARE @X XML  
SET @X = N'...'  
-- Insert XML instance into an xml type column.  
INSERT INTO T VALUES (N'...')  
-- Create an XML schema collection  
CREATE XML SCHEMA COLLECTION XMLCOLL1 AS N'<xsd:schema ... '  
```  
  
## <a name="see-also"></a><span data-ttu-id="34b57-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34b57-142">See Also</span></span>  
 [<span data-ttu-id="34b57-143">XML 資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="34b57-143">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
