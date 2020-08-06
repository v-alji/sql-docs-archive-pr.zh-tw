---
title: 教學課程：使用 hierarchyid 資料類型 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- tutorials [hierarchyid]
- hierarchyid [Database Engine], tutorial
ms.assetid: 5a7f7cfd-7faf-439f-8085-8fd6bf7db355
author: stevestein
ms.author: sstein
ms.openlocfilehash: a735b4c2b51e1c680c8129647733ce1efd9f9984
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593913"
---
# <a name="tutorial-using-the-hierarchyid-data-type"></a><span data-ttu-id="43b5c-102">教學課程：使用 hierarchyid 資料類型</span><span class="sxs-lookup"><span data-stu-id="43b5c-102">Tutorial: Using the hierarchyid Data Type</span></span>
  <span data-ttu-id="43b5c-103">本教學課程的主要對象是對 [!INCLUDE[tsql](../../includes/tsql-md.md)] 有經驗，但對 `hierarchyid` 資料類型是新手的使用者。</span><span class="sxs-lookup"><span data-stu-id="43b5c-103">This tutorial is intended for users who are experienced with [!INCLUDE[tsql](../../includes/tsql-md.md)], but are new to the `hierarchyid` data type.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="43b5c-104">學習內容</span><span class="sxs-lookup"><span data-stu-id="43b5c-104">What You Will Learn</span></span>  
 <span data-ttu-id="43b5c-105">這個教學課程分成兩個課程：</span><span class="sxs-lookup"><span data-stu-id="43b5c-105">This tutorial is divided into two lessons:</span></span>  
  
 [<span data-ttu-id="43b5c-106">第 1 課：將資料表轉換為階層式結構</span><span class="sxs-lookup"><span data-stu-id="43b5c-106">Lesson 1: Converting a Table to a Hierarchical Structure</span></span>](lesson-1-converting-a-table-to-a-hierarchical-structure.md)  
 <span data-ttu-id="43b5c-107">在本課程中，您會使用結構為父子式階層的現有員工資料表，並使用 `hierarchyid` 資料類型，將資料移到代表階層的新資料表中。</span><span class="sxs-lookup"><span data-stu-id="43b5c-107">In this lesson, you take an existing employee table that is structured as a parent/child hierarchy and move the data into a new table that represents the hierarchy by using the `hierarchyid` data type.</span></span> <span data-ttu-id="43b5c-108">本課程需要使用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="43b5c-108">This lesson requires the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
 [<span data-ttu-id="43b5c-109">第 2 課：在階層式資料表中建立與管理資料</span><span class="sxs-lookup"><span data-stu-id="43b5c-109">Lesson 2: Creating and Managing Data in a Hierarchical Table</span></span>](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
 <span data-ttu-id="43b5c-110">在本課程中，您可以使用 `hierarchyid` 資料類型建立資料表來代表階層結構。</span><span class="sxs-lookup"><span data-stu-id="43b5c-110">In this lesson, you create a table by using the `hierarchyid` data type to represent the hierarchy structure.</span></span> <span data-ttu-id="43b5c-111">然後，您可以使用階層式方法操作資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="43b5c-111">Then, you manipulate the data in the table by using the hierarchical methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43b5c-112">需求</span><span class="sxs-lookup"><span data-stu-id="43b5c-112">Requirements</span></span>  
 <span data-ttu-id="43b5c-113">另外，系統必須有安裝下列程式：</span><span class="sxs-lookup"><span data-stu-id="43b5c-113">Your system must have the following installed:</span></span>  
  
-   <span data-ttu-id="43b5c-114">任何 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 版本或更新版本。</span><span class="sxs-lookup"><span data-stu-id="43b5c-114">Any edition of [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later.</span></span>  
  
-   <span data-ttu-id="43b5c-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express。</span><span class="sxs-lookup"><span data-stu-id="43b5c-115">Either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express.</span></span>  
  
-   <span data-ttu-id="43b5c-116">Internet Explorer 6 或更新的版本。</span><span class="sxs-lookup"><span data-stu-id="43b5c-116">Internet Explorer 6 or a later version.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b5c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43b5c-117">See Also</span></span>  
 <span data-ttu-id="43b5c-118">[教學課程：使用資料庫引擎消費者入門](../tutorial-getting-started-with-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="43b5c-118">[Tutorial: Getting Started with the Database Engine](../tutorial-getting-started-with-the-database-engine.md) </span></span>  
 <span data-ttu-id="43b5c-119">[教學課程：撰寫 Transact-sql 語句](../../t-sql/tutorial-writing-transact-sql-statements.md) </span><span class="sxs-lookup"><span data-stu-id="43b5c-119">[Tutorial: Writing Transact-SQL Statements](../../t-sql/tutorial-writing-transact-sql-statements.md) </span></span>  
 <span data-ttu-id="43b5c-120">[hierarchyid 資料類型方法參考](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) </span><span class="sxs-lookup"><span data-stu-id="43b5c-120">[hierarchyid Data Type Method Reference](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) </span></span>  
 <span data-ttu-id="43b5c-121">[階層式資料 &#40;SQL Server&#41;](../hierarchical-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="43b5c-121">[Hierarchical Data &#40;SQL Server&#41;](../hierarchical-data-sql-server.md) </span></span>  
 [<span data-ttu-id="43b5c-122">hierarchyid &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="43b5c-122">hierarchyid &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/hierarchyid-data-type-method-reference)  
  
  
