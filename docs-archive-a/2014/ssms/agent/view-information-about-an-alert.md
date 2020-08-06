---
title: 檢視有關警示的資訊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- viewing alerts
- alerts [SQL Server], viewing
- displaying alerts
- status information [SQL Server], alerts
ms.assetid: a0e3a8c4-e3c2-42a5-b2f8-aa06061d3fa6
author: stevestein
ms.author: sstein
ms.openlocfilehash: ee72512a507299e71f13fee689709a9403bb04e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594322"
---
# <a name="view-information-about-an-alert"></a><span data-ttu-id="95522-102">檢視有關警示的資訊</span><span class="sxs-lookup"><span data-stu-id="95522-102">View Information About an Alert</span></span>
  <span data-ttu-id="95522-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或，在中查看 Agent 警示的相關資訊 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="95522-103">This topic describes how to view information about [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="95522-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="95522-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="95522-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="95522-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="95522-106">安全性</span><span class="sxs-lookup"><span data-stu-id="95522-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="95522-107">**若要使用下列項目檢視有關警示的資訊：**</span><span class="sxs-lookup"><span data-stu-id="95522-107">**To view information about an alert, using:**</span></span>  
  
     [<span data-ttu-id="95522-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="95522-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="95522-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="95522-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="95522-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="95522-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="95522-111">Security</span><span class="sxs-lookup"><span data-stu-id="95522-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="95522-112">權限</span><span class="sxs-lookup"><span data-stu-id="95522-112">Permissions</span></span>  
 <span data-ttu-id="95522-113">依預設， **系統管理員 (sysadmin)** 固定伺服器角色的成員可以檢視警示的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="95522-113">By default, members of the **sysadmin** fixed server role can view information about an alert.</span></span> <span data-ttu-id="95522-114">其他使用者必須被授與 **msdb** 資料庫的 **SQLAgentOperatorRole** 固定資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="95522-114">Other users must be granted the **SQLAgentOperatorRole** fixed database role in the **msdb** database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="95522-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="95522-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-information-about-an-alert"></a><span data-ttu-id="95522-116">若要檢視有關警示的資訊</span><span class="sxs-lookup"><span data-stu-id="95522-116">To view information about an alert</span></span>  
  
1.  <span data-ttu-id="95522-117">在 **[物件總管]** 中，按一下加號，展開要檢視警示相關資訊的伺服器。</span><span class="sxs-lookup"><span data-stu-id="95522-117">In **Object Explorer,** click the plus sign to expand the server where you want to view information about an alert.</span></span>  
  
2.  <span data-ttu-id="95522-118">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="95522-118">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="95522-119">按一下加號展開 **[警示]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="95522-119">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="95522-120">以滑鼠右鍵按一下您想要檢視其資訊的警示，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="95522-120">Right-click the alert that has the information you want to view and select **Properties**.</span></span>  
  
     <span data-ttu-id="95522-121">如需 [<警示名稱> 警示屬性]__\*\*\*\* 對話方塊中之可用選項的詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="95522-121">For more information on the available options contained in the _alert_name_**alert properties** dialog box, see:</span></span>  
  
    -   [<span data-ttu-id="95522-122">警示屬性-新增警示 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="95522-122">Alert Properties-New Alert &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [<span data-ttu-id="95522-123">警示屬性-新增警示 &#40;回應頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="95522-123">Alert Properties-New Alert &#40;Response Page&#41;</span></span>](alert-properties-new-alert-response-page.md)  
  
    -   [<span data-ttu-id="95522-124">警示屬性：新增警示 &#40;選項頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="95522-124">Alert Properties: New Alert &#40;Options Page&#41;</span></span>](alert-properties-new-alert-options-page.md)  
  
    -   [<span data-ttu-id="95522-125">警示屬性 &#40;記錄頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="95522-125">Alert Properties &#40;History Page&#41;</span></span>](alert-properties-history-page.md)  
  
5.  <span data-ttu-id="95522-126">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="95522-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="95522-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="95522-127">Using Transact-SQL</span></span>  
  
#### <a name="to-view-information-about-an-alert"></a><span data-ttu-id="95522-128">若要檢視有關警示的資訊</span><span class="sxs-lookup"><span data-stu-id="95522-128">To view information about an alert</span></span>  
  
1.  <span data-ttu-id="95522-129">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="95522-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="95522-130">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="95522-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="95522-131">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="95522-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- reports information about the Demo: Sev. 25 Errors alert  
    -- This example assumes that the 'Demo: Sev. 25 Errors' alert exists.  
    USE msdb ;  
    GO  
  
    EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors'  
    GO  
    ```  
  
 <span data-ttu-id="95522-132">如需詳細資訊，請參閱[sp_help_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-alert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="95522-132">For more information, see [sp_help_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-alert-transact-sql).</span></span>  
  
  
