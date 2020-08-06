---
title: 將定義域匯出為 .dqs 檔案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: eba10d3d-b5c4-447b-8a30-fa07996cb28e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5d23e9efa2b3224aab5623201a54d1af56e49e09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592856"
---
# <a name="export-a-domain-to-a-dqs-file"></a><span data-ttu-id="69d5d-102">將定義域匯出成 .dqs 檔案</span><span class="sxs-lookup"><span data-stu-id="69d5d-102">Export a Domain to a .dqs File</span></span>
  <span data-ttu-id="69d5d-103">此主題描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中將定義域匯出至 .dqs 檔案。</span><span class="sxs-lookup"><span data-stu-id="69d5d-103">This topic describes how to export a domain to a .dqs file in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="69d5d-104">您可以將定義域或整個知識庫匯出到資料檔。</span><span class="sxs-lookup"><span data-stu-id="69d5d-104">You can export a domain or an entire knowledge base to a data file.</span></span> <span data-ttu-id="69d5d-105">如需匯出知識庫的資訊，請參閱[將知識庫匯出為 .dqs 檔案](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)。</span><span class="sxs-lookup"><span data-stu-id="69d5d-105">For information about exporting a knowledge base, see [Export a Knowledge Base to a .dqs File](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md).</span></span>  
  
 <span data-ttu-id="69d5d-106">將某個知識庫中的定義域匯出到 .dqs 資料檔，然後將它匯入另一個知識庫將會簡化知識產生程序，以節省時間與精力。</span><span class="sxs-lookup"><span data-stu-id="69d5d-106">Exporting a domain from one knowledge base to a .dqs data file, and then importing it to another knowledge base simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="69d5d-107">這樣可讓您將定義域和定義域的知識與其他人分享。</span><span class="sxs-lookup"><span data-stu-id="69d5d-107">It enables you to share a domain and its knowledge with others.</span></span>  
  
 <span data-ttu-id="69d5d-108">您可以匯出單一定義域或複合定義域。</span><span class="sxs-lookup"><span data-stu-id="69d5d-108">You can export either a single domain or composite domain.</span></span> <span data-ttu-id="69d5d-109">包含單一定義域的 .dqs 檔案包括所有定義域資料，其中包括定義域屬性、值和規則，但不包括附加的參考資料資訊。</span><span class="sxs-lookup"><span data-stu-id="69d5d-109">A .dqs file containing a single domain includes all domain data including domain properties, values, and rules except for the attached reference data information.</span></span> <span data-ttu-id="69d5d-110">含有複合定義域的 .dqs 檔案包括所有複合定義域資料，其中包括複合定義域內所容納之定義域的所有定義域資料，以及複合定義域屬性、關聯和規則，但不包括參考資料資訊。</span><span class="sxs-lookup"><span data-stu-id="69d5d-110">A .dqs file containing a composite domain includes all composite domain data, including all domain data for the domains that are contained in the composite domain, and the composite domain properties, relations, and rules, except for the reference data information.</span></span> <span data-ttu-id="69d5d-111">匯入 .dqs 檔之後，如有必要，您必須將定義域或複合定義域再次附加至適當的參考資料服務。</span><span class="sxs-lookup"><span data-stu-id="69d5d-111">You must attach the domain or the composite domain to appropriate reference data services again, if required, after importing the .dqs file.</span></span> <span data-ttu-id="69d5d-112">已發行和未發行的資料都會匯出。</span><span class="sxs-lookup"><span data-stu-id="69d5d-112">Both published and unpublished data is exported.</span></span>  
  
 <span data-ttu-id="69d5d-113">匯出程序所建立的 .dqs 資料檔已經過加密，因此無法檢視內容。</span><span class="sxs-lookup"><span data-stu-id="69d5d-113">The .dqs data file created by the export process is encrypted, so the contents cannot be viewed.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="69d5d-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="69d5d-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="69d5d-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="69d5d-115">Prerequisites</span></span>  
 <span data-ttu-id="69d5d-116">若要將定義域匯出到 .dqs 資料檔，您必須已經建立及選取單一定義域或是包含多個單一定義域的複合定義域。</span><span class="sxs-lookup"><span data-stu-id="69d5d-116">To export a domain to a .dqs data file, you must have created and selected a single domain or a composite domain containing multiple single domains.</span></span> <span data-ttu-id="69d5d-117">您不需要擁有匯出目標的 .dqs 檔案，系統會為您建立一個檔案。</span><span class="sxs-lookup"><span data-stu-id="69d5d-117">You do not need to have a .dqs file to export into; one will be created for you.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="69d5d-118">Security</span><span class="sxs-lookup"><span data-stu-id="69d5d-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="69d5d-119">權限</span><span class="sxs-lookup"><span data-stu-id="69d5d-119">Permissions</span></span>  
 <span data-ttu-id="69d5d-120">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 角色或 dqs_administrator 角色，才能將定義域匯出到 .dqs 資料檔。</span><span class="sxs-lookup"><span data-stu-id="69d5d-120">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to export a domain to a .dqs data file.</span></span>  
  
##  <a name="export-a-domain-to-a-dqs-file"></a><a name="Export"></a><span data-ttu-id="69d5d-121">將網域匯出至 dqs 檔案</span><span class="sxs-lookup"><span data-stu-id="69d5d-121">Export a domain to a .dqs file</span></span>  
 <span data-ttu-id="69d5d-122">您可以從任何 [定義域管理] 頁面匯出。</span><span class="sxs-lookup"><span data-stu-id="69d5d-122">You can export from any Domain Management page.</span></span> <span data-ttu-id="69d5d-123">您可以從使用者介面的控制項或是 [定義域清單] 窗格之內容功能表的命令中取得匯出命令。</span><span class="sxs-lookup"><span data-stu-id="69d5d-123">The export command is available from both a control in the user interface and from a command in the context menu of the Domain List pane.</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="69d5d-124">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="69d5d-124">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="69d5d-125">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，於 [定義域管理] 活動中開啟知識庫。</span><span class="sxs-lookup"><span data-stu-id="69d5d-125">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="69d5d-126">在 **[定義域管理]** 頁面 (包含任何選取的索引標籤) 中，於 **[定義域]** 清單中選取單一定義域或複合定義域。</span><span class="sxs-lookup"><span data-stu-id="69d5d-126">In the **Domain Management page** (with any tab selected), select a single domain or a composite domain in the **Domain** list.</span></span>  
  
4.  <span data-ttu-id="69d5d-127">按一下定義域清單上方的 **[匯出知識庫資料]** 圖示，然後按一下 **[匯出定義域]**。</span><span class="sxs-lookup"><span data-stu-id="69d5d-127">Click the **Export Knowledge Base data** icon above the domain list, and then click **Export Domain**.</span></span> <span data-ttu-id="69d5d-128">另外，您也可以用滑鼠右鍵按一下 **[定義域]** 清單中的定義域，指向 **[匯出]**，然後按一下 **[匯出定義域]**。</span><span class="sxs-lookup"><span data-stu-id="69d5d-128">Alternatively, you can right-click the domain in the **Domain** list, point to **Export**, and then click **Export Domain**.</span></span>  
  
5.  <span data-ttu-id="69d5d-129">在 [匯出到資料檔]\*\*\*\* 對話方塊中，移至您想要用來儲存檔案的資料夾、為檔案命名或是保留預設名稱、將 [DQS 資料檔 (\*.dqs)]\*\*\*\* 保留為 [檔案類型]\*\*\*\*，然後按一下 [儲存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69d5d-129">In the **Export to Data File** dialog box, move to the folder that you want to save the file in, name the file or keep the default name, keep **DQS Data Files (\*.dqs)** as the **Save as type**, and then click **Save**.</span></span>  
  
6.  <span data-ttu-id="69d5d-130">在 **[匯出定義域]** 對話方塊中，確認此對話方塊中的狀態行指出已完成匯出。</span><span class="sxs-lookup"><span data-stu-id="69d5d-130">In the **Export Domain** dialog box, verify that the status line in the dialog box indicates that the export completed.</span></span> <span data-ttu-id="69d5d-131">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="69d5d-131">Click **OK**.</span></span>  
  
##  <a name="follow-up-after-exporting-a-domain-to-a-dqs-file"></a><a name="FollowUp"></a><span data-ttu-id="69d5d-132">後續操作：將定義域匯出至 dqs 檔案之後</span><span class="sxs-lookup"><span data-stu-id="69d5d-132">Follow Up: After Exporting a Domain to a .dqs File</span></span>  
 <span data-ttu-id="69d5d-133">在您將定義域匯出到 .dqs 檔案之後，您可以將此定義域匯入另一個知識庫中。</span><span class="sxs-lookup"><span data-stu-id="69d5d-133">After you export a domain to a .dqs file, you can import the domain into another knowledge base.</span></span>  
  
  
