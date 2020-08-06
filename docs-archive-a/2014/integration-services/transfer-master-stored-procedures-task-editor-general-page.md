---
title: 傳送主要預存程式工作編輯器 (一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.general.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: fa1abd4c-e2be-427f-be53-860e49c97227
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a25a5c9c6ed3802e21ac522e94163ce5fb9e8c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703117"
---
# <a name="transfer-master-stored-procedures-task-editor-general-page"></a><span data-ttu-id="ab5e0-102">傳送主要預存程序工作編輯器 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="ab5e0-102">Transfer Master Stored Procedures Task Editor (General Page)</span></span>
  <span data-ttu-id="ab5e0-103">使用 [傳送主要預存程序工作編輯器] 對話方塊的 [一般] 頁面，即可命名和描述傳送主要預存程序工作。</span><span class="sxs-lookup"><span data-stu-id="ab5e0-103">Use the **General** page of the **Transfer Master Stored Procedures Task Editor** dialog box to name and describe the Transfer Master Stored Procedures task.</span></span> <span data-ttu-id="ab5e0-104">如需這項工作的詳細資訊，請參閱 [傳送主要預存程序工作](control-flow/transfer-master-stored-procedures-task.md)。</span><span class="sxs-lookup"><span data-stu-id="ab5e0-104">For more information about this task, see [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab5e0-105">此工作只會從來源伺服器上的 **master** 資料庫，將 **dbo** 擁有的使用者定義預存程序，傳送到目的地伺服器上的 **master** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ab5e0-105">This task transfers only user-defined stored procedures owned by **dbo** from a **master** database on the source server to a **master** database on the destination server.</span></span> <span data-ttu-id="ab5e0-106">使用者必須有目的地伺服器上之 **master** 資料庫的 CREATE PROCEDURE 權限，或是目的地伺服器上之 **sysadmin** 固定伺服器角色的成員，才能在目的地伺服器建立預存程序。</span><span class="sxs-lookup"><span data-stu-id="ab5e0-106">Users must be granted the CREATE PROCEDURE permission in the **master** database on the destination server or be members of the **sysadmin** fixed server role on the destination server to create stored procedures there.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ab5e0-107">選項。</span><span class="sxs-lookup"><span data-stu-id="ab5e0-107">Options</span></span>  
 <span data-ttu-id="ab5e0-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="ab5e0-108">**Name**</span></span>  
 <span data-ttu-id="ab5e0-109">輸入傳送主要預存程序工作的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="ab5e0-109">Type a unique name for the Transfer Master Stored Procedures task.</span></span> <span data-ttu-id="ab5e0-110">這個名稱是作為工作圖示中的標籤使用。</span><span class="sxs-lookup"><span data-stu-id="ab5e0-110">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab5e0-111">工作名稱在封裝內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="ab5e0-111">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="ab5e0-112">**說明**</span><span class="sxs-lookup"><span data-stu-id="ab5e0-112">**Description**</span></span>  
 <span data-ttu-id="ab5e0-113">輸入傳送主要預存程序工作的描述。</span><span class="sxs-lookup"><span data-stu-id="ab5e0-113">Type a description of the Transfer Master Stored Procedures task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab5e0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab5e0-114">See Also</span></span>  
 <span data-ttu-id="ab5e0-115">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ab5e0-115">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="ab5e0-116">[Integration Services 工作](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="ab5e0-116">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="ab5e0-117">[傳送主要預存程式工作編輯器 &#40;預存程式頁面&#41;](../../2014/integration-services/transfer-master-stored-procedures-task-editor-stored-procedures-page.md) </span><span class="sxs-lookup"><span data-stu-id="ab5e0-117">[Transfer Master Stored Procedures Task Editor &#40;Stored Procedures Page&#41;](../../2014/integration-services/transfer-master-stored-procedures-task-editor-stored-procedures-page.md) </span></span>  
 [<span data-ttu-id="ab5e0-118">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="ab5e0-118">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
