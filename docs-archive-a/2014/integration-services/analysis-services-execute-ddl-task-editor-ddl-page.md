---
title: Analysis Services (DDL 頁面) 執行 DDL 工作編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asexecuteddltask.ddl.f1
helpviewer_keywords:
- Analysis Services Execute DDL Task Editor
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d207afe666e582c44f1014a6c80f4f4984fd5410
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593524"
---
# <a name="analysis-services-execute-ddl-task-editor-ddl-page"></a><span data-ttu-id="a4d1a-102">Analysis Services 執行 DDL 工作編輯器 (DDL 頁面)</span><span class="sxs-lookup"><span data-stu-id="a4d1a-102">Analysis Services Execute DDL Task Editor (DDL Page)</span></span>
  <span data-ttu-id="a4d1a-103">使用 [Analysis Services 執行 DDL 工作編輯器]  對話方塊的 [DDL]  頁面，即可指定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫的連接，並提供資料定義語言 (DDL) 陳述式來源的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a4d1a-103">Use the **DDL** page of the **Analysis Services Execute DDL Task Editor** dialog box to specify a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project or an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database and to provide information about the source of data definition language (DDL) statements.</span></span>  
  
 <span data-ttu-id="a4d1a-104">若要了解這個工作，請參閱＜ [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a4d1a-104">To learn about this task, see [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="a4d1a-105">靜態選項</span><span class="sxs-lookup"><span data-stu-id="a4d1a-105">Static Options</span></span>  
 <span data-ttu-id="a4d1a-106">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="a4d1a-106">**Connection**</span></span>  
 <span data-ttu-id="a4d1a-107">選取清單中的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 連線管理員，或按一下 \<**New connection...**> 並使用 [新增 Analysis Services 連線管理員] 對話方塊，即可建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="a4d1a-107">Select an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project or an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] connection manager in the list, or click \<**New connection...**> and use the **Add Analysis Services Connection Manager** dialog box to create a new connection.</span></span>  
  
 <span data-ttu-id="a4d1a-108">**相關主題：** [加入 Analysis Services 連線管理員對話方塊 UI 參考](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)、[Analysis Services 連線管理員](connection-manager/analysis-services-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="a4d1a-108">**Related Topics:** [Add Analysis Services Connection Manager Dialog Box UI Reference](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md), [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md)</span></span>  
  
 <span data-ttu-id="a4d1a-109">**SourceType**</span><span class="sxs-lookup"><span data-stu-id="a4d1a-109">**SourceType**</span></span>  
 <span data-ttu-id="a4d1a-110">指定 DDL 陳述式的來源類型。</span><span class="sxs-lookup"><span data-stu-id="a4d1a-110">Specify the source type of the DDL statements.</span></span> <span data-ttu-id="a4d1a-111">此屬性具有下表所列的選項：</span><span class="sxs-lookup"><span data-stu-id="a4d1a-111">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="a4d1a-112">值</span><span class="sxs-lookup"><span data-stu-id="a4d1a-112">Value</span></span>|<span data-ttu-id="a4d1a-113">描述</span><span class="sxs-lookup"><span data-stu-id="a4d1a-113">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4d1a-114">**直接輸入**</span><span class="sxs-lookup"><span data-stu-id="a4d1a-114">**Direct Input**</span></span>|<span data-ttu-id="a4d1a-115">將來源設定為 [SourceDirect]  文字方塊中所儲存的 DDL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a4d1a-115">Set the source to the DDL statement stored in the **SourceDirect** text box.</span></span> <span data-ttu-id="a4d1a-116">選取這個值就會顯示在下列章節中的動態選項。</span><span class="sxs-lookup"><span data-stu-id="a4d1a-116">Selecting this value displays the dynamic options in the following section.</span></span>|  
|<span data-ttu-id="a4d1a-117">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="a4d1a-117">**File Connection**</span></span>|<span data-ttu-id="a4d1a-118">將來源設定為包含 DDL 陳述式的檔案。</span><span class="sxs-lookup"><span data-stu-id="a4d1a-118">Set the source to a file that contains the DDL statement.</span></span> <span data-ttu-id="a4d1a-119">選取這個值就會顯示在下列章節中的動態選項。</span><span class="sxs-lookup"><span data-stu-id="a4d1a-119">Selecting this value displays the dynamic options in the following section.</span></span>|  
|<span data-ttu-id="a4d1a-120">**變數**</span><span class="sxs-lookup"><span data-stu-id="a4d1a-120">**Variable**</span></span>|<span data-ttu-id="a4d1a-121">將來源設定為變數。</span><span class="sxs-lookup"><span data-stu-id="a4d1a-121">Set the source to a variable.</span></span> <span data-ttu-id="a4d1a-122">選取這個值就會顯示在下列章節中的動態選項。</span><span class="sxs-lookup"><span data-stu-id="a4d1a-122">Selecting this value displays the dynamic options in the following section.</span></span>|  
  
## <a name="dynamic-options"></a><span data-ttu-id="a4d1a-123">動態選項</span><span class="sxs-lookup"><span data-stu-id="a4d1a-123">Dynamic Options</span></span>  
  
### <a name="sourcetype--direct-input"></a><span data-ttu-id="a4d1a-124">SourceType = 直接輸入</span><span class="sxs-lookup"><span data-stu-id="a4d1a-124">SourceType = Direct Input</span></span>  
 <span data-ttu-id="a4d1a-125">**Source**</span><span class="sxs-lookup"><span data-stu-id="a4d1a-125">**Source**</span></span>  
 <span data-ttu-id="a4d1a-126">鍵入 DDL 陳述式或按一下省略符號 **(...)** ，然後在 [DDL 陳述式]  對話方塊中鍵入陳述式。</span><span class="sxs-lookup"><span data-stu-id="a4d1a-126">Type the DDL statements or click the ellipsis **(...)** and then type the statements in the **DDL Statements** dialog box.</span></span>  
  
### <a name="sourcetype--file-connection"></a><span data-ttu-id="a4d1a-127">SourceType = 檔案連接</span><span class="sxs-lookup"><span data-stu-id="a4d1a-127">SourceType = File Connection</span></span>  
 <span data-ttu-id="a4d1a-128">**Source**</span><span class="sxs-lookup"><span data-stu-id="a4d1a-128">**Source**</span></span>  
 <span data-ttu-id="a4d1a-129">選取清單中的 [檔案連線]，或按一下 \<**New connection...**> 並使用 [檔案連線管理員] 對話方塊，即可建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="a4d1a-129">Select a File connection in the list, or click \<**New connection...**> and use the **File Connection Manager** dialog box to create a new connection.</span></span>  
  
 <span data-ttu-id="a4d1a-130">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="a4d1a-130">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md)</span></span>  
  
### <a name="sourcetype--variable"></a><span data-ttu-id="a4d1a-131">SourceType = 變數</span><span class="sxs-lookup"><span data-stu-id="a4d1a-131">SourceType = Variable</span></span>  
 <span data-ttu-id="a4d1a-132">**Source**</span><span class="sxs-lookup"><span data-stu-id="a4d1a-132">**Source**</span></span>  
 <span data-ttu-id="a4d1a-133">在清單中選取變數，或按一下 \<**New variable...**> 並使用 [新增變數] 對話方塊，即可建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="a4d1a-133">Select a variable in the list, or click \<**New variable...**> and use the **Add Variable** dialog box to create a new variable.</span></span>  
  
 <span data-ttu-id="a4d1a-134">**相關主題：** [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)</span><span class="sxs-lookup"><span data-stu-id="a4d1a-134">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4d1a-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4d1a-135">See Also</span></span>  
 <span data-ttu-id="a4d1a-136">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a4d1a-136">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="a4d1a-137">[Analysis Services 執行 DDL 工作編輯器 &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="a4d1a-137">[Analysis Services Execute DDL Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="a4d1a-138">[運算式頁面](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="a4d1a-138">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="a4d1a-139">[控制流程](control-flow/control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="a4d1a-139">[Control Flow](control-flow/control-flow.md) </span></span>  
 <span data-ttu-id="a4d1a-140">[Analysis Services 指令碼語言 &#40;ASSL&#41; 參考](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) </span><span class="sxs-lookup"><span data-stu-id="a4d1a-140">[Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) </span></span>  
 [<span data-ttu-id="a4d1a-141">XML for Analysis &#40;XMLA&#41; 參考</span><span class="sxs-lookup"><span data-stu-id="a4d1a-141">XML for Analysis  &#40;XMLA&#41; Reference</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)  
  
  
