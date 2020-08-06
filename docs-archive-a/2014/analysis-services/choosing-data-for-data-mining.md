---
title: 選擇資料獲取的資料 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content type [data mining]
- nested tables
- key [data mining]
- continuous values
- key sequence [data mining]
- table data type
- key time [data mining]
- discrete values
- discretized
ms.assetid: 7c72d80e-913c-4bbe-b258-444294a78838
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b655e344bd9976c30781efb7be41a3fc602174d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593078"
---
# <a name="choosing-data-for-data-mining"></a><span data-ttu-id="94ddb-102">選擇要進行資料採礦的資料</span><span class="sxs-lookup"><span data-stu-id="94ddb-102">Choosing Data for Data Mining</span></span>
  <span data-ttu-id="94ddb-103">當您開始進行資料採礦時，您可能會問「我需要多少資料？」</span><span class="sxs-lookup"><span data-stu-id="94ddb-103">As you start data mining, you might ask "How much data do I need?"</span></span> <span data-ttu-id="94ddb-104">或「在清除或格式化資料時，是否有任何特殊需求？」</span><span class="sxs-lookup"><span data-stu-id="94ddb-104">or "Are there any special requirements I should know about when cleaning or formatting my data?"</span></span>  
  
 <span data-ttu-id="94ddb-105">特別是，資料採礦的新手經常會遇到 Excel 資料的問題，例如需要在資料行內持續地格式化資料、清除遺漏值或分類收納數字。</span><span class="sxs-lookup"><span data-stu-id="94ddb-105">In particular, people new to data mining often run into problems with Excel data, such as needing to format data consistently within columns, cleaning up missing values, or binning numbers.</span></span> <span data-ttu-id="94ddb-106">本章節也會列出特定模型種類的資料需求。</span><span class="sxs-lookup"><span data-stu-id="94ddb-106">This section also lists data requirements for specific kinds of models.</span></span>  
  
 [<span data-ttu-id="94ddb-107">選擇資料</span><span class="sxs-lookup"><span data-stu-id="94ddb-107">Choosing Data</span></span>](#bkmk_ChoosingData)  
  
 [<span data-ttu-id="94ddb-108">常見資料問題</span><span class="sxs-lookup"><span data-stu-id="94ddb-108">Common Data Problems</span></span>](#bkmk_CommonDataProblems)  
  
 [<span data-ttu-id="94ddb-109">其他資料需求</span><span class="sxs-lookup"><span data-stu-id="94ddb-109">Other Data Requirements</span></span>](#bkmk_OtherRequirements)  
  
##  <a name="choosing-data"></a><a name="bkmk_ChoosingData"></a><span data-ttu-id="94ddb-110">選擇資料</span><span class="sxs-lookup"><span data-stu-id="94ddb-110">Choosing Data</span></span>  
 <span data-ttu-id="94ddb-111">選取用於分析的資料或許是資料採礦程序中最重要的部分，甚至比選取演算法還重要。</span><span class="sxs-lookup"><span data-stu-id="94ddb-111">Selection of the data used for analysis is perhaps the most important part of the data mining process, more so even than the selection of an algorithm.</span></span> <span data-ttu-id="94ddb-112">這是因為資料採礦通常不是假設導向，而是資料導向。</span><span class="sxs-lookup"><span data-stu-id="94ddb-112">The reason is that data mining is generally not hypothesis-driven, but data-driven.</span></span> <span data-ttu-id="94ddb-113">資料採礦可能會取用資料並探索新的相互關聯性 (或者未能發現任何模式)，而不像傳統統計模型可能會事先選取及測試變數。</span><span class="sxs-lookup"><span data-stu-id="94ddb-113">Rather than select and test variables in advance, as you might with traditional statistical modeling, data mining can take data and discover new correlations (or fail to discover any patterns at all).</span></span> <span data-ttu-id="94ddb-114">資料的品質和數量對於結果會有重大的影響。</span><span class="sxs-lookup"><span data-stu-id="94ddb-114">The quality and amount of your data can have a significant effect on results.</span></span>  
  
 <span data-ttu-id="94ddb-115">一般而言，請觀察以下規則：</span><span class="sxs-lookup"><span data-stu-id="94ddb-115">In general, observe the following rules:</span></span>  
  
-   <span data-ttu-id="94ddb-116">盡量取得更多乾淨的資料。</span><span class="sxs-lookup"><span data-stu-id="94ddb-116">Get as much clean data as possible.</span></span>  
  
-   <span data-ttu-id="94ddb-117">在您嘗試任何模型之前，請先執行資料分析。</span><span class="sxs-lookup"><span data-stu-id="94ddb-117">Conduct data profiling before you try any models.</span></span> <span data-ttu-id="94ddb-118">您必須先了解資料，然後才可以從資料衍生意義。</span><span class="sxs-lookup"><span data-stu-id="94ddb-118">You need to understand your data before you can derive meaning from it.</span></span> <span data-ttu-id="94ddb-119">最低限度：</span><span class="sxs-lookup"><span data-stu-id="94ddb-119">At minimum:</span></span>  
  
    1.  <span data-ttu-id="94ddb-120">使用增益集中的工具來尋找您的最大值與最小值、最常見的值和平均值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-120">Use the tools in the add-ins to find your maximum and minimum values, the most common values, and average values.</span></span>  
  
    2.  <span data-ttu-id="94ddb-121">填入遺漏的值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-121">Fill in missing values.</span></span> <span data-ttu-id="94ddb-122">增益集 (以及某些演算法) 會提供工具來輸入遺漏的值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-122">The add-ins (as well as some algorithms) provide tools for imputing missing values.</span></span>  
  
    3.  <span data-ttu-id="94ddb-123">盡可能更正不正確的資料。</span><span class="sxs-lookup"><span data-stu-id="94ddb-123">Correct bad data whenever possible.</span></span> <span data-ttu-id="94ddb-124">資料採礦專案通常會當做新資料品質計劃的推動力量。</span><span class="sxs-lookup"><span data-stu-id="94ddb-124">Data mining projects often serve as the impetus for new data quality initiatives.</span></span>  
  
-   <span data-ttu-id="94ddb-125">嘗試建立測試模型，並以此方式尋找資料問題。</span><span class="sxs-lookup"><span data-stu-id="94ddb-125">Try building a test model and find data problems that way.</span></span> <span data-ttu-id="94ddb-126">例如，當您查看結果時，您可能會發現銷售預測是根據貨幣轉換錯誤而產生的異常資料。</span><span class="sxs-lookup"><span data-stu-id="94ddb-126">As you look at the results, you might find, for example, that sales projections are based on anomalous data due to a currency conversion error.</span></span>  
  
-   <span data-ttu-id="94ddb-127">嘗試將資料轉換成不同格式，或是嘗試儲存數字。</span><span class="sxs-lookup"><span data-stu-id="94ddb-127">Try casting your data into different formats, or try bucketing numbers.</span></span> <span data-ttu-id="94ddb-128">當轉換資料時，通常會出現模式。</span><span class="sxs-lookup"><span data-stu-id="94ddb-128">Patterns often emerge when data is transformed.</span></span>  
  
     <span data-ttu-id="94ddb-129">例如，撥接中心的服務等級可能會受到星期幾所影響，如果您只使用日期時間值就不會看到這個狀況。</span><span class="sxs-lookup"><span data-stu-id="94ddb-129">For example, the service level at the call center might be affected by the day of the week, which you would not see if you were using only the datetime values.</span></span> <span data-ttu-id="94ddb-130">以 10 天的循環週期產生的預測可能會優於以每週或每天為單位的預測。</span><span class="sxs-lookup"><span data-stu-id="94ddb-130">Forecasts might be better when generated on 10-day cycles rather than weekly or daily units.</span></span>  
  
-   <span data-ttu-id="94ddb-131">將數字放在適當的分類收納中，以減少可能用於分析的值數目。</span><span class="sxs-lookup"><span data-stu-id="94ddb-131">Put numbers in appropriate bins, to reduce the number of possible values for analysis.</span></span>  
  
-   <span data-ttu-id="94ddb-132">建立資料的多個版本，並建立多個模型。</span><span class="sxs-lookup"><span data-stu-id="94ddb-132">Create multiple versions of your data and build multiple models.</span></span>  
  
 <span data-ttu-id="94ddb-133">如需有關如何選取、修改和查看資料的其他秘訣，請參閱[資料採礦準備的檢查清單](checklist-of-preparation-for-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="94ddb-133">For additional tips on how to select, modify, and review data, see [Checklist of Preparation for Data Mining](checklist-of-preparation-for-data-mining.md).</span></span>  
  
### <a name="how-much-data-do-i-need"></a><span data-ttu-id="94ddb-134">我需要多少資料？</span><span class="sxs-lookup"><span data-stu-id="94ddb-134">How Much Data Do I Need?</span></span>  
 <span data-ttu-id="94ddb-135">基本原則如下：最簡單的模型類型和案例絕對不要擁有少於 50-100 個資料列的資料。</span><span class="sxs-lookup"><span data-stu-id="94ddb-135">A rule of thumb is to never have less than 50-100 rows of data for the simplest models types and scenarios.</span></span> <span data-ttu-id="94ddb-136">例如，如果您使用貝氏機率分類模型預測單一屬性，而且資料集的格式正確，您或許可以使用 50-100 個資料列的資料產生相當精確的預測。</span><span class="sxs-lookup"><span data-stu-id="94ddb-136">For example, if you are predicting a single attribute using a Naïve Bayes model and the data set is well-formed, you might be able to generate fairly accurate predictions using 50-100 rows of data.</span></span>  
  
 <span data-ttu-id="94ddb-137">對於關聯模型，您通常需要更多的資料-如果您要分析許多屬性（例如產品之間的關聯），則會有一千個數據列可能無法滿足。</span><span class="sxs-lookup"><span data-stu-id="94ddb-137">For association models, you typically need much more data - a thousand rows might not suffice if you are analyzing many attributes, such as associations among products.</span></span> <span data-ttu-id="94ddb-138">如果您的資料集太大或太小，您有時可以將資料列摺疊到類別目錄中來獲得較好的結果。</span><span class="sxs-lookup"><span data-stu-id="94ddb-138">If your data set is too big or too small, you can sometimes achieve better results by collapsing rows into categories.</span></span> <span data-ttu-id="94ddb-139">例如，您可以分類產品，而不用分析個別產品之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="94ddb-139">For example, instead of analyzing associations among individual products, you could categorize the products.</span></span>  
  
 <span data-ttu-id="94ddb-140">如果您有大小適當的資料集，請將焦點放在資料品質，而不是增加更多的資料。</span><span class="sxs-lookup"><span data-stu-id="94ddb-140">If you have a data set of a reasonable size, focus more on data quality rather than adding more and more data.</span></span> <span data-ttu-id="94ddb-141">在某個點之後，統計上有效的所有模式都將會被發現，而增加更多資料並不會改善其有效性。</span><span class="sxs-lookup"><span data-stu-id="94ddb-141">After a point, all the patterns that are statistically valid will have been found, and adding more data does not improve their validity.</span></span> <span data-ttu-id="94ddb-142">相反地，增加更多資料有時可能會導入意外的相互關聯性。</span><span class="sxs-lookup"><span data-stu-id="94ddb-142">Conversely, as you add more data sometimes you can introduce accidental correlations.</span></span>  
  
### <a name="discrete-vs-continuous-numbers"></a><span data-ttu-id="94ddb-143">離散與連續數位</span><span class="sxs-lookup"><span data-stu-id="94ddb-143">Discrete vs. Continuous Numbers</span></span>  
 <span data-ttu-id="94ddb-144">*離散*資料行包含有限數量的值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-144">A *discrete* column contains a finite number of values.</span></span> <span data-ttu-id="94ddb-145">例如，文字一定會被視為離散值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-145">For example, text is always treated as discrete values.</span></span>  
  
 <span data-ttu-id="94ddb-146">離散值有一些重要的屬性。</span><span class="sxs-lookup"><span data-stu-id="94ddb-146">There are some important attributes to discrete values.</span></span> <span data-ttu-id="94ddb-147">例如，如果您將數字視為離散，數字之間就不會隱含任何順序，您也無法平均數字或加總數字。</span><span class="sxs-lookup"><span data-stu-id="94ddb-147">For example, if you treat numbers as discrete, no order is implied among them, and you cannot average or sum the numbers.</span></span> <span data-ttu-id="94ddb-148">電話區域碼是很好的離散數值資料範例，您絕對不會使用這些代碼執行數學運算。</span><span class="sxs-lookup"><span data-stu-id="94ddb-148">Telephone area codes are a good example of discrete numeric data that you would never use to perform mathematical operations.</span></span>  
  
 <span data-ttu-id="94ddb-149">離散值有時稱為類別值，因為您可以依類別來分組資料，但您無法將排列成無限數列的數字分組。</span><span class="sxs-lookup"><span data-stu-id="94ddb-149">Discrete values are sometimes referred to as categorical values, because you can group a set of data by them, whereas you cannot with numbers arranged in an infinite series.</span></span>  
  
 <span data-ttu-id="94ddb-150">如果值是明確分隔的，並且不可能有小數值或是小數值不實用，您也可能決定將這些數字視為離散值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-150">You might also decide to treat numbers as discrete when the values are clearly separated, and there is no possibility of fractional values, or fractional values are not useful.</span></span>  
  
 <span data-ttu-id="94ddb-151">*連續*數值資料可以包含無限數目的小數值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-151">*Continuous* numeric data can contain an infinite number of fractional values.</span></span> <span data-ttu-id="94ddb-152">收入資料行就是連續屬性資料行的一個範例。</span><span class="sxs-lookup"><span data-stu-id="94ddb-152">An income column is an example of a continuous attribute column.</span></span> <span data-ttu-id="94ddb-153">如果您指定某資料行為數值，則該資料行中的每一個值都必須是數字，除了 Null。</span><span class="sxs-lookup"><span data-stu-id="94ddb-153">If you specify that a column is numeric, every value in that column must be a number, except for nulls.</span></span> <span data-ttu-id="94ddb-154">請注意，在 Excel 中，時間戳記以及可轉換成 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料類型的任何其他日期時間表示法都算是數值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-154">Note that in Excel, timestamps and any other date-time representation that can be converted to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data type can be considered.</span></span>  
  
 <span data-ttu-id="94ddb-155">**將數字轉換成類別變數**</span><span class="sxs-lookup"><span data-stu-id="94ddb-155">**Converting Numbers to Categorical Variables**</span></span>  
  
 <span data-ttu-id="94ddb-156">並不是說資料行包含數字就表示您應該將它們視為連續的數字。</span><span class="sxs-lookup"><span data-stu-id="94ddb-156">Just because a column contains numbers does not mean that you should treat them as continuous numbers.</span></span> <span data-ttu-id="94ddb-157">*離散*化提供許多分析的優點。</span><span class="sxs-lookup"><span data-stu-id="94ddb-157">*Discretization* provides many advantages for analysis.</span></span> <span data-ttu-id="94ddb-158">其中一個優點是減少問題空間。</span><span class="sxs-lookup"><span data-stu-id="94ddb-158">One is that the problem space is reduced.</span></span> <span data-ttu-id="94ddb-159">另一個優點如下：有時數字並不是呈現結果的適當方式。</span><span class="sxs-lookup"><span data-stu-id="94ddb-159">Another is that sometimes numbers are not the appropriate way to express a result.</span></span>  
  
 <span data-ttu-id="94ddb-160">例如，每戶家庭的孩童數目可以被視為連續或離散值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-160">For example, the number of children per household can be treated either as a continuous or discrete value.</span></span> <span data-ttu-id="94ddb-161">因為一個家庭不可能有 2.5 個小孩，而且有 3 個或更多小孩的家庭與有 2 個小孩的家庭可能會有非常不同的行為模式，所以將這個數字視為一個類別目錄可能會得到更好的結果。</span><span class="sxs-lookup"><span data-stu-id="94ddb-161">Since it is not possible to have 2.5 children in the household, and households with 3 or more children can behave very differently from households with 2 children, you might get better results by treating this number as a category.</span></span> <span data-ttu-id="94ddb-162">不過，如果您要建立迴歸模型或是需要平均值 (例如每個家庭 1.357 個小孩)，您就會使用連續數字資料類型。</span><span class="sxs-lookup"><span data-stu-id="94ddb-162">However, if you are building a regression model or otherwise require an average (such as 1.357 children per household), then you would use a continuous number data type.</span></span>  
  
 <span data-ttu-id="94ddb-163">建立具有連續資料的採礦模型，稍後便不可能將資料行視為離散的。</span><span class="sxs-lookup"><span data-stu-id="94ddb-163">It is not possible to create a mining model that has continuous data and then treat the column as discrete later.</span></span> <span data-ttu-id="94ddb-164">這兩個資料集必須以不同方式處理，而且在後端要當做個別的採礦結構來處理。</span><span class="sxs-lookup"><span data-stu-id="94ddb-164">The two data sets must be processed differently and are handled on the backend as separate mining structures.</span></span> <span data-ttu-id="94ddb-165">如果您不確定處理資料的正確方式為何，您應該建立以不同方式處理資料的個別模型。</span><span class="sxs-lookup"><span data-stu-id="94ddb-165">If you are unsure of the right way to handle the data, you should create separate models that handle the data differently.</span></span> <span data-ttu-id="94ddb-166">在任何情況下，這都是取得資料的不同觀點以及可能的不同結果的好方法。</span><span class="sxs-lookup"><span data-stu-id="94ddb-166">In any case, this is a good way to get a different perspective on your data, and perhaps different results.</span></span>  
  
 <span data-ttu-id="94ddb-167">**將數字轉換成文字**</span><span class="sxs-lookup"><span data-stu-id="94ddb-167">**Converting Numbers to Text**</span></span>  
  
 <span data-ttu-id="94ddb-168">應該是離散的值 (如男性和女性) 常常會以數值資料表示，例如使用標籤 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="94ddb-168">Very often values that should be discrete, such as Male and Female, are represented as numeric data, using the labels 1 and 2.</span></span> <span data-ttu-id="94ddb-169">一般來說，執行這樣的編碼是為了簡化資料輸入，或是為了節省資料庫中的儲存空間，但是這樣的編碼也可能會導致有關這些值本質或意義上的模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="94ddb-169">Typically this coding is performed to simplify data entry, or to save storage space in a database, but the coding can lead to ambiguity about the nature or meaning of the values.</span></span> <span data-ttu-id="94ddb-170">此外，因為離散的值會儲存成數字，所以當您在應用程式之間移動資料時，您可能會遇到資料類型轉換的錯誤，而且這些值可能會被計算或是視為連續的值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-170">Moreover, because discrete values are stored as numbers, as you move data between applications you may encounter data type conversion errors, and the values might be calculated or otherwise treated as continuous.</span></span> <span data-ttu-id="94ddb-171">為了避免這類問題，在開始資料採礦之前，您應該將數值標籤轉換回離散文字標籤。</span><span class="sxs-lookup"><span data-stu-id="94ddb-171">To prevent such problems, before beginning data mining, you should convert the numeric labels back to discrete text labels.</span></span>  
  
 <span data-ttu-id="94ddb-172">**分類收納數字**</span><span class="sxs-lookup"><span data-stu-id="94ddb-172">**Binning Numbers**</span></span>  
  
 <span data-ttu-id="94ddb-173">雖然原則中的所有數位都是無限的，因此，當您將資訊模型化時，您可能會發現*離散化*或將可用的值設為 [ *bin* ] 會更有效率。</span><span class="sxs-lookup"><span data-stu-id="94ddb-173">Although all numbers in principle are infinite and are therefore continuous, when you are modeling information you might find it more effective to *discretize* or *bin* the available values.</span></span>  
  
 <span data-ttu-id="94ddb-174">您有許多方式可以分類收納資料：</span><span class="sxs-lookup"><span data-stu-id="94ddb-174">You can bin data in many ways:</span></span>  
  
-   <span data-ttu-id="94ddb-175">指定數量有限的貯體，然後讓演算法排序值放入貯體。</span><span class="sxs-lookup"><span data-stu-id="94ddb-175">Specify a finite number of buckets and let the algorithm sort the values into buckets.</span></span>  
  
-   <span data-ttu-id="94ddb-176">您可以建立幾個具有商業意義或比較容易使用的群組，自己先將它們分組。</span><span class="sxs-lookup"><span data-stu-id="94ddb-176">Pre-group them yourself, by creating some set of groupings that either has business meaning or is easier to work with.</span></span> <span data-ttu-id="94ddb-177">使用這種方法時，通常會遺失值的真正散發意義，不過，其範圍對使用者而言比較容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="94ddb-177">With this approach, you often miss the true distribution of values, but the ranges are easier for users to read.</span></span>  
  
-   <span data-ttu-id="94ddb-178">讓演算法決定貯體的最佳數量和值的散發。</span><span class="sxs-lookup"><span data-stu-id="94ddb-178">Let the algorithm determine both the optimum number of buckets and the distribution of values.</span></span> <span data-ttu-id="94ddb-179">這是大部分工具中的預設值，但您可以在 [**資料採礦**] 工具列的 [嚮導] 中覆寫這些預設值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-179">This is the default in most tools, but you can override these defaults in the **Data Mining** toolbar wizards.</span></span>  
  
-   <span data-ttu-id="94ddb-180">將值逼近到中央平均值或代表值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-180">Approximating values to a central mean or representative value.</span></span>  
  
##  <a name="common-data-problems"></a><a name="bkmk_CommonDataProblems"></a><span data-ttu-id="94ddb-181">常見的資料問題</span><span class="sxs-lookup"><span data-stu-id="94ddb-181">Common Data Problems</span></span>  
  
### <a name="excel-number-formats"></a><span data-ttu-id="94ddb-182">Excel 數字格式</span><span class="sxs-lookup"><span data-stu-id="94ddb-182">Excel Number Formats</span></span>  
 <span data-ttu-id="94ddb-183">Excel 是一種容易使用的工具，因為它是容許的，您幾乎可以在任何地方放置任何類型的資料！</span><span class="sxs-lookup"><span data-stu-id="94ddb-183">Excel is an easy tool to use because it is forgiving - you can put just about any kind of data anywhere!</span></span> <span data-ttu-id="94ddb-184">不過，在開始尋找模式和分析相互關聯性之前，您需要給資料加上一些結構或條件約束。</span><span class="sxs-lookup"><span data-stu-id="94ddb-184">However, before you begin to look for patterns and analyze correlations, you need to impose some structure or constraints on your data.</span></span>  
  
 <span data-ttu-id="94ddb-185">根據預設，當您將數值資料匯入至 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 時，數字會以含兩個小數位數的十進位格式儲存。</span><span class="sxs-lookup"><span data-stu-id="94ddb-185">By default, when you import numeric data into [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel, the numbers are stored in a decimal format with two decimal places.</span></span> <span data-ttu-id="94ddb-186">如果這不是適當的數字格式，您應該將它變更成另一個數值格式，或變更小數位數。</span><span class="sxs-lookup"><span data-stu-id="94ddb-186">If this is not an appropriate number format, you should change to another numeric format, or change the number of decimal places.</span></span>  
  
 <span data-ttu-id="94ddb-187">其中一個選項是使用重定卷[標工具來](relabel-sql-server-data-mining-add-ins.md)變更數位的顯示或分組方式。</span><span class="sxs-lookup"><span data-stu-id="94ddb-187">One option is to use the [Relabel](relabel-sql-server-data-mining-add-ins.md) tool to change the way that numbers are displayed or grouped.</span></span>  
  
 <span data-ttu-id="94ddb-188">不過，如果您的資料太複雜而無法使用重新**標記**工具處理，您可以使用 Excel 中的數值函數將資料轉換成離散範圍，將該結果儲存到個別的資料行，然後改用離散化資料行進行分類。</span><span class="sxs-lookup"><span data-stu-id="94ddb-188">However, if your data is too complex to process with the **Relabel** tool, you can use the numeric functions in Excel to convert your data to discrete ranges, save that result into a separate column, and then use the discretized column for classification instead.</span></span>  
  
 <span data-ttu-id="94ddb-189">例如，如果您要分析賽跑結果，並想要以分鐘為單位，將跑者依其抵達終點的時間來加以分組，則可以藉由四捨五入法取最接近的分鐘值，並將該捨入值儲存到新資料行。</span><span class="sxs-lookup"><span data-stu-id="94ddb-189">For example, if you are analyzing race results and want to group racers by their finish times in minutes, you can round up to the nearest minute and save that rounded value to a new column.</span></span> <span data-ttu-id="94ddb-190">也可以使用 `MINUTE` 函數只擷取分鐘值，然後將該值儲存到新資料行供分析使用。</span><span class="sxs-lookup"><span data-stu-id="94ddb-190">You could also extract only the minute value by using the `MINUTE` function, and then save that value to a new column for use in analysis.</span></span>  
  
### <a name="discretizing-numbers-and-dates-in-excel"></a><span data-ttu-id="94ddb-191">在 Excel 中離散化數字和日期</span><span class="sxs-lookup"><span data-stu-id="94ddb-191">Discretizing Numbers and Dates in Excel</span></span>  
 <span data-ttu-id="94ddb-192">根據預設，Excel 中的數值資料會儲存為 `Double`。</span><span class="sxs-lookup"><span data-stu-id="94ddb-192">By default, numeric data in Excel is stored as a `Double`.</span></span> <span data-ttu-id="94ddb-193">日期和時間也是以數值格式儲存。</span><span class="sxs-lookup"><span data-stu-id="94ddb-193">Dates and times also are stored in a numeric format.</span></span> <span data-ttu-id="94ddb-194">如果您為了資料採礦而需要離散化數字或日期，則應該在建立資料採礦模型之前加入新的資料行，或預先將日期和數字轉換成另一個格式。</span><span class="sxs-lookup"><span data-stu-id="94ddb-194">If you need to discretize numbers or dates for data mining, you should add new columns before you build your data mining model, or convert dates and numbers to another format beforehand.</span></span>  
  
### <a name="scientific-number-formats"></a><span data-ttu-id="94ddb-195">科學數字格式</span><span class="sxs-lookup"><span data-stu-id="94ddb-195">Scientific Number Formats</span></span>  
 <span data-ttu-id="94ddb-196">資料採礦工具通常會以科學記號標記法 (代表非常大或非常小的數字) 輸出機率。</span><span class="sxs-lookup"><span data-stu-id="94ddb-196">The data mining tools often output probabilities in scientific notation, to represent numbers that are very large or very small.</span></span> <span data-ttu-id="94ddb-197">如果您不熟悉科學記號標記法，只要變更資料格的格式，就可以使用其他格式輕鬆顯示這些數字。</span><span class="sxs-lookup"><span data-stu-id="94ddb-197">If you are not familiar with scientific notation, you can easily display these numbers in another format by simply changing the cell formatting.</span></span>  
  
##### <a name="to-change-scientific-notation-to-a-decimal-numeric-format"></a><span data-ttu-id="94ddb-198">將科學記號標記法變更為十進位數值格式</span><span class="sxs-lookup"><span data-stu-id="94ddb-198">To change scientific notation to a decimal numeric format</span></span>  
  
1.  <span data-ttu-id="94ddb-199">在 Excel 資料表中，反白顯示包含使用科學記號標記法之數字的資料行或資料格。</span><span class="sxs-lookup"><span data-stu-id="94ddb-199">In the Excel data table, highlight the column or cell that contains the number in scientific notation.</span></span>  
  
2.  <span data-ttu-id="94ddb-200">以滑鼠右鍵按一下，然後從快捷方式功能表選取 [**格式化儲存格**]。</span><span class="sxs-lookup"><span data-stu-id="94ddb-200">Right-click and select **Format cells** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="94ddb-201">在 [**類別**] 清單中，選取 [**數位**]。</span><span class="sxs-lookup"><span data-stu-id="94ddb-201">In the **Category** list, select **Number**.</span></span>  
  
4.  <span data-ttu-id="94ddb-202">增加小數位數。</span><span class="sxs-lookup"><span data-stu-id="94ddb-202">Increase the number of decimal places.</span></span> <span data-ttu-id="94ddb-203">以科學記號標記法表示的機率通常非常小。</span><span class="sxs-lookup"><span data-stu-id="94ddb-203">A probability that is represented in scientific notation is generally very small.</span></span>  
  
     <span data-ttu-id="94ddb-204">只有數字的顯示會變更，基礎值則不會變更。</span><span class="sxs-lookup"><span data-stu-id="94ddb-204">Only the display of the number is changed, not the underlying value.</span></span>  
  
### <a name="working-with-dates-and-times"></a><span data-ttu-id="94ddb-205">處理日期和時間</span><span class="sxs-lookup"><span data-stu-id="94ddb-205">Working with Dates and Times</span></span>  
 <span data-ttu-id="94ddb-206">當您的 Excel 資料表中有日期並且使用此資料行做為輸入或預測時，根據日期或時間資訊的格式，可能會發生未預期的結果。</span><span class="sxs-lookup"><span data-stu-id="94ddb-206">When you have dates in an Excel table and use the column either as input or for prediction, you might receive unexpected results, depending on how the date or time information is formatted.</span></span> <span data-ttu-id="94ddb-207">例如，當您使用 [偵測**類別目錄**] 或 [**分類**]，並包含包含日期的資料行時，會將日期分類為具有許多小數位數的數值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-207">For example, when you use **Detect Categories** or **Classify** and include a column that contains dates, the dates are categorized as numbers with many decimal places.</span></span> <span data-ttu-id="94ddb-208">這不是錯誤，而是基礎資料的正確表示方式。</span><span class="sxs-lookup"><span data-stu-id="94ddb-208">This is not an error; it is an accurate representation of the underlying data.</span></span> <span data-ttu-id="94ddb-209">資料採礦演算法會使用基礎儲存格式，而非顯示格式。</span><span class="sxs-lookup"><span data-stu-id="94ddb-209">The data mining algorithm works with the underlying storage format, not the display format.</span></span>  
  
 <span data-ttu-id="94ddb-210">如果您在使用日期有困難，而且要使用月或日之類的常識群組來分析日期，可以使用 Excel 的 DATE 函數，將年、月或日擷取至另一個資料行，然後改用此資料行進行分類。</span><span class="sxs-lookup"><span data-stu-id="94ddb-210">If you have difficulty working with dates and want to analyze dates using such common-sense groupings as month or day, you can use the DATE functions in Excel to extract the year, month, or day into a separate column and then use that column for classification instead.</span></span>  
  
##  <a name="other-data-requirements"></a><a name="bkmk_OtherRequirements"></a><span data-ttu-id="94ddb-211">其他資料需求</span><span class="sxs-lookup"><span data-stu-id="94ddb-211">Other Data Requirements</span></span>  
  
### <a name="requirements-by-algorithm-type"></a><span data-ttu-id="94ddb-212">依演算法類型的需求</span><span class="sxs-lookup"><span data-stu-id="94ddb-212">Requirements by Algorithm Type</span></span>  
 <span data-ttu-id="94ddb-213">在增益集中使用的某些演算法需要特定資料類型或內容類型才能建立模型。</span><span class="sxs-lookup"><span data-stu-id="94ddb-213">Some algorithms that are used in the add-ins require specific data types or content types to create a model.</span></span>  
  
 <span data-ttu-id="94ddb-214">**貝氏機率分類模型**</span><span class="sxs-lookup"><span data-stu-id="94ddb-214">**Naïve Bayes models**</span></span>  
  
-   <span data-ttu-id="94ddb-215">[!INCLUDE[msCoName](../includes/msconame-md.md)] 貝氏機率分類演算法不能使用連續資料行當做輸入。</span><span class="sxs-lookup"><span data-stu-id="94ddb-215">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes algorithm cannot use continuous columns as input.</span></span> <span data-ttu-id="94ddb-216">這表示您必須分類收納數字，或是在有幾個足夠的值時，將其當做離散值來處理。</span><span class="sxs-lookup"><span data-stu-id="94ddb-216">That means you must either bin numbers, or if there are few enough values, handle them as discrete values.</span></span>  
  
-   <span data-ttu-id="94ddb-217">這種模型也無法預測連續值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-217">This type of model also cannot predict continuous values.</span></span> <span data-ttu-id="94ddb-218">因此，如果您想要預測類似收入的連續數字，您應該先將值分類收納成有意義的範圍。</span><span class="sxs-lookup"><span data-stu-id="94ddb-218">Therefore, if you want to predict a continuous number such as income (for example) you should first bin the values into meaningful ranges.</span></span> <span data-ttu-id="94ddb-219">如果您不確定適當的範圍為何，您可以使用群集演算法來識別資料中的數字團塊。</span><span class="sxs-lookup"><span data-stu-id="94ddb-219">If you are not sure what the appropriate ranges are, you can use the clustering algorithm to identify clumps of numbers in your data.</span></span>  
  
-   <span data-ttu-id="94ddb-220">當您使用以此演算法為基礎的 wizard (例如[分析關鍵影響因數 &#40;適用于 Excel 的資料表分析工具&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)) 時，會由您的 wizard 分類收納連續的資料行。</span><span class="sxs-lookup"><span data-stu-id="94ddb-220">When you use a wizard based on this algorithm (such as [Analyze Key Influencers &#40;Table Analysis Tools for Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)), columns that are continuous will be binned by the wizard you.</span></span>  
  
-   <span data-ttu-id="94ddb-221">如果您使用 [[適用于 Excel &#40;的資料貝氏增益集&#41;](advanced-modeling-data-mining-add-ins-for-excel.md) ] 選項來建立貝氏機率分類模型，則會從模型中移除數位行。</span><span class="sxs-lookup"><span data-stu-id="94ddb-221">If you build a Naive Bayes model using the [Advanced Modeling &#40;Data Mining Add-ins for Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md) option, number columns will be removed from the model.</span></span> <span data-ttu-id="94ddb-222">如果您想要避免這種情況，請使用 [重定標籤[&#40;SQL Server 資料採礦增益集]&#41;](relabel-sql-server-data-mining-add-ins.md)工具來建立具有分類收納值的新資料行。</span><span class="sxs-lookup"><span data-stu-id="94ddb-222">If you want to avoid this, use the [Relabel &#40;SQL Server Data Mining Add-ins&#41;](relabel-sql-server-data-mining-add-ins.md) tool to create a new column with binned values.</span></span>  
  
 <span data-ttu-id="94ddb-223">**群集模型**</span><span class="sxs-lookup"><span data-stu-id="94ddb-223">**Clustering Models**</span></span>  
  
-   <span data-ttu-id="94ddb-224">叢集工具 (叢集[Wizard &#40;適用于 excel 的資料採礦增益集&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)並偵測[類別 &#40;適用于 Excel&#41;的資料表分析工具](detect-categories-table-analysis-tools-for-excel.md)) 也不能使用連續數位，但這兩個工具都會自動為您提供數位資料行。</span><span class="sxs-lookup"><span data-stu-id="94ddb-224">The clustering tools ([Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md) and [Detect Categories &#40;Table Analysis Tools for Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)) also cannot use continuous numbers, but both of these tools will automatically bin number columns for you.</span></span>  
  
-   <span data-ttu-id="94ddb-225">這兩種工具都提供選項讓您選擇結果中輸出類別的數目，但如果您要控制個別資料行中值的分組方式，就應該以您要的群組來建立新的資料行。</span><span class="sxs-lookup"><span data-stu-id="94ddb-225">Both tools give you the option to choose the number of output categories in the results, but if you want to control the way that values in individual columns are grouped, you should create a new column with the grouping you want.</span></span>  
  
 <span data-ttu-id="94ddb-226">**預測模型**</span><span class="sxs-lookup"><span data-stu-id="94ddb-226">**Forecasting Models**</span></span>  
  
-   <span data-ttu-id="94ddb-227">所有預測工具都會要求您預測連續的數字。</span><span class="sxs-lookup"><span data-stu-id="94ddb-227">All forecasting tools require that you predict a continuous number.</span></span> <span data-ttu-id="94ddb-228">您無法預測已經儲存為文字的數字。</span><span class="sxs-lookup"><span data-stu-id="94ddb-228">You cannot predict a number that has been saved as text.</span></span>  
  
-   <span data-ttu-id="94ddb-229">如果您的資料包含錯誤資料類型的數字資料行，您可以使用 Excel 函數或 PowerPivot 函數來複製具有正確數值資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="94ddb-229">If your data contains number columns that have the wrong data type, you can use Excel functions or PowerPivot functions to make a copy of the column that has the correct numeric data type.</span></span> <span data-ttu-id="94ddb-230">如果您這樣做，請務必移除具有文字數字的資料行複本，這樣值就不會重複。</span><span class="sxs-lookup"><span data-stu-id="94ddb-230">If you do this, be sure to remove the copy of the column that has the text numbers, so that the values are not duplicated.</span></span>  
  
-   <span data-ttu-id="94ddb-231">如果您要建立迴歸模型的散佈圖，輸入變數也必須是連續數字 (以適當的資料類型表示)。</span><span class="sxs-lookup"><span data-stu-id="94ddb-231">If you want to create a scatter plot of a regression model, the input variables must also be continuous numbers, expressed as an appropriate data type.</span></span>  
  
### <a name="using-content-types-to-make-better-models"></a><span data-ttu-id="94ddb-232">使用內容類型製作更好的模型</span><span class="sxs-lookup"><span data-stu-id="94ddb-232">Using Content Types to Make Better Models</span></span>  
 <span data-ttu-id="94ddb-233">「*內容類型」（content type* ）是您套用至資料行的屬性，用來指定模型應該如何使用資料行資料。</span><span class="sxs-lookup"><span data-stu-id="94ddb-233">A *content type* is a property you apply to a column to specify how the column data should be used by the model.</span></span> <span data-ttu-id="94ddb-234">當執行分析時，演算法可以使用內容類型當做指示或提示。</span><span class="sxs-lookup"><span data-stu-id="94ddb-234">The algorithm can use the content type as an instruction or hint when performing the analysis.</span></span>  
  
 <span data-ttu-id="94ddb-235">例如，如果資料行包含的數字以特定間隔重複 (表示星期幾)，您可能會指定該資料行的內容類型為 `Cyclical`。</span><span class="sxs-lookup"><span data-stu-id="94ddb-235">For example, if a column contains numbers that repeat in a specific interval to indicate the days of the week, you might specify the content type of that column as `Cyclical`.</span></span>  
  
 <span data-ttu-id="94ddb-236">如果您使用此增益集所提供的「嚮導」和「工具」，則不需要擔心內容類型。不過，如果您使用 [[將模型加入至 Excel &#40;資料採礦增益集&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)模型化] 選項將新模型加入現有的資料中，您可能會收到與內容類型相關的錯誤。</span><span class="sxs-lookup"><span data-stu-id="94ddb-236">You don't have to worry about content types if you use the wizards and tools provided in this add-ins. However, if you use the [Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md) modeling option to add a new model to existing data, you might get an error relating to content types.</span></span>  
  
 <span data-ttu-id="94ddb-237">原因是某些模型類型需要特定種類的資料 (例如時間戳記)。</span><span class="sxs-lookup"><span data-stu-id="94ddb-237">The reason is that some types of model require a certain kind of data (such as a time stamp).</span></span> <span data-ttu-id="94ddb-238">工具會依據特定需求來處理這些資料行，也會加入內容類型屬性。</span><span class="sxs-lookup"><span data-stu-id="94ddb-238">The tools process these columns according to specific requirements and also add a content type property.</span></span> <span data-ttu-id="94ddb-239">因此，如果您以完全不同的演算法重複使用資料，您可能需要變更資料類型或內容類型。</span><span class="sxs-lookup"><span data-stu-id="94ddb-239">Therefore, if you re-use the data with a completely different algorithm, you might need to change the data type or content type.</span></span>  
  
 <span data-ttu-id="94ddb-240">下列清單描述資料採礦中使用的內容類型，並識別支援每一種類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="94ddb-240">The following list describes the content types that are used in data mining, and identifies the data types that support each type.</span></span>  
  
 `Discrete`  
 <span data-ttu-id="94ddb-241">此資料行包含有限數量的值，且值之間沒有延續。</span><span class="sxs-lookup"><span data-stu-id="94ddb-241">The column contains a finite number of values with no continuum between the values.</span></span> <span data-ttu-id="94ddb-242">例如，性別資料行是一個典型的離散屬性資料行，因為其資料代表特定數量的類別。</span><span class="sxs-lookup"><span data-stu-id="94ddb-242">For example, a gender column is a typical discrete attribute column, in that the data represents a specific number of categories.</span></span>  
  
 <span data-ttu-id="94ddb-243">`Discrete` 內容類型可用於所有資料類型。</span><span class="sxs-lookup"><span data-stu-id="94ddb-243">The `Discrete` content type can be used with all data types.</span></span>  
  
 `Continuous`  
 <span data-ttu-id="94ddb-244">此資料行包含的值代表刻度允許過渡值的數值資料。</span><span class="sxs-lookup"><span data-stu-id="94ddb-244">The column contains values that represent numeric data on a scale that allows interim values.</span></span> <span data-ttu-id="94ddb-245">連續資料行代表可擴充的度量，其資料可能包含無限個小數值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-245">A continuous column represents scalable measurements, and it is possible for the data to contain an infinite number of fractional values.</span></span> <span data-ttu-id="94ddb-246">溫度資料行就是連續屬性資料行的一個範例。</span><span class="sxs-lookup"><span data-stu-id="94ddb-246">A column of temperatures is an example of a continuous attribute column.</span></span>  
  
 <span data-ttu-id="94ddb-247"> 內容類型可以用於以下資料類型：、 和 。</span><span class="sxs-lookup"><span data-stu-id="94ddb-247">The `Continuous` content type can be used with the following data types: `Date`, `Double`, and `Long`.</span></span>  
  
 `Discretized`  
 <span data-ttu-id="94ddb-248">此資料行包含的值代表從連續資料行衍生之值的群組。</span><span class="sxs-lookup"><span data-stu-id="94ddb-248">The column contains values that represent groups of values that have been derived from a continuous column.</span></span> <span data-ttu-id="94ddb-249">值區會被視為已**排序**和離散值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-249">The buckets are treated as **ordered** and discrete values.</span></span>  
  
 <span data-ttu-id="94ddb-250"> 內容類型可以用於以下資料類型：、 和 。</span><span class="sxs-lookup"><span data-stu-id="94ddb-250">The `Discretized` content type can be used with the following data types: `Date`, `Double`, `Long`.</span></span>  
  
 <span data-ttu-id="94ddb-251">**索引鍵**</span><span class="sxs-lookup"><span data-stu-id="94ddb-251">**Key**</span></span>  
 <span data-ttu-id="94ddb-252">此資料行會唯一識別資料列。</span><span class="sxs-lookup"><span data-stu-id="94ddb-252">The column uniquely identifies a row.</span></span>  
  
 <span data-ttu-id="94ddb-253">索引鍵資料行通常是數值或文字識別碼，不應該用於分析，只能用於追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="94ddb-253">Typically the key column is a numeric or text identifier that should not be used for analysis, only for tracking records.</span></span> <span data-ttu-id="94ddb-254">時間序列索引鍵和時序索引鍵則是例外。</span><span class="sxs-lookup"><span data-stu-id="94ddb-254">The exceptions are time series keys and sequence keys.</span></span>  
  
 <span data-ttu-id="94ddb-255">只有當您從已定義為數據源視圖的外部資料源取得資料時，才會使用**嵌套的資料表索引鍵** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="94ddb-255">**Nested table keys** are used only when you get data from an external data source that has been defined as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source view.</span></span> <span data-ttu-id="94ddb-256">如需有關嵌套資料表的詳細資訊，請參閱 [https://msdn.microsoft.com/library/ms175659.aspx](https://msdn.microsoft.com/library/ms175659.aspx) ：</span><span class="sxs-lookup"><span data-stu-id="94ddb-256">For more information about nested tables, see [https://msdn.microsoft.com/library/ms175659.aspx](https://msdn.microsoft.com/library/ms175659.aspx):</span></span>  
  
 <span data-ttu-id="94ddb-257">此內容類型可以用於以下資料類型：`Date`、`Double`、`Long` 和 `Text`。</span><span class="sxs-lookup"><span data-stu-id="94ddb-257">This content type can be used with the following data types: `Date`, `Double`, `Long`, and `Text`.</span></span>  
  
 <span data-ttu-id="94ddb-258">**Key Sequence**</span><span class="sxs-lookup"><span data-stu-id="94ddb-258">**Key Sequence**</span></span>  
 <span data-ttu-id="94ddb-259">此資料行包含代表事件序列的值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-259">The column contains values that represent a sequence of events.</span></span> <span data-ttu-id="94ddb-260">其值已排序，但不必為等距。</span><span class="sxs-lookup"><span data-stu-id="94ddb-260">The values are ordered, but do not have to be an equal distance apart.</span></span>  
  
 <span data-ttu-id="94ddb-261">這個內容類型受到下列資料類型所支援：`Double`、`Long`、`Text` 和 `Date`。</span><span class="sxs-lookup"><span data-stu-id="94ddb-261">This content type is supported by the following data types: `Double`, `Long`, `Text`, and `Date`.</span></span>  
  
 <span data-ttu-id="94ddb-262">**Key Time**</span><span class="sxs-lookup"><span data-stu-id="94ddb-262">**Key Time**</span></span>  
 <span data-ttu-id="94ddb-263">此資料行包含已排序而且代表時間刻度的值。</span><span class="sxs-lookup"><span data-stu-id="94ddb-263">The column contains values that are ordered and represent a time scale.</span></span> <span data-ttu-id="94ddb-264">只有在模型為時間序列模型或時序群集模型時，才可以使用 Key Time 內容類型。</span><span class="sxs-lookup"><span data-stu-id="94ddb-264">You can use the key time content type only if the model is a time series model or a sequence clustering model.</span></span>  
  
 <span data-ttu-id="94ddb-265">這個內容類型受到下列資料類型所支援：`Double`、`Long` 和 `Date`。</span><span class="sxs-lookup"><span data-stu-id="94ddb-265">This content type is supported by the following data types: `Double`, `Long`, and `Date`.</span></span>  
  
 <span data-ttu-id="94ddb-266">**資料表**</span><span class="sxs-lookup"><span data-stu-id="94ddb-266">**Table**</span></span>  
 <span data-ttu-id="94ddb-267">同樣的，只有從已定義為 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料來源檢視的外部資料來源取得資料時，才可以使用此內容類型。</span><span class="sxs-lookup"><span data-stu-id="94ddb-267">This content type also is used only when you get data from an external data source that has been defined as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source view.</span></span>  
  
 <span data-ttu-id="94ddb-268">也就是說，每個資料列實際上是包含了巢狀資料表 (具有一個或多個資料行以及一個或多個資料列)。</span><span class="sxs-lookup"><span data-stu-id="94ddb-268">What it means is that each row of data actually contains a nested data table, with one or more columns and one or more rows.</span></span>  
  
 <span data-ttu-id="94ddb-269">嵌套資料表非常方便，但您只能搭配[適用于 Excel 的 Advanced 模型 &#40;資料採礦增益集&#41;](advanced-modeling-data-mining-add-ins-for-excel.md)模型選項來使用它們。</span><span class="sxs-lookup"><span data-stu-id="94ddb-269">Nested tables are very handy, but you can use them only with the [Advanced Modeling &#40;Data Mining Add-ins for Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md) modeling options.</span></span> <span data-ttu-id="94ddb-270">例如，[[關聯] wizard &#40;[適用于&#41;excel 的資料採礦用戶端](associate-wizard-data-mining-client-for-excel.md)] 和 [[購物籃分析](shopping-basket-analysis-table-analysistools-for-excel.md)] 的範例資料會 &#40;[適用于 excel 的資料表 AnalysisTools]&#41;工具組含從嵌套資料表簡維化的資料。</span><span class="sxs-lookup"><span data-stu-id="94ddb-270">For example, the sample data for the [Associate Wizard &#40;Data Mining Client for Excel&#41;](associate-wizard-data-mining-client-for-excel.md) wizard and [Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) tool contains data that has been flattened from a nested table.</span></span>  

  
  
