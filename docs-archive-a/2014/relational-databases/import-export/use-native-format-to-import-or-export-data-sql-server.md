---
title: 使用原生格式匯入或匯出資料 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- native data format [SQL Server]
- data formats [SQL Server], native
ms.assetid: eb279b2f-0f1f-428f-9b8f-2a7fc495b79f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab42ba3eb6468aac3da2fa780d371818c8776690
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708397"
---
# <a name="use-native-format-to-import-or-export-data-sql-server"></a><span data-ttu-id="b6b41-102">使用原生格式匯入或匯出資料 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b6b41-102">Use Native Format to Import or Export Data (SQL Server)</span></span>
  <span data-ttu-id="b6b41-103">在多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之間，使用不包含任何擴充/雙位元組字集 (DBCS) 字元的資料檔傳送大量資料時，建議使用原生格式。</span><span class="sxs-lookup"><span data-stu-id="b6b41-103">Native format is recommended when you bulk transfer data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using a data file that does not contain any extended/double-byte character set (DBCS) characters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6b41-104">若要在多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之間，使用包含擴充或 DBCS 字元的資料檔大量傳送資料，您應該使用 Unicode 原生格式。</span><span class="sxs-lookup"><span data-stu-id="b6b41-104">To bulk transfer data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains extended or DBCS characters, you should use the Unicode native format.</span></span> <span data-ttu-id="b6b41-105">如需詳細資訊，請參閱 [使用 Unicode 原生格式匯入或匯出資料 &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b6b41-105">For more information, see [Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="b6b41-106">原生格式會維持資料庫的原生資料類型。</span><span class="sxs-lookup"><span data-stu-id="b6b41-106">Native format maintains the native data types of a database.</span></span> <span data-ttu-id="b6b41-107">原生格式的目的是為了在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表之間進行資料的高速資料傳送。</span><span class="sxs-lookup"><span data-stu-id="b6b41-107">Native format is intended for high-speed data transfer of data between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span> <span data-ttu-id="b6b41-108">如果您使用格式檔案，則來源與目標資料表不需要相同。</span><span class="sxs-lookup"><span data-stu-id="b6b41-108">If you use a format file, the source and target tables do not need to be identical.</span></span> <span data-ttu-id="b6b41-109">資料傳送包含兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="b6b41-109">The data transfer involves two steps:</span></span>  
  
1.  <span data-ttu-id="b6b41-110">將來源資料表中的資料大量匯出到資料檔</span><span class="sxs-lookup"><span data-stu-id="b6b41-110">Bulk exporting the data from a source table into a data file</span></span>  
  
2.  <span data-ttu-id="b6b41-111">將資料檔中的資料大量匯入目標資料表</span><span class="sxs-lookup"><span data-stu-id="b6b41-111">Bulk importing the data from the data file into the target table</span></span>  
  
 <span data-ttu-id="b6b41-112">在相同資料表之間使用原生格式，可避免資料類型與字元格式間進行不需要的來回轉換，因而可節省時間及空間。</span><span class="sxs-lookup"><span data-stu-id="b6b41-112">The use of native format between identical tables avoids unnecessary conversion of data types to and from character format, saving time and space.</span></span> <span data-ttu-id="b6b41-113">不過，若要取得最佳的傳輸率，必須針對資料格式化做一些檢查。</span><span class="sxs-lookup"><span data-stu-id="b6b41-113">To achieve the optimum transfer rate, however, few checks are performed regarding data formatting.</span></span> <span data-ttu-id="b6b41-114">若要防止所載入的資料發生問題，請參閱下列限制清單。</span><span class="sxs-lookup"><span data-stu-id="b6b41-114">To prevent problems with the loaded data, see the following restrictions list.</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="b6b41-115">限制</span><span class="sxs-lookup"><span data-stu-id="b6b41-115">Restrictions</span></span>  
 <span data-ttu-id="b6b41-116">若要以原生格式成功匯入資料，請確定：</span><span class="sxs-lookup"><span data-stu-id="b6b41-116">To import data in native format successfully, ensure that:</span></span>  
  
-   <span data-ttu-id="b6b41-117">資料檔具有原生格式。</span><span class="sxs-lookup"><span data-stu-id="b6b41-117">The data file is in native format.</span></span>  
  
-   <span data-ttu-id="b6b41-118">目標資料表必須與資料檔相容 (具有正確的資料行數目、資料類型、長度、NULL 狀態等等)，否則您必須使用格式檔案，將每一個欄位對應到它的對應資料行。</span><span class="sxs-lookup"><span data-stu-id="b6b41-118">Either the target table must be compatible with the data file (having the correct number of columns, data type, length, NULL status, and so forth), or you must use a format file to map each field to its corresponding columns.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b6b41-119">如果您從與目標資料表不相符的檔案匯入資料，匯入作業或許會成功，但是插入目標資料表的資料值可能不正確。</span><span class="sxs-lookup"><span data-stu-id="b6b41-119">If you import data from a file that is mismatched with the target table, the import operation might succeed but the data values inserted into the target table are likely to be incorrect.</span></span> <span data-ttu-id="b6b41-120">原因是檔案中的資料是使用目標資料表的格式來解譯。</span><span class="sxs-lookup"><span data-stu-id="b6b41-120">This is because the data from the file is interpreted by using the format of the target table.</span></span> <span data-ttu-id="b6b41-121">因此，任何不相符都會導致插入的值不正確。</span><span class="sxs-lookup"><span data-stu-id="b6b41-121">Therefore, any mismatch results in the insertion of incorrect values.</span></span> <span data-ttu-id="b6b41-122">不過，這樣的不相符在任何情況下，都不會導致資料庫中發生邏輯或實體不一致性。</span><span class="sxs-lookup"><span data-stu-id="b6b41-122">However, under no circumstances can such a mismatch cause logical or physical inconsistencies in the database.</span></span>  
  
     <span data-ttu-id="b6b41-123">如需使用格式檔案的詳細資訊，請參閱[匯入或匯出資料的格式檔案 &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b6b41-123">For information on using format files, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="b6b41-124">成功的匯入作業不會損毀目標資料表。</span><span class="sxs-lookup"><span data-stu-id="b6b41-124">A successful import will not corrupt the target table.</span></span>  
  
## <a name="how-bcp-handles-data-in-native-format"></a><span data-ttu-id="b6b41-125">bcp 如何處理原生格式的資料</span><span class="sxs-lookup"><span data-stu-id="b6b41-125">How bcp Handles Data in Native Format</span></span>  
 <span data-ttu-id="b6b41-126">本節討論 **bcp** 公用程式如何匯出及匯入原生格式資料的特殊考量。</span><span class="sxs-lookup"><span data-stu-id="b6b41-126">This section discusses special considerations for how the **bcp** utility exports and imports data in native format.</span></span>  
  
-   <span data-ttu-id="b6b41-127">非字元資料</span><span class="sxs-lookup"><span data-stu-id="b6b41-127">Noncharacter data</span></span>  
  
     <span data-ttu-id="b6b41-128">bcp 公用程式使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 內部二進位資料格式，將資料表中的非字元資料寫入資料檔。</span><span class="sxs-lookup"><span data-stu-id="b6b41-128">The bcp utility uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] internal binary data format to write noncharacter data from a table to a data file.</span></span>  
  
-   <span data-ttu-id="b6b41-129">`char` 或 `varchar` 資料</span><span class="sxs-lookup"><span data-stu-id="b6b41-129">`char` or `varchar` data</span></span>  
  
     <span data-ttu-id="b6b41-130">在每個 `char` 或欄位的開頭 `varchar` ， **bcp**都會加入前置長度。</span><span class="sxs-lookup"><span data-stu-id="b6b41-130">At the beginning of each `char` or `varchar` field, **bcp** adds the prefix length.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="b6b41-131">使用原生模式時， **bcp**公用程式預設會將中的字元轉換 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 為 OEM 字元，然後再將它們複製到資料檔案。</span><span class="sxs-lookup"><span data-stu-id="b6b41-131">When native mode is used, by default, the **bcp** utility converts characters from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to OEM characters before it copies them to a data file.</span></span> <span data-ttu-id="b6b41-132">**Bcp**公用程式會先將資料檔案中的字元轉換為 ANSI 字元，然後再將它們大量匯入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中。</span><span class="sxs-lookup"><span data-stu-id="b6b41-132">The **bcp** utility converts characters from a data file to ANSI characters before it bulk imports them into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="b6b41-133">在進行這些轉換期間，可能會遺失擴充字元。</span><span class="sxs-lookup"><span data-stu-id="b6b41-133">During these conversions, extended character data can be lost.</span></span> <span data-ttu-id="b6b41-134">如有擴充字元，請使用 Unicode 原生格式或指定字碼頁。</span><span class="sxs-lookup"><span data-stu-id="b6b41-134">For extended characters, either use Unicode native format or specify a code page.</span></span>  
  
-   <span data-ttu-id="b6b41-135">`sql_variant` 資料</span><span class="sxs-lookup"><span data-stu-id="b6b41-135">`sql_variant` data</span></span>  
  
     <span data-ttu-id="b6b41-136">如果 `sql_variant` 資料以原生格式資料檔儲存為 SQLVARIANT，則資料會維持它所有的特性。</span><span class="sxs-lookup"><span data-stu-id="b6b41-136">If `sql_variant` data is stored as a SQLVARIANT in a native-format data file, the data maintains all of its characteristics.</span></span> <span data-ttu-id="b6b41-137">用來記錄每一個資料值的資料類型的中繼資料，會與資料值一起儲存。</span><span class="sxs-lookup"><span data-stu-id="b6b41-137">The metadata that records the data type of each data value is stored along with the data value.</span></span> <span data-ttu-id="b6b41-138">中繼資料是用來以目的地 `sql_variant` 資料行中相同的資料類型，重新建立資料值。</span><span class="sxs-lookup"><span data-stu-id="b6b41-138">This metadata is used to re-create the data value with the same data type in a destination `sql_variant` column.</span></span>  
  
     <span data-ttu-id="b6b41-139">如果目的地資料行的資料類型不是 `sql_variant`，則每一個資料值將依照隱含資料轉換的一般規則，轉換為目的地資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b6b41-139">If the data type of the destination column is not `sql_variant`, each data value is converted to the data type of the destination column, following the normal rules of implicit data conversion.</span></span> <span data-ttu-id="b6b41-140">如果資料轉換期間發生錯誤，將會回復目前批次。</span><span class="sxs-lookup"><span data-stu-id="b6b41-140">If an error occurs during data conversion, the current batch is rolled back.</span></span> <span data-ttu-id="b6b41-141">任何在 `char` 資料行之間傳送的 `varchar` 及 `sql_variant` 值，都可能有字碼頁轉換問題。</span><span class="sxs-lookup"><span data-stu-id="b6b41-141">Any `char` and `varchar` values that are transferred between `sql_variant` columns may have code page conversion issues.</span></span>  
  
     <span data-ttu-id="b6b41-142">如需資料轉換的詳細資訊，請參閱[資料類型轉換 &#40;Database Engine&#41;](/sql/t-sql/data-types/data-type-conversion-database-engine)。</span><span class="sxs-lookup"><span data-stu-id="b6b41-142">For more information about data conversion, see [Data Type Conversion &#40;Database Engine&#41;](/sql/t-sql/data-types/data-type-conversion-database-engine).</span></span>  
  
## <a name="command-options-for-native-format"></a><span data-ttu-id="b6b41-143">原生格式的命令選項</span><span class="sxs-lookup"><span data-stu-id="b6b41-143">Command Options for Native Format</span></span>  
 <span data-ttu-id="b6b41-144">您可以使用**bcp**、BULK INSERT 或 INSERT ...，將原生格式資料匯入資料表中。SELECT \* FROM OPENROWSET (BULK ... ) 。對於**bcp**命令或 BULK INSERT 語句，您可以在命令列上指定資料格式。</span><span class="sxs-lookup"><span data-stu-id="b6b41-144">You can import native format data into a table using **bcp**, BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...). For a **bcp** command or BULK INSERT statement, you can specify the data format on the command line.</span></span> <span data-ttu-id="b6b41-145">對於 INSERT...SELECT \* FROM OPENROWSET(BULK...) 陳述式，您必須在格式檔案中指定資料格式。</span><span class="sxs-lookup"><span data-stu-id="b6b41-145">For an INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement, you must specify the data format in a format file.</span></span>  
  
 <span data-ttu-id="b6b41-146">下列命令列選項支援原生格式：</span><span class="sxs-lookup"><span data-stu-id="b6b41-146">Native format is supported by the following command line options:</span></span>  
  
|<span data-ttu-id="b6b41-147">Command</span><span class="sxs-lookup"><span data-stu-id="b6b41-147">Command</span></span>|<span data-ttu-id="b6b41-148">選項</span><span class="sxs-lookup"><span data-stu-id="b6b41-148">Option</span></span>|<span data-ttu-id="b6b41-149">描述</span><span class="sxs-lookup"><span data-stu-id="b6b41-149">Description</span></span>|  
|-------------|------------|-----------------|  
|<span data-ttu-id="b6b41-150">**bcp**</span><span class="sxs-lookup"><span data-stu-id="b6b41-150">**bcp**</span></span>|<span data-ttu-id="b6b41-151">**-n**</span><span class="sxs-lookup"><span data-stu-id="b6b41-151">**-n**</span></span>|<span data-ttu-id="b6b41-152">使**bcp**公用程式使用資料的原生資料類型。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6b41-152">Causes the **bcp** utility to use the native data types of the data.<sup>1</sup></span></span>|  
|<span data-ttu-id="b6b41-153">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="b6b41-153">BULK INSERT</span></span>|<span data-ttu-id="b6b41-154">DATAFILETYPE **= '** native **'**</span><span class="sxs-lookup"><span data-stu-id="b6b41-154">DATAFILETYPE **='** native **'**</span></span>|<span data-ttu-id="b6b41-155">使用資料的原生或 widenative 資料類型。</span><span class="sxs-lookup"><span data-stu-id="b6b41-155">Uses the native or wide native data types of the data.</span></span> <span data-ttu-id="b6b41-156">請注意，如果利用了格式檔案指定資料類型，就不需要 DATAFILETYPE。</span><span class="sxs-lookup"><span data-stu-id="b6b41-156">Note that DATAFILETYPE is not needed if a format file specifies the data types.</span></span>|  
  
 <span data-ttu-id="b6b41-157"><sup>1</sup>若要將原生 (**-n**) 資料載入與舊版用戶端相容的格式 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請使用 **-V**參數。</span><span class="sxs-lookup"><span data-stu-id="b6b41-157"><sup>1</sup> To load native (**-n**) data to a format compatible with earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clients, use the **-V** switch.</span></span> <span data-ttu-id="b6b41-158">如需詳細資訊，請參閱 [從舊版 SQL Server 匯入原生與字元格式資料](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b6b41-158">For more information, see [Import Native and Character Format Data from Earlier Versions of SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md).</span></span>  
  
 <span data-ttu-id="b6b41-159">如需詳細資訊，請參閱 [bcp 公用程式](../../tools/bcp-utility.md)、[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) 或 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b6b41-159">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), or [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6b41-160">或者，您可以在格式檔案中按照每個欄位指定格式。</span><span class="sxs-lookup"><span data-stu-id="b6b41-160">Alternatively, you can specify formatting on a per-field basis in a format file.</span></span> <span data-ttu-id="b6b41-161">如需詳細資訊，請參閱 [匯入或匯出資料的格式檔案 &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="b6b41-161">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b6b41-162">範例</span><span class="sxs-lookup"><span data-stu-id="b6b41-162">Examples</span></span>  
 <span data-ttu-id="b6b41-163">下列範例示範如何使用 **bcp** 大量匯出原生資料，以及使用 BULK INSERT 大量匯入相同的資料。</span><span class="sxs-lookup"><span data-stu-id="b6b41-163">The following examples demonstrate how to bulk export native data using **bcp** and bulk import the same data using BULK INSERT.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="b6b41-164">範例資料表</span><span class="sxs-lookup"><span data-stu-id="b6b41-164">Sample Table</span></span>  
 <span data-ttu-id="b6b41-165">這些範例需要在 **AdventureWorks** 範例資料庫中，以 **dbo** 結構描述建立一個名為 **myTestNativeData** 的資料表。</span><span class="sxs-lookup"><span data-stu-id="b6b41-165">The examples require that a table named **myTestNativeData** table be created in the **AdventureWorks** sample database under the **dbo** schema.</span></span> <span data-ttu-id="b6b41-166">您必須先建立這個資料表，才能執行範例。</span><span class="sxs-lookup"><span data-stu-id="b6b41-166">Before you can run the examples, you must create this table.</span></span> <span data-ttu-id="b6b41-167">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行：</span><span class="sxs-lookup"><span data-stu-id="b6b41-167">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestNativeData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 <span data-ttu-id="b6b41-168">若要擴展這個資料表及檢視產生的內容，請執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="b6b41-168">To populate this table and view the resulting contents execute the following statements:</span></span>  
  
```  
INSERT INTO myTestNativeData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestNativeData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestNativeData  
  
```  
  
### <a name="using-bcp-to-bulk-export-native-data"></a><span data-ttu-id="b6b41-169">使用 bcp 大量匯出原生資料</span><span class="sxs-lookup"><span data-stu-id="b6b41-169">Using bcp to Bulk Export Native Data</span></span>  
 <span data-ttu-id="b6b41-170">若要從資料表將資料匯出到資料檔案，請使用 **bcp** 配合 **out** 選項與下列限定詞：</span><span class="sxs-lookup"><span data-stu-id="b6b41-170">To export data from the table to the data file, use **bcp** with the **out** option and the following qualifiers:</span></span>  
  
|<span data-ttu-id="b6b41-171">限定詞</span><span class="sxs-lookup"><span data-stu-id="b6b41-171">Qualifiers</span></span>|<span data-ttu-id="b6b41-172">描述</span><span class="sxs-lookup"><span data-stu-id="b6b41-172">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="b6b41-173">**-n**</span><span class="sxs-lookup"><span data-stu-id="b6b41-173">**-n**</span></span>|<span data-ttu-id="b6b41-174">指定原生資料類型。</span><span class="sxs-lookup"><span data-stu-id="b6b41-174">Specifies native data types.</span></span>|  
|<span data-ttu-id="b6b41-175">**-T**</span><span class="sxs-lookup"><span data-stu-id="b6b41-175">**-T**</span></span>|<span data-ttu-id="b6b41-176">指定 **bcp** 公用程式使用整合式安全性的信任連接，連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b6b41-176">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="b6b41-177">如果未指定 **-T** ，則必須指定 **-U** 與 **-P** ，才能順利登入。</span><span class="sxs-lookup"><span data-stu-id="b6b41-177">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>|  
  
 <span data-ttu-id="b6b41-178">下列範例會以原生格式從 `myTestNativeData` 資料表，將資料大量匯出至名為 `myTestNativeData-n.Dat` 資料檔的新資料檔。</span><span class="sxs-lookup"><span data-stu-id="b6b41-178">The following example bulk exports data in native format from the `myTestNativeData` table into a new data file named `myTestNativeData-n.Dat` data file.</span></span> <span data-ttu-id="b6b41-179">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="b6b41-179">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks..myTestNativeData out C:\myTestNativeData-n.Dat -n -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-native-data"></a><span data-ttu-id="b6b41-180">使用 BULK INSERT 大量匯入原生資料</span><span class="sxs-lookup"><span data-stu-id="b6b41-180">Using BULK INSERT to Bulk Import Native Data</span></span>  
 <span data-ttu-id="b6b41-181">下列範例使用 BULK INSERT 將 `myTestNativeData-n.Dat` 資料檔中的資料匯入至 `myTestNativeData` 資料表。</span><span class="sxs-lookup"><span data-stu-id="b6b41-181">The following example uses BULK INSERT to import the data in the `myTestNativeData-n.Dat` data file into the `myTestNativeData` table.</span></span> <span data-ttu-id="b6b41-182">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行：</span><span class="sxs-lookup"><span data-stu-id="b6b41-182">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestNativeData   
    FROM 'C:\myTestNativeData-n.Dat'   
   WITH (DATAFILETYPE='native');   
GO  
SELECT Col1,Col2,Col3 FROM myTestNativeData  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b6b41-183">相關工作</span><span class="sxs-lookup"><span data-stu-id="b6b41-183">Related Tasks</span></span>  
 <span data-ttu-id="b6b41-184">**若要使用大量匯入或大量匯出的資料格式**</span><span class="sxs-lookup"><span data-stu-id="b6b41-184">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="b6b41-185">從舊版 SQL Server 匯入原生與字元格式資料</span><span class="sxs-lookup"><span data-stu-id="b6b41-185">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="b6b41-186">使用字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b6b41-186">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="b6b41-187">使用 Unicode 字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b6b41-187">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="b6b41-188">使用 Unicode 原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b6b41-188">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="b6b41-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6b41-189">See Also</span></span>  
 <span data-ttu-id="b6b41-190">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="b6b41-190">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="b6b41-191">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b6b41-191">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="b6b41-192">[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b6b41-192">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="b6b41-193">[sql_variant &#40;Transact-SQL&#41;](/sql/t-sql/data-types/sql-variant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b6b41-193">[sql_variant &#40;Transact-SQL&#41;](/sql/t-sql/data-types/sql-variant-transact-sql) </span></span>  
 <span data-ttu-id="b6b41-194">[從舊版 SQL Server 匯入原生與字元格式資料](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b6b41-194">[Import Native and Character Format Data from Earlier Versions of SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md) </span></span>  
 <span data-ttu-id="b6b41-195">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b6b41-195">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 [<span data-ttu-id="b6b41-196">使用 Unicode 原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b6b41-196">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
  
