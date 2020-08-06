---
title: 建立、刪除或修改資料夾 (報表管理員) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing folders
- modifying folders
- deleting folders
- folders [Reporting Services], creating
- folders [Reporting Services], deleting
- folders [Reporting Services], modifying
ms.assetid: d62159a8-ec67-4e28-a9f1-05a9250065bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9bd7d5ceebdb7b3a48ded66ed108bddda25d8a46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597587"
---
# <a name="create-delete-or-modify-a-folder-report-manager"></a><span data-ttu-id="835ea-102">建立、刪除或修改資料夾 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="835ea-102">Create, Delete, or Modify a Folder (Report Manager)</span></span>
  <span data-ttu-id="835ea-103">您可以建立資料夾來組織與管理發行至報表伺服器的項目。</span><span class="sxs-lookup"><span data-stu-id="835ea-103">You can create folders to organize and manage the items you publish to a report server.</span></span> <span data-ttu-id="835ea-104">建立資料夾可以協助使用者尋找他們感興趣的報表。</span><span class="sxs-lookup"><span data-stu-id="835ea-104">Creating folders can help users find reports of interest to them.</span></span> <span data-ttu-id="835ea-105">對於內容管理員而言，資料夾會提供套用權限的架構。</span><span class="sxs-lookup"><span data-stu-id="835ea-105">For content managers, folders provide a framework for applying permissions.</span></span> <span data-ttu-id="835ea-106">您可以針對特定資料夾建立角色指派，以便限制在開發中或不應該廣為散發之報表的存取權。</span><span class="sxs-lookup"><span data-stu-id="835ea-106">You can create role assignments on specific folders to restrict access to reports that are in development or that should not be widely distributed.</span></span>  
  
### <a name="to-create-a-folder"></a><span data-ttu-id="835ea-107">若要建立資料夾</span><span class="sxs-lookup"><span data-stu-id="835ea-107">To create a folder</span></span>  
  
1.  <span data-ttu-id="835ea-108">啟動 [報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="835ea-108">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="835ea-109">在報表管理員中，選取主資料夾，然後按一下 [新增資料夾]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="835ea-109">In Report Manager, select the Home folder and click **New Folder**.</span></span> <span data-ttu-id="835ea-110">或者若要在現有資料夾下建立資料夾，請在 [內容]\*\*\*\* 頁面中巡覽到該資料夾，然後按一下資料夾以開啟資料夾。</span><span class="sxs-lookup"><span data-stu-id="835ea-110">Or, to create a folder under an existing folder, navigate to that folder in the **Contents** page and click the folder to open it.</span></span> <span data-ttu-id="835ea-111">接著按一下 [新增資料夾]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="835ea-111">Then click **New Folder**.</span></span>  
  
     <span data-ttu-id="835ea-112"> [新增資料夾\]\*\*\** 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="835ea-112">The **New Folder** page opens.</span></span>  
  
3.  <span data-ttu-id="835ea-113">輸入資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="835ea-113">Type a folder name.</span></span> <span data-ttu-id="835ea-114">資料夾名稱可以包含空格，但是不能包含用於 URL 編碼的保留字元：; ?</span><span class="sxs-lookup"><span data-stu-id="835ea-114">A folder name can include spaces, but cannot include reserved characters that are used for URL encoding: ; ?</span></span> <span data-ttu-id="835ea-115">： \@ & = +，$/\* \< > |。</span><span class="sxs-lookup"><span data-stu-id="835ea-115">: \@ & = + , $ / \* \< > |.</span></span> <span data-ttu-id="835ea-116">您無法一次輸入一連串的資料夾名稱來建立數個資料夾。</span><span class="sxs-lookup"><span data-stu-id="835ea-116">You cannot type a series of folder names to create several folders at once.</span></span>  
  
4.  <span data-ttu-id="835ea-117">選擇性地輸入描述。</span><span class="sxs-lookup"><span data-stu-id="835ea-117">Optionally type a description.</span></span>  
  
5.  <span data-ttu-id="835ea-118">如果您不要在 [內容]\*\*\*\* 頁面的預設檢視中顯示資料夾，請選取 [在清單檢視中隱藏]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="835ea-118">Select **Hide in list view** if you do not want to display the folder in the default view of the **Contents** page.</span></span> <span data-ttu-id="835ea-119">使用者只有在按一下 [內容]\*\*\*\* 頁面上的 [顯示詳細資料]\*\*\*\* 時，才看得到資料夾。</span><span class="sxs-lookup"><span data-stu-id="835ea-119">The folder will be visible to users only when they click **Show Details** on the **Contents** page.</span></span>  
  
6.  <span data-ttu-id="835ea-120">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="835ea-120">Click **OK**.</span></span>  
  
### <a name="to-delete-a-folder"></a><span data-ttu-id="835ea-121">若要刪除資料夾</span><span class="sxs-lookup"><span data-stu-id="835ea-121">To delete a folder</span></span>  
  
1.  <span data-ttu-id="835ea-122">在報表管理員中，巡覽到 [內容]\*\*\*\* 頁面，然後找出您要修改的項目。</span><span class="sxs-lookup"><span data-stu-id="835ea-122">In Report Manager, navigate to the **Contents** page, and locate the item that you want to modify.</span></span>  
  
2.  <span data-ttu-id="835ea-123">將滑鼠停留在該項目上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="835ea-123">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="835ea-124">在下拉式功能表中，按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="835ea-124">In the drop-down menu, click **Delete**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-modify-or-delete-a-folder"></a><span data-ttu-id="835ea-125">若要修改或刪除資料夾</span><span class="sxs-lookup"><span data-stu-id="835ea-125">To modify or delete a folder</span></span>  
  
1.  <span data-ttu-id="835ea-126">在報表管理員中，巡覽到 [內容]\*\*\*\* 頁面，然後找出您要修改的項目。</span><span class="sxs-lookup"><span data-stu-id="835ea-126">In Report Manager, navigate to the **Contents** page, and locate the item that you want to modify.</span></span>  
  
2.  <span data-ttu-id="835ea-127">將滑鼠停留在該項目上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="835ea-127">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="835ea-128">在下拉式功能表中，按一下 **[管理]**。</span><span class="sxs-lookup"><span data-stu-id="835ea-128">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="835ea-129">[一般屬性] 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="835ea-129">The General Properties page opens.</span></span>  
  
4.  <span data-ttu-id="835ea-130">若要變更資料夾位置，請按一下 [移動]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="835ea-130">To change the folder location, click **Move**.</span></span> <span data-ttu-id="835ea-131">鍵入目的資料夾的位置，或者從樹狀目錄中選擇目的資料夾，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="835ea-131">Type the location of the destination folder, or choose the destination folder from the tree, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="835ea-132">或者，利用下列方式修改資料夾屬性：</span><span class="sxs-lookup"><span data-stu-id="835ea-132">Or, modify folder properties in the following ways:</span></span>  
  
    -   <span data-ttu-id="835ea-133">若要修改有關資料夾的顯示文字，請輸入名稱或描述。</span><span class="sxs-lookup"><span data-stu-id="835ea-133">To modify display text about the folder, type a name or description.</span></span>  
  
    -   <span data-ttu-id="835ea-134">若要在 [內容]\*\*\*\* 頁面的預設檢視中顯示資料夾，請清除 [在清單檢視中隱藏]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="835ea-134">To display the folder in the default view on the **Contents** page, clear **Hide in list view**.</span></span>  
  
6.  <span data-ttu-id="835ea-135">或者，若要移除資料夾及其內容，請按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="835ea-135">Or, to remove the folder and its contents, click **Delete**.</span></span>  
  
7.  <span data-ttu-id="835ea-136">按一下 [套用]\*\*\*\* 以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="835ea-136">Click **Apply** to save changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="835ea-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="835ea-137">See Also</span></span>  
 <span data-ttu-id="835ea-138">[新增資料夾頁面 &#40;報表管理員&#41;](../new-folder-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="835ea-138">[New Folder Page &#40;Report Manager&#41;](../new-folder-page-report-manager.md) </span></span>  
 <span data-ttu-id="835ea-139">[[內容] 頁面 &#40;報表管理員&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="835ea-139">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 [<span data-ttu-id="835ea-140">尋找、檢視和管理報表 &#40;報表產生器及 SSRS &#41;</span><span class="sxs-lookup"><span data-stu-id="835ea-140">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
