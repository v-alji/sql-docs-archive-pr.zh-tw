---
title: 取得檢視的資訊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.viewproperties.general.f1
helpviewer_keywords:
- views [SQL Server], status information
- metadata [SQL Server], views
- dependencies [SQL Server], views
- displaying view information
- views [SQL Server], metadata
- viewing view information
- status information [SQL Server], views
- view dependencies
ms.assetid: 05a73e33-8f85-4fb6-80c1-1b659e753403
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4277aad4c1de0140606575c7ba437408518b3c8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585209"
---
# <a name="get-information-about-a-view"></a><span data-ttu-id="01ba4-102">取得檢視的資訊</span><span class="sxs-lookup"><span data-stu-id="01ba4-102">Get Information About a View</span></span>
  <span data-ttu-id="01ba4-103">您可以透過使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]，取得 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中檢視定義或屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="01ba4-103">You can gain information about a view's definition or properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="01ba4-104">您可能需要查看檢視的定義才能了解如何從來源資料表衍生出資料；或是查看檢視所定義的資料。</span><span class="sxs-lookup"><span data-stu-id="01ba4-104">You may need to see the definition of the view to understand how its data is derived from the source tables or to see the data defined by the view.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="01ba4-105">如果變更檢視所參考的物件名稱，就必須修改檢視，使其文字反映新的名稱。</span><span class="sxs-lookup"><span data-stu-id="01ba4-105">If you change the name of an object referenced by a view, you must modify the view so that its text reflects the new name.</span></span> <span data-ttu-id="01ba4-106">因此，在重新命名物件前，應先顯示物件的相依性，以判斷是否有任何檢視會受預期的變更所影響。</span><span class="sxs-lookup"><span data-stu-id="01ba4-106">Therefore, before renaming an object, display the dependencies of the object first to determine if any views are affected by the proposed change.</span></span>  
  
 <span data-ttu-id="01ba4-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="01ba4-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="01ba4-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="01ba4-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="01ba4-109">安全性</span><span class="sxs-lookup"><span data-stu-id="01ba4-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="01ba4-110">**使用下列方法取得檢視的相關資訊：**</span><span class="sxs-lookup"><span data-stu-id="01ba4-110">**To get information about a view, using:**</span></span>  
  
     [<span data-ttu-id="01ba4-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="01ba4-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="01ba4-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="01ba4-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="01ba4-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="01ba4-113">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="01ba4-114">Security</span><span class="sxs-lookup"><span data-stu-id="01ba4-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="01ba4-115">權限</span><span class="sxs-lookup"><span data-stu-id="01ba4-115">Permissions</span></span>  
 <span data-ttu-id="01ba4-116">使用 `sp_helptext` 傳回檢視的定義，需要 **Public** 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="01ba4-116">Using `sp_helptext` to return the definition of a view requires membership in the **public** role.</span></span> <span data-ttu-id="01ba4-117">使用 `sys.sql_expression_dependencies` 尋找檢視的所有相依性，需要資料庫的 VIEW DEFINITION 權限和資料庫之 `sys.sql_expression_dependencies` 的 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="01ba4-117">Using `sys.sql_expression_dependencies` to find all the dependencies on a view requires VIEW DEFINITION permission on the database and SELECT permission on `sys.sql_expression_dependencies` for the database.</span></span> <span data-ttu-id="01ba4-118">系統物件定義是公開可見的，就像 SELECT OBJECT_DEFINITION 中傳回的定義一樣。</span><span class="sxs-lookup"><span data-stu-id="01ba4-118">System object definitions, like the ones returned in SELECT OBJECT_DEFINITION, are publicly visible.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="01ba4-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="01ba4-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="get-view-properties-by-using-object-explorer"></a><span data-ttu-id="01ba4-120">透過使用物件總管取得檢視屬性</span><span class="sxs-lookup"><span data-stu-id="01ba4-120">Get view properties by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="01ba4-121">在 **[物件總管]** 中，按一下資料庫旁邊的加號，此資料庫包含您要查看其屬性的檢視，然後按一下加號展開 **[檢視]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="01ba4-121">In **Object Explorer**, click the plus sign next to the database that contains the view to which you want to view the properties, and then click the plus sign to expand the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="01ba4-122">以滑鼠右鍵按一下要查看其屬性的檢視，然後選取 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="01ba4-122">Right-click the view of which you want to view the properties and select **Properties**.</span></span>  
  
     <span data-ttu-id="01ba4-123">下列屬性會在 **[檢視屬性]** 對話方塊中顯示。</span><span class="sxs-lookup"><span data-stu-id="01ba4-123">The following properties show in the **View Properties** dialog box.</span></span>  
  
     <span data-ttu-id="01ba4-124">**Database**</span><span class="sxs-lookup"><span data-stu-id="01ba4-124">**Database**</span></span>  
     <span data-ttu-id="01ba4-125">包含此檢視之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="01ba4-125">The name of the database containing this view.</span></span>  
  
     <span data-ttu-id="01ba4-126">**Server**</span><span class="sxs-lookup"><span data-stu-id="01ba4-126">**Server**</span></span>  
     <span data-ttu-id="01ba4-127">目前伺服器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="01ba4-127">The name of the current server instance.</span></span>  
  
     <span data-ttu-id="01ba4-128">**使用者**</span><span class="sxs-lookup"><span data-stu-id="01ba4-128">**User**</span></span>  
     <span data-ttu-id="01ba4-129">這個連接之使用者的名稱。</span><span class="sxs-lookup"><span data-stu-id="01ba4-129">The name of the user of this connection.</span></span>  
  
     <span data-ttu-id="01ba4-130">**建立日期**</span><span class="sxs-lookup"><span data-stu-id="01ba4-130">**Created date**</span></span>  
     <span data-ttu-id="01ba4-131">顯示建立檢視的日期。</span><span class="sxs-lookup"><span data-stu-id="01ba4-131">Displays the date the view was created.</span></span>  
  
     <span data-ttu-id="01ba4-132">**名稱**</span><span class="sxs-lookup"><span data-stu-id="01ba4-132">**Name**</span></span>  
     <span data-ttu-id="01ba4-133">目前檢視的名稱。</span><span class="sxs-lookup"><span data-stu-id="01ba4-133">The name of the current view.</span></span>  
  
     <span data-ttu-id="01ba4-134">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="01ba4-134">**Schema**</span></span>  
     <span data-ttu-id="01ba4-135">顯示擁有檢視的結構描述。</span><span class="sxs-lookup"><span data-stu-id="01ba4-135">Displays the schema that owns the view.</span></span>  
  
     <span data-ttu-id="01ba4-136">**系統物件**</span><span class="sxs-lookup"><span data-stu-id="01ba4-136">**System object**</span></span>  
     <span data-ttu-id="01ba4-137">指出檢視是否為系統物件。</span><span class="sxs-lookup"><span data-stu-id="01ba4-137">Indicates whether the view is a system object.</span></span> <span data-ttu-id="01ba4-138">值為 True 與 False。</span><span class="sxs-lookup"><span data-stu-id="01ba4-138">Values are True and False.</span></span>  
  
     <span data-ttu-id="01ba4-139">**ANSI NULLS**</span><span class="sxs-lookup"><span data-stu-id="01ba4-139">**ANSI NULLs**</span></span>  
     <span data-ttu-id="01ba4-140">指出物件是否使用 ANSI NULLS 選項建立。</span><span class="sxs-lookup"><span data-stu-id="01ba4-140">Indicates if the object was created with the ANSI NULLs option.</span></span>  
  
     <span data-ttu-id="01ba4-141">**已加密**</span><span class="sxs-lookup"><span data-stu-id="01ba4-141">**Encrypted**</span></span>  
     <span data-ttu-id="01ba4-142">指出檢視表是否已加密。</span><span class="sxs-lookup"><span data-stu-id="01ba4-142">Indicates whether the view is encrypted.</span></span> <span data-ttu-id="01ba4-143">值為 True 與 False。</span><span class="sxs-lookup"><span data-stu-id="01ba4-143">Values are True and False.</span></span>  
  
     <span data-ttu-id="01ba4-144">**引號識別碼**</span><span class="sxs-lookup"><span data-stu-id="01ba4-144">**Quoted identifier**</span></span>  
     <span data-ttu-id="01ba4-145">指出物件是否使用引號識別碼選項建立。</span><span class="sxs-lookup"><span data-stu-id="01ba4-145">Indicates if the object was created with the quoted identifier option.</span></span>  
  
     <span data-ttu-id="01ba4-146">**結構描述繫結**</span><span class="sxs-lookup"><span data-stu-id="01ba4-146">**Schema bound**</span></span>  
     <span data-ttu-id="01ba4-147">指出檢視是否以結構描述繫結。</span><span class="sxs-lookup"><span data-stu-id="01ba4-147">Indicates whether the view is schema-bound.</span></span> <span data-ttu-id="01ba4-148">值為 True 與 False。</span><span class="sxs-lookup"><span data-stu-id="01ba4-148">Values are True and False.</span></span> <span data-ttu-id="01ba4-149">如需結構描述繫結檢視的相關資訊，請參閱 [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) 的 SCHEMABINDING 部分。</span><span class="sxs-lookup"><span data-stu-id="01ba4-149">For information about schema-bound views, see the SCHEMABINDING portion of [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span></span>  
  
#### <a name="getting-view-properties-by-using-the-view-designer-tool"></a><span data-ttu-id="01ba4-150">透過使用檢視設計工具取得檢視屬性</span><span class="sxs-lookup"><span data-stu-id="01ba4-150">Getting view properties by using the View Designer tool</span></span>  
  
1.  <span data-ttu-id="01ba4-151">在 **[物件總管]** 中，展開資料庫，此資料庫包含您要查看其屬性的檢視，然後展開 **[檢視]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="01ba4-151">In **Object Explorer**, expand the database that contains the view to which you want to view the properties, and then expand the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="01ba4-152">以滑鼠右鍵按一下要查看其屬性的檢視，然後選取 **[設計]** 。</span><span class="sxs-lookup"><span data-stu-id="01ba4-152">Right-click the view of which you want to view the properties and select **Design**.</span></span>  
  
3.  <span data-ttu-id="01ba4-153">在 [圖表] 窗格的空白處按一下滑鼠右鍵，再按 [ **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="01ba4-153">Right-click in the blank space of the Diagram pane and click **Properties**.</span></span>  
  
     <span data-ttu-id="01ba4-154">下列屬性會在 **[屬性]** 窗格中顯示。</span><span class="sxs-lookup"><span data-stu-id="01ba4-154">The following properties show in the **Properties** pane.</span></span>  
  
     <span data-ttu-id="01ba4-155">**(名稱)**</span><span class="sxs-lookup"><span data-stu-id="01ba4-155">**(Name)**</span></span>  
     <span data-ttu-id="01ba4-156">目前檢視的名稱。</span><span class="sxs-lookup"><span data-stu-id="01ba4-156">The name of the current view.</span></span>  
  
     <span data-ttu-id="01ba4-157">**Database Name**</span><span class="sxs-lookup"><span data-stu-id="01ba4-157">**Database Name**</span></span>  
     <span data-ttu-id="01ba4-158">包含此檢視之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="01ba4-158">The name of the database containing this view.</span></span>  
  
     <span data-ttu-id="01ba4-159">**說明**</span><span class="sxs-lookup"><span data-stu-id="01ba4-159">**Description**</span></span>  
     <span data-ttu-id="01ba4-160">目前檢視的簡要描述。</span><span class="sxs-lookup"><span data-stu-id="01ba4-160">A brief description of the current view.</span></span>  
  
     <span data-ttu-id="01ba4-161">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="01ba4-161">**Schema**</span></span>  
     <span data-ttu-id="01ba4-162">顯示擁有檢視的結構描述。</span><span class="sxs-lookup"><span data-stu-id="01ba4-162">Displays the schema that owns the view.</span></span>  
  
     <span data-ttu-id="01ba4-163">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="01ba4-163">**Server Name**</span></span>  
     <span data-ttu-id="01ba4-164">目前伺服器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="01ba4-164">The name of the current server instance.</span></span>  
  
     <span data-ttu-id="01ba4-165">**繫結至結構描述**</span><span class="sxs-lookup"><span data-stu-id="01ba4-165">**Bind to Schema**</span></span>  
     <span data-ttu-id="01ba4-166">防止使用者以任何可能會導致檢視定義失效的方式修改促成此檢視的基礎物件。</span><span class="sxs-lookup"><span data-stu-id="01ba4-166">Prevents users from modifying the underlying objects that contribute to this view in any way that would invalidate the view definition.</span></span>  
  
     <span data-ttu-id="01ba4-167">**具決定性**</span><span class="sxs-lookup"><span data-stu-id="01ba4-167">**Deterministic**</span></span>  
     <span data-ttu-id="01ba4-168">顯示是否可以確定地決定選取之資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="01ba4-168">Shows whether the data type of the selected column can be determined with certainty</span></span>  
  
     <span data-ttu-id="01ba4-169">**重複資料僅顯示一筆**</span><span class="sxs-lookup"><span data-stu-id="01ba4-169">**Distinct Values**</span></span>  
     <span data-ttu-id="01ba4-170">指定查詢會篩選檢視中重複的資料。</span><span class="sxs-lookup"><span data-stu-id="01ba4-170">Specifies that the query will filter out duplicates in the view.</span></span> <span data-ttu-id="01ba4-171">如果只使用資料表中的一部分資料行，而這些資料行包含了重複的值；或者聯結兩個以上資料表的處理序，會在結果集中產生重複的資料列時，這個選項非常實用。</span><span class="sxs-lookup"><span data-stu-id="01ba4-171">This option is useful when you are using only some of the columns from a table and those columns might contain duplicate values, or when the process of joining two or more tables produces duplicate rows in the result set.</span></span> <span data-ttu-id="01ba4-172">選擇此選項相當於在 [SQL] 窗格中的陳述式裡插入 DISTINCT 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="01ba4-172">Choosing this option is equivalent to inserting the keyword DISTINCT into the statement in the SQL pane.</span></span>  
  
     <span data-ttu-id="01ba4-173">**GROUP BY 擴充選項**</span><span class="sxs-lookup"><span data-stu-id="01ba4-173">**GROUP BY Extension**</span></span>  
     <span data-ttu-id="01ba4-174">指定彙總查詢為基礎的檢視有其他可用的選項。</span><span class="sxs-lookup"><span data-stu-id="01ba4-174">Specifies that additional options for views based on aggregate queries are available.</span></span>  
  
     <span data-ttu-id="01ba4-175">**輸出全部資料行**</span><span class="sxs-lookup"><span data-stu-id="01ba4-175">**Output All Columns**</span></span>  
     <span data-ttu-id="01ba4-176">顯示選定的檢視是否傳回所有資料行。</span><span class="sxs-lookup"><span data-stu-id="01ba4-176">Shows whether all columns are returned by the selected view.</span></span> <span data-ttu-id="01ba4-177">這是在建立檢視時設定的。</span><span class="sxs-lookup"><span data-stu-id="01ba4-177">This is set at the time the view is created.</span></span>  
  
     <span data-ttu-id="01ba4-178">**SQL 註解**</span><span class="sxs-lookup"><span data-stu-id="01ba4-178">**SQL Comment**</span></span>  
     <span data-ttu-id="01ba4-179">顯示 SQL 陳述式的描述。</span><span class="sxs-lookup"><span data-stu-id="01ba4-179">Shows a description of the SQL statements.</span></span> <span data-ttu-id="01ba4-180">若要查看或編輯整個描述，請按一下 [描述]，然後按一下屬性右側的省略符號 **(...)** 。</span><span class="sxs-lookup"><span data-stu-id="01ba4-180">To see the entire description, or to edit it, click the description and then click the ellipses **(...)** to the right of the property.</span></span> <span data-ttu-id="01ba4-181">您的註解中可能包含使用檢視的人及使用時間等這類資訊。</span><span class="sxs-lookup"><span data-stu-id="01ba4-181">Your comments might include information such as who uses the view and when they use it.</span></span>  
  
     <span data-ttu-id="01ba4-182">**Top 規格**</span><span class="sxs-lookup"><span data-stu-id="01ba4-182">**Top Specification**</span></span>  
     <span data-ttu-id="01ba4-183">展開以顯示 **[Top]** 、 **[運算式]** 、 **[百分比]** 屬性，以及 **[WITH TIES]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="01ba4-183">Expands to show properties for the **Top**, **Expression**, **Percent**, and **With Ties** properties.</span></span>  
  
     <span data-ttu-id="01ba4-184">**(Top)**</span><span class="sxs-lookup"><span data-stu-id="01ba4-184">**(Top)**</span></span>  
     <span data-ttu-id="01ba4-185">指定檢視將包含 TOP 子句，而這個子句只會傳回結果集內的前 n 個資料列，或前百分之 n 的資料列。</span><span class="sxs-lookup"><span data-stu-id="01ba4-185">Specifies that the view will include a TOP clause, which returns only the first n rows or first n percentage of rows in the result set.</span></span> <span data-ttu-id="01ba4-186">預設值是檢視會傳回結果集裡前 10 個資料列。</span><span class="sxs-lookup"><span data-stu-id="01ba4-186">The default is that the view returns the first 10 rows in the result set.</span></span> <span data-ttu-id="01ba4-187">使用此選項變更傳回的資料列數目，或指定不同的百分比。</span><span class="sxs-lookup"><span data-stu-id="01ba4-187">Use this to change the number of rows to return or to specify a different percentage</span></span>  
  
     <span data-ttu-id="01ba4-188">**運算式**</span><span class="sxs-lookup"><span data-stu-id="01ba4-188">**Expression**</span></span>  
     <span data-ttu-id="01ba4-189">顯示檢視會傳回多少百分比 (如果 **[百分比]** 設定為 **[是]** ) 或何種記錄 (如果 **[百分比]** 設定為 **[否]** )。</span><span class="sxs-lookup"><span data-stu-id="01ba4-189">Shows what percent (if **Percent** is set to **Yes**) or records (if **Percent** is set to **No**) that the view will return.</span></span>  
  
     <span data-ttu-id="01ba4-190">**Percent**</span><span class="sxs-lookup"><span data-stu-id="01ba4-190">**Percent**</span></span>  
     <span data-ttu-id="01ba4-191">指定查詢將包含 **TOP** 子句，只會傳回結果集內的前百分之 n 的資料列。</span><span class="sxs-lookup"><span data-stu-id="01ba4-191">Specifies that the query will include a **TOP** clause, returning only the first n percentage of rows in the result set</span></span>  
  
     <span data-ttu-id="01ba4-192">**With Ties**</span><span class="sxs-lookup"><span data-stu-id="01ba4-192">**With Ties**</span></span>  
     <span data-ttu-id="01ba4-193">指定檢視中會包含 **WITH TIES** 子句。</span><span class="sxs-lookup"><span data-stu-id="01ba4-193">Specifies that the view will include a **WITH TIES** clause.</span></span> <span data-ttu-id="01ba4-194">如果檢視中包含了**WITH TIES** 子句和以百分比為基礎的 **WITH TIES** 子句， **WITH TIES** 非常實用。</span><span class="sxs-lookup"><span data-stu-id="01ba4-194">**WITH TIES** is useful if a view includes an **ORDER BY** clause and a **TOP** clause based on percentage.</span></span> <span data-ttu-id="01ba4-195">如果設定了此選項，而且百分比截止點落在 **ORDER BY** 子句裡一組相同值的資料列中間，將會擴充檢視以將這些資料列全部包含。</span><span class="sxs-lookup"><span data-stu-id="01ba4-195">If this option is set, and if the percentage cutoff falls in the middle of a set of rows with identical values in the **ORDER BY** clause, the view is extended to include all such rows.</span></span>  
  
     <span data-ttu-id="01ba4-196">**更新規格**</span><span class="sxs-lookup"><span data-stu-id="01ba4-196">**Update Specification**</span></span>  
     <span data-ttu-id="01ba4-197">展開以顯示 **[使用檢視規則更新]** 屬性和 **[檢查選項]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="01ba4-197">Expands to show properties for the **Update Using View Rules** and **Check Option** properties.</span></span>  
  
     <span data-ttu-id="01ba4-198">**(使用檢視規則更新)**</span><span class="sxs-lookup"><span data-stu-id="01ba4-198">**(Update Using View Rules)**</span></span>  
     <span data-ttu-id="01ba4-199">指示檢視的所有更新和插入都會由 Microsoft Data Access Components (MDAC) 轉譯為參考檢視的 SQL 陳述式，而不是轉譯為直接參考檢視之基底資料表的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="01ba4-199">Indicates that all updates and insertions to the view will be translated by Microsoft Data Access Components (MDAC) into SQL statements that refer to the view, rather than into SQL statements that refer directly to the view's base tables.</span></span>  
  
     <span data-ttu-id="01ba4-200">在某些情況下，MDAC 會表示檢視更新和檢視插入作業是針對檢視之基礎基底資料表的更新和插入。</span><span class="sxs-lookup"><span data-stu-id="01ba4-200">In some cases, MDAC manifests view update and view insert operations as updates and inserts against the view's underlying base tables.</span></span> <span data-ttu-id="01ba4-201">透過選取 **[使用檢視規則更新]** ，可以確保 MDAC 會針對檢視本身產生更新和插入作業。</span><span class="sxs-lookup"><span data-stu-id="01ba4-201">By selecting **Update Using View Rules**, you can ensure that MDAC generates update and insert operations against the view itself.</span></span>  
  
     <span data-ttu-id="01ba4-202">**檢查選項**</span><span class="sxs-lookup"><span data-stu-id="01ba4-202">**Check Option**</span></span>  
     <span data-ttu-id="01ba4-203">指示當您開啟此檢視並修改 **[結果]** 窗格時，資料來源會檢查加入或修改的資料是否滿足檢視定義的 **WHERE** 子句。</span><span class="sxs-lookup"><span data-stu-id="01ba4-203">Indicates that when you open this view and modify the **Results** pane, the data source checks whether the added or modified data satisfies the **WHERE** clause of the view definition.</span></span> <span data-ttu-id="01ba4-204">如果您的修改無法滿足 **WHERE** 子句，您將看到錯誤附帶詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="01ba4-204">If your modification do not satisfy the **WHERE** clause, you will see an error with more information.</span></span>  
  
#### <a name="to-get-dependencies-on-the-view"></a><span data-ttu-id="01ba4-205">取得檢視的相依性</span><span class="sxs-lookup"><span data-stu-id="01ba4-205">To get dependencies on the view</span></span>  
  
1.  <span data-ttu-id="01ba4-206">在 **[物件總管]** 中，展開資料庫，此資料庫包含您要查看其屬性的檢視，然後展開 **[檢視]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="01ba4-206">In **Object Explorer**, expand the database that contains the view to which you want to view the properties, and then expand the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="01ba4-207">以滑鼠右鍵按一下要查看其屬性的檢視，然後選取 **[檢視相依性]** 。</span><span class="sxs-lookup"><span data-stu-id="01ba4-207">Right-click the view of which you want to view the properties and select **View Dependencies**.</span></span>  
  
3.  <span data-ttu-id="01ba4-208">選取 **[相依於 [檢視名稱] 的物件]** ，以顯示參考檢視的物件。</span><span class="sxs-lookup"><span data-stu-id="01ba4-208">Select **Objects that depend on [view name]** to display the objects that refer to the view.</span></span>  
  
4.  <span data-ttu-id="01ba4-209">選取 **[[檢視表名稱] 所相依的物件]** ，以顯示檢視表所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="01ba4-209">Select **Objects on which [view name] depends** to display the objects that are referenced by the view.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="01ba4-210">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="01ba4-210">Using Transact-SQL</span></span>  
  
#### <a name="to-get-the-definition-and-properties-of-a-view"></a><span data-ttu-id="01ba4-211">取得檢視定義和屬性</span><span class="sxs-lookup"><span data-stu-id="01ba4-211">To get the definition and properties of a view</span></span>  
  
1.  <span data-ttu-id="01ba4-212">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="01ba4-212">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="01ba4-213">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="01ba4-213">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="01ba4-214">將下列其中一個範例複製並貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="01ba4-214">Copy and paste one of the following examples into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition, uses_ansi_nulls, uses_quoted_identifier, is_schema_bound  
    FROM sys.sql_modules  
    WHERE object_id = OBJECT_ID('HumanResources.vEmployee');   
    GO  
    ```  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID('HumanResources.vEmployee')) AS ObjectDefinition;   
    GO  
    ```  
  
    ```  
    EXEC sp_helptext 'HumanResources.vEmployee';  
    ```  
  
 <span data-ttu-id="01ba4-215">如需詳細資訊，請參閱 [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)、[OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql) 和 [sp_helptext &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="01ba4-215">For more information, see [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql), [OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql) and [sp_helptext &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql).</span></span>  
  
#### <a name="to-get-the-dependencies-of-a-view"></a><span data-ttu-id="01ba4-216">取得檢視的相依性</span><span class="sxs-lookup"><span data-stu-id="01ba4-216">To get the dependencies of a view</span></span>  
  
1.  <span data-ttu-id="01ba4-217">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="01ba4-217">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="01ba4-218">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="01ba4-218">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="01ba4-219">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="01ba4-219">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referencing_id = OBJECT_ID(N'Production.vProductAndDescription');  
    GO  
    ```  
  
 <span data-ttu-id="01ba4-220">如需詳細資訊，請參閱 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) 和 [sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="01ba4-220">For more information, see [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) and [sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql).</span></span>  
  
  
