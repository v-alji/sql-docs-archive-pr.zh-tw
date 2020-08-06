---
title: 使用格式檔案略過資料欄位 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- format files [SQL Server], skipping data fields
- skipping data fields when importing
ms.assetid: 6a76517e-983b-47a1-8f02-661b99859a8b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2d3f78c3c97c5bbe862867d5f51ff35f57d147df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607399"
---
# <a name="use-a-format-file-to-skip-a-data-field-sql-server"></a><span data-ttu-id="9c634-102">使用格式檔案略過資料欄位 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9c634-102">Use a Format File to Skip a Data Field (SQL Server)</span></span>
  <span data-ttu-id="9c634-103">資料檔所包含的欄位，可以比資料表中的資料行數多。</span><span class="sxs-lookup"><span data-stu-id="9c634-103">A data file can contain more fields than the number of columns in the table.</span></span> <span data-ttu-id="9c634-104">此主題描述如何將資料表資料行對應到相對的資料欄位並忽略多餘欄位，藉以修改非 XML 格式檔案與 XML 格式檔案，讓資料檔能容納更多欄位。</span><span class="sxs-lookup"><span data-stu-id="9c634-104">This topic describes modifying both non-XML and XML format files to accommodate a data file with more fields by mapping the table columns to the corresponding data fields and ignoring the extra fields.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c634-105">可以使用非 XML 或 XML 格式檔案，將資料檔案大量匯入資料表，方法是使用**bcp**命令、BULK INSERT 語句或 INSERT .。。SELECT \* FROM OPENROWSET (BULK ... ) 語句。</span><span class="sxs-lookup"><span data-stu-id="9c634-105">Either a non-XML or XML format file can be used to bulk import a data file into the table by using a **bcp** command, BULK INSERT statement, or INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement.</span></span> <span data-ttu-id="9c634-106">如需詳細資訊，請參閱[使用格式檔案大量匯入資料 &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9c634-106">For more information, see [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md).</span></span>  
  
## <a name="sample-data-file-and-table"></a><span data-ttu-id="9c634-107">範例資料檔與資料表</span><span class="sxs-lookup"><span data-stu-id="9c634-107">Sample Data File and Table</span></span>  
 <span data-ttu-id="9c634-108">此主題中的修改格式檔案的範例是以下列資料表與資料檔為基礎。</span><span class="sxs-lookup"><span data-stu-id="9c634-108">The examples of modified format files in this topic are based on the following table and data file.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="9c634-109">範例資料表</span><span class="sxs-lookup"><span data-stu-id="9c634-109">Sample Table</span></span>  
 <span data-ttu-id="9c634-110">此範例需要在 `myTestSkipField` 結構描述底下的 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 範例資料庫中建立一個名為 `dbo` 的資料表。</span><span class="sxs-lookup"><span data-stu-id="9c634-110">The examples require that a table named `myTestSkipField` be created in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database under the `dbo` schema.</span></span> <span data-ttu-id="9c634-111">若要建立此資料表，請在 [ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查詢編輯器] 中執行下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="9c634-111">To create this table, in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, run the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestSkipField   
   (  
   PersonID smallint,  
   FirstName nvarchar(50) ,  
   LastName nvarchar(50)   
   );  
GO  
```  
  
### <a name="sample-data-file"></a><span data-ttu-id="9c634-112">範例資料檔</span><span class="sxs-lookup"><span data-stu-id="9c634-112">Sample Data File</span></span>  
 <span data-ttu-id="9c634-113">資料檔 `myTestSkipField-c.dat` 包含下列記錄：</span><span class="sxs-lookup"><span data-stu-id="9c634-113">The data file, `myTestSkipField-c.dat`, contains the following records:</span></span>  
  
```  
1,Skipme,DataField3,DataField4  
1,Skipme,DataField3,DataField4  
1,Skipme,DataField3,DataField4  
```  
  
 <span data-ttu-id="9c634-114">若要從 `myTestSkipField-c.dat` 大量匯入資料到 `myTestSkipField` 資料表中，格式檔案必須執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="9c634-114">To bulk import data from `myTestSkipField-c.dat` into the `myTestSkipField` table, the format file must do the following:</span></span>  
  
-   <span data-ttu-id="9c634-115">將第一個資料欄位對應到第一個資料行 `PersonID`。</span><span class="sxs-lookup"><span data-stu-id="9c634-115">Map the first data field to the first column, `PersonID`.</span></span>  
  
-   <span data-ttu-id="9c634-116">略過第二個資料欄位。</span><span class="sxs-lookup"><span data-stu-id="9c634-116">Skip the second data field.</span></span>  
  
-   <span data-ttu-id="9c634-117">將第三個資料欄位對應到第二個資料行 `FirstName`。</span><span class="sxs-lookup"><span data-stu-id="9c634-117">Map the third data field to the second column, `FirstName`.</span></span>  
  
-   <span data-ttu-id="9c634-118">將第四個資料欄位對應到第三個資料行 `LastName`。</span><span class="sxs-lookup"><span data-stu-id="9c634-118">Map the fourth data field to the third column, `LastName`.</span></span>  
  
## <a name="non-xml-format-file-for-more-data-fields"></a><span data-ttu-id="9c634-119">使用非 XML 格式檔案以取得更多資料欄位</span><span class="sxs-lookup"><span data-stu-id="9c634-119">Non-XML Format File for More Data Fields</span></span>  
 <span data-ttu-id="9c634-120">下列格式檔案 `myTestSkipField.fmt` 會將 `myTestSkipField-c.dat` 中的欄位對應至 `myTestSkipField` 資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="9c634-120">The following format file, `myTestSkipField.fmt`, maps the fields in `myTestSkipField-c.dat` to the columns of the `myTestSkipField` table.</span></span> <span data-ttu-id="9c634-121">格式檔案使用字元資料格式。</span><span class="sxs-lookup"><span data-stu-id="9c634-121">The format file uses character data format.</span></span> <span data-ttu-id="9c634-122">若要略過資料行對應，就必須將其資料行順序值變更為 0，如格式檔案中的 `ExtraField` 資料行所示。</span><span class="sxs-lookup"><span data-stu-id="9c634-122">Skipping a column mapping requires changing its column order value to 0, as shown for the `ExtraField` column in the format file.</span></span>  
  
 <span data-ttu-id="9c634-123">`myTestSkipField.fmt` 格式檔案包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="9c634-123">The `myTestSkipField.fmt` format file contains the following information:</span></span>  
  
```  
9.0  
4  
1       SQLCHAR       0       7       ","      1     PersonID               ""  
2       SQLCHAR       0       100       ","    0     ExtraField             SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     ","      2     FirstName              SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       100     "\r\n"   3     LastName               SQL_Latin1_General_CP1_CI_AS  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="9c634-124">如需非 XML 格式檔案語法的相關資訊，請參閱[非 XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9c634-124">For information about the syntax of non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="9c634-125">範例</span><span class="sxs-lookup"><span data-stu-id="9c634-125">Examples</span></span>  
 <span data-ttu-id="9c634-126">下列範例會利用 `INSERT ... SELECT * FROM OPENROWSET(BULK...)` 格式檔案來使用 `myTestSkipField.fmt`。</span><span class="sxs-lookup"><span data-stu-id="9c634-126">The following example uses `INSERT ... SELECT * FROM OPENROWSET(BULK...)` using the `myTestSkipField.fmt` format file.</span></span> <span data-ttu-id="9c634-127">此範例會將 `myTestSkipField-c.dat` 資料檔案大量匯入 `myTestSkipField` 資料表。</span><span class="sxs-lookup"><span data-stu-id="9c634-127">The example bulk imports the `myTestSkipField-c.dat` data file into the `myTestSkipField` table.</span></span> <span data-ttu-id="9c634-128">若要建立範例資料表和資料檔，請參閱本主題前面的「範例資料檔與資料表」。</span><span class="sxs-lookup"><span data-stu-id="9c634-128">To create the sample table and data file, see "Sample Data File and Table," earlier in this topic.</span></span>  
  
 <span data-ttu-id="9c634-129">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="9c634-129">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, run the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestSkipField   
   SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestSkipField-c.dat',  
      FORMATFILE='C:\myTestSkipField.fmt'    
       ) AS t1;  
GO   
```  
  
## <a name="xml-format-file-for-more-data-fields"></a><span data-ttu-id="9c634-130">使用 XML 格式檔案以取得更多資料欄位</span><span class="sxs-lookup"><span data-stu-id="9c634-130">XML Format File for More Data Fields</span></span>  
 <span data-ttu-id="9c634-131">此範例中的格式檔案，所根據的是另一個格式檔案 `myTestSkipField.xml`，它在整個檔案中都使用字元資料格式，且其欄位在數量與順序上都與 `myTestSkipField` 資料表中的資料行對應。</span><span class="sxs-lookup"><span data-stu-id="9c634-131">The format file presented in this example is based on another format file, `myTestSkipField.xml`, which uses character data format throughout and whose fields correspond exactly in number and order to the columns in the `myTestSkipField` table.</span></span> <span data-ttu-id="9c634-132">若要檢視該格式檔案的內容，請參閱[建立格式檔案 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9c634-132">To view the contents of that format file, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
 <span data-ttu-id="9c634-133">下列格式檔案 `myTestSkipField.xml` 會將 `myTestSkipField-c.dat` 中的欄位對應至 `myTestSkipField` 資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="9c634-133">The following format file, `myTestSkipField.xml`, maps the fields in `myTestSkipField-c.dat` to the columns of the `myTestSkipField` table.</span></span> <span data-ttu-id="9c634-134">格式檔案使用字元資料格式。</span><span class="sxs-lookup"><span data-stu-id="9c634-134">The format file uses character data format.</span></span>  
  
 <span data-ttu-id="9c634-135">`myTestSkipField.xml` 格式檔案包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="9c634-135">The `myTestSkipField.xml` format file contains the following information:</span></span>  
  
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
  <COLUMN SOURCE="1" NAME="PersonID" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="3" NAME="FirstName" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="LastName" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
### <a name="examples"></a><span data-ttu-id="9c634-136">範例</span><span class="sxs-lookup"><span data-stu-id="9c634-136">Examples</span></span>  
 <span data-ttu-id="9c634-137">下列範例會利用 `INSERT ... SELECT * FROM OPENROWSET(BULK...)` 格式檔案來使用 `myTestSkipField.Xml`。</span><span class="sxs-lookup"><span data-stu-id="9c634-137">The following example uses `INSERT ... SELECT * FROM OPENROWSET(BULK...)` using the `myTestSkipField.Xml` format file.</span></span> <span data-ttu-id="9c634-138">此範例會將 `myTestSkipField-c.dat` 資料檔案大量匯入 `myTestSkipField` 資料表。</span><span class="sxs-lookup"><span data-stu-id="9c634-138">The example bulk imports the `myTestSkipField-c.dat` data file into the `myTestSkipField` table.</span></span> <span data-ttu-id="9c634-139">若要建立範例資料表和資料檔，請參閱本主題前面的「範例資料檔與資料表」。</span><span class="sxs-lookup"><span data-stu-id="9c634-139">To create the sample table and data file, see "Sample Data File and Table," earlier in this topic.</span></span>  
  
 <span data-ttu-id="9c634-140">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="9c634-140">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, run the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestSkipField   
  SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestSkipField-c.dat',  
      FORMATFILE='C:\myTestSkipField.xml'    
       ) AS t1;  
GO  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="9c634-141">如需 XML 結構描述語法的相關資訊以及 XML 格式檔案的其他範例，請參閱 [XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9c634-141">For information about the syntax of the XML Schema and additional samples of XML format files, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c634-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c634-142">See Also</span></span>  
 <span data-ttu-id="9c634-143">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="9c634-143">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="9c634-144">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9c634-144">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="9c634-145">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9c634-145">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="9c634-146">[使用格式檔案略過資料表資料行 &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9c634-146">[Use a Format File to Skip a Table Column &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md) </span></span>  
 [<span data-ttu-id="9c634-147">使用格式檔案將資料表資料行對應至資料檔案欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9c634-147">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
  
