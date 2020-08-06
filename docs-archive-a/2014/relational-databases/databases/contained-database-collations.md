---
title: 自主資料庫定序 | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- contained database, collations
ms.assetid: 4b44f6b9-2359-452f-8bb1-5520f2528483
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2648dbedea7708c4f39c922c56bba96cf38b0c0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702970"
---
# <a name="contained-database-collations"></a><span data-ttu-id="c72fc-102">自主資料庫定序</span><span class="sxs-lookup"><span data-stu-id="c72fc-102">Contained Database Collations</span></span>
  <span data-ttu-id="c72fc-103">許多屬性會影響文字資料的排序次序和相等語意，包括區分大小寫、區分腔調字和使用的基底語言。</span><span class="sxs-lookup"><span data-stu-id="c72fc-103">Various properties affect the sort order and equality semantics of textual data, including case sensitivity, accent sensitivity, and the base language being used.</span></span> <span data-ttu-id="c72fc-104">這些品質會透過資料的定序選擇表達至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c72fc-104">These qualities are expressed to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] through the choice of collation for the data.</span></span> <span data-ttu-id="c72fc-105">如需定序本身的更深入討論，請參閱 [定序與 Unicode 支援](../collations/collation-and-unicode-support.md)。</span><span class="sxs-lookup"><span data-stu-id="c72fc-105">For a more in-depth discussion of collations themselves, see [Collation and Unicode Support](../collations/collation-and-unicode-support.md).</span></span>  
  
 <span data-ttu-id="c72fc-106">定序不只會套用至儲存在使用者資料表中的資料，還會套用至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所處理的所有文字，包括中繼資料、暫存物件、變數名稱等。在自主及非自主資料庫中，這些項目的處理方式有所不同。</span><span class="sxs-lookup"><span data-stu-id="c72fc-106">Collations apply not only to data stored in user tables, but to all text handled by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], including metadata, temporary objects, variable names, etc. The handling of these differs in contained and non-contained databases.</span></span> <span data-ttu-id="c72fc-107">雖然這項變更不會影響許多使用者，不過有助於提供執行個體獨立性和統一性。</span><span class="sxs-lookup"><span data-stu-id="c72fc-107">This change will not affect many users, but helps provide instance independence and uniformity.</span></span> <span data-ttu-id="c72fc-108">但是，這項變更可能也會導致一些混淆，並且導致同時存取包含和非自主資料庫的工作階段發生問題。</span><span class="sxs-lookup"><span data-stu-id="c72fc-108">But this may also cause some confusion, as well as problems for sessions that access both contained and non-contained databases.</span></span>  
  
 <span data-ttu-id="c72fc-109">本主題將釐清此變更的內容，並且檢查此變更可能會導致問題的區域。</span><span class="sxs-lookup"><span data-stu-id="c72fc-109">This topic clarifies the content of the change, and examines areas where the change may cause problems.</span></span>  
  
## <a name="non-contained-databases"></a><span data-ttu-id="c72fc-110">非自主資料庫</span><span class="sxs-lookup"><span data-stu-id="c72fc-110">Non-Contained Databases</span></span>  
 <span data-ttu-id="c72fc-111">所有資料庫都具有預設定序 (可在建立或改變資料庫時設定)。</span><span class="sxs-lookup"><span data-stu-id="c72fc-111">All databases have a default collation (which can be set when creating or altering a database.</span></span> <span data-ttu-id="c72fc-112">這個定序會用於資料庫中的所有中繼資料，以及資料庫中所有字串資料行的預設值。</span><span class="sxs-lookup"><span data-stu-id="c72fc-112">This collation is used for all metadata in the database, as well as the default for all string columns within the database.</span></span> <span data-ttu-id="c72fc-113">使用者可以使用 `COLLATE` 子句，針對任何特定的資料行選擇不同的定序。</span><span class="sxs-lookup"><span data-stu-id="c72fc-113">Users can choose a different collation for any particular column by using the `COLLATE` clause.</span></span>  
  
### <a name="example-1"></a><span data-ttu-id="c72fc-114">範例 1</span><span class="sxs-lookup"><span data-stu-id="c72fc-114">Example 1</span></span>  
 <span data-ttu-id="c72fc-115">例如，如果我們在北京工作，可能會使用中文定序：</span><span class="sxs-lookup"><span data-stu-id="c72fc-115">For example, if we were working in Beijing, we might use a Chinese collation:</span></span>  
  
```sql  
ALTER DATABASE MyDB COLLATE Chinese_Simplified_Pinyin_100_CI_AS;  
```  
  
 <span data-ttu-id="c72fc-116">現在，如果我們建立一個資料行，其預設定序就是這個中文定序，但是如果我們想要，也可以選擇另一個定序：</span><span class="sxs-lookup"><span data-stu-id="c72fc-116">Now if we create a column, its default collation will be this Chinese collation, but we can choose another one if we want:</span></span>  
  
```sql  
CREATE TABLE MyTable  
      (mycolumn1 nvarchar,  
      mycolumn2 nvarchar COLLATE Frisian_100_CS_AS);  
GO  
SELECT name, collation_name  
FROM sys.columns  
WHERE name LIKE 'mycolumn%' ;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```sql  
name            collation_name  
--------------- ----------------------------------  
mycolumn1       Chinese_Simplified_Pinyin_100_CI_AS  
mycolumn2       Frisian_100_CS_AS  
```  
  
 <span data-ttu-id="c72fc-117">這段程式碼似乎相當簡單，不過卻引發許多問題。</span><span class="sxs-lookup"><span data-stu-id="c72fc-117">This appears relatively simple, but several problems arise.</span></span> <span data-ttu-id="c72fc-118">因為資料行的定序相依于建立資料表所在的資料庫，所以使用儲存在中的臨時表就會發生問題 `tempdb` 。</span><span class="sxs-lookup"><span data-stu-id="c72fc-118">Because the collation for a column is dependent on the database in which the table is created, problems arise with the use of temporary tables which are stored in `tempdb`.</span></span> <span data-ttu-id="c72fc-119">的定序 `tempdb` 通常符合實例的定序，而不需要符合資料庫定序。</span><span class="sxs-lookup"><span data-stu-id="c72fc-119">The collation of `tempdb` usually matches the collation for the instance, which does not have to match the database collation.</span></span>  
  
### <a name="example-2"></a><span data-ttu-id="c72fc-120">範例 2</span><span class="sxs-lookup"><span data-stu-id="c72fc-120">Example 2</span></span>  
 <span data-ttu-id="c72fc-121">例如，假設上述 (中文) 資料庫使用於具有 **Latin1_General** 定序的執行個體上：</span><span class="sxs-lookup"><span data-stu-id="c72fc-121">For example, consider the (Chinese) database above when used on an instance with a **Latin1_General** collation:</span></span>  
  
```sql  
CREATE TABLE T1 (T1_txt nvarchar(max)) ;  
GO  
CREATE TABLE #T2 (T2_txt nvarchar(max)) ;  
GO  
```  
  
 <span data-ttu-id="c72fc-122">第一眼看起來，這兩個資料表看似具有相同的結構描述，不過因為資料庫的定序不同，所以其值實際上不相容：</span><span class="sxs-lookup"><span data-stu-id="c72fc-122">At first glance, these two tables look like they have the same schema, but since the collations of the databases differ, the values are actually incompatible:</span></span>  
  
```  
SELECT T1_txt, T2_txt  
FROM T1   
JOIN #T2   
    ON T1.T1_txt = #T2.T2_txt  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 <span data-ttu-id="c72fc-123">訊息 468，層級 16，狀態 9，行 2</span><span class="sxs-lookup"><span data-stu-id="c72fc-123">Msg 468, Level 16, State 9, Line 2</span></span>  
  
 <span data-ttu-id="c72fc-124">無法解析 equal to 作業中 "Latin1_General_100_CI_AS_KS_WS_SC" 及 "Chinese_Simplified_Pinyin_100_CI_AS" 之間的定序衝突。</span><span class="sxs-lookup"><span data-stu-id="c72fc-124">Cannot resolve the collation conflict between "Latin1_General_100_CI_AS_KS_WS_SC" and Chinese_Simplified_Pinyin_100_CI_AS" in the equal to operation.</span></span>  
  
 <span data-ttu-id="c72fc-125">修正此問題的方法是明確地建立暫時資料表的定序。</span><span class="sxs-lookup"><span data-stu-id="c72fc-125">We can fix this by explicitly collating the temporary table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c72fc-126">可提供 `DATABASE_DEFAULT` 子句的 `COLLATE` 關鍵字，以簡化此作業。</span><span class="sxs-lookup"><span data-stu-id="c72fc-126">makes this somewhat easier by providing the `DATABASE_DEFAULT` keyword for the `COLLATE` clause.</span></span>  
  
```sql  
CREATE TABLE T1 (T1_txt nvarchar(max)) ;  
GO  
CREATE TABLE #T2 (T2_txt nvarchar(max) COLLATE DATABASE_DEFAULT);  
GO  
SELECT T1_txt, T2_txt  
FROM T1   
JOIN #T2   
    ON T1.T1_txt = #T2.T2_txt ;  
```  
  
 <span data-ttu-id="c72fc-127">這段程式碼現在執行時不會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c72fc-127">This now runs without error.</span></span>  
  
 <span data-ttu-id="c72fc-128">我們也可以使用變數來查看定序相依的行為。</span><span class="sxs-lookup"><span data-stu-id="c72fc-128">We can also see collation-dependent behavior with variables.</span></span> <span data-ttu-id="c72fc-129">以下列函數為例：</span><span class="sxs-lookup"><span data-stu-id="c72fc-129">Consider the following function:</span></span>  
  
```  
CREATE FUNCTION f(@x INT) RETURNS INT  
AS BEGIN   
      DECLARE @I INT = 1  
      DECLARE @?? INT = 2  
      RETURN @x * @i  
END;  
```  
  
 <span data-ttu-id="c72fc-130">這是相當罕見的函數。</span><span class="sxs-lookup"><span data-stu-id="c72fc-130">This is a rather peculiar function.</span></span> <span data-ttu-id="c72fc-131">在區分大小寫的定序中， @i return 子句中的無法系結至 @I 或 @??。</span><span class="sxs-lookup"><span data-stu-id="c72fc-131">In a case-sensitive collation, the @i in the return clause cannot bind to either @I or @??.</span></span> <span data-ttu-id="c72fc-132">在不區分大小寫的 Latin1_General 定序中，@i 會繫結至 @I，而且函數會傳回 1。</span><span class="sxs-lookup"><span data-stu-id="c72fc-132">In a case-insensitive Latin1_General collation, @i binds to @I, and the function returns 1.</span></span> <span data-ttu-id="c72fc-133">但在不區分大小寫的土耳其文定序中，會系結 @i 至 @??,，而函式會傳回2。</span><span class="sxs-lookup"><span data-stu-id="c72fc-133">But in a case-insensitive Turkish collation, @i binds to @??, and the function returns 2.</span></span> <span data-ttu-id="c72fc-134">這在具有不同定序之執行個體之間移動的資料庫上可能會造成破壞。</span><span class="sxs-lookup"><span data-stu-id="c72fc-134">This can wreak havoc on a database that moves between instances with different collations.</span></span>  
  
## <a name="contained-databases"></a><span data-ttu-id="c72fc-135">自主資料庫</span><span class="sxs-lookup"><span data-stu-id="c72fc-135">Contained Databases</span></span>  
 <span data-ttu-id="c72fc-136">因為自主資料庫的設計目標是要讓它們各自獨立，所以必須切斷執行個體和 `tempdb` 定序的相依性。</span><span class="sxs-lookup"><span data-stu-id="c72fc-136">Since a design objective of contained databases is to make them self-contained, the dependence on the instance and `tempdb` collations must be severed.</span></span> <span data-ttu-id="c72fc-137">為了達到此目的，自主資料庫導入了目錄定序的概念。</span><span class="sxs-lookup"><span data-stu-id="c72fc-137">To do this, contained databases introduce the concept of the catalog collation.</span></span> <span data-ttu-id="c72fc-138">目錄定序會用於系統中繼資料和暫時性物件。</span><span class="sxs-lookup"><span data-stu-id="c72fc-138">The catalog collation is used for system metadata and transient objects.</span></span> <span data-ttu-id="c72fc-139">下面將提供詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c72fc-139">Details are provided below.</span></span>  
  
 <span data-ttu-id="c72fc-140">在自主資料庫中，目錄定序 **Latin1_General_100_CI_AS_WS_KS_SC**。</span><span class="sxs-lookup"><span data-stu-id="c72fc-140">In a contained database, the catalog collation **Latin1_General_100_CI_AS_WS_KS_SC**.</span></span> <span data-ttu-id="c72fc-141">對於所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上之所有自主資料庫而言，這個定序都相同，而且無法變更。</span><span class="sxs-lookup"><span data-stu-id="c72fc-141">This collation is the same for all contained databases on all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and cannot be changed.</span></span>  
  
 <span data-ttu-id="c72fc-142">雖然資料庫定序會保留下來，不過只當做使用者資料的預設定序使用。</span><span class="sxs-lookup"><span data-stu-id="c72fc-142">The database collation is retained, but is only used as the default collation for user data.</span></span> <span data-ttu-id="c72fc-143">根據預設，資料庫定序等於模型資料庫定序，但是使用者可透過或命令加以變更， `CREATE` `ALTER DATABASE` 就如同非自主資料庫一樣。</span><span class="sxs-lookup"><span data-stu-id="c72fc-143">By default, the database collation is equal to the model database collation, but can be changed by the user through a `CREATE` or `ALTER DATABASE` command as with non-contained databases.</span></span>  
  
 <span data-ttu-id="c72fc-144">`CATALOG_DEFAULT` 子句提供了新的關鍵字 `COLLATE`。</span><span class="sxs-lookup"><span data-stu-id="c72fc-144">A new keyword, `CATALOG_DEFAULT`, is available in the `COLLATE` clause.</span></span> <span data-ttu-id="c72fc-145">在包含和非自主資料庫中，這個關鍵字會當做中繼資料之目前定序的捷徑使用。</span><span class="sxs-lookup"><span data-stu-id="c72fc-145">This is used as a shortcut to the current collation of metadata in both contained and non-contained databases.</span></span> <span data-ttu-id="c72fc-146">也就是說，在非自主資料庫中，`CATALOG_DEFAULT` 將傳回目前資料庫定序，因為中繼資料已在資料庫定序中定序。</span><span class="sxs-lookup"><span data-stu-id="c72fc-146">That is, in a non-contained database, `CATALOG_DEFAULT` will return the current database collation, since metadata is collated in the database collation.</span></span> <span data-ttu-id="c72fc-147">在自主資料庫中，這兩個值可能會不同，因為使用者可以變更資料庫定序，讓它不符合目錄定序。</span><span class="sxs-lookup"><span data-stu-id="c72fc-147">In a contained database, these two values may be different, since the user can change the database collation so that it does not match the catalog collation.</span></span>  
  
 <span data-ttu-id="c72fc-148">下表將摘要說明包含和非自主資料庫中各種物件的行為：</span><span class="sxs-lookup"><span data-stu-id="c72fc-148">The behavior of various objects in both non-contained and contained databases is summarized in this table:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="c72fc-149">**Item**</span><span class="sxs-lookup"><span data-stu-id="c72fc-149">**Item**</span></span>|<span data-ttu-id="c72fc-150">**非自主資料庫**</span><span class="sxs-lookup"><span data-stu-id="c72fc-150">**Non-Contained Database**</span></span>|<span data-ttu-id="c72fc-151">**自主資料庫**</span><span class="sxs-lookup"><span data-stu-id="c72fc-151">**Contained Database**</span></span>|  
|<span data-ttu-id="c72fc-152">使用者資料 (預設值)</span><span class="sxs-lookup"><span data-stu-id="c72fc-152">User Data (default)</span></span>|<span data-ttu-id="c72fc-153">COLLATE</span><span class="sxs-lookup"><span data-stu-id="c72fc-153">DATABASE_DEFAULT</span></span>|<span data-ttu-id="c72fc-154">COLLATE</span><span class="sxs-lookup"><span data-stu-id="c72fc-154">DATABASE_DEFAULT</span></span>|  
|<span data-ttu-id="c72fc-155">暫存資料 (預設值)</span><span class="sxs-lookup"><span data-stu-id="c72fc-155">Temp Data (default)</span></span>|<span data-ttu-id="c72fc-156">TempDB 定序</span><span class="sxs-lookup"><span data-stu-id="c72fc-156">TempDB Collation</span></span>|<span data-ttu-id="c72fc-157">COLLATE</span><span class="sxs-lookup"><span data-stu-id="c72fc-157">DATABASE_DEFAULT</span></span>|  
|<span data-ttu-id="c72fc-158">中繼資料</span><span class="sxs-lookup"><span data-stu-id="c72fc-158">Metadata</span></span>|<span data-ttu-id="c72fc-159">DATABASE_DEFAULT / CATALOG_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="c72fc-159">DATABASE_DEFAULT / CATALOG_DEFAULT</span></span>|<span data-ttu-id="c72fc-160">COLLATE</span><span class="sxs-lookup"><span data-stu-id="c72fc-160">CATALOG_DEFAULT</span></span>|  
|<span data-ttu-id="c72fc-161">暫存中繼資料</span><span class="sxs-lookup"><span data-stu-id="c72fc-161">Temporary Metadata</span></span>|<span data-ttu-id="c72fc-162">TempDB 定序</span><span class="sxs-lookup"><span data-stu-id="c72fc-162">tempdb Collation</span></span>|<span data-ttu-id="c72fc-163">COLLATE</span><span class="sxs-lookup"><span data-stu-id="c72fc-163">CATALOG_DEFAULT</span></span>|  
|<span data-ttu-id="c72fc-164">變數</span><span class="sxs-lookup"><span data-stu-id="c72fc-164">Variables</span></span>|<span data-ttu-id="c72fc-165">執行個體定序</span><span class="sxs-lookup"><span data-stu-id="c72fc-165">Instance Collation</span></span>|<span data-ttu-id="c72fc-166">COLLATE</span><span class="sxs-lookup"><span data-stu-id="c72fc-166">CATALOG_DEFAULT</span></span>|  
|<span data-ttu-id="c72fc-167">Goto 標籤</span><span class="sxs-lookup"><span data-stu-id="c72fc-167">Goto Labels</span></span>|<span data-ttu-id="c72fc-168">執行個體定序</span><span class="sxs-lookup"><span data-stu-id="c72fc-168">Instance Collation</span></span>|<span data-ttu-id="c72fc-169">COLLATE</span><span class="sxs-lookup"><span data-stu-id="c72fc-169">CATALOG_DEFAULT</span></span>|  
|<span data-ttu-id="c72fc-170">資料指標名稱</span><span class="sxs-lookup"><span data-stu-id="c72fc-170">Cursor Names</span></span>|<span data-ttu-id="c72fc-171">執行個體定序</span><span class="sxs-lookup"><span data-stu-id="c72fc-171">Instance Collation</span></span>|<span data-ttu-id="c72fc-172">COLLATE</span><span class="sxs-lookup"><span data-stu-id="c72fc-172">CATALOG_DEFAULT</span></span>|  
  
 <span data-ttu-id="c72fc-173">在先前所描述的暫存資料表範例中，我們可以看見這個定序行為排除了在大部分暫存資料表中使用明確 `COLLATE` 子句的需求。</span><span class="sxs-lookup"><span data-stu-id="c72fc-173">If we temp table example previously described, we can see that this collation behavior eliminates the need for an explicit `COLLATE` clause in most temp table uses.</span></span> <span data-ttu-id="c72fc-174">在自主資料庫中，這段程式碼現在執行時不會發生錯誤，即使資料庫和執行個體定序不同也一樣：</span><span class="sxs-lookup"><span data-stu-id="c72fc-174">In a contained database, this code now runs without error, even if the database and instance collations differ:</span></span>  
  
```sql  
CREATE TABLE T1 (T1_txt nvarchar(max)) ;  
GO  
CREATE TABLE #T2 (T2_txt nvarchar(max));  
GO  
SELECT T1_txt, T2_txt  
FROM T1   
JOIN #T2   
    ON T1.T1_txt = #T2.T2_txt ;  
```  
  
 <span data-ttu-id="c72fc-175">這段程式碼會正常運作，因為 `T1_txt` 和 `T2_txt` 已在自主資料庫的資料庫定序中定序。</span><span class="sxs-lookup"><span data-stu-id="c72fc-175">This works because both `T1_txt` and `T2_txt` are collated in the database collation of the contained database.</span></span>  
  
## <a name="crossing-between-contained-and-uncontained-contexts"></a><span data-ttu-id="c72fc-176">跨越包含與未包含的內容</span><span class="sxs-lookup"><span data-stu-id="c72fc-176">Crossing Between Contained and Uncontained Contexts</span></span>  
 <span data-ttu-id="c72fc-177">只要自主資料庫中的工作階段維持包含狀態，它就必須保留在所連接的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="c72fc-177">As long as a session in a contained database remains contained, it must remain within the database to which it connected.</span></span> <span data-ttu-id="c72fc-178">在此情況下，其行為非常直接。</span><span class="sxs-lookup"><span data-stu-id="c72fc-178">In this case the behavior is very straightforward.</span></span> <span data-ttu-id="c72fc-179">但是，如果工作階段跨越包含與非包含的內容，其行為就會變得更複雜，因為您必須橋接這兩組規則。</span><span class="sxs-lookup"><span data-stu-id="c72fc-179">But if a session crosses between contained and non-contained contexts, the behavior becomes more complex, since the two sets of rules must be bridged.</span></span> <span data-ttu-id="c72fc-180">部分自主資料庫可能會發生這種情況，因為使用者可能會針對另一個資料庫執行 `USE`。</span><span class="sxs-lookup"><span data-stu-id="c72fc-180">This can happen in a partially-contained database, since a user may `USE` to another database.</span></span> <span data-ttu-id="c72fc-181">在此情況下，定序規則的差異是由下列原則處理。</span><span class="sxs-lookup"><span data-stu-id="c72fc-181">In this case, the difference in collation rules is handled by the following principle.</span></span>  
  
-   <span data-ttu-id="c72fc-182">批次的定序行為是由批次開始的資料庫所決定。</span><span class="sxs-lookup"><span data-stu-id="c72fc-182">The collation behavior for a batch is determined by the database in which the batch begins.</span></span>  
  
 <span data-ttu-id="c72fc-183">請注意，這項決定是在發出任何命令之前進行，包括初始 `USE`。</span><span class="sxs-lookup"><span data-stu-id="c72fc-183">Note that this decision is made before any commands are issued, including an initial `USE`.</span></span> <span data-ttu-id="c72fc-184">也就是說，如果批次在自主資料庫中開始，但是第一個命令是針對非自主資料庫執行 `USE`，包含的定序行為仍然會用於該批次。</span><span class="sxs-lookup"><span data-stu-id="c72fc-184">That is, if a batch begins in a contained database, but the first command is a `USE` to a non-contained database, the contained collation behavior will still be used for the batch.</span></span> <span data-ttu-id="c72fc-185">根據這點，變數的參考可能會產生多個可能的結果：</span><span class="sxs-lookup"><span data-stu-id="c72fc-185">Given this, a reference to a variable, for example, may have multiple possible outcomes:</span></span>  
  
-   <span data-ttu-id="c72fc-186">參考可能只會尋找一個符合項目。</span><span class="sxs-lookup"><span data-stu-id="c72fc-186">The reference may find exactly one match.</span></span> <span data-ttu-id="c72fc-187">在此情況下，參考運作時不會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c72fc-187">In this case, the reference will work without error.</span></span>  
  
-   <span data-ttu-id="c72fc-188">參考可能不會在先前存在符合項目的目前定序中尋找符合項目。</span><span class="sxs-lookup"><span data-stu-id="c72fc-188">The reference may not find a match in the current collation where there was one before.</span></span> <span data-ttu-id="c72fc-189">這會引發錯誤，表示變數不存在，即使顯然已建立變數也一樣。</span><span class="sxs-lookup"><span data-stu-id="c72fc-189">This will raise an error indicating that the variable does not exist, even though it was apparently created.</span></span>  
  
-   <span data-ttu-id="c72fc-190">參考可能會尋找原本不同的多個相符項目。</span><span class="sxs-lookup"><span data-stu-id="c72fc-190">The reference may find multiple matches that were originally distinct.</span></span> <span data-ttu-id="c72fc-191">這也會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="c72fc-191">This will also raise an error.</span></span>  
  
 <span data-ttu-id="c72fc-192">我們將使用一些範例來說明這點。</span><span class="sxs-lookup"><span data-stu-id="c72fc-192">We'll illustrate this with a few examples.</span></span> <span data-ttu-id="c72fc-193">在這些範例中，我們假設有一個名為 `MyCDB` 之部分自主資料庫，而且其資料庫定序設定為預設定序 **Latin1_General_100_CI_AS_WS_KS_SC**。</span><span class="sxs-lookup"><span data-stu-id="c72fc-193">For these we assume there is a partially-contained database named `MyCDB` with its database collation set to the default collation, **Latin1_General_100_CI_AS_WS_KS_SC**.</span></span> <span data-ttu-id="c72fc-194">此外，我們假設執行個體定序為 `Latin1_General_100_CS_AS_WS_KS_SC`。</span><span class="sxs-lookup"><span data-stu-id="c72fc-194">We assume that the instance collation is `Latin1_General_100_CS_AS_WS_KS_SC`.</span></span> <span data-ttu-id="c72fc-195">這兩個定序只有區分大小寫不同。</span><span class="sxs-lookup"><span data-stu-id="c72fc-195">The two collations differ only in case sensitivity.</span></span>  
  
### <a name="example-1"></a><span data-ttu-id="c72fc-196">範例 1</span><span class="sxs-lookup"><span data-stu-id="c72fc-196">Example 1</span></span>  
 <span data-ttu-id="c72fc-197">下列範例將說明參考只會尋找一個符合項目的案例。</span><span class="sxs-lookup"><span data-stu-id="c72fc-197">The following example illustrates the case where the reference finds exactly one match.</span></span>  
  
```  
USE MyCDB;  
GO  
  
CREATE TABLE #a(x int);  
INSERT INTO #a VALUES(1);  
GO  
  
USE master;  
GO  
  
SELECT * FROM #a;  
GO  
  
Results:  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
x  
-----------  
1  
```  
  
 <span data-ttu-id="c72fc-198">在此情況下，識別的 #a 會在不區分大小寫的目錄定序與區分大小寫的執行個體定序中繫結，而且程式碼正常運作。</span><span class="sxs-lookup"><span data-stu-id="c72fc-198">In this case, the identified #a binds in both the case-insensitive catalog collation and the case-sensitive instance collation, and the code works.</span></span>  
  
### <a name="example-2"></a><span data-ttu-id="c72fc-199">範例 2</span><span class="sxs-lookup"><span data-stu-id="c72fc-199">Example 2</span></span>  
 <span data-ttu-id="c72fc-200">下列範例將說明參考不會在先前存在符合項目的目前定序中尋找符合項目的案例。</span><span class="sxs-lookup"><span data-stu-id="c72fc-200">The following example illustrates the case where the reference does not find a match in the current collation where there was one before.</span></span>  
  
```  
USE MyCDB;  
GO  
  
CREATE TABLE #a(x int);  
INSERT INTO #A VALUES(1);  
GO  
```  
  
 <span data-ttu-id="c72fc-201">此處，#A 會繫結至不區分大小寫之預設定序中的 #a，而且插入作業正常運作。</span><span class="sxs-lookup"><span data-stu-id="c72fc-201">Here, the #A binds to #a in the case-insensitive default collation, and the insert works,</span></span>  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
(1 row(s) affected)  
```  
  
 <span data-ttu-id="c72fc-202">但是，如果我們繼續執行指令碼...</span><span class="sxs-lookup"><span data-stu-id="c72fc-202">But if we continue the script...</span></span>  
  
```  
USE master;  
GO  
  
SELECT * FROM #A;  
GO  
```  
  
 <span data-ttu-id="c72fc-203">當我們嘗試繫結至區分大小寫之執行個體定序中的 #A 時，就會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="c72fc-203">We get an error trying to bind to #A in the case-sensitive instance collation;</span></span>  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 <span data-ttu-id="c72fc-204">訊息 208，層級 16，狀態 0，行 2</span><span class="sxs-lookup"><span data-stu-id="c72fc-204">Msg 208, Level 16, State 0, Line 2</span></span>  
  
 <span data-ttu-id="c72fc-205">無效的物件名稱 '#A'。</span><span class="sxs-lookup"><span data-stu-id="c72fc-205">Invalid object name '#A'.</span></span>  
  
### <a name="example-3"></a><span data-ttu-id="c72fc-206">範例 3</span><span class="sxs-lookup"><span data-stu-id="c72fc-206">Example 3</span></span>  
 <span data-ttu-id="c72fc-207">下列範例將說明參考會尋找原本不同的多個相符項目的案例。</span><span class="sxs-lookup"><span data-stu-id="c72fc-207">The following example illustrates the case where the reference finds multiple matches that were originally distinct.</span></span> <span data-ttu-id="c72fc-208">首先，我們會在 (中開始， `tempdb` 其具有與實例) 相同的區分大小寫定序，並執行下列語句。</span><span class="sxs-lookup"><span data-stu-id="c72fc-208">First, we start in `tempdb` (which has the same case-sensitive collation as our instance) and execute the following statements.</span></span>  
  
```  
USE tempdb;  
GO  
  
CREATE TABLE #a(x int);  
GO  
CREATE TABLE #A(x int);  
GO  
INSERT INTO #a VALUES(1);  
GO  
INSERT INTO #A VALUES(2);  
GO  
```  
  
 <span data-ttu-id="c72fc-209">這個陳述式會成功執行，因為在此定序中，這些資料表各不相同：</span><span class="sxs-lookup"><span data-stu-id="c72fc-209">This succeeds, since the tables are distinct in this collation:</span></span>  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
(1 row(s) affected)  
(1 row(s) affected)  
```  
  
 <span data-ttu-id="c72fc-210">不過，如果我們移入自主資料庫，就會發現無法再繫結至這些資料表。</span><span class="sxs-lookup"><span data-stu-id="c72fc-210">If we move into our contained database, however, we find that we can no longer bind to these tables.</span></span>  
  
```  
USE MyCDB;  
GO  
SELECT * FROM #a;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 <span data-ttu-id="c72fc-211">訊息 12800，層級 16，狀態 1，行 2</span><span class="sxs-lookup"><span data-stu-id="c72fc-211">Msg 12800, Level 16, State 1, Line 2</span></span>  
  
 <span data-ttu-id="c72fc-212">暫存資料表名稱 '#a' 的參考模稜兩可，無法解析。</span><span class="sxs-lookup"><span data-stu-id="c72fc-212">The reference to temp table name '#a' is ambiguous and cannot be resolved.</span></span> <span data-ttu-id="c72fc-213">可能的候選方式為 '#a' 和 '#A'。</span><span class="sxs-lookup"><span data-stu-id="c72fc-213">Possible candidates are '#a' and '#A'.</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="c72fc-214">結論</span><span class="sxs-lookup"><span data-stu-id="c72fc-214">Conclusion</span></span>  
 <span data-ttu-id="c72fc-215">自主資料庫的定序行為與非自主資料庫稍有不同。</span><span class="sxs-lookup"><span data-stu-id="c72fc-215">The collation behavior of contained databases differs subtly from that in non-contained databases.</span></span> <span data-ttu-id="c72fc-216">這種行為通常很有用，可提供執行個體獨立性和簡單性。</span><span class="sxs-lookup"><span data-stu-id="c72fc-216">This behavior is generally beneficial, providing instance-independence and simplicity.</span></span> <span data-ttu-id="c72fc-217">但是，某些使用者可能會遇到問題，尤其是當工作階段同時存取包含和非自主資料庫時。</span><span class="sxs-lookup"><span data-stu-id="c72fc-217">Some users may have issues, particularly when a session accesses both contained and non-contained databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c72fc-218">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c72fc-218">See Also</span></span>  
 [<span data-ttu-id="c72fc-219">自主資料庫</span><span class="sxs-lookup"><span data-stu-id="c72fc-219">Contained Databases</span></span>](contained-databases.md)  
  
  
