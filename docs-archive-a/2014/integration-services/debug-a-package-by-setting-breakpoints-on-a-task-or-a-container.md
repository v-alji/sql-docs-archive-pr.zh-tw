---
title: 藉由在工作或容器上設定中斷點來對封裝進行偵錯工具 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], breakpoints
- breakpoints [Integration Services]
- tasks [Integration Services], breakpoints
ms.assetid: e7fa106a-2221-403a-bb74-efc9f12bb450
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 21e334faff95e63e59bbf9c40fdf7e479de949da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592767"
---
# <a name="debug-a-package-by-setting-breakpoints-on-a-task-or-a-container"></a><span data-ttu-id="ce4ab-102">針對工作或容器設定中斷點以偵錯封裝</span><span class="sxs-lookup"><span data-stu-id="ce4ab-102">Debug a Package by Setting Breakpoints on a Task or a Container</span></span>
  <span data-ttu-id="ce4ab-103">此程序描述如何在封裝、工作、「For 迴圈」容器、「Foreach 迴圈」容器或「時序」容器中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="ce4ab-103">This procedure describes how to set breakpoints in a package, a task, a For Loop container, a Foreach Loop container, or a Sequence container.</span></span>  
  
### <a name="to-set-breakpoints-in-a-package-a-task-or-a-container"></a><span data-ttu-id="ce4ab-104">若要在封裝、工作或容器中設定中斷點</span><span class="sxs-lookup"><span data-stu-id="ce4ab-104">To set breakpoints in a package, a task, or a container</span></span>  
  
1.  <span data-ttu-id="ce4ab-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="ce4ab-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="ce4ab-106">按兩下要在其中設定中斷點的封裝。</span><span class="sxs-lookup"><span data-stu-id="ce4ab-106">Double-click the package in which you want to set breakpoints.</span></span>  
  
3.  <span data-ttu-id="ce4ab-107">在 [SSIS 設計師] 中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ce4ab-107">In SSIS Designer, do the following:</span></span>  
  
    -   <span data-ttu-id="ce4ab-108">若要在封裝物件中設定中斷點，請按一下 [控制流程]  索引標籤，並將資料指標置於設計介面背景上的任意位置，再以滑鼠右鍵按一下，然後按一下 [編輯中斷點]  。</span><span class="sxs-lookup"><span data-stu-id="ce4ab-108">To set breakpoints in the package object, click the **Control Flow** tab, place the cursor anywhere on the background of the design surface, right-click, and then click **Edit Breakpoints**.</span></span>  
  
    -   <span data-ttu-id="ce4ab-109">若要在封裝控制流程中設定中斷點，請按一下 [控制流程]  索引標籤，並以滑鼠右鍵按一下工作、「For 迴圈」容器、「Foreach 迴圈」容器或「時序」容器，然後按一下 [編輯中斷點]  。</span><span class="sxs-lookup"><span data-stu-id="ce4ab-109">To set breakpoints in a package control flow, click the **Control Flow** tab, right-click a task, a For Loop container, a Foreach Loop container, or a Sequence container, and then click **Edit Breakpoints**.</span></span>  
  
    -   <span data-ttu-id="ce4ab-110">若要在事件處理常式中設定中斷點，請按一下 [事件處理常式]  索引標籤，並以滑鼠右鍵按一下工作、「For 迴圈」容器、「Foreach 迴圈」容器或「時序」容器，然後按一下 [編輯中斷點]  。</span><span class="sxs-lookup"><span data-stu-id="ce4ab-110">To set breakpoints in an event handler, click the **Event Handler** tab, right-click a task, a For Loop container, a Foreach Loop container, or a Sequence container, and then click **Edit Breakpoints**.</span></span>  
  
4.  <span data-ttu-id="ce4ab-111">在 [設定中斷點 \<container name>] 對話方塊中，選取要啟用的中斷點。</span><span class="sxs-lookup"><span data-stu-id="ce4ab-111">In the **Set Breakpoints \<container name>** dialog box, select the breakpoints to enable.</span></span>  
  
5.  <span data-ttu-id="ce4ab-112">選擇性地修改每個中斷點的叫用計數類型和叫用計數數目。</span><span class="sxs-lookup"><span data-stu-id="ce4ab-112">Optionally, modify the hit count type and the hit count number for each breakpoint.</span></span>  
  
6.  <span data-ttu-id="ce4ab-113">若要儲存封裝，請按一下 [檔案]  功能表上的 [儲存選取項目]  。</span><span class="sxs-lookup"><span data-stu-id="ce4ab-113">To save the package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce4ab-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce4ab-114">See Also</span></span>  
 <span data-ttu-id="ce4ab-115">[疑難排解封裝開發的工具](troubleshooting/troubleshooting-tools-for-package-development.md) </span><span class="sxs-lookup"><span data-stu-id="ce4ab-115">[Troubleshooting Tools for Package Development](troubleshooting/troubleshooting-tools-for-package-development.md) </span></span>  
 <span data-ttu-id="ce4ab-116">[在腳本工作和腳本元件中設定中斷點來進行腳本的偵錯工具](data-flow/transformations/script-component.md) </span><span class="sxs-lookup"><span data-stu-id="ce4ab-116">[Debug a Script by Setting Breakpoints in a Script Task and Script Component](data-flow/transformations/script-component.md) </span></span>  
 <span data-ttu-id="ce4ab-117">[撰寫腳本工作的程式碼和進行偵錯工具](control-flow/script-task.md) </span><span class="sxs-lookup"><span data-stu-id="ce4ab-117">[Coding and Debugging the Script Task](control-flow/script-task.md) </span></span>  
 [<span data-ttu-id="ce4ab-118">編碼和偵錯指令碼元件</span><span class="sxs-lookup"><span data-stu-id="ce4ab-118">Coding and Debugging the Script Component</span></span>](extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  
