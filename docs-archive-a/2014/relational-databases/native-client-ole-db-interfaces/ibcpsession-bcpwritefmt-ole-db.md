---
title: IBCPSession::BCPWriteFmt (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPWriteFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPWriteFmt method
ms.assetid: add50425-2ed6-411a-a391-4ce63c364892
author: rothja
ms.author: jroth
ms.openlocfilehash: ee4dcb5809c0f0fbb6d3f7aba6f4af5f6991e0e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599501"
---
# <a name="ibcpsessionbcpwritefmt-ole-db"></a><span data-ttu-id="13682-102">IBCPSession::BCPWriteFmt (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="13682-102">IBCPSession::BCPWriteFmt (OLE DB)</span></span>
  <span data-ttu-id="13682-103">將每個資料行的格式資訊寫入格式檔案。</span><span class="sxs-lookup"><span data-stu-id="13682-103">Writes format information for each column to the format file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13682-104">語法</span><span class="sxs-lookup"><span data-stu-id="13682-104">Syntax</span></span>  
  
```  
  
HRESULT BCPWriteFmt(   
const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a><span data-ttu-id="13682-105">備註</span><span class="sxs-lookup"><span data-stu-id="13682-105">Remarks</span></span>  
 <span data-ttu-id="13682-106">格式檔案會指定大量複製所建立之資料檔的資料格式。</span><span class="sxs-lookup"><span data-stu-id="13682-106">The format file specifies the data format of a data file created by bulk copy.</span></span> <span data-ttu-id="13682-107">[IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) 和 [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) 方法的呼叫會定義資料檔案的格式。</span><span class="sxs-lookup"><span data-stu-id="13682-107">Calls to the [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) and [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) methods define the format of the data file.</span></span> <span data-ttu-id="13682-108">**BCPWriteFmt** 方法會將此定義儲存在 pwszFormatFile 引數參考的檔案中。</span><span class="sxs-lookup"><span data-stu-id="13682-108">The **BCPWriteFmt** method saves this definition in the file referenced by the pwszFormatFile argument.</span></span>  
  
 <span data-ttu-id="13682-109">**BCPWriteFmt** 方法可以用 xml 或文字格式儲存格式檔案。</span><span class="sxs-lookup"><span data-stu-id="13682-109">The **BCPWriteFmt** method can save the format files in either xml or text format.</span></span> <span data-ttu-id="13682-110">這必須搭配 [IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) 方法使用 BCP_OPTION_XML 控制選項指示。</span><span class="sxs-lookup"><span data-stu-id="13682-110">This must be indicated by using the BCP_OPTION_XML control option with the [IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) method.</span></span>  
  
 <span data-ttu-id="13682-111">若要載入已儲存的格式檔案，請使用 [IBCPSession::BCPReadFmt](ibcpsession-bcpreadfmt-ole-db.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="13682-111">To load a saved format file, use the [IBCPSession::BCPReadFmt](ibcpsession-bcpreadfmt-ole-db.md) method.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="13682-112">引數</span><span class="sxs-lookup"><span data-stu-id="13682-112">Arguments</span></span>  
 <span data-ttu-id="13682-113">*pwszFormatFile*[in]</span><span class="sxs-lookup"><span data-stu-id="13682-113">*pwszFormatFile*[in]</span></span>  
 <span data-ttu-id="13682-114">包含資料檔案式值之檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="13682-114">The path and file name of the file containing the format values for the data file.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="13682-115">傳回碼值</span><span class="sxs-lookup"><span data-stu-id="13682-115">Return Code Values</span></span>  
 <span data-ttu-id="13682-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="13682-116">S_OK</span></span>  
 <span data-ttu-id="13682-117">此方法已成功。</span><span class="sxs-lookup"><span data-stu-id="13682-117">The method succeeded.</span></span>  
  
 <span data-ttu-id="13682-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="13682-118">E_FAIL</span></span>  
 <span data-ttu-id="13682-119">發生提供者特定的錯誤;如需詳細資訊，請使用[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)介面。</span><span class="sxs-lookup"><span data-stu-id="13682-119">A provider-specific error occurred; for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="13682-120">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="13682-120">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="13682-121">記憶體不足錯誤</span><span class="sxs-lookup"><span data-stu-id="13682-121">Out-of-memory error.</span></span>  
  
 <span data-ttu-id="13682-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="13682-122">E_UNEXPECTED</span></span>  
 <span data-ttu-id="13682-123">此方法的呼叫是非預期的。</span><span class="sxs-lookup"><span data-stu-id="13682-123">The call to the method was unexpected.</span></span> <span data-ttu-id="13682-124">例如，在呼叫這個方法之前，不會呼叫 [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="13682-124">For example, the [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) method was not called before calling this method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13682-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13682-125">See Also</span></span>  
 <span data-ttu-id="13682-126">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="13682-126">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="13682-127">執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="13682-127">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
