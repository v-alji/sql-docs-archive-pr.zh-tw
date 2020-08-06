---
title: 不能肯定的交易解析伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- distributed transactions [SQL Server], unresolved transactions
- unresolved transactions
- in-doubt xact resolution option
ms.assetid: 3426fd32-cad2-4f2f-8ca9-e0296cc12703
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6b8db57ef2a4ee85d65e8c25de28ff7ada7994e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688226"
---
# <a name="in-doubt-xact-resolution-server-configuration-option"></a><span data-ttu-id="dc8f8-102">不能肯定的交易解析伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="dc8f8-102">in-doubt xact resolution Server Configuration Option</span></span>
  <span data-ttu-id="dc8f8-103">使用 [不能肯定的交易解析] 選項，可控制 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) 無法解析之交易的預設結果。</span><span class="sxs-lookup"><span data-stu-id="dc8f8-103">Use the **in-doubt xact resolution** option to control the default outcome of transactions that the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) is unable to resolve.</span></span> <span data-ttu-id="dc8f8-104">無法解析交易的原因，可能與 MS DTC 停機，或在復原時出現未知的交易結果等狀況有關。</span><span class="sxs-lookup"><span data-stu-id="dc8f8-104">Inability to resolve transactions may be related to the MS DTC down time or an unknown transaction outcome at the time of recovery.</span></span>  
  
 <span data-ttu-id="dc8f8-105">下表列出解析不確定的交易時，可能出現的結果值。</span><span class="sxs-lookup"><span data-stu-id="dc8f8-105">The following table lists the possible outcome values for resolving an in-doubt transaction.</span></span>  
  
|<span data-ttu-id="dc8f8-106">結果值</span><span class="sxs-lookup"><span data-stu-id="dc8f8-106">Outcome value</span></span>|<span data-ttu-id="dc8f8-107">描述</span><span class="sxs-lookup"><span data-stu-id="dc8f8-107">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="dc8f8-108">0</span><span class="sxs-lookup"><span data-stu-id="dc8f8-108">0</span></span>|<span data-ttu-id="dc8f8-109">無假設結果。</span><span class="sxs-lookup"><span data-stu-id="dc8f8-109">No presumption.</span></span> <span data-ttu-id="dc8f8-110">如果 MS DTC 有無法解析的不確定交易，復原即會失敗。</span><span class="sxs-lookup"><span data-stu-id="dc8f8-110">Recovery fails if MS DTC cannot resolve any in-doubt transactions.</span></span>|  
|<span data-ttu-id="dc8f8-111">1</span><span class="sxs-lookup"><span data-stu-id="dc8f8-111">1</span></span>|<span data-ttu-id="dc8f8-112">假設為認可。</span><span class="sxs-lookup"><span data-stu-id="dc8f8-112">Presume commit.</span></span> <span data-ttu-id="dc8f8-113">任何 MS DTC 不確定的交易都假設為已認可。</span><span class="sxs-lookup"><span data-stu-id="dc8f8-113">Any MS DTC in-doubt transactions are presumed to have committed.</span></span>|  
|<span data-ttu-id="dc8f8-114">2</span><span class="sxs-lookup"><span data-stu-id="dc8f8-114">2</span></span>|<span data-ttu-id="dc8f8-115">假設為中止。</span><span class="sxs-lookup"><span data-stu-id="dc8f8-115">Presume abort.</span></span> <span data-ttu-id="dc8f8-116">任何 MS DTC 不確定的交易都假設為已中止。</span><span class="sxs-lookup"><span data-stu-id="dc8f8-116">Any MS DTC in-doubt transactions are presumed to have aborted.</span></span>|  
  
 <span data-ttu-id="dc8f8-117">若要將停機時間降到最低，系統管理員可將此選項設為「假設為認可」或「假設為中止」，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="dc8f8-117">To minimize the possibility of extended down time, an administrator might choose to configure this option either to presume commit or presume abort, as shown in the following example.</span></span>  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 2 -- presume abort  
GO  
RECONFIGURE  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="dc8f8-118">或者，系統管理員也可以採用預設值 (無假設結果) 並允許復原失敗，以便記錄 DTC 失敗，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="dc8f8-118">Alternatively, the administrator might want to leave the default (no presumption) and allow recovery to fail in order to be made aware of a DTC failure, as shown in the following example.</span></span>  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 1 -- presume commit  
GO  
reconfigure  
GO  
ALTER DATABASE pubs SET ONLINE -- run recovery again  
GO  
sp_configure 'in-doubt xact resolution', 0 -- back to no assumptions  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="dc8f8-119">[不能肯定的交易解析] 選項屬於進階選項。</span><span class="sxs-lookup"><span data-stu-id="dc8f8-119">The **in-doubt xact resolution** option is an advanced option.</span></span> <span data-ttu-id="dc8f8-120">如果您要使用 **sp_configure** 系統預存程序來變更此設定，只有在 [顯示進階選項] 設為 1 時，才能變更 [不能肯定的交易解析]。</span><span class="sxs-lookup"><span data-stu-id="dc8f8-120">If you are using the **sp_configure** system stored procedure to change the setting, you can change **in-doubt xact resolution** only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="dc8f8-121">設定會立即生效，伺服器不必重新啟動。</span><span class="sxs-lookup"><span data-stu-id="dc8f8-121">The setting takes effect immediately without a server restart.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc8f8-122">在與分散式交易相關的所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上，讓此選項的組態都維持一致，將有助於避免資料不一致。</span><span class="sxs-lookup"><span data-stu-id="dc8f8-122">Consistent configuration of this option across all [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances involved in any distributed transactions will help avoid data inconsistencies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc8f8-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc8f8-123">See Also</span></span>  
 <span data-ttu-id="dc8f8-124">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dc8f8-124">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="dc8f8-125">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="dc8f8-125">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="dc8f8-126">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dc8f8-126">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
