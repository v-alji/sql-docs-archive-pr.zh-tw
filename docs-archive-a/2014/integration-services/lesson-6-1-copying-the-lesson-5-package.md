---
title: 步驟 1：複製第 5 課套件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a25fcc13-987e-4f3d-8f0c-76f7e6e59920
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b30ec927084548a2371f22d857d5302e5dc84c5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606985"
---
# <a name="step-1-copying-the-lesson-5-package"></a><span data-ttu-id="220d6-102">步驟 1:複製第 5 課的封裝</span><span class="sxs-lookup"><span data-stu-id="220d6-102">Step 1: Copying the Lesson 5 Package</span></span>
  <span data-ttu-id="220d6-103">在這項工作中，您將為第 5 課所建立的 Lesson 5.dtsx 封裝建立複本。</span><span class="sxs-lookup"><span data-stu-id="220d6-103">In this task, you will create a copy of the Lesson 5.dtsx package that you created in Lesson 5.</span></span> <span data-ttu-id="220d6-104">另外，您也可以將此教學課程中隨附之已完成的第 5 課封裝加入至專案中，然後改為複製該封裝。</span><span class="sxs-lookup"><span data-stu-id="220d6-104">Alternatively, you can add the completed lesson 5 package that is included with the tutorial to the project, and then copy it instead.</span></span> <span data-ttu-id="220d6-105">在第 6 課其餘的課程中，您將使用這個新的副本。</span><span class="sxs-lookup"><span data-stu-id="220d6-105">You will use this new copy throughout the rest of Lesson 6.</span></span>  
  
### <a name="to-copy-the-lesson-5-package"></a><span data-ttu-id="220d6-106">若要複製第 5 課的封裝</span><span class="sxs-lookup"><span data-stu-id="220d6-106">To copy the Lesson 5 package</span></span>  
  
1.  <span data-ttu-id="220d6-107">如果 SQL Server Data Tools 尚未開啟，請按一下 [開始]，依序指向 [所有程式] 和 [Microsoft SQL Server 2012]，然後按一下 [SQL Server Data Tools]。</span><span class="sxs-lookup"><span data-stu-id="220d6-107">If SQL Server Data Tools is not already open, click Start, point to All Programs, point to Microsoft SQL Server 2012, and then click SQL Server Data Tools.</span></span>  
  
2.  <span data-ttu-id="220d6-108">在 [檔案] 功能表上，依序按一下 [開啟] 和 [專案/方案]，選取 [SSIS 教學課程]，然後按一下 [開啟]，再按兩下 SSIS Tutorial.sln。</span><span class="sxs-lookup"><span data-stu-id="220d6-108">On the File menu, click Open, click Project/Solution, select SSIS Tutorial and click Open, and then double-click SSIS Tutorial.sln.</span></span>  
  
3.  <span data-ttu-id="220d6-109">在 [方案總管] 中，以滑鼠右鍵按一下 Lesson 5.dtsx，然後按一下 [複製]。</span><span class="sxs-lookup"><span data-stu-id="220d6-109">In Solution Explorer, right-click Lesson 5.dtsx, and then click Copy.</span></span>  
  
4.  <span data-ttu-id="220d6-110">在 [方案總管] 中，以滑鼠右鍵按一下 [SSIS 封裝]，然後按一下 [貼上]。</span><span class="sxs-lookup"><span data-stu-id="220d6-110">In Solution Explorer, right-click SSIS Packages, and then click Paste.</span></span>  
  
     <span data-ttu-id="220d6-111">依預設，所複製的封裝稱為 Lesson 6.dtsx。</span><span class="sxs-lookup"><span data-stu-id="220d6-111">By default, the copied package is named Lesson 6.dtsx.</span></span>  
  
5.  <span data-ttu-id="220d6-112">在 [方案總管] 中，按兩下 Lesson 6.dtsx 來開啟封裝。</span><span class="sxs-lookup"><span data-stu-id="220d6-112">In the Solution Explorer, double-click Lesson 6.dtsx to open the package.</span></span>  
  
6.  <span data-ttu-id="220d6-113">以滑鼠右鍵按一下 [控制流程] 索引標籤背景的任何位置，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="220d6-113">Right-click anywhere in the background of the Control Flow tab then click Properties.</span></span>  
  
7.  <span data-ttu-id="220d6-114">在 [屬性] 視窗中，將 Name 屬性更新為第 6 課。</span><span class="sxs-lookup"><span data-stu-id="220d6-114">In the Properties window, update the Name property to Lesson 6.</span></span>  
  
8.  <span data-ttu-id="220d6-115">依序按一下 ID 屬性的方塊、下拉箭頭及 [ \<Generate New ID>]。</span><span class="sxs-lookup"><span data-stu-id="220d6-115">Click the box for the ID property, then click the dropdown arrow, and then click \<Generate New ID>.</span></span>  
  
### <a name="to-add-the-completed-lesson-5-package"></a><span data-ttu-id="220d6-116">若要加入已完成的第 5 課封裝</span><span class="sxs-lookup"><span data-stu-id="220d6-116">To add the completed Lesson 5 package</span></span>  
  
1.  <span data-ttu-id="220d6-117">開啟 SQL Server Data Tools 及 SSIS 教學課程專案。</span><span class="sxs-lookup"><span data-stu-id="220d6-117">Open SQL Server Data Tools and open the SSIS Tutorial project.</span></span>  
  
2.  <span data-ttu-id="220d6-118">在 [方案總管] 中，以滑鼠右鍵按一下 [SSIS 封裝]，然後按一下 [加入現有的封裝]。</span><span class="sxs-lookup"><span data-stu-id="220d6-118">In Solution Explorer, right-click SSIS Packages, and click Add Existing Package.</span></span>  
  
3.  <span data-ttu-id="220d6-119">在 [加入現有封裝的副本] 對話方塊的 [封裝位置] 中，選取 [檔案系統]。</span><span class="sxs-lookup"><span data-stu-id="220d6-119">In the Add Copy of Existing Package dialog box, in Package location, select File system.</span></span>  
  
4.  <span data-ttu-id="220d6-120">按一下瀏覽 (...) 按鈕，巡覽至電腦上的 Lesson 5.dtsx，然後按一下 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="220d6-120">Click the browse (...) button, Lesson 5.dtsx on your machine, and then click **Open**.</span></span>  
  
     <span data-ttu-id="220d6-121">若要下載此教學課程的所有課程封裝，請執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="220d6-121">To download all of the lesson packages for this tutorial, do the following.</span></span>  
  
    1.  <span data-ttu-id="220d6-122">導覽至 [Integration Services 產品範例](https://go.microsoft.com/fwlink/?LinkId=275027)</span><span class="sxs-lookup"><span data-stu-id="220d6-122">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="220d6-123">按一下 [**下載**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="220d6-123">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="220d6-124">按一下 SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="220d6-124">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="220d6-125">複製並貼上第 5 課封裝，如上一個程序的步驟 3-8 所述。</span><span class="sxs-lookup"><span data-stu-id="220d6-125">Copy and paste the Lesson 5 package as described in steps 3-8 in the previous procedure.</span></span>  
  
     <span data-ttu-id="220d6-126">在複製第 5 課封裝之後，如果您目前在方案中已經有之前課程的封裝，請以滑鼠右鍵按一下 1-5 課的每一個封裝，並按一下 [從專案移除]。</span><span class="sxs-lookup"><span data-stu-id="220d6-126">After copying the Lesson 5 package, if you currently have the packages from the previous lessons in your solution, right-click each package from lessons 1-5 and click Exclude From Project.</span></span> <span data-ttu-id="220d6-127">當您完成時，您的方案中應該只有 Lesson 6.dtsx。</span><span class="sxs-lookup"><span data-stu-id="220d6-127">When done you should have only Lesson 6.dtsx in your solution.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="220d6-128">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="220d6-128">Next Task in Lesson</span></span>  
 [<span data-ttu-id="220d6-129">步驟 2:將專案轉換成專案部署模型</span><span class="sxs-lookup"><span data-stu-id="220d6-129">Step 2: Converting the Project to the Project Deployment Model</span></span>](lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
  
