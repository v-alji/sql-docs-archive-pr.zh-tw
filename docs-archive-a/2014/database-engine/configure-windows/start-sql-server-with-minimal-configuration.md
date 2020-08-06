---
title: 以最低組態啟動 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- minimal configuration [SQL Server]
- starting SQL Server, minimal configuration
ms.assetid: 4d733c99-28b3-42d8-b7f6-7b943b548173
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5c78fc10be584803b438b2cd125a77400ff369b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585578"
---
# <a name="start-sql-server-with-minimal-configuration"></a><span data-ttu-id="89be1-102">以最低組態啟動 SQL Server</span><span class="sxs-lookup"><span data-stu-id="89be1-102">Start SQL Server with Minimal Configuration</span></span>
  <span data-ttu-id="89be1-103">如果因組態問題而無法啟動伺服器，則可使用最低組態啟動選項來啟動 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="89be1-103">If you have configuration problems that prevent the server from starting, you can start an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the minimal configuration startup option.</span></span> <span data-ttu-id="89be1-104">此為啟動選項 **-f**。</span><span class="sxs-lookup"><span data-stu-id="89be1-104">This is the startup option **-f**.</span></span> <span data-ttu-id="89be1-105">以最低組態啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，會自動將伺服器設定為單一使用者模式。</span><span class="sxs-lookup"><span data-stu-id="89be1-105">Starting an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with minimal configuration automatically puts the server in single-user mode.</span></span>  
  
 <span data-ttu-id="89be1-106">以最低組態模式啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時，請注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="89be1-106">When you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in minimal configuration mode, note the following:</span></span>  
  
-   <span data-ttu-id="89be1-107">只有一位使用者可以連接，而且不會執行 CHECKPOINT 處理序。</span><span class="sxs-lookup"><span data-stu-id="89be1-107">Only a single user can connect, and the CHECKPOINT process is not executed.</span></span>  
  
-   <span data-ttu-id="89be1-108">會關閉遠端存取與預先讀取 (Read-ahead) 功能。</span><span class="sxs-lookup"><span data-stu-id="89be1-108">Remote access and read-ahead are disabled.</span></span>  
  
-   <span data-ttu-id="89be1-109">不會執行啟動預存程序。</span><span class="sxs-lookup"><span data-stu-id="89be1-109">Startup stored procedures do not run.</span></span>  
  
 <span data-ttu-id="89be1-110">在伺服器以最低組態啟動後，您應該變更適當的伺服器選項值，然後將伺服器停止，再重新啟動。</span><span class="sxs-lookup"><span data-stu-id="89be1-110">After the server has been started with minimal configuration, you should change the appropriate server option value or values, stop, and then restart the server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="89be1-111">使用 **sqlcmd** 公用程式與專用管理員連接 (DAC) 連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="89be1-111">Use the **sqlcmd** utility and the dedicated administrator connection (DAC) to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="89be1-112">如果您使用一般連接，請先停止 SQL Server Agent 服務，再以最低組態模式連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="89be1-112">If you use a typical connection, stop the SQL Server Agent service before connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in minimal configuration mode.</span></span> <span data-ttu-id="89be1-113">否則，SQL Server Agent 服務會使用連接，從而將其封鎖。</span><span class="sxs-lookup"><span data-stu-id="89be1-113">Otherwise, the SQL Server Agent service uses the connection, thereby blocking it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89be1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89be1-114">See Also</span></span>  
 <span data-ttu-id="89be1-115">[啟動、停止或暫停 SQL Server Agent 服務](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md) </span><span class="sxs-lookup"><span data-stu-id="89be1-115">[Start, Stop, or Pause the SQL Server Agent Service](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md) </span></span>  
 <span data-ttu-id="89be1-116">[資料庫管理員的診斷連接](diagnostic-connection-for-database-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="89be1-116">[Diagnostic Connection for Database Administrators](diagnostic-connection-for-database-administrators.md) </span></span>  
 <span data-ttu-id="89be1-117">[sqlcmd 公用程式](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="89be1-117">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 <span data-ttu-id="89be1-118">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="89be1-118">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="89be1-119">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="89be1-119">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="89be1-120">Database Engine 服務啟動選項</span><span class="sxs-lookup"><span data-stu-id="89be1-120">Database Engine Service Startup Options</span></span>](database-engine-service-startup-options.md)  
  
  
