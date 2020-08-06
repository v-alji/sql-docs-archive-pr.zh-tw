---
title: 匯入或匯出資料的格式檔案 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], format files
- bulk importing [SQL Server], format files
- format files [SQL Server]
ms.assetid: b7b97d68-4336-4091-aee4-1941fab568e3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1143690f0322fef2612fde51eebcb7427ee237ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598386"
---
# <a name="format-files-for-importing-or-exporting-data-sql-server"></a><span data-ttu-id="14baf-102">匯入或匯出資料的格式檔案 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="14baf-102">Format Files for Importing or Exporting Data (SQL Server)</span></span>
  <span data-ttu-id="14baf-103">當您將資料大量匯入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表，或從資料表大量匯出資料時，可以使用「格式檔案」  來儲存大量匯出或大量匯入資料所需的所有格式資訊。</span><span class="sxs-lookup"><span data-stu-id="14baf-103">When you bulk import data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or bulk export data from a table, you can use a *format file* to store all the format information that is required to bulk export or bulk import data.</span></span> <span data-ttu-id="14baf-104">這包含相對於該資料表之資料檔中各欄位的格式資訊。</span><span class="sxs-lookup"><span data-stu-id="14baf-104">This includes format information for each field in a data file relative to that table.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="14baf-105">支援兩種類型的格式檔案：XML 格式和非 XML 格式檔案。</span><span class="sxs-lookup"><span data-stu-id="14baf-105">supports two types of format files: XML formats and non-XML format files.</span></span> <span data-ttu-id="14baf-106">非 XML 格式檔案和 XML 格式檔案都會將每個欄位的描述包含在資料檔中，而且 XML 格式檔案也包含對應資料表資料行的描述。</span><span class="sxs-lookup"><span data-stu-id="14baf-106">Both non-XML format files and XML format files contain descriptions of every field in a data file, and XML format files also contain descriptions of the corresponding table columns.</span></span> <span data-ttu-id="14baf-107">一般而言，XML 和非 XML 格式檔案可以互換使用，</span><span class="sxs-lookup"><span data-stu-id="14baf-107">Generally, XML and non-XML format files are interchangeable.</span></span> <span data-ttu-id="14baf-108">但是，仍建議您在新的格式檔案中使用 XML 語法，因為 XML 比非 XML 格式檔案多了一些優點。</span><span class="sxs-lookup"><span data-stu-id="14baf-108">However, we recommend that you use the XML syntax for new format files because they provide several advantages over non-XML format files.</span></span> <span data-ttu-id="14baf-109">如需詳細資訊，請參閱 [XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="14baf-109">For more information, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
 
  
##  <a name="benefits-of-format-files"></a><a name="Benefits"></a> <span data-ttu-id="14baf-110">格式檔案的優點</span><span class="sxs-lookup"><span data-stu-id="14baf-110">Benefits of Format Files</span></span>  
  
-   <span data-ttu-id="14baf-111">提供可用來寫入資料檔的彈性系統，幾乎不需要進行編輯，即可符合其他資料格式或從其他軟體中讀取資料檔。</span><span class="sxs-lookup"><span data-stu-id="14baf-111">Provides a flexible system for writing data files that requires little or no editing to comply with other data formats or to read data files from other software.</span></span>  
  
-   <span data-ttu-id="14baf-112">可讓您大量匯入資料，而不需要加入或刪除不需要的資料，或是重新排列資料檔中的現有資料。</span><span class="sxs-lookup"><span data-stu-id="14baf-112">Enables you to bulk import data without having to add or delete unnecessary data or to reorder existing data in the data file.</span></span> <span data-ttu-id="14baf-113">當資料檔欄位與資料表資料行不相符時，格式檔案就會特別有用。</span><span class="sxs-lookup"><span data-stu-id="14baf-113">Format files are particularly useful when a mismatch exists between fields in the data file and columns in the table.</span></span>  
  
##  <a name="examples-of-format-files"></a><a name="ExamplesOfFFs"></a> <span data-ttu-id="14baf-114">格式檔案的範例</span><span class="sxs-lookup"><span data-stu-id="14baf-114">Examples of Format Files</span></span>  
 <span data-ttu-id="14baf-115">下列範例顯示非 XML 格式檔案及 XML 格式檔案的配置。</span><span class="sxs-lookup"><span data-stu-id="14baf-115">The following examples show the layout of a non-XML format file and of an XML format file.</span></span> <span data-ttu-id="14baf-116">這些格式檔案會對應到 `HumanResources.myTeam` 範例資料庫中的 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="14baf-116">These format files correspond to the `HumanResources.myTeam` table in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="14baf-117">這個資料表包含四個資料行： `EmployeeID`、 `Name`、 `Title`和 `ModifiedDate`。</span><span class="sxs-lookup"><span data-stu-id="14baf-117">This table contains four columns: `EmployeeID`, `Name`, `Title`, and `ModifiedDate`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="14baf-118">如需此資料表及建立方式的相關資訊，請參閱 [HumanResources.myTeam 範例資料表 &#40;SQL Server&#41;](humanresources-myteam-sample-table-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="14baf-118">For information about this table and how to create it, see [HumanResources.myTeam Sample Table &#40;SQL Server&#41;](humanresources-myteam-sample-table-sql-server.md).</span></span>  
  
### <a name="a-using-a-non-xml-format-file"></a><span data-ttu-id="14baf-119">A.</span><span class="sxs-lookup"><span data-stu-id="14baf-119">A.</span></span> <span data-ttu-id="14baf-120">使用非 XML 格式檔案</span><span class="sxs-lookup"><span data-stu-id="14baf-120">Using a non-XML format file</span></span>  
 <span data-ttu-id="14baf-121">下列非 XML 格式檔案使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表的 `HumanResources.myTeam` 原生資料格式。</span><span class="sxs-lookup"><span data-stu-id="14baf-121">The following non-XML format file uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data format for the `HumanResources.myTeam` table.</span></span> <span data-ttu-id="14baf-122">這個格式檔案是使用下列 `bcp` 命令所建立。</span><span class="sxs-lookup"><span data-stu-id="14baf-122">This format file was created by using the following `bcp` command.</span></span>  
  
```  
bcp AdventureWorks.HumanResources.myTeam format nul -f myTeam.Fmt -n -T   
The contents of this format file are as follows: 9.0  
4  
1       SQLSMALLINT   0       2       ""   1     EmployeeID               ""  
2       SQLNCHAR      2       100     ""   2     Name                     SQL_Latin1_General_CP1_CI_AS  
3       SQLNCHAR      2       100     ""   3     Title                    SQL_Latin1_General_CP1_CI_AS  
4       SQLNCHAR      2       100     ""   4     Background               SQL_Latin1_General_CP1_CI_AS  
```  
  
 <span data-ttu-id="14baf-123">如需詳細資訊，請參閱 [非 XML 格式檔案 &#40;SQL Server&#41;](non-xml-format-files-sql-server.md)所支援的原始格式。</span><span class="sxs-lookup"><span data-stu-id="14baf-123">For more information, see [Non-XML Format Files &#40;SQL Server&#41;](non-xml-format-files-sql-server.md).</span></span>  
  
 
  
### <a name="b-using-an-xml-format-file"></a><span data-ttu-id="14baf-124">B.</span><span class="sxs-lookup"><span data-stu-id="14baf-124">B.</span></span> <span data-ttu-id="14baf-125">使用 XML 格式檔案</span><span class="sxs-lookup"><span data-stu-id="14baf-125">Using an XML format file</span></span>  
 <span data-ttu-id="14baf-126">下列 XML 格式檔案使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表的 `HumanResources.myTeam` 原生資料格式。</span><span class="sxs-lookup"><span data-stu-id="14baf-126">The following XML format file uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data format for the `HumanResources.myTeam` table.</span></span> <span data-ttu-id="14baf-127">這個格式檔案是使用下列 `bcp` 命令所建立。</span><span class="sxs-lookup"><span data-stu-id="14baf-127">This format file was created by using the following `bcp` command.</span></span>  
  
```  
bcp AdventureWorks.HumanResources.myTeam format nul -f myTeam.Xml -x -n -T   
```  
  
 <span data-ttu-id="14baf-128">格式檔案包含：</span><span class="sxs-lookup"><span data-stu-id="14baf-128">The format file contains:</span></span>  
  
```  
 <?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="NativePrefix" LENGTH="1"/>  
  <FIELD ID="2" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="4" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="EmployeeID" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Name" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="Title" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Background" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
 <span data-ttu-id="14baf-129">如需詳細資訊，請參閱 [XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="14baf-129">For more information, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  

  
##  <a name="when-is-a-format-file-required"></a><a name="WhenFFrequired"></a> <span data-ttu-id="14baf-130">何時需要格式檔案？</span><span class="sxs-lookup"><span data-stu-id="14baf-130">When Is a Format File Required?</span></span>  
 <span data-ttu-id="14baf-131">INSERT ...SELECT \* FROM OPENROWSET(BULK...) 陳述式永遠需要格式檔案。</span><span class="sxs-lookup"><span data-stu-id="14baf-131">An INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement always requires a format file.</span></span>  
  
-   <span data-ttu-id="14baf-132">至於 **bcp** 或 BULK INSERT，在簡單的情況下，可以選擇是否使用格式檔案，但很少會需要。</span><span class="sxs-lookup"><span data-stu-id="14baf-132">For **bcp** or BULK INSERT, in simple situations, using a format file is optional and rarely necessary.</span></span> <span data-ttu-id="14baf-133">不過，在複雜的大量匯入情況下，就經常需要格式檔案。</span><span class="sxs-lookup"><span data-stu-id="14baf-133">However, for complex bulk-import situations, a format file is frequently required.</span></span>  
  
 <span data-ttu-id="14baf-134">下列情況需要格式檔案：</span><span class="sxs-lookup"><span data-stu-id="14baf-134">Format files are required if:</span></span>  
  
-   <span data-ttu-id="14baf-135">多個具有不同結構描述的資料表，使用同一個資料檔做為來源。</span><span class="sxs-lookup"><span data-stu-id="14baf-135">The same data file is used as a source for multiple tables that have different schemas.</span></span>  
  
-   <span data-ttu-id="14baf-136">資料檔的欄位數目和目標資料表的資料行數目不同；例如：</span><span class="sxs-lookup"><span data-stu-id="14baf-136">The data file has a different number of fields that the target table has columns; for example:</span></span>  
  
    -   <span data-ttu-id="14baf-137">目標資料表至少有一個資料行，其中定義了預設值或允許 NULL。</span><span class="sxs-lookup"><span data-stu-id="14baf-137">The target table contains at least one column for which either a default value is defined or NULL is allowed.</span></span>  
  
    -   <span data-ttu-id="14baf-138">使用者在資料表中的一或多個資料行上沒有 SELECT/INSERT 權限。</span><span class="sxs-lookup"><span data-stu-id="14baf-138">The users do not have SELECT/INSERT permissions on one or more columns in the table.</span></span>  
  
    -   <span data-ttu-id="14baf-139">兩個以上具有不同結構描述的資料表，使用單一資料檔。</span><span class="sxs-lookup"><span data-stu-id="14baf-139">A single data file is used with two or more tables that have different schemas.</span></span>  
  
-   <span data-ttu-id="14baf-140">資料檔與資料表的資料行順序不同。</span><span class="sxs-lookup"><span data-stu-id="14baf-140">The column order is different for the data file and table.</span></span>  
  
-   <span data-ttu-id="14baf-141">資料檔的資料行之間，有不同的終止字元或前置長度。</span><span class="sxs-lookup"><span data-stu-id="14baf-141">The terminating characters or prefix lengths differ among the columns of the data file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="14baf-142">在沒有格式檔案的情況下，如果 **bcp** 命令指定資料格式參數 ( **-n**、 **-c**、 **-w**或 **-N**)，或 BULK INSERT 作業指定 DATAFILETYPE 選項，則會採用指定的資料格式來做為解譯資料檔欄位的預設方法。</span><span class="sxs-lookup"><span data-stu-id="14baf-142">In the absence of a format file, if a **bcp** command specifies a data-format switch (**-n**, **-c**, **-w**, or **-N**) or a BULK INSERT operation specifies the DATAFILETYPE option, the specified data format is used as the default method of interpreting the fields of the data file.</span></span>  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="14baf-143">相關工作</span><span class="sxs-lookup"><span data-stu-id="14baf-143">Related Tasks</span></span>  
  
-   [<span data-ttu-id="14baf-144">建立格式檔案 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="14baf-144">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="14baf-145">使用格式檔案大量匯入資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="14baf-145">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="14baf-146">使用格式檔案略過資料表資料行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="14baf-146">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="14baf-147">使用格式檔案略過資料欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="14baf-147">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="14baf-148">使用格式檔案將資料表資料行對應至資料檔案欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="14baf-148">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="14baf-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14baf-149">See Also</span></span>  
 <span data-ttu-id="14baf-150">[非 XML 格式檔案 &#40;SQL Server&#41;](non-xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="14baf-150">[Non-XML Format Files &#40;SQL Server&#41;](non-xml-format-files-sql-server.md) </span></span>  
 <span data-ttu-id="14baf-151">[XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="14baf-151">[XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span></span>  
 [<span data-ttu-id="14baf-152">大量匯入或大量匯出的資料格式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="14baf-152">Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;</span></span>](data-formats-for-bulk-import-or-bulk-export-sql-server.md)  
  
  
