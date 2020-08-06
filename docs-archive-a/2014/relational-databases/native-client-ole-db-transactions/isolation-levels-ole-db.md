---
title: 隔離等級 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
author: rothja
ms.author: jroth
ms.openlocfilehash: c7f6cbff4e68eaedd3e78a82cddd872ba5f8f19e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597081"
---
# <a name="isolation-levels-ole-db"></a><span data-ttu-id="f5d0f-102">隔離等級 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="f5d0f-102">Isolation Levels (OLE DB)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f5d0f-103">用戶端可以控制連線的交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="f5d0f-103">clients can control transaction-isolation levels for a connection.</span></span> <span data-ttu-id="f5d0f-104">若要控制交易隔離等級， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者取用者會使用：</span><span class="sxs-lookup"><span data-stu-id="f5d0f-104">To control transaction-isolation level, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer uses:</span></span>  
  
-   <span data-ttu-id="f5d0f-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者預設自動認可模式的 DBPROPSET_SESSION 屬性 DBPROP_SESS_AUTOCOMMITISOLEVELS。</span><span class="sxs-lookup"><span data-stu-id="f5d0f-105">DBPROPSET_SESSION property DBPROP_SESS_AUTOCOMMITISOLEVELS for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider default autocommit mode.</span></span>  
  
     <span data-ttu-id="f5d0f-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]層級的 Native Client OLE DB 提供者預設值為 DBPROPVAL_TI_READCOMMITTED。</span><span class="sxs-lookup"><span data-stu-id="f5d0f-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider default for the level is DBPROPVAL_TI_READCOMMITTED.</span></span>  
  
-   <span data-ttu-id="f5d0f-107">適用於本機手動認可交易之 **ITransactionLocal::StartTransaction** 方法的 *isoLevel* 參數。</span><span class="sxs-lookup"><span data-stu-id="f5d0f-107">The *isoLevel* parameter of the **ITransactionLocal::StartTransaction** method for local manual-commit transactions.</span></span>  
  
-   <span data-ttu-id="f5d0f-108">適用於 MS DTC 協調分散式交易之 **ITransactionDispenser::BeginTransaction** 方法的 *isoLevel* 參數。</span><span class="sxs-lookup"><span data-stu-id="f5d0f-108">The *isoLevel* parameter of the **ITransactionDispenser::BeginTransaction** method for MS DTC-coordinated distributed transactions.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f5d0f-109">允許中途讀取隔離等級的唯讀存取。</span><span class="sxs-lookup"><span data-stu-id="f5d0f-109">allows read-only access at the dirty read isolation level.</span></span> <span data-ttu-id="f5d0f-110">其他所有等級藉由將鎖定套用至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件以限制並行存取。</span><span class="sxs-lookup"><span data-stu-id="f5d0f-110">All other levels restrict concurrency by applying locks to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects.</span></span> <span data-ttu-id="f5d0f-111">由於用戶端需要更高的並行存取等級，因此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會對資料並行存取套用更大的限制。</span><span class="sxs-lookup"><span data-stu-id="f5d0f-111">As the client requires greater concurrency levels, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applies greater restrictions on concurrent access to data.</span></span> <span data-ttu-id="f5d0f-112">為了維持最高層級的資料平行存取， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者取用者應該以智慧方式控制它對特定並行層級的要求。</span><span class="sxs-lookup"><span data-stu-id="f5d0f-112">To maintain the highest level of concurrent access to data, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer should intelligently control its requests for specific concurrency levels.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="f5d0f-113">引入了快照集隔離等級。</span><span class="sxs-lookup"><span data-stu-id="f5d0f-113">introduced snapshot isolation level.</span></span> <span data-ttu-id="f5d0f-114">如需詳細資訊，請參閱[使用快照隔離](../native-client/features/working-with-snapshot-isolation.md)。</span><span class="sxs-lookup"><span data-stu-id="f5d0f-114">For more information, see [Working with Snapshot Isolation](../native-client/features/working-with-snapshot-isolation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5d0f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5d0f-115">See Also</span></span>  
 [<span data-ttu-id="f5d0f-116">交易</span><span class="sxs-lookup"><span data-stu-id="f5d0f-116">Transactions</span></span>](transactions.md)  
  
  
