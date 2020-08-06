---
title: 步驟 1：複製第 4 課套件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8aa7d690-4649-4c0a-ac6f-9504637ee426
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1140c0e7d26f11f79e18d42143c1ed084c4ff144
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606417"
---
# <a name="step-1-copying-the-lesson-4-package"></a><span data-ttu-id="64fcd-102">步驟 1:複製第 4 課的封裝</span><span class="sxs-lookup"><span data-stu-id="64fcd-102">Step 1: Copying the Lesson 4 Package</span></span>
  <span data-ttu-id="64fcd-103">在這項工作中，您將為第 4 課所建立的 Lesson 4.dtsx 套件建立複本。</span><span class="sxs-lookup"><span data-stu-id="64fcd-103">In this task, you will create a copy of the Lesson 4.dtsx package that you created in Lesson 4.</span></span> <span data-ttu-id="64fcd-104">另外，您也可以將此教學課程中隨附之已完成的第 4 課套件加入至專案中，然後改為複製該套件。</span><span class="sxs-lookup"><span data-stu-id="64fcd-104">Alternatively, you can add the completed lesson 4 package that is included with the tutorial to the project, and then copy it instead.</span></span> <span data-ttu-id="64fcd-105">在第 5 課其餘的課程中，您將使用這個新的副本。</span><span class="sxs-lookup"><span data-stu-id="64fcd-105">You will use this new copy throughout the rest of Lesson 5.</span></span>  
  
### <a name="to-copy-the-lesson-4-package"></a><span data-ttu-id="64fcd-106">複製第 4 課的套件</span><span class="sxs-lookup"><span data-stu-id="64fcd-106">To copy the Lesson 4 package</span></span>  
  
1.  <span data-ttu-id="64fcd-107">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools 尚未開啟，請按一下 [開始]\*\*\*\*，並依序指向 [所有程式]\*\*\*\* 和 [Microsoft SQL Server 2012]\*\*\*\*，然後按一下 [SQL Server Data Tools]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="64fcd-107">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2012**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="64fcd-108">在 [檔案]\*\*\*\* 功能表上，依序按一下 [開啟]\*\*\*\* 和 [專案/方案]\*\*\*\*，選取 [SSIS 教學課程]\*\*\*\*，再按一下 [開啟]\*\*\*\*，然後按兩下 **SSIS Tutorial.sln**。</span><span class="sxs-lookup"><span data-stu-id="64fcd-108">On the **File** menu, click **Open**, click **Project/Solution**, select **SSIS Tutorial** and click **Open**, and then double-click **SSIS Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="64fcd-109">在方案總管中，以滑鼠右鍵按一下 **Lesson 4.dtsx**，然後按一下 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="64fcd-109">In Solution Explorer, right-click **Lesson 4.dtsx**, and then click **Copy**.</span></span>  
  
4.  <span data-ttu-id="64fcd-110">在方案總管中，以滑鼠右鍵按一下 [ **SSIS 封裝**]，然後按一下 [**貼**上]。</span><span class="sxs-lookup"><span data-stu-id="64fcd-110">In Solution Explorer, right-click **SSIS Packages**, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="64fcd-111">依預設，所複製的套件稱為 Lesson 5.dtsx。</span><span class="sxs-lookup"><span data-stu-id="64fcd-111">By default, the copied package is named Lesson 5.dtsx.</span></span>  
  
5.  <span data-ttu-id="64fcd-112">在方案總管中，按兩下 **Lesson 5.dtsx** 來開啟套件。</span><span class="sxs-lookup"><span data-stu-id="64fcd-112">In the Solution Explorer, double-click **Lesson 5.dtsx** to open the package.</span></span>  
  
6.  <span data-ttu-id="64fcd-113">以滑鼠右鍵按一下 [**控制流程**] 索引標籤背景的任何位置，然後按一下 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="64fcd-113">Right-click anywhere in the background of the **Control Flow** tab then click **Properties**.</span></span>  
  
7.  <span data-ttu-id="64fcd-114">在屬性視窗中，將 `Name` 屬性更新為 `Lesson 5` 。</span><span class="sxs-lookup"><span data-stu-id="64fcd-114">In the Properties window, update the `Name` property to `Lesson 5`.</span></span>  
  
8.  <span data-ttu-id="64fcd-115">依序按一下 **ID** 屬性的方塊、下拉箭頭及 [ **\<Generate New ID>**]。</span><span class="sxs-lookup"><span data-stu-id="64fcd-115">Click the box for the **ID** property, then click the dropdown arrow, and then click **\<Generate New ID>**.</span></span>  
  
### <a name="to-add-the-completed-lesson-4-package"></a><span data-ttu-id="64fcd-116">新增已完成的第 4 課套件</span><span class="sxs-lookup"><span data-stu-id="64fcd-116">To add the completed Lesson 4 package</span></span>  
  
1.  <span data-ttu-id="64fcd-117">開啟 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools 及 SSIS 教學課程專案。</span><span class="sxs-lookup"><span data-stu-id="64fcd-117">Open [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools and open the SSIS Tutorial project.</span></span>  
  
2.  <span data-ttu-id="64fcd-118">在方案總管中，以滑鼠右鍵按一下 [ **SSIS 封裝**]，然後按一下 [**新增現有套件**]。</span><span class="sxs-lookup"><span data-stu-id="64fcd-118">In Solution Explorer, right-click **SSIS Packages**, and click **Add Existing Package**.</span></span>  
  
3.  <span data-ttu-id="64fcd-119">在 [加入現有封裝的複本]  對話方塊的 [封裝位置]  中，選取 [檔案系統]  。</span><span class="sxs-lookup"><span data-stu-id="64fcd-119">In the **Add Copy of Existing Package** dialog box, in **Package location**, select **File system**.</span></span>  
  
4.  <span data-ttu-id="64fcd-120">按一下瀏覽 **(...)** 按鈕，巡覽至電腦上的 **Lesson 4.dtsx**，然後按一下 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="64fcd-120">Click the browse **(...)** button, navigate to **Lesson 4.dtsx** on your machine, and then click **Open**.</span></span>  
  
     <span data-ttu-id="64fcd-121">若要下載此教學課程的所有課程封裝，請執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="64fcd-121">To download all of the lesson packages for this tutorial, do the following.</span></span>  
  
    1.  <span data-ttu-id="64fcd-122">導覽至 [Integration Services 產品範例](https://go.microsoft.com/fwlink/?LinkId=275027)</span><span class="sxs-lookup"><span data-stu-id="64fcd-122">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="64fcd-123">按一下 [**下載**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="64fcd-123">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="64fcd-124">按一下 SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="64fcd-124">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="64fcd-125">複製並貼上第 4 課套件，如上一個程序的步驟 3-8 所述。</span><span class="sxs-lookup"><span data-stu-id="64fcd-125">Copy and paste the Lesson 4 package as described in steps 3-8 in the previous procedure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="64fcd-126">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="64fcd-126">Next Task in Lesson</span></span>  
 [<span data-ttu-id="64fcd-127">步驟 2:啟用和設定封裝組態</span><span class="sxs-lookup"><span data-stu-id="64fcd-127">Step 2: Enabling and Configuring Package Configurations</span></span>](lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
  
