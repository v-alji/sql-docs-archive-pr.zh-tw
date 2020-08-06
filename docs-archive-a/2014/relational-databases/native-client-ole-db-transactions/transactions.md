---
title: 交易 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
author: rothja
ms.author: jroth
ms.openlocfilehash: 1067820e80f9c7a4e1af2c8a14c85bc9dbfdd6aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598824"
---
# <a name="transactions"></a><span data-ttu-id="4c9cc-102">異動</span><span class="sxs-lookup"><span data-stu-id="4c9cc-102">Transactions</span></span>
  <span data-ttu-id="4c9cc-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會實行本機交易支援。</span><span class="sxs-lookup"><span data-stu-id="4c9cc-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements local transaction support.</span></span> <span data-ttu-id="4c9cc-104">取用者可以使用 Microsoft 分散式交易協調器 (MS DTC) 來使用分散式或協調的交易。</span><span class="sxs-lookup"><span data-stu-id="4c9cc-104">The consumer can use distributed or coordinated transactions by using Microsoft Distributed Transaction Coordinator (MS DTC).</span></span> <span data-ttu-id="4c9cc-105">若取用者需要跨多個會話的交易控制， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者可以聯結由 MS DTC 所起始和維護的交易。</span><span class="sxs-lookup"><span data-stu-id="4c9cc-105">For consumers requiring transaction control that spans multiple sessions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can join transactions initiated and maintained by MS DTC.</span></span>  
  
 <span data-ttu-id="4c9cc-106">根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會使用自動認可交易模式，其中取用者會話上的每個離散動作都是針對實例所組成的完整交易 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4c9cc-106">By default, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider uses an autocommit transaction mode, where each discrete action on a consumer session comprises a complete transaction against an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4c9cc-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者自動認可模式為本機，而自動認可交易絕不會跨越一個以上的會話。</span><span class="sxs-lookup"><span data-stu-id="4c9cc-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider autocommit mode is local, and autocommit transactions never span more than a single session.</span></span>  
  
 <span data-ttu-id="4c9cc-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會公開**ITransactionLocal**介面，讓取用者在實例的單一連接上，明確地使用並隱含啟動交易 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4c9cc-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ITransactionLocal** interface, allowing the consumer to use explicitly and implicitly start transactions on a single connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4c9cc-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者不支援嵌套的本機交易。</span><span class="sxs-lookup"><span data-stu-id="4c9cc-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support nested local transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c9cc-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="4c9cc-110">In This Section</span></span>  
  
-   [<span data-ttu-id="4c9cc-111">支援本機交易</span><span class="sxs-lookup"><span data-stu-id="4c9cc-111">Supporting Local Transactions</span></span>](supporting-local-transactions.md)  
  
-   [<span data-ttu-id="4c9cc-112">支援分散式交易</span><span class="sxs-lookup"><span data-stu-id="4c9cc-112">Supporting Distributed Transactions</span></span>](supporting-distributed-transactions.md)  
  
-   [<span data-ttu-id="4c9cc-113">隔離等級 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="4c9cc-113">Isolation Levels &#40;OLE DB&#41;</span></span>](isolation-levels-ole-db.md)  
  
## <a name="see-also"></a><span data-ttu-id="4c9cc-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c9cc-114">See Also</span></span>  
 [<span data-ttu-id="4c9cc-115">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="4c9cc-115">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
