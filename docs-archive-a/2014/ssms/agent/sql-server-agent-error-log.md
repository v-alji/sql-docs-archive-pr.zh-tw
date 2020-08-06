---
title: SQL Server Agent 錯誤記錄檔 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- messages [SQL Server], SQL Server Agent
- errors [SQL Server], logs
- SQL Server Agent, errors
ms.assetid: 0b2d6e6e-cd2d-4b8b-9fa2-2bbd2fc0da41
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea9a723695c6993f4f07897f49d8014a86ce78b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699166"
---
# <a name="sql-server-agent-error-log"></a><span data-ttu-id="b4a44-102">SQL Server Agent 錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="b4a44-102">SQL Server Agent Error Log</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b4a44-103">依預設，Agent 會建立錯誤記錄檔來記錄警告與錯誤。</span><span class="sxs-lookup"><span data-stu-id="b4a44-103">Agent creates an error log that records warnings and errors by default.</span></span> <span data-ttu-id="b4a44-104">記錄檔中會顯示下列警告和錯誤：</span><span class="sxs-lookup"><span data-stu-id="b4a44-104">The following warnings and errors are displayed in the log:</span></span>  
  
-   <span data-ttu-id="b4a44-105">提供潛在問題相關資訊的警告訊息，例如「作業 \<*job_name*> 在執行時刪除」。</span><span class="sxs-lookup"><span data-stu-id="b4a44-105">Warning messages that provide information about potential problems, such as "Job \<*job_name*> was deleted while it was running."</span></span>  
  
-   <span data-ttu-id="b4a44-106">通常需要系統管理員介入的錯誤訊息，例如「無法啟動郵件工作階段」。</span><span class="sxs-lookup"><span data-stu-id="b4a44-106">Error messages that usually require intervention by a system administrator, such as "Unable to start mail session."</span></span> <span data-ttu-id="b4a44-107">錯誤訊息可以藉由 **net send**來傳送給特定的使用者或電腦。</span><span class="sxs-lookup"><span data-stu-id="b4a44-107">Error messages can be sent to a specific user or computer by **net send**.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b4a44-108">至多可以維護九個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b4a44-108">maintains up to nine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error logs.</span></span> <span data-ttu-id="b4a44-109">每個已封存之記錄檔的副檔名都會指出記錄檔的相對存在時間。</span><span class="sxs-lookup"><span data-stu-id="b4a44-109">Each archived log has an extension that indicates the relative age of the log.</span></span> <span data-ttu-id="b4a44-110">例如，.1 的副檔名表示它是最近新封存的錯誤記錄檔，而 .9 的副檔名則表示是最早封存的錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b4a44-110">For example, an extension of .1 indicates the newest archived error log and an extension of .9 indicates the oldest archived error log.</span></span>  
  
 <span data-ttu-id="b4a44-111">因為執行追蹤訊息會填滿 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 錯誤記錄檔，所以在預設情況下，並不會寫入錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b4a44-111">By default, execution trace messages are not written to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log, because they can fill it.</span></span> <span data-ttu-id="b4a44-112">當錯誤記錄檔滿了，會降低您選取與分析更困難錯誤的能力。</span><span class="sxs-lookup"><span data-stu-id="b4a44-112">When the error log is full, your ability to select and analyze more difficult errors is reduced.</span></span> <span data-ttu-id="b4a44-113">因為記錄檔會增加伺服器的處理負擔，請務必仔細考慮將執行追蹤訊息擷取到錯誤記錄檔是否值得。</span><span class="sxs-lookup"><span data-stu-id="b4a44-113">Because the log adds to the server's processing load, it is important to consider carefully what value you obtain by capturing execution trace messages to the error log.</span></span> <span data-ttu-id="b4a44-114">一般而言，最好只有在為一個特定問題進行偵錯時，您才擷取所有的訊息。</span><span class="sxs-lookup"><span data-stu-id="b4a44-114">Generally, it is best to capture all messages only when you are debugging a specific problem.</span></span>  
  
 <span data-ttu-id="b4a44-115">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 停止時，您可以修改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 錯誤記錄檔的位置。</span><span class="sxs-lookup"><span data-stu-id="b4a44-115">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is stopped, you can modify the location of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log.</span></span> <span data-ttu-id="b4a44-116">您無法開啟空的錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b4a44-116">When the error log is empty, the log cannot be opened.</span></span> <span data-ttu-id="b4a44-117">您可以隨時循環使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 記錄檔，無須停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent。</span><span class="sxs-lookup"><span data-stu-id="b4a44-117">You can cycle the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent log at any time without stopping [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
 <span data-ttu-id="b4a44-118">**若要檢視 SQL Server Agent 錯誤記錄檔**</span><span class="sxs-lookup"><span data-stu-id="b4a44-118">**To view the SQL Server Agent error log**</span></span>  
  
-   [<span data-ttu-id="b4a44-119">檢視 SQL Server Agent 錯誤記錄檔 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b4a44-119">View SQL Server Agent Error Log &#40;SQL Server Management Studio&#41;</span></span>](view-sql-server-agent-error-log-sql-server-management-studio.md) 
  
 <span data-ttu-id="b4a44-120">**若要重新命名 SQL Server Agent 錯誤記錄檔**</span><span class="sxs-lookup"><span data-stu-id="b4a44-120">**To rename a SQL Server Agent error log**</span></span>  
  
-   [<span data-ttu-id="b4a44-121">重新命名 SQL Server Agent 錯誤記錄檔 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b4a44-121">Rename a SQL Server Agent Error Log &#40;SQL Server Management Studio&#41;</span></span>](rename-a-sql-server-agent-error-log-sql-server-management-studio.md)  
  
 <span data-ttu-id="b4a44-122">**若要傳送 SQL Server Agent 錯誤訊息**</span><span class="sxs-lookup"><span data-stu-id="b4a44-122">**To send SQL Server Agent error messages**</span></span>  
  
-   [<span data-ttu-id="b4a44-123">傳送 SQL Server Agent 錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="b4a44-123">Send SQL Server Agent Error Messages</span></span>](send-sql-server-agent-error-messages.md)  
  
 <span data-ttu-id="b4a44-124">**若要將執行追蹤訊息寫入 SQL Server Agent 錯誤記錄檔**</span><span class="sxs-lookup"><span data-stu-id="b4a44-124">**To write execution trace messages to the SQL Server Agent error log**</span></span>  
  
-   [<span data-ttu-id="b4a44-125">在 SQL Server Agent 錯誤記錄檔中寫入執行追蹤訊息 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b4a44-125">Write Execution Trace Messages to the SQL Server Agent Error Log &#40;SQL Server Management Studio&#41;</span></span>](write-execution-trace-messages-to-sql-server-agent-log-ssms.md)  
  
  
