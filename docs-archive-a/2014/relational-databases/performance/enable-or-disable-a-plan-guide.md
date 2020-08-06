---
title: 啟用或停用計畫指南 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], disabling
- enabling plan guides
- plan guides [SQL Server], enabling
- disabling plan guides
ms.assetid: b00ab550-5308-4cb8-8330-483cd1d25654
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2611697e479d318245d8306b28c826e744ae85ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705093"
---
# <a name="enable-or-disable-a-plan-guide"></a><span data-ttu-id="7907e-102">啟用或停用計畫指南</span><span class="sxs-lookup"><span data-stu-id="7907e-102">Enable or Disable a Plan Guide</span></span>
  <span data-ttu-id="7907e-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中停用和啟用計畫指南。</span><span class="sxs-lookup"><span data-stu-id="7907e-103">You can disable and enable plan guides in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="7907e-104">您可以啟用或停用資料庫中的單一計畫指南或所有計畫指南。</span><span class="sxs-lookup"><span data-stu-id="7907e-104">Either a single plan guides or all plan guides in a database can be enabled or disabled.</span></span>  
  
 <span data-ttu-id="7907e-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="7907e-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7907e-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="7907e-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7907e-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="7907e-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="7907e-108">安全性</span><span class="sxs-lookup"><span data-stu-id="7907e-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7907e-109">**若要使用下列項目來停用和啟用計畫指南：**</span><span class="sxs-lookup"><span data-stu-id="7907e-109">**To disable and enable plan guides, using:**</span></span>  
  
     [<span data-ttu-id="7907e-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7907e-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7907e-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7907e-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7907e-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="7907e-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7907e-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="7907e-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="7907e-114">試圖卸除或修改計畫指南所參考的函數、預存程序或 DML 觸發程序，不論是已啟用或已停用，都會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="7907e-114">Trying to drop or modify a function, stored procedure, or DML trigger that is referenced by a plan guide, either enabled or disabled, causes an error.</span></span> <span data-ttu-id="7907e-115">請務必在卸除或修改上述任何物件之前，檢查是否存在相依性。</span><span class="sxs-lookup"><span data-stu-id="7907e-115">Always check for dependencies before dropping or modifying any of the objects listed above.</span></span>  
  
-   <span data-ttu-id="7907e-116">停用已停用的計畫指南，或啟用已啟用的計畫指南，都沒有作用，執行時也不會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7907e-116">Disabling a disabled plan guide or enabling an enabled plan guide has no effect and runs without error.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7907e-117">Security</span><span class="sxs-lookup"><span data-stu-id="7907e-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7907e-118">權限</span><span class="sxs-lookup"><span data-stu-id="7907e-118">Permissions</span></span>  
 <span data-ttu-id="7907e-119">停用或啟用 OBJECT 計畫指南需要計畫指南所參考之物件 (例如：函數、預存程序) 的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="7907e-119">Disabling or enabling an OBJECT plan guide requires ALTER permission on the object (for example: function, stored procedure) that is referenced by the plan guide.</span></span> <span data-ttu-id="7907e-120">所有其他計畫指南都需要 ALTER DATABASE 權限。</span><span class="sxs-lookup"><span data-stu-id="7907e-120">All other plan guides require ALTER DATABASE permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7907e-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7907e-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-or-enable-a-plan-guide"></a><span data-ttu-id="7907e-122">若要停用或啟用計畫指南</span><span class="sxs-lookup"><span data-stu-id="7907e-122">To disable or enable a plan guide</span></span>  
  
1.  <span data-ttu-id="7907e-123">按一下加號，展開您要在其中停用或啟用計畫指南的資料庫，然後按一下加號展開 **[可程式性]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7907e-123">Click the plus sign to expand the database in which you want to disable or enable a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="7907e-124">按一下加號展開 **[計畫指南]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7907e-124">Click the plus sign to expand the **Plan Guides** folder.</span></span>  
  
3.  <span data-ttu-id="7907e-125">以滑鼠右鍵按一下您想要停用或啟用的計畫指南，然後選取 [停用] 或 [啟用]。</span><span class="sxs-lookup"><span data-stu-id="7907e-125">Right-click the plan guide you want to disable or enable and select either **Disable** or **Enable**.</span></span>  
  
4.  <span data-ttu-id="7907e-126">在 **[停用計畫指南]** 或 **[啟用計畫指南]** 對話方塊中，確認選擇的動作已成功，然後按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="7907e-126">In either the **Disable Plan Guide** or **Enable Plan Guide** dialog box, verify that the chosen action was successful and then click **Close**.</span></span>  
  
#### <a name="to-disable-or-enable-all-plan-guides-in-a-database"></a><span data-ttu-id="7907e-127">若要停用或啟用資料庫中的所有計畫指南</span><span class="sxs-lookup"><span data-stu-id="7907e-127">To disable or enable all plan guides in a database</span></span>  
  
1.  <span data-ttu-id="7907e-128">按一下加號，展開您要在其中停用或啟用計畫指南的資料庫，然後按一下加號展開 **[可程式性]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7907e-128">Click the plus sign to expand the database in which you want to disable or enable a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="7907e-129">以滑鼠右鍵按一下 [計畫指南] 資料夾，然後選取 [全部啟用] 或 [全部停用]。</span><span class="sxs-lookup"><span data-stu-id="7907e-129">Right-click the **Plan Guides** folder and then select either **Enable All** or **Disable All**.</span></span>  
  
3.  <span data-ttu-id="7907e-130">在 **[停用所有計畫指南]** 或 **[啟用所有計畫指南]** 對話方塊中，確認選擇的動作已成功，然後按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="7907e-130">In either the **Disable all Plan Guides** or **Enable all Plan Guides** dialog box, verify that the chosen action was successful and then click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7907e-131">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7907e-131">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-or-enable-a-plan-guide"></a><span data-ttu-id="7907e-132">若要停用或啟用計畫指南</span><span class="sxs-lookup"><span data-stu-id="7907e-132">To disable or enable a plan guide</span></span>  
  
1.  <span data-ttu-id="7907e-133">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7907e-133">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7907e-134">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="7907e-134">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7907e-135">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="7907e-135">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    --Create a procedure on which to define the plan guide.  
    IF OBJECT_ID(N'Sales.GetSalesOrderByCountry', N'P') IS NOT NULL  
        DROP PROCEDURE Sales.GetSalesOrderByCountry;  
    GO  
    CREATE PROCEDURE Sales.GetSalesOrderByCountry   
        (@Country nvarchar(60))  
    AS  
    BEGIN  
        SELECT *  
        FROM Sales.SalesOrderHeader AS h   
        INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
        INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
        WHERE t.CountryRegionCode = @Country;  
    END  
    GO  
    --Create the plan guide.  
    EXEC sp_create_plan_guide N'Guide3',  
        N'SELECT *  
        FROM Sales.SalesOrderHeader AS h   
        INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
        INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
        WHERE t.CountryRegionCode = @Country',  
        N'OBJECT',  
        N'Sales.GetSalesOrderByCountry',  
        NULL,  
        N'OPTION (OPTIMIZE FOR (@Country = N''US''))';  
    --Disable the plan guide.  
    EXEC sp_control_plan_guide N'DISABLE', N'Guide3';  
    GO  
    --Enable the plan guide.  
    EXEC sp_control_plan_guide N'ENABLE', N'Guide3';  
    GO  
  
    ```  
  
#### <a name="to-disable-or-enable-all-plan-guides-in-a-database"></a><span data-ttu-id="7907e-136">若要停用或啟用資料庫中的所有計畫指南</span><span class="sxs-lookup"><span data-stu-id="7907e-136">To disable or enable all plan guides in a database</span></span>  
  
1.  <span data-ttu-id="7907e-137">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7907e-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7907e-138">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="7907e-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7907e-139">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="7907e-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    --Disable all plan guides in the database.  
    EXEC sp_control_plan_guide N'DISABLE ALL';  
    GO  
    --Enable all plan guides in the database.  
    EXEC sp_control_plan_guide N'ENABLE ALL';  
    GO  
  
    ```  
  
 <span data-ttu-id="7907e-140">如需詳細資訊，請參閱 [sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7907e-140">For more information, see [sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql).</span></span>  
  
  
