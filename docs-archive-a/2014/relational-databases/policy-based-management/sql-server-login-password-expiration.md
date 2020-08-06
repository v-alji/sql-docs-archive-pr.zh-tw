---
title: SQL Server 登入密碼逾期 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7e3bf9da-a436-433d-847a-47c30428cad3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 678e8e9c6b567014bdd49e89d043165bc48d168a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585334"
---
# <a name="sql-server-login-password-expiration"></a><span data-ttu-id="c04c7-102">SQL Server 登入密碼逾期</span><span class="sxs-lookup"><span data-stu-id="c04c7-102">SQL Server Login Password Expiration</span></span>
  <span data-ttu-id="c04c7-103">此規則會檢查每一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入的「密碼逾期」是否已啟用。</span><span class="sxs-lookup"><span data-stu-id="c04c7-103">This rule checks whether "Password expiration" of each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login is enabled.</span></span> <span data-ttu-id="c04c7-104">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證已啟用，而且作業系統版本比 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]舊，則攻擊者可能會重複利用已知的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入密碼。</span><span class="sxs-lookup"><span data-stu-id="c04c7-104">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is enabled and if the operating system version is earlier than [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], an attacker could repeatedly exploit a known [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login password.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="c04c7-105">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="c04c7-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="c04c7-106">我們建議您將作業系統升級到 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c04c7-106">We recommend that you upgrade the operating system to [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)].</span></span>  
  
 <span data-ttu-id="c04c7-107">如果您的環境中不需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，請使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c04c7-107">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is not required in your environment, use Windows Authentication.</span></span> <span data-ttu-id="c04c7-108">如需詳細資訊，請參閱 [選擇驗證模式](../security/choose-an-authentication-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="c04c7-108">For more information, see [Choose an Authentication Mode](../security/choose-an-authentication-mode.md).</span></span>  
  
 <span data-ttu-id="c04c7-109">針對所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入啟用「密碼逾期」。</span><span class="sxs-lookup"><span data-stu-id="c04c7-109">Enable "Password expiration" for all the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span> <span data-ttu-id="c04c7-110">使用 [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) 來為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入設定密碼原則。</span><span class="sxs-lookup"><span data-stu-id="c04c7-110">Use [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) to configure the password policy for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="c04c7-111">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="c04c7-111">For More Information</span></span>  
 [<span data-ttu-id="c04c7-112">密碼原則</span><span class="sxs-lookup"><span data-stu-id="c04c7-112">Password Policy</span></span>](../security/password-policy.md)  
  
## <a name="see-also"></a><span data-ttu-id="c04c7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c04c7-113">See Also</span></span>  
 [<span data-ttu-id="c04c7-114">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="c04c7-114">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
