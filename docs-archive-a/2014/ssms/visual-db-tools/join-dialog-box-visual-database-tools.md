---
title: 聯結對話方塊 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.ppg.joinline
- vdtsql.chm:69638
ms.assetid: 0d9516bb-4ad3-4fcf-bb77-93474dea698f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7fbd2b61a080a681b5d15a4b69c466fae76e04e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686688"
---
# <a name="join-dialog-box-visual-database-tools"></a><span data-ttu-id="1a1b8-102">聯結對話方塊 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="1a1b8-102">Join Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="1a1b8-103">使用此對話方塊可指定聯結資料表的選項。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-103">Use this dialog box to specify options for joining tables.</span></span> <span data-ttu-id="1a1b8-104">若要存取此對話方塊，請在 [設計]  窗格中選取聯結線 (Join Line)。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-104">To access this dialog, in the **Design** pane select a join line.</span></span> <span data-ttu-id="1a1b8-105">然後，在 [屬性]  視窗中按一下 [聯結條件及類型]  ，並按一下顯示在屬性右邊的省略符號 **(...)** 。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-105">Then in the **Properties** window click **Join Condition And Type**, and click the ellipses **(...)** that appear to the right of the property.</span></span>  
  
 <span data-ttu-id="1a1b8-106">依照預設，是使用根據包含聯結資料行中符合資訊資料列來建立結果集的內部聯結，將關聯資料表聯結在一起。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-106">By default, related tables are joined using an inner join that creates a result set based on rows containing matching information in the join columns.</span></span> <span data-ttu-id="1a1b8-107">藉由設定 [聯結]  對話方塊中的選項，可以根據不同的運算子指定聯結，也可以指定外部聯結。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-107">By setting options in the **Join** dialog box, you can specify a join based on a different operator, and you can specify an outer join.</span></span>  
  
 <span data-ttu-id="1a1b8-108">如需聯結資料表的詳細資訊，請參閱[使用聯結查詢 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-108">For more information about joining tables, see [Query with Joins &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1a1b8-109">選項。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-109">Options</span></span>  
  
|<span data-ttu-id="1a1b8-110">**字詞**</span><span class="sxs-lookup"><span data-stu-id="1a1b8-110">**Term**</span></span>|<span data-ttu-id="1a1b8-111">**[定義]**</span><span class="sxs-lookup"><span data-stu-id="1a1b8-111">**Definition**</span></span>|  
|--------------|--------------------|  
|<span data-ttu-id="1a1b8-112">**Table**</span><span class="sxs-lookup"><span data-stu-id="1a1b8-112">**Table**</span></span>|<span data-ttu-id="1a1b8-113">聯結中相關資料表或資料表值物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-113">The names of the tables or table-valued objects involved in the join.</span></span> <span data-ttu-id="1a1b8-114">不能在這裡變更資料表的名稱 - 此資訊的顯示僅供參考。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-114">You cannot change the names of the tables here - this information is displayed for information only.</span></span>|  
|<span data-ttu-id="1a1b8-115">**資料行**</span><span class="sxs-lookup"><span data-stu-id="1a1b8-115">**Column**</span></span>|<span data-ttu-id="1a1b8-116">用於聯結資料表的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-116">The names of the columns used for joining the tables.</span></span> <span data-ttu-id="1a1b8-117">運算子清單中的運算子會指定各資料行中資料之間的關係。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-117">The operator in the operator list specifies the relationship between the data in the columns.</span></span> <span data-ttu-id="1a1b8-118">不能在這裡變更資料行的名稱 - 此資訊的顯示僅供參考。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-118">You cannot change the names of the columns here - this information is displayed for information only.</span></span>|  
|<span data-ttu-id="1a1b8-119">**運算子**</span><span class="sxs-lookup"><span data-stu-id="1a1b8-119">**Operator**</span></span>|<span data-ttu-id="1a1b8-120">指定用於關聯聯結資料行的運算子。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-120">Specify the operator used to relate the join columns.</span></span> <span data-ttu-id="1a1b8-121">若要指定等於 (=) 之外的運算子，請從清單中選取。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-121">To specify an operator other than equal (=), select it from the list.</span></span> <span data-ttu-id="1a1b8-122">關閉屬性頁時，您選取的運算子會出現在聯結線的菱形圖中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1a1b8-122">When you close the property page, the operator you selected will appear in the diamond graphic of the join line, as in the following:</span></span><br /><br /> <span data-ttu-id="1a1b8-123">![Visual Database Tools 圖示](../../database-engine/media//dv3wbii.gif "Visual Database Tools 圖示")</span><span class="sxs-lookup"><span data-stu-id="1a1b8-123">![Visual Database Tools icon](../../database-engine/media//dv3wbii.gif "Visual Database Tools icon")</span></span>|  
|<span data-ttu-id="1a1b8-124">**選取所有資料列，從 \<table1>**</span><span class="sxs-lookup"><span data-stu-id="1a1b8-124">**All rows from \<table1>**</span></span>|<span data-ttu-id="1a1b8-125">指定輸出中顯示左邊資料表裡全部的資料列，即使右邊資料表中沒有對應的符合也一樣。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-125">Specify that all the rows from the left table appear in the output, even if there are no corresponding matches in the right table.</span></span> <span data-ttu-id="1a1b8-126">右邊資料表中沒有符合資料的資料行會顯示為 null。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-126">Columns with no matching data in the right table appear as null.</span></span> <span data-ttu-id="1a1b8-127">選擇此選項就等於在 SQL 陳述式中指定 LEFT OUTER JOIN。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-127">Choosing this option is equivalent to specifying LEFT OUTER JOIN in the SQL statement.</span></span>|  
|<span data-ttu-id="1a1b8-128">**選取所有資料列，從 \<table2>**</span><span class="sxs-lookup"><span data-stu-id="1a1b8-128">**All rows from \<table2>**</span></span>|<span data-ttu-id="1a1b8-129">指定輸出中顯示右邊資料表裡全部的資料列，即使左邊資料表中沒有對應的符合也一樣。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-129">Specify that all the rows from the right table appear in the output, even if there are no corresponding matches in the left table.</span></span> <span data-ttu-id="1a1b8-130">左邊資料表中沒有符合資料的資料行會顯示為 null。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-130">Columns with no matching data in the left table appear as null.</span></span> <span data-ttu-id="1a1b8-131">選擇此選項就等於在 SQL 陳述式中指定 RIGHT OUTER JOIN。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-131">Choosing this option is equivalent to specifying RIGHT OUTER JOIN in the SQL statement.</span></span>|  
  
 <span data-ttu-id="1a1b8-132">同時選取 [選取所有資料列，從 \<table1>] 和 [選取所有資料列，從 \<table2>]，與在 SQL 陳述式中指定 FULL OUTER JOIN 相同。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-132">Selecting both All **rows from \<table1>** and **All rows from \<table2>** is equivalent to specifying FULL OUTER JOIN in the SQL statement.</span></span>  
  
 <span data-ttu-id="1a1b8-133">選取某個選項建立外部聯結時，聯結線中的菱形圖就會改變，以指示聯結為左邊外部、右邊外部或完整外部聯結。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-133">When you select an option to create an outer join, the diamond graphic in the join line changes to indicate that the join is a left outer, right outer, or full outer join.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1a1b8-134">「左邊」和「右邊」這兩個字不一定對應到 [圖表] 窗格中的資料表位置。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-134">The words "left" and "right" do not necessarily correspond to the position of tables in the Diagram pane.</span></span> <span data-ttu-id="1a1b8-135">「左邊」指的是在 SQL 陳述式中名稱出現在關鍵字 JOIN 左邊的資料表，「右邊」指的是名稱出現在關鍵字 JOIN 右邊的資料表。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-135">"Left" refers to the table whose name appears to the left of the keyword JOIN in the SQL statement, and "right" refers to the table whose name appears to the right of the JOIN keyword.</span></span> <span data-ttu-id="1a1b8-136">如果在 [圖表]  窗格中移動資料表，則不必變更資料表是左邊或右邊的考量。</span><span class="sxs-lookup"><span data-stu-id="1a1b8-136">If you move tables in the **Diagram** pane, you do not change which table is considered left or right.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a1b8-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a1b8-137">See Also</span></span>  
 <span data-ttu-id="1a1b8-138">[使用 Join 查詢 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="1a1b8-138">[Query with Joins &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="1a1b8-139">設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="1a1b8-139">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
