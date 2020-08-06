---
title: 使用 Unicode 原生格式匯入或匯出資料 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- Unicode [SQL Server], bulk importing and exporting
- data formats [SQL Server], Unicode native
ms.assetid: a6213308-f3d5-406e-9029-19d8bb3367f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: beae2f836de16dedf3be6d8c196910c53be02266
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708382"
---
# <a name="use-unicode-native-format-to-import-or-export-data-sql-server"></a><span data-ttu-id="c8b86-102">使用 Unicode 原生格式匯入或匯出資料 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c8b86-102">Use Unicode Native Format to Import or Export Data (SQL Server)</span></span>
  <span data-ttu-id="c8b86-103">當必須從某個 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝將資訊複製到其他安裝時，Unicode 原生格式很有用。</span><span class="sxs-lookup"><span data-stu-id="c8b86-103">Unicode native format is helpful when information must be copied from one [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation to another.</span></span> <span data-ttu-id="c8b86-104">對非字元的資料使用原生格式可節省時間，消除在資料類型與字元格式之間，不必要的來回轉換。</span><span class="sxs-lookup"><span data-stu-id="c8b86-104">The use of native format for noncharacter data saves time, eliminating unnecessary conversion of data types to and from character format.</span></span> <span data-ttu-id="c8b86-105">對所有字元資料使用 Unicode 字元格式，可以防止在使用不同字碼頁的伺服器之間大量傳送資料期間，失去任何擴充字元。</span><span class="sxs-lookup"><span data-stu-id="c8b86-105">The use of Unicode character format for all character data prevents loss of any extended characters during bulk transfer of data between servers using different code pages.</span></span> <span data-ttu-id="c8b86-106">任何大量匯入方法都可以讀取以 Unicode 原生格式表示的資料檔。</span><span class="sxs-lookup"><span data-stu-id="c8b86-106">A data file in Unicode native format can be read by any bulk-import method.</span></span>  
  
 <span data-ttu-id="c8b86-107">建議使用 Unicode 原生格式，在多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之間，使用包含擴充字元或 DBCS 字元的資料檔，大量傳送資料。</span><span class="sxs-lookup"><span data-stu-id="c8b86-107">Unicode native format is recommended for the bulk transfer of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains extended or DBCS characters.</span></span> <span data-ttu-id="c8b86-108">若是非字元資料，Unicode 原生格式會使用原生 (資料庫) 資料類型。</span><span class="sxs-lookup"><span data-stu-id="c8b86-108">For noncharacter data, Unicode native format uses native (database) data types.</span></span> <span data-ttu-id="c8b86-109">若是字元資料，如 `char`、`nchar`、`varchar`、`nvarchar`、`text`、`varchar(max)`、`nvarchar(max)` 及 `ntext`，Unicode 原生格式會使用 Unicode 字元資料格式。</span><span class="sxs-lookup"><span data-stu-id="c8b86-109">For character data, such as `char`, `nchar`, `varchar`, `nvarchar`, `text`, `varchar(max)`, `nvarchar(max)`, and `ntext`, the Unicode native format uses Unicode character data format.</span></span>  
  
 <span data-ttu-id="c8b86-110">以 SQLVARIANT 儲存在 Unicode 原生格式資料檔的 `sql_variant` 資料，會以它在原生格式資料檔的相同方式操作，不同處是 `char` 及 `varchar` 值會轉換為 `nchar` 及 `nvarchar`，這會讓受影響資料行所需的儲存體數量加倍。</span><span class="sxs-lookup"><span data-stu-id="c8b86-110">The `sql_variant` data that is stored as a SQLVARIANT in a Unicode native-format data file operates in the same manner as it does in a native-format data file, except that `char` and `varchar` values are converted to `nchar` and `nvarchar`, which doubles the amount of storage required for the affected columns.</span></span> <span data-ttu-id="c8b86-111">原始中繼資料會加以保留，而且在大量匯入資料表資料行時，這些值會轉換回它們的原始 `char` 及 `varchar` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="c8b86-111">The original metadata is preserved, and the values are converted back to their original `char` and `varchar` data type when bulk imported into a table column.</span></span>  
  
## <a name="command-options-for-unicode-native-format"></a><span data-ttu-id="c8b86-112">Unicode 原生格式的命令選項</span><span class="sxs-lookup"><span data-stu-id="c8b86-112">Command Options for Unicode Native Format</span></span>  
 <span data-ttu-id="c8b86-113">您可以使用**bcp**、BULK INSERT 或 INSERT ...，將 Unicode 原生格式資料匯入資料表中。SELECT \* FROM OPENROWSET (BULK ... ) 。對於**bcp**命令或 BULK INSERT 語句，您可以在命令列上指定資料格式。</span><span class="sxs-lookup"><span data-stu-id="c8b86-113">You can import Unicode native format data into a table using **bcp**, BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...). For a **bcp** command or BULK INSERT statement, you can specify the data format on the command line.</span></span> <span data-ttu-id="c8b86-114">對於 INSERT...SELECT \* FROM OPENROWSET(BULK...) 陳述式，您必須在格式檔案中指定資料格式。</span><span class="sxs-lookup"><span data-stu-id="c8b86-114">For an INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement, you must specify the data format in a format file.</span></span>  
  
 <span data-ttu-id="c8b86-115">下列選項支援 Unicode 原生格式：</span><span class="sxs-lookup"><span data-stu-id="c8b86-115">Unicode native format is supported by the following options:</span></span>  
  
|<span data-ttu-id="c8b86-116">Command</span><span class="sxs-lookup"><span data-stu-id="c8b86-116">Command</span></span>|<span data-ttu-id="c8b86-117">選項</span><span class="sxs-lookup"><span data-stu-id="c8b86-117">Option</span></span>|<span data-ttu-id="c8b86-118">描述</span><span class="sxs-lookup"><span data-stu-id="c8b86-118">Description</span></span>|  
|-------------|------------|-----------------|  
|<span data-ttu-id="c8b86-119">**bcp**</span><span class="sxs-lookup"><span data-stu-id="c8b86-119">**bcp**</span></span>|<span data-ttu-id="c8b86-120">**-N**</span><span class="sxs-lookup"><span data-stu-id="c8b86-120">**-N**</span></span>|<span data-ttu-id="c8b86-121">使**bcp**公用程式使用 Unicode 原生格式，其會使用原生 (資料庫) 資料類型，用於所有字元 (`char` 、、、、 `nchar` `varchar` `nvarchar` `text` 和 `ntext`) 資料的所有非字元資料和 Unicode 字元資料格式。</span><span class="sxs-lookup"><span data-stu-id="c8b86-121">Causes the **bcp** utility to use the Unicode native format, which uses native (database) data types for all noncharacter data and Unicode character data format for all character (`char`, `nchar`, `varchar`, `nvarchar`, `text`, and `ntext`) data.</span></span>|  
|<span data-ttu-id="c8b86-122">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="c8b86-122">BULK INSERT</span></span>|<span data-ttu-id="c8b86-123">DATAFILETYPE **= '** widenative **'**</span><span class="sxs-lookup"><span data-stu-id="c8b86-123">DATAFILETYPE **='** widenative **'**</span></span>|<span data-ttu-id="c8b86-124">當大量匯入資料時，使用 Unicode 原生格式。</span><span class="sxs-lookup"><span data-stu-id="c8b86-124">Use Unicode native format when bulk importing data.</span></span>|  
  
 <span data-ttu-id="c8b86-125">如需詳細資訊，請參閱 [bcp 公用程式](../../tools/bcp-utility.md)、[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) 或 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c8b86-125">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), or [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c8b86-126">或者，您可以在格式檔案中按照每個欄位指定格式。</span><span class="sxs-lookup"><span data-stu-id="c8b86-126">Alternatively, you can specify formatting on a per-field basis in a format file.</span></span> <span data-ttu-id="c8b86-127">如需詳細資訊，請參閱 [匯入或匯出資料的格式檔案 &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="c8b86-127">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c8b86-128">範例</span><span class="sxs-lookup"><span data-stu-id="c8b86-128">Examples</span></span>  
 <span data-ttu-id="c8b86-129">下列範例示範如何使用 **bcp** 大量匯出原生資料，以及使用 BULK INSERT 大量匯入相同的資料。</span><span class="sxs-lookup"><span data-stu-id="c8b86-129">The following examples demonstrate how to bulk export native data using **bcp** and bulk import the same data using BULK INSERT.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="c8b86-130">範例資料表</span><span class="sxs-lookup"><span data-stu-id="c8b86-130">Sample Table</span></span>  
 <span data-ttu-id="c8b86-131">以上範例需要在 **dbo** 結構描述下的 **AdventureWorks** 範例資料庫中，建立一個名為 **myTestUniNativeData** 的資料表。</span><span class="sxs-lookup"><span data-stu-id="c8b86-131">The examples require that a table named **myTestUniNativeData** table be created in the **AdventureWorks** sample database under the **dbo** schema.</span></span> <span data-ttu-id="c8b86-132">您必須先建立這個資料表，才能執行範例。</span><span class="sxs-lookup"><span data-stu-id="c8b86-132">Before you can run the examples, you must create this table.</span></span> <span data-ttu-id="c8b86-133">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行：</span><span class="sxs-lookup"><span data-stu-id="c8b86-133">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestUniNativeData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 <span data-ttu-id="c8b86-134">若要擴展這個資料表及檢視產生的內容，請執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="c8b86-134">To populate this table and view the resulting contents execute the following statements:</span></span>  
  
```  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData  
  
```  
  
### <a name="using-bcp-to-bulk-export-native-data"></a><span data-ttu-id="c8b86-135">使用 bcp 大量匯出原生資料</span><span class="sxs-lookup"><span data-stu-id="c8b86-135">Using bcp to Bulk Export Native Data</span></span>  
 <span data-ttu-id="c8b86-136">若要從資料表將資料匯出到資料檔案，請使用 **bcp** 配合 **out** 選項與下列限定詞：</span><span class="sxs-lookup"><span data-stu-id="c8b86-136">To export data from the table to the data file, use **bcp** with the **out** option and the following qualifiers:</span></span>  
  
|<span data-ttu-id="c8b86-137">限定詞</span><span class="sxs-lookup"><span data-stu-id="c8b86-137">Qualifiers</span></span>|<span data-ttu-id="c8b86-138">描述</span><span class="sxs-lookup"><span data-stu-id="c8b86-138">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="c8b86-139">**-N**</span><span class="sxs-lookup"><span data-stu-id="c8b86-139">**-N**</span></span>|<span data-ttu-id="c8b86-140">指定原生資料類型。</span><span class="sxs-lookup"><span data-stu-id="c8b86-140">Specifies native data types.</span></span>|  
|<span data-ttu-id="c8b86-141">**-T**</span><span class="sxs-lookup"><span data-stu-id="c8b86-141">**-T**</span></span>|<span data-ttu-id="c8b86-142">指定 **bcp** 公用程式使用整合式安全性的信任連接，連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c8b86-142">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="c8b86-143">如果未指定 **-T** ，則必須指定 **-U** 與 **-P** ，才能順利登入。</span><span class="sxs-lookup"><span data-stu-id="c8b86-143">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>|  
  
 <span data-ttu-id="c8b86-144">下列範例會以原生格式從 `myTestUniNativeData` 資料表，將資料大量匯出至名為 `myTestUniNativeData-N.Dat` 資料檔的新資料檔。</span><span class="sxs-lookup"><span data-stu-id="c8b86-144">The following example bulk exports data in native format from the `myTestUniNativeData` table into a new data file named `myTestUniNativeData-N.Dat` data file.</span></span> <span data-ttu-id="c8b86-145">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="c8b86-145">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks..myTestUniNativeData out C:\myTestUniNativeData-N.Dat -N -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-native-data"></a><span data-ttu-id="c8b86-146">使用 BULK INSERT 大量匯入原生資料</span><span class="sxs-lookup"><span data-stu-id="c8b86-146">Using BULK INSERT to Bulk Import Native Data</span></span>  
 <span data-ttu-id="c8b86-147">下列範例使用 BULK INSERT 將 `myTestUniNativeData-N.Dat` 資料檔中的資料匯入至 `myTestUniNativeData` 資料表。</span><span class="sxs-lookup"><span data-stu-id="c8b86-147">The following example uses BULK INSERT to import the data in the `myTestUniNativeData-N.Dat` data file into the `myTestUniNativeData` table.</span></span> <span data-ttu-id="c8b86-148">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行：</span><span class="sxs-lookup"><span data-stu-id="c8b86-148">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestUniNativeData   
    FROM 'C:\myTestUniNativeData-N.Dat'   
   WITH (DATAFILETYPE='widenative');   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="c8b86-149">相關工作</span><span class="sxs-lookup"><span data-stu-id="c8b86-149">Related Tasks</span></span>  
 <span data-ttu-id="c8b86-150">**若要使用大量匯入或大量匯出的資料格式**</span><span class="sxs-lookup"><span data-stu-id="c8b86-150">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="c8b86-151">從舊版 SQL Server 匯入原生與字元格式資料</span><span class="sxs-lookup"><span data-stu-id="c8b86-151">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="c8b86-152">使用字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c8b86-152">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="c8b86-153">使用原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c8b86-153">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="c8b86-154">使用 Unicode 字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c8b86-154">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="c8b86-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8b86-155">See Also</span></span>  
 <span data-ttu-id="c8b86-156">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="c8b86-156">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="c8b86-157">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c8b86-157">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="c8b86-158">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c8b86-158">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 [<span data-ttu-id="c8b86-159">資料類型 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c8b86-159">Data Types &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
