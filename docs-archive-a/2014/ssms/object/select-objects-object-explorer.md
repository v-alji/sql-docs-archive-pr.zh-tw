---
title: 選取物件 (物件總管) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.common.selectobjects.f1
ms.assetid: 692477fe-dd7c-403d-acd2-bb108b6077f1
author: stevestein
ms.author: sstein
ms.openlocfilehash: ceec604d9fe07b339af11ed69226d41a7f616678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686735"
---
# <a name="select-objects-object-explorer"></a><span data-ttu-id="2bc93-102">選取物件 (物件總管)</span><span class="sxs-lookup"><span data-stu-id="2bc93-102">Select Objects (Object Explorer)</span></span>
  <span data-ttu-id="2bc93-103">使用 [選取物件]  對話方塊，即可將物件新增至另一個對話方塊中的清單。</span><span class="sxs-lookup"><span data-stu-id="2bc93-103">Use the **Select Objects** dialog box to add an object to a list in another dialog box.</span></span> <span data-ttu-id="2bc93-104">對話方塊中可用的對話方塊標題和選項，會視其如何開啟而定。</span><span class="sxs-lookup"><span data-stu-id="2bc93-104">The dialog box title and the options available in the dialog box depend upon how it was opened.</span></span> <span data-ttu-id="2bc93-105">只有可用的選項會出現；例如，當您選取新物件的擁有者時，只可以使用登入。</span><span class="sxs-lookup"><span data-stu-id="2bc93-105">Only available options appear; for instance, only logins are available when you are selecting an owner for a new object.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2bc93-106">選項。</span><span class="sxs-lookup"><span data-stu-id="2bc93-106">Options</span></span>  
 <span data-ttu-id="2bc93-107">**選取下列物件類型**</span><span class="sxs-lookup"><span data-stu-id="2bc93-107">**Select these object types**</span></span>  
 <span data-ttu-id="2bc93-108">顯示要選取之物件所屬類型的清單。</span><span class="sxs-lookup"><span data-stu-id="2bc93-108">Displays a list of the types of which the objects to be selected belong.</span></span> <span data-ttu-id="2bc93-109">這些類型包括 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 層級和資料庫層級的主體，以及安全性實體。</span><span class="sxs-lookup"><span data-stu-id="2bc93-109">The types include [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] level and database level principals and securables.</span></span> <span data-ttu-id="2bc93-110">這個方塊是從 [選取物件類型]  對話方塊中的選取項目擴展而來，對話方塊可以從 [物件類型]  按鈕進行存取。</span><span class="sxs-lookup"><span data-stu-id="2bc93-110">This box is populated from the selections made from the **Select Object Types** dialog box, accessed from the **Objects Type** button.</span></span>  
  
 <span data-ttu-id="2bc93-111">**輸入要選取的物件名稱**</span><span class="sxs-lookup"><span data-stu-id="2bc93-111">**Enter the object names to select**</span></span>  
 <span data-ttu-id="2bc93-112">以分號分隔，輸入要選取之物件的名稱清單。</span><span class="sxs-lookup"><span data-stu-id="2bc93-112">Enter a semicolon-separated list of names of the objects to be selected.</span></span> <span data-ttu-id="2bc93-113">要選取之物件的類型，必須是 [選取下列物件類型]  方塊中所列出的類型。</span><span class="sxs-lookup"><span data-stu-id="2bc93-113">Objects to be selected must be of a type listed in the **Select these object types** box.</span></span> <span data-ttu-id="2bc93-114">按一下 [瀏覽]  按鈕，即可從出現的清單中選取物件。</span><span class="sxs-lookup"><span data-stu-id="2bc93-114">Objects can be selected from a list accessed by clicking the **Browse** button.</span></span>  
  
 <span data-ttu-id="2bc93-115">**物件類型**</span><span class="sxs-lookup"><span data-stu-id="2bc93-115">**Object Types**</span></span>  
 <span data-ttu-id="2bc93-116">顯示物件類型的清單。</span><span class="sxs-lookup"><span data-stu-id="2bc93-116">Displays a list of object types.</span></span> <span data-ttu-id="2bc93-117">透過選取對應至類型的核取方塊，選取一或多個類型。</span><span class="sxs-lookup"><span data-stu-id="2bc93-117">Select one or more by selecting the check box corresponding to the type.</span></span>  
  
 <span data-ttu-id="2bc93-118">**檢查名稱**</span><span class="sxs-lookup"><span data-stu-id="2bc93-118">**Check Names**</span></span>  
 <span data-ttu-id="2bc93-119">驗證 [輸入要選取的物件名稱]  方塊中的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="2bc93-119">Validates the object names in the **Enter the object names to select** box.</span></span> <span data-ttu-id="2bc93-120">如果列出的物件名稱無效，會出現 [找不到名稱]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2bc93-120">If an object name that is not valid is listed, the **Name not Found** dialog box is presented.</span></span> <span data-ttu-id="2bc93-121">使用這個對話方塊，即可從要選取的物件清單中更正或移除名稱。</span><span class="sxs-lookup"><span data-stu-id="2bc93-121">With this dialog box, the name can be corrected or removed from the list of objects to select.</span></span>  
  
 <span data-ttu-id="2bc93-122">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="2bc93-122">**Browse**</span></span>  
 <span data-ttu-id="2bc93-123">會呈現 [瀏覽物件]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2bc93-123">Presents the **Browse for Objects** dialog box.</span></span> <span data-ttu-id="2bc93-124">這包含列示在 [選取下列物件類型]  方塊中之類型的物件清單。</span><span class="sxs-lookup"><span data-stu-id="2bc93-124">This contains a list of objects of the types listed in the **Select These Object Types** box.</span></span> <span data-ttu-id="2bc93-125">透過選取對應的核取方塊，即可從這份清單中選取物件。</span><span class="sxs-lookup"><span data-stu-id="2bc93-125">Select objects from this list by selecting the corresponding check boxes.</span></span>  
  
  
