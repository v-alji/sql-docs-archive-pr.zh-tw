---
title: access check cache 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- access check cache option
- access check cache bucket count
- access check cache quota
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: feed895eeb7b11b4c41c51c4c26859a1057d2733
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584732"
---
# <a name="access-check-cache-server-configuration-options"></a><span data-ttu-id="c3254-102">存取檢查快取伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="c3254-102">access check cache Server Configuration Options</span></span>
<span data-ttu-id="c3254-103">當資料庫物件是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]所存取時，存取檢查會在稱為 **access check result cache**的內部結構中進行快取。</span><span class="sxs-lookup"><span data-stu-id="c3254-103">When database objects are accessed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the access check is cached in an internal structure called the **access check result cache**.</span></span> 
  
<span data-ttu-id="c3254-104">[存取檢查快取 Bucket 計數] 選項可控制用於存取檢查結果快取的雜湊貯體數目。</span><span class="sxs-lookup"><span data-stu-id="c3254-104">The **access check cache bucket count** option controls the number of hash buckets that are used for the access check result cache.</span></span> 

<span data-ttu-id="c3254-105">[存取檢查快取配額] 選項可控制儲存在存取檢查結果快取中的項目數。</span><span class="sxs-lookup"><span data-stu-id="c3254-105">The **access check cache quota** option controls the number of entries that are stored in the access check result cache.</span></span> <span data-ttu-id="c3254-106">達到最大項目數時，會從存取檢查結果快取中移除最舊的項目。</span><span class="sxs-lookup"><span data-stu-id="c3254-106">When the maximum number of entries is reached, the oldest entries are removed from the access check result cache.</span></span>
  
<span data-ttu-id="c3254-107">預設值 0 表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在管理這些選項。</span><span class="sxs-lookup"><span data-stu-id="c3254-107">The default values of 0 indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is managing these options.</span></span> <span data-ttu-id="c3254-108">從 [!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)] 到 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] ，預設值會轉譯為下列內部設定：</span><span class="sxs-lookup"><span data-stu-id="c3254-108">From [!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)] through [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], the default values translate to the following internal configurations:</span></span>
-   <span data-ttu-id="c3254-109">針對存取檢查快取 bucket 計數，值0會設定 x86 架構的預設值為256，而 x64 和 IA-64 架構則為 2048 bucket。</span><span class="sxs-lookup"><span data-stu-id="c3254-109">For access check cache bucket count, the value 0 sets a default value of 256 buckets for x86 architecture, and 2,048 buckets for x64 and IA-64 architectures.</span></span>
-   <span data-ttu-id="c3254-110">針對存取檢查快取配額，值0會為 x86 架構設定1024專案的預設值，以及 x64 和 IA-64 架構的 28192048 bucket。</span><span class="sxs-lookup"><span data-stu-id="c3254-110">For access check cache quota, the value 0 sets a default value of 1,024 entries for x86 architecture, and 28,192,048 buckets for x64 and IA-64 architectures.</span></span>

<span data-ttu-id="c3254-111">在罕見的情況下，可以變更這些選項來提升效能。</span><span class="sxs-lookup"><span data-stu-id="c3254-111">In rare circumstances, performance can be improved by changing these options.</span></span> <span data-ttu-id="c3254-112">例如，如果使用太多記憶體，則建議減少存取檢查結果快取的大小。</span><span class="sxs-lookup"><span data-stu-id="c3254-112">For example, you may want to reduce the size of the access check result cache if too much memory is used.</span></span> <span data-ttu-id="c3254-113">或者，如果在重新計算權限時出現高 CPU 使用量，則建議增加存取檢查結果快取的大小。</span><span class="sxs-lookup"><span data-stu-id="c3254-113">Or, you may want to increase the size of the access check result cache if you experience high CPU usage when permissions are recalculated.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3254-114">Microsoft 建議只要變更 Microsoft 客戶支援服務所導向的那些選項。</span><span class="sxs-lookup"><span data-stu-id="c3254-114">Microsoft recommends only changing these options when directed by Microsoft Customer Support Services.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c3254-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3254-115">See Also</span></span>  
 <span data-ttu-id="c3254-116">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c3254-116">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="c3254-117">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c3254-117">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
