---
title: 視圖專案歷程記錄 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing project history
- version control services [SQL Server], project history
- projects [SQL Server Management Studio], historical information
- historical information [SQL Server], projects
ms.assetid: be0ea2ac-4a35-429c-9c9e-4001ea9035a4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 85028141050e19e6ed6394a5bb17709ac8f906ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606436"
---
# <a name="view-project-history"></a><span data-ttu-id="5d02d-102">檢視專案記錄</span><span class="sxs-lookup"><span data-stu-id="5d02d-102">View Project History</span></span>
  <span data-ttu-id="5d02d-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe (VSS) 專案記錄包括一份在每個專案檔上所採用的完整動作清單，其中包括建立、新增、刪除和復原檔案。</span><span class="sxs-lookup"><span data-stu-id="5d02d-103">The history of a [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe (VSS) project includes a list of all the actions taken on each of the project files, including file creation, addition, deletion, and recovery.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5d02d-104">Visual SourceSafe 專案通常稱為原始檔控制伺服器資料夾，它是原始檔控制檔案儲存在伺服器中的伺服器版本的位置。</span><span class="sxs-lookup"><span data-stu-id="5d02d-104">A Visual SourceSafe project is more commonly referred to as the source control server folder, the location where the server version of a source-controlled file is stored on the server.</span></span>  
  
 <span data-ttu-id="5d02d-105">您可以利用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 來檢查目前載入的方案所屬之 Visual SourceSafe 專案記錄。</span><span class="sxs-lookup"><span data-stu-id="5d02d-105">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to examine the history of the Visual SourceSafe project to which the currently loaded solution belongs.</span></span> <span data-ttu-id="5d02d-106">您可以根據專案記錄中所顯示的資訊來擷取檔案版本的本機副本、還原已刪除的版本，或在專案之間共用檔案版本。</span><span class="sxs-lookup"><span data-stu-id="5d02d-106">Based on the information displayed as part of the history of a project, you can retrieve local copies of file versions, restore deleted versions, or share a file version between projects.</span></span>  
  
### <a name="to-view-the-history-of-a-vss-project"></a><span data-ttu-id="5d02d-107">檢視 VSS 專案記錄</span><span class="sxs-lookup"><span data-stu-id="5d02d-107">To view the history of a VSS project</span></span>  
  
1.  <span data-ttu-id="5d02d-108">在 [方案總管] 中選取專案。</span><span class="sxs-lookup"><span data-stu-id="5d02d-108">In Solution Explorer, select the project.</span></span>  
  
2.  <span data-ttu-id="5d02d-109">**在 [檔案**] 功能表上，指向 [原始檔**控制**]，然後按一下 [ **View 歷程記錄**]。</span><span class="sxs-lookup"><span data-stu-id="5d02d-109">On the **File** menu, point to **Source Control** and click **View History**.</span></span>  
  
3.  <span data-ttu-id="5d02d-110">在 [歷程**記錄** \<Project> ] 對話方塊中，執行下列任一動作：</span><span class="sxs-lookup"><span data-stu-id="5d02d-110">In the **History of** \<Project> dialog box, perform any of the following actions:</span></span>  
  
    -   <span data-ttu-id="5d02d-111">檢視原始檔控制系統的所選檔案副本。</span><span class="sxs-lookup"><span data-stu-id="5d02d-111">View the source control system's copy of a selected file.</span></span>  
  
    -   <span data-ttu-id="5d02d-112">檢視所選檔案的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5d02d-112">View detailed information about a selected file.</span></span>  
  
    -   <span data-ttu-id="5d02d-113">將所選檔案擷取到本機磁碟中。</span><span class="sxs-lookup"><span data-stu-id="5d02d-113">Retrieve a selected file to your local disk.</span></span>  
  
    -   <span data-ttu-id="5d02d-114">簽出所選的檔案。</span><span class="sxs-lookup"><span data-stu-id="5d02d-114">Check out a selected file.</span></span>  
  
    -   <span data-ttu-id="5d02d-115">在兩個原始檔控制專案之間共用所選的檔案。</span><span class="sxs-lookup"><span data-stu-id="5d02d-115">Share a selected file between two source control projects.</span></span>  
  
    -   <span data-ttu-id="5d02d-116">將記錄報表匯出到印表機、檔案或 [剪貼簿] 中。</span><span class="sxs-lookup"><span data-stu-id="5d02d-116">Export the history report to a printer, a file, or the Clipboard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d02d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d02d-117">See Also</span></span>  
 <span data-ttu-id="5d02d-118">[設定和抓取版本資訊](../../2014/database-engine/set-and-retrieve-version-information.md) </span><span class="sxs-lookup"><span data-stu-id="5d02d-118">[Set and Retrieve Version Information](../../2014/database-engine/set-and-retrieve-version-information.md) </span></span>  
 <span data-ttu-id="5d02d-119">[View File Status](../../2014/database-engine/view-file-status.md) </span><span class="sxs-lookup"><span data-stu-id="5d02d-119">[View File Status](../../2014/database-engine/view-file-status.md) </span></span>  
 <span data-ttu-id="5d02d-120">[取出檔案](../../2014/database-engine/retrieve-files.md) </span><span class="sxs-lookup"><span data-stu-id="5d02d-120">[Retrieve Files](../../2014/database-engine/retrieve-files.md) </span></span>  
 [<span data-ttu-id="5d02d-121">比較檔案</span><span class="sxs-lookup"><span data-stu-id="5d02d-121">Compare Files</span></span>](../../2014/database-engine/compare-files.md)  
  
  
