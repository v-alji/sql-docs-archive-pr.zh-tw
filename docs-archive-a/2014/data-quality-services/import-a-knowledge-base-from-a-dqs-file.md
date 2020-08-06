---
title: 從 .dqs 檔案匯入知識庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 9b9786fe-9e80-429a-afcb-dc3b3dd6f0b0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 522c5f6d8f962cef77e215c21133927e8da4d04f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701992"
---
# <a name="import-a-knowledge-base-from-a-dqs-file"></a><span data-ttu-id="f6b49-102">從 .dqs 檔案匯入知識庫</span><span class="sxs-lookup"><span data-stu-id="f6b49-102">Import a Knowledge Base from a .dqs File</span></span>
  <span data-ttu-id="f6b49-103">此主題描述如何從 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中的 .dqs 資料檔匯入整個知識庫。</span><span class="sxs-lookup"><span data-stu-id="f6b49-103">This topic describes how to import an entire knowledge base from a .dqs data file in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="f6b49-104">您從 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 應用程式匯出現有的知識庫來建立此資料檔 (請參閱＜ [將知識庫匯出到.dqs 檔案](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)＞)。</span><span class="sxs-lookup"><span data-stu-id="f6b49-104">You create the data file by exporting an existing knowledge base from within the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application (see [Export a Knowledge Base to a .dqs File](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)).</span></span>  
  
 <span data-ttu-id="f6b49-105">使用 .dqs 資料檔匯出知識庫的內容，然後將內容匯入相同 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 或不同 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 上的另一個知識庫會簡化知識產生程序，以節省時間與精力。</span><span class="sxs-lookup"><span data-stu-id="f6b49-105">Using a .dqs data file to export the contents of a knowledge base and then import the contents into another knowledge base on the same [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] or a different [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="f6b49-106">這樣可讓您將知識庫和知識庫的知識與其他人分享，以節省他們的時間。</span><span class="sxs-lookup"><span data-stu-id="f6b49-106">It enables you to share a knowledge base and its knowledge with others, saving them time.</span></span> <span data-ttu-id="f6b49-107">.dqs 檔將包含所有知識庫資訊，包括定義域和比對原則，但不包括附加的參考資料資訊。</span><span class="sxs-lookup"><span data-stu-id="f6b49-107">The .dqs file will contain all knowledge base information, including domains and the matching policy, except for the attached reference data information.</span></span> <span data-ttu-id="f6b49-108">已發行和未發行的資料都將匯入。</span><span class="sxs-lookup"><span data-stu-id="f6b49-108">Published and unpublished data will be imported.</span></span>  
  
 <span data-ttu-id="f6b49-109">.dqs 資料檔已加密，所以無法檢視。</span><span class="sxs-lookup"><span data-stu-id="f6b49-109">A .dqs data file is encrypted, so cannot be viewed.</span></span>  
  
 <span data-ttu-id="f6b49-110">當您匯入知識庫時，您可以使用相同的名稱，除非此知識庫名稱已存在於用戶端應用程式中 (此時必須重新命名)。</span><span class="sxs-lookup"><span data-stu-id="f6b49-110">When you import a knowledge base, you can use the same name, unless the knowledge base name already exists in the client application, in which case you must rename it.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f6b49-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="f6b49-111">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="f6b49-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="f6b49-112">Prerequisites</span></span>  
 <span data-ttu-id="f6b49-113">若要從 .dqs 檔案匯入知識庫，您必須已將知識庫匯出到 .dqs 檔案。</span><span class="sxs-lookup"><span data-stu-id="f6b49-113">To import a knowledge base from a .dqs file, you must have already exported the knowledge base into the .dqs file.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f6b49-114">Security</span><span class="sxs-lookup"><span data-stu-id="f6b49-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f6b49-115">權限</span><span class="sxs-lookup"><span data-stu-id="f6b49-115">Permissions</span></span>  
 <span data-ttu-id="f6b49-116">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 角色或 dqs_administrator 角色，才能從 .dqs 資料檔匯入知識庫。</span><span class="sxs-lookup"><span data-stu-id="f6b49-116">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to import a knowledge base from a .dqs data file.</span></span>  
  
##  <a name="import-a-knowledge-base-from-a-dqs-file"></a><a name="Import"></a><span data-ttu-id="f6b49-117">從 dqs 檔案匯入知識庫</span><span class="sxs-lookup"><span data-stu-id="f6b49-117">Import a knowledge base from a .dqs file</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="f6b49-118">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="f6b49-118">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="f6b49-119">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面上，按一下 **[新增知識庫]**。</span><span class="sxs-lookup"><span data-stu-id="f6b49-119">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **New knowledge base**.</span></span>  
  
3.  <span data-ttu-id="f6b49-120">輸入知識庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6b49-120">Enter a name for the knowledge base.</span></span>  
  
4.  <span data-ttu-id="f6b49-121">按一下 **[建立知識庫來源]** 的向下箭號，然後選取 **[從 DQS 檔案匯入]**。</span><span class="sxs-lookup"><span data-stu-id="f6b49-121">Click the down arrow for **Create knowledge base from**, and then select **Import from DQS file**.</span></span>  
  
5.  <span data-ttu-id="f6b49-122">針對 **[選取資料檔]** 按一下 **[瀏覽]**。</span><span class="sxs-lookup"><span data-stu-id="f6b49-122">For **Select data file**, click **Browse**.</span></span>  
  
6.  <span data-ttu-id="f6b49-123">在 **[從資料檔匯入]** 對話方塊中，移至包含您要匯入之 .dqs 檔案的資料夾，然後按一下檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6b49-123">In the **Import from Data File** dialog box, move to the folder that contains the .dqs file that you want to import, and then click the name of the file.</span></span> <span data-ttu-id="f6b49-124">按一下 **[開啟]** 。</span><span class="sxs-lookup"><span data-stu-id="f6b49-124">Click **Open**.</span></span>  
  
7.  <span data-ttu-id="f6b49-125">確認 **[定義域]** 清單中是否顯示正確的知識庫和定義域。</span><span class="sxs-lookup"><span data-stu-id="f6b49-125">Verify that the correct knowledge base and domains are displayed in the **Domain** list.</span></span>  
  
8.  <span data-ttu-id="f6b49-126">請選取您要執行的活動，然後按一下 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="f6b49-126">Select the activity that you want to perform, and then click **Create**.</span></span>  
  
9. <span data-ttu-id="f6b49-127">在 **[匯入知識庫]** 對話方塊中，確認狀態行指出已完成匯入。</span><span class="sxs-lookup"><span data-stu-id="f6b49-127">In the **Import Knowledge Base** dialog box, verify that the status line indicates that the import completed.</span></span> <span data-ttu-id="f6b49-128">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="f6b49-128">Click **OK**.</span></span>  
  
10. <span data-ttu-id="f6b49-129">完成您需要執行的知識探索、定義域管理或比對原則工作，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="f6b49-129">Complete the knowledge discovery, domain management, or matching policy tasks that you need to perform, and then click **Finish**.</span></span>  
  
11. <span data-ttu-id="f6b49-130">按一下 **[發行]** 發行知識庫中的知識，或是按一下 **[否]** ，不發行。</span><span class="sxs-lookup"><span data-stu-id="f6b49-130">Click **Publish** to publish the knowledge in the knowledge base, or **No** not to.</span></span>  
  
12. <span data-ttu-id="f6b49-131">如果您已發行知識庫，請按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f6b49-131">If you published the knowledge base, click **OK**.</span></span>  
  
13. <span data-ttu-id="f6b49-132">在 Data Quality Services 首頁上，確認此知識庫列在 **[最近使用的知識庫]** 底下。</span><span class="sxs-lookup"><span data-stu-id="f6b49-132">In the Data Quality Services home page, verify that the knowledge base is listed under **Recent knowledge bases**.</span></span>  
  
##  <a name="follow-up-after-importing-a-knowledge-base-from-a-dqs-file"></a><a name="FollowUp"></a> <span data-ttu-id="f6b49-133">後續操作：從 .dqs 檔案匯入知識庫之後</span><span class="sxs-lookup"><span data-stu-id="f6b49-133">Follow Up: After Importing a Knowledge Base from a .dqs File</span></span>  
 <span data-ttu-id="f6b49-134">當您從 .dqs 檔案匯入知識庫之後，您可以將知識加入至知識庫，或是在清理或比對專案中使用此知識庫 (根據知識庫的內容而定)。</span><span class="sxs-lookup"><span data-stu-id="f6b49-134">After you import a knowledge base from a .dqs file, you can add knowledge to the knowledge base or use the knowledge base in a cleansing or matching project, depending on the contents of the knowledge base.</span></span> <span data-ttu-id="f6b49-135">如需詳細資訊，請參閱[執行知識探索](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理定義域](../../2014/data-quality-services/managing-a-domain.md)、[管理複合定義域](../../2014/data-quality-services/managing-a-composite-domain.md)、[建立比對原則](../../2014/data-quality-services/create-a-matching-policy.md)、[資料清理](../../2014/data-quality-services/data-cleansing.md)或[資料比對](../../2014/data-quality-services/data-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="f6b49-135">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), [Managing a Composite Domain](../../2014/data-quality-services/managing-a-composite-domain.md), [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md), [Data Cleansing](../../2014/data-quality-services/data-cleansing.md), or [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
  
