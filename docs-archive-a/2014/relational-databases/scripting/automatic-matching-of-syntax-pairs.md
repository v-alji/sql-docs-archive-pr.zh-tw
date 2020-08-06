---
title: 語法組的自動比對
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [SQL Server], delimiter highlighting
- IntelliSense [SQL Server], syntax pair matching
ms.assetid: bfc54cda-bfd6-4545-a5b9-f9db2ae13769
author: rothja
ms.author: jroth
ms.openlocfilehash: d1237eeb9aaec39e3210b00c880c0005ef3d95bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594464"
---
# <a name="automatic-matching-of-syntax-pairs"></a><span data-ttu-id="85c11-102">語法組的自動比對</span><span class="sxs-lookup"><span data-stu-id="85c11-102">Automatic Matching of Syntax Pairs</span></span>
  <span data-ttu-id="85c11-103">語法組的自動比對會提供有關必須成對編碼的語法元素是否正確配對的立即回應給您。</span><span class="sxs-lookup"><span data-stu-id="85c11-103">Automatic matching of syntax pairs gives you immediate feedback on whether syntax elements that must be coded in pairs are correctly paired.</span></span> <span data-ttu-id="85c11-104">這就是 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器中的分隔符號比對、Analysis Services XMLA 查詢編輯器中的大括號比對，以及 MDX 和 DMX 編輯器中的括號比對。</span><span class="sxs-lookup"><span data-stu-id="85c11-104">This is known as delimiter matching in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor, brace matching in the Analysis Services XMLA Query Editor, and parenthesis matching in the MDX and DMX editors.</span></span>  
  
## <a name="database-engine-query-editor-delimiter-matching"></a><span data-ttu-id="85c11-105">Database Engine 查詢編輯器的分隔符號比對</span><span class="sxs-lookup"><span data-stu-id="85c11-105">Database Engine Query Editor Delimiter Matching</span></span>  
 <span data-ttu-id="85c11-106">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器會比對可識別程式碼區塊界限的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="85c11-106">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor matches the delimiters that identify the boundaries of code blocks.</span></span> <span data-ttu-id="85c11-107">比對是以兩種方式完成：</span><span class="sxs-lookup"><span data-stu-id="85c11-107">The matching is done in two ways:</span></span>  
  
-   <span data-ttu-id="85c11-108">當您完成輸入配對中的第二個分隔符號時，編輯器就會反白顯示配對中的兩個分隔符號。</span><span class="sxs-lookup"><span data-stu-id="85c11-108">The editor highlights both delimiters in a pair when you finish typing the second delimiter in the pair.</span></span>  
  
-   <span data-ttu-id="85c11-109">游標隨時都位於配對的其中一個分隔符號內，因此您可以使用 CTRL+] 鍵盤快速鍵來跳到對稱的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="85c11-109">Anytime the cursor is in one of the delimiters in a pair, you can use the CTRL+] keyboard shortcut to jump to the matching delimiter.</span></span>  
  
### <a name="delimiter-pairs"></a><span data-ttu-id="85c11-110">分隔符號組</span><span class="sxs-lookup"><span data-stu-id="85c11-110">Delimiter Pairs</span></span>  
 <span data-ttu-id="85c11-111">自動分隔符號比對會辨識下列分隔符號集合：</span><span class="sxs-lookup"><span data-stu-id="85c11-111">Automatic delimiter matching recognizes the following sets of delimiters:</span></span>  
  
|<span data-ttu-id="85c11-112">開頭分隔符號</span><span class="sxs-lookup"><span data-stu-id="85c11-112">Lead Delimiter</span></span>|<span data-ttu-id="85c11-113">結束分隔符號</span><span class="sxs-lookup"><span data-stu-id="85c11-113">Closing Delimiter</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="85c11-114">**(**</span><span class="sxs-lookup"><span data-stu-id="85c11-114">**(**</span></span>|<span data-ttu-id="85c11-115">**)**</span><span class="sxs-lookup"><span data-stu-id="85c11-115">**)**</span></span>|  
|<span data-ttu-id="85c11-116">**BEGIN**</span><span class="sxs-lookup"><span data-stu-id="85c11-116">**BEGIN**</span></span>|<span data-ttu-id="85c11-117">**END**</span><span class="sxs-lookup"><span data-stu-id="85c11-117">**END**</span></span>|  
|<span data-ttu-id="85c11-118">**BEGIN TRY**</span><span class="sxs-lookup"><span data-stu-id="85c11-118">**BEGIN TRY**</span></span>|<span data-ttu-id="85c11-119">**END TRY**</span><span class="sxs-lookup"><span data-stu-id="85c11-119">**END TRY**</span></span>|  
|<span data-ttu-id="85c11-120">**BEGIN CATCH**</span><span class="sxs-lookup"><span data-stu-id="85c11-120">**BEGIN CATCH**</span></span>|<span data-ttu-id="85c11-121">**END CATCH**</span><span class="sxs-lookup"><span data-stu-id="85c11-121">**END CATCH**</span></span>|  
  
 <span data-ttu-id="85c11-122">自動分隔符號比對不會辨識括號識別碼 ([ObjectName]) 或引號識別碼 ("ObjectName") 的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="85c11-122">Automatic delimiter matching does not recognize the delimiters for bracketed identifiers ([ObjectName]), or quoted identifiers ("ObjectName").</span></span> <span data-ttu-id="85c11-123">配對比對不會比對字串常值 ('string') 的單引號分隔符號，因為色彩編碼已經提供字串是否已分隔的視覺指示。</span><span class="sxs-lookup"><span data-stu-id="85c11-123">Pair matching does not match the single quotation delimiters for string literals ('string') because color coding already gives a visual indication of whether the string has been delimited.</span></span>  
  
### <a name="delimiter-highlighting"></a><span data-ttu-id="85c11-124">分隔符號反白顯示</span><span class="sxs-lookup"><span data-stu-id="85c11-124">Delimiter Highlighting</span></span>  
 <span data-ttu-id="85c11-125">比對會反白顯示一對分隔符號的開頭和結束元素。</span><span class="sxs-lookup"><span data-stu-id="85c11-125">Matching highlights both the lead and closing element of a pair of delimiters.</span></span> <span data-ttu-id="85c11-126">這可讓您以視覺化方式識別程式碼區塊並檢查是否有不對稱的分隔符號組。</span><span class="sxs-lookup"><span data-stu-id="85c11-126">This lets you visually identify code blocks and check for mismatched pairs of delimiters.</span></span>  
  
 <span data-ttu-id="85c11-127">當您輸入完成配對的最後一個字母時，分隔符號就會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="85c11-127">Delimiters are highlighted when you type the final letter that completes the pair.</span></span> <span data-ttu-id="85c11-128">例如，在您先輸入 BEGIN 然後接著 END 的 BEGIN END 配對中，當您輸入 END 的最後一個字母時，反白顯示就會開啟。</span><span class="sxs-lookup"><span data-stu-id="85c11-128">For example, for a BEGIN END pair where you type BEGIN first followed by END, highlighting turns on when you type the final letter in END.</span></span> <span data-ttu-id="85c11-129">您不需要輸入開頭分隔符號，後面接著結尾分隔符號，即可開啟反白顯示。</span><span class="sxs-lookup"><span data-stu-id="85c11-129">You do not have to type the lead delimiter followed by the closing delimiter to turn on highlighting.</span></span> <span data-ttu-id="85c11-130">如果您先輸入 END，然後向上捲動指令碼並輸入 BEGIN，則當您輸入 BEGIN 的最後一個字母時，反白顯示就會開啟。</span><span class="sxs-lookup"><span data-stu-id="85c11-130">If you type END first, then scroll back up the script and type BEGIN, highlighting is turned on when you type the final letter in BEGIN.</span></span> <span data-ttu-id="85c11-131">輸入的最後一個字母不需要是分隔符號中的結尾字母。</span><span class="sxs-lookup"><span data-stu-id="85c11-131">The final letter typed does not have to be the end letter in the delimiter.</span></span> <span data-ttu-id="85c11-132">例如，您可能會將 BEGIN 拼錯為 BEIN。當您插入最後一個 G 時，BEGIN END 配對就會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="85c11-132">For example, you could misspell BEGIN as BEIN, when you insert the final G the BEGIN END pair is highlighted.</span></span>  
  
 <span data-ttu-id="85c11-133">分隔符號組會維持反白顯示，直到您移動游標為止。</span><span class="sxs-lookup"><span data-stu-id="85c11-133">The delimiter pair remains highlighted until you move the cursor.</span></span> <span data-ttu-id="85c11-134">當游標移動時，反白顯示就會關閉，即使新的游標位置維持在相同的分隔符號中也一樣。</span><span class="sxs-lookup"><span data-stu-id="85c11-134">The highlighting is turned off when the cursor is moved, even if the new cursor position remains in the same delimiter.</span></span> <span data-ttu-id="85c11-135">您可以透過刪除並重新輸入任何一個配對成員的任何字母，重新開啟反白顯示。</span><span class="sxs-lookup"><span data-stu-id="85c11-135">You can turn the highlighting back on by deleting and retyping any letter in either member of the pair.</span></span>  
  
## <a name="analysis-services-xmla-query-editor-brace-matching"></a><span data-ttu-id="85c11-136">Analysis Services XMLA 查詢編輯器的大括號比對</span><span class="sxs-lookup"><span data-stu-id="85c11-136">Analysis Services XMLA Query Editor Brace Matching</span></span>  
 <span data-ttu-id="85c11-137">XMLA 查詢編輯器的大括號比對會透過反白顯示左右大括號，顯示您是否已關閉元素。</span><span class="sxs-lookup"><span data-stu-id="85c11-137">The XMLA Query Editor brace matching shows if you have closed elements by highlighting opening and closing braces.</span></span> <span data-ttu-id="85c11-138">您也可以使用 CTRL+] 鍵盤快速鍵，從一個大括號跳至對稱的大括號。</span><span class="sxs-lookup"><span data-stu-id="85c11-138">You can also use the CTRL+] keyboard shortcut to jump from one brace to the matching brace.</span></span>  
  
 <span data-ttu-id="85c11-139">XMLA 查詢編輯器會針對下列詞彙進行大括號比對：</span><span class="sxs-lookup"><span data-stu-id="85c11-139">The XMLA Query Editor does brace matching for the following terms:</span></span>  
  
-   <span data-ttu-id="85c11-140">對稱的開始與結束標記。</span><span class="sxs-lookup"><span data-stu-id="85c11-140">Matching start and end tags.</span></span>  
  
-   <span data-ttu-id="85c11-141">任何一對「」 \<" and "> 角括弧。</span><span class="sxs-lookup"><span data-stu-id="85c11-141">Any pair of "\<" and ">" angle brackets.</span></span>  
  
-   <span data-ttu-id="85c11-142">註解的開始與結束。</span><span class="sxs-lookup"><span data-stu-id="85c11-142">Start and end of comments.</span></span>  
  
-   <span data-ttu-id="85c11-143">處理指示的開始與結束。</span><span class="sxs-lookup"><span data-stu-id="85c11-143">Start and end of processing instructions.</span></span>  
  
-   <span data-ttu-id="85c11-144">CDATA 區塊的開始與結束。</span><span class="sxs-lookup"><span data-stu-id="85c11-144">Start and end of CDATA blocks.</span></span>  
  
-   <span data-ttu-id="85c11-145">DTD 宣告的開始與結束。</span><span class="sxs-lookup"><span data-stu-id="85c11-145">Start and end of DTD declarations.</span></span>  
  
-   <span data-ttu-id="85c11-146">屬性上的開頭及結束引號。</span><span class="sxs-lookup"><span data-stu-id="85c11-146">Opening and closing quotes on attributes.</span></span>  
  
## <a name="mdx-and-dmx-editor-parenthesis-matching"></a><span data-ttu-id="85c11-147">MDX 和 DMX 編輯器的括號比對</span><span class="sxs-lookup"><span data-stu-id="85c11-147">MDX and DMX Editor Parenthesis Matching</span></span>  
 <span data-ttu-id="85c11-148">多維度運算式 (MDX) 和資料採礦運算式 (DMX) 編輯器會自動比對函式中的括號組。</span><span class="sxs-lookup"><span data-stu-id="85c11-148">The Multi-Dimensional Expressions (MDX) and Data Mining Expressions (DMX) Editors automatically match parenthesis pairs in functions.</span></span>  
  
  
