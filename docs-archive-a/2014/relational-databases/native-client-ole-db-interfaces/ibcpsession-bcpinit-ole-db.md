---
title: IBCPSession::BCPInit (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPInit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPInit method
ms.assetid: 583096d7-da34-49be-87fd-31210aac81aa
author: rothja
ms.author: jroth
ms.openlocfilehash: 25a01c71811de9d47ce01714402460bb53d4c70e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698137"
---
# <a name="ibcpsessionbcpinit-ole-db"></a><span data-ttu-id="f7594-102">IBCPSession::BCPInit (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="f7594-102">IBCPSession::BCPInit (OLE DB)</span></span>
  <span data-ttu-id="f7594-103">初始化大量複製結構、執行一些錯誤檢查、確認資料和格式檔案名稱正確無誤，然後開啟這些項目。</span><span class="sxs-lookup"><span data-stu-id="f7594-103">Initializes the bulk copy structure, performs some error checking, verifies that the data and format file names are correct, and then opens them.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7594-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7594-104">Syntax</span></span>  
  
```  
  
HRESULT BCPInit(   
const wchar_t *pwszTable,  
const wchar_t *pwszDataFile,  
const wchar_t *pwszErrorFile,  
inteDirection);  
```  
  
## <a name="remarks"></a><span data-ttu-id="f7594-105">備註</span><span class="sxs-lookup"><span data-stu-id="f7594-105">Remarks</span></span>  
 <span data-ttu-id="f7594-106">**BCPInit** 方法應該在任何其他的大量複製方法之前呼叫。</span><span class="sxs-lookup"><span data-stu-id="f7594-106">The **BCPInit** method should be called before any other bulk-copy method.</span></span> <span data-ttu-id="f7594-107">**BCPInit** 方法會針對工作站和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之間資料的大量複製，執行必要的初始化。</span><span class="sxs-lookup"><span data-stu-id="f7594-107">The **BCPInit** method performs the necessary initializations for a bulk copy of data between the workstation and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f7594-108">**BCPInit** 方法會檢查資料庫來源或目標資料表的結構，而不會檢查資料檔案的結構。</span><span class="sxs-lookup"><span data-stu-id="f7594-108">The **BCPInit** method examines the structure of the database source or target table, not the data file.</span></span> <span data-ttu-id="f7594-109">此方法會根據資料庫資料表、檢視或 SELECT 結果集中的每個資料行，指定資料檔的資料格式值。</span><span class="sxs-lookup"><span data-stu-id="f7594-109">It specifies data format values for the data file based on each column in the database table, view, or SELECT result set.</span></span> <span data-ttu-id="f7594-110">這個指定包括每個資料行的資料類型、資料中是否有長度或 null 指標和結束字元位元組字串，以及固定長度資料類型的寬度。</span><span class="sxs-lookup"><span data-stu-id="f7594-110">This specification includes the data type of each column, the presence or absence of a length or null indicator and terminator byte strings in the data, and the width of fixed-length data types.</span></span> <span data-ttu-id="f7594-111">**BCPInit** 方法會設定這些值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f7594-111">The **BCPInit** method sets these values as follows:</span></span>  
  
-   <span data-ttu-id="f7594-112">指定的資料類型為資料行在資料庫資料表、檢視或 SELECT 結果集中的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f7594-112">The data type specified is the data type of the column in the database table, view, or SELECT result set.</span></span> <span data-ttu-id="f7594-113">資料類型是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以 Native Client 標頭檔中指定的原生資料類型來列舉， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (sqlncli) 。</span><span class="sxs-lookup"><span data-stu-id="f7594-113">The data type is enumerated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data types specified in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client header file (sqlncli.h).</span></span> <span data-ttu-id="f7594-114">其值會採用 BCP_TYPE_XXX 的模式。</span><span class="sxs-lookup"><span data-stu-id="f7594-114">Their values are in the pattern of BCP_TYPE_XXX.</span></span> <span data-ttu-id="f7594-115">資料會以其電腦格式表示。</span><span class="sxs-lookup"><span data-stu-id="f7594-115">The data is represented in its computer form.</span></span> <span data-ttu-id="f7594-116">也就是說，來自 integer 資料類型之資料行的資料會根據建立資料檔案之電腦，以四個位元組由大到小或由小到大的順序表示。</span><span class="sxs-lookup"><span data-stu-id="f7594-116">That is, data from a column of integer data type is represented by a four-byte sequence that is big-or little-endian based on the computer that created the data file.</span></span>  
  
-   <span data-ttu-id="f7594-117">如果資料庫資料類型的長度是固定的，資料檔案資料的長度也是固定的。</span><span class="sxs-lookup"><span data-stu-id="f7594-117">If a database data type is fixed in length, the data file data is also fixed in length.</span></span> <span data-ttu-id="f7594-118">處理資料的大量複製方法 (例如 [IBCPSession::BCPExec](ibcpsession-bcpexec-ole-db.md)) 會剖析資料列，期望資料在資料檔案中的長度與資料在資料庫資料表、檢視或 SELECT 資料行清單中指定的長度相同。</span><span class="sxs-lookup"><span data-stu-id="f7594-118">Bulk-copy methods that process data (for example, [IBCPSession::BCPExec](ibcpsession-bcpexec-ole-db.md)) parse data rows expecting the length of the data in the data file to be identical to the length of the data specified in the database table, view, or SELECT column list.</span></span> <span data-ttu-id="f7594-119">例如，定義為 `char(13)` 之資料庫資料行的資料，對於檔案中資料的每個資料列，必須以 13 個字元表示。</span><span class="sxs-lookup"><span data-stu-id="f7594-119">For example, data for a database column defined as `char(13)` must be represented by 13 characters for each row of data in the file.</span></span> <span data-ttu-id="f7594-120">如果資料庫資料行允許使用 Null 值，固定長度的資料前置詞可以是 Null 指標。</span><span class="sxs-lookup"><span data-stu-id="f7594-120">Fixed-length data can be prefixed with a null indicator if the database column allows null values.</span></span>  
  
-   <span data-ttu-id="f7594-121">複製資料到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，資料檔案對於資料庫資料表中的每個資料行都必須有資料。</span><span class="sxs-lookup"><span data-stu-id="f7594-121">When copying data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the data file must have data for each column in the database table.</span></span> <span data-ttu-id="f7594-122">從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複製資料時，來自資料庫資料表、檢視或 SELECT 結果集中所有資料行的資料都會複製到資料檔案中。</span><span class="sxs-lookup"><span data-stu-id="f7594-122">When copying data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], data from all columns in the database table, view, or SELECT result set are copied to the data file.</span></span>  
  
-   <span data-ttu-id="f7594-123">複製資料到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，資料行在資料檔案中的序數位置必須與資料行在資料庫資料表中的序數位置相同。</span><span class="sxs-lookup"><span data-stu-id="f7594-123">When copying data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the ordinal position of a column in the data file must be identical to the ordinal position of the column in the database table.</span></span> <span data-ttu-id="f7594-124">從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複製資料時，**BCPExec** 方法會根據資料行在資料庫資料表中的位置來放置資料。</span><span class="sxs-lookup"><span data-stu-id="f7594-124">When copying data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the **BCPExec** method places data based on the ordinal position of the column in the database table.</span></span>  
  
-   <span data-ttu-id="f7594-125">如果資料庫資料類型的長度是變數 (例如，`varbinary(22)`)，或者如果資料庫資料行可以包含 Null 值，資料檔案中資料的前置詞為長度/Null 指標。</span><span class="sxs-lookup"><span data-stu-id="f7594-125">If a database data type is variable in length (for example, `varbinary(22)`) or if a database column can contain null values, data in the data file is prefixed by a length/null indicator.</span></span> <span data-ttu-id="f7594-126">指標的寬度會根據資料類型和大量複製的版本而改變。</span><span class="sxs-lookup"><span data-stu-id="f7594-126">The width of the indicator varies based on the data type and version of bulk copy.</span></span> <span data-ttu-id="f7594-127">[IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) 方法選項 BCP_OPTION_FILEFMT 會在資料中的指標寬度比預期窄時指出，藉以提供舊版大量複製資料檔案與執行新版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之伺服器之間的相容性。</span><span class="sxs-lookup"><span data-stu-id="f7594-127">The [IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) method option BCP_OPTION_FILEFMT provides compatibility between earlier bulk-copy data files and servers running later versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by indicating when the width of indicators in the data is narrower than expected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7594-128">若要變更針對資料檔案而指定的資料格式值，請使用 [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) 和 [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="f7594-128">To change the data format values specified for a data file, use the [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) and [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) methods.</span></span>  
  
 <span data-ttu-id="f7594-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的大量複製可以針對不包含索引的資料表進行最佳化，方法是設定資料庫選項 **select into/bulkcopy**。</span><span class="sxs-lookup"><span data-stu-id="f7594-129">Bulk copies to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be optimized for tables that do not contain indexes by setting the database option **select into/bulkcopy**.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="f7594-130">引數</span><span class="sxs-lookup"><span data-stu-id="f7594-130">Arguments</span></span>  
 <span data-ttu-id="f7594-131">*pwszTable*[in]</span><span class="sxs-lookup"><span data-stu-id="f7594-131">*pwszTable*[in]</span></span>  
 <span data-ttu-id="f7594-132">這是要來回複製之資料庫資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="f7594-132">The name of the database table to be copied into or out of.</span></span> <span data-ttu-id="f7594-133">此名稱也可以包含資料庫名稱或擁有者名稱。</span><span class="sxs-lookup"><span data-stu-id="f7594-133">The name can include the database name or the owner name.</span></span> <span data-ttu-id="f7594-134">例如，"pubs.username.titles"、"pubs..titles" 和 "username.titles" 等。</span><span class="sxs-lookup"><span data-stu-id="f7594-134">For example, "pubs.username.titles", "pubs..titles", "username.titles".</span></span>  
  
 <span data-ttu-id="f7594-135">如果 eDirection 引數設定為 BCP_DIRECTION_OUT，則 pwszTable 引數也可以做為資料庫檢視的名稱。</span><span class="sxs-lookup"><span data-stu-id="f7594-135">If the eDirection argument is set to BCP_DIRECTION_OUT, the pwszTable argument can be the name of a database view.</span></span>  
  
 <span data-ttu-id="f7594-136">如果 eDirection 引數設定為 BCP_DIRECTION_OUT，而且會在呼叫 **BCPExec** 方法之前，使用 **BCPControl** 方法來指定 SELECT 陳述式，則 *pwszTable* 引數必須設定為 NULL。</span><span class="sxs-lookup"><span data-stu-id="f7594-136">If the eDirection argument is set to BCP_DIRECTION_OUT and a SELECT statement is specified using the **BCPControl** method before the **BCPExec** method is called, the *pwszTable* argument must be set to NULL.</span></span>  
  
 <span data-ttu-id="f7594-137">*pwszDataFile*[in]</span><span class="sxs-lookup"><span data-stu-id="f7594-137">*pwszDataFile*[in]</span></span>  
 <span data-ttu-id="f7594-138">這是要來回複製之使用者檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="f7594-138">The name of the user file to be copied into or out of.</span></span>  
  
 <span data-ttu-id="f7594-139">*pwszErrorFile*[in]</span><span class="sxs-lookup"><span data-stu-id="f7594-139">*pwszErrorFile*[in]</span></span>  
 <span data-ttu-id="f7594-140">這是錯誤檔案的名稱，該檔案會以進度訊息、錯誤訊息，以及因為任何原因而無法從使用者檔案複製到資料表之任何資料列的複本。</span><span class="sxs-lookup"><span data-stu-id="f7594-140">The name of the error file to be filled with progress messages, error messages, and copies of any rows that could not be copied from a user file to a table.</span></span> <span data-ttu-id="f7594-141">如果 *pwszErrorFile* 引數設定為 NULL，則不會使用任何錯誤檔案。</span><span class="sxs-lookup"><span data-stu-id="f7594-141">If the *pwszErrorFile* argument is set to NULL, no error file is used.</span></span>  
  
 <span data-ttu-id="f7594-142">*eDirection*[in]</span><span class="sxs-lookup"><span data-stu-id="f7594-142">*eDirection*[in]</span></span>  
 <span data-ttu-id="f7594-143">這是複製的方向，BCP_DIRECTION_IN 或 BCP_DIRECTION _OUT。</span><span class="sxs-lookup"><span data-stu-id="f7594-143">The direction of the copy operation, either BCP_DIRECTION_IN or BCP_DIRECTION _OUT.</span></span> <span data-ttu-id="f7594-144">BCP_DIRECTION _IN 代表從使用者檔案複製到資料庫資料表；BCP_DIRECTION _OUT 則代表從資料庫資料表複製到使用者檔案。</span><span class="sxs-lookup"><span data-stu-id="f7594-144">BCP_DIRECTION _IN indicates a copy from a user file to a database table; BCP_DIRECTION _OUT indicates a copy from a database table to a user file.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="f7594-145">傳回碼值</span><span class="sxs-lookup"><span data-stu-id="f7594-145">Return Code Values</span></span>  
 <span data-ttu-id="f7594-146">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7594-146">S_OK</span></span>  
 <span data-ttu-id="f7594-147">此方法已成功。</span><span class="sxs-lookup"><span data-stu-id="f7594-147">The method succeeded.</span></span>  
  
 <span data-ttu-id="f7594-148">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f7594-148">E_FAIL</span></span>  
 <span data-ttu-id="f7594-149">發生提供者特定的錯誤。如需詳細資訊，請使用[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)介面。</span><span class="sxs-lookup"><span data-stu-id="f7594-149">A provider specific error occurred' for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="f7594-150">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f7594-150">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="f7594-151">記憶體不足錯誤</span><span class="sxs-lookup"><span data-stu-id="f7594-151">Out-of-memory error.</span></span>  
  
 <span data-ttu-id="f7594-152">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f7594-152">E_INVALIDARG</span></span>  
 <span data-ttu-id="f7594-153">未正確指定一個或多個引數。</span><span class="sxs-lookup"><span data-stu-id="f7594-153">One or more of the arguments was not correctly specified.</span></span> <span data-ttu-id="f7594-154">例如，指定了無效的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="f7594-154">For example, an invalid file name was given.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7594-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7594-155">See Also</span></span>  
 <span data-ttu-id="f7594-156">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="f7594-156">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="f7594-157">執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="f7594-157">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
