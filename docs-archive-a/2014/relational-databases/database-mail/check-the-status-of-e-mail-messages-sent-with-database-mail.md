---
title: 檢查使用 Database Mail 傳送之電子郵件訊息的狀態 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- e-mail [SQL Server], status information
- mail [SQL Server], status information
- Database Mail [SQL Server], message status
- status information [Database Mail]
ms.assetid: eb290f24-b52f-46bc-84eb-595afee6a5f3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1642c456cd64484dede64f8127ff2f979f2242e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606874"
---
# <a name="check-the-status-of-e-mail-messages-sent-with-database-mail"></a><span data-ttu-id="62c0a-102">檢查使用 Database Mail 傳送之電子郵件訊息的狀態</span><span class="sxs-lookup"><span data-stu-id="62c0a-102">Check the Status of E-Mail Messages Sent With Database Mail</span></span>
  <span data-ttu-id="62c0a-103">本主題描述如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]來檢查透過 Database Mail 傳送之電子郵件訊息的狀態。</span><span class="sxs-lookup"><span data-stu-id="62c0a-103">This topic describes how to check the status of the e-mail message sent using Database Mail  in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="62c0a-104">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="62c0a-104">**Before you begin:**</span></span>  
  
-   <span data-ttu-id="62c0a-105">**使用下列項目，檢視透過 Database Mail 所傳送電子郵件的狀態：** [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="62c0a-105">**To view the status of the e-mail sent using Database Mail, using:**  [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="62c0a-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="62c0a-106">Before You Begin</span></span>  
 <span data-ttu-id="62c0a-107">Database Mail 會保留外寄電子郵件訊息的副本，並在 **msdb**資料庫的 **sysmail_allitems**、 **sysmail_sentitems**、 **sysmail_unsentitems** 、 **sysmail_faileditems** 檢視中顯示它們。</span><span class="sxs-lookup"><span data-stu-id="62c0a-107">Database Mail keeps copies of outgoing e-mail messages and displays them in the **sysmail_allitems**, **sysmail_sentitems**, **sysmail_unsentitems**, **sysmail_faileditems** views of the **msdb** database.</span></span> <span data-ttu-id="62c0a-108">Database Mail 外部程式會記錄活動，並透過「Windows 應用程式事件記錄檔」和 **msdb** 資料庫中的 **sysmail_event_log** 檢視來顯示記錄檔。</span><span class="sxs-lookup"><span data-stu-id="62c0a-108">The Database Mail external program logs activity and displays the log through the Windows Application Event Log and the **sysmail_event_log** view in the **msdb** database.</span></span> <span data-ttu-id="62c0a-109">若要檢查電子郵件訊息的狀態，請對此檢視執行查詢。</span><span class="sxs-lookup"><span data-stu-id="62c0a-109">To check the status of an e-mail message, run a query against this view.</span></span> <span data-ttu-id="62c0a-110">電子郵件訊息狀態可為下列四種之一： **「已傳送」** 、 **「未傳送」** 、 **「正在重試」** 及 **「失敗」** 。</span><span class="sxs-lookup"><span data-stu-id="62c0a-110">E-mail messages have one of four possible statuses: **sent**, **unsent**, **retrying**, and **failed**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="62c0a-111">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="62c0a-111">Using Transact-SQL</span></span>  
 <span data-ttu-id="62c0a-112">**若要檢視使用 Database Mail 傳送之電子郵件的狀態**</span><span class="sxs-lookup"><span data-stu-id="62c0a-112">**To view the status of the e-mail sent using Database Mail**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="62c0a-113">如需這個程序的範例，請參閱本節稍後的 [範例 &#40;Transact-SQL&#41;](#TsqlExample)。</span><span class="sxs-lookup"><span data-stu-id="62c0a-113">For an example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="62c0a-114">從 **sysmail_allitems** 資料表進行選取，按照 **mailitem_id** 或 **sent_status**指定所需的訊息。</span><span class="sxs-lookup"><span data-stu-id="62c0a-114">Select from the **sysmail_allitems** table, specifying the messages of interest by **mailitem_id** or **sent_status**.</span></span>  
  
2.  <span data-ttu-id="62c0a-115">若要檢查外部程式為電子郵件訊息所傳回的狀態，請將 **sysmail_allitems** 聯結到 **sysmail_event_log** 檢視的 **mailitem_id** 資料行，如下節所示。</span><span class="sxs-lookup"><span data-stu-id="62c0a-115">To check the status returned from the external program for the e-mail messages, join **sysmail_allitems** to **sysmail_event_log** view on the **mailitem_id** column, as shown in the following section.</span></span>  
  
     <span data-ttu-id="62c0a-116">依預設，外部程式不會記錄已成功傳送的訊息之相關資訊。</span><span class="sxs-lookup"><span data-stu-id="62c0a-116">By default, the external program does not log information about messages that were successfully sent.</span></span> <span data-ttu-id="62c0a-117">若要記錄所有訊息，請使用 **[Database Mail 組態精靈]** 的 **[設定系統參數]** 頁面，將記錄層級設為詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="62c0a-117">To log all messages, set the logging level to verbose using the **Configure System Parameters** page of the **Database Mail Configuration Wizard.**</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="62c0a-118">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="62c0a-118">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="62c0a-119">以下範例列出任何外部程式無法順利傳送而傳送至 `danw` 的電子郵件訊息相關資訊。</span><span class="sxs-lookup"><span data-stu-id="62c0a-119">The following example lists information about any e-mail messages sent to `danw` that the external program could not send successfully.</span></span> <span data-ttu-id="62c0a-120">此陳述式會列出外部程式無法傳送之訊息的主旨、日期和時間，以及 Database Mail 記錄檔中的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="62c0a-120">The statement lists the subject, the date and time that the external program failed to send the message, and the error message from the Database Mail log.</span></span>  
  
```  
USE msdb ;  
GO  
  
-- Show the subject, the time that the mail item row was last  
-- modified, and the log information.  
-- Join sysmail_faileditems to sysmail_event_log   
-- on the mailitem_id column.  
-- In the WHERE clause list items where danw was in the recipients,  
-- copy_recipients, or blind_copy_recipients.  
-- These are the items that would have been sent  
-- to danw.  
  
SELECT items.subject,  
    items.last_mod_date  
    ,l.description FROM dbo.sysmail_faileditems as items  
INNER JOIN dbo.sysmail_event_log AS l  
    ON items.mailitem_id = l.mailitem_id  
WHERE items.recipients LIKE '%danw%'    
    OR items.copy_recipients LIKE '%danw%'   
    OR items.blind_copy_recipients LIKE '%danw%'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="62c0a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62c0a-121">See Also</span></span>  
 [<span data-ttu-id="62c0a-122">Database Mail 記錄與稽核</span><span class="sxs-lookup"><span data-stu-id="62c0a-122">Database Mail Log and Audits</span></span>](database-mail-log-and-audits.md)  
  
  
