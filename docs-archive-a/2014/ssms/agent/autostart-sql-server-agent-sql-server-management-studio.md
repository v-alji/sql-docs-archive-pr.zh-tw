---
title: 自動啟動 SQL Server Agent (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, starting
- autostart SQL Server Agent
ms.assetid: 2ea332da-0ede-4d2b-b122-c4c10eaca191
author: stevestein
ms.author: sstein
ms.openlocfilehash: a39c7c7a112370797a965cfa601bc07f983a7a37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597544"
---
# <a name="autostart-sql-server-agent-sql-server-management-studio"></a><span data-ttu-id="3ea9c-102">Autostart SQL Server Agent (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3ea9c-102">Autostart SQL Server Agent (SQL Server Management Studio)</span></span>
  <span data-ttu-id="3ea9c-103">本主題描述如何將 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 設定為在不預期地停止時自動重新開機 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-103">This topic describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to automatically restart if it should stop unexpectedly in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="3ea9c-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="3ea9c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3ea9c-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="3ea9c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3ea9c-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="3ea9c-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3ea9c-107">安全性</span><span class="sxs-lookup"><span data-stu-id="3ea9c-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="3ea9c-108">若要使用 SQL Server Management Studio，將 SQL Server Agent 設定為自動重新啟動</span><span class="sxs-lookup"><span data-stu-id="3ea9c-108">To configure SQL Server Agent to automatically restart, using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3ea9c-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="3ea9c-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3ea9c-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="3ea9c-110">Limitations and Restrictions</span></span>  
 <span data-ttu-id="3ea9c-111">只有當您擁有使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 節點的權限時，[物件總管] 才會顯示該節點。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-111">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3ea9c-112">Security</span><span class="sxs-lookup"><span data-stu-id="3ea9c-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3ea9c-113">權限</span><span class="sxs-lookup"><span data-stu-id="3ea9c-113">Permissions</span></span>  
 <span data-ttu-id="3ea9c-114">若要執行功能，您必須將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 設定為使用帳戶認證，此帳戶必須是 **中** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](系統管理員) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-114">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3ea9c-115">此帳戶必須擁有下列 Windows 權限：</span><span class="sxs-lookup"><span data-stu-id="3ea9c-115">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="3ea9c-116">以服務登入 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="3ea9c-116">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="3ea9c-117">取代處理序層級 Token (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="3ea9c-117">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="3ea9c-118">略過跨越檢查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="3ea9c-118">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="3ea9c-119">調整處理序的記憶體配額 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="3ea9c-119">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="3ea9c-120">如需 Agent 服務帳戶所需之 Windows 許可權的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[選取 SQL Server Agent 服務的帳戶](select-an-account-for-the-sql-server-agent-service.md)和[設定 Windows 服務帳戶與許可權](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-120">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3ea9c-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3ea9c-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-sql-server-agent-to-automatically-restart"></a><span data-ttu-id="3ea9c-122">若要將 SQL Server Agent 設定為自動重新啟動</span><span class="sxs-lookup"><span data-stu-id="3ea9c-122">To configure SQL Server Agent to automatically restart</span></span>  
  
1.  <span data-ttu-id="3ea9c-123">在 **[物件總管]** 中，按一下加號，展開要設定 SQL Server Agent 自動重新啟動的伺服器。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-123">In **Object Explorer**, click the plus sign to expand the server where you want to configure SQL Server Agent to automatically restart.</span></span>  
  
2.  <span data-ttu-id="3ea9c-124">以滑鼠右鍵按一下 [SQL Server Agent]\*\*\*\*，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-124">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="3ea9c-125">在 **[一般]** 頁面上，核取 **[如果 SQL Server Agent 非預期地停止，則自動予以重新啟動]**。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-125">On the **General** page, check **Auto restart SQL Server Agent if it stops unexpectedly**.</span></span>  
  
  
