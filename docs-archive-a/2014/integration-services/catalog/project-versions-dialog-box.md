---
title: 專案版本對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isprojectprop.versions.f1
ms.assetid: a48a387c-2e70-45bc-be2e-26e57a9bb2c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 998dd194c2a056121fd6f7a404e75c7080b85aa1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705362"
---
# <a name="project-versions-dialog-box"></a><span data-ttu-id="2a54d-102">專案版本對話方塊</span><span class="sxs-lookup"><span data-stu-id="2a54d-102">Project Versions Dialog Box</span></span>
  <span data-ttu-id="2a54d-103">使用 **[專案版本]** 對話方塊檢視專案版本，以及還原舊版。</span><span class="sxs-lookup"><span data-stu-id="2a54d-103">Use the **Project Versions** dialog box to view versions of a project and to restore a previous version.</span></span>  
  
 <span data-ttu-id="2a54d-104">您也可以在 [catalog.object_versions &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-views/catalog-object-versions-ssisdb-database) 檢視中檢視舊版，並使用 [catalog.restore_project &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database) 預存程序還原舊版。</span><span class="sxs-lookup"><span data-stu-id="2a54d-104">You can also view previous versions in the [catalog.object_versions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-object-versions-ssisdb-database) view, and use the [catalog.restore_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database) stored procedure to restore previous versions.</span></span>  
  
 <span data-ttu-id="2a54d-105">**您想要做什麼事？**</span><span class="sxs-lookup"><span data-stu-id="2a54d-105">**What do you want to do?**</span></span>  
  
-   <span data-ttu-id="2a54d-106">[開啟 [專案版本] 對話方塊](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="2a54d-106">[Open the Project Versions dialog box](#open_dialog)</span></span>  
  
-   [<span data-ttu-id="2a54d-107">還原專案版本</span><span class="sxs-lookup"><span data-stu-id="2a54d-107">Restore a Project Version</span></span>](#restore)  
  
##  <a name="open-the-project-versions-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="2a54d-108">開啟 [專案版本] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="2a54d-108">Open the Project Versions dialog box</span></span>  
  
1.  <span data-ttu-id="2a54d-109">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接至 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="2a54d-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="2a54d-110">亦即連接到主控 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 資料庫的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a54d-110">That is, connect to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="2a54d-111">在 [物件總管] 中，展開樹狀目錄以顯示 **[Integration Services 目錄]** 節點。</span><span class="sxs-lookup"><span data-stu-id="2a54d-111">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="2a54d-112">展開 **[Integration Services 目錄]** 節點以顯示 **[SSISDB]** 節點。</span><span class="sxs-lookup"><span data-stu-id="2a54d-112">Expand the **Integration Services Catalogs** node to display the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="2a54d-113">**[SSISDB]** 節點包含一個或多個資料夾，且每個資料夾包含一個或多個專案。</span><span class="sxs-lookup"><span data-stu-id="2a54d-113">The **SSISDB** node contains one or more folders that each contain one or more projects.</span></span> <span data-ttu-id="2a54d-114">展開包含您感興趣之專案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="2a54d-114">Expand the folder that contains the project you are interested in.</span></span>  
  
5.  <span data-ttu-id="2a54d-115">以滑鼠右鍵按一下專案，然後按一下 [版本]  。</span><span class="sxs-lookup"><span data-stu-id="2a54d-115">Right-click the project, and then click **Versions**.</span></span>  
  
 <span data-ttu-id="2a54d-116">在 [專案版本]  對話方塊中，[版本]  資料表會顯示已經在伺服器上部署之專案版本的清單、版本部署的日期和時間、版本還原的日期和時間 (如果已還原)、版本描述，以及版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="2a54d-116">In the **Project Versions** dialog box, the **Versions** table displays the list of versions of the project that have been deployed on the server, with the date and time the version was deployed, the date and time the version was restored (if it was restored), the version description, and a version identifier.</span></span> <span data-ttu-id="2a54d-117">目前使用中的版本會以資料表之 **[目前]** 資料行中的核取記號表示。</span><span class="sxs-lookup"><span data-stu-id="2a54d-117">The currently active version is indicated with a check mark in the **Current** column of the table.</span></span>  
  
##  <a name="restore-a-project-version"></a><a name="restore"></a> <span data-ttu-id="2a54d-118">還原專案版本</span><span class="sxs-lookup"><span data-stu-id="2a54d-118">Restore a Project Version</span></span>  
 <span data-ttu-id="2a54d-119">若要還原舊版專案，請在 **[版本]** 資料表中選取版本，然後按一下 **[還原至選取的版本]** 。</span><span class="sxs-lookup"><span data-stu-id="2a54d-119">To restore a previous version of a project, select the version in the **Versions** table, and then click **Restore to Selected Version**.</span></span> <span data-ttu-id="2a54d-120">專案便會還原到選取的版本，而且該版本會以 **[版本]** 資料表之 **[目前]** 資料行中的核取記號表示。</span><span class="sxs-lookup"><span data-stu-id="2a54d-120">The project is restored to the selected version and that version is indicated with a check mark in the **Current** column of the **Versions** table.</span></span>  
  
  
