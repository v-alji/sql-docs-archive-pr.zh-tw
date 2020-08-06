---
title: 維護清除工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.maintenancecleanuptask.f1
helpviewer_keywords:
- deleting files
- removing files
- Maintenance Cleanup task
ms.assetid: 73ad3cd6-9a6d-44cf-905f-c56aa658bf42
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4d39dd775402adadbe51eaadc530f4feb288ab9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594619"
---
# <a name="maintenance-cleanup-task"></a><span data-ttu-id="41c7c-102">維護清除工作</span><span class="sxs-lookup"><span data-stu-id="41c7c-102">Maintenance Cleanup Task</span></span>
  <span data-ttu-id="41c7c-103">「維護清除」工作會移除與維護計畫相關的檔案，包括資料庫備份檔案以及維護計畫所建立的報表。</span><span class="sxs-lookup"><span data-stu-id="41c7c-103">The Maintenance Cleanup task removes files related to maintenance plans, including database backup files and reports created by maintenance plans.</span></span> <span data-ttu-id="41c7c-104">如需詳細資訊，請參閱 [維護計畫](../../relational-databases/maintenance-plans/maintenance-plans.md) 和 [SQL Server 資料庫的備份與還原](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="41c7c-104">For more information, see [Maintenance Plans](../../relational-databases/maintenance-plans/maintenance-plans.md) and [Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
 <span data-ttu-id="41c7c-105">封裝可以使用「維護清除」工作來移除指定伺服器上的備份檔案或維護計畫報表。</span><span class="sxs-lookup"><span data-stu-id="41c7c-105">By using the Maintenance Cleanup task, a package can remove the backup files or maintenance plan reports on the specified server.</span></span> <span data-ttu-id="41c7c-106">「維護清除」工作包含一個選項，可用來移除某個特定檔案或移除資料夾中的某個檔案群組。</span><span class="sxs-lookup"><span data-stu-id="41c7c-106">The Maintenance Cleanup task includes an option to remove a specific file or remove a group of files in a folder.</span></span> <span data-ttu-id="41c7c-107">您也可以選擇指定要刪除之檔案的副檔名。</span><span class="sxs-lookup"><span data-stu-id="41c7c-107">Optionally you can specify the extension of the files to delete.</span></span>  
  
 <span data-ttu-id="41c7c-108">當您設定「維護清除」工作來移除備份檔時，預設副檔名是 BAK。</span><span class="sxs-lookup"><span data-stu-id="41c7c-108">When you configure the Maintenance Cleanup task to remove backup files, the default file name extension is BAK.</span></span> <span data-ttu-id="41c7c-109">如果是報表檔案，預設副檔名是 TXT。</span><span class="sxs-lookup"><span data-stu-id="41c7c-109">For report files, the default file name extension is TXT.</span></span> <span data-ttu-id="41c7c-110">您可以更新副檔名，以符合您的需求，唯一的限制是副檔名的長度必須小於 256 個字元。</span><span class="sxs-lookup"><span data-stu-id="41c7c-110">You can update the extensions to suit your needs; the only limitation is that extensions must be less than 256 characters long.</span></span>  
  
 <span data-ttu-id="41c7c-111">通常您會想移除已經不需要的舊檔案，而且可以設定「維護清除」工作，以刪除已經到達指定存在時間的檔案。</span><span class="sxs-lookup"><span data-stu-id="41c7c-111">Typically, you want to remove old files that are no longer needed, and the Maintenance Cleanup task can be configured to delete files that have reached a specified age.</span></span> <span data-ttu-id="41c7c-112">例如，您可以設定工作以刪除存在時間已超過四週的檔案。</span><span class="sxs-lookup"><span data-stu-id="41c7c-112">For example, the task can be configured to delete files that are older than four weeks.</span></span> <span data-ttu-id="41c7c-113">您可以使用天數、週數、月數或年數來指定要刪除之檔案的存在時間。</span><span class="sxs-lookup"><span data-stu-id="41c7c-113">You can specify the age of files to delete by using days, weeks, months, or years.</span></span> <span data-ttu-id="41c7c-114">如果沒有指定要刪除之檔案的最低存在時間，則會刪除指定類型的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="41c7c-114">If you do not specify the minimum age of files to delete, all files of the specified type are deleted.</span></span>  
  
 <span data-ttu-id="41c7c-115">與舊版的「維護清除」工作不同， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版的工作並不會自動刪除指定目錄之子目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="41c7c-115">In contrast to earlier versions of the Maintenance Cleanup task, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version of the task does not automatically delete files in the subdirectories of the specified directory.</span></span> <span data-ttu-id="41c7c-116">此條件約束會縮小任何可能利用「維護清除」工作功能惡意刪除檔案之攻擊的介面區。</span><span class="sxs-lookup"><span data-stu-id="41c7c-116">This constraint reduces the surface area of any attack that could exploit the functionality of the Maintenance Cleanup task to delete files maliciously.</span></span> <span data-ttu-id="41c7c-117">若要刪除第一層子資料夾，您必須選取 [維護清除工作] 對話方塊中的 [包含第一層的子資料夾] 選項，明確選擇要執行此動作。</span><span class="sxs-lookup"><span data-stu-id="41c7c-117">To delete the first-level subfolders, you must explicitly elect to do this by checking the **Include first-level subfolders** option in the **Maintenance Cleanup Task** dialog box.</span></span>  
  
## <a name="configuration-of-the-maintenance-cleanup-task"></a><span data-ttu-id="41c7c-118">設定維護清除工作</span><span class="sxs-lookup"><span data-stu-id="41c7c-118">Configuration of the Maintenance Cleanup Task</span></span>  
 <span data-ttu-id="41c7c-119">您可以透過 [ [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師] 設定屬性。</span><span class="sxs-lookup"><span data-stu-id="41c7c-119">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="41c7c-120">這項工作位於「 **設計師」中** [工具箱] **的** [維護計畫工作] [!INCLUDE[ssIS](../../includes/ssis-md.md)] 區段。</span><span class="sxs-lookup"><span data-stu-id="41c7c-120">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="41c7c-121">如需有關可在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="41c7c-121">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="41c7c-122">維護清除工作 &#40;維護計畫&#41;</span><span class="sxs-lookup"><span data-stu-id="41c7c-122">Maintenance Cleanup Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/maintenance-cleanup-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="41c7c-123">相關工作</span><span class="sxs-lookup"><span data-stu-id="41c7c-123">Related Tasks</span></span>  
 <span data-ttu-id="41c7c-124">如需如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計工具中設定這些屬性的詳細資訊，請參閱 [設定工作或容器的屬性](../set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="41c7c-124">For details about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c7c-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41c7c-125">See Also</span></span>  
 <span data-ttu-id="41c7c-126">[Integration Services 工作](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="41c7c-126">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="41c7c-127">控制流程</span><span class="sxs-lookup"><span data-stu-id="41c7c-127">Control Flow</span></span>](control-flow.md)  
  
  
