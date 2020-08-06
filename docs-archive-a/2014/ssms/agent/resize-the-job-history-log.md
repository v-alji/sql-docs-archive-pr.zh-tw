---
title: 調整作業記錄大小 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- resizing job history log
- size [SQL Server], job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: ddee1ce8-9d1b-4017-9894-bf7256aed95d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4c25cc43295d47b2bc19d48b5b257dbbe6bcfe9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594327"
---
# <a name="resize-the-job-history-log"></a><span data-ttu-id="463fc-102">調整作業記錄大小</span><span class="sxs-lookup"><span data-stu-id="463fc-102">Resize the Job History Log</span></span>
  <span data-ttu-id="463fc-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用，在中設定 Agent 作業記錄的大小限制 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="463fc-103">This topic describes how to set size limits for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history logs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="463fc-104">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="463fc-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="463fc-105">安全性</span><span class="sxs-lookup"><span data-stu-id="463fc-105">Security</span></span>](#Security)  
  
-   <span data-ttu-id="463fc-106">**若要使用下列項目設定作業記錄的大小限制：**</span><span class="sxs-lookup"><span data-stu-id="463fc-106">**To set size limits for job history logs, using:**</span></span>  
  
     [<span data-ttu-id="463fc-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="463fc-107">SQL Server Management Studio</span></span>](#SSMS)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="463fc-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="463fc-108">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="463fc-109">Security</span><span class="sxs-lookup"><span data-stu-id="463fc-109">Security</span></span>  
 <span data-ttu-id="463fc-110">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="463fc-110">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="463fc-111">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="463fc-111">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-resize-the-job-history-log-based-on-raw-size"></a><span data-ttu-id="463fc-112">若要根據原始大小調整作業記錄大小</span><span class="sxs-lookup"><span data-stu-id="463fc-112">To resize the job history log based on raw size</span></span>  
  
1.  <span data-ttu-id="463fc-113">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="463fc-113">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="463fc-114">以滑鼠右鍵按一下 [SQL Server Agent]\*\*\*\*，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="463fc-114">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="463fc-115">選取 [記錄]\*\*\*\* 頁面，然後確認已選取 [限制作業記錄大小]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="463fc-115">Select the **History** page, and then confirm that **Limit size of job history log**is checked.</span></span>  
  
4.  <span data-ttu-id="463fc-116">在 **[最大作業記錄大小]** 方塊中，輸入作業記錄所允許的最大資料列數。</span><span class="sxs-lookup"><span data-stu-id="463fc-116">In the **Maximum job history log size** box, enter the maximum number of rows the job history log should allow.</span></span>  
  
5.  <span data-ttu-id="463fc-117">在 **[每項作業的作業記錄最大資料列數]** 方塊中，輸入作業所允許的最大作業記錄資料列數。</span><span class="sxs-lookup"><span data-stu-id="463fc-117">In the **Maximum job history rows per job** box, enter the maximum number of job history rows to allow for a job.</span></span>  
  
#### <a name="to-resize-the-job-history-log-based-on-time"></a><span data-ttu-id="463fc-118">若要根據時間調整作業記錄大小</span><span class="sxs-lookup"><span data-stu-id="463fc-118">To resize the job history log based on time</span></span>  
  
1.  <span data-ttu-id="463fc-119">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="463fc-119">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="463fc-120">以滑鼠右鍵按一下 [SQL Server Agent]\*\*\*\*，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="463fc-120">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="463fc-121">選取 **[記錄]** 頁面，然後按一下 **[自動移除代理程式記錄]**。</span><span class="sxs-lookup"><span data-stu-id="463fc-121">Select the **History** page, and then click **Automatically remove agent history**.</span></span>  
  
4.  <span data-ttu-id="463fc-122">選取適當的 [天]\*\*\*\*、[週]\*\*\*\* 或 [月]\*\*\*\* 數。</span><span class="sxs-lookup"><span data-stu-id="463fc-122">Select the appropriate number of **Days(s)**, **Week(s)**, or **Month(s)**.</span></span>  
  
  
