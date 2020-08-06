---
title: IBCPSession::BCPColFmt (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPColFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPColFmt method
ms.assetid: 2852f4ba-f1c6-4c4c-86b2-b77e4abe70de
author: rothja
ms.author: jroth
ms.openlocfilehash: d60fa5dc93473f477926719cdcc05d13e72d8fd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707462"
---
# <a name="ibcpsessionbcpcolfmt-ole-db"></a><span data-ttu-id="94494-102">IBCPSession::BCPColFmt (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="94494-102">IBCPSession::BCPColFmt (OLE DB)</span></span>
  <span data-ttu-id="94494-103">在程式變數與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料行之間建立繫結。</span><span class="sxs-lookup"><span data-stu-id="94494-103">Creates a binding between program variables and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94494-104">語法</span><span class="sxs-lookup"><span data-stu-id="94494-104">Syntax</span></span>  
  
```  
  
HRESULT BCPColFmt(   
DBORDINALidxUserDataCol,  
inteUserDataType,  
intcbIndicator,  
intcbUserData,  
BYTE *pbUserDataTerm,  
intcbUserDataTerm,  
DBORDINALidxServerCol);  
```  
  
## <a name="remarks"></a><span data-ttu-id="94494-105">備註</span><span class="sxs-lookup"><span data-stu-id="94494-105">Remarks</span></span>  
 <span data-ttu-id="94494-106">**BCPColFmt** 方法是用來建立 BCP 資料檔欄位與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料行之間的繫結。</span><span class="sxs-lookup"><span data-stu-id="94494-106">The **BCPColFmt** method is used to create a binding between BCP data file fields and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columns.</span></span> <span data-ttu-id="94494-107">它會使用資料行的長度、類型、結束字元和前置長度當做參數，並為個別欄位設定每一個屬性。</span><span class="sxs-lookup"><span data-stu-id="94494-107">It takes in the length, type, terminator, and prefix length of a column as parameters and sets each of these properties for individual fields.</span></span>  
  
 <span data-ttu-id="94494-108">如果使用者選擇互動模式，就會呼叫這個方法兩次；一次是根據預設值設定資料行格式 (預設值是根據伺服器資料行的類型)，另一次是根據互動模式期間選擇之用戶端的資料行類型，針對每一個資料行設定格式。</span><span class="sxs-lookup"><span data-stu-id="94494-108">If the user chooses interactive mode, this method is called twice; once to set the column format according to the default values (which are according to the type of the server column), and once to set the format according to the column type of the choice of the client chosen during interactive mode, for each column.</span></span>  
  
 <span data-ttu-id="94494-109">在非互動模式中，每一個資料行只會呼叫這個方法一次，以便將每一個資料行的類型設定為字元或原生類型，或是設定資料行和資料列結束字元。</span><span class="sxs-lookup"><span data-stu-id="94494-109">In non-interactive modes, it is called only once per column to set the type of each column to character or native type, and to set the column and row terminators.</span></span>  
  
 <span data-ttu-id="94494-110">**BCPColFmt** 方法可讓您指定大量複製的使用者檔案格式。</span><span class="sxs-lookup"><span data-stu-id="94494-110">The **BCPColFmt** method allows you to specify the user-file format for bulk copies.</span></span> <span data-ttu-id="94494-111">針對大量複製，格式包含下列部分：</span><span class="sxs-lookup"><span data-stu-id="94494-111">For bulk copy, a format contains the following parts:</span></span>  
  
-   <span data-ttu-id="94494-112">從使用者檔案欄位對應至資料庫資料行。</span><span class="sxs-lookup"><span data-stu-id="94494-112">A mapping from user-file fields to database columns.</span></span>  
  
-   <span data-ttu-id="94494-113">每個使用者檔案欄位的資料類型。</span><span class="sxs-lookup"><span data-stu-id="94494-113">The data type of each user-file field.</span></span>  
  
-   <span data-ttu-id="94494-114">每個欄位的選擇性指標長度。</span><span class="sxs-lookup"><span data-stu-id="94494-114">The length of the optional indicator for each field.</span></span>  
  
-   <span data-ttu-id="94494-115">每個使用者檔案欄位的資料最大長度。</span><span class="sxs-lookup"><span data-stu-id="94494-115">The maximum length of data per user-file field.</span></span>  
  
-   <span data-ttu-id="94494-116">每個欄位的選擇性結束位元組順序。</span><span class="sxs-lookup"><span data-stu-id="94494-116">The optional terminating byte sequence for each field.</span></span>  
  
-   <span data-ttu-id="94494-117">選擇性結束位元組順序的長度。</span><span class="sxs-lookup"><span data-stu-id="94494-117">The length of the optional terminating byte sequence.</span></span>  
  
 <span data-ttu-id="94494-118">**BCPColFmt** 的每個呼叫都會針對一個使用者檔案欄位指定格式。</span><span class="sxs-lookup"><span data-stu-id="94494-118">Each call to **BCPColFmt** specifies the format for one user-file field.</span></span> <span data-ttu-id="94494-119">例如，若要在五個欄位的使用者資料檔案中變更三個欄位的預設值，請先呼叫 `BCPColumns(5)`，然後呼叫 **BCPColFmt** 五次，其中三次呼叫會設定您的自訂格式。</span><span class="sxs-lookup"><span data-stu-id="94494-119">For example, to change the default settings for three fields in a five-field user data file, first call `BCPColumns(5)`, and then call **BCPColFmt** five times, with three of those calls setting your custom format.</span></span> <span data-ttu-id="94494-120">在其餘兩個呼叫中，將 *eUserDataType* 設定為 BCP_TYPE_DEFAULT，並將 *cbIndicator*、*cbUserData* 和 *cbUserDataTerm* 分別設定為 0、BCP_VARIABLE_LENGTH 和 0。</span><span class="sxs-lookup"><span data-stu-id="94494-120">For the remaining two calls, set *eUserDataType* to BCP_TYPE_DEFAULT, and set *cbIndicator*, *cbUserData*, and *cbUserDataTerm* to 0, BCP_VARIABLE_LENGTH, and 0 respectively.</span></span> <span data-ttu-id="94494-121">此程序會複製全部五個資料行，其中三個為您自訂的格式，而另兩個為預設格式。</span><span class="sxs-lookup"><span data-stu-id="94494-121">This procedure copies all five columns, three with your customized format and two with the default format.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="94494-122">必須先呼叫 [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) 方法，才能進行 **BCPColFmt** 的任何呼叫。</span><span class="sxs-lookup"><span data-stu-id="94494-122">The [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) method must be called before any calls to **BCPColFmt**.</span></span> <span data-ttu-id="94494-123">您必須在使用者檔案中，針對每個資料行呼叫 **BCPColFmt** 一次。</span><span class="sxs-lookup"><span data-stu-id="94494-123">You must call **BCPColFmt** once for each column in the user file.</span></span> <span data-ttu-id="94494-124">針對任何使用者檔案資料行多次呼叫 **BCPColFmt** 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="94494-124">Calling **BCPColFmt** more than once for any user-file column causes an error.</span></span>  
  
 <span data-ttu-id="94494-125">您不必將使用者檔案中的所有資料複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="94494-125">You do not have to copy all of the data in a user file to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="94494-126">若要略過資料行，請指定資料行的資料格式，並將 idxServerCol 參數設定為 0。</span><span class="sxs-lookup"><span data-stu-id="94494-126">To skip a column, specify the format of the data for the column setting the idxServerCol parameter to 0.</span></span> <span data-ttu-id="94494-127">為了略過欄位，您仍然需要所有資訊，才能讓此方法正確運作。</span><span class="sxs-lookup"><span data-stu-id="94494-127">In order to skip a field, you still need all the information for the method to work correctly.</span></span>  
  
 <span data-ttu-id="94494-128">**注意**：可使用 [IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) 函式來保存透過 **BCPColFmt** 提供的格式規格。</span><span class="sxs-lookup"><span data-stu-id="94494-128">**Note** The [IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) function can be used to persist the format specification provided through **BCPColFmt**.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="94494-129">引數</span><span class="sxs-lookup"><span data-stu-id="94494-129">Arguments</span></span>  
 <span data-ttu-id="94494-130">*idxUserDataCol*[in]</span><span class="sxs-lookup"><span data-stu-id="94494-130">*idxUserDataCol*[in]</span></span>  
 <span data-ttu-id="94494-131">使用者的資料檔案中的欄位索引。</span><span class="sxs-lookup"><span data-stu-id="94494-131">Index of field in the user's data file.</span></span>  
  
 <span data-ttu-id="94494-132">*eUserDataType*[in]</span><span class="sxs-lookup"><span data-stu-id="94494-132">*eUserDataType*[in]</span></span>  
 <span data-ttu-id="94494-133">使用者的資料檔案中欄位的資料類型。</span><span class="sxs-lookup"><span data-stu-id="94494-133">The data type of field in the user's data file.</span></span> <span data-ttu-id="94494-134">可用的資料類型會列在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 標頭檔中 (sqlncli，) BCP_TYPE_XXX 格式，例如 BCP_TYPE_SQLINT4。</span><span class="sxs-lookup"><span data-stu-id="94494-134">The data types available are listed in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client header file (sqlncli.h) with BCP_TYPE_XXX format, for example, BCP_TYPE_SQLINT4.</span></span> <span data-ttu-id="94494-135">如果指定了 BCP_TYPE_DEFAULT 值，提供者會嘗試使用與資料表或檢視表資料行類型相同的類型。</span><span class="sxs-lookup"><span data-stu-id="94494-135">If the BCP_TYPE_DEFAULT value is specified, the provider tries to use the same type as the table or view column type.</span></span> <span data-ttu-id="94494-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]當 `eUserDataType` 引數 BCP_TYPE_SQLDECIMAL 或 BCP_TYPE_SQLNUMERIC 時，從和到檔案的大量複製作業：</span><span class="sxs-lookup"><span data-stu-id="94494-136">For bulk copy operations out of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and into a file when the `eUserDataType` argument is BCP_TYPE_SQLDECIMAL or BCP_TYPE_SQLNUMERIC:</span></span>  
  
-   <span data-ttu-id="94494-137">如果來源資料行不是小數或數值，便會使用預設的有效位數和小數位數。</span><span class="sxs-lookup"><span data-stu-id="94494-137">If the source column is not decimal or numeric, the default precision and scale are used.</span></span>  
  
-   <span data-ttu-id="94494-138">如果來源資料行是小數或數值，則會使用來源資料行的有效位數和小數位數。</span><span class="sxs-lookup"><span data-stu-id="94494-138">If the source column is decimal or numeric, the precision and scale of the source column are used.</span></span>  
  
 <span data-ttu-id="94494-139">*cbIndicator*[in]</span><span class="sxs-lookup"><span data-stu-id="94494-139">*cbIndicator*[in]</span></span>  
 <span data-ttu-id="94494-140">欄位的前置長度。</span><span class="sxs-lookup"><span data-stu-id="94494-140">Prefix length for the field.</span></span> <span data-ttu-id="94494-141">預設值為 BCP_PREFIX_DEFAULT。</span><span class="sxs-lookup"><span data-stu-id="94494-141">The default is BCP_PREFIX_DEFAULT.</span></span> <span data-ttu-id="94494-142">此前置詞的有效長度為 0、1、2、4 和 8。</span><span class="sxs-lookup"><span data-stu-id="94494-142">The valid lengths for the prefix are 0, 1, 2, 4 and 8.</span></span> <span data-ttu-id="94494-143">前置詞大小 8 最常用來指示此欄位已分成若干區塊。</span><span class="sxs-lookup"><span data-stu-id="94494-143">A prefix size of 8 is most commonly used to indicate that the field is chunked.</span></span> <span data-ttu-id="94494-144">這可用來有效率地大量複製大型值類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="94494-144">This is used for efficiently bulk copying large value type columns.</span></span>  
  
 <span data-ttu-id="94494-145">*cbUserData*[in]</span><span class="sxs-lookup"><span data-stu-id="94494-145">*cbUserData*[in]</span></span>  
 <span data-ttu-id="94494-146">使用者檔案中此欄位之資料的最大長度 (以位元組為單位)，不包括任何長度指標或結束字元的長度。</span><span class="sxs-lookup"><span data-stu-id="94494-146">The maximum length, in bytes, of this field's data in the user file, not including the length of any length indicator or terminator.</span></span>  
  
 <span data-ttu-id="94494-147">將設定 `cbUserData` 為 BCP_LENGTH_Null 表示資料檔案欄位中的所有值都是，或應設定為 Null。</span><span class="sxs-lookup"><span data-stu-id="94494-147">Setting `cbUserData` to BCP_LENGTH_NULL indicates that all values in the data file fields are, or should be set to NULL.</span></span> <span data-ttu-id="94494-148">將設定 `cbUserData` 為 BCP_LENGTH_VARIABLE 表示系統應該決定每個欄位的資料長度。</span><span class="sxs-lookup"><span data-stu-id="94494-148">Setting `cbUserData` to BCP_LENGTH_VARIABLE indicates that the system should determine the length of data for each field.</span></span> <span data-ttu-id="94494-149">對於某些欄位而言，這可能表示長度/null 指標會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複本之資料前產生，或者表示該指標應該會在複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的資料中出現。</span><span class="sxs-lookup"><span data-stu-id="94494-149">For some fields, this could mean that a length/null indicator is generated to precede data on a copy from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or that the indicator is expected in data copied to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="94494-150">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是字元和二進位資料類型， `cbUserData` 可以是 BCP_LENGTH_VARIABLE、BCP_LENGTH_Null、0或某個正數值。</span><span class="sxs-lookup"><span data-stu-id="94494-150">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character and binary data types, `cbUserData` can be BCP_LENGTH_VARIABLE, BCP_LENGTH_NULL, 0, or some positive value.</span></span> <span data-ttu-id="94494-151">如果 `cbUserData` BCP_LENGTH_VARIABLE，則系統會使用長度指標（如果有的話）或結束字元順序來決定資料的長度。</span><span class="sxs-lookup"><span data-stu-id="94494-151">If `cbUserData` is BCP_LENGTH_VARIABLE, the system uses either the length indicator, if present, or a terminator sequence to determine the length of the data.</span></span> <span data-ttu-id="94494-152">如果同時提供長度指標與結束字元順序，大量複製會使用導致複製最少量資料者。</span><span class="sxs-lookup"><span data-stu-id="94494-152">If both a length indicator and a terminator sequence are supplied, bulk copy uses the one that results in the least amount of data being copied.</span></span> <span data-ttu-id="94494-153">如果 `cbUserData` BCP_LENGTH_VARIABLE，則資料類型為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 字元或二進位類型，如果長度指標和結束字元順序都未指定，系統就會傳回錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="94494-153">If `cbUserData` is BCP_LENGTH_VARIABLE, the data type is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character or binary type, and if neither a length indicator nor a terminator sequence is specified, the system returns an error message.</span></span>  
  
 <span data-ttu-id="94494-154">如果 `cbUserData` 為0或正值，則系統會使用 `cbUserData` 做為資料長度的最大值。</span><span class="sxs-lookup"><span data-stu-id="94494-154">If `cbUserData` is 0 or a positive value, the system uses `cbUserData` as the maximum data length.</span></span> <span data-ttu-id="94494-155">不過，如果除了正數 `cbUserData` ，也提供長度指標或結束字元順序，系統會使用導致複製最少量資料的方法來決定資料長度。</span><span class="sxs-lookup"><span data-stu-id="94494-155">However, if, in addition to a positive `cbUserData`, a length indicator or terminator sequence is provided, the system determines the data length by using the method that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="94494-156">`cbUserData`值表示資料的位元組計數。</span><span class="sxs-lookup"><span data-stu-id="94494-156">The `cbUserData` value represents the count of bytes of data.</span></span> <span data-ttu-id="94494-157">如果字元資料是以 Unicode 寬字元表示，則正 `cbUserData` 參數值代表每個字元的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="94494-157">If character data is represented by Unicode wide characters, then a positive `cbUserData` parameter value represents the number of characters multiplied by the size, in bytes, of each character.</span></span>  
  
 <span data-ttu-id="94494-158">*pbUserDataTerm*[size_is][in]</span><span class="sxs-lookup"><span data-stu-id="94494-158">*pbUserDataTerm*[size_is][in]</span></span>  
 <span data-ttu-id="94494-159">用於此欄位的結束字元順序。</span><span class="sxs-lookup"><span data-stu-id="94494-159">The terminator sequence to be used for the field.</span></span> <span data-ttu-id="94494-160">此參數主要用於字元資料類型，因為其他所有類型都屬固定長度；如果是二進位資料，則需要一個長度指標，才能正確記錄出現的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="94494-160">This parameter is useful mainly for character data types because all other types are of fixed length or, in the case of binary data, require an indicator of length to accurately record the number of bytes present.</span></span>  
  
 <span data-ttu-id="94494-161">為避免結束已擷取的資料，或要指出使用者檔案中的資料未結束，將此參數設定為 NULL。</span><span class="sxs-lookup"><span data-stu-id="94494-161">To avoid terminating extracted data, or to indicate that data in a user file is not terminated, set this parameter to NULL.</span></span>  
  
 <span data-ttu-id="94494-162">如果使用多種指定使用者檔案資料行長度的方式 (例如結束字元和長度指標，或結束字元和資料行長度最大值)，大量複製會選擇導致複製最少量資料的方式。</span><span class="sxs-lookup"><span data-stu-id="94494-162">If more than one means of specifying a user-file column length is used (such as a terminator and a length indicator, or a terminator and a maximum column length), bulk copy chooses the one that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="94494-163">大量複製 API 會視需要執行 Unicode 到 MBCS 的字元轉換。</span><span class="sxs-lookup"><span data-stu-id="94494-163">The bulk copy API performs Unicode-to-MBCS character conversion as required.</span></span> <span data-ttu-id="94494-164">請務必確認結束字元位元組字串與位元組字串長度的設定正確。</span><span class="sxs-lookup"><span data-stu-id="94494-164">Care must be taken to ensure that both the terminator byte string and the length of the byte string are set correctly.</span></span>  
  
 <span data-ttu-id="94494-165">*cbUserDataTerm*[in]</span><span class="sxs-lookup"><span data-stu-id="94494-165">*cbUserDataTerm*[in]</span></span>  
 <span data-ttu-id="94494-166">要用於此資料行的結束字元順序長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="94494-166">The length, in bytes, of the terminator sequence to be used for the column.</span></span> <span data-ttu-id="94494-167">如果資料中沒有或不需要結束字元，將此值設定為 0。</span><span class="sxs-lookup"><span data-stu-id="94494-167">If no terminator is present or desired in the data, set this value to 0.</span></span>  
  
 <span data-ttu-id="94494-168">*idxServerCol*[in]</span><span class="sxs-lookup"><span data-stu-id="94494-168">*idxServerCol*[in]</span></span>  
 <span data-ttu-id="94494-169">此資料行在資料庫資料表中的序數位置。</span><span class="sxs-lookup"><span data-stu-id="94494-169">The ordinal position of the column in the database table.</span></span> <span data-ttu-id="94494-170">第一個資料行編號為 1。</span><span class="sxs-lookup"><span data-stu-id="94494-170">The first column number is 1.</span></span> <span data-ttu-id="94494-171">資料行的序數位置是由 **IColumnsInfo::GetColumnInfo** 或類似的方法所報告。</span><span class="sxs-lookup"><span data-stu-id="94494-171">The ordinal position of a column is reported by **IColumnsInfo::GetColumnInfo** or similar methods.</span></span> <span data-ttu-id="94494-172">如果此值為 0，大量複製會在資料檔案中忽略此欄位。</span><span class="sxs-lookup"><span data-stu-id="94494-172">If this value is 0, bulk copy ignores the field in the data file.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="94494-173">傳回碼值</span><span class="sxs-lookup"><span data-stu-id="94494-173">Return Code Values</span></span>  
 <span data-ttu-id="94494-174">S_OK</span><span class="sxs-lookup"><span data-stu-id="94494-174">S_OK</span></span>  
 <span data-ttu-id="94494-175">此方法已成功。</span><span class="sxs-lookup"><span data-stu-id="94494-175">The method succeeded.</span></span>  
  
 <span data-ttu-id="94494-176">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="94494-176">E_FAIL</span></span>  
 <span data-ttu-id="94494-177">發生提供者特定的錯誤，如需詳細資訊，請使用[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)介面。</span><span class="sxs-lookup"><span data-stu-id="94494-177">A provider specific error occurred, for detailed information use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="94494-178">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="94494-178">E_UNEXPECTED</span></span>  
 <span data-ttu-id="94494-179">此方法的呼叫是非預期的。</span><span class="sxs-lookup"><span data-stu-id="94494-179">The call to the method was unexpected.</span></span> <span data-ttu-id="94494-180">例如，在呼叫這個方法之前，不會呼叫 [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="94494-180">For example, the [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) method was not called before calling this method.</span></span>  
  
 <span data-ttu-id="94494-181">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="94494-181">E_INVALIDARG</span></span>  
 <span data-ttu-id="94494-182">此引數無效。</span><span class="sxs-lookup"><span data-stu-id="94494-182">The argument was invalid.</span></span>  
  
 <span data-ttu-id="94494-183">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="94494-183">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="94494-184">記憶體不足的錯誤。</span><span class="sxs-lookup"><span data-stu-id="94494-184">Out of memory error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94494-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94494-185">See Also</span></span>  
 <span data-ttu-id="94494-186">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="94494-186">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="94494-187">執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="94494-187">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
