---
title: 第4課：標記為日期資料表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c32cc336-b7d8-4122-9d62-4936344d2315
author: minewiskan
ms.author: owend
ms.openlocfilehash: c3ccc57d770d954e9523196d2393fa9dc2ada5b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597431"
---
# <a name="lesson-4-mark-as-date-table"></a><span data-ttu-id="ee22e-102">第 4 課：標記為日期資料表</span><span class="sxs-lookup"><span data-stu-id="ee22e-102">Lesson 4: Mark as Date Table</span></span>
  <span data-ttu-id="ee22e-103">在「第 2 課：加入資料」中，您已匯入了名為 DimDate 的維度資料表。</span><span class="sxs-lookup"><span data-stu-id="ee22e-103">In Lesson 2: Add Data, you imported a dimension table named DimDate.</span></span> <span data-ttu-id="ee22e-104">接著您在「第 3 課：重新命名資料行」中，將 DimDate 資料表重新命名為簡化的 Date。</span><span class="sxs-lookup"><span data-stu-id="ee22e-104">You then renamed the DimDate table, in Lesson 3: Rename Columns, to simply, Date.</span></span> <span data-ttu-id="ee22e-105">當模型中的此資料表已命名為 Date 時，也可以稱作「日期資料表」\*\*，並會在其中包含日期及時間資料。</span><span class="sxs-lookup"><span data-stu-id="ee22e-105">While in your model this table is now named Date, it can also be known as a *Date table*, in that it contains date and time data.</span></span>  
  
 <span data-ttu-id="ee22e-106">每當您在計算中使用時間智慧函數時，就像您稍後建立量值時一樣，必須指定日期資料表屬性，其中包含「日期資料表」**，以及該資料表中的唯一識別碼「日期資料行」**。</span><span class="sxs-lookup"><span data-stu-id="ee22e-106">Whenever you use Time Intelligence functions in calculations, as you will do when you create measures a little later, you must specify date table properties, which include a *Date table* and a unique identifier *Date column* in that table.</span></span> <span data-ttu-id="ee22e-107">接著您就可以在其他資料表與此 Date 資料表之間建立有效的關聯性；這對於使用 DAX 時間智慧函數進行計算為必要步驟。</span><span class="sxs-lookup"><span data-stu-id="ee22e-107">You can then create valid relationships between other tables and the Date table; necessary for calculations using DAX time intelligence functions.</span></span>  
  
 <span data-ttu-id="ee22e-108">在這一課，您將標記所匯入並重新命名的 Date 資料表為「日期資料表」**，而 Date 資料行 (包含在 Date 資料表中) 則會標記為「日期資料行」**(唯一識別碼)。</span><span class="sxs-lookup"><span data-stu-id="ee22e-108">In this lesson, you will mark the imported and renamed Date table as the *Date table* and the Date column (in the Date table) as the *Date column* (unique identifier).</span></span> <span data-ttu-id="ee22e-109">名稱日期的所有使用都可能會令人困惑，但您很快就會得到這種想法。</span><span class="sxs-lookup"><span data-stu-id="ee22e-109">All the use of the name Date can get kind of confusing, but you'll soon get the idea.</span></span>  
  
 <span data-ttu-id="ee22e-110">完成本課程的估計時間： **3 分鐘**</span><span class="sxs-lookup"><span data-stu-id="ee22e-110">Estimated time to complete this lesson: **3 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ee22e-111">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="ee22e-111">Prerequisites</span></span>  
 <span data-ttu-id="ee22e-112">本主題是表格式模型教學課程的一部分，請依序完成。</span><span class="sxs-lookup"><span data-stu-id="ee22e-112">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="ee22e-113">在執行本課中的工作之前，您應已完成上一課： [第 3 課：重新命名資料行](rename-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="ee22e-113">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 3: Rename Columns](rename-columns.md).</span></span>  
  
### <a name="to-set-mark-as-date-table"></a><span data-ttu-id="ee22e-114">設定標記為日期資料表</span><span class="sxs-lookup"><span data-stu-id="ee22e-114">To set Mark as Date Table</span></span>  
  
1.  <span data-ttu-id="ee22e-115">在模型設計師中，按一下 [Date]\*\*\*\* 資料表 (索引標籤)。</span><span class="sxs-lookup"><span data-stu-id="ee22e-115">In the model designer, click the **Date** table (tab).</span></span>  
  
2.  <span data-ttu-id="ee22e-116">依序按一下 [**資料表**] 功能表、[**日期**] 和 [**標記為日期資料表**]。</span><span class="sxs-lookup"><span data-stu-id="ee22e-116">Click the **Table** menu, then click **Date**, and then click **Mark as Date Table**.</span></span>  
  
3.  <span data-ttu-id="ee22e-117">在 [標記為日期資料表]\*\*\*\* 對話方塊中，在 [日期]\*\*\*\* 清單方塊中選取 [Date]\*\*\*\* 資料行當作唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="ee22e-117">In the **Mark as Date Table** dialog box, in the **Date** listbox, select the **Date** column as the unique identifier.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ee22e-118">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ee22e-118">Next Steps</span></span>  
 <span data-ttu-id="ee22e-119">若要繼續進行本教學課程，請前往下一課： [第 5 課：建立關聯性](lesson-4-create-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="ee22e-119">To continue this tutorial, go to the next lesson: [Lesson 5: Create Relationships](lesson-4-create-relationships.md).</span></span>  
  
  
