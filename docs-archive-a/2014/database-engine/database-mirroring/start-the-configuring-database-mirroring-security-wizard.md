---
title: 啟動 [設定資料庫鏡像安全性嚮導] (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], security
- Configuring Database Mirroring Security Wizard
ms.assetid: 1c846950-0a2d-45df-b0d5-193e455f7cd5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fab3a0a48633f70a91d4e65bd31b7d3f9c314ca3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599672"
---
# <a name="start-the-configuring-database-mirroring-security-wizard-sql-server-management-studio"></a><span data-ttu-id="491dc-102">啟動設定資料庫鏡像安全性精靈 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="491dc-102">Start the Configuring Database Mirroring Security Wizard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="491dc-103">「設定資料庫鏡像安全性精靈」可用來對涉及鏡像的所有或部分伺服器執行個體，設定初始安全性設定。</span><span class="sxs-lookup"><span data-stu-id="491dc-103">The Configure Database Mirroring Security Wizard can be used to initially configure security settings at all or some server instances involved in mirroring.</span></span> <span data-ttu-id="491dc-104">這個精靈會與 **[資料庫屬性]** 對話方塊的 **[鏡像]** 頁面一起運作。</span><span class="sxs-lookup"><span data-stu-id="491dc-104">This wizard works in conjunction with the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
### <a name="to-launch-the-configure-database-mirroring-security-wizard"></a><span data-ttu-id="491dc-105">若要啟動設定資料庫鏡像安全性精靈</span><span class="sxs-lookup"><span data-stu-id="491dc-105">To launch the Configure Database Mirroring Security Wizard</span></span>  
  
1.  <span data-ttu-id="491dc-106">連接到主體伺服器執行個體後，在 [物件總管] 中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="491dc-106">After connecting to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="491dc-107">展開 **[資料庫]** ，然後選取要鏡像的資料庫。</span><span class="sxs-lookup"><span data-stu-id="491dc-107">Expand **Databases**, and select the database to be mirrored.</span></span>  
  
3.  <span data-ttu-id="491dc-108">以滑鼠右鍵按一下資料庫，選取 [工作]，然後按一下 [鏡像]。</span><span class="sxs-lookup"><span data-stu-id="491dc-108">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="491dc-109">這會開啟 [**資料庫屬性**] 對話方塊的 [[鏡像] 頁面](../../relational-databases/databases/database-properties-mirroring-page.md)。</span><span class="sxs-lookup"><span data-stu-id="491dc-109">This opens the [Mirroring Page](../../relational-databases/databases/database-properties-mirroring-page.md) of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="491dc-110">按一下 **[設定安全性]** 。</span><span class="sxs-lookup"><span data-stu-id="491dc-110">Click **Configure Security**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="491dc-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="491dc-111">See Also</span></span>  
 <span data-ttu-id="491dc-112">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="491dc-112">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="491dc-113">[資料庫屬性 &#40;鏡像頁面&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="491dc-113">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 [<span data-ttu-id="491dc-114">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="491dc-114">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
  
