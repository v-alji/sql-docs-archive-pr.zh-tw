---
title: SQL Server 擴充的事件引擎 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], engine
ms.assetid: d74642a5-42b9-4a15-aa3d-f98bfe695050
author: rothja
ms.author: jroth
ms.openlocfilehash: ef11ac8e2cfaf39d2bca90f1d5d52439989ee327
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585404"
---
# <a name="sql-server-extended-events-engine"></a><span data-ttu-id="f39da-102">SQL Server 擴充的事件引擎</span><span class="sxs-lookup"><span data-stu-id="f39da-102">SQL Server Extended Events Engine</span></span>
  <span data-ttu-id="f39da-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 擴充的事件引擎是執行以下作業之服務與物件的集合：</span><span class="sxs-lookup"><span data-stu-id="f39da-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Extended Events engine is a collection of services and objects that:</span></span>  
  
-   <span data-ttu-id="f39da-104">啟用事件的定義。</span><span class="sxs-lookup"><span data-stu-id="f39da-104">Enable the definition of events.</span></span>  
  
-   <span data-ttu-id="f39da-105">啟用事件資料的處理。</span><span class="sxs-lookup"><span data-stu-id="f39da-105">Enable processing event data.</span></span>  
  
-   <span data-ttu-id="f39da-106">管理系統中擴充的事件服務和物件。</span><span class="sxs-lookup"><span data-stu-id="f39da-106">Manage Extended Events services and objects in the system.</span></span>  
  
-   <span data-ttu-id="f39da-107">維護擴充的事件工作階段清單及管理對此清單的存取。</span><span class="sxs-lookup"><span data-stu-id="f39da-107">Maintain a list of Extended Events sessions and manage access to that list.</span></span>  
  
 <span data-ttu-id="f39da-108">擴充的事件引擎本身並未提供當事件引發時所要採取的任何事件或動作。</span><span class="sxs-lookup"><span data-stu-id="f39da-108">The Extended Events engine itself does not provide any events or actions to take when an event fires.</span></span> <span data-ttu-id="f39da-109">使用擴充之事件引擎的程序會定義與該引擎之間的互動。</span><span class="sxs-lookup"><span data-stu-id="f39da-109">The processes that use the Extended Events engine define interaction with the engine.</span></span> <span data-ttu-id="f39da-110">這些程序會加入事件點，並提供為了回應事件引發所要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="f39da-110">These processes add event points and supply the actions to take in response to event firing.</span></span>  
  
 <span data-ttu-id="f39da-111">下圖顯示擴充的事件工作階段的簡化檢視。</span><span class="sxs-lookup"><span data-stu-id="f39da-111">The following illustration shows a simplified view of an Extended Events session.</span></span> <span data-ttu-id="f39da-112">如需詳細資訊，請參閱 [SQL Server 擴充的事件工作階段](sql-server-extended-events-sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="f39da-112">For more information, see [SQL Server Extended Events Sessions](sql-server-extended-events-sessions.md).</span></span>  
  
 <span data-ttu-id="f39da-113">![詳細的擴充事件架構](../../database-engine/media/xearchitecturedetailed.gif "詳細的擴充事件架構")</span><span class="sxs-lookup"><span data-stu-id="f39da-113">![Detailed extended events architecture](../../database-engine/media/xearchitecturedetailed.gif "Detailed extended events architecture")</span></span>  
  
 <span data-ttu-id="f39da-114">請注意：</span><span class="sxs-lookup"><span data-stu-id="f39da-114">Note the following:</span></span>  
  
-   <span data-ttu-id="f39da-115">每一個 Windows 處理序都可以有一或多個模組 (**Win32 處理序**、 **Win32 模組**)。</span><span class="sxs-lookup"><span data-stu-id="f39da-115">Each Windows process can have one or more modules (**Win32 process**, **Win32 module**).</span></span> <span data-ttu-id="f39da-116">這些也稱為「二進位檔」\*\* 或「可執行模組」\*\*。</span><span class="sxs-lookup"><span data-stu-id="f39da-116">These are also known as *binaries* or *executable modules*.</span></span>  
  
-   <span data-ttu-id="f39da-117">每一個 Windows 處理序模組都可包含一或多個擴充的事件封裝 (**Package**)，其中包含一或多個擴充的事件物件 (**Type**、 **Target**、 **Action**、 **Map**、 **Predicate**和 **Event**)。</span><span class="sxs-lookup"><span data-stu-id="f39da-117">Each of the Windows process modules can contain one or more Extended Events packages (**Package**), which contain one or more Extended Events objects (**Type**, **Target**, **Action**, **Map**, **Predicate**, and **Event**).</span></span>  
  
-   <span data-ttu-id="f39da-118">在主機處理序內，只能有一個擴充的事件引擎執行個體 (**擴充的事件引擎**)，此執行個體會執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="f39da-118">Inside a host process there can only be one instance of the Extended Events engine (**Extended event engine**), which:</span></span>  
  
    -   <span data-ttu-id="f39da-119">管理此工作階段的某些層面 (例如，列舉工作階段)。</span><span class="sxs-lookup"><span data-stu-id="f39da-119">Manages some aspects of the session (for example, enumerating sessions).</span></span>  
  
    -   <span data-ttu-id="f39da-120">處理分派 (**發送器**)。</span><span class="sxs-lookup"><span data-stu-id="f39da-120">Handles dispatching (**Dispatcher**).</span></span> <span data-ttu-id="f39da-121">這與執行緒集區非常類似。</span><span class="sxs-lookup"><span data-stu-id="f39da-121">This is similar to a thread pool.</span></span>  
  
    -   <span data-ttu-id="f39da-122">處理事件的記憶體緩衝區 (**緩衝區**)。</span><span class="sxs-lookup"><span data-stu-id="f39da-122">Handles memory buffers (**Buffer**) for events.</span></span> <span data-ttu-id="f39da-123">當緩衝區填滿時，會將緩衝區分派給目標。</span><span class="sxs-lookup"><span data-stu-id="f39da-123">When buffers are filled, the buffers are dispatched to targets.</span></span>  
  
-   <span data-ttu-id="f39da-124">當建立工作階段，而且選擇性地將事件繫結至工作階段 (**工作階段內容**) 之後：</span><span class="sxs-lookup"><span data-stu-id="f39da-124">After a session is created and events are optionally bound to the session (**Session context**):</span></span>  
  
    -   <span data-ttu-id="f39da-125">也可能會建立目標的執行個體 (**目標執行個體**)，並將其加入工作階段。</span><span class="sxs-lookup"><span data-stu-id="f39da-125">Instances of targets (**Target instance**) may be also be created and added to the session.</span></span>  
  
    -   <span data-ttu-id="f39da-126">當緩衝區填滿時，會將這些緩衝區分派給目標。</span><span class="sxs-lookup"><span data-stu-id="f39da-126">When buffers are filled, those buffers are dispatched to targets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f39da-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f39da-127">See Also</span></span>  
 [<span data-ttu-id="f39da-128">擴充事件</span><span class="sxs-lookup"><span data-stu-id="f39da-128">Extended Events</span></span>](extended-events.md)  
  
  
