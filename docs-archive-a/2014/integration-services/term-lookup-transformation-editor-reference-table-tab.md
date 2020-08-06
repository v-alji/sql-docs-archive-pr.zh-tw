---
title: 詞彙查閱轉換編輯器 (參考資料表索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termlookup.referencetable.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 86ccec6d-615b-4f84-9226-ff80d8012f17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f76f15d894896e70139ef80cb2ebad7004ef47ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606412"
---
# <a name="term-lookup-transformation-editor-reference-table-tab"></a><span data-ttu-id="7c484-102">詞彙查閱轉換編輯器 (參考資料表索引標籤)</span><span class="sxs-lookup"><span data-stu-id="7c484-102">Term Lookup Transformation Editor (Reference Table Tab)</span></span>
  <span data-ttu-id="7c484-103">使用 [詞彙查閱轉換編輯器]  對話方塊的 [參考資料表]  索引標籤，即可指定參考 (查閱) 資料表的連接。</span><span class="sxs-lookup"><span data-stu-id="7c484-103">Use the **Reference Table** tab of the **Term Lookup Transformation Editor** dialog box to specify the connection to the reference (lookup) table.</span></span>  
  
 <span data-ttu-id="7c484-104">若要深入了解模糊查閱轉換，請參閱＜ [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7c484-104">To learn more about the Term Lookup transformation, see [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7c484-105">選項。</span><span class="sxs-lookup"><span data-stu-id="7c484-105">Options</span></span>  
 <span data-ttu-id="7c484-106">**[無快取]**</span><span class="sxs-lookup"><span data-stu-id="7c484-106">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="7c484-107">從清單中選取現有的連線管理員，或按一下 [新增]  來建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="7c484-107">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="7c484-108">**新增**</span><span class="sxs-lookup"><span data-stu-id="7c484-108">**New**</span></span>  
 <span data-ttu-id="7c484-109">使用 [設定 OLE DB 連接管理員]  對話方塊來建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="7c484-109">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="7c484-110">**參考資料表名稱**</span><span class="sxs-lookup"><span data-stu-id="7c484-110">**Reference table name**</span></span>  
 <span data-ttu-id="7c484-111">從清單中選取項目，以選取資料庫中的查閱資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="7c484-111">Select a lookup table or view from the database by selecting an item from the list.</span></span> <span data-ttu-id="7c484-112">資料表或檢視應包含具有現有詞彙清單的資料行，可以用來與來源資料行中的文字進行比較。</span><span class="sxs-lookup"><span data-stu-id="7c484-112">The table or view should contain a column with an existing list of terms that the text in the source column can be compared to.</span></span>  
  
 <span data-ttu-id="7c484-113">**設定錯誤輸出**</span><span class="sxs-lookup"><span data-stu-id="7c484-113">**Configure Error Output**</span></span>  
 <span data-ttu-id="7c484-114">使用 [ [設定錯誤輸出](../../2014/integration-services/configure-error-output.md) ] 對話方塊，即可指定造成錯誤之資料列的錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="7c484-114">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling options for rows that cause errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c484-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c484-115">See Also</span></span>  
 <span data-ttu-id="7c484-116">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="7c484-116">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="7c484-117">[詞彙查閱轉換編輯器 &#40;詞彙查閱] 索引標籤&#41;](../../2014/integration-services/term-lookup-transformation-editor-term-lookup-tab.md) </span><span class="sxs-lookup"><span data-stu-id="7c484-117">[Term Lookup Transformation Editor &#40;Term Lookup Tab&#41;](../../2014/integration-services/term-lookup-transformation-editor-term-lookup-tab.md) </span></span>  
 <span data-ttu-id="7c484-118">[詞彙查閱轉換編輯器 &#40;[Advanced] 索引標籤&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md) </span><span class="sxs-lookup"><span data-stu-id="7c484-118">[Term Lookup Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md) </span></span>  
 [<span data-ttu-id="7c484-119">詞彙擷取轉換</span><span class="sxs-lookup"><span data-stu-id="7c484-119">Term Extraction Transformation</span></span>](data-flow/transformations/term-extraction-transformation.md)  
  
  
