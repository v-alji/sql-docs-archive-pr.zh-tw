---
title: 建立索引檢視表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexed views [SQL Server], creating
- clustered indexes, views
- CREATE INDEX statement
- large_value_types_out_of_row option
- indexed views [SQL Server]
- views [SQL Server], indexed views
ms.assetid: f86dd29f-52dd-44a9-91ac-1eb305c1ca8d
author: stevestein
ms.author: sstein
ms.openlocfilehash: d33ff37caca04f46edd6ad92d0686713829bb270
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585214"
---
# <a name="create-indexed-views"></a><span data-ttu-id="24fc7-102">建立索引檢視表</span><span class="sxs-lookup"><span data-stu-id="24fc7-102">Create Indexed Views</span></span>
  <span data-ttu-id="24fc7-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立索引檢視表。</span><span class="sxs-lookup"><span data-stu-id="24fc7-103">This topic describes how to create an indexed view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="24fc7-104">對檢視建立的第一個索引必須是唯一的叢集索引。</span><span class="sxs-lookup"><span data-stu-id="24fc7-104">The first index created on a view must be a unique clustered index.</span></span> <span data-ttu-id="24fc7-105">建好唯一的叢集索引後，才可以建立其他非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="24fc7-105">After the unique clustered index has been created, you can create more nonclustered indexes.</span></span> <span data-ttu-id="24fc7-106">為檢視表建立唯一的叢集索引，可以提升查詢效能，因為檢視表儲存在資料庫中的方式與包含叢集索引之資料表的儲存方式一樣。</span><span class="sxs-lookup"><span data-stu-id="24fc7-106">Creating a unique clustered index on a view improves query performance because the view is stored in the database in the same way a table with a clustered index is stored.</span></span> <span data-ttu-id="24fc7-107">查詢最佳化工具可以利用索引檢視表來加快查詢執行的速度。</span><span class="sxs-lookup"><span data-stu-id="24fc7-107">The query optimizer may use indexed views to speed up the query execution.</span></span> <span data-ttu-id="24fc7-108">不必在查詢中參考此檢視表，最佳化工具仍會考慮以該檢視表做為替代方式。</span><span class="sxs-lookup"><span data-stu-id="24fc7-108">The view does not have to be referenced in the query for the optimizer to consider that view for a substitution.</span></span>  
  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="24fc7-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="24fc7-109">Before You Begin</span></span>  
 <span data-ttu-id="24fc7-110">以下是建立索引檢視表所需要的步驟，這些步驟對於能否順利完成索引檢視表的實作是很重要的：</span><span class="sxs-lookup"><span data-stu-id="24fc7-110">The following steps are required to create an indexed view and are critical to the successful implementation of the indexed view:</span></span>  
  
1.  <span data-ttu-id="24fc7-111">確認檢視表中所要參考之所有現有資料表的 SET 選項是正確的。</span><span class="sxs-lookup"><span data-stu-id="24fc7-111">Verify the SET options are correct for all existing tables that will be referenced in the view.</span></span>  
  
2.  <span data-ttu-id="24fc7-112">先確認工作階段之 SET 選項的設定是正確的，再建立任何資料表和檢視表。</span><span class="sxs-lookup"><span data-stu-id="24fc7-112">Verify that the SET options for the session are set correctly before you create any tables and the view.</span></span>  
  
3.  <span data-ttu-id="24fc7-113">確認檢視表定義具決定性。</span><span class="sxs-lookup"><span data-stu-id="24fc7-113">Verify that the view definition is deterministic.</span></span>  
  
4.  <span data-ttu-id="24fc7-114">利用 WITH SCHEMABINDING 選項來建立檢視表。</span><span class="sxs-lookup"><span data-stu-id="24fc7-114">Create the view by using the WITH SCHEMABINDING option.</span></span>  
  
5.  <span data-ttu-id="24fc7-115">在檢視表上建立唯一的叢集索引。</span><span class="sxs-lookup"><span data-stu-id="24fc7-115">Create the unique clustered index on the view.</span></span>  
  
###  <a name="required-set-options-for-indexed-views"></a><a name="Restrictions"></a> <span data-ttu-id="24fc7-116">需要索引檢視表的 SET 選項</span><span class="sxs-lookup"><span data-stu-id="24fc7-116">Required SET Options for Indexed Views</span></span>  
 <span data-ttu-id="24fc7-117">如果在查詢執行時有不同的使用中 SET 選項，則評估相同的運算式可能會在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中產生不同的結果。</span><span class="sxs-lookup"><span data-stu-id="24fc7-117">Evaluating the same expression can produce different results in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] when different SET options are active when the query is executed.</span></span> <span data-ttu-id="24fc7-118">例如，將 SET 選項 CONCAT_NULL_YIELDS_NULL 設為 ON 之後，運算式 **'** abc **'** + NULL 會傳回 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="24fc7-118">For example, after the SET option CONCAT_NULL_YIELDS_NULL is set to ON, the expression **'** abc **'** + NULL returns the value NULL.</span></span> <span data-ttu-id="24fc7-119">不過，將 CONCAT_NULL_YIEDS_NULL 設為 OFF 之後，相同的運算式則會產生 **'** abc **'**。</span><span class="sxs-lookup"><span data-stu-id="24fc7-119">However, after CONCAT_NULL_YIEDS_NULL is set to OFF, the same expression produces **'** abc **'**.</span></span>  
  
 <span data-ttu-id="24fc7-120">若要確定檢視表可以正確地維護並傳回一致的結果，索引檢視表需要數個 SET 選項的固定值。</span><span class="sxs-lookup"><span data-stu-id="24fc7-120">To make sure that the views can be maintained correctly and return consistent results, indexed views require fixed values for several SET options.</span></span> <span data-ttu-id="24fc7-121">當下列情況發生時，您必須將下表中的 SET 選項設定為**RequiredValue**資料行中顯示的值：</span><span class="sxs-lookup"><span data-stu-id="24fc7-121">The SET options in the following table must be set to the values shown in the **RequiredValue** column whenever the following conditions occur:</span></span>  
  
-   <span data-ttu-id="24fc7-122">建立檢視表和檢視表的後續索引。</span><span class="sxs-lookup"><span data-stu-id="24fc7-122">The view and subsequent indexes on the view are created.</span></span>  
  
-   <span data-ttu-id="24fc7-123">建立資料表時檢視中所參考的基底資料表。</span><span class="sxs-lookup"><span data-stu-id="24fc7-123">The base tables referenced in the view at the time the table is created.</span></span>  
  
-   <span data-ttu-id="24fc7-124">有在任何參與索引檢視表的資料表上執行的任何插入、更新或刪除作業。</span><span class="sxs-lookup"><span data-stu-id="24fc7-124">There is any insert, update, or delete operation performed on any table that participates in the indexed view.</span></span> <span data-ttu-id="24fc7-125">這項需求包括大量複製、複寫及分散式查詢等作業。</span><span class="sxs-lookup"><span data-stu-id="24fc7-125">This requirement includes operations such as bulk copy, replication, and distributed queries.</span></span>  
  
-   <span data-ttu-id="24fc7-126">查詢最佳化工具會利用索引檢視表來產生查詢計劃。</span><span class="sxs-lookup"><span data-stu-id="24fc7-126">The indexed view is used by the query optimizer to produce the query plan.</span></span>  
  
    |<span data-ttu-id="24fc7-127">Set 選項</span><span class="sxs-lookup"><span data-stu-id="24fc7-127">SET options</span></span>|<span data-ttu-id="24fc7-128">必要值</span><span class="sxs-lookup"><span data-stu-id="24fc7-128">Required value</span></span>|<span data-ttu-id="24fc7-129">預設伺服器值</span><span class="sxs-lookup"><span data-stu-id="24fc7-129">Default server value</span></span>|<span data-ttu-id="24fc7-130">預設</span><span class="sxs-lookup"><span data-stu-id="24fc7-130">Default</span></span><br /><br /> <span data-ttu-id="24fc7-131">OLE DB 與 ODBC 值</span><span class="sxs-lookup"><span data-stu-id="24fc7-131">OLE DB and ODBC value</span></span>|<span data-ttu-id="24fc7-132">預設</span><span class="sxs-lookup"><span data-stu-id="24fc7-132">Default</span></span><br /><br /> <span data-ttu-id="24fc7-133">DB-Library 值</span><span class="sxs-lookup"><span data-stu-id="24fc7-133">DB-Library value</span></span>|  
    |-----------------|--------------------|--------------------------|---------------------------------------|-----------------------------------|  
    |<span data-ttu-id="24fc7-134">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="24fc7-134">ANSI_NULLS</span></span>|<span data-ttu-id="24fc7-135">開啟</span><span class="sxs-lookup"><span data-stu-id="24fc7-135">ON</span></span>|<span data-ttu-id="24fc7-136">開啟</span><span class="sxs-lookup"><span data-stu-id="24fc7-136">ON</span></span>|<span data-ttu-id="24fc7-137">開啟</span><span class="sxs-lookup"><span data-stu-id="24fc7-137">ON</span></span>|<span data-ttu-id="24fc7-138">OFF</span><span class="sxs-lookup"><span data-stu-id="24fc7-138">OFF</span></span>|  
    |<span data-ttu-id="24fc7-139">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="24fc7-139">ANSI_PADDING</span></span>|<span data-ttu-id="24fc7-140">開啟</span><span class="sxs-lookup"><span data-stu-id="24fc7-140">ON</span></span>|<span data-ttu-id="24fc7-141">開啟</span><span class="sxs-lookup"><span data-stu-id="24fc7-141">ON</span></span>|<span data-ttu-id="24fc7-142">開啟</span><span class="sxs-lookup"><span data-stu-id="24fc7-142">ON</span></span>|<span data-ttu-id="24fc7-143">OFF</span><span class="sxs-lookup"><span data-stu-id="24fc7-143">OFF</span></span>|  
    |<span data-ttu-id="24fc7-144">ANSI_WARNINGS\*</span><span class="sxs-lookup"><span data-stu-id="24fc7-144">ANSI_WARNINGS\*</span></span>|<span data-ttu-id="24fc7-145">開啟</span><span class="sxs-lookup"><span data-stu-id="24fc7-145">ON</span></span>|<span data-ttu-id="24fc7-146">開啟</span><span class="sxs-lookup"><span data-stu-id="24fc7-146">ON</span></span>|<span data-ttu-id="24fc7-147">開啟</span><span class="sxs-lookup"><span data-stu-id="24fc7-147">ON</span></span>|<span data-ttu-id="24fc7-148">OFF</span><span class="sxs-lookup"><span data-stu-id="24fc7-148">OFF</span></span>|  
    |<span data-ttu-id="24fc7-149">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="24fc7-149">ARITHABORT</span></span>|<span data-ttu-id="24fc7-150">開啟</span><span class="sxs-lookup"><span data-stu-id="24fc7-150">ON</span></span>|<span data-ttu-id="24fc7-151">開啟</span><span class="sxs-lookup"><span data-stu-id="24fc7-151">ON</span></span>|<span data-ttu-id="24fc7-152">OFF</span><span class="sxs-lookup"><span data-stu-id="24fc7-152">OFF</span></span>|<span data-ttu-id="24fc7-153">OFF</span><span class="sxs-lookup"><span data-stu-id="24fc7-153">OFF</span></span>|  
    |<span data-ttu-id="24fc7-154">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="24fc7-154">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="24fc7-155">開啟</span><span class="sxs-lookup"><span data-stu-id="24fc7-155">ON</span></span>|<span data-ttu-id="24fc7-156">開啟</span><span class="sxs-lookup"><span data-stu-id="24fc7-156">ON</span></span>|<span data-ttu-id="24fc7-157">開啟</span><span class="sxs-lookup"><span data-stu-id="24fc7-157">ON</span></span>|<span data-ttu-id="24fc7-158">OFF</span><span class="sxs-lookup"><span data-stu-id="24fc7-158">OFF</span></span>|  
    |<span data-ttu-id="24fc7-159">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="24fc7-159">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="24fc7-160">OFF</span><span class="sxs-lookup"><span data-stu-id="24fc7-160">OFF</span></span>|<span data-ttu-id="24fc7-161">OFF</span><span class="sxs-lookup"><span data-stu-id="24fc7-161">OFF</span></span>|<span data-ttu-id="24fc7-162">OFF</span><span class="sxs-lookup"><span data-stu-id="24fc7-162">OFF</span></span>|<span data-ttu-id="24fc7-163">OFF</span><span class="sxs-lookup"><span data-stu-id="24fc7-163">OFF</span></span>|  
    |<span data-ttu-id="24fc7-164">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="24fc7-164">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="24fc7-165">開啟</span><span class="sxs-lookup"><span data-stu-id="24fc7-165">ON</span></span>|<span data-ttu-id="24fc7-166">開啟</span><span class="sxs-lookup"><span data-stu-id="24fc7-166">ON</span></span>|<span data-ttu-id="24fc7-167">開啟</span><span class="sxs-lookup"><span data-stu-id="24fc7-167">ON</span></span>|<span data-ttu-id="24fc7-168">OFF</span><span class="sxs-lookup"><span data-stu-id="24fc7-168">OFF</span></span>|  
  
     <span data-ttu-id="24fc7-169">\*將 ANSI_WARNINGS 設為 ON 會將 ARITHABORT 隱含地設為 ON。</span><span class="sxs-lookup"><span data-stu-id="24fc7-169">\*Setting ANSI_WARNINGS to ON implicitly sets ARITHABORT to ON.</span></span>  
  
 <span data-ttu-id="24fc7-170">如果您要使用 OLE DB 或 ODBC 伺服器連接，唯一必須修改的值是 ARITHABORT 設定。</span><span class="sxs-lookup"><span data-stu-id="24fc7-170">If you are using an OLE DB or ODBC server connection, the only value that must be modified is the ARITHABORT setting.</span></span> <span data-ttu-id="24fc7-171">必須在伺服器層級利用 **sp_configure** 來正確地設定所有 DB-Library 值，或者，必須從應用程式利用 SET 命令來正確地設定所有 DB-Library 值。</span><span class="sxs-lookup"><span data-stu-id="24fc7-171">All DB-Library values must be set correctly either at the server level by using **sp_configure** or from the application by using the SET command.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="24fc7-172">強烈建議您在伺服器之任何資料庫的計算資料行上建立第一個索引檢視表或索引之後，立即在伺服器範圍將 ARITHABORT 使用者選項設為 ON。</span><span class="sxs-lookup"><span data-stu-id="24fc7-172">We strongly recommend that you set the ARITHABORT user option to ON server-wide as soon as the first indexed view or index on a computed column is created in any database on the server.</span></span>  
  
### <a name="deterministic-views"></a><span data-ttu-id="24fc7-173">具決定性的檢視</span><span class="sxs-lookup"><span data-stu-id="24fc7-173">Deterministic Views</span></span>  
 <span data-ttu-id="24fc7-174">索引檢視表的定義必須具決定性。</span><span class="sxs-lookup"><span data-stu-id="24fc7-174">The definition of an indexed view must be deterministic.</span></span> <span data-ttu-id="24fc7-175">如果選取清單及 WHERE 和 GROUP BY 子句中的所有運算式都具決定性，則檢視表也具決定性。</span><span class="sxs-lookup"><span data-stu-id="24fc7-175">A view is deterministic if all expressions in the select list, as well as the WHERE and GROUP BY clauses, are deterministic.</span></span> <span data-ttu-id="24fc7-176">每當利用一組特定的輸入值來評估具決定性的運算式時，具決定性的運算式一律傳回相同的結果。</span><span class="sxs-lookup"><span data-stu-id="24fc7-176">Deterministic expressions always return the same result any time they are evaluated with a specific set of input values.</span></span> <span data-ttu-id="24fc7-177">只有具決定性的函數可以參與具決定性的運算式。</span><span class="sxs-lookup"><span data-stu-id="24fc7-177">Only deterministic functions can participate in deterministic expressions.</span></span> <span data-ttu-id="24fc7-178">例如，DATEADD 函數具決定性，因為它會針對它的三個參數之任何一組給定的引數值一律傳回相同的結果。</span><span class="sxs-lookup"><span data-stu-id="24fc7-178">For example, the DATEADD function is deterministic because it always returns the same result for any given set of argument values for its three parameters.</span></span> <span data-ttu-id="24fc7-179">GETDATE 不具決定性，因為它一律被相同的引數叫用，但是，每當它被執行時，它所傳回的值都會變更。</span><span class="sxs-lookup"><span data-stu-id="24fc7-179">GETDATE is not deterministic because it is always invoked with the same argument, but the value it returns changes each time it is executed.</span></span>  
  
 <span data-ttu-id="24fc7-180">若要判斷檢視表資料行是否具決定性，請使用 **COLUMNPROPERTY** 函數的 [IsDeterministic](/sql/t-sql/functions/columnproperty-transact-sql) 屬性。</span><span class="sxs-lookup"><span data-stu-id="24fc7-180">To determine whether a view column is deterministic, use the **IsDeterministic** property of the [COLUMNPROPERTY](/sql/t-sql/functions/columnproperty-transact-sql) function.</span></span> <span data-ttu-id="24fc7-181">若要判斷含有結構描述繫結之檢視表中的具決定性資料行是否為精確資料行，請利用 COLUMNPROPERTY 函數的 **IsPrecise** 屬性。</span><span class="sxs-lookup"><span data-stu-id="24fc7-181">To determine if a deterministic column in a view with schema binding is precise, use the **IsPrecise** property of the COLUMNPROPERTY function.</span></span> <span data-ttu-id="24fc7-182">如果是 TRUE，COLUMNPROPERTY 會傳回 1；如果是 FALSE，則傳回 0；如果輸入無效，則傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="24fc7-182">COLUMNPROPERTY returns 1 if TRUE, 0 if FALSE, and NULL for input that is not valid.</span></span> <span data-ttu-id="24fc7-183">這表示這個資料行不具決定性或不是精確資料行。</span><span class="sxs-lookup"><span data-stu-id="24fc7-183">This means the column is not deterministic or not precise.</span></span>  
  
 <span data-ttu-id="24fc7-184">即使運算式具決定性，如果它包含浮點運算式，確切的結果仍取決於處理器架構或微碼的版本而定。</span><span class="sxs-lookup"><span data-stu-id="24fc7-184">Even if an expression is deterministic, if it contains float expressions, the exact result may depend on the processor architecture or version of microcode.</span></span> <span data-ttu-id="24fc7-185">若要確保資料完整性，這類運算式在參與時可以只做為索引檢視表的非索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="24fc7-185">To ensure data integrity, such expressions can participate only as non-key columns of indexed views.</span></span> <span data-ttu-id="24fc7-186">未含浮點運算式之具決定性的運算式稱為精確運算式。</span><span class="sxs-lookup"><span data-stu-id="24fc7-186">Deterministic expressions that do not contain float expressions are called precise.</span></span> <span data-ttu-id="24fc7-187">只有精確之具決定性的運算式可以參與索引鍵資料行和索引檢視表的 WHERE 或 GROUP BY 子句。</span><span class="sxs-lookup"><span data-stu-id="24fc7-187">Only precise deterministic expressions can participate in key columns and in WHERE or GROUP BY clauses of indexed views.</span></span>  
  
### <a name="additional-requirements"></a><span data-ttu-id="24fc7-188">其他需求</span><span class="sxs-lookup"><span data-stu-id="24fc7-188">Additional Requirements</span></span>  
 <span data-ttu-id="24fc7-189">除了 SET 選項和具決定性函數的需求以外，下列需求也必須符合：</span><span class="sxs-lookup"><span data-stu-id="24fc7-189">In addition to the SET options and deterministic function requirements, the following requirements must be met:</span></span>  
  
-   <span data-ttu-id="24fc7-190">執行 CREATE INDEX 的使用者必須是檢視表的擁有者。</span><span class="sxs-lookup"><span data-stu-id="24fc7-190">The user that executes CREATE INDEX must be the owner of the view.</span></span>  
  
-   <span data-ttu-id="24fc7-191">當您建立索引時，IGNORE_DUP_KEY 選項必須設定為 OFF (預設值)。</span><span class="sxs-lookup"><span data-stu-id="24fc7-191">When you create the index, the IGNORE_DUP_KEY option must be set to OFF (the default setting).</span></span>  
  
-   <span data-ttu-id="24fc7-192">在檢視定義中，兩部分名稱 _schema_ **.** _tablename_ 必須參考資料表。</span><span class="sxs-lookup"><span data-stu-id="24fc7-192">Tables must be referenced by two-part names, _schema_**.**_tablename_ in the view definition.</span></span>  
  
-   <span data-ttu-id="24fc7-193">檢視中所參考的使用者自訂函數，必須使用 WITH SCHEMABINDING 選項來建立。</span><span class="sxs-lookup"><span data-stu-id="24fc7-193">User-defined functions referenced in the view must be created by using the WITH SCHEMABINDING option.</span></span>  
  
-   <span data-ttu-id="24fc7-194">在此視圖中參考的任何使用者定義函數，都必須由兩部分名稱_schema_所參考 **。**_函數_。</span><span class="sxs-lookup"><span data-stu-id="24fc7-194">Any user-defined functions referenced in the view must be referenced by two-part names, _schema_**.**_function_.</span></span>  
  
-   <span data-ttu-id="24fc7-195">使用者自訂函數的資料存取屬性必須是 NO SQL，而外部存取屬性必須是 NO。</span><span class="sxs-lookup"><span data-stu-id="24fc7-195">The data access property of a user-defined function must be NO SQL, and external access property must be NO.</span></span>  
  
-   <span data-ttu-id="24fc7-196">Common Language Runtime (CLR) 函數可以在檢視的選取清單中出現，但是不可以是叢集索引鍵定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="24fc7-196">Common language runtime (CLR) functions can appear in the select list of the view, but cannot be part of the definition of the clustered index key.</span></span> <span data-ttu-id="24fc7-197">CLR 函數不能出現在檢視的 WHERE 子句或檢視中之 JOIN 作業的 ON 子句。</span><span class="sxs-lookup"><span data-stu-id="24fc7-197">CLR functions cannot appear in the WHERE clause of the view or the ON clause of a JOIN operation in the view.</span></span>  
  
-   <span data-ttu-id="24fc7-198">用於檢視定義中的 CLR 函數和 CLR 使用者定義型別的方法必須有下表所示的屬性。</span><span class="sxs-lookup"><span data-stu-id="24fc7-198">CLR functions and methods of CLR user-defined types used in the view definition must have the properties set as shown in the following table.</span></span>  
  
    |<span data-ttu-id="24fc7-199">屬性</span><span class="sxs-lookup"><span data-stu-id="24fc7-199">Property</span></span>|<span data-ttu-id="24fc7-200">附註</span><span class="sxs-lookup"><span data-stu-id="24fc7-200">Note</span></span>|  
    |--------------|----------|  
    |<span data-ttu-id="24fc7-201">DETERMINISTIC = TRUE</span><span class="sxs-lookup"><span data-stu-id="24fc7-201">DETERMINISTIC = TRUE</span></span>|<span data-ttu-id="24fc7-202">必須明確宣告為 Microsoft .NET Framework 方法的屬性。</span><span class="sxs-lookup"><span data-stu-id="24fc7-202">Must be declared explicitly as an attribute of the Microsoft .NET Framework method.</span></span>|  
    |<span data-ttu-id="24fc7-203">PRECISE = TRUE</span><span class="sxs-lookup"><span data-stu-id="24fc7-203">PRECISE = TRUE</span></span>|<span data-ttu-id="24fc7-204">必須明確宣告為 .NET Framework 方法的屬性。</span><span class="sxs-lookup"><span data-stu-id="24fc7-204">Must be declared explicitly as an attribute of the .NET Framework method.</span></span>|  
    |<span data-ttu-id="24fc7-205">DATA ACCESS = NO SQL</span><span class="sxs-lookup"><span data-stu-id="24fc7-205">DATA ACCESS = NO SQL</span></span>|<span data-ttu-id="24fc7-206">將 DataAccess 屬性設定為 DataAccessKind.None 以及將 SystemDataAccess 屬性設定為 SystemDataAccessKind.None 決定。</span><span class="sxs-lookup"><span data-stu-id="24fc7-206">Determined by setting DataAccess attribute to DataAccessKind.None and SystemDataAccess attribute to SystemDataAccessKind.None.</span></span>|  
    |<span data-ttu-id="24fc7-207">EXTERNAL ACCESS = NO</span><span class="sxs-lookup"><span data-stu-id="24fc7-207">EXTERNAL ACCESS = NO</span></span>|<span data-ttu-id="24fc7-208">對 CLR 常式，此屬性預設為 NO。</span><span class="sxs-lookup"><span data-stu-id="24fc7-208">This property defaults to NO for CLR routines.</span></span>|  
  
-   <span data-ttu-id="24fc7-209">必須利用 WITH SCHEMABINDING 選項來建立檢視表。</span><span class="sxs-lookup"><span data-stu-id="24fc7-209">The view must be created by using the WITH SCHEMABINDING option.</span></span>  
  
-   <span data-ttu-id="24fc7-210">檢視必須只參考與檢視位於相同資料庫中的基底資料表。</span><span class="sxs-lookup"><span data-stu-id="24fc7-210">The view must reference only base tables that are in the same database as the view.</span></span> <span data-ttu-id="24fc7-211">檢視不可參考其他檢視。</span><span class="sxs-lookup"><span data-stu-id="24fc7-211">The view cannot reference other views.</span></span>  
  
-   <span data-ttu-id="24fc7-212">檢視定義中的 SELECT 陳述式不得包含下列 Transact-SQL 元素：</span><span class="sxs-lookup"><span data-stu-id="24fc7-212">The SELECT statement in the view definition must not contain the following Transact-SQL elements:</span></span>  
  
    ||||  
    |-|-|-|  
    |<span data-ttu-id="24fc7-213">COUNT</span><span class="sxs-lookup"><span data-stu-id="24fc7-213">COUNT</span></span>|<span data-ttu-id="24fc7-214">ROWSET 函數 (OPENDATASOURCE、OPENQUERY、OPENROWSET 和 OPENXML)</span><span class="sxs-lookup"><span data-stu-id="24fc7-214">ROWSET functions (OPENDATASOURCE, OPENQUERY, OPENROWSET, AND OPENXML)</span></span>|<span data-ttu-id="24fc7-215">OUTER 聯結 (LEFT、RIGHT 或 FULL)</span><span class="sxs-lookup"><span data-stu-id="24fc7-215">OUTER joins (LEFT, RIGHT, or FULL)</span></span>|  
    |<span data-ttu-id="24fc7-216">衍生資料表 (藉由在 FROM 子句中指定 SELECT 陳述式定義)</span><span class="sxs-lookup"><span data-stu-id="24fc7-216">Derived table (defined by specifying a SELECT statement in the FROM clause)</span></span>|<span data-ttu-id="24fc7-217">自我聯結</span><span class="sxs-lookup"><span data-stu-id="24fc7-217">Self-joins</span></span>|<span data-ttu-id="24fc7-218">使用 SELECT \* 或 SELECT *table_name*\* 指定資料行。</span><span class="sxs-lookup"><span data-stu-id="24fc7-218">Specifying columns by using SELECT \* or SELECT *table_name*.\*</span></span>|  
    |<span data-ttu-id="24fc7-219">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="24fc7-219">DISTINCT</span></span>|<span data-ttu-id="24fc7-220">STDEV、STDEVP、VAR、VARP 或 AVG</span><span class="sxs-lookup"><span data-stu-id="24fc7-220">STDEV, STDEVP, VAR, VARP, or AVG</span></span>|<span data-ttu-id="24fc7-221">通用資料表運算式 (CTE)</span><span class="sxs-lookup"><span data-stu-id="24fc7-221">Common table expression (CTE)</span></span>|  
    |<span data-ttu-id="24fc7-222">`float`\*、 `text` 、 `ntext` 、 `image` 、 `XML` 或資料 `filestream` 行</span><span class="sxs-lookup"><span data-stu-id="24fc7-222">`float`\*, `text`, `ntext`, `image`, `XML`, or `filestream` columns</span></span>|<span data-ttu-id="24fc7-223">子查詢</span><span class="sxs-lookup"><span data-stu-id="24fc7-223">Subquery</span></span>|<span data-ttu-id="24fc7-224">OVER 子句，其中包含次序或彙總視窗函數</span><span class="sxs-lookup"><span data-stu-id="24fc7-224">OVER clause, which includes ranking or aggregate window functions</span></span>|  
    |<span data-ttu-id="24fc7-225">全文檢索述詞 (CONTAIN、FREETEXT)</span><span class="sxs-lookup"><span data-stu-id="24fc7-225">Full-text predicates (CONTAIN, FREETEXT)</span></span>|<span data-ttu-id="24fc7-226">SUM 函數，參考可為 Null 值的運算式</span><span class="sxs-lookup"><span data-stu-id="24fc7-226">SUM function that references a nullable expression</span></span>|<span data-ttu-id="24fc7-227">排序依據</span><span class="sxs-lookup"><span data-stu-id="24fc7-227">ORDER BY</span></span>|  
    |<span data-ttu-id="24fc7-228">CLR 使用者定義彙總函式</span><span class="sxs-lookup"><span data-stu-id="24fc7-228">CLR user-defined aggregate function</span></span>|<span data-ttu-id="24fc7-229">頂端</span><span class="sxs-lookup"><span data-stu-id="24fc7-229">TOP</span></span>|<span data-ttu-id="24fc7-230">CUBE、ROLLUP 或 GROUPING SETS 運算子</span><span class="sxs-lookup"><span data-stu-id="24fc7-230">CUBE, ROLLUP, or GROUPING SETS operators</span></span>|  
    |<span data-ttu-id="24fc7-231">MIN、MAX</span><span class="sxs-lookup"><span data-stu-id="24fc7-231">MIN, MAX</span></span>|<span data-ttu-id="24fc7-232">UNION、EXCEPT 或 INTERSECT 運算子</span><span class="sxs-lookup"><span data-stu-id="24fc7-232">UNION, EXCEPT, or INTERSECT operators</span></span>|<span data-ttu-id="24fc7-233">TABLESAMPLE</span><span class="sxs-lookup"><span data-stu-id="24fc7-233">TABLESAMPLE</span></span>|  
    |<span data-ttu-id="24fc7-234">資料表變數</span><span class="sxs-lookup"><span data-stu-id="24fc7-234">Table variables</span></span>|<span data-ttu-id="24fc7-235">OUTER APPLY 或 CROSS APPLY</span><span class="sxs-lookup"><span data-stu-id="24fc7-235">OUTER APPLY or CROSS APPLY</span></span>|<span data-ttu-id="24fc7-236">PIVOT、UNPIVOT</span><span class="sxs-lookup"><span data-stu-id="24fc7-236">PIVOT, UNPIVOT</span></span>|  
    |<span data-ttu-id="24fc7-237">疏鬆資料行集合</span><span class="sxs-lookup"><span data-stu-id="24fc7-237">Sparse column sets</span></span>|<span data-ttu-id="24fc7-238">內嵌或多重陳述式資料表值函式</span><span class="sxs-lookup"><span data-stu-id="24fc7-238">Inline or multi-statement table-valued functions</span></span>|<span data-ttu-id="24fc7-239">OFFSET</span><span class="sxs-lookup"><span data-stu-id="24fc7-239">OFFSET</span></span>|  
    |<span data-ttu-id="24fc7-240">CHECKSUM_AGG</span><span class="sxs-lookup"><span data-stu-id="24fc7-240">CHECKSUM_AGG</span></span>|||  
  
     <span data-ttu-id="24fc7-241">\*索引視圖可以包含資料 `float` 行; 不過，這類資料行不能包含在叢集索引鍵中。</span><span class="sxs-lookup"><span data-stu-id="24fc7-241">\*The indexed view can contain `float` columns; however, such columns cannot be included in the clustered index key.</span></span>  
  
-   <span data-ttu-id="24fc7-242">如果有 GROUP BY，VIEW 定義必須包含 COUNT_BIG(\*)，且不能包含 HAVING。</span><span class="sxs-lookup"><span data-stu-id="24fc7-242">If GROUP BY is present, the VIEW definition must contain COUNT_BIG(\*) and must not contain HAVING.</span></span> <span data-ttu-id="24fc7-243">GROUP BY 限制只適用於索引檢視表定義。</span><span class="sxs-lookup"><span data-stu-id="24fc7-243">These GROUP BY restrictions are applicable only to the indexed view definition.</span></span> <span data-ttu-id="24fc7-244">即使索引檢視表不符合這些 GROUP BY 限制，查詢還是可以在它的執行計畫中使用索引檢視表。</span><span class="sxs-lookup"><span data-stu-id="24fc7-244">A query can use an indexed view in its execution plan even if it does not satisfy these GROUP BY restrictions.</span></span>  
  
-   <span data-ttu-id="24fc7-245">如果檢視表定義包含 GROUP BY 子句，唯一叢集索引的索引鍵則只能參考 GROUP BY 子句中指定的資料行。</span><span class="sxs-lookup"><span data-stu-id="24fc7-245">If the view definition contains a GROUP BY clause, the key of the unique clustered index can reference only the columns specified in the GROUP BY clause.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="24fc7-246">建議</span><span class="sxs-lookup"><span data-stu-id="24fc7-246">Recommendations</span></span>  
 <span data-ttu-id="24fc7-247">當您在索引檢視中參考 `datetime` 和 `smalldatetime` 字串常值時，我們建議您使用決定性的日期格式樣式，將常值明確轉換成您想要的日期類型。</span><span class="sxs-lookup"><span data-stu-id="24fc7-247">When you refer to `datetime` and `smalldatetime` string literals in indexed views, we recommend that you explicitly convert the literal to the date type you want by using a deterministic date format style.</span></span> <span data-ttu-id="24fc7-248">如需具有決定性之日期格式樣式的清單，請參閱 [CAST 和 CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="24fc7-248">For a list of the date format styles that are deterministic, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span> <span data-ttu-id="24fc7-249">牽涉到將字元字串隱含轉換成 `datetime` 或 `smalldatetime` 的運算式是視為非決定性的。</span><span class="sxs-lookup"><span data-stu-id="24fc7-249">Expressions that involve implicit conversion of character strings to `datetime` or `smalldatetime` are considered nondeterministic.</span></span> <span data-ttu-id="24fc7-250">這是因為結果需視伺服器工作階段的 LANGUAGE 和 DATEFORMAT 設定而定。</span><span class="sxs-lookup"><span data-stu-id="24fc7-250">This is because the results depend on the LANGUAGE and DATEFORMAT settings of the server session.</span></span> <span data-ttu-id="24fc7-251">例如，運算式 `CONVERT (datetime, '30 listopad 1996', 113)` 的結果需視 LANGUAGE 設定而定，因為字串 '`listopad`' 在不同的語言中表示不同的月份。</span><span class="sxs-lookup"><span data-stu-id="24fc7-251">For example, the results of the expression `CONVERT (datetime, '30 listopad 1996', 113)` depend on the LANGUAGE setting because the string '`listopad`' means different months in different languages.</span></span> <span data-ttu-id="24fc7-252">同樣地，在運算式 `DATEADD(mm,3,'2000-12-01')`中， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會根據 DATEFORMAT 設定解譯字串 `'2000-12-01'` 。</span><span class="sxs-lookup"><span data-stu-id="24fc7-252">Similarly, in the expression `DATEADD(mm,3,'2000-12-01')`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprets the string `'2000-12-01'` based on the DATEFORMAT setting.</span></span>  
  
 <span data-ttu-id="24fc7-253">非 Unicode 字元資料與定序之間的隱含轉換也是視為非決定性的。</span><span class="sxs-lookup"><span data-stu-id="24fc7-253">Implicit conversion of non-Unicode character data between collations is also considered nondeterministic.</span></span>  
  
###  <a name="considerations"></a><a name="Considerations"></a> <span data-ttu-id="24fc7-254">考量</span><span class="sxs-lookup"><span data-stu-id="24fc7-254">Considerations</span></span>  
 <span data-ttu-id="24fc7-255">索引檢視表中資料行的 **large_value_types_out_of_row** 選項設定是繼承基底資料表中對應的資料行設定。</span><span class="sxs-lookup"><span data-stu-id="24fc7-255">The setting of the **large_value_types_out_of_row** option of columns in an indexed view is inherited from the setting of the corresponding column in the base table.</span></span> <span data-ttu-id="24fc7-256">此值可透過 [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql)設定。</span><span class="sxs-lookup"><span data-stu-id="24fc7-256">This value is set by using [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql).</span></span> <span data-ttu-id="24fc7-257">由運算式形成的資料行其預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="24fc7-257">The default setting for columns formed from expressions is 0.</span></span> <span data-ttu-id="24fc7-258">這表示大數值類型是以資料列的方式儲存。</span><span class="sxs-lookup"><span data-stu-id="24fc7-258">This means that large value types are stored in-row.</span></span>  
  
 <span data-ttu-id="24fc7-259">可以在分割區資料表上建立索引檢視表，且索引檢視表本身也可以分割。</span><span class="sxs-lookup"><span data-stu-id="24fc7-259">Indexed views can be created on a partitioned table, and can themselves be partitioned.</span></span>  
  
 <span data-ttu-id="24fc7-260">若要防止 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 使用索引檢視表，請在查詢上併入 OPTION (EXPAND VIEWS) 提示。</span><span class="sxs-lookup"><span data-stu-id="24fc7-260">To prevent the [!INCLUDE[ssDE](../../includes/ssde-md.md)] from using indexed views, include the OPTION (EXPAND VIEWS) hint on the query.</span></span> <span data-ttu-id="24fc7-261">另外，如果列出的選項中有任何選項設定不正確，就會防止最佳化工具使用檢視表上的索引。</span><span class="sxs-lookup"><span data-stu-id="24fc7-261">Also, if any of the listed options are incorrectly set, this will prevent the optimizer from using the indexes on the views.</span></span> <span data-ttu-id="24fc7-262">如需 OPTION (EXPAND VIEWS) 提示的詳細資訊，請參閱 [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="24fc7-262">For more information about the OPTION (EXPAND VIEWS) hint, see [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql).</span></span>  
  
 <span data-ttu-id="24fc7-263">卸除檢視時會卸除檢視的所有索引。</span><span class="sxs-lookup"><span data-stu-id="24fc7-263">All indexes on a view are dropped when the view is dropped.</span></span> <span data-ttu-id="24fc7-264">如果卸除叢集索引，也會卸除檢視的所有非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="24fc7-264">All nonclustered indexes and auto-created statistics on the view are dropped when the clustered index is dropped.</span></span> <span data-ttu-id="24fc7-265">但會保留使用者在檢視所建立的統計。</span><span class="sxs-lookup"><span data-stu-id="24fc7-265">User-created statistics on the view are maintained.</span></span> <span data-ttu-id="24fc7-266">每個非叢集索引則可以分別卸除。</span><span class="sxs-lookup"><span data-stu-id="24fc7-266">Nonclustered indexes can be individually dropped.</span></span> <span data-ttu-id="24fc7-267">卸除檢視的叢集索引會刪除儲存的結果集，使最佳化工具回到以標準檢視的方式處理檢視。</span><span class="sxs-lookup"><span data-stu-id="24fc7-267">Dropping the clustered index on the view removes the stored result set, and the optimizer returns to processing the view like a standard view.</span></span>  
  
 <span data-ttu-id="24fc7-268">您可以停用資料表與檢視的索引。</span><span class="sxs-lookup"><span data-stu-id="24fc7-268">Indexes on tables and views can be disabled.</span></span> <span data-ttu-id="24fc7-269">停用資料表的叢集索引時，也會停用與資料表相關之檢視的索引。</span><span class="sxs-lookup"><span data-stu-id="24fc7-269">When a clustered index on a table is disabled, indexes on views associated with the table are also disabled.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="24fc7-270">Security</span><span class="sxs-lookup"><span data-stu-id="24fc7-270">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="24fc7-271">權限</span><span class="sxs-lookup"><span data-stu-id="24fc7-271">Permissions</span></span>  
 <span data-ttu-id="24fc7-272">至少必須有資料庫中的 CREATE VIEW 權限，以及正在建立之檢視表所在之結構描述的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="24fc7-272">Requires CREATE VIEW permission in the database and ALTER permission on the schema in which the view is being created.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="24fc7-273">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="24fc7-273">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-indexed-view"></a><span data-ttu-id="24fc7-274">建立索引檢視表</span><span class="sxs-lookup"><span data-stu-id="24fc7-274">To create an indexed view</span></span>  
  
1.  <span data-ttu-id="24fc7-275">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="24fc7-275">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="24fc7-276">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="24fc7-276">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="24fc7-277">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="24fc7-277">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="24fc7-278">此範例會建立檢視表並在該檢視表上建立索引。</span><span class="sxs-lookup"><span data-stu-id="24fc7-278">The example creates a view and an index on that view.</span></span> <span data-ttu-id="24fc7-279">內含使用索引檢視的兩項查詢。</span><span class="sxs-lookup"><span data-stu-id="24fc7-279">Two queries are included that use the indexed view.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    --Set the options to support indexed views.  
    SET NUMERIC_ROUNDABORT OFF;  
    SET ANSI_PADDING, ANSI_WARNINGS, CONCAT_NULL_YIELDS_NULL, ARITHABORT,  
        QUOTED_IDENTIFIER, ANSI_NULLS ON;  
    GO  
    --Create view with schemabinding.  
    IF OBJECT_ID ('Sales.vOrders', 'view') IS NOT NULL  
    DROP VIEW Sales.vOrders ;  
    GO  
    CREATE VIEW Sales.vOrders  
    WITH SCHEMABINDING  
    AS  
        SELECT SUM(UnitPrice*OrderQty*(1.00-UnitPriceDiscount)) AS Revenue,  
            OrderDate, ProductID, COUNT_BIG(*) AS COUNT  
        FROM Sales.SalesOrderDetail AS od, Sales.SalesOrderHeader AS o  
        WHERE od.SalesOrderID = o.SalesOrderID  
        GROUP BY OrderDate, ProductID;  
    GO  
    --Create an index on the view.  
    CREATE UNIQUE CLUSTERED INDEX IDX_V1   
        ON Sales.vOrders (OrderDate, ProductID);  
    GO  
    --This query can use the indexed view even though the view is   
    --not specified in the FROM clause.  
    SELECT SUM(UnitPrice*OrderQty*(1.00-UnitPriceDiscount)) AS Rev,   
        OrderDate, ProductID  
    FROM Sales.SalesOrderDetail AS od  
        JOIN Sales.SalesOrderHeader AS o ON od.SalesOrderID=o.SalesOrderID  
            AND ProductID BETWEEN 700 and 800  
            AND OrderDate >= CONVERT(datetime,'05/01/2002',101)  
    GROUP BY OrderDate, ProductID  
    ORDER BY Rev DESC;  
    GO  
    --This query can use the above indexed view.  
    SELECT  OrderDate, SUM(UnitPrice*OrderQty*(1.00-UnitPriceDiscount)) AS Rev  
    FROM Sales.SalesOrderDetail AS od  
        JOIN Sales.SalesOrderHeader AS o ON od.SalesOrderID=o.SalesOrderID  
            AND DATEPART(mm,OrderDate)= 3  
            AND DATEPART(yy,OrderDate) = 2002  
    GROUP BY OrderDate  
    ORDER BY OrderDate ASC;  
    GO  
    ```  
  
 <span data-ttu-id="24fc7-280">如需詳細資訊，請參閱 [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="24fc7-280">For more information, see [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24fc7-281">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24fc7-281">See Also</span></span>  
 <span data-ttu-id="24fc7-282">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="24fc7-282">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="24fc7-283">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="24fc7-283">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span></span>  
 <span data-ttu-id="24fc7-284">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="24fc7-284">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span></span>  
 <span data-ttu-id="24fc7-285">[SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="24fc7-285">[SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql) </span></span>  
 <span data-ttu-id="24fc7-286">[SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="24fc7-286">[SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql) </span></span>  
 <span data-ttu-id="24fc7-287">[SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-concat-null-yields-null-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="24fc7-287">[SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-concat-null-yields-null-transact-sql) </span></span>  
 <span data-ttu-id="24fc7-288">[SET NUMERIC_ROUNDABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-numeric-roundabort-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="24fc7-288">[SET NUMERIC_ROUNDABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-numeric-roundabort-transact-sql) </span></span>  
 [<span data-ttu-id="24fc7-289">SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="24fc7-289">SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-quoted-identifier-transact-sql)  
  
  
