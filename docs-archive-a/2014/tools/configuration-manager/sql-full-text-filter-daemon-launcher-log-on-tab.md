---
title: SQL 全文檢索篩選精靈啟動器 ([登入] 索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 13e260f9-a75f-430b-88a3-959ddcead8fe
author: stevestein
ms.author: sstein
ms.openlocfilehash: cb3f23907e96214929617bf2923e46148c0ab1f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605966"
---
# <a name="sql-full-text-filter-daemon-launcher-log-on-tab"></a><span data-ttu-id="df9d3-102">SQL 全文檢索篩選背景程式啟動器 (登入索引標籤)</span><span class="sxs-lookup"><span data-stu-id="df9d3-102">SQL Full-text Filter Daemon Launcher (Log On Tab)</span></span>
  <span data-ttu-id="df9d3-103">從 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]開始， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文檢索搜尋就會使用 SQL 全文檢索篩選背景程式啟動器 (FDHOST 啟動器) 服務。</span><span class="sxs-lookup"><span data-stu-id="df9d3-103">Beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the SQL Full-text Filter Daemon Launcher (FDHOST Launcher) service is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text search.</span></span> <span data-ttu-id="df9d3-104">如果您使用全文檢索搜尋，這個服務就必須執行。</span><span class="sxs-lookup"><span data-stu-id="df9d3-104">This service must be running if you use full-text search.</span></span> <span data-ttu-id="df9d3-105">如需有關篩選背景程式主機處理序的詳細資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜全文檢索搜尋架構＞。</span><span class="sxs-lookup"><span data-stu-id="df9d3-105">For information about the filter daemon host processes, see "Full-Text Search Architecture" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="df9d3-106">您可以使用 **[SQL 全文檢索篩選背景程式啟動器屬性]** 對話方塊的 **[登入]** 索引標籤來指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文檢索服務所使用的帳戶、變更帳戶的密碼，以及啟動和停止服務。</span><span class="sxs-lookup"><span data-stu-id="df9d3-106">Use the **Log On** tab of the **SQL Full-text Filter Daemon Launcher  Properties** dialog box to specify the account used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text service, to change the password of an account, and to start and stop the service.</span></span> <span data-ttu-id="df9d3-107">帳戶密碼的變更會在重新啟動服務之後生效。</span><span class="sxs-lookup"><span data-stu-id="df9d3-107">Changing the password of an account takes affect after restarting the service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df9d3-108">在叢集執行個體上變更服務所使用的帳戶名稱時，新帳戶必須是服務安裝期間所指定之網域群組的成員，或者您必須擁有在該群組中加入成員的權限。</span><span class="sxs-lookup"><span data-stu-id="df9d3-108">When changing the account name used by a service on a clustered instance, either the new account must be a member of the domain group specified during setup for the service, or you must have permission to add members to that group.</span></span> <span data-ttu-id="df9d3-109">如果您沒有修改群組成員資格的權限，請與網域管理員連絡。</span><span class="sxs-lookup"><span data-stu-id="df9d3-109">If you do not have permission to modify group membership, contact the domain administrator.</span></span>  
>   
>  <span data-ttu-id="df9d3-110">如需有關選取帳戶以執行服務的詳細資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜設定 Windows 服務帳戶＞。</span><span class="sxs-lookup"><span data-stu-id="df9d3-110">For more information about selecting an account to run the service, see "Setting Up Windows Service Accounts" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="df9d3-111">選項。</span><span class="sxs-lookup"><span data-stu-id="df9d3-111">Options</span></span>  
 <span data-ttu-id="df9d3-112">**內建帳戶**</span><span class="sxs-lookup"><span data-stu-id="df9d3-112">**Built-in account**</span></span>  
 <span data-ttu-id="df9d3-113">**本機系統**</span><span class="sxs-lookup"><span data-stu-id="df9d3-113">**Local System**</span></span>  
 <span data-ttu-id="df9d3-114">指定本機系統帳戶。</span><span class="sxs-lookup"><span data-stu-id="df9d3-114">Specify the local system account.</span></span> <span data-ttu-id="df9d3-115">這個帳戶不需要密碼。</span><span class="sxs-lookup"><span data-stu-id="df9d3-115">This account does not require a password.</span></span> <span data-ttu-id="df9d3-116">但是，根據授與帳戶的權限，本機系統帳戶可能會禁止服務與其他伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="df9d3-116">However, the local system account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="df9d3-117">**本機服務**</span><span class="sxs-lookup"><span data-stu-id="df9d3-117">**Local Service**</span></span>  
 <span data-ttu-id="df9d3-118">指定本機服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="df9d3-118">Specify the local service account.</span></span> <span data-ttu-id="df9d3-119">這個帳戶不需要密碼。</span><span class="sxs-lookup"><span data-stu-id="df9d3-119">This account does not require a password.</span></span> <span data-ttu-id="df9d3-120">但是，根據授與帳戶的權限，本機服務帳戶可能會禁止服務與其他伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="df9d3-120">However, the local service account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="df9d3-121">**網路服務**</span><span class="sxs-lookup"><span data-stu-id="df9d3-121">**Network Service**</span></span>  
 <span data-ttu-id="df9d3-122">我們建議您不要針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務，使用網路服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="df9d3-122">We recommend that you do not use the Network Service account for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent services.</span></span> <span data-ttu-id="df9d3-123">本機使用者或網域使用者帳戶更適合這些服務。</span><span class="sxs-lookup"><span data-stu-id="df9d3-123">Local User or Domain User accounts are more appropriate for these services.</span></span>  
  
 <span data-ttu-id="df9d3-124">**這個帳戶**</span><span class="sxs-lookup"><span data-stu-id="df9d3-124">**This account**</span></span>  
 <span data-ttu-id="df9d3-125">指定使用 Windows 驗證的本機或網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="df9d3-125">Specify a local or domain user account that uses Windows Authentication.</span></span> <span data-ttu-id="df9d3-126">建議您使用具有最少服務權限的網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="df9d3-126">We recommend that you use a domain user account that has minimal rights for services.</span></span>  
  
 <span data-ttu-id="df9d3-127">**帳戶名稱**</span><span class="sxs-lookup"><span data-stu-id="df9d3-127">**Account Name**</span></span>  
 <span data-ttu-id="df9d3-128">指定本機或網域使用者帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="df9d3-128">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="df9d3-129">**密碼**</span><span class="sxs-lookup"><span data-stu-id="df9d3-129">**Password**</span></span>  
 <span data-ttu-id="df9d3-130">輸入帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="df9d3-130">Type the password of the account.</span></span>  
  
 <span data-ttu-id="df9d3-131">**確認密碼**</span><span class="sxs-lookup"><span data-stu-id="df9d3-131">**Confirm password**</span></span>  
 <span data-ttu-id="df9d3-132">再次輸入帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="df9d3-132">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="df9d3-133">**啟動**</span><span class="sxs-lookup"><span data-stu-id="df9d3-133">**Start**</span></span>  
 <span data-ttu-id="df9d3-134">啟動服務。</span><span class="sxs-lookup"><span data-stu-id="df9d3-134">Start the service.</span></span>  
  
 <span data-ttu-id="df9d3-135">**停止**</span><span class="sxs-lookup"><span data-stu-id="df9d3-135">**Stop**</span></span>  
 <span data-ttu-id="df9d3-136">停止服務。</span><span class="sxs-lookup"><span data-stu-id="df9d3-136">Stop the service.</span></span>  
  
 <span data-ttu-id="df9d3-137">**暫停**</span><span class="sxs-lookup"><span data-stu-id="df9d3-137">**Pause**</span></span>  
 <span data-ttu-id="df9d3-138">暫停服務。</span><span class="sxs-lookup"><span data-stu-id="df9d3-138">Pause the service.</span></span> <span data-ttu-id="df9d3-139">不適用於這項服務。</span><span class="sxs-lookup"><span data-stu-id="df9d3-139">Not available for this service.</span></span>  
  
 <span data-ttu-id="df9d3-140">**繼續**</span><span class="sxs-lookup"><span data-stu-id="df9d3-140">**Resume**</span></span>  
 <span data-ttu-id="df9d3-141">繼續已暫停的服務。</span><span class="sxs-lookup"><span data-stu-id="df9d3-141">Resume a paused service.</span></span>  
  
  
