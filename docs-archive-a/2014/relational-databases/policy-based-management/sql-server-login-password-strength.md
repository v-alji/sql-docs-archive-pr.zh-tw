---
title: SQL Server 登入密碼強度 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b0862c3a-926b-490c-a37f-382e50146a3e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5534748fbbf810539f2dcfc22239e4b987cf0f77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687758"
---
# <a name="sql-server-login-password-strength"></a><span data-ttu-id="86597-102">SQL Server 登入密碼強度</span><span class="sxs-lookup"><span data-stu-id="86597-102">SQL Server Login Password Strength</span></span>
  <span data-ttu-id="86597-103">此規則會檢查每一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入的「強制執行密碼原則」是否已啟用。</span><span class="sxs-lookup"><span data-stu-id="86597-103">This rule checks whether "Enforce password policy" of each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login is enabled.</span></span> <span data-ttu-id="86597-104">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證已啟用，而且作業系統版本比 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]舊，則攻擊者可能會重複利用已知的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入密碼。</span><span class="sxs-lookup"><span data-stu-id="86597-104">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is enabled and if the operating system version is earlier than [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], an attacker could repeatedly exploit a known [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login password.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="86597-105">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="86597-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="86597-106">我們建議您將作業系統升級到 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="86597-106">We recommend that you upgrade the operating system to [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)].</span></span>  
  
 <span data-ttu-id="86597-107">如果您的環境中不需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，請使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="86597-107">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is not required in your environment, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="86597-108">針對所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入啟用「強制執行密碼原則」。</span><span class="sxs-lookup"><span data-stu-id="86597-108">Enable "Enforce password policy" for all the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span> <span data-ttu-id="86597-109">使用 [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) 來為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入設定密碼原則。</span><span class="sxs-lookup"><span data-stu-id="86597-109">Use [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) to configure the password policy for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="86597-110">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="86597-110">For More Information</span></span>  
 [<span data-ttu-id="86597-111">密碼原則</span><span class="sxs-lookup"><span data-stu-id="86597-111">Password Policy</span></span>](../security/password-policy.md)  
  
## <a name="see-also"></a><span data-ttu-id="86597-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86597-112">See Also</span></span>  
 [<span data-ttu-id="86597-113">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="86597-113">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
