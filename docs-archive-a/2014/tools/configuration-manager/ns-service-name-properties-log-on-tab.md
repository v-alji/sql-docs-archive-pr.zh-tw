---
title: NS $ &lt; service 名稱 &gt; 屬性 ([登入] 索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 5e6816ec-d4c5-4429-8033-b97427584890
author: stevestein
ms.author: sstein
ms.openlocfilehash: b175895f2385717a67642a41a44dc0d47a1d8d92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705793"
---
# <a name="nsltservice-namegt-properties-log-on-tab"></a><span data-ttu-id="48a3c-102">NS$&lt;服務名稱&gt; 屬性 ([登入] 索引標籤)</span><span class="sxs-lookup"><span data-stu-id="48a3c-102">NS$&lt;service name&gt; Properties (Log On Tab)</span></span>
  <span data-ttu-id="48a3c-103">您可以使用 **[Notification Services 屬性]** 對話方塊的 **[登入]** 索引標籤，來指定要供 [!INCLUDE[ssNS](../../includes/ssns-md.md)] 服務使用的帳戶，以及啟動和停止該服務。</span><span class="sxs-lookup"><span data-stu-id="48a3c-103">Use the **Log On** tab of the **Notification Services Properties** dialog box to specify the account used by the [!INCLUDE[ssNS](../../includes/ssns-md.md)] service, and to start and stop the service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="48a3c-104">選項。</span><span class="sxs-lookup"><span data-stu-id="48a3c-104">Options</span></span>  
 <span data-ttu-id="48a3c-105">**本機系統帳戶**</span><span class="sxs-lookup"><span data-stu-id="48a3c-105">**Local System account**</span></span>  
 <span data-ttu-id="48a3c-106">指定不需要密碼的本機系統帳戶。</span><span class="sxs-lookup"><span data-stu-id="48a3c-106">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="48a3c-107">但是，根據授與帳戶的權限，本機系統帳戶可能會限制服務與其他伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="48a3c-107">However, the local system account may restrict the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="48a3c-108">**這個帳戶**</span><span class="sxs-lookup"><span data-stu-id="48a3c-108">**This account**</span></span>  
 <span data-ttu-id="48a3c-109">指定使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 驗證的本機或網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="48a3c-109">Specify a local or domain user account that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="48a3c-110">建議您使用具有最少服務權限的網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="48a3c-110">recommends using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="48a3c-111">如需有關選取帳戶的資訊，請搜尋《線上叢書》的＜設定 Windows 服務帳戶＞主題。</span><span class="sxs-lookup"><span data-stu-id="48a3c-111">For information about selecting an account, search Books Online for the topic, "Setting Up Windows Service Accounts."</span></span>  
  
 <span data-ttu-id="48a3c-112">**帳戶名稱**</span><span class="sxs-lookup"><span data-stu-id="48a3c-112">**Account Name**</span></span>  
 <span data-ttu-id="48a3c-113">指定本機或網域使用者帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="48a3c-113">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="48a3c-114">**密碼**</span><span class="sxs-lookup"><span data-stu-id="48a3c-114">**Password**</span></span>  
 <span data-ttu-id="48a3c-115">輸入帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="48a3c-115">Type the password of the account.</span></span>  
  
 <span data-ttu-id="48a3c-116">**確認密碼**</span><span class="sxs-lookup"><span data-stu-id="48a3c-116">**Confirm password**</span></span>  
 <span data-ttu-id="48a3c-117">再次輸入帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="48a3c-117">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="48a3c-118">**啟動**</span><span class="sxs-lookup"><span data-stu-id="48a3c-118">**Start**</span></span>  
 <span data-ttu-id="48a3c-119">啟動服務。</span><span class="sxs-lookup"><span data-stu-id="48a3c-119">Start the service.</span></span>  
  
 <span data-ttu-id="48a3c-120">**停止**</span><span class="sxs-lookup"><span data-stu-id="48a3c-120">**Stop**</span></span>  
 <span data-ttu-id="48a3c-121">停止服務。</span><span class="sxs-lookup"><span data-stu-id="48a3c-121">Stop the service.</span></span>  
  
 <span data-ttu-id="48a3c-122">**暫停**</span><span class="sxs-lookup"><span data-stu-id="48a3c-122">**Pause**</span></span>  
 <span data-ttu-id="48a3c-123">暫停服務。</span><span class="sxs-lookup"><span data-stu-id="48a3c-123">Pause the service.</span></span>  
  
 <span data-ttu-id="48a3c-124">**繼續**</span><span class="sxs-lookup"><span data-stu-id="48a3c-124">**Resume**</span></span>  
 <span data-ttu-id="48a3c-125">繼續已暫停的服務。</span><span class="sxs-lookup"><span data-stu-id="48a3c-125">Resume a paused service.</span></span>  
  
  
