---
title: 報表伺服器屬性 (登入索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: f54be594-f290-4db2-bf18-fd2521728a4a
author: stevestein
ms.author: sstein
ms.openlocfilehash: a2fca58ee9b419613bc8f1dbd325481efc9069c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597472"
---
# <a name="report-server-properties-log-on-tab"></a><span data-ttu-id="23e4e-102">Report Server 屬性 (登入索引標籤)</span><span class="sxs-lookup"><span data-stu-id="23e4e-102">Report Server Properties (Log On Tab)</span></span>
  <span data-ttu-id="23e4e-103">您可以使用 **[Report Server 屬性]** 對話方塊的 **[登入]** 索引標籤來指定 Report Server 服務所使用的帳戶，以及啟動和停止該服務。</span><span class="sxs-lookup"><span data-stu-id="23e4e-103">Use the **Log On** tab of the **Report Server Properties** dialog box to specify the account used by the Report Server service, and to start and stop the service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="23e4e-104">選項。</span><span class="sxs-lookup"><span data-stu-id="23e4e-104">Options</span></span>  
 <span data-ttu-id="23e4e-105">**本機系統帳戶**</span><span class="sxs-lookup"><span data-stu-id="23e4e-105">**Local System account**</span></span>  
 <span data-ttu-id="23e4e-106">指定不需要密碼的本機系統帳戶。</span><span class="sxs-lookup"><span data-stu-id="23e4e-106">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="23e4e-107">但是，根據授與帳戶的權限，本機系統帳戶可能會限制服務與其他伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="23e4e-107">However, the local system account may restrict the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="23e4e-108">**這個帳戶**</span><span class="sxs-lookup"><span data-stu-id="23e4e-108">**This account**</span></span>  
 <span data-ttu-id="23e4e-109">指定使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 驗證的本機或網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="23e4e-109">Specify a local or domain user account that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="23e4e-110">建議您使用具有最少服務權限的網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="23e4e-110">recommends using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="23e4e-111">如需有關選取帳戶的資訊，請搜尋《線上叢書》的＜設定 Windows 服務帳戶＞主題。</span><span class="sxs-lookup"><span data-stu-id="23e4e-111">For information about selecting an account, search Books Online for the topic Setting Up Windows Service Accounts.</span></span>  
  
 <span data-ttu-id="23e4e-112">**帳戶名稱**</span><span class="sxs-lookup"><span data-stu-id="23e4e-112">**Account Name**</span></span>  
 <span data-ttu-id="23e4e-113">指定本機或網域使用者帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="23e4e-113">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="23e4e-114">**密碼**</span><span class="sxs-lookup"><span data-stu-id="23e4e-114">**Password**</span></span>  
 <span data-ttu-id="23e4e-115">輸入帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="23e4e-115">Type the password of the account.</span></span>  
  
 <span data-ttu-id="23e4e-116">**確認密碼**</span><span class="sxs-lookup"><span data-stu-id="23e4e-116">**Confirm password**</span></span>  
 <span data-ttu-id="23e4e-117">再次輸入帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="23e4e-117">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="23e4e-118">**啟動**</span><span class="sxs-lookup"><span data-stu-id="23e4e-118">**Start**</span></span>  
 <span data-ttu-id="23e4e-119">啟動服務。</span><span class="sxs-lookup"><span data-stu-id="23e4e-119">Start the service.</span></span>  
  
 <span data-ttu-id="23e4e-120">**停止**</span><span class="sxs-lookup"><span data-stu-id="23e4e-120">**Stop**</span></span>  
 <span data-ttu-id="23e4e-121">停止服務。</span><span class="sxs-lookup"><span data-stu-id="23e4e-121">Stop the service.</span></span>  
  
 <span data-ttu-id="23e4e-122">**暫停**</span><span class="sxs-lookup"><span data-stu-id="23e4e-122">**Pause**</span></span>  
 <span data-ttu-id="23e4e-123">暫停服務。</span><span class="sxs-lookup"><span data-stu-id="23e4e-123">Pause the service.</span></span>  
  
 <span data-ttu-id="23e4e-124">**繼續**</span><span class="sxs-lookup"><span data-stu-id="23e4e-124">**Resume**</span></span>  
 <span data-ttu-id="23e4e-125">繼續已暫停的服務。</span><span class="sxs-lookup"><span data-stu-id="23e4e-125">Resume a paused service.</span></span>  
  
  
