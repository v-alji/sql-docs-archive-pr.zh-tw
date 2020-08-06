---
title: Debug 商務邏輯處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- merge replication business logic handlers [SQL Server replication]
- business logic handlers [SQL Server replication]
- BusinessLogicModule class
ms.assetid: edd0d17a-0e9c-4c28-8395-a7d47e8ce3d6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7b255407783b1e52a376e562ec910f8b123e42c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585886"
---
# <a name="debug-a-business-logic-handler-replication-programming"></a><span data-ttu-id="aef8f-102">偵錯商務邏輯處理常式 (複寫程式設計)</span><span class="sxs-lookup"><span data-stu-id="aef8f-102">Debug a Business Logic Handler (Replication Programming)</span></span>
  <span data-ttu-id="aef8f-103">使用商務邏輯處理常式，以便在同步處理合併訂閱期間叫用自訂商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="aef8f-103">Use a business logic handler to invoke custom business logic when a merge subscription is synchronized.</span></span> <span data-ttu-id="aef8f-104">如需詳細資訊，請參閱[在合併同步處理期間執行商務邏輯](merge/execute-business-logic-during-merge-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="aef8f-104">For more information, see [Execute Business Logic During Merge Synchronization](merge/execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="aef8f-105">合併式複寫重新調整器 (replrec.dll) 會呼叫包含此商務邏輯的 Managed 程式碼組件。</span><span class="sxs-lookup"><span data-stu-id="aef8f-105">The Merge Replication Reconciler (replrec.dll) calls the managed code assembly containing the business logic.</span></span> <span data-ttu-id="aef8f-106">在大部分情況下，會在合併代理程式執行所在的電腦上執行 replrec.dll 和自訂商務邏輯 (如果是提取訂閱，會在訂閱者上；如果是發送訂閱，則會在散發者上)。</span><span class="sxs-lookup"><span data-stu-id="aef8f-106">In most cases, replrec.dll and the custom business logic is executed on the computer where the Merge Agent runs (at the Subscriber for a pull subscription or at the Distributor for a push subscription).</span></span> <span data-ttu-id="aef8f-107">如果是 Web 同步處理的情況或 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 訂閱者的情況，會在 Web 伺服器上執行此調整器和自訂商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="aef8f-107">In the case of Web synchronization, or in the case of a [!INCLUDE[ssEW](../../includes/ssew-md.md)] Subscriber, the reconciler and the custom business logic is executed on the Web server.</span></span>  
  
### <a name="to-debug-a-business-logic-handler-on-a-local-computer"></a><span data-ttu-id="aef8f-108">在本機電腦上偵錯商務邏輯處理常式</span><span class="sxs-lookup"><span data-stu-id="aef8f-108">To debug a business logic handler on a local computer</span></span>  
  
1.  <span data-ttu-id="aef8f-109">設定發行和散發、建立發行集，以及建立發行集的訂閱。</span><span class="sxs-lookup"><span data-stu-id="aef8f-109">Configure publishing and distribution, create a publication, and create a subscription to the publication.</span></span> <span data-ttu-id="aef8f-110">如需詳細資訊，請參閱[設定發行和散發](configure-publishing-and-distribution.md)及[建立發行集](publish/create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="aef8f-110">For more information, see [Configure Publishing and Distribution](configure-publishing-and-distribution.md) and [Create a Publication](publish/create-a-publication.md).</span></span>  
  
2.  <span data-ttu-id="aef8f-111">建立及註冊商務邏輯處理常式。</span><span class="sxs-lookup"><span data-stu-id="aef8f-111">Create and register a business logic handler.</span></span> <span data-ttu-id="aef8f-112">如需詳細資訊，請參閱 [為合併發行項實作商務邏輯處理常式](implement-a-business-logic-handler-for-a-merge-article.md)。</span><span class="sxs-lookup"><span data-stu-id="aef8f-112">For more information, see [Implement a Business Logic Handler for a Merge Article](implement-a-business-logic-handler-for-a-merge-article.md).</span></span>  
  
3.  <span data-ttu-id="aef8f-113">在以程式設計方式同步啟動合併代理程式的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 中，建立 Replication Management Objects (RMO) 專案。</span><span class="sxs-lookup"><span data-stu-id="aef8f-113">Create a Replication Management Objects (RMO) project in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio that programmatically starts the Merge Agent synchronously.</span></span> <span data-ttu-id="aef8f-114">如需相關資訊，請參閱 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="aef8f-114">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
4.  <span data-ttu-id="aef8f-115">在商務邏輯處理常式程式碼中設定中斷點 (在所偵錯的方法中或是類別建構函式中)。</span><span class="sxs-lookup"><span data-stu-id="aef8f-115">Set a breakpoint in the business logic handler code, either in the method being debugged or in the class constructor.</span></span> <span data-ttu-id="aef8f-116">如需有關可以在商務邏輯處理常式中實作之方法的詳細資訊，請參閱 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 方法主題。</span><span class="sxs-lookup"><span data-stu-id="aef8f-116">For more information about the methods that can be implemented in a business logic handler, see the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> methods topic.</span></span>  
  
5.  <span data-ttu-id="aef8f-117">在偵錯模式下建立此商務邏輯處理常式，並在步驟 1 註冊的位置中部署此組件和偵錯符號檔 (.pdb)。</span><span class="sxs-lookup"><span data-stu-id="aef8f-117">Build the business logic handler in debug mode and deploy the assembly and debugging symbol file (.pdb) in the location registered in step 1.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="aef8f-118">若要簡化偵錯，請建立一個同時包含商務邏輯處理常式專案和同步處理訂閱之專案的 Visual Studio .NET 方案。</span><span class="sxs-lookup"><span data-stu-id="aef8f-118">To simplify debugging, create a single Visual Studio .NET solution that contains both the business logic handler project and the project that synchronizes the subscription.</span></span> <span data-ttu-id="aef8f-119">在此情況下，請將同步處理專案設定為啟始專案，並設定建立環境，將商務邏輯組件部署到步驟 1 偵錯時所註冊的位置中。</span><span class="sxs-lookup"><span data-stu-id="aef8f-119">In this case, set the synchronization project as the startup project, and configure the build environment to deploy the business logic assembly to the location registered in step 1 during debugging.</span></span>  
  
6.  <span data-ttu-id="aef8f-120">針對訂閱或發行集資料庫執行插入、更新或刪除命令。</span><span class="sxs-lookup"><span data-stu-id="aef8f-120">Execute insert, update, or delete commands against the subscription or publication database.</span></span> <span data-ttu-id="aef8f-121">此命令和執行位置取決於所偵錯的方法而定。</span><span class="sxs-lookup"><span data-stu-id="aef8f-121">The command and execution location depends on the method being debugged.</span></span>  
  
7.  <span data-ttu-id="aef8f-122">在偵錯模式下從步驟 3 啟動此專案，以同步處理訂閱。</span><span class="sxs-lookup"><span data-stu-id="aef8f-122">Start the project from step 3 in debug mode to synchronize the subscription.</span></span>  
  
8.  <span data-ttu-id="aef8f-123">假設未設定任何其他中斷點，而且複寫了適當的命令，則當到達商務邏輯處理常式中的中斷點時，會停止執行。</span><span class="sxs-lookup"><span data-stu-id="aef8f-123">Assuming that no other breakpoints are set and the proper commands are replicated, the execution stops when it reaches the breakpoint in the business logic handler.</span></span>  
  
### <a name="to-debug-a-business-logic-handler-on-a-web-server-using-web-synchronization-or-for-a-sql-server-compact-subscriber"></a><span data-ttu-id="aef8f-124">使用 Web 同步處理在 Web 伺服器上偵錯商務邏輯處理常式，或是針對 SQL Server Compact 訂閱者進行偵錯</span><span class="sxs-lookup"><span data-stu-id="aef8f-124">To debug a business logic handler on a Web server using Web synchronization, or for a SQL Server Compact Subscriber</span></span>  
  
1.  <span data-ttu-id="aef8f-125">設定發行和散發、建立發行集，以及建立發行集的提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="aef8f-125">Configure publishing and distribution, create a publication, and create a pull subscription to the publication.</span></span> <span data-ttu-id="aef8f-126">此發行集必須支援 Web 同步處理或 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 訂閱者。</span><span class="sxs-lookup"><span data-stu-id="aef8f-126">The publication must support Web synchronization or [!INCLUDE[ssEW](../../includes/ssew-md.md)] Subscribers.</span></span>  
  
2.  <span data-ttu-id="aef8f-127">建立及註冊商務邏輯處理常式。</span><span class="sxs-lookup"><span data-stu-id="aef8f-127">Create and register a business logic handler.</span></span> <span data-ttu-id="aef8f-128">如需詳細資訊，請參閱 [為合併發行項實作商務邏輯處理常式](implement-a-business-logic-handler-for-a-merge-article.md)。</span><span class="sxs-lookup"><span data-stu-id="aef8f-128">For more information, see [Implement a Business Logic Handler for a Merge Article](implement-a-business-logic-handler-for-a-merge-article.md).</span></span>  
  
3.  <span data-ttu-id="aef8f-129">在商務邏輯處理常式程式碼中設定中斷點 (在所偵錯的方法中或是類別建構函式中)。</span><span class="sxs-lookup"><span data-stu-id="aef8f-129">Set a breakpoint in the business logic handler code, either in the method being debugged or in the class constructor.</span></span> <span data-ttu-id="aef8f-130">如需有關可以在商務邏輯處理常式中實作之方法的詳細資訊，請參閱 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 方法主題。</span><span class="sxs-lookup"><span data-stu-id="aef8f-130">For more information about the methods that can be implemented in a business logic handler, see the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> methods topic.</span></span>  
  
4.  <span data-ttu-id="aef8f-131">在偵錯模式下建立此商務邏輯處理常式，並在步驟 1 註冊的位置中，於 Web 伺服器上部署此組件和偵錯符號檔 (.pdb)。</span><span class="sxs-lookup"><span data-stu-id="aef8f-131">Build the business logic handler in debug mode and deploy the assembly and debugging symbol file (.pdb) at the Web server in the location registered in step 1.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="aef8f-132">如果因為此組件在使用中而導致無法建立商務邏輯處理常式，請在此 Web 伺服器的命令提示字元上輸入 `iisreset` 命令，以重設 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="aef8f-132">If the business logic handler fails to build because the assembly is in use, type the command `iisreset` on the Web server at the command prompt to reset the Web server.</span></span>  
  
5.  <span data-ttu-id="aef8f-133">在啟用 Web 同步處理的情況下同步處理訂閱。</span><span class="sxs-lookup"><span data-stu-id="aef8f-133">Synchronize the subscription with Web synchronization enabled.</span></span> <span data-ttu-id="aef8f-134">在同步處理期間，Web 伺服器會載入註冊的組件。</span><span class="sxs-lookup"><span data-stu-id="aef8f-134">During synchronization, the Web server loads the registered assembly.</span></span>  
  
6.  <span data-ttu-id="aef8f-135">使用 Visual Studio .NET 偵錯工具，附加到 Web 伺服器上的下列其中一個處理序：</span><span class="sxs-lookup"><span data-stu-id="aef8f-135">Using the Visual Studio .NET debugger, attach to the one of the following processes on the Web server:</span></span>  
  
    -   <span data-ttu-id="aef8f-136">w3wp.exe - Windows Server 2003。</span><span class="sxs-lookup"><span data-stu-id="aef8f-136">w3wp.exe - Windows Server 2003.</span></span>  
  
    -   <span data-ttu-id="aef8f-137">inetinfo.exe - Windows 2000 和 Windows XP。</span><span class="sxs-lookup"><span data-stu-id="aef8f-137">inetinfo.exe - Windows 2000 and Windows XP.</span></span>  
  
7.  <span data-ttu-id="aef8f-138">在 **[輸出]** 視窗中，檢查偵錯輸出，以確認註冊之組件的符號已正確載入。</span><span class="sxs-lookup"><span data-stu-id="aef8f-138">In the **Output** window, check the debug output to verify that the symbols for the registered assembly loaded properly.</span></span> <span data-ttu-id="aef8f-139">如果未載入符號，請確定步驟 4 中是否複製了正確的 .pdb 檔案，並重複步驟 5。</span><span class="sxs-lookup"><span data-stu-id="aef8f-139">If the symbols were not loaded, ensure that the correct .pdb file was copied in step 4, and repeat step 5.</span></span>  
  
8.  <span data-ttu-id="aef8f-140">針對訂閱或發行集資料庫執行插入、更新或刪除命令。</span><span class="sxs-lookup"><span data-stu-id="aef8f-140">Execute insert, update, or delete commands against the subscription or publication database.</span></span> <span data-ttu-id="aef8f-141">此命令和執行位置取決於所偵錯的方法而定。</span><span class="sxs-lookup"><span data-stu-id="aef8f-141">The command and execution location depends on the method being debugged.</span></span>  
  
9. <span data-ttu-id="aef8f-142">使用 Visual Studio 偵錯工具，附加到 w3wp.exe 處理序。</span><span class="sxs-lookup"><span data-stu-id="aef8f-142">Using the Visual Studio debugger, attach to the w3wp.exe process.</span></span>  
  
10. <span data-ttu-id="aef8f-143">使用 Web 同步處理再次同步處理訂閱。</span><span class="sxs-lookup"><span data-stu-id="aef8f-143">Synchronize the subscription again, using Web synchronization.</span></span>  
  
11. <span data-ttu-id="aef8f-144">假設未設定任何其他中斷點，而且複寫了適當的命令，則當到達商務邏輯處理常式中的中斷點時，會停止執行。</span><span class="sxs-lookup"><span data-stu-id="aef8f-144">Assuming that no other breakpoints are set and the proper commands are replicated, the execution stops when it reaches the breakpoint in the business logic handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef8f-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aef8f-145">See Also</span></span>  
 [<span data-ttu-id="aef8f-146">為合併發行項實作商務邏輯處理常式</span><span class="sxs-lookup"><span data-stu-id="aef8f-146">Implement a Business Logic Handler for a Merge Article</span></span>](implement-a-business-logic-handler-for-a-merge-article.md)  
  
  
