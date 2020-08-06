---
title: 建立知識庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.selectkb.f1
- sql12.dqs.kb.newkb.f1
ms.assetid: 2733a284-975f-4650-abcc-cc2aad074cab
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 281fa663362cc4462cd4e32839c1eaf6908394e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592268"
---
# <a name="create-a-knowledge-base"></a><span data-ttu-id="852c8-102">建立知識庫</span><span class="sxs-lookup"><span data-stu-id="852c8-102">Create a Knowledge Base</span></span>
  <span data-ttu-id="852c8-103">本主題描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中建立知識庫，並預備此知識庫進行定義域管理、知識探索或是加入比對原則。</span><span class="sxs-lookup"><span data-stu-id="852c8-103">This topic describes how to create a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS), and prepare it for domain management, knowledge discovery, or adding a matching policy.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="852c8-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="852c8-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="852c8-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="852c8-105">Prerequisites</span></span>  
 <span data-ttu-id="852c8-106">若要建立知識庫，您必須已經安裝 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 和 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="852c8-106">To create a knowledge base, you must have installed [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] and [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="852c8-107">Security</span><span class="sxs-lookup"><span data-stu-id="852c8-107">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="852c8-108">權限</span><span class="sxs-lookup"><span data-stu-id="852c8-108">Permissions</span></span>  
 <span data-ttu-id="852c8-109">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 或 dqs_administrator 角色，才能建立知識庫。</span><span class="sxs-lookup"><span data-stu-id="852c8-109">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to create a knowledge base.</span></span>  
  
##  <a name="create-a-knowledge-base"></a><a name="Createaknowledgebase"></a><span data-ttu-id="852c8-110">建立知識庫</span><span class="sxs-lookup"><span data-stu-id="852c8-110">Create a knowledge base</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="852c8-111">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="852c8-111">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="852c8-112">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面上，按一下 **[新增知識庫]**。</span><span class="sxs-lookup"><span data-stu-id="852c8-112">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **New knowledge base**.</span></span>  
  
3.  <span data-ttu-id="852c8-113">輸入新知識庫的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="852c8-113">Enter a name and description for the new knowledge base.</span></span>  
  
4.  <span data-ttu-id="852c8-114">在 **[建立知識庫來源]** 中，選取要做為知識庫基礎的來源：</span><span class="sxs-lookup"><span data-stu-id="852c8-114">In **Create knowledge base from**, select what to base the knowledge base on:</span></span>  
  
    -   <span data-ttu-id="852c8-115">如果您不想要使用現有的知識庫或資料檔案做為新知識庫的基礎，請選取 **[無]** 。</span><span class="sxs-lookup"><span data-stu-id="852c8-115">Select **None** if you do not want to base the new knowledge base on an existing knowledge base or data file.</span></span>  
  
    -   <span data-ttu-id="852c8-116">若要使用已經在 **上建立的知識庫或預設知識庫做為新知識庫的基礎，請選取** [現有知識庫] [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="852c8-116">Select **Existing Knowledge Base** to base the new knowledge base on a knowledge base that has already been created on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], or on the default knowledge base.</span></span> <span data-ttu-id="852c8-117">從 **[選取知識庫]** 下拉式清單中選取知識庫，或按一下 **[瀏覽]** 顯示 **[選取知識庫]** 對話方塊、選取要做為新知識庫基礎的現有知識庫，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="852c8-117">Select the knowledge base from the **Select Knowledge Base** drop-down list, or click **Browse** to display the **Select a Knowledge Base** dialog box, select an existing knowledge base to base the new knowledge base on, and then click **OK**.</span></span> <span data-ttu-id="852c8-118">當您從資料表中選取知識庫時，該知識庫的定義域和比對規則就會顯示在對話方塊的右窗格中。</span><span class="sxs-lookup"><span data-stu-id="852c8-118">When you select a knowledge base from the tablet, the domains and matching rules in the knowledge base will be displayed in the right-hand pane of the dialog box.</span></span> <span data-ttu-id="852c8-119">您也可以選取 [DQS 資料] \*\*\*\* 知識庫，這是預設知識庫，其中包含與美國公司、地址和政黨資料有關的一般現成定義域及知識。</span><span class="sxs-lookup"><span data-stu-id="852c8-119">You can also select the **DQS Data** knowledge base, which is the default knowledge base that contains common out-of-the-box domains and knowledge related to U.S. company, address, and party data.</span></span>  
  
    -   <span data-ttu-id="852c8-120">選取 **[從 DQS 檔案匯入]** ，即可使用 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]上的 DQS 檔案做為新知識庫的基礎。</span><span class="sxs-lookup"><span data-stu-id="852c8-120">Select **Import from DQS File** to base the new knowledge base on a DQS file on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span> <span data-ttu-id="852c8-121">按一下 **[瀏覽]**、選取副檔名為 .dqs 的 DQS 資料檔案，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="852c8-121">Click **Browse**, select a DQS data file with an extension of .dqs, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="852c8-122">在 **[選取活動]** 中，選取您想要在新知識庫上執行的活動：</span><span class="sxs-lookup"><span data-stu-id="852c8-122">In **Select Activity**, select the activity that you want to perform on the new knowledge base:</span></span>  
  
    -   <span data-ttu-id="852c8-123">選取 **[定義域管理]** 建立知識庫，並且進入用來修改知識庫中定義域的畫面。</span><span class="sxs-lookup"><span data-stu-id="852c8-123">Select **Domain Management** to create the knowledge base and enter the screens that you use to modify the domains in the knowledge base.</span></span>  
  
    -   <span data-ttu-id="852c8-124">選取 **[知識探索]** 建立知識庫，並且進入用來分析資料樣本並以結果擴展知識庫定義域的精靈。</span><span class="sxs-lookup"><span data-stu-id="852c8-124">Select **Knowledge Discovery** to create the knowledge base and enter the wizard that you use to analyze a data sample and populate the domains of the knowledge base with the results.</span></span>  
  
    -   <span data-ttu-id="852c8-125">選取 **[比對原則]** 建立比對原則，並將其加入至知識庫。</span><span class="sxs-lookup"><span data-stu-id="852c8-125">Select **Matching Policy** to create a matching policy and add it to the knowledge base.</span></span>  
  
6.  <span data-ttu-id="852c8-126">按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="852c8-126">Click **Create**.</span></span>  
  
##  <a name="follow-up-after-creating-a-knowledge-base"></a><a name="FollowUp"></a> <span data-ttu-id="852c8-127">後續操作：建立知識庫之後</span><span class="sxs-lookup"><span data-stu-id="852c8-127">Follow Up: After Creating a Knowledge Base</span></span>  
 <span data-ttu-id="852c8-128">建立知識庫之後，系統會顯示可用來執行知識探索的精靈、建立比對原則的精靈或是執行定義域管理的頁面。</span><span class="sxs-lookup"><span data-stu-id="852c8-128">After you create a knowledge base, you are presented with a wizard that you can use to perform knowledge discovery, a wizard to create a matching policy, or pages to perform domain management.</span></span> <span data-ttu-id="852c8-129">如需有關知識探索、定義域管理或比對原則的詳細資訊，請參閱[執行知識探索](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理定義域](../../2014/data-quality-services/managing-a-domain.md)或[建立比對原則](../../2014/data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="852c8-129">For more information about the knowledge discovery, domain management, or matching policy, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
  
