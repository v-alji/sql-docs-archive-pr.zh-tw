---
title: 指定&#39;s 位置 (SQL Server Management Studio) 的目標伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], location
ms.assetid: 511ff311-21f5-4f2f-839f-b4deee26ec98
author: stevestein
ms.author: sstein
ms.openlocfilehash: 938528ab78f0f457cde69d8fd4d5432cc14a79b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598107"
---
# <a name="specify-a-target-server39s-location-sql-server-management-studio"></a><span data-ttu-id="f6177-102">指定目標伺服器的位置 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f6177-102">Specify a Target Server&#39;s Location (SQL Server Management Studio)</span></span>
  <span data-ttu-id="f6177-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中於多伺服器管理組態指定目標伺服器的位置。</span><span class="sxs-lookup"><span data-stu-id="f6177-103">This topic describes how to specify the location of a target server in a multiserver administration configuration in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f6177-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="f6177-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f6177-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="f6177-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f6177-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="f6177-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f6177-107">安全性</span><span class="sxs-lookup"><span data-stu-id="f6177-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f6177-108">**若要使用下列項目指定目標伺服器的位置：**</span><span class="sxs-lookup"><span data-stu-id="f6177-108">**To specify a target server's location, using:**</span></span>  
  
     [<span data-ttu-id="f6177-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f6177-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f6177-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f6177-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f6177-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="f6177-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f6177-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="f6177-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="f6177-113">執行此動作會編輯登錄。</span><span class="sxs-lookup"><span data-stu-id="f6177-113">Performing this action edits the registry.</span></span> <span data-ttu-id="f6177-114">您最好不要手動編輯登錄，因為不當或不正確的變更會使系統發生嚴重的組態問題。</span><span class="sxs-lookup"><span data-stu-id="f6177-114">Manual editing of the registry is not recommended because inappropriate or incorrect changes can cause serious configuration problems for your system.</span></span> <span data-ttu-id="f6177-115">因此，只有資深使用者才應該利用登錄編輯器程式來編輯登錄。</span><span class="sxs-lookup"><span data-stu-id="f6177-115">Therefore, only experienced users should use the Registry Editor program to edit the registry.</span></span> <span data-ttu-id="f6177-116">如需詳細資訊，請參閱 Microsoft Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="f6177-116">For more information, see the Microsoft Windows documentation.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f6177-117">Security</span><span class="sxs-lookup"><span data-stu-id="f6177-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f6177-118">權限</span><span class="sxs-lookup"><span data-stu-id="f6177-118">Permissions</span></span>  
 <span data-ttu-id="f6177-119">需要 **系統管理員 (sysadmin)** 固定伺服器角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="f6177-119">Requires membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f6177-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f6177-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-a-target-servers-location"></a><span data-ttu-id="f6177-121">若要指定目標伺服器的位置</span><span class="sxs-lookup"><span data-stu-id="f6177-121">To specify a target server's location</span></span>  
  
1.  <span data-ttu-id="f6177-122">在 **[物件總管]** 中，按一下加號，展開要指定目標伺服器位置的主要伺服器。</span><span class="sxs-lookup"><span data-stu-id="f6177-122">In **Object Explorer**, click the plus sign to expand the master server on which you want to specify a target server's location.</span></span>  
  
2.  <span data-ttu-id="f6177-123">以滑鼠右鍵按一下 [SQL Server Agent]\*\*\*\*、指向 [多伺服器管理]\*\*\*\*，然後選取 [管理目標伺服器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f6177-123">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and select **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="f6177-124">以滑鼠右鍵按一下目標伺服器，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f6177-124">Right-click a target server and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="f6177-125">在 **[位置]** 方塊中輸入伺服器的位置，再按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f6177-125">In the **Location** box, enter a location for the server, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f6177-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f6177-126">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-a-target-servers-location"></a><span data-ttu-id="f6177-127">若要指定目標伺服器的位置</span><span class="sxs-lookup"><span data-stu-id="f6177-127">To specify a target server's location</span></span>  
  
1.  <span data-ttu-id="f6177-128">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f6177-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f6177-129">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="f6177-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f6177-130">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="f6177-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb ;  
    GO  
    -- enlists the current server into the AdventureWorks1 master server.   
    -- The location for the current server is Building 21, Room 309, Rack 5  
    EXEC dbo.sp_msx_enlist N'AdventureWorks2012',   
        N'Building 21, Room 309, Rack 5' ;  
    GO  
    ```  
  
 <span data-ttu-id="f6177-131">如需詳細資訊，請參閱[sp_msx_enlist &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f6177-131">For more information, see [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql).</span></span>  
  
  
