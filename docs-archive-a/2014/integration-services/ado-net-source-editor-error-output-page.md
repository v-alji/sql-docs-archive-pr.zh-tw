---
title: ADO NET 來源編輯器 (錯誤輸出頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.erroroutput.f1
ms.assetid: 4dd9d129-a95c-4d3a-bbbf-e84a39089950
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9ee480caa8764d70b52b25a416f200f353d30c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707746"
---
# <a name="ado-net-source-editor-error-output-page"></a><span data-ttu-id="62b85-102">ADO NET 來源編輯器 (錯誤輸出頁面)</span><span class="sxs-lookup"><span data-stu-id="62b85-102">ADO NET Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="62b85-103">使用 [ADO NET 來源編輯器]  對話方塊的 [錯誤輸出]  頁面，即可選取錯誤處理選項，並設定錯誤輸出資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="62b85-103">Use the **Error Output** page of the **ADO NET Source Editor** dialog box to select error handling options and to set properties on error output columns.</span></span>  
  
 <span data-ttu-id="62b85-104">若要深入了解 ADO NET 來源，請參閱＜ [ADO NET Source](data-flow/ado-net-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="62b85-104">To learn more about the ADO NET source, see [ADO NET Source](data-flow/ado-net-source.md).</span></span>  
  
 <span data-ttu-id="62b85-105">**開啟錯誤輸出頁面**</span><span class="sxs-lookup"><span data-stu-id="62b85-105">**To open the Error Output page**</span></span>  
  
1.  <span data-ttu-id="62b85-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟具有 ADO NET 來源的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="62b85-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET source.</span></span>  
  
2.  <span data-ttu-id="62b85-107">在 [資料流程]  索引標籤上，按兩下 ADO NET 來源。</span><span class="sxs-lookup"><span data-stu-id="62b85-107">On the **Data Flow** tab, double-click the ADO NET source.</span></span>  
  
3.  <span data-ttu-id="62b85-108">在 [ADO NET 來源編輯器]  中，按一下 [錯誤輸出]  。</span><span class="sxs-lookup"><span data-stu-id="62b85-108">In the **ADO NET Source Editor**, click **Error Output**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="62b85-109">選項。</span><span class="sxs-lookup"><span data-stu-id="62b85-109">Options</span></span>  
 <span data-ttu-id="62b85-110">**輸入/輸出**</span><span class="sxs-lookup"><span data-stu-id="62b85-110">**Input/Output**</span></span>  
 <span data-ttu-id="62b85-111">檢視資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="62b85-111">View the name of the data source.</span></span>  
  
 <span data-ttu-id="62b85-112">**資料行**</span><span class="sxs-lookup"><span data-stu-id="62b85-112">**Column**</span></span>  
 <span data-ttu-id="62b85-113">檢視您在 [ADO NET 來源編輯器]  對話方塊之 [連接管理員]  頁面上所選取的外部 (來源) 資料行。</span><span class="sxs-lookup"><span data-stu-id="62b85-113">View the external (source) columns that you selected on the **Connection Manager** page of the **ADO NET Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="62b85-114">**錯誤**</span><span class="sxs-lookup"><span data-stu-id="62b85-114">**Error**</span></span>  
 <span data-ttu-id="62b85-115">指定錯誤發生時要採取的動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="62b85-115">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="62b85-116">**相關主題：** [資料中的錯誤處理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="62b85-116">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="62b85-117">**截斷**</span><span class="sxs-lookup"><span data-stu-id="62b85-117">**Truncation**</span></span>  
 <span data-ttu-id="62b85-118">指定截斷發生時要採取的動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="62b85-118">Specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="62b85-119">**說明**</span><span class="sxs-lookup"><span data-stu-id="62b85-119">**Description**</span></span>  
 <span data-ttu-id="62b85-120">檢視錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="62b85-120">View the description of the error.</span></span>  
  
 <span data-ttu-id="62b85-121">**將這個值設定到選取的資料格**</span><span class="sxs-lookup"><span data-stu-id="62b85-121">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="62b85-122">指定發生錯誤或截斷時要對所有選取之資料格採取的動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="62b85-122">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="62b85-123">**套用**</span><span class="sxs-lookup"><span data-stu-id="62b85-123">**Apply**</span></span>  
 <span data-ttu-id="62b85-124">將錯誤處理選項套用至選取的資料格。</span><span class="sxs-lookup"><span data-stu-id="62b85-124">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62b85-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62b85-125">See Also</span></span>  
 <span data-ttu-id="62b85-126">[ADO NET 來源編輯器 &#40;連線管理員頁面&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="62b85-126">[ADO NET Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="62b85-127">[ADO NET 來源編輯器 &#40;資料行] 頁面&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="62b85-127">[ADO NET Source Editor &#40;Columns Page&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="62b85-128">ADO.NET 連線管理員</span><span class="sxs-lookup"><span data-stu-id="62b85-128">ADO.NET Connection Manager</span></span>](connection-manager/ado-net-connection-manager.md)  
  
  
