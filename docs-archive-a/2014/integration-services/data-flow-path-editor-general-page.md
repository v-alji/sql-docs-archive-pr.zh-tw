---
title: 資料流程路徑編輯器 (一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.patheditor.general.f1
helpviewer_keywords:
- Data Flow Path Editor dialog box
ms.assetid: 72a9ff1d-3748-41d1-a9b2-63f4a77bba24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 71eca61b1454e2e8cb811bbe450f584191ae77b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688109"
---
# <a name="data-flow-path-editor-general-page"></a><span data-ttu-id="9beb0-102">資料流程路徑編輯器 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="9beb0-102">Data Flow Path Editor (General Page)</span></span>
  <span data-ttu-id="9beb0-103">使用 **[資料流程路徑編輯器]** 對話方塊，即可設定路徑屬性、檢視資料行中繼資料，以及管理附加至路徑的資料檢視器。</span><span class="sxs-lookup"><span data-stu-id="9beb0-103">Use the **Data Flow Path Editor** dialog box to set path properties, view column metadata, and manage the data viewers attached to the path.</span></span>  
  
 <span data-ttu-id="9beb0-104">使用 **[資料流程路徑編輯器]** 對話方塊的 **[一般]** 節點，即可命名和描述路徑，以及指定路徑註解的選項。</span><span class="sxs-lookup"><span data-stu-id="9beb0-104">Use the **General** node of the **Data Flow Path Editor** dialog box to name and describe the path, and to specify the options for path annotation.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9beb0-105">選項。</span><span class="sxs-lookup"><span data-stu-id="9beb0-105">Options</span></span>  
 <span data-ttu-id="9beb0-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="9beb0-106">**Name**</span></span>  
 <span data-ttu-id="9beb0-107">提供路徑的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="9beb0-107">Provide a unique name for the path.</span></span>  
  
 <span data-ttu-id="9beb0-108">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="9beb0-108">**ID**</span></span>  
 <span data-ttu-id="9beb0-109">路徑的歷程識別碼。</span><span class="sxs-lookup"><span data-stu-id="9beb0-109">The lineage identifier of the path.</span></span> <span data-ttu-id="9beb0-110">這個屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="9beb0-110">This property is read-only.</span></span>  
  
 <span data-ttu-id="9beb0-111">**IdentificationString**</span><span class="sxs-lookup"><span data-stu-id="9beb0-111">**IdentificationString**</span></span>  
 <span data-ttu-id="9beb0-112">識別路徑的字串。</span><span class="sxs-lookup"><span data-stu-id="9beb0-112">The string that identifies the path.</span></span> <span data-ttu-id="9beb0-113">根據前面輸入的名稱自動產生。</span><span class="sxs-lookup"><span data-stu-id="9beb0-113">Automatically generated from the name entered above.</span></span>  
  
 <span data-ttu-id="9beb0-114">**說明**</span><span class="sxs-lookup"><span data-stu-id="9beb0-114">**Description**</span></span>  
 <span data-ttu-id="9beb0-115">描述路徑。</span><span class="sxs-lookup"><span data-stu-id="9beb0-115">Describe the path.</span></span>  
  
 <span data-ttu-id="9beb0-116">**PathAnnotation**</span><span class="sxs-lookup"><span data-stu-id="9beb0-116">**PathAnnotation**</span></span>  
 <span data-ttu-id="9beb0-117">指定要使用之註解的類型。</span><span class="sxs-lookup"><span data-stu-id="9beb0-117">Specify the type of annotation to use.</span></span> <span data-ttu-id="9beb0-118">選擇 **[Never]** 以停用註解，選擇 **[AsNeeded]** 以視需要啟用註解，選擇 **[SourceName]** 以使用 **[SourceName]** 選項的值來自動註解，以及選擇 **[PathName]** 以使用 **[Name]** 屬性的值來自動註解。</span><span class="sxs-lookup"><span data-stu-id="9beb0-118">Choose **Never** to disable annotations, **AsNeeded** to enable annotation on demand, **SourceName** to automatically annotate using the value of the **SourceName** option, and **PathName** to automatically annotate using the value of the **Name** property.</span></span>  
  
 <span data-ttu-id="9beb0-119">**DestinationName**</span><span class="sxs-lookup"><span data-stu-id="9beb0-119">**DestinationName**</span></span>  
 <span data-ttu-id="9beb0-120">顯示路徑末端的輸入。</span><span class="sxs-lookup"><span data-stu-id="9beb0-120">Displays the input that is the end of the path.</span></span>  
  
 <span data-ttu-id="9beb0-121">**SourceName**</span><span class="sxs-lookup"><span data-stu-id="9beb0-121">**SourceName**</span></span>  
 <span data-ttu-id="9beb0-122">顯示路徑開頭的輸出。</span><span class="sxs-lookup"><span data-stu-id="9beb0-122">Displays the output that is the start of the path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9beb0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9beb0-123">See Also</span></span>  
 <span data-ttu-id="9beb0-124">[資料流程路徑編輯器 &#40;中繼資料頁面&#41;](../../2014/integration-services/data-flow-path-editor-metadata-page.md) </span><span class="sxs-lookup"><span data-stu-id="9beb0-124">[Data Flow Path Editor &#40;Metadata Page&#41;](../../2014/integration-services/data-flow-path-editor-metadata-page.md) </span></span>  
 <span data-ttu-id="9beb0-125">[資料檢視器頁面 &#40;的資料流程路徑編輯器&#41;](../../2014/integration-services/data-flow-path-editor-data-viewers-page.md) </span><span class="sxs-lookup"><span data-stu-id="9beb0-125">[Data Flow Path Editor &#40;Data Viewers Page&#41;](../../2014/integration-services/data-flow-path-editor-data-viewers-page.md) </span></span>  
 <span data-ttu-id="9beb0-126">[資料流程](data-flow/data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="9beb0-126">[Data Flow](data-flow/data-flow.md) </span></span>  
 [<span data-ttu-id="9beb0-127">使用封裝中的註解</span><span class="sxs-lookup"><span data-stu-id="9beb0-127">Use Annotations in Packages</span></span>](use-annotations-in-packages.md)  
  
  
