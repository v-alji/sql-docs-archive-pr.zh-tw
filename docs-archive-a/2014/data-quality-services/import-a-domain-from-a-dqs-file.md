---
title: 從 .dqs 檔案匯入定義域 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fabd88b0-22b3-4543-a993-6d5b202ded80
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2e08837fd0b160732b506af77a6cf4a1cbe1966f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700261"
---
# <a name="import-a-domain-from-a-dqs-file"></a><span data-ttu-id="dc46f-102">從 .dqs 檔案匯入定義域</span><span class="sxs-lookup"><span data-stu-id="dc46f-102">Import a Domain from a .dqs File</span></span>
  <span data-ttu-id="dc46f-103">此主題描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中將 .dqs 檔案中的定義域匯入現有的知識庫中。</span><span class="sxs-lookup"><span data-stu-id="dc46f-103">This topic describes how to import a domain from a .dqs file into an existing knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="dc46f-104">.dqs 資料檔的建立方式是從 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 應用程式匯出定義域或知識庫。</span><span class="sxs-lookup"><span data-stu-id="dc46f-104">A .dqs data file is created by exporting a domain or knowledge base from the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application.</span></span> <span data-ttu-id="dc46f-105">.dqs 資料檔已加密，所以無法檢視。</span><span class="sxs-lookup"><span data-stu-id="dc46f-105">A .dqs data file is encrypted, so cannot be viewed.</span></span>  
  
 <span data-ttu-id="dc46f-106">使用 .dqs 資料檔匯出某個知識庫中的定義域，然後將它匯入另一個知識庫將會簡化知識產生程序，以節省時間與精力。</span><span class="sxs-lookup"><span data-stu-id="dc46f-106">Using a .dqs data file to export a domain from one knowledge base and then import it to another knowledge base simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="dc46f-107">這樣可讓您將定義域和定義域的知識與其他人分享，以節省他們的時間。</span><span class="sxs-lookup"><span data-stu-id="dc46f-107">It enables you to share a domain and its knowledge with others, saving them time.</span></span> <span data-ttu-id="dc46f-108">您可以匯入一個單一定義域或一個複合定義域 (包含多個單一定義域)。</span><span class="sxs-lookup"><span data-stu-id="dc46f-108">You can import either one single domain or one composite domain (containing multiple single domains).</span></span> <span data-ttu-id="dc46f-109">包含單一定義域的 .dqs 檔案包括所有定義域資料，其中包括定義域屬性、值和規則資料，但不包括對應的參考資料資訊。</span><span class="sxs-lookup"><span data-stu-id="dc46f-109">A .dqs file containing a single domain includes all domain data including domain properties, values, and rules data, except for the mapped reference data information.</span></span> <span data-ttu-id="dc46f-110">含有複合定義域的 .dqs 檔案包括所有複合定義域資料，其中包括複合定義域內所容納之單一定義域的所有定義域資料，以及複合定義域屬性、值關聯和 CD 規則，但不包括對應的參考資料。</span><span class="sxs-lookup"><span data-stu-id="dc46f-110">A .dqs file containing a composite domain includes all composite domain data, including all domain data for the singles domains that are contained within the composite domain, and the composite domain properties, value relations, and CD rules, except for the mapped reference data.</span></span> <span data-ttu-id="dc46f-111">已發行和未發行的資料都將匯入。</span><span class="sxs-lookup"><span data-stu-id="dc46f-111">Published and unpublished data will be imported.</span></span>  
  
 <span data-ttu-id="dc46f-112">當您匯入定義域時，此定義域的名稱依然與一開始匯出的定義域名稱相同，除非此定義域名稱已經存在 (此時 DQS 會在名稱中附加 "_1")。</span><span class="sxs-lookup"><span data-stu-id="dc46f-112">When you import a domain, the name of the domain remains the same as the name of the domain that was originally exported, unless the domain name already exists, in which case DQS will append "_1" to the name.</span></span> <span data-ttu-id="dc46f-113">如果您匯入的複合定義域所包含的個別定義域與現有定義域同名，這個情況也會成立。</span><span class="sxs-lookup"><span data-stu-id="dc46f-113">This is also true if you import a composite domain that contains an individual domain with the same name as an existing domain.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="dc46f-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="dc46f-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="dc46f-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="dc46f-115">Prerequisites</span></span>  
 <span data-ttu-id="dc46f-116">若要從 .dqs 檔案匯入定義域，您必須已將一個單一定義域或是一個複合定義域 (包含多個單一定義域) 匯出到 .dqs 檔案。</span><span class="sxs-lookup"><span data-stu-id="dc46f-116">To import a domain from a .dqs file, you must have already exported one single domain or one composite domain (containing multiple single domains) into the .dqs file.</span></span> <span data-ttu-id="dc46f-117">此 .dqs 檔案只能包含一個定義域。</span><span class="sxs-lookup"><span data-stu-id="dc46f-117">The .dqs file must only contain one domain.</span></span> <span data-ttu-id="dc46f-118">您也必須已建立及開啟知識庫，才能將定義域匯入其中。</span><span class="sxs-lookup"><span data-stu-id="dc46f-118">You must also have created and opened a knowledge base to import the domain into.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="dc46f-119">Security</span><span class="sxs-lookup"><span data-stu-id="dc46f-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="dc46f-120">權限</span><span class="sxs-lookup"><span data-stu-id="dc46f-120">Permissions</span></span>  
 <span data-ttu-id="dc46f-121">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 角色或 dqs_administrator 角色，才能從 .dqs 資料檔匯入定義域。</span><span class="sxs-lookup"><span data-stu-id="dc46f-121">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to import a domain from a .dqs data file.</span></span>  
  
##  <a name="import-a-domain-from-a-dqs-file"></a><a name="Import"></a><span data-ttu-id="dc46f-122">從 dqs 檔案匯入定義域</span><span class="sxs-lookup"><span data-stu-id="dc46f-122">Import a domain from a .dqs file</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="dc46f-123">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="dc46f-123">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="dc46f-124">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，於 [定義域管理] 活動中開啟知識庫。</span><span class="sxs-lookup"><span data-stu-id="dc46f-124">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="dc46f-125">按一下 **[從資料檔匯入定義域]** 圖示。</span><span class="sxs-lookup"><span data-stu-id="dc46f-125">Click the **Import Domain from data file** icon.</span></span>  
  
4.  <span data-ttu-id="dc46f-126">在 **[從資料檔匯入]** 對話方塊中，移至包含您要匯入之檔案的資料夾，然後選取檔案 (檔案類型為 DQS 檔案)，再按一下 **[開啟]**。</span><span class="sxs-lookup"><span data-stu-id="dc46f-126">In the **Import from Data File** dialog box, move to the folder that you want to import the file from, select the file (of type DQS File), and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="dc46f-127">在 **[匯入定義域]** 對話方塊中，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="dc46f-127">In the **Import Domain** dialog box, click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dc46f-128">只有當匯入的來源 .dqs 檔案只包含一個單一定義域或是一個複合定義域 (包含多個單一定義域) 時，匯入作業才會成功。</span><span class="sxs-lookup"><span data-stu-id="dc46f-128">The import operation will succeed only if the .dqs file that you are importing from contains only one single domain or one composite domain (containing multiple single domains).</span></span>  
  
6.  <span data-ttu-id="dc46f-129">確認您匯入的定義域顯示在 **[定義域]** 清單中。</span><span class="sxs-lookup"><span data-stu-id="dc46f-129">Verify that the domain that you imported is displayed in the **Domain** list.</span></span> <span data-ttu-id="dc46f-130">如果您匯入複合定義域，請確認此複合定義域以及其中包含的單一定義域全都位於 **[定義域]** 清單中。</span><span class="sxs-lookup"><span data-stu-id="dc46f-130">If you imported a composite domain, verify that the composite domain and the single domains contained in it are all in the **Domain** list.</span></span>  
  
##  <a name="follow-up-after-importing-a-domain-from-a-dqs-file"></a><a name="FollowUp"></a> <span data-ttu-id="dc46f-131">後續操作：從 .dqs 檔案匯入定義域之後</span><span class="sxs-lookup"><span data-stu-id="dc46f-131">Follow Up: After Importing a Domain from a .dqs File</span></span>  
 <span data-ttu-id="dc46f-132">當您從 .dqs 檔案匯入定義域之後，您可以將知識加入至定義域，或是在清理或比對專案中使用定義域 (根據定義域的內容而定)。</span><span class="sxs-lookup"><span data-stu-id="dc46f-132">After you import a domain from a .dqs file, you can add knowledge to the domain or use the domain in a cleansing or matching project, depending on the contents of the domain.</span></span> <span data-ttu-id="dc46f-133">如需詳細資訊，請參閱[執行知識探索](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理定義域](../../2014/data-quality-services/managing-a-domain.md)、[管理複合定義域](../../2014/data-quality-services/managing-a-composite-domain.md)、[建立比對原則](../../2014/data-quality-services/create-a-matching-policy.md)、[資料清理](../../2014/data-quality-services/data-cleansing.md)或[資料比對](../../2014/data-quality-services/data-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="dc46f-133">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), [Managing a Composite Domain](../../2014/data-quality-services/managing-a-composite-domain.md), [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md), [Data Cleansing](../../2014/data-quality-services/data-cleansing.md), or [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
  
