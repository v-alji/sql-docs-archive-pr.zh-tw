---
title: 操作員 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- operators (users) [Database Engine]
- fail-safe operator [SQL Server]
- aliases [SQL Server], operators
- SQL Server Agent alerts, operators
- contact information [SQL Server Agent]
- net send [SQL Server]
- e-mail [SQL Server], SQL Server Agent operators
- pager notifications [SQL Server Agent]
- mail [SQL Server], SQL Server Agent operators
- operators (users) [Database Engine], defining
- jobs [SQL Server Agent], operators
- alerts [SQL Server], operators
ms.assetid: 38e8488f-2669-4cea-b9c3-5f394a663678
author: stevestein
ms.author: sstein
ms.openlocfilehash: d141a2db9a69603701200bc50dcac57ef402968a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704669"
---
# <a name="operators"></a><span data-ttu-id="a80d9-102">運算子</span><span class="sxs-lookup"><span data-stu-id="a80d9-102">Operators</span></span>
  <span data-ttu-id="a80d9-103">操作員是人員或群組的別名，當作業完成或產生警示時，可收到電子通知。</span><span class="sxs-lookup"><span data-stu-id="a80d9-103">Operators are aliases for people or groups that can receive electronic notification when jobs have completed or alerts have been raised.</span></span> <span data-ttu-id="a80d9-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務可支援透過操作員，發送通知給系統管理員。</span><span class="sxs-lookup"><span data-stu-id="a80d9-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service supports the notification of administrators through operators.</span></span> <span data-ttu-id="a80d9-105">操作員會啟用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的通知和監視功能。</span><span class="sxs-lookup"><span data-stu-id="a80d9-105">Operators enable notification and monitoring capabilities of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
## <a name="operator-attributes-and-concepts"></a><span data-ttu-id="a80d9-106">操作員屬性和概念</span><span class="sxs-lookup"><span data-stu-id="a80d9-106">Operator Attributes and Concepts</span></span>  
 <span data-ttu-id="a80d9-107">操作員的主要屬性如下：</span><span class="sxs-lookup"><span data-stu-id="a80d9-107">The primary attributes of an operator are:</span></span>  
  
-   <span data-ttu-id="a80d9-108">操作員名稱</span><span class="sxs-lookup"><span data-stu-id="a80d9-108">Operator name</span></span>  
  
-   <span data-ttu-id="a80d9-109">連絡人資訊</span><span class="sxs-lookup"><span data-stu-id="a80d9-109">Contact information</span></span>  
  
### <a name="naming-an-operator"></a><span data-ttu-id="a80d9-110">為操作員命名</span><span class="sxs-lookup"><span data-stu-id="a80d9-110">Naming an Operator</span></span>  
 <span data-ttu-id="a80d9-111">每個操作員都必須要有一個名稱。</span><span class="sxs-lookup"><span data-stu-id="a80d9-111">Every operator must have a name.</span></span> <span data-ttu-id="a80d9-112">操作員名稱必須是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中唯一的名稱，而且不可長於 **128** 個字元。</span><span class="sxs-lookup"><span data-stu-id="a80d9-112">Operator names must be unique within the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance and can be no longer than **128** characters.</span></span>  
  
### <a name="contact-information"></a><span data-ttu-id="a80d9-113">連絡資訊</span><span class="sxs-lookup"><span data-stu-id="a80d9-113">Contact Information</span></span>  
 <span data-ttu-id="a80d9-114">操作員的連絡資訊會定義如何通知操作員。</span><span class="sxs-lookup"><span data-stu-id="a80d9-114">An operator's contact information defines how the operator is notified.</span></span> <span data-ttu-id="a80d9-115">您可以透過電子郵件、呼叫器或 **net send** 命令來通知操作員：</span><span class="sxs-lookup"><span data-stu-id="a80d9-115">Operators can be notified by e-mail, pager, or through the **net send** command:</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a80d9-116">呼叫器和 **net send** 選項會從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 未來版本的 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a80d9-116">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a80d9-117">請避免在新的開發工作中使用這些功能，並規劃修改目前使用這些功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a80d9-117">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="a80d9-118">**電子郵件通知**</span><span class="sxs-lookup"><span data-stu-id="a80d9-118">**E-mail notification**</span></span>  
  
     <span data-ttu-id="a80d9-119">電子郵件通知會傳送電子郵件訊息給操作員。</span><span class="sxs-lookup"><span data-stu-id="a80d9-119">E-mail notification sends an e-mail message to the operator.</span></span> <span data-ttu-id="a80d9-120">若是使用電子郵件通知，您需提供操作員的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="a80d9-120">For e-mail notification, you provide the e-mail address for the operator.</span></span>  
  
-   <span data-ttu-id="a80d9-121">**呼叫器通知**</span><span class="sxs-lookup"><span data-stu-id="a80d9-121">**Pager notification**</span></span>  
  
     <span data-ttu-id="a80d9-122">呼叫是透過電子郵件來實作的。</span><span class="sxs-lookup"><span data-stu-id="a80d9-122">Paging is implemented by e-mail.</span></span> <span data-ttu-id="a80d9-123">若是使用呼叫器通知，您需提供操作員用來接收呼叫器訊息的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="a80d9-123">For pager notification, you provide the e-mail address where the operator receives pager messages.</span></span> <span data-ttu-id="a80d9-124">若要設定呼叫器通知，您必須將軟體安裝在郵件伺服器上，以便處理傳入郵件，並將其轉換為呼叫器訊息。</span><span class="sxs-lookup"><span data-stu-id="a80d9-124">To set up pager notification, you must install software on the mail server that processes inbound mail and converts it to a pager message.</span></span> <span data-ttu-id="a80d9-125">該軟體可以採取幾種方法之一，包括：</span><span class="sxs-lookup"><span data-stu-id="a80d9-125">The software can take one of several approaches, including:</span></span>  
  
    -   <span data-ttu-id="a80d9-126">將郵件轉寄到位於呼叫器供應商站台的遠端郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="a80d9-126">Forwarding the mail to a remote mail server at the site of the pager provider.</span></span>  
  
         <span data-ttu-id="a80d9-127">雖然所需的軟體一般都存在於本機郵件系統而可以使用，但是呼叫器供應商必須提供這項服務。</span><span class="sxs-lookup"><span data-stu-id="a80d9-127">The pager provider must offer this service, although the software required is generally available as part of the local mail system.</span></span> <span data-ttu-id="a80d9-128">如需詳細資訊，請參閱您的呼叫器文件集。</span><span class="sxs-lookup"><span data-stu-id="a80d9-128">For more information, see your pager documentation.</span></span>  
  
    -   <span data-ttu-id="a80d9-129">透過 Internet，將電子郵件路由傳送到位於呼叫器供應商站台的電子郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="a80d9-129">Routing the e-mail by way of the Internet to an e-mail server at the pager provider's site.</span></span>  
  
         <span data-ttu-id="a80d9-130">這是第一個方法的另一種做法。</span><span class="sxs-lookup"><span data-stu-id="a80d9-130">This is a variation on the first approach.</span></span>  
  
    -   <span data-ttu-id="a80d9-131">處理傳入電子郵件，並使用連接的數據機來撥接呼叫器。</span><span class="sxs-lookup"><span data-stu-id="a80d9-131">Processing the inbound e-mail and dialing the pager by using an attached modem.</span></span>  
  
         <span data-ttu-id="a80d9-132">這個軟體是呼叫器服務供應商的專利。</span><span class="sxs-lookup"><span data-stu-id="a80d9-132">This software is proprietary to pager service providers.</span></span> <span data-ttu-id="a80d9-133">這個軟體的作用像是電子郵件用戶端，可將所有或部分電子郵件地址資訊解譯成呼叫器號碼，或是將電子郵件名稱對應到轉換表中的呼叫器號碼，以定期處理其收件匣。</span><span class="sxs-lookup"><span data-stu-id="a80d9-133">The software acts as a e-mail client that periodically processes its inbox either by interpreting all or part of the e-mail address information as a pager number, or by matching the e-mail name to a pager number in a translation table.</span></span>  
  
         <span data-ttu-id="a80d9-134">如果所有的操作員共用同一個呼叫器供應商，您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來指定呼叫器轉電子郵件系統所需的任何特殊電子郵件格式。</span><span class="sxs-lookup"><span data-stu-id="a80d9-134">If all of the operators share a pager provider, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to specify any special e-mail formatting that is required by the pager-to-e-mail system.</span></span> <span data-ttu-id="a80d9-135">此特殊格式可以是前置詞或後置詞，並可包含在下列的電子郵件字行中：</span><span class="sxs-lookup"><span data-stu-id="a80d9-135">The special formatting can be a prefix or a suffix and can be included in the following lines of the e-mail:</span></span>  
  
         <span data-ttu-id="a80d9-136">**主體：**</span><span class="sxs-lookup"><span data-stu-id="a80d9-136">**Subject:**</span></span>  
  
         <span data-ttu-id="a80d9-137">副本：</span><span class="sxs-lookup"><span data-stu-id="a80d9-137">**Cc**:</span></span>  
  
         <span data-ttu-id="a80d9-138">**收件者**：</span><span class="sxs-lookup"><span data-stu-id="a80d9-138">**To**:</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a80d9-139">如果使用低容量的英數字元呼叫系統，您可以將呼叫器通知中的錯誤文字排除，以縮短所傳送的文字。</span><span class="sxs-lookup"><span data-stu-id="a80d9-139">If you use a low-capacity alphanumeric paging system, you can shorten the text that is sent by excluding the error text from the pager notification.</span></span> <span data-ttu-id="a80d9-140">例如，有一種低容量英數字元呼叫系統，每頁限制為 64 個字元。</span><span class="sxs-lookup"><span data-stu-id="a80d9-140">An example of a low-capacity alphanumeric paging system is one that is limited to 64 characters per page.</span></span>  
  
-   <span data-ttu-id="a80d9-141">**net sendnotification**</span><span class="sxs-lookup"><span data-stu-id="a80d9-141">**net sendnotification**</span></span>  
  
     <span data-ttu-id="a80d9-142">這是利用 **net send** 命令來將訊息傳送給操作員。</span><span class="sxs-lookup"><span data-stu-id="a80d9-142">This sends a message to the operator by means of the **net send** command.</span></span> <span data-ttu-id="a80d9-143">若是使用 **net send**，請指定網路訊息的收件者 (電腦或使用者)。</span><span class="sxs-lookup"><span data-stu-id="a80d9-143">For **net send**, specify the recipient (computer or user) of a network message.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a80d9-144">**Net send** 命令會使用 Microsoft Windows Messenger。</span><span class="sxs-lookup"><span data-stu-id="a80d9-144">The **net send** command uses Microsoft Windows Messenger.</span></span> <span data-ttu-id="a80d9-145">為了順利傳送警示，執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的電腦和操作員所使用的電腦上，都必須執行此服務。</span><span class="sxs-lookup"><span data-stu-id="a80d9-145">To successfully send alerts, this service must be running on both the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running and the computer that the operator uses.</span></span>  
  
## <a name="alerting-and-fail-safe-operators"></a><span data-ttu-id="a80d9-146">警示及保全操作員</span><span class="sxs-lookup"><span data-stu-id="a80d9-146">Alerting and Fail-Safe Operators</span></span>  
 <span data-ttu-id="a80d9-147">您可以選擇要告知的操作員來回應警示。</span><span class="sxs-lookup"><span data-stu-id="a80d9-147">You can choose which operators are to be notified in response to an alert.</span></span> <span data-ttu-id="a80d9-148">例如，您可以排定警示，來指派操作員通知的輪替責任區分。</span><span class="sxs-lookup"><span data-stu-id="a80d9-148">For example, you can assign rotating responsibilities for operator notification by scheduling alerts.</span></span> <span data-ttu-id="a80d9-149">例如，發生於星期一、星期三或星期五的警示會告知「人員 A」，而發生於星期二、星期四或星期六的警示則會告知「人員 B」。</span><span class="sxs-lookup"><span data-stu-id="a80d9-149">For example, Individual A is notified of alerts that occur on Monday, Wednesday, or Friday, and Individual B is notified of alerts that occur on Tuesday, Thursday, or Saturday.</span></span>  
  
 <span data-ttu-id="a80d9-150">如果所有要傳送給指定操作員的呼叫器通知都失敗，保全操作員就會收到警示通知。</span><span class="sxs-lookup"><span data-stu-id="a80d9-150">The fail-safe operator receives an alert notification after all pager notifications to the designated operators have failed.</span></span> <span data-ttu-id="a80d9-151">例如，如果您已經定義三個呼叫器告知的操作員，但是沒有一個指定的操作員可以呼叫成功，那麼將會告知保全操作員。</span><span class="sxs-lookup"><span data-stu-id="a80d9-151">For example, if you have defined three operators for pager notifications and none of the designated operators can be paged, the fail-safe operator is notified.</span></span>  
  
 <span data-ttu-id="a80d9-152">發生下列狀況時，會通知保全操作員：</span><span class="sxs-lookup"><span data-stu-id="a80d9-152">The fail-safe operator is notified when:</span></span>  
  
-   <span data-ttu-id="a80d9-153">無法呼叫到負責警示的操作員。</span><span class="sxs-lookup"><span data-stu-id="a80d9-153">The operators responsible for the alert could not be paged.</span></span>  
  
     <span data-ttu-id="a80d9-154">連絡主要操作員會失敗的原因，包括：呼叫器號碼錯誤，以及操作員已下班。</span><span class="sxs-lookup"><span data-stu-id="a80d9-154">Reasons for failure to reach primary operators include incorrect pager addresses and off-duty operators.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a80d9-155">Agent 無法存取 **msdb** 資料庫中的系統資料表。</span><span class="sxs-lookup"><span data-stu-id="a80d9-155">Agent cannot access system tables in the **msdb** database.</span></span>  
  
     <span data-ttu-id="a80d9-156">**sysnotifications** 系統資料表指定負責警示的操作員。</span><span class="sxs-lookup"><span data-stu-id="a80d9-156">The **sysnotifications** system table specifies operator responsibilities for alerts.</span></span>  
  
 <span data-ttu-id="a80d9-157">保全操作員是一種安全功能。</span><span class="sxs-lookup"><span data-stu-id="a80d9-157">The fail-safe operator is a security feature.</span></span> <span data-ttu-id="a80d9-158">若您要刪除負有保全任務的操作員，您必須先將保全任務重新指派給另一個操作員，或是刪除整個保全指派任務。</span><span class="sxs-lookup"><span data-stu-id="a80d9-158">You cannot delete the operator assigned to fail-safe duty without reassigning fail-safe duty to another operator, or deleting the fail-safe assignment altogether.</span></span>  
  
## <a name="notifying-an-operator"></a><span data-ttu-id="a80d9-159">通知操作員</span><span class="sxs-lookup"><span data-stu-id="a80d9-159">Notifying an Operator</span></span>  
 <span data-ttu-id="a80d9-160">您必須設定下列一項或多項，才能通知操作員：</span><span class="sxs-lookup"><span data-stu-id="a80d9-160">You must set up one or more of the following in order to notify an operator:</span></span>  
  
-   <span data-ttu-id="a80d9-161">若要使用 Database Mail 功能來傳送電子郵件，您必須能夠存取支援 SMTP 的電子郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="a80d9-161">To send e-mail with Database Mail functionality, you must have access to an e-mail server that supports SMTP.</span></span>  
  
-   <span data-ttu-id="a80d9-162">若是使用呼叫器，您必須要有協力廠商呼叫器轉電子郵件的軟體及/或硬體。</span><span class="sxs-lookup"><span data-stu-id="a80d9-162">For paging, you must have third-party pager-to-e-mail software and/or hardware.</span></span>  
  
-   <span data-ttu-id="a80d9-163">若要使用 **net send**，操作員必須登入指定的電腦，而指定的電腦必須能夠接受來自 Windows Messenger 的訊息。</span><span class="sxs-lookup"><span data-stu-id="a80d9-163">To use **net send**, the operator must be logged on to the specified computer, and the specified computer must allow messages from Windows Messenger.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="a80d9-164">相關工作</span><span class="sxs-lookup"><span data-stu-id="a80d9-164">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a80d9-165">**工作**</span><span class="sxs-lookup"><span data-stu-id="a80d9-165">**Tasks**</span></span>|<span data-ttu-id="a80d9-166">**主題**</span><span class="sxs-lookup"><span data-stu-id="a80d9-166">**Topic**</span></span>|  
|<span data-ttu-id="a80d9-167">與建立操作員相關的工作</span><span class="sxs-lookup"><span data-stu-id="a80d9-167">Tasks related to creating an operator</span></span>|[<span data-ttu-id="a80d9-168">建立操作員</span><span class="sxs-lookup"><span data-stu-id="a80d9-168">Create an Operator</span></span>](create-an-operator.md)<br /><br /> [<span data-ttu-id="a80d9-169">Designate a Fail-Safe Operator</span><span class="sxs-lookup"><span data-stu-id="a80d9-169">Designate a Fail-Safe Operator</span></span>](designate-a-fail-safe-operator.md)|  
|<span data-ttu-id="a80d9-170">與指派警示相關的工作</span><span class="sxs-lookup"><span data-stu-id="a80d9-170">Tasks related to assigning alerts</span></span>|[<span data-ttu-id="a80d9-171">指派警示給操作員</span><span class="sxs-lookup"><span data-stu-id="a80d9-171">Assign Alerts to an Operator</span></span>](assign-alerts-to-an-operator.md)<br /><br /> [<span data-ttu-id="a80d9-172">定義對警示的回應 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a80d9-172">Define the Response to an Alert &#40;SQL Server Management Studio&#41;</span></span>](define-the-response-to-an-alert-sql-server-management-studio.md)<br /><br /> [<span data-ttu-id="a80d9-173">sp_add_notification &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="a80d9-173">sp_add_notification &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)<br /><br /> [<span data-ttu-id="a80d9-174">指派警示給操作員</span><span class="sxs-lookup"><span data-stu-id="a80d9-174">Assign Alerts to an Operator</span></span>](assign-alerts-to-an-operator.md)|  
  
## <a name="see-also"></a><span data-ttu-id="a80d9-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a80d9-175">See Also</span></span>  
 [<span data-ttu-id="a80d9-176">Database Mail</span><span class="sxs-lookup"><span data-stu-id="a80d9-176">Database Mail</span></span>](../../relational-databases/database-mail/database-mail.md)  
  
  
