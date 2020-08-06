---
title: 自訂 (命令頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.vs.customizecom.f1
ms.assetid: c8965f2c-51d9-437d-a6f3-8ac2075ede6b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 684fb9a6266fafae00b9881eb64a3642e6c98c79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702281"
---
# <a name="customize-commands-page"></a><span data-ttu-id="63122-102">自訂 (命令頁面)</span><span class="sxs-lookup"><span data-stu-id="63122-102">Customize (Commands Page)</span></span>
  <span data-ttu-id="63122-103">此對話方塊讓您能夠在工具列和功能表上加入與移除命令，以及變更用作工具列按鈕或功能表命令的影像。</span><span class="sxs-lookup"><span data-stu-id="63122-103">This dialog box enables you to add and remove commands on toolbars and menus as well as change the images used for toolbar buttons or menu commands.</span></span> <span data-ttu-id="63122-104">您可以按一下 [工具] 功能表上的 [自訂]，然後按一下 [命令] 來存取 [命令] 頁面。</span><span class="sxs-lookup"><span data-stu-id="63122-104">You can access the **Commands** page by clicking **Customize** on the **Tools** menu and then clicking **Commands**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="63122-105">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="63122-105">UI element list</span></span>  
 <span data-ttu-id="63122-106">**類別**</span><span class="sxs-lookup"><span data-stu-id="63122-106">**Categories**</span></span>  
 <span data-ttu-id="63122-107">指定要顯示在 [命令]  清單方塊中的命令集。</span><span class="sxs-lookup"><span data-stu-id="63122-107">Specifies the set of commands that are displayed in the **Commands** list box.</span></span> <span data-ttu-id="63122-108">命令的類別目錄，會依據工具和設計師所提供，且環境有支援的功能表標題而定。</span><span class="sxs-lookup"><span data-stu-id="63122-108">The categories of commands are based on menu titles provided by the tools and designers that the environment is currently supporting.</span></span> <span data-ttu-id="63122-109">此標題清單是動態的，因此類別目錄的順序和功能表標題會變更，變更會視工具與設計師以及所做的自訂作業而定。</span><span class="sxs-lookup"><span data-stu-id="63122-109">This list of titles is dynamic so that the order of categories and the menu titles change, depending on the tools and the designer, as well as any customizations made to them.</span></span> <span data-ttu-id="63122-110">所以由不同設計師所設計的兩個功能表，可能會有相同的名稱，因此同一個標題可以針對不同的命令集出現兩次。</span><span class="sxs-lookup"><span data-stu-id="63122-110">Therefore, it is possible for two menus from different designers to have the same name, so the same title can appear twice but offer different command sets.</span></span>  
  
 <span data-ttu-id="63122-111">**命令**</span><span class="sxs-lookup"><span data-stu-id="63122-111">**Commands**</span></span>  
 <span data-ttu-id="63122-112">依據您所選取的類別目錄，來顯示命令與命令的影像。</span><span class="sxs-lookup"><span data-stu-id="63122-112">Displays the commands and command images based on the category you selected.</span></span> <span data-ttu-id="63122-113">您可以將命令拖曳至想要自訂的工具列上。</span><span class="sxs-lookup"><span data-stu-id="63122-113">You can drag a command onto the toolbar you want to customize.</span></span>  
  
 <span data-ttu-id="63122-114">**修改選取項目**</span><span class="sxs-lookup"><span data-stu-id="63122-114">**Modify Selection**</span></span>  
 <span data-ttu-id="63122-115">顯示命令的清單，您可以用來自訂工具列上之按鈕的顯示。</span><span class="sxs-lookup"><span data-stu-id="63122-115">Displays a list of commands you can use to customize the display of the button on the toolbar.</span></span> <span data-ttu-id="63122-116">例如，您可以變更影像或加速鍵，以及指定是否要顯示命令的文字取代其影像。</span><span class="sxs-lookup"><span data-stu-id="63122-116">For example, you can change the image or accelerator keys, as well as specify whether to display text instead of an image for the command.</span></span> <span data-ttu-id="63122-117">您在工具列上選取了想要自訂的命令按鈕之後，此按鈕就可以使用。</span><span class="sxs-lookup"><span data-stu-id="63122-117">This button is available after you select a command button on a toolbar you want to customize.</span></span>  
  
 <span data-ttu-id="63122-118">**重新排列命令**</span><span class="sxs-lookup"><span data-stu-id="63122-118">**Rearrange Commands**</span></span>  
 <span data-ttu-id="63122-119">顯示 [重新排列命令]  對話方塊可讓您對功能表與工具列上的命令執行重新命名、重新排序、新增及移除等動作，並能變更按鈕及命令的影像。</span><span class="sxs-lookup"><span data-stu-id="63122-119">Displays the **Rearrange Commands** dialog box, which allows you to rename, reorder, add, and remove commands on menus and toolbars as well as change button and command images.</span></span>  
  
 <span data-ttu-id="63122-120">**鍵盤**</span><span class="sxs-lookup"><span data-stu-id="63122-120">**Keyboard**</span></span>  
 <span data-ttu-id="63122-121">顯示 [選項] 對話方塊的 [鍵盤] 頁面，讓您可以指定命令的快速鍵組合。</span><span class="sxs-lookup"><span data-stu-id="63122-121">Displays the **Keyboard** page of the **Options** dialog box so you can specify shortcut key combinations for commands.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63122-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63122-122">See Also</span></span>  
 [<span data-ttu-id="63122-123">自訂功能表與快速鍵</span><span class="sxs-lookup"><span data-stu-id="63122-123">Customize Menus and Shortcut Keys</span></span>](../customize-menus-and-shortcut-keys.md)  
