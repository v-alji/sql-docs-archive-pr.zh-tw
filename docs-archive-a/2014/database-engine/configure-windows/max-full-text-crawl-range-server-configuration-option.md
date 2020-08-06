---
title: 全文檢索編目最大範圍伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- crawls [full-text search]
- max full-text crawl range option
ms.assetid: a49de86b-0891-4dcd-89c0-ead30aab00e0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e1dbd9e44518b6e849a06a76e21fc605172fd2ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687150"
---
# <a name="max-full-text-crawl-range-server-configuration-option"></a><span data-ttu-id="fe56d-102">全文檢索搜耙最大範圍伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="fe56d-102">max full-text crawl range Server Configuration Option</span></span>
  <span data-ttu-id="fe56d-103">使用 **max full-text crawl range** 選項可最佳化 CPU 使用率，這會在完整搜耙期間增進搜耙效能。</span><span class="sxs-lookup"><span data-stu-id="fe56d-103">Use the **max full-text crawl range** option to optimize CPU utilization, which improves crawl performance during a full crawl.</span></span> <span data-ttu-id="fe56d-104">使用這個選項，您可以指定完整索引搜耙期間 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 應該使用的資料分割數目。</span><span class="sxs-lookup"><span data-stu-id="fe56d-104">Using this option, you can specify the number of partitions that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should use during a full index crawl.</span></span> <span data-ttu-id="fe56d-105">例如，如果有多個 CPU 且其使用率不是最好的，則您可以增加這個選項的最大值。</span><span class="sxs-lookup"><span data-stu-id="fe56d-105">For example, if there are many CPUs and their utilization is not optimal, you can increase the maximum value of this option.</span></span> <span data-ttu-id="fe56d-106">除了這個選項之外， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 還會使用一些其他因素，如資料表中的資料列數目及 CPU 數目，來判斷實際使用的資料分割數目。</span><span class="sxs-lookup"><span data-stu-id="fe56d-106">In addition to this option, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses a number of other factors, such as the number of rows in the table and the number of CPUs, to determine the actual number of partitions used.</span></span>  
  
 <span data-ttu-id="fe56d-107">此選項的預設值為 4、最小值為 1，而最大值為 256。</span><span class="sxs-lookup"><span data-stu-id="fe56d-107">The default value of this option is 4; the minimum value is 1, and the maximum value is 256.</span></span> <span data-ttu-id="fe56d-108">變更此選項僅會影響後續的搜耙。</span><span class="sxs-lookup"><span data-stu-id="fe56d-108">Changes made to this option affect only subsequent crawls.</span></span> <span data-ttu-id="fe56d-109">這個選項設定中的變更將不會影響進行中的搜耙。</span><span class="sxs-lookup"><span data-stu-id="fe56d-109">Crawls in process will not be affected by a change in this option setting.</span></span>  
  
 <span data-ttu-id="fe56d-110">**max full-text crawl range** 選項是進階選項。</span><span class="sxs-lookup"><span data-stu-id="fe56d-110">The **max full-text crawl range** option is an advanced option.</span></span> <span data-ttu-id="fe56d-111">如果您要使用 **sp_configure** 系統預存程序來變更設定，只有當 **show advanced options** 設為 1 時，才能變更 **max full-text crawl range** 。</span><span class="sxs-lookup"><span data-stu-id="fe56d-111">If you are using the **sp_configure** system stored procedure to change the setting, you can change **max full-text crawl range** only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="fe56d-112">設定會立即生效，伺服器不必重新啟動。</span><span class="sxs-lookup"><span data-stu-id="fe56d-112">The setting takes effect immediately without a server restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe56d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe56d-113">See Also</span></span>  
 <span data-ttu-id="fe56d-114">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fe56d-114">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="fe56d-115">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fe56d-115">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="fe56d-116">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fe56d-116">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
