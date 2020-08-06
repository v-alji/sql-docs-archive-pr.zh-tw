---
title: 步驟 2：建立部署專案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 59990fe2-7036-4e9c-8efc-6ece9e66eda7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ebfce8796f98628c2832c5ab7f4be665c7915d10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596142"
---
# <a name="step-2-creating-the-deployment-project"></a><span data-ttu-id="a9402-102">步驟 2:建立部署專案</span><span class="sxs-lookup"><span data-stu-id="a9402-102">Step 2: Creating the Deployment Project</span></span>
  <span data-ttu-id="a9402-103">在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]中，可部署的單位是 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="a9402-103">In [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the deployable unit is an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="a9402-104">部署封裝之前，必須先建立新的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案，並且將所有封裝以及要隨同封裝一起部署的所有輔助檔案全部加入至該專案中。</span><span class="sxs-lookup"><span data-stu-id="a9402-104">Before you can deploy packages, you must create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project and add all the packages and any ancillary files that you want to deploy with the packages to that project.</span></span>  
  
### <a name="to-create-the-integration-services-project"></a><span data-ttu-id="a9402-105">若要建立 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="a9402-105">To create the Integration Services project</span></span>  
  
1.  <span data-ttu-id="a9402-106">按一下 [開始]  ，依序指向 [所有程式]  和 [Microsoft SQL Server]  ，然後按一下 [SQL Server]、[SQL Server Data Tools]  。</span><span class="sxs-lookup"><span data-stu-id="a9402-106">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL ServerSQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="a9402-107">在 [檔案]  功能表上，指向 [開新檔案]  ，然後按一下 [專案]  建立新的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="a9402-107">On the **File** menu, point to **New**, and then click **Project** to create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
3.  <span data-ttu-id="a9402-108">在 [新增專案] 對話方塊中，選取 [範本] 窗格中的 [Integration Services 專案]。</span><span class="sxs-lookup"><span data-stu-id="a9402-108">In the **New Project** dialog box, select **Integration Services Project** in the **Templates** pane.</span></span>  
  
4.  <span data-ttu-id="a9402-109">在 [名稱]  方塊中，將預設名稱變更為**部署教學課程**。</span><span class="sxs-lookup"><span data-stu-id="a9402-109">In the **Name** box, change the default name to **Deployment Tutorial**.</span></span> <span data-ttu-id="a9402-110">您可以選擇性地清除 **[建立方案的目錄]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a9402-110">Optionally, clear the **Create directory for solution** check box.</span></span>  
  
5.  <span data-ttu-id="a9402-111">接受預設位置，或按一下 [瀏覽]  尋找您要使用的資料夾。</span><span class="sxs-lookup"><span data-stu-id="a9402-111">Accept the default location, or click **Browse** to locate the folder you want to use.</span></span>  
  
6.  <span data-ttu-id="a9402-112">在 [專案位置]  對話方塊中，按一下該資料夾，然後按一下 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="a9402-112">In the **Project Location** dialog box, click the folder, and then click **Open**.</span></span>  
  
7.  <span data-ttu-id="a9402-113">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="a9402-113">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="a9402-114">依預設，會建立名稱為 Package.dtsx 的空白封裝，並將其加入至專案中。</span><span class="sxs-lookup"><span data-stu-id="a9402-114">By default, an empty package, named Package.dtsx, is created and added to your project.</span></span> <span data-ttu-id="a9402-115">但是，您並不會使用此封裝，而是將現有的封裝加入至專案中。</span><span class="sxs-lookup"><span data-stu-id="a9402-115">However, you will not use this package; instead, you will add existing packages to the project.</span></span> <span data-ttu-id="a9402-116">由於專案中的所有封裝都會包含在部署中，因此應該刪除 Package.dtsx。</span><span class="sxs-lookup"><span data-stu-id="a9402-116">Because all the packages in a project will be included in the deployment, you should delete Package.dtsx.</span></span> <span data-ttu-id="a9402-117">若要刪除，請以滑鼠右鍵按一下這個檔案，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="a9402-117">To delete it, right-click it, and then click **Delete**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a9402-118">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="a9402-118">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a9402-119">步驟 3：新增套件和其他檔案</span><span class="sxs-lookup"><span data-stu-id="a9402-119">Step 3: Adding Packages and Other Files</span></span>](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
<span data-ttu-id="a9402-120">![Integration Services 圖示 (小型) ](media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="a9402-120">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="a9402-121">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="a9402-121">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="a9402-122">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="a9402-122">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="a9402-123">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="a9402-123">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9402-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9402-124">See Also</span></span>  
 [<span data-ttu-id="a9402-125">Integration Services &#40;SSIS&#41; 專案</span><span class="sxs-lookup"><span data-stu-id="a9402-125">Integration Services &#40;SSIS&#41; Projects</span></span>](integration-services-ssis-projects-and-solutions.md)  
  
  
