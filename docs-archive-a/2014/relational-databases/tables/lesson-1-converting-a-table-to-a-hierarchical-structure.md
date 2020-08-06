---
title: 第 1 課：將資料表轉換為階層式結構 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 196a546093786f9be4b88536763b3150ae750f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708154"
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a><span data-ttu-id="f4063-102">第 1 課：將資料表轉換為階層式結構</span><span class="sxs-lookup"><span data-stu-id="f4063-102">Lesson 1: Converting a Table to a Hierarchical Structure</span></span>
  <span data-ttu-id="f4063-103">具有使用自我聯結表達階層式關聯性之資料表的客戶可以使用本課程當做指導方針，將其資料表轉換為階層式結構。</span><span class="sxs-lookup"><span data-stu-id="f4063-103">Customers who have tables using self joins to express hierarchical relationships can convert their tables to a hierarchical structure using this lesson as a guide.</span></span> <span data-ttu-id="f4063-104">從這種表示法移轉到另一種使用 `hierarchyid` 之表示法的步驟非常簡單。</span><span class="sxs-lookup"><span data-stu-id="f4063-104">It is relatively easy to migrate from this representation to one using `hierarchyid`.</span></span> <span data-ttu-id="f4063-105">移轉之後，使用者將會有一個精簡而且容易了解的階層式表示法，可以使用數種方式建立索引以便進行有效率的查詢。</span><span class="sxs-lookup"><span data-stu-id="f4063-105">After migration, users will have a compact and easy to understand hierarchical representation, which can be indexed in several ways for efficient queries.</span></span>  
  
 <span data-ttu-id="f4063-106">本課程會檢查現有的資料表、建立包含 `hierarchyid` 資料行的新資料列、使用來源資料表中的資料擴展資料表，然後示範三個索引策略。</span><span class="sxs-lookup"><span data-stu-id="f4063-106">This lesson, examines an existing table, creates a new table containing a `hierarchyid` column, populates the table with the data from the source table, and then demonstrates three indexing strategies.</span></span> <span data-ttu-id="f4063-107">這個課程包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="f4063-107">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="f4063-108">檢查 Employee 資料表的目前結構</span><span class="sxs-lookup"><span data-stu-id="f4063-108">Examining the Current Structure of the Employee Table</span></span>](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
-   [<span data-ttu-id="f4063-109">使用現有的階層式資料填入資料表</span><span class="sxs-lookup"><span data-stu-id="f4063-109">Populating a Table with Existing Hierarchical Data</span></span>](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
-   [<span data-ttu-id="f4063-110">最佳化 NewOrg 資料表</span><span class="sxs-lookup"><span data-stu-id="f4063-110">Optimizing the NewOrg Table</span></span>](lesson-1-3-optimizing-the-neworg-table.md)  
  
-   [<span data-ttu-id="f4063-111">摘要：將資料表轉換為階層式結構</span><span class="sxs-lookup"><span data-stu-id="f4063-111">Summary: Converting a Table to a Hierarchical Structure</span></span>](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## <a name="prerequisites"></a><span data-ttu-id="f4063-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f4063-112">Prerequisites</span></span>  
 <span data-ttu-id="f4063-113">本課程需要使用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="f4063-113">This lesson requires the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="f4063-114">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="f4063-114">Next Task in Lesson</span></span>  
 [<span data-ttu-id="f4063-115">檢查 Employee 資料表的目前結構</span><span class="sxs-lookup"><span data-stu-id="f4063-115">Examining the Current Structure of the Employee Table</span></span>](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="f4063-116">下一課</span><span class="sxs-lookup"><span data-stu-id="f4063-116">Next Lesson</span></span>  
 [<span data-ttu-id="f4063-117">第 2 課：在階層式資料表中建立與管理資料</span><span class="sxs-lookup"><span data-stu-id="f4063-117">Lesson 2: Creating and Managing Data in a Hierarchical Table</span></span>](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  
