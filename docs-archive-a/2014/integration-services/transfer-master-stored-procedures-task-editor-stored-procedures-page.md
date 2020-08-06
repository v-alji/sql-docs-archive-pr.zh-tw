---
title: 傳送主要預存程式工作編輯器 (預存程式頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.storedprocedures.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: 5fcf171e-cc0b-4c24-8eb5-3a4b4775e64a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5f9fad408b54d4ef27d4c5d06b0d352f366ad9c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703113"
---
# <a name="transfer-master-stored-procedures-task-editor-stored-procedures-page"></a><span data-ttu-id="cf0a1-102">傳送主要預存程序工作編輯器 (預存程序頁面)</span><span class="sxs-lookup"><span data-stu-id="cf0a1-102">Transfer Master Stored Procedures Task Editor (Stored Procedures Page)</span></span>
  <span data-ttu-id="cf0a1-103">使用 [傳送主要預存程序工作編輯器] 對話方塊的 [預存程序] 頁面，即可指定屬性，以將一個或多個使用者定義預存程序從 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體之某個執行個體的 **master** 資料庫，複製到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 之另一個執行個體的 **master** 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="cf0a1-103">Use the **Stored Procedures** page of the **Transfer Master Stored Procedures Task Editor** dialog box to specify properties for copying one or more user-defined stored procedures from the **master** database in one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance to a **master** database in another instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cf0a1-104">如需這項工作的詳細資訊，請參閱 [傳送主要預存程序工作](control-flow/transfer-master-stored-procedures-task.md)。</span><span class="sxs-lookup"><span data-stu-id="cf0a1-104">For more information about this task, see [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cf0a1-105">此工作只會從來源伺服器上的 **master** 資料庫，將 **dbo** 擁有的使用者定義預存程序，傳送到目的地伺服器上的 **master** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="cf0a1-105">This task transfers only user-defined stored procedures owned by **dbo** from a **master** database on the source server to a **master** database on the destination server.</span></span> <span data-ttu-id="cf0a1-106">使用者必須有目的地伺服器上之 **master** 資料庫的 CREATE PROCEDURE 權限，或是目的地伺服器上之 **sysadmin** 固定伺服器角色的成員，才能在目的地伺服器建立預存程序。</span><span class="sxs-lookup"><span data-stu-id="cf0a1-106">Users must be granted the CREATE PROCEDURE permission in the **master** database on the destination server or be members of the **sysadmin** fixed server role on the destination server to create stored procedures there.</span></span>  
  
## <a name="options"></a><span data-ttu-id="cf0a1-107">選項。</span><span class="sxs-lookup"><span data-stu-id="cf0a1-107">Options</span></span>  
 <span data-ttu-id="cf0a1-108">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="cf0a1-108">**SourceConnection**</span></span>  
 <span data-ttu-id="cf0a1-109">在清單中選取一個 SMO 連線管理員，或按一下 **\<New connection...>** ，以建立新的來源伺服器連線。</span><span class="sxs-lookup"><span data-stu-id="cf0a1-109">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="cf0a1-110">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="cf0a1-110">**DestinationConnection**</span></span>  
 <span data-ttu-id="cf0a1-111">在清單中選取一個 SMO 連線管理員，或按一下 **\<New connection...>** ，以建立新的目的地伺服器連線。</span><span class="sxs-lookup"><span data-stu-id="cf0a1-111">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="cf0a1-112">**IfObjectExists**</span><span class="sxs-lookup"><span data-stu-id="cf0a1-112">**IfObjectExists**</span></span>  
 <span data-ttu-id="cf0a1-113">選取工作應如何處理在目的地伺服器上的 **master** 資料庫中已經存在有相同名稱的使用者定義預存程序。</span><span class="sxs-lookup"><span data-stu-id="cf0a1-113">Select how the task should handle user-defined stored procedures of the same name that already exist in the **master** database on the destination server.</span></span>  
  
 <span data-ttu-id="cf0a1-114">此屬性具有下表所列的選項：</span><span class="sxs-lookup"><span data-stu-id="cf0a1-114">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="cf0a1-115">值</span><span class="sxs-lookup"><span data-stu-id="cf0a1-115">Value</span></span>|<span data-ttu-id="cf0a1-116">描述</span><span class="sxs-lookup"><span data-stu-id="cf0a1-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cf0a1-117">**FailTask**</span><span class="sxs-lookup"><span data-stu-id="cf0a1-117">**FailTask**</span></span>|<span data-ttu-id="cf0a1-118">如果目的地伺服器上的 **master** 資料庫中已經存在有相同名稱的預存程序，則工作失敗。</span><span class="sxs-lookup"><span data-stu-id="cf0a1-118">Task fails if stored procedures of the same name already exist in the **master** database on the destination server.</span></span>|  
|<span data-ttu-id="cf0a1-119">**Overwrite**</span><span class="sxs-lookup"><span data-stu-id="cf0a1-119">**Overwrite**</span></span>|<span data-ttu-id="cf0a1-120">工作會覆寫目的地伺服器上的 **master** 資料庫中有相同名稱的預存程序。</span><span class="sxs-lookup"><span data-stu-id="cf0a1-120">Task overwrites stored procedures of the same name in the **master** database on the destination server.</span></span>|  
|<span data-ttu-id="cf0a1-121">**Skip**</span><span class="sxs-lookup"><span data-stu-id="cf0a1-121">**Skip**</span></span>|<span data-ttu-id="cf0a1-122">工作會略過目的地伺服器上的 **master** 資料庫中存在有相同名稱的預存程序。</span><span class="sxs-lookup"><span data-stu-id="cf0a1-122">Task skips stored procedures of the same name that exist in the **master** database on the destination server.</span></span>|  
  
 <span data-ttu-id="cf0a1-123">**TransferAllStoredProcedures**</span><span class="sxs-lookup"><span data-stu-id="cf0a1-123">**TransferAllStoredProcedures**</span></span>  
 <span data-ttu-id="cf0a1-124">選取是否應將來源伺服器上之 **master** 資料庫中的所有使用者定義預存程序，複製到目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="cf0a1-124">Select whether all user-defined stored procedures in the **master** database on the source server should be copied to the destination server.</span></span>  
  
|<span data-ttu-id="cf0a1-125">值</span><span class="sxs-lookup"><span data-stu-id="cf0a1-125">Value</span></span>|<span data-ttu-id="cf0a1-126">描述</span><span class="sxs-lookup"><span data-stu-id="cf0a1-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cf0a1-127">**True**</span><span class="sxs-lookup"><span data-stu-id="cf0a1-127">**True**</span></span>|<span data-ttu-id="cf0a1-128">複製 **master** 資料庫中的所有使用者定義預存程序。</span><span class="sxs-lookup"><span data-stu-id="cf0a1-128">Copy all user-defined stored procedures in the **master** database.</span></span>|  
|<span data-ttu-id="cf0a1-129">**False**</span><span class="sxs-lookup"><span data-stu-id="cf0a1-129">**False**</span></span>|<span data-ttu-id="cf0a1-130">只複製指定的預存程序。</span><span class="sxs-lookup"><span data-stu-id="cf0a1-130">Copy only the specified stored procedures.</span></span>|  
  
 <span data-ttu-id="cf0a1-131">**StoredProceduresList**</span><span class="sxs-lookup"><span data-stu-id="cf0a1-131">**StoredProceduresList**</span></span>  
 <span data-ttu-id="cf0a1-132">選取應將來源伺服器上之 **master** 資料庫中的哪些使用者定義預存程序，複製到目的地 **master** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="cf0a1-132">Select which user-defined stored procedures in the **master** database on the source server should be copied to the destination **master** database.</span></span> <span data-ttu-id="cf0a1-133">只有 [TransferAllStoredProcedures]  設定為 [False]  時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="cf0a1-133">This option is only available when **TransferAllStoredProcedures** is set to **False**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf0a1-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf0a1-134">See Also</span></span>  
 <span data-ttu-id="cf0a1-135">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="cf0a1-135">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="cf0a1-136">[Integration Services 工作](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="cf0a1-136">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="cf0a1-137">[傳送主要預存程式工作編輯器 &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="cf0a1-137">[Transfer Master Stored Procedures Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="cf0a1-138">[運算式頁面](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="cf0a1-138">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="cf0a1-139">SMO 連線管理員</span><span class="sxs-lookup"><span data-stu-id="cf0a1-139">SMO Connection Manager</span></span>](connection-manager/smo-connection-manager.md)  
  
  
