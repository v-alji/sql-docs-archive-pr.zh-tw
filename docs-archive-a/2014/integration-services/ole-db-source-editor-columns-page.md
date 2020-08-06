---
title: OLE DB 來源編輯器 (資料行] 頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbsourceadapter.columns.f1
helpviewer_keywords:
- OLE DB Source Editor
ms.assetid: bfbb0ae1-7759-4d45-8865-31df36ae5b34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 575a5a02198606d2412ff187750963ccb171e338
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592759"
---
# <a name="ole-db-source-editor-columns-page"></a><span data-ttu-id="5451b-102">OLE DB 來源編輯器 (資料行頁面)</span><span class="sxs-lookup"><span data-stu-id="5451b-102">OLE DB Source Editor (Columns Page)</span></span>
  <span data-ttu-id="5451b-103">使用 [OLE DB 來源編輯器]  對話方塊的 [資料行]  頁面，即可將輸出資料行對應至每個外部 (來源) 資料行。</span><span class="sxs-lookup"><span data-stu-id="5451b-103">Use the **Columns** page of the **OLE DB Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="5451b-104">若要深入了解 OLE DB 來源，請參閱＜ [OLE DB Source](data-flow/ole-db-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5451b-104">To learn more about the OLE DB source, see [OLE DB Source](data-flow/ole-db-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5451b-105">選項。</span><span class="sxs-lookup"><span data-stu-id="5451b-105">Options</span></span>  
 <span data-ttu-id="5451b-106">**可用的外部資料行**</span><span class="sxs-lookup"><span data-stu-id="5451b-106">**Available External Columns**</span></span>  
 <span data-ttu-id="5451b-107">在資料來源中檢視可用的外部資料行清單。</span><span class="sxs-lookup"><span data-stu-id="5451b-107">View the list of available external columns in the data source.</span></span> <span data-ttu-id="5451b-108">您無法使用此資料表來加入或刪除資料行。</span><span class="sxs-lookup"><span data-stu-id="5451b-108">You cannot use this table to add or delete columns.</span></span>  
  
 <span data-ttu-id="5451b-109">**[外部資料行]**</span><span class="sxs-lookup"><span data-stu-id="5451b-109">**External Column**</span></span>  
 <span data-ttu-id="5451b-110">依您在設定使用此來源之資料的元件時所見的順序來檢視外部 (來源) 資料行。</span><span class="sxs-lookup"><span data-stu-id="5451b-110">View external (source) columns in the order in which you will see them when configuring components that consume data from this source.</span></span> <span data-ttu-id="5451b-111">首先取消選取資料表中選取的資料行，然後依不同順序從清單中選取外部資料行，就可以變更此順序。</span><span class="sxs-lookup"><span data-stu-id="5451b-111">You can change this order by first clearing the selected columns in the table, and then selecting external columns from the list in a different order.</span></span>  
  
 <span data-ttu-id="5451b-112">**輸出資料行**</span><span class="sxs-lookup"><span data-stu-id="5451b-112">**Output Column**</span></span>  
 <span data-ttu-id="5451b-113">為每個輸出資料行提供唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="5451b-113">Provide a unique name for each output column.</span></span> <span data-ttu-id="5451b-114">預設值為選取的外部 (來源) 資料行的名稱；不過，您也可以選擇任何唯一的、描述性的名稱。</span><span class="sxs-lookup"><span data-stu-id="5451b-114">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="5451b-115">提供的名稱將顯示在  設計師內。</span><span class="sxs-lookup"><span data-stu-id="5451b-115">The name provided will be displayed within the SSIS Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5451b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5451b-116">See Also</span></span>  
 <span data-ttu-id="5451b-117">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="5451b-117">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="5451b-118">[OLE DB 來源編輯器 &#40;連線管理員頁面&#41;](../../2014/integration-services/ole-db-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="5451b-118">[OLE DB Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ole-db-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="5451b-119">[OLE DB 來源編輯器 &#40;錯誤輸出頁面&#41;](../../2014/integration-services/ole-db-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="5451b-119">[OLE DB Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/ole-db-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="5451b-120">[使用 OLE DB 來源來解壓縮資料](data-flow/extract-data-by-using-the-ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="5451b-120">[Extract Data by Using the OLE DB Source](data-flow/extract-data-by-using-the-ole-db-source.md) </span></span>  
 [<span data-ttu-id="5451b-121">OLE DB 連線管理員</span><span class="sxs-lookup"><span data-stu-id="5451b-121">OLE DB Connection Manager</span></span>](connection-manager/ole-db-connection-manager.md)  
  
  
