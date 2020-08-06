---
title: 使用 Database Mail 取代 SQL Mail | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b08df7be-d8be-4184-a661-38ec0ac85cd1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a6a957b65975645bdeb9f55faee4e650b53718b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593988"
---
# <a name="use-database-mail-instead-of-sql-mail"></a><span data-ttu-id="0e392-102">使用 Database Mail 而非 SQL Mail</span><span class="sxs-lookup"><span data-stu-id="0e392-102">Use Database Mail Instead of SQL Mail</span></span>
  <span data-ttu-id="0e392-103">此規則會檢查 sys.configurations 目錄檢視，以判斷 SQL Mail XP 的整個伺服器組態選項是否設定為 ON。</span><span class="sxs-lookup"><span data-stu-id="0e392-103">This rule checks the sys.configurations catalog view to determine whether the SQL Mail XPs server-wide configuration option is set to ON.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="0e392-104">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="0e392-104">Best Practices Recommendations</span></span>  
 <span data-ttu-id="0e392-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的未來版本將移除 SQL Mail。</span><span class="sxs-lookup"><span data-stu-id="0e392-105">SQL Mail will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0e392-106">請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0e392-106">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span> <span data-ttu-id="0e392-107">若要傳送郵件，請使用 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="0e392-107">To send mail, use Database Mail.</span></span>  
  
 <span data-ttu-id="0e392-108">SQL Mail 會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的同處理序執行。</span><span class="sxs-lookup"><span data-stu-id="0e392-108">SQL Mail runs in-process to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="0e392-109">如果 SQL Mail 關閉，伺服器也會關閉。</span><span class="sxs-lookup"><span data-stu-id="0e392-109">If SQL Mail goes down, so does the server.</span></span> <span data-ttu-id="0e392-110">Database Mail 會在不同處理序的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 外部執行，它可以擴充，而且不需要在實際執行伺服器上安裝延伸的 MAPI 用戶端元件。</span><span class="sxs-lookup"><span data-stu-id="0e392-110">Database Mail runs outside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a separate process, is scalable, and does not require Extended MAPI client components to be installed on the production server.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="0e392-111">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="0e392-111">For More Information</span></span>  
 [<span data-ttu-id="0e392-112">Database Mail</span><span class="sxs-lookup"><span data-stu-id="0e392-112">Database Mail</span></span>](../database-mail/database-mail.md)  
  
## <a name="see-also"></a><span data-ttu-id="0e392-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e392-113">See Also</span></span>  
 [<span data-ttu-id="0e392-114">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="0e392-114">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
