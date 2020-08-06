---
title: 原始檔控制基本概念 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- source controls [SQL Server Management Studio], providers
- source controls [SQL Server Management Studio]
- source controls [SQL Server Management Studio], about source controls
- source controls [SQL Server Management Studio], clients
ms.assetid: ca35b67a-104a-41fb-ac58-a61be06fe114
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1112dcd8cfdec429b27b22ea3853de859553af0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585563"
---
# <a name="source-control-basics"></a><span data-ttu-id="a91e1-102">原始檔控制基本概念</span><span class="sxs-lookup"><span data-stu-id="a91e1-102">Source Control Basics</span></span>
  <span data-ttu-id="a91e1-103">「原始檔控制」是指利用一段中央伺服器軟體來儲存和追蹤檔案版本及控制檔案存取動作的系統。</span><span class="sxs-lookup"><span data-stu-id="a91e1-103">Source control refers to a system in which a central piece of server software stores and tracks file versions, and also controls access to files.</span></span> <span data-ttu-id="a91e1-104">典型的原始檔控制系統包括一個原始檔控制提供者及兩個或更多原始檔控制用戶端。</span><span class="sxs-lookup"><span data-stu-id="a91e1-104">A typical source control system includes a source control provider and two or more source control clients.</span></span>  
  
## <a name="source-control-benefits"></a><span data-ttu-id="a91e1-105">原始檔控制的好處</span><span class="sxs-lookup"><span data-stu-id="a91e1-105">Source Control Benefits</span></span>  
 <span data-ttu-id="a91e1-106">將檔案放在原始檔控制之下，就能夠執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a91e1-106">Placing your files under source control makes it possible to</span></span>  
  
-   <span data-ttu-id="a91e1-107">管理在不同人員之間傳遞項目控制權的程序。</span><span class="sxs-lookup"><span data-stu-id="a91e1-107">Manage the process by which the control of items passes from one person to another.</span></span> <span data-ttu-id="a91e1-108">原始檔控制提供者支援共用和獨佔兩種檔案存取模式。</span><span class="sxs-lookup"><span data-stu-id="a91e1-108">Source control providers support both shared and exclusive file access.</span></span> <span data-ttu-id="a91e1-109">如果專案檔的存取是獨佔的，原始檔控制提供者每次只允許一位使用者簽出和修改檔案。</span><span class="sxs-lookup"><span data-stu-id="a91e1-109">If access to project files is exclusive, the source control provider allows only one user at a time to check files out and modify them.</span></span> <span data-ttu-id="a91e1-110">如果存取是共用的，便可以讓多位使用者簽出指令碼檔案，在各版本簽入時，原始檔控制提供者會提供用來合併它們的機制。</span><span class="sxs-lookup"><span data-stu-id="a91e1-110">If access is shared, more than one user can check out the script file, and the source control provider provides a mechanism for merging the versions as they are checked in.</span></span>  
  
-   <span data-ttu-id="a91e1-111">保存原始檔控制項目的連續版本。</span><span class="sxs-lookup"><span data-stu-id="a91e1-111">Archive successive versions of source-controlled items.</span></span> <span data-ttu-id="a91e1-112">原始檔控制提供者會儲存用來區分原始檔控制項目各個版本的資料。</span><span class="sxs-lookup"><span data-stu-id="a91e1-112">A source control provider stores the data that distinguishes one version of a source-controlled item from another.</span></span> <span data-ttu-id="a91e1-113">提供者會將版本之間的差異儲存起來，也會將版本的重要資訊儲存起來，其中包括它的建立時間、修改時間，以及修改者。</span><span class="sxs-lookup"><span data-stu-id="a91e1-113">The provider stores the differences between versions, as well as crucial information about the version: when it was created, when it was modified, and by whom.</span></span> <span data-ttu-id="a91e1-114">當許多人在處理相同的檔案時，他們必須使用相同的字碼頁，以便能夠精確地比較版本。</span><span class="sxs-lookup"><span data-stu-id="a91e1-114">When several people are working on the same file, they must use the same code page, so that versions can be accurately compared.</span></span> <span data-ttu-id="a91e1-115">因此，您可以擷取原始檔控制項目的任何版本。</span><span class="sxs-lookup"><span data-stu-id="a91e1-115">Consequently, you can retrieve any version of a source-controlled item.</span></span> <span data-ttu-id="a91e1-116">您也可以將任何版本指定為這個項目的最新版本。</span><span class="sxs-lookup"><span data-stu-id="a91e1-116">You can also designate any version to be the latest version of that item.</span></span>  
  
-   <span data-ttu-id="a91e1-117">維護原始檔控制項目的詳細歷程和版本資訊。</span><span class="sxs-lookup"><span data-stu-id="a91e1-117">Maintain detailed historical and version information on source-controlled items.</span></span> <span data-ttu-id="a91e1-118">原始檔控制會儲存項目的建立日期和時間、簽出或簽入的時間，以及執行動作的使用者。</span><span class="sxs-lookup"><span data-stu-id="a91e1-118">Source control stores the date and time on which the item was created, when it was checked out or checked in, and the user who performed the action.</span></span>  
  
-   <span data-ttu-id="a91e1-119">跨專案的協同運作。</span><span class="sxs-lookup"><span data-stu-id="a91e1-119">Collaborate across projects.</span></span> <span data-ttu-id="a91e1-120">檔案的共用使得多個專案有可能共用相同的原始檔控制項目。</span><span class="sxs-lookup"><span data-stu-id="a91e1-120">File sharing makes it possible for multiple projects to share source-controlled items.</span></span> <span data-ttu-id="a91e1-121">共用項目的變更，會反映在共用這個項目的所有專案中。</span><span class="sxs-lookup"><span data-stu-id="a91e1-121">Changes to a shared item are reflected in all the projects that share the item.</span></span>  
  
-   <span data-ttu-id="a91e1-122">自動執行經常重複的原始檔控制作業。</span><span class="sxs-lookup"><span data-stu-id="a91e1-122">Automate frequently repeated source control operations.</span></span> <span data-ttu-id="a91e1-123">原始檔控制提供者可以從命令提示字元之下，定義一個支援原始檔控制主要功能的介面。</span><span class="sxs-lookup"><span data-stu-id="a91e1-123">A source control provider may define an interface from the command prompt that supports the key features of source control.</span></span> <span data-ttu-id="a91e1-124">您可以在批次檔中利用這個介面來自動執行您定期執行的原始檔控制工作。</span><span class="sxs-lookup"><span data-stu-id="a91e1-124">You can use this interface in batch files to automate the source control tasks that you perform regularly.</span></span>  
  
-   <span data-ttu-id="a91e1-125">從意外刪除中復原。</span><span class="sxs-lookup"><span data-stu-id="a91e1-125">Recover from accidental deletions.</span></span> <span data-ttu-id="a91e1-126">您可以還原簽入原始檔控制中的最新檔案版本。</span><span class="sxs-lookup"><span data-stu-id="a91e1-126">You can restore the latest file version checked into source control.</span></span>  
  
-   <span data-ttu-id="a91e1-127">節省原始檔控制用戶端和伺服器的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="a91e1-127">Conserve disk space on both the source control client and server.</span></span> <span data-ttu-id="a91e1-128">部份原始檔控制提供者 (如 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe) 支援儲存檔案的最新版本及各版本之間的差異，以節省伺服器的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="a91e1-128">Some source control providers, such as [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, support disk space conservation on the server by storing the latest version of a file and the differences between each version and the version that precedes or follows it.</span></span> <span data-ttu-id="a91e1-129">Visual SourceSafe 支援節省用戶端的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="a91e1-129">On the client, Visual SourceSafe supports disk space conservation.</span></span> <span data-ttu-id="a91e1-130">您可以隱藏資料夾和檔案，使它們不會下載到您的本機磁碟中。</span><span class="sxs-lookup"><span data-stu-id="a91e1-130">You can cloak folders and files so that they are not downloaded to your local disk.</span></span>  
  
 <span data-ttu-id="a91e1-131">檔案的簽出、簽入及其他原始檔控制作業，實際上，都是由 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 之類的原始檔控制用戶端來完成的。</span><span class="sxs-lookup"><span data-stu-id="a91e1-131">File check outs, check ins, and other source control operations are actually accomplished through a source control client, such as [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="a91e1-132">用戶端的設計就是為了與提供者互動，以便將提供者的功能提供給分散的使用者群組使用。</span><span class="sxs-lookup"><span data-stu-id="a91e1-132">The client is designed to interact with the provider to make the provider's capabilities available to a distributed group of users.</span></span> <span data-ttu-id="a91e1-133">當使用原始檔控制用戶端時，使用者可以瀏覽提供者所儲存的檔案、加入和刪除檔案、簽入和簽出檔案，以及擷取本機檔案副本。</span><span class="sxs-lookup"><span data-stu-id="a91e1-133">Using a source control client, users can browse the files stored by the provider; add and delete files; check files in and out; and retrieve copies of local files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a91e1-134">這份文件集假設您的原始檔控制提供者是 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe。</span><span class="sxs-lookup"><span data-stu-id="a91e1-134">This documentation assumes that you are using [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe as your source control provider.</span></span> <span data-ttu-id="a91e1-135">如果您使用其他原始檔控制提供者，這份文件集和您在執行的軟體可能會不同。</span><span class="sxs-lookup"><span data-stu-id="a91e1-135">If you are using a different source control provider, you might see differences between this documentation and the software you are running.</span></span> <span data-ttu-id="a91e1-136">如果不同，請參閱您的原始檔控制提供者的文件集。</span><span class="sxs-lookup"><span data-stu-id="a91e1-136">If you see differences, consult the documentation for your source control provider.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="a91e1-137">相關工作</span><span class="sxs-lookup"><span data-stu-id="a91e1-137">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a91e1-138">**Task**</span><span class="sxs-lookup"><span data-stu-id="a91e1-138">**Task**</span></span>|<span data-ttu-id="a91e1-139">**主題**</span><span class="sxs-lookup"><span data-stu-id="a91e1-139">**Topic**</span></span>|  
|<span data-ttu-id="a91e1-140">設定原始檔控制選項</span><span class="sxs-lookup"><span data-stu-id="a91e1-140">Set Source Control options</span></span>|[<span data-ttu-id="a91e1-141">設定原始檔控制選項</span><span class="sxs-lookup"><span data-stu-id="a91e1-141">Set Source Control Options</span></span>](../../2014/database-engine/set-source-control-options.md)|  
|<span data-ttu-id="a91e1-142">變更原始檔控制連接</span><span class="sxs-lookup"><span data-stu-id="a91e1-142">Change source control Connections</span></span>|[<span data-ttu-id="a91e1-143">變更原始檔控制連接</span><span class="sxs-lookup"><span data-stu-id="a91e1-143">Change Source Control Connections</span></span>](../../2014/database-engine/change-source-control-connections.md)|  
|<span data-ttu-id="a91e1-144">從原始檔控制中排除檔案</span><span class="sxs-lookup"><span data-stu-id="a91e1-144">Exclude files from source control</span></span>|[<span data-ttu-id="a91e1-145">從原始檔控制中排除檔案</span><span class="sxs-lookup"><span data-stu-id="a91e1-145">Exclude Files from Source Control</span></span>](../../2014/database-engine/exclude-files-from-source-control.md)|  
  
  
