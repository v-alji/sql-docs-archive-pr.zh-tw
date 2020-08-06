---
title: ADO NET 來源編輯器 (資料行] 頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.columns.f1
ms.assetid: fbc205b9-2001-4737-a76b-1ba777344bd9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d89f8c926761b9149f19269bc2519c12bcf130e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596236"
---
# <a name="ado-net-source-editor-columns-page"></a><span data-ttu-id="f834d-102">ADO NET 來源編輯器 (資料行頁面)</span><span class="sxs-lookup"><span data-stu-id="f834d-102">ADO NET Source Editor (Columns Page)</span></span>
  <span data-ttu-id="f834d-103">使用 [ADO NET 來源編輯器]  對話方塊的 [資料行]  頁面，即可將輸出資料行對應至每個外部 (來源) 資料行。</span><span class="sxs-lookup"><span data-stu-id="f834d-103">Use the **Columns** page of the **ADO NET Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="f834d-104">若要深入了解 ADO NET 來源，請參閱＜ [ADO NET Source](data-flow/ado-net-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="f834d-104">To learn more about the ADO NET source, see [ADO NET Source](data-flow/ado-net-source.md).</span></span>  
  
 <span data-ttu-id="f834d-105">**開啟資料行頁面**</span><span class="sxs-lookup"><span data-stu-id="f834d-105">**To open the Columns page**</span></span>  
  
1.  <span data-ttu-id="f834d-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟具有 ADO NET 來源的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="f834d-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET source.</span></span>  
  
2.  <span data-ttu-id="f834d-107">在 [資料流程]  索引標籤上，按兩下 ADO NET 來源。</span><span class="sxs-lookup"><span data-stu-id="f834d-107">On the **Data Flow** tab, double-click the ADO NET source.</span></span>  
  
3.  <span data-ttu-id="f834d-108">在 **[ADO NET 來源編輯器]** 中，按一下 **[資料行]** 。</span><span class="sxs-lookup"><span data-stu-id="f834d-108">In the **ADO NET Source Editor**, click **Columns**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f834d-109">選項。</span><span class="sxs-lookup"><span data-stu-id="f834d-109">Options</span></span>  
 <span data-ttu-id="f834d-110">**可用的外部資料行**</span><span class="sxs-lookup"><span data-stu-id="f834d-110">**Available External Columns**</span></span>  
 <span data-ttu-id="f834d-111">在資料來源中檢視可用的外部資料行清單。</span><span class="sxs-lookup"><span data-stu-id="f834d-111">View the list of available external columns in the data source.</span></span> <span data-ttu-id="f834d-112">您無法使用此資料表來加入或刪除資料行。</span><span class="sxs-lookup"><span data-stu-id="f834d-112">You cannot use this table to add or delete columns.</span></span>  
  
 <span data-ttu-id="f834d-113">**[外部資料行]**</span><span class="sxs-lookup"><span data-stu-id="f834d-113">**External Column**</span></span>  
 <span data-ttu-id="f834d-114">依您在設定使用此來源之資料的元件時所見的順序來檢視外部 (來源) 資料行。</span><span class="sxs-lookup"><span data-stu-id="f834d-114">View external (source) columns in the order in which you will see them when configuring components that consume data from this source.</span></span>  
  
 <span data-ttu-id="f834d-115">**輸出資料行**</span><span class="sxs-lookup"><span data-stu-id="f834d-115">**Output Column**</span></span>  
 <span data-ttu-id="f834d-116">為每個輸出資料行提供唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="f834d-116">Provide a unique name for each output column.</span></span> <span data-ttu-id="f834d-117">預設值為選取的外部 (來源) 資料行的名稱；不過，您也可以選擇任何唯一的、描述性的名稱。</span><span class="sxs-lookup"><span data-stu-id="f834d-117">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="f834d-118">提供的名稱將顯示在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師內。</span><span class="sxs-lookup"><span data-stu-id="f834d-118">The name provided will be displayed within the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f834d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f834d-119">See Also</span></span>  
 <span data-ttu-id="f834d-120">[ADO NET 來源編輯器 &#40;連線管理員頁面&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="f834d-120">[ADO NET Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="f834d-121">[ADO NET 來源編輯器 &#40;錯誤輸出頁面&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="f834d-121">[ADO NET Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="f834d-122">ADO.NET 連線管理員</span><span class="sxs-lookup"><span data-stu-id="f834d-122">ADO.NET Connection Manager</span></span>](connection-manager/ado-net-connection-manager.md)  
  
  
