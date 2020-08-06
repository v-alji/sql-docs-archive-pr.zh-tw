---
title: 設定 DQS 使用參考資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.rds.f1
- sql12.dqs.administration.rdsconfiguration.f1
- sql12.dqs.administration.configuration.createDirectRDS.f1
ms.assetid: fae745e7-57a7-4cbc-8979-56ea8e392e4e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 670e984c2afabb70dece75d94701d7a3a03c95bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687172"
---
# <a name="configure-dqs-to-use-reference-data"></a><span data-ttu-id="ca3d8-102">設定 DQS 使用參考資料</span><span class="sxs-lookup"><span data-stu-id="ca3d8-102">Configure DQS to Use Reference Data</span></span>
  <span data-ttu-id="ca3d8-103">此主題描述如何設定 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 來使用參考資料清理您的資料。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-103">This topic describes how to configure [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) to use reference data for cleansing your data.</span></span> <span data-ttu-id="ca3d8-104">您可以使用來自 Azure Marketplace 的參考資料，或從直接線上協力廠商參考資料提供者。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-104">You could either use reference data from Azure Marketplace or from direct online third-party reference data providers.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="ca3d8-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="ca3d8-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="ca3d8-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="ca3d8-106">Prerequisites</span></span>  
 <span data-ttu-id="ca3d8-107">若要使用服務商場的參考資料，您必須擁有有效的服務商場帳號金鑰。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-107">To use reference data from Marketplace, you must have a valid Marketplace account key.</span></span> <span data-ttu-id="ca3d8-108">如需有關建立 Marketplace 帳戶金鑰的詳細資訊，請參閱 ([建立您的帳戶](https://go.microsoft.com/fwlink/?LinkId=212936) https://go.microsoft.com/fwlink/?LinkId=212936) 。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-108">For detailed information about creating a Marketplace account key, see [Create Your Account](https://go.microsoft.com/fwlink/?LinkId=212936) (https://go.microsoft.com/fwlink/?LinkId=212936).</span></span> <span data-ttu-id="ca3d8-109">您也可以從 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 建立服務商場帳號金鑰，方法是按一下 **首頁畫面中** [管理] **底下的** [組態] [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] ，然後按一下 **[參考資料]** 索引標籤底下的 **[建立 DataMarket 帳戶識別碼]** 。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-109">You can also create a Marketplace account key from within [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] by clicking **Configuration** under **Administration** in the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, and then clicking **Create a DataMarket Account ID** under the **Reference Data** tab.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ca3d8-110">Security</span><span class="sxs-lookup"><span data-stu-id="ca3d8-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ca3d8-111">權限</span><span class="sxs-lookup"><span data-stu-id="ca3d8-111">Permissions</span></span>  
 <span data-ttu-id="ca3d8-112">您必須擁有 DQS_MAIN 資料庫的 dqs_administrator 角色，才能在 DQS 中設定參考資料服務。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-112">You must have the dqs_administrator role on the DQS_MAIN database to configure reference data service settings in DQS.</span></span>  
  
##  <a name="configure-dqs-to-use-reference-data-from-marketplace"></a><a name="Marketplace"></a> <span data-ttu-id="ca3d8-113">設定 DQS 使用服務商場中的參考資料</span><span class="sxs-lookup"><span data-stu-id="ca3d8-113">Configure DQS to Use Reference Data from Marketplace</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="ca3d8-114">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-114">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="ca3d8-115">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，按一下 **[管理]** 底下的 **[組態]**。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-115">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, under **Administration**, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="ca3d8-116">在 **[參考資料]** 索引標籤的 **[網路設定]** 區域底下，於 **[Proxy 伺服器]** 和 **[通訊埠]** 方塊中輸入適當的值 (如果您或您的組織使用 Proxy 伺服器連接至網際網路)。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-116">In the **Reference Data** tab, under the **Network Settings** area, type appropriate values in the **Proxy Server** and **Port** boxes if you or your organization uses proxy server to connect to the Internet.</span></span>  
  
4.  <span data-ttu-id="ca3d8-117">在 **[DataMarket 帳戶識別碼]** 方塊中指定服務商場帳號金鑰，然後按一下 **[驗證 DataMarket 帳戶識別碼]** 圖示來驗證此帳號金鑰。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-117">Specify the Marketplace account key in the **DataMarket Account ID** box, and click the **Validate DataMarket Account ID** icon to validate the account key.</span></span> <span data-ttu-id="ca3d8-118">隨即出現一則訊息，顯示指定的服務商場帳號金鑰是否有效。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-118">A message appears to display whether the specified Marketplace account key is valid.</span></span>  
  
 <span data-ttu-id="ca3d8-119">您現在已經準備好開始在 DQS 中使用來自服務商場的參考資料服務 (這些服務是針對指定的服務商場帳號金鑰所訂閱)。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-119">You are now ready to use the reference data services from Marketplace in DQS that are subscribed for the specified Marketplace account key.</span></span>  
  
##  <a name="configure-dqs-to-use-reference-data-from-direct-online-third-party-reference-data-providers"></a><a name="ThirdParty"></a> <span data-ttu-id="ca3d8-120">設定 DQS 使用直接線上協力廠商參考資料提供者所提供的參考資料</span><span class="sxs-lookup"><span data-stu-id="ca3d8-120">Configure DQS to Use Reference Data from Direct Online Third-Party Reference Data Providers</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="ca3d8-121">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-121">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="ca3d8-122">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，按一下 **[管理]** 底下的 **[組態]**。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-122">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, under **Administration**, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="ca3d8-123">在 **[參考資料]** 索引標籤的 **[網路設定]** 區域底下，於 **[Proxy 伺服器]** 和 **[通訊埠]** 方塊中輸入適當的值 (如果您或您的組織使用 Proxy 伺服器連接至網際網路)。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-123">In the **Reference Data** tab, under the **Network Settings** area, type appropriate values in the **Proxy Server** and **Port** boxes if you or your organization uses proxy server to connect to the Internet.</span></span>  
  
4.  <span data-ttu-id="ca3d8-124">在 **[直接線上協力廠商參考資料服務設定]** 區域中按一下 **[加入新的參考資料服務提供者]** 圖示。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-124">In the **Direct Online 3rd Party Reference Data Service Settings** area, click the **Add new reference data service provider** icon.</span></span>  
  
5.  <span data-ttu-id="ca3d8-125">在 **[建立新的直接線上協力廠商參考資料服務提供者]** 對話方塊中，指定以下詳細資料：</span><span class="sxs-lookup"><span data-stu-id="ca3d8-125">In the **Create New Direct Online 3rd Party Reference Data Service Provider** dialog box, specify the following details:</span></span>  
  
    1.  <span data-ttu-id="ca3d8-126">在 **[名稱]** 方塊中，輸入新的直接參考資料服務提供者的名稱。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-126">In the **Name** box, type a name of the new direct reference data service provider.</span></span>  
  
    2.  <span data-ttu-id="ca3d8-127">(選擇性) 在 **[描述]** 方塊中，輸入新的直接參考資料服務提供者的描述。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-127">(Optional) In the **Description** box, type a description of the new direct reference data service provider.</span></span>  
  
    3.  <span data-ttu-id="ca3d8-128">在 **[類別目錄]** 方塊中，輸入新的直接參考資料服務提供者所提供之資料的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-128">In the **Category** box, type the category of the data provided by the new direct reference data service provider.</span></span>  
  
    4.  <span data-ttu-id="ca3d8-129">在 [結構描述] 方塊中，指定可定義要從直接參考資料服務提供者使用之欄位字串 (資料行名稱) 的結構描述。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-129">In the Schema box, specify the schema that defines the string of fields (column names) to be used from the direct reference data service provider.</span></span> <span data-ttu-id="ca3d8-130">欄位名稱不能包含空格，而且應該以逗號分隔欄位。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-130">A field name should not contain a space, and the fields should be separated by commas.</span></span> <span data-ttu-id="ca3d8-131">例如：`FirstName, LastName, City, State`。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-131">For example: `FirstName, LastName, City, State`.</span></span>  
  
    5.  <span data-ttu-id="ca3d8-132">在 **[URI]** 方塊中，輸入直接參考資料服務提供者的 URI。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-132">In the **URI** box, type the URI of the direct reference data service provider.</span></span> <span data-ttu-id="ca3d8-133">DQS 中只允許安全的 URI (以 "https://" 開頭的位址)。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-133">Only secure URIs (address starting with "https://") are allowed in DQS.</span></span>  
  
    6.  <span data-ttu-id="ca3d8-134">在 **[最大批次大小]** 方塊中，輸入將傳送給參考資料服務提供者進行清理之每個批次的最大記錄數目。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-134">In the **Max Batch Size** box, type the maximum number of records per batch that will be sent to the reference data service provider for cleansing.</span></span> <span data-ttu-id="ca3d8-135">每個批次最多可以針對清理活動指定 100 筆記錄。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-135">A maximum of 100 records per batch can be specified for the cleansing activity.</span></span>  
  
    7.  <span data-ttu-id="ca3d8-136">在 **[帳戶識別碼]** 方塊中，輸入參考資料服務提供者之訂閱者的帳戶識別碼。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-136">In the **Account ID** box, type the account ID of the subscriber with the reference data service provider.</span></span>  
  
6.  <span data-ttu-id="ca3d8-137">按一下 **[確定]** 儲存資料，並關閉 **[建立新的直接線上協力廠商參考資料服務提供者]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-137">Click **OK** to save the data, and close the **Create New Direct Online 3rd Party Reference Data Service Provider** dialog box.</span></span> <span data-ttu-id="ca3d8-138">新加入的直接線上協力廠商參考資料提供者便可以在 DQS 中的 **[直接參考資料服務提供者]** 方格內使用。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-138">The newly added direct online third party reference data provider becomes available in the **Direct Reference Data Service Providers Grid** in DQS.</span></span>  
  
 <span data-ttu-id="ca3d8-139">您現在已經準備好開始在 DQS 中使用來自新設定的直接線上協力廠商參考資料服務提供者所提供的參考資料服務。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-139">You are now ready to use the reference data services from the newly configured direct online third-party reference data service provider in DQS.</span></span>  
  
##  <a name="follow-up-after-configuring-dqs-to-use-reference-data"></a><a name="FollowUp"></a><span data-ttu-id="ca3d8-140">後續操作：設定 DQS 使用參考資料之後</span><span class="sxs-lookup"><span data-stu-id="ca3d8-140">Follow Up: After Configuring DQS to use Reference Data</span></span>  
 <span data-ttu-id="ca3d8-141">您現在必須將必要的知識庫定義域對應到您剛才設定的資料提供者所提供的參考資料。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-141">You must now map the required knowledge base domains to the reference data available from the data providers you just configured.</span></span> <span data-ttu-id="ca3d8-142">若要這樣做，請參閱[將定義域或複合定義域附加至參考資料](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)。</span><span class="sxs-lookup"><span data-stu-id="ca3d8-142">To do so, see [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).</span></span>  
  
  
