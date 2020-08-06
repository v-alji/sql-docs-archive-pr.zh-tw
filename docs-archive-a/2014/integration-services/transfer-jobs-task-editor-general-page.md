---
title: '[傳送作業工作編輯器] (一般頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.general.f1
helpviewer_keywords:
- Transfer Jobs Task Editor
ms.assetid: 96531920-92d4-4a3b-a38a-6f0c8bc78ada
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d824c1904b8a3ffd0078f778a78dea898ab53577
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686444"
---
# <a name="transfer-jobs-task-editor-general-page"></a><span data-ttu-id="cb5cf-102">傳送作業工作編輯器 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="cb5cf-102">Transfer Jobs Task Editor (General Page)</span></span>
  <span data-ttu-id="cb5cf-103">使用 **[傳送作業工作編輯器]** 對話方塊的 **[一般]** 頁面，即可命名和描述傳送作業工作。</span><span class="sxs-lookup"><span data-stu-id="cb5cf-103">Use the **General** page of the **Transfer Jobs Task Editor** dialog box to name and describe the Transfer Jobs task.</span></span> <span data-ttu-id="cb5cf-104">如需有關傳送作業工作的詳細資訊，請參閱＜ [Transfer Jobs Task](control-flow/transfer-jobs-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="cb5cf-104">For more information about the Transfer Jobs task, see [Transfer Jobs Task](control-flow/transfer-jobs-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb5cf-105">只有目的地伺服器上的 **系統管理員 (sysadmin)** 固定伺服器角色的成員，或其中一個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 固定資料庫角色的成員，才能在目的地伺服器上成功建立作業。</span><span class="sxs-lookup"><span data-stu-id="cb5cf-105">Only members of the **sysadmin** fixed server role or one of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent fixed database roles on the destination server can successfully create jobs there.</span></span> <span data-ttu-id="cb5cf-106">若要存取來源伺服器上的作業，則在來源伺服器上使用者必須至少是 **SQLAgentUserRole** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="cb5cf-106">To access jobs on the source server, users must be a member of at least the **SQLAgentUserRole** fixed database role there.</span></span> <span data-ttu-id="cb5cf-107">如需 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 固定資料庫角色及其權限的詳細資訊，請參閱 [SQL Server Agent 固定資料庫角色](../ssms/agent/sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="cb5cf-107">For more information about [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent fixed database roles and their permissions, see [SQL Server Agent Fixed Database Roles](../ssms/agent/sql-server-agent-fixed-database-roles.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="cb5cf-108">選項。</span><span class="sxs-lookup"><span data-stu-id="cb5cf-108">Options</span></span>  
 <span data-ttu-id="cb5cf-109">**名稱**</span><span class="sxs-lookup"><span data-stu-id="cb5cf-109">**Name**</span></span>  
 <span data-ttu-id="cb5cf-110">輸入傳送作業工作的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="cb5cf-110">Type a unique name for the Transfer Jobs task.</span></span> <span data-ttu-id="cb5cf-111">這個名稱是作為工作圖示中的標籤使用。</span><span class="sxs-lookup"><span data-stu-id="cb5cf-111">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb5cf-112">工作名稱在封裝內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="cb5cf-112">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="cb5cf-113">**說明**</span><span class="sxs-lookup"><span data-stu-id="cb5cf-113">**Description**</span></span>  
 <span data-ttu-id="cb5cf-114">輸入傳送作業工作的描述。</span><span class="sxs-lookup"><span data-stu-id="cb5cf-114">Type a description of the Transfer Jobs task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb5cf-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb5cf-115">See Also</span></span>  
 <span data-ttu-id="cb5cf-116">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="cb5cf-116">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="cb5cf-117">[Integration Services 工作](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="cb5cf-117">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="cb5cf-118">[傳送作業工作編輯器 &#40;作業頁面&#41;](../../2014/integration-services/transfer-jobs-task-editor-jobs-page.md) </span><span class="sxs-lookup"><span data-stu-id="cb5cf-118">[Transfer Jobs Task Editor &#40;Jobs Page&#41;](../../2014/integration-services/transfer-jobs-task-editor-jobs-page.md) </span></span>  
 [<span data-ttu-id="cb5cf-119">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="cb5cf-119">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
