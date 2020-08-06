---
title: 步驟 1：複製第 1 課套件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7f1616c2-2b4e-4010-be50-27d7b897403a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 43e117d82983bdaca8959fe7af8940d248ded97b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596111"
---
# <a name="step-1-copying-the-lesson-1-package"></a><span data-ttu-id="13917-102">步驟 1:複製第 1 課的封裝</span><span class="sxs-lookup"><span data-stu-id="13917-102">Step 1: Copying the Lesson 1 Package</span></span>
  <span data-ttu-id="13917-103">在這項工作中，您將為第 1 課所建立的 Lesson 1.dtsx 套件建立複本。</span><span class="sxs-lookup"><span data-stu-id="13917-103">In this task, you will create a copy of the Lesson 1.dtsx package that you created in Lesson 1.</span></span> <span data-ttu-id="13917-104">如果您並未完成第 1 課，可以將此教學課程中隨附之已完成的第 1 課封裝加入至專案中，然後改為複製該封裝。</span><span class="sxs-lookup"><span data-stu-id="13917-104">If you did not complete Lesson 1, you can add the completed lesson 1 package that is included with the tutorial to the project, and then copy it instead.</span></span> <span data-ttu-id="13917-105">在第 2 課其餘的課程中，您將使用這個新的複本。</span><span class="sxs-lookup"><span data-stu-id="13917-105">You will use this new copy throughout the rest of Lesson 2.</span></span>  
  
### <a name="to-create-the-lesson-2-package"></a><span data-ttu-id="13917-106">若要建立第 2 課的封裝</span><span class="sxs-lookup"><span data-stu-id="13917-106">To create the Lesson 2 package</span></span>  
  
1.  <span data-ttu-id="13917-107">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools 尚未開啟，請按一下 [開始]\*\*\*\*，並依序指向 [所有程式]\*\*\*\* 和 [Microsoft SQL Server 2012]\*\*\*\*，然後按一下 [SQL Server Data Tools]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="13917-107">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2012**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="13917-108">在 [檔案]\*\*\*\* 功能表上，依序按一下 [開啟]\*\*\*\*、[專案/方案]\*\*\*\* 和 [SSIS 教學課程]\*\*\*\* 資料夾，然後按一下 [開啟]\*\*\*\*，再按兩下 [SSIS Tutorial.sln]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="13917-108">On the **File** menu, click **Open**, click **Project/Solution**, click the **SSIS Tutorial** folder and click **Open**, and then double-click **SSIS Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="13917-109">在方案總管中，以滑鼠右鍵按一下 [Lesson 1.dtsx]\*\*\*\*，然後按一下 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="13917-109">In Solution Explorer, right-click **Lesson 1.dtsx**, and then click **Copy**.</span></span>  
  
4.  <span data-ttu-id="13917-110">在方案總管中，以滑鼠右鍵按一下 [ **SSIS 封裝**]，然後按一下 [**貼**上]。</span><span class="sxs-lookup"><span data-stu-id="13917-110">In Solution Explorer, right-click **SSIS Packages**, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="13917-111">依預設，所複製的封裝稱為 Lesson 2.dtsx。</span><span class="sxs-lookup"><span data-stu-id="13917-111">By default, the copied package will be named Lesson 2.dtsx.</span></span>  
  
5.  <span data-ttu-id="13917-112">在方案總管中，按兩下**第2課**以開啟封裝</span><span class="sxs-lookup"><span data-stu-id="13917-112">In Solution Explorer, double-click **Lesson 2.dtsx** to open the package</span></span>  
  
6.  <span data-ttu-id="13917-113">以滑鼠右鍵按一下 [控制流程]\*\*\*\* 設計介面背景的任何位置，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="13917-113">Right-click anywhere in the background of the **Control Flow** design surface and click **Properties**.</span></span>  
  
7.  <span data-ttu-id="13917-114">在屬性視窗中，將 `Name` 屬性更新為 `Lesson 2` 。</span><span class="sxs-lookup"><span data-stu-id="13917-114">In the Properties window, update the `Name` property to `Lesson 2`.</span></span>  
  
8.  <span data-ttu-id="13917-115">按一下 [ID]\*\*\*\* 屬性的方塊，並按一下下拉箭頭，然後按一下 **\<Generate New ID>**。</span><span class="sxs-lookup"><span data-stu-id="13917-115">Click the box for the **ID** property, click the dropdown arrow and then click **\<Generate New ID>**.</span></span>  
  
### <a name="to-add-the-completed-lesson-1-package"></a><span data-ttu-id="13917-116">新增已完成的第 1 課套件</span><span class="sxs-lookup"><span data-stu-id="13917-116">To add the completed Lesson 1 package</span></span>  
  
1.  <span data-ttu-id="13917-117">開啟 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools 及 SSIS 教學課程專案。</span><span class="sxs-lookup"><span data-stu-id="13917-117">Open [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools and open the SSIS Tutorial project.</span></span>  
  
2.  <span data-ttu-id="13917-118">在方案總管中，以滑鼠右鍵按一下 [ **SSIS 封裝**]，然後按一下 [**新增現有套件**]。</span><span class="sxs-lookup"><span data-stu-id="13917-118">In Solution Explorer, right-click **SSIS Packages**, and click **Add Existing Package**.</span></span>  
  
3.  <span data-ttu-id="13917-119">在 [加入現有封裝的複本]  對話方塊的 [封裝位置]  中，選取 [檔案系統]  。</span><span class="sxs-lookup"><span data-stu-id="13917-119">In the **Add Copy of Existing Package** dialog box, in **Package location**, select **File system**.</span></span>  
  
4.  <span data-ttu-id="13917-120">按一下瀏覽 **(…)** 按鈕，巡覽至電腦上的 **Lesson 1.dtsx**，然後按一下 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="13917-120">Click the browse **(...)** button, navigate to **Lesson 1.dtsx** on your machine, and then click **Open**.</span></span>  
  
     <span data-ttu-id="13917-121">若要下載此教學課程的所有課程封裝，請執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="13917-121">To download all of the lesson packages for this tutorial, do the following.</span></span>  
  
    1.  <span data-ttu-id="13917-122">導覽至 [Integration Services 產品範例](https://go.microsoft.com/fwlink/?LinkId=275027)</span><span class="sxs-lookup"><span data-stu-id="13917-122">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="13917-123">按一下 [**下載**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="13917-123">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="13917-124">按一下 SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="13917-124">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="13917-125">複製並貼上第 1 課套件，如上一個程序的步驟 3-8 所述。</span><span class="sxs-lookup"><span data-stu-id="13917-125">Copy and paste the Lesson 1 package as described in steps 3-8 in the previous procedure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="13917-126">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="13917-126">Next Task in Lesson</span></span>  
 [<span data-ttu-id="13917-127">步驟 2:新增和設定 Foreach 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="13917-127">Step 2: Adding and Configuring the Foreach Loop Container</span></span>](lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
  
