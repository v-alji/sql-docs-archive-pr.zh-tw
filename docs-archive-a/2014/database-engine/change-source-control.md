---
title: 變更原始檔控制 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- IDD_SCC_CONNECTION_DIALOG
helpviewer_keywords:
- Change Source Control dialog box
ms.assetid: e6a5d83c-5809-4c56-907a-73d0c7ccdd7a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 55831529243608e8c71972a31009e5672fb0234f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597368"
---
# <a name="change-source-control"></a><span data-ttu-id="3a526-102">變更原始檔控制</span><span class="sxs-lookup"><span data-stu-id="3a526-102">Change Source Control</span></span>
  <span data-ttu-id="3a526-103">建立與管理連接和繫結，連接和繫結會將本機上儲存的方案或專案連結至原始檔控制資料庫資料夾。</span><span class="sxs-lookup"><span data-stu-id="3a526-103">Creates and manages the connections and bindings that link a locally saved solution or project to a source control database folder.</span></span>  
  
## <a name="dialog-box-access"></a><span data-ttu-id="3a526-104">對話方塊存取</span><span class="sxs-lookup"><span data-stu-id="3a526-104">Dialog Box Access</span></span>  
 <span data-ttu-id="3a526-105">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中，選取方案總管中的項目。</span><span class="sxs-lookup"><span data-stu-id="3a526-105">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], select an item in Solution Explorer.</span></span> <span data-ttu-id="3a526-106">**在 [檔案**] 功能表上，按一下 [原始檔**控制**]，然後**變更 [原始檔控制**]。</span><span class="sxs-lookup"><span data-stu-id="3a526-106">On the **File** menu, click **Source Control**, and then **Change Source Control**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a526-107">在方案總管中以滑鼠右鍵按一下項目，亦可使用此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3a526-107">This dialog box is also available by right-clicking the item in Solution Explorer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3a526-108">選項</span><span class="sxs-lookup"><span data-stu-id="3a526-108">Options</span></span>  
 <span data-ttu-id="3a526-109">**Bind**</span><span class="sxs-lookup"><span data-stu-id="3a526-109">**Bind**</span></span>  
 <span data-ttu-id="3a526-110">建立選取的項目與指定的原始檔控制伺服器位置的關聯。</span><span class="sxs-lookup"><span data-stu-id="3a526-110">Associate selected items with a specified source control server location.</span></span> <span data-ttu-id="3a526-111">例如，您可以使用此按鈕，來繫節至最後的已知原始檔控制伺服器和資料庫。</span><span class="sxs-lookup"><span data-stu-id="3a526-111">For example, you can use this button to bind to the last known source control server folder and database.</span></span> <span data-ttu-id="3a526-112">如果找不到最近使用的伺服器資料夾或資料庫，就會提示您指定另一個。</span><span class="sxs-lookup"><span data-stu-id="3a526-112">If a recent server folder or database cannot be found, you are prompted to specify another.</span></span>  
  
 <span data-ttu-id="3a526-113">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="3a526-113">**Browse**</span></span>  
 <span data-ttu-id="3a526-114">導覽至指定之項目的新原始檔控制伺服器位置。</span><span class="sxs-lookup"><span data-stu-id="3a526-114">Navigate to a new source control server location for the specified item.</span></span>  
  
 <span data-ttu-id="3a526-115">**資料行**</span><span class="sxs-lookup"><span data-stu-id="3a526-115">**Columns**</span></span>  
 <span data-ttu-id="3a526-116">識別要顯示的資料行以及它們顯示的順序。</span><span class="sxs-lookup"><span data-stu-id="3a526-116">Identify columns to display and the order in which they are displayed.</span></span>  
  
 <span data-ttu-id="3a526-117">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="3a526-117">**Connect**</span></span>  
 <span data-ttu-id="3a526-118">在選取的項目和原始檔控制伺服器之間建立連接。</span><span class="sxs-lookup"><span data-stu-id="3a526-118">Create a connection between selected items and the source control server.</span></span>  
  
 <span data-ttu-id="3a526-119">**已連接**</span><span class="sxs-lookup"><span data-stu-id="3a526-119">**Connected**</span></span>  
 <span data-ttu-id="3a526-120">顯示選取之方案或專案的連接狀態。</span><span class="sxs-lookup"><span data-stu-id="3a526-120">Displays the connection status of a selected solution or project.</span></span>  
  
 <span data-ttu-id="3a526-121">**中斷連線**</span><span class="sxs-lookup"><span data-stu-id="3a526-121">**Disconnect**</span></span>  
 <span data-ttu-id="3a526-122">將電腦上的方案或專案的本機副本與資料庫中的主要副本中斷連接。</span><span class="sxs-lookup"><span data-stu-id="3a526-122">Disconnect the local copy of a solution or project on your computer from its master copy in the database.</span></span> <span data-ttu-id="3a526-123">在將電腦與原始檔控制伺服器中斷連接之前 (例如，在膝上型電腦上離線工作時)，請使用此命令。</span><span class="sxs-lookup"><span data-stu-id="3a526-123">Use this command before disconnecting your computer from the source control server, for example, when working offline on your laptop.</span></span>  
  
 <span data-ttu-id="3a526-124">**確定**</span><span class="sxs-lookup"><span data-stu-id="3a526-124">**OK**</span></span>  
 <span data-ttu-id="3a526-125">接受在對話方塊中所做的變更。</span><span class="sxs-lookup"><span data-stu-id="3a526-125">Accept changes made in the dialog box.</span></span>  
  
 <span data-ttu-id="3a526-126">**提供者**</span><span class="sxs-lookup"><span data-stu-id="3a526-126">**Provider**</span></span>  
 <span data-ttu-id="3a526-127">顯示原始檔控制外掛程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a526-127">Displays the name of your source control plug-in.</span></span>  
  
 <span data-ttu-id="3a526-128">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="3a526-128">**Refresh**</span></span>  
 <span data-ttu-id="3a526-129">針對此對話方塊中所列出的所有專案，重新整理連接資訊。</span><span class="sxs-lookup"><span data-stu-id="3a526-129">Refreshes the connection information for all projects listed in this dialog box.</span></span>  
  
 <span data-ttu-id="3a526-130">**伺服器繫結**</span><span class="sxs-lookup"><span data-stu-id="3a526-130">**Server Binding**</span></span>  
 <span data-ttu-id="3a526-131">指出項目繫結至原始檔控制伺服器。</span><span class="sxs-lookup"><span data-stu-id="3a526-131">Indicates the item's binding to a source control server.</span></span>  
  
 <span data-ttu-id="3a526-132">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="3a526-132">**Server Name**</span></span>  
 <span data-ttu-id="3a526-133">顯示對應之方案或專案所繫結到的原始檔控制伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a526-133">Displays the name of the source control server to which the corresponding solution or project is bound.</span></span>  
  
 <span data-ttu-id="3a526-134">**方案/專案**</span><span class="sxs-lookup"><span data-stu-id="3a526-134">**Solution/Project**</span></span>  
 <span data-ttu-id="3a526-135">顯示目前選取項目中之每個方案和專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a526-135">Displays the name of each solution and project in the current selection.</span></span>  
  
 <span data-ttu-id="3a526-136">**排序**</span><span class="sxs-lookup"><span data-stu-id="3a526-136">**Sort**</span></span>  
 <span data-ttu-id="3a526-137">排序顯示之資料行的順序。</span><span class="sxs-lookup"><span data-stu-id="3a526-137">Sort the order of displayed columns.</span></span>  
  
 <span data-ttu-id="3a526-138">**狀態**</span><span class="sxs-lookup"><span data-stu-id="3a526-138">**Status**</span></span>  
 <span data-ttu-id="3a526-139">識別項目的繫結和連接狀態。</span><span class="sxs-lookup"><span data-stu-id="3a526-139">Identifies the binding and connection status of an item.</span></span> <span data-ttu-id="3a526-140">可能的值為：</span><span class="sxs-lookup"><span data-stu-id="3a526-140">Possible options are:</span></span>  
  
|<span data-ttu-id="3a526-141">**選項**</span><span class="sxs-lookup"><span data-stu-id="3a526-141">**Option**</span></span>|<span data-ttu-id="3a526-142">**說明**</span><span class="sxs-lookup"><span data-stu-id="3a526-142">**Description**</span></span>|  
|----------------|---------------------|  
|<span data-ttu-id="3a526-143">有效</span><span class="sxs-lookup"><span data-stu-id="3a526-143">Valid</span></span>|<span data-ttu-id="3a526-144">項目已正確地繫結並連接到其所屬的伺服器資料夾。</span><span class="sxs-lookup"><span data-stu-id="3a526-144">The item is correctly bound and connected to the server folder to which it belongs.</span></span>|  
|<span data-ttu-id="3a526-145">無效</span><span class="sxs-lookup"><span data-stu-id="3a526-145">Invalid</span></span>|<span data-ttu-id="3a526-146">項目不正確地繫結至其所屬的資料夾，或是中斷與其所屬之資料夾的連接。</span><span class="sxs-lookup"><span data-stu-id="3a526-146">The item is incorrectly bound to or disconnected from the folder to which it belongs.</span></span> <span data-ttu-id="3a526-147">使用 [**加入至原始檔控制**] 命令，而**不是 [** 系結] 這個專案。</span><span class="sxs-lookup"><span data-stu-id="3a526-147">Use the **Add to Source Control** command instead of **Bind** for this item.</span></span>|  
|<span data-ttu-id="3a526-148">Unknown</span><span class="sxs-lookup"><span data-stu-id="3a526-148">Unknown</span></span>|<span data-ttu-id="3a526-149">尚未決定在原始檔控制下之項目的狀態。</span><span class="sxs-lookup"><span data-stu-id="3a526-149">The status of the item under source control has not yet been determined.</span></span>|  
|<span data-ttu-id="3a526-150">未控制</span><span class="sxs-lookup"><span data-stu-id="3a526-150">Not Controlled</span></span>|<span data-ttu-id="3a526-151">項目尚未放置在原始檔控制之下。</span><span class="sxs-lookup"><span data-stu-id="3a526-151">The item has not been placed under source control.</span></span>|  
  
 <span data-ttu-id="3a526-152">**解除繫結**</span><span class="sxs-lookup"><span data-stu-id="3a526-152">**Unbind**</span></span>  
 <span data-ttu-id="3a526-153">顯示 [**原始檔控制**] 對話方塊，可讓您從原始檔控制中移除選取的專案，並將專案從其目前的資料夾永久解除關聯。</span><span class="sxs-lookup"><span data-stu-id="3a526-153">Display the **Source Control** dialog box to allow you to remove selected items from source control and permanently disassociate the items from their present folders.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a526-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a526-154">See Also</span></span>  
 [<span data-ttu-id="3a526-155">方案總管原始檔控制</span><span class="sxs-lookup"><span data-stu-id="3a526-155">Solution Explorer Source Control</span></span>](../../2014/database-engine/solution-explorer-source-control.md)  
  
  
