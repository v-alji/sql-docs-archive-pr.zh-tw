---
title: 使用 bcp 公用程式匯入及匯出大量資料 (SQL Server) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], bcp utility
- bulk importing [SQL Server], bcp utility
- bcp utility [SQL Server], about bcp utility
ms.assetid: 73e949de-67a3-4c84-9735-7da1ad4ba34a
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 06/14/2017
ms.openlocfilehash: 7d1892b26f3c638a696d8ed15e739f56ac2e682f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598380"
---
# <a name="import-and-export-bulk-data-by-using-the-bcp-utility-sql-server"></a><span data-ttu-id="801a3-102">使用 bcp 公用程式匯入及匯出大量資料 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="801a3-102">Import and Export Bulk Data by Using the bcp Utility (SQL Server)</span></span>

<span data-ttu-id="801a3-103">本主題提供有關使用 [bcp 公用程式](../../tools/bcp-utility.md) ，從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫任何執行 SELECT 陳述式的位置 (包括資料分割檢視) 匯出資料的概觀。</span><span class="sxs-lookup"><span data-stu-id="801a3-103">This topic provides an overview for using the [bcp utility](../../tools/bcp-utility.md) to export data from anywhere in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database where a SELECT statement works, including partitioned views.</span></span>  
  
 <span data-ttu-id="801a3-104">bcp 公用程式 (Bcp.exe) 是使用大量複製程式 (BCP) API 的命令列工具。</span><span class="sxs-lookup"><span data-stu-id="801a3-104">The bcp utility (Bcp.exe) is a command-line tool that uses the Bulk Copy Program (BCP) API.</span></span> <span data-ttu-id="801a3-105">bcp 公用程式可執行以下工作：</span><span class="sxs-lookup"><span data-stu-id="801a3-105">The bcp utility performs the following tasks:</span></span>  
  
-   <span data-ttu-id="801a3-106">從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表將資料大量匯出到資料檔案。</span><span class="sxs-lookup"><span data-stu-id="801a3-106">Bulk exports data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table into a data file.</span></span>  
  
-   <span data-ttu-id="801a3-107">從查詢大量匯出資料。</span><span class="sxs-lookup"><span data-stu-id="801a3-107">Bulk exports data from a query.</span></span>  
  
-   <span data-ttu-id="801a3-108">從資料檔案將資料大量匯入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="801a3-108">Bulk imports data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
-   <span data-ttu-id="801a3-109">產生格式檔案。</span><span class="sxs-lookup"><span data-stu-id="801a3-109">Generates format files.</span></span>  
  
 <span data-ttu-id="801a3-110">bcp 公用程式是透過 **bcp** 命令進行存取。</span><span class="sxs-lookup"><span data-stu-id="801a3-110">The bcp utility is accessed by the **bcp** command.</span></span> <span data-ttu-id="801a3-111">除非使用預先存在的格式檔案，否則您必須了解資料表結構描述及其資料行的資料類型，才能使用 **bcp** 命令大量匯入資料。</span><span class="sxs-lookup"><span data-stu-id="801a3-111">To use the **bcp** command to bulk import data, you must understand the schema of the table and the data types of its columns, unless you are using a pre-existing format file.</span></span>  
  
 <span data-ttu-id="801a3-112">bcp 公用程式可以將資料從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表匯出至資料檔，以供其他程式使用。</span><span class="sxs-lookup"><span data-stu-id="801a3-112">The bcp utility can export data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table to a data file for use in other programs.</span></span> <span data-ttu-id="801a3-113">此公用程式也可以從另一個程式將資料匯入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表，通常是從另一個資料庫管理系統 (DBMS) 匯入。</span><span class="sxs-lookup"><span data-stu-id="801a3-113">The utility can also import data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table from another program, usually another database management system (DBMS).</span></span> <span data-ttu-id="801a3-114">資料會先從來源程式匯出到資料檔案，接著再以個別的作業，從資料檔案複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="801a3-114">The data is first exported from the source program to a data file and then, in a separate operation, copied from the data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="801a3-115">**bcp** 命令提供參數，用來指定資料檔的資料類型及其他資訊。</span><span class="sxs-lookup"><span data-stu-id="801a3-115">The **bcp** command provides switches that you use to specify the data type of the data file and other information.</span></span> <span data-ttu-id="801a3-116">如果未指定這些參數，命令會提示您輸入格式資訊，例如資料檔案中的資料欄位類型。</span><span class="sxs-lookup"><span data-stu-id="801a3-116">If these switches are not specified, the command prompts for formatting information, such as the type of data fields in a data file.</span></span> <span data-ttu-id="801a3-117">此命令會接著詢問您是否想要建立包含互動式回應的格式檔案。</span><span class="sxs-lookup"><span data-stu-id="801a3-117">The command then asks whether you want to create a format file that contains your interactive responses.</span></span> <span data-ttu-id="801a3-118">如果想要讓未來的大量匯入或大量匯出作業具有彈性，格式檔案通常會很有用。</span><span class="sxs-lookup"><span data-stu-id="801a3-118">If you want flexibility for future bulk-import or bulk-export operations, a format file is often useful.</span></span> <span data-ttu-id="801a3-119">您可以在稍後的 **bcp** 命令上，對相等的資料檔指定格式檔案。</span><span class="sxs-lookup"><span data-stu-id="801a3-119">You can specify the format file on later **bcp** commands for equivalent data files.</span></span> <span data-ttu-id="801a3-120">如需詳細資訊，請參閱[使用 bcp 時指定相容性的資料格式 &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="801a3-120">For more information, see [Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="801a3-121">bcp 公用程式是透過使用 ODBC 大量複製撰寫的。</span><span class="sxs-lookup"><span data-stu-id="801a3-121">The bcp utility is written by using the ODBC bulk-copy</span></span>  
  
 <span data-ttu-id="801a3-122">如需 **bcp** 命令語法的描述，請參閱 [bcp 公用程式](../../tools/bcp-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="801a3-122">For a description of the **bcp** command syntax, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="801a3-123">範例</span><span class="sxs-lookup"><span data-stu-id="801a3-123">Examples</span></span>

 <span data-ttu-id="801a3-124">如需 **bcp** 範例，請參閱：</span><span class="sxs-lookup"><span data-stu-id="801a3-124">For **bcp** examples, see:</span></span>  
  
-   [<span data-ttu-id="801a3-125">bcp 公用程式</span><span class="sxs-lookup"><span data-stu-id="801a3-125">bcp Utility</span></span>](../../tools/bcp-utility.md)  
  
-   [<span data-ttu-id="801a3-126">建立格式檔案 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="801a3-126">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="801a3-127">大量匯入與匯出 XML 文件的範例 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="801a3-127">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [<span data-ttu-id="801a3-128">大量匯入資料時保留識別值 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="801a3-128">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="801a3-129">大量匯入期間保留 Null 或使用預設值 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="801a3-129">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="801a3-130">指定欄位與資料列結束字元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="801a3-130">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
-   [<span data-ttu-id="801a3-131">使用格式檔案大量匯入資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="801a3-131">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="801a3-132">使用字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="801a3-132">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="801a3-133">使用原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="801a3-133">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="801a3-134">使用 Unicode 字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="801a3-134">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="801a3-135">使用 Unicode 原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="801a3-135">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  

## <a name="see-also"></a><span data-ttu-id="801a3-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="801a3-136">See Also</span></span>

<span data-ttu-id="801a3-137">[INSERT &#40;transact-sql&#41;](/sql/t-sql/statements/insert-transact-sql) 
[&#40;transact-sql&#41;](/sql/t-sql/queries/select-clause-transact-sql) 
 的 SELECT 子句[Bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="801a3-137">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)
[SELECT Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql)
[bcp Utility](../../tools/bcp-utility.md) </span></span>  
<span data-ttu-id="801a3-138">[準備大量匯入資料 &#40;SQL Server&#41;](prepare-to-bulk-import-data-sql-server.md) 
[BULK INSERT &#40;transact-sql&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) 
[大量匯入和匯出資料 &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) 
[OPENROWSET &#40;transact-sql&#41;](/sql/t-sql/functions/openrowset-transact-sql) 
[建立格式檔案 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="801a3-138">[Prepare to Bulk Import Data &#40;SQL Server&#41;](prepare-to-bulk-import-data-sql-server.md)
[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)
[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md)
[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)
[Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md)</span></span>