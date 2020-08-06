---
title: 將專案加入至原始檔控制 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- projects [SQL Server Management Studio], adding
ms.assetid: fd4616b2-a564-4a66-ac53-d1f5cba213c2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0afef4ef91e4d80db7e956d03a95a2ecffe1dc4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592845"
---
# <a name="add-projects-to-source-control"></a><span data-ttu-id="79a47-102">將專案加入原始檔控制中</span><span class="sxs-lookup"><span data-stu-id="79a47-102">Add Projects to Source Control</span></span>
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="79a47-103">方案可以主控多個指令碼專案。</span><span class="sxs-lookup"><span data-stu-id="79a47-103">solutions can host multiple script projects.</span></span> <span data-ttu-id="79a47-104">您如何將專案加入原始檔控制中，會隨著專案所屬的方案是否在原始檔控制之下而不同。</span><span class="sxs-lookup"><span data-stu-id="79a47-104">How you add a project to source control depends upon whether the solution to which the project belongs is under source control.</span></span> <span data-ttu-id="79a47-105">如果方案在原始檔控制之下，簽入方案會自動將專案加入原始檔控制中。</span><span class="sxs-lookup"><span data-stu-id="79a47-105">If the solution is under source control, checking in the solution automatically adds the project to source control.</span></span> <span data-ttu-id="79a47-106">如需簽入方案的詳細資訊，請參閱[簽入](../../2014/database-engine/check-in-files.md)檔案。</span><span class="sxs-lookup"><span data-stu-id="79a47-106">For more information about checking in solutions, see [Check In Files](../../2014/database-engine/check-in-files.md).</span></span>  
  
 <span data-ttu-id="79a47-107">如果這個專案所屬的方案不在原始檔控制之下，您可以將這個方案加入原始檔控制中，之後，便會自動加入方案的專案。</span><span class="sxs-lookup"><span data-stu-id="79a47-107">If the solution that this project belongs to is not under source control, you can add that solution to source control, which then automatically adds the solution's projects.</span></span> <span data-ttu-id="79a47-108">如需將方案加入至原始檔控制的詳細資訊，請參閱[將方案加入至原始檔控制](../../2014/database-engine/add-solutions-to-source-control.md)。</span><span class="sxs-lookup"><span data-stu-id="79a47-108">For more information about adding solutions to source control, see [Add Solutions to Source Control](../../2014/database-engine/add-solutions-to-source-control.md).</span></span>  
  
 <span data-ttu-id="79a47-109">如果您不想要將方案加入至原始檔控制，可以使用 [**將選取專案加入至原始檔控制**] 命令來手動加入專案。</span><span class="sxs-lookup"><span data-stu-id="79a47-109">If you do not want to add the solution to source control, you can use the **Add Selection to Source Control** command to add the project manually.</span></span>  
  
 <span data-ttu-id="79a47-110">資料庫物件並未直接受到原始檔控制提供者的保護，但是您可以建立資料庫物件的指令碼，並在原始檔控制下儲存指令碼。</span><span class="sxs-lookup"><span data-stu-id="79a47-110">Database objects are not directly protected by the source control provider, but you can create scripts of database objects and save the scripts under source control.</span></span>  
  
### <a name="to-add-a-project-to-source-control"></a><span data-ttu-id="79a47-111">將專案加入原始檔控制中</span><span class="sxs-lookup"><span data-stu-id="79a47-111">To add a project to source control</span></span>  
  
1.  <span data-ttu-id="79a47-112">在 [方案總管] 中選取專案。</span><span class="sxs-lookup"><span data-stu-id="79a47-112">In Solution Explorer, select a project.</span></span>  
  
2.  <span data-ttu-id="79a47-113">**在 [檔案**] 功能表上，指向 [原始檔**控制**]，然後按一下 [**將選取的專案加入至原始檔控制**]。</span><span class="sxs-lookup"><span data-stu-id="79a47-113">On the **File** menu, point to **Source Control**, and then click **Add Selected Projects to Source Control**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="79a47-114">如果您使用 [**將選取的專案加入至原始檔控制**] 命令來加入屬於原始檔控制方案的專案，系統會提示您是否要將專案加入至原始檔控制方案的子資料夾，或加入專案做為個別的資料夾。</span><span class="sxs-lookup"><span data-stu-id="79a47-114">If you use the **Add Selected Projects to Source Control** command to add a project that belongs to a source-controlled solution, you are prompted whether you want to add the project as a subfolder of the source-controlled solution or to add the project as a separate folder.</span></span>  
  
3.  <span data-ttu-id="79a47-115">如果出現提示，請登入您的原始檔控制提供者。</span><span class="sxs-lookup"><span data-stu-id="79a47-115">If prompted, log on to your source control provider.</span></span>  
  
4.  <span data-ttu-id="79a47-116">[**加入至 SourceSafe 專案**] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="79a47-116">The **Add to SourceSafe Project** dialog box appears.</span></span> <span data-ttu-id="79a47-117">專案的名稱會出現在 [**專案**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="79a47-117">The name of your project appears in the **Project** box.</span></span>  
  
5.  <span data-ttu-id="79a47-118">在 [**資料夾**] 清單中，開啟您要放置專案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="79a47-118">In the **Folders** list, open the folder where you want to place your project.</span></span> <span data-ttu-id="79a47-119">或者，您也可以按一下 [**建立**]，以在 [**專案**] 方塊中顯示名稱來建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="79a47-119">Alternatively, you can click **Create** to create a folder with the name displayed in the **Project** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79a47-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79a47-120">See Also</span></span>  
 [<span data-ttu-id="79a47-121">將方案與專案加入原始檔控制</span><span class="sxs-lookup"><span data-stu-id="79a47-121">Add Solutions and Projects to Source Control</span></span>](../../2014/database-engine/add-solutions-and-projects-to-source-control.md)  
  
  
