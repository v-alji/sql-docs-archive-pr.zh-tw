---
title: ISSAbort (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISSAbort interface
ms.assetid: 7c4df482-4a83-4da0-802b-3637b507693a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7195311fefe3f0f1b7b4d6d789aa8d8487bc3bfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709846"
---
# <a name="issabort-ole-db"></a><span data-ttu-id="5131b-102">ISSAbort (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="5131b-102">ISSAbort (OLE DB)</span></span>
  <span data-ttu-id="5131b-103">**ISSAbort**介面（在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者中公開）提供了[ISSAbort：： Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)方法，可用於取消目前的資料列集，加上使用命令批次處理的任何命令，這是一開始產生資料列集，而且尚未完成執行。</span><span class="sxs-lookup"><span data-stu-id="5131b-103">The **ISSAbort** interface, which is exposed in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, provides the [ISSAbort::Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) method that is used to cancel the current rowset plus any commands batched with the command that initially generated the rowset, and that have not yet completed execution.</span></span>  
  
 <span data-ttu-id="5131b-104">**ISSAbort**是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 原生用戶端提供者特定的介面，可在**ICommand：： Execute**或**IOpenRowset：： OpenRowset**所傳回的**IMultipleResults**物件上使用**QueryInterface** 。</span><span class="sxs-lookup"><span data-stu-id="5131b-104">**ISSAbort** is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client provider-specific interface available by using **QueryInterface** on the **IMultipleResults** object returned by **ICommand::Execute** or **IOpenRowset::OpenRowset**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5131b-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="5131b-105">In This Section</span></span>  
  
|<span data-ttu-id="5131b-106">方法</span><span class="sxs-lookup"><span data-stu-id="5131b-106">Method</span></span>|<span data-ttu-id="5131b-107">描述</span><span class="sxs-lookup"><span data-stu-id="5131b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5131b-108">ISSAbort：： Abort &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="5131b-108">ISSAbort::Abort &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)|<span data-ttu-id="5131b-109">取消目前的資料列集加上與目前命令相關聯之任何批次處理的命令。</span><span class="sxs-lookup"><span data-stu-id="5131b-109">Cancels the current rowset plus any batched commands associated with the current command.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5131b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5131b-110">See Also</span></span>  
 [<span data-ttu-id="5131b-111">介面 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="5131b-111">Interfaces &#40;OLE DB&#41;</span></span>](../../../2014/database-engine/dev-guide/interfaces-ole-db.md)  
  
  
