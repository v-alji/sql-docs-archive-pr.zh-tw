---
title: 偵錯指令碼 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Script task [Integration Services], debugging
- debugging [Integration Services], scripts
- scripts [Integration Services], debugging
ms.assetid: fddf57d8-8607-4f88-85a0-1b683087b491
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a7926f806f20f76c7aaac0c22b970addc5e93a78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705246"
---
# <a name="debugging-script"></a><span data-ttu-id="c43e3-102">偵錯指令碼</span><span class="sxs-lookup"><span data-stu-id="c43e3-102">Debugging Script</span></span>
  <span data-ttu-id="c43e3-103">您可以撰寫指令碼工作和指令碼元件在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 中使用的指令碼。</span><span class="sxs-lookup"><span data-stu-id="c43e3-103">You write the scripts that the Script task and Script component use, in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span>  
  
 <span data-ttu-id="c43e3-104">您可以在 VSTA 中設定中斷點和編寫中斷點指令碼。</span><span class="sxs-lookup"><span data-stu-id="c43e3-104">You set and script breakpoints in VSTA.</span></span> <span data-ttu-id="c43e3-105">您可以在 VSTA 中管理中斷點，但您也可以使用「[!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」提供的 [設定中斷點] 對話方塊管理中斷點。</span><span class="sxs-lookup"><span data-stu-id="c43e3-105">You can manage breakpoints in VSTA, but you can also manage the breakpoints using the **Set Breakpoints** dialog box that [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides.</span></span> <span data-ttu-id="c43e3-106">如需詳細資訊，請參閱 [偵錯控制流程](debugging-control-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="c43e3-106">For more information, see [Debugging Control Flow](debugging-control-flow.md).</span></span>  
  
 <span data-ttu-id="c43e3-107">[設定中斷點]  對話方塊包含指令碼中斷點。</span><span class="sxs-lookup"><span data-stu-id="c43e3-107">The **Set Breakpoints** dialog box includes the script breakpoints.</span></span> <span data-ttu-id="c43e3-108">這些中斷點出現在中斷點清單的底部，並顯示中斷點所在之函數的行號和名稱。</span><span class="sxs-lookup"><span data-stu-id="c43e3-108">These breakpoints appear at the bottom of the breakpoint list, and display the line number and the name of the function in which the breakpoint appears.</span></span> <span data-ttu-id="c43e3-109">您可以從 [設定中斷點]  對話方塊刪除指令碼中斷點。</span><span class="sxs-lookup"><span data-stu-id="c43e3-109">You can delete a script breakpoint from the **Set Breakpoints** dialog box.</span></span>  
  
 <span data-ttu-id="c43e3-110">在執行階段，於指令碼中程式碼行上設定的中斷點會與封裝上或封裝的工作和容器上設定的中斷點整合。</span><span class="sxs-lookup"><span data-stu-id="c43e3-110">At run time, the breakpoints set on lines of code in script are integrated with the breakpoints set on the package or the tasks and containers in the package.</span></span> <span data-ttu-id="c43e3-111">偵錯工具可以從指令碼中的中斷點執行到封裝、工作或容器上設定的中斷點，反之亦可。</span><span class="sxs-lookup"><span data-stu-id="c43e3-111">The debugger can run from a breakpoint in the script to a breakpoint set on the package, task, or container, and vice versa.</span></span> <span data-ttu-id="c43e3-112">例如，封裝可能具有以封裝接收到 **OnPreExecute** 和 **OnPostExecute** 事件時發生之中斷條件設定的中斷點，而且封裝還可擁有在其指令碼行上具有中斷點的指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="c43e3-112">For example, a package might have breakpoints set on the break conditions that occur when the package receives the **OnPreExecute** and **OnPostExecute** events, and also have a Script task that has breakpoints on lines of its script.</span></span> <span data-ttu-id="c43e3-113">在此案例中，封裝可以暫停與 **OnPreExecute** 事件相關之中斷條件的執行，而執行到指令碼中的中斷點，並最終執行到與 **OnPostExecute** 事件相關的中斷條件。</span><span class="sxs-lookup"><span data-stu-id="c43e3-113">In this scenario, the package can suspend execution on the break condition associated with the **OnPreExecute** event, run to the breakpoints in the script, and finally run to the break condition associated with the **OnPostExecute** event.</span></span>  
  
 <span data-ttu-id="c43e3-114">如需偵錯指令碼工作和指令碼元件的詳細資訊，請參閱 [指令碼工作的程式碼撰寫和偵錯](../extending-packages-scripting/task/coding-and-debugging-the-script-task.md) 和 [指令碼元件的程式碼撰寫和偵錯](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="c43e3-114">For more information about debugging the Script task and Script component, see [Coding and Debugging the Script Task](../extending-packages-scripting/task/coding-and-debugging-the-script-task.md) and [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).</span></span>  
  
### <a name="to-set-a-breakpoint-in-visual-studio-for-applications"></a><span data-ttu-id="c43e3-115">在 Visual Studio for Applications 中設定中斷點</span><span class="sxs-lookup"><span data-stu-id="c43e3-115">To set a breakpoint in Visual Studio for Applications</span></span>  
  
-   [<span data-ttu-id="c43e3-116">在指令碼工作和指令碼元件中設定中斷點來對指令碼偵錯</span><span class="sxs-lookup"><span data-stu-id="c43e3-116">Debug a Script by Setting Breakpoints in a Script Task and Script Component</span></span>](../extending-packages-scripting/debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component.md)  
  
## <a name="see-also"></a><span data-ttu-id="c43e3-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c43e3-117">See Also</span></span>  
 [<span data-ttu-id="c43e3-118">套件開發的疑難排解工具</span><span class="sxs-lookup"><span data-stu-id="c43e3-118">Troubleshooting Tools for Package Development</span></span>](troubleshooting-tools-for-package-development.md)  
  
  
