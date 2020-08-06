---
title: 啟用或停用資料收集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collector [SQL Server], disabling
- data collector [SQL Server], enabling
ms.assetid: 0137971b-fb48-4a3e-822a-3df2b9bb09d7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: af5cc647a63d3a9451086fc9e2211dec809e88fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592706"
---
# <a name="enable-or-disable-data-collection"></a><span data-ttu-id="6799e-102">啟用或停用資料收集</span><span class="sxs-lookup"><span data-stu-id="6799e-102">Enable or Disable Data Collection</span></span>
  <span data-ttu-id="6799e-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中啟用或停用資料收集。</span><span class="sxs-lookup"><span data-stu-id="6799e-103">This topic describes how to enable or disable data collection in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="6799e-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="6799e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6799e-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="6799e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6799e-106">安全性</span><span class="sxs-lookup"><span data-stu-id="6799e-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6799e-107">**若要使用下列項目啟用或停用資料收集：**</span><span class="sxs-lookup"><span data-stu-id="6799e-107">**To enable or disable data collection, using:**</span></span>  
  
     [<span data-ttu-id="6799e-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6799e-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6799e-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6799e-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6799e-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="6799e-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6799e-111">Security</span><span class="sxs-lookup"><span data-stu-id="6799e-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6799e-112">權限</span><span class="sxs-lookup"><span data-stu-id="6799e-112">Permissions</span></span>  
 <span data-ttu-id="6799e-113">需要 **dc_admin** 或 **dc_operator** (具有 EXECUTE 權限) 固定資料庫角色中的成員資格，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="6799e-113">Requires membership in the **dc_admin** or **dc_operator** (with EXECUTE permission) fixed database role to execute this procedure.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6799e-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6799e-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-enable-the-data-collector"></a><span data-ttu-id="6799e-115">若要啟用資料收集器</span><span class="sxs-lookup"><span data-stu-id="6799e-115">To enable the data collector</span></span>  
  
1.  <span data-ttu-id="6799e-116">在 [物件總管] 中，展開 **[管理]** 節點。</span><span class="sxs-lookup"><span data-stu-id="6799e-116">In Object Explorer, expand the **Management** node.</span></span>  
  
2.  <span data-ttu-id="6799e-117">以滑鼠右鍵按一下 **[資料收集]** ，然後按一下 **[啟用資料收集]** 。</span><span class="sxs-lookup"><span data-stu-id="6799e-117">Right-click **Data Collection**, and then click **Enable Data Collection**.</span></span>  
  
#### <a name="to-disable-the-data-collector"></a><span data-ttu-id="6799e-118">若要停用資料收集器</span><span class="sxs-lookup"><span data-stu-id="6799e-118">To disable the data collector</span></span>  
  
1.  <span data-ttu-id="6799e-119">在 [物件總管] 中，展開 **[管理]** 節點。</span><span class="sxs-lookup"><span data-stu-id="6799e-119">In Object Explorer, expand the **Management** node.</span></span>  
  
2.  <span data-ttu-id="6799e-120">以滑鼠右鍵按一下 **[資料收集]** ，然後按一下 **[停用資料收集]** 。</span><span class="sxs-lookup"><span data-stu-id="6799e-120">Right-click **Data Collection**, and then click **Disable Data Collection**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6799e-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6799e-121">Using Transact-SQL</span></span>  
  
#### <a name="to-enable-the-data-collector"></a><span data-ttu-id="6799e-122">若要啟用資料收集器</span><span class="sxs-lookup"><span data-stu-id="6799e-122">To enable the data collector</span></span>  
  
1.  <span data-ttu-id="6799e-123">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6799e-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6799e-124">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="6799e-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6799e-125">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="6799e-125">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6799e-126">此範例使用 [sp_syscollector_enable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) 啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="6799e-126">This example uses [sp_syscollector_enable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) to enable the data collector.</span></span>  
  
```sql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_enable_collector ;  
```  
  
#### <a name="to-disable-the-data-collector"></a><span data-ttu-id="6799e-127">若要停用資料收集器</span><span class="sxs-lookup"><span data-stu-id="6799e-127">To disable the data collector</span></span>  
  
1.  <span data-ttu-id="6799e-128">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6799e-128">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6799e-129">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="6799e-129">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6799e-130">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="6799e-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6799e-131">此範例使用 [sp_syscollector_disable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) 停用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="6799e-131">This example uses [sp_syscollector_disable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) to disable the data collector.</span></span>  
  
```sql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_disable_collector;  
```  
  
## <a name="see-also"></a><span data-ttu-id="6799e-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6799e-132">See Also</span></span>  
 <span data-ttu-id="6799e-133">[資料收集](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="6799e-133">[Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="6799e-134">系統預存程序 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6799e-134">System Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)  
  
  
