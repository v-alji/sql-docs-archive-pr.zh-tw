---
title: TOKENCOUNT (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1c0efed1-c2b3-4f20-a3a1-ad91283b7c0a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9068e4958570a0222bc8e1a4c90d34acc5bdf3dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701335"
---
# <a name="tokencount-ssis-expression"></a><span data-ttu-id="ad1a2-102">TOKENCOUNT (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="ad1a2-102">TOKENCOUNT (SSIS Expression)</span></span>
  <span data-ttu-id="ad1a2-103">傳回包含以分隔符號分隔之 Token 的字串中的 Token 數。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-103">Returns the number of tokens in a string that contains tokens separated by the specified delimiters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad1a2-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad1a2-104">Syntax</span></span>  
  
```  
TOKENCOUNT(character_expression, delimiter_string)  
```  
  
## <a name="arguments"></a><span data-ttu-id="ad1a2-105">引數</span><span class="sxs-lookup"><span data-stu-id="ad1a2-105">Arguments</span></span>  
 <span data-ttu-id="ad1a2-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="ad1a2-106">*character_expression*</span></span>  
 <span data-ttu-id="ad1a2-107">包含以分隔符號分隔之 Token 的字串。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-107">A string that contains tokens separated by delimiters.</span></span>  
  
 <span data-ttu-id="ad1a2-108">*delimiter_string*</span><span class="sxs-lookup"><span data-stu-id="ad1a2-108">*delimiter_string*</span></span>  
 <span data-ttu-id="ad1a2-109">包含分隔符號字元的字串。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-109">A string that contains delimiter characters.</span></span> <span data-ttu-id="ad1a2-110">例如，"; ," 包含分號、空格和逗號三個分隔符號字元。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-110">For example, "; ," contains three delimiter characters semi-colon, a blank space, and a comma.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ad1a2-111">結果類型</span><span class="sxs-lookup"><span data-stu-id="ad1a2-111">Result Types</span></span>  
 <span data-ttu-id="ad1a2-112">DT_I4</span><span class="sxs-lookup"><span data-stu-id="ad1a2-112">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad1a2-113">備註</span><span class="sxs-lookup"><span data-stu-id="ad1a2-113">Remarks</span></span>  
 <span data-ttu-id="ad1a2-114">下列備註適用於 TOKEN 函數：</span><span class="sxs-lookup"><span data-stu-id="ad1a2-114">The following remarks apply to the TOKEN function:</span></span>  
  
-   <span data-ttu-id="ad1a2-115">分隔符號字串可以包含一個或多個分隔符號字元。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-115">The delimiter string can contain one or more delimiter characters.</span></span>  
  
-   <span data-ttu-id="ad1a2-116">前導分隔符號會予略過。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-116">Leading delimiters are skipped.</span></span>  
  
-   <span data-ttu-id="ad1a2-117">TOKENCOUNT 只適用於 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-117">TOKENCOUNT works only with the DT_WSTR data type.</span></span> <span data-ttu-id="ad1a2-118">如果 *character_expression* 引數是字串常值或具有 DT_STR 資料類型的資料行，則該引數會在 TOKEN 執行其作業前隱含轉換成 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-118">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before TOKEN performs its operation.</span></span> <span data-ttu-id="ad1a2-119">其他資料類型必須明確地轉換為 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-119">Other data types must be explicitly cast to the DT_WSTR data type.</span></span>  
  
-   <span data-ttu-id="ad1a2-120">如果 character_expression 為 Null，TOKENCOUNT 會傳回 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-120">TOKENCOUNT returns 0 (zero) if the character_expression is null.</span></span>  
  
-   <span data-ttu-id="ad1a2-121">您可以使用變數和資料行做為此運算式的引數。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-121">You can use variables and columns as arguments for this expression.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="ad1a2-122">運算式範例</span><span class="sxs-lookup"><span data-stu-id="ad1a2-122">Expression Examples</span></span>  
 <span data-ttu-id="ad1a2-123">在下列範例中，因為字串包含 "01"、"12"、"2011" 三個權杖，所以 TOKENCOUNT 函式會傳回 3。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-123">In the following example, the TOKENCOUNT function returns 3 because the string contains three tokens: "01", "12", "2011".</span></span>  
  
```  
TOKENCOUNT("01/12/2011", "/")  
```  
  
 <span data-ttu-id="ad1a2-124">下列範例中因有四個權杖 ("a"、"little"、"white"、"dog")，所以 TOKENCOUNT 函式會傳回 4。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-124">In the following example, the TOKENCOUNT function returns 4 because there are four tokens ("a", "little", "white", "dog").</span></span>  
  
```  
TOKENCOUNT("a little white dog"," ")  
```  
  
 <span data-ttu-id="ad1a2-125">在下列範例中，TOKENCOUNT 函數會傳回 1。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-125">In the following example, the TOKENCOUNT function returns 1.</span></span> <span data-ttu-id="ad1a2-126">此函數會剖析輸入字串中的分隔符號，但因為字串中不具分隔符號，所以會直接加入整個字串做為第一個 Token。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-126">The function parses the input string for delimiters and since there are none in the string, it just adds the entire string as the first token.</span></span>  
  
```  
TOKENCOUNT("a little white dog","|")  
```  
  
 <span data-ttu-id="ad1a2-127">在下列範例中，TOKENCOUNT 函數會傳回 4。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-127">In the following example, the TOKENCOUNT function returns 4.</span></span> <span data-ttu-id="ad1a2-128">此範例中的分隔符號字串包含 5 個分隔符號。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-128">The delimiter string in this example contains 5 delimiters.</span></span> <span data-ttu-id="ad1a2-129">輸入字串中包含 "a"、"little"、"white"、"dog" 4 個權杖。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-129">The input string contains 4 tokens: "a", "little", "white", "dog".</span></span>  
  
```  
TOKENCOUNT("a:little|white dog","| ,.:")  
```  
  
 <span data-ttu-id="ad1a2-130">在下列範例中，TOKENCOUNT 函數會傳回 4。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-130">In the following example, the TOKENCOUNT function returns 4.</span></span> <span data-ttu-id="ad1a2-131">其將忽略所有的前導空格字元。</span><span class="sxs-lookup"><span data-stu-id="ad1a2-131">It ignores all the leading space characters.</span></span>  
  
```  
TOKENCOUNT("        a little white dog", " ")  
```  
  
## <a name="see-also"></a><span data-ttu-id="ad1a2-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad1a2-132">See Also</span></span>  
 [<span data-ttu-id="ad1a2-133">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="ad1a2-133">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
