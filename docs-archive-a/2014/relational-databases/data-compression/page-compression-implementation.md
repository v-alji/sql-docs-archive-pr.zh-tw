---
title: 頁面壓縮實作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- page compression [Database Engine]
- compression [SQL Server], page
ms.assetid: 78c83277-1dbb-4e07-95bd-47b14d2b5cd4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e6edba79d1548d68e60f406d370abd5354a62fcb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598998"
---
# <a name="page-compression-implementation"></a><span data-ttu-id="0ad71-102">頁面壓縮實作</span><span class="sxs-lookup"><span data-stu-id="0ad71-102">Page Compression Implementation</span></span>
  <span data-ttu-id="0ad71-103">本主題摘要說明 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 如何實作頁面壓縮。</span><span class="sxs-lookup"><span data-stu-id="0ad71-103">This topic summarizes how the [!INCLUDE[ssDE](../../includes/ssde-md.md)] implements page compression.</span></span> <span data-ttu-id="0ad71-104">這個摘要提供協助您計畫資料所需之儲存空間的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="0ad71-104">This summary provides basic information to help you plan the storage space that you need for your data.</span></span>  
  
 <span data-ttu-id="0ad71-105">資料表、資料表資料分割、索引和索引資料分割的頁面壓縮都很類似。</span><span class="sxs-lookup"><span data-stu-id="0ad71-105">Page compression is similar for tables, table partitions, indexes, and index partitions.</span></span> <span data-ttu-id="0ad71-106">下列的資料表頁面壓縮描述同樣適用於所有物件類型的頁面壓縮。</span><span class="sxs-lookup"><span data-stu-id="0ad71-106">The following description of page compression for a table applies equally to page compression for all object types.</span></span> <span data-ttu-id="0ad71-107">下列範例會壓縮字元字串，但前置詞和字典壓縮會對其他的資料類型套用相同的原則。</span><span class="sxs-lookup"><span data-stu-id="0ad71-107">The following examples compress character strings, but both prefix and dictionary compression apply the same principles to other data types.</span></span>  
  
 <span data-ttu-id="0ad71-108">以頁面壓縮來壓縮資料表及索引的分葉層級是由下列順序的三種作業組成：</span><span class="sxs-lookup"><span data-stu-id="0ad71-108">Compressing the leaf level of tables and indexes with page compression consists of three operations in the following order:</span></span>  
  
1.  <span data-ttu-id="0ad71-109">資料列壓縮</span><span class="sxs-lookup"><span data-stu-id="0ad71-109">Row compression</span></span>  
  
2.  <span data-ttu-id="0ad71-110">前置詞壓縮</span><span class="sxs-lookup"><span data-stu-id="0ad71-110">Prefix compression</span></span>  
  
3.  <span data-ttu-id="0ad71-111">字典壓縮</span><span class="sxs-lookup"><span data-stu-id="0ad71-111">Dictionary compression</span></span>  
  
 <span data-ttu-id="0ad71-112">在您使用頁面壓縮時，索引的非分葉層級頁面會藉由僅使用資料列壓縮來進行壓縮。</span><span class="sxs-lookup"><span data-stu-id="0ad71-112">When you use page compression, non-leaf-level pages of indexes are compressed by using only row compression.</span></span> <span data-ttu-id="0ad71-113">如需資料列壓縮的詳細資訊，請參閱 [資料列壓縮實作](../data-compression/row-compression-implementation.md)。</span><span class="sxs-lookup"><span data-stu-id="0ad71-113">For more information about row compression, see [Row Compression Implementation](../data-compression/row-compression-implementation.md).</span></span>  
  
## <a name="prefix-compression"></a><span data-ttu-id="0ad71-114">前置詞壓縮</span><span class="sxs-lookup"><span data-stu-id="0ad71-114">Prefix Compression</span></span>  
 <span data-ttu-id="0ad71-115">對於進行壓縮的每個頁面，前置詞壓縮會使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="0ad71-115">For each page that is being compressed, prefix compression uses the following steps:</span></span>  
  
1.  <span data-ttu-id="0ad71-116">針對每個欄位識別一個值，以用來減少每個資料行中值的儲存空間。</span><span class="sxs-lookup"><span data-stu-id="0ad71-116">For each column, a value is identified that can be used to reduce the storage space for the values in each column.</span></span>  
  
2.  <span data-ttu-id="0ad71-117">會建立代表每個資料行前置詞值的資料列，並將其儲存在緊接在頁面標頭後的壓縮資訊 (CI) 結構中。</span><span class="sxs-lookup"><span data-stu-id="0ad71-117">A row that represents the prefix values for each column is created and stored in the compression information (CI) structure that immediately follows the page header.</span></span>  
  
3.  <span data-ttu-id="0ad71-118">資料行中重複的前置詞值會由對應之前置詞的參考取代。</span><span class="sxs-lookup"><span data-stu-id="0ad71-118">The repeated prefix values in the column are replaced by a reference to the corresponding prefix.</span></span> <span data-ttu-id="0ad71-119">如果資料列中的值不完全符合選取的前置詞值，仍可指出部分相符。</span><span class="sxs-lookup"><span data-stu-id="0ad71-119">If the value in a row does not exactly match the selected prefix value, a partial match can still be indicated.</span></span>  
  
 <span data-ttu-id="0ad71-120">下列圖例顯示資料表範例頁面在前置詞壓縮前的狀況。</span><span class="sxs-lookup"><span data-stu-id="0ad71-120">The following illustration shows a sample page of a table before prefix compression.</span></span>  
  
 <span data-ttu-id="0ad71-121">![前置詞壓縮前的頁面](../media/skt-tblcompression1c.gif "前置詞壓縮前的頁面")</span><span class="sxs-lookup"><span data-stu-id="0ad71-121">![Page before prefix compression](../media/skt-tblcompression1c.gif "Page before prefix compression")</span></span>  
  
 <span data-ttu-id="0ad71-122">下列圖例顯示相同頁面在前置詞壓縮後的狀況。</span><span class="sxs-lookup"><span data-stu-id="0ad71-122">The following illustration shows the same page after prefix compression.</span></span> <span data-ttu-id="0ad71-123">前置詞會移到標頭，而資料行值則變更為前置詞的參考。</span><span class="sxs-lookup"><span data-stu-id="0ad71-123">The prefix is moved to the header, and the column values are changed to references to the prefix.</span></span>  
  
 <span data-ttu-id="0ad71-124">![前置詞壓縮後的頁面](../media/tblcompression2.gif "前置詞壓縮後的頁面")</span><span class="sxs-lookup"><span data-stu-id="0ad71-124">![Page after prefix compression](../media/tblcompression2.gif "Page after prefix compression")</span></span>  
  
 <span data-ttu-id="0ad71-125">在第一個資料列的第一個資料行中，值 4b 指出該資料列會有前置詞 (aaab) 的前四個字元和字元 b。</span><span class="sxs-lookup"><span data-stu-id="0ad71-125">In the first column of the first row, the value 4b indicates that the first four characters of the prefix (aaab) are present for that row, and also the character b.</span></span> <span data-ttu-id="0ad71-126">這樣會產生結果值 aaabb，即為原始值。</span><span class="sxs-lookup"><span data-stu-id="0ad71-126">This makes the resultant value aaabb, which is the original value.</span></span>  
  
## <a name="dictionary-compression"></a><span data-ttu-id="0ad71-127">字典壓縮</span><span class="sxs-lookup"><span data-stu-id="0ad71-127">Dictionary Compression</span></span>  
 <span data-ttu-id="0ad71-128">在完成前置詞壓縮後，就會套用字典壓縮。</span><span class="sxs-lookup"><span data-stu-id="0ad71-128">After prefix compression has been completed, dictionary compression is applied.</span></span> <span data-ttu-id="0ad71-129">字典壓縮會搜尋頁面上的任何位置是否有重複的值，然後將它們儲存在 CI 區域中。</span><span class="sxs-lookup"><span data-stu-id="0ad71-129">Dictionary compression searches for repeated values anywhere on the page, and stores them in the CI area.</span></span> <span data-ttu-id="0ad71-130">與前置詞壓縮不同的是，字典壓縮並不是限定於單一資料行。</span><span class="sxs-lookup"><span data-stu-id="0ad71-130">Unlike prefix compression, dictionary compression is not restricted to one column.</span></span> <span data-ttu-id="0ad71-131">字典壓縮可以取代頁面上任何位置的重複值。</span><span class="sxs-lookup"><span data-stu-id="0ad71-131">Dictionary compression can replace repeated values that occur anywhere on a page.</span></span> <span data-ttu-id="0ad71-132">下列圖例顯示相同頁面在字典壓縮後的狀況。</span><span class="sxs-lookup"><span data-stu-id="0ad71-132">The following illustration shows the same page after dictionary compression.</span></span>  
  
 <span data-ttu-id="0ad71-133">![字典壓縮後的頁面](../media/tblcompression3.gif "字典壓縮後的頁面")</span><span class="sxs-lookup"><span data-stu-id="0ad71-133">![Page after dictionary compression](../media/tblcompression3.gif "Page after dictionary compression")</span></span>  
  
 <span data-ttu-id="0ad71-134">請注意，值 4b 已由頁面的不同資料行參考。</span><span class="sxs-lookup"><span data-stu-id="0ad71-134">Note that the value 4b has been referenced from different columns of the page.</span></span>  
  
## <a name="when-page-compression-occurs"></a><span data-ttu-id="0ad71-135">何時會發生頁面壓縮</span><span class="sxs-lookup"><span data-stu-id="0ad71-135">When Page Compression Occurs</span></span>  
 <span data-ttu-id="0ad71-136">在建立具有頁面壓縮的新資料表時，不會進行任何壓縮。</span><span class="sxs-lookup"><span data-stu-id="0ad71-136">When a new table is created that has page compression, no compression occurs.</span></span> <span data-ttu-id="0ad71-137">不過，資料表的中繼資料指出應該使用頁面壓縮。</span><span class="sxs-lookup"><span data-stu-id="0ad71-137">However, the metadata for the table indicates that page compression should be used.</span></span> <span data-ttu-id="0ad71-138">資料在新增至第一個資料頁面時會進行資料列壓縮。</span><span class="sxs-lookup"><span data-stu-id="0ad71-138">As data is added to the first data page, data is row-compressed.</span></span> <span data-ttu-id="0ad71-139">因為頁面尚未填滿，所以無法藉由頁面壓縮取得任何優點。</span><span class="sxs-lookup"><span data-stu-id="0ad71-139">Because the page is not full, no benefit is gained from page compression.</span></span> <span data-ttu-id="0ad71-140">當頁面填滿時，下一個新增的資料列就會起始頁面壓縮作業。</span><span class="sxs-lookup"><span data-stu-id="0ad71-140">When the page is full, the next row to be added initiates the page compression operation.</span></span> <span data-ttu-id="0ad71-141">此時會檢視整個頁面；每個資料行都會受到評估，查看是否要進行前置詞壓縮，然後再評估是否要進行字典壓縮。</span><span class="sxs-lookup"><span data-stu-id="0ad71-141">The whole page is reviewed; each column is evaluated for prefix compression, and then all columns are evaluated for dictionary compression.</span></span> <span data-ttu-id="0ad71-142">如果頁面壓縮已在頁面上建立足夠的空間容納額外的資料列，則會新增該資料列，然後再對資料進行資料列壓縮及頁面壓縮。</span><span class="sxs-lookup"><span data-stu-id="0ad71-142">If page compression has created enough room on the page for an additional row, the row is added, and the data is both row- and page-compressed.</span></span> <span data-ttu-id="0ad71-143">如果透過頁面壓縮所取得的空間與 CI 結構所需的空間之間的差異並不明顯，則不會針對該頁面使用頁面壓縮。</span><span class="sxs-lookup"><span data-stu-id="0ad71-143">If the space gained by page compression minus the space that is required for the CI structure is not significant, page compression is not used for that page.</span></span> <span data-ttu-id="0ad71-144">新頁面若可以容納未來的資料列則已，若不能容納，就會對資料表新增新的頁面。</span><span class="sxs-lookup"><span data-stu-id="0ad71-144">Future rows either fit onto the new page or, if they do not fit, a new page is added to the table.</span></span> <span data-ttu-id="0ad71-145">新頁面一開始並不會進行頁面壓縮，這與第一個頁面類似。</span><span class="sxs-lookup"><span data-stu-id="0ad71-145">Similar to the first page, the new page is not at first page-compressed.</span></span>  
  
 <span data-ttu-id="0ad71-146">當包含資料的現有資料表轉換成頁面壓縮時，每個頁面都會重建且接受評估。</span><span class="sxs-lookup"><span data-stu-id="0ad71-146">When an existing table that contains data is converted to page compression, each page is rebuilt and evaluated.</span></span> <span data-ttu-id="0ad71-147">重建所有頁面會導致資料表、索引或資料分割的重建。</span><span class="sxs-lookup"><span data-stu-id="0ad71-147">Rebuilding all the pages causes the rebuilding of the table, index, or partition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ad71-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ad71-148">See Also</span></span>  
 <span data-ttu-id="0ad71-149">[資料壓縮](data-compression.md) </span><span class="sxs-lookup"><span data-stu-id="0ad71-149">[Data Compression](data-compression.md) </span></span>  
 [<span data-ttu-id="0ad71-150">資料列壓縮實作</span><span class="sxs-lookup"><span data-stu-id="0ad71-150">Row Compression Implementation</span></span>](row-compression-implementation.md)  
  
  
