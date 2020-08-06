---
title: 設定 SQL Server Agent Mail 使用 Database Mail | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], SQL Server Agent Mail
- SQL Server Agent Mail
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
author: stevestein
ms.author: sstein
ms.openlocfilehash: 31d116c0bc8d7e148fc2ef6d2e344400516ad923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686979"
---
# <a name="configure-sql-server-agent-mail-to-use-database-mail"></a><span data-ttu-id="0a4e0-102">設定 SQL Server Agent Mail 使用 Database Mail</span><span class="sxs-lookup"><span data-stu-id="0a4e0-102">Configure SQL Server Agent Mail to Use Database Mail</span></span>
  <span data-ttu-id="0a4e0-103">本主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中將 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Agent 設定為使用 Database Mail 來傳送通知和警示。</span><span class="sxs-lookup"><span data-stu-id="0a4e0-103">This topic describes how to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to use Database Mail to send notification and alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="0a4e0-104">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="0a4e0-104">**Before you begin:**</span></span>  
  
-   [<span data-ttu-id="0a4e0-105">先決條件</span><span class="sxs-lookup"><span data-stu-id="0a4e0-105">Prerequisites</span></span>](#Prerequisites)  
  
-   [<span data-ttu-id="0a4e0-106">安全性</span><span class="sxs-lookup"><span data-stu-id="0a4e0-106">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="0a4e0-107">使用 SQL Server Management Studio 將 SQL Server Agent 設定為使用 Database Mail</span><span class="sxs-lookup"><span data-stu-id="0a4e0-107">To Configure SQL Server Agent to use Database Mail, using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="0a4e0-108">後續工作</span><span class="sxs-lookup"><span data-stu-id="0a4e0-108">Follow-up Tasks</span></span>](#Follow_Up)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0a4e0-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="0a4e0-109">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="0a4e0-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="0a4e0-110">Prerequisites</span></span>  
  
-   <span data-ttu-id="0a4e0-111">啟用 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="0a4e0-111">Enable Database Mail.</span></span>  
  
-   <span data-ttu-id="0a4e0-112">對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務帳戶建立要使用的 Database Mail 帳戶。</span><span class="sxs-lookup"><span data-stu-id="0a4e0-112">Create a Database Mail account for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account to use.</span></span>  
  
-   <span data-ttu-id="0a4e0-113">建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務帳戶要使用的 Database Mail 設定檔，並新增使用者至 **msdb** 資料庫中的 **DatabaseMailUserRole** 。</span><span class="sxs-lookup"><span data-stu-id="0a4e0-113">Create a Database Mail profile for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account to use and add the user to the **DatabaseMailUserRole** in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="0a4e0-114">將設定檔設為 **msdb** 資料庫的預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="0a4e0-114">Set the profile as the default profile for the **msdb** database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0a4e0-115">Security</span><span class="sxs-lookup"><span data-stu-id="0a4e0-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0a4e0-116">權限</span><span class="sxs-lookup"><span data-stu-id="0a4e0-116">Permissions</span></span>  
 <span data-ttu-id="0a4e0-117">建立設定檔帳戶以及執行預存程序的使用者，應該是系統管理員 (sysadmin) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="0a4e0-117">The user creating the profiles accounts and executing stored procedures should be a member of the sysadmin fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0a4e0-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0a4e0-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="0a4e0-119">**設定 SQL Server Agent 使用 Database Mail**</span><span class="sxs-lookup"><span data-stu-id="0a4e0-119">**To configure SQL Server Agent to use Database Mail**</span></span>  
  
-   <span data-ttu-id="0a4e0-120">在 [物件總管] 中，展開 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a4e0-120">In Object Explorer, expand a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="0a4e0-121">以滑鼠右鍵按一下 [SQL Server Agent]\*\*\*\*，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0a4e0-121">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
-   <span data-ttu-id="0a4e0-122">按一下 **[警示系統]**。</span><span class="sxs-lookup"><span data-stu-id="0a4e0-122">Click **Alert System**.</span></span>  
  
-   <span data-ttu-id="0a4e0-123">選取 **[啟用郵件設定檔]**。</span><span class="sxs-lookup"><span data-stu-id="0a4e0-123">Select **Enable Mail Profile**.</span></span>  
  
-   <span data-ttu-id="0a4e0-124">在 **[郵件系統]** 清單中，選取 **[Database Mail]**。</span><span class="sxs-lookup"><span data-stu-id="0a4e0-124">In the **Mail system** list, select **Database Mail**.</span></span>  
  
-   <span data-ttu-id="0a4e0-125">在 **[郵件設定檔]** 清單中，選取 Database Mail 的郵件設定檔。</span><span class="sxs-lookup"><span data-stu-id="0a4e0-125">In the **Mail profile list**, select a mail profile for Database Mail.</span></span>  
  
-   <span data-ttu-id="0a4e0-126">重新啟動 SQL Server Agent。</span><span class="sxs-lookup"><span data-stu-id="0a4e0-126">Restart SQL Server Agent.</span></span>  
  
##  <a name="follow-up-tasks"></a><a name="Follow_Up"></a> <span data-ttu-id="0a4e0-127">後續工作</span><span class="sxs-lookup"><span data-stu-id="0a4e0-127">Follow-up Tasks</span></span>  
 <span data-ttu-id="0a4e0-128">需要進行下列工作，才能完成將 Agent 設定為傳送警示和通知的作業。</span><span class="sxs-lookup"><span data-stu-id="0a4e0-128">The following tasks are necessary to complete the configuration of Agent to send alerts and notifications.</span></span>  
  
-   [<span data-ttu-id="0a4e0-129">警示</span><span class="sxs-lookup"><span data-stu-id="0a4e0-129">Alerts</span></span>](../../ssms/agent/alerts.md)  
  
     <span data-ttu-id="0a4e0-130">將警示設定為在發生特定資料庫事件或作業系統狀況時通知操作員。</span><span class="sxs-lookup"><span data-stu-id="0a4e0-130">Alerts can be configured to notify an operator of a particular database event or operating system condition.</span></span>  
  
-   [<span data-ttu-id="0a4e0-131">運算子</span><span class="sxs-lookup"><span data-stu-id="0a4e0-131">Operators</span></span>](../../ssms/agent/operators.md)  
  
     <span data-ttu-id="0a4e0-132">操作員是可接收電子通知之人員或群組使用的別名</span><span class="sxs-lookup"><span data-stu-id="0a4e0-132">Operators are aliases for people or groups that can receive electronic notification</span></span>  
  
  
