---
title: 全文檢索編目頻寬伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- large memory buffers
- memory [SQL Server], buffers
- ft crawl bandwidth option
ms.assetid: e5864ad9-92f5-43b5-95de-46d68ded8694
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 33821ff1fdbc4248c71906d8307a8164a7f64d24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708598"
---
# <a name="ft-crawl-bandwidth-server-configuration-option"></a><span data-ttu-id="8140d-102">全文檢索耙梳頻寬伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="8140d-102">ft crawl bandwidth Server Configuration Option</span></span>
  <span data-ttu-id="8140d-103">使用 **ft crawl bandwidth** 選項，可指定大型記憶體緩衝區的集區可以成長到多大的大小。</span><span class="sxs-lookup"><span data-stu-id="8140d-103">Use the **ft crawl bandwidth** option to specify the size to which the pool of large memory buffers can grow.</span></span> <span data-ttu-id="8140d-104">大型記憶體緩衝區的大小是 4 MB。</span><span class="sxs-lookup"><span data-stu-id="8140d-104">Large memory buffers are 4 megabytes (MB) in size.</span></span> <span data-ttu-id="8140d-105">**max** 參數值指定全文檢索記憶體管理員應該在大型緩衝集區中維持的最大緩衝區數目。</span><span class="sxs-lookup"><span data-stu-id="8140d-105">The **max** parameter value specifies the maximum number of buffers that the full-text memory manager should maintain in a large buffer pool.</span></span> <span data-ttu-id="8140d-106">如果 **max** 值為零，則位在大型緩衝集區的緩衝區數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="8140d-106">If the **max** value is zero, then there is no upper limit to the number of buffers that can be in a large buffer pool.</span></span>  
  
 <span data-ttu-id="8140d-107">**min** 參數指定必須在大型記憶體緩衝集區維持的最小記憶體緩衝區數目。</span><span class="sxs-lookup"><span data-stu-id="8140d-107">The **min** parameter specifies the minimum number of memory buffers that must be maintained in the pool of large memory buffers.</span></span> <span data-ttu-id="8140d-108">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記憶體管理員的要求下，所有額外緩衝集區都會釋放，但仍會維護最小數目的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8140d-108">Upon request from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory manager, all extra buffer pools will be released but this minimum number of buffers will be maintained.</span></span> <span data-ttu-id="8140d-109">但是，如果指定的 **min** 值是零，則會釋放所有記憶體緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8140d-109">If, however, the **min** value specified is zero, then all memory buffers are released.</span></span>  
  
 <span data-ttu-id="8140d-110">在某些情況下，目前配置的緩衝區數目小於 **min** 參數所指定的值。</span><span class="sxs-lookup"><span data-stu-id="8140d-110">Under certain circumstances, the number of buffers currently allocated is less than the value specified by the **min** parameter.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8140d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8140d-111">See Also</span></span>  
 <span data-ttu-id="8140d-112">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8140d-112">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="8140d-113">[全文檢索通知頻寬伺服器組態選項](ft-notify-bandwidth-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="8140d-113">[ft notify bandwidth Server Configuration Option](ft-notify-bandwidth-server-configuration-option.md) </span></span>  
 [<span data-ttu-id="8140d-114">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8140d-114">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
