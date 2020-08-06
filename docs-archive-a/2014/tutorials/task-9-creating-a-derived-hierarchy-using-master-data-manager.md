---
title: 工作9：使用主資料管理員建立衍生階層 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3bd2ec05-933f-4947-b1fe-c9226961eb7d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5c85750e4556722c6e6a5edbccb4a3c82c119a74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710038"
---
# <a name="task-9-creating-a-derived-hierarchy-using-master-data-manager"></a><span data-ttu-id="73b1a-102">工作 9：使用主資料管理員建立衍生階層</span><span class="sxs-lookup"><span data-stu-id="73b1a-102">Task 9: Creating a Derived Hierarchy using Master Data Manager</span></span>
  <span data-ttu-id="73b1a-103">在這項工作中，您會使用主資料管理員建立衍生階層。</span><span class="sxs-lookup"><span data-stu-id="73b1a-103">In this task, you create a derived hierarchy by using Master Data Manager.</span></span> <span data-ttu-id="73b1a-104">這個衍生階層衍生自**供應商**和**州**實體之間的網域屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="73b1a-104">This derived hierarchy is derived from the domain-based attribute relationships between the **Supplier** and **State** entities.</span></span>  
  
1.  <span data-ttu-id="73b1a-105">按一下頁面頂端的 [ **SQL Server 2012 Master Data Services** ]，切換至**主資料管理員**的主頁面。</span><span class="sxs-lookup"><span data-stu-id="73b1a-105">Switch to the main page of **Master Data Manager** by clicking **SQL Server 2012 Master Data Services** at the top of the page.</span></span>  
  
2.  <span data-ttu-id="73b1a-106">按一下 [**管理**工作] 區段中的 [**系統管理**]。</span><span class="sxs-lookup"><span data-stu-id="73b1a-106">Click **System Administration** in the **Administrative Tasks** section.</span></span>  
  
3.  <span data-ttu-id="73b1a-107">將滑鼠停留在功能表列上的 [**管理**] 上，然後按一下 [**衍生**階層]。</span><span class="sxs-lookup"><span data-stu-id="73b1a-107">Hover the mouse over **Manage** on the menu bar, and click **Derived Hierarchies**.</span></span>  
  
     <span data-ttu-id="73b1a-108">![管理功能表 - 已選取 [衍生階層]](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "管理功能表 - 已選取 [衍生階層]")</span><span class="sxs-lookup"><span data-stu-id="73b1a-108">![Manage Menu - Derived Hierarchies Selected](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "Manage Menu - Derived Hierarchies Selected")</span></span>  
  
4.  <span data-ttu-id="73b1a-109">按一下工具列上的 [\*\*加入衍生階層] (+) \*\* ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="73b1a-109">Click **Add Derived Hierarchy (+)** button on the toolbar.</span></span>  
  
     <span data-ttu-id="73b1a-110">![[加入衍生階層] 按鈕](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "[加入衍生階層] 按鈕")</span><span class="sxs-lookup"><span data-stu-id="73b1a-110">![Add Derived Hierarchy Button](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "Add Derived Hierarchy Button")</span></span>  
  
5.  <span data-ttu-id="73b1a-111">針對 [衍生階層**名稱**] 輸入**SuppliersInState** 。</span><span class="sxs-lookup"><span data-stu-id="73b1a-111">Type **SuppliersInState** for the **Derived hierarchy name**.</span></span>  
  
6.  <span data-ttu-id="73b1a-112">按一下工具列上的 [**儲存**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="73b1a-112">Click **Save** button on the toolbar.</span></span>  
  
     <span data-ttu-id="73b1a-113">![[儲存衍生階層] 按鈕](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "[儲存衍生階層] 按鈕")</span><span class="sxs-lookup"><span data-stu-id="73b1a-113">![Save Derived Hierarchy Button](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "Save Derived Hierarchy Button")</span></span>  
  
7.  <span data-ttu-id="73b1a-114">從可用的**層級**拖曳**供應商**： SuppliersInState 至**目前的層級： SuppliersInState**。</span><span class="sxs-lookup"><span data-stu-id="73b1a-114">Drag **Supplier** from **Available Levels: SuppliersInState** to **Current Levels: SuppliersInState**.</span></span>  
  
     <span data-ttu-id="73b1a-115">![目前層級可用的實體和階層](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "目前層級可用的實體和階層")</span><span class="sxs-lookup"><span data-stu-id="73b1a-115">![Avialble Entities and Hierarchies to Current Level](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "Avialble Entities and Hierarchies to Current Level")</span></span>  
  
8.  <span data-ttu-id="73b1a-116">從**State**可用的**層級拖曳狀態： SuppliersInState**到**目前的層級： SuppliersInState**。</span><span class="sxs-lookup"><span data-stu-id="73b1a-116">Drag **State** from **Available Levels: SuppliersInState** to **Current Levels: SuppliersInState**.</span></span> <span data-ttu-id="73b1a-117">畫面應具有**目前的層級**，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="73b1a-117">The screen should have **Current Levels** as shown in the following picture.</span></span>  
  
     <span data-ttu-id="73b1a-118">![衍生階層的目前層級和預覽](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "衍生階層的目前層級和預覽")</span><span class="sxs-lookup"><span data-stu-id="73b1a-118">![Current Levels and Preview of Derived Hierarchy](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "Current Levels and Preview of Derived Hierarchy")</span></span>  
  
9. <span data-ttu-id="73b1a-119">在 [**預覽**] 視窗中，展開 [ **NY {紐約}** ]，您應該會看到該狀態的一個供應商，如上圖所示。</span><span class="sxs-lookup"><span data-stu-id="73b1a-119">In the **Preview** window, expand **NY { New York}** and you should see one supplier in that state as shown in the preceding image.</span></span>  
  
10. <span data-ttu-id="73b1a-120">按一下頁面頂端的 [ **SQL Server 2012 Master Data Services** ]，切換至**主資料管理員**的主頁面。</span><span class="sxs-lookup"><span data-stu-id="73b1a-120">Switch to the main page of **Master Data Manager** by clicking **SQL Server 2012 Master Data Services** at the top of the page.</span></span>  
  
11. <span data-ttu-id="73b1a-121">按一下 **[總管]**。</span><span class="sxs-lookup"><span data-stu-id="73b1a-121">Click **Explorer**.</span></span>  
  
12. <span data-ttu-id="73b1a-122">將滑鼠**停留在階層上，** 然後按一下 [**衍生： SuppliersInState**]。</span><span class="sxs-lookup"><span data-stu-id="73b1a-122">Hover the mouse over **Hierarchies** and click **Derived:SuppliersInState**.</span></span>  
  
     <span data-ttu-id="73b1a-123">![階層 - [衍生:SuppliersInState] 功能表](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "階層 - [衍生:SuppliersInState] 功能表")</span><span class="sxs-lookup"><span data-stu-id="73b1a-123">![Hierarchies - Derived:SuppliersInState Menu](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "Hierarchies - Derived:SuppliersInState Menu")</span></span>  
  
13. <span data-ttu-id="73b1a-124">按一下**樹狀檢視**中的任何**狀態**節點，您應該會在右窗格中看到該狀態的供應商。</span><span class="sxs-lookup"><span data-stu-id="73b1a-124">Click on any **state** node in the **tree view** and you should see the suppliers in that state in the right pane.</span></span>  
  
     <span data-ttu-id="73b1a-125">![檔案總管中的衍生階層](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "檔案總管中的衍生階層")</span><span class="sxs-lookup"><span data-stu-id="73b1a-125">![Derived Hierarchy in Explorer](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "Derived Hierarchy in Explorer")</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="73b1a-126">後續步驟</span><span class="sxs-lookup"><span data-stu-id="73b1a-126">Next Step</span></span>  
 [<span data-ttu-id="73b1a-127">第 5 課：使用 SSIS 將清理和比對自動化</span><span class="sxs-lookup"><span data-stu-id="73b1a-127">Lesson 5: Automating the Cleansing and Matching using SSIS</span></span>](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)  
  
  
