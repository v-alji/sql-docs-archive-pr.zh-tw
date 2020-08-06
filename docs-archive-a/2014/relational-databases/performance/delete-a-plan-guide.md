---
title: 刪除計畫指南 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], deleting
ms.assetid: aa4d3188-6927-43de-a3e3-90fc16eeaca7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 303ad6f59cbe24265aec66f3cb780a5b4ad4f157
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698002"
---
# <a name="delete-a-plan-guide"></a><span data-ttu-id="25565-102">刪除計畫指南</span><span class="sxs-lookup"><span data-stu-id="25565-102">Delete a Plan Guide</span></span>
  <span data-ttu-id="25565-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中刪除 (卸除) 計畫指南。</span><span class="sxs-lookup"><span data-stu-id="25565-103">You can delete (drop) a plan guide in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="25565-104">您也可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]來刪除資料庫中的所有計畫指南。</span><span class="sxs-lookup"><span data-stu-id="25565-104">Using [!INCLUDE[tsql](../../includes/tsql-md.md)], you can also delete all of the plan guides in a database.</span></span>  
  
 <span data-ttu-id="25565-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="25565-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="25565-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="25565-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="25565-107">安全性</span><span class="sxs-lookup"><span data-stu-id="25565-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="25565-108">**若要使用下列項目來刪除計畫指南：**</span><span class="sxs-lookup"><span data-stu-id="25565-108">**To delete a plan guide, using:**</span></span>  
  
     [<span data-ttu-id="25565-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="25565-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="25565-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="25565-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="25565-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="25565-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="25565-112">Security</span><span class="sxs-lookup"><span data-stu-id="25565-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="25565-113">權限</span><span class="sxs-lookup"><span data-stu-id="25565-113">Permissions</span></span>  
 <span data-ttu-id="25565-114">刪除 OBJECT 計畫指南需要計畫指南所參考之物件 (例如：函數、預存程序) 的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="25565-114">Deleting an OBJECT plan guide requires ALTER permission on the object (for example: function, stored procedure) that is referenced by the plan guide.</span></span> <span data-ttu-id="25565-115">所有其他計畫指南都需要 ALTER DATABASE 權限。</span><span class="sxs-lookup"><span data-stu-id="25565-115">All other plan guides require ALTER DATABASE permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="25565-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="25565-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-plan-guide"></a><span data-ttu-id="25565-117">若要刪除計畫指南</span><span class="sxs-lookup"><span data-stu-id="25565-117">To delete a plan guide</span></span>  
  
1.  <span data-ttu-id="25565-118">按一下加號，展開您要在其中刪除計畫指南的資料庫，然後按一下加號展開 **[可程式性]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="25565-118">Click the plus sign to expand the database in which you want to delete a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="25565-119">按一下加號展開 **[計畫指南]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="25565-119">Click the plus sign to expand the **Plan Guides** folder.</span></span>  
  
3.  <span data-ttu-id="25565-120">以滑鼠右鍵按一下您想要刪除的計畫指南，然後選取 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="25565-120">Right-click the plan guide you want to delete and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="25565-121">在 **[刪除物件]** 對話方塊中，確定已選取正確的計畫指南，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="25565-121">In the **Delete Object** dialog box, ensure that the correct plan guide is selected and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="25565-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="25565-122">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-single-plan-guide"></a><span data-ttu-id="25565-123">若要刪除單一計畫指南</span><span class="sxs-lookup"><span data-stu-id="25565-123">To delete a single plan guide</span></span>  
  
1.  <span data-ttu-id="25565-124">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="25565-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="25565-125">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="25565-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="25565-126">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="25565-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
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
    GO  
    --Drop the plan guide.  
    EXEC sp_control_plan_guide N'DROP', N'Guide3';  
    GO  
    ```  
  
#### <a name="to-delete-all-plan-guides-in-a-database"></a><span data-ttu-id="25565-127">若要刪除資料庫中的所有計畫指南</span><span class="sxs-lookup"><span data-stu-id="25565-127">To delete all plan guides in a database</span></span>  
  
1.  <span data-ttu-id="25565-128">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="25565-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="25565-129">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="25565-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="25565-130">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="25565-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_control_plan_guide N'DROP ALL';  
    GO  
    ```  
  
 <span data-ttu-id="25565-131">如需詳細資訊，請參閱 [sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="25565-131">For more information, see [sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql).</span></span>  
  
  
