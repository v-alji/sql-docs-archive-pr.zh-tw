---
title: 一般檔案連線管理員編輯器 (預覽頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ffileconnection.preview.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: de47ea98-135e-4730-900e-dac629848798
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b0f71b347bc943216a4b309cc58202ed8ab9183e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592158"
---
# <a name="flat-file-connection-manager-editor-preview-page"></a><span data-ttu-id="848cf-102">一般檔案連接管理員編輯器 (預覽頁面)</span><span class="sxs-lookup"><span data-stu-id="848cf-102">Flat File Connection Manager Editor (Preview Page)</span></span>
  <span data-ttu-id="848cf-103">使用 [一般檔案連線管理員編輯器]\*\*\*\* 對話方塊的 [預覽]\*\*\*\* 節點，即可以表格式格式來檢視來源檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="848cf-103">Use the **Preview** node of the **Flat File Connection Manager Editor** dialog box to view the contents of the source file in a tabular format.</span></span>  
  
 <span data-ttu-id="848cf-104">若要深入了解一般檔案連接管理員，請參閱＜ [Flat File Connection Manager](connection-manager/file-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="848cf-104">To learn more about the Flat File connection manager, see [Flat File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="848cf-105">選項。</span><span class="sxs-lookup"><span data-stu-id="848cf-105">Options</span></span>  
 <span data-ttu-id="848cf-106">**連線管理員名稱**</span><span class="sxs-lookup"><span data-stu-id="848cf-106">**Connection manager name**</span></span>  
 <span data-ttu-id="848cf-107">提供唯一的名稱給工作流程中的一般檔案連接。</span><span class="sxs-lookup"><span data-stu-id="848cf-107">Provide a unique name for the Flat File connection in the workflow.</span></span> <span data-ttu-id="848cf-108">提供的名稱將顯示在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師內。</span><span class="sxs-lookup"><span data-stu-id="848cf-108">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="848cf-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="848cf-109">**Description**</span></span>  
 <span data-ttu-id="848cf-110">描述連接。</span><span class="sxs-lookup"><span data-stu-id="848cf-110">Describe the connection.</span></span> <span data-ttu-id="848cf-111">最佳作法是以其用途描述連接，使封裝可以自我記錄並易於維護。</span><span class="sxs-lookup"><span data-stu-id="848cf-111">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="848cf-112">**略過的資料列數**</span><span class="sxs-lookup"><span data-stu-id="848cf-112">**Data rows to skip**</span></span>  
 <span data-ttu-id="848cf-113">指定在一般檔案開頭要略過的資料列數。</span><span class="sxs-lookup"><span data-stu-id="848cf-113">Specify how many rows to skip at the beginning of the flat file.</span></span>  
  
 <span data-ttu-id="848cf-114">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="848cf-114">**Refresh**</span></span>  
 <span data-ttu-id="848cf-115">按一下 [重新整理]\*\*\*\*，即可檢視變更要略過之資料列數的影響。</span><span class="sxs-lookup"><span data-stu-id="848cf-115">View the effect of changing the number of rows to skip by clicking **Refresh**.</span></span> <span data-ttu-id="848cf-116">僅在您已變更其他連接選項之後，才會看見此按鈕。</span><span class="sxs-lookup"><span data-stu-id="848cf-116">This button only becomes visible after you have changed other connection options.</span></span>  
  
 <span data-ttu-id="848cf-117">**預覽資料列**</span><span class="sxs-lookup"><span data-stu-id="848cf-117">**Preview rows**</span></span>  
 <span data-ttu-id="848cf-118">檢視一般檔案中的範例資料，根據您選取的選項將資料分為資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="848cf-118">View sample data in the flat file, divided into columns and rows according to the options you have selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="848cf-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="848cf-119">See Also</span></span>  
 <span data-ttu-id="848cf-120">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="848cf-120">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="848cf-121">[一般檔案連線管理員編輯器 &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="848cf-121">[Flat File Connection Manager Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="848cf-122">[一般檔案連接管理員編輯器 &#40;資料行] 頁面&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="848cf-122">[Flat File Connection Manager Editor &#40;Columns Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="848cf-123">一般檔案連線管理員編輯器 &#40;進階頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="848cf-123">Flat File Connection Manager Editor &#40;Advanced Page&#41;</span></span>](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)  
  
  
