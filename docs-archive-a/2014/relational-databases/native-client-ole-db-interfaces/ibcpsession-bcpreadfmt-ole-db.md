---
title: IBCPSession::BCPReadFmt (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPReadFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPReadFmt method
ms.assetid: e2a12050-94e4-48a3-8a48-b780d646f116
author: rothja
ms.author: jroth
ms.openlocfilehash: ca811dceb8ab6771e3bdd6689a8e11eca6a0e3ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707446"
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a><span data-ttu-id="7feaa-102">IBCPSession::BCPReadFmt (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="7feaa-102">IBCPSession::BCPReadFmt (OLE DB)</span></span>
  <span data-ttu-id="7feaa-103">從格式檔案中讀取每個資料行的格式資訊。</span><span class="sxs-lookup"><span data-stu-id="7feaa-103">Reads format information for each column from the format file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7feaa-104">語法</span><span class="sxs-lookup"><span data-stu-id="7feaa-104">Syntax</span></span>  
  
```  
  
HRESULT BCPReadFmt(   
const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a><span data-ttu-id="7feaa-105">備註</span><span class="sxs-lookup"><span data-stu-id="7feaa-105">Remarks</span></span>  
 <span data-ttu-id="7feaa-106">**BCPReadFmt** 方法是用來讀取格式檔案中的資料 (格式檔案會指定資料檔中的資料格式)。</span><span class="sxs-lookup"><span data-stu-id="7feaa-106">The **BCPReadFmt** method is used for reading data from a format file that specifies the format of data in the data file.</span></span> <span data-ttu-id="7feaa-107">這個方法能夠偵測格式檔案的正確版本。</span><span class="sxs-lookup"><span data-stu-id="7feaa-107">This method is capable of detecting the correct version of the format file.</span></span> <span data-ttu-id="7feaa-108">它可以自動偵測格式檔案為 xml 還是舊樣式的文字格式，並適當地產生行為。</span><span class="sxs-lookup"><span data-stu-id="7feaa-108">It can automatically detect whether the format file is in xml or old style text format and behaves accordingly.</span></span> <span data-ttu-id="7feaa-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者 BCP 支援的格式檔案版本是6.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="7feaa-109">The format file versions supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider BCP are version 6.0 or newer.</span></span>  
  
 <span data-ttu-id="7feaa-110">當 **BCPReadFmt** 方法讀取格式值以後，它會適當地呼叫 [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) 和 [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="7feaa-110">After the **BCPReadFmt** method reads the format values, it makes the appropriate calls to the [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) and [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) methods.</span></span> <span data-ttu-id="7feaa-111">使用者不需要剖析格式檔案，也不需要進行這些呼叫。</span><span class="sxs-lookup"><span data-stu-id="7feaa-111">There is no need for the user to parse a format file and make these calls.</span></span>  
  
 <span data-ttu-id="7feaa-112">若要儲存格式檔案，請呼叫 [IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="7feaa-112">To save a format file, call the [IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) method.</span></span> <span data-ttu-id="7feaa-113">**BCPReadFmt** 方法的呼叫可以參考已儲存的格式。</span><span class="sxs-lookup"><span data-stu-id="7feaa-113">Calls to the **BCPReadFmt** method can reference saved formats.</span></span> <span data-ttu-id="7feaa-114">另外，大量複製公用程式 (**bcp**) 可以將使用者定義的資料格式儲存在由 **BCPReadFmt** 方法參考的檔案中。</span><span class="sxs-lookup"><span data-stu-id="7feaa-114">Alternatively, the bulk-copy utility (**bcp**) can save user-defined data formats in files that can be referenced by the **BCPReadFmt** method.</span></span>  
  
 <span data-ttu-id="7feaa-115">`BCP_OPTION_DELAYREADFMT` [IBCPSession：： BCPControl](ibcpsession-bcpcontrol-ole-db.md)的*eOption*參數值會修改 IBCPSession：： BCPReadFmt 的行為。</span><span class="sxs-lookup"><span data-stu-id="7feaa-115">The `BCP_OPTION_DELAYREADFMT` value of the *eOption* parameter of [IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) modifies the behavior of IBCPSession::BCPReadFmt.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="7feaa-116">引數</span><span class="sxs-lookup"><span data-stu-id="7feaa-116">Arguments</span></span>  
 <span data-ttu-id="7feaa-117">*pwszFormatFile*[in]</span><span class="sxs-lookup"><span data-stu-id="7feaa-117">*pwszFormatFile*[in]</span></span>  
 <span data-ttu-id="7feaa-118">包含資料檔案式值之檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="7feaa-118">The path and file name of the file containing the format values for the data file.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="7feaa-119">傳回碼值</span><span class="sxs-lookup"><span data-stu-id="7feaa-119">Return Code Values</span></span>  
 <span data-ttu-id="7feaa-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="7feaa-120">S_OK</span></span>  
 <span data-ttu-id="7feaa-121">此方法已成功。</span><span class="sxs-lookup"><span data-stu-id="7feaa-121">The method succeeded.</span></span>  
  
 <span data-ttu-id="7feaa-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7feaa-122">E_FAIL</span></span>  
 <span data-ttu-id="7feaa-123">發生提供者特定的錯誤，如需詳細資訊，請使用 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) 介面。</span><span class="sxs-lookup"><span data-stu-id="7feaa-123">A provider-specific error occurred, for detailed information use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="7feaa-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7feaa-124">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="7feaa-125">記憶體不足的錯誤。</span><span class="sxs-lookup"><span data-stu-id="7feaa-125">Out of memory error.</span></span>  
  
 <span data-ttu-id="7feaa-126">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="7feaa-126">E_UNEXPECTED</span></span>  
 <span data-ttu-id="7feaa-127">此方法的呼叫是非預期的。</span><span class="sxs-lookup"><span data-stu-id="7feaa-127">The call to the method was unexpected.</span></span> <span data-ttu-id="7feaa-128">例如，在呼叫這個方法之前，不會呼叫 [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="7feaa-128">For example, the [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) method was not called before calling this method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7feaa-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7feaa-129">See Also</span></span>  
 <span data-ttu-id="7feaa-130">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="7feaa-130">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="7feaa-131">執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="7feaa-131">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
