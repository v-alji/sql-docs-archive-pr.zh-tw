---
title: 包含見證伺服器 (設定資料庫鏡像安全性精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.inclwitness.f1
ms.assetid: f04b38a4-f4e2-4d4c-bdac-7cc70e5a5684
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 314d2205463436e2182b8d1a4cc0cc972213bd5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592200"
---
# <a name="include-witness-server-configure-database-mirroring-security-wizard"></a><span data-ttu-id="99a3a-102">包含見證伺服器 (設定資料庫鏡像安全性精靈)</span><span class="sxs-lookup"><span data-stu-id="99a3a-102">Include Witness Server (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="99a3a-103">使用此頁面，來指定您是否想要將見證伺服器包含在資料庫鏡像的這個安全性組態中。</span><span class="sxs-lookup"><span data-stu-id="99a3a-103">Use this page to specify whether you want to include a witness server in this security configuration for database mirroring.</span></span>  
  
 <span data-ttu-id="99a3a-104">**若要使用 SQL Server Management Studio 設定資料庫鏡像**</span><span class="sxs-lookup"><span data-stu-id="99a3a-104">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="99a3a-105">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="99a3a-105">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="99a3a-106">啟動設定資料庫鏡像安全性精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="99a3a-106">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="99a3a-107">選項。</span><span class="sxs-lookup"><span data-stu-id="99a3a-107">Options</span></span>  
 <span data-ttu-id="99a3a-108">**是**</span><span class="sxs-lookup"><span data-stu-id="99a3a-108">**Yes**</span></span>  
 <span data-ttu-id="99a3a-109">按一下即可將見證伺服器執行個體包含在安全性組態中。</span><span class="sxs-lookup"><span data-stu-id="99a3a-109">Click to include a witness server instance in the security configuration.</span></span> <span data-ttu-id="99a3a-110">具有自動容錯移轉的高安全性模式必須要有見證伺服器，如果主體伺服器執行個體失敗，這個見證伺服器就可以支援自動容錯移轉至鏡像伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="99a3a-110">The witness is necessary for high-safety mode with automatic failover, which supports automatic failover to the mirror server instance if the principal server instance fails.</span></span>  
  
 <span data-ttu-id="99a3a-111">**否**</span><span class="sxs-lookup"><span data-stu-id="99a3a-111">**No**</span></span>  
 <span data-ttu-id="99a3a-112">按一下即可設定不具見證的安全性。</span><span class="sxs-lookup"><span data-stu-id="99a3a-112">Click to configure security without a witness.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99a3a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99a3a-113">See Also</span></span>  
 <span data-ttu-id="99a3a-114">[資料庫屬性 &#40;鏡像頁面&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="99a3a-114">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="99a3a-115">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="99a3a-115">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="99a3a-116">資料庫鏡像見證</span><span class="sxs-lookup"><span data-stu-id="99a3a-116">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
