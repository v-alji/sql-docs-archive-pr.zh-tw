---
title: 步驟 1：複製第 3 課的封裝 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0d053786-5203-43f3-a613-27a8dd2bc44a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fde3bd907e8a55b1ac9a164b2960268189b19392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595179"
---
# <a name="step-1-copying-the-lesson-3-package"></a><span data-ttu-id="e9834-102">步驟 1:複製第 3 課的封裝</span><span class="sxs-lookup"><span data-stu-id="e9834-102">Step 1: Copying the Lesson 3 Package</span></span>
  <span data-ttu-id="e9834-103">在這項工作中，您將為第 3 課所建立的 Lesson 3.dtsx 套件建立複本。</span><span class="sxs-lookup"><span data-stu-id="e9834-103">In this task, you will create a copy of the Lesson 3.dtsx package that you created in Lesson 3.</span></span> <span data-ttu-id="e9834-104">另外，如果您並未完成第 3 課，可以將此教學課程中隨附之已完成的第 3 課封裝加入至專案中，然後建立該封裝的複本來使用。</span><span class="sxs-lookup"><span data-stu-id="e9834-104">Alternatively, if you did not complete lesson 3, you can add the completed lesson 3 package that is included with the tutorial to the project, and then make a copy of it to work with.</span></span> <span data-ttu-id="e9834-105">在第 4 課的其餘課程中，您將使用這個新的複本。</span><span class="sxs-lookup"><span data-stu-id="e9834-105">You will use this new copy throughout the rest of Lesson 4.</span></span>  
  
### <a name="to-create-the-lesson-4-package"></a><span data-ttu-id="e9834-106">建立第 4 課的套件</span><span class="sxs-lookup"><span data-stu-id="e9834-106">To create the Lesson 4 package</span></span>  
  
1.  <span data-ttu-id="e9834-107">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools 尚未開啟，請按一下 [開始]\*\*\*\*，並依序指向 [所有程式]\*\*\*\* 和 [Microsoft SQL Server]\*\*\*\*，然後按一下 [SQL Server Data Tools]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e9834-107">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="e9834-108">在 [檔案]\*\*\*\* 功能表上，依序按一下 [開啟]\*\*\*\* 和 [專案/方案]\*\*\*\*，選取 [SSIS 教學課程]\*\*\*\*，再按一下 [開啟]\*\*\*\*，然後按兩下 **SSIS Tutorial.sln**。</span><span class="sxs-lookup"><span data-stu-id="e9834-108">On the **File** menu, click **Open**, click **Project/Solution**, select **SSIS Tutorial** and click **Open**, and then double-click **SSIS Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="e9834-109">在方案總管中，以滑鼠右鍵按一下 **Lesson 3.dtsx**，然後按一下 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e9834-109">In Solution Explorer, right-click **Lesson 3.dtsx**, and then click **Copy**.</span></span>  
  
4.  <span data-ttu-id="e9834-110">在方案總管中，以滑鼠右鍵按一下 [ **SSIS 封裝**]，然後按一下 [**貼**上]。</span><span class="sxs-lookup"><span data-stu-id="e9834-110">In Solution Explorer, right-click **SSIS Packages**, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="e9834-111">依預設，所複製的套件稱為 Lesson 4.dtsx。</span><span class="sxs-lookup"><span data-stu-id="e9834-111">By default, the copied package is named Lesson 4.dtsx.</span></span>  
  
5.  <span data-ttu-id="e9834-112">在方案總管中，按兩下 [**第4課**] 以開啟封裝。</span><span class="sxs-lookup"><span data-stu-id="e9834-112">In Solution Explorer, double-click **Lesson 4.dtsx** to open the package.</span></span>  
  
6.  <span data-ttu-id="e9834-113">以滑鼠右鍵按一下 [控制流程]\*\*\*\* 索引標籤背景的任何位置，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e9834-113">Right-click anywhere in the background of the **Control Flow** tab and click **Properties**.</span></span>  
  
7.  <span data-ttu-id="e9834-114">在屬性視窗中，將 `Name` 屬性更新為 `Lesson 4` 。</span><span class="sxs-lookup"><span data-stu-id="e9834-114">In the Properties window, update the `Name` property to `Lesson 4`.</span></span>  
  
8.  <span data-ttu-id="e9834-115">按一下 [識別碼]\*\*\*\* 屬性的方塊，然後在清單中按一下 [\<Generate New ID>]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e9834-115">Click the box for the **ID** property, and then in the list, click **\<Generate New ID>**.</span></span>  
  
### <a name="to-add-the-completed-lesson-3-package"></a><span data-ttu-id="e9834-116">新增已完成的第 3 課套件</span><span class="sxs-lookup"><span data-stu-id="e9834-116">To add the completed Lesson 3 package</span></span>  
  
1.  <span data-ttu-id="e9834-117">開啟 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 及開啟 SSIS 教學課程專案。</span><span class="sxs-lookup"><span data-stu-id="e9834-117">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and open the SSIS Tutorial project.</span></span>  
  
2.  <span data-ttu-id="e9834-118">在方案總管中，以滑鼠右鍵按一下 [ **SSIS 封裝**]，然後按一下 [**新增現有套件**]。</span><span class="sxs-lookup"><span data-stu-id="e9834-118">In Solution Explorer, right-click **SSIS Packages**, and click **Add Existing Package**.</span></span>  
  
3.  <span data-ttu-id="e9834-119">在 [加入現有封裝的複本]  對話方塊的 [封裝位置]  中，選取 [檔案系統]  。</span><span class="sxs-lookup"><span data-stu-id="e9834-119">In the **Add Copy of Existing Package** dialog box, in **Package location**, select **File system**.</span></span>  
  
4.  <span data-ttu-id="e9834-120">按一下瀏覽 **(…)** 按鈕，巡覽至電腦上的 Lesson 3.dtsx，然後按一下 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e9834-120">Click the browse **(...)** button, navigate to Lesson 3.dtsx on your machine, and then click **Open**.</span></span>  
  
     <span data-ttu-id="e9834-121">若要下載此教學課程的所有課程封裝，請執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="e9834-121">To download all of the lesson packages for this tutorial, do the following.</span></span>  
  
    1.  <span data-ttu-id="e9834-122">導覽至 [Integration Services 產品範例](https://go.microsoft.com/fwlink/?LinkId=275027)</span><span class="sxs-lookup"><span data-stu-id="e9834-122">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="e9834-123">按一下 [**下載**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e9834-123">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="e9834-124">按一下 SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="e9834-124">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="e9834-125">複製並貼上第 3 課中的套件，如上一個程序的步驟 3-8 所述。</span><span class="sxs-lookup"><span data-stu-id="e9834-125">Copy and paste the Lesson 3 package as described in steps 3-8 in the previous procedure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="e9834-126">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="e9834-126">Next Task in Lesson</span></span>  
 [<span data-ttu-id="e9834-127">步驟 2:建立損毀的檔案</span><span class="sxs-lookup"><span data-stu-id="e9834-127">Step 2: Creating a Corrupted File</span></span>](lesson-4-2-creating-a-corrupted-file.md)  
  
  
