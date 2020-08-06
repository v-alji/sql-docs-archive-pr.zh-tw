---
title: 建立使用者定義資料類型別名 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.userdefineddatatype.general.f1
- sql12.swb.new.datatype.properties.general.f1
helpviewer_keywords:
- alias data types [SQL Server], creating
ms.assetid: b1dd8413-0cd0-411b-a79b-1bb043ccc62d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35db332c23e2df5a8e67c3677cd2411768816765
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584568"
---
# <a name="create-a-user-defined-data-type-alias"></a><span data-ttu-id="ba314-102">建立使用者定義資料類型別名</span><span class="sxs-lookup"><span data-stu-id="ba314-102">Create a User-Defined Data Type Alias</span></span>
  <span data-ttu-id="ba314-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立新的使用者定義資料類型別名。</span><span class="sxs-lookup"><span data-stu-id="ba314-103">This topic describes how to create a new user-defined data type alias in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ba314-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="ba314-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ba314-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="ba314-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ba314-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="ba314-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ba314-107">安全性</span><span class="sxs-lookup"><span data-stu-id="ba314-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ba314-108">**使用下列方法建立使用者定義資料類型別名：**</span><span class="sxs-lookup"><span data-stu-id="ba314-108">**To create a user-defined data type alias, using:**</span></span>  
  
     [<span data-ttu-id="ba314-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ba314-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ba314-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ba314-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ba314-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="ba314-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ba314-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="ba314-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ba314-113">使用者定義資料類型別名的名稱必須符合識別碼的規則。</span><span class="sxs-lookup"><span data-stu-id="ba314-113">The name of a user-defined data type alias must comply with the rules for identifiers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ba314-114">Security</span><span class="sxs-lookup"><span data-stu-id="ba314-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ba314-115">權限</span><span class="sxs-lookup"><span data-stu-id="ba314-115">Permissions</span></span>  
 <span data-ttu-id="ba314-116">需要目前資料庫的 CREATE TYPE 權限，以及 *schema_name*的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="ba314-116">Requires CREATE TYPE permission in the current database and ALTER permission on *schema_name*.</span></span> <span data-ttu-id="ba314-117">如果未指定 *schema_name* ，則套用用來判斷目前使用者之結構描述的預設名稱解析規則。</span><span class="sxs-lookup"><span data-stu-id="ba314-117">If *schema_name* is not specified, the default name resolution rules for determining the schema for the current user apply.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ba314-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ba314-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-user-defined-data-type"></a><span data-ttu-id="ba314-119">若要建立使用者自訂的資料類型</span><span class="sxs-lookup"><span data-stu-id="ba314-119">To create a user-defined data type</span></span>  
  
1.  <span data-ttu-id="ba314-120">在物件總管中，依序展開 [資料庫]、某個資料庫、[可程式性] 和 [類型]，並以滑鼠右鍵按一下 [使用者定義資料類型]，然後按一下 [新增使用者定義資料類型]。</span><span class="sxs-lookup"><span data-stu-id="ba314-120">In Object Explorer, expand **Databases**, expand a database, expand **Programmability**, expand **Types**, right-click **User-Defined Data Types**, and then click **New User-Defined Data Type**.</span></span>  
  
     <span data-ttu-id="ba314-121">**允許 NULL**</span><span class="sxs-lookup"><span data-stu-id="ba314-121">**Allow NULLs**</span></span>  
     <span data-ttu-id="ba314-122">指定使用者定義資料類型是否可接受 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="ba314-122">Specify whether the user-defined data type can accept NULL values.</span></span> <span data-ttu-id="ba314-123">無法編輯現有使用者定義資料類型的 Null 屬性。</span><span class="sxs-lookup"><span data-stu-id="ba314-123">The nullability of an existing user-defined data type is not editable.</span></span>  
  
     <span data-ttu-id="ba314-124">**Data type**</span><span class="sxs-lookup"><span data-stu-id="ba314-124">**Data type**</span></span>  
     <span data-ttu-id="ba314-125">從清單方塊中選取基底資料類型。</span><span class="sxs-lookup"><span data-stu-id="ba314-125">Select the base data type from the list box.</span></span> <span data-ttu-id="ba314-126">這個清單方塊會顯示除了 `geography`、`geometry`、`hierarchyid`、`sysname`、`timestamp` 和 `xml` 資料類型以外的所有資料類型。</span><span class="sxs-lookup"><span data-stu-id="ba314-126">The list box displays all data types except for the `geography`, `geometry`, `hierarchyid`, `sysname`, `timestamp` , and `xml` data types.</span></span> <span data-ttu-id="ba314-127">無法編輯現有使用者定義資料類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ba314-127">The data type of an existing user-defined data type is not editable.</span></span>  
  
     <span data-ttu-id="ba314-128">**預設值**</span><span class="sxs-lookup"><span data-stu-id="ba314-128">**Default**</span></span>  
     <span data-ttu-id="ba314-129">選擇性地選取繫結到使用者定義資料類型別名的規則或預設值。</span><span class="sxs-lookup"><span data-stu-id="ba314-129">Optionally select a rule or a default to bind to the user-defined data type alias.</span></span>  
  
     <span data-ttu-id="ba314-130">**長度/有效位數**</span><span class="sxs-lookup"><span data-stu-id="ba314-130">**Length/Precision**</span></span>  
     <span data-ttu-id="ba314-131">顯示適用之資料類型的長度或有效位數。</span><span class="sxs-lookup"><span data-stu-id="ba314-131">Displays the length or precision of the data type as applicable.</span></span> <span data-ttu-id="ba314-132">[長度] 適用於字元為主的使用者定義資料類型；[有效位數] 只適用於數值為主的使用者定義資料類型。</span><span class="sxs-lookup"><span data-stu-id="ba314-132">**Length** applies to character-based user-defined data types; **Precision** applies only to numeric-based user-defined data types.</span></span> <span data-ttu-id="ba314-133">標籤會根據稍早選取的資料類型而變更。</span><span class="sxs-lookup"><span data-stu-id="ba314-133">The label changes depending on the data type selected earlier.</span></span> <span data-ttu-id="ba314-134">如果選取之資料類型的長度或有效位數是固定的，則無法編輯此方塊。</span><span class="sxs-lookup"><span data-stu-id="ba314-134">This box is not editable if the length or precision of the selected data type is fixed.</span></span>  
  
     <span data-ttu-id="ba314-135">`nvarchar(max)`、`varchar(max)` 或 `varbinary(max)` 資料類型不會顯示長度。</span><span class="sxs-lookup"><span data-stu-id="ba314-135">Length is not displayed for `nvarchar(max)`, `varchar(max)`, or `varbinary(max)` data types.</span></span>  
  
     <span data-ttu-id="ba314-136">**名稱**</span><span class="sxs-lookup"><span data-stu-id="ba314-136">**Name**</span></span>  
     <span data-ttu-id="ba314-137">如果您正在建立新的使用者定義資料類型別名，請輸入跨資料庫使用以代表使用者定義資料類型的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="ba314-137">If you are creating a new user-defined data type alias, type a unique name to be used across the database to represent the user-defined data type.</span></span> <span data-ttu-id="ba314-138">字元數目上限必須符合系統 `sysname` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="ba314-138">The maximum number of characters must match the system `sysname` data type.</span></span> <span data-ttu-id="ba314-139">無法編輯現有的使用者定義資料類型別名的名稱。</span><span class="sxs-lookup"><span data-stu-id="ba314-139">The name of an existing user-defined data type alias is not editable.</span></span>  
  
     <span data-ttu-id="ba314-140">**規則**</span><span class="sxs-lookup"><span data-stu-id="ba314-140">**Rule**</span></span>  
     <span data-ttu-id="ba314-141">選擇性地選取繫結到使用者定義資料類型別名的規則。</span><span class="sxs-lookup"><span data-stu-id="ba314-141">Optionally select a rule to bind to the user-defined data type alias.</span></span>  
  
     <span data-ttu-id="ba314-142">**調整**</span><span class="sxs-lookup"><span data-stu-id="ba314-142">**Scale**</span></span>  
     <span data-ttu-id="ba314-143">指定小數點右方的小數位數上限。</span><span class="sxs-lookup"><span data-stu-id="ba314-143">Specify the maximum number of decimal digits that can be stored to the right of the decimal point.</span></span>  
  
     <span data-ttu-id="ba314-144">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="ba314-144">**Schema**</span></span>  
     <span data-ttu-id="ba314-145">從目前使用者可用的所有結構描述清單中選取結構描述。</span><span class="sxs-lookup"><span data-stu-id="ba314-145">Select a schema from a list of all schemas available to the current user.</span></span> <span data-ttu-id="ba314-146">預設選取項目是目前使用者的預設結構描述。</span><span class="sxs-lookup"><span data-stu-id="ba314-146">The default selection is the default schema for the current user.</span></span>  
  
     <span data-ttu-id="ba314-147">**Storage**</span><span class="sxs-lookup"><span data-stu-id="ba314-147">**Storage**</span></span>  
     <span data-ttu-id="ba314-148">顯示使用者定義資料類型別名的儲存體大小上限。</span><span class="sxs-lookup"><span data-stu-id="ba314-148">Displays the maximum storage size for the user-defined data type alias.</span></span> <span data-ttu-id="ba314-149">儲存體大小上限會根據有效位數而不同。</span><span class="sxs-lookup"><span data-stu-id="ba314-149">Maximum storage sizes vary, based on precision.</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="ba314-150">1 - 9</span><span class="sxs-lookup"><span data-stu-id="ba314-150">1 - 9</span></span>|<span data-ttu-id="ba314-151">5</span><span class="sxs-lookup"><span data-stu-id="ba314-151">5</span></span>|  
    |<span data-ttu-id="ba314-152">10 - 19</span><span class="sxs-lookup"><span data-stu-id="ba314-152">10 - 19</span></span>|<span data-ttu-id="ba314-153">9</span><span class="sxs-lookup"><span data-stu-id="ba314-153">9</span></span>|  
    |<span data-ttu-id="ba314-154">20 - 28</span><span class="sxs-lookup"><span data-stu-id="ba314-154">20 - 28</span></span>|<span data-ttu-id="ba314-155">13</span><span class="sxs-lookup"><span data-stu-id="ba314-155">13</span></span>|  
    |<span data-ttu-id="ba314-156">29 - 38</span><span class="sxs-lookup"><span data-stu-id="ba314-156">29 - 38</span></span>|<span data-ttu-id="ba314-157">17</span><span class="sxs-lookup"><span data-stu-id="ba314-157">17</span></span>|  
  
     <span data-ttu-id="ba314-158">針對 `nchar` 和 `nvarchar` 資料類型，儲存體值一律為 [**長度**] 值的兩倍。</span><span class="sxs-lookup"><span data-stu-id="ba314-158">For `nchar` and `nvarchar` data types, the storage value is always two times the value in **Length**.</span></span>  
  
     <span data-ttu-id="ba314-159">`nvarchar(max)`、`varchar(max)` 或 `varbinary(max)` 資料類型不會顯示儲存體。</span><span class="sxs-lookup"><span data-stu-id="ba314-159">Storage is not displayed for `nvarchar(max)`, `varchar(max)`, or `varbinary(max)` data types.</span></span>  
  
2.  <span data-ttu-id="ba314-160">在 [新增使用者定義資料類型] 對話方塊的 [結構描述] 方塊中，輸入要擁有此資料類型別名的結構描述，或使用瀏覽按鈕來選取結構描述。</span><span class="sxs-lookup"><span data-stu-id="ba314-160">In the **New User-defined Data Type** dialog box, in the **Schema** box, type the schema to own this data type alias, or use the browse button to select the schema.</span></span>  
  
3.  <span data-ttu-id="ba314-161">在 **[名稱]** 方塊中，輸入新資料類型別名的名稱。</span><span class="sxs-lookup"><span data-stu-id="ba314-161">In the **Name** box, type a name for the new data type alias.</span></span>  
  
4.  <span data-ttu-id="ba314-162">在 **[資料類型]** 方塊中，選取將做為新資料類型別名基礎的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ba314-162">In the **Data type** box, select the data type that the new data type alias will be based on.</span></span>  
  
5.  <span data-ttu-id="ba314-163">依該資料類型的情況，完成 **[長度]** 、 **[有效位數]** 和 **[小數位數]** 方塊。</span><span class="sxs-lookup"><span data-stu-id="ba314-163">Complete the **Length**, **Precision**, and **Scale** boxes if appropriate for that data type.</span></span>  
  
6.  <span data-ttu-id="ba314-164">若新的資料類型別名可允許 NULL 值，請選取 **[允許 NULL]** 。</span><span class="sxs-lookup"><span data-stu-id="ba314-164">Check **Allow NULLs** if the new data type alias can permit NULL values.</span></span>  
  
7.  <span data-ttu-id="ba314-165">若您要將預設值或規則繫結至新的資料類型別名，請在 **[繫結]** 區域中，完成 **[預設值]** 或 **[規則]** 方塊。</span><span class="sxs-lookup"><span data-stu-id="ba314-165">In the **Binding** area, complete the **Default** or **Rule** boxes if you want to bind a default or rule to the new data type alias.</span></span> <span data-ttu-id="ba314-166">您不能在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中建立預設值和規則。</span><span class="sxs-lookup"><span data-stu-id="ba314-166">Defaults and rules cannot be created in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="ba314-167">使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ba314-167">Use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ba314-168">[範本總管] 中有可供建立預設值和規則的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="ba314-168">Example code for creating defaults and rules are available in Template Explorer.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ba314-169">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ba314-169">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-user-defined-data-type-alias"></a><span data-ttu-id="ba314-170">若要建立使用者定義資料類型別名</span><span class="sxs-lookup"><span data-stu-id="ba314-170">To create a user-defined data type alias</span></span>  
  
1.  <span data-ttu-id="ba314-171">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ba314-171">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ba314-172">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="ba314-172">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ba314-173">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="ba314-173">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ba314-174">這個範例根據系統提供的 `varchar` 資料類型建立資料類型別名。</span><span class="sxs-lookup"><span data-stu-id="ba314-174">This example creates a data type alias based on the system-supplied `varchar` data type.</span></span> <span data-ttu-id="ba314-175">`ssn` 資料類型別名用於保留 11 位數之社會保險號碼 (999-99-9999) 的資料行。</span><span class="sxs-lookup"><span data-stu-id="ba314-175">The `ssn` data type alias is used for columns holding 11-digit social security numbers (999-99-9999).</span></span> <span data-ttu-id="ba314-176">該資料行不能是 NULL。</span><span class="sxs-lookup"><span data-stu-id="ba314-176">The column cannot be NULL.</span></span>  
  
```sql  
CREATE TYPE ssn  
FROM varchar(11) NOT NULL ;  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba314-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba314-177">See Also</span></span>  
 <span data-ttu-id="ba314-178">[資料庫識別碼](database-identifiers.md) </span><span class="sxs-lookup"><span data-stu-id="ba314-178">[Database Identifiers](database-identifiers.md) </span></span>  
 [<span data-ttu-id="ba314-179">CREATE TYPE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba314-179">CREATE TYPE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-type-transact-sql)  
  
  
