---
title: " (DTA) 的工作負載元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Workload element
ms.assetid: 68ffd473-6546-4015-98d0-3763165de65c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 20184760c3fcb5eed6c02b8f8fd9b63f5586c9af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594886"
---
# <a name="workload-element-dta"></a><span data-ttu-id="8780a-102">Workload 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="8780a-102">Workload Element (DTA)</span></span>
  <span data-ttu-id="8780a-103">指定微調工作階段所用的工作負載。</span><span class="sxs-lookup"><span data-stu-id="8780a-103">Specifies the workload to be used for a tuning session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8780a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8780a-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="8780a-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="8780a-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="8780a-106">特性</span><span class="sxs-lookup"><span data-stu-id="8780a-106">Characteristic</span></span>|<span data-ttu-id="8780a-107">描述</span><span class="sxs-lookup"><span data-stu-id="8780a-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="8780a-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="8780a-108">**Data type and length**</span></span>|<span data-ttu-id="8780a-109">無。</span><span class="sxs-lookup"><span data-stu-id="8780a-109">None.</span></span>|  
|<span data-ttu-id="8780a-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="8780a-110">**Default value**</span></span>|<span data-ttu-id="8780a-111">無。</span><span class="sxs-lookup"><span data-stu-id="8780a-111">None.</span></span>|  
|<span data-ttu-id="8780a-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="8780a-112">**Occurrence**</span></span>|<span data-ttu-id="8780a-113">每個 `DTAInput` 元素需要使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="8780a-113">Required once for each `DTAInput` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="8780a-114">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="8780a-114">Element Relationships</span></span>  
  
|<span data-ttu-id="8780a-115">關聯性</span><span class="sxs-lookup"><span data-stu-id="8780a-115">Relationship</span></span>|<span data-ttu-id="8780a-116">元素</span><span class="sxs-lookup"><span data-stu-id="8780a-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="8780a-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="8780a-117">**Parent element**</span></span>|[<span data-ttu-id="8780a-118">啟動及使用 Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="8780a-118">Start and Use the Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)|  
|<span data-ttu-id="8780a-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="8780a-119">**Child elements**</span></span>|[<span data-ttu-id="8780a-120">File 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8780a-120">File Element &#40;DTA&#41;</span></span>](file-element-dta.md)<br /><br /> [<span data-ttu-id="8780a-121">工作負載的 Database 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8780a-121">Database Element for Workload &#40;DTA&#41;</span></span>](database-element-for-workload-dta.md)<br /><br /> [<span data-ttu-id="8780a-122">EventString 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8780a-122">EventString Element &#40;DTA&#41;</span></span>](eventstring-element-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="8780a-123">備註</span><span class="sxs-lookup"><span data-stu-id="8780a-123">Remarks</span></span>  
 <span data-ttu-id="8780a-124">工作負載是針對需要微調的一或多個資料庫來執行的一組 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8780a-124">A workload is a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against a database or databases that you want to tune.</span></span> <span data-ttu-id="8780a-125">Database Engine Tuning Advisor 可以利用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼、追蹤檔和追蹤資料表來作為工作負載。</span><span class="sxs-lookup"><span data-stu-id="8780a-125">The Database Engine Tuning Advisor can use [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, trace files, and trace tables as workloads.</span></span>  
  
 <span data-ttu-id="8780a-126">如果您在 XML 輸入檔中指定工作負載，以及在命令列中利用 **dta** 工具來指定工作負載，就會利用命令列所指定的工作負載來進行微調。</span><span class="sxs-lookup"><span data-stu-id="8780a-126">If you specify a workload in an XML input file and a workload on the command line with the **dta** tool, the workload specified on the command line will be used for tuning.</span></span> <span data-ttu-id="8780a-127">命令列所指定的所有微調選項都會覆寫 XML 輸入檔中所指定的微調選項。</span><span class="sxs-lookup"><span data-stu-id="8780a-127">All tuning options specified on the command line override those that are specified in an XML input file.</span></span> <span data-ttu-id="8780a-128">XML 輸入檔中以評估模式輸入的使用者指定組態是唯一例外。</span><span class="sxs-lookup"><span data-stu-id="8780a-128">The only exception is if a user-specified configuration is entered in the evaluate mode in the XML input file.</span></span> <span data-ttu-id="8780a-129">例如，如果在 XML 輸入檔的 `Configuration` 元素中輸入了某項組態，`EvaluateConfiguration` 元素也指定成某個微調選項，XML 輸入檔所指定的微調選項會覆寫在命令列中輸入的任何微調選項。</span><span class="sxs-lookup"><span data-stu-id="8780a-129">For example, if a configuration is entered in the `Configuration` element of the XML input file and the `EvaluateConfiguration` element is also specified as one of the tuning options, the tuning options specified in the XML input file will override any tuning options entered at the command line.</span></span>  
  
 <span data-ttu-id="8780a-130">每個微調工作階段都必須指定一個工作負載。</span><span class="sxs-lookup"><span data-stu-id="8780a-130">One workload must be specified for each tuning session.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8780a-131">範例</span><span class="sxs-lookup"><span data-stu-id="8780a-131">Example</span></span>  
 <span data-ttu-id="8780a-132">下列程式碼範例會指定元素的**MyDatabase. mydatabase.mydbowner.tuningtable001. TuningTable001**追蹤資料表 `Workload` 。</span><span class="sxs-lookup"><span data-stu-id="8780a-132">The following code example specifies the **MyDatabase.MyDBOwner.TuningTable001** trace table for the `Workload` element.</span></span> <span data-ttu-id="8780a-133">搭配 SQL Server Profiler 使用微調範本來建立 **TuningTable001** ，並將這份追蹤輸出儲存成一份資料表。</span><span class="sxs-lookup"><span data-stu-id="8780a-133">The **TuningTable001** was created by using the Tuning template with SQL Server Profiler and saving the trace output as a table.</span></span>  
  
```  
<DTAXML ...>  
  <DTAInput>  
    <Server>  
...code removed here...  
    </Server>  
    <Workload>  
      <Database>  
        <Name>MyDatabase</Name>  
        <Schema>  
          <Name>MyDBOwner</Name>  
            <Table>  
              <Name>TuningTable001</Name>  
            </Table>  
        </Schema>  
      </Database>  
    </Workload>  
...code removed here...  
  </DTAInput>  
</DTAXML>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8780a-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8780a-134">See Also</span></span>  
 [<span data-ttu-id="8780a-135">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="8780a-135">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
