---
title: 增加或停用已封鎖的處理序閾值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 71db8ef6-341b-4465-99db-5c63e48d4c7d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a7a90aea3fa8fb4d9c423cea1ec6008b01cde883
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591981"
---
# <a name="increase-or-disable-blocked-process-threshold"></a><span data-ttu-id="dcf50-102">增加或停用 Blocked Process Threshold</span><span class="sxs-lookup"><span data-stu-id="dcf50-102">Increase or Disable Blocked Process Threshold</span></span>
  <span data-ttu-id="dcf50-103">此規則會檢查 blocked process threshold 選項設定為 0 (已停用) 還是設定為高於或等於 5 (秒) 的值。</span><span class="sxs-lookup"><span data-stu-id="dcf50-103">This rules checks that the blocked process threshold option is set to 0 (disabled) or set to a value higher than or equal to 5 (seconds).</span></span> <span data-ttu-id="dcf50-104">將 blocked process threshold 選項設定為 1 到 4 的值會造成死結監視器不斷執行。</span><span class="sxs-lookup"><span data-stu-id="dcf50-104">Setting the blocked process threshold option to a value from 1 to 4 can cause the deadlock monitor to run constantly.</span></span> <span data-ttu-id="dcf50-105">1 到 4 之間的值應該只用於疑難排解，絕不能在沒有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶服務與支援中心協助的情形下，長期使用或用在實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="dcf50-105">Values 1 to 4 should only be used for troubleshooting, and never long term or in a production environment without the assistance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="dcf50-106">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="dcf50-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="dcf50-107">若要解決這個問題，請將 blocked process threshold 選項設定為 5 (秒) 或更高的值，或是將此值設定為 0 來停用 blocked process threshold。</span><span class="sxs-lookup"><span data-stu-id="dcf50-107">To resolve this problem, set the blocked process threshold option to a value of 5 (seconds) or higher, or disable blocked process threshold by setting the value to 0.</span></span> <span data-ttu-id="dcf50-108">若要將 blocked process threshold 設定為 `5` 秒的值，請執行以下陳述式：</span><span class="sxs-lookup"><span data-stu-id="dcf50-108">To set the blocked process threshold to a value of `5` seconds, execute the following statement:</span></span>  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 5 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="for-more-information"></a><span data-ttu-id="dcf50-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="dcf50-109">For More Information</span></span>  
 [<span data-ttu-id="dcf50-110">已封鎖的處理序臨界值伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="dcf50-110">blocked process threshold Server Configuration Option</span></span>](../../database-engine/configure-windows/blocked-process-threshold-server-configuration-option.md)  
  
## <a name="see-also"></a><span data-ttu-id="dcf50-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcf50-111">See Also</span></span>  
 [<span data-ttu-id="dcf50-112">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="dcf50-112">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
