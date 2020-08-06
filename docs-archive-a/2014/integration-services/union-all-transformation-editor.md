---
title: 聯集全部轉換編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unionalltransformation.f1
helpviewer_keywords:
- Union All Transformation Editor
ms.assetid: 32fbc1c1-da83-4684-9479-31fc3e2df98c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a7e84c106767aa897b2e419b51ca5b5c538501cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592743"
---
# <a name="union-all-transformation-editor"></a><span data-ttu-id="e6c25-102">聯集全部轉換編輯器</span><span class="sxs-lookup"><span data-stu-id="e6c25-102">Union All Transformation Editor</span></span>
  <span data-ttu-id="e6c25-103">使用 **[聯集全部轉換編輯器]** 對話方塊，即可將數個輸入資料列集合併至單一輸出資料列集。</span><span class="sxs-lookup"><span data-stu-id="e6c25-103">Use the **Union All Transformation Editor** dialog box to merge several input rowsets into a single output rowset.</span></span> <span data-ttu-id="e6c25-104">藉由在資料流程中包含聯集全部轉換，您可以合併多個資料流程中的資料、藉由巢狀聯集全部轉換來建立複雜資料集、以及更正資料中的錯誤之後重新合併資料列。</span><span class="sxs-lookup"><span data-stu-id="e6c25-104">By including the Union All transformation in a data flow, you can merge data from multiple data flows, create complex datasets by nesting Union All transformations, and re-merge rows after you correct errors in the data.</span></span>  
  
 <span data-ttu-id="e6c25-105">若要深入了解聯集全部轉換，請參閱＜ [Union All Transformation](data-flow/transformations/union-all-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e6c25-105">To learn more about the Union All transformation, see [Union All Transformation](data-flow/transformations/union-all-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e6c25-106">選項</span><span class="sxs-lookup"><span data-stu-id="e6c25-106">Options</span></span>  
 <span data-ttu-id="e6c25-107">**輸出資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="e6c25-107">**Output Column Name**</span></span>  
 <span data-ttu-id="e6c25-108">輸入每個資料行的別名。</span><span class="sxs-lookup"><span data-stu-id="e6c25-108">Type an alias for each column.</span></span> <span data-ttu-id="e6c25-109">預設值為第一個 (參考) 輸入的輸入資料行名稱；不過，您也可以選擇任何唯一的、描述性的名稱。</span><span class="sxs-lookup"><span data-stu-id="e6c25-109">The default is the name of the input column from the first (reference) input; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="e6c25-110">**聯集全部輸入 1**</span><span class="sxs-lookup"><span data-stu-id="e6c25-110">**Union All Input 1**</span></span>  
 <span data-ttu-id="e6c25-111">從第一個 (參考) 輸入的可用輸入資料行清單中選取。</span><span class="sxs-lookup"><span data-stu-id="e6c25-111">Select from the list of available input columns in the first (reference) input.</span></span> <span data-ttu-id="e6c25-112">對應資料行的中繼資料必須相符。</span><span class="sxs-lookup"><span data-stu-id="e6c25-112">The metadata of mapped columns must match.</span></span>  
  
 <span data-ttu-id="e6c25-113">**聯集全部輸入 n**</span><span class="sxs-lookup"><span data-stu-id="e6c25-113">**Union All Input n**</span></span>  
 <span data-ttu-id="e6c25-114">從第二個和其他輸入的可用輸入資料行清單中選取。</span><span class="sxs-lookup"><span data-stu-id="e6c25-114">Select from the list of available input columns in the second and additional inputs.</span></span> <span data-ttu-id="e6c25-115">對應資料行的中繼資料必須相符。</span><span class="sxs-lookup"><span data-stu-id="e6c25-115">The metadata of mapped columns must match.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6c25-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6c25-116">See Also</span></span>  
 <span data-ttu-id="e6c25-117">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e6c25-117">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="e6c25-118">[使用聯集全部轉換來合併資料](data-flow/transformations/merge-data-by-using-the-union-all-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="e6c25-118">[Merge Data by Using the Union All Transformation](data-flow/transformations/merge-data-by-using-the-union-all-transformation.md) </span></span>  
 <span data-ttu-id="e6c25-119">[合併轉換](data-flow/transformations/merge-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="e6c25-119">[Merge Transformation](data-flow/transformations/merge-transformation.md) </span></span>  
 [<span data-ttu-id="e6c25-120">合併聯結轉換</span><span class="sxs-lookup"><span data-stu-id="e6c25-120">Merge Join Transformation</span></span>](data-flow/transformations/merge-join-transformation.md)  
  
  
