---
title: 建立專案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], creating
ms.assetid: 7897be19-365b-4b06-bcf0-8a669f67a673
author: stevestein
ms.author: sstein
ms.openlocfilehash: 269feee7225ceb09b1c2ed86419b19ec4001c1f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597523"
---
# <a name="create-a-project"></a><span data-ttu-id="d57e5-102">建立專案</span><span class="sxs-lookup"><span data-stu-id="d57e5-102">Create a Project</span></span>
  <span data-ttu-id="d57e5-103">您可以在現有方案內，建立一或多個專案。</span><span class="sxs-lookup"><span data-stu-id="d57e5-103">You can create one or more projects within an existing solution.</span></span>  
  
### <a name="to-create-a-new-project-and-add-it-to-a-solution"></a><span data-ttu-id="d57e5-104">建立新的專案，將它加入方案中</span><span class="sxs-lookup"><span data-stu-id="d57e5-104">To create a new project and add it to a solution</span></span>  
  
1.  <span data-ttu-id="d57e5-105">在 [方案總管] 中，選取方案。</span><span class="sxs-lookup"><span data-stu-id="d57e5-105">In Solution Explorer, select the solution.</span></span>  
  
2.  <span data-ttu-id="d57e5-106">在 [檔案]  功能表上，指向 [新增]  ，再按一下 [新增專案]  。</span><span class="sxs-lookup"><span data-stu-id="d57e5-106">On the **File** menu, point to **Add**, and click **New Project**.</span></span>  
  
3.  <span data-ttu-id="d57e5-107">在 [新增專案]  對話方塊中，按一下某個專案類型。</span><span class="sxs-lookup"><span data-stu-id="d57e5-107">In the  **New Project** dialog box, click a type of project.</span></span>  
  
     <span data-ttu-id="d57e5-108">**範本**</span><span class="sxs-lookup"><span data-stu-id="d57e5-108">**Templates**</span></span>  
     <span data-ttu-id="d57e5-109">在 [範本]  方塊中，請選取一個範本。</span><span class="sxs-lookup"><span data-stu-id="d57e5-109">In the **Templates** box, select a template.</span></span> <span data-ttu-id="d57e5-110">選取的專案範本的簡短描述會出現在 [範本]  方塊以下。</span><span class="sxs-lookup"><span data-stu-id="d57e5-110">A brief description of the selected project template appears beneath the **Templates** box.</span></span>  
  
     <span data-ttu-id="d57e5-111">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d57e5-111">**Name**</span></span>  
     <span data-ttu-id="d57e5-112">請輸入您想要建立的指令碼專案名稱。</span><span class="sxs-lookup"><span data-stu-id="d57e5-112">Enter the name of the script project you want to create.</span></span> <span data-ttu-id="d57e5-113">和專案具有相同名稱的資料夾也會建立於顯示在 [位置]  欄位中的位置。</span><span class="sxs-lookup"><span data-stu-id="d57e5-113">A folder with the same name as the project is also created in the location displayed in the **Location** field.</span></span> <span data-ttu-id="d57e5-114">針對某些專案， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 會建立來源以及其他支援檔案，並將它們加入新專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="d57e5-114">For some projects, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] creates source and other supporting files and adds them to the new project folder.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d57e5-115">針對某些專案類型，[名稱]  文字方塊無法使用，因為指定位置會設定名稱。</span><span class="sxs-lookup"><span data-stu-id="d57e5-115">For some project types, the **Name** text box is unavailable because specifying the location sets the name.</span></span> <span data-ttu-id="d57e5-116">例如，Web 應用程式和 Web 服務位於 Web 伺服器上，並且從該伺服器上指定的虛擬目錄衍生出它們的名稱。</span><span class="sxs-lookup"><span data-stu-id="d57e5-116">For example, Web applications and Web services are located on a Web server and derive their name from the virtual directory specified on that server.</span></span>  
  
     <span data-ttu-id="d57e5-117">名稱不可包含以下字元：</span><span class="sxs-lookup"><span data-stu-id="d57e5-117">Names cannot contain the following characters:</span></span>  
  
    -   <span data-ttu-id="d57e5-118">井字號 (#)</span><span class="sxs-lookup"><span data-stu-id="d57e5-118">Pound (#)</span></span>  
  
    -   <span data-ttu-id="d57e5-119">百分比 (%)</span><span class="sxs-lookup"><span data-stu-id="d57e5-119">Percent (%)</span></span>  
  
    -   <span data-ttu-id="d57e5-120">連字號 (&)</span><span class="sxs-lookup"><span data-stu-id="d57e5-120">Ampersand (&)</span></span>  
  
    -   <span data-ttu-id="d57e5-121">星號 (\*)</span><span class="sxs-lookup"><span data-stu-id="d57e5-121">Asterisk (\*)</span></span>  
  
    -   <span data-ttu-id="d57e5-122">分隔號 (|)</span><span class="sxs-lookup"><span data-stu-id="d57e5-122">Vertical bar (|)</span></span>  
  
    -   <span data-ttu-id="d57e5-123">反斜線 (\\)</span><span class="sxs-lookup"><span data-stu-id="d57e5-123">Backslash (\\)</span></span>  
  
    -   <span data-ttu-id="d57e5-124">冒號 (:)</span><span class="sxs-lookup"><span data-stu-id="d57e5-124">Colon (:)</span></span>  
  
    -   <span data-ttu-id="d57e5-125">引號 (")</span><span class="sxs-lookup"><span data-stu-id="d57e5-125">Quotation mark (")</span></span>  
  
    -   <span data-ttu-id="d57e5-126">小於 (\<)</span><span class="sxs-lookup"><span data-stu-id="d57e5-126">Less than (\<)</span></span>  
  
    -   <span data-ttu-id="d57e5-127">大於 (>)</span><span class="sxs-lookup"><span data-stu-id="d57e5-127">Greater than (>)</span></span>  
  
    -   <span data-ttu-id="d57e5-128">問號 (?)</span><span class="sxs-lookup"><span data-stu-id="d57e5-128">Question mark (?)</span></span>  
  
    -   <span data-ttu-id="d57e5-129">斜線 (/)</span><span class="sxs-lookup"><span data-stu-id="d57e5-129">Forward slash (/)</span></span>  
  
    -   <span data-ttu-id="d57e5-130">開頭或尾端空白 (' ')</span><span class="sxs-lookup"><span data-stu-id="d57e5-130">Leading or trailing spaces (' ')</span></span>  
  
    -   <span data-ttu-id="d57e5-131">保留給 Microsoft Windows 或 MS-DOS 的名稱，例如 ("nul"、"aux"、"con"、"com1"、"lpt1" 等等)</span><span class="sxs-lookup"><span data-stu-id="d57e5-131">Names reserved for Microsoft Windows or MS-DOS, such as ("nul", "aux", "con", "com1", "lpt1", and so on)</span></span>  
  
     <span data-ttu-id="d57e5-132">**位置**</span><span class="sxs-lookup"><span data-stu-id="d57e5-132">**Location**</span></span>  
     <span data-ttu-id="d57e5-133">請輸入您想要建立專案的位置，或從清單中選擇。</span><span class="sxs-lookup"><span data-stu-id="d57e5-133">Enter the location where you want to create your project, or choose one from the list.</span></span>  
  
     <span data-ttu-id="d57e5-134">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="d57e5-134">**Browse**</span></span>  
     <span data-ttu-id="d57e5-135">顯示 [專案位置]  對話方塊，可以讓您導覽至新目錄以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="d57e5-135">Displays the **Project Location** dialog box, allowing you to navigate to a new directory in which to save the project.</span></span>  
  
     <span data-ttu-id="d57e5-136">**方案**</span><span class="sxs-lookup"><span data-stu-id="d57e5-136">**Solution**</span></span>  
     <span data-ttu-id="d57e5-137">選取 [建立新方案]  ，即可在方案總管中建立方案。</span><span class="sxs-lookup"><span data-stu-id="d57e5-137">Select **Create new Solution** to create a solution in Solution Explorer.</span></span> <span data-ttu-id="d57e5-138">選取 [新增至方案]  即可將新專案新增至方案總管中目前開啟的方案。</span><span class="sxs-lookup"><span data-stu-id="d57e5-138">Select **Add to Solution** to add the new project to the solution currently open in Solution Explorer.</span></span>  
  
     <span data-ttu-id="d57e5-139">**建立方案的目錄**</span><span class="sxs-lookup"><span data-stu-id="d57e5-139">**Create directory for Solution**</span></span>  
     <span data-ttu-id="d57e5-140">選取以啟用 [(方案) 名稱]  文字方塊。</span><span class="sxs-lookup"><span data-stu-id="d57e5-140">Select to enable the **(Solution) Name** text box.</span></span> <span data-ttu-id="d57e5-141">此選項會根據您為專案和方案選擇的名稱，來建立新的目錄。</span><span class="sxs-lookup"><span data-stu-id="d57e5-141">This option creates a new directory of the name you choose for your project and solution.</span></span>  
  
     <span data-ttu-id="d57e5-142">**方案名稱**</span><span class="sxs-lookup"><span data-stu-id="d57e5-142">**Solution Name**</span></span>  
     <span data-ttu-id="d57e5-143">輸入您希望在其中建立專案的新方案名稱。</span><span class="sxs-lookup"><span data-stu-id="d57e5-143">Enter the name of the new solution in which you want your project to be created.</span></span> <span data-ttu-id="d57e5-144">依預設，此欄位會使用 [名稱]  欄位中輸入的名稱。</span><span class="sxs-lookup"><span data-stu-id="d57e5-144">By default, this field uses the same name as entered in the **Name** field.</span></span>  
  
     <span data-ttu-id="d57e5-145">**請注意**：若要存取此選項，您必須同時選取 [方案]  中的 [建立新方案]  以及 [建立方案的目錄]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d57e5-145">**Note** To access this option, you must select both the **Create New Solution** in the **Solution** and the **Create directory for Solution** check boxes.</span></span> <span data-ttu-id="d57e5-146">有些專案範本 (例如 Web 應用程式) 不支援此選項。</span><span class="sxs-lookup"><span data-stu-id="d57e5-146">Some project templates do not support this option, such as Web applications.</span></span>  
  
     <span data-ttu-id="d57e5-147">**加入至原始檔控制**</span><span class="sxs-lookup"><span data-stu-id="d57e5-147">**Add to Source Control**</span></span>  
     <span data-ttu-id="d57e5-148">如果選取此核取方塊，當您按一下 [確定]  時，原始檔控制應用程式就會開啟。</span><span class="sxs-lookup"><span data-stu-id="d57e5-148">When this check box is selected, your source control application opens when you click **OK**.</span></span> <span data-ttu-id="d57e5-149">填妥原始檔控制應用程式所需的資訊之後，才能繼續。</span><span class="sxs-lookup"><span data-stu-id="d57e5-149">Complete any information required by your source control application to continue.</span></span> <span data-ttu-id="d57e5-150">您必須有安裝原始檔控制用戶端應用程式，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="d57e5-150">You must have a source control client application installed to use this option.</span></span>  
  
4.  <span data-ttu-id="d57e5-151">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d57e5-151">Click **OK**.</span></span>  
  
 <span data-ttu-id="d57e5-152">您可以設定指令碼專案的名稱，但資料夾名稱由 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 建立，無法變更。</span><span class="sxs-lookup"><span data-stu-id="d57e5-152">You can set a name for the script project, but the folder names are established by [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and cannot be changed.</span></span> <span data-ttu-id="d57e5-153">您可以使用 [新增專案]  對話方塊，為一組常用資料夾設定磁碟和路徑規格。</span><span class="sxs-lookup"><span data-stu-id="d57e5-153">You can configure the drive and path specification for the common set of folders by using the **Add New Project** dialog box.</span></span> <span data-ttu-id="d57e5-154">在方案總管  中，以滑鼠右鍵按一下方案，然後按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="d57e5-154">Right-click the solution icon in **Solution Explorer**, and then click **Add**.</span></span> <span data-ttu-id="d57e5-155">指令碼專案資料夾的預設位置是 C:\Documents and Settings\\<使用者名>  \My Documents\SQL Server Management Studio\Projects\\。</span><span class="sxs-lookup"><span data-stu-id="d57e5-155">The default location for script project folders is: C:\Documents and Settings\\*username*\My Documents\SQL Server Management Studio\Projects\\.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d57e5-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d57e5-156">See Also</span></span>  
 <span data-ttu-id="d57e5-157">[方案總管](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="d57e5-157">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="d57e5-158">[將現有的專案加入至方案](add-an-existing-project-to-a-solution.md) </span><span class="sxs-lookup"><span data-stu-id="d57e5-158">[Add an Existing Project to a Solution](add-an-existing-project-to-a-solution.md) </span></span>  
 <span data-ttu-id="d57e5-159">[將新專案新增至專案](add-new-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="d57e5-159">[Add New Items to a Project](add-new-items-to-a-project.md) </span></span>  
 <span data-ttu-id="d57e5-160">[將現有專案加入至專案](add-existing-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="d57e5-160">[Add Existing Items to a Project](add-existing-items-to-a-project.md) </span></span>  
 <span data-ttu-id="d57e5-161">[變更專案的預設位置](change-the-default-location-for-projects.md) </span><span class="sxs-lookup"><span data-stu-id="d57e5-161">[Change the Default Location for Projects](change-the-default-location-for-projects.md) </span></span>  
 <span data-ttu-id="d57e5-162">[移除或刪除專案或專案](remove-or-delete-an-item-or-project.md) </span><span class="sxs-lookup"><span data-stu-id="d57e5-162">[Remove or Delete an Item or Project](remove-or-delete-an-item-or-project.md) </span></span>  
 [<span data-ttu-id="d57e5-163">刪除方案</span><span class="sxs-lookup"><span data-stu-id="d57e5-163">Delete a Solution</span></span>](delete-a-solution.md)  
  
  
