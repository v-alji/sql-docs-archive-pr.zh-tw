---
title: Issue 元素 (ssbdiagnose) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- issue element
- XML output file format [ssbdiagnose], issue element
- ssbdiagnose
ms.assetid: 2246a886-686b-44ca-9771-b155cedad8be
author: stevestein
ms.author: sstein
ms.openlocfilehash: a178c1323c1c20f84e67d4d7699fc313090a4c71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686571"
---
# <a name="issue-element-ssbdiagnose"></a><span data-ttu-id="53a09-102">Issue 元素 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="53a09-102">Issue Element (ssbdiagnose)</span></span>
  <span data-ttu-id="53a09-103">報告 **ssbdiagnose** 公用程式所發現的問題。</span><span class="sxs-lookup"><span data-stu-id="53a09-103">Reports an issue that was found by the **ssbdiagnose** utility.</span></span> <span data-ttu-id="53a09-104">**ssbdiagnose** XML 輸出檔案中每個報告的問題都有一個 Issue 元素。</span><span class="sxs-lookup"><span data-stu-id="53a09-104">The **ssbdiagnose** XML output file has one Issue element per issue reported.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53a09-105">語法</span><span class="sxs-lookup"><span data-stu-id="53a09-105">Syntax</span></span>  
  
```  
  
<Issue  
    type="..."   
    code="..."   
    server="..."   
    database="..."   
    object="...">   
    ...   
</Issue>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="53a09-106">元素屬性</span><span class="sxs-lookup"><span data-stu-id="53a09-106">Element Attributes</span></span>  
  
|<span data-ttu-id="53a09-107">屬性</span><span class="sxs-lookup"><span data-stu-id="53a09-107">Attribute</span></span>|<span data-ttu-id="53a09-108">描述</span><span class="sxs-lookup"><span data-stu-id="53a09-108">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="53a09-109">識別 Issue 元素所報告的問題類別：</span><span class="sxs-lookup"><span data-stu-id="53a09-109">Identifies which category of problem the Issue element is reporting:</span></span><br /><br /> <span data-ttu-id="53a09-110">**「診斷」** ：報告在您分析 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 設定時發現的設定問題。</span><span class="sxs-lookup"><span data-stu-id="53a09-110">**"Diagnosis"** Reports a configuration issue found when you analyze a [!INCLUDE[ssSB](../../includes/sssb-md.md)] configuration.</span></span><br /><br /> <span data-ttu-id="53a09-111">**「問題」** ：報告讓 **ssbdiagnose** 無法完成其分析的問題。</span><span class="sxs-lookup"><span data-stu-id="53a09-111">**"Problem"** Reports an issue that has prevented **ssbdiagnose** from completing its analysis.</span></span> <span data-ttu-id="53a09-112">請更正問題並重新執行 **ssbdiagnose**。</span><span class="sxs-lookup"><span data-stu-id="53a09-112">Correct the problem and rerun **ssbdiagnose**.</span></span><br /><br /> <span data-ttu-id="53a09-113">**「事件」** ：報告在您執行 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] -RUNTIME **檢查時發現的** 事件。</span><span class="sxs-lookup"><span data-stu-id="53a09-113">**"Event"** Reports a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] event found when you run a **-RUNTIME** check.</span></span> <span data-ttu-id="53a09-114">只有在您指定 **-SHOWEVENTS** 時才會報告事件。</span><span class="sxs-lookup"><span data-stu-id="53a09-114">Events are only reported if **-SHOWEVENTS** is specified.</span></span>|  
|`code`|<span data-ttu-id="53a09-115">識別訊息的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="53a09-115">Identifies the error number for the message.</span></span>|  
|`server`|<span data-ttu-id="53a09-116">識別在其中發現問題的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="53a09-116">Identifies the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in which the problem was found.</span></span> <span data-ttu-id="53a09-117">如果問題位於預設執行個體中，server 屬性就只有電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="53a09-117">If the problem was in a default instance, the server attribute only has the computer name.</span></span> <span data-ttu-id="53a09-118">如果問題位於具名執行個體中，server 屬性就會採用 ComputerName\InstanceName 的格式。</span><span class="sxs-lookup"><span data-stu-id="53a09-118">If the problem was in a named instance, the server attribute is in the form ComputerName\InstanceName.</span></span>|  
|`database`|<span data-ttu-id="53a09-119">識別在其中發現問題的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="53a09-119">Identifies the name of the database in which the problem was found.</span></span>|  
|`object`|<span data-ttu-id="53a09-120">識別在其中發現問題的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="53a09-120">Identifies the name of the object in which the problem was found.</span></span> <span data-ttu-id="53a09-121">如果問題是執行個體或資料庫層級問題，object 屬性就會重複執行個體或資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="53a09-121">If the problem was an instance or database level issue, the object attribute repeats the instance or database name.</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="53a09-122">元素特性</span><span class="sxs-lookup"><span data-stu-id="53a09-122">Element Characteristics</span></span>  
  
|<span data-ttu-id="53a09-123">特性</span><span class="sxs-lookup"><span data-stu-id="53a09-123">Characteristic</span></span>|<span data-ttu-id="53a09-124">描述</span><span class="sxs-lookup"><span data-stu-id="53a09-124">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="53a09-125">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="53a09-125">**Data type and length**</span></span>|<span data-ttu-id="53a09-126">`string`，沒有長度限制。</span><span class="sxs-lookup"><span data-stu-id="53a09-126">`string`, length is unlimited.</span></span>|  
|<span data-ttu-id="53a09-127">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="53a09-127">**Value**</span></span>|<span data-ttu-id="53a09-128">傳回錯誤訊息的文字。</span><span class="sxs-lookup"><span data-stu-id="53a09-128">Returns the text of the error message.</span></span>|  
|<span data-ttu-id="53a09-129">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="53a09-129">**Occurrence**</span></span>|<span data-ttu-id="53a09-130">每個報告的錯誤出現一次。</span><span class="sxs-lookup"><span data-stu-id="53a09-130">Once per reported error.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="53a09-131">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="53a09-131">Element Relationships</span></span>  
  
|<span data-ttu-id="53a09-132">關聯性</span><span class="sxs-lookup"><span data-stu-id="53a09-132">Relationship</span></span>|<span data-ttu-id="53a09-133">元素</span><span class="sxs-lookup"><span data-stu-id="53a09-133">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="53a09-134">**父元素**</span><span class="sxs-lookup"><span data-stu-id="53a09-134">**Parent element**</span></span>|[<span data-ttu-id="53a09-135">DiagnosticInformation 元素 &#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="53a09-135">DiagnosticInformation Element &#40;ssbdiagnose&#41;</span></span>](diagnosticinformation-element-ssbdiagnose.md)|  
|<span data-ttu-id="53a09-136">**子元素**</span><span class="sxs-lookup"><span data-stu-id="53a09-136">**Child elements**</span></span>|<span data-ttu-id="53a09-137">None</span><span class="sxs-lookup"><span data-stu-id="53a09-137">None</span></span>|  
  
## <a name="example"></a><span data-ttu-id="53a09-138">範例</span><span class="sxs-lookup"><span data-stu-id="53a09-138">Example</span></span>  
 <span data-ttu-id="53a09-139">這個元素會針對沒有主要金鑰的資料庫報告 1102 錯誤，而這項錯誤是在您分析 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 組態時發現的。</span><span class="sxs-lookup"><span data-stu-id="53a09-139">This element reports an 1102 error for a database that does not have a master key, where the error was found when you analyzed a [!INCLUDE[ssSB](../../includes/sssb-md.md)] configuration.</span></span>  
  
```  
<Issue type="Diagnosis" code="1102" server="TestComputer" database="TargetDB" object="TargetDB">The master key was not found</diagnostic>  
```  
  
## <a name="see-also"></a><span data-ttu-id="53a09-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53a09-140">See Also</span></span>  
 [<span data-ttu-id="53a09-141">ssbdiagnose 公用程式 &#40;Service Broker&#41;</span><span class="sxs-lookup"><span data-stu-id="53a09-141">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](ssbdiagnose-utility-service-broker.md)  
  
  
