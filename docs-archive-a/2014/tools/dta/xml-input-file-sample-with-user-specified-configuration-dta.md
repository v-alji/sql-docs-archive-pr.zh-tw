---
title: 含使用者指定設定的 XML 輸入檔案範例 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- sample applications [DTA]
ms.assetid: b29c9716-e5c3-4003-9efb-3ade2197b630
author: stevestein
ms.author: sstein
ms.openlocfilehash: 121972518aa114e16cc81517d52a9d9656b067c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598089"
---
# <a name="xml-input-file-sample-with-user-specified-configuration-dta"></a><span data-ttu-id="ecb10-102">含使用者指定組態的 XML 輸入檔範例 (DTA)</span><span class="sxs-lookup"><span data-stu-id="ecb10-102">XML Input File Sample with User-specified Configuration (DTA)</span></span>
  <span data-ttu-id="ecb10-103">請複製利用 **Configuration** 元素指定使用者指定組態的這個 XML 輸入檔範例，再將它貼到您喜愛的 XML 編輯器或文字編輯器中。</span><span class="sxs-lookup"><span data-stu-id="ecb10-103">Copy and paste this sample of an XML input file that specifies a user-specified configuration with the **Configuration** element into your favorite XML editor or text editor.</span></span> <span data-ttu-id="ecb10-104">這可讓您進行「假設」分析。</span><span class="sxs-lookup"><span data-stu-id="ecb10-104">This enables you to perform "what-if" analysis.</span></span> <span data-ttu-id="ecb10-105">「假設」分析包括利用 **Configuration** 元素來指定您要微調之資料庫的一組假設性實體設計結構。</span><span class="sxs-lookup"><span data-stu-id="ecb10-105">"What-if" analysis involves using the **Configuration** element to specify a set of hypothetical physical design structures for the database you want to tune.</span></span> <span data-ttu-id="ecb10-106">之後，您再利用 Database Engine Tuning Advisor 來分析針對這個假設性組態來執行工作負載的效果，以了解它是否能夠改進查詢的處理效能。</span><span class="sxs-lookup"><span data-stu-id="ecb10-106">Then you use Database Engine Tuning Advisor to analyze the effects of running a workload against this hypothetical configuration to find out whether it improves query processing performance.</span></span> <span data-ttu-id="ecb10-107">這類分析的好處是既能夠評估新的組態，又免除了實際實作的負擔。</span><span class="sxs-lookup"><span data-stu-id="ecb10-107">This type of analysis provides the advantage of evaluating the new configuration without incurring the overhead of actually implementing it.</span></span> <span data-ttu-id="ecb10-108">如果假設性組態所改進的效能不符需求，您很容易改變它，再分析它，直到產生的結果符合需求的組態出現為止。</span><span class="sxs-lookup"><span data-stu-id="ecb10-108">If your hypothetical configuration does not provide the performance improvements you want, it is easy to change it and analyze it again until you reach the configuration that produces the results you need.</span></span>  
  
 <span data-ttu-id="ecb10-109">將這個範例複製到編輯工具之後，請利用您的特定微調工作階段的各個值來取代指定給 **Server**、 **Database**、 **Schema**、 **Table**、 **Workload**、 **TuningOptions**和 **Configuration** 等元素的值。</span><span class="sxs-lookup"><span data-stu-id="ecb10-109">After copying this sample into your editing tool, replace the values specified for the **Server**, **Database**, **Schema**, **Table**, **Workload**, **TuningOptions**, and **Configuration** elements with those for your specific tuning session.</span></span> <span data-ttu-id="ecb10-110">如需可以搭配這些元素來使用的所有屬性和子元素的詳細資訊，請參閱 [XML 輸入檔參考 &#40;Database Engine Tuning Advisor&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="ecb10-110">For more information about all of the attributes and child elements that you can use with these elements, see the [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](xml-input-file-reference-database-engine-tuning-advisor.md).</span></span> <span data-ttu-id="ecb10-111">下列範例只用到部份可用的屬性及子元素選項。</span><span class="sxs-lookup"><span data-stu-id="ecb10-111">The following sample uses only a subset of available attribute and child element options.</span></span>  
  
## <a name="code"></a><span data-ttu-id="ecb10-112">程式碼</span><span class="sxs-lookup"><span data-stu-id="ecb10-112">Code</span></span>  
 [!code-xml[InputFileSamples#UserSpecifiedConfigInputFile](../../snippets/xml/SQL14/dta_xml/inputfilesamples/xml/dta_xml_input_file_samples.xml#userspecifiedconfiginputfile)]  
  
## <a name="comments"></a><span data-ttu-id="ecb10-113">註解</span><span class="sxs-lookup"><span data-stu-id="ecb10-113">Comments</span></span>  
  
-   <span data-ttu-id="ecb10-114">如果您指定了 **Configuration** 元素的 **Absolute** 模式 (`Configuration SpecificationMode="Absolute"`)，便不支援卸除實體設計結構。</span><span class="sxs-lookup"><span data-stu-id="ecb10-114">Dropping physical design structures is not supported if you specify the **Absolute** mode for the **Configuration** element (`Configuration SpecificationMode="Absolute"`).</span></span>  
  
-   <span data-ttu-id="ecb10-115">您無法在**Configuration** 元素的任何一個模式 ( **Relative**或 **Absolute** ) 中，建立和卸除相同的實體設計結構。</span><span class="sxs-lookup"><span data-stu-id="ecb10-115">You cannot create and drop the same physical design structure in either mode (**Relative** or **Absolute**) of the **Configuration** element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb10-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecb10-116">See Also</span></span>  
 <span data-ttu-id="ecb10-117">[啟動及使用 Database Engine Tuning Advisor](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="ecb10-117">[Start and Use the Database Engine Tuning Advisor](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md) </span></span>  
 <span data-ttu-id="ecb10-118">[檢視及處理 Database Engine Tuning Advisor 的輸出](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="ecb10-118">[View and Work with the Output from the Database Engine Tuning Advisor](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md) </span></span>  
 [<span data-ttu-id="ecb10-119">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="ecb10-119">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
