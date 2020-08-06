---
title: 自動刪除作業 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- dropping jobs
- SQL Server Agent jobs, removing
- automatic job removal
- jobs [SQL Server Agent], deleting
- deleting jobs
- removing jobs
ms.assetid: 92dbb6da-5919-4bde-9354-d454e9ea3da0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 07a10ec4a31d553a548bfecdcba426e3b46a1782
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597549"
---
# <a name="automatically-delete-a-job"></a><span data-ttu-id="5d039-102">自動刪除作業</span><span class="sxs-lookup"><span data-stu-id="5d039-102">Automatically Delete a Job</span></span>
  <span data-ttu-id="5d039-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或 SQL Server 管理物件，在中設定 Agent 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 作業成功、失敗或完成時自動予以刪除 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5d039-103">This topic describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to automatically delete jobs when they succeed, fail, or complete by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="5d039-104">作業回應可確保資料庫管理員知道作業已完成，以及作業的執行頻率。</span><span class="sxs-lookup"><span data-stu-id="5d039-104">Job responses ensure that database administrators know when jobs complete and how frequently they run.</span></span> <span data-ttu-id="5d039-105">典型的作業回應包括：</span><span class="sxs-lookup"><span data-stu-id="5d039-105">Typical job responses include:</span></span>  
  
-   <span data-ttu-id="5d039-106">使用電子郵件、電子呼叫或 **net send** 訊息通知操作員。</span><span class="sxs-lookup"><span data-stu-id="5d039-106">Notifying the operator by using e-mail, electronic paging, or a **net send** message.</span></span>  
  
     <span data-ttu-id="5d039-107">如果操作員必須執行後續動作，請使用其中一個作業回應。</span><span class="sxs-lookup"><span data-stu-id="5d039-107">Use one of these job responses if the operator must perform a follow-up action.</span></span> <span data-ttu-id="5d039-108">例如，如果備份作業成功完成，必須告知操作員以取下備份磁帶，並將其存放在安全的地方。</span><span class="sxs-lookup"><span data-stu-id="5d039-108">For example, if a backup job completes successfully, the operator must be notified to remove the backup tape and store it in a safe location.</span></span>  
  
-   <span data-ttu-id="5d039-109">將事件訊息寫入至 Windows 應用程式記錄。</span><span class="sxs-lookup"><span data-stu-id="5d039-109">Writing an event message to the Windows application log.</span></span>  
  
     <span data-ttu-id="5d039-110">這個回應只用於失敗的作業。</span><span class="sxs-lookup"><span data-stu-id="5d039-110">You can use this response only for failed jobs.</span></span>  
  
-   <span data-ttu-id="5d039-111">自動刪除作業。</span><span class="sxs-lookup"><span data-stu-id="5d039-111">Automatically deleting the job.</span></span>  
  
     <span data-ttu-id="5d039-112">如果確定您將不再需要重新執行這個作業，請使用這個作業回應。</span><span class="sxs-lookup"><span data-stu-id="5d039-112">Use this job response if you are certain that you do not need to rerun this job.</span></span>  
  
 <span data-ttu-id="5d039-113">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="5d039-113">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5d039-114">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="5d039-114">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5d039-115">安全性</span><span class="sxs-lookup"><span data-stu-id="5d039-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5d039-116">**若要使用下列項目指定作業回應：**</span><span class="sxs-lookup"><span data-stu-id="5d039-116">**To specify job responses, using:**</span></span>  
  
     [<span data-ttu-id="5d039-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5d039-117">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="5d039-118">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="5d039-118">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5d039-119">開始之前</span><span class="sxs-lookup"><span data-stu-id="5d039-119">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5d039-120">Security</span><span class="sxs-lookup"><span data-stu-id="5d039-120">Security</span></span>  
 <span data-ttu-id="5d039-121">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5d039-121">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="5d039-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5d039-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-automatically-delete-a-job"></a><span data-ttu-id="5d039-123">若要自動刪除作業</span><span class="sxs-lookup"><span data-stu-id="5d039-123">To automatically delete a job</span></span>  
  
1.  <span data-ttu-id="5d039-124">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="5d039-124">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="5d039-125">展開 **[SQL Server Agent]**，展開 **[作業]**，以滑鼠右鍵按一下要編輯的作業，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="5d039-125">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to edit, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="5d039-126">選取 **[通知]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="5d039-126">Select the **Notifications** page.</span></span>  
  
4.  <span data-ttu-id="5d039-127">選取 **[自動刪除作業]**，然後選擇下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="5d039-127">Check **Automatically delete job**, and choose one of the following:</span></span>  
  
    -   <span data-ttu-id="5d039-128">按一下 **[當作業成功時]** ，以便在作業順利完成時刪除作業狀態。</span><span class="sxs-lookup"><span data-stu-id="5d039-128">Click **When the job succeeds** to delete the job status when it has completed successfully.</span></span>  
  
    -   <span data-ttu-id="5d039-129">按一下 **[當作業失敗時]** ，以便在作業未順利完成時刪除作業。</span><span class="sxs-lookup"><span data-stu-id="5d039-129">Click **When the job fails** to delete the job when it has completed unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="5d039-130">按一下 **[作業完成時]** ，不管完成狀態為何都刪除作業。</span><span class="sxs-lookup"><span data-stu-id="5d039-130">Click **When the job completes** to delete the job regardless of completion status.</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="5d039-131">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="5d039-131">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="5d039-132">**若要自動刪除作業**</span><span class="sxs-lookup"><span data-stu-id="5d039-132">**To automatically delete a job**</span></span>  
  
 <span data-ttu-id="5d039-133">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `DeleteLevel` 類別的 `Job` 屬性。</span><span class="sxs-lookup"><span data-stu-id="5d039-133">Use the `DeleteLevel` property of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="5d039-134">如需詳細資訊，請參閱 [SQL Server 管理物件 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5d039-134">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
  
  
