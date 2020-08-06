---
title: 選項 (文字編輯器：編輯器索引標籤和狀態列頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqleditors.editorcontextsettings
- VS.ToolsOptionsPages.Text_Editor.EditorTabAndStatusBar
ms.assetid: e4815678-7885-4631-878f-c6a2b857ee05
author: rothja
ms.author: jroth
ms.openlocfilehash: 920b7d48b5f7a2472a521af21c8217b1adba486a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599175"
---
# <a name="options-text-editor-editor-tab-and-status-bar-page"></a><span data-ttu-id="8d77d-102">選項 (文字編輯器：編輯器索引標籤和狀態列頁面)</span><span class="sxs-lookup"><span data-stu-id="8d77d-102">Options (Text Editor: Editor Tab and Status Bar Page)</span></span>
  <span data-ttu-id="8d77d-103">[編輯器索引標籤和狀態列]\*\*\*\* 頁面可讓您自訂 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 查詢編輯器所顯示的資訊。</span><span class="sxs-lookup"><span data-stu-id="8d77d-103">The **Editor Tab and Status Bar Page** lets you customize the information displayed by the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Query Editors.</span></span> <span data-ttu-id="8d77d-104">您可以指定 [查詢編輯器] 視窗的索引標籤和狀態列中顯示的資訊層級，以及狀態列出現在編輯器視窗頂端或底部。</span><span class="sxs-lookup"><span data-stu-id="8d77d-104">You can specify the level of information displayed in the tab and status bar of the Query Editor window, and whether the status bar appears at the top or bottom of the editor window.</span></span>  
  
## <a name="option-settings-by-editor"></a><span data-ttu-id="8d77d-105">依編輯器的選項設定</span><span class="sxs-lookup"><span data-stu-id="8d77d-105">Option Settings by Editor</span></span>  
 <span data-ttu-id="8d77d-106">所有 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 編輯器中都可以使用編輯器索引標籤和狀態列，但有不同的功能等級。</span><span class="sxs-lookup"><span data-stu-id="8d77d-106">The editor tab and the status bar are available in all of the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] editors, but have different levels of functionality.</span></span>  
  
 <span data-ttu-id="8d77d-107">Database Engine 查詢編輯器可以連接至伺服器群組，在此情況下，它會開啟伺服器群組中所有執行個體的連接，而且可以同時在每個連接上執行相同查詢。</span><span class="sxs-lookup"><span data-stu-id="8d77d-107">The Database Engine Query Editor can connect to a server group, in which case it opens connections to all the instances in the Server Group and can simultaneously run the same query on each connection.</span></span> <span data-ttu-id="8d77d-108">您可以使用這個對話方塊，指定當連接至多個執行個體，而不是一個執行個體時，狀態列會有不同的色彩。若要變更多伺服器的結果選項時，請使用[選項 (查詢結果/SQL Server/多伺服器)](../../2014/database-engine/options-query-results-sql-server-multi-server.md) 頁面。</span><span class="sxs-lookup"><span data-stu-id="8d77d-108">You can use this dialog to specify that the status bar has different colors when connected to multiple instances rather than one instance.To change the multi-server results options, use the [Options (Query Results/SQL Server/Multi-Server)](../../2014/database-engine/options-query-results-sql-server-multi-server.md) page.</span></span>  
  
## <a name="status-bar-content"></a><span data-ttu-id="8d77d-109">狀態列內容</span><span class="sxs-lookup"><span data-stu-id="8d77d-109">Status Bar Content</span></span>  
 <span data-ttu-id="8d77d-110">指定出現在查詢編輯器狀態列中的資訊。</span><span class="sxs-lookup"><span data-stu-id="8d77d-110">Specifies the information that appears in the Query Editor status bar.</span></span>  
  
 <span data-ttu-id="8d77d-111">**顯示執行時間**</span><span class="sxs-lookup"><span data-stu-id="8d77d-111">**Display execution time**</span></span>  
 <span data-ttu-id="8d77d-112">包括指令碼執行時間。</span><span class="sxs-lookup"><span data-stu-id="8d77d-112">Includes the script execution time.</span></span> <span data-ttu-id="8d77d-113">設定如下：</span><span class="sxs-lookup"><span data-stu-id="8d77d-113">The settings are as follows:</span></span>  
  
 <span data-ttu-id="8d77d-114">**None**</span><span class="sxs-lookup"><span data-stu-id="8d77d-114">**None**</span></span>  
 <span data-ttu-id="8d77d-115">狀態列不會顯示任何時間資訊。</span><span class="sxs-lookup"><span data-stu-id="8d77d-115">The status bar displays no time information.</span></span>  
  
 <span data-ttu-id="8d77d-116">**結束**</span><span class="sxs-lookup"><span data-stu-id="8d77d-116">**End**</span></span>  
 <span data-ttu-id="8d77d-117">狀態列會在指令碼執行時顯示目前當日時間。</span><span class="sxs-lookup"><span data-stu-id="8d77d-117">The status bar displays the current time of day while the script is running.</span></span> <span data-ttu-id="8d77d-118">當指令碼完成時，則會顯示指令碼完成的當日時間。</span><span class="sxs-lookup"><span data-stu-id="8d77d-118">When the script completes, the display shows the time of day that the script completed.</span></span>  
  
 <span data-ttu-id="8d77d-119">**總值**</span><span class="sxs-lookup"><span data-stu-id="8d77d-119">**Elapsed**</span></span>  
 <span data-ttu-id="8d77d-120">狀態列會顯示指令碼已執行的時間長度。</span><span class="sxs-lookup"><span data-stu-id="8d77d-120">The status bar displays the length of time that the script has been running.</span></span> <span data-ttu-id="8d77d-121">當指令碼完成時，則會顯示執行指令碼所花費的時間。</span><span class="sxs-lookup"><span data-stu-id="8d77d-121">When the script completes, the display shows how much time was taken to run the script.</span></span>  
  
 <span data-ttu-id="8d77d-122">**包含資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="8d77d-122">**Include database name**</span></span>  
 <span data-ttu-id="8d77d-123">包含連接的目前資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="8d77d-123">Includes the name of the current database for the connection.</span></span> <span data-ttu-id="8d77d-124">當第一次開啟查詢編輯器時，這是登入的預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="8d77d-124">When the query editor is first opened, this is the default database for the login.</span></span> <span data-ttu-id="8d77d-125">稍後可透過 Transact-SQL USE 陳述式變更資料庫內容。</span><span class="sxs-lookup"><span data-stu-id="8d77d-125">The database context can later be changed by using the Transact-SQL USE statement.</span></span>  
  
 <span data-ttu-id="8d77d-126">**包含登入名稱**</span><span class="sxs-lookup"><span data-stu-id="8d77d-126">**Include login name**</span></span>  
 <span data-ttu-id="8d77d-127">包含登入名稱。</span><span class="sxs-lookup"><span data-stu-id="8d77d-127">Includes the login name.</span></span>  
  
 <span data-ttu-id="8d77d-128">**包含資料列計數**</span><span class="sxs-lookup"><span data-stu-id="8d77d-128">**Include row count**</span></span>  
 <span data-ttu-id="8d77d-129">包含目前執行之指令碼已處理的資料列計數。</span><span class="sxs-lookup"><span data-stu-id="8d77d-129">Includes a count of the rows that have been processed by the script that is currently executing.</span></span>  
  
 <span data-ttu-id="8d77d-130">**包含伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="8d77d-130">**Include server name**</span></span>  
 <span data-ttu-id="8d77d-131">包含伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="8d77d-131">Includes the server name.</span></span> <span data-ttu-id="8d77d-132">如果是本機連接，這是執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="8d77d-132">For local connections, this is the instance name.</span></span> <span data-ttu-id="8d77d-133">如果是遠端連接，這是遠端電腦名稱與執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="8d77d-133">For remote connections, this is the remote computer name and instance name.</span></span>  
  
## <a name="status-bar-layout-and-colors"></a><span data-ttu-id="8d77d-134">狀態列配置和色彩</span><span class="sxs-lookup"><span data-stu-id="8d77d-134">Status Bar Layout and Colors</span></span>  
 <span data-ttu-id="8d77d-135">指定查詢編輯器狀態列中項目的色彩。</span><span class="sxs-lookup"><span data-stu-id="8d77d-135">Specifies the colors for items in the Query Editor status bar.</span></span>  
  
 <span data-ttu-id="8d77d-136">**群組連接**</span><span class="sxs-lookup"><span data-stu-id="8d77d-136">**Group connections**</span></span>  
 <span data-ttu-id="8d77d-137">當查詢編輯器有一個以上的連接時，設定狀態列的色彩。</span><span class="sxs-lookup"><span data-stu-id="8d77d-137">Set the color of the status bar when the Query Editor has more than one connection.</span></span>  
  
 <span data-ttu-id="8d77d-138">**單一伺服器連接**</span><span class="sxs-lookup"><span data-stu-id="8d77d-138">**Single server connections**</span></span>  
 <span data-ttu-id="8d77d-139">當查詢編輯器有單一連接時，設定狀態列的色彩。</span><span class="sxs-lookup"><span data-stu-id="8d77d-139">Set the color of the status bar when the Query Editor has one connection.</span></span>  
  
 <span data-ttu-id="8d77d-140">**狀態列位置**</span><span class="sxs-lookup"><span data-stu-id="8d77d-140">**Status bar location**</span></span>  
 <span data-ttu-id="8d77d-141">指定狀態列的位置。</span><span class="sxs-lookup"><span data-stu-id="8d77d-141">Specifies the location of the status bar.</span></span> <span data-ttu-id="8d77d-142">設定如下：</span><span class="sxs-lookup"><span data-stu-id="8d77d-142">The settings are as follows:</span></span>  
  
 <span data-ttu-id="8d77d-143">**前幾個**</span><span class="sxs-lookup"><span data-stu-id="8d77d-143">**Top**</span></span>  
 <span data-ttu-id="8d77d-144">狀態列會出現在 [查詢編輯器] 視窗頂端。</span><span class="sxs-lookup"><span data-stu-id="8d77d-144">The status bar appears at the top of the Query Editor window.</span></span>  
  
 <span data-ttu-id="8d77d-145">**下層**</span><span class="sxs-lookup"><span data-stu-id="8d77d-145">**Bottom**</span></span>  
 <span data-ttu-id="8d77d-146">狀態列會出現在 [查詢編輯器] 視窗的底部。</span><span class="sxs-lookup"><span data-stu-id="8d77d-146">The status bar appears at the bottom of the Query Editor window.</span></span>  
  
## <a name="tab-text"></a><span data-ttu-id="8d77d-147">索引標籤文字</span><span class="sxs-lookup"><span data-stu-id="8d77d-147">Tab Text</span></span>  
 <span data-ttu-id="8d77d-148">指定出現在 [查詢編輯器] 視窗頂端之索引標籤的文字。</span><span class="sxs-lookup"><span data-stu-id="8d77d-148">Specifies the text that appears in the tab at the top of a Query Editor window.</span></span> <span data-ttu-id="8d77d-149">如果因文字太長而無法顯示時，您可以將滑鼠停留在索引標籤顯示工具提示，檢視其中的完整字串。</span><span class="sxs-lookup"><span data-stu-id="8d77d-149">If the text is too long to display, you can view the full string in a tooltip that is displayed if you hover over the tab.</span></span>  
  
 <span data-ttu-id="8d77d-150">**包含資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="8d77d-150">**Include database name**</span></span>  
 <span data-ttu-id="8d77d-151">包含連接的目前資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="8d77d-151">Includes the name of the current database for the connection.</span></span> <span data-ttu-id="8d77d-152">當第一次開啟查詢編輯器時，這是登入的預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="8d77d-152">When the query editor is first opened, this is the default database for the login.</span></span> <span data-ttu-id="8d77d-153">稍後可透過 Transact-SQL USE 陳述式變更資料庫內容。</span><span class="sxs-lookup"><span data-stu-id="8d77d-153">The database context can later be changed by using the Transact-SQL USE statement.</span></span>  
  
 <span data-ttu-id="8d77d-154">**包含檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="8d77d-154">**Include file name**</span></span>  
 <span data-ttu-id="8d77d-155">包含儲存指令碼的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="8d77d-155">Includes the name of the file where the script is stored.</span></span>  
  
 <span data-ttu-id="8d77d-156">**包括資料夾名稱**</span><span class="sxs-lookup"><span data-stu-id="8d77d-156">**Include folder name**</span></span>  
 <span data-ttu-id="8d77d-157">包含儲存指令碼檔的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="8d77d-157">Includes the path of the folder where the script file is stored.</span></span>  
  
 <span data-ttu-id="8d77d-158">**包含登入名稱**</span><span class="sxs-lookup"><span data-stu-id="8d77d-158">**Include login name**</span></span>  
 <span data-ttu-id="8d77d-159">包含登入名稱。</span><span class="sxs-lookup"><span data-stu-id="8d77d-159">Includes the login name.</span></span>  
  
 <span data-ttu-id="8d77d-160">**包含伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="8d77d-160">**Include server name**</span></span>  
 <span data-ttu-id="8d77d-161">包含伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="8d77d-161">Includes the server name.</span></span> <span data-ttu-id="8d77d-162">如果是本機連接，這是執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="8d77d-162">For local connections, this is the instance name.</span></span> <span data-ttu-id="8d77d-163">如果是遠端連接，這是遠端電腦名稱與執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="8d77d-163">For remote connections, this is the remote computer name and instance name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d77d-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d77d-164">See Also</span></span>  
 <span data-ttu-id="8d77d-165">[選項 &#40;環境：字型和色彩頁面&#41;](../ssms/menu-help/options-environment-fonts-and-colors-page.md) </span><span class="sxs-lookup"><span data-stu-id="8d77d-165">[Options &#40;Environment: Fonts and Colors Page&#41;](../ssms/menu-help/options-environment-fonts-and-colors-page.md) </span></span>  
 [<span data-ttu-id="8d77d-166">查詢編輯器中的色彩編碼</span><span class="sxs-lookup"><span data-stu-id="8d77d-166">Color Coding in Query Editors</span></span>](../relational-databases/scripting/color-coding-in-query-editors.md)  
  
  
