---
title: 建立統計資料 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.statistics.propertis.f1
- sql12.swb.statistics.filter.f1
- sql12.swb.stat.properties.f1
- sql12.swb.stat.columns.f1
helpviewer_keywords:
- creating statistics
- statistics [SQL Server], creating
ms.assetid: 95a455fb-664d-4c95-851e-c6b62d7ebe04
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 230bd4d840c3d59dc1267dd6801754b68386cb32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599420"
---
# <a name="create-statistics"></a><span data-ttu-id="89e82-102">建立統計資料</span><span class="sxs-lookup"><span data-stu-id="89e82-102">Create Statistics</span></span>
  <span data-ttu-id="89e82-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中針對資料表或索引檢視表的一個或多個資料行建立查詢最佳化統計資料。</span><span class="sxs-lookup"><span data-stu-id="89e82-103">You can create query optimization statistics on one or more columns of a table or indexed view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="89e82-104">對於大部分查詢而言，查詢最佳化工具已經產生高品質查詢計畫的必要統計資料。不過，在少數情況下，您必須建立其他統計資料。</span><span class="sxs-lookup"><span data-stu-id="89e82-104">For most queries, the query optimizer already generates the necessary statistics for a high-quality query plan; in a few cases, you need to create additional statistics.</span></span>  
  
 <span data-ttu-id="89e82-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="89e82-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="89e82-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="89e82-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="89e82-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="89e82-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="89e82-108">安全性</span><span class="sxs-lookup"><span data-stu-id="89e82-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="89e82-109">**若要使用下列項目建立統計資料：**</span><span class="sxs-lookup"><span data-stu-id="89e82-109">**To create statistics, using:**</span></span>  
  
     [<span data-ttu-id="89e82-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="89e82-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="89e82-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="89e82-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="89e82-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="89e82-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="89e82-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="89e82-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="89e82-114">使用 CREATE STATISTICS 陳述式來建立統計資料之前，請確認 AUTO_CREATE_STATISTICS 選項是在資料庫層級設定。</span><span class="sxs-lookup"><span data-stu-id="89e82-114">Before creating statistics with the CREATE STATISTICS statement, verify that the AUTO_CREATE_STATISTICS option is set at the database level.</span></span> <span data-ttu-id="89e82-115">這將確保查詢最佳化工具能夠繼續例行地針對查詢述詞資料行建立單一資料行統計資料。</span><span class="sxs-lookup"><span data-stu-id="89e82-115">This will ensure that the query optimizer continues to routinely create single-column statistics for query predicate columns.</span></span>  
  
-   <span data-ttu-id="89e82-116">您最多可以針對每個統計資料物件列出 32 個資料行。</span><span class="sxs-lookup"><span data-stu-id="89e82-116">You can list up to 32 columns per statistics object.</span></span>  
  
-   <span data-ttu-id="89e82-117">您不能卸除、重新命名或變更在篩選統計資料述詞中定義的資料表資料行定義。</span><span class="sxs-lookup"><span data-stu-id="89e82-117">You cannot drop, rename, or alter the definition of a table column that is defined in a filtered statistics predicate.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="89e82-118">Security</span><span class="sxs-lookup"><span data-stu-id="89e82-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="89e82-119">權限</span><span class="sxs-lookup"><span data-stu-id="89e82-119">Permissions</span></span>  
 <span data-ttu-id="89e82-120">使用者必須是資料表或索引檢視表擁有者，或是下列其中一個角色的成員： **系統管理員** 固定伺服器角色、 **db_owner** 固定資料庫角色或 **db_ddladmin** 固定資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="89e82-120">Requires that the user be the table or indexed view owner, or a member of one of the following roles: **sysadmin** fixed server role, **db_owner** fixed database role, or the **db_ddladmin** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="89e82-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="89e82-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-statistics"></a><span data-ttu-id="89e82-122">若要建立統計資料</span><span class="sxs-lookup"><span data-stu-id="89e82-122">To create statistics</span></span>  
  
1.  <span data-ttu-id="89e82-123">在 **[物件總管]** 中，按一下加號展開要在其中建立新統計資料的資料庫。</span><span class="sxs-lookup"><span data-stu-id="89e82-123">In **Object Explorer**, click the plus sign to expand the database in which you want to create a new statistic.</span></span>  
  
2.  <span data-ttu-id="89e82-124">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="89e82-124">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="89e82-125">按一下加號展開要在其中建立新統計資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="89e82-125">Click the plus sign to expand the table in which you want to create a new statistic.</span></span>  
  
4.  <span data-ttu-id="89e82-126">以滑鼠右鍵按一下 [統計資料] 資料夾，然後選取 [新增統計資料…]。</span><span class="sxs-lookup"><span data-stu-id="89e82-126">Right-click the **Statistics** folder and select **New Statistics...**.</span></span>  
  
     <span data-ttu-id="89e82-127">下列屬性會在 [資料表_table_name_ **上的新統計資料**] 對話方塊的 [**一般**] 頁面上顯示。</span><span class="sxs-lookup"><span data-stu-id="89e82-127">The following properties show on the **General** page in the **New Statistics on Table**_table_name_ dialog box.</span></span>  
  
     <span data-ttu-id="89e82-128">**資料表名稱**</span><span class="sxs-lookup"><span data-stu-id="89e82-128">**Table Name**</span></span>  
     <span data-ttu-id="89e82-129">顯示統計資料所描述的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="89e82-129">Displays the name of the table described by the statistics.</span></span>  
  
     <span data-ttu-id="89e82-130">**統計資料名稱**</span><span class="sxs-lookup"><span data-stu-id="89e82-130">**Statistics Name**</span></span>  
     <span data-ttu-id="89e82-131">顯示儲存統計資料的資料庫物件名稱。</span><span class="sxs-lookup"><span data-stu-id="89e82-131">Displays the name of the database object where the statistics are stored.</span></span>  
  
     <span data-ttu-id="89e82-132">**統計資料行**</span><span class="sxs-lookup"><span data-stu-id="89e82-132">**Statistics Columns**</span></span>  
     <span data-ttu-id="89e82-133">此方格會顯示此組統計資料所描述的資料行。</span><span class="sxs-lookup"><span data-stu-id="89e82-133">This grid shows the columns described by this set of statistics.</span></span> <span data-ttu-id="89e82-134">方格中所有的值均為唯讀。</span><span class="sxs-lookup"><span data-stu-id="89e82-134">All values in the grid are read-only.</span></span>  
  
     <span data-ttu-id="89e82-135">**名稱**</span><span class="sxs-lookup"><span data-stu-id="89e82-135">**Name**</span></span>  
     <span data-ttu-id="89e82-136">顯示統計資料所描述的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="89e82-136">Displays the name of the column described by the statistics.</span></span> <span data-ttu-id="89e82-137">這可以是單一資料行，或單一資料表中的資料行組合。</span><span class="sxs-lookup"><span data-stu-id="89e82-137">This can be a single column or a combination of columns in a single table.</span></span>  
  
     <span data-ttu-id="89e82-138">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="89e82-138">**Data Type**</span></span>  
     <span data-ttu-id="89e82-139">指出統計資料所描述之資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="89e82-139">Indicates the data type of the columns described by the statistics.</span></span>  
  
     <span data-ttu-id="89e82-140">**大小**</span><span class="sxs-lookup"><span data-stu-id="89e82-140">**Size**</span></span>  
     <span data-ttu-id="89e82-141">顯示各個資料行的資料類型大小。</span><span class="sxs-lookup"><span data-stu-id="89e82-141">Displays the size of the data type for each column.</span></span>  
  
     <span data-ttu-id="89e82-142">**身分識別**</span><span class="sxs-lookup"><span data-stu-id="89e82-142">**Identity**</span></span>  
     <span data-ttu-id="89e82-143">勾選時表示為識別欄位。</span><span class="sxs-lookup"><span data-stu-id="89e82-143">Indicates an identity column when it is checked.</span></span>  
  
     <span data-ttu-id="89e82-144">**允許 Null**</span><span class="sxs-lookup"><span data-stu-id="89e82-144">**Allow Nulls**</span></span>  
     <span data-ttu-id="89e82-145">指出資料行是否接受 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="89e82-145">Indicates whether the column accepts NULL values.</span></span>  
  
     <span data-ttu-id="89e82-146">**加入**</span><span class="sxs-lookup"><span data-stu-id="89e82-146">**Add**</span></span>  
     <span data-ttu-id="89e82-147">將資料表的其他資料行加入統計資料方格。</span><span class="sxs-lookup"><span data-stu-id="89e82-147">Add additional columns from the table to the statistics grid.</span></span>  
  
     <span data-ttu-id="89e82-148">**移除**</span><span class="sxs-lookup"><span data-stu-id="89e82-148">**Remove**</span></span>  
     <span data-ttu-id="89e82-149">從統計資料方格中移除選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="89e82-149">Remove the selected column from the statistics grid.</span></span>  
  
     <span data-ttu-id="89e82-150">**上移**</span><span class="sxs-lookup"><span data-stu-id="89e82-150">**Move Up**</span></span>  
     <span data-ttu-id="89e82-151">將選取的資料行移動到統計資料方格中較前面的位置。</span><span class="sxs-lookup"><span data-stu-id="89e82-151">Move the selected column to an earlier location in the statistics grid.</span></span> <span data-ttu-id="89e82-152">方格中的位置，會大幅影響統計資料的效益。</span><span class="sxs-lookup"><span data-stu-id="89e82-152">The location in the grid can substantially impact the usefulness of the statistics.</span></span>  
  
     <span data-ttu-id="89e82-153">**下移**</span><span class="sxs-lookup"><span data-stu-id="89e82-153">**Move Down**</span></span>  
     <span data-ttu-id="89e82-154">將選取的資料行，移動到統計資料方格中較後面的位置。</span><span class="sxs-lookup"><span data-stu-id="89e82-154">Move the selected column to a later location in the statistics grid.</span></span>  
  
     <span data-ttu-id="89e82-155">**上次更新這些資料行的統計資料：**</span><span class="sxs-lookup"><span data-stu-id="89e82-155">**Statistics for these columns were last updated:**</span></span>  
     <span data-ttu-id="89e82-156">指出統計資料有多舊。</span><span class="sxs-lookup"><span data-stu-id="89e82-156">Indicates how old the statistics are.</span></span> <span data-ttu-id="89e82-157">愈新的統計資料愈有價值。</span><span class="sxs-lookup"><span data-stu-id="89e82-157">Statistics are more valuable when they are current.</span></span> <span data-ttu-id="89e82-158">在資料大量變更後，或加入非典型資料後，更新統計資料。</span><span class="sxs-lookup"><span data-stu-id="89e82-158">Update statistics after large changes to the data or after adding atypical data.</span></span> <span data-ttu-id="89e82-159">資料的分佈較為一致的資料表統計資料，就不需要經常地更新。</span><span class="sxs-lookup"><span data-stu-id="89e82-159">Statistics for tables that have a consistent distribution of data need to be updated less frequently.</span></span>  
  
     <span data-ttu-id="89e82-160">**更新這些資料行的統計資料**</span><span class="sxs-lookup"><span data-stu-id="89e82-160">**Update statistics for these columns**</span></span>  
     <span data-ttu-id="89e82-161">勾選即可在對話方塊關閉時更新統計資料。</span><span class="sxs-lookup"><span data-stu-id="89e82-161">Check to update the statistics when the dialog box is closed.</span></span>  
  
     <span data-ttu-id="89e82-162">下列屬性會在 [資料表_table_name_ **上的新統計資料**] 對話方塊中的 [**篩選**] 頁面上顯示。</span><span class="sxs-lookup"><span data-stu-id="89e82-162">The following property shows on the **Filter** page in the **New Statistics on Table**_table_name_ dialog box.</span></span>  
  
     <span data-ttu-id="89e82-163">**篩選運算式**</span><span class="sxs-lookup"><span data-stu-id="89e82-163">**Filter Expression**</span></span>  
     <span data-ttu-id="89e82-164">定義要在篩選統計資料中包含什麼資料列。</span><span class="sxs-lookup"><span data-stu-id="89e82-164">Defines which data rows to include in the filtered statistics.</span></span> <span data-ttu-id="89e82-165">例如， `Production.ProductSubcategoryID IN ( 1,2,3 )`</span><span class="sxs-lookup"><span data-stu-id="89e82-165">For example, `Production.ProductSubcategoryID IN ( 1,2,3 )`</span></span>  
  
5.  <span data-ttu-id="89e82-166">在 [**資料表 table_name 的新統計資料**_ _ ] 對話方塊的 [**一般**] 頁面上，按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="89e82-166">In the **New Statistics on Table**_table_name_ dialog box, on the **General** page, click **Add**.</span></span>  
  
     <span data-ttu-id="89e82-167">下列屬性會在 **[選取資料行]** 對話方塊中顯示。</span><span class="sxs-lookup"><span data-stu-id="89e82-167">The following properties show in the **Select Columns** dialog box.</span></span> <span data-ttu-id="89e82-168">此資訊是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="89e82-168">This information is read-only.</span></span>  
  
     <span data-ttu-id="89e82-169">**名稱**</span><span class="sxs-lookup"><span data-stu-id="89e82-169">**Name**</span></span>  
     <span data-ttu-id="89e82-170">顯示統計資料所描述的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="89e82-170">Displays the name of the column described by the statistics.</span></span> <span data-ttu-id="89e82-171">這可以是單一資料行，或單一資料表中的資料行組合。</span><span class="sxs-lookup"><span data-stu-id="89e82-171">This can be a single column or a combination of columns in a single table.</span></span>  
  
     <span data-ttu-id="89e82-172">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="89e82-172">**Data Type**</span></span>  
     <span data-ttu-id="89e82-173">指出統計資料所描述之資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="89e82-173">Indicates the data type of the columns described by the statistics.</span></span>  
  
     <span data-ttu-id="89e82-174">**大小**</span><span class="sxs-lookup"><span data-stu-id="89e82-174">**Size**</span></span>  
     <span data-ttu-id="89e82-175">顯示各個資料行的資料類型大小。</span><span class="sxs-lookup"><span data-stu-id="89e82-175">Displays the size of the data type for each column.</span></span>  
  
     <span data-ttu-id="89e82-176">**身分識別**</span><span class="sxs-lookup"><span data-stu-id="89e82-176">**Identity**</span></span>  
     <span data-ttu-id="89e82-177">勾選時表示為識別欄位。</span><span class="sxs-lookup"><span data-stu-id="89e82-177">Indicates an identity column when checked.</span></span>  
  
     <span data-ttu-id="89e82-178">**允許 NULL**</span><span class="sxs-lookup"><span data-stu-id="89e82-178">**Allow NULLs**</span></span>  
     <span data-ttu-id="89e82-179">指出資料行是否接受 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="89e82-179">Indicates whether the column accepts NULL values.</span></span>  
  
6.  <span data-ttu-id="89e82-180">在 **[選取資料行]** 對話方塊中，選取要為其建立統計資料的每個資料行的核取方塊，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="89e82-180">In the **Select Columns** dialog box, select the check box or check boxes of each column for which you want to create a statistic and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="89e82-181">在 [**資料表 table_name 的新統計資料**_ _ ] 對話方塊中，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="89e82-181">In the **New Statistics on Table**_table_name_ dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="89e82-182">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="89e82-182">Using Transact-SQL</span></span>  
  
#### <a name="to-create-statistics"></a><span data-ttu-id="89e82-183">若要建立統計資料</span><span class="sxs-lookup"><span data-stu-id="89e82-183">To create statistics</span></span>  
  
1.  <span data-ttu-id="89e82-184">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="89e82-184">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="89e82-185">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="89e82-185">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="89e82-186">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="89e82-186">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- Create new statistic object called ContactMail1  
    -- on the BusinessEntityID and EmailPromotion columns in the Person.Person table.   
  
    CREATE STATISTICS ContactMail1  
        ON Person.Person (BusinessEntityID, EmailPromotion);   
    GO  
    ```  
  
4.  <span data-ttu-id="89e82-187">以上建立的統計資訊可能會改進下列查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="89e82-187">The statistic created above potentially improves the results for the following query.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT LastName, FirstName  
    FROM Person.Person  
    WHERE EmailPromotion = 2  
    ORDER BY LastName, FirstName;   
    GO  
    ```  
  
 <span data-ttu-id="89e82-188">如需詳細資訊，請參閱 [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="89e82-188">For more information, see [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).</span></span>  
  
  
