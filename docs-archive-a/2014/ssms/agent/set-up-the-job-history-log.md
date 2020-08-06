---
title: 設定作業記錄 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 018e5c49-d3a0-4504-851a-f70996a34bb7
author: stevestein
ms.author: sstein
ms.openlocfilehash: cb42e1daaee8a3a9e5ae9cc3c09a8cc42dcbff56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686751"
---
# <a name="set-up-the-job-history-log"></a><span data-ttu-id="482a3-102">Set Up the Job History Log</span><span class="sxs-lookup"><span data-stu-id="482a3-102">Set Up the Job History Log</span></span>
  <span data-ttu-id="482a3-103">本主題描述如何設定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="482a3-103">This topic describes how to set up the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history log.</span></span>  
  
-   <span data-ttu-id="482a3-104">**開始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="482a3-104">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="482a3-105">**若要使用下列項目設定作業記錄：**  [SQL Server Management Studio](#SSMS)</span><span class="sxs-lookup"><span data-stu-id="482a3-105">**To setup the job history log, using:**  [SQL Server Management Studio](#SSMS)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="482a3-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="482a3-106">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="482a3-107">Security</span><span class="sxs-lookup"><span data-stu-id="482a3-107">Security</span></span>  
 <span data-ttu-id="482a3-108">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="482a3-108">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="482a3-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="482a3-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="482a3-110">**若要設定作業記錄**</span><span class="sxs-lookup"><span data-stu-id="482a3-110">**To set up the job history log**</span></span>  
  
1.  <span data-ttu-id="482a3-111">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="482a3-111">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="482a3-112">以滑鼠右鍵按一下 [SQL Server Agent]\*\*\*\*，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="482a3-112">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="482a3-113">在 **[SQL Server Agent 屬性]** 對話方塊中，選取 **[記錄]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="482a3-113">In the **SQL Server Agent Properties** dialog box, select the **History** page.</span></span>  
  
4.  <span data-ttu-id="482a3-114">選擇下列選項：</span><span class="sxs-lookup"><span data-stu-id="482a3-114">Choose from the following options:</span></span>  
  
    1.  <span data-ttu-id="482a3-115">核取 **[限制作業記錄大小]**，然後輸入作業記錄的最大資料列數，以及每一個作業的最大資料列數。</span><span class="sxs-lookup"><span data-stu-id="482a3-115">Check **Limit size of job history log**, and then type the maximum number of rows for the job history log, and the maximum number of rows per job.</span></span>  
  
    2.  <span data-ttu-id="482a3-116">核取 **[自動移除代理程式記錄]**，並指定時間週期，比此週期要舊的記錄將會從記錄清除。</span><span class="sxs-lookup"><span data-stu-id="482a3-116">Check **Automatically remove agent history**, and specify a time period, such that history older than this period will be purged from the log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="482a3-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="482a3-117">See Also</span></span>  
 <span data-ttu-id="482a3-118">[實作作業](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="482a3-118">[Implement Jobs](implement-jobs.md) </span></span>  
 <span data-ttu-id="482a3-119">[監視作業活動](monitor-job-activity.md) </span><span class="sxs-lookup"><span data-stu-id="482a3-119">[Monitor Job Activity](monitor-job-activity.md) </span></span>  
 [<span data-ttu-id="482a3-120">建立作業</span><span class="sxs-lookup"><span data-stu-id="482a3-120">Create Jobs</span></span>](create-jobs.md)  
  
  
