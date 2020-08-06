---
title: 切換中斷點
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c477ab89-a1cd-4f2c-aa7c-40525041100f
author: rothja
ms.author: jroth
ms.openlocfilehash: 72e26e9b1d04bc2eced6bcb6d93d3c86a016d308
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598799"
---
# <a name="toggle-a-breakpoint"></a><span data-ttu-id="4de2b-102">切換中斷點</span><span class="sxs-lookup"><span data-stu-id="4de2b-102">Toggle a Breakpoint</span></span>
  <span data-ttu-id="4de2b-103">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式上設定中斷點的動作稱為切換中斷點。</span><span class="sxs-lookup"><span data-stu-id="4de2b-103">The act of setting a breakpoint on a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is called toggling a breakpoint.</span></span>  
  
## <a name="breakpoints"></a><span data-ttu-id="4de2b-104">中斷點</span><span class="sxs-lookup"><span data-stu-id="4de2b-104">Breakpoints</span></span>  
 <span data-ttu-id="4de2b-105">一旦設定中斷點，就會以陳述式左邊灰色列中的圖示來表示它。</span><span class="sxs-lookup"><span data-stu-id="4de2b-105">Once the breakpoint has been set, it is represented by an icon in the grey bar to the left of the statement.</span></span> <span data-ttu-id="4de2b-106">此圖示稱為中斷點圖像。</span><span class="sxs-lookup"><span data-stu-id="4de2b-106">The icon is called a breakpoint glyph.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="4de2b-107">中斷點會套用至完整的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="4de2b-107">breakpoints are applied to a complete [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="4de2b-108">當中斷點切換為開時，偵錯工具會反白顯示關聯的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="4de2b-108">When a breakpoint is toggled on, the debugger highlights the associated [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
 <span data-ttu-id="4de2b-109">如果在一行中有多個 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，您可以切換每個陳述式的中斷點。</span><span class="sxs-lookup"><span data-stu-id="4de2b-109">If there are multiple [!INCLUDE[tsql](../../includes/tsql-md.md)] statements on a line, you can toggle a breakpoint for each statement.</span></span> <span data-ttu-id="4de2b-110">如果按一下視窗左邊灰色列，會切換行中第一個陳述式的中斷點。</span><span class="sxs-lookup"><span data-stu-id="4de2b-110">Clicking in the grey bar on the left of the window toggles a breakpoint on the first statement on the line.</span></span> <span data-ttu-id="4de2b-111">藉由反白顯示陳述式的任何部分或將游標移至陳述式，然後按下 F9 或按一下 [偵錯] 功能表上的 [切換中斷點]，可切換後續陳述式的中斷點。</span><span class="sxs-lookup"><span data-stu-id="4de2b-111">You can toggle a breakpoint in a subsequent statement by highlighting any part of the statement, or moving the cursor into the statement, and then either pressing F9 or clicking **Toggle Breakpoint** on the **Debug** menu.</span></span> <span data-ttu-id="4de2b-112">如果在一行中有多個中斷點，左邊灰色列中只有一個中斷點圖像。</span><span class="sxs-lookup"><span data-stu-id="4de2b-112">If you have multiple breakpoints on a line, there is only one breakpoint glyph in the grey bar on the left.</span></span>  
  
 <span data-ttu-id="4de2b-113">切換中斷點之後，您可以針對中斷點執行各種動作，例如編輯其屬性或暫時予以停用。</span><span class="sxs-lookup"><span data-stu-id="4de2b-113">After a breakpoint has been toggled, you can perform various actions on the breakpoint, such as editing its properties or temporarily disabling it.</span></span> <span data-ttu-id="4de2b-114">如需詳細資訊，請參閱 [Transact-SQL 中斷點](transact-sql-breakpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="4de2b-114">For more information, see [Transact-SQL Breakpoints](transact-sql-breakpoints.md).</span></span>  
  
## <a name="toggle-a-breakpoint"></a><span data-ttu-id="4de2b-115">切換中斷點</span><span class="sxs-lookup"><span data-stu-id="4de2b-115">Toggle a Breakpoint</span></span>  
 <span data-ttu-id="4de2b-116">**切換 Transact-SQL 陳述式上的中斷點**</span><span class="sxs-lookup"><span data-stu-id="4de2b-116">**To toggle a breakpoint on a Transact-SQL statement**</span></span>  
  
1.  <span data-ttu-id="4de2b-117">按一下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式左邊的灰色列。</span><span class="sxs-lookup"><span data-stu-id="4de2b-117">Click the gray bar to the left side of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
2.  <span data-ttu-id="4de2b-118">或是反白顯示陳述式的任何部分或將游標移至陳述式，然後執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="4de2b-118">Alternatively, either highlight any part of the statement or move the cursor to the statement, and then perform either action:</span></span>  
  
    -   <span data-ttu-id="4de2b-119">按 F9 鍵。</span><span class="sxs-lookup"><span data-stu-id="4de2b-119">Press F9.</span></span>  
  
    -   <span data-ttu-id="4de2b-120">在 [偵錯]  功能表上，按一下 [切換中斷點]  。</span><span class="sxs-lookup"><span data-stu-id="4de2b-120">On the **Debug** menu, click **Toggle Breakpoint**.</span></span>  
  
  
