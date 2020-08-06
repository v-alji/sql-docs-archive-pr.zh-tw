---
title: Unpivot 轉換編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unpivottransformation.f1
helpviewer_keywords:
- Unpivot Transformation Editor
ms.assetid: 72a36ef0-4070-4f6c-9c74-0720109617dd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6c3b93370b34440b73b4c9c78dc7d19fa4095275
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592742"
---
# <a name="unpivot-transformation-editor"></a><span data-ttu-id="0f597-102">取消樞紐轉換編輯器</span><span class="sxs-lookup"><span data-stu-id="0f597-102">Unpivot Transformation Editor</span></span>
  <span data-ttu-id="0f597-103">使用 **[取消樞紐轉換編輯器]** 對話方塊，即可選取要樞紐轉換為資料列的資料行，以及指定資料行和新的樞紐值輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="0f597-103">Use the **Unpivot Transformation Editor** dialog box to select the columns to pivot into rows, and to specify the data column and the new pivot value output column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f597-104">此主題依賴於 [取消樞紐轉換](data-flow/transformations/unpivot-transformation.md) 中所描述的取消樞紐狀況，來說明選項的使用。</span><span class="sxs-lookup"><span data-stu-id="0f597-104">This topic relies on the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md) to illustrate the use of the options.</span></span>  
  
 <span data-ttu-id="0f597-105">若要深入了解取消樞紐轉換，請參閱＜ [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="0f597-105">To learn more about the Unpivot transformation, see [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0f597-106">選項。</span><span class="sxs-lookup"><span data-stu-id="0f597-106">Options</span></span>  
 <span data-ttu-id="0f597-107">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="0f597-107">**Available Input Columns**</span></span>  
 <span data-ttu-id="0f597-108">使用此核取方塊，指定要樞紐轉換為資料列的資料行。</span><span class="sxs-lookup"><span data-stu-id="0f597-108">Using the check boxes, specify the columns to pivot into rows.</span></span>  
  
 <span data-ttu-id="0f597-109">**名稱**</span><span class="sxs-lookup"><span data-stu-id="0f597-109">**Name**</span></span>  
 <span data-ttu-id="0f597-110">檢視可用輸入資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="0f597-110">View the name of the available input column.</span></span>  
  
 <span data-ttu-id="0f597-111">**通過**</span><span class="sxs-lookup"><span data-stu-id="0f597-111">**Pass Through**</span></span>  
 <span data-ttu-id="0f597-112">指出是否將資料行包含在取消樞紐的輸出中。</span><span class="sxs-lookup"><span data-stu-id="0f597-112">Indicate whether to include the column in the unpivoted output.</span></span>  
  
 <span data-ttu-id="0f597-113">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="0f597-113">**Input Column**</span></span>  
 <span data-ttu-id="0f597-114">從每個資料列的可用輸入資料行清單中選取。</span><span class="sxs-lookup"><span data-stu-id="0f597-114">Select from the list of available input columns for each row.</span></span> <span data-ttu-id="0f597-115">您的選擇會反映在 **[可用的輸入資料行]** 資料表的核取方塊選擇中。</span><span class="sxs-lookup"><span data-stu-id="0f597-115">Your selections are reflected in the check box selections in the **Available Input Columns** table.</span></span>  
  
 <span data-ttu-id="0f597-116">在＜ [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)＞所描述的取消樞紐狀況中，輸入資料行是 **Ham**, **Soda**, **Milk**, **Beer**和 **Chips** 資料行。</span><span class="sxs-lookup"><span data-stu-id="0f597-116">In the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), the Input Columns are the **Ham**, **Soda**, **Milk**, **Beer**, and **Chips** columns.</span></span>  
  
 <span data-ttu-id="0f597-117">**目的地資料行**</span><span class="sxs-lookup"><span data-stu-id="0f597-117">**Destination Column**</span></span>  
 <span data-ttu-id="0f597-118">提供資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="0f597-118">Provide a name for the data column.</span></span>  
  
 <span data-ttu-id="0f597-119">在 [取消樞紐轉換](data-flow/transformations/unpivot-transformation.md)所描述的取消樞紐狀況中，目的地資料行就是數量 (**Qty**) 資料行。</span><span class="sxs-lookup"><span data-stu-id="0f597-119">In the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), the Destination Column is the quantity (**Qty**) column.</span></span>  
  
 <span data-ttu-id="0f597-120">**樞紐索引鍵值**</span><span class="sxs-lookup"><span data-stu-id="0f597-120">**Pivot Key Value**</span></span>  
 <span data-ttu-id="0f597-121">提供樞紐值的名稱。</span><span class="sxs-lookup"><span data-stu-id="0f597-121">Provide a name for the pivot value.</span></span> <span data-ttu-id="0f597-122">預設是輸入資料行的名稱；但是，您可以選擇任何唯一的、描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="0f597-122">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="0f597-123">此屬性的值可以使用屬性運算式指定。</span><span class="sxs-lookup"><span data-stu-id="0f597-123">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="0f597-124">在＜ [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)＞所描述的取消樞紐狀況中，樞紐值會在 **[樞紐索引鍵值資料行名稱]** 選項所指定之新 Product 資料行中顯示為下列文字值： **Ham**, **Soda**, **Milk**, **Beer**和 **Chips**。</span><span class="sxs-lookup"><span data-stu-id="0f597-124">In the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), the Pivot Values will appear in the new Product column designated by the **Pivot Key Value Column Name** option, as the text values **Ham**, **Soda**, **Milk**, **Beer**, and **Chips**.</span></span>  
  
 <span data-ttu-id="0f597-125">**[樞紐索引鍵值資料行名稱]**</span><span class="sxs-lookup"><span data-stu-id="0f597-125">**Pivot Key Value Column Name**</span></span>  
 <span data-ttu-id="0f597-126">提供樞紐值資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="0f597-126">Provide a name for the pivot value column.</span></span> <span data-ttu-id="0f597-127">預設為「樞紐索引鍵值」；然而，您可以選擇任何唯一的、描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="0f597-127">The default is "Pivot Key Value"; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="0f597-128">在＜ [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)＞所描述的取消樞紐狀況中，樞紐索引鍵值資料行名稱為 **Product** ，並且會將新的 **Product** 資料行指定給 **Ham**, **Soda**, **Milk**, **Beer**和 **Chips** 資料行，以取消樞紐。</span><span class="sxs-lookup"><span data-stu-id="0f597-128">In the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), the Pivot Key Value Column Name is **Product** and designates the new **Product** column into which the **Ham**, **Soda**, **Milk**, **Beer**, and **Chips** columns are unpivoted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f597-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f597-129">See Also</span></span>  
 <span data-ttu-id="0f597-130">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0f597-130">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="0f597-131">樞紐轉換</span><span class="sxs-lookup"><span data-stu-id="0f597-131">Pivot Transformation</span></span>](data-flow/transformations/pivot-transformation.md)  
  
  
