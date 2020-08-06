---
title: 變更操作員的可用性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- canceling operators
- reactivating operators
- removing operators
- deleting operators
- available operators [SQL Server]
- dropping operators
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
- disabling operators
- operators (users) [Database Engine], changing availability with Management Studio
ms.assetid: 10d58b92-b67b-47e2-af9c-9f9fd6968bba
author: stevestein
ms.author: sstein
ms.openlocfilehash: fb369ea6a2d1edf1ed8f4377b627fb1ba7339a03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606591"
---
# <a name="change-an-operator39s-availability"></a><span data-ttu-id="c2658-102">變更操作員的可用性</span><span class="sxs-lookup"><span data-stu-id="c2658-102">Change an Operator&#39;s Availability</span></span>
  <span data-ttu-id="c2658-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中變更操作員接收警示通知的排程。</span><span class="sxs-lookup"><span data-stu-id="c2658-103">This topic describes how to change an operator's schedule for receiving alert notifications in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="c2658-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="c2658-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c2658-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="c2658-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c2658-106">安全性</span><span class="sxs-lookup"><span data-stu-id="c2658-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c2658-107">**若要使用下列項目變更操作員的可用性：**</span><span class="sxs-lookup"><span data-stu-id="c2658-107">**To change an operator's availability, using:**</span></span>  
  
     [<span data-ttu-id="c2658-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c2658-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c2658-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c2658-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c2658-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="c2658-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c2658-111">Security</span><span class="sxs-lookup"><span data-stu-id="c2658-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c2658-112">權限</span><span class="sxs-lookup"><span data-stu-id="c2658-112">Permissions</span></span>  
 <span data-ttu-id="c2658-113">只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才可以編輯操作員。</span><span class="sxs-lookup"><span data-stu-id="c2658-113">Only members of the **sysadmin** fixed server role can edit operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c2658-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c2658-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-an-operators-availability"></a><span data-ttu-id="c2658-115">若要變更操作員的可用性</span><span class="sxs-lookup"><span data-stu-id="c2658-115">To change an operator's availability</span></span>  
  
1.  <span data-ttu-id="c2658-116">在 **[物件總管]** 中，按一下加號，展開包含您要啟用或停用操作員的伺服器。</span><span class="sxs-lookup"><span data-stu-id="c2658-116">In **Object Explorer**, click the plus sign to expand server that contains the operator that you want to enable or disable.</span></span>  
  
2.  <span data-ttu-id="c2658-117">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="c2658-117">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="c2658-118">按一下加號展開 **[操作員]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c2658-118">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="c2658-119">以滑鼠右鍵按一下要啟用或停用的操作員並選取 [屬性]\*\*\*\*，然後按一下 [一般]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c2658-119">Right-click the operator that you want to enable or disable and select **Properties**, then click the **General** tab.</span></span>  
  
5.  <span data-ttu-id="c2658-120">在 [ _operator_name_**屬性**] 對話方塊中，選取或清除 [**已啟用**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c2658-120">In the _operator_name_**Properties** dialog box, select or clear the **Enabled** check box.</span></span>  
  
6.  <span data-ttu-id="c2658-121">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="c2658-121">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c2658-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c2658-122">Using Transact-SQL</span></span>  
  
#### <a name="to-change-an-operators-availability"></a><span data-ttu-id="c2658-123">若要變更操作員的可用性</span><span class="sxs-lookup"><span data-stu-id="c2658-123">To change an operator's availability</span></span>  
  
1.  <span data-ttu-id="c2658-124">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c2658-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c2658-125">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="c2658-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c2658-126">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="c2658-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- disables the 'Fran??ois Ajenstat' operator  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_operator   
        @name = N'Fran??ois Ajenstat',  
        @enabled = 0;  
    GO  
    ```  
  
 <span data-ttu-id="c2658-127">如需詳細資訊，請參閱[sp_update_operator &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c2658-127">For more information, see [sp_update_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql).</span></span>  
  
  
