---
title: 建立使用者定義的事件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent alerts, user-defined events
- user-defined events [SQL Server]
- multiple language support [SQL Server], alerts
- languages [SQL Server], alerts
- severity levels [SQL Server]
- global considerations [SQL Server], alerts
- events [SQL Server], user-defined
- SQL Server Agent alerts, multiple-language environments
- alerts [SQL Server], user-defined events
- alerts [SQL Server], multiple-language environments
- custom events [SQL Server Agent]
- international considerations [SQL Server], alerts
ms.assetid: 03d71a35-97fa-4bba-aa9a-23ac9c9cf879
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2323dc4da3d1a8a67dad41ea189877ade25eff0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710105"
---
# <a name="create-a-user-defined-event"></a><span data-ttu-id="bf33a-102">建立使用者定義的事件</span><span class="sxs-lookup"><span data-stu-id="bf33a-102">Create a User-Defined Event</span></span>
  <span data-ttu-id="bf33a-103">若要監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預先定義之事件以外的其他事件，您可以建立使用者自訂的事件。</span><span class="sxs-lookup"><span data-stu-id="bf33a-103">You can create user-defined events if you want to monitor events other than events that are predefined by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bf33a-104">您也可以指派嚴重性層級到每個使用者自訂事件。</span><span class="sxs-lookup"><span data-stu-id="bf33a-104">You can also assign a severity level to each user-defined event.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bf33a-105">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 時，請針對每個使用者自訂事件訊息選取 [寫入 Windows 應用程式事件記錄]\*\*\*\* 選項，以確保該訊息會被記錄下來。</span><span class="sxs-lookup"><span data-stu-id="bf33a-105">When using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the **Write to Windows application event log** option for each user-defined event message, to ensure that the messages are logged.</span></span> <span data-ttu-id="bf33a-106">根據預設，發生嚴重性低於 19 的使用者自訂訊息時，不會將這些訊息傳送到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 應用程式記錄。</span><span class="sxs-lookup"><span data-stu-id="bf33a-106">By default, user-defined messages of severity lower than 19 are not sent to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application log when they occur.</span></span> <span data-ttu-id="bf33a-107">因此，嚴重性低於 19 的使用者自訂訊息不會觸發 SQL Server Agent 警示。</span><span class="sxs-lookup"><span data-stu-id="bf33a-107">User-defined messages of severity lower than 19 therefore do not trigger SQL Server Agent alerts.</span></span>  
  
 <span data-ttu-id="bf33a-108">使用者自訂事件必須有唯一的訊息編號。</span><span class="sxs-lookup"><span data-stu-id="bf33a-108">User-defined events must have a unique message number.</span></span> <span data-ttu-id="bf33a-109">使用者自訂事件的訊息編號必須大於 50,000。</span><span class="sxs-lookup"><span data-stu-id="bf33a-109">Message numbers for a user-defined event must be greater than 50,000.</span></span> <span data-ttu-id="bf33a-110">您可以使用多種語言來定義事件訊息。</span><span class="sxs-lookup"><span data-stu-id="bf33a-110">You can define messages for the event in multiple languages.</span></span> <span data-ttu-id="bf33a-111">但是，必須有 **En-US** 錯誤訊息，才能新增其他語言的訊息。</span><span class="sxs-lookup"><span data-stu-id="bf33a-111">However, an **En-US** error message must exist before messages in other languages can be added.</span></span>  
  
 <span data-ttu-id="bf33a-112">如果您管理多重語言的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境，請使用每個支援的語言建立使用者定義的訊息。</span><span class="sxs-lookup"><span data-stu-id="bf33a-112">If you administer a multiple-language [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environment, create user-defined messages in each of the languages that are supported.</span></span> <span data-ttu-id="bf33a-113">例如，如果您正建立將使用在英文與德文伺服器上的新事件訊息，請為兩者使用相同的訊息編號，但為每個指派不同的語言。</span><span class="sxs-lookup"><span data-stu-id="bf33a-113">For example, if you are creating a new event message to be used on both an English and a German server, use the same message number and severity for both, but assign a different language to each.</span></span>  
  
 <span data-ttu-id="bf33a-114">下列工作提供如何建立使用者自訂事件與回應事件之警示的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="bf33a-114">The following tasks provide information about how to create user-defined events and alerts that respond to them:</span></span>  
  
 <span data-ttu-id="bf33a-115">**若要以訊息編號為基礎建立警示**</span><span class="sxs-lookup"><span data-stu-id="bf33a-115">**To create an alert based on a message number**</span></span>  
  
-   [<span data-ttu-id="bf33a-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bf33a-116">SQL Server Management Studio</span></span>](create-an-alert-using-an-error-number.md)  
  
-   [<span data-ttu-id="bf33a-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bf33a-117">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 <span data-ttu-id="bf33a-118">**若要以嚴重性層級為基礎建立警示**</span><span class="sxs-lookup"><span data-stu-id="bf33a-118">**To create an alert based on severity levels**</span></span>  
  
-   [<span data-ttu-id="bf33a-119">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bf33a-119">SQL Server Management Studio</span></span>](create-an-alert-using-severity-level.md)  
  
-   [<span data-ttu-id="bf33a-120">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bf33a-120">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 <span data-ttu-id="bf33a-121">**若要定義對警示的回應**</span><span class="sxs-lookup"><span data-stu-id="bf33a-121">**To define the response to an alert**</span></span>  
  
-   [<span data-ttu-id="bf33a-122">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bf33a-122">SQL Server Management Studio</span></span>](../sql-server-management-studio-ssms.md)  
  
-   [<span data-ttu-id="bf33a-123">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bf33a-123">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)  
  
 <span data-ttu-id="bf33a-124">**若要建立使用者自訂的事件錯誤訊息**</span><span class="sxs-lookup"><span data-stu-id="bf33a-124">**To create a user-defined event error message**</span></span>  
  
-   [<span data-ttu-id="bf33a-125">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bf33a-125">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql)  
  
 <span data-ttu-id="bf33a-126">**若要修改使用者自訂的事件錯誤訊息**</span><span class="sxs-lookup"><span data-stu-id="bf33a-126">**To modify a user-defined event error message**</span></span>  
  
-   [<span data-ttu-id="bf33a-127">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bf33a-127">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-altermessage-transact-sql)  
  
 <span data-ttu-id="bf33a-128">**若要刪除使用者自訂的事件錯誤訊息**</span><span class="sxs-lookup"><span data-stu-id="bf33a-128">**To delete a user-defined event error message**</span></span>  
  
-   [<span data-ttu-id="bf33a-129">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bf33a-129">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropmessage-transact-sql)  
  
 <span data-ttu-id="bf33a-130">**若要停用或重新啟動警示**</span><span class="sxs-lookup"><span data-stu-id="bf33a-130">**To disable or reactivate an alert**</span></span>  
  
-   [<span data-ttu-id="bf33a-131">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bf33a-131">SQL Server Management Studio</span></span>](disable-or-reactivate-an-alert.md)  
  
-   [<span data-ttu-id="bf33a-132">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bf33a-132">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="bf33a-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf33a-133">See Also</span></span>  
 [<span data-ttu-id="bf33a-134">sp_update_alert &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="bf33a-134">sp_update_alert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
  
