---
title: OLE DB 來源編輯器 (錯誤輸出頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbsourceadapter.errorhandling.f1
helpviewer_keywords:
- OLE DB Source Editor
ms.assetid: 7737c6ae-c16b-4856-aa6e-5882640093b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ded87747f041a4d8451048d4ef4671b029125873
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599591"
---
# <a name="ole-db-source-editor-error-output-page"></a><span data-ttu-id="cef40-102">OLE DB 來源編輯器 (錯誤輸出頁面)</span><span class="sxs-lookup"><span data-stu-id="cef40-102">OLE DB Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="cef40-103">使用 [OLE DB 來源編輯器]  對話方塊的 [錯誤輸出]  頁面，以選取錯誤處理選項，並設定錯誤輸出資料行上的屬性。</span><span class="sxs-lookup"><span data-stu-id="cef40-103">Use the **Error Output** page of the **OLE DB Source Editor** dialog box to select error handling options and to set properties on error output columns.</span></span>  
  
 <span data-ttu-id="cef40-104">若要深入了解 OLE DB 來源，請參閱＜ [OLE DB Source](data-flow/ole-db-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="cef40-104">To learn more about the OLE DB source, see [OLE DB Source](data-flow/ole-db-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="cef40-105">選項。</span><span class="sxs-lookup"><span data-stu-id="cef40-105">Options</span></span>  
 <span data-ttu-id="cef40-106">**輸入/輸出**</span><span class="sxs-lookup"><span data-stu-id="cef40-106">**Input/Output**</span></span>  
 <span data-ttu-id="cef40-107">檢視資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="cef40-107">View the name of the data source.</span></span>  
  
 <span data-ttu-id="cef40-108">**資料行**</span><span class="sxs-lookup"><span data-stu-id="cef40-108">**Column**</span></span>  
 <span data-ttu-id="cef40-109">檢視您在 [OLE DB 來源編輯器]  對話方塊的 [連接管理員]  頁面上所選取的外部 (來源) 資料行。</span><span class="sxs-lookup"><span data-stu-id="cef40-109">View the external (source) columns that you selected on the **Connection Manager** page of the **OLE DB Source Editor**dialog box.</span></span>  
  
 <span data-ttu-id="cef40-110">**錯誤**</span><span class="sxs-lookup"><span data-stu-id="cef40-110">**Error**</span></span>  
 <span data-ttu-id="cef40-111">指定錯誤發生時要採取的動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="cef40-111">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="cef40-112">**相關主題：** [資料中的錯誤處理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="cef40-112">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="cef40-113">**截斷**</span><span class="sxs-lookup"><span data-stu-id="cef40-113">**Truncation**</span></span>  
 <span data-ttu-id="cef40-114">指定截斷發生時要採取的動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="cef40-114">Specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="cef40-115">**說明**</span><span class="sxs-lookup"><span data-stu-id="cef40-115">**Description**</span></span>  
 <span data-ttu-id="cef40-116">檢視錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="cef40-116">View the description of the error.</span></span>  
  
 <span data-ttu-id="cef40-117">**將這個值設定到選取的資料格**</span><span class="sxs-lookup"><span data-stu-id="cef40-117">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="cef40-118">指定發生錯誤或截斷時要對所有選取之資料格採取的動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="cef40-118">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="cef40-119">**套用**</span><span class="sxs-lookup"><span data-stu-id="cef40-119">**Apply**</span></span>  
 <span data-ttu-id="cef40-120">將錯誤處理選項套用至選取的資料格。</span><span class="sxs-lookup"><span data-stu-id="cef40-120">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cef40-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cef40-121">See Also</span></span>  
 <span data-ttu-id="cef40-122">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="cef40-122">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="cef40-123">[OLE DB 來源編輯器 &#40;連線管理員頁面&#41;](../../2014/integration-services/ole-db-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="cef40-123">[OLE DB Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ole-db-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="cef40-124">[OLE DB 來源編輯器 &#40;資料行] 頁面&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="cef40-124">[OLE DB Source Editor &#40;Columns Page&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="cef40-125">[使用 OLE DB 來源來解壓縮資料](data-flow/extract-data-by-using-the-ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="cef40-125">[Extract Data by Using the OLE DB Source](data-flow/extract-data-by-using-the-ole-db-source.md) </span></span>  
 [<span data-ttu-id="cef40-126">OLE DB 連線管理員</span><span class="sxs-lookup"><span data-stu-id="cef40-126">OLE DB Connection Manager</span></span>](connection-manager/ole-db-connection-manager.md)  
  
  
