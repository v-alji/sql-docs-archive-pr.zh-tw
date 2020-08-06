---
title: 建立資料品質專案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dqproject.newdqproject.f1
helpviewer_keywords:
- create,data quality project
- data quality project,create
ms.assetid: 19c52d2b-d28e-4449-ab59-5fe0dc326cd9
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3bab14b34123464450bcf0de7540364fc642343e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687159"
---
# <a name="create-a-data-quality-project"></a><span data-ttu-id="a85e3-102">建立資料品質專案</span><span class="sxs-lookup"><span data-stu-id="a85e3-102">Create a Data Quality Project</span></span>
  <span data-ttu-id="a85e3-103">本主題描述如何使用 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]來建立資料品質專案。</span><span class="sxs-lookup"><span data-stu-id="a85e3-103">This topic describes how to create a data quality project by using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="a85e3-104">資料品質專案是用來在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中執行清理或比對活動。</span><span class="sxs-lookup"><span data-stu-id="a85e3-104">A data quality project is used to run the cleansing or matching activity in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a85e3-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="a85e3-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="a85e3-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="a85e3-106">Prerequisites</span></span>  
 <span data-ttu-id="a85e3-107">您必須擁有要用於資料品質專案的相關知識庫，才能進行清理或比對活動。</span><span class="sxs-lookup"><span data-stu-id="a85e3-107">You must have a relevant knowledge base to use in the data quality project for the cleansing or matching activity.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a85e3-108">Security</span><span class="sxs-lookup"><span data-stu-id="a85e3-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a85e3-109">權限</span><span class="sxs-lookup"><span data-stu-id="a85e3-109">Permissions</span></span>  
 <span data-ttu-id="a85e3-110">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 或 dqs_kb_operator 角色，才能建立資料品質專案。</span><span class="sxs-lookup"><span data-stu-id="a85e3-110">You must have the dqs_kb_editor or dqs_kb_operator role on the DQS_MAIN database to create a data quality project.</span></span>  
  
##  <a name="create-a-data-quality-project"></a><a name="Create"></a><span data-ttu-id="a85e3-111">建立資料品質專案</span><span class="sxs-lookup"><span data-stu-id="a85e3-111">Create a Data Quality Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="a85e3-112">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a85e3-112">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="a85e3-113">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，按一下 **[新增資料品質專案]**。</span><span class="sxs-lookup"><span data-stu-id="a85e3-113">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **New data quality project**.</span></span>  
  
3.  <span data-ttu-id="a85e3-114">在 **[新增資料品質專案]** 畫面中：</span><span class="sxs-lookup"><span data-stu-id="a85e3-114">In the **New Data Quality Project** screen:</span></span>  
  
    1.  <span data-ttu-id="a85e3-115">在 **[名稱]** 方塊中，輸入新資料品質專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="a85e3-115">In the **Name** box, type a name for the new data quality project.</span></span>  
  
    2.  <span data-ttu-id="a85e3-116">(選擇性) 在 **[描述]** 方塊中，輸入新資料品質專案的描述。</span><span class="sxs-lookup"><span data-stu-id="a85e3-116">(Optional) In the **Description** box, type a description for the new data quality project.</span></span>  
  
    3.  <span data-ttu-id="a85e3-117">在 **[使用知識庫]** 清單中，按一下以選取要用於資料品質專案的知識庫。</span><span class="sxs-lookup"><span data-stu-id="a85e3-117">In the **Use Knowledge base** list, click to select a knowledge base to be used for the data quality project.</span></span> <span data-ttu-id="a85e3-118">右側的 [知識庫詳細資料: <知識庫名稱>]\*\*\*\* 區域會顯示所選知識庫中可用的定義域名稱。</span><span class="sxs-lookup"><span data-stu-id="a85e3-118">The **Knowledge base details: <Knowledge_Base_Name>** area on the right side displays the domain names available in the selected knowledge base.</span></span>  
  
    4.  <span data-ttu-id="a85e3-119">在 **[選取活動]** 區域中，按一下您想要使用此資料品質專案來執行的活動：</span><span class="sxs-lookup"><span data-stu-id="a85e3-119">In the **Select Activity** area, click on an activity that you want to perform using this data quality project:</span></span>  
  
        -   <span data-ttu-id="a85e3-120">**清理**：若要清理來源資料，請選取此活動。</span><span class="sxs-lookup"><span data-stu-id="a85e3-120">**Cleansing**: Select this activity to cleanse the source data.</span></span>  
  
        -   <span data-ttu-id="a85e3-121">**比對**：若要執行比對，請選取此活動。</span><span class="sxs-lookup"><span data-stu-id="a85e3-121">**Matching**: Select this activity to perform matching.</span></span> <span data-ttu-id="a85e3-122">只有當您針對資料品質專案所選取的知識庫包含比對原則時，才能使用此活動。</span><span class="sxs-lookup"><span data-stu-id="a85e3-122">This activity is available only if the knowledge base selected for the data quality project contains a matching policy.</span></span>  
  
4.  <span data-ttu-id="a85e3-123">按一下 **[建立]** ，建立資料品質專案。</span><span class="sxs-lookup"><span data-stu-id="a85e3-123">Click **Create** to create a data quality project.</span></span>  
  
##  <a name="follow-up-after-creating-a-data-quality-project"></a><a name="FollowUp"></a><span data-ttu-id="a85e3-124">後續操作：建立資料品質專案之後</span><span class="sxs-lookup"><span data-stu-id="a85e3-124">Follow Up: After Creating a Data Quality Project</span></span>  
 <span data-ttu-id="a85e3-125">建立資料品質專案之後，系統會顯示可用來執行選取活動的精靈：清理或比對。</span><span class="sxs-lookup"><span data-stu-id="a85e3-125">After you create a data quality project, you are presented with a wizard that you use to perform the selected activity: cleansing or matching.</span></span> <span data-ttu-id="a85e3-126">如需清理和比對活動的詳細資訊，請參閱[資料清理](../../2014/data-quality-services/data-cleansing.md)和[資料比對](../../2014/data-quality-services/data-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="a85e3-126">For more information about the cleansing and matching activities, see [Data Cleansing](../../2014/data-quality-services/data-cleansing.md) and [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
  
