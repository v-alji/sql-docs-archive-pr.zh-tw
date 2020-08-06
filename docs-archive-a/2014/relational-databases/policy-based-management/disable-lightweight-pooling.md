---
title: 停用輕量型共用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 481bb43d-6fe5-497c-9096-971fb6bf733b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 13b9ccba0a3a5805dab2eec1d04cc161e6dbd6ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709270"
---
# <a name="disable-lightweight-pooling"></a><span data-ttu-id="889ee-102">停用輕量型共用</span><span class="sxs-lookup"><span data-stu-id="889ee-102">Disable Lightweight Pooling</span></span>
  <span data-ttu-id="889ee-103">這個規則會檢查輕量型共用是否已經在伺服器上停用。</span><span class="sxs-lookup"><span data-stu-id="889ee-103">This rule checks that lightweight pooling is disabled on the server.</span></span> <span data-ttu-id="889ee-104">將 lightweightpooling 設定為 1 會使得 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 切換到 Fiber 模式排程。</span><span class="sxs-lookup"><span data-stu-id="889ee-104">Setting lightweightpooling to 1 causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to switch to fiber mode scheduling.</span></span> <span data-ttu-id="889ee-105">Fiber 模式適用於 UMS 工作者的環境切換是重要效能瓶頸的某些狀況。</span><span class="sxs-lookup"><span data-stu-id="889ee-105">Fiber mode is intended for certain situations in which the context switching of the UMS workers is the important bottleneck in performance.</span></span> <span data-ttu-id="889ee-106">因為這個狀況非常罕見，所以 Fiber 模式幾乎不太會提高一般系統上的效能或延展性。</span><span class="sxs-lookup"><span data-stu-id="889ee-106">Because this is rare, fiber mode seldom improves performance or scalability on the typical system.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="889ee-107">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="889ee-107">Best Practices Recommendations</span></span>  
 <span data-ttu-id="889ee-108">只有在徹底測試之後、評估所有其他效能微調機會之後以及環境切換是您所在環境的已知問題時，才應該啟用 lightweightpooling 選項。</span><span class="sxs-lookup"><span data-stu-id="889ee-108">The lightweightpooling option should only be enabled after thorough testing, after all other performance tuning opportunities are evaluated, and when context switching is a known issue in your environment.</span></span>  
  
 <span data-ttu-id="889ee-109">我們建議您不要針對日常作業使用 Fiber 模式排程，因為 Fiber 模式可能會抑制一般環境切換的好處而降低效能，而且使用執行緒本機存放裝置 (TLS) 或執行緒擁有之物件 (如 Mutex，這是一種 Win32 核心物件) 的某些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件無法在 Fiber 模式下正確運作。</span><span class="sxs-lookup"><span data-stu-id="889ee-109">We recommend that you do not use fiber mode scheduling for routine operation because it can decrease performance by preventing the regular benefits of context switching, and because some components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that use Thread Local Storage (TLS) or thread-owned objects, such as mutexes (a kind of Win32 kernel object), cannot function correctly in fiber mode</span></span>  
  
 <span data-ttu-id="889ee-110">若要移除輕量型共用，請執行以下陳述式，然後重新啟動： [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="889ee-110">To remove lightweight pooling, execute the following statement, and then restart the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
sp_configure 'lightweightpooling', 0;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="for-more-information"></a><span data-ttu-id="889ee-111">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="889ee-111">For More Information</span></span>  
 [<span data-ttu-id="889ee-112">輕量型共用伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="889ee-112">lightweight pooling Server Configuration Option</span></span>](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)  
  
## <a name="see-also"></a><span data-ttu-id="889ee-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="889ee-113">See Also</span></span>  
 [<span data-ttu-id="889ee-114">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="889ee-114">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
