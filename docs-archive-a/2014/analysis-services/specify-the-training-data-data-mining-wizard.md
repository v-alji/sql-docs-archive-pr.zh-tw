---
title: 指定定型資料 (資料採礦嚮導) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.specifytrainingdata.f1
ms.assetid: cb04deeb-0f89-4bba-b3f1-efccada16825
author: minewiskan
ms.author: owend
ms.openlocfilehash: 87a802256d287a3e8e9e7fb65bbd91687cb71a4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598543"
---
# <a name="specify-the-training-data-data-mining-wizard"></a><span data-ttu-id="18acd-102">指定培訓資料 (資料採礦精靈)</span><span class="sxs-lookup"><span data-stu-id="18acd-102">Specify the Training Data (Data Mining Wizard)</span></span>
  <span data-ttu-id="18acd-103">使用 [指定定型資料]\*\*\*\* 頁面，即可識別要在採礦結構中包含什麼資料行。</span><span class="sxs-lookup"><span data-stu-id="18acd-103">Use the **Specify the Training Data** page to identify which columns to include in the mining structure.</span></span> <span data-ttu-id="18acd-104">您可以選取要包含在結構中的資料行，即使不會在所有模型中使用也是如此。</span><span class="sxs-lookup"><span data-stu-id="18acd-104">You can select columns to include in the structure even if you do not use them in all models.</span></span> <span data-ttu-id="18acd-105">例如，如果想要從採礦模型鑽研資料行，則可將這些資料行包含在結構中 (而非模型中)。</span><span class="sxs-lookup"><span data-stu-id="18acd-105">For example, if you want to drill through to the columns from the mining model, you can include them in the structure but not in the model.</span></span>  
  
 <span data-ttu-id="18acd-106">包含在結構中的每個資料表都至少需要一個索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="18acd-106">At least one key column is required for each table that is included in the structure.</span></span> <span data-ttu-id="18acd-107">您挑選為索引鍵的資料行是根據資料表是案例資料表或巢狀資料表而定。</span><span class="sxs-lookup"><span data-stu-id="18acd-107">The column that you pick as the key depends on whether the table is a case table or a nested table.</span></span> <span data-ttu-id="18acd-108">如果資料表是巢狀資料表，則索引鍵通常是可預測的資料行，而不是關聯的外部索引鍵。</span><span class="sxs-lookup"><span data-stu-id="18acd-108">If the table is a nested table, the key is often also the predictable column, not the relational foreign key.</span></span> <span data-ttu-id="18acd-109">若要深入了解巢狀索引鍵，請參閱[巢狀資料表 &#40;Analysis Services - 資料採礦&#41;](data-mining/nested-tables-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="18acd-109">To learn about nested keys, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](data-mining/nested-tables-analysis-services-data-mining.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18acd-110">不同的採礦演算法會以不同的方式使用索引鍵。</span><span class="sxs-lookup"><span data-stu-id="18acd-110">Different mining algorithms use keys differently.</span></span> <span data-ttu-id="18acd-111">若要深入了解不同種類的索引鍵，請參閱[內容類型 &#40;資料採礦&#41;](data-mining/content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="18acd-111">To learn about the different kinds of keys, see [Content Types &#40;Data Mining&#41;](data-mining/content-types-data-mining.md).</span></span>  
  
 <span data-ttu-id="18acd-112">**如需詳細資訊，請參閱** [採礦結構 &#40;Analysis Services - 資料採礦&#41;](data-mining/mining-structures-analysis-services-data-mining.md)、[採礦模型資料行](data-mining/mining-model-columns.md)、[資料採礦精靈 &#40;Analysis Services - 資料採礦&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md)、[建立關聯式採礦結構](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="18acd-112">**For More Information:** [Mining Structures &#40;Analysis Services - Data Mining&#41;](data-mining/mining-structures-analysis-services-data-mining.md), [Mining Model Columns](data-mining/mining-model-columns.md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="18acd-113">選項</span><span class="sxs-lookup"><span data-stu-id="18acd-113">Options</span></span>  
 <span data-ttu-id="18acd-114">**資料表/資料行**</span><span class="sxs-lookup"><span data-stu-id="18acd-114">**Tables/Columns**</span></span>  
 <span data-ttu-id="18acd-115">顯示在精靈的上一頁上所選取的資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="18acd-115">Displays the tables and columns that you selected on the previous page of the wizard.</span></span>  
  
 **\<check box>**  
 <span data-ttu-id="18acd-116">選取要包含在採礦結構中的資料行。</span><span class="sxs-lookup"><span data-stu-id="18acd-116">Select the columns to include in the mining structure.</span></span>  
  
 <span data-ttu-id="18acd-117">如果資料來源包含巢狀資料表或多個檢視，請展開資料行清單來檢視巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="18acd-117">If your data source includes nested tables or multiple views, expand the column list to view the nested tables.</span></span>  
  
 <span data-ttu-id="18acd-118">**索引鍵**</span><span class="sxs-lookup"><span data-stu-id="18acd-118">**Key**</span></span>  
 <span data-ttu-id="18acd-119">選取即可使用資料行作為資料的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="18acd-119">Select to use the column as a unique identifier for the data.</span></span>  
  
 <span data-ttu-id="18acd-120">對案例資料表而言，索引鍵通常是唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="18acd-120">For a case table, the key is usually the unique identifier.</span></span>  
  
 <span data-ttu-id="18acd-121">對巢狀資料表而言，[索引鍵]\*\*\*\* 指出相關聯案例內容中之資料列的識別碼。</span><span class="sxs-lookup"><span data-stu-id="18acd-121">For nested table, the **Key** indicates the identifier of a row in the context of the associated case.</span></span>  
  
 <span data-ttu-id="18acd-122">**輸入**</span><span class="sxs-lookup"><span data-stu-id="18acd-122">**Input**</span></span>  
 <span data-ttu-id="18acd-123">選取即可在建立預測時使用資料行。</span><span class="sxs-lookup"><span data-stu-id="18acd-123">Select to use the column in creating predictions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18acd-124">只有在建立採礦模型時同時建立採礦結構，才可以使用這個資料行。</span><span class="sxs-lookup"><span data-stu-id="18acd-124">This column is only available when you are creating a mining model together with the mining structure.</span></span>  
  
 <span data-ttu-id="18acd-125">**可預測**</span><span class="sxs-lookup"><span data-stu-id="18acd-125">**Predictable**</span></span>  
 <span data-ttu-id="18acd-126">選取即可啟用依據其他未來的輸入，來預測資料表或資料行。</span><span class="sxs-lookup"><span data-stu-id="18acd-126">Select to enable the table or column to be predicted based on additional future input.</span></span>  
  
 <span data-ttu-id="18acd-127">如果您也將巢狀資料表標示為可預測，則整個巢狀資料表會變成可預測。</span><span class="sxs-lookup"><span data-stu-id="18acd-127">If you also mark a nested table as predictable, the whole nested table becomes predictable.</span></span> <span data-ttu-id="18acd-128">如果巢狀資料表中沒有資料行標示為輸入或可預測，巢狀資料表就會出現在採礦結構中，但是在模型中會被忽略。</span><span class="sxs-lookup"><span data-stu-id="18acd-128">If no columns in the nested table are marked as input or predictable, the nested table will appear in the mining structure, but will be ignored in the model.</span></span>  
  
 <span data-ttu-id="18acd-129">**注意** ：只有在建立採礦模型時同時建立採礦結構，才可以使用這個資料行。</span><span class="sxs-lookup"><span data-stu-id="18acd-129">**Note** This column is only available when you are creating a mining model together with the mining structure.</span></span>  
  
 <span data-ttu-id="18acd-130">**建議**</span><span class="sxs-lookup"><span data-stu-id="18acd-130">**Suggest**</span></span>  
 <span data-ttu-id="18acd-131">按一下即可開啟 [建議相關資料行]\*\*\*\* 對話方塊，它會對採樣資料進行分析，來識別與依據 Entropy 所選取 [可預測]\*\*\*\* 資料行展現最大關聯性的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="18acd-131">Click to open the **Suggest Related Columns** dialog box, which performs an analysis on a sample of data to identify input columns that show the greatest relationship to the selected **Predictable** column based on entropy.</span></span> <span data-ttu-id="18acd-132">此分析也適用於以 OLAP 來源為基礎的巢狀資料表資料行或採礦結構。</span><span class="sxs-lookup"><span data-stu-id="18acd-132">This analysis also applies to nested table columns or mining structures that are based on OLAP sources.</span></span>  
  
 <span data-ttu-id="18acd-133">**附註** 只有在建立採礦模型時同時建立採礦結構，才可以使用這個資料行。</span><span class="sxs-lookup"><span data-stu-id="18acd-133">**Note** This column only available when you are creating a mining model together with the mining structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18acd-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18acd-134">See Also</span></span>  
 <span data-ttu-id="18acd-135">[資料採礦嚮導 F1 說明 &#40;Analysis Services-資料採礦&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="18acd-135">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="18acd-136">[建議相關資料行 &#40;Data 採集 Wizard&#41;](suggest-related-columns-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="18acd-136">[Suggest Related Columns &#40;Data Mining Wizard&#41;](suggest-related-columns-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="18acd-137">[指定資料表類型 &#40;資料採礦嚮導&#41;](specify-table-types-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="18acd-137">[Specify Table Types &#40;Data Mining Wizard&#41;](specify-table-types-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="18acd-138">[指定資料行的內容和資料類型 &#40;[Data] [Wizard]&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md)</span><span class="sxs-lookup"><span data-stu-id="18acd-138">[Specify the Column's Content and Data Type &#40;Data Mining Wizard&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md)</span></span>  
  
  
