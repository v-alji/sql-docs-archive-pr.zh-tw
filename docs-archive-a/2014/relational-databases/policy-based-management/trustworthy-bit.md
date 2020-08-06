---
title: Trustworthy 位元 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 062a63dd52f4641a0ddfcbc20cb9bad3cce6dc61
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593999"
---
# <a name="trustworthy-bit"></a><span data-ttu-id="c71a8-102">Trustworthy 位元</span><span class="sxs-lookup"><span data-stu-id="c71a8-102">Trustworthy Bit</span></span>
  <span data-ttu-id="c71a8-103">此規則會判斷資料庫的 dbo 角色是否指派給系統管理員 (sysadmin) 固定伺服器角色，且資料庫的 trustworthy 位元是否設定為 ON。</span><span class="sxs-lookup"><span data-stu-id="c71a8-103">This rule determines whether the dbo role for a database is assigned to the sysadmin fixed server role and the database has its trustworthy bit set to ON.</span></span>  
  
 <span data-ttu-id="c71a8-104">如果滿足這些條件，有權限的資料庫使用者可以將權限提高為系統管理員 (sysadmin) 角色。</span><span class="sxs-lookup"><span data-stu-id="c71a8-104">If these conditions are met, a privileged database user can elevate privileges to the sysadmin role.</span></span> <span data-ttu-id="c71a8-105">在這個角色中，使用者可以建立及執行危害系統的不安全組件。</span><span class="sxs-lookup"><span data-stu-id="c71a8-105">In this role, the user can create and run unsafe assemblies that compromise the system.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="c71a8-106">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="c71a8-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="c71a8-107">關閉 trustworthy 位元，或是從 dbo 資料庫角色撤銷系統管理員 (sysadmin) 權限。</span><span class="sxs-lookup"><span data-stu-id="c71a8-107">Turn off the trustworthy bit or revoke sysadmin permissions from the dbo database role.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="c71a8-108">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="c71a8-108">For More Information</span></span>  
 [<span data-ttu-id="c71a8-109">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c71a8-109">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="c71a8-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c71a8-110">See Also</span></span>  
 [<span data-ttu-id="c71a8-111">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="c71a8-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
