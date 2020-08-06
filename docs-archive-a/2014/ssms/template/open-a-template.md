---
title: 開啟範本 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- templates [Transact-SQL], opening
- opening templates
ms.assetid: 605b0f4c-5ba1-4249-ad1c-6341df77cd7a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 43b75d68fafea759e4d7873c1fb738d7964dcf57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597516"
---
# <a name="open-a-template"></a><span data-ttu-id="786d2-102">開啟範本</span><span class="sxs-lookup"><span data-stu-id="786d2-102">Open a Template</span></span>
  <span data-ttu-id="786d2-103">您可以從範本總管開啟範本。</span><span class="sxs-lookup"><span data-stu-id="786d2-103">You can open a template from Template Explorer.</span></span>  
  
## <a name="to-open-a-template-from-template-explorer"></a><span data-ttu-id="786d2-104">若要從範本總管開啟範本</span><span class="sxs-lookup"><span data-stu-id="786d2-104">To open a template from Template Explorer</span></span>  
 <span data-ttu-id="786d2-105">您可以從範本總管開啟範本。</span><span class="sxs-lookup"><span data-stu-id="786d2-105">You can open templates from the Template Explorer.</span></span>  
  
1.  <span data-ttu-id="786d2-106">若要開啟範本總管，請按一下 [檢視]  功能表中的 [範本總管]  。</span><span class="sxs-lookup"><span data-stu-id="786d2-106">To open Template Explorer, on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="786d2-107">在範本類別目錄清單中，展開包含要開啟之範本的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="786d2-107">In the list of template categories, expand the category that contains the template you want to open.</span></span>  
  
3.  <span data-ttu-id="786d2-108">有三種方法可以開啟範本：</span><span class="sxs-lookup"><span data-stu-id="786d2-108">There are three ways to open the template:</span></span>  
  
    1.  <span data-ttu-id="786d2-109">按兩下範本，在程式碼編輯器視窗中開啟。</span><span class="sxs-lookup"><span data-stu-id="786d2-109">Double-click the template to open it in a code editor window.</span></span>  
  
    2.  <span data-ttu-id="786d2-110">在範本上按一下滑鼠右鍵，然後選取 [開啟]  ，以在程式碼編輯器視窗中開啟該範本。</span><span class="sxs-lookup"><span data-stu-id="786d2-110">Right-click the template and select **Open** to open it in a code editor window.</span></span>  
  
    3.  <span data-ttu-id="786d2-111">將範本拖曳到程式碼編輯器視窗，即可將範本程式碼加入至編輯器視窗的內容。</span><span class="sxs-lookup"><span data-stu-id="786d2-111">Drag the template into a code editor window to add the template code to the contents of the editor window.</span></span>  
  
 <span data-ttu-id="786d2-112">開啟範本後，請使用 [取代範本參數]  對話方塊，將範本參數置換成您的值。</span><span class="sxs-lookup"><span data-stu-id="786d2-112">After the template is open, use the **Replace Template Parameters** dialog box to replace the template parameters with your values.</span></span>  
  
 <span data-ttu-id="786d2-113">如果開啟範本會啟動新的編輯器視窗，則開啟此視窗時，將會包含目前使用中連接的認證。</span><span class="sxs-lookup"><span data-stu-id="786d2-113">If opening a template launches a new editor window, the window will open with the credentials of the current active connection.</span></span> <span data-ttu-id="786d2-114">例如，如果當您開啟 CREATE DATABASE 範本時，您將焦點放在物件總管中的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體，將會使用該執行個體的連接開啟新的編輯器視窗。</span><span class="sxs-lookup"><span data-stu-id="786d2-114">For example, if you are focused on an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in Object Explorer when you open the CREATE DATABASE template, a new editor window will be opened using a connection to that instance.</span></span> <span data-ttu-id="786d2-115">如果沒有使用中連接， [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 將會顯示登入對話方塊。</span><span class="sxs-lookup"><span data-stu-id="786d2-115">If there is no active connection, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] will present a login dialog.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="786d2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="786d2-116">See Also</span></span>  
 <span data-ttu-id="786d2-117">[範本瀏覽器](template-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="786d2-117">[Template Explorer](template-explorer.md) </span></span>  
 [<span data-ttu-id="786d2-118">取代範本參數</span><span class="sxs-lookup"><span data-stu-id="786d2-118">Replace Template Parameters</span></span>](replace-template-parameters.md)  
  
  
