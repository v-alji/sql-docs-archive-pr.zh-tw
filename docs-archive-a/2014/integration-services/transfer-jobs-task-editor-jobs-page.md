---
title: 傳送作業工作編輯器 (作業頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.jobs.f1
helpviewer_keywords:
- Transfer Jobs Task Editor
ms.assetid: e72b1dc7-8cda-4ee6-abb5-d438370f04df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d2d506da6997965e40d66521f7dccb8218e165fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607455"
---
# <a name="transfer-jobs-task-editor-jobs-page"></a><span data-ttu-id="0733b-102">傳送作業工作編輯器 (作業頁面)</span><span class="sxs-lookup"><span data-stu-id="0733b-102">Transfer Jobs Task Editor (Jobs Page)</span></span>
  <span data-ttu-id="0733b-103">使用 [傳送作業工作編輯器] 對話方塊的 [作業] 頁面，即可指定屬性用來將一或多個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 作業，從 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的一個執行個體複製到另一個。</span><span class="sxs-lookup"><span data-stu-id="0733b-103">Use the **Jobs** page of the **Transfer Jobs Task Editor** dialog box to specify properties for copying one or more [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another.</span></span> <span data-ttu-id="0733b-104">如需有關傳送作業工作的詳細資訊，請參閱＜ [Transfer Jobs Task](control-flow/transfer-jobs-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="0733b-104">For more information about the Transfer Jobs task, see [Transfer Jobs Task](control-flow/transfer-jobs-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0733b-105">若要存取來源伺服器上的作業，使用者就必須至少是伺服器上之 **SQLAgentUserRole** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="0733b-105">To access jobs on the source server, users must be a member of at least the **SQLAgentUserRole** fixed database role on the server.</span></span> <span data-ttu-id="0733b-106">若要在目的地伺服器上順利建立作業，使用者就必須是 **sysadmin** 固定伺服器角色的成員，或是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="0733b-106">To successfully create jobs on the destination server, the user must be a member of the **sysadmin** fixed server role or one of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent fixed database roles.</span></span> <span data-ttu-id="0733b-107">如需 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 固定資料庫角色及其權限的詳細資訊，請參閱 [SQL Server Agent 固定資料庫角色](../ssms/agent/sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="0733b-107">For more information about [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent fixed database roles and their permissions, see [SQL Server Agent Fixed Database Roles](../ssms/agent/sql-server-agent-fixed-database-roles.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0733b-108">選項。</span><span class="sxs-lookup"><span data-stu-id="0733b-108">Options</span></span>  
 <span data-ttu-id="0733b-109">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="0733b-109">**SourceConnection**</span></span>  
 <span data-ttu-id="0733b-110">在清單中選取一個 SMO 連線管理員，或按一下 **\<New connection...>** ，以建立新的來源伺服器連線。</span><span class="sxs-lookup"><span data-stu-id="0733b-110">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="0733b-111">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="0733b-111">**DestinationConnection**</span></span>  
 <span data-ttu-id="0733b-112">在清單中選取一個 SMO 連線管理員，或按一下 **\<New connection...>** ，以建立新的目的地伺服器連線。</span><span class="sxs-lookup"><span data-stu-id="0733b-112">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="0733b-113">**TransferAllJobs**</span><span class="sxs-lookup"><span data-stu-id="0733b-113">**TransferAllJobs**</span></span>  
 <span data-ttu-id="0733b-114">選取工作是否應將所有作業或只有指定的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 作業，從來源複製到目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="0733b-114">Select whether the task should copy all or only the specified [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs from the source to the destination server.</span></span>  
  
 <span data-ttu-id="0733b-115">此屬性具有下表所列的選項：</span><span class="sxs-lookup"><span data-stu-id="0733b-115">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="0733b-116">值</span><span class="sxs-lookup"><span data-stu-id="0733b-116">Value</span></span>|<span data-ttu-id="0733b-117">描述</span><span class="sxs-lookup"><span data-stu-id="0733b-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0733b-118">**True**</span><span class="sxs-lookup"><span data-stu-id="0733b-118">**True**</span></span>|<span data-ttu-id="0733b-119">複製所有作業。</span><span class="sxs-lookup"><span data-stu-id="0733b-119">Copy all jobs.</span></span>|  
|<span data-ttu-id="0733b-120">**False**</span><span class="sxs-lookup"><span data-stu-id="0733b-120">**False**</span></span>|<span data-ttu-id="0733b-121">只複製指定的作業。</span><span class="sxs-lookup"><span data-stu-id="0733b-121">Copy only the specified jobs.</span></span>|  
  
 <span data-ttu-id="0733b-122">**JobsList**</span><span class="sxs-lookup"><span data-stu-id="0733b-122">**JobsList**</span></span>  
 <span data-ttu-id="0733b-123">按一下瀏覽按鈕 **(...)** 來選取要複製的作業。</span><span class="sxs-lookup"><span data-stu-id="0733b-123">Click the browse button **(...)** to select the jobs to copy.</span></span> <span data-ttu-id="0733b-124">必須至少選取一個作業。</span><span class="sxs-lookup"><span data-stu-id="0733b-124">At least one job must be selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0733b-125">選取要複製的作業之前，請指定 **SourceConnection** 。</span><span class="sxs-lookup"><span data-stu-id="0733b-125">Specify the **SourceConnection** before selecting jobs to copy.</span></span>  
  
 <span data-ttu-id="0733b-126">當 **TransferAllJobs** 設定為 **True** 時，無法使用 **JobsList**選項。</span><span class="sxs-lookup"><span data-stu-id="0733b-126">The **JobsList** option is unavailable when **TransferAllJobs** is set to **True**.</span></span>  
  
 <span data-ttu-id="0733b-127">**IfObjectExists**</span><span class="sxs-lookup"><span data-stu-id="0733b-127">**IfObjectExists**</span></span>  
 <span data-ttu-id="0733b-128">選取工作應如何處理已經存在於目的地伺服器上，且具有相同名稱的作業。</span><span class="sxs-lookup"><span data-stu-id="0733b-128">Select how the task should handle jobs of the same name that already exist on the destination server.</span></span>  
  
 <span data-ttu-id="0733b-129">此屬性具有下表所列的選項：</span><span class="sxs-lookup"><span data-stu-id="0733b-129">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="0733b-130">值</span><span class="sxs-lookup"><span data-stu-id="0733b-130">Value</span></span>|<span data-ttu-id="0733b-131">描述</span><span class="sxs-lookup"><span data-stu-id="0733b-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0733b-132">**FailTask**</span><span class="sxs-lookup"><span data-stu-id="0733b-132">**FailTask**</span></span>|<span data-ttu-id="0733b-133">如果具有相同名稱的作業己經存在於目的地伺服器上，工作就會失敗。</span><span class="sxs-lookup"><span data-stu-id="0733b-133">Task fails if jobs of the same name already exist on the destination server.</span></span>|  
|<span data-ttu-id="0733b-134">**Overwrite**</span><span class="sxs-lookup"><span data-stu-id="0733b-134">**Overwrite**</span></span>|<span data-ttu-id="0733b-135">工作會覆寫目的地伺服器上具有相同名稱的作業。</span><span class="sxs-lookup"><span data-stu-id="0733b-135">Task overwrites jobs of the same name on the destination server.</span></span>|  
|<span data-ttu-id="0733b-136">**Skip**</span><span class="sxs-lookup"><span data-stu-id="0733b-136">**Skip**</span></span>|<span data-ttu-id="0733b-137">工作會略過存在於目的地伺服器上具有相同名稱的作業。</span><span class="sxs-lookup"><span data-stu-id="0733b-137">Task skips jobs of the same name that exist on the destination server.</span></span>|  
  
 <span data-ttu-id="0733b-138">**EnableJobsAtDestination**</span><span class="sxs-lookup"><span data-stu-id="0733b-138">**EnableJobsAtDestination**</span></span>  
 <span data-ttu-id="0733b-139">選取是否應啟用已複製到目的地伺服器的作業。</span><span class="sxs-lookup"><span data-stu-id="0733b-139">Select whether the jobs copied to the destination server should be enabled.</span></span>  
  
 <span data-ttu-id="0733b-140">此屬性具有下表所列的選項：</span><span class="sxs-lookup"><span data-stu-id="0733b-140">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="0733b-141">值</span><span class="sxs-lookup"><span data-stu-id="0733b-141">Value</span></span>|<span data-ttu-id="0733b-142">描述</span><span class="sxs-lookup"><span data-stu-id="0733b-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0733b-143">**True**</span><span class="sxs-lookup"><span data-stu-id="0733b-143">**True**</span></span>|<span data-ttu-id="0733b-144">啟用目的地伺服器上的作業。</span><span class="sxs-lookup"><span data-stu-id="0733b-144">Enable jobs on destination server.</span></span>|  
|<span data-ttu-id="0733b-145">**False**</span><span class="sxs-lookup"><span data-stu-id="0733b-145">**False**</span></span>|<span data-ttu-id="0733b-146">停用目的地伺服器上的作業。</span><span class="sxs-lookup"><span data-stu-id="0733b-146">Disable jobs on destination server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0733b-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0733b-147">See Also</span></span>  
 <span data-ttu-id="0733b-148">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0733b-148">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="0733b-149">[Integration Services 工作](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="0733b-149">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="0733b-150">[[傳送作業工作編輯器] &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="0733b-150">[Transfer Jobs Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="0733b-151">[運算式頁面](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="0733b-151">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="0733b-152">SMO 連線管理員</span><span class="sxs-lookup"><span data-stu-id="0733b-152">SMO Connection Manager</span></span>](connection-manager/smo-connection-manager.md)  
  
  
