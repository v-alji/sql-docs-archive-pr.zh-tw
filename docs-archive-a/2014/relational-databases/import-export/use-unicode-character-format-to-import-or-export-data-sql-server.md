---
title: 使用 Unicode 字元格式匯入或匯出資料 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], Unicode character
- Unicode [SQL Server], bulk importing and exporting
ms.assetid: 74342a11-c1c0-4746-b482-7f3537744a70
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 520ce1b4eed8dc11d6d3fe038969257aea1e90fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708393"
---
# <a name="use-unicode-character-format-to-import-or-export-data-sql-server"></a><span data-ttu-id="b5289-102">使用 Unicode 字元格式匯入或匯出資料 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b5289-102">Use Unicode Character Format to Import or Export Data (SQL Server)</span></span>
  <span data-ttu-id="b5289-103">使用含有擴充/DBCS 字元的資料檔在多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之間大量傳送資料時，建議使用 Unicode 字元格式。</span><span class="sxs-lookup"><span data-stu-id="b5289-103">Unicode character format is recommended for bulk transfer of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains extended/DBCS characters.</span></span> <span data-ttu-id="b5289-104">Unicode 字元資料格式可允許從伺服器匯出資料時所使用的字碼頁，與執行作業之用戶端所使用的字碼頁不同。</span><span class="sxs-lookup"><span data-stu-id="b5289-104">The Unicode character data format allows data to be exported from a server by using a code page that differs from the code page used by the client that is performing the operation.</span></span> <span data-ttu-id="b5289-105">在此情況下，使用 Unicode 字元格式具有下列優點：</span><span class="sxs-lookup"><span data-stu-id="b5289-105">In such cases, use of Unicode character format has the following advantages:</span></span>  
  
-   <span data-ttu-id="b5289-106">如果來源資料和目的地資料都是 Unicode 資料類型，使用 Unicode 字元格式可保留所有的字元資料。</span><span class="sxs-lookup"><span data-stu-id="b5289-106">If the source and destination data are Unicode data types, use of Unicode character format preserves all of the character data.</span></span>  
  
-   <span data-ttu-id="b5289-107">如果來源資料和目的地資料不是 Unicode 資料類型，使用 Unicode 字元格式可使來源資料中，擴充字元的遺失可能性降到最低 (該擴充字元無法在目的地中表示)。</span><span class="sxs-lookup"><span data-stu-id="b5289-107">if the source and destination data are not Unicode data types, use of Unicode character format minimizes the loss of extended characters in the source data that cannot be represented at the destination.</span></span>  
  
 <span data-ttu-id="b5289-108">Unicode 字元格式資料檔遵循 Unicode 檔案的慣例。</span><span class="sxs-lookup"><span data-stu-id="b5289-108">Unicode character format data files follow the conventions for Unicode files.</span></span> <span data-ttu-id="b5289-109">檔案的前兩個位元組是十六進位數字 0xFFFE。</span><span class="sxs-lookup"><span data-stu-id="b5289-109">The first two bytes of the file are hexadecimal numbers, 0xFFFE.</span></span> <span data-ttu-id="b5289-110">這些位元組可作為位元組順序的遮罩，指定先儲存或後儲存高順序的位元組至檔案中。</span><span class="sxs-lookup"><span data-stu-id="b5289-110">These bytes serve as byte-order marks, specifying whether the high-order byte is stored first or last in the file.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b5289-111">如果格式檔案要與 Unicode 字元資料檔案搭配使用，則所有的輸入欄位都必須是 Unicode 文字字串 (也就是固定大小或以字元結束的 Unicode 字串)。</span><span class="sxs-lookup"><span data-stu-id="b5289-111">For a format file to work with a Unicode character data file, all the input fields must be Unicode text strings (that is, either fixed-size or character-terminated Unicode strings).</span></span>  
  
 <span data-ttu-id="b5289-112">儲存在 Unicode 字元格式資料檔的 `sql_variant` 資料，其操作方式和在字元格式資料檔中相同，不同之處在於資料是儲存為 `nchar`，而非 `char` 資料。</span><span class="sxs-lookup"><span data-stu-id="b5289-112">The `sql_variant` data that is stored in a Unicode character-format data file operates in the same way it operates in a character-format data file, except that the data is stored as `nchar` instead of `char` data.</span></span> <span data-ttu-id="b5289-113">如需詳細資訊，請參閱 [定序和 Unicode 支援](../collations/collation-and-unicode-support.md)。</span><span class="sxs-lookup"><span data-stu-id="b5289-113">For more information about character format, see [Collation and Unicode Support](../collations/collation-and-unicode-support.md).</span></span>  
  
 <span data-ttu-id="b5289-114">若要使用 Unicode 字元格式預設值以外的欄位或資料列結束字元，請參閱[指定欄位與資料列結束字元 &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b5289-114">To use a field or row terminator other than the default that is provided with Unicode character format, see [Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).</span></span>  
  
## <a name="command-options-for-unicode-character-format"></a><span data-ttu-id="b5289-115">Unicode 字元格式的命令選項</span><span class="sxs-lookup"><span data-stu-id="b5289-115">Command Options for Unicode Character Format</span></span>  
 <span data-ttu-id="b5289-116">您可以使用**bcp**、BULK INSERT 或 INSERT ...，將 Unicode 字元格式資料匯入資料表中。SELECT \* FROM OPENROWSET (BULK ... ) 。對於**bcp**命令或 BULK INSERT 語句，您可以在命令列上指定資料格式。</span><span class="sxs-lookup"><span data-stu-id="b5289-116">You can import Unicode character format data into a table using **bcp**, BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...). For a **bcp** command or BULK INSERT statement, you can specify the data format on the command line.</span></span> <span data-ttu-id="b5289-117">對於 INSERT...SELECT \* FROM OPENROWSET(BULK...) 陳述式，您必須在格式檔案中指定資料格式。</span><span class="sxs-lookup"><span data-stu-id="b5289-117">For an INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement, you must specify the data format in a format file.</span></span>  
  
 <span data-ttu-id="b5289-118">下列命令列選項支援 Unicode 字元格式：</span><span class="sxs-lookup"><span data-stu-id="b5289-118">Unicode character format is supported by the following command line options:</span></span>  
  
|<span data-ttu-id="b5289-119">Command</span><span class="sxs-lookup"><span data-stu-id="b5289-119">Command</span></span>|<span data-ttu-id="b5289-120">選項</span><span class="sxs-lookup"><span data-stu-id="b5289-120">Option</span></span>|<span data-ttu-id="b5289-121">描述</span><span class="sxs-lookup"><span data-stu-id="b5289-121">Description</span></span>|  
|-------------|------------|-----------------|  
|<span data-ttu-id="b5289-122">**bcp**</span><span class="sxs-lookup"><span data-stu-id="b5289-122">**bcp**</span></span>|<span data-ttu-id="b5289-123">**-w**</span><span class="sxs-lookup"><span data-stu-id="b5289-123">**-w**</span></span>|<span data-ttu-id="b5289-124">使用 Unicode 字元格式。</span><span class="sxs-lookup"><span data-stu-id="b5289-124">Uses the Unicode character format.</span></span>|  
|<span data-ttu-id="b5289-125">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="b5289-125">BULK INSERT</span></span>|<span data-ttu-id="b5289-126">DATAFILETYPE **= '** widechar **'**</span><span class="sxs-lookup"><span data-stu-id="b5289-126">DATAFILETYPE **='** widechar **'**</span></span>|<span data-ttu-id="b5289-127">大量匯入資料時，使用 Unicode 字元格式。</span><span class="sxs-lookup"><span data-stu-id="b5289-127">Uses Unicode character format when bulk importing data.</span></span>|  
  
 <span data-ttu-id="b5289-128">如需詳細資訊，請參閱 [bcp 公用程式](../../tools/bcp-utility.md)、[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) 或 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5289-128">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), or [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5289-129">或者，您可以在格式檔案中按照每個欄位指定格式。</span><span class="sxs-lookup"><span data-stu-id="b5289-129">Alternatively, you can specify formatting on a per-field basis in a format file.</span></span> <span data-ttu-id="b5289-130">如需詳細資訊，請參閱 [匯入或匯出資料的格式檔案 &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="b5289-130">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b5289-131">範例</span><span class="sxs-lookup"><span data-stu-id="b5289-131">Examples</span></span>  
 <span data-ttu-id="b5289-132">下列範例示範如何使用 **bcp** 大量匯出 Unicode 字元資料，以及如何使用 BULK INSERT 大量匯入相同的資料。</span><span class="sxs-lookup"><span data-stu-id="b5289-132">The following examples demonstrate how to bulk export Unicode character data using **bcp** and to bulk import the same data using BULK INSERT.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="b5289-133">範例資料表</span><span class="sxs-lookup"><span data-stu-id="b5289-133">Sample Table</span></span>  
 <span data-ttu-id="b5289-134">下列範例會要求在 `myTestUniCharData` 結構描述底下的 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 範例資料庫中建立一個名為 `dbo` 的資料表。</span><span class="sxs-lookup"><span data-stu-id="b5289-134">The examples require that a table named `myTestUniCharData` table be created in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database under the `dbo` schema.</span></span> <span data-ttu-id="b5289-135">您必須先建立這個資料表，才能執行範例。</span><span class="sxs-lookup"><span data-stu-id="b5289-135">Before you can run the examples, you must create this table.</span></span> <span data-ttu-id="b5289-136">若要建立這個資料表，請在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行：</span><span class="sxs-lookup"><span data-stu-id="b5289-136">To create this table, in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestUniCharData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 <span data-ttu-id="b5289-137">若要擴展這個資料表及檢視產生的內容，請執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="b5289-137">To populate this table and view the resulting contents execute the following statements:</span></span>  
  
```  
INSERT INTO myTestUniCharData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3')   
        ,(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
  
```  
  
### <a name="using-bcp-to-bulk-export-unicode-character-data"></a><span data-ttu-id="b5289-138">使用 bcp 大量匯出 Unicode 字元資料</span><span class="sxs-lookup"><span data-stu-id="b5289-138">Using bcp to Bulk Export Unicode Character Data</span></span>  
 <span data-ttu-id="b5289-139">若要從資料表將資料匯出到資料檔案，請使用 **bcp** 配合 **out** 選項與下列限定詞：</span><span class="sxs-lookup"><span data-stu-id="b5289-139">To export data from the table to the data file, use **bcp** with the **out** option and the following qualifiers:</span></span>  
  
|<span data-ttu-id="b5289-140">限定詞</span><span class="sxs-lookup"><span data-stu-id="b5289-140">Qualifiers</span></span>|<span data-ttu-id="b5289-141">描述</span><span class="sxs-lookup"><span data-stu-id="b5289-141">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="b5289-142">**-w**</span><span class="sxs-lookup"><span data-stu-id="b5289-142">**-w**</span></span>|<span data-ttu-id="b5289-143">指定 Unicode 字元格式。</span><span class="sxs-lookup"><span data-stu-id="b5289-143">Specifies Unicode character format.</span></span>|  
|<span data-ttu-id="b5289-144">**-t** `,`</span><span class="sxs-lookup"><span data-stu-id="b5289-144">**-t** `,`</span></span>|<span data-ttu-id="b5289-145">指定逗號 (`,`) 作為欄位結束字元。</span><span class="sxs-lookup"><span data-stu-id="b5289-145">Specifies a comma (`,`) as the field terminator.</span></span><br /><br /> <span data-ttu-id="b5289-146">注意：預設欄位結束字元是索引標籤 Unicode 字元 ( \t) 。</span><span class="sxs-lookup"><span data-stu-id="b5289-146">Note: The default field terminator is the tab Unicode character (\t).</span></span> <span data-ttu-id="b5289-147">如需詳細資訊，請參閱 [指定欄位與資料列結束字元 &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b5289-147">For more information, see [Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).</span></span>|  
|<span data-ttu-id="b5289-148">**-T**</span><span class="sxs-lookup"><span data-stu-id="b5289-148">**-T**</span></span>|<span data-ttu-id="b5289-149">指定 **bcp** 公用程式使用整合式安全性的信任連接，連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b5289-149">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="b5289-150">如果未指定 **-T** ，則必須指定 **-U** 與 **-P** ，才能順利登入。</span><span class="sxs-lookup"><span data-stu-id="b5289-150">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>|  
  
 <span data-ttu-id="b5289-151">下列範例會將 Unicode 字元格式的資料，從 `myTestUniCharData` 資料表大量匯出到名為 `myTestUniCharData-w.Dat` 的新資料檔，並使用逗號 (`,`) 做為欄位結束字元。</span><span class="sxs-lookup"><span data-stu-id="b5289-151">The following example bulk exports data in Unicode character format from the `myTestUniCharData` table into a new data file named `myTestUniCharData-w.Dat` data file that uses the comma (`,`) as the field terminator.</span></span> <span data-ttu-id="b5289-152">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="b5289-152">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012..myTestUniCharData out C:\myTestUniCharData-w.Dat -w -t, -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-unicode-character-data"></a><span data-ttu-id="b5289-153">使用 BULK INSERT 大量匯入 Unicode 字元資料</span><span class="sxs-lookup"><span data-stu-id="b5289-153">Using BULK INSERT to Bulk Import Unicode Character Data</span></span>  
 <span data-ttu-id="b5289-154">下列範例會使用 `BULK INSERT`，將 `myTestUniCharData-w.Dat` 資料檔中的資料匯入至 `myTestUniCharData` 資料表。</span><span class="sxs-lookup"><span data-stu-id="b5289-154">The following example uses `BULK INSERT` to import the data in the `myTestUniCharData-w.Dat` data file into the `myTestUniCharData` table.</span></span> <span data-ttu-id="b5289-155">您必須在陳述式中宣告非預設的欄位結束字元 (`,`)。</span><span class="sxs-lookup"><span data-stu-id="b5289-155">The nondefault field terminator (`,`) must be declared in the statement.</span></span> <span data-ttu-id="b5289-156">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行：</span><span class="sxs-lookup"><span data-stu-id="b5289-156">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestUniCharData   
   FROM 'C:\myTestUniCharData-w.Dat'   
   WITH (  
      DATAFILETYPE='widechar',  
      FIELDTERMINATOR=','  
   );   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b5289-157">相關工作</span><span class="sxs-lookup"><span data-stu-id="b5289-157">Related Tasks</span></span>  
 <span data-ttu-id="b5289-158">**若要使用大量匯入或大量匯出的資料格式**</span><span class="sxs-lookup"><span data-stu-id="b5289-158">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="b5289-159">從舊版 SQL Server 匯入原生與字元格式資料</span><span class="sxs-lookup"><span data-stu-id="b5289-159">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="b5289-160">使用字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b5289-160">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="b5289-161">使用原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b5289-161">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="b5289-162">使用 Unicode 原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b5289-162">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="b5289-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5289-163">See Also</span></span>  
 <span data-ttu-id="b5289-164">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="b5289-164">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="b5289-165">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b5289-165">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="b5289-166">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b5289-166">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="b5289-167">[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b5289-167">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 [<span data-ttu-id="b5289-168">定序與 Unicode 支援</span><span class="sxs-lookup"><span data-stu-id="b5289-168">Collation and Unicode Support</span></span>](../collations/collation-and-unicode-support.md)  
  
  
