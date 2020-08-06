---
title: 傳送登入工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferloginstask.f1
helpviewer_keywords:
- Transfer Logins task [Integration Services]
ms.assetid: 1df60fd6-c019-405d-8155-c330dbac2cc1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d42d39b6cc7c2f350e3e3adc774be23934981369
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584662"
---
# <a name="transfer-logins-task"></a><span data-ttu-id="57fef-102">傳送登入工作</span><span class="sxs-lookup"><span data-stu-id="57fef-102">Transfer Logins Task</span></span>
  <span data-ttu-id="57fef-103">「傳送登入」工作會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體之間傳送一個或多個登入。</span><span class="sxs-lookup"><span data-stu-id="57fef-103">The Transfer Logins task transfers one or more logins between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="transfer-logins-between-instances-of-sql-server"></a><span data-ttu-id="57fef-104">在 SQL Server 的執行個體之間傳送登入</span><span class="sxs-lookup"><span data-stu-id="57fef-104">Transfer Logins Between Instances of SQL Server</span></span>  
 <span data-ttu-id="57fef-105">傳送登入工作支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 來源和目的地。</span><span class="sxs-lookup"><span data-stu-id="57fef-105">The Transfer Logins task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="57fef-106">事件</span><span class="sxs-lookup"><span data-stu-id="57fef-106">Events</span></span>  
 <span data-ttu-id="57fef-107">「傳送登入」工作會引發報告已傳送登入數目的資訊事件，並在覆寫登入時引發警告事件。</span><span class="sxs-lookup"><span data-stu-id="57fef-107">The task raises an information event that reports the number of logins transferred and a warning event when a login is overwritten.</span></span>  
  
 <span data-ttu-id="57fef-108">該工作並不報告登入傳送的累加進度，它只報告 0% 和 100 % 完成。</span><span class="sxs-lookup"><span data-stu-id="57fef-108">The Transfer Logins task does not report incremental progress of the login transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="57fef-109">執行值</span><span class="sxs-lookup"><span data-stu-id="57fef-109">Execution Value</span></span>  
 <span data-ttu-id="57fef-110">工作之 `ExecutionValue` 屬性中定義的執行值會傳回已傳送的登入數目。</span><span class="sxs-lookup"><span data-stu-id="57fef-110">The execution value, defined in the `ExecutionValue` property of the task, returns the number of logins transferred.</span></span> <span data-ttu-id="57fef-111">透過將使用者自訂變數指派給「傳送登入」工作的 `ExecValueVariable` 屬性，可將與登入傳送相關的資訊用於封裝中的其他物件。</span><span class="sxs-lookup"><span data-stu-id="57fef-111">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Logins task, information about the login transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="57fef-112">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md)和[在封裝中使用變數](../use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="57fef-112">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="57fef-113">記錄項目</span><span class="sxs-lookup"><span data-stu-id="57fef-113">Log Entries</span></span>  
 <span data-ttu-id="57fef-114">「傳送登入」工作包含下列自訂記錄項目：</span><span class="sxs-lookup"><span data-stu-id="57fef-114">The Transfer Logins task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="57fef-115">TransferLoginsTaskStarTransferringObjects   此記錄項目報告傳送已開始。</span><span class="sxs-lookup"><span data-stu-id="57fef-115">TransferLoginsTaskStarTransferringObjects    This log entry reports the transfer has started.</span></span> <span data-ttu-id="57fef-116">記錄項目會包含開始時間。</span><span class="sxs-lookup"><span data-stu-id="57fef-116">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="57fef-117">TransferLoginsTaskFinishedTransferringObjects   此記錄項目報告傳送已完成。</span><span class="sxs-lookup"><span data-stu-id="57fef-117">TransferLoginsTaskFinishedTransferringObjects   This log entry reports the transfer has completed.</span></span> <span data-ttu-id="57fef-118">記錄項目會包含結束時間。</span><span class="sxs-lookup"><span data-stu-id="57fef-118">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="57fef-119">此外，`OnInformation` 事件的記錄項目會報告已傳送的登入數目，並會為在目的地上覆寫的每個登入，寫入 `OnWarning` 事件的記錄項目。</span><span class="sxs-lookup"><span data-stu-id="57fef-119">In addition, a log entry for the `OnInformation` event reports the number of logins that were transferred, and a log entry for the `OnWarning` event is written for each login on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="57fef-120">安全性和權限</span><span class="sxs-lookup"><span data-stu-id="57fef-120">Security and Permissions</span></span>  
 <span data-ttu-id="57fef-121">若要瀏覽來源伺服器上的登入，並在目的地伺服器上建立登入，使用者必須同時是兩個伺服器上 sysadmin 伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="57fef-121">To browse logins on the source server and to create logins on the destination server, the user must be a member of the sysadmin server role on both servers.</span></span>  
  
## <a name="configuration-of-the-transfer-logins-task"></a><span data-ttu-id="57fef-122">設定傳送登入工作</span><span class="sxs-lookup"><span data-stu-id="57fef-122">Configuration of the Transfer Logins Task</span></span>  
 <span data-ttu-id="57fef-123">「傳送登入」工作可以設定為傳送所有登入、只傳送指定的登入，或只傳送具有指定之資料庫存取權的所有登入。</span><span class="sxs-lookup"><span data-stu-id="57fef-123">The Transfer Logins task can be configured to transfer all logins, only specified logins, or all logins that have access to specified databases only.</span></span> <span data-ttu-id="57fef-124">無法傳送 sa 登入。</span><span class="sxs-lookup"><span data-stu-id="57fef-124">The sa login cannot be transferred.</span></span> <span data-ttu-id="57fef-125">可能已重新命名 SA 登入，不過，重新命名的 SA 登入仍然無法傳送。</span><span class="sxs-lookup"><span data-stu-id="57fef-125">The sa login may be renamed; however, the renamed sa login cannot be transferred either.</span></span>  
  
 <span data-ttu-id="57fef-126">您還可以指出工作是否複製與登入相關聯的安全性識別碼 (SID)。</span><span class="sxs-lookup"><span data-stu-id="57fef-126">You can also indicate whether the task copies the security identifiers (SIDs) associated with the logins.</span></span> <span data-ttu-id="57fef-127">如果將「傳送登入」工作與「傳送資料庫」工作一起使用，則必須將 SID 複製到目的地，否則，目的地資料庫將無法辨識傳送的登入。</span><span class="sxs-lookup"><span data-stu-id="57fef-127">If the Transfer Logins task is used in conjunction with the Transfer Database task the SIDs must be copied to the destination; otherwise, the transferred logins are not recognized by the destination database.</span></span>  
  
 <span data-ttu-id="57fef-128">在目的地上，會停用傳送的登入，並為其指派隨機密碼。</span><span class="sxs-lookup"><span data-stu-id="57fef-128">At the destination, the transferred logins are disabled and assigned random passwords.</span></span> <span data-ttu-id="57fef-129">目的地伺服器上 sysadmin 角色的成員必須變更密碼，並啟用登入，才可以使用這些登入。</span><span class="sxs-lookup"><span data-stu-id="57fef-129">A member of the sysadmin role on the destination server must change the passwords and enable the logins before the logins can be used.</span></span>  
  
 <span data-ttu-id="57fef-130">要傳送的登入可能已存在於目的地上。</span><span class="sxs-lookup"><span data-stu-id="57fef-130">The logins to be transferred may already exist on the destination.</span></span> <span data-ttu-id="57fef-131">可以設定「傳送登入」工作以下列方式處理現有的登入：</span><span class="sxs-lookup"><span data-stu-id="57fef-131">The Transfer Logins task can be configured to handle existing logins in the following ways:</span></span>  
  
-   <span data-ttu-id="57fef-132">覆寫現有的登入。</span><span class="sxs-lookup"><span data-stu-id="57fef-132">Overwrite existing logins.</span></span>  
  
-   <span data-ttu-id="57fef-133">存在重複的登入時讓工作失敗。</span><span class="sxs-lookup"><span data-stu-id="57fef-133">Fail the task when duplicate logins exist.</span></span>  
  
-   <span data-ttu-id="57fef-134">略過重複的登入。</span><span class="sxs-lookup"><span data-stu-id="57fef-134">Skip duplicate logins.</span></span>  
  
 <span data-ttu-id="57fef-135">在執行階段，「傳送登入」工作會使用兩個 SMO 連接管理員，連接到來源和目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="57fef-135">At run time, the Transfer Logins task connects to the source and destination servers by using two SMO connection managers.</span></span> <span data-ttu-id="57fef-136">SMO 連接管理員會在「傳送登入」工作以外另行設定，然後在「傳送登入」工作中參考。</span><span class="sxs-lookup"><span data-stu-id="57fef-136">The SMO connection managers are configured separately from the Transfer Logins task, and then referenced in the Transfer Logins task.</span></span> <span data-ttu-id="57fef-137">存取伺服器時，SMO 連接管理員會指定要使用的伺服器和驗證模式。</span><span class="sxs-lookup"><span data-stu-id="57fef-137">The SMO connection managers specify the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="57fef-138">如需詳細資訊，請參閱 [SMO Connection Manager](../connection-manager/smo-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="57fef-138">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
 <span data-ttu-id="57fef-139">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="57fef-139">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="57fef-140">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="57fef-140">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="57fef-141">傳送登入工作編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="57fef-141">Transfer Logins Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="57fef-142">傳送登入工作編輯器 &#40;登入頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="57fef-142">Transfer Logins Task Editor &#40;Logins Page&#41;</span></span>](../transfer-logins-task-editor-logins-page.md)  
  
-   [<span data-ttu-id="57fef-143">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="57fef-143">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="57fef-144">如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="57fef-144">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="57fef-145">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="57fef-145">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-transfer-logins-task"></a><span data-ttu-id="57fef-146">以程式設計方式設定傳送登入工作</span><span class="sxs-lookup"><span data-stu-id="57fef-146">Programmatic Configuration of the Transfer Logins Task</span></span>  
 <span data-ttu-id="57fef-147">如需有關以程式設計方式設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="57fef-147">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferLoginsTask.TransferLoginsTask>  
  
  
