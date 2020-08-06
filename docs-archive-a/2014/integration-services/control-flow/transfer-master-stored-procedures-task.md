---
title: 傳送主要預存程序工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfermasterspstask.f1
helpviewer_keywords:
- Transfer Master Stored Procedures task [Integration Services]
ms.assetid: 81702560-48a3-46d1-a469-e41304c7af8e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1915a3129eeb6e14c4315c37f2c6c2bf5b0d5412
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708521"
---
# <a name="transfer-master-stored-procedures-task"></a><span data-ttu-id="d0e8f-102">傳送主要預存程序工作</span><span class="sxs-lookup"><span data-stu-id="d0e8f-102">Transfer Master Stored Procedures Task</span></span>
  <span data-ttu-id="d0e8f-103">「傳送主要預存程序」工作會在 **執行個體上的** master [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料庫之間，傳送一個或多個使用者自訂預存程序。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-103">The Transfer Master Stored Procedures task transfers one or more user-defined stored procedures between **master** databases on instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d0e8f-104">若要從 **master** 資料庫傳送預存程序，程序的擁有者必須為 dbo。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-104">To transfer a stored procedure from the **master** database, the owner of the procedure must be dbo.</span></span>  
  
 <span data-ttu-id="d0e8f-105">可以設定「傳送主要預存程序」工作傳送所有的預存程序，或只傳送指定的預存程序。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-105">The Transfer Master Stored Procedures task can be configured to transfer all stored procedures or only specified stored procedures.</span></span> <span data-ttu-id="d0e8f-106">此工作不會複製系統預存程序。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-106">This task does not copy system stored procedures.</span></span>  
  
 <span data-ttu-id="d0e8f-107">目的地可能已存在要傳送的主要預存程序。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-107">The master stored procedures to be transferred may already exist on the destination.</span></span> <span data-ttu-id="d0e8f-108">可以設定「傳送主要預存程序」工作以下列方式處理現有的預存程序：</span><span class="sxs-lookup"><span data-stu-id="d0e8f-108">The Transfer Master Stored Procedures task can be configured to handle existing stored procedures in the following ways:</span></span>  
  
-   <span data-ttu-id="d0e8f-109">覆寫現有預存程序。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-109">Overwrite existing stored procedures.</span></span>  
  
-   <span data-ttu-id="d0e8f-110">存在重複的預存程序時讓工作失敗。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-110">Fail the task when duplicate stored procedures exist.</span></span>  
  
-   <span data-ttu-id="d0e8f-111">略過重複的預存程序。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-111">Skip duplicate stored procedures.</span></span>  
  
 <span data-ttu-id="d0e8f-112">在執行階段，「傳送主要預存程序」工作會使用兩個 SMO 連接管理員，連接到來源和目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-112">At run time, the Transfer Master Stored Procedures task connects to the source and destination servers by using two SMO connection managers.</span></span> <span data-ttu-id="d0e8f-113">SMO 連結管理員會在「傳送主要預存程序」工作以外另行設定，然後在「傳送主要預存程序」工作中參考。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-113">The SMO connection managers are configured separately from the Transfer Master Stored Procedures task, and then referenced in the Transfer Master Stored Procedures task.</span></span> <span data-ttu-id="d0e8f-114">存取伺服器時，SMO 連接管理員會指定要使用的伺服器和驗證模式。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-114">The SMO connection managers specify the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="d0e8f-115">如需詳細資訊，請參閱 [SMO Connection Manager](../connection-manager/smo-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-115">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
## <a name="transferring-stored-procedures-between-instances-of-sql-server"></a><span data-ttu-id="d0e8f-116">在 SQL Server 的執行個體之間傳送預存程序</span><span class="sxs-lookup"><span data-stu-id="d0e8f-116">Transferring Stored Procedures Between Instances of SQL Server</span></span>  
 <span data-ttu-id="d0e8f-117">「傳送主要預存程序」工作可支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 來源及目的地。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-117">The Transfer Master Stored Procedures task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="d0e8f-118">事件</span><span class="sxs-lookup"><span data-stu-id="d0e8f-118">Events</span></span>  
 <span data-ttu-id="d0e8f-119">該工作會引發報告已傳送預存程序數目的資訊事件，並在覆寫預存程序時引發警告事件。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-119">The task raises an information event that reports the number of stored procedures transferred and a warning event when a stored procedure is overwritten.</span></span>  
  
 <span data-ttu-id="d0e8f-120">「傳送主要預存程序」工作並不報告登入傳送的累加進度，它只報告 0% 和 100 % 完成。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-120">The Transfer Master Stored Procedures task does not report incremental progress of the login transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="d0e8f-121">執行值</span><span class="sxs-lookup"><span data-stu-id="d0e8f-121">Execution Value</span></span>  
 <span data-ttu-id="d0e8f-122">工作之 `ExecutionValue` 屬性中定義的執行值會傳回已傳送的預存程序數。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-122">The execution value, defined in the `ExecutionValue` property of the task, returns the number of stored procedures transferred.</span></span> <span data-ttu-id="d0e8f-123">透過將使用者自訂變數指派給「傳送主要預存程序」工作的 `ExecValueVariable` 屬性，可將與預存程序傳送相關的資訊用於封裝中的其他物件。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-123">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Master Stored Procedures task, information about the stored procedure transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="d0e8f-124">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md)和[在封裝中使用變數](../use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-124">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="d0e8f-125">記錄項目</span><span class="sxs-lookup"><span data-stu-id="d0e8f-125">Log Entries</span></span>  
 <span data-ttu-id="d0e8f-126">「傳送主要預存程序」工作包含下列自訂記錄項目：</span><span class="sxs-lookup"><span data-stu-id="d0e8f-126">The Transfer Master Stored Procedures task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="d0e8f-127">TransferStoredProceduresTaskStartTransferringObjects  此記錄項目報告傳送已開始。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-127">TransferStoredProceduresTaskStartTransferringObjects  This log entry reports that the transfer has started.</span></span> <span data-ttu-id="d0e8f-128">記錄項目會包含開始時間。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-128">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="d0e8f-129">TransferSStoredProceduresTaskFinishedTransferringObjects  此記錄項目報告傳送已完成。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-129">TransferSStoredProceduresTaskFinishedTransferringObjects  This log entry reports that the transfer has finished.</span></span> <span data-ttu-id="d0e8f-130">記錄項目會包含結束時間。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-130">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="d0e8f-131">此外，`OnInformation` 事件的記錄項目會報告已傳送的預存程序數目，並會為在目的地上覆寫的每個預存程序，寫入 `OnWarning` 事件的記錄項目。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-131">In addition, a log entry for the `OnInformation` event reports the number of stored procedures that were transferred, and a log entry for the `OnWarning` event is written for each stored procedure on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="d0e8f-132">安全性和權限</span><span class="sxs-lookup"><span data-stu-id="d0e8f-132">Security and Permissions</span></span>  
 <span data-ttu-id="d0e8f-133">使用者必須具有來源上 **master** 資料庫中預存程序清單的檢視權限，且必須是系統管理員 (sysadmin) 伺服器角色的成員，或者具有目的地伺服器上 **master** 資料庫中已建立之預存程序的權限。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-133">The user must have permission to view the list of stored procedure in the **master** database on the source, and must be a member of the sysadmin server role or have permission to created stored procedures in the **master** database on the destination server.</span></span>  
  
## <a name="configuration-of-the-transfer-master-stored-procedures-task"></a><span data-ttu-id="d0e8f-134">設定傳送主要預存程序工作</span><span class="sxs-lookup"><span data-stu-id="d0e8f-134">Configuration of the Transfer Master Stored Procedures Task</span></span>  
 <span data-ttu-id="d0e8f-135">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="d0e8f-135">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="d0e8f-136">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="d0e8f-136">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d0e8f-137">傳送主要預存程序工作編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="d0e8f-137">Transfer Master Stored Procedures Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="d0e8f-138">傳送主要預存程序工作編輯器 &#40;預存程序頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="d0e8f-138">Transfer Master Stored Procedures Task Editor &#40;Stored Procedures Page&#41;</span></span>](../transfer-master-stored-procedures-task-editor-stored-procedures-page.md)  
  
-   [<span data-ttu-id="d0e8f-139">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="d0e8f-139">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="d0e8f-140">如需有關如何以程式設計方式設定這些屬性的詳細資訊，請按以下主題：</span><span class="sxs-lookup"><span data-stu-id="d0e8f-140">For information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferStoredProceduresTask.TransferStoredProceduresTask>  
  
### <a name="configuring-the-transfer-master-stored-procedures-task-programmatically"></a><span data-ttu-id="d0e8f-141">以程式設計方式設定傳送主要預存程序工作</span><span class="sxs-lookup"><span data-stu-id="d0e8f-141">Configuring the Transfer Master Stored Procedures Task Programmatically</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="d0e8f-142">相關工作</span><span class="sxs-lookup"><span data-stu-id="d0e8f-142">Related Tasks</span></span>  
 <span data-ttu-id="d0e8f-143">如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="d0e8f-143">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="d0e8f-144">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="d0e8f-144">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="d0e8f-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0e8f-145">See Also</span></span>  
 <span data-ttu-id="d0e8f-146">[傳送 SQL Server 物件工作](transfer-sql-server-objects-task.md) </span><span class="sxs-lookup"><span data-stu-id="d0e8f-146">[Transfer SQL Server Objects Task](transfer-sql-server-objects-task.md) </span></span>  
 <span data-ttu-id="d0e8f-147">[Integration Services 工作](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="d0e8f-147">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="d0e8f-148">控制流程</span><span class="sxs-lookup"><span data-stu-id="d0e8f-148">Control Flow</span></span>](control-flow.md)  
  
  
