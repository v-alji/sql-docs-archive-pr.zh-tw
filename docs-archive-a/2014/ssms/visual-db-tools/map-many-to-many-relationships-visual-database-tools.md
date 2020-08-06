---
title: 對應多對多關聯性 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- relationships [SQL Server], many-to-many
- junction tables [SQL Server]
- many-to-many relationships [SQL Server]
- mapping many-to-many relationships [SQL Server]
- database diagrams [SQL Server], relationships
ms.assetid: 2977cf92-98b5-48b2-b0fd-8fbc7040f2b4
author: stevestein
ms.author: sstein
ms.openlocfilehash: cbcbdbdf8d8371baa2a817e43b831535723be7ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606002"
---
# <a name="map-many-to-many-relationships-visual-database-tools"></a><span data-ttu-id="ec332-102">對應多對多關聯性 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ec332-102">Map Many-to-Many Relationships (Visual Database Tools)</span></span>
  <span data-ttu-id="ec332-103">多對多關聯性可讓您將一個資料表中的每一個資料列，關聯到另一個資料表的多個資料列，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="ec332-103">Many-to-many relationships let you relate each row in one table to many rows in another table, and vice versa.</span></span> <span data-ttu-id="ec332-104">例如，您可以建立 `authors` 資料表和 `titles` 資料表之間的多對多關聯性，以將每一個作者和他/她的書搭配，並將每一本書和所有的作者搭配。</span><span class="sxs-lookup"><span data-stu-id="ec332-104">For example, you could create a many-to-many relationship between the `authors` table and the `titles` table to match each author to all of his or her books and to match each book to all of its authors.</span></span> <span data-ttu-id="ec332-105">在任一資料表建立一對多關聯性，可能會錯指每一本書只能有一位作者，或每一位作者只能寫一本書。</span><span class="sxs-lookup"><span data-stu-id="ec332-105">Creating a one-to-many relationship from either table would incorrectly indicate that every book can have only one author, or that every author can write only one book.</span></span>  
  
 <span data-ttu-id="ec332-106">資料表之間的多對多關聯性，會藉由聯合資料表在資料庫中進行調整。</span><span class="sxs-lookup"><span data-stu-id="ec332-106">Many-to-many relationships between tables are accommodated in databases by means of junction tables.</span></span> <span data-ttu-id="ec332-107">聯合資料表包含您要關聯的兩個資料表的主索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="ec332-107">A junction table contains the primary key columns of the two tables you want to relate.</span></span> <span data-ttu-id="ec332-108">您可以建立兩個資料表的主索引鍵資料行，與聯合資料表中相符的資料行的關聯性。</span><span class="sxs-lookup"><span data-stu-id="ec332-108">You then create a relationship from the primary key columns of each of those two tables to the matching columns in the junction table.</span></span> <span data-ttu-id="ec332-109">在 pubs 資料庫中， `titleauthor` 資料表為聯合資料表。</span><span class="sxs-lookup"><span data-stu-id="ec332-109">In the pubs database, the `titleauthor` table is a junction table.</span></span>  
  
### <a name="to-create-a-many-to-many-relationship-between-tables"></a><span data-ttu-id="ec332-110">若要建立資料表間的多對多關聯性</span><span class="sxs-lookup"><span data-stu-id="ec332-110">To create a many-to-many relationship between tables</span></span>  
  
1.  <span data-ttu-id="ec332-111">在資料庫圖表中，加入您要在其間建立多對多關聯性的資料表。</span><span class="sxs-lookup"><span data-stu-id="ec332-111">In your database diagram, add the tables that you want to create a many-to-many relationship between.</span></span>  
  
2.  <span data-ttu-id="ec332-112">在圖表上按一下滑鼠右鍵，並從快速鍵功能表選擇 [新增資料表]  ，建立第三個資料表。</span><span class="sxs-lookup"><span data-stu-id="ec332-112">Create a third table by right-clicking the diagram and choosing **New Table** from the shortcut menu.</span></span> <span data-ttu-id="ec332-113">這會成為聯合資料表。</span><span class="sxs-lookup"><span data-stu-id="ec332-113">This will become the junction table.</span></span>  
  
3.  <span data-ttu-id="ec332-114">在 [選擇名稱]  對話方塊中，變更系統指派的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="ec332-114">In the **Choose Name** dialog box, change the system-assigned table name.</span></span> <span data-ttu-id="ec332-115">例如，`titles` 資料表和 `authors` 資料表之間的聯合資料表，現在的名稱為 `titleauthors`。</span><span class="sxs-lookup"><span data-stu-id="ec332-115">For example, the junction table between the `titles` table and the `authors` table is now named `titleauthors`.</span></span>  
  
4.  <span data-ttu-id="ec332-116">將兩個資料表的主索引鍵資料行都複製到聯合資料表。</span><span class="sxs-lookup"><span data-stu-id="ec332-116">Copy the primary key columns from each of the other two tables to the junction table.</span></span> <span data-ttu-id="ec332-117">您可以將其他資料行加入到此資料表，也可以加入到其他資料表。</span><span class="sxs-lookup"><span data-stu-id="ec332-117">You can add other columns to this table, just as you can to any other table.</span></span>  
  
5.  <span data-ttu-id="ec332-118">在聯合資料表中，將主索引鍵設定為包含來自其他兩個資料表的所有主索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="ec332-118">In the junction table, set the primary key to include all the primary key columns from the other two tables.</span></span> <span data-ttu-id="ec332-119">如需詳細資訊，請參閱[建立主鍵](../../relational-databases/tables/create-primary-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="ec332-119">For details, see [Create Primary Keys](../../relational-databases/tables/create-primary-keys.md).</span></span>  
  
6.  <span data-ttu-id="ec332-120">定義兩個主資料表和聯合資料表之間的一對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="ec332-120">Define a one-to-many relationship between each of the two primary tables and the junction table.</span></span> <span data-ttu-id="ec332-121">聯合資料表應該位於所建立的兩個關聯性「多」的一方。</span><span class="sxs-lookup"><span data-stu-id="ec332-121">The junction table should be at the "many" side of both of the relationships you create.</span></span> <span data-ttu-id="ec332-122">如需詳細資訊，請參閱[建立外鍵關聯](../../relational-databases/tables/create-foreign-key-relationships.md)性。</span><span class="sxs-lookup"><span data-stu-id="ec332-122">For details, see [Create Foreign Key Relationships](../../relational-databases/tables/create-foreign-key-relationships.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ec332-123">在資料庫圖表中建立聯合資料表，並不會將關聯資料表的資料插入至聯合資料表。</span><span class="sxs-lookup"><span data-stu-id="ec332-123">The creation of a junction table in a database diagram does not insert data from the related tables into the junction table.</span></span> <span data-ttu-id="ec332-124">如需將資料插入資料表的詳細資訊，請參閱[建立插入結果查詢 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="ec332-124">For information about inserting data into a table, see [Create Insert Results Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec332-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec332-125">See Also</span></span>  
 [<span data-ttu-id="ec332-126">使用資料庫圖表 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="ec332-126">Work with Database Diagrams &#40;Visual Database Tools&#41;</span></span>](work-with-database-diagrams-visual-database-tools.md)  
  
  
