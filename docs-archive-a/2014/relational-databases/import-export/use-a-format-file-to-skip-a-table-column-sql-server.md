---
title: 使用格式檔案以略過資料表資料行 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- skipping columns when importing
- format files [SQL Server], skipping columns
ms.assetid: 30e0e7b9-d131-46c7-90a4-6ccf77e3d4f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 153ef21209ff4261020e26aca3bc52d28dc852a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607391"
---
# <a name="use-a-format-file-to-skip-a-table-column-sql-server"></a><span data-ttu-id="44eb6-102">使用格式檔案以略過資料表資料行 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="44eb6-102">Use a Format File to Skip a Table Column (SQL Server)</span></span>
  <span data-ttu-id="44eb6-103">本主題將說明格式檔案。</span><span class="sxs-lookup"><span data-stu-id="44eb6-103">This topic describes format files.</span></span> <span data-ttu-id="44eb6-104">當欄位不存在於資料檔案中時，您就可以使用格式檔案來略過資料表資料行的匯入。</span><span class="sxs-lookup"><span data-stu-id="44eb6-104">You can use a format file to skip importing a table column when the field does not exist in the data file.</span></span> <span data-ttu-id="44eb6-105">只有在略過的資料行可為 Null 和/或有預設值時，資料檔案所包含的欄位才可以少於資料表中的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="44eb6-105">A data file can contain fewer fields than the number of columns in the table only if the skipped columns are nullable and/or have default value.</span></span>

## <a name="sample-table-and-data-file"></a><span data-ttu-id="44eb6-106">範例資料表與資料檔</span><span class="sxs-lookup"><span data-stu-id="44eb6-106">Sample Table and Data File</span></span>
 <span data-ttu-id="44eb6-107">下列範例會要求在 `myTestSkipCol` dbo [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 結構描述下之 **範例資料庫中有一個名為** 的資料表。</span><span class="sxs-lookup"><span data-stu-id="44eb6-107">The following examples require a table named `myTestSkipCol` in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database under the **dbo** schema.</span></span> <span data-ttu-id="44eb6-108">使用如下陳述式建立此資料表：</span><span class="sxs-lookup"><span data-stu-id="44eb6-108">Create this table as follows:</span></span>

```
USE AdventureWorks2012;
GO
CREATE TABLE myTestSkipCol 
   (
   Col1 smallint,
   Col2 nvarchar(50) NULL,
   Col3 nvarchar(50) not NULL
   );
GO
```

 <span data-ttu-id="44eb6-109">下列範例會使用範例資料檔案 `myTestSkipCol2.dat`，而且這個檔案只包含兩個欄位 (雖然對應的資料表包含三個資料行)：</span><span class="sxs-lookup"><span data-stu-id="44eb6-109">The following examples use a sample data file, `myTestSkipCol2.dat`, which contains only two fields, although the corresponding table contains three columns:</span></span>

```
1,DataForColumn3
1,DataForColumn3
1,DataForColumn3

```

 <span data-ttu-id="44eb6-110">若要將資料從 `myTestSkipCol2.dat` 大量匯入 `myTestSkipCol` 資料表中，格式檔案必須將第一個資料欄位對應到 `Col1`、第二個欄位對應到 `Col3`，但是要略過 `Col2`。</span><span class="sxs-lookup"><span data-stu-id="44eb6-110">To bulk import data from `myTestSkipCol2.dat` into the `myTestSkipCol` table, the format file must map the first data field to `Col1`, the second field to `Col3`, skipping `Col2`.</span></span>

## <a name="using-a-non-xml-format-file"></a><span data-ttu-id="44eb6-111">使用非 XML 格式檔案</span><span class="sxs-lookup"><span data-stu-id="44eb6-111">Using a Non-XML Format File</span></span>
 <span data-ttu-id="44eb6-112">您可以修改非 XML 格式檔案以略過資料表資料行。</span><span class="sxs-lookup"><span data-stu-id="44eb6-112">You can modify a non-XML format file to skip a table column.</span></span> <span data-ttu-id="44eb6-113">一般而言，這涉及到使用 **bcp** 公用程式以建立預設的非 XML 格式檔案，以及在文字編輯器中修改預設的檔案。</span><span class="sxs-lookup"><span data-stu-id="44eb6-113">Typically, this involves using the **bcp** utility to create a default non-XML format file and the modifying the default file in a text editor.</span></span> <span data-ttu-id="44eb6-114">修改過的格式檔案必須將每個現有欄位對應到相對的資料表資料行，並且指出要略過哪些資料表資料行或資料行。</span><span class="sxs-lookup"><span data-stu-id="44eb6-114">The modified format file must map each existing fields to its corresponding table column and indicate which table column or columns to skip.</span></span> <span data-ttu-id="44eb6-115">有兩個替代方法可以修改預設的非 XML 資料檔案。</span><span class="sxs-lookup"><span data-stu-id="44eb6-115">Two alternatives exist for modifying a default non-XML data file.</span></span> <span data-ttu-id="44eb6-116">兩個替代方法都會指出資料欄位並不存在於資料檔案中，且不會將任何資料插入對應的資料表資料行。</span><span class="sxs-lookup"><span data-stu-id="44eb6-116">Either alternative indicates that the data field does not exist in the data file and that no data will be inserted into the corresponding table column.</span></span>

### <a name="creating-a-default-non-xml-format-file"></a><span data-ttu-id="44eb6-117">建立預設的非 XML 格式檔案</span><span class="sxs-lookup"><span data-stu-id="44eb6-117">Creating a Default Non-XML Format File</span></span>
 <span data-ttu-id="44eb6-118">本主題使用 `myTestSkipCol` 範例資料表的預設非 XML 格式檔案，這是使用下列 **bcp** 命令所建立：</span><span class="sxs-lookup"><span data-stu-id="44eb6-118">This topic uses the default non-XML format file that was created for the `myTestSkipCol` sample table by using the following **bcp** command:</span></span>

```
bcp AdventureWorks2012..myTestSkipCol format nul -f myTestSkipCol_Default.fmt -c -T
```

 <span data-ttu-id="44eb6-119">上述命令會建立非 XML 格式檔案 `myTestSkipCol_Default.fmt`。</span><span class="sxs-lookup"><span data-stu-id="44eb6-119">The previous command creates a non-XML format file, `myTestSkipCol_Default.fmt`.</span></span> <span data-ttu-id="44eb6-120">這個格式檔案稱為「預設格式檔案」  (Default Format File)，因為它是 **bcp** 所產生的格式。</span><span class="sxs-lookup"><span data-stu-id="44eb6-120">This format file is called a *default format file* because it is the form generated by **bcp**.</span></span> <span data-ttu-id="44eb6-121">一般而言，預設格式檔案描述資料檔欄位與資料表資料行之間的一對一對應。</span><span class="sxs-lookup"><span data-stu-id="44eb6-121">Typically, a default format file describes a one-to-one correspondence between data-file fields and table columns.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="44eb6-122">您可能需要指定您要連接的伺服器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="44eb6-122">You might have to specify the name of the server instance to which you are connecting.</span></span> <span data-ttu-id="44eb6-123">此外，也可能需要指定使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="44eb6-123">Also, you might have to specify the user name and password.</span></span> <span data-ttu-id="44eb6-124">如需相關資訊，請參閱 [bcp Utility](../../tools/bcp-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="44eb6-124">For more information, see [bcp Utility](../../tools/bcp-utility.md).</span></span>

 <span data-ttu-id="44eb6-125">下列圖解顯示了這個範例預設格式檔案中的值。</span><span class="sxs-lookup"><span data-stu-id="44eb6-125">The following illustration shows the values in this sample default format files.</span></span> <span data-ttu-id="44eb6-126">此圖解同時顯示每個格式檔欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="44eb6-126">The illustration also shows the name of each format-file field.</span></span>

 <span data-ttu-id="44eb6-127">![myTestSkipCol 的預設非 XML 格式檔案](../../database-engine/media/mytestskipcol-f-c-default-fmt.gif "myTestSkipCol 的預設非 XML 格式檔案")</span><span class="sxs-lookup"><span data-stu-id="44eb6-127">![default non-XML format file for myTestSkipCol](../../database-engine/media/mytestskipcol-f-c-default-fmt.gif "default non-XML format file for myTestSkipCol")</span></span>

> [!NOTE]
>  <span data-ttu-id="44eb6-128">如需格式檔案欄位的詳細資訊，請參閱[非 XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="44eb6-128">For more information about the format-file fields, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>

### <a name="methods-for-modifying-a-non-xml-format-file"></a><span data-ttu-id="44eb6-129">修改非 XML 格式檔案的方法</span><span class="sxs-lookup"><span data-stu-id="44eb6-129">Methods for Modifying a Non-XML Format File</span></span>
 <span data-ttu-id="44eb6-130">若要略過資料表資料行，請編輯預設的非 XML 格式檔案，並且使用下列其中一個替代方法來修改檔案：</span><span class="sxs-lookup"><span data-stu-id="44eb6-130">To skip a table column, edit the default non-XML format file and modify the file by using one of the following alternative methods:</span></span>

-   <span data-ttu-id="44eb6-131">慣用的方法包括三個基本步驟。</span><span class="sxs-lookup"><span data-stu-id="44eb6-131">The preferred method involves three basic steps.</span></span> <span data-ttu-id="44eb6-132">首先，刪除資料檔案中遺失的、任何描述欄位的格式檔資料列。</span><span class="sxs-lookup"><span data-stu-id="44eb6-132">First, delete any format-file row that describes a field that is missing from the data file.</span></span> <span data-ttu-id="44eb6-133">接著，減少所刪除的資料列之後的、每個格式檔資料列的「主檔案欄位順序」值。</span><span class="sxs-lookup"><span data-stu-id="44eb6-133">Then, reduce the "Host file field order" value of each format-file row that follows a deleted row.</span></span> <span data-ttu-id="44eb6-134">目的是要產生連續的「主檔案欄位順序」值 (1 到 *n*)，以反映每個資料欄位在資料檔案中的實際位置。</span><span class="sxs-lookup"><span data-stu-id="44eb6-134">The goal is sequential "Host file field order" values, 1 through *n*, that reflect the actual position of each data field in the data file.</span></span> <span data-ttu-id="44eb6-135">最後，減少 [資料行數目] 欄位中的值，以反映資料檔案中欄位的實際數目。</span><span class="sxs-lookup"><span data-stu-id="44eb6-135">Finally, reduce the value in the "Number of columns" field to reflect the actual number of fields in the data file.</span></span>

     <span data-ttu-id="44eb6-136">下列範例根據 `myTestSkipCol` 資料表的預設格式檔案，這是本主題先前在「建立預設的非 XML 格式檔案」中建立的格式檔。</span><span class="sxs-lookup"><span data-stu-id="44eb6-136">The following example is based on the default format file for the `myTestSkipCol` table, which is created in "Creating a Default Non-XML Format File," earlier in this topic.</span></span> <span data-ttu-id="44eb6-137">這個修改過的格式檔案將第一個資料欄位對應到 `Col1`、略過 `Col2`，然後對應第二個資料欄位到 `Col3`。</span><span class="sxs-lookup"><span data-stu-id="44eb6-137">This modified format file maps the first data field to `Col1`, skips `Col2`, and maps the second data field to `Col3`.</span></span> <span data-ttu-id="44eb6-138">`Col2` 資料列現在已經刪除。</span><span class="sxs-lookup"><span data-stu-id="44eb6-138">The row for `Col2` has been deleted.</span></span> <span data-ttu-id="44eb6-139">其他修改的部分會以粗體顯示：</span><span class="sxs-lookup"><span data-stu-id="44eb6-139">Other modifications are indicated in bold:</span></span>

    ```
    9.0
    2
    1       SQLCHAR       0       7       "\t"     1     Col1         ""
    2       SQLCHAR       0       100     "\r\n"   3     Col3         SQL_Latin1_General_CP1_CI_AS
    ```

-   <span data-ttu-id="44eb6-140">此外，若要略過資料表資料行，您也可以修改對應於資料表資料行的格式檔資料列的定義。</span><span class="sxs-lookup"><span data-stu-id="44eb6-140">Alternatively, to skip a table column, you can modify the definition of the format-file row that corresponds to the table column.</span></span> <span data-ttu-id="44eb6-141">在這個格式檔資料列中，[前置長度]、[主檔案資料長度] 和 [伺服器資料行順序] 值都必須設定為 0。</span><span class="sxs-lookup"><span data-stu-id="44eb6-141">In this format-file row, the "prefix length," "host file data length," and "server column order" values must be set to 0.</span></span> <span data-ttu-id="44eb6-142">此外，[結束字元] 和 [資料行定序] 欄位則必須設定為 "" (NULL)。</span><span class="sxs-lookup"><span data-stu-id="44eb6-142">Also, the "terminator" and "column collation" fields must be set to "" (NULL).</span></span>

     <span data-ttu-id="44eb6-143">雖然不需要實際的資料行名稱，但是 [伺服器資料行名稱] 值仍必須為非空白字串。</span><span class="sxs-lookup"><span data-stu-id="44eb6-143">The "server column name" value requires a nonblank string, though the actual column name is not necessary.</span></span> <span data-ttu-id="44eb6-144">其餘的格式欄位需要各自的預設值。</span><span class="sxs-lookup"><span data-stu-id="44eb6-144">The remaining format fields require their default values.</span></span>

     <span data-ttu-id="44eb6-145">下列範例也是從 `myTestSkipCol` 資料表的預設格式檔案衍生的。</span><span class="sxs-lookup"><span data-stu-id="44eb6-145">The following example is also derived from the default format file for the `myTestSkipCol` table.</span></span> <span data-ttu-id="44eb6-146">必須為 0 或 NULL 的值會以粗體顯示。</span><span class="sxs-lookup"><span data-stu-id="44eb6-146">Values that must be 0 or NULL are indicated in bold.</span></span>

    ```
    9.0
    3
    1       SQLCHAR       0       7       "\t"     1     Col1         ""
    2       SQLCHAR       00""0     Col2         ""
    3       SQLCHAR       0       100     "\r\n"   3     Col3         SQL_Latin1_General_CP1_CI_AS
    ```

### <a name="examples"></a><span data-ttu-id="44eb6-147">範例</span><span class="sxs-lookup"><span data-stu-id="44eb6-147">Examples</span></span>
 <span data-ttu-id="44eb6-148">下列範例也是基於本主題先前在「範例資料表與資料檔」中建立的 `myTestSkipCol` 範例資料表以及 `myTestSkipCol2.dat` 範例資料檔案。</span><span class="sxs-lookup"><span data-stu-id="44eb6-148">The following examples are also based on the `myTestSkipCol` sample table and the `myTestSkipCol2.dat` sample data file that are created in "Sample Table and Data File," earlier in this topic.</span></span>

#### <a name="using-bulk-insert"></a><span data-ttu-id="44eb6-149">使用 BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="44eb6-149">Using BULK INSERT</span></span>
 <span data-ttu-id="44eb6-150">這個範例要使用本主題先前在「修改非 XML 格式檔案的方法」中建立的任一修改過的非 XML 格式檔案，才能運作。</span><span class="sxs-lookup"><span data-stu-id="44eb6-150">This example works by using either of the modified non-XML format files created in "Methods for Modifying a Non-XML Format File," earlier in this topic.</span></span> <span data-ttu-id="44eb6-151">在這個範例中，修改的格式檔案命名為 `C:\myTestSkipCol2.fmt`。</span><span class="sxs-lookup"><span data-stu-id="44eb6-151">In this example, the modified format file is named `C:\myTestSkipCol2.fmt`.</span></span> <span data-ttu-id="44eb6-152">若要使用 `BULK INSERT` 大量匯入 `myTestSkipCol2.dat` 資料檔，請在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中執行下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="44eb6-152">To use `BULK INSERT` to bulk import the `myTestSkipCol2.dat` data file, in the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>

```
USE AdventureWorks2012;
GO
BULK INSERT myTestSkipCol 
   FROM 'C:\myTestSkipCol2.dat' 
   WITH (FORMATFILE = 'C:\myTestSkipCol2.fmt');
GO
SELECT * FROM myTestSkipCol;
GO
```

## <a name="using-an-xml-format-file"></a><span data-ttu-id="44eb6-153">使用 XML 格式檔案</span><span class="sxs-lookup"><span data-stu-id="44eb6-153">Using an XML Format File</span></span>
 <span data-ttu-id="44eb6-154">如果使用 XML 格式檔案，您就不能在直接匯入至資料表時，使用 **bcp** 命令或 BULK INSERT 陳述式來略過資料行。</span><span class="sxs-lookup"><span data-stu-id="44eb6-154">With an XML format file, you cannot skip a column when you are importing directly into a table by using a **bcp** command or a BULK INSERT statement.</span></span> <span data-ttu-id="44eb6-155">不過，您可以匯入資料表最後一個資料行以外的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="44eb6-155">However, you can import into all but the last column of a table.</span></span> <span data-ttu-id="44eb6-156">如果您必須略過最後一個資料行以外的任何資料行，就必須建立只有包含資料檔案中包含之資料行的目標資料表檢視。</span><span class="sxs-lookup"><span data-stu-id="44eb6-156">If you have to skip any but the last column, you must create a view of the target table that contains only the columns contained in the data file.</span></span> <span data-ttu-id="44eb6-157">然後，您就可以從該檔案將大量資料匯入檢視。</span><span class="sxs-lookup"><span data-stu-id="44eb6-157">Then, you can bulk import data from that file into the view.</span></span>

 <span data-ttu-id="44eb6-158">若要利用 OPENROWSET(BULK...) 來使用 XML 格式檔案，以略過資料表資料行，您就必須在選取清單和目標資料表中提供明確的資料行清單，如下所示：</span><span class="sxs-lookup"><span data-stu-id="44eb6-158">To use an XML format file to skip a table column by using OPENROWSET(BULK...), you have to provide explicit list of columns in the select list and also in the target table, as follows:</span></span>

 <span data-ttu-id="44eb6-159">INSERT ...<column_list> SELECT <column_list> FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="44eb6-159">INSERT ...<column_list> SELECT <column_list> FROM OPENROWSET(BULK...)</span></span>

### <a name="creating-a-default-xml-format-file"></a><span data-ttu-id="44eb6-160">建立預設的 XML 格式檔案</span><span class="sxs-lookup"><span data-stu-id="44eb6-160">Creating a Default XML Format File</span></span>
 <span data-ttu-id="44eb6-161">修改的格式檔案的範例以本主題先前在＜範例資料表與資料檔＞中建立的 `myTestSkipCol` 範例資料表與資料檔為基礎。</span><span class="sxs-lookup"><span data-stu-id="44eb6-161">The examples of modified format files are based on the `myTestSkipCol` sample table and data file that are created in "Sample Table and Data File," earlier in this topic.</span></span> <span data-ttu-id="44eb6-162">下列 **bcp** 命令會建立 `myTestSkipCol` 資料表的預設 XML 格式檔案：</span><span class="sxs-lookup"><span data-stu-id="44eb6-162">The following **bcp** command creates a default XML format file for the `myTestSkipCol` table:</span></span>

```
bcp AdventureWorks2012..myTestSkipCol format nul -f myTestSkipCol_Default.xml -c -x -T
```

 <span data-ttu-id="44eb6-163">產生的預設非 XML 格式檔案描述的是資料檔欄位與資料表資料行之間的一對一對應，如下所示：</span><span class="sxs-lookup"><span data-stu-id="44eb6-163">The resulting default non-XML format file describes a one-to-one correspondence between data-file fields and table columns, as follows:</span></span>

```
<?xml version="1.0"?>
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
 <RECORD>
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="7"/>
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
 </RECORD>
 <ROW>
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>
  <COLUMN SOURCE="3" NAME="Col3" xsi:type="SQLNVARCHAR"/>
 </ROW>
</BCPFORMAT>
```

> [!NOTE]
>  <span data-ttu-id="44eb6-164">如需 XML 格式檔案之結構的相關資訊，請參閱 [XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="44eb6-164">For information about the structure of XML format files, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>

### <a name="examples"></a><span data-ttu-id="44eb6-165">範例</span><span class="sxs-lookup"><span data-stu-id="44eb6-165">Examples</span></span>
 <span data-ttu-id="44eb6-166">本節中的範例使用本主題先前在「範例資料表與資料檔」中建立的 `myTestSkipCol` 範例資料表以及 `myTestSkipCol2.dat` 範例資料檔案。</span><span class="sxs-lookup"><span data-stu-id="44eb6-166">The examples in this section use the `myTestSkipCol` sample table and the `myTestSkipCol2.dat` sample data file that are created in "Sample Table and Data File," earlier in this topic.</span></span> <span data-ttu-id="44eb6-167">為了將資料從 `myTestSkipCol2.dat` 匯入至 `myTestSkipCol` 資料表，這個範例使用修改過的 XML 格式檔案 `myTestSkipCol2-x.xml`。</span><span class="sxs-lookup"><span data-stu-id="44eb6-167">To import the data from `myTestSkipCol2.dat` into the `myTestSkipCol` table, the examples use the following modified XML format file, `myTestSkipCol2-x.xml`.</span></span> <span data-ttu-id="44eb6-168">這個檔案是以本主題先前在＜建立預設的 XML 格式檔案＞中建立的格式檔案為基礎。</span><span class="sxs-lookup"><span data-stu-id="44eb6-168">This is based on the format file that is created in "Creating a Default XML Format File," earlier in this topic.</span></span>

```
<?xml version="1.0"?>
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
 <RECORD>
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
 </RECORD>
 <ROW>
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>
  <COLUMN SOURCE="2" NAME="Col3" xsi:type="SQLNVARCHAR"/>
 </ROW>
</BCPFORMAT>
```

#### <a name="using-openrowsetbulk"></a><span data-ttu-id="44eb6-169">使用 OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="44eb6-169">Using OPENROWSET(BULK...)</span></span>
 <span data-ttu-id="44eb6-170">下列範例會使用 `OPENROWSET` 大量資料列集提供者和 `myTestSkipCol2.xml` 格式檔案。</span><span class="sxs-lookup"><span data-stu-id="44eb6-170">The following example uses the `OPENROWSET` bulk rowset provider and the `myTestSkipCol2.xml` format file.</span></span> <span data-ttu-id="44eb6-171">此範例會將 `myTestSkipCol2.dat` 資料檔案大量匯入 `myTestSkipCol` 資料表。</span><span class="sxs-lookup"><span data-stu-id="44eb6-171">The example bulk imports the `myTestSkipCol2.dat` data file into the `myTestSkipCol` table.</span></span> <span data-ttu-id="44eb6-172">此陳述式會依需要，在選取清單還有目標資料表中包含明確的資料行清單。</span><span class="sxs-lookup"><span data-stu-id="44eb6-172">The statement contains an explicit list of columns in the select list and also in the target table, as required.</span></span>

 <span data-ttu-id="44eb6-173">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="44eb6-173">In the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>

```
USE AdventureWorks2012;
GO
INSERT INTO myTestSkipCol
  (Col1,Col3)
    SELECT Col1,Col3
      FROM  OPENROWSET(BULK  'C:\myTestSkipCol2.Dat',
      FORMATFILE='C:\myTestSkipCol2.Xml'  
       ) as t1 ;
GO
```

#### <a name="using-bulk-import-on-a-view"></a><span data-ttu-id="44eb6-174">在檢視上使用 BULK IMPORT</span><span class="sxs-lookup"><span data-stu-id="44eb6-174">Using BULK IMPORT on a View</span></span>
 <span data-ttu-id="44eb6-175">下列範例會在 `v_myTestSkipCol` 資料表上建立 `myTestSkipCol` 。</span><span class="sxs-lookup"><span data-stu-id="44eb6-175">The following example creates the `v_myTestSkipCol` on the `myTestSkipCol` table.</span></span> <span data-ttu-id="44eb6-176">這個檢視會略過第二個資料表資料行 `Col2`。</span><span class="sxs-lookup"><span data-stu-id="44eb6-176">This view skips the second table column, `Col2`.</span></span> <span data-ttu-id="44eb6-177">然後，此範例會使用 `BULK INSERT` ，將 `myTestSkipCol2.dat` 資料檔案匯入這個檢視。</span><span class="sxs-lookup"><span data-stu-id="44eb6-177">The example then uses `BULK INSERT` to import the `myTestSkipCol2.dat` data file into this view.</span></span>

 <span data-ttu-id="44eb6-178">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="44eb6-178">In the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>

```
CREATE VIEW v_myTestSkipCol AS
    SELECT Col1,Col3
    FROM myTestSkipCol;
GO

USE AdventureWorks2012;
GO
BULK INSERT v_myTestSkipCol
FROM 'C:\myTestSkipCol2.dat'
WITH (FORMATFILE='C:\myTestSkipCol2.xml');
GO
```

## <a name="see-also"></a><span data-ttu-id="44eb6-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44eb6-179">See Also</span></span>
 <span data-ttu-id="44eb6-180">[Bcp 公用程式](../../tools/bcp-utility.md) [BULK INSERT &#40;transact-sql&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) [OPENROWSET &#40;Transact-sql&#41;](/sql/t-sql/functions/openrowset-transact-sql) [使用格式檔案略過資料欄位 &#40;](use-a-format-file-to-skip-a-data-field-sql-server.md) SQL Server&#41;[使用格式檔案將資料表資料行對應至資料檔案欄位 &#40;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md) SQL Server&#41;[使用格式檔案大量匯入資料 &#40;](use-a-format-file-to-bulk-import-data-sql-server.md) SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="44eb6-180">[bcp Utility](../../tools/bcp-utility.md) [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) [Use a Format File to Skip a Data Field &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md) [Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md) [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)</span></span>


