---
title: SQL Server 屬性 (登入索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 405073fc-eaa3-43c6-bf82-2cd58cacc1c3
author: stevestein
ms.author: sstein
ms.openlocfilehash: adec9ed7c69023218baa96ab8f8edbb6f2b365bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596411"
---
# <a name="sql-server-properties-log-on-tab"></a><span data-ttu-id="07249-102">SQL Server 屬性 (登入索引標籤)</span><span class="sxs-lookup"><span data-stu-id="07249-102">SQL Server Properties (Log On Tab)</span></span>
  <span data-ttu-id="07249-103">您可以使用 **[SQL Server 屬性]** 對話方塊的 **[登入]** 索引標籤，來指定要供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務使用的帳戶、變更帳戶的密碼，以及啟動和停止該服務。</span><span class="sxs-lookup"><span data-stu-id="07249-103">Use the **Log On** tab of the **SQL Server Properties** dialog box to specify the account used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service, to change the password of an account, and to start and stop the service.</span></span> <span data-ttu-id="07249-104">帳戶密碼的變更會立即生效。</span><span class="sxs-lookup"><span data-stu-id="07249-104">Changing the password of an account takes effect immediately.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07249-105">在叢集執行個體上變更服務所使用的帳戶名稱時，新帳戶必須是所要變更之服務安裝期間所指定網域群組的成員，或者您必須擁有在該群組中加入成員的權限。</span><span class="sxs-lookup"><span data-stu-id="07249-105">When changing the account name used by a service on a clustered instance, the new account must be a member of the domain group specified during setup for the service being changed, or you must have permission to add members to that group.</span></span> <span data-ttu-id="07249-106">如果您沒有修改群組成員資格的權限，請與網域管理員連絡。</span><span class="sxs-lookup"><span data-stu-id="07249-106">If you do not have permission to modify group membership, contact the domain administrator.</span></span>  
>   
>  <span data-ttu-id="07249-107">如需有關選取帳戶以執行服務的詳細資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜設定 Windows 服務帳戶＞。</span><span class="sxs-lookup"><span data-stu-id="07249-107">For more information about selecting an account to run the service, see "Setting Up Windows Service Accounts" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="07249-108">選項。</span><span class="sxs-lookup"><span data-stu-id="07249-108">Options</span></span>  
 <span data-ttu-id="07249-109">**內建帳戶**</span><span class="sxs-lookup"><span data-stu-id="07249-109">**Built-in account**</span></span>  
 <span data-ttu-id="07249-110">**本機系統**</span><span class="sxs-lookup"><span data-stu-id="07249-110">**Local System**</span></span>  
 -   <span data-ttu-id="07249-111">指定本機系統帳戶。</span><span class="sxs-lookup"><span data-stu-id="07249-111">Specify the local system account.</span></span> <span data-ttu-id="07249-112">這個帳戶不需要密碼。</span><span class="sxs-lookup"><span data-stu-id="07249-112">This account does not require a password.</span></span> <span data-ttu-id="07249-113">但是，根據授與帳戶的權限，本機系統帳戶可能會禁止服務與其他伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="07249-113">However, the local system account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="07249-114">**本機服務**</span><span class="sxs-lookup"><span data-stu-id="07249-114">**Local Service**</span></span>  
 -   <span data-ttu-id="07249-115">指定本機服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="07249-115">Specify the local service account.</span></span> <span data-ttu-id="07249-116">這個帳戶不需要密碼。</span><span class="sxs-lookup"><span data-stu-id="07249-116">This account does not require a password.</span></span> <span data-ttu-id="07249-117">但是，根據授與帳戶的權限，本機服務帳戶可能會禁止服務與其他伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="07249-117">However, the local service account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="07249-118">**網路服務**</span><span class="sxs-lookup"><span data-stu-id="07249-118">**Network Service**</span></span>  
 -   <span data-ttu-id="07249-119">我們建議您不要在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務上，使用網路服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="07249-119">We recommend that you do not use the Network Service account for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent services.</span></span> <span data-ttu-id="07249-120">本機使用者或網域使用者帳戶更適合這些服務。</span><span class="sxs-lookup"><span data-stu-id="07249-120">Local User or Domain User accounts are more appropriate for these services.</span></span>  
  
 <span data-ttu-id="07249-121">**這個帳戶**</span><span class="sxs-lookup"><span data-stu-id="07249-121">**This account**</span></span>  
 <span data-ttu-id="07249-122">指定使用 Windows 驗證的本機或網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="07249-122">Specify a local or domain user account that uses Windows Authentication.</span></span> <span data-ttu-id="07249-123">建議您使用具有最少服務權限的網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="07249-123">We recommend that you use a domain user account that has minimal rights for services.</span></span>  
  
 <span data-ttu-id="07249-124">**帳戶名稱**</span><span class="sxs-lookup"><span data-stu-id="07249-124">**Account Name**</span></span>  
 <span data-ttu-id="07249-125">指定本機或網域使用者帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="07249-125">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="07249-126">**密碼**</span><span class="sxs-lookup"><span data-stu-id="07249-126">**Password**</span></span>  
 <span data-ttu-id="07249-127">輸入帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="07249-127">Type the password of the account.</span></span>  
  
 <span data-ttu-id="07249-128">**確認密碼**</span><span class="sxs-lookup"><span data-stu-id="07249-128">**Confirm password**</span></span>  
 <span data-ttu-id="07249-129">再次輸入帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="07249-129">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="07249-130">**啟動**</span><span class="sxs-lookup"><span data-stu-id="07249-130">**Start**</span></span>  
 <span data-ttu-id="07249-131">啟動服務。</span><span class="sxs-lookup"><span data-stu-id="07249-131">Start the service.</span></span>  
  
 <span data-ttu-id="07249-132">**停止**</span><span class="sxs-lookup"><span data-stu-id="07249-132">**Stop**</span></span>  
 <span data-ttu-id="07249-133">停止服務。</span><span class="sxs-lookup"><span data-stu-id="07249-133">Stop the service.</span></span>  
  
 <span data-ttu-id="07249-134">**暫停**</span><span class="sxs-lookup"><span data-stu-id="07249-134">**Pause**</span></span>  
 <span data-ttu-id="07249-135">暫停服務。</span><span class="sxs-lookup"><span data-stu-id="07249-135">Pause the service.</span></span>  
  
 <span data-ttu-id="07249-136">**繼續**</span><span class="sxs-lookup"><span data-stu-id="07249-136">**Resume**</span></span>  
 <span data-ttu-id="07249-137">繼續已暫停的服務。</span><span class="sxs-lookup"><span data-stu-id="07249-137">Resume a paused service.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="07249-138">根據預設，只有本機 Administrators 群組的成員能夠啟動、停止、暫停、繼續或重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="07249-138">By default, only members of the local administrators group can start, stop, pause, resume or restart a service.</span></span> <span data-ttu-id="07249-139">若要將管理服務的能力授與非系統管理員，請參閱 [How to grant users rights to manage services in Windows Server 2003](https://support.microsoft.com/kb/325349)(如何在 Windows Server 2003 中，將管理服務的權限授與使用者)。</span><span class="sxs-lookup"><span data-stu-id="07249-139">To grant non-administrators the ability to manage services, see [How to grant users rights to manage services in Windows Server 2003](https://support.microsoft.com/kb/325349).</span></span> <span data-ttu-id="07249-140">(其他 Windows 版本的程序都很相似)。</span><span class="sxs-lookup"><span data-stu-id="07249-140">(The process is similar on other versions of Windows.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07249-141">啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]時，包含「未實作 [0x80004001]」片語的 WMI 錯誤，可能表示目標電腦上並未安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="07249-141">When starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a WMI error containing the phrase "not implemented [0x80004001]" may indicate that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not installed on the target computer.</span></span>  
  
  
