---
title: 資料轉換編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontransformation.f1
helpviewer_keywords:
- Data Conversion Transformation Editor
ms.assetid: 7b4e4873-e8fe-4549-a965-65bebdb270bc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4b893f04dcca2dd2a1a5874b55c1c1c608aaeb12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709834"
---
# <a name="data-conversion-transformation-editor"></a><span data-ttu-id="bcd08-102">資料轉換編輯器</span><span class="sxs-lookup"><span data-stu-id="bcd08-102">Data Conversion Transformation Editor</span></span>
  <span data-ttu-id="bcd08-103">使用 [資料轉換編輯器]\*\*\*\* 對話方塊，即可選取要轉換的資料行、選取資料行要轉換成哪一種資料類型，以及設定轉換屬性。</span><span class="sxs-lookup"><span data-stu-id="bcd08-103">Use the **Data Conversion Transformation Editor** dialog box to select the columns to convert, select the data type to which the column is converted, and set conversion attributes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bcd08-104">[資料轉換 `FastParse` **編輯器**] 中無法使用資料轉換之輸出資料行的屬性，但是可以使用 [**進階編輯器**] 來設定它。</span><span class="sxs-lookup"><span data-stu-id="bcd08-104">The `FastParse` property of the output columns of the Data Conversion transformation is not available in the **Data Conversion Transformation Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="bcd08-105">如需這個屬性的詳細資訊，請參閱 [轉換自訂屬性](data-flow/transformations/transformation-custom-properties.md)的＜資料轉換＞一節。</span><span class="sxs-lookup"><span data-stu-id="bcd08-105">For more information on this property, see the Data Conversion Transformation section of [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="bcd08-106">若要深入了解資料轉換，請參閱 [資料轉換](data-flow/transformations/data-conversion-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="bcd08-106">To learn more about the Data Conversion transformation, see [Data Conversion Transformation](data-flow/transformations/data-conversion-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="bcd08-107">選項。</span><span class="sxs-lookup"><span data-stu-id="bcd08-107">Options</span></span>  
 <span data-ttu-id="bcd08-108">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="bcd08-108">**Available Input Columns**</span></span>  
 <span data-ttu-id="bcd08-109">使用核取方塊選取要轉換的資料行。</span><span class="sxs-lookup"><span data-stu-id="bcd08-109">Select columns to convert by using the check boxes.</span></span> <span data-ttu-id="bcd08-110">您的選取範圍會將輸入資料行加入下列資料表中。</span><span class="sxs-lookup"><span data-stu-id="bcd08-110">Your selections add input columns to the table below.</span></span>  
  
 <span data-ttu-id="bcd08-111">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="bcd08-111">**Input Column**</span></span>  
 <span data-ttu-id="bcd08-112">從可用的輸入資料行清單中，選取要轉換的資料行。</span><span class="sxs-lookup"><span data-stu-id="bcd08-112">Select columns to convert from the list of available input columns.</span></span> <span data-ttu-id="bcd08-113">您的選擇會反映在上面所勾選的核取方塊中。</span><span class="sxs-lookup"><span data-stu-id="bcd08-113">Your selections are reflected in the check box selections above.</span></span>  
  
 <span data-ttu-id="bcd08-114">**輸出別名**</span><span class="sxs-lookup"><span data-stu-id="bcd08-114">**Output Alias**</span></span>  
 <span data-ttu-id="bcd08-115">輸入每一個新資料行的別名。</span><span class="sxs-lookup"><span data-stu-id="bcd08-115">Type an alias for each new column.</span></span> <span data-ttu-id="bcd08-116">預設為 `Copy of`，後面接著輸入資料行的名稱；但是您也可以選擇任何唯一的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="bcd08-116">The default is `Copy of` followed by the input column name; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="bcd08-117">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="bcd08-117">**Data Type**</span></span>  
 <span data-ttu-id="bcd08-118">從清單中選取可用的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bcd08-118">Select an available data type from the list.</span></span> <span data-ttu-id="bcd08-119">如需詳細資訊，請參閱 [Integration Services 資料類型](data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="bcd08-119">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="bcd08-120">**長度**</span><span class="sxs-lookup"><span data-stu-id="bcd08-120">**Length**</span></span>  
 <span data-ttu-id="bcd08-121">設定字串資料的資料行長度。</span><span class="sxs-lookup"><span data-stu-id="bcd08-121">Set the column length for string data.</span></span>  
  
 <span data-ttu-id="bcd08-122">**有效位數**</span><span class="sxs-lookup"><span data-stu-id="bcd08-122">**Precision**</span></span>  
 <span data-ttu-id="bcd08-123">設定數值資料的有效位數。</span><span class="sxs-lookup"><span data-stu-id="bcd08-123">Set the precision for numeric data.</span></span>  
  
 <span data-ttu-id="bcd08-124">**縮放比例**</span><span class="sxs-lookup"><span data-stu-id="bcd08-124">**Scale**</span></span>  
 <span data-ttu-id="bcd08-125">設定數值資料的小數位數。</span><span class="sxs-lookup"><span data-stu-id="bcd08-125">Set the scale for numeric data.</span></span>  
  
 <span data-ttu-id="bcd08-126">**字碼頁**</span><span class="sxs-lookup"><span data-stu-id="bcd08-126">**Code page**</span></span>  
 <span data-ttu-id="bcd08-127">為 DT_STR 類型的資料行選取適當的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="bcd08-127">Select the appropriate code page for columns of type DT_STR.</span></span>  
  
 <span data-ttu-id="bcd08-128">**設定錯誤輸出**</span><span class="sxs-lookup"><span data-stu-id="bcd08-128">**Configure error output**</span></span>  
 <span data-ttu-id="bcd08-129">使用 [設定錯誤輸出](../../2014/integration-services/configure-error-output.md) 對話方塊來指定如何處理資料列層級錯誤。</span><span class="sxs-lookup"><span data-stu-id="bcd08-129">Specify how to handle row-level errors by using the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcd08-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcd08-130">See Also</span></span>  
 <span data-ttu-id="bcd08-131">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="bcd08-131">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="bcd08-132">使用資料轉換將資料轉換至不同的資料類型</span><span class="sxs-lookup"><span data-stu-id="bcd08-132">Convert Data to a Different Data Type by Using the Data Conversion Transformation</span></span>](data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md)  
  
  
