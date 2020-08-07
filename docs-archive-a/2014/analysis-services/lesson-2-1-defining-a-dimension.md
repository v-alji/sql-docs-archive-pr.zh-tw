---
title: 定義維度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 112696db-3838-4b50-91bd-d2ce5fa04ee5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2eb7a695ffc2c0588396a4a9ea655983c26cc719
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584778"
---
# <a name="defining-a-dimension"></a><span data-ttu-id="d7878-102">定義維度</span><span class="sxs-lookup"><span data-stu-id="d7878-102">Defining a Dimension</span></span>
  <span data-ttu-id="d7878-103">在下列工作中，您將使用「維度精靈」來建立「日期」維度。</span><span class="sxs-lookup"><span data-stu-id="d7878-103">In the following task, you will use the Dimension Wizard to build a Date dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7878-104">您必須先完成第 1 課的所有程序，才能進行這一課。</span><span class="sxs-lookup"><span data-stu-id="d7878-104">This lesson requires that you have completed all the procedures in Lesson 1.</span></span>  
  
### <a name="to-define-a-dimension"></a><span data-ttu-id="d7878-105">定義維度</span><span class="sxs-lookup"><span data-stu-id="d7878-105">To define a dimension</span></span>  
  
1.  <span data-ttu-id="d7878-106">在方案總管中 (於 Microsoft Visual Studio 視窗右側)，以滑鼠右鍵按一下 [維度]\*\*\*\*，然後按一下 [新增維度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d7878-106">In Solution Explorer (on the right side of Microsoft Visual Studio), right-click **Dimensions**, and then click **New Dimension**.</span></span> <span data-ttu-id="d7878-107">[維度精靈] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d7878-107">The Dimension Wizard appears.</span></span>  
  
2.  <span data-ttu-id="d7878-108">在 [歡迎使用維度精靈]\*\*\*\* 頁面上，按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d7878-108">On the **Welcome to the Dimension Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="d7878-109">在 [選取建立方法]\*\*\*\* 頁面上，確認已選取 [使用現有的資料表]\*\*\*\* 選項，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d7878-109">On the **Select Creation Method** page, verify that the **Use an existing table** option is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="d7878-110">在 [指定來源資訊]\*\*\*\* 頁面上，確認已選取 **Adventure Works DW 2012** 資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="d7878-110">On the **Specify Source Information** page, verify that the **Adventure Works DW 2012** data source view is selected.</span></span>  
  
5.  <span data-ttu-id="d7878-111">在 [主資料表]\*\*\*\* 清單中，選取 [日期]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d7878-111">In the **Main table** list, select **Date**.</span></span>  
  
6.  <span data-ttu-id="d7878-112">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="d7878-112">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="d7878-113">在 [選取維度屬性]\*\*\*\* 頁面上，選取下列屬性旁的核取方塊：</span><span class="sxs-lookup"><span data-stu-id="d7878-113">On the **Select Dimension Attributes** page, select the check boxes next to the following attributes:</span></span>  
  
    -   <span data-ttu-id="d7878-114">**日期索引鍵**</span><span class="sxs-lookup"><span data-stu-id="d7878-114">**Date Key**</span></span>  
  
    -   <span data-ttu-id="d7878-115">**完整日期替代索引鍵**</span><span class="sxs-lookup"><span data-stu-id="d7878-115">**Full Date Alternate Key**</span></span>  
  
    -   <span data-ttu-id="d7878-116">**英文月份**</span><span class="sxs-lookup"><span data-stu-id="d7878-116">**English Month Name**</span></span>  
  
    -   <span data-ttu-id="d7878-117">**日曆季**</span><span class="sxs-lookup"><span data-stu-id="d7878-117">**Calendar Quarter**</span></span>  
  
    -   <span data-ttu-id="d7878-118">**行事歷年度**</span><span class="sxs-lookup"><span data-stu-id="d7878-118">**Calendar Year**</span></span>  
  
    -   <span data-ttu-id="d7878-119">**Calendar Semester**</span><span class="sxs-lookup"><span data-stu-id="d7878-119">**Calendar Semester**</span></span>  
  
8.  <span data-ttu-id="d7878-120">將 [完整日期替代索引鍵]\*\*\*\* 屬性之 [屬性類型]\*\*\*\* 資料行的設定，從 [一般]\*\*\*\* 變更為 [日期]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d7878-120">Change the setting of the **Full Date Alternate Key** attribute's **Attribute Type** column from **Regular** to **Date**.</span></span> <span data-ttu-id="d7878-121">若要這樣做，請在 [屬性類型]\*\*\*\* 資料行中按一下 [一般]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d7878-121">To do this, click **Regular** in the **Attribute Type** column.</span></span> <span data-ttu-id="d7878-122">然後，按一下箭號，以便展開選項。</span><span class="sxs-lookup"><span data-stu-id="d7878-122">Then click the arrow to expand the options.</span></span> <span data-ttu-id="d7878-123">接下來，按一下 [**日期**行事  >  **曆**  >  **日期**]。</span><span class="sxs-lookup"><span data-stu-id="d7878-123">Next, click **Date** > **Calendar** > **Date**.</span></span> <span data-ttu-id="d7878-124">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d7878-124">Click **OK**.</span></span> <span data-ttu-id="d7878-125">重複這些步驟，即可變更屬性的屬性類型，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d7878-125">Repeat these steps to change the attribute type of the attributes as follows:</span></span>  
  
    -   <span data-ttu-id="d7878-126">[英文月份名稱]\*\*\*\* 變更為 [月]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d7878-126">**English Month Name** to **Month**</span></span>  
  
    -   <span data-ttu-id="d7878-127">[日曆季]\*\*\*\* 變更為 [季]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d7878-127">**Calendar Quarter** to **Quarter**</span></span>  
  
    -   <span data-ttu-id="d7878-128">[日曆年度]\*\*\*\* 變更為 [年度]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d7878-128">**Calendar Year** to **Year**</span></span>  
  
    -   <span data-ttu-id="d7878-129">[日曆半年度]\*\*\*\* 變更為 [半年]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d7878-129">**Calendar Semester** to **Half Year**</span></span>  
  
9. <span data-ttu-id="d7878-130">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="d7878-130">Click **Next**.</span></span>  
  
10. <span data-ttu-id="d7878-131">在 [正在完成精靈]\*\*\*\* 頁面上，您可以在 [預覽] 窗格中看見 [日期]\*\*\*\* 維度及其屬性。</span><span class="sxs-lookup"><span data-stu-id="d7878-131">On the **Completing the Wizard** page, in the Preview pane, you can see the **Date** dimension and its attributes.</span></span>  
  
11. <span data-ttu-id="d7878-132">按一下 [完成]\*\*\*\* 以完成程序。</span><span class="sxs-lookup"><span data-stu-id="d7878-132">Click **Finish** to complete the wizard.</span></span>  
  
     <span data-ttu-id="d7878-133">在方案總管的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程專案中，[日期] 維度會顯示在 [維度]\*\*\*\* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="d7878-133">In Solution Explorer, in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, the Date dimension appears in the **Dimensions** folder.</span></span> <span data-ttu-id="d7878-134">在開發環境的中心，維度設計師會顯示「日期」維度。</span><span class="sxs-lookup"><span data-stu-id="d7878-134">In the center of the development environment, Dimension Designer displays the Date dimension.</span></span>  
  
12. <span data-ttu-id="d7878-135">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="d7878-135">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="d7878-136">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="d7878-136">Next Task in Lesson</span></span>  
 [<span data-ttu-id="d7878-137">定義 Cube</span><span class="sxs-lookup"><span data-stu-id="d7878-137">Defining a Cube</span></span>](lesson-2-2-defining-a-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="d7878-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7878-138">See Also</span></span>  
 <span data-ttu-id="d7878-139">[多維度模型中的維度](multidimensional-models/dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="d7878-139">[Dimensions in Multidimensional Models](multidimensional-models/dimensions-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="d7878-140">[使用現有的資料表建立維度](multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span><span class="sxs-lookup"><span data-stu-id="d7878-140">[Create a Dimension by Using an Existing Table](multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span></span>  
 [<span data-ttu-id="d7878-141">使用維度精靈建立維度</span><span class="sxs-lookup"><span data-stu-id="d7878-141">Create a Dimension Using the Dimension Wizard</span></span>](multidimensional-models/create-a-dimension-using-the-dimension-wizard.md)  
  
  
