---
title: 在 SQL Server Data Tools 中執行封裝 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, running
- SSIS packages, running
- packages [Integration Services], running
- SQL Server Integration Services packages, running
ms.assetid: 318e6beb-5540-4101-82a5-18c9d47f0570
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 31ca2390ef6bb04b63e4de9978193aed8884da36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687962"
---
# <a name="run-a-package-in-sql-server-data-tools"></a><span data-ttu-id="88e05-102">在 SQL Server Data Tools 中執行套件</span><span class="sxs-lookup"><span data-stu-id="88e05-102">Run a Package in SQL Server Data Tools</span></span>
  <span data-ttu-id="88e05-103">在開發、偵錯和測試封裝期間，您通常會在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中執行封裝。</span><span class="sxs-lookup"><span data-stu-id="88e05-103">You typically run packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] during the development, debugging, and testing of packages.</span></span> <span data-ttu-id="88e05-104">當您從「 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師」執行封裝時，封裝一定會立即執行。</span><span class="sxs-lookup"><span data-stu-id="88e05-104">When you run a package from [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the package always runs immediately.</span></span>  
  
 <span data-ttu-id="88e05-105">封裝執行時， [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師會在 **[進度]** 索引標籤上顯示封裝執行的進度。您可以檢視封裝的開始和結束時間、它的工作和容器，以及封裝中任何失敗之工作或容器的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="88e05-105">While a package is running, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer displays the progress of package execution on the **Progress** tab. You can view the start and finish time of the package and its tasks and containers, in addition to information about any tasks or containers in the package that failed.</span></span> <span data-ttu-id="88e05-106">在完成執行封裝後，執行階段資訊會在 [執行結果]  索引標籤上保持可用。如需詳細資訊，請參閱＜ [Debugging Control Flow](control-flow/control-flow.md)＞主題中的＜進度報表＞一節。</span><span class="sxs-lookup"><span data-stu-id="88e05-106">After the package finishes running, the run-time information remains available on the **Execution Results** tab. For more information, see the section, "Progress Reporting," in the topic, [Debugging Control Flow](control-flow/control-flow.md).</span></span>  
  
 <span data-ttu-id="88e05-107">**設計階段部署**。</span><span class="sxs-lookup"><span data-stu-id="88e05-107">**Design-time deployment**.</span></span> <span data-ttu-id="88e05-108">當您在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中執行封裝時，會建立封裝，然後部署至資料夾。</span><span class="sxs-lookup"><span data-stu-id="88e05-108">When you run a package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], the package is built and then deployed to a folder.</span></span> <span data-ttu-id="88e05-109">在執行封裝之前，您可以指定要用來部署封裝的資料夾。</span><span class="sxs-lookup"><span data-stu-id="88e05-109">Before you run the package, you can specify the folder to which the package is deployed.</span></span> <span data-ttu-id="88e05-110">如果未指定資料夾，預設將會使用 **bin** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="88e05-110">If you do not specify a folder, the **bin** folder is used by default.</span></span> <span data-ttu-id="88e05-111">這種類型的部署稱為設計階段部署。</span><span class="sxs-lookup"><span data-stu-id="88e05-111">This type of deployment is called design-time deployment.</span></span>  
  
### <a name="to-run-a-package-in-sql-server-data-tools"></a><span data-ttu-id="88e05-112">若要在 SQL Server Data Tools 中執行封裝</span><span class="sxs-lookup"><span data-stu-id="88e05-112">To run a package in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="88e05-113">在方案總管中，如果您的方案包含多個專案，請以滑鼠右鍵按一下包含封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案，然後按一下 [設定為啟始物件]  以設定啟始物件。</span><span class="sxs-lookup"><span data-stu-id="88e05-113">In Solution Explorer, if your solution contains multiple projects, right-click the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package, and then click **Set as StartUp Object** to set the startup project.</span></span>  
  
2.  <span data-ttu-id="88e05-114">在方案總管中，如果您的專案包含多個封裝，請以滑鼠右鍵按一下封裝，然後按一下 [設定為啟始物件]  以設定啟始封裝。</span><span class="sxs-lookup"><span data-stu-id="88e05-114">In Solution Explorer, if your project contains multiple packages, right-click a package, and then click **Set as StartUp Object** to set the startup package.</span></span>  
  
3.  <span data-ttu-id="88e05-115">若要執行封裝，請使用下列其中一個程序：</span><span class="sxs-lookup"><span data-stu-id="88e05-115">To run a package, use one of the following procedures:</span></span>  
  
    -   <span data-ttu-id="88e05-116">開啟您要執行的封裝，然後按一下功能表列上的 **[啟動偵錯]** ，或按下 F5。</span><span class="sxs-lookup"><span data-stu-id="88e05-116">Open the package that you want to run and then click **Start Debugging** on the menu bar, or press F5.</span></span> <span data-ttu-id="88e05-117">在封裝完成執行後，按下 Shift+F5 以返回設計模式。</span><span class="sxs-lookup"><span data-stu-id="88e05-117">After the package finishes running, press Shift+F5 to return to design mode.</span></span>  
  
    -   <span data-ttu-id="88e05-118">在方案總管中，以滑鼠右鍵按一下封裝，然後按一下 [執行封裝]  。</span><span class="sxs-lookup"><span data-stu-id="88e05-118">In Solution Explorer, right-click the package, and then click **Execute Package**.</span></span>  
  
### <a name="to-specify-a-different-folder-for-design-time-deployment"></a><span data-ttu-id="88e05-119">若要為設計階段部署指定不同的資料夾</span><span class="sxs-lookup"><span data-stu-id="88e05-119">To specify a different folder for design-time deployment</span></span>  
  
1.  <span data-ttu-id="88e05-120">在方案總管中，以滑鼠右鍵按一下包含您要執行之封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案資料夾，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="88e05-120">In Solution Explorer, right-click the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project folder that contains the package you want to run, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="88e05-121">在 [\<project name> 屬性頁面] 對話方塊中，按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="88e05-121">In the **\<project name> Property Pages** dialog box, click **Build**.</span></span>  
  
3.  <span data-ttu-id="88e05-122">更新 OutputPath 屬性中的值，以指定要用於設計階段部署的資料夾，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="88e05-122">Update the value in the OutputPath property to specify the folder you want to use for design-time deployment, and click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88e05-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88e05-123">See Also</span></span>  
 <span data-ttu-id="88e05-124">[執行專案和套件](packages/run-integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="88e05-124">[Execution of Projects and Packages](packages/run-integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="88e05-125">Integration Services &#40;SSIS&#41; 封裝</span><span class="sxs-lookup"><span data-stu-id="88e05-125">Integration Services &#40;SSIS&#41; Packages</span></span>](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  
