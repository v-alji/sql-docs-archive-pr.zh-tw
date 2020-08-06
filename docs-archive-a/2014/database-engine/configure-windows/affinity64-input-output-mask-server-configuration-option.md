---
title: Affinity64 I/O Mask 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- processor affinity [SQL Server]
- binding processors [SQL Server]
- affinity64 I/O mask option
ms.assetid: d304eae7-5116-40ee-a0fa-0a3c0bc20c01
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19616f5718254bde5601ea1beeec21412ad867de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597353"
---
# <a name="affinity64-input-output-mask-server-configuration-option"></a><span data-ttu-id="a9d40-102">affinity64 輸入輸出伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="a9d40-102">affinity64 Input-Output mask Server Configuration Option</span></span>
  <span data-ttu-id="a9d40-103">**affinity64 I/O mask** 會將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 磁碟 I/O 繫結至指定的 CPU 子集 (與 **affinity I/O mask** 選項很相似)。</span><span class="sxs-lookup"><span data-stu-id="a9d40-103">The **affinity64 I/O mask** binds [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disk I/O to a specified subset of CPUs, similar to the **affinity I/O mask** option.</span></span> <span data-ttu-id="a9d40-104">請使用 **affinity I/O mask** 來繫結前 32 個處理器，然後使用 **affinity64 I/O mask** 來繫結電腦上剩餘的處理器。</span><span class="sxs-lookup"><span data-stu-id="a9d40-104">Use **affinity I/O mask** to bind the first 32 processors, and use **affinity64 I/O mask** to bind the remaining processors on the computer.</span></span> <span data-ttu-id="a9d40-105">如果您重新設定 **affinity64 I/O mask**，就必須重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a9d40-105">If you reconfigure the **affinity64 I/O mask**, you must restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a9d40-106">這個選項只出現在 64 位元版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a9d40-106">This option is only visible on the 64-bit version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9d40-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9d40-107">See Also</span></span>  
 <span data-ttu-id="a9d40-108">[affinity Input-Output mask 伺服器組態選項](affinity-input-output-mask-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="a9d40-108">[affinity Input-Output mask Server Configuration Option](affinity-input-output-mask-server-configuration-option.md) </span></span>  
 <span data-ttu-id="a9d40-109">[監視資源使用量 &#40;系統監視器&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="a9d40-109">[Monitor Resource Usage &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="a9d40-110">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a9d40-110">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="a9d40-111">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a9d40-111">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="a9d40-112">RECONFIGURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a9d40-112">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
