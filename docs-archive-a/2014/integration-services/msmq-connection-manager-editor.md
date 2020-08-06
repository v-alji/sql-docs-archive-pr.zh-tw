---
title: MSMQ 連線管理員編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msmqconnectionmanager.f1
helpviewer_keywords:
- MSMQ Connection Manager Editor
ms.assetid: ef842cb4-82da-4550-85fe-9bedbc1e77c7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 41d4231ce121d596c8d818485eccf5ddf6127470
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592110"
---
# <a name="msmq-connection-manager-editor"></a><span data-ttu-id="99937-102">MSMQ 連線管理員編輯器</span><span class="sxs-lookup"><span data-stu-id="99937-102">MSMQ Connection Manager Editor</span></span>
  <span data-ttu-id="99937-103">使用 [MSMQ 連線管理員]  對話方塊，來指定 Message Queuing (又稱為 MSMQ) 訊息佇列的路徑。</span><span class="sxs-lookup"><span data-stu-id="99937-103">Use the **MSMQ Connection Manager** dialog box to specify the path to a Message Queuing (also known as MSMQ) message queue.</span></span>  
  
 <span data-ttu-id="99937-104">若要深入了解 MSMQ 連線管理員，請參閱＜ [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="99937-104">To learn more about the MSMQ connection manager, see [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="99937-105">MSMQ 連線管理員支援本機的共用和私用佇列，以及遠端的公用佇列。</span><span class="sxs-lookup"><span data-stu-id="99937-105">The MSMQ connection manager supports local public and private queues and remote public queues.</span></span> <span data-ttu-id="99937-106">但不支援遠端私用佇列。</span><span class="sxs-lookup"><span data-stu-id="99937-106">It does not support remote private queues.</span></span> <span data-ttu-id="99937-107">如需使用指令碼工作的解決方案，請參閱＜ [以指令碼工作傳送至遠端私用訊息佇列](control-flow/script-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="99937-107">For a workaround that uses the Script Task, see [Sending to a Remote Private Message Queue with the Script Task](control-flow/script-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="99937-108">選項。</span><span class="sxs-lookup"><span data-stu-id="99937-108">Options</span></span>  
 <span data-ttu-id="99937-109">**名稱**</span><span class="sxs-lookup"><span data-stu-id="99937-109">**Name**</span></span>  
 <span data-ttu-id="99937-110">提供唯一的名稱給工作流程中的 MSMQ 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="99937-110">Provide a unique name for the MSMQ connection manager in the workflow.</span></span> <span data-ttu-id="99937-111">提供的名稱將顯示在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師內。</span><span class="sxs-lookup"><span data-stu-id="99937-111">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="99937-112">**說明**</span><span class="sxs-lookup"><span data-stu-id="99937-112">**Description**</span></span>  
 <span data-ttu-id="99937-113">描述連接管理員。</span><span class="sxs-lookup"><span data-stu-id="99937-113">Describe the connection manager.</span></span> <span data-ttu-id="99937-114">最佳作法是以其用途描述連接管理員，使封裝可以自我記錄並易於維護。</span><span class="sxs-lookup"><span data-stu-id="99937-114">As a best practice, describe the connection manager in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="99937-115">**路徑**</span><span class="sxs-lookup"><span data-stu-id="99937-115">**Path**</span></span>  
 <span data-ttu-id="99937-116">輸入訊息佇列的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="99937-116">Type the complete path of the message queue.</span></span> <span data-ttu-id="99937-117">路徑的格式取決於佇列的類型。</span><span class="sxs-lookup"><span data-stu-id="99937-117">The format of the path depends on the type of queue.</span></span>  
  
|<span data-ttu-id="99937-118">佇列類型</span><span class="sxs-lookup"><span data-stu-id="99937-118">Queue type</span></span>|<span data-ttu-id="99937-119">範例路徑</span><span class="sxs-lookup"><span data-stu-id="99937-119">Sample path</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="99937-120">公開</span><span class="sxs-lookup"><span data-stu-id="99937-120">Public</span></span>|<span data-ttu-id="99937-121">\<computer name>\\<佇列名稱\></span><span class="sxs-lookup"><span data-stu-id="99937-121">\<computer name>\\<queue name\></span></span>|  
|<span data-ttu-id="99937-122">Private</span><span class="sxs-lookup"><span data-stu-id="99937-122">Private</span></span>|<span data-ttu-id="99937-123">\<computer name>\Private$\\<佇列名稱\></span><span class="sxs-lookup"><span data-stu-id="99937-123">\<computer name>\Private$\\<queue name\></span></span>|  
  
 <span data-ttu-id="99937-124">您可以使用 "." 代表本機電腦。</span><span class="sxs-lookup"><span data-stu-id="99937-124">You can use "." to represent the local computer.</span></span>  
  
 <span data-ttu-id="99937-125">**Test**</span><span class="sxs-lookup"><span data-stu-id="99937-125">**Test**</span></span>  
 <span data-ttu-id="99937-126">在設定 MSMQ 連線管理員之後，請按一下 [測試]  來確認連接已可使用。</span><span class="sxs-lookup"><span data-stu-id="99937-126">After configuring the MSMQ connection manager, confirm that the connection is viable by clicking **Test**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99937-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99937-127">See Also</span></span>  
 [<span data-ttu-id="99937-128">Integration Services 錯誤和訊息參考</span><span class="sxs-lookup"><span data-stu-id="99937-128">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
