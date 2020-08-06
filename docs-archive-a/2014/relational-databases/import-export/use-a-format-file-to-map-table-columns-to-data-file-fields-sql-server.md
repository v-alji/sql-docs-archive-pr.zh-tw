---
title: 使用格式檔案將資料表資料行對應至資料檔案欄位 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- mapping columns to fields during import [SQL Server]
- format files [SQL Server], mapping columns to fields
ms.assetid: e7ee4f7e-24c4-4eb7-84d2-41e57ccc1ef1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c7de0b5ce486f187a1bdd27197984aa3c411f4a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593391"
---
# <a name="use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server"></a><span data-ttu-id="3b735-102">使用格式檔案將資料表資料行對應至資料檔欄位 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3b735-102">Use a Format File to Map Table Columns to Data-File Fields (SQL Server)</span></span>
  <span data-ttu-id="3b735-103">資料檔中包含的欄位順序可以與資料表中對應資料行的順序不同。</span><span class="sxs-lookup"><span data-stu-id="3b735-103">A data file can contain fields arranged in a different order from the corresponding columns in the table.</span></span> <span data-ttu-id="3b735-104">此主題呈現非 XML 與 XML 格式檔案，這些檔案已經過修改，以配合欄位順序與資料表資料行不同的資料檔。</span><span class="sxs-lookup"><span data-stu-id="3b735-104">This topic presents both non-XML and XML format files that have been modified to accommodate a data file whose fields are arranged in a different order from the table columns.</span></span> <span data-ttu-id="3b735-105">已修改的格式檔案可將資料欄位對應到與它們對應的資料表資料行。</span><span class="sxs-lookup"><span data-stu-id="3b735-105">The modified format file maps the data fields to their corresponding table columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b735-106">非 XML 格式檔案或 XML 格式檔案可以用來將資料檔案大量匯入資料表，方法是使用**bcp**命令、BULK INSERT 語句或 INSERT .。。SELECT \* FROM OPENROWSET (BULK ... ) 語句。</span><span class="sxs-lookup"><span data-stu-id="3b735-106">Either a non-XML format file or an XML format file can be used to bulk import a data file into the table by using a **bcp** command, BULK INSERT statement, or INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement.</span></span> <span data-ttu-id="3b735-107">如需詳細資訊，請參閱[使用格式檔案大量匯入資料 &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3b735-107">For more information, see [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md).</span></span>  
  
## <a name="sample-table-and-data-file"></a><span data-ttu-id="3b735-108">範例資料表與資料檔</span><span class="sxs-lookup"><span data-stu-id="3b735-108">Sample Table and Data File</span></span>  
 <span data-ttu-id="3b735-109">此主題中的修改格式檔案的範例是以下列資料表與資料檔為基礎。</span><span class="sxs-lookup"><span data-stu-id="3b735-109">The examples of modified format files in this topic are based on the following table and data file.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="3b735-110">範例資料表</span><span class="sxs-lookup"><span data-stu-id="3b735-110">Sample Table</span></span>  
 <span data-ttu-id="3b735-111">本主題中的範例需要在 `dbo` 結構描述底下的 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 範例資料庫中建立一個名為 `myTestOrder` 的資料表。</span><span class="sxs-lookup"><span data-stu-id="3b735-111">The examples in this topic require that a table named `myTestOrder` be created in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database under the `dbo` schema.</span></span> <span data-ttu-id="3b735-112">若要建立這個資料表，請在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="3b735-112">To create this table, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestOrder   
   (  
   Col1 smallint,  
   Col2 nvarchar(50) ,  
   Col3 nvarchar(50) ,   
   Col4 nvarchar(50)   
   );  
GO  
  
```  
  
### <a name="data-file"></a><span data-ttu-id="3b735-113">資料檔</span><span class="sxs-lookup"><span data-stu-id="3b735-113">Data File</span></span>  
 <span data-ttu-id="3b735-114">資料檔 `myTestOrder-c.txt` 包含下列記錄：</span><span class="sxs-lookup"><span data-stu-id="3b735-114">The data file, `myTestOrder-c.txt`, contains the following records:</span></span>  
  
```  
DataField3,DataField2,1,DataField4  
DataField3,DataField2,1,DataField4  
DataField3,DataField2,1,DataField4  
  
```  
  
 <span data-ttu-id="3b735-115">若要從 `myTestSkipCol2-c.dat` 大量匯入資料到 `myTestSkipCol` 資料表中，格式檔案必須對應第一個資料欄位至 `Col3`、第二個資料欄位至 `Col2`、第三個資料欄位至 `Col1`，以及第四個資料欄位至 `Col4`。</span><span class="sxs-lookup"><span data-stu-id="3b735-115">To bulk import data from `myTestSkipCol2-c.dat` into the `myTestSkipCol` table, the format file must map the first data field to `Col3`, the second data field to `Col2`, the third data field to `Col1`, and the fourth data field to `Col4`.</span></span>  
  
## <a name="using-a-non-xml-format-file"></a><span data-ttu-id="3b735-116">使用非 XML 格式檔案</span><span class="sxs-lookup"><span data-stu-id="3b735-116">Using a Non-XML Format File</span></span>  
 <span data-ttu-id="3b735-117">您可以變更資料行的順序值，指出對應資料欄位的位置，來變更資料行對應的順序。</span><span class="sxs-lookup"><span data-stu-id="3b735-117">You can change the order of a column mapping by changing the order value for the column to indicate the position of the corresponding data field.</span></span>  
  
 <span data-ttu-id="3b735-118">下列非 XML 格式檔案範例呈現格式檔案 `myTestOrder.fmt`，它會將 `myTestOrder-c.txt` 中的欄位對應到 `myTestOrder` 資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="3b735-118">The following sample non-XML format file presents a format file, `myTestOrder.fmt`, that maps the fields in `myTestOrder-c.txt` to the columns of the `myTestOrder` table.</span></span> <span data-ttu-id="3b735-119">如需有關如何建立範例資料表和資料檔的詳細資訊，請參閱本主題前面的「範例資料表與資料檔」。</span><span class="sxs-lookup"><span data-stu-id="3b735-119">For information about how to create the data file and table, see "Sample Table and Data File," earlier in this topic.</span></span> <span data-ttu-id="3b735-120">格式檔案使用字元資料格式。</span><span class="sxs-lookup"><span data-stu-id="3b735-120">The format file uses character data format.</span></span>  
  
 <span data-ttu-id="3b735-121">格式檔案包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="3b735-121">The format file contains the following information:</span></span>  
  
```  
9.0  
4  
1       SQLCHAR       0       100     ","     3     Col3               SQL_Latin1_General_CP1_CI_AS  
2       SQLCHAR       0       100     ","     2     Col2               SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       7       ","     1     Col1               ""  
4       SQLCHAR       0       100     "\r\n"  4     Col4               SQL_Latin1_General_CP1_CI_AS  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="3b735-122">如需非 XML 格式檔案版面配置的詳細資訊，請參閱[非 XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3b735-122">For more information about the layout of non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="3b735-123">範例</span><span class="sxs-lookup"><span data-stu-id="3b735-123">Example</span></span>  
 <span data-ttu-id="3b735-124">下列範例使用 `BULK INSERT` 陳述式，利用 `myTestOrder-c.txt` 非 XML 格式檔案，將 `myTestOrder` 資料檔中的資料大量匯入 `myTestOrder.fmt` 範例資料表。</span><span class="sxs-lookup"><span data-stu-id="3b735-124">The following example uses a `BULK INSERT` statement to bulk import data from the `myTestOrder-c.txt` data file into the `myTestOrder` sample table by using the `myTestOrder.fmt` non-XML format file.</span></span>  
  
 <span data-ttu-id="3b735-125">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行：</span><span class="sxs-lookup"><span data-stu-id="3b735-125">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestOrder  
FROM 'C:\myTestOrder-c.txt'   
WITH (formatfile='C:\myTestOrder.fmt');  
GO  
  
```  
  
## <a name="using-an-xml-format-file"></a><span data-ttu-id="3b735-126">使用 XML 格式檔案</span><span class="sxs-lookup"><span data-stu-id="3b735-126">Using an XML Format File</span></span>  
 <span data-ttu-id="3b735-127">下列非 XML 格式檔案範例呈現格式檔案 `myTestOrder.xml`，它會將 `myTestOrder-c.txt` 中的欄位對應到 `myTestOrder` 資料表的資料行。如需有關如何建立資料表和資料檔的詳細資訊，請參閱本主題前面的「範例資料表與資料檔」。</span><span class="sxs-lookup"><span data-stu-id="3b735-127">The following sample non-XML format file presents a format file, `myTestOrder.xml`, that maps the fields in `myTestOrder-c.txt` to the columns of the `myTestOrder` table For information about how to create the data file and table, see "Sample Table and Data File," earlier in this topic.</span></span>  
  
 <span data-ttu-id="3b735-128">`myTestOrder.xml` 格式檔案包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="3b735-128">The `myTestOrder.xml` format file contains the following information:</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="3" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="1" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Col4" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="3b735-129">如需 XML 結構描述語法的相關資訊以及 XML 格式檔案的其他範例，請參閱 [XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3b735-129">For information about the syntax of the XML Schema and additional samples of XML format files, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="3b735-130">範例</span><span class="sxs-lookup"><span data-stu-id="3b735-130">Example</span></span>  
 <span data-ttu-id="3b735-131">下列範例使用 `OPENROWSET` 大量資料列集提供者，利用 `myTestOrder-c.txt` XML 格式檔案，將 `myTestOrder` 資料檔中的資料匯入 `myTestOrder.xml` 範例資料表。</span><span class="sxs-lookup"><span data-stu-id="3b735-131">The following example uses the `OPENROWSET` bulk rowset provider to import data from the `myTestOrder-c.txt` data file into the `myTestOrder` sample table by using the `myTestOrder.xml` XML format file.</span></span> <span data-ttu-id="3b735-132">`INSERT... SELECT`陳述式指定選取清單中的資料行清單。</span><span class="sxs-lookup"><span data-stu-id="3b735-132">The `INSERT... SELECT` statement specifies the column list in the select list.</span></span>  
  
 <span data-ttu-id="3b735-133">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="3b735-133">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestOrder   
  SELECT Col1, Col2, Col3, Col4  
      FROM  OPENROWSET(BULK  'C:\myTestOrder-c.txt',  
      FORMATFILE='C:\myTestOrder.Xml'    
       ) AS t1;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b735-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b735-134">See Also</span></span>  
 <span data-ttu-id="3b735-135">[使用格式檔案略過資料表資料行 &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3b735-135">[Use a Format File to Skip a Table Column &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md) </span></span>  
 [<span data-ttu-id="3b735-136">使用格式檔案略過資料欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b735-136">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
  
