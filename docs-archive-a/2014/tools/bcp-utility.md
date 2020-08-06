---
title: bcp 公用程式 | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server]
- exporting data
- row exporting [SQL Server]
- copying data [SQL Server], bcp utility
- command prompt utilities [SQL Server], bcp
- tables [SQL Server], importing data
- column importing [SQL Server]
- bcp utility [SQL Server], command options
- file exporting [SQL Server]
- bulk copy [SQL Server]
- bcp utility [SQL Server], about bcp utility
- tables [SQL Server], exporting data
- row importing [SQL Server]
- importing data, bcp utility
- file importing [SQL Server]
- column exporting [SQL Server]
ms.assetid: c0af54f5-ca4a-4995-a3a4-0ce39c30ec38
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0ddc4c4e7023a83bfde9295a1410e7db5cb90b84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596417"
---
# <a name="bcp-utility"></a><span data-ttu-id="ab218-102">bcp 公用程式</span><span class="sxs-lookup"><span data-stu-id="ab218-102">bcp Utility</span></span>
  <span data-ttu-id="ab218-103">**Bcp**公用程式會 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 以使用者指定的格式，在實例與資料檔案之間大量複製資料。</span><span class="sxs-lookup"><span data-stu-id="ab218-103">The **bcp** utility bulk copies data between an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and a data file in a user-specified format.</span></span> <span data-ttu-id="ab218-104">您可以利用 **bcp** 公用程式，將大量的新資料列匯入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料表，或將資料表的資料匯出至資料檔案。</span><span class="sxs-lookup"><span data-stu-id="ab218-104">The **bcp** utility can be used to import large numbers of new rows into [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tables or to export data out of tables into data files.</span></span> <span data-ttu-id="ab218-105">除了搭配 **bcp** 選項使用之外，此公用程式不需要任何 [!INCLUDE[tsql](../includes/tsql-md.md)]方面的知識。</span><span class="sxs-lookup"><span data-stu-id="ab218-105">Except when used with the **queryout** option, the utility requires no knowledge of [!INCLUDE[tsql](../includes/tsql-md.md)].</span></span> <span data-ttu-id="ab218-106">若要將資料匯入資料表中，您必須使用專為這份資料表而建立的格式檔，或了解資料表的結構及其資料行的有效資料類型。</span><span class="sxs-lookup"><span data-stu-id="ab218-106">To import data into a table, you must either use a format file created for that table or understand the structure of the table and the types of data that are valid for its columns.</span></span>  
  
 <span data-ttu-id="ab218-107">![主題連結圖示](../../2014/database-engine/media/topic-link.gif "主題連結圖示") 針對用於 **bcp** 語法的語法慣例，請參閱 [Transact-SQL 語法慣例 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ab218-107">![Topic link icon](../../2014/database-engine/media/topic-link.gif "Topic link icon") For the syntax conventions that are used for the **bcp** syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab218-108">若您使用 **bcp** 備份資料，請建立格式檔案以記錄資料格式。</span><span class="sxs-lookup"><span data-stu-id="ab218-108">If you use **bcp** to back up your data, create a format file to record the data format.</span></span> <span data-ttu-id="ab218-109">**bcp** 資料檔案 不包含 任何結構描述或格式資訊，所以如果資料表或檢視表遭到卸除，而您又沒有格式檔案，即可能就無法匯入資料。</span><span class="sxs-lookup"><span data-stu-id="ab218-109">**bcp** data files do not include any schema or format information, so if a table or view is dropped and you do not have a format file, you may be unable to import the data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab218-110">語法</span><span class="sxs-lookup"><span data-stu-id="ab218-110">Syntax</span></span>  
  
```  
  
   bcp [database_name.] schema.{table_name | view_name | "query" {indata_file | outdata_file | queryoutdata_file | format nul}  
  
[-apacket_size]  
[-bbatch_size]  
[-c]  
[-C { ACP | OEM | RAW | code_page } ]  
[-ddatabase_name]  
[-eerr_file]  
[-E]  
[-fformat_file]  
[-Ffirst_row]  
[-h"hint [,...n]"]   
[-iinput_file]  
[-k]  
[-Kapplication_intent]  
[-Llast_row]  
[-mmax_errors]  
[-n]  
[-N]  
[-ooutput_file]  
[-Ppassword]  
[-q]  
[-rrow_term]  
[-R]  
[-S [server_name[\instance_name]]  
[-tfield_term]  
[-T]  
[-Ulogin_id]  
[-v]  
[-V (80 | 90 | 100 | 110)]  
[-w]  
[-x]  
/?  
```  
  
## <a name="arguments"></a><span data-ttu-id="ab218-111">引數</span><span class="sxs-lookup"><span data-stu-id="ab218-111">Arguments</span></span>  
 <span data-ttu-id="ab218-112">*data_file*</span><span class="sxs-lookup"><span data-stu-id="ab218-112">*data_file*</span></span>  
 <span data-ttu-id="ab218-113">這是資料檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="ab218-113">Is the full path of the data file.</span></span> <span data-ttu-id="ab218-114">當資料大量匯入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]時，資料檔案會包含要複製到指定資料表或檢視表的資料。</span><span class="sxs-lookup"><span data-stu-id="ab218-114">When data is bulk imported into [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the data file contains the data to be copied into the specified table or view.</span></span> <span data-ttu-id="ab218-115">當從 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]大量匯出資料時，資料檔案會包含從資料表或檢視表複製的資料。</span><span class="sxs-lookup"><span data-stu-id="ab218-115">When data is bulk exported from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the data file contains the data copied from the table or view.</span></span> <span data-ttu-id="ab218-116">路徑可以有 1 至 255 個字元。</span><span class="sxs-lookup"><span data-stu-id="ab218-116">The path can have from 1 through 255 characters.</span></span> <span data-ttu-id="ab218-117">資料檔案最多可以包含2個<sup>63</sup> -1 個數據列。</span><span class="sxs-lookup"><span data-stu-id="ab218-117">The data file can contain a maximum of 2<sup>63</sup> - 1 rows.</span></span>  
  
 <span data-ttu-id="ab218-118">*database_name*</span><span class="sxs-lookup"><span data-stu-id="ab218-118">*database_name*</span></span>  
 <span data-ttu-id="ab218-119">這是指定之資料表或檢視表所在的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ab218-119">Is the name of the database in which the specified table or view resides.</span></span> <span data-ttu-id="ab218-120">若未指定，這就是使用者的預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="ab218-120">If not specified, this is the default database for the user.</span></span>  
  
 <span data-ttu-id="ab218-121">您也可以使用 `d-` 明確指定資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ab218-121">You can also explicitly specify the database name with `d-`.</span></span>  
  
 <span data-ttu-id="ab218-122">**in** _data_file_  |  **out**_data_file_  |  **queryout**_data_file_  |  **format nul**</span><span class="sxs-lookup"><span data-stu-id="ab218-122">**in** _data_file_ | **out**_data_file_ | **queryout**_data_file_ | **format nul**</span></span>  
 <span data-ttu-id="ab218-123">請依照下列方式指定大量複製的方向：</span><span class="sxs-lookup"><span data-stu-id="ab218-123">Specifies the direction of the bulk copy, as follows:</span></span>  
  
-   <span data-ttu-id="ab218-124">**in** 會從檔案複製到資料庫資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="ab218-124">**in** copies from a file into the database table or view.</span></span>  
  
-   <span data-ttu-id="ab218-125">**out** 會從資料庫資料表或檢視複製到檔案。</span><span class="sxs-lookup"><span data-stu-id="ab218-125">**out** copies from the database table or view to a file.</span></span> <span data-ttu-id="ab218-126">若您指定現有的檔案，將會覆寫該檔案。</span><span class="sxs-lookup"><span data-stu-id="ab218-126">If you specify an existing file, the file is overwritten.</span></span> <span data-ttu-id="ab218-127">擷取資料時，請注意 **bcp** 公用程式會以 null 代表空白字串，並以空白字串代表 null 字串。</span><span class="sxs-lookup"><span data-stu-id="ab218-127">When extracting data, note that the **bcp** utility represents an empty string as a null and a null string as an empty string.</span></span>  
  
-   <span data-ttu-id="ab218-128">**queryout** 會從查詢複製資料，而且只有從查詢複製大量資料時才可指定。</span><span class="sxs-lookup"><span data-stu-id="ab218-128">**queryout** copies from a query and must be specified only when bulk copying data from a query.</span></span>  
  
-   <span data-ttu-id="ab218-129">**format**會根據指定的選項建立格式檔案 (**-n**、、 `-c` `-w` 或 **-n**) 以及資料表或視圖分隔符號。</span><span class="sxs-lookup"><span data-stu-id="ab218-129">**format** creates a format file based on the option specified (**-n**, `-c`, `-w`, or **-N**) and the table or view delimiters.</span></span> <span data-ttu-id="ab218-130">大量複製資料時， **bcp**命令可以參考格式檔案，讓您不需要以互動方式重新輸入格式資訊。</span><span class="sxs-lookup"><span data-stu-id="ab218-130">When bulk copying data, the **bcp** command can refer to a format file, which saves you from re-entering format information interactively.</span></span> <span data-ttu-id="ab218-131">**format** 選項需要 **-f** 選項；建立 XML 格式檔案也需要 **-x** 選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-131">The **format** option requires the **-f** option; creating an XML format file, also requires the **-x** option.</span></span> <span data-ttu-id="ab218-132">如需詳細資訊，請參閱[建立格式檔案 &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab218-132">For more information, see [Create a Format File &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md).</span></span> <span data-ttu-id="ab218-133">您必須將 **nul** 指定為值 (**format nul**)。</span><span class="sxs-lookup"><span data-stu-id="ab218-133">You must specify **nul** as the value (**format nul**).</span></span>  
  
 <span data-ttu-id="ab218-134">*owner*</span><span class="sxs-lookup"><span data-stu-id="ab218-134">*owner*</span></span>  
 <span data-ttu-id="ab218-135">這是資料表或檢視表的擁有者名稱。</span><span class="sxs-lookup"><span data-stu-id="ab218-135">Is the name of the owner of the table or view.</span></span> <span data-ttu-id="ab218-136">如果執行該作業的使用者擁有指定的資料表或檢視表，則可選擇是否要使用*owner* 。</span><span class="sxs-lookup"><span data-stu-id="ab218-136">*owner* is optional if the user performing the operation owns the specified table or view.</span></span> <span data-ttu-id="ab218-137">如果未指定 *owner* ，且執行作業的使用者並不擁有指定的資料表或檢視表，則 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會傳回錯誤訊息，並取消作業。</span><span class="sxs-lookup"><span data-stu-id="ab218-137">If *owner* is not specified and the user performing the operation does not own the specified table or view, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] returns an error message, and the operation is canceled.</span></span>  
  
 <span data-ttu-id="ab218-138">**"** 「_查詢_ **"** 」</span><span class="sxs-lookup"><span data-stu-id="ab218-138">**"** _query_ **"**</span></span>  
 <span data-ttu-id="ab218-139">這是一個傳回結果集的 [!INCLUDE[tsql](../includes/tsql-md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="ab218-139">Is a [!INCLUDE[tsql](../includes/tsql-md.md)] query that returns a result set.</span></span> <span data-ttu-id="ab218-140">如果查詢傳回多個結果集，則只會將第一個結果集複製到資料檔案中，並會忽略接下來的結果集。</span><span class="sxs-lookup"><span data-stu-id="ab218-140">If the query returns multiple result sets, only the first result set is copied to the data file; subsequent result sets are ignored.</span></span> <span data-ttu-id="ab218-141">請利用雙引號括住查詢，利用單引號括住內嵌在查詢中的任何項目。</span><span class="sxs-lookup"><span data-stu-id="ab218-141">Use double quotation marks around the query and single quotation marks around anything embedded in the query.</span></span> <span data-ttu-id="ab218-142">從查詢中複製大量資料時，也必須指定**queryout** 。</span><span class="sxs-lookup"><span data-stu-id="ab218-142">**queryout** must also be specified when bulk copying data from a query.</span></span>  
  
 <span data-ttu-id="ab218-143">只要在預存程序內參考的所有資料表在 bcp 陳述式執行之前就已存在，查詢就可以參考預存程序。</span><span class="sxs-lookup"><span data-stu-id="ab218-143">The query can reference a stored procedure as long as all tables referenced inside the stored procedure exist prior to executing the bcp statement.</span></span> <span data-ttu-id="ab218-144">例如，如果預存程序產生暫存資料表，則 **bcp** 陳述式會失敗，這是因為暫存資料表只可在執行階段使用，而無法在陳述式執行階段使用。</span><span class="sxs-lookup"><span data-stu-id="ab218-144">For example, if the stored procedure generates a temp table, the **bcp** statement fails because the temp table is available only at run time and not at statement execution time.</span></span> <span data-ttu-id="ab218-145">在此種情況下，請考慮將預存程序的結果插入資料表中，然後使用 **bcp** 將資料表的資料複製到資料檔案。</span><span class="sxs-lookup"><span data-stu-id="ab218-145">In this case, consider inserting the results of the stored procedure into a table and then use **bcp** to copy the data from the table into a data file.</span></span>  
  
 <span data-ttu-id="ab218-146">*table_name*</span><span class="sxs-lookup"><span data-stu-id="ab218-146">*table_name*</span></span>  
 <span data-ttu-id="ab218-147">這是將資料匯入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**in**) 時的目的地資料表名稱，以及從 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**out**) 匯出資料時的來源資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="ab218-147">Is the name of the destination table when importing data into [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**in**), and the source table when exporting data from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**out**).</span></span>  
  
 <span data-ttu-id="ab218-148">*view_name*</span><span class="sxs-lookup"><span data-stu-id="ab218-148">*view_name*</span></span>  
 <span data-ttu-id="ab218-149">這是將資料複製到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**in**) 時的目的地檢視表名稱，以及從 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**out**) 中複製資料時的來源檢視表名稱。</span><span class="sxs-lookup"><span data-stu-id="ab218-149">Is the name of the destination view when copying data into [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**in**), and the source view when copying data from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**out**).</span></span> <span data-ttu-id="ab218-150">只有所有資料行都參考相同資料表的檢視表，才能用來做為目的地檢視表。</span><span class="sxs-lookup"><span data-stu-id="ab218-150">Only views in which all columns refer to the same table can be used as destination views.</span></span> <span data-ttu-id="ab218-151">如需將資料複製到檢視表之限制的詳細資訊，請參閱 [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ab218-151">For more information on the restrictions for copying data into views, see [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql).</span></span>  
  
 <span data-ttu-id="ab218-152">**-a** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="ab218-152">**-a** _packet_size_</span></span>  
 <span data-ttu-id="ab218-153">指定伺服器所收送之每個網路封包的位元組數。</span><span class="sxs-lookup"><span data-stu-id="ab218-153">Specifies the number of bytes, per network packet, sent to and from the server.</span></span> <span data-ttu-id="ab218-154">您可以利用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (或 **sp_configure** 系統預存程序) 來設定伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-154">A server configuration option can be set by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (or the **sp_configure** system stored procedure).</span></span> <span data-ttu-id="ab218-155">但是使用此選項可以個別地覆寫伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-155">However, the server configuration option can be overridden on an individual basis by using this option.</span></span> <span data-ttu-id="ab218-156">*packet_size* 可以是 4096 到 65535 個位元組；預設值是 4096。</span><span class="sxs-lookup"><span data-stu-id="ab218-156">*packet_size* can be from 4096 to 65535 bytes; the default is 4096.</span></span>  
  
 <span data-ttu-id="ab218-157">增加封包大小可以增強大量複製作業的效能。</span><span class="sxs-lookup"><span data-stu-id="ab218-157">Increased packet size can enhance performance of bulk-copy operations.</span></span> <span data-ttu-id="ab218-158">若要求了較大的封包但無法為您授與該封包，便會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="ab218-158">If a larger packet is requested but cannot be granted, the default is used.</span></span> <span data-ttu-id="ab218-159">**bcp** 公用程式所產生的效能統計資料，會顯示所用的封包大小。</span><span class="sxs-lookup"><span data-stu-id="ab218-159">The performance statistics generated by the **bcp** utility show the packet size used.</span></span>  
  
 <span data-ttu-id="ab218-160">**-b** _batch_size_</span><span class="sxs-lookup"><span data-stu-id="ab218-160">**-b** _batch_size_</span></span>  
 <span data-ttu-id="ab218-161">指定每一批次匯入資料的資料列數。</span><span class="sxs-lookup"><span data-stu-id="ab218-161">Specifies the number of rows per batch of imported data.</span></span> <span data-ttu-id="ab218-162">每一批次會以個別交易的方式 (在認可之前匯入整個批次) 匯入及記錄。</span><span class="sxs-lookup"><span data-stu-id="ab218-162">Each batch is imported and logged as a separate transaction that imports the whole batch before being committed.</span></span> <span data-ttu-id="ab218-163">根據預設，資料檔案中的所有資料列是以一個批次匯入。</span><span class="sxs-lookup"><span data-stu-id="ab218-163">By default, all the rows in the data file are imported as one batch.</span></span> <span data-ttu-id="ab218-164">若要在多個批次之間分散資料列，請指定小於資料檔案之資料列數目的 *batch_size* 。</span><span class="sxs-lookup"><span data-stu-id="ab218-164">To distribute the rows among multiple batches, specify a *batch_size* that is smaller than the number of rows in the data file.</span></span> <span data-ttu-id="ab218-165">如果有任何批次的交易失敗，只回復目前批次的插入項。</span><span class="sxs-lookup"><span data-stu-id="ab218-165">If the transaction for any batch fails, only insertions from the current batch are rolled back.</span></span> <span data-ttu-id="ab218-166">之後的失敗不會影響已認可的交易所匯入的批次。</span><span class="sxs-lookup"><span data-stu-id="ab218-166">Batches already imported by committed transactions are unaffected by a later failure.</span></span>  
  
 <span data-ttu-id="ab218-167">請勿將此選項與 **-h "** ROWS_PER_BATCH \*\* = *`bb`* "\*\* 選項一起使用。</span><span class="sxs-lookup"><span data-stu-id="ab218-167">Do not use this option in conjunction with the **-h"** ROWS_PER_BATCH **=*`bb`*"** option.</span></span>  
  
 `-c`  
 <span data-ttu-id="ab218-168">利用字元資料類型來執行作業。</span><span class="sxs-lookup"><span data-stu-id="ab218-168">Performs the operation using a character data type.</span></span> <span data-ttu-id="ab218-169">並非每個欄位都有這個選項的提示。它會使用 `char` 做為儲存類型（沒有前置詞）和**\t** (定位字元) 做為欄位分隔符號，並使用**\r\n** (分行符號) 做為資料列結束字元。</span><span class="sxs-lookup"><span data-stu-id="ab218-169">This option does not prompt for each field; it uses `char` as the storage type, without prefixes and with **\t** (tab character) as the field separator and **\r\n** (newline character) as the row terminator.</span></span> <span data-ttu-id="ab218-170">`-c` 與 `-w` 不相容。</span><span class="sxs-lookup"><span data-stu-id="ab218-170">`-c` is not compatible with `-w`.</span></span>  
  
 <span data-ttu-id="ab218-171">如需詳細資訊，請參閱[使用 Unicode 字元格式匯入或匯出資料 &#40;SQL Server&#41;](../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab218-171">For more information, see [Use Character Format to Import or Export Data &#40;SQL Server&#41;](../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="ab218-172">**-C** { **ACP** | **OEM** | **RAW** | *code_page* }</span><span class="sxs-lookup"><span data-stu-id="ab218-172">**-C** { **ACP** | **OEM** | **RAW** | *code_page* }</span></span>  
 <span data-ttu-id="ab218-173">指定資料檔案中之資料的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="ab218-173">Specifies the code page of the data in the data file.</span></span> <span data-ttu-id="ab218-174">*code_page*只有當資料包含 `char` `varchar` `text` 字元值大於127或小於32的、或資料行時，code_page 才會相關。</span><span class="sxs-lookup"><span data-stu-id="ab218-174">*code_page* is relevant only if the data contains `char`, `varchar`, or `text` columns with character values greater than 127 or less than 32.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab218-175">我們建議您在格式檔案中，最好針對每一個資料行各指定一個定序名稱。</span><span class="sxs-lookup"><span data-stu-id="ab218-175">We recommend specifying a collation name for each column in a format file.</span></span>  
  
|<span data-ttu-id="ab218-176">字碼頁值</span><span class="sxs-lookup"><span data-stu-id="ab218-176">Code page value</span></span>|<span data-ttu-id="ab218-177">描述</span><span class="sxs-lookup"><span data-stu-id="ab218-177">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="ab218-178">ACP</span><span class="sxs-lookup"><span data-stu-id="ab218-178">ACP</span></span>|[!INCLUDE[vcpransi](../includes/vcpransi-md.md)]<span data-ttu-id="ab218-179">/Microsoft Windows (ISO 1252)。</span><span class="sxs-lookup"><span data-stu-id="ab218-179">/Microsoft Windows (ISO 1252).</span></span>|  
|<span data-ttu-id="ab218-180">OEM</span><span class="sxs-lookup"><span data-stu-id="ab218-180">OEM</span></span>|<span data-ttu-id="ab218-181">用戶端所用的預設字碼頁。</span><span class="sxs-lookup"><span data-stu-id="ab218-181">Default code page used by the client.</span></span> <span data-ttu-id="ab218-182">如果未指定 **-C** ，這是預設字碼頁。</span><span class="sxs-lookup"><span data-stu-id="ab218-182">This is the default code page used if **-C** is not specified.</span></span>|  
|<span data-ttu-id="ab218-183">RAW</span><span class="sxs-lookup"><span data-stu-id="ab218-183">RAW</span></span>|<span data-ttu-id="ab218-184">不會將字碼頁轉換成另一種字碼頁。</span><span class="sxs-lookup"><span data-stu-id="ab218-184">No conversion from one code page to another occurs.</span></span> <span data-ttu-id="ab218-185">這是最快的選項，因為不進行轉換。</span><span class="sxs-lookup"><span data-stu-id="ab218-185">This is the fastest option because no conversion occurs.</span></span>|  
|<span data-ttu-id="ab218-186">*code_page*</span><span class="sxs-lookup"><span data-stu-id="ab218-186">*code_page*</span></span>|<span data-ttu-id="ab218-187">特定字碼頁編號；如 850。</span><span class="sxs-lookup"><span data-stu-id="ab218-187">Specific code page number; for example, 850.</span></span><br /><br /> <span data-ttu-id="ab218-188">**&#42;&#42; 重要 &#42;&#42;** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]不支援字碼頁 65001 (UTF-8 編碼) 。</span><span class="sxs-lookup"><span data-stu-id="ab218-188">**&#42;&#42; Important &#42;&#42;** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not support code page 65001 (UTF-8 encoding).</span></span>|  
  
 <span data-ttu-id="ab218-189">`-d`*database_name*</span><span class="sxs-lookup"><span data-stu-id="ab218-189">`-d` *database_name*</span></span>  
 <span data-ttu-id="ab218-190">指定要連接的資料庫。</span><span class="sxs-lookup"><span data-stu-id="ab218-190">Specifies the database to connect to.</span></span> <span data-ttu-id="ab218-191">根據預設，bcp.exe 會連線到使用者的預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="ab218-191">By default, bcp.exe connects to the user's default database.</span></span> <span data-ttu-id="ab218-192">如果 `-d` *database_name*和三部分名稱 (*database_name*，做為第一個參數傳遞至 bcp.exe) ，則會發生錯誤，因為您無法指定資料庫名稱兩次。如果*database_name*的開頭是連字號 (-) 或斜線 (/) ，請勿在與資料庫名稱之間加上空格 `-d` 。</span><span class="sxs-lookup"><span data-stu-id="ab218-192">If `-d`*database_name* and a three part name (*database_name.schema.table*, passed as the first parameter to bcp.exe) is specified, an error will occur because you cannot specify the database name twice.If *database_name* begins with a hyphen (-) or a forward slash (/), do not add a space between `-d` and the database name.</span></span>  
  
 <span data-ttu-id="ab218-193">**-e** _err_file_</span><span class="sxs-lookup"><span data-stu-id="ab218-193">**-e** _err_file_</span></span>  
 <span data-ttu-id="ab218-194">指定錯誤檔的完整路徑，該錯誤檔用來儲存 **bcp** 公用程式無法從檔案傳送至資料庫的任何資料列。</span><span class="sxs-lookup"><span data-stu-id="ab218-194">Specifies the full path of an error file used to store any rows that the **bcp** utility cannot transfer from the file to the database.</span></span> <span data-ttu-id="ab218-195">**bcp** 命令所產生的錯誤訊息，會送往使用者的工作站。</span><span class="sxs-lookup"><span data-stu-id="ab218-195">Error messages from the **bcp** command go to the workstation of the user.</span></span> <span data-ttu-id="ab218-196">如果未使用這個選項，就不會建立錯誤檔。</span><span class="sxs-lookup"><span data-stu-id="ab218-196">If this option is not used, an error file is not created.</span></span>  
  
 <span data-ttu-id="ab218-197">如果 *err_file* 的開頭是連字號 (-) 或斜線 (/)，請勿在 **-e** 與 *err_file* 值之間加上空格。</span><span class="sxs-lookup"><span data-stu-id="ab218-197">If *err_file* begins with a hyphen (-) or a forward slash (/), do not include a space between **-e** and the *err_file* value.</span></span>  
  
 <span data-ttu-id="ab218-198">**-E**</span><span class="sxs-lookup"><span data-stu-id="ab218-198">**-E**</span></span>  
 <span data-ttu-id="ab218-199">指定識別欄位要使用匯入之資料檔案中的一個或多個識別值。</span><span class="sxs-lookup"><span data-stu-id="ab218-199">Specifies that identity value or values in the imported data file are to be used for the identity column.</span></span> <span data-ttu-id="ab218-200">如果未提供 **-E** ，就會略過匯入的資料檔案中此資料行的識別值，且 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會根據建立資料表期間所指定的初始值與遞增值，自動指派唯一值。</span><span class="sxs-lookup"><span data-stu-id="ab218-200">If **-E** is not given, the identity values for this column in the data file being imported are ignored, and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] automatically assigns unique values based on the seed and increment values specified during table creation.</span></span>  
  
 <span data-ttu-id="ab218-201">如果資料檔案中沒有資料表或檢視表中之識別欄位的值，請利用格式檔指定，在匯入資料時，應該略過資料表或檢視表中的識別欄位； [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會自動指派資料行的唯一值。</span><span class="sxs-lookup"><span data-stu-id="ab218-201">If the data file does not contain values for the identity column in the table or view, use a format file to specify that the identity column in the table or view should be skipped when importing data; [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] automatically assigns unique values for the column.</span></span> <span data-ttu-id="ab218-202">如需詳細資訊，請參閱 [DBCC CHECKIDENT &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ab218-202">For more information, see [DBCC CHECKIDENT &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql).</span></span>  
  
 <span data-ttu-id="ab218-203">**-E** 選項有特殊權限需求。</span><span class="sxs-lookup"><span data-stu-id="ab218-203">The **-E** option has a special permissions requirement.</span></span> <span data-ttu-id="ab218-204">如需詳細資訊，請參閱本主題稍後的＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="ab218-204">For more information, see "Remarks" later in this topic.</span></span>  
  
 <span data-ttu-id="ab218-205">**-f** _format_file_</span><span class="sxs-lookup"><span data-stu-id="ab218-205">**-f** _format_file_</span></span>  
 <span data-ttu-id="ab218-206">指定格式檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="ab218-206">Specifies the full path of a format file.</span></span> <span data-ttu-id="ab218-207">這個選項的意義會隨著使用它的環境而有所不同，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ab218-207">The meaning of this option depends on the environment in which it is used, as follows:</span></span>  
  
-   <span data-ttu-id="ab218-208">如果 **-f** 與 **format** 選項一起使用，會對指定的資料表或檢視表建立所指定的 *format_file* 。</span><span class="sxs-lookup"><span data-stu-id="ab218-208">If **-f** is used with the **format** option, the specified *format_file* is created for the specified table or view.</span></span> <span data-ttu-id="ab218-209">若要建立 XML 格式檔案，也請指定 **-x** 選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-209">To create an XML format file, also specify the **-x** option.</span></span> <span data-ttu-id="ab218-210">如需詳細資訊，請參閱[建立格式檔案 &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab218-210">For more information, see [Create a Format File &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md).</span></span>  
  
-   <span data-ttu-id="ab218-211">搭配 **in** 或 **out** 選項一起使用時， **-f** 需要現有的格式檔案。</span><span class="sxs-lookup"><span data-stu-id="ab218-211">If used with the **in** or **out** option, **-f** requires an existing format file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ab218-212">使用格式檔，其中的 **in** 或 **out** 選項為選擇性。</span><span class="sxs-lookup"><span data-stu-id="ab218-212">Using a format file in with the **in** or **out** option is optional.</span></span> <span data-ttu-id="ab218-213">在沒有 **-f**選項的情況下，如果未指定 **-n**、 `-c` 、 `-w` 或 **-n** ，命令會提示您輸入格式資訊，並可讓您將回應儲存 (其預設檔案名為 bcp.fmt) 的格式檔案中。</span><span class="sxs-lookup"><span data-stu-id="ab218-213">In the absence of the **-f** option, if **-n**, `-c`, `-w`, or **-N** is not specified, the command prompts for format information and lets you save your responses in a format file (whose default file name is Bcp.fmt).</span></span>  
  
 <span data-ttu-id="ab218-214">如果 *format_file* 的開頭是連字號 (-) 或斜線 (/)，請勿在 **-f** 與 *format_file* 值之間加上空格。</span><span class="sxs-lookup"><span data-stu-id="ab218-214">If *format_file* begins with a hyphen (-) or a forward slash (/), do not include a space between **-f** and the *format_file* value.</span></span>  
  
 <span data-ttu-id="ab218-215">**-F** _first_row_</span><span class="sxs-lookup"><span data-stu-id="ab218-215">**-F** _first_row_</span></span>  
 <span data-ttu-id="ab218-216">指定要從資料表匯出或從資料檔案匯入之第一個資料列的號碼。</span><span class="sxs-lookup"><span data-stu-id="ab218-216">Specifies the number of the first row to export from a table or import from a data file.</span></span> <span data-ttu-id="ab218-217">這個參數需要大於 ( # A0) 0 但小於 (\<) 或等於 (=) 總計數個數據列的值。</span><span class="sxs-lookup"><span data-stu-id="ab218-217">This parameter requires a value greater than (>) 0 but less than (\<) or equal to (=) the total number rows.</span></span> <span data-ttu-id="ab218-218">如果沒有這個參數，預設值是檔案中的第一個資料列。</span><span class="sxs-lookup"><span data-stu-id="ab218-218">In the absence of this parameter, the default is the first row of the file.</span></span>  
  
 <span data-ttu-id="ab218-219">*first_row* 可以是值高達 2^63-1 的正整數。</span><span class="sxs-lookup"><span data-stu-id="ab218-219">*first_row* can be a positive integer with a value up to 2^63-1.</span></span> <span data-ttu-id="ab218-220">**-F**_first_row_ 以 1 為基礎。</span><span class="sxs-lookup"><span data-stu-id="ab218-220">**-F**_first_row_ is 1-based.</span></span>  
  
 <span data-ttu-id="ab218-221">**-h"** _hint_[ **,**... *n*] **"**</span><span class="sxs-lookup"><span data-stu-id="ab218-221">**-h"** _hint_[ **,**... *n*] **"**</span></span>  
 <span data-ttu-id="ab218-222">指定將資料大量匯入資料表或檢視表期間，所要使用的一個或多個提示。</span><span class="sxs-lookup"><span data-stu-id="ab218-222">Specifies the hint or hints to be used during a bulk import of data into a table or view.</span></span>  
  
 <span data-ttu-id="ab218-223">ORDER\*\* (\*\* 資料_行_[ASC |DESC] [**，**.。。*n*]\*\*) \*\*</span><span class="sxs-lookup"><span data-stu-id="ab218-223">ORDER **(**_column_[ASC | DESC] [**,**...*n*]**)**</span></span>  
 <span data-ttu-id="ab218-224">資料檔案中之資料的排序順序。</span><span class="sxs-lookup"><span data-stu-id="ab218-224">The sort order of the data in the data file.</span></span> <span data-ttu-id="ab218-225">如果匯入資料時是依照資料表的叢集索引來排序，將可提升大量匯入的效能。</span><span class="sxs-lookup"><span data-stu-id="ab218-225">Bulk import performance is improved if the data being imported is sorted according to the clustered index on the table, if any.</span></span> <span data-ttu-id="ab218-226">如果不是依照叢集索引鍵的順序排序資料檔案，或是資料表沒有叢集索引，便會忽略 ORDER 子句。</span><span class="sxs-lookup"><span data-stu-id="ab218-226">If the data file is sorted in a different order, that is other than the order of a clustered index key, or if there is no clustered index on the table, the ORDER clause is ignored.</span></span> <span data-ttu-id="ab218-227">提供的資料行名稱必須是目的地資料表中的有效資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="ab218-227">The column names supplied must be valid column names in the destination table.</span></span> <span data-ttu-id="ab218-228">根據預設， **bcp** 會假設資料檔案沒有排序。</span><span class="sxs-lookup"><span data-stu-id="ab218-228">By default, **bcp** assumes the data file is unordered.</span></span> <span data-ttu-id="ab218-229">為了達到最佳的大量匯入效果， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 也會驗證匯入的資料是否已排序。</span><span class="sxs-lookup"><span data-stu-id="ab218-229">For optimized bulk import, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] also validates that the imported data is sorted.</span></span>  
  
 <span data-ttu-id="ab218-230">ROWS_PER_BATCH **=** _bb_</span><span class="sxs-lookup"><span data-stu-id="ab218-230">ROWS_PER_BATCH **=**_bb_</span></span>  
 <span data-ttu-id="ab218-231">每一批資料的資料列數目 (如 *bb*)。</span><span class="sxs-lookup"><span data-stu-id="ab218-231">Number of rows of data per batch (as *bb*).</span></span> <span data-ttu-id="ab218-232">在未指定 **-b** 時使用，結果會將整個資料檔案當做單一交易來傳給伺服器。</span><span class="sxs-lookup"><span data-stu-id="ab218-232">Used when **-b** is not specified, resulting in the entire data file being sent to the server as a single transaction.</span></span> <span data-ttu-id="ab218-233">伺服器根據 *bb*值，將大量載入最佳化。</span><span class="sxs-lookup"><span data-stu-id="ab218-233">The server optimizes the bulk load according to the value *bb*.</span></span> <span data-ttu-id="ab218-234">根據預設，ROWS_PER_BATCH 是未知的。</span><span class="sxs-lookup"><span data-stu-id="ab218-234">By default, ROWS_PER_BATCH is unknown.</span></span>  
  
 <span data-ttu-id="ab218-235">KILOBYTES_PER_BATCH **=** _cc_</span><span class="sxs-lookup"><span data-stu-id="ab218-235">KILOBYTES_PER_BATCH **=** _cc_</span></span>  
 <span data-ttu-id="ab218-236">每一批資料的近似 KB 數 (如 *cc*)。</span><span class="sxs-lookup"><span data-stu-id="ab218-236">Approximate number of kilobytes of data per batch (as *cc*).</span></span> <span data-ttu-id="ab218-237">依預設，KILOBYTES_PER_BATCH 是未知的。</span><span class="sxs-lookup"><span data-stu-id="ab218-237">By default, KILOBYTES_PER_BATCH is unknown.</span></span>  
  
 <span data-ttu-id="ab218-238">TABLOCK</span><span class="sxs-lookup"><span data-stu-id="ab218-238">TABLOCK</span></span>  
 <span data-ttu-id="ab218-239">指定在大量載入作業期間，取得大量更新資料表層級鎖定；否則，便取得資料列層級鎖定。</span><span class="sxs-lookup"><span data-stu-id="ab218-239">Specifies that a bulk update table-level lock is acquired for the duration of the bulk load operation; otherwise, a row-level lock is acquired.</span></span> <span data-ttu-id="ab218-240">這個提示會大幅提升效能，因為在大量複製作業期間保留鎖定，會減少競爭資料表鎖定的情況。</span><span class="sxs-lookup"><span data-stu-id="ab218-240">This hint significantly improves performance because holding a lock for the duration of the bulk-copy operation reduces lock contention on the table.</span></span> <span data-ttu-id="ab218-241">如果資料表沒有索引，且指定了 **TABLOCK** ，多個用戶端便可以同時載入這份資料表。</span><span class="sxs-lookup"><span data-stu-id="ab218-241">A table can be loaded concurrently by multiple clients if the table has no indexes and **TABLOCK** is specified.</span></span> <span data-ttu-id="ab218-242">根據預設，鎖定行為是由資料表選項 **table lock on bulk load**所決定。</span><span class="sxs-lookup"><span data-stu-id="ab218-242">By default, locking behavior is determined by the table option **table lock on bulk load**.</span></span>  
  
 <span data-ttu-id="ab218-243">CHECK_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="ab218-243">CHECK_CONSTRAINTS</span></span>  
 <span data-ttu-id="ab218-244">指定在大量匯入作業期間，必須檢查目標資料表或檢視表的所有條件約束。</span><span class="sxs-lookup"><span data-stu-id="ab218-244">Specifies that all constraints on the target table or view must be checked during the bulk-import operation.</span></span> <span data-ttu-id="ab218-245">當沒有 CHECK_CONSTRAINTS 提示時，會忽略所有 CHECK 和 FOREIGN KEY 條件約束，在作業之後，會將資料表的條件約束標記為不受信任。</span><span class="sxs-lookup"><span data-stu-id="ab218-245">Without the CHECK_CONSTRAINTS hint, any CHECK and FOREIGN KEY constraints are ignored, and after the operation the constraint on the table is marked as not-trusted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab218-246">一律強制實施 UNIQUE、PRIMARY KEY 和 NOT NULL 條件約束。</span><span class="sxs-lookup"><span data-stu-id="ab218-246">UNIQUE, PRIMARY KEY, and NOT NULL constraints are always enforced.</span></span>  
  
 <span data-ttu-id="ab218-247">在某些時候，您必須檢查整份資料表的條件約束。</span><span class="sxs-lookup"><span data-stu-id="ab218-247">At some point, you will need to check the constraints on the entire table.</span></span> <span data-ttu-id="ab218-248">如果在大量匯入作業之前，資料表不是空的，重新驗證條件約束的成本，可能會超出在累加資料上套用 CHECK 條件約束的成本。</span><span class="sxs-lookup"><span data-stu-id="ab218-248">If the table was nonempty before the bulk import operation, the cost of revalidating the constraint may exceed the cost of applying CHECK constraints to the incremental data.</span></span> <span data-ttu-id="ab218-249">因此，建議您在進行累加大量匯入期間，通常要啟用條件約束檢查。</span><span class="sxs-lookup"><span data-stu-id="ab218-249">Therefore, we recommend that normally you enable constraint checking during an incremental bulk import.</span></span>  
  
 <span data-ttu-id="ab218-250">如果輸入資料包含違反條件約束的資料列，您可能會想停用條件約束 (預設行為)。</span><span class="sxs-lookup"><span data-stu-id="ab218-250">A situation in which you might want constraints disabled (the default behavior) is if the input data contains rows that violate constraints.</span></span> <span data-ttu-id="ab218-251">當停用 CHECK 條件約束時，您可以先匯入資料，再利用 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式來移除無效的資料。</span><span class="sxs-lookup"><span data-stu-id="ab218-251">With CHECK constraints disabled, you can import the data and then use [!INCLUDE[tsql](../includes/tsql-md.md)] statements to remove data that is not valid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab218-252">**bcp** 現在會強制進行資料驗證與資料檢查，若針對資料檔案中無效的資料執行指令碼，這些資料驗證與檢查作業可能會導致指令碼失敗。</span><span class="sxs-lookup"><span data-stu-id="ab218-252">**bcp** now enforces data validation and data checks that might cause scripts to fail if they are executed on invalid data in a data file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab218-253">**-m** _max_errors_ 參數不適用於條件約束檢查。</span><span class="sxs-lookup"><span data-stu-id="ab218-253">The **-m** _max_errors_ switch does not apply to constraint checking.</span></span>  
  
 <span data-ttu-id="ab218-254">FIRE_TRIGGERS</span><span class="sxs-lookup"><span data-stu-id="ab218-254">FIRE_TRIGGERS</span></span>  
 <span data-ttu-id="ab218-255">利用 **in** 引數加以指定，任何定義於目的地資料表上的插入觸發程序，都會在大量複製作業期間執行。</span><span class="sxs-lookup"><span data-stu-id="ab218-255">Specified with the **in** argument, any insert triggers defined on the destination table will run during the bulk-copy operation.</span></span> <span data-ttu-id="ab218-256">如果未指定 FIRE_TRIGGERS，就不會執行任何插入觸發程序。</span><span class="sxs-lookup"><span data-stu-id="ab218-256">If FIRE_TRIGGERS is not specified, no insert triggers will run.</span></span> <span data-ttu-id="ab218-257">**out**、 **queryout**和 **format** 引數會略過 FIRE_TRIGGERS。</span><span class="sxs-lookup"><span data-stu-id="ab218-257">FIRE_TRIGGERS is ignored for the **out**, **queryout**, and **format** arguments.</span></span>  
  
 <span data-ttu-id="ab218-258">**-i** _input_file_</span><span class="sxs-lookup"><span data-stu-id="ab218-258">**-i** _input_file_</span></span>  
 <span data-ttu-id="ab218-259">指定回應檔的名稱，其中包含在使用互動模式執行大量複製時，每個資料欄位的命令提示字元問題的回應 (**-n**、、 `-c` `-w` 或 **-n**未指定) 。</span><span class="sxs-lookup"><span data-stu-id="ab218-259">Specifies the name of a response file, containing the responses to the command prompt questions for each data field when a bulk copy is being performed using interactive mode (**-n**, `-c`, `-w`, or **-N** not specified).</span></span>  
  
 <span data-ttu-id="ab218-260">如果 *input_file* 的開頭是連字號 (-) 或斜線 (/)，請勿在 **-i** 與 *input_file* 值之間加上空格。</span><span class="sxs-lookup"><span data-stu-id="ab218-260">If *input_file* begins with a hyphen (-) or a forward slash (/), do not include a space between **-i** and the *input_file* value.</span></span>  
  
 <span data-ttu-id="ab218-261">**-k**</span><span class="sxs-lookup"><span data-stu-id="ab218-261">**-k**</span></span>  
 <span data-ttu-id="ab218-262">指定空白資料行在作業過程中應保持 Null 值，而非保有插入之資料行的任何預設值。</span><span class="sxs-lookup"><span data-stu-id="ab218-262">Specifies that empty columns should retain a null value during the operation, rather than have any default values for the columns inserted.</span></span> <span data-ttu-id="ab218-263">如需詳細資訊，請參閱[大量匯入期間保留 Null 或使用預設值 &#40;SQL Server&#41;](../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab218-263">For more information, see [Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;](../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md).</span></span>  
  
 <span data-ttu-id="ab218-264">**-K** _application_intent_</span><span class="sxs-lookup"><span data-stu-id="ab218-264">**-K** _application_intent_</span></span>  
 <span data-ttu-id="ab218-265">宣告連接到伺服器時的應用程式工作負載類型。</span><span class="sxs-lookup"><span data-stu-id="ab218-265">Declares the application workload type when connecting to a server.</span></span> <span data-ttu-id="ab218-266">唯一可能的值是 **ReadOnly**。</span><span class="sxs-lookup"><span data-stu-id="ab218-266">The only value that is possible is **ReadOnly**.</span></span> <span data-ttu-id="ab218-267">若未指定 **-K**，bcp 公用程式將不會支援在 AlwaysOn 可用性群組中連接次要複本。</span><span class="sxs-lookup"><span data-stu-id="ab218-267">If **-K** is not specified, the bcp utility will not support connectivity to a secondary replica in an AlwaysOn availability group.</span></span> <span data-ttu-id="ab218-268">如需詳細資訊，請參閱[Active 次要：可讀取的次要複本 (AlwaysOn 可用性群組) ](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="ab218-268">For more information, see [Active Secondaries: Readable Secondary Replicas (AlwaysOn Availability Groups)](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="ab218-269">**-L** _last_row_</span><span class="sxs-lookup"><span data-stu-id="ab218-269">**-L** _last_row_</span></span>  
 <span data-ttu-id="ab218-270">指定要從資料表匯出或從資料檔案匯入的最後一個資料列的號碼。</span><span class="sxs-lookup"><span data-stu-id="ab218-270">Specifies the number of the last row to export from a table or import from a data file.</span></span> <span data-ttu-id="ab218-271">此參數所需的值大於 ( # A0) 0，但小於 (\<) 或等於 (=) 最後一個資料列的編號。</span><span class="sxs-lookup"><span data-stu-id="ab218-271">This parameter requires a value greater than (>) 0 but less than (\<) or equal to (=) the number of the last row.</span></span> <span data-ttu-id="ab218-272">如果沒有這個參數，預設值是檔案中的最後一個資料列。</span><span class="sxs-lookup"><span data-stu-id="ab218-272">In the absence of this parameter, the default is the last row of the file.</span></span>  
  
 <span data-ttu-id="ab218-273">*last_row* 可以是值高達 2^63-1 的正整數。</span><span class="sxs-lookup"><span data-stu-id="ab218-273">*last_row* can be a positive integer with a value up to 2^63-1.</span></span>  
  
 <span data-ttu-id="ab218-274">**-m** _max_errors_</span><span class="sxs-lookup"><span data-stu-id="ab218-274">**-m** _max_errors_</span></span>  
 <span data-ttu-id="ab218-275">指定 **bcp** 作業取消前，可以出現的語法錯誤數上限。</span><span class="sxs-lookup"><span data-stu-id="ab218-275">Specifies the maximum number of syntax errors that can occur before the **bcp** operation is canceled.</span></span> <span data-ttu-id="ab218-276">語法錯誤也暗示著對於目的地資料類型的資料轉換錯誤。</span><span class="sxs-lookup"><span data-stu-id="ab218-276">A syntax error implies a data conversion error to the target data type.</span></span> <span data-ttu-id="ab218-277">*max_errors* 總計將只能在伺服器偵測的錯誤排除在外，例如條件約束違規。</span><span class="sxs-lookup"><span data-stu-id="ab218-277">The *max_errors* total excludes any errors that can be detected only at the server, such as constraint violations.</span></span>  
  
 <span data-ttu-id="ab218-278">將會忽略 **bcp** 公用程式無法複製的資料列，並計算為一次錯誤。</span><span class="sxs-lookup"><span data-stu-id="ab218-278">A row that cannot be copied by the **bcp** utility is ignored and is counted as one error.</span></span> <span data-ttu-id="ab218-279">如果未併入這個選項，預設值是 10。</span><span class="sxs-lookup"><span data-stu-id="ab218-279">If this option is not included, the default is 10.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab218-280">**-M**選項也不適用於轉換 `money` 或 `bigint` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="ab218-280">The **-m** option also does not apply to converting the `money` or `bigint` data types.</span></span>  
  
 <span data-ttu-id="ab218-281">**-n**</span><span class="sxs-lookup"><span data-stu-id="ab218-281">**-n**</span></span>  
 <span data-ttu-id="ab218-282">利用資料的原生 (資料庫) 資料類型來執行大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="ab218-282">Performs the bulk-copy operation using the native (database) data types of the data.</span></span> <span data-ttu-id="ab218-283">並非每個欄位都有這個選項的提示。它會使用原生值。</span><span class="sxs-lookup"><span data-stu-id="ab218-283">This option does not prompt for each field; it uses the native values.</span></span>  
  
 <span data-ttu-id="ab218-284">如需詳細資訊，請參閱[使用原生格式匯入或匯出資料 &#40;SQL Server&#41;](../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab218-284">For more information, see [Use Native Format to Import or Export Data &#40;SQL Server&#41;](../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="ab218-285">**-N**</span><span class="sxs-lookup"><span data-stu-id="ab218-285">**-N**</span></span>  
 <span data-ttu-id="ab218-286">如果是非字元資料，請使用資料的原生 (資料庫) 資料類型執行大量複製作業；如果是字元資料，請使用 Unicode 字元執行大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="ab218-286">Performs the bulk-copy operation using the native (database) data types of the data for noncharacter data, and Unicode characters for character data.</span></span> <span data-ttu-id="ab218-287">此選項為 `-w` 選項提供較佳的高效能替代方式，它的用途在於利用資料檔案，在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行個體之間傳送資料。</span><span class="sxs-lookup"><span data-stu-id="ab218-287">This option offers a higher performance alternative to the `-w` option, and is intended for transferring data from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another using a data file.</span></span> <span data-ttu-id="ab218-288">並非每個欄位都有這項提示。</span><span class="sxs-lookup"><span data-stu-id="ab218-288">It does not prompt for each field.</span></span> <span data-ttu-id="ab218-289">當您要傳送的資料包含 ANSI 擴充字元而且您要利用原生模式的效能時，請使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-289">Use this option when you are transferring data that contains ANSI extended characters and you want to take advantage of the performance of native mode.</span></span>  
  
 <span data-ttu-id="ab218-290">如需詳細資訊，請參閱 [使用 Unicode 原生格式匯入或匯出資料 &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab218-290">For more information, see [Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="ab218-291">如果您使用 bcp.exe 搭配 **-N**，將資料匯出然後匯入相同的資料表架構，則如果有固定長度的非 Unicode 字元資料行 (例如) ，可能會看到截斷警告 `char(10)` 。</span><span class="sxs-lookup"><span data-stu-id="ab218-291">If you export and then import data to the same table schema by using bcp.exe with **-N**, you might see a truncation warning if there is a fixed length, non-Unicode character column (for example, `char(10)`).</span></span>  
  
 <span data-ttu-id="ab218-292">可以忽略此警告。</span><span class="sxs-lookup"><span data-stu-id="ab218-292">The warning can be ignored.</span></span> <span data-ttu-id="ab218-293">解決這個警告的其中一種方式是使用 **-n** 取代 **-N**。</span><span class="sxs-lookup"><span data-stu-id="ab218-293">One way to resolve this warning is to use **-n** instead of **-N**.</span></span>  
  
 <span data-ttu-id="ab218-294">**-o** _output_file_</span><span class="sxs-lookup"><span data-stu-id="ab218-294">**-o** _output_file_</span></span>  
 <span data-ttu-id="ab218-295">指定接收來自命令提示字元重新導向之輸出的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="ab218-295">Specifies the name of a file that receives output redirected from the command prompt.</span></span>  
  
 <span data-ttu-id="ab218-296">如果 *output_file* 的開頭是連字號 (-) 或斜線 (/)，請勿在 **-o** 與 *output_file* 值之間加上空格。</span><span class="sxs-lookup"><span data-stu-id="ab218-296">If *output_file* begins with a hyphen (-) or a forward slash (/), do not include a space between **-o** and the *output_file* value.</span></span>  
  
 <span data-ttu-id="ab218-297">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="ab218-297">**-P** _password_</span></span>  
 <span data-ttu-id="ab218-298">指定登入識別碼的密碼。</span><span class="sxs-lookup"><span data-stu-id="ab218-298">Specifies the password for the login ID.</span></span> <span data-ttu-id="ab218-299">如果未使用此選項， **bcp** 命令會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="ab218-299">If this option is not used, the **bcp** command prompts for a password.</span></span> <span data-ttu-id="ab218-300">如果在未使用密碼的情況下，於命令提示字元尾端使用此選項， **bcp** 就會使用預設密碼 (NULL)。</span><span class="sxs-lookup"><span data-stu-id="ab218-300">If this option is used at the end of the command prompt without a password, **bcp** uses the default password (NULL).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../includes/ssnotestrongpass-md.md)]  
  
 <span data-ttu-id="ab218-301">若要遮罩您的密碼，請勿連同 **-P** 選項指定 **-U** 選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-301">To mask your password, do not specify the **-P** option along with the **-U** option.</span></span> <span data-ttu-id="ab218-302">而是改為在搭配 **-U** 選項及其他參數 (不指定 **-P** ) 指定 **bcp**之後，按 ENTER，該命令就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="ab218-302">Instead, after specifying **bcp** along with the **-U** option and other switches (do not specify **-P**), press ENTER, and the command will prompt you for a password.</span></span> <span data-ttu-id="ab218-303">這個方法可確保在輸入密碼時，遮罩您的密碼。</span><span class="sxs-lookup"><span data-stu-id="ab218-303">This method ensures that your password will be masked when it is entered.</span></span>  
  
 <span data-ttu-id="ab218-304">如果 *password* 的開頭是連字號 (-) 或斜線 (/)，請勿在 **-P** 與 *password* 值之間加上空格。</span><span class="sxs-lookup"><span data-stu-id="ab218-304">If *password* begins with a hyphen (-) or a forward slash (/), do not add a space between **-P** and the *password* value.</span></span>  
  
 `-q`  
 <span data-ttu-id="ab218-305">在 **bcp** 公用程式與 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體之間的連接中，執行 SET QUOTED_IDENTIFIERS ON 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ab218-305">Executes the SET QUOTED_IDENTIFIERS ON statement in the connection between the **bcp** utility and an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ab218-306">請利用這個選項來指定包含空格或單引號的資料庫、擁有者、資料表或檢視表名稱。</span><span class="sxs-lookup"><span data-stu-id="ab218-306">Use this option to specify a database, owner, table, or view name that contains a space or a single quotation mark.</span></span> <span data-ttu-id="ab218-307">請用引號 ("") 括住整個三部分資料表或檢視表名稱。</span><span class="sxs-lookup"><span data-stu-id="ab218-307">Enclose the entire three-part table or view name in quotation marks ("").</span></span>  
  
 <span data-ttu-id="ab218-308">若要指定包含空格或單引號的資料庫名稱，您必須使用 **-q** 選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-308">To specify a database name that contains a space or single quotation mark, you must use the **-q** option.</span></span>  
  
 <span data-ttu-id="ab218-309">`-q` 不適用於傳遞給 `-d` 的值。</span><span class="sxs-lookup"><span data-stu-id="ab218-309">`-q` does not apply to values passed to `-d`.</span></span>  
  
 <span data-ttu-id="ab218-310">如需詳細資訊，請參閱本主題稍後的＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="ab218-310">For more information, see Remarks, later in this topic.</span></span>  
  
 <span data-ttu-id="ab218-311">**-r** _row_term_</span><span class="sxs-lookup"><span data-stu-id="ab218-311">**-r** _row_term_</span></span>  
 <span data-ttu-id="ab218-312">指定資料列結束字元。</span><span class="sxs-lookup"><span data-stu-id="ab218-312">Specifies the row terminator.</span></span> <span data-ttu-id="ab218-313">預設值是 **\n** (新行字元)。</span><span class="sxs-lookup"><span data-stu-id="ab218-313">The default is **\n** (newline character).</span></span> <span data-ttu-id="ab218-314">請利用這個參數來覆寫預設的資料列結束字元。</span><span class="sxs-lookup"><span data-stu-id="ab218-314">Use this parameter to override the default row terminator.</span></span> <span data-ttu-id="ab218-315">如需詳細資訊，請參閱 [指定欄位與資料列結束字元 &#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab218-315">For more information, see [Specify Field and Row Terminators &#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md).</span></span>  
  
 <span data-ttu-id="ab218-316">如果您在 bcp.exe 命令中使用十六進位表示法來指定資料列結束字元，該值將會在 0x00 處截斷。</span><span class="sxs-lookup"><span data-stu-id="ab218-316">If you specify the row terminator in hexadecimal notation in a bcp.exe command, the value will be truncated at 0x00.</span></span> <span data-ttu-id="ab218-317">例如，如果您指定 0x410041，將會使用 0x41。</span><span class="sxs-lookup"><span data-stu-id="ab218-317">For example, if you specify 0x410041, 0x41 will be used.</span></span>  
  
 <span data-ttu-id="ab218-318">如果 *row_term* 的開頭是連字號 (-) 或斜線 (/)，請勿在 **-r** 與 *row_term* 值之間加上空格。</span><span class="sxs-lookup"><span data-stu-id="ab218-318">If *row_term* begins with a hyphen (-) or a forward slash (/), do not include a space between **-r** and the *row_term* value.</span></span>  
  
 <span data-ttu-id="ab218-319">**-R**</span><span class="sxs-lookup"><span data-stu-id="ab218-319">**-R**</span></span>  
 <span data-ttu-id="ab218-320">指定要使用定義給用戶端電腦地區設定的區域格式，將貨幣、日期和時間資料大量複製到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="ab218-320">Specifies that currency, date, and time data is bulk copied into [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] using the regional format defined for the locale setting of the client computer.</span></span> <span data-ttu-id="ab218-321">依預設，會忽略地區設定。</span><span class="sxs-lookup"><span data-stu-id="ab218-321">By default, regional settings are ignored.</span></span>  
  
 <span data-ttu-id="ab218-322">**-S** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="ab218-322">**-S** _server_name_[ **\\**_instance_name_]</span></span>  
 <span data-ttu-id="ab218-323">指定要連接的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab218-323">Specifies the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to which to connect.</span></span> <span data-ttu-id="ab218-324">如果未指定任何伺服器， **bcp** 公用程式會連接至本機電腦的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab218-324">If no server is specified, the **bcp** utility connects to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="ab218-325">透過網路上的遠端電腦或本機具名執行個體執行 **bcp** 指令時，此選項為必要選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-325">This option is required when a **bcp** command is run from a remote computer on the network or a local named instance.</span></span> <span data-ttu-id="ab218-326">若要連接到伺服器上的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 預設執行個體，只要指定 *server_name*。</span><span class="sxs-lookup"><span data-stu-id="ab218-326">To connect to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on a server, specify only *server_name*.</span></span> <span data-ttu-id="ab218-327">若要連接到的已命名實例 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請指定*server_name **_\\_** instance_name*。</span><span class="sxs-lookup"><span data-stu-id="ab218-327">To connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], specify *server_name\*\*_\\_*\* instance_name\*.</span></span>  
  
 <span data-ttu-id="ab218-328">`-t`*field_term*</span><span class="sxs-lookup"><span data-stu-id="ab218-328">`-t` *field_term*</span></span>  
 <span data-ttu-id="ab218-329">指定欄位結束字元。</span><span class="sxs-lookup"><span data-stu-id="ab218-329">Specifies the field terminator.</span></span> <span data-ttu-id="ab218-330">預設值是 **\t** (定位字元)。</span><span class="sxs-lookup"><span data-stu-id="ab218-330">The default is **\t** (tab character).</span></span> <span data-ttu-id="ab218-331">請利用這個參數來覆寫預設的欄位結束字元。</span><span class="sxs-lookup"><span data-stu-id="ab218-331">Use this parameter to override the default field terminator.</span></span> <span data-ttu-id="ab218-332">如需詳細資訊，請參閱 [指定欄位與資料列結束字元 &#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab218-332">For more information, see [Specify Field and Row Terminators &#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md).</span></span>  
  
 <span data-ttu-id="ab218-333">如果您在 bcp.exe 命令中使用十六進位表示法來指定欄位結束字元，該值將會在 0x00 處截斷。</span><span class="sxs-lookup"><span data-stu-id="ab218-333">If you specify the field terminator in hexadecimal notation in a bcp.exe command, the value will be truncated at 0x00.</span></span> <span data-ttu-id="ab218-334">例如，如果您指定 0x410041，將會使用 0x41。</span><span class="sxs-lookup"><span data-stu-id="ab218-334">For example, if you specify 0x410041, 0x41 will be used.</span></span>  
  
 <span data-ttu-id="ab218-335">如果*field_term*的開頭是連字號 (-) 或斜線 (/) ，請勿在 `-t` 與*field_term*值之間加上空格。</span><span class="sxs-lookup"><span data-stu-id="ab218-335">If *field_term* begins with a hyphen (-) or a forward slash (/), do not include a space between `-t` and the *field_term* value.</span></span>  
  
 <span data-ttu-id="ab218-336">**-T**</span><span class="sxs-lookup"><span data-stu-id="ab218-336">**-T**</span></span>  
 <span data-ttu-id="ab218-337">指定 **bcp** 公用程式使用整合式安全性的信任連接，連接至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ab218-337">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="ab218-338">網路使用者的安全性認證、 *login_id*及 *password* 不是必要的選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-338">The security credentials of the network user, *login_id*, and *password* are not required.</span></span> <span data-ttu-id="ab218-339">如果未指定 **-T** ，則必須指定 **-U** 與 **-P** ，才能順利登入。</span><span class="sxs-lookup"><span data-stu-id="ab218-339">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>  
  
 <span data-ttu-id="ab218-340">**-U** _login_id_</span><span class="sxs-lookup"><span data-stu-id="ab218-340">**-U** _login_id_</span></span>  
 <span data-ttu-id="ab218-341">指定用來連接至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的登入識別碼。</span><span class="sxs-lookup"><span data-stu-id="ab218-341">Specifies the login ID used to connect to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ab218-342">指定 **bcp** 公用程式要使用整合式安全性的信任連接，連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 時，請使用 **-T** 選項 (信任連接)，而非「使用者名稱」和「密碼」的組合。</span><span class="sxs-lookup"><span data-stu-id="ab218-342">When the **bcp** utility is connecting to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with a trusted connection using integrated security, use the **-T** option (trusted connection) instead of the *user name* and *password* combination.</span></span>  
  
 <span data-ttu-id="ab218-343">**-v**</span><span class="sxs-lookup"><span data-stu-id="ab218-343">**-v**</span></span>  
 <span data-ttu-id="ab218-344">報告 **bcp** 公用程式版本號碼和著作權。</span><span class="sxs-lookup"><span data-stu-id="ab218-344">Reports the **bcp** utility version number and copyright.</span></span>  
  
 <span data-ttu-id="ab218-345">**-V** (**80** | **90** | **100**| **110**)</span><span class="sxs-lookup"><span data-stu-id="ab218-345">**-V** (**80** | **90** | **100**| **110**)</span></span>  
 <span data-ttu-id="ab218-346">利用舊版 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的資料類型執行大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="ab218-346">Performs the bulk-copy operation using data types from an earlier version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ab218-347">不是每個欄位都有這個選項的提示，它會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="ab218-347">This option does not prompt for each field; it uses the default values.</span></span>  
  
 <span data-ttu-id="ab218-348">**80** = [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab218-348">**80** = [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]</span></span>  
  
 <span data-ttu-id="ab218-349">**90** = [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab218-349">**90** = [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]</span></span>  
  
 <span data-ttu-id="ab218-350">**100** = [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 及 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab218-350">**100** = [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] and [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]</span></span>  
  
 <span data-ttu-id="ab218-351">**110 =[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="ab218-351">**110 = [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]**</span></span>  
  
 <span data-ttu-id="ab218-352">例如，若要產生 [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]不支援但在新版 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中所引入的資料類型，請使用 -V80 選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-352">For example, to generate data for types not supported by [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)], but were introduced in later versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], use the -V80 option.</span></span>  
  
 <span data-ttu-id="ab218-353">如需詳細資訊，請參閱 [從舊版 SQL Server 匯入原生與字元格式資料](../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab218-353">For more information, see [Import Native and Character Format Data from Earlier Versions of SQL Server](../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md).</span></span>  
  
 `-w`  
 <span data-ttu-id="ab218-354">利用 Unicode 字元執行大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="ab218-354">Performs the bulk copy operation using Unicode characters.</span></span> <span data-ttu-id="ab218-355">並非每個欄位都有這個選項的提示。它會使用 `nchar` 做為儲存類型（沒有前置詞）、 **\t** (定位字元) 做為欄位分隔符號，而**\n** (換行字元) 做為資料列結束字元。</span><span class="sxs-lookup"><span data-stu-id="ab218-355">This option does not prompt for each field; it uses `nchar` as the storage type, no prefixes, **\t** (tab character) as the field separator, and **\n** (newline character) as the row terminator.</span></span> <span data-ttu-id="ab218-356">`-w` 與 `-c` 不相容。</span><span class="sxs-lookup"><span data-stu-id="ab218-356">`-w` is not compatible with `-c`.</span></span>  
  
 <span data-ttu-id="ab218-357">如需詳細資訊，請參閱 [使用 Unicode 字元格式匯入或匯出資料 &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab218-357">For more information, see [Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="ab218-358">**-x**</span><span class="sxs-lookup"><span data-stu-id="ab218-358">**-x**</span></span>  
 <span data-ttu-id="ab218-359">與 **format** 和 **-f**_format_file_ 選項一起使用會產生以 XML 為基礎的格式檔案，而非預設的非 XML 格式檔案。</span><span class="sxs-lookup"><span data-stu-id="ab218-359">Used with the **format** and **-f**_format_file_ options, generates an XML-based format file instead of the default non-XML format file.</span></span> <span data-ttu-id="ab218-360">匯入或匯出資料時， **-x** 無法運作。</span><span class="sxs-lookup"><span data-stu-id="ab218-360">The **-x** does not work when importing or exporting data.</span></span> <span data-ttu-id="ab218-361">如果沒有與 **format** 和 **-f**_format_file_ 一起使用，則會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ab218-361">It generates an error if used without both **format** and **-f**_format_file_.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab218-362">備註</span><span class="sxs-lookup"><span data-stu-id="ab218-362">Remarks</span></span>  
 <span data-ttu-id="ab218-363">當您安裝工具時，會安裝**bcp** 12.0 用戶端 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ab218-363">The **bcp** 12.0 client is installed when you install [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] tools.</span></span> <span data-ttu-id="ab218-364">如果同時為 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 和舊版 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝工具，則根據 PATH 環境變數值的不同，您也可以使用舊版的 **bcp** 用戶端來取代 **bcp** 12.0 用戶端。</span><span class="sxs-lookup"><span data-stu-id="ab218-364">If tools are installed for both [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] and an earlier version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], depending on the value of the PATH environment variable, you might be using the earlier **bcp** client instead of the **bcp** 12.0 client.</span></span> <span data-ttu-id="ab218-365">這個環境變數定義了 Windows 用來搜尋可執行檔的一組目錄。</span><span class="sxs-lookup"><span data-stu-id="ab218-365">This environment variable defines the set of directories used by Windows to search for executable files.</span></span> <span data-ttu-id="ab218-366">若要確定您所使用的版本，請在 Windows 命令提示字元處執行 **bcp /v** 命令。</span><span class="sxs-lookup"><span data-stu-id="ab218-366">To discover which version you are using, run the **bcp /v** command at the Windows Command Prompt.</span></span> <span data-ttu-id="ab218-367">如需有關如何在 PATH 環境變數中設定命令路徑的詳細資訊，請參閱 Windows 說明。</span><span class="sxs-lookup"><span data-stu-id="ab218-367">For information about how to set the command path in the PATH environment variable, see Windows Help.</span></span>  
  
 <span data-ttu-id="ab218-368">只有在同時安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 工具和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client 時，才能支援 XML 格式檔案。</span><span class="sxs-lookup"><span data-stu-id="ab218-368">XML format files are only supported when [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tools are installed together with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="ab218-369">如需 **bcp** 公用程式的尋找位置與執行方式，以及命令提示字元公用程式語法慣例的資訊，請參閱[命令提示字元公用程式參考 &#40;Database Engine&#41;](../tools/command-prompt-utility-reference-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="ab218-369">For information about where to find or how to run the **bcp** utility and about the command prompt utilities syntax conventions, see [Command Prompt Utility Reference &#40;Database Engine&#41;](../tools/command-prompt-utility-reference-database-engine.md).</span></span>  
  
 <span data-ttu-id="ab218-370">如需準備資料進行大量匯入或匯出作業的資訊，請參閱 [準備大量匯出或匯入的資料 &#40;SQL Server&#41;](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)方面的知識。</span><span class="sxs-lookup"><span data-stu-id="ab218-370">For information on preparing data for bulk import or export operations, see [Prepare Data for Bulk Export or Import &#40;SQL Server&#41;](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).</span></span>  
  
 <span data-ttu-id="ab218-371">如需大量匯入所執行的資料列插入作業於何時記錄到交易記錄的資訊，請參閱 [大量匯入採用最低限度記錄的必要條件](../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md)。</span><span class="sxs-lookup"><span data-stu-id="ab218-371">For information about when row-insert operations that are performed by bulk import are logged in the transaction log, see [Prerequisites for Minimal Logging in Bulk Import](../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md).</span></span>  
  
## <a name="native-data-file-support"></a><span data-ttu-id="ab218-372">原生資料檔案支援</span><span class="sxs-lookup"><span data-stu-id="ab218-372">Native Data File Support</span></span>  
 <span data-ttu-id="ab218-373">在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]中， **bcp** 公用程式可支援與 [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]、 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]、 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]和 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]相容的原生資料檔案。</span><span class="sxs-lookup"><span data-stu-id="ab218-373">In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], the **bcp** utility supports native data files compatible with [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], and [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
## <a name="computed-columns-and-timestamp-columns"></a><span data-ttu-id="ab218-374">計算資料行和時間戳記資料行</span><span class="sxs-lookup"><span data-stu-id="ab218-374">Computed Columns and timestamp Columns</span></span>  
 <span data-ttu-id="ab218-375">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會忽略針對計算資料行或 `timestamp` 資料行匯入之資料檔案中的值，並自動指派值。</span><span class="sxs-lookup"><span data-stu-id="ab218-375">Values in the data file being imported for computed or `timestamp` columns are ignored, and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] automatically assigns values.</span></span> <span data-ttu-id="ab218-376">如果資料檔案不包含資料表中計算資料行或 `timestamp` 資料行的值，請使用格式檔案指定在匯入資料時應略過資料表中的計算資料行或 `timestamp` 資料行；[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會自動指派資料行的值。</span><span class="sxs-lookup"><span data-stu-id="ab218-376">If the data file does not contain values for the computed or `timestamp` columns in the table, use a format file to specify that the computed or `timestamp` columns in the table should be skipped when importing data; [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] automatically assigns values for the column.</span></span>  
  
 <span data-ttu-id="ab218-377">計算資料行和 `timestamp` 資料行會照常從 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 大量複製到資料檔案中。</span><span class="sxs-lookup"><span data-stu-id="ab218-377">Computed and `timestamp` columns are bulk copied from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to a data file as usual.</span></span>  
  
## <a name="specifying-identifiers-that-contain-spaces-or-quotation-marks"></a><span data-ttu-id="ab218-378">指定包含空格或引號的識別碼</span><span class="sxs-lookup"><span data-stu-id="ab218-378">Specifying Identifiers That Contain Spaces or Quotation Marks</span></span>  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="ab218-379">識別碼可以包括內嵌空格和引號之類的字元。</span><span class="sxs-lookup"><span data-stu-id="ab218-379">identifiers can include characters such as embedded spaces and quotation marks.</span></span> <span data-ttu-id="ab218-380">您必須依照下列方式來處理這些識別碼：</span><span class="sxs-lookup"><span data-stu-id="ab218-380">Such identifiers must be treated as follows:</span></span>  
  
-   <span data-ttu-id="ab218-381">當您在命令提示字元之下，指定包含空格或引號的識別碼或檔案名稱時，請用引號 ("") 括住識別碼。</span><span class="sxs-lookup"><span data-stu-id="ab218-381">When you specify an identifier or file name that includes a space or quotation mark at the command prompt, enclose the identifier in quotation marks ("").</span></span>  
  
     <span data-ttu-id="ab218-382">例如，下列 `bcp out` 命令會建立名稱為 `Currency Types.dat`的資料檔案：</span><span class="sxs-lookup"><span data-stu-id="ab218-382">For example, the following `bcp out` command creates a data file named `Currency Types.dat`:</span></span>  
  
    ```  
    bcp AdventureWorks2012.Sales.Currency out "Currency Types.dat" -T -c  
    ```  
  
-   <span data-ttu-id="ab218-383">若要指定包含空格或引號的資料庫名稱，您必須使用 `-q` 選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-383">To specify a database name that contains a space or quotation mark, you must use the `-q` option.</span></span>  
  
-   <span data-ttu-id="ab218-384">如果擁有者、資料表或檢視表名稱包含內嵌的空格或引號，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ab218-384">For owner, table, or view names that contain embedded spaces or quotation marks, you can either:</span></span>  
  
    -   <span data-ttu-id="ab218-385">指定 `-q` 選項，或</span><span class="sxs-lookup"><span data-stu-id="ab218-385">Specify the `-q` option, or</span></span>  
  
    -   <span data-ttu-id="ab218-386">在引號內，用方括號 ([]) 括住擁有者、資料表或檢視表名稱。</span><span class="sxs-lookup"><span data-stu-id="ab218-386">Enclose the owner, table, or view name in brackets ([]) inside the quotation marks.</span></span>  
  
## <a name="data-validation"></a><span data-ttu-id="ab218-387">資料驗證</span><span class="sxs-lookup"><span data-stu-id="ab218-387">Data Validation</span></span>  
 <span data-ttu-id="ab218-388">**bcp** 現在會強制進行資料驗證與資料檢查，若針對資料檔案中無效的資料執行指令碼，這些資料驗證與檢查作業可能會導致指令碼失敗。</span><span class="sxs-lookup"><span data-stu-id="ab218-388">**bcp** now enforces data validation and data checks that might cause scripts to fail if they are executed on invalid data in a data file.</span></span> <span data-ttu-id="ab218-389">例如， **bcp** 現在會驗證：</span><span class="sxs-lookup"><span data-stu-id="ab218-389">For example, **bcp** now verifies that:</span></span>  
  
-   <span data-ttu-id="ab218-390">`float` 或 `real` 資料類型的原生表示法是否有效。</span><span class="sxs-lookup"><span data-stu-id="ab218-390">The native representation of `float` or `real` data types are valid.</span></span>  
  
-   <span data-ttu-id="ab218-391">Unicode 資料的長度是否為偶數位元組。</span><span class="sxs-lookup"><span data-stu-id="ab218-391">Unicode data has an even-byte length.</span></span>  
  
 <span data-ttu-id="ab218-392">可在舊版 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中大量匯入的無效資料形式，現在可能無法載入。不過，在舊版中，除非用戶端嘗試存取無效資料，否則不會發生作業失敗的情況。</span><span class="sxs-lookup"><span data-stu-id="ab218-392">Forms of invalid data that could be bulk imported in earlier versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] might fail to load now; whereas, in earlier versions, the failure did not occur until a client tried to access the invalid data.</span></span> <span data-ttu-id="ab218-393">新增的驗證會使大量載入之後的資料查詢，將出現意外的狀況減到最少。</span><span class="sxs-lookup"><span data-stu-id="ab218-393">The added validation minimizes surprises when querying the data after bulk load.</span></span>  
  
## <a name="bulk-exporting-or-importing-sqlxml-documents"></a><span data-ttu-id="ab218-394">大量匯出或匯入 SQLXML 文件</span><span class="sxs-lookup"><span data-stu-id="ab218-394">Bulk Exporting or Importing SQLXML Documents</span></span>  
 <span data-ttu-id="ab218-395">若要大量匯出或匯入 SQLXML 資料，請在格式檔案中使用下列其中一種資料類型。</span><span class="sxs-lookup"><span data-stu-id="ab218-395">To bulk export or import SQLXML data, use one of the following data types in your format file.</span></span>  
  
|<span data-ttu-id="ab218-396">資料類型</span><span class="sxs-lookup"><span data-stu-id="ab218-396">Data type</span></span>|<span data-ttu-id="ab218-397">效果</span><span class="sxs-lookup"><span data-stu-id="ab218-397">Effect</span></span>|  
|---------------|------------|  
|<span data-ttu-id="ab218-398">SQLCHAR 或 SQLVARYCHAR</span><span class="sxs-lookup"><span data-stu-id="ab218-398">SQLCHAR or SQLVARYCHAR</span></span>|<span data-ttu-id="ab218-399">資料是使用用戶端字碼頁或定序所隱含的字碼頁所傳送。</span><span class="sxs-lookup"><span data-stu-id="ab218-399">The data is sent in the client code page or in the code page implied by the collation).</span></span> <span data-ttu-id="ab218-400">其效果與指定 `-c` 參數但不指定格式檔案相同。</span><span class="sxs-lookup"><span data-stu-id="ab218-400">The effect is the same as specifying the `-c` switch without specifying a format file.</span></span>|  
|<span data-ttu-id="ab218-401">SQLNCHAR 或 SQLNVARCHAR</span><span class="sxs-lookup"><span data-stu-id="ab218-401">SQLNCHAR or SQLNVARCHAR</span></span>|<span data-ttu-id="ab218-402">以 Unicode 格式傳送這份資料。</span><span class="sxs-lookup"><span data-stu-id="ab218-402">The data is sent as Unicode.</span></span> <span data-ttu-id="ab218-403">其效果與指定 `-w` 參數但不指定格式檔案相同。</span><span class="sxs-lookup"><span data-stu-id="ab218-403">The effect is the same as specifying the `-w` switch without specifying a format file.</span></span>|  
|<span data-ttu-id="ab218-404">SQLBINARY 或 SQLVARYBIN</span><span class="sxs-lookup"><span data-stu-id="ab218-404">SQLBINARY or SQLVARYBIN</span></span>|<span data-ttu-id="ab218-405">未經任何轉換即傳送這份資料。</span><span class="sxs-lookup"><span data-stu-id="ab218-405">The data is sent without any conversion.</span></span>|  
  
## <a name="permissions"></a><span data-ttu-id="ab218-406">權限</span><span class="sxs-lookup"><span data-stu-id="ab218-406">Permissions</span></span>  
 <span data-ttu-id="ab218-407">**bcpout** 作業需要來源資料表的 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="ab218-407">A **bcpout** operation requires SELECT permission on the source table.</span></span>  
  
 <span data-ttu-id="ab218-408">**bcpin** 作業至少需要目標資料表的 SELECT/INSERT 權限。</span><span class="sxs-lookup"><span data-stu-id="ab218-408">A **bcpin** operation minimally requires SELECT/INSERT permissions on the target table.</span></span> <span data-ttu-id="ab218-409">另外，如果符合下列中的任何狀況，便需要 ALTER TABLE 權限：</span><span class="sxs-lookup"><span data-stu-id="ab218-409">In addition, ALTER TABLE permission is required if any of the following is true:</span></span>  
  
-   <span data-ttu-id="ab218-410">存在有條件約束，而且未指定 CHECK_CONSTRAINTS 提示。</span><span class="sxs-lookup"><span data-stu-id="ab218-410">Constraints exist and the CHECK_CONSTRAINTS hint is not specified.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ab218-411">停用條件約束是預設行為。</span><span class="sxs-lookup"><span data-stu-id="ab218-411">Disabling constraints is the default behavior.</span></span> <span data-ttu-id="ab218-412">若要明確啟用條件約束，請搭配 CHECK_CONSTRAINTS 提示使用 **-h** 選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-412">To enable constraints explicitly, use the **-h** option with the CHECK_CONSTRAINTS hint.</span></span>  
  
-   <span data-ttu-id="ab218-413">存在有觸發程序，而且未指定 FIRE_TRIGGER 提示。</span><span class="sxs-lookup"><span data-stu-id="ab218-413">Triggers exist and the FIRE_TRIGGER hint is not specified.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ab218-414">依預設不會引發觸發程序。</span><span class="sxs-lookup"><span data-stu-id="ab218-414">By default, triggers are not fired.</span></span> <span data-ttu-id="ab218-415">若要明確引發觸發程序，請搭配 FIRE_TRIGGERS 提示使用 **-h** 選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-415">To fire triggers explicitly, use the **-h** option with the FIRE_TRIGGERS hint.</span></span>  
  
-   <span data-ttu-id="ab218-416">您利用 **-E** 選項，從資料檔案匯入識別值。</span><span class="sxs-lookup"><span data-stu-id="ab218-416">You use the **-E** option to import identity values from a data file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab218-417">在 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]中，目標資料表的 ALTER TABLE 權限是一項新的需求。</span><span class="sxs-lookup"><span data-stu-id="ab218-417">Requiring ALTER TABLE permission on the target table was new in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="ab218-418">如果使用者帳戶沒有目標資料表的 ALTER 資料表權限，這項新的需求可能會讓不會強制進行觸發程序和條件約束檢查的 **bcp** 指令碼失敗。</span><span class="sxs-lookup"><span data-stu-id="ab218-418">This new requirement might cause **bcp** scripts that do not enforce triggers and constraint checks to fail if the user account lacks ALTER table permissions for the target table.</span></span>  
  
## <a name="character-mode--c-and-native-mode--n-best-practices"></a><span data-ttu-id="ab218-419">字元模式 (-c) 與原生模式 (-n) 最佳做法</span><span class="sxs-lookup"><span data-stu-id="ab218-419">Character Mode (-c) and Native Mode (-n) Best Practices</span></span>  
 <span data-ttu-id="ab218-420">本節具有字元模式 (-c) 與原生模式 (-n) 的建議事項。</span><span class="sxs-lookup"><span data-stu-id="ab218-420">This section has recommendations for to character mode (-c) and native mode (-n).</span></span>  
  
-   <span data-ttu-id="ab218-421">(管理員/使用者) 盡可能使用原生格式 (-n) 來避免分隔符號問題。</span><span class="sxs-lookup"><span data-stu-id="ab218-421">(Administrator/User) When possible, use native format (-n) to avoid the separator issue.</span></span> <span data-ttu-id="ab218-422">您可以使用原生格式，透過 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]匯出和匯入。</span><span class="sxs-lookup"><span data-stu-id="ab218-422">Use the native format to export and import using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ab218-423">如果資料將匯入非 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫，請使用 -c 或 -w 選項，從[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 匯出資料。</span><span class="sxs-lookup"><span data-stu-id="ab218-423">Export data from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] using the -c or -w option if the data will be imported to a non-[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span>  
  
-   <span data-ttu-id="ab218-424">(管理員) 使用 BCP OUT 時確認資料。</span><span class="sxs-lookup"><span data-stu-id="ab218-424">(Administrator) Verify data when using BCP OUT.</span></span> <span data-ttu-id="ab218-425">例如，當您依序使用 BCP OUT、BCP IN 和 BCP OUT 時，請確認資料正確匯出，而且結束字元值並未當做某些資料值的一部分使用。</span><span class="sxs-lookup"><span data-stu-id="ab218-425">For example, when you use BCP OUT, BCP IN, and then BCP OUT verify that the data is properly exported and the terminator values are not used as part of some data value.</span></span> <span data-ttu-id="ab218-426">請考慮使用隨機十六進位值來覆寫預設結束字元 (使用 -t 和 -r 選項)，避免結束字元值與資料值之間發生衝突。</span><span class="sxs-lookup"><span data-stu-id="ab218-426">Please consider overriding the default terminators (using -t and -r options) with random hexadecimal values to avoid conflicts between terminator values and data values.</span></span>  
  
-   <span data-ttu-id="ab218-427">(使用者) 使用長且唯一的結束字元 (任何位元組或字元序列)，將實際字串值發生衝突的可能性降到最低。</span><span class="sxs-lookup"><span data-stu-id="ab218-427">(User) Use a long and unique terminator (any sequence of bytes or characters) to minimize the possibility of a conflict with the actual string value.</span></span> <span data-ttu-id="ab218-428">這可透過使用 -t 和 -r 選項完成。</span><span class="sxs-lookup"><span data-stu-id="ab218-428">This can be done by using the -t and -r options.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ab218-429">範例</span><span class="sxs-lookup"><span data-stu-id="ab218-429">Examples</span></span>  
 <span data-ttu-id="ab218-430">本區段包含下列範例：</span><span class="sxs-lookup"><span data-stu-id="ab218-430">This section contains the following examples:</span></span>  
  
-   <span data-ttu-id="ab218-431">A.</span><span class="sxs-lookup"><span data-stu-id="ab218-431">A.</span></span> <span data-ttu-id="ab218-432">將資料表資料列複製到資料檔案中 (使用信任連接)</span><span class="sxs-lookup"><span data-stu-id="ab218-432">Copying table rows into a data file (with a trusted connection)</span></span>  
  
-   <span data-ttu-id="ab218-433">B.</span><span class="sxs-lookup"><span data-stu-id="ab218-433">B.</span></span> <span data-ttu-id="ab218-434">將資料表資料列複製到資料檔案中 (使用混合模式驗證)</span><span class="sxs-lookup"><span data-stu-id="ab218-434">Copying table rows into a data file (with Mixed-mode Authentication)</span></span>  
  
-   <span data-ttu-id="ab218-435">C.</span><span class="sxs-lookup"><span data-stu-id="ab218-435">C.</span></span> <span data-ttu-id="ab218-436">將檔案資料複製到資料表中</span><span class="sxs-lookup"><span data-stu-id="ab218-436">Copying data from a file to a table</span></span>  
  
-   <span data-ttu-id="ab218-437">D.</span><span class="sxs-lookup"><span data-stu-id="ab218-437">D.</span></span> <span data-ttu-id="ab218-438">將特定資料行複製到資料檔案中</span><span class="sxs-lookup"><span data-stu-id="ab218-438">Copying a specific column into a data file</span></span>  
  
-   <span data-ttu-id="ab218-439">E.</span><span class="sxs-lookup"><span data-stu-id="ab218-439">E.</span></span> <span data-ttu-id="ab218-440">將特定資料列複製到資料檔案中</span><span class="sxs-lookup"><span data-stu-id="ab218-440">Copying a specific row into a data file</span></span>  
  
-   <span data-ttu-id="ab218-441">F.</span><span class="sxs-lookup"><span data-stu-id="ab218-441">F.</span></span> <span data-ttu-id="ab218-442">將查詢的資料複製到資料檔案中</span><span class="sxs-lookup"><span data-stu-id="ab218-442">Copying data from a query to a data file</span></span>  
  
-   <span data-ttu-id="ab218-443">G.</span><span class="sxs-lookup"><span data-stu-id="ab218-443">G.</span></span> <span data-ttu-id="ab218-444">建立非 XML 格式檔案</span><span class="sxs-lookup"><span data-stu-id="ab218-444">Creating a non-XML format file</span></span>  
  
-   <span data-ttu-id="ab218-445">H.</span><span class="sxs-lookup"><span data-stu-id="ab218-445">H.</span></span> <span data-ttu-id="ab218-446">建立 XML 格式檔案</span><span class="sxs-lookup"><span data-stu-id="ab218-446">Creating an XML format file</span></span>  
  
-   <span data-ttu-id="ab218-447">I.</span><span class="sxs-lookup"><span data-stu-id="ab218-447">I.</span></span> <span data-ttu-id="ab218-448">使用格式檔案以 **bcp**進行大量匯入</span><span class="sxs-lookup"><span data-stu-id="ab218-448">Using a format file to bulk import with **bcp**</span></span>  
  
### <a name="a-copying-table-rows-into-a-data-file-with-a-trusted-connection"></a><span data-ttu-id="ab218-449">A.</span><span class="sxs-lookup"><span data-stu-id="ab218-449">A.</span></span> <span data-ttu-id="ab218-450">將資料表資料列複製到資料檔案中 (使用信任連接)</span><span class="sxs-lookup"><span data-stu-id="ab218-450">Copying table rows into a data file (with a trusted connection)</span></span>  
 <span data-ttu-id="ab218-451">下列範例說明 **資料表上的** out `AdventureWorks2012.Sales.Currency` 選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-451">The following example illustrates the **out** option on the `AdventureWorks2012.Sales.Currency` table.</span></span> <span data-ttu-id="ab218-452">這個範例會建立一個名稱為 `Currency.dat` 的資料檔案，且會利用字元格式，將資料表的資料複製到這個資料檔案中。</span><span class="sxs-lookup"><span data-stu-id="ab218-452">This example creates a data file named `Currency.dat` and copies the table data into it using character format.</span></span> <span data-ttu-id="ab218-453">這個範例假設您使用 Windows 驗證，且有信任連接通往您在執行 **bcp** 命令的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab218-453">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="ab218-454">請在命令提示字元之下，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="ab218-454">At a command prompt, enter the following command:</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency out Currency.dat -T -c  
```  
  
### <a name="b-copying-table-rows-into-a-data-file-with-mixed-mode-authentication"></a><span data-ttu-id="ab218-455">B.</span><span class="sxs-lookup"><span data-stu-id="ab218-455">B.</span></span> <span data-ttu-id="ab218-456">將資料表資料列複製到資料檔案中 (使用混合模式驗證)</span><span class="sxs-lookup"><span data-stu-id="ab218-456">Copying table rows into a data file (with mixed-mode authentication)</span></span>  
 <span data-ttu-id="ab218-457">下列範例說明 **資料表上的** out `AdventureWorks2012.Sales.Currency` 選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-457">The following example illustrates the **out** option on the `AdventureWorks2012.Sales.Currency` table.</span></span> <span data-ttu-id="ab218-458">這個範例會建立一個名稱為 `Currency.dat` 的資料檔案，且會利用字元格式，將資料表的資料複製到這個資料檔案中。</span><span class="sxs-lookup"><span data-stu-id="ab218-458">This example creates a data file named `Currency.dat` and copies the table data into it using character format.</span></span>  
  
 <span data-ttu-id="ab218-459">此範例假設您使用的是混合模式驗證，您必須使用 **-U** 參數指定您的登入識別碼。</span><span class="sxs-lookup"><span data-stu-id="ab218-459">The example assumes that you are using mixed-mode authentication, you must use the **-U** switch to specify your login ID.</span></span> <span data-ttu-id="ab218-460">同時，除非您要連接到本機電腦上的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 預設執行個體，否則請使用 **-S** 參數指定系統名稱，並選擇性地指定執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="ab218-460">Also, unless you are connecting to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer, use the **-S** switch to specify the system name and, optionally, an instance name.</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency out Currency.dat -c -U<login_id> -S<server_name\instance_name>  
```  
  
 <span data-ttu-id="ab218-461">系統會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="ab218-461">The system will prompt you for your password.</span></span>  
  
### <a name="c-copying-data-from-a-file-to-a-table"></a><span data-ttu-id="ab218-462">C.</span><span class="sxs-lookup"><span data-stu-id="ab218-462">C.</span></span> <span data-ttu-id="ab218-463">將檔案資料複製到資料表中</span><span class="sxs-lookup"><span data-stu-id="ab218-463">Copying data from a file to a table</span></span>  
 <span data-ttu-id="ab218-464">下列範例會利用先前範例 (`Currency.dat`) 中所建立的檔案，說明 **in** 選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-464">The following example illustrates the **in** option by using the file created in the preceding example (`Currency.dat`).</span></span> <span data-ttu-id="ab218-465">不過，這個範例會先建立空的 `AdventureWorks2012 Sales.Currency` 資料表複本 `Sales.Currency2`，以便將資料複製到這個複本中。</span><span class="sxs-lookup"><span data-stu-id="ab218-465">First, however, this example creates an empty copy of the `AdventureWorks2012 Sales.Currency` table, `Sales.Currency2`, into which the data is copied.</span></span> <span data-ttu-id="ab218-466">這個範例假設您使用 Windows 驗證，且有信任連接通往您在執行 **bcp** 命令的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab218-466">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="ab218-467">若要在查詢編輯器中建立空的資料表，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="ab218-467">To create the empty table, in Query Editor, enter the following command:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * INTO AdventureWorks2012.Sales.Currency2   
FROM AdventureWorks2012.Sales.Currency WHERE 1=2;  
```  
  
 <span data-ttu-id="ab218-468">若要將字元資料大量複製到新資料表中 (也就是匯入資料)，請在命令提示字元之下，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="ab218-468">To bulk copy the character data into the new table, that is to import the data, enter the following command at a command prompt:</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency2 in Currency.dat -T -c  
```  
  
 <span data-ttu-id="ab218-469">若要確認命令已順利完成，請在查詢編輯器中顯示資料表的內容，再輸入：</span><span class="sxs-lookup"><span data-stu-id="ab218-469">To verify that the command succeeded, display the contents of the table in Query Editor, and enter:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM Sales.Currency2  
```  
  
### <a name="d-copying-a-specific-column-into-a-data-file"></a><span data-ttu-id="ab218-470">D.</span><span class="sxs-lookup"><span data-stu-id="ab218-470">D.</span></span> <span data-ttu-id="ab218-471">將特定資料行複製到資料檔案中</span><span class="sxs-lookup"><span data-stu-id="ab218-471">Copying a specific column into a data file</span></span>  
 <span data-ttu-id="ab218-472">若要複製特定資料行，您可以使用 **queryout** 選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-472">To copy a specific column, you can use the **queryout** option.</span></span> <span data-ttu-id="ab218-473">下列範例只會將 `Name` 資料表的 `Sales.Currency` 資料行複製到資料檔案中。</span><span class="sxs-lookup"><span data-stu-id="ab218-473">The following example copies only the `Name` column of the `Sales.Currency` table into a data file.</span></span> <span data-ttu-id="ab218-474">這個範例假設您使用 Windows 驗證，且有信任連接通往您在執行 **bcp** 命令的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab218-474">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="ab218-475">請在 Windows 命令提示字元之下，輸入：</span><span class="sxs-lookup"><span data-stu-id="ab218-475">At the Windows command prompt, enter:</span></span>  
  
```  
bcp "SELECT Name FROM AdventureWorks.Sales.Currency" queryout Currency.Name.dat -T -c  
```  
  
### <a name="e-copying-a-specific-row-into-a-data-file"></a><span data-ttu-id="ab218-476">E.</span><span class="sxs-lookup"><span data-stu-id="ab218-476">E.</span></span> <span data-ttu-id="ab218-477">將特定資料列複製到資料檔案中</span><span class="sxs-lookup"><span data-stu-id="ab218-477">Copying a specific row into a data file</span></span>  
 <span data-ttu-id="ab218-478">若要複製特定資料列，您可以使用 **queryout** 選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-478">To copy a specific row, you can use the **queryout** option.</span></span> <span data-ttu-id="ab218-479">下列範例只會將 `AdventureWorks2012.Person.Person` 資料表中名為 `Jarrod Rana` 之連絡人的資料列，複製到資料檔案 (`Jarrod Rana.dat`) 中。這個範例假設您使用 Windows 驗證，且有信任連接通往您執行 **bcp** 命令的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab218-479">The following example copies only the row for the contact named `Jarrod Rana` from the `AdventureWorks2012.Person.Person` table into a data file (`Jarrod Rana.dat`).The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="ab218-480">請在 Windows 命令提示字元之下，輸入：</span><span class="sxs-lookup"><span data-stu-id="ab218-480">At the Windows command prompt, enter:</span></span>  
  
```  
bcp "SELECT * FROM AdventureWorks2012.Person.Person WHERE FirstName='Jarrod' AND LastName='Rana' "  queryout "Jarrod Rana.dat" -T -c  
```  
  
### <a name="f-copying-data-from-a-query-to-a-data-file"></a><span data-ttu-id="ab218-481">F.</span><span class="sxs-lookup"><span data-stu-id="ab218-481">F.</span></span> <span data-ttu-id="ab218-482">將查詢的資料複製到資料檔案中</span><span class="sxs-lookup"><span data-stu-id="ab218-482">Copying data from a query to a data file</span></span>  
 <span data-ttu-id="ab218-483">若要將 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式的結果集複製到資料檔案中，請使用 **queryout** 選項。</span><span class="sxs-lookup"><span data-stu-id="ab218-483">To copy the result set from a [!INCLUDE[tsql](../includes/tsql-md.md)] statement to a data file, use the **queryout** option.</span></span> <span data-ttu-id="ab218-484">下列範例會依照先姓氏後名字的方式，將 `AdventureWorks2012.Person.Person` 資料表中的名稱複製到 `Contacts.txt` 資料檔案中。</span><span class="sxs-lookup"><span data-stu-id="ab218-484">The following example copies the names from the `AdventureWorks2012.Person.Person` table, ordered by last name then first name, into the `Contacts.txt` data file.</span></span> <span data-ttu-id="ab218-485">這個範例假設您使用 Windows 驗證，且有信任連接通往您在執行 **bcp** 命令的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab218-485">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="ab218-486">請在 Windows 命令提示字元之下，輸入：</span><span class="sxs-lookup"><span data-stu-id="ab218-486">At the Windows command prompt, enter:</span></span>  
  
```  
bcp "SELECT FirstName, LastName FROM AdventureWorks2012.Person.Person ORDER BY LastName, Firstname" queryout Contacts.txt -c -T  
```  
  
### <a name="g-creating-a-non-xml-format-file"></a><span data-ttu-id="ab218-487">G.</span><span class="sxs-lookup"><span data-stu-id="ab218-487">G.</span></span> <span data-ttu-id="ab218-488">建立非 XML 格式檔案</span><span class="sxs-lookup"><span data-stu-id="ab218-488">Creating a non-XML format file</span></span>  
 <span data-ttu-id="ab218-489">下列範例會針對 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫中的 `Currency.fmt` 資料表，建立 XML 格式檔案 `Sales.Currency`。</span><span class="sxs-lookup"><span data-stu-id="ab218-489">The following example creates a non-XML format file, `Currency.fmt`, for the `Sales.Currency` table in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="ab218-490">這個範例假設您使用 Windows 驗證，且有信任連接通往您在執行 **bcp** 命令的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab218-490">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="ab218-491">請在 Windows 命令提示字元之下，輸入：</span><span class="sxs-lookup"><span data-stu-id="ab218-491">At the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency format nul -T -c  -f Currency.fmt  
```  
  
 <span data-ttu-id="ab218-492">如需詳細資訊，請參閱 [非 XML 格式檔案 &#40;SQL Server&#41;](../relational-databases/import-export/xml-format-files-sql-server.md)所支援的原始格式。</span><span class="sxs-lookup"><span data-stu-id="ab218-492">For more information, see [Non-XML Format Files &#40;SQL Server&#41;](../relational-databases/import-export/xml-format-files-sql-server.md).</span></span>  
  
### <a name="h-creating-an-xml-format-file"></a><span data-ttu-id="ab218-493">H.</span><span class="sxs-lookup"><span data-stu-id="ab218-493">H.</span></span> <span data-ttu-id="ab218-494">建立 XML 格式檔案</span><span class="sxs-lookup"><span data-stu-id="ab218-494">Creating an XML format file</span></span>  
 <span data-ttu-id="ab218-495">下列範例會針對 `Currency.xml` 資料庫中的 `Sales.Currency` 資料表來建立名稱為 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 的 XML 格式檔。</span><span class="sxs-lookup"><span data-stu-id="ab218-495">The following example creates an XML format file named `Currency.xml` for the `Sales.Currency` table in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="ab218-496">這個範例假設您使用 Windows 驗證，且有信任連接通往您在執行 **bcp** 命令的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab218-496">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="ab218-497">請在 Windows 命令提示字元之下，輸入：</span><span class="sxs-lookup"><span data-stu-id="ab218-497">At the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency format nul -T -c -x -f Currency.xml  
```  
  
> [!NOTE]  
>  <span data-ttu-id="ab218-498">若要使用 **-x** 參數，您必須使用 **bcp** 9.0 用戶端。</span><span class="sxs-lookup"><span data-stu-id="ab218-498">To use the **-x** switch, you must be using a **bcp** 9.0 client.</span></span> <span data-ttu-id="ab218-499">如需有關如何使用**bcp** 9.0 用戶端的詳細資訊，請參閱「備註」。</span><span class="sxs-lookup"><span data-stu-id="ab218-499">For information about how to use the **bcp** 9.0 client, see "Remarks."</span></span>  
  
 <span data-ttu-id="ab218-500">如需詳細資訊，請參閱 [XML 格式檔案 &#40;SQL Server&#41;](../relational-databases/import-export/xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab218-500">For more information, see [XML Format Files &#40;SQL Server&#41;](../relational-databases/import-export/xml-format-files-sql-server.md).</span></span>  
  
### <a name="i-using-a-format-file-to-bulk-import-with-bcp"></a><span data-ttu-id="ab218-501">I.</span><span class="sxs-lookup"><span data-stu-id="ab218-501">I.</span></span> <span data-ttu-id="ab218-502">使用格式檔案以 bcp 進行大量匯入</span><span class="sxs-lookup"><span data-stu-id="ab218-502">Using a format file to bulk import with bcp</span></span>  
 <span data-ttu-id="ab218-503">若要在將資料匯入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的執行個體時使用先前所建立的格式檔案，請搭配 **in** 選項使用 **-f** 參數。</span><span class="sxs-lookup"><span data-stu-id="ab218-503">To use a previously created format file when importing data into an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], use the **-f** switch with the **in** option.</span></span> <span data-ttu-id="ab218-504">例如，下列命令會利用先前建立的格式檔案 (`Currency.dat`)，將 `Sales.Currency` 資料檔案的內容大量複製到 `Sales.Currency2` 資料表的複本 (`Currency.xml`) 中。</span><span class="sxs-lookup"><span data-stu-id="ab218-504">For example, the following command bulk copies the contents of a data file, `Currency.dat`, into a copy of the `Sales.Currency` table (`Sales.Currency2`) by using the previously created format file (`Currency.xml`).</span></span> <span data-ttu-id="ab218-505">這個範例假設您使用 Windows 驗證，且有信任連接通往您在執行 **bcp** 命令的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab218-505">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="ab218-506">請在 Windows 命令提示字元之下，輸入：</span><span class="sxs-lookup"><span data-stu-id="ab218-506">At the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency2 in Currency.dat -T -f Currency.xml  
```  
  
> [!NOTE]  
>  <span data-ttu-id="ab218-507">當資料檔案欄位與資料表資料行不同 (如號碼、排序或資料類型) 時，格式檔案就非常有用。</span><span class="sxs-lookup"><span data-stu-id="ab218-507">Format files are useful when the data file fields are different from the table columns; for example, in their number, ordering, or data types.</span></span> <span data-ttu-id="ab218-508">如需詳細資訊，請參閱 [匯入或匯出資料的格式檔案 &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ab218-508">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="ab218-509">其他範例</span><span class="sxs-lookup"><span data-stu-id="ab218-509">Additional Examples</span></span>  
 <span data-ttu-id="ab218-510">下列主題包含使用**bcp**的範例：</span><span class="sxs-lookup"><span data-stu-id="ab218-510">The following topics contain examples of using **bcp**:</span></span>  
  
-   [<span data-ttu-id="ab218-511">建立格式檔案 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ab218-511">Create a Format File &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="ab218-512">大量匯入與匯出 XML 文件的範例 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ab218-512">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [<span data-ttu-id="ab218-513">大量匯入資料時保留識別值 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ab218-513">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="ab218-514">大量匯入期間保留 Null 或使用預設值 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ab218-514">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="ab218-515">指定欄位與資料列結束字元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ab218-515">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)  
  
-   [<span data-ttu-id="ab218-516">使用格式檔案大量匯入資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ab218-516">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="ab218-517">使用字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ab218-517">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="ab218-518">使用原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ab218-518">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="ab218-519">使用 Unicode 字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ab218-519">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="ab218-520">使用 Unicode 原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ab218-520">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="ab218-521">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab218-521">See Also</span></span>  
 <span data-ttu-id="ab218-522">[準備大量匯出或匯入的資料 &#40;SQL Server&#41;](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ab218-522">[Prepare Data for Bulk Export or Import &#40;SQL Server&#41;](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md) </span></span>  
 <span data-ttu-id="ab218-523">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab218-523">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="ab218-524">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab218-524">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="ab218-525">[設定 QUOTED_IDENTIFIER &#40;Transact-sql&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab218-525">[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql) </span></span>  
 <span data-ttu-id="ab218-526">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab218-526">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="ab218-527">[sp_tableoption &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab218-527">[sp_tableoption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql) </span></span>  
 [<span data-ttu-id="ab218-528">匯入或匯出資料的格式檔案 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ab218-528">Format Files for Importing or Exporting Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)  
  
  
