---
title: 索引作業的交易記錄磁碟空間 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index disk space [SQL Server]
- space [SQL Server], indexes
- transaction logs [SQL Server], disk space
- disk space [SQL Server], transaction logs
- space [SQL Server], transaction logs
ms.assetid: 4f8a4922-4507-4072-be67-c690528d5c3b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c34c9ff7a9494496d6c60d5920184c0ce86131d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707518"
---
# <a name="transaction-log-disk-space-for-index-operations"></a><span data-ttu-id="3904b-102">索引作業的交易記錄磁碟空間</span><span class="sxs-lookup"><span data-stu-id="3904b-102">Transaction Log Disk Space for Index Operations</span></span>
  <span data-ttu-id="3904b-103">大規模的索引作業會產生大量資料載入，而造成交易記錄檔迅速填滿。</span><span class="sxs-lookup"><span data-stu-id="3904b-103">Large-scale index operations can generate large data loads that can cause the transaction log to fill quickly.</span></span> <span data-ttu-id="3904b-104">為了確保索引作業可以回復，在索引作業完成之前，交易記錄檔不得遭到截斷；不過，在索引作業期間可以備份記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3904b-104">To make sure that the index operation can be rolled back, the transaction log cannot be truncated until the index operation has completed; however, the log can be backed up during the index operation.</span></span> <span data-ttu-id="3904b-105">因此，交易記錄檔必須有足夠空間來儲存索引作業交易，以及索引作業期間的任何並行使用者交易。</span><span class="sxs-lookup"><span data-stu-id="3904b-105">Therefore, the transaction log must have sufficient room to store both the index operation transactions and any concurrent user transactions for the duration of the index operation.</span></span> <span data-ttu-id="3904b-106">不管是離線或線上索引作業都是如此。</span><span class="sxs-lookup"><span data-stu-id="3904b-106">This is true for both offline and online index operations.</span></span> <span data-ttu-id="3904b-107">因為在離線索引作業期間無法存取基礎資料表，所以使用者交易不多，記錄檔應該不會成長太快。</span><span class="sxs-lookup"><span data-stu-id="3904b-107">Because the underlying tables cannot be accessed during an offline index operation, there may be few user transactions and the log may not grow as quickly.</span></span> <span data-ttu-id="3904b-108">線上索引作業並不禁止並行使用者活動，因此大規模的線上索引作業若再結合大量的並行使用者交易，會造成交易記錄檔持續成長，同時又無法截斷記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3904b-108">Online index operations do not prevent concurrent user activity, therefore, large-scale online index operations combined with significant concurrent user transactions can cause continuous growth of the transaction log without an option to truncate the log.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="3904b-109">建議</span><span class="sxs-lookup"><span data-stu-id="3904b-109">Recommendations</span></span>  
 <span data-ttu-id="3904b-110">當您執行大規模的索引作業時，請考慮下列建議：</span><span class="sxs-lookup"><span data-stu-id="3904b-110">When you run large-scale index operations, consider the following recommendations:</span></span>  
  
1.  <span data-ttu-id="3904b-111">確定在執行線上大規模索引作業之前已備份及截斷交易記錄檔，且記錄檔有足夠空間可儲存預計的索引和使用者交易。</span><span class="sxs-lookup"><span data-stu-id="3904b-111">Make sure the transaction log has been backed up and truncated before running large-scale index operations online, and that the log has sufficient space to store the projected index and user transactions.</span></span>  
  
2.  <span data-ttu-id="3904b-112">針對索引作業，請考慮將 SORT_IN_TEMPDB 選項設為 ON。</span><span class="sxs-lookup"><span data-stu-id="3904b-112">Consider setting the SORT_IN_TEMPDB option to ON for the index operation.</span></span> <span data-ttu-id="3904b-113">這樣可將索引交易與並行使用者交易區分開來。</span><span class="sxs-lookup"><span data-stu-id="3904b-113">This separates the index transactions from the concurrent user transactions.</span></span> <span data-ttu-id="3904b-114">索引交易將儲存在 **tempdb** 交易記錄檔中，並行使用者交易則儲存在使用者資料庫的交易記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="3904b-114">The index transactions will be stored in the **tempdb** transaction log, and the concurrent user transactions will be stored in the transaction log of the user database.</span></span> <span data-ttu-id="3904b-115">這樣可在索引作業期間，讓使用者資料庫的交易記錄檔進行截斷 (如果有此需要的話)。</span><span class="sxs-lookup"><span data-stu-id="3904b-115">This allows for the transaction log of the user database to be truncated during the index operation if it is required.</span></span> <span data-ttu-id="3904b-116">另外，如果 **tempdb** 記錄檔與使用者資料庫記錄檔不在同一個磁碟上，這兩個記錄檔就不會競爭相同的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="3904b-116">Additionally, if the **tempdb** log is not on the same disk as the user database log, the two logs are not competing for the same disk space.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3904b-117">確認 **tempdb** 資料庫和交易記錄檔有足夠的磁碟空間可處理索引作業。</span><span class="sxs-lookup"><span data-stu-id="3904b-117">Verify that the **tempdb** database and transaction log have sufficient disk space to handle the index operation.</span></span> <span data-ttu-id="3904b-118">要等到索引作業完成之後，才能截斷 **tempdb** 交易記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3904b-118">The **tempdb** transaction log cannot be truncated until the index operation is completed.</span></span>  
  
3.  <span data-ttu-id="3904b-119">使用資料庫復原模式，可使索引作業的記錄量減至最少。</span><span class="sxs-lookup"><span data-stu-id="3904b-119">Use a database recovery model that allows for minimal logging of the index operation.</span></span> <span data-ttu-id="3904b-120">這樣會減少記錄檔大小，防止記錄填滿記錄檔空間。</span><span class="sxs-lookup"><span data-stu-id="3904b-120">This may reduce the size of the log and prevent the log from filling the log space.</span></span>  
  
4.  <span data-ttu-id="3904b-121">不要在外顯交易中執行線上索引作業。</span><span class="sxs-lookup"><span data-stu-id="3904b-121">Do not run the online index operation in an explicit transaction.</span></span> <span data-ttu-id="3904b-122">這樣需等到外顯交易結束之後，才能截斷記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3904b-122">The log will not be truncated until the explicit transaction ends.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="3904b-123">相關內容</span><span class="sxs-lookup"><span data-stu-id="3904b-123">Related Content</span></span>  
 [<span data-ttu-id="3904b-124">Disk Space Requirements for Index DDL Operations</span><span class="sxs-lookup"><span data-stu-id="3904b-124">Disk Space Requirements for Index DDL Operations</span></span>](disk-space-requirements-for-index-ddl-operations.md)  
  
 [<span data-ttu-id="3904b-125">索引磁碟空間範例</span><span class="sxs-lookup"><span data-stu-id="3904b-125">Index Disk Space Example</span></span>](index-disk-space-example.md)  
  
  
