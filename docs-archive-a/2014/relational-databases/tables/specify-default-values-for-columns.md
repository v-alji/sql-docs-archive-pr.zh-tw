---
title: 指定資料行的預設值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], defaults
- default values
ms.assetid: 64514aed-b846-407b-992e-cf813f9a1a91
author: stevestein
ms.author: sstein
ms.openlocfilehash: 650347c29e1175c5a1fe646fc079478520dc8c6d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598758"
---
# <a name="specify-default-values-for-columns"></a><span data-ttu-id="0d2b2-102">指定資料行的預設值</span><span class="sxs-lookup"><span data-stu-id="0d2b2-102">Specify Default Values for Columns</span></span>
  <span data-ttu-id="0d2b2-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中指定將在資料行中輸入的預設值。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-103">You can specify a default value that will be entered in the column in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0d2b2-104">如果您沒有指派預設值，而且使用者將資料行保留空白，則：</span><span class="sxs-lookup"><span data-stu-id="0d2b2-104">If you do not assign a default value and the user leaves the column blank, then:</span></span>  
  
-   <span data-ttu-id="0d2b2-105">如果設定了允許 Null 值的選項，會將 NULL 插入資料行。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-105">If you set the option to allow null values, NULL will be inserted into the column.</span></span>  
  
-   <span data-ttu-id="0d2b2-106">如果沒有設定允許 Null 值的選項，資料行將會保留空白，但是使用者必須在提供資料行的值之後，才能儲存資料列。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-106">If you do not set the option to allow null values, the column will remain blank, but the user will not be able to save the row until they supply a value for the column.</span></span>  
  
 <span data-ttu-id="0d2b2-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="0d2b2-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0d2b2-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="0d2b2-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0d2b2-109">限制事項</span><span class="sxs-lookup"><span data-stu-id="0d2b2-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0d2b2-110">安全性</span><span class="sxs-lookup"><span data-stu-id="0d2b2-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0d2b2-111">**若要使用下列項目來指定預設值：**</span><span class="sxs-lookup"><span data-stu-id="0d2b2-111">**To specify a default value, using:**</span></span>  
  
     [<span data-ttu-id="0d2b2-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0d2b2-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0d2b2-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0d2b2-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0d2b2-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="0d2b2-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0d2b2-115">限制事項</span><span class="sxs-lookup"><span data-stu-id="0d2b2-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="0d2b2-116">如果 [預設值]\*\*\*\* 欄位中的輸入內容取代繫結的預設值 (顯示為沒有括弧)，系統會提示您解除繫結預設值，並使用新的預設值加以取代。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-116">If your entry in the **Default Value** field replaces a bound default (which is shown without parentheses), you will be prompted to unbind the default and replace it with your new default.</span></span>  
  
-   <span data-ttu-id="0d2b2-117">若要輸入文字字串，請將此值放在單引號 (') 之中，不要使用雙引號 (")，因為它們是保留供引號識別碼使用。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-117">To enter a text string, enclose the value in single quotation marks ('); do not use double quotation marks (") because they are reserved for quoted identifiers.</span></span>  
  
-   <span data-ttu-id="0d2b2-118">若要輸入數字預設值，請輸入數字，但不要加上引號。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-118">To enter a numeric default, enter the number without quotation marks around it.</span></span>  
  
-   <span data-ttu-id="0d2b2-119">若要輸入物件/函數，請輸入物件/函數的名稱，但不要加上引號。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-119">To enter an object/function, enter the name of the object/function without quotation marks around it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0d2b2-120">Security</span><span class="sxs-lookup"><span data-stu-id="0d2b2-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0d2b2-121">權限</span><span class="sxs-lookup"><span data-stu-id="0d2b2-121">Permissions</span></span>  
 <span data-ttu-id="0d2b2-122">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-122">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0d2b2-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0d2b2-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-a-default-value-for-a-column"></a><span data-ttu-id="0d2b2-124">若要指定資料行的預設值</span><span class="sxs-lookup"><span data-stu-id="0d2b2-124">To specify a default value for a column</span></span>  
  
1.  <span data-ttu-id="0d2b2-125">在 [物件總管]\*\*\*\* 中，找到要變更小數位數的資料行，以滑鼠右鍵按一下包含該資料行的資料表，然後按一下 [設計]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-125">In **Object Explorer**, right-click the table with columns for which you want to change the scale and click **Design**.</span></span>  
  
2.  <span data-ttu-id="0d2b2-126">選取您要指定預設值的資料行。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-126">Select the column for which you want to specify a default value.</span></span>  
  
3.  <span data-ttu-id="0d2b2-127">在 **[資料行屬性]** 索引標籤的 **[預設值或繫結]** 屬性中，輸入新的預設值。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-127">In the **Column Properties** tab, enter the new default value in the **Default Value or Binding** property.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0d2b2-128">若要輸入數字預設值，請輸入數字。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-128">To enter a numeric default value, enter the number.</span></span> <span data-ttu-id="0d2b2-129">若為物件或函數，請輸入其名稱。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-129">For an object or function enter its name.</span></span> <span data-ttu-id="0d2b2-130">若為英數字元預設值，請在單引號內部輸入值。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-130">For an alphanumeric default enter the value inside single quotes.</span></span>  
  
4.  <span data-ttu-id="0d2b2-131">在 [檔案] \*\*\*\* 功能表上，按一下 [儲存「資料表名稱」__]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-131">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0d2b2-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0d2b2-132">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-a-default-value-for-a-column"></a><span data-ttu-id="0d2b2-133">若要指定資料行的預設值</span><span class="sxs-lookup"><span data-stu-id="0d2b2-133">To specify a default value for a column</span></span>  
  
1.  <span data-ttu-id="0d2b2-134">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0d2b2-135">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0d2b2-136">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    CREATE TABLE dbo.doc_exz ( column_a INT, column_b INT) ;  
    GO  
    INSERT INTO dbo.doc_exz (column_a)VALUES ( 7 ) ;  
    GO  
    ALTER TABLE dbo.doc_exz  
    ADD CONSTRAINT col_b_def  
    DEFAULT 50 FOR column_b ;  
    GO  
  
    ```  
  
 <span data-ttu-id="0d2b2-137">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0d2b2-137">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
