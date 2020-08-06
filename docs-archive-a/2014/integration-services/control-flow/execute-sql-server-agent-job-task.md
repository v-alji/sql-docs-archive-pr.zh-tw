---
title: 執行 SQL Server Agent 作業工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqlserveragentjobtask.f1
helpviewer_keywords:
- Execute SQL Server Agent Job task [Integration Services]
- jobs [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 3aa3bc0e-1a1c-452e-81b8-b4e3422ea053
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d0c66eb7022312fa3ec3d161f63a9aee92b840f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596842"
---
# <a name="execute-sql-server-agent-job-task"></a><span data-ttu-id="4c2fb-102">執行 SQL Server Agent 作業工作</span><span class="sxs-lookup"><span data-stu-id="4c2fb-102">Execute SQL Server Agent Job Task</span></span>
  <span data-ttu-id="4c2fb-103">「執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式作業」工作會執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式作業。</span><span class="sxs-lookup"><span data-stu-id="4c2fb-103">The Execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Job task runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4c2fb-104">Agent 是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 服務，可執行 SQL Server 執行個體中所定義的作業。</span><span class="sxs-lookup"><span data-stu-id="4c2fb-104">Agent is a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows service that runs jobs that have been defined in an instance of SQL Server.</span></span> <span data-ttu-id="4c2fb-105">您可以建立執行 Transact-SQL 陳述式和 ActiveX 指令碼的作業、執行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 和「複寫維護」工作，或執行封裝。</span><span class="sxs-lookup"><span data-stu-id="4c2fb-105">You can create jobs that execute Transact-SQL statements and ActiveX scripts, perform [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and Replication maintenance tasks, or run packages.</span></span> <span data-ttu-id="4c2fb-106">您也可以設定作業來監視 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以及引發警示。</span><span class="sxs-lookup"><span data-stu-id="4c2fb-106">You can also configure a job to monitor [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and fire alerts.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4c2fb-107">Agent 作業通常可用來自動化重複執行的工作。</span><span class="sxs-lookup"><span data-stu-id="4c2fb-107">Agent jobs are typically used to automate tasks that you perform repeatedly.</span></span> <span data-ttu-id="4c2fb-108">如需詳細資訊，請參閱 [實作作業](../../ssms/agent/implement-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="4c2fb-108">For more information, see [Implement Jobs](../../ssms/agent/implement-jobs.md).</span></span>  
  
 <span data-ttu-id="4c2fb-109">封裝可藉由使用「執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業」工作，執行與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件有關的管理工作。</span><span class="sxs-lookup"><span data-stu-id="4c2fb-109">By using the Execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Job task, a package can perform administrative tasks related to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="4c2fb-110">例如， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業可執行 **sp_enum_dtspackages** 這類系統預存程序，以取得資料夾中的封裝清單。</span><span class="sxs-lookup"><span data-stu-id="4c2fb-110">For example, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job can run a system stored procedure such as **sp_enum_dtspackages** to obtain a list of packages in a folder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4c2fb-111">Agent 必須先執行，本機或多伺服器管理作業才能自動執行。</span><span class="sxs-lookup"><span data-stu-id="4c2fb-111">Agent must be running before local or multiserver administrative jobs can run automatically.</span></span>  
  
 <span data-ttu-id="4c2fb-112">此工作會封裝 **sp_start_job** 系統程序，並將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業的名稱傳遞至程序作為引數。</span><span class="sxs-lookup"><span data-stu-id="4c2fb-112">This task encapsulates the **sp_start_job** system procedure and passes the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job to the procedure as an argument.</span></span> <span data-ttu-id="4c2fb-113">如需詳細資訊，請參閱 [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4c2fb-113">For more information, see [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).</span></span>  
  
## <a name="configuring-the-execute-sql-server-agent-job-task"></a><span data-ttu-id="4c2fb-114">設定執行 SQL Server Agent 作業工作</span><span class="sxs-lookup"><span data-stu-id="4c2fb-114">Configuring the Execute SQL Server Agent Job Task</span></span>  
 <span data-ttu-id="4c2fb-115">您可以透過 [ [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師] 設定屬性。</span><span class="sxs-lookup"><span data-stu-id="4c2fb-115">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="4c2fb-116">這項工作位於「 **設計師」中** [工具箱] **的** [維護計畫工作] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 區段。</span><span class="sxs-lookup"><span data-stu-id="4c2fb-116">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="4c2fb-117">如需有關可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="4c2fb-117">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="4c2fb-118">執行 SQL Server Agent 作業工作 &#40;維護計畫&#41;</span><span class="sxs-lookup"><span data-stu-id="4c2fb-118">Execute SQL Server Agent Job Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/execute-sql-server-agent-job-task-maintenance-plan.md)  
  
 <span data-ttu-id="4c2fb-119">如需有關如何在「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="4c2fb-119">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="4c2fb-120">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="4c2fb-120">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
