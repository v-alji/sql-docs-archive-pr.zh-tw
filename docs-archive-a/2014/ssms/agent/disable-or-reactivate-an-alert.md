---
title: 停用或重新啟用警示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], reactivating
- deleting alerts
- canceling alerts
- dropping alerts
- disabling alerts
- alerts [SQL Server], disabling
- reactivating alerts
- removing alerts
ms.assetid: 4cb37dc6-1134-405d-8590-58b44dcf63b2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3eec4ea7288f4847c0e9b861d80f23eb9c9ddba8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703754"
---
# <a name="disable-or-reactivate-an-alert"></a><span data-ttu-id="76f93-102">停用或重新啟用警示</span><span class="sxs-lookup"><span data-stu-id="76f93-102">Disable or Reactivate an Alert</span></span>
  <span data-ttu-id="76f93-103">本主題描述如何使用或，在中停用或重新開機 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 警示 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="76f93-103">This topic describes how to disable or reactivate a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="76f93-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="76f93-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="76f93-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="76f93-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="76f93-106">安全性</span><span class="sxs-lookup"><span data-stu-id="76f93-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="76f93-107">**若要使用下列項目停用或重新啟動警示：**</span><span class="sxs-lookup"><span data-stu-id="76f93-107">**To disable or reactivate an alert, using:**</span></span>  
  
     [<span data-ttu-id="76f93-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="76f93-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="76f93-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="76f93-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="76f93-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="76f93-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="76f93-111">Security</span><span class="sxs-lookup"><span data-stu-id="76f93-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="76f93-112">權限</span><span class="sxs-lookup"><span data-stu-id="76f93-112">Permissions</span></span>  
 <span data-ttu-id="76f93-113">依預設， **系統管理員 (sysadmin)** 固定伺服器角色的成員可以編輯警示中的資訊。</span><span class="sxs-lookup"><span data-stu-id="76f93-113">By default, members of the **sysadmin** fixed server role can edit information in an alert.</span></span> <span data-ttu-id="76f93-114">其他使用者必須被授與 **msdb** 資料庫的 **SQLAgentOperatorRole** 固定資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="76f93-114">Other users must be granted the **SQLAgentOperatorRole** fixed database role in the **msdb** database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="76f93-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="76f93-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-or-reactivate-an-alert"></a><span data-ttu-id="76f93-116">若要停用或重新啟動警示</span><span class="sxs-lookup"><span data-stu-id="76f93-116">To disable or reactivate an alert</span></span>  
  
1.  <span data-ttu-id="76f93-117">在 **[物件總管]** 中，按一下加號，展開包含您想要停用或重新啟動之警示的伺服器。</span><span class="sxs-lookup"><span data-stu-id="76f93-117">In **Object Explorer**, click the plus sign to expand server that contains the alert you wish to disable or reactivate.</span></span>  
  
2.  <span data-ttu-id="76f93-118">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="76f93-118">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="76f93-119">按一下加號展開 **[警示]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="76f93-119">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="76f93-120">以滑鼠右鍵按一下您想要啟用的警示，然後選取 [啟用]\*\*\*\*。若要停用警示，請以滑鼠右鍵按一下您想要停用的警示，然後選取 [停用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="76f93-120">Right-click the alert you wish to enable and select **Enable** To disable an alert, right-click the alert you want to disable and select **Disable**.</span></span>  
  
5.  <span data-ttu-id="76f93-121">畫面上會顯示 **[停用警示]** 或 **[啟用警示]** 對話方塊，並顯示處理的狀態。</span><span class="sxs-lookup"><span data-stu-id="76f93-121">The **Disable Alert** or **Enable Alert** dialog box displays showing the status of the process.</span></span> <span data-ttu-id="76f93-122">完成後，請按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="76f93-122">When finished, click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="76f93-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="76f93-123">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-or-reactivate-an-alert"></a><span data-ttu-id="76f93-124">若要停用或重新啟動警示</span><span class="sxs-lookup"><span data-stu-id="76f93-124">To disable or reactivate an alert</span></span>  
  
1.  <span data-ttu-id="76f93-125">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="76f93-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="76f93-126">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="76f93-126">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="76f93-127">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="76f93-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the enabled setting of Test Alert to 0  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_alert  
        @name = N'Test Alert',  
        @enabled = 0 ;  
    GO  
    ```  
  
 <span data-ttu-id="76f93-128">如需詳細資訊，請參閱[sp_update_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="76f93-128">For more information, see [sp_update_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql).</span></span>  
  
  
