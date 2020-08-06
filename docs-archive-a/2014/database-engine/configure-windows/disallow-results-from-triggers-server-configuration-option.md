---
title: 不允許來自觸發程序的結果伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], result sets
- result sets [SQL Server], triggers
- disallow results from triggers option
ms.assetid: 47149073-307d-47a5-b7d2-66a737d3231d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f162a6e06706561d861bfc54a1ae4027f2c3466e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686479"
---
# <a name="disallow-results-from-triggers-server-configuration-option"></a><span data-ttu-id="4969f-102">不允許來自觸發程序的結果伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="4969f-102">disallow results from triggers Server Configuration Option</span></span>
  <span data-ttu-id="4969f-103">使用 **disallow results from triggers** 選項來控制觸發程序是否要傳回結果集。</span><span class="sxs-lookup"><span data-stu-id="4969f-103">Use the **disallow results from triggers** option to control whether triggers return result sets.</span></span> <span data-ttu-id="4969f-104">傳回結果集的觸發程序可能會導致非專用的應用程式發生非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="4969f-104">Triggers that return result sets may cause unexpected behavior in applications that are not designed to work with them.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] <span data-ttu-id="4969f-105">建議您將此值設定為 1。</span><span class="sxs-lookup"><span data-stu-id="4969f-105">We recommend that you set this value to 1.</span></span>  
  
 <span data-ttu-id="4969f-106">若設為 1， **disallow results from triggers** 選項就會設為 ON。</span><span class="sxs-lookup"><span data-stu-id="4969f-106">When set to 1, the **disallow results from triggers** option is set to ON.</span></span> <span data-ttu-id="4969f-107">這個選項的預設值是 0 (OFF)。</span><span class="sxs-lookup"><span data-stu-id="4969f-107">The default setting for this option is 0 (OFF).</span></span> <span data-ttu-id="4969f-108">若此選項設為 1 (ON)，則觸發程序嘗試傳回結果集的任何動作都會失敗，而使用者會收到下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="4969f-108">If this option is set to 1 (ON), any attempt by a trigger to return a result set fails, and the user receives the following error message:</span></span>  
  
 <span data-ttu-id="4969f-109">「訊息 524，層級 16，狀態 1，程序 \<Procedure Name>，行 \<Line#>」</span><span class="sxs-lookup"><span data-stu-id="4969f-109">"Msg 524, Level 16, State 1, Procedure \<Procedure Name>, Line \<Line#></span></span>  
  
 <span data-ttu-id="4969f-110">「觸發程序傳回一個結果集，而且伺服器選項 'disallow_results_from_triggers' 為 True。」</span><span class="sxs-lookup"><span data-stu-id="4969f-110">"A trigger returned a resultset and the server option 'disallow_results_from_triggers' is true."</span></span>  
  
 <span data-ttu-id="4969f-111">[不允許來自觸發程序的結果] 選項是套用於 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體層級，且它會決定執行個體中所有現有觸發程序的行為。</span><span class="sxs-lookup"><span data-stu-id="4969f-111">The **disallow results from triggers** option is applied at the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance level, and it will determine behavior for all existing triggers within the instance.</span></span>  
  
 <span data-ttu-id="4969f-112">**disallow results from triggers** 選項是進階選項。</span><span class="sxs-lookup"><span data-stu-id="4969f-112">The **disallow results from triggers** option is an advanced option.</span></span> <span data-ttu-id="4969f-113">若使用 **sp_configure** 系統預存程序來變更設定，只有當 [顯示進階選項] 設為 1 時，才能變更觸發程序不允許的結果。</span><span class="sxs-lookup"><span data-stu-id="4969f-113">If you are using the **sp_configure** system stored procedure to change the setting, you can change disallow results from triggers only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="4969f-114">設定會立即生效，伺服器不必重新啟動。</span><span class="sxs-lookup"><span data-stu-id="4969f-114">The setting takes effect immediately without a server restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4969f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4969f-115">See Also</span></span>  
 <span data-ttu-id="4969f-116">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4969f-116">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="4969f-117">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4969f-117">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="4969f-118">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4969f-118">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
