---
title: IBCPSession::BCPColumns (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPColumns (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPColumns method
ms.assetid: c338abe8-9e30-4853-a7c6-b1a6c00095e1
author: rothja
ms.author: jroth
ms.openlocfilehash: c842b2a815074c0db7e6ab21e0a85eac68a986a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707457"
---
# <a name="ibcpsessionbcpcolumns-ole-db"></a><span data-ttu-id="dc494-102">IBCPSession::BCPColumns (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="dc494-102">IBCPSession::BCPColumns (OLE DB)</span></span>
  <span data-ttu-id="dc494-103">設定要繫結至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中之資料行的欄位數目。</span><span class="sxs-lookup"><span data-stu-id="dc494-103">Sets the number of fields that are to be bound to the columns in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc494-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc494-104">Syntax</span></span>  
  
```  
  
HRESULT BCPColumns(   
DBCOUNTITEMnColumns);  
```  
  
## <a name="remarks"></a><span data-ttu-id="dc494-105">備註</span><span class="sxs-lookup"><span data-stu-id="dc494-105">Remarks</span></span>  
 <span data-ttu-id="dc494-106">它會在內部呼叫 [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) 來設定欄位資料的預設值。</span><span class="sxs-lookup"><span data-stu-id="dc494-106">Internally it calls [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) to set the default values for field data.</span></span> <span data-ttu-id="dc494-107">這些預設值會從 SQL Server 資料行資訊取得，提供者會在透過 [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) 指定資料表名稱時，在內部擷取這項資訊。</span><span class="sxs-lookup"><span data-stu-id="dc494-107">These default values are obtained from the SQL Server column information that the provider internally retrieves when the table name is specified through [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc494-108">只有在已使用有效的檔案名稱呼叫 **BCPInit** 後，才可以呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="dc494-108">This method can be called only after **BCPInit** has been called with a valid file name.</span></span>  
  
 <span data-ttu-id="dc494-109">只有打算使用與預設值不同的使用者檔案格式時，才可以呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="dc494-109">You should call this method only if you intend to use a user-file format that differs from the default.</span></span> <span data-ttu-id="dc494-110">如需預設使用者檔案格式之描述的詳細資訊，請參閱 **BCPInit** 方法。</span><span class="sxs-lookup"><span data-stu-id="dc494-110">For more information about a description of the default user-file format, see the **BCPInit** method.</span></span>  
  
 <span data-ttu-id="dc494-111">在呼叫 **BCPColumns** 方法之後，您必須針對使用者檔案中的每個資料行呼叫 **BCPColFmt** 方法，以完整定義自訂的檔案格式。</span><span class="sxs-lookup"><span data-stu-id="dc494-111">After calling the **BCPColumns** method, you must call the **BCPColFmt** method for each column in the user file to completely define a custom file format.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="dc494-112">引數</span><span class="sxs-lookup"><span data-stu-id="dc494-112">Arguments</span></span>  
 <span data-ttu-id="dc494-113">*nColumns*[in]</span><span class="sxs-lookup"><span data-stu-id="dc494-113">*nColumns*[in]</span></span>  
 <span data-ttu-id="dc494-114">使用者檔案中的欄位總數。</span><span class="sxs-lookup"><span data-stu-id="dc494-114">The total number of fields in the user file.</span></span> <span data-ttu-id="dc494-115">即使您準備要將資料從使用者檔案大量複製到 SQL Server 資料表，而不想複製使用者檔案中的所有欄位，也仍必須將 *nColumns* 引數設定為使用者檔案欄位的總數。</span><span class="sxs-lookup"><span data-stu-id="dc494-115">Even if you are preparing to bulk copy data from the user file to a SQL Server table and do not intend to copy all fields in the user file, you must still set the *nColumns* argument to the total number of user-file fields.</span></span> <span data-ttu-id="dc494-116">接著，系統可以透過 **BCPColFmt** 指定略過的欄位。</span><span class="sxs-lookup"><span data-stu-id="dc494-116">The skipped fields can then be specified through **BCPColFmt**.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="dc494-117">傳回碼值</span><span class="sxs-lookup"><span data-stu-id="dc494-117">Return Code Values</span></span>  
 <span data-ttu-id="dc494-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="dc494-118">S_OK</span></span>  
 <span data-ttu-id="dc494-119">此方法已成功。</span><span class="sxs-lookup"><span data-stu-id="dc494-119">The method succeeded.</span></span>  
  
 <span data-ttu-id="dc494-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dc494-120">E_FAIL</span></span>  
 <span data-ttu-id="dc494-121">發生提供者特定的錯誤;如需詳細資訊，請使用[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)介面。</span><span class="sxs-lookup"><span data-stu-id="dc494-121">A provider-specific error occurred; for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="dc494-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="dc494-122">E_UNEXPECTED</span></span>  
 <span data-ttu-id="dc494-123">此方法的呼叫是非預期的。</span><span class="sxs-lookup"><span data-stu-id="dc494-123">The call to the method was unexpected.</span></span> <span data-ttu-id="dc494-124">例如，在呼叫這個方法之前，不會呼叫 **BCPInit** 方法。</span><span class="sxs-lookup"><span data-stu-id="dc494-124">For example, the **BCPInit** method was not called before calling this method.</span></span> <span data-ttu-id="dc494-125">針對大量複製作業呼叫此方法超過一次時，也會發生這個狀況。</span><span class="sxs-lookup"><span data-stu-id="dc494-125">Also occurs when this method is called more than once for a bulk copy operation.</span></span>  
  
 <span data-ttu-id="dc494-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="dc494-126">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="dc494-127">記憶體不足錯誤</span><span class="sxs-lookup"><span data-stu-id="dc494-127">Out-of-memory error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc494-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc494-128">See Also</span></span>  
 <span data-ttu-id="dc494-129">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="dc494-129">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="dc494-130">執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="dc494-130">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
