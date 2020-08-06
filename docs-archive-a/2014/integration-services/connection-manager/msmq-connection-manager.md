---
title: MSMQ 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], message queues
- connection managers [Integration Services], MSMQ
- MSMQ connection manager
- message queue connections [Integration Services]
ms.assetid: a86900e2-450e-479f-b207-e1b02361d395
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0c51866eeef281f6587bf281461e4faa2278308d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599139"
---
# <a name="msmq-connection-manager"></a><span data-ttu-id="2cd14-102">MSMQ 連接管理員</span><span class="sxs-lookup"><span data-stu-id="2cd14-102">MSMQ Connection Manager</span></span>
  <span data-ttu-id="2cd14-103">MSMQ 連接管理員可讓封裝連接到使用 Message Queuing (又稱為 MSMQ) 的訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="2cd14-103">An MSMQ connection manager enables a package to connect to a message queue that uses Message Queuing (also known as MSMQ).</span></span> <span data-ttu-id="2cd14-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含的「訊息佇列」工作會使用 MSMQ 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="2cd14-104">The Message Queue task that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses an MSMQ connection manager.</span></span>  
  
 <span data-ttu-id="2cd14-105">當您將 MSMQ 連接管理員加入封裝時，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會建立在執行階段解析為 MSMQ 連接的連接管理員、設定連接管理員屬性，並將連接管理員加入封裝上的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="2cd14-105">When you add an MSMQ connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an MSMQ connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="2cd14-106">連接管理員的 `ConnectionManagerType` 屬性會設為 `MSMQ`。</span><span class="sxs-lookup"><span data-stu-id="2cd14-106">The `ConnectionManagerType` property of the connection manager is set to `MSMQ`.</span></span>  
  
 <span data-ttu-id="2cd14-107">您可以利用下列方式設定 MSMQ 連接管理員：</span><span class="sxs-lookup"><span data-stu-id="2cd14-107">You can configure an MSMQ connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="2cd14-108">提供連接字串。</span><span class="sxs-lookup"><span data-stu-id="2cd14-108">Provide a connection string.</span></span>  
  
-   <span data-ttu-id="2cd14-109">提供要連接之訊息佇列的路徑。</span><span class="sxs-lookup"><span data-stu-id="2cd14-109">Provide the path of the message queue to connect to.</span></span>  
  
 <span data-ttu-id="2cd14-110">路徑的格式取決於佇列類型，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="2cd14-110">The format of the path depends on the type of queue, as shown in the following table.</span></span>  
  
|<span data-ttu-id="2cd14-111">佇列類型</span><span class="sxs-lookup"><span data-stu-id="2cd14-111">Queue type</span></span>|<span data-ttu-id="2cd14-112">範例路徑</span><span class="sxs-lookup"><span data-stu-id="2cd14-112">Sample path</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="2cd14-113">公開</span><span class="sxs-lookup"><span data-stu-id="2cd14-113">Public</span></span>|<span data-ttu-id="2cd14-114">\<computer name>\\<佇列名稱\></span><span class="sxs-lookup"><span data-stu-id="2cd14-114">\<computer name>\\<queue name\></span></span>|  
|<span data-ttu-id="2cd14-115">Private</span><span class="sxs-lookup"><span data-stu-id="2cd14-115">Private</span></span>|<span data-ttu-id="2cd14-116">\<computer name>\Private$\\<佇列名稱\></span><span class="sxs-lookup"><span data-stu-id="2cd14-116">\<computer name>\Private$\\<queue name\></span></span>|  
  
 <span data-ttu-id="2cd14-117">您可以使用句號 (.) 代表本機電腦。</span><span class="sxs-lookup"><span data-stu-id="2cd14-117">You can use a period (.) to represent the local computer.</span></span>  
  
## <a name="configuration-of-the-msmq-connection-manager"></a><span data-ttu-id="2cd14-118">MSMQ 連接管理員的組態</span><span class="sxs-lookup"><span data-stu-id="2cd14-118">Configuration of the MSMQ Connection Manager</span></span>  
 <span data-ttu-id="2cd14-119">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="2cd14-119">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="2cd14-120">如需可在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請參閱 [MSMQ 連線管理員編輯器](../msmq-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="2cd14-120">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [MSMQ Connection Manager Editor](../msmq-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="2cd14-121">如需以程式設計方式設定連線管理員的資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以程式設計方式加入連接](../building-packages-programmatically/adding-connections-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="2cd14-121">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cd14-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cd14-122">See Also</span></span>  
 <span data-ttu-id="2cd14-123">[訊息佇列工作](../control-flow/message-queue-task.md) </span><span class="sxs-lookup"><span data-stu-id="2cd14-123">[Message Queue Task](../control-flow/message-queue-task.md) </span></span>  
 [<span data-ttu-id="2cd14-124">Integration Services &#40;SSIS&#41; 連接</span><span class="sxs-lookup"><span data-stu-id="2cd14-124">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
