---
title: 資料表值參數 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, table-valued parameters
- table-valued parameters (OLE DB)
ms.assetid: 4298b73d-615b-4d28-9843-03b4d5fc489e
author: rothja
ms.author: jroth
ms.openlocfilehash: 41d125bcb254125d7f7562ca1873e8af03dab929
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706410"
---
# <a name="table-valued-parameters-ole-db"></a><span data-ttu-id="d0a5d-102">資料表值參數 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="d0a5d-102">Table-Valued Parameters (OLE DB)</span></span>
  <span data-ttu-id="d0a5d-103">本章節描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者對資料表值參數的支援。</span><span class="sxs-lookup"><span data-stu-id="d0a5d-103">This section describes support for table-valued parameters in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider.</span></span> <span data-ttu-id="d0a5d-104">如需其他總覽資訊，請參閱[資料表值參數 &#40;SQL Server Native Client&#41;](../native-client/features/table-valued-parameters-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="d0a5d-104">For additional overview information, see [Table-Valued Parameters &#40;SQL Server Native Client&#41;](../native-client/features/table-valued-parameters-sql-server-native-client.md).</span></span> <span data-ttu-id="d0a5d-105">如需範例，請參閱[使用資料表值參數 &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="d0a5d-105">For a sample, see [Use Table-Valued Parameters &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0a5d-106">備註</span><span class="sxs-lookup"><span data-stu-id="d0a5d-106">Remarks</span></span>  
 <span data-ttu-id="d0a5d-107">目前可以藉由參數集將多個資料列當做程序的參數傳送給伺服器 (`ICommand::Execute` 中的 DBPARAMS 參數)。</span><span class="sxs-lookup"><span data-stu-id="d0a5d-107">Currently, you can send multirow data to the server as parameters to a procedure with parameter sets (the DBPARAMS parameter in `ICommand::Execute`).</span></span> <span data-ttu-id="d0a5d-108">使用參數集時，該集合中的每個元素都必須以對伺服器的個別遠端程序呼叫 (RPC) 要求來進行傳送。</span><span class="sxs-lookup"><span data-stu-id="d0a5d-108">With parameter sets, every element of the set has to be sent in a separate remote procedure call (RPC) request to the server.</span></span> <span data-ttu-id="d0a5d-109">資料表值參數提供類似的功能，但能與伺服器更緊密地整合。</span><span class="sxs-lookup"><span data-stu-id="d0a5d-109">Table-valued parameters provide similar functionality, but there is better integration with the server.</span></span> <span data-ttu-id="d0a5d-110">如此可以減少 RPC 要求數目，並以集合為基礎在伺服器上進行作業。</span><span class="sxs-lookup"><span data-stu-id="d0a5d-110">This reduces the number of RPC requests and enables set-based operations on the server.</span></span>  
  
 <span data-ttu-id="d0a5d-111">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者中，是以 OLE DB `Rowset` 物件的形式支援資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="d0a5d-111">Table-value parameters are supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider as OLE DB `Rowset` objects.</span></span> <span data-ttu-id="d0a5d-112">任何 `Rowset` 物件都可以藉由取用者 (也就是使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者的用戶端應用程式)，以資料表值參數的參數預留位置來提供。</span><span class="sxs-lookup"><span data-stu-id="d0a5d-112">Any `Rowset` object could be provided by the consumer (that is, the client application using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider) as a placeholder for table-valued parameter parameters.</span></span> <span data-ttu-id="d0a5d-113">資料表值參數會被視為類似於其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 參數類型。</span><span class="sxs-lookup"><span data-stu-id="d0a5d-113">Table-valued parameters are treated like other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] parameter types.</span></span> <span data-ttu-id="d0a5d-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者能提供建立、探索、規格、繫結和結構描述介面。</span><span class="sxs-lookup"><span data-stu-id="d0a5d-114">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider provides creation, discovery, specification, binding and schema interfaces.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0a5d-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="d0a5d-115">In This Section</span></span>  
  
-   [<span data-ttu-id="d0a5d-116">建立資料表值參數資料列集</span><span class="sxs-lookup"><span data-stu-id="d0a5d-116">Table-Valued Parameter Rowset Creation</span></span>](table-valued-parameter-rowset-creation.md)  
  
-   [<span data-ttu-id="d0a5d-117">資料表值參數類型探索</span><span class="sxs-lookup"><span data-stu-id="d0a5d-117">Table-Valued Parameter Type Discovery</span></span>](../../database-engine/dev-guide/table-valued-parameter-type-discovery.md)  
  
-   [<span data-ttu-id="d0a5d-118">執行包含資料表值參數的命令</span><span class="sxs-lookup"><span data-stu-id="d0a5d-118">Executing Commands Containing Table-Valued Parameters</span></span>](executing-commands-containing-table-valued-parameters.md)  
  
-   [<span data-ttu-id="d0a5d-119">將資料插入至資料表值參數</span><span class="sxs-lookup"><span data-stu-id="d0a5d-119">Inserting Data into Table-Valued Parameters</span></span>](inserting-data-into-table-valued-parameters.md)  
  
-   [<span data-ttu-id="d0a5d-120">針對 OLE DB 資料表值參數變更的架構資料列集</span><span class="sxs-lookup"><span data-stu-id="d0a5d-120">Schema Rowsets Changed for OLE DB Table-Valued Parameters</span></span>](schema-rowsets-changed-for-ole-db-table-valued-parameters.md)  
  
-   [<span data-ttu-id="d0a5d-121">OLE DB 資料表值參數類型支援</span><span class="sxs-lookup"><span data-stu-id="d0a5d-121">OLE DB Table-Valued Parameter Type Support</span></span>](ole-db-table-valued-parameter-type-support.md)  
  
-   [<span data-ttu-id="d0a5d-122">OLE DB 資料表值參數類型支援 &#40;方法&#41;</span><span class="sxs-lookup"><span data-stu-id="d0a5d-122">OLE DB Table-Valued Parameter Type Support &#40;Methods&#41;</span></span>](ole-db-table-valued-parameter-type-support-methods.md)  
  
-   [<span data-ttu-id="d0a5d-123">OLE DB 資料表值參數類型支援 &#40;屬性&#41;</span><span class="sxs-lookup"><span data-stu-id="d0a5d-123">OLE DB Table-Valued Parameter Type Support &#40;Properties&#41;</span></span>](ole-db-table-valued-parameter-type-support-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="d0a5d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0a5d-124">See Also</span></span>  
 <span data-ttu-id="d0a5d-125">[SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="d0a5d-125">[SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md) </span></span>  
 [<span data-ttu-id="d0a5d-126">使用資料表值參數 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="d0a5d-126">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
