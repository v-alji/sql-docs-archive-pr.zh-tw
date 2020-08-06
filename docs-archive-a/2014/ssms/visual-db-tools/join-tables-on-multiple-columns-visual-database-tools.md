---
title: 以多個資料行聯結資料表 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiple column joins
- joins [SQL Server], multiple columns
ms.assetid: 56a158bc-a42a-4b78-baad-4721d2d22cd3
author: stevestein
ms.author: sstein
ms.openlocfilehash: dda52fe27b2034242c8cbf458dd010240c792146
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596424"
---
# <a name="join-tables-on-multiple-columns-visual-database-tools"></a><span data-ttu-id="e3565-102">以多個資料行聯結資料表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e3565-102">Join Tables on Multiple Columns (Visual Database Tools)</span></span>
  <span data-ttu-id="e3565-103">可以聯結具有多重資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="e3565-103">You can join tables with multiple columns.</span></span> <span data-ttu-id="e3565-104">也就是說，可以建立查詢，使其找出兩個資料表中滿足多重條件的資料列。</span><span class="sxs-lookup"><span data-stu-id="e3565-104">That is, you can create a query that matches rows from the two tables only if they satisfy multiple conditions.</span></span> <span data-ttu-id="e3565-105">如果資料庫包含使某資料表中多重外部索引鍵資料行符合另一個資料表中多重資料行主索引鍵的關聯性，則可以使用此關聯性來建立多重資料行聯結。</span><span class="sxs-lookup"><span data-stu-id="e3565-105">If the database contains a relationship matching multiple foreign-key columns in one table to a multicolumn primary key in the other table, you can use this relationship to create a multicolumn join.</span></span> <span data-ttu-id="e3565-106">如需詳細資料，請參閱[自動聯結資料表 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="e3565-106">For details, see [Join Tables Automatically &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="e3565-107">即使資料庫不包含多重資料行外部索引鍵關聯性，也可以手動建立聯結。</span><span class="sxs-lookup"><span data-stu-id="e3565-107">Even if the database contains no multi-column foreign-key relationship, you can create the join manually.</span></span>  
  
### <a name="to-manually-create-a-multicolumn-join"></a><span data-ttu-id="e3565-108">若要手動建立多重資料行聯結</span><span class="sxs-lookup"><span data-stu-id="e3565-108">To manually create a multicolumn join</span></span>  
  
1.  <span data-ttu-id="e3565-109">將您要聯結的資料表新增到 [圖表窗格](diagram-pane-visual-database-tools.md) 中。</span><span class="sxs-lookup"><span data-stu-id="e3565-109">Add to the [Diagram pane](diagram-pane-visual-database-tools.md) the tables you want to join.</span></span>  
  
2.  <span data-ttu-id="e3565-110">將第一個資料表視窗中的第一個聯結資料行，拖放至第二個資料表視窗中的相關資料行。</span><span class="sxs-lookup"><span data-stu-id="e3565-110">Drag the name of the first join column in the first table window and drop it onto the related column in the second table window.</span></span> <span data-ttu-id="e3565-111">不可讓聯結以 text、ntext 或 image 資料行為基礎。</span><span class="sxs-lookup"><span data-stu-id="e3565-111">You cannot base a join on text, ntext, or image columns.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e3565-112">一般來說，聯結資料行必須具有相同的 (或相容的) 資料類型。</span><span class="sxs-lookup"><span data-stu-id="e3565-112">In general, the join columns must be of the same (or compatible) data types.</span></span> <span data-ttu-id="e3565-113">例如，如果第一個資料表的聯結資料行為日期，就必須關聯至第二個資料表的日期資料行。</span><span class="sxs-lookup"><span data-stu-id="e3565-113">For example, if the join column in the first table is a date, you must relate it to a date column in the second table.</span></span> <span data-ttu-id="e3565-114">另一方面，如果第一個聯結資料行為整數，則關聯的聯結資料行也必須為整數資料類型，但其大小可有所不同。</span><span class="sxs-lookup"><span data-stu-id="e3565-114">On the other hand, if the first join column is an integer, the related join column must also be of an integer data type, but it can be a different size.</span></span> <span data-ttu-id="e3565-115">然而，可能會發生隱含的資料類型轉換聯結似乎不相容的資料行的情形。</span><span class="sxs-lookup"><span data-stu-id="e3565-115">However, there may be cases where implicit data type conversions can join seemingly incompatible columns will work.</span></span>  
    >   
    >  <span data-ttu-id="e3565-116">[查詢和檢視設計工具](query-and-view-designer-tools-visual-database-tools.md) 不會檢查您建立聯結時所使用的資料行資料類型，但當您執行查詢時，若資料類型不相容，資料庫便會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="e3565-116">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) will not check the data types of the columns you use to create a join, but when you execute the query, the database will display an error if the data types are not compatible.</span></span>  
  
3.  <span data-ttu-id="e3565-117">將第一個資料表視窗中的第二個聯結資料行，拖放至第二個資料表視窗中的相關資料行。</span><span class="sxs-lookup"><span data-stu-id="e3565-117">Drag the name of the second join column in the first table window and drop it onto the related column in the second table window.</span></span>  
  
4.  <span data-ttu-id="e3565-118">對兩個資料表中其他的聯結資料行重複步驟 3。</span><span class="sxs-lookup"><span data-stu-id="e3565-118">Repeat step 3 for each additional pair of join columns in the two tables.</span></span>  
  
5.  <span data-ttu-id="e3565-119">執行查詢。</span><span class="sxs-lookup"><span data-stu-id="e3565-119">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3565-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3565-120">See Also</span></span>  
 [<span data-ttu-id="e3565-121">使用聯結查詢 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="e3565-121">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
