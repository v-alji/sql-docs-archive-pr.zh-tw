---
title: 大量匯入與匯出 XML 文件的範例 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- field terminators [SQL Server]
- bulk importing [SQL Server], data formats
- row terminators [SQL Server]
- OPENROWSET function, XML bulk load
- terminators [SQL Server]
- bulk exporting [SQL Server], data formats
- XML bulk load [SQL Server]
ms.assetid: dff99404-a002-48ee-910e-f37f013d946d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d72c84a7ed84503e0c88d2a46c808196903900b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598392"
---
# <a name="examples-of-bulk-import-and-export-of-xml-documents-sql-server"></a><span data-ttu-id="71c06-102">大量匯入與匯出 XML 文件的範例 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="71c06-102">Examples of Bulk Import and Export of XML Documents (SQL Server)</span></span>
    
##  <a name="you-can-bulk-import-xml-documents-into-a-ssnoversion-database-or-bulk-export-them-from-a-ssnoversion-database-this-topic-provides-examples-of-both"></a><a name="top"></a><span data-ttu-id="71c06-103">您可以將 XML 檔大量匯入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫，或從資料庫大量匯出它們 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="71c06-103">You can bulk import XML documents into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database or bulk export them from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="71c06-104">本主題將提供這兩種情況的範例。</span><span class="sxs-lookup"><span data-stu-id="71c06-104">This topic provides examples of both.</span></span>  
  
 <span data-ttu-id="71c06-105">若要從資料檔將資料大量匯入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表或非資料分割檢視，您可以使用下列方式：</span><span class="sxs-lookup"><span data-stu-id="71c06-105">To bulk import data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or non-partitioned view, you can use the following:</span></span>  
  
-   <span data-ttu-id="71c06-106">**bcp** 公用程式</span><span class="sxs-lookup"><span data-stu-id="71c06-106">**bcp** utility</span></span>  
  
     <span data-ttu-id="71c06-107">您也可以使用 **bcp** 公用程式，從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中能執行 SELECT 陳述式的任意位置 (包括資料分割檢視) 匯出資料。</span><span class="sxs-lookup"><span data-stu-id="71c06-107">You can also use the **bcp** utility to export data from anywhere in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that a SELECT statement works, including partitioned views.</span></span>  
  
-   <span data-ttu-id="71c06-108">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="71c06-108">BULK INSERT</span></span>  
  
-   <span data-ttu-id="71c06-109">INSERT ...SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="71c06-109">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>  
  
 <span data-ttu-id="71c06-110">如需詳細資訊，請參閱[使用 Bcp 公用程式匯入和匯出大量資料 &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)並[使用 BULK INSERT 或 OPENROWSET&#40;bulk ... &#41; &#40;SQL Server&#41;來匯入大量資料](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="71c06-110">For more information, see [Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md) and [Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="71c06-111">範例</span><span class="sxs-lookup"><span data-stu-id="71c06-111">Examples</span></span>  
 <span data-ttu-id="71c06-112">此範例如下：</span><span class="sxs-lookup"><span data-stu-id="71c06-112">The examples are the following:</span></span>  
  
-   <span data-ttu-id="71c06-113">A.</span><span class="sxs-lookup"><span data-stu-id="71c06-113">A.</span></span> [<span data-ttu-id="71c06-114">以二進位位元組資料流程大量匯入 XML 資料</span><span class="sxs-lookup"><span data-stu-id="71c06-114">BULK importing XML data as a binary byte stream</span></span>](#binary_byte_stream)  
  
-   <span data-ttu-id="71c06-115">B.</span><span class="sxs-lookup"><span data-stu-id="71c06-115">B.</span></span> [<span data-ttu-id="71c06-116">在現有資料列中大量匯入 XML 資料</span><span class="sxs-lookup"><span data-stu-id="71c06-116">Bulk importing XML data in an existing row</span></span>](#existing_row)  
  
-   <span data-ttu-id="71c06-117">C.</span><span class="sxs-lookup"><span data-stu-id="71c06-117">C.</span></span> [<span data-ttu-id="71c06-118">從包含 DTD 的檔案大量匯入 XML 資料</span><span class="sxs-lookup"><span data-stu-id="71c06-118">Bulk importing XML data from a file that contains a DTD</span></span>](#file_contains_dtd)  
  
-   <span data-ttu-id="71c06-119">D.</span><span class="sxs-lookup"><span data-stu-id="71c06-119">D.</span></span> [<span data-ttu-id="71c06-120">使用格式檔案明確指定欄位結束字元</span><span class="sxs-lookup"><span data-stu-id="71c06-120">Specifying the field terminator explicitly using a format file</span></span>](#field_terminator_in_format_file)  
  
-   <span data-ttu-id="71c06-121">E.</span><span class="sxs-lookup"><span data-stu-id="71c06-121">E.</span></span> [<span data-ttu-id="71c06-122">大量匯出 XML 資料</span><span class="sxs-lookup"><span data-stu-id="71c06-122">Bulk exporting XML data</span></span>](#bulk_export_xml_data)  
  
###  <a name="a-bulk-importing-xml-data-as-a-binary-byte-stream"></a><a name="binary_byte_stream"></a> <span data-ttu-id="71c06-123">A.</span><span class="sxs-lookup"><span data-stu-id="71c06-123">A.</span></span> <span data-ttu-id="71c06-124">以二進位位元組資料流大量匯入 XML 資料</span><span class="sxs-lookup"><span data-stu-id="71c06-124">Bulk importing XML data as a binary byte stream</span></span>  
 <span data-ttu-id="71c06-125">從包含您要套用的編碼宣告之檔案大量匯入 XML 資料時，請在 OPENROWSET(BULK…) 子句中指定 SINGLE_BLOB 選項。</span><span class="sxs-lookup"><span data-stu-id="71c06-125">When you bulk import XML data from a file that contains an encoding declaration that you want to apply, specify the SINGLE_BLOB option in the OPENROWSET(BULK...) clause.</span></span> <span data-ttu-id="71c06-126">SINGLE_BLOB 選項可確保 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 XML 剖析器，會根據 XML 宣告中指定的編碼配置來匯入資料。</span><span class="sxs-lookup"><span data-stu-id="71c06-126">The SINGLE_BLOB option makes sure that the XML parser in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] imports the data according to the encoding scheme specified in the XML declaration.</span></span>  
  
#### <a name="sample-table"></a><span data-ttu-id="71c06-127">範例資料表</span><span class="sxs-lookup"><span data-stu-id="71c06-127">Sample Table</span></span>  
 <span data-ttu-id="71c06-128">若要測試範例 A，您必須建立範例資料表 `T`。</span><span class="sxs-lookup"><span data-stu-id="71c06-128">To test example A, you must create sample table `T`.</span></span>  
  
```  
USE tempdb  
CREATE TABLE T (IntCol int, XmlCol xml);  
GO  
```  
  
#### <a name="sample-data-file"></a><span data-ttu-id="71c06-129">範例資料檔</span><span class="sxs-lookup"><span data-stu-id="71c06-129">Sample Data File</span></span>  
 <span data-ttu-id="71c06-130">在執行範例 A 之前，您必須先建立 UTF-8 編碼檔 (`C:\SampleFolder\SampleData3.txt`)，其中包含指定 `UTF-8` 編碼配置的下列範例執行個體。</span><span class="sxs-lookup"><span data-stu-id="71c06-130">Before you can run example A, you must create a UTF-8 encoded file (`C:\SampleFolder\SampleData3.txt`) that contains the following sample instance that specifies the `UTF-8` encoding scheme.</span></span>  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<Root>  
          <ProductDescription ProductModelID="5">  
             <Summary>Some Text</Summary>  
          </ProductDescription>  
</Root>  
```  
  
#### <a name="example-a"></a><span data-ttu-id="71c06-131">範例 A</span><span class="sxs-lookup"><span data-stu-id="71c06-131">Example A</span></span>  
 <span data-ttu-id="71c06-132">這個範例在 `SINGLE_BLOB` 陳述式中使用 `INSERT ... SELECT * FROM OPENROWSET(BULK...)` 選項，以從名為 `SampleData3.txt` 的檔案匯入資料，並將 XML 執行個體插入範例資料表 `T`這個單一資料行資料表。</span><span class="sxs-lookup"><span data-stu-id="71c06-132">This example uses the `SINGLE_BLOB` option in an `INSERT ... SELECT * FROM OPENROWSET(BULK...)` statement to import data from a file named `SampleData3.txt` and insert an XML instance in the single-column table, sample table `T`.</span></span>  
  
```  
INSERT INTO T(XmlCol)  
SELECT * FROM OPENROWSET(  
   BULK 'c:\SampleFolder\SampleData3.txt',  
   SINGLE_BLOB) AS x;  
```  
  
#### <a name="remarks"></a><span data-ttu-id="71c06-133">備註</span><span class="sxs-lookup"><span data-stu-id="71c06-133">Remarks</span></span>  
 <span data-ttu-id="71c06-134">以此方式使用 SINGLE_BLOB 時，可以避免 XML 文件編碼 (由 XML 編碼宣告指定) 與伺服器隱含的字串字碼頁不相符。</span><span class="sxs-lookup"><span data-stu-id="71c06-134">By using SINGLE_BLOB in this case, you can avoid a mismatch between the encoding of the XML document (as specified by the XML encoding declaration) and the string codepage implied by the server.</span></span>  
  
 <span data-ttu-id="71c06-135">如果在使用 NCLOB 或 CLOB 時發生字碼頁或編碼衝突，您必須執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="71c06-135">If you use NCLOB or CLOB data types and run into a codepage or encoding conflict, you must do one of the following:</span></span>  
  
-   <span data-ttu-id="71c06-136">移除 XML 宣告以順利匯入 XML 資料檔的內容。</span><span class="sxs-lookup"><span data-stu-id="71c06-136">Remove the XML declaration to successfully import the contents of the XML data file.</span></span>  
  
-   <span data-ttu-id="71c06-137">在查詢的 CODEPAGE 選項指定符合 XML 宣告中使用之編碼配置的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="71c06-137">Specify a code page in the CODEPAGE option of the query that matches the encoding scheme that is used in the XML declaration.</span></span>  
  
-   <span data-ttu-id="71c06-138">比對或解析資料庫定序設定與非 Unicode XML 編碼配置。</span><span class="sxs-lookup"><span data-stu-id="71c06-138">Match, or resolve, the database collation settings with a non-Unicode XML encoding scheme.</span></span>  
  
 <span data-ttu-id="71c06-139">[[頁首]](#top)</span><span class="sxs-lookup"><span data-stu-id="71c06-139">[&#91;Top&#93;](#top)</span></span>  
  
###  <a name="b-bulk-importing-xml-data-in-an-existing-row"></a><a name="existing_row"></a> <span data-ttu-id="71c06-140">B.</span><span class="sxs-lookup"><span data-stu-id="71c06-140">B.</span></span> <span data-ttu-id="71c06-141">在現有資料列中大量匯入 XML 資料</span><span class="sxs-lookup"><span data-stu-id="71c06-141">Bulk importing XML data in an existing row</span></span>  
 <span data-ttu-id="71c06-142">這個範例使用 `OPENROWSET` 大量資料列集提供者，將 XML 執行個體加入範例資料表 `T`中的現有資料列。</span><span class="sxs-lookup"><span data-stu-id="71c06-142">This example uses the `OPENROWSET` bulk rowset provider to add an XML instance to an existing row or rows in sample table `T`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71c06-143">若要執行這個範例，首先必須完成範例 A 提供的測試指令碼。該範例會建立 `tempdb.dbo.T` 資料表，並從 `SampleData3.txt`大量匯入資料。</span><span class="sxs-lookup"><span data-stu-id="71c06-143">To run this example, you must first complete the test script provided in example A. That example creates the `tempdb.dbo.T` table and bulk imports data from `SampleData3.txt`.</span></span>  
  
#### <a name="sample-data-file"></a><span data-ttu-id="71c06-144">範例資料檔</span><span class="sxs-lookup"><span data-stu-id="71c06-144">Sample Data File</span></span>  
 <span data-ttu-id="71c06-145">範例 B 使用前面範例中的 `SampleData3.txt` 範例資料檔的修改版本。</span><span class="sxs-lookup"><span data-stu-id="71c06-145">Example B uses a modified version of the `SampleData3.txt` sample data file from the preceding example.</span></span> <span data-ttu-id="71c06-146">若要執行此範例，請將此檔案的內容修改如下：</span><span class="sxs-lookup"><span data-stu-id="71c06-146">To run this example, modify the content of this file as follows:</span></span>  
  
```  
<Root>  
          <ProductDescription ProductModelID="10">  
             <Summary>Some New Text</Summary>  
          </ProductDescription>  
</Root>  
```  
  
#### <a name="example-b"></a><span data-ttu-id="71c06-147">範例 B</span><span class="sxs-lookup"><span data-stu-id="71c06-147">Example B</span></span>  
  
```  
-- Query before update shows initial state of XmlCol values.  
SELECT * FROM T  
UPDATE T  
SET XmlCol =(  
SELECT * FROM OPENROWSET(  
   BULK 'C:\SampleFolder\SampleData3.txt',  
           SINGLE_BLOB  
) AS x  
)  
WHERE IntCol = 1;  
GO  
```  
  
 <span data-ttu-id="71c06-148">[[頁首]](#top)</span><span class="sxs-lookup"><span data-stu-id="71c06-148">[&#91;Top&#93;](#top)</span></span>  
  
###  <a name="c-bulk-importing-xml-data-from-a-file-that-contains-a-dtd"></a><a name="file_contains_dtd"></a> <span data-ttu-id="71c06-149">C.</span><span class="sxs-lookup"><span data-stu-id="71c06-149">C.</span></span> <span data-ttu-id="71c06-150">從包含 DTD 的檔案大量匯入 XML 資料</span><span class="sxs-lookup"><span data-stu-id="71c06-150">Bulk importing XML data from a file that contains a DTD</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="71c06-151">如果您的 XML 環境不需要文件類型定義 (DTD)，我們建議您不要啟用這項支援。</span><span class="sxs-lookup"><span data-stu-id="71c06-151">We recommended that you not enable support for Document Type Definitions (DTDs) if it is not required in your XML environment.</span></span> <span data-ttu-id="71c06-152">開啟 DTD 支援會增加您伺服器受攻擊的介面區，以及將它暴露於阻絕服務攻擊的危險。</span><span class="sxs-lookup"><span data-stu-id="71c06-152">Turning on DTD support increases the attackable surface area of your server, and may expose it to a denial-of-service attack.</span></span> <span data-ttu-id="71c06-153">如果您必須啟用 DTD 支援，可以藉由只處理信任的 XML 文件來減輕此安全性風險。</span><span class="sxs-lookup"><span data-stu-id="71c06-153">If you must enable DTD support, you can reduce this security risk by processing only trusted XML documents.</span></span>  
  
 <span data-ttu-id="71c06-154">在嘗試使用 [bcp](../../tools/bcp-utility.md) 命令，從包含 DTD 的檔案匯入 XML 資料期間，可能會發生類似下列的錯誤：</span><span class="sxs-lookup"><span data-stu-id="71c06-154">During an attempt to use a [bcp](../../tools/bcp-utility.md) command to import XML data from a file that contains a DTD, an error similar to the following can occur:</span></span>  
  
 <span data-ttu-id="71c06-155">「SQLState = 42000、NativeError = 6359」</span><span class="sxs-lookup"><span data-stu-id="71c06-155">"SQLState = 42000, NativeError = 6359"</span></span>  
  
 <span data-ttu-id="71c06-156">「錯誤 = [Microsoft][SQL Server Native Client][ SQL Server]不允許以內部子集 DTD 剖析 XML。</span><span class="sxs-lookup"><span data-stu-id="71c06-156">"Error = [Microsoft][SQL Server Native Client][ SQL Server]Parsing XML with internal subset DTDs not allowed.</span></span> <span data-ttu-id="71c06-157">請使用 CONVERT 配合樣式選項 2，啟用有限的內部子集 DTD 支援。」</span><span class="sxs-lookup"><span data-stu-id="71c06-157">Use CONVERT with style option 2 to enable limited internal subset DTD support."</span></span>  
  
 <span data-ttu-id="71c06-158">「BCP 複製 %s 失敗」</span><span class="sxs-lookup"><span data-stu-id="71c06-158">"BCP copy %s failed"</span></span>  
  
 <span data-ttu-id="71c06-159">若要解決這個問題，您可以從包含 DTD 的資料檔匯入 XML 資料，方法是使用 `OPENROWSET(BULK...)` 函數，然後在命令的 `CONVERT` 子句中指定 `SELECT` 選項。</span><span class="sxs-lookup"><span data-stu-id="71c06-159">To work around this problem, you can import XML data from a data file that contains a DTD by using the `OPENROWSET(BULK...)` function and then specifying the `CONVERT` option in the `SELECT` clause of the command.</span></span> <span data-ttu-id="71c06-160">此命令的基本語法如下：</span><span class="sxs-lookup"><span data-stu-id="71c06-160">The basic syntax for the command is:</span></span>  
  
 `INSERT ... SELECT CONVERT(...) FROM OPENROWSET(BULK...)`  
  
#### <a name="sample-data-file"></a><span data-ttu-id="71c06-161">範例資料檔</span><span class="sxs-lookup"><span data-stu-id="71c06-161">Sample Data File</span></span>  
 <span data-ttu-id="71c06-162">在測試這個大量匯入範例之前，請建立包含下列範例執行個體的檔案 (`C:\temp\Dtdfile.xml`)：</span><span class="sxs-lookup"><span data-stu-id="71c06-162">Before you can test this bulk import example, create a file (`C:\temp\Dtdfile.xml`) that contains the following sample instance:</span></span>  
  
```  
<!DOCTYPE DOC [<!ATTLIST elem1 attr1 CDATA "defVal1">]><elem1>January</elem1>  
```  
  
#### <a name="sample-table"></a><span data-ttu-id="71c06-163">範例資料表</span><span class="sxs-lookup"><span data-stu-id="71c06-163">Sample Table</span></span>  
 <span data-ttu-id="71c06-164">範例 C 使用由下列 `T1` 陳述式所建立的 `CREATE TABLE` 範例資料表：</span><span class="sxs-lookup"><span data-stu-id="71c06-164">Example C uses the `T1` sample table that is created by the following `CREATE TABLE` statement:</span></span>  
  
```  
USE tempdb;  
CREATE TABLE T1(XmlCol xml);  
GO  
```  
  
#### <a name="example-c"></a><span data-ttu-id="71c06-165">範例 C</span><span class="sxs-lookup"><span data-stu-id="71c06-165">Example C</span></span>  
 <span data-ttu-id="71c06-166">這個範例使用 `OPENROWSET(BULK...)` ，並在 `CONVERT` 子句中指定 `SELECT` 選項，將 XML 資料從 `Dtdfile.xml` 匯入範例資料表 `T1`。</span><span class="sxs-lookup"><span data-stu-id="71c06-166">This example uses `OPENROWSET(BULK...)` and specifies the `CONVERT` option in the `SELECT` clause to import the XML data from `Dtdfile.xml` into sample table `T1`.</span></span>  
  
```  
INSERT T1  
  SELECT CONVERT(xml, BulkColumn, 2) FROM   
    OPENROWSET(Bulk 'c:\temp\Dtdfile.xml', SINGLE_BLOB) [rowsetresults];  
```  
  
 <span data-ttu-id="71c06-167">在執行 `INSERT` 陳述式之後，會從 XML 移除 DTD，並將它儲存在 `T1` 資料表中。</span><span class="sxs-lookup"><span data-stu-id="71c06-167">After the `INSERT` statement executes, the DTD is stripped from the XML and stored in the `T1` table.</span></span>  
  
 <span data-ttu-id="71c06-168">[[頁首]](#top)</span><span class="sxs-lookup"><span data-stu-id="71c06-168">[&#91;Top&#93;](#top)</span></span>  
  
###  <a name="d-specifying-the-field-terminator-explicitly-using-a-format-file"></a><a name="field_terminator_in_format_file"></a> <span data-ttu-id="71c06-169">D.</span><span class="sxs-lookup"><span data-stu-id="71c06-169">D.</span></span> <span data-ttu-id="71c06-170">使用格式檔案明確指定欄位結束字元</span><span class="sxs-lookup"><span data-stu-id="71c06-170">Specifying the field terminator explicitly using a format file</span></span>  
 <span data-ttu-id="71c06-171">下列範例顯示如何大量匯入下列 XML 文件 `Xmltable.dat`。</span><span class="sxs-lookup"><span data-stu-id="71c06-171">The following example shows how to bulk import the following XML document, `Xmltable.dat`.</span></span>  
  
#### <a name="sample-data-file"></a><span data-ttu-id="71c06-172">範例資料檔</span><span class="sxs-lookup"><span data-stu-id="71c06-172">Sample Data File</span></span>  
 <span data-ttu-id="71c06-173">`Xmltable.dat` 中的文件包含兩個 XML 值，每列各有一個值。</span><span class="sxs-lookup"><span data-stu-id="71c06-173">The document in `Xmltable.dat` contains two XML values, one for each row.</span></span> <span data-ttu-id="71c06-174">第一個 XML 值是以 UTF-16 編碼，而第二個值則是以 UTF-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="71c06-174">The first XML value is encoded with UTF-16, and the second value is encoded with UTF-8.</span></span>  
  
 <span data-ttu-id="71c06-175">這個資料檔的內容顯示在下列十六進位傾印中：</span><span class="sxs-lookup"><span data-stu-id="71c06-175">The contents of this data file are shown in the following Hex dump:</span></span>  
  
```  
FF FE 3C 00 3F 00 78 00-6D 00 6C 00 20 00 76 00  *..<.?.x.m.l. .v.*  
65 00 72 00 73 00 69 00-6F 00 6E 00 3D 00 22 00  *e.r.s.i.o.n.=.".*  
31 00 2E 00 30 00 22 00-20 00 65 00 6E 00 63 00  *1...0.". .e.n.c.*  
6F 00 64 00 69 00 6E 00-67 00 3D 00 22 00 75 00  *o.d.i.n.g.=.".u.*  
74 00 66 00 2D 00 31 00-36 00 22 00 3F 00 3E 00  *t.f.-.1.6.".?.>.*  
3C 00 72 00 6F 00 6F 00-74 00 3E 00 A2 4F 9C 76  *<.r.o.o.t.>..O.v*  
0C FA 77 E4 80 00 89 00-00 06 90 06 91 2E 9B 2E  *..w.............*  
99 34 A2 34 86 00 83 02-92 20 7F 02 4E C5 E4 A3  *.4.4..... ..N...*  
34 B2 B7 B3 B7 FE F8 FF-F8 00 3C 00 2F 00 72 00  *4.........<./.r.*  
6F 00 6F 00 74 00 3E 00-00 00 00 00 7A EF BB BF  *o.o.t.>.....z...*  
3C 3F 78 6D 6C 20 76 65-72 73 69 6F 6E 3D 22 31  *<?xml version="1*  
2E 30 22 20 65 6E 63 6F-64 69 6E 67 3D 22 75 74  *.0" encoding="ut*  
66 2D 38 22 3F 3E 3C 72-6F 6F 74 3E E4 BE A2 E7  *f-8"?><root>....*  
9A 9C EF A8 8C EE 91 B7-C2 80 C2 89 D8 80 DA 90  *................*  
E2 BA 91 E2 BA 9B E3 92-99 E3 92 A2 C2 86 CA 83  *................*  
E2 82 92 C9 BF EC 95 8E-EA 8F A4 EB 88 B4 EB 8E  *................*  
B7 EF BA B7 EF BF B8 C3-B8 3C 2F 72 6F 6F 74 3E  *.........</root>*  
00 00 00 00 7A                                   *....z*  
```  
  
#### <a name="sample-table"></a><span data-ttu-id="71c06-176">範例資料表</span><span class="sxs-lookup"><span data-stu-id="71c06-176">Sample Table</span></span>  
 <span data-ttu-id="71c06-177">當大量匯入或匯出 XML 文件時，您應該使用任何文件都無法顯示的 [欄位結束字元](specify-field-and-row-terminators-sql-server.md) ；例如，連續四個 Null (`\0`) 後面接著字母 `z`： `\0\0\0\0z`。</span><span class="sxs-lookup"><span data-stu-id="71c06-177">When you bulk import or export an XML document, you should use a [field terminator](specify-field-and-row-terminators-sql-server.md) that cannot possibly appear in any of the documents; for example, a series of four nulls (`\0`) followed by the letter `z`: `\0\0\0\0z`.</span></span>  
  
 <span data-ttu-id="71c06-178">這個範例顯示如何將這個欄位結束字元使用於 `xTable` 範例資料表。</span><span class="sxs-lookup"><span data-stu-id="71c06-178">This example shows how to use this field terminator for the `xTable` sample table.</span></span> <span data-ttu-id="71c06-179">若要建立這個範例資料表，請使用下列 `CREATE TABLE` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="71c06-179">To create this sample table, use the following `CREATE TABLE` statement:</span></span>  
  
```  
USE tempdb;  
CREATE TABLE xTable (xCol xml);  
GO  
```  
  
#### <a name="sample-format-file"></a><span data-ttu-id="71c06-180">範例格式檔案</span><span class="sxs-lookup"><span data-stu-id="71c06-180">Sample Format File</span></span>  
 <span data-ttu-id="71c06-181">在格式檔案中必須指定欄位結束字元。</span><span class="sxs-lookup"><span data-stu-id="71c06-181">The field terminator must be specified in the format file.</span></span> <span data-ttu-id="71c06-182">範例 D 使用名為 `Xmltable.fmt` 的非 XML 格式檔案，其中包含下列內容：</span><span class="sxs-lookup"><span data-stu-id="71c06-182">Example D uses a non-XML format file named `Xmltable.fmt` that contains the following:</span></span>  
  
```  
9.0  
1  
1       SQLBINARY     0       0       "\0\0\0\0z"    1     xCol         ""  
```  
  
 <span data-ttu-id="71c06-183">您可以使用這個格式檔案，將 XML 文件大量匯入 `xTable` 資料表，方法是使用 `bcp` 命令或 `BULK INSERT` 或 `INSERT ... SELECT * FROM OPENROWSET(BULK...)` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="71c06-183">You can use this format file to bulk import XML documents into the `xTable` table by using a `bcp` command or a `BULK INSERT` or `INSERT ... SELECT * FROM OPENROWSET(BULK...)` statement.</span></span>  
  
#### <a name="example-d"></a><span data-ttu-id="71c06-184">範例 D</span><span class="sxs-lookup"><span data-stu-id="71c06-184">Example D</span></span>  
 <span data-ttu-id="71c06-185">這個範例在 `Xmltable.fmt` 陳述式中使用 `BULK INSERT` 格式檔案，以匯入名為 `Xmltable.dat`之 XML 資料檔的內容。</span><span class="sxs-lookup"><span data-stu-id="71c06-185">This example uses the `Xmltable.fmt` format file in a `BULK INSERT` statement to import the contents of an XML data file named `Xmltable.dat`.</span></span>  
  
```  
BULK INSERT xTable   
FROM 'C:\Xmltable.dat'  
WITH (FORMATFILE = 'C:\Xmltable.fmt');  
GO  
```  
  
 <span data-ttu-id="71c06-186">[[頁首]](#top)</span><span class="sxs-lookup"><span data-stu-id="71c06-186">[&#91;Top&#93;](#top)</span></span>  
  
###  <a name="e-bulk-exporting-xml-data"></a><a name="bulk_export_xml_data"></a> <span data-ttu-id="71c06-187">E.</span><span class="sxs-lookup"><span data-stu-id="71c06-187">E.</span></span> <span data-ttu-id="71c06-188">大量匯出 XML 資料</span><span class="sxs-lookup"><span data-stu-id="71c06-188">Bulk exporting XML data</span></span>  
 <span data-ttu-id="71c06-189">下列範例使用 `bcp` 從前面範例所建立的資料表 (使用相同的 XML 格式檔案) 大量匯入 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="71c06-189">The following example uses `bcp` to bulk export XML data from the table that is created in the preceding example by using the same XML format file.</span></span> <span data-ttu-id="71c06-190">在下列 `bcp` 命令中， `<server_name>` 和 `<instance_name>` 代表必須以適當值取代的預留位置：</span><span class="sxs-lookup"><span data-stu-id="71c06-190">In the following `bcp` command, `<server_name>` and `<instance_name>` represent placeholders that must be replaced with appropriate values:</span></span>  
  
```  
bcp bulktest..xTable out a-wn.out -N -T -S<server_name>\<instance_name>  
```  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="71c06-191">當 XML 資料保存於資料庫時，並不會儲存 XML 編碼。</span><span class="sxs-lookup"><span data-stu-id="71c06-191">does not save the XML encoding when XML data is persisted in the database.</span></span> <span data-ttu-id="71c06-192">因此，一旦匯出 XML 資料之後，便無法使用 XML 欄位的原始編碼。</span><span class="sxs-lookup"><span data-stu-id="71c06-192">Therefore, the original encoding of XML fields is not available when XML data is exported.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="71c06-193">會在匯出 XML 資料時使用 UTF-16 編碼。</span><span class="sxs-lookup"><span data-stu-id="71c06-193">uses UTF-16 encoding when exporting XML data.</span></span>  
  
 <span data-ttu-id="71c06-194">[[頁首]](#top)</span><span class="sxs-lookup"><span data-stu-id="71c06-194">[&#91;Top&#93;](#top)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71c06-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71c06-195">See Also</span></span>  
 <span data-ttu-id="71c06-196">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="71c06-196">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 <span data-ttu-id="71c06-197">[SELECT 子句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="71c06-197">[SELECT Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) </span></span>  
 <span data-ttu-id="71c06-198">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="71c06-198">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="71c06-199">[資料的大量匯入及匯出 &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="71c06-199">[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span></span>  
 <span data-ttu-id="71c06-200">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="71c06-200">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 [<span data-ttu-id="71c06-201">OPENROWSET &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="71c06-201">OPENROWSET &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
