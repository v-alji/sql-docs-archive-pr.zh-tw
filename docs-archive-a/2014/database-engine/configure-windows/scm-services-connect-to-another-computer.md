---
title: 連接至另一部電腦 (SQL Server 組態管理員) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], other computers
ms.assetid: c4c1e94f-4f5f-431e-8b5b-d5ff97baf723
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f3d478cebc1ca36ccb8f87b0355b7c8fe0a928cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607090"
---
# <a name="connect-to-another-computer-sql-server-configuration-manager"></a><span data-ttu-id="ca0fb-102">連接至另一部電腦 (SQL Server 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="ca0fb-102">Connect to Another Computer (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="ca0fb-103">此主題描述如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中連接到另一部電腦。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-103">This topic describes how to connect to another computer in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="ca0fb-104">請遵循第一個程序，開啟 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console (mmc) 中的 Windows [電腦管理]，並連接到該電腦，然後展開 [服務與應用程式] 樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-104">Follow the first procedure to open the Windows Computer Management [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console (mmc), connect to the computer, and expand the Services and Applications tree.</span></span> <span data-ttu-id="ca0fb-105">請遵循第二個程序，在遠端電腦上建立連結至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員的檔案。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-105">Follow the second procedure to create a file with a link to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager on a remote computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ca0fb-106">從遠端連線時，有些動作 Configuration Manager 無法執行。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-106">Some actions cannot be performed by Configuration Manager when connecting remotely.</span></span>  
  
 <span data-ttu-id="ca0fb-107">若要啟動、停止、暫停或繼續另一台電腦上的服務，您也可使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]連接到伺服器，並以滑鼠右鍵按一下伺服器或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent，然後按一下所要的動作。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-107">To start, stop, pause, or resume services on another computer, you can also connect to the server with [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click the server or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent and then click the desired action.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-connect-to-another-computer-with-windows-computer-management"></a><span data-ttu-id="ca0fb-108">若要以 Windows 電腦管理連接到另一部電腦</span><span class="sxs-lookup"><span data-stu-id="ca0fb-108">To connect to another computer with Windows Computer Management</span></span>  
  
1.  <span data-ttu-id="ca0fb-109">在 [開始]\*\*\*\* 功能表中，以滑鼠右鍵按一下 [我的電腦]\*\*\*\*，然後按一下 [管理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-109">On the **Start** menu, right-click **My Computer**, and then click **Manage.**</span></span>  
  
2.  <span data-ttu-id="ca0fb-110">在 [電腦管理]\*\*\*\* 中，以滑鼠右鍵按一下 [電腦管理 (本機)]\*\*\*\*，然後按一下 [連線到另一台電腦]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-110">In **Computer Management**, right-click **Computer Management (Local)**, and then click **Connect to another computer**.</span></span>  
  
3.  <span data-ttu-id="ca0fb-111">在 [選取電腦] 對話方塊的 [另一台電腦] 文字方塊中，輸入要管理的電腦名稱，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-111">In the **Select Computer** dialog box, in the **Another computer** text box, type the name of the computer you want to manage, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ca0fb-112">[電腦管理] 會顯示出遠端電腦上執行的服務。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-112">Computer Management displays the services running on the remote computer.</span></span> <span data-ttu-id="ca0fb-113">最上層節點會變更為 [電腦管理 \<*remotecomputer*>]。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-113">The top-level node changes to **Computer Management** \<*remotecomputer*>.</span></span>  
  
4.  <span data-ttu-id="ca0fb-114">在主控台樹狀目錄中，展開 [服務與應用程式]，然後展開 [SQL Server 組態管理員]，來管理遠端電腦的服務。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-114">In the console tree, expand **Services and Applications**, and then expand **SQL Server Configuration Manager** to manage the remote computer's services.</span></span>  
  
#### <a name="to-save-a-link-to-sql-server-configuration-manager-for-another-computer"></a><span data-ttu-id="ca0fb-115">若要儲存另一台電腦的 SQL Server 組態管理員連結</span><span class="sxs-lookup"><span data-stu-id="ca0fb-115">To save a link to SQL Server Configuration Manager for another computer</span></span>  
  
1.  <span data-ttu-id="ca0fb-116">在 **[開始]** 功能表上，按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-116">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="ca0fb-117">在 [**開啟**] 方塊中，輸入 `mmc -a` 以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 在作者模式中開啟管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-117">In the **Open** box, type `mmc -a` to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console in author mode.</span></span>  
  
3.  <span data-ttu-id="ca0fb-118">在 [檔案] 功能表上，按一下 [新增/移除嵌入式管理單元]。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-118">On the **File** menu, click **Add/Remove Snap-in**.</span></span>  
  
4.  <span data-ttu-id="ca0fb-119">在 [新增/移除嵌入式管理單元] 視窗中，按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-119">In the **Add/Remove Snap-in** window, click **Add**.</span></span>  
  
5.  <span data-ttu-id="ca0fb-120">在 [新增獨立嵌入式管理單元] 視窗中，依序按一下 [電腦管理] 和 [新增]。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-120">In the **Add Standalone Snap-in** window, click **Computer Management** and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="ca0fb-121">在 [電腦管理] 視窗中，按一下 [另一台電腦]，並輸入想要管理之遠端電腦的名稱，然後按一下 [完成]。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-121">In the **Computer Management** window, click **Another computer**, type the name of the remote computer you wish to manage, and then click **Finish**.</span></span>  
  
7.  <span data-ttu-id="ca0fb-122">在 [新增獨立嵌入式管理單元] 視窗中，按一下 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-122">In the **Add Standalone Snap-in** window, click **Close**.</span></span>  
  
8.  <span data-ttu-id="ca0fb-123">在 [新增/移除嵌入式管理單元] 視窗中，按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-123">In the **Add/Remove Snap-in** window, click **OK**.</span></span>  
  
9. <span data-ttu-id="ca0fb-124">展開 [**電腦管理] (***\<computer name>***) **，以及 [**服務和應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-124">Expand **Computer Management (***\<computer name>***)**, and **Services and Applications**.</span></span>  
  
10. <span data-ttu-id="ca0fb-125">以滑鼠右鍵按一下 [SQL Server 組態管理員]，然後按一下 [從這裡新增視窗]。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-125">Right-click **SQL Server Configuration Manager**, and then click **New Window from here**.</span></span>  
  
11. <span data-ttu-id="ca0fb-126">在 [視窗] 功能表上，按一下 [主控台根目錄]，以切換回第一個視窗，並刪除該視窗。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-126">On the **Window** menu, click **Console Root**, to switch back to the first window, and delete the window.</span></span>  
  
12. <span data-ttu-id="ca0fb-127">在 [檔案 **] 功能表上，按一下 [** **另存**新檔]，然後將檔案儲存在所需的資料夾中，副檔名為的適當名稱 `.msc` 。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-127">On the **File** menu, click **Save As**, and save the file in the desired folder, with an appropriate name with the `.msc` file extension.</span></span> <span data-ttu-id="ca0fb-128">請關閉 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-128">Close the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console.</span></span>  
  
13. <span data-ttu-id="ca0fb-129">若要在目標電腦上開啟 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員，請按兩下該檔案。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-129">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager on the target computer, double-click the file.</span></span> <span data-ttu-id="ca0fb-130">如果想要，也請將檔案的連結儲存在桌面或 [開始] 功能表中。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-130">If desired, save a link to the file on the desktop or in the **Start** menu.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="ca0fb-131">在遠端電腦上使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員時，電腦名稱並不明顯，且可能會錯誤地停止或設定錯誤的電腦。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-131">When using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager on a remote computer, the computer name is not obvious and it is possible to mistakenly stop or configure the wrong computer.</span></span> <span data-ttu-id="ca0fb-132">在 [服務] 索引標籤上，核取 [主機名稱] 方塊，以便在修改服務之前確認電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="ca0fb-132">On the **Service** tab, check the **Host Name** box to confirm the computer name before modifying a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca0fb-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca0fb-133">See Also</span></span>  
 [<span data-ttu-id="ca0fb-134">設定 WMI 在 SQL Server 工具中顯示伺服器狀態</span><span class="sxs-lookup"><span data-stu-id="ca0fb-134">Configure WMI to Show Server Status in SQL Server Tools</span></span>](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
