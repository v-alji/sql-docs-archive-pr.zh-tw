---
title: bcp_bind |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_bind
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_bind function
ms.assetid: 6e335a5c-64b2-4bcf-a88f-35dc9393f329
author: rothja
ms.author: jroth
ms.openlocfilehash: db0a58398bf47bd0bb96bd1ef587d41890ed8461
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698167"
---
# <a name="bcp_bind"></a><span data-ttu-id="9328c-102">bcp_bind</span><span class="sxs-lookup"><span data-stu-id="9328c-102">bcp_bind</span></span>
  <span data-ttu-id="9328c-103">將程式變數中的資料繫結至資料表資料行，以便在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中進行大量複製。</span><span class="sxs-lookup"><span data-stu-id="9328c-103">Binds data from a program variable to a table column for bulk copy into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9328c-104">語法</span><span class="sxs-lookup"><span data-stu-id="9328c-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_bind (  
HDBC   
hdbc  
,   
LPCBYTE   
pData  
,  
INT   
cbIndicator  
,  
DBINT   
cbData  
,  
LPCBYTE   
pTerm  
,  
INT   
cbTerm  
,  
INT   
eDataType  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="9328c-105">引數</span><span class="sxs-lookup"><span data-stu-id="9328c-105">Arguments</span></span>  
 <span data-ttu-id="9328c-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="9328c-106">*hdbc*</span></span>  
 <span data-ttu-id="9328c-107">這是已啟用大量複製的 ODBC 連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="9328c-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="9328c-108">*pData*</span><span class="sxs-lookup"><span data-stu-id="9328c-108">*pData*</span></span>  
 <span data-ttu-id="9328c-109">這是已複製之資料的指標。</span><span class="sxs-lookup"><span data-stu-id="9328c-109">Is a pointer to the data copied.</span></span> <span data-ttu-id="9328c-110">如果*eDataType*為 SQLTEXT、SQLNTEXT、SQLXML、SQLUDT、SQLCHARACTER、SQLVARCHAR、SQLVARBINARY、SQLBINARY、SQLNCHAR 或 SQLIMAGE，則*PDATA*可以是 Null。</span><span class="sxs-lookup"><span data-stu-id="9328c-110">If *eDataType* is SQLTEXT, SQLNTEXT, SQLXML, SQLUDT, SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, SQLNCHAR or SQLIMAGE, *pData* can be NULL.</span></span> <span data-ttu-id="9328c-111">Null *pData*表示 long 資料值將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用[bcp_moretext](bcp-moretext.md)以區區塊轉送至。</span><span class="sxs-lookup"><span data-stu-id="9328c-111">A NULL *pData* indicates that long data values will be sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in chunks using [bcp_moretext](bcp-moretext.md).</span></span> <span data-ttu-id="9328c-112">只有當對應到使用者系結欄位的資料行是 BLOB 資料行時，使用者才應該將*pData*設定為 Null，否則**bcp_bind**將會失敗。</span><span class="sxs-lookup"><span data-stu-id="9328c-112">The user should only set *pData* to NULL if the column corresponding to the user bound field is a BLOB column otherwise **bcp_bind** will fail.</span></span>  
  
 <span data-ttu-id="9328c-113">如果這些指標出現在資料中，它們會直接出現在資料前的記憶體中。</span><span class="sxs-lookup"><span data-stu-id="9328c-113">If indicators are present in the data, they appear in memory directly before the data.</span></span> <span data-ttu-id="9328c-114">在此情況下， *pData*參數會指向指標變數，而大量複製會使用指標的寬度（ *cbIndicator*參數）來正確處理使用者資料。</span><span class="sxs-lookup"><span data-stu-id="9328c-114">The *pData* parameter points to the indicator variable in this case, and the width of the indicator, the *cbIndicator* parameter, is used by bulk copy to address user data correctly.</span></span>  
  
 <span data-ttu-id="9328c-115">*cbIndicator*</span><span class="sxs-lookup"><span data-stu-id="9328c-115">*cbIndicator*</span></span>  
 <span data-ttu-id="9328c-116">這是資料行的資料內，長度或 Null 指標的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="9328c-116">Is the length, in bytes, of a length or null indicator for the column's data.</span></span> <span data-ttu-id="9328c-117">有效的指標長度值為 0 (不使用指標時)、1、2、4 或 8。</span><span class="sxs-lookup"><span data-stu-id="9328c-117">Valid indicator length values are 0 (when using no indicator), 1, 2, 4, or 8.</span></span> <span data-ttu-id="9328c-118">指標會直接出現在任何資料前的記憶體中。</span><span class="sxs-lookup"><span data-stu-id="9328c-118">Indicators appear in memory directly before any data.</span></span> <span data-ttu-id="9328c-119">例如，下列結構類型定義可用於使用大量複製，將整數值插入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表：</span><span class="sxs-lookup"><span data-stu-id="9328c-119">For example, the following structure type definition could be used to insert integer values into an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table using bulk copy:</span></span>  
  
```  
typedef struct tagBCPBOUNDINT  
    {  
    int iIndicator;  
    int Value;  
    } BCPBOUNDINT;  
```  
  
 <span data-ttu-id="9328c-120">在範例案例中， *pData*參數會設定為結構的已宣告實例位址，也就是 BCPBOUNDINT *iIndicator*結構成員的位址。</span><span class="sxs-lookup"><span data-stu-id="9328c-120">In the example case, the *pData* parameter would be set to the address of a declared instance of the structure, the address of the BCPBOUNDINT *iIndicator* structure member.</span></span> <span data-ttu-id="9328c-121">*CbIndicator*參數會設定為 (sizeof (int) # A3 的整數大小，而*cbData*參數會再次設定為整數 (sizeof (int) # A7 的大小。</span><span class="sxs-lookup"><span data-stu-id="9328c-121">The *cbIndicator* parameter would be set to the size of an integer (sizeof(int)), and the *cbData* parameter would again be set to the size of an integer (sizeof(int)).</span></span> <span data-ttu-id="9328c-122">若要將資料列大量複製到包含系結資料行之 Null 值的伺服器，實例的*iIndicator*成員值應該設定為 SQL_Null_DATA。</span><span class="sxs-lookup"><span data-stu-id="9328c-122">To bulk copy a row to the server containing a NULL value for the bound column, the value of the instance's *iIndicator* member should be set to SQL_NULL_DATA.</span></span>  
  
 <span data-ttu-id="9328c-123">*cbData*</span><span class="sxs-lookup"><span data-stu-id="9328c-123">*cbData*</span></span>  
 <span data-ttu-id="9328c-124">這是資料在程式變數中的位元組計數，不包括任何長度或 Null 指標或結束字元的長度。</span><span class="sxs-lookup"><span data-stu-id="9328c-124">Is the count of bytes of data in the program variable, not including the length of any length or null indicator or terminator.</span></span>  
  
 <span data-ttu-id="9328c-125">將*cbData*設定為 SQL_Null_DATA 表示複製到伺服器的所有資料列都包含資料行的 Null 值。</span><span class="sxs-lookup"><span data-stu-id="9328c-125">Setting *cbData* to SQL_NULL_DATA signifies that all rows copied to the server contain a NULL value for the column.</span></span>  
  
 <span data-ttu-id="9328c-126">將*cbData*設定為 SQL_VARLEN_DATA 表示系統會使用字串結束字元或其他方法來判斷複製的資料長度。</span><span class="sxs-lookup"><span data-stu-id="9328c-126">Setting *cbData* to SQL_VARLEN_DATA indicates that the system will use a string terminator, or other method, to determine the length of data copied.</span></span>  
  
 <span data-ttu-id="9328c-127">對於整數之類的固定長度資料類型，此資料類型會指出系統之資料的長度。</span><span class="sxs-lookup"><span data-stu-id="9328c-127">For fixed-length data types, such as integers, the data type indicates the length of the data to the system.</span></span> <span data-ttu-id="9328c-128">因此，如果是固定長度的資料類型， *cbData*可以安全地 SQL_VARLEN_DATA 或資料的長度。</span><span class="sxs-lookup"><span data-stu-id="9328c-128">Therefore, for fixed-length data types, *cbData* can safely be SQL_VARLEN_DATA or the length of the data.</span></span>  
  
 <span data-ttu-id="9328c-129">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是字元和二進位資料類型， *cbData*可以是 SQL_VARLEN_DATA、SQL_Null_DATA、某個正值或0。</span><span class="sxs-lookup"><span data-stu-id="9328c-129">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character and binary data types, *cbData* can be SQL_VARLEN_DATA, SQL_NULL_DATA, some positive value, or 0.</span></span> <span data-ttu-id="9328c-130">如果 SQL_VARLEN_DATA *cbData* ，系統會使用長度/null 指標 (（如果有的話）) 或結束字元序列來決定資料的長度。</span><span class="sxs-lookup"><span data-stu-id="9328c-130">If *cbData* is SQL_VARLEN_DATA, the system uses either a length/null indicator (if present) or a terminator sequence to determine the length of the data.</span></span> <span data-ttu-id="9328c-131">如果同時提供兩者，系統會使用導致複製最少量資料者。</span><span class="sxs-lookup"><span data-stu-id="9328c-131">If both are supplied, the system uses the one that results in the least amount of data being copied.</span></span> <span data-ttu-id="9328c-132">如果*cbData*為 SQL_VARLEN_DATA，則資料行的資料類型為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 字元或二進位類型，而且長度指標和結束字元順序都未指定，系統會傳回錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="9328c-132">If *cbData* is SQL_VARLEN_DATA, the data type of the column is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character or binary type, and neither a length indicator nor a terminator sequence is specified, the system returns an error message.</span></span>  
  
 <span data-ttu-id="9328c-133">如果*cbData*為0或正值，則系統會使用*cbData*做為資料長度。</span><span class="sxs-lookup"><span data-stu-id="9328c-133">If *cbData* is 0 or a positive value, the system uses *cbData* as the data length.</span></span> <span data-ttu-id="9328c-134">不過，如果除了正的*cbData*值之外，也提供長度指標或結束字元序列，系統會使用導致複製最少量資料的方法來決定資料長度。</span><span class="sxs-lookup"><span data-stu-id="9328c-134">However, if, in addition to a positive *cbData* value, a length indicator or terminator sequence is provided, the system determines the data length by using the method that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="9328c-135">*CbData*參數值表示資料的位元組計數。</span><span class="sxs-lookup"><span data-stu-id="9328c-135">The *cbData* parameter value represents the count of bytes of data.</span></span> <span data-ttu-id="9328c-136">如果字元資料是以 Unicode 寬字元表示，則正*cbData*參數值代表字元數乘以每個字元的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="9328c-136">If character data is represented by Unicode wide characters, then a positive *cbData* parameter value represents the number of characters multiplied by the size in bytes of each character.</span></span>  
  
 <span data-ttu-id="9328c-137">*pTerm*</span><span class="sxs-lookup"><span data-stu-id="9328c-137">*pTerm*</span></span>  
 <span data-ttu-id="9328c-138">這是位元組模式的指標 (如果有的話)，可標示此程式變數的結尾。</span><span class="sxs-lookup"><span data-stu-id="9328c-138">Is a pointer to the byte pattern, if any, that marks the end of this program variable.</span></span> <span data-ttu-id="9328c-139">例如，ANSI 和 MBCS C 字串通常有 1 個位元組的結束字元 (\0)。</span><span class="sxs-lookup"><span data-stu-id="9328c-139">For example, ANSI and MBCS C strings usually have a 1-byte terminator (\0).</span></span>  
  
 <span data-ttu-id="9328c-140">如果變數沒有結束字元，請將*pTerm*設定為 Null。</span><span class="sxs-lookup"><span data-stu-id="9328c-140">If there is no terminator for the variable, set *pTerm* to NULL.</span></span>  
  
 <span data-ttu-id="9328c-141">您可以使用任何空字串 ("") 來指定 C Null 結束字元，做為程式變數的結束字元。</span><span class="sxs-lookup"><span data-stu-id="9328c-141">You can use an empty string ("") to designate the C null terminator as the program-variable terminator.</span></span> <span data-ttu-id="9328c-142">因為以 null 結束的空字串構成單一位元組 (結束字元位元組本身) ，請將*cbTerm*設定為1。</span><span class="sxs-lookup"><span data-stu-id="9328c-142">Because the null-terminated empty string constitutes a single byte (the terminator byte itself), set *cbTerm* to 1.</span></span> <span data-ttu-id="9328c-143">例如，表示*szName*中的字串是以 null 終止，而且應該使用結束字元來表示長度：</span><span class="sxs-lookup"><span data-stu-id="9328c-143">For example, to indicate that the string in *szName* is null-terminated and that the terminator should be used to indicate the length:</span></span>  
  
```  
bcp_bind(hdbc, szName, 0,  
   SQL_VARLEN_DATA, "", 1,  
   SQLCHARACTER, 2)  
```  
  
 <span data-ttu-id="9328c-144">這個範例的 nonterminated 表單可能表示從*szName*變數複製15個字元到系結資料表的第二個數據行：</span><span class="sxs-lookup"><span data-stu-id="9328c-144">A nonterminated form of this example could indicate that 15 characters be copied from the *szName* variable to the second column of the bound table:</span></span>  
  
```  
bcp_bind(hdbc, szName, 0, 15,   
   NULL, 0, SQLCHARACTER, 2)  
```  
  
 <span data-ttu-id="9328c-145">大量複製 API 會視需要執行 Unicode 到 MBCS 的字元轉換。</span><span class="sxs-lookup"><span data-stu-id="9328c-145">The bulk copy API performs Unicode-to-MBCS character conversion as required.</span></span> <span data-ttu-id="9328c-146">請確認結束字元位元組字串與位元組字串長度的設定正確。</span><span class="sxs-lookup"><span data-stu-id="9328c-146">Make sure that both the terminator byte string and the length of the byte string are set correctly.</span></span> <span data-ttu-id="9328c-147">例如，若要指出*szName*中的字串是 unicode 寬字元字串，請以 unicode null 結束字元值結束：</span><span class="sxs-lookup"><span data-stu-id="9328c-147">For example, to indicate that the string in *szName* is a Unicode wide character string, terminated by the Unicode null terminator value:</span></span>  
  
```  
bcp_bind(hdbc, szName, 0,   
   SQL_VARLEN_DATA, L"",  
   sizeof(WCHAR), SQLNCHAR, 2)  
```  
  
 <span data-ttu-id="9328c-148">如果系結的資料 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 行是寬字元，則不會在[bcp_sendrow](bcp-sendrow.md)上執行任何轉換。</span><span class="sxs-lookup"><span data-stu-id="9328c-148">If the bound [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] column is wide character, no conversion is performed on [bcp_sendrow](bcp-sendrow.md).</span></span> <span data-ttu-id="9328c-149">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料行為 MBCS 字元類型，當資料傳送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，會執行寬字元到多位元組字元的轉換。</span><span class="sxs-lookup"><span data-stu-id="9328c-149">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] column is an MBCS character type, wide character to multibyte character conversion is performed as the data is sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9328c-150">*cbTerm*</span><span class="sxs-lookup"><span data-stu-id="9328c-150">*cbTerm*</span></span>  
 <span data-ttu-id="9328c-151">這是出現在程式變數之結束字元中的位元組計數 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="9328c-151">Is the count of bytes present in the terminator for the program variable, if any.</span></span> <span data-ttu-id="9328c-152">如果變數沒有結束字元，請將*cbTerm*設定為0。</span><span class="sxs-lookup"><span data-stu-id="9328c-152">If there is no terminator for the variable, set *cbTerm* to 0.</span></span>  
  
 <span data-ttu-id="9328c-153">*eDataType*</span><span class="sxs-lookup"><span data-stu-id="9328c-153">*eDataType*</span></span>  
 <span data-ttu-id="9328c-154">這是程式變數的 C 資料類型。</span><span class="sxs-lookup"><span data-stu-id="9328c-154">Is the C data type of the program variable.</span></span> <span data-ttu-id="9328c-155">程式變數中的資料會轉換為資料庫資料行的類型。</span><span class="sxs-lookup"><span data-stu-id="9328c-155">The data in the program variable is converted to the type of the database column.</span></span> <span data-ttu-id="9328c-156">如果此參數為 0，則不會執行任何轉換。</span><span class="sxs-lookup"><span data-stu-id="9328c-156">If this parameter is 0, no conversion is performed.</span></span>  
  
 <span data-ttu-id="9328c-157">*EDataType*參數是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sqlncli 中的資料類型標記所列舉，而不是 ODBC C 資料類型枚舉器。</span><span class="sxs-lookup"><span data-stu-id="9328c-157">The *eDataType* parameter is enumerated by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type tokens in sqlncli.h, not the ODBC C data type enumerators.</span></span> <span data-ttu-id="9328c-158">例如，您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 專屬類型 SQLINT2 來指定兩個位元組的整數 ODBC 類型 SQL_C_SHORT。</span><span class="sxs-lookup"><span data-stu-id="9328c-158">For example, you can specify a two-byte integer, ODBC type SQL_C_SHORT, using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific type SQLINT2.</span></span>  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<span data-ttu-id="9328c-159">在參數中引進了 SQLXML 和 SQLUDT 資料類型標記的支援 *`eDataType`* 。</span><span class="sxs-lookup"><span data-stu-id="9328c-159">introduced support for SQLXML and SQLUDT data type tokens in the *`eDataType`* paramenter.</span></span>  
  
 <span data-ttu-id="9328c-160">*idxServerCol*</span><span class="sxs-lookup"><span data-stu-id="9328c-160">*idxServerCol*</span></span>  
 <span data-ttu-id="9328c-161">這是資料庫資料表中要將資料複製到其中之資料行的序數位置。</span><span class="sxs-lookup"><span data-stu-id="9328c-161">Is the ordinal position of the column in the database table to which the data is copied.</span></span> <span data-ttu-id="9328c-162">資料表中的第一個資料行是資料行 1。</span><span class="sxs-lookup"><span data-stu-id="9328c-162">The first column in a table is column 1.</span></span> <span data-ttu-id="9328c-163">資料行的序數位置是由[SQLColumns](../native-client-odbc-api/sqlcolumns.md)所報告。</span><span class="sxs-lookup"><span data-stu-id="9328c-163">The ordinal position of a column is reported by [SQLColumns](../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
## <a name="returns"></a><span data-ttu-id="9328c-164">傳回</span><span class="sxs-lookup"><span data-stu-id="9328c-164">Returns</span></span>  
 <span data-ttu-id="9328c-165">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="9328c-165">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9328c-166">備註</span><span class="sxs-lookup"><span data-stu-id="9328c-166">Remarks</span></span>  
 <span data-ttu-id="9328c-167">使用**bcp_bind** ，以快速且有效率的方式，將程式變數中的資料複製到中的資料表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9328c-167">Use **bcp_bind** for a fast, efficient way to copy data from a program variable into a table in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9328c-168">呼叫此或任何其他大量複製函數之前，請先呼叫[bcp_init](bcp-init.md) 。</span><span class="sxs-lookup"><span data-stu-id="9328c-168">Call [bcp_init](bcp-init.md) before calling this or any other bulk-copy function.</span></span> <span data-ttu-id="9328c-169">呼叫**bcp_init**會設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用於大量複製的目標資料表。</span><span class="sxs-lookup"><span data-stu-id="9328c-169">Calling **bcp_init** sets the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] target table for bulk copy.</span></span> <span data-ttu-id="9328c-170">呼叫**bcp_init**以與**bcp_bind**和[bcp_sendrow](bcp-sendrow.md)搭配使用時，表示資料檔的**bcp_init** _szDataFile_參數會設定為 Null;**bcp_init**_eDirection_參數設為 DB_IN。</span><span class="sxs-lookup"><span data-stu-id="9328c-170">When calling **bcp_init** for use with **bcp_bind** and [bcp_sendrow](bcp-sendrow.md), the **bcp_init** _szDataFile_ parameter, indicating the data file, is set to NULL; the **bcp_init**_eDirection_ parameter is set to DB_IN.</span></span>  
  
 <span data-ttu-id="9328c-171">針對您要複製的資料表中的每個資料行，建立個別的**bcp_bind**呼叫 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9328c-171">Make a separate **bcp_bind** call for every column in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table into which you want to copy.</span></span> <span data-ttu-id="9328c-172">完成必要的**bcp_bind**呼叫之後，請呼叫**bcp_sendrow** ，將您的程式變數中的資料列傳送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9328c-172">After the necessary **bcp_bind** calls have been made, then call **bcp_sendrow** to send a row of data from your program variables to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9328c-173">不支援重新繫結資料行。</span><span class="sxs-lookup"><span data-stu-id="9328c-173">Rebinding a column is not supported.</span></span>  
  
 <span data-ttu-id="9328c-174">每當您想 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 要認可已收到的資料列時，請呼叫[bcp_batch](bcp-batch.md)。</span><span class="sxs-lookup"><span data-stu-id="9328c-174">Whenever you want [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to commit the rows already received, call [bcp_batch](bcp-batch.md).</span></span> <span data-ttu-id="9328c-175">例如，針對每1000個插入的資料列，或在任何其他間隔呼叫一次**bcp_batch** 。</span><span class="sxs-lookup"><span data-stu-id="9328c-175">For example, call **bcp_batch** once for every 1000 rows inserted or at any other interval.</span></span>  
  
 <span data-ttu-id="9328c-176">當沒有要插入的資料列時，請呼叫[bcp_done](bcp-done.md)。</span><span class="sxs-lookup"><span data-stu-id="9328c-176">When there are no more rows to be inserted, call [bcp_done](bcp-done.md).</span></span> <span data-ttu-id="9328c-177">無法執行這項操作時，會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="9328c-177">Failure to do so results in an error.</span></span>  
  
 <span data-ttu-id="9328c-178">以[bcp_control](bcp-control.md)指定的控制項參數設定不會影響**bcp_bind**資料列傳輸。</span><span class="sxs-lookup"><span data-stu-id="9328c-178">Control parameter settings, specified with [bcp_control](bcp-control.md), have no effect on **bcp_bind** row transfers.</span></span>  
  
 <span data-ttu-id="9328c-179">如果資料行的*pData*是設為 Null，因為[bcp_moretext](bcp-moretext.md)的呼叫將會提供它的值，而*EDATATYPE*設定為 SQLTEXT、SQLNTEXT、SQLXML、SQLUDT、SQLCHARACTER、SQLVARCHAR、SQLVARBINARY、SQLBINARY、SQLNCHAR 或 SQLIMAGE 的任何後續資料行，也必須與設定為 Null 的*pData*系結，而且其值也必須透過呼叫來提供 `bcp_moretext` 。</span><span class="sxs-lookup"><span data-stu-id="9328c-179">If *pData* for a column is set to NULL because its value will be supplied by calls to [bcp_moretext](bcp-moretext.md), any subsequent columns with *eDataType* set to SQLTEXT, SQLNTEXT, SQLXML, SQLUDT, SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, SQLNCHAR, or SQLIMAGE must also be bound with *pData* set to NULL, and their values must also be supplied by calls to `bcp_moretext`.</span></span>  
  
 <span data-ttu-id="9328c-180">對於新的大數數值型別，例如 `varchar(max)` 、 `varbinary(max)` 或 `nvarchar(max)` ，您可以使用 SQLCHARACTER、SQLVARCHAR、SQLVARBINARY、SQLBINARY 和 SQLNCHAR 作為*eDataType*參數中的類型指標。</span><span class="sxs-lookup"><span data-stu-id="9328c-180">For new large value types, such as `varchar(max)`, `varbinary(max)`, or `nvarchar(max)`, you can use SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, and SQLNCHAR as type indicators in the *eDataType* parameter.</span></span>  
  
 <span data-ttu-id="9328c-181">如果*cbTerm*不是0，則任何 (1、2、4或 8) 的值，對於前置詞 (*cbIndicator*) 都是有效的。</span><span class="sxs-lookup"><span data-stu-id="9328c-181">If *cbTerm* is not 0, any value (1, 2, 4, or 8) is valid for the prefix (*cbIndicator*).</span></span> <span data-ttu-id="9328c-182">在這種情況下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 將會搜尋結束字元、計算結束字元)  (的資料長度， *i*並將*cbData*設定為較小的 i 值和前置詞的值。</span><span class="sxs-lookup"><span data-stu-id="9328c-182">In this situation, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client will search for the terminator, calculate data length with respect to the terminator (*i*), and set the *cbData* to the smaller value of i and the value of prefix.</span></span>  
  
 <span data-ttu-id="9328c-183">如果*cbTerm*為0，而*cbIndicator* (前置詞) 不是0，則*cbIndicator*必須是8。</span><span class="sxs-lookup"><span data-stu-id="9328c-183">If *cbTerm* is 0 and *cbIndicator* (the prefix) is not 0, *cbIndicator* must be 8.</span></span> <span data-ttu-id="9328c-184">8 位元組前置詞可以採用下列值：</span><span class="sxs-lookup"><span data-stu-id="9328c-184">The 8 byte prefix can take the following values:</span></span>  
  
-   <span data-ttu-id="9328c-185">0xFFFFFFFFFFFFFFFF 表示欄位的 Null 值</span><span class="sxs-lookup"><span data-stu-id="9328c-185">0xFFFFFFFFFFFFFFFF means a null value for the field</span></span>  
  
-   <span data-ttu-id="9328c-186">0xFFFFFFFFFFFFFFFE 會視為特殊的前置詞值，用於將區塊中的資料有效傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="9328c-186">0xFFFFFFFFFFFFFFFE is treated as a special prefix value which is used for efficiently sending data in chunks to the server.</span></span> <span data-ttu-id="9328c-187">包含此特殊前置詞之資料的格式為：</span><span class="sxs-lookup"><span data-stu-id="9328c-187">The format of data with this special prefix is:</span></span>  
  
-   <span data-ttu-id="9328c-188"><SPECIAL_PREFIX> \<0 or more  DATA CHUNKS> <ZERO_CHUNK> 位置：</span><span class="sxs-lookup"><span data-stu-id="9328c-188"><SPECIAL_PREFIX> \<0 or more  DATA CHUNKS> <ZERO_CHUNK> where:</span></span>  
  
-   <span data-ttu-id="9328c-189">SPECIAL_PREFIX 是 0xFFFFFFFFFFFFFFFE</span><span class="sxs-lookup"><span data-stu-id="9328c-189">SPECIAL_PREFIX is 0xFFFFFFFFFFFFFFFE</span></span>  
  
-   <span data-ttu-id="9328c-190">DATA_CHUNK 是包含區塊長度的 4 位元組前置詞，後面接著以 4 位元組前置詞指定其長度的實際資料。</span><span class="sxs-lookup"><span data-stu-id="9328c-190">DATA_CHUNK is a 4 byte prefix containing length of the chunk,followed by the actual data whose length is specified in the 4 byte prefix.</span></span>  
  
-   <span data-ttu-id="9328c-191">ZERO_CHUNK 是包含全部零 (00000000) 的 4 位元組值，表示資料的結尾。</span><span class="sxs-lookup"><span data-stu-id="9328c-191">ZERO_CHUNK is a 4 byte value containing all zeros (00000000) indicating the end of data.</span></span>  
  
-   <span data-ttu-id="9328c-192">其他任何有效的 8 位元組長度會視為一般資料長度。</span><span class="sxs-lookup"><span data-stu-id="9328c-192">Any other valid 8 byte length is treated as a regular data length.</span></span>  
  
 <span data-ttu-id="9328c-193">使用**bcp_bind**呼叫[bcp_columns](bcp-columns.md)會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="9328c-193">Calling [bcp_columns](bcp-columns.md) when using **bcp_bind** results in an error.</span></span>  
  
## <a name="bcp_bind-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="9328c-194">bcp_bind 支援增強的日期和時間功能</span><span class="sxs-lookup"><span data-stu-id="9328c-194">bcp_bind Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="9328c-195">如需有關與日期/時間類型的*eDataType*參數搭配使用之類型的詳細資訊，請參閱[增強型日期和時間類型的大量複製變更 &#40;OLE DB 和 ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="9328c-195">For information about the types used with the *eDataType* parameter for date/time types, see [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span>  
  
 <span data-ttu-id="9328c-196">如需詳細資訊，請參閱[ODBC&#41;&#40;的日期和時間改善](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="9328c-196">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9328c-197">範例</span><span class="sxs-lookup"><span data-stu-id="9328c-197">Example</span></span>  
  
```  
#include sql.h  
#include sqlext.h  
#include odbcss.h  
// Variables like henv not specified.  
HDBC      hdbc;  
char         szCompanyName[MAXNAME];  
DBINT      idCompany;  
DBINT      nRowsProcessed;  
DBBOOL      bMoreData;  
char*      pTerm = "\t\t";  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source; return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bcp.   
if (bcp_init(hdbc, "comdb..accounts_info", NULL, NULL  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idCompany, 0, sizeof(DBINT), NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_bind(hdbc, (LPCBYTE) szCompanyName, 0, SQL_VARLEN_DATA,  
   (LPCBYTE) pTerm, strnlen(pTerm, sizeof(pTerm)), SQLCHARACTER, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
while (TRUE)  
   {  
   // Retrieve and process program data.   
   if ((bMoreData = getdata(&idCompany, szCompanyName)) == TRUE)  
      {  
      // Send the data.   
      if (bcp_sendrow(hdbc) == FAIL)  
         {  
         // Raise error and return.  
         return;  
         }  
      }  
   else  
      {  
      // Break out of loop.  
      break;  
      }  
   }  
  
// Terminate the bulk copy operation.  
if ((nRowsProcessed = bcp_done(hdbc)) == -1)  
   {  
   printf_s("Bulk-copy unsuccessful.\n");  
   return;  
   }  
  
printf_s("%ld rows copied.\n", nRowsProcessed);  
```  
  
## <a name="see-also"></a><span data-ttu-id="9328c-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9328c-198">See Also</span></span>  
 [<span data-ttu-id="9328c-199">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="9328c-199">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
