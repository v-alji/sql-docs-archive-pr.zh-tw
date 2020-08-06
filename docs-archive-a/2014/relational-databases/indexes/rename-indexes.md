---
title: 重新命名索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- renaming indexes
- index names [SQL Server]
- indexes [SQL Server], renaming
ms.assetid: d3d612a1-ea1b-4d99-85d2-0a2ad54f4b0e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 184d6e20f7857c5ea3535e77e21a0630ffc7b678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606291"
---
# <a name="rename-indexes"></a><span data-ttu-id="c363e-102">重新命名索引</span><span class="sxs-lookup"><span data-stu-id="c363e-102">Rename Indexes</span></span>
  <span data-ttu-id="c363e-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中重新命名索引。</span><span class="sxs-lookup"><span data-stu-id="c363e-103">This topic describes how to rename an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c363e-104">重新命名索引將以您提供的新索引名稱來取代目前的名稱。</span><span class="sxs-lookup"><span data-stu-id="c363e-104">Renaming an index replaces the current index name with the new name that you provide.</span></span> <span data-ttu-id="c363e-105">指定的名稱在資料表或檢視內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="c363e-105">The specified name must be unique within the table or view.</span></span> <span data-ttu-id="c363e-106">例如，兩個資料表可以同時擁有名稱為 **XPK_1**的索引，但同一個資料表不能具有兩個名稱為 **XPK_1**的索引。</span><span class="sxs-lookup"><span data-stu-id="c363e-106">For example, two tables can have an index named **XPK_1**, but the same table cannot have two indexes named **XPK_1**.</span></span> <span data-ttu-id="c363e-107">您不能使用與現有停用之索引相同的名稱來建立索引。</span><span class="sxs-lookup"><span data-stu-id="c363e-107">You cannot create an index with the same name as an existing disabled index.</span></span> <span data-ttu-id="c363e-108">重新命名索引並不會重建索引。</span><span class="sxs-lookup"><span data-stu-id="c363e-108">Renaming an index does not cause the index to be rebuilt.</span></span>  
  
 <span data-ttu-id="c363e-109">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="c363e-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c363e-110">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="c363e-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c363e-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="c363e-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="c363e-112">安全性</span><span class="sxs-lookup"><span data-stu-id="c363e-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c363e-113">**使用下列方法重新命名索引：**</span><span class="sxs-lookup"><span data-stu-id="c363e-113">**To rename an index, using:**</span></span>  
  
     [<span data-ttu-id="c363e-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c363e-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c363e-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c363e-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c363e-116">開始之前</span><span class="sxs-lookup"><span data-stu-id="c363e-116">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c363e-117">限制事項</span><span class="sxs-lookup"><span data-stu-id="c363e-117">Limitations and Restrictions</span></span>  
 <span data-ttu-id="c363e-118">當您在資料表上建立 PRIMARY KEY 或 UNIQUE 條件約束時，也會自動為資料表建立一個與條件約束名稱相同的索引。</span><span class="sxs-lookup"><span data-stu-id="c363e-118">When you create a PRIMARY KEY or UNIQUE constraint on a table, an index with the same name as the constraint is automatically created for the table.</span></span> <span data-ttu-id="c363e-119">因為資料表內的索引名稱必須是獨一無二的，所以無法使用與資料表上現有 PRIMARY KEY 或 UNIQUE 條件約束相同的名稱來建立或重新命名索引。</span><span class="sxs-lookup"><span data-stu-id="c363e-119">Because index names must be unique within the table, you cannot create or rename an index to have the same name as an existing PRIMARY KEY or UNIQUE constraint on the table.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c363e-120">Security</span><span class="sxs-lookup"><span data-stu-id="c363e-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c363e-121">權限</span><span class="sxs-lookup"><span data-stu-id="c363e-121">Permissions</span></span>  
 <span data-ttu-id="c363e-122">需要索引的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="c363e-122">Requires ALTER permission on the index.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c363e-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c363e-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-an-index-by-using-the-table-designer"></a><span data-ttu-id="c363e-124">使用資料表設計工具重新命名索引</span><span class="sxs-lookup"><span data-stu-id="c363e-124">To rename an index by using the Table Designer</span></span>  
  
1.  <span data-ttu-id="c363e-125">在 [物件總管] 中，按一下加號展開資料庫，此資料庫包含您要重新命名索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="c363e-125">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to rename an index.</span></span>  
  
2.  <span data-ttu-id="c363e-126">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c363e-126">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="c363e-127">以滑鼠右鍵按一下要重新命名索引的資料表，然後選取 [設計]  。</span><span class="sxs-lookup"><span data-stu-id="c363e-127">Right-click the table on which you want to rename an index and select **Design**.</span></span>  
  
4.  <span data-ttu-id="c363e-128">在 [資料表設計工具]  功能表上，按一下 [索引/索引鍵]  。</span><span class="sxs-lookup"><span data-stu-id="c363e-128">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="c363e-129">從 [選取的主/唯一索引鍵或索引]  文字方塊中選取要重新命名的索引。</span><span class="sxs-lookup"><span data-stu-id="c363e-129">Select the index you want to rename in the **Selected Primary/Unique Key or Index** text box.</span></span>  
  
6.  <span data-ttu-id="c363e-130">在方格中，按一下 [ **名稱** ]，然後在文字方塊輸入新名稱。</span><span class="sxs-lookup"><span data-stu-id="c363e-130">In the grid, click **Name** and type a new name into the text box.</span></span>  
  
7.  <span data-ttu-id="c363e-131">按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="c363e-131">Click **Close**.</span></span>  
  
8.  <span data-ttu-id="c363e-132">在 [檔案] 功能表上，按一下 [儲存 _資料表名稱_]。</span><span class="sxs-lookup"><span data-stu-id="c363e-132">On the **File** menu, click **Save**_table_name_.</span></span>  
  
#### <a name="to-rename-an-index-by-using-object-explorer"></a><span data-ttu-id="c363e-133">使用物件總管重新命名索引</span><span class="sxs-lookup"><span data-stu-id="c363e-133">To rename an index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="c363e-134">在 [物件總管] 中，按一下加號展開資料庫，此資料庫包含您要重新命名索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="c363e-134">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to rename an index.</span></span>  
  
2.  <span data-ttu-id="c363e-135">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c363e-135">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="c363e-136">按一下加號展開要重新命名索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="c363e-136">Click the plus sign to expand the table on which you want to rename an index.</span></span>  
  
4.  <span data-ttu-id="c363e-137">按一下加號展開 **[索引]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c363e-137">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="c363e-138">以滑鼠右鍵按一下您要重新命名的索引，然後選取 [重新命名]  。</span><span class="sxs-lookup"><span data-stu-id="c363e-138">Right-click the index you want to rename and select **Rename**.</span></span>  
  
6.  <span data-ttu-id="c363e-139">鍵入索引的新名稱，然後按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="c363e-139">Type the index's new name and press Enter.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c363e-140">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c363e-140">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-an-index"></a><span data-ttu-id="c363e-141">若要重新命名索引</span><span class="sxs-lookup"><span data-stu-id="c363e-141">To rename an index</span></span>  
  
1.  <span data-ttu-id="c363e-142">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c363e-142">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c363e-143">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="c363e-143">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c363e-144">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="c363e-144">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    --Renames the IX_ProductVendor_VendorID index on the Purchasing.ProductVendor table to IX_VendorID.   
  
    EXEC sp_rename N'Purchasing.ProductVendor.IX_ProductVendor_VendorID', N'IX_VendorID', N'INDEX';   
    GO  
    ```  
  
 <span data-ttu-id="c363e-145">如需詳細資訊，請參閱 [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c363e-145">For more information, see  [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).</span></span>  
  
  
