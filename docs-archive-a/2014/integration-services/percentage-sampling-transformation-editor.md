---
title: 百分比取樣轉換編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.percentagesamplingtransformation.f1
helpviewer_keywords:
- Percentage Sampling Transformation Editor
ms.assetid: 2c40d804-26a3-4d35-809b-bc923d83d451
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c4dbd96ab952b6c88bdaa7bf56a0a2f1b3585c57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592094"
---
# <a name="percentage-sampling-transformation-editor"></a><span data-ttu-id="9ecca-102">百分比取樣轉換編輯器</span><span class="sxs-lookup"><span data-stu-id="9ecca-102">Percentage Sampling Transformation Editor</span></span>
  <span data-ttu-id="9ecca-103">使用 **[百分比取樣轉換編輯器]** 對話方塊，即可依指定的資料列百分比，將輸入的一部分分割為取樣。</span><span class="sxs-lookup"><span data-stu-id="9ecca-103">Use the **Percentage Sampling Transformation Editor** dialog box to split part of an input into a sample using a specified percentage of rows.</span></span> <span data-ttu-id="9ecca-104">這個轉換會將輸入分成兩個不同的輸出。</span><span class="sxs-lookup"><span data-stu-id="9ecca-104">This transformation divides the input into two separate outputs.</span></span>  
  
 <span data-ttu-id="9ecca-105">若要深入了解百分比取樣轉換，請參閱＜ [Percentage Sampling Transformation](data-flow/transformations/percentage-sampling-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9ecca-105">To learn more about the percentage sampling transformation, see [Percentage Sampling Transformation](data-flow/transformations/percentage-sampling-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9ecca-106">選項</span><span class="sxs-lookup"><span data-stu-id="9ecca-106">Options</span></span>  
 <span data-ttu-id="9ecca-107">**資料列的百分比**</span><span class="sxs-lookup"><span data-stu-id="9ecca-107">**Percentage of rows**</span></span>  
 <span data-ttu-id="9ecca-108">指定在輸入中，要作為取樣的資料列百分比。</span><span class="sxs-lookup"><span data-stu-id="9ecca-108">Specify the percentage of rows in the input to use as a sample.</span></span>  
  
 <span data-ttu-id="9ecca-109">此屬性的值可以使用屬性運算式指定。</span><span class="sxs-lookup"><span data-stu-id="9ecca-109">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="9ecca-110">**取樣輸出名稱**</span><span class="sxs-lookup"><span data-stu-id="9ecca-110">**Sample output name**</span></span>  
 <span data-ttu-id="9ecca-111">提供包含取樣資料列之輸出的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="9ecca-111">Provide a unique name for the output that will include the sampled rows.</span></span> <span data-ttu-id="9ecca-112">提供的名稱將顯示在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師內。</span><span class="sxs-lookup"><span data-stu-id="9ecca-112">The name provided will be displayed within the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="9ecca-113">**未選取的輸出名稱**</span><span class="sxs-lookup"><span data-stu-id="9ecca-113">**Unselected output name**</span></span>  
 <span data-ttu-id="9ecca-114">提供輸出的唯一名稱，其中包含從取樣排除的資料列。</span><span class="sxs-lookup"><span data-stu-id="9ecca-114">Provide a unique name for the output that will contain the rows excluded from the sampling.</span></span> <span data-ttu-id="9ecca-115">提供的名稱將顯示在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師內。</span><span class="sxs-lookup"><span data-stu-id="9ecca-115">The name provided will be displayed within the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="9ecca-116">**使用下列隨機種子**</span><span class="sxs-lookup"><span data-stu-id="9ecca-116">**Use the following random seed**</span></span>  
 <span data-ttu-id="9ecca-117">指定轉換用來建立取樣之隨機號碼產生器的取樣種子。</span><span class="sxs-lookup"><span data-stu-id="9ecca-117">Specify the sampling seed for the random number generator that the transformation uses to create a sample.</span></span> <span data-ttu-id="9ecca-118">只建議用於開發和測試。</span><span class="sxs-lookup"><span data-stu-id="9ecca-118">This is only recommended for development and testing.</span></span> <span data-ttu-id="9ecca-119">如果未指定隨機種子，轉換會使用 Microsoft Windows 滴答計數。</span><span class="sxs-lookup"><span data-stu-id="9ecca-119">The transformation uses the Microsoft Windows tick count if a random seed is not specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ecca-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ecca-120">See Also</span></span>  
 <span data-ttu-id="9ecca-121">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9ecca-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="9ecca-122">資料列取樣轉換</span><span class="sxs-lookup"><span data-stu-id="9ecca-122">Row Sampling Transformation</span></span>](data-flow/transformations/row-sampling-transformation.md)  
  
  
