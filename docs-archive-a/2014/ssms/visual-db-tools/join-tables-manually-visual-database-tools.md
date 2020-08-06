---
title: 手動聯結資料表 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- manual joins [SQL Server]
- joins [SQL Server], manual
- joins [SQL Server], creating
ms.assetid: 9c785356-646b-4c87-82d4-25efd6051d9d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83f7615be3f5f18164dd3ca0f62ef6cbd9167be3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686687"
---
# <a name="join-tables-manually-visual-database-tools"></a><span data-ttu-id="01e62-102">手動聯結資料表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="01e62-102">Join Tables Manually (Visual Database Tools)</span></span>
  <span data-ttu-id="01e62-103">在新增兩個 (或更多) 資料表至查詢時， [查詢和檢視表設計工具](visual-database-tools.md) 會根據通用資料或資料庫中所儲存有關資料表關聯方式的資訊，聯結這些資料表。</span><span class="sxs-lookup"><span data-stu-id="01e62-103">When you add two (or more) tables to a query, the [Query and View Designer](visual-database-tools.md) attempts to join them based on common data or on information stored in the database about how tables are related.</span></span> <span data-ttu-id="01e62-104">如需詳細資料，請參閱[自動聯結資料表 &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="01e62-104">For details, see [Join Tables Automatically &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md).</span></span> <span data-ttu-id="01e62-105">不過，如果 [查詢和檢視設計師] 尚未自動聯結資料表，或者想要在資料表間建立額外的聯結，則可以手動聯結資料表。</span><span class="sxs-lookup"><span data-stu-id="01e62-105">However, if the Query and View Designer has not joined the tables automatically, or if you want to create additional join conditions between tables, you can join tables manually.</span></span>  
  
 <span data-ttu-id="01e62-106">可以根據任兩個資料行間的比較來建立聯結，而不只是根據包含相同資訊的資料行。</span><span class="sxs-lookup"><span data-stu-id="01e62-106">You can create joins based on comparisons between any two columns, not just columns that contain the same information.</span></span> <span data-ttu-id="01e62-107">例如，如果資料庫包含兩個資料表 `titles` 和 `roysched`，則可以比較 `ytd_sales` 資料表的 `titles` 資料行與 `lorange` 資料表的 `hirange` 和 `roysched` 資料行的值。</span><span class="sxs-lookup"><span data-stu-id="01e62-107">For example, if your database contains two tables, `titles` and `roysched`, you can compare values in the `ytd_sales` column of the `titles` table against the `lorange` and `hirange` columns in the `roysched` table.</span></span> <span data-ttu-id="01e62-108">建立此聯結將可讓您找到年度迄今的版稅支出落於低和高範圍之間的書名。</span><span class="sxs-lookup"><span data-stu-id="01e62-108">Creating this join would allow you to find titles for which the year-to-date sales falls between the low and high ranges for the royalty payments.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="01e62-109">如果聯結條件中的資料行已經建立索引，則聯結會工作得較快。</span><span class="sxs-lookup"><span data-stu-id="01e62-109">Joins work fastest if the columns in the join condition have been indexed.</span></span> <span data-ttu-id="01e62-110">在某些狀況下，聯結未建立索引的資料行將導致較慢的查詢。</span><span class="sxs-lookup"><span data-stu-id="01e62-110">In some cases, joining on unindexed columns can result in a slow query.</span></span>  
  
### <a name="to-manually-join-tables-or-table-structured-objects"></a><span data-ttu-id="01e62-111">若要手動聯結資料表或表格化物件</span><span class="sxs-lookup"><span data-stu-id="01e62-111">To manually join tables or table-structured objects</span></span>  
  
1.  <span data-ttu-id="01e62-112">將想要聯結的物件新增至 [圖表窗格](diagram-pane-visual-database-tools.md) 中。</span><span class="sxs-lookup"><span data-stu-id="01e62-112">Add to the [Diagram pane](diagram-pane-visual-database-tools.md) the objects you want to join.</span></span>  
  
2.  <span data-ttu-id="01e62-113">將聯結資料行的名稱拖曳至第一個資料表或表格化物件上，然後將它放在第二個資料表或表格化物件的關聯資料行中。</span><span class="sxs-lookup"><span data-stu-id="01e62-113">Drag the name of the join column in the first table or table-structured object and drop it onto the related column in the second table or table-structured object.</span></span> <span data-ttu-id="01e62-114">不可讓聯結以 `text`、`ntext` 或 i`mage` 資料行為基礎。</span><span class="sxs-lookup"><span data-stu-id="01e62-114">You cannot base a join on `text`, `ntext`, or i`mage` columns.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="01e62-115">聯結資料行必須具有相同的 (或相容的) 資料類型。</span><span class="sxs-lookup"><span data-stu-id="01e62-115">The join columns must be of the same (or compatible) data types.</span></span> <span data-ttu-id="01e62-116">例如，如果第一個資料表的聯結資料行為日期，就必須關聯至第二個資料表的日期資料行。</span><span class="sxs-lookup"><span data-stu-id="01e62-116">For example, if the join column in the first table is a date, you must relate it to a date column in the second table.</span></span> <span data-ttu-id="01e62-117">另一方面，如果第一個聯結資料行為整數，則關聯的聯結資料行也必須為整數資料類型，但其大小可有所不同。</span><span class="sxs-lookup"><span data-stu-id="01e62-117">On the other hand, if the first join column is an integer, the related join column must also be of an integer data type, but it can be a different size.</span></span> <span data-ttu-id="01e62-118">[查詢和檢視設計師] 不會檢查用來建立聯結的資料行資料類型，但在執行查詢時，如果資料類型不相容，則資料庫將顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="01e62-118">The Query and View Designer will not check the data types of the columns you use to create a join, but when you execute the query, the database will display an error if the data types are not compatible.</span></span>  
  
3.  <span data-ttu-id="01e62-119">必要時，請變更聯結運算子。在預設狀況下，此運算子為等號 (=)。</span><span class="sxs-lookup"><span data-stu-id="01e62-119">If necessary, change the join operator; by default, the operator is an equal sign (=).</span></span> <span data-ttu-id="01e62-120">如需詳細資訊，請參閱[修改聯結運算子 &#40;Visual Database Tools&#41;](modify-join-operators-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="01e62-120">For details, see [Modify Join Operators &#40;Visual Database Tools&#41;](modify-join-operators-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="01e62-121">查詢和檢視表設計工具會將 INNER JOIN 子句新增至 [SQL 窗格](sql-pane-visual-database-tools.md)中的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="01e62-121">The Query and View Designer adds an INNER JOIN clause to the SQL statement in the [SQL pane](sql-pane-visual-database-tools.md).</span></span> <span data-ttu-id="01e62-122">您可以將類型變更為外部聯結 (Outer Join)。</span><span class="sxs-lookup"><span data-stu-id="01e62-122">You can change the type to an outer join.</span></span> <span data-ttu-id="01e62-123">如需詳細資訊，請參閱[建立外部聯結 &#40;Visual Database Tools&#41;](create-outer-joins-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="01e62-123">For details see [Create Outer Joins &#40;Visual Database Tools&#41;](create-outer-joins-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e62-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01e62-124">See Also</span></span>  
 [<span data-ttu-id="01e62-125">使用聯結查詢 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="01e62-125">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
