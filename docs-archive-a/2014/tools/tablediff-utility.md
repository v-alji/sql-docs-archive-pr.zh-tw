---
title: tablediff 公用程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- comparing data
- tablediff utility
- tables [SQL Server replication]
- table comparisons [SQL Server]
- command prompt utilities [SQL Server], tablediff
- troubleshooting [SQL Server replication], non-convergence
- non-convergence [SQL Server]
ms.assetid: 3c3cb865-7a4d-4d66-98f2-5935e28929fc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0a23465a7d2c7db53475a6dca81a8471a3b78b50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704541"
---
# <a name="tablediff-utility"></a><span data-ttu-id="9670d-102">tablediff 公用程式</span><span class="sxs-lookup"><span data-stu-id="9670d-102">tablediff Utility</span></span>
  <span data-ttu-id="9670d-103">**tablediff** 公用程式用來比較兩份資料表之資料的非聚合狀況，當進行複寫拓撲中之非聚合狀況的疑難排解時，它尤其有用。</span><span class="sxs-lookup"><span data-stu-id="9670d-103">The **tablediff** utility is used to compare the data in two tables for non-convergence, and is particularly useful for troubleshooting non-convergence in a replication topology.</span></span> <span data-ttu-id="9670d-104">您可以在命令提示字元之下，或在批次檔中，利用這個公用程式來執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="9670d-104">This utility can be used from the command prompt or in a batch file to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="9670d-105">在 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的來源資料表 (作為複寫發行者) 與一或多個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的目的地資料表 (作為複寫訂閱者) 之間，逐一進行資料列比較。</span><span class="sxs-lookup"><span data-stu-id="9670d-105">A row by row comparison between a source table in an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] acting as a replication Publisher and the destination table at one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] acting as replication Subscribers.</span></span>  
  
-   <span data-ttu-id="9670d-106">執行快速比較，只比較資料列計數和結構描述。</span><span class="sxs-lookup"><span data-stu-id="9670d-106">Perform a fast comparison by only comparing row counts and schema.</span></span>  
  
-   <span data-ttu-id="9670d-107">進行資料行層級的比較。</span><span class="sxs-lookup"><span data-stu-id="9670d-107">Perform column-level comparisons.</span></span>  
  
-   <span data-ttu-id="9670d-108">產生 [!INCLUDE[tsql](../includes/tsql-md.md)] 指令碼來修正目的地伺服器不一致的情形，以便聚合來源和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="9670d-108">Generate a [!INCLUDE[tsql](../includes/tsql-md.md)] script to fix discrepancies at the destination server to bring the source and destination tables into convergence.</span></span>  
  
-   <span data-ttu-id="9670d-109">將結果記錄在輸出檔中，或記錄在目的地資料庫的資料表中。</span><span class="sxs-lookup"><span data-stu-id="9670d-109">Log results to an output file or into a table in the destination database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9670d-110">語法</span><span class="sxs-lookup"><span data-stu-id="9670d-110">Syntax</span></span>  
  
```  
  
      tablediff   
[ -? ] |   
{  
        -sourceserversource_server_name[\instance_name]  
        -sourcedatabasesource_database-sourcetablesource_table_name   
    [ -sourceschemasource_schema_name ]  
    [ -sourcepasswordsource_password ]  
    [ -sourceusersource_login ]  
    [ -sourcelocked ]  
        -destinationserverdestination_server_name[\instance_name]  
        -destinationdatabasesubscription_database-destinationtabledestination_table   
    [ -destinationschemadestination_schema_name ]  
    [ -destinationpassworddestination_password ]  
    [ -destinationuserdestination_login ]  
    [ -destinationlocked ]  
    [ -blarge_object_bytes ]   
    [ -bfnumber_of_statements ]   
    [ -c ]   
    [ -dt ]   
    [ -ettable_name ]   
    [ -f [ file_name ] ]   
    [ -ooutput_file_name ]   
    [ -q ]   
    [ -rcnumber_of_retries ]   
    [ -riretry_interval ]   
    [ -strict ]  
    [ -tconnection_timeouts ]   
}  
```  
  
## <a name="arguments"></a><span data-ttu-id="9670d-111">引數</span><span class="sxs-lookup"><span data-stu-id="9670d-111">Arguments</span></span>  
 <span data-ttu-id="9670d-112">[ **-?**</span><span class="sxs-lookup"><span data-stu-id="9670d-112">[ **-?**</span></span> <span data-ttu-id="9670d-113">]</span><span class="sxs-lookup"><span data-stu-id="9670d-113">]</span></span>  
 <span data-ttu-id="9670d-114">傳回支援的參數清單。</span><span class="sxs-lookup"><span data-stu-id="9670d-114">Returns the list of supported parameters.</span></span>  
  
 <span data-ttu-id="9670d-115">**-sourceserver** *source_server_name*[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="9670d-115">**-sourceserver** *source_server_name*[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="9670d-116">這是來源伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="9670d-116">Is the name of the source server.</span></span> <span data-ttu-id="9670d-117">指定預設實例的_來源 \_ 伺服器 \_ 名稱_ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9670d-117">Specify _source\_server\_name_ for the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9670d-118">針對的已命名實例指定_來源 \_ 伺服器 \_ 名稱_ **\\** _實例 \_ 名稱_ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9670d-118">Specify _source\_server\_name_**\\**_instance\_name_ for a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9670d-119">**-sourcedatabase** *source_database*</span><span class="sxs-lookup"><span data-stu-id="9670d-119">**-sourcedatabase** *source_database*</span></span>  
 <span data-ttu-id="9670d-120">這是來源資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="9670d-120">Is the name of the source database.</span></span>  
  
 <span data-ttu-id="9670d-121">**-sourcetable** *source_table_name*</span><span class="sxs-lookup"><span data-stu-id="9670d-121">**-sourcetable** *source_table_name*</span></span>  
 <span data-ttu-id="9670d-122">這是所檢查的來源資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="9670d-122">Is the name of the source table being checked.</span></span>  
  
 <span data-ttu-id="9670d-123">**-sourceschema** *source_schema_name*</span><span class="sxs-lookup"><span data-stu-id="9670d-123">**-sourceschema** *source_schema_name*</span></span>  
 <span data-ttu-id="9670d-124">來源資料表的結構描述擁有者。</span><span class="sxs-lookup"><span data-stu-id="9670d-124">The schema owner of the source table.</span></span> <span data-ttu-id="9670d-125">依預設，資料表擁有者假設為 dbo。</span><span class="sxs-lookup"><span data-stu-id="9670d-125">By default, the table owner is assumed to be dbo.</span></span>  
  
 <span data-ttu-id="9670d-126">**-sourcepassword** *source_password*</span><span class="sxs-lookup"><span data-stu-id="9670d-126">**-sourcepassword** *source_password*</span></span>  
 <span data-ttu-id="9670d-127">這是用來連接使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證之來源伺服器的登入密碼。</span><span class="sxs-lookup"><span data-stu-id="9670d-127">Is the password for the login used to connect to the source server using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9670d-128">可能的話，請在執行階段提供安全性認證。</span><span class="sxs-lookup"><span data-stu-id="9670d-128">When possible, supply security credentials at runtime.</span></span> <span data-ttu-id="9670d-129">如果您必須將認證儲存在指令碼檔案中，您應該維護這個檔案的安全性，使他人無法在未獲授權的情況下擅自存取。</span><span class="sxs-lookup"><span data-stu-id="9670d-129">If you must store credentials in a script file, you should secure the file to prevent unauthorized access.</span></span>  
  
 <span data-ttu-id="9670d-130">**-sourceuser** *source_login*</span><span class="sxs-lookup"><span data-stu-id="9670d-130">**-sourceuser** *source_login*</span></span>  
 <span data-ttu-id="9670d-131">這是用來連接使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證之來源伺服器的登入。</span><span class="sxs-lookup"><span data-stu-id="9670d-131">Is the login used to connect to the source server using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="9670d-132">如果未提供 *source_login* ，在連接到來源伺服器時，會使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="9670d-132">If *source_login* is not supplied, then Windows Authentication is used when connecting to the source server.</span></span> [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 <span data-ttu-id="9670d-133">**-sourcelocked**</span><span class="sxs-lookup"><span data-stu-id="9670d-133">**-sourcelocked**</span></span>  
 <span data-ttu-id="9670d-134">在比較期間，來源資料表以 TABLOCK 和 HOLDLOCK 資料表提示鎖定。</span><span class="sxs-lookup"><span data-stu-id="9670d-134">The source table is locked during the comparison using the TABLOCK and HOLDLOCK table hints.</span></span>  
  
 <span data-ttu-id="9670d-135">**-destinationserver** *destination_server_name*[ **\\** _實例 \_ 名稱_]</span><span class="sxs-lookup"><span data-stu-id="9670d-135">**-destinationserver** *destination_server_name*[**\\**_instance\_name_]</span></span>  
 <span data-ttu-id="9670d-136">這是目的地伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="9670d-136">Is the name of the destination server.</span></span> <span data-ttu-id="9670d-137">指定 *預設執行個體的* destination_server_name [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9670d-137">Specify *destination_server_name* for the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9670d-138">針對的已命名實例指定_目的地 \_ 伺服器 \_ 名稱_ **\\** _實例 \_ 名稱_ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9670d-138">Specify _destination\_server\_name_**\\**_instance\_name_ for a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9670d-139">**-destinationdatabase** *subscription_database*</span><span class="sxs-lookup"><span data-stu-id="9670d-139">**-destinationdatabase** *subscription_database*</span></span>  
 <span data-ttu-id="9670d-140">這是目的地資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="9670d-140">Is the name of the destination database.</span></span>  
  
 <span data-ttu-id="9670d-141">**-destinationtable** *destination_table*</span><span class="sxs-lookup"><span data-stu-id="9670d-141">**-destinationtable** *destination_table*</span></span>  
 <span data-ttu-id="9670d-142">這是目的地資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="9670d-142">Is the name of the destination table.</span></span>  
  
 <span data-ttu-id="9670d-143">**-destinationschema** *destination_schema_name*</span><span class="sxs-lookup"><span data-stu-id="9670d-143">**-destinationschema** *destination_schema_name*</span></span>  
 <span data-ttu-id="9670d-144">目的地資料表的結構描述擁有者。</span><span class="sxs-lookup"><span data-stu-id="9670d-144">The schema owner of the destination table.</span></span> <span data-ttu-id="9670d-145">依預設，資料表擁有者假設為 dbo。</span><span class="sxs-lookup"><span data-stu-id="9670d-145">By default, the table owner is assumed to be dbo.</span></span>  
  
 <span data-ttu-id="9670d-146">**-destinationpassword** *destination_password*</span><span class="sxs-lookup"><span data-stu-id="9670d-146">**-destinationpassword** *destination_password*</span></span>  
 <span data-ttu-id="9670d-147">這是用來連接使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證之目的地伺服器的登入密碼。</span><span class="sxs-lookup"><span data-stu-id="9670d-147">Is the password for the login used to connect to the destination server using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9670d-148">可能的話，請在執行階段提供安全性認證。</span><span class="sxs-lookup"><span data-stu-id="9670d-148">When possible, supply security credentials at runtime.</span></span> <span data-ttu-id="9670d-149">如果您必須將認證儲存在指令碼檔案中，您應該維護這個檔案的安全性，使他人無法在未獲授權的情況下擅自存取。</span><span class="sxs-lookup"><span data-stu-id="9670d-149">If you must store credentials in a script file, you should secure the file to prevent unauthorized access.</span></span>  
  
 <span data-ttu-id="9670d-150">**-destinationuser** *destination_login*</span><span class="sxs-lookup"><span data-stu-id="9670d-150">**-destinationuser** *destination_login*</span></span>  
 <span data-ttu-id="9670d-151">這是用來連接使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證之目的地伺服器的登入。</span><span class="sxs-lookup"><span data-stu-id="9670d-151">Is the login used to connect to the destination server using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="9670d-152">如果未提供 *destination_login* ，在連接到伺服器時，會使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="9670d-152">If *destination_login* is not supplied, then Windows Authentication is used when connecting to the server.</span></span> [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 <span data-ttu-id="9670d-153">**-destinationlocked**</span><span class="sxs-lookup"><span data-stu-id="9670d-153">**-destinationlocked**</span></span>  
 <span data-ttu-id="9670d-154">在比較期間，目的地資料表以 TABLOCK 和 HOLDLOCK 資料表提示鎖定。</span><span class="sxs-lookup"><span data-stu-id="9670d-154">The destination table is locked during the comparison using the TABLOCK and HOLDLOCK table hints.</span></span>  
  
 <span data-ttu-id="9670d-155">**-b** *large_object_bytes*</span><span class="sxs-lookup"><span data-stu-id="9670d-155">**-b** *large_object_bytes*</span></span>  
 <span data-ttu-id="9670d-156">這是用來進行下列大型物件資料類型之資料行比較的位元組數目，其中包括：`text`、`ntext`、`image`、`varchar(max)`、`nvarchar(max)` 和 `varbinary(max)`。</span><span class="sxs-lookup"><span data-stu-id="9670d-156">Is the number of bytes to compare for large object data type columns, which includes: `text`, `ntext`, `image`, `varchar(max)`, `nvarchar(max)` and `varbinary(max)`.</span></span> <span data-ttu-id="9670d-157">*large_object_bytes* 預設為資料行的大小。</span><span class="sxs-lookup"><span data-stu-id="9670d-157">*large_object_bytes* defaults to the size of the column.</span></span> <span data-ttu-id="9670d-158">不比較任何超出 *large_object_bytes* 的資料。</span><span class="sxs-lookup"><span data-stu-id="9670d-158">Any data above *large_object_bytes* will not be compared.</span></span>  
  
 <span data-ttu-id="9670d-159">**-bf**  *number_of_statements*</span><span class="sxs-lookup"><span data-stu-id="9670d-159">**-bf**  *number_of_statements*</span></span>  
 <span data-ttu-id="9670d-160">這是使用 [!INCLUDE[tsql](../includes/tsql-md.md)] -f [!INCLUDE[tsql](../includes/tsql-md.md)] 選項時要寫入目前 **指令碼檔案中的** 陳述式數目。</span><span class="sxs-lookup"><span data-stu-id="9670d-160">Is the number of [!INCLUDE[tsql](../includes/tsql-md.md)] statements to write to the current [!INCLUDE[tsql](../includes/tsql-md.md)] script file when the **-f** option is used.</span></span> <span data-ttu-id="9670d-161">當 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式數目超出 *number_of_statements*時，會建立新的 [!INCLUDE[tsql](../includes/tsql-md.md)] 指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="9670d-161">When the number of [!INCLUDE[tsql](../includes/tsql-md.md)] statements exceeds *number_of_statements*, a new [!INCLUDE[tsql](../includes/tsql-md.md)] script file is created.</span></span>  
  
 <span data-ttu-id="9670d-162">**-c**</span><span class="sxs-lookup"><span data-stu-id="9670d-162">**-c**</span></span>  
 <span data-ttu-id="9670d-163">比較資料行層級的差異。</span><span class="sxs-lookup"><span data-stu-id="9670d-163">Compare column-level differences.</span></span>  
  
 <span data-ttu-id="9670d-164">**-dt**</span><span class="sxs-lookup"><span data-stu-id="9670d-164">**-dt**</span></span>  
 <span data-ttu-id="9670d-165">卸除 *table_name*指定的結果資料表 (如果該資料表已存在的話)。</span><span class="sxs-lookup"><span data-stu-id="9670d-165">Drop the result table specified by *table_name*, if the table already exists.</span></span>  
  
 <span data-ttu-id="9670d-166">**-et** *table_name*</span><span class="sxs-lookup"><span data-stu-id="9670d-166">**-et** *table_name*</span></span>  
 <span data-ttu-id="9670d-167">指定要建立的結果資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="9670d-167">Specifies the name of the result table to create.</span></span> <span data-ttu-id="9670d-168">如果這份資料表已經存在，就必須使用 **-DT** ，否則作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="9670d-168">If this table already exists, **-DT** must be used or the operation will fail.</span></span>  
  
 <span data-ttu-id="9670d-169">**-f** [ *file_name* ]</span><span class="sxs-lookup"><span data-stu-id="9670d-169">**-f** [ *file_name* ]</span></span>  
 <span data-ttu-id="9670d-170">產生一份 [!INCLUDE[tsql](../includes/tsql-md.md)] 指令碼來聚合目的地伺服器的資料表與來源伺服器的資料表。</span><span class="sxs-lookup"><span data-stu-id="9670d-170">Generates a [!INCLUDE[tsql](../includes/tsql-md.md)] script to bring the table at the destination server into convergence with the table at the source server.</span></span> <span data-ttu-id="9670d-171">您可以選擇性地為所產生的 [!INCLUDE[tsql](../includes/tsql-md.md)] 指令碼檔案指定名稱和路徑。</span><span class="sxs-lookup"><span data-stu-id="9670d-171">You can optionally specify a name and path for the generated [!INCLUDE[tsql](../includes/tsql-md.md)] script file.</span></span> <span data-ttu-id="9670d-172">如果未指定 *file_name* ， [!INCLUDE[tsql](../includes/tsql-md.md)] 指令碼檔案會產生在執行公用程式的目錄中。</span><span class="sxs-lookup"><span data-stu-id="9670d-172">If *file_name* is not specified, the [!INCLUDE[tsql](../includes/tsql-md.md)] script file is generated in the directory where the utility runs.</span></span>  
  
 <span data-ttu-id="9670d-173">**-o** *output_file_name*</span><span class="sxs-lookup"><span data-stu-id="9670d-173">**-o** *output_file_name*</span></span>  
 <span data-ttu-id="9670d-174">這是輸出檔的完整名稱和路徑。</span><span class="sxs-lookup"><span data-stu-id="9670d-174">Is the full name and path of the output file.</span></span>  
  
 <span data-ttu-id="9670d-175">**-q**</span><span class="sxs-lookup"><span data-stu-id="9670d-175">**-q**</span></span>  
 <span data-ttu-id="9670d-176">執行快速比較，只比較資料列計數和結構描述。</span><span class="sxs-lookup"><span data-stu-id="9670d-176">Perform a fast comparison by only comparing row counts and schema.</span></span>  
  
 <span data-ttu-id="9670d-177">**-rc** *number_of_retries*</span><span class="sxs-lookup"><span data-stu-id="9670d-177">**-rc** *number_of_retries*</span></span>  
 <span data-ttu-id="9670d-178">公用程式重試失敗作業的次數。</span><span class="sxs-lookup"><span data-stu-id="9670d-178">Number of times that the utility retries a failed operation.</span></span>  
  
 <span data-ttu-id="9670d-179">**-ri**  *retry_interval*</span><span class="sxs-lookup"><span data-stu-id="9670d-179">**-ri**  *retry_interval*</span></span>  
 <span data-ttu-id="9670d-180">兩次重試之間等待的間隔秒數。</span><span class="sxs-lookup"><span data-stu-id="9670d-180">Interval, in seconds, to wait between retries.</span></span>  
  
 <span data-ttu-id="9670d-181">**-strict**</span><span class="sxs-lookup"><span data-stu-id="9670d-181">**-strict**</span></span>  
 <span data-ttu-id="9670d-182">嚴格比較來源和目的地結構描述。</span><span class="sxs-lookup"><span data-stu-id="9670d-182">Source and destination schema are strictly compared.</span></span>  
  
 <span data-ttu-id="9670d-183">**-t** *connection_timeouts*</span><span class="sxs-lookup"><span data-stu-id="9670d-183">**-t** *connection_timeouts*</span></span>  
 <span data-ttu-id="9670d-184">設定通往來源伺服器和目的地伺服器之連接的連接逾時期限 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="9670d-184">Sets the connection timeout period, in seconds, for connections to the source server and destination server.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9670d-185">傳回值</span><span class="sxs-lookup"><span data-stu-id="9670d-185">Return Value</span></span>  
  
|<span data-ttu-id="9670d-186">值</span><span class="sxs-lookup"><span data-stu-id="9670d-186">Value</span></span>|<span data-ttu-id="9670d-187">描述</span><span class="sxs-lookup"><span data-stu-id="9670d-187">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9670d-188">**0**</span><span class="sxs-lookup"><span data-stu-id="9670d-188">**0**</span></span>|<span data-ttu-id="9670d-189">Success</span><span class="sxs-lookup"><span data-stu-id="9670d-189">Success</span></span>|  
|<span data-ttu-id="9670d-190">**1**</span><span class="sxs-lookup"><span data-stu-id="9670d-190">**1**</span></span>|<span data-ttu-id="9670d-191">嚴重錯誤</span><span class="sxs-lookup"><span data-stu-id="9670d-191">Critical error</span></span>|  
|<span data-ttu-id="9670d-192">**2**</span><span class="sxs-lookup"><span data-stu-id="9670d-192">**2**</span></span>|<span data-ttu-id="9670d-193">資料表差異</span><span class="sxs-lookup"><span data-stu-id="9670d-193">Table differences</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9670d-194">備註</span><span class="sxs-lookup"><span data-stu-id="9670d-194">Remarks</span></span>  
 <span data-ttu-id="9670d-195">**Tablediff**公用程式不能與非伺服器一起使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9670d-195">The **tablediff** utility cannot be used with non-[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] servers.</span></span>  
  
 <span data-ttu-id="9670d-196">具有 `sql_variant` 資料類型資料行的資料表不受支援。</span><span class="sxs-lookup"><span data-stu-id="9670d-196">Tables with `sql_variant` data type columns are not supported.</span></span>  
  
 <span data-ttu-id="9670d-197">根據預設， **tablediff** 公用程式支援來源和目的地資料行之間的下列資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="9670d-197">By default, the **tablediff** utility supports the following data type mappings between source and destination columns.</span></span>  
  
|<span data-ttu-id="9670d-198">來源資料類型</span><span class="sxs-lookup"><span data-stu-id="9670d-198">Source data type</span></span>|<span data-ttu-id="9670d-199">目的地資料類型</span><span class="sxs-lookup"><span data-stu-id="9670d-199">Destination data type</span></span>|  
|----------------------|---------------------------|  
|`tinyint`|<span data-ttu-id="9670d-200">`smallint`、`int` 或 `bigint`</span><span class="sxs-lookup"><span data-stu-id="9670d-200">`smallint`, `int`, or `bigint`</span></span>|  
|`smallint`|<span data-ttu-id="9670d-201">`int` 或 `bigint`</span><span class="sxs-lookup"><span data-stu-id="9670d-201">`int` or `bigint`</span></span>|  
|`int`|`bigint`|  
|`timestamp`|`varbinary`|  
|`varchar(max)`|`text`|  
|`nvarchar(max)`|`ntext`|  
|`varbinary(max)`|`image`|  
|`text`|`varchar(max)`|  
|`ntext`|`nvarchar(max)`|  
|`image`|`varbinary(max)`|  
  
 <span data-ttu-id="9670d-202">使用 **-strict** 選項可禁止這些對應並執行嚴格驗證。</span><span class="sxs-lookup"><span data-stu-id="9670d-202">Use the **-strict** option to disallow these mappings and perform a strict validation.</span></span>  
  
 <span data-ttu-id="9670d-203">比較中的來源資料表必須至少包含一個主索引鍵、身分識別或 ROWGUID 資料行。</span><span class="sxs-lookup"><span data-stu-id="9670d-203">The source table in the comparison must contain at least one primary key, identity, or ROWGUID column.</span></span> <span data-ttu-id="9670d-204">當您使用 **-strict** 選項時，目的地資料表也必須有主索引鍵、識別或 ROWGUID 資料行。</span><span class="sxs-lookup"><span data-stu-id="9670d-204">When you use the **-strict** option, the destination table must also have a primary key, identity, or ROWGUID column.</span></span>  
  
 <span data-ttu-id="9670d-205">為了使目的地資料表達到聚合而產生的 [!INCLUDE[tsql](../includes/tsql-md.md)] 指令碼不包括下列資料類型：</span><span class="sxs-lookup"><span data-stu-id="9670d-205">The [!INCLUDE[tsql](../includes/tsql-md.md)] script generated to bring the destination table into convergence does not include the following data types:</span></span>  
  
-   `varchar(max)`  
  
-   `nvarchar(max)`  
  
-   `varbinary(max)`  
  
-   `timestamp`  
  
-   <span data-ttu-id="9670d-206">**xml**</span><span class="sxs-lookup"><span data-stu-id="9670d-206">**xml**</span></span>  
  
-   `text`  
  
-   `ntext`  
  
-   `image`  
  
## <a name="permissions"></a><span data-ttu-id="9670d-207">權限</span><span class="sxs-lookup"><span data-stu-id="9670d-207">Permissions</span></span>  
 <span data-ttu-id="9670d-208">若要比較資料表，您必須具有所比較之資料表物件的 SELECT ALL 權限。</span><span class="sxs-lookup"><span data-stu-id="9670d-208">To compare tables, you need SELECT ALL permissions on the table objects being compared.</span></span>  
  
 <span data-ttu-id="9670d-209">若要使用 **-et** 選項，您必須是 db_owner 固定資料庫角色的成員，或至少具有訂閱資料庫中的 CREATE TABLE 權限，或目的地伺服器之目的地擁有者結構描述的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="9670d-209">To use the **-et** option, you must be a member of the db_owner fixed database role, or at least have CREATE TABLE permission in the subscription database and ALTER permission on the destination owner schema at the destination server.</span></span>  
  
 <span data-ttu-id="9670d-210">若要使用 **-dt** 選項，您必須是 db_owner 固定資料庫角色的成員，或至少具有目的地伺服器之目的地擁有者結構描述的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="9670d-210">To use the **-dt** option, you must be a member of the db_owner fixed database role, or at least have ALTER permission on the destination owner schema at the destination server.</span></span>  
  
 <span data-ttu-id="9670d-211">若要使用 **-o** 或 **-f** 選項，您必須具有指定檔案目錄位置的寫入權限。</span><span class="sxs-lookup"><span data-stu-id="9670d-211">To use the **-o** or **-f** options, you must have write permissions to the specified file directory location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9670d-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9670d-212">See Also</span></span>  
 [<span data-ttu-id="9670d-213">比較複寫資料表的差異 &#40;複寫程式設計&#41;</span><span class="sxs-lookup"><span data-stu-id="9670d-213">Compare Replicated Tables for Differences &#40;Replication Programming&#41;</span></span>](../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md)  
  
  
