---
title: 刪除警示 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], deleting
- deleting alerts
- canceling alerts
- dropping alerts
- disabling alerts
- removing alerts
ms.assetid: c982b208-e2d1-4d34-8cee-940b9baf6586
author: stevestein
ms.author: sstein
ms.openlocfilehash: 15fdae19b150a5a06a32e91ec1947a0acfa5f900
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598110"
---
# <a name="delete-an-alert"></a><span data-ttu-id="38000-102">Delete an Alert</span><span class="sxs-lookup"><span data-stu-id="38000-102">Delete an Alert</span></span>
  <span data-ttu-id="38000-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或，在中刪除 Agent 警示 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="38000-103">This topic describes how to delete [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="38000-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="38000-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="38000-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="38000-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="38000-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="38000-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="38000-107">安全性</span><span class="sxs-lookup"><span data-stu-id="38000-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="38000-108">**若要使用下列項目刪除警示：**</span><span class="sxs-lookup"><span data-stu-id="38000-108">**To delete an alert, using:**</span></span>  
  
     [<span data-ttu-id="38000-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="38000-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="38000-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="38000-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="38000-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="38000-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="38000-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="38000-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="38000-113">移除警示也會移除警示的任何相關通知。</span><span class="sxs-lookup"><span data-stu-id="38000-113">Removing an alert also removes any notifications associated with the alert.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="38000-114">Security</span><span class="sxs-lookup"><span data-stu-id="38000-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="38000-115">權限</span><span class="sxs-lookup"><span data-stu-id="38000-115">Permissions</span></span>  
 <span data-ttu-id="38000-116">依預設，只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠刪除警示。</span><span class="sxs-lookup"><span data-stu-id="38000-116">By default, only members of the **sysadmin** fixed server role can delete alerts.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="38000-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="38000-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-an-alert"></a><span data-ttu-id="38000-118">若要刪除警示</span><span class="sxs-lookup"><span data-stu-id="38000-118">To delete an alert</span></span>  
  
1.  <span data-ttu-id="38000-119">在 **[物件總管]** 中，按一下加號展開伺服器，此伺服器包含要刪除的 SQL Server Agent 警示。</span><span class="sxs-lookup"><span data-stu-id="38000-119">In **Object Explorer,** click the plus sign to expand the server that contains the SQL Server Agent alert that you want to delete.</span></span>  
  
2.  <span data-ttu-id="38000-120">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="38000-120">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="38000-121">按一下加號展開 **[警示]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="38000-121">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="38000-122">在您要刪除的警示上按一下滑鼠右鍵，然後選取 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38000-122">Right-click the alert you want to delete and select **Delete**.</span></span>  
  
5.  <span data-ttu-id="38000-123">在 **[刪除物件]** 對話方塊中，確認已選取正確的警示，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="38000-123">In the **Delete Object** dialog box, confirm that the correct alert is selected and click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="38000-124">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="38000-124">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-an-alert"></a><span data-ttu-id="38000-125">若要刪除警示</span><span class="sxs-lookup"><span data-stu-id="38000-125">To delete an alert</span></span>  
  
1.  <span data-ttu-id="38000-126">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="38000-126">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="38000-127">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="38000-127">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="38000-128">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="38000-128">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- deletes the SQL Server Agent alert called 'Test Alert.'  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_alert  
       @name = N'Test Alert' ;  
    GO  
    ```  
  
 <span data-ttu-id="38000-129">如需詳細資訊，請參閱 s[sp_delete_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-alert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="38000-129">For more information, see s[sp_delete_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-alert-transact-sql).</span></span>  
  
  
