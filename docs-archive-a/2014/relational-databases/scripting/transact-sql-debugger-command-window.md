---
title: 命令視窗
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
author: rothja
ms.author: jroth
ms.openlocfilehash: c766ed5408de96b6a2305ce377f9031947618a7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599454"
---
# <a name="command-window"></a><span data-ttu-id="4d156-102">命令視窗</span><span class="sxs-lookup"><span data-stu-id="4d156-102">Command Window</span></span>
  <span data-ttu-id="4d156-103">使用 [命令]  視窗可針對目前所偵錯之 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] [查詢編輯器] 視窗內的程式碼執行命令，例如偵錯和編輯命令。</span><span class="sxs-lookup"><span data-stu-id="4d156-103">Use the **CommandWindow** to run commands, such as debug and edit commands, against the code in the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Query Editor window that is currently being debugged.</span></span> <span data-ttu-id="4d156-104">您必須在偵錯模式中，才能使用 [命令] 視窗  。</span><span class="sxs-lookup"><span data-stu-id="4d156-104">You must be in debug mode to use the **Command Window**.</span></span> <span data-ttu-id="4d156-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [命令]  視窗支援許多相同的命令。</span><span class="sxs-lookup"><span data-stu-id="4d156-105">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger supports many of the commands that are also supported in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Command** window.</span></span> <span data-ttu-id="4d156-106">如需詳細資訊，請參閱 [Visual Studio 命令視窗](https://go.microsoft.com/fwlink/?LinkId=112007)。</span><span class="sxs-lookup"><span data-stu-id="4d156-106">For more information, see [Visual Studio Command Window](https://go.microsoft.com/fwlink/?LinkId=112007).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="4d156-107">工作清單</span><span class="sxs-lookup"><span data-stu-id="4d156-107">Task List</span></span>  
 <span data-ttu-id="4d156-108">**存取命令視窗**</span><span class="sxs-lookup"><span data-stu-id="4d156-108">**To access the Command Window**</span></span>  
  
-   <span data-ttu-id="4d156-109">在 **[偵錯]** 功能表上，按一下 **[開始偵錯]** 。</span><span class="sxs-lookup"><span data-stu-id="4d156-109">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
 <span data-ttu-id="4d156-110">**列印變數的值**</span><span class="sxs-lookup"><span data-stu-id="4d156-110">**To print the value of a variable**</span></span>  
  
-   <span data-ttu-id="4d156-111">在**命令**中，輸入\*\*Debug. Print \<VariableName> \*\*，然後按 enter。</span><span class="sxs-lookup"><span data-stu-id="4d156-111">In the **CommandWindow**, type **Debug.Print \<VariableName>**, and then press ENTER.</span></span>  
  
 <span data-ttu-id="4d156-112">**列出有關目前執行緒的資訊**</span><span class="sxs-lookup"><span data-stu-id="4d156-112">**To list information about the current thread**</span></span>  
  
-   <span data-ttu-id="4d156-113">在**命令**中，輸入 `Debug.ListThread` ，然後按 enter。</span><span class="sxs-lookup"><span data-stu-id="4d156-113">In the **CommandWindow**, type `Debug.ListThread`, and then press ENTER.</span></span>  
  
 <span data-ttu-id="4d156-114">**將變數加入至快速監看式視窗**</span><span class="sxs-lookup"><span data-stu-id="4d156-114">**To add a variable to the QuickWatch window**</span></span>  
  
-   <span data-ttu-id="4d156-115">在**命令**中，輸入\*\*Debug. 快速 \<VariableName> \*\*監看式，然後按 enter。</span><span class="sxs-lookup"><span data-stu-id="4d156-115">In the **CommandWindow**, type **Debug.QuickWatch \<VariableName>**, and then press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d156-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d156-116">See Also</span></span>  
 [<span data-ttu-id="4d156-117">Transact-SQL 偵錯工具</span><span class="sxs-lookup"><span data-stu-id="4d156-117">Transact-SQL Debugger</span></span>](transact-sql-debugger.md)  
