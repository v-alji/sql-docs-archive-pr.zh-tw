---
title: 匯出資料行轉換編輯器 (錯誤輸出頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileextractortransformation.errorhandling.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: 260be463-01a9-460c-9c98-e5265cb2b1e9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 04a9c277bb4aaa28933d443bd12e6c2b39ed844e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710750"
---
# <a name="export-column-transformation-editor-error-output-page"></a><span data-ttu-id="62557-102">匯出資料行轉換編輯器 (錯誤輸出頁面)</span><span class="sxs-lookup"><span data-stu-id="62557-102">Export Column Transformation Editor (Error Output Page)</span></span>
  <span data-ttu-id="62557-103">使用 **[匯出資料行轉換編輯器]** 對話方塊的 **[錯誤輸出]** 頁面，即可指定如何處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="62557-103">Use the **Error Output** page of the **Export Column Transformation Editor** dialog box to specify how to handle errors.</span></span>  
  
 <span data-ttu-id="62557-104">若要深入了解匯出資料行轉換，請參閱＜ [Export Column Transformation](data-flow/transformations/export-column-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="62557-104">To learn more about the Export Column transformation, see [Export Column Transformation](data-flow/transformations/export-column-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="62557-105">選項。</span><span class="sxs-lookup"><span data-stu-id="62557-105">Options</span></span>  
 <span data-ttu-id="62557-106">**輸入/輸出**</span><span class="sxs-lookup"><span data-stu-id="62557-106">**Input/Output**</span></span>  
 <span data-ttu-id="62557-107">檢視輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="62557-107">View the name of the output.</span></span> <span data-ttu-id="62557-108">按一下名稱即可展開檢視來包含資料行。</span><span class="sxs-lookup"><span data-stu-id="62557-108">Click the name to expand the view to include columns.</span></span>  
  
 <span data-ttu-id="62557-109">**資料行**</span><span class="sxs-lookup"><span data-stu-id="62557-109">**Column**</span></span>  
 <span data-ttu-id="62557-110">檢視您在 [匯出資料行轉換編輯器]\*\*\*\* 對話方塊的 [資料行]\*\*\*\* 頁面上選取的輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="62557-110">View the output columns that you selected on the **Columns** page of the **Export Column Transformation Editor** dialog box.</span></span>  
  
 <span data-ttu-id="62557-111">**錯誤**</span><span class="sxs-lookup"><span data-stu-id="62557-111">**Error**</span></span>  
 <span data-ttu-id="62557-112">指定您要在錯誤發生時採取什麼動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="62557-112">Specify what you want to happen if an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="62557-113">**截斷**</span><span class="sxs-lookup"><span data-stu-id="62557-113">**Truncation**</span></span>  
 <span data-ttu-id="62557-114">指定您要在截斷發生時採取什麼動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="62557-114">Specify what you want to happen if a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="62557-115">**說明**</span><span class="sxs-lookup"><span data-stu-id="62557-115">**Description**</span></span>  
 <span data-ttu-id="62557-116">檢視作業的描述。</span><span class="sxs-lookup"><span data-stu-id="62557-116">View the description of the operation.</span></span>  
  
 <span data-ttu-id="62557-117">**將這個值設定到選取的資料格**</span><span class="sxs-lookup"><span data-stu-id="62557-117">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="62557-118">指定發生錯誤或截斷時要對所有選取之資料格採取的動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="62557-118">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="62557-119">**套用**</span><span class="sxs-lookup"><span data-stu-id="62557-119">**Apply**</span></span>  
 <span data-ttu-id="62557-120">將錯誤處理選項套用至選取的資料格。</span><span class="sxs-lookup"><span data-stu-id="62557-120">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62557-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62557-121">See Also</span></span>  
 <span data-ttu-id="62557-122">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="62557-122">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="62557-123">匯出資料行轉換編輯器 &#40;資料行頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="62557-123">Export Column Transformation Editor &#40;Columns Page&#41;</span></span>](../../2014/integration-services/export-column-transformation-editor-columns-page.md)  
  
  
