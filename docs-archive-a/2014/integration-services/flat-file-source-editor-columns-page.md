---
title: '[一般檔案來源編輯器] ([資料行] 頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.columns.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: b5af5f65-c087-44fd-b5ae-d0441245fef2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9b0249b2b17d50fdef4b5cf4aff70a1318614257
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592149"
---
# <a name="flat-file-source-editor-columns-page"></a><span data-ttu-id="130a3-102">一般檔案來源編輯器 (資料行頁面)</span><span class="sxs-lookup"><span data-stu-id="130a3-102">Flat File Source Editor (Columns Page)</span></span>
  <span data-ttu-id="130a3-103">使用 [一般檔案來源編輯器]\*\*\*\* 對話方塊的 [資料行]\*\*\*\* 節點，將輸出資料行對應至每個外部 (來源) 資料行。</span><span class="sxs-lookup"><span data-stu-id="130a3-103">Use the **Columns** node of the **Flat File Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="130a3-104">[一般檔案 `FileNameColumnName` 來源編輯器] 中無法使用一般檔案來源的屬性和 `FastParse` 其輸出資料行**Flat File Source Editor**的屬性，但是可以使用 [**進階編輯器**] 來設定。</span><span class="sxs-lookup"><span data-stu-id="130a3-104">The `FileNameColumnName` property of the Flat File source and the `FastParse` property of its output columns are not available in the **Flat File Source Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="130a3-105">如需這些屬性的詳細資訊，請參閱 [一般檔案自訂屬性](data-flow/flat-file-custom-properties.md)的＜一般檔案來源＞一節。</span><span class="sxs-lookup"><span data-stu-id="130a3-105">For more information on these properties, see the Flat File Source section of [Flat File Custom Properties](data-flow/flat-file-custom-properties.md).</span></span>  
  
 <span data-ttu-id="130a3-106">若要深入了解一般檔案來源，請參閱＜ [Flat File Source](data-flow/flat-file-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="130a3-106">To learn more about the Flat File source, see [Flat File Source](data-flow/flat-file-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="130a3-107">選項。</span><span class="sxs-lookup"><span data-stu-id="130a3-107">Options</span></span>  
 <span data-ttu-id="130a3-108">**可用的外部資料行**</span><span class="sxs-lookup"><span data-stu-id="130a3-108">**Available External Columns**</span></span>  
 <span data-ttu-id="130a3-109">在資料來源中檢視可用的外部資料行清單。</span><span class="sxs-lookup"><span data-stu-id="130a3-109">View the list of available external columns in the data source.</span></span> <span data-ttu-id="130a3-110">您無法使用此資料表來加入或刪除資料行。</span><span class="sxs-lookup"><span data-stu-id="130a3-110">You cannot use this table to add or delete columns.</span></span>  
  
 <span data-ttu-id="130a3-111">**[外部資料行]**</span><span class="sxs-lookup"><span data-stu-id="130a3-111">**External Column**</span></span>  
 <span data-ttu-id="130a3-112">依工作讀取外部 (來源) 資料行的順序來檢視它們。</span><span class="sxs-lookup"><span data-stu-id="130a3-112">View external (source) columns in the order in which the task will read them.</span></span> <span data-ttu-id="130a3-113">首先取消選取資料表中選取的資料行，然後依不同順序從清單中選取外部資料行，就可以變更此順序。</span><span class="sxs-lookup"><span data-stu-id="130a3-113">You can change this order by first clearing the selected columns in the table, and then selecting external columns from the list in a different order.</span></span>  
  
 <span data-ttu-id="130a3-114">**輸出資料行**</span><span class="sxs-lookup"><span data-stu-id="130a3-114">**Output Column**</span></span>  
 <span data-ttu-id="130a3-115">為每個輸出資料行提供唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="130a3-115">Provide a unique name for each output column.</span></span> <span data-ttu-id="130a3-116">預設值為選取的外部 (來源) 資料行的名稱；不過，您也可以選擇任何唯一的、描述性的名稱。</span><span class="sxs-lookup"><span data-stu-id="130a3-116">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="130a3-117">提供的名稱將顯示在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師內。</span><span class="sxs-lookup"><span data-stu-id="130a3-117">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="130a3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="130a3-118">See Also</span></span>  
 <span data-ttu-id="130a3-119">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="130a3-119">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="130a3-120">[[一般檔案來源編輯器] &#40;連線管理員頁面&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="130a3-120">[Flat File Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="130a3-121">[一般檔案來源編輯器 &#40;錯誤輸出頁面&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="130a3-121">[Flat File Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="130a3-122">一般檔案連線管理員</span><span class="sxs-lookup"><span data-stu-id="130a3-122">Flat File Connection Manager</span></span>](connection-manager/file-connection-manager.md)  
  
  
