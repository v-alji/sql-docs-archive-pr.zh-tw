---
title: 變數方格選項 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.variableoptionswindow.f1
helpviewer_keywords:
- Choose Variable Columns dialog box
ms.assetid: 7cccc230-3b20-4074-804f-3448d9616a83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b90e1a3c69e4eaf1f123603e0082ecb1eda4e893
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592739"
---
# <a name="variable-grid-options"></a><span data-ttu-id="e5c84-102">變數方格選項</span><span class="sxs-lookup"><span data-stu-id="e5c84-102">Variable Grid Options</span></span>
  <span data-ttu-id="e5c84-103">使用 **[變數方格選項]** 對話方塊選擇將顯示在 **[變數]** 視窗中的資料行，並選取要套用到此變數清單的篩選。</span><span class="sxs-lookup"><span data-stu-id="e5c84-103">Use the **Variable Grid Options** dialog box to select the columns that will display in the **Variables** window and to select the filters to apply to the list of variables.</span></span> <span data-ttu-id="e5c84-104">如需所對應之變數屬性的詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="e5c84-104">For more information about the corresponding variable properties, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
## <a name="options-for-filter"></a><span data-ttu-id="e5c84-105">篩選選項</span><span class="sxs-lookup"><span data-stu-id="e5c84-105">Options for Filter</span></span>  
 <span data-ttu-id="e5c84-106">**顯示系統變數**</span><span class="sxs-lookup"><span data-stu-id="e5c84-106">**Show system variables**</span></span>  
 <span data-ttu-id="e5c84-107">選取此選項即可在 [變數]\*\*\*\* 視窗中列出系統變數。</span><span class="sxs-lookup"><span data-stu-id="e5c84-107">Select to list system variables in the **Variables** window.</span></span> <span data-ttu-id="e5c84-108">系統變數是預先定義的，</span><span class="sxs-lookup"><span data-stu-id="e5c84-108">System variables are predefined.</span></span> <span data-ttu-id="e5c84-109">您無法加入或刪除系統變數。</span><span class="sxs-lookup"><span data-stu-id="e5c84-109">You cannot add or delete system variables.</span></span> <span data-ttu-id="e5c84-110">但您可以修改 **RaiseChangedEvent** 屬性設定。</span><span class="sxs-lookup"><span data-stu-id="e5c84-110">You can modify the **RaiseChangedEvent** property setting.</span></span>  
  
 <span data-ttu-id="e5c84-111">此清單有色碼。</span><span class="sxs-lookup"><span data-stu-id="e5c84-111">This list is color coded.</span></span> <span data-ttu-id="e5c84-112">系統變數是灰色，而使用者定義的變數是黑色。</span><span class="sxs-lookup"><span data-stu-id="e5c84-112">System variables are gray, and user-defined variables are black.</span></span>  
  
 <span data-ttu-id="e5c84-113">**顯示所有範圍的變數**</span><span class="sxs-lookup"><span data-stu-id="e5c84-113">**Show variables of all scopes**</span></span>  
 <span data-ttu-id="e5c84-114">選取此選項即可顯示封裝範圍內、和封裝中的容器、工作及事件處理常式範圍內的變數。</span><span class="sxs-lookup"><span data-stu-id="e5c84-114">Select to show variables within the scope the package, and within the scope of containers, tasks, and event handlers in the package.</span></span> <span data-ttu-id="e5c84-115">清除此選項則只會顯示封裝範圍內以及所選取之容器、工作或事件處理常式範圍內的變數。</span><span class="sxs-lookup"><span data-stu-id="e5c84-115">Clear this option to show only variables within the scope of the package and within the scope of a selected container, task, or event handler.</span></span>  
  
 <span data-ttu-id="e5c84-116">如需變數範圍的詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="e5c84-116">For more information about variable scope, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
## <a name="options-for-columns"></a><span data-ttu-id="e5c84-117">資料行選項</span><span class="sxs-lookup"><span data-stu-id="e5c84-117">Options for Columns</span></span>  
 <span data-ttu-id="e5c84-118">選取您想要在 **[變數]** 視窗中顯示的資料行。</span><span class="sxs-lookup"><span data-stu-id="e5c84-118">Select the columns that you want to appear in the **Variables** window.</span></span>  
  
-   <span data-ttu-id="e5c84-119">**範圍**</span><span class="sxs-lookup"><span data-stu-id="e5c84-119">**Scope**</span></span>  
  
-   <span data-ttu-id="e5c84-120">**Data type**</span><span class="sxs-lookup"><span data-stu-id="e5c84-120">**Data type**</span></span>  
  
-   <span data-ttu-id="e5c84-121">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="e5c84-121">**Value**</span></span>  
  
-   <span data-ttu-id="e5c84-122">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="e5c84-122">**Namespace**</span></span>  
  
-   <span data-ttu-id="e5c84-123">**變數值變更時引發事件**</span><span class="sxs-lookup"><span data-stu-id="e5c84-123">**Raise event when variable value changes**</span></span>  
  
-   <span data-ttu-id="e5c84-124">**說明**</span><span class="sxs-lookup"><span data-stu-id="e5c84-124">**Description**</span></span>  
  
-   <span data-ttu-id="e5c84-125">**運算式**</span><span class="sxs-lookup"><span data-stu-id="e5c84-125">**Expression**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5c84-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5c84-126">See Also</span></span>  
 <span data-ttu-id="e5c84-127">[變數視窗](../../2014/integration-services/variables-window.md) </span><span class="sxs-lookup"><span data-stu-id="e5c84-127">[Variables Window](../../2014/integration-services/variables-window.md) </span></span>  
 <span data-ttu-id="e5c84-128">[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="e5c84-128">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="e5c84-129">[在封裝中使用變數](../../2014/integration-services/use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="e5c84-129">[Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md) </span></span>  
 [<span data-ttu-id="e5c84-130">Integration Services &#40;SSIS&#41; 事件處理常式</span><span class="sxs-lookup"><span data-stu-id="e5c84-130">Integration Services &#40;SSIS&#41; Event Handlers</span></span>](integration-services-ssis-event-handlers.md)  
  
  
