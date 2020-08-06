---
title: 準備大量匯出或匯入的資料 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], planning
- bulk importing [SQL Server], from a CSV file
- data formats [SQL Server], planning operations
- CSV files [SQL Server]
- quoted fields in CSV files [SQL Server]
ms.assetid: 783fd581-2e5f-496b-b79c-d4de1e09ea30
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4f2780a4eadfc27ed2db15881d676965fca81e35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706533"
---
# <a name="prepare-data-for-bulk-export-or-import-sql-server"></a><span data-ttu-id="7b4e2-102">準備大量匯出或匯入的資料 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7b4e2-102">Prepare Data for Bulk Export or Import (SQL Server)</span></span>
  <span data-ttu-id="7b4e2-103">本節討論關於大量匯出作業之規劃與大量匯入作業之需求的考量。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-103">This section discusses the considerations involved in planning for bulk-export operations and the requirements for bulk-import operations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b4e2-104">如果您不確定如何格式化資料檔以進行大量匯入，則可以使用 **bcp** 公用程式將資料從資料表匯出至資料檔。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-104">If you are uncertain about how to format a data file for bulk importing, you can use the **bcp** utility to export data from the table into a data file.</span></span> <span data-ttu-id="7b4e2-105">此檔案中每個資料欄位的格式會顯示將資料大量匯入對應資料表資料行所需的格式。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-105">The formatting of each data field in this file shows the formatting required to bulk import data into the corresponding table column.</span></span> <span data-ttu-id="7b4e2-106">請使用資料檔案欄位的相同資料格式。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-106">Use the same data formatting for fields of your data file.</span></span>  
  
## <a name="data-file-format-considerations-for-bulk-export"></a><span data-ttu-id="7b4e2-107">大量匯出的資料檔格式考量</span><span class="sxs-lookup"><span data-stu-id="7b4e2-107">Data-File Format Considerations for Bulk Export</span></span>  
 <span data-ttu-id="7b4e2-108">使用 **bcp** 命令執行大量匯出作業之前，請考慮下列事項：</span><span class="sxs-lookup"><span data-stu-id="7b4e2-108">Before you perform a bulk-export operation by using the **bcp** command, consider the following:</span></span>  
  
-   <span data-ttu-id="7b4e2-109">將資料匯出至檔案時， **bcp** 命令會使用指定的檔案名稱自動建立資料檔。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-109">When data is exported to a file, the **bcp** command creates the data file automatically by using the specified file name.</span></span> <span data-ttu-id="7b4e2-110">如果該檔名已在使用中，則大量複製到資料檔的資料會覆寫檔案現有的內容。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-110">If that file name is already in use, the data that is being bulk copied to the data file overwrites the existing contents of the file.</span></span>  
  
-   <span data-ttu-id="7b4e2-111">從資料表或檢視大量匯出到資料檔，需要大量複製的資料表或檢視之 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-111">Bulk export from a table or view to a data file requires SELECT permission on the table or view that is being bulk copied.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="7b4e2-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可使用平行掃描來擷取資料。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can use parallel scans to retrieve data.</span></span> <span data-ttu-id="7b4e2-113">因此，從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體大量匯出的資料表資料列，通常不能保證在資料檔中具有特定順序。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-113">Therefore, the table rows that are bulk exported in from an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are not ordinarily guaranteed to be in any specific order in the data file.</span></span> <span data-ttu-id="7b4e2-114">若要確定大量匯出的資料表資料列以特定順序顯示在資料檔中，請使用 **queryout** 選項從查詢進行大量匯出，以及指定 ORDER BY 子句。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-114">To make sure that bulk-exported table rows appear in a specific order in the data file, use the **queryout** option to bulk export from a query, and specify an ORDER BY clause.</span></span>  
  
## <a name="data-file-format-requirements-for-bulk-import"></a><span data-ttu-id="7b4e2-115">大量匯入的資料檔格式需求</span><span class="sxs-lookup"><span data-stu-id="7b4e2-115">Data-File Format Requirements for Bulk Import</span></span>  
 <span data-ttu-id="7b4e2-116">若要從資料檔匯入資料，該檔案必須符合下列基本需求：</span><span class="sxs-lookup"><span data-stu-id="7b4e2-116">To import data from a data file, the file must meet the following basic requirements:</span></span>  
  
-   <span data-ttu-id="7b4e2-117">資料必須為資料列與資料行的格式。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-117">The data must be in row and column format.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b4e2-118">因為在大量匯入處理期間可略過或重新排列資料行，資料檔的結構並不需要與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表的結構相同。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-118">The structure of the data file does not need to be identical to the structure of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table because columns can be skipped or reordered during the bulk-import process.</span></span>  
  
-   <span data-ttu-id="7b4e2-119">資料檔中的資料必須為支援的格式，如字元或原生格式。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-119">The data in the data file must be in a supported format such as character or native format.</span></span>  
  
-   <span data-ttu-id="7b4e2-120">資料的格式可以是字元或原生二進位格式，包括 Unicode。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-120">The data can be in character or native binary format including Unicode.</span></span>  
  
-   <span data-ttu-id="7b4e2-121">若要使用 **bcp** 命令、BULK INSERT 陳述式或 INSERT ...SELECT \* FROM OPENROWSET(BULK...) 陳述式來匯入資料，目的地資料表必須已經存在。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-121">To import data by using a **bcp** command, BULK INSERT statement, or INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement, the destination table must already exist.</span></span>  
  
-   <span data-ttu-id="7b4e2-122">資料檔中的每個欄位都必須與目標資料表中的對應資料行相容。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-122">Each field in the data file must be compatible with the corresponding column in the target table.</span></span> <span data-ttu-id="7b4e2-123">例如，無法將 `int` 欄位載入 `datetime` 資料行。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-123">For example, an `int` field cannot be loaded into a `datetime` column.</span></span> <span data-ttu-id="7b4e2-124">如需詳細資訊，請參閱[大量匯入或大量匯出的資料格式 &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md) 和[使用 bcp 指定相容性的資料格式 &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-124">For more information, see [Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md) and [Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7b4e2-125">若要指定從資料檔而非整個檔案中匯入資料列子集，您可以搭配使用 **bcp** 命令與 **-F** *first_row* 參數及/或 **-L** *last_row* 參數。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-125">To specify a subset of rows to import from a data file rather than the entire file, you can use a **bcp** command with the **-F** *first_row* switch and/or **-L** *last_row* switch.</span></span> <span data-ttu-id="7b4e2-126">如需相關資訊，請參閱 [bcp Utility](../../tools/bcp-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-126">For more information, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
-   <span data-ttu-id="7b4e2-127">若要從包含固定長度或固定寬度欄位的資料檔案匯入資料，您必須使用格式檔案。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-127">To import data from data files with fixed-length or fixed-width fields, you must use a format file.</span></span> <span data-ttu-id="7b4e2-128">如需詳細資訊，請參閱 [XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-128">For more information, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
-   <span data-ttu-id="7b4e2-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 大量匯入作業不支援逗號分隔值 (CSV) 檔案。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-129">Comma-separated value (CSV) files are not supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk-import operations.</span></span> <span data-ttu-id="7b4e2-130">不過，在某些情況下，CSV 檔案可用來當做資料檔案，以便將資料大量匯入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-130">However, in some cases, a CSV file can be used as the data file for a bulk import of data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7b4e2-131">請注意，CSV 檔案的欄位結束字元不必是逗號。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-131">Note that the field terminator of a CSV file does not have to be a comma.</span></span> <span data-ttu-id="7b4e2-132">為了能夠當做資料檔使用來進行大量匯入，CSV 檔案必須符合下列限制：</span><span class="sxs-lookup"><span data-stu-id="7b4e2-132">To be usable as a data file for bulk import, a CSV file must comply with the following restrictions:</span></span>  
  
    -   <span data-ttu-id="7b4e2-133">資料欄位永遠不會包含欄位結束字元。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-133">Data fields never contain the field terminator.</span></span>  
  
    -   <span data-ttu-id="7b4e2-134">引號 ("") 中會括住資料欄位內的所有值或是不括住任何值。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-134">Either none or all of the values in a data field are enclosed in quotation marks ("").</span></span>  
  
     <span data-ttu-id="7b4e2-135">若要從 [!INCLUDE[msCoName](../../includes/msconame-md.md)] FoxPro 或 Visual FoxPro 資料表 (.dbf) 檔案或 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 工作表 (.xls) 檔案大量匯入資料，您必須將該資料轉換成符合前述限制的 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-135">To bulk import data from a [!INCLUDE[msCoName](../../includes/msconame-md.md)] FoxPro or Visual FoxPro table (.dbf) file or a [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] worksheet (.xls) file, you would need to convert the data into a CSV file that complies to the preceding restrictions.</span></span> <span data-ttu-id="7b4e2-136">副檔名通常為 .csv。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-136">The file extension will typically be .csv.</span></span> <span data-ttu-id="7b4e2-137">然後，您就可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 大量匯入作業中，將此 .csv 檔案當做資料檔使用。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-137">You can then use the .csv file as a data file in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk-import operation.</span></span>  
  
     <span data-ttu-id="7b4e2-138">在 32 位元系統上，您可以搭配 OLE DB Provider for Jet 使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OPENROWSET [，將 CSV 資料匯入](/sql/t-sql/functions/openrowset-transact-sql) 資料表，而不需要將大量匯入最佳化。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-138">On 32-bit systems, it is possible to import CSV data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table without bulk-import optimizations by using [OPENROWSET](/sql/t-sql/functions/openrowset-transact-sql) with the OLE DB Provider for Jet.</span></span> <span data-ttu-id="7b4e2-139">Jet 會將文字檔視為資料表，其中包含與資料來源位於相同目錄中之 schema.ini 檔所定義的結構描述。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-139">Jet treats text files as tables, with the schema defined by a schema.ini file that is located in the same directory as the data source.</span></span>  <span data-ttu-id="7b4e2-140">若是 CSV 資料，schema.ini 檔中的其中一個參數將會是 "FORMAT=CSVDelimited"。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-140">For a CSV data, one of the parameters in the schema.ini file would be "FORMAT=CSVDelimited".</span></span> <span data-ttu-id="7b4e2-141">若要使用此解決方案，您需要了解 Jet Test IISAMm 如何運作 (其連接字串語法、schema.ini 用法、登錄設定選項等等)。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-141">To use this solution, you would need to understand how the Jet Test IISAMm operations-its connection string syntax, schema.ini usage, registry setting options, and so on).</span></span>  <span data-ttu-id="7b4e2-142">此資訊的最佳來源為 Microsoft Access 說明以及知識庫 (KB) 文件。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-142">The best sources of this information are Microsoft Access Help and Knowledge Base (KB) articles.</span></span> <span data-ttu-id="7b4e2-143">如需詳細資訊，請參閱[初始化文字資料來源驅動程式](https://docs.microsoft.com/office/client-developer/access/desktop-database-reference/initializing-the-text-data-source-driver)、[如何搭配安全保護 Access 資料庫的連結伺服器使用 SQL Server 7.0 分散式查詢](https://go.microsoft.com/fwlink/?LinkId=128504)、[如何：使用 Jet OLE DB Provider 4.0 連線到 ISAM 資料庫 ](https://go.microsoft.com/fwlink/?LinkId=128505)，以及[如何使用 Jet 提供者的文字 IIsam 開啟分隔的文字檔](https://go.microsoft.com/fwlink/?LinkId=128501)。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-143">For more information, see [Initializing the Text Data Source Driver](https://docs.microsoft.com/office/client-developer/access/desktop-database-reference/initializing-the-text-data-source-driver), [How To Use a SQL Server 7.0 Distributed Query with a Linked Server to Secured Access Databases](https://go.microsoft.com/fwlink/?LinkId=128504), [HOW TO: Use Jet OLE DB Provider 4.0 to Connect to ISAM Databases](https://go.microsoft.com/fwlink/?LinkId=128505), and [How To Open Delimited Text Files Using the Jet Provider's Text IIsam](https://go.microsoft.com/fwlink/?LinkId=128501).</span></span>  
  
 <span data-ttu-id="7b4e2-144">此外，將資料從資料檔大量匯入到資料表中需要下列：</span><span class="sxs-lookup"><span data-stu-id="7b4e2-144">In addition, the bulk import of data from a data file into a table requires the following:</span></span>  
  
-   <span data-ttu-id="7b4e2-145">使用者必須具有該資料表的 INSERT 與 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-145">Users must have INSERT and SELECT permissions on the table.</span></span> <span data-ttu-id="7b4e2-146">使用者在使用需要資料定義語言 (DDL) 作業的選項 (如停用條件約束) 時，也需要 ALTER TABLE 權限。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-146">Users also need ALTER TABLE permission when they use options that require data definition language (DDL) operations, such as disabling constraints.</span></span>  
  
-   <span data-ttu-id="7b4e2-147">當您使用 BULK INSERT 或 INSERT ...SELECT \* FROM OPENROWSET(BULK...) 來大量匯入資料時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序的安全性設定檔 (若使用者利用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供的登入來登入) 和用於委託安全性的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 登入，必須可存取資料檔以進行讀取作業。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-147">When you bulk import data by using BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...), the data file must be accessible for read operations by either the security profile of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process (if the user logs in using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provided login) or by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login that is used under delegated security.</span></span> <span data-ttu-id="7b4e2-148">此外，使用者必須具有 ADMINISTER BULK OPERATIONS 權限才能讀取檔案。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-148">Additionally, the user must have ADMINISTER BULK OPERATIONS permission to read the file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b4e2-149">系統並不支援大量匯入到資料分割檢視，而嘗試將資料大量匯入到資料分割檢視會失敗。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-149">Bulk importing into a partitioned view is unsupported, and attempts to bulk import data into a partitioned view fail.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="7b4e2-150">外部資源</span><span class="sxs-lookup"><span data-stu-id="7b4e2-150">External Resources</span></span>  
 [<span data-ttu-id="7b4e2-151">如何將 Excel 中的資料匯入到 SQL Server</span><span class="sxs-lookup"><span data-stu-id="7b4e2-151">How to import data from Excel to SQL Server</span></span>](https://support.microsoft.com/kb/321686)  
  
## <a name="change-history"></a><span data-ttu-id="7b4e2-152">變更記錄</span><span class="sxs-lookup"><span data-stu-id="7b4e2-152">Change History</span></span>  
  
|<span data-ttu-id="7b4e2-153">更新的內容</span><span class="sxs-lookup"><span data-stu-id="7b4e2-153">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="7b4e2-154">已加入使用 OLE DB Provider for Jet 匯入 CSV 資料的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7b4e2-154">Added information about using the OLE DB Provider for Jet to import CSV data.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b4e2-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b4e2-155">See Also</span></span>  
 <span data-ttu-id="7b4e2-156">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="7b4e2-156">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="7b4e2-157">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7b4e2-157">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="7b4e2-158">[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7b4e2-158">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="7b4e2-159">[使用字元格式匯入或匯出資料 &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7b4e2-159">[Use Character Format to Import or Export Data &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md) </span></span>  
 [<span data-ttu-id="7b4e2-160">使用原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7b4e2-160">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
  
