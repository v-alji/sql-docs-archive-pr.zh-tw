---
title: 檢視關於操作員的資訊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- viewing operators
- operators (users) [Database Engine], viewing with Management Studio
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
- displaying operators
ms.assetid: 92c82cdf-f704-444e-9539-82aea7fe6fb7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 680b90401f800a9c435bdae33b8e55385541cc4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594319"
---
# <a name="view-information-about-an-operator"></a><span data-ttu-id="d4664-102">檢視關於操作員的資訊</span><span class="sxs-lookup"><span data-stu-id="d4664-102">View Information About an Operator</span></span>
  <span data-ttu-id="d4664-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或，在中查看 Agent 操作員的相關資訊 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d4664-103">This topic describes how to view information about a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operator in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="d4664-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="d4664-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d4664-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="d4664-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d4664-106">安全性</span><span class="sxs-lookup"><span data-stu-id="d4664-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d4664-107">**若要使用下列項目，檢視關於操作員的資訊：**</span><span class="sxs-lookup"><span data-stu-id="d4664-107">**To view information about an operator, using:**</span></span>  
  
     [<span data-ttu-id="d4664-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d4664-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d4664-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d4664-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d4664-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="d4664-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d4664-111">Security</span><span class="sxs-lookup"><span data-stu-id="d4664-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d4664-112">權限</span><span class="sxs-lookup"><span data-stu-id="d4664-112">Permissions</span></span>  
 <span data-ttu-id="d4664-113">依預設，只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠執行這個預存程序。</span><span class="sxs-lookup"><span data-stu-id="d4664-113">By default, members of the **sysadmin** fixed server role can execute this stored procedure.</span></span> <span data-ttu-id="d4664-114">其他使用者必須被授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **資料庫的下列其中一個** Agent 固定資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="d4664-114">Other users must be granted one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the **msdb** database:</span></span>  
  
-   <span data-ttu-id="d4664-115">**SQLAgentUserRole**</span><span class="sxs-lookup"><span data-stu-id="d4664-115">**SQLAgentUserRole**</span></span>  
  
-   <span data-ttu-id="d4664-116">**SQLAgentReaderRole**</span><span class="sxs-lookup"><span data-stu-id="d4664-116">**SQLAgentReaderRole**</span></span>  
  
-   <span data-ttu-id="d4664-117">**SQLAgentOperatorRole**</span><span class="sxs-lookup"><span data-stu-id="d4664-117">**SQLAgentOperatorRole**</span></span>  
  
 <span data-ttu-id="d4664-118">如需這些角色權限的詳細資訊，請參閱 [SQL Server Agent 固定資料庫角色](sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="d4664-118">For details about the permissions of these roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d4664-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d4664-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-information-about-an-operator"></a><span data-ttu-id="d4664-120">若要檢視關於操作員的資訊</span><span class="sxs-lookup"><span data-stu-id="d4664-120">To view information about an operator</span></span>  
  
1.  <span data-ttu-id="d4664-121">在 **[物件總管]** 中，按一下加號，展開包含要檢視之操作員的伺服器。</span><span class="sxs-lookup"><span data-stu-id="d4664-121">In **Object Explorer**, click the plus sign to expand the server that contains the operator you want to view.</span></span>  
  
2.  <span data-ttu-id="d4664-122">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="d4664-122">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="d4664-123">按一下加號展開 **[操作員]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4664-123">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="d4664-124">以滑鼠右鍵按一下您要檢視的操作員，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d4664-124">Right-click the operator that you want to view and select **Properties**.</span></span>  
  
     <span data-ttu-id="d4664-125">如需 [<操作員名稱> 屬性]__\*\*\*\* 對話方塊中之可用選項的詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="d4664-125">For more information on the available options contained in the _operator_name_**Properties** dialog box, see:</span></span>  
  
    -   [<span data-ttu-id="d4664-126">操作員屬性和 New 運算子 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="d4664-126">Operator Properties and New Operator &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [<span data-ttu-id="d4664-127">操作員屬性：新的操作員 &#40;通知頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="d4664-127">Operator Properties: New Operator &#40;Notifications Page&#41;</span></span>](operator-properties-new-operator-notifications-page.md)  
  
    -   [<span data-ttu-id="d4664-128">操作員屬性 &#40;記錄頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="d4664-128">Operator Properties &#40;History Page&#41;</span></span>](operator-properties-history-page.md)  
  
5.  <span data-ttu-id="d4664-129">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="d4664-129">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d4664-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d4664-130">Using Transact-SQL</span></span>  
  
#### <a name="to-view-information-about-an-operator"></a><span data-ttu-id="d4664-131">若要檢視關於操作員的資訊</span><span class="sxs-lookup"><span data-stu-id="d4664-131">To view information about an operator</span></span>  
  
1.  <span data-ttu-id="d4664-132">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d4664-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d4664-133">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="d4664-133">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d4664-134">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="d4664-134">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- reports information about operator Fran??ois Ajenstat   
    -- This example assumes that the operator exists.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_operator  
        @operator_name = N'Fran??ois Ajenstat' ;  
    GO  
    ```  
  
 <span data-ttu-id="d4664-135">如需詳細資訊，請參閱[sp_help_operator &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-operator-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d4664-135">For more information, see [sp_help_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-operator-transact-sql).</span></span>  
  
  
