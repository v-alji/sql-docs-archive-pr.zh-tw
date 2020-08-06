---
title: 資料列取樣轉換編輯器 (取樣頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ROWSAMPLINGTRANSFORMATION.COLUMNS.F1
- sql12.dts.designer.rowsamplingtransformation.f1
helpviewer_keywords:
- Row Sampling Transformation Editor
ms.assetid: 544c7709-6de0-4c08-bda3-759985be9a05
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 26d0c0439e548172225f02220d8f6814a1168ea9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687982"
---
# <a name="row-sampling-transformation-editor-sampling-page"></a><span data-ttu-id="fd169-102">資料列取樣轉換編輯器 (取樣頁面)</span><span class="sxs-lookup"><span data-stu-id="fd169-102">Row Sampling Transformation Editor (Sampling Page)</span></span>
  <span data-ttu-id="fd169-103">使用 **[資料列取樣轉換編輯器]** 對話方塊，即可將輸入的一部分分割為指定資料列數目的取樣。</span><span class="sxs-lookup"><span data-stu-id="fd169-103">Use the **Row Sampling Transformation Editor** dialog box to split a portion of an input into a sample using a specified number of rows.</span></span> <span data-ttu-id="fd169-104">這個轉換會將輸入分成兩個不同的輸出。</span><span class="sxs-lookup"><span data-stu-id="fd169-104">This transformation divides the input into two separate outputs.</span></span>  
  
 <span data-ttu-id="fd169-105">若要深入了解資料列取樣轉換，請參閱＜ [Row Sampling Transformation](data-flow/transformations/row-sampling-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fd169-105">To learn more about the Row Sampling transformation, see [Row Sampling Transformation](data-flow/transformations/row-sampling-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="fd169-106">選項。</span><span class="sxs-lookup"><span data-stu-id="fd169-106">Options</span></span>  
 <span data-ttu-id="fd169-107">**資料列數目**</span><span class="sxs-lookup"><span data-stu-id="fd169-107">**Number of rows**</span></span>  
 <span data-ttu-id="fd169-108">指定輸入中的資料列數目作為取樣。</span><span class="sxs-lookup"><span data-stu-id="fd169-108">Specify the number of rows from the input to use as a sample.</span></span>  
  
 <span data-ttu-id="fd169-109">此屬性的值可以使用屬性運算式指定。</span><span class="sxs-lookup"><span data-stu-id="fd169-109">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="fd169-110">**取樣輸出名稱**</span><span class="sxs-lookup"><span data-stu-id="fd169-110">**Sample output name**</span></span>  
 <span data-ttu-id="fd169-111">提供包含取樣資料列之輸出的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="fd169-111">Provide a unique name for the output that will include the sampled rows.</span></span> <span data-ttu-id="fd169-112">提供的名稱將顯示在 SSIS 設計師內。</span><span class="sxs-lookup"><span data-stu-id="fd169-112">The name provided will be displayed within SSIS Designer.</span></span>  
  
 <span data-ttu-id="fd169-113">**未選取的輸出名稱**</span><span class="sxs-lookup"><span data-stu-id="fd169-113">**Unselected output name**</span></span>  
 <span data-ttu-id="fd169-114">提供輸出的唯一名稱，其中包含從取樣排除的資料列。</span><span class="sxs-lookup"><span data-stu-id="fd169-114">Provide a unique name for the output that will contain the rows excluded from the sampling.</span></span> <span data-ttu-id="fd169-115">提供的名稱將顯示在 SSIS 設計師內。</span><span class="sxs-lookup"><span data-stu-id="fd169-115">The name provided will be displayed within SSIS Designer.</span></span>  
  
 <span data-ttu-id="fd169-116">**使用下列隨機種子**</span><span class="sxs-lookup"><span data-stu-id="fd169-116">**Use the following random seed**</span></span>  
 <span data-ttu-id="fd169-117">指定轉換用來建立取樣之隨機號碼產生器的取樣種子。</span><span class="sxs-lookup"><span data-stu-id="fd169-117">Specify the sampling seed for the random number generator that the transformation uses to create a sample.</span></span> <span data-ttu-id="fd169-118">只建議用於開發和測試。</span><span class="sxs-lookup"><span data-stu-id="fd169-118">This is only recommended for development and testing.</span></span> <span data-ttu-id="fd169-119">如果未指定隨機種子，則轉換會使用 Microsoft Windows 滴答計數作為種子。</span><span class="sxs-lookup"><span data-stu-id="fd169-119">The transformation uses the Microsoft Windows tick count as a seed if a random seed is not specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd169-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd169-120">See Also</span></span>  
 <span data-ttu-id="fd169-121">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fd169-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="fd169-122">百分比取樣轉換</span><span class="sxs-lookup"><span data-stu-id="fd169-122">Percentage Sampling Transformation</span></span>](data-flow/transformations/percentage-sampling-transformation.md)  
  
  
