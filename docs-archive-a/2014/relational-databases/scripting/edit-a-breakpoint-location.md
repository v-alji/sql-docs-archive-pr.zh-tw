---
title: 編輯中斷點位置
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint location
ms.assetid: 5c28e411-0377-4210-a7ce-2a5c13dcdf74
author: rothja
ms.author: jroth
ms.openlocfilehash: 919e62d53d5c9e8898bf1d49c4b5e5aa4c0ed107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584360"
---
# <a name="edit-a-breakpoint-location"></a><span data-ttu-id="2d24f-102">編輯中斷點位置</span><span class="sxs-lookup"><span data-stu-id="2d24f-102">Edit a Breakpoint Location</span></span>
  <span data-ttu-id="2d24f-103">中斷點位置會指定中斷點位於 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼檔案中的行和字元。</span><span class="sxs-lookup"><span data-stu-id="2d24f-103">The breakpoint location specifies the line and character where the breakpoint resides in a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file.</span></span> <span data-ttu-id="2d24f-104">您可以編輯中斷點位址，將中斷點移至指令碼中的另一個位置，或移至不同的指令碼。</span><span class="sxs-lookup"><span data-stu-id="2d24f-104">You can edit the breakpoint location to move the breakpoint to another location in the script, or to a different script.</span></span>  
  
## <a name="editing-a-location"></a><span data-ttu-id="2d24f-105">編輯位置</span><span class="sxs-lookup"><span data-stu-id="2d24f-105">Editing a Location</span></span>  
 <span data-ttu-id="2d24f-106">當您編輯中斷點位置時，中斷點就會移至新的位置，並且帶有所有現有的屬性，例如叫用計數或條件。</span><span class="sxs-lookup"><span data-stu-id="2d24f-106">When you edit a breakpoint location, the breakpoint moves to the new location, carrying with it all of the existing properties, such as a hit count or condition.</span></span>  
  
#### <a name="to-edit-a-breakpoint-location"></a><span data-ttu-id="2d24f-107">若要編輯中斷點位置</span><span class="sxs-lookup"><span data-stu-id="2d24f-107">To Edit a Breakpoint Location</span></span>  
  
1.  <span data-ttu-id="2d24f-108">在編輯器視窗中，以滑鼠右鍵按一下中斷點圖像，然後按一下快速鍵功能表上的 [位置]  。</span><span class="sxs-lookup"><span data-stu-id="2d24f-108">In the editor window, right-click the breakpoint glyph, and then click **Location** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="2d24f-109">-或-</span><span class="sxs-lookup"><span data-stu-id="2d24f-109">-or-</span></span>  
  
     <span data-ttu-id="2d24f-110">在 [中斷點]  視窗中，以滑鼠右鍵按一下中斷點圖像，然後按一下快速鍵功能表上的 [位置]  。</span><span class="sxs-lookup"><span data-stu-id="2d24f-110">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Location** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="2d24f-111">在 [檔案中斷點]  對話方塊中，編輯 [檔案]  以指定新的檔案、編輯 [行]  以指定新的行，或編輯 [字元]  以指定該行中的新位置。</span><span class="sxs-lookup"><span data-stu-id="2d24f-111">In the **File Breakpoint** dialog box, edit **File** to specify a new file, **Line** to specify a new line, or **Character** to specify a new location within the line.</span></span> <span data-ttu-id="2d24f-112">如果您所指定的新檔案已經開啟在 [查詢編輯器] 視窗中，中斷點就會移至該編輯器視窗。</span><span class="sxs-lookup"><span data-stu-id="2d24f-112">If the new file you specify is already open in a query editor window, the breakpoint is moved to that editor window.</span></span> <span data-ttu-id="2d24f-113">如果該檔案尚未開啟，系統就會開啟新的編輯器視窗、載入該檔案，而且中斷點會移至新的位置。</span><span class="sxs-lookup"><span data-stu-id="2d24f-113">If the file is not opened, a new editor window is opened, the file is loaded in, and the breakpoint moved to the new location.</span></span>  
  
     <span data-ttu-id="2d24f-114">偵錯 [!INCLUDE[tsql](../../includes/tsql-md.md)] 時，[允許原始程式碼與原始版本不同] 選項沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="2d24f-114">The **Allow the source code to be different from the original version** option has no effect when debugging [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d24f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d24f-115">See Also</span></span>  
 <span data-ttu-id="2d24f-116">[指定叫用計數](specify-a-hit-count.md) </span><span class="sxs-lookup"><span data-stu-id="2d24f-116">[Specify a Hit Count](specify-a-hit-count.md) </span></span>  
 <span data-ttu-id="2d24f-117">[指定中斷點動作](specify-a-breakpoint-action.md) </span><span class="sxs-lookup"><span data-stu-id="2d24f-117">[Specify a Breakpoint Action](specify-a-breakpoint-action.md) </span></span>  
 <span data-ttu-id="2d24f-118">[指定中斷點條件](specify-a-breakpoint-condition.md) </span><span class="sxs-lookup"><span data-stu-id="2d24f-118">[Specify a Breakpoint Condition](specify-a-breakpoint-condition.md) </span></span>  
 [<span data-ttu-id="2d24f-119">指定中斷點篩選條件</span><span class="sxs-lookup"><span data-stu-id="2d24f-119">Specify a Breakpoint Filter</span></span>](specify-a-breakpoint-filter.md)  
