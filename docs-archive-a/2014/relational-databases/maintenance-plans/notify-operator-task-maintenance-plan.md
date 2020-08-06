---
title: 通知操作員工作 (維護計畫) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.notifyoperator.f1
helpviewer_keywords:
- Notify Operator Task dialog box
ms.assetid: 39c0797c-ad2b-4591-85c9-a23a7f902895
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4feb59622c2a42de67193c75d545a6b8a2a08863
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597117"
---
# <a name="notify-operator-task-maintenance-plan"></a><span data-ttu-id="0af00-102">通知操作員工作 (維護計畫)</span><span class="sxs-lookup"><span data-stu-id="0af00-102">Notify Operator Task (Maintenance Plan)</span></span>
  <span data-ttu-id="0af00-103">使用 **[通知操作員工作]** 對話方塊，將自動通知加入此維護計畫。</span><span class="sxs-lookup"><span data-stu-id="0af00-103">Use the **Notify Operators Task** dialog to add an automatic notification to this maintenance plan.</span></span> <span data-ttu-id="0af00-104">若要使用這項工作，您必須先啟用 Database Mail，並正確設定 MSDB 作為郵件主機資料庫，同時擁有具有效電子郵件地址的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 運算子。</span><span class="sxs-lookup"><span data-stu-id="0af00-104">To use this task you must have Database Mail enabled and properly configured with MSDB as a Mail Host Database, and have a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operator with a valid e-mail address.</span></span>  
  
 <span data-ttu-id="0af00-105">這項工作會使用 sp_notify_operator 預存程序。</span><span class="sxs-lookup"><span data-stu-id="0af00-105">This task uses the sp_notify_operator stored procedure.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0af00-106">選項。</span><span class="sxs-lookup"><span data-stu-id="0af00-106">Options</span></span>  
 <span data-ttu-id="0af00-107">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="0af00-107">**Connection**</span></span>  
 <span data-ttu-id="0af00-108">選取執行此工作時要使用的伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="0af00-108">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="0af00-109">**新增**</span><span class="sxs-lookup"><span data-stu-id="0af00-109">**New**</span></span>  
 <span data-ttu-id="0af00-110">建立新的伺服器連接，以便執行此工作時使用。</span><span class="sxs-lookup"><span data-stu-id="0af00-110">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="0af00-111">下面會描述 **[新增連接]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0af00-111">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="0af00-112">**要通知的操作員**</span><span class="sxs-lookup"><span data-stu-id="0af00-112">**Operators to notify**</span></span>  
 <span data-ttu-id="0af00-113">指定電子郵件的收件者。</span><span class="sxs-lookup"><span data-stu-id="0af00-113">Specify the recipient of the e-mail.</span></span>  
  
 <span data-ttu-id="0af00-114">**通知訊息主旨**</span><span class="sxs-lookup"><span data-stu-id="0af00-114">**Notification message subject**</span></span>  
 <span data-ttu-id="0af00-115">指定通知訊息主旨行中要包含的文字。</span><span class="sxs-lookup"><span data-stu-id="0af00-115">Specify the text to include in the notification message subject line.</span></span>  
  
 <span data-ttu-id="0af00-116">**通知訊息主體**</span><span class="sxs-lookup"><span data-stu-id="0af00-116">**Notification message body**</span></span>  
 <span data-ttu-id="0af00-117">指定通知訊息主體中要包含的文字。</span><span class="sxs-lookup"><span data-stu-id="0af00-117">Specify the text to include in the notification message body.</span></span>  
  
 <span data-ttu-id="0af00-118">**檢視 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="0af00-118">**View T-SQL**</span></span>  
 <span data-ttu-id="0af00-119">根據選取的選項，檢視此工作在伺服器上執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0af00-119">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0af00-120">受影響的物件數目較為大量時，會多花一些時間才會顯示。</span><span class="sxs-lookup"><span data-stu-id="0af00-120">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="0af00-121">新增連接對話方塊</span><span class="sxs-lookup"><span data-stu-id="0af00-121">New Connection Dialog Box</span></span>  
 <span data-ttu-id="0af00-122">**連線名稱**</span><span class="sxs-lookup"><span data-stu-id="0af00-122">**Connection name**</span></span>  
 <span data-ttu-id="0af00-123">輸入新連接的名稱。</span><span class="sxs-lookup"><span data-stu-id="0af00-123">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="0af00-124">**選取或輸入伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="0af00-124">**Select or enter a server name**</span></span>  
 <span data-ttu-id="0af00-125">選取執行此工作時要連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="0af00-125">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="0af00-126">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="0af00-126">**Refresh**</span></span>  
 <span data-ttu-id="0af00-127">重新整理可用的伺服器清單。</span><span class="sxs-lookup"><span data-stu-id="0af00-127">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="0af00-128">**輸入要登入到伺服器的資訊**</span><span class="sxs-lookup"><span data-stu-id="0af00-128">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="0af00-129">指定如何對伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="0af00-129">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="0af00-130">**使用 Windows 整合式安全性**</span><span class="sxs-lookup"><span data-stu-id="0af00-130">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="0af00-131">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 驗證連線到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0af00-131">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="0af00-132">**使用特定的使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="0af00-132">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="0af00-133">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連線到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0af00-133">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="0af00-134">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="0af00-134">This option is not available.</span></span>  
  
 <span data-ttu-id="0af00-135">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="0af00-135">**User name**</span></span>  
 <span data-ttu-id="0af00-136">提供驗證時要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="0af00-136">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="0af00-137">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="0af00-137">This option is not available.</span></span>  
  
 <span data-ttu-id="0af00-138">**密碼**</span><span class="sxs-lookup"><span data-stu-id="0af00-138">**Password**</span></span>  
 <span data-ttu-id="0af00-139">提供驗證時要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="0af00-139">Provide a password to use when authenticating.</span></span> <span data-ttu-id="0af00-140">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="0af00-140">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0af00-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0af00-141">See Also</span></span>  
 <span data-ttu-id="0af00-142">[Database Mail](../database-mail/database-mail.md) </span><span class="sxs-lookup"><span data-stu-id="0af00-142">[Database Mail](../database-mail/database-mail.md) </span></span>  
 [<span data-ttu-id="0af00-143">sp_notify_operator &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0af00-143">sp_notify_operator &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql)  
  
  
