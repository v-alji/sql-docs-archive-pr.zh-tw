---
title: 將 SQL Server 的實例設定為自動啟動 (SQL Server 組態管理員) |Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, automatic startup
- starting SQL Server, automatically
ms.assetid: aa2b6bde-e76d-4fea-a560-54a63745d9b1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2fc21bd881c1588da47710c6d8437e31d3df2ab4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706745"
---
# <a name="set-an-instance-of-sql-server-to-start-automatically-sql-server-configuration-manager"></a><span data-ttu-id="02ac9-102">將 SQL Server 執行個體設定為自動啟動 (SQL Server 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="02ac9-102">Set an Instance of SQL Server to Start Automatically (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="02ac9-103">此主題描述如何使用 SQL Server 組態管理員，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中設定 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 執行個體自動啟動。</span><span class="sxs-lookup"><span data-stu-id="02ac9-103">This topic describes how to set an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to start automatically in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="02ac9-104">在安裝期間， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通常會設定為自動啟動。</span><span class="sxs-lookup"><span data-stu-id="02ac9-104">During setup, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is normally configured to start automatically.</span></span> <span data-ttu-id="02ac9-105">如果沒有這樣執行，您隨時都可以變更該設定。</span><span class="sxs-lookup"><span data-stu-id="02ac9-105">If this was not done, you can change that setting at any time.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="02ac9-106">使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="02ac9-106">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-set-an-instance-of-sql-server-to-start-automatically"></a><span data-ttu-id="02ac9-107">將 SQL Server 執行個體設定為自動啟動</span><span class="sxs-lookup"><span data-stu-id="02ac9-107">To set an instance of SQL Server to start automatically</span></span>  
  
1.  <span data-ttu-id="02ac9-108">指向 **[開始]** 功能表上的 **[所有程式]** ，然後依序指向 [ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]] 和 **[組態工具]** ，再按一下 **[SQL Server 組態管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="02ac9-108">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="02ac9-109">因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理主控台程式的嵌入式管理單元，而不是獨立的程式，所以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員在較新版本的 Windows 中不會作為應用程式出現。</span><span class="sxs-lookup"><span data-stu-id="02ac9-109">Because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager is a snap-in for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console program and not a stand-alone program, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager does not appear as an application in newer versions of Windows.</span></span>  
    >   
    >  -   <span data-ttu-id="02ac9-110">**Windows 10**：</span><span class="sxs-lookup"><span data-stu-id="02ac9-110">**Windows 10**:</span></span>  
    >          <span data-ttu-id="02ac9-111">若要開啟 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager，請在 [**開始] 頁面**上，輸入適用于) 的 sqlservermanager12.msc (。 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02ac9-111">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager12.msc (for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]).</span></span> <span data-ttu-id="02ac9-112">針對先前版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，以較小的數字取代 12。</span><span class="sxs-lookup"><span data-stu-id="02ac9-112">For previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replace 12 with a smaller number.</span></span> <span data-ttu-id="02ac9-113">按一下 SQLServerManager12.msc 即可開啟 Configuration Manager。</span><span class="sxs-lookup"><span data-stu-id="02ac9-113">Clicking SQLServerManager12.msc opens the Configuration Manager.</span></span> <span data-ttu-id="02ac9-114">若要將 Configuration Manager 釘選到起始頁或工作列，請在 [Sqlservermanager12.msc] 上按一下滑鼠右鍵，然後按一下 [**開啟檔案位置**]。</span><span class="sxs-lookup"><span data-stu-id="02ac9-114">To pin the Configuration Manager to the Start Page or Task Bar, right-click SQLServerManager12.msc, and then click **Open file location**.</span></span> <span data-ttu-id="02ac9-115">在 Windows 檔案瀏覽器中，以滑鼠右鍵按一下 [Sqlservermanager12.msc]，然後按一下 [**釘選到開始**] 或 [**釘選到工作列**]。</span><span class="sxs-lookup"><span data-stu-id="02ac9-115">In the Windows File Explorer, right-click SQLServerManager12.msc, and then click **Pin to Start** or **Pin to taskbar**.</span></span>  
    > -   <span data-ttu-id="02ac9-116">**Windows 8**：</span><span class="sxs-lookup"><span data-stu-id="02ac9-116">**Windows 8**:</span></span>  
    >          <span data-ttu-id="02ac9-117">若要開啟 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager，請在 [**搜尋**] 快速鍵的 [**應用程式**] 底下，輸入**SQLServerManager \<version> \*\* （例如 `SQLServerManager12.msc` ），然後按**enter\*\*。</span><span class="sxs-lookup"><span data-stu-id="02ac9-117">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager\<version>.msc** such as `SQLServerManager12.msc`, and then press **Enter**.</span></span>  
  
2.  <span data-ttu-id="02ac9-118">在 **[SQL Server 組態管理員]** 中展開 **[服務]** ，然後按一下 **[SQL Server]** 。</span><span class="sxs-lookup"><span data-stu-id="02ac9-118">In **SQL Server Configuration Manager**, expand **Services**, and then click **SQL Server**.</span></span>  
  
3.  <span data-ttu-id="02ac9-119">在詳細資料窗格中，以滑鼠右鍵按一下您想要自動啟動的執行個體名稱，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="02ac9-119">In the details pane, right-click the name of the instance you want to start automatically, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="02ac9-120">在 [SQL Server \<***instancename***> 屬性] 對話方塊中，將 [啟動模式] 設定為 [自動]。</span><span class="sxs-lookup"><span data-stu-id="02ac9-120">In the **SQL Server \<***instancename***> Properties** dialog box, set **Start Mode** to **Automatic**.</span></span>  
  
5.  <span data-ttu-id="02ac9-121">按一下 **[確定]** ，然後關閉 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員。</span><span class="sxs-lookup"><span data-stu-id="02ac9-121">Click **OK**, and then close [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ac9-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02ac9-122">See Also</span></span>  
 <span data-ttu-id="02ac9-123">[避免自動啟動 SQL Server 的執行個體 &#40;SQL Server 組態管理員&#41;](scm-services-prevent-automatic-startup-of-an-instance.md) </span><span class="sxs-lookup"><span data-stu-id="02ac9-123">[Prevent Automatic Startup of an Instance of SQL Server &#40;SQL Server Configuration Manager&#41;](scm-services-prevent-automatic-startup-of-an-instance.md) </span></span>  
 <span data-ttu-id="02ac9-124">[連接至另一部電腦 &#40;SQL Server 組態管理員&#41;](scm-services-connect-to-another-computer.md) </span><span class="sxs-lookup"><span data-stu-id="02ac9-124">[Connect to Another Computer &#40;SQL Server Configuration Manager&#41;](scm-services-connect-to-another-computer.md) </span></span>  
 [<span data-ttu-id="02ac9-125">設定 WMI 在 SQL Server 工具中顯示伺服器狀態</span><span class="sxs-lookup"><span data-stu-id="02ac9-125">Configure WMI to Show Server Status in SQL Server Tools</span></span>](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
