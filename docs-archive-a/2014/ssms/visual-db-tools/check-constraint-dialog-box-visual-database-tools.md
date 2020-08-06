---
title: 檢查條件約束對話方塊 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.checkconstraint
ms.assetid: ad0bbf7f-b0de-406a-bd0a-cb779816b101
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7244984b869a1c68e597984a1cd03e16e53d0306
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584238"
---
# <a name="check-constraint-dialog-box-visual-database-tools"></a><span data-ttu-id="30fcb-102">檢查條件約束對話方塊 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="30fcb-102">Check Constraint Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="30fcb-103">當您在資料表設計工具的資料表定義方格上按一下滑鼠右鍵，再按 [檢查條件約束]  時，這個對話方塊便會出現。</span><span class="sxs-lookup"><span data-stu-id="30fcb-103">This dialog box appears when you right-click a table definition grid in Table Designer and click **Check Constraints**.</span></span> <span data-ttu-id="30fcb-104">此對話方塊包含一組附加至資料庫資料表的非唯一條件約束的屬性。</span><span class="sxs-lookup"><span data-stu-id="30fcb-104">The dialog box contains a set of properties for non-unique constraints attached to the tables in your database.</span></span> <span data-ttu-id="30fcb-105">套用至唯一條件約束的屬性會出現在 [索引/索引鍵]  對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="30fcb-105">Properties applying to unique constraints appear in the **Indexes/Keys** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30fcb-106">如果資料表是要發佈以進行複寫，則必須使用 Transact-SQL 陳述式 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 SQL Server 管理物件 (SMO) 變更結構描述。</span><span class="sxs-lookup"><span data-stu-id="30fcb-106">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="30fcb-107">使用 [資料表設計工具] 或 [資料庫圖表設計工具] 變更結構描述時，會嘗試卸除並重新建立資料表。</span><span class="sxs-lookup"><span data-stu-id="30fcb-107">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="30fcb-108">您無法卸除已發行的物件，因此結構描述變更將會失敗。</span><span class="sxs-lookup"><span data-stu-id="30fcb-108">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="options"></a><span data-ttu-id="30fcb-109">選項。</span><span class="sxs-lookup"><span data-stu-id="30fcb-109">Options</span></span>  
 <span data-ttu-id="30fcb-110">**選取的檢查條件約束**</span><span class="sxs-lookup"><span data-stu-id="30fcb-110">**Selected Check Constraints**</span></span>  
 <span data-ttu-id="30fcb-111">列出可用的檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="30fcb-111">Lists available check constraints.</span></span> <span data-ttu-id="30fcb-112">若要檢視條件約束的屬性，請在清單中選取該條件約束。</span><span class="sxs-lookup"><span data-stu-id="30fcb-112">To view the properties of a constraint, select it in the list.</span></span>  
  
 <span data-ttu-id="30fcb-113">**加入**</span><span class="sxs-lookup"><span data-stu-id="30fcb-113">**Add**</span></span>  
 <span data-ttu-id="30fcb-114">為選取的資料庫資料表建立新的條件約束，並提供該條件約束的預設名稱和其他值。</span><span class="sxs-lookup"><span data-stu-id="30fcb-114">Create a new constraint for the selected database table and provide a default name and other values for the constraint.</span></span> <span data-ttu-id="30fcb-115">在輸入條件約束的運算式之後，條件約束才會有效。</span><span class="sxs-lookup"><span data-stu-id="30fcb-115">The constraint will not become valid until an expression is entered for the constraint.</span></span>  
  
 <span data-ttu-id="30fcb-116">**刪除**</span><span class="sxs-lookup"><span data-stu-id="30fcb-116">**Delete**</span></span>  
 <span data-ttu-id="30fcb-117">從資料表中刪除選取的條件約束。</span><span class="sxs-lookup"><span data-stu-id="30fcb-117">Remove the selected constraint from the table.</span></span> <span data-ttu-id="30fcb-118">若要刪除加入的檢查條件約束，請使用此按鈕移除該條件約束。</span><span class="sxs-lookup"><span data-stu-id="30fcb-118">To cancel the addition of a check constraint, use this button to remove the constraint.</span></span>  
  
 <span data-ttu-id="30fcb-119">**一般類別目錄**</span><span class="sxs-lookup"><span data-stu-id="30fcb-119">**General Category**</span></span>  
 <span data-ttu-id="30fcb-120">展開以顯示 [運算式]  屬性欄位。</span><span class="sxs-lookup"><span data-stu-id="30fcb-120">Expand to show the **Expression** property field.</span></span>  
  
 <span data-ttu-id="30fcb-121">**運算式**</span><span class="sxs-lookup"><span data-stu-id="30fcb-121">**Expression**</span></span>  
 <span data-ttu-id="30fcb-122">顯示已選取之檢查條件約束的運算式。</span><span class="sxs-lookup"><span data-stu-id="30fcb-122">Displays the expression for the selected check constraint.</span></span> <span data-ttu-id="30fcb-123">對於新的條件約束，退出此方塊之前必須先輸入運算式。</span><span class="sxs-lookup"><span data-stu-id="30fcb-123">For new constraints, you must enter the expression before exiting this box.</span></span> <span data-ttu-id="30fcb-124">您也可以編輯現有的檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="30fcb-124">You can also edit existing check constraints.</span></span> <span data-ttu-id="30fcb-125">如需詳細資訊，請參閱 [Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="30fcb-125">For more information, see [Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md).</span></span>  
  
 <span data-ttu-id="30fcb-126">**識別類別目錄**</span><span class="sxs-lookup"><span data-stu-id="30fcb-126">**Identity Category**</span></span>  
 <span data-ttu-id="30fcb-127">展開以顯示 [名稱]  與 [描述]  屬性。</span><span class="sxs-lookup"><span data-stu-id="30fcb-127">Expand to show properties for **Name** and **Description**.</span></span>  
  
 <span data-ttu-id="30fcb-128">**名稱**</span><span class="sxs-lookup"><span data-stu-id="30fcb-128">**Name**</span></span>  
 <span data-ttu-id="30fcb-129">顯示已選取之檢查條件約束的名稱。</span><span class="sxs-lookup"><span data-stu-id="30fcb-129">Shows the name of the selected check constraint.</span></span> <span data-ttu-id="30fcb-130">若要變更這個條件約束的名稱，請直接在屬性欄位中輸入文字。</span><span class="sxs-lookup"><span data-stu-id="30fcb-130">To change the name of this constraint, type the text directly in the property field.</span></span>  
  
 <span data-ttu-id="30fcb-131">**說明**</span><span class="sxs-lookup"><span data-stu-id="30fcb-131">**Description**</span></span>  
 <span data-ttu-id="30fcb-132">描述此檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="30fcb-132">Describing this check constraint.</span></span> <span data-ttu-id="30fcb-133">您可以在屬性欄位中鍵入來編輯描述，或按一下屬性欄位右側的省略符號按鈕 ( **...** )，並編輯 [描述屬性]  對話方塊中的描述。</span><span class="sxs-lookup"><span data-stu-id="30fcb-133">You can edit the description by typing into the property field or you can click the ellipsis button (**...**) that appears to the right of the property field and edit the description in the **Description Property** dialog box.</span></span>  
  
 <span data-ttu-id="30fcb-134">**資料表設計工具類別目錄**</span><span class="sxs-lookup"><span data-stu-id="30fcb-134">**Table Designer Category**</span></span>  
 <span data-ttu-id="30fcb-135">展開以顯示 [檢查建立或重新啟用時的現有資料]  、[於 INSERT 及 UPDATE 時強制套用]  與 [強制複寫]  的屬性。</span><span class="sxs-lookup"><span data-stu-id="30fcb-135">Expand to show properties for **Check Existing Data on Creation or Re-enabling**, **Enforce For Inserts And Updates**, and **Enforce Replication**.</span></span>  
  
 <span data-ttu-id="30fcb-136">**檢查建立或重新啟用時的現有資料**</span><span class="sxs-lookup"><span data-stu-id="30fcb-136">**Check Existing Data On Creation or Re-Enabling**</span></span>  
 <span data-ttu-id="30fcb-137">指定是否依照條件約束驗證所有先前已存在的資料 (在建立條件約束前已存在於資料表中的資料)。</span><span class="sxs-lookup"><span data-stu-id="30fcb-137">Specify whether all pre-existing data (data existing in the table before the constraint is created) is verified against the constraint.</span></span>  
  
 <span data-ttu-id="30fcb-138">**於 INSERTs 及 UPDATEs 時強制套用**</span><span class="sxs-lookup"><span data-stu-id="30fcb-138">**Enforce For Inserts And Updates**</span></span>  
 <span data-ttu-id="30fcb-139">指定是否在將資料插入資料表中或更新資料表時，強制使用條件約束。</span><span class="sxs-lookup"><span data-stu-id="30fcb-139">Specify whether the constraint is enforced when data is inserted into or updated in the table.</span></span>  
  
 <span data-ttu-id="30fcb-140">**強制複寫**</span><span class="sxs-lookup"><span data-stu-id="30fcb-140">**Enforce For Replication**</span></span>  
 <span data-ttu-id="30fcb-141">指示當複寫代理程式在此資料表上執行插入或更新時，是否要強制使用條件約束。</span><span class="sxs-lookup"><span data-stu-id="30fcb-141">Indicates whether to enforce the constraint when a replication agent performs an insert or update on this table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30fcb-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30fcb-142">See Also</span></span>  
 <span data-ttu-id="30fcb-143">[Unique 條件約束和 Check 條件約束](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="30fcb-143">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 <span data-ttu-id="30fcb-144">[[索引和索引鍵] 對話方塊 &#40;Visual Database Tools&#41;](visual-database-tools.md)</span><span class="sxs-lookup"><span data-stu-id="30fcb-144">[Indexes and Keys Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md)</span></span>  
  
  
