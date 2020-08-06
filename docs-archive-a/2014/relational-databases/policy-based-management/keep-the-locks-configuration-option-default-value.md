---
title: 保留鎖定組態選項預設值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: f214f05b-5f0b-4786-b2ad-b8b4b6e58d72
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a1d1dcf82d9cd0ef8ef2c15cb68ef78b53a8a54a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591971"
---
# <a name="keep-the-locks-configuration-option-default-value"></a><span data-ttu-id="8ac9d-102">保留鎖定組態選項預設值</span><span class="sxs-lookup"><span data-stu-id="8ac9d-102">Keep the Locks Configuration Option Default Value</span></span>
  <span data-ttu-id="8ac9d-103">此規則會檢查 locks configuration 選項的值。</span><span class="sxs-lookup"><span data-stu-id="8ac9d-103">This rule checks the value of the locks configuration option.</span></span> <span data-ttu-id="8ac9d-104">這個選項會判斷可用鎖定數目的最大值。</span><span class="sxs-lookup"><span data-stu-id="8ac9d-104">This option determines the maximum number of available locks.</span></span> <span data-ttu-id="8ac9d-105">這會限制 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 用於鎖定的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="8ac9d-105">This limits how much memory the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses for locks.</span></span> <span data-ttu-id="8ac9d-106">預設值 0 會讓 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 根據變更的系統需求，動態配置及取消配置鎖定結構。</span><span class="sxs-lookup"><span data-stu-id="8ac9d-106">The default setting of 0 enables the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to allocate and deallocate lock structures dynamically based on changing system requirements.</span></span>  
  
 <span data-ttu-id="8ac9d-107">如果鎖定是非零的值，批次作業將會停止，而且如果超過指定的值，將會產生「鎖定不足」的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="8ac9d-107">If locks is nonzero, batch jobs will stop, and an "out of locks" error message will be generated, if the value specified is exceeded.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="8ac9d-108">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="8ac9d-108">Best Practices Recommendations</span></span>  
 <span data-ttu-id="8ac9d-109">使用 sp_configure 系統預存程序，可透過以下陳述式將鎖定的值變更為它的預設值：</span><span class="sxs-lookup"><span data-stu-id="8ac9d-109">Use the sp_configure system stored procedure to change the value of locks to its default setting by using the following statement:</span></span>  
  
```  
EXEC sp_configure 'locks', 0;  
```  
  
## <a name="for-more-information"></a><span data-ttu-id="8ac9d-110">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="8ac9d-110">For More Information</span></span>  
 [<span data-ttu-id="8ac9d-111">設定 locks 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="8ac9d-111">Configure the locks Server Configuration Option</span></span>](../../database-engine/configure-windows/configure-the-locks-server-configuration-option.md)  
  
 [<span data-ttu-id="8ac9d-112">sys.dm_tran_locks &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8ac9d-112">sys.dm_tran_locks &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql)  
  
 [<span data-ttu-id="8ac9d-113">sys.dm_os_wait_stats &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8ac9d-113">sys.dm_os_wait_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql)  
  
 [<span data-ttu-id="8ac9d-114">Microsoft 知識庫文章 271509</span><span class="sxs-lookup"><span data-stu-id="8ac9d-114">Microsoft Knowledge Base article 271509</span></span>](https://go.microsoft.com/fwlink/?linkid=117788)  
  
## <a name="see-also"></a><span data-ttu-id="8ac9d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ac9d-115">See Also</span></span>  
 [<span data-ttu-id="8ac9d-116">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="8ac9d-116">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
