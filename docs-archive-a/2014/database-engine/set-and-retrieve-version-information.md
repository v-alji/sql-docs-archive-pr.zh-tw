---
title: 設定和抓取版本資訊 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- historical information [SQL Server]
- source controls [SQL Server Management Studio], version information
- retrieving version information
- current file version information
- version control services [SQL Server], retrieving version information
- version control services [SQL Server], setting version information
- status information [SQL Server], source control files
- historical information [SQL Server], source control files
ms.assetid: c3f253c4-4e3d-48e8-8d90-bd6ee899faf7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: eff3d40ba9b663ba8611508c5b9f0c9961005b81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687139"
---
# <a name="set-and-retrieve-version-information"></a><span data-ttu-id="5f886-102">設定及擷取版本資訊</span><span class="sxs-lookup"><span data-stu-id="5f886-102">Set and Retrieve Version Information</span></span>
  <span data-ttu-id="5f886-103">版本資訊包括原始檔控制檔案的記錄和目前狀態。</span><span class="sxs-lookup"><span data-stu-id="5f886-103">Version information includes the history and current status of a source-controlled file.</span></span> <span data-ttu-id="5f886-104">[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe 會維護每個原始檔控制檔案的完整歷程，供您追蹤一或多個檔案在時間中的進展。</span><span class="sxs-lookup"><span data-stu-id="5f886-104">For every source-controlled file, [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe maintains a comprehensive history, so you can track the evolution of one or more files over time.</span></span> <span data-ttu-id="5f886-105">您也可以利用這項資訊來擷取檔案任何版本的本機副本，或比較任意兩個檔案版本。</span><span class="sxs-lookup"><span data-stu-id="5f886-105">You can also use this information to retrieve a local copy of any version of the file or to compare any two file versions.</span></span>  
  
 <span data-ttu-id="5f886-106">檔案的記錄包括：</span><span class="sxs-lookup"><span data-stu-id="5f886-106">The history of a file includes:</span></span>  
  
-   <span data-ttu-id="5f886-107">版本號碼，用來識別它在相同檔案各其他版本之間的順序。</span><span class="sxs-lookup"><span data-stu-id="5f886-107">The version number, which identifies its sequence among other versions of the same file.</span></span>  
  
-   <span data-ttu-id="5f886-108">執行的動作。</span><span class="sxs-lookup"><span data-stu-id="5f886-108">The action performed.</span></span> <span data-ttu-id="5f886-109">追蹤的作業包括檔案的建立、簽入和刪除。</span><span class="sxs-lookup"><span data-stu-id="5f886-109">Tracked operations include file creation, check in, and deletion.</span></span>  
  
-   <span data-ttu-id="5f886-110">涉及檔案的動作之執行者的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="5f886-110">The user name of the person who performed an action involving the file.</span></span>  
  
-   <span data-ttu-id="5f886-111">作業的執行日期和時間。</span><span class="sxs-lookup"><span data-stu-id="5f886-111">The date and time when the operation was performed.</span></span>  
  
 <span data-ttu-id="5f886-112">另外，Visual SourceSafe 也會維護目前載入的方案之目前的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="5f886-112">Visual SourceSafe also maintains current status information on the currently loaded solution.</span></span> <span data-ttu-id="5f886-113">這項資訊提供檔案目前狀態的快照，其中包括：</span><span class="sxs-lookup"><span data-stu-id="5f886-113">This information provides a snapshot of the current state of the file, including:</span></span>  
  
-   <span data-ttu-id="5f886-114">簽出檔案之使用者的識別。</span><span class="sxs-lookup"><span data-stu-id="5f886-114">The identity of the user who has the file checked out.</span></span>  
  
-   <span data-ttu-id="5f886-115">所選檔案最新的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="5f886-115">The latest version number of the selected file.</span></span>  
  
-   <span data-ttu-id="5f886-116">版本的建立日期。</span><span class="sxs-lookup"><span data-stu-id="5f886-116">The date when the version was created.</span></span>  
  
-   <span data-ttu-id="5f886-117">版本的相關使用者註解。</span><span class="sxs-lookup"><span data-stu-id="5f886-117">The user comment associated with the version.</span></span>  
  
-   <span data-ttu-id="5f886-118">共用檔案之專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="5f886-118">The paths to the projects with which the file is shared.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5f886-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="5f886-119">In This Section</span></span>  
  
-   [<span data-ttu-id="5f886-120">檢視檔案記錄</span><span class="sxs-lookup"><span data-stu-id="5f886-120">View File History</span></span>](../../2014/database-engine/view-file-history.md)  
  
-   [<span data-ttu-id="5f886-121">檢視專案記錄</span><span class="sxs-lookup"><span data-stu-id="5f886-121">View Project History</span></span>](../../2014/database-engine/view-project-history.md)  
  
-   [<span data-ttu-id="5f886-122">檢視檔案狀態</span><span class="sxs-lookup"><span data-stu-id="5f886-122">View File Status</span></span>](../../2014/database-engine/view-file-status.md)  
  
-   [<span data-ttu-id="5f886-123">擷取檔案</span><span class="sxs-lookup"><span data-stu-id="5f886-123">Retrieve Files</span></span>](../../2014/database-engine/retrieve-files.md)  
  
-   [<span data-ttu-id="5f886-124">將版本指定為最新版</span><span class="sxs-lookup"><span data-stu-id="5f886-124">Specify a Version as the Latest Version</span></span>](../../2014/database-engine/specify-a-version-as-the-latest-version.md)  
  
-   [<span data-ttu-id="5f886-125">比較檔案</span><span class="sxs-lookup"><span data-stu-id="5f886-125">Compare Files</span></span>](../../2014/database-engine/compare-files.md)  
  
-   [<span data-ttu-id="5f886-126">共用檔案</span><span class="sxs-lookup"><span data-stu-id="5f886-126">Share Files</span></span>](../../2014/database-engine/share-files.md)  
  
-   [<span data-ttu-id="5f886-127">建立記錄和狀態報表</span><span class="sxs-lookup"><span data-stu-id="5f886-127">Create History and Status Reports</span></span>](../../2014/database-engine/create-history-and-status-reports.md)  
  
## <a name="see-also"></a><span data-ttu-id="5f886-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f886-128">See Also</span></span>  
 [<span data-ttu-id="5f886-129">原始檔控制基本概念</span><span class="sxs-lookup"><span data-stu-id="5f886-129">Source Control Basics</span></span>](../../2014/database-engine/source-control-basics.md)  
  
  
