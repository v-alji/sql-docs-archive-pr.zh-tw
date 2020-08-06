---
title: SQL Server Agent 屬性 (登入索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 01fc6329-5d6b-4186-9565-395f375477bb
author: stevestein
ms.author: sstein
ms.openlocfilehash: cd899e8824adacd07fa1d8d7d51b2143d10cadd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595336"
---
# <a name="sql-server-agent-properties-log-on-tab"></a><span data-ttu-id="9e8a2-102">SQL Server Agent 屬性 (登入索引標籤)</span><span class="sxs-lookup"><span data-stu-id="9e8a2-102">SQL Server Agent Properties (Log On Tab)</span></span>
  <span data-ttu-id="9e8a2-103">您可以使用 **[SQL Server Agent 屬性]** 對話方塊的 **[登入]** 索引標籤指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務所使用的帳戶，以及啟動和停止該服務。</span><span class="sxs-lookup"><span data-stu-id="9e8a2-103">Use the **Log On** tab of the **SQL Server Agent Properties** dialog box to specify the account used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service, and to start and stop the service.</span></span> <span data-ttu-id="9e8a2-104">帳戶密碼的變更會立即生效，不需要重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="9e8a2-104">Changing the password of an account takes effect immediately without restarting the service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e8a2-105">在叢集執行個體上變更服務所使用的帳戶名稱時，新帳戶必須是所要變更之服務安裝期間所指定網域群組的成員，或者您必須擁有在該群組中加入成員的權限。</span><span class="sxs-lookup"><span data-stu-id="9e8a2-105">When changing the account name used by a service on a clustered instance, the new account must be a member of the domain group specified during setup for the service being changed, or you must have permission to add members to that group.</span></span> <span data-ttu-id="9e8a2-106">如果您沒有修改群組成員資格的權限，請與網域管理員連絡。</span><span class="sxs-lookup"><span data-stu-id="9e8a2-106">If you do not have permission to modify group membership, contact the domain administrator.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9e8a2-107">選項。</span><span class="sxs-lookup"><span data-stu-id="9e8a2-107">Options</span></span>  
 <span data-ttu-id="9e8a2-108">**本機系統帳戶**</span><span class="sxs-lookup"><span data-stu-id="9e8a2-108">**Local System account**</span></span>  
 <span data-ttu-id="9e8a2-109">指定不需要密碼的本機系統帳戶。</span><span class="sxs-lookup"><span data-stu-id="9e8a2-109">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="9e8a2-110">但是，根據授與帳戶的權限，本機系統帳戶可能會限制服務與其他伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="9e8a2-110">However, the local system account may restrict the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="9e8a2-111">**這個帳戶**</span><span class="sxs-lookup"><span data-stu-id="9e8a2-111">**This account**</span></span>  
 <span data-ttu-id="9e8a2-112">指定使用 Windows 驗證的本機或網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9e8a2-112">Specify a local or domain user account that uses Windows Authentication.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="9e8a2-113">建議您使用具有最少服務權限的網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9e8a2-113">recommends using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="9e8a2-114">如需有關選取帳戶的資訊，請搜尋《線上叢書》的＜設定 Windows 服務帳戶＞。</span><span class="sxs-lookup"><span data-stu-id="9e8a2-114">For information about selecting an account, search Books Online for "Setting Up Windows Service Accounts."</span></span>  
  
 <span data-ttu-id="9e8a2-115">**帳戶名稱**</span><span class="sxs-lookup"><span data-stu-id="9e8a2-115">**Account Name**</span></span>  
 <span data-ttu-id="9e8a2-116">指定本機或網域使用者帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="9e8a2-116">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="9e8a2-117">**密碼**</span><span class="sxs-lookup"><span data-stu-id="9e8a2-117">**Password**</span></span>  
 <span data-ttu-id="9e8a2-118">輸入帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="9e8a2-118">Type the password of the account.</span></span>  
  
 <span data-ttu-id="9e8a2-119">**確認密碼**</span><span class="sxs-lookup"><span data-stu-id="9e8a2-119">**Confirm password**</span></span>  
 <span data-ttu-id="9e8a2-120">再次輸入帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="9e8a2-120">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="9e8a2-121">**啟動**</span><span class="sxs-lookup"><span data-stu-id="9e8a2-121">**Start**</span></span>  
 <span data-ttu-id="9e8a2-122">啟動服務。</span><span class="sxs-lookup"><span data-stu-id="9e8a2-122">Start the service.</span></span>  
  
 <span data-ttu-id="9e8a2-123">**停止**</span><span class="sxs-lookup"><span data-stu-id="9e8a2-123">**Stop**</span></span>  
 <span data-ttu-id="9e8a2-124">停止服務。</span><span class="sxs-lookup"><span data-stu-id="9e8a2-124">Stop the service.</span></span>  
  
 <span data-ttu-id="9e8a2-125">**暫停**</span><span class="sxs-lookup"><span data-stu-id="9e8a2-125">**Pause**</span></span>  
 <span data-ttu-id="9e8a2-126">暫停服務。</span><span class="sxs-lookup"><span data-stu-id="9e8a2-126">Pause the service.</span></span>  
  
 <span data-ttu-id="9e8a2-127">**繼續**</span><span class="sxs-lookup"><span data-stu-id="9e8a2-127">**Resume**</span></span>  
 <span data-ttu-id="9e8a2-128">繼續已暫停的服務。</span><span class="sxs-lookup"><span data-stu-id="9e8a2-128">Resume a paused service.</span></span>  
  
  
