---
title: 設定作業執行關機 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
- SQL Server Agent jobs, execution shutdowns
ms.assetid: ac23e88f-53fc-41de-bb16-0c27c002d5a5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0e60807676c3c54faf1d44de318ff0a31c2e20b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599317"
---
# <a name="set-job-execution-shutdown-sql-server-management-studio"></a><span data-ttu-id="0215b-102">設定作業執行關機 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="0215b-102">Set Job Execution Shutdown (SQL Server Management Studio)</span></span>
  <span data-ttu-id="0215b-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用，在中設定 agent 等待執行中作業完成的時間，然後 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent 本身才會完成 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0215b-103">This topic describes how to set the time that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will wait for executing jobs to finish before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent itself finishes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="0215b-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="0215b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0215b-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="0215b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0215b-106">安全性</span><span class="sxs-lookup"><span data-stu-id="0215b-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0215b-107">**若要使用下列項目設定 SQL Server Agent 作業的關機時間：**</span><span class="sxs-lookup"><span data-stu-id="0215b-107">**To set a shutdown time for a SQL Server Agent job, using:**</span></span>  
  
     [<span data-ttu-id="0215b-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0215b-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0215b-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="0215b-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0215b-110">Security</span><span class="sxs-lookup"><span data-stu-id="0215b-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0215b-111">權限</span><span class="sxs-lookup"><span data-stu-id="0215b-111">Permissions</span></span>  
 <span data-ttu-id="0215b-112">根據預設，**系統管理員**固定伺服器角色成員可以設定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 等待執行中作業完成的等候時間，之後 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 便會自行結束。</span><span class="sxs-lookup"><span data-stu-id="0215b-112">By default, members of the **sysadmin** fixed server role can set the time that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will wait for executing jobs to finish before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent itself finishes.</span></span> <span data-ttu-id="0215b-113">其他使用者必須被授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **資料庫的下列其中一個** Agent 固定資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="0215b-113">Other users must be granted one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the **msdb** database:</span></span>  
  
-   <span data-ttu-id="0215b-114">**SQLAgentUserRole**</span><span class="sxs-lookup"><span data-stu-id="0215b-114">**SQLAgentUserRole**</span></span>  
  
-   <span data-ttu-id="0215b-115">**SQLAgentReaderRole**</span><span class="sxs-lookup"><span data-stu-id="0215b-115">**SQLAgentReaderRole**</span></span>  
  
-   <span data-ttu-id="0215b-116">**SQLAgentOperatorRole**</span><span class="sxs-lookup"><span data-stu-id="0215b-116">**SQLAgentOperatorRole**</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0215b-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0215b-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-job-execution-shutdown"></a><span data-ttu-id="0215b-118">若要設定作業執行關機</span><span class="sxs-lookup"><span data-stu-id="0215b-118">To set job execution shutdown</span></span>  
  
1.  <span data-ttu-id="0215b-119">在 **[物件總管]** 中，按一下加號，展開要設定作業執行關機間隔的伺服器。</span><span class="sxs-lookup"><span data-stu-id="0215b-119">In **Object Explorer,** , click the plus sign to expand the server where you want to set a job execution shutdown interval.</span></span>  
  
2.  <span data-ttu-id="0215b-120">以滑鼠右鍵按一下**SQL Server Agent** ，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="0215b-120">Right-click **SQL Server Agent** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="0215b-121">在 **[選取頁面]** 底下，選取 **[作業的系統]**。</span><span class="sxs-lookup"><span data-stu-id="0215b-121">Under **Select a page**, select **Job System**.</span></span>  
  
4.  <span data-ttu-id="0215b-122">設定 [關機逾時間隔]\*\*\*\* \(以秒為單位)，以增加或減少關機的逾時間隔。</span><span class="sxs-lookup"><span data-stu-id="0215b-122">Set the **Shutdown time-out interval** in seconds to increase or decrease the shutdown time-out interval.</span></span> <span data-ttu-id="0215b-123">這決定了在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 自行結束前， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會等待執行中作業完成的時間。</span><span class="sxs-lookup"><span data-stu-id="0215b-123">This determines how long [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will wait for executing jobs to finish before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent itself finishes.</span></span>  
  
  
