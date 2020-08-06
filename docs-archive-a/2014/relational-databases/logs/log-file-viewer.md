---
title: 記錄檔檢視器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer
ms.assetid: a4ea7fc8-1cb2-4c98-bc86-8991c5e748b2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5139a32838070b817fce3bccf22b9fe08b5012e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594539"
---
# <a name="log-file-viewer"></a><span data-ttu-id="92d58-102">記錄檔檢視器</span><span class="sxs-lookup"><span data-stu-id="92d58-102">Log File Viewer</span></span>
  <span data-ttu-id="92d58-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的記錄檔檢視器是用於存取有關記錄檔中所擷取之錯誤和事件的資訊。</span><span class="sxs-lookup"><span data-stu-id="92d58-103">Log File Viewer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is used to access information about errors and events that are captured in log files.</span></span>  
  
## <a name="benefits-of-using-log-file-viewer"></a><span data-ttu-id="92d58-104">記錄檔檢視器的優點</span><span class="sxs-lookup"><span data-stu-id="92d58-104">Benefits of using Log File Viewer</span></span>  
 <span data-ttu-id="92d58-105">當目標執行個體已離線或無法啟動時，您可以從本機或遠端 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="92d58-105">You can view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files from a local or remote instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] when the target instance is offline or cannot start.</span></span> <span data-ttu-id="92d58-106">您可以從 [已註冊的伺服器] 存取離線記錄檔，也可以透過 WMI 和 WQL (WMI 查詢語言) 查詢以程式設計方式存取。</span><span class="sxs-lookup"><span data-stu-id="92d58-106">You can access the offline log files from Registered Servers, or programmatically through WMI and WQL (WMI Query Language) queries.</span></span> <span data-ttu-id="92d58-107">如需詳細資訊，請參閱 [檢視離線記錄檔](view-offline-log-files.md)。</span><span class="sxs-lookup"><span data-stu-id="92d58-107">For more information, see [View Offline Log Files](view-offline-log-files.md).</span></span> <span data-ttu-id="92d58-108">下列是您可以使用記錄檔檢視器存取的記錄檔類型：</span><span class="sxs-lookup"><span data-stu-id="92d58-108">Following are the types of log files you can access using Log File Viewer:</span></span>  
  
-   <span data-ttu-id="92d58-109">稽核集合</span><span class="sxs-lookup"><span data-stu-id="92d58-109">Audit Collection</span></span>  
  
-   <span data-ttu-id="92d58-110">資料收集</span><span class="sxs-lookup"><span data-stu-id="92d58-110">Data Collection</span></span>  
  
-   <span data-ttu-id="92d58-111">Database Mail</span><span class="sxs-lookup"><span data-stu-id="92d58-111">Database Mail</span></span>  
  
-   <span data-ttu-id="92d58-112">作業記錄</span><span class="sxs-lookup"><span data-stu-id="92d58-112">Job History</span></span>  
  
-   <span data-ttu-id="92d58-113">維護計畫</span><span class="sxs-lookup"><span data-stu-id="92d58-113">Maintenance Plans</span></span>  
  
-   <span data-ttu-id="92d58-114">遠端維護計畫</span><span class="sxs-lookup"><span data-stu-id="92d58-114">Remote Maintenance Plans</span></span>  
  
-   <span data-ttu-id="92d58-115">SQL Server</span><span class="sxs-lookup"><span data-stu-id="92d58-115">SQL Server</span></span>  
  
-   <span data-ttu-id="92d58-116">SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="92d58-116">SQL Server Agent</span></span>  
  
-   <span data-ttu-id="92d58-117">Windows NT (這些是也可以從事件檢視器存取的 Windows 事件)。</span><span class="sxs-lookup"><span data-stu-id="92d58-117">Windows NT (These are Windows events that can also be accessed from Event Viewer.)</span></span>  
  
## <a name="log-file-viewer-tasks"></a><span data-ttu-id="92d58-118">記錄檔檢視器工作</span><span class="sxs-lookup"><span data-stu-id="92d58-118">Log File Viewer Tasks</span></span>  
  
|<span data-ttu-id="92d58-119">工作描述</span><span class="sxs-lookup"><span data-stu-id="92d58-119">Task Description</span></span>|<span data-ttu-id="92d58-120">主題</span><span class="sxs-lookup"><span data-stu-id="92d58-120">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="92d58-121">描述如何根據想要檢視的資訊來開啟記錄檔檢視器。</span><span class="sxs-lookup"><span data-stu-id="92d58-121">Describes how to open Log File Viewer depending on the information that you want to view.</span></span>|[<span data-ttu-id="92d58-122">開啟記錄檔檢視器</span><span class="sxs-lookup"><span data-stu-id="92d58-122">Open Log File Viewer</span></span>](open-log-file-viewer.md)|  
|<span data-ttu-id="92d58-123">描述如何透過已註冊的伺服器來檢視離線記錄檔，以及如何驗證 WMI 權限。</span><span class="sxs-lookup"><span data-stu-id="92d58-123">Describes how to view offline log files through registered servers and how to verify WMI permissions.</span></span>|[<span data-ttu-id="92d58-124">檢視離線記錄檔</span><span class="sxs-lookup"><span data-stu-id="92d58-124">View Offline Log Files</span></span>](view-offline-log-files.md)|  
|<span data-ttu-id="92d58-125">提供記錄檔檢視器 F1 説明。</span><span class="sxs-lookup"><span data-stu-id="92d58-125">Provides Log File Viewer F1 Help.</span></span>|[<span data-ttu-id="92d58-126">記錄檔檢視器 F1 說明</span><span class="sxs-lookup"><span data-stu-id="92d58-126">Log File Viewer F1 Help</span></span>](log-file-viewer-f1-help.md)|  
  
## <a name="see-also"></a><span data-ttu-id="92d58-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92d58-127">See Also</span></span>  
 <span data-ttu-id="92d58-128">[SQL Server Audit &#40;Database Engine&#41;](../security/auditing/sql-server-audit-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="92d58-128">[SQL Server Audit &#40;Database Engine&#41;](../security/auditing/sql-server-audit-database-engine.md) </span></span>  
 [<span data-ttu-id="92d58-129">SQL Server Agent 錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="92d58-129">SQL Server Agent Error Log</span></span>](../../ssms/agent/sql-server-agent-error-log.md)  
  
  
