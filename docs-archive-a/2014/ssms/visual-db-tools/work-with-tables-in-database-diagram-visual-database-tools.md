---
title: 使用資料庫圖表中的資料表 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- database diagrams [SQL Server], tables
- Table Designer, database diagrams
- tables [SQL Server], database diagrams
- database diagrams [SQL Server], Table Designer
ms.assetid: ee2c5d84-22bf-4597-ac70-a27ed8cc94f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: f648cd5fd08ed47c6670491ad5b7f3d75b7ead47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597492"
---
# <a name="work-with-tables-in-database-diagram-visual-database-tools"></a><span data-ttu-id="dfa46-102">使用資料庫圖表中的資料表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="dfa46-102">Work with Tables in Database Diagram (Visual Database Tools)</span></span>
  <span data-ttu-id="dfa46-103">您可以在 [資料表設計工具] 或 [資料庫圖表設計工具] 中修改和建立資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="dfa46-103">You can modify and create database tables in either Table Designer or Database Diagram Designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dfa46-104">如果資料表是要發佈以進行複寫，則必須使用 Transact-SQL 陳述式 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 SQL Server 管理物件 (SMO) 變更結構描述。</span><span class="sxs-lookup"><span data-stu-id="dfa46-104">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="dfa46-105">使用 [資料表設計工具] 或 [資料庫圖表設計工具] 變更結構描述時，會嘗試卸除並重新建立資料表。</span><span class="sxs-lookup"><span data-stu-id="dfa46-105">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="dfa46-106">您無法卸除已發行的物件，因此結構描述變更將會失敗。</span><span class="sxs-lookup"><span data-stu-id="dfa46-106">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dfa46-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="dfa46-107">In This Section</span></span>  
 [<span data-ttu-id="dfa46-108">將資料表新增至圖表 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="dfa46-108">Add Tables to Diagrams &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
 [<span data-ttu-id="dfa46-109">將相關的資料表新增至圖表 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="dfa46-109">Add Related Tables to Diagrams &#40;Visual Database Tools&#41;</span></span>](add-related-tables-to-diagrams-visual-database-tools.md)  
  
 [<span data-ttu-id="dfa46-110">儲存圖表上所選的資料表 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="dfa46-110">Save Selected Tables on a Diagram &#40;Visual Database Tools&#41;</span></span>](save-selected-tables-on-a-diagram-visual-database-tools.md)  
  
 [<span data-ttu-id="dfa46-111">將資料表從一個資料庫圖表複製至另一個資料庫圖表 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="dfa46-111">Copy Tables from One Database Diagrams to Another &#40;Visual Database Tools&#41;</span></span>](copy-tables-from-one-database-diagrams-to-another-visual-database-tools.md)  
  
 [<span data-ttu-id="dfa46-112">從資料庫圖表移除資料表 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="dfa46-112">Remove Tables from Database Diagrams &#40;Visual Database Tools&#41;</span></span>](remove-tables-from-database-diagrams-visual-database-tools.md)  
  
 [<span data-ttu-id="dfa46-113">對應多對多關聯性 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="dfa46-113">Map Many-to-Many Relationships &#40;Visual Database Tools&#41;</span></span>](map-many-to-many-relationships-visual-database-tools.md)  
  
 [<span data-ttu-id="dfa46-114">繪製自反關聯性 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="dfa46-114">Draw Reflexive Relationships &#40;Visual Database Tools&#41;</span></span>](draw-reflexive-relationships-visual-database-tools.md)  
  
## <a name="reference"></a><span data-ttu-id="dfa46-115">參考</span><span class="sxs-lookup"><span data-stu-id="dfa46-115">Reference</span></span>  
 [<span data-ttu-id="dfa46-116">新增資料表對話方塊 &#40;資料庫設計工具&#41; &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="dfa46-116">Add Table Dialog Box &#40;Database Designer&#41; &#40;Visual Database Tools&#41;</span></span>](add-table-dialog-box-database-designer-visual-database-tools.md)  
  
## <a name="related-sections"></a><span data-ttu-id="dfa46-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="dfa46-117">Related Sections</span></span>  
  
