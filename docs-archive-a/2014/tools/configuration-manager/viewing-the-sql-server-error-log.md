---
title: 查看 SQL Server 錯誤記錄檔 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cycling SQL Server error log
- viewing SQL Server error log
- errors [SQL Server], logs
- SQL Server error log
- displaying SQL Server error log
- logs [SQL Server], SQL Server error logs
ms.assetid: 6908c21a-65e3-458f-a272-fee256d86448
author: stevestein
ms.author: sstein
ms.openlocfilehash: 822ae4fba589f005aaee41857a9db3388a309254
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584218"
---
# <a name="viewing-the-sql-server-error-log"></a><span data-ttu-id="8dbc1-102">檢視 SQL Server 錯誤記錄</span><span class="sxs-lookup"><span data-stu-id="8dbc1-102">Viewing the SQL Server Error Log</span></span>
  <span data-ttu-id="8dbc1-103">您可以檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，確定處理序已順利完成 (例如，備份與還原作業、批次命令或其他指令碼和處理序)。</span><span class="sxs-lookup"><span data-stu-id="8dbc1-103">View the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to ensure that processes have completed successfully (for example, backup and restore operations, batch commands, or other scripts and processes).</span></span> <span data-ttu-id="8dbc1-104">這有助於偵測任何目前的或潛在的問題區域，包括自動復原訊息 (尤其是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體已停止又重新啟動時)、核心訊息或其他伺服器層級的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="8dbc1-104">This can be helpful to detect any current or potential problem areas, including automatic recovery messages (particularly if an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been stopped and restarted), kernel messages, or other server-level error messages.</span></span>  
  
 <span data-ttu-id="8dbc1-105">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或任何文字編輯器來檢視 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="8dbc1-105">View the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or any text editor.</span></span> <span data-ttu-id="8dbc1-106">如需有關如何檢視錯誤記錄檔的詳細資訊，請參閱＜ [Open Log File Viewer](../../relational-databases/logs/log-file-viewer.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8dbc1-106">For more information about how to view the error log, see [Open Log File Viewer](../../relational-databases/logs/log-file-viewer.md).</span></span> <span data-ttu-id="8dbc1-107">根據預設，錯誤記錄檔是位於 `Program Files\Microsoft SQL Server\MSSQL.`*n*`\MSSQL\LOG\ERRORLOG` 和 `ERRORLOG.`*n* 檔案中。</span><span class="sxs-lookup"><span data-stu-id="8dbc1-107">By default, the error log is located at `Program Files\Microsoft SQL Server\MSSQL.`*n*`\MSSQL\LOG\ERRORLOG` and `ERRORLOG.`*n* files.</span></span>  
  
 <span data-ttu-id="8dbc1-108">每次啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時，就會建立新的錯誤記錄檔，不過， [sp_cycle_errorlog](/sql/relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql) 系統預存程序可用來循環錯誤記錄檔，而不必重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="8dbc1-108">A new error log is created each time an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started, although the [sp_cycle_errorlog](/sql/relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql) system stored procedure can be used to cycle the error log files without having to restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8dbc1-109">通常， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會保留前 6 個記錄檔的備份，並提供副檔名 .1 給最新的記錄檔備份，提供副檔名 .2 給第二新的備份...依此類推。</span><span class="sxs-lookup"><span data-stu-id="8dbc1-109">Typically, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retains backups of the previous six logs and gives the most recent log backup the extension .1, the second most recent the extension .2, and so on.</span></span> <span data-ttu-id="8dbc1-110">目前的錯誤記錄檔並沒有副檔名。</span><span class="sxs-lookup"><span data-stu-id="8dbc1-110">The current error log has no extension.</span></span>  
  
 <span data-ttu-id="8dbc1-111">請注意，您也可以在離線或無法啟動的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="8dbc1-111">Be aware that you can also view the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log on instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are offline or cannot start.</span></span> <span data-ttu-id="8dbc1-112">如需詳細資訊，請參閱 [檢視離線記錄檔](../../relational-databases/logs/view-offline-log-files.md)。</span><span class="sxs-lookup"><span data-stu-id="8dbc1-112">For more information, see [View Offline Log Files](../../relational-databases/logs/view-offline-log-files.md).</span></span>  
  
  
