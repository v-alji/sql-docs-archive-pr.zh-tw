---
title: 在物件總管中管理事件工作階段 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
ms.assetid: 16849e38-d3fb-414d-8dcb-797b5ffce6ee
author: rothja
ms.author: jroth
ms.openlocfilehash: 1aa33a97137f63348898e6b1fcb7b19b2d218573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585409"
---
# <a name="manage-event-sessions-in-the-object-explorer"></a><span data-ttu-id="49648-102">在物件總管中管理事件工作階段</span><span class="sxs-lookup"><span data-stu-id="49648-102">Manage Event Sessions in the Object Explorer</span></span>
  <span data-ttu-id="49648-103">本主題將討論您可以在 **[物件總管]** 中採取以影響「擴充事件」的動作：</span><span class="sxs-lookup"><span data-stu-id="49648-103">This topic discusses the actions you can take in **Object Explorer** that affect Extended Events:</span></span>  
  
-   <span data-ttu-id="49648-104">建立擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="49648-104">Create an Extended Events Session</span></span>  
  
-   <span data-ttu-id="49648-105">啟動或停止擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="49648-105">Starting or Stopping an Extended Events Session</span></span>  
  
-   <span data-ttu-id="49648-106">匯出擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="49648-106">Export an Extended Events Session</span></span>  
  
-   <span data-ttu-id="49648-107">匯入擴充事件工作階段範本</span><span class="sxs-lookup"><span data-stu-id="49648-107">Import an Extended Events Session Template</span></span>  
  
-   <span data-ttu-id="49648-108">編輯擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="49648-108">Edit an Extended Events Session</span></span>  
  
-   <span data-ttu-id="49648-109">刪除擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="49648-109">Delete an Extended Events Session</span></span>  
  
## <a name="create-an-extended-events-session"></a><span data-ttu-id="49648-110">建立擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="49648-110">Create an Extended Events Session</span></span>  
 <span data-ttu-id="49648-111">如需有關建立「擴充事件」工作階段的詳細資訊，請參閱＜ [Create an Extended Events Session](../../database-engine/create-an-extended-events-session.md)＞。</span><span class="sxs-lookup"><span data-stu-id="49648-111">For more information about creating an Extended Events session, see [Create an Extended Events Session](../../database-engine/create-an-extended-events-session.md).</span></span>  
  
## <a name="starting-or-stopping-an-extended-events-session"></a><span data-ttu-id="49648-112">啟動或停止擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="49648-112">Starting or Stopping an Extended Events Session</span></span>  
 <span data-ttu-id="49648-113">您可以使用**Query Editor** `ALTER EVENT SESSION` 語句，或使用**物件總管**的 [**擴充事件**] 節點，透過查詢編輯器啟動或停止「擴充事件」會話。</span><span class="sxs-lookup"><span data-stu-id="49648-113">You can start or stop an Extended Events session through the **Query Editor** using the `ALTER EVENT SESSION` statement, or by using the **Extended Events** node of **Object Explorer**.</span></span>  
  
 <span data-ttu-id="49648-114">當您停止事件工作階段時，此工作階段不再列為 sys.dm_xe_sessions 動態管理檢視 (DMV) 中的使用中工作階段。</span><span class="sxs-lookup"><span data-stu-id="49648-114">When you stop an event session, the session is no longer listed as an active session in the sys.dm_xe_sessions dynamic management view (DMV).</span></span> <span data-ttu-id="49648-115">但是，工作階段定義會保持不變，而且您可以重新啟動工作階段。</span><span class="sxs-lookup"><span data-stu-id="49648-115">However, the session definition remains intact, and you can restart the session.</span></span> <span data-ttu-id="49648-116">若要完全移除工作階段定義，您必須刪除工作階段。</span><span class="sxs-lookup"><span data-stu-id="49648-116">To completely remove a session definition, you must delete the session.</span></span>  
  
 <span data-ttu-id="49648-117">若要啟動或停止「擴充事件」工作階段，您必須擁有 ALTER ANY EVENT SESSION 權限。</span><span class="sxs-lookup"><span data-stu-id="49648-117">To start or stop an Extended Events session, you must have the ALTER ANY EVENT SESSION permission.</span></span>  
  
 <span data-ttu-id="49648-118">當您停止了使用記憶體中目標 (如信號緩衝區、值區、事件配對或同步事件計數器目標) 的工作階段時，儲存在工作階段緩衝區中的所有資訊 (sys.dm_xe_session_targets DMV 的 target_data 資料行) 都將遺失。</span><span class="sxs-lookup"><span data-stu-id="49648-118">When you stop a session that uses an in-memory target, such as the ring buffer, bucketing, event pairing, or synchronous event counter targets, all the information stored in the session's buffer (the target_data column of the sys.dm_xe_session_targets DMV) will be lost.</span></span> <span data-ttu-id="49648-119">若要在停止工作階段之後存取事件資料，您應該在停止工作階段之前先儲存資料，或是將工作階段設定為使用檔案目標。</span><span class="sxs-lookup"><span data-stu-id="49648-119">To access event data after you stop the session, you should either save the data before you stop the session, or configure the session to use the file target.</span></span>  
  
### <a name="start-or-stop-an-extended-events-session-using-query-editor"></a><span data-ttu-id="49648-120">使用查詢編輯器啟動或停止擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="49648-120">Start or Stop an Extended Events Session Using Query Editor</span></span>  
 <span data-ttu-id="49648-121">若要啟動工作階段，請發出下列陳述式，使用「擴充事件」工作階段名稱來取代 *session_name* ：</span><span class="sxs-lookup"><span data-stu-id="49648-121">To start a session, issue the following statements, replacing *session_name* with the name of the Extended Events session:</span></span>  
  
```  
ALTER EVENT SESSION [session_name]  
ON SERVER  
STATE = START  
```  
  
 <span data-ttu-id="49648-122">若要停止工作階段，請發出下列陳述式，使用「擴充事件」工作階段名稱來取代 *session_name* ：</span><span class="sxs-lookup"><span data-stu-id="49648-122">To stop a session, issue the following statements, replacing *session_name* with the name of the Extended Events session:</span></span>  
  
```  
ALTER EVENT SESSION [session_name]  
ON SERVER  
STATE = STOP  
```  
  
### <a name="start-or-stop-an-extended-events-session-in-object-explorer"></a><span data-ttu-id="49648-123">在物件總管中啟動或停止擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="49648-123">Start or Stop an Extended Events Session in Object Explorer</span></span>  
 <span data-ttu-id="49648-124">若要在 **[物件總管]** 中啟動或停止「擴充事件」工作階段，請依序展開 **[管理]** 、 **[擴充事件]** 和 **[工作階段]** 節點、以滑鼠右鍵按一下工作階段，然後按一下 **[啟動工作階段]** 或 **[停止工作階段]** 。</span><span class="sxs-lookup"><span data-stu-id="49648-124">To start or stop an Extended Events session in **Object Explorer**, expand the **Management**, **Extended Events**, and then **Sessions** nodes and right click on a session and then click **Start Session** or **Stop Session**.</span></span>  
  
## <a name="export-an-extended-events-session-template"></a><span data-ttu-id="49648-125">匯出擴充事件工作階段範本</span><span class="sxs-lookup"><span data-stu-id="49648-125">Export an Extended Events Session Template</span></span>  
 <span data-ttu-id="49648-126">您可以使用 **[物件總管]** 來匯出「擴充事件」工作階段，並將它儲存為 .xml 範本檔案。</span><span class="sxs-lookup"><span data-stu-id="49648-126">You can export an Extended Events session using **Object Explorer**, and save it as an .xml template file.</span></span> <span data-ttu-id="49648-127">例如，您可能會想要匯出工作階段，然後使用 **[新增工作階段精靈]** 或 **[新增工作階段]** 精靈，將範本套用到新的事件工作階段。</span><span class="sxs-lookup"><span data-stu-id="49648-127">For example, you may want to export a session and then apply the template to a new event session using the **New Session Wizard** or the **New Session** wizard.</span></span>  
  
 <span data-ttu-id="49648-128">當您匯出工作階段時，請務必將範本檔案儲存到使用 NTFS 檔案系統的位置，而且要將存取限制為被授權能夠檢視資訊的使用者。</span><span class="sxs-lookup"><span data-stu-id="49648-128">When you export a session, make sure that you save the template file to a location that uses the NTFS file system, and that you restrict access to users who are authorized to view the information.</span></span>  
  
 <span data-ttu-id="49648-129">若要在 **[物件總管]** 中匯出「擴充事件」工作階段：</span><span class="sxs-lookup"><span data-stu-id="49648-129">To export an Extended Events session in **Object Explorer**:</span></span>  
  
1.  <span data-ttu-id="49648-130">依序展開 **[管理]** 、 **[擴充事件]** 和 **[工作階段]** 節點。</span><span class="sxs-lookup"><span data-stu-id="49648-130">Expand the **Management**, **Extended Events**, and then **Sessions** nodes</span></span>  
  
2.  <span data-ttu-id="49648-131">以滑鼠右鍵按一下您想要匯出的工作階段，然後選取 [匯出工作階段]。</span><span class="sxs-lookup"><span data-stu-id="49648-131">Right-click the session that you want to export, and select **Export Session**.</span></span>  
  
3.  <span data-ttu-id="49648-132">在 **[另存新檔]** 對話方塊中，選取儲存檔案的位置，並在 **[檔案名稱]** 方塊中輸入檔案名稱，然後按一下 **[儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="49648-132">In the **Save As** dialog box, select a location to save the file, type the file name in the **File name** box, and then click **Save**.</span></span>  
  
     <span data-ttu-id="49648-133">如果您將檔案儲存至預設 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 範本位置，當您使用 **[新增工作階段精靈]** 和 **[新增工作階段]** 對話方塊時，此範本將顯示在預先定義範本的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="49648-133">If you save the file to the default [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] template location, the template will appear in the dropdown list of predefined templates when you use the **New Session Wizard** and **New Session** dialog.</span></span>  
  
## <a name="import-an-extended-events-session-template"></a><span data-ttu-id="49648-134">匯入擴充事件工作階段範本</span><span class="sxs-lookup"><span data-stu-id="49648-134">Import an Extended Events Session Template</span></span>  
 <span data-ttu-id="49648-135">您可以使用 **[物件總管]** 來匯入「擴充事件」工作階段的範本。</span><span class="sxs-lookup"><span data-stu-id="49648-135">Using **Object Explorer**, you can import a template for an Extended Events session.</span></span> <span data-ttu-id="49648-136">例如，您可能會想要這樣做，以便根據從另一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體匯出的範本建立工作階段。</span><span class="sxs-lookup"><span data-stu-id="49648-136">For example, you may want to do this to create a session from a template that was exported from another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="49648-137">若要匯入「擴充事件」工作階段，您必須擁有必要的 `ALTER ANY EVENT SESSION` 權限。</span><span class="sxs-lookup"><span data-stu-id="49648-137">To import an Extended Events session, you must have the necessary `ALTER ANY EVENT SESSION` permissions.</span></span>  
  
 <span data-ttu-id="49648-138">匯入範本檔案之前，請確定檔案來自信任的來源。</span><span class="sxs-lookup"><span data-stu-id="49648-138">Before you import a template file, make sure that the file is from a trusted source.</span></span> <span data-ttu-id="49648-139">範本檔案應該儲存至使用 NTFS 檔案系統的位置，而且其存取權應該限制為被授權能夠檢視資訊的使用者。</span><span class="sxs-lookup"><span data-stu-id="49648-139">Template files should be saved to a location that uses the NTFS file system and where access is restricted to users who are authorized to view the information.</span></span>  
  
 <span data-ttu-id="49648-140">若要匯入「擴充事件」工作階段：</span><span class="sxs-lookup"><span data-stu-id="49648-140">To import an Extended Events session:</span></span>  
  
1.  <span data-ttu-id="49648-141">在 **[物件總管]** 中，依序展開 **[管理]** 和 **[擴充事件]** 節點。</span><span class="sxs-lookup"><span data-stu-id="49648-141">In **Object Explorer**, expand the **Management**, and then **Extended Events** nodes.</span></span>  
  
2.  <span data-ttu-id="49648-142">以滑鼠右鍵按一下 [工作階段]，然後選取 [新增工作階段]。</span><span class="sxs-lookup"><span data-stu-id="49648-142">Right-click **Sessions** and select **New Session**.</span></span>  
  
3.  <span data-ttu-id="49648-143">指定工作階段的名稱。</span><span class="sxs-lookup"><span data-stu-id="49648-143">Specify a name for the session.</span></span>  
  
4.  <span data-ttu-id="49648-144">展開 **[範本]** 下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="49648-144">Expand the **Template** drop down box.</span></span>  
  
5.  <span data-ttu-id="49648-145">按一下 [\<File From ...>開啟]，然後瀏覽至您想要匯入的工作階段 (XML 檔案)。</span><span class="sxs-lookup"><span data-stu-id="49648-145">Click **\<File From ...>Open** and browse for the session (XML file) you want to import.</span></span>  
  
 <span data-ttu-id="49648-146">此工作階段會顯示在 **[工作階段]** 節點底下。</span><span class="sxs-lookup"><span data-stu-id="49648-146">The session appears under the **Sessions** node.</span></span> <span data-ttu-id="49648-147">根據預設，工作階段不會啟動。</span><span class="sxs-lookup"><span data-stu-id="49648-147">By default, the session is not started.</span></span>  
  
## <a name="edit-an-extended-events-session"></a><span data-ttu-id="49648-148">編輯擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="49648-148">Edit an Extended Events Session</span></span>  
 <span data-ttu-id="49648-149">您可以在 [物件總管] 中編輯「擴充事件」工作階段。</span><span class="sxs-lookup"><span data-stu-id="49648-149">You can edit an Extended Events session in Object Explorer.</span></span>  
  
 <span data-ttu-id="49648-150">若要編輯「擴充事件」工作階段：</span><span class="sxs-lookup"><span data-stu-id="49648-150">To edit an Extended Events session:</span></span>  
  
1.  <span data-ttu-id="49648-151">在 **[物件總管]** 中，依序展開 **[管理]** 、 **[擴充事件]** 和 **[工作階段]** 節點。</span><span class="sxs-lookup"><span data-stu-id="49648-151">In **Object Explorer**, expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  
  
2.  <span data-ttu-id="49648-152">以滑鼠右鍵按一下工作階段，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="49648-152">Right-click a session and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="49648-153">在 **[選取頁面]** 區段中，選取要編輯的頁面。</span><span class="sxs-lookup"><span data-stu-id="49648-153">In the **Select a page** section, select the page or pages you want to edit.</span></span>  
  
4.  <span data-ttu-id="49648-154">完成事件工作階段的修訂之後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="49648-154">After you finish revising the event session, click **OK**.</span></span>  
  
## <a name="script-an-event-session-definition-using-tsql"></a><span data-ttu-id="49648-155">使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49648-155">Script an Event Session Definition Using [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
 <span data-ttu-id="49648-156">[新增工作階段精靈] 和 [新增工作階段] 對話方塊都具有指令碼選項，可產生定義「擴充事件」工作階段的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="49648-156">Both the New Session Wizard and the New Session dialog have a Script option that generates the [!INCLUDE[tsql](../../includes/tsql-md.md)] that defines the Extended Events session.</span></span>  
  
 <span data-ttu-id="49648-157">您可以用滑鼠右鍵按一下工作階段名稱、選取 [!INCLUDE[tsql](../../includes/tsql-md.md)] [編寫工作階段的指令碼為] **，然後選取**[CREATE 至] **，藉以存取現有「擴充事件」工作階段的**。</span><span class="sxs-lookup"><span data-stu-id="49648-157">You can access the [!INCLUDE[tsql](../../includes/tsql-md.md)] for an existing Extended Events session by right clicking the session name, selecting **Script Session as**, and then selecting **Create to**.</span></span>  
  
## <a name="delete-an-extended-events-session"></a><span data-ttu-id="49648-158">刪除擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="49648-158">Delete an Extended Events Session</span></span>  
 <span data-ttu-id="49648-159">您可以刪除「擴充事件」工作階段：</span><span class="sxs-lookup"><span data-stu-id="49648-159">You can delete an Extended Events session:</span></span>  
  
-   <span data-ttu-id="49648-160">在 [查詢編輯器] 中使用 `DROP EVENT SESSION`。</span><span class="sxs-lookup"><span data-stu-id="49648-160">In Query Editor using `DROP EVENT SESSION`.</span></span>  
  
-   <span data-ttu-id="49648-161">在 **[物件總管]** 中。</span><span class="sxs-lookup"><span data-stu-id="49648-161">In **Object Explorer**.</span></span>  
  
 <span data-ttu-id="49648-162">當您刪除事件工作階段時，便會移除所有組態資訊，而且工作階段定義不會再出現在 sys.server_event_sessions 目錄檢視中。</span><span class="sxs-lookup"><span data-stu-id="49648-162">When you delete an event session, all configuration information is removed and the session definition no longer appears in the sys.server_event_sessions catalog view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="49648-163">system_health 和 AlwaysOn_health 包含在中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; 請勿將它們刪除。</span><span class="sxs-lookup"><span data-stu-id="49648-163">system_health and AlwaysOn_health are included with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; do not delete them.</span></span> <span data-ttu-id="49648-164">system_health 預設為啟用 (如需詳細資訊，請參閱 [使用 system_health 工作階段](use-the-ssms-xe-profiler.md))。</span><span class="sxs-lookup"><span data-stu-id="49648-164">system_health is enabled by default (for more information, see [Use the system_health Session](use-the-ssms-xe-profiler.md)).</span></span> <span data-ttu-id="49648-165">AlwaysOn_health 預設為關閉。</span><span class="sxs-lookup"><span data-stu-id="49648-165">AlwaysOn_health is off by default.</span></span> <span data-ttu-id="49648-166">這些工作階段會收集可用於診斷效能問題的資料。</span><span class="sxs-lookup"><span data-stu-id="49648-166">These sessions collect data that can be useful for diagnosing performance issues.</span></span>  
  
 <span data-ttu-id="49648-167">若要刪除「擴充事件」工作階段，您必須擁有 ALTER ANY EVENT SESSION 權限。</span><span class="sxs-lookup"><span data-stu-id="49648-167">To delete an Extended Events session, you must have the ALTER ANY EVENT SESSION permission.</span></span>  
  
 <span data-ttu-id="49648-168">若要在 **[物件總管]** 中刪除「擴充事件」工作階段：</span><span class="sxs-lookup"><span data-stu-id="49648-168">To delete an Extended Events session in **Object Explorer**:</span></span>  
  
1.  <span data-ttu-id="49648-169">依序展開 **[管理]** 、 **[擴充事件]** 和 **[工作階段]** 節點。</span><span class="sxs-lookup"><span data-stu-id="49648-169">Expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  
  
2.  <span data-ttu-id="49648-170">以滑鼠右鍵按一下工作階段，然後選取 [刪除]。</span><span class="sxs-lookup"><span data-stu-id="49648-170">Right-click a session and select **Delete**.</span></span>  
  
3.  <span data-ttu-id="49648-171">在 **[刪除物件]** 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="49648-171">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
4.  <span data-ttu-id="49648-172">完成事件工作階段的修訂之後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="49648-172">After you finish revising the event session, click **OK**.</span></span>  
  
 <span data-ttu-id="49648-173">若要在 [查詢編輯器] 中刪除「擴充事件」工作階段，請發出下列陳述式，使用您想要刪除的「擴充事件」工作階段名稱來取代 *session_name*：</span><span class="sxs-lookup"><span data-stu-id="49648-173">To delete an Extended Events session in the **Query Editor**, Issue the following statements, replacing *session_name* with the name of the Extended Events session that you want to delete:</span></span>  
  
```  
DROP EVENT SESSION [session_name]  
ON SERVER  
```  
  
  
