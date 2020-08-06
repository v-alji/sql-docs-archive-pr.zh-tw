---
title: ISSAsynchStatus (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSAsynchStatus interface
ms.assetid: c643f09f-9ccc-4d8b-9243-3cde86c2bd46
author: rothja
ms.author: jroth
ms.openlocfilehash: 4489f9d1ad576d49d885842f6969f9b61065791c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594042"
---
# <a name="issasynchstatus-ole-db"></a><span data-ttu-id="38ba2-102">ISSAsynchStatus (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="38ba2-102">ISSAsynchStatus (OLE DB)</span></span>
  <span data-ttu-id="38ba2-103">**ISSAsynchStatus**會公開對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 非同步作業的支援。</span><span class="sxs-lookup"><span data-stu-id="38ba2-103">**ISSAsynchStatus** exposes support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] asynchronous operations.</span></span> <span data-ttu-id="38ba2-104">這是選擇性的介面，繼承自核心 OLE DB 介面**IDBAsynchStatus**。</span><span class="sxs-lookup"><span data-stu-id="38ba2-104">This is an optional interface that inherits from the core OLE DB interface **IDBAsynchStatus**.</span></span> <span data-ttu-id="38ba2-105">除了繼承自 **IDBAsynchStatus** 的 **Abort** 和 **GetStatus** 方法之外，**ISSAsynchStatus** 還提供一個新方法，用來等到非同步作業完成或發生逾時。</span><span class="sxs-lookup"><span data-stu-id="38ba2-105">In addition to the **Abort** and **GetStatus** methods inherited from **IDBAsynchStatus**, **ISSAsynchStatus** provides one new method that is used to wait until an asynchronous operation has completed or a time-out occurs.</span></span>  
  
|<span data-ttu-id="38ba2-106">方法</span><span class="sxs-lookup"><span data-stu-id="38ba2-106">Method</span></span>|<span data-ttu-id="38ba2-107">描述</span><span class="sxs-lookup"><span data-stu-id="38ba2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="38ba2-108">ISSAsynchStatus::Abort &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="38ba2-108">ISSAsynchStatus::Abort &#40;OLE DB&#41;</span></span>](issasynchstatus-abort-ole-db.md)|<span data-ttu-id="38ba2-109">取消非同步執行的作業。</span><span class="sxs-lookup"><span data-stu-id="38ba2-109">Cancels an asynchronously executing operation.</span></span>|  
|[<span data-ttu-id="38ba2-110">ISSAsynchStatus::GetStatus &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="38ba2-110">ISSAsynchStatus::GetStatus &#40;OLE DB&#41;</span></span>](issasynchstatus-getstatus-ole-db.md)|<span data-ttu-id="38ba2-111">傳回以非同步方式執行作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="38ba2-111">Returns the status of an asynchronously executing operation.</span></span>|  
|[<span data-ttu-id="38ba2-112">ISSAsynchStatus::WaitForAsynchCompletion &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="38ba2-112">ISSAsynchStatus::WaitForAsynchCompletion &#40;OLE DB&#41;</span></span>](issasynchstatus-waitforasynchcompletion-ole-db.md)|<span data-ttu-id="38ba2-113">等到非同步執行的作業完成或發生逾時為止。</span><span class="sxs-lookup"><span data-stu-id="38ba2-113">Waits until the asynchronously executing operation is complete or a time-out occurs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38ba2-114">備註</span><span class="sxs-lookup"><span data-stu-id="38ba2-114">Remarks</span></span>  
 <span data-ttu-id="38ba2-115">**ISSAsynchStatus::GetStatus** 方法的 **ISSAsynchStatus** 實作與 **IDBAsynchStatus::GetStatus** 方法相同，不同的是如果中止資料來源物件的初始化，便會傳回 E_UNEXPECTED，而不是 DB_E_CANCELED (雖然 **ISSAsynchStatus::WaitForAsynchCompletion** 會傳回 DB_E_CANCELED)。</span><span class="sxs-lookup"><span data-stu-id="38ba2-115">The **ISSAsynchStatus** implementation of the **ISSAsynchStatus::GetStatus** method is the same as the **IDBAsynchStatus::GetStatus** method except that if the initialization of a data source object is aborted, E_UNEXPECTED is returned rather than DB_E_CANCELED (although **ISSAsynchStatus::WaitForAsynchCompletion** returns DB_E_CANCELED).</span></span> <span data-ttu-id="38ba2-116">這是因為資料來源物件在中止作業後不會保留在一般的狀態，如此可以讓系統嘗試進一步的初始化作業。</span><span class="sxs-lookup"><span data-stu-id="38ba2-116">This is because the data source object is not left in the usual state following an abort operation, so that further initialization operations may be attempted.</span></span>  
  
 <span data-ttu-id="38ba2-117">下列方法支援在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中使用非同步執行：</span><span class="sxs-lookup"><span data-stu-id="38ba2-117">The following methods support the use of asynchronous execution in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="38ba2-118">**ICommand::Execute**</span><span class="sxs-lookup"><span data-stu-id="38ba2-118">**ICommand::Execute**</span></span>  
  
-   <span data-ttu-id="38ba2-119">**IOpenRowset::OpenRowset**</span><span class="sxs-lookup"><span data-stu-id="38ba2-119">**IOpenRowset::OpenRowset**</span></span>  
  
-   <span data-ttu-id="38ba2-120">**IMultipleResults::GetResult**</span><span class="sxs-lookup"><span data-stu-id="38ba2-120">**IMultipleResults::GetResult**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ba2-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38ba2-121">See Also</span></span>  
 <span data-ttu-id="38ba2-122">[介面 &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="38ba2-122">[Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span></span>  
 [<span data-ttu-id="38ba2-123">執行非同步作業</span><span class="sxs-lookup"><span data-stu-id="38ba2-123">Performing Asynchronous Operations</span></span>](../native-client/features/performing-asynchronous-operations.md)  
  
  
