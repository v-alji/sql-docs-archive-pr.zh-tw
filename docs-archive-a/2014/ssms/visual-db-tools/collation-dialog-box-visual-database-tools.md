---
title: 定序對話方塊 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.definecolumncollation
- vdtsql.chm:65561
ms.assetid: e4020f79-7abf-4839-b9b2-984ef7049817
author: stevestein
ms.author: sstein
ms.openlocfilehash: d551b2ae7ca27250c144afedf13038efd78ad6ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607193"
---
# <a name="collation-dialog-box-visual-database-tools"></a><span data-ttu-id="68728-102">定序對話方塊 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="68728-102">Collation Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="68728-103">這個對話方塊讓您指定資料行的定序序列 (Collation Sequence)。</span><span class="sxs-lookup"><span data-stu-id="68728-103">This dialog box lets you specify a collation sequence for the column.</span></span> <span data-ttu-id="68728-104">在將資料行的值與另一個資料行的值或常數值進行比較的任何作業中，會使用資料行的定序序列。</span><span class="sxs-lookup"><span data-stu-id="68728-104">A column's collation sequence is used in any operation that compares values of the column to another column or to constant values.</span></span> <span data-ttu-id="68728-105">它也會影響某些字串函數的行為，例如 SUBSTRING 和 CHARINDEX。</span><span class="sxs-lookup"><span data-stu-id="68728-105">It also affects the behavior of some string functions, such as SUBSTRING and CHARINDEX.</span></span> <span data-ttu-id="68728-106">如需資料行定序設定作用的完整清單，請參閱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 文件。</span><span class="sxs-lookup"><span data-stu-id="68728-106">For a complete list of the effects of a column's collation setting, see the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentation.</span></span>  
  
 <span data-ttu-id="68728-107">下列情況會出現這個對話方塊：</span><span class="sxs-lookup"><span data-stu-id="68728-107">This dialog box appears:</span></span>  
  
-   <span data-ttu-id="68728-108">在 [資料行屬性]  索引標籤的 [定序]  欄位中輸入無效的定序名稱。</span><span class="sxs-lookup"><span data-stu-id="68728-108">If you enter an invalid collation name in the **Collation** field on the **Column Properties** tab.</span></span>  
  
-   <span data-ttu-id="68728-109">在 [資料行屬性] 索引標籤的 [定序] 欄位中按一下，然後按一下欄位右側的省略符號按鈕 ( **...** )。</span><span class="sxs-lookup"><span data-stu-id="68728-109">If you click in the **Collation** field on the **Column Properties** tab, and then click the ellipsis button (**...**) to the right of the field.</span></span>  
  
## <a name="options"></a><span data-ttu-id="68728-110">選項。</span><span class="sxs-lookup"><span data-stu-id="68728-110">Options</span></span>  
 <span data-ttu-id="68728-111">**SQL 定序**</span><span class="sxs-lookup"><span data-stu-id="68728-111">**SQL Collation**</span></span>  
 <span data-ttu-id="68728-112">從下拉式清單中選擇 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所定義的定序序列。</span><span class="sxs-lookup"><span data-stu-id="68728-112">Choose among the collation sequences defined by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the drop-down list.</span></span>  
  
 <span data-ttu-id="68728-113">**Windows 定序**</span><span class="sxs-lookup"><span data-stu-id="68728-113">**Windows Collation**</span></span>  
 <span data-ttu-id="68728-114">從下拉式清單中選擇 Windows 所定義的定序序列。</span><span class="sxs-lookup"><span data-stu-id="68728-114">Choose among the collation sequences defined by Windows from the drop-down list.</span></span>  
  
 <span data-ttu-id="68728-115">**二進位編碼排序**</span><span class="sxs-lookup"><span data-stu-id="68728-115">**Binary Sort**</span></span>  
 <span data-ttu-id="68728-116">使用字元值的二進位碼進行比較。</span><span class="sxs-lookup"><span data-stu-id="68728-116">Use the binary codes of character values for comparisons.</span></span> <span data-ttu-id="68728-117">如果選取此選項，某些字母順序比較選項會無法使用。</span><span class="sxs-lookup"><span data-stu-id="68728-117">If you select this option, certain alphabetic comparison options become unavailable.</span></span> <span data-ttu-id="68728-118">例如，區分字母大小寫的比較會無法使用，因為大寫字母和小寫字母有不同的二進位編碼方式。</span><span class="sxs-lookup"><span data-stu-id="68728-118">For example, case-insensitive comparisons become unavailable because uppercase letters and lowercase letters have different binary encodings.</span></span> <span data-ttu-id="68728-119">只有在選取 [Windows 定序]  時適用。</span><span class="sxs-lookup"><span data-stu-id="68728-119">Applies only if you select **Windows collation**.</span></span>  
  
 <span data-ttu-id="68728-120">**字典排序**</span><span class="sxs-lookup"><span data-stu-id="68728-120">**Dictionary Sort**</span></span>  
 <span data-ttu-id="68728-121">使用字母順序比較選項。</span><span class="sxs-lookup"><span data-stu-id="68728-121">Use alphabetic comparison options.</span></span> <span data-ttu-id="68728-122">只有在選取 [Windows 定序]  時適用。</span><span class="sxs-lookup"><span data-stu-id="68728-122">Applies only if you select **Windows collation**.</span></span> <span data-ttu-id="68728-123">The alphabetic comparisons options are:</span><span class="sxs-lookup"><span data-stu-id="68728-123">The alphabetic comparisons options are:</span></span>  
  
-   <span data-ttu-id="68728-124">**區分大小寫** ：若要比較作業將大寫和小寫字母視為不相同，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="68728-124">**Case Sensitive** Select this if you want comparisons to consider uppercase and lowercase letters to be unequal.</span></span>  
  
-   <span data-ttu-id="68728-125">**區分腔調字** (Accent Sensitive)：若要比較作業將腔調字母和非腔調字母視為不相同，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="68728-125">**Accent Sensitive** Select this if you want comparisons to consider accented and unaccented letters to be unequal.</span></span> <span data-ttu-id="68728-126">如果選取此選項，比較作業也會將不同的腔調字母視為不相同。</span><span class="sxs-lookup"><span data-stu-id="68728-126">If you select this, comparisons will also consider differently accented letters to be unequal.</span></span>  
  
-   <span data-ttu-id="68728-127">**區分假名** ：若要比較作業將日文音節的片假名和平假名視為不相同，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="68728-127">**Kana Sensitive** Select this if you want comparisons to consider katakana and hiragana Japanese syllables to be unequal.</span></span>  
  
-   <span data-ttu-id="68728-128">**全半形需相符** (Width Sensitive)：若要比較作業將半形字元和全形字元視為不相同，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="68728-128">**Width Sensitive** Select this if you want comparisons to consider half-width and full-width characters to be unequal.</span></span>  
  
 <span data-ttu-id="68728-129">**還原預設值按鈕**</span><span class="sxs-lookup"><span data-stu-id="68728-129">**Restore Default Button**</span></span>  
 <span data-ttu-id="68728-130">對此資料行套用預設的資料庫定序序列。</span><span class="sxs-lookup"><span data-stu-id="68728-130">Apply the default collation sequence for the database to the column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68728-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68728-131">See Also</span></span>  
 [<span data-ttu-id="68728-132">在彙總查詢中使用資料行 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="68728-132">Work with Columns in Aggregate Queries &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
