---
title: 傳送錯誤訊息工作編輯器 (訊息頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.errormessages.F1
helpviewer_keywords:
- Transfer Error Messages Task Editor
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a0d626f01e05a30777810b26880da5aedc3e7ad3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607456"
---
# <a name="transfer-error-messages-task-editor-messages-page"></a><span data-ttu-id="705be-102">傳送錯誤訊息工作編輯器 (訊息頁面)</span><span class="sxs-lookup"><span data-stu-id="705be-102">Transfer Error Messages Task Editor (Messages Page)</span></span>
  <span data-ttu-id="705be-103">使用 [傳送錯誤訊息工作編輯器] 對話方塊的 [訊息] 頁面，即可指定屬性用來將一或多個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 使用者自訂錯誤訊息，從 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的一個執行個體複製到另一個。</span><span class="sxs-lookup"><span data-stu-id="705be-103">Use the **Messages** page of the **Transfer Error Messages Task Editor** dialog box to specify properties for copying one or more [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] user-defined error messages from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another.</span></span> <span data-ttu-id="705be-104">如需這項工作的詳細資訊，請參閱 [傳送錯誤訊息工作](control-flow/transfer-error-messages-task.md)。</span><span class="sxs-lookup"><span data-stu-id="705be-104">For more information about this task, see [Transfer Error Messages Task](control-flow/transfer-error-messages-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="705be-105">選項。</span><span class="sxs-lookup"><span data-stu-id="705be-105">Options</span></span>  
 <span data-ttu-id="705be-106">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="705be-106">**SourceConnection**</span></span>  
 <span data-ttu-id="705be-107">在清單中選取一個 SMO 連線管理員，或按一下 **\<New connection...>** ，以建立新的來源伺服器連線。</span><span class="sxs-lookup"><span data-stu-id="705be-107">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="705be-108">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="705be-108">**DestinationConnection**</span></span>  
 <span data-ttu-id="705be-109">在清單中選取一個 SMO 連線管理員，或按一下 **\<New connection...>** ，以建立新的目的地伺服器連線。</span><span class="sxs-lookup"><span data-stu-id="705be-109">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="705be-110">**IfObjectExists**</span><span class="sxs-lookup"><span data-stu-id="705be-110">**IfObjectExists**</span></span>  
 <span data-ttu-id="705be-111">如果有相同名稱的錯誤訊息已存在於目的地伺服器上，選取工作應覆寫現有使用者自訂錯誤訊息、略過現有訊息，或是失敗。</span><span class="sxs-lookup"><span data-stu-id="705be-111">Select whether the task should overwrite existing user-defined error messages, skip existing messages, or fail if error messages of the same name already exist on the destination server.</span></span>  
  
 <span data-ttu-id="705be-112">**TransferAllErrorMessages**</span><span class="sxs-lookup"><span data-stu-id="705be-112">**TransferAllErrorMessages**</span></span>  
 <span data-ttu-id="705be-113">選取工作應將所有的訊息或只有指定的使用者自訂訊息，從來源伺服器複製到目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="705be-113">Select whether the task should copy all or only the specified user-defined messages from the source server to the destination server.</span></span>  
  
 <span data-ttu-id="705be-114">此屬性具有下表所列的選項：</span><span class="sxs-lookup"><span data-stu-id="705be-114">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="705be-115">值</span><span class="sxs-lookup"><span data-stu-id="705be-115">Value</span></span>|<span data-ttu-id="705be-116">描述</span><span class="sxs-lookup"><span data-stu-id="705be-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="705be-117">**True**</span><span class="sxs-lookup"><span data-stu-id="705be-117">**True**</span></span>|<span data-ttu-id="705be-118">複製所有的使用者自訂訊息。</span><span class="sxs-lookup"><span data-stu-id="705be-118">Copy all user-defined messages.</span></span>|  
|<span data-ttu-id="705be-119">**False**</span><span class="sxs-lookup"><span data-stu-id="705be-119">**False**</span></span>|<span data-ttu-id="705be-120">只複製指定的使用者自訂訊息。</span><span class="sxs-lookup"><span data-stu-id="705be-120">Copy only the specified user-defined messages.</span></span>|  
  
 <span data-ttu-id="705be-121">**ErrorMessagesList**</span><span class="sxs-lookup"><span data-stu-id="705be-121">**ErrorMessagesList**</span></span>  
 <span data-ttu-id="705be-122">按一下瀏覽按鈕 **(...)** 來選取要複製的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="705be-122">Click the browse button **(...)** to select the error messages to copy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="705be-123">您必須先指定 [SourceConnection]  ，才能選取要複製的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="705be-123">You must specify the **SourceConnection** before you can select error messages to copy.</span></span>  
  
 <span data-ttu-id="705be-124">**ErrorMessageLanguagesList**</span><span class="sxs-lookup"><span data-stu-id="705be-124">**ErrorMessageLanguagesList**</span></span>  
 <span data-ttu-id="705be-125">按一下瀏覽按鈕 **(...)** ，來選取將使用者定義之錯誤訊息複製到目的地伺服器所用的語言。</span><span class="sxs-lookup"><span data-stu-id="705be-125">Click the browse button **(...)** to select the languages for which to copy user-defined error messages to the destination server.</span></span> <span data-ttu-id="705be-126">在您可以傳送其他語言版本的訊息至目的地伺服器之前，us_english (字碼頁 1033) 版的訊息必須存在於該伺服器上。</span><span class="sxs-lookup"><span data-stu-id="705be-126">A us_english (code page 1033) version of the message must exist on the destination server before you can transfer other language versions of the message to that server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="705be-127">您必須先指定 [SourceConnection]  ，才能選取要複製的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="705be-127">You must specify the **SourceConnection** before you can select error messages to copy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="705be-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="705be-128">See Also</span></span>  
 <span data-ttu-id="705be-129">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="705be-129">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="705be-130">[Integration Services 工作](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="705be-130">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="705be-131">[傳送錯誤訊息工作編輯器 &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="705be-131">[Transfer Error Messages Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="705be-132">[SMO 連線管理員](connection-manager/smo-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="705be-132">[SMO Connection Manager](connection-manager/smo-connection-manager.md) </span></span>  
 <span data-ttu-id="705be-133">[傳送錯誤訊息工作編輯器 &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="705be-133">[Transfer Error Messages Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="705be-134">SMO 連線管理員</span><span class="sxs-lookup"><span data-stu-id="705be-134">SMO Connection Manager</span></span>](connection-manager/smo-connection-manager.md)  
  
  
