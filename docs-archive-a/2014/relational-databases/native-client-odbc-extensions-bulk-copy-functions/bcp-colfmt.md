---
title: bcp_colfmt |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_colfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_colfmt function
ms.assetid: 5c3b6299-80c7-4e84-8e69-4ff33009548e
author: rothja
ms.author: jroth
ms.openlocfilehash: f646f3aaf9a8f640d829020bd6762c07c406b61f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709377"
---
# <a name="bcp_colfmt"></a><span data-ttu-id="874b1-102">bcp_colfmt</span><span class="sxs-lookup"><span data-stu-id="874b1-102">bcp_colfmt</span></span>
  <span data-ttu-id="874b1-103">在使用者檔案中指定資料的來源或目標格式。</span><span class="sxs-lookup"><span data-stu-id="874b1-103">Specifies the source or target format of the data in a user file.</span></span> <span data-ttu-id="874b1-104">當做來源格式使用時， **bcp_colfmt**會將當做大量複製中資料來源使用之現有資料檔案的格式指定為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="874b1-104">When used as a source format, **bcp_colfmt** specifies the format of an existing data file used as the source of data in a bulk copy to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="874b1-105">當做目標格式使用時，會使用以**bcp_colfmt**指定的資料行格式建立資料檔案。</span><span class="sxs-lookup"><span data-stu-id="874b1-105">When used as a target format, the data file is created using the column formats specified with **bcp_colfmt**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="874b1-106">語法</span><span class="sxs-lookup"><span data-stu-id="874b1-106">Syntax</span></span>  
  
```  
  
RETCODE bcp_colfmt (  
HDBC   
hdbc  
,  
INT  
idxUserDataCol  
,  
BYTE   
eUserDataType  
,  
INT   
cbIndicator  
,  
DBINT   
cbUserData  
,  
LPCBYTE   
pUserDataTerm  
,  
INT   
cbUserDataTerm  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="874b1-107">引數</span><span class="sxs-lookup"><span data-stu-id="874b1-107">Arguments</span></span>  
 <span data-ttu-id="874b1-108">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="874b1-108">*hdbc*</span></span>  
 <span data-ttu-id="874b1-109">這是已啟用大量複製的 ODBC 連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="874b1-109">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="874b1-110">*idxUserDataCol*</span><span class="sxs-lookup"><span data-stu-id="874b1-110">*idxUserDataCol*</span></span>  
 <span data-ttu-id="874b1-111">這是使用者資料檔案中，要指定其格式的序數資料行編號。</span><span class="sxs-lookup"><span data-stu-id="874b1-111">Is the ordinal column number in the user data file for which the format is being specified.</span></span> <span data-ttu-id="874b1-112">第一個資料行是 1。</span><span class="sxs-lookup"><span data-stu-id="874b1-112">The first column is 1.</span></span>  
  
 <span data-ttu-id="874b1-113">*eUserDataType*</span><span class="sxs-lookup"><span data-stu-id="874b1-113">*eUserDataType*</span></span>  
 <span data-ttu-id="874b1-114">這是使用者檔案中，此資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="874b1-114">Is the data type of this column in the user file.</span></span> <span data-ttu-id="874b1-115">如果與資料庫資料表中對應資料行的資料類型不同 (*idxServerColumn*) ，大量複製就會轉換資料（如果可能的話）。</span><span class="sxs-lookup"><span data-stu-id="874b1-115">If different from the data type of the corresponding column in the database table (*idxServerColumn*), bulk copy converts the data if possible.</span></span>  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<span data-ttu-id="874b1-116">在*eUserDataType*參數中引進了 SQLXML 和 SQLUDT 資料類型標記的支援。</span><span class="sxs-lookup"><span data-stu-id="874b1-116">introduced support for SQLXML and SQLUDT data type tokens in the *eUserDataType* parameter.</span></span>  
  
 <span data-ttu-id="874b1-117">*EUserDataType*參數是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sqlncli 中的資料類型標記所列舉，而不是 ODBC C 資料類型枚舉器。</span><span class="sxs-lookup"><span data-stu-id="874b1-117">The *eUserDataType* parameter is enumerated by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type tokens in sqlncli.h, not the ODBC C data type enumerators.</span></span> <span data-ttu-id="874b1-118">例如，您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 專屬類型 SQLCHARACTER 來指定字元字串 ODBC type SQL_C_CHAR。</span><span class="sxs-lookup"><span data-stu-id="874b1-118">For example, you can specify a character string, ODBC type SQL_C_CHAR, using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific type SQLCHARACTER.</span></span>  
  
 <span data-ttu-id="874b1-119">若要指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型的預設資料表示法，將此參數設定為 0。</span><span class="sxs-lookup"><span data-stu-id="874b1-119">To specify the default data representation for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type, set this parameter to 0.</span></span>  
  
 <span data-ttu-id="874b1-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]當*EUSERDATATYPE*為 SQLDECIMAL 或 SQLNUMERIC 時，將大量複製到檔案中：</span><span class="sxs-lookup"><span data-stu-id="874b1-120">For a bulk copy out of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] into a file, when *eUserDataType* is SQLDECIMAL or SQLNUMERIC:</span></span>  
  
-   <span data-ttu-id="874b1-121">如果來源資料行不是**decimal**或**numeric**，就會使用預設的有效位數和小數位數。</span><span class="sxs-lookup"><span data-stu-id="874b1-121">If the source column is not **decimal** or **numeric**, the default precision and scale are used.</span></span>  
  
-   <span data-ttu-id="874b1-122">如果來源資料行是**小數**或**數值**，則會使用來源資料行的有效位數和小數位數。</span><span class="sxs-lookup"><span data-stu-id="874b1-122">If the source column is **decimal** or **numeric**, the precision and scale of the source column are used.</span></span>  
  
 <span data-ttu-id="874b1-123">*cbIndicator*</span><span class="sxs-lookup"><span data-stu-id="874b1-123">*cbIndicator*</span></span>  
 <span data-ttu-id="874b1-124">這是資料行資料內，長度/null 指標的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="874b1-124">Is the length, in bytes, of a length/null indicator within the column data.</span></span> <span data-ttu-id="874b1-125">有效的指標長度值為 0 (不使用指標時)、1、2、4 或 8。</span><span class="sxs-lookup"><span data-stu-id="874b1-125">Valid indicator length values are 0 (when using no indicator), 1, 2, 4, or 8.</span></span>  
  
 <span data-ttu-id="874b1-126">若要指定預設大量複製指標使用率，將此參數設定為 SQL_VARLEN_DATA。</span><span class="sxs-lookup"><span data-stu-id="874b1-126">To specify default bulk copy indicator usage, set this parameter to SQL_VARLEN_DATA.</span></span>  
  
 <span data-ttu-id="874b1-127">這些指標會出現在任何資料正前方的記憶體中，以及所套用之資料正前方的資料檔案中。</span><span class="sxs-lookup"><span data-stu-id="874b1-127">Indicators appear in memory directly before any data, and in the data file directly before the data to which they apply.</span></span>  
  
 <span data-ttu-id="874b1-128">如果使用多種指定資料檔案資料行長度的方式 (例如指標和最大資料行長度，或指標和結束字元順序)，大量複製會選擇導致複製最少量資料的方式。</span><span class="sxs-lookup"><span data-stu-id="874b1-128">If more than one means of specifying a data file column length is used (such as an indicator and a maximum column length, or an indicator and a terminator sequence), bulk copy chooses the one that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="874b1-129">大量複製在不透過使用者操作來調整資料格式時所產生的資料檔案，會在資料行資料長度可以改變，或資料行可以當做值接受 NULL 時包含指標。</span><span class="sxs-lookup"><span data-stu-id="874b1-129">Data files generated by bulk copy when no user intervention adjusts the format of the data contain indicators when the column data can vary in length or the column can accept NULL as a value.</span></span>  
  
 <span data-ttu-id="874b1-130">*cbUserData*</span><span class="sxs-lookup"><span data-stu-id="874b1-130">*cbUserData*</span></span>  
 <span data-ttu-id="874b1-131">這是使用者檔案中此資料行之資料的最大長度 (以位元組為單位)，不包括任何長度指標或結束字元的長度。</span><span class="sxs-lookup"><span data-stu-id="874b1-131">Is the maximum length, in bytes, of this column's data in the user file, not including the length of any length indicator or terminator.</span></span>  
  
 <span data-ttu-id="874b1-132">將*cbUserData*設定為 SQL_Null_DATA 表示資料檔案欄位中的所有值都是，或應設定為 Null。</span><span class="sxs-lookup"><span data-stu-id="874b1-132">Setting *cbUserData* to SQL_NULL_DATA indicates that all values in the data file column are, or should be set to NULL.</span></span>  
  
 <span data-ttu-id="874b1-133">將*cbUserData*設定為 SQL_VARLEN_DATA 表示系統應該決定每個資料行中的資料長度。</span><span class="sxs-lookup"><span data-stu-id="874b1-133">Setting *cbUserData* to SQL_VARLEN_DATA indicates that the system should determine the length of data in each column.</span></span> <span data-ttu-id="874b1-134">對於某些資料行，這可能表示長度/null 指標會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複本之資料前產生，或者表示該指標應該會在複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的資料中出現。</span><span class="sxs-lookup"><span data-stu-id="874b1-134">For some columns, this could mean that a length/null indicator is generated to precede data on a copy from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or that the indicator is expected in data copied to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="874b1-135">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是字元和二進位資料類型， *cbUserData*可以是 SQL_VARLEN_DATA、SQL_Null_DATA、0或某個正數值。</span><span class="sxs-lookup"><span data-stu-id="874b1-135">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character and binary data types, *cbUserData* can be SQL_VARLEN_DATA, SQL_NULL_DATA, 0, or some positive value.</span></span> <span data-ttu-id="874b1-136">如果*cbUserData*為 SQL_VARLEN_DATA，則系統會使用長度指標（如果有的話）或結束字元序列來決定資料的長度。</span><span class="sxs-lookup"><span data-stu-id="874b1-136">If *cbUserData* is SQL_VARLEN_DATA, the system uses either the length indicator, if present, or a terminator sequence to determine the length of the data.</span></span> <span data-ttu-id="874b1-137">如果同時提供長度指標與結束字元順序，大量複製會使用導致複製最少量資料者。</span><span class="sxs-lookup"><span data-stu-id="874b1-137">If both a length indicator and a terminator sequence are supplied, bulk copy uses the one that results in the least amount of data being copied.</span></span> <span data-ttu-id="874b1-138">如果*cbUserData*為 SQL_VARLEN_DATA，則資料類型為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 字元或二進位類型，而且長度指標和結束字元順序都未指定，系統會傳回錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="874b1-138">If *cbUserData* is SQL_VARLEN_DATA, the data type is an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character or binary type, and neither a length indicator nor a terminator sequence is specified, the system returns an error message.</span></span>  
  
 <span data-ttu-id="874b1-139">如果 *cbUserData* 為 0 或正值，則系統會使用 *cbUserData* 當作最大的資料長度。</span><span class="sxs-lookup"><span data-stu-id="874b1-139">If *cbUserData* is 0 or a positive value, the system uses *cbUserData* as the maximum data length.</span></span> <span data-ttu-id="874b1-140">不過，如果除了正的 *cbUserData* 之外，也提供長度指標或結束字元順序，系統會使用導致複製最少量資料的方式決定資料長度。</span><span class="sxs-lookup"><span data-stu-id="874b1-140">However, if, in addition to a positive *cbUserData*, a length indicator or terminator sequence is provided, the system determines the data length by using the method that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="874b1-141">*cbUserData* 值表示資料的位元組計數。</span><span class="sxs-lookup"><span data-stu-id="874b1-141">The *cbUserData* value represents the count of bytes of data.</span></span> <span data-ttu-id="874b1-142">如果字元資料是以 Unicode 寬字元表示，則 *cbUserData* 正參數值表示字元數乘以每個字元的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="874b1-142">If character data is represented by Unicode wide characters, then a positive *cbUserData* parameter value represents the number of characters multiplied by the size, in bytes, of each character.</span></span>  
  
 <span data-ttu-id="874b1-143">*pUserDataTerm*</span><span class="sxs-lookup"><span data-stu-id="874b1-143">*pUserDataTerm*</span></span>  
 <span data-ttu-id="874b1-144">這是要用於此資料行的結束字元順序。</span><span class="sxs-lookup"><span data-stu-id="874b1-144">Is the terminator sequence to be used for this column.</span></span> <span data-ttu-id="874b1-145">此參數主要用於字元資料類型，因為其他所有類型都屬固定長度；如果是二進位資料，則需要一個長度指標，才能正確記錄出現的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="874b1-145">This parameter is useful mainly for character data types because all other types are of fixed length or, in the case of binary data, require an indicator of length to accurately record the number of bytes present.</span></span>  
  
 <span data-ttu-id="874b1-146">為避免結束已擷取的資料，或要指出使用者檔案中的資料未結束，將此參數設定為 NULL。</span><span class="sxs-lookup"><span data-stu-id="874b1-146">To avoid terminating extracted data, or to indicate that data in a user file is not terminated, set this parameter to NULL.</span></span>  
  
 <span data-ttu-id="874b1-147">如果使用多種指定使用者檔案資料行長度的方式 (例如結束字元和長度指標，或結束字元和資料行長度最大值)，大量複製會選擇導致複製最少量資料的方式。</span><span class="sxs-lookup"><span data-stu-id="874b1-147">If more than one means of specifying a user-file column length is used (such as a terminator and a length indicator, or a terminator and a maximum column length), bulk copy chooses the one that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="874b1-148">大量複製 API 會視需要執行 Unicode 到 MBCS 的字元轉換。</span><span class="sxs-lookup"><span data-stu-id="874b1-148">The bulk copy API performs Unicode-to-MBCS character conversion as required.</span></span> <span data-ttu-id="874b1-149">請務必確認結束字元位元組字串與位元組字串長度的設定正確。</span><span class="sxs-lookup"><span data-stu-id="874b1-149">Care must be taken to ensure that both the terminator byte string and the length of the byte string are set correctly.</span></span>  
  
 <span data-ttu-id="874b1-150">*cbUserDataTerm*</span><span class="sxs-lookup"><span data-stu-id="874b1-150">*cbUserDataTerm*</span></span>  
 <span data-ttu-id="874b1-151">這是要用於此資料行的結束字元順序長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="874b1-151">Is the length, in bytes, of the terminator sequence to be used for this column.</span></span> <span data-ttu-id="874b1-152">如果資料中沒有或不需要結束字元，將此值設定為 0。</span><span class="sxs-lookup"><span data-stu-id="874b1-152">If no terminator is present or desired in the data, set this value to 0.</span></span>  
  
 <span data-ttu-id="874b1-153">*idxServerCol*</span><span class="sxs-lookup"><span data-stu-id="874b1-153">*idxServerCol*</span></span>  
 <span data-ttu-id="874b1-154">這是資料行在資料庫資料表中的序數位置。</span><span class="sxs-lookup"><span data-stu-id="874b1-154">Is the ordinal position of the column in the database table.</span></span> <span data-ttu-id="874b1-155">第一個資料行編號為 1。</span><span class="sxs-lookup"><span data-stu-id="874b1-155">The first column number is 1.</span></span> <span data-ttu-id="874b1-156">資料行的序數位置是由[SQLColumns](../native-client-odbc-api/sqlcolumns.md)所報告。</span><span class="sxs-lookup"><span data-stu-id="874b1-156">The ordinal position of a column is reported by [SQLColumns](../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
 <span data-ttu-id="874b1-157">如果此值為 0，大量複製在資料檔案中會忽略資料行。</span><span class="sxs-lookup"><span data-stu-id="874b1-157">If this value is 0, bulk copy ignores the column in the data file.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="874b1-158">傳回</span><span class="sxs-lookup"><span data-stu-id="874b1-158">Returns</span></span>  
 <span data-ttu-id="874b1-159">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="874b1-159">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="874b1-160">備註</span><span class="sxs-lookup"><span data-stu-id="874b1-160">Remarks</span></span>  
 <span data-ttu-id="874b1-161">**Bcp_colfmt**函數可讓您指定大量複製的使用者檔案格式。</span><span class="sxs-lookup"><span data-stu-id="874b1-161">The **bcp_colfmt** function allows you to specify the user-file format for bulk copies.</span></span> <span data-ttu-id="874b1-162">針對大量複製，格式包含下列部分：</span><span class="sxs-lookup"><span data-stu-id="874b1-162">For bulk copy, a format contains the following parts:</span></span>  
  
-   <span data-ttu-id="874b1-163">從使用者檔案資料行對應至資料庫資料行。</span><span class="sxs-lookup"><span data-stu-id="874b1-163">A mapping from user-file columns to database columns.</span></span>  
  
-   <span data-ttu-id="874b1-164">每個使用者檔案資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="874b1-164">The data type of each user-file column.</span></span>  
  
-   <span data-ttu-id="874b1-165">每個資料行的選擇性指標長度。</span><span class="sxs-lookup"><span data-stu-id="874b1-165">The length of the optional indicator for each column.</span></span>  
  
-   <span data-ttu-id="874b1-166">每個使用者檔案資料行的資料最大長度。</span><span class="sxs-lookup"><span data-stu-id="874b1-166">The maximum length of data per user-file column.</span></span>  
  
-   <span data-ttu-id="874b1-167">每個資料行的選擇性結束位元組順序。</span><span class="sxs-lookup"><span data-stu-id="874b1-167">The optional terminating byte sequence for each column.</span></span>  
  
-   <span data-ttu-id="874b1-168">選擇性結束位元組順序的長度。</span><span class="sxs-lookup"><span data-stu-id="874b1-168">The length of the optional terminating byte sequence.</span></span>  
  
 <span data-ttu-id="874b1-169">**Bcp_colfmt**的每個呼叫都會指定一個使用者檔案資料行的格式。</span><span class="sxs-lookup"><span data-stu-id="874b1-169">Each call to **bcp_colfmt** specifies the format for one user-file column.</span></span> <span data-ttu-id="874b1-170">例如，若要在五個數據行的使用者資料檔案中變更三個數據行的預設設定，請先呼叫[bcp_columns](bcp-columns.md) \*\* (5) **，然後再呼叫**bcp_colfmt\*\*五次，其中三個呼叫會設定您的自訂格式。</span><span class="sxs-lookup"><span data-stu-id="874b1-170">For example, to change the default settings for three columns in a five-column user data file, first call [bcp_columns](bcp-columns.md)**(5)**, and then call **bcp_colfmt** five times, with three of those calls setting your custom format.</span></span> <span data-ttu-id="874b1-171">針對剩餘的兩個呼叫，請將*eUserDataType*設定為0，並分別將*cbIndicator*、 *cbUserData*和*cbUserDataTerm*設定為0、SQL_VARLEN_DATA 和0。</span><span class="sxs-lookup"><span data-stu-id="874b1-171">For the remaining two calls, set *eUserDataType* to 0, and set *cbIndicator*, *cbUserData*, and *cbUserDataTerm* to 0, SQL_VARLEN_DATA, and 0 respectively.</span></span> <span data-ttu-id="874b1-172">此程序會複製全部五個資料行，其中三個為您自訂的格式，而另兩個為預設格式。</span><span class="sxs-lookup"><span data-stu-id="874b1-172">This procedure copies all five columns, three with your customized format and two with the default format.</span></span>  
  
 <span data-ttu-id="874b1-173">若為*cbIndicator*，值為8表示大數數值型別現在有效。</span><span class="sxs-lookup"><span data-stu-id="874b1-173">For *cbIndicator*, a value of 8 to indicate a large value type is now valid.</span></span> <span data-ttu-id="874b1-174">如果有針對其對應資料行是新最大類型的欄位指定前置詞，則僅能將該前置詞設定為 8。</span><span class="sxs-lookup"><span data-stu-id="874b1-174">If the prefix is specified for a field whose corresponding column is a new max type, it can only be set to 8.</span></span> <span data-ttu-id="874b1-175">如需詳細資訊，請參閱[bcp_bind](bcp-bind.md)。</span><span class="sxs-lookup"><span data-stu-id="874b1-175">For details, see [bcp_bind](bcp-bind.md).</span></span>  
  
 <span data-ttu-id="874b1-176">呼叫**bcp_colfmt**之前，必須先呼叫**bcp_columns**函式。</span><span class="sxs-lookup"><span data-stu-id="874b1-176">The **bcp_columns** function must be called before any calls to **bcp_colfmt**.</span></span>  
  
 <span data-ttu-id="874b1-177">您必須針對使用者檔案中的每個資料行呼叫一次**bcp_colfmt** 。</span><span class="sxs-lookup"><span data-stu-id="874b1-177">You must call **bcp_colfmt** once for each column in the user file.</span></span>  
  
 <span data-ttu-id="874b1-178">針對任何使用者檔案資料行多次呼叫**bcp_colfmt**會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="874b1-178">Calling **bcp_colfmt** more than once for any user-file column causes an error.</span></span>  
  
 <span data-ttu-id="874b1-179">您不需要將使用者檔案中的所有資料複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="874b1-179">You do not need to copy all data in a user file to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="874b1-180">若要略過資料行，請將*並將 idxservercol*參數設定為0，以指定資料行的資料格式。</span><span class="sxs-lookup"><span data-stu-id="874b1-180">To skip a column, specify the format of the data for the column, setting the *idxServerCol* parameter to 0.</span></span> <span data-ttu-id="874b1-181">如果您要略過資料行，則必須指定其類型。</span><span class="sxs-lookup"><span data-stu-id="874b1-181">If you want to skip a column, you must specify its type.</span></span>  
  
 <span data-ttu-id="874b1-182">[Bcp_writefmt](bcp-writefmt.md)函數可以用來保存格式規格。</span><span class="sxs-lookup"><span data-stu-id="874b1-182">The [bcp_writefmt](bcp-writefmt.md) function can be used to persist the format specification.</span></span>  
  
## <a name="bcp_colfmt-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="874b1-183">bcp_colfmt 支援增強的日期和時間功能</span><span class="sxs-lookup"><span data-stu-id="874b1-183">bcp_colfmt Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="874b1-184">如需 aboutt 與日期/時間類型的*eUserDataType*參數搭配使用的資訊，請參閱[增強型日期和時間類型的大量複製變更 &#40;OLE DB 和 ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="874b1-184">For information aboutt he types used with the *eUserDataType* parameter for date/time types, see [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span>  
  
 <span data-ttu-id="874b1-185">如需詳細資訊，請參閱[ODBC&#41;&#40;的日期和時間改善](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="874b1-185">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="874b1-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="874b1-186">See Also</span></span>  
 [<span data-ttu-id="874b1-187">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="874b1-187">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
