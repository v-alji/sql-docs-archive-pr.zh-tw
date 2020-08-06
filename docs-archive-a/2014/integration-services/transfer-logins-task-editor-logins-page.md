---
title: 傳送登入工作編輯器 (登入頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferloginstask.logins.f1
helpviewer_keywords:
- Transfer Logins Task Editor
ms.assetid: bf244c24-bd45-4ece-b66b-78b488f35c5b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b33fea6c78df75b7eebe8987f952dce33bdc4407
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607448"
---
# <a name="transfer-logins-task-editor-logins-page"></a><span data-ttu-id="a4a7a-102">傳送登入工作編輯器 (登入頁面)</span><span class="sxs-lookup"><span data-stu-id="a4a7a-102">Transfer Logins Task Editor (Logins Page)</span></span>
  <span data-ttu-id="a4a7a-103">使用 [傳送登入工作編輯器] 對話方塊的 [登入] 頁面，即可指定屬性將一個或多個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登入，從 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的一個執行個體複製到另一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-103">Use the **Logins** page of the **Transfer Logins Task Editor** dialog box to specify properties for copying one or more [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logins from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another.</span></span> <span data-ttu-id="a4a7a-104">如需這項工作的詳細資訊，請參閱 [傳送登入工作](control-flow/transfer-logins-task.md)。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-104">For more information about this task, see [Transfer Logins Task](control-flow/transfer-logins-task.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a4a7a-105">執行傳送登入工作時，目的地伺服器上會建立具隨機密碼的登入，且會停用這些密碼。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-105">When the Transfer Logins task is executed, logins are created on the destination server with random passwords and the passwords are disabled.</span></span> <span data-ttu-id="a4a7a-106">若要使用這些登入， **系統管理員** 固定伺服器角色的成員就必須變更密碼，然後啟用密碼。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-106">To use these logins, a member of the **sysadmin** fixed server role must change the passwords and then enable them.</span></span> <span data-ttu-id="a4a7a-107">無法傳送 **sa** 登入。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-107">The **sa** login cannot be transferred.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a4a7a-108">選項。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-108">Options</span></span>  
 <span data-ttu-id="a4a7a-109">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="a4a7a-109">**SourceConnection**</span></span>  
 <span data-ttu-id="a4a7a-110">在清單中選取一個 SMO 連線管理員，或按一下 **\<New connection...>** ，以建立新的來源伺服器連線。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-110">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="a4a7a-111">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="a4a7a-111">**DestinationConnection**</span></span>  
 <span data-ttu-id="a4a7a-112">在清單中選取一個 SMO 連線管理員，或按一下 **\<New connection...>** ，以建立新的目的地伺服器連線。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-112">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="a4a7a-113">**LoginsToTransfer**</span><span class="sxs-lookup"><span data-stu-id="a4a7a-113">**LoginsToTransfer**</span></span>  
 <span data-ttu-id="a4a7a-114">選取要從來源複製到目的地伺服器的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-114">Select the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logins to copy from the source to the destination server.</span></span> <span data-ttu-id="a4a7a-115">此屬性具有下表所列的選項：</span><span class="sxs-lookup"><span data-stu-id="a4a7a-115">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="a4a7a-116">值</span><span class="sxs-lookup"><span data-stu-id="a4a7a-116">Value</span></span>|<span data-ttu-id="a4a7a-117">描述</span><span class="sxs-lookup"><span data-stu-id="a4a7a-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4a7a-118">**AllLogins**</span><span class="sxs-lookup"><span data-stu-id="a4a7a-118">**AllLogins**</span></span>|<span data-ttu-id="a4a7a-119">來源伺服器上的所有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登入，都會複製到目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-119">All [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logins on the source server will be copied to the destination server.</span></span>|  
|<span data-ttu-id="a4a7a-120">**SelectedLogins**</span><span class="sxs-lookup"><span data-stu-id="a4a7a-120">**SelectedLogins**</span></span>|<span data-ttu-id="a4a7a-121">只有使用 **LoginsList** 指定的登入，才會複製到目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-121">Only logins specified with **LoginsList** will be copied to the destination server.</span></span>|  
|<span data-ttu-id="a4a7a-122">**AllLoginsFromSelectedDatabases**</span><span class="sxs-lookup"><span data-stu-id="a4a7a-122">**AllLoginsFromSelectedDatabases**</span></span>|<span data-ttu-id="a4a7a-123">使用 **DatabasesList** 指定之資料庫中的所有登入，都會複製到目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-123">All logins from the databases specified with **DatabasesList** will be copied to the destination server.</span></span>|  
  
 <span data-ttu-id="a4a7a-124">**LoginsList**</span><span class="sxs-lookup"><span data-stu-id="a4a7a-124">**LoginsList**</span></span>  
 <span data-ttu-id="a4a7a-125">選取來源伺服器上要複製到目的地伺服器的登入。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-125">Select the logins on the source server to be copied to the destination server.</span></span> <span data-ttu-id="a4a7a-126">唯有針對 [LoginsToTransfer] 選取了 [SelectedLogins] 時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-126">This option is only available when **SelectedLogins** is selected for **LoginsToTransfer**.</span></span>  
  
 <span data-ttu-id="a4a7a-127">**DatabasesList**</span><span class="sxs-lookup"><span data-stu-id="a4a7a-127">**DatabasesList**</span></span>  
 <span data-ttu-id="a4a7a-128">選取來源伺服器上的資料庫，其中包含要複製到目的地伺服器的登入。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-128">Select the databases on the source server that contain logins to be copied to the destination server.</span></span> <span data-ttu-id="a4a7a-129">唯有針對 [LoginsToTransfer] 選取了 [AllLoginsFromSelectedDatabases] 時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-129">This option is only available when **AllLoginsFromSelectedDatabases** is selected for **LoginsToTransfer**.</span></span>  
  
 <span data-ttu-id="a4a7a-130">**IfObjectExists**</span><span class="sxs-lookup"><span data-stu-id="a4a7a-130">**IfObjectExists**</span></span>  
 <span data-ttu-id="a4a7a-131">選取工作應如何處理已經存在於目的地伺服器上，且具有相同名稱的登入。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-131">Select how the task should handle logins of the same name that already exist on the destination server.</span></span>  
  
 <span data-ttu-id="a4a7a-132">此屬性具有下表所列的選項：</span><span class="sxs-lookup"><span data-stu-id="a4a7a-132">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="a4a7a-133">值</span><span class="sxs-lookup"><span data-stu-id="a4a7a-133">Value</span></span>|<span data-ttu-id="a4a7a-134">描述</span><span class="sxs-lookup"><span data-stu-id="a4a7a-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4a7a-135">**FailTask**</span><span class="sxs-lookup"><span data-stu-id="a4a7a-135">**FailTask**</span></span>|<span data-ttu-id="a4a7a-136">如果具有相同名稱的登入已經存在於目的地伺服器上，工作就會失敗。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-136">Task fails if logins of the same name already exist on the destination server.</span></span>|  
|<span data-ttu-id="a4a7a-137">**Overwrite**</span><span class="sxs-lookup"><span data-stu-id="a4a7a-137">**Overwrite**</span></span>|<span data-ttu-id="a4a7a-138">工作會覆寫目的地伺服器上具有相同名稱的登入。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-138">Task overwrites logins of the same name on the destination server.</span></span>|  
|<span data-ttu-id="a4a7a-139">**Skip**</span><span class="sxs-lookup"><span data-stu-id="a4a7a-139">**Skip**</span></span>|<span data-ttu-id="a4a7a-140">工作會略過目的地伺服器上具有相同名稱的登入。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-140">Task skips logins of the same name that exist on the destination server.</span></span>|  
  
 <span data-ttu-id="a4a7a-141">**CopySids**</span><span class="sxs-lookup"><span data-stu-id="a4a7a-141">**CopySids**</span></span>  
 <span data-ttu-id="a4a7a-142">選取與登入相關聯的安全性識別碼，是否應複製到目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-142">Select whether the security identifiers associated with the logins should be copied to the destination server.</span></span> <span data-ttu-id="a4a7a-143">如果「傳送登入」工作是與「傳送資料庫」工作一併使用，[CopySids]  就必須設定為 [True]  。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-143">**CopySids** must be set to **True** if the Transfer Logins task is used along with the Transfer Database task.</span></span> <span data-ttu-id="a4a7a-144">否則，已傳送的資料庫就無法辨識被複製的登入。</span><span class="sxs-lookup"><span data-stu-id="a4a7a-144">Otherwise, the copied logins will not be recognized by the transferred database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a7a-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4a7a-145">See Also</span></span>  
 <span data-ttu-id="a4a7a-146">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a4a7a-146">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="a4a7a-147">[Integration Services 工作](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="a4a7a-147">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="a4a7a-148">[[傳送登入工作編輯器] &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="a4a7a-148">[Transfer Logins Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="a4a7a-149">[運算式頁面](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="a4a7a-149">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="a4a7a-150">[SMO 連線管理員](connection-manager/smo-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="a4a7a-150">[SMO Connection Manager](connection-manager/smo-connection-manager.md) </span></span>  
 <span data-ttu-id="a4a7a-151">[增強式密碼](../relational-databases/security/strong-passwords.md) </span><span class="sxs-lookup"><span data-stu-id="a4a7a-151">[Strong Passwords](../relational-databases/security/strong-passwords.md) </span></span>  
 [<span data-ttu-id="a4a7a-152">SQL Server 安裝的安全性考量</span><span class="sxs-lookup"><span data-stu-id="a4a7a-152">Security Considerations for a SQL Server Installation</span></span>](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
