---
title: 步驟 1：建立新的 Integration Services 專案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f14521b5-941e-443b-8f5e-385f98e37fbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d6d16d7febcdecb01eb7a93167c2a18d225a9c2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596148"
---
# <a name="step-1-creating-a-new-integration-services-project"></a><span data-ttu-id="3d617-102">步驟 1:建立新的 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="3d617-102">Step 1: Creating a New Integration Services Project</span></span>
  <span data-ttu-id="3d617-103">在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中建立封裝的第一步就是建立 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="3d617-103">The first step in creating a package in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] is to create an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="3d617-104">這個專案包含物件的範本 (資料來源、資料來源檢視和封裝)，您在資料轉換方案中會用到它們。</span><span class="sxs-lookup"><span data-stu-id="3d617-104">This project includes the templates for the objects - data sources, data source views, and packages - that you use in a data transformation solution.</span></span>  
  
 <span data-ttu-id="3d617-105">您在這個 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 教學課程中建立的封裝將解譯區分地區設定資料的值。</span><span class="sxs-lookup"><span data-stu-id="3d617-105">The packages that you will create in this [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] tutorial interpret the values of locale-sensitive data.</span></span> <span data-ttu-id="3d617-106">如果電腦未設定為使用地區設定選項 [英文 (美國)]，則您需要在封裝中設定其他屬性。</span><span class="sxs-lookup"><span data-stu-id="3d617-106">If your computer is not configured to use the regional option English (United States), you need to set additional properties in the package.</span></span> <span data-ttu-id="3d617-107">您在第 2 課到第 5 課使用的封裝，是從第 1 課建立的封裝複製而來，您不需要在複製的封裝中更新區分地區設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="3d617-107">The packages that you use in lessons 2 through 5 are copied from the package created in lesson 1, and you need not update locale-sensitive properties in the copied packages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3d617-108">這個教學課程需要 Microsoft SQL Server Data Tools。</span><span class="sxs-lookup"><span data-stu-id="3d617-108">This tutorial requires Microsoft SQL Server Data Tools.</span></span>  
>   
>  <span data-ttu-id="3d617-109">如需安裝 SQL Server Data Tools 的詳細資訊，請參閱 [SQL Server Data Tools 下載](https://msdn.microsoft.com/data/hh297027)。</span><span class="sxs-lookup"><span data-stu-id="3d617-109">For more information on installing the SQL Server Data Tools see [SQL Server Data Tools Download](https://msdn.microsoft.com/data/hh297027).</span></span>  
  
### <a name="to-create-a-new-integration-services-project"></a><span data-ttu-id="3d617-110">若要建立新的 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="3d617-110">To create a new Integration Services project</span></span>  
  
1.  <span data-ttu-id="3d617-111">在 **[開始]** 功能表上，依序指向 **[所有程式]** 和 **[Microsoft SQL Server]** ，然後按一下 **[SQL Server Data Tools]** 。</span><span class="sxs-lookup"><span data-stu-id="3d617-111">On the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server**, and click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="3d617-112">在 **[檔案]** 功能表上，指向 **[新增]**，然後按一下 **[專案]** 來建立新的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="3d617-112">On the **File** menu, point to **New**, and click **Project** to create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
3.  <span data-ttu-id="3d617-113">在 **[新增專案]** 對話方塊中，展開 **[已安裝的範本]** 底下的 **[商業智慧]** 節點，然後選取 **[範本]** 窗格中的 **[Integration Services 專案]** 。</span><span class="sxs-lookup"><span data-stu-id="3d617-113">In the **New Project** dialog box, expand the **Business Intelligence** node under **Installed Templates**, and select **Integration Services Project** in the **Templates** pane.</span></span>  
  
4.  <span data-ttu-id="3d617-114">在 **[名稱]** 方塊中，將預設名稱變更為 **SSIS 教學課程**。</span><span class="sxs-lookup"><span data-stu-id="3d617-114">In the **Name** box, change the default name to **SSIS Tutorial**.</span></span> <span data-ttu-id="3d617-115">您可以選擇性地清除 **[建立方案的目錄]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="3d617-115">Optionally, clear the **Create directory for solution** check box.</span></span>  
  
5.  <span data-ttu-id="3d617-116">接受預設位置，或按一下 **[瀏覽]** 來瀏覽並尋找您要使用的資料夾。</span><span class="sxs-lookup"><span data-stu-id="3d617-116">Accept the default location, or click **Browse** to browse to locate the folder you want to use.</span></span> <span data-ttu-id="3d617-117">在 **[專案位置]** 對話方塊中，按一下該資料夾，然後按一下 **[選取資料夾]**。</span><span class="sxs-lookup"><span data-stu-id="3d617-117">In the **Project Location** dialog box, click the folder and click **Select Folder**.</span></span>  
  
6.  <span data-ttu-id="3d617-118">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="3d617-118">Click **OK**.</span></span>  
  
     <span data-ttu-id="3d617-119">根據預設，系統會建立標題為 **Package.dtsx**的空白封裝，並加入至 SSIS 封裝底下的專案。</span><span class="sxs-lookup"><span data-stu-id="3d617-119">By default, an empty package, titled **Package.dtsx**, will be created and added to your project under SSIS Packages.</span></span>  
  
7.  <span data-ttu-id="3d617-120">在 [ **方案總管** ] 工具列上，以滑鼠右鍵按一下 [ **Package.dtsx**]、按一下 **[重新命名]**，然後將預設封裝重新命名為 **Lesson 1.dtsx**。</span><span class="sxs-lookup"><span data-stu-id="3d617-120">In **Solution Explorer** toolbar, right-click **Package.dtsx**, click **Rename**, and rename the default package to **Lesson 1.dtsx**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="3d617-121">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="3d617-121">Next Task in Lesson</span></span>  
 [<span data-ttu-id="3d617-122">步驟 2:新增和設定一般檔案連線管理員</span><span class="sxs-lookup"><span data-stu-id="3d617-122">Step 2: Adding and Configuring a Flat File Connection Manager</span></span>](lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
  
