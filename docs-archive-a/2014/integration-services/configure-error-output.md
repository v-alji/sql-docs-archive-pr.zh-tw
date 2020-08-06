---
title: 設定錯誤輸出 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.configureerroroutput.f1
ms.assetid: 5f8da390-fab5-44f8-b268-d8fa313ce4b9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: de1a5908c6075438599f4108e9780f5591b042c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597279"
---
# <a name="configure-error-output"></a><span data-ttu-id="7986e-102">設定錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="7986e-102">Configure Error Output</span></span>
  <span data-ttu-id="7986e-103">使用 [設定錯誤輸出] 對話方塊，即可為支援錯誤輸出的資料流程轉換設定錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="7986e-103">Use the **Configure Error Output** dialog box to configure error handling options for data flow transformations that support an error output.</span></span>  
  
 <span data-ttu-id="7986e-104">若要深入了解如何使用錯誤輸出，請參閱[處理資料中的錯誤](data-flow/error-handling-in-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7986e-104">To learn more about working with error outputs, see [Error Handling in Data](data-flow/error-handling-in-data.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7986e-105">選項。</span><span class="sxs-lookup"><span data-stu-id="7986e-105">Options</span></span>  
 <span data-ttu-id="7986e-106">**輸入或輸出**</span><span class="sxs-lookup"><span data-stu-id="7986e-106">**Input or Output**</span></span>  
 <span data-ttu-id="7986e-107">檢視輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="7986e-107">View the name of the output.</span></span>  
  
 <span data-ttu-id="7986e-108">**資料行**</span><span class="sxs-lookup"><span data-stu-id="7986e-108">**Column**</span></span>  
 <span data-ttu-id="7986e-109">檢視您在 [轉換編輯器] 對話方塊中選取的輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="7986e-109">View the output columns that you selected in the transformation editor dialog box.</span></span>  
  
 <span data-ttu-id="7986e-110">**錯誤**</span><span class="sxs-lookup"><span data-stu-id="7986e-110">**Error**</span></span>  
 <span data-ttu-id="7986e-111">如果適用的話，請指定錯誤發生時要採取的動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="7986e-111">If applicable, specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="7986e-112">**相關主題：** [資料中的錯誤處理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="7986e-112">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="7986e-113">**截斷**</span><span class="sxs-lookup"><span data-stu-id="7986e-113">**Truncation**</span></span>  
 <span data-ttu-id="7986e-114">如果適用的話，請指定截斷發生時要採取的動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="7986e-114">If applicable, specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="7986e-115">**相關主題：** [資料中的錯誤處理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="7986e-115">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="7986e-116">**說明**</span><span class="sxs-lookup"><span data-stu-id="7986e-116">**Description**</span></span>  
 <span data-ttu-id="7986e-117">檢視作業的描述。</span><span class="sxs-lookup"><span data-stu-id="7986e-117">View the description of the operation.</span></span>  
  
 <span data-ttu-id="7986e-118">**將這個值設定到選取的資料格**</span><span class="sxs-lookup"><span data-stu-id="7986e-118">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="7986e-119">指定發生錯誤或截斷時要對所有選取之資料格採取的動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="7986e-119">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="7986e-120">**套用**</span><span class="sxs-lookup"><span data-stu-id="7986e-120">**Apply**</span></span>  
 <span data-ttu-id="7986e-121">將錯誤處理選項套用至選取的資料格。</span><span class="sxs-lookup"><span data-stu-id="7986e-121">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7986e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7986e-122">See Also</span></span>  
 [<span data-ttu-id="7986e-123">Integration Services 錯誤和訊息參考</span><span class="sxs-lookup"><span data-stu-id="7986e-123">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
