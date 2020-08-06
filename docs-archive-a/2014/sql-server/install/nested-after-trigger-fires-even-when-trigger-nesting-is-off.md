---
title: 即使觸發程式的嵌套已關閉，也會引發 Nested AFTER 觸發程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- DML triggers, nested
- nested triggers option
- triggers [SQL Server], nested
ms.assetid: 94d72960-676e-40d9-81bc-08bffe778110
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f91c04e8d69880b451c1479e2907cd1910e8f9c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710177"
---
# <a name="nested-after-trigger-fires-even-when-trigger-nesting-is-off"></a><span data-ttu-id="2276a-102">即使觸發程序巢狀結構是 OFF，也會引發巢狀 AFTER 觸發程序</span><span class="sxs-lookup"><span data-stu-id="2276a-102">Nested AFTER trigger fires even when trigger nesting is OFF</span></span>
  <span data-ttu-id="2276a-103">Upgrade Advisor 偵測到在一個或多個資料表上所定義的 INSTEAD OF 觸發程序內，有巢狀的 AFTER 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="2276a-103">Upgrade Advisor detected an AFTER trigger nested inside an INSTEAD OF trigger that is defined on one or more tables.</span></span> <span data-ttu-id="2276a-104">即使 `nested triggers` 伺服器組態選項設定為 0，巢狀 AFTER 觸發程序仍可能引發。</span><span class="sxs-lookup"><span data-stu-id="2276a-104">Nested AFTER triggers may fire even when the `nested triggers` server configuration option is set to 0.</span></span>  
  
## <a name="component"></a><span data-ttu-id="2276a-105">元件</span><span class="sxs-lookup"><span data-stu-id="2276a-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="2276a-106">描述</span><span class="sxs-lookup"><span data-stu-id="2276a-106">Description</span></span>  
 <span data-ttu-id="2276a-107">即使 `nested triggers` 伺服器組態選項設為 0，INSTEAD OF 觸發程序內部的第一個巢狀 AFTER 觸發程序仍會引發。</span><span class="sxs-lookup"><span data-stu-id="2276a-107">The first AFTER trigger nested inside an INSTEAD OF trigger fires even if the `nested triggers` server configuration option is set to 0.</span></span> <span data-ttu-id="2276a-108">不過，在此設定下，後續的 AFTER 觸發程序不會引發。</span><span class="sxs-lookup"><span data-stu-id="2276a-108">However, under this setting, subsequent AFTER triggers do not fire.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="2276a-109">更正動作</span><span class="sxs-lookup"><span data-stu-id="2276a-109">Corrective Action</span></span>  
 <span data-ttu-id="2276a-110">請檢閱應用程式中是否有巢狀觸發程序，以判斷當 `nested triggers` 伺服器組態選項設定為 0 時，這些應用程式的新行為是否仍符合您的商務規則，然後進行適當的修改。</span><span class="sxs-lookup"><span data-stu-id="2276a-110">Review your applications for nested triggers to determine whether the applications still comply with your business rules with regard to this new behavior when the `nested triggers` server configuration option is set to 0, and then make appropriate modifications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2276a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2276a-111">See Also</span></span>  
 <span data-ttu-id="2276a-112">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="2276a-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="2276a-113">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="2276a-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
