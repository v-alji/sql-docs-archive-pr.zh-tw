---
title: 使用格式檔案大量匯入資料 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], format files
- format files [SQL Server], importing data using
ms.assetid: 2956df78-833f-45fa-8a10-41d6522562b9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c6d9779209b3ffb317658243c168d74740f6731b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607400"
---
# <a name="use-a-format-file-to-bulk-import-data-sql-server"></a><span data-ttu-id="938e4-102">使用格式檔案大量匯入資料 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="938e4-102">Use a Format File to Bulk Import Data (SQL Server)</span></span>
  <span data-ttu-id="938e4-103">此主題說明格式檔案在大量匯入作業中的用法。</span><span class="sxs-lookup"><span data-stu-id="938e4-103">This topic illustrates the use of a format file in bulk-import operations.</span></span> <span data-ttu-id="938e4-104">格式檔案會將資料檔案的欄位對應到資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="938e4-104">The format file maps the fields of the data file to the columns of the table.</span></span>  <span data-ttu-id="938e4-105">使用**bcp**命令或 BULK INSERT 或 INSERT ... 時，您可以使用非 XML 或 xml 格式檔案來大量匯入資料SELECT \* FROM OPENROWSET (BULK ... ) [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令。</span><span class="sxs-lookup"><span data-stu-id="938e4-105">You can use a non-XML or XML format file to bulk import data when using a **bcp** command or a BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...) [!INCLUDE[tsql](../../includes/tsql-md.md)] command.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="938e4-106">如果格式檔案要與 Unicode 字元資料檔案搭配使用，則所有的輸入欄位都必須是 Unicode 文字字串 (也就是固定大小或以字元結束的 Unicode 字串)。</span><span class="sxs-lookup"><span data-stu-id="938e4-106">For a format file to work with a Unicode character data file, all the input fields must be Unicode text strings (that is, either fixed-size or character-terminated Unicode strings).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="938e4-107">如果您不熟悉格式檔案，請參閱[非 XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md)和[xml 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="938e4-107">If you are unfamiliar with format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) and [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
## <a name="format-file-options-for-bulk-import-commands"></a><span data-ttu-id="938e4-108">大量匯入命令的格式檔案選項</span><span class="sxs-lookup"><span data-stu-id="938e4-108">Format File Options for Bulk-Import Commands</span></span>  
 <span data-ttu-id="938e4-109">下表摘述每個大量匯入命令的格式檔案選項。</span><span class="sxs-lookup"><span data-stu-id="938e4-109">The following table summarizes the format-file option of for each of the bulk-import commands.</span></span>  
  
|<span data-ttu-id="938e4-110">大量載入命令</span><span class="sxs-lookup"><span data-stu-id="938e4-110">Bulk-load Command</span></span>|<span data-ttu-id="938e4-111">使用格式檔案選項</span><span class="sxs-lookup"><span data-stu-id="938e4-111">Using the Format-File Option</span></span>|  
|------------------------|-----------------------------------|  
|<span data-ttu-id="938e4-112">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="938e4-112">BULK INSERT</span></span>|<span data-ttu-id="938e4-113">FORMATFILE = '*format_file_path*'</span><span class="sxs-lookup"><span data-stu-id="938e4-113">FORMATFILE = '*format_file_path*'</span></span>|  
|<span data-ttu-id="938e4-114">INSERT ...SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="938e4-114">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>|<span data-ttu-id="938e4-115">FORMATFILE = '*format_file_path*'</span><span class="sxs-lookup"><span data-stu-id="938e4-115">FORMATFILE = '*format_file_path*'</span></span>|  
|<span data-ttu-id="938e4-116">**bcp** .。。**中的**</span><span class="sxs-lookup"><span data-stu-id="938e4-116">**bcp** ... **in**</span></span>|<span data-ttu-id="938e4-117">**-f** *format_file*</span><span class="sxs-lookup"><span data-stu-id="938e4-117">**-f** *format_file*</span></span>|  
  
 <span data-ttu-id="938e4-118">如需詳細資訊，請參閱 [bcp 公用程式](../../tools/bcp-utility.md)、[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) 或 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="938e4-118">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), or [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="938e4-119">若要大量匯出或匯入 SQLXML 資料，請在格式檔案中使用下列其中一種資料類型：SQLCHAR 或 SQLVARYCHAR (資料會以用戶端字碼頁或定序所隱含的字碼頁傳送)、SQLNCHAR 或 SQLNVARCHAR (資料會以 Unicode 傳送)，或是 SQLBINARY 或 SQLVARYBIN (資料不經轉換即傳送)。</span><span class="sxs-lookup"><span data-stu-id="938e4-119">To bulk export or import SQLXML data, use one of the following data types in your format file: SQLCHAR or SQLVARYCHAR (the data is sent in the client code page or in the code page implied by the collation), SQLNCHAR or SQLNVARCHAR (the data is sent as Unicode), or SQLBINARY or SQLVARYBIN (the data is sent without any conversion).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="938e4-120">範例</span><span class="sxs-lookup"><span data-stu-id="938e4-120">Examples</span></span>  
 <span data-ttu-id="938e4-121">本節中的範例說明如何使用格式檔案，利用**bcp**命令和 BULK INSERT 來大量匯入資料，然後插入 .。。SELECT \* FROM OPENROWSET (BULK ... ) 語句。</span><span class="sxs-lookup"><span data-stu-id="938e4-121">The examples in this section illustrate how to use format files to bulk-import data by using the **bcp** command and the BULK INSERT, and INSERT ... SELECT \* FROM OPENROWSET(BULK...) statements.</span></span> <span data-ttu-id="938e4-122">執行其中一個大量匯入範例之前，必須先建立範例資料表、資料檔案與格式檔案。</span><span class="sxs-lookup"><span data-stu-id="938e4-122">Before you can run one of the bulk-import examples, you need to create a sample table, data file, and a format file.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="938e4-123">範例資料表</span><span class="sxs-lookup"><span data-stu-id="938e4-123">Sample Table</span></span>  
 <span data-ttu-id="938e4-124">這些範例在 **dbo** 結構描述下的 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 範例資料庫中，需要建立一個名為 **myTestFormatFiles** 的資料表。</span><span class="sxs-lookup"><span data-stu-id="938e4-124">The examples require that a table named **myTestFormatFiles** table be created in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database under the **dbo** schema.</span></span> <span data-ttu-id="938e4-125">若要建立這個資料表，請在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行：</span><span class="sxs-lookup"><span data-stu-id="938e4-125">To create this table, in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestFormatFiles (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50),  
   Col4 nvarchar(50)  
   );  
GO  
```  
  
### <a name="sample-data-file"></a><span data-ttu-id="938e4-126">範例資料檔</span><span class="sxs-lookup"><span data-stu-id="938e4-126">Sample Data File</span></span>  
 <span data-ttu-id="938e4-127">此範例使用範例資料檔案 `myTestFormatFiles-c.Dat`，包含下列記錄。</span><span class="sxs-lookup"><span data-stu-id="938e4-127">The examples use a sample data file, `myTestFormatFiles-c.Dat`, which contains the following records.</span></span> <span data-ttu-id="938e4-128">若要建立資料檔，請在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="938e4-128">To create the data file, at the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
10,Field2,Field3,Field4  
15,Field2,Field3,Field4  
46,Field2,Field3,Field4  
58,Field2,Field3,Field4  
```  
  
### <a name="sample-format-files"></a><span data-ttu-id="938e4-129">範例格式檔案</span><span class="sxs-lookup"><span data-stu-id="938e4-129">Sample Format Files</span></span>  
 <span data-ttu-id="938e4-130">本節中有部分範例會使用 XML 格式檔案 `myTestFormatFiles-f-x-c.Xml`，而其他範例會使用非 XML 格式檔案。</span><span class="sxs-lookup"><span data-stu-id="938e4-130">Some of the examples in this section use an XML format file, `myTestFormatFiles-f-x-c.Xml`, and other examples use a non-XML format file.</span></span> <span data-ttu-id="938e4-131">兩種格式檔案都使用字元資料格式和非預設欄位結束字元 (,)。</span><span class="sxs-lookup"><span data-stu-id="938e4-131">Both format files use character data formats and a non-default field terminator (,).</span></span>  
  
#### <a name="the-sample-non-xml-format-file"></a><span data-ttu-id="938e4-132">非 XML 格式檔案範例</span><span class="sxs-lookup"><span data-stu-id="938e4-132">The Sample Non-XML Format File</span></span>  
 <span data-ttu-id="938e4-133">下列範例會使用 **bcp**，從 `myTestFormatFiles` 資料表產生 XML 格式檔案。</span><span class="sxs-lookup"><span data-stu-id="938e4-133">The following example uses **bcp** to generate an XML format file from the `myTestFormatFiles` table.</span></span> <span data-ttu-id="938e4-134">`myTestFormatFiles.Fmt` 檔案包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="938e4-134">The `myTestFormatFiles.Fmt` file contains the following information:</span></span>  
  
```  
9.0  
4  
1       SQLCHAR       0       7       ","      1     Col1         ""  
2       SQLCHAR       0       100     ","      2     Col2         SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     ","      3     Col3         SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       100     "\r\n"   4     Col4         SQL_Latin1_General_CP1_CI_AS  
```  
  
 <span data-ttu-id="938e4-135">若要使用 **bcp** 搭配 **format** 選項以建立此格式檔案，請在 Windows 命令提示字元中輸入：</span><span class="sxs-lookup"><span data-stu-id="938e4-135">To use **bcp** with the **format** option to create this format file, at the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012..MyTestFormatFiles format nul -c -t, -f myTestFormatFiles.Fmt -T  
  
```  
  
 <span data-ttu-id="938e4-136">如需建立格式檔案的詳細資訊，請參閱[建立格式檔案 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="938e4-136">For more information about creating a format file, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
#### <a name="the-sample-xml-format-file"></a><span data-ttu-id="938e4-137">XML 格式檔案範例</span><span class="sxs-lookup"><span data-stu-id="938e4-137">The Sample XML Format File</span></span>  
 <span data-ttu-id="938e4-138">下列範例使用 **bcp**，從 `myTestFormatFiles` 資料表建立以產生 XML 格式檔案。</span><span class="sxs-lookup"><span data-stu-id="938e4-138">The following example uses **bcp** to create to generate an XML format file from the `myTestFormatFiles` table.</span></span> <span data-ttu-id="938e4-139">`myTestFormatFiles.Xml` 檔案包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="938e4-139">The `myTestFormatFiles.Xml` file contains the following information:</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Col4" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
 <span data-ttu-id="938e4-140">若要使用 **bcp** 搭配 **format** 選項以建立此格式檔案，請在 Windows 命令提示字元中輸入：</span><span class="sxs-lookup"><span data-stu-id="938e4-140">To use **bcp** with the **format** option to create this format file, at the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012..MyTestFormatFiles format nul -c -t, -x -f myTestFormatFiles.Xml -T  
```  
  
### <a name="using-bcp"></a><span data-ttu-id="938e4-141">使用 bcp</span><span class="sxs-lookup"><span data-stu-id="938e4-141">Using bcp</span></span>  
 <span data-ttu-id="938e4-142">下列範例使用 **bcp**，將 `myTestFormatFiles-c.Dat` 資料檔中的資料大量匯入到範例資料庫中的 `HumanResources.myTestFormatFiles` 資料表。</span><span class="sxs-lookup"><span data-stu-id="938e4-142">The following example uses **bcp** to bulk import data from the `myTestFormatFiles-c.Dat` data file into `HumanResources.myTestFormatFiles` table in the  sample database.</span></span> <span data-ttu-id="938e4-143">這個範例使用 XML 格式檔案 `MyTestFormatFiles.Xml`。</span><span class="sxs-lookup"><span data-stu-id="938e4-143">This example uses an XML format file, `MyTestFormatFiles.Xml`.</span></span> <span data-ttu-id="938e4-144">這個範例會在匯入資料檔之前，刪除任何現有的資料表資料列。</span><span class="sxs-lookup"><span data-stu-id="938e4-144">The example deletes any existing table rows before importing the data file.</span></span>  
  
 <span data-ttu-id="938e4-145">請在 Windows 命令提示字元之下，輸入：</span><span class="sxs-lookup"><span data-stu-id="938e4-145">At the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012..myTestFormatFiles in C:\myTestFormatFiles-c.Dat -f C:\myTestFormatFiles.Xml -T  
```  
  
> [!NOTE]  
>  <span data-ttu-id="938e4-146">如需此命令的詳細資訊，請參閱 [bcp 公用程式](../../tools/bcp-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="938e4-146">For more information about this command, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
### <a name="using-bulk-insert"></a><span data-ttu-id="938e4-147">使用 BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="938e4-147">Using BULK INSERT</span></span>  
 <span data-ttu-id="938e4-148">下列範例使用 BULK INSERT，將 `myTestFormatFiles-c.Dat` 資料檔中的資料大量匯入到 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 範例資料庫中的 `HumanResources.myTestFormatFiles` 資料表。</span><span class="sxs-lookup"><span data-stu-id="938e4-148">The following example uses BULK INSERT to bulk import data from the `myTestFormatFiles-c.Dat` data file into `HumanResources.myTestFormatFiles` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="938e4-149">這個範例使用非 XML 格式檔案 `MyTestFormatFiles.Fmt`。</span><span class="sxs-lookup"><span data-stu-id="938e4-149">This example uses a non-XML format file, `MyTestFormatFiles.Fmt`.</span></span> <span data-ttu-id="938e4-150">這個範例會在匯入資料檔之前，刪除任何現有的資料表資料列。</span><span class="sxs-lookup"><span data-stu-id="938e4-150">The example deletes any existing table rows before importing the data file.</span></span>  
  
 <span data-ttu-id="938e4-151">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行：</span><span class="sxs-lookup"><span data-stu-id="938e4-151">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DELETE myTestFormatFiles;  
GO  
BULK INSERT myTestFormatFiles   
   FROM 'C:\myTestFormatFiles-c.Dat'   
   WITH (FORMATFILE = 'C:\myTestFormatFiles.Fmt');  
GO  
SELECT * FROM myTestFormatFiles;  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="938e4-152">如需此陳述式的詳細資訊，請參閱 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="938e4-152">For more information about this statement, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
### <a name="using-the-openrowset-bulk-rowset-provider"></a><span data-ttu-id="938e4-153">使用 OPENROWSET Bulk 資料列集提供者</span><span class="sxs-lookup"><span data-stu-id="938e4-153">Using the OPENROWSET Bulk Rowset Provider</span></span>  
 <span data-ttu-id="938e4-154">下列範例使用 `INSERT ... SELECT * FROM OPENROWSET(BULK...)`，將 `myTestFormatFiles-c.Dat` 資料檔中的資料大量匯入到 `HumanResources.myTestFormatFiles` 範例資料庫中的 `AdventureWorks` 資料表。</span><span class="sxs-lookup"><span data-stu-id="938e4-154">The following example uses `INSERT ... SELECT * FROM OPENROWSET(BULK...)` to bulk import data from the `myTestFormatFiles-c.Dat` data file into `HumanResources.myTestFormatFiles` table in the `AdventureWorks` sample database.</span></span> <span data-ttu-id="938e4-155">這個範例使用 XML 格式檔案 `MyTestFormatFiles.Xml`。</span><span class="sxs-lookup"><span data-stu-id="938e4-155">This example uses an XML format file, `MyTestFormatFiles.Xml`.</span></span> <span data-ttu-id="938e4-156">這個範例會在匯入資料檔之前，刪除任何現有的資料表資料列。</span><span class="sxs-lookup"><span data-stu-id="938e4-156">The example deletes any existing table rows before importing the data file.</span></span>  
  
 <span data-ttu-id="938e4-157">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行：</span><span class="sxs-lookup"><span data-stu-id="938e4-157">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
DELETE myTestFormatFiles;  
GO  
INSERT INTO myTestFormatFiles  
    SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestFormatFiles-c.Dat',  
      FORMATFILE='C:\myTestFormatFiles.Xml'       
      ) as t1 ;  
GO  
SELECT * FROM myTestFormatFiles;  
GO  
```  
  
 <span data-ttu-id="938e4-158">結束使用範例資料表時，可使用以下陳述式卸除該資料表：</span><span class="sxs-lookup"><span data-stu-id="938e4-158">When you finish using the sample table, you can drop it using the following statement:</span></span>  
  
```  
DROP TABLE myTestFormatFiles  
```  
  
> [!NOTE]  
>  <span data-ttu-id="938e4-159">如需有關 OPENROWSET BULK 子句的詳細資訊，請參閱 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="938e4-159">For more information about the OPENROWSET BULK clause, see [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="938e4-160">其他範例</span><span class="sxs-lookup"><span data-stu-id="938e4-160">Additional Examples</span></span>  
 [<span data-ttu-id="938e4-161">建立格式檔案 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="938e4-161">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
 [<span data-ttu-id="938e4-162">使用格式檔案略過資料表資料行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="938e4-162">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 [<span data-ttu-id="938e4-163">使用格式檔案略過資料欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="938e4-163">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
 [<span data-ttu-id="938e4-164">使用格式檔案將資料表資料行對應至資料檔案欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="938e4-164">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="938e4-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="938e4-165">See Also</span></span>  
 <span data-ttu-id="938e4-166">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="938e4-166">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="938e4-167">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="938e4-167">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="938e4-168">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="938e4-168">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="938e4-169">[非 XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="938e4-169">[Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span></span>  
 [<span data-ttu-id="938e4-170">XML 格式檔案 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="938e4-170">XML Format Files &#40;SQL Server&#41;</span></span>](xml-format-files-sql-server.md)  
  
  
