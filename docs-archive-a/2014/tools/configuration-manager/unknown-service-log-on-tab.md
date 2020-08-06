---
title: 未知的服務 (登入] 索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: e9b35cb5-d8ae-42ea-b59e-deedc99c4823
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0bda49cd95475d4f922f41ebe1701a814c3f60fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592419"
---
# <a name="unknown-service-log-on-tab"></a><span data-ttu-id="39913-102">未知的服務 (登入索引標籤)</span><span class="sxs-lookup"><span data-stu-id="39913-102">Unknown Service (Log On Tab)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="39913-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員無法識別此服務。</span><span class="sxs-lookup"><span data-stu-id="39913-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager is unable to identify this service.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="39913-104">組態管理員」從執行該服務之電腦的 WMI 提供者取得服務資訊。</span><span class="sxs-lookup"><span data-stu-id="39913-104">Configuration Manager receives service information from the WMI provider on the computer running the service.</span></span> <span data-ttu-id="39913-105">讀取服務屬性時發生錯誤，或服務屬性不完整。</span><span class="sxs-lookup"><span data-stu-id="39913-105">Either there was an error while reading the service properties, or the service properties are not complete.</span></span> <span data-ttu-id="39913-106">若要解決此問題，請嘗試關閉並重新開啟「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」，或檢查執行該服務之電腦的 WMI 提供者。</span><span class="sxs-lookup"><span data-stu-id="39913-106">To resolve the problem, try closing and reopening [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or check the WMI provider on the computer running the service.</span></span>  
  
 <span data-ttu-id="39913-107">WMI 提供者是 Windows 元件。</span><span class="sxs-lookup"><span data-stu-id="39913-107">The WMI provider is a Windows component.</span></span> <span data-ttu-id="39913-108">如需有關如何檢查 WMI 提供者之權限的資訊，請參閱《SQL Server 線上叢書》中的＜如何：設定 WMI 在 SQL Server 工具中顯示伺服器狀態＞。</span><span class="sxs-lookup"><span data-stu-id="39913-108">For information on how to check permissions on the WMI provider, see "How to: Configure WMI to Show Server Status in SQL Server Tools" in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="39913-109">如果您確認自己檢視的是正確的服務，請使用 **[未知的服務屬性]** 對話方塊的 **[登入]** 索引標籤來指定此服務所使用的帳戶，以及啟動和停止該服務。</span><span class="sxs-lookup"><span data-stu-id="39913-109">If you believe you are viewing the correct service, use the **Log On** tab of the **Unknown Service Properties** dialog box to specify the account used by this service, and to start and stop the service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="39913-110">選項。</span><span class="sxs-lookup"><span data-stu-id="39913-110">Options</span></span>  
 <span data-ttu-id="39913-111">**本機系統帳戶**</span><span class="sxs-lookup"><span data-stu-id="39913-111">**Local System account**</span></span>  
 <span data-ttu-id="39913-112">指定不需要密碼的本機系統帳戶。</span><span class="sxs-lookup"><span data-stu-id="39913-112">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="39913-113">但是，根據授與帳戶的權限，本機系統帳戶可能會禁止服務與其他伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="39913-113">However, the local system account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="39913-114">**這個帳戶**</span><span class="sxs-lookup"><span data-stu-id="39913-114">**This account**</span></span>  
 <span data-ttu-id="39913-115">指定使用 Windows 驗證的本機或網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="39913-115">Specify a local or domain user account that uses Windows Authentication.</span></span> <span data-ttu-id="39913-116">建議您使用具有最少服務權限的網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="39913-116">We recommend using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="39913-117">如需有關選取帳戶的資訊，請參閱《SQL Server 線上叢書》中的＜設定 Windows 服務帳戶＞。</span><span class="sxs-lookup"><span data-stu-id="39913-117">For information about selecting an account, "Setting Up Windows Service Accounts" in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="39913-118">**帳戶名稱**</span><span class="sxs-lookup"><span data-stu-id="39913-118">**Account Name**</span></span>  
 <span data-ttu-id="39913-119">指定本機或網域使用者帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="39913-119">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="39913-120">**密碼**</span><span class="sxs-lookup"><span data-stu-id="39913-120">**Password**</span></span>  
 <span data-ttu-id="39913-121">輸入帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="39913-121">Type the password of the account.</span></span>  
  
 <span data-ttu-id="39913-122">**確認密碼**</span><span class="sxs-lookup"><span data-stu-id="39913-122">**Confirm password**</span></span>  
 <span data-ttu-id="39913-123">再次輸入帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="39913-123">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="39913-124">**啟動**</span><span class="sxs-lookup"><span data-stu-id="39913-124">**Start**</span></span>  
 <span data-ttu-id="39913-125">啟動服務。</span><span class="sxs-lookup"><span data-stu-id="39913-125">Start the service.</span></span>  
  
 <span data-ttu-id="39913-126">**停止**</span><span class="sxs-lookup"><span data-stu-id="39913-126">**Stop**</span></span>  
 <span data-ttu-id="39913-127">停止服務。</span><span class="sxs-lookup"><span data-stu-id="39913-127">Stop the service.</span></span>  
  
 <span data-ttu-id="39913-128">**暫停**</span><span class="sxs-lookup"><span data-stu-id="39913-128">**Pause**</span></span>  
 <span data-ttu-id="39913-129">暫停服務。</span><span class="sxs-lookup"><span data-stu-id="39913-129">Pause the service.</span></span>  
  
 <span data-ttu-id="39913-130">**繼續**</span><span class="sxs-lookup"><span data-stu-id="39913-130">**Resume**</span></span>  
 <span data-ttu-id="39913-131">繼續已暫停的服務。</span><span class="sxs-lookup"><span data-stu-id="39913-131">Resume a paused service.</span></span>  
  
  
