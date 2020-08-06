---
title: '[詞彙解壓縮轉換編輯器] (排除索引標籤) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextraction.inclusionexclusion.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 90110d95-fd97-4542-9cda-832c86606130
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9bc4b0401a1dd27111d0498e9e0d848c80da1742
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606416"
---
# <a name="term-extraction-transformation-editor-exclusion-tab"></a><span data-ttu-id="9cdfb-102">詞彙擷取轉換編輯器 (排除索引標籤)</span><span class="sxs-lookup"><span data-stu-id="9cdfb-102">Term Extraction Transformation Editor (Exclusion Tab)</span></span>
  <span data-ttu-id="9cdfb-103">使用 **[詞彙擷取轉換編輯器]** 對話方塊的 **[排除]** 索引標籤，可設定排除資料表的連接，並指定包含排除詞彙的資料行。</span><span class="sxs-lookup"><span data-stu-id="9cdfb-103">Use the **Exclusion** tab of the **Term Extraction Transformation Editor** dialog box to set up a connection to an exclusion table and specify the columns that contain exclusion terms.</span></span>  
  
 <span data-ttu-id="9cdfb-104">若要深入了解詞彙擷取轉換，請參閱＜ [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9cdfb-104">To learn more about the Term Extraction transformation, see [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9cdfb-105">選項。</span><span class="sxs-lookup"><span data-stu-id="9cdfb-105">Options</span></span>  
 <span data-ttu-id="9cdfb-106">**使用排除詞彙**</span><span class="sxs-lookup"><span data-stu-id="9cdfb-106">**Use exclusion terms**</span></span>  
 <span data-ttu-id="9cdfb-107">藉由指定包含排除詞彙的資料行，指出是否要在詞彙擷取期間排除特定詞彙。</span><span class="sxs-lookup"><span data-stu-id="9cdfb-107">Indicate whether to exclude specific terms during term extraction by specifying a column that contains exclusion terms.</span></span> <span data-ttu-id="9cdfb-108">如果您選擇要排除詞彙，就必須指定下列來源屬性。</span><span class="sxs-lookup"><span data-stu-id="9cdfb-108">You must specify the following source properties if you choose to exclude terms.</span></span>  
  
 <span data-ttu-id="9cdfb-109">**[無快取]**</span><span class="sxs-lookup"><span data-stu-id="9cdfb-109">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="9cdfb-110">選取現有的 OLE DB 連線管理員，或按一下 [新增]  來建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="9cdfb-110">Select an existing OLE DB connection manager, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="9cdfb-111">**新增**</span><span class="sxs-lookup"><span data-stu-id="9cdfb-111">**New**</span></span>  
 <span data-ttu-id="9cdfb-112">使用 [設定 OLE DB 連線管理員]  對話方塊，來建立新的資料庫連接。</span><span class="sxs-lookup"><span data-stu-id="9cdfb-112">Create a new connection to a database by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="9cdfb-113">**資料表或檢視**</span><span class="sxs-lookup"><span data-stu-id="9cdfb-113">**Table or view**</span></span>  
 <span data-ttu-id="9cdfb-114">選取包含排除詞彙的資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="9cdfb-114">Select the table or view that contains the exclusion terms.</span></span>  
  
 <span data-ttu-id="9cdfb-115">**資料行**</span><span class="sxs-lookup"><span data-stu-id="9cdfb-115">**Column**</span></span>  
 <span data-ttu-id="9cdfb-116">選取包含排除詞彙之資料表或檢視中的資料行。</span><span class="sxs-lookup"><span data-stu-id="9cdfb-116">Select the column in the table or view that contains the exclusion terms.</span></span>  
  
 <span data-ttu-id="9cdfb-117">**設定錯誤輸出**</span><span class="sxs-lookup"><span data-stu-id="9cdfb-117">**Configure Error Output**</span></span>  
 <span data-ttu-id="9cdfb-118">使用 [[設定錯誤輸出]](../../2014/integration-services/configure-error-output.md) 對話方塊，即可指定造成錯誤之資料列的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="9cdfb-118">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling for rows that cause errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cdfb-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cdfb-119">See Also</span></span>  
 <span data-ttu-id="9cdfb-120">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9cdfb-120">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="9cdfb-121">[[詞彙解壓縮轉換編輯器] &#40;[詞彙] [提取] 索引標籤&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md) </span><span class="sxs-lookup"><span data-stu-id="9cdfb-121">[Term Extraction Transformation Editor &#40;Term Extraction Tab&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md) </span></span>  
 <span data-ttu-id="9cdfb-122">[[詞彙解壓縮轉換編輯器] &#40;[Advanced] 索引標籤&#41;](../../2014/integration-services/term-extraction-transformation-editor-advanced-tab.md) </span><span class="sxs-lookup"><span data-stu-id="9cdfb-122">[Term Extraction Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/term-extraction-transformation-editor-advanced-tab.md) </span></span>  
 [<span data-ttu-id="9cdfb-123">詞彙查閱轉換</span><span class="sxs-lookup"><span data-stu-id="9cdfb-123">Term Lookup Transformation</span></span>](data-flow/transformations/lookup-transformation.md)  
  
  
