---
title: 查閱轉換編輯器 (錯誤輸出頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.erroroutput.f1
ms.assetid: 15d53bb0-8be1-46fb-b459-04a397e75fac
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9cd78f40a0072f7f0c5c923cdd51431873402f3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596102"
---
# <a name="lookup-transformation-editor-error-output-page"></a><span data-ttu-id="9112b-102">查閱轉換編輯器 (錯誤輸出頁面)</span><span class="sxs-lookup"><span data-stu-id="9112b-102">Lookup Transformation Editor (Error Output Page)</span></span>
  <span data-ttu-id="9112b-103">使用 **[查閱轉換編輯器]** 對話方塊的 **[錯誤輸出]** 頁面，來指定錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="9112b-103">Use the **Error Output** page of the **Lookup Transformation Editor** dialog box to specify error handling options.</span></span>  
  
 <span data-ttu-id="9112b-104">若要深入了解查閱轉換，請參閱＜ [Lookup Transformation](data-flow/transformations/lookup-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9112b-104">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9112b-105">選項。</span><span class="sxs-lookup"><span data-stu-id="9112b-105">Options</span></span>  
 <span data-ttu-id="9112b-106">**輸入/輸出**</span><span class="sxs-lookup"><span data-stu-id="9112b-106">**Input/Output**</span></span>  
 <span data-ttu-id="9112b-107">檢視輸入的名稱。</span><span class="sxs-lookup"><span data-stu-id="9112b-107">View the name of the input.</span></span>  
  
 <span data-ttu-id="9112b-108">**資料行**</span><span class="sxs-lookup"><span data-stu-id="9112b-108">**Column**</span></span>  
 <span data-ttu-id="9112b-109">未使用。</span><span class="sxs-lookup"><span data-stu-id="9112b-109">Not used.</span></span>  
  
 <span data-ttu-id="9112b-110">**錯誤**</span><span class="sxs-lookup"><span data-stu-id="9112b-110">**Error**</span></span>  
 <span data-ttu-id="9112b-111">指定處理在參考資料集中沒有相符項目的資料列時會發生什麼類型的錯誤：</span><span class="sxs-lookup"><span data-stu-id="9112b-111">Specify what type of error should occur when handling rows without matching entries in the reference dataset:</span></span>  
  
-   <span data-ttu-id="9112b-112">忽略失敗並將資料列導向輸出。</span><span class="sxs-lookup"><span data-stu-id="9112b-112">Ignore the failure and direct the rows to an output.</span></span>  
  
-   <span data-ttu-id="9112b-113">將資料列重新導向錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="9112b-113">Redirect the rows to an error output.</span></span>  
  
-   <span data-ttu-id="9112b-114">使元件失效。</span><span class="sxs-lookup"><span data-stu-id="9112b-114">Fail the component.</span></span>  
  
 <span data-ttu-id="9112b-115">在 **[指定如何處理無相符項目的資料列]** 清單中選取 **[將資料列重新導向無相符結果輸出]** 時，無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="9112b-115">This option is not available when you select **Redirect rows to no match output** in the **Specify how to handle rows with no matching entries** list.</span></span> <span data-ttu-id="9112b-116">此清單位在 **[查閱轉換編輯器]** 對話方塊的 **[一般]** 頁面上。</span><span class="sxs-lookup"><span data-stu-id="9112b-116">This list is on the **General** page of the **Lookup Transformation Editor** dialog box.</span></span>  
  
 <span data-ttu-id="9112b-117">**相關主題：** [資料中的錯誤處理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="9112b-117">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="9112b-118">**截斷**</span><span class="sxs-lookup"><span data-stu-id="9112b-118">**Truncation**</span></span>  
 <span data-ttu-id="9112b-119">指定資料截斷發生時要採取的動作：</span><span class="sxs-lookup"><span data-stu-id="9112b-119">Specify what should happen when data truncation occurs:</span></span>  
  
-   <span data-ttu-id="9112b-120">忽略失敗。</span><span class="sxs-lookup"><span data-stu-id="9112b-120">Ignore the failure.</span></span>  
  
-   <span data-ttu-id="9112b-121">重新導向資料列。</span><span class="sxs-lookup"><span data-stu-id="9112b-121">Redirect the row.</span></span>  
  
-   <span data-ttu-id="9112b-122">使元件失效。</span><span class="sxs-lookup"><span data-stu-id="9112b-122">Fail the component.</span></span>  
  
 <span data-ttu-id="9112b-123">**說明**</span><span class="sxs-lookup"><span data-stu-id="9112b-123">**Description**</span></span>  
 <span data-ttu-id="9112b-124">檢視作業的描述。</span><span class="sxs-lookup"><span data-stu-id="9112b-124">View the description of the operation.</span></span>  
  
 <span data-ttu-id="9112b-125">**將選取的資料格設定為此值**</span><span class="sxs-lookup"><span data-stu-id="9112b-125">**Set selected cells to this value**</span></span>  
 <span data-ttu-id="9112b-126">指定在錯誤或截斷發生時對所有選取的資料格進行什麼作業。</span><span class="sxs-lookup"><span data-stu-id="9112b-126">Specify what should happen to all the selected cells when an error or truncation occurs:</span></span>  
  
-   <span data-ttu-id="9112b-127">忽略失敗。</span><span class="sxs-lookup"><span data-stu-id="9112b-127">Ignore the failure.</span></span>  
  
-   <span data-ttu-id="9112b-128">重新導向資料列。</span><span class="sxs-lookup"><span data-stu-id="9112b-128">Redirect the row.</span></span>  
  
-   <span data-ttu-id="9112b-129">使元件失效。</span><span class="sxs-lookup"><span data-stu-id="9112b-129">Fail the component.</span></span>  
  
 <span data-ttu-id="9112b-130">**套用**</span><span class="sxs-lookup"><span data-stu-id="9112b-130">**Apply**</span></span>  
 <span data-ttu-id="9112b-131">將錯誤處理選項套用至選取的資料格。</span><span class="sxs-lookup"><span data-stu-id="9112b-131">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9112b-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9112b-132">See Also</span></span>  
 [<span data-ttu-id="9112b-133">Integration Services 錯誤和訊息參考</span><span class="sxs-lookup"><span data-stu-id="9112b-133">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
