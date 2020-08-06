---
title: 指定事件轉送伺服器 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- alerts [SQL Server], forwarded events
ms.assetid: 81dfcbe4-3000-4e77-99de-bf85fef63a12
author: stevestein
ms.author: sstein
ms.openlocfilehash: bc5f01507bf893d1bffc682f65a01b9ff48ffa9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705878"
---
# <a name="designate-an-events-forwarding-server-sql-server-management-studio"></a><span data-ttu-id="3751f-102">指定事件轉送伺服器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3751f-102">Designate an Events Forwarding Server (SQL Server Management Studio)</span></span>
  <span data-ttu-id="3751f-103">本主題描述如何使用，在中指定將 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事件轉送到哪一台伺服器 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3751f-103">This topic describes how to designate a server to which [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] forwards events in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .</span></span> <span data-ttu-id="3751f-104">請注意，事件轉送適用於在伺服器之間轉送的事件，而不適用於在單一電腦上裝載之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之間轉送的事件。</span><span class="sxs-lookup"><span data-stu-id="3751f-104">Note that event forwarding applies to events forwarded between servers, not to events forwarded between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hosted on a single computer.</span></span> <span data-ttu-id="3751f-105">同時請注意，若要接收轉送的事件，則警示管理伺服器必須是預設的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3751f-105">Also note that in order to receive forwarded events, the alerts management server must be a default instance of SQL Server.</span></span>  
  
 <span data-ttu-id="3751f-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="3751f-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3751f-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="3751f-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3751f-108">安全性</span><span class="sxs-lookup"><span data-stu-id="3751f-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3751f-109">**若要使用下列項目指定事件轉送伺服器：**</span><span class="sxs-lookup"><span data-stu-id="3751f-109">**To designate an events forwarding server, using:**</span></span>  
  
     [<span data-ttu-id="3751f-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3751f-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3751f-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="3751f-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3751f-112">Security</span><span class="sxs-lookup"><span data-stu-id="3751f-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3751f-113">權限</span><span class="sxs-lookup"><span data-stu-id="3751f-113">Permissions</span></span>  
 <span data-ttu-id="3751f-114">需要 **系統管理員 (sysadmin)** 固定伺服器角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="3751f-114">Requires membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3751f-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3751f-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-designate-an-events-forwarding-server"></a><span data-ttu-id="3751f-116">指定事件轉送伺服器</span><span class="sxs-lookup"><span data-stu-id="3751f-116">To designate an events forwarding server</span></span>  
  
1.  <span data-ttu-id="3751f-117">在 **[物件總管]** 中，按一下加號展開伺服器，從此伺服器轉送事件到另一部伺服器。</span><span class="sxs-lookup"><span data-stu-id="3751f-117">In **Object Explorer,** click the plus sign to expand the server from which you want to forward events to another server.</span></span>  
  
2.  <span data-ttu-id="3751f-118">以滑鼠右鍵按一下**SQL Server Agent** ，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="3751f-118">Right-click **SQL Server Agent** and select **Properties**.</span></span>  

3.  <span data-ttu-id="3751f-119">在 [SQL Server Agent 屬性 - <伺服器名稱>]\*\*\*\*__ 對話方塊的 [選取頁面]\*\*\*\* 下，選取 [進階]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3751f-119">In the **SQL Server Agent Properties -**_server_name_ dialog box, under **Select a page**, select **Advanced**.</span></span>  

4.  <span data-ttu-id="3751f-120">在 **[SQL Server 事件轉送]** 下，選取 **[轉送事件到另一部伺服器]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="3751f-120">Under **SQL Server event forwarding**, select the **Forward events to a different server** check box.</span></span>  
  
5.  <span data-ttu-id="3751f-121">在 **[伺服器]** 清單中選取伺服器，然後在 **[事件]** 下選取下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="3751f-121">In the **Server** list, select a server, and then, under **Events**, select one of the following:</span></span>  
  
    -   <span data-ttu-id="3751f-122">選取 **[未處理的事件]** ，只轉送本機警示尚未處理的事件。</span><span class="sxs-lookup"><span data-stu-id="3751f-122">Select **Unhandled events** to forward only the events that have not been handled by local alerts.</span></span>  
  
    -   <span data-ttu-id="3751f-123">選取 **[所有事件]** ，轉送所有的事件，不論本機警示是否已處理。</span><span class="sxs-lookup"><span data-stu-id="3751f-123">Select **All events** to forward all events regardless of whether they have been handled by local alerts.</span></span>  
  
6.  <span data-ttu-id="3751f-124">在 **[如果事件的嚴重性等於或高於]** 清單中，按一下會開始將事件轉送至選定伺服器的嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="3751f-124">In the **If event has severity at or above** list, click the severity level at which events are forwarded to the selected server.</span></span>  
  
7.  <span data-ttu-id="3751f-125">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="3751f-125">When finished, click **OK**.</span></span>  
  
  
