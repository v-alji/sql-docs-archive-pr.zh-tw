---
title: 交易存留期 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8c00050ee323cade7493d44c4c296ba4ce6811e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709654"
---
# <a name="transaction-lifetimes"></a><span data-ttu-id="da598-102">交易存留期間</span><span class="sxs-lookup"><span data-stu-id="da598-102">Transaction Lifetimes</span></span>
  <span data-ttu-id="da598-103">利用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序啟動的交易以及利用 Managed 程式碼啟動的交易間有一個重要的差異：Common Language Runtime (CLR) 程式碼無法在進入或離開 CLR 引動過程時讓交易狀態不平衡。</span><span class="sxs-lookup"><span data-stu-id="da598-103">There is an important difference between transactions started in [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures and those started in managed code: common language runtime (CLR) code cannot unbalance the transaction state on entry or exit of a CLR invocation.</span></span> <span data-ttu-id="da598-104">請注意此差異的下列含意：</span><span class="sxs-lookup"><span data-stu-id="da598-104">Be aware of the following implications of this difference:</span></span>  
  
-   <span data-ttu-id="da598-105">在 CLR 框架內部啟動的交易必須認可或回復，否則 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在離開框架時會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="da598-105">A transaction started inside a CLR frame must be committed or rolled back, or else [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generates an error when the frame is exited.</span></span>  
  
-   <span data-ttu-id="da598-106">外部交易無法在 CLR 程式碼內部認可或回復。</span><span class="sxs-lookup"><span data-stu-id="da598-106">An outer transaction cannot be committed or rolled back inside the CLR code.</span></span>  
  
-   <span data-ttu-id="da598-107">嘗試認可未在相同程序中啟動的交易時，會造成執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="da598-107">An attempt to commit a transaction not started in the same procedure causes a run-time error.</span></span>  
  
-   <span data-ttu-id="da598-108">嘗試回復不是在相同程式中啟動的交易，會導致交易停止回應 (防止任何其他副作用的作業) 發生。</span><span class="sxs-lookup"><span data-stu-id="da598-108">An attempt to roll back a transaction not started in the same procedure causes the transaction to stop responding (preventing any other side-effecting operation from happening).</span></span> <span data-ttu-id="da598-109">交易會停止，直到 CLR 程式碼超出範圍為止。</span><span class="sxs-lookup"><span data-stu-id="da598-109">The transaction discontinues until the CLR code goes out of scope.</span></span> <span data-ttu-id="da598-110">請注意，當您在程序內部偵測到錯誤，而且想要確認整個交易結束時，這可能相當實用。</span><span class="sxs-lookup"><span data-stu-id="da598-110">Note that this can be useful when you detect an error inside your procedure and want to make sure the whole transaction terminates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da598-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da598-111">See Also</span></span>  
 [<span data-ttu-id="da598-112">CLR 整合和交易</span><span class="sxs-lookup"><span data-stu-id="da598-112">CLR Integration and Transactions</span></span>](../native-client-ole-db-transactions/transactions.md)  
  
  
