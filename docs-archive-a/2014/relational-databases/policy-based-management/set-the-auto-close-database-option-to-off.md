---
title: 將 AUTO_CLOSE 資料庫選項設定為 OFF | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: db6cf5a3f82c3493a8732958594743104fccc968
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708206"
---
# <a name="set-the-auto_close-database-option-to-off"></a><span data-ttu-id="92b9d-102">將 AUTO_CLOSE 資料庫選項設定為 OFF</span><span class="sxs-lookup"><span data-stu-id="92b9d-102">Set the AUTO_CLOSE Database Option to OFF</span></span>
  <span data-ttu-id="92b9d-103">這個規則會檢查 AUTO_ CLOSE 選項是否設定為 OFF。</span><span class="sxs-lookup"><span data-stu-id="92b9d-103">This rule checks whether the AUTO_ CLOSE option is set OFF.</span></span> <span data-ttu-id="92b9d-104">當 AUTO_CLOSE 設定為 ON 時，這個選項可能會造成經常存取之資料庫的效能降低，因為在每一個連接之後都會增加開啟和關閉資料庫的負擔。</span><span class="sxs-lookup"><span data-stu-id="92b9d-104">When AUTO_CLOSE is set ON, this option can cause performance degradation on frequently accessed databases because of the increased overhead of opening and closing the database after each connection.</span></span> <span data-ttu-id="92b9d-105">在每一個連接之後，AUTO_CLOSE 也會排清程序快取。</span><span class="sxs-lookup"><span data-stu-id="92b9d-105">AUTO_CLOSE also flushes the procedure cache after each connection.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="92b9d-106">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="92b9d-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="92b9d-107">如果經常存取資料庫，請將此資料庫的 AUTO_CLOSE 選項設定為 OFF。</span><span class="sxs-lookup"><span data-stu-id="92b9d-107">If a database is accessed frequently, set the AUTO_CLOSE option to OFF for the database.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="92b9d-108">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="92b9d-108">For More Information</span></span>  
 [<span data-ttu-id="92b9d-109">ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="92b9d-109">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
## <a name="see-also"></a><span data-ttu-id="92b9d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92b9d-110">See Also</span></span>  
 [<span data-ttu-id="92b9d-111">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="92b9d-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
