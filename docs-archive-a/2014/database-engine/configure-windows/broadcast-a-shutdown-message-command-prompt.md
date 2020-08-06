---
title: 廣播關機訊息 (命令提示字元) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, stopping
- named instances [SQL Server], broadcasting shutdown messages
- shutdown message broadcast
- broadcasting shutdown message
- command prompt [SQL Server], broadcasting shutdown messages
- default instances [SQL Server], broadcasting shutdown messages
- stopping SQL Server
ms.assetid: 9f20ccd5-d952-431d-ba12-339911af9430
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 540baada4a78d7b5caf54cbabb9196ce5a79780e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701881"
---
# <a name="broadcast-a-shutdown-message-command-prompt"></a><span data-ttu-id="69343-102">廣播關機訊息 (命令提示字元)</span><span class="sxs-lookup"><span data-stu-id="69343-102">Broadcast a Shutdown Message (Command Prompt)</span></span>
  <span data-ttu-id="69343-103">本主題描述如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中使用 **net send** 命令廣播關機訊息。</span><span class="sxs-lookup"><span data-stu-id="69343-103">This topic describes how to broadcast a shutdown message in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using the **net send** command.</span></span> <span data-ttu-id="69343-104">在訊息中包含要停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的時間，讓使用者能夠完成其工作。</span><span class="sxs-lookup"><span data-stu-id="69343-104">In the message, include the time the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will be stopped so that users can finish their tasks.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-broadcast-a-shutdown-message"></a><span data-ttu-id="69343-105">若要廣播關閉訊息</span><span class="sxs-lookup"><span data-stu-id="69343-105">To broadcast a shutdown message</span></span>  
  
1.  <span data-ttu-id="69343-106">在命令提示字元下，輸入：</span><span class="sxs-lookup"><span data-stu-id="69343-106">From a command prompt, enter:</span></span>  
  
     <span data-ttu-id="69343-107">**net send /users "message"**</span><span class="sxs-lookup"><span data-stu-id="69343-107">**net send /users "message"**</span></span>  
  
     <span data-ttu-id="69343-108">**/users** 選項可指定將訊息傳送給連接到伺服器的所有使用者。</span><span class="sxs-lookup"><span data-stu-id="69343-108">The **/users** option specifies that the message be sent to all users connected to the server</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69343-109">**net send** 命令需要 Messenger 服務同時在傳送與接收電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="69343-109">The **net send** command requires the messenger service to be running on both the sending and the receiving computers.</span></span> <span data-ttu-id="69343-110">Windows Server 2003 預設會停用 Messenger 服務。</span><span class="sxs-lookup"><span data-stu-id="69343-110">The messenger service is disabled by default on Windows Server 2003.</span></span> <span data-ttu-id="69343-111">如需有關 **net send**的詳細資訊，請參閱 Windows 文件。</span><span class="sxs-lookup"><span data-stu-id="69343-111">For information about **net send**, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="69343-112">在您的網路上，使用電子郵件或電話來連絡使用者可能會更加適合。</span><span class="sxs-lookup"><span data-stu-id="69343-112">On your network, it may be more appropriate to contact users by e-mail or the telephone.</span></span> <span data-ttu-id="69343-113">若要判斷目前有哪些使用者連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，請使用活動監視器。</span><span class="sxs-lookup"><span data-stu-id="69343-113">To determine which users are currently connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], use the Activity Monitor.</span></span> <span data-ttu-id="69343-114">如需活動監視器的相關資訊，請參閱[活動監視器](../../relational-databases/performance-monitor/activity-monitor.md)和[開啟活動監視器 &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="69343-114">For information on the Activity Monitor, see [Activity Monitor](../../relational-databases/performance-monitor/activity-monitor.md) and [Open Activity Monitor &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69343-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69343-115">See Also</span></span>  
 [<span data-ttu-id="69343-116">啟動、停止、暫停、繼續、重新啟動 Database Engine、SQL Server Agent 或 SQL Server Browser 服務</span><span class="sxs-lookup"><span data-stu-id="69343-116">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](start-stop-pause-resume-restart-sql-server-services.md)  
  
  
