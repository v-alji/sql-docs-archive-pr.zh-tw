---
title: SQL Server Integration Services 屬性 ([登入] 索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c0eb1b87-6bb0-475e-8492-0fd3c3f910ea
author: stevestein
ms.author: sstein
ms.openlocfilehash: dfef02a82872ea1df25e7ccb8526e488aaa5f406
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705781"
---
# <a name="sql-server-integration-services-properties-log-on-tab"></a><span data-ttu-id="d7f1f-102">SQL Server Integration Services 屬性 (登入索引標籤)</span><span class="sxs-lookup"><span data-stu-id="d7f1f-102">SQL Server Integration Services Properties (Log On Tab)</span></span>
  <span data-ttu-id="d7f1f-103">使用  **[屬性]** [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 對話方塊的 [登入]  索引標籤，指定要供 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服務使用的帳戶，以及啟動和停止該服務。</span><span class="sxs-lookup"><span data-stu-id="d7f1f-103">Use the **Log On** tab of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **Properties** dialog box to specify the account used by the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service, and to start and stop the service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d7f1f-104">選項。</span><span class="sxs-lookup"><span data-stu-id="d7f1f-104">Options</span></span>  
 <span data-ttu-id="d7f1f-105">**本機系統帳戶**</span><span class="sxs-lookup"><span data-stu-id="d7f1f-105">**Local System account**</span></span>  
 <span data-ttu-id="d7f1f-106">指定不需要密碼的本機系統帳戶。</span><span class="sxs-lookup"><span data-stu-id="d7f1f-106">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="d7f1f-107">但是，根據授與帳戶的權限，本機系統帳戶可能會限制服務與其他伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="d7f1f-107">However, the local system account may restrict the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="d7f1f-108">**這個帳戶**</span><span class="sxs-lookup"><span data-stu-id="d7f1f-108">**This account**</span></span>  
 <span data-ttu-id="d7f1f-109">指定使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 驗證的本機或網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d7f1f-109">Specify a local or domain user account that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="d7f1f-110">建議您使用具有最少服務權限的網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d7f1f-110">recommends using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="d7f1f-111">如需有關選取帳戶的資訊，請搜尋《線上叢書》的＜設定 Windows 服務帳戶＞主題。</span><span class="sxs-lookup"><span data-stu-id="d7f1f-111">For information about selecting an account, search Books Online for the topic, "Setting Up Windows Service Accounts."</span></span>  
  
 <span data-ttu-id="d7f1f-112">**帳戶名稱**</span><span class="sxs-lookup"><span data-stu-id="d7f1f-112">**Account Name**</span></span>  
 <span data-ttu-id="d7f1f-113">指定本機或網域使用者帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="d7f1f-113">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="d7f1f-114">**密碼**</span><span class="sxs-lookup"><span data-stu-id="d7f1f-114">**Password**</span></span>  
 <span data-ttu-id="d7f1f-115">輸入帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="d7f1f-115">Type the password of the account.</span></span>  
  
 <span data-ttu-id="d7f1f-116">**確認密碼**</span><span class="sxs-lookup"><span data-stu-id="d7f1f-116">**Confirm password**</span></span>  
 <span data-ttu-id="d7f1f-117">再次輸入帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="d7f1f-117">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="d7f1f-118">**啟動**</span><span class="sxs-lookup"><span data-stu-id="d7f1f-118">**Start**</span></span>  
 <span data-ttu-id="d7f1f-119">啟動服務。</span><span class="sxs-lookup"><span data-stu-id="d7f1f-119">Start the service.</span></span>  
  
 <span data-ttu-id="d7f1f-120">**停止**</span><span class="sxs-lookup"><span data-stu-id="d7f1f-120">**Stop**</span></span>  
 <span data-ttu-id="d7f1f-121">停止服務。</span><span class="sxs-lookup"><span data-stu-id="d7f1f-121">Stop the service.</span></span>  
  
 <span data-ttu-id="d7f1f-122">**暫停**</span><span class="sxs-lookup"><span data-stu-id="d7f1f-122">**Pause**</span></span>  
 <span data-ttu-id="d7f1f-123">暫停服務。</span><span class="sxs-lookup"><span data-stu-id="d7f1f-123">Pause the service.</span></span>  
  
 <span data-ttu-id="d7f1f-124">**繼續**</span><span class="sxs-lookup"><span data-stu-id="d7f1f-124">**Resume**</span></span>  
 <span data-ttu-id="d7f1f-125">繼續已暫停的服務。</span><span class="sxs-lookup"><span data-stu-id="d7f1f-125">Resume a paused service.</span></span>  
  
  
