---
title: 選擇工具箱項目 (維護工作頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vs.chooseitems.maintenance_tasks
- VS.ToolboxPages.Maintenance_Tasks
helpviewer_keywords:
- Customize Toolbox dialog box
ms.assetid: b92c9054-7479-45d8-a54c-c1bb6699bdb3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28c90cd0abc76a7ae721ff0580aa119c3c5639b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702282"
---
# <a name="choose-toolbox-items-maintenance-tasks-page"></a><span data-ttu-id="7bae4-102">選擇工具箱項目 (維護工作頁面)</span><span class="sxs-lookup"><span data-stu-id="7bae4-102">Choose Toolbox Items (Maintenance Tasks Page)</span></span>
  <span data-ttu-id="7bae4-103">[自訂工具箱]  對話方塊的這個索引標籤，會顯示所有已在您電腦上註冊的維護工作元件清單，而且可讓您變更工具箱中所顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="7bae4-103">This tab of the **Customize Toolbox** dialog box displays a list of all maintenancetask components registered on your computer and makes it possible for you to change the ones that are displayed in the Toolbox.</span></span> <span data-ttu-id="7bae4-104">您可以從 [工具]  功能表開啟 [自訂工具箱]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7bae4-104">You can open the **Customize Toolbox** dialog box from the **Tools** menu.</span></span> <span data-ttu-id="7bae4-105">若要排序元件的清單，請選取任何資料行標題。</span><span class="sxs-lookup"><span data-stu-id="7bae4-105">To sort the list of components, select any column heading.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7bae4-106">選項。</span><span class="sxs-lookup"><span data-stu-id="7bae4-106">Options</span></span>  
 <span data-ttu-id="7bae4-107">[維護工作]  索引標籤包含下列資料行資訊。</span><span class="sxs-lookup"><span data-stu-id="7bae4-107">The **Maintenance Tasks** tab includes the following columns of information.</span></span>  
  
 <span data-ttu-id="7bae4-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="7bae4-108">**Name**</span></span>  
 <span data-ttu-id="7bae4-109">顯示可用元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="7bae4-109">Displays the names of available components.</span></span> <span data-ttu-id="7bae4-110">每個名稱前面都有個核取方塊。</span><span class="sxs-lookup"><span data-stu-id="7bae4-110">Preceding each name is a check box.</span></span> <span data-ttu-id="7bae4-111">如果選取此選項，核取方塊就會指出 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 已經在電腦登錄中找到之元件的項目。</span><span class="sxs-lookup"><span data-stu-id="7bae4-111">If selected, a check box indicates that [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] has found an entry for the component in your computer's registry.</span></span> <span data-ttu-id="7bae4-112">元件若不是已經顯示在使用中的 [工具箱]  索引標籤，就是在按一下 [確定]  時新增。</span><span class="sxs-lookup"><span data-stu-id="7bae4-112">The component is either already displayed on the active **Toolbox** tab, or it will be added to it when you click **OK**.</span></span> <span data-ttu-id="7bae4-113">如果取消選取此選項，核取方塊就會指出元件目前並未顯示在 [工具箱]  中，或者在按一下 [確定]  時會將它從 [工具箱]  中移除。</span><span class="sxs-lookup"><span data-stu-id="7bae4-113">If cleared, a check box indicates that the component is not currently displayed in the **Toolbox**, or that it will be removed from the **Toolbox** when you click **OK**.</span></span>  
  
 <span data-ttu-id="7bae4-114">**路徑**</span><span class="sxs-lookup"><span data-stu-id="7bae4-114">**Path**</span></span>  
 <span data-ttu-id="7bae4-115">顯示元件的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="7bae4-115">Displays the full path to the component.</span></span> <span data-ttu-id="7bae4-116">若要識別隨附於產品的預設元件，請在此資料行上排序，然後尋找儲存在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 安裝路徑中的元件。</span><span class="sxs-lookup"><span data-stu-id="7bae4-116">To identify the default components that shipped with the product, sort on this column and then locate those stored on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio installation path.</span></span>  
  
 <span data-ttu-id="7bae4-117">**上次修改**</span><span class="sxs-lookup"><span data-stu-id="7bae4-117">**Last Modified**</span></span>  
 <span data-ttu-id="7bae4-118">顯示元件的上次修改日期。</span><span class="sxs-lookup"><span data-stu-id="7bae4-118">Displays the date when the component was last modified.</span></span>  
  
 <span data-ttu-id="7bae4-119">按一下名稱即可在 [語言]  與 [版本]  方塊中顯示元件的屬性，以及它的圖示。</span><span class="sxs-lookup"><span data-stu-id="7bae4-119">Click on a name to show the attributes of the component in the **Language** and **Version** boxes, along with the icon.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7bae4-120">選項。</span><span class="sxs-lookup"><span data-stu-id="7bae4-120">Options</span></span>  
 <span data-ttu-id="7bae4-121">**語言**</span><span class="sxs-lookup"><span data-stu-id="7bae4-121">**Language**</span></span>  
 <span data-ttu-id="7bae4-122">元件的語言。</span><span class="sxs-lookup"><span data-stu-id="7bae4-122">The language of the component.</span></span>  
  
 <span data-ttu-id="7bae4-123">**版本**</span><span class="sxs-lookup"><span data-stu-id="7bae4-123">**Version**</span></span>  
 <span data-ttu-id="7bae4-124">元件的版本。</span><span class="sxs-lookup"><span data-stu-id="7bae4-124">The version of the component.</span></span>  
  
  
