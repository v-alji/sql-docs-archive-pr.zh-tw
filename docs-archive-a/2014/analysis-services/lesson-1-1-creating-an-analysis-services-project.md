---
title: 建立 Analysis Services 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 065fdc60-1791-4e27-9ed5-51d751b3f8c4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 50640dd7821943dfc3914326f7e8cba32253d307
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584800"
---
# <a name="creating-an-analysis-services-project"></a><span data-ttu-id="ea830-102">建立 Analysis Services 專案</span><span class="sxs-lookup"><span data-stu-id="ea830-102">Creating an Analysis Services Project</span></span>
  <span data-ttu-id="ea830-103">在下列工作中，您會 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] `Analysis Services Tutorial` 根據專案範本，使用來建立名為的新專案 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ea830-103">In the following task, you use [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create a new [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project named `Analysis Services Tutorial`, based on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Project template.</span></span> <span data-ttu-id="ea830-104">*「專案」* (Project) 是相關物件的集合。</span><span class="sxs-lookup"><span data-stu-id="ea830-104">A *project* is a collection of related objects.</span></span> <span data-ttu-id="ea830-105">專案存在於方案內，方案包括一或多個專案。</span><span class="sxs-lookup"><span data-stu-id="ea830-105">Projects exist within a solution, which includes one or more projects.</span></span> <span data-ttu-id="ea830-106">如需詳細資訊，請參閱 [建立 Analysis Services 專案 &#40;SSDT&#41;](multidimensional-models/create-an-analysis-services-project-ssdt.md)。</span><span class="sxs-lookup"><span data-stu-id="ea830-106">For more information, see [Create an Analysis Services Project &#40;SSDT&#41;](multidimensional-models/create-an-analysis-services-project-ssdt.md).</span></span>  
  
### <a name="to-create-a-new-analysis-services-project"></a><span data-ttu-id="ea830-107">若要建立新的 Analysis Services 專案</span><span class="sxs-lookup"><span data-stu-id="ea830-107">To create a new Analysis Services project</span></span>  
  
1.  <span data-ttu-id="ea830-108">按一下 **[開始]**、依序指向 **[所有程式]** 和 **[Microsoft SQL Server 2012]**，然後按一下 **[SQL Server 資料工具]**。</span><span class="sxs-lookup"><span data-stu-id="ea830-108">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2012**, and then click **SQL Server Data Tools**.</span></span>  
  
     <span data-ttu-id="ea830-109">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 開發環境隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="ea830-109">The [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] development environment opens.</span></span>  
  
2.  <span data-ttu-id="ea830-110">在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的起始頁面上，按一下 **[新增專案]**。</span><span class="sxs-lookup"><span data-stu-id="ea830-110">On the Start page of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], click **New Project**.</span></span>  
  
3.  <span data-ttu-id="ea830-111">在 **[新增專案]** 對話方塊的 **[已安裝的範本]** 窗格中，展開 **[Business Intelligence]**，然後選取 **[Analysis Services]**。</span><span class="sxs-lookup"><span data-stu-id="ea830-111">In the **New Project** dialog box, in the **Installed Templates** pane, expand **Business Intelligence**, and then select **Analysis Services**.</span></span> <span data-ttu-id="ea830-112">選擇 **[Analysis Services 多維度和資料採礦專案]** 範本。</span><span class="sxs-lookup"><span data-stu-id="ea830-112">Choose the **Analysis Services Multidimensional and Data Mining Project** template.</span></span>  
  
     <span data-ttu-id="ea830-113">請注意，對話方塊底端會產生預設專案名稱、位置和預設方案名稱。</span><span class="sxs-lookup"><span data-stu-id="ea830-113">Notice the default project name, location, and the default solution name are generated in the bottom of the dialog box.</span></span> <span data-ttu-id="ea830-114">根據預設，會為方案建立新目錄。</span><span class="sxs-lookup"><span data-stu-id="ea830-114">By default, a new directory is created for the solution.</span></span>  
  
4.  <span data-ttu-id="ea830-115">將專案名稱變更為 `Analysis Services Tutorial` ，這也會變更 [**方案名稱**] 方塊，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="ea830-115">Change the project Name to `Analysis Services Tutorial`, which also changes the **Solution name** box, and then click **OK**.</span></span>  
  
 <span data-ttu-id="ea830-116">您已 `Analysis Services Tutorial` 根據在也名為的新方案中的**Analysis Services 多維度和資料採礦專案**範本，成功建立專案 `Analysis Services Tutorial` 。</span><span class="sxs-lookup"><span data-stu-id="ea830-116">You have successfully created the `Analysis Services Tutorial` project, based on the **Analysis Services Multidimensional and Data Mining Project** template, within a new solution that is also named `Analysis Services Tutorial`.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="ea830-117">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="ea830-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="ea830-118">定義資料來源</span><span class="sxs-lookup"><span data-stu-id="ea830-118">Defining a Data Source</span></span>](lesson-1-2-defining-a-data-source.md)  
  
## <a name="see-also"></a><span data-ttu-id="ea830-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea830-119">See Also</span></span>  
 <span data-ttu-id="ea830-120">[使用 SQL Server Data Tools &#40;SSDT&#41;建立多維度模型](multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="ea830-120">[Creating Multidimensional Models Using SQL Server Data Tools &#40;SSDT&#41;](multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md) </span></span>  
 [<span data-ttu-id="ea830-121">建立 Analysis Services 專案 &#40;SSDT&#41;</span><span class="sxs-lookup"><span data-stu-id="ea830-121">Create an Analysis Services Project &#40;SSDT&#41;</span></span>](multidimensional-models/create-an-analysis-services-project-ssdt.md)  
  
  
