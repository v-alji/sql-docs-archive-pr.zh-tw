---
title: 查詢和視圖設計工具如何表示 (Visual Database Tools) 的聯結 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL pane [Visual Database Tools]
- joins [SQL Server], Query and View Designer
- Diagram pane [Visual Database Tools]
ms.assetid: 20a99dcb-83bd-4aa6-9139-92e2e5ba4887
author: stevestein
ms.author: sstein
ms.openlocfilehash: 55fdea533436f9fa7c2a902667b3166085c27e99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596980"
---
# <a name="how-the-query-and-view-designer-represents-joins-visual-database-tools"></a><span data-ttu-id="8fb83-102">查詢和檢視設計工具表示聯結的方式 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8fb83-102">How the Query and View Designer Represents Joins (Visual Database Tools)</span></span>
  <span data-ttu-id="8fb83-103">如果資料表是聯結的， [查詢和檢視表設計工具](visual-database-tools.md) 將在 [圖表窗格](diagram-pane-visual-database-tools.md) 中以圖形表示該聯結，並在 [SQL 窗格](sql-pane-visual-database-tools.md)中使用 SQL 語法。</span><span class="sxs-lookup"><span data-stu-id="8fb83-103">If tables are joined, the [Query and View Designer](visual-database-tools.md) represents the join graphically in the [Diagram pane](diagram-pane-visual-database-tools.md) and by using SQL syntax in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
## <a name="diagram-pane"></a><span data-ttu-id="8fb83-104">圖表窗格</span><span class="sxs-lookup"><span data-stu-id="8fb83-104">Diagram Pane</span></span>  
 <span data-ttu-id="8fb83-105">[查詢和檢視設計師] 會在 [圖表] 窗格中，顯示與聯結相關之資料行之間的聯結線。</span><span class="sxs-lookup"><span data-stu-id="8fb83-105">In the Diagram pane the Query and View Designer displays a join line between the data columns involved in the join.</span></span> <span data-ttu-id="8fb83-106">查詢和檢視設計師可顯示每個聯結狀況的聯結線。</span><span class="sxs-lookup"><span data-stu-id="8fb83-106">The Query and View Designer displays one join line for each join condition.</span></span> <span data-ttu-id="8fb83-107">例如，下列圖示即說明兩個聯結的資料表之間的聯結線：</span><span class="sxs-lookup"><span data-stu-id="8fb83-107">For example, the following illustration shows a join line between two tables that are joined:</span></span>  
  
 <span data-ttu-id="8fb83-108">![聯結線會顯示兩個資料表之間的關聯性](../../database-engine/media//dv3wbig.gif "聯結線會顯示兩個資料表之間的關聯性")</span><span class="sxs-lookup"><span data-stu-id="8fb83-108">![Join line shows relationship between two tables](../../database-engine/media//dv3wbig.gif "Join line shows relationship between two tables")</span></span>  
  
 <span data-ttu-id="8fb83-109">如果資料表使用一個以上的聯結條件來進行聯結，查詢和檢視設計師將顯示多重聯結線，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8fb83-109">If tables are joined using more than one join condition, the Query and View Designer displays multiple join lines, as in the following example:</span></span>  
  
 <span data-ttu-id="8fb83-110">![使用一個以上聯結條件所聯結的資料表](../../database-engine/media//dv3w9n1.gif "使用一個以上聯結條件所聯結的資料表")</span><span class="sxs-lookup"><span data-stu-id="8fb83-110">![Tables joined using more than one join condition](../../database-engine/media//dv3w9n1.gif "Tables joined using more than one join condition")</span></span>  
  
 <span data-ttu-id="8fb83-111">如果聯結線並未顯示 (例如，代表資料表或表格化物件的矩形被最小化，或該聯結使用運算式)，查詢和檢視設計師將在代表資料表或表格化物件的矩形標題列上放置聯結線。</span><span class="sxs-lookup"><span data-stu-id="8fb83-111">If the joined data columns are not displayed (for example, the rectangle representing the table or table-structured object is minimized or the join involves an expression), the Query and View Designer places the join line at the title bar of the rectangle representing the table or table-structured object.</span></span>  
  
 <span data-ttu-id="8fb83-112">聯結線中間的圖示形狀即表示資料表或表格化物件的聯結方式。</span><span class="sxs-lookup"><span data-stu-id="8fb83-112">The shape of the icon in the middle of the join line indicates how the tables or table-structured objects are joined.</span></span> <span data-ttu-id="8fb83-113">如果聯結子句使用等號 (=) 以外的運算子，該運算子將出現在聯結線圖示中。</span><span class="sxs-lookup"><span data-stu-id="8fb83-113">If the join clause uses an operator other than equal (=), the operator appears in the join line icon.</span></span> <span data-ttu-id="8fb83-114">下表將列出可顯現於聯結線中的圖示。</span><span class="sxs-lookup"><span data-stu-id="8fb83-114">The following table lists the icons that appear in the join line.</span></span>  
  
|<span data-ttu-id="8fb83-115">**聯結線圖示**</span><span class="sxs-lookup"><span data-stu-id="8fb83-115">**Join line icon**</span></span>|<span data-ttu-id="8fb83-116">**說明**</span><span class="sxs-lookup"><span data-stu-id="8fb83-116">**Description**</span></span>|  
|------------------------|---------------------|  
|<span data-ttu-id="8fb83-117">![Visual Database Tools 圖示](../../database-engine/media//dv3wbih.gif "Visual Database Tools 圖示")</span><span class="sxs-lookup"><span data-stu-id="8fb83-117">![Visual Database Tools icon](../../database-engine/media//dv3wbih.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="8fb83-118">內部聯結 (使用等號建立)。</span><span class="sxs-lookup"><span data-stu-id="8fb83-118">Inner join (created using an equal sign).</span></span>|  
|<span data-ttu-id="8fb83-119">![Visual Database Tools 圖示](../../database-engine/media//dv3wbii.gif "Visual Database Tools 圖示")</span><span class="sxs-lookup"><span data-stu-id="8fb83-119">![Visual Database Tools icon](../../database-engine/media//dv3wbii.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="8fb83-120">使用「大於」運算子的內部聯結。</span><span class="sxs-lookup"><span data-stu-id="8fb83-120">Inner join based on the "greater than" operator.</span></span>|  
|<span data-ttu-id="8fb83-121">![Visual Database Tools 圖示](../../database-engine/media//dv3wbij.gif "Visual Database Tools 圖示")</span><span class="sxs-lookup"><span data-stu-id="8fb83-121">![Visual Database Tools icon](../../database-engine/media//dv3wbij.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="8fb83-122">外部聯結，將包括左邊資料表的所有資料列，即使該資料表在相關資料表並沒有相符項目。</span><span class="sxs-lookup"><span data-stu-id="8fb83-122">Outer join in which all rows from the table represented on the left will be included, even if they do not have matches in the related table.</span></span>|  
|<span data-ttu-id="8fb83-123">![Visual Database Tools 圖示](../../database-engine/media//dv3wbik.gif "Visual Database Tools 圖示")</span><span class="sxs-lookup"><span data-stu-id="8fb83-123">![Visual Database Tools icon](../../database-engine/media//dv3wbik.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="8fb83-124">外部聯結，將包括右邊資料表的所有資料列，即使該資料表在相關資料表中並沒有相符項目。</span><span class="sxs-lookup"><span data-stu-id="8fb83-124">Outer join in which all rows from the table represented on the right will be included, even if they do not have matches in the related table.</span></span>|  
|<span data-ttu-id="8fb83-125">![Visual Database Tools 圖示](../../database-engine/media//dv3wbil.gif "Visual Database Tools 圖示")</span><span class="sxs-lookup"><span data-stu-id="8fb83-125">![Visual Database Tools icon](../../database-engine/media//dv3wbil.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="8fb83-126">完整的外部聯結，將同時包括兩邊資料表的所有資料列，即使該資料表在相關資料表中並沒有相符項目。</span><span class="sxs-lookup"><span data-stu-id="8fb83-126">Full outer join in which all rows from both tables will be included, even if they do not have matches in the related table.</span></span>|  
  
 <span data-ttu-id="8fb83-127">聯結線結束部分的符號可表示聯結的類型。</span><span class="sxs-lookup"><span data-stu-id="8fb83-127">The symbols on the ends of the join line indicate the type of join.</span></span> <span data-ttu-id="8fb83-128">下表即列出聯結的類型和聯結線結束部分所顯示的圖示。</span><span class="sxs-lookup"><span data-stu-id="8fb83-128">The following table lists the types of joins and the icons displayed on the ends of the join line.</span></span>  
  
|<span data-ttu-id="8fb83-129">**聯結線結束部分所顯示的圖示**</span><span class="sxs-lookup"><span data-stu-id="8fb83-129">**Icon on ends of join line**</span></span>|<span data-ttu-id="8fb83-130">**聯結類型**</span><span class="sxs-lookup"><span data-stu-id="8fb83-130">**Type of join**</span></span>|  
|-----------------------------------|----------------------|  
|<span data-ttu-id="8fb83-131">![Visual Database Tools 圖示](../../database-engine/media//dv3wbim.gif "Visual Database Tools 圖示")</span><span class="sxs-lookup"><span data-stu-id="8fb83-131">![Visual Database Tools icon](../../database-engine/media//dv3wbim.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="8fb83-132">一對一聯結。</span><span class="sxs-lookup"><span data-stu-id="8fb83-132">One-to-one join.</span></span>|  
|<span data-ttu-id="8fb83-133">![Visual Database Tools 圖示](../../database-engine/media//dv3wbin.gif "Visual Database Tools 圖示")</span><span class="sxs-lookup"><span data-stu-id="8fb83-133">![Visual Database Tools icon](../../database-engine/media//dv3wbin.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="8fb83-134">一對多聯結。</span><span class="sxs-lookup"><span data-stu-id="8fb83-134">One-to-many join.</span></span>|  
|<span data-ttu-id="8fb83-135">![Visual Database Tools 圖示](../../database-engine/media//dv3wbio.gif "Visual Database Tools 圖示")</span><span class="sxs-lookup"><span data-stu-id="8fb83-135">![Visual Database Tools icon](../../database-engine/media//dv3wbio.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="8fb83-136">查詢和檢視設計師無法決定聯結類型。</span><span class="sxs-lookup"><span data-stu-id="8fb83-136">Query and View Designer cannot determine the join type.</span></span> <span data-ttu-id="8fb83-137">當您手動建立某個聯結後，常會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="8fb83-137">This situation occurs most often when you have created a join manually.</span></span>|  
  
## <a name="sql-pane"></a><span data-ttu-id="8fb83-138">SQL 窗格</span><span class="sxs-lookup"><span data-stu-id="8fb83-138">SQL Pane</span></span>  
 <span data-ttu-id="8fb83-139">SQL 陳述式有數種方法來表示聯結。</span><span class="sxs-lookup"><span data-stu-id="8fb83-139">A join can be expressed in a number of ways in an SQL statement.</span></span> <span data-ttu-id="8fb83-140">確切的語法則視您使用的資料庫和您定義聯結的方式而定。</span><span class="sxs-lookup"><span data-stu-id="8fb83-140">The exact syntax depends on the database you are using and on how you have defined the join.</span></span>  
  
 <span data-ttu-id="8fb83-141">聯結資料表的語法選項包括：</span><span class="sxs-lookup"><span data-stu-id="8fb83-141">Syntax options for joining tables include:</span></span>  
  
-   <span data-ttu-id="8fb83-142">**FROM 子句的 JOIN 限定詞**。</span><span class="sxs-lookup"><span data-stu-id="8fb83-142">**JOIN qualifier for the FROM clause**.</span></span>   <span data-ttu-id="8fb83-143">關鍵字 INNER 和 OUTER 將指定聯結類型。</span><span class="sxs-lookup"><span data-stu-id="8fb83-143">The keywords INNER and OUTER specify the join type.</span></span> <span data-ttu-id="8fb83-144">這為 ANSI 92 SQL 的標準語法。</span><span class="sxs-lookup"><span data-stu-id="8fb83-144">This syntax is standard for ANSI 92 SQL.</span></span>  
  
     <span data-ttu-id="8fb83-145">例如，如果您根據每個資料表中的 `publishers` 資料行來聯結 `pub_info` 和 `pub_id` 資料表，將產生以下 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="8fb83-145">For example, if you join the `publishers` and `pub_info` tables based on the `pub_id` column in each table, the resulting SQL statement might look like this:</span></span>  
  
    ```  
    SELECT *  
    FROM publishers INNER JOIN pub_info ON  
       publishers.pub_id = pub_info.pub_id  
    ```  
  
     <span data-ttu-id="8fb83-146">如果您要建立外部聯結，LEFT OUTER 或 RIGHT OUTER 等字樣將取代 INNER 一字。</span><span class="sxs-lookup"><span data-stu-id="8fb83-146">If you create an outer join, the words LEFT OUTER or RIGHT OUTER appear in place of the word INNER.</span></span>  
  
-   <span data-ttu-id="8fb83-147">**WHERE 子句將比較兩個資料表中的資料行**。</span><span class="sxs-lookup"><span data-stu-id="8fb83-147">**WHERE clause compares columns in both tables**.</span></span>   <span data-ttu-id="8fb83-148">如果資料庫不支援 JOIN 語法 (或者您自行輸入該語法)，則將出現 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="8fb83-148">A WHERE clause appears if the database does not support the JOIN syntax (or if you entered it yourself).</span></span> <span data-ttu-id="8fb83-149">如果在 WHERE 子句中建立聯結，FROM 子句將同時出現這兩個資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="8fb83-149">If the join is created in the WHERE clause, both table names appear in the FROM clause.</span></span>  
  
     <span data-ttu-id="8fb83-150">例如，下列陳述式即聯結了 `publishers` 和 `pub_info` 資料表。</span><span class="sxs-lookup"><span data-stu-id="8fb83-150">For example, the following statement joins the `publishers` and `pub_info` tables.</span></span>  
  
    ```  
    SELECT *  
    FROM publishers, pub_info  
    WHERE publishers.pub_id = pub_info.pub_id  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8fb83-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fb83-151">See Also</span></span>  
 <span data-ttu-id="8fb83-152">[使用 Join 查詢 &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="8fb83-152">[Query with Joins &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="8fb83-153">聯結對話方塊 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="8fb83-153">Join Dialog Box &#40;Visual Database Tools&#41;</span></span>](join-dialog-box-visual-database-tools.md)  
  
  
