---
title: 建立和管理 (SSAS 表格式) 的觀點 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.perspectivedb.f1
ms.assetid: 2a411c2b-2820-4086-ad7f-ce6a941fefc7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6d0029ff61aa05e2e83f34833c3d0af17ddb3beb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592299"
---
# <a name="create-and-manage-perspectives-ssas-tabular"></a><span data-ttu-id="497d4-102">建立及管理檢視方塊 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="497d4-102">Create and Manage Perspectives (SSAS Tabular)</span></span>
  <span data-ttu-id="497d4-103">檢視方塊會定義可檢視之模型子集，對模型提供具體的商務特有或應用程式特有視點。</span><span class="sxs-lookup"><span data-stu-id="497d4-103">Perspectives define viewable subsets of a model that provide focused, business-specific, or application-specific viewpoints of the model.</span></span> <span data-ttu-id="497d4-104">本主題中的工作會描述如何使用模型設計師中的 **[檢視方塊]** 對話方塊，建立及管理檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="497d4-104">The tasks in this topic describe how to create and manage perspectives by using the **Perspectives** dialog box in the model designer.</span></span>  
  
 <span data-ttu-id="497d4-105">本主題也包括下列工作：</span><span class="sxs-lookup"><span data-stu-id="497d4-105">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="497d4-106">若要加入觀點</span><span class="sxs-lookup"><span data-stu-id="497d4-106">To add a perspective</span></span>](#bkmk_add)  
  
-   [<span data-ttu-id="497d4-107">若要編輯檢視方塊</span><span class="sxs-lookup"><span data-stu-id="497d4-107">To edit a perspective</span></span>](#bkmk_edit)  
  
-   [<span data-ttu-id="497d4-108">重新命名檢視方塊</span><span class="sxs-lookup"><span data-stu-id="497d4-108">To rename a perspective</span></span>](#bkmk_rename)  
  
-   [<span data-ttu-id="497d4-109">刪除檢視方塊</span><span class="sxs-lookup"><span data-stu-id="497d4-109">To delete a perspective</span></span>](#bkmk_delete)  
  
-   [<span data-ttu-id="497d4-110">複製檢視方塊</span><span class="sxs-lookup"><span data-stu-id="497d4-110">To copy a perspective</span></span>](#bkmk_copy)  
  
## <a name="tasks"></a><span data-ttu-id="497d4-111">工作</span><span class="sxs-lookup"><span data-stu-id="497d4-111">Tasks</span></span>  
 <span data-ttu-id="497d4-112">若要建立檢視方塊，請使用 **[檢視方塊]** 對話方塊，即可在其中加入、編輯、刪除、複製及查看檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="497d4-112">To create perspectives, you will use the **Perspectives** dialog box, where you can add, edit, delete, copy, and view perspectives.</span></span> <span data-ttu-id="497d4-113">若要在 **中檢視** [檢視方塊] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]對話方塊，請按一下 **[模型]** 功能表，然後按一下 **[檢視方塊]**。</span><span class="sxs-lookup"><span data-stu-id="497d4-113">To view the **Perspectives** dialog box, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click on the **Model** menu, and then click **Perspectives**.</span></span>  
  
###  <a name="to-add-a-perspective"></a><a name="bkmk_add"></a> <span data-ttu-id="497d4-114">加入檢視方塊</span><span class="sxs-lookup"><span data-stu-id="497d4-114">To add a perspective</span></span>  
  
-   <span data-ttu-id="497d4-115">若要加入新檢視方塊，請按一下 **[新增檢視方塊]**。</span><span class="sxs-lookup"><span data-stu-id="497d4-115">To add a new perspective, click **New Perspective**.</span></span> <span data-ttu-id="497d4-116">即可核取或取消核取要包含的欄位物件，並提供新檢視方塊的名稱。</span><span class="sxs-lookup"><span data-stu-id="497d4-116">You can then check and uncheck field objects to be included and provide a name for the new perspective.</span></span>  
  
     <span data-ttu-id="497d4-117">如果您建立空白檢視方塊 (已取消核取所有欄位物件)，則使用此檢視方塊的使用者會看到空白的欄位清單。</span><span class="sxs-lookup"><span data-stu-id="497d4-117">If you create an empty perspective with all of the field object fields, then a user using this perspective will see an empty Field List.</span></span> <span data-ttu-id="497d4-118">檢視方塊應該至少包含一個資料表和一個資料行。</span><span class="sxs-lookup"><span data-stu-id="497d4-118">Perspectives should contain at least one table and column.</span></span>  
  
###  <a name="to-edit-a-perspective"></a><a name="bkmk_edit"></a><span data-ttu-id="497d4-119">編輯觀點</span><span class="sxs-lookup"><span data-stu-id="497d4-119">To edit a perspective</span></span>  
  
-   <span data-ttu-id="497d4-120">若要修改觀點，請檢查並取消核取觀點的資料行中的欄位，這會從觀點來加入和移除欄位物件。</span><span class="sxs-lookup"><span data-stu-id="497d4-120">To modify a perspective, check and uncheck fields in the perspective's column, which adds and removes field objects from the perspective.</span></span>  
  
###  <a name="to-rename-a-perspective"></a><a name="bkmk_rename"></a><span data-ttu-id="497d4-121">若要重新命名觀點</span><span class="sxs-lookup"><span data-stu-id="497d4-121">To rename a perspective</span></span>  
  
-   <span data-ttu-id="497d4-122">當您將滑鼠停留在觀點的資料行標頭時 () 的觀點名稱，[**重新命名**] 按鈕隨即出現。</span><span class="sxs-lookup"><span data-stu-id="497d4-122">When you hover over a perspective's column header (the name of the perspective), the **Rename** button appears.</span></span> <span data-ttu-id="497d4-123">若要重新命名檢視方塊，請按一下 **[重新命名]**，然後輸入新名稱或編輯現有名稱。</span><span class="sxs-lookup"><span data-stu-id="497d4-123">To rename the perspective, click **Rename**, and then enter a new name or edit the existing name.</span></span>  
  
###  <a name="to-delete-a-perspective"></a><a name="bkmk_delete"></a><span data-ttu-id="497d4-124">若要刪除觀點</span><span class="sxs-lookup"><span data-stu-id="497d4-124">To delete a perspective</span></span>  
  
-   <span data-ttu-id="497d4-125">當您將滑鼠停留在觀點的資料行標頭時 () 的觀點名稱，就會出現 [**刪除**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="497d4-125">When you hover over a perspective's column header (the name of the perspective), the **Delete** button appears.</span></span> <span data-ttu-id="497d4-126">若要刪除檢視方塊，請按一下 **[刪除]** 按鈕，然後在確認視窗中按一下 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="497d4-126">To delete the perspective, click the **Delete** button, and then click **Yes** in the confirmation window.</span></span>  
  
###  <a name="to-copy-a-perspective"></a><a name="bkmk_copy"></a><span data-ttu-id="497d4-127">複製觀點</span><span class="sxs-lookup"><span data-stu-id="497d4-127">To copy a perspective</span></span>  
  
-   <span data-ttu-id="497d4-128">當您將滑鼠停留在某個觀點的資料行標頭上方時，[**複製**] 按鈕隨即出現。</span><span class="sxs-lookup"><span data-stu-id="497d4-128">When you hover over a perspective's column header, the **Copy** button appears.</span></span> <span data-ttu-id="497d4-129">若要複製檢視方塊，請按一下 **[複製]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="497d4-129">To create a copy of that perspective, click the **Copy** button.</span></span> <span data-ttu-id="497d4-130">在現有檢視方塊的右邊就會加入選定檢視方塊的副本，做為新檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="497d4-130">A copy of the selected perspective is added as a new perspective to the right of existing perspectives.</span></span> <span data-ttu-id="497d4-131">新檢視方塊會繼承原本檢視方塊的名稱，並且於名稱結尾處加上 *- 複本* 註記。</span><span class="sxs-lookup"><span data-stu-id="497d4-131">The new perspective inherits the name of the copied perspective and a *- Copy* annotation is appended to the end of the name.</span></span> <span data-ttu-id="497d4-132">例如，如果建立了*銷售*觀點的副本，新的觀點就稱為「*銷售-複製*」。</span><span class="sxs-lookup"><span data-stu-id="497d4-132">For example, if a copy of the *Sales* perspective is created, the new perspective is called *Sales - Copy*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="497d4-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="497d4-133">See Also</span></span>  
 <span data-ttu-id="497d4-134">[SSAS 表格式 &#40;的觀點&#41;](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="497d4-134">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="497d4-135">階層 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="497d4-135">Hierarchies &#40;SSAS Tabular&#41;</span></span>](hierarchies-ssas-tabular.md)  
  
  
