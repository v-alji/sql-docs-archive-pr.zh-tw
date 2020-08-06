---
title: 比較檔案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- versions [SQL Server], file comparisons
- comparing files
- file comparisons [SQL Server]
ms.assetid: 728811c4-5d7a-4420-abce-f56c5a0994d2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f29bf7098f0c73d0b672e20b973b1347349b31f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597359"
---
# <a name="compare-files"></a><span data-ttu-id="22761-102">比較檔案</span><span class="sxs-lookup"><span data-stu-id="22761-102">Compare Files</span></span>
  <span data-ttu-id="22761-103">您可以比較檔案來判斷檔案如何進入目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="22761-103">You can compare files to determine how a file has progressed to its present state.</span></span> <span data-ttu-id="22761-104">例如，如果您在簽入特定來源檔案版本之後，在程式碼專案的某項建置中偵測到錯誤，您可以比較目前的檔案版本和先前的版本。</span><span class="sxs-lookup"><span data-stu-id="22761-104">For example, if you detect a defect in a build of your code project after a particular source file version is checked in, you can compare the current file version to a previous one.</span></span> <span data-ttu-id="22761-105">這可以協助您找出引起錯誤的程式碼。</span><span class="sxs-lookup"><span data-stu-id="22761-105">This helps you to pinpoint the code that introduced the defect.</span></span>  
  
 <span data-ttu-id="22761-106">您可以利用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 來比較專案或檔案的本機副本與原始檔控制所儲存的版本，或比較兩個本機檔案。</span><span class="sxs-lookup"><span data-stu-id="22761-106">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to compare a local copy of a project or file to the version stored in source control, or to compare two local files.</span></span> <span data-ttu-id="22761-107">此外，使用 [歷程**記錄**] 命令，您可以比較任何兩個原始檔控制版本。</span><span class="sxs-lookup"><span data-stu-id="22761-107">Also, using the **History** command, you can compare any two source-controlled versions.</span></span>  
  
### <a name="to-compare-files"></a><span data-ttu-id="22761-108">比較檔案</span><span class="sxs-lookup"><span data-stu-id="22761-108">To compare files</span></span>  
  
1.  <span data-ttu-id="22761-109">在 [方案總管] 中，選取一個專案或某個專案檔。</span><span class="sxs-lookup"><span data-stu-id="22761-109">In Solution Explorer, select either a project or one of the project files.</span></span>  
  
2.  <span data-ttu-id="22761-110">**在 [檔案**] 功能表上，指向 [原始檔**控制**]，然後按一下 [**比較**]。</span><span class="sxs-lookup"><span data-stu-id="22761-110">On the **File** menu, point to **Source Control**, and click **Compare**.</span></span>  
  
3.  <span data-ttu-id="22761-111">在 [**差異選項**] 對話方塊中，選取適當的選項，然後按一下 [**報表**]。</span><span class="sxs-lookup"><span data-stu-id="22761-111">In the **Difference Options** dialog box, select the appropriate options, and then click **Report**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22761-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22761-112">See Also</span></span>  
 <span data-ttu-id="22761-113">[設定和抓取版本資訊](../../2014/database-engine/set-and-retrieve-version-information.md) </span><span class="sxs-lookup"><span data-stu-id="22761-113">[Set and Retrieve Version Information](../../2014/database-engine/set-and-retrieve-version-information.md) </span></span>  
 <span data-ttu-id="22761-114">[View File 歷程記錄](../../2014/database-engine/view-file-history.md) </span><span class="sxs-lookup"><span data-stu-id="22761-114">[View File History](../../2014/database-engine/view-file-history.md) </span></span>  
 <span data-ttu-id="22761-115">[視圖專案歷程記錄](../../2014/database-engine/view-project-history.md) </span><span class="sxs-lookup"><span data-stu-id="22761-115">[View Project History](../../2014/database-engine/view-project-history.md) </span></span>  
 <span data-ttu-id="22761-116">[View File Status](../../2014/database-engine/view-file-status.md) </span><span class="sxs-lookup"><span data-stu-id="22761-116">[View File Status](../../2014/database-engine/view-file-status.md) </span></span>  
 [<span data-ttu-id="22761-117">擷取檔案</span><span class="sxs-lookup"><span data-stu-id="22761-117">Retrieve Files</span></span>](../../2014/database-engine/retrieve-files.md)  
  
  
