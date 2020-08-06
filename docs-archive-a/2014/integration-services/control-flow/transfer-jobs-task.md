---
title: 傳送作業工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.f1
helpviewer_keywords:
- Transfer Jobs task [Integration Services]
ms.assetid: 1bf33885-9c5b-47e4-a549-f5920b66a1de
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d692934d5f7c8c1449b123ee8b9caf1d8bb34744
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584664"
---
# <a name="transfer-jobs-task"></a><span data-ttu-id="5cbdb-102">傳送作業工作</span><span class="sxs-lookup"><span data-stu-id="5cbdb-102">Transfer Jobs Task</span></span>
  <span data-ttu-id="5cbdb-103">「傳送作業」工作會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體之間，傳送一個或多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-103">The Transfer Jobs task transfers one or more [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5cbdb-104">「傳送作業」工作可以設定為傳送所有作業，或只傳送指定的作業。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-104">The Transfer Jobs task can be configured to transfer all jobs, or only specified jobs.</span></span> <span data-ttu-id="5cbdb-105">您還可以指出是否在目的地啟用已傳送的作業。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-105">You can also indicate whether the transferred jobs are enabled at the destination.</span></span>  
  
 <span data-ttu-id="5cbdb-106">要傳送的作業可能已存在於目的地上。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-106">The jobs to be transferred may already exist on the destination.</span></span> <span data-ttu-id="5cbdb-107">可以設定「傳送作業」工作以下列方式處理現有的作業：</span><span class="sxs-lookup"><span data-stu-id="5cbdb-107">The Transfer Jobs task can be configured to handle existing jobs in the following ways:</span></span>  
  
-   <span data-ttu-id="5cbdb-108">覆寫現有的作業。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-108">Overwrite existing jobs.</span></span>  
  
-   <span data-ttu-id="5cbdb-109">存在重複的作業時讓工作失敗。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-109">Fail the task when duplicate jobs exist.</span></span>  
  
-   <span data-ttu-id="5cbdb-110">略過重複的作業。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-110">Skip duplicate jobs.</span></span>  
  
 <span data-ttu-id="5cbdb-111">在執行階段，「傳送作業」工作會使用一或兩個 SMO 連接管理員，連接到來源和目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-111">At run time, the Transfer Jobs task connects to the source and destination servers by using one or two SMO connection managers.</span></span> <span data-ttu-id="5cbdb-112">SMO 連接管理員會在「傳送作業」工作以外另行設定，然後在「傳送作業」工作中參考。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-112">The SMO connection manager is configured separately from the Transfer Jobs task, and then is referenced in the Transfer Jobs task.</span></span> <span data-ttu-id="5cbdb-113">存取伺服器時，SMO 連接管理員會指定要使用的伺服器和驗證模式。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-113">The SMO connection manager specifies the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="5cbdb-114">如需詳細資訊，請參閱 [SMO Connection Manager](../connection-manager/smo-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-114">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
## <a name="transferring-jobs-between-instances-of-sql-server"></a><span data-ttu-id="5cbdb-115">在 SQL Server 的執行個體之間傳送作業</span><span class="sxs-lookup"><span data-stu-id="5cbdb-115">Transferring Jobs Between Instances of SQL Server</span></span>  
 <span data-ttu-id="5cbdb-116">「傳送作業」工作支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 來源和目的地。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-116">The Transfer Jobs task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span> <span data-ttu-id="5cbdb-117">將哪一個用作來源或目的地是沒有限制的。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-117">There are no restrictions on which version to use as a source or destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="5cbdb-118">事件</span><span class="sxs-lookup"><span data-stu-id="5cbdb-118">Events</span></span>  
 <span data-ttu-id="5cbdb-119">「傳送作業」工作會引發報告已傳送作業數目的資訊事件，並在覆寫作業時引發警告事件。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-119">The Transfer Jobs task raises an information event that reports the number of jobs transferred and a warning event when a job is overwritten.</span></span> <span data-ttu-id="5cbdb-120">該工作並不報告作業傳送的累加進度，它只報告 0% 和 100% 完成。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-120">The task does not report incremental progress of the job transfer; it reports only 0% and 100% completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="5cbdb-121">執行值</span><span class="sxs-lookup"><span data-stu-id="5cbdb-121">Execution Value</span></span>  
 <span data-ttu-id="5cbdb-122">工作之 `ExecutionValue` 屬性中定義的執行值會傳回已傳送的作業數目。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-122">The execution value, defined in the `ExecutionValue` property of the task, returns the number of jobs that are transferred.</span></span> <span data-ttu-id="5cbdb-123">透過將使用者自訂變數指派給「傳送作業」工作的 `ExecValueVariable` 屬性，可將與作業傳送相關的資訊用於封裝中的其他物件。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-123">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Jobs task, information about the job transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="5cbdb-124">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md)和[在封裝中使用變數](../use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-124">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="5cbdb-125">記錄項目</span><span class="sxs-lookup"><span data-stu-id="5cbdb-125">Log Entries</span></span>  
 <span data-ttu-id="5cbdb-126">「傳送作業」工作包含下列自訂記錄項目：</span><span class="sxs-lookup"><span data-stu-id="5cbdb-126">The Transfer Jobs task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="5cbdb-127">TransferJobsTaskStarTransferringObjects   此記錄項目報告傳送已開始。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-127">TransferJobsTaskStarTransferringObjects   This log entry reports that the transfer has started.</span></span> <span data-ttu-id="5cbdb-128">記錄項目會包含開始時間。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-128">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="5cbdb-129">TransferJobsTaskFinishedTransferringObjects   此記錄項目報告傳送已完成。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-129">TransferJobsTaskFinishedTransferringObjects    This log entry reports that the transfer has finished.</span></span> <span data-ttu-id="5cbdb-130">記錄項目會包含結束時間。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-130">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="5cbdb-131">此外，`OnInformation` 事件的記錄項目會報告已傳送的作業數目，並會為在目的地上覆寫的每個作業，寫入 `OnWarning` 事件的記錄項目。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-131">In addition, a log entry for the `OnInformation` event reports the number of jobs that were transferred and a log entry for the `OnWarning` event is written for each job on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="5cbdb-132">安全性和權限</span><span class="sxs-lookup"><span data-stu-id="5cbdb-132">Security and Permissions</span></span>  
 <span data-ttu-id="5cbdb-133">若要傳送作業，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的來源和目的地執行個體上，使用者都必須是系統管理員 (sysadmin) 固定伺服器角色的成員，或者是 msdb 資料庫上固定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent 固定資料庫角色的其中一個成員。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-133">To transfer jobs, the user must be a member of the sysadmin fixed server role or one of the fixed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles on the msdb database on the both the source and destination instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="configuration-of-the-transfer-jobs-task"></a><span data-ttu-id="5cbdb-134">設定傳送作業工作</span><span class="sxs-lookup"><span data-stu-id="5cbdb-134">Configuration of the Transfer Jobs Task</span></span>  
 <span data-ttu-id="5cbdb-135">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="5cbdb-135">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="5cbdb-136">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="5cbdb-136">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="5cbdb-137">傳送作業工作編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="5cbdb-137">Transfer Jobs Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="5cbdb-138">傳送作業工作編輯器 &#40;作業頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="5cbdb-138">Transfer Jobs Task Editor &#40;Jobs Page&#41;</span></span>](../transfer-jobs-task-editor-jobs-page.md)  
  
-   [<span data-ttu-id="5cbdb-139">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="5cbdb-139">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="5cbdb-140">如需有關以程式設計方式設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="5cbdb-140">For information about programmatically setting these properties, click the of the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferJobsTask.TransferJobsTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="5cbdb-141">相關工作</span><span class="sxs-lookup"><span data-stu-id="5cbdb-141">Related Tasks</span></span>  
 <span data-ttu-id="5cbdb-142">如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="5cbdb-142">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="5cbdb-143">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="5cbdb-143">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="5cbdb-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cbdb-144">See Also</span></span>  
 <span data-ttu-id="5cbdb-145">[Integration Services 工作](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="5cbdb-145">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="5cbdb-146">控制流程</span><span class="sxs-lookup"><span data-stu-id="5cbdb-146">Control Flow</span></span>](control-flow.md)  
  
  
