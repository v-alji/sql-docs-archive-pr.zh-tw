---
title: 修改資料行 (Database Engine) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- modifying data types
- column data types [SQL Server]
- data types [SQL Server], columns
ms.assetid: b67b95c5-61ef-4bd8-9a3e-1640eb7583ac
author: stevestein
ms.author: sstein
ms.openlocfilehash: a73c25d91b742f1cc1f7edcc8a95cdf226b2683c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597032"
---
# <a name="modify-columns-database-engine"></a><span data-ttu-id="92f18-102">修改資料行 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="92f18-102">Modify Columns (Database Engine)</span></span>
  <span data-ttu-id="92f18-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="92f18-103">You can modify the data type of a column in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="92f18-104">修改已經包含資料之資料行的資料類型可能會在現有資料轉換為新類型時，導致資料永久喪失。</span><span class="sxs-lookup"><span data-stu-id="92f18-104">Modifying the data type of a column that already contains data can result in the permanent loss of data when the existing data is converted to the new type.</span></span> <span data-ttu-id="92f18-105">此外，依據修改資料行的程式碼和應用程式可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="92f18-105">In addition, code and applications that depend on the modified column may fail.</span></span> <span data-ttu-id="92f18-106">這些包含查詢、檢視、預存程序、使用者自訂函數，以及用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="92f18-106">These include queries, views, stored procedures, user-defined functions, and client applications.</span></span> <span data-ttu-id="92f18-107">注意，這些失敗會串聯。</span><span class="sxs-lookup"><span data-stu-id="92f18-107">Note that these failures will cascade.</span></span> <span data-ttu-id="92f18-108">例如，呼叫相依於已修改資料行之使用者自訂函數的預存程序可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="92f18-108">For example, a stored procedure that calls a user-defined function that depends on the modified column may fail.</span></span> <span data-ttu-id="92f18-109">在對資料行進行任何變更之前，請審慎考慮。</span><span class="sxs-lookup"><span data-stu-id="92f18-109">Carefully consider any changes you want to make to a column before making it.</span></span>  
  
 <span data-ttu-id="92f18-110">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="92f18-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="92f18-111">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="92f18-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="92f18-112">安全性</span><span class="sxs-lookup"><span data-stu-id="92f18-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="92f18-113">**若要使用下列項目來修改資料行的資料類型：**</span><span class="sxs-lookup"><span data-stu-id="92f18-113">**To modify the data type of a column, using:**</span></span>  
  
     [<span data-ttu-id="92f18-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="92f18-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="92f18-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="92f18-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="92f18-116">開始之前</span><span class="sxs-lookup"><span data-stu-id="92f18-116">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="92f18-117">Security</span><span class="sxs-lookup"><span data-stu-id="92f18-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="92f18-118">權限</span><span class="sxs-lookup"><span data-stu-id="92f18-118">Permissions</span></span>  
 <span data-ttu-id="92f18-119">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="92f18-119">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="92f18-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="92f18-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-the-data-type-of-a-column"></a><span data-ttu-id="92f18-121">若要修改資料行的資料類型</span><span class="sxs-lookup"><span data-stu-id="92f18-121">To modify the data type of a column</span></span>  
  
1.  <span data-ttu-id="92f18-122">在 [物件總管]  中，找到要變更小數位數的資料行，以滑鼠右鍵按一下包含該資料行的資料表，然後按一下 [設計]  。</span><span class="sxs-lookup"><span data-stu-id="92f18-122">In **Object Explorer**, right-click the table with columns for which you want to change the scale and click **Design**.</span></span>  
  
2.  <span data-ttu-id="92f18-123">選取要修改資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="92f18-123">Select the column for which you want to modify the data type.</span></span>  
  
3.  <span data-ttu-id="92f18-124">在 [資料行屬性]  索引標籤中，按一下 [資料類型]  屬性的方格資料格，並且從下拉式清單中選擇新的資料類型。</span><span class="sxs-lookup"><span data-stu-id="92f18-124">In the **Column Properties** tab, click the grid cell for the **Data Type** property and choose a new data type from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="92f18-125">在 [檔案]  功能表上，按一下 [儲存「資料表名稱」]。</span><span class="sxs-lookup"><span data-stu-id="92f18-125">On the **File** menu, click **Save**_table name_.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="92f18-126">在修改資料行的資料類型時，資料表設計工具會套用所選取資料類型的預設長度，即使您已經指定另一個資料類型也是如此。</span><span class="sxs-lookup"><span data-stu-id="92f18-126">When you modify the data type of a column, Table Designer applies the default length of the data type you selected, even if you have already specified another.</span></span> <span data-ttu-id="92f18-127">一定要在指定資料類型之後，設定所需值的資料類型長度。</span><span class="sxs-lookup"><span data-stu-id="92f18-127">Always set the data type length for to the desired value after specifying the data type.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="92f18-128">如果您嘗試修改與其他資料表相關之資料行的資料類型，資料表設計工具會要求您確認也會針對其他資料表中的資料行進行此變更。</span><span class="sxs-lookup"><span data-stu-id="92f18-128">If you attempt to modify the data type of a column that relates to other tables, Table Designer asks you to confirm that the change should be made to the columns in the other tables as well.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="92f18-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="92f18-129">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-the-data-type-of-a-column"></a><span data-ttu-id="92f18-130">若要修改資料行的資料類型</span><span class="sxs-lookup"><span data-stu-id="92f18-130">To modify the data type of a column</span></span>  
  
1.  <span data-ttu-id="92f18-131">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="92f18-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="92f18-132">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="92f18-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="92f18-133">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="92f18-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    CREATE TABLE dbo.doc_exy (column_a INT ) ;  
    GO  
    INSERT INTO dbo.doc_exy (column_a) VALUES (10) ;  
    GO  
    ALTER TABLE dbo.doc_exy ALTER COLUMN column_a DECIMAL (5, 2) ;  
    GO  
  
    ```  
  
 <span data-ttu-id="92f18-134">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="92f18-134">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)</span></span>  
  
  
