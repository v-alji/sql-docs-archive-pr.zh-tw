---
title: SQL Server Agent 屬性 (警示系統頁面) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.alert.f1
ms.assetid: 3e6d3bfd-20ee-4593-86cc-f65b1c08c69d
author: stevestein
ms.author: sstein
ms.openlocfilehash: ff203be21efbd99b90f02261cfe94dd49bd0d849
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599312"
---
# <a name="sql-server-agent-properties-alert-system-page"></a><span data-ttu-id="8731b-102">SQL Server Agent 屬性 (警示系統頁面)</span><span class="sxs-lookup"><span data-stu-id="8731b-102">SQL Server Agent Properties (Alert System Page)</span></span>
  <span data-ttu-id="8731b-103">使用此頁面來檢視和修改 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 警示所傳送的訊息設定。</span><span class="sxs-lookup"><span data-stu-id="8731b-103">Use this page to view and modify the settings for messages sent by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8731b-104">選項。</span><span class="sxs-lookup"><span data-stu-id="8731b-104">Options</span></span>  
 <span data-ttu-id="8731b-105">**郵件工作階段**</span><span class="sxs-lookup"><span data-stu-id="8731b-105">**Mail session**</span></span>  
 <span data-ttu-id="8731b-106">此章節中的選項會設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 郵件。</span><span class="sxs-lookup"><span data-stu-id="8731b-106">The options in this section configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Mail.</span></span>  
  
 <span data-ttu-id="8731b-107">**啟用郵件設定檔**</span><span class="sxs-lookup"><span data-stu-id="8731b-107">**Enable mail profile**</span></span>  
 <span data-ttu-id="8731b-108">啟用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 郵件。</span><span class="sxs-lookup"><span data-stu-id="8731b-108">Enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Mail.</span></span> <span data-ttu-id="8731b-109">依預設，未啟用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 郵件。</span><span class="sxs-lookup"><span data-stu-id="8731b-109">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Mail is not enabled.</span></span>  
  
 <span data-ttu-id="8731b-110">**郵件系統**</span><span class="sxs-lookup"><span data-stu-id="8731b-110">**Mail System**</span></span>  
 <span data-ttu-id="8731b-111">設定郵件系統供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 使用。</span><span class="sxs-lookup"><span data-stu-id="8731b-111">Sets the mail system for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to use.</span></span> <span data-ttu-id="8731b-112">Database Mail</span><span class="sxs-lookup"><span data-stu-id="8731b-112">Database Mail</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8731b-113">在變更電子郵件系統之後，您必須重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務，才能使變更生效。</span><span class="sxs-lookup"><span data-stu-id="8731b-113">After changing the e-mail system, you must restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service for the change to take effect.</span></span>  
  
 <span data-ttu-id="8731b-114">**郵件設定檔**</span><span class="sxs-lookup"><span data-stu-id="8731b-114">**Mail Profile**</span></span>  
 <span data-ttu-id="8731b-115">設定設定檔供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 使用。</span><span class="sxs-lookup"><span data-stu-id="8731b-115">Sets the profile for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to use.</span></span> <span data-ttu-id="8731b-116">您也可以選取 **\<new Database Mail profile...>** ，建立新的設定檔。</span><span class="sxs-lookup"><span data-stu-id="8731b-116">You may also select **\<new Database Mail profile...>** to create a new profile.</span></span>  
  
 <span data-ttu-id="8731b-117">**呼叫器電子郵件**</span><span class="sxs-lookup"><span data-stu-id="8731b-117">**Pager e-mails**</span></span>  
 <span data-ttu-id="8731b-118">本節中的選項可以讓您設定傳送到呼叫器號碼的電子郵件訊息，以搭配呼叫系統使用。</span><span class="sxs-lookup"><span data-stu-id="8731b-118">The options in this section allow you to configure e-mail messages sent to pager addresses to work with your paging system.</span></span>  
  
 <span data-ttu-id="8731b-119">**呼叫器電子郵件位址格式**</span><span class="sxs-lookup"><span data-stu-id="8731b-119">**Address formatting for pager e-mails**</span></span>  
 <span data-ttu-id="8731b-120">此章節可以讓您指定位址格式，以及呼叫器電子郵件中所包含的主旨。</span><span class="sxs-lookup"><span data-stu-id="8731b-120">This section allows you to specify the format of the addresses and the subject line included in pager e-mails.</span></span>  
  
 <span data-ttu-id="8731b-121">**收件者**</span><span class="sxs-lookup"><span data-stu-id="8731b-121">**To line**</span></span>  
 <span data-ttu-id="8731b-122">指定訊息之 [收件者]  的選項</span><span class="sxs-lookup"><span data-stu-id="8731b-122">Specifies the options for the **To** line of the message</span></span>  
  
 <span data-ttu-id="8731b-123">**Prefix**</span><span class="sxs-lookup"><span data-stu-id="8731b-123">**Prefix**</span></span>  
 <span data-ttu-id="8731b-124">在傳送到呼叫器的訊息之 [收件者]  的開頭處，輸入系統要求的任何固定文字。</span><span class="sxs-lookup"><span data-stu-id="8731b-124">Type any fixed text that your system requires at the beginning of the **To** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="8731b-125">**呼叫器**</span><span class="sxs-lookup"><span data-stu-id="8731b-125">**Pager**</span></span>  
 <span data-ttu-id="8731b-126">在前置詞與後置詞之間包含訊息的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="8731b-126">Includes the e-mail address for the message between the prefix and the suffix.</span></span>  
  
 <span data-ttu-id="8731b-127">**尾碼**</span><span class="sxs-lookup"><span data-stu-id="8731b-127">**Suffix**</span></span>  
 <span data-ttu-id="8731b-128">在傳送到呼叫器的訊息之 [收件者]  的結尾處，輸入呼叫器系統要求的任何固定文字。</span><span class="sxs-lookup"><span data-stu-id="8731b-128">Type any fixed text that your paging system requires at the end of the **To** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="8731b-129">**副本**</span><span class="sxs-lookup"><span data-stu-id="8731b-129">**Cc line**</span></span>  
 <span data-ttu-id="8731b-130">指定訊息之 [副本]  的選項。</span><span class="sxs-lookup"><span data-stu-id="8731b-130">Specifies options for the **Cc** line of the message.</span></span>  
  
 <span data-ttu-id="8731b-131">**Prefix**</span><span class="sxs-lookup"><span data-stu-id="8731b-131">**Prefix**</span></span>  
 <span data-ttu-id="8731b-132">在傳送到呼叫器的訊息之 [副本]  的開頭處，輸入系統要求的任何固定文字。</span><span class="sxs-lookup"><span data-stu-id="8731b-132">Type any fixed text that your system requires at the beginning of the **Cc** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="8731b-133">**呼叫器**</span><span class="sxs-lookup"><span data-stu-id="8731b-133">**Pager**</span></span>  
 <span data-ttu-id="8731b-134">在前置詞與後置詞之間包含訊息的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="8731b-134">Includes the e-mail address for the message between the prefix and the suffix.</span></span>  
  
 <span data-ttu-id="8731b-135">**尾碼**</span><span class="sxs-lookup"><span data-stu-id="8731b-135">**Suffix**</span></span>  
 <span data-ttu-id="8731b-136">在傳送到呼叫器的訊息之 [副本]  的結尾處，輸入呼叫器系統要求的任何固定文字。</span><span class="sxs-lookup"><span data-stu-id="8731b-136">Type any fixed text that your paging system requires at the end of the **Cc** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="8731b-137">**主旨**</span><span class="sxs-lookup"><span data-stu-id="8731b-137">**Subject**</span></span>  
 <span data-ttu-id="8731b-138">指定訊息主旨的選項。</span><span class="sxs-lookup"><span data-stu-id="8731b-138">Specifies the options for the subject of the message.</span></span>  
  
 <span data-ttu-id="8731b-139">**Prefix**</span><span class="sxs-lookup"><span data-stu-id="8731b-139">**Prefix**</span></span>  
 <span data-ttu-id="8731b-140">在傳送到呼叫器的訊息之 [主旨]  的開頭處，輸入呼叫器系統要求的任何固定文字。</span><span class="sxs-lookup"><span data-stu-id="8731b-140">Type any fixed text that your paging system requires at the beginning of the **Subject** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="8731b-141">**尾碼**</span><span class="sxs-lookup"><span data-stu-id="8731b-141">**Suffix**</span></span>  
 <span data-ttu-id="8731b-142">在傳送到呼叫器的訊息之 [主旨]  的結尾處，輸入呼叫器系統要求的任何固定文字。</span><span class="sxs-lookup"><span data-stu-id="8731b-142">Type any fixed text that your paging system requires at the end of the **Subject** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="8731b-143">**在通知訊息中包含主體**</span><span class="sxs-lookup"><span data-stu-id="8731b-143">**Include body of e-mail in notification message**</span></span>  
 <span data-ttu-id="8731b-144">在傳送給呼叫器的訊息中，包含電子郵件訊息的主體。</span><span class="sxs-lookup"><span data-stu-id="8731b-144">Includes the body of the e-mail message in the message sent to the pager.</span></span>  
  
 <span data-ttu-id="8731b-145">**保全操作員**</span><span class="sxs-lookup"><span data-stu-id="8731b-145">**Fail-safe operator**</span></span>  
 <span data-ttu-id="8731b-146">此章節可以讓您指定保全操作員的選項。</span><span class="sxs-lookup"><span data-stu-id="8731b-146">This section allows you to specify the options for the fail-safe operator.</span></span>  
  
 <span data-ttu-id="8731b-147">**啟用保全操作員**</span><span class="sxs-lookup"><span data-stu-id="8731b-147">**Enable fail-safe operator**</span></span>  
 <span data-ttu-id="8731b-148">指定保全操作員。</span><span class="sxs-lookup"><span data-stu-id="8731b-148">Specifies a fail safe operator.</span></span>  
  
 <span data-ttu-id="8731b-149">**運算子**</span><span class="sxs-lookup"><span data-stu-id="8731b-149">**Operator**</span></span>  
 <span data-ttu-id="8731b-150">設定要接收保全通知的操作員名稱。</span><span class="sxs-lookup"><span data-stu-id="8731b-150">Sets the name of the operator to receive fail-safe notifications.</span></span>  
  
 <span data-ttu-id="8731b-151">**通知使用**</span><span class="sxs-lookup"><span data-stu-id="8731b-151">**Notify using**</span></span>  
 <span data-ttu-id="8731b-152">設定通知保全操作員的方法。</span><span class="sxs-lookup"><span data-stu-id="8731b-152">Sets the method to use for notifying the fail-safe operator.</span></span>  
  
 <span data-ttu-id="8731b-153">**Token 取代**</span><span class="sxs-lookup"><span data-stu-id="8731b-153">**Token Replacement**</span></span>  
 <span data-ttu-id="8731b-154">此章節可讓您啟動作業步驟 Token，這些 Token 可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 警示所執行的作業中使用。</span><span class="sxs-lookup"><span data-stu-id="8731b-154">This section allows you to enable job step tokens that can be used in jobs run by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span> <span data-ttu-id="8731b-155">如需有關作業步驟 Token 的詳細資訊，請參閱 [在作業步驟中使用 Token](use-tokens-in-job-steps.md)。</span><span class="sxs-lookup"><span data-stu-id="8731b-155">For more information about job step tokens, see [Use Tokens in Job Steps](use-tokens-in-job-steps.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8731b-156">在 Windows 事件記錄檔上具有寫入權限的任何 Windows 使用者，可以存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 警示所啟動的作業步驟。</span><span class="sxs-lookup"><span data-stu-id="8731b-156">Any Windows user with write permissions on the Windows Event Log may be able to access job steps that are activated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span> <span data-ttu-id="8731b-157">為了避免此安全性風險，依預設會停用在警示啟動的作業中可以使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Token。</span><span class="sxs-lookup"><span data-stu-id="8731b-157">To avoid this security risk, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent tokens that can be used in jobs activated by alerts are disabled by default.</span></span> <span data-ttu-id="8731b-158">這些 Token 包括： **$(A-DBN)** 、 **$(A-SVR)** 、 **$(A-ERR)** 、 **$(A-SEV)** 和 **$(A-MSG)** 。</span><span class="sxs-lookup"><span data-stu-id="8731b-158">These tokens are: **$(A-DBN)**, **$(A-SVR)**, **$(A-ERR)**, **$(A-SEV)**, and **$(A-MSG)**.</span></span>  
>   
>  <span data-ttu-id="8731b-159">如果您需要使用這些 Token，在啟用之前，請確定只有信任的 Windows 安全性群組的成員，例如 Administrators 群組，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所在的電腦的事件記錄檔上才具有寫入權限。</span><span class="sxs-lookup"><span data-stu-id="8731b-159">If you need to use these tokens, ensure that only members of trusted Windows security groups, such as the Administrators group, have write permissions on the Event Log of the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resides before enabling them.</span></span>  
  
 <span data-ttu-id="8731b-160">**取代回應警示之所有作業的 Token**</span><span class="sxs-lookup"><span data-stu-id="8731b-160">**Replace tokens for all job responses to alerts**</span></span>  
 <span data-ttu-id="8731b-161">選取此核取方塊，以允許在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 警示所啟動的作業上取代 Token。</span><span class="sxs-lookup"><span data-stu-id="8731b-161">Select this check box to enable token replacement for jobs that are activated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alerts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8731b-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8731b-162">See Also</span></span>  
 <span data-ttu-id="8731b-163">[人員](operators.md) </span><span class="sxs-lookup"><span data-stu-id="8731b-163">[Operators](operators.md) </span></span>  
 <span data-ttu-id="8731b-164">[設定 SQL Server Agent Mail 以使用 Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md) </span><span class="sxs-lookup"><span data-stu-id="8731b-164">[Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md) </span></span>  
 [<span data-ttu-id="8731b-165">Database Mail</span><span class="sxs-lookup"><span data-stu-id="8731b-165">Database Mail</span></span>](../../relational-databases/database-mail/database-mail.md)  
  
  
