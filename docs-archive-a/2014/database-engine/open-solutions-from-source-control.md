---
title: 從原始檔控制開啟方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- opening solutions
- solutions [SQL Server Management Studio], opening
ms.assetid: a96a1f0d-0183-4587-a3b0-4598309cbdd2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 808a4851bcc1f51690b2ba924a859bcccf9a6adb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599651"
---
# <a name="open-solutions-from-source-control"></a><span data-ttu-id="4f8a7-102">從原始檔控制開啟方案</span><span class="sxs-lookup"><span data-stu-id="4f8a7-102">Open Solutions from Source Control</span></span>
  <span data-ttu-id="4f8a7-103">您可以利用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]，直接從原始檔控制中開啟方案。</span><span class="sxs-lookup"><span data-stu-id="4f8a7-103">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to open solutions directly from source control.</span></span> <span data-ttu-id="4f8a7-104">當您執行這個動作時，Studio 環境會在您指定的位置上，建立方案檔最新版本的副本。</span><span class="sxs-lookup"><span data-stu-id="4f8a7-104">When you do this, the Studio environment creates a copy of the latest version of the solution files at the location you specify.</span></span>  
  
 <span data-ttu-id="4f8a7-105">如果方案的本機副本不在本機磁碟中，您必須先從原始檔控制中開啟專案，之後，才能利用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 來簽出方案或擷取方案檔。</span><span class="sxs-lookup"><span data-stu-id="4f8a7-105">If a local copy of the solution does not exist on your local disk, you must open the project from source control before you can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to check out the solution or retrieve solution files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4f8a7-106">如果您已有從原始檔控制開啟之方案的本機副本，系統會提示您覆寫本機副本。</span><span class="sxs-lookup"><span data-stu-id="4f8a7-106">If you already have a local copy of the solution you are opening from source control, you are prompted to overwrite the local copy.</span></span>  
  
### <a name="to-open-a-solution-from-source-control"></a><span data-ttu-id="4f8a7-107">從原始檔控制中開啟方案</span><span class="sxs-lookup"><span data-stu-id="4f8a7-107">To open a solution from source control</span></span>  
  
1.  <span data-ttu-id="4f8a7-108">**在 [檔案**] 功能表上，指向 [原始檔**控制**]，然後按一下 [**從原始檔控制開啟**]。</span><span class="sxs-lookup"><span data-stu-id="4f8a7-108">On the **File** menu, point to **Source Control**, and click **Open From Source Control**.</span></span>  
  
2.  <span data-ttu-id="4f8a7-109">如果出現提示，請登入 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe。</span><span class="sxs-lookup"><span data-stu-id="4f8a7-109">If prompted, log on to [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe.</span></span>  
  
3.  <span data-ttu-id="4f8a7-110">在 [**從 SourceSafe 建立本機專案**] 對話方塊中，選取包含您想要開啟之方案的資料夾，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="4f8a7-110">In the **Create local project from SourceSafe** dialog box, select the folder that contains the solution you want to open, and click **OK**.</span></span>  
  
4.  <span data-ttu-id="4f8a7-111">如果解決方案的工作資料夾已經存在於您的本機磁片磁碟機上，[在**資料夾中建立新專案**] 方塊會變更，以識別本機目錄。</span><span class="sxs-lookup"><span data-stu-id="4f8a7-111">If a working folder for the solution already exists on your local disk drive, the **Create a new project in the folder** box changes to identify the local directory.</span></span> <span data-ttu-id="4f8a7-112">如果沒有方案的工作目錄，您可以輸入或瀏覽到應該在其中開啟方案的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="4f8a7-112">If no working folder for the solution exists, you can type or browse to the local directory in which the solution should be opened.</span></span>  
  
5.  <span data-ttu-id="4f8a7-113">在 [**開啟方案**] 對話方塊中，選取方案檔，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="4f8a7-113">In the **Open Solution** dialog box, select the solution file, and click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f8a7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f8a7-114">See Also</span></span>  
 [<span data-ttu-id="4f8a7-115">從原始檔控制開啟專案</span><span class="sxs-lookup"><span data-stu-id="4f8a7-115">Open Projects from Source Control</span></span>](../../2014/database-engine/open-projects-from-source-control.md)  
  
  
