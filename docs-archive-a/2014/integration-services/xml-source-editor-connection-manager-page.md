---
title: XML 來源編輯器 (連線管理員頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmlsourceadapter.connectionmanager.f1
helpviewer_keywords:
- XML Source Editor
ms.assetid: e6507403-a3ce-4b6f-91fc-a7de9f7b6283
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0e40ca6ef2d8fbcd10b756a2ce15f33730c367d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606408"
---
# <a name="xml-source-editor-connection-manager-page"></a><span data-ttu-id="596ad-102">XML 來源編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="596ad-102">XML Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="596ad-103">使用 **[XML 來源編輯器]** 的 **[連接管理員]** 頁面，來指定 XML 檔案和轉換 XML 資料的 XSD。</span><span class="sxs-lookup"><span data-stu-id="596ad-103">Use the **Connection Manager** page of the **XML Source Editor** to specify an XML file and the XSD that transforms the XML data.</span></span>  
  
 <span data-ttu-id="596ad-104">如需有關 XML 來源的詳細資訊，請參閱＜ [XML Source](data-flow/xml-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="596ad-104">For more information about the XML source, see [XML Source](data-flow/xml-source.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="596ad-105">靜態選項</span><span class="sxs-lookup"><span data-stu-id="596ad-105">Static Options</span></span>  
 <span data-ttu-id="596ad-106">**資料存取模式**</span><span class="sxs-lookup"><span data-stu-id="596ad-106">**Data access mode**</span></span>  
 <span data-ttu-id="596ad-107">從來源中指定選取資料的方法。</span><span class="sxs-lookup"><span data-stu-id="596ad-107">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="596ad-108">值</span><span class="sxs-lookup"><span data-stu-id="596ad-108">Value</span></span>|<span data-ttu-id="596ad-109">描述</span><span class="sxs-lookup"><span data-stu-id="596ad-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="596ad-110">XML 檔案位置</span><span class="sxs-lookup"><span data-stu-id="596ad-110">XML file location</span></span>|<span data-ttu-id="596ad-111">從 XML 檔案擷取資料。</span><span class="sxs-lookup"><span data-stu-id="596ad-111">Retrieve data from an XML file.</span></span>|  
|<span data-ttu-id="596ad-112">來自變數的 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="596ad-112">XML file from variable</span></span>|<span data-ttu-id="596ad-113">指定變數中的 XML 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="596ad-113">Specify the XML file name in a variable.</span></span><br /><br /> <span data-ttu-id="596ad-114">**相關資訊**：[在套件中使用變數](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="596ad-114">**Related information**: [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="596ad-115">來自變數的 XML 資料</span><span class="sxs-lookup"><span data-stu-id="596ad-115">XML data from variable</span></span>|<span data-ttu-id="596ad-116">從變數中擷取 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="596ad-116">Retrieve XML data from a variable.</span></span>|  
  
 <span data-ttu-id="596ad-117">**使用內嵌結構描述**</span><span class="sxs-lookup"><span data-stu-id="596ad-117">**Use inline schema**</span></span>  
 <span data-ttu-id="596ad-118">指定 XML 來源資料本身是否包含定義及驗證其結構和資料的 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="596ad-118">Specify whether the XML source data itself contains the XSD schema that defines and validates its structure and data.</span></span>  
  
 <span data-ttu-id="596ad-119">**XSD 位置**</span><span class="sxs-lookup"><span data-stu-id="596ad-119">**XSD location**</span></span>  
 <span data-ttu-id="596ad-120">輸入 XSD 結構描述檔案的路徑和檔案名稱，或按一下 [瀏覽]\*\*\*\* 來找出檔案。</span><span class="sxs-lookup"><span data-stu-id="596ad-120">Type the path and file name of the XSD schema file, or locate the file by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="596ad-121">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="596ad-121">**Browse**</span></span>  
 <span data-ttu-id="596ad-122">使用 [開啟]\*\*\*\* 對話方塊來找出 XSD 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="596ad-122">Use the **Open** dialog box to locate the XSD schema file.</span></span>  
  
 <span data-ttu-id="596ad-123">**產生 XSD**</span><span class="sxs-lookup"><span data-stu-id="596ad-123">**Generate XSD**</span></span>  
 <span data-ttu-id="596ad-124">使用 [另存新檔]\*\*\*\* 對話方塊，來選取自動產生之 XSD 結構描述檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="596ad-124">Use the **Save As** dialog box to select a location for the auto-generated XSD schema file.</span></span> <span data-ttu-id="596ad-125">編輯器會從 XML 資料的結構中推斷結構描述。</span><span class="sxs-lookup"><span data-stu-id="596ad-125">The editor infers the schema from the structure of the XML data.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="596ad-126">資料存取模式動態選項</span><span class="sxs-lookup"><span data-stu-id="596ad-126">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--xml-file-location"></a><span data-ttu-id="596ad-127">資料存取模式 = XML 檔案位置</span><span class="sxs-lookup"><span data-stu-id="596ad-127">Data access mode = XML file location</span></span>  
 <span data-ttu-id="596ad-128">**XML 位置**</span><span class="sxs-lookup"><span data-stu-id="596ad-128">**XML location**</span></span>  
 <span data-ttu-id="596ad-129">輸入 XML 資料檔的路徑和檔案名稱，或按一下 [瀏覽]\*\*\*\* 來找出檔案。</span><span class="sxs-lookup"><span data-stu-id="596ad-129">Type the path and file name of the XML data file, or locate the file by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="596ad-130">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="596ad-130">**Browse**</span></span>  
 <span data-ttu-id="596ad-131">使用 [開啟]\*\*\*\* 對話方塊來找出 XML 資料檔。</span><span class="sxs-lookup"><span data-stu-id="596ad-131">Use the **Open** dialog box to locate the XML data file.</span></span>  
  
### <a name="data-access-mode--xml-file-from-variable"></a><span data-ttu-id="596ad-132">資料存取模式 = 來自變數的 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="596ad-132">Data access mode = XML file from variable</span></span>  
 <span data-ttu-id="596ad-133">**變數名稱**</span><span class="sxs-lookup"><span data-stu-id="596ad-133">**Variable name**</span></span>  
 <span data-ttu-id="596ad-134">選取包含 XML 檔案之路徑和檔案名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="596ad-134">Select the variable that contains the path and file name of the XML file.</span></span>  
  
### <a name="data-access-mode--xml-data-from-variable"></a><span data-ttu-id="596ad-135">資料存取模式 = 來自變數的 XML 資料</span><span class="sxs-lookup"><span data-stu-id="596ad-135">Data access mode = XML data from variable</span></span>  
 <span data-ttu-id="596ad-136">**變數名稱**</span><span class="sxs-lookup"><span data-stu-id="596ad-136">**Variable name**</span></span>  
 <span data-ttu-id="596ad-137">選取包含 XML 資料的變數。</span><span class="sxs-lookup"><span data-stu-id="596ad-137">Select the variable that contains the XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="596ad-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="596ad-138">See Also</span></span>  
 <span data-ttu-id="596ad-139">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="596ad-139">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="596ad-140">[XML 來源編輯器 &#40;資料行] 頁面&#41;](../../2014/integration-services/xml-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="596ad-140">[XML Source Editor &#40;Columns Page&#41;](../../2014/integration-services/xml-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="596ad-141">[XML 來源編輯器 &#40;錯誤輸出頁面&#41;](../../2014/integration-services/xml-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="596ad-141">[XML Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/xml-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="596ad-142">使用 XML 來源來擷取資料</span><span class="sxs-lookup"><span data-stu-id="596ad-142">Extract Data by Using the XML Source</span></span>](data-flow/extract-data-by-using-the-xml-source.md)  
  
  
