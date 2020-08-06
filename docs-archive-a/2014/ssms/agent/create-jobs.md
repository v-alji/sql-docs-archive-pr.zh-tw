---
title: 建立作業 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: 465fb7fc-7622-4252-a178-ea51691c935b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 706b9348eed5b190f99543a74e7019dc1bde5978
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699241"
---
# <a name="create-jobs"></a><span data-ttu-id="42f01-102">建立作業</span><span class="sxs-lookup"><span data-stu-id="42f01-102">Create Jobs</span></span>
  <span data-ttu-id="42f01-103">作業是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 循序執行的一系列指定作業。</span><span class="sxs-lookup"><span data-stu-id="42f01-103">A job is a specified series of operations performed sequentially by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="42f01-104">一項作業可執行大範圍的活動，包括執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼、命令提示字元應用程式、Microsoft ActiveX 指令碼、Integration Services 封裝、Analysis Services 命令及查詢，或是「複寫」作業。</span><span class="sxs-lookup"><span data-stu-id="42f01-104">A job can perform a wide range of activities, including running [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, command prompt applications, Microsoft ActiveX scripts, Integration Services packages, Analysis Services commands and queries, or Replication tasks.</span></span> <span data-ttu-id="42f01-105">作業可執行重複性或可排程的工作，並可自動產生警示，通知使用者作業的狀態，進而大量地簡化 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的管理程序。</span><span class="sxs-lookup"><span data-stu-id="42f01-105">Jobs can run repetitive or schedulable tasks, and they can automatically notify users of job status by generating alerts, thereby greatly simplifying [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administration.</span></span>  
  
 <span data-ttu-id="42f01-106">若要建立作業，使用者必須是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 固定資料庫角色或 **系統管理員 (sysadmin)** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="42f01-106">To create a job, a user must be a member of one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles or the **sysadmin** fixed server role.</span></span> <span data-ttu-id="42f01-107">只有作業擁有者或隸屬 **sysadmin** 角色的成員可以編輯作業。</span><span class="sxs-lookup"><span data-stu-id="42f01-107">A job can be edited only by its owner or members of the **sysadmin** role.</span></span> <span data-ttu-id="42f01-108">隸屬 **sysadmin** 角色的成員可以將作業擁有權指定給其他使用者，無論作業擁有者是誰，都可以執行任何作業。</span><span class="sxs-lookup"><span data-stu-id="42f01-108">Members of the **sysadmin** role can assign job ownership to other users, and they can run any job, regardless of the job owner.</span></span> <span data-ttu-id="42f01-109">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 固定資料庫角色的詳細資訊，請參閱 [SQL Server Agent 固定資料庫角色](sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="42f01-109">For more information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="42f01-110">您可以撰寫作業，讓它在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的本機執行個體或是整個企業的多個執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="42f01-110">Jobs can be written to run on the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or on multiple instances across an enterprise.</span></span> <span data-ttu-id="42f01-111">若要在多個伺服器上執行作業，您必須設定至少一個主要伺服器與一或多個目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="42f01-111">To run jobs on multiple servers, you must set up at least one master server and one or more target servers.</span></span> <span data-ttu-id="42f01-112">如需主要及目標伺服器的詳細資訊，請參閱 [將整個企業的管理自動化](automated-administration-across-an-enterprise.md)。</span><span class="sxs-lookup"><span data-stu-id="42f01-112">For more information about master and target servers, see [Automated Administration Across an Enterprise](automated-administration-across-an-enterprise.md)</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="42f01-113">Agent 會將作業及作業步驟資訊記錄在作業記錄中。</span><span class="sxs-lookup"><span data-stu-id="42f01-113">Agent records job and job step information in the job history.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="42f01-114">相關工作</span><span class="sxs-lookup"><span data-stu-id="42f01-114">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="42f01-115">**說明**</span><span class="sxs-lookup"><span data-stu-id="42f01-115">**Description**</span></span>|<span data-ttu-id="42f01-116">**主題**</span><span class="sxs-lookup"><span data-stu-id="42f01-116">**Topic**</span></span>|  
|<span data-ttu-id="42f01-117">描述如何建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="42f01-117">Describes how to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>|[<span data-ttu-id="42f01-118">建立作業</span><span class="sxs-lookup"><span data-stu-id="42f01-118">Create a Job</span></span>](create-a-job.md)|  
|<span data-ttu-id="42f01-119">描述如何將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業的擁有權重新指派給其他使用者。</span><span class="sxs-lookup"><span data-stu-id="42f01-119">Describes how to reassign ownership of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs to another user.</span></span>|[<span data-ttu-id="42f01-120">將作業擁有權授與其他人</span><span class="sxs-lookup"><span data-stu-id="42f01-120">Give Others Ownership of a Job</span></span>](give-others-ownership-of-a-job.md)|  
|<span data-ttu-id="42f01-121">描述如何設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的作業記錄。</span><span class="sxs-lookup"><span data-stu-id="42f01-121">Describes how to set up the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history log.</span></span>|[<span data-ttu-id="42f01-122">Set Up the Job History Log</span><span class="sxs-lookup"><span data-stu-id="42f01-122">Set Up the Job History Log</span></span>](set-up-the-job-history-log.md)|  
  
## <a name="see-also"></a><span data-ttu-id="42f01-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42f01-123">See Also</span></span>  
 <span data-ttu-id="42f01-124">[管理作業步驟](manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="42f01-124">[Manage Job Steps](manage-job-steps.md) </span></span>  
 <span data-ttu-id="42f01-125">[將整個企業的管理自動化](automated-administration-across-an-enterprise.md) </span><span class="sxs-lookup"><span data-stu-id="42f01-125">[Automated Administration Across an Enterprise](automated-administration-across-an-enterprise.md) </span></span>  
 <span data-ttu-id="42f01-126">[建立排程並將其附加至作業](create-and-attach-schedules-to-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="42f01-126">[Create and Attach Schedules to Jobs](create-and-attach-schedules-to-jobs.md) </span></span>  
 <span data-ttu-id="42f01-127">[執行作業](run-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="42f01-127">[Run Jobs](run-jobs.md) </span></span>  
 [<span data-ttu-id="42f01-128">檢視或修改作業</span><span class="sxs-lookup"><span data-stu-id="42f01-128">View or Modify Jobs</span></span>](view-or-modify-jobs.md)  
  
  
