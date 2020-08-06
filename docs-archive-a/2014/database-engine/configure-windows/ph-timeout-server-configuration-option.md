---
title: PH 逾時伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- time limit for protocol handler wait [SQL Server]
- timeout options [SQL Server], ph timeout option
- protocols [SQL Server], timing out
- ph timeout option
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 515ed74a4b92259d53770bf6d970626eba686453
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688201"
---
# <a name="ph-timeout-server-configuration-option"></a><span data-ttu-id="639fd-102">PH 逾時伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="639fd-102">PH timeout Server Configuration Option</span></span>
  <span data-ttu-id="639fd-103">使用 PH 逾時選項來指定全文檢索通訊協定處理常式在資料庫連接逾時之前，需先等候的時間 (以秒為單位)。預設值為 60 秒。</span><span class="sxs-lookup"><span data-stu-id="639fd-103">Use the PH timeout option to specify the time, in seconds, that the full-text protocol handler should wait to connect to a database before timing out. The default value is 60 seconds.</span></span> <span data-ttu-id="639fd-104">若連接嘗試因為暫時性的網路問題而逾時，請增加 ph timeout 值。</span><span class="sxs-lookup"><span data-stu-id="639fd-104">Increase the ph timeout value when connection attempts are timing out due to temporary network issues.</span></span>  
  
 <span data-ttu-id="639fd-105">全文檢索通訊協定處理常式是由篩選背景程式主機所控管，而且可用來從 SQL Server 提取要編製全文檢索索引的資料。</span><span class="sxs-lookup"><span data-stu-id="639fd-105">The full-text protocol handler is hosted in the filter daemon host and is used to fetch from SQL Server the data to be full-text indexed.</span></span> <span data-ttu-id="639fd-106">如需有關全文檢索搜尋元件的詳細資訊，請參閱 [全文檢索搜尋](../../relational-databases/search/full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="639fd-106">For more information about full-text search components, see [Full-Text Search](../../relational-databases/search/full-text-search.md).</span></span>  
  
 <span data-ttu-id="639fd-107">嘗試提取資料列時，若通訊協定處理常式無法在指定的時間內連接到 SQL Server，則會報告該資料列逾時錯誤。</span><span class="sxs-lookup"><span data-stu-id="639fd-107">When attempting to fetch a data row, if the protocol handler cannot connect to SQL Server within the specified time, it reports a time-out error for that row.</span></span> <span data-ttu-id="639fd-108">全文檢索收集程式會稍後會嘗試重新提取該資料列。</span><span class="sxs-lookup"><span data-stu-id="639fd-108">The full-text gatherer will retry the row later.</span></span> <span data-ttu-id="639fd-109">如需有關全文檢索收集程式的詳細資訊，請參閱 [擴展全文檢索索引](../../relational-databases/indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="639fd-109">For more information about the full-text gatherer, see [Populate Full-Text Indexes](../../relational-databases/indexes/indexes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="639fd-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="639fd-110">See Also</span></span>  
 <span data-ttu-id="639fd-111">[全文檢索搜尋](../../relational-databases/search/full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="639fd-111">[Full-Text Search](../../relational-databases/search/full-text-search.md) </span></span>  
 <span data-ttu-id="639fd-112">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="639fd-112">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="639fd-113">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="639fd-113">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="639fd-114">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="639fd-114">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
