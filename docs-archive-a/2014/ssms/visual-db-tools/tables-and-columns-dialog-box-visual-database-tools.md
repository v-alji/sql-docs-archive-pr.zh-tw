---
title: 資料表和資料行對話方塊 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.tablesandcolumns
ms.assetid: 8cf27be1-e66d-4735-a428-9ab4b33af4f5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28e0c52b74413a3a5a4122412c6028b34e974b09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599298"
---
# <a name="tables-and-columns-dialog-box-visual-database-tools"></a><span data-ttu-id="8d13a-102">資料表和資料行對話方塊 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8d13a-102">Tables and Columns Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="8d13a-103">使用此對話方塊將一個資料表中的主索引鍵對應至另一個資料表中的外部索引鍵。</span><span class="sxs-lookup"><span data-stu-id="8d13a-103">Use this dialog box to map a primary key in one table to a foreign key in another.</span></span> <span data-ttu-id="8d13a-104">若要存取此對話方塊，請從 [資料表設計工具]  功能表按一下 [關聯性]  。</span><span class="sxs-lookup"><span data-stu-id="8d13a-104">To access this dialog box, from the **Table Designer** menu, click **Relationships**.</span></span> <span data-ttu-id="8d13a-105">在 [外部索引鍵關聯性]  對話方塊中，按一下 [資料表及資料行規格]  欄位，然後按一下屬性右邊的省略符號 ([...]  )。</span><span class="sxs-lookup"><span data-stu-id="8d13a-105">In the **Foreign Key Relationships** dialog box, click the **Tables and Columns Specification** field, and then click the ellipses **(...)** to the right of the property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8d13a-106">如果資料表是要發佈以進行複寫，則必須使用 Transact-SQL 陳述式 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 SQL Server 管理物件 (SMO) 變更結構描述。</span><span class="sxs-lookup"><span data-stu-id="8d13a-106">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="8d13a-107">使用 [資料表設計工具] 或 [資料庫圖表設計工具] 變更結構描述時，會嘗試卸除並重新建立資料表。</span><span class="sxs-lookup"><span data-stu-id="8d13a-107">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="8d13a-108">您無法卸除已發行的物件，因此結構描述變更將會失敗。</span><span class="sxs-lookup"><span data-stu-id="8d13a-108">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8d13a-109">選項。</span><span class="sxs-lookup"><span data-stu-id="8d13a-109">Options</span></span>  
 <span data-ttu-id="8d13a-110">**關聯性名稱**</span><span class="sxs-lookup"><span data-stu-id="8d13a-110">**Relationship name**</span></span>  
 <span data-ttu-id="8d13a-111">顯示關聯性的名稱。</span><span class="sxs-lookup"><span data-stu-id="8d13a-111">Shows the name of the relationship.</span></span>  
  
 <span data-ttu-id="8d13a-112">**主索引鍵資料表**</span><span class="sxs-lookup"><span data-stu-id="8d13a-112">**Primary Key Table**</span></span>  
 <span data-ttu-id="8d13a-113">列出資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="8d13a-113">Lists the tables in the database.</span></span> <span data-ttu-id="8d13a-114">選擇將位在關聯性主索引鍵端的資料表。</span><span class="sxs-lookup"><span data-stu-id="8d13a-114">Choose the table that will be on the primary-key side of the relationship.</span></span>  
  
 <span data-ttu-id="8d13a-115">**外部索引鍵資料表**</span><span class="sxs-lookup"><span data-stu-id="8d13a-115">**Foreign Key Table**</span></span>  
 <span data-ttu-id="8d13a-116">顯示位在關聯性外部索引鍵端的資料表。</span><span class="sxs-lookup"><span data-stu-id="8d13a-116">Shows the table on the foreign key side of the relationship.</span></span> <span data-ttu-id="8d13a-117">這是目前在 [資料表設計師] 中選取的資料表。</span><span class="sxs-lookup"><span data-stu-id="8d13a-117">This is the table currently selected in Table Designer.</span></span>  
  
 <span data-ttu-id="8d13a-118">**主索引鍵資料表底下方格**</span><span class="sxs-lookup"><span data-stu-id="8d13a-118">**Grid beneath Primary Key Table**</span></span>  
 <span data-ttu-id="8d13a-119">列出在 [主索引鍵資料表]  清單中所選取資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="8d13a-119">List the columns of the table selected in the **Primary Key Table** list.</span></span> <span data-ttu-id="8d13a-120">輸入提供該資料表之主索引鍵的資料行。</span><span class="sxs-lookup"><span data-stu-id="8d13a-120">Enter the columns contributing to that table's primary key.</span></span>  
  
 <span data-ttu-id="8d13a-121">**外部索引鍵資料表底下方格**</span><span class="sxs-lookup"><span data-stu-id="8d13a-121">**Grid beneath Foreign Key Table**</span></span>  
 <span data-ttu-id="8d13a-122">列出在 [外部索引鍵資料表]  清單中所選取資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="8d13a-122">List the columns of the table selected in the **Foreign Key Table** list.</span></span> <span data-ttu-id="8d13a-123">輸入外部索引鍵資料表的外部索引鍵資料行，該資料行對應至主索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="8d13a-123">Enter the foreign-key column of the foreign-key table that corresponds to the primary key column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8d13a-124">為外部索引鍵選擇的資料行，必須與對應到的主索引鍵資料行具有相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="8d13a-124">The columns you choose for the foreign key must have the same data type of the primary columns they correspond to.</span></span> <span data-ttu-id="8d13a-125">每個索引鍵中的資列行數目必須相等。</span><span class="sxs-lookup"><span data-stu-id="8d13a-125">There must be an equal number of columns in each of the keys.</span></span> <span data-ttu-id="8d13a-126">例如，如果位在關聯性主索引鍵端的資料表之主索引鍵是由兩個資料行所組成，這兩個資料行的每一個都必須與關聯性外部索引鍵端資料表中的一個資料行相符。</span><span class="sxs-lookup"><span data-stu-id="8d13a-126">For example, if the primary key of the table on the primary side of the relationship is made up of two columns, you will need to match each of those columns with a column in the table for the foreign key side of the relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d13a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d13a-127">See Also</span></span>  
 [<span data-ttu-id="8d13a-128">建立外部索引鍵關聯性</span><span class="sxs-lookup"><span data-stu-id="8d13a-128">Create Foreign Key Relationships</span></span>](../../relational-databases/tables/create-foreign-key-relationships.md)  
  
  
