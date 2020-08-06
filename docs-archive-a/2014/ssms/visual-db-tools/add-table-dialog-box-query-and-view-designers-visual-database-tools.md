---
title: '[加入資料表] 對話方塊 (查詢和視圖設計工具)  (Visual Database Tools) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.query.addtable
- vdtsql.chm:65565
ms.assetid: fce7adcc-4cf5-4a52-9203-11c13d1ecf08
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8d7bf30cbdd37927735c36f184208a1ded957763
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593756"
---
# <a name="add-table-dialog-box-query-and-view-designers-visual-database-tools"></a><span data-ttu-id="ab5dc-102">加入資料表對話方塊 (查詢和檢視表設計工具) (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ab5dc-102">Add Table Dialog Box (Query and View Designers) (Visual Database Tools)</span></span>
  <span data-ttu-id="ab5dc-103">這個對話方塊可讓您將資料表、檢視、使用者自訂函數或同義字加入查詢或檢視中。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-103">This dialog box lets you add tables, views, user-defined functions, or synonyms to a query or view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab5dc-104">如果資料表是要發佈以進行複寫，則必須使用 Transact-SQL 陳述式 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 SQL Server 管理物件 (SMO) 變更結構描述。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-104">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="ab5dc-105">使用 [資料表設計工具] 或 [資料庫圖表設計工具] 變更結構描述時，會嘗試卸除並重新建立資料表。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-105">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="ab5dc-106">您無法卸除已發行的物件，因此結構描述變更將會失敗。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-106">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ab5dc-107">選項。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-107">Options</span></span>  
 <span data-ttu-id="ab5dc-108">**資料表**</span><span class="sxs-lookup"><span data-stu-id="ab5dc-108">**Tables**</span></span>  
 <span data-ttu-id="ab5dc-109">列出可以新增至 [圖表]  窗格的資料表。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-109">Lists the tables you can add to the **Diagram** pane.</span></span> <span data-ttu-id="ab5dc-110">若要新增資料表，請選取資料表，再按 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-110">To add a table, select it and click **Add**.</span></span> <span data-ttu-id="ab5dc-111">若要一次新增數個資料表，請選取資料表，再按 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-111">To add several tables at once, select them and click **Add**.</span></span>  
  
 <span data-ttu-id="ab5dc-112">**檢視**</span><span class="sxs-lookup"><span data-stu-id="ab5dc-112">**Views**</span></span>  
 <span data-ttu-id="ab5dc-113">列出可以新增至 [圖表]  窗格的檢視表。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-113">Lists the views you can add to the **Diagram** pane.</span></span> <span data-ttu-id="ab5dc-114">若要新增檢視表，請選取檢視表，再按 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-114">To add a view, select it and click **Add**.</span></span> <span data-ttu-id="ab5dc-115">若要一次新增數個檢視表，請選取檢視表，再按 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-115">To add several views at once, select them and click **Add**.</span></span>  
  
 <span data-ttu-id="ab5dc-116">**函數**</span><span class="sxs-lookup"><span data-stu-id="ab5dc-116">**Functions**</span></span>  
 <span data-ttu-id="ab5dc-117">列出可新增至 [圖表]  窗格的使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-117">Lists the user-defined functions you can add to the **Diagram** pane.</span></span> <span data-ttu-id="ab5dc-118">若要新增函數，請選取函數，再按 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-118">To add a function, select it and click **Add**.</span></span> <span data-ttu-id="ab5dc-119">若要一次新增數個函數，請選取函數，再按 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-119">To add several functions at once, select them and click **Add**.</span></span>  
  
 <span data-ttu-id="ab5dc-120">**同義字**</span><span class="sxs-lookup"><span data-stu-id="ab5dc-120">**Synonyms**</span></span>  
 <span data-ttu-id="ab5dc-121">列出可新增至 [圖表]  窗格的同義資料表。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-121">Lists the synonyms you can add to the **Diagram** pane.</span></span> <span data-ttu-id="ab5dc-122">若要新增同義資料表，請選取同義資料表，再按 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-122">To add a synonym, select it and click **Add**.</span></span> <span data-ttu-id="ab5dc-123">若要一次新增數個同義資料表，請選取同義資料表，再按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-123">To add several synonyms at once, select them and click **Add**.</span></span>  
  
 <span data-ttu-id="ab5dc-124">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="ab5dc-124">**Refresh**</span></span>  
 <span data-ttu-id="ab5dc-125">更新清單以包含自上次擷取清單以來對資料庫所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-125">Update the list to include any changes made to the database since the list was last retrieved.</span></span>  
  
 <span data-ttu-id="ab5dc-126">**加入**</span><span class="sxs-lookup"><span data-stu-id="ab5dc-126">**Add**</span></span>  
 <span data-ttu-id="ab5dc-127">加入選取的一或多個項目。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-127">Add the selected item or items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab5dc-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab5dc-128">See Also</span></span>  
 [<span data-ttu-id="ab5dc-129">設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="ab5dc-129">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
