---
title: '[一般檔案來源編輯器] (連線管理員頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.connection.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: 2efd6baa-ed75-4f3f-b667-514024cebdb8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 03c1693c001dad2c8e90211b065eda208c42a07b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592145"
---
# <a name="flat-file-source-editor-connection-manager-page"></a><span data-ttu-id="3ea3a-102">一般檔案來源編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="3ea3a-102">Flat File Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="3ea3a-103">使用 **[一般檔案來源編輯器]** 對話方塊的 **[連接管理員]** 頁面，以選取一般檔案來源將要使用的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="3ea3a-103">Use the **Connection Manager** page of the **Flat File Source Editor** dialog box to select the connection manager that the Flat File source will use.</span></span> <span data-ttu-id="3ea3a-104">一般檔案來源會從文字檔讀取資料，其格式可以是分隔、固定寬度或混合格式。</span><span class="sxs-lookup"><span data-stu-id="3ea3a-104">The Flat File source reads data from a text file, which can be in a delimited, fixed width, or mixed format.</span></span>  
  
 <span data-ttu-id="3ea3a-105">一般檔案來源可以使用下列其中一種類型的連接管理員：</span><span class="sxs-lookup"><span data-stu-id="3ea3a-105">A Flat File source can use one of the following types of connection managers:</span></span>  
  
-   <span data-ttu-id="3ea3a-106">如果來源為單一的一般檔案，則為「一般檔案」連接管理員。</span><span class="sxs-lookup"><span data-stu-id="3ea3a-106">A Flat File connection manager if the source is a single flat file.</span></span> <span data-ttu-id="3ea3a-107">如需相關資訊，請參閱 [Flat File Connection Manager](connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="3ea3a-107">For more information, see [Flat File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
-   <span data-ttu-id="3ea3a-108">如果來源為多個一般檔案，而且資料流程工作位於迴圈容器 (如 For 迴圈容器) 內，則為「多個一般檔案」連接管理員。</span><span class="sxs-lookup"><span data-stu-id="3ea3a-108">A Multiple Flat Files connection manager if the source is multiple flat files and the Data Flow task is inside a loop container, such as the For Loop container.</span></span> <span data-ttu-id="3ea3a-109">在此容器的每一個迴圈上，「一般檔案」來源會從「多個一般檔案」連接管理員提供的下一個檔案名稱中載入資料。</span><span class="sxs-lookup"><span data-stu-id="3ea3a-109">On each loop of the container, the Flat File source loads data from the next file name that the Multiple Flat Files connection manager provides.</span></span> <span data-ttu-id="3ea3a-110">如需詳細資訊，請參閱 [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="3ea3a-110">For more information, see [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).</span></span>  
  
 <span data-ttu-id="3ea3a-111">若要深入了解一般檔案來源，請參閱＜ [Flat File Source](data-flow/flat-file-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="3ea3a-111">To learn more about the Flat File source, see [Flat File Source](data-flow/flat-file-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3ea3a-112">選項</span><span class="sxs-lookup"><span data-stu-id="3ea3a-112">Options</span></span>  
 <span data-ttu-id="3ea3a-113">**一般檔案連線管理員**</span><span class="sxs-lookup"><span data-stu-id="3ea3a-113">**Flat file connection manager**</span></span>  
 <span data-ttu-id="3ea3a-114">從清單中選取現有的連線管理員，或按一下 [新增]\*\*\*\* 建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="3ea3a-114">Select an existing connection manager from the list, or create a new connection manager by clicking **New**.</span></span>  
  
 <span data-ttu-id="3ea3a-115">**新增**</span><span class="sxs-lookup"><span data-stu-id="3ea3a-115">**New**</span></span>  
 <span data-ttu-id="3ea3a-116">使用 [一般檔案連線管理員編輯器]\*\*\*\* 對話方塊建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="3ea3a-116">Create a new connection manager by using the **Flat File Connection Manager Editor** dialog box.</span></span>  
  
 <span data-ttu-id="3ea3a-117">**將來源的 Null 值保留為資料流程中的 Null 值**</span><span class="sxs-lookup"><span data-stu-id="3ea3a-117">**Retain null values from the source as null values in the data flow**</span></span>  
 <span data-ttu-id="3ea3a-118">指定擷取資料時是否保留 Null 值。</span><span class="sxs-lookup"><span data-stu-id="3ea3a-118">Specify whether to keep null values when data is extracted.</span></span> <span data-ttu-id="3ea3a-119">此屬性的預設值為 **false**。</span><span class="sxs-lookup"><span data-stu-id="3ea3a-119">The default value of this property is **false**.</span></span> <span data-ttu-id="3ea3a-120">當此值為 `alse` 時，一般檔案來源會以各資料行適當的預設值取代來源資料的 Null 值，例如字串資料行的空白字串和數值資料行的零。</span><span class="sxs-lookup"><span data-stu-id="3ea3a-120">When this value is f`alse`, the Flat File source replaces null values from the source data with appropriate default values for each column, such as empty strings for string columns and zero for numeric columns.</span></span>  
  
 <span data-ttu-id="3ea3a-121">**預覽**</span><span class="sxs-lookup"><span data-stu-id="3ea3a-121">**Preview**</span></span>  
 <span data-ttu-id="3ea3a-122">使用 [資料檢視]  對話方塊來預覽結果。</span><span class="sxs-lookup"><span data-stu-id="3ea3a-122">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="3ea3a-123">預覽最多可顯示 200 個資料列。</span><span class="sxs-lookup"><span data-stu-id="3ea3a-123">Preview can display up to 200 rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ea3a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ea3a-124">See Also</span></span>  
 <span data-ttu-id="3ea3a-125">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3ea3a-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="3ea3a-126">[[一般檔案來源編輯器] &#40;[資料行] 頁面&#41;](../../2014/integration-services/flat-file-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="3ea3a-126">[Flat File Source Editor &#40;Columns Page&#41;](../../2014/integration-services/flat-file-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="3ea3a-127">[一般檔案來源編輯器 &#40;錯誤輸出頁面&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="3ea3a-127">[Flat File Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="3ea3a-128">一般檔案連線管理員</span><span class="sxs-lookup"><span data-stu-id="3ea3a-128">Flat File Connection Manager</span></span>](connection-manager/file-connection-manager.md)  
  
  
