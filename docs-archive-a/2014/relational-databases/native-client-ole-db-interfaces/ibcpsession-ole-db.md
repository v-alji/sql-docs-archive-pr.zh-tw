---
title: IBCPSession (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
author: rothja
ms.author: jroth
ms.openlocfilehash: 0d32da9c06a200d5924dbae18d6b7513f46c88ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707449"
---
# <a name="ibcpsession-ole-db"></a><span data-ttu-id="8cd60-102">IBCPSession (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="8cd60-102">IBCPSession (OLE DB)</span></span>
  <span data-ttu-id="8cd60-103">**IBCPSession** 介面會公開以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 檔案為基礎之大量複製作業的支援。</span><span class="sxs-lookup"><span data-stu-id="8cd60-103">The **IBCPSession** interface exposes support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] file-based bulk copy operations.</span></span> <span data-ttu-id="8cd60-104">**IBCPSession**介面會在與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會話相同層級的 Native Client OLE DB 提供者中公開。</span><span class="sxs-lookup"><span data-stu-id="8cd60-104">The **IBCPSession** interface is exposed in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider under the same level as Sessions.</span></span> <span data-ttu-id="8cd60-105">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者中，資料來源物件是會話物件的 factory，而大量複製作業則是在連接屬性 SSPROP_ENABLEBULKCOPY 中指定。</span><span class="sxs-lookup"><span data-stu-id="8cd60-105">In the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, data source objects are factories for Session objects, and bulk copy operations are specified in the connection property SSPROP_ENABLEBULKCOPY.</span></span> <span data-ttu-id="8cd60-106">此外，SSPROP_ENABLEFASTLOAD 屬性應該要設定為 true。</span><span class="sxs-lookup"><span data-stu-id="8cd60-106">In addition, the SSPROP_ENABLEFASTLOAD property should be set to true.</span></span>  
  
 <span data-ttu-id="8cd60-107">然後，呼叫 **IDBCreateSession::CreateSession** 方法將會導致建立 **BulkCopySession** 物件。</span><span class="sxs-lookup"><span data-stu-id="8cd60-107">Calling the **IDBCreateSession::CreateSession** method will then result in the creation of a **BulkCopySession** object.</span></span> <span data-ttu-id="8cd60-108">所有透過 **IBCPSession** 物件公開之以檔案為基礎的大量複製方法會變成可在這個 **IBCPSession** 物件的 **IBCPSession** 介面上使用幾乎相同的簽章進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="8cd60-108">All the file-based bulk copy methods exposed through the **IBCPSession** object are then callable with nearly similar signatures on this **IBCPSession** object's **IBCPSession** interface.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8cd60-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者支援透過[IRowsetFastLoad](irowsetfastload-ole-db.md)介面進行以記憶體為基礎的大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="8cd60-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports memory-based bulk copy operations through the [IRowsetFastLoad](irowsetfastload-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="8cd60-110">如需有關使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者進行大量複製作業的詳細資訊，請參閱[執行大量複製作業](../native-client/features/performing-bulk-copy-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="8cd60-110">For more information about using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider for bulk copy operations, see [Performing Bulk Copy Operations](../native-client/features/performing-bulk-copy-operations.md).</span></span>  
  
 <span data-ttu-id="8cd60-111">如需示範如何使用 **IBCPSession** 介面的範例，請參閱 [IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="8cd60-111">For a sample showing how to use the **IBCPSession** interface, see [IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8cd60-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="8cd60-112">In This Section</span></span>  
  
|<span data-ttu-id="8cd60-113">方法</span><span class="sxs-lookup"><span data-stu-id="8cd60-113">Method</span></span>|<span data-ttu-id="8cd60-114">描述</span><span class="sxs-lookup"><span data-stu-id="8cd60-114">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8cd60-115">IBCPSession::BCPColFmt &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd60-115">IBCPSession::BCPColFmt &#40;OLE DB&#41;</span></span>](ibcpsession-bcpcolfmt-ole-db.md)|<span data-ttu-id="8cd60-116">在程式變數與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料行之間建立繫結。</span><span class="sxs-lookup"><span data-stu-id="8cd60-116">Creates a binding between program variables and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columns.</span></span>|  
|[<span data-ttu-id="8cd60-117">IBCPSession::BCPColumns &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd60-117">IBCPSession::BCPColumns &#40;OLE DB&#41;</span></span>](ibcpsession-bcpcolumns-ole-db.md)|<span data-ttu-id="8cd60-118">設定要繫結至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中之資料行的欄位數目。</span><span class="sxs-lookup"><span data-stu-id="8cd60-118">Sets the number of fields that are to be bound to the columns in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>|  
|[<span data-ttu-id="8cd60-119">IBCPSession::BCPControl &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd60-119">IBCPSession::BCPControl &#40;OLE DB&#41;</span></span>](ibcpsession-bcpcontrol-ole-db.md)|<span data-ttu-id="8cd60-120">設定大量複製作業的選項。</span><span class="sxs-lookup"><span data-stu-id="8cd60-120">Sets the options for a bulk copy operation.</span></span>|  
|[<span data-ttu-id="8cd60-121">IBCPSession::BCPDone &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd60-121">IBCPSession::BCPDone &#40;OLE DB&#41;</span></span>](ibcpsession-bcpdone-ole-db.md)|<span data-ttu-id="8cd60-122">認可要傳送至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的其餘資料列。</span><span class="sxs-lookup"><span data-stu-id="8cd60-122">Commits the remaining rows to be sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="8cd60-123">IBCPSession::BCPExec &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd60-123">IBCPSession::BCPExec &#40;OLE DB&#41;</span></span>](ibcpsession-bcpexec-ole-db.md)|<span data-ttu-id="8cd60-124">執行大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="8cd60-124">Performs the bulk copy operation.</span></span>|  
|[<span data-ttu-id="8cd60-125">IBCPSession::BCPInit &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd60-125">IBCPSession::BCPInit &#40;OLE DB&#41;</span></span>](ibcpsession-bcpinit-ole-db.md)|<span data-ttu-id="8cd60-126">初始化大量複製結構、執行一些錯誤檢查、確認資料和格式檔案名稱正確無誤，然後開啟這些項目。</span><span class="sxs-lookup"><span data-stu-id="8cd60-126">Initializes the bulk copy structure, performs some error checking, verifies that the data and format file names are correct, and then opens them.</span></span>|  
|[<span data-ttu-id="8cd60-127">IBCPSession::BCPReadFmt &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd60-127">IBCPSession::BCPReadFmt &#40;OLE DB&#41;</span></span>](ibcpsession-bcpreadfmt-ole-db.md)|<span data-ttu-id="8cd60-128">從格式檔案中讀取每個資料行的格式資訊。</span><span class="sxs-lookup"><span data-stu-id="8cd60-128">Reads format information for each column from the format file.</span></span>|  
|[<span data-ttu-id="8cd60-129">IBCPSession::BCPWriteFmt &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd60-129">IBCPSession::BCPWriteFmt &#40;OLE DB&#41;</span></span>](ibcpsession-bcpwritefmt-ole-db.md)|<span data-ttu-id="8cd60-130">將每個資料行的格式資訊寫入格式檔案。</span><span class="sxs-lookup"><span data-stu-id="8cd60-130">Writes format information for each column to the format file.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8cd60-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cd60-131">See Also</span></span>  
 [<span data-ttu-id="8cd60-132">介面 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd60-132">Interfaces &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
