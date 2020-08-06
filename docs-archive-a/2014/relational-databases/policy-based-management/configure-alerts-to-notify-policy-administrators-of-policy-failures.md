---
title: 設定警示以便向原則管理員通知原則失敗 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, configure alerts
ms.assetid: e8e60159-d5b0-49d5-91f3-af8e9cb994c1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9eb84ced3bb6313dd5920deaf479925556f08fc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686914"
---
# <a name="configure-alerts-to-notify-policy-administrators-of-policy-failures"></a><span data-ttu-id="bec8d-102">設定警示以便向原則管理員通知原則失敗</span><span class="sxs-lookup"><span data-stu-id="bec8d-102">Configure Alerts to Notify Policy Administrators of Policy Failures</span></span>
  <span data-ttu-id="bec8d-103">當原則式管理原則在其中一種自動評估模式中執行時，如果發生原則違規，系統就會在事件記錄檔中寫入一則訊息。</span><span class="sxs-lookup"><span data-stu-id="bec8d-103">When Policy-Based Management policies are executed in one of the three automated evaluation modes, if a policy violation occurs, a message is written to the event log.</span></span> <span data-ttu-id="bec8d-104">若要在這則訊息寫入事件記錄檔時收到通知，您可以建立偵測訊息並執行動作的警示。</span><span class="sxs-lookup"><span data-stu-id="bec8d-104">To be notified when this message is written to the event log, you can create an alert to detect the message and perform an action.</span></span> <span data-ttu-id="bec8d-105">此警示應該會偵測到下表所列的訊息。</span><span class="sxs-lookup"><span data-stu-id="bec8d-105">The alert should detect the messages as shown in the following table.</span></span>  
  
|<span data-ttu-id="bec8d-106">執行模式</span><span class="sxs-lookup"><span data-stu-id="bec8d-106">Execution mode</span></span>|<span data-ttu-id="bec8d-107">訊息編號</span><span class="sxs-lookup"><span data-stu-id="bec8d-107">Message number</span></span>|  
|--------------------|--------------------|  
|<span data-ttu-id="bec8d-108">變更時 - 避免</span><span class="sxs-lookup"><span data-stu-id="bec8d-108">On change: prevent</span></span><br /><br /> <span data-ttu-id="bec8d-109">(若為自動)</span><span class="sxs-lookup"><span data-stu-id="bec8d-109">(if automatic)</span></span>|<span data-ttu-id="bec8d-110">34050</span><span class="sxs-lookup"><span data-stu-id="bec8d-110">34050</span></span>|  
|<span data-ttu-id="bec8d-111">變更時 - 避免</span><span class="sxs-lookup"><span data-stu-id="bec8d-111">On change: prevent</span></span><br /><br /> <span data-ttu-id="bec8d-112">(若為視需要)</span><span class="sxs-lookup"><span data-stu-id="bec8d-112">(if On demand)</span></span>|<span data-ttu-id="bec8d-113">34051</span><span class="sxs-lookup"><span data-stu-id="bec8d-113">34051</span></span>|  
|<span data-ttu-id="bec8d-114">按排程時間</span><span class="sxs-lookup"><span data-stu-id="bec8d-114">On schedule</span></span>|<span data-ttu-id="bec8d-115">34052</span><span class="sxs-lookup"><span data-stu-id="bec8d-115">34052</span></span>|  
|<span data-ttu-id="bec8d-116">變更時</span><span class="sxs-lookup"><span data-stu-id="bec8d-116">On change</span></span>|<span data-ttu-id="bec8d-117">34053</span><span class="sxs-lookup"><span data-stu-id="bec8d-117">34053</span></span>|  
  
 <span data-ttu-id="bec8d-118">若要設定警示來回應原則式管理錯誤訊息，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="bec8d-118">To set up an alert to respond to the Policy-Based Management error messages, see the following topics:</span></span>  
  
-   [<span data-ttu-id="bec8d-119">建立操作員</span><span class="sxs-lookup"><span data-stu-id="bec8d-119">Create an Operator</span></span>](../../ssms/agent/create-an-operator.md)  
  
-   [<span data-ttu-id="bec8d-120">使用錯誤號碼建立警示</span><span class="sxs-lookup"><span data-stu-id="bec8d-120">Create an Alert Using an Error Number</span></span>](../../ssms/agent/create-an-alert-using-an-error-number.md)  
  
-   [<span data-ttu-id="bec8d-121">指派警示給操作員</span><span class="sxs-lookup"><span data-stu-id="bec8d-121">Assign Alerts to an Operator</span></span>](../../ssms/agent/assign-alerts-to-an-operator.md)  
  
## <a name="permissions"></a><span data-ttu-id="bec8d-122">權限</span><span class="sxs-lookup"><span data-stu-id="bec8d-122">Permissions</span></span>  
 <span data-ttu-id="bec8d-123">視需要評估原則時，這些原則就會在使用者的安全性內容中執行。</span><span class="sxs-lookup"><span data-stu-id="bec8d-123">When policies are evaluated on demand, they execute in the security context of the user.</span></span> <span data-ttu-id="bec8d-124">若要寫入錯誤記錄檔，使用者必須擁有 ALTER TRACE 權限或屬於系統管理員 (sysadmin) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="bec8d-124">To write to the error log, the user must have ALTER TRACE permissions or be a member of the sysadmin fixed server role.</span></span> <span data-ttu-id="bec8d-125">擁有較低權限之使用者所評估的原則不會寫入事件記錄檔，而且不會引發警示。</span><span class="sxs-lookup"><span data-stu-id="bec8d-125">Policies that are evaluated by a user that has less privileges will not write to the event log, and will not fire an alert.</span></span>  
  
 <span data-ttu-id="bec8d-126">自動執行模式會以系統管理員 (sysadmin) 角色成員的身分執行。</span><span class="sxs-lookup"><span data-stu-id="bec8d-126">The automated execution modes execute as a member of the sysadmin role.</span></span> <span data-ttu-id="bec8d-127">這樣可讓原則寫入錯誤記錄檔並且引發警示。</span><span class="sxs-lookup"><span data-stu-id="bec8d-127">This allows the policy to write to the error log and raise an alert.</span></span>  
  
## <a name="additional-considerations-about-alerts"></a><span data-ttu-id="bec8d-128">關於警示的其他考量</span><span class="sxs-lookup"><span data-stu-id="bec8d-128">Additional Considerations About Alerts</span></span>  
 <span data-ttu-id="bec8d-129">請注意下列關於警示的其他考量：</span><span class="sxs-lookup"><span data-stu-id="bec8d-129">Be aware of the following additional considerations about alerts:</span></span>  
  
-   <span data-ttu-id="bec8d-130">系統只會針對啟用的原則引發警示。</span><span class="sxs-lookup"><span data-stu-id="bec8d-130">Alerts are raised only for policies that are enabled.</span></span> <span data-ttu-id="bec8d-131">由於無法啟用 [視需要]\*\*\*\* 原則，因此無法針對視需要執行的原則引發警示。</span><span class="sxs-lookup"><span data-stu-id="bec8d-131">Because **On demand** policies cannot be enabled, alerts are not raised for policies that are executed on demand.</span></span>  
  
-   <span data-ttu-id="bec8d-132">如果您想要採取的動作包含傳送電子郵件訊息，就必須設定郵件帳戶。</span><span class="sxs-lookup"><span data-stu-id="bec8d-132">If the action you want to take includes sending an e-mail message, you must configure a mail account.</span></span> <span data-ttu-id="bec8d-133">我們建議您使用 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="bec8d-133">We recommend that you use Database Mail.</span></span> <span data-ttu-id="bec8d-134">如需設定 Database Mail 的詳細資訊，請參閱 [建立 Database Mail 帳戶](../database-mail/create-a-database-mail-account.md)。</span><span class="sxs-lookup"><span data-stu-id="bec8d-134">For more information about how to set up Database Mail, see [Create a Database Mail Account](../database-mail/create-a-database-mail-account.md).</span></span>  
  
  
