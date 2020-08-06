---
title: 重新命名 SQL Server Agent 錯誤記錄檔 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- renaming SQL Server Agent error log
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: dee2b199-48af-44cb-9177-d029a5edb169
author: stevestein
ms.author: sstein
ms.openlocfilehash: c1c85550a29bfff316ffc275ba2d4e4df10686d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606550"
---
# <a name="rename-a-sql-server-agent-error-log-sql-server-management-studio"></a><span data-ttu-id="17b96-102">Rename a SQL Server Agent Error Log (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="17b96-102">Rename a SQL Server Agent Error Log (SQL Server Management Studio)</span></span>
  <span data-ttu-id="17b96-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用，在中重新命名 Agent 錯誤所寫入的檔案 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="17b96-103">This topic describes how to rename the file where [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent errors are written in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="17b96-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="17b96-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="17b96-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="17b96-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="17b96-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="17b96-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="17b96-107">安全性</span><span class="sxs-lookup"><span data-stu-id="17b96-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="17b96-108">若要使用 SQL Server Management Studio 重新命名 SQL Server Agent 錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="17b96-108">To rename a SQL Server Agent error log using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="17b96-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="17b96-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="17b96-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="17b96-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="17b96-111">只有當您擁有使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 節點的權限時，[物件總管] 才會顯示該節點。</span><span class="sxs-lookup"><span data-stu-id="17b96-111">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="17b96-112">Agent 不會寫入到新的記錄檔中，除非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務重新啟動。</span><span class="sxs-lookup"><span data-stu-id="17b96-112">Agent will not write to the new log file until the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is restarted.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="17b96-113">Security</span><span class="sxs-lookup"><span data-stu-id="17b96-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="17b96-114">權限</span><span class="sxs-lookup"><span data-stu-id="17b96-114">Permissions</span></span>  
 <span data-ttu-id="17b96-115">若要執行功能，您必須將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 設定為使用帳戶認證，此帳戶必須是 **中** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](系統管理員) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="17b96-115">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="17b96-116">此帳戶必須擁有下列 Windows 權限：</span><span class="sxs-lookup"><span data-stu-id="17b96-116">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="17b96-117">以服務登入 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="17b96-117">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="17b96-118">取代處理序層級 Token (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="17b96-118">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="17b96-119">略過跨越檢查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="17b96-119">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="17b96-120">調整處理序的記憶體配額 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="17b96-120">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="17b96-121">如需 Agent 服務帳戶所需之 Windows 許可權的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[選取 SQL Server Agent 服務的帳戶](select-an-account-for-the-sql-server-agent-service.md)和[設定 Windows 服務帳戶與許可權](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="17b96-121">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="17b96-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="17b96-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-sql-server-agent-error-log"></a><span data-ttu-id="17b96-123">若要重新命名 SQL Server Agent 錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="17b96-123">To rename a SQL Server Agent error log</span></span>  
  
1.  <span data-ttu-id="17b96-124">在 **[物件總管]** 中，按一下加號展開伺服器，此伺服器包含要重新命名的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="17b96-124">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log that you want to rename.</span></span>  
  
2.  <span data-ttu-id="17b96-125">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="17b96-125">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="17b96-126">以滑鼠右鍵按一下 [錯誤記錄檔]\*\*\*\* 資料夾，然後選取 [設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="17b96-126">Right-click the **Error Logs** folder and select **Configure**.</span></span>  
  
4.  <span data-ttu-id="17b96-127">在 **[設定 SQL Server Agent 錯誤記錄檔]** 對話方塊的 **[錯誤記錄檔]** 方塊中，輸入錯誤記錄檔的新路徑與檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="17b96-127">In the **Configure SQL Server Agent Error Logs** dialog box, in the **Error log file** box, enter the new file path and file name for the error log.</span></span> <span data-ttu-id="17b96-128">或者，按一下省略符號 **(...)** 開啟 [指定代理程式錯誤記錄檔的位置]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="17b96-128">Alternately, click the ellipsis **(...)** to open the **Specify agent error log location** dialog box.</span></span>  
  
5.  <span data-ttu-id="17b96-129">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="17b96-129">When finished, click **OK**.</span></span>  
  
  
