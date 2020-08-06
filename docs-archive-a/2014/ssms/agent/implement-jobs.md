---
title: 實作作業 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent]
- SQL Server Agent jobs
- SQL Server Agent jobs, about jobs
- jobs [SQL Server Agent], about jobs
ms.assetid: 69e06724-25c7-4fb3-8a5b-3d4596f21756
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1925b3113db8d7c57ac4344958c0247763cfd1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584951"
---
# <a name="implement-jobs"></a><span data-ttu-id="2da89-102">實作作業</span><span class="sxs-lookup"><span data-stu-id="2da89-102">Implement Jobs</span></span>
  <span data-ttu-id="2da89-103">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業，使例行性管理工作自動化，並重複執行它們，使管理更有效率。</span><span class="sxs-lookup"><span data-stu-id="2da89-103">You can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs to automate routine administrative tasks and run them on a recurring basis, making administration more efficient.</span></span>  
  
 <span data-ttu-id="2da89-104">作業是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 循序執行的一系列指定作業。</span><span class="sxs-lookup"><span data-stu-id="2da89-104">A job is a specified series of operations performed sequentially by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="2da89-105">作業可執行各式各樣的活動，包括執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼、命令列應用程式、Microsoft ActiveX Script、Integration Services 封裝、Analysis Services 命令和查詢，或複寫工作。</span><span class="sxs-lookup"><span data-stu-id="2da89-105">A job can perform a wide range of activities, including running [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, command-line applications, Microsoft ActiveX scripts, Integration Services packages, Analysis Services commands and queries, or Replication tasks.</span></span> <span data-ttu-id="2da89-106">作業可執行重複性工作或可排程的工作，而且可產生警示，將作業狀態自動通知使用者，藉此大幅簡化 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的管理。</span><span class="sxs-lookup"><span data-stu-id="2da89-106">Jobs can run repetitive tasks or those that can be scheduled, and they can automatically notify users of job status by generating alerts, thereby greatly simplifying [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administration.</span></span>  
  
 <span data-ttu-id="2da89-107">您可以手動執行作業，或將作業設定為根據排程或為了回應警示而執行。</span><span class="sxs-lookup"><span data-stu-id="2da89-107">You can run a job manually, or you can configure it to run according to a schedule or in response to alerts.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="2da89-108">相關工作</span><span class="sxs-lookup"><span data-stu-id="2da89-108">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2da89-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="2da89-109">**Description**</span></span>|<span data-ttu-id="2da89-110">**主題**</span><span class="sxs-lookup"><span data-stu-id="2da89-110">**Topic**</span></span>|  
|<span data-ttu-id="2da89-111">包含有關建立作業及指派擁有權的資訊。</span><span class="sxs-lookup"><span data-stu-id="2da89-111">Contains information about creating jobs and assigning ownership.</span></span>|[<span data-ttu-id="2da89-112">建立作業</span><span class="sxs-lookup"><span data-stu-id="2da89-112">Create Jobs</span></span>](create-jobs.md)|  
|<span data-ttu-id="2da89-113">包含有關將作業組織成類別目錄的資訊。</span><span class="sxs-lookup"><span data-stu-id="2da89-113">Contains information about organizing jobs into categories.</span></span>|[<span data-ttu-id="2da89-114">組織作業</span><span class="sxs-lookup"><span data-stu-id="2da89-114">Organize Jobs</span></span>](organize-jobs.md)|  
|<span data-ttu-id="2da89-115">包含關於您可以建立的不同種類作業步驟及如何管理它們的資訊。</span><span class="sxs-lookup"><span data-stu-id="2da89-115">Contains information about the different kinds of job steps you can create and how to manage them.</span></span>|[<span data-ttu-id="2da89-116">管理作業步驟</span><span class="sxs-lookup"><span data-stu-id="2da89-116">Manage Job Steps</span></span>](manage-job-steps.md)|  
|<span data-ttu-id="2da89-117">包含關於如何定義作業何時開始執行及作業執行頻率等資訊。</span><span class="sxs-lookup"><span data-stu-id="2da89-117">Contains information about how to define when jobs start running and how often they should run.</span></span>|[<span data-ttu-id="2da89-118">建立及附加排程至作業</span><span class="sxs-lookup"><span data-stu-id="2da89-118">Create and Attach Schedules to Jobs</span></span>](create-and-attach-schedules-to-jobs.md)|  
|<span data-ttu-id="2da89-119">包含關於手動執行作業 (沒有排程) 的資訊。</span><span class="sxs-lookup"><span data-stu-id="2da89-119">Contains information about manually running jobs (without a schedule).</span></span>|[<span data-ttu-id="2da89-120">執行作業</span><span class="sxs-lookup"><span data-stu-id="2da89-120">Run Jobs</span></span>](run-jobs.md)|  
|<span data-ttu-id="2da89-121">包含關於如何設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 回應作業的資訊。</span><span class="sxs-lookup"><span data-stu-id="2da89-121">Contains information about how you can configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to respond to jobs.</span></span> <span data-ttu-id="2da89-122">例如，您可以設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 在作業完成時通知管理者。</span><span class="sxs-lookup"><span data-stu-id="2da89-122">For example, you can configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to notify administrators when jobs are finished.</span></span>|[<span data-ttu-id="2da89-123">指定作業回應</span><span class="sxs-lookup"><span data-stu-id="2da89-123">Specify Job Responses</span></span>](specify-job-responses.md)|  
|<span data-ttu-id="2da89-124">包含關於如何檢視現有的作業、其執行的記錄及如何修改它們等資訊。</span><span class="sxs-lookup"><span data-stu-id="2da89-124">Contains information about how to view existing jobs, their history once executes, and how to modify them.</span></span>|[<span data-ttu-id="2da89-125">檢視或修改作業</span><span class="sxs-lookup"><span data-stu-id="2da89-125">View or Modify Jobs</span></span>](view-or-modify-jobs.md)|  
|<span data-ttu-id="2da89-126">包含如何刪除作業的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2da89-126">Contains information about how to delete jobs.</span></span>|[<span data-ttu-id="2da89-127">刪除作業</span><span class="sxs-lookup"><span data-stu-id="2da89-127">Delete Jobs</span></span>](delete-jobs.md)|  
  
## <a name="see-also"></a><span data-ttu-id="2da89-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2da89-128">See Also</span></span>  
 [<span data-ttu-id="2da89-129">實作 SQL Server Agent 安全性</span><span class="sxs-lookup"><span data-stu-id="2da89-129">Implement SQL Server Agent Security</span></span>](implement-sql-server-agent-security.md)  
  
  
