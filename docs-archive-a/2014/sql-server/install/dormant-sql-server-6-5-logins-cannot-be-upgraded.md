---
title: 無法升級休眠 SQL Server 6.5 登入 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- passwords [SQL Server], dormant logins
- dormant logins
- logins [SQL Server], upgrading dormant logins
- identifying dormant logins
- password hashes [SQL Server]
ms.assetid: ebe18a74-0375-4df4-b894-239f8fdabb64
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f78bca9bf2b99b2ab6f530613b64bc0e46c4001c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595481"
---
# <a name="dormant-sql-server-65-logins-cannot-be-upgraded"></a><span data-ttu-id="0ed53-102">無法升級休眠 SQL Server 6.5 登入</span><span class="sxs-lookup"><span data-stu-id="0ed53-102">Dormant SQL Server 6.5 logins cannot be upgraded</span></span>
  <span data-ttu-id="0ed53-103">Upgrade Advisor 偵測到密碼無法直接升級到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="0ed53-103">Upgrade Advisor detected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login whose password cannot be directly upgraded to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="0ed53-104">若要啟用這項登入，您必須重設其密碼。</span><span class="sxs-lookup"><span data-stu-id="0ed53-104">To enable this login, you must reset its password.</span></span> <span data-ttu-id="0ed53-105">您可以使用 ALTER LOGIN 來重設密碼。</span><span class="sxs-lookup"><span data-stu-id="0ed53-105">You can reset the password by using ALTER LOGIN.</span></span>  
  
```  
ALTER LOGIN <login name> WITH PASSWORD = '<new password>' MUST_CHANGE  
```  
  
 <span data-ttu-id="0ed53-106">除非已停用原則檢查，否則，將根據系統的密碼複雜性原則來驗證新密碼。</span><span class="sxs-lookup"><span data-stu-id="0ed53-106">The new password will be validated against your system's password complexity policy, unless policy checking is disabled.</span></span> <span data-ttu-id="0ed53-107">建議您使用複雜密碼，而且不停用原則檢查。</span><span class="sxs-lookup"><span data-stu-id="0ed53-107">We recommend that you use complex passwords and not disable policy checking.</span></span> <span data-ttu-id="0ed53-108">MUST_CHANGE 選項會強制使用者選取新密碼。</span><span class="sxs-lookup"><span data-stu-id="0ed53-108">The MUST_CHANGE option forces the user to select a new password.</span></span> <span data-ttu-id="0ed53-109">雖然這不是必要的條件，但建議您這麼做。</span><span class="sxs-lookup"><span data-stu-id="0ed53-109">This is not required, but it is recommended.</span></span>  
  
 <span data-ttu-id="0ed53-110">您可以使用下列查詢來識別休眠登入：</span><span class="sxs-lookup"><span data-stu-id="0ed53-110">You can identify dormant logins by using the following query:</span></span>  
  
```  
SELECT * FROM sysxlogins WHERE (xstatus & 2048) = 2048;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ed53-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ed53-111">See Also</span></span>  
 <span data-ttu-id="0ed53-112">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="0ed53-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="0ed53-113">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="0ed53-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
