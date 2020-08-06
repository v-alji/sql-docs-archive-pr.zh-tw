---
title: 監視錯誤記錄檔 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server]
- database performance [SQL Server], errors
- Windows application logs [SQL Server]
- monitoring performance [SQL Server], errors
- server performance [SQL Server], errors
- comparing error and application log output
- errors [SQL Server], logs
- tuning databases [SQL Server], errors
- database monitoring [SQL Server], errors
- SQL Server error log
- logs [SQL Server], SQL Server error logs
- error logs [SQL Server]
- logs [SQL Server], Windows application logs
ms.assetid: e250336b-0695-44f6-a42f-23222f94e377
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2a47891599dbe735bd437f5239c73bfd34c422ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595340"
---
# <a name="monitoring-the-error-logs"></a><span data-ttu-id="2719a-102">監視錯誤記錄</span><span class="sxs-lookup"><span data-stu-id="2719a-102">Monitoring the Error Logs</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2719a-103">將特定系統事件和使用者自訂事件記錄到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 應用程式記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="2719a-103">logs certain system events and user-defined events to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application log.</span></span> <span data-ttu-id="2719a-104">這兩種記錄檔都會自動替所有記錄的事件加入時間戳記。</span><span class="sxs-lookup"><span data-stu-id="2719a-104">Both logs automatically timestamp all recorded events.</span></span> <span data-ttu-id="2719a-105">請使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔中的資訊來解決 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的相關問題。</span><span class="sxs-lookup"><span data-stu-id="2719a-105">Use the information in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to troubleshoot problems related to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2719a-106">Windows 應用程式記錄檔可針對 Windows 作業系統上所發生的事件，以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 中的事件，提供整體描述。</span><span class="sxs-lookup"><span data-stu-id="2719a-106">The Windows application log provides an overall picture of events that occur on the Windows operating system, as well as events in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="2719a-107">使用「Windows 事件檢視器」可檢視 Windows 應用程式記錄檔，以及篩選資訊。</span><span class="sxs-lookup"><span data-stu-id="2719a-107">Use the Windows Event Viewer to view the Windows application log and to filter the information.</span></span> <span data-ttu-id="2719a-108">例如，您可以篩選事件，例如資訊、警告、錯誤、成功稽核與失敗稽核。</span><span class="sxs-lookup"><span data-stu-id="2719a-108">For example, you can filter events, such as information, warning, error, success audit, and failure audit.</span></span>  
  
## <a name="comparing-error-and-application-log-output"></a><span data-ttu-id="2719a-109">比較錯誤與應用程式記錄輸出</span><span class="sxs-lookup"><span data-stu-id="2719a-109">Comparing Error and Application Log Output</span></span>  
 <span data-ttu-id="2719a-110">您可以同時使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔和 Windows 應用程式記錄檔，來找出問題的原因。</span><span class="sxs-lookup"><span data-stu-id="2719a-110">You can use both the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and the Windows application log to identify the cause of problems.</span></span> <span data-ttu-id="2719a-111">例如，在監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔時，您可能會收到不含原因資訊的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="2719a-111">For example, while monitoring the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, you may encounter error messages that do not contain cause information.</span></span> <span data-ttu-id="2719a-112">藉由比較這些記錄之間的事件日期和時間，可以縮小可能原因的範圍。</span><span class="sxs-lookup"><span data-stu-id="2719a-112">By comparing the dates and times for events between these logs, you can narrow the list of probable causes.</span></span> <span data-ttu-id="2719a-113">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 記錄檔檢視器可讓您將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 與 Windows 記錄檔整合為一份清單，以便輕鬆地了解相關的伺服器事件與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事件。</span><span class="sxs-lookup"><span data-stu-id="2719a-113">The [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Log File Viewer lets you integrate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, and the Windows logs into a single list, making it easy to understand related server events and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events.</span></span> <span data-ttu-id="2719a-114">如需詳細資訊，請參閱《SQL Server 線上叢書》中的＜記錄檔檢視器＞主題。</span><span class="sxs-lookup"><span data-stu-id="2719a-114">For more information, see the topic "Log File Viewer" in SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2719a-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="2719a-115">In This Section</span></span>  
  
|<span data-ttu-id="2719a-116">主題</span><span class="sxs-lookup"><span data-stu-id="2719a-116">Topic</span></span>|<span data-ttu-id="2719a-117">描述</span><span class="sxs-lookup"><span data-stu-id="2719a-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2719a-118">檢視 SQL Server 錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="2719a-118">Viewing the SQL Server Error Log</span></span>](../../../2014/tools/configuration-manager/viewing-the-sql-server-error-log.md)|<span data-ttu-id="2719a-119">包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔及其檢視方式的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2719a-119">Contains information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and how to view it.</span></span>|  
|[<span data-ttu-id="2719a-120">檢視 Windows 應用程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="2719a-120">Viewing the Windows Application Log</span></span>](viewing-the-windows-application-log.md)|<span data-ttu-id="2719a-121">包含 Windows 應用程式記錄檔及其檢視方式的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2719a-121">Contains information about the Windows application log and how to view it.</span></span>|  
  
  
