---
title: 第1課：建立 Azure 儲存體物件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 74edd1fd-ab00-46f7-9e29-7ba3f1a446c5
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: d46c6d22ffd92dbf8035bff140960af8ef56122d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592398"
---
# <a name="lesson-1-create-azure-storage-objects"></a><span data-ttu-id="e4a59-102">第 1 課：建立 Azure 儲存體物件</span><span class="sxs-lookup"><span data-stu-id="e4a59-102">Lesson 1: Create Azure Storage Objects</span></span>
  <span data-ttu-id="e4a59-103">您必須先建立儲存體帳戶，然後建立 Blob 容器，才能在雲端儲存體上建立 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 備份。</span><span class="sxs-lookup"><span data-stu-id="e4a59-103">Before you can create [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backups on cloud storage, you must first create a storage account, and then a blob container.</span></span> <span data-ttu-id="e4a59-104">第1課會引導您完成登入 Azure 管理入口網站、建立儲存體帳戶和 blob 容器的步驟。</span><span class="sxs-lookup"><span data-stu-id="e4a59-104">Lesson 1 walks you through the steps of Logging into the Azure Management Portal, creating a storage account and a blob container.</span></span>  
  
## <a name="create-a-storage-account"></a><span data-ttu-id="e4a59-105">建立儲存體帳戶</span><span class="sxs-lookup"><span data-stu-id="e4a59-105">Create a storage Account</span></span>  
 <span data-ttu-id="e4a59-106">若要從 Azure 管理入口網站建立儲存體帳戶，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="e4a59-106">To create a storage account from the Azure Management Portal, use the following steps:</span></span>  
  
1.  <span data-ttu-id="e4a59-107">使用您的帳戶，登入 Azure 管理入口網站。</span><span class="sxs-lookup"><span data-stu-id="e4a59-107">Log in to the Azure Management Portal using your account.</span></span> <span data-ttu-id="e4a59-108">如果您沒有 Azure 帳戶，請[造訪 azure 3 個月免費試用](https://go.microsoft.com/fwlink/?LinkId=271927)。</span><span class="sxs-lookup"><span data-stu-id="e4a59-108">If you do not have an Azure account, [visit Azure 3-Month free trial](https://go.microsoft.com/fwlink/?LinkId=271927).</span></span>  
  
     <span data-ttu-id="e4a59-109">![Azure 登入畫面](../../2014/tutorials/media/windowazurelogin-backuptocloud.gif "Azure 登入畫面")</span><span class="sxs-lookup"><span data-stu-id="e4a59-109">![Azure Login Screen](../../2014/tutorials/media/windowazurelogin-backuptocloud.gif "Azure Login Screen")</span></span>  
  
2.  <span data-ttu-id="e4a59-110">使用[這裡](https://go.microsoft.com/fwlink/?LinkId=271926)詳述的逐步指示來建立儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="e4a59-110">Use the step by step instructions detailed [here](https://go.microsoft.com/fwlink/?LinkId=271926), to create a storage account.</span></span>  
  
3.  <span data-ttu-id="e4a59-111">瀏覽至您在上一個步驟中建立的儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="e4a59-111">Browse to the storage account you created in previous step.</span></span> <span data-ttu-id="e4a59-112">從網頁的正下方，按一下 [**管理金鑰**]。</span><span class="sxs-lookup"><span data-stu-id="e4a59-112">From the bottom center of the web page, click **MANAGE KEYS**.</span></span> <span data-ttu-id="e4a59-113">帳戶資訊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="e4a59-113">The account information is displayed.</span></span> <span data-ttu-id="e4a59-114">複製儲存體帳戶名稱以及存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="e4a59-114">Copy the storage account name, and the Access Keys.</span></span> <span data-ttu-id="e4a59-115">這項資訊是建立 SQL 預存認證的必要資訊。</span><span class="sxs-lookup"><span data-stu-id="e4a59-115">This information is required to create SQL Stored Credentials.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="e4a59-116">會使用這項資訊來存取儲存體帳戶並建立備份。</span><span class="sxs-lookup"><span data-stu-id="e4a59-116">uses this information to access the storage account and create backups.</span></span>  
  
     <span data-ttu-id="e4a59-117">![Azure 儲存體帳戶金鑰的螢幕擷取畫面](../../2014/tutorials/media/manageaccesskeys-backuptocloud.gif "Azure 儲存體帳戶金鑰的螢幕擷取畫面")</span><span class="sxs-lookup"><span data-stu-id="e4a59-117">![Screen shot of Azure Storage Account Keys](../../2014/tutorials/media/manageaccesskeys-backuptocloud.gif "Screen shot of Azure Storage Account Keys")</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e4a59-118">您也可以使用 REST API，以程式設計方式建立儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="e4a59-118">You can also create a storage account programmatically using REST APIs.</span></span> <span data-ttu-id="e4a59-119">如需詳細資訊，請參閱[建立儲存體帳戶](https://go.microsoft.com/fwlink/?LinkId=271928)。</span><span class="sxs-lookup"><span data-stu-id="e4a59-119">For more information, see [Create Storage Account](https://go.microsoft.com/fwlink/?LinkId=271928).</span></span>  
  
### <a name="create-a-blob-container"></a><span data-ttu-id="e4a59-120">建立 Blob 容器</span><span class="sxs-lookup"><span data-stu-id="e4a59-120">Create a Blob Container</span></span>  
 <span data-ttu-id="e4a59-121">容器會提供一組 Blob 的群組。</span><span class="sxs-lookup"><span data-stu-id="e4a59-121">A container provides a grouping of a set of blobs.</span></span> <span data-ttu-id="e4a59-122">所有 Blob 都必須位於容器中。</span><span class="sxs-lookup"><span data-stu-id="e4a59-122">All blobs must be in a container.</span></span> <span data-ttu-id="e4a59-123">帳戶可以包含不限數目的容器，但是至少必須具有一個容器。</span><span class="sxs-lookup"><span data-stu-id="e4a59-123">An account can contain an unlimited number of containers, but must have at least one container.</span></span> <span data-ttu-id="e4a59-124">容器可以儲存不限數目的 Blob。</span><span class="sxs-lookup"><span data-stu-id="e4a59-124">A container can store an unlimited number of blobs.</span></span>  
  
 <span data-ttu-id="e4a59-125">若要建立容器，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="e4a59-125">To create a Container, use the following steps:</span></span>  
  
1.  <span data-ttu-id="e4a59-126">選取儲存體帳戶，按一下 [**容器**] 索引標籤，然後按一下畫面底部的 [**新增容器**]，開啟新的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e4a59-126">Select the storage account, click the **CONTAINERS** tab and click **ADD CONTAINER** at the bottom of the screen which opens a new dialog box.</span></span>  
  
     <span data-ttu-id="e4a59-127">![建立管理入口網站中的容器](../../2014/tutorials/media/backuptocloud.gif "建立管理入口網站中的容器")</span><span class="sxs-lookup"><span data-stu-id="e4a59-127">![Creating a Container in the Management Portal](../../2014/tutorials/media/backuptocloud.gif "Creating a Container in the Management Portal")</span></span>  
  
2.  <span data-ttu-id="e4a59-128">輸入容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="e4a59-128">Enter the name for the container.</span></span> <span data-ttu-id="e4a59-129">記下您所指定的容器名稱。</span><span class="sxs-lookup"><span data-stu-id="e4a59-129">Make a note of the container name you specified.</span></span> <span data-ttu-id="e4a59-130">這項資訊會用於第 3 課和第 4 課的 T-SQL 陳述式 URL (備份檔的路徑) 中。</span><span class="sxs-lookup"><span data-stu-id="e4a59-130">This information is used in the URL (path to backup file) in the T-SQL statements in lesson 3 and 4.</span></span>  
  
3.  <span data-ttu-id="e4a59-131">針對 [**存取類型**] 選取 [私用]。</span><span class="sxs-lookup"><span data-stu-id="e4a59-131">Select Private for **Access Type**.</span></span> <span data-ttu-id="e4a59-132">我們建議您建立私用容器以確保備份檔安全。</span><span class="sxs-lookup"><span data-stu-id="e4a59-132">We recommend creating private containers for securing your backup files.</span></span>  
  
     <span data-ttu-id="e4a59-133">![正在建立新的 BLOB 容器](../../2014/tutorials/media/backuptocloud-newblobcontainer.gif "正在建立新的 BLOB 容器")</span><span class="sxs-lookup"><span data-stu-id="e4a59-133">![Creating a new blob container](../../2014/tutorials/media/backuptocloud-newblobcontainer.gif "Creating a new blob container")</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e4a59-134">即使您選擇建立公用容器，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 備份與還原仍然需要儲存體帳戶的驗證。</span><span class="sxs-lookup"><span data-stu-id="e4a59-134">Authentication to the storage account is required for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backup and restore even if you choose to create a public container.</span></span>  
    >   
    >  <span data-ttu-id="e4a59-135">您也可以使用 REST API，以程式設計方式建立容器。</span><span class="sxs-lookup"><span data-stu-id="e4a59-135">You can also create a container programmatically using REST APIs.</span></span> <span data-ttu-id="e4a59-136">如需詳細資訊，請參閱[Create Container](https://go.microsoft.com/fwlink/?LinkId=271946)。</span><span class="sxs-lookup"><span data-stu-id="e4a59-136">For more information, see [Create Container](https://go.microsoft.com/fwlink/?LinkId=271946).</span></span>  
  
### <a name="next-lesson"></a><span data-ttu-id="e4a59-137">下一課</span><span class="sxs-lookup"><span data-stu-id="e4a59-137">Next Lesson</span></span>  
 <span data-ttu-id="e4a59-138">[第2課：建立 SQL Server 認證](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md)。</span><span class="sxs-lookup"><span data-stu-id="e4a59-138">[Lesson 2: Create a SQL Server Credential](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md).</span></span>  
  
  
