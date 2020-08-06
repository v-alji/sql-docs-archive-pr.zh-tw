---
title: 啟動資料庫鏡像監視器 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- monitoring database mirroring [SQL Server]
- Database Mirroring Monitor [SQL Server], starting
- database mirroring [SQL Server], monitoring
ms.assetid: 53165335-97ca-4f88-8e78-22f1839dee98
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67c7b393b28d4d400535281c18c637146a5d8da7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584726"
---
# <a name="start-database-mirroring-monitor-sql-server-management-studio"></a><span data-ttu-id="38d88-102">啟動資料庫鏡像監視器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="38d88-102">Start Database Mirroring Monitor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="38d88-103">資料庫鏡像監視器是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 監視器的一部分，是從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]啟動。</span><span class="sxs-lookup"><span data-stu-id="38d88-103">The Database Mirroring Monitor is part of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Monitor, which is launched from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38d88-104">並非所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本都可使用資料庫鏡像監視器。</span><span class="sxs-lookup"><span data-stu-id="38d88-104">Database Mirroring Monitor is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="38d88-105">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="38d88-105">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
### <a name="to-launch-the-database-mirroring-monitor"></a><span data-ttu-id="38d88-106">啟動資料庫鏡像監視器</span><span class="sxs-lookup"><span data-stu-id="38d88-106">To launch the Database Mirroring Monitor</span></span>  
  
1.  <span data-ttu-id="38d88-107">連接到主體伺服器執行個體後，在 [物件總管] 中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="38d88-107">After connecting to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="38d88-108">展開 [資料庫]\*\*\*\*，然後選取要監視的資料庫。</span><span class="sxs-lookup"><span data-stu-id="38d88-108">Expand **Databases**, and select the database to be monitored.</span></span>  
  
3.  <span data-ttu-id="38d88-109">以滑鼠右鍵按一下資料庫，選取 [工作]\*\*\*\*，再按一下 [啟動資料庫鏡像監視器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38d88-109">Right-click the database, select **Tasks**, and then click **Launch Database Mirroring Monitor**.</span></span>  
  
4.  <span data-ttu-id="38d88-110">在 [資料庫鏡像監視器]\*\*\*\* 對話方塊中，按一下 [註冊鏡像資料庫]\*\*\*\* 以註冊一或多個鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="38d88-110">In the **Database Mirroring Monitor** dialog box, click **Register Mirrored Database** to register one or more mirrored database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="38d88-111">當您在某個夥伴註冊資料庫時，就會在另一個夥伴自動註冊資料庫。</span><span class="sxs-lookup"><span data-stu-id="38d88-111">When you register a database at one partner, the database is automatically registered at the other partner.</span></span> <span data-ttu-id="38d88-112">如果監視器已經有其他夥伴執行個體的連接認證時，就會使用這些認證進行連接，</span><span class="sxs-lookup"><span data-stu-id="38d88-112">If the monitor already has connection credentials for the other partner instance, those are used to connect.</span></span> <span data-ttu-id="38d88-113">否則監視器會嘗試使用 Windows 驗證進行連接。</span><span class="sxs-lookup"><span data-stu-id="38d88-113">Otherwise the monitor attempts to connect using Windows Authentication.</span></span> <span data-ttu-id="38d88-114">如果您想要變更用來連接至任一伺服器執行個體的認證，請按一下 [當我按一下確定時，即顯示管理伺服器連接對話方塊]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38d88-114">If you want to change the credentials used to connect to either server instance, click **Show the Manage Server Connections dialog box when I click OK**.</span></span>  
  
 <span data-ttu-id="38d88-115">如需資料庫鏡像監視器的詳細資訊，請參閱[資料庫鏡像監視器概觀](database-mirroring-monitor-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="38d88-115">For more information about Database Mirroring Monitor, see [Database Mirroring Monitor Overview](database-mirroring-monitor-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d88-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38d88-116">See Also</span></span>  
 <span data-ttu-id="38d88-117">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="38d88-117">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="38d88-118">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="38d88-118">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
  
