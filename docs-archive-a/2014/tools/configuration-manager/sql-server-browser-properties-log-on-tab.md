---
title: SQL Server Browser 屬性 (登入索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0c1f7d0cfd9e9b05a2a04f3c3e9efba687522298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686655"
---
# <a name="sql-server-browser-properties-log-on-tab"></a><span data-ttu-id="35098-102">SQL Server Browser 屬性 (登入索引標籤)</span><span class="sxs-lookup"><span data-stu-id="35098-102">SQL Server Browser Properties (Log On Tab)</span></span>
  <span data-ttu-id="35098-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 程式會以伺服器服務的方式執行。</span><span class="sxs-lookup"><span data-stu-id="35098-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser program runs as a service on the server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="35098-104">Browser 會接聽 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源的內送要求，並提供有關在電腦上所安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的資訊。</span><span class="sxs-lookup"><span data-stu-id="35098-104">Browser listens for incoming requests for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources and provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="35098-105">瀏覽器會接聽 UDP 通訊埠，並接受使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol (SSRP) 的未驗證要求。</span><span class="sxs-lookup"><span data-stu-id="35098-105">Browser listens on a UDP port and accepts unauthenticated requests using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol (SSRP).</span></span>  
  
 <span data-ttu-id="35098-106">帳戶密碼的變更會立即生效，不需要重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="35098-106">Changing the password of an account takes effect immediately without restarting the service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="35098-107">選項。</span><span class="sxs-lookup"><span data-stu-id="35098-107">Options</span></span>  
 <span data-ttu-id="35098-108">**本機系統帳戶**</span><span class="sxs-lookup"><span data-stu-id="35098-108">**Local System account**</span></span>  
 <span data-ttu-id="35098-109">在本機系統帳戶的安全性內容執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務。</span><span class="sxs-lookup"><span data-stu-id="35098-109">Run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service in the security context of the Local System account.</span></span> <span data-ttu-id="35098-110">如果可能的話，請另外使用權限較低的帳戶來執行。</span><span class="sxs-lookup"><span data-stu-id="35098-110">When possible, use a low-permission account instead.</span></span>  
  
 <span data-ttu-id="35098-111">**這個帳戶**</span><span class="sxs-lookup"><span data-stu-id="35098-111">**This account**</span></span>  
 <span data-ttu-id="35098-112">指定使用 Windows 驗證的本機或網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="35098-112">Specify a local or domain user account that uses Windows Authentication.</span></span> <span data-ttu-id="35098-113">建議您使用具有最少服務權限的網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="35098-113">We recommend using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="35098-114">如需有關選取帳戶的資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜設定 Windows 服務帳戶＞。</span><span class="sxs-lookup"><span data-stu-id="35098-114">For information about selecting an account, see "Setting Up Windows Service Accounts" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="35098-115">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="35098-115">**Browse**</span></span>  
 <span data-ttu-id="35098-116">瀏覽使用者或內建的安全性主體。</span><span class="sxs-lookup"><span data-stu-id="35098-116">Browse for a user or built-in security principal.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="35098-117">請使用低權限的帳戶。</span><span class="sxs-lookup"><span data-stu-id="35098-117">Use a low-permission account.</span></span> <span data-ttu-id="35098-118">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務所需權限的資訊，請參閱 [SQL Server Browser 服務](../../../2014/tools/configuration-manager/sql-server-browser-service.md)的＜安全性＞一節。</span><span class="sxs-lookup"><span data-stu-id="35098-118">For information about the permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Service, see the Security section of [SQL Server Browser Service](../../../2014/tools/configuration-manager/sql-server-browser-service.md).</span></span>  
  
 <span data-ttu-id="35098-119">**密碼**</span><span class="sxs-lookup"><span data-stu-id="35098-119">**Password**</span></span>  
 <span data-ttu-id="35098-120">輸入安全性主體的密碼。</span><span class="sxs-lookup"><span data-stu-id="35098-120">Enter the password of the security principal.</span></span>  
  
 <span data-ttu-id="35098-121">**確認密碼**</span><span class="sxs-lookup"><span data-stu-id="35098-121">**Confirm password**</span></span>  
 <span data-ttu-id="35098-122">確認安全性主體的密碼。</span><span class="sxs-lookup"><span data-stu-id="35098-122">Confirm the password of the security principal.</span></span>  
  
 <span data-ttu-id="35098-123">**服務狀態**</span><span class="sxs-lookup"><span data-stu-id="35098-123">**Service status**</span></span>  
 <span data-ttu-id="35098-124">表示這項服務為執行中、已停止或已停用。</span><span class="sxs-lookup"><span data-stu-id="35098-124">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="35098-125">" **...** " 表示狀態變更已暫止。</span><span class="sxs-lookup"><span data-stu-id="35098-125">"**...**" indicates a state change is pending.</span></span>  
  
 <span data-ttu-id="35098-126">**啟動**</span><span class="sxs-lookup"><span data-stu-id="35098-126">**Start**</span></span>  
 <span data-ttu-id="35098-127">啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 瀏覽器服務。</span><span class="sxs-lookup"><span data-stu-id="35098-127">Start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
 <span data-ttu-id="35098-128">**停止**</span><span class="sxs-lookup"><span data-stu-id="35098-128">**Stop**</span></span>  
 <span data-ttu-id="35098-129">停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="35098-129">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
 <span data-ttu-id="35098-130">**暫停**</span><span class="sxs-lookup"><span data-stu-id="35098-130">**Pause**</span></span>  
 <span data-ttu-id="35098-131">暫停 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務。</span><span class="sxs-lookup"><span data-stu-id="35098-131">Pause the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
 <span data-ttu-id="35098-132">**繼續**</span><span class="sxs-lookup"><span data-stu-id="35098-132">**Resume**</span></span>  
 <span data-ttu-id="35098-133">繼續已暫停的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 瀏覽器服務。</span><span class="sxs-lookup"><span data-stu-id="35098-133">Resume a paused [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35098-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35098-134">See Also</span></span>  
 [<span data-ttu-id="35098-135">SQL Server Browser 服務</span><span class="sxs-lookup"><span data-stu-id="35098-135">SQL Server Browser Service</span></span>](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
