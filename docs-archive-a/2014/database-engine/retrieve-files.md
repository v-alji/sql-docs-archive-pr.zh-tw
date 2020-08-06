---
title: 取出檔案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- version control services [SQL Server], file retrieval
- file retrieval [SQL Server]
- retrieving files
ms.assetid: 37b74426-e262-43b2-a81f-79b1fd1a36ec
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ebced9ea69f304344893289140687cd6d511e923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599159"
---
# <a name="retrieve-files"></a><span data-ttu-id="c9274-102">擷取檔案</span><span class="sxs-lookup"><span data-stu-id="c9274-102">Retrieve Files</span></span>
  <span data-ttu-id="c9274-103">開啟原始檔控制專案之後，您可以利用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]，將原始檔控制存放區中的專案檔本機複本擷取到專案所在的本機目錄中。</span><span class="sxs-lookup"><span data-stu-id="c9274-103">After you have opened a source-controlled project, you can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to retrieve local copies of project files from the source control store to the local directory in which the project resides.</span></span>  
  
 <span data-ttu-id="c9274-104">您可以依照下列方式，利用整合式原始檔控制來擷取檔案：</span><span class="sxs-lookup"><span data-stu-id="c9274-104">You can use integrated source control to retrieve files in the following ways:</span></span>  
  
-   <span data-ttu-id="c9274-105">**取得 (遞迴) 命令的最新版本**</span><span class="sxs-lookup"><span data-stu-id="c9274-105">**Get Latest Version (Recursive)** command</span></span>  
  
     <span data-ttu-id="c9274-106">擷取所選檔案最新的簽入版本。</span><span class="sxs-lookup"><span data-stu-id="c9274-106">Retrieves the latest checked in version of the selected files.</span></span> <span data-ttu-id="c9274-107">如果選取某個方案或專案，這個命令會擷取所有方案或專案檔的最新版本。</span><span class="sxs-lookup"><span data-stu-id="c9274-107">If a solution or project is selected, this command retrieves the latest version of all solution and project files.</span></span>  
  
-   <span data-ttu-id="c9274-108">**Get**命令</span><span class="sxs-lookup"><span data-stu-id="c9274-108">**Get** command</span></span>  
  
     <span data-ttu-id="c9274-109">顯示 [**取得**] 對話方塊，您可以使用此對話方塊來抓取所選檔案的最新版本，或是抓取所選方案或專案中的檔案子集。</span><span class="sxs-lookup"><span data-stu-id="c9274-109">Displays the **Get** dialog box, which you can use to retrieve the latest version of a selected file, or to retrieve a subset of the files in the selected solution or project.</span></span>  
  
### <a name="to-retrieve-the-latest-version-of-all-the-files-in-a-project"></a><span data-ttu-id="c9274-110">擷取專案中所有檔案的最新版本</span><span class="sxs-lookup"><span data-stu-id="c9274-110">To retrieve the latest version of all the files in a project</span></span>  
  
1.  <span data-ttu-id="c9274-111">在 [方案總管] 中選取專案。</span><span class="sxs-lookup"><span data-stu-id="c9274-111">In Solution Explorer, select the project.</span></span>  
  
2.  <span data-ttu-id="c9274-112">**在 [檔案**] 功能表上，指向 [原始檔**控制**]，然後按一下 [\*\*取得最新的版本 (遞迴) \*\*]。</span><span class="sxs-lookup"><span data-stu-id="c9274-112">On the **File** menu, point to **Source Control**, and then click **Get Latest Version (Recursive)**.</span></span>  
  
 <span data-ttu-id="c9274-113">專案中檔案的最新版本會擷取到本機磁碟的專案位置中。</span><span class="sxs-lookup"><span data-stu-id="c9274-113">The most recent versions of the files in the project are retrieved to the project location on your local disk.</span></span>  
  
#### <a name="to-retrieve-only-certain-files-in-a-project"></a><span data-ttu-id="c9274-114">只擷取專案中的某些檔案</span><span class="sxs-lookup"><span data-stu-id="c9274-114">To retrieve only certain files in a project</span></span>  
  
1.  <span data-ttu-id="c9274-115">在 [方案總管] 中，選取您要擷取的項目。</span><span class="sxs-lookup"><span data-stu-id="c9274-115">In Solution Explorer, select the item you want to retrieve.</span></span>  
  
2.  <span data-ttu-id="c9274-116">**在 [檔案**] 功能表上，指向 [原始檔**控制**]，然後按一下 [**取得**]。</span><span class="sxs-lookup"><span data-stu-id="c9274-116">On the **File** menu, point to **Source Control**, and then click **Get**.</span></span>  
  
3.  <span data-ttu-id="c9274-117">在 [**取得**] 對話方塊中，按一下 **[確定**]。</span><span class="sxs-lookup"><span data-stu-id="c9274-117">In the **Get** dialog box, click **OK**.</span></span> <span data-ttu-id="c9274-118">另外，如果您在 [方案總管] 中選取方案或專案，請清除您不要擷取的項目旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c9274-118">Alternatively, if you selected a solution or project in Solution Explorer, clear the check boxes that appear next to the items you do not want to retrieve.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9274-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9274-119">See Also</span></span>  
 <span data-ttu-id="c9274-120">[[取得] 對話方塊 &#40;原始檔控制&#41;](../../2014/database-engine/get-dialog-box-source-control.md) </span><span class="sxs-lookup"><span data-stu-id="c9274-120">[Get Dialog Box &#40;Source Control&#41;](../../2014/database-engine/get-dialog-box-source-control.md) </span></span>  
 <span data-ttu-id="c9274-121">[設定和抓取版本資訊](../../2014/database-engine/set-and-retrieve-version-information.md) </span><span class="sxs-lookup"><span data-stu-id="c9274-121">[Set and Retrieve Version Information](../../2014/database-engine/set-and-retrieve-version-information.md) </span></span>  
 <span data-ttu-id="c9274-122">[視圖專案歷程記錄](../../2014/database-engine/view-project-history.md) </span><span class="sxs-lookup"><span data-stu-id="c9274-122">[View Project History](../../2014/database-engine/view-project-history.md) </span></span>  
 [<span data-ttu-id="c9274-123">檢視檔案狀態</span><span class="sxs-lookup"><span data-stu-id="c9274-123">View File Status</span></span>](../../2014/database-engine/view-file-status.md)  
  
  
