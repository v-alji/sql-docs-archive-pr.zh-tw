---
title: 第 1 課：建立用於複寫的 Windows 帳戶 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
- replication [SQL Server], administering
ms.assetid: 65c3816b-47f0-448c-a4a4-ebd3e2a58820
author: rothja
ms.author: jroth
ms.openlocfilehash: 29f1008338b3ba728066ed611108477586a4c899
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585812"
---
# <a name="lesson-1-creating-windows-accounts-for-replication"></a><span data-ttu-id="dce6f-102">第 1 課：建立用於複寫的 Windows 帳戶</span><span class="sxs-lookup"><span data-stu-id="dce6f-102">Lesson 1: Creating Windows Accounts for Replication</span></span>
  <span data-ttu-id="dce6f-103">在這一課，您將建立 Windows 帳戶，以執行複寫代理程式。</span><span class="sxs-lookup"><span data-stu-id="dce6f-103">In this lesson, you will create Windows accounts to run replication agents.</span></span> <span data-ttu-id="dce6f-104">您將在本機伺服器上，另外為下列代理程式建立 Windows 帳戶：</span><span class="sxs-lookup"><span data-stu-id="dce6f-104">You will create a separate Windows account on the local server for the following agents:</span></span>  
  
|<span data-ttu-id="dce6f-105">代理程式</span><span class="sxs-lookup"><span data-stu-id="dce6f-105">Agent</span></span>|<span data-ttu-id="dce6f-106">Location</span><span class="sxs-lookup"><span data-stu-id="dce6f-106">Location</span></span>|<span data-ttu-id="dce6f-107">帳戶名稱</span><span class="sxs-lookup"><span data-stu-id="dce6f-107">Account name</span></span>|  
|-----------|--------------|------------------|  
|<span data-ttu-id="dce6f-108">快照集代理程式</span><span class="sxs-lookup"><span data-stu-id="dce6f-108">Snapshot Agent</span></span>|<span data-ttu-id="dce6f-109">Publisher</span><span class="sxs-lookup"><span data-stu-id="dce6f-109">Publisher</span></span>|<span data-ttu-id="dce6f-110">\<*machine_name*>\ repl_snapshot</span><span class="sxs-lookup"><span data-stu-id="dce6f-110">\<*machine_name*>\repl_snapshot</span></span>|  
|<span data-ttu-id="dce6f-111">記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="dce6f-111">Log Reader Agent</span></span>|<span data-ttu-id="dce6f-112">Publisher</span><span class="sxs-lookup"><span data-stu-id="dce6f-112">Publisher</span></span>|<span data-ttu-id="dce6f-113">\<*machine_name*>\ repl_logreader</span><span class="sxs-lookup"><span data-stu-id="dce6f-113">\<*machine_name*>\repl_logreader</span></span>|  
|<span data-ttu-id="dce6f-114">散發代理程式</span><span class="sxs-lookup"><span data-stu-id="dce6f-114">Distribution Agent</span></span>|<span data-ttu-id="dce6f-115">發行者和訂閱者</span><span class="sxs-lookup"><span data-stu-id="dce6f-115">Publisher and Subscriber</span></span>|<span data-ttu-id="dce6f-116">\<*machine_name*>\ repl_distribution</span><span class="sxs-lookup"><span data-stu-id="dce6f-116">\<*machine_name*>\repl_distribution</span></span>|  
|<span data-ttu-id="dce6f-117">合併代理程式</span><span class="sxs-lookup"><span data-stu-id="dce6f-117">Merge Agent</span></span>|<span data-ttu-id="dce6f-118">發行者和訂閱者</span><span class="sxs-lookup"><span data-stu-id="dce6f-118">Publisher and Subscriber</span></span>|<span data-ttu-id="dce6f-119">\<*machine_name*>\ repl_merge</span><span class="sxs-lookup"><span data-stu-id="dce6f-119">\<*machine_name*>\repl_merge</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="dce6f-120">在複寫教學課程中，發行者和散發者會共用相同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="dce6f-120">In the replication tutorials, the Publisher and Distributor share the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="dce6f-121">發行者和訂閱者可以共用相同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體，但這不是必要條件。</span><span class="sxs-lookup"><span data-stu-id="dce6f-121">The Publisher and Subscriber may share the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but it is not a requirement.</span></span> <span data-ttu-id="dce6f-122">如果發行者和訂閱者共用相同的執行個體，則不需要在訂閱者上建立帳戶的步驟。</span><span class="sxs-lookup"><span data-stu-id="dce6f-122">If the Publisher and Subscriber share the same instance, the steps that are used to create accounts at the Subscriber are not required.</span></span>  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-publisher"></a><span data-ttu-id="dce6f-123">在發行者端建立複寫代理程式的本機 Windows 帳戶</span><span class="sxs-lookup"><span data-stu-id="dce6f-123">To create local Windows accounts for replication agents at the Publisher</span></span>  
  
1.  <span data-ttu-id="dce6f-124">在發行者端，從 [控制台] 中的 [系統**管理工具**] 開啟 [**電腦管理**]。</span><span class="sxs-lookup"><span data-stu-id="dce6f-124">At the Publisher, open **Computer Management** from **Administrative Tools** in Control Panel.</span></span>  
  
2.  <span data-ttu-id="dce6f-125">在 [系統工具]\*\*\*\* 中，展開 [本機使用者和群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dce6f-125">In **System Tools**, expand **Local Users and Groups**.</span></span>  
  
3.  <span data-ttu-id="dce6f-126">以滑鼠右鍵按一下 [**使用者**]，然後按一下 [**新增使用者**]。</span><span class="sxs-lookup"><span data-stu-id="dce6f-126">Right-click **Users** and then click **New User**.</span></span>  
  
4.  <span data-ttu-id="dce6f-127">`repl_snapshot`在 [**使用者名稱**] 方塊中輸入、提供密碼和其他相關資訊，然後按一下 [**建立**] 以建立 repl_snapshot 帳戶。</span><span class="sxs-lookup"><span data-stu-id="dce6f-127">Enter `repl_snapshot` in the **User name** box, provide the password and other relevant information, and then click **Create** to create the repl_snapshot account.</span></span>  
  
5.  <span data-ttu-id="dce6f-128">重複執行先前的步驟，以建立 repl_logreader、repl_distribution 和 repl_merge 帳戶。</span><span class="sxs-lookup"><span data-stu-id="dce6f-128">Repeat the previous step to create the repl_logreader, repl_distribution, and repl_merge accounts.</span></span>  
  
6.  <span data-ttu-id="dce6f-129">按一下 **關閉**。</span><span class="sxs-lookup"><span data-stu-id="dce6f-129">Click **Close**.</span></span>  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a><span data-ttu-id="dce6f-130">在訂閱者端建立複寫代理程式的本機 Windows 帳戶</span><span class="sxs-lookup"><span data-stu-id="dce6f-130">To create local Windows accounts for replication agents at the Subscriber</span></span>  
  
1.  <span data-ttu-id="dce6f-131">在訂閱者端，從 [控制台] 中的 [系統**管理工具**] 開啟 [**電腦管理**]。</span><span class="sxs-lookup"><span data-stu-id="dce6f-131">At the Subscriber, open **Computer Management** from **Administrative Tools** in Control Panel.</span></span>  
  
2.  <span data-ttu-id="dce6f-132">在 [系統工具]\*\*\*\* 中，展開 [本機使用者和群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dce6f-132">In **System Tools**, expand **Local Users and Groups**.</span></span>  
  
3.  <span data-ttu-id="dce6f-133">以滑鼠右鍵按一下 [**使用者**]，然後按一下 [**新增使用者**]。</span><span class="sxs-lookup"><span data-stu-id="dce6f-133">Right-click **Users** and then click **New User**.</span></span>  
  
4.  <span data-ttu-id="dce6f-134">`repl_distribution`在 [**使用者名稱**] 方塊中輸入、提供密碼和其他相關資訊，然後按一下 [**建立**] 以建立 repl_distribution 帳戶。</span><span class="sxs-lookup"><span data-stu-id="dce6f-134">Enter `repl_distribution` in the **User name** box, provide the password and other relevant information, and then click **Create** to create the repl_distribution account.</span></span>  
  
5.  <span data-ttu-id="dce6f-135">重複執行先前的步驟，以建立 repl_merge 帳戶。</span><span class="sxs-lookup"><span data-stu-id="dce6f-135">Repeat the previous step to create the repl_merge account.</span></span>  
  
6.  <span data-ttu-id="dce6f-136">按一下 **關閉**。</span><span class="sxs-lookup"><span data-stu-id="dce6f-136">Click **Close**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="dce6f-137">後續步驟</span><span class="sxs-lookup"><span data-stu-id="dce6f-137">Next Steps</span></span>  
 <span data-ttu-id="dce6f-138">您已順利建立複寫代理程式的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="dce6f-138">You have successfully created Windows accounts for replication agents.</span></span> <span data-ttu-id="dce6f-139">下一步，您將設定快照集資料夾。</span><span class="sxs-lookup"><span data-stu-id="dce6f-139">Next, you will configure the snapshot folder.</span></span> <span data-ttu-id="dce6f-140">請參閱 [第 2 課：準備快照集資料夾](lesson-2-preparing-the-snapshot-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="dce6f-140">See [Lesson 2: Preparing the Snapshot Folder](lesson-2-preparing-the-snapshot-folder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce6f-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dce6f-141">See Also</span></span>  
 [<span data-ttu-id="dce6f-142">複寫代理程式概觀</span><span class="sxs-lookup"><span data-stu-id="dce6f-142">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
