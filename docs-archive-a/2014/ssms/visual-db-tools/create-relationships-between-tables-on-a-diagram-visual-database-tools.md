---
title: 在圖表上建立資料表之間的關聯性 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- diagrams [SQL Server], designing
ms.assetid: 28e9630c-dff4-46cc-bb0e-fe77998b6ac2
author: stevestein
ms.author: sstein
ms.openlocfilehash: d7d627a37f84dcb66b2129bb9c7dbc5890ccd46c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708038"
---
# <a name="create-relationships-between-tables-on-a-diagram-visual-database-tools"></a><span data-ttu-id="77f3f-102">在圖表上建立資料表之間的關聯性 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="77f3f-102">Create Relationships Between Tables on a Diagram (Visual Database Tools)</span></span>
  <span data-ttu-id="77f3f-103">在圖表設計工具中，您可以在資料表之間拖曳資料行，以建立不同資料表資料行之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="77f3f-103">You can create relationships between columns in different tables in the Diagram Designer by dragging columns between tables.</span></span>  
  
### <a name="to-create-a-relationship-graphically"></a><span data-ttu-id="77f3f-104">若要以圖形建立關聯性</span><span class="sxs-lookup"><span data-stu-id="77f3f-104">To create a relationship graphically</span></span>  
  
1.  <span data-ttu-id="77f3f-105">在資料庫設計工具中，針對一個或多個要關聯到其他資料表資料行的資料庫資料行，按一下資料列選取器。</span><span class="sxs-lookup"><span data-stu-id="77f3f-105">In Database Designer, click the row selector for one or more database columns that you want to relate to a column in another table.</span></span>  
  
2.  <span data-ttu-id="77f3f-106">將選取的資料行拖曳到關聯的資料表。</span><span class="sxs-lookup"><span data-stu-id="77f3f-106">Drag the selected column(s) to the related table.</span></span>  
  
3.  <span data-ttu-id="77f3f-107">會出現兩個對話方塊：[外部索引鍵關聯性]  和 [資料表與資料行]  ，而後者會顯示在前景中。</span><span class="sxs-lookup"><span data-stu-id="77f3f-107">Two dialog boxes appear: **Foreign Key Relationship** and **Tables and Columns**, with the latter appearing in the foreground.</span></span>  
  
4.  <span data-ttu-id="77f3f-108">**關聯性名稱**具有系統提供的名稱，格式為 FK_*localtable*_*foreigntable*。</span><span class="sxs-lookup"><span data-stu-id="77f3f-108">**Relationship name** has a system-provided name in the format FK_*localtable*_*foreigntable*.</span></span> <span data-ttu-id="77f3f-109">您可以變更這個值。</span><span class="sxs-lookup"><span data-stu-id="77f3f-109">You may change this value.</span></span>  
  
5.  <span data-ttu-id="77f3f-110">確認 [主索引鍵資料表]  是否指定正確的資料表。</span><span class="sxs-lookup"><span data-stu-id="77f3f-110">Verify that **Primary key table** specifies the correct table.</span></span>  
  
6.  <span data-ttu-id="77f3f-111">方格會列出本地資料行及其對應的外部資料行。</span><span class="sxs-lookup"><span data-stu-id="77f3f-111">The grid lists the local columns and their matching foreign columns.</span></span> <span data-ttu-id="77f3f-112">您可以加入或移除資料表資料行，或變更對應。</span><span class="sxs-lookup"><span data-stu-id="77f3f-112">You can add or remove table columns or change mappings.</span></span>  
  
7.  <span data-ttu-id="77f3f-113">選擇 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="77f3f-113">Choose **OK**.</span></span>  
  
     <span data-ttu-id="77f3f-114">[外部索引鍵關聯性]  對話方塊便會出現。</span><span class="sxs-lookup"><span data-stu-id="77f3f-114">The **Foreign Key Relationship** dialog box appears.</span></span> <span data-ttu-id="77f3f-115">[選取的關聯性]  會顯示您所建立的關聯性。</span><span class="sxs-lookup"><span data-stu-id="77f3f-115">**Selected Relationship** shows the relationship you have created.</span></span>  
  
8.  <span data-ttu-id="77f3f-116">變更方格中關聯性的屬性。</span><span class="sxs-lookup"><span data-stu-id="77f3f-116">Change properties for the relationship in the grid.</span></span>  
  
9. <span data-ttu-id="77f3f-117">選擇 **[確定]** 建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="77f3f-117">Choose **OK** to create the relationship.</span></span>  
  
     <span data-ttu-id="77f3f-118">資料庫設計工具會顯示您選擇的資料行之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="77f3f-118">Database Designer shows a relationship between the columns you chose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f3f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77f3f-119">See Also</span></span>  
 <span data-ttu-id="77f3f-120">[[資料表和資料行] 對話方塊 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="77f3f-120">[Tables and Columns Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="77f3f-121">[Unique 條件約束和 Check 條件約束](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="77f3f-121">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 [<span data-ttu-id="77f3f-122">使用資料庫圖表中的資料表 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="77f3f-122">Work with Tables in Database Diagram &#40;Visual Database Tools&#41;</span></span>](work-with-tables-in-database-diagram-visual-database-tools.md)  
  
  
