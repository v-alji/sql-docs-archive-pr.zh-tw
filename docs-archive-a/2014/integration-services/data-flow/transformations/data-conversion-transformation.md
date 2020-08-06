---
title: 資料轉換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontrans.f1
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: fd515bbc-6f49-4d0c-ae7f-6ea3c3f24a1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 57b1f70c070cdf81dc0bc899ed365d048db26cc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585517"
---
# <a name="data-conversion-transformation"></a><span data-ttu-id="db08f-102">資料轉換</span><span class="sxs-lookup"><span data-stu-id="db08f-102">Data Conversion Transformation</span></span>
  <span data-ttu-id="db08f-103">「資料轉換」會將輸入資料行中的資料轉換成不同的資料類型，然後將它複製到新的輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="db08f-103">The Data Conversion transformation converts the data in an input column to a different data type and then copies it to a new output column.</span></span> <span data-ttu-id="db08f-104">例如，封裝可從多個來源擷取資料，然後使用此轉換將資料行轉換成目的地資料存放區所需的資料類型。</span><span class="sxs-lookup"><span data-stu-id="db08f-104">For example, a package can extract data from multiple sources, and then use this transformation to convert columns to the data type required by the destination data store.</span></span> <span data-ttu-id="db08f-105">您可以對單一輸入資料行套用多項轉換。</span><span class="sxs-lookup"><span data-stu-id="db08f-105">You can apply multiple conversions to a single input column.</span></span>  
  
 <span data-ttu-id="db08f-106">使用此轉換，封裝即可執行下列類型的資料轉換：</span><span class="sxs-lookup"><span data-stu-id="db08f-106">Using this transformation, a package can perform the following types of data conversions:</span></span>  
  
-   <span data-ttu-id="db08f-107">變更資料類型。</span><span class="sxs-lookup"><span data-stu-id="db08f-107">Change the data type.</span></span> <span data-ttu-id="db08f-108">如需詳細資訊，請參閱 [Integration Services 資料類型](../integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="db08f-108">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="db08f-109">如果您要將資料轉換成日期或日期時間資料類型，則輸出資料行中的資料會使用 ISO 格式，即使地區設定偏好設定可能指定不同的格式。</span><span class="sxs-lookup"><span data-stu-id="db08f-109">If you are converting data to a date or a datetime data type, the date in the output column is in the ISO format, although the locale preference may specify a different format.</span></span>  
  
-   <span data-ttu-id="db08f-110">設定字串資料的資料行長度，以及數值資料的有效位數和小數位數。</span><span class="sxs-lookup"><span data-stu-id="db08f-110">Set the column length of string data and the precision and scale on numeric data.</span></span> <span data-ttu-id="db08f-111">如需詳細資訊，請參閱[有效位數、小數位數和長度 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/precision-scale-and-length-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="db08f-111">For more information, see [Precision, Scale, and Length &#40;Transact-SQL&#41;](/sql/t-sql/data-types/precision-scale-and-length-transact-sql).</span></span>  
  
-   <span data-ttu-id="db08f-112">指定字碼頁。</span><span class="sxs-lookup"><span data-stu-id="db08f-112">Specify a code page.</span></span> <span data-ttu-id="db08f-113">如需詳細資訊，請參閱 [Comparing String Data](../comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="db08f-113">For more information, see [Comparing String Data](../comparing-string-data.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="db08f-114">在字串資料類型的資料行之間進行複製時，兩個資料行必須使用相同字碼頁。</span><span class="sxs-lookup"><span data-stu-id="db08f-114">When copying between columns with a string data type, the two columns must use the same code page.</span></span>  
  
 <span data-ttu-id="db08f-115">如果字串資料的輸出資料行長度比其對應輸入資料行的長度短，則輸出資料會遭到截斷。</span><span class="sxs-lookup"><span data-stu-id="db08f-115">If the length of an output column of string data is shorter than the length of its corresponding input column, the output data is truncated.</span></span> <span data-ttu-id="db08f-116">如需詳細資訊，請參閱 [處理資料中的錯誤](../error-handling-in-data.md)。</span><span class="sxs-lookup"><span data-stu-id="db08f-116">For more information, see [Error Handling in Data](../error-handling-in-data.md).</span></span>  
  
 <span data-ttu-id="db08f-117">這個轉換有一個輸入、一個輸出與一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="db08f-117">This transformation has one input, one output, and one error output.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="db08f-118">相關工作</span><span class="sxs-lookup"><span data-stu-id="db08f-118">Related Tasks</span></span>  
 <span data-ttu-id="db08f-119">您可以透過「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="db08f-119">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span> <span data-ttu-id="db08f-120">如需在 SSIS 設計師中使用「資料轉換」的相關資訊，請參閱 [使用資料轉換將資料轉換至不同的資料類型](data-conversion-transformation.md) 和 [資料轉換編輯器](../../data-conversion-transformation-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="db08f-120">For information about using the Data Conversion Transformation in the SSIS Designer, see [Convert Data to a Different Data Type by Using the Data Conversion Transformation](data-conversion-transformation.md) and [Data Conversion Transformation Editor](../../data-conversion-transformation-editor.md).</span></span> <span data-ttu-id="db08f-121">如需以程式設計方式設定此轉換屬性的詳細資訊，請參閱 [通用屬性](../../common-properties.md) 和 [轉換自訂屬性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="db08f-121">For information about setting properties of this transformation programmatically, see [Common Properties](../../common-properties.md) and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="db08f-122">相關內容</span><span class="sxs-lookup"><span data-stu-id="db08f-122">Related Content</span></span>  
 <span data-ttu-id="db08f-123">blogs.msdn.com 上的部落格文章： [SSIS 2008 中各種資料類型轉換技術的效能比較](https://techcommunity.microsoft.com/t5/datacat/performance-comparison-between-data-type-conversion-techniques/ba-p/305035)。</span><span class="sxs-lookup"><span data-stu-id="db08f-123">Blog entry, [Performance Comparison between Data Type Conversion Techniques in SSIS 2008](https://techcommunity.microsoft.com/t5/datacat/performance-comparison-between-data-type-conversion-techniques/ba-p/305035), on blogs.msdn.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db08f-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db08f-124">See Also</span></span>  
 <span data-ttu-id="db08f-125">[快速剖析](../../fast-parse.md) </span><span class="sxs-lookup"><span data-stu-id="db08f-125">[Fast Parse](../../fast-parse.md) </span></span>  
 <span data-ttu-id="db08f-126">[資料流程](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="db08f-126">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="db08f-127">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="db08f-127">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
