---
title: SQL Server Agent 屬性 (進階頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.advanced.f1
ms.assetid: a4d798ee-4c18-40d4-b6af-63d17503738c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8ec0d9d7fbd51f9350bf692588f90c292e54f4e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599315"
---
# <a name="sql-server-agent-properties-advanced-page"></a><span data-ttu-id="7ca6d-102">SQL Server Agent 屬性 (進階頁面)</span><span class="sxs-lookup"><span data-stu-id="7ca6d-102">SQL Server Agent Properties (Advanced Page)</span></span>
  <span data-ttu-id="7ca6d-103">使用此頁面來查看和修改 Agent 服務的 advanced 屬性 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7ca6d-103">Use this page to view and modify advanced properties of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7ca6d-104">選項</span><span class="sxs-lookup"><span data-stu-id="7ca6d-104">Options</span></span>  
 <span data-ttu-id="7ca6d-105">**SQL Server 事件轉送**</span><span class="sxs-lookup"><span data-stu-id="7ca6d-105">**SQL Server event forwarding**</span></span>  
 <span data-ttu-id="7ca6d-106">此類別目錄中的選項會啟動和設定事件轉送。</span><span class="sxs-lookup"><span data-stu-id="7ca6d-106">The options in this category activate and configure event forwarding.</span></span>  
  
 <span data-ttu-id="7ca6d-107">**轉送事件到另一部伺服器**</span><span class="sxs-lookup"><span data-stu-id="7ca6d-107">**Forward events to a different server**</span></span>  
 <span data-ttu-id="7ca6d-108">轉送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 事件到另一部伺服器。</span><span class="sxs-lookup"><span data-stu-id="7ca6d-108">Forwards [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent events to a different server.</span></span>  
  
 <span data-ttu-id="7ca6d-109">**Server**</span><span class="sxs-lookup"><span data-stu-id="7ca6d-109">**Server**</span></span>  
 <span data-ttu-id="7ca6d-110">選取要接收轉送事件之伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="7ca6d-110">Select the name of the server to forward events to.</span></span>  
  
 <span data-ttu-id="7ca6d-111">**未處理的事件**</span><span class="sxs-lookup"><span data-stu-id="7ca6d-111">**Unhandled events**</span></span>  
 <span data-ttu-id="7ca6d-112">只轉送未處理的事件到指定的伺服器。</span><span class="sxs-lookup"><span data-stu-id="7ca6d-112">Forwards only unhandled events to the specified server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7ca6d-113">Agent 只轉送警示未回應的事件。</span><span class="sxs-lookup"><span data-stu-id="7ca6d-113">Agent forwards only events that no alert responds to.</span></span>  
  
 <span data-ttu-id="7ca6d-114">**所有事件**</span><span class="sxs-lookup"><span data-stu-id="7ca6d-114">**All events**</span></span>  
 <span data-ttu-id="7ca6d-115">轉送所有事件。</span><span class="sxs-lookup"><span data-stu-id="7ca6d-115">Forwards all events.</span></span> <span data-ttu-id="7ca6d-116">當邏輯執行個體中的警示回應事件時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 將同時轉送事件和處理警示。</span><span class="sxs-lookup"><span data-stu-id="7ca6d-116">When an alert in the local instance responds to the event, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent will both forward the event and process the alert.</span></span>  
  
 <span data-ttu-id="7ca6d-117">**如果事件的嚴重性等於或高於**</span><span class="sxs-lookup"><span data-stu-id="7ca6d-117">**If event has severity at or above**</span></span>  
 <span data-ttu-id="7ca6d-118">只轉送等於或高於指定層級的嚴重性層級事件。</span><span class="sxs-lookup"><span data-stu-id="7ca6d-118">Forwards only events with a severity level at or above the level specified.</span></span>  
  
 <span data-ttu-id="7ca6d-119">**閒置 CPU 的條件**</span><span class="sxs-lookup"><span data-stu-id="7ca6d-119">**Idle CPU Condition**</span></span>  
 <span data-ttu-id="7ca6d-120">此類別目錄中的選項，會定義 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 執行已排程要在閒置 CPU 排程上執行之作業的條件。</span><span class="sxs-lookup"><span data-stu-id="7ca6d-120">The options in this category define the conditions under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs jobs scheduled to run on the Idle CPU schedule.</span></span>  
  
 <span data-ttu-id="7ca6d-121">**定義閒置 CPU 的條件**</span><span class="sxs-lookup"><span data-stu-id="7ca6d-121">**Define idle CPU condition**</span></span>  
 <span data-ttu-id="7ca6d-122">定義 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 將 CPU 視為閒置的條件。</span><span class="sxs-lookup"><span data-stu-id="7ca6d-122">Defines the conditions under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent considers the CPU to be idle.</span></span>  
  
 <span data-ttu-id="7ca6d-123">**平均 CPU 使用量低於**</span><span class="sxs-lookup"><span data-stu-id="7ca6d-123">**Average CPU usage falls below**</span></span>  
 <span data-ttu-id="7ca6d-124">低於此百分比的 CPU 使用量百分比，就將 CPU 視為閒置。</span><span class="sxs-lookup"><span data-stu-id="7ca6d-124">Percentage of CPU usage below which the CPU is considered to be idle.</span></span>  
  
 <span data-ttu-id="7ca6d-125">**並且持續低於此狀態達**</span><span class="sxs-lookup"><span data-stu-id="7ca6d-125">**And remains below this level for**</span></span>  
 <span data-ttu-id="7ca6d-126">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 執行閒置 CPU 排程上的作業之前，平均 CPU 必須低於指定層級的時間量。</span><span class="sxs-lookup"><span data-stu-id="7ca6d-126">Amount of time that the average CPU must below the level specified before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs jobs on the Idle CPU schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca6d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ca6d-127">See Also</span></span>  
 <span data-ttu-id="7ca6d-128">[建立排程並將其附加至作業](create-and-attach-schedules-to-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="7ca6d-128">[Create and Attach Schedules to Jobs](create-and-attach-schedules-to-jobs.md) </span></span>  
 [<span data-ttu-id="7ca6d-129">管理事件</span><span class="sxs-lookup"><span data-stu-id="7ca6d-129">Manage Events</span></span>](manage-events.md)  
  
  
