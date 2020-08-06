---
title: 刪除操作員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- canceling operators
- removing operators
- deleting operators
- dropping operators
- jobs [SQL Server Agent], operators
- operators (users) [Database Engine], deleting with Management Studio
ms.assetid: 2b7b8627-082d-4189-8584-abd3a9b604cf
author: stevestein
ms.author: sstein
ms.openlocfilehash: 75bea1c5c5fabff7ce55fe07a5181baa8f99e0fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585759"
---
# <a name="delete-an-operator"></a><span data-ttu-id="2cb38-102">刪除操作員</span><span class="sxs-lookup"><span data-stu-id="2cb38-102">Delete an Operator</span></span>
  <span data-ttu-id="2cb38-103">本主題描述如何使用或，在中移除操作員，使其不會再收到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 警示通知 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2cb38-103">This topic describes how to remove an operator so they no longer receive [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert notifications in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2cb38-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="2cb38-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2cb38-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="2cb38-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2cb38-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="2cb38-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2cb38-107">安全性</span><span class="sxs-lookup"><span data-stu-id="2cb38-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2cb38-108">**若要使用下列項目刪除操作員：**</span><span class="sxs-lookup"><span data-stu-id="2cb38-108">**To delete an operator, using:**</span></span>  
  
     [<span data-ttu-id="2cb38-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2cb38-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2cb38-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2cb38-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2cb38-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="2cb38-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2cb38-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="2cb38-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="2cb38-113">當移除操作員時，也會移除操作員的所有相關通知。</span><span class="sxs-lookup"><span data-stu-id="2cb38-113">When an operator is removed, all the notifications associated with the operator are also removed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2cb38-114">Security</span><span class="sxs-lookup"><span data-stu-id="2cb38-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2cb38-115">權限</span><span class="sxs-lookup"><span data-stu-id="2cb38-115">Permissions</span></span>  
 <span data-ttu-id="2cb38-116">**系統管理員 (sysadmin)** 固定伺服器角色的成員可以刪除操作員。</span><span class="sxs-lookup"><span data-stu-id="2cb38-116">Members of the **sysadmin** fixed server role can delete operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2cb38-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2cb38-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-an-operator"></a><span data-ttu-id="2cb38-118">若要刪除操作員</span><span class="sxs-lookup"><span data-stu-id="2cb38-118">To delete an operator</span></span>  
  
1.  <span data-ttu-id="2cb38-119">在 **[物件總管]** 中，按一下加號，展開包含要刪除之操作員的伺服器。</span><span class="sxs-lookup"><span data-stu-id="2cb38-119">In **Object Explorer**, click the plus sign to expand the server that contains the operator you want to delete.</span></span>  
  
2.  <span data-ttu-id="2cb38-120">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="2cb38-120">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="2cb38-121">按一下加號展開 **[操作員]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2cb38-121">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="2cb38-122">以滑鼠右鍵按一下您要刪除的操作員，然後選取 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2cb38-122">Right-click the operator that you want to delete and select **Delete**.</span></span>  
  
5.  <span data-ttu-id="2cb38-123">在 **[刪除物件]** 對話方塊中，確定已選取正確的操作員，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2cb38-123">In the **Delete Object** dialog box, make sure that the correct operator is selected, and then click **OK**.</span></span> <span data-ttu-id="2cb38-124">如果希望另一個操作員可以收到會傳送給已刪除操作員的警示與作業，請核取 **[重新指派給]** ，然後在清單中選取操作員。</span><span class="sxs-lookup"><span data-stu-id="2cb38-124">If you want another operator to receive the alerts and jobs sent to the deleted operator, check **Reassign to** and select an operator in the list.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2cb38-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2cb38-125">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-an-operator"></a><span data-ttu-id="2cb38-126">若要刪除操作員</span><span class="sxs-lookup"><span data-stu-id="2cb38-126">To delete an operator</span></span>  
  
1.  <span data-ttu-id="2cb38-127">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2cb38-127">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2cb38-128">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="2cb38-128">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2cb38-129">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="2cb38-129">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- deletes operator 'Test Operator' and reassigns all alerts and jobs sent to that operator to 'Fran??ois Ajenstat'  
    USE msdb ;  
    GO  
  
    EXEC sp_delete_operator @name = 'Test Operator',  
        @reassign_to_operator = 'Fran??ois Ajenstat';  
    GO  
    ```  
  
 <span data-ttu-id="2cb38-130">如需詳細資訊，請參閱[sp_delete_operator &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-operator-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2cb38-130">For more information, see [sp_delete_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-operator-transact-sql).</span></span>  
  
  
