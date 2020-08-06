---
title: 管理定義域 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: c5ab71a3-0dac-45b1-be8e-93bf7e0e03ce
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 67f58df490bca5a811442fb33805ceb546de92d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592264"
---
# <a name="managing-a-domain"></a><span data-ttu-id="82491-102">管理定義域</span><span class="sxs-lookup"><span data-stu-id="82491-102">Managing a Domain</span></span>
  <span data-ttu-id="82491-103">此主題描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中使用定義域。</span><span class="sxs-lookup"><span data-stu-id="82491-103">This topic describes the use of domains in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="82491-104">定義域包含要分析之資料來源中特定欄位內之資料的語意表示法。</span><span class="sxs-lookup"><span data-stu-id="82491-104">A domain contains a semantic representation of the data in a specific field in the data source that is to be analyzed.</span></span> <span data-ttu-id="82491-105">定義域是您為資料來源建立之知識庫的一部分，而且您藉由分析取樣資料來源或匯入資料所建立的知識會加入至知識庫中所定義的定義域。</span><span class="sxs-lookup"><span data-stu-id="82491-105">A domain is part of the knowledge base that you create for a data source, and the knowledge that you build up by analyzing a sample data source, or importing data, is added to the domains defined in the knowledge base.</span></span> <span data-ttu-id="82491-106">之後會使用這些定義域中的知識，於資料品質專案中執行清理和比對。</span><span class="sxs-lookup"><span data-stu-id="82491-106">The knowledge in those domains is later used to perform cleansing and matching in a data quality project.</span></span> <span data-ttu-id="82491-107">定義域位於 Data Quality Services 中所有活動的核心。</span><span class="sxs-lookup"><span data-stu-id="82491-107">Domains are at the core of all activities in Data Quality Services.</span></span>  
  
 <span data-ttu-id="82491-108">定義域會對應至資料來源欄位，而且會在知識探索、定義域管理和比對活動中擴展。</span><span class="sxs-lookup"><span data-stu-id="82491-108">A domain is mapped to a data source field, and is populated in the knowledge discovery, domain management, and matching activities.</span></span> <span data-ttu-id="82491-109">定義域屬性中會定義要如何從資料來源及報表中的輸出資料載入資料。</span><span class="sxs-lookup"><span data-stu-id="82491-109">How you load data from the data source and output data in a report is defined in domain properties.</span></span> <span data-ttu-id="82491-110">當您使用參考資料提供者來清理資料時，您會將參考資料服務附加至單一或複合定義域。</span><span class="sxs-lookup"><span data-stu-id="82491-110">When you use a reference data provider to cleanse data, you attach a reference data service to a single or composite domain.</span></span> <span data-ttu-id="82491-111">您會在定義域中建立要套用至資料的規則，而且您可以為定義域建立以詞彙為主的關聯。</span><span class="sxs-lookup"><span data-stu-id="82491-111">You create rules to be applied to your data in a domain, and you can create term-based relations for a domain.</span></span> <span data-ttu-id="82491-112">您可以檢視及更正定義域中的資料。</span><span class="sxs-lookup"><span data-stu-id="82491-112">You can view and correct data in the domain.</span></span>  
  
 <span data-ttu-id="82491-113">您也可以建立由兩個或多個個別定義域所組成的複合定義域，其中每一個定義域都包含有關一般資料的知識。</span><span class="sxs-lookup"><span data-stu-id="82491-113">You can also create a composite domain that is comprised of two or more individual domains that each contains knowledge about common data.</span></span> <span data-ttu-id="82491-114">如需詳細資訊，請參閱[管理複合定義域](../../2014/data-quality-services/managing-a-composite-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="82491-114">For more information, see [Managing a Composite Domain](../../2014/data-quality-services/managing-a-composite-domain.md).</span></span>  
  
## <a name="domain-properties"></a><span data-ttu-id="82491-115">定義域屬性</span><span class="sxs-lookup"><span data-stu-id="82491-115">Domain Properties</span></span>  
 <span data-ttu-id="82491-116">當您建立定義域時，您可以選擇以下方式從來源資料擴展定義域以及輸出定義域值。</span><span class="sxs-lookup"><span data-stu-id="82491-116">When you create a domain, you have the following options for how to populate the domain from the source data and how to output the domain values.</span></span> <span data-ttu-id="82491-117">如需詳細資訊，請參閱[設定定義域屬性](../../2014/data-quality-services/set-domain-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="82491-117">For more information, see [Set Domain Properties](../../2014/data-quality-services/set-domain-properties.md).</span></span>  
  
-   <span data-ttu-id="82491-118">選取您要用來擴展定義域的資料類型。</span><span class="sxs-lookup"><span data-stu-id="82491-118">Select the type of the data that you populate the domain with.</span></span> <span data-ttu-id="82491-119">如需有關每種定義域資料類型所支援之資料類型的詳細資訊，請參閱＜ [DQS 定義域支援的 SQL Server 和 SSIS 資料類型](../../2014/data-quality-services/supported-sql-server-and-ssis-data-types-for-dqs-domains.md)＞。</span><span class="sxs-lookup"><span data-stu-id="82491-119">For information about data types supported for each domain data type, see [Supported SQL Server and SSIS Data Types for DQS Domains](../../2014/data-quality-services/supported-sql-server-and-ssis-data-types-for-dqs-domains.md).</span></span>  
  
-   <span data-ttu-id="82491-120">指定只有前置值 (而非其同義字) 將會是定義域中的輸出。</span><span class="sxs-lookup"><span data-stu-id="82491-120">Specify that only leading values, not their synonyms, will be output from the domain.</span></span>  
  
-   <span data-ttu-id="82491-121">根據資料類型指定定義域值應該是某種格式的輸出。</span><span class="sxs-lookup"><span data-stu-id="82491-121">Specify that domain values be output in a certain format, depending on the data type.</span></span>  
  
-   <span data-ttu-id="82491-122">如果資料類型是字串，從資料來源將此字串載入定義域時，您可以移除特殊字元來將此字串標準化。</span><span class="sxs-lookup"><span data-stu-id="82491-122">If the data type is a string, you can normalize the string by removing special characters when the string is loaded from the data source into the domain.</span></span>  
  
-   <span data-ttu-id="82491-123">如果資料類型是字串，您可以執行 DQS 拼字檢查來檢查字串的語法、拼字和句子結構，並在 **[定義域管理]** 的 **[定義域值]** 頁面中指示任何潛在錯誤。</span><span class="sxs-lookup"><span data-stu-id="82491-123">If the data type is a string, you can run the DQS Speller to check the syntax, spelling, and sentence structure of the string, and indicate any potential errors in the **Domain Values** page of **Domain Management**.</span></span> <span data-ttu-id="82491-124">其中包括指定執行拼字檢查所使用的語言。</span><span class="sxs-lookup"><span data-stu-id="82491-124">This includes specifying the language that the Speller will run in.</span></span>  
  
-   <span data-ttu-id="82491-125">如果資料類型是字串，當您知道語法錯誤不會出現在字串中時，您可以指定 DQS 不會識別語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="82491-125">If the data type is a string, you can specify that DQS not identify syntax errors when you know that syntax errors will not occur in strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="82491-126">本節內容</span><span class="sxs-lookup"><span data-stu-id="82491-126">In This Section</span></span>  
 <span data-ttu-id="82491-127">使用定義域可讓您執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="82491-127">Using a domain enables you to do the following:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="82491-128">針對具有特定資料類型的資料欄位建立語意表示法、指定如何擴展定義域，以及設定定義域輸出的格式</span><span class="sxs-lookup"><span data-stu-id="82491-128">Create a semantic representation for a data field with a specific data type, specify how the domain is populated, and format the output of the domain</span></span>|[<span data-ttu-id="82491-129">建立定義域</span><span class="sxs-lookup"><span data-stu-id="82491-129">Create a Domain</span></span>](../../2014/data-quality-services/create-a-domain.md)|  
|<span data-ttu-id="82491-130">將定義域連結到另一個定義域，讓它共用相同的設定與值</span><span class="sxs-lookup"><span data-stu-id="82491-130">Link a domain to another domain, enabling it to share the same settings and values</span></span>|[<span data-ttu-id="82491-131">建立連結的定義域</span><span class="sxs-lookup"><span data-stu-id="82491-131">Create a Linked Domain</span></span>](../../2014/data-quality-services/create-a-linked-domain.md)|  
|<span data-ttu-id="82491-132">將參考資料服務附加至單一或複合定義域</span><span class="sxs-lookup"><span data-stu-id="82491-132">Attach a reference data service to a single or composite domain</span></span>|[<span data-ttu-id="82491-133">將定義域或複合定義域附加至參考資料</span><span class="sxs-lookup"><span data-stu-id="82491-133">Attach a Domain or Composite Domain to Reference Data</span></span>](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)|  
|<span data-ttu-id="82491-134">變更或增加知識庫中的值</span><span class="sxs-lookup"><span data-stu-id="82491-134">Change or augment the values in a knowledge base</span></span>|[<span data-ttu-id="82491-135">變更定義域值</span><span class="sxs-lookup"><span data-stu-id="82491-135">Change Domain Values</span></span>](../../2014/data-quality-services/change-domain-values.md)|  
|<span data-ttu-id="82491-136">使用驗證和標準化規則</span><span class="sxs-lookup"><span data-stu-id="82491-136">Use validation and standardization rules</span></span>|[<span data-ttu-id="82491-137">建立定義域規則</span><span class="sxs-lookup"><span data-stu-id="82491-137">Create a Domain Rule</span></span>](../../2014/data-quality-services/create-a-domain-rule.md)|  
|<span data-ttu-id="82491-138">使用關聯來更正屬於定義域值之一部分的詞彙</span><span class="sxs-lookup"><span data-stu-id="82491-138">Use relations to correct a term that is part of a value in a domain</span></span>|[<span data-ttu-id="82491-139">建立以詞彙為主的關聯</span><span class="sxs-lookup"><span data-stu-id="82491-139">Create Term-Based Relations</span></span>](../../2014/data-quality-services/create-term-based-relations.md)|  
|<span data-ttu-id="82491-140">完成、關閉或取消定義域管理活動</span><span class="sxs-lookup"><span data-stu-id="82491-140">Complete, close, or cancel the domain management activity</span></span>|[<span data-ttu-id="82491-141">結束定義域管理活動</span><span class="sxs-lookup"><span data-stu-id="82491-141">End the Domain Management Activity</span></span>](../../2014/data-quality-services/end-the-domain-management-activity.md)|  
  
## <a name="related-tasks"></a><span data-ttu-id="82491-142">相關工作</span><span class="sxs-lookup"><span data-stu-id="82491-142">Related Tasks</span></span>  
  
|<span data-ttu-id="82491-143">工作描述</span><span class="sxs-lookup"><span data-stu-id="82491-143">Task Description</span></span>|<span data-ttu-id="82491-144">主題</span><span class="sxs-lookup"><span data-stu-id="82491-144">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="82491-145">藉由執行知識探索以及以互動方式管理知識來建立知識庫</span><span class="sxs-lookup"><span data-stu-id="82491-145">Building a knowledge base by running knowledge discovery and interactively managing knowledge</span></span>|[<span data-ttu-id="82491-146">建立知識庫</span><span class="sxs-lookup"><span data-stu-id="82491-146">Building a Knowledge Base</span></span>](../../2014/data-quality-services/building-a-knowledge-base.md)|  
|<span data-ttu-id="82491-147">將知識匯入知識庫或是從知識庫匯出知識。</span><span class="sxs-lookup"><span data-stu-id="82491-147">Importing knowledge into, or exporting it from, a knowledge base.</span></span>|[<span data-ttu-id="82491-148">匯入和匯出知識</span><span class="sxs-lookup"><span data-stu-id="82491-148">Importing and Exporting Knowledge</span></span>](../../2014/data-quality-services/importing-and-exporting-knowledge.md)|  
|<span data-ttu-id="82491-149">建立複合定義域，並將知識加入至定義域。</span><span class="sxs-lookup"><span data-stu-id="82491-149">Creating a composite domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="82491-150">管理複合定義域</span><span class="sxs-lookup"><span data-stu-id="82491-150">Managing a Composite Domain</span></span>](../../2014/data-quality-services/managing-a-composite-domain.md)|  
  
  
