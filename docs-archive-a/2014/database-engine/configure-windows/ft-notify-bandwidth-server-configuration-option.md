---
title: 全文檢索通知頻寬伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- ft notify bandwidth opion
- small memory buffers
- memory [SQL Server], buffers
ms.assetid: 9ca284c5-f3e0-4a67-a132-fff376ff0ffe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dc5839f699d55edf86c5e3e3f0eb001089a0a5dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706746"
---
# <a name="ft-notify-bandwidth-server-configuration-option"></a><span data-ttu-id="b4ac3-102">全文檢索通知頻寬伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="b4ac3-102">ft notify bandwidth Server Configuration Option</span></span>
  <span data-ttu-id="b4ac3-103">使用 [全文檢索通知頻寬] 選項，指定小型記憶體緩衝集區可以成長到何種大小。</span><span class="sxs-lookup"><span data-stu-id="b4ac3-103">Use the **ft notify bandwidth** option to specify the size to which the pool of small memory buffers can grow.</span></span> <span data-ttu-id="b4ac3-104">小型記憶體緩衝區的大小是 64 KB。</span><span class="sxs-lookup"><span data-stu-id="b4ac3-104">Small memory buffers are 64 kilobytes (KB) in size.</span></span> <span data-ttu-id="b4ac3-105">*max* 參數值會指定全文檢索記憶體管理員應該在小型緩衝集區中維持的最大緩衝區數目。</span><span class="sxs-lookup"><span data-stu-id="b4ac3-105">The *max* parameter value specifies the maximum number of buffers that the full-text memory manager should maintain in a small buffer pool.</span></span> <span data-ttu-id="b4ac3-106">如果 `max` 值為零，則可以位於小型緩衝集區的緩衝區數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="b4ac3-106">If the `max` value is zero, then there is no upper limit to the number of buffers that can be in a small buffer pool.</span></span>  
  
 <span data-ttu-id="b4ac3-107">**min** 參數指定必須在小型記憶體緩衝集區中維持的最小記憶體緩衝區數目。</span><span class="sxs-lookup"><span data-stu-id="b4ac3-107">The **min** parameter specifies the minimum number of memory buffers that must be maintained in the pool of small memory buffers.</span></span> <span data-ttu-id="b4ac3-108">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記憶體管理員的要求下，所有額外緩衝集區都會釋放，但仍會維護最小數目的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b4ac3-108">Upon request from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory manager, all extra buffer pools will be released but this minimum number of buffers will be maintained.</span></span> <span data-ttu-id="b4ac3-109">但是，如果指定的 **min** 值是零，則會釋放所有記憶體緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b4ac3-109">If, however, the **min** value specified is zero, then all memory buffers are released.</span></span>  
  
 <span data-ttu-id="b4ac3-110">在某些情況下，目前配置的緩衝區數目小於 **min** 參數所指定的值。</span><span class="sxs-lookup"><span data-stu-id="b4ac3-110">Under certain circumstances the number of buffers currently allocated is less than the value specified by the **min** parameter.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b4ac3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4ac3-111">See Also</span></span>  
 <span data-ttu-id="b4ac3-112">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b4ac3-112">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="b4ac3-113">[全文檢索編目頻寬伺服器組態選項](ft-crawl-bandwidth-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="b4ac3-113">[ft crawl bandwidth Server Configuration Option](ft-crawl-bandwidth-server-configuration-option.md) </span></span>  
 [<span data-ttu-id="b4ac3-114">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b4ac3-114">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
