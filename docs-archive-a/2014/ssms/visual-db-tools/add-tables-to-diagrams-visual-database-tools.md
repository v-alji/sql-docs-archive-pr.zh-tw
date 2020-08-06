---
title: 將資料表加入圖表 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting tables
- adding tables
ms.assetid: 5440fdf7-ac04-4325-9f32-181f4cd402e5
author: stevestein
ms.author: sstein
ms.openlocfilehash: fe5c1274ac390f4834bd8ac1088258061fc0406d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596437"
---
# <a name="add-tables-to-diagrams-visual-database-tools"></a><span data-ttu-id="32f92-102">將資料表加入圖表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="32f92-102">Add Tables to Diagrams (Visual Database Tools)</span></span>
  <span data-ttu-id="32f92-103">您可以加入資料表至資料庫圖表中，以編輯其結構或使它關聯圖表中的其他資料表。</span><span class="sxs-lookup"><span data-stu-id="32f92-103">You can add a table to your database diagram to edit its structure or relate it to other tables in your diagram.</span></span> <span data-ttu-id="32f92-104">也可以加入現有的資料庫資料表至圖表中，或插入尚未在資料庫中定義的新資料表。</span><span class="sxs-lookup"><span data-stu-id="32f92-104">You can either add existing database tables to a diagram or insert a new table that has not yet been defined in the database.</span></span>  
  
### <a name="to-insert-a-new-table-into-a-diagram"></a><span data-ttu-id="32f92-105">若要將新資料表插入圖表中</span><span class="sxs-lookup"><span data-stu-id="32f92-105">To insert a new table into a diagram</span></span>  
  
1.  <span data-ttu-id="32f92-106">確定您已經連接想要建立資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="32f92-106">Make sure you are connected to the database in which you want to create the table.</span></span>  
  
     <span data-ttu-id="32f92-107">若要在目前的圖表中建立資料表，請按一下工具列上的 [新增資料表]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="32f92-107">To create a table in your current diagram, click the **New Table** button on the toolbar.</span></span>  
  
     <span data-ttu-id="32f92-108">-或-</span><span class="sxs-lookup"><span data-stu-id="32f92-108">-or-</span></span>  
  
     <span data-ttu-id="32f92-109">在圖表上按一下滑鼠右鍵，然後選取 [新增資料表]  。</span><span class="sxs-lookup"><span data-stu-id="32f92-109">Right-click in the diagram and select **New Table**.</span></span>  
  
2.  <span data-ttu-id="32f92-110">在 [選擇名稱]  對話方塊中，修改或接受系統指派的資料表名稱，然後選擇 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="32f92-110">Modify or accept the system-assigned table name, in the **Choose Name** dialog box, and then choose **OK**.</span></span>  
  
     <span data-ttu-id="32f92-111">新資料表會以標準檢視顯示於圖表中。</span><span class="sxs-lookup"><span data-stu-id="32f92-111">A new table appears in the diagram in Standard view.</span></span>  
  
3.  <span data-ttu-id="32f92-112">在新資料表的第一個資料格中，輸入資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="32f92-112">In the first cell of the new table, type a column name.</span></span> <span data-ttu-id="32f92-113">然後按下 TAB 鍵以移至下一個資料格。</span><span class="sxs-lookup"><span data-stu-id="32f92-113">Then press the TAB key to move to the next cell.</span></span>  
  
4.  <span data-ttu-id="32f92-114">在 [資料類型]  下，選取資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="32f92-114">Under **Data Type**, select a data type for the column.</span></span> <span data-ttu-id="32f92-115">每個資料行都必須有名稱和資料類型。</span><span class="sxs-lookup"><span data-stu-id="32f92-115">Each column must have a name and data type.</span></span>  
  
     <span data-ttu-id="32f92-116">您可以在 [資料表設計工具] 中設定資料行的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="32f92-116">You can set the column's other properties in Table Designer.</span></span>  
  
5.  <span data-ttu-id="32f92-117">對想要加入資料表的每個資料行重複步驟 3 和 4。</span><span class="sxs-lookup"><span data-stu-id="32f92-117">Repeat steps 3 and 4 for each column you want to add to the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32f92-118">在儲存資料庫圖表時，新資料表就會加入資料庫中。</span><span class="sxs-lookup"><span data-stu-id="32f92-118">When you save your database diagram, the new table will be added to your database.</span></span>  
  
### <a name="to-add-an-existing-table-to-a-diagram"></a><span data-ttu-id="32f92-119">若要將現有的資料表加入圖表中</span><span class="sxs-lookup"><span data-stu-id="32f92-119">To add an existing table to a diagram</span></span>  
  
1.  <span data-ttu-id="32f92-120">確定您已經連接到想要編輯資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="32f92-120">Make sure you are connected to the database whose tables you want to edit.</span></span>  
  
2.  <span data-ttu-id="32f92-121">在 [資料表]  資料夾中選取資料表。</span><span class="sxs-lookup"><span data-stu-id="32f92-121">Select a table in the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="32f92-122">將資料表拖曳至資料庫圖表中。</span><span class="sxs-lookup"><span data-stu-id="32f92-122">Drag the table into your database diagram.</span></span>  
  
4.  <span data-ttu-id="32f92-123">放開滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="32f92-123">Release the mouse button.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32f92-124">如果選定的資料表與圖表中其他資料表之間有關聯性，則會自動繪出其關聯線。</span><span class="sxs-lookup"><span data-stu-id="32f92-124">If relationships exist between the selected table and other tables in your diagram, relationship lines are automatically drawn.</span></span>  
  
### <a name="to-add-related-tables-to-a-diagram"></a><span data-ttu-id="32f92-125">若要將關聯資料表加入圖表</span><span class="sxs-lookup"><span data-stu-id="32f92-125">To add related tables to a diagram</span></span>  
  
1.  <span data-ttu-id="32f92-126">在資料庫圖表中選取一個或多個具有外部索引鍵條件約束的資料表。</span><span class="sxs-lookup"><span data-stu-id="32f92-126">Select one or more tables with foreign key constraints in the database diagram.</span></span>  
  
2.  <span data-ttu-id="32f92-127">在選取的資料表上按一下滑鼠右鍵，然後選擇 [加入關聯資料表]  。</span><span class="sxs-lookup"><span data-stu-id="32f92-127">Right-click any of the selected tables and choose **Add Related Tables**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32f92-128">選定的資料表的外部索引鍵條件約束所參考的資料表，以及參考具有外部索引鍵條件約束的選定資料表的資料表，都會加入圖表中。</span><span class="sxs-lookup"><span data-stu-id="32f92-128">Both those tables referenced by a foreign key constraint from the selected table(s) and those referencing the selected table(s) with a foreign key constraint are added to the diagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32f92-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32f92-129">See Also</span></span>  
 <span data-ttu-id="32f92-130">[使用資料庫關係圖 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="32f92-130">[Work with Database Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="32f92-131">使用資料庫圖表中的資料表 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="32f92-131">Work with Tables in Database Diagram &#40;Visual Database Tools&#41;</span></span>](work-with-tables-in-database-diagram-visual-database-tools.md)  
  
  
