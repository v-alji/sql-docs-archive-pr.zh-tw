---
title: 將知識庫匯出為 .dqs 檔案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a324ead5-c8aa-4e26-abe3-ef415add00f8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 81dfc8e7f20fae9dacd521595d101be3117a6794
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592851"
---
# <a name="export-a-knowledge-base-to-a-dqs-file"></a><span data-ttu-id="fd1a5-102">將知識庫匯出到 .dqs 檔案</span><span class="sxs-lookup"><span data-stu-id="fd1a5-102">Export a Knowledge Base to a .dqs File</span></span>
  <span data-ttu-id="fd1a5-103">此主題描述如何將整個知識庫匯出到 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中的 .dqs 資料檔。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-103">This topic describes how to export an entire knowledge base to a .dqs data file in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="fd1a5-104">您可以將定義域或整個知識庫匯出到資料檔。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-104">You can export a domain or an entire knowledge base to a data file.</span></span> <span data-ttu-id="fd1a5-105">如需匯出定義域的資訊，請參閱[將定義域匯出為 .dqs 檔案](../../2014/data-quality-services/export-a-domain-to-a-dqs-file.md)。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-105">For information about exporting a domain, see [Export a Domain to a .dqs File](../../2014/data-quality-services/export-a-domain-to-a-dqs-file.md).</span></span>  
  
 <span data-ttu-id="fd1a5-106">將知識庫匯出到 .dqs 檔，然後將此檔案當做另一個知識庫匯入將會簡化知識產生程序，以節省時間與精力。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-106">Exporting a knowledge base to a .dqs file, and then importing it as another knowledge base simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="fd1a5-107">這樣可讓您將知識庫和其知識與其他人分享。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-107">It enables you to share a knowledge base and its knowledge with others.</span></span> <span data-ttu-id="fd1a5-108">.dqs 檔將包含所有知識庫資訊，包括定義域和比對原則，但不包括附加的參考資料資訊。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-108">The .dqs file will contain all knowledge base information, including domains and the matching policy, except for the attached reference data information.</span></span> <span data-ttu-id="fd1a5-109">匯入 .dqs 檔之後，如有必要，您必須將必要的定義域再次附加至適當的參考資料服務。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-109">You must attach the required domains to appropriate reference data services again, if required, after importing the .dqs file.</span></span> <span data-ttu-id="fd1a5-110">知識庫中已發行和未發行的資料都會匯出。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-110">Both published and unpublished data in a knowledge base is exported.</span></span>  
  
 <span data-ttu-id="fd1a5-111">匯出程序所建立的 .dqs 資料檔已經過加密，因此無法檢視內容。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-111">The .dqs data file created by the export process is encrypted, so the contents cannot be viewed.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fd1a5-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="fd1a5-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="fd1a5-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="fd1a5-113">Prerequisites</span></span>  
 <span data-ttu-id="fd1a5-114">若要將知識庫匯出到 .dqs 資料檔，您必須已建立及開啟知識庫。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-114">To export a knowledge base to a .dqs data file, you must have created and opened a knowledge base.</span></span> <span data-ttu-id="fd1a5-115">您不需要擁有匯出目標的 .dqs 檔案，系統會為您建立一個檔案。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-115">You do not need to have a .dqs file to export into; one will be created for you.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fd1a5-116">Security</span><span class="sxs-lookup"><span data-stu-id="fd1a5-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fd1a5-117">權限</span><span class="sxs-lookup"><span data-stu-id="fd1a5-117">Permissions</span></span>  
 <span data-ttu-id="fd1a5-118">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 角色或 dqs_administrator 角色，才能將知識庫匯出到 .dqs 資料檔。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-118">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to export a knowledge base to a .dqs data file.</span></span>  
  
##  <a name="export-a-knowledge-base-to-a-dqs-file"></a><a name="Export"></a><span data-ttu-id="fd1a5-119">將知識庫匯出至 dqs 檔案</span><span class="sxs-lookup"><span data-stu-id="fd1a5-119">Export a knowledge base to a .dqs file</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="fd1a5-120">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-120">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="fd1a5-121">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，於 [定義域管理] 活動中開啟知識庫。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-121">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="fd1a5-122">在 [定義域管理] 頁面中 (包含任何選取的索引標籤)，按一下定義域清單上方的 **[匯出知識庫資料]** 圖示，然後按一下 **[匯出知識庫]**。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-122">In the Domain Management page (with any tab selected), click the **Export Knowledge Base data** icon above the Domain list, and then click **Export Knowledge Base**.</span></span> <span data-ttu-id="fd1a5-123">另外，您也可以用滑鼠右鍵按一下 **[定義域]** 清單，將游標移到 **[匯出]** 上方，然後按一下 **[匯出知識庫]**。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-123">Alternatively, you can also right-click in the **Domain** list, hover over **Export**, and then click **Export Knowledge Base**.</span></span>  
  
4.  <span data-ttu-id="fd1a5-124">在 [匯出到資料檔]\*\*\*\* 對話方塊中，移至您想要用來儲存檔案的資料夾、為檔案命名或是保留知識庫名稱、將 [DQS 資料檔 (\*.dqs)]\*\*\*\* 保留為 [另存新檔]\*\*\*\* 類型，然後按一下 [儲存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-124">In the **Export to Data File** dialog box, move to the folder that you want to save the file in, name the file or keep the knowledge base name, keep **DQS Data Files (\*.dqs)** as the **Save as** type, and then click **Save**.</span></span>  
  
5.  <span data-ttu-id="fd1a5-125">在 **[匯出知識庫]** 對話方塊中，確認狀態行指出已完成匯出。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-125">In the **Export Knowledge Base** dialog box, verify that the status line indicates that the export completed.</span></span> <span data-ttu-id="fd1a5-126">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-126">Click **OK**.</span></span>  
  
##  <a name="follow-up-after-exporting-a-domain-to-a-dqs-file"></a><a name="FollowUp"></a><span data-ttu-id="fd1a5-127">後續操作：將定義域匯出至 dqs 檔案之後</span><span class="sxs-lookup"><span data-stu-id="fd1a5-127">Follow Up: After Exporting a Domain to a .dqs File</span></span>  
 <span data-ttu-id="fd1a5-128">當您將知識庫匯出到 .dqs 檔案之後，您可以將此知識庫匯入相同的 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] (具有新的名稱) 或不同的 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fd1a5-128">After you export a knowledge base to a .dqs file, you can import the knowledge base into the same [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] (with a new name) or into a different [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
  
