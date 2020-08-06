---
title: 修改外部索引鍵關聯性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65538
- vdt.ppg.relationships
helpviewer_keywords:
- foreign keys [SQL Server], modifying
- modifying foreign keys
ms.assetid: 0c9ca80d-d79b-44c4-a21e-0fce39c398ec
author: stevestein
ms.author: sstein
ms.openlocfilehash: ba9010b0d634a174dd35391c870d5003aa78efa1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585786"
---
# <a name="modify-foreign-key-relationships"></a><span data-ttu-id="4e4ce-102">修改外部索引鍵關聯性</span><span class="sxs-lookup"><span data-stu-id="4e4ce-102">Modify Foreign Key Relationships</span></span>
  <span data-ttu-id="4e4ce-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改關聯性的外部索引鍵端。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-103">You can modify the foreign key side of a relationship in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="4e4ce-104">修改資料表的外部索引鍵，會變更與主索引鍵資料表中資料行相關的資料行。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-104">Modifying a table's foreign key changes which columns are related to columns in the primary key table.</span></span>  
  
 <span data-ttu-id="4e4ce-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4e4ce-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4e4ce-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="4e4ce-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4e4ce-108">安全性</span><span class="sxs-lookup"><span data-stu-id="4e4ce-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4e4ce-109">**使用下列方法修改外部索引鍵：**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-109">**To modify a foreign key using:**</span></span>  
  
     [<span data-ttu-id="4e4ce-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4e4ce-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4e4ce-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4e4ce-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4e4ce-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="4e4ce-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4e4ce-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="4e4ce-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="4e4ce-114">新的外部索引鍵資料行必須符合其相關主要索引鍵資料行的資料類型和大小，但是例外如下：</span><span class="sxs-lookup"><span data-stu-id="4e4ce-114">The new foreign key column must match the data type and size of the primary key column to which it relates, with these exceptions:</span></span>  
  
-   <span data-ttu-id="4e4ce-115">`char` 資料行或 `sysname` 資料行可以與 `varchar` 資料行相關聯。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-115">A `char` column or `sysname` column can relate to a `varchar` column.</span></span>  
  
-   <span data-ttu-id="4e4ce-116">`binary` 資料行可以與 `varbinary` 資料行相關聯。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-116">A `binary` column can relate to a `varbinary` column.</span></span>  
  
-   <span data-ttu-id="4e4ce-117">別名資料類型可以與其基底類型相關聯。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-117">An alias data type can relate to its base type.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4e4ce-118">Security</span><span class="sxs-lookup"><span data-stu-id="4e4ce-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4e4ce-119">權限</span><span class="sxs-lookup"><span data-stu-id="4e4ce-119">Permissions</span></span>  
 <span data-ttu-id="4e4ce-120">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-120">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4e4ce-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4e4ce-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-foreign-key"></a><span data-ttu-id="4e4ce-122">若要修改外部索引鍵</span><span class="sxs-lookup"><span data-stu-id="4e4ce-122">To modify a foreign key</span></span>  
  
1.  <span data-ttu-id="4e4ce-123">在 **[物件總管]** 中，展開含有外部索引鍵的資料表，然後展開 **[索引鍵]** 。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-123">In **Object Explorer**, expand the table with the foreign key and then expand **Keys**.</span></span>  
  
2.  <span data-ttu-id="4e4ce-124">以滑鼠右鍵按一下您要修改的外部索引鍵，然後選取 [修改]  。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-124">Right-click the foreign key to be modified and select **Modify**.</span></span>  
  
3.  <span data-ttu-id="4e4ce-125">在 **[外部索引鍵關聯性]** 對話方塊中，您可以進行下列修改。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-125">In the **Foreign Key Relationships** dialog box, you can make the following modifications.</span></span>  
  
     <span data-ttu-id="4e4ce-126">**選取的關聯性**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-126">**Selected Relationship**</span></span>  
     <span data-ttu-id="4e4ce-127">列出現有的關聯性。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-127">Lists existing relationships.</span></span> <span data-ttu-id="4e4ce-128">選取關聯性，在右邊方格中顯示其屬性。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-128">Select a relationship to show its properties in the grid to the right.</span></span> <span data-ttu-id="4e4ce-129">如果清單是空的，表示此資料表沒有定義關聯性。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-129">If the list is empty, no relationships have been defined for the table.</span></span>  
  
     <span data-ttu-id="4e4ce-130">**加入**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-130">**Add**</span></span>  
     <span data-ttu-id="4e4ce-131">建立新的關聯性。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-131">Create a new relationship.</span></span> <span data-ttu-id="4e4ce-132">[ **資料表及資料行規格** ] 必須在關聯性生效之前設定。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-132">The **Tables and Columns Specifications** must be set before the relationship will be valid.</span></span>  
  
     <span data-ttu-id="4e4ce-133">**刪除**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-133">**Delete**</span></span>  
     <span data-ttu-id="4e4ce-134">在 [選取的關聯性]  清單中刪除選取的關聯性。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-134">Delete the relationship selected in the **Selected Relationships** list.</span></span> <span data-ttu-id="4e4ce-135">若要刪除加入的關聯性，請使用此按鈕移除該關聯性。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-135">To cancel the addition of a relationship, use this button to remove the relationship.</span></span>  
  
     <span data-ttu-id="4e4ce-136">**一般類別目錄**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-136">**General Category**</span></span>  
     <span data-ttu-id="4e4ce-137">展開以顯示 [檢查建立或重新啟用時的現有資料]  以及 [資料表及資料行規格]  。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-137">Expand to show **Check Existing Data on Creation or RE-Enabling** and **Tables and Columns Specifications**.</span></span>  
  
     <span data-ttu-id="4e4ce-138">**檢查建立或重新啟用時的現有資料**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-138">**Check Existing Data on Creation or Re-Enabling**</span></span>  
     <span data-ttu-id="4e4ce-139">在建立或重新啟用條件約束之前，依照條件約束驗證資料表中所有現有的資料。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-139">Verify all existing data in the table before the constraint was created or re-enabled, against the constraint.</span></span>  
  
     <span data-ttu-id="4e4ce-140">**資料表及資料行規格分類**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-140">**Tables and Columns Specifications Category**</span></span>  
     <span data-ttu-id="4e4ce-141">展開以顯示哪些資料表的哪些資料行，在關聯性中做為外部索引鍵和主要 (或唯一) 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-141">Expand to show which columns from which tables act as the foreign key and primary (or unique) key in the relationship.</span></span> <span data-ttu-id="4e4ce-142">若要編輯或定義這些值，請按一下屬性欄位右邊的省略符號按鈕 ( **...** )。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-142">To edit or define these values, click the ellipsis button (**...**) to the right of the property field.</span></span>  
  
     <span data-ttu-id="4e4ce-143">**外部索引鍵基底資料表**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-143">**Foreign Key Base Table**</span></span>  
     <span data-ttu-id="4e4ce-144">顯示所選取的關聯性中，哪些資料表包含有做為外部索引鍵的資料行。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-144">Shows which table contains the column acting as a foreign key in the selected relationship.</span></span>  
  
     <span data-ttu-id="4e4ce-145">**外部索引鍵資料行**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-145">**Foreign Key Columns**</span></span>  
     <span data-ttu-id="4e4ce-146">顯示所選取的關聯性中，哪些資料行做為外部索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-146">Shows which column acts as a foreign key in the selected relationship.</span></span>  
  
     <span data-ttu-id="4e4ce-147">**主/唯一索引鍵基底資料表**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-147">**Primary/Unique Key Base Table**</span></span>  
     <span data-ttu-id="4e4ce-148">顯示所選取的關聯性中，哪些資料表包含有做為主要 (或唯一) 索引鍵的資料行。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-148">Shows which table contains the column acting as a primary (or unique) key in the selected relationship.</span></span>  
  
     <span data-ttu-id="4e4ce-149">**主/唯一索引鍵資料行**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-149">**Primary/Unique Key Columns**</span></span>  
     <span data-ttu-id="4e4ce-150">顯示所選取的關聯性中，哪些資料行做為主要 (或唯一) 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-150">Shows which column acts as a primary (or unique) key in the selected relationship.</span></span>  
  
     <span data-ttu-id="4e4ce-151">**識別類別目錄**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-151">**Identity Category**</span></span>  
     <span data-ttu-id="4e4ce-152">展開以顯示 [名稱]  和 [描述]  的屬性欄位。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-152">Expand to show the property fields for **Name** and **Description**.</span></span>  
  
     <span data-ttu-id="4e4ce-153">**名稱**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-153">**Name**</span></span>  
     <span data-ttu-id="4e4ce-154">顯示關聯性的名稱。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-154">Shows the name of the relationship.</span></span> <span data-ttu-id="4e4ce-155">在建立新的關聯性時，會根據 [ **資料表設計工具**] 作用中視窗的資料表，給予預設的名稱。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-155">When a new relationship is created, it is given a default name based on the table in the active window in **Table Designer**.</span></span> <span data-ttu-id="4e4ce-156">您可以隨時變更名稱。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-156">You can change the name at any time.</span></span>  
  
     <span data-ttu-id="4e4ce-157">**說明**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-157">**Description**</span></span>  
     <span data-ttu-id="4e4ce-158">描述關聯性。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-158">Describe the relationship.</span></span> <span data-ttu-id="4e4ce-159">若要撰寫更詳細的描述，請按一下 [描述]  ，然後按一下屬性欄位右邊的省略符號 **(...)** 。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-159">To write a more detailed description, click **Description** and then click the ellipsis **(...)** that appears to the right of the property field.</span></span> <span data-ttu-id="4e4ce-160">如此便可提供較大的區域以寫入文字。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-160">This provides a larger area in which to write text.</span></span>  
  
     <span data-ttu-id="4e4ce-161">**資料表設計工具類別目錄**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-161">**Table Designer Category**</span></span>  
     <span data-ttu-id="4e4ce-162">展開以顯示 [檢查建立或重新啟用時的現有資料]  和 [強制複寫]  的資訊。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-162">Expand to show information for **Check Existing Data on Creation or Re-Enabling** and **Enforce for Replication**.</span></span>  
  
     <span data-ttu-id="4e4ce-163">**強制複寫**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-163">**Enforce For Replication**</span></span>  
     <span data-ttu-id="4e4ce-164">指示當複寫代理程式在此資料表上執行插入、更新或刪除時，是否要強制使用條件約束。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-164">Indicates whether to enforce the constraint when a replication agent performs an insert, update, or delete on this table.</span></span>  
  
     <span data-ttu-id="4e4ce-165">**強制使用外部索引鍵條件約束**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-165">**Enforce Foreign Key Constraint**</span></span>  
     <span data-ttu-id="4e4ce-166">指定變更關聯性中的資料行資料時，如果變更會破壞外部索引鍵關聯性的完整性，是否允許執行。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-166">Specify whether changes are allowed to the data of the columns in the relationship if those changes would invalidate the integrity of the foreign key relationship.</span></span> <span data-ttu-id="4e4ce-167">如果不允許這樣的變更，請選擇 [ **是** ]，如果允許，請選擇 [ **否** ]。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-167">Choose **Yes** if you do not want to allow such changes, and choose **No** if you do want to allow them.</span></span>  
  
     <span data-ttu-id="4e4ce-168">**INSERT 和 UPDATE 規格分類**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-168">**INSERT and UPDATE Specification Category**</span></span>  
     <span data-ttu-id="4e4ce-169">展開以顯示關聯性之 [刪除規則]  和 [更新規則]  的資訊。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-169">Expand to show information for the **Delete Rule** and the **Update Rule** for the relationship.</span></span>  
  
     <span data-ttu-id="4e4ce-170">**刪除規則**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-170">**Delete Rule**</span></span>  
     <span data-ttu-id="4e4ce-171">指定當使用者嘗試刪除與外部索引鍵關聯性相關的資料列時，應該採取什麼動作：</span><span class="sxs-lookup"><span data-stu-id="4e4ce-171">Specify what happens if a user tries to delete a row with data that is involved in a foreign key relationship:</span></span>  
  
    -   <span data-ttu-id="4e4ce-172">**沒有動作** ：錯誤訊息會告知使用者不允許執行刪除，並且會回復 DELETE 命令。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-172">**No Action** An error message tells the user that the deletion is not allowed and the DELETE is rolled back.</span></span>  
  
    -   <span data-ttu-id="4e4ce-173">**串聯** ：刪除包含與外部索引鍵關聯性相關之資料的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-173">**Cascade** Deletes all rows containing data involved in the foreign key relationship.</span></span> <span data-ttu-id="4e4ce-174">如果資料表要包含在使用邏輯記錄的合併式發行集中，請勿指定 CASCADE。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-174">Do not specify CASCADE if the table will be included in a merge publication that uses logical records.</span></span>  
  
    -   <span data-ttu-id="4e4ce-175">**設為 Null** ：如果資料表的所有外部索引鍵資料行都可以接受 null 值，就可以將值設為 null。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-175">**Set Null** Sets the value to null if all foreign key columns for the table can accept null values.</span></span>  
  
    -   <span data-ttu-id="4e4ce-176">**設為預設值** ：如果資料表的所有外部索引鍵資料行都具有為其所定義的預設值，就可以將值設為資料行所定義的預設值。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-176">**Set Default** Sets the value to the default value defined for the column if all foreign key columns for the table have defaults defined for them.</span></span>  
  
     <span data-ttu-id="4e4ce-177">**更新規則**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-177">**Update Rule**</span></span>  
     <span data-ttu-id="4e4ce-178">指定當使用者嘗試更新與外部索引鍵關聯性相關的資料列時，應該採取什麼動作：</span><span class="sxs-lookup"><span data-stu-id="4e4ce-178">Specify what occurs if a user tries to update a row with data that is involved in a foreign key relationship:</span></span>  
  
    -   <span data-ttu-id="4e4ce-179">**沒有動作** ：錯誤訊息會告知使用者不允許執行更新，並且會還原 UPDATE 命令。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-179">**No Action** An error message tells the user that the update is not allowed and the UPDATE is rolled back.</span></span>  
  
    -   <span data-ttu-id="4e4ce-180">**串聯** ：更新包含與外部索引鍵關聯性相關之資料的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-180">**Cascade** Updates all rows that contain data involved in the foreign key relationship.</span></span> <span data-ttu-id="4e4ce-181">如果資料表要包含在使用邏輯記錄的合併式發行集中，請勿指定 CASCADE。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-181">Do not specify CASCADE if the table will be included in a merge publication that uses logical records.</span></span>  
  
    -   <span data-ttu-id="4e4ce-182">**設為 Null** ：如果資料表的所有外部索引鍵資料行都可以接受 null 值，就可以將值設為 null。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-182">**Set Null** Sets the value to null if all foreign key columns for the table can accept null values.</span></span>  
  
    -   <span data-ttu-id="4e4ce-183">**設為預設值** ：如果資料表的所有外部索引鍵資料行都具有為其所定義的預設值，就可以將值設為資料行所定義的預設值。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-183">**Set Default** Sets the value to the default value that is defined for the column if all foreign key columns for the table have defaults defined for them.</span></span>  
  
4.  <span data-ttu-id="4e4ce-184">在 [檔案]  功能表上，按一下 [儲存「資料表名稱」]。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-184">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4e4ce-185">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4e4ce-185">Using Transact-SQL</span></span>  
 <span data-ttu-id="4e4ce-186">**若要修改外部索引鍵**</span><span class="sxs-lookup"><span data-stu-id="4e4ce-186">**To modify a foreign key**</span></span>  
  
 <span data-ttu-id="4e4ce-187">若要使用 Transact-SQL 修改 FOREIGN KEY 條件約束，您必須先刪除現有的 FOREIGN KEY 條件約束，然後使用新的定義來重新建立。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-187">To modify a FOREIGN KEY constraint by using Transact-SQL, you must first delete the existing FOREIGN KEY constraint and then re-create it with the new definition.</span></span> <span data-ttu-id="4e4ce-188">如需相關資訊，請參閱 [Delete Foreign Key Relationships](delete-foreign-key-relationships.md) 及 [Create Foreign Key Relationships](create-foreign-key-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="4e4ce-188">For more information, see [Delete Foreign Key Relationships](delete-foreign-key-relationships.md) and [Create Foreign Key Relationships](create-foreign-key-relationships.md).</span></span>  
  
###  <a name="TsqlExample"></a>  
