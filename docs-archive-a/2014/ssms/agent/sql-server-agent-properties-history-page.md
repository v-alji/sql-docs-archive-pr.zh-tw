---
title: SQL Server Agent 屬性 (記錄頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
author: stevestein
ms.author: sstein
ms.openlocfilehash: d67ff3da97e11292abcac03958fe1e423b35d7d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599308"
---
# <a name="sql-server-agent-properties-history-page"></a><span data-ttu-id="34d86-102">SQL Server Agent 屬性 (記錄頁面)</span><span class="sxs-lookup"><span data-stu-id="34d86-102">SQL Server Agent Properties (History Page)</span></span>
  <span data-ttu-id="34d86-103">使用此頁面來查看和修改管理 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務歷程記錄的設定。</span><span class="sxs-lookup"><span data-stu-id="34d86-103">Use this page to view and modify settings for managing the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service history log.</span></span>  
  
## <a name="options"></a><span data-ttu-id="34d86-104">選項</span><span class="sxs-lookup"><span data-stu-id="34d86-104">Options</span></span>  
 <span data-ttu-id="34d86-105">**限制作業記錄大小**</span><span class="sxs-lookup"><span data-stu-id="34d86-105">**Limit size of job history log**</span></span>  
 <span data-ttu-id="34d86-106">對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 在記錄中所保留的作業記錄資訊量加以設限。</span><span class="sxs-lookup"><span data-stu-id="34d86-106">Sets limits for the amount of job history information that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent retains in the log.</span></span>  
  
 <span data-ttu-id="34d86-107">**作業記錄大小上限 (以資料列為單位)**</span><span class="sxs-lookup"><span data-stu-id="34d86-107">**Maximum job history log size (in rows)**</span></span>  
 <span data-ttu-id="34d86-108">設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會保留的最大資料列數目。</span><span class="sxs-lookup"><span data-stu-id="34d86-108">Sets the maximum number of rows that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent retains.</span></span> <span data-ttu-id="34d86-109">當記錄成長至此資料列數目時，隨著新資料列的輸入， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會移除記錄中最舊的資料列。</span><span class="sxs-lookup"><span data-stu-id="34d86-109">When the log grows to contain this number of rows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent removes the oldest rows in the log as new rows are entered.</span></span>  
  
 <span data-ttu-id="34d86-110">**每項作業的作業記錄最大資料列數**</span><span class="sxs-lookup"><span data-stu-id="34d86-110">**Maximum job history rows per job**</span></span>  
 <span data-ttu-id="34d86-111">設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會為每項作業保留的最大資料列數目。</span><span class="sxs-lookup"><span data-stu-id="34d86-111">Sets the maximum number of rows that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent retains per job.</span></span> <span data-ttu-id="34d86-112">當特定作業的記錄成長至此資料列數目時，隨著新資料列的輸入， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會移除記錄中最舊的資料列。</span><span class="sxs-lookup"><span data-stu-id="34d86-112">When the history for a particular job grows to contain this number of rows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent removes the oldest rows in the log as new rows are entered.</span></span>  
  
 <span data-ttu-id="34d86-113">**移除代理程式記錄**</span><span class="sxs-lookup"><span data-stu-id="34d86-113">**Remove agent history**</span></span>  
 <span data-ttu-id="34d86-114">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會移除已存在於記錄中超過指定時間長度的項目。</span><span class="sxs-lookup"><span data-stu-id="34d86-114">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will remove entries that have been in the log longer than a specified length of time.</span></span> <span data-ttu-id="34d86-115">這是單次移除記錄的執行作業。</span><span class="sxs-lookup"><span data-stu-id="34d86-115">This is a one-time execution to remove the history.</span></span> <span data-ttu-id="34d86-116">如果需要重複的作業，請建立並排程含有清除作業的維護計畫。</span><span class="sxs-lookup"><span data-stu-id="34d86-116">If a reoccurring job is needed, create and schedule a maintenance plan with a cleanup job.</span></span>  
  
 <span data-ttu-id="34d86-117">**早於**</span><span class="sxs-lookup"><span data-stu-id="34d86-117">**Older than**</span></span>  
 <span data-ttu-id="34d86-118">設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會保留項目的時間。</span><span class="sxs-lookup"><span data-stu-id="34d86-118">Sets the amount of time that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will retain entries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34d86-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34d86-119">See Also</span></span>  
 [<span data-ttu-id="34d86-120">SQL Server Agent 錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="34d86-120">SQL Server Agent Error Log</span></span>](sql-server-agent-error-log.md)  
  
  
