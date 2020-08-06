---
title: 伺服器觸發程序遞迴伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- recursive triggers [SQL Server]
- triggers [SQL Server], recursive
- server trigger recursion option
ms.assetid: da4c25f5-d04c-4951-a3db-409e71a1b468
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 23a4997bd1a6f8b2c04af34d5cdc3229575901a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707850"
---
# <a name="server-trigger-recursion-server-configuration-option"></a><span data-ttu-id="2e876-102">伺服器觸發程序遞迴伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="2e876-102">server trigger recursion Server Configuration Option</span></span>
  <span data-ttu-id="2e876-103">使用 [伺服器觸發程序遞迴] 選項，可指定是否允許伺服器層級的觸發程序以遞迴方式引發。</span><span class="sxs-lookup"><span data-stu-id="2e876-103">Use the **server trigger recursion** option to specify whether to allow server-level triggers to fire recursively.</span></span> <span data-ttu-id="2e876-104">如果此選項設成 1 (ON)，則允許伺服器層級的觸發程序以遞迴方式引發。</span><span class="sxs-lookup"><span data-stu-id="2e876-104">When this option is set to 1 (ON), server-level triggers will be allowed to fire recursively.</span></span> <span data-ttu-id="2e876-105">若設成 0 (OFF)，則伺服器層級的觸發程序無法以遞迴方式引發。</span><span class="sxs-lookup"><span data-stu-id="2e876-105">When set to 0 (OFF), server-level triggers cannot be fired recursively.</span></span> <span data-ttu-id="2e876-106">當 server trigger recursion 選項設為 0 (OFF)，只能阻止直接遞迴。</span><span class="sxs-lookup"><span data-stu-id="2e876-106">Only direct recursion is prevented when the server trigger recursion option is set to 0 (OFF).</span></span> <span data-ttu-id="2e876-107">(若要停用間接遞迴，請將 [巢狀觸發程序] 選項設定為 0)。這個選項的預設值是 1 (ON)。</span><span class="sxs-lookup"><span data-stu-id="2e876-107">(To disable indirect recursion, set the **nested triggers** option to 0.) The default value for this option is 1 (ON).</span></span> <span data-ttu-id="2e876-108">伺服器不需重新啟動，設定即可立刻生效。</span><span class="sxs-lookup"><span data-stu-id="2e876-108">The setting takes effect immediately (without a server restart).</span></span>  
  
 <span data-ttu-id="2e876-109">如需相關資訊，請參閱 [建立巢狀觸發程序](../../relational-databases/triggers/create-nested-triggers.md)。</span><span class="sxs-lookup"><span data-stu-id="2e876-109">For more information, see [Create Nested Triggers](../../relational-databases/triggers/create-nested-triggers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e876-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e876-110">See Also</span></span>  
 <span data-ttu-id="2e876-111">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2e876-111">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="2e876-112">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2e876-112">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="2e876-113">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2e876-113">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
