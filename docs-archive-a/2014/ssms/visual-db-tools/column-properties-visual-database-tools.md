---
title: 資料行屬性 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.designers.properties.Column.ColumnIdentitySpec
- vdt.designers.properties.Column
- vdt.tablecolumn
- vdt.designers.properties.Column.ColumnComputedColumnSpec
- vdt.designers.properties.Column.ColumnFulltextSpec
ms.assetid: e549a2a8-4154-4ec8-b146-614564169b39
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6aeb4d01cae7c09c27cafa8284638bf0a7de9691
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686711"
---
# <a name="column-properties-visual-database-tools"></a><span data-ttu-id="b2b1d-102">資料行屬性 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b2b1d-102">Column Properties (Visual Database Tools)</span></span>
  <span data-ttu-id="b2b1d-103">系統提供兩組資料行屬性：您可以在資料表設計工具的 [資料行屬性]  索引標籤中看到整組屬性 (僅適用於 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫)，並可以使用伺服器總管在 [屬性] 視窗中看到子集。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-103">There are two sets of properties for columns: a full set that you can see in the **Column Properties** tab within Table Designer (available only for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases) and a subset you can see in the Properties window using Server Explorer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b2b1d-104">此主題中的屬性，是依類別目錄的順序排列，而非依字母排列。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-104">The properties in this topic are ordered by category rather than alphabet.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b2b1d-105">您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b2b1d-106">若要變更您的設定，請在 [工具]  功能表上選擇 [匯入和匯出設定]  。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span>  
  
## <a name="properties-window"></a><span data-ttu-id="b2b1d-107">屬性視窗</span><span class="sxs-lookup"><span data-stu-id="b2b1d-107">Properties Window</span></span>  
 <span data-ttu-id="b2b1d-108">當您在伺服器總管中選取資料行時，這些屬性會出現在 [屬性] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-108">These properties appear in the Properties window when you select a column in Server Explorer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b2b1d-109">這些屬性可使用 [伺服器總管] 來存取，而且都是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-109">These properties, accessed using Server Explorer, are read-only.</span></span> <span data-ttu-id="b2b1d-110">若要編輯 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的資料行屬性，請在 [資料表設計工具] 中選取資料行。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-110">To edit column properties for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, select the column in Table Designer.</span></span> <span data-ttu-id="b2b1d-111">本主題稍後將描述這些屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-111">Those properties are described later in this topic.</span></span>  
  
 <span data-ttu-id="b2b1d-112">**識別類別目錄**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-112">**Identity Category**</span></span>  
 <span data-ttu-id="b2b1d-113">展開以顯示 [名稱]  和 [資料庫]  屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-113">Expands to show the **Name** and **Database** properties.</span></span>  
  
 <span data-ttu-id="b2b1d-114">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-114">**Name**</span></span>  
 <span data-ttu-id="b2b1d-115">顯示資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-115">Shows the name of the column.</span></span>  
  
 <span data-ttu-id="b2b1d-116">**Database**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-116">**Database**</span></span>  
 <span data-ttu-id="b2b1d-117">顯示選取的資料行之資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-117">Shows the name of the data source for the selected column.</span></span> <span data-ttu-id="b2b1d-118">(僅適用於 OLE DB)。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-118">(Applies only to OLE DB.)</span></span>  
  
 <span data-ttu-id="b2b1d-119">**其他類別目錄**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-119">**Misc Category**</span></span>  
 <span data-ttu-id="b2b1d-120">展開以顯示其餘屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-120">Expands to show the remaining properties.</span></span>  
  
 <span data-ttu-id="b2b1d-121">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-121">**Data Type**</span></span>  
 <span data-ttu-id="b2b1d-122">顯示選取之資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-122">Shows the data type of the selected column.</span></span> <span data-ttu-id="b2b1d-123">如需詳細資訊，請參閱[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-123">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
 <span data-ttu-id="b2b1d-124">**識別值增量**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-124">**Identity Increment**</span></span>  
 <span data-ttu-id="b2b1d-125">針對識別欄位之每個後續的資料列，顯示將加到 [識別值種子]  的遞增量。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-125">Shows the increment that will be added to the **Identity Seed** for each subsequent row of the identity column.</span></span> <span data-ttu-id="b2b1d-126">(只適用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-126">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="b2b1d-127">**識別種子**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-127">**Identity Seed**</span></span>  
 <span data-ttu-id="b2b1d-128">顯示針對識別欄位，指派給資料表中之第一個資料列的種子值。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-128">Shows the seed value assigned to the first row in the table for the identity column.</span></span> <span data-ttu-id="b2b1d-129">(只適用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-129">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="b2b1d-130">**為識別**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-130">**Is Identity**</span></span>  
 <span data-ttu-id="b2b1d-131">顯示選取的資料行是否為資料表的識別欄位。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-131">Shows whether the selected column is the identity column for the table.</span></span> <span data-ttu-id="b2b1d-132">(只適用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-132">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="b2b1d-133">**長度**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-133">**Length**</span></span>  
 <span data-ttu-id="b2b1d-134">顯示以字元為基礎的資料類型所允許的字元數。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-134">Shows the number of characters allowed for character-based data types.</span></span>  
  
 <span data-ttu-id="b2b1d-135">**可為 Null**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-135">**Nullable**</span></span>  
 <span data-ttu-id="b2b1d-136">顯示資料行是否允許 Null 值。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-136">Shows whether or not the column allows null values.</span></span>  
  
 <span data-ttu-id="b2b1d-137">**有效位數**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-137">**Precision**</span></span>  
 <span data-ttu-id="b2b1d-138">顯示數值資料類型所允許的最大位數數目。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-138">Shows the maximum number of digits allowed for numeric data types.</span></span> <span data-ttu-id="b2b1d-139">這個屬性會顯示 **0** 來表示非數字的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-139">This property shows **0** for nonnumeric data types.</span></span>  
  
 <span data-ttu-id="b2b1d-140">**調整**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-140">**Scale**</span></span>  
 <span data-ttu-id="b2b1d-141">若為數值資料類型，顯示可在小數點右邊顯示的最大位數數目。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-141">Shows the maximum number of digits that can appear to the right of the decimal point for numeric data types.</span></span> <span data-ttu-id="b2b1d-142">這個值必須小於或等於有效位數。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-142">This value must be less than or equal to the precision.</span></span> <span data-ttu-id="b2b1d-143">這個屬性會顯示 **0** 來表示非數字的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-143">This property shows **0** for nonnumeric data types.</span></span>  
  
## <a name="column-properties-tab"></a><span data-ttu-id="b2b1d-144">資料行屬性索引標籤</span><span class="sxs-lookup"><span data-stu-id="b2b1d-144">Column Properties Tab</span></span>  
 <span data-ttu-id="b2b1d-145">若要存取這些屬性，請在伺服器總管中，以滑鼠右鍵按一下資料行所屬的資料表，選擇 [開啟資料表定義]  ，然後在資料表設計工具裡選取資料表方格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-145">To access these properties, in Server Explorer right-click the table to which the column belongs, choose **Open Table Definition**, and select the row in the table grid in Table Designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b2b1d-146">這些屬性只適用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-146">These properties apply only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b2b1d-147">**一般類別目錄**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-147">**General Category**</span></span>  
 <span data-ttu-id="b2b1d-148">展開以顯示 [名稱]  、[允許 Null]  、[資料類型]  、[預設值或繫結]  、[長度]  、[有效位數]  和 [小數位數]  。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-148">Expands to show **Name**, **Allow Nulls**, **Data Type**, **Default Value or Binding**, **Length**, **Precision**, and **Scale**.</span></span>  
  
 <span data-ttu-id="b2b1d-149">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-149">**Name**</span></span>  
 <span data-ttu-id="b2b1d-150">顯示資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-150">Displays the name of the column.</span></span> <span data-ttu-id="b2b1d-151">若要編輯名稱，請在文字方塊中輸入。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-151">To edit the name, type in the text box.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="b2b1d-152">如果現有的查詢、檢視、使用者自訂函數、預存程序或程式參考資料行，修改名稱就會使這些物件無效。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-152">If existing queries, views, user-defined functions, stored procedures, or programs refer to the column, the name modification will make these objects invalid.</span></span>  
  
 <span data-ttu-id="b2b1d-153">**允許 Null**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-153">**Allow Nulls**</span></span>  
 <span data-ttu-id="b2b1d-154">顯示資料行的資料類型是否允許 Null 值。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-154">Shows whether or not the column's data type allows null values.</span></span>  
  
 <span data-ttu-id="b2b1d-155">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-155">**Data Type**</span></span>  
 <span data-ttu-id="b2b1d-156">顯示選取之資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-156">Shows the data type for the selected column.</span></span> <span data-ttu-id="b2b1d-157">若要編輯這個屬性，請按一下該屬性的值，並展開下拉式清單，然後選擇另一個值。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-157">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span> <span data-ttu-id="b2b1d-158">如需詳細資訊，請參閱[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-158">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
 <span data-ttu-id="b2b1d-159">**預設值或繫結**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-159">**Default Value or Binding**</span></span>  
 <span data-ttu-id="b2b1d-160">沒有為此資料行指定值時，顯示此資料行的預設值。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-160">Shows the default for this column when no value is specified for this column.</span></span> <span data-ttu-id="b2b1d-161">下拉式清單包含資料來源中所定義的所有全域預設值。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-161">The drop-down list contains all global defaults defined in the data source.</span></span> <span data-ttu-id="b2b1d-162">若要將資料行繫結到全域預設值，請從下拉式清單中選取。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-162">To bind the column to a global default, select from the drop-down list.</span></span> <span data-ttu-id="b2b1d-163">此外，若要為資料行建立預設條件約束，請直接將預設值當作文字輸入。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-163">Alternatively, to create a default constraint for the column, type the default value directly as text.</span></span>  
  
 <span data-ttu-id="b2b1d-164">**長度**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-164">**Length**</span></span>  
 <span data-ttu-id="b2b1d-165">顯示以字元為基礎的資料類型所允許的字元數。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-165">Shows the number of characters allowed for character-based data types.</span></span> <span data-ttu-id="b2b1d-166">此屬性只適用於以字元為主的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-166">This property is only available for character-based data types.</span></span>  
  
 <span data-ttu-id="b2b1d-167">**有效位數**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-167">**Precision**</span></span>  
 <span data-ttu-id="b2b1d-168">顯示數值資料類型所允許的最大位數數目。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-168">Shows the maximum number of digits allowed for numeric data types.</span></span> <span data-ttu-id="b2b1d-169">這個屬性會顯示 **0** 來表示非數字的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-169">This property shows **0** for nonnumeric data types.</span></span> <span data-ttu-id="b2b1d-170">此屬性僅適用於數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-170">This property is only available for numeric data types.</span></span>  
  
 <span data-ttu-id="b2b1d-171">**調整**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-171">**Scale**</span></span>  
 <span data-ttu-id="b2b1d-172">若為數值資料類型，顯示可在小數點右邊顯示的最大位數數目。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-172">Shows the maximum number of digits that can appear to the right of the decimal point for numeric data types.</span></span> <span data-ttu-id="b2b1d-173">這個值必須小於或等於有效位數。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-173">This value must be less than or equal to the precision.</span></span> <span data-ttu-id="b2b1d-174">這個屬性會顯示 **0** 來表示非數字的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-174">This property shows **0** for nonnumeric data types.</span></span> <span data-ttu-id="b2b1d-175">此屬性僅適用於數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-175">This property is only available for numeric data types.</span></span>  
  
 <span data-ttu-id="b2b1d-176">**資料表設計工具類別目錄**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-176">**Table Designer Category**</span></span>  
 <span data-ttu-id="b2b1d-177">展開以顯示其餘屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-177">Expands to show the remaining properties.</span></span>  
  
 <span data-ttu-id="b2b1d-178">**定序**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-178">**Collation**</span></span>  
 <span data-ttu-id="b2b1d-179">顯示選取之資料行的定序設定。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-179">Shows the collation setting for the selected column.</span></span> <span data-ttu-id="b2b1d-180">若要變更此設定，請按一下 [定序]  ，然後按一下值右邊的省略符號 (...)  。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-180">To change this setting, click **Collation** and then click the ellipses **(...)** to the right of the value.</span></span>  
  
 <span data-ttu-id="b2b1d-181">**計算資料行規格類別目錄**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-181">**Computed Column Specification Category**</span></span>  
 <span data-ttu-id="b2b1d-182">展開以顯示 [公式]  和 [為永續性]  的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-182">Expands to show properties for **Formula** and **Is Persisted**.</span></span> <span data-ttu-id="b2b1d-183">如果資料行為計算的，則也會顯示公式。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-183">If the column is computed, the formula will also be displayed.</span></span> <span data-ttu-id="b2b1d-184">若要編輯公式，請展開此類別目錄，並在 [公式]  屬性中編輯它。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-184">To edit the formula, expand this category and edit it in the **Formula** property.</span></span>  
  
 <span data-ttu-id="b2b1d-185">**公式**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-185">**Formula**</span></span>  
 <span data-ttu-id="b2b1d-186">如果選取之資料行是計算的資料行，則顯示該資料行所使用的公式。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-186">Shows the formula that the selected column uses if it is a computed column.</span></span> <span data-ttu-id="b2b1d-187">在此欄位中，您可以輸入或變更公式。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-187">In this field you can enter or change a formula.</span></span>  
  
 <span data-ttu-id="b2b1d-188">**為保存的**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-188">**Is Persisted**</span></span>  
 <span data-ttu-id="b2b1d-189">允許您將計算的資料行與資料來源儲存在一起。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-189">Allows you to save the computed column with the data source.</span></span> <span data-ttu-id="b2b1d-190">保存的計算資料行可以建立索引。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-190">A persisted computed column can be indexed.</span></span>  
  
 <span data-ttu-id="b2b1d-191">**資料類型扼要**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-191">**Condensed Data Type**</span></span>  
 <span data-ttu-id="b2b1d-192">顯示欄位的資料類型資訊，使用與 SQL CREATE TABLE 陳述式相同的格式。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-192">Displays information about the field's data type, in the same format as the SQL CREATE TABLE statement.</span></span> <span data-ttu-id="b2b1d-193">例如，包含可變長度字串 (最大長度為 20 個字元) 的欄位可表示為「varchar(20)」。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-193">For example, a field containing a variable-length string with a maximum length of 20 characters would be represented as "varchar(20)."</span></span> <span data-ttu-id="b2b1d-194">若要變更這個屬性，請直接輸入屬性值。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-194">To change this property, type the value directly.</span></span>  
  
 <span data-ttu-id="b2b1d-195">**說明**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-195">**Description**</span></span>  
 <span data-ttu-id="b2b1d-196">顯示資料行的描述。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-196">Shows the description of the column.</span></span> <span data-ttu-id="b2b1d-197">若要查看完整的描述，或要編輯它，請按一下 [描述]，然後按一下屬性右邊的省略符號 (...)  。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-197">To see the full description or to edit it, click Description, and then click the ellipses **(...)** to the right of the property.</span></span>  
  
 <span data-ttu-id="b2b1d-198">**全文檢索規格類別目錄**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-198">**Full-text Specification Category**</span></span>  
 <span data-ttu-id="b2b1d-199">展開以顯示全文檢索資料行特定的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-199">Expands to show properties specific to full-text columns.</span></span>  
  
 <span data-ttu-id="b2b1d-200">**為全文檢索索引**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-200">**Is Full-text Indexed**</span></span>  
 <span data-ttu-id="b2b1d-201">指出此資料行是否為全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-201">Indicates whether this column is full-text indexed.</span></span> <span data-ttu-id="b2b1d-202">只有在此資料行的資料類型能以全文檢索搜尋，以及此資料行所屬的資料表具有為其指定的全文檢索索引時，才能將這個屬性設定為 [是]  。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-202">This property can be set to **Yes** only if the data type for this column is full-text searchable and if the table to which this column belongs has a full-text index specified for it.</span></span> <span data-ttu-id="b2b1d-203">若要變更此值，請按一下它，展開下拉式清單，然後選擇新的值。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-203">To change this value, click it, expand the drop-down list, and choose a new value.</span></span>  
  
 <span data-ttu-id="b2b1d-204">**全文檢索類型資料行**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-204">**Full-text type column**</span></span>  
 <span data-ttu-id="b2b1d-205">顯示哪個資料行是用來定義影像類型資料行的文件類型。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-205">Shows which column is used to define the document type of a column of type image.</span></span> <span data-ttu-id="b2b1d-206">影像資料類型可用來儲存從 .doc 檔至 xml 檔案的各種文件。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-206">The image data type can be used to store documents ranging from .doc files to xml files.</span></span>  
  
 <span data-ttu-id="b2b1d-207">**語言**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-207">**Language**</span></span>  
 <span data-ttu-id="b2b1d-208">指出用來建立資料行索引的語言。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-208">Indicates the language used to index the column.</span></span>  
  
 <span data-ttu-id="b2b1d-209">**統計語意**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-209">**Statistical Semantics**</span></span>  
 <span data-ttu-id="b2b1d-210">選取是否要針對選取的資料行啟用統計語意索引。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-210">Select whether to enable statistical semantic indexing for the selected column.</span></span> <span data-ttu-id="b2b1d-211">如需詳細資訊，請參閱[語意搜尋 &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-211">For more information, see [Semantic Search &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md).</span></span>  
  
 <span data-ttu-id="b2b1d-212">如果您在選取 **[統計語意]** 之前選取 **[語言]** ，而且選取的語言沒有相關聯的語意語言模型，則 **[統計語意]** 選項會設定為 **[否]** ，而且無法修改。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-212">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** option is set to **No** and cannot be modified.</span></span> <span data-ttu-id="b2b1d-213">如果您在選取 **[語言]** 之前針對 **[統計語意]** 選項選取 **[是]** ，則 **[語言]** 欄中的可用語言將受限為有語意語言模型支援的語言。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-213">If you select **Yes** for the **Statistical Semantics** option prior to selecting a **Language**, then the languages available in the **Language** column will be restricted to those for which there is Semantic Language Model support.</span></span>  
  
 <span data-ttu-id="b2b1d-214">**有非 SQL Server 訂閱者**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-214">**Has Non-SQL Server Subscriber**</span></span>  
 <span data-ttu-id="b2b1d-215">顯示資料行是否具有非 Microsoft SQL Server 訂閱者。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-215">Shows whether the column has a non-Microsoft SQL Server subscriber.</span></span>  
  
 <span data-ttu-id="b2b1d-216">**識別規格類別目錄**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-216">**Identity Specification Category**</span></span>  
 <span data-ttu-id="b2b1d-217">展開以顯示 [為識別]  、[識別值增量]  和 [識別種子]  的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-217">Expands to show properties for **Is Identity**, **Identity Increment**, and **Identity Seed**.</span></span>  
  
 <span data-ttu-id="b2b1d-218">**為識別**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-218">**Is Identity**</span></span>  
 <span data-ttu-id="b2b1d-219">顯示選取的資料行是否為資料表的識別欄位。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-219">Shows whether the selected column is the identity column for the table.</span></span> <span data-ttu-id="b2b1d-220">若要變更屬性，請在資料表設計工具中開啟資料表，並在 [屬性]  視窗中編輯屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-220">To change the property, open the table in Table Designer and edit the properties in the **Properties** window.</span></span> <span data-ttu-id="b2b1d-221">此設定僅適用於以數值為基礎之資料類型的資料行，例如 *int*。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-221">This setting applies only to columns with a number-based data type, such as *int*.</span></span>  
  
 <span data-ttu-id="b2b1d-222">**識別值增量**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-222">**Identity Increment**</span></span>  
 <span data-ttu-id="b2b1d-223">針對每個後續的資料列，顯示將加到 [識別種子]  的遞增量。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-223">Shows the increment that will be added to the **Identity Seed** for each subsequent row.</span></span> <span data-ttu-id="b2b1d-224">如果將這個資料格保留空白，則預設會指派值 1。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-224">If you leave this cell blank, the value 1 will be assigned by default.</span></span> <span data-ttu-id="b2b1d-225">若要編輯這個屬性，請直接輸入新值。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-225">To edit this property, type the new value directly.</span></span>  
  
 <span data-ttu-id="b2b1d-226">**識別種子**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-226">**Identity Seed**</span></span>  
 <span data-ttu-id="b2b1d-227">顯示指派至資料表之中第一個資料列的值。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-227">Shows the value assigned to the first row in the table.</span></span> <span data-ttu-id="b2b1d-228">如果將這個資料格保留空白，則預設會指派值 1。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-228">If you leave this cell blank, the value 1 will be assigned by default.</span></span> <span data-ttu-id="b2b1d-229">若要編輯這個屬性，請直接輸入新值。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-229">To edit this property, type the new value directly.</span></span>  
  
 <span data-ttu-id="b2b1d-230">**為決定性的**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-230">**Is Deterministic**</span></span>  
 <span data-ttu-id="b2b1d-231">顯示是否可以確定地決定選取之資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-231">Shows whether the data type of the selected column can be determined with certainty.</span></span>  
  
 <span data-ttu-id="b2b1d-232">**為以 DTS 發行**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-232">**Is DTS-published**</span></span>  
 <span data-ttu-id="b2b1d-233">顯示資料行是否為以 DTS 發行。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-233">Shows whether the column is DTS-published.</span></span>  
  
 <span data-ttu-id="b2b1d-234">**為可編索引**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-234">**Is Indexable**</span></span>  
 <span data-ttu-id="b2b1d-235">顯示選取的資料行是否可以建立索引。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-235">Shows whether the selected column can be indexed.</span></span> <span data-ttu-id="b2b1d-236">例如，不具決定性之計算的資料行不可以建立索引。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-236">For example, non-deterministic computed columns cannot be indexed.</span></span>  
  
 <span data-ttu-id="b2b1d-237">**為合併發行**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-237">**Is Merge-published**</span></span>  
 <span data-ttu-id="b2b1d-238">顯示資料行是否為合併發行。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-238">Shows whether the column is merge-published.</span></span>  
  
 <span data-ttu-id="b2b1d-239">**為不可複寫**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-239">**Is Not For Replication**</span></span>  
 <span data-ttu-id="b2b1d-240">指出在複寫期間是否保留原始識別值。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-240">Indicates whether original identity values are preserved during replication.</span></span> <span data-ttu-id="b2b1d-241">若要編輯這個屬性，請按一下該屬性的值，並展開下拉式清單，然後選擇另一個值。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-241">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="b2b1d-242">**為已複寫**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-242">**Is Replicated**</span></span>  
 <span data-ttu-id="b2b1d-243">顯示此資料行是否在其他位置已複寫。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-243">Shows whether this column is replicated in another location.</span></span>  
  
 <span data-ttu-id="b2b1d-244">**為 RowGuid**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-244">**Is RowGuid**</span></span>  
 <span data-ttu-id="b2b1d-245">指出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是否會使用資料行當做 ROWGUID。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-245">Indicates whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the column as a ROWGUID.</span></span> <span data-ttu-id="b2b1d-246">您只能針對資料類型為的資料行，將此值設定為 **[是]** `uniqueidentifier` 。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-246">You can set this value to **Yes** only for a column with the data type of `uniqueidentifier`.</span></span> <span data-ttu-id="b2b1d-247">若要編輯這個屬性，請按一下該屬性的值，並展開下拉式清單，然後選擇另一個值。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-247">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="b2b1d-248">**大小**</span><span class="sxs-lookup"><span data-stu-id="b2b1d-248">**Size**</span></span>  
 <span data-ttu-id="b2b1d-249">以位元組為單位，顯示資料行之資料類型所允許的大小。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-249">Shows the size in bytes allowed by column's data type.</span></span> <span data-ttu-id="b2b1d-250">例如，`nchar` 資料類型的長度可能是 10 (字元數)，但是針對 Unicode 字元集，大小就會是 20。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-250">For example, a `nchar` data type may have a length of 10 (the number of characters) but it would have a size of 20 to account for Unicode character sets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b2b1d-251">每個資料列的 `varchar(max)` 資料類型長度都會不同。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-251">The length of a `varchar(max)` data type varies for each row.</span></span> <span data-ttu-id="b2b1d-252">sp_help 會傳回 (-1) 做為資料 `varchar(max)` 行的長度。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-252">sp_help returns (-1) as the length of `varchar(max)` column.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="b2b1d-253">會顯示 -1 當作資料行大小。</span><span class="sxs-lookup"><span data-stu-id="b2b1d-253">displays -1 as the column size.</span></span>  
  
  
