---
title: 第8課：定義動作 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 15459396-83c9-48a0-b10a-99ae38768c79
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4d4daaed3f1992478b309529fc15e2e903a27920
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705686"
---
# <a name="lesson-8-defining-actions"></a><span data-ttu-id="3c4e1-102">第 8 課：定義動作</span><span class="sxs-lookup"><span data-stu-id="3c4e1-102">Lesson 8: Defining Actions</span></span>
  <span data-ttu-id="3c4e1-103">在這一課，您將學會定義 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案中的動作。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-103">In this lesson, you will learn to define actions in your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="3c4e1-104">動作只是一個儲存在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的多維度運算式 (MDX) 陳述式，可以併入用戶端應用程式中，由使用者啟動。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-104">An action is just a Multidimensional Expressions (MDX) statement that is stored in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and which can be incorporated into client applications and started by a user.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c4e1-105">此教學課程中，所有課程已完成的專案都可在線上取得。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-105">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="3c4e1-106">您可以從先前的課程中使用已完成的專案做為起點，向前跳到任何課程。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-106">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="3c4e1-107">[按一下這裡](https://go.microsoft.com/fwlink/?LinkID=221866) ，下載此教學課程隨附的範例專案。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-107">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="3c4e1-108">支援下表所說明的動作類型。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-108">supports the types of actions that are described in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3c4e1-109">CommandLine</span><span class="sxs-lookup"><span data-stu-id="3c4e1-109">CommandLine</span></span>|<span data-ttu-id="3c4e1-110">在命令提示字元執行命令。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-110">Executes a command at the command prompt</span></span>|  
|<span data-ttu-id="3c4e1-111">資料集</span><span class="sxs-lookup"><span data-stu-id="3c4e1-111">Dataset</span></span>|<span data-ttu-id="3c4e1-112">將資料集傳回用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-112">Returns a dataset to a client application.</span></span>|  
|<span data-ttu-id="3c4e1-113">鑽研</span><span class="sxs-lookup"><span data-stu-id="3c4e1-113">Drillthrough</span></span>|<span data-ttu-id="3c4e1-114">將 drillthrough 陳述式當做運算式傳回，用戶端會執行這個運算式來傳回資料列集。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-114">Returns a drillthrough statement as an expression, which the client executes to return a rowset</span></span>|  
|<span data-ttu-id="3c4e1-115">HTML</span><span class="sxs-lookup"><span data-stu-id="3c4e1-115">Html</span></span>|<span data-ttu-id="3c4e1-116">在網際網路瀏覽器中執行 HTML 指令碼。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-116">Executes an HTML script in an Internet browser</span></span>|  
|<span data-ttu-id="3c4e1-117">專屬</span><span class="sxs-lookup"><span data-stu-id="3c4e1-117">Proprietary</span></span>|<span data-ttu-id="3c4e1-118">使用不同於此資料表列出的介面來執行作業。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-118">Performs an operation by using an interface other than those listed in this table.</span></span>|  
|<span data-ttu-id="3c4e1-119">報告</span><span class="sxs-lookup"><span data-stu-id="3c4e1-119">Report</span></span>|<span data-ttu-id="3c4e1-120">將一個以 URL 為基礎的參數化要求，提交給報表伺服器，然後將報表傳回用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-120">Submits a parameterized URL-based request to a report server and returns a report to a client application.</span></span>|  
|<span data-ttu-id="3c4e1-121">資料列集</span><span class="sxs-lookup"><span data-stu-id="3c4e1-121">Rowset</span></span>|<span data-ttu-id="3c4e1-122">將資料列集傳回用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-122">Returns a rowset to a client application.</span></span>|  
|<span data-ttu-id="3c4e1-123">陳述式</span><span class="sxs-lookup"><span data-stu-id="3c4e1-123">Statement</span></span>|<span data-ttu-id="3c4e1-124">執行 OLE DB 命令。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-124">Runs an OLE DB command.</span></span>|  
|<span data-ttu-id="3c4e1-125">URL</span><span class="sxs-lookup"><span data-stu-id="3c4e1-125">URL</span></span>|<span data-ttu-id="3c4e1-126">在網際網路瀏覽器中顯示動態網頁。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-126">Displays a dynamic Web page in an Internet browser.</span></span>|  
  
 <span data-ttu-id="3c4e1-127">動作可讓使用者啟動應用程式，或者在所選項目的內容當中執行其他步驟。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-127">Actions let users start an application or perform other steps within the context of a selected item.</span></span> <span data-ttu-id="3c4e1-128">如需詳細資訊，請參閱 [動作 &#40;Analysis Services - 多維度資料&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md)和 [多維度模型中的動作](multidimensional-models/actions-in-multidimensional-models.md)</span><span class="sxs-lookup"><span data-stu-id="3c4e1-128">For more information, see [Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md), [Actions in Multidimensional Models](multidimensional-models/actions-in-multidimensional-models.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c4e1-129">若要取得動作的範例，請參閱 [計算工具] 窗格中 [範本] 索引標籤上的動作範例，或是 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 範例資料倉儲中的範例。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-129">For examples of actions, see the action examples on the Templates tab in the Calculation Tools pane or in the examples in the [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW sample data warehouse.</span></span> <span data-ttu-id="3c4e1-130">如需此資料庫的安裝詳細資訊，請參閱 [安裝 Analysis Services 多維度模型化教學課程的範例資料和專案](install-sample-data-and-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-130">For more information about installing this database, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).</span></span>  
  
 <span data-ttu-id="3c4e1-131">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="3c4e1-131">This lesson includes the following task:</span></span>  
  
 [<span data-ttu-id="3c4e1-132">定義和使用鑽研動作</span><span class="sxs-lookup"><span data-stu-id="3c4e1-132">Defining and Using a Drillthrough Action</span></span>](lesson-8-1-defining-and-using-a-drillthrough-action.md)  
 <span data-ttu-id="3c4e1-133">在這項工作中，您要透過稍早在教學課程中所定義的事實維度關聯性，來定義、使用，然後修改鑽研動作。</span><span class="sxs-lookup"><span data-stu-id="3c4e1-133">In this task, you define, use, and then modify a drillthrough action through the fact dimension relationship that you defined earlier in this tutorial.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="3c4e1-134">下一課</span><span class="sxs-lookup"><span data-stu-id="3c4e1-134">Next Lesson</span></span>  
 [<span data-ttu-id="3c4e1-135">第9課：定義觀點和翻譯</span><span class="sxs-lookup"><span data-stu-id="3c4e1-135">Lesson 9: Defining Perspectives and Translations</span></span>](lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a><span data-ttu-id="3c4e1-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c4e1-136">See Also</span></span>  
 <span data-ttu-id="3c4e1-137">[Analysis Services 教學課程案例](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="3c4e1-137">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="3c4e1-138">[多維度模型化 &#40;的艾德作品教學課程&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="3c4e1-138">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 <span data-ttu-id="3c4e1-139">[&#40;Analysis Services 多維度資料的動作&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="3c4e1-139">[Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="3c4e1-140">多維度模型中的動作</span><span class="sxs-lookup"><span data-stu-id="3c4e1-140">Actions in Multidimensional Models</span></span>](multidimensional-models/actions-in-multidimensional-models.md)  
  
  
