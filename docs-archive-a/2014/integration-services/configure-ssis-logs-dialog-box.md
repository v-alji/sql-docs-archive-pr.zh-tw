---
title: '[設定 SSIS 記錄] 對話方塊 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.configuredtslogs.loggingdetails.f1
- sql12.dts.designer.configuredtslogs.providersandlogs.f1
- sql12.dts.designer.configuredtslogs.containers.f1
helpviewer_keywords:
- Configure SSIS Logs dialog box
ms.assetid: 4b980275-cd9a-4943-8c36-727d51f9a484
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 252b45765fb784790bcca0fb86e2e56e7e7baddc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594634"
---
# <a name="configure-ssis-logs-dialog-box"></a><span data-ttu-id="b145e-102">設定 SSIS 記錄對話方塊</span><span class="sxs-lookup"><span data-stu-id="b145e-102">Configure SSIS Logs Dialog Box</span></span>
  <span data-ttu-id="b145e-103">使用 **[設定 SSIS 記錄]** 對話方塊定義封裝的記錄選項。</span><span class="sxs-lookup"><span data-stu-id="b145e-103">Use the **Configure SSIS Logs** dialog box to define logging options for a package.</span></span>  
  
 <span data-ttu-id="b145e-104">**您想要做什麼事？**</span><span class="sxs-lookup"><span data-stu-id="b145e-104">**What do you want to do?**</span></span>  
  
1.  <span data-ttu-id="b145e-105">[開啟 [設定 SSIS 記錄] 對話方塊。](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="b145e-105">[Open the Configure SSIS Logs Dialog Box](#open_dialog)</span></span>  
  
2.  <span data-ttu-id="b145e-106">[設定 [容器] 窗格中的選項](#container)</span><span class="sxs-lookup"><span data-stu-id="b145e-106">[Configure the Options in the Containers Pane](#container)</span></span>  
  
3.  <span data-ttu-id="b145e-107">[設定 [提供者與記錄] 索引標籤上的選項](#provider)</span><span class="sxs-lookup"><span data-stu-id="b145e-107">[Configure the Options on the Providers and Logs Tab](#provider)</span></span>  
  
4.  <span data-ttu-id="b145e-108">[設定 [詳細資料] 索引標籤上的選項](#detail)</span><span class="sxs-lookup"><span data-stu-id="b145e-108">[Configure the Options on the Details Tab](#detail)</span></span>  
  
##  <a name="open-the-configure-ssis-logs-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="b145e-109">開啟 [設定 SSIS 記錄] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b145e-109">Open the Configure SSIS Logs Dialog Box</span></span>  
 <span data-ttu-id="b145e-110">**開啟 [設定 SSIS 記錄] 對話方塊**</span><span class="sxs-lookup"><span data-stu-id="b145e-110">**To open the Configure SSIS Logs dialog box**</span></span>  
  
-   <span data-ttu-id="b145e-111">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師中，按一下 **[SSIS]** 功能表上的 **[記錄]** 。</span><span class="sxs-lookup"><span data-stu-id="b145e-111">In the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click **Logging** on the **SSIS** menu.</span></span>  
  
##  <a name="configure-the-options-in-the-containers-pane"></a><a name="container"></a> <span data-ttu-id="b145e-112">設定 [容器] 窗格中的選項</span><span class="sxs-lookup"><span data-stu-id="b145e-112">Configure the Options in the Containers Pane</span></span>  
 <span data-ttu-id="b145e-113">使用 **[設定 SSIS 記錄]** 對話方塊的 **[容器]** 窗格，即可啟用封裝及其容器以進行記錄。</span><span class="sxs-lookup"><span data-stu-id="b145e-113">Use the **Containers** pane of the **Configure SSIS Logs** dialog box to enable the package and its containers for logging.</span></span>  
  
### <a name="options"></a><span data-ttu-id="b145e-114">選項。</span><span class="sxs-lookup"><span data-stu-id="b145e-114">Options</span></span>  
 <span data-ttu-id="b145e-115">**容器**</span><span class="sxs-lookup"><span data-stu-id="b145e-115">**Containers**</span></span>  
 <span data-ttu-id="b145e-116">在階層式檢視中選取核取方塊，即可啟用封裝及其容器以進行記錄：</span><span class="sxs-lookup"><span data-stu-id="b145e-116">Select the check boxes in the hierarchical view to enable the package and its containers for logging:</span></span>  
  
-   <span data-ttu-id="b145e-117">如果已清除，則表示並未啟用容器來進行記錄。</span><span class="sxs-lookup"><span data-stu-id="b145e-117">If cleared, the container is not enabled for logging.</span></span> <span data-ttu-id="b145e-118">選取即可啟用記錄。</span><span class="sxs-lookup"><span data-stu-id="b145e-118">Select to enable logging.</span></span>  
  
-   <span data-ttu-id="b145e-119">如果呈暗灰色，容器就會使用其父系的記錄選項。</span><span class="sxs-lookup"><span data-stu-id="b145e-119">If dimmed, the container uses the logging options of its parent.</span></span> <span data-ttu-id="b145e-120">封裝無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="b145e-120">This option is not available for the package.</span></span>  
  
-   <span data-ttu-id="b145e-121">如果已核取，則容器會定義它自己的記錄選項。</span><span class="sxs-lookup"><span data-stu-id="b145e-121">If checked, the container defines its own logging options.</span></span>  
  
 <span data-ttu-id="b145e-122">如果容器呈暗灰色，而您要在容器上設定記錄選項，請按兩下其核取方塊。</span><span class="sxs-lookup"><span data-stu-id="b145e-122">If a container is dimmed and you want to set logging options on the container, click its check box twice.</span></span> <span data-ttu-id="b145e-123">第一次點選時會清除核取方塊，而第二次點選則會選取核取方塊，讓您可以選擇要使用的記錄提供者和選取要記錄的資訊。</span><span class="sxs-lookup"><span data-stu-id="b145e-123">The first click clears the check box, and the second click selects it, enabling you to choose the log providers to use and select the information to log.</span></span>  
  
##  <a name="configure-the-options-on-the-providers-and-logs-tab"></a><a name="provider"></a> <span data-ttu-id="b145e-124">設定 [提供者與記錄] 索引標籤上的選項</span><span class="sxs-lookup"><span data-stu-id="b145e-124">Configure the Options on the Providers and Logs Tab</span></span>  
 <span data-ttu-id="b145e-125">使用 [設定 SSIS 記錄] 對話方塊的 [提供者與記錄] 索引標籤，即可建立和設定用於擷取執行階段事件的記錄。</span><span class="sxs-lookup"><span data-stu-id="b145e-125">Use the **Providers and Logs** tab of the **Configure SSIS Logs** dialog box to create and configure logs for capturing run-time events.</span></span>  
  
### <a name="options"></a><span data-ttu-id="b145e-126">選項。</span><span class="sxs-lookup"><span data-stu-id="b145e-126">Options</span></span>  
 <span data-ttu-id="b145e-127">**提供者類型**</span><span class="sxs-lookup"><span data-stu-id="b145e-127">**Provider type**</span></span>  
 <span data-ttu-id="b145e-128">從清單中選取記錄提供者的類型。</span><span class="sxs-lookup"><span data-stu-id="b145e-128">Select a type of log provider from the list.</span></span>  
  
 <span data-ttu-id="b145e-129">**加入**</span><span class="sxs-lookup"><span data-stu-id="b145e-129">**Add**</span></span>  
 <span data-ttu-id="b145e-130">將所指定類型的記錄加入至封裝之記錄提供者的集合。</span><span class="sxs-lookup"><span data-stu-id="b145e-130">Add a log of the specified type to the collection of log providers of the package.</span></span>  
  
 <span data-ttu-id="b145e-131">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b145e-131">**Name**</span></span>  
 <span data-ttu-id="b145e-132">使用這些核取方塊，啟用或停用容器的記錄，或是 [設定 SSIS 記錄] 對話方塊的 [容器] 窗格中選取之工作的記錄。</span><span class="sxs-lookup"><span data-stu-id="b145e-132">Enable or disable logs for containers or tasks selected in the **Containers** pane of the **Configure SSIS Logs** dialog box, by using the check boxes.</span></span> <span data-ttu-id="b145e-133">名稱欄位是可編輯的。</span><span class="sxs-lookup"><span data-stu-id="b145e-133">The name field is editable.</span></span> <span data-ttu-id="b145e-134">使用提供者的預設名稱，或輸入唯一的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="b145e-134">Use the default name for the provider, or type a unique descriptive name.</span></span>  
  
 <span data-ttu-id="b145e-135">**說明**</span><span class="sxs-lookup"><span data-stu-id="b145e-135">**Description**</span></span>  
 <span data-ttu-id="b145e-136">描述欄位是可編輯的。</span><span class="sxs-lookup"><span data-stu-id="b145e-136">The description field is editable.</span></span> <span data-ttu-id="b145e-137">按一下，然後修改記錄的預設描述。</span><span class="sxs-lookup"><span data-stu-id="b145e-137">Click and then modify the default description of the log.</span></span>  
  
 <span data-ttu-id="b145e-138">**組態**</span><span class="sxs-lookup"><span data-stu-id="b145e-138">**Configuration**</span></span>  
 <span data-ttu-id="b145e-139">在清單中選取現有的連線管理員，或按一下 \<**New connection...**> 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="b145e-139">Select an existing connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span> <span data-ttu-id="b145e-140">視記錄提供者的類型而定，您可以設定 OLE DB 連接管理員或檔案連接管理員。</span><span class="sxs-lookup"><span data-stu-id="b145e-140">Depending on the type of log provider, you can configure an OLE DB connection manager or a File connection manager.</span></span> <span data-ttu-id="b145e-141">[!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 事件記錄檔的記錄提供者不需要有連接。</span><span class="sxs-lookup"><span data-stu-id="b145e-141">The log provider for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Event Log requires no connection.</span></span>  
  
 <span data-ttu-id="b145e-142">相關主題： [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md) 、 [File Connection Manager](connection-manager/file-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="b145e-142">Related Topics: [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md) manager, [File Connection Manager](connection-manager/file-connection-manager.md)</span></span>  
  
 <span data-ttu-id="b145e-143">**刪除**</span><span class="sxs-lookup"><span data-stu-id="b145e-143">**Delete**</span></span>  
 <span data-ttu-id="b145e-144">選取記錄提供者，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="b145e-144">Select a log provider and then click **Delete**.</span></span>  
  
##  <a name="configure-the-options-on-the-details-tab"></a><a name="detail"></a> <span data-ttu-id="b145e-145">設定 [詳細資料] 索引標籤上的選項</span><span class="sxs-lookup"><span data-stu-id="b145e-145">Configure the Options on the Details Tab</span></span>  
 <span data-ttu-id="b145e-146">使用 **[設定 SSIS 記錄]** 對話方塊的 **[詳細資料]** 索引標籤，即可指定要啟用記錄的事件以及要記錄的資訊詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b145e-146">Use the **Details** tab of the **Configure SSIS Logs** dialog box to specify the events to enable for logging and the information details to log.</span></span> <span data-ttu-id="b145e-147">您選取的資訊適用於封裝中的所有記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="b145e-147">The information that you select applies to all the log providers in the package.</span></span> <span data-ttu-id="b145e-148">例如，您無法寫入部份資訊到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體，而寫入不同資訊到文字檔。</span><span class="sxs-lookup"><span data-stu-id="b145e-148">For example, you cannot write some information to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance and different information to a text file.</span></span>  
  
### <a name="options"></a><span data-ttu-id="b145e-149">選項。</span><span class="sxs-lookup"><span data-stu-id="b145e-149">Options</span></span>  
 <span data-ttu-id="b145e-150">**事件**</span><span class="sxs-lookup"><span data-stu-id="b145e-150">**Events**</span></span>  
 <span data-ttu-id="b145e-151">啟用或停用記錄事件。</span><span class="sxs-lookup"><span data-stu-id="b145e-151">Enable or disable events for logging.</span></span>  
  
 <span data-ttu-id="b145e-152">**說明**</span><span class="sxs-lookup"><span data-stu-id="b145e-152">**Description**</span></span>  
 <span data-ttu-id="b145e-153">檢視事件的描述。</span><span class="sxs-lookup"><span data-stu-id="b145e-153">View a description of the event.</span></span>  
  
 <span data-ttu-id="b145e-154">**進階**</span><span class="sxs-lookup"><span data-stu-id="b145e-154">**Advanced**</span></span>  
 <span data-ttu-id="b145e-155">選取或清除要記錄的事件，以及選取或清除要為每個事件記錄的資訊。</span><span class="sxs-lookup"><span data-stu-id="b145e-155">Select or clear events to log, and select or clear information to log for each event.</span></span> <span data-ttu-id="b145e-156">按一下 **[基本]** ，即可隱藏除了事件清單以外的所有記錄詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b145e-156">Click **Basic** to hide all logging details, except the list of events.</span></span> <span data-ttu-id="b145e-157">記錄可以使用下列資訊：</span><span class="sxs-lookup"><span data-stu-id="b145e-157">The following information is available for logging:</span></span>  
  
|<span data-ttu-id="b145e-158">值</span><span class="sxs-lookup"><span data-stu-id="b145e-158">Value</span></span>|<span data-ttu-id="b145e-159">描述</span><span class="sxs-lookup"><span data-stu-id="b145e-159">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b145e-160">**電腦**</span><span class="sxs-lookup"><span data-stu-id="b145e-160">**Computer**</span></span>|<span data-ttu-id="b145e-161">記錄事件發生所在之電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="b145e-161">The name of the computer on which the logged event occurred.</span></span>|  
|<span data-ttu-id="b145e-162">**運算子**</span><span class="sxs-lookup"><span data-stu-id="b145e-162">**Operator**</span></span>|<span data-ttu-id="b145e-163">啟動封裝之人員的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="b145e-163">The user name of the person who started the package.</span></span>|  
|<span data-ttu-id="b145e-164">**SourceName**</span><span class="sxs-lookup"><span data-stu-id="b145e-164">**SourceName**</span></span>|<span data-ttu-id="b145e-165">記錄事件發生所在之封裝、容器或工作的名稱。</span><span class="sxs-lookup"><span data-stu-id="b145e-165">The name of the package, container, or task in which the logged event occurred.</span></span>|  
|<span data-ttu-id="b145e-166">**SourceID**</span><span class="sxs-lookup"><span data-stu-id="b145e-166">**SourceID**</span></span>|<span data-ttu-id="b145e-167">記錄事件發生所在之封裝、容器或工作的全域唯一識別碼 (GUID)。</span><span class="sxs-lookup"><span data-stu-id="b145e-167">The global unique identifier (GUID) of the package, container, or task in which the logged event occurred.</span></span>|  
|<span data-ttu-id="b145e-168">**ExecutionID**</span><span class="sxs-lookup"><span data-stu-id="b145e-168">**ExecutionID**</span></span>|<span data-ttu-id="b145e-169">封裝執行個體的全域唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="b145e-169">The global unique identifier of the package execution instance.</span></span>|  
|<span data-ttu-id="b145e-170">**MessageText**</span><span class="sxs-lookup"><span data-stu-id="b145e-170">**MessageText**</span></span>|<span data-ttu-id="b145e-171">與記錄項目相關聯的訊息。</span><span class="sxs-lookup"><span data-stu-id="b145e-171">A message associated with the log entry.</span></span>|  
|<span data-ttu-id="b145e-172">**DataBytes**</span><span class="sxs-lookup"><span data-stu-id="b145e-172">**DataBytes**</span></span>|<span data-ttu-id="b145e-173">保留供未來使用。</span><span class="sxs-lookup"><span data-stu-id="b145e-173">Reserved for future use.</span></span>|  
  
 <span data-ttu-id="b145e-174">**基本**</span><span class="sxs-lookup"><span data-stu-id="b145e-174">**Basic**</span></span>  
 <span data-ttu-id="b145e-175">選取或清除要記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="b145e-175">Select or clear events to log.</span></span> <span data-ttu-id="b145e-176">此選項會隱藏除了事件清單以外的記錄詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b145e-176">This option hides logging details except the list of events.</span></span> <span data-ttu-id="b145e-177">依預設，如果您選取某個事件，該事件的所有記錄詳細資料都會被選取。</span><span class="sxs-lookup"><span data-stu-id="b145e-177">If you select an event, all logging details are selected for the event by default.</span></span> <span data-ttu-id="b145e-178">按一下 **[進階]** ，即可顯示所有的記錄詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b145e-178">Click **Advanced** to show all logging details.</span></span>  
  
 <span data-ttu-id="b145e-179">**載入**</span><span class="sxs-lookup"><span data-stu-id="b145e-179">**Load**</span></span>  
 <span data-ttu-id="b145e-180">指定現有的 XML 檔案，即可用來作為設定記錄選項的範本。</span><span class="sxs-lookup"><span data-stu-id="b145e-180">Specify an existing XML file to use as a template for setting logging options.</span></span>  
  
 <span data-ttu-id="b145e-181">**儲存**</span><span class="sxs-lookup"><span data-stu-id="b145e-181">**Save**</span></span>  
 <span data-ttu-id="b145e-182">將組態詳細資料儲存為 XML 檔案的範本。</span><span class="sxs-lookup"><span data-stu-id="b145e-182">Save configuration details as a template to an XML file.</span></span>  
  
  
