---
title: FORMATED_VALUE 上的語言和 FORMAT_STRING |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7534ff5f-954e-47d4-a2ed-4b5b8ccb30e6
author: minewiskan
ms.author: owend
ms.openlocfilehash: ba4aacbbd440da6048680054771c86c40ef96daa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584757"
---
# <a name="language-and-format_string-on-formated_value"></a><span data-ttu-id="8b138-102">FORMATED_VALUE 上的 LANGUAGE 及 FORMAT_STRING</span><span class="sxs-lookup"><span data-stu-id="8b138-102">LANGUAGE and FORMAT_STRING on FORMATED_VALUE</span></span>
  <span data-ttu-id="8b138-103">FORMATTED_VALUE 屬性是根據資料格中 VALUE、FORMAT_STRING 和 LANGUAGE 屬性的互動而建立。</span><span class="sxs-lookup"><span data-stu-id="8b138-103">The FORMATTED_VALUE property is built on the interactions of the VALUE, FORMAT_STRING and LANGUAGE properties of the cell.</span></span> <span data-ttu-id="8b138-104">本主題將說明這些屬性如何互動，以便建立 FORMATTED_VALUE 屬性。</span><span class="sxs-lookup"><span data-stu-id="8b138-104">This topic explains how these properties interact to build the FORMATTED_VALUE property.</span></span>  
  
## <a name="value-format_string-language-properties"></a><span data-ttu-id="8b138-105">VALUE、FORMAT_STRING、LANGUAGE 屬性</span><span class="sxs-lookup"><span data-stu-id="8b138-105">VALUE, FORMAT_STRING, LANGUAGE properties</span></span>  
 <span data-ttu-id="8b138-106">下表說明這些屬性為何，讓您準備一起使用這些屬性。</span><span class="sxs-lookup"><span data-stu-id="8b138-106">The following table explains what these properties are, to help prepare us to use them in combination.</span></span>  
  
 <span data-ttu-id="8b138-107">值</span><span class="sxs-lookup"><span data-stu-id="8b138-107">VALUE</span></span>  
 <span data-ttu-id="8b138-108">未格式化的資料格值。</span><span class="sxs-lookup"><span data-stu-id="8b138-108">The unformatted value of the cell.</span></span>  
  
 <span data-ttu-id="8b138-109">FORMAT_STRING</span><span class="sxs-lookup"><span data-stu-id="8b138-109">FORMAT_STRING</span></span>  
 <span data-ttu-id="8b138-110">要套用至資料格值來產生 FORMATTED_VALUE 屬性的格式化範本。</span><span class="sxs-lookup"><span data-stu-id="8b138-110">The formatting template to be applied to the value of the cell to generate FORMATTED_VALUE property</span></span>  
  
 <span data-ttu-id="8b138-111">LANGUAGE</span><span class="sxs-lookup"><span data-stu-id="8b138-111">LANGUAGE</span></span>  
 <span data-ttu-id="8b138-112">要沿著 FORMAT_STRING 套用來產生當地語系化 FORMATTED_VALUE 版本的地區設定規格。</span><span class="sxs-lookup"><span data-stu-id="8b138-112">The locale specification to be applied alongside FORMAT_STRING to generate a localized version of FORMATTED_VALUE</span></span>  
  
## <a name="formatted_value-constructed"></a><span data-ttu-id="8b138-113">建構的 FORMATTED_VALUE</span><span class="sxs-lookup"><span data-stu-id="8b138-113">FORMATTED_VALUE constructed</span></span>  
 <span data-ttu-id="8b138-114">FORMATTED_VALUE 屬性的建構方式是利用 VALUE 屬性中的值，以及將 FORMAT_STRING 屬性中指定的格式範本套用到該值。</span><span class="sxs-lookup"><span data-stu-id="8b138-114">The FORMATTED_VALUE property is constructed by using the value from the VALUE property and applying the format template specified in the FORMAT_STRING property to that value.</span></span> <span data-ttu-id="8b138-115">此外，每當格式值是 `named formatting literal` 時，LANGUAGE 屬性規格就會修改 FORMAT_STRING 的輸出，以遵循具名格式的語言使用方式。</span><span class="sxs-lookup"><span data-stu-id="8b138-115">In addition, whenever the formatting value is a `named formatting literal` the LANGUAGE property specification modifies the output of FORMAT_STRING to follow the language usage for the named formatting.</span></span> <span data-ttu-id="8b138-116">具名格式常值全都是以可當地語系化的方式來定義。</span><span class="sxs-lookup"><span data-stu-id="8b138-116">Named formatting literals are all defined in a way that can be localized.</span></span> <span data-ttu-id="8b138-117">例如， `"General Date"` 是一種可以當地語系化的規格，與下列範本 `"YYYY-MM-DD hh:nn:ss",` 相反，後者指出日期是以範本定義的方式呈現，不論語言規格為何。</span><span class="sxs-lookup"><span data-stu-id="8b138-117">For example, `"General Date"` is a specification that can be localized, as opposed to the following template `"YYYY-MM-DD hh:nn:ss",` which states that the date is to be presented as defined by the template regardless of the language specification.</span></span>  
  
 <span data-ttu-id="8b138-118">如果 FORMAT_STRING 範本與 LANGUAGE 規格之間有衝突，FORMAT_STRING 範本會覆寫 LANGUAGE 規格。</span><span class="sxs-lookup"><span data-stu-id="8b138-118">If there is a conflict between the FORMAT_STRING template and the LANGUAGE specification, the FORMAT_STRING template overrides the LANGUAGE specification.</span></span> <span data-ttu-id="8b138-119">例如，如果 FORMAT_STRING="$ #0" 且 LANGUAGE=1034 (西班牙)，而且 VALUE=123.456 然後 FORMATTED_VALUE="$ 123" 而非 FORMATTED_VALUE="€ 123"，則預期的格式會是歐元，因為格式範本的值會覆寫指定的語言。</span><span class="sxs-lookup"><span data-stu-id="8b138-119">For example, if FORMAT_STRING="$ #0" and LANGUAGE=1034 (Spain), and VALUE=123.456 then FORMATTED_VALUE="$ 123" instead of FORMATTED_VALUE="€ 123", the expected format is in Euros, because the value of the format template overrides the language specified.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="8b138-120">範例</span><span class="sxs-lookup"><span data-stu-id="8b138-120">Examples</span></span>  
 <span data-ttu-id="8b138-121">下列範例示範當搭配 FORMAT_STRING 使用 LANGUAGE 時所取得的輸出。</span><span class="sxs-lookup"><span data-stu-id="8b138-121">The following examples show the output obtained when LANGUAGE is used in conjunction with FORMAT_STRING.</span></span>  
  
 <span data-ttu-id="8b138-122">第一個範例說明格式化數值，第二個範例說明格式化日期和時間值。</span><span class="sxs-lookup"><span data-stu-id="8b138-122">The first example explains formatting numerical values; the second example explains formatting date and time values.</span></span>  
  
 <span data-ttu-id="8b138-123">每一個範例都有提供多維度運算式 (MDX) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="8b138-123">For each example the Multidimensional Expressions (MDX) code is given.</span></span>  
  
 `with`  
  
 `member measures.A as 5040, FORMAT_STRING="Currency"`  
  
 `member measures.B as measures.A, LANGUAGE=1034`  
  
 `member measures.C as measures.A, LANGUAGE=1034 , FORMAT_STRING="$#,##0.00"`  
  
 `member measures.D as measures.A, FORMAT_STRING="Scientific"`  
  
 `member measures.E as measures.A, LANGUAGE=1034 , FORMAT_STRING="Scientific"`  
  
 `member measures.F as 0.5040, FORMAT_STRING="Percent"`  
  
 `member measures.G as measures.F, LANGUAGE=1034`  
  
 `member measures.H as 0, LANGUAGE=1034 , FORMAT_STRING="Yes/No"`  
  
 `member measures.I as 59, LANGUAGE=1034 , FORMAT_STRING="Yes/No"`  
  
 `member measures.J as 0, LANGUAGE=1034 , FORMAT_STRING="ON/OFF"`  
  
 `member measures.K as -312, LANGUAGE=1034 , FORMAT_STRING="ON/OFF"`  
  
 `Select {measures.A, measures.B, measures.C, measures.D, measures.E, measures.F, measures.G, measures.H, measures.I, measures.J, measures.K} on 0`  
  
 `from [Adventure Works]`  
  
 `cell properties VALUE, FORMAT_STRING, LANGUAGE, FORMATTED_VALUE`  
  
 <span data-ttu-id="8b138-124">在伺服器上使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 來執行上述 MDX 查詢，而且用戶端的地區設定為 1033 時，調換的結果如下所示：</span><span class="sxs-lookup"><span data-stu-id="8b138-124">The results, transposed, when the above MDX query was run using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] over a server and client with locale 1033 are as follows:</span></span>  
  
|<span data-ttu-id="8b138-125">成員</span><span class="sxs-lookup"><span data-stu-id="8b138-125">Member</span></span>|<span data-ttu-id="8b138-126">FORMATTED_VALUE</span><span class="sxs-lookup"><span data-stu-id="8b138-126">FORMATTED_VALUE</span></span>|<span data-ttu-id="8b138-127">說明</span><span class="sxs-lookup"><span data-stu-id="8b138-127">Explanation</span></span>|  
|------------|----------------------|-----------------|  
|<span data-ttu-id="8b138-128">A</span><span class="sxs-lookup"><span data-stu-id="8b138-128">A</span></span>|<span data-ttu-id="8b138-129">$5,040.00</span><span class="sxs-lookup"><span data-stu-id="8b138-129">$5,040.00</span></span>|<span data-ttu-id="8b138-130">FORMAT_STRING 設定為 `Currency` 而且 LANGUAGE 為 `1033`(從系統地區設定值繼承而來)。</span><span class="sxs-lookup"><span data-stu-id="8b138-130">FORMAT_STRING is set to `Currency` and LANGUAGE is `1033`, inherited from system locale value</span></span>|  
|<span data-ttu-id="8b138-131">B</span><span class="sxs-lookup"><span data-stu-id="8b138-131">B</span></span>|<span data-ttu-id="8b138-132">5.040,00</span><span class="sxs-lookup"><span data-stu-id="8b138-132">€5.040,00</span></span>|<span data-ttu-id="8b138-133">FORMAT_STRING 設定為 `Currency` (繼承自 A) 而且 LANGUAGE 明確設定為 `1034` (西班牙)，因此是歐元符號、不同的小數分隔符號和不同的千位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8b138-133">FORMAT_STRING is set to `Currency` (inherited from A) and LANGUAGE is explicitly set to `1034` (Spain) hence the Euro sign, the different decimal separator and the different thousand separator.</span></span>|  
|<span data-ttu-id="8b138-134">C</span><span class="sxs-lookup"><span data-stu-id="8b138-134">C</span></span>|<span data-ttu-id="8b138-135">$5.040,00</span><span class="sxs-lookup"><span data-stu-id="8b138-135">$5.040,00</span></span>|<span data-ttu-id="8b138-136">FORMAT_STRING 設定為 `$#,##0.00` (從 A 覆寫貨幣)，而且 LANGUAGE 明確設定為 `1034` (西班牙)。</span><span class="sxs-lookup"><span data-stu-id="8b138-136">FORMAT_STRING is set to `$#,##0.00` an override to Currency, from A, and LANGUAGE is explicitly set to `1034` (Spain).</span></span> <span data-ttu-id="8b138-137">因為 FORMAT_STRING 屬性明確將貨幣符號設定為 $，所以會使用 $ 符號表示 FORMATTED_VALUE。</span><span class="sxs-lookup"><span data-stu-id="8b138-137">Because the FORMAT_STRING property explicitly set the currency symbol to $, the FORMATTED_VALUE is presented with the $ sign.</span></span> <span data-ttu-id="8b138-138">但是，因為 `.` (點) 和 `,` (逗號) 分別為小數分隔符號和千位分隔符號的預留位置，所以語言規格會影響它們產生針對小數分隔符號和千位分隔符號所當地語系化的輸出。</span><span class="sxs-lookup"><span data-stu-id="8b138-138">However, because `.` (dot) and `,` (comma) are placeholders for decimal separator and thousand separator respectively, the language specification affects them generating an output that is localized for decimal and thousand separators.</span></span>|  
|<span data-ttu-id="8b138-139">D</span><span class="sxs-lookup"><span data-stu-id="8b138-139">D</span></span>|<span data-ttu-id="8b138-140">5.04E+03</span><span class="sxs-lookup"><span data-stu-id="8b138-140">5.04E+03</span></span>|<span data-ttu-id="8b138-141">FORMAT_STRING 設定為 `Scientific` 而且 LANGUAGE 設定為 `1033`(從系統地區設定值繼承而來)，因此 `.` (點) 是小數分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8b138-141">FORMAT_STRING is set to `Scientific` and LANGUAGE is set to `1033`, inherited from system locale value, hence `.` (dot) is the decimal separator.</span></span>|  
|<span data-ttu-id="8b138-142">E</span><span class="sxs-lookup"><span data-stu-id="8b138-142">E</span></span>|<span data-ttu-id="8b138-143">5,04E+03</span><span class="sxs-lookup"><span data-stu-id="8b138-143">5,04E+03</span></span>|<span data-ttu-id="8b138-144">FORMAT_STRING 設定為 `Scientific` 而且 LANGUAGE 明確設定為 `1034,` ，因此 `,` (逗號) 是小數分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8b138-144">FORMAT_STRING is set to `Scientific` and LANGUAGE is set explicitly to `1034,` hence `,` (comma) is the decimal separator.</span></span>|  
|<span data-ttu-id="8b138-145">F</span><span class="sxs-lookup"><span data-stu-id="8b138-145">F</span></span>|<span data-ttu-id="8b138-146">50.40%</span><span class="sxs-lookup"><span data-stu-id="8b138-146">50.40%</span></span>|<span data-ttu-id="8b138-147">FORMAT_STRING 設定為 `Percent` 而且 LANGUAGE 設定為 `1033`(從系統地區設定值繼承而來)，因此 `.` (點) 是小數分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8b138-147">FORMAT_STRING is set to `Percent` and LANGUAGE is set to `1033`, inherited from system locale value, hence `.` (dot) is the decimal separator.</span></span><br /><br /> <span data-ttu-id="8b138-148">請注意，VALUE 已經從 5040 變更為 0.5040</span><span class="sxs-lookup"><span data-stu-id="8b138-148">Note that VALUE was changed from 5040 to 0.5040</span></span>|  
|<span data-ttu-id="8b138-149">G</span><span class="sxs-lookup"><span data-stu-id="8b138-149">G</span></span>|<span data-ttu-id="8b138-150">50,40%</span><span class="sxs-lookup"><span data-stu-id="8b138-150">50,40%</span></span>|<span data-ttu-id="8b138-151">FORMAT_STRING 設定為 `Percent`(繼承自 F)，而且 LANGUAGE 明確設定為 `1034` ，因此 `,` (逗號) 是小數分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8b138-151">FORMAT_STRING is set to `Percent`, inherited from F, and LANGUAGE is set explicitly to `1034` hence `,` (comma) is the decimal separator.</span></span><br /><br /> <span data-ttu-id="8b138-152">請注意，VALUE 繼承自 F 值。</span><span class="sxs-lookup"><span data-stu-id="8b138-152">Note that VALUE was inherited from F value.</span></span>|  
|<span data-ttu-id="8b138-153">H</span><span class="sxs-lookup"><span data-stu-id="8b138-153">H</span></span>|<span data-ttu-id="8b138-154">否</span><span class="sxs-lookup"><span data-stu-id="8b138-154">No</span></span>|<span data-ttu-id="8b138-155">FORMAT_STRING 設定為 `YES/NO`、VALUE 設定為 0 而且 LANGUAGE 明確設定為 `1034`；因為英文 NO 與西班牙 NO 之間沒有任何差異，所以使用者在 FORMATTED_VALUE 中看不到任何差異。</span><span class="sxs-lookup"><span data-stu-id="8b138-155">FORMAT_STRING is set to `YES/NO`, VALUE is set to 0 and LANGUAGE is set explicitly to `1034`; because there is no difference between English NO and Spanish NO the user sees no difference in the FORMATTED_VALUE.</span></span>|  
|<span data-ttu-id="8b138-156">I</span><span class="sxs-lookup"><span data-stu-id="8b138-156">I</span></span>|<span data-ttu-id="8b138-157">SI</span><span class="sxs-lookup"><span data-stu-id="8b138-157">SI</span></span>|<span data-ttu-id="8b138-158">FORMAT_STRING 設定為 `YES/NO`、VALUE 設定為 59 而且 LANGUAGE 明確設定為 `1034`；如同針對 YES/NO 格式所定義，因為與零 (0) 不同的任何值都是 YES 而且語言設定為西班牙文，所以 FORMATTED_VALUE 為 SI。</span><span class="sxs-lookup"><span data-stu-id="8b138-158">FORMAT_STRING is set to `YES/NO`, VALUE is set to 59 and LANGUAGE is set explicitly to `1034`; as defined for YES/NO formatting, any value different from zero (0) is a YES and because language is set to Spanish then the FORMATTED_VALUE is SI.</span></span>|  
|<span data-ttu-id="8b138-159">J</span><span class="sxs-lookup"><span data-stu-id="8b138-159">J</span></span>|<span data-ttu-id="8b138-160">Desactivado</span><span class="sxs-lookup"><span data-stu-id="8b138-160">Desactivado</span></span>|<span data-ttu-id="8b138-161">FORMAT_STRING 設定為 `ON/OFF`、VALUE 設定為 0 而且 LANGUAGE 明確設定為 `1034`；如同針對 ON/OFF 格式所定義，因為等於零 (0) 的任何值都是 OFF 而且語言設定為西班牙文，所以 FORMATTED_VALUE 為 Desactivado。</span><span class="sxs-lookup"><span data-stu-id="8b138-161">FORMAT_STRING is set to `ON/OFF`, VALUE is set to 0 and LANGUAGE is set explicitly to `1034`; as defined for ON/OFF formatting, any value equal to zero (0) is an OFF and because language is set to Spanish then the FORMATTED_VALUE is Desactivado.</span></span>|  
|<span data-ttu-id="8b138-162">K</span><span class="sxs-lookup"><span data-stu-id="8b138-162">K</span></span>|<span data-ttu-id="8b138-163">Activado</span><span class="sxs-lookup"><span data-stu-id="8b138-163">Activado</span></span>|<span data-ttu-id="8b138-164">FORMAT_STRING 設定為 `ON/OFF`、VALUE 設定為 -312 而且 LANGUAGE 明確設定為 `1034`；如同針對 ON/OFF 格式所定義，因為與零 (0) 不同的任何值都是 ON 而且語言設定為西班牙文，所以 FORMATTED_VALUE 為 Activado。</span><span class="sxs-lookup"><span data-stu-id="8b138-164">FORMAT_STRING is set to `ON/OFF`, VALUE is set to -312 and LANGUAGE is set explicitly to `1034`; as defined for ON/OFF formatting, any value different from zero (0) is an ON and because language is set to Spanish then the FORMATTED_VALUE is Activado.</span></span>|  
  
 `with`  
  
 `member measures.A as 'CDate("1959-03-12 06:30")'`  
  
 `member measures.B as measures.A, FORMAT_STRING="Long Date"`  
  
 `member measures.C as measures.A, LANGUAGE=1034 , FORMAT_STRING="General Date"`  
  
 `member measures.D as measures.A, LANGUAGE=1034, FORMAT_STRING="Long Date"`  
  
 `member measures.E as measures.A, LANGUAGE=1041 , FORMAT_STRING="General Date"`  
  
 `member measures.F as measures.A, LANGUAGE=1041 , FORMAT_STRING="Long Date"`  
  
 `member measures.G as measures.A, FORMAT_STRING="Long Time"`  
  
 `member measures.H as measures.A, FORMAT_STRING="Short Time"`  
  
 `member measures.I as measures.A, LANGUAGE=1034 , FORMAT_STRING="Long Time"`  
  
 `member measures.J as measures.A, LANGUAGE=1034 , FORMAT_STRING="Short Time"`  
  
 `member measures.K as measures.A, LANGUAGE=1041 , FORMAT_STRING="Long Time"`  
  
 `member measures.L as measures.A, LANGUAGE=1041 , FORMAT_STRING="Short Time"`  
  
 `Select {measures.A, measures.B, measures.C, measures.D, measures.E, measures.F`  
  
 `, measures.G, measures.H, measures.I, measures.J, measures.K, measures.L} on 0`  
  
 `from [Adventure Works]`  
  
 `cell properties VALUE, FORMAT_STRING, LANGUAGE, FORMATTED_VALUE`  
  
 <span data-ttu-id="8b138-165">在伺服器上使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 來執行上述 MDX 查詢，而且用戶端的地區設定為 1033 時，調換的結果如下所示：</span><span class="sxs-lookup"><span data-stu-id="8b138-165">The results, transposed, when the above MDX query was run using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] over a server and client with locale 1033 are as follows:</span></span>  
  
|<span data-ttu-id="8b138-166">成員</span><span class="sxs-lookup"><span data-stu-id="8b138-166">Member</span></span>|<span data-ttu-id="8b138-167">FORMATTED_VALUE</span><span class="sxs-lookup"><span data-stu-id="8b138-167">FORMATTED_VALUE</span></span>|<span data-ttu-id="8b138-168">說明</span><span class="sxs-lookup"><span data-stu-id="8b138-168">Explanation</span></span>|  
|------------|----------------------|-----------------|  
|<span data-ttu-id="8b138-169">A</span><span class="sxs-lookup"><span data-stu-id="8b138-169">A</span></span>|<span data-ttu-id="8b138-170">3/12/1959 6:30:00 AM</span><span class="sxs-lookup"><span data-stu-id="8b138-170">3/12/1959 6:30:00 AM</span></span>|<span data-ttu-id="8b138-171">FORMAT_STRING 由 CDate() 運算式隱含地設定為 `General Date` ，而且 LANGUAGE 是 `1033` (英文)，這是從系統地區設定值繼承而來。</span><span class="sxs-lookup"><span data-stu-id="8b138-171">FORMAT_STRING is set implicitly to `General Date` by the CDate() expression and LANGUAGE is `1033` (English), inherited from system locale value</span></span>|  
|<span data-ttu-id="8b138-172">B</span><span class="sxs-lookup"><span data-stu-id="8b138-172">B</span></span>|<span data-ttu-id="8b138-173">Thursday, March 12, 1959</span><span class="sxs-lookup"><span data-stu-id="8b138-173">Thursday, March 12, 1959</span></span>|<span data-ttu-id="8b138-174">FORMAT_STRING 明確設定為 `Long Date` 而且 LANGUAGE 為 `1033` (英文)，這是從系統地區設定值繼承而來。</span><span class="sxs-lookup"><span data-stu-id="8b138-174">FORMAT_STRING is set explicitly to `Long Date` and LANGUAGE is `1033` (English), inherited from system locale value</span></span>|  
|<span data-ttu-id="8b138-175">C</span><span class="sxs-lookup"><span data-stu-id="8b138-175">C</span></span>|<span data-ttu-id="8b138-176">12/03/1959 6:30:00</span><span class="sxs-lookup"><span data-stu-id="8b138-176">12/03/1959 6:30:00</span></span>|<span data-ttu-id="8b138-177">FORMAT_STRING 明確設定為 `General Date` 且 LANGUAGE 明確設定為 `1034` (西班牙文)。</span><span class="sxs-lookup"><span data-stu-id="8b138-177">FORMAT_STRING is set explicitly to `General Date` and LANGUAGE is explicitly `1034` (Spanish).</span></span><br /><br /> <span data-ttu-id="8b138-178">請注意，當與美國格式樣式相比較時，就會切換月和日。</span><span class="sxs-lookup"><span data-stu-id="8b138-178">Note that month and day are switched when compared to U.S. formatting style</span></span>|  
|<span data-ttu-id="8b138-179">D</span><span class="sxs-lookup"><span data-stu-id="8b138-179">D</span></span>|<span data-ttu-id="8b138-180">jueves, 12 de marzo de 1959</span><span class="sxs-lookup"><span data-stu-id="8b138-180">jueves, 12 de marzo de 1959</span></span>|<span data-ttu-id="8b138-181">FORMAT_STRING 明確設定為 `Long Date` 且 LANGUAGE 明確設定為 `1034` (西班牙文)。</span><span class="sxs-lookup"><span data-stu-id="8b138-181">FORMAT_STRING is set explicitly to `Long Date` and LANGUAGE is explicitly `1034` (Spanish).</span></span><br /><br /> <span data-ttu-id="8b138-182">請注意，月和星期幾是以西班牙文描述。</span><span class="sxs-lookup"><span data-stu-id="8b138-182">Note that month and day of the week are worded in Spanish</span></span>|  
|<span data-ttu-id="8b138-183">E</span><span class="sxs-lookup"><span data-stu-id="8b138-183">E</span></span>|<span data-ttu-id="8b138-184">1959/03/12 6:30:00</span><span class="sxs-lookup"><span data-stu-id="8b138-184">1959/03/12 6:30:00</span></span>|<span data-ttu-id="8b138-185">FORMAT_STRING 明確設定為 `General Date` 且 LANGUAGE 明確設定為 `1041` (日文)。</span><span class="sxs-lookup"><span data-stu-id="8b138-185">FORMAT_STRING is set explicitly to `General Date` and LANGUAGE is explicitly `1041` (Japanese).</span></span><br /><br /> <span data-ttu-id="8b138-186">請注意，日期現在的格式為：Year/Month/Day Hour:Minutes:Seconds</span><span class="sxs-lookup"><span data-stu-id="8b138-186">Note that the date is now formatted Year/Month/Day Hour:Minutes:Seconds</span></span>|  
|<span data-ttu-id="8b138-187">F</span><span class="sxs-lookup"><span data-stu-id="8b138-187">F</span></span>|<span data-ttu-id="8b138-188">1959年3月12日</span><span class="sxs-lookup"><span data-stu-id="8b138-188">1959年3月12日</span></span>|<span data-ttu-id="8b138-189">FORMAT_STRING 明確設定為 `Long Date` 且 LANGUAGE 明確設定為 `1041` (日文)。</span><span class="sxs-lookup"><span data-stu-id="8b138-189">FORMAT_STRING is set explicitly to `Long Date` and LANGUAGE is explicitly `1041` (Japanese).</span></span>|  
|<span data-ttu-id="8b138-190">G</span><span class="sxs-lookup"><span data-stu-id="8b138-190">G</span></span>|<span data-ttu-id="8b138-191">6:30:00 AM</span><span class="sxs-lookup"><span data-stu-id="8b138-191">6:30:00 AM</span></span>|<span data-ttu-id="8b138-192">FORMAT_STRING 明確設定為 `Long Time` 而且 LANGUAGE 為 `1033` (英文)，這是從系統地區設定值繼承而來。</span><span class="sxs-lookup"><span data-stu-id="8b138-192">FORMAT_STRING is set explicitly to `Long Time` and LANGUAGE is `1033` (English), inherited from system locale value.</span></span>|  
|<span data-ttu-id="8b138-193">H</span><span class="sxs-lookup"><span data-stu-id="8b138-193">H</span></span>|<span data-ttu-id="8b138-194">06:30</span><span class="sxs-lookup"><span data-stu-id="8b138-194">06:30</span></span>|<span data-ttu-id="8b138-195">FORMAT_STRING 明確設定為 `Short Time` 而且 LANGUAGE 為 `1033` (英文)，這是從系統地區設定值繼承而來。</span><span class="sxs-lookup"><span data-stu-id="8b138-195">FORMAT_STRING is set explicitly to `Short Time` and LANGUAGE is `1033` (English), inherited from system locale value.</span></span>|  
|<span data-ttu-id="8b138-196">I</span><span class="sxs-lookup"><span data-stu-id="8b138-196">I</span></span>|<span data-ttu-id="8b138-197">6:30:00</span><span class="sxs-lookup"><span data-stu-id="8b138-197">6:30:00</span></span>|<span data-ttu-id="8b138-198">FORMAT_STRING 明確設定為 `Long Time` 且 LANGUAGE 明確設定為 `1034` (西班牙文)。</span><span class="sxs-lookup"><span data-stu-id="8b138-198">FORMAT_STRING is set explicitly to `Long Time` and LANGUAGE is set explicitly to `1034` (Spanish).</span></span>|  
|<span data-ttu-id="8b138-199">J</span><span class="sxs-lookup"><span data-stu-id="8b138-199">J</span></span>|<span data-ttu-id="8b138-200">06:30</span><span class="sxs-lookup"><span data-stu-id="8b138-200">06:30</span></span>|<span data-ttu-id="8b138-201">FORMAT_STRING 明確設定為 `Short Time` 且 LANGUAGE 明確設定為 `1034` (西班牙文)。</span><span class="sxs-lookup"><span data-stu-id="8b138-201">FORMAT_STRING is set explicitly to `Short Time` and LANGUAGE is set explicitly to `1034` (Spanish).</span></span>|  
|<span data-ttu-id="8b138-202">K</span><span class="sxs-lookup"><span data-stu-id="8b138-202">K</span></span>|<span data-ttu-id="8b138-203">6:30:00</span><span class="sxs-lookup"><span data-stu-id="8b138-203">6:30:00</span></span>|<span data-ttu-id="8b138-204">FORMAT_STRING 明確設定為 `Long Time` 且 LANGUAGE 明確設定為 `1041` (日文)。</span><span class="sxs-lookup"><span data-stu-id="8b138-204">FORMAT_STRING is set explicitly to `Long Time` and LANGUAGE is set explicitly to `1041` (Japanese).</span></span>|  
|<span data-ttu-id="8b138-205">L</span><span class="sxs-lookup"><span data-stu-id="8b138-205">L</span></span>|<span data-ttu-id="8b138-206">06:30</span><span class="sxs-lookup"><span data-stu-id="8b138-206">06:30</span></span>|<span data-ttu-id="8b138-207">FORMAT_STRING 明確設定為 `Short Time` 且 LANGUAGE 明確設定為 `1041` (日文)。</span><span class="sxs-lookup"><span data-stu-id="8b138-207">FORMAT_STRING is set explicitly to `Short Time` and LANGUAGE is set explicitly to `1041` (Japanese).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b138-208">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b138-208">See Also</span></span>  
 <span data-ttu-id="8b138-209">[FORMAT_STRING &#40;MDX 的內容&#41;](mdx-cell-properties-format-string-contents.md) </span><span class="sxs-lookup"><span data-stu-id="8b138-209">[FORMAT_STRING Contents &#40;MDX&#41;](mdx-cell-properties-format-string-contents.md) </span></span>  
 <span data-ttu-id="8b138-210">[使用資料格屬性 &#40;MDX&#41;](mdx-cell-properties-using-cell-properties.md) </span><span class="sxs-lookup"><span data-stu-id="8b138-210">[Using Cell Properties &#40;MDX&#41;](mdx-cell-properties-using-cell-properties.md) </span></span>  
 <span data-ttu-id="8b138-211">[&#40;MDX&#41;建立和使用屬性值](../../creating-and-using-property-values-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="8b138-211">[Creating and Using Property Values &#40;MDX&#41;](../../creating-and-using-property-values-mdx.md) </span></span>  
 [<span data-ttu-id="8b138-212">MDX 查詢基礎觀念 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8b138-212">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
