---
title: 從原始檔控制開啟專案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], opening
- opening projects
ms.assetid: 942f93a3-e264-4ec4-ba72-a28e0509a527
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 944b121516e3782e35e213e165405b0ecceb7456
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599653"
---
# <a name="open-projects-from-source-control"></a><span data-ttu-id="30c23-102">從原始檔控制開啟專案</span><span class="sxs-lookup"><span data-stu-id="30c23-102">Open Projects from Source Control</span></span>
  <span data-ttu-id="30c23-103">您可以利用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]，直接從原始檔控制中開啟專案。</span><span class="sxs-lookup"><span data-stu-id="30c23-103">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to open projects directly from source control.</span></span> <span data-ttu-id="30c23-104">當您執行這個動作時，[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 會擷取專案的最新版本，將它複製到本機磁碟中。</span><span class="sxs-lookup"><span data-stu-id="30c23-104">When you do this, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] retrieves the latest version of the project and copies it to your local disk.</span></span> <span data-ttu-id="30c23-105">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 環境也會自動建立一項專案的方案。</span><span class="sxs-lookup"><span data-stu-id="30c23-105">The [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment also creates a solution for the project automatically.</span></span>  
  
 <span data-ttu-id="30c23-106">從原始檔控制中開啟專案之後，您便可以簽出和修改專案檔。</span><span class="sxs-lookup"><span data-stu-id="30c23-106">After you have opened a project from source control, you can check out and modify the project files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30c23-107">下列程序只應使用一次。</span><span class="sxs-lookup"><span data-stu-id="30c23-107">The following procedure should only be used once.</span></span> <span data-ttu-id="30c23-108">之後，您應該依序按一下 [檔案]、[**開啟**] 和 [**專案**) ]，來開啟**專案，就**像任何其他專案一樣 (。</span><span class="sxs-lookup"><span data-stu-id="30c23-108">Thereafter, you should open the project like any other project (by clicking **File**, **Open**, and then **Project**).</span></span>  
  
### <a name="to-open-a-project-from-source-control"></a><span data-ttu-id="30c23-109">從原始檔控制中開啟專案</span><span class="sxs-lookup"><span data-stu-id="30c23-109">To open a project from source control</span></span>  
  
1.  <span data-ttu-id="30c23-110">**在 [檔案**] 功能表上，指向 [原始檔**控制**]，然後按一下 [**從原始檔控制開啟**]。</span><span class="sxs-lookup"><span data-stu-id="30c23-110">On the **File** menu, point to **Source Control**, and click **Open From Source Control**.</span></span>  
  
2.  <span data-ttu-id="30c23-111">如果出現提示，請登入 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe。</span><span class="sxs-lookup"><span data-stu-id="30c23-111">If prompted, log on to [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe.</span></span>  
  
3.  <span data-ttu-id="30c23-112">在 [**從 SourceSafe 建立本機專案**] 對話方塊中，開啟包含要開啟之專案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="30c23-112">In the **Create local project from SourceSafe** dialog box, open the folder that contains the project to open.</span></span>  
  
4.  <span data-ttu-id="30c23-113">[在**資料夾中建立新專案**] 方塊會變更，以識別要在其中建立專案的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="30c23-113">The **Create a new project in the folder** box changes to identify the local directory in which the project will be created.</span></span> <span data-ttu-id="30c23-114">如果您想要將專案放在不同的目錄中，請輸入目錄的路徑，或使用 [**流覽]** 按鈕找出本機磁片上的目錄。</span><span class="sxs-lookup"><span data-stu-id="30c23-114">If you want to place the project in a different directory, type the path to the directory or use the **Browse** button to locate the directory on your local disk.</span></span>  
  
5.  <span data-ttu-id="30c23-115">在 [在**資料夾中建立新專案**] 方塊中，確認已顯示正確的資料夾，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="30c23-115">In the **Create a new project in the folder box**, verify that the correct folder is displayed, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="30c23-116">在 [**開啟方案**] 對話方塊中，選取您要開啟的專案，然後按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="30c23-116">In the **Open Solution** dialog box, select the project you want to open, and click **Open**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30c23-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30c23-117">See Also</span></span>  
 <span data-ttu-id="30c23-118">[從原始檔控制開啟方案和專案](../../2014/database-engine/open-solutions-and-projects-from-source-control.md) </span><span class="sxs-lookup"><span data-stu-id="30c23-118">[Open Solutions and Projects from Source Control](../../2014/database-engine/open-solutions-and-projects-from-source-control.md) </span></span>  
 [<span data-ttu-id="30c23-119">從原始檔控制開啟方案</span><span class="sxs-lookup"><span data-stu-id="30c23-119">Open Solutions from Source Control</span></span>](../../2014/database-engine/open-solutions-from-source-control.md)  
  
  
