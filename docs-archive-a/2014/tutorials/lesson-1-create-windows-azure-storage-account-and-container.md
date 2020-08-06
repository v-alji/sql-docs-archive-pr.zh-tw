---
title: 第1課：建立 Azure 儲存體帳戶和容器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: efdbd930-cde5-41b0-90ad-58a6cc68dddc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 07167c513d2c6ed3ae0f7b431461ee3915047636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585712"
---
# <a name="lesson-1-create-azure-storage-account-and-container"></a><span data-ttu-id="2915c-102">第 1 課：建立 Azure 儲存體帳戶和容器</span><span class="sxs-lookup"><span data-stu-id="2915c-102">Lesson 1: Create Azure Storage Account and Container</span></span>
  <span data-ttu-id="2915c-103">您必須先建立 Azure 儲存體帳戶和 blob 容器以及共用存取簽章，才能開始在 Azure 儲存體中儲存 SQL Server 的資料檔案。</span><span class="sxs-lookup"><span data-stu-id="2915c-103">Before you can start storing SQL Server data files in Azure Storage, you must first create an Azure Storage account and a blob container, and a shared access signature.</span></span> <span data-ttu-id="2915c-104">第1課會逐步引導您登入 Azure 管理入口網站、建立儲存體帳戶、blob 容器，以及共用存取簽章。</span><span class="sxs-lookup"><span data-stu-id="2915c-104">Lesson 1 walks you through the steps of logging into the Azure Management Portal, creating a storage account, a blob container, and a shared access signature.</span></span>  
  
 <span data-ttu-id="2915c-105">根據預設，只有儲存體帳戶的擁有者才可以存取該帳戶內的 Blob、資料表和佇列。</span><span class="sxs-lookup"><span data-stu-id="2915c-105">By default, only the owner of the storage account may access blobs, tables, and queues within that account.</span></span> <span data-ttu-id="2915c-106">若要能夠在不共用儲存體帳戶存取金鑰的情況下，使用這個新的 SQL Server 增強功能存取這些資源，您需要執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="2915c-106">To be able to access these resources using this new SQL Server enhancement without sharing the storage account access key, you are required to do these:</span></span>  
  
-   <span data-ttu-id="2915c-107">將容器的權限設為私用。</span><span class="sxs-lookup"><span data-stu-id="2915c-107">Set the container's permissions to private.</span></span>  
  
-   <span data-ttu-id="2915c-108">建立共用存取簽章。</span><span class="sxs-lookup"><span data-stu-id="2915c-108">Create a shared access signature.</span></span> <span data-ttu-id="2915c-109">它可讓您藉由指定提供資源的間隔以及用戶端對其擁有的權限，委派容器、Blob、資料表或佇列資源的有限存取權。</span><span class="sxs-lookup"><span data-stu-id="2915c-109">It enables you to delegate restricted access to a container, blob, table, or queue resource by specifying the interval for which the resources are available and the permissions that a client will have to it.</span></span>  
  
-   <span data-ttu-id="2915c-110">使用預存的存取原則管理容器或其 Blob 的共用存取簽章。</span><span class="sxs-lookup"><span data-stu-id="2915c-110">Use a stored access policy to manage shared access signatures for a container or its blobs.</span></span> <span data-ttu-id="2915c-111">預存的存取原則為您提供另一種控制共用存取簽章的方法，同時也提供了直接將簽章撤銷的方式。</span><span class="sxs-lookup"><span data-stu-id="2915c-111">The stored access policy gives you an additional measure of control over your shared access signatures and also provides a straightforward means to revoke them.</span></span>  
  
 <span data-ttu-id="2915c-112">如需詳細資訊，請參閱[管理 Azure 儲存體資源的存取](https://msdn.microsoft.com/library/windowsazure/ee393343.aspx)。</span><span class="sxs-lookup"><span data-stu-id="2915c-112">For more information, see [Manage Access to Azure Storage Resources](https://msdn.microsoft.com/library/windowsazure/ee393343.aspx).</span></span>  
  
## <a name="create-storage-account"></a><span data-ttu-id="2915c-113">建立儲存體帳戶</span><span class="sxs-lookup"><span data-stu-id="2915c-113">Create Storage Account</span></span>  
 <span data-ttu-id="2915c-114">若要在 Azure 管理入口網站上建立儲存體帳戶，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="2915c-114">To create a storage account on the Azure Management Portal, follow these steps:</span></span>  
  
1.  <span data-ttu-id="2915c-115">使用您的帳戶登入[Azure 管理入口網站](https://manage.windowsazure.com)。</span><span class="sxs-lookup"><span data-stu-id="2915c-115">Log in to the [Azure Management Portal](https://manage.windowsazure.com) using your account.</span></span> <span data-ttu-id="2915c-116">如果您沒有 Azure 帳戶，請造訪 [Azure 免費試用](https://www.windowsazure.com/pricing/free-trial/)。</span><span class="sxs-lookup"><span data-stu-id="2915c-116">If you do not have an Azure account, visit [Azure free trial](https://www.windowsazure.com/pricing/free-trial/).</span></span>  
  
     <span data-ttu-id="2915c-117">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="2915c-117">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")</span></span>  
  
2.  <span data-ttu-id="2915c-118">使用逐步指示來[建立儲存體帳戶](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/)。</span><span class="sxs-lookup"><span data-stu-id="2915c-118">Use the step by step instructions to [create a storage account](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).</span></span> <span data-ttu-id="2915c-119">請注意，建立要用於 Azure 功能中 SQL Server 資料檔案的儲存體帳戶時，您應該取消選取或停用異地複寫。</span><span class="sxs-lookup"><span data-stu-id="2915c-119">Note that when creating a storage account to be used for the SQL Server Data Files in Azure feature, you should unselect or disable the geo-replication.</span></span> <span data-ttu-id="2915c-120">這是因為無法保證參與地理複寫的多個 Blob 的寫入順序。</span><span class="sxs-lookup"><span data-stu-id="2915c-120">This is because write order is not guaranteed for multiple blobs participating in geo-replication.</span></span> <span data-ttu-id="2915c-121">如果儲存體帳戶為地理複寫且需要復原，則會發生損毀。</span><span class="sxs-lookup"><span data-stu-id="2915c-121">If a storage account is geo-replicated and recovery is required, a corruption occurs.</span></span>  
  
     <span data-ttu-id="2915c-122">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="2915c-122">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")</span></span>  
  
## <a name="create-a-blob-container"></a><span data-ttu-id="2915c-123">建立 Blob 容器</span><span class="sxs-lookup"><span data-stu-id="2915c-123">Create a Blob container</span></span>  
 <span data-ttu-id="2915c-124">在 Azure 中，容器會提供一組 blob 的群組。</span><span class="sxs-lookup"><span data-stu-id="2915c-124">In Azure, a container provides a grouping of a set of blobs.</span></span> <span data-ttu-id="2915c-125">所有 Blob 都必須位於容器中。</span><span class="sxs-lookup"><span data-stu-id="2915c-125">All blobs must be in a container.</span></span> <span data-ttu-id="2915c-126">儲存體帳戶可以包含不限數目的容器，但是至少必須具有一個容器。</span><span class="sxs-lookup"><span data-stu-id="2915c-126">A storage account can contain an unlimited number of containers, but must have at least one container.</span></span> <span data-ttu-id="2915c-127">容器可以儲存不限數目的 Blob。</span><span class="sxs-lookup"><span data-stu-id="2915c-127">A container can store an unlimited number of blobs.</span></span> <span data-ttu-id="2915c-128">如需有關儲存體大小限制的最新資訊，請參閱[如何在 .net 中使用 Azure Blob 儲存體服務](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/)。</span><span class="sxs-lookup"><span data-stu-id="2915c-128">For most up-to-date information on storage size limits, see [How to use the Azure Blob Storage Service in .NET](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/).</span></span>  
  
 <span data-ttu-id="2915c-129">若要在 Azure 中建立容器，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="2915c-129">To create a container in Azure, follow these steps:</span></span>  
  
1.  <span data-ttu-id="2915c-130">登入 [[Azure 管理入口網站]](https://manage.windowsazure.com)。</span><span class="sxs-lookup"><span data-stu-id="2915c-130">Log in to the [Azure Management Portal](https://manage.windowsazure.com).</span></span>  
  
2.  <span data-ttu-id="2915c-131">選取儲存體帳戶，按一下 [**容器**] 索引標籤，然後按一下畫面底部的 [**新增容器**]，這會開啟新的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2915c-131">Select the storage account, click the **CONTAINERS** tab and click **ADD CONTAINER** at the bottom of the screen, which opens a new dialog box.</span></span>  
  
3.  <span data-ttu-id="2915c-132">輸入容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="2915c-132">Enter a name for the container.</span></span>  
  
4.  <span data-ttu-id="2915c-133">針對 [**存取類型**] 選取 [**私**用]。</span><span class="sxs-lookup"><span data-stu-id="2915c-133">Select **Private** for **Access Type**.</span></span> <span data-ttu-id="2915c-134">當您將存取權設為 [私用] 時，只有 Azure 帳戶擁有者可以讀取容器和 blob 資料。</span><span class="sxs-lookup"><span data-stu-id="2915c-134">When you set the access to private, the container and blob data can be read by the Azure account owner only.</span></span>  
  
     <span data-ttu-id="2915c-135">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="2915c-135">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2915c-136">若要以程式設計方式建立容器，您也可以使用 REST 應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="2915c-136">To create a container programmatically, you can also use REST APIs.</span></span> <span data-ttu-id="2915c-137">如需詳細資訊，請參閱[建立容器](https://msdn.microsoft.com/library/windowsazure/dd179468.aspx)和[Azure 儲存體服務 REST API 參考](https://msdn.microsoft.com/library/windowsazure/dd179355.aspx)。</span><span class="sxs-lookup"><span data-stu-id="2915c-137">For more information, see [Create Container](https://msdn.microsoft.com/library/windowsazure/dd179468.aspx) and also [Azure Storage Services REST API Reference](https://msdn.microsoft.com/library/windowsazure/dd179355.aspx).</span></span>  
  
 <span data-ttu-id="2915c-138">**下一課：**</span><span class="sxs-lookup"><span data-stu-id="2915c-138">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="2915c-139">第2課。在容器上建立原則並產生共用存取簽章 &#40;SAS&#41; 金鑰</span><span class="sxs-lookup"><span data-stu-id="2915c-139">Lesson 2. Create a policy on container and generate a Shared Access Signature &#40;SAS&#41; key</span></span>](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)  
  
