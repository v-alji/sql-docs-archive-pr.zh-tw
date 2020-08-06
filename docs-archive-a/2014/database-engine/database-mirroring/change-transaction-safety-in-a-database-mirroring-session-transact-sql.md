---
title: 變更資料庫鏡像工作階段中的交易安全性 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- transaction safety [SQL Server database mirroring]
ms.assetid: 8b03bb82-8589-4558-8545-9942fe008391
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d8bc9d0fb639770d33507c29a6ec67f60bd0434a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593584"
---
# <a name="change-transaction-safety-in-a-database-mirroring-session-transact-sql"></a><span data-ttu-id="0b5da-102">變更資料庫鏡像工作階段中的異動安全性 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0b5da-102">Change Transaction Safety in a Database Mirroring Session (Transact-SQL)</span></span>
  <span data-ttu-id="0b5da-103">交易安全性是控制工作階段作業模式的屬性。</span><span class="sxs-lookup"><span data-stu-id="0b5da-103">Transaction safety is the attribute that controls the operating mode of the session.</span></span> <span data-ttu-id="0b5da-104">不過，資料庫擁有者可隨時變更交易安全性。</span><span class="sxs-lookup"><span data-stu-id="0b5da-104">At any time, however, the database owner can change the transaction safety.</span></span> <span data-ttu-id="0b5da-105">依預設，交易安全性的等級會設定為 FULL (同步作業模式)。</span><span class="sxs-lookup"><span data-stu-id="0b5da-105">By default, the level of transaction safety is set to FULL (synchronous operating mode).</span></span>  
  
 <span data-ttu-id="0b5da-106">關閉交易安全性會將工作階段轉換為非同步作業模式，可達到最大效能。</span><span class="sxs-lookup"><span data-stu-id="0b5da-106">Turning off transaction safety shifts the session into asynchronous operating mode, which maximizes performance.</span></span> <span data-ttu-id="0b5da-107">如果主體無法使用，鏡像就會停止，但可以當做暖待命伺服器使用 (容錯移轉需要強制服務，且可能遺失資料)。</span><span class="sxs-lookup"><span data-stu-id="0b5da-107">If the principal becomes unavailable, the mirror stops but is available as a warm standby (failover requires forcing service with possible data loss).</span></span>  
  
### <a name="to-turn-on-transaction-safety"></a><span data-ttu-id="0b5da-108">若要開啟交易安全性</span><span class="sxs-lookup"><span data-stu-id="0b5da-108">To turn on transaction safety</span></span>  
  
1.  <span data-ttu-id="0b5da-109">連接到主體伺服器。</span><span class="sxs-lookup"><span data-stu-id="0b5da-109">Connect to the principal server.</span></span>  
  
2.  <span data-ttu-id="0b5da-110">發出下列 Transact-SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="0b5da-110">Issue the following Transact-SQL statement:</span></span>  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY FULL  
    ```  
  
     <span data-ttu-id="0b5da-111">其中 *\<database>* 是鏡像資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="0b5da-111">where *\<database>* is the name of the mirrored database.</span></span>  
  
### <a name="to-turn-off-transaction-safety"></a><span data-ttu-id="0b5da-112">關閉交易安全性</span><span class="sxs-lookup"><span data-stu-id="0b5da-112">To turn off transaction safety</span></span>  
  
1.  <span data-ttu-id="0b5da-113">連接到主體伺服器。</span><span class="sxs-lookup"><span data-stu-id="0b5da-113">Connect to the principal server.</span></span>  
  
2.  <span data-ttu-id="0b5da-114">發出下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="0b5da-114">Issue the following statement:</span></span>  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY OFF  
    ```  
  
     <span data-ttu-id="0b5da-115">其中 *\<database>* 是鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="0b5da-115">where *\<database>* is the mirrored database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b5da-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b5da-116">See Also</span></span>  
 <span data-ttu-id="0b5da-117">[ALTER DATABASE 資料庫鏡像 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="0b5da-117">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 [<span data-ttu-id="0b5da-118">Database Mirroring Operating Modes</span><span class="sxs-lookup"><span data-stu-id="0b5da-118">Database Mirroring Operating Modes</span></span>](database-mirroring-operating-modes.md)  
  
  
