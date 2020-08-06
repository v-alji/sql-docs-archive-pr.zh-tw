---
title: 執行 SQL Server Agent 作業工作 (維護計畫) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.executejob.f1
helpviewer_keywords:
- Execute SQL Server Agent Job Task dialog box
ms.assetid: 4ed75956-ebb8-4d8c-9c16-fc0eb00bd3a0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b997d5144b113102ba0ed2d9d1df59b6707acbee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598356"
---
# <a name="execute-sql-server-agent-job-task-maintenance-plan"></a><span data-ttu-id="a22f7-102">執行 SQL Server Agent 作業工作 (維護計畫)</span><span class="sxs-lookup"><span data-stu-id="a22f7-102">Execute SQL Server Agent Job Task (Maintenance Plan)</span></span>
  <span data-ttu-id="a22f7-103">使用 [執行 SQL Server Agent 作業工作] 對話方塊，即可在維護計畫內執行 Microsoft SQL Server Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="a22f7-103">Use the **Execute SQL Server Agent Job Task** dialog to execute Microsoft SQL Server Agent jobs within a maintenance plan.</span></span> <span data-ttu-id="a22f7-104">如果選取的連接上沒有 SQL Server Agent 作業，將無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="a22f7-104">This option will not be available if you have no SQL Server Agent jobs on the selected connection.</span></span>  
  
 <span data-ttu-id="a22f7-105">此工作使用 **.sp_start_job** 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a22f7-105">This task uses the **.sp_start_job** statement.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="a22f7-106">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="a22f7-106">UI element list</span></span>  
 <span data-ttu-id="a22f7-107">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="a22f7-107">**Connection**</span></span>  
 <span data-ttu-id="a22f7-108">選取執行此工作時要使用的伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="a22f7-108">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="a22f7-109">**新增**</span><span class="sxs-lookup"><span data-stu-id="a22f7-109">**New**</span></span>  
 <span data-ttu-id="a22f7-110">建立新的伺服器連接，以便執行此工作時使用。</span><span class="sxs-lookup"><span data-stu-id="a22f7-110">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="a22f7-111">下面會描述 **[新增連接]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a22f7-111">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="a22f7-112">**可用的 SQL 代理程式作業**</span><span class="sxs-lookup"><span data-stu-id="a22f7-112">**Available SQL Agent jobs**</span></span>  
 <span data-ttu-id="a22f7-113">選取要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="a22f7-113">Select the job to execute.</span></span> <span data-ttu-id="a22f7-114">方格提供 [作業名稱] 和 [描述] 來識別作業。</span><span class="sxs-lookup"><span data-stu-id="a22f7-114">The grid provides the **Job name** and **Description** to identify the jobs.</span></span>  
  
 <span data-ttu-id="a22f7-115">**檢視 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="a22f7-115">**View T-SQL**</span></span>  
 <span data-ttu-id="a22f7-116">根據選取的選項，檢視此工作在伺服器上執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a22f7-116">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a22f7-117">受影響的物件數目較為大量時，會多花一些時間才會顯示。</span><span class="sxs-lookup"><span data-stu-id="a22f7-117">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="a22f7-118">新增連接對話方塊</span><span class="sxs-lookup"><span data-stu-id="a22f7-118">New Connection Dialog Box</span></span>  
 <span data-ttu-id="a22f7-119">**連線名稱**</span><span class="sxs-lookup"><span data-stu-id="a22f7-119">**Connection name**</span></span>  
 <span data-ttu-id="a22f7-120">輸入新連接的名稱。</span><span class="sxs-lookup"><span data-stu-id="a22f7-120">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="a22f7-121">**選取或輸入伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="a22f7-121">**Select or enter a server name**</span></span>  
 <span data-ttu-id="a22f7-122">選取執行此工作時要連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="a22f7-122">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="a22f7-123">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="a22f7-123">**Refresh**</span></span>  
 <span data-ttu-id="a22f7-124">重新整理可用的伺服器清單。</span><span class="sxs-lookup"><span data-stu-id="a22f7-124">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="a22f7-125">**輸入要登入到伺服器的資訊**</span><span class="sxs-lookup"><span data-stu-id="a22f7-125">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="a22f7-126">指定如何對伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="a22f7-126">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="a22f7-127">**使用 Windows 整合式安全性**</span><span class="sxs-lookup"><span data-stu-id="a22f7-127">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="a22f7-128">使用 Microsoft Windows 驗證連線到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a22f7-128">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with Microsoft Windows Authentication.</span></span>  
  
 <span data-ttu-id="a22f7-129">**使用特定的使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="a22f7-129">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="a22f7-130">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連線到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a22f7-130">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="a22f7-131">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="a22f7-131">This option is not available.</span></span>  
  
 <span data-ttu-id="a22f7-132">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="a22f7-132">**User name**</span></span>  
 <span data-ttu-id="a22f7-133">提供驗證時要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="a22f7-133">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="a22f7-134">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="a22f7-134">This option is not available.</span></span>  
  
 <span data-ttu-id="a22f7-135">**密碼**</span><span class="sxs-lookup"><span data-stu-id="a22f7-135">**Password**</span></span>  
 <span data-ttu-id="a22f7-136">提供驗證時要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="a22f7-136">Provide a password to use when authenticating.</span></span> <span data-ttu-id="a22f7-137">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="a22f7-137">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a22f7-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a22f7-138">See Also</span></span>  
 <span data-ttu-id="a22f7-139">[sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a22f7-139">[sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql) </span></span>  
 <span data-ttu-id="a22f7-140">[建立作業](../../ssms/agent/create-a-job.md) </span><span class="sxs-lookup"><span data-stu-id="a22f7-140">[Create a Job](../../ssms/agent/create-a-job.md) </span></span>  
 [<span data-ttu-id="a22f7-141">sp_start_job &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a22f7-141">sp_start_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)  
  
  
