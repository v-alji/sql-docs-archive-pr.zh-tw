---
title: 檢視統計資料屬性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.statistics.details.f1
helpviewer_keywords:
- viewing statistics properties
- statistics [SQL Server], viewing properties
ms.assetid: 0eaa2101-006e-4015-9979-3468b50e0aaa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 63cabc5d8844982604993acac6a791317ee36925
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599406"
---
# <a name="view-statistics-properties"></a><span data-ttu-id="9e4ed-102">檢視統計資料屬性</span><span class="sxs-lookup"><span data-stu-id="9e4ed-102">View Statistics Properties</span></span>
  <span data-ttu-id="9e4ed-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中針對資料表或索引檢視表顯示目前的查詢最佳化統計資料。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-103">You can display current query optimization statistics for a table or indexed view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="9e4ed-104">統計資料物件包含標頭 (其中包含有關統計資料的中繼資料)、長條圖 (包含統計資料物件之第一個索引鍵資料行中的值分佈)，以及用來測量跨資料行關聯的密度向量。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-104">Statistics objects include a header with metadata about the statistics, a histogram with the distribution of values in the first key column of the statistics object, and a density vector to measure cross-column correlation.</span></span> <span data-ttu-id="9e4ed-105">如需長條圖和密度向量的詳細資訊，請參閱 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="9e4ed-105">For more information about histograms and density vectors, see [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql)</span></span>  
  
 <span data-ttu-id="9e4ed-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9e4ed-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9e4ed-108">安全性</span><span class="sxs-lookup"><span data-stu-id="9e4ed-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9e4ed-109">**若要使用下列項目檢視統計資料屬性：**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-109">**To view statistics properties, using:**</span></span>  
  
     [<span data-ttu-id="9e4ed-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9e4ed-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9e4ed-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9e4ed-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9e4ed-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="9e4ed-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9e4ed-113">Security</span><span class="sxs-lookup"><span data-stu-id="9e4ed-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9e4ed-114">權限</span><span class="sxs-lookup"><span data-stu-id="9e4ed-114">Permissions</span></span>  
 <span data-ttu-id="9e4ed-115">使用者必須擁有資料表，或者使用者必須是系統管理員 (`sysadmin`) 固定伺服器角色、`db_owner` 固定資料庫角色或 `db_ddladmin` 固定資料庫角色的成員，才能檢視統計資料物件。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-115">In order to view the statistics object, the user must own the table or the user must be a member of the `sysadmin` fixed server role, the `db_owner` fixed database role, or the `db_ddladmin` fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9e4ed-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9e4ed-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-statistics-properties"></a><span data-ttu-id="9e4ed-117">若要檢視統計資料屬性</span><span class="sxs-lookup"><span data-stu-id="9e4ed-117">To view statistics properties</span></span>  
  
1.  <span data-ttu-id="9e4ed-118">在 **[物件總管]** 中，按一下加號展開要在其中建立新統計資料的資料庫。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-118">In **Object Explorer**, click the plus sign to expand the database in which you want to create a new statistic.</span></span>  
  
2.  <span data-ttu-id="9e4ed-119">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-119">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="9e4ed-120">按一下加號展開要在其中檢視統計資料屬性的資料表。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-120">Click the plus sign to expand the table in which you want to view the statistic's properties.</span></span>  
  
4.  <span data-ttu-id="9e4ed-121">按一下加號展開 **[統計資料]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-121">Click the plus sign to expand the **Statistics** folder.</span></span>  
  
5.  <span data-ttu-id="9e4ed-122">以滑鼠右鍵按一下要檢視其屬性的統計資料物件，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-122">Right-click the Statistics object of which you want to view the properties and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="9e4ed-123">在 [統計資料屬性 - _statistics_name_] 對話方塊的 [選取頁面] 窗格中，選取 [詳細資料]。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-123">In the **Statistics Properties -** _statistics_name_ dialog box, in the **Select a page** pane, select **Details**.</span></span>  
  
     <span data-ttu-id="9e4ed-124">下列屬性會在 [統計資料屬性 - _statistics_name_] 對話方塊的 [詳細資料] 頁面中顯示。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-124">The following properties show on the **Details** page in the **Statistics Properties -** _statistics_name_ dialog box.</span></span>  
  
     <span data-ttu-id="9e4ed-125">**資料表名稱**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-125">**Table Name**</span></span>  
     <span data-ttu-id="9e4ed-126">顯示統計資料所描述的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-126">Displays the name of the table described by the statistics.</span></span>  
  
     <span data-ttu-id="9e4ed-127">**統計資料名稱**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-127">**Statistics Name**</span></span>  
     <span data-ttu-id="9e4ed-128">顯示儲存統計資料的資料庫物件名稱。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-128">Displays the name of the database object where the statistics are stored.</span></span>  
  
     <span data-ttu-id="9e4ed-129">**INDEXstatistics_name 的統計資料**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-129">**Statistics for INDEXstatistics_name**</span></span>  
     <span data-ttu-id="9e4ed-130">此文字方塊顯示從統計資料物件傳回的屬性。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-130">This text box shows the properties returned from the statistics object.</span></span> <span data-ttu-id="9e4ed-131">此屬性分為三個區段：統計資料標頭、密度向量和長條圖。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-131">This properties are divided into three sections: Stats Header, Density Vector, and Histogram.</span></span>  
  
     <span data-ttu-id="9e4ed-132">下列資訊描述結果集針對統計資料標頭所傳回的資料行。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-132">The following information describes the columns returned in the result set for the Stats Header.</span></span>  
  
     <span data-ttu-id="9e4ed-133">**名稱**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-133">**Name**</span></span>  
     <span data-ttu-id="9e4ed-134">統計資料物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-134">Name of the statistics object.</span></span>  
  
     <span data-ttu-id="9e4ed-135">**已更新**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-135">**Updated**</span></span>  
     <span data-ttu-id="9e4ed-136">上次更新統計資料的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-136">Date and time the statistics were last updated.</span></span>  
  
     <span data-ttu-id="9e4ed-137">**資料列**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-137">**Rows**</span></span>  
     <span data-ttu-id="9e4ed-138">上一次更新統計資料時位於資料表或索引檢視表中的資料列總數。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-138">Total number of rows in the table or indexed view when the statistics were last updated.</span></span> <span data-ttu-id="9e4ed-139">如果篩選了統計資料或是統計資料對應至篩選過的索引，此資料列數可能會少於資料表中的資料列數。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-139">If the statistics are filtered or correspond to a filtered index, the number of rows might be less than the number of rows in the table.</span></span>  
  
     <span data-ttu-id="9e4ed-140">**取樣的資料列**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-140">**Rows Sampled**</span></span>  
     <span data-ttu-id="9e4ed-141">針對統計資料計算進行取樣的資料列總數。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-141">Total number of rows sampled for statistics calculations.</span></span> <span data-ttu-id="9e4ed-142">如果取樣的資料列數 < 資料列數，顯示的長條圖和密度結果將會是根據取樣資料列數的預估值。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-142">If Rows Sampled < Rows, the displayed histogram and density results are estimates based on the sampled rows.</span></span>  
  
     <span data-ttu-id="9e4ed-143">**步驟**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-143">**Steps**</span></span>  
     <span data-ttu-id="9e4ed-144">長條圖中的步驟數。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-144">Number of steps in the histogram.</span></span> <span data-ttu-id="9e4ed-145">每一個步驟都會跨越某個範圍的資料行值，後面緊接著上限資料行值。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-145">Each step spans a range of column values followed by an upper bound column value.</span></span> <span data-ttu-id="9e4ed-146">長條圖步驟會在統計資料中的第一個索引鍵資料行上定義。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-146">The histogram steps are defined on the first key column in the statistics.</span></span> <span data-ttu-id="9e4ed-147">步驟數的最大值為 200。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-147">The maximum number of steps is 200.</span></span>  
  
     <span data-ttu-id="9e4ed-148">**密度**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-148">**Density**</span></span>  
     <span data-ttu-id="9e4ed-149">針對統計資料物件第一個索引鍵資料行中的所有值，計算為 1 / 相異值，不包括長條圖界限值。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-149">Calculated as 1 / *distinct values* for all values in the first key column of the statistics object, excluding the histogram boundary values.</span></span> <span data-ttu-id="9e4ed-150">查詢最佳化工具不會使用這個密度值，而且會針對與 SQL Server 2008 之前版本之間的回溯相容性顯示。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-150">This Density value is not used by the query optimizer and is displayed for backward compatibility with versions before SQL Server 2008.</span></span>  
  
     <span data-ttu-id="9e4ed-151">**平均索引鍵長度**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-151">**Average Key Length**</span></span>  
     <span data-ttu-id="9e4ed-152">針對統計資料物件中的所有索引鍵資料行計算之每個值的平均位元組數。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-152">Average number of bytes per value for all of the key columns in the statistics object.</span></span>  
  
     <span data-ttu-id="9e4ed-153">**String Index**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-153">**String Index**</span></span>  
     <span data-ttu-id="9e4ed-154">Yes 表示統計資料物件包含了字串摘要統計資料來改善使用 LIKE 運算子之查詢述詞的基數預估，例如 `WHERE ProductName LIKE '%Bike'`。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-154">Yes indicates the statistics object contains string summary statistics to improve the cardinality estimates for query predicates that use the LIKE operator; for example, `WHERE ProductName LIKE '%Bike'`.</span></span> <span data-ttu-id="9e4ed-155">字串摘要統計資料會與長條圖分開儲存，而且會在具有 **char**、 **varchar**、 **nchar**、 **nvarchar**、 **varchar(max)** 、 **nvarchar(max)** 、 **text**或 **ntext**類型時於統計資料物件的第一個索引鍵資料行上建立。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-155">String summary statistics are stored separately from the histogram and are created on the first key column of the statistics object when it is of type **char**, **varchar**, **nchar**, **nvarchar**, **varchar(max)**, **nvarchar(max)**, **text**, or **ntext**.</span></span>  
  
     <span data-ttu-id="9e4ed-156">**篩選運算式**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-156">**Filter Expression**</span></span>  
     <span data-ttu-id="9e4ed-157">包含在統計資料物件中之資料表資料列子集的述詞。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-157">Predicate for the subset of table rows included in the statistics object.</span></span> <span data-ttu-id="9e4ed-158">NULL = 非篩選的統計資料。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-158">NULL = non-filtered statistics.</span></span>  
  
     <span data-ttu-id="9e4ed-159">**Unfiltered Rows**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-159">**Unfiltered Rows**</span></span>  
     <span data-ttu-id="9e4ed-160">套用篩選運算式之前，資料表中的資料列總數。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-160">Total number of rows in the table before applying the filter expression.</span></span> <span data-ttu-id="9e4ed-161">如果 Filter Expression 為 NULL，Unfiltered Rows 就會等於 Rows。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-161">If Filter Expression is NULL, Unfiltered Rows is equal to Rows.</span></span>  
  
     <span data-ttu-id="9e4ed-162">下列資訊描述結果集針對密度向量所傳回的資料行。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-162">The following information describes the columns returned in the result set for the Density Vector.</span></span>  
  
     <span data-ttu-id="9e4ed-163">**所有密度**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-163">**All Density**</span></span>  
     <span data-ttu-id="9e4ed-164">密度是 1 / 相異值。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-164">Density is 1 / *distinct values*.</span></span> <span data-ttu-id="9e4ed-165">結果會針對統計資料物件中資料行的每個前置詞來顯示密度，一個密度一個資料列。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-165">Results display density for each prefix of columns in the statistics object, one row per density.</span></span> <span data-ttu-id="9e4ed-166">相異值是每個資料列和每個資料行前置詞的資料行值相異清單。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-166">A distinct value is a distinct list of the column values per row and per columns prefix.</span></span> <span data-ttu-id="9e4ed-167">例如，如果統計資料物件包含索引鍵資料行 (A, B, C)，結果就會報告每一個資料行前置詞中相異值清單的密度：(A)、(A,B) 和 (A, B, C)。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-167">For example, if the statistics object contains key columns (A, B, C), the results report the density of the distinct lists of values in each of these column prefixes: (A), (A,B), and (A, B, C).</span></span> <span data-ttu-id="9e4ed-168">使用前置詞 (A, B, C) 時，這些清單的每一個都會是相異值清單：(3, 5, 6)、(4, 4, 6)、(4, 5, 6)、(4, 5, 7)。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-168">Using the prefix (A, B, C), each of these lists is a distinct value list: (3, 5, 6), (4, 4, 6), (4, 5, 6), (4, 5, 7).</span></span> <span data-ttu-id="9e4ed-169">使用前置詞 (A, B) 時，相同的資料行值都會有這些相異值清單：(3, 5)、(4, 4) 和 (4, 5)。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-169">Using the prefix (A, B) the same column values have these distinct value lists: (3, 5), (4, 4), and (4, 5).</span></span>  
  
     <span data-ttu-id="9e4ed-170">**平均長度**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-170">**Average Length**</span></span>  
     <span data-ttu-id="9e4ed-171">平均長度 (以位元組為單位)，用來儲存資料行前置詞的資料行值清單。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-171">Average length, in bytes, to store a list of the column values for the column prefix.</span></span> <span data-ttu-id="9e4ed-172">例如，如果清單 (3, 5, 6) 中的每一個值都需要 4 位元組，長度就是 12 位元組。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-172">For example, if the values in the list (3, 5, 6) each require 4 bytes the length is 12 bytes.</span></span>  
  
     <span data-ttu-id="9e4ed-173">**資料行**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-173">**Columns**</span></span>  
     <span data-ttu-id="9e4ed-174">在前置詞中顯示 All density 和 Average length 的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-174">Names of columns in the prefix for which All density and Average length are displayed.</span></span>  
  
     <span data-ttu-id="9e4ed-175">下列資訊描述結果集針對長條圖所傳回的資料行。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-175">The following information describes the columns returned in the result set for the Histogram.</span></span>  
  
     <span data-ttu-id="9e4ed-176">**RANGE_HI_KEY**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-176">**RANGE_HI_KEY**</span></span>  
     <span data-ttu-id="9e4ed-177">長條圖步驟的上限資料行值。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-177">Upper bound column value for a histogram step.</span></span> <span data-ttu-id="9e4ed-178">此資料行值也稱為索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-178">The column value is also called a key value.</span></span>  
  
     <span data-ttu-id="9e4ed-179">**RANGE_ROWS**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-179">**RANGE_ROWS**</span></span>  
     <span data-ttu-id="9e4ed-180">資料行值在長條圖步驟內的預估資料列數，不包括上限。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-180">Estimated number of rows whose column value falls within a histogram step, excluding the upper bound.</span></span>  
  
     <span data-ttu-id="9e4ed-181">**EQ_ROWS**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-181">**EQ_ROWS**</span></span>  
     <span data-ttu-id="9e4ed-182">資料行值等於長條圖步驟之上限的預估資料列數。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-182">Estimated number of rows whose column value equals the upper bound of the histogram step.</span></span>  
  
     <span data-ttu-id="9e4ed-183">**DISTINCT_RANGE_ROWS**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-183">**DISTINCT_RANGE_ROWS**</span></span>  
     <span data-ttu-id="9e4ed-184">在長條圖步驟內具有相異資料行值的預估資料列數，不包括上限。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-184">Estimated number of rows with a distinct column value within a histogram step, excluding the upper bound.</span></span>  
  
     <span data-ttu-id="9e4ed-185">**AVG_RANGE_ROWS**</span><span class="sxs-lookup"><span data-stu-id="9e4ed-185">**AVG_RANGE_ROWS**</span></span>  
     <span data-ttu-id="9e4ed-186">在長條圖步驟內具有重複資料行值的平均資料列數，上限不包括在內 (RANGE_ROWS / DISTINCT_RANGE_ROWS for DISTINCT_RANGE_ROWS > 0)。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-186">Average number of rows with duplicate column values within a histogram step, excluding the upper bound (RANGE_ROWS / DISTINCT_RANGE_ROWS for DISTINCT_RANGE_ROWS > 0).</span></span>  
  
7.  <span data-ttu-id="9e4ed-187">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-187">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9e4ed-188">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9e4ed-188">Using Transact-SQL</span></span>  
  
#### <a name="to-view-statistics-properties"></a><span data-ttu-id="9e4ed-189">若要檢視統計資料屬性</span><span class="sxs-lookup"><span data-stu-id="9e4ed-189">To view statistics properties</span></span>  
  
1.  <span data-ttu-id="9e4ed-190">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-190">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9e4ed-191">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-191">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9e4ed-192">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-192">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- The following example displays all statistics information for the AK_Address_rowguid index of the Person.Address table.   
    DBCC SHOW_STATISTICS ("Person.Address", AK_Address_rowguid);   
    GO  
    ```  
  
 <span data-ttu-id="9e4ed-193">如需詳細資訊，請參閱 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-193">For more information, see [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql).</span></span>  
  
#### <a name="to-find-all-of-the-statistics-on-a-table-or-view"></a><span data-ttu-id="9e4ed-194">若要尋找資料表或檢視表的所有統計資料</span><span class="sxs-lookup"><span data-stu-id="9e4ed-194">To find all of the statistics on a table or view</span></span>  
  
1.  <span data-ttu-id="9e4ed-195">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-195">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9e4ed-196">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-196">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9e4ed-197">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-197">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    /*Gets the following information: name and ID of the statistics, whether the statistics were created automatically or by the user, whether the statistics were created with the NORECOMPUTE option, and whether the statistics have a filter and, if so, what that filter is.  
    */  
    SELECT name AS statistics_name  
        ,stats_id  
        ,auto_created  
        ,user_created  
        ,no_recompute  
        ,has_filter  
        ,filter_definition  
    -- using the sys.stats catalog view  
    FROM sys.stats  
    -- for the Sales.SpecialOffer table  
    WHERE object_id = OBJECT_ID('Sales.SpecialOffer');  
    GO  
    ```  
  
 <span data-ttu-id="9e4ed-198">如需詳細資訊，請參閱 [sys.stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-stats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9e4ed-198">For more information, see [sys.stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-stats-transact-sql).</span></span>  
  
  
