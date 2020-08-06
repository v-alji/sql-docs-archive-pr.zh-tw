---
title: 指定作業回應 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], responses
- SQL Server Agent jobs, responses
- actions [SQL Server Agent jobs]
- responding to jobs
ms.assetid: 050242e1-9b79-4ade-91a9-580707b9d2d9
author: stevestein
ms.author: sstein
ms.openlocfilehash: d41c5e1552a1ff16343bdb2c4e9feaafb51c5783
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686753"
---
# <a name="specify-job-responses"></a><span data-ttu-id="d77e2-102">指定作業回應</span><span class="sxs-lookup"><span data-stu-id="d77e2-102">Specify Job Responses</span></span>
  <span data-ttu-id="d77e2-103">作業回應可指定完成作業後 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式服務將採取的動作。</span><span class="sxs-lookup"><span data-stu-id="d77e2-103">Job responses specify actions that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service will take after a job completes.</span></span> <span data-ttu-id="d77e2-104">作業回應可確保資料庫管理員知道作業已完成，以及作業的執行頻率。</span><span class="sxs-lookup"><span data-stu-id="d77e2-104">Job responses ensure that database administrators know when jobs complete and how frequently they run.</span></span> <span data-ttu-id="d77e2-105">典型的作業回應包括：</span><span class="sxs-lookup"><span data-stu-id="d77e2-105">Typical job responses include:</span></span>  
  
-   <span data-ttu-id="d77e2-106">使用電子郵件、電子呼叫或 **net send** 訊息通知操作員。</span><span class="sxs-lookup"><span data-stu-id="d77e2-106">Notifying the operator by using e-mail, electronic paging, or a **net send** message.</span></span>  
  
     <span data-ttu-id="d77e2-107">如果操作員必須執行後續動作，請使用其中一個作業回應。</span><span class="sxs-lookup"><span data-stu-id="d77e2-107">Use one of these job responses if the operator must perform a follow-up action.</span></span> <span data-ttu-id="d77e2-108">例如，如果備份作業成功完成，必須告知操作員以取下備份磁帶，並將其存放在安全的地方。</span><span class="sxs-lookup"><span data-stu-id="d77e2-108">For example, if a backup job completes successfully, the operator must be notified to remove the backup tape and store it in a safe location.</span></span>  
  
-   <span data-ttu-id="d77e2-109">將事件訊息寫入至 Windows 應用程式記錄。</span><span class="sxs-lookup"><span data-stu-id="d77e2-109">Writing an event message to the Windows application log.</span></span>  
  
     <span data-ttu-id="d77e2-110">這個回應只用於失敗的作業。</span><span class="sxs-lookup"><span data-stu-id="d77e2-110">You can use this response only for failed jobs.</span></span>  
  
-   <span data-ttu-id="d77e2-111">自動刪除作業。</span><span class="sxs-lookup"><span data-stu-id="d77e2-111">Automatically deleting the job.</span></span>  
  
     <span data-ttu-id="d77e2-112">如果確定您將不再需要重新執行這個作業，請使用這個作業回應。</span><span class="sxs-lookup"><span data-stu-id="d77e2-112">Use this job response if you are certain that you do not need to rerun this job.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="d77e2-113">相關工作</span><span class="sxs-lookup"><span data-stu-id="d77e2-113">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d77e2-114">**說明**</span><span class="sxs-lookup"><span data-stu-id="d77e2-114">**Description**</span></span>|<span data-ttu-id="d77e2-115">**主題**</span><span class="sxs-lookup"><span data-stu-id="d77e2-115">**Topic**</span></span>|  
|<span data-ttu-id="d77e2-116">描述如何通知操作員作業狀態。</span><span class="sxs-lookup"><span data-stu-id="d77e2-116">Describes how to notify an operator of job status.</span></span>|[<span data-ttu-id="d77e2-117">通知操作員作業狀態</span><span class="sxs-lookup"><span data-stu-id="d77e2-117">Notify an Operator of Job Status</span></span>](notify-an-operator-of-job-status.md)|  
|<span data-ttu-id="d77e2-118">描述如何將作業狀態寫入 Windows 應用程式記錄檔。</span><span class="sxs-lookup"><span data-stu-id="d77e2-118">Describes how to write job status to the Windows application log.</span></span>|[<span data-ttu-id="d77e2-119">若要將作業狀態寫入到 Windows 應用程式記錄</span><span class="sxs-lookup"><span data-stu-id="d77e2-119">Write the Job Status to the Windows Application Log</span></span>](../../reporting-services/report-server/windows-application-log.md)|  
  
## <a name="see-also"></a><span data-ttu-id="d77e2-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d77e2-120">See Also</span></span>  
 [<span data-ttu-id="d77e2-121">監視及回應事件</span><span class="sxs-lookup"><span data-stu-id="d77e2-121">Monitor and Respond to Events</span></span>](monitor-and-respond-to-events.md)  
  
  
