---
title: 設定 CPU 閒置與持續時間 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CPU [SQL Server], idle conditions
- time [SQL Server], CPU idle and duration
- duration of CPU idle [SQL Server]
- SQL Server Agent, CPU idle conditions
- idle time [SQL Server]
ms.assetid: 8647b465-d899-4cc7-9640-134a506d0a2e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1660f6d70977b8f590a18adf952a6a19f32a26cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710097"
---
# <a name="set-cpu-idle-time-and-duration-sql-server-management-studio"></a><span data-ttu-id="3cd0d-102">設定 CPU 閒置與持續時間 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3cd0d-102">Set CPU Idle Time and Duration (SQL Server Management Studio)</span></span>
  <span data-ttu-id="3cd0d-103">本主題說明如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]定義伺服器的 CPU 閒置條件。</span><span class="sxs-lookup"><span data-stu-id="3cd0d-103">This topic explains how to define the CPU idle condition for your server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="3cd0d-104">CPU 閒置定義會影響 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 回應事件的方式。</span><span class="sxs-lookup"><span data-stu-id="3cd0d-104">The CPU idle definition influences how [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent responds to events.</span></span> <span data-ttu-id="3cd0d-105">例如，假設您將 CPU 閒置條件定義為平均 CPU 使用量低於百分之十且此狀態持續 10 分鐘。</span><span class="sxs-lookup"><span data-stu-id="3cd0d-105">For example, suppose that you define the CPU idle condition as when the average CPU usage falls below 10 percent and remains at this level for 10 minutes.</span></span> <span data-ttu-id="3cd0d-106">然後，如果您已定義每當伺服器 CPU 達到閒置條件時要執行的作業，當 CPU 使用量低於百分之十且此狀態持續 10 分鐘，將會執行該作業。</span><span class="sxs-lookup"><span data-stu-id="3cd0d-106">Then if you have defined jobs to execute whenever the server CPU reaches an idle condition, the job will start when the CPU usage falls below 10 percent and remains at that level for 10 minutes.</span></span> <span data-ttu-id="3cd0d-107">如果此作業會明顯影響伺服器的效能，則如何定義 CPU 閒置條件就很重要。</span><span class="sxs-lookup"><span data-stu-id="3cd0d-107">If this is a job that significantly impacts the performance of your server, how you define the CPU idle condition is important.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3cd0d-108">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3cd0d-108">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-cpu-idle-time-and-duration"></a><span data-ttu-id="3cd0d-109">若要設定 CPU 閒置時間與期間</span><span class="sxs-lookup"><span data-stu-id="3cd0d-109">To set CPU idle time and duration</span></span>  
  
1.  <span data-ttu-id="3cd0d-110">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="3cd0d-110">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="3cd0d-111">以滑鼠右鍵按一下 [SQL Server Agent]\*\*\*\*，按一下 [屬性]\*\*\*\*，然後選取 [進階]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="3cd0d-111">Right-click **SQL Server Agent**, click **Properties**, and select the **Advanced** page.</span></span>  
  
3.  <span data-ttu-id="3cd0d-112">在 **[閒置 CPU 的條件]** 下方，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="3cd0d-112">Under **Idle CPU condition**, do the following:</span></span>  
  
    -   <span data-ttu-id="3cd0d-113">核取 **[定義閒置 CPU 的條件]**。</span><span class="sxs-lookup"><span data-stu-id="3cd0d-113">Check **Define idle CPU condition.**</span></span>  
  
    -   <span data-ttu-id="3cd0d-114">在 [平均 CPU 使用量低於]\*\*\*\* \(所有 CPU) 方塊中指定百分比。</span><span class="sxs-lookup"><span data-stu-id="3cd0d-114">Specify a percentage for the **Average CPU usage falls below** (across all CPUs) box.</span></span> <span data-ttu-id="3cd0d-115">這樣會設定 CPU 必須低於此使用量才會視為閒置。</span><span class="sxs-lookup"><span data-stu-id="3cd0d-115">This sets the usage level that the CPU must fall below before it is considered idle.</span></span>  
  
    -   <span data-ttu-id="3cd0d-116">在 **[並且持續低於此狀態達]** 方塊中指定秒數。</span><span class="sxs-lookup"><span data-stu-id="3cd0d-116">Specify a number of seconds for the **And remains below this level for** box.</span></span> <span data-ttu-id="3cd0d-117">這樣會設定此期間必須維持最小 CPU 用量才會視為閒置。</span><span class="sxs-lookup"><span data-stu-id="3cd0d-117">This sets the duration that the minimum CPU usage must remain at before it is considered idle.</span></span>  
  
  
