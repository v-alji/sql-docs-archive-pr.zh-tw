---
title: Affinity64 Mask 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- processor affinity [SQL Server]
- affinity64 mask option
- binding processors [SQL Server]
ms.assetid: 75ed08c7-f85c-4e15-9ee1-e7bc545d3293
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d2ea6d2e364feaa67d91de0055617aac9dc285ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597351"
---
# <a name="affinity64-mask-server-configuration-option"></a><span data-ttu-id="0082e-102">affinity64 mask 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="0082e-102">affinity64 mask Server Configuration Option</span></span>
  <span data-ttu-id="0082e-103">與 affinity mask 選項類似，affinity64 mask 會將處理器繫結到特定的執行緒。</span><span class="sxs-lookup"><span data-stu-id="0082e-103">The affinity64 mask binds processors to specific threads, similar to the affinity mask option.</span></span> <span data-ttu-id="0082e-104">請使用 affinity mask 來繫結前 32 個處理器，然後使用 affinity64 mask 來繫結電腦上剩餘的處理器。</span><span class="sxs-lookup"><span data-stu-id="0082e-104">Use affinity mask to bind the first 32 processors, and use affinity64 mask to bind the remaining processors on the computer.</span></span> <span data-ttu-id="0082e-105">這個選項只出現在 64 位元版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0082e-105">This option is only visible on the 64-bit version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)] <span data-ttu-id="0082e-106">請改用 [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0082e-106">Use [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql) instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0082e-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0082e-107">See Also</span></span>  
 <span data-ttu-id="0082e-108">[affinity mask 伺服器組態選項](affinity-mask-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="0082e-108">[affinity mask Server Configuration Option](affinity-mask-server-configuration-option.md) </span></span>  
 <span data-ttu-id="0082e-109">[監視資源使用量 &#40;系統監視器&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="0082e-109">[Monitor Resource Usage &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="0082e-110">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0082e-110">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="0082e-111">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0082e-111">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="0082e-112">RECONFIGURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0082e-112">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
