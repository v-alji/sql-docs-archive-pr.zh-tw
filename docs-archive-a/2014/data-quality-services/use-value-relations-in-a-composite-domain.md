---
title: 使用複合定義域中的值關聯 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.cdvaluerelations.f1
ms.assetid: 5ee468f0-8538-4620-90e8-63f466c9000e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 135934ec99fed612609e5e1b962f08bb93b98ede
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709946"
---
# <a name="use-value-relations-in-a-composite-domain"></a><span data-ttu-id="19ff0-102">使用複合定義域中的值關聯</span><span class="sxs-lookup"><span data-stu-id="19ff0-102">Use Value Relations in a Composite Domain</span></span>
  <span data-ttu-id="19ff0-103">此主題描述如何檢視在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 的知識探索程序期間針對複合定義域找到的值組合。</span><span class="sxs-lookup"><span data-stu-id="19ff0-103">This topic describes how to view value combinations found for the composite domain during the knowledge discovery process in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="19ff0-104">這個頁面會顯示值組合出現的次數。</span><span class="sxs-lookup"><span data-stu-id="19ff0-104">This page shows the number of occurrences of the value combinations.</span></span> <span data-ttu-id="19ff0-105">複合定義域不支援值管理，所以您無法針對這些值執行任何作業。</span><span class="sxs-lookup"><span data-stu-id="19ff0-105">Value management is not supported for composite domains, so you cannot perform any operations on these values.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="19ff0-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="19ff0-106">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="19ff0-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="19ff0-107">Prerequisites</span></span>  
 <span data-ttu-id="19ff0-108">若要檢視值關聯，您必須已建立及開啟複合定義域。</span><span class="sxs-lookup"><span data-stu-id="19ff0-108">To view value relations, you must have created and opened a composite domain.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="19ff0-109">Security</span><span class="sxs-lookup"><span data-stu-id="19ff0-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="19ff0-110">權限</span><span class="sxs-lookup"><span data-stu-id="19ff0-110">Permissions</span></span>  
 <span data-ttu-id="19ff0-111">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 角色或 dqs_administrator 角色，才能檢視複合定義域中的值關聯。</span><span class="sxs-lookup"><span data-stu-id="19ff0-111">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to view value relations in a composite domain.</span></span>  
  
##  <a name="view-value-relations"></a><a name="Use"></a><span data-ttu-id="19ff0-112">視圖值關聯</span><span class="sxs-lookup"><span data-stu-id="19ff0-112">View Value Relations</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="19ff0-113">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="19ff0-113">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="19ff0-114">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面上，開啟或建立知識庫。</span><span class="sxs-lookup"><span data-stu-id="19ff0-114">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open or create a knowledge base.</span></span> <span data-ttu-id="19ff0-115">選取 **[定義域管理]** 當做活動，然後按一下 **[開啟]** 或 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="19ff0-115">Select **Domain Management** as the activity, and then click **Open** or **Create**.</span></span> <span data-ttu-id="19ff0-116">如需相關資訊，請參閱 [建立知識庫](../../2014/data-quality-services/create-a-knowledge-base.md) 或 [開啟知識庫](../../2014/data-quality-services/open-a-knowledge-base.md)。</span><span class="sxs-lookup"><span data-stu-id="19ff0-116">For more information, see [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md) or [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
3.  <span data-ttu-id="19ff0-117">從 **[定義域管理]** 頁面的 **[定義域清單]** 中，選取您想要建立定義域規則的複合定義域，或是建立新的複合定義域。</span><span class="sxs-lookup"><span data-stu-id="19ff0-117">From the **Domain list** on the **Domain Management** page, select the composite domain that you want to create a domain rule for, or create a new composite domain.</span></span> <span data-ttu-id="19ff0-118">如果您必須建立新的定義域，請參閱＜ [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md)＞。</span><span class="sxs-lookup"><span data-stu-id="19ff0-118">If you have to create a new domain, see [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md).</span></span>  
  
4.  <span data-ttu-id="19ff0-119">按一下 **[值關聯]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="19ff0-119">Click the **Value Relations** tab.</span></span>  
  
5.  <span data-ttu-id="19ff0-120">檢視針對每一個值組合顯示的頻率。</span><span class="sxs-lookup"><span data-stu-id="19ff0-120">View the frequencies displayed for each value combination.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="19ff0-121">**[值]** 資料表會顯示存在於複合定義域中的每一個值組合。</span><span class="sxs-lookup"><span data-stu-id="19ff0-121">The **Value** table shows each combination of values that exists in the composite domain.</span></span> <span data-ttu-id="19ff0-122">每一個值都會顯示在它所適用的單一定義域中。</span><span class="sxs-lookup"><span data-stu-id="19ff0-122">Each value is shown in the single domain that it applies to.</span></span> <span data-ttu-id="19ff0-123">值關聯資料表預設會依據頻率排序，但是您可以按一下另一個資料行，依據該資料行排序。</span><span class="sxs-lookup"><span data-stu-id="19ff0-123">The default sorting of the value relations table is by frequency, but you can click on another column to sort by that column.</span></span> <span data-ttu-id="19ff0-124">只會顯示頻率大於或等於 20 的值。</span><span class="sxs-lookup"><span data-stu-id="19ff0-124">Only those values with a frequency greater than or equal to 20 are displayed.</span></span>  
  
6.  <span data-ttu-id="19ff0-125">您不能變更資料表中的任何值。</span><span class="sxs-lookup"><span data-stu-id="19ff0-125">You cannot change any of the values in the table.</span></span> <span data-ttu-id="19ff0-126">如果您已執行其他作業，請按一下 **[完成]** ，完成定義域管理活動。</span><span class="sxs-lookup"><span data-stu-id="19ff0-126">If you have performed other operations, click **Finish** to complete the domain management activity.</span></span> <span data-ttu-id="19ff0-127">否則，請按一下 [**取消**]。</span><span class="sxs-lookup"><span data-stu-id="19ff0-127">Otherwise, click **Cancel**.</span></span>  
  
##  <a name="follow-up-after-viewing-value-relations"></a><a name="FollowUp"></a><span data-ttu-id="19ff0-128">後續操作：查看值關聯之後</span><span class="sxs-lookup"><span data-stu-id="19ff0-128">Follow Up: After Viewing Value Relations</span></span>  
 <span data-ttu-id="19ff0-129">在檢視值關聯之後，您可以針對定義域執行其他定義域管理工作、執行知識探索來將知識加入至定義域，或者將比對原則加入至定義域。</span><span class="sxs-lookup"><span data-stu-id="19ff0-129">After you view value relations, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="19ff0-130">如需詳細資訊，請參閱[執行知識探索](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理定義域](../../2014/data-quality-services/managing-a-domain.md)或[建立比對原則](../../2014/data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="19ff0-130">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
  
