---
title: 建立新的 Integration Services 專案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Integration Services], creating
- Integration Services projects, creating
- SQL Server Integration Services projects, creating
- SSIS projects, creating
ms.assetid: 1e23f259-0401-4333-ab4f-89809aae63b1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f62d3ac2d33bb51a0ccc3b77d9f8b5ec0f52b345
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594622"
---
# <a name="create-a-new-integration-services-project"></a><span data-ttu-id="fd896-102">建立新的 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="fd896-102">Create a New Integration Services Project</span></span>
  <span data-ttu-id="fd896-103">此程序會建立新的專案和新的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 方案。</span><span class="sxs-lookup"><span data-stu-id="fd896-103">This procedure creates a new project and a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] solution.</span></span>  
  
### <a name="to-create-a-new-integration-services-project"></a><span data-ttu-id="fd896-104">若要建立新的 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="fd896-104">To create a new Integration Services project</span></span>  
  
1.  <span data-ttu-id="fd896-105">開啟 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fd896-105">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="fd896-106">在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。</span><span class="sxs-lookup"><span data-stu-id="fd896-106">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="fd896-107">在 **[新增專案]** 對話方塊的 **[範本]** 窗格中，選取 **[Integration Services 專案]** 範本。</span><span class="sxs-lookup"><span data-stu-id="fd896-107">In the **New Project** dialog box, in the **Templates** pane, select the **Integration Services Project** template.</span></span>  
  
     <span data-ttu-id="fd896-108">**[Integration Services 專案]** 範本會建立一個包含單一、空白封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="fd896-108">The **Integration Services Project** template creates an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains a single, empty package.</span></span>  
  
4.  <span data-ttu-id="fd896-109">(選擇性) 編輯專案名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="fd896-109">(Optional) Edit the project name and the location.</span></span>  
  
     <span data-ttu-id="fd896-110">方案名稱會自動更新為符合專案名稱。</span><span class="sxs-lookup"><span data-stu-id="fd896-110">The solution name is automatically updated to match the project name.</span></span>  
  
5.  <span data-ttu-id="fd896-111">若要為方案檔建立個別的資料夾，請選取 **[為方案建立目錄]**。</span><span class="sxs-lookup"><span data-stu-id="fd896-111">To create a separate folder for the solution file, select **Create directory for solution**.</span></span> <span data-ttu-id="fd896-112">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="fd896-112">This is the default option.</span></span>  
  
6.  <span data-ttu-id="fd896-113">如果電腦上安裝了原始檔控制軟體，請選取 **[加入至原始檔控制]**  以將專案與原始檔控制相關聯。</span><span class="sxs-lookup"><span data-stu-id="fd896-113">If source control software is installed on the computer, select **Add to source control**  to associate the project with source control.</span></span>  
  
7.  <span data-ttu-id="fd896-114">如果原始檔控制軟體是 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe，則 **[Visual SourceSafe 登入]** 對話方塊會開啟。</span><span class="sxs-lookup"><span data-stu-id="fd896-114">If the source control software is [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, the **Visual SourceSafe Login** dialog box opens.</span></span> <span data-ttu-id="fd896-115">請在 **[Visual SourceSafe 登入]** 中，提供使用者名稱、密碼，以及 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="fd896-115">In **Visual SourceSafe Login**, provide a user name, a password, and the name of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe database.</span></span> <span data-ttu-id="fd896-116">按一下 **[瀏覽]** 找出資料庫。</span><span class="sxs-lookup"><span data-stu-id="fd896-116">Click **Browse** to locate the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fd896-117">若要檢視和變更選取的原始檔控制外掛程式，以及設定原始檔控制環境，請按一下 [工具]\*\*\*\* 功能表上的 [選項]\*\*\*\*，然後展開 [原始檔控制]\*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="fd896-117">To view and change the selected source control plug-in and to configure the source control environment, click **Options** on the **Tools** menu, and then expand the **Source Control** node.</span></span>  
  
8.  <span data-ttu-id="fd896-118">按一下 **[確定]** ，將方案加入方案**探索**r 中，並將專案新增至方案。</span><span class="sxs-lookup"><span data-stu-id="fd896-118">Click **OK** to add the solution to **Solution Explore**r and add the project to the solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd896-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd896-119">See Also</span></span>  
 <span data-ttu-id="fd896-120">[Integration Services &#40;SSIS&#41; 專案](integration-services-ssis-projects-and-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="fd896-120">[Integration Services &#40;SSIS&#41; Projects](integration-services-ssis-projects-and-solutions.md) </span></span>  
 [<span data-ttu-id="fd896-121">在方案中加入或移除 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="fd896-121">Add or Remove an Integration Services Project in a Solution</span></span>](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)  
  
  
