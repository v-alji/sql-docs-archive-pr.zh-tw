---
title: Integration Services 使用者介面 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services, SSIS Designer
- tools [Integration Services], SSIS Designer
- SSIS Designer
- SSIS, SSIS Designer
- Integration Services, SSIS Designer
ms.assetid: d2c48cff-46f4-4c70-b1f3-c88f9b8757f3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 60951be420397354976b8a0b6a411f18746bc735
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596150"
---
# <a name="integration-services-user-interface"></a><span data-ttu-id="0bf5c-102">Integration Services 使用者介面</span><span class="sxs-lookup"><span data-stu-id="0bf5c-102">Integration Services User Interface</span></span>
  <span data-ttu-id="0bf5c-103">除了 [ [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] 索引標籤上的設計介面以外，使用者介面還提供對下列視窗和對話方塊 (用以將功能加入封裝及設定封裝物件屬性) 的存取權：</span><span class="sxs-lookup"><span data-stu-id="0bf5c-103">In addition to the design surfaces on the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer tabs, the user interface provides access to the following windows and dialog boxes for adding features to packages and configuring the properties of package objects:</span></span>  
  
-   <span data-ttu-id="0bf5c-104">用來將功能 (例如，記錄和組態) 加入封裝的對話方塊和視窗。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-104">The dialog boxes and windows that you use to add functionality such as logging and configurations to packages.</span></span>  
  
-   <span data-ttu-id="0bf5c-105">用來設定封裝物件屬性的自訂編輯器。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-105">The custom editors for configuring the properties of package objects.</span></span> <span data-ttu-id="0bf5c-106">幾乎每種類型的容器、工作和資料流程元件都擁有自己的自訂編輯器。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-106">Almost every type of container, task, and data flow component has its own custom editor.</span></span>  
  
-   <span data-ttu-id="0bf5c-107">而 [進階編輯器]  對話方塊是一種一般編輯器，可為許多資料流程元件提供更詳細的組態選項。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-107">The **Advanced Editor** dialog box, a generic editor that provides more detailed configuration options for many data flow components.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="0bf5c-108">還提供用來設定環境與使用封裝的視窗和對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-108">also provides windows and dialog boxes for configuring the environment and working with packages.</span></span>  
  
## <a name="dialog-boxes-and-windows"></a><span data-ttu-id="0bf5c-109">對話方塊和視窗</span><span class="sxs-lookup"><span data-stu-id="0bf5c-109">Dialog Boxes and Windows</span></span>  
 <span data-ttu-id="0bf5c-110">在「 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師」中開啟封裝或新建封裝後，可以使用下列對話方塊和視窗。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-110">After you open a package or create a new package in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the following dialog boxes and windows are available.</span></span>  
  
 <span data-ttu-id="0bf5c-111">下表列出 [SSIS]  功能表和 [[!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] 之設計介面中可用的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-111">This table lists the dialog boxes that are available from the **SSIS** menu and the design surfaces of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
|<span data-ttu-id="0bf5c-112">對話方塊</span><span class="sxs-lookup"><span data-stu-id="0bf5c-112">Dialog box</span></span>|<span data-ttu-id="0bf5c-113">目的</span><span class="sxs-lookup"><span data-stu-id="0bf5c-113">Purpose</span></span>|<span data-ttu-id="0bf5c-114">存取</span><span class="sxs-lookup"><span data-stu-id="0bf5c-114">Access</span></span>|  
|----------------|-------------|------------|  
|<span data-ttu-id="0bf5c-115">**快速入門**</span><span class="sxs-lookup"><span data-stu-id="0bf5c-115">**Getting Started**</span></span>|<span data-ttu-id="0bf5c-116">存取範例、教學課程和影片。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-116">Access samples, tutorials, and videos.</span></span>|<span data-ttu-id="0bf5c-117">在 [控制流程]  索引標籤或 [資料流程]  索引標籤的設計介面上按一下滑鼠右鍵，然後按一下 [使用者入門]  。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-117">On the design surface of the **Control Flow** tab or the **Data Flow** tab, right-click and then click **Getting Started**.</span></span><br /><br /> <span data-ttu-id="0bf5c-118">若要在建立新 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案時自動顯示 [使用者入門] 視窗，請選取視窗最下方的 [Always show in new project (永遠在新專案中顯示)]。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-118">To automatically display the **Getting Started** window when you create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, select **Always show in new project** at the bottom of the window.</span></span>|  
|<span data-ttu-id="0bf5c-119">**[設定 SSIS 記錄]**</span><span class="sxs-lookup"><span data-stu-id="0bf5c-119">**Configure SSIS Logs**</span></span>|<span data-ttu-id="0bf5c-120">透過加入記錄和設定記錄詳細資料來設定封裝及其工作的記錄。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-120">Configure logging for a package and its tasks by adding logs and setting logging details.</span></span>|<span data-ttu-id="0bf5c-121">在 **[SSIS]** 功能表上，按一下 **[記錄]** 。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-121">On the **SSIS** menu, click **Logging**.</span></span><br /><br /> <span data-ttu-id="0bf5c-122">-或-</span><span class="sxs-lookup"><span data-stu-id="0bf5c-122">-or-</span></span><br /><br /> <span data-ttu-id="0bf5c-123">以滑鼠右鍵按一下 [控制流程]  索引標籤之設計介面的任意位置，然後按一下 [記錄]  。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-123">Right-click anywhere on the design surface of the **Control Flow** tab, and then click **Logging**.</span></span>|  
|<span data-ttu-id="0bf5c-124">**[封裝組態組合管理]**</span><span class="sxs-lookup"><span data-stu-id="0bf5c-124">**Package Configuration Organizer**</span></span>|<span data-ttu-id="0bf5c-125">加入並編輯封裝組態。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-125">Add and edit package configurations.</span></span> <span data-ttu-id="0bf5c-126">您可從此對話方塊執行「封裝組態精靈」。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-126">You run the Package Configuration Wizard from this dialog box.</span></span>|<span data-ttu-id="0bf5c-127">在 [SSIS]  功能表上，按一下 [封裝組態]  。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-127">On the **SSIS** menu, click **Package Configurations**.</span></span><br /><br /> <span data-ttu-id="0bf5c-128">-或-</span><span class="sxs-lookup"><span data-stu-id="0bf5c-128">-or-</span></span><br /><br /> <span data-ttu-id="0bf5c-129">以滑鼠右鍵按一下 [控制流程]  索引標籤之設計介面的任意位置，然後按一下 [封裝組態]  。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-129">Right-click anywhere on the design surface of the **Control Flow** tab, and then click **Package Configurations**.</span></span>|  
|<span data-ttu-id="0bf5c-130">**數位簽章**</span><span class="sxs-lookup"><span data-stu-id="0bf5c-130">**Digital Signing**</span></span>|<span data-ttu-id="0bf5c-131">簽署封裝或從封裝中移除簽章。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-131">Sign a package or remove the signature from the package.</span></span>|<span data-ttu-id="0bf5c-132">在 **[SSIS]** 功能表上，按一下 **數位簽章**。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-132">On the **SSIS** menu, click **Digital Signing**.</span></span><br /><br /> <span data-ttu-id="0bf5c-133">-或-</span><span class="sxs-lookup"><span data-stu-id="0bf5c-133">-or-</span></span><br /><br /> <span data-ttu-id="0bf5c-134">以滑鼠右鍵按一下 [控制流程]  索引標籤之設計介面的任意位置，然後按一下 [數位簽章]  。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-134">Right-click anywhere on the design surface of the **Control Flow** tab, and then click **Digital Signing**.</span></span>|  
|<span data-ttu-id="0bf5c-135">**設定中斷點**</span><span class="sxs-lookup"><span data-stu-id="0bf5c-135">**Set Breakpoints**</span></span>|<span data-ttu-id="0bf5c-136">啟用工作上的中斷點並設定中斷點屬性。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-136">Enable breakpoints on tasks and set breakpoint properties.</span></span>|<span data-ttu-id="0bf5c-137">在 [控制流程]  索引標籤的設計介面上，以滑鼠右鍵按一下工作或容器，然後按一下 [編輯中斷點]  。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-137">On the design surface of the **Control Flow** tab, right-click a task or container, and then click **Edit Breakpoints**.</span></span> <span data-ttu-id="0bf5c-138">若要設定封裝上的中斷點，請以滑鼠右鍵按一下 [控制流程]  索引標籤之設計介面的任意位置，然後按一下 [編輯中斷點]  。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-138">To set a breakpoint on the package, right-click anywhere on the design surface of the **Control Flow** tab, and then click **Edit Breakpoints**.</span></span>|  
  
 <span data-ttu-id="0bf5c-139">[使用者入門]  視窗提供範例、教學課程和影片的連結。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-139">The **Getting Started** window provides links to samples, tutorials, and videos.</span></span> <span data-ttu-id="0bf5c-140">若要加入其他內容的連結，請修改目前版本 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]隨附的 SamplesSites.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-140">To add links to additional content, modify the SamplesSites.xml file that is included with the current release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="0bf5c-141">建議不要修改指定 RSS 摘要 URL 的 \<GettingStartedSamples> 元素值。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-141">It is recommended that you not modify the \<GettingStartedSamples> element value that specifies the RSS feed URL.</span></span> <span data-ttu-id="0bf5c-142">檔案位於 *\<drive>* :\Program Files\Microsoft SQL Server\110\DTS\Binn 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-142">The file is located in the *\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn folder.</span></span> <span data-ttu-id="0bf5c-143">在 64 位元電腦上，檔案位於 *\<drive>* :\Program Files(x86)\Microsoft SQL Server\110\DTS\Binn 資料夾</span><span class="sxs-lookup"><span data-stu-id="0bf5c-143">On a 64-bit computer, the file is located in the *\<drive>*:\Program Files(x86)\Microsoft SQL Server\110\DTS\Binn folder</span></span>  
  
 <span data-ttu-id="0bf5c-144">如果 SamplesSites.xml 檔案未損毀，請使用下列預設 xml 取代檔案中的 xml。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-144">If the SamplesSites.xml file does become corrupted, replace the xml in the file with the following default xml.</span></span>  
  
 `<?xml version="1.0" ?>`  
  
 `- <SamplesSites>`  
  
 `<GettingStartedSamples>https://go.microsoft.com/fwlink/?LinkID=203147</GettingStartedSamples>`  
  
 `- <ToolboxSamples>`  
  
 `<Site>https://go.microsoft.com/fwlink/?LinkID=203286&query=SSIS%20{0}</Site>`  
  
 `</ToolboxSamples>`  
  
 `</SamplesSites>`  
  
 <span data-ttu-id="0bf5c-145">下表列出 [SSIS]  和 [檢視]  功能表，以及 [[!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] 之設計介面中可用的視窗。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-145">This table lists the windows that are available from the **SSIS** and **View** menus and the design surfaces of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
|<span data-ttu-id="0bf5c-146">時間範圍</span><span class="sxs-lookup"><span data-stu-id="0bf5c-146">Window</span></span>|<span data-ttu-id="0bf5c-147">目的</span><span class="sxs-lookup"><span data-stu-id="0bf5c-147">Purpose</span></span>|<span data-ttu-id="0bf5c-148">存取</span><span class="sxs-lookup"><span data-stu-id="0bf5c-148">Access</span></span>|  
|------------|-------------|------------|  
|<span data-ttu-id="0bf5c-149">**變數**</span><span class="sxs-lookup"><span data-stu-id="0bf5c-149">**Variables**</span></span>|<span data-ttu-id="0bf5c-150">加入並管理自訂變數。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-150">Add and manage custom variables.</span></span>|<span data-ttu-id="0bf5c-151">在 **[SSIS]** 功能表上，按一下 **變數**。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-151">On the **SSIS** menu, click **Variables**.</span></span><br /><br /> <span data-ttu-id="0bf5c-152">-或-</span><span class="sxs-lookup"><span data-stu-id="0bf5c-152">-or-</span></span><br /><br /> <span data-ttu-id="0bf5c-153">以滑鼠右鍵按一下 [控制流程]  和 [資料流程]  索引標籤之設計介面的任意位置，然後按一下 [變數]  。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-153">Right-click anywhere in the design surface of the **Control Flow** and **Data Flow** tabs, and then click **Variables**.</span></span><br /><br /> <span data-ttu-id="0bf5c-154">-或-</span><span class="sxs-lookup"><span data-stu-id="0bf5c-154">-or-</span></span><br /><br /> <span data-ttu-id="0bf5c-155">在 [檢視]  功能表上，指向 [其他視窗]  ，然後按一下 [變數]  。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-155">On the **View** menu, point to **Other Windows**, and then click **Variables**.</span></span>|  
|<span data-ttu-id="0bf5c-156">**記錄事件**</span><span class="sxs-lookup"><span data-stu-id="0bf5c-156">**Log Events**</span></span>|<span data-ttu-id="0bf5c-157">檢視執行階段的記錄項目。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-157">View log entries at run time.</span></span>|<span data-ttu-id="0bf5c-158">在 **[SSIS]** 功能表上，按一下 **記錄事件**。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-158">On the **SSIS** menu, click **Log Events**.</span></span><br /><br /> <span data-ttu-id="0bf5c-159">-或-</span><span class="sxs-lookup"><span data-stu-id="0bf5c-159">-or-</span></span><br /><br /> <span data-ttu-id="0bf5c-160">以滑鼠右鍵按一下 [控制流程]  和 [資料流程]  索引標籤之設計介面的任意位置，然後按一下 [記錄事件]  。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-160">Right-click anywhere in the design surface of the **Control Flow** and **Data Flow** tabs, and then click **Log Events**.</span></span><br /><br /> <span data-ttu-id="0bf5c-161">-或-</span><span class="sxs-lookup"><span data-stu-id="0bf5c-161">-or-</span></span><br /><br /> <span data-ttu-id="0bf5c-162">在 [檢視]  功能表上，指向 [其他視窗]  ，然後按一下 [記錄事件]  。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-162">On the **View** menu, point to **Other Windows**, and then click **Log Events**.</span></span>|  
  
## <a name="custom-editors"></a><span data-ttu-id="0bf5c-163">自訂編輯器</span><span class="sxs-lookup"><span data-stu-id="0bf5c-163">Custom Editors</span></span>  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="0bf5c-164">為大多數容器、工作、來源、轉換和目的地提供自訂對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-164">provides a custom dialog box for most containers, tasks, sources, transformations, and destinations.</span></span>  
  
 <span data-ttu-id="0bf5c-165">下表描述如何存取自訂對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-165">The following table describes how to access custom dialog boxes.</span></span>  
  
|<span data-ttu-id="0bf5c-166">編輯器類型</span><span class="sxs-lookup"><span data-stu-id="0bf5c-166">Editor type</span></span>|<span data-ttu-id="0bf5c-167">存取</span><span class="sxs-lookup"><span data-stu-id="0bf5c-167">Access</span></span>|  
|-----------------|------------|  
|<span data-ttu-id="0bf5c-168">容器。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-168">Container.</span></span> <span data-ttu-id="0bf5c-169">如需詳細資訊，請參閱 [整合服務容器](control-flow/integration-services-containers.md)。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-169">For more information, see [Integration Services Containers](control-flow/integration-services-containers.md).</span></span>|<span data-ttu-id="0bf5c-170">在 [控制流程]  索引標籤的設計介面上，按兩下容器。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-170">On the design surface of the **Control Flow** tab, double-click the container.</span></span>|  
|<span data-ttu-id="0bf5c-171">工作。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-171">Task.</span></span> <span data-ttu-id="0bf5c-172">如需詳細資訊，請參閱 [Integration Services Tasks](control-flow/integration-services-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-172">For more information, see [Integration Services Tasks](control-flow/integration-services-tasks.md).</span></span>|<span data-ttu-id="0bf5c-173">在 [控制流程]  索引標籤的設計介面上，按兩下工作。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-173">On the design surface of the **Control Flow** tab, double-click the task.</span></span>|  
|<span data-ttu-id="0bf5c-174">來源。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-174">Source.</span></span>|<span data-ttu-id="0bf5c-175">在 [資料流程]  索引標籤的設計介面上，按兩下來源。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-175">On the design surface of the **Data Flow** tab, double-click the source.</span></span>|  
|<span data-ttu-id="0bf5c-176">轉換。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-176">Transformation.</span></span> <span data-ttu-id="0bf5c-177">如需詳細資訊，請參閱 [Integration Services 轉換](data-flow/transformations/integration-services-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-177">For more information, see [Integration Services Transformations](data-flow/transformations/integration-services-transformations.md).</span></span>|<span data-ttu-id="0bf5c-178">在 [資料流程]  索引標籤的設計介面上，按兩下轉換。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-178">On the design surface of the **Data Flow** tab, double-click the transformation.</span></span>|  
|<span data-ttu-id="0bf5c-179">目的地。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-179">Destination.</span></span>|<span data-ttu-id="0bf5c-180">在 [資料流程]  索引標籤的設計介面上，按兩下目的地。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-180">On the design surface of the **Data Flow** tab, double-click the destination.</span></span>|  
  
## <a name="advanced-editor"></a><span data-ttu-id="0bf5c-181">進階編輯器</span><span class="sxs-lookup"><span data-stu-id="0bf5c-181">Advanced Editor</span></span>  
 <span data-ttu-id="0bf5c-182">[進階編輯器]  對話方塊是用於設定資料流程元件的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-182">The **Advanced Editor** dialog box is a user interface for configuring data flow components.</span></span> <span data-ttu-id="0bf5c-183">它反映使用一般配置之元件的屬性。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-183">It reflects the properties of the component using a generic layout.</span></span> <span data-ttu-id="0bf5c-184">[進階編輯器]  對話方塊不可用於具有多個輸入的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 轉換。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-184">The **Advanced Editor** dialog box is not available to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] transformations that have multiple inputs.</span></span>  
  
 <span data-ttu-id="0bf5c-185">若要開啟此編輯器，請在 [屬性] 視窗中按一下 [顯示進階編輯器]，或以滑鼠右鍵按一下資料流程元件，然後按一下 [顯示進階編輯器]。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-185">To open this editor, click **ShowAdvanced Editor** in the **Properties** window or right-click a data flow component, and then click **ShowAdvanced Editor**.</span></span>  
  
 <span data-ttu-id="0bf5c-186">如果您要建立自訂來源、轉換或目的地，但不想寫入自訂使用者介面，可改用 [進階編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-186">If you create a custom source, transformation, or destination but do not want to write a custom user interface, you can use the **Advanced Editor** instead.</span></span>  
  
## <a name="sql-server-data-tools-features"></a><span data-ttu-id="0bf5c-187">SQL Server Data Tools 功能</span><span class="sxs-lookup"><span data-stu-id="0bf5c-187">SQL Server Data Tools Features</span></span>  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="0bf5c-188">提供使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝的視窗、對話方塊和功能表選項。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-188">provides windows, dialog boxes, and menu options for working with [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 <span data-ttu-id="0bf5c-189">以下是可用視窗和功能表的摘要。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-189">The following is a summary of the available windows and menus:</span></span>  
  
-   <span data-ttu-id="0bf5c-190">方案總管視窗會列出專案 (包括開發 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案) 及專案檔案。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-190">The **Solution Explorer** window lists projects, including the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in which you develop [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages, and project files.</span></span>  
  
     <span data-ttu-id="0bf5c-191">若要依名稱排序專案中包含的封裝，請以滑鼠右鍵按一下 [SSIS 封裝]  節點，然後按一下 [依名稱排序]  。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-191">To sort by name the packages contained in a project, right-click the **SSIS Packages** node and then click **Sort by name**.</span></span>  
  
-   <span data-ttu-id="0bf5c-192">[工具箱]  視窗會列出用於建立控制流程和資料流程的控制流程項目和資料流程項目。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-192">The **Toolbox** window lists the control flow and data flow items for building control flows and data flows.</span></span>  
  
-   <span data-ttu-id="0bf5c-193">[屬性]  視窗會列出物件屬性。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-193">The **Properties** window lists object properties.</span></span>  
  
-   <span data-ttu-id="0bf5c-194">[格式]  功能表提供用於調整封裝中控制項的大小以及對齊這些控制項的選項。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-194">The **Format** menu provides options for sizing and aligning controls in a package.</span></span>  
  
-   <span data-ttu-id="0bf5c-195">[編輯]  功能表提供用於在設計介面上複製物件的複製和貼上功能。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-195">The **Edit** menu provides copy and paste functionality for copying objects on the design surfaces.</span></span>  
  
-   <span data-ttu-id="0bf5c-196">[檢視]  功能表提供用於在 [[!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] 中修改物件之圖形表示的選項</span><span class="sxs-lookup"><span data-stu-id="0bf5c-196">The **View** menu provides options for modifying the graphical representation of objects in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer</span></span>  
  
 <span data-ttu-id="0bf5c-197">如需有關其他視窗和功能表的詳細資訊，請參閱 Visual Studio 文件集。</span><span class="sxs-lookup"><span data-stu-id="0bf5c-197">For more information about additional windows and menus, see the Visual Studio documentation.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0bf5c-198">相關工作</span><span class="sxs-lookup"><span data-stu-id="0bf5c-198">Related Tasks</span></span>  
 <span data-ttu-id="0bf5c-199">如需如何在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中建立封裝的資訊，請參閱 [在 SQL Server 資料工具中建立封裝](create-packages-in-sql-server-data-tools.md)</span><span class="sxs-lookup"><span data-stu-id="0bf5c-199">For information about how to create packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], see [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bf5c-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bf5c-200">See Also</span></span>  
 [<span data-ttu-id="0bf5c-201">SSIS 設計工具</span><span class="sxs-lookup"><span data-stu-id="0bf5c-201">SSIS Designer</span></span>](ssis-designer.md)  
  
  
