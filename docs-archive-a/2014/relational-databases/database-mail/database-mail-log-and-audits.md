---
title: Database Mail 記錄與稽核 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- Database Mail [SQL Server], auditing
- logs [Database Mail]
- audits [SQL Server], Database Mail
- Database Mail [SQL Server], logging
ms.assetid: 846589ee-5fe5-4ab3-b335-0c253e569f99
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6267389f187b955982ec1c18c411f703b4562f3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709613"
---
# <a name="database-mail-log-and-audits"></a><span data-ttu-id="34875-102">Database Mail 記錄與稽核</span><span class="sxs-lookup"><span data-stu-id="34875-102">Database Mail Log and Audits</span></span>
  <span data-ttu-id="34875-103">Database Mail 記錄功能的設計目的是要提供方法來隔離並更正問題。</span><span class="sxs-lookup"><span data-stu-id="34875-103">The Database Mail logging functionality is designed to provide a way to isolate and correct problems.</span></span> <span data-ttu-id="34875-104">Database Mail 會將記錄資訊儲存至 **msdb** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="34875-104">Database Mail stores the log information in the **msdb** database.</span></span> <span data-ttu-id="34875-105">Database Mail 電子郵件內容、電子郵件狀態和任何收到之訊息 (例如錯誤) 的相關資訊，是透過 Database Mail 進行記錄，而且可用於進行疑難排解和稽核。</span><span class="sxs-lookup"><span data-stu-id="34875-105">Information about Database Mail e-mail content, status of e-mails, and any messages received, such as errors  are logged by Database Mail and can be used for troubleshooting and auditing purposes.</span></span>  
  
## <a name="database-mail-logs"></a><span data-ttu-id="34875-106">Database Mail 記錄檔</span><span class="sxs-lookup"><span data-stu-id="34875-106">Database Mail Logs</span></span>  
 <span data-ttu-id="34875-107">**msdb** 資料庫中的資料表會記錄來自 [Database Mail 外部程式](database-mail-external-program.md)的資訊。</span><span class="sxs-lookup"><span data-stu-id="34875-107">Tables in the **msdb** database log information from the [Database Mail External Program](database-mail-external-program.md).</span></span> <span data-ttu-id="34875-108">[Database Mail 檢視 &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/database-mail-views-transact-sql) 會公開資料表以供疑難排解之用。</span><span class="sxs-lookup"><span data-stu-id="34875-108">[Database Mail Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/database-mail-views-transact-sql) expose the tables for troubleshooting purposes.</span></span> <span data-ttu-id="34875-109">如果 Service Broker 無法啟動外部程式、外部程式發生網路問題或 Simple Mail Transport Protocol (SMTP) 伺服器拒絕電子郵件訊息，則 [sysmail_event_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-event-log-transact-sql) 檢視中會出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="34875-109">Errors appear in the [sysmail_event_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-event-log-transact-sql) view if Service Broker cannot activate the external program, if the external program encounters networking errors or if the Simple Mail Transport Protocol (SMTP) server refuses an e-mail message.</span></span> <span data-ttu-id="34875-110">當外部程式無法登入 **msdb** 資料表時，該程式會將錯誤記錄到 Windows 應用程式事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="34875-110">In the event that the external program cannot log to the **msdb** tables, the program logs errors to the Windows application event log.</span></span>  
  
 <span data-ttu-id="34875-111">**msdb** 資料庫中的內部資料表包含從 Database Mail 送出的電子郵件訊息與附加檔案，以及每封訊息的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="34875-111">Internal tables in the **msdb** database contain the e-mail messages and attachments sent from Database Mail, together with the current status of each message.</span></span> <span data-ttu-id="34875-112">Database Mail 會在每個訊息處理後更新這些資料表。</span><span class="sxs-lookup"><span data-stu-id="34875-112">Database Mail updates these tables as each message is processed.</span></span>  
  
## <a name="database-mail-auditing-tasks"></a><span data-ttu-id="34875-113">Database Mail 稽核工作</span><span class="sxs-lookup"><span data-stu-id="34875-113">Database Mail Auditing tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="34875-114">**檢閱和管理 Database Mail 記錄檔**</span><span class="sxs-lookup"><span data-stu-id="34875-114">**Reviewing and managing Database Mail logs**</span></span>|<span data-ttu-id="34875-115">**連結至主題**</span><span class="sxs-lookup"><span data-stu-id="34875-115">**Link to Topic**</span></span>|  
|<span data-ttu-id="34875-116">檢查個別訊息的傳遞狀態</span><span class="sxs-lookup"><span data-stu-id="34875-116">Check the delivery status of an individual message</span></span>|[<span data-ttu-id="34875-117">檢查使用 Database Mail 傳送之電子郵件訊息的狀態</span><span class="sxs-lookup"><span data-stu-id="34875-117">Check the Status of E-Mail Messages Sent With Database Mail</span></span>](check-the-status-of-e-mail-messages-sent-with-database-mail.md)|  
|<span data-ttu-id="34875-118">清除 Database Mail 訊息、附件和記錄項目</span><span class="sxs-lookup"><span data-stu-id="34875-118">Clean up Database Mail messages, attachments, and log entries</span></span>|[<span data-ttu-id="34875-119">sysmail_delete_mailitems_sp &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="34875-119">sysmail_delete_mailitems_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql)<br /><br /> [<span data-ttu-id="34875-120">sysmail_delete_log_sp &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="34875-120">sysmail_delete_log_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql)|  
|<span data-ttu-id="34875-121">封存資料庫電子郵件訊息和記錄檔</span><span class="sxs-lookup"><span data-stu-id="34875-121">Archive the Database Email Messages and Logs</span></span>|[<span data-ttu-id="34875-122">建立 SQL Server Agent 作業以封存 Database Mail 訊息及事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="34875-122">Create a SQL Server Agent Job to Archive Database Mail Messages and Event Logs</span></span>](create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)|  
  
## <a name="see-also"></a><span data-ttu-id="34875-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34875-123">See Also</span></span>  
 [<span data-ttu-id="34875-124">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="34875-124">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](../performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
