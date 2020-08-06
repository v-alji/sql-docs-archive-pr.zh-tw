---
title: 使用結果窗格中的資料 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- queries [Visual Database Tools]
- result sets [SQL Server], queries
- Query Designer [SQL Server], Results pane
- results [SQL Server], query
- Visual Database Tools [SQL Server], queries
- queries [SQL Server], results
- Results pane
ms.assetid: 4f8a0080-91ef-4442-83ae-53be2f478c54
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1c914b924ee477c3a59d78ae3ec114c88497726a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596419"
---
# <a name="work-with-data-in-the-results-pane-visual-database-tools"></a><span data-ttu-id="db71d-102">使用結果窗格中的資料 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="db71d-102">Work with Data in the Results Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="db71d-103">在您執行查詢或檢視後，結果會顯示在 [結果] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="db71d-103">After you run a query or view, the results are shown in the Results pane.</span></span> <span data-ttu-id="db71d-104">接著您就可以使用這些結果。</span><span class="sxs-lookup"><span data-stu-id="db71d-104">You can then work with those results.</span></span> <span data-ttu-id="db71d-105">例如，您可以加入與刪除資料列，輸入或變更資料，並且輕易地巡覽大筆的結果集。</span><span class="sxs-lookup"><span data-stu-id="db71d-105">For example, you can add and delete rows, input or change data, and easily navigate through large results sets.</span></span>  
  
 <span data-ttu-id="db71d-106">下列資訊可以協助您避免問題，並且有效率地使用結果集。</span><span class="sxs-lookup"><span data-stu-id="db71d-106">The following information can help you avoid problems and work effectively with your results sets.</span></span>  
  
## <a name="returning-the-results-set"></a><span data-ttu-id="db71d-107">傳回結果集</span><span class="sxs-lookup"><span data-stu-id="db71d-107">Returning the results set</span></span>  
 <span data-ttu-id="db71d-108">您可從查詢或檢視傳回結果，並選擇是否僅開啟結果窗格或開啟所有窗格。</span><span class="sxs-lookup"><span data-stu-id="db71d-108">You can return results from either a query or a view and can choose whether to open just the results pane or all panes.</span></span> <span data-ttu-id="db71d-109">不論使用哪一種方式，都會在 [查詢和檢視設計師] 中開啟查詢或檢視。</span><span class="sxs-lookup"><span data-stu-id="db71d-109">In either case the query or view will open in Query and View Designer.</span></span> <span data-ttu-id="db71d-110">兩者的差異在於一個僅顯示 [結果] 窗格，另一個則開啟在 [選項] 對話方塊中所選取的所有視窗。</span><span class="sxs-lookup"><span data-stu-id="db71d-110">The difference is that one opens with only the Results pane showing and the other opens with all windows that have been selected in the Options dialog box.</span></span> <span data-ttu-id="db71d-111">預設值是所有四個窗格 (結果、SQL、圖表與準則)。</span><span class="sxs-lookup"><span data-stu-id="db71d-111">The default is all four panes (Results, SQL, Diagram, and Criteria).</span></span>  
  
 <span data-ttu-id="db71d-112">如需詳細資訊，請參閱[開啟查詢 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="db71d-112">For more information see [Open Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="db71d-113">若要變更查詢或檢視的設計，使其傳回不同的結果集，或依不同的順序傳回資料錄，請參閱[設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) 中所列的主題。</span><span class="sxs-lookup"><span data-stu-id="db71d-113">To change the design of the query or view so it returns a different set of results or returns records in a different order see the topics listed in [Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="db71d-114">您亦可以下列兩種方式來決定是否傳回全部或部份的結果集；當其執行時停止查詢，或在執行查詢前選擇要傳回的結果數量。</span><span class="sxs-lookup"><span data-stu-id="db71d-114">You can also determine whether to return all or part of the results set in two ways--stop the query as it runs or choose how much of results to return before the query is run.</span></span>  
  
## <a name="navigating-in-the-results-pane"></a><span data-ttu-id="db71d-115">在結果窗格中巡覽</span><span class="sxs-lookup"><span data-stu-id="db71d-115">Navigating in the results pane</span></span>  
 <span data-ttu-id="db71d-116">您可使用在 [結果] 窗格下方的巡覽列快速巡覽資料錄。</span><span class="sxs-lookup"><span data-stu-id="db71d-116">You can quickly navigate through the records using the navigation bar at the bottom of the Results pane.</span></span>  
  
 <span data-ttu-id="db71d-117">有按鈕可移至第一筆與最後一筆資料錄、下一筆與前一筆資料錄，以及移至特定資料錄。</span><span class="sxs-lookup"><span data-stu-id="db71d-117">There are buttons for going to the first and last records, the next and previous records, and for going to a particular record.</span></span>  
  
 <span data-ttu-id="db71d-118">若要移至特定資料錄，在巡覽列文字方塊中輸入列號，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="db71d-118">To go to a particular record, type the number of the row in the text box in the navigation bar and then press ENTER.</span></span>  
  
 <span data-ttu-id="db71d-119">如需在查詢和檢視表設計工具中使用鍵盤快速鍵的詳細資訊，請參閱[在查詢和檢視表設計工具中巡覽 &#40;Visual Database Tools&#41;](navigate-in-the-query-and-view-designer-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="db71d-119">For information about using keyboard shortcuts in the Query and View Designer see [Navigate in the Query and View Designer &#40;Visual Database Tools&#41;](navigate-in-the-query-and-view-designer-visual-database-tools.md).</span></span>  
  
## <a name="committing-changes-to-the-database"></a><span data-ttu-id="db71d-120">資料庫認可變更</span><span class="sxs-lookup"><span data-stu-id="db71d-120">Committing changes to the database</span></span>  
 <span data-ttu-id="db71d-121">[結果] 窗格使用開放式並行存取控制，所以方格顯示的是資料庫資料的複本，而不是完整的即時檢視。</span><span class="sxs-lookup"><span data-stu-id="db71d-121">The Results pane uses optimistic concurrency control so the grid shows a copy of the data in the database rather than an entirely live view.</span></span> <span data-ttu-id="db71d-122">依此方式所產生之資料的變更，僅會在您完成資料列的檢視後，認可至資料庫。</span><span class="sxs-lookup"><span data-stu-id="db71d-122">This way changes are only committed to the database after you move off of a row.</span></span> <span data-ttu-id="db71d-123">此方式允許一個以上使用者同時使用資料庫。</span><span class="sxs-lookup"><span data-stu-id="db71d-123">This allows more than one user to work with the database at the same time.</span></span> <span data-ttu-id="db71d-124">若有衝突發生 (例如，其他使用者先變更了您要變更的同一資料列，並將該變更寫入至資料庫)，您會收到發生衝突的訊息，並提供解決方式。</span><span class="sxs-lookup"><span data-stu-id="db71d-124">If there are conflicts (for example if another user changed the same row you changed and committed it to the database before you did) you will receive a message telling you of the conflict and offering resolutions.</span></span>  
  
## <a name="undo-changes-using-esc"></a><span data-ttu-id="db71d-125">使用 ESC 恢復變更</span><span class="sxs-lookup"><span data-stu-id="db71d-125">Undo changes using ESC</span></span>  
 <span data-ttu-id="db71d-126">您僅能恢復資料庫尚未認可的變更。</span><span class="sxs-lookup"><span data-stu-id="db71d-126">You can only undo a change if it hasn't yet been committed to the database.</span></span> <span data-ttu-id="db71d-127">若您尚未完成確認資料錄，或完成確認後但仍收到資料庫將不會認可變更的錯誤訊息，資料庫都將不會認可該資料。</span><span class="sxs-lookup"><span data-stu-id="db71d-127">The data is not committed if you haven't moved off of the record or if once you do move off the record you get an error message indicating the change won't be committed.</span></span> <span data-ttu-id="db71d-128">若資料庫尚未認可該變更，可使用 ESC 鍵將其恢復。</span><span class="sxs-lookup"><span data-stu-id="db71d-128">If it hasn't been committed you can undo the change by using the ESC key.</span></span>  
  
 <span data-ttu-id="db71d-129">若要恢復資料列中所有的變更，請移至尚未編輯的資料列中的資料格，然後按下 ESC 鍵。</span><span class="sxs-lookup"><span data-stu-id="db71d-129">To undo all changes in a row, move to a cell in that row that you have not edited and press the ESC key.</span></span>  
  
 <span data-ttu-id="db71d-130">若要恢復已編輯之特定資料格的變更，請移至該資料格，並按下 ESC 鍵。</span><span class="sxs-lookup"><span data-stu-id="db71d-130">To undo changes to a particular cell that you have edited, move to that cell press the ESC key.</span></span>  
  
## <a name="adding-or-deleting-data-in-the-database"></a><span data-ttu-id="db71d-131">在資料庫中加入或刪除資料</span><span class="sxs-lookup"><span data-stu-id="db71d-131">Adding or deleting data in the database</span></span>  
 <span data-ttu-id="db71d-132">若要了解資料庫設計的運作方式，您可能必須將資料範例加入資料庫中。</span><span class="sxs-lookup"><span data-stu-id="db71d-132">To see how your database design is working you may need to add sample data to the database.</span></span> <span data-ttu-id="db71d-133">您可將它直接輸入至結果窗格，或從另一個程式 (例如，記事本或 Excel) 複製並貼至結果窗格。</span><span class="sxs-lookup"><span data-stu-id="db71d-133">You can enter it into the results pane directly or you can copy it from another program, such as notepad or Excel, and paste it into the results pane.</span></span>  
  
 <span data-ttu-id="db71d-134">除了複製資料列至 [結果] 窗格，您還可以加入新的資料錄，或是修改或刪除現有的資料錄。</span><span class="sxs-lookup"><span data-stu-id="db71d-134">In addition to copying rows into the Results pane you can add new records or modify or delete existing ones.</span></span> <span data-ttu-id="db71d-135">如需詳細資訊，請參閱[在結果窗格中新增資料列 &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md)、[在結果窗格中刪除資料列 &#40;Visual Database Tools&#41;](delete-rows-in-the-results-pane-visual-database-tools.md) 和[在結果窗格中編輯資料列 &#40;Visual Database Tools&#41;](edit-rows-in-the-results-pane-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="db71d-135">For more information see [Add New Rows in the Results Pane &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md), [Delete Rows in the Results Pane &#40;Visual Database Tools&#41;](delete-rows-in-the-results-pane-visual-database-tools.md), and [Edit Rows in the Results Pane &#40;Visual Database Tools&#41;](edit-rows-in-the-results-pane-visual-database-tools.md).</span></span>  
  
## <a name="tips-for-working-with-null-values-and-empty-cells"></a><span data-ttu-id="db71d-136">NULL 值與空資料格的使用提示</span><span class="sxs-lookup"><span data-stu-id="db71d-136">Tips for working with NULL values and empty cells</span></span>  
 <span data-ttu-id="db71d-137">當您按一下空資料列以加入新資料錄時，所有資料行的初始值將為 *NULL*。</span><span class="sxs-lookup"><span data-stu-id="db71d-137">When you click on an empty row to add a new record, the initial value for all columns is *NULL*.</span></span> <span data-ttu-id="db71d-138">若資料行允許 null 值，您可讓它保持原狀。</span><span class="sxs-lookup"><span data-stu-id="db71d-138">If a column allows null values you can leave it as is.</span></span>  
  
 <span data-ttu-id="db71d-139">若想要以 null 值取代非 null 值，則輸入大寫的 NULL。</span><span class="sxs-lookup"><span data-stu-id="db71d-139">If you want to replace a non-null value with null, type NULL in capital letters.</span></span> <span data-ttu-id="db71d-140">[結果] 窗格將會以斜體格式顯示該字，表示其被識別為 null 值而非字串。</span><span class="sxs-lookup"><span data-stu-id="db71d-140">The Results pane will give the word italic formatting to indicate that it is to be recognized as a null value rather than as a string.</span></span>  
  
 <span data-ttu-id="db71d-141">若要輸入字串 "null"，請輸入不帶有引號之字母。</span><span class="sxs-lookup"><span data-stu-id="db71d-141">To type in the string "null" type the letters without quotes.</span></span> <span data-ttu-id="db71d-142">若其中至少有一個字母為小寫，則其值將會被視為字串，而不是 null 值。</span><span class="sxs-lookup"><span data-stu-id="db71d-142">As long as at least one of the letters is in lower case, the value will be treated as a string rather than a null value.</span></span>  
  
 <span data-ttu-id="db71d-143">二進位資料類型的資料行預設值為 NULL。</span><span class="sxs-lookup"><span data-stu-id="db71d-143">Values for columns with a binary data type will have NULL values by default.</span></span> <span data-ttu-id="db71d-144">這些值無法在 [結果] 窗格中進行變更。</span><span class="sxs-lookup"><span data-stu-id="db71d-144">These values can't be changed in the Results pane.</span></span>  
  
 <span data-ttu-id="db71d-145">若要輸入空格取代 null，請刪除現有的文字，並移開資料格。</span><span class="sxs-lookup"><span data-stu-id="db71d-145">To input an empty space instead of using null, delete the existing text and move off of the cell.</span></span>  
  
## <a name="validating-data"></a><span data-ttu-id="db71d-146">驗證資料</span><span class="sxs-lookup"><span data-stu-id="db71d-146">Validating data</span></span>  
 <span data-ttu-id="db71d-147">[查詢和檢視設計師] 可以根據資料行屬性來驗證某些資料。</span><span class="sxs-lookup"><span data-stu-id="db71d-147">The Query and View Designer can validate some kinds of data against the columns properties.</span></span> <span data-ttu-id="db71d-148">例如，若在具有 float 資料類型的資料行中輸入 "abc"，您將會收到錯誤訊息，且資料庫將不會認可這個變更。</span><span class="sxs-lookup"><span data-stu-id="db71d-148">For example, if you enter "abc" into a column with a float data type, you will receive an error and the change will not be committed to the database.</span></span>  
  
 <span data-ttu-id="db71d-149">在 [結果] 窗格中檢視資料行資料類型最快速的方法就是，開啟 [圖表] 窗格，將滑鼠指標停留在資料表或資料表值物件中的資料行名稱上。</span><span class="sxs-lookup"><span data-stu-id="db71d-149">The quickest way to see the data type of a column when you're in the Results pane is to open the Diagram pane and hover over the name of the column in the table or table-valued object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db71d-150">[結果] 窗格所能顯示之文字資料類型的最大長度為 2,147,483,647。</span><span class="sxs-lookup"><span data-stu-id="db71d-150">The maximum length the Results pane can show for a text data type is 2,147,483,647.</span></span>  
  
## <a name="keeping-the-results-set-synchronized-with-the-query-definition"></a><span data-ttu-id="db71d-151">保持結果集與查詢定義同步</span><span class="sxs-lookup"><span data-stu-id="db71d-151">Keeping the results set synchronized with the query definition</span></span>  
 <span data-ttu-id="db71d-152">當您在處理查詢或檢視結果時，[結果] 窗格中的資料錄可能未與查詢定義保持同步。</span><span class="sxs-lookup"><span data-stu-id="db71d-152">While you're working on the results of a query or view it is possible for the records in the results pane to get out of synchronization with the queries definition.</span></span> <span data-ttu-id="db71d-153">例如，若您在資料表中執行五個資料行其中四個的查詢，然後使用 [圖表] 窗格在查詢定義中加入第五個資料行，則第五個資料行的資料將不會自動加入至結果窗格中。</span><span class="sxs-lookup"><span data-stu-id="db71d-153">For example, if you ran a query for four out of five columns in a table, then used the Diagram pane to add the fifth column to the definition of the query, that fifth column's data will not automatically be added to the results pane.</span></span> <span data-ttu-id="db71d-154">若要讓 [結果] 窗格反映新的查詢定義，請再次執行查詢。</span><span class="sxs-lookup"><span data-stu-id="db71d-154">To make the results pane reflect the new query definition, run the query again.</span></span>  
  
 <span data-ttu-id="db71d-155">您能夠判斷是否有這樣的情況發生 -- 在 [結果] 窗格的右下角會有警告圖示以及出現「已變更的查詢」文字，且圖示會在窗格的左上角重複出現。</span><span class="sxs-lookup"><span data-stu-id="db71d-155">You can tell if this happens--an alert icon and the text "Query Changed" appears in the lower-right corner of the results pane and the icon is repeated in the upper-left corner of the pane.</span></span>  
  
## <a name="reconciling-changes-made-by-multiple-users"></a><span data-ttu-id="db71d-156">協調多位使用者進行的變更</span><span class="sxs-lookup"><span data-stu-id="db71d-156">Reconciling changes made by multiple users</span></span>  
 <span data-ttu-id="db71d-157">當您在處理查詢或檢視的結果時，正在使用資料庫的其他使用者可能會變更資料錄。</span><span class="sxs-lookup"><span data-stu-id="db71d-157">While you're working on the results of a query or view it is possible fore the records to be changed by a different user who is also working with the database.</span></span>  
  
 <span data-ttu-id="db71d-158">若發生這種情形，您會在移開資料格時收到衝突通知。</span><span class="sxs-lookup"><span data-stu-id="db71d-158">If this happens you will receive a notice as soon as you move off of the cell with the conflict.</span></span> <span data-ttu-id="db71d-159">然後您便可以覆寫其他使用者的變更、更新其他使用者的變更至 [結果] 窗格或是忽略該變更並繼續您的編輯。</span><span class="sxs-lookup"><span data-stu-id="db71d-159">You will then be able to override the other user's change, update your results pane with the other user's change, or keep editing your results pane without reconciling the differences.</span></span> <span data-ttu-id="db71d-160">如果選擇忽略該變更，則資料庫將不會認可您所做的變更。</span><span class="sxs-lookup"><span data-stu-id="db71d-160">If you choose not to reconcile the differences your changes will not be committed to the database.</span></span>  
  
## <a name="limitations-in-the-results-pane"></a><span data-ttu-id="db71d-161">結果窗格中的限制</span><span class="sxs-lookup"><span data-stu-id="db71d-161">Limitations in the Results pane</span></span>  
  
### <a name="what-can-not-be-updated"></a><span data-ttu-id="db71d-162">何者無法更新</span><span class="sxs-lookup"><span data-stu-id="db71d-162">What can not be updated</span></span>  
 <span data-ttu-id="db71d-163">這些提示有助於順利使用 [結果] 窗格中的資料。</span><span class="sxs-lookup"><span data-stu-id="db71d-163">These tips may help you work successfully with data in the Results pane.</span></span>  
  
-   <span data-ttu-id="db71d-164">包含來自一個以上資料表或檢視的資料行之查詢，無法更新。</span><span class="sxs-lookup"><span data-stu-id="db71d-164">Queries that include columns from more than one table or view can't be updated.</span></span>  
  
-   <span data-ttu-id="db71d-165">檢視僅能在資料庫條件約束允許時進行更新。</span><span class="sxs-lookup"><span data-stu-id="db71d-165">Views can only be updated if the database constraints allow it.</span></span>  
  
-   <span data-ttu-id="db71d-166">由預存程序所傳回的結果無法更新。</span><span class="sxs-lookup"><span data-stu-id="db71d-166">Results returned by a stored procedure can't be updated.</span></span>  
  
-   <span data-ttu-id="db71d-167">使用 GROUP BY、DISTINCT 或 TO XML 子句的查詢或檢視無法更新。</span><span class="sxs-lookup"><span data-stu-id="db71d-167">Queries or views using the GROUP BY, DISTINCT, or TO XML clauses are not updatable.</span></span>  
  
-   <span data-ttu-id="db71d-168">資料表值函數所傳回的結果，只能在某些情況下更新。</span><span class="sxs-lookup"><span data-stu-id="db71d-168">Results returned by table-valued functions can only be updated in some cases.</span></span>  
  
-   <span data-ttu-id="db71d-169">來自查詢運算式結果之資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="db71d-169">Data in columns that result from an expression in the query.</span></span>  
  
-   <span data-ttu-id="db71d-170">提供者未順利轉譯的資料。</span><span class="sxs-lookup"><span data-stu-id="db71d-170">Data that was not successfully translated by the provider.</span></span>  
  
### <a name="what-can-not-be-represented-fully"></a><span data-ttu-id="db71d-171">何者無法完整表示</span><span class="sxs-lookup"><span data-stu-id="db71d-171">What can not be represented fully</span></span>  
 <span data-ttu-id="db71d-172">從資料庫傳回 [結果] 窗格的資料，大部份是由您所使用之資料來源的提供者控制。</span><span class="sxs-lookup"><span data-stu-id="db71d-172">What is returned to the Results pane from the database is greatly controlled by the provider for the data source you are using.</span></span> <span data-ttu-id="db71d-173">[結果] 窗格未必能轉譯來自所有資料庫管理系統之資料。</span><span class="sxs-lookup"><span data-stu-id="db71d-173">The Results pane can't always translate the data from all database management systems.</span></span> <span data-ttu-id="db71d-174">此處的範例即有這種情形。</span><span class="sxs-lookup"><span data-stu-id="db71d-174">Here are come cases where this is so.</span></span>  
  
-   <span data-ttu-id="db71d-175">通常二進位資料類型對於在 [結果] 窗格中工作的人不太有用，而且下載要花費很長的時間。</span><span class="sxs-lookup"><span data-stu-id="db71d-175">Binary data types are often not useful for people working in the Results pane and they can take a very long time to download.</span></span> <span data-ttu-id="db71d-176">因此，它們由 *\<Binary data>* 或 *Null*代表。</span><span class="sxs-lookup"><span data-stu-id="db71d-176">So they are represented by *\<Binary data>* or *Null*.</span></span>  
  
-   <span data-ttu-id="db71d-177">有效位數與小數位數未必會被保留。</span><span class="sxs-lookup"><span data-stu-id="db71d-177">Precision and scale can not always be preserved.</span></span> <span data-ttu-id="db71d-178">例如，[結果] 窗格支援 27 位數的有效位數。</span><span class="sxs-lookup"><span data-stu-id="db71d-178">For example, the Results pane supports a precision of 27.</span></span> <span data-ttu-id="db71d-179">若資料具有較高有效位數的資料類型，則資料可能會被截斷或由 *\<Unable to read data>* 代表。</span><span class="sxs-lookup"><span data-stu-id="db71d-179">If data is of a data type with a greater precision, the data may be truncated or may be represented by *\<Unable to read data>*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db71d-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db71d-180">See Also</span></span>  
 <span data-ttu-id="db71d-181">[使用 &#40;Visual Database Tools 的查詢來執行基本作業&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="db71d-181">[Perform Basic Operations with Queries &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="db71d-182">指定搜尋準則 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="db71d-182">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
