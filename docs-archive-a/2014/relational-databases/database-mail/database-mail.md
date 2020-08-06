---
title: Database Mail | Microsoft 文件
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- architecture [SQL Server], Database Mail
- Database Mail [SQL Server], architecture
- Database Mail [SQL Server], components
ms.assetid: 9e4563dd-4799-4b32-a78a-048ea44a44c1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 97a5a459fafd80956a2b8d31c27b86169c6fa850
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709601"
---
# <a name="database-mail"></a><span data-ttu-id="eb27c-102">Database Mail</span><span class="sxs-lookup"><span data-stu-id="eb27c-102">Database Mail</span></span>
  <span data-ttu-id="eb27c-103">Database Mail 是從 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 傳送電子郵件訊息的企業解決方案。</span><span class="sxs-lookup"><span data-stu-id="eb27c-103">Database Mail is an enterprise solution for sending e-mail messages from the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="eb27c-104">使用 Database Mail，資料庫應用程式就能夠將電子郵件訊息傳送給使用者。</span><span class="sxs-lookup"><span data-stu-id="eb27c-104">Using Database Mail, your database applications can send e-mail messages to users.</span></span> <span data-ttu-id="eb27c-105">這類訊息能包含查詢結果，也可以包含來自網路上任何資源的檔案。</span><span class="sxs-lookup"><span data-stu-id="eb27c-105">The messages can contain query results, and can also include files from any resource on your network.</span></span>  
  
 
  
##  <a name="benefits-of-using-database-mail"></a><a name="Benefits"></a> <span data-ttu-id="eb27c-106">使用 Database Mail 的優點</span><span class="sxs-lookup"><span data-stu-id="eb27c-106">Benefits of using Database Mail</span></span>  
 <span data-ttu-id="eb27c-107">Database Mail 具有可靠性、延展性、安全性及可支援性。</span><span class="sxs-lookup"><span data-stu-id="eb27c-107">Database Mail is designed for reliability, scalability, security, and supportability.</span></span>  
  
### <a name="reliability"></a><span data-ttu-id="eb27c-108">可靠性</span><span class="sxs-lookup"><span data-stu-id="eb27c-108">Reliability</span></span>  
  
-   <span data-ttu-id="eb27c-109">Database Mail 會使用標準的 Simple Mail Transfer Protocol (SMTP) 來傳送郵件。</span><span class="sxs-lookup"><span data-stu-id="eb27c-109">Database Mail uses the standard Simple Mail Transfer Protocol (SMTP) to send mail.</span></span> <span data-ttu-id="eb27c-110">您不需要在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的電腦上安裝「擴充 MAPI」用戶端，就可以使用 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="eb27c-110">You can use Database Mail without installing an Extended MAPI client on the computer that runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="eb27c-111">處理序隔離。</span><span class="sxs-lookup"><span data-stu-id="eb27c-111">Process isolation.</span></span> <span data-ttu-id="eb27c-112">為了將對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的影響減到最小，傳遞電子郵件的元件必須在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]外部的個別處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="eb27c-112">To minimize the impact on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the component that delivers e-mail runs outside of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in a separate process.</span></span> <span data-ttu-id="eb27c-113">即使外部處理序停止或失敗，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 仍會繼續將電子郵件訊息排入佇列中。</span><span class="sxs-lookup"><span data-stu-id="eb27c-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will continue to queue e-mail messages even if the external process stops or fails.</span></span> <span data-ttu-id="eb27c-114">佇列的訊息會在外部處理序或 SMTP 伺服器恢復連線後傳送。</span><span class="sxs-lookup"><span data-stu-id="eb27c-114">The queued messages will be sent once the outside process or SMTP server comes online.</span></span>  
  
-   <span data-ttu-id="eb27c-115">容錯移轉帳戶。</span><span class="sxs-lookup"><span data-stu-id="eb27c-115">Failover accounts.</span></span> <span data-ttu-id="eb27c-116">您可以使用 Database Mail 設定檔，指定多個 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="eb27c-116">A Database Mail profile allows you to specify more than one SMTP server.</span></span> <span data-ttu-id="eb27c-117">萬一 SMTP 伺服器無法使用時，還是可以將郵件傳遞到另一個 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="eb27c-117">Should an SMTP server be unavailable, mail can still be delivered to another SMTP server.</span></span>  
  
-   <span data-ttu-id="eb27c-118">叢集支援。</span><span class="sxs-lookup"><span data-stu-id="eb27c-118">Cluster support.</span></span> <span data-ttu-id="eb27c-119">Database Mail 可感知叢集，而且在叢集上完全受到支援。</span><span class="sxs-lookup"><span data-stu-id="eb27c-119">Database Mail is cluster-aware and is fully supported on a cluster.</span></span>  
  
### <a name="scalability"></a><span data-ttu-id="eb27c-120">延展性</span><span class="sxs-lookup"><span data-stu-id="eb27c-120">Scalability</span></span>  
  
-   <span data-ttu-id="eb27c-121">背景傳遞：Database Mail 提供背景或非同步傳遞功能。</span><span class="sxs-lookup"><span data-stu-id="eb27c-121">Background Delivery: Database Mail provides background, or asynchronous, delivery.</span></span> <span data-ttu-id="eb27c-122">呼叫 **sp_send_dbmail** 以傳送訊息時，Database Mail 會將要求加入 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 佇列。</span><span class="sxs-lookup"><span data-stu-id="eb27c-122">When you call **sp_send_dbmail** to send a message, Database Mail adds a request to a [!INCLUDE[ssSB](../../includes/sssb-md.md)] queue.</span></span> <span data-ttu-id="eb27c-123">此舉會立即傳回預存程序。</span><span class="sxs-lookup"><span data-stu-id="eb27c-123">The stored procedure returns immediately.</span></span> <span data-ttu-id="eb27c-124">外部電子郵件元件就會收到該要求，並傳遞電子郵件。</span><span class="sxs-lookup"><span data-stu-id="eb27c-124">The external e-mail component receives the request and delivers the e-mail.</span></span>  
  
-   <span data-ttu-id="eb27c-125">多個設定檔：您可以使用 Database Mail，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體內建立多個設定檔。</span><span class="sxs-lookup"><span data-stu-id="eb27c-125">Multiple profiles: Database Mail allows you to create multiple profiles within a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="eb27c-126">選擇性地傳送訊息時，您可以選擇 Database Mail 使用的設定檔。</span><span class="sxs-lookup"><span data-stu-id="eb27c-126">Optionally, you can choose the profile that Database Mail uses when you send a message.</span></span>  
  
-   <span data-ttu-id="eb27c-127">多個帳戶：每個設定檔都可以包含多個容錯移轉帳戶。</span><span class="sxs-lookup"><span data-stu-id="eb27c-127">Multiple accounts: Each profile can contain multiple failover accounts.</span></span> <span data-ttu-id="eb27c-128">您可以設定不同的設定檔使用不同的帳戶，在多個電子郵件伺服器散發電子郵件。</span><span class="sxs-lookup"><span data-stu-id="eb27c-128">You can configure different profiles with different accounts to distribute e-mail across multiple e-mail servers.</span></span>  
  
-   <span data-ttu-id="eb27c-129">64 位元相容性： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的 64 位元安裝完全支援 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="eb27c-129">64-bit compatibility: Database Mail is fully supported on 64-bit installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="security"></a><span data-ttu-id="eb27c-130">安全性</span><span class="sxs-lookup"><span data-stu-id="eb27c-130">Security</span></span>  
  
-   <span data-ttu-id="eb27c-131">預設為關閉狀態：為了要縮小 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的介面區，預設會停用 Database Mail 預存程序。</span><span class="sxs-lookup"><span data-stu-id="eb27c-131">Off by default: To reduce the surface area of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Database Mail stored procedures are disabled by default.</span></span>  
  
-   <span data-ttu-id="eb27c-132">郵件安全性：若要傳送 Database Mail，您必須是 **msdb** 資料庫中 **DatabaseMailUserRole** 資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="eb27c-132">Mail Security:To send Database Mail, you must be a member of the **DatabaseMailUserRole** database role in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="eb27c-133">設定檔安全性：Database Mail 會強制執行郵件設定檔的安全性。</span><span class="sxs-lookup"><span data-stu-id="eb27c-133">Profile security: Database Mail enforces security for mail profiles.</span></span> <span data-ttu-id="eb27c-134">您要選擇擁有 Database Mail 設定檔存取權的 **msdb** 資料庫使用者或群組。</span><span class="sxs-lookup"><span data-stu-id="eb27c-134">You choose the **msdb** database users or groups that have access to a Database Mail profile.</span></span> <span data-ttu-id="eb27c-135">您可以將存取權授與給 **msdb**中的特定使用者或所有使用者。</span><span class="sxs-lookup"><span data-stu-id="eb27c-135">You can grant access to either specific users, or all users in **msdb**.</span></span> <span data-ttu-id="eb27c-136">私人設定檔限制清單上指定的使用者才有存取權。</span><span class="sxs-lookup"><span data-stu-id="eb27c-136">A private profile restricts access to a specified list of users.</span></span> <span data-ttu-id="eb27c-137">公用設定檔可供資料庫的所有使用者使用。</span><span class="sxs-lookup"><span data-stu-id="eb27c-137">A public profile is available to all users in a database.</span></span>  
  
-   <span data-ttu-id="eb27c-138">附件大小管理員：Database Mail 會強制執行附加檔案大小的可設定限制。</span><span class="sxs-lookup"><span data-stu-id="eb27c-138">Attachment size governor: Database Mail enforces a configurable limit on the attachment file size.</span></span> <span data-ttu-id="eb27c-139">您可以使用 [sysmail_configure_sp](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql) 預存程序來變更這項限制。</span><span class="sxs-lookup"><span data-stu-id="eb27c-139">You can change this limit by using the [sysmail_configure_sp](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql) stored procedure.</span></span>  
  
-   <span data-ttu-id="eb27c-140">禁止的副檔名：Database Mail 維護一個禁止的副檔名清單。</span><span class="sxs-lookup"><span data-stu-id="eb27c-140">Prohibited file extensions: Database Mail maintains a list of prohibited file extensions.</span></span> <span data-ttu-id="eb27c-141">使用者無法附加副檔名出現在清單中的檔案。</span><span class="sxs-lookup"><span data-stu-id="eb27c-141">Users cannot attach files with an extension that appears in the list.</span></span> <span data-ttu-id="eb27c-142">您可以使用 sysmail_configure_sp 來變更此清單。</span><span class="sxs-lookup"><span data-stu-id="eb27c-142">You can change this list by using sysmail_configure_sp.</span></span>  
  
-   <span data-ttu-id="eb27c-143">Database Mail 會以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 引擎服務帳戶執行。</span><span class="sxs-lookup"><span data-stu-id="eb27c-143">Database Mail runs under the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Engine service account.</span></span> <span data-ttu-id="eb27c-144">若要從資料夾將檔案附加至電子郵件，則 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 引擎帳戶應具備存取包含該檔案之資料夾的權限。</span><span class="sxs-lookup"><span data-stu-id="eb27c-144">To attach a file from a folder to an email, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] engine account should have permissions to access the folder with the file.</span></span>  
  
### <a name="supportability"></a><span data-ttu-id="eb27c-145">可支援性</span><span class="sxs-lookup"><span data-stu-id="eb27c-145">Supportability</span></span>  
  
-   <span data-ttu-id="eb27c-146">整合式組態：Database Mail 可維護 [!INCLUDE[ssDEnoversion](../../includes/tsql-md.md)]內電子郵件帳戶的資訊。</span><span class="sxs-lookup"><span data-stu-id="eb27c-146">Integrated configuration: Database Mail maintains the information for e-mail accounts within [!INCLUDE[ssDEnoversion](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="eb27c-147">記錄。</span><span class="sxs-lookup"><span data-stu-id="eb27c-147">Logging.</span></span> <span data-ttu-id="eb27c-148">Database Mail 會將電子郵件活動記錄到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、Microsoft Windows 應用程式事件記錄檔，以及 **msdb** 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="eb27c-148">Database Mail logs e-mail activity to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the Microsoft Windows application event log, and to tables in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="eb27c-149">稽核：Database Mail 會在 **msdb** 資料庫中保留所傳送的郵件與附件的複本。</span><span class="sxs-lookup"><span data-stu-id="eb27c-149">Auditing: Database Mail keeps copies of messages and attachments sent in the **msdb** database.</span></span> <span data-ttu-id="eb27c-150">您可以輕鬆稽核 Database Mail 的使用狀況，並檢閱所保留的郵件。</span><span class="sxs-lookup"><span data-stu-id="eb27c-150">You can easily audit Database Mail usage and review the retained messages.</span></span>  
  
-   <span data-ttu-id="eb27c-151">支援 HTML：您可以使用 Database Mail 傳送 HTML 格式的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="eb27c-151">Support for HTML: Database Mail allows you to send e-mail formatted as HTML.</span></span>  
  

  
##  <a name="database-mail-architecture"></a><a name="VisualElement"></a> <span data-ttu-id="eb27c-152">Database Mail 架構</span><span class="sxs-lookup"><span data-stu-id="eb27c-152">Database Mail Architecture</span></span>  
 <span data-ttu-id="eb27c-153">Database Mail 是根據使用 Service Broker 技術的佇列架構而設計。</span><span class="sxs-lookup"><span data-stu-id="eb27c-153">Database Mail is designed on a queued architecture that uses service broker technologies.</span></span> <span data-ttu-id="eb27c-154">當使用者執行 **sp_send_dbmail**時，預存程序會在郵件佇列中插入項目，並建立包含該電子郵件訊息的記錄。</span><span class="sxs-lookup"><span data-stu-id="eb27c-154">When users execute **sp_send_dbmail**, the stored procedure inserts an item into the mail queue and creates a record that contains the e-mail message.</span></span> <span data-ttu-id="eb27c-155">在郵件佇列中插入新項目會啟動外部 Database Mail 處理序 (DatabaseMail.exe)。</span><span class="sxs-lookup"><span data-stu-id="eb27c-155">Inserting the new entry in the mail queue starts the external Database Mail process (DatabaseMail.exe).</span></span> <span data-ttu-id="eb27c-156">外部處理序會讀取電子郵件資訊，並傳送電子郵件訊息到適當的電子郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="eb27c-156">The external process reads the e-mail information and sends the e-mail message to the appropriate e-mail server or servers.</span></span> <span data-ttu-id="eb27c-157">外部處理序會在「狀態」佇列中插入項目，表示傳送作業的結果。</span><span class="sxs-lookup"><span data-stu-id="eb27c-157">The external process inserts an item in the Status queue for the outcome of the send operation.</span></span> <span data-ttu-id="eb27c-158">在狀態佇列中插入新記錄會啟動內部預存程序，此預存程序會更新電子郵件訊息的狀態。</span><span class="sxs-lookup"><span data-stu-id="eb27c-158">Inserting the new entry in the status queue starts an internal stored procedure that updates the status of the e-mail message.</span></span> <span data-ttu-id="eb27c-159">除了儲存已傳送 (或未傳送) 的電子郵件訊息之外，Database Mail 也會在系統資料表中記錄任何電子郵件附加檔案。</span><span class="sxs-lookup"><span data-stu-id="eb27c-159">Besides storing the sent, or unsent, e-mail message, Database Mail also records any e-mail attachments in the system tables.</span></span> <span data-ttu-id="eb27c-160">Database Mail 檢視提供可用於進行疑難排解的訊息狀態，並提供可用來管理 Database Mail 佇列的預存程序。</span><span class="sxs-lookup"><span data-stu-id="eb27c-160">Database Mail views provide the status of messages for troubleshooting, and stored procedures allow for administration of the Database Mail queue.</span></span>  
  
 <span data-ttu-id="eb27c-161">![msdb 傳送訊息到 SMTP 郵件伺服器](../../database-engine/media/databasemail.gif "msdb 傳送訊息到 SMTP 郵件伺服器")</span><span class="sxs-lookup"><span data-stu-id="eb27c-161">![msdb sends messages to an SMTP mail server](../../database-engine/media/databasemail.gif "msdb sends messages to an SMTP mail server")</span></span>  
  

  
##  <a name="introduction-to-database-mail-components"></a><a name="ComponentsAndConcepts"></a> <span data-ttu-id="eb27c-162">Database Mail 元件簡介</span><span class="sxs-lookup"><span data-stu-id="eb27c-162">Introduction to Database Mail Components</span></span>  
 <span data-ttu-id="eb27c-163">Database Mail 是由下列主要元件所組成：</span><span class="sxs-lookup"><span data-stu-id="eb27c-163">Database Mail consists of the following main components:</span></span>  
  
-   <span data-ttu-id="eb27c-164">組態與安全性元件</span><span class="sxs-lookup"><span data-stu-id="eb27c-164">Configuration and security components</span></span>  
  
     <span data-ttu-id="eb27c-165">Database Mail 會將組態與安全性資訊儲存在 **msdb** 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="eb27c-165">Database Mail stores configuration and security information in the **msdb** database.</span></span> <span data-ttu-id="eb27c-166">組態與安全性物件會建立用於 Database Mail 的設定檔與帳戶。</span><span class="sxs-lookup"><span data-stu-id="eb27c-166">Configuration and security objects create profiles and accounts used by Database Mail.</span></span>  
  
-   <span data-ttu-id="eb27c-167">訊息元件</span><span class="sxs-lookup"><span data-stu-id="eb27c-167">Messaging components</span></span>  
  
     <span data-ttu-id="eb27c-168">**msdb** 資料庫會充當郵件主機資料庫，其中會保存 Database Mail 用來傳送電子郵件的訊息物件。</span><span class="sxs-lookup"><span data-stu-id="eb27c-168">The **msdb** database acts as the mail-host database that holds the messaging objects that Database Mail uses to send e-mail.</span></span> <span data-ttu-id="eb27c-169">這些物件包括 **sp_send_dbmail** 預存程序，以及保存訊息相關資訊的資料結構。</span><span class="sxs-lookup"><span data-stu-id="eb27c-169">These objects include the **sp_send_dbmail** stored procedure and the data structures that hold information about messages.</span></span>  
  
-   <span data-ttu-id="eb27c-170">Database Mail 可執行檔</span><span class="sxs-lookup"><span data-stu-id="eb27c-170">Database Mail executable</span></span>  
  
     <span data-ttu-id="eb27c-171">Database Mail 可執行檔是一個外部程式，它會從 **msdb** 資料庫中的佇列讀取，並傳送訊息到電子郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="eb27c-171">The Database Mail executable is an external program that reads from a queue in the **msdb** database and sends messages to e-mail servers.</span></span>  
  
-   <span data-ttu-id="eb27c-172">記錄與稽核元件</span><span class="sxs-lookup"><span data-stu-id="eb27c-172">Logging and auditing components</span></span>  
  
     <span data-ttu-id="eb27c-173">Database Mail 會將記錄資訊記錄在 **msdb** 資料庫與 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 應用程式事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="eb27c-173">Database Mail records logging information in the **msdb** database and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application event log.</span></span>  
  
 <span data-ttu-id="eb27c-174">**設定 Agent 使用 Database Mail：**</span><span class="sxs-lookup"><span data-stu-id="eb27c-174">**Configuring Agent to use Database Mail:**</span></span>  
  
 <span data-ttu-id="eb27c-175">SQL Server Agent 可以設定成使用 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="eb27c-175">SQL Server Agent can be configured to use Database Mail.</span></span> <span data-ttu-id="eb27c-176">警示通知和完成作業時的自動通知都需要 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="eb27c-176">This is required for alert notifications and automatic notification when a job completes.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="eb27c-177">未將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 設定成使用 Database Mail，作業內的個別作業步驟也可以傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="eb27c-177">Individual job steps within a job can also send e-mail without configuring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to use Database Mail.</span></span> <span data-ttu-id="eb27c-178">例如， [!INCLUDE[tsql](../../../includes/tsql-md.md)] 作業步驟可以使用 Database Mail，將查詢結果傳送到收件者清單。</span><span class="sxs-lookup"><span data-stu-id="eb27c-178">For example, a [!INCLUDE[tsql](../../../includes/tsql-md.md)] job step can use Database Mail to send the results of a query to a list of recipients.</span></span>  
  
 <span data-ttu-id="eb27c-179">您可以設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent，在下列時機將電子郵件訊息傳送給預先定義的操作員：</span><span class="sxs-lookup"><span data-stu-id="eb27c-179">You can configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to send e-mail messages to predefined operators when:</span></span>  
  
-   <span data-ttu-id="eb27c-180">觸發警示時。</span><span class="sxs-lookup"><span data-stu-id="eb27c-180">An alert is triggered.</span></span> <span data-ttu-id="eb27c-181">經過設定後，警示可以為發生的特定事件傳送電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="eb27c-181">Alerts can be configured to send e-mail notification of specific events that occur.</span></span> <span data-ttu-id="eb27c-182">例如，將警示設成在發生必須立即處理的資料庫事件或作業系統狀況時通知操作員。</span><span class="sxs-lookup"><span data-stu-id="eb27c-182">For example, alerts can be configured to notify an operator of a particular database event or operating system condition that may need immediate action.</span></span> <span data-ttu-id="eb27c-183">如需設定警示的詳細資訊，請參閱 [警示](../../ssms/agent/alerts.md)。</span><span class="sxs-lookup"><span data-stu-id="eb27c-183">For more information about configuring alerts, see [Alerts](../../ssms/agent/alerts.md).</span></span>  
  
-   <span data-ttu-id="eb27c-184">排程工作 (如資料庫備份或複寫事件) 成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="eb27c-184">A scheduled task, such as a database backup or replication event, succeeds or fails.</span></span> <span data-ttu-id="eb27c-185">例如，可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Mail，通知操作員在該月結束時的處理期間，是否發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="eb27c-185">For example, you can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Mail to notify operators if an error occurs during processing at the end of a month.</span></span>  
  
 
  
##  <a name="database-mail-component-topics"></a><a name="RelatedContent"></a> <span data-ttu-id="eb27c-186">Database Mail 元件主題</span><span class="sxs-lookup"><span data-stu-id="eb27c-186">Database Mail Component Topics</span></span>  
  
-   [<span data-ttu-id="eb27c-187">Database Mail 組態物件</span><span class="sxs-lookup"><span data-stu-id="eb27c-187">Database Mail Configuration Objects</span></span>](database-mail-configuration-objects.md)  
  
-   [<span data-ttu-id="eb27c-188">Database Mail 訊息物件</span><span class="sxs-lookup"><span data-stu-id="eb27c-188">Database Mail Messaging Objects</span></span>](database-mail-messaging-objects.md)  
  
-   [<span data-ttu-id="eb27c-189">Database Mail 外部程式</span><span class="sxs-lookup"><span data-stu-id="eb27c-189">Database Mail External Program</span></span>](database-mail-external-program.md)  
  
-   [<span data-ttu-id="eb27c-190">Database Mail 記錄與稽核</span><span class="sxs-lookup"><span data-stu-id="eb27c-190">Database Mail Log and Audits</span></span>](database-mail-log-and-audits.md)  
  
-   [<span data-ttu-id="eb27c-191">設定 SQL Server Agent Mail 使用 Database Mail</span><span class="sxs-lookup"><span data-stu-id="eb27c-191">Configure SQL Server Agent Mail to Use Database Mail</span></span>](configure-sql-server-agent-mail-to-use-database-mail.md)  
  

  
  
