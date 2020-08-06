---
title: " (資料採礦) 的內容類型 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], content types
- KEY SEQUENCE column
- content types [data mining]
- attributes [data mining]
- DISCRETIZED column
- CONTINUOUS column
- CYCLICAL column
- ORDERED column
- discretized columns [data mining]
- discrete columns [Analysis Services]
- DISCRETE column
- KEY column
- KEY TIME column
- continuous columns
- coding [Data Mining]
ms.assetid: 2dacd968-70e8-4993-88b6-a6d36024a4e4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8e3400d904bc857bc282bb1ad9220c1e01fe5a4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686548"
---
# <a name="content-types-data-mining"></a><span data-ttu-id="015bc-102">內容類型 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="015bc-102">Content Types (Data Mining)</span></span>
  <span data-ttu-id="015bc-103">在中， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 您可以在模型中使用時，同時定義資料行的實體資料類型，以及資料行的邏輯內容類型。</span><span class="sxs-lookup"><span data-stu-id="015bc-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can define the both the physical data type for a column in a mining structure, and a logical content type for the column when used in a model,</span></span>  
  
 <span data-ttu-id="015bc-104">*「資料類型」* 會決定當您建立採礦模型時，演算法要如何處理這些資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="015bc-104">The *data type* determines how algorithms process the data in those columns when you create mining models.</span></span> <span data-ttu-id="015bc-105">定義資料行的資料類型會提供資訊給演算法，這是有關資料行中的資料類型及如何處理資料的資訊。</span><span class="sxs-lookup"><span data-stu-id="015bc-105">Defining the data type of a column gives the algorithm information about the type of data in the columns, and how to process the data.</span></span> <span data-ttu-id="015bc-106">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的每一個資料類型都會支援一個或多個適用於資料採礦的內容類型。</span><span class="sxs-lookup"><span data-stu-id="015bc-106">Each data type in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supports one or more content types for data mining.</span></span>  
  
 <span data-ttu-id="015bc-107">*「內容類型」* 會描述資料行所包含之內容的行為。</span><span class="sxs-lookup"><span data-stu-id="015bc-107">The *content type* describes the behavior of the content that the column contains.</span></span> <span data-ttu-id="015bc-108">例如，若資料行中的內容以特定間隔重複 (例如每星期幾)，您可以指定資料行的內容類型為循環。</span><span class="sxs-lookup"><span data-stu-id="015bc-108">For example, if the content in a column repeats in a specific interval, such as days of the week, you can specify the content type of that column as cyclical.</span></span>  
  
 <span data-ttu-id="015bc-109">有些演算法需要特定資料類型和內容類型才能正確運作。</span><span class="sxs-lookup"><span data-stu-id="015bc-109">Some algorithms require specific data types and specific content types to be able to function correctly.</span></span> <span data-ttu-id="015bc-110">例如，Microsoft 貝氏機率分類演算法無法使用連續資料行做為輸入，也無法預測連續值。</span><span class="sxs-lookup"><span data-stu-id="015bc-110">For example, the Microsoft Naive Bayes algorithm cannot use continuous columns as input, and cannot predict continuous values.</span></span> <span data-ttu-id="015bc-111">某些內容類型 (如 Key Sequence) 只會由特定的演算法所使用。</span><span class="sxs-lookup"><span data-stu-id="015bc-111">Some content types, such as Key Sequence, are used only by a specific algorithm.</span></span> <span data-ttu-id="015bc-112">如需演算法清單和各演算法支援的內容類型，請參閱[資料採礦演算法 &#40;Analysis Services-資料採礦 &#41;](data-mining-algorithms-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="015bc-112">For a list of the algorithms and the content types that each supports, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="015bc-113">下列清單描述資料採礦中使用的內容類型，並識別支援每一種類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="015bc-113">The following list describes the content types that are used in data mining, and identifies the data types that support each type.</span></span>  
  
## <a name="discrete"></a><span data-ttu-id="015bc-114">Discrete</span><span class="sxs-lookup"><span data-stu-id="015bc-114">Discrete</span></span>  
 <span data-ttu-id="015bc-115">*Discrete* 代表資料行包含有限數量的值，且值之間沒有延續。</span><span class="sxs-lookup"><span data-stu-id="015bc-115">*Discrete* means that the column contains a finite number of values with no continuum between values.</span></span> <span data-ttu-id="015bc-116">例如，性別資料行是一個典型的離散屬性資料行，因為其資料代表特定數量的類別。</span><span class="sxs-lookup"><span data-stu-id="015bc-116">For example, a gender column is a typical discrete attribute column, in that the data represents a specific number of categories.</span></span>  
  
 <span data-ttu-id="015bc-117">離散屬性資料行中的值不代表順序，即使值為數值。</span><span class="sxs-lookup"><span data-stu-id="015bc-117">The values in a discrete attribute column cannot imply ordering, even if the values are numeric.</span></span> <span data-ttu-id="015bc-118">此外，即使用於離散資料行的值為數值，也無法計算小數值。</span><span class="sxs-lookup"><span data-stu-id="015bc-118">Moreover, even if the values used for the discrete column are numeric, fractional values cannot be calculated.</span></span> <span data-ttu-id="015bc-119">電話區碼是數字分隔資料的理想範例。</span><span class="sxs-lookup"><span data-stu-id="015bc-119">Telephone area codes are a good example of discrete data that is numeric.</span></span>  
  
 <span data-ttu-id="015bc-120">`Discrete` 內容類型受所有資料採礦資料類型的支援。</span><span class="sxs-lookup"><span data-stu-id="015bc-120">The `Discrete` content type is supported by all data mining data types.</span></span>  
  
## <a name="continuous"></a><span data-ttu-id="015bc-121">連續</span><span class="sxs-lookup"><span data-stu-id="015bc-121">Continuous</span></span>  
 <span data-ttu-id="015bc-122">*Continuous* 表示此資料行包含的值代表小數位數允許過渡值的數值資料。</span><span class="sxs-lookup"><span data-stu-id="015bc-122">*Continuous* means that the column contains values that represent numeric data on a scale that allows interim values.</span></span> <span data-ttu-id="015bc-123">與代表有限可計算資料的離散資料行不同，連續資料行代表可擴充的度量，其資料可能包含無限個小數值。</span><span class="sxs-lookup"><span data-stu-id="015bc-123">Unlike a discrete column, which represents finite, countable data, a continuous column represents scalable measurements, and it is possible for the data to contain an infinite number of fractional values.</span></span> <span data-ttu-id="015bc-124">溫度資料行就是連續屬性資料行的一個範例。</span><span class="sxs-lookup"><span data-stu-id="015bc-124">A column of temperatures is an example of a continuous attribute column.</span></span>  
  
 <span data-ttu-id="015bc-125">當資料行包含連續數值資料，而且您知道應該要如何散發資料時，您可以指定預期的值分佈來提升分析的精確度。</span><span class="sxs-lookup"><span data-stu-id="015bc-125">When a column contains continuous numeric data, and you know how the data should be distributed, you can potentially improve the accuracy of the analysis by specifying the expected distribution of values.</span></span> <span data-ttu-id="015bc-126">您會在採礦結構的層級上指定資料行散發。</span><span class="sxs-lookup"><span data-stu-id="015bc-126">You specify the column distribution at the level of the mining structure.</span></span> <span data-ttu-id="015bc-127">因此，此設定會套用到根據此結構的所有模型上。如需詳細資訊，請參閱[資料行散發 &#40;資料採礦&#41;](column-distributions-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="015bc-127">Therefore, the setting applies to all models that are based on the structure, For more information, see [Column Distributions &#40;Data Mining&#41;](column-distributions-data-mining.md).</span></span>  
  
 <span data-ttu-id="015bc-128">`Continuous` 內容類型受到下列資料類型的支援：`Date`、`Double` 和 `Long`。</span><span class="sxs-lookup"><span data-stu-id="015bc-128">The `Continuous` content type is supported by the following data types: `Date`, `Double`, and `Long`.</span></span>  
  
## <a name="discretized"></a><span data-ttu-id="015bc-129">Discretized</span><span class="sxs-lookup"><span data-stu-id="015bc-129">Discretized</span></span>  
 <span data-ttu-id="015bc-130">*「離散化」* (Discretization) 是將連續資料集的值放入值區內的程序，以產生有限數目的可能值。</span><span class="sxs-lookup"><span data-stu-id="015bc-130">*Discretization* is the process of putting values of a continuous set of data into buckets so that there are a limited number of possible values.</span></span> <span data-ttu-id="015bc-131">您只能離散化數值資料。</span><span class="sxs-lookup"><span data-stu-id="015bc-131">You can discretize only numeric data.</span></span>  
  
 <span data-ttu-id="015bc-132">因此， *「離散化」* (Discretized) 內容類型表示此資料行包含的值代表從連續資料行衍生之值的群組或值區。</span><span class="sxs-lookup"><span data-stu-id="015bc-132">Thus, the *discretized* content type indicates that the column contains values that represent groups, or buckets, of values that are derived from a continuous column.</span></span> <span data-ttu-id="015bc-133">貯體會被當成已排序的離散值來處理。</span><span class="sxs-lookup"><span data-stu-id="015bc-133">The buckets are treated as ordered and discrete values.</span></span>  
  
 <span data-ttu-id="015bc-134">您可以手動離散化資料，以確保您能取得所要的值區，或者可以使用在 SQL Server Analysis Services 中提供的離散化方法。</span><span class="sxs-lookup"><span data-stu-id="015bc-134">You can discretize your data manually, to ensure that you get the buckets you want, or you can use the discretization methods provided in SQL Server Analysis Services.</span></span> <span data-ttu-id="015bc-135">某些演算法會自動執行離散化。</span><span class="sxs-lookup"><span data-stu-id="015bc-135">Some algorithms perform discretization automatically.</span></span> <span data-ttu-id="015bc-136">如需詳細資訊，請參閱 [變更採礦模型中的資料行分隔](change-the-discretization-of-a-column-in-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="015bc-136">For more information, see [Change the Discretization of a Column in a Mining Model](change-the-discretization-of-a-column-in-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="015bc-137">`Discretized` 內容類型受到下列資料類型的支援：`Date`、`Double`、`Long` 和 `Text`。</span><span class="sxs-lookup"><span data-stu-id="015bc-137">The `Discretized` content type is supported by the following data types: `Date`, `Double`, `Long`, and `Text`.</span></span>  
  
## <a name="key"></a><span data-ttu-id="015bc-138">Key</span><span class="sxs-lookup"><span data-stu-id="015bc-138">Key</span></span>  
 <span data-ttu-id="015bc-139">*key* 內容類型表示資料行會唯一識別資料列。</span><span class="sxs-lookup"><span data-stu-id="015bc-139">The *key* content type means that the column uniquely identifies a row.</span></span> <span data-ttu-id="015bc-140">在案例資料表中，索引鍵資料行通常是數值的或文字的識別碼。</span><span class="sxs-lookup"><span data-stu-id="015bc-140">In a case table, typically the key column is a numeric or text identifier.</span></span> <span data-ttu-id="015bc-141">您可以將內容類型設定為 `key`，以代表資料行只可以用於追蹤記錄，而不能用於分析。</span><span class="sxs-lookup"><span data-stu-id="015bc-141">You set the content type to `key` to indicate that the column should not be used for analysis, only for tracking records.</span></span>  
  
 <span data-ttu-id="015bc-142">巢狀資料表也具有索引鍵，但巢狀資料表索引鍵的用法稍有不同。</span><span class="sxs-lookup"><span data-stu-id="015bc-142">Nested tables also have keys, but the usage of the nested table key is a little different.</span></span> <span data-ttu-id="015bc-143">如果資料行是您想要分析的屬性，請在巢狀資料表中將內容類型設定為 `key`。</span><span class="sxs-lookup"><span data-stu-id="015bc-143">You set the content type to `key` in a nested table if the column is the attribute that you want to analyze.</span></span> <span data-ttu-id="015bc-144">每個案例的巢狀資料表索引鍵值都必須是唯一的，但在整個案例集合中可能會有重複的值。</span><span class="sxs-lookup"><span data-stu-id="015bc-144">The values in the nested table key must be unique for each case but there can be duplicates across the entire set of cases.</span></span>  
  
 <span data-ttu-id="015bc-145">例如，如果要分析客戶購買的產品，則可以將內容類型設定為案例資料表中 **CustomerID** 資料行的索引鍵，然後再次將內容類型設定為巢狀資料表中 **PurchasedProducts** 資料行的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="015bc-145">For example, if you are analyzing the products that customers purchase, you would set content type to key for the **CustomerID** column in the case table, and set content type to key again for the **PurchasedProducts** column in the nested table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="015bc-146">只有在從已定義為 Analysis Services 資料來源檢視的外部資料來源使用資料時，才可以使用巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="015bc-146">Nested tables are available only if you use data from an external data source that has been defined as an Analysis services data source view.</span></span>  
  
 <span data-ttu-id="015bc-147">這個內容類型受到下列資料類型所支援：`Date`、`Double`、`Long` 和 `Text`。</span><span class="sxs-lookup"><span data-stu-id="015bc-147">This content type is supported by the following data types: `Date`, `Double`, `Long`, and `Text`.</span></span>  
  
## <a name="key-sequence"></a><span data-ttu-id="015bc-148">Key Sequence</span><span class="sxs-lookup"><span data-stu-id="015bc-148">Key Sequence</span></span>  
 <span data-ttu-id="015bc-149">*key sequence* 內容類型只能用於時序群集模型。</span><span class="sxs-lookup"><span data-stu-id="015bc-149">The *key sequence* content type can only be used in sequence clustering models.</span></span> <span data-ttu-id="015bc-150">將內容類型設定為 `key sequence` 時，代表資料行包含代表事件序列的值。</span><span class="sxs-lookup"><span data-stu-id="015bc-150">When you set content type to `key sequence`, it indicates that the column contains values that represent a sequence of events.</span></span> <span data-ttu-id="015bc-151">其值已排序，但不必為等距。</span><span class="sxs-lookup"><span data-stu-id="015bc-151">The values are ordered, but do not have to be an equal distance apart.</span></span>  
  
 <span data-ttu-id="015bc-152">這個內容類型受到下列資料類型所支援：`Double`、`Long`、`Text` 和 `Date`。</span><span class="sxs-lookup"><span data-stu-id="015bc-152">This content type is supported by the following data types: `Double`, `Long`, `Text`, and `Date`.</span></span>  
  
## <a name="key-time"></a><span data-ttu-id="015bc-153">Key Time</span><span class="sxs-lookup"><span data-stu-id="015bc-153">Key Time</span></span>  
 <span data-ttu-id="015bc-154">*key time* 內容類型只能用於時間序列模型。</span><span class="sxs-lookup"><span data-stu-id="015bc-154">The *key time* content type can only be used in time series models.</span></span> <span data-ttu-id="015bc-155">將內容類型設定為 `key time` 時，代表值已排序且代表時段。</span><span class="sxs-lookup"><span data-stu-id="015bc-155">When you set content type to `key time`, it indicates that the values are ordered and represent a time scale.</span></span>  
  
 <span data-ttu-id="015bc-156">這個內容類型受到下列資料類型所支援：`Double`、`Long` 和 `Date`。</span><span class="sxs-lookup"><span data-stu-id="015bc-156">This content type is supported by the following data types: `Double`, `Long`, and `Date`.</span></span>  
  
## <a name="table"></a><span data-ttu-id="015bc-157">資料表</span><span class="sxs-lookup"><span data-stu-id="015bc-157">Table</span></span>  
 <span data-ttu-id="015bc-158">*table* 內容類型表示資料行包含另一個資料表，資料表內有一個或多個資料行及一個或多個資料列。</span><span class="sxs-lookup"><span data-stu-id="015bc-158">The *table* content type indicates that the column contains another data table, with one or more columns and one or more rows.</span></span> <span data-ttu-id="015bc-159">對於案例資料表中的任何特定資料列，這個資料行也可以包含多個全與父案例記錄相關的值。</span><span class="sxs-lookup"><span data-stu-id="015bc-159">For any particular row in the case table, this column can contain multiple values, all related to the parent case record.</span></span> <span data-ttu-id="015bc-160">例如，如果主要案例資料表包含客戶清單，則您可以擁有數個包含巢狀資料表的資料行，例如 **ProductsPurchased** 資料行 (其中巢狀資料表會列出此客戶過去購買的產品) 及 **Hobbies** 資料行 (列出客戶興趣)。</span><span class="sxs-lookup"><span data-stu-id="015bc-160">For example, if the main case table contains a listing of customers, you could have several columns that contain nested tables, such as a **ProductsPurchased** column, where the nested table lists products bought by this customer in the past, and a **Hobbies** column that lists the interests of the customer.</span></span>  
  
 <span data-ttu-id="015bc-161">此資料行的資料類型一定是 `Table`。</span><span class="sxs-lookup"><span data-stu-id="015bc-161">The data type of this column is always `Table`.</span></span>  
  
## <a name="cyclical"></a><span data-ttu-id="015bc-162">Cyclical</span><span class="sxs-lookup"><span data-stu-id="015bc-162">Cyclical</span></span>  
 <span data-ttu-id="015bc-163">*cyclical* 內容類型表示資料行包含了代表循環之已排序集合的值。</span><span class="sxs-lookup"><span data-stu-id="015bc-163">The *cyclical* content type means that the column contains values that represent a cyclical ordered set.</span></span> <span data-ttu-id="015bc-164">例如，有編號的星期幾就是一個循環已排序集合，因為第 7 天後面就是第 1 天。</span><span class="sxs-lookup"><span data-stu-id="015bc-164">For example, the numbered days of the week is a cyclical ordered set, because day number one follows day number seven.</span></span>  
  
 <span data-ttu-id="015bc-165">在內容類型方面，循環資料行會被視為已排序且分隔。</span><span class="sxs-lookup"><span data-stu-id="015bc-165">Cyclical columns are considered both ordered and discrete in terms of content type.</span></span>  
  
 <span data-ttu-id="015bc-166">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中的所有資料採礦資料類型，都支援此內容類型。</span><span class="sxs-lookup"><span data-stu-id="015bc-166">This content type is supported by all the data mining data types in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="015bc-167">不過，大部分的演算法將循環值視為離散值，因此不會執行特殊處理。</span><span class="sxs-lookup"><span data-stu-id="015bc-167">However, most algorithms treat cyclical values as discrete values and do not perform special processing.</span></span>  
  
## <a name="ordered"></a><span data-ttu-id="015bc-168">訂購時間</span><span class="sxs-lookup"><span data-stu-id="015bc-168">Ordered</span></span>  
 <span data-ttu-id="015bc-169">*Ordered* 內容類型也表示包含了定義順序或次序之值的資料行。</span><span class="sxs-lookup"><span data-stu-id="015bc-169">The *Ordered* content type also indicates that the column contains values that define a sequence or order.</span></span> <span data-ttu-id="015bc-170">但是，在這個內容類型中，用於排序的值不表示該集合中各值之間的距離或大小關聯性。</span><span class="sxs-lookup"><span data-stu-id="015bc-170">However, in this content type the values used for ordering do not imply any distance or magnitude relationship between values in the set.</span></span> <span data-ttu-id="015bc-171">例如，若已排序屬性資料行包含有關技能層級的資訊，按照 1 到 5 的次序排序，則技能層級之間的距離沒有任何隱含資訊；技能層級 5 不一定比技能層級 1 好 5 倍。</span><span class="sxs-lookup"><span data-stu-id="015bc-171">For example, if an ordered attribute column contains information about skill levels in rank order from one to five, there is no implied information in the distance between skill levels; a skill level of five is not necessarily five times better than a skill level of one.</span></span>  
  
 <span data-ttu-id="015bc-172">在內容類型方面，已排序屬性資料行會被視為分隔。</span><span class="sxs-lookup"><span data-stu-id="015bc-172">Ordered attribute columns are considered to be discrete in terms of content type.</span></span>  
  
 <span data-ttu-id="015bc-173">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中的所有資料採礦資料類型，都支援此內容類型。</span><span class="sxs-lookup"><span data-stu-id="015bc-173">This content type is supported by all the data mining data types in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="015bc-174">不過，大部分的演算法將已排序的值視為離散值，因此不會執行特殊處理。</span><span class="sxs-lookup"><span data-stu-id="015bc-174">However, however, most algorithms treat ordered values as discrete values and do not perform special processing.</span></span>  
  
## <a name="classified"></a><span data-ttu-id="015bc-175">Classified</span><span class="sxs-lookup"><span data-stu-id="015bc-175">Classified</span></span>  
 <span data-ttu-id="015bc-176">除了前述常用於所有模型的內容類型之外，您可以使用分類資料行來定義某些資料類型的內容類型。</span><span class="sxs-lookup"><span data-stu-id="015bc-176">In addition to the preceding content types that are in common use with all models, for some data types you can use classified columns to define content types.</span></span> <span data-ttu-id="015bc-177">如需分類資料行的詳細資訊，請參閱[分類資料行 &#40;資料採礦&#41;](classified-columns-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="015bc-177">For more information about classified columns, see [Classified Columns &#40;Data Mining&#41;](classified-columns-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="015bc-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="015bc-178">See Also</span></span>  
 <span data-ttu-id="015bc-179">[DMX&#41;&#40;內容類型](/sql/dmx/content-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="015bc-179">[Content Types &#40;DMX&#41;](/sql/dmx/content-types-dmx) </span></span>  
 <span data-ttu-id="015bc-180">[資料類型 &#40;資料採礦&#41;](data-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="015bc-180">[Data Types &#40;Data Mining&#41;](data-types-data-mining.md) </span></span>  
 <span data-ttu-id="015bc-181">[DMX&#41;的資料類型 &#40;](/sql/dmx/data-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="015bc-181">[Data Types &#40;DMX&#41;](/sql/dmx/data-types-dmx) </span></span>  
 <span data-ttu-id="015bc-182">[變更採礦結構的屬性](change-the-properties-of-a-mining-structure.md) </span><span class="sxs-lookup"><span data-stu-id="015bc-182">[Change the Properties of a Mining Structure](change-the-properties-of-a-mining-structure.md) </span></span>  
 [<span data-ttu-id="015bc-183">採礦結構資料行</span><span class="sxs-lookup"><span data-stu-id="015bc-183">Mining Structure Columns</span></span>](mining-structure-columns.md)  
  
  
