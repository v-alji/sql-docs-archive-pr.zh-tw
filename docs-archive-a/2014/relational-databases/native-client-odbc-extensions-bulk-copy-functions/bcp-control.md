---
title: bcp_control |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_control
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_control function
ms.assetid: 32187282-1385-4c52-9134-09f061eb44f5
author: rothja
ms.author: jroth
ms.openlocfilehash: 7ea5d60da8069707a53f3bdf2de53345cd11090f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584481"
---
# <a name="bcp_control"></a><span data-ttu-id="c1e97-102">bcp_control</span><span class="sxs-lookup"><span data-stu-id="c1e97-102">bcp_control</span></span>
  <span data-ttu-id="c1e97-103">針對檔案和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之間的大量複製，變更各種控制項參數的預設設定。</span><span class="sxs-lookup"><span data-stu-id="c1e97-103">Changes the default settings for various control parameters for a bulk copy between a file and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1e97-104">語法</span><span class="sxs-lookup"><span data-stu-id="c1e97-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_control (  
HDBC   
hdbc  
,  
INT   
eOption  
,  
void*   
iValue  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="c1e97-105">引數</span><span class="sxs-lookup"><span data-stu-id="c1e97-105">Arguments</span></span>  
 <span data-ttu-id="c1e97-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="c1e97-106">*hdbc*</span></span>  
 <span data-ttu-id="c1e97-107">這是已啟用大量複製的 ODBC 連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="c1e97-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="c1e97-108">*eOption*</span><span class="sxs-lookup"><span data-stu-id="c1e97-108">*eOption*</span></span>  
 <span data-ttu-id="c1e97-109">為下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="c1e97-109">Is one of the following:</span></span>  
  
 <span data-ttu-id="c1e97-110">BCPABORT</span><span class="sxs-lookup"><span data-stu-id="c1e97-110">BCPABORT</span></span>  
 <span data-ttu-id="c1e97-111">停止已經進行的大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="c1e97-111">Stops a bulk-copy operation that is already in progress.</span></span> <span data-ttu-id="c1e97-112">從另一個執行緒呼叫具有 BCPABORT *eOption*的**bcp_control** ，以停止執行大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="c1e97-112">Call **bcp_control** with an *eOption* of BCPABORT from another thread to stop a running bulk copy operation.</span></span> <span data-ttu-id="c1e97-113">*IValue*參數會被忽略。</span><span class="sxs-lookup"><span data-stu-id="c1e97-113">The *iValue* parameter is ignored.</span></span>  
  
 <span data-ttu-id="c1e97-114">BCPBATCH</span><span class="sxs-lookup"><span data-stu-id="c1e97-114">BCPBATCH</span></span>  
 <span data-ttu-id="c1e97-115">這是每一批次中的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="c1e97-115">Is the number of rows per batch.</span></span> <span data-ttu-id="c1e97-116">預設值為 0，這表示在擷取資料時，會指出資料表中的所有資料列，或在資料複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，會指出使用者資料檔中的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="c1e97-116">The default is 0, which indicates either all rows in a table, when data is being extracted, or all rows in the user data file, when data is being copied to an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c1e97-117">小於 1 的值會重設 BCPBATCH 為預設值。</span><span class="sxs-lookup"><span data-stu-id="c1e97-117">A value less than 1 resets BCPBATCH to the default.</span></span>  
  
 <span data-ttu-id="c1e97-118">BCPDELAYREADFMT</span><span class="sxs-lookup"><span data-stu-id="c1e97-118">BCPDELAYREADFMT</span></span>  
 <span data-ttu-id="c1e97-119">布林值，如果設定為 true，將會導致[bcp_readfmt](bcp-readfmt.md)在執行時讀取。</span><span class="sxs-lookup"><span data-stu-id="c1e97-119">A Boolean, if set to true, will cause [bcp_readfmt](bcp-readfmt.md) to read at execution.</span></span> <span data-ttu-id="c1e97-120">如果為 false (預設) ，bcp_readfmt 會立即讀取格式檔案。</span><span class="sxs-lookup"><span data-stu-id="c1e97-120">If false (the default), bcp_readfmt will immediately read the format file.</span></span> <span data-ttu-id="c1e97-121">如果 BCPDELAYREADFMT 為 true，而且您呼叫 bcp_columns 或 bcp_setcolfmt，就會發生順序錯誤。</span><span class="sxs-lookup"><span data-stu-id="c1e97-121">A sequence error will occur if BCPDELAYREADFMT is true and you call bcp_columns or bcp_setcolfmt.</span></span>  
  
 <span data-ttu-id="c1e97-122">`bcp_control(hdbc,` `, (void *)FALSE)` 呼叫 `bcp_control(hdbc,` BCPDELAYREADFMT `, (void *)TRUE)` 和 bcp_writefmt 之後，如果您呼叫 BCPDELAYREADFMT，也會發生順序錯誤。</span><span class="sxs-lookup"><span data-stu-id="c1e97-122">A sequence error will also occur if you call `bcp_control(hdbc,` BCPDELAYREADFMT`, (void *)FALSE)` after calling `bcp_control(hdbc,` BCPDELAYREADFMT`, (void *)TRUE)` and bcp_writefmt.</span></span>  
  
 <span data-ttu-id="c1e97-123">如需詳細資訊，請參閱[中繼資料探索](../native-client/features/metadata-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="c1e97-123">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
 <span data-ttu-id="c1e97-124">BCPFILECP</span><span class="sxs-lookup"><span data-stu-id="c1e97-124">BCPFILECP</span></span>  
 <span data-ttu-id="c1e97-125">*iValue*包含資料檔案的字碼頁數目。</span><span class="sxs-lookup"><span data-stu-id="c1e97-125">*iValue* contains the number of the code page for the data file.</span></span> <span data-ttu-id="c1e97-126">您可以指定字碼頁的數目，例如 1252 或 850，或以下任一個值：</span><span class="sxs-lookup"><span data-stu-id="c1e97-126">You can specify the number of the code page, such as 1252 or 850, or one of these values:</span></span>  
  
 <span data-ttu-id="c1e97-127">BCPFILE_ACP：檔案中的資料是在 Microsoft Windows 嗎？</span><span class="sxs-lookup"><span data-stu-id="c1e97-127">BCPFILE_ACP: data in the file is in the Microsoft Windows??</span></span> <span data-ttu-id="c1e97-128">用戶端的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="c1e97-128">code page of the client.</span></span>  
  
 <span data-ttu-id="c1e97-129">BCPFILE_OEMCP：檔案中的資料位於用戶端的 OEM 字碼頁 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="c1e97-129">BCPFILE_OEMCP: data in the file is in the OEM code page of the client (default).</span></span>  
  
 <span data-ttu-id="c1e97-130">BCPFILE_RAW：檔案中的資料位於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="c1e97-130">BCPFILE_RAW: data in the file is in the code page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c1e97-131">BCPFILEFMT</span><span class="sxs-lookup"><span data-stu-id="c1e97-131">BCPFILEFMT</span></span>  
 <span data-ttu-id="c1e97-132">資料檔案格式的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="c1e97-132">The version number of the data file format.</span></span> <span data-ttu-id="c1e97-133">這個號碼可以是 80 ([!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)])、90 ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)])、100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)])、110 ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) 或 120 ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="c1e97-133">This can be 80 ([!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]), 90 ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]), 100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]), 110 ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]), or 120 ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]).</span></span> <span data-ttu-id="c1e97-134">120 是預設值。</span><span class="sxs-lookup"><span data-stu-id="c1e97-134">120 is the default.</span></span> <span data-ttu-id="c1e97-135">這個值在使用舊版伺服器支援的格式匯出和匯入資料時非常實用。</span><span class="sxs-lookup"><span data-stu-id="c1e97-135">This is useful for exporting and importing data in formats that were supported by earlier version of the server.</span></span> <span data-ttu-id="c1e97-136">例如，若要將從伺服器文字資料行取得的資料匯入 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 至或更新版本之伺服器中的\*\*Varchar (max) \*\*資料行 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ，您應該指定80。</span><span class="sxs-lookup"><span data-stu-id="c1e97-136">For example, to import data that was obtained from a text column in a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] server into a **varchar(max)** column in a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later server, you should specify 80.</span></span> <span data-ttu-id="c1e97-137">同樣地，如果您在從\*\*Varchar (max) \*\*資料行匯出資料時指定80，則會儲存它，就像是以格式儲存文字資料行， [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 而且可以匯入到伺服器的文字資料行 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c1e97-137">Similarly, if you specify 80 when exporting data from a **varchar(max)** column, it will be saved just like text columns are saved in the [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] format, and can be imported into a text column of a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] server.</span></span>  
  
 <span data-ttu-id="c1e97-138">BCPFIRST</span><span class="sxs-lookup"><span data-stu-id="c1e97-138">BCPFIRST</span></span>  
 <span data-ttu-id="c1e97-139">這是要複製的檔案或資料表的第一個資料列。</span><span class="sxs-lookup"><span data-stu-id="c1e97-139">Is the first row of data to file or table to copy.</span></span> <span data-ttu-id="c1e97-140">預設值為 1，小於 1 的值會將這個選項重設為預設。</span><span class="sxs-lookup"><span data-stu-id="c1e97-140">The default is 1; a value less than 1 resets this option to its default.</span></span>  
  
 <span data-ttu-id="c1e97-141">BCPFIRSTEX</span><span class="sxs-lookup"><span data-stu-id="c1e97-141">BCPFIRSTEX</span></span>  
 <span data-ttu-id="c1e97-142">如果是 BCP Out 作業，則指定將資料庫資料表第一個資料列複製到資料檔案中。</span><span class="sxs-lookup"><span data-stu-id="c1e97-142">For BCP out operations, specifies the first row of the database table to copy into the data file.</span></span>  
  
 <span data-ttu-id="c1e97-143">如果是 BCP In 作業，則指定將資料檔案的第一個資料列複製到資料庫資料表中。</span><span class="sxs-lookup"><span data-stu-id="c1e97-143">For BCP in operations, specifies the first row of the data file to copy into the database table.</span></span>  
  
 <span data-ttu-id="c1e97-144">*IValue*參數應該是包含值的帶正負號64位整數的位址。</span><span class="sxs-lookup"><span data-stu-id="c1e97-144">The *iValue* parameter is expected to be the address of a signed 64-bit integer containing the value.</span></span> <span data-ttu-id="c1e97-145">可傳遞至 BCPFIRSTEX 的最大值為 2^63-1。</span><span class="sxs-lookup"><span data-stu-id="c1e97-145">The maximum value that can be passed to BCPFIRSTEX is 2^63-1.</span></span>  
  
 <span data-ttu-id="c1e97-146">BCPFMTXML</span><span class="sxs-lookup"><span data-stu-id="c1e97-146">BCPFMTXML</span></span>  
 <span data-ttu-id="c1e97-147">指定所產生的格式檔案應該是 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="c1e97-147">Specifies that the format file generated should be in XML format.</span></span> <span data-ttu-id="c1e97-148">預設為關閉。</span><span class="sxs-lookup"><span data-stu-id="c1e97-148">It is off by default.</span></span>  
  
 <span data-ttu-id="c1e97-149">XML 格式檔案提供更高的彈性，但是需要加入一些條件約束。</span><span class="sxs-lookup"><span data-stu-id="c1e97-149">XML format files provide greater flexibility but with some added constraints.</span></span> <span data-ttu-id="c1e97-150">例如，您不可以同時指定欄位的前置詞和結束字元，即使在舊版的格式檔案中可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="c1e97-150">For example, you can not specify the prefix and terminator for a field simultaneously, which was possible in older format files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c1e97-151">XML 格式檔案只有在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 一起安裝時才受到支援。</span><span class="sxs-lookup"><span data-stu-id="c1e97-151">XML format files are only supported when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed along with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="c1e97-152">BCPHINTS</span><span class="sxs-lookup"><span data-stu-id="c1e97-152">BCPHINTS</span></span>  
 <span data-ttu-id="c1e97-153">*iValue*包含 SQLTCHAR 字元字串指標。</span><span class="sxs-lookup"><span data-stu-id="c1e97-153">*iValue* contains an SQLTCHAR character string pointer.</span></span> <span data-ttu-id="c1e97-154">定址的字串會指定處理提示的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 大量複製或傳回結果集的 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c1e97-154">The string addressed specifies either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk-copy processing hints or a Transact-SQL statement that returns a result set.</span></span> <span data-ttu-id="c1e97-155">如果 Transact-SQL 陳述式指定為傳回一個以上的結果集，則第一個結果集之後的所有結果集都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="c1e97-155">If a Transact-SQL statement is specified that returns more than one result set, all result sets after the first are ignored.</span></span> <span data-ttu-id="c1e97-156">如需大量複製處理提示的詳細資訊，請參閱[Bcp Utility](../../tools/bcp-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="c1e97-156">For more information about bulk-copy processing hints, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
 <span data-ttu-id="c1e97-157">BCPKEEPIDENTITY</span><span class="sxs-lookup"><span data-stu-id="c1e97-157">BCPKEEPIDENTITY</span></span>  
 <span data-ttu-id="c1e97-158">當*iValue*為 TRUE 時，指定大量複製函數會插入為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用 identity 條件約束所定義之資料行提供的資料值。</span><span class="sxs-lookup"><span data-stu-id="c1e97-158">When *iValue* is TRUE, specifies that bulk copy functions insert data values supplied for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columns defined with an identity constraint.</span></span> <span data-ttu-id="c1e97-159">輸入檔案必須提供識別資料行的值。</span><span class="sxs-lookup"><span data-stu-id="c1e97-159">The input file must supply values for the identity columns.</span></span> <span data-ttu-id="c1e97-160">如果沒有設定，就會為插入的資料列產生新的識別值。</span><span class="sxs-lookup"><span data-stu-id="c1e97-160">If this is not set, new identity values are generated for the inserted rows.</span></span> <span data-ttu-id="c1e97-161">檔案中屬於識別欄位的所有資料都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="c1e97-161">Any data present in the file for the identity columns is ignored.</span></span>  
  
 <span data-ttu-id="c1e97-162">BCPKEEPNULLS</span><span class="sxs-lookup"><span data-stu-id="c1e97-162">BCPKEEPNULLS</span></span>  
 <span data-ttu-id="c1e97-163">指定檔案中的空資料值在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中是否會轉換為 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="c1e97-163">Specifies whether empty data values in the file will be converted to NULL values in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="c1e97-164">當*iValue*為 TRUE 時，空值會在資料表中轉換成 Null [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c1e97-164">When *iValue* is TRUE, empty values will be converted to NULL in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="c1e97-165">預設是將空的值轉換為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中資料行的預設值 (如果有預設值的話)。</span><span class="sxs-lookup"><span data-stu-id="c1e97-165">The default is for empty values to be converted to a default value for the column in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table if a default exists.</span></span>  
  
 <span data-ttu-id="c1e97-166">BCPLAST</span><span class="sxs-lookup"><span data-stu-id="c1e97-166">BCPLAST</span></span>  
 <span data-ttu-id="c1e97-167">這是要複製的最後一個資料列。</span><span class="sxs-lookup"><span data-stu-id="c1e97-167">Is the last row to copy.</span></span> <span data-ttu-id="c1e97-168">預設是複製所有的資料列；小於 1 的值會將這個選項重設為預設值。</span><span class="sxs-lookup"><span data-stu-id="c1e97-168">The default is to copy all rows; a value less than 1 resets this option to its default.</span></span>  
  
 <span data-ttu-id="c1e97-169">BCPLASTEX</span><span class="sxs-lookup"><span data-stu-id="c1e97-169">BCPLASTEX</span></span>  
 <span data-ttu-id="c1e97-170">如果是 BCP Out 作業，則指定將資料庫資料表最後一個資料列複製到資料檔案中。</span><span class="sxs-lookup"><span data-stu-id="c1e97-170">For BCP out operations, specifies the last row of the database table to copy into the data file.</span></span>  
  
 <span data-ttu-id="c1e97-171">如果是 BCP In 作業，則指定將資料檔案的最後一個資料列複製到資料庫資料表中。</span><span class="sxs-lookup"><span data-stu-id="c1e97-171">For BCP in operations, specifies the last row of the data file to copy into the database table.</span></span>  
  
 <span data-ttu-id="c1e97-172">*IValue*參數應該是包含值的帶正負號64位整數的位址。</span><span class="sxs-lookup"><span data-stu-id="c1e97-172">The *iValue* parameter is expected to be the address of a signed 64-bit integer containing the value.</span></span> <span data-ttu-id="c1e97-173">可傳遞至 BCPLASTEX 的最大值是 2^63-1。</span><span class="sxs-lookup"><span data-stu-id="c1e97-173">The maximum value that can be passed to BCPLASTEX is 2^63-1.</span></span>  
  
 <span data-ttu-id="c1e97-174">BCPMAXERRS</span><span class="sxs-lookup"><span data-stu-id="c1e97-174">BCPMAXERRS</span></span>  
 <span data-ttu-id="c1e97-175">這是在大量複製作業失敗之前所允許的錯誤數目。</span><span class="sxs-lookup"><span data-stu-id="c1e97-175">Is the number of errors allowed before the bulk copy operation fails.</span></span> <span data-ttu-id="c1e97-176">預設值為 10;小於1的值會將這個選項重設為預設值。</span><span class="sxs-lookup"><span data-stu-id="c1e97-176">The default is 10; a value less than 1 resets this option to its default.</span></span> <span data-ttu-id="c1e97-177">大量複製會限制 65,535 個錯誤的上限。</span><span class="sxs-lookup"><span data-stu-id="c1e97-177">Bulk copy imposes a maximum of 65,535 errors.</span></span> <span data-ttu-id="c1e97-178">如果嘗試將這個選項設為大於 65,535 的值，則該選項會設定為 65,535。</span><span class="sxs-lookup"><span data-stu-id="c1e97-178">An attempt to set this option to a value larger than 65,535 results in the option being set to 65,535.</span></span>  
  
 <span data-ttu-id="c1e97-179">BCPODBC</span><span class="sxs-lookup"><span data-stu-id="c1e97-179">BCPODBC</span></span>  
 <span data-ttu-id="c1e97-180">當為 TRUE 時，指定以字元格式儲存的**datetime**和**Smalldatetime**值將會使用 ODBC 時間戳記 escape 序列前置詞和後置詞。</span><span class="sxs-lookup"><span data-stu-id="c1e97-180">When TRUE, specifies that **datetime** and **smalldatetime** values saved in character format will use the ODBC timestamp escape sequence prefix and suffix.</span></span> <span data-ttu-id="c1e97-181">BCPODBC 選項只適用於 BCP_OUT。</span><span class="sxs-lookup"><span data-stu-id="c1e97-181">The BCPODBC option only applies to BCP_OUT.</span></span>  
  
 <span data-ttu-id="c1e97-182">若為 FALSE，則會將代表1997年1月1日的**datetime**值轉換成字元字串： 1997-01-01 00：00：00.000。</span><span class="sxs-lookup"><span data-stu-id="c1e97-182">When FALSE, a **datetime** value representing January 1, 1997 is converted to the character string: 1997-01-01 00:00:00.000.</span></span> <span data-ttu-id="c1e97-183">當為 TRUE 時，相同的**datetime**值會表示為： {ts ' 1997-01-01 00：00： 00.000 '}。</span><span class="sxs-lookup"><span data-stu-id="c1e97-183">When TRUE, the same **datetime** value is represented as: {ts '1997-01-01 00:00:00.000'}.</span></span>  
  
 <span data-ttu-id="c1e97-184">BCPROWCOUNT</span><span class="sxs-lookup"><span data-stu-id="c1e97-184">BCPROWCOUNT</span></span>  
 <span data-ttu-id="c1e97-185">傳回受到目前 (或最近) BCP 作業影響的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="c1e97-185">Returns the number of rows affected by the current (or last) BCP operation.</span></span>  
  
 <span data-ttu-id="c1e97-186">BCPTEXTFILE</span><span class="sxs-lookup"><span data-stu-id="c1e97-186">BCPTEXTFILE</span></span>  
 <span data-ttu-id="c1e97-187">當設定為 TRUE 時，這個選項會指定資料檔為文字檔，而不是二進位檔。</span><span class="sxs-lookup"><span data-stu-id="c1e97-187">When TRUE, specifies that the data file is a text file, rather than a binary file.</span></span> <span data-ttu-id="c1e97-188">如果檔案為文字檔，則 BCP 會藉由在資料檔的頭 2 個位元組中檢查 Unicode 位元組標記，判斷文字檔是否為 Unicode。</span><span class="sxs-lookup"><span data-stu-id="c1e97-188">If the file is a text file, BCP determines whether or not it is Unicode by checking the Unicode byte marker in the first two bytes of the data file.</span></span>  
  
 <span data-ttu-id="c1e97-189">BCPUNICODEFILE</span><span class="sxs-lookup"><span data-stu-id="c1e97-189">BCPUNICODEFILE</span></span>  
 <span data-ttu-id="c1e97-190">當設定為 TRUE 時，這個選項會指定輸入檔為 Unicode 檔案格式。</span><span class="sxs-lookup"><span data-stu-id="c1e97-190">When TRUE, specifies the input file is a Unicode file.</span></span>  
  
 <span data-ttu-id="c1e97-191">*iValue*</span><span class="sxs-lookup"><span data-stu-id="c1e97-191">*iValue*</span></span>  
 <span data-ttu-id="c1e97-192">這是指定之*eOption*的值。</span><span class="sxs-lookup"><span data-stu-id="c1e97-192">Is the value for the specified *eOption*.</span></span> <span data-ttu-id="c1e97-193">*iValue*是整數， (LONGLONG 轉換成 void 指標的) 值，以允許未來擴充至64位值。</span><span class="sxs-lookup"><span data-stu-id="c1e97-193">*iValue* is an integer (LONGLONG) value cast to a void pointer to allow for future expansion to 64 bit values.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="c1e97-194">傳回</span><span class="sxs-lookup"><span data-stu-id="c1e97-194">Returns</span></span>  
 <span data-ttu-id="c1e97-195">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="c1e97-195">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1e97-196">備註</span><span class="sxs-lookup"><span data-stu-id="c1e97-196">Remarks</span></span>  
 <span data-ttu-id="c1e97-197">此函數會設定各種大量複製作業的控制參數，包含取消大量複製之前所允許的錯誤次數、從資料檔複製的第一個和最後一個資料列的數目，以及批次大小。</span><span class="sxs-lookup"><span data-stu-id="c1e97-197">This function sets various control parameters for bulk-copy operations, including the number of errors allowed before canceling a bulk copy, the numbers of the first and last rows to copy from a data file, and the batch size.</span></span>  
  
 <span data-ttu-id="c1e97-198">從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 大量複製 SELECT 的結果集時，這個函數也可用來指定 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c1e97-198">This function is also used to specify the SELECT statement when bulk copying out from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] the result set of a SELECT.</span></span> <span data-ttu-id="c1e97-199">將*eOption*設定為 BCPHINTS，並將*iValue*設定為具有包含 SELECT 語句之 SQLTCHAR 字串的指標。</span><span class="sxs-lookup"><span data-stu-id="c1e97-199">Set *eOption* to BCPHINTS and set *iValue* to have a pointer to an SQLTCHAR string containing the SELECT statement.</span></span>  
  
 <span data-ttu-id="c1e97-200">只有在使用者檔案和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表之間進行複製時，這些控制項參數才有意義。</span><span class="sxs-lookup"><span data-stu-id="c1e97-200">These control parameters are only meaningful when copying between a user file and an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="c1e97-201">控制項參數設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 對於使用[bcp_sendrow](bcp-sendrow.md)複製到的資料列不會有任何影響。</span><span class="sxs-lookup"><span data-stu-id="c1e97-201">Control parameter settings have no effect on rows copied to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1e97-202">範例</span><span class="sxs-lookup"><span data-stu-id="c1e97-202">Example</span></span>  
  
```  
// Variables like henv not specified.  
SQLHDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("address"), _T("address.add"), _T("addr.err"),  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the number of rows per batch.   
if (bcp_control(hdbc, BCPBATCH, (void*) 1000) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set file column count.   
if (bcp_columns(hdbc, 1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the file format.   
if (bcp_colfmt(hdbc, 1, 0, 0, SQL_VARLEN_DATA, '\n', 1, 1)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
printf_s("%ld rows processed by bulk copy.", nRowsProcessed);  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1e97-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1e97-203">See Also</span></span>  
 [<span data-ttu-id="c1e97-204">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="c1e97-204">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
