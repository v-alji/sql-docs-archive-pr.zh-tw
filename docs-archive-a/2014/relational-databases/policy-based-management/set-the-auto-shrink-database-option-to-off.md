---
title: 將 AUTO_SHRINK 資料庫選項設定為 OFF | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 16403850-d745-4754-b84f-5f01aaecd24e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 42d79ed13a691c3d39a28e7ab35a740a9f613fac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708205"
---
# <a name="set-the-auto_shrink-database-option-to-off"></a><span data-ttu-id="4e904-102">將 AUTO_SHRINK 資料庫選項設定為 OFF</span><span class="sxs-lookup"><span data-stu-id="4e904-102">Set the AUTO_SHRINK Database Option to OFF</span></span>
  <span data-ttu-id="4e904-103">這個規則會檢查 AUTO_SHRINK 資料庫選項是否設定為 OFF。</span><span class="sxs-lookup"><span data-stu-id="4e904-103">This rule checks whether the AUTO_SHRINK database option is set to OFF.</span></span> <span data-ttu-id="4e904-104">通常壓縮和展開資料庫可能會導致實體片段。</span><span class="sxs-lookup"><span data-stu-id="4e904-104">Frequently shrinking and expanding a database can lead to physical fragmentation.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="4e904-105">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="4e904-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="4e904-106">將 AUTO_SHRINK 資料庫選項設定為 OFF。</span><span class="sxs-lookup"><span data-stu-id="4e904-106">Set the AUTO_SHRINK database option to OFF.</span></span> <span data-ttu-id="4e904-107">如果您知道您所回收的空間不需要在將來使用，您可以手動壓縮資料庫來回收該空間。</span><span class="sxs-lookup"><span data-stu-id="4e904-107">If you know that the space that you are reclaiming will not be needed in the future, you can reclaim the space by manually shrinking the database.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="4e904-108">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="4e904-108">For More Information</span></span>  
 <span data-ttu-id="4e904-109">Microsoft 知識庫文件 [315512](https://go.microsoft.com/fwlink/?linkid=117750)</span><span class="sxs-lookup"><span data-stu-id="4e904-109">Microsoft Knowledge Base article [315512](https://go.microsoft.com/fwlink/?linkid=117750)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e904-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e904-110">See Also</span></span>  
 [<span data-ttu-id="4e904-111">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="4e904-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
