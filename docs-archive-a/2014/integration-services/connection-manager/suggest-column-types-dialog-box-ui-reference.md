---
title: 建議資料行類型對話方塊 UI 參考 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.suggestdatatypes.f1
ms.assetid: 8d5652e0-cf57-483f-828b-10f00c08418b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4cbca2a3186a58b1148eb9627825fdfddf334339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708541"
---
# <a name="suggest-column-types-dialog-box-ui-reference"></a><span data-ttu-id="0ff0d-102">建議資料行類型對話方塊 UI 參考</span><span class="sxs-lookup"><span data-stu-id="0ff0d-102">Suggest Column Types Dialog Box UI Reference</span></span>
  <span data-ttu-id="0ff0d-103">使用 [建議資料行類型]  對話方塊，根據檔案內容的取樣來識別一般檔案連線管理員中之資料行的資料類型與長度。</span><span class="sxs-lookup"><span data-stu-id="0ff0d-103">Use the **Suggest Column Types** dialog box to identify the data type and length of columns in a Flat File Connection Manager based on a sampling of the file content.</span></span>  
  
 <span data-ttu-id="0ff0d-104">若要深入了解 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]所使用的資料類型，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="0ff0d-104">To learn more about the data types used by [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0ff0d-105">選項。</span><span class="sxs-lookup"><span data-stu-id="0ff0d-105">Options</span></span>  
 <span data-ttu-id="0ff0d-106">**資料列數目**</span><span class="sxs-lookup"><span data-stu-id="0ff0d-106">**Number of rows**</span></span>  
 <span data-ttu-id="0ff0d-107">輸入或選取演算法所用之範例中的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="0ff0d-107">Type or select the number of rows in the sample that the algorithm uses.</span></span>  
  
 <span data-ttu-id="0ff0d-108">**建議最小整數資料類型**</span><span class="sxs-lookup"><span data-stu-id="0ff0d-108">**Suggest the smallest integer data type**</span></span>  
 <span data-ttu-id="0ff0d-109">清除這個核取方塊以略過評估。</span><span class="sxs-lookup"><span data-stu-id="0ff0d-109">Clear this check box to skip the assessment.</span></span> <span data-ttu-id="0ff0d-110">如果選取，則會決定含有整數數值資料之資料行的最小可能整數資料類型。</span><span class="sxs-lookup"><span data-stu-id="0ff0d-110">If selected, determines the smallest possible integer data type for columns that contain integral numeric data.</span></span>  
  
 <span data-ttu-id="0ff0d-111">**建議最小實數資料類型**</span><span class="sxs-lookup"><span data-stu-id="0ff0d-111">**Suggest the smallest real data type**</span></span>  
 <span data-ttu-id="0ff0d-112">清除這個核取方塊以略過評估。</span><span class="sxs-lookup"><span data-stu-id="0ff0d-112">Clear this check box to skip the assessment.</span></span> <span data-ttu-id="0ff0d-113">如果選取，則決定含有實數數值資料的資料行是否可使用最小實數資料類型 DT_R4。</span><span class="sxs-lookup"><span data-stu-id="0ff0d-113">If selected, determines whether columns that contain real numeric data can use the smaller real data type, DT_R4.</span></span>  
  
 <span data-ttu-id="0ff0d-114">**使用下列的值來識別布林資料行**</span><span class="sxs-lookup"><span data-stu-id="0ff0d-114">**Identify Boolean columns using the following values**</span></span>  
 <span data-ttu-id="0ff0d-115">輸入您要用來作為布林值 True 與 False 的兩個值。</span><span class="sxs-lookup"><span data-stu-id="0ff0d-115">Type the two values that you want to use as the Boolean values true and false.</span></span> <span data-ttu-id="0ff0d-116">這些值必須以逗號分隔，且第一個值代表 True。</span><span class="sxs-lookup"><span data-stu-id="0ff0d-116">The values must be separated by a comma, and the first value represents True.</span></span>  
  
 <span data-ttu-id="0ff0d-117">**填補字串資料行**</span><span class="sxs-lookup"><span data-stu-id="0ff0d-117">**Pad string columns**</span></span>  
 <span data-ttu-id="0ff0d-118">選取此核取方塊以啟用字串填補。</span><span class="sxs-lookup"><span data-stu-id="0ff0d-118">Select this check box to enable string padding.</span></span>  
  
 <span data-ttu-id="0ff0d-119">**百分比填補**</span><span class="sxs-lookup"><span data-stu-id="0ff0d-119">**Percent padding**</span></span>  
 <span data-ttu-id="0ff0d-120">輸入或選取資料行長度的百分比，以用來增加字元資料類型之資料行的長度。</span><span class="sxs-lookup"><span data-stu-id="0ff0d-120">Type or select the percentage of the column lengths by which to increase the length of columns for character data types.</span></span> <span data-ttu-id="0ff0d-121">百分比必須是整數。</span><span class="sxs-lookup"><span data-stu-id="0ff0d-121">The percentage must be an integer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ff0d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ff0d-122">See Also</span></span>  
 <span data-ttu-id="0ff0d-123">[Integration Services 錯誤和訊息參考](../integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0ff0d-123">[Integration Services Error and Message Reference](../integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="0ff0d-124">一般檔案連線管理員</span><span class="sxs-lookup"><span data-stu-id="0ff0d-124">Flat File Connection Manager</span></span>](file-connection-manager.md)  
  
  
