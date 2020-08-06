---
title: 將資料行新增至資料表 (資料庫引擎) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- inserting columns
- columns [SQL Server], adding
- adding columns
ms.assetid: abeb8d52-d562-4e29-9e1e-2923ae874859
author: stevestein
ms.author: sstein
ms.openlocfilehash: f7e9294de10be0df9ef470c75d0934e9f8787b55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595882"
---
# <a name="add-columns-to-a-table-database-engine"></a><span data-ttu-id="a24ce-102">將資料行加入資料表 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="a24ce-102">Add Columns to a Table (Database Engine)</span></span>
  <span data-ttu-id="a24ce-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中將新的資料行加入至資料表。</span><span class="sxs-lookup"><span data-stu-id="a24ce-103">This topic describes how to add new columns to a table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a24ce-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="a24ce-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a24ce-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="a24ce-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a24ce-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="a24ce-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a24ce-107">安全性</span><span class="sxs-lookup"><span data-stu-id="a24ce-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a24ce-108">**若要使用下列項目來插入資料行：**</span><span class="sxs-lookup"><span data-stu-id="a24ce-108">**To insert columns, using:**</span></span>  
  
     [<span data-ttu-id="a24ce-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a24ce-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a24ce-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a24ce-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a24ce-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="a24ce-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a24ce-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="a24ce-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="a24ce-113">如果您使用 ALTER TABLE 陳述式，將資料行加入至資料表，系統就會自動將這些資料行加入至資料表的結尾。</span><span class="sxs-lookup"><span data-stu-id="a24ce-113">Using the ALTER TABLE statement to add columns to a table automatically adds those columns to the end of the table.</span></span> <span data-ttu-id="a24ce-114">如果您想要讓資料行按照特定順序列在資料表中，請使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a24ce-114">If you want the columns in a specific order in the table, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="a24ce-115">不過，請注意，這並非資料庫設計最佳作法。</span><span class="sxs-lookup"><span data-stu-id="a24ce-115">However, note that this is not a database design best practice.</span></span> <span data-ttu-id="a24ce-116">最佳作法是在應用程式和查詢層級指定傳回資料行的順序。</span><span class="sxs-lookup"><span data-stu-id="a24ce-116">Best practice is to specify the order in which the columns are returned at the application and query level.</span></span> <span data-ttu-id="a24ce-117">您不應該仰賴使用 SELECT \*，根據資料表中定義資料行的順序，按照預期的順序傳回所有資料行。</span><span class="sxs-lookup"><span data-stu-id="a24ce-117">You should not rely on the use of SELECT \* to return all columns in an expected order based on the order in which they are defined in the table.</span></span> <span data-ttu-id="a24ce-118">請務必按照您想要顯示資料行的順序，在查詢和應用程式中依名稱指定資料行。</span><span class="sxs-lookup"><span data-stu-id="a24ce-118">Always specify the columns by name in your queries and applications in the order in which you would like them to appear.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a24ce-119">Security</span><span class="sxs-lookup"><span data-stu-id="a24ce-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a24ce-120">權限</span><span class="sxs-lookup"><span data-stu-id="a24ce-120">Permissions</span></span>  
 <span data-ttu-id="a24ce-121">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="a24ce-121">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a24ce-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a24ce-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-insert-columns-into-a-table-with-table-designer"></a><span data-ttu-id="a24ce-123">若要使用資料表設計工具將資料行插入資料表中</span><span class="sxs-lookup"><span data-stu-id="a24ce-123">To insert columns into a table with Table Designer</span></span>  
  
1.  <span data-ttu-id="a24ce-124">在物件總管\*\*\*\* 中，以滑鼠右鍵按一下要加入資料行的資料表，然後選擇 [設計]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a24ce-124">In **Object Explorer**, right-click the table to which you want to add columns and choose **Design**.</span></span>  
  
2.  <span data-ttu-id="a24ce-125">在 **[資料行名稱]** 資料行中，按一下第一個空白資料格。</span><span class="sxs-lookup"><span data-stu-id="a24ce-125">Click in the first blank cell in the **Column Name** column.</span></span>  
  
3.  <span data-ttu-id="a24ce-126">在資料格中輸入資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="a24ce-126">Type the column name in the cell.</span></span> <span data-ttu-id="a24ce-127">資料行名稱為必要值。</span><span class="sxs-lookup"><span data-stu-id="a24ce-127">The column name is a required value.</span></span>  
  
4.  <span data-ttu-id="a24ce-128">按下 TAB 鍵以移至 [ **資料類型** ] 資料格，然後從下拉式清單中選取資料類型。</span><span class="sxs-lookup"><span data-stu-id="a24ce-128">Press the TAB key to go to the **Data Type** cell and select a data type from the dropdown.</span></span> <span data-ttu-id="a24ce-129">這也是必要值。如果未選擇，將會指派預設值。</span><span class="sxs-lookup"><span data-stu-id="a24ce-129">This too is a required value, and will be assigned the default value if you don't choose one.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a24ce-130"> 您可以在 [ **資料庫工具** ] 的 [ **選項**] 對話方塊中變更預設值。</span><span class="sxs-lookup"><span data-stu-id="a24ce-130">You can change the default value in the **Options** dialog box under **Database Tools**.</span></span>  
  
5.  <span data-ttu-id="a24ce-131">在 [ **資料行屬性** ] 索引標籤中繼續定義其他任何的資料行屬性。</span><span class="sxs-lookup"><span data-stu-id="a24ce-131">Continue to define any other column properties in the **Column Properties** tab.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a24ce-132"> 資料行屬性的預設值會在您建立新資料行時加入，但是您可以在 **[資料行屬性]** 索引標籤中變更預設值。</span><span class="sxs-lookup"><span data-stu-id="a24ce-132">The default values for your column properties are added when you create a new column, but you can change them in the **Column Properties** tab.</span></span>  
  
6.  <span data-ttu-id="a24ce-133">新增資料行之後，請從 [檔案]\*\*\*\* 功能表中，選擇 [儲存 <資料表名稱>]\*\*\*\*__。</span><span class="sxs-lookup"><span data-stu-id="a24ce-133">When you are finished adding columns, from the **File** menu, choose **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a24ce-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a24ce-134">Using Transact-SQL</span></span>  
  
#### <a name="to-insert-columns-into-a-table"></a><span data-ttu-id="a24ce-135">若要將資料行插入資料表中</span><span class="sxs-lookup"><span data-stu-id="a24ce-135">To insert columns into a table</span></span>  
  
1.  <span data-ttu-id="a24ce-136">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a24ce-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a24ce-137">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="a24ce-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a24ce-138">下列範例會將兩個資料行加入至 `dbo.doc_exa`資料表。</span><span class="sxs-lookup"><span data-stu-id="a24ce-138">The following example adds two columns to the table `dbo.doc_exa`.</span></span> <span data-ttu-id="a24ce-139">將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]**</span><span class="sxs-lookup"><span data-stu-id="a24ce-139">Copy and paste the following example into the query window and click **Execute**</span></span>  
  
```  
ALTER TABLE dbo.doc_exa ADD column_b VARCHAR(20) NULL, column_c INT NULL ;  
```  
  
##  <a name="for-more-information-see-alter-table-40transact-sql41"></a><a name="FollowUp"></a><span data-ttu-id="a24ce-140">如需詳細資訊，請參閱[ALTER TABLE &#40;transact-sql&#41;](/sql/t-sql/statements/alter-table-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="a24ce-140">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)</span></span>  
  
  
