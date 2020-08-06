---
title: 刪除作業 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- delete jobs
ms.assetid: bffb915e-bc84-4417-aa35-183243ca3312
author: stevestein
ms.author: sstein
ms.openlocfilehash: f66387a1334f91c29b8edddad293d76064430b39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705881"
---
# <a name="delete-jobs"></a><span data-ttu-id="6aff1-102">刪除作業</span><span class="sxs-lookup"><span data-stu-id="6aff1-102">Delete Jobs</span></span>
  <span data-ttu-id="6aff1-103">作業是 SQL Server Agent 循序執行的一系列指定作業。</span><span class="sxs-lookup"><span data-stu-id="6aff1-103">A job is a specified series of operations performed sequentially by SQL Server Agent.</span></span> <span data-ttu-id="6aff1-104">根據預設，執行完成時不會刪除作業。</span><span class="sxs-lookup"><span data-stu-id="6aff1-104">By default, jobs are not deleted when execution finishes.</span></span> <span data-ttu-id="6aff1-105">您可以刪除一個或多個 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業，無論作業成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="6aff1-105">You can delete one or more [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs regardless of success or failure of the job.</span></span> <span data-ttu-id="6aff1-106">您也可以設定 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 在作業成功、失敗或完成時自動予以刪除。</span><span class="sxs-lookup"><span data-stu-id="6aff1-106">You can also configure [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to automatically delete jobs when they succeed, fail, or complete.</span></span>  
  
 <span data-ttu-id="6aff1-107">根據預設，系統管理員（ **sysadmin** ）固定伺服器角色的成員可以執行[Sp_delete_job，&#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql)系統預存程式來刪除作業。</span><span class="sxs-lookup"><span data-stu-id="6aff1-107">By default, members of the **sysadmin** fixed server role can execute the [sp_delete_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql) system stored procedure to delete a job.</span></span> <span data-ttu-id="6aff1-108">其他使用者必須被授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **資料庫的下列其中一個** Agent 固定資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="6aff1-108">Other users must be granted one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the **msdb** database:</span></span>  
  
-   <span data-ttu-id="6aff1-109">**SQLAgentUserRole**</span><span class="sxs-lookup"><span data-stu-id="6aff1-109">**SQLAgentUserRole**</span></span>  
  
-   <span data-ttu-id="6aff1-110">**SQLAgentReaderRole**</span><span class="sxs-lookup"><span data-stu-id="6aff1-110">**SQLAgentReaderRole**</span></span>  
  
-   <span data-ttu-id="6aff1-111">**SQLAgentOperatorRole**</span><span class="sxs-lookup"><span data-stu-id="6aff1-111">**SQLAgentOperatorRole**</span></span>  
  
 <span data-ttu-id="6aff1-112">如需這些角色權限的詳細資訊，請參閱 [SQL Server Agent 固定資料庫角色](sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="6aff1-112">For details about the permissions of these roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="6aff1-113">**系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠執行 **sp_delete_job** 來刪除任何作業。</span><span class="sxs-lookup"><span data-stu-id="6aff1-113">Members of the **sysadmin** fixed server role can execute **sp_delete_job** to delete any job.</span></span> <span data-ttu-id="6aff1-114">本身不是 **系統管理員 (sysadmin)** 固定伺服器角色成員的使用者只能刪除其本身所擁有的作業。</span><span class="sxs-lookup"><span data-stu-id="6aff1-114">A user that is not a member of the **sysadmin** fixed server role can only delete jobs owned by that user.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="6aff1-115">相關工作</span><span class="sxs-lookup"><span data-stu-id="6aff1-115">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6aff1-116">**說明**</span><span class="sxs-lookup"><span data-stu-id="6aff1-116">**Description**</span></span>|<span data-ttu-id="6aff1-117">**主題**</span><span class="sxs-lookup"><span data-stu-id="6aff1-117">**Topic**</span></span>|  
|<span data-ttu-id="6aff1-118">描述如何刪除一個或多個 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="6aff1-118">Describes how to delete one or more [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|[<span data-ttu-id="6aff1-119">刪除一個或多個作業</span><span class="sxs-lookup"><span data-stu-id="6aff1-119">Delete One or More Jobs</span></span>](delete-one-or-more-jobs.md)|  
|<span data-ttu-id="6aff1-120">描述如何設定 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 在作業成功、失敗或完成時自動予以刪除。</span><span class="sxs-lookup"><span data-stu-id="6aff1-120">Describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to automatically delete jobs when they succeed, fail, or complete.</span></span>|[<span data-ttu-id="6aff1-121">自動刪除作業</span><span class="sxs-lookup"><span data-stu-id="6aff1-121">Automatically Delete a Job</span></span>](automatically-delete-a-job.md)|  
  
  
