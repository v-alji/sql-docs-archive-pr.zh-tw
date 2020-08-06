---
title: File 元素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- File element
ms.assetid: 73dce835-9a80-4aef-8e0f-9dcf07dd5b80
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0eeb2bdcc9513ca6283447daca63c8bbc4fa1726
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704582"
---
# <a name="file-element-dta"></a><span data-ttu-id="0053b-102">File 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="0053b-102">File Element (DTA)</span></span>
  <span data-ttu-id="0053b-103">指定工作負載檔。</span><span class="sxs-lookup"><span data-stu-id="0053b-103">Specifies the workload file.</span></span> <span data-ttu-id="0053b-104">工作負載是針對需要微調的一或多個資料庫來執行的一組 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0053b-104">A workload is a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against a database or databases that you want to tune.</span></span> <span data-ttu-id="0053b-105">工作負載檔可以是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼 (.sql) 或追蹤檔 (.trc)。</span><span class="sxs-lookup"><span data-stu-id="0053b-105">Workload files can be [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts (.sql) or trace files (.trc).</span></span> <span data-ttu-id="0053b-106">如需詳細資訊，請參閱 [啟動及使用 Database Engine Tuning Advisor](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="0053b-106">For more information, see [Start and Use the Database Engine Tuning Advisor](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0053b-107">語法</span><span class="sxs-lookup"><span data-stu-id="0053b-107">Syntax</span></span>  
  
```  
  
<DTAInput>  
  <Server>...</Server>  
  <Workload>  
    <File>...</File>  
  </Workload>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="0053b-108">元素特性</span><span class="sxs-lookup"><span data-stu-id="0053b-108">Element Characteristics</span></span>  
  
|<span data-ttu-id="0053b-109">特性</span><span class="sxs-lookup"><span data-stu-id="0053b-109">Characteristic</span></span>|<span data-ttu-id="0053b-110">描述</span><span class="sxs-lookup"><span data-stu-id="0053b-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="0053b-111">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="0053b-111">**Data type and length**</span></span>|<span data-ttu-id="0053b-112">請利用 `string` 資料類型來指定工作負載檔的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="0053b-112">Use the `string` data type to specify the directory path to your workload file.</span></span> <span data-ttu-id="0053b-113">例如：</span><span class="sxs-lookup"><span data-stu-id="0053b-113">For example:</span></span><br /><br /> `<File>C:\Tuning\tun.sql</File>`<br /><br /> <span data-ttu-id="0053b-114">伺服器強制實施長度限制。</span><span class="sxs-lookup"><span data-stu-id="0053b-114">Length limit is enforced by the server.</span></span>|  
|<span data-ttu-id="0053b-115">**預設值**</span><span class="sxs-lookup"><span data-stu-id="0053b-115">**Default value**</span></span>|<span data-ttu-id="0053b-116">無。</span><span class="sxs-lookup"><span data-stu-id="0053b-116">None.</span></span>|  
|<span data-ttu-id="0053b-117">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="0053b-117">**Occurrence**</span></span>|<span data-ttu-id="0053b-118">如果未指定任何其他工作負載類型，便需要使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="0053b-118">Required once if no other type of workload is specified.</span></span> <span data-ttu-id="0053b-119">您必須指定 **EventString**父系的 **File**、 **Database** 或 **Workload** 子元素，但只能使用一種類型。</span><span class="sxs-lookup"><span data-stu-id="0053b-119">You must specify an **EventString**, a **File**, or a **Database** child element for the **Workload** parent, but only one type can be used.</span></span> <span data-ttu-id="0053b-120">例如，如果您利用 **File** 元素指定了工作負載，便不能在相同 XML 輸入檔中，同時利用 **Database** 元素來指定工作負載。</span><span class="sxs-lookup"><span data-stu-id="0053b-120">For example, if you specify a workload with the **File** element, then you cannot also specify a workload with the **Database** element in the same XML input file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="0053b-121">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="0053b-121">Element Relationships</span></span>  
  
|<span data-ttu-id="0053b-122">關聯性</span><span class="sxs-lookup"><span data-stu-id="0053b-122">Relationship</span></span>|<span data-ttu-id="0053b-123">元素</span><span class="sxs-lookup"><span data-stu-id="0053b-123">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="0053b-124">**父元素**</span><span class="sxs-lookup"><span data-stu-id="0053b-124">**Parent element**</span></span>|[<span data-ttu-id="0053b-125">Workload 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0053b-125">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)|  
|<span data-ttu-id="0053b-126">**子元素**</span><span class="sxs-lookup"><span data-stu-id="0053b-126">**Child elements**</span></span>|<span data-ttu-id="0053b-127">無。</span><span class="sxs-lookup"><span data-stu-id="0053b-127">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0053b-128">範例</span><span class="sxs-lookup"><span data-stu-id="0053b-128">Example</span></span>  
 <span data-ttu-id="0053b-129">如需此元素的使用範例，請參閱[簡單 XML 輸入檔範例 &#40;DTA&#41;](simple-xml-input-file-sample-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="0053b-129">For a usage example of this element, see [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0053b-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0053b-130">See Also</span></span>  
 [<span data-ttu-id="0053b-131">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="0053b-131">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
