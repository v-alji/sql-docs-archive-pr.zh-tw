---
title: 伺服器 public 權限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7913c4715f47b8105b72b1c817dbe77e52d40539
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708217"
---
# <a name="server-public-permissions"></a><span data-ttu-id="86095-102">伺服器 public 權限</span><span class="sxs-lookup"><span data-stu-id="86095-102">Server public Permissions</span></span>
  <span data-ttu-id="86095-103">此規則會判斷 public 伺服器角色是否有伺服器權限。</span><span class="sxs-lookup"><span data-stu-id="86095-103">This rule determines whether the public server role has server permissions.</span></span> <span data-ttu-id="86095-104">伺服器上建立的每一個登入都是 public 伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="86095-104">Every login that is created on the server is a member of the public server role.</span></span> <span data-ttu-id="86095-105">如果符合這個條件，伺服器上的每個登入都具有伺服器權限。</span><span class="sxs-lookup"><span data-stu-id="86095-105">If this condition is met, every login on the server will have server permissions.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="86095-106">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="86095-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="86095-107">請勿將伺服器權限授與給伺服器 public 角色。</span><span class="sxs-lookup"><span data-stu-id="86095-107">Do not grant server permissions to the server public role.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="86095-108">在安裝程式完成之後， **PUBLIC**角色具有 `CONNECT` 所有端點的許可權，但**專用管理員連接**除外。</span><span class="sxs-lookup"><span data-stu-id="86095-108">After setup completes the **PUBLIC** role has `CONNECT` permission on all the endpoints except the **Dedicated Admin Connection**.</span></span> <span data-ttu-id="86095-109">這是正常狀況，通常不應該變更</span><span class="sxs-lookup"><span data-stu-id="86095-109">This is normal and should not be normally changed.</span></span> <span data-ttu-id="86095-110">(存取權是使用建立新登入時自動授與的 `CONNECT SQL` 權限來控制)。</span><span class="sxs-lookup"><span data-stu-id="86095-110">(Access is controlled by using the `CONNECT SQL` permission which is automatically granted when new logins are created.)</span></span>  
  
### <a name="for-more-information"></a><span data-ttu-id="86095-111">取得詳細資訊</span><span class="sxs-lookup"><span data-stu-id="86095-111">For more information</span></span>  
 [<span data-ttu-id="86095-112">保護 SQL Server 的安全</span><span class="sxs-lookup"><span data-stu-id="86095-112">Securing SQL Server</span></span>](../security/securing-sql-server.md)  
  
  
