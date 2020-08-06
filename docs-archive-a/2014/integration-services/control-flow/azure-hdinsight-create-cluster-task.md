---
title: Azure HDInsight 建立叢集工作 | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpcreatecltask.f1
- sql11.dts.designer.afpcreatecltask.f1
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e4029e3a01cbcfe04be5f2879a9b60866bfc867a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688113"
---
# <a name="azure-hdinsight-create-cluster-task"></a><span data-ttu-id="d0441-102">Azure HDInsight 建立叢集工作</span><span class="sxs-lookup"><span data-stu-id="d0441-102">Azure HDInsight Create Cluster Task</span></span>
<span data-ttu-id="d0441-103">[Azure HDInsight 建立叢集工作]  可讓 SSIS 套件在指定的 Azure 訂用帳戶和資源群組中建立 Azure HDInsight 叢集。</span><span class="sxs-lookup"><span data-stu-id="d0441-103">The **Azure HDInsight Create Cluster Task** enables an SSIS package to create an Azure HDInsight cluster in the specified Azure subscription and resource group.</span></span>
  
> [!NOTE]  
> - <span data-ttu-id="d0441-104">建立新的 HDInsight 叢集可能需要 10~20 分鐘。</span><span class="sxs-lookup"><span data-stu-id="d0441-104">Creating a new HDInsight cluster may take 10~20 minutes.</span></span>  
> - <span data-ttu-id="d0441-105">建立與執行 Azure HDInsight 叢集需要支付相關成本。</span><span class="sxs-lookup"><span data-stu-id="d0441-105">There is a cost associated with creating and running an Azure HDInsight cluster.</span></span> <span data-ttu-id="d0441-106">如需詳細資料，請參閱 [HDInsight 價格](https://azure.microsoft.com/pricing/details/hdinsight/)。</span><span class="sxs-lookup"><span data-stu-id="d0441-106">See [HDInsight Pricing](https://azure.microsoft.com/pricing/details/hdinsight/) for details.</span></span>  
  
<span data-ttu-id="d0441-107">若要加入 [Azure HDInsight Create Cluster Task (Azure HDInsight 建立叢集工作)]\*\*\*\*，請將其拖放至 SSIS 設計師，並按兩下或在其上按一下滑鼠右鍵，然後按一下 [編輯]\*\*\*\*，即可看到以下 [Azure HDInsight Create Cluster Task Editor (Azure HDInsight 建立叢集工作編輯器)]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d0441-107">To add an **Azure HDInsight Create Cluster Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure HDInsight Create Cluster Task Editor** dialog box.</span></span>  
  
<span data-ttu-id="d0441-108">下表提供此對話方塊的欄位描述。</span><span class="sxs-lookup"><span data-stu-id="d0441-108">The following table provides a description of the fields in this dialog box.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d0441-109">**欄位**</span><span class="sxs-lookup"><span data-stu-id="d0441-109">**Field**</span></span>|<span data-ttu-id="d0441-110">**說明**</span><span class="sxs-lookup"><span data-stu-id="d0441-110">**Description**</span></span>|  
|<span data-ttu-id="d0441-111">AzureResourceManagerConnection</span><span class="sxs-lookup"><span data-stu-id="d0441-111">AzureResourceManagerConnection</span></span>|<span data-ttu-id="d0441-112">選取現有的 Azure Resource Manager 連線管理員或建立新的連線管理員，用以建立 HDInsight 叢集。</span><span class="sxs-lookup"><span data-stu-id="d0441-112">Select an existing Azure Resource Manager Connection Manager or create a new one that will be used to create the HDInsight cluster.</span></span>|  
|<span data-ttu-id="d0441-113">AzureStorageConnection</span><span class="sxs-lookup"><span data-stu-id="d0441-113">AzureStorageConnection</span></span>|<span data-ttu-id="d0441-114">選取現有的 Azure 儲存體連線管理員，或建立參考 Azure 儲存體帳戶的新連線管理員，該連線管理員會與 HDInsight 叢集建立關聯。</span><span class="sxs-lookup"><span data-stu-id="d0441-114">Select an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account that will be associated with the HDInsight cluster.</span></span>|
|<span data-ttu-id="d0441-115">SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="d0441-115">SubscriptionId</span></span>|<span data-ttu-id="d0441-116">指定 HDInsight 叢集日後建立所在的訂用帳戶識別碼。</span><span class="sxs-lookup"><span data-stu-id="d0441-116">Specify the ID of the subscription the HDInsight cluster will be created in.</span></span>|
|<span data-ttu-id="d0441-117">ResourceGroup</span><span class="sxs-lookup"><span data-stu-id="d0441-117">ResourceGroup</span></span>|<span data-ttu-id="d0441-118">指定 HDInsight 叢集日後建立所在的 Azure 資源群組。</span><span class="sxs-lookup"><span data-stu-id="d0441-118">Specify the Azure resource group the HDInsight cluster will be created in.</span></span>|
|<span data-ttu-id="d0441-119">Location</span><span class="sxs-lookup"><span data-stu-id="d0441-119">Location</span></span>|<span data-ttu-id="d0441-120">指定 HDInsight 叢集的位置。</span><span class="sxs-lookup"><span data-stu-id="d0441-120">Specify the location of the HDInsight cluster.</span></span> <span data-ttu-id="d0441-121">叢集必須建立在和 Azure 儲存體帳戶指定位置相同的位置。</span><span class="sxs-lookup"><span data-stu-id="d0441-121">The cluster must be created in the same location as the Azure Storage Account specified.</span></span>|  
|<span data-ttu-id="d0441-122">ClusterName</span><span class="sxs-lookup"><span data-stu-id="d0441-122">ClusterName</span></span>|<span data-ttu-id="d0441-123">指定要建立的 HDInsight 叢集名稱。</span><span class="sxs-lookup"><span data-stu-id="d0441-123">Specify a name for the HDInsight cluster to be created.</span></span>|  
|<span data-ttu-id="d0441-124">clusterSize</span><span class="sxs-lookup"><span data-stu-id="d0441-124">ClusterSize</span></span>|<span data-ttu-id="d0441-125">指定要在叢集中建立的節點數目。</span><span class="sxs-lookup"><span data-stu-id="d0441-125">Specify the number of nodes to create in the cluster.</span></span>|  
|<span data-ttu-id="d0441-126">BlobContainer</span><span class="sxs-lookup"><span data-stu-id="d0441-126">BlobContainer</span></span>|<span data-ttu-id="d0441-127">指定要與 HDInsight 叢集建立關聯的預設儲存體容器名稱。</span><span class="sxs-lookup"><span data-stu-id="d0441-127">Specify the name of the default storage container to be associated with the HDInsight cluster.</span></span>|  
|<span data-ttu-id="d0441-128">UserName</span><span class="sxs-lookup"><span data-stu-id="d0441-128">UserName</span></span>|<span data-ttu-id="d0441-129">指定連線至 HDInsight 叢集要使用的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="d0441-129">Specify the user name to be used for connecting to the HDInsight cluster.</span></span>|  
|<span data-ttu-id="d0441-130">密碼</span><span class="sxs-lookup"><span data-stu-id="d0441-130">Password</span></span>|<span data-ttu-id="d0441-131">指定連線至 HDInsight 叢集要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="d0441-131">Specify the password to be used for connecting to the HDInsight cluster.</span></span>|
|<span data-ttu-id="d0441-132">SshUserName</span><span class="sxs-lookup"><span data-stu-id="d0441-132">SshUserName</span></span>|<span data-ttu-id="d0441-133">指定從遠端存取使用 SSH 的 HDInsight 叢集時所用的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="d0441-133">Specify the user name used to remotely access the HDInsight cluster using SSH.</span></span>|
|<span data-ttu-id="d0441-134">SshPassword</span><span class="sxs-lookup"><span data-stu-id="d0441-134">SshPassword</span></span>|<span data-ttu-id="d0441-135">指定從遠端存取使用 SSH 的 HDInsight 叢集時所用的密碼。</span><span class="sxs-lookup"><span data-stu-id="d0441-135">Specify the password used to remotely access the HDInsight cluster using SSH.</span></span>|
|<span data-ttu-id="d0441-136">FailIfExists</span><span class="sxs-lookup"><span data-stu-id="d0441-136">FailIfExists</span></span>|<span data-ttu-id="d0441-137">指定若叢集已存在則工作是否會失敗。</span><span class="sxs-lookup"><span data-stu-id="d0441-137">Specify whether the task should fail if the cluster already exists.</span></span>|  
  
> [!NOTE]  
> <span data-ttu-id="d0441-138">HDInsight 叢集與 Azure 儲存體帳戶的位置必須相同。</span><span class="sxs-lookup"><span data-stu-id="d0441-138">The locations of the HDInsight cluster and the Azure Storage Account must be the same.</span></span>
