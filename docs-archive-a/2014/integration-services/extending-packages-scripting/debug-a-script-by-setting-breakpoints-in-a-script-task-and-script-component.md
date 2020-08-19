---
title: 在指令碼工作和指令碼元件中設定中斷點來偵錯指令碼 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- breakpoints [Integration Services]
- scripts [Integration Services], breakpoints
ms.assetid: 6c03464f-3f7d-4882-b7f8-8e396f8e2944
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 45e7ffc6680c33e3b17b9b39fba0aabd8fa4028c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593451"
---
# <a name="debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component"></a><span data-ttu-id="3b902-102">在指令碼工作和指令碼元件中設定中斷點來偵錯指令碼</span><span class="sxs-lookup"><span data-stu-id="3b902-102">Debug a Script by Setting Breakpoints in a Script Task and Script Component</span></span>
  <span data-ttu-id="3b902-103">此程序描述如何在用於指令碼工作和指令碼元件的指令碼中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="3b902-103">This procedure describes how to set breakpoints in the scripts that are used in the Script task and Script component.</span></span>  
  
 <span data-ttu-id="3b902-104">在指令碼中設定中斷點後，[設定中斷點 - \<object name>] 對話方塊會列出中斷點與內建的中斷點。</span><span class="sxs-lookup"><span data-stu-id="3b902-104">After you set breakpoints in the script, the **Set Breakpoints - \<object name>** dialog box lists the breakpoints, along with the built-in breakpoints.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3b902-105">在某些情況下，會忽略指令碼工作和指令碼元件的中斷點。</span><span class="sxs-lookup"><span data-stu-id="3b902-105">Under certain circumstances, breakpoints in the Script task and Script component are ignored.</span></span> <span data-ttu-id="3b902-106">如需詳細資訊，請參閱程式碼撰寫和偵測[腳本](../control-flow/script-task.md)工作中**的腳本工作一節**，以及 [編碼和偵測腳本元件] 中的**腳本元件**區段的偵錯工具 (。/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md.</span><span class="sxs-lookup"><span data-stu-id="3b902-106">For more information, see the **Debugging the Script Task** section in [Coding and Debugging the Script Task](../control-flow/script-task.md) and the **Debugging the Script Component** section in [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md.</span></span>  
  
### <a name="to-set-a-breakpoint-in-script"></a><span data-ttu-id="3b902-107">在指令碼中設定中斷點</span><span class="sxs-lookup"><span data-stu-id="3b902-107">To set a breakpoint in script</span></span>  
  
1.  <span data-ttu-id="3b902-108">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="3b902-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="3b902-109">按兩下內含要在其中設定中斷點之指令碼的封裝。</span><span class="sxs-lookup"><span data-stu-id="3b902-109">Double-click the package that contains the script in which you want to set breakpoints.</span></span>  
  
3.  <span data-ttu-id="3b902-110">若要開啟指令碼工作，請按一下 [控制流程]  索引標籤，然後按兩下指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="3b902-110">To open the Script task, click the **Control Flow** tab, and then double-click the Script task.</span></span>  
  
4.  <span data-ttu-id="3b902-111">若要開啟指令碼元件，請按一下 [資料流程]  索引標籤，然後按兩下指令碼元件。</span><span class="sxs-lookup"><span data-stu-id="3b902-111">To open the Script component, click the **Data Flow** tab, and then double-click the Script component.</span></span>  
  
5.  <span data-ttu-id="3b902-112">按一下 [指令碼]  ，然後按一下 [編輯指令碼]  。</span><span class="sxs-lookup"><span data-stu-id="3b902-112">Click **Script** and then click **Edit Script**.</span></span>  
  
6.  <span data-ttu-id="3b902-113">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 中，找出要在其上設定中斷點的指令碼行，以滑鼠右鍵按一下該行，並指向 [中斷點]  ，然後按一下 [插入中斷點]  。</span><span class="sxs-lookup"><span data-stu-id="3b902-113">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA), locate the line of script on which you want to set a breakpoint, right-click that line, point to **Breakpoint**, and then click **Insert Breakpoint**.</span></span>  
  
     <span data-ttu-id="3b902-114">中斷點圖示隨即出現在程式碼行上。</span><span class="sxs-lookup"><span data-stu-id="3b902-114">The breakpoint icon appears on the line of code.</span></span>  
  
7.  <span data-ttu-id="3b902-115">在 **[檔案]** 功能表上按一下 **[結束]** 。</span><span class="sxs-lookup"><span data-stu-id="3b902-115">On the **File** menu, click **Exit**.</span></span>  
  
8.  <span data-ttu-id="3b902-116">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="3b902-116">Click **OK**.</span></span>  
  
9. <span data-ttu-id="3b902-117">若要儲存封裝，請按一下 [檔案] 功能表上的 [儲存選取項目]。</span><span class="sxs-lookup"><span data-stu-id="3b902-117">To save the package, click **Save Selected Items** on the **File** menu.</span></span>  
  
  
