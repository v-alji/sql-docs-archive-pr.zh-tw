---
title: 檢查使用中的檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ccd65867-d4c0-43b2-8361-7fd41c6f79ac
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 51505b0dece146b7f6fcdf982e6f88a5715357e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595514"
---
# <a name="check-files-in-use"></a><span data-ttu-id="275a4-102">檢查使用中的檔案</span><span class="sxs-lookup"><span data-stu-id="275a4-102">Check Files In Use</span></span>
  <span data-ttu-id="275a4-103">若要避免在安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新之後重新啟動 Windows，請使用 [檢查使用中檔案] 頁面來識別正在鎖定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新安裝程式所需之檔案的處理序。</span><span class="sxs-lookup"><span data-stu-id="275a4-103">To avoid restarting Windows after you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] updates, use the Check Files in Use page to identify processes that are locking files required by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] update Setup program.</span></span>  
  
 <span data-ttu-id="275a4-104">停止所有連接到正在更新之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的應用程式和服務。</span><span class="sxs-lookup"><span data-stu-id="275a4-104">Stop all applications and services that make connections to the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are being updated.</span></span> <span data-ttu-id="275a4-105">其中包括停止 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="275a4-105">This includes stopping [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="275a4-106">如果安裝程式判斷在安裝時鎖定了檔案，則在安裝完成之後可能必須重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="275a4-106">If Setup determines that files are locked during installation, you might have to restart your computer after installation is completed.</span></span> <span data-ttu-id="275a4-107">如有必要，安裝程式會提示您重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="275a4-107">If necessary, Setup prompts you to restart your computer.</span></span> <span data-ttu-id="275a4-108">如果安裝程式必須在安裝時結束某項服務，它會在安裝完成之後重新啟動該服務。</span><span class="sxs-lookup"><span data-stu-id="275a4-108">If the Setup program must stop a service during installation, it will restart the service after installation is completed.</span></span>  
  
 <span data-ttu-id="275a4-109">為了排除安裝之後重新啟動電腦的需求，安裝程式會顯示正在鎖定檔案之處理序的清單。</span><span class="sxs-lookup"><span data-stu-id="275a4-109">To eliminate the requirement to restart your computer after installation, Setup displays a list of processes that are locking files.</span></span> <span data-ttu-id="275a4-110">請停止或結束此清單中的處理序和應用程式，</span><span class="sxs-lookup"><span data-stu-id="275a4-110">Stop or end the processes and applications in the list.</span></span> <span data-ttu-id="275a4-111">然後按一下 **[重新整理檢查]** 重新執行檢查。</span><span class="sxs-lookup"><span data-stu-id="275a4-111">Then click **Refresh check** to rerun the check.</span></span> <span data-ttu-id="275a4-112">按一下 **[停止檢查]** 可結束正在執行的檢查作業。</span><span class="sxs-lookup"><span data-stu-id="275a4-112">Click **Stop check** to end a check that is running.</span></span> <span data-ttu-id="275a4-113">如果找不到鎖定的檔案，表格會是空的。</span><span class="sxs-lookup"><span data-stu-id="275a4-113">If locked files are not found, the table is empty.</span></span> <span data-ttu-id="275a4-114">當所有鎖定的處理序都已關閉或停止時，請按 **[下一步]** 繼續。</span><span class="sxs-lookup"><span data-stu-id="275a4-114">When all locked processes have been closed or stopped, click **Next** to continue.</span></span>  
  
 <span data-ttu-id="275a4-115">安裝程式會將資訊記錄到記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="275a4-115">Setup logs the information in the log files.</span></span> <span data-ttu-id="275a4-116">如需有關如何檢視記錄檔的詳細資訊，請參閱 [檢視與讀取 SQL Server 安裝程式記錄檔](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md) 和 [如何：讀取 SQL Server 安裝程式記錄檔](https://go.microsoft.com/fwlink/?LinkID=134490)。</span><span class="sxs-lookup"><span data-stu-id="275a4-116">For more information about how to view the log files, see [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md) and [How to: Read a SQL Server Setup Log File](https://go.microsoft.com/fwlink/?LinkID=134490).</span></span>  
  
 <span data-ttu-id="275a4-117">記錄檔中將包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="275a4-117">The following information is included in the log file:</span></span>  
  
-   <span data-ttu-id="275a4-118">處理序的名稱</span><span class="sxs-lookup"><span data-stu-id="275a4-118">Name of the process</span></span>  
  
-   <span data-ttu-id="275a4-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能的名稱</span><span class="sxs-lookup"><span data-stu-id="275a4-119">Name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] feature</span></span>  
  
-   <span data-ttu-id="275a4-120">處理序類型</span><span class="sxs-lookup"><span data-stu-id="275a4-120">Process type</span></span>  
  
-   <span data-ttu-id="275a4-121">執行處理序所使用的帳戶</span><span class="sxs-lookup"><span data-stu-id="275a4-121">Account under which the process is running</span></span>  
  
-   <span data-ttu-id="275a4-122">處理序識別碼</span><span class="sxs-lookup"><span data-stu-id="275a4-122">Process ID</span></span>  
  
-   <span data-ttu-id="275a4-123">鎖定的檔案名稱</span><span class="sxs-lookup"><span data-stu-id="275a4-123">Name of the file that is locked</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="275a4-124">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="275a4-124">UI element list</span></span>  
  
|<span data-ttu-id="275a4-125">名稱</span><span class="sxs-lookup"><span data-stu-id="275a4-125">Name</span></span>|<span data-ttu-id="275a4-126">描述</span><span class="sxs-lookup"><span data-stu-id="275a4-126">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="275a4-127">Process</span><span class="sxs-lookup"><span data-stu-id="275a4-127">Process</span></span>|<span data-ttu-id="275a4-128">顯示正在使用要更新之檔案的處理序完整名稱。</span><span class="sxs-lookup"><span data-stu-id="275a4-128">Displays the full name of the process that is using the files to be updated.</span></span>|  
|<span data-ttu-id="275a4-129">類型</span><span class="sxs-lookup"><span data-stu-id="275a4-129">Type</span></span>|<span data-ttu-id="275a4-130">顯示處理序的類型。</span><span class="sxs-lookup"><span data-stu-id="275a4-130">Displays the type of process.</span></span>|  
|<span data-ttu-id="275a4-131">帳戶</span><span class="sxs-lookup"><span data-stu-id="275a4-131">Account</span></span>|<span data-ttu-id="275a4-132">顯示執行處理序所使用的帳戶。</span><span class="sxs-lookup"><span data-stu-id="275a4-132">Displays the account under which the process is running.</span></span>|  
|<span data-ttu-id="275a4-133">處理序識別碼</span><span class="sxs-lookup"><span data-stu-id="275a4-133">Process ID</span></span>|<span data-ttu-id="275a4-134">顯示處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="275a4-134">Displays the process ID.</span></span>|  
  
  
