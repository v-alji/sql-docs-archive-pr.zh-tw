---
title: 建立定義域 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.createdomain.f1
ms.assetid: 5c4828f5-bd51-4c29-b3de-87b7d2f2d3e5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fad6abd795aa9412bb71d251623d92d3e13b889c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592270"
---
# <a name="create-a-domain"></a><span data-ttu-id="bf5dd-102">建立定義域</span><span class="sxs-lookup"><span data-stu-id="bf5dd-102">Create a Domain</span></span>
  <span data-ttu-id="bf5dd-103">此主題描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中建立定義域。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-103">This topic describes how to create a domain in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="bf5dd-104">定義域中的值是欄位中資料的語意表示法。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-104">The values in the domain are a semantic representation of the data in a field.</span></span> <span data-ttu-id="bf5dd-105">如需定義域的詳細資訊，請參閱[管理定義域](../../2014/data-quality-services/managing-a-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-105">For more information on domains, see [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md).</span></span>  
  
 <span data-ttu-id="bf5dd-106">建立新的定義域的方式有兩種。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-106">There are two ways to create a new domain.</span></span> <span data-ttu-id="bf5dd-107">第一種方式是在知識探索活動的對應步驟期間，當您正在分析資料取樣，將知識加入至新的知識庫或現有知識庫時。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-107">The first is during the Map step of the knowledge discovery activity, when you are in the process of analyzing a data sample to add knowledge to a new or existing knowledge base.</span></span> <span data-ttu-id="bf5dd-108">第二種方式是在定義域管理活動期間，當您建立新的定義域，而不是變更現有定義域時。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-108">The second is during the domain management activity, when instead of changing an existing domain, you create a new one.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bf5dd-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="bf5dd-109">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="bf5dd-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="bf5dd-110">Prerequisites</span></span>  
 <span data-ttu-id="bf5dd-111">若要建立定義域，您必須已建立及開啟知識庫。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-111">To create a domain, you must have created and opened a knowledge base.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bf5dd-112">Security</span><span class="sxs-lookup"><span data-stu-id="bf5dd-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bf5dd-113">權限</span><span class="sxs-lookup"><span data-stu-id="bf5dd-113">Permissions</span></span>  
 <span data-ttu-id="bf5dd-114">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 角色或 dqs_administrator 角色，才能建立定義域。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-114">You must have the dqs_kb_editor role or the dqs_administrator on the DQS_MAIN database to create a domain.</span></span>  
  
##  <a name="create-a-domain-in-the-knowledge-discovery-activity"></a><a name="Discovery"></a> <span data-ttu-id="bf5dd-115">在知識探索活動中建立定義域</span><span class="sxs-lookup"><span data-stu-id="bf5dd-115">Create a Domain in the Knowledge Discovery Activity</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="bf5dd-116">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-116">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="bf5dd-117">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，按一下 **[開啟知識庫]** ，然後選取知識庫，或是按一下 **[新增知識庫]** ，並輸入新知識庫的屬性。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-117">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open knowledge base** and then select a knowledge base, or click **New knowledge base** and enter properties for the new knowledge base.</span></span>  
  
3.  <span data-ttu-id="bf5dd-118">選取 **[知識探索]** 當做活動，然後按一下 **[建立]** 建立新的知識庫，或按一下 **[開啟]** 開啟現有的知識庫。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-118">Select **Knowledge Discovery** as the activity, and then click **Create** to create the new knowledge base or **Open** to open an existing knowledge base.</span></span>  
  
4.  <span data-ttu-id="bf5dd-119">在 **[對應]** 頁面上，指定資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-119">On the **Map** page, specify a connection to the data source.</span></span> <span data-ttu-id="bf5dd-120">如需詳細資訊，請參閱＜ [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md)＞。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-120">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md).</span></span>  
  
5.  <span data-ttu-id="bf5dd-121">在 **[對應]** 資料表中，從空白資料列之 **[來源資料行]** 資料行的下拉式清單中選取來源資料行。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-121">In the **Mappings** table, select a source column from the drop-down list for the **Source Column** column of an empty row.</span></span> <span data-ttu-id="bf5dd-122">如果沒有對應的定義域存在，請按一下 **[建立定義域]** 圖示。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-122">If no corresponding domain exists, click the **Create a Domain** icon.</span></span>  
  
##  <a name="create-a-domain-in-the-domain-management-activity"></a><a name="DomainManagement"></a> <span data-ttu-id="bf5dd-123">在定義域管理活動中建立定義域</span><span class="sxs-lookup"><span data-stu-id="bf5dd-123">Create a Domain in the Domain Management Activity</span></span>  
  
1.  <span data-ttu-id="bf5dd-124">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，按一下 **[開啟知識庫]** ，然後選取知識庫，或是按一下 **[新增知識庫]** ，並輸入新知識庫的屬性。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-124">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open knowledge base** and then select a knowledge base, or click **New knowledge base** and enter properties for the new knowledge base.</span></span>  
  
2.  <span data-ttu-id="bf5dd-125">選取 **[定義域管理]** 當做活動，然後按一下 **[建立]** 建立新的知識庫，或按一下 **[開啟]** 開啟現有的知識庫。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-125">Select **Domain Management** as the activity, and then click **Create** to create the new knowledge base or **Open** to open an existing knowledge base.</span></span>  
  
3.  <span data-ttu-id="bf5dd-126">在 **[定義域管理]** 頁面上，按一下定義域清單上方的 **[建立定義域]** 圖示。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-126">On the **Domain Management** page, click the **Create a Domain** icon above the Domain list.</span></span>  
  
##  <a name="set-domain-properties"></a><a name="Properties"></a><span data-ttu-id="bf5dd-127">設定網域屬性</span><span class="sxs-lookup"><span data-stu-id="bf5dd-127">Set Domain Properties</span></span>  
  
1.  <span data-ttu-id="bf5dd-128">在 **[建立定義域]** 對話方塊中，輸入知識庫特有的名稱以及最多 256 個字元的描述。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-128">In the **Create Domain** dialog box, enter a name that is unique to the knowledge base and a description up to 256 characters.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bf5dd-129">如需有關定義域屬性的詳細資訊，請參閱＜ [Set Domain Properties](../../2014/data-quality-services/set-domain-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-129">For more information about domain properties, see [Set Domain Properties](../../2014/data-quality-services/set-domain-properties.md).</span></span>  
  
2.  <span data-ttu-id="bf5dd-130">為定義域中的值，從 **[資料類型]** 清單選取資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-130">From the **Data Type** list, select a data type for the values in the domain.</span></span> <span data-ttu-id="bf5dd-131">資料類型可以是 **[字串]** (預設值)、 **[日期]**、 **[整數]** 或 **[十進位]**。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-131">The data type can be **String** (the default), **Date**, **Integer**, or **Decimal**.</span></span>  
  
3.  <span data-ttu-id="bf5dd-132">選取 **[使用前置值]** 指定一組同義字中的前置值將會是輸出，而不是與其同義的值。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-132">Select **Use Leading Values** to specify that the leading value in a group of synonyms will be output instead of a value that is a synonym to it.</span></span> <span data-ttu-id="bf5dd-133">取消選取 **[使用前置值]** ，指定每一個同義字值都是正確或更正形式的輸出，而且不會由其群組的前置值加以取代。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-133">Deselect **Use Leading Values** to specify that each synonym value is output in its correct or corrected form, and is not replaced by the leading value for its group.</span></span>  
  
4.  <span data-ttu-id="bf5dd-134">如果資料類型是 **[字串]**，請選取 **[正在將字串標準化]** 來移除定義域值中的特殊字元，這樣可能會提升相符的可能性。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-134">If the data type is **String**, select **Normalize String** to remove special characters in the domain values, which may improve the likelihood of matches.</span></span>  
  
5.  <span data-ttu-id="bf5dd-135">從 **[設定輸出格式為]** 下拉式清單中，選取當定義域中的資料值為輸出時，將套用的格式。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-135">From the **Format Output to** drop-down list, select the formatting that will be applied when the data values in the domain are output.</span></span> <span data-ttu-id="bf5dd-136">此格式專屬於步驟 2 中選取的資料類型，如下列清單所示：</span><span class="sxs-lookup"><span data-stu-id="bf5dd-136">The formatting is specific to the data type selected in step 2, as shown in the following list:</span></span>  
  
    -   <span data-ttu-id="bf5dd-137">如果是字串值，您可以指定字串應該輸出為大寫或小寫。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-137">For a string value, you can specify that the string be output as upper case, lower case, or capitalized.</span></span>  
  
    -   <span data-ttu-id="bf5dd-138">如果是日期值，您可以指定日、月和年的格式。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-138">For a date value, you can specify the format of the day, month, and year.</span></span>  
  
    -   <span data-ttu-id="bf5dd-139">如果是整數值，您可以指定要套用之格式遮罩的類型。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-139">For an integer value, you can specify the type of format mask to be applied.</span></span>  
  
    -   <span data-ttu-id="bf5dd-140">如果是十進位值，您可以指定要套用之格式遮罩的精確度和類型。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-140">For a decimal value, you can specify the accuracy and the type of format mask to be applied.</span></span>  
  
     <span data-ttu-id="bf5dd-141">在 **[設定輸出格式為]** 下拉式清單中選取 **[無]** ，表示不會套用清單中的任何格式。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-141">Selecting **None** in the **Format Output to** drop-down list means none of the formats in the list will be applied.</span></span>  
  
6.  <span data-ttu-id="bf5dd-142">如果資料類型是 **[字串]**，請在 **[語言]** 下拉式清單中選取您想要套用哪一個語言版本的拼字檢查 (如果您啟用拼字檢查)。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-142">If the data type is **String**, in the **Language** drop-down list, select which language version of the speller you want to apply if you enable the speller.</span></span>  
  
7.  <span data-ttu-id="bf5dd-143">如果資料類型是 **[字串]**，請選取 **[啟用拼字檢查]** ，在擴展定義域時針對所有字串值執行拼字檢查。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-143">If the data type is **String**, select **Enable Speller** to run the Speller on all string values when populating the domain.</span></span>  
  
8.  <span data-ttu-id="bf5dd-144">如果資料類型是 **[字串]**，請選取 **[停用語法錯誤演算法]** 來擴展定義域，而不檢查字串值的語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-144">If the data type is **String**, select **Disable Syntax Error Algorithms** to populate the domain without checking string values for syntax errors.</span></span>  
  
9. <span data-ttu-id="bf5dd-145">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-145">Click **OK**.</span></span>  
  
10. <span data-ttu-id="bf5dd-146">按一下 **[完成]** ，完成定義域管理活動，如＜ [結束定義域管理活動](../../2014/data-quality-services/end-the-domain-management-activity.md)＞中所述。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-146">Click **Finish** to complete the domain management activity, as described in [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md).</span></span>  
  
##  <a name="follow-up-after-creating-a-domain"></a><a name="FollowUp"></a> <span data-ttu-id="bf5dd-147">後續操作：建立定義域之後</span><span class="sxs-lookup"><span data-stu-id="bf5dd-147">Follow Up: After Creating a Domain</span></span>  
 <span data-ttu-id="bf5dd-148">在建立定義域之後，您可以針對定義域執行其他定義域管理工作、執行知識探索來將知識加入至定義域，或者將比對原則加入至定義域。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-148">After you create a domain, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="bf5dd-149">如需詳細資訊，請參閱[執行知識探索](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理定義域](../../2014/data-quality-services/managing-a-domain.md)或[建立比對原則](../../2014/data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="bf5dd-149">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
  
