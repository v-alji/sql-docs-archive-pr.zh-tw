---
title: 刪除統計資料 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- statistics [SQL Server], deleting
- deleting statistics
ms.assetid: eccce0aa-591e-4a1d-bd10-373b022f8749
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 36b74d7e1465c0742cda4fef9f34fb4b3930719c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599419"
---
# <a name="delete-statistics"></a><span data-ttu-id="ef0ba-102">刪除統計資料</span><span class="sxs-lookup"><span data-stu-id="ef0ba-102">Delete Statistics</span></span>
  <span data-ttu-id="ef0ba-103">您可以在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，從資料表或檢視中刪除 (卸除) 統計資料，透過使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef0ba-103">You can delete (drop) statistics from tables and views in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
 <span data-ttu-id="ef0ba-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="ef0ba-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ef0ba-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="ef0ba-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ef0ba-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="ef0ba-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ef0ba-107">安全性</span><span class="sxs-lookup"><span data-stu-id="ef0ba-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ef0ba-108">**若要使用下列項目卸除資料表或檢視的統計資訊：**</span><span class="sxs-lookup"><span data-stu-id="ef0ba-108">**To drop statistics from a table or view, using:**</span></span>  
  
     [<span data-ttu-id="ef0ba-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ef0ba-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ef0ba-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ef0ba-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ef0ba-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="ef0ba-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ef0ba-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="ef0ba-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ef0ba-113">當您卸除統計資料時，請小心。</span><span class="sxs-lookup"><span data-stu-id="ef0ba-113">Be careful when you drop statistics.</span></span> <span data-ttu-id="ef0ba-114">執行這個動作，可能會影響查詢最佳化工具所選擇的執行計畫。</span><span class="sxs-lookup"><span data-stu-id="ef0ba-114">Doing so may affect the execution plan chosen by the query optimizer.</span></span>  
  
-   <span data-ttu-id="ef0ba-115">索引的統計資料無法利用 DROP STATISTICS 來卸除。</span><span class="sxs-lookup"><span data-stu-id="ef0ba-115">Statistics on indexes cannot be dropped by using DROP STATISTICS.</span></span> <span data-ttu-id="ef0ba-116">只要索引存在，就會保留統計資料。</span><span class="sxs-lookup"><span data-stu-id="ef0ba-116">Statistics remain as long as the index exists.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ef0ba-117">Security</span><span class="sxs-lookup"><span data-stu-id="ef0ba-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ef0ba-118">權限</span><span class="sxs-lookup"><span data-stu-id="ef0ba-118">Permissions</span></span>  
 <span data-ttu-id="ef0ba-119">需要資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="ef0ba-119">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ef0ba-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ef0ba-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-drop-statistics-from-a-table-or-view"></a><span data-ttu-id="ef0ba-121">若要卸除資料表或檢視的統計資訊</span><span class="sxs-lookup"><span data-stu-id="ef0ba-121">To drop statistics from a table or view</span></span>  
  
1.  <span data-ttu-id="ef0ba-122">在 **[物件總管]** 中，按一下加號展開要在其中刪除統計資料的資料庫。</span><span class="sxs-lookup"><span data-stu-id="ef0ba-122">In **Object Explorer**, click the plus sign to expand the database in which you want to delete a statistic.</span></span>  
  
2.  <span data-ttu-id="ef0ba-123">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ef0ba-123">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="ef0ba-124">按一下加號展開要在其中刪除統計資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="ef0ba-124">Click the plus sign to expand the table in which you want to delete a statistic.</span></span>  
  
4.  <span data-ttu-id="ef0ba-125">按一下加號展開 **[統計資料]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ef0ba-125">Click the plus sign to expand the **Statistics** folder.</span></span>  
  
5.  <span data-ttu-id="ef0ba-126">以滑鼠右鍵按一下您想要刪除的統計資料物件，然後選取 [刪除]。</span><span class="sxs-lookup"><span data-stu-id="ef0ba-126">Right-click the statistics object that you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="ef0ba-127">在 **[刪除物件]** 對話方塊中，確定已選取正確的統計資料，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="ef0ba-127">In the **Delete Object** dialog box, ensure that the correct statistic has been selected and click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ef0ba-128">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ef0ba-128">Using Transact-SQL</span></span>  
  
#### <a name="to-drop-statistics-from-a-table-or-view"></a><span data-ttu-id="ef0ba-129">若要卸除資料表或檢視的統計資訊</span><span class="sxs-lookup"><span data-stu-id="ef0ba-129">To drop statistics from a table or view</span></span>  
  
1.  <span data-ttu-id="ef0ba-130">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef0ba-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ef0ba-131">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="ef0ba-131">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ef0ba-132">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="ef0ba-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- First, create two statistics named VendorCredit and CustomerTotal  
    -- The first statistic uses a random 50% sample of information provided from the Name and CreditRating columns in the Purchasing.Vendor table.  
    CREATE STATISTICS VendorCredit  
        ON Purchasing.Vendor (Name, CreditRating)  
        WITH SAMPLE 50 PERCENT  
    -- The second statistic uses all of the information from the CustomerID and TotalDue columns in the Sales.SalesOrderHeader table  
    CREATE STATISTICS CustomerTotal  
        ON Sales.SalesOrderHeader (CustomerID, TotalDue)  
        WITH FULLSCAN;  
    GO  
    -- This next statement drops both of the statistics created above. Note that the naming convention is [table_name].[statistics_name].  
    DROP STATISTICS Purchasing.Vendor.VendorCredit, Sales.SalesOrderHeader.CustomerTotal;  
    GO  
    ```  
  
 <span data-ttu-id="ef0ba-133">如需詳細資訊，請參閱 [DROP STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-statistics-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ef0ba-133">For more information, see [DROP STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-statistics-transact-sql).</span></span>  
  
  
