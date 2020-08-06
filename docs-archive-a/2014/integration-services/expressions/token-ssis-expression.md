---
title: TOKEN (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9fdd06bf-5bc9-445c-95bf-709e0ca5989b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5c0598c3832e4bf6f838087be4fee541663c8bff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701347"
---
# <a name="token--ssis-expression"></a><span data-ttu-id="ee962-102">TOKEN (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="ee962-102">TOKEN  (SSIS Expression)</span></span>
  <span data-ttu-id="ee962-103">依據字串中用來分隔 Token 的指定分隔符號，以及表示要傳回哪個 Token 的 Token 號碼，從字串傳回 Token (子字串)。</span><span class="sxs-lookup"><span data-stu-id="ee962-103">Returns a token (substring) from a string based on the specified delimiters that separate tokens in the string and the number of the token that denotes which token to be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee962-104">語法</span><span class="sxs-lookup"><span data-stu-id="ee962-104">Syntax</span></span>  
  
```  
TOKEN(character_expression, delimiter_string, occurrence)  
```  
  
## <a name="arguments"></a><span data-ttu-id="ee962-105">引數</span><span class="sxs-lookup"><span data-stu-id="ee962-105">Arguments</span></span>  
 <span data-ttu-id="ee962-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="ee962-106">*character_expression*</span></span>  
 <span data-ttu-id="ee962-107">包含以分隔符號分隔之 Token 的字串。</span><span class="sxs-lookup"><span data-stu-id="ee962-107">A string that contains tokens separated by delimiters.</span></span>  
  
 <span data-ttu-id="ee962-108">*delimiter_string*</span><span class="sxs-lookup"><span data-stu-id="ee962-108">*delimiter_string*</span></span>  
 <span data-ttu-id="ee962-109">包含分隔符號字元的字串。</span><span class="sxs-lookup"><span data-stu-id="ee962-109">A string that contains delimiter characters.</span></span> <span data-ttu-id="ee962-110">例如，"; ," 包含分號、空格和逗號三個分隔符號字元。</span><span class="sxs-lookup"><span data-stu-id="ee962-110">For example, "; ," contains three delimiter characters semi-colon, a blank space, and a comma.</span></span>  
  
 <span data-ttu-id="ee962-111">*occurrence*</span><span class="sxs-lookup"><span data-stu-id="ee962-111">*occurrence*</span></span>  
 <span data-ttu-id="ee962-112">帶正負號或不帶正負號的整數，指定要傳回的 Token。</span><span class="sxs-lookup"><span data-stu-id="ee962-112">A signed or unsigned integer that specifies the token to be returned.</span></span> <span data-ttu-id="ee962-113">例如，若您指定 3 做為此參數的值，則會傳回字串中的第三個 Token。</span><span class="sxs-lookup"><span data-stu-id="ee962-113">For example, if you specify 3 as a value for this parameter, the third token in the string is returned.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ee962-114">結果類型</span><span class="sxs-lookup"><span data-stu-id="ee962-114">Result Types</span></span>  
 <span data-ttu-id="ee962-115">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="ee962-115">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee962-116">備註</span><span class="sxs-lookup"><span data-stu-id="ee962-116">Remarks</span></span>  
 <span data-ttu-id="ee962-117">此函式會將 <character_expression> 字串分割成一組以 <delimiter_string> 中所指定分隔符號來分隔的 Token，然後傳回第 N 個 Token (其中 N 是 \<occurrence> 參數指定的 Token 出現編號)。</span><span class="sxs-lookup"><span data-stu-id="ee962-117">This function splits up the <character_expression> string into a set of tokens separated by the delimiters specified in the <delimiter_string> and then returns the Nth token where N is the number of occurrence of the token specified by the \<occurrence> parameter.</span></span> <span data-ttu-id="ee962-118">如需此函數的範例用法，請參閱＜範例＞一節。</span><span class="sxs-lookup"><span data-stu-id="ee962-118">See Examples section for sample usages of this function.</span></span>  
  
 <span data-ttu-id="ee962-119">下列備註適用於 TOKEN 函數：</span><span class="sxs-lookup"><span data-stu-id="ee962-119">The following remarks apply to the TOKEN function:</span></span>  
  
-   <span data-ttu-id="ee962-120">分隔符號字串可以包含一個或多個分隔符號字元。</span><span class="sxs-lookup"><span data-stu-id="ee962-120">The delimiter string can contain one or more delimiter characters.</span></span>  
  
-   <span data-ttu-id="ee962-121">如果 \<occurrence> 參數值大於字串中的 Token 總數，則函式就會傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="ee962-121">If the value of \<occurrence> parameter is higher than the total number of tokens in the string, the function returns NULL.</span></span>  
  
-   <span data-ttu-id="ee962-122">前導分隔符號會予略過。</span><span class="sxs-lookup"><span data-stu-id="ee962-122">Leading delimiters are skipped.</span></span>  
  
-   <span data-ttu-id="ee962-123">TOKEN 只適用於 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="ee962-123">TOKEN works only with the DT_WSTR data type.</span></span> <span data-ttu-id="ee962-124">如果 *character_expression* 引數是字串常值或具有 DT_STR 資料類型的資料行，則該引數會在 TOKEN 執行其作業前隱含轉換成 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="ee962-124">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before TOKEN performs its operation.</span></span> <span data-ttu-id="ee962-125">其他資料類型必須明確地轉換為 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="ee962-125">Other data types must be explicitly cast to the DT_WSTR data type.</span></span>  
  
-   <span data-ttu-id="ee962-126">如果 character_expression 為 Null，則 TOKEN 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="ee962-126">TOKEN returns a null result if the character_expression is null.</span></span>  
  
-   <span data-ttu-id="ee962-127">您可以使用變數和資料行來做為運算式中所有引數的值。</span><span class="sxs-lookup"><span data-stu-id="ee962-127">You can use variables and columns as values of all arguments in the expression.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="ee962-128">運算式範例</span><span class="sxs-lookup"><span data-stu-id="ee962-128">Expression Examples</span></span>  
 <span data-ttu-id="ee962-129">在下列範例中，TOKEN 函數會傳回 "a"。</span><span class="sxs-lookup"><span data-stu-id="ee962-129">In the following example, the TOKEN function returns "a".</span></span> <span data-ttu-id="ee962-130">"a little white dog" 字串中有 4 個權杖："a"、"little"、"white"、"dog"，並以分隔符號 " " (空格字元) 分隔。</span><span class="sxs-lookup"><span data-stu-id="ee962-130">The string "a little white dog" has 4 tokens "a", "little", "white", "dog" separated by the delimiter " " (space character).</span></span> <span data-ttu-id="ee962-131">第二個引數 (分隔符號字串) 僅指定一個分隔符號 (空格字元)，以用來將輸入字串分割成 Token。</span><span class="sxs-lookup"><span data-stu-id="ee962-131">The second argument, a delimiter string, specifies only one delimiter, the space character, to be used in splitting the input string into tokens.</span></span> <span data-ttu-id="ee962-132">最後一個引數 1 指定要傳回的第一個 Token。</span><span class="sxs-lookup"><span data-stu-id="ee962-132">The last argument, 1, specifies that the first token to be returned.</span></span> <span data-ttu-id="ee962-133">此範例字串中的第一個權杖是 "a"。</span><span class="sxs-lookup"><span data-stu-id="ee962-133">The first token is "a" in this sample string.</span></span>  
  
```  
TOKEN("a little white dog"," ",1)  
```  
  
 <span data-ttu-id="ee962-134">在下列範例中，TOKEN 函數會傳回 "dog"。</span><span class="sxs-lookup"><span data-stu-id="ee962-134">In the following example, the TOKEN function returns "dog".</span></span> <span data-ttu-id="ee962-135">此範例中的分隔符號字串包含 5 個分隔符號。</span><span class="sxs-lookup"><span data-stu-id="ee962-135">The delimiter string in this example contains 5 delimiters.</span></span> <span data-ttu-id="ee962-136">輸入字串中包含 "a"、"little"、"white"、"dog" 4 個權杖。</span><span class="sxs-lookup"><span data-stu-id="ee962-136">The input string contains 4 tokens: "a", "little", "white", "dog".</span></span>  
  
```  
TOKEN("a:little|white dog","| ,.:",4)  
```  
  
 <span data-ttu-id="ee962-137">在下列範例中，TOKEN 函數會傳回 "" (空字串)，因為字串中沒有 99 個 TOKEN。</span><span class="sxs-lookup"><span data-stu-id="ee962-137">In the following example, the TOKEN function returns "" (an empty string) because there are no 99 tokens in the string.</span></span>  
  
```  
TOKEN("a little white dog"," ",99)  
```  
  
 <span data-ttu-id="ee962-138">在下列範例中，TOKEN 函數會傳回完整字串。</span><span class="sxs-lookup"><span data-stu-id="ee962-138">In the following example, the TOKEN function returns the full string.</span></span> <span data-ttu-id="ee962-139">此函數會剖析輸入字串中的分隔符號，但因為字串中不具分隔符號，所以會直接加入整個字串做為第一個 Token。</span><span class="sxs-lookup"><span data-stu-id="ee962-139">The function parses the input string for delimiters and since there are none in the string, it just adds the entire string as the first token.</span></span>  
  
```  
TOKEN("a little white dog","|",1)  
```  
  
 <span data-ttu-id="ee962-140">在下列範例中，TOKEN 函數會傳回 "a"。</span><span class="sxs-lookup"><span data-stu-id="ee962-140">In the following example, the TOKEN function returns "a".</span></span> <span data-ttu-id="ee962-141">其將忽略所有的前導空格字元。</span><span class="sxs-lookup"><span data-stu-id="ee962-141">It ignores all the leading space characters.</span></span>  
  
```  
TOKEN("        a little white dog", " ", 1)  
```  
  
 <span data-ttu-id="ee962-142">在下列範例中，TOKEN 函數會傳回日期起始年份 (year from a date) 字串。</span><span class="sxs-lookup"><span data-stu-id="ee962-142">In the following example, the TOKEN function returns the year from a date string.</span></span>  
  
```  
TOKEN("2009/01/01", "/"), 1  
```  
  
 <span data-ttu-id="ee962-143">在下列範例中，TOKEN 函數會從指定路徑傳回檔名。</span><span class="sxs-lookup"><span data-stu-id="ee962-143">In the following example, the TOKEN function returns the file name from the specified path.</span></span> <span data-ttu-id="ee962-144">例如，如果 User::Path 的值為 "c:\program files\data\myfile.txt"，TOKEN 函式就會傳回 "myfile.txt"。</span><span class="sxs-lookup"><span data-stu-id="ee962-144">For example, if the value of User::Path is "c:\program files\data\myfile.txt", the TOKEN function returns "myfile.txt".</span></span> <span data-ttu-id="ee962-145">TOKENCOUNT 函式會傳回 4，而 TOKEN 函式會傳回第 4 個權杖 "myfile.txt"。</span><span class="sxs-lookup"><span data-stu-id="ee962-145">The TOKENCOUNT function returns 4 and the TOKEN function return the 4th token, "myfile.txt".</span></span>  
  
```  
TOKEN(@[User::Path], "\\", TOKENCOUNT(@[User::Path], "\\"))  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee962-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee962-146">See Also</span></span>  
 [<span data-ttu-id="ee962-147">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="ee962-147">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
