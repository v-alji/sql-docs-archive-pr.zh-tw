---
title: 編輯警示 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], modifying
- modifying alerts
ms.assetid: f518e528-cc8f-446a-b37d-98505b86e430
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1eae606b3c2ca4c18d088e650e774986d4e31387
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596997"
---
# <a name="edit-an-alert"></a><span data-ttu-id="7474a-102">編輯警示</span><span class="sxs-lookup"><span data-stu-id="7474a-102">Edit an Alert</span></span>
  <span data-ttu-id="7474a-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或，在中編輯 Agent 警示 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7474a-103">This topic describes how to edit a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="7474a-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="7474a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7474a-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="7474a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7474a-106">安全性</span><span class="sxs-lookup"><span data-stu-id="7474a-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7474a-107">**若要使用下列項目編輯警示：**</span><span class="sxs-lookup"><span data-stu-id="7474a-107">**To edit an alert, using:**</span></span>  
  
     [<span data-ttu-id="7474a-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7474a-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7474a-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7474a-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7474a-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="7474a-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7474a-111">Security</span><span class="sxs-lookup"><span data-stu-id="7474a-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7474a-112">權限</span><span class="sxs-lookup"><span data-stu-id="7474a-112">Permissions</span></span>  
 <span data-ttu-id="7474a-113">依預設， **系統管理員 (sysadmin)** 固定伺服器角色的成員可以編輯警示中的資訊。</span><span class="sxs-lookup"><span data-stu-id="7474a-113">By default, members of the **sysadmin** fixed server role can edit information in an alert.</span></span> <span data-ttu-id="7474a-114">其他使用者必須被授與 **msdb** 資料庫的 **SQLAgentOperatorRole** 固定資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="7474a-114">Other users must be granted the **SQLAgentOperatorRole** fixed database role in the **msdb** database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7474a-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7474a-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-edit-an-alert"></a><span data-ttu-id="7474a-116">若要編輯警示</span><span class="sxs-lookup"><span data-stu-id="7474a-116">To edit an alert</span></span>  
  
1.  <span data-ttu-id="7474a-117">在 **[物件總管]** 中，按一下加號，展開包含要編輯之警示的伺服器。</span><span class="sxs-lookup"><span data-stu-id="7474a-117">In **Object Explorer,** click the plus sign to expand the server containing the alert you want to edit.</span></span>  
  
2.  <span data-ttu-id="7474a-118">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="7474a-118">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="7474a-119">按一下加號展開 **[警示]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7474a-119">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="7474a-120">以滑鼠右鍵按一下要編輯的警示，並且選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7474a-120">Right-click the alert you want to edit and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="7474a-121">更新 **[一般]**、 **[回應]** 和 **[選項]** 頁面上的警示屬性。</span><span class="sxs-lookup"><span data-stu-id="7474a-121">Update the alert properties on the **General**, **Response**, and **Options** pages.</span></span>  
  
6.  <span data-ttu-id="7474a-122">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="7474a-122">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7474a-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7474a-123">Using Transact-SQL</span></span>  
  
#### <a name="to-edit-an-alert"></a><span data-ttu-id="7474a-124">若要編輯警示</span><span class="sxs-lookup"><span data-stu-id="7474a-124">To edit an alert</span></span>  
  
1.  <span data-ttu-id="7474a-125">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7474a-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7474a-126">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="7474a-126">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7474a-127">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="7474a-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the enabled setting of Test Alert to 0  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_alert  
        @name = N'Test Alert',  
        @enabled = 0 ;  
    GO  
    ```  
  
 <span data-ttu-id="7474a-128">如需詳細資訊，請參閱[sp_update_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7474a-128">For more information, see [sp_update_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql).</span></span>  
  
  
