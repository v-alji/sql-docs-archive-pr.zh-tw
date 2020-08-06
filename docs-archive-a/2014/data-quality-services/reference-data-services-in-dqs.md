---
title: DQS 中的 Reference Data Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ef217717-6d05-443e-af26-44dc745a349d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d4ed286b5834d81f775ee097672bfbc861c0b369
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596290"
---
# <a name="reference-data-services-in-dqs"></a><span data-ttu-id="b30c1-102">DQS 中的 Reference Data Services</span><span class="sxs-lookup"><span data-stu-id="b30c1-102">Reference Data Services in DQS</span></span>
  <span data-ttu-id="b30c1-103">參考資料指的是一組精確且完整的相關或已分類的全域資料 (在企業界限範圍之外)，這些資料是在可靠的公用網域或是由優質商業內容提供者所提供。</span><span class="sxs-lookup"><span data-stu-id="b30c1-103">Reference data refers to an accurate and complete set of related or categorized global data (beyond the boundaries of an enterprise) that is available at trusted public domains or from premium commercial content providers.</span></span>  
  
 <span data-ttu-id="b30c1-104">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中的參考資料服務功能可讓您訂閱協力廠商參考資料提供者，並針對高品質資料來驗證您的商務資料，輕鬆地清理及豐富這些商務資料。</span><span class="sxs-lookup"><span data-stu-id="b30c1-104">The Reference Data Service feature in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) enables you to subscribe to third-party reference data providers, and to easily cleanse and enrich your business data by validating it against their high-quality data.</span></span> <span data-ttu-id="b30c1-105">您可以使用 DQS 中主要 Data Quality Services 提供者的服務，在清除程序中標準化、更正或豐富您的資料。</span><span class="sxs-lookup"><span data-stu-id="b30c1-105">You can use services from leading data quality service providers from within DQS to standardize, correct, or enrich your data during the cleansing process.</span></span> <span data-ttu-id="b30c1-106">例如，您可以針對參考資料使用區碼或郵遞區號的清單，以驗證客戶的地址。</span><span class="sxs-lookup"><span data-stu-id="b30c1-106">For example, you can use a list of area codes or zip codes against the reference data to validate addresses of your customers.</span></span>  
  
 <span data-ttu-id="b30c1-107">參考資料服務功能具有以下優點：</span><span class="sxs-lookup"><span data-stu-id="b30c1-107">The Reference Data Service feature has the following benefits:</span></span>  
  
-   <span data-ttu-id="b30c1-108">參考資料可讓您將資料與協力廠商擔保的資料做比較來確保資料的品質。</span><span class="sxs-lookup"><span data-stu-id="b30c1-108">Reference data enables you to ensure the quality of your data by comparing it to data guaranteed by a third-party company.</span></span>  
  
-   <span data-ttu-id="b30c1-109">參考資料程序會併入 DQS 知識庫建立和資料品質專案中，好讓您建立全面性的資料品質程序。</span><span class="sxs-lookup"><span data-stu-id="b30c1-109">The reference data process is incorporated into DQS knowledge base building and a data quality project, enabling you to institute a comprehensive data quality process.</span></span>  
  
-   <span data-ttu-id="b30c1-110">支援使用來自 Azure Marketplace 的參考資料，以及直接從協力廠商參考資料提供者。</span><span class="sxs-lookup"><span data-stu-id="b30c1-110">Supports using reference data from Azure Marketplace as well as directly from third party reference data providers.</span></span>  
  
##  <a name="using-reference-data-from-azure-marketplace"></a><a name="Marketplace"></a><span data-ttu-id="b30c1-111">使用來自 Azure Marketplace 的參考資料</span><span class="sxs-lookup"><span data-stu-id="b30c1-111">Using Reference Data from Azure Marketplace</span></span>  
 <span data-ttu-id="b30c1-112">DQS 支援使用來自 Azure Marketplace 的參考資料，讓內容提供者透過 Marketplace 提供參考資料服務。</span><span class="sxs-lookup"><span data-stu-id="b30c1-112">DQS supports using reference data from Azure Marketplace to enable content providers to provide reference data services through Marketplace.</span></span> <span data-ttu-id="b30c1-113">服務商場是 Microsoft 的服務，可針對高品質資料和應用程式提供單一服務商場和傳遞通道，並提供雲端服務。</span><span class="sxs-lookup"><span data-stu-id="b30c1-113">Marketplace is a service from Microsoft that provides a single marketplace and delivery channel for high-quality data and applications as cloud services.</span></span> <span data-ttu-id="b30c1-114">如需 Marketplace 的詳細資訊，請參閱[瞭解 Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/)。</span><span class="sxs-lookup"><span data-stu-id="b30c1-114">For more information about Marketplace, see [Learn About Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/).</span></span>  
  
 <span data-ttu-id="b30c1-115">服務商場與 DQS 之間的順暢整合會簡化與探索、瀏覽及取得 DQS 內的資料品質專案資訊相關的步驟。</span><span class="sxs-lookup"><span data-stu-id="b30c1-115">The seamless integration between Marketplace and DQS simplifies the steps associated with discovering, exploring, and acquiring information for data quality projects from within DQS.</span></span> <span data-ttu-id="b30c1-116">這些資料是從 DQS 取用，而且有助於 DQS 使用者以創新方式將 DQS、服務商場和參考資料服務提供者結合在一起，以達成高資料品質。</span><span class="sxs-lookup"><span data-stu-id="b30c1-116">The data is consumed from DQS, and helps DQS users achieve high data quality by bringing together DQS, Marketplace, and reference data service providers in an innovative way.</span></span>  
  
 <span data-ttu-id="b30c1-117">若要針對清理活動在 DQS 中使用服務商場的參考資料，您必須擁有服務商場帳號金鑰。</span><span class="sxs-lookup"><span data-stu-id="b30c1-117">To use reference data from Marketplace in DQS for the cleansing activity, you must have a Marketplace account key.</span></span> <span data-ttu-id="b30c1-118">建立服務商場帳號金鑰是免費的，只有當您訂閱付費的資料集時才需要付費。</span><span class="sxs-lookup"><span data-stu-id="b30c1-118">Creating a Marketplace account key is free, and you pay only if you subscribe to paid datasets.</span></span> <span data-ttu-id="b30c1-119">訂閱及使用免費的資料集不需要支付任何費用。</span><span class="sxs-lookup"><span data-stu-id="b30c1-119">There is no charge for subscribing to, and using free datasets.</span></span> <span data-ttu-id="b30c1-120">如需有關建立 Marketplace 帳戶金鑰的詳細資訊，請參閱 ([建立您的帳戶](https://go.microsoft.com/fwlink/?LinkId=212936) https://go.microsoft.com/fwlink/?LinkId=212936) 。</span><span class="sxs-lookup"><span data-stu-id="b30c1-120">For detailed information about creating a Marketplace account key, see [Create Your Account](https://go.microsoft.com/fwlink/?LinkId=212936) (https://go.microsoft.com/fwlink/?LinkId=212936).</span></span>  
  
 <span data-ttu-id="b30c1-121">此外，您可以從 DQS 執行下列服務商場活動：</span><span class="sxs-lookup"><span data-stu-id="b30c1-121">Additionally, you can perform the following Marketplace activities from within DQS:</span></span>  
  
-   <span data-ttu-id="b30c1-122">瀏覽服務商場中的資料集。</span><span class="sxs-lookup"><span data-stu-id="b30c1-122">Browse data sets in Marketplace.</span></span>  
  
-   <span data-ttu-id="b30c1-123">建立服務商場帳號金鑰。</span><span class="sxs-lookup"><span data-stu-id="b30c1-123">Create a Marketplace account key.</span></span>  
  
-   <span data-ttu-id="b30c1-124">管理您的服務商場帳戶詳細資料，例如帳號金鑰及資料提供者訂閱。</span><span class="sxs-lookup"><span data-stu-id="b30c1-124">Manage your Marketplace account details such as account keys and subscriptions to data providers.</span></span>  
  
 <span data-ttu-id="b30c1-125">在 **中，您可以在** [組態] **畫面的** [參考資料] [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]索引標籤上執行這些活動。</span><span class="sxs-lookup"><span data-stu-id="b30c1-125">You can perform these activities in the **Reference Data** tab of the **Configuration** screen in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
##  <a name="using-reference-data-directly-from-the-third-party-reference-data-providers"></a><a name="Direct"></a> <span data-ttu-id="b30c1-126">使用直接從協力廠商參考資料提供者所提供的參考資料</span><span class="sxs-lookup"><span data-stu-id="b30c1-126">Using Reference Data Directly from the Third Party Reference Data Providers</span></span>  
 <span data-ttu-id="b30c1-127">如果您未連接到網際網路而無法使用服務商場，DQS 也支援您的組織網路中所提供之資料提供者的直接連接。</span><span class="sxs-lookup"><span data-stu-id="b30c1-127">If you are not connected to the Internet and therefore cannot use Marketplace, DQS also supports direct connection to data providers that are available within your organization's network.</span></span> <span data-ttu-id="b30c1-128">若要使用直接線上協力廠商參考資料提供者所提供的參考資料，您必須為 DQS 中的資料提供者建立記錄。</span><span class="sxs-lookup"><span data-stu-id="b30c1-128">To use reference data from direct online third-party reference data providers, you have to create a record for the data provider in DQS.</span></span>  
  
##  <a name="how-to-cleanse-data-by-using-the-reference-data"></a><a name="HowToCleanse"></a> <span data-ttu-id="b30c1-129">如何使用參考資料清理資料</span><span class="sxs-lookup"><span data-stu-id="b30c1-129">How to Cleanse Data by Using the Reference Data</span></span>  
 <span data-ttu-id="b30c1-130">使用參考資料在 DQS 中清理資料包括以下三個步驟：</span><span class="sxs-lookup"><span data-stu-id="b30c1-130">Cleansing your data in DQS using reference data includes the following three steps:</span></span>  
  
1.  <span data-ttu-id="b30c1-131">**在 DQS 中設定參考資料提供者詳細資料**：在您可以在 DQS 中使用參考資料之前，您必須先在 DQS 中設定參考資料服務詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b30c1-131">**Configuring the reference data provider details in DQS**: Before you can use reference data in DQS, you must configure reference data service details in DQS.</span></span>  
  
    1.  <span data-ttu-id="b30c1-132">如果您使用服務商場，請提供有效的服務商場帳號金鑰、瀏覽至服務商場中的 [Data Quality Services](../data-quality-services/data-quality-services.md) 資料類別目錄，並訂閱所需的提供者。</span><span class="sxs-lookup"><span data-stu-id="b30c1-132">If you are using Marketplace, provide a valid Marketplace account key, browse to the [Data Quality Services](../data-quality-services/data-quality-services.md) data category in Marketplace, and subscribe to the required providers.</span></span>  
  
    2.  <span data-ttu-id="b30c1-133">如果您使用直接線上參考資料提供者，您必須先在 DQS 中加入直接參考資料提供者詳細資料，然後才可以使用它。</span><span class="sxs-lookup"><span data-stu-id="b30c1-133">If you are using a direct online reference data provider, you must add direct reference data provider details in DQS before you can use it.</span></span>  
  
     <span data-ttu-id="b30c1-134">在 DQS 中設定參考資料提供者詳細資料對於特定資料提供者而言是一次性的活動。</span><span class="sxs-lookup"><span data-stu-id="b30c1-134">Configuring the reference data provider details in DQS is one time activity for a particular data provider.</span></span> <span data-ttu-id="b30c1-135">只有 DQS 管理員可以在 DQS 中設定參考資料設定。</span><span class="sxs-lookup"><span data-stu-id="b30c1-135">Only DQS administrators can configure reference data settings in DQS.</span></span>  
  
2.  <span data-ttu-id="b30c1-136">**將知識庫中的定義域/複合定義域對應至參考資料服務**：將定義域/複合定義域對應至步驟 1 所訂閱/加入的適當參考資料服務。</span><span class="sxs-lookup"><span data-stu-id="b30c1-136">**Map a domain/composite domain in a knowledge base to the reference data service**: Map a domain/composite domain to the appropriate reference data service subscribed/added in step 1.</span></span>  
  
3.  <span data-ttu-id="b30c1-137">**在資料品質專案中將對應的定義域用於清理活動**：在針對 **[清理]** 活動建立資料品質專案時，請選取包含定義域/複合定義域的知識庫 (這些定義域與步驟 2 中的參考資料服務相對應)，並執行清理活動。</span><span class="sxs-lookup"><span data-stu-id="b30c1-137">**Use the Mapped Domains for the Cleansing activity in a data quality project**: While creating a data quality project for the **Cleansing** activity, select the knowledge base that contains domains/composite domains mapped with reference data services in step 2, and perform the cleansing activity.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b30c1-138">相關工作</span><span class="sxs-lookup"><span data-stu-id="b30c1-138">Related Tasks</span></span>  
  
|<span data-ttu-id="b30c1-139">工作描述</span><span class="sxs-lookup"><span data-stu-id="b30c1-139">Task Description</span></span>|<span data-ttu-id="b30c1-140">主題</span><span class="sxs-lookup"><span data-stu-id="b30c1-140">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="b30c1-141">描述如何設定 DQS 使用服務商場或直接線上協力廠商資料提供者所提供的參考資料服務。</span><span class="sxs-lookup"><span data-stu-id="b30c1-141">Describes how to configure DQS to use reference data services from Marketplace or direct third-party online data providers.</span></span>|[<span data-ttu-id="b30c1-142">設定 DQS 使用參考資料</span><span class="sxs-lookup"><span data-stu-id="b30c1-142">Configure DQS to Use Reference Data</span></span>](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md)|  
|<span data-ttu-id="b30c1-143">描述如何將知識庫中的定義域/複合定義域對應至參考資料服務。</span><span class="sxs-lookup"><span data-stu-id="b30c1-143">Describes how to map a domain/composite domain in a knowledge base to a reference data service.</span></span>|[<span data-ttu-id="b30c1-144">將定義域或複合定義域附加至參考資料</span><span class="sxs-lookup"><span data-stu-id="b30c1-144">Attach a Domain or Composite Domain to Reference Data</span></span>](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)|  
|<span data-ttu-id="b30c1-145">描述如何使用參考資料服務清理資料。</span><span class="sxs-lookup"><span data-stu-id="b30c1-145">Describes how to cleanse data using reference data service.</span></span>|[<span data-ttu-id="b30c1-146">使用參考資料 &#40;外部&#41; 知識清理資料</span><span class="sxs-lookup"><span data-stu-id="b30c1-146">Cleanse Data Using Reference Data &#40;External&#41; Knowledge</span></span>](../../2014/data-quality-services/cleanse-data-using-reference-data-external-knowledge.md)|  
  
  
