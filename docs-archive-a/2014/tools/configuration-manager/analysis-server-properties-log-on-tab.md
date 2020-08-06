---
title: Analysis Server 屬性 (登入索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: a82e0c98-efaa-4b0b-9582-3c879ee42444
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8db5576e48e7f12ef1733175875d2cd065e376fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708874"
---
# <a name="analysis-server-properties-log-on-tab"></a><span data-ttu-id="9cf0c-102">Analysis Server 屬性 (登入索引標籤)</span><span class="sxs-lookup"><span data-stu-id="9cf0c-102">Analysis Server Properties (Log On Tab)</span></span>
  <span data-ttu-id="9cf0c-103">您可以使用 **[Analysis Server 屬性]** 對話方塊的 **[登入]** 索引標籤，來指定要供 [!INCLUDE[ssAS](../../includes/ssas-md.md)] 服務使用的帳戶，以及啟動和停止該服務。</span><span class="sxs-lookup"><span data-stu-id="9cf0c-103">Use the **Log On** tab of the **Analysis Server Properties** dialog box to specify the account used by the [!INCLUDE[ssAS](../../includes/ssas-md.md)] service, and to start and stop the service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9cf0c-104">在叢集執行個體上變更服務所使用的 **[帳戶名稱]** 時，新帳戶必須是所要變更之服務安裝期間所指定網域群組的成員，或者您必須擁有在該群組中加入成員的權限。</span><span class="sxs-lookup"><span data-stu-id="9cf0c-104">When changing the **Account Name** used by a service on a clustered instance, the new account must either be a member of the domain group specified during setup for the service being changed, or you must have permission to add members to that group.</span></span> <span data-ttu-id="9cf0c-105">如果您沒有修改群組成員資格的權限，請與網域管理員連絡。</span><span class="sxs-lookup"><span data-stu-id="9cf0c-105">If you do not have permission to modify group membership, contact the domain administrator.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9cf0c-106">選項。</span><span class="sxs-lookup"><span data-stu-id="9cf0c-106">Options</span></span>  
 <span data-ttu-id="9cf0c-107">**本機系統帳戶**</span><span class="sxs-lookup"><span data-stu-id="9cf0c-107">**Local System account**</span></span>  
 <span data-ttu-id="9cf0c-108">指定不需要密碼的本機系統帳戶。</span><span class="sxs-lookup"><span data-stu-id="9cf0c-108">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="9cf0c-109">但是，根據授與帳戶的權限，本機系統帳戶可能會限制服務與其他伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="9cf0c-109">However, the local system account may restrict the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="9cf0c-110">**這個帳戶**</span><span class="sxs-lookup"><span data-stu-id="9cf0c-110">**This account**</span></span>  
 <span data-ttu-id="9cf0c-111">指定使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 驗證的本機或網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9cf0c-111">Specify a local or domain user account that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="9cf0c-112">建議您使用具有最少服務權限的網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9cf0c-112">recommends using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="9cf0c-113">如需有關選取帳戶的資訊，請搜尋《線上叢書》的＜設定 Windows 服務帳戶＞主題。</span><span class="sxs-lookup"><span data-stu-id="9cf0c-113">For information about selecting an account, search Books Online for the topic Setting Up Windows Service Accounts.</span></span>  
  
 <span data-ttu-id="9cf0c-114">**帳戶名稱**</span><span class="sxs-lookup"><span data-stu-id="9cf0c-114">**Account Name**</span></span>  
 <span data-ttu-id="9cf0c-115">指定本機或網域使用者帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="9cf0c-115">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="9cf0c-116">**密碼**</span><span class="sxs-lookup"><span data-stu-id="9cf0c-116">**Password**</span></span>  
 <span data-ttu-id="9cf0c-117">輸入帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="9cf0c-117">Type the password of the account.</span></span>  
  
 <span data-ttu-id="9cf0c-118">**確認密碼**</span><span class="sxs-lookup"><span data-stu-id="9cf0c-118">**Confirm password**</span></span>  
 <span data-ttu-id="9cf0c-119">再次輸入帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="9cf0c-119">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="9cf0c-120">**啟動**</span><span class="sxs-lookup"><span data-stu-id="9cf0c-120">**Start**</span></span>  
 <span data-ttu-id="9cf0c-121">啟動服務。</span><span class="sxs-lookup"><span data-stu-id="9cf0c-121">Start the service.</span></span>  
  
 <span data-ttu-id="9cf0c-122">**停止**</span><span class="sxs-lookup"><span data-stu-id="9cf0c-122">**Stop**</span></span>  
 <span data-ttu-id="9cf0c-123">停止服務。</span><span class="sxs-lookup"><span data-stu-id="9cf0c-123">Stop the service.</span></span>  
  
 <span data-ttu-id="9cf0c-124">**暫停**</span><span class="sxs-lookup"><span data-stu-id="9cf0c-124">**Pause**</span></span>  
 <span data-ttu-id="9cf0c-125">暫停服務。</span><span class="sxs-lookup"><span data-stu-id="9cf0c-125">Pause the service.</span></span>  
  
 <span data-ttu-id="9cf0c-126">**繼續**</span><span class="sxs-lookup"><span data-stu-id="9cf0c-126">**Resume**</span></span>  
 <span data-ttu-id="9cf0c-127">繼續已暫停的服務。</span><span class="sxs-lookup"><span data-stu-id="9cf0c-127">Resume a paused service.</span></span>  
  
  
