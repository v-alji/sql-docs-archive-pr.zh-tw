---
title: 將現有的項目加入至專案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 084b3879-e96b-45a7-b421-6a4b0db2b92b
author: stevestein
ms.author: sstein
ms.openlocfilehash: cffa683bfa2a2c81c059d887231531f03d5c892b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606532"
---
# <a name="add-existing-items-to-a-project"></a><span data-ttu-id="7b8ae-102">將現有的項目加入至專案</span><span class="sxs-lookup"><span data-stu-id="7b8ae-102">Add Existing Items to a Project</span></span>
  <span data-ttu-id="7b8ae-103">請將新的項目加入專案中，來延伸應用程式功能。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-103">Add new items to a project to extend application functionality.</span></span> <span data-ttu-id="7b8ae-104">現有項目可以是查詢或其他檔案。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-104">An existing item can be a query or a miscellaneous file.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="7b8ae-105">有兩種專案類型： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指令碼專案和 Analysis Services 指令碼專案。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-105">has two project types: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Script Project, and Analysis Services Script Project.</span></span> <span data-ttu-id="7b8ae-106">專案類型決定了可以加入專案中的查詢檔。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-106">The project type determines the query files that you can add to the project.</span></span> <span data-ttu-id="7b8ae-107">例如，您可以將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢 (副檔名是 .sql 的檔案) 加入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指令碼專案中，但您不能將它加入 Analysis Services 指令碼專案中。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-107">For example, you can add a [!INCLUDE[tsql](../../includes/tsql-md.md)] query (a file with a .sql extension) to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Script project, but you cannot add it to an Analysis Services Script Project.</span></span> <span data-ttu-id="7b8ae-108">若要將其他副檔名與專案類型產生關聯，請參閱[使副檔名與程式碼編輯器產生關聯](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-108">To associate additional file extensions to a project type, see [Associate File Extensions to a Code Editor](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md).</span></span>  
  
### <a name="to-add-an-existing-query-or-a-miscellaneous-file-to-a-project"></a><span data-ttu-id="7b8ae-109">將現有的查詢或其他檔案加入專案中</span><span class="sxs-lookup"><span data-stu-id="7b8ae-109">To add an existing query or a miscellaneous file to a project</span></span>  
  
1.  <span data-ttu-id="7b8ae-110">在 [方案總管] 中，選取一個目標專案。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-110">In Solution Explorer, select a target project.</span></span>  
  
2.  <span data-ttu-id="7b8ae-111">在 [專案]  功能表上，按一下 [新增現有項目]  。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-111">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
     <span data-ttu-id="7b8ae-112">**Look in**</span><span class="sxs-lookup"><span data-stu-id="7b8ae-112">**Look in**</span></span>  
     <span data-ttu-id="7b8ae-113">從此清單中找出要加入專案的檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-113">Locate the files or folders to add to your project from this list.</span></span> <span data-ttu-id="7b8ae-114">針對 XML Web 服務和 ASP.NET Web 應用程式，這些檔案是位於 Web 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-114">For XML Web services and ASP.NET Web applications, the files are located on the Web server.</span></span>  
  
     <span data-ttu-id="7b8ae-115">**桌面**</span><span class="sxs-lookup"><span data-stu-id="7b8ae-115">**Desktop**</span></span>  
     <span data-ttu-id="7b8ae-116">顯示位於桌面上的檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-116">Displays the files and folders located on the desktop.</span></span>  
  
     <span data-ttu-id="7b8ae-117">**我的專案**</span><span class="sxs-lookup"><span data-stu-id="7b8ae-117">**My Projects**</span></span>  
     <span data-ttu-id="7b8ae-118">顯示位於預設 [我的專案]  位置處的檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-118">Displays the files and folders at the default **My Projects** location.</span></span>  
  
     <span data-ttu-id="7b8ae-119">**我的電腦**</span><span class="sxs-lookup"><span data-stu-id="7b8ae-119">**My Computer**</span></span>  
     <span data-ttu-id="7b8ae-120">顯示 [我的電腦]  資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-120">Displays the contents of your **My Computer** folder.</span></span>  
  
     <span data-ttu-id="7b8ae-121">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="7b8ae-121">**File name**</span></span>  
     <span data-ttu-id="7b8ae-122">使用此選項來篩選所顯示的檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-122">Use this option to filter the files and folders that are displayed.</span></span> <span data-ttu-id="7b8ae-123">輸入要篩選的完整或部份檔案名稱；使用星號 (`*`) 作為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-123">Enter the full or partial file name on which to filter; use an asterisk (`*`) as a wildcard.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7b8ae-124">在 [檔案名稱]  方塊中輸入 URL 或網路路徑，導覽至 Web 和網路位置。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-124">Navigate to Web and network locations by entering the URL or network path in the **File name** box.</span></span> <span data-ttu-id="7b8ae-125">例如， **http://mywebsite** 會顯示在 mywebsite Web 位置上的可用檔案，而 **\\\myserver\myshare** 則會顯示在 myserver 的 myshare 位置上的可用檔案。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-125">For example, **http://mywebsite** displays the files available at the mywebsite Web location, and **\\\myserver\myshare** displays the files available at the myshare location on myserver.</span></span>  
  
     <span data-ttu-id="7b8ae-126">**檔案類型**</span><span class="sxs-lookup"><span data-stu-id="7b8ae-126">**Files of type**</span></span>  
     <span data-ttu-id="7b8ae-127">使用此選項根據副檔名篩選檔案。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-127">Use this option to filter files based on file extension.</span></span> <span data-ttu-id="7b8ae-128">每個產品都會列出最常用之檔案類型的預設篩選。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-128">Each product lists default filters of the most common file types.</span></span>  
  
     <span data-ttu-id="7b8ae-129">**加入**</span><span class="sxs-lookup"><span data-stu-id="7b8ae-129">**Add**</span></span>  
     <span data-ttu-id="7b8ae-130">使用此下拉式按鈕將項目加入專案中並在預設編輯器中開啟項目。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-130">Use this drop-down button to add the item to the project and open the item in its default editor.</span></span>  
  
    -   <span data-ttu-id="7b8ae-131">**加入**</span><span class="sxs-lookup"><span data-stu-id="7b8ae-131">**Add**</span></span>  
  
         <span data-ttu-id="7b8ae-132">將現有的項目複製到磁碟上的專案資料夾，並將項目加入方案總管中所選取的專案之下。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-132">Copies the existing item to your project folder on disk and adds the item under the selected project in Solution Explorer.</span></span> <span data-ttu-id="7b8ae-133">對項目所做的任何變更不會反映到位於原始位置的項目中。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-133">Any changes made to the item are not reflected in the item at the original location.</span></span> <span data-ttu-id="7b8ae-134">這是此檔案類型的預設編輯器。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-134">This is the default editor for the file type.</span></span>  
  
    -   <span data-ttu-id="7b8ae-135">**加入做為連結**</span><span class="sxs-lookup"><span data-stu-id="7b8ae-135">**Add As Link**</span></span>  
  
         <span data-ttu-id="7b8ae-136">將選取的檔案加入專案中並以該檔案類型的預設編輯器開啟它。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-136">Adds the selected file to the project and opens it with the default editor for the file type.</span></span> <span data-ttu-id="7b8ae-137">此選項會開啟原始選取的檔案，但不會將檔案複製到專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-137">This option opens the originally selected file and does not copy the file to the project folder.</span></span>  
  
3.  <span data-ttu-id="7b8ae-138">如果您要加入查詢檔，連接對話方塊會提示您指定查詢的連接。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-138">If you are adding query files, the connection dialog will prompt you to specify a connection for the query.</span></span> <span data-ttu-id="7b8ae-139">如果不要將連接關聯於這項查詢，您可以在連接對話中，按一下 [取消]  。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-139">You can click **Cancel** on the connection dialog if you do not want to associate a connection to the query.</span></span>  
  
4.  <span data-ttu-id="7b8ae-140">此時檔案會加入專案的 [查詢]  或 [其他檔案]  資料夾中。</span><span class="sxs-lookup"><span data-stu-id="7b8ae-140">The file will be added to the **Queries** or **Miscellaneous Files** folder of the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b8ae-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b8ae-141">See Also</span></span>  
 <span data-ttu-id="7b8ae-142">[方案總管](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="7b8ae-142">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="7b8ae-143">[將新專案新增至專案](add-new-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="7b8ae-143">[Add New Items to a Project](add-new-items-to-a-project.md) </span></span>  
 [<span data-ttu-id="7b8ae-144">移除或刪除項目或專案</span><span class="sxs-lookup"><span data-stu-id="7b8ae-144">Remove or Delete an Item or Project</span></span>](remove-or-delete-an-item-or-project.md)  
  
  
