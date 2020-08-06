---
title: 啟用、停用以及刪除中斷點
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 357b5874-273f-43a9-8e30-83872bdea5dc
author: rothja
ms.author: jroth
ms.openlocfilehash: 17e83c6488b9d9026fb78e5fb8f50e22533fa61e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606227"
---
# <a name="enable-disable-and-delete-breakpoints"></a><span data-ttu-id="566d5-102">啟用、停用以及刪除中斷點</span><span class="sxs-lookup"><span data-stu-id="566d5-102">Enable, Disable, and Delete Breakpoints</span></span>
  <span data-ttu-id="566d5-103">若要檢視和管理所有已開啟的中斷點，您可以使用 **[中斷點]** 視窗。</span><span class="sxs-lookup"><span data-stu-id="566d5-103">To view and manage all the open breakpoints, you can use the **Breakpoints** window.</span></span> <span data-ttu-id="566d5-104">這個視窗可用以檢視中斷點資訊，以及採取刪除、停用或啟用中斷點的這類動作。</span><span class="sxs-lookup"><span data-stu-id="566d5-104">Use the window to view breakpoint information and to take actions such as deleting, disabling, or enabling breakpoints.</span></span>  
  
## <a name="the-breakpoints-window"></a><span data-ttu-id="566d5-105">中斷點視窗</span><span class="sxs-lookup"><span data-stu-id="566d5-105">The Breakpoints Window</span></span>  
 <span data-ttu-id="566d5-106">**[中斷點]** 視窗會列出一些資訊，例如中斷點所在的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="566d5-106">The **Breakpoints** window lists information such as which line of code the breakpoint is located on.</span></span> <span data-ttu-id="566d5-107">在 **[中斷點]** 視窗中，您也可以刪除、停用和啟用中斷點。</span><span class="sxs-lookup"><span data-stu-id="566d5-107">In the **Breakpoints** window, you can also delete, disable, and enable breakpoints.</span></span> <span data-ttu-id="566d5-108">如需有關 **[中斷點]** 視窗的詳細資訊，請參閱＜ [[中斷點] Window](transact-sql-debugger-breakpoints-window.md)＞。</span><span class="sxs-lookup"><span data-stu-id="566d5-108">For more information about the **Breakpoints** window, see [Breakpoints Window](transact-sql-debugger-breakpoints-window.md)</span></span>  
  
 <span data-ttu-id="566d5-109">停用中斷點會讓中斷點無法暫停執行，但是會將定義保留在原處，讓您可以在之後想要啟用中斷點時使用。</span><span class="sxs-lookup"><span data-stu-id="566d5-109">Disabling a breakpoint prevents it from pausing execution, but leaves the definition in place in case you want to enable the breakpoint later.</span></span> <span data-ttu-id="566d5-110">刪除中斷點，即會永久刪除中斷點。</span><span class="sxs-lookup"><span data-stu-id="566d5-110">Deleting a breakpoint removes it permanently.</span></span> <span data-ttu-id="566d5-111">您必須切換新的中斷點，以暫停陳述式的執行。</span><span class="sxs-lookup"><span data-stu-id="566d5-111">You must toggle a new breakpoint to pause execution on the statement.</span></span>  
  
## <a name="to-open-the-breakpoints-window"></a><span data-ttu-id="566d5-112">開啟中斷點視窗</span><span class="sxs-lookup"><span data-stu-id="566d5-112">To Open the Breakpoints Window</span></span>  
 <span data-ttu-id="566d5-113">**To open the Breakpoints window**</span><span class="sxs-lookup"><span data-stu-id="566d5-113">**To open the Breakpoints window**</span></span>  
  
 <span data-ttu-id="566d5-114">您可以利用下列其中一種方式來開啟 **[中斷點]** 視窗：</span><span class="sxs-lookup"><span data-stu-id="566d5-114">You can open the **Breakpoints** window in one of the following ways:</span></span>  
  
-   <span data-ttu-id="566d5-115">在 **[偵錯]** 功能表上，按一下 **[視窗]** ，然後按一下 **[中斷點]** 。</span><span class="sxs-lookup"><span data-stu-id="566d5-115">On the **Debug** menu, click **Windows**, and then click **Breakpoints**.</span></span>  
  
-   <span data-ttu-id="566d5-116">在 **[偵錯]** 工具列上，按一下 **[中斷點]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="566d5-116">On the **Debug** toolbar, click the **Breakpoints** button.</span></span>  
  
-   <span data-ttu-id="566d5-117">按下 CTRL+ALT+B。</span><span class="sxs-lookup"><span data-stu-id="566d5-117">Press CTRL+ALT+B.</span></span>  
  
## <a name="to-disable-a-single-breakpoint"></a><span data-ttu-id="566d5-118">停用單一中斷點</span><span class="sxs-lookup"><span data-stu-id="566d5-118">To Disable a Single Breakpoint</span></span>  
 <span data-ttu-id="566d5-119">**To disable a single breakpoint**</span><span class="sxs-lookup"><span data-stu-id="566d5-119">**To disable a single breakpoint**</span></span>  
  
 <span data-ttu-id="566d5-120">您可以使用下列其中一種方式以停用單一中斷點：</span><span class="sxs-lookup"><span data-stu-id="566d5-120">You can disable a single breakpoint in one of the following ways:</span></span>  
  
-   <span data-ttu-id="566d5-121">在 [查詢編輯器] 視窗中，以滑鼠右鍵按一下中斷點，然後按一下 [停用中斷點]  。</span><span class="sxs-lookup"><span data-stu-id="566d5-121">In the Query Editor window, right-click the breakpoint, and then click **Disable Breakpoint**.</span></span>  
  
-   <span data-ttu-id="566d5-122">在 [中斷點] 視窗中，清除中斷點左側的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="566d5-122">In the Breakpoints window, clear the check box to the left of the breakpoint.</span></span>  
  
## <a name="to-disable-all-breakpoints"></a><span data-ttu-id="566d5-123">停用所有中斷點</span><span class="sxs-lookup"><span data-stu-id="566d5-123">To Disable All Breakpoints</span></span>  
 <span data-ttu-id="566d5-124">**To disable all breakpoints**</span><span class="sxs-lookup"><span data-stu-id="566d5-124">**To disable all breakpoints**</span></span>  
  
 <span data-ttu-id="566d5-125">您可以使用下列其中一種方式以停用所有中斷點：</span><span class="sxs-lookup"><span data-stu-id="566d5-125">You can disable all breakpoints in one of the following ways:</span></span>  
  
-   <span data-ttu-id="566d5-126">在 **[偵錯]** 功能表上，按一下 **[停用所有中斷點]** 。</span><span class="sxs-lookup"><span data-stu-id="566d5-126">On the **Debug** menu, click **Disable All Breakpoints**.</span></span>  
  
-   <span data-ttu-id="566d5-127">在 **[中斷點]** 視窗的工具列上，按一下 **[停用所有中斷點]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="566d5-127">On the toolbar of the **Breakpoints** window, click the **Disable All Breakpoints** button.</span></span>  
  
## <a name="to-enable-a-single-breakpoint"></a><span data-ttu-id="566d5-128">啟用單一中斷點</span><span class="sxs-lookup"><span data-stu-id="566d5-128">To Enable a Single Breakpoint</span></span>  
 <span data-ttu-id="566d5-129">**To enable a single breakpoint**</span><span class="sxs-lookup"><span data-stu-id="566d5-129">**To enable a single breakpoint**</span></span>  
  
 <span data-ttu-id="566d5-130">您可以使用下列其中一種方式以啟用單一中斷點：</span><span class="sxs-lookup"><span data-stu-id="566d5-130">You can enable a single breakpoint in one of the following ways:</span></span>  
  
-   <span data-ttu-id="566d5-131">在 [查詢編輯器] 視窗中，以滑鼠右鍵按一下中斷點，然後按一下 [啟用中斷點]  。</span><span class="sxs-lookup"><span data-stu-id="566d5-131">In the Query Editor window, right-click the breakpoint, and then click **Enable Breakpoint**.</span></span>  
  
-   <span data-ttu-id="566d5-132">在 [中斷點] 視窗中，按一下中斷點左側的方塊。</span><span class="sxs-lookup"><span data-stu-id="566d5-132">In the Breakpoints window, click the box to the left of the breakpoint.</span></span>  
  
## <a name="to-enable-all-breakpoints"></a><span data-ttu-id="566d5-133">啟用所有中斷點</span><span class="sxs-lookup"><span data-stu-id="566d5-133">To Enable All Breakpoints</span></span>  
 <span data-ttu-id="566d5-134">**To enable all breakpoints**</span><span class="sxs-lookup"><span data-stu-id="566d5-134">**To enable all breakpoints**</span></span>  
  
 <span data-ttu-id="566d5-135">您可以使用下列其中一種方式以啟用所有中斷點：</span><span class="sxs-lookup"><span data-stu-id="566d5-135">You can enable all breakpoints in one of the following ways:</span></span>  
  
-   <span data-ttu-id="566d5-136">在 **[偵錯]** 功能表上，按一下 **[啟用所有中斷點]** 。</span><span class="sxs-lookup"><span data-stu-id="566d5-136">On the **Debug** menu, click **Enable All Breakpoints**.</span></span>  
  
-   <span data-ttu-id="566d5-137">在 **[中斷點]** 視窗的工具列上，按一下 **[啟用所有中斷點]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="566d5-137">On the toolbar of the **Breakpoints** window, click the **Enable All Breakpoints** button.</span></span>  
  
## <a name="to-delete-a-single-breakpoint"></a><span data-ttu-id="566d5-138">刪除單一中斷點</span><span class="sxs-lookup"><span data-stu-id="566d5-138">To Delete a Single Breakpoint</span></span>  
 <span data-ttu-id="566d5-139">**To delete a single breakpoint**</span><span class="sxs-lookup"><span data-stu-id="566d5-139">**To delete a single breakpoint**</span></span>  
  
 <span data-ttu-id="566d5-140">您可以使用下列其中一種方式以刪除單一中斷點：</span><span class="sxs-lookup"><span data-stu-id="566d5-140">You can delete a single breakpoint in one of the following ways:</span></span>  
  
-   <span data-ttu-id="566d5-141">在 [查詢編輯器] 視窗中，以滑鼠右鍵按一下中斷點，然後按一下 [刪除中斷點]  。</span><span class="sxs-lookup"><span data-stu-id="566d5-141">In the Query Editor window, right-click the breakpoint, and then click **Delete Breakpoint**.</span></span>  
  
-   <span data-ttu-id="566d5-142">在 [中斷點] 視窗中，以滑鼠右鍵按一下中斷點，然後按一下捷徑功能表上的 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="566d5-142">In the Breakpoints window, right-click the breakpoint, and then click **Delete** on the shortcut menu.</span></span>  
  
-   <span data-ttu-id="566d5-143">在 [中斷點] 視窗中，選取中斷點，然後按下 DELETE。</span><span class="sxs-lookup"><span data-stu-id="566d5-143">In the Breakpoints window, select the breakpoint, and then press DELETE.</span></span>  
  
## <a name="to-delete-all-breakpoints"></a><span data-ttu-id="566d5-144">刪除所有中斷點</span><span class="sxs-lookup"><span data-stu-id="566d5-144">To Delete All Breakpoints</span></span>  
 <span data-ttu-id="566d5-145">**To delete all breakpoints**</span><span class="sxs-lookup"><span data-stu-id="566d5-145">**To delete all breakpoints**</span></span>  
  
 <span data-ttu-id="566d5-146">您可以使用下列其中一種方式以刪除所有中斷點：</span><span class="sxs-lookup"><span data-stu-id="566d5-146">You can delete all breakpoints in one of the following ways:</span></span>  
  
-   <span data-ttu-id="566d5-147">在 **[偵錯]** 功能表上，按一下 **[刪除所有中斷點]** 。</span><span class="sxs-lookup"><span data-stu-id="566d5-147">On the **Debug** menu, cllick **Delete All Breakpoints**.</span></span>  
  
-   <span data-ttu-id="566d5-148">在 **[中斷點]** 視窗的工具列上，按一下 **[刪除所有中斷點]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="566d5-148">On the toolbar of the **Breakpoints** window, click the **Delete All Breakpoints** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="566d5-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="566d5-149">See Also</span></span>  
 [<span data-ttu-id="566d5-150">切換中斷點</span><span class="sxs-lookup"><span data-stu-id="566d5-150">Toggle a Breakpoint</span></span>](../spatial/point.md)  
  
  
