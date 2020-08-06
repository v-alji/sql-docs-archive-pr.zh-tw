---
title: 指定保全操作員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- fail-safe operator [SQL Server]
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 0f4eb513-5c0a-4523-974e-e85c1deeb57f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 714ed78875bd289f2fe2d64a5699c59bce58ced0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705882"
---
# <a name="designate-a-fail-safe-operator"></a><span data-ttu-id="abc80-102">指定保全操作員</span><span class="sxs-lookup"><span data-stu-id="abc80-102">Designate a Fail-Safe Operator</span></span>
  <span data-ttu-id="abc80-103">如果在無法聯繫到指定的操作員時，就會由保全操作員這位使用者接收警示。</span><span class="sxs-lookup"><span data-stu-id="abc80-103">A fail-safe operator is a user who receives the alert if the designated operator cannot be reached.</span></span> <span data-ttu-id="abc80-104">本主題描述如何使用，在中設定要接收 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 警示通知的失敗安全操作員 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="abc80-104">This topic describes how to set a fail-safe operator to receive [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert notifications in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="abc80-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="abc80-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="abc80-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="abc80-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="abc80-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="abc80-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="abc80-108">安全性</span><span class="sxs-lookup"><span data-stu-id="abc80-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="abc80-109">**若要使用下列項目指定保全操作員：**</span><span class="sxs-lookup"><span data-stu-id="abc80-109">**To designate a fail-safe operator, using:**</span></span>  
  
     [<span data-ttu-id="abc80-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="abc80-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="abc80-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="abc80-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="abc80-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="abc80-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="abc80-113">呼叫器和 **net send** 選項會從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 未來版本的 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="abc80-113">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="abc80-114">請避免在新的開發工作中使用這些功能，並規劃修改目前使用這些功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="abc80-114">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="abc80-115">請注意，必須設定 SQL Server Agent 使用 Database Mail，才能將電子郵件及呼叫器通知傳送給操作員。</span><span class="sxs-lookup"><span data-stu-id="abc80-115">Note that SQL Server Agent must be configured to use Database Mail to send e-mail and pager notifications to operators.</span></span> <span data-ttu-id="abc80-116">如需詳細資訊，請參閱＜ [指派警示給操作員](assign-alerts-to-an-operator.md)＞。</span><span class="sxs-lookup"><span data-stu-id="abc80-116">For more information, see [Assign Alerts to an Operator](assign-alerts-to-an-operator.md).</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="abc80-117">提供了一種簡單的圖形方式供您管理各項作業，建議您利用這個方式來建立和管理作業基礎結構。</span><span class="sxs-lookup"><span data-stu-id="abc80-117">provides an easy, graphical way to manage jobs, and is the recommended way to create and manage the job infrastructure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="abc80-118">Security</span><span class="sxs-lookup"><span data-stu-id="abc80-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="abc80-119">權限</span><span class="sxs-lookup"><span data-stu-id="abc80-119">Permissions</span></span>  
 <span data-ttu-id="abc80-120">只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員才能指定保全操作員。</span><span class="sxs-lookup"><span data-stu-id="abc80-120">Only members of the **sysadmin** fixed server role can designate fail-safe operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="abc80-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="abc80-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-designate-a-fail-safe-operator"></a><span data-ttu-id="abc80-122">若要指定保全操作員</span><span class="sxs-lookup"><span data-stu-id="abc80-122">To designate a fail-safe operator</span></span>  
  
1.  <span data-ttu-id="abc80-123">在物件總管\*\*\*\* 中，按一下加號，展開包含要指定為保全操作員之 SQL Server Agent 操作員的伺服器。</span><span class="sxs-lookup"><span data-stu-id="abc80-123">In **Object Explorer,** click the plus sign to expand the server that contains the SQL Server Agent operator that you want to designate as a fail-safe.</span></span>  
  
2.  <span data-ttu-id="abc80-124">以滑鼠右鍵按一下**SQL Server Agent** ，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="abc80-124">Right-click **SQL Server Agent** and select **Properties**.</span></span>  

3.  <span data-ttu-id="abc80-125">在 [ **SQL Server Agent 屬性-**_server_name_ ] 對話方塊的 [**選取頁面**] 底下，選取 [**警示系統**]。</span><span class="sxs-lookup"><span data-stu-id="abc80-125">In the **SQL Server Agent Properties -**_server_name_ dialog box, under **Select a page**, select **Alert System**.</span></span>  
 
4.  <span data-ttu-id="abc80-126">在 [保全操作員]\*\*\*\* 下方，選取 [啟用保全操作員]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="abc80-126">Under **Fail-safe operator**, select **Enable fail-safe operator**.</span></span>  
  
5.  <span data-ttu-id="abc80-127">在 [操作員]\*\*\*\* 清單中，選取您想要設為保全操作員的操作員。</span><span class="sxs-lookup"><span data-stu-id="abc80-127">In the **Operator** list, select the operator that you want to make a fail-safe.</span></span>  
  
6.  <span data-ttu-id="abc80-128">選取下列任何一個或所有核取方塊，指定通知操作員的方法：[電子郵件]\*\*\*\*、[呼叫器]\*\*\*\* 或 [Net send]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="abc80-128">Select either any or all of the following check boxes to specify how the operator will be notified: **E-mail**, **Pager**, or **Net send**.</span></span>  
  
7.  <span data-ttu-id="abc80-129">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="abc80-129">When finished, click **OK**.</span></span>  
  
  
