---
title: 加入資料表對話方塊 (資料庫設計工具) (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65555
- vdt.dlgbox.schema.addtable
ms.assetid: 3c0b1b30-795c-4240-91d6-890b8348014a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ae9d3763ef66c0a7580cc516169c2f273f36528
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593757"
---
# <a name="add-table-dialog-box-database-designer-visual-database-tools"></a><span data-ttu-id="af5bf-102">加入資料表對話方塊 (資料庫設計工具) (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="af5bf-102">Add Table Dialog Box (Database Designer) (Visual Database Tools)</span></span>
  <span data-ttu-id="af5bf-103">讓您在 [資料庫設計工具] 中加入資料表。</span><span class="sxs-lookup"><span data-stu-id="af5bf-103">Lets you add tables in Database Designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af5bf-104">如果資料表是要發佈以進行複寫，則必須使用 Transact-SQL 陳述式 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 SQL Server 管理物件 (SMO) 變更結構描述。</span><span class="sxs-lookup"><span data-stu-id="af5bf-104">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="af5bf-105">使用 [資料表設計工具] 或 [資料庫圖表設計工具] 變更結構描述時，會嘗試卸除並重新建立資料表。</span><span class="sxs-lookup"><span data-stu-id="af5bf-105">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="af5bf-106">您無法卸除已發行的物件，因此結構描述變更將會失敗。</span><span class="sxs-lookup"><span data-stu-id="af5bf-106">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="af5bf-107">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="af5bf-107">UI element list</span></span>  
 <span data-ttu-id="af5bf-108">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="af5bf-108">**Refresh**</span></span>  
 <span data-ttu-id="af5bf-109">重新整理資料表清單，以符合資料庫目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="af5bf-109">Refreshed the list of tables to match the current state of the database.</span></span>  
  
 <span data-ttu-id="af5bf-110">**加入**</span><span class="sxs-lookup"><span data-stu-id="af5bf-110">**Add**</span></span>  
 <span data-ttu-id="af5bf-111">加入選取的資料表或多個資料表。</span><span class="sxs-lookup"><span data-stu-id="af5bf-111">Adds the selected table or tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af5bf-112">若要將好幾個資料表加入至圖表，可以在按一下 [新增]  之前選取所有資料表。</span><span class="sxs-lookup"><span data-stu-id="af5bf-112">If you want to add several tables to the diagram, you can select them all before clicking **Add**.</span></span> <span data-ttu-id="af5bf-113">或是，按兩下每一個要加入的資料表，完成時按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="af5bf-113">Alternatively, you can double-click each table you want to add, then click **Close** when you are finished.</span></span>  
  
 <span data-ttu-id="af5bf-114">**關閉**</span><span class="sxs-lookup"><span data-stu-id="af5bf-114">**Close**</span></span>  
 <span data-ttu-id="af5bf-115">關閉對話方塊，而不再加入其他資料表。</span><span class="sxs-lookup"><span data-stu-id="af5bf-115">Closes the dialog box without adding further tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af5bf-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af5bf-116">See Also</span></span>  
 [<span data-ttu-id="af5bf-117">將資料表新增至圖表 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="af5bf-117">Add Tables to Diagrams &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
