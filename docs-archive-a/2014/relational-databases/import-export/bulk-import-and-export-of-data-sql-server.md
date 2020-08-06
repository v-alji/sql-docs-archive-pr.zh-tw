---
title: 資料的大量匯入及匯出 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- exporting data
- bulk importing [SQL Server], about bulk importing
- data [SQL Server], bulk export and import
- transferring data
- importing data, (See also bulk importing [SQL Server])
- copying data [SQL Server]
- bulk exporting [SQL Server]
- importing data, bulk import
- copying data [SQL Server], bulk export and import
- exporting data,(See also bulk exporting [SQL Server])
- bulk exporting [SQL Server], about bulk exporting
- bulk importing [SQL Server]
- importing data
ms.assetid: 19049021-c048-44a2-b38d-186d9f9e4a65
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2b4e7611270135735cf3f7aada808a0a27ba927c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595000"
---
# <a name="bulk-import-and-export-of-data-sql-server"></a><span data-ttu-id="70df2-102">資料的大量匯入及匯出 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="70df2-102">Bulk Import and Export of Data (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="70df2-103">支援從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表匯出大量資料 (「大量資料」  )，以及將大量資料匯入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表或未分割的檢視。</span><span class="sxs-lookup"><span data-stu-id="70df2-103">supports exporting data in bulk (*bulk data*) from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table and importing bulk data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or nonpartitioned view.</span></span> <span data-ttu-id="70df2-104">大量匯入和大量匯出對於在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 與異質資料來源間有效傳送資料，是必要條件。</span><span class="sxs-lookup"><span data-stu-id="70df2-104">Bulk importing and bulk exporting are essential to efficient transfer data between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and heterogeneous data sources.</span></span> <span data-ttu-id="70df2-105">*「大量匯出」* 代表將資料從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表複製到資料檔。</span><span class="sxs-lookup"><span data-stu-id="70df2-105">*Bulk exporting* refers to copying data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table to a data file.</span></span> <span data-ttu-id="70df2-106">*「大量匯入」* 代表從資料檔載入資料至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="70df2-106">*Bulk importing* refers to loading data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="70df2-107">例如，您可以從 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 應用程式中將資料匯出至資料檔，然後將資料大量匯入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中。</span><span class="sxs-lookup"><span data-stu-id="70df2-107">For example, you can export data from a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel application to a data file and then bulk import that data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="70df2-108">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="70df2-108">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="70df2-109">大量匯入和大量匯出作業簡介</span><span class="sxs-lookup"><span data-stu-id="70df2-109">Introduction to Bulk Import and Bulk Export Operations</span></span>](#Intro)  
  
-   [<span data-ttu-id="70df2-110">相關工作</span><span class="sxs-lookup"><span data-stu-id="70df2-110">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="bulk-import-and-bulk-export-overview"></a><a name="Intro"></a><span data-ttu-id="70df2-111">大量匯入和大量匯出總覽</span><span class="sxs-lookup"><span data-stu-id="70df2-111">Bulk Import and Bulk Export Overview</span></span>  
 <span data-ttu-id="70df2-112">本節列出並簡要比較各種適用於大量匯入和匯出資料的方法。</span><span class="sxs-lookup"><span data-stu-id="70df2-112">This section lists and briefly compares the various methods that are available for bulk importing and exporting data.</span></span> <span data-ttu-id="70df2-113">本節也介紹格式檔案。</span><span class="sxs-lookup"><span data-stu-id="70df2-113">The section also introduces format files.</span></span>  
  
 <span data-ttu-id="70df2-114">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="70df2-114">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="70df2-115">大量匯入和匯出資料的方法</span><span class="sxs-lookup"><span data-stu-id="70df2-115">Methods for Bulk Importing and Exporting Data</span></span>](#MethodsForBuliIE)  
  
-   [<span data-ttu-id="70df2-116">格式檔案</span><span class="sxs-lookup"><span data-stu-id="70df2-116">Format Files</span></span>](#FFs)  
  
###  <a name="methods-for-bulk-importing-and-exporting-data"></a><a name="MethodsForBuliIE"></a><span data-ttu-id="70df2-117">大量匯入和匯出資料的方法</span><span class="sxs-lookup"><span data-stu-id="70df2-117">Methods for Bulk Importing and Exporting Data</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="70df2-118">支援從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表大量匯出資料，以及將資料大量匯入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表或未分割的檢視。</span><span class="sxs-lookup"><span data-stu-id="70df2-118">supports bulk exporting data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table and for bulk importing data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or nonpartitioned view.</span></span> <span data-ttu-id="70df2-119">有下列基本方法可用。</span><span class="sxs-lookup"><span data-stu-id="70df2-119">The following basic methods are available.</span></span>  
  
|<span data-ttu-id="70df2-120">方法</span><span class="sxs-lookup"><span data-stu-id="70df2-120">Method</span></span>|<span data-ttu-id="70df2-121">描述</span><span class="sxs-lookup"><span data-stu-id="70df2-121">Description</span></span>|<span data-ttu-id="70df2-122">匯入資料</span><span class="sxs-lookup"><span data-stu-id="70df2-122">Imports data</span></span>|<span data-ttu-id="70df2-123">匯出資料</span><span class="sxs-lookup"><span data-stu-id="70df2-123">Exports data</span></span>|  
|------------|-----------------|------------------|------------------|  
|[<span data-ttu-id="70df2-124">bcp 公用程式</span><span class="sxs-lookup"><span data-stu-id="70df2-124">bcp utility</span></span>](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)|<span data-ttu-id="70df2-125">可大量匯出和大量匯入資料並產生格式檔案的命令列公用程式 (Bcp.exe)。</span><span class="sxs-lookup"><span data-stu-id="70df2-125">A command-line utility (Bcp.exe) that bulk exports and bulk imports data and generates format files.</span></span>|<span data-ttu-id="70df2-126">是</span><span class="sxs-lookup"><span data-stu-id="70df2-126">Yes</span></span>|<span data-ttu-id="70df2-127">是</span><span class="sxs-lookup"><span data-stu-id="70df2-127">Yes</span></span>|  
|[<span data-ttu-id="70df2-128">BULK INSERT 陳述式</span><span class="sxs-lookup"><span data-stu-id="70df2-128">BULK INSERT statement</span></span>](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|<span data-ttu-id="70df2-129">[!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，可將資料直接從資料檔案匯入至資料庫資料表或非資料分割的檢視。</span><span class="sxs-lookup"><span data-stu-id="70df2-129">A [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that imports data directly from a data file into a database table or nonpartitioned view.</span></span>|<span data-ttu-id="70df2-130">是</span><span class="sxs-lookup"><span data-stu-id="70df2-130">Yes</span></span>|<span data-ttu-id="70df2-131">否</span><span class="sxs-lookup"><span data-stu-id="70df2-131">No</span></span>|  
|[<span data-ttu-id="70df2-132">INSERT ...SELECT \* FROM OPENROWSET(BULK...) 陳述式</span><span class="sxs-lookup"><span data-stu-id="70df2-132">INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement</span></span>](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|<span data-ttu-id="70df2-133">[!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，其指定 OPENROWSET(BULK…) 函數選取 INSERT 陳述式中的資料，以使用 OPENROWSET BULK 資料列集提供者，將資料大量匯入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="70df2-133">A [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that uses the OPENROWSET bulk rowset provider to bulk import data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table by specifying the OPENROWSET(BULK...) function to select data in an INSERT statement.</span></span>|<span data-ttu-id="70df2-134">是</span><span class="sxs-lookup"><span data-stu-id="70df2-134">Yes</span></span>|<span data-ttu-id="70df2-135">否</span><span class="sxs-lookup"><span data-stu-id="70df2-135">No</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="70df2-136">SQL Server 大量匯入作業不支援逗號分隔值 (CSV) 檔案。</span><span class="sxs-lookup"><span data-stu-id="70df2-136">Comma-separated value (CSV) files are not supported by SQL Server bulk-import operations.</span></span> <span data-ttu-id="70df2-137">不過，在某些情況下，CSV 檔案可用以當做資料檔，以便將資料大量匯入 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="70df2-137">However, in some cases, a CSV file can be used as the data file for a bulk import of data into SQL Server.</span></span> <span data-ttu-id="70df2-138">請注意，CSV 檔案的欄位結束字元不必是逗號。</span><span class="sxs-lookup"><span data-stu-id="70df2-138">Note that the field terminator of a CSV file does not have to be a comma.</span></span> <span data-ttu-id="70df2-139">如需詳細資訊，請參閱[準備大量匯出或匯入的資料 &#40;SQL Server&#41;](prepare-data-for-bulk-export-or-import-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="70df2-139">For more information, see [Prepare Data for Bulk Export or Import &#40;SQL Server&#41;](prepare-data-for-bulk-export-or-import-sql-server.md).</span></span>  
  
###  <a name="format-files"></a><a name="FFs"></a><span data-ttu-id="70df2-140">格式檔案</span><span class="sxs-lookup"><span data-stu-id="70df2-140">Format Files</span></span>  
 <span data-ttu-id="70df2-141">**Bcp**公用程式、BULK INSERT 和 INSERT .。。SELECT \* FROM OPENROWSET (BULK ... ) all 支援使用特殊*格式*檔案，該檔案會將每個欄位的格式資訊儲存在資料檔案中。</span><span class="sxs-lookup"><span data-stu-id="70df2-141">The **bcp** utility, BULK INSERT, and INSERT ... SELECT \* FROM OPENROWSET(BULK...) all support the use of a specialized *format file* that stores format information for each field in a data file.</span></span> <span data-ttu-id="70df2-142">格式檔案也可以包含對應的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="70df2-142">A format file might also contain information about the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="70df2-143">對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體大量匯出與大量匯入資料時，格式檔案可以提供所需的所有格式資訊。</span><span class="sxs-lookup"><span data-stu-id="70df2-143">The format file can be used to provide all the format information that is required to bulk export data from and bulk import data to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="70df2-144">格式檔案提供彈性方式，在匯入期間用於解譯資料檔中的資料，以及在匯出期間用於格式化資料檔中的資料。</span><span class="sxs-lookup"><span data-stu-id="70df2-144">Format files provide a flexible way to interpret data as it is in the data file during import, and also to format data in the data file during export.</span></span> <span data-ttu-id="70df2-145">這樣的彈性讓您不需撰寫特殊用途的程式碼來解譯資料，也不需因應 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或外部應用程式的特定需求將資料重新格式化。</span><span class="sxs-lookup"><span data-stu-id="70df2-145">This flexibility eliminates the need to write special-purpose code to interpret the data or reformat the data to the specific requirements of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the external application.</span></span> <span data-ttu-id="70df2-146">例如，如果您大量匯出的資料即將要載入到需要逗號分隔值的應用程式中，則可以使用格式檔案，在匯出的資料中插入逗號當做欄位結束字元。</span><span class="sxs-lookup"><span data-stu-id="70df2-146">For example, if you are bulk exporting data to be loaded into an application that requires comma-separated values, you can use a format file to insert commas as field terminators in the exported data.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="70df2-147">支援兩種類型的格式檔案：XML 格式檔案和非 XML 格式檔案。</span><span class="sxs-lookup"><span data-stu-id="70df2-147">supports two kinds of format files: XML format files and non-XML format files.</span></span>  
  
 <span data-ttu-id="70df2-148">**Bcp**公用程式是唯一可以產生格式檔案的工具。</span><span class="sxs-lookup"><span data-stu-id="70df2-148">The **bcp** utility is the only tool that can generate a format file.</span></span> <span data-ttu-id="70df2-149">如需詳細資訊，請參閱[建立格式檔案 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="70df2-149">For more information, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span> <span data-ttu-id="70df2-150">如需格式檔案的詳細資訊，請參閱[匯入或匯出資料的格式檔案 &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="70df2-150">For more information about format files, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70df2-151">萬一在大量匯出或匯入作業期間未提供格式檔案，您可以在命令列覆寫預設格式。</span><span class="sxs-lookup"><span data-stu-id="70df2-151">In cases when a format file is not supplied during a bulk export or import operations, you can override the default formatting at the command line.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="70df2-152">相關工作</span><span class="sxs-lookup"><span data-stu-id="70df2-152">Related Tasks</span></span>  
  
-   [<span data-ttu-id="70df2-153">使用 bcp 公用程式匯入及匯出大量資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-153">Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;</span></span>](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)  
  
-   [<span data-ttu-id="70df2-154">使用 BULK INSERT 或 OPENROWSET&#40;BULK...&#41; 匯入大量資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-154">Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;</span></span>](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)  
  
-   [<span data-ttu-id="70df2-155">大量匯入資料時保留識別值 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-155">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="70df2-156">大量匯入期間保留 Null 或使用預設值 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-156">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="70df2-157">準備大量匯出或匯入的資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-157">Prepare Data for Bulk Export or Import &#40;SQL Server&#41;</span></span>](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 <span data-ttu-id="70df2-158">**若要使用格式檔案**</span><span class="sxs-lookup"><span data-stu-id="70df2-158">**To use a format file**</span></span>  
  
-   [<span data-ttu-id="70df2-159">建立格式檔案 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-159">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="70df2-160">使用格式檔案大量匯入資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-160">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="70df2-161">使用格式檔案將資料表資料行對應至資料檔案欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-161">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [<span data-ttu-id="70df2-162">使用格式檔案略過資料欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-162">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="70df2-163">使用格式檔案略過資料表資料行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-163">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 <span data-ttu-id="70df2-164">**若要使用大量匯入或大量匯出的資料格式**</span><span class="sxs-lookup"><span data-stu-id="70df2-164">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="70df2-165">從舊版 SQL Server 匯入原生與字元格式資料</span><span class="sxs-lookup"><span data-stu-id="70df2-165">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="70df2-166">使用字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-166">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="70df2-167">使用原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-167">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="70df2-168">使用 Unicode 字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-168">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="70df2-169">使用 Unicode 原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-169">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 <span data-ttu-id="70df2-170">**若要在使用 bcp 時指定相容性的資料格式**</span><span class="sxs-lookup"><span data-stu-id="70df2-170">**To specify data formats for compatibility when using bcp**</span></span>  
  
1.  [<span data-ttu-id="70df2-171">指定欄位與資料列結束字元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-171">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
2.  [<span data-ttu-id="70df2-172">使用 bcp 指定資料檔的前置長度 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-172">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
3.  [<span data-ttu-id="70df2-173">使用 bcp 時指定檔案儲存類型 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-173">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="70df2-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70df2-174">See Also</span></span>  
 <span data-ttu-id="70df2-175">[大量匯入採用最低限度記錄的必要條件](prerequisites-for-minimal-logging-in-bulk-import.md) </span><span class="sxs-lookup"><span data-stu-id="70df2-175">[Prerequisites for Minimal Logging in Bulk Import](prerequisites-for-minimal-logging-in-bulk-import.md) </span></span>  
 <span data-ttu-id="70df2-176">[匯入或匯出資料的格式檔案 &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="70df2-176">[Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md) </span></span>  
 <span data-ttu-id="70df2-177">[大量匯入和匯出 XML 檔的範例 &#40;SQL Server&#41;](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="70df2-177">[Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md) </span></span>  
 <span data-ttu-id="70df2-178">[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="70df2-178">[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md) </span></span>  
 <span data-ttu-id="70df2-179">[複製資料庫至其他伺服器](../databases/copy-databases-to-other-servers.md) </span><span class="sxs-lookup"><span data-stu-id="70df2-179">[Copy Databases to Other Servers](../databases/copy-databases-to-other-servers.md) </span></span>  
 <span data-ttu-id="70df2-180">[執行 XML 資料的大量載入 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="70df2-180">[Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="70df2-181">[執行大量複製作業](../native-client/features/performing-bulk-copy-operations.md) </span><span class="sxs-lookup"><span data-stu-id="70df2-181">[Performing Bulk Copy Operations](../native-client/features/performing-bulk-copy-operations.md) </span></span>  
 <span data-ttu-id="70df2-182">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="70df2-182">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="70df2-183">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="70df2-183">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="70df2-184">[匯入或匯出資料的格式檔案 &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="70df2-184">[Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md) </span></span>  
 [<span data-ttu-id="70df2-185">OPENROWSET &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="70df2-185">OPENROWSET &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
