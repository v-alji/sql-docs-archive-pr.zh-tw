---
title: 資料表資料行屬性 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65558
- vdtsql.chm:69657
- vdt.ppg.columns
ms.assetid: 09830897-cc10-46b8-95f5-e0e9681b668c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1894b074491af1962d2180337288e188d41b2951
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607329"
---
# <a name="table-column-properties-sql-server-management-studio"></a><span data-ttu-id="ffeee-102">資料表資料行屬性 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="ffeee-102">Table Column Properties (SQL Server Management Studio)</span></span>
  <span data-ttu-id="ffeee-103">這些屬性會出現在 [資料表設計工具] 的下方窗格中。</span><span class="sxs-lookup"><span data-stu-id="ffeee-103">These properties appear in the bottom pane of Table Designer.</span></span> <span data-ttu-id="ffeee-104">已選取資料行時，您可以在 [屬性] 視窗中編輯這些屬性 (除非另有附註)。</span><span class="sxs-lookup"><span data-stu-id="ffeee-104">Unless otherwise noted, you can edit these properties in the Properties window when the column is selected.</span></span> <span data-ttu-id="ffeee-105">可依類別目錄或依字母順序顯示 **[資料行屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="ffeee-105">The **Column Properties** can be displayed in categories or alphabetically.</span></span> <span data-ttu-id="ffeee-106">且只會出現或只可變更特定資料類型的一些屬性。</span><span class="sxs-lookup"><span data-stu-id="ffeee-106">Many properties only appear or can only be changed for certain data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ffeee-107">如果已發行要複寫的資料表，則必須使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理物件 (SMO) 來進行結構描述變更。</span><span class="sxs-lookup"><span data-stu-id="ffeee-107">If the table is published for replication, you must make schema changes using the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).</span></span> <span data-ttu-id="ffeee-108">使用 [資料表設計工具] 或 [資料庫圖表設計工具] 變更結構描述時，會嘗試卸除並重新建立資料表。</span><span class="sxs-lookup"><span data-stu-id="ffeee-108">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="ffeee-109">您無法卸除已發行的物件，因此結構描述變更將會失敗。</span><span class="sxs-lookup"><span data-stu-id="ffeee-109">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
 <span data-ttu-id="ffeee-110">**一般**</span><span class="sxs-lookup"><span data-stu-id="ffeee-110">**General**</span></span>  
 <span data-ttu-id="ffeee-111">展開以顯示 [名稱]  、[允許 Null]  、[資料類型]  、[預設值或繫結]  、[長度]  、[有效位數]  和 [小數位數]  。</span><span class="sxs-lookup"><span data-stu-id="ffeee-111">Expands to show **Name**, **Allow Nulls**, **Data Type**, **Default Value or Binding**, **Length**, **Precision**, and **Scale**.</span></span>  
  
 <span data-ttu-id="ffeee-112">**名稱**</span><span class="sxs-lookup"><span data-stu-id="ffeee-112">**Name**</span></span>  
 <span data-ttu-id="ffeee-113">顯示所選取資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="ffeee-113">Displays the name of the selected column.</span></span>  
  
 <span data-ttu-id="ffeee-114">**允許 Null**</span><span class="sxs-lookup"><span data-stu-id="ffeee-114">**Allow Nulls**</span></span>  
 <span data-ttu-id="ffeee-115">指示這個資料行是否允許 Null。</span><span class="sxs-lookup"><span data-stu-id="ffeee-115">Indicates whether this column allows nulls.</span></span> <span data-ttu-id="ffeee-116">若要編輯這個屬性，請按一下 [資料表設計工具] 上方窗格中對應此資料行的 [允許 Null] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ffeee-116">To edit this property, click the Allow Nulls checkbox corresponding to the column in the top pane of Table Designer.</span></span>  
  
 <span data-ttu-id="ffeee-117">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="ffeee-117">**Data Type**</span></span>  
 <span data-ttu-id="ffeee-118">顯示選定資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ffeee-118">Displays the data type for the selected column.</span></span> <span data-ttu-id="ffeee-119">若要編輯這個屬性，請按一下該屬性的值，並展開下拉式清單，然後選擇另一個值。</span><span class="sxs-lookup"><span data-stu-id="ffeee-119">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="ffeee-120">**預設值或繫結**</span><span class="sxs-lookup"><span data-stu-id="ffeee-120">**Default Value or Binding**</span></span>  
 <span data-ttu-id="ffeee-121">顯示沒有為此資料行指定任何值時，此資料行的預設值為何。</span><span class="sxs-lookup"><span data-stu-id="ffeee-121">Displays the default for this column whenever no value is specified for this column.</span></span> <span data-ttu-id="ffeee-122">這個欄位的值可以是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預設條件約束的值，或是資料行所繫結的全域條件約束名稱。</span><span class="sxs-lookup"><span data-stu-id="ffeee-122">The value of this field can be either the value of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] default constraint or the name of a global constraint to which the column is bound.</span></span> <span data-ttu-id="ffeee-123">下拉式清單包含資料庫中定義的所有全域預設值。</span><span class="sxs-lookup"><span data-stu-id="ffeee-123">The drop-down list contains all global defaults defined in the database.</span></span> <span data-ttu-id="ffeee-124">若要將資料行繫結到全域預設值，請從下拉式清單中選取。</span><span class="sxs-lookup"><span data-stu-id="ffeee-124">To bind the column to a global default, select from the drop-down list.</span></span> <span data-ttu-id="ffeee-125">此外，若要為資料行建立預設條件約束，請直接將預設值當作文字輸入。</span><span class="sxs-lookup"><span data-stu-id="ffeee-125">Alternatively, to create a default constraint for the column, type the default value directly as text.</span></span>  
  
 <span data-ttu-id="ffeee-126">**長度**</span><span class="sxs-lookup"><span data-stu-id="ffeee-126">**Length**</span></span>  
 <span data-ttu-id="ffeee-127">顯示以字元為基礎的資料類型所允許的字元數。</span><span class="sxs-lookup"><span data-stu-id="ffeee-127">Shows the number of characters allowed for character-based data types.</span></span> <span data-ttu-id="ffeee-128">這個屬性只適用於以字元為主的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ffeee-128">This property is only available for character-based data types</span></span>  
  
 <span data-ttu-id="ffeee-129">**調整**</span><span class="sxs-lookup"><span data-stu-id="ffeee-129">**Scale**</span></span>  
 <span data-ttu-id="ffeee-130">顯示這個資料行數值的小數點右邊可以出現的位數上限。</span><span class="sxs-lookup"><span data-stu-id="ffeee-130">Displays the maximum number of digits that can appear to the right of the decimal point for values of this column.</span></span> <span data-ttu-id="ffeee-131">這個屬性會顯示 **0** 來表示非數字的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ffeee-131">This property shows **0** for nonnumeric data types.</span></span>  
  
 <span data-ttu-id="ffeee-132">**有效位數**</span><span class="sxs-lookup"><span data-stu-id="ffeee-132">**Precision**</span></span>  
 <span data-ttu-id="ffeee-133">顯示這個資料行中數值的最大位數。</span><span class="sxs-lookup"><span data-stu-id="ffeee-133">Displays the maximum number of digits for values in this column.</span></span> <span data-ttu-id="ffeee-134">這個屬性會顯示 **0** 來表示非數字的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ffeee-134">This property shows **0** for nonnumeric data types.</span></span>  
  
 <span data-ttu-id="ffeee-135">**資料表設計工具**</span><span class="sxs-lookup"><span data-stu-id="ffeee-135">**Table Designer**</span></span>  
 <span data-ttu-id="ffeee-136">展開 [資料表設計工具]  區段。</span><span class="sxs-lookup"><span data-stu-id="ffeee-136">Expands the **Table Designer** section.</span></span>  
  
 <span data-ttu-id="ffeee-137">**定序**</span><span class="sxs-lookup"><span data-stu-id="ffeee-137">**Collation**</span></span>  
 <span data-ttu-id="ffeee-138">當資料行的值用來排序查詢結果的資料列時，顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預設會套用至資料行的定序序列。</span><span class="sxs-lookup"><span data-stu-id="ffeee-138">Displays the collating sequence that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applies by default to the column whenever the column values are used to sort rows of a query result.</span></span> <span data-ttu-id="ffeee-139">若要編輯定序，請選取屬性，並按一下屬性值右邊的省略符號 (...) 以開啟 [定序]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ffeee-139">To edit the collation, select the property, click the ellipsis (   ) that appears to the right of the property value to bring up the **Collation** dialog box.</span></span>  
  
 <span data-ttu-id="ffeee-140">**計算資料行規格**</span><span class="sxs-lookup"><span data-stu-id="ffeee-140">**Computed Column Specification**</span></span>  
 <span data-ttu-id="ffeee-141">顯示計算資料行的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ffeee-141">Displays information about a computed column.</span></span> <span data-ttu-id="ffeee-142">顯示的屬性值與 [公式]  子屬性的值相同，且會顯示計算資料行的公式。</span><span class="sxs-lookup"><span data-stu-id="ffeee-142">The value shown for property is the same as the value of the **Formula** child property and displays the formula for the computed column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ffeee-143">若要變更 [計算資料行規格]  屬性顯示的值，您必須將它展開並編輯 [公式]  子屬性。</span><span class="sxs-lookup"><span data-stu-id="ffeee-143">To change the value shown for the **Computed Column Specification** property, you must expand it and edit the **Formula** child property.</span></span>  
  
-   <span data-ttu-id="ffeee-144">[公式]  ：顯示計算資料行的公式。</span><span class="sxs-lookup"><span data-stu-id="ffeee-144">**Formula** Displays the formula for the computed column.</span></span> <span data-ttu-id="ffeee-145">若要編輯這個屬性，請直接輸入新公式。</span><span class="sxs-lookup"><span data-stu-id="ffeee-145">To edit this property, type a new formula directly.</span></span>  
  
-   <span data-ttu-id="ffeee-146">[]  ：指示是否已儲存公式的結果。</span><span class="sxs-lookup"><span data-stu-id="ffeee-146">**Is Persisted** Indicates whether the results of the formula are stored.</span></span> <span data-ttu-id="ffeee-147">如果這個屬性設定為 [否]  ，則只會儲存公式，而且會在每次參考這個資料行時計算這些值。</span><span class="sxs-lookup"><span data-stu-id="ffeee-147">If this property is set to **No** then only the formula is stored and the values are calculated every time this column is referenced.</span></span> <span data-ttu-id="ffeee-148">若要編輯這個屬性，請按一下該屬性的值，並展開下拉式清單，然後選擇另一個值。</span><span class="sxs-lookup"><span data-stu-id="ffeee-148">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="ffeee-149">如需詳細資訊，請參閱 [Specify Computed Columns in a Table](../tables/specify-computed-columns-in-a-table.md)。</span><span class="sxs-lookup"><span data-stu-id="ffeee-149">For more information, see [Specify Computed Columns in a Table](../tables/specify-computed-columns-in-a-table.md).</span></span>  
  
 <span data-ttu-id="ffeee-150">**資料類型扼要**</span><span class="sxs-lookup"><span data-stu-id="ffeee-150">**Condensed Data Type**</span></span>  
 <span data-ttu-id="ffeee-151">顯示欄位的資料類型資訊，使用與 SQL CREATE TABLE 陳述式相同的格式。</span><span class="sxs-lookup"><span data-stu-id="ffeee-151">Displays information about the field's data type, in the same format as the SQL CREATE TABLE statement.</span></span> <span data-ttu-id="ffeee-152">例如，包含可變長度字串的欄位，若長度最大可為 20 個字元，則可以表示為 "varchar(20)"。</span><span class="sxs-lookup"><span data-stu-id="ffeee-152">For example, a field containing a variable-length string with a maximum length of 20 characters would be represented as "varchar(20)".</span></span> <span data-ttu-id="ffeee-153">若要變更這個屬性，請直接輸入屬性值。</span><span class="sxs-lookup"><span data-stu-id="ffeee-153">To change this property, type the value directly.</span></span>  
  
 <span data-ttu-id="ffeee-154">**說明**</span><span class="sxs-lookup"><span data-stu-id="ffeee-154">**Description**</span></span>  
 <span data-ttu-id="ffeee-155">顯示描述這個資料行的文字。</span><span class="sxs-lookup"><span data-stu-id="ffeee-155">Displays text describing this column.</span></span> <span data-ttu-id="ffeee-156">若要編輯描述，請選取屬性，按一下屬性值右邊的省略符號 (...)，然後在 [描述屬性]  對話方塊中編輯描述。</span><span class="sxs-lookup"><span data-stu-id="ffeee-156">To edit the description, select the property, click the ellipsis (   ) that appears to the right of the property value and edit the description in the **Description Property** dialog box.</span></span>  
  
 <span data-ttu-id="ffeee-157">**具決定性**</span><span class="sxs-lookup"><span data-stu-id="ffeee-157">**Deterministic**</span></span>  
 <span data-ttu-id="ffeee-158">顯示是否可以確定地決定選取之資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ffeee-158">Shows whether the data type of the selected column can be determined with certainty.</span></span>  
  
 <span data-ttu-id="ffeee-159">**以 DTS 發行**</span><span class="sxs-lookup"><span data-stu-id="ffeee-159">**DTS-published**</span></span>  
 <span data-ttu-id="ffeee-160">顯示資料行是否為以 DTS 發行。</span><span class="sxs-lookup"><span data-stu-id="ffeee-160">Shows whether the column is DTS-published.</span></span>  
  
 <span data-ttu-id="ffeee-161">**全文檢索規格**</span><span class="sxs-lookup"><span data-stu-id="ffeee-161">**Full-text Specification**</span></span>  
 <span data-ttu-id="ffeee-162">顯示全文檢索索引的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ffeee-162">Displays information about a full-text index.</span></span> <span data-ttu-id="ffeee-163">這個屬性的值是 [已全文檢索索引]\*\*\*\* 子屬性的值，並且指出這個資料行是否已全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="ffeee-163">The value of this property is the value of the **Is Full-text Indexed** child property and indicates whether this column is full-text indexed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ffeee-164">若要變更 [全文檢索規格]\*\*\*\* 屬性顯示的值，您必須將它展開並編輯 [已全文檢索索引]\*\*\*\* 子屬性。</span><span class="sxs-lookup"><span data-stu-id="ffeee-164">To change the value shown for the **Full-text Specification** property, you must expand it and edit the **Is Full-text Indexed** child property.</span></span>  
  
-   <span data-ttu-id="ffeee-165">**已全文檢索索引** ：指出這個資料行是否已全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="ffeee-165">**Is Full-text Indexed** Indicates whether this column is full-text indexed.</span></span> <span data-ttu-id="ffeee-166">只有在此資料行的資料類型能以全文檢索搜尋，以及此資料行所屬的資料表具有為其指定的全文檢索索引時，才能將這個屬性設定為 [是]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ffeee-166">This property can be set to **Yes** only if the data type for this column is full-text searchable and if the table to which this column belongs has a full-text index specified for it.</span></span> <span data-ttu-id="ffeee-167">若要編輯這個屬性，請按一下屬性的值、展開下拉式清單，然後選擇一個值。</span><span class="sxs-lookup"><span data-stu-id="ffeee-167">To edit this property, click its value, expand the drop-down list, and choose a value.</span></span>  
  
-   <span data-ttu-id="ffeee-168">**全文檢索型別資料行：** 顯示執行這個資料行的全文檢索索引所依據的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="ffeee-168">**Full-text Type Column** Displays the name of the column on which this column is full-text indexed.</span></span> <span data-ttu-id="ffeee-169">如果這個資料行的 [資料類型] \*\*\*\* 屬性為 image \*\*\*\* 或 varbinary \*\*\*\*，則必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="ffeee-169">This property must be set if the **Datatype** property for this column is either **image** or **varbinary**.</span></span> <span data-ttu-id="ffeee-170">在這個屬性中命名的資料行必須為 **[n]char、[n]varchar** 或 **xml**類型，且這個屬性的下拉式清單中包含的資料行只能是這三種資料類型中的其中一種。</span><span class="sxs-lookup"><span data-stu-id="ffeee-170">The column named in this property must be of type **[n]char, [n]varchar,** or **xml**, and the drop-down list for this property contains only columns that have one of these three data types.</span></span> <span data-ttu-id="ffeee-171">這個屬性所命名的資料行中的資料列，會指示可全文檢索搜尋的資料行中對應資料列的文件類型。</span><span class="sxs-lookup"><span data-stu-id="ffeee-171">Rows in the column named by this property indicate the document type of the corresponding rows in the full-text-searchable column.</span></span> <span data-ttu-id="ffeee-172">若要編輯這個屬性，請按一下該屬性的值，並展開下拉式清單，然後選擇另一個值。</span><span class="sxs-lookup"><span data-stu-id="ffeee-172">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
-   <span data-ttu-id="ffeee-173">[語言]\*\*\*\* ：指示用來索引資料行的文字分隔語言。</span><span class="sxs-lookup"><span data-stu-id="ffeee-173">**Language** Indicates the language of the word breaker used to index the column.</span></span> <span data-ttu-id="ffeee-174">屬性中儲存的值實際上是文字分隔的地區設定識別碼。</span><span class="sxs-lookup"><span data-stu-id="ffeee-174">The value stored in the property is actually the locale identifier for the word breaker.</span></span> <span data-ttu-id="ffeee-175">如需有關文字分隔和 LCID 的詳細資訊，請參閱＜文字分隔與字幹分析器＞(Word Breakers and Stemmers)。</span><span class="sxs-lookup"><span data-stu-id="ffeee-175">For more information about word breakers and LCIDs, see Word Breakers and Stemmers.</span></span> <span data-ttu-id="ffeee-176">若要編輯這個屬性，請按一下該屬性的值，並展開下拉式清單，然後選擇另一個值。</span><span class="sxs-lookup"><span data-stu-id="ffeee-176">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="ffeee-177">**統計語意**</span><span class="sxs-lookup"><span data-stu-id="ffeee-177">**Statistical Semantics**</span></span>  
 <span data-ttu-id="ffeee-178">選取是否要針對選取的資料行啟用統計語意索引。</span><span class="sxs-lookup"><span data-stu-id="ffeee-178">Select whether to enable statistical semantic indexing for the selected column.</span></span> <span data-ttu-id="ffeee-179">如需詳細資訊，請參閱[語意搜尋 &#40;SQL Server&#41;](../search/semantic-search-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ffeee-179">For more information, see [Semantic Search &#40;SQL Server&#41;](../search/semantic-search-sql-server.md).</span></span>  
  
 <span data-ttu-id="ffeee-180">如果您在選取 **[統計語意]** 之前選取 **[語言]**，而且選取的語言沒有相關聯的語意語言模型，則 **[統計語意]** 選項會設定為 **[否]** ，而且無法修改。</span><span class="sxs-lookup"><span data-stu-id="ffeee-180">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** option is set to **No** and cannot be modified.</span></span> <span data-ttu-id="ffeee-181">如果您在選取 **[語言]** 之前針對 **[統計語意]** 選項選取 **[是]**，則 **[語言]** 欄中的可用語言將受限為有語意語言模型支援的語言。</span><span class="sxs-lookup"><span data-stu-id="ffeee-181">If you select **Yes** for the **Statistical Semantics** option prior to selecting a **Language**, then the languages available in the **Language** column will be restricted to those for which there is Semantic Language Model support.</span></span>  
  
 <span data-ttu-id="ffeee-182">**有非 SQL Server 訂閱者**</span><span class="sxs-lookup"><span data-stu-id="ffeee-182">**Has Non-SQL Server Subscriber**</span></span>  
 <span data-ttu-id="ffeee-183">指出是否正在將資料行複寫至不是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="ffeee-183">Indicates if the column is being replicated to a subscriber that is not a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="ffeee-184">**識別規格**</span><span class="sxs-lookup"><span data-stu-id="ffeee-184">**Identity Specification**</span></span>  
 <span data-ttu-id="ffeee-185">顯示這個資料行的數值是否強制使用唯一性，以及強制執行方式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ffeee-185">Displays information about whether and how this column enforces uniqueness on its values.</span></span> <span data-ttu-id="ffeee-186">這個屬性的值指示這個資料行是否為識別欄位，以及是否與 [為識別] \*\*\*\* 子屬性的值相同。</span><span class="sxs-lookup"><span data-stu-id="ffeee-186">The value of this property indicates whether or not this column is an identity column and is the same as the value of the child property **Is Identity**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ffeee-187"> 若要變更 [識別規格]\ \*\*\** 屬性顯示的值，您必須將它展開並編輯 [為識別]\ \*\*\** 子屬性。</span><span class="sxs-lookup"><span data-stu-id="ffeee-187">To change the value shown for the **Identity Specification** property, you must expand it and edit the **Is Identity** child property.</span></span>  
  
-   <span data-ttu-id="ffeee-188">[為識別]\*\*\*\* ：指示這個資料行是否為識別欄位。</span><span class="sxs-lookup"><span data-stu-id="ffeee-188">**Is Identity** Indicates whether or not this column is an identity column.</span></span> <span data-ttu-id="ffeee-189">若要編輯這個屬性，請按一下該屬性的值，並展開下拉式清單，然後選擇另一個值。</span><span class="sxs-lookup"><span data-stu-id="ffeee-189">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
-   <span data-ttu-id="ffeee-190">[識別值種子]\*\*\*\* ：顯示建立此識別欄位期間指定的種子值。</span><span class="sxs-lookup"><span data-stu-id="ffeee-190">**Identity Seed** Displays the seed value specified during the creation of this identity column.</span></span> <span data-ttu-id="ffeee-191">這個值會指派至資料表的第一個資料列。</span><span class="sxs-lookup"><span data-stu-id="ffeee-191">This value is assigned to the first row in the table.</span></span> <span data-ttu-id="ffeee-192">如果將這個資料格保留空白，則預設會指派值 1。</span><span class="sxs-lookup"><span data-stu-id="ffeee-192">If you leave this cell blank, the value 1 will be assigned by default.</span></span> <span data-ttu-id="ffeee-193">若要編輯這個屬性，請直接輸入新值。</span><span class="sxs-lookup"><span data-stu-id="ffeee-193">To edit this property, type the new value directly.</span></span>  
  
-   <span data-ttu-id="ffeee-194">[識別值增量]\*\*\*\* ：顯示建立此識別欄位期間指定的遞增值。</span><span class="sxs-lookup"><span data-stu-id="ffeee-194">**Identity Increment** Displays the increment value specified during the creation of this identity column.</span></span> <span data-ttu-id="ffeee-195">系統會將後續每一個資料列的「 **識別值種子** 」加入這個增量值。</span><span class="sxs-lookup"><span data-stu-id="ffeee-195">This value is the increment that will be added to the **Identity Seed** for each subsequent row.</span></span> <span data-ttu-id="ffeee-196">如果將這個資料格保留空白，則預設會指派值 1。</span><span class="sxs-lookup"><span data-stu-id="ffeee-196">If you leave this cell blank, the value 1 will be assigned by default.</span></span> <span data-ttu-id="ffeee-197">若要編輯這個屬性，請直接輸入新值。</span><span class="sxs-lookup"><span data-stu-id="ffeee-197">To edit this property, type the new value directly.</span></span>  
  
 <span data-ttu-id="ffeee-198">**可索引的**</span><span class="sxs-lookup"><span data-stu-id="ffeee-198">**Indexable**</span></span>  
 <span data-ttu-id="ffeee-199">顯示選取的資料行是否可以建立索引。</span><span class="sxs-lookup"><span data-stu-id="ffeee-199">Shows whether the selected column can be indexed.</span></span> <span data-ttu-id="ffeee-200">例如，不具決定性之計算的資料行不可以建立索引。</span><span class="sxs-lookup"><span data-stu-id="ffeee-200">For example, non-deterministic computed columns cannot be indexed.</span></span>  
  
 <span data-ttu-id="ffeee-201">**合併發行**</span><span class="sxs-lookup"><span data-stu-id="ffeee-201">**Merge-published**</span></span>  
 <span data-ttu-id="ffeee-202">顯示資料行是否為合併發行。</span><span class="sxs-lookup"><span data-stu-id="ffeee-202">Shows whether the column is merge-published.</span></span>  
  
 <span data-ttu-id="ffeee-203">**Not For Replication**</span><span class="sxs-lookup"><span data-stu-id="ffeee-203">**Not For Replication**</span></span>  
 <span data-ttu-id="ffeee-204">指出在複寫期間是否保留原始識別值。</span><span class="sxs-lookup"><span data-stu-id="ffeee-204">Indicates whether original identity values are preserved during replication.</span></span> <span data-ttu-id="ffeee-205">如需複製的詳細資訊，請參閱 CREATE TABLE。</span><span class="sxs-lookup"><span data-stu-id="ffeee-205">For more information on replication see CREATE TABLE.</span></span> <span data-ttu-id="ffeee-206">若要編輯這個屬性，請按一下該屬性的值，並展開下拉式清單，然後選擇另一個值。</span><span class="sxs-lookup"><span data-stu-id="ffeee-206">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="ffeee-207">**已複寫**</span><span class="sxs-lookup"><span data-stu-id="ffeee-207">**Replicated**</span></span>  
 <span data-ttu-id="ffeee-208">顯示此資料行是否在其他位置已複寫。</span><span class="sxs-lookup"><span data-stu-id="ffeee-208">Shows whether this column is replicated in another location.</span></span>  
  
 <span data-ttu-id="ffeee-209">**RowGuid**</span><span class="sxs-lookup"><span data-stu-id="ffeee-209">**RowGuid**</span></span>  
 <span data-ttu-id="ffeee-210">指出 SQL Server 是否會使用資料行做為 ROWGUID。</span><span class="sxs-lookup"><span data-stu-id="ffeee-210">Indicates whether SQL Server uses the column as a ROWGUID.</span></span> <span data-ttu-id="ffeee-211">您只能將唯一識別欄位的這個值設定為 [是] \*\*\*\* 。</span><span class="sxs-lookup"><span data-stu-id="ffeee-211">You can set this value to **Yes** only for a unique identity column.</span></span> <span data-ttu-id="ffeee-212">若要編輯這個屬性，請按一下該屬性的值，並展開下拉式清單，然後選擇另一個值。</span><span class="sxs-lookup"><span data-stu-id="ffeee-212">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="ffeee-213">**大小**</span><span class="sxs-lookup"><span data-stu-id="ffeee-213">**Size**</span></span>  
 <span data-ttu-id="ffeee-214">以位元組為單位，顯示資料行之資料類型所允許的大小。</span><span class="sxs-lookup"><span data-stu-id="ffeee-214">Shows the size in bytes allowed by column's data type.</span></span> <span data-ttu-id="ffeee-215">例如，nchar 資料類型的長度可能是 10 (字元數)，但是針對 Unicode 字元集，大小就會是 20。</span><span class="sxs-lookup"><span data-stu-id="ffeee-215">For example, a nchar data type may have a length of 10 (the number of characters) but it would have a size of 20 to account for Unicode character sets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ffeee-216">每個資料列的 **(max)** 資料類型長度都會不同。</span><span class="sxs-lookup"><span data-stu-id="ffeee-216">The length of a **(max)** data types vary for each row.</span></span> <span data-ttu-id="ffeee-217">**sp_help** 會傳回 (-1) 當作 **(max)** 資料行的長度。</span><span class="sxs-lookup"><span data-stu-id="ffeee-217">**sp_help** returns (-1) as the length of **(max)** columns.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="ffeee-218">會顯示 -1 當作資料行大小。</span><span class="sxs-lookup"><span data-stu-id="ffeee-218">displays -1 as the column size.</span></span>  
  
  
