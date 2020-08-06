---
title: 修改控制器與用戶端服務帳戶 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 44a73ddb-18ad-415c-bfbe-126ab2e3290b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 62a054749f1d53323bde5c9d05a1e7632b1dda85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703653"
---
# <a name="modify-the-controller-and-client-services-accounts"></a><span data-ttu-id="09997-102">修改控制器服務帳戶與用戶端服務帳戶</span><span class="sxs-lookup"><span data-stu-id="09997-102">Modify the Controller and Client Services Accounts</span></span>
  <span data-ttu-id="09997-103">在本主題中，您將了解如何修改 Distributed Replay Controller 和用戶端服務帳戶，然後重新套用存取控制清單 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="09997-103">In this topic, you will learn how to modify the Distributed Replay controller and client service accounts, and then reapply the access control lists (ACLs).</span></span>  
  
### <a name="to-start-or-stop-the-distributed-replay-services-using-computer-management"></a><span data-ttu-id="09997-104">若要使用電腦管理來啟動或停止 Distributed Replay 服務</span><span class="sxs-lookup"><span data-stu-id="09997-104">To start or stop the Distributed Replay services using Computer Management</span></span>  
  
1.  <span data-ttu-id="09997-105">在安裝 Distributed Replay 服務的電腦上，於命令提示字元中輸入 `dcomcnfg`。</span><span class="sxs-lookup"><span data-stu-id="09997-105">On the computer on which the Distributed Replay services are installed, from the command prompt, type `dcomcnfg`.</span></span>  
  
2.  <span data-ttu-id="09997-106">按兩下 [**服務**]，並在\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay \<service name> **按一下滑鼠右鍵，然後按一下 [**開始**] 或 [**停止\*\*]。</span><span class="sxs-lookup"><span data-stu-id="09997-106">Double-click **Services**, scroll down and right-click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay \<service name>**, and then click **Start** or **Stop**.</span></span>  
  
### <a name="to-modify-the-distributed-replay-controller-service"></a><span data-ttu-id="09997-107">若要修改 Distributed Replay Controller 服務</span><span class="sxs-lookup"><span data-stu-id="09997-107">To modify the Distributed Replay controller service</span></span>  
  
1.  <span data-ttu-id="09997-108">在控制器電腦上，停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller 服務。</span><span class="sxs-lookup"><span data-stu-id="09997-108">On the controller computer, stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay controller service.</span></span>  
  
2.  <span data-ttu-id="09997-109">在 [服務]  底下，以滑鼠右鍵按一下 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller]  ，然後選取 [內容]  。</span><span class="sxs-lookup"><span data-stu-id="09997-109">Under **Services**, right-click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller**, and then select **Properties**.</span></span>  
  
3.  <span data-ttu-id="09997-110">在 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller 內容]  視窗的 [登入]  索引標籤上選取 [這個帳戶]  ，輸入或按一下 [瀏覽]  輸入新的登入帳戶，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="09997-110">In the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller Properties** window, on the **Log On** tab, select **This account**, type or click **Browse** to enter the new logon account, and then click **OK**.</span></span>  
  
     <span data-ttu-id="09997-111">**重要**：當您設定 Distributed Replay Controller 時，可以指定要用來執行 Distributed Replay Client 服務的一或多個使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="09997-111">**Important**: When you configure Distributed Replay Controller, you can specify one or more user accounts that will be used to run the Distributed Replay Client services.</span></span> <span data-ttu-id="09997-112">下列是支援帳戶的清單：</span><span class="sxs-lookup"><span data-stu-id="09997-112">The following is the list of supported accounts:</span></span>  
  
    -   <span data-ttu-id="09997-113">網域使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="09997-113">Domain user account</span></span>  
  
    -   <span data-ttu-id="09997-114">使用者建立的本機使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="09997-114">User created local user account</span></span>  
  
    -   <span data-ttu-id="09997-115">系統管理員</span><span class="sxs-lookup"><span data-stu-id="09997-115">Administrator</span></span>  
  
    -   <span data-ttu-id="09997-116">虛擬帳戶和 MSA (受管理的服務帳戶)</span><span class="sxs-lookup"><span data-stu-id="09997-116">Virtual account and MSA (Managed Service Account)</span></span>  
  
    -   <span data-ttu-id="09997-117">網路服務、本機系統和系統</span><span class="sxs-lookup"><span data-stu-id="09997-117">Network Services, Local Services, and System</span></span>  
  
     <span data-ttu-id="09997-118">不接受群組帳戶 (本機或網域) 和其他內建帳戶 (例如 Everyone)。</span><span class="sxs-lookup"><span data-stu-id="09997-118">Group accounts (local or domain) and other built-in accounts (like Everyone) are not accepted.</span></span>  
  
4.  <span data-ttu-id="09997-119">啟動 Distributed Replay Controller 服務。</span><span class="sxs-lookup"><span data-stu-id="09997-119">Start the Distributed Replay controller service.</span></span>  
  
### <a name="to-modify-the-distributed-replay-client-service"></a><span data-ttu-id="09997-120">若要修改 Distributed Replay Client 服務</span><span class="sxs-lookup"><span data-stu-id="09997-120">To modify the Distributed Replay client service</span></span>  
  
1.  <span data-ttu-id="09997-121">修改 Distributed Replay Client 服務之前，請先確定已在安裝期間指定您要變更的用戶端服務帳戶 (於控制器電腦的 CTLRUSERS 參數中)。</span><span class="sxs-lookup"><span data-stu-id="09997-121">Before you modify the Distributed Replay client service, make sure the client service account you are changing was specified during setup (in the CTLRUSERS parameter on the controller computer).</span></span> <span data-ttu-id="09997-122">如果未在安裝期間指定您要變更的用戶端服務帳戶，則必須先執行以下步驟：</span><span class="sxs-lookup"><span data-stu-id="09997-122">If the client service account you are changing was not specified during setup, you must perform the following steps first:</span></span>  
  
    1.  <span data-ttu-id="09997-123">停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller 服務。</span><span class="sxs-lookup"><span data-stu-id="09997-123">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay controller service.</span></span>  
  
    2.  <span data-ttu-id="09997-124">在安裝控制器服務的控制器電腦上，於命令提示字元中輸入 `dcomcnfg`。</span><span class="sxs-lookup"><span data-stu-id="09997-124">On the controller computer on which the controller service is installed, from the command prompt, type `dcomcnfg`.</span></span>  
  
    3.  <span data-ttu-id="09997-125">在 [元件服務]  視窗中，巡覽至主控台根目錄 -> [元件服務] -> [電腦] -> [我的電腦] -> [DCOM 設定] -> [DReplayController]  。</span><span class="sxs-lookup"><span data-stu-id="09997-125">In the **Component Services** window, navigate to **Console Root -> Component Services -> Computers -> My Computer -> DCOM Config ->DReplayController**.</span></span>  
  
    4.  <span data-ttu-id="09997-126">以滑鼠右鍵按一下 [DReplayController]  ，然後按一下 [內容]  。</span><span class="sxs-lookup"><span data-stu-id="09997-126">Right-click **DReplayController**, and then click **Properties**.</span></span>  
  
    5.  <span data-ttu-id="09997-127">在 [DReplayController 內容]  視窗的 [安全性]  索引標籤上，按一下 [啟動和啟用權限]  區段中的 [編輯]  。</span><span class="sxs-lookup"><span data-stu-id="09997-127">In the **DReplayController Properties** window, on the **Security** tab, click **Edit** in the **Launch and Activation Permissions** section.</span></span>  
  
    6.  <span data-ttu-id="09997-128">將**本機和遠端啟用**權限授與新的用戶端服務登入帳戶，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="09997-128">Grant the new client service logon account **Local and Remote activation** permissions, and then click **OK**.</span></span>  
  
    7.  <span data-ttu-id="09997-129">按一下 [存取權限]  區段中的 [編輯]  ，將**本機和遠端存取**權限授與新的用戶端服務登入帳戶，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="09997-129">Click **Edit** in the **Access Permissions** section, and grant the new client service logon account **Local and Remote access** permissions, and then click **OK**.</span></span>  
  
    8.  <span data-ttu-id="09997-130">按一下 [確定]  關閉 [DReplayController 內容]  視窗。</span><span class="sxs-lookup"><span data-stu-id="09997-130">Click **OK** to close the **DReplayController Properties** window.</span></span>  
  
    9. <span data-ttu-id="09997-131">在控制器電腦上，將已變更的用戶端服務登入帳戶加入 [Distributed COM Users]  群組。</span><span class="sxs-lookup"><span data-stu-id="09997-131">On the controller computer, add the changed client service logon account to the **Distributed COM Users** group.</span></span>  
  
    10. <span data-ttu-id="09997-132">啟動 SQL Server Distributed Replay Controller 服務。</span><span class="sxs-lookup"><span data-stu-id="09997-132">Start the SQL Server Distributed Replay controller service.</span></span>  
  
2.  <span data-ttu-id="09997-133">停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client 服務。</span><span class="sxs-lookup"><span data-stu-id="09997-133">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay client service.</span></span>  
  
3.  <span data-ttu-id="09997-134">在 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client 內容]  視窗的 [登入]  索引標籤上選取 [這個帳戶]  ，輸入或按一下 [瀏覽]  輸入新的登入帳戶，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="09997-134">In the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client Properties** window, on the **Log On** tab, select **This account**, type or click **Browse** to enter the new logon account, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="09997-135">啟動 Distributed Replay Client 服務。</span><span class="sxs-lookup"><span data-stu-id="09997-135">Start the Distributed Replay client service.</span></span>  
  
  
