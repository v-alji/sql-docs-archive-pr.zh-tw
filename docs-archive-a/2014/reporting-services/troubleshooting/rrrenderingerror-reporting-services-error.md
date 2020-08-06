---
title: rrRenderingError - Reporting Services 錯誤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rrRenderingError
ms.assetid: 0751efc3-b81b-44ee-8aac-8560f86ca322
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b44b042c5f3c0cfdb9ffb99d3f45ed073beb972a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700639"
---
# <a name="rrrenderingerror---reporting-services-error"></a><span data-ttu-id="9743a-102">rrRenderingError - Reporting Services 錯誤</span><span class="sxs-lookup"><span data-stu-id="9743a-102">rrRenderingError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="9743a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9743a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9743a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9743a-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="9743a-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9743a-105">Event ID</span></span>|<span data-ttu-id="9743a-106">rrRenderingError</span><span class="sxs-lookup"><span data-stu-id="9743a-106">rrRenderingError</span></span>|  
|<span data-ttu-id="9743a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="9743a-107">Event Source</span></span>|<span data-ttu-id="9743a-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources.Strings</span><span class="sxs-lookup"><span data-stu-id="9743a-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources.Strings</span></span>|  
|<span data-ttu-id="9743a-109">元件</span><span class="sxs-lookup"><span data-stu-id="9743a-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="9743a-110">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9743a-110">Message Text</span></span>|<span data-ttu-id="9743a-111">轉譯報表期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="9743a-111">An error occurred during rendering of the report.</span></span> <span data-ttu-id="9743a-112">(rrRenderingError) %1</span><span class="sxs-lookup"><span data-stu-id="9743a-112">(rrRenderingError) %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9743a-113">說明</span><span class="sxs-lookup"><span data-stu-id="9743a-113">Explanation</span></span>  
 <span data-ttu-id="9743a-114">當 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 無法轉譯或匯出報表時，就會傳回這個訊息。</span><span class="sxs-lookup"><span data-stu-id="9743a-114">This message is returned when [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] cannot render or export the report.</span></span>  
  
 <span data-ttu-id="9743a-115">當指定的 RDL 頁面大小無效時，通常會產生一個訊息，指出不支援該大小。</span><span class="sxs-lookup"><span data-stu-id="9743a-115">A message that indicates that the size is not supported is typically caused when the specified RDL page size is not valid.</span></span> <span data-ttu-id="9743a-116">請指定有效的 RDL 頁面大小，然後重試一遍。</span><span class="sxs-lookup"><span data-stu-id="9743a-116">Specify a valid RDL page size and then try again.</span></span>  
  
 <span data-ttu-id="9743a-117">當指定了不支援的單位類型時，通常會產生一個訊息，指出不支援 RDL 大小度量。</span><span class="sxs-lookup"><span data-stu-id="9743a-117">A message that indicates that an RDL size measurement is not supported is typically caused when an unsupported unit type is specified.</span></span> <span data-ttu-id="9743a-118">有效的單位類型為 cm、in、mm、pc 和 pt。</span><span class="sxs-lookup"><span data-stu-id="9743a-118">Valid unit types are cm, in, mm, pc, and pt.</span></span> <span data-ttu-id="9743a-119">請指定有效的單位類型，然後重試一遍。</span><span class="sxs-lookup"><span data-stu-id="9743a-119">Specify a valid unit type and then try again.</span></span>  
  
 <span data-ttu-id="9743a-120">當指定了頁面大小的負數度量 (如 -5 cm) 時，通常會產生一個訊息，指出不支援負數大小。</span><span class="sxs-lookup"><span data-stu-id="9743a-120">A message that indicates that a negative size is not supported is typically caused when a negative measurement for the page size, for example -5 cm, is specified.</span></span> <span data-ttu-id="9743a-121">請為頁面大小指定正數，然後重試一遍。</span><span class="sxs-lookup"><span data-stu-id="9743a-121">Specify a positive number for the page size and then try again.</span></span>  
  
 <span data-ttu-id="9743a-122">當頁面大小的度量超出有效頁面邊界大小時，通常會產生一個訊息，指出指定的 RDL 大小超出範圍。</span><span class="sxs-lookup"><span data-stu-id="9743a-122">A message that indicates that an RDL size is specified out of range is typically caused when a measurement for the page size is outside of the valid page margin size.</span></span> <span data-ttu-id="9743a-123">請針對頁面大小指定在有效頁面邊界大小內的度量。</span><span class="sxs-lookup"><span data-stu-id="9743a-123">Specify a measurement for the page size that is within the valid page margin sizes.</span></span>  
  
 <span data-ttu-id="9743a-124">當 RDL 中指定的色彩無效時，通常會產生一個訊息，指出指定的色彩無效。</span><span class="sxs-lookup"><span data-stu-id="9743a-124">A message that indicates that a color specified is not supported is typically caused when a color specified in the RDL is not valid.</span></span> <span data-ttu-id="9743a-125">請選擇 RDL 支援的色彩，然後重試一遍。</span><span class="sxs-lookup"><span data-stu-id="9743a-125">Choose a color supported by RDL and then try again.</span></span>  
  
 <span data-ttu-id="9743a-126">當指定的動作標籤無效時，通常會產生一個訊息，指出動作標籤在使用單一動作時只是選擇性，而且加入多個動作需要每一個動作的標籤。</span><span class="sxs-lookup"><span data-stu-id="9743a-126">A message that indicates that the action label is only optional when using a single action and that adding multiple actions requires labels for each action is typically caused when an action label is specified and it is not valid.</span></span> <span data-ttu-id="9743a-127">請針對每一個動作指定有效的動作標籤。</span><span class="sxs-lookup"><span data-stu-id="9743a-127">Specify a valid action label for each action.</span></span>  
  
 <span data-ttu-id="9743a-128">當針對資料類型指定了不正確的樣式值時，通常會產生一個訊息，指出樣式引數必須是特定的類型。</span><span class="sxs-lookup"><span data-stu-id="9743a-128">A message that indicates the style argument has to be of a specific type is typically caused when an incorrect style value for the data type is specified.</span></span> <span data-ttu-id="9743a-129">RDL 規格會識別您可以在不同 RDL 元素的樣式值中使用的有效類型。</span><span class="sxs-lookup"><span data-stu-id="9743a-129">The RDL specification identifies the valid types that you can use in the style values of different RDL elements.</span></span> <span data-ttu-id="9743a-130">例如，背景色彩的不正確樣式值為 "2pt"，而不正確的高度值為 "true"。</span><span class="sxs-lookup"><span data-stu-id="9743a-130">For example, an incorrect style value for background color is "2pt" and incorrect value for height is "true".</span></span> <span data-ttu-id="9743a-131">請指定一個正確的值，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="9743a-131">Specify a correct value and then try again.</span></span>  
  
 <span data-ttu-id="9743a-132">當指定的框線樣式無效時，通常會產生一個訊息，指出不支援此框線樣式。</span><span class="sxs-lookup"><span data-stu-id="9743a-132">A message that indicates that the border style is not supported is typically caused when the border style specified is not valid.</span></span> <span data-ttu-id="9743a-133">請指定支援的框線樣式，然後重試一遍。</span><span class="sxs-lookup"><span data-stu-id="9743a-133">Specify a supported border style and then try again.</span></span>  
  
 <span data-ttu-id="9743a-134">當影像報表項目的指定 mimetype 無效時，通常會產生一個訊息，指出不支援該影像 mimetype。</span><span class="sxs-lookup"><span data-stu-id="9743a-134">A message that indicates that the image mimetype is not supported is typically caused when the specified mimetype for an image report item is not valid.</span></span> <span data-ttu-id="9743a-135">請為此報表項目指定支援的 mimetype，然後重試一遍。</span><span class="sxs-lookup"><span data-stu-id="9743a-135">Specify a supported mimetype for the report item and then try again.</span></span>  
  
 <span data-ttu-id="9743a-136">當超出 Excel 工作表內的資料列數時，通常會產生一個訊息，指出資料列數超出每一工作表的最大可能資料列數。</span><span class="sxs-lookup"><span data-stu-id="9743a-136">A message that indicates that the number of rows exceeds the maximum possible rows per sheet is typically caused when the number of rows in an Excel worksheet is exceeded.</span></span> <span data-ttu-id="9743a-137">Excel 最多支援 65,000 個資料列。</span><span class="sxs-lookup"><span data-stu-id="9743a-137">Excel supports up to 65,000 rows.</span></span>  
  
 <span data-ttu-id="9743a-138">當超出 Excel 工作表內的資料行數時，通常會產生一個訊息，指出資料行數超出每一工作表的最大可能資料行數。</span><span class="sxs-lookup"><span data-stu-id="9743a-138">A message that indicates that the number of columns exceeds the maximum possible columns per sheet is typically caused when the number of columns in an Excel worksheet is exceeded.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9743a-139">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9743a-139">User Action</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="9743a-140">僅供內部使用</span><span class="sxs-lookup"><span data-stu-id="9743a-140">Internal-Only</span></span>  
  
