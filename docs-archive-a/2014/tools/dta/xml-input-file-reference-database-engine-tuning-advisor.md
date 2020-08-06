---
title: XML 輸入檔參考 (Database Engine Tuning Advisor) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], XML input files
- input file reference [Database Engine Tuning Advisor]
- XML input files [Database Engine Tuning Advisor]
ms.assetid: 05e5e5f0-d6df-4336-b18e-e9bc2835a766
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3bbd38299e4921db33cbaf318883c2f0a9041d92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708857"
---
# <a name="xml-input-file-reference-database-engine-tuning-advisor"></a><span data-ttu-id="7880d-102">XML 輸入檔參考 (Database Engine Tuning Advisor)</span><span class="sxs-lookup"><span data-stu-id="7880d-102">XML Input File Reference (Database Engine Tuning Advisor)</span></span>
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="7880d-103">Tuning Advisor 可以利用 XML 輸入檔來微調資料庫。</span><span class="sxs-lookup"><span data-stu-id="7880d-103">Tuning Advisor can use an XML input file to tune a database.</span></span> <span data-ttu-id="7880d-104">這個 XML 檔會指定微調工作階段要使用哪些資料庫、資料表、工作負載檔或資料表，以及微調選項。</span><span class="sxs-lookup"><span data-stu-id="7880d-104">This XML file designates which databases, tables, workload files or tables, and tuning options to use for the tuning session.</span></span> <span data-ttu-id="7880d-105">您也可以利用這個檔案來指定使用者指定的組態，以執行「假設」分析。</span><span class="sxs-lookup"><span data-stu-id="7880d-105">You can also use this file to specify a user-specified configuration to perform "what-if" analysis.</span></span>  
  
 <span data-ttu-id="7880d-106">[!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML 輸入檔包含 XML 元素的階層，每個元素都包含指定微調工作階段設定的文字或其他元素。</span><span class="sxs-lookup"><span data-stu-id="7880d-106">A [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML input file contains a hierarchy of XML elements, each containing text or other elements that specify the tuning session settings.</span></span> <span data-ttu-id="7880d-107">[!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML 輸入檔必須符合格式正確之 XML 的標準，因此，所有元素名稱都會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="7880d-107">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML input file must conform to the standards for well-formed XML, so all element names are case sensitive.</span></span> <span data-ttu-id="7880d-108">元素利用 Pascal 案例來指定，這表示第一個字元是大寫，任何後續串連單字的第一個字母也是大寫。</span><span class="sxs-lookup"><span data-stu-id="7880d-108">Elements are specified using Pascal case, which means that the first character is uppercase and the first letter of any subsequent concatenated word is uppercase.</span></span>  
  
 <span data-ttu-id="7880d-109">所有元素值都必須符合 XML 命名慣例。</span><span class="sxs-lookup"><span data-stu-id="7880d-109">All element values must conform to XML naming conventions.</span></span> <span data-ttu-id="7880d-110">如需有關這些慣例的詳細資訊，請參閱 MSDN Library 中的＜ [XML Textual Content](https://go.microsoft.com/fwlink/?LinkId=7614) ＞。</span><span class="sxs-lookup"><span data-stu-id="7880d-110">For more information about these conventions, see [XML Textual Content](https://go.microsoft.com/fwlink/?LinkId=7614) in the MSDN Library.</span></span>  
  
 <span data-ttu-id="7880d-111">請注意，這份參考並不完整。</span><span class="sxs-lookup"><span data-stu-id="7880d-111">Note that this reference is not comprehensive.</span></span> <span data-ttu-id="7880d-112">如需有關可用來定義 XML 輸入之所有元素的資訊，請參閱＜ [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML 結構描述 (DTASchema.xsd)＞。</span><span class="sxs-lookup"><span data-stu-id="7880d-112">For information about all the elements you can use to define XML input, refer to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema, DTASchema.xsd.</span></span>  
  
## <a name="xml-declaration"></a><span data-ttu-id="7880d-113">XML 宣告</span><span class="sxs-lookup"><span data-stu-id="7880d-113">XML Declaration</span></span>  
  
-   [<span data-ttu-id="7880d-114">XML 資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-114">XML Data &#40;SQL Server&#41;</span></span>](../../relational-databases/xml/xml-data-sql-server.md)  
  
## <a name="dtaxml-root-element"></a><span data-ttu-id="7880d-115">DTAXML 根元素</span><span class="sxs-lookup"><span data-stu-id="7880d-115">DTAXML Root Element</span></span>  
  
-   [<span data-ttu-id="7880d-116">DTAXML 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-116">DTAXML Element &#40;DTA&#41;</span></span>](dtaxml-element-dta.md)  
  
## <a name="dtainput-elements"></a><span data-ttu-id="7880d-117">DTAInput 元素</span><span class="sxs-lookup"><span data-stu-id="7880d-117">DTAInput Elements</span></span>  
  
-   [<span data-ttu-id="7880d-118">DTAInput 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-118">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)  
  
-   [<span data-ttu-id="7880d-119">Server 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-119">Server Element &#40;DTA&#41;</span></span>](server-element-dta.md)  
  
-   [<span data-ttu-id="7880d-120">Workload 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-120">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)  
  
-   [<span data-ttu-id="7880d-121">TuningOptions 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-121">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)  
  
-   [<span data-ttu-id="7880d-122">Configuration 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-122">Configuration Element &#40;DTA&#41;</span></span>](configuration-element-dta.md)  
  
## <a name="server-elements"></a><span data-ttu-id="7880d-123">伺服器元素</span><span class="sxs-lookup"><span data-stu-id="7880d-123">Server Elements</span></span>  
  
-   [<span data-ttu-id="7880d-124">伺服器的 Name 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-124">Name Element for Server &#40;DTA&#41;</span></span>](name-element-for-server-dta.md)  
  
-   [<span data-ttu-id="7880d-125">伺服器的 Database 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-125">Database Element for Server &#40;DTA&#41;</span></span>](database-element-for-server-dta.md)  
  
## <a name="workload-elements"></a><span data-ttu-id="7880d-126">工作負載元素</span><span class="sxs-lookup"><span data-stu-id="7880d-126">Workload Elements</span></span>  
  
-   [<span data-ttu-id="7880d-127">File 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-127">File Element &#40;DTA&#41;</span></span>](file-element-dta.md)  
  
-   [<span data-ttu-id="7880d-128">工作負載的 Database 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-128">Database Element for Workload &#40;DTA&#41;</span></span>](database-element-for-workload-dta.md)  
  
-   [<span data-ttu-id="7880d-129">EventString 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-129">EventString Element &#40;DTA&#41;</span></span>](eventstring-element-dta.md)  
  
## <a name="tuning-options-elements"></a><span data-ttu-id="7880d-130">微調選項元素</span><span class="sxs-lookup"><span data-stu-id="7880d-130">Tuning Options Elements</span></span>  
  
-   [<span data-ttu-id="7880d-131">TuningTimeInMin 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-131">TuningTimeInMin Element &#40;DTA&#41;</span></span>](tuningtimeinmin-element-dta.md)  
  
-   [<span data-ttu-id="7880d-132">StorageBoundInMB 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-132">StorageBoundInMB Element &#40;DTA&#41;</span></span>](storageboundinmb-element-dta.md)  
  
-   [<span data-ttu-id="7880d-133">TestServer 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-133">TestServer Element &#40;DTA&#41;</span></span>](testserver-element-dta.md)  
  
-   [<span data-ttu-id="7880d-134">FeatureSet 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-134">FeatureSet Element &#40;DTA&#41;</span></span>](featureset-element-dta.md)  
  
-   [<span data-ttu-id="7880d-135">Partitioning 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-135">Partitioning Element &#40;DTA&#41;</span></span>](partitioning-element-dta.md)  
  
-   [<span data-ttu-id="7880d-136">DropOnlyMode 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-136">DropOnlyMode Element &#40;DTA&#41;</span></span>](droponlymode-element-dta.md)  
  
-   [<span data-ttu-id="7880d-137">KeepExisting 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-137">KeepExisting Element &#40;DTA&#41;</span></span>](keepexisting-element-dta.md)  
  
-   [<span data-ttu-id="7880d-138">OnlineIndexOperation 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-138">OnlineIndexOperation Element &#40;DTA&#41;</span></span>](onlineindexoperation-element-dta.md)  
  
-   [<span data-ttu-id="7880d-139">DatabaseToConnect 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-139">DatabaseToConnect Element &#40;DTA&#41;</span></span>](databasetoconnect-element-dta.md)  
  
## <a name="configuration-elements"></a><span data-ttu-id="7880d-140">組態元素</span><span class="sxs-lookup"><span data-stu-id="7880d-140">Configuration Elements</span></span>  
  
-   [<span data-ttu-id="7880d-141">組態的 Server 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-141">Server Element for Configuration &#40;DTA&#41;</span></span>](server-element-for-configuration-dta.md)  
  
-   [<span data-ttu-id="7880d-142">組態的 Database 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-142">Database Element for Configuration &#40;DTA&#41;</span></span>](database-element-for-configuration-dta.md)  
  
-   [<span data-ttu-id="7880d-143">Recommendation 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-143">Recommendation Element &#40;DTA&#41;</span></span>](recommendation-element-dta.md)  
  
-   [<span data-ttu-id="7880d-144">Create 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-144">Create Element &#40;DTA&#41;</span></span>](create-element-dta.md)  
  
-   [<span data-ttu-id="7880d-145">Index 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-145">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)  
  
-   [<span data-ttu-id="7880d-146">索引的 Name 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-146">Name Element for Index &#40;DTA&#41;</span></span>](name-element-for-index-dta.md)  
  
-   [<span data-ttu-id="7880d-147">索引的 Column 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-147">Column Element for Index &#40;DTA&#41;</span></span>](column-element-for-index-dta.md)  
  
-   [<span data-ttu-id="7880d-148">資料行的 Name 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-148">Name Element for Column &#40;DTA&#41;</span></span>](name-element-for-column-dta.md)  
  
-   [<span data-ttu-id="7880d-149">索引的 Filegroup 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-149">Filegroup Element for Index &#40;DTA&#41;</span></span>](filegroup-element-for-index-dta.md)  
  
## <a name="database-elements"></a><span data-ttu-id="7880d-150">資料庫元素</span><span class="sxs-lookup"><span data-stu-id="7880d-150">Database Elements</span></span>  
  
-   [<span data-ttu-id="7880d-151">資料庫的 Name 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-151">Name Element for Database &#40;DTA&#41;</span></span>](name-element-for-database-dta.md)  
  
-   [<span data-ttu-id="7880d-152">資料庫的 Schema 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-152">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)  
  
-   [<span data-ttu-id="7880d-153">結構描述的 Name 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-153">Name Element for Schema &#40;DTA&#41;</span></span>](name-element-for-schema-dta.md)  
  
-   [<span data-ttu-id="7880d-154">結構描述的 Table 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-154">Table Element for Schema &#40;DTA&#41;</span></span>](table-element-for-schema-dta.md)  
  
-   [<span data-ttu-id="7880d-155">資料表的 Name 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7880d-155">Name Element for Table &#40;DTA&#41;</span></span>](name-element-for-table-dta.md)  
  
## <a name="see-also"></a><span data-ttu-id="7880d-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7880d-156">See Also</span></span>  
 [<span data-ttu-id="7880d-157">Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="7880d-157">Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
