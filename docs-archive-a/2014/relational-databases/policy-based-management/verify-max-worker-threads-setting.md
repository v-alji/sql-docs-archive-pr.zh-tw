---
title: 驗證最大工作者執行緒設定 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 2d94adfd-3ba1-493a-b29a-b436f9d583df
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5dbffb87f58d2beb633f43ff18680222ea62cf5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593986"
---
# <a name="verify-max-worker-threads-setting"></a><span data-ttu-id="14390-102">確認最大工作者執行緒設定</span><span class="sxs-lookup"><span data-stu-id="14390-102">Verify Max Worker Threads Setting</span></span>
  <span data-ttu-id="14390-103">此規則會檢查 max worker threads server 選項中是否可能有不正確的設定。</span><span class="sxs-lookup"><span data-stu-id="14390-103">This rule checks the max worker threads server option for potentially incorrect settings.</span></span> <span data-ttu-id="14390-104">將 max worker threads 選項設定為很小的值可能會阻礙足夠的執行緒及時服務內送用戶端要求，而且可能會導致執行緒資源用盡。</span><span class="sxs-lookup"><span data-stu-id="14390-104">Setting the max worker threads option to a small value may prevent enough threads from servicing incoming client requests in a timely manner and could lead to "thread starvation".</span></span> <span data-ttu-id="14390-105">但是，將此選項設定為較大的值可能會浪費位址空間，因為每一個使用中執行緒都會在 32 位元伺服器上耗用 512 KB 空間，並在 64 位元伺服器上最多耗用 4 MB 空間。</span><span class="sxs-lookup"><span data-stu-id="14390-105">However, setting the option to a large value can waste address space, because each active thread consumes 512 KB on 32-bit servers and up to 4 MB on 64-bit servers.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="14390-106">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="14390-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="14390-107">將 max worker threads 選項設成 0。</span><span class="sxs-lookup"><span data-stu-id="14390-107">Set the max worker threads option to 0.</span></span> <span data-ttu-id="14390-108">如此可讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 根據使用者要求來自動判斷 active worker threads 的正確數目。</span><span class="sxs-lookup"><span data-stu-id="14390-108">This enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to automatically determine the correct number of active worker threads based on user requests.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="14390-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="14390-109">For More Information</span></span>  
 [<span data-ttu-id="14390-110">設定 max worker threads 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="14390-110">Configure the max worker threads Server Configuration Option</span></span>](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)  
  
## <a name="see-also"></a><span data-ttu-id="14390-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14390-111">See Also</span></span>  
 [<span data-ttu-id="14390-112">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="14390-112">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
