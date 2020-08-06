---
title: 設計資料庫圖表 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65536
- vdt.DatabaseDesigner
helpviewer_keywords:
- Database Diagram Designer
- Visual Database Tools [SQL Server], database diagrams
- database diagrams [SQL Server], designing
- diagrams [SQL Server], designing
ms.assetid: 6d2c14e1-3d73-4d10-ae5b-7f2b5d6c4ea8
author: stevestein
ms.author: sstein
ms.openlocfilehash: bb4cbc518b6878ed8fb6e9f7d5d2d00803ab4d62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688417"
---
# <a name="design-database-diagrams-visual-database-tools"></a><span data-ttu-id="48471-102">設計資料庫圖表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="48471-102">Design Database Diagrams (Visual Database Tools)</span></span>
  <span data-ttu-id="48471-103">「資料庫設計工具」為視覺化工具，可讓您設計連接的資料庫，並將該資料庫視覺化。</span><span class="sxs-lookup"><span data-stu-id="48471-103">The Database Designer is a visual tool that allows you to design and visualize a database to which you are connected.</span></span> <span data-ttu-id="48471-104">設計資料庫時，您可以使用資料庫設計工具建立、編輯或刪除資料表、資料行、索引鍵、索引、關聯性和條件約束。</span><span class="sxs-lookup"><span data-stu-id="48471-104">When designing a database, you can use Database Designer to create, edit, or delete tables, columns, keys, indexes, relationships, and constraints.</span></span> <span data-ttu-id="48471-105">若要以視覺化方式呈現資料庫，可以建立一或多個圖表說明該資料庫中部分或全部的資料表、資料行、索引鍵和關聯性。</span><span class="sxs-lookup"><span data-stu-id="48471-105">To visualize a database, you can create one or more diagrams illustrating some or all of the tables, columns, keys, and relationships in it.</span></span>  
  
 <span data-ttu-id="48471-106">![說明資料表關聯性的資料庫圖表](../../database-engine/media//dv3w7c1.gif "說明資料表關聯性的資料庫圖表")</span><span class="sxs-lookup"><span data-stu-id="48471-106">![Database diagram illustrating table relationships](../../database-engine/media//dv3w7c1.gif "Database diagram illustrating table relationships")</span></span>  
  
 <span data-ttu-id="48471-107">您可以根據您的需要在任何資料庫中建立資料庫圖表 (不限個數)；不論圖表數量為何，每個圖表中都將出現資料庫表格。</span><span class="sxs-lookup"><span data-stu-id="48471-107">For any database, you can create as many database diagrams as you like; each database table can appear on any number of diagrams.</span></span> <span data-ttu-id="48471-108">因此您可建立不同的圖表，將資料庫的不同部份進行視覺化，或強調不同的設計重點。</span><span class="sxs-lookup"><span data-stu-id="48471-108">Thus, you can create different diagrams to visualize different portions of the database, or to accentuate different aspects of the design.</span></span> <span data-ttu-id="48471-109">例如，您可以建立大型圖表來顯示所有資料表和資料行，以及建立小型圖表來顯示所有的資料表，但不顯示資料行。</span><span class="sxs-lookup"><span data-stu-id="48471-109">For example, you can create a large diagram showing all tables and columns, and you can create a smaller diagram showing all tables without showing the columns.</span></span>  
  
 <span data-ttu-id="48471-110">您建立的所有資料庫圖表都將存放在相關資料庫中。</span><span class="sxs-lookup"><span data-stu-id="48471-110">Each database diagram you create is stored in the associated database.</span></span>  
  
## <a name="tables-and-columns-in-a-database-diagram"></a><span data-ttu-id="48471-111">資料庫圖表中的資料表和資料行</span><span class="sxs-lookup"><span data-stu-id="48471-111">Tables and Columns in a Database Diagram</span></span>  
 <span data-ttu-id="48471-112">資料庫圖表中的每個資料表都具有三項功能：標題列、資料列選取器和一組屬性欄位。</span><span class="sxs-lookup"><span data-stu-id="48471-112">Within a database diagram, each table can appear with three distinct features: a title bar, a row selector, and a set of property columns.</span></span>  
  
 <span data-ttu-id="48471-113">**標題列** ：標題列顯示資料表的名稱</span><span class="sxs-lookup"><span data-stu-id="48471-113">**Title Bar** The title bar shows the name of the table</span></span>  
  
 <span data-ttu-id="48471-114">如果您已經修改某個資料表但尚未儲存，該資料表名稱的後方將出現星號 (\*) 表示尚未儲存變更。</span><span class="sxs-lookup"><span data-stu-id="48471-114">If you have modified a table and have not yet saved it, an asterisk (\*) appears at the end of the table name to indicate unsaved changes.</span></span> <span data-ttu-id="48471-115">如需儲存修改過的資料表和圖表的詳細資訊，請參閱 [使用資料庫圖表 &#40;Visual Database Tools&#41;](visual-database-tools.md)</span><span class="sxs-lookup"><span data-stu-id="48471-115">For information about saving modified tables and diagrams, see [Work with Database Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md)</span></span>  
  
 <span data-ttu-id="48471-116">**資料列選取器** ：您可以按一下資料列選取器，選取資料表中的資料庫資料行。</span><span class="sxs-lookup"><span data-stu-id="48471-116">**Row Selector** You can click the row selector to select a database column in the table.</span></span> <span data-ttu-id="48471-117">如果該資料行位於資料表的主索引鍵，資料列選取器將顯示索引鍵符號。</span><span class="sxs-lookup"><span data-stu-id="48471-117">The row selector displays a key symbol if the column is in the table's primary key.</span></span> <span data-ttu-id="48471-118">如需主鍵的詳細資訊，請參閱[primary 和 Foreign Key 條件約束](../../relational-databases/tables/primary-and-foreign-key-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="48471-118">For information about primary keys, see [Primary and Foreign Key Constraints](../../relational-databases/tables/primary-and-foreign-key-constraints.md).</span></span>  
  
 <span data-ttu-id="48471-119">**屬性資料行** ：屬性資料行組只有在資料表中的特定檢視才可見。</span><span class="sxs-lookup"><span data-stu-id="48471-119">**Property Columns** The set of property columns is visible only in the certain views of your table.</span></span> <span data-ttu-id="48471-120">您可以使用五種檢視方法來檢視資料表，任何一種方法都可以協助您管理圖表的大小和配置。</span><span class="sxs-lookup"><span data-stu-id="48471-120">You can view a table in any of five different views to help you manage the size and layout of your diagram.</span></span>  
  
 <span data-ttu-id="48471-121">如需資料表檢視的詳細資訊，請參閱[自訂圖表中顯示的資料量 &#40;Visual Database Tools&#41;](customize-the-amount-of-information-displayed-in-diagrams-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="48471-121">For more information about table views, see [Customize the Amount of Information Displayed in Diagrams &#40;Visual Database Tools&#41;](customize-the-amount-of-information-displayed-in-diagrams-visual-database-tools.md).</span></span>  
  
## <a name="relationships-in-a-database-diagram"></a><span data-ttu-id="48471-122">資料庫圖表中的關聯性</span><span class="sxs-lookup"><span data-stu-id="48471-122">Relationships in a Database Diagram</span></span>  
 <span data-ttu-id="48471-123">資料庫圖表中的每個關聯性都具有三項功能：結束點、行樣式和相關資料表。</span><span class="sxs-lookup"><span data-stu-id="48471-123">Within a database diagram, each relationship can appear with three distinct features: endpoints, a line style, and related tables.</span></span>  
  
 <span data-ttu-id="48471-124">**結束點** ：行的結束點可以顯示其關聯性為一對一或一對多。</span><span class="sxs-lookup"><span data-stu-id="48471-124">**Endpoints** The endpoints of the line indicate whether the relationship is one-to-one or one-to-many.</span></span> <span data-ttu-id="48471-125">如果關聯性在結束點具有一個索引鍵，且在其他結束點擁有 ∞，該關聯性即為一對多關聯性 (One-To-Many Relationship)。</span><span class="sxs-lookup"><span data-stu-id="48471-125">If a relationship has a key at one endpoint and a figure-eight at the other, it is a one-to-many relationship.</span></span> <span data-ttu-id="48471-126">如果關聯性在每個結束點都擁有一個索引鍵，該關聯性即為一對一關聯性。</span><span class="sxs-lookup"><span data-stu-id="48471-126">If a relationship has a key at each endpoint, it is a one-to-one relationship.</span></span>  
  
 <span data-ttu-id="48471-127">**行樣式** ：資料行本身 (非其結束點) 可指出當新資料加入至外部索引鍵表格時，資料庫管理系統 (DBMS) 是否會強制使用關聯性的參考完整性 (Referential Integrity)。</span><span class="sxs-lookup"><span data-stu-id="48471-127">**Line Style** The line itself (not its endpoints) indicates whether the Database Management System (DBMS) enforces referential integrity for the relationship when new data is added to the foreign-key table.</span></span> <span data-ttu-id="48471-128">如果該行為實線，當您在外部索引鍵資料表中加入或修改資料列時，DBMS 將強制使用關聯性的參考完整性。</span><span class="sxs-lookup"><span data-stu-id="48471-128">If the line appears solid, the DBMS enforces referential integrity for the relationship when rows are added or modified in the foreign-key table.</span></span> <span data-ttu-id="48471-129">如果該行為虛線，當您在外部索引資料表中加入或修改資料列時，DBMS 將不會強制使用關聯性的參考完整性。</span><span class="sxs-lookup"><span data-stu-id="48471-129">If the line appears dotted, the DBMS does not enforce referential integrity for the relationship when rows are added or modified in the foreign-key table.</span></span>  
  
 <span data-ttu-id="48471-130">**相關資料表** ：關聯性行將指出兩個表格之間是否存在外部索引鍵關聯性。</span><span class="sxs-lookup"><span data-stu-id="48471-130">**Related Tables** The relationship line indicates that a foreign-key relationship exists between one table and another.</span></span> <span data-ttu-id="48471-131">如果是一對多關聯性，外部索引鍵表即為該行 ∞ 符號旁的資料表。</span><span class="sxs-lookup"><span data-stu-id="48471-131">For a one-to-many relationship, the foreign-key table is the table near the line's figure-eight symbol.</span></span> <span data-ttu-id="48471-132">如果該行的兩個結束點都與同一個資料表連接，則該關聯性即為自反關聯性 (Reflexive Relationship)。</span><span class="sxs-lookup"><span data-stu-id="48471-132">If both endpoints of the line attach to the same table, the relationship is a reflexive relationship.</span></span> <span data-ttu-id="48471-133">如需詳細資訊，請參閱[繪製自反關聯性 &#40;Visual Database Tools&#41;](draw-reflexive-relationships-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="48471-133">For more information, see [Draw Reflexive Relationships &#40;Visual Database Tools&#41;](draw-reflexive-relationships-visual-database-tools.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="48471-134">本章節內容</span><span class="sxs-lookup"><span data-stu-id="48471-134">In this Section</span></span>  
 [<span data-ttu-id="48471-135">了解資料庫圖表擁有權 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="48471-135">Understand Database Diagram Ownership &#40;Visual Database Tools&#41;</span></span>](understand-database-diagram-ownership-visual-database-tools.md)  
  
 [<span data-ttu-id="48471-136">在資料庫圖表設計工具中導覽 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="48471-136">Navigate in Database Diagram Designer &#40;Visual Database Tools&#41;</span></span>](navigate-in-database-diagram-designer-visual-database-tools.md)  
  
 [<span data-ttu-id="48471-137">設定資料庫圖表設計工具 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="48471-137">Set Up Database Diagram Designer &#40;Visual Database Tools&#41;</span></span>](set-up-database-diagram-designer-visual-database-tools.md)  
  
 [<span data-ttu-id="48471-138">升級舊版的資料庫圖表 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="48471-138">Upgrade Database Diagrams from Previous Editions &#40;Visual Database Tools&#41;</span></span>](upgrade-database-diagrams-from-previous-editions-visual-database-tools.md)  
  
 [<span data-ttu-id="48471-139">開啟資料庫圖表設計工具 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="48471-139">Open Database Diagram Designer &#40;Visual Database Tools&#41;</span></span>](open-database-diagram-designer-visual-database-tools.md)  
  
## <a name="see-also"></a><span data-ttu-id="48471-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48471-140">See Also</span></span>  
 <span data-ttu-id="48471-141">[使用資料庫關係圖 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="48471-141">[Work with Database Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="48471-142">[使用資料庫關係圖中的資料表 &#40;Visual Database Tools&#41;](work-with-tables-in-database-diagram-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="48471-142">[Work with Tables in Database Diagram &#40;Visual Database Tools&#41;](work-with-tables-in-database-diagram-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="48471-143">使用圖表配置 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="48471-143">Work with Diagram Layout &#40;Visual Database Tools&#41;</span></span>](work-with-diagram-layout-visual-database-tools.md)  
  
  
