---
title: 模型專案安全性頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.modelproperties.modelitemsecurity.f1
ms.assetid: 8c5b29ae-1f17-41f2-ab59-97899b8fb4fc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 928572437990c7f7fe1117c086c65c939aa9c999
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585127"
---
# <a name="model-item-security-page-report-manager"></a><span data-ttu-id="dd5ae-102">模型項目安全性頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="dd5ae-102">Model Item Security Page (Report Manager)</span></span>
  <span data-ttu-id="dd5ae-103">您可以使用這個頁面，透過授與或撤銷特定項目的唯讀權限，保護模型的各部分。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-103">Use this page to secure parts of a model by granting or revoking read-only permissions on particular items.</span></span> <span data-ttu-id="dd5ae-104">模型項目安全性會影響執行階段的特定資料瀏覽，以及在報表產生器中建立報表時使用已發行模型之各部分的能力。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-104">Model item security affects ad hoc data exploration at run time and the ability to use parts of a published model when creating reports in Report Builder.</span></span> <span data-ttu-id="dd5ae-105">若要使用這項功能，您必須擁有「內容管理員」權限。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-105">To use this feature, you must have Content Manager permissions.</span></span>  
  
 <span data-ttu-id="dd5ae-106">模型項目安全性會套用到報表伺服器上處理的模型，而且不會影響您在模型設計師中編輯或在報表設計師中使用的 .smdl 檔案。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-106">Model item security is applied to a model that is processed on the report server and does not affect .smdl files that you edit in Model Designer or use in Report Designer.</span></span> <span data-ttu-id="dd5ae-107">此外，它也不會影響具有修改模型定義之權限的使用者。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-107">Furthermore, it has no effect on users who have permission to modify a model definition.</span></span> <span data-ttu-id="dd5ae-108">具有模型之內容管理員或發行者權限的任何使用者都可以看到它所有的部分，不論您是否套用模型項目安全性。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-108">Any user who has Content Manager or Publisher permissions on a model can see all parts of it, regardless of whether you apply model item security.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd5ae-109">模型項目可進一步透過安全性篩選的使用來維護安全。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-109">Model items can be further secured through the use of security filters.</span></span>  
  
 <span data-ttu-id="dd5ae-110">您可以針對模型內部的實體、資料夾和個別欄位定義模型項目安全性。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-110">You can define model item security on entities, folders, and individual fields within a model.</span></span> <span data-ttu-id="dd5ae-111">由於模型會呈現此一龐大的安全性實體項目表面，因此模型會內建權限繼承，如此您可以透過相當少數的角色指派來保護大量項目的安全。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-111">Because a model presents such a large surface of securable items, permission inheritance is built into the model so that you can secure a large number of items through a relatively small number of role assignments.</span></span> <span data-ttu-id="dd5ae-112">權限繼承是以下列項目為基礎：</span><span class="sxs-lookup"><span data-stu-id="dd5ae-112">Permission inheritance is based on the following:</span></span>  
  
-   <span data-ttu-id="dd5ae-113">模型</span><span class="sxs-lookup"><span data-stu-id="dd5ae-113">Model</span></span>  
  
-   <span data-ttu-id="dd5ae-114">根節點</span><span class="sxs-lookup"><span data-stu-id="dd5ae-114">Root node</span></span>  
  
-   <span data-ttu-id="dd5ae-115">資料夾或實體</span><span class="sxs-lookup"><span data-stu-id="dd5ae-115">Folders or entities</span></span>  
  
-   <span data-ttu-id="dd5ae-116">欄位</span><span class="sxs-lookup"><span data-stu-id="dd5ae-116">Fields</span></span>  
  
 <span data-ttu-id="dd5ae-117">起初，存取模型項目的權限是透過模型本身設定的角色指派繼承的。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-117">Initially, permission to access to model items is inherited through role assignments that are set on the model itself.</span></span> <span data-ttu-id="dd5ae-118">有權在報表管理員的資料夾中檢視模型的使用者就可以檢視該模型中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-118">A user who has permission to view a model in a folder in Report Manager can view all of the items in the model.</span></span>  
  
 <span data-ttu-id="dd5ae-119">如果您套用了模型項目安全性，就至少必須在根節點上建立一個角色指派。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-119">If you apply model item security, you must create at least one role assignment on the root node.</span></span> <span data-ttu-id="dd5ae-120">根節點上的這個初始角色指派會成為繼承權限的新來源。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-120">This initial role assignment on the root node becomes the new source of inherited permissions.</span></span> <span data-ttu-id="dd5ae-121">根節點上的角色指派會自動由模型階層中的所有項目繼承。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-121">The role assignment on the root node is automatically inherited by all items in the model hierarchy.</span></span>  
  
 <span data-ttu-id="dd5ae-122">若要進一步自訂資料瀏覽的權限，您可以改變資料夾和實體的權限。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-122">To further customize permissions on data exploration, you can vary permissions on folders and entities.</span></span> <span data-ttu-id="dd5ae-123">最後，您可以設定個別欄位的權限。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-123">Finally, you can set permissions on individual fields.</span></span>  
  
 <span data-ttu-id="dd5ae-124">為了使角色指派較容易維護，請單獨設定資料夾或實體的權限，而非個別欄位的權限。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-124">To make role assignments easier to maintain, set permissions only on folders or entities rather than individual fields.</span></span> <span data-ttu-id="dd5ae-125">您無法搜尋自己建立的角色指派。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-125">You cannot search for role assignments that you create.</span></span> <span data-ttu-id="dd5ae-126">如果在特定欄位上設定安全性而且您想要稍後更新安全性設定，就必須在模型命名空間中點選連結，以尋找您所保護的欄位。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-126">If you set security on specific fields and you want to update the security settings later, you must click through the model namespace to find the fields you secured.</span></span>  
  
 <span data-ttu-id="dd5ae-127">若要開始作業，請在根節點上建立角色指派，然後在實體和資料夾上建立其他角色指派。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-127">To get started, create a role assignment on the root node and then create additional role assignments on entities and folders.</span></span> <span data-ttu-id="dd5ae-128">若要清除模型項目安全性，請清除 **[獨立保護此模型的個別模型項目]** 的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-128">To clear model item security, clear the check box for **Secure individual model items independently for this model**.</span></span> <span data-ttu-id="dd5ae-129">清除此核取方塊就會還原回從模型繼承的初始權限。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-129">Clearing the check box reverts back to the initial permissions that are inherited from the model.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="dd5ae-130">導覽</span><span class="sxs-lookup"><span data-stu-id="dd5ae-130">Navigation</span></span>  
 <span data-ttu-id="dd5ae-131">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-131">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-general-properties-page-for-a-report"></a><span data-ttu-id="dd5ae-132">若要開啟報表的一般屬性頁面</span><span class="sxs-lookup"><span data-stu-id="dd5ae-132">To open the General properties page for a report</span></span>  
  
1.  <span data-ttu-id="dd5ae-133">開啟報表管理員，然後找出您想要設定模型項目安全性的模型。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-133">Open Report Manager, and locate the model for which you want to configure security for model items.</span></span>  
  
2.  <span data-ttu-id="dd5ae-134">將滑鼠停留在該模型上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-134">Hover over the model, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="dd5ae-135">在下拉式功能表中，按一下 **[管理]**。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-135">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="dd5ae-136">這樣就會開啟該模型的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-136">This opens the General properties page for the model.</span></span>  
  
4.  <span data-ttu-id="dd5ae-137">選取 **[模型項目安全性]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-137">Select the **Model Item Security** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dd5ae-138">選項</span><span class="sxs-lookup"><span data-stu-id="dd5ae-138">Options</span></span>  
 <span data-ttu-id="dd5ae-139">**[獨立保護此模型的個別模型項目]**</span><span class="sxs-lookup"><span data-stu-id="dd5ae-139">**Secure individual model items independently for this model**</span></span>  
 <span data-ttu-id="dd5ae-140">按一下此核取方塊，即可啟用模型項目安全性。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-140">Click this check box to enable model item security.</span></span>  
  
 <span data-ttu-id="dd5ae-141">**指定模型中個別模型項目的安全性**</span><span class="sxs-lookup"><span data-stu-id="dd5ae-141">**Specify security for individual model items in the mode**</span></span>  
 <span data-ttu-id="dd5ae-142">顯示模型中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-142">Shows all of the items in a model.</span></span> <span data-ttu-id="dd5ae-143">您可以導覽模型命名空間，以選取要保護的項目。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-143">You can navigate the model namespace to select the item you want to secure.</span></span> <span data-ttu-id="dd5ae-144">您一次只能選取一個項目。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-144">You can only select one item at a time.</span></span> <span data-ttu-id="dd5ae-145">請務必在根節點上建立第一個角色指派，然後再繼續處理其他實體和資料夾。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-145">Be sure to create the first role assignment on the root node before proceeding to other entities and folders.</span></span>  
  
 <span data-ttu-id="dd5ae-146">**從父項目繼承權限**</span><span class="sxs-lookup"><span data-stu-id="dd5ae-146">**Inherit permissions from the parent item**</span></span>  
 <span data-ttu-id="dd5ae-147">按一下此選項，即可繼承父項目的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-147">Click this option to inherit the security settings of the parent item.</span></span>  
  
 <span data-ttu-id="dd5ae-148">**指派讀取權限給下列使用者和群組 (用分號分隔)**</span><span class="sxs-lookup"><span data-stu-id="dd5ae-148">**Assign read permission to the following users and groups (semi-colon separated)**</span></span>  
 <span data-ttu-id="dd5ae-149">按一下此選項，即可指定您正在定義存取權的使用者或群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-149">Click this option to specify the user or group account for which you are defining access.</span></span> <span data-ttu-id="dd5ae-150">如果您是使用預設安全性，則使用者和群組帳戶是 Windows 網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-150">If you are using default security, the user and group accounts are Windows domain accounts.</span></span> <span data-ttu-id="dd5ae-151">請以此格式指定帳戶： \* \<domain> \\<帳戶 \> \*。</span><span class="sxs-lookup"><span data-stu-id="dd5ae-151">Specify the accounts in this format: *\<domain>\\<account\>*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd5ae-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd5ae-152">See Also</span></span>  
 [<span data-ttu-id="dd5ae-153">Management Studio F1 說明中的報表伺服器</span><span class="sxs-lookup"><span data-stu-id="dd5ae-153">Report Server in Management Studio F1 Help</span></span>](tools/report-server-in-management-studio-f1-help.md)  
  
  
